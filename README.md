# 🎫 Customer Support Ticket Priority Prediction & Automated Assignment System

A Salesforce-based intelligent customer support system that automatically analyzes support tickets, predicts their priority, creates urgent tasks, and assigns them to the appropriate support level using **Salesforce Flow and Agentforce**.

---

## 🎥 Project Resources

- 🎬 **Demo Video:** [Watch Project Demo](https://drive.google.com/file/d/1kZkqjSE2PE4VYHx4s_H7Lt3V36bs3RXK/view?usp=sharing)
- 📄 **Project Documentation:** [View Project Documentation](https://drive.google.com/file/d/1VdhbGEpzcC5DVX9RS7r8ZSt8sG4Z-bxp/view?usp=sharing)

---

## 👥 Team Details

**Team ID:** `SWTID-2026-4152`  
**Team Size:** 4  
**College:** St. Joseph's College of Engineering and Technology, Thanjavur  
**College Code:** `8219`

| Name | Role | NMID |
|---|---|---|
| **Abishek T** | Team Leader | `7E1A977E3A8DCACAC4E4061CA8D874B9` |
| **Joshua S** | Team Member | `A83BB4CDFF13894AA6A477D84C70CFC0` |
| **Arun R** | Team Member | `2B33CF751857FFC9E7F4C63C1B9085C6` |
| **Nawin Prasath S** | Team Member | `83579FFF1150A67B4C045EE491954AEF` |

---

## 📌 Project Overview

Support teams often spend time manually checking tickets, deciding which issues are urgent, and assigning them to the right support agent.

This project automates that process.

The system:

- Retrieves the latest support ticket for a customer Account
- Analyzes the ticket description
- Classifies the ticket as **High, Medium, or Low**
- Automatically creates an urgent task for High-priority tickets
- Assigns High-priority tickets to a **Senior Support Agent**
- Provides conversational access through **Agentforce**
- Performs an optional SLA breach-risk check

The complete solution is built using Salesforce, an Auto-Launched Flow, and an Agentforce subagent.

---

## 🚀 Key Features

### 🔹 Automatic Ticket Priority

Tickets are classified based on keywords in the ticket description:

| Priority | Keywords | Action |
|---|---|---|
| 🔴 **High** | `urgent`, `not working`, `failure` | Create urgent task + assign Senior Support Agent |
| 🟠 **Medium** | `issue`, `slow`, `delay` | Mark for handling shortly |
| 🟢 **Low** | None of the above | Queue for processing |

High-priority conditions are checked first, so if a ticket contains both High and Medium keywords, it is classified as **High**.

---

## 🤖 Agentforce Integration

The project uses an Agentforce subagent called:

**Support Ticket Priority Analysis**

The user only needs to provide an **Account Name**.

Agentforce then:

1. Retrieves the latest ticket.
2. Reads the ticket description.
3. Determines the priority.
4. Triggers the Salesforce Flow.
5. Creates an urgent task for High-priority tickets.
6. Assigns the appropriate support level.
7. Returns the result to the user.

The Agentforce action uses the Auto-Launched Flow as its backend automation.

---

## ⚙️ Technology Stack

- **Salesforce**
- **Salesforce Developer Edition**
- **Trailhead Playground**
- **Salesforce Flow**
- **Auto-Launched Flow**
- **Agentforce**
- **Custom Salesforce Object**
- **Account & Contact Records**
- **Task Management**

---

## 🏗️ Architecture

```text
                User
                  │
                  ▼
            Agentforce
                  │
                  ▼
     Support Ticket Priority
          Analysis Subagent
                  │
                  ▼
        Auto-Launched Flow
                  │
          ┌───────┴───────┐
          ▼               ▼
    Get Account       Get Latest Ticket
          │               │
          └───────┬───────┘
                  ▼
          Analyze Description
                  │
        ┌─────────┼─────────┐
        ▼         ▼         ▼
      HIGH      MEDIUM      LOW
        │         │          │
        ▼         ▼          ▼
  Create Task   Handle      Queue
  Senior Agent  Shortly    Processing
