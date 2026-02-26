# Example: 從中間進入 Pipeline（Mid-Entry）

## 情境說明

**使用者類型**：大學教授，有論文寫作經驗
**情境**：已經完成一篇英文論文草稿，想在投稿前做一次模擬審查
**目標**：審查 --> 修訂 --> 格式轉換（LaTeX）
**語言**：English（論文為英文，與 orchestrator 的對話用中文）

---

## 使用者輸入

```
我已經寫好一篇英文論文，主題是 "Machine Learning Approaches for
Predicting University Attrition Risk in Taiwan"，大概 7,000 words。
想做一次模擬審查再投稿。
```

---

## Pipeline 執行紀錄

### Orchestrator: Mid-Entry 偵測

```
偵測結果：
- 材料：完整英文論文草稿（7,000 words）
- 目標：模擬審查 + 修訂 + 投稿準備
- 進入點：Stage 3 (REVIEW)
- 使用者類型：有經驗的研究者

偵測到你有完整論文，可以直接進入 Stage 3 (REVIEW)。

在開始之前，確認一下：
1. 論文結構是什麼？（IMRaD / 其他）
2. 你想要哪種審查模式？
   - full：完整 4 人審查（EIC + 3 Peer Reviewers）
   - quick：EIC 快速評估（15 分鐘版）
   - guided：蘇格拉底式引導審查（互動對話）
3. 預計投稿哪個期刊（或什麼等級）？
4. 審查完成後需要修訂和格式轉換嗎？

如果之後想根據審查意見修改，我會自動引導你進入 Stage 4。
```

**使用者**：IMRaD 結構，想要 quick review 先看看大方向有沒有問題，目標是 Computers & Education（SSCI Q1）。審查完看情況再說。

### Orchestrator: 確認配置

```
收到。Pipeline 配置：

  Stage 1 RESEARCH    [--] 跳過（你已有研究基礎）
  Stage 2 WRITE       [--] 跳過（你已有完整論文）
  Stage 3 REVIEW:     quick -- 先用 EIC 快速評估，看大方向
  Stage 4 REVISE:     待定 -- 根據 Stage 3 結果決定
  Stage 5 FINALIZE:   待定 -- 需要時再啟動

開始 Stage 3 (REVIEW) quick mode？

進度：[--]研究 -> [--]撰寫 -> [..]審查 -> [ ]修訂 -> [ ]完稿
```

**使用者**：開始。

---

### Stage 3: REVIEW (quick mode)

```
進入 Stage 3 (REVIEW) -- 使用 academic-paper-reviewer quick mode

載入 academic-paper-reviewer SKILL.md...
接收使用者提供的論文草稿...
field_analyst_agent 分析論文領域...
eic_agent 執行快速評估...
```

**Field Analysis（快速版）：**
```
論文領域：Educational Data Mining / Higher Education
方法類型：Machine Learning (Supervised Classification)
目標期刊：Computers & Education (SSCI Q1, IF: 12.0)

EIC Persona:
  Computers & Education 副主編
  專長：Learning Analytics, Educational AI
```

**EIC Quick Assessment：**

```
Overall: Promising but needs work (Minor-to-Major Revision range)

Key Strengths (top 3):
1. Timely topic -- university attrition prediction highly relevant
   in Taiwan's demographic context
2. Good feature engineering -- combining MOE open data with
   institutional records is novel
3. Clear methodology -- model comparison (RF, XGBoost, LSTM)
   is well-structured

Key Concerns (top 3):
C1: [CRITICAL] Ethical considerations section is missing.
    C&E requires explicit discussion of algorithmic fairness,
    student privacy, and potential discriminatory outcomes.
C2: [MAJOR] Model interpretability not discussed.
    C&E reviewers expect SHAP values or similar explainability
    analysis, not just accuracy metrics.
C3: [MAJOR] Literature gap -- no mention of Dropout Factory
    literature (Balfanz & Legters, 2004) or recent European
    attrition studies. Too Taiwan-centric for an international
    journal.

Quick Verdict: Major Revision
  Before full submission, address C1-C3.
  Estimated revision effort: 2-3 weeks.
```

**Stage 3 完成產出物：**
- EIC Quick Assessment Report
- 3 個關鍵問題清單（Priority 排序）

---

### Orchestrator: 轉場建議

