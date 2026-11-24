# YouAR｜AI 協同開發 SOP v2.0

本檔是所有組員與 AI Agent 的共用入口。目標是讓第一次使用 Unity、Rider、GitHub 或 AI 的同學也能完成自己的任務。使用繁體中文溝通、文件及提交說明；程式類別、變數及路徑使用清楚英文。AI 是教學助手，不是替學生驗收或替組長決策的人。

## 0. 新同學：只需要把這段貼給 AI

> 我是 YouAR 的組員，請先讀取根目錄 AGENTS.md，依照 SOP 引導我完成工作。我可能不熟悉 Unity、Rider 或 GitHub。請先檢查專案現況與我的分支，再確認我的任務。一次教我一個可操作步驟，告訴我按哪裡、預期看到什麼、如何確認成功。不要直接修改 master，不要自行合併 PR，也不要假裝已完成 Unity 測試。

Codex、Claude Code、Kiro、Antigravity 可使用既有規則入口；Rider AI、ChatGPT 或其他工具若未自動載入，請提供本檔或要求讀取。不要假定工具有本機、GitHub 或 Unity Editor 權限；沒有權限時改為提供操作步驟。ChatGPT 連接 GitHub 不代表可以操作本機 Unity。Unity MCP 為選配，不強制安裝任何 AI 付費工具。

## 1. AI 第一次接手：先讀、再問、再做

依序讀取：
- 本檔、README.md、docs/PROJECT_STATUS.md。
- docs/ 下的「Checkpoint｜筏子溪植物 AR 圖鑑」期中考文件（以實際檔名為準）、本次 Issue 或組長交付的任務。
- docs/02_初始化與InputSystem.md、docs/03_AI協作流程.md；需要時再讀其他教學文件。
- ProjectSettings/ProjectVersion.txt、Packages/manifest.json、packages-lock.json，以及相關 ProjectSettings、Scene、Prefab、Script。
- 有 GitHub 權限時檢查最新 master、個人分支、相關 Issues 與 PR；地端先檢查 git status、目前分支及未提交修改（可使用 Rider Git 視窗或唯讀指令）。

README 與 PROJECT_STATUS 可能仍是原始教學範本，不能因此要求同學重新初始化。以實際檔案、已合併成果、期中需求及組長確認為依據；若互相矛盾，列出差異與待確認事項。原始 Checkpoint 不可任意改寫。

首次回覆用簡短表格列出：組員／負責功能、目前分支、Unity 版本、相關任務與 PR、未提交變更、可用工具、下一步。已知資訊不要重問。缺少組員分支或任務時才詢問；未確認前不修改檔案。已有工作先保留，不擅自 stash、reset、checkout 或覆蓋。

## 2. 專案需求：不要重新發想

YouAR 是「筏子溪植物 AR 圖鑑」，Android 手機掃描紙本植物圖卡，使用 Unity + Vuforia Image Target。植物：美人樹、合子草、土丁桂、水丁香、台灣水龍。
- 首頁：開始掃描、收藏入口。
- 掃描：相機辨識圖卡，顯示跟隨目標的 2D 植物資訊面板。
- 首次辨識解鎖徽章；重複辨識不得增加收藏數。
- 收藏頁顯示五種植物，未解鎖灰階，已解鎖可查看介紹；本機保存進度。
- MVP 不需要 GPS、帳號、網路、雲端、問答、多人連線；核心體驗須可離線。
- Checkpoint 記載五張圖卡五星評級及 Figma 完成，但不代表已匯入 Unity、已驗證實機或已查證植物在筏子溪分布。先驗證一張，再擴充五張；植物資料與素材來源需查證。
- 不自行改用 AR Foundation、其他辨識 SDK 或新增後端。未安裝 Vuforia 時由指定組員整合，不能假定已安裝。

## 3. GitHub 多人協作：老師要求一人一分支，Rider 優先

