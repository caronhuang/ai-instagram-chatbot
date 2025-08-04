🔐Step 1: Prepare OpenAI API


Go to [OpenAI](https://platform.openai.com/)

Generate an API key and keep it. (You can save it in a .env file (do not commit this file to GitHub))

❗ Make sure to go to Billing and pay at least $5 before using your API key

---

🧠 Step 2: Setup ManyChat

Create a Custom Field
In ManyChat > Settings > Custom Fields:

Add a new Text field named: `ai_reply`

❗ Do NOT create a field called `field_name` or `field_value`.
These are JSON parameter keys, not variables in ManyChat.

---
🔄 Step 3: Build Make Scenario

Module 1 – Webhooks [Trigger]
Type: Webhooks → Custom Webhook

Set user_id and last_input_text as incoming JSON keys from ManyChat

---
to be continued...

