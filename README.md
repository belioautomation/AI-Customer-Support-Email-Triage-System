# 📩 AI Customer Support Email Triage System — n8n Automation

An AI-powered customer support automation workflow built using **n8n**, **Google Gemini AI**, **Gmail**, **Google Sheets**, and **Telegram Bot API**.

This system automatically monitors incoming customer support emails, analyzes messages using AI, classifies customer issues, detects sentiment, assigns priority levels, generates summaries, logs support tickets, sends urgent notifications, and automatically responds to customers.

**Stack:**  
n8n · Google Gemini AI · Gmail · Google Sheets · Telegram Bot · JavaScript · Google Workspace API


---

# 🎯 Project Overview


## Problem

Customer support teams receive large amounts of emails every day, including:

- Technical problems
- Account issues
- Product questions
- Complaints
- Urgent requests


Manual email handling creates challenges:

- Slow response times
- Difficulty identifying urgent issues
- Inconsistent prioritization
- Increased workload for support teams


---

## Solution

This project creates an AI-powered email triage system that:


1. Monitors incoming Gmail messages
2. Extracts customer information
3. Uses Google Gemini AI to analyze emails
4. Classifies customer requests
5. Detects customer sentiment
6. Assigns ticket priority
7. Generates automatic replies
8. Stores support records
9. Alerts teams about urgent issues


---

# ✨ Features


## Email Automation

✅ Gmail inbox monitoring  
✅ Automatic support email detection  
✅ Email content extraction  
✅ Customer information processing  


## AI Analysis

✅ Google Gemini AI classification  
✅ Issue category detection  
✅ Priority prediction  
✅ Sentiment analysis  
✅ AI-generated summaries  
✅ Automated response generation  


## Support Workflow

✅ High-priority escalation  
✅ Telegram team notifications  
✅ Google Sheets ticket tracking  
✅ Automatic customer acknowledgment  


---

# 🗺️ System Architecture


```mermaid
flowchart TD


A["📩 Customer Email"]

--> B["📧 Gmail Trigger"]


B --> C["🤖 Google Gemini AI"]


C --> D["📝 Parse AI JSON Output"]


D --> E["🔀 Merge Gmail + AI Data"]


E --> F{"🚨 Priority Check"}


F -->|High| G["📱 Telegram Alert"]


F -->|Medium / Low| H["📧 Auto Reply"]


G --> H


H --> I["📊 Google Sheets Ticket Log"]

````

---

# 🏗️ Workflow Implementation

# Workflow 1: AI Email Triage Pipeline

## Node 1 — Gmail Trigger

### Purpose

Monitor incoming customer support emails.

Captured Data:

| Field     | Description      |
| --------- | ---------------- |
| Sender    | Customer email   |
| Subject   | Email subject    |
| Body      | Customer message |
| Timestamp | Received date    |

Configuration:

```
Trigger:
Gmail Trigger

Event:
New Email Received
```

---

# Node 2 — Google Gemini AI

### Purpose

Analyze customer emails and generate structured support information.

AI Evaluation:

* Request category
* Priority level
* Customer sentiment
* Issue summary
* Suggested response

Example AI Output:

```json
{
"category":
"Technical",

"priority":
"High",

"sentiment":
"Negative",

"summary":
"Customer cannot log into account after password reset.",

"reply":
"Thank you for contacting support. Our team is reviewing your request."
}
```

---

# Node 3 — Code Node

### Purpose

Parse Gemini AI JSON output into structured workflow data.

Process:

```
Gemini Response

        ↓

JavaScript Parser

        ↓

n8n Data Object
```

Example:

```json
{
"priority":"High",
"category":"Technical",
"sentiment":"Negative"
}
```

---

# Node 4 — Merge Node

### Purpose

Combine original Gmail information with AI analysis results.

Combined Data:

```
Gmail Metadata

+

AI Evaluation

=

Complete Support Ticket
```

---

# Node 5 — IF Node

### Purpose

Route tickets depending on priority.

Logic:

```
Priority = High

        ↓

Urgent Escalation


Priority = Medium/Low

        ↓

Normal Processing
```

---

# Node 6 — Telegram Notification

### Purpose

Notify support teams about urgent issues.

Example:

```
🚨 High Priority Support Ticket


Category:
Technical


Priority:
High


Sentiment:
Negative


Summary:

Customer cannot log into their account.
```

---

# Node 7 — Gmail Auto Reply

### Purpose

Send automatic acknowledgment emails.

Example:

```
Hello,

Thank you for contacting our support team.

Your request has been received and is currently being reviewed.