master 是正式整合版本。每位同學只在組長指定的個人分支工作（例如 ar-pic）；已有分支就沿用，不另建同名或任務分支。新的共用管理分支需組長同意。
- 首次加入：接受 GitHub 協作者邀請 → Rider Get from VCS（或 Clone Repository）→ https://github.com/wupojung/YouAR.git → Unity Hub 加入本機專案 → 確認 Editor 版本 → 在 Rider 確認遠端及個人分支。
- 若個人遠端分支已存在：在 Rider 的 Git Branches 選 origin/個人分支 → Checkout，建立追蹤分支。若不存在：工作區乾淨時更新 master → New Branch → Checkout → Push。切換前保留並確認未提交工作；不得在 master 實作。
- 每次開始：確認自己在正確分支，Fetch、Pull 自己的遠端分支，並檢查 master 是否有新成果；需要同步時，在個人分支使用 Merge origin/master into Current（依 Rider 版本選單可能不同）。遇到衝突先停下，交由檔案負責人及組長協調，不盲目選 Accept Yours/Theirs。
- 完成後在 Rider Commit 視窗逐項檢查 diff（Windows 預設 Ctrl+K），Commit 後 Push（Ctrl+Shift+K）。不要提交無關檔案；提交訊息如 feat: 新增植物收藏頁、fix: 修正重複解鎖。
- Rider 的 GitHub / Pull Requests 功能建立 PR（base=master，head=自己的分支），選組長為 Reviewer。若選單不可用，請組長確認課堂允許的替代方式。AI 可在明確授權且有權限時協助建立 PR；不得代替組長 Approve 或 Merge。
- 同一個尚未合併的 PR 有修改要求時，繼續在原分支 Commit、Push，原 PR 自動更新。先查有無現存 PR，避免重複建立。合併後保留個人分支，下一次工作前與 master 同步；若採 squash merge 導致歷史分歧，請組長協助，不自行 force push。
- 禁止直接 Push master、修改其他組員分支、force push、reset --hard、git clean -fd 或刪除分支。組長決定合併策略，未獲授權不得修改 Repository 設定。
- AI 預設只做唯讀檢查與已確認任務內的本機修改；Commit、Push、PR、遠端寫入須取得同學明確授權。不可因具備權限就直接操作。

## 4. 任務 SOP：每次只做一件可驗證的事

A. 確認：讀取現有 Issue，確認負責人、目的、分支及驗收條件。若沒有 Issue，先提出簡短任務規格，由組長確認後建立，避免重複。不可杜撰 Issue 編號。
B. 規劃：以白話說明預期成果、預計改動檔案、依賴、Unity 操作與驗收；涉及共用檔、套件或架構先取得同意。簡單且已授權的任務直接執行，不反覆詢問。
C. 實作：只修改本次範圍；先找既有程式與資料，重用而非重複建立。
D. 驗證：先編譯，再 Inspector、Play Mode、必要的測試或 Android Build。每個結果標記 PASS / FAIL / NOT RUN / N/A，附證據及重現步驟。
E. 交付：解釋改動、提供操作指引、更新任務交接、檢查 diff；由同學確認後 Commit、Push、PR。
F. 審查：組長或指定獨立審查者檢查需求、diff、測試、衝突、共用檔案與素材安全；修正後重測。組長確認後才合併。

## 5. Unity 技術規範（保留老師原始要求）

- 固定 Unity 6000.3.17f1。保留現有 URP。不得自行升級 Editor、套件或切換渲染管線；套件安裝由指定負責人及組長確認。使用 Package Manager 可相容版本並提交 manifest 與 lock 檔。
- 只用 com.unity.inputsystem 與 UnityEngine.InputSystem；Active Input Handling = Input System Package (New)，禁止 Both / Input Manager (Old)。
- 禁止新增 UnityEngine.Input、Input.GetAxis、Input.GetAxisRaw、Input.GetButton、Input.GetKey、Input.GetMouseButton、舊 StandaloneInputModule。
- 遊戲操作以 Input Actions 定義，集中 Assets/_Project/Input；用 InputActionReference 或 PlayerInput。直接 Keyboard.current/Mouse.current 僅限有明確需求的工具或除錯，須處理裝置不存在。
- uGUI 使用 InputSystemUIInputModule，驗證 UI Actions；UI Toolkit 依該版本官方方式，不強行套用 uGUI。Action Enable/Disable、事件訂閱/取消須成對。
- 自有資產放 Assets/_Project，第三方放 Assets/ThirdParty（套件管理器或 SDK 自動生成的必要路徑保持原樣）。優先在 Unity Editor 移動、重新命名或刪除資產，保留 .meta 與 GUID。
- 不手寫不存在的 Scene、Prefab 或 .meta 來假裝 Editor 工作完成。必要時提供可執行的 Editor 工具或操作指引；新增 SerializeField 或公開欄位要說明 Inspector 指派、預設值。
- 優先簡單 MonoBehaviour 與小型 C# 類別；不任意引入框架、單例群、服務容器。測試需要 asmdef 時按實際 Runtime 與測試依賴設計，不假定現況。
- Vuforia 辨識使用 SDK 既有事件；先證明追蹤及失去追蹤時的顯示行為，再做收藏。圖卡需驗證匯入格式、實際列印大小及 Android 相機權限。

