---
name: academic-paper
description: "Academic paper writing skill with 10-agent pipeline. v2.0: NEW plan mode (Socratic guided chapter-by-chapter planning), deep-research handoff protocol, Chinese APA 7.0 citation guide, failure path handling. Supports IMRaD, literature review, theoretical, case study, policy brief, and conference paper structures. APA 7.0 (default), Chicago, MLA, IEEE, Vancouver citation formats. Bilingual abstracts (zh-TW + EN). Multi-format output (LaTeX, DOCX, PDF, Markdown). Triggers on: write paper, 寫論文, academic paper, 學術論文, paper outline, 論文大綱, write abstract, 寫摘要, revise paper, 修改論文, check citations, 檢查引用, convert to LaTeX, 轉換格式, guide my paper, 引導我寫論文."
metadata:
  version: "2.0"
  last_updated: "2026-02"
---

# Academic Paper — 學術論文撰寫 Agent Team

通用學術論文撰寫工具 — 10-agent pipeline，涵蓋所有學科，預設高教領域專門 reference。v2.0 新增 Plan mode（蘇格拉底式逐章引導）、deep-research Handoff、中文 APA 引用、失敗路徑處理。

## Quick Start

**最小指令：**
```
Write a paper on the impact of AI on higher education quality assurance
```

```
寫一篇關於少子化對私立大學經營策略影響的論文
```

**執行流程：**
1. 組態訪談 — 論文類型、學科、引用格式、輸出格式
2. 文獻搜尋 — 系統性搜尋策略、來源篩選
3. 架構設計 — 論文結構、大綱、字數分配
4. 論證建構 — 主張-證據鏈、邏輯流程
5. 全文撰寫 — 逐節草稿、語域調整
6. 引用合規 + 雙語摘要（並行）
7. 同儕審查 — 五維度評分、修訂建議
8. 輸出格式化 — LaTeX/DOCX/PDF/Markdown

---

## Trigger Conditions

### Trigger Keywords

**English**: write paper, academic paper, paper outline, write abstract, revise paper, literature review paper, check citations, convert to LaTeX, format paper, conference paper, journal article, thesis chapter, research paper, guide my paper, help me plan my paper, step by step paper
**中文**: 寫論文, 學術論文, 論文大綱, 寫摘要, 修改論文, 文獻回顧論文, 檢查引用, 轉換格式, 格式化論文, 研討會論文, 期刊文章, 學位論文章節, 研究論文, 引導我寫論文, 一步一步寫, 幫我規劃論文

### Does NOT Trigger

| Scenario | Use Instead |
|----------|-------------|
| Deep research / fact-checking (not paper writing) | `deep-research` |
| Taiwan university data query | `tw-hei-intelligence` |
| Single institution analysis | `tw-hei-analysis` |
| Multi-school comparison | `hei-agent-team` |

### Distinction from `deep-research`

| Feature | `academic-paper` | `deep-research` |
|---------|-------------------|-----------------|
| Primary output | Publishable paper draft | Research report |
| Structure | Journal-ready (IMRaD, etc.) | APA 7.0 report |
| Citation | Multi-format (APA/Chicago/MLA/IEEE/Vancouver) | APA 7.0 only |
| Abstract | Bilingual (zh-TW + EN) | Single language |
| Peer review | Simulated 5-dimension review | Editorial review |
| Output format | LaTeX/DOCX/PDF/Markdown | Markdown only |
| Revision loop | Max 2 rounds with targeted feedback | Max 2 rounds |

---

## Agent Team (10 Agents)

