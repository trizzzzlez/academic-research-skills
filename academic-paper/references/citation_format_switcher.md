# Citation Format Switcher — 多引用格式切換

Quick-reference for switching between 5 citation formats. Used by `citation_compliance_agent` and `formatter_agent`.

## Format Comparison Matrix

### In-Text Citation Patterns

| Scenario | APA 7th | Chicago (Notes) | Chicago (Author-Date) | MLA 9th | IEEE | Vancouver |
|----------|---------|-----------------|----------------------|---------|------|-----------|
| Single author | (Smith, 2024) | ¹ (footnote) | (Smith 2024) | (Smith 45) | [1] | ¹ (superscript) |
| Two authors | (Smith & Jones, 2024) | ¹ | (Smith and Jones 2024) | (Smith and Jones 45) | [1] | ¹ |
| 3+ authors | (Smith et al., 2024) | ¹ | (Smith et al. 2024) | (Smith et al. 45) | [1] | ¹ |
| Direct quote | (Smith, 2024, p. 45) | ¹ | (Smith 2024, 45) | (Smith 45) | [1, p. 45] | ¹⁽ᵖ⁴⁵⁾ |
| Multiple works | (Chen, 2023; Smith, 2024) | ¹ ² | (Chen 2023; Smith 2024) | (Chen 12; Smith 45) | [1], [2] | ¹˒² |
| Order | Alphabetical | Order of appearance | Alphabetical | Alphabetical | Order of appearance | Order of appearance |

### Reference List Naming

| Format | Section Title | Entry Order |
|--------|--------------|-------------|
| APA 7th | References | Alphabetical |
| Chicago (Notes) | Bibliography | Alphabetical |
| Chicago (Author-Date) | References | Alphabetical |
| MLA 9th | Works Cited | Alphabetical |
| IEEE | References | Order of appearance |
| Vancouver | References | Order of appearance |

## Format Details

### APA 7th Edition
**Discipline**: Education, Psychology, Social Sciences

**Journal Article**:
```
Smith, J. A., & Jones, B. C. (2024). Article title in sentence case.
    Journal Title in Title Case, 45(2), 123-145. https://doi.org/10.xxxx
```

**Book**:
```
Smith, J. A. (2024). Book title in sentence case (2nd ed.). Publisher.
```

**Key rules**: Hanging indent, DOI as URL, sentence case for titles, "&" before last author.

---

### Chicago 17th (Notes-Bibliography)
**Discipline**: History, Humanities, some Social Sciences

**Footnote (first citation)**:
```
1. John A. Smith and Betty C. Jones, "Article Title in Title Case,"
Journal Title 45, no. 2 (2024): 123, https://doi.org/10.xxxx.
```

**Footnote (subsequent)**:
```
2. Smith and Jones, "Article Title," 130.
```

**Bibliography entry**:
```
Smith, John A., and Betty C. Jones. "Article Title in Title Case."
    Journal Title 45, no. 2 (2024): 123-145.
    https://doi.org/10.xxxx.
```

**Key rules**: Full names, title case throughout, footnotes + bibliography, period after URL.

---

### Chicago 17th (Author-Date)
**Discipline**: Natural Sciences, some Social Sciences

**In-text**: (Smith 2024, 45)

**Reference**:
```
Smith, John A. 2024. "Article Title in Title Case." Journal Title
    45 (2): 123-145. https://doi.org/10.xxxx.
```

**Key rules**: Year after author name, full names in reference, title case.

---

### MLA 9th Edition
**Discipline**: Literature, Languages, Cultural Studies

**In-text**: (Smith 45) — author + page, no comma, no year

**Works Cited**:
```
Smith, John A., and Betty C. Jones. "Article Title in Title Case."
    Journal Title, vol. 45, no. 2, 2024, pp. 123-45.
```

**Key rules**: No year in in-text, page numbers always, containers model, no DOI in basic format (include if online), title case for all titles.

---

### IEEE
**Discipline**: Engineering, Computer Science, Technology

**In-text**: [1] — numbered brackets in order of appearance

