# 🤖 AI Customer Support Email Triage System

> **Day 13 – 30-Day n8n Automation Roadmap**

An AI-powered customer support automation workflow built with **n8n**, **Google Gemini AI**, **Gmail**, **Google Sheets**, and **Telegram**. The workflow automatically classifies incoming emails, determines their priority, logs support tickets, sends notifications for urgent issues, and replies to customers.

---

## 📌 Overview

This workflow helps automate customer support by reducing manual email triage.

For every new email received:

- 📥 Monitors Gmail inbox
- 🤖 Uses Google Gemini AI to analyze the email
- 🏷️ Classifies the email category
- 🚨 Assigns a priority level
- 😊 Detects customer sentiment
- 📝 Generates a short summary
- 📊 Logs the ticket into Google Sheets
- 📱 Sends Telegram alerts for high-priority tickets
- 📧 Sends an automatic acknowledgment email

---

## ✨ Features

- Gmail Trigger
- AI Email Classification
- Structured JSON Output
- Prompt Engineering
- JavaScript JSON Parsing
- Conditional Routing (IF Node)
- Google Sheets Ticket Logging
- Telegram High-Priority Notifications
- Automatic Gmail Replies
- Self-hosted n8n Compatible

---

## 🛠️ Tech Stack

- n8n (Self-hosted)
- Google Gemini AI
- Gmail API
- Google Sheets API
- Telegram Bot API
- JavaScript

---

## 🏗️ Workflow Architecture

```text
                    Gmail Trigger
                          │
                          ▼
                 Google Gemini AI
                          │
                          ▼
              Code Node (Parse JSON)
                          │
                          ▼
                     Merge Node
                          │
                          ▼
               IF (Priority == High?)
                 ┌───────────────┐
                 │               │
             TRUE              FALSE
                 │               │
         ┌───────┼───────┐       ├──────────────┐
         ▼       ▼       ▼       ▼              ▼
 Telegram  Gmail Reply  Google Sheets Gmail Reply Google Sheets
```

---

## 🧠 AI Output

The AI extracts the following information:

- Category
- Priority
- Sentiment
- Summary
- Professional Reply

### Example Output

```json
{
  "category": "Technical",
  "priority": "High",
  "sentiment": "Negative",
  "summary": "Customer cannot log into their account after password reset.",
  "reply": "Thank you for contacting us. We have received your request and our support team is reviewing it."
}
```

---

## 📂 Email Categories

- Billing
- Technical
- Refund
- Complaint
- Feedback
- Account
- General
- Other

---

## 🚨 Priority Levels

| Priority | Workflow |
|-----------|----------|
| High | Telegram → Gmail Reply → Google Sheets |
| Medium | Gmail Reply → Google Sheets |
| Low | Gmail Reply → Google Sheets |

---

## 😊 Sentiment Detection

The AI classifies emails as:

- Positive
- Neutral
- Negative

---

## 📊 Google Sheets Log

Each email is automatically stored with the following information:

| Column |
|----------|
| Timestamp |
| Sender |
| Subject |
| Category |
| Priority |
| Sentiment |
| Summary |
| Status |

Example:

| Timestamp | Sender | Subject | Category | Priority | Status |
|-----------|--------|---------|----------|----------|--------|
| 2026-07-10 | customer@example.com | Unable to Login | Technical | High | Open |

---

## 📱 Telegram Notification

High-priority emails generate an instant notification.

Example:

```
🚨 HIGH PRIORITY SUPPORT EMAIL

From:
customer@example.com

Subject:
Unable to Login

Category:
Technical

Priority:
High

Summary:
Customer cannot log into their account after password reset.
```

---

## 📧 Automatic Email Reply

Example:

```
Hello,

Thank you for contacting us.

We have successfully received your support request.

Our support team will review your concern as soon as possible.

Thank you,
Customer Support Team
```

---

## 🔄 Workflow Process

1. Gmail Trigger detects a new email.
2. Google Gemini AI analyzes the email.
3. AI returns structured JSON.
4. JavaScript parses the response.
5. Merge node combines AI output with Gmail metadata.
6. IF node checks the priority.
7. High-priority emails trigger a Telegram notification.
8. Ticket information is logged into Google Sheets.
9. Customer receives an automatic acknowledgment email.

---

## 📸 Screenshots

Add screenshots after testing.

```
screenshots/
│
├── workflow.png
├── gmail-trigger.png
├── gemini-output.png
├── code-node.png
├── merge-node.png
├── if-node.png
├── telegram-alert.png
├── google-sheets.png
└── gmail-reply.png
```

---

## 📁 Repository Structure

```
day13-ai-customer-support-email-triage-system/
│
├── README.md
├── workflow.json
├── screenshots/
├── assets/
└── LICENSE
```

---

## 🚀 Future Improvements

- Ticket ID generation
- SLA monitoring
- Duplicate email detection
- Agent assignment
- CRM integration
- Attachment analysis
- Multi-language support
- Slack & Microsoft Teams notifications
- Dashboard with ticket analytics
- AI-generated response suggestions

---

## 📚 Skills Demonstrated

- Workflow Automation
- AI Integration
- Prompt Engineering
- JSON Parsing
- JavaScript
- Gmail API
- Google Sheets API
- Telegram Bot API
- Conditional Logic
- Business Process Automation

---

## 🎯 Learning Outcomes

This project demonstrates how AI can automate customer support workflows using n8n and Google Gemini AI. It showcases practical skills in workflow design, API integration, AI-powered classification, conditional routing, and automated communication.

---

## 👨‍💻 Author

**Belio Sinangote**

- 🎓 BS Information Technology Student
- 🤖 n8n Automation Enthusiast
- 💻 Self-hosted Automation Developer

---

## 📅 Project Information

- **Project:** AI Customer Support Email Triage System
- **Roadmap:** 30-Day n8n Automation Roadmap
- **Day:** 13
- **Status:** ✅ Completed
- **Workflow Version:** 1.0
