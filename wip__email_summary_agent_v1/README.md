# Autonomous Daily Email Triage & Telegram Digest Agent

## Problem Statement
Inboxes are inherently chaotic. Professionals are constantly bombarded by marketing newsletters, automated platform notifications, and low-stakes updates that bury time-sensitive demands, critical project deadlines, or high-value networking opportunities (such as MBA exchange events). Manually triaging emails throughout the workday shatters deep focus and creates an operational bottleneck.

This project solves inbox fatigue by deploying an autonomous, scheduled AI agent within Zapier Central. Instead of relying on a reactive real-time pipeline that constantly interrupts your day, this solution introduces an automated checkpoint. Every day at 12:00 PM, the agent wakes up, runs a sophisticated text-filtering and cognitive-reasoning sweep over your unread Outlook messages, extracts actionable tasks, and delivers a beautifully structured briefing directly to your Telegram app—keeping you out of your inbox and focused on execution. 

## System Architecture & Data Flow
The pipeline leverages Zapier Agents to dynamically query inbox data at a designated execution time, process unstructured communication using an AI reasoning layer, and push structured data to a secure chat endpoint.

* **Trigger (Temporal Scheduler):** Automatically fires once a day precisely at 12:00 PM to initiate the daily audit.

* **Context Retrieval Layer (Microsoft Outlook API):** The agent programmatically executes a search query across your primary inbox to harvest all raw, unread message payloads.

* **Cognitive Filtering & Triage Layer (Zapier AI Orchestration):** Processes the raw text block through an intelligence evaluation matrix. It instantly suppresses designated noise domains while honoring strict bypass exceptions (such as specialized MBA event coordinators). It then scans the valid text for priority intent signals (like deadlines, invoices, or meeting requests).

WIP

---

## Technical Specifications & Configuration

WIP

---

## Agent Core Instructions & Behavioral Logic

WIP

### 1. Trigger Definition
WIP

### 2. Execution Steps & Behavioral Directives
WIP
