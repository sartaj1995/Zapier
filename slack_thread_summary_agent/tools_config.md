```markdown
# Tools Configuration Guide

Because Zapier Agent tool settings are managed through interactive dropdowns and options rather than code, use this guide to configure the required connected applications.

## 1. Slack (Retrieve Thread Messages)
After adding the Slack tool to your agent, click the gear icon to open its configurations and map the fields exactly like this:

* **Channel:** Select *Let your agent select a value for this field*. This grants the AI permission to dynamically detect what channel you are active in.
* **Thread Timestamp:** Select *Let your agent select a value for this field*. This allows the AI to grab the exact thread linked to your emoji trigger.

## 2. Gmail (Send Email)
After adding the Gmail tool, open its configuration window. This tool needs strict boundaries to prevent data leaks.

* **To:** Change the dropdown setting to *Set a specific value*. Type your personal email address directly into the field. Do not let the AI choose this value dynamically.
* **Subject:** Leave as *Let your agent select a value for this field*. The AI will create a context-aware subject line automatically.
* **Body Type:** Set to `Markdown` or `Plain`.
* **Body:** Leave as *Let your agent select a value for this field*. The AI will automatically inject the formatted summary here.