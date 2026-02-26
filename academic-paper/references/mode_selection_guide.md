# Mode Selection Guide — 模式選擇指南

本指南幫助使用者和 intake_agent 選擇最適合的 operational mode。

---

## 模式選擇流程圖

```
用戶輸入 →
│
├── 已有完整研究？
│   ├── Yes → 要完整論文？
│   │   ├── Yes ─────────────────────────→ full mode
│   │   └── No → 只要大綱？
│   │       ├── Yes ─────────────────────→ outline-only mode
│   │       └── No → 只要摘要？
│   │           ├── Yes ──────────────────→ abstract-only mode
│   │           └── No → 只要文獻回顧？
│   │               ├── Yes ─────────────→ lit-review mode
│   │               └── No ──────────────→ full mode
│   │
│   └── No → 想被引導思考？
│       ├── Yes ─────────────────────────→ plan mode ★ NEW
│       └── No ──────────────────────────→ full mode（Phase 0 會訪談）
│
├── 已有論文要修訂？ ──────────────────────→ revision mode
├── 只要轉換格式？ ────────────────────────→ format-convert mode
└── 只要檢查引用？ ────────────────────────→ citation-check mode
```

---

## 各模式詳細說明

### full mode — 完整論文撰寫

**適用場景**：
- 使用者有明確的研究問題和（部分）材料
- 需要從頭到尾產出完整論文
- 包含所有階段：訪談 → 文獻 → 架構 → 論證 → 撰寫 → 引用 → 審查 → 格式化

**不適用場景**：
- 使用者對研究方向完全沒有想法（→ 先用 deep-research）
- 只需要特定段落（→ 用其他專門 mode）

**預期產出**：完整論文草稿 + 參考文獻 + 雙語摘要 + 審查報告
**預期時間**：長（8 個 Phase 完整執行）
**使用 Agent**：全部 9 個 + socratic_mentor（如需要）

---

### outline-only mode — 大綱產出

**適用場景**：
- 只需要論文架構和大綱
- 要提交給指導教授審查的 proposal
- 需要快速規劃論文結構

**不適用場景**：
- 需要完整論文內容（→ full mode）
- 需要被引導思考（→ plan mode）

**預期產出**：詳細大綱 + 證據配置 + 字數分配
**預期時間**：短（Phase 0-2）
**使用 Agent**：intake → literature_strategist → structure_architect

---

### plan mode — 逐章節引導規劃 ★ NEW

**適用場景**：
- 使用者有想法但還不夠清楚
- 想要被引導思考每個章節的內容
- 第一次寫學術論文的新手
- 想在動筆前把每個部分想清楚
- 剛從 deep-research 拿到材料，需要轉化為論文規劃

**不適用場景**：
- 已經很清楚要寫什麼（→ full mode 更快）
- 只需要大綱不需要深度思考（→ outline-only mode）
- 時間緊迫需要快速產出（→ full mode）

**預期產出**：Chapter Plan + INSIGHT Collection
**預期時間**：中等（Step 0-3，約 20-30 輪對話）
**使用 Agent**：intake → socratic_mentor → structure_architect → argument_builder

**後續銜接**：
- Chapter Plan → full mode（產出完整論文）
- Chapter Plan → academic-paper-reviewer（審查規劃）

---

### revision mode — 論文修訂

**適用場景**：
- 已有完成的論文草稿
- 收到審稿意見需要修訂
- 自己覺得某些段落需要改善

**不適用場景**：
- 沒有現成的論文草稿（→ full mode）
- 只需要檢查引用格式（→ citation-check mode）

**預期產出**：修訂後的論文 + 修訂說明（tracked changes）
**預期時間**：中等
**使用 Agent**：peer_reviewer → draft_writer → citation_compliance

**前提**：使用者必須提供現有論文內容

---

### abstract-only mode — 摘要撰寫

**適用場景**：
- 論文已完成，只需要摘要
- 需要提交研討會的摘要
- 需要雙語摘要

**不適用場景**：
- 沒有論文內容可以摘要（→ full mode 或 plan mode）

**預期產出**：雙語摘要（zh-TW + EN）+ 關鍵詞
**預期時間**：短
**使用 Agent**：intake → abstract_bilingual

---

### lit-review mode — 文獻回顧

**適用場景**：
- 需要特定主題的文獻回顧
- 準備論文的 Literature Review 章節
- 需要系統性搜尋策略和文獻矩陣

