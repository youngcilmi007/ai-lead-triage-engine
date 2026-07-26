# Database Schemas & Field Mapping Guide

This document defines the exact data structure used to sync raw form inputs, AI enrichment outputs, and actionable CRM records across Google Sheets and Notion.

---

## 📊 1. Google Sheets Master Log Schema
The Google Sheet acts as the immutable historical record for every inbound submission, ensuring zero data loss before conditional routing occurs.

| Column Letter | Column Header | Data Type | Source / Description |
| :--- | :--- | :--- | :--- |
| **A** | `Timestamp` | DateTime | Automatic Zapier capture time |
| **B** | `Lead Name` | Text | Form Submission (`Full Name`) |
| **C** | `Email` | Text | Form Submission (`Email`) |
| **D** | `Company` | Text | Form Submission (`Company Name`) |
| **E** | `Budget` | Text | Form Submission (`Stated Budget`) |
| **F** | `AI Temperature` | Select | JSON Output (`lead_temperature`: Hot/Warm/Cold) |
| **G** | `Company Tier` | Select | JSON Output (`estimated_company_tier`: Enterprise/SMB) |
| **H** | `Outreach Icebreaker` | Text | AI Generated 1-sentence opening line |
| **I** | `Status` | Status | Default: `Logged` / `Synced` |

---

## 🗂️ 2. Notion CRM Database Properties
The Notion workspace acts as the dynamic, actionable board for the sales team, filtered explicitly for high-priority opportunities.

* **Name (Title):** Lead Name + Company (e.g., *Jane Doe - Acme Corp*)
* **Email (Email):** Prospect contact email
* **Lead Temperature (Select):** 
  * 🔴 `Hot` (Triggers immediate notification & high priority)
  * 🟡 `Warm` (Added to nurturing sequence)
  * 🔵 `Cold` (Archived)
* **Company Tier (Select):** `Enterprise` | `Mid-Market` | `SMB`
* **Outreach Icebreaker (Text / Code Block):** The AI-generated opening line ready for the sales rep to copy-paste.
* **Follow-up Status (Status):** `Not Started` | `In Progress` | `Contacted`
