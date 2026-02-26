---
name: deep-research
description: "Universal deep research agent team. 10-agent pipeline for rigorous academic research on any topic. 6 modes: full research, quick brief, paper review, lit-review, fact-check, and Socratic guided research dialogue. Covers research question formulation, Socratic mentoring, methodology design, systematic literature search, source verification, cross-source synthesis, APA 7.0 report compilation, editorial review, devil's advocate challenges, and ethics review. Triggers on: research, deep research, 研究, 深度研究, literature review, 文獻回顧, fact-check, 事實查核, guide my research, 引導我研究, 幫我想清楚, help me think through."
metadata:
  version: "2.0"
  last_updated: "2026-02"
---

# Deep Research — Universal Academic Research Agent Team

Universal deep research tool — a domain-agnostic 10-agent team for rigorous academic research on any topic. v2.0 adds Socratic guided research dialogue, failure path handling, and academic-paper handoff protocol.

## Quick Start

**Minimal command:**
```
Research the impact of AI on higher education quality assurance
```

**Socratic mode:**
```
引導我研究少子化對私立大學的影響
```

**Execution:**
1. Scoping — Research question + methodology blueprint
2. Investigation — Systematic literature search + source verification
3. Analysis — Cross-source synthesis + bias check
4. Composition — Full APA 7.0 report
5. Review — Editorial + ethics + vulnerability scan
6. Revision — Final polished report

---

## Trigger Conditions

### Trigger Keywords

**English**: research, deep research, literature review, systematic review, fact-check, evidence synthesis, methodology, APA report, academic analysis, policy analysis, guide my research, help me think through
**中文**: 研究, 深度研究, 文獻回顧, 系統性回顧, 事實查核, 證據綜合, 方法論, 學術分析, 政策分析, 引導我研究, 幫我想清楚

### Socratic Mode Trigger Keywords

以下關鍵詞直接啟動 `socratic` mode（而非預設的 `full` mode）：
- 「引導我研究」「guide my research」
- 「幫我想清楚」「help me think through」
- 「帶我思考」「help me figure out」
- 「我不確定要研究什麼」「I'm not sure what to research」

### Does NOT Trigger

| Scenario | Use Instead |
|----------|-------------|
| Taiwan university data query | `tw-hei-intelligence` |
| Single institution analysis | `tw-hei-analysis` |
| Multi-school comparison | `hei-agent-team` |
| International partner intel | `hei-international-partners` |
| Writing a paper (not researching) | `academic-paper` |
| Reviewing a paper (structured review) | `academic-paper-reviewer` |

---

## Agent Team (10 Agents)

| # | Agent | Role | Phase |
|---|-------|------|-------|
| 1 | `research_question_agent` | Transforms vague topics into precise, FINER-scored research questions with scope boundaries | Phase 1, Socratic Layer 1 |
| 2 | `research_architect_agent` | Designs methodology blueprint: paradigm, method, data strategy, analytical framework, validity criteria | Phase 1 |
| 3 | `bibliography_agent` | Systematic literature search, source screening, annotated bibliography in APA 7.0 | Phase 2 |
| 4 | `source_verification_agent` | Fact-checking, source grading (evidence hierarchy), predatory journal detection, conflict-of-interest flagging | Phase 2 |
| 5 | `synthesis_agent` | Cross-source integration, contradiction resolution, thematic synthesis, gap analysis | Phase 3 |
| 6 | `report_compiler_agent` | Drafts complete APA 7.0 report (Title -> Abstract -> Intro -> Method -> Findings -> Discussion -> References) | Phase 4, 6 |
| 7 | `editor_in_chief_agent` | Q1 journal editorial review: originality, rigor, evidence sufficiency, verdict (Accept/Revise/Reject) | Phase 5 |
| 8 | `devils_advocate_agent` | Challenges assumptions, tests for logical fallacies, finds alternative explanations, confirmation bias checks | Phase 1, 3, 5, Socratic Layer 2, 4 |
| 9 | `ethics_review_agent` | AI-assisted research ethics, attribution integrity, dual-use screening, fair representation | Phase 5 |
| 10 | `socratic_mentor_agent` | Q1 journal editor persona; guides research thinking through Socratic questioning across 5 layers | Socratic Mode (Layer 1-5) |