| # | Agent | Role | Phase |
|---|-------|------|-------|
| 1 | `intake_agent` | 組態訪談：論文類型、學科、期刊、引用格式、輸出格式、語言、字數；Handoff 偵測；Plan mode 簡化訪談 | Phase 0 |
| 2 | `literature_strategist_agent` | 搜尋策略設計、來源篩選、註解書目、文獻矩陣 | Phase 1 |
| 3 | `structure_architect_agent` | 選擇論文結構、詳細大綱、字數分配、證據配置 | Phase 2 |
| 4 | `argument_builder_agent` | 論點建構、主張-證據鏈、邏輯流程、反論處理；Plan mode 論點壓力測試 | Phase 3 / Plan Step 3 |
| 5 | `draft_writer_agent` | 逐節撰寫完整草稿、學科語域調整、字數追蹤 | Phase 4 |
| 6 | `citation_compliance_agent` | 引用格式驗證、參考文獻完整性、DOI 檢查 | Phase 5a |
| 7 | `abstract_bilingual_agent` | 雙語摘要（zh-TW + EN）、各 5-7 關鍵詞 | Phase 5b |
| 8 | `peer_reviewer_agent` | 模擬雙盲審查、五維度評分、修訂建議（最多 2 輪） | Phase 6 |
| 9 | `formatter_agent` | 轉換為 LaTeX/DOCX/PDF/Markdown、期刊格式化、cover letter | Phase 7 |
| 10 | `socratic_mentor_agent` | Plan mode 蘇格拉底式導師：逐章節引導、5 必答問題、INSIGHT 萃取 | Plan Step 0-3 |

---

## Orchestration Workflow (8 Phases)

```
User: "Write a paper on [topic]" / "寫一篇關於 [topic] 的論文"
     |
=== Phase 0: CONFIG (Interactive) ===
     |
     +-> [intake_agent] -> Paper Configuration Record
         - Paper type (IMRaD / Lit Review / Theoretical / Case Study / Policy Brief / Conference)
         - Discipline and sub-field
         - Target journal (optional)
         - Citation format (APA 7 / Chicago / MLA / IEEE / Vancouver)
         - Output format (LaTeX / DOCX / PDF / Markdown / Combined)
         - Language (EN / zh-TW / bilingual sections)
         - Bilingual abstract (Yes / EN-only / zh-TW-only)
         - Word count target
         - Existing materials (RQ, data, drafts, lit)
     |
     ** User confirms configuration **
     |
=== Phase 1: RESEARCH ===
     |
     +-> [literature_strategist_agent] -> Search Strategy + Source Corpus
         - Database selection + search strings
         - Inclusion/exclusion criteria
         - Source screening + annotated bibliography
         - Literature matrix (Source × Theme)
         - Research gap mapping
     |
     ** User reviews sources (optional add/remove) **
     |
=== Phase 2: ARCHITECTURE ===
     |
     +-> [structure_architect_agent] -> Paper Outline + Evidence Map
         - Structure pattern selection (from paper_structure_patterns.md)
         - Section-by-section outline with word count allocation
         - Evidence-to-section assignment
         - Transition logic between sections
     |
     ** User approves outline **
     |
=== Phase 3: ARGUMENTATION ===
     |
     +-> [argument_builder_agent] -> Argument Blueprint
         - Central thesis + sub-arguments
         - Claim-Evidence-Reasoning chains per section
         - Counter-argument identification + rebuttal strategy
         - Logical flow diagram
     |
=== Phase 4: DRAFTING ===
     |
     +-> [draft_writer_agent] -> Complete Draft
         - Section-by-section writing following outline
         - Register adjustment for discipline
         - In-text citations integrated
         - Word count tracking per section
         - Transition paragraphs between sections
     |
=== Phase 5a & 5b: CITATIONS + ABSTRACT (Parallel) ===
     |
     |-> [citation_compliance_agent] -> Citation Audit Report
     |   - In-text ↔ reference list cross-check (zero orphans)
     |   - Format compliance (per selected style)
     |   - DOI/URL verification
     |   - Self-citation ratio check
     |   - Auto-correction of detected errors
     |
     +-> [abstract_bilingual_agent] -> Bilingual Abstract + Keywords
         - English abstract (150-300 words, structured)
         - 繁體中文摘要 (300-500 字, structured)
         - EN keywords (5-7)
         - zh-TW 關鍵詞 (5-7)
         - Independent writing (not mechanical translation)
     |
=== Phase 6: PEER REVIEW ===
     |
     +-> [peer_reviewer_agent] -> Review Report + Revision Instructions
         - 5-dimension scoring:
           Originality (20%) | Methodological Rigor (25%) | Evidence Sufficiency (25%)
           Argument Coherence (15%) | Writing Quality (15%)
         - Verdict: Accept / Minor Revision / Major Revision / Reject
         - Line-level feedback with suggested fixes
         - Max 2 revision loops → back to Phase 4 [draft_writer_agent]
     |
=== Phase 7: FORMAT ===
     |
     +-> [formatter_agent] -> Final Output Package
         - Target format conversion (LaTeX + .bib / DOCX / PDF / Markdown)
         - Journal-specific formatting (if target journal specified)
         - Cover letter (if journal submission)
         - AI disclosure statement
         - Final quality checklist
```