**不適用場景**：
- 需要完整論文（→ full mode）
- 需要深入的研究調查（→ deep-research）

**預期產出**：註解書目 + 文獻矩陣 + 綜合評析
**預期時間**：中等
**使用 Agent**：intake → literature_strategist

---

### format-convert mode — 格式轉換

**適用場景**：
- 已有論文內容，需要轉換格式
- Markdown → LaTeX / DOCX / PDF
- 需要符合特定期刊的格式要求

**不適用場景**：
- 沒有現成內容（→ full mode）
- 需要修改內容（→ revision mode）

**預期產出**：目標格式的文件
**預期時間**：短
**使用 Agent**：formatter 單獨使用

---

### citation-check mode — 引用檢查

**適用場景**：
- 已有論文，只需要檢查引用格式
- 投稿前的最後檢查
- 切換引用格式（如 APA → IEEE）

**不適用場景**：
- 沒有現成的引用列表（→ full mode）
- 需要修改論文內容（→ revision mode）

**預期產出**：引用錯誤報告 + 自動修正建議
**預期時間**：短
**使用 Agent**：citation_compliance 單獨使用

---

## 從 deep-research 銜接的路徑

```
deep-research 完成
  │
  ├── deep-research (full mode) 產出：
  │   RQ Brief + Methodology Blueprint + Annotated Bibliography + Synthesis Report
  │   │
  │   ├── 想直接寫論文 ──→ academic-paper (full mode)
  │   │   intake_agent 自動偵測材料，跳過冗餘問題
  │   │
  │   └── 想先規劃再寫 ──→ academic-paper (plan mode)
  │       socratic_mentor 利用已有材料加速引導
  │
  └── deep-research (socratic mode) 產出：
      INSIGHT Collection + Synthesis Report
      │
      ├── INSIGHT 已足夠清晰 ──→ academic-paper (full mode)
      │
      └── 需要更多引導 ──→ academic-paper (plan mode)
          socratic_mentor 從 INSIGHT 繼續深化
```

## 到 academic-paper-reviewer 的銜接

```
academic-paper 完成
  │
  ├── full mode 產出完整論文 ──→ academic-paper-reviewer (full / guided)
  │   完整的同儕審查 + 修訂建議
  │
  ├── plan mode 產出 Chapter Plan ──→ academic-paper-reviewer (guided)
  │   審查規劃的可行性和完整性
  │
  └── reviewer 回饋 ──→ academic-paper (revision mode)
      根據審查意見修訂論文
```

---

## 常見誤選場景

| 使用者說 | 容易誤選 | 正確選擇 | 原因 |
|---------|---------|---------|------|
| 「幫我寫個大綱」 | outline-only | 先確認：是要簡單大綱還是深度規劃？ | 可能需要 plan mode |
| 「我想寫論文但不知道怎麼開始」 | full | plan mode | 需要引導思考 |
| 「幫我改論文」 | revision | 先確認：有沒有審稿意見？ | 可能需要 full mode 重寫 |
| 「幫我查文獻」 | lit-review | 先確認：是要論文的文獻回顧還是研究調查？ | 可能需要 deep-research |
| 「我有 deep-research 的結果，幫我寫論文」 | full（直接跳過 Phase 0） | full（但 intake 需偵測 handoff） | 需要正確匯入材料 |
| 「我想一步一步規劃論文」 | outline-only | plan mode | 需要互動式引導 |
| 「論文格式不對」 | revision | citation-check 或 format-convert | 可能只需格式修正 |

---

## 快速決策表

| 你有什麼？ | 你要什麼？ | 選這個 mode |
|-----------|-----------|------------|
| 什麼都沒有 | 完整論文 | plan mode → full mode |
| 研究問題 + 文獻 | 完整論文 | full mode |
| 研究問題 + 文獻 | 大綱 | outline-only mode |
| 模糊的想法 | 論文規劃 | plan mode |
| deep-research 結果 | 完整論文 | full mode（auto-handoff） |
| deep-research 結果 | 引導式規劃 | plan mode |
| 完成的論文 | 修訂 | revision mode |
| 完成的論文 | 摘要 | abstract-only mode |
| 完成的論文 | 格式轉換 | format-convert mode |
| 完成的論文 | 引用檢查 | citation-check mode |
