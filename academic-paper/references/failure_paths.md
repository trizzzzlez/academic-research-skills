# Failure Paths — 學術論文撰寫失敗路徑圖

本文件記錄 academic-paper skill 在各階段可能遭遇的失敗情境、觸發條件及處理策略。所有 agent 在偵測到失敗情境時應參照本指南。

---

## 失敗路徑總覽

| # | 失敗情境 | 觸發條件 | 嚴重度 | 處理策略 |
|---|---------|---------|--------|---------|
| F1 | 研究基礎不足 | Plan mode Step 0 發現無 RQ / 無數據 | High | 建議先跑 `deep-research` |
| F2 | 論文結構選錯 | structure_architect 發現 RQ 與結構不匹配 | Medium | 退回 Phase 2，建議替代結構 |
| F3 | 字數嚴重超標 | Draft 超過目標字數 30% 以上 | Medium | 識別可刪減段落，建議精簡 |
| F4 | 字數嚴重不足 | Draft 低於目標字數 30% 以上 | Medium | 識別需擴充段落，建議補充 |
| F5 | 引用格式全錯 | citation_compliance 發現 > 50% 格式錯誤 | High | 全面重跑 citation phase |
| F6 | 雙語摘要品質差 | 中英文摘要邏輯不一致 | Medium | abstract_bilingual 重跑 |
| F7 | Peer Review 拒稿 | peer_reviewer 給出 Reject 判決 | High | 分析拒稿原因，建議重大修訂或重構 |
| F8 | Plan mode 不收斂 | > 15 輪對話未完成所有章節 | Medium | 建議跳到 outline-only mode |
| F9 | Handoff 材料不完整 | 來自 deep-research 但缺關鍵材料 | Low | 列出缺失項，建議補充或重跑 |
| F10 | 使用者中途放棄 | 明確表示不想繼續 | Low | 儲存已完成的 Chapter Plan |

---

## 詳細處理策略

### F1: 研究基礎不足

**觸發時機**：Plan mode 的 Step 0（Research Readiness Check）或 Full mode 的 Phase 0

**偵測指標**：
- 使用者無法用一句話描述研究問題
- 沒有任何文獻基礎
- 對研究方法沒有概念
- 主題過於廣泛且無法聚焦

**處理流程**：
```
1. 肯定使用者的研究興趣
2. 具體說明目前缺少什麼
3. 建議使用 deep-research（socratic mode）
4. 說明 deep-research 完成後可以回來繼續
5. 如果使用者堅持繼續，切換為 outline-only mode（低風險）
```

**回應範本**：
```
你的研究主題很有趣，但我注意到目前還缺少明確的研究問題和文獻基礎。

建議你先使用 deep-research 工具來：
1. 系統性地搜尋和整理相關文獻
2. 聚焦出可研究的問題
3. 初步了解可能的研究方法

完成後帶著材料回來，我們就能更有效率地寫出高品質的論文。
```

---

### F2: 論文結構選錯

**觸發時機**：Phase 2（structure_architect_agent）

**偵測指標**：
- RQ 是因果型問題但選了 Literature Review 結構
- 沒有數據卻選了 IMRaD
- 主題適合 Case Study 但選了 Policy Brief
- 字數目標與結構不匹配（如 3000 字 IMRaD）

**處理流程**：
```
1. 指出 RQ 和結構的不匹配之處
2. 解釋為什麼不匹配
3. 建議 1-2 個替代結構
4. 說明替代結構如何更好地回答 RQ
5. 退回 Phase 2 讓使用者重新選擇
```

---

### F3: 字數嚴重超標

**觸發時機**：Phase 4（draft_writer_agent 完成後）

**偵測指標**：
- 實際字數 > 目標字數 x 1.3

**處理流程**：
```
1. 列出每個章節的實際字數 vs 目標字數
2. 識別超標最嚴重的章節
3. 建議刪減策略：
   a. 合併重複論點
   b. 精簡文獻回顧（保留核心文獻）
   c. 移除過度詳細的方法描述
   d. 壓縮 Discussion 中重複的文獻對話
4. 不主動刪減，讓使用者決定
```

---

### F4: 字數嚴重不足

**觸發時機**：Phase 4（draft_writer_agent 完成後）

**偵測指標**：
- 實際字數 < 目標字數 x 0.7

**處理流程**：
```
1. 列出每個章節的實際字數 vs 目標字數
2. 識別不足最嚴重的章節
3. 建議擴充策略：
   a. 增加文獻回顧的深度和廣度
   b. 補充更多證據和範例
   c. 擴展 Discussion（更多文獻對話）
   d. 增加方法論的細節描述
4. 提供具體的擴充方向
```

---

### F5: 引用格式全錯

**觸發時機**：Phase 5a（citation_compliance_agent）

**偵測指標**：
- 引用格式錯誤率 > 50%
- 系統性錯誤（如全部缺 DOI、全部用錯格式）

**處理流程**：
```
1. 分析錯誤模式（系統性 vs 零散）
2. 如果是系統性錯誤：
   a. 識別根本原因（使用者可能選錯了引用格式）
   b. 確認正確的引用格式
   c. 全面重跑 citation phase
3. 如果是零散錯誤：
   a. 逐一修正
   b. 產出修正報告
```