### Checkpoint Rules

1. **Phase 0 → 1**: User must confirm Paper Configuration Record
2. **Phase 2 → 3**: User must approve outline (can request restructuring)
3. **Phase 6**: Max 2 revision loops; unresolved items → "Acknowledged Limitations"
4. **Peer Review** Critical-severity issues block progression to Phase 7
5. User can skip Phase 1 (literature) if providing own sources

---

## Operational Modes (8 Modes)

| Mode | Trigger | Agents | Output |
|------|---------|--------|--------|
| `full` | "Write a paper" / "寫論文" | All 9 | Complete paper draft |
| `outline-only` | "Paper outline" / "論文大綱" | 1→2→3 | Detailed outline + evidence map |
| `revision` | "Revise paper" / "修改論文" | 8→5→6 | Revised draft with tracked changes |
| `abstract-only` | "Write abstract" / "寫摘要" | 1→7 | Bilingual abstract + keywords |
| `lit-review` | "Literature review" / "文獻回顧" | 1→2 | Annotated bibliography + synthesis |
| `format-convert` | "Convert to LaTeX" / "轉換格式" | 9 only | Formatted document |
| `citation-check` | "Check citations" / "檢查引用" | 6 only | Citation error report |
| `plan` | "引導我寫論文" / "guide my paper" / "一步一步寫" | 1→10→3→4 | Chapter Plan + INSIGHT Collection |

### Mode Selection Logic

```
"Write a paper on SDGs in HEI"           -> full
"Give me a paper outline for..."         -> outline-only
"Revise this paper based on feedback"    -> revision
"Write an abstract for this paper"       -> abstract-only
"Do a literature review on..."           -> lit-review
"Convert this paper to LaTeX"            -> format-convert
"Check the citations in this paper"      -> citation-check
"引導我寫論文" / "guide my paper"         -> plan
"一步一步寫" / "help me plan my paper"   -> plan
```

### Mode Selection Guide

詳見 `references/mode_selection_guide.md`。快速流程圖：

```
用戶輸入 →
├── 已有完整研究？
│   ├── Yes → 要完整論文？
│   │   ├── Yes → full mode
│   │   └── No → 只要大綱？ → outline-only mode
│   └── No → 想被引導？
│       ├── Yes → plan mode
│       └── No → full mode（Phase 0 會訪談）
├── 已有論文要修訂？ → revision mode
├── 只要摘要？ → abstract-only mode
├── 只要文獻回顧？ → lit-review mode
├── 要轉換格式？ → format-convert mode
└── 要檢查引用？ → citation-check mode
```

---

## Plan Mode: CHAPTER-BY-CHAPTER GUIDED PLANNING

核心原則：以資深博士導師 + 學科方法專家的視角，逐章節引導使用者想清楚論文的每個部分。不直接撰寫，而是透過蘇格拉底式對話讓使用者自己想清楚要寫什麼。

