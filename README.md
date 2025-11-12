# 🧠 Industry Automation Cloud with AI Agents – HR Department  
**Author: Denisa Pitnerová**  
*Junior DevOps | Cloud & AI Automation Enthusiast | Self-taught Learner*

---

## 💡 Project Overview  
This project was created as part of my personal journey in **DevOps, Cloud and AI automation**.  
My goal is to build a functional HR system that uses **AI agents**, **cloud integrations** and **automation workflows**.  
All processes are orchestrated under the main AI agent **IssueCoin HR**, who manages sub-agents and coordinates HR operations.

---

## 🧩 System Architecture and AI Agents  

The project is divided into several functional agents:

- 🧠 **IssueCoin HR Agent** – the main supervisor, responsible for coordination, reporting and email communication.  
- 👩‍💻 **Attendance Agent** – processes employee leave requests using Microsoft Forms, OneDrive, n8n and SendGrid.  
- 🧳 **OnOff_Boarding Agent** – handles employee onboarding and offboarding workflows via Azure Logic Apps, OneDrive, Outlook and SendGrid API.  
- 📁 **Other agents (Access, Payroll, Reports)** will be added later as the HR ecosystem expands.

Each agent reports to its superior – the **IssueCoin HR Agent**, who supervises them and will eventually use **Azure OpenAI** as its “brain” for autonomous reasoning and decision-making.

---

## 🧠 AI Agent Pyramid Model (Pydantic Architecture)

The **AI Agent Pyramid** represents how the agents communicate and report within the system hierarchy.  
All HR agents report to the main **IssueCoin HR Agent**, who aggregates, analyzes and generates reports.  
This structure is modeled using **Python and Pydantic**, ensuring data consistency and validation across all sub-agents.

