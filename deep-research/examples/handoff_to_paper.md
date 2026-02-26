# Handoff 範例：deep-research → academic-paper

本範例展示 deep-research full mode 完成研究後，如何銜接到 academic-paper 開始論文寫作。

---

## 情境設定

使用者已完成 deep-research full mode，研究主題為「AI-Assisted Quality Assurance in Higher Education: A Comparative Analysis of Implementation Strategies in East Asian Universities」。以下是研究產出摘要。

---

## deep-research 產出摘要

### 1. Research Question Brief（from research_question_agent）

```markdown
### Primary Research Question
How do East Asian universities (Taiwan, Japan, South Korea) differ in their
implementation strategies for AI-assisted quality assurance, and what factors
explain the variation in adoption patterns?

### FINER Assessment
| Criterion   | Score | Justification |
|-------------|-------|---------------|
| Feasible    | 4/5   | Public data + policy documents available |
| Interesting | 5/5   | Timely: AI policy divergence across similar systems |
| Novel       | 4/5   | Few cross-national comparisons in this space |
| Ethical     | 5/5   | No human subjects; public policy analysis |
| Relevant    | 5/5   | Directly informs HEEACT and peer agencies |
| **Average** | **4.6/5** | |

### Sub-questions
1. What AI-QA tools and frameworks have been adopted by accreditation agencies
   in Taiwan, Japan, and South Korea?
2. What institutional and policy factors facilitate or hinder AI-QA adoption?
3. To what extent do implementation outcomes align with stated policy objectives?
```

### 2. Methodology Blueprint（from research_architect_agent）

```markdown
- Paradigm: Pragmatist (comparative policy analysis)
- Method: Qualitative comparative analysis (QCA) + document analysis
- Data sources:
  - Policy documents (3 countries' QA frameworks)
  - Accreditation agency reports (HEEACT, JUAA/NIAD-QE, KCUE)
  - Published case studies and conference proceedings
- Analytical framework: Diffusion of Innovation (Rogers) +
  Institutional Isomorphism (DiMaggio & Powell)
- Validity: Triangulation across document types + member checking
  with QA practitioners
```

### 3. Annotated Bibliography（from bibliography_agent）

```markdown
23 sources identified, 18 retained after quality screening:
- 6 peer-reviewed articles (Level II-III evidence)
- 4 accreditation agency reports (Level IV)
- 3 policy documents (Level IV)
- 3 conference proceedings (Level V)
- 2 institutional case studies (Level V)

Key themes identified:
- AI adoption maturity gap (Taiwan > Korea > Japan in QA applications)
- Regulatory divergence (Japan's cautious approach vs Korea's top-down push)
- Data infrastructure as prerequisite (not just technology)
```

### 4. Synthesis Report（from synthesis_agent）

```markdown
## Core Findings

1. **Adoption patterns cluster into 3 models**:
   - Taiwan: bottom-up experimentation (agency-led pilots)
   - South Korea: top-down mandate (ministry-driven framework)
   - Japan: cautious incrementalism (voluntary guidelines)

2. **Critical success factors** (converging evidence across all 3 countries):
   - Data infrastructure maturity
   - Accreditation agency technical capacity
   - University willingness to share data
   - Clear governance framework for AI decisions

3. **Key tension**: efficiency gains vs transparency concerns
   - All 3 countries report resistance from faculty regarding "black box" decisions
   - Only Korea has attempted regulatory response (AI Ethics in Education Act 2025)

4. **Evidence gap**:
   - No rigorous outcome studies yet (all countries < 3 years into implementation)
   - Student/faculty experience data almost entirely absent

## Contradictions Identified
- Taiwan HEEACT reports "high adoption" but academic literature suggests
  most universities are still in pilot phase → definition of "adoption" varies

## Knowledge Gaps
- Impact on accreditation outcomes (pass/fail rates)
- Cost-effectiveness analysis
- Faculty perceptions and behavioral changes
```

---

## Handoff 指令

使用者完成 deep-research 後輸入：

```
現在幫我根據這個研究寫一篇論文
```

---

## academic-paper intake_agent 自動偵測

**intake_agent 偵測流程**：

```
Scanning available materials...

[DETECTED] Research Question Brief
  - Source: deep-research / research_question_agent
  - Status: Complete (FINER 4.6/5)
  - Action: SKIP academic-paper Phase 1 (topic scoping)

[DETECTED] Methodology Blueprint
  - Source: deep-research / research_architect_agent
  - Status: Complete (pragmatist QCA + document analysis)
  - Action: SKIP academic-paper Phase 2 (methodology design)
  - Note: Will integrate into Method section directly

[DETECTED] Annotated Bibliography (18 sources, APA 7.0)
  - Source: deep-research / bibliography_agent
  - Status: Complete, quality-screened
  - Action: SKIP academic-paper literature search
  - Note: Will use as foundation for Literature Review section

[DETECTED] Synthesis Report
  - Source: deep-research / synthesis_agent
  - Status: Complete (3 core findings + 1 contradiction + 2 gaps)
  - Action: SKIP academic-paper analysis phase
  - Note: Will structure Findings and Discussion sections around synthesis

Materials Assessment: COMPREHENSIVE
Recommended academic-paper mode: full (with accelerated pipeline)
Estimated sections already covered: 60-70%
Remaining work: Writing, formatting, argumentation, and polish
```

---

## 跳過的步驟和原因

