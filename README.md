# 🤖 Cash Voice BOT Pipeline

> An interactive Voice BOT automation workflow and real-time monitoring dashboard — built to demonstrate end-to-end AI-powered loan reminder automation for fintech companies.



---

## 📌 Project Overview

This project simulates a production-grade **Voice BOT automation pipeline** designed for a fintech/lending company like Cash Nigeria. It demonstrates how AI, voice call technology, and workflow automation can work together to:

- Automatically remind customers about overdue loan repayments
- Handle customer responses via Speech-to-Text
- Update CRM records based on call outcomes
- Generate and upload performance reports automatically

---

## 🗂️ Files in This Repository

| File | Description |
|------|-------------|
| `voicebot_workflow.html` | Interactive n8n-style workflow pipeline simulator |
| `voicebot_dashboard.html` | Real-time Voice BOT monitoring dashboard |
| `README.md` | Project documentation (this file) |

---

## 🚀 Live Demo

👉 Open `voicebot_workflow.html` in your browser and click **"Execute Workflow"** to see the full pipeline run in real time, with animated data packets traveling between nodes and live log outputs.

👉 Open `voicebot_dashboard.html` to see how a Voice BOT Manager monitors KPIs, live calls, intent breakdowns, and system alerts.

---

## 🔁 Workflow Pipeline — 7 Nodes

```
⏰ Schedule Trigger
      ↓
🔌 Fetch Loan Data  (HTTP Request → CashXpress Loan API)
      ↓
🤖 AI Voice Script  (Claude / GPT → Personalized call script per customer)
      ↓
📞 Make Voice Call  (Twilio → IVR outbound calls to 142 customers)
      ↓
🎙️ Capture Response (Google Speech-to-Text → Detect customer intent)
      ↓
🗄️ Update CRM       (Write outcomes: will pay / extension / escalate)
      ↓
📊 Send Report      (Upload CSV summary to Google Drive)
```

### Node Details

#### 1. ⏰ Schedule Trigger
Fires every 30 minutes automatically. Identifies customers with overdue loan repayments and passes them downstream.

#### 2. 🔌 Fetch Loan Data
Makes an HTTP GET request to the CashXpress Loan API to retrieve the list of overdue customers including their phone numbers, loan amounts, and due dates.

```json
{
  "endpoint": "/api/loans/overdue",
  "method": "GET",
  "records": 142,
  "sample": {
    "customer": "Mary Adeyemi",
    "phone": "+234 803 XXX XXXX",
    "amount_due": "₦25,000",
    "due_date": "2026-02-14"
  }
}
```

#### 3. 🤖 AI Voice Script
Sends each customer's data to an AI language model (Claude/GPT) which generates a personalised, natural-sounding call script for each customer.

```
"Hello Mary, this is Cash. Your loan repayment of ₦25,000 
was due on February 14th. Please call us or visit our app to 
make payment. Thank you."
```

#### 4. 📞 Make Voice Call
Uses **Twilio** to place outbound voice calls to all 142 customers simultaneously using the AI-generated script delivered via Text-to-Speech IVR.

```json
{
  "calls_initiated": 142,
  "calls_answered": 98,
  "calls_voicemail": 31,
  "calls_failed": 13,
  "containment_rate": "84.2%"
}
```

#### 5. 🎙️ Capture Response
Listens to and transcribes customer responses using **Google Speech-to-Text**, then classifies the intent:

| Intent | Count |
|--------|-------|
| Will pay today | 42 |
| Requesting extension | 28 |
| Disputing amount | 15 |
| Escalate to agent | 13 |

#### 6. 🗄️ Update CRM
Writes call outcomes back to the CashXpress CRM system, updating fields like `last_contact_date`, `call_outcome`, `follow_up_required`, and `promise_to_pay`.

#### 7. 📊 Send Report
Generates a CSV summary report and uploads it to **Google Drive** for the operations team to review.

---

## 📊 Dashboard Metrics

The monitoring dashboard tracks the following KPIs in real time:

| Metric | Description |
|--------|-------------|
| **Containment Rate** | % of calls handled by the bot without human escalation |
| **Total Calls Today** | Volume of outbound calls placed |
| **Avg Handle Time** | Average duration per call interaction |
| **CSAT Score** | Customer satisfaction score from post-call surveys |
| **Fallback Rate** | % of times the bot failed to understand the customer |

---

## 🛠️ Technologies Used

| Layer | Tool |
|-------|------|
| Workflow Automation | n8n |
| Voice Calls | Twilio |
| AI Language Model | Claude (Anthropic) / GPT |
| Speech-to-Text | Google Speech-to-Text |
| API Integration | REST HTTP |
| Reporting | Google Drive |
| Frontend Demo | HTML, CSS, JavaScript |

---

## 💡 Key Concepts Demonstrated

- **Voice BOT architecture** — how components connect end-to-end
- **NLP intent detection** — understanding what customers say
- **API integration** — connecting voice systems to loan data
- **Automation monitoring** — KPI tracking and alert management
- **Workflow orchestration** — managing multi-step automated pipelines

---

## 📁 How to Run Locally

1. Clone or download this repository
2. Open `voicebot_workflow.html` in any modern browser
3. Click **"Execute Workflow"** to simulate the full pipeline
4. Open `voicebot_dashboard.html` to view the monitoring dashboard
5. No installation or server required — runs entirely in the browser

---

## 👩‍💻 Author

**Mary** — Software Developer transitioning into AI Automation & Voice BOT Manage<img width="1280" height="800" alt="Screenshot 2026-02-16 at 14 18 57" src="https://github.com/user-attachments/assets/ba987c6b-9f03-49f9-990d-17869b92afed" />
ment