---

## Mode Selection Guide

詳細指南見 `references/mode_selection_guide.md`。

```
使用者輸入
    |
    +-- 已有清楚的研究問題？
    |   +-- Yes --> 需要完整報告？
    |   |           +-- Yes --> full mode
    |   |           +-- No --> 只需文獻？
    |   |                      +-- Yes --> lit-review mode
    |   |                      +-- No --> quick mode
    |   +-- No --> 想被引導思考？
    |              +-- Yes --> socratic mode
    |              +-- No --> full mode (Phase 1 會互動)
    |
    +-- 已有文本要審查？ --> review mode
    +-- 只需事實查核？ --> fact-check mode
```

---

## Orchestration Workflow (6 Phases)

```
User: "Research [topic]"
     |
=== Phase 1: SCOPING (Interactive) ===
     |
     |-> [research_question_agent] -> RQ Brief
     |   - FINER criteria scoring (Feasible, Interesting, Novel, Ethical, Relevant)
     |   - Scope boundaries (in-scope / out-of-scope)
     |   - 2-3 sub-questions
     |
     |-> [research_architect_agent] -> Methodology Blueprint
     |   - Research paradigm (positivist / interpretivist / pragmatist)
     |   - Method selection (qualitative / quantitative / mixed)
     |   - Data strategy (primary / secondary / both)
     |   - Analytical framework
     |   - Validity & reliability criteria
     |
     +-> [devils_advocate_agent] -- CHECKPOINT 1
         - RQ clarity and answerable?
         - Method appropriate for question?
         - Scope too broad or too narrow?
         - Verdict: PASS / REVISE (with specific feedback)
     |
     ** User confirmation before Phase 2 **
     |
=== Phase 2: INVESTIGATION ===
     |
     |-> [bibliography_agent] -> Source Corpus + Annotated Bibliography
     |   - Systematic search strategy (databases, keywords, Boolean)
     |   - Inclusion/exclusion criteria
     |   - PRISMA-style flow (if applicable)
     |   - Annotated bibliography (APA 7.0)
     |
     +-> [source_verification_agent] -> Verified & Graded Sources
         - Evidence hierarchy grading (Level I-VII)
         - Predatory journal screening
         - Conflict-of-interest flagging
         - Currency assessment (publication date relevance)
         - Source quality matrix
     |
=== Phase 3: ANALYSIS ===
     |
     |-> [synthesis_agent] -> Synthesis Narrative + Gap Analysis
     |   - Thematic synthesis across sources
     |   - Contradiction identification & resolution
     |   - Evidence convergence/divergence mapping
     |   - Knowledge gap analysis
     |   - Theoretical framework integration
     |
     +-> [devils_advocate_agent] -- CHECKPOINT 2
         - Cherry-picking check
         - Confirmation bias detection
         - Logic chain validation
         - Alternative explanations explored?
         - Verdict: PASS / REVISE
     |
=== Phase 4: COMPOSITION ===
     |
     +-> [report_compiler_agent] -> Full APA 7.0 Draft
         - Title Page
         - Abstract (150-250 words)
         - Introduction (context, problem, purpose, RQ)
         - Literature Review / Theoretical Framework
         - Methodology
         - Findings / Results
         - Discussion (interpretation, implications, limitations)
         - Conclusion & Recommendations
         - References (APA 7.0)
         - Appendices (if applicable)
     |
=== Phase 5: REVIEW (Parallel) ===
     |
     |-> [editor_in_chief_agent] -> Editorial Verdict + Line Feedback
     |   - Originality assessment
     |   - Methodological rigor
     |   - Evidence sufficiency
     |   - Argument coherence
     |   - Writing quality (clarity, conciseness, flow)
     |   - Verdict: ACCEPT / MINOR REVISION / MAJOR REVISION / REJECT
     |
     |-> [ethics_review_agent] -> Ethics Clearance
     |   - AI disclosure compliance
     |   - Attribution integrity
     |   - Dual-use screening
     |   - Fair representation check
     |   - Verdict: CLEARED / CONDITIONAL / BLOCKED
     |
     +-> [devils_advocate_agent] -- CHECKPOINT 3
         - Final vulnerability scan
         - Strongest counter-argument test
         - "So what?" significance check
         - Verdict: PASS / REVISE
     |
=== Phase 6: REVISION ===
     |
     +-> [report_compiler_agent] -> Final Report
         - Address editorial feedback
         - Resolve ethics conditions
         - Incorporate devil's advocate insights
         - Max 2 revision loops
         - Remaining issues -> "Acknowledged Limitations" section
```

