# Zapier Agent Core Instructions

Paste the text block below directly into the main instructions panel of your Zapier Agent editor. This acts as the runtime logic for the AI.

```text
Trigger: When you add a notebook reaction (📓 emoji) to a message in Slack.

1. Capture the Slack message that was reacted to, including the full thread of replies using the Slack: Retrieve Thread Messages tool associated with that specific message.
2. Compile all messages in the thread into a single block of text, preserving the chronological order of the conversation.
3. Send the compiled thread text to the AI core engine with the following exact prompt instructions: 
   "Please summarize the key information and any action items from the following Slack thread conversation. Format the response cleanly with two distinct sections: 'Key Information' and 'Action Items'."
4. Retrieve the AI-generated summary response.
5. Send an email to your verified personal email address using the Gmail tool configured with:
   - To: [Your Hardcoded Email Address]
   - Subject: "Slack Thread Summary: [first few words of the original message or channel name]"
   - Body: Injected AI-generated summary including the structured 'Key Information' and 'Action Items' sections.

Expected Outcome:
Whenever you react to any Slack message with the notebook emoji, you will receive an email containing a neatly formatted summary of the entire thread, highlighting the most important information and any action items you need to be aware of.