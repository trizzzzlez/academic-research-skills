# Pipeline State Machine -- 完整定義

本文件定義 academic-pipeline 的所有合法狀態、轉換條件、轉換動作和異常處理。

---

## 狀態定義

### Stage 狀態

| 狀態 | 說明 |
|------|------|
| `pending` | 尚未開始，等待前置 stage 完成 |
| `in_progress` | 正在執行中 |
| `completed` | 已完成，產出物已記錄 |
| `skipped` | 使用者選擇跳過 |

### Pipeline 全域狀態

| 狀態 | 說明 |
|------|------|
| `initializing` | 正在偵測進入點和材料 |
| `running` | Pipeline 執行中（至少一個 stage 為 in_progress） |
| `paused` | 使用者暫停，可隨時恢復 |
| `completed` | 所有必要 stage 完成，最終論文已產出 |
| `aborted` | 使用者放棄（如 Reject 後選擇放棄） |

---

## 狀態轉換圖（ASCII）

```
                        +-------------+
                        | INITIALIZING|
                        +------+------+
                               |
                    [偵測進入點 & 材料]
                               |
              +----------------+----------------+
              |                |                |
              v                v                v
        +---------+     +---------+      +---------+
        | Stage 1 |     | Stage 2 |      | Stage 3 |  ... (mid-entry)
        | RESEARCH|     | WRITE   |      | REVIEW  |
        +----+----+     +----+----+      +----+----+
             |               |                |
       [materials]     [paper draft]    [editorial decision]
             |               |                |
             v               v                |
        +---------+     +---------+           |
        | Stage 2 |     | Stage 3 |           |
        | WRITE   |     | REVIEW  |           |
        +----+----+     +----+----+           |
             |               |                |
             v               v                v
        +---------+     +----+----------------+----+
        | Stage 3 |     |   DECISION ROUTER        |
        | REVIEW  |     +----+----+----+----+------+
        +----+----+          |    |    |    |
             |               |    |    |    |
             v               v    v    v    v
    +--------+--------+    Acc  Min  Maj  Rej
    | DECISION ROUTER |     |    |    |    |
    +-+---+---+---+---+     |    |    |    +---> [使用者選擇]
      |   |   |   |         |    |    |              |     |
      v   v   v   v         |    v    v              v     v
     Acc Min Maj Rej        | +------+------+    Stage 2  ABORT
      |   |   |   |         | | Stage 4     |    (重構)
      |   |   |   |         | | REVISE      |
      |   |   |   |         | +------+------+
      |   |   v   v         |        |
      |   | +------+        |  [revised draft]
      |   | |Stage4|        |        |
      |   | |REVISE|        |        v
      |   | +--+---+        | +------+------+
      |   |    |             | | Stage 3'    |
      |   |    v             | | RE-REVIEW   |
      |   | +------+        | +------+------+
      |   | |Stg 3'|        |        |
      |   | |RE-REV|        |  [loop_count check]
      |   | +--+---+        |        |
      |   |    |             |   +----+----+
      |   |    v             |   |         |
      |   | [decision]       | <=2       >2
      |   |    |             |   |         |
      v   v    v             v   v         v
    +-+---+----+---+      Stage 4    +---------+
    | Stage 5      |      (再修訂)   | Stage 5 |
    | FINALIZE     |                 | (附警告) |
    +------+-------+                 +----+----+
           |                              |
           v                              v
       +-------+                      +-------+
       |  END  |                      |  END  |
       +-------+                      +-------+
```

---

## 合法的狀態轉換

### 正常流程轉換

| 從 | 到 | 前置條件 | 動作 |
|----|-----|---------|------|
| INIT | Stage 1 | 使用者確認要從 Stage 1 開始 | 偵測 mode 偏好，啟動 deep-research |
| INIT | Stage 2 | 使用者有研究材料，確認跳過 Stage 1 | 偵測材料，啟動 academic-paper |
| INIT | Stage 3 | 使用者有完整論文 | 確認論文語言/領域，啟動 reviewer |
| INIT | Stage 4 | 使用者有審查意見 | 確認論文 + 審查意見，啟動 revision |
| INIT | Stage 5 | 使用者有最終稿要轉格式 | 確認格式需求，啟動 format-convert |
| Stage 1 | Stage 2 | Stage 1 completed，材料齊備 | handoff RQ Brief + Bibliography + Synthesis |
| Stage 2 | Stage 3 | Stage 2 completed，Paper Draft 產出 | 傳遞 Paper Draft 給 reviewer |
| Stage 3 | Stage 4 | Decision = Minor/Major Revision | 傳遞 Revision Roadmap |
| Stage 3 | Stage 5 | Decision = Accept | 傳遞 accepted draft |
| Stage 4 | Stage 3' | Stage 4 completed | 傳遞 Revised Draft + Response to Reviewers |
| Stage 3' | Stage 4 | Decision = Major，loop_count <= 2 | 傳遞新的 Revision Roadmap |
| Stage 3' | Stage 5 | Decision = Accept/Minor，或 loop_count > 2 | 傳遞 final draft |