```
User: "引導我寫論文" / "guide my paper" / "help me plan my paper" / "一步一步寫"
     |
=== Step 0: RESEARCH READINESS CHECK ===
     |
     +-> [socratic_mentor_agent] → 確認使用者已有什麼材料
         - "你目前有哪些研究資料？（文獻、數據、分析結果）"
         - "你的研究問題確定了嗎？能用一句話說清楚嗎？"
         → 如果缺研究基礎，建議先跑 deep-research (socratic mode)
     |
=== Step 1: THESIS CRYSTALLIZATION ===
     |
     +-> [socratic_mentor_agent] → 追問核心論點
         - "你的論文要論證什麼？"
         - "一個不同意你的人會怎麼反駁？"
         - "你的論文完成後，讀者會改變什麼想法？"
         萃取 [INSIGHT: thesis_statement]
     |
=== Step 2: CHAPTER-BY-CHAPTER NEGOTIATION ===
     |
     For each chapter (Introduction → Literature → Method → Results → Discussion → Conclusion):
     |
     +-> [socratic_mentor_agent] → 追問該章節的目的和內容
     |
     |   Introduction:
     |   - "你要讓讀者感受到什麼問題的急迫性？"
     |   - "讀者讀完 Introduction 應該期待接下來看到什麼？"
     |   - "你的研究缺口是什麼？用一句話說"
     |
     |   Literature Review:
     |   - "你要講幾個故事？它們之間的關係是什麼？"
     |   - "你的文獻回顧最後要導向什麼結論？"
     |   - "有沒有一篇你不同意的重要文獻？為什麼？"
     |
     |   Methodology:
     |   - "如果有人質疑你的方法，你怎麼回應？"
     |   - "有沒有更簡單的方法也能回答你的問題？為什麼你沒有選？"
     |   - "你的方法最大的限制是什麼？你怎麼處理？"
     |
     |   Results:
     |   - "你最重要的發現是什麼？用一句話說"
     |   - "有沒有出乎意料的結果？怎麼解釋？"
     |   - "你的數據中有沒有不支持你假設的證據？"
     |
     |   Discussion:
     |   - "你的結果和現有文獻有什麼對話？"
     |   - "你最想讓讀者記住的一件事是什麼？"
     |   - "你的研究對實務/政策有什麼建議？"
     |
     |   Conclusion:
     |   - "如果只能留一段話，你要說什麼？"
     |   - "你的研究開啟了什麼未來的研究方向？"
     |
     每個章節至少 2 輪對話
     每個章節結束後 [socratic_mentor_agent] 萃取 Chapter Summary
     |
     +-> [structure_architect_agent] → 根據所有 Chapter Summary 產出完整大綱
     |
=== Step 3: ARGUMENT STRESS TEST ===
     |
     +-> [socratic_mentor_agent + argument_builder_agent]
         → 對每個子論點追問證據和邏輯
         → "你這個論點最薄弱的地方在哪？"
         → "如果把你的論點反過來，能成立嗎？"
         → 最終產出 Chapter Plan（含每章節的核心論點、支持證據、預期字數）
     |
Output: Chapter Plan + INSIGHT Collection
→ 使用者可接著用 full mode 產出完整論文
→ 或接著用 academic-paper-reviewer 審查 Chapter Plan
```

---

## Handoff Protocol: deep-research → academic-paper

當偵測到來自 deep-research 的材料時：
1. `intake_agent` 自動辨識已有材料
2. 跳過冗餘的 Phase 0 問題（RQ、method 已確定）
3. 自動匯入 Bibliography 到 Phase 1
4. 自動匯入 Synthesis 到 Phase 3

### 接受的材料格式

| 材料 | 來源 | 匯入到 |
|------|------|--------|
| Research Question Brief | deep-research Phase 0 | Phase 0（自動填入 RQ） |
| Methodology Blueprint | deep-research Phase 0 | Phase 0（自動填入 Method） |
| Annotated Bibliography（APA 7.0） | deep-research Phase 1-2 | Phase 1（literature_strategist） |
| Synthesis Report | deep-research Phase 3 | Phase 3（argument_builder） |
| INSIGHT Collection | deep-research socratic mode | Plan mode Step 1（thesis crystallization） |

---

## Failure Paths

詳見 `references/failure_paths.md`。快速參考：

| 失敗情境 | 處理策略 |
|---------|---------|
| 研究基礎不足 | 建議先跑 `deep-research` |
| 論文結構選錯 | 退回 Phase 2，建議替代結構 |
| 字數嚴重超標/不足 | 識別問題章節，建議精簡/擴充 |
| 引用格式全錯 | 全面重跑 citation phase |
| Peer Review 拒稿 | 分析拒稿原因，建議重大修訂或重構 |
| Plan mode 不收斂 | 建議跳到 outline-only mode |
| Handoff 材料不完整 | 列出缺失項，建議補充或重跑 |
| 使用者中途放棄 | 儲存已完成的 Chapter Plan |

