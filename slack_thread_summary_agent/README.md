# Autonomous Slack Thread Summary Agent

## Business Problem Statement
Slack workspaces move at a chaotic pace. Active conversations regularly spiral into long, messy threads containing dozens of replies, split decisions, and unassigned deliverables. For professionals managing multiple channels, keeping up with these exploding notification threads creates a massive operational bottleneck. Manually reading through historical context eats up valuable focus time, and critical action items are frequently buried or completely forgotten.

This project solves this information tracking issue by deploying an autonomous, no-code AI agent within Zapier. Instead of setting up rigid, traditional automation pipelines that require static channel definitions, this solution uses a flexible AI reasoning layer. By dropping a single notebook emoji reaction onto any message, you kick off an automatic triage process. The agent extracts the entire conversational string, distills the key points, isolates every explicit assignment, and sends a structured digest straight to your personal inbox. 

## System Architecture & Data Flow
The pipeline leverages Zapier Agents to dynamically evaluate runtime data, access third-party communication tools, and execute context-aware workflows.

* **Trigger (Slack Reaction):** Wakes up the moment you add a specific closed notebook (📓) emoji reaction to a message in any monitored public channel.
* **Dynamic Context Retrieval Layer (Slack API):** Traditional automations require hardcoding a specific channel or message path. This agent overcomes that restriction by using dynamic routing. It analyzes the incoming trigger payload and automatically isolates the correct Channel ID and Thread Timestamp on the fly to scrape the entire message tree.
* **Cognitive Summarization Layer (Zapier AI Orchestration):** Consolidates the unstructured conversational replies into a linear text string. It passes this data block to a high-capacity language model, instructing it to run an analytical sweep that separates high-level background information from time-sensitive operational tasks.
* **Targeted Delivery Layer (Gmail API):** Routes the final structured text straight to a designated personal inbox. The distribution path uses a hardcoded, secure email destination to prevent the AI from misrouting sensitive internal data, while allowing the subject line and body copy to generate dynamically.

---

## Technical Specifications & Configuration

To make this agent functional, tool permissions inside the Zapier Agent interface must be split between autonomous decision-making and fixed structural boundaries.

| Component / Tool | Action or Event | Configuration Setting | Core Mapping Logic |
| :--- | :--- | :--- | :--- |
| **Slack Trigger** | New Reaction Added | Reaction: notebook (📓) | Listens globally across public spaces for the specific validation emoji. |
| **Slack Tool** | Retrieve Thread Messages | Channel & Timestamp: Let agent select a value | Grants the AI permission to dynamically extract location coordinates from the trigger event. |
| **Gmail Tool** | Send Email | To: Hardcoded Specific Value | Restricts routing to your explicit email address to ensure data security. |
| **Gmail Tool** | Send Email | Subject & Body: Let agent select a value | Allows the AI to generate custom subject titles and markdown-formatted email layouts. |

---

## Agent Core Instructions & Behavioral Logic

The operational guardrails below are injected directly into the agent's core instructions panel. This natural language script serves as the software's functional source code:

### 1. Trigger Definition
```text
Trigger: When you add a notebook reaction (📓 emoji) to a message in Slack.