# Pipeline Status Dashboard Template

本模板定義 Progress Dashboard 的輸出格式。根據使用者語言切換中文/英文版本。

---

## 繁體中文版

```
+=========================================+
|   Academic Pipeline Status              |
+=========================================+
| 主題：{topic}                            |
+-----------------------------------------+

  Stage 1 RESEARCH    [{status_icon}] {status_text}
    {mode_line}
    {outputs_line}

  Stage 2 WRITE       [{status_icon}] {status_text}
    {mode_line}
    {outputs_line}

  Stage 3 REVIEW      [{status_icon}] {status_text}
    {mode_line}
    {decision_line}

  Stage 4 REVISE      [{status_icon}] {status_text}
    {revision_round_line}
    {addressed_line}

  Stage 3' RE-REVIEW  [{status_icon}] {status_text}
    {loop_count_line}

  Stage 5 FINALIZE    [{status_icon}] {status_text}
    {format_line}

+-----------------------------------------+
| 材料清單：                               |
|   [{icon}] 研究問題摘要 (RQ Brief)       |
|   [{icon}] 方法論藍圖                    |
|   [{icon}] 文獻書目                      |
|   [{icon}] 綜合分析報告                  |
|   [{icon}] 論文草稿                      |
|   [{icon}] 審查報告                      |
|   [{icon}] 修訂路線圖                    |
|   [{icon}] 修訂稿                        |
|   [{icon}] 回覆審查者                    |
|   [{icon}] 最終論文                      |
+-----------------------------------------+
| 修訂歷程：                               |
|   {revision_history}                     |
+-----------------------------------------+
| 下一步：{next_step_suggestion}            |
+=========================================+
```

## English Version

```
+=========================================+
|   Academic Pipeline Status              |
+=========================================+
| Topic: {topic}                          |
+-----------------------------------------+

  Stage 1 RESEARCH    [{status_icon}] {status_text}
    {mode_line}
    {outputs_line}

  Stage 2 WRITE       [{status_icon}] {status_text}
    {mode_line}
    {outputs_line}

  Stage 3 REVIEW      [{status_icon}] {status_text}
    {mode_line}
    {decision_line}

  Stage 4 REVISE      [{status_icon}] {status_text}
    {revision_round_line}
    {addressed_line}

  Stage 3' RE-REVIEW  [{status_icon}] {status_text}
    {loop_count_line}

  Stage 5 FINALIZE    [{status_icon}] {status_text}
    {format_line}

+-----------------------------------------+
| Materials:                              |
|   [{icon}] RQ Brief                     |
|   [{icon}] Methodology Blueprint        |
|   [{icon}] Bibliography                 |
|   [{icon}] Synthesis Report             |
|   [{icon}] Paper Draft                  |
|   [{icon}] Review Reports               |
|   [{icon}] Revision Roadmap             |
|   [{icon}] Revised Draft                |
|   [{icon}] Response to Reviewers        |
|   [{icon}] Final Paper                  |
+-----------------------------------------+
| Revision History:                       |
|   {revision_history}                    |
+-----------------------------------------+
| Next Step: {next_step_suggestion}       |
+=========================================+
```

---

## 欄位定義

### status_icon

| 狀態 | Icon |
|------|------|
| completed | `v` |
| in_progress | `..` |
| pending | ` ` (空格) |
| skipped | `--` |

### status_text

| 狀態 | 中文 | English |
|------|------|---------|
| completed | 已完成 | Completed |
| in_progress | 進行中 | In Progress |
| pending | 待執行 | Pending |
| skipped | 已跳過 | Skipped |

### mode_line

格式：`Mode: {mode_name}`
- 僅在 status 為 completed 或 in_progress 時顯示
- 如果 mode 有切換（如 plan --> full），顯示完整路徑

### outputs_line

格式：`Outputs: {output_1}, {output_2}, ...`
- 僅在 status 為 completed 時顯示
- 列出該 stage 的所有產出物

### decision_line

格式：`Decision: {Accept/Minor Revision/Major Revision/Reject}`
- 僅在 Stage 3 或 Stage 3' completed 時顯示

### revision_round_line

格式：`Revision Round: {current}/{max}`
- 僅在 Stage 4 in_progress 時顯示

### addressed_line

格式：`Addressed: {count}/{total} required revisions`
- 僅在 Stage 4 in_progress 時顯示

### loop_count_line

格式：`Loop: {count}/2`
- 僅在 Stage 3' 時顯示

### material icon

| 狀態 | Icon |
|------|------|
| available | `v` |
| missing | ` ` (空格) |

### revision_history

每輪一行：
```
Round {n}: {decision} | {addressed}/{total} items addressed
  Pending: {pending_items_summary}
```

如果沒有修訂歷史，顯示「（尚無修訂歷程）」或「(No revision history yet)」。

### next_step_suggestion

根據當前狀態自動產生的建議：
- Stage 1 completed: 「建議進入 Stage 2 (WRITE)，使用 {recommended_mode} mode」
- Stage 3 completed (Major): 「需要進入 Stage 4 (REVISE)，有 {N} 個必修項目」
- Stage 4 completed: 「建議進入 Stage 3' (RE-REVIEW) 確認修訂品質」
- Stage 3' completed (Accept): 「恭喜！進入 Stage 5 (FINALIZE) 產出最終版本」
- Pipeline completed: 「Pipeline 完成！最終論文已就緒。」

---

## 簡化版（Stage 完成後自動附上）

一行式進度條：

```
Pipeline: [v]RESEARCH -> [v]WRITE -> [..]REVIEW -> [ ]REVISE -> [ ]FINALIZE
```

或中文版：

```
進度：[v]研究 -> [v]撰寫 -> [..]審查 -> [ ]修訂 -> [ ]完稿
```