```
Stage 3 (REVIEW) quick mode 完成！

審查結果：Major Revision 方向
  C1: [CRITICAL] 缺少倫理討論（C&E 的硬性要求）
  C2: [MAJOR] 缺少模型可解釋性分析
  C3: [MAJOR] 文獻回顧國際視野不足

這是 quick review 的結果。你有幾個選項：

  a) 直接進入 Stage 4 (REVISE) 修訂這 3 個問題
  b) 升級為 full review（完整 4 人審查），
     看看還有沒有其他問題
  c) 先自己修改，改完再回來

我的建議：因為你要投 C&E（Q1 期刊），
建議先修完 C1-C3，再做一次 full review 確保品質。

你選哪個？
```

**使用者**：先修 C1-C3，然後做 full review。

### Orchestrator: 更新配置

```
好的，更新 pipeline：

  Stage 3 REVIEW (quick):  [v] 已完成
  Stage 4 REVISE:          [..] 接下來 -- 修 C1-C3
  Stage 3' RE-REVIEW:      full mode -- 修完後完整審查
  Stage 5 FINALIZE:        待定

開始 Stage 4 (REVISE)？

進度：[--]研究 -> [--]撰寫 -> [v]審查 -> [..]修訂 -> [ ]再審 -> [ ]完稿
```

**使用者**：開始修訂。

---

### Stage 4: REVISE (revision mode, Round 1)

```
進入 Stage 4 (REVISE) -- 使用 academic-paper revision mode

載入 academic-paper SKILL.md (revision mode)...
傳遞 Paper Draft + Quick Assessment Report...
```

**Revision 進度追蹤：**
```
C1: [v] 新增 Ethics & Fairness section (Section 5.3)
    - Algorithmic fairness analysis (demographic parity, equalized odds)
    - Student privacy framework (FERPA-equivalent for Taiwan)
    - Potential discriminatory outcomes discussion
    - Added 5 citations on AI ethics in education

C2: [v] 新增 Model Interpretability analysis (Section 4.3)
    - SHAP value analysis for top 20 features
    - Feature importance comparison across 3 models
    - Case study: 3 individual prediction explanations
    - Added SHAP visualization figures

C3: [v] 擴充 Literature Review (Section 2)
    - Added Dropout Factory framework (Balfanz & Legters)
    - Added 6 European attrition studies (2020-2026)
    - Added cross-cultural comparison discussion
    - Restructured into 3 sub-sections: global -> Asia -> Taiwan
```

**Stage 4 完成產出物：**
- Revised Draft（9,200 words，比原稿增加 2,200 words）
- Response to Reviewers（R-A-C 格式，3 項全部處理）

---

### Orchestrator: Stage 4 --> 3' 轉場

```
Stage 4 (REVISE) 完成！

修訂成果：
- 3/3 問題全部處理
- 論文從 7,000 words 擴充至 9,200 words
- 新增 Ethics section, SHAP analysis, international literature
- 新增 11 筆引用

下一步是 Stage 3' (RE-REVIEW) -- 這次用 full mode。
4 位 reviewer 完整審查修訂版。
這是第 1 輪修訂循環（最多 2 輪）。

要送出 full review 嗎？

進度：[--]研究 -> [--]撰寫 -> [v]審查 -> [v]修訂 -> [..]再審 -> [ ]完稿
```

**使用者**：送出。

---

### Stage 3': RE-REVIEW (full mode, Loop 1)

```
進入 Stage 3' (RE-REVIEW) -- full mode, Loop 1/2

載入 academic-paper-reviewer SKILL.md (full mode)...
傳遞 Revised Draft + Response to Reviewers...
field_analyst_agent 重新分析...
```

**Reviewer Configuration:**
```
EIC:        Computers & Education 副主編
            Educational AI, Learning Analytics
Reviewer 1: Machine Learning 專家
            Predictive modeling, Model evaluation
Reviewer 2: Higher Education researcher
            Student success, Retention strategies
Reviewer 3: Research Ethics / Data Science ethicist
            Algorithmic fairness, Educational data mining ethics
```

**4 份審查報告彙整：**

```
EIC: Minor Revision
  - C1 回應充分，Ethics section well-structured
  - 建議 Abstract 更新以反映新增的 ethics + interpretability 貢獻
  - 建議加一個 Practical Implications section for university administrators

Reviewer 1: Accept
  - SHAP analysis 完整且有洞察
  - Model comparison fair and well-documented
  - Minor: Table 3 的 precision/recall 建議加 confidence intervals

Reviewer 2: Minor Revision
  - International literature coverage 大幅改善
  - 建議 Discussion 加入與 Tinto's Student Integration Model 的對話
  - Minor: Section 2.1 引用 Chen (2023) 應為 Chen (2024)

Reviewer 3: Accept
  - Ethics section 水準很高，超出 C&E 一般標準
  - Algorithmic fairness metrics well-chosen
  - 建議加一段 "limitations of fairness metrics" 的反思
```