---

### F6: 雙語摘要品質差

**觸發時機**：Phase 5b（abstract_bilingual_agent）

**偵測指標**：
- 中英文摘要涵蓋的重點不一致
- 某一語言的摘要遺漏了重要發現
- 關鍵詞中英文不對應
- 字數嚴重偏離標準

**處理流程**：
```
1. 比對中英文摘要的結構和涵蓋面
2. 列出不一致之處
3. 以論文實際內容為基準重寫
4. 確保兩個版本獨立撰寫但涵蓋相同重點
```

---

### F7: Peer Review 拒稿

**觸發時機**：Phase 6（peer_reviewer_agent 給出 Reject）

**偵測指標**：
- 五維度評分中有 2 項以上低於 60 分
- 存在致命缺陷（邏輯斷裂、核心證據缺失、方法論嚴重瑕疵）

**處理流程**：
```
1. 列出所有被標記為 Critical 的問題
2. 分類問題性質：
   a. 可修復（寫作、格式、小邏輯問題） → 建議 Major Revision
   b. 結構性問題（論點架構需重組） → 退回 Phase 3 重構
   c. 根本性問題（RQ 不可行、數據不足） → 退回 Phase 0 重新評估
3. 產出修訂路線圖
4. 使用者確認後執行修訂
```

**注意**：2 輪修訂仍為 Reject 時，建議使用者：
- 諮詢領域專家
- 重新思考研究設計
- 考慮更換目標期刊（降低要求）

---

### F8: Plan Mode 不收斂

**觸發時機**：Plan mode 對話超過 15 輪

**偵測指標**：
- 使用者反覆修改同一章節的方向
- 無法做出明確決定
- 討論偏離論文主題

**處理流程**：
```
1. 暫停並歸納目前已確定的內容
2. 列出已完成和未完成的章節
3. 提供兩個選項：
   a. 跳到 outline-only mode（直接產出大綱）
   b. 繼續對話（但縮小每次討論範圍）
4. 儲存已完成的 Chapter Plan
```

---

### F9: Handoff 材料不完整

**觸發時機**：intake_agent 偵測到 deep-research 材料但不完整

**偵測指標**：
- 有 RQ 但缺 Annotated Bibliography
- 有 Bibliography 但缺 Synthesis Report
- 有 INSIGHT Collection 但部分 INSIGHT 不完整

**處理流程**：
```
1. 列出已收到和缺失的材料
2. 評估缺失材料的影響：
   a. 缺 Bibliography → 需要 Phase 1（literature_strategist）
   b. 缺 Synthesis → 可以繼續，Phase 3 額外處理
   c. 缺 Methodology Blueprint → 需要 Phase 0 補問
3. 建議：
   a. 回 deep-research 補完
   b. 或在 academic-paper 中補充（增加 Phase 0 訪談問題）
```

---

### F10: 使用者中途放棄

**觸發時機**：使用者明確表示不想繼續

**偵測指標**：
- 「算了」「不寫了」「太複雜」「我再想想」
- 長時間無回應後表示放棄

**處理流程**：
```
1. 尊重使用者的決定
2. 儲存已完成的所有產出：
   - Paper Configuration Record
   - Chapter Plan（已完成部分）
   - INSIGHT Collection
   - 任何已完成的草稿段落
3. 告知使用者可以隨時帶著這些材料回來繼續
4. 不主動勸說繼續（但可以提供鼓勵）
```

**儲存格式**：
```markdown
## Academic Paper — 暫存紀錄

**主題**：{topic}
**進度**：Phase {N} / Step {M}
**已完成**：
- [x] Paper Configuration Record
- [x/partial] Chapter Plan (完成 {N}/{total} 章節)
- [ ] Draft
- [ ] Citation check
- [ ] Peer review

**接續方式**：帶著本紀錄重新啟動 academic-paper，可從 Phase {N} 繼續
```

---

## 失敗路徑之間的關聯

```
F1 (研究基礎不足) → 建議 deep-research → 回來後可能遇到 F9 (材料不完整)
F2 (結構選錯) → 退回 Phase 2 → 可能連帶影響 F3/F4 (字數問題)
F5 (引用全錯) → 可能是 F2 的下游效應（選錯格式）
F7 (拒稿) → 分析後可能需要退回到 F2 (結構) 或 F1 (基礎)
F8 (不收斂) → 可能演變為 F10 (放棄)
```

## 預防措施

| 失敗路徑 | 預防措施 |
|---------|---------|
| F1 | Phase 0 / Step 0 嚴格檢查研究準備程度 |
| F2 | structure_architect 交叉比對 RQ 和結構的匹配度 |
| F3/F4 | draft_writer 每完成一節就檢查字數進度 |
| F5 | draft_writer 在撰寫時就使用正確格式 |
| F6 | abstract_bilingual 以論文內容為基準獨立撰寫 |
| F7 | argument_builder 在 Phase 3 就做論點壓力測試 |
| F8 | socratic_mentor 設定每章節對話上限 |
| F9 | intake_agent 在偵測 handoff 時就完整檢查材料 |
| F10 | 保持對話節奏，避免讓使用者感到疲累 |