---

## Full Academic Pipeline

```
deep-research (socratic/full)
  → academic-paper (plan/full)
    → academic-paper-reviewer (full/guided)
      → academic-paper (revision)
```

完整路徑說明：
1. `deep-research`：上游研究引擎——調查、文獻搜尋、事實查核、綜合分析
2. `academic-paper`：下游出版引擎——論文規劃、撰寫、引用、格式化
3. `academic-paper-reviewer`：品質守門——同儕審查、修訂建議
4. 回到 `academic-paper (revision)`：根據審查意見修訂

---

## Phase 0: Configuration Interview

When activated, `intake_agent` collects the following (showing defaults):

### 1. Paper Type
| Type | Structure | Typical Word Count |
|------|-----------|-------------------|
| IMRaD | Intro → Method → Results → Discussion | 5,000-8,000 |
| Literature Review | Intro → Thematic Sections → Synthesis → Gaps | 6,000-10,000 |
| Theoretical | Intro → Framework → Analysis → Implications | 5,000-8,000 |
| Case Study | Intro → Context → Analysis → Discussion | 4,000-7,000 |
| Policy Brief | Executive Summary → Background → Analysis → Recommendations | 2,000-4,000 |
| Conference Paper | Extended Abstract or Short Paper | 2,000-5,000 |

### 2. Discipline
Education, Computer Science, Engineering, Medicine, Humanities, Social Science, Business, Law, Natural Sciences, Arts, or custom.

### 3. Target Journal (Optional)
If specified, `formatter_agent` will apply journal-specific formatting rules.

### 4. Citation Format
| Format | Default For |
|--------|------------|
| APA 7th (default) | Education, Psychology, Social Sciences |
| Chicago 17th | History, Humanities |
| MLA 9th | Literature, Languages |
| IEEE | Engineering, Computer Science |
| Vancouver | Medicine, Biomedical |

### 5. Output Format
LaTeX (.tex + .bib) / DOCX / PDF / Markdown / Combined (all formats)

### 6. Language
EN / zh-TW / Bilingual (section-specific, e.g., zh-TW body + EN abstract)

### 7. Bilingual Abstract
Yes (default: zh-TW + EN with 5-7 keywords each) / EN only / zh-TW only

### 8. Word Count Target
Auto-suggested based on paper type; user can override.

### 9. Existing Materials
- Research question or thesis statement
- Literature / annotated bibliography
- Data / results
- Existing draft sections
- Reviewer feedback (for revision mode)

→ Produces **Paper Configuration Record** → waits for user confirmation

---

## Agent File References

| Agent | Definition File |
|-------|----------------|
| intake_agent | `agents/intake_agent.md` |
| literature_strategist_agent | `agents/literature_strategist_agent.md` |
| structure_architect_agent | `agents/structure_architect_agent.md` |
| argument_builder_agent | `agents/argument_builder_agent.md` |
| draft_writer_agent | `agents/draft_writer_agent.md` |
| citation_compliance_agent | `agents/citation_compliance_agent.md` |
| abstract_bilingual_agent | `agents/abstract_bilingual_agent.md` |
| peer_reviewer_agent | `agents/peer_reviewer_agent.md` |
| formatter_agent | `agents/formatter_agent.md` |
| socratic_mentor_agent | `agents/socratic_mentor_agent.md` |

---

## Reference Files

| Reference | Purpose | Used By |
|-----------|---------|---------|
| `references/apa7_extended_guide.md` | APA 7th 擴充指南（延伸自 deep-research） | citation_compliance, draft_writer, formatter |
| `references/apa7_chinese_citation_guide.md` | APA 7.0 中文引用完整規範（台灣學術慣例） | citation_compliance, draft_writer, formatter |
| `references/citation_format_switcher.md` | 多引用格式切換規則（含中文格式） | citation_compliance, formatter |
| `references/paper_structure_patterns.md` | 6 種論文結構模式 | structure_architect, intake |
| `references/academic_writing_style.md` | 學術寫作風格指南 | draft_writer, peer_reviewer |
| `references/hei_domain_glossary.md` | 高教術語雙語對照 | all agents (domain context) |
| `references/journal_submission_guide.md` | 期刊投稿指南 | formatter, intake |
| `references/abstract_writing_guide.md` | 摘要撰寫指南 | abstract_bilingual |
| `references/latex_template_reference.md` | LaTeX 範本參考 | formatter |
| `references/failure_paths.md` | 失敗路徑圖（10 種情境 + 處理策略） | all agents |
| `references/mode_selection_guide.md` | 8 種模式選擇指南 + 銜接路徑 | intake |

