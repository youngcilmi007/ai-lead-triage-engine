# ai-lead-triage-engine
An end-to-end AI automation portfolio project featuring Zapier, OpenAI/Gemini, Google Sheets, and Notion integrations.
# AI-Powered Lead Triage & Enrichment Engine

An enterprise-grade, end-to-end AI automation workflow built using **Zapier**, **OpenAI/Gemini**, **Google Sheets**, and **Notion**. This project automates the entire inbound lead lifecycle—from raw form submission to AI-driven enrichment, sentiment scoring, logging, and CRM routing.

---

## 🎯 The Business Problem
Sales teams often waste valuable hours manually qualifying inbound leads, searching company backgrounds, and organizing data across disjointed spreadsheets. This creates delayed response times and lost deals.

## 💡 The Automated Solution
This workflow creates an autonomous triage loop:
1. **Intake:** Captures new form submissions instantly via webhook or trigger.
2. **AI Processing:** Analyzes intent, categorizes lead temperature, estimates company tier, and generates a personalized outreach icebreaker.
3. **Master Logging:** Safely logs all raw payload data into a structured Google Sheet for analytics.
4. **CRM Action:** Automatically creates a high-priority entry inside a custom Notion CRM dashboard if the lead qualifies as "Hot".

---

## 🧱 Workflow Architecture

```text
[Lead Form/Weai-lead-triage-engine Zapier Pipeline
Trigger Step: GitHub — New Commit or New Push

Repository: youngcilmi007/ai-lead-triage-engine

Branch: main

Action Step: Google Sheets — Create Spreadsheet Row

Spreadsheet: fc lion (or your Lead Automation Log)

Row Mappings:

Commit Reference: Map to GitHub Commit ID / Hash

Lead / Component Title: Map to Commit Message

Triage Status: Set to Processed or Synced

Generation Date: Map to Zapier Execution Timestamp ({{zap_meta_human_now}})

GitHub Asset URL: Map to Commit URLbhook] ➔ [Zapier Core Logic] ➔ [AI Enrichment Agent] 
                                                        │
         ┌──────────────────────────────────────────────┘
         ▼
[Google Sheets Master Log] ──► [Notion CRM (Conditional Hot Lead Routing)]
