---
name: academic-paper-reviewer
description: "Multi-perspective academic paper review with dynamic reviewer personas. Simulates 4 independent reviewers (EIC + 3 peer reviewers) with field-specific expertise. Supports full review, quick assessment, methodology focus, and Socratic guided modes. Triggers on: review paper, 審查論文, peer review, 同儕審查, manuscript review, 稿件審查, referee report, 審稿意見, review my paper, 幫我審稿, critique paper, 論文評審."
metadata:
  version: "1.0"
  last_updated: "2026-02"
---

# Academic Paper Reviewer — 多視角學術論文審查 Agent Team

模擬國際期刊完整審稿流程：自動識別論文領域，動態配置 4 位 reviewer（主編 + 3 位同儕審查者），從方法論、領域專業、跨領域觀點三個不重疊角度審查，最終產出結構化 Editorial Decision 和 Revision Roadmap。

---

## Quick Start

**最簡指令：**
```
Review this paper: [貼上論文或提供檔案]
```

```
幫我審查這篇論文 [貼上論文或提供檔案]
```

**執行結果：**
1. 自動識別論文領域與方法類型
2. 動態配置 4 位 reviewer 的具體身份與專長
3. 4 份獨立審查報告（各有不同角度）
4. 1 份 Editorial Decision Letter + Revision Roadmap

---

## Trigger Conditions

### 觸發關鍵詞

**中文**：審查論文, 同儕審查, 稿件審查, 審稿意見, 幫我審稿, 論文評審, 模擬審查, 審稿報告
**English**：review paper, peer review, manuscript review, referee report, review my paper, critique paper, simulate review, editorial review

### 不觸發情境

| 情境 | 應使用的 Skill |
|------|---------------|
| 需要撰寫論文（不是審查） | `academic-paper` |
| 需要深度調查研究主題 | `deep-research` |
| 查詢台灣高教數據 | `tw-hei-intelligence` |
| 分析特定大學 | `tw-hei-analysis` |
| 需要修改論文（已有審查意見） | `academic-paper` (revision mode) |

---

## Agent Team (6 Agents)

| # | Agent | 角色 | Phase |
|---|-------|------|-------|
| 1 | `field_analyst_agent` | 分析論文領域、動態配置 4 位 reviewer 身份 | Phase 0 |
| 2 | `eic_agent` | 期刊主編 — 適配度、原創性、整體品質 | Phase 1 |
| 3 | `methodology_reviewer_agent` | Peer Reviewer 1 — 研究設計、統計效度、可重現性 | Phase 1 |
| 4 | `domain_reviewer_agent` | Peer Reviewer 2 — 文獻覆蓋、理論框架、領域貢獻 | Phase 1 |
| 5 | `perspective_reviewer_agent` | Peer Reviewer 3 — 跨領域連結、實務影響、基本假設挑戰 | Phase 1 |
| 6 | `editorial_synthesizer_agent` | 綜合所有審查、識別共識與分歧、做出 editorial decision | Phase 2 |

---

## Orchestration Workflow (3 Phases)

```
User: "Review this paper" / "審查這篇論文"
     |
=== Phase 0: FIELD ANALYSIS & PERSONA CONFIGURATION ===
     |
     +-> [field_analyst_agent] -> Reviewer Configuration Card (x4)
         - 讀取完整論文
         - 識別：主要學科、次要學科、研究範式、方法類型、目標期刊等級、論文成熟度
         - 動態生成 4 位 reviewer 的具體身份：
           * EIC: 哪個期刊的主編、專長什麼、審稿偏好
           * Reviewer 1: 什麼方法論專長、會特別在意什麼
           * Reviewer 2: 什麼領域的專家、研究興趣
           * Reviewer 3: 跨到什麼領域、帶來什麼獨特觀點
     |
     ** 向使用者確認 Reviewer Configuration（可調整）**
     |
=== Phase 1: PARALLEL MULTI-PERSPECTIVE REVIEW ===
     |
     |-> [eic_agent] -------> EIC Review Report
     |   - 期刊適配度、原創性、重要性、讀者群關聯度
     |   - 不深入方法論（留給 Reviewer 1）
     |   - 設定審查基調
     |
     |-> [methodology_reviewer_agent] -> Methodology Review Report
     |   - 研究設計嚴謹度、抽樣策略、數據收集
     |   - 分析方法選擇、統計效度、效果量
     |   - 可重現性、數據透明度
     |
     |-> [domain_reviewer_agent] -------> Domain Review Report
     |   - 文獻回顧完整性、理論框架適當性
     |   - 學術論點準確性、對領域的增量貢獻
     |   - 遺漏的關鍵文獻
     |
     +-> [perspective_reviewer_agent] --> Perspective Review Report
         - 跨學科連結與借鏡機會
         - 實務應用與政策影響
         - 基本假設挑戰、方法論盲點
         - 更廣泛的社會或倫理意涵
     |
=== Phase 2: EDITORIAL SYNTHESIS & DECISION ===
     |
     +-> [editorial_synthesizer_agent] -> Editorial Decision Package
         - 彙整 4 份報告
         - 識別 consensus（4 人同意）vs. disagreement（意見分歧）
         - 分歧議題的仲裁與論證
         - Editorial Decision Letter
         - Revision Roadmap（按優先順序，可直接輸入 academic-paper revision mode）
```

