# Example: 跨領域論文審查

本範例展示 `academic-paper-reviewer` 在面對高度跨領域論文時，如何配置 reviewer 角色並處理學科間的張力。模擬審查一篇題為「運用機器學習預測台灣大學退場風險：以校務研究數據為基礎」的論文。

---

## 模擬論文摘要

> **標題**：運用機器學習預測台灣大學退場風險：以校務研究數據為基礎
>
> **摘要**：本研究開發一套基於機器學習的大學退場風險預測系統。以教育部公開數據（2010-2023 年，涵蓋 152 所大專校院）為訓練集，納入 47 個特徵變項（含招生率、財務指標、師資結構、產學合作等），比較 Random Forest、XGBoost、Logistic Regression、SVM 四種分類模型的預測表現。研究以 2018 年後已停辦或列為專案輔導的 12 所學校為正例（positive cases），採用 SMOTE 處理類別不平衡問題。結果顯示 XGBoost 模型表現最佳（AUC = 0.94, F1 = 0.87），前五大重要特徵為：新生註冊率、流動負債比率、專任教師離職率、碩博士班招生達成率、產學合作收入占比。本研究為教育主管機關提供早期預警工具的實證基礎。
>
> **關鍵詞**：機器學習、大學退場、風險預測、校務研究、台灣高等教育
>
> **全文約 8,500 字，引用文獻 52 篇**

---

## Phase 0: Field Analysis & Persona Configuration

### Field Analysis Report

#### 論文基本資訊
- **標題**：運用機器學習預測台灣大學退場風險：以校務研究數據為基礎
- **全文長度**：約 8,500 字
- **引用文獻數**：52 篇

#### 領域分析

| 維度 | 分析結果 |
|------|---------|
| Primary Discipline | 高等教育管理 + 資料科學（雙主學科） |
| Secondary Disciplines | 教育政策、財務管理、機構研究 (IR) |
| Research Paradigm | 量化研究（Quantitative）— 預測模型 |
| Methodology Type | 統計建模 / 機器學習（Classification） |
| Target Journal Tier | Q2-Q3 — 跨領域論文在兩個領域都可能不夠「專」 |
| Paper Maturity | 投稿前（Pre-submission）— 結構完整、分析完成 |

#### 建議目標期刊（Top 3）
1. **Studies in Higher Education** — 如果強化高教理論框架，主打教育政策貢獻
2. **Education and Information Technologies** — 教育科技導向，接受 ML 應用研究
3. **Journal of Higher Education Policy and Management** — 政策管理取向，接受量化研究

#### Reviewer Configuration Cards

---

### Reviewer Configuration Card #1

**角色**：EIC
**身份描述**：*Education and Information Technologies* (Springer) 副主編，專長教育數據科學與學習分析 (Learning Analytics)，過去 5 年主持多篇 ML 在教育領域應用的審稿。
**審查焦點**：
  1. ML 應用在高教管理的新穎性 — 這類研究在學生層級（學生流失預測）已很多，機構層級是否有足夠的新貢獻
  2. 論文的實際影響力 — 模型真的能被教育主管機關使用嗎
  3. 跨領域整合的品質 — 是否只是技術展示還是有教育洞見
**會特別在意的點**：「AUC = 0.94 是否過於樂觀，特別是在正例只有 12 所的情況下」
**可能的盲點**：可能過於關注技術面，忽略政策應用的複雜性

---

### Reviewer Configuration Card #2

**角色**：Peer Reviewer 1（方法論 — ML 技術專家）
**身份描述**：統計學習 / 機器學習方法論研究者，專長分類模型、類別不平衡處理、模型評估，在社會科學 ML 應用領域有多篇方法論文章。
**審查焦點**：
  1. 類別不平衡處理（12 正例 vs 140 負例）— SMOTE 是否是最佳策略
  2. 過度擬合風險 — 47 個特徵 + 小正例數 + 未見到 feature selection 策略
  3. 模型評估的嚴謹度 — cross-validation 策略、temporal split、out-of-time validation
**會特別在意的點**：「12 個正例的 F1 = 0.87 在統計上是否可靠，bootstrapped confidence interval 是否被報告」
**可能的盲點**：對高教退場的實質意義可能不夠敏感

