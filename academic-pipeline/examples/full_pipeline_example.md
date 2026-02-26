# Example: 完整 Pipeline 對話紀錄

## 情境說明

**使用者類型**：教育研究所碩士生，第一次寫學術論文
**主題**：少子化對台灣私立大學招生策略的影響
**目標**：完成一篇可投稿的 IMRaD 論文
**語言**：繁體中文（摘要雙語）

---

## 使用者輸入

```
我想寫一篇關於少子化對台灣私立大學招生策略影響的論文，
從頭到尾幫我，我是第一次寫學術論文，不太確定流程。
```

---

## Pipeline 執行紀錄

### Orchestrator: 啟動偵測

```
偵測結果：
- 材料：無（從零開始）
- 目標：完整流程
- 進入點：Stage 1 (RESEARCH)
- 使用者偏好：第一次寫論文 --> 推薦引導模式

推薦 Pipeline 配置：

  Stage 1 RESEARCH: socratic -- 第一次做研究，蘇格拉底式引導幫你想清楚
  Stage 2 WRITE:    plan     -- 逐章節引導你規劃論文結構
  Stage 3 REVIEW:   full     -- 完整 4 人審查，模擬真實投稿體驗
  Stage 4 REVISE:   revision -- 根據審查意見逐項修改
  Stage 5 FINALIZE: format   -- 轉換為你需要的格式（LaTeX/DOCX/PDF）

你可以隨時調整任何 stage 的 mode。要開始嗎？
```

**使用者**：好的，開始吧！

---

### Stage 1: RESEARCH (socratic mode)

```
進入 Stage 1 (RESEARCH) -- 使用 deep-research socratic mode

載入 deep-research SKILL.md...
啟動 socratic_mentor_agent...
```

**Socratic Mentor**：你提到「少子化對私立大學招生策略的影響」。在我們開始之前，我想先了解幾件事：

1. 你為什麼對這個主題感興趣？是因為你觀察到了什麼現象嗎？
2. 當你說「招生策略」，你心裡想的是哪一種？網路行銷？獎學金？科系調整？還是全部？

**使用者**：我觀察到很多私立大學開始做一些以前不會做的事，像是到高中辦說明會、降低入學門檻、開很多新科系。我想知道這些策略到底有沒有效。

**Socratic Mentor**：很好的觀察。你提到了三種策略：推廣活動、入學標準調整、科系新設。

那我追問一下：你說的「有沒有效」，是指什麼？新生註冊率提高？學生素質維持？還是學校存活下來？不同的「效」會導向完全不同的研究問題。

**使用者**：我覺得最重要的是新生註冊率，畢竟招不到學生什麼都不用談了。

**Socratic Mentor**：
[INSIGHT: 研究焦點 = 招生策略對新生註冊率的實際效果]

好，那再深入一步。如果你的研究結論是「某些策略確實能提高註冊率」，這對誰有用？私立大學的校長？教育部的政策制定者？還是高中生的家長？

不同的讀者群，你的論文寫法會很不一樣。

**使用者**：主要是給大學管理者看的，讓他們知道哪些策略值得投資。

*（socratic 對話持續 8 輪，涵蓋 5 個 Layer...）*

**Socratic Mentor -- 最終彙整**：

```
Research Plan Summary

研究問題：
  在少子化趨勢下，台灣私立大學採用的招生策略（推廣活動、
  入學標準調整、科系新設）對新生註冊率的影響為何？
  哪些策略對不同類型的私立大學（一般/技職）最有效？

方法論：
  混合方法（Mixed Methods）
  - 量化：教育部公開資料分析（109-113 學年度）
  - 質化：3-5 所私立大學招生主管深度訪談

目標期刊等級：TSSCI

已萃取的 INSIGHT（8 條）：
  [INSIGHT 1] 研究焦點 = 招生策略對新生註冊率的實際效果
  [INSIGHT 2] 讀者群 = 大學管理者
  [INSIGHT 3] 三種策略維度：推廣、入學標準、科系調整
  [INSIGHT 4] 需要控制變項：學校地理位置、學校規模、學費水準
  [INSIGHT 5] 方法選擇：混合方法（量化趨勢 + 質化脈絡）
  [INSIGHT 6] 量化資料來源：教育部校務資訊公開平臺
  [INSIGHT 7] 最大限制：無法取得個別學校的行銷預算數據
  [INSIGHT 8] 研究貢獻：為資源有限的私立大學提供證據基礎的策略建議
```

