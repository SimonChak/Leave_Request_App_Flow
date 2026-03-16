# 請假申請應用與流程 (Leave Request App & Flow)
本專案旨在建立自動化工作流程以管理員工的請假申請。系統運用 Microsoft Power Apps 與 Microsoft Power Automate 精簡流程，並整合 Microsoft Teams 作為使用者互動介面、SharePoint 作為資料儲存與計算中心，以及 Outlook 作為電子郵件通知工具。

The project creates an automated workflow to manage employee leave requests. It leverages Microsoft Power Apps and Microsoft Power Automate to streamline processes, integrating Microsoft Teams for user interaction, SharePoint for data storage and calculations, and Outlook for email notifications.

# 1. 使用者介面：Power Apps (User Interface: Power Apps)
**請假申請**：員工使用自訂的 Power Apps 表單提交請假，並即時驗證輸入，表單擷取關鍵資訊（例如：假別、開始／結束日期、天數、事由、審批人員）。

**角色式存取**：員工與管理者擁有量身打造的視圖——員工負責提交申請；管理者可在儀表板審閱／核准／駁回申請。

**即時回饋**：應用即刻確認提交，並顯示申請狀態（如「待審核」、「已核准」、「已駁回」）。

**Leave Request Submission**: Employees submit requests via a custom Power Apps form with real-time validation. The form captures key details (e.g., leave type, start/end dates, number of days, reason, approver).

**Role-Based Access**: Employees and managers have tailored views—employees submit requests, while managers use a dashboard to review/approve/reject.

**Real-Time Feedback**: The app provides instant submission confirmation and displays request status (e.g., “Pending Approval,” “Approved,” “Rejected”).

# 2. 後端自動化：Power Automate (Backend Automation: Power Automate)

多步驟 Power Automate 流程協調整個請假核准生命週期：

**觸發條件**：當透過 Power Apps（或 SharePoint）提交新申請時啟動。

**初步驗證**：檢查申請細節（如日期衝突、剩餘假期）並分派至適當管理者。

**核准階段**：在 Microsoft Teams 向管理者發送自適應卡，支援一鍵核准／駁回。

**設有提醒機制**：若 7 天內未處理，將自動重發審批要求

**資料同步與計算**：在 SharePoint（中央資料庫）更新申請狀態、剩餘假期與歷史紀錄。

**通知**：向員工與管理者發送電子郵件／簡訊提醒（例如：「您的申請已核准」、「有新的請假申請待審核」）。

A multi-step Power Automate flow orchestrates the entire leave approval lifecycle:

**Trigger**: Starts when a new request is submitted via Power Apps (or SharePoint).

**Initial Validation**: Verifies details (e.g., date conflicts, leave balance) and routes to the right manager.

**Approval Stages**: Sends an adaptive card in Microsoft Teams to the manager with approve/reject actions.

**Includes a reminder mechanism**: if no action is taken within 7 days, the approval request will be automatically resent.

**Data Sync & Calculation**: Updates SharePoint (the central data store) with status, balances, and history.

**Notifications**: Sends email/SMS alerts to employees (e.g., “Your request is approved”) and managers (e.g., “New leave request pending your review”).

<img width="1710" height="854" alt="image" src="https://github.com/user-attachments/assets/77bdf2b7-c613-4483-a7c9-6a5efec89439" />

<img width="1778" height="4930" alt="image" src="https://github.com/user-attachments/assets/1158600f-8e6b-4e31-86e3-8af7b858b14b" />

<p align="center">[插圖：Power Automate 流程設計圖]</p>

<p align="center">[Illustration: Power Automate flow design]</p>

# 3. 協作與通知：Microsoft Teams (Collaboration & Notifications: Microsoft Teams)

**互動式核准**：管理者以 Teams 自適應卡接收請假申請，可在不離開 Teams 的情況下一鍵處理。

**團隊可見性**：在 Teams 頻道顯示待審與已核准申請更新，促進跨部門透明與協作。

**Interactive Approvals**: Managers receive adaptive cards in Teams and can approve/reject with one click without switching apps.

**Team Visibility**: Teams channels display updates on pending/approved requests, fostering cross-department transparency.

<img width="556" height="433" alt="image" src="https://github.com/user-attachments/assets/2d26dc57-f800-451e-903e-6d896b3f68cb" />

<p align="center">[插圖：Teams 自適應卡範例]</p>
<p align="center">[Illustration: Teams adaptive card sample]</p>

# 4. 資料管理：SharePoint（集中式儲存庫） (Data Management: SharePoint – Centralized Repository)

**結構化資料儲存**：SharePoint 清單保存所有請假申請、核准歷程與員工假期餘額，作為報表與稽核的「單一真相來源」。

**自動計算**：核准後由 Power Automate 依據 SharePoint 資料自動更新剩餘假期。

**版本控管與安全性**：SharePoint 權限確保僅授權人員（如人資、管理者）可存取敏感資料。

**Structured Data Storage**: A SharePoint list stores all requests, approval history, and balances—the single source of truth for reporting and auditing.

**Automated Calculations**: After approval, Power Automate updates remaining balances using SharePoint data.

**Version Control & Security**: SharePoint permissions ensure only authorized users (e.g., HR, managers) can access sensitive data.

# 5. 端到端流程摘要 (End-to-End Workflow Summary)

**員工提交申請**：以 Power Apps 輸入請假細節。

**觸發與驗證**：Power Automate 觸發、驗證並發送 Teams 通知給管理者。

**管理者處理**：於 Teams 自適應卡核准／駁回；Power Automate 同步更新 SharePoint。

**員工通知**：以電子郵件／簡訊收到處理結果。

**資料儲存與報表**：SharePoint 保存紀錄；人資／團隊可存取報表以進行規劃。

**Employee Submits Request**: Uses Power Apps to enter leave details.

**Power Automate Triggers**: Validates the request and sends a Teams notification to the manager.

**Manager Acts**: Approves/rejects via the Teams adaptive card; Power Automate updates SharePoint.

**Employee Notification**: Receives an email/SMS with the decision.

**Data Storage & Reporting**: SharePoint stores all records; HR/teams access reports for planning.

# 效益 (Benefits)

**效率**：消除手動郵件往返與試算表追蹤。

**透明度**：員工與管理者可透過 Power Apps／Teams 即時追蹤申請。

**準確性**：自動計算（假期餘額、核准流程）降低人為錯誤。

**可擴展性**：可因應團隊成長與複雜核准階層進行擴充。

**Efficiency**: Eliminates manual email chains and spreadsheet tracking.

**Transparency**: Employees and managers track requests in real time via Power Apps/Teams.

**Accuracy**: Automated calculations (leave balances, approval workflows) reduce human error.

**Scalability**: Adapts to growing teams and complex approval hierarchies.
