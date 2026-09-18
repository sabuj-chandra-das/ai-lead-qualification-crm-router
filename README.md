# AI Lead Qualification & CRM Router

An AI-powered lead qualification and CRM routing workflow built with **n8n, OpenAI, HubSpot, Google Sheets, and Gmail**.

The system captures incoming leads through an n8n form, validates and normalizes the submitted information, uses AI to evaluate the lead against an Ideal Customer Profile (ICP), calculates a lead score and tier, maps key pain points, updates the CRM, routes the lead based on qualification, logs the result, and sends the appropriate sales notification.

---

## 🎯 Project Overview

Manual lead qualification can require sales teams to review large amounts of information before deciding how a lead should be handled.

This automation creates a structured qualification pipeline that processes each submitted lead automatically.

### Core Workflow

**Lead Form → Validation → AI Qualification → Lead Scoring → Pain Point Mapping → CRM Update → Lead Routing → Sales Notification → Audit Log**

The workflow demonstrates how AI can be combined with traditional automation, APIs, CRM systems, structured data processing, and conditional routing.

---

## ⚙️ What the Automation Does

The workflow performs the following operations:

1. Captures lead information through an n8n form.
2. Validates required fields and email format.
3. Normalizes the lead data into a consistent structure.
4. Sends the lead information to an OpenAI model for qualification.
5. Evaluates the lead against defined ICP criteria.
6. Determines buying intent, budget level, authority level, need level, and timeline.
7. Extracts key pain points.
8. Generates a recommended solution and qualification summary.
9. Calculates a lead score.
10. Assigns a lead tier: HOT, WARM, or COLD.
11. Maps AI-generated pain points into standardized categories.
12. Creates or updates the lead as a HubSpot contact.
13. Determines the appropriate routing path.
14. Routes leads based on tier and industry.
15. Sends email notifications to the appropriate sales or nurture team.
16. Records qualification results in Google Sheets for auditing and tracking.

---

## 🧠 AI Lead Qualification

The AI qualification stage analyzes submitted lead information using a defined Ideal Customer Profile.

The qualification process considers factors such as:

- Company size
- Decision-making authority
- Budget
- AI or automation requirements
- Business problem clarity
- Implementation timeline
- Buying intent
- Pain points

The AI qualification prompt is designed not to invent information. When a qualification factor cannot be determined from the submitted information, the workflow can return **Unknown**.

---

## 📊 Lead Scoring

The workflow calculates a score out of 100 using several qualification factors.

### Scoring Factors

| Factor | Maximum Points |
|---|---:|
| ICP Fit | 20 |
| Decision-making Authority | 15 |
| Budget | 20 |
| Business Need | 20 |
| Timeline | 15 |
| Problem Clarity / Pain Points | 10 |
| **Total** | **100** |

### Lead Tiers

The resulting score is used to classify the lead:

- **HOT** — Score 80+
- **WARM** — Score 50–79
- **COLD** — Score below 50

---

## 🛣️ Intelligent Lead Routing

After qualification, the workflow determines a routing value based on the lead tier and industry.

Examples of routing paths include:

- HOT SaaS → SaaS Sales Team
- HOT E-commerce → E-commerce Sales Team
- HOT Professional Services → General Sales
- Other HOT leads → General Sales
- WARM → Nurture
- COLD → Marketing/Nurture

This allows qualified leads to be automatically directed toward the appropriate follow-up process.

---

## 🔗 CRM Integration

The workflow integrates with **HubSpot** to create or update contact records.

The workflow can store qualification information alongside the lead, including:

- Lead score
- Lead tier
- ICP fit
- Buying intent
- Budget level
- Authority level
- Need level
- Timeline
- Pain points
- Qualification summary

This creates a structured CRM record that can be used by sales teams for follow-up and lead segmentation.

---

## 📧 Automated Notifications

The workflow sends email notifications based on the routing decision.

Different notification paths are available for:

- SaaS Sales
- E-commerce Sales
- General Sales
- Nurture
- Marketing/Nurture

The notification includes relevant lead information and the AI qualification results.

---

## 📋 Audit Logging

Qualification results are also recorded in Google Sheets.

The audit log can contain:

- Processing timestamp
- Lead name
- Email
- Company
- Industry
- Lead score
- Lead tier
- Buying intent
- ICP fit
- Budget level
- Authority level
- Need level
- Timeline
- Pain points
- Qualification summary
- Routing result

This provides a historical record of processed leads for tracking and auditing.

---

