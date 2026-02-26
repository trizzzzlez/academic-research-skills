# Mode Selection Guide — 模式選擇指南

## 概述

deep-research 提供 6 種模式，適用於不同的研究階段和需求。本指南幫助使用者選擇最適合的模式。

---

## 決策流程圖

```
使用者輸入
    │
    ├── 已有清楚的研究問題？
    │   ├── Yes ──→ 已有文本要審查？
    │   │            ├── Yes ──→ review mode
    │   │            └── No ───→ 需要完整報告？
    │   │                         ├── Yes ──→ full mode
    │   │                         └── No ───→ 只需文獻？
    │   │                                     ├── Yes ──→ lit-review mode
    │   │                                     └── No ───→ quick mode
    │   │
    │   └── No ──→ 想被引導思考？
    │              ├── Yes ──→ socratic mode
    │              └── No ───→ full mode
    │                          (Phase 1 互動式 RQ 釐清)
    │
    ├── 只需要驗證特定事實？
    │   └── Yes ──→ fact-check mode
    │
    └── 不確定需要什麼？
        └── 描述你的情境 → 系統自動推薦模式
```

---

## 各模式詳細資訊

### full mode（完整研究）

| 項目 | 說明 |
|------|------|
| **適用場景** | 需要從零開始進行完整的學術研究，產出可引用的研究報告 |
| **不適用場景** | 只需要快速了解一個主題；已有完整研究只需審查；只需要文獻清單 |
| **典型使用者** | 研究生準備論文提案、政策研究員撰寫分析報告、學者進行新領域探索 |
| **預期產出** | 完整 APA 7.0 報告（3,000-8,000 字），含文獻回顧、方法論、分析、結論 |
| **預期對話輪數** | 2-5 輪（Phase 1 互動 + 確認點） |
| **啟用 Agent 數** | 全部 9 個 |
| **所需時間** | 較長，適合不趕時間的深入研究 |

**觸發範例**：
```
"Research the impact of AI on higher education quality assurance"
"深度研究少子化對台灣高等教育的影響"
"研究 SDGs 在亞洲大學的實踐現況"
```

---

### quick mode（快速研究）

| 項目 | 說明 |
|------|------|
| **適用場景** | 需要快速了解一個主題的核心觀點和主要文獻，時間有限 |
| **不適用場景** | 需要完整的方法論設計；需要深入的批判性分析；需要可發表品質的報告 |
| **典型使用者** | 準備會議背景資料的行政人員、需要快速文獻掃描的研究者、寫提案前的初步探索 |
| **預期產出** | 研究簡報（500-1,500 字），含重點摘要、主要文獻、初步觀點 |
| **預期對話輪數** | 0-1 輪（通常直接產出） |
| **啟用 Agent 數** | 4 個（RQ + Biblio + Verification + Report） |
| **所需時間** | 較短 |

**觸發範例**：
```
"Quick research on blockchain in education"
"快速研究一下教育科技的最新趨勢"
```

---

### review mode（文本審查）

| 項目 | 說明 |
|------|------|
| **適用場景** | 已有一篇論文/報告/草稿，需要專業的審查和回饋 |
| **不適用場景** | 還沒有文本要審查；需要從零寫一篇研究；需要文獻搜尋 |
| **典型使用者** | 論文寫完需要審稿回饋的研究生、期刊投稿前的自我檢查、同儕審查 |
| **預期產出** | 審查報告，含 Editorial Verdict（Accept/Revise/Reject）、具體修改建議、倫理審查 |
| **預期對話輪數** | 0-1 輪 |
| **啟用 Agent 數** | 3 個（Editor + Devil's Advocate + Ethics） |
| **所需時間** | 中等，取決於文本長度 |

**觸發範例**：
```
"Review this paper"
"幫我審查這篇論文的方法論"
"Check this manuscript before submission"
```

---

### lit-review mode（文獻回顧）

| 項目 | 說明 |
|------|------|
| **適用場景** | 需要系統性的文獻搜尋和整合分析，但不需要完整的研究報告 |
| **不適用場景** | 需要包含原創分析的完整報告；只需要驗證幾個事實；需要方法論設計 |
| **典型使用者** | 撰寫論文文獻回顧章節的研究生、進行系統性回顧的研究團隊、課程作業 |
| **預期產出** | 註釋書目 + 綜合分析（1,500-4,000 字），含主題分類、證據矩陣、研究空白 |
| **預期對話輪數** | 1-2 輪（確認搜尋範圍） |
| **啟用 Agent 數** | 3 個（Biblio + Verification + Synthesis） |
| **所需時間** | 中等 |

**觸發範例**：
```
"Literature review on SDGs in higher education"
"文獻回顧：台灣高教品質保證的演進"
"Systematic review of AI-assisted assessment"
```

---

### fact-check mode（事實查核）

