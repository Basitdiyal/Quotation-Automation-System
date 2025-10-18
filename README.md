# 🚛 Quotation Automation System for Logistics Companies

An AI-powered automation system that streamlines the **freight quotation process** for logistics companies — from WhatsApp inquiry to professional email quotation — without any manual effort.

![Automation](https://img.shields.io/badge/Automation-AI%20%26%20n8n-blue)
![Status](https://img.shields.io/badge/Status-Working-brightgreen)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 🌟 Overview

This project was built as a practical implementation of automation concepts learned under the guidance of **Sir Zafar Iqbal**.  
The goal was to create a fully automated workflow that eliminates repetitive quotation tasks, reduces human dependency, and improves customer response time.

> 💡 Idea inspired by a real-world Upwork project — implemented for learning, practice, and real business value.

---

## ⚙️ How It Works

1. **WhatsApp Inquiry**  
   Customer sends a freight inquiry via WhatsApp.

2. **Dynamic Conversation Flow**  
   The system asks required shipment details step by step (origin, destination, cargo type, weight, etc.).

3. **Rate Checking**  
   System automatically checks rates from a **Vector Store** (pre-stored database of logistic rates).

4. **Quotation Generation**  
   Once details are complete, an **AI model (LLM)** prepares a professional quotation.

5. **WhatsApp Auto Reply**  
   The quotation is instantly shared back with the customer via WhatsApp.

6. **Email Confirmation**  
   Upon customer confirmation, a professionally formatted quotation is emailed to the client.

7. **Google Sheets Logging**  
   All inquiries and quotations are automatically logged in Google Sheets for tracking and analytics.

---

## 🧩 Tech Stack

| Component | Description |
|------------|--------------|
| **n8n** | Automation workflow orchestration |
| **OpenAI / GPT** | Natural language understanding and quotation generation |
| **Twilio / WhatsApp Cloud API** | WhatsApp communication |
| **Google Sheets API** | Logging and record-keeping |
| **Vector Store (e.g., Supabase / Pinecone)** | Freight rate lookup |
| **Gmail API / SMTP** | Sending professional email quotations |

---

## 🧠 Workflow Diagram

```mermaid
sequenceDiagram
    participant C as Customer (WhatsApp)
    participant W as WhatsApp API
    participant N as n8n Workflow
    participant V as Vector Store
    participant G as Google Sheets
    participant E as Email Service

    C->>W: Sends Freight Inquiry
    W->>N: Trigger n8n Workflow
    N->>C: Requests Shipment Details
    C->>N: Provides Required Info
    N->>V: Fetch Rates from Vector Store
    V-->>N: Return Best Match Rate
    N->>C: Share Auto Quotation via WhatsApp
    C->>N: Confirms Quotation
    N->>E: Send Final Quotation Email
    N->>G: Log Quotation in Google Sheets
