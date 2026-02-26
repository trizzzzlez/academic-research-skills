# Editorial Decision Standards — 編輯決定判定標準

本文件定義 Accept / Minor Revision / Major Revision / Reject 的明確判定標準，供 `eic_agent` 和 `editorial_synthesizer_agent` 使用。

---

## 1. Decision Categories（決定類別）

### Accept（接受）

**定義**：論文可以在無需進一步審查的情況下出版。

**判定標準**：
- 所有通用維度平均分 >= 4.0
- 沒有任何維度低於 3.0
- 至少 3/4 位 reviewer 推薦 Accept 或 Minor Revision
- 沒有未解決的重大學術問題

**附帶條件**：
- 可能附帶小量 copyediting 建議
- 可能要求最終的格式調整
- 不需要再次送審

**典型情境**：
- 論文已經過多輪修訂，問題已全部解決
- 罕見的一次通過（top-tier 期刊 < 5% 的投稿）

---

### Minor Revision（小幅修改）

**定義**：論文基本合格，需要有限度的修改後可以出版，修改後通常不需要再次送審。

**判定標準**：
- 所有通用維度平均分 >= 3.5
- 沒有任何維度低於 2.5
- 至少 3/4 位 reviewer 推薦 Accept 或 Minor Revision
- 問題可在 2-4 週內解決
- 修改不涉及核心論點或方法的重構

**典型修改項目**：
- 補充少量文獻
- 釐清方法描述的某些細節
- 改善論述的清晰度
- 修正引用格式
- 增加對 limitation 的討論
- 調整結論的表述（避免 overclaiming）

**回覆要求**：
- 作者需逐項回應 reviewer 意見
- 修改後由 EIC 審閱（通常不再送外審）
- 修改期限：2-4 週

---

### Major Revision（大幅修改）

**定義**：論文有潛力但存在重大問題，需要大幅修改後重新審查。

**判定標準**：
- 通用維度平均分在 2.5-3.4 之間
- 某些維度可能低於 2.5（但非致命性的）
- 至少 2/4 位 reviewer 推薦 Major Revision 或更好
- 問題嚴重但可以修復（不是根本性的設計缺陷）
- 修改需要 6-8 週的工作量

**典型修改項目**：
- 重新分析數據（補充分析或修正錯誤）
- 大幅重寫文獻回顧（遺漏關鍵文獻）
- 補充額外的數據收集
- 重新組織論文結構
- 修正方法論的顯著缺陷
- 強化理論框架的應用
- 增加 robustness check

**回覆要求**：
- 作者需撰寫詳細的 point-by-point response letter
- 修改後重新送審（可能送回原 reviewer 或新 reviewer）
- 修改期限：6-8 週
- 通常最多允許 2 輪 Major Revision

---

### Reject（拒絕）

**定義**：論文不適合在此期刊出版，即使修改也無法達到要求。

**判定標準（滿足任一即可觸發 Reject 考量）**：
- 通用維度平均分 < 2.5
- 任何核心維度（方法論、證據）= 1
- 至少 3/4 位 reviewer 推薦 Reject
- 存在無法修復的根本性問題

**Reject 的子類型**：

| 子類型 | 描述 | 建議 |
|--------|------|------|
| **Reject — Out of Scope** | 主題不在期刊範圍內 | 推薦更適合的期刊 |
| **Reject — Fundamental Flaw** | 研究設計有致命缺陷 | 建議重新設計研究 |
| **Reject — Insufficient Contribution** | 缺乏原創性或增量貢獻 | 建議如何強化貢獻 |
| **Reject — Premature** | 論文還不夠成熟 | 建議具體的改善方向 |
| **Reject — Resubmit Encouraged** | 有潛力但需要根本性重構 | 給予詳細的重構建議 |

**即使 Reject 也要做到**：
- 肯定論文的可取之處
- 提供具體的改善建議
- 推薦更適合的期刊（如果是 scope 問題）
- 語氣專業、尊重

---

## 2. Decision Matrix（決定矩陣）

### 基於 Reviewer 推薦的決定矩陣