**Editorial Decision：Minor Revision (Accept 方向)**

```
Required Revisions:
R1: 更新 Abstract（反映新貢獻）
R2: 新增 Practical Implications section

Suggested Revisions:
S1: Table 3 加 confidence intervals
S2: Discussion 加 Tinto's model 對話
S3: 修正 Chen (2023) -> Chen (2024) 引用年份
S4: 加 fairness metrics limitations 段落
```

---

### Orchestrator: 快速修訂 + FINALIZE

```
Stage 3' (RE-REVIEW) 完成！

審查結果：Minor Revision (Accept 方向)
  - 4 位 reviewer 中 2 位 Accept + 2 位 Minor Revision
  - 2 個必修項目（Abstract 更新 + Practical Implications）
  - 4 個建議修改

這些都是小幅修改，可以在 Stage 5 (FINALIZE) 一併處理。
或者你想先進 Stage 4 正式修訂再送審？

我的建議：因為全是 minor 項目，直接進 Stage 5 一併處理即可。

你需要什麼格式？
  a) LaTeX (.tex + .bib) -- 適合投 C&E
  b) 其他格式

進度：[--]研究 -> [--]撰寫 -> [v]審查 -> [v]修訂 -> [v]再審 -> [..]完稿
```

**使用者**：直接 finalize，LaTeX 格式。

---

### Stage 5: FINALIZE (format-convert mode)

```
進入 Stage 5 (FINALIZE) -- format-convert mode

一併處理 minor revision items：
R1: [v] Abstract 更新
R2: [v] 新增 Practical Implications section (200 words)
S1: [v] Table 3 加 confidence intervals
S2: [v] Discussion 加 Tinto's model 段落
S3: [v] 修正 Chen 引用年份
S4: [v] 加 fairness metrics limitations 段落

formatter_agent 執行 LaTeX 轉換...
- 使用 Elsevier article template (C&E format)
- 產出 .tex + .bib + figures/
- 產出 cover letter draft
```

**Stage 5 完成產出物：**
- `ml_university_attrition_taiwan.tex`（LaTeX 主文）
- `references.bib`（BibTeX 檔）
- `figures/`（所有圖表）
- `cover_letter.tex`（投稿信草稿）

---

### Orchestrator: Pipeline 完成

```
+=========================================+
|   Academic Pipeline Status              |
+=========================================+
| Topic: ML Approaches for Predicting     |
|        University Attrition Risk        |
+-----------------------------------------+

  Stage 1 RESEARCH    [--] Skipped
  Stage 2 WRITE       [--] Skipped
  Stage 3 REVIEW      [v] Completed
    Mode: quick
    Decision: Major Revision (3 items)
  Stage 4 REVISE      [v] Completed
    Round: 1, Addressed: 3/3
  Stage 3' RE-REVIEW  [v] Completed
    Mode: full, Loop: 1/2
    Decision: Minor Revision (Accept)
  Stage 5 FINALIZE    [v] Completed
    Format: LaTeX (Elsevier)

+-----------------------------------------+
| Materials:                              |
|   [--] RQ Brief (skipped)               |
|   [--] Methodology (skipped)            |
|   [--] Bibliography (skipped)           |
|   [--] Synthesis (skipped)              |
|   [v] Paper Draft (user-provided)       |
|   [v] Review Reports (quick + full)     |
|   [v] Revision Roadmap                  |
|   [v] Revised Draft (9,500 words)       |
|   [v] Response to Reviewers             |
|   [v] Final Paper (LaTeX)              |
+-----------------------------------------+
| Revision History:                       |
|   Round 1: Major -> 3/3 addressed       |
|   RE-REVIEW: Minor (Accept direction)   |
|   Final minor fixes in FINALIZE         |
+-----------------------------------------+
| Pipeline 完成！                          |
+=========================================+

你的論文已準備好投稿 Computers & Education。

最終交付物：
1. ml_university_attrition_taiwan.tex（主文）
2. references.bib（引用）
3. figures/（圖表）
4. cover_letter.tex（投稿信草稿）

投稿前建議：
- 再讀一次 cover letter，調整為你的語氣
- 確認 C&E 的 Author Guidelines 沒有額外格式要求
- 準備 Highlights（3-5 bullet points）和 Graphical Abstract
```