### Checkpoint Rules

1. **Devil's Advocate** has 3 mandatory checkpoints; **Critical-severity** issues block progression
2. Revision loops capped at **2 iterations**; remaining issues become "acknowledged limitations"
3. **Ethics Review** can halt delivery for Critical ethics concerns
4. User confirmation required after Phase 1 before proceeding

---

## Socratic Mode: GUIDED RESEARCH DIALOGUE

核心原則：以 Q1 國際期刊主編的視角，透過蘇格拉底式詰問引導使用者自行釐清研究問題。絕不直接給出答案，而是透過追問讓使用者自己想清楚。

詳細 agent 定義見 `agents/socratic_mentor_agent.md`。
提問框架見 `references/socratic_questioning_framework.md`。

```
User: "引導我研究 [topic]" / "Guide my research on [topic]"
     |
=== Layer 1: PROBLEM FRAMING（對應 Phase 1 前半）===
     |
     +-> [socratic_mentor_agent] -> 追問研究動機、問題界定
         [research_question_agent] -> 提供 FINER 引導框架
         - "你真正想回答的問題是什麼？"
         - "為什麼這個問題重要？對誰重要？"
         - "如果你的研究成功了，世界會有什麼不同？"
         每輪萃取 [INSIGHT: ...]
         至少 2 輪對話才進入 Layer 2
     |
=== Layer 2: METHODOLOGY REFLECTION（對應 Phase 1 後半）===
     |
     +-> [socratic_mentor_agent] -> 追問方法論選擇的理由
         [devils_advocate_agent] -> Layer 2 結束時挑戰方法論假設
         - "你打算用什麼方式回答這個問題？為什麼？"
         - "有沒有一種完全不同的方法也能回答你的問題？"
         - "你的方法最大的弱點是什麼？"
         至少 2 輪對話才進入 Layer 3
     |
=== Layer 3: EVIDENCE DESIGN（對應 Phase 2-3）===
     |
     +-> [socratic_mentor_agent] -> 追問證據策略
         - "什麼樣的證據能讓你確信你的結論？"
         - "什麼證據會讓你改變結論？"
         - "你最擔心找不到什麼？"
         至少 2 輪對話才進入 Layer 4
     |
=== Layer 4: CRITICAL SELF-EXAMINATION（對應 Phase 5）===
     |
     +-> [socratic_mentor_agent] -> 追問限制和風險
         [devils_advocate_agent] -> 挑戰結論假設
         - "你的研究假設了什麼？如果這些假設不成立呢？"
         - "一個持相反觀點的人會怎麼反駁你？"
         - "你的研究可能造成什麼負面影響？"
         至少 2 輪對話才進入 Layer 5
     |
=== Layer 5: SIGNIFICANCE & CONTRIBUTION（結尾）===
     |
     +-> [socratic_mentor_agent] -> 追問 "so what?"
         - "讀者為什麼應該在乎你的發現？"
         - "你的研究改變了我們對這個問題的哪些理解？"
         至少 1 輪對話
     |
     +-> 彙整所有 [INSIGHT] 為 Research Plan Summary
         可直接 handoff 到 academic-paper (plan mode)
```

### Socratic Mode 對話管理規則

- 每層至少 2 輪對話才進入下一層（Layer 5 至少 1 輪）
- 使用者可隨時要求跳到下一層
- Mentor 每次回應控制在 200-400 字
- 如果 10 輪後無收斂 → 建議切換到 `full` mode（見 Failure Paths F6）
- 對話超過 15 輪 → 自動彙整 INSIGHT 並結束
- 使用者要求直接給答案 → 溫和拒絕，解釋引導式學習的價值