| 項目 | 說明 |
|------|------|
| **適用場景** | 需要驗證特定事實聲明的真實性和來源品質 |
| **不適用場景** | 需要完整的研究分析；需要文獻綜合；需要產出研究報告 |
| **典型使用者** | 驗證會議中引用的數據、檢查報告中的事實準確性、查核政策聲明 |
| **預期產出** | 驗證報告（300-800 字），含來源評級、事實準確度評估、可信度判定 |
| **預期對話輪數** | 0 輪（直接產出） |
| **啟用 Agent 數** | 1 個（Source Verification） |
| **所需時間** | 最短 |

**觸發範例**：
```
"Fact-check these claims about Taiwan's university enrollment"
"事實查核：台灣大學數量是否真的在下降？"
"Verify: 'OECD countries average 50% tertiary attainment rate'"
```

---

### socratic mode（引導式研究）

| 項目 | 說明 |
|------|------|
| **適用場景** | 對一個主題有興趣但不確定如何開始研究；想透過對話釐清思路；需要研究指導 |
| **不適用場景** | 已有明確的研究問題和方法論；需要快速產出報告；只需要文獻或事實查核 |
| **典型使用者** | 初次接觸研究的碩士生、轉換研究領域的學者、構思研究提案的博士生 |
| **預期產出** | Research Plan Summary，含萃取的 INSIGHT、研究問題方向、方法論建議 |
| **預期對話輪數** | 8-15 輪（多輪對話是核心特色） |
| **啟用 Agent 數** | 2-3 個（socratic_mentor + research_question + devils_advocate 視情況） |
| **所需時間** | 較長，但重點在思考過程而非產出速度 |

**觸發範例**：
```
"引導我研究高等教育的主題"
"Guide my research on educational technology"
"幫我想清楚我的論文方向"
"Help me think through my research topic"
```

---

## 常見誤選場景

| 使用者說的 | 他們可能真正需要的 | 建議模式 | 原因 |
|-----------|------------------|---------|------|
| 「幫我做一個完整的文獻回顧」 | 完整報告（含分析和結論） | `full`，非 `lit-review` | lit-review 只產出書目和綜合，不含原創分析 |
| 「快速查一下 X 的情況」 | 事實查核 | `fact-check`，非 `quick` | 如果只需要驗證特定事實，fact-check 更精準 |
| 「我想研究 X」（但說不清楚想知道什麼） | 研究思路釐清 | `socratic`，非 `full` | full mode 的 Phase 1 也能互動，但 socratic 更深入 |
| 「幫我改這篇論文」 | 論文修改指導 | `review`，非 `full` | 已有文本，需要審查而非從零研究 |
| 「我需要 APA 格式的參考文獻」 | 文獻格式化 | `lit-review`，非 `full` | 如果只需要文獻列表和格式，不需要完整研究 |
| 「幫我想一個研究題目」 | 研究方向探索 | `socratic` | 最適合沒有明確方向的使用者 |

---

## 模式間的銜接

### 常見銜接路徑

```
socratic → full        Socratic 完成後想要完整研究
socratic → academic-paper (plan)   Socratic 完成後直接寫論文
lit-review → full      文獻回顧後想要做完整分析
fact-check → full      事實查核後發現需要深入研究
quick → full           快速研究後覺得值得深入
review → full          審查後發現需要重新研究
```

### deep-research 與 academic-paper 的模式對照

| deep-research 模式 | 產出 | 銜接到 academic-paper 模式 | 說明 |
|-------------------|------|--------------------------|------|
| `full` | 完整研究報告 | `full` 或 `revision` | 研究完成，進入論文寫作 |
| `socratic` | Research Plan Summary | `plan` | 研究方向確定，規劃論文結構 |
| `lit-review` | 註釋書目 + 綜合 | `full`（以文獻為基礎） | 文獻回顧完成，開始寫論文 |
| `quick` | 研究簡報 | `plan`（需要擴充） | 初步探索完成，規劃完整論文 |
| `review` | 審查報告 | 不銜接 | 審查結束，修改原論文 |
| `fact-check` | 驗證報告 | 不銜接 | 查核結束 |

### deep-research 與 academic-paper-reviewer 的模式對照

| deep-research `review` mode | academic-paper-reviewer |
|------------------------------|------------------------|
| 3 agents（Editor + DA + Ethics） | 專屬論文審查 skill |
| 適合任何文本的品質審查 | 專為學術論文設計的審稿流程 |
| 產出 Editorial Verdict | 產出結構化審稿意見 |
| 推薦用於：初稿粗篩、非學術文本 | 推薦用於：投稿前正式審查 |

---

## 完整學術研究 Pipeline

```
Step 1: deep-research (socratic/full)
          ↓ Research Plan / Full Report
Step 2: academic-paper (plan/full)
          ↓ 論文草稿
Step 3: academic-paper-reviewer (full/guided)
          ↓ 審稿意見
Step 4: academic-paper (revision)
          ↓ 修訂版論文
Step 5: [重複 Step 3-4 直到通過]
          ↓ 最終版論文
```
