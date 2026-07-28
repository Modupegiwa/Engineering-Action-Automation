# ⚙️ Engineering Action Automation System

An automated Engineering Daily Operational Review (DOR) workflow built using n8n, Google Sheets, and Microsoft Outlook to improve action tracking, ownership visibility, and follow-up management within engineering operations.

The system automates the distribution of engineering action items after daily review meetings by generating personalized reminders for task owners and providing management with a consolidated operational summary.

---

# 📌 Project Overview

Engineering teams often conduct daily operational review meetings where action items are assigned with owners and deadlines. However, manual follow-up can lead to:

- Missed deadlines
- Poor visibility of pending actions
- Delayed escalation of critical issues
- Time-consuming manual reminders

This project addresses these challenges by automating the action management process from task extraction to communication.

---

# 🎯 Objectives

The automation was designed to:

1. Automatically retrieve engineering action items from a centralized tracker.
2. Group tasks by responsible owner.
3. Calculate remaining days until deadlines.
4. Send personalized task reminders to engineers.
5. Generate daily operational summaries for engineering manager.
6. Improve accountability and visibility of outstanding actions.

---

# 🏗️ Workflow Architecture

                ┌─────────────────────────┐
                │   Schedule Trigger      │
                │  (10:00 AM)    │
                └────────────┬────────────┘
                             │
                             ▼
                ┌─────────────────────────┐
                │    Google Sheets        │
                │ Engineering Action      │
                │ Tracker                 │
                └────────────┬────────────┘
                             │
                             ▼
                ┌─────────────────────────┐
                │   Filter Active Tasks   │
                │   Status = Open         │
                └────────────┬────────────┘
                             │
                             ▼
                ┌─────────────────────────┐
                │ JavaScript Processing   │
                │                         │
                │ • Calculate deadline    │
                │   aging                 │
                │ • Group tasks by owner  │
                │ • Identify overdue      │
                │   actions               │
                └────────────┬────────────┘
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
          ▼                  ▼                  ▼

 Individual Task       Daily Summary      Escalation Alert
    Reminder             Report              System

          │                  │                  │
          ▼                  ▼                  ▼

    Engineer Email     Engineering Lead    Engineering Manager
    Notification       Summary             + Owner CC

---

# 🔄 Workflow Breakdown

## 1. Schedule Trigger

The workflow runs automatically on weekdays:

- 10:00 AM → Post daily operational review action distribution

---

## 2. Fetch Engineering Actions

The workflow retrieves action items from Google Sheets containing:

- Task description
- Category
- Task owner
- Deadline
- Status
- Contact information

---

## 3. Task Processing

Using JavaScript within n8n, the workflow:

- Calculates deadline status
- Determines days remaining
- Identifies overdue actions

---

# ✉️ Automated Notifications

## Individual Engineer Reminder

Each engineer receives a personalized message containing:

- Assigned tasks
- Deadline dates
- Remaining days
- Follow-up instructions

---

## Engineering Summary Report

A consolidated operational review summary is generated for engineering manager containing:

- Outstanding actions
- Task owners
- Deadlines
- Deadline status

---

## Automated Escalation Alert System

The system automatically identifies overdue engineering actions and escalates them based on task aging.

### Escalation Logic:

- The workflow continuously evaluates open tasks against their deadlines.
- Any task overdue by *1 day or more* triggers an escalation alert.
- The Engineering Manager receives an escalation email containing all overdue actions.
- The responsible engineers are included in CC to ensure ownership and transparency.

### Escalation Alert Includes:

- Overdue task description
- Responsible owner
- Original deadline
- Number of overdue days

---

# 🛠️ Tech Stack

| Category | Tool |
|---|---|
| Workflow Automation | n8n |
| Data Storage | Google Sheets |
| Programming | JavaScript |
| Email Communication | Microsoft Outlook API |
| Data Analysis | Google Sheets Dashboard |
| Reporting | Power BI (Planned Enhancement) |

---

# 📊 Planned Enhancements

Future improvements include:

- WhatsApp Business API integration
- Automated escalation to Engineering Manager for overdue tasks
- Action closure tracking
- Engineering performance dashboard
- Task aging analysis
- Power BI operational dashboard

---

# 🚀 Getting Started

## Prerequisites

You need:

- n8n Cloud or self-hosted instance
- Google Sheets account
- Microsoft Outlook account
- Engineering action tracker dataset

---

## Installation

Clone repository:

git clone https://github.com/your-username/engineering-action-automation.git

Import workflow:
	1.	Open n8n
	2.	Select Import Workflow
	3.	Upload workflow.json

---

## Configure Credentials

Connect:
	•	Google Sheets credentials
	•	Microsoft Outlook OAuth credentials

Update:
	•	Email recipients
	•	Contact details
	•	Spreadsheet reference

---

## 📂 Repository Structure

engineering-action-automation/

│
├── Engineering DORB Automation.json
├── README.md
├── Screenshots
└── sample-data/
    └── engineering-action-board.xlsx

---

## 💡 Business Impact

This project demonstrates how workflow automation can improve engineering operations by reducing manual follow-up, improving accountability, and creating better visibility of operational actions.
