# ai-instagram-chatbot
### 🤖 AI Instagram Chatbot with ManyChat + Make + OpenAI  
### This project demonstrates how to build an Instagram chatbot that uses ManyChat, Make.com, and OpenAI to automatically respond to user messages. 
---
Preparation
---

- ManyChat :  (Paid service, $15/month)
- Make.com 
- OpenAI GPT-4 API (Paid service, Minimum $5/time)
- Instagram business account (Must be linked to its Facebook fan page due to Instagram messenger function is linked to Facebook)

---
Flowchart
---
<img width="913" height="306" alt="manychat" src="https://github.com/user-attachments/assets/1ed75a55-a357-4321-b38b-c306db109060" />
<img width="1084" height="341" alt="makecom" src="https://github.com/user-attachments/assets/752e206e-473c-4aff-9564-bc32c29486f1" />

---
Feature Discription
---
- User sends a message on Instagram
- ManyChat triggers a webhook to Make
- Make sends the message to OpenAI GPT-4 API
- OpenAI returns a response
- Make updates the user's Custom Field(in this case, {{ai_reply}}) in ManyChat
- ManyChat sends the response back to the user
