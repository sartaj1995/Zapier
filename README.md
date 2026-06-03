# Enterprise Automation & AI Engineering Portfolio (using Zapier)

This repository holds my production-ready automation pipelines. It shows how I connect data ops, low-code tools, and LLMs to fix slow, manual corporate processes. 

Instead of just connecting apps blindly, I focus on strict data mapping, solid prompt engineering, and human-in-the-loop safety frameworks built for real analytics environments.

---

## 📂 Project Directory

Below are the operational engines running inside this repository. Each project lives in its own subfolder with complete JSON configurations, raw source code scripts, and prompt blueprints.

### 1. [Automated Video Production Pipeline: End-to-End Content Orchestration Engine](./youtube_shorts_generator)
* **Core Objective:** Automates the extraction, script generation, and publication scheduling of short-form video content. 
* **The Stack:** Zapier, Google AI Studio (Gemini), Custom Python Data Transformations, YouTube Data API.
* **Key Innovation:** Features an isolated scripting step that handles messy text extraction and runs it through a programmatic formatting filter. This guarantees clean outputs before hitting production APIs.

### 2. [AI-Powered Customer Support Routing & Intelligent Drafting Engine](./customer_support_automation_v1)
* **Core Objective:** Eliminates repetitive ticket queues by dynamically generating human-in-the-loop email responses. 
* **The Stack:** Zapier, Google Forms, Google Gemini, Gmail/Outlook APIs.
* **Key Innovation:** Implements strict behavioral guardrails using split-instruction prompt architecture. By separating system instructions from payload variables, the pipeline avoids AI hallucinations and threads formatted HTML drafts directly into live customer conversations for agent review.

---

## 🛠️ Core Competencies Demonstrated

This portfolio demonstrates a practical understanding of production-grade operational workflows:

* **Data Engineering Mindset:** Mapping custom schemas, handling dynamic payloads, and utilizing distinct tracking markers like `Thread IDs` to maintain continuity across asynchronous webhooks.
* **Prompt Engineering Architecture:** Utilizing system-level instructions, few-shot conditioning, and explicit formatting constraints to ensure AI outputs match strict corporate guidelines.
* **Low-Code / Code Hybridization:** Knowing exactly when to use native platform triggers and when to drop into custom Python or JavaScript environments to execute advanced data transformations.
* **Risk Mitigation:** Building safety-first architectures that preserve brand reputation by keeping human reviews integrated directly into automated loops.

---

> ### How to Navigate This Repo
> Click into any of the folder links above to see a deep dive into the business metrics, full visual architecture diagrams, and the actual raw prompt text or code blocks used to power the systems.