🔐Step 1: Prepare OpenAI API


Go to [OpenAI](https://platform.openai.com/)

Generate an API key and keep it. (You can save it in a .env file (do not commit this file to GitHub))

❗ Make sure to go to Billing and pay at least $5 before using your API key

---

🧠 Step 2: Setup ManyChat

0. Create a Custom Field
> In ManyChat > Settings > Custom Fields:
> Add a new Text field named: `ai_reply`

❗ Do NOT create a field called `field_name` or `field_value`.
These are JSON parameter keys, not variables in ManyChat.

1. Add a trigger →  **User sends a direct message** or **User sends a message** , depending on what criteria you want to trigger a workflow
2. Make an external request to make.com

3. Smart delay 
> ManyChat will not wait for Make.com runs all modules til complete, it will execute along the workflow itself → if we don't add 「Delay」process, it is likely to send out a blank due to make.com has not yet updated a value to `ai_reply`. Delay second is subject to the minimum requirement. Now is 10 sec.

4. Instagram →  send message
> `ai_reply`

---
🔄 Step 3: Build Make Scenario

❗Be sure to finish your account connection with facebook/google sheet/OpenAI

Module 1 – Webhooks [Trigger]
Type: Webhooks → Custom Webhook

> Set user_id and last_input_text as incoming JSON keys from ManyChat

Module2 - Google Sheet→ get a cell

> Use **text aggregator** or **TextJoin** function to save all reference data into a cell in a sheet. 

Module3 - OpenAI(ChatGPT)→  create a completion(prompt)

> Below is a prompt example. 
```
[
  { "role": "system", "content": "You are a helpful customer support agent." },
  { "role": "user", "content": " Before replying, you need to read this content. {{2.value}} After reading above, please answer the question in Module1 {{1.last_input_text}}" }
]
```
Module4 - Http → make a request

> This module is to make a request to manychat, writing AI result into a Custom Field `ai_reply`
> For your external integration (OpenAI via Make → ManyChat → Instagram), a Pro license of ManyChat is required, because the “return trip” uses ManyChat’s API.
```
{
  "subscriber_id": "{{1.user_id}}",
  "field_name": "ai_reply", 
  "field_value": "{{3.result}}"
}
```
Module5 - Webhooks → webhook resposne

> This module is optional.
> In your AI chatbot setup, ManyChat is the caller.
> Make grabs the incoming message, sends it to OpenAI, then writes the answer back into ManyChat via the HTTP → ManyChat API.
> The Webhook Response is optional if you’re already handling the return trip via ManyChat’s API.
But if ManyChat expects a confirmation from its webhook trigger, you use this module to send back something lightweight like:
```
{
  "status": "success",
  "note": "Message received by Make"
}

```
Here is the value you need to fill in into this module
```
{
  "messages": [
    {
      "text": "{{3.result}}"
    }
  ]
}
```

---
to be continued...

