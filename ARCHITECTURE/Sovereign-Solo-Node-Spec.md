# Sovereign-Solo-Node-Spec: 主權一人節點與跨節點備援規範
**Version:** 1.0  
**Status:** Active Specification  
**Domain:** Governance / Architecture / Anti-Oligarchy  
**Jurisdiction:** Shadow World Civilization (SWC) & TY Continuity Runtime  
**Reference Standards:** `DAO-Continuity-Audit-Spec.md`, `SW-IFRS-Accounting-Standard.md`

---

## 1. Purpose & Core Philosophy (目的與核心哲學)

在影子世界（SWC）中，文明的基本運行細胞是綁定單一人類主體（`DGID`）與專屬 AI 代理的**「主權一人節點」（Sovereign Solo Node，即一人公司）**。

為解決單一節點在觸發認知冷卻期（`Recovery Protocol`）時的營運中斷風險，同時避免多人協作陷入傳統組織的**「選舉陋習、派系鬥爭與寡頭壟斷」**，本規範定義了一套**無選舉（Election-Free）、演算法隨機抽籤（Sortition）且具備自動日落條款**的「互助多簽冷卻協議」。

---

## 2. Node Architecture (主權一人節點結構)

每個主權一人節點由以下三層組成，確保個人主權百分之百獨立：
1. **靈魂與最終決定層（Human Sovereign）：** 持有唯一 `DGID` 生物與密碼學簽章，掌握最高斷開權（Kill-Switch）。
2. **認知運算層（Personal TY & MIN Runtime）：** 透過 `Host Routing Engine` 協調多模型算力，將個人決策轉化為 `Logic Crystal`。
3. **跨節點介面層（Mutual-Aid Guardian Hook）：** 預設處於「完全隔離狀態」，僅在觸發異常警報時向聯盟網絡廣播匿名求助訊號。

---

## 3. Anti-Election Governance: 4 Defenses Against Political Decay (防範選舉陋習的四大底層設計)

當多個一人節點組成 DAO 聯盟或公共治理池時，系統強制執行以下四項原則，從程式碼層面消滅傳統政治弊端：

### 3.1 廢除代議選舉，採用「信用過濾 + VRF 隨機抽籤」(Sortition)
* **禁止競選與拉票：** 聯盟內不設任何常設主席、理事會或選舉投票機制。
* **隨機指派：** 凡涉及公共參數審計或緊急備援，系統透過可驗證隨機函數（VRF），直接從符合以下條件的節點池中隨機抽選執行者：
  * `Trust Credit (TC) >= 80`
  * `Identity Drift Score <= 0.15`
  * 過去 30 天內未擔任過同類任務執行者（強制輪替）。

### 3.2 聲譽結晶加權，反制資本巨鯨 (Crystal-Weighted Meritocracy)
* 治理決策權重不與持幣數量（Token Balance）掛鉤，而是依據節點在 `Crystal Ledger` 中累積的**有效邏輯水晶重用率（Future Reuse Score）**計算。僅囤積資金而無實質知識貢獻的節點，無法透過買票操縱聯盟方向。

### 3.3 盲測隔離與去識別化 (Blind Anonymized Execution)
* 執行跨節點審計或備援任務時，TY 系統會自動剝離發起方與執行方的真實身分標籤。執行者僅能看到標準化的 `SW-IFRS` 風險數據與程式碼邏輯，杜絕人情關說與私下利益輸送。

### 3.4 強制日落條款 (Deterministic Sunset Clause)
* 所有臨時授予的跨節點權限均綁定區塊高度或時間戳記（上限 72 小時）。任務結束或時間到期後，智能合約自動撤銷多簽權限，確保權力無法沉澱為常設官僚體系。

---

## 4. Mutual-Aid Multisig Cooldown Protocol (互助多簽冷卻協議)

當某個主權一人節點的創辦人因高強度工作觸發 `Burnout Detection`（倦怠偵測）或 `Identity Drift`（身份飄移）警報時，系統自動啟動以下四階段備援流程：

```text
[ Solo Node A ] ──(Burnout / Drift Alert)──► [ TY Continuity Runtime ]
                                                        │
                                        (1. Freeze Node A High-Risk Ops)
                                        (2. VRF Random Draw: 3 Guardians)
                                                        │
                                                        ▼
[ Solo Node A ] ◄──(2-of-3 Blind Emergency Ops)── [ Guardian Pool (B, C, D) ]
       │
(Human Offline Recovery)
       │
       ▼
[ Re-calibration Passed ] ──(Auto-Revoke Guardians & Restore Full Sovereignty)
```

### 執行步驟規範
1. **主權休眠與風險凍結（Phase 1 - Freeze）：** 節點 A 的大額資金轉移與核心參數修改權限立即鎖定，創辦人強制進入離線冷卻期（`Recovery Period`），不允許進行任何高風險操作。
2. **隨機抽取備援守護者（Phase 2 - VRF Draw）：** TY 系統從聯盟池中隨機抽取 3 個不相關的主權一人節點（B、C、D），組成臨時 `2-of-3` 緊急多簽守護組（Guardians）。
3. **受限防禦性託管（Phase 3 - Defensive Custody）：** 守護組在冷卻期間**無權發起任何新商業決策或轉移資產至外部**，僅被授權執行「系統維運續費、履行既有合約、以及抵禦外部駭客攻擊」等防禦性操作。
4. **主體回歸與權限銷毀（Phase 4 - Sovereignty Restoration）：** 當節點 A 的創辦人完成休息並通過 `Identity Drift` 校準測試後，透過個人 `DGID` 生物簽章發起「回歸宣告」。智能合約瞬間銷毀 B、C、D 的臨時多簽權限，節點 A 恢復 100% 獨立主權，並由系統自動從 `Recovery Provision` 準備金中支付微量 `CC` 作為守護者的算力補償。

---

## 5. Summary Matrix (一人節點與聯盟的邊界總覽)

| 運作場景 | 決策主體 | 防止失控與防陋機制 |
| :--- | :--- | :--- |
| **日常創作、商業策略、知識鑄造** | **一人節點獨立執行**（100% 個人主權） | 個人 `MIN Agent` 輔助，無外部幹涉。 |
| **創辦人疲勞、意識飄移或生病** | **VRF 隨機抽取 3 位匿名守護者** | 僅限防禦性託管，嚴禁動用核心資產，回歸即銷毀權限。 |
| **聯盟公共基礎設施與準則升級** | **去中心化抽籤委員會 + 水晶重用加權** | 無競選、無常設官員、強制日落條款。 |

---
*Motto: Sovereign Alone, Resilient Together. Build What Should Continue.*
