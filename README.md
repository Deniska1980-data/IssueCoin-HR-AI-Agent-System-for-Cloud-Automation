## 1️⃣ Project Title & Intro

# 🧠 IssueCoin HR – AI Agent System for Cloud Automation

An AI-driven HR automation system using **Microsoft Forms**, **OneDrive**, **n8n**, **Azure Logic App**, and **SendGrid** — built with **DevSecOps** and **Cloud Automation** principles.

## 📜 2️⃣ Table of Contents

1. Overview
2. Architecture & Components
3. Technical Workflow
4. AI Agents Structure
5. Implementation Screenshots
6. DevSecOps & Security
7. Future Enhancements
8. Author

## 🌍 3️⃣ Overview

IssueCoin HR automates the entire HR leave request and onboarding process.
Employees submit forms, managers approve requests via email buttons, and AI agents handle communication, updates, and notifications — all without Power Automate or corporate licensing.

## ⚙️ 4️⃣ Architecture & Components

| Layer         | Purpose                  | Tools Used             |
|--------       |----------                |-------------           |
| Input         | Data collection          | Microsoft Forms        |
| Storage       | File persistence         | OneDrive               |
| Orchestration | Workflow automation      | n8n                    |
| Logic Layer   | Decision and API control | Azure Logic App        |
| Communication | Email notifications      | SendGrid               |
| Security      | Credentials management   | OAuth2, GitHub Secrets |

## 🔄 5️⃣ Technical Workflow

1. Employee submits a leave request via Microsoft Forms.
2. Data is stored in OneDrive.
3. n8n triggers workflow and sends approval email via SendGrid.
4. Manager clicks Approve/Reject (Azure Logic App webhook).
5. Logic App updates records and sends final notification.

## 🤖 6️⃣ AI Agents Structure
**Main Agent:**
- 🧠 IssueCoin HR — controls all HR automation and triggers workflows.

**Sub-Agents:**
- 🕒 Attendance Agent — monitors and validates attendance data.
- 📩 OnOffBoarding Agent — sends onboarding questionnaire (PDF) before start.
- 💰 Payroll Agent — adjusts salary sheets based on approved leave.

## 🧩 7️⃣ Implementation Screenshots

### Microsoft Forms – Leave Request
![Forms Screenshot](screenshots/forms.png)

### n8n – Workflow Automation
![n8n Workflow](screenshots/n8n_trigger.png)

### Azure Logic App – Approval Logic
![Logic App](screenshots/azure_logicapp.png)

### SendGrid – Email Notification
![SendGrid Email](screenshots/sendgrid_email.png)

### Final AI Agent Message
![Final Email](screenshots/final_email.png)

## 🔐 8️⃣ DevSecOps & Security

- Secrets managed via **OAuth2** and **GitHub Secrets**
- Future migration to **Azure Key Vault**
- HTTPS communication across all webhooks
- GDPR-friendly: no data stored outside controlled cloud space

## 🚀 9️⃣ Future Enhancements

- Integrate **Azure OpenAI** for automatic email message generation
- Add **Logic App + Power BI Dashboard** for analytics
- Use **GitHub Actions CI/CD** for automated deployment of Logic App templates

## 👩‍💻 🔟 Author

Created by **Denisa Pitnerová**  
💼 DevOps & Cloud Automation Enthusiast  
🔗 LinkedIn: [linkedin.com/in/denisa-pitnerova](https://linkedin.com/in/denisa-pitnerova)
