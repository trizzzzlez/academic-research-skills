# Research Methodology Patterns — Design Templates

## Purpose
Ready-to-use methodology templates for common research designs. Used by the research_architect_agent.

## Pattern 1: Systematic Literature Review

### When to Use
- Mapping the state of knowledge on a topic
- Identifying gaps in existing research
- Synthesizing evidence for policy/practice recommendations

### Design Template
```
Research Question: What is known about [topic] in [context]?

Protocol:
1. Register protocol (PROSPERO or similar)
2. Define search strategy (databases, keywords, Boolean operators)
3. Establish inclusion/exclusion criteria
4. Search execution + documentation
5. Two-pass screening (title/abstract → full text)
6. Quality appraisal of included studies
7. Data extraction
8. Synthesis (narrative, thematic, or meta-analytic)
9. Report per PRISMA guidelines

Quality Criteria:
- Comprehensive search (minimum 3 databases)
- Reproducible strategy
- Dual screening (2 reviewers or reviewer + verification)
- PRISMA checklist completed
```

### PRISMA Flow Template
```
Records identified through database searching (n = )
Additional records from other sources (n = )
         ↓
Records after duplicates removed (n = )
         ↓
Records screened (title/abstract) (n = )
Records excluded (n = )
         ↓
Full-text articles assessed for eligibility (n = )
Full-text excluded, with reasons (n = )
         ↓
Studies included in synthesis (n = )
```

## Pattern 2: Comparative Case Study

### When to Use
- Comparing policies, programs, or institutions
- Understanding how context shapes outcomes
- Generating theoretical propositions from multiple cases

### Design Template
```
Research Question: How does [phenomenon] vary across [cases]?

Protocol:
1. Case selection (theoretical or purposive sampling)
2. Define comparison framework (dimensions, variables)
3. Data collection per case (documents, interviews, data)
4. Within-case analysis
5. Cross-case analysis
6. Pattern identification and explanation

Quality Criteria:
- Explicit case selection rationale
- Consistent data collection across cases
- Both within-case and cross-case analysis
- Rival explanations considered
```

### Comparison Matrix Template
```
| Dimension | Case A | Case B | Case C | Pattern |
|-----------|--------|--------|--------|---------|
| Context   |        |        |        |         |
| Input     |        |        |        |         |
| Process   |        |        |        |         |
| Outcome   |        |        |        |         |
```

## Pattern 3: Policy Analysis

### When to Use
- Evaluating existing or proposed policies
- Comparing policy approaches across jurisdictions
- Assessing policy outcomes and unintended consequences

### Design Template
```
Research Question: How effective is [policy] in achieving [goal]?

Framework Options:
A. Bardach's Eightfold Path
B. Dunn's Policy Analysis Framework
C. SWOT Analysis
D. Logic Model (Input → Activity → Output → Outcome → Impact)

Protocol:
1. Problem definition
2. Evidence gathering (quantitative + qualitative)
3. Policy option identification
4. Criteria development (effectiveness, efficiency, equity, feasibility)
5. Option assessment against criteria
6. Recommendation with trade-offs

Quality Criteria:
- Multiple criteria (not just effectiveness)
- Stakeholder perspectives included
- Unintended consequences assessed
- Implementation feasibility addressed
```

## Pattern 4: Mixed Methods (Convergent Parallel)

### When to Use
- Complex phenomena requiring multiple data types
- Need to triangulate findings
- Quantitative data needs qualitative explanation (or vice versa)

### Design Template
```
Research Question: What is the nature and extent of [phenomenon]?

Protocol:
QUAN strand:                    QUAL strand:
1. Survey/data collection       1. Interviews/focus groups
2. Statistical analysis         2. Thematic analysis
3. Quantitative findings        3. Qualitative findings
                    ↓
            4. Integration
            5. Joint display
            6. Meta-inference

Quality Criteria:
- Both strands have independent rigor
- Integration strategy explicit (not just parallel reporting)
- Joint display or mixed methods matrix
- Meta-inferences draw on both strands
```

## Pattern 5: Content/Document Analysis

### When to Use
- Analyzing texts, policies, media, or documents
- Identifying patterns in communication
- Systematic examination of large document sets

### Design Template
```
Research Question: What themes/patterns emerge from [document set]?

Protocol:
1. Define corpus (which documents, inclusion criteria)
2. Develop coding framework (deductive, inductive, or hybrid)
3. Code systematically (inter-coder reliability if multiple coders)
4. Analyze codes → categories → themes
5. Report with exemplar quotes/excerpts

Quality Criteria:
- Corpus selection transparent
- Coding framework documented
- Inter-coder reliability reported (if applicable)
- Saturation discussed
```

## Pattern 6: Exploratory Research

### When to Use
- New or under-researched topics
- Generating hypotheses for future research
- Understanding phenomena from participant perspective

### Design Template
```
Research Question: How do [participants] experience/understand [phenomenon]?

Protocol:
1. Purposive sampling
2. Semi-structured interviews or observations
3. Iterative data collection and analysis
4. Open coding → axial coding → selective coding
5. Theory or framework development
6. Member checking / peer debriefing

Quality Criteria:
- Reflexivity statement
- Thick description
- Data saturation discussed
- Transferability criteria addressed
```