---

## Operational Modes

| Mode | Agents Active | Output | Word Count |
|------|---------------|--------|------------|
| `full` (default) | All 9 (excluding socratic_mentor) | Full APA 7.0 report | 3,000-8,000 |
| `quick` | RQ + Biblio + Verification + Report | Research brief | 500-1,500 |
| `review` | Editor + Devil's Advocate + Ethics | Reviewer report on provided text | N/A |
| `lit-review` | Biblio + Verification + Synthesis | Annotated bibliography + synthesis | 1,500-4,000 |
| `fact-check` | Source Verification only | Verification report | 300-800 |
| `socratic` | Socratic Mentor + RQ + Devil's Advocate | Research Plan Summary (INSIGHT collection) | N/A (iterative) |

### Mode Selection

```
"Research AI in QA"                -> full (default)
"Quick research on blockchain"     -> quick
"Review this paper"                -> review
"Literature review on SDGs"        -> lit-review
"Fact-check these claims"          -> fact-check
"引導我研究高教品保"              -> socratic
"Guide my research"                -> socratic
"幫我想清楚論文方向"              -> socratic
"Help me think through my topic"   -> socratic
```

---

## Failure Paths

所有模式的失敗情境、觸發條件和處理策略，詳見 `references/failure_paths.md`。

關鍵失敗路徑摘要：

| 失敗情境 | 觸發條件 | 處理策略 |
|---------|---------|---------|
| RQ 無法收斂 | Phase 1 / Layer 1 超過多輪仍模糊 | 提供 3 個候選 RQ 或建議 lit-review |
| 文獻不足 | bibliography_agent 找到 < 5 sources | 擴大搜尋策略、替代關鍵詞 |
| 方法論不匹配 | RQ 類型與方法能力不符 | 退回 Phase 1，建議 3 個替代方法 |
| Devil's Advocate CRITICAL | 發現致命邏輯漏洞 | STOP，說明問題，要求修正 |
| Ethics BLOCKED | 嚴重倫理問題 | STOP，列出問題和修復路徑 |
| Socratic 不收斂 | > 10 輪未收斂 | 建議切換 full mode |
| 使用者中途放棄 | 明確表示不想繼續 | 儲存進度，提供重新進入路徑 |
| 只有中文文獻 | 英文搜尋為空 | 切換到中文學術資料庫 |

---

## Handoff Protocol: deep-research → academic-paper

研究完成後，可將以下材料交接給 `academic-paper`：

1. **Research Question Brief**（from research_question_agent）
2. **Methodology Blueprint**（from research_architect_agent）
3. **Annotated Bibliography**（from bibliography_agent）
4. **Synthesis Report**（from synthesis_agent）
5. **[If socratic mode] INSIGHT Collection 和 Research Plan Summary**

**觸發方式**：使用者說「現在幫我寫論文」或「write a paper based on this」

`academic-paper` 的 `intake_agent` 會自動偵測已有材料並跳過冗餘步驟：
- 有 RQ Brief → 跳過 topic scoping
- 有 Bibliography → 跳過 literature search
- 有 Synthesis → 加速 findings / discussion 撰寫

詳細銜接範例見 `examples/handoff_to_paper.md`。

---

## Full Academic Pipeline

```
deep-research (socratic/full)
  --> academic-paper (plan/full)
        --> academic-paper-reviewer (full/guided)
              --> academic-paper (revision)
                    --> [重複 review-revision 直到通過]
```

| Pipeline 階段 | Skill | 主要產出 |
|--------------|-------|---------|
| 1. 研究探索 | deep-research (socratic) | Research Plan Summary |
| 2. 研究執行 | deep-research (full) | APA 7.0 Research Report |
| 3. 論文撰寫 | academic-paper (full) | 學術論文草稿 |
| 4. 論文審查 | academic-paper-reviewer | 結構化審稿意見 |
| 5. 論文修訂 | academic-paper (revision) | 修訂版論文 |

---

## Agent File References