| EIC | R1 | R2 | R3 | → 建議決定 |
|-----|----|----|-----|-----------|
| Accept | Accept | Accept | Accept | **Accept** |
| Accept | Accept | Accept | Minor | **Accept** (with suggestions) |
| Accept | Accept | Minor | Minor | **Minor Revision** |
| Accept | Minor | Minor | Minor | **Minor Revision** |
| Minor | Minor | Minor | Minor | **Minor Revision** |
| Minor | Minor | Minor | Major | **Minor-to-Major** (視具體問題) |
| Minor | Minor | Major | Major | **Major Revision** |
| Minor | Major | Major | Major | **Major Revision** |
| Major | Major | Major | Major | **Major Revision** |
| Major | Major | Major | Reject | **Major Revision** (最後機會) |
| Major | Major | Reject | Reject | **Reject** (resubmit encouraged) |
| Major | Reject | Reject | Reject | **Reject** |
| Reject | Reject | Reject | Reject | **Reject** |

### 特殊情況處理

**Split Decision（票數平分）**：
- 例如：Accept + Accept + Reject + Reject
- EIC（或 synthesizer）需要深入分析分歧原因
- 傾向採取保守策略：Major Revision，要求作者回應 Reject 方的意見
- 可考慮邀請第五位 reviewer

**One Outlier（一位意見特殊）**：
- 例如：Minor + Minor + Minor + Reject
- 仔細檢查 Reject 的理由
- 如果理由成立且其他人遺漏了，升級為 Major Revision
- 如果理由不充分，維持 Minor Revision 但在 Decision Letter 中提及該意見

---

## 3. Decision Confidence Calibration（決定信心校準）

### Reviewer Confidence Score 的影響

| Confidence | 對決定的影響 |
|-----------|-------------|
| 5 (Very High) | 該 reviewer 的意見權重最高 |
| 4 (High) | 標準權重 |
| 3 (Medium) | 標準權重，但分歧時降權 |
| 2 (Low) | 僅供參考，不作為決定性意見 |
| 1 (Very Low) | 忽略該 reviewer 的推薦（但保留具體意見） |

### 跨維度的嚴重度評估

| 情況 | 嚴重度 | 處理 |
|------|--------|------|
| 方法論有致命缺陷（R1 分數 = 1） | Critical | 即使其他維度優秀，也傾向 Reject |
| 文獻回顧重大遺漏（R2 分數 = 2） | Serious | Major Revision，要求補充 |
| 跨領域觀點被忽略（R3 分數 = 2） | Moderate | Minor/Major，視其他維度 |
| 寫作品質不佳（分數 = 2） | Minor | 不影響學術決定，但要求語言修改 |

---

## 4. Revision Round Policy（修訂回合政策）

### 標準政策

| 回合 | 期待 | 處理 |
|------|------|------|
| R1（首次修訂） | 回應所有 reviewer 意見 | 再次送審或 EIC 審閱 |
| R2（第二次修訂） | 回應殘餘問題 | 通常由 EIC 最終決定 |
| R3（第三次修訂） | 極少見，通常只處理格式 | EIC 最終決定 |

### 升級/降級規則

- Minor Revision 修改不完整 → 可能升級為 Major Revision
- Major Revision 修改優秀 → 可能降級為 Minor Revision 或 Accept
- Major Revision 修改不足 → 可能 Reject（不鼓勵無限次修訂）
- 超過 2 輪 Major Revision → 強烈建議 Accept 或 Reject，不再延續

---

## 5. Professional Ethics of Editorial Review（專業審查倫理守則）

### Reviewer 倫理

1. **保密原則**：審查過程和論文內容保密
2. **利益衝突**：如果與作者有合作或競爭關係，應迴避
3. **時效性**：在承諾的時間內完成審查
4. **建設性**：即使推薦 Reject，也要提供有建設性的回饋
5. **公正性**：不因作者的性別、種族、機構、國籍而有偏見
6. **不剽竊**：不使用審查中看到的未發表想法
7. **適當用詞**：避免人身攻擊、諷刺、貶低性語言

### Editor 倫理

1. **公正決定**：基於學術品質，不受外部壓力影響
2. **透明流程**：Decision letter 要清楚說明理由
3. **合理期限**：給作者足夠的修改時間
4. **申訴管道**：作者有權回應或質疑審查意見
5. **一致標準**：相似品質的論文應得到相似的決定

### 特殊情況的倫理考量

| 情況 | 倫理處理 |
|------|---------|
| 作者是你的學生/同事 | 必須迴避或揭露關係 |
| 論文觀點與你相反 | 評估論證品質，非立場正確性 |
| 論文使用你的理論但誤解 | 可以指出但不能要求引用自己的著作 |
| 發現數據造假嫌疑 | 報告 EIC，由期刊啟動調查程序 |
| 論文與你正在進行的研究相似 | 揭露潛在的利益衝突 |