接著由 bibliography_agent 執行文獻搜尋、source_verification_agent 驗證來源...

**Stage 1 完成產出物：**
- RQ Brief（含 FINER 評分）
- Methodology Blueprint（混合方法設計）
- Annotated Bibliography（22 筆文獻，APA 7.0）
- Synthesis Report（主題綜合分析 + 研究缺口）

---

### Orchestrator: Stage 1 --> 2 轉場

```
Stage 1 (RESEARCH) 完成！

產出物：
- RQ Brief：聚焦於私立大學三種招生策略對註冊率的影響
- Methodology Blueprint：混合方法（量化 MOE 資料 + 質化訪談）
- Annotated Bibliography：22 筆文獻（17 中文 + 5 英文）
- Synthesis Report：識別 3 個研究缺口

下一步是 Stage 2 (WRITE)。
因為你是第一次寫論文，我推薦用 plan mode（逐章引導）。
規劃完大綱後，再切到 full mode 產出完整草稿。

要繼續嗎？

進度：[v]研究 -> [..]撰寫 -> [ ]審查 -> [ ]修訂 -> [ ]完稿
```

**使用者**：繼續！

---

### Stage 2: WRITE (plan --> full mode)

```
進入 Stage 2 (WRITE) -- 使用 academic-paper plan mode

載入 academic-paper SKILL.md...
handoff 材料：RQ Brief + Bibliography + Synthesis
intake_agent 自動偵測到 deep-research 產出，跳過冗餘的 Phase 0 問題
啟動 socratic_mentor_agent (plan mode)...
```

**Plan Mode Mentor**：我看到你的 Research Plan Summary 了。研究問題很清楚。我們來逐章規劃論文。先從 Introduction 開始。

你要讓讀者感受到什麼問題的急迫性？換句話說，為什麼讀者現在就該讀這篇論文？

**使用者**：因為少子化已經是現在進行式了，很多大學可能 5 年內就要退場。

**Plan Mode Mentor**：好。那你的 Introduction 的開場可以用一個具體的數字讓讀者感受到急迫性。你知道最近 5 年有多少私立大學退場或停招嗎？

*（plan mode 對話持續 12 輪，涵蓋 6 個章節...）*

**Plan Mode 完成 --> 切換到 full mode**

```
Chapter Plan 完成。接下來切換到 full mode 撰寫完整草稿。

academic-paper draft_writer_agent 根據 Chapter Plan 撰寫...
citation_compliance_agent 驗證引用...
abstract_bilingual_agent 撰寫雙語摘要...
```

**Stage 2 完成產出物：**
- Paper Draft（5,200 字，IMRaD 結構，含雙語摘要）

---

### Orchestrator: Stage 2 --> 3 轉場

```
Stage 2 (WRITE) 完成！

產出物：
- Paper Draft：5,200 字 IMRaD 論文
  - 摘要（中文 420 字 + 英文 230 words）
  - Introduction：研究背景與問題陳述
  - Literature Review：三個主題（少子化趨勢、招生策略分類、成效評估）
  - Methodology：混合方法設計
  - Results：量化發現 + 質化主題
  - Discussion：策略效果比較 + 政策建議
  - References：22 筆（APA 7.0）

下一步是 Stage 3 (REVIEW)。
使用 full mode，模擬 4 位 reviewer 的完整審稿流程。
審查完成後會產出 Editorial Decision 和 Revision Roadmap。

要繼續嗎？

進度：[v]研究 -> [v]撰寫 -> [..]審查 -> [ ]修訂 -> [ ]完稿
```

**使用者**：好，幫我審查。

---

### Stage 3: REVIEW (full mode)

```
進入 Stage 3 (REVIEW) -- 使用 academic-paper-reviewer full mode

載入 academic-paper-reviewer SKILL.md...
傳遞 Paper Draft 給 reviewer...
field_analyst_agent 分析論文領域...
```

**Field Analysis 結果：**
```
論文領域：教育政策 / 高等教育管理
研究範式：Pragmatism（混合方法）
方法類型：量化（次級資料分析）+ 質化（訪談）

Reviewer Configuration:
  EIC:        《教育政策論壇》主編，專長教育經濟學
  Reviewer 1: 量化方法專家，專長教育統計與大型資料庫分析
  Reviewer 2: 高等教育管理學者，專長大學治理與招生政策
  Reviewer 3: 人口學家，專長少子化與勞動市場，跨領域觀點
```