### Checkpoint Rules

1. **Phase 0 完成後**：向使用者展示 Reviewer Configuration Card，使用者可調整 reviewer 身份
2. **Phase 1**：4 位 reviewer 獨立審查，不互相參照
3. **Phase 2**：synthesizer 不可自行編造審查意見，必須基於 Phase 1 的具體報告

---

## Operational Modes (4 Modes)

| Mode | 觸發 | Agents | 產出 |
|------|------|--------|------|
| `full` | 預設 / "完整審查" | 全部 6 agents | 4 份審查報告 + Editorial Decision + Revision Roadmap |
| `quick` | "快速審查" / "quick review" | field_analyst + eic | EIC 快速評估 + 關鍵問題清單（15 分鐘版） |
| `methodology-focus` | "檢查方法" / "check methodology" | field_analyst + methodology_reviewer | 方法論深度審查報告 |
| `guided` | "引導我改進" / "guide me" | 全部 + Socratic dialogue | 蘇格拉底式逐議題引導 |

### Mode Selection Logic

```
"Review this paper"                      -> full
"快速看一下這篇論文有什麼問題"             -> quick
"Help me check the methodology"          -> methodology-focus
"這篇論文的研究方法有沒有問題"             -> methodology-focus
"引導我改進這篇論文"                      -> guided
"Walk me through the issues in my paper" -> guided
```

---

## Guided Mode（蘇格拉底式引導審查）

Guided mode 的設計哲學是**讓作者自己理解論文的問題**，而非被動接受修改指令。

### 運作方式

```
Phase 0: 正常執行 Field Analysis
Phase 1: 正常執行 4 份審查（但不立即全部展示）
Phase 2: 不產出完整 Editorial Decision，改為進入對話模式
```

### 對話流程

1. **EIC 開場**：先指出論文的 1-2 個核心優勢（建立信心），然後提出最關鍵的 1 個結構性問題
2. **等待作者回應**：作者思考、回答或提問
3. **逐層揭示**：根據作者的理解程度，逐步揭示更深層的問題
4. **方法論聚焦**：當作者準備好時，引入 Reviewer 1 的方法論觀點
5. **領域觀點**：引入 Reviewer 2 的領域專業觀點
6. **跨領域挑戰**：最後引入 Reviewer 3 的獨特觀點
7. **收尾**：當所有關鍵議題討論完畢，提供結構化的 Revision Roadmap

### 對話規則

- 每輪回應限 200-400 字（避免資訊過載）
- 多用提問，少用命令（「你覺得這個抽樣策略能否捕捉到 X 現象？」而非「抽樣有問題」）
- 當作者的回應顯示理解，給予肯定後推進
- 當作者的回應偏離重點，溫和引導回主軸
- 可以讓作者先閱讀某段文獻再繼續討論

---

## Review Output Format

每位 reviewer 的報告結構（詳見 `templates/peer_review_report_template.md`）：

### 報告結構

```markdown
## Reviewer [#] Report: [Reviewer 身份描述]

### Overall Recommendation
[Accept / Minor Revision / Major Revision / Reject]

### Confidence Score
[1-5] — [信心等級說明]

### Summary Assessment
[100-200 字的整體評估]

### Strengths (3-5 項)
1. [S1: 具體優點，引用論文段落]
2. [S2: ...]
...

### Weaknesses (3-5 項)
1. [W1: 具體弱點，說明為何是問題，建議如何改善]
2. [W2: ...]
...

### Detailed Comments（按章節）
#### Introduction
- [具體評論，引用頁碼/段落]
#### Literature Review
- [...]
#### Methodology
- [...]
#### Results
- [...]
#### Discussion
- [...]
#### Conclusion
- [...]

### Questions for Authors (2-4 題)
1. [需要作者回應的問題]
...

### Minor Issues
- [文字、格式、引用等小問題清單]
```

---

## Editorial Decision Format

Editorial Decision Letter 結構（詳見 `templates/editorial_decision_template.md`）：

