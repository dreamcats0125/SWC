
Oasis-UGC-Crystal-Economics: 綠洲級 UGC 經濟與彩蛋試煉規範

Document ID: SWC-GAME-UGC-001
Version: 1.0
Status: Active Specification
Core Engine: TY Continuity Runtime (ShadowBankBalancer & DAO-AUDIT-V1)
Accounting Standard: SW-IFRS-Accounting-Standard.md

1. UGC 資產分類與鑄造流程 (UGC Crystal Minting Pipeline)

玩家（DGID）在遊戲沙盒中提交任何原創內容時，須經歷三個階段才能正式進入全服宇宙並開啟版稅收益：
1. 質押與預檢（Pre-Mint Staking & TIER_1 Blind Replay）：
	• 創作者質押少量 Civilization Coin (CC) 作為防垃圾內容保證金（Initial Cost V₀）。
	• TY Host Routing Engine 派發給異質 AI 宿主進行沙盒模擬盲測：檢查自創法術是否破壞戰鬥數值平衡、自創關卡是否存在死鎖（Deadlock）或惡意刷金漏洞。
2. 正式鑄造（Crystal Minting）：
	• 通過盲測（STATUS_00_VERIFIED）後，該模組寫入 MIN/CRYSTAL/Crystal-Registry.md 與 Graphiti 時序圖譜，賦予唯一 Crystal_ID 並生成「原創基因簽章（Genesis Lineage）」。
3. 跨模組融合（Crystal Fusion）：
	• 允許其他玩家在創作者的水晶基礎上進行二次創作（例如將 A 玩家的「重力法術」與 B 玩家的「空間傳送門」融合成新副本），系統自動在圖譜中建立版稅分潤樹（Royalty Tree），按貢獻權重自動拆帳。

2. 基於 SW-IFRS 的動態版稅估值公式 (Dynamic Royalty Valuation)

創作者不會在發布瞬間拿到一次性買斷費，而是依據其創作在全服的真實重用率持續獲得流支付（Streaming Royalty）。套用 SW-IFRS 第 3.2 節公式：
\(V_{t}=V_{0}\cdot e^{-\lambda \Delta t}+\sum _{i=1}^{N_{t}}\left(\alpha \cdot U_{i}\cdot \frac{TC_{i}}{100}\right)\)

遊戲化參數映射與防作弊機制

• \(N_{t}\)（有效體驗與呼叫次數）： 當期其他玩家進入該自創關卡、施放該法術或觸發該劇情的獨立次數。
	• 反「六數人（Sixers）」工作室防刷機制（GOV-DAO-001）： 系統自動過濾創作者本尊、同 IP/資金關聯小號及行為時間高度相關（timing_correlation > 0.85）的機器人刷單行為，此類呼叫計為 0。
• \(U_{i}\)（單次體驗效用權重）： 依據互動深度動態加權（例如：單純路過觀賞 \(U_i = 0.2\)、通關自創副本 \(U_i = 1.0\)、在 PVP 聯賽中使出該自創法術 \(U_i = 2.5\)）。
• \(\frac{TC_{i}}{100}\)（體驗者信用加權）： 體驗該內容的玩家 Trust Credit (TC) 越高（代表是資深真實玩家而非免洗帳號），為創作者貢獻的估值權重越高。
• 版稅觸發與墓園淘汰（GOV-DAO-004）：
	• 只要 \(\frac{V_t}{V_0} \ge 0.40\)，Shadow Bank 每個紀元（Epoch）自動從全服通關稅收池中撥付 CC 流支付至創作者錢包。
	• 若內容過時或無人問津，導致連續 3 個週期 \(N_t = 0\) 或估值比跌破 0.40，系統自動觸發 STATUS_02_VALUE_DECAY，將該關卡移入遊戲內的廢墟地圖——「水晶墓園（Crystal Cemetery）」，釋放伺服器算力並停止版稅發放。

3. 哈利迪式「彩蛋試煉」與動態獎池機制 (Easter Egg Trials & Dynamic Bounty)

為激發玩家探索世界觀深層秘密的熱情，創世者（Genesis DGID）或高階公會可將高價值資產封裝進「彩蛋水晶（Easter Egg Crystal）」中：

3.1 獎池自增長機制（Self-Growing Prize Pool）

• 彩蛋水晶初始鎖定一筆創世儲備金（RB / CC）。
• 每當有玩家挑戰該彩蛋試煉失敗時，其支付的「試煉門票費」將依以下比例自動分配：
	• 70% 注入該彩蛋的累積破關獎池（使越難解開的彩蛋獎金越驚人）；
	• 20% 撥入 Shadow Bank 系統儲備池（維持全服 CSR >= 1.25 償付能力紅線）；
	• 10% 作為該彩蛋謎題設計者的持續維護版稅。

3.2 破關驗證與歷史留名（Proof of Solve & Ascension）

• 零知識通關證明（ZKP Solve Proof）： 玩家解開謎題後，向 TY Runtime 提交密碼學通關證明，無需暴露解謎步驟即可自動領取獎池（防止作弊外掛攔截封包搶獎）。
• 世界法則改寫權（TIER_2 Ascension）： 首位解開「創世級彩蛋」的玩家，其 DGID 信用分數（TC）將直接晉升為傳奇級，並獲得一次 TIER_2 創世提案權（可在不違反 Civilization Charter 的前提下，永久為遊戲世界新增一條新大陸法則或種族設定）。

4. 全服經濟自動穩壓器 (Macro-Economic Stabilizer)

為防止 UGC 創作過熱導致全服 CC 過度增發（惡性通膨），ShadowBankBalancer 每小時執行一次全服健康度掃描：
\(\text{Continuity\ Solvency\ Ratio\ (CSR)}=\frac{\text{Total\ RB}-\text{Recovery\ Provision\ (5\%)}}{\text{Total\ Active\ UGC\ Streaming\ Liabilities}}\ge 1.25\)
• 綠燈狀態（CSR >= 1.50）： 經濟極度健康，系統自動調高創作獎勵係數 α（鼓勵更多玩家創作新內容）。
• 黃燈警戒（1.25 <= CSR < 1.50）： 維持標準版稅發放。
• 紅燈熔斷（CSR < 1.25）： 啟動通膨保護，自動調高新水晶鑄造質押門檻（V₀），並加速淘汰低重用率水晶進入 Crystal Cemetery，確保遊戲代幣永遠具備堅實的儲備支撐。