### 特殊流程轉換

| 從 | 到 | 前置條件 | 動作 |
|----|-----|---------|------|
| Stage 3 (Reject) | Stage 2 | 使用者選擇重構 | 清除 Stage 2-3 狀態，保留 Stage 1 材料，重啟 Stage 2 |
| Stage 3 (Reject) | ABORT | 使用者選擇放棄 | 儲存所有已產出材料，標記 pipeline aborted |
| Stage 3' (loop > 2) | Stage 5 | 自動觸發 | 附警告訊息，未解決問題標記為 Acknowledged Limitations |
| Any stage | PAUSED | 使用者說「暫停」「先這樣」 | 儲存 pipeline state |
| PAUSED | 上次 stage | 使用者回來繼續 | 恢復 pipeline state，顯示 Dashboard |

### 禁止的轉換（不合法）

| 從 | 到 | 原因 |
|----|-----|------|
| Stage 1 | Stage 3 | 不可跳過 Stage 2（除非 mid-entry）|
| Stage 4 | Stage 5 | 不可跳過 RE-REVIEW（修訂後必須再審） |
| Stage 5 | Stage 3 | 不可回退（FINALIZE 後不可再審查） |
| Stage 3' | Stage 2 | 不可回退到 WRITE（只有 Reject 時才可） |
| completed | in_progress | 已完成的 stage 不可重新開始 |

---

## 材料依賴矩陣

| 材料 | 產出於 | 消費於 | 必要/建議 |
|------|--------|--------|----------|
| RQ Brief | Stage 1 | Stage 2 (Phase 0) | 建議 |
| Methodology Blueprint | Stage 1 | Stage 2 (Phase 0) | 建議 |
| Bibliography | Stage 1 | Stage 2 (Phase 1) | 建議 |
| Synthesis Report | Stage 1 | Stage 2 (Phase 3) | 建議 |
| Paper Draft | Stage 2 | Stage 3 (Phase 0) | 必要 |
| Review Reports (x4) | Stage 3 | Stage 4 (input) | 必要 |
| Editorial Decision | Stage 3 | Stage 4 (input) | 必要 |
| Revision Roadmap | Stage 3 | Stage 4 (input) | 必要 |
| Revised Draft | Stage 4 | Stage 3' (Phase 0) | 必要 |
| Response to Reviewers | Stage 4 | Stage 3' (input) | 建議 |
| Final Paper | Stage 5 | END (delivery) | 必要 |

---

## 異常狀態處理

### 超時

如果某個 stage 長時間無進展（例如 Socratic mode 超過 15 輪未收斂）：
1. state_tracker 標記該 stage 為 `stalled`
2. orchestrator 提供選項：
   - 切換 mode（socratic --> full）
   - 縮小範圍
   - 跳過此 stage

### 材料遺失

如果轉場時發現需要的材料不存在：
1. state_tracker 報告材料缺口
2. orchestrator 建議回到產出該材料的 stage
3. 使用者可以選擇：補做 / 跳過（自負風險）

### Session 中斷

如果使用者離開後回來：
1. orchestrator 顯示 Progress Dashboard
2. 確認是否從斷點繼續
3. 檢查是否需要刷新任何已過時的材料

---

## Revision Loop 規則

### 計數

```
loop_count 定義：
  Stage 3 (首次 REVIEW) --> 不計入 loop_count
  Stage 3' (第一次 RE-REVIEW) --> loop_count = 1
  Stage 3' (第二次 RE-REVIEW) --> loop_count = 2
  loop_count > 2 --> 觸發強制 FINALIZE
```

### 強制 FINALIZE 警告訊息

```
已達到最大修訂輪數（2 輪）。

目前仍有 [N] 個未解決的審查意見。
這些問題將被標記為論文的 Acknowledged Limitations。

建議：
1. 進入 Stage 5 (FINALIZE)，在論文中明確說明這些限制
2. 如果你覺得這些問題很關鍵，可以考慮在未來的研究中處理

要進入 FINALIZE 嗎？
```
