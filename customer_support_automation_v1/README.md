# AI-Powered Customer Support Routing & Intelligent Drafting Engine

## Business Problem Statement
Customer support teams face a continuous operational bottleneck handling repetitive inquiries, such as account cancellations, data deletions, and basic informational requests. Relying entirely on manual drafting slows down initial response times and degrades the customer experience. However, putting generative AI on total autopilot to reply directly to customers introduces severe risks of factual "hallucinations," broken URLs, or improper brand tone. 

This project solves these inefficiencies by deploying a safety-first automation pipeline. By linking structured data collection, instantaneous automated engagement, and a split-instruction generative AI layer, this workflow cuts draft writing time by roughly 90% while keeping a human support agent in the loop to review and approve responses before they reach the customer.

## System Architecture & Data Flow
The pipeline utilizes a multi-step automation architecture built in Zapier to manage data intake, enforce context boundaries, and dynamically thread email drafts.

* **Trigger (Google Forms):** Captures customer input using a clean schema (First Name, Email, Category, and Message). This ensures the intake data is structured properly before passing it down the pipeline.
* **Immediate Acknowledgment Layer (Gmail/Outlook API):** Instantly fires a friendly, HTML-formatted acknowledgment email back to the customer. This confirms receipt, copies their original query back to them for compliance, and generates a unique email `Thread ID`.
* **AI Processing Layer (Google Gemini):** Passes the customer's query to Gemini. To maximize reliability, the architecture segregates the instruction set into **System Instructions** (hardcoded guardrails preventing hallucinations) and the **Prompt payload** (the company rules, routing documentation, and customer variables). 
* **Dynamic Deployment Layer (Gmail/Outlook API - Create Draft Reply):** Instead of emailing the customer directly, the pipeline uses the `Create Draft Reply` event. By mapping the dynamic `Thread ID` extracted from the acknowledgment step, Zapier injects Gemini's formatted HTML output directly into the existing customer email chain as a pending draft.

---

## Technical Specifications & Field Mapping

| Zapier Step | App Component | Action/Event | Core Mapping Logic |
| :--- | :--- | :--- | :--- |
| **Step 1** | Google Forms | New Form Response | Captures customer variables: `{{First Name}}`, `{{Email}}`, `{{Message}}` |
| **Step 2** | Gmail / Outlook | Send Email | Generates initial acknowledgment. Outputs critical `{{Thread ID}}` |
| **Step 3** | Google Gemini | Generate Content | Evaluates message text against strict FAQ rules; outputs clean email HTML |
| **Step 4** | Gmail / Outlook | Create Draft Reply | Anchors to `{{Thread ID}}` from Step 2. Maps `{{Candidates Content Parts Text}}` from Step 3 into the HTML body |

---

## Prompt Engineering Architecture

To guarantee absolute compliance and prevent the AI from generating rogue information, the Gemini step is explicitly broken down into structural roles:

### 1. System Instructions (Behavioral Guardrails)
```text
You are a strict, polite customer support assistant for Prompt Genie. 
Your core directive is to answer customer queries using ONLY the facts provided to you. 

CRITICAL RULES:
1. DO NOT make up information. If an answer cannot be verified by your instructions, default to a fallback message.
2. Output your response using clean HTML formatting suitable for an email body (use <br> for breaks, <a> tags for links). 
3. Never output raw URLs. Always use descriptive anchor text for hyperlinks (e.g., <a href="URL">Click here to manage your account</a>).
```

### 2. Context Prompt (Operational Logic & Inputs)
``` text
Analyze the following Customer Query and draft a reply based on these business rules:

- Rule A (Account Deletion): If they want to delete their account, provide this link: https://ssd.com/account-deletion
- Rule B (Cancel/Unsubscribe): If they want to cancel a free trial or unsubscribe, provide this link: https://www.ssd.com/my-account
- Rule C (Fallback): For any other topics (billing bugs, feature requests, complaints), politely inform them that a human support representative is reviewing their request and will email them shortly.

Customer Query:

Draft HTML Response:
```