*（4 位 reviewer 平行審查...editorial_synthesizer_agent 彙整...）*

**Editorial Decision：Major Revision**

```
Required Revisions（必須修改）：
R1: [Methodology] 量化分析缺少控制變項（學校規模、地理位置）
    -- Reviewer 1, Priority 1
R2: [Literature]  文獻回顧缺少 2024-2026 年的最新研究
    -- Reviewer 2, Priority 1
R3: [Results]     質化訪談僅 3 所學校，樣本代表性不足
    -- Reviewer 1 & 3 共識, Priority 2
R4: [Discussion]  結論過於籠統，未區分一般/技職大學的差異
    -- Reviewer 2, Priority 2
R5: [Introduction] 研究缺口論證不夠鋒利，需要更具體的數據支撐
    -- EIC, Priority 3
```

**Stage 3 完成產出物：**
- 4 份獨立審查報告
- Editorial Decision Letter: Major Revision
- Revision Roadmap（5 個必修項目 + 3 個建議修改）

---

### Orchestrator: Stage 3 --> 4 轉場

```
Stage 3 (REVIEW) 完成！

審查結果：Major Revision
  - 5 個必須修改項目
  - 3 個建議修改項目
  - 最關鍵問題：量化分析的控制變項 + 文獻更新

下一步是 Stage 4 (REVISE)。
我會將 Revision Roadmap 傳給 academic-paper revision mode，
逐項引導你完成修訂。

修訂完成後進入 Stage 3' (RE-REVIEW) 確認品質。
最多 2 輪修訂循環。

要開始修訂嗎？

進度：[v]研究 -> [v]撰寫 -> [v]審查 -> [..]修訂 -> [ ]完稿
```

**使用者**：開始修訂。

---

### Stage 4: REVISE (revision mode, Round 1)

```
進入 Stage 4 (REVISE) -- 使用 academic-paper revision mode

載入 academic-paper SKILL.md (revision mode)...
傳遞 Paper Draft + Revision Roadmap...
peer_reviewer_agent 監督修訂品質...
```

**Revision 進度追蹤：**
```
R1: [v] 新增控制變項（學校規模、地理位置、學費水準）
R2: [v] 補充 2024-2026 年文獻（新增 8 筆引用）
R3: [v] 補充說明質化樣本選取策略（purposive sampling 理由）
R4: [v] 分離一般/技職大學的分析結果，新增比較表
R5: [v] 改寫 Introduction 第 2-3 段，加入退場學校數據
```

**Stage 4 完成產出物：**
- Revised Draft（6,800 字，比原稿增加 1,600 字）
- Response to Reviewers（R-A-C 格式，逐項回覆）

---

### Orchestrator: Stage 4 --> 3' 轉場

```
Stage 4 (REVISE) 完成！修訂輪次：Round 1

修訂成果：
- 5/5 必修項目全部處理
- 論文從 5,200 字擴充至 6,800 字
- 新增 8 筆 2024-2026 年引用
- 新增一般/技職大學比較表
- Response to Reviewers 已完成

下一步是 Stage 3' (RE-REVIEW)。
使用 full mode 確認修訂品質。
這是第 1 輪修訂循環（最多 2 輪）。

要送出 re-review 嗎？

進度：[v]研究 -> [v]撰寫 -> [v]審查 -> [v]修訂 -> [..]再審 -> [ ]完稿
```

**使用者**：送出再審。

---

### Stage 3': RE-REVIEW (full mode, Loop 1)

```
進入 Stage 3' (RE-REVIEW) -- Loop 1/2

載入 academic-paper-reviewer SKILL.md...
傳遞 Revised Draft + Response to Reviewers...
4 位 reviewer 重新審查修訂品質...
```

**Editorial Decision：Minor Revision**

```
R1 回應：[v] 充分回應，控制變項分析完整
R2 回應：[v] 文獻更新充分
R3 回應：[v] 抽樣策略說明可接受，但建議加一句限制聲明
R4 回應：[v] 比較分析清楚，但 Discussion 最後一段可再精煉
R5 回應：[v] Introduction 改善明顯

新增建議：
S1: Discussion 最後一段建議精煉，聚焦政策建議
S2: 抽樣限制聲明建議移至 Methodology 的 Limitations 段
```