```python
from pydantic import BaseModel, EmailStr
from typing import List

class AttendanceAgent(BaseModel):
    name: str = "Attendance Agent"
    tools: List[str] = ["Forms", "OneDrive", "n8n", "SendGrid"]
    def handle_leave_request(self, employee_email: EmailStr):
        return f"Processed leave request for {employee_email}"

class OnOffBoardingAgent(BaseModel):
    name: str = "OnOff_Boarding Agent"
    tools: List[str] = ["Azure Logic Apps", "OneDrive", "SendGrid", "Outlook"]
    def prepare_onboarding(self, employee_name: str):
        return f"Prepared onboarding documents for {employee_name}"

class IssueCoinHRAgent(BaseModel):
    name: str = "IssueCoin HR Agent"
    sub_agents: List[str] = ["AttendanceAgent", "OnOffBoardingAgent"]
    def generate_report(self):
        return f"{self.name} aggregated data from all sub-agents."

# Example interaction
hr_agent = IssueCoinHRAgent()
print(hr_agent.generate_report())

🧩 This model shows:

Clear hierarchy: Sub-agents report upwards to a supervisor.

Data validation: Pydantic ensures each agent's inputs and outputs are structured.

Scalability: New agents (Access, Payroll, etc.) can easily be added to the hierarchy.

Future AI expansion: Azure OpenAI will become the cognitive layer for reasoning and automation.

⚙️ Workflow Phases (Step by Step)
🟢 Phase 1 – Attendance and Leave Requests

The employee submits a leave request via Microsoft Forms.

Data is stored automatically on OneDrive (Excel / CSV).

n8n monitors file changes using triggers.

SendGrid API sends approval/denial emails to the HR manager.

Once “Approve” or “Reject” is clicked, an automatic response is sent to the employee.

The communication flow runs between Yahoo (Employee) and Outlook (Company byDenisa).

🟣 Phase 2 – Pre-Onboarding Workflow

Built in Azure Logic Apps.

Automatically triggers emails 7 days before a new employee’s start date.

Sends a pre-boarding questionnaire via Outlook or SendGrid.

Each email dynamically includes name, team and start date from the OneDrive data source.

🔵 Phase 3 – Onboarding

Once the employee is confirmed, they are added to the Employee Register (Excel/OneDrive).

Access credentials are automatically prepared (OneDrive, Forms, Chatsky).

The OnOff_Boarding agent reports completion to the IssueCoin HR Agent.

🔸 Phase 4 – Agent Communication

All sub-agents (Attendance, OnOff_Boarding, Payroll…) report to the main IssueCoin HR Agent.

IssueCoin HR aggregates data, evaluates results and generates HR reports.

💻 Code and Workflow Examples
1️⃣ n8n Webhook (JSON Payload)
{
  "employee_name": "Denisa Pitnerová",
  "employee_email": "denisa_pitnerova@yahoo.com",
  "date_from": "2025-11-20",
  "date_to": "2025-11-25",
  "reason": "Vacation",
  "workflow": "LeaveRequestApproval"
}

2️⃣ Azure Logic App – HTTP Trigger
{
  "triggers": {
    "manual": {
      "type": "Request",
      "kind": "Http",
      "inputs": {
        "schema": {
          "type": "object",
          "properties": {
            "employee_name": { "type": "string" },
            "employee_email": { "type": "string" }
          }
        }
      }
    }
  }
}

3️⃣ AI Decision Logic (Python + Pydantic)
from pydantic import BaseModel, EmailStr
import random

class LeaveRequest(BaseModel):
    employee_name: str
    employee_email: EmailStr
    date_from: str
    date_to: str
    reason: str

def decide_leave(request: LeaveRequest):
    approved = random.choice([True, False])
    if approved:
        return f"✅ Leave approved for {request.employee_name}."
    else:
        return f"❌ Leave denied for {request.employee_name}."

🔐 DevSecOps & Security Implementation

All API keys, credentials and connections are stored securely:

n8n Credentials Manager

Azure Logic App Connections

OAuth2 and 2FA authentication

Separate app passwords for Outlook, Yahoo and SendGrid

Implemented principles:

🔒 Separation of secrets

🧱 Least privilege principle

🧩 Multi-factor authentication

✅ Connection validation before deployment

🧠 Technical Setup & Testing Challenges

Since I work in a personal, non-corporate environment without enterprise permissions or a team of colleagues,
I had to build and test everything fully on my own from analysis to debugging.

🔥 Main challenges I faced:

Azure and n8n could not connect directly due to permissions, so I had to design alternative workflows.

I didn’t have access to Power Automate or SharePoint, so I used OneDrive and custom webhooks instead.

Learned how to build triggers, debug JSON errors and integrate SendGrid API with SMTP.

Fixed real-world issues such as invalid payloads, missing triggers, or failed API responses.

💬 Every failure was a lesson. It taught me how systems behave under real conditions and how to think like an engineer.

📚 Courses and Knowledge

🎓 Vanderbilt University – Prompt Engineering for Generative AI

⚙️ DevOps & DevSecOps (KodeKloud, IBM, Red Hat)

☁️ Azure & Cloud Fundamentals (Google, Microsoft)

🤖 AI Prompt Engineering & Automation (IBM, SkillUp, Coursera)

🐍 Python & Automation Fundamentals (Coursera)

These courses gave me theoretical foundations,
but my real experience comes from hands-on projects like this one.

👩‍💻 About the Author

I’m Denisa Pitnerová, a junior DevOps and AI automation enthusiast.
I learn step by step, make mistakes, fix them, and always aim to understand why something works — not just how.

I use AI tools like ChatGPT and Gemini as my coding and debugging partners,
but I’m the one who deploys, tests and ensures full functionality.

As Professor Barry from AI for Lawyers said:
“We must never blindly trust AI. Always ask questions why it works, what happens if I change this and how can I make it better?”

This mindset helps me combine AI, DevOps and Cloud into a functional, secure and useful system.

🧩 Project created and maintained by Denisa Pitnerová – Junior DevOps & AI Automation Enthusiast
📧 denisa.pitnerova@yahoo.com
 |  LinkedInhttps://www.linkedin.com/in/denisa-pitnerova
 |  github.com/Deniska1980-data 
 |  kaggle.com/denisapitnerov/code 

