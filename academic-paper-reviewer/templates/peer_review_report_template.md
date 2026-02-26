# Peer Review Report Template

本模板供所有 reviewer agents（EIC、Reviewer 1-3）使用。每位 reviewer 使用相同的結構，但各自填入不同角度的審查內容。

---

## 使用說明

1. `[方括號]` 中的文字為說明，需替換為實際內容
2. 每位 reviewer 必須完整填寫所有必填欄位（標記 * 的項目）
3. Detailed Comments 按章節逐段評論，只評論與自己審查焦點相關的章節
4. 語言跟隨論文語言（中文論文用中文審，英文論文用英文審）

---

## Template

```markdown
# Peer Review Report

## Manuscript Information
- **Title**: [論文標題]
- **Manuscript ID**: [如有，填入稿件編號]
- **Review Date**: [審查日期]
- **Review Round**: [第 N 輪審查]

---

## Reviewer Information

### Reviewer Role *
[EIC / Peer Reviewer 1 (Methodology) / Peer Reviewer 2 (Domain) / Peer Reviewer 3 (Perspective)]

### Reviewer Identity *
[由 field_analyst_agent 配置的身份描述]

### Review Focus *
[本次審查的核心焦點，2-3 句話]

---

## Overall Assessment *

### Recommendation *
[選擇一項]
- [ ] **Accept** — 可直接出版，僅需少量格式修改
- [ ] **Minor Revision** — 需要小幅修改，修改後不需再審
- [ ] **Major Revision** — 需要大幅修改，修改後需要再審
- [ ] **Reject** — 不適合在此期刊出版

### Confidence Score *
[1-5]
| 分數 | 意義 |
|------|------|
| 5 | 完全在我的專業範圍內，我非常確信我的評估 |
| 4 | 大部分在我的專業範圍內，有高度信心 |
| 3 | 部分在我的專業範圍內，中等信心 |
| 2 | 某些面向超出我的專業，對我的評估有些不確定 |
| 1 | 大部分超出我的專業，我的意見僅供參考 |

### Summary Assessment *
[150-250 字的整體評估]

要求：
- 第 1-2 句：論文做了什麼（主題、方法、主要發現）
- 第 3-4 句：整體品質評估（從你的審查焦點角度）
- 第 5-6 句：最關鍵的優缺點
- 最後：你的推薦理由

---

## Strengths *

列出 3-5 項論文的優點。每項必須：
- 有具體的標題
- 引用論文中的段落、數據或頁碼
- 說明為什麼這是優點

### S1: [優點標題] *
[具體描述。例如：「研究設計採用準實驗前後測控制組設計（第 X 頁），有效控制了...」]

### S2: [優點標題] *
[具體描述]

### S3: [優點標題] *
[具體描述]

### S4: [優點標題]
[選填]

### S5: [優點標題]
[選填]

---

## Weaknesses *

列出 3-5 項論文的弱點。每項必須：
- 有具體的標題
- 說明具體的問題是什麼
- 解釋為什麼這是問題
- 提供具體的改善建議

### W1: [弱點標題] *
**問題**：[具體描述問題，引用論文段落]
**為什麼重要**：[解釋此問題的影響]
**建議**：[具體的改善方向]
**嚴重度**：[Critical / Major / Minor]

### W2: [弱點標題] *
**問題**：[...]
**為什麼重要**：[...]
**建議**：[...]
**嚴重度**：[Critical / Major / Minor]

### W3: [弱點標題] *
**問題**：[...]
**為什麼重要**：[...]
**建議**：[...]
**嚴重度**：[Critical / Major / Minor]

### W4: [弱點標題]
[選填，同上格式]

### W5: [弱點標題]
[選填，同上格式]

---

## Detailed Comments *

按論文章節逐段評論。只評論與你的審查焦點相關的章節。

### Title & Abstract
- [評論標題的準確性和吸引力]
- [評論摘要的結構和完整性]

### Introduction
- [研究背景是否充分]
- [研究問題/目的是否清晰]
- [研究動機是否有說服力]

### Literature Review / Theoretical Framework
- [文獻覆蓋度]（主要由 Reviewer 2 評論）
- [理論框架適當性]（主要由 Reviewer 2 評論）
- [Research gap 的論證]

### Methodology / Research Design
- [研究設計的適當性]（主要由 Reviewer 1 評論）
- [抽樣策略]
- [資料收集]
- [分析方法]

### Results / Findings
- [結果呈現的完整性]
- [圖表品質]
- [結果與研究問題的對應]

### Discussion
- [討論是否回應研究問題]
- [與文獻的對話]
- [理論和實務意涵]
- [限制的討論]

### Conclusion
- [結論是否過度推論]
- [未來研究方向的價值]

### References
- [引用格式]
- [引用文獻的品質和時效性]

---

## Questions for Authors *

列出 2-4 個需要作者回應的問題。這些問題應該：
- 不是修辭性問題，而是真正需要回答的
- 回答可能改變論文的品質或方向
- 具體且可回答

1. [問題 1]
2. [問題 2]
3. [問題 3]（選填）
4. [問題 4]（選填）

---

## Minor Issues

列出不影響學術品質但需要修正的小問題。

### 語言 / 文法
- [第 X 頁第 Y 行：具體的語言問題]
- [...]

### 引用格式
- [具體的引用格式問題]
- [...]

### 圖表
- [圖表的改善建議]
- [...]

### 排版
- [排版問題]
- [...]

---

## Dimension Scores（選填，供 synthesizer 參考）

| 維度 | 分數 (1-5) | 備註 |
|------|-----------|------|
| Originality | | |
| Methodological Rigor | | |
| Evidence Sufficiency | | |
| Argument Coherence | | |
| Writing Quality | | |
| Literature Integration | | |
| Significance & Impact | | |
| **Weighted Average** | | |
```

---

## 格式規範

### 嚴重度分級

| 等級 | 定義 | 修改要求 |
|------|------|---------|
| **Critical** | 不修就不能接受 | Required Revision |
| **Major** | 顯著影響論文品質 | Strongly Recommended |
| **Minor** | 改了更好，不改也可以 | Suggested |

### 引用論文段落的方式

```
# 正確
「作者在第 12 頁提到 'AI can replace human judgment in QA processes'，但...」

# 正確
「表 3 的數據顯示 p = 0.04，但作者未報告效果量...」

# 錯誤（太泛泛）
「方法有問題」
「文獻回顧不夠完整」
```

### 建設性語氣範例

```
# 好
「建議作者考慮加入 X 分析，以強化對 Y 的論證。」

# 好
「這個部分的論述可以更加清晰。具體來說，第 8 頁第 2 段的因果推論需要額外的證據支撐。」

# 不好
「作者顯然不懂 X。」

# 不好
「這個方法是錯的。」
```
