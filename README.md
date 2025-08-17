# ai-instagram-chatbot
### 🤖 AI Instagram Chatbot with ManyChat + Make + OpenAI  
### This project demonstrates how to build an Instagram chatbot that uses ManyChat, Make.com, and OpenAI to automatically respond to user messages. 
---
Preparation
---

- ManyChat : Chatbot platform focused on IG / FB / WhatsApp, etc. Work as a bridge between Instagram and Make.com
  - [ ] Pay for API, under 500 followers $15/month
- Make.com : Automation workflow design platform. Other options as Zapier or n8n
- OpenAI developer platform : 
  - [ ] Pay for tokens and API, Minimum $5/time
- Instagram business account
  - [ ] Must be linked to its Facebook fan page because Instagram messenger function is built within Facebook. If you do not have a Facebook fan page, create one.
- Google Sheet : To enable RAG (Retrieval-Augmented Generation)
   - [ ] In this project, all data is stored in a cell in sheet 1 using `textjoin` function.
   - [ ] Data is maintained/updated in sheet 2.
   - [ ] The first row of dataset can only be title and can't be retrievd as data when sending to manychat/make.com.
---
Flowchart
---
<img width="913" height="306" alt="manychat" src="https://github.com/user-attachments/assets/1ed75a55-a357-4321-b38b-c306db109060" />
<img width="956" height="225" alt="截圖 2025-08-17 20 54 17" src="https://github.com/user-attachments/assets/4d38d7d3-0165-4abd-93c0-e152ddfb6b0f" />

---
Feature Discription
---
- User sends a message on Instagram
- ManyChat triggers a webhook to Make.com
- Make.com sends the message to OpenAI GPT-4 API
- OpenAI returns a response
- Make.com updates the user's Custom Field. In this case, {{ai_reply}} in ManyChat
- ManyChat sends the response back to the user from Instagram message inbox
