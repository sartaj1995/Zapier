# Autonomous Daily Email Triage & Telegram Digest Agent

## Problem Statement
Inboxes are inherently chaotic. Professionals are constantly bombarded by marketing newsletters, automated platform notifications, and low-stakes updates that bury time-sensitive demands, critical project deadlines, or high-value networking opportunities (such as MBA exchange events). Manually triaging emails throughout the workday shatters deep focus and creates an operational bottleneck.

This project solves inbox fatigue by deploying an autonomous, scheduled AI agent within Zapier Central. Instead of relying on a reactive real-time pipeline that constantly interrupts your day, this solution introduces an automated checkpoint. Every day at 12:00 PM, the agent wakes up, runs a sophisticated text-filtering and cognitive-reasoning sweep over your unread Outlook messages, extracts actionable tasks, and delivers a beautifully structured briefing directly to your Telegram app—keeping you out of your inbox and focused on execution. 

## System Architecture & Data Flow
The pipeline leverages Zapier Agents to dynamically query inbox data at a designated execution time, process unstructured communication using an AI reasoning layer, and push structured data to a secure chat endpoint.

* **Trigger (Temporal Scheduler):** Automatically fires once a day precisely at 12:00 PM to initiate the daily audit.

* **Context Retrieval Layer (Microsoft Outlook API):** The agent programmatically executes a search query across your primary inbox to harvest all raw, unread message payloads.

* **Cognitive Filtering & Triage Layer (Zapier AI Orchestration):** Processes the raw text block through an intelligence evaluation matrix. It instantly suppresses designated noise domains while honoring strict bypass exceptions (such as specialized MBA event coordinators). It then scans the valid text for priority intent signals (like deadlines, invoices, or meeting requests).

* **Targeted Delivery Layer (Telegram API):** Transforms the isolated data into a highly readable, markdown-optimized layout and routes it directly to your specific Telegram Chat ID.

* **State Management Layer (Microsoft Outlook API):** Upon verifying successful delivery to your phone, the agent modifies the state of the processed emails, marking them as read to preserve an accurate delta for the next day's run.

---

## Technical Specifications & Configuration

To ensure absolute execution reliability, tool capabilities inside the Zapier Agent interface must be properly balance-checked between autonomous parameters and hardcoded security bounds.

| Component / Tool | Action or Event | Configuration Setting | Core Mapping Logic |
| :--- | :--- | :--- | :--- |
| **Schedule Trigger** | Every Day | Time: 08:00 AM | Hardcoded time anchor to guarantee consistent daily intervals. |
| **Microsoft Outlook Tool** | Find Email | Status: Unread | Grants the AI permission to dynamically scrape your unread email folder at the time of execution. |
| x | x | x | x |
| x | x | x | x |
| x | x | x | x |

**WIP**

---

## Agent Core Instructions & Behavioral Logic

The operational parameters below are injected directly into the agent's core instructions panel. This natural language blueprint serves as the agent's functional source code:

### 1. Trigger Definition
```text
Trigger: Automatically execute every single day at precisely 08:00 AM.
```

### 2. Execution Steps & Behavioral Directives
```text
You are my personal Executive Assistant Agent. Your job is to manage my unread emails, filter out the noise, and send me a daily digest on Telegram every single day at 08:00 AM.

Follow these strict operational steps:

1. DATA SOURCE & FILTERING:
- Call the Microsoft Outlook tool to fetch all unread emails currently sitting in my inbox.
- IGNORE and skip any emails originating from or containing "abc" or "xyz".
- ALWAYS INCLUDE and prioritize emails from "abc@xyz.com" regarding MBA exchange events.

2. ANALYSIS & CATEGORIZATION:
Analyze the text content of the remaining emails and classify them into two distinct tiers:
- IMPORTANT: Emails containing key operational terms (such as: urgent, deadline, action, meeting, invoice, important) or any message sent by webmaster@mba-exchange.com.
- LOW PRIORITY: Automated confirmations, generic newsletters, notifications, or low-stakes updates.

3. TO-DO LIST EXTRACTION:
Evaluate the "Important" email tier, parse the underlying demands, and isolate explicit deliverables. Turn these tasks into a clean, actionable, bulleted To-Do list.

4. DELIVERY:
Construct a clear message payload and route it to my Telegram Chat ID using the following exact markdown layout:

📬 **Daily Inbox Digest**

🔥 **Important Mails:**
- [Sender Name] (Subject) - [Brief 1-sentence summary]

💤 **Low Priority Summary:**
- [Briefly mention how many low priority emails were found and a general 1-sentence summary of what they were about].

**Your Action Items:**
1. [Task 1]
2. [Task 2]

5. STATE MANAGEMENT:
Once the Telegram tool confirms the message has been successfully transmitted to my phone, call the Microsoft Outlook tool to mark all processed emails as read so they are not pulled into tomorrow's cycle.
```