## Pattern 7: Benchmarking Study

### When to Use
- Comparing performance against standards or peers
- Identifying best practices
- Setting performance targets

### Design Template
```
Research Question: How does [entity] perform compared to [benchmark]?

Protocol:
1. Select benchmarking type (internal, competitive, functional, generic)
2. Identify indicators and metrics
3. Collect comparable data
4. Analyze gaps
5. Identify best practices from high performers
6. Develop improvement recommendations

Quality Criteria:
- Comparable metrics (apples to apples)
- Context factors acknowledged
- Multiple indicators (not single metric)
- Actionable recommendations
```

## Pattern 8: Technology Requirements Analysis（技術需求分析）

### When to Use
- 評估新技術的可行性、需求分析、技術比較
- 系統設計前的技術選型決策
- 技術導入的風險與效益評估
- 當研究問題涉及「該用什麼技術？」或「這個技術能解決問題嗎？」

### Design Template
```
Research Question: What technology approach best addresses [need] given [constraints]?

Protocol:
1. 需求收集（Requirement Elicitation）
   - 利害關係人訪談
   - 現有系統/流程分析
   - 功能性需求 vs 非功能性需求（效能、安全、可擴充性）
2. 技術掃描（Technology Scanning）
   - 候選技術盤點（至少 3 個方案）
   - 技術成熟度評估（TRL, Technology Readiness Level）
   - 社群活躍度、文件完整度、長期維護風險
3. 可行性評估（Feasibility Assessment）
   - 技術可行性：能不能做？
   - 經濟可行性：值不值得做？
   - 組織可行性：團隊有能力做嗎？
   - 時程可行性：時間夠嗎？
4. 原型/概念驗證（PoC, Proof of Concept）
   - 針對關鍵技術風險建構最小驗證
   - 定義成功標準（效能門檻、整合測試通過率）
   - 記錄遇到的問題和解決方案
5. 需求規格（Requirement Specification）
   - 產出正式需求文件
   - 定義驗收標準
   - 建立可追溯性矩陣（需求 ↔ 設計 ↔ 測試）

Quality Criteria:
- 需求完整性：所有利害關係人的需求都被收集
- 可追溯性：每個需求都能追溯到來源，每個設計決策都有對應需求
- 技術可行性驗證：關鍵技術風險已透過 PoC 驗證
- 方案比較公平：使用一致的評估框架比較不同技術方案
```

### Technology Comparison Matrix Template
```
| 評估維度       | 方案 A | 方案 B | 方案 C | 權重 |
|---------------|--------|--------|--------|------|
| 功能符合度     |        |        |        | 30%  |
| 技術成熟度     |        |        |        | 20%  |
| 導入成本       |        |        |        | 15%  |
| 維護成本       |        |        |        | 10%  |
| 學習曲線       |        |        |        | 10%  |
| 擴充性         |        |        |        | 10%  |
| 社群/生態系    |        |        |        | 5%   |
| 加權總分       |        |        |        | 100% |
```

## Pattern 9: Legal Case Analysis（法律案例分析）

### When to Use
- 法規政策分析、判例研究、法律文本詮釋
- 分析特定法律問題的現行規範與實務見解
- 比較不同法域（jurisdictions）的法律處理方式
- 當研究問題涉及法規解釋、權利義務分析、政策法律面分析時

### 與 Pattern 3（Policy Analysis）的區別
- **Policy Analysis**：偏重政策效果評估，關心「這個政策有沒有效？」「有沒有更好的政策選項？」
- **Legal Case Analysis**：偏重法律文本和判例分析，關心「法律怎麼規定？」「法院怎麼解釋？」「有沒有法律漏洞？」

### Design Template
```
Research Question: How does the law address [issue] and what are the implications for [context]?

Protocol:
1. 法律問題界定（Issue Identification）
   - 將研究問題轉化為具體的法律爭點
   - 區分事實問題 vs 法律問題
   - 界定涉及的法律領域（公法/私法/國際法）
2. 相關法規盤點（Legal Framework Mapping）
   - 憲法層級規範
   - 法律/命令/行政規則層級
   - 國際公約/軟法（soft law）
   - 立法沿革與修法理由
3. 判例檢索與分析（Case Law Analysis）
   - 系統性判例檢索（法院層級、時間範圍、關鍵字）
   - 判決要旨萃取
   - 判例演進趨勢分析
   - 識別主流見解 vs 少數見解
4. 法理論證（Legal Reasoning）
   - 文義解釋、體系解釋、目的解釋、歷史解釋
   - 比較法分析（其他法域的處理方式）
   - 學說見解整理與評析
   - 利益衡量與價值判斷
5. 建議（Recommendations）
   - 現行法的解釋建議
   - 修法建議（如有必要）
   - 實務操作建議
   - 風險提示

Quality Criteria:
- 法源正確性：引用的法規、判例必須是現行有效版本
- 邏輯一致性：法理論證過程不能自相矛盾
- 論證完整性：所有可能的解釋路徑都被考慮
- 比較法嚴謹性：比較不同法域時要注意法制背景差異
```