Our team will respond as soon as possible.
```

---

# Node 8 — Google Sheets

### Purpose

Store support tickets for tracking and reporting.

Database Structure:

| Field     | Description      |
| --------- | ---------------- |
| Timestamp | Ticket date      |
| Sender    | Customer email   |
| Subject   | Email title      |
| Category  | Issue type       |
| Priority  | Urgency level    |
| Sentiment | Customer emotion |
| Summary   | AI summary       |
| Status    | Ticket state     |

---

# 📊 Support Ticket Database Example

| Customer                                    | Category  | Priority | Sentiment | Status  |
| ------------------------------------------- | --------- | -------- | --------- | ------- |
| [user@email.com](mailto:user@email.com)     | Technical | High     | Negative  | Open    |
| [client@email.com](mailto:client@email.com) | Billing   | Medium   | Neutral   | Pending |

---

# 🔐 Credentials Required

| Service       | Purpose            |
| ------------- | ------------------ |
| Gmail OAuth2  | Email monitoring   |
| Gemini API    | AI analysis        |
| Google OAuth2 | Sheets storage     |
| Telegram API  | Notifications      |
| n8n Instance  | Workflow execution |

---

# ⚙️ Setup Guide

## 1. Configure Gmail

Enable Gmail OAuth credentials.

Required access:

```
Read Emails
Send Emails
```

---

## 2. Configure Google Gemini AI

Add Gemini API credentials:

```
GOOGLE_GEMINI_API_KEY
```

Test AI classification.

---

## 3. Create Ticket Database

Create Google Sheet:

```
Customer Support Tickets
```

Columns:

```
Timestamp
Sender
Subject
Category
Priority
Sentiment
Summary
Status
```

---

## 4. Setup Telegram Bot

Steps:

1. Create bot using BotFather
2. Copy token
3. Configure Telegram credential
4. Add notification chat

---

## 5. Import Workflow

Import:

```
workflow.json
```

Configure:

* Gmail
* Gemini AI
* Google Sheets
* Telegram

Activate workflow.

---

# 🧪 Testing Checklist

| Test Case              | Expected Result         |
| ---------------------- | ----------------------- |
| Receive support email  | Workflow triggers       |
| Gemini analyzes email  | AI data generated       |
| High priority detected | Telegram alert sent     |
| Auto reply generated   | Customer receives email |
| Google Sheets updated  | Ticket logged           |
| Sentiment detected     | Correct classification  |

---

# 📁 Repository Structure

```
day13-ai-customer-support-email-triage-system/

│
├── README.md
│
├── workflow.json
│
├── screenshots/
│   │
│   ├── workflow.png
│   ├── gmail-trigger.png
│   ├── gemini-output.png
│   ├── code-node.png
│   ├── merge-node.png
│   ├── if-node.png
│   ├── google-sheets.png
│   ├── telegram-alert.png
│   └── gmail-reply.png
│
├── assets/
│
└── LICENSE
```

---

# 📸 Screenshots

Recommended screenshots:

* Complete n8n workflow
* Gmail Trigger
* Gemini AI analysis
* JSON parser
* Merge Node
* Priority routing
* Google Sheets ticket database
* Telegram escalation
* Gmail response

---

# 🚀 Future Improvements

| Feature                | Implementation              |
| ---------------------- | --------------------------- |
| Ticket ID Generation   | Unique support tracking     |
| SLA Monitoring         | Response deadline tracking  |
| Duplicate Detection    | Similar email matching      |
| Agent Assignment       | Automatic routing           |
| CRM Integration        | Salesforce/Zendesk          |
| Attachment Analysis    | AI document processing      |
| Multi-language Support | Language detection          |
| Slack Integration      | Team communication          |
| Analytics Dashboard    | Support performance metrics |
| AI Reply Suggestions   | Agent assistance            |

---

# 🎓 Skills Applied

## Automation

* n8n Workflow Automation
* Business process automation
* Event-driven systems

## Artificial Intelligence

* Google Gemini AI
* Email classification
* Sentiment analysis
* Prompt Engineering

## Programming

* JavaScript
* JSON processing
* Data transformation

## APIs

* Gmail API
* Google Sheets API
* Telegram Bot API

---

# 📚 Learning Objectives

This project demonstrates:

* Building AI-powered customer support systems
* Automating email workflows
* Integrating LLMs into business processes
* Creating priority-based routing systems
* Designing scalable support automation

---

# 🙌 Acknowledgements

* n8n
* Google Gemini AI
* Gmail API
* Google Sheets API
* Telegram Bot API

---

# 👨‍💻 Author

**Belio C. Sinangote**

BS Information Technology Student
Cebu Technological University (CTU)

GitHub:

[https://github.com/belioautomation](https://github.com/belioautomation)

This project is part of my **30-Day n8n Automation Portfolio**, showcasing AI-powered workflow automation using n8n, Google Gemini AI, APIs, and real-world customer support solutions.

---

# 📄 License

MIT License

```

This one is a stronger portfolio piece than the previous customer support triage because it demonstrates a complete **AI Support Operations Pipeline**:
**Email → AI Understanding → Classification → Escalation → Response → Database Logging**.
```