---

### Reviewer Configuration Card #3

**角色**：Peer Reviewer 2（領域 — 校務研究專家）
**身份描述**：台灣校務研究（IR）學者，專長高教數據分析、指標體系建構，參與過教育部大學退場預警機制的規劃。
**審查焦點**：
  1. 47 個特徵變項的選擇邏輯 — 是否涵蓋關鍵指標，是否有遺漏
  2. 數據品質 — 公開數據的準確性、缺失值處理、跨年度一致性
  3. 「退場」的操作定義 — 12 所正例是否包含所有情況（停辦、合併、改制）
**會特別在意的點**：「退場不只是財務問題，是否考慮了治理、地理位置、政治因素等非量化指標」
**可能的盲點**：可能對 ML 方法的細節不夠敏感

---

### Reviewer Configuration Card #4

**角色**：Peer Reviewer 3（跨領域 — 公共政策 / AI 倫理）
**身份描述**：公共政策學者，專長 AI 在公共部門的應用倫理、演算法決策的公平性與透明性，研究 AI 在教育政策中的角色。
**審查焦點**：
  1. 演算法公平性 — 預測模型是否可能對特定類型的學校（偏鄉、技職、原住民學院）產生系統性偏見
  2. 政策應用的倫理考量 — 如果政府使用此模型，被標記為「高風險」的學校會面臨什麼後果
  3. 自我實現預言 — 模型預測一所學校會退場，是否可能加速其退場
**會特別在意的點**：「黑箱模型（XGBoost）在公共政策中是否可被接受，可解釋性的要求」
**可能的盲點**：可能對模型技術細節不夠了解

---

## Phase 1: Parallel Multi-Perspective Review（摘要版）

### EIC Review Report（摘要）

**Recommendation**: Major Revision | **Confidence**: 4/5

**核心觀點**：研究方向有創新性——從學生層級的預測提升到機構層級。但論文在技術展示和教育洞見之間失衡，目前更像是一篇 ML 技術論文恰好用了教育數據，而非一篇教育研究恰好用了 ML 方法。需要大幅加強「特徵重要性的教育意涵」的討論。

**Key Strengths**:
1. 將 ML 預測從學生層級提升到機構層級，填補研究缺口
2. 多模型比較設計合理
3. 前五大重要特徵的政策意涵有啟發性

**Key Weaknesses**:
1. 技術與教育洞見失衡 — Discussion 幾乎只在討論模型表現，缺少教育理論的對話
2. 12 個正例的模型穩定性令人擔憂
3. 缺少模型的外部驗證（如使用其他國家/地區的數據）

---

### Methodology Review Report — R1（摘要）

**Recommendation**: Major Revision | **Confidence**: 5/5

**核心觀點**：ML 方法的執行有幾個重要的技術問題需要解決。12 個正例是這篇論文最大的方法論挑戰——不是不可克服，但需要更謹慎的處理和更保守的宣稱。

**Key Strengths**:
1. 四模型比較（RF, XGBoost, LR, SVM）的設計合理
2. 使用 SMOTE 處理類別不平衡至少顯示作者意識到了這個問題
3. 使用 AUC 而非 Accuracy 作為主要指標是正確的

**Key Weaknesses**:
1. **Temporal Leakage 風險**（Critical）：論文使用 2010-2023 的完整數據集做 k-fold CV，但退場是時間序列事件。正確的做法是 temporal split（如用 2010-2019 訓練，2020-2023 驗證），否則模型可能使用了「未來」資訊
2. **SMOTE 在極小正例的問題**（Critical）：12 個正例經 SMOTE 生成合成樣本，但 SMOTE 的效果在極小樣本時非常不穩定。建議比較 SMOTE vs ADASYN vs cost-sensitive learning
3. **過度擬合**（Major）：47 個特徵 + 12 個正例 → 特徵數遠大於正例數，過度擬合風險極高。必須報告 feature selection（如 recursive feature elimination）的結果
4. **信賴區間缺失**（Major）：AUC=0.94 但無 bootstrapped 95% CI，在 12 個正例下 CI 可能極寬

**Questions for Authors**:
1. 請提供 temporal split 的結果。如果只有 12 個正例且多數在近年退場，temporal split 可能讓正例數更少，你如何處理？
2. 是否考慮過 Leave-One-Out Cross-Validation (LOOCV) 作為替代？在小樣本下可能更穩定。

---

### Domain Review Report — R2（摘要）

**Recommendation**: Minor Revision | **Confidence**: 5/5

**核心觀點**：從校務研究的角度，論文的數據處理基本合理，47 個特徵涵蓋了主要的校務指標。但有幾個關鍵的數據品質和定義問題需要釐清。

**Key Strengths**:
1. 47 個特徵變項涵蓋招生、財務、師資、研究、產學合作五大面向，比多數同類研究更全面
2. 使用教育部公開數據，研究可重現性高
3. 前五大特徵與校務研究的實務經驗一致

**Key Weaknesses**:
1. **「退場」定義不夠精確**（Major）：12 所正例是否包含「停辦」和「合併」？兩者的原因可能完全不同——有些合併是策略性的（如成功的合併升格），不應被歸為「退場失敗」
2. **遺漏非量化但關鍵的因素**（Major）：私校退場常與以下因素高度相關但難以量化——董事會治理品質、校地位置（偏鄉）、學校類型（宗教、專科改制）。論文需要在限制討論中明確標示
3. **數據跨年一致性**（Minor）：2010-2023 的指標定義是否有變化（如教育部統計項目的調整）？需要說明

---

### Perspective Review Report — R3（摘要）

**Recommendation**: Major Revision | **Confidence**: 3/5

**核心觀點**：從 AI 在公共政策應用的角度，這篇論文觸碰了一個重要但危險的領域——用演算法來「標記」可能退場的學校。技術上可能可行，但倫理和政策面的考量嚴重不足。

**Key Strengths**:
1. 願意探討 AI 在高教政策中的預測應用，走在研究前沿
2. Feature importance 分析提供了可解釋性的初步嘗試
3. 研究的實務動機明確

**Key Weaknesses**:
1. **自我實現預言 (Self-fulfilling Prophecy)**（Critical）：如果教育部使用此模型，被標記為「高風險」的學校可能面臨——招生更困難（家長和學生看到預測避而遠之）、銀行拒絕貸款、優秀教師離職。模型的預測可能直接加速學校退場。論文完全沒有討論這個倫理問題。建議增加 "Ethical Implications" 一節。
2. **演算法公平性 (Algorithmic Fairness)**（Major）：模型是否可能對特定類型的學校有系統性偏見？例如：偏鄉學校的招生率天然較低、技職院校的財務結構與一般大學不同、原住民族學院的設立目的不在於規模。如果不考慮這些結構性差異，模型可能會「懲罰」本來就處於弱勢的學校。
3. **黑箱問題與政策可接受性**（Major）：XGBoost 的可解釋性不足以支撐高風險的政策決策。建議至少提供 SHAP (SHapley Additive exPlanations) 分析，讓每所學校的預測結果都可以被解釋。在公共政策中，「模型為什麼這樣判斷」比「模型準不準」更重要。

**Cross-Disciplinary Reading Recommendations**:
- O'Neil, C. (2016). *Weapons of Math Destruction*. Crown.
- Selbst, A.D. et al. (2019). Fairness and abstraction in sociotechnical systems. *FAT* Conference*.
- Veale, M. & Binns, R. (2017). Fairer machine learning in the real world. *Big Data & Society*.
- Williamson, B. (2021). Education policy and the digital data state. *British Educational Research Journal*.

**Questions for Authors**:
1. 假設教育部明天就要使用你的模型，你會建議怎麼使用？有沒有什麼使用條件或限制？
2. 你是否考慮過讓「被預測」的學校有機會對模型結果提出異議？這在 AI 倫理中稱為 "right to contestation"。

---

## Phase 2: Editorial Synthesis & Decision（摘要版）

### Decision: **Major Revision**

### Consensus Analysis

**[CONSENSUS-4]**：
1. 研究方向具有創新性和實務價值
2. 12 個正例是重大方法論挑戰
3. 論文需要更多教育/政策面的討論

**[CONSENSUS-3]**：
1. 模型評估需要更嚴謹（EIC + R1 + R3）
2. 需要增加倫理考量的討論（EIC + R2 + R3）