## 6. 避免 Unity 多人衝突與資料外洩

每個人使用獨立 Scene、Prefab、Script 或資產目錄；以下為工作範圍建議，實際負責人由組長指定，不假定目錄已存在。

| 功能 | 工作範圍 |
| --- | --- |
| AR 圖卡與辨識（例如 ar-pic） | 圖片素材、Image Target、獨立測試場景 |
| 植物資訊 | 植物資料、資訊面板 Prefab |
| 收藏與徽章 | 解鎖邏輯、本機儲存、收藏 Prefab |
| UI | 首頁、收藏頁、頁面切換 |
| 組長或指定整合者 | 主場景、共用設定、整合與發布 |

Packages/manifest.json、packages-lock.json、ProjectSettings、共用 Scene/Prefab、Input Actions、AGENTS.md 是共用檔，修改前先協調。不得擅自重建 GUID、覆蓋別人的場景、全專案格式化或搬移資產。若必須跨模組，先約定介面和資料識別 ID。

本 Repo 為公開專案：不得提交 Vuforia License Key、Token、密碼、個資、未授權第三方素材或付費素材。不得提交 Library、Temp、Obj、Logs、UserSettings、Builds、IDE 產生檔及帳密設定。檢查 .gitignore 與實際 diff，資產與對應 .meta 一起提交。若發現密鑰已進入 Git，先停止推送、通知組長並撤銷或輪替，不自行重寫歷史。

## 7. AI 教學模式與除錯 SOP

每次給新手一個可操作步驟：工具／選單路徑 → 要做什麼 → 預期結果 → 如何驗證。不要一次丟出大量程式碼或指令。若學生要求直接實作且已有授權，可執行最小修改後說明。
- 遇到錯誤先取得 Console 第一個相關紅字、完整錯誤訊息、場景及操作步驟，辨別 Git、C# 編譯、Inspector、SDK、Android Build 或實機問題。
- 一次修一個根因，修改前保留原始工作，修正後重新驗證。禁止為了消除錯誤而隨意刪檔、降版、關掉檢查或改成 Both。
- 不知道選單或 API 時，依實際版本及官方文件確認；不要編造操作畫面。
- 無法操作 Editor 時，明確列出學生要做的 Inspector 操作與測試，標記待 Editor 驗證；Rider 編譯或靜態分析不等於 Unity Play Mode / Build 通過。
- 每次交付解釋至少一個核心概念及一個小練習，學生需能說明自己改了什麼、怎麼測試。

## 8. PR 交付格式（配合既有 PR Template）

標題：feat / fix / docs: 清楚描述單一成果。
內文至少包含：
- 任務：Issue #編號（有且實際完成才使用 Closes #編號；未完成使用 Refs），沒有則寫無。
- 負責人、來源分支、目標 master、變更目的與檔案清單。
- Inspector 與操作步驟、Unity 及套件實際版本。
- 驗收項目及 PASS / FAIL / NOT RUN / N/A，測試證據、已知問題與待辦。
- 學生理解的概念與小練習。
- 請組長 Review；Reviewer 不明時請同學指定，不能猜帳號。

提交前檢查：正確分支、無無關變更、資產 Meta 齊全、無秘密、測試狀態真實、未覆蓋他人。缺少必要驗證時先使用 Draft PR 或明示阻塞，不宣稱可合併。AI 不替組長審查自己成果，不自行 Merge 或關閉尚未驗收 Issue。

## 9. 交接與下一次啟動

每次交付提供以下摘要（以 Issue / PR 或個人任務文件保存）：
- 任務、負責人、分支、commit / PR（未建立則寫未建立）
- 已完成、修改檔案、操作方式
- 驗證證據、未完成、阻塞、下一步
- 需要組長或其他組員協助的事項

更新 docs/PROJECT_STATUS.md 的專案級狀態由組長統一整合；組員在任務交接中提供更新內容，避免每個人同時改同一份文件。已確認的結果才標記完成。所有其他 Agent 入口只引用本檔，不維護重複規則。

最後提醒：一人一分支、一次一任務、先測試再交付、組長 Review 後才 Merge。