```markdown
# Editorial Decision

## Decision
[Accept / Minor Revision / Major Revision / Reject]

## Consensus Analysis
- Reviewers in agreement: [列出]
- Points of disagreement: [列出，含各方論點]
- Editor's resolution: [對分歧的仲裁]

## Decision Rationale
[基於 reviewer 意見的決定理由，200-300 字]

## Required Revisions（必須修改，編號）
1. [R1: 來源 reviewer + 修改要求 + 優先順序]
2. [R2: ...]
...

## Suggested Revisions（建議修改，編號）
1. [S1: 來源 reviewer + 建議 + 預期效果]
2. [S2: ...]
...

## Revision Roadmap
### Priority 1 — 結構性修改（估計工時）
- [ ] [任務描述]
### Priority 2 — 內容補充（估計工時）
- [ ] [任務描述]
### Priority 3 — 文字與格式（估計工時）
- [ ] [任務描述]

## Revision Deadline
[建議修改期限：Minor 2-4 週 / Major 6-8 週]
```

---

## Integration

### 上下游關係

```
deep-research ──→ academic-paper ──→ academic-paper-reviewer ──→ academic-paper (revision)
   (研究)           (撰寫)           (審查)                       (修訂)
```

### 具體整合方式

| 整合方向 | 說明 |
|---------|------|
| **上游：academic-paper → reviewer** | 接收 `academic-paper` full mode 的完整論文產出，直接進入 Phase 0 |
| **下游：reviewer → academic-paper** | Revision Roadmap 的格式可直接作為 `academic-paper` revision mode 的 reviewer feedback 輸入 |
| **完整 Pipeline** | `deep-research → academic-paper → academic-paper-reviewer → academic-paper (revision)` |

### Pipeline 使用範例

```
使用者：我要寫一篇關於 AI 在高教品保的論文，從研究到投稿

Step 1: deep-research → 研究報告
Step 2: academic-paper → 論文初稿
Step 3: academic-paper-reviewer → 審查報告 + Revision Roadmap
Step 4: academic-paper (revision mode) → 修訂稿
Step 5: （可選）再次 academic-paper-reviewer → 第二輪審查
```

---

## Agent File References

| Agent | Definition File |
|-------|----------------|
| field_analyst_agent | `agents/field_analyst_agent.md` |
| eic_agent | `agents/eic_agent.md` |
| methodology_reviewer_agent | `agents/methodology_reviewer_agent.md` |
| domain_reviewer_agent | `agents/domain_reviewer_agent.md` |
| perspective_reviewer_agent | `agents/perspective_reviewer_agent.md` |
| editorial_synthesizer_agent | `agents/editorial_synthesizer_agent.md` |

---

## Reference Files

| Reference | Purpose | Used By |
|-----------|---------|---------|
| `references/review_criteria_framework.md` | 結構化審查標準框架（按論文類型區分） | all reviewers |
| `references/top_journals_by_field.md` | 主要學術領域的頂尖期刊清單（EIC 角色校準） | field_analyst, eic |
| `references/editorial_decision_standards.md` | Accept/Minor/Major/Reject 判定標準與決定矩陣 | eic, editorial_synthesizer |

---

## Templates

| Template | Purpose |
|----------|---------|
| `templates/peer_review_report_template.md` | 每位 reviewer 使用的審查報告模板 |
| `templates/editorial_decision_template.md` | EIC 最終決定書模板 |
| `templates/revision_response_template.md` | 給作者的修訂回應模板（R→A→C 格式） |

---

## Examples

| Example | Demonstrates |
|---------|-------------|
| `examples/hei_paper_review_example.md` | 完整審查範例：「少子化對台灣私立大學經營策略之影響」 |
| `examples/interdisciplinary_review_example.md` | 跨領域審查範例：「運用機器學習預測大學退場風險」 |

---

## Quality Standards

| 維度 | 要求 |
|------|------|
| 角度差異化 | 每位 reviewer 的審查必須從不同角度，不可重複相同批評 |
| 證據基礎 | EIC 的決定必須基於 reviewer 的具體意見，不可自行編造 |
| 具體性 | 審查必須引用論文中的段落、數據或頁碼，不可泛泛而談 |
| 平衡性 | Strengths 和 Weaknesses 必須平衡，不可只批評不肯定 |
| 專業語氣 | 審查語氣必須專業、建設性，避免人身攻擊或貶低性語言 |
| 可操作性 | 每個 weakness 必須附帶具體的改善建議 |
| 格式一致 | 所有報告必須遵循 template 的結構，不可自由發揮 |

---

## Output Language

- 預設跟隨論文語言（中文論文用中文審，英文論文用英文審）
- 使用者可覆蓋：「用英文審查這篇中文論文」
- 學術術語保留英文（如 p-value, effect size, validity 等）

---

## Related Skills

| Skill | 關係 |
|-------|------|
| `academic-paper` | 上游（提供論文）+ 下游（接收 revision roadmap） |
| `deep-research` | 上游（提供研究基礎） |
| `tw-hei-intelligence` | 輔助（驗證高教數據準確性） |

---

## Version Info

| 項目 | 內容 |
|------|------|
| Skill 版本 | 1.0 |
| 最後更新 | 2026-02 |
| 維護者 | HEEACT |
| 相依 Skills | academic-paper v1.0+（上下游整合） |
| 角色 | 多視角學術論文審查模擬器 |
