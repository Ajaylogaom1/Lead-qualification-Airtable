# Lead-qualification-Airtable
🤖 AI Lead Qualification & Approval Workflow (n8n)
📌 Overview

This project is an end-to-end AI-powered lead qualification system built using n8n, Airtable, Google Gemini AI, and Telegram.

It automatically:

Captures leads from a form

Checks for duplicates

Uses AI to analyze and qualify leads

Sends approval requests via Telegram

Updates records based on human approval or rejection

Notifies users via email and Telegram

This workflow is suitable for:

Marketing agencies

SaaS companies

Lead resellers

Sales teams

Automation freelancers

# 🧩 High-Level Workflow Architecture
Form Submission
   ↓
Duplicate Check (Airtable)
   ↓
AI Lead Qualification (Gemini)
   ↓
Approval Request (Telegram)
   ↓
Human Decision (Approve / Reject)
   ↓
Database Update + Notifications

# 🛠️ Tools & Services Used

n8n – Workflow automation engine

Airtable – Lead database (CRUD operations)

Google Gemini Chat Model – AI lead analysis

Telegram Bot API – Human approval interface

Gmail – Email notifications

# 📂 Workflow Breakdown (Node-by-Node)
# 1️⃣ Lead Intake & Validation
🔹 On Form Submission

Triggered when a user submits a form

Receives lead details (name, email, requirement, budget, timeline)

🔹 Edit Fields

Cleans and formats incoming data

Standardizes field names before processing

🔹 Search Records (Airtable)

Checks if the lead already exists using email or unique identifier

🔹 IF (Duplicate Check)

True → No operation (prevents duplicate entry)

False → Continues workflow for new lead creation

# 2️⃣ AI-Based Lead Qualification
🔹 Create Record (Airtable)

Stores the new lead with initial status

🔹 Google Gemini Chat Model

Analyzes lead quality using AI

Evaluates parameters like:

Budget

Urgency

Requirement clarity

🔹 Output Parser

Converts AI response into structured data

Extracts decision, confidence, and reasoning

🔹 Create Record (AI Output)

Saves AI decision results into Airtable

# 3️⃣ Decision Routing
🔹 Switch (Rules Mode)

Routes based on AI decision:

Approve

Reject

Follow-up Needed

# 🔹 Telegram – Approval Message

Sends approval request to admin with inline buttons

Includes lead details and AI confidence

🔹 Telegram – Message

Sends rejection or follow-up notification

# 4️⃣ Telegram Human Approval Flow
🔹 Telegram Trigger (Callback Query)

Listens for button clicks:

Approve

Reject

🔹 Switch (Callback Rules)

Identifies action from callback data

🔹 Edit Fields

Extracts record ID and decision

🔹 Get Record (Airtable)

Fetches the corresponding lead record

# 5️⃣ Final AI + Notification Layer
🔹 Message a Model

Generates a human-like response message

Used for client-facing communication

🔹 Send a Message (Gmail)

Sends final email notification to lead or internal team

🔹 IF (Final Validation)

Checks decision consistency

🔹 Update Record (Airtable)

Updates lead status:

Approved

Rejected

Closed

🔹 No Operation

Graceful exit for completed or invalid paths

# 🗂️ Airtable Schema (Recommended)
Field Name	Type
Full Name	Text
Email	Email
Requirement	Long Text
Budget	Number
Timeline	Single Select
Lead Status	Single Select
AI Decision	Single Select
AI Confidence	Number
Approval Status	Single Select
Telegram Action	Text
Created Time	Date
# 🔐 Environment Variables Required
AIRTABLE_API_KEY
AIRTABLE_BASE_ID
AIRTABLE_TABLE_NAME
GOOGLE_GEMINI_API_KEY
TELEGRAM_BOT_TOKEN
GMAIL_CREDENTIALS

# 🚀 Key Features

✅ Duplicate lead prevention

🤖 AI-based decision making

🧠 Human-in-the-loop approval

📲 Telegram inline approvals

📊 Centralized CRM-style database

📧 Automated email notifications

🔁 Fully scalable & reusable

# 💡 Use Cases

Lead qualification for agencies

AI-powered sales screening

Client onboarding automation

SaaS trial request filtering

Lead reselling workflows





✅ Prepare a client demo script

Just tell me what’s next 👍
