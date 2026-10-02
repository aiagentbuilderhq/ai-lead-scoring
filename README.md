# Project 5: AI Lead Scoring System — Apollo + Hunter + Gemini + n8n + MCP + APIs

> **One-liner:** Leads sourced via Apollo/Hunter APIs, scored 1-10 by Gemini against Ideal Client Profile, daily digest of 8+ only. Review time: 5 hrs/week → 15 min/day. Built with Make.com + n8n + MCP + Multiple APIs.

[![Apollo.io API](https://img.shields.io/badge/Apollo.io%20API-Lead%20Sourcing-blue)](https://apollo.io)
[![Hunter.io API](https://img.shields.io/badge/Hunter.io%20API-Email%20Verification-orange)](https://hunter.io)
[![Gemini](https://img.shields.io/badge/Gemini%201.5%20Flash-AI%20Scoring-blue)](https://aistudio.google.com)
[![n8n](https://img.shields.io/badge/n8n-Workflow-red)](https://n8n.io)
[![MCP](https://img.shields.io/badge/MCP-Model%20Context%20Protocol-purple)](https://modelcontextprotocol.io)
[![APIs](https://img.shields.io/badge/APIs-REST%20%2F%20JSON-green)](https://en.wikipedia.org/wiki/REST)

**Live Hub:** [automation-portfolio](https://github.com/aiagentbuilderhq/automation-portfolio) | **Other Projects:** [Sheets → Gmail](https://github.com/aiagentbuilderhq/sheets-gmail-automation) · [Weather Bot](https://github.com/aiagentbuilderhq/weather-telegram-bot) · [Form → Slack](https://github.com/aiagentbuilderhq/form-slack-leads) · [AI Inbox](https://github.com/aiagentbuilderhq/ai-inbox-assistant)

## 🎯 Problem
Founders spend 5+ hours weekly researching leads and guessing which ones are worth contacting. Manual review is slow, subjective, inconsistent. High-fit leads buried among low-fit. Apollo and Hunter have APIs — but most founders don't connect them to AI scoring.

## ✅ Solution — 3-Part System + MCP Pattern (Make.com + n8n)

**Part 1: Sourcing — Apollo API + Hunter API + Webhooks**
- Apollo.io API Free: Search "US e-commerce, 1-50 employees" → Export 15 leads via API
- Hunter.io API Free: Verify 10 emails (25 searches/month) via API
- Google Sheet `Lead Inbox` via Sheets API: Name, Company, Role, Website, Email, Notes, Score, Reason

**Part 2: AI Scoring — Gemini API + Groq + MCP**
- Make.com/n8n: Watch New Rows (Sheets API + Webhook) → Gemini Prompt via API: "You are a lead qualifier. I sell automation to US e-commerce brands under 50 staff, founder-led. Score this lead 1-10. Name: {{Name}} — Company: {{Company}} — Website: {{Website}} — Notes: {{Notes}} — Output ONLY: SCORE: X/10 | REASON: 1 line" — MCP pattern: Model (Gemini) + Context (Lead data from Sheets) + Protocol (Update Sheet)
- Sheets API: Update Row → Write Score + Reason — Groq fallback if Gemini quota hit

**Part 3: Daily Digest — Scheduling + Gmail API**
- Schedule Trigger (Cron): Every day 7:30 AM → Search Rows via Sheets API where Score ≥8 → Gmail API: Send Email "🎯 Daily digest: {{count}} high-fit leads" + list names/companies + reasons

**n8n Version:**
```
[Schedule Trigger: Daily 7:30 AM] → [Google Sheets Node: Search Rows Score≥8] → [Gmail Node: Send Digest] + [Slack Node: Post Digest to #sales]
[Sheets Trigger: New Lead] → [AI Agent Node: Gemini + MCP] → [Sheets Node: Update Score]
```

**Why MCP + Multiple APIs?** Founders searching "Apollo API", "Hunter API", "lead enrichment", "MCP", "AI scoring" want someone who connects multiple APIs + AI. I do Apollo + Hunter + Sheets + Gmail + Gemini in one workflow — that's API orchestration, high-value skill.

## 🏗️ Architecture

```
[Google Sheets: Lead Inbox — Sheets API — 25 Leads from Apollo API + Hunter API]
        ↓
[Make.com/n8n: Watch New Rows — Webhook + Sheets API]
        ↓
[Gemini: Score 1-10 Against ICP — Gemini API + Groq Fallback — MCP Pattern]
Prompt: "Score this lead 1-10 against: US e-commerce <50 staff, founder-led. Output SCORE: X/10 | REASON: 1 line"
        ↓
[Google Sheets: Update Row — Sheets API — Score + Reason]
        ↓
[Schedule: Daily 7:30 AM — Cron]
        ↓
[Google Sheets: Search Rows Score≥8 — Sheets API]
        ↓
[Gmail: Daily Digest Email — Gmail API + Slack API Optional]
Subject: 🎯 Daily digest: 6 high-fit leads
Body: List of 8+/10 leads with reasons
```

## 📈 Results

- **Before:** 5 hrs/week manual research + subjective guessing
- **After:** 15 min/day reviewing only 8+/10 leads
- **Quality:** AI scoring consistent, explains reasoning (REASON column) — MCP + RAG-lite pattern
- **Time Saved:** 4.5 hrs/week + higher conversion (focus on best leads)
- **Build Time:** 3 days (Day 15 sourcing, Day 16 scoring+digest, Day 17 case study)
- **APIs Connected:** 5 APIs in one workflow — Apollo, Hunter, Sheets, Gmail, Gemini — that's API orchestration, what founders pay premium for

## 🛠️ Tools Used — High-Value, Founder-Searched Skills

- **APIs:** Apollo.io API · Hunter.io API · Google Sheets API · Gmail API · Gemini API · Groq API · Slack API · Webhooks · REST / JSON · Email Verification · Lead Enrichment
- **Automation:** Make.com (Free) · n8n (Free self-host + cloud) · Scheduling / Cron · Error Handling · Router · Data Store
- **AI & Advanced:** MCP (Model Context Protocol) · LangChain pattern (Retrieve → Score → Digest) · Prompt Engineering · Confidence Scoring · AI Fallback (Gemini → Groq) · RAG-lite
- **Patterns:** API Orchestration (5 APIs in one flow), Lead Enrichment Pipeline, Daily Digest Automation, Human-in-the-loop (human reviews 8+ leads)
- **Why Both Make.com + n8n?** Client uses n8n? I build in n8n. Make.com? I build there. No new tool. Plus MCP + API orchestration is what advanced founders search for — "Apollo API automation", "lead scoring AI", "MCP agent".

## 🎥 Demo Video

**YouTube Unlisted:** `[Paste Link]`
Demo: Show Lead Inbox sheet with 25 leads (from Apollo/Hunter APIs) → Show Make.com/n8n scoring scenario run → Show Score + Reason columns populating → Show digest scenario → Show Gmail digest email with 8+ leads only → Show n8n version

## 💼 Client Pitch — Sounds Premium

> "You don't need more leads — you need to know which leads are worth your time. This system connects Apollo + Hunter APIs → Scores every lead 1-10 against your ICP via Gemini + MCP → Sends you only 8+ leads every morning via Gmail + Slack. Manual review: 5 hrs/week → 15 min/day. It's API orchestration — 5 APIs in one workflow — plus AI scoring with reasoning. That's what teams searching for 'Apollo API', 'lead enrichment', and 'MCP' want. Built on both Make.com and n8n, so I work in your stack."

## 🔒 Security

- No Apollo/Hunter/Gemini API keys in repo, fake/demo leads only, real client ICP redacted

---
**Built by Isaac — aiagentbuilderhq | [Full Portfolio Hub](https://github.com/aiagentbuilderhq/automation-portfolio) | Tech: Make.com + n8n + Apollo API + Hunter API + Sheets API + Gmail API + Gemini API + Groq + MCP + Webhooks + Lead Enrichment**