| Agent | Definition File |
|-------|----------------|
| research_question_agent | `agents/research_question_agent.md` |
| research_architect_agent | `agents/research_architect_agent.md` |
| bibliography_agent | `agents/bibliography_agent.md` |
| source_verification_agent | `agents/source_verification_agent.md` |
| synthesis_agent | `agents/synthesis_agent.md` |
| report_compiler_agent | `agents/report_compiler_agent.md` |
| editor_in_chief_agent | `agents/editor_in_chief_agent.md` |
| devils_advocate_agent | `agents/devils_advocate_agent.md` |
| ethics_review_agent | `agents/ethics_review_agent.md` |
| socratic_mentor_agent | `agents/socratic_mentor_agent.md` |

---

## Reference Files

| Reference | Purpose | Used By |
|-----------|---------|---------|
| `references/apa7_style_guide.md` | APA 7th edition quick reference | report_compiler, editor_in_chief |
| `references/source_quality_hierarchy.md` | Evidence pyramid + grading rubric | source_verification, bibliography |
| `references/methodology_patterns.md` | Research design templates | research_architect |
| `references/logical_fallacies.md` | 30+ fallacies catalog | devils_advocate |
| `references/ethics_checklist.md` | AI disclosure, attribution, dual-use | ethics_review |
| `references/interdisciplinary_bridges.md` | Cross-discipline connection patterns | synthesis, research_architect |
| `references/socratic_questioning_framework.md` | 6 types of Socratic questions + 30+ prompt patterns | socratic_mentor |
| `references/failure_paths.md` | 12 failure scenarios with triggers and recovery paths | all agents |
| `references/mode_selection_guide.md` | Mode selection flowchart and comparison table | orchestrator |

---

## Templates

| Template | Purpose |
|----------|---------|
| `templates/research_brief_template.md` | Quick mode output format |
| `templates/literature_matrix_template.md` | Source x Theme analysis matrix |
| `templates/evidence_assessment_template.md` | Per-source quality assessment card |

---

## Examples

| Example | Demonstrates |
|---------|-------------|
| `examples/exploratory_research.md` | Full 6-phase pipeline walkthrough |
| `examples/systematic_review.md` | PRISMA-style literature review |
| `examples/policy_analysis.md` | Applied comparative policy research |
| `examples/socratic_guided_research.md` | Complete Socratic mode multi-turn dialogue (12 rounds, traditional Chinese) |
| `examples/handoff_to_paper.md` | deep-research full mode handoff to academic-paper |
| `examples/review_mode.md` | Review mode: 3-agent review pipeline for policy recommendation text |
| `examples/fact_check_mode.md` | Fact-check mode: source verification of HEI claims with per-claim verdicts |

---

## Output Language

Default: matches user's input language. If user writes in 繁體中文, output in 繁體中文. If in English, output in English. User can override explicitly.

Socratic mode 特別注意：對話語氣自然，術語保留英文（如 research question、methodology、FINER），中英混用時 Mentor 也中英混用。

---

## Quality Standards

1. **Every claim must have a citation** — no unsupported assertions
2. **Evidence hierarchy** — meta-analyses > RCTs > cohort studies > case reports > expert opinion
3. **Contradiction disclosure** — if sources disagree, report both sides with evidence quality comparison
4. **Limitation transparency** — every report must have an explicit limitations section
5. **AI disclosure** — all reports include a statement that AI-assisted research tools were used
6. **Reproducibility** — search strategies, inclusion criteria, and analytical methods must be documented for replication
7. **Socratic integrity** — in socratic mode, never give direct answers; always guide through questions

---

## Integration with Other Skills

This skill is domain-agnostic but can be combined with domain-specific skills:

```
deep-research + tw-hei-intelligence     -> Evidence-based HEI policy research
deep-research + report-to-website       -> Interactive research report
deep-research + podcast-script-generator -> Research podcast
deep-research + academic-paper          -> Full research-to-publication pipeline
deep-research (socratic) + academic-paper (plan) -> Guided research + paper planning
```

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 2.0 | 2026-02 | Added socratic mode (10th agent), failure paths, mode selection guide, handoff protocol, 2 new examples, 3 new references |
| 1.0 | 2026-02 | Initial release: 9 agents, 5 modes, 6-phase pipeline |