**Reference**:
```
[1] J. A. Smith and B. C. Jones, "Article title in sentence case,"
    Journal Title, vol. 45, no. 2, pp. 123-145, Feb. 2024,
    doi: 10.xxxx.
```

**Key rules**: Numbered [N], initials before surname, abbreviated month, "doi:" prefix (not URL).

---

### Vancouver
**Discipline**: Medicine, Biomedical Sciences, Nursing

**In-text**: Superscript numbers ¹ or (1) in order of appearance

**Reference**:
```
1. Smith JA, Jones BC. Article title in sentence case. Journal Title.
   2024;45(2):123-145. doi:10.xxxx
```

**Key rules**: Numbered in order of appearance, no spaces in initials, abbreviated journal titles (per NLM), semicolon before volume, colon before pages.

## Conversion Quick Reference

### APA → Chicago (Notes-Bibliography)
1. Change in-text (Author, Year) → footnotes
2. Expand first names in reference list
3. Change sentence case → title case for article titles
4. Add period after URLs
5. Rename "References" → "Bibliography"

### APA → MLA
1. Remove years from in-text, add page numbers
2. Expand first names, change "&" → "and"
3. Change format: vol., no., year order
4. Remove DOIs (unless online-only source)
5. Rename "References" → "Works Cited"

### APA → IEEE
1. Change (Author, Year) → [N] numbered brackets
2. Reorder references by appearance (not alphabetical)
3. Change to initials-first format
4. Add "doi:" prefix to DOIs
5. Abbreviate month names

### APA → Vancouver
1. Change (Author, Year) → superscript numbers
2. Reorder references by appearance
3. Remove spaces between initials
4. Abbreviate journal titles (NLM catalog)
5. Use semicolons/colons for volume/page separators

## 中文引用格式切換

### APA 7.0 中文格式

完整規範詳見 `apa7_chinese_citation_guide.md`。以下為快速參考。

**中文期刊論文**：
```
王大明、李小華（2024）。文章標題。期刊名稱，卷(期)，頁碼。https://doi.org/xxxxx
```

**中文書籍**：
```
張三（2023）。書名。出版社。
```

**政府出版品**：
```
教育部（2024）。出版品名稱。https://url
```

### 中英混合文獻處理

**文中引用**：
- 中文用全形括號「（作者，年份）」
- 英文用半形括號 (Author, Year)
- 中文多位作者用頓號「、」，英文用 &

**參考文獻排序**：

| 方案 | 說明 | 適用情境 |
|------|------|---------|
| **方案 A（推薦）** | 中文在前（依筆畫排序），英文在後（依字母排序） | 多數台灣期刊的慣例 |
| **方案 B** | 中英混合排列（依筆畫/字母統一排序） | 部分國際期刊 |

**同一作者有中英文著作**：分開列出，中文歸中文區，英文歸英文區。

### 格式轉換注意事項（中文論文）

**中文 APA → Chicago**：
1. 出版社格式不同（APA 7 不需出版地，Chicago 需要）
2. 標題改為「標題大寫」格式
3. 加入腳註引用系統

**中文 APA → IEEE**：
1. 加入數字編號 [N]
2. 移除年份在作者後的位置
3. 依引用順序（非筆畫排序）排列

**中文論文格式慣例**：
- 多數台灣期刊使用 APA
- 人文學科（歷史、文學）偶爾使用 Chicago
- 工程/資訊類多使用 IEEE
- 醫學類使用 Vancouver

---

## AI-Generated Content Citation (by Format)

| Format | How to Cite AI |
|--------|---------------|
| APA 7th | OpenAI. (2024). ChatGPT (Version 4) [Large language model]. https://chat.openai.com |
| Chicago | OpenAI. ChatGPT. Version 4. 2024. Large language model. https://chat.openai.com. |
| MLA | "ChatGPT response to [prompt description]." OpenAI, 15 Mar. 2024, chat.openai.com. |
| IEEE | [N] OpenAI, "ChatGPT," ver. 4, 2024. [Online]. Available: https://chat.openai.com |
| Vancouver | OpenAI. ChatGPT [Large language model]. 2024. Available from: https://chat.openai.com |
