# 📩 AI Customer Support Email Triage System — n8n Automation

![n8n](https://img.shields.io/badge/n8n-Automation-orange)
![Google Gemini](https://img.shields.io/badge/AI-Google%20Gemini-blue)
![Gmail](https://img.shields.io/badge/API-Gmail-red)
![Telegram](https://img.shields.io/badge/API-Telegram-green)
![JavaScript](https://img.shields.io/badge/Code-JavaScript-yellow)
![License](https://img.shields.io/badge/license-MIT-green)

An AI-powered customer support email automation workflow built using **n8n**, **Google Gemini AI**, **Gmail API**, **Google Sheets**, and **Telegram Bot API**.

This system automatically monitors incoming customer support emails, analyzes messages using AI, classifies customer issues, detects sentiment, assigns priority levels, generates summaries, creates support records, sends urgent notifications, and automatically responds to customers.

**Stack:**  
n8n · Google Gemini AI · Gmail API · Google Sheets · Telegram Bot API · JavaScript · Google Workspace API · AI Automation


---

# 🎯 Project Overview


## Problem

Customer support teams receive large volumes of emails every day, including:


- Technical issues
- Account problems
- Billing concerns
- Product inquiries
- Customer complaints
- Urgent support requests


Manually processing every email creates several challenges:


- Slow response times
- Difficult ticket prioritization
- Missed urgent issues
- Increased support workload
- Inconsistent customer handling


---

## Solution

This project creates an AI-powered email triage system that automatically:


1. Monitors incoming Gmail messages
2. Extracts customer information
3. Analyzes emails using Google Gemini AI
4. Classifies customer requests
5. Detects customer sentiment
6. Assigns ticket priority
7. Generates AI-powered responses
8. Stores support ticket records
9. Sends alerts for urgent issues


The workflow acts as an intelligent support assistant that helps teams process customer requests faster and more efficiently.


---

# ✨ Features


## Email Processing

✅ Gmail inbox monitoring  
✅ Automatic support email detection  
✅ Email content extraction  
✅ Customer information processing  
✅ Automated ticket creation  


## AI Support Analysis

✅ Google Gemini AI classification  
✅ Issue category detection  
✅ Priority prediction  
✅ Sentiment analysis  
✅ AI-generated summaries  
✅ Automated response generation  


## Support Automation

✅ Priority-based ticket routing  
✅ Telegram escalation alerts  
✅ Google Sheets ticket database  
✅ Customer acknowledgment emails  
✅ End-to-end support workflow automation  


---

# 🗺️ System Architecture


```mermaid
flowchart TD


A["📩 Customer Email"]

--> B["📧 Gmail Trigger"]


B --> C["🤖 Google Gemini AI"]


C --> D["📝 Parse AI JSON Output"]


D --> E["🔀 Merge Email + AI Data"]


E --> F{"🚨 Priority Evaluation"}


F -->|High Priority| G["📱 Telegram Alert"]


F -->|Medium / Low| H["📧 Customer Auto Reply"]


G --> H


H --> I["📊 Google Sheets Ticket Database"]

````

---

# 🏗️ Workflow Implementation

# Workflow 1: AI Customer Support Email Triage Pipeline

## Node 1 — Gmail Trigger

### Purpose

Monitor incoming customer support emails and start the automation workflow.

Configuration:

```
Trigger:

Gmail Trigger


Event:

New Email Received
```

Captured Information:

| Field     | Description         |
| --------- | ------------------- |
| Sender    | Customer email      |
| Subject   | Email subject       |
| Body      | Customer message    |
| Timestamp | Email received date |

Example:

```json
{
"sender":
"customer@email.com",

"subject":
"Unable to login",

"message":
"I cannot access my account after resetting my password."
}
```

---

# Node 2 — Google Gemini AI

### Purpose

Analyze customer messages and generate structured support information.

AI Evaluation Criteria:

* Issue category
* Customer sentiment
* Priority level
* Ticket summary
* Suggested response

Example AI Output:

```json
{
"category":
"Technical Support",

"priority":
"High",

"sentiment":
"Negative",

"summary":
"Customer cannot login after password reset.",

"reply":
"Thank you for contacting support. Our team is reviewing your request."
}
```

---

# Node 3 — Code Node

### Purpose

Convert Gemini AI output into structured n8n data.

Processing:

```
Gemini AI Response

        ↓

JavaScript JSON Parser

        ↓

Structured Support Data
```

Example Output:

```json
{
"category":
"Technical Support",

"priority":
"High",

"sentiment":
"Negative"
}
```

---

# Node 4 — Merge Node

### Purpose

Combine Gmail information with AI-generated analysis.

Data Combination:

```
Customer Email Data

+

AI Evaluation

=

Complete Support Ticket
```

Final Ticket Contains:

* Customer information
* Email details
* AI classification
* Priority
* Sentiment
* Summary

---

# Node 5 — IF Node

### Purpose

Route tickets based on priority level.

Logic:

```
Priority = High

        ↓

Urgent Escalation


Priority = Medium / Low

        ↓

Normal Processing
```

## High Priority

Actions:

* Notify support team
* Generate response
* Save ticket

## Medium / Low Priority

Actions:

* Generate acknowledgment
* Save ticket

---

# Node 6 — Telegram Notification

### Purpose

Alert support teams about urgent customer issues.

Example:

```
🚨 High Priority Support Ticket


Category:

Technical Support


Priority:

High


Sentiment:

Negative


Issue:

Customer cannot login after password reset.
```

---

# Node 7 — Gmail Auto Reply

### Purpose

Automatically acknowledge customer requests.

Example:

```
Hello,


Thank you for contacting our support team.


Your request has been received and is currently being reviewed.


Our team will respond as soon as possible.


Thank you.
```

---

# Node 8 — Google Sheets

### Purpose

Store support tickets for tracking and reporting.

Database Structure:

| Field     | Description          |
| --------- | -------------------- |
| Timestamp | Ticket creation date |
| Sender    | Customer email       |
| Subject   | Email title          |
| Category  | Issue classification |
| Priority  | Urgency level        |
| Sentiment | Customer emotion     |
| Summary   | AI-generated summary |
| Status    | Ticket state         |

---

# 📊 Support Ticket Database Example

| Customer                                        | Category  | Priority | Sentiment | Status  |
| ----------------------------------------------- | --------- | -------- | --------- | ------- |
| [customer@email.com](mailto:customer@email.com) | Technical | High     | Negative  | Open    |
| [client@email.com](mailto:client@email.com)     | Billing   | Medium   | Neutral   | Pending |

---

# 🔐 Credentials Required

| Service           | Purpose                      |
| ----------------- | ---------------------------- |
| Gmail OAuth2      | Email monitoring and replies |
| Google Gemini API | AI analysis                  |
| Google OAuth2     | Sheets storage               |
| Telegram API      | Team notifications           |
| n8n Instance      | Workflow execution           |

---

# ⚙️ Setup Guide

## 1. Configure Gmail

Create Gmail OAuth credentials.

Required permissions:

```
Read Emails

Send Emails
```

Connect credentials inside n8n.

---

## 2. Configure Google Gemini AI

Add Gemini API credentials:

```
GOOGLE_GEMINI_API_KEY
```

Test AI classification response.

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

## 4. Configure Telegram Bot

Steps:

1. Create bot using BotFather
2. Copy API token
3. Add Telegram credentials in n8n
4. Configure notification chat ID

---

## 5. Import Workflow

Import:

```
workflow.json
```

Configure:

* Gmail credential
* Gemini API
* Google Sheets
* Telegram Bot

Activate workflow.

---

# 🧪 Testing Checklist

| Test Case               | Expected Result         |
| ----------------------- | ----------------------- |
| Receive customer email  | Workflow starts         |
| Gemini analyzes message | AI data generated       |
| Sentiment detected      | Classification created  |
| High priority found     | Telegram alert sent     |
| Auto reply generated    | Customer receives email |
| Google Sheets updated   | Ticket logged           |

---

# 📁 Repository Structure

```text
AI-Customer-Support-Email-Triage-System/

│
├── README.md
│
├── workflow.json
│
├── screenshots/
│   │
│   ├── workflow.png
│   ├── gmail-trigger.png
│   ├── gemini-analysis.png
│   ├── code-node.png
│   ├── merge-node.png
│   ├── if-node-routing.png
│   ├── google-sheets-ticket-log.png
│   ├── telegram-alert.png
│   └── gmail-auto-reply.png
│
└── LICENSE
```

---

# 📸 Screenshots

Recommended screenshots:

* Complete n8n workflow
* Gmail Trigger configuration
* Gemini AI analysis output
* JSON parsing result
* Merge Node execution
* Priority routing logic
* Google Sheets ticket database
* Telegram escalation message
* Gmail customer response

---

# 🚀 Future Improvements

| Feature                | Implementation                |
| ---------------------- | ----------------------------- |
| Ticket ID System       | Unique support tracking       |
| SLA Monitoring         | Response deadline tracking    |
| Duplicate Detection    | Similar ticket matching       |
| Agent Assignment       | Automatic team routing        |
| CRM Integration        | Salesforce/Zendesk connection |
| Attachment Analysis    | AI document processing        |
| Multi-language Support | Language detection            |
| Slack Integration      | Team communication            |
| Analytics Dashboard    | Support performance metrics   |
| AI Reply Suggestions   | Agent assistance              |

---

# 🎓 Skills Applied

## Automation

* n8n Workflow Automation
* Business process automation
* Event-driven systems
* Support workflow design

## Artificial Intelligence

* Google Gemini AI
* Email classification
* Sentiment analysis
* Prompt Engineering
* AI response generation

## Programming

* JavaScript
* JSON processing
* Data transformation
* Workflow logic

## APIs

* Gmail API
* Google Sheets API
* Telegram Bot API

---

# 📚 Learning Objectives

This project demonstrates:

* Building AI-powered support systems
* Automating email-based workflows
* Integrating LLMs into business processes
* Creating intelligent ticket routing systems
* Designing scalable customer support automation

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

This project is part of my **30-Day n8n Automation Portfolio**, showcasing AI-powered workflow automation using **n8n, Google Gemini AI, APIs, and real-world customer support automation systems**.

---

# 📄 License

MIT License

```
```
