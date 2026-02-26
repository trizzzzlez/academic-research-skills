# Editorial Decision Template

本模板供 `editorial_synthesizer_agent` 使用，產出最終的 Editorial Decision Package。

---

## Template

```markdown
# Editorial Decision

## Manuscript Information
- **Title**: [論文標題]
- **Manuscript ID**: [如有]
- **Submission Date**: [投稿日期]
- **Decision Date**: [決定日期]
- **Review Round**: [第 N 輪]

---

## Decision *

### [Accept / Minor Revision / Major Revision / Reject]

[如果是 Reject，標註子類型：Out of Scope / Fundamental Flaw / Insufficient Contribution / Premature / Resubmit Encouraged]

---

## Reviewer Summary

| Reviewer | Role | Recommendation | Confidence |
|----------|------|---------------|------------|
| EIC | [期刊主編身份] | [Accept/Minor/Major/Reject] | [1-5] |
| Reviewer 1 | [方法論專家身份] | [Accept/Minor/Major/Reject] | [1-5] |
| Reviewer 2 | [領域專家身份] | [Accept/Minor/Major/Reject] | [1-5] |
| Reviewer 3 | [跨領域專家身份] | [Accept/Minor/Major/Reject] | [1-5] |

---

## Consensus Analysis *

### Points of Agreement（共識）

**[CONSENSUS-4]**（所有 reviewer 同意）：
1. [共識內容 — 引用各 reviewer 的相關段落]
2. [...]

**[CONSENSUS-3]**（3/4 reviewer 同意）：
1. [共識內容 — 標註哪 3 位同意，哪 1 位有不同看法]
2. [...]

### Points of Disagreement（分歧）

**分歧 1: [議題名稱]**
- **R[X] 觀點**：[具體觀點，引用報告]
- **R[Y] 觀點**：[具體觀點，引用報告]
- **分歧類型**：[觀點差異 / 嚴重度分歧 / 存在分歧 / 方向分歧]
- **Editor's Resolution**：[仲裁結果]
- **Resolution Rationale**：[仲裁理由 — 基於證據/專業/保守原則]

**分歧 2: [議題名稱]**
- [同上格式]

---

## Decision Rationale *

[200-300 字，說明基於什麼做出這個決定]

要求：
- 引用具體的 reviewer 意見
- 說明分歧是如何被解決的
- 解釋為什麼選擇這個決定而非更嚴格或更寬鬆的決定
- 如果是 Reject，說明為什麼修改也無法挽救

---

## Required Revisions *（必須修改）

[只有 Minor Revision 和 Major Revision 需要此段落]

| # | 修改項目 | 來源 Reviewer | 嚴重度 | 章節 | 預估工時 |
|---|---------|-------------|--------|------|---------|
| R1 | [描述] | [EIC/R1/R2/R3] | Critical | [章節名] | [X 天] |
| R2 | [描述] | [來源] | Critical/Major | [章節名] | [X 天] |
| R3 | [描述] | [來源] | Major | [章節名] | [X 天] |
...

### 必修項目說明

**R1: [標題]**
- **問題**：[具體描述]
- **來源**：[哪位 reviewer 提出，引用報告段落]
- **要求**：[具體要怎麼改]
- **驗收標準**：[改完後怎麼確認問題已解決]

**R2: [標題]**
- [同上格式]

---

## Suggested Revisions（建議修改）

| # | 修改項目 | 來源 Reviewer | 優先順序 | 章節 | 預估效果 |
|---|---------|-------------|---------|------|---------|
| S1 | [描述] | [來源] | P2 | [章節名] | [改善什麼] |
| S2 | [描述] | [來源] | P2/P3 | [章節名] | [改善什麼] |
...

---

## Revision Roadmap *

### Priority 1 — 結構性修改（預估總工時：X 天）
- [ ] R1: [任務描述 — 關聯到上方 Required Revisions]
- [ ] R2: [任務描述]
- [ ] R3: [任務描述]

### Priority 2 — 內容補充（預估總工時：X 天）
- [ ] S1: [任務描述]
- [ ] S2: [任務描述]

### Priority 3 — 文字與格式（預估總工時：X 天）
- [ ] [來自各 reviewer 的 Minor Issues 合併]
- [ ] [語言潤色項目]
- [ ] [引用格式修正]

### 總預估工時
- **Minor Revision**: [X-Y 天]
- **Major Revision**: [X-Y 週]

---

## Revision Deadline

- **建議截止日期**：[日期]
- **依據**：[Minor: 2-4 週 / Major: 6-8 週]
- **延期政策**：[如需延期，請在截止前 1 週通知]

---

## Response Letter Instructions

請使用 `templates/revision_response_template.md` 的格式，逐項回應所有 reviewer 意見。

**必須包含**：
1. 對每項 Required Revision 的回應和修改說明
2. 對每項 Suggested Revision 的回應（採納或說明不採納的理由）
3. 修改標示（在修訂稿中以顏色或追蹤修訂標示所有變更）
4. 新增頁碼/段落的對照表

---

## Closing

[正式結尾，根據決定類型調整語氣]

### Accept 版本
We are pleased to accept your manuscript for publication in [期刊名]. [如有，附帶 minor suggestions]

### Minor Revision 版本
We invite you to submit a revised version of your manuscript, addressing the points raised by the reviewers. We look forward to receiving your revision within [期限].

### Major Revision 版本
We encourage you to carefully consider the reviewers' comments and submit a substantially revised manuscript. Please note that the revised manuscript will undergo another round of review.

### Reject 版本
After careful consideration, we are unable to accept your manuscript for publication in [期刊名]. We appreciate the effort you have put into this work and hope the reviewers' comments will be helpful for future development of this research.

[如果適合，推薦替代期刊]

---

## Appendix: Full Reviewer Reports

[附上 4 份完整的 reviewer 報告，供作者參考]
```

---

## 格式規範

### Revision Roadmap 的設計原則

1. **可操作性**：每一項都是具體的任務，不是抽象的建議
2. **可追溯性**：每一項都能追溯到具體的 reviewer 意見
3. **優先排序**：Priority 1 > 2 > 3，作者可以按順序處理
4. **時間估計**：幫助作者規劃修改時程
5. **相容性**：格式可直接作為 `academic-paper` revision mode 的輸入

### 嚴重度與優先順序的對應

| 嚴重度 | 優先順序 | 修改類型 |
|--------|---------|---------|
| Critical | P1 | Required Revision |
| Major | P1/P2 | Required / Strongly Suggested |
| Minor | P2/P3 | Suggested |
| Cosmetic | P3 | Optional |