## 🏗️ Workflow Architecture

    ┌──────────────────────┐
    │    n8n Lead Form     │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │ Validate & Normalize │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │   AI Qualification   │
    │       OpenAI         │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │ Merge Lead + Result  │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │ Calculate Lead Score │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │  Map Pain Points     │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │   Update HubSpot     │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │   Determine Route    │
    └──────────┬───────────┘
               │
          ┌────┴────┐
          │         │
          ▼         ▼
    ┌──────────┐  ┌──────────────┐
    │Route Lead│  │Google Sheets │
    │by Tier & │  │  Audit Log   │
    │Industry  │  └──────────────┘
    └────┬─────┘
         │
    ┌────┼─────────────┐
    │    │             │
    ▼    ▼             ▼
  Sales Nurture     Marketing
  Email  Email       Email

---

## 🔧 Technologies Used

| Technology | Purpose |
|---|---|
| **n8n** | Workflow orchestration and automation |
| **OpenAI** | AI-powered lead qualification |
| **HubSpot** | CRM contact creation/update |
| **Google Sheets** | Audit logging and tracking |
| **Gmail** | Automated sales/nurture notifications |
| **JavaScript** | Data validation, scoring, transformation, and routing |

---

## 📸 Workflow Screenshot

![AI Lead Qualification & CRM Router](screenshots/01-lead-qualification-crm-router.png)

---

## 📂 Repository Structure

    ai-lead-qualification-crm-router/
    │
    ├── workflows/
    │   └── lead-qualification-crm-router.json
    │
    ├── screenshots/
    │   └── 01-lead-qualification-crm-router.png
    │
    └── README.md

---

## 🚀 Setup Overview

To recreate the workflow:

1. Install or access an n8n instance.
2. Import the workflow JSON from the `workflows` directory.
3. Create your own OpenAI credential.
4. Create your own HubSpot credential/token.
5. Create your own Google Sheets credential.
6. Create your own Gmail credential.
7. Configure the Google Sheets audit-log destination.
8. Configure the notification email addresses.
9. Review the AI qualification prompt and ICP criteria.
10. Test the workflow with sample lead data.
11. Verify HubSpot updates.
12. Verify Google Sheets logging.
13. Verify the appropriate email notification is triggered.

---

## 🔐 Security

The workflow JSON included in this repository is **sanitized for public sharing**.

API keys, private tokens, credential IDs, private email addresses, and other sensitive identifiers should not be committed to the repository.

Before using the workflow, configure your own:

- OpenAI credentials
- HubSpot credentials
- Google Sheets credentials
- Gmail credentials
- Google Sheets document
- Notification email addresses

**Never publish real API keys, private access tokens, or credentials in workflow exports.**

---

## 💡 Automation Concepts Demonstrated

This project demonstrates practical AI automation concepts including:

- AI-assisted lead qualification
- Structured LLM output
- CRM automation
- Lead scoring
- Rule-based routing
- Industry-based routing
- Data validation
- Data normalization
- JavaScript transformation
- Pain-point classification
- API integration
- Automated email notifications
- Audit logging
- Multi-branch workflow design
- Human sales-team handoff

---

## 🔄 End-to-End Process

### 1. Lead Submission

A prospect submits information through the n8n lead qualification form.

### 2. Validation

The workflow checks required fields and validates the email format.

### 3. AI Analysis

OpenAI analyzes the submitted lead against the defined ICP.

### 4. Qualification

The system determines:

- ICP fit
- Buying intent
- Budget level
- Authority level
- Need level
- Timeline
- Pain points
- Recommended solution
- Qualification summary

### 5. Lead Scoring

The workflow calculates a score from 0–100.

### 6. Pain Point Mapping

AI-generated pain points are mapped into standardized business categories.

### 7. CRM Update

The lead is created or updated in HubSpot.

### 8. Routing

The workflow determines the appropriate sales or nurture route based on qualification results.

### 9. Notification

The appropriate team receives an automated email containing the lead and qualification details.

### 10. Audit Log

The processed lead and qualification results are recorded in Google Sheets.

---

## 📌 Project Highlights

- End-to-end AI lead qualification pipeline
- Structured AI output using an n8n output parser
- Automated lead scoring system
- CRM integration with HubSpot
- Industry and lead-tier based routing
- Automated sales notifications
- Google Sheets audit trail
- JavaScript-based data transformation
- API-driven workflow architecture
- Multi-branch workflow automation
- Designed for practical sales automation use cases

---

## 📚 Learning Outcomes

This project demonstrates experience with:

- Designing production-style n8n workflows
- Integrating AI models into business processes
- Working with structured LLM responses
- Connecting external APIs
- Designing CRM automation
- Building conditional routing logic
- Processing and transforming JSON data
- Creating automated notification systems
- Maintaining audit logs
- Handling sensitive credentials safely

---

## 👤 Author

**Sabuj Chandra Das**

AI Automation Engineer

---

## 📄 Project Status

**Completed — Portfolio Project**

The workflow is provided as a sanitized example for demonstration and learning purposes.