Also references from `deep-research`:
- `deep-research/references/apa7_style_guide.md` — base APA 7 reference (this skill extends, not duplicates)

---

## Templates

| Template | Purpose |
|----------|---------|
| `templates/imrad_template.md` | IMRaD 結構範本 |
| `templates/literature_review_template.md` | 文獻回顧範本 |
| `templates/case_study_template.md` | 個案研究範本 |
| `templates/theoretical_paper_template.md` | 理論論文範本 |
| `templates/policy_brief_template.md` | 政策簡報範本 |
| `templates/conference_paper_template.md` | 研討會論文範本 |
| `templates/latex_article_template.tex` | LaTeX starter template |
| `templates/bilingual_abstract_template.md` | 雙語摘要範本 |

---

## Examples

| Example | Demonstrates |
|---------|-------------|
| `examples/imrad_hei_example.md` | 完整 IMRaD 論文範例（高教領域，英文） |
| `examples/literature_review_example.md` | 文獻回顧論文範例 |
| `examples/plan_mode_guided_writing.md` | Plan mode 逐章節引導對話範例（混成學習主題） |
| `examples/chinese_paper_example.md` | 完整中文學術論文範例（IMRaD，中文 APA 7.0 引用） |
| `examples/revision_mode_example.md` | Revision mode 完整流程：peer review 意見回應 + 修訂對照表 |

---

## Quality Standards

### Writing Quality
1. **Every claim must have a citation** or be supported by the paper's own data
2. **Zero citation orphans** — in-text citations ↔ reference list must perfectly match
3. **Consistent register** — academic tone appropriate for the discipline
4. **Logical flow** — clear transitions between paragraphs and sections
5. **Word count compliance** — within ±10% of target

### Bilingual Abstract Quality
6. **Independent writing** — zh-TW and EN abstracts are independently composed, NOT mechanical translations
7. **Structural alignment** — both abstracts cover the same key points in the same order
8. **Keywords** — 5-7 per language, reflecting the paper's core concepts
9. **Word count** — EN: 150-300 words; zh-TW: 300-500 字

### Citation Quality
10. **Format compliance** — 100% adherence to selected citation style
11. **DOI inclusion** — every source with a DOI must include it
12. **Currency** — flag sources older than 10 years (unless seminal works)
13. **Self-citation ratio** — flag if >15%

### Peer Review
14. **Five dimensions** — Originality (20%), Methodological Rigor (25%), Evidence Sufficiency (25%), Argument Coherence (15%), Writing Quality (15%)
15. **Actionable feedback** — every criticism must include a specific suggestion
16. **Max 2 revision rounds** — unresolved items become Acknowledged Limitations

### Mandatory Inclusions
17. **AI disclosure statement** — every paper must include a statement on AI tool usage
18. **Limitations section** — explicitly discuss study limitations
19. **Ethics statement** — when applicable (human subjects, sensitive data)

---

## Output Language

Default: matches user's input language. If user writes in 繁體中文, paper body defaults to 繁體中文. If in English, defaults to English. User can override via Phase 0 configuration. Bilingual abstract is always offered regardless of body language.

---

## Integration with Other Skills

```
academic-paper + tw-hei-intelligence  -> Evidence-based HEI paper with real MOE data
academic-paper + deep-research        -> Deep research phase → paper writing phase (auto-handoff)
academic-paper + report-to-website    -> Interactive web version of the paper
academic-paper + notebooklm-slides-generator -> Presentation slides from paper
academic-paper + academic-paper-reviewer -> Peer review → revision loop
```

### Full Academic Pipeline (Recommended)

```
deep-research (socratic/full)
  → academic-paper (plan/full)
    → academic-paper-reviewer (full/guided)
      → academic-paper (revision)
```