**Editorial Synthesizer**：修訂品質良好。剩餘問題均為 minor，建議 Accept with Minor Revision。

---

### Orchestrator: Stage 3' --> 5 轉場

```
Stage 3' (RE-REVIEW) 完成！

審查結果：Minor Revision (Accept 方向)
  - 所有必修項目通過
  - 剩餘 2 個小型建議修改（non-blocking）

因為是 Minor Revision（非 Major），可以直接進入 Stage 5 (FINALIZE)。
小型修改會在格式化過程中一併處理。

你需要什麼格式的最終版本？
  a) LaTeX (.tex + .bib) -- 適合投稿 TSSCI 期刊
  b) DOCX -- 適合校內審查
  c) PDF -- 適合分享
  d) 全部都要

進度：[v]研究 -> [v]撰寫 -> [v]審查 -> [v]修訂 -> [v]再審 -> [..]完稿
```

**使用者**：全部都要。

---

### Stage 5: FINALIZE (format-convert mode)

```
進入 Stage 5 (FINALIZE) -- 使用 academic-paper format-convert mode

載入 academic-paper SKILL.md (format-convert mode)...
一併處理 2 個 minor revision items...
formatter_agent 執行格式轉換...
```

**Stage 5 完成產出物：**
- `declining_birthrate_private_university.tex` + `.bib`（LaTeX 版）
- `declining_birthrate_private_university.docx`（DOCX 版）
- `declining_birthrate_private_university.pdf`（PDF 版）
- `declining_birthrate_private_university.md`（Markdown 原稿）

---

### Orchestrator: Pipeline 完成

```
+=========================================+
|   Academic Pipeline Status              |
+=========================================+
| 主題：少子化對台灣私立大學招生策略的影響  |
+-----------------------------------------+

  Stage 1 RESEARCH    [v] 已完成
    Mode: socratic
    Outputs: RQ Brief, Methodology,
             Bibliography (22 sources),
             Synthesis

  Stage 2 WRITE       [v] 已完成
    Mode: plan -> full
    Outputs: Paper Draft
             (5,200 words, IMRaD)

  Stage 3 REVIEW      [v] 已完成
    Mode: full
    Decision: Major Revision
    Required Revisions: 5 items

  Stage 4 REVISE      [v] 已完成
    Revision Round: 1
    Addressed: 5/5 required revisions

  Stage 3' RE-REVIEW  [v] 已完成
    Loop: 1/2
    Decision: Minor Revision (Accept)

  Stage 5 FINALIZE    [v] 已完成
    Formats: LaTeX, DOCX, PDF, Markdown

+-----------------------------------------+
| 材料清單：                               |
|   [v] 研究問題摘要 (RQ Brief)            |
|   [v] 方法論藍圖                         |
|   [v] 文獻書目 (30 sources)              |
|   [v] 綜合分析報告                       |
|   [v] 論文草稿                           |
|   [v] 審查報告 (4 份)                    |
|   [v] 修訂路線圖                         |
|   [v] 修訂稿                             |
|   [v] 回覆審查者                         |
|   [v] 最終論文 (4 格式)                  |
+-----------------------------------------+
| 修訂歷程：                               |
|   Round 1: Major -> 5/5 items addressed  |
|   RE-REVIEW: Minor Revision (Accept)     |
+-----------------------------------------+
| Pipeline 完成！                          |
| 最終論文：6,800 字 IMRaD                 |
| 引用：30 筆 (APA 7.0)                   |
| 摘要：中文 420 字 + 英文 230 words       |
+=========================================+

恭喜完成！你的論文已準備好投稿。

最終交付物：
1. LaTeX 版：declining_birthrate_private_university.tex
2. DOCX 版：declining_birthrate_private_university.docx
3. PDF 版：declining_birthrate_private_university.pdf
4. 原稿：declining_birthrate_private_university.md

如果你之後需要：
- 再次修改 --> 直接說「修改論文」（觸發 academic-paper revision mode）
- 做成簡報 --> 說「做成投影片」（觸發 notebooklm-slides-generator）
- 轉成網頁 --> 說「做成互動網頁」（觸發 report-to-website）
```