| academic-paper 步驟 | 正常流程 | Handoff 後 | 原因 |
|---------------------|---------|-----------|------|
| Phase 1: Topic Scoping | intake_agent 從零釐清 | SKIPPED | RQ Brief 已完整 |
| Phase 2: Structure Planning | outline_agent 設計結構 | PARTIAL | 有 Blueprint 但需轉為論文結構 |
| Phase 3: Literature Search | literature_agent 搜尋 | SKIPPED | Bibliography 已完整 |
| Phase 4: Literature Review Writing | review_writer_agent 撰寫 | ACTIVE | 有 Synthesis 但需轉為論文語氣 |
| Phase 5: Methodology Writing | method_writer_agent 撰寫 | ACTIVE | 有 Blueprint 但需展開為完整段落 |
| Phase 6: Findings Writing | findings_writer_agent 撰寫 | ACTIVE | 有 Synthesis 但需展開論證 |
| Phase 7: Discussion Writing | discussion_writer_agent 撰寫 | ACTIVE | 需原創論述（非直接複製 Synthesis） |
| Phase 8: Intro + Conclusion | bookend_agent 撰寫 | ACTIVE | 需要根據全文撰寫 |
| Phase 9: Abstract + Formatting | format_agent 處理 | ACTIVE | 需要全文完成後產出 |
| Phase 10: Self-Review | review_agent 審查 | ACTIVE | 必須執行 |

---

## 銜接後 academic-paper 的實際工作流程

```
=== academic-paper: Accelerated Pipeline ===

Step 1: STRUCTURAL MAPPING
  [outline_agent]
  - Input: RQ Brief + Methodology Blueprint + Synthesis Report
  - Output: 完整論文大綱，每個段落標註對應的 deep-research 材料
  - 產出範例：

    I. Introduction
       - Context: AI in HE QA (from Synthesis background)
       - Problem: Cross-national variation unexplained
       - Purpose: Compare 3 East Asian models
       - RQ: [直接引用 RQ Brief]

    II. Literature Review
       - 2.1 AI in Quality Assurance (from Bibliography themes)
       - 2.2 Diffusion of Innovation framework (from Blueprint)
       - 2.3 Institutional Isomorphism (from Blueprint)
       - 2.4 East Asian HE systems comparison

    III. Methodology
       - 3.1 Research design: QCA + document analysis (from Blueprint)
       - 3.2 Case selection and data sources
       - 3.3 Analytical framework
       - 3.4 Validity and limitations

    IV. Findings
       - 4.1 Three adoption models (from Synthesis Finding 1)
       - 4.2 Critical success factors (from Synthesis Finding 2)
       - 4.3 Efficiency vs transparency tension (from Synthesis Finding 3)

    V. Discussion
       - 5.1 Theoretical implications
       - 5.2 Policy implications for accreditation agencies
       - 5.3 Practical recommendations
       - 5.4 Limitations (from Synthesis gaps + Blueprint validity)

    VI. Conclusion
       - Summary + Future research directions

Step 2: SECTION WRITING (Parallel)
  [review_writer_agent] → Literature Review
    - 基於 Annotated Bibliography 和 Synthesis，轉化為流暢的文獻回顧
    - 不是逐篇摘要，而是主題式整合

  [method_writer_agent] → Methodology
    - 將 Blueprint 展開為完整的方法論段落
    - 補充 QCA 的技術細節和程序說明

  [findings_writer_agent] → Findings
    - 將 Synthesis 的 3 個核心發現展開為有證據支持的論述
    - 每個發現附具體案例和數據
    - 處理 Synthesis 中標記的矛盾

Step 3: DISCUSSION + BOOKENDS
  [discussion_writer_agent] → Discussion
    - 原創論述：發現與理論的對話
    - 不重複 Findings，而是解釋「為什麼」
    - 整合 deep-research 的 Knowledge Gaps 為 Future Research

  [bookend_agent] → Introduction + Conclusion
    - Introduction：從宏觀背景導入具體 RQ
    - Conclusion：不引入新資訊，呼應 RQ 並展望未來

Step 4: ABSTRACT + FORMAT
  [format_agent]
    - Abstract: 150-250 字，IMRAD 結構
    - APA 7.0 全文格式化
    - Reference list 整理（基於 Bibliography + 新增引用）

Step 5: SELF-REVIEW
  [review_agent]
    - 內部一致性檢查（RQ → Method → Findings → Discussion 的邏輯鏈）
    - 引用完整性（每個 claim 有 citation）
    - 格式規範
    - 判定：Ready for submission / Needs revision
```

---

## 使用者看到的銜接體驗

**academic-paper 的開場訊息**：

> 我已經讀取了你在 deep-research 階段的完整產出，包括：
> - Research Question Brief（FINER 4.6/5）
> - Methodology Blueprint（QCA + document analysis）
> - Annotated Bibliography（18 篇已篩選來源）
> - Synthesis Report（3 核心發現 + 2 知識空白）
>
> 基於這些材料，我已經完成了論文大綱的初步規劃。以下是預計的論文結構：
> [顯示大綱]
>
> 我有兩個問題需要你確認：
> 1. 你的目標期刊是什麼？（會影響字數限制和格式要求）
> 2. 論文語言是英文還是中英雙語？
>
> 確認後我就開始撰寫。因為研究基礎已經很完整，預計可以跳過前期的探索階段，直接進入論文寫作。

---

## 注意事項

1. **不是複製貼上**：academic-paper 不會直接複製 deep-research 的產出，而是將其轉化為論文的語氣和格式
2. **可能發現新問題**：在撰寫過程中，academic-paper 的 agents 可能發現 deep-research 遺漏的點，會主動補充
3. **仍需要使用者確認**：目標期刊、語言偏好、特定格式要求等仍需使用者輸入
4. **審稿建議自動銜接**：論文完成後，可接續使用 `academic-paper-reviewer` 進行正式審查
