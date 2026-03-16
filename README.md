# 請假申請應用與流程 (Leave Request App & Flow)

本專案旨在建立自動化工作流程以管理員工的請假申請，系統運用Microsoft Power Apps 和 Microsoft Power Automate 來精簡流程，並整合 Microsoft Teams 作為使用者互動介面、SharePoint 作為資料儲存與計算，以及 Outlook 用於電子郵件通知。

The project involves creating an automated workflow to manage employee leave requests. The system leverages Microsoft Power Automate to streamline the process, integrating Microsoft Teams for user interaction, SharePoint for data storage and calculations, and Outlook for email notifications.

# 1.使用者介面：Power Apps (User Interface: Power Apps)
**直接的請假申請：** 員工使用自訂的 Power Apps 表單提交請假申請。關鍵資訊（如假期類別、開始／結束日期、日數、原因、審批人員）。
**Intuitive Leave Request Submission:** Employees use a custom Power Apps form to submit leave requests. The UI captures key details (e.g., leave type, start/end dates, reason) and validates inputs in real time.

**Role-Based Access:** Managers and employees have tailored views—employees submit requests, while managers access a dashboard to review/approve/reject requests.

**Real-Time Feedback:** The app provides instant confirmation of submission and tracks request status (e.g., “Pending Approval,” “Approved,” “Rejected”).

# 2. Backend Automation: Power Automate
A multi-step Power Automate flow orchestrates the entire leave approval lifecycle:

**Trigger:** Initiates when a new leave request is submitted via Power Apps (or SharePoint).

**Initial Validation:** Verifies request details (e.g., date conflicts, leave balance) and routes requests to the appropriate manager.

**Approval Stages:**
Sends an adaptive card in Microsoft Teams​ to the manager for review (with approve/reject actions).
Includes logic for escalations (e.g., if a manager does not act within 48 hours, the request is escalated to a senior leader).

**Data Sync & Calculation:** Updates SharePoint​ (the central data store) with request status, leave balances, and historical records.

**Notifications:** Sends email/SMS alerts to employees (e.g., “Your request is approved”) and managers (e.g., “New leave request pending your review”).

<img width="1710" height="854" alt="image" src="https://github.com/user-attachments/assets/77bdf2b7-c613-4483-a7c9-6a5efec89439" />

<img width="1778" height="4930" alt="image" src="https://github.com/user-attachments/assets/1158600f-8e6b-4e31-86e3-8af7b858b14b" />

# 3. Collaboration & Notifications: Microsoft Teams

**Interactive Approvals:** Managers receive leave requests as adaptive cards in Teams, enabling them to approve/reject with a single click (no need to switch apps).

**Team Visibility:** Teams channels display updates on pending/approved requests, fostering transparency across departments.

<img width="556" height="433" alt="image" src="https://github.com/user-attachments/assets/2d26dc57-f800-451e-903e-6d896b3f68cb" />

# 4. Data Management: SharePoint (Centralized Repository)

**Structured Data Storage:** A SharePoint list stores all leave requests, approval history, and employee leave balances. This acts as the “single source of truth” for reporting and auditing.

**Automated Calculations:** Power Automate uses SharePoint data to update remaining leave balances after approvals.

**Version Control & Security:** SharePoint’s built-in permissions ensure only authorized users (e.g., HR, managers) can access sensitive data.

# 5. End-to-End Workflow Summary

**Employee Submits Request:** Uses Power Apps to input leave details.

**Power Automate Triggers:** Validates the request and sends a Teams notification to the manager.

**Manager Approves/Rejects:** Acts via the Teams adaptive card; Power Automate updates SharePoint.

**Employee Notification:** Receives an email/SMS with the decision.

**Data Storage & Reporting:** SharePoint stores all records; HR/teams access reports for planning.

# Benefits
**Efficiency:** Eliminates manual email chains and spreadsheet tracking.

**Transparency:** Employees and managers track requests in real time (via Power Apps/Teams).

**Accuracy:** Automated calculations (leave balances, approval workflows) reduce human error.

**Scalability:** Adapts to growing teams and complex approval hierarchies.