**分歧 1: 技術嚴重度**
- **R1**: temporal leakage 和 SMOTE 問題是 Critical 級別
- **R2**: 數據處理基本合理（Minor Revision）
- **Resolution**: R1 是 ML 方法論專家（confidence 5/5），在其專業範圍內。temporal leakage 確實可能導致模型過度樂觀，列為 P1 必修項目。

**分歧 2: 倫理議題的權重**
- **R3**: 自我實現預言是 Critical 級別
- **R1/R2**: 倫理重要但不影響學術品質判斷
- **Resolution**: R3 的 confidence 只有 3/5，但其觀點在公共政策 AI 應用中是被廣泛認可的核心議題。列為 P1 但以「增加討論段落」的方式處理，不要求作者修改模型。

### Revision Roadmap

**Priority 1 — 結構性修改（預估工時：12-16 天）**
- [ ] R1: 執行 temporal split validation 並報告結果（來源：R1-W1, Critical）
- [ ] R2: 比較 SMOTE vs ADASYN vs cost-sensitive learning（來源：R1-W2, Critical）
- [ ] R3: 新增「Ethical Implications」一節，討論自我實現預言和演算法公平性（來源：R3-W1/W2, Critical）
- [ ] R4: 新增 SHAP 分析，提供個案層級的可解釋性（來源：R3-W3, Major）
- [ ] R5: 執行 feature selection，報告精簡模型的表現（來源：R1-W3, Major）

**Priority 2 — 內容補充（預估工時：6-8 天）**
- [ ] S1: 報告 bootstrapped 95% CI（來源：R1-W4）
- [ ] S2: 精確定義「退場」，區分停辦和合併（來源：R2-W1）
- [ ] S3: 在討論中加強特徵重要性的教育理論對話（來源：EIC-W1）
- [ ] S4: 在限制中討論非量化因素的缺失（來源：R2-W2）
- [ ] S5: 討論數據跨年一致性處理（來源：R2-W3）

**Priority 3 — 文字與格式（預估工時：2 天）**
- [ ] 調整標題，突出預測模型的政策意涵
- [ ] 增加模型外部驗證的未來研究建議
- [ ] 統一引用格式

**Revision Deadline**：建議 8 週

---

## 本範例的教學價值

### 1. 跨領域 Reviewer 配置的挑戰

本論文涉及 ML 技術 + 高教管理 + 公共政策三個領域。`field_analyst_agent` 的配置策略是：
- **R1（方法論）**：ML 技術專家 — 因為技術嚴謹度是這類論文的立足點
- **R2（領域）**：校務研究專家 — 因為數據的領域知識至關重要
- **R3（跨領域）**：AI 倫理/公共政策 — 因為這是作者最可能忽略的面向

如果三位 reviewer 都是高教學者，技術問題會被漏掉；如果都是 ML 學者，政策倫理會被忽略。

### 2. Reviewer 3 的獨特價值

在這個例子中，R3（AI 倫理學者）提出了其他 reviewer 完全沒提到的問題：
- 自我實現預言
- 演算法公平性
- 黑箱政策決策的可接受性

這正是 `perspective_reviewer_agent` 的設計價值——它代表了一個作者可能沒有對話的學術社群。

### 3. 分歧處理的範例

R1 認為技術問題是 Critical，R2 認為是 Minor。`editorial_synthesizer_agent` 的仲裁依據是：
- R1 在 ML 方法論上有 5/5 的信心
- Temporal leakage 確實是一個公認的嚴重問題
- 因此採納 R1 的判斷

R3 的倫理觀點 confidence 只有 3/5，但觀點本身被廣泛認可。仲裁結果是「列為 P1 但以增加討論段落處理」——重視觀點的有效性，同時考慮 confidence 的限制。

### 4. 與學生層級 ML 研究的差異

本論文的獨特挑戰在於「正例極少」（只有 12 所退場學校）。這與學生層級的 ML 研究（通常有數百到數千個正例）有根本性差異。R1 的審查因此特別聚焦在小樣本下的模型穩定性問題，而非一般 ML 論文常見的「模型選擇」或「超參數調優」問題。