### Legal Analysis Structure Template
```
一、法律問題
   [具體法律爭點]

二、相關規範
   1. 法律層級：
   2. 命令層級：
   3. 國際規範：

三、實務見解
   1. 主流見解：[判決字號] [要旨]
   2. 少數見解：[判決字號] [要旨]
   3. 趨勢：

四、學說見解
   1. 甲說：
   2. 乙說：
   3. 本文見解：

五、比較法
   [其他法域處理方式]

六、結論與建議
```

## Pattern 10: Creative/Practice-Based Research（創意/實踐導向研究）

### When to Use
- 藝術研究（art-based research）：透過藝術創作探究知識
- 設計研究（design research / research through design）：透過設計過程產生知識
- 實踐導向研究（practice-based / practice-led research）：實踐本身就是研究方法
- 當研究問題涉及創作實踐、設計思維、藝術探究時

### 與傳統學術研究的差異
- **成果形式**：可以是作品+論文（而非只有論文）
- **知識類型**：重視實踐知識（tacit knowledge）、身體知識（embodied knowledge）
- **過程即方法**：創作/設計過程本身就是研究方法，不只是研究的客體
- **主觀性**：研究者的主觀經驗是合法的知識來源，但需要系統性反思

### Design Template
```
Research Question: What knowledge emerges through the practice of [creative activity] in [context]?

Protocol:
1. 實踐反思（Reflective Practice）
   - 界定研究問題與創作意圖
   - 建立反思框架（如 Schön 的 reflection-in-action / reflection-on-action）
   - 確認研究者的定位（insider / practitioner-researcher）
2. 創作過程紀錄（Process Documentation）
   - 工作日誌（studio journal / design diary）
   - 過程影像/錄音紀錄
   - 迭代版本紀錄（sketches, drafts, prototypes）
   - 決策點紀錄：為什麼這樣做而不是那樣做？
3. 脈絡化分析（Contextual Analysis）
   - 將創作過程放入學科/文化/歷史脈絡
   - 與既有作品/理論對話
   - 識別創作中浮現的主題和洞察
4. 知識萃取（Knowledge Articulation）
   - 將隱性知識（tacit knowledge）轉化為可傳達的形式
   - 建立從實踐到概念的橋樑
   - 提煉可轉移的原則或框架
5. 成果展示（Presentation of Findings）
   - 作品展示（展覽、表演、原型展示）
   - 書面論述（exegesis / critical commentary）
   - 整合作品與論述的關聯性

Quality Criteria:
- 反思深度：不只是描述「做了什麼」，而是分析「為什麼這樣做」以及「學到了什麼」
- 創作過程透明性：讀者可以理解從問題到作品的完整路徑
- 知識貢獻明確性：清楚說明這個研究對知識的貢獻是什麼
- 脈絡化品質：作品不是孤立存在，而是與學科對話
- 方法論反身性：研究者對自身角色和偏見有所覺察
```

### Practice-Based Research Documentation Template
```
階段一：定位
- 研究問題：
- 創作意圖：
- 研究者定位（practitioner / observer / participant）：
- 理論框架：

階段二：過程
| 迭代 | 日期 | 行動 | 反思 | 轉折點 |
|------|------|------|------|--------|
| v1   |      |      |      |        |
| v2   |      |      |      |        |
| v3   |      |      |      |        |

階段三：成果
- 作品描述：
- 知識貢獻：
- 可轉移的原則/框架：
- 對後續實踐/研究的建議：
```

## Choosing the Right Pattern

```
What type of question?
├── "What is known?" → Systematic Literature Review
├── "How do cases compare?" → Comparative Case Study
├── "Is this policy working?" → Policy Analysis
├── "What's happening and why?" → Mixed Methods
├── "What do documents reveal?" → Content Analysis
├── "How is this experienced?" → Exploratory Research
├── "How do we compare?" → Benchmarking Study
├── "Which technology should we use?" → Technology Requirements Analysis
├── "What does the law say?" → Legal Case Analysis
└── "What knowledge emerges from practice?" → Creative/Practice-Based Research

More nuanced decision:
├── 技術評估相關
│   ├── 比較不同技術方案 → Pattern 8 (Technology Requirements Analysis)
│   └── 比較不同組織的技術採用 → Pattern 2 (Comparative Case Study)
├── 法律/政策相關
│   ├── 法律文本怎麼規定、判例怎麼解釋 → Pattern 9 (Legal Case Analysis)
│   └── 政策有沒有效、該怎麼改 → Pattern 3 (Policy Analysis)
├── 創作/設計相關
│   ├── 透過創作過程產生知識 → Pattern 10 (Creative/Practice-Based Research)
│   ├── 理解創作者的經驗 → Pattern 6 (Exploratory Research)
│   └── 分析創作文本/作品 → Pattern 5 (Content Analysis)
└── 不確定
    ├── 問題很新、文獻很少 → Pattern 6 (Exploratory Research)
    ├── 問題複雜、需要多種數據 → Pattern 4 (Mixed Methods)
    └── 先看看別人怎麼做 → Pattern 1 (Systematic Literature Review)
```
