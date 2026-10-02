# Project 5: AI Lead Scoring System — Apollo + Hunter + Gemini + Daily Digest

> **One-liner:** Leads sourced via Apollo/Hunter, scored 1-10 by Gemini against Ideal Client Profile, daily digest of only 8+ leads. Review time: 5 hrs/week → 15 min/day.

[![Apollo](https://img.shields.io/badge/Apollo.io-Lead%20Sourcing-blue)](https://apollo.io)
[![Hunter](https://img.shields.io/badge/Hunter.io-Email%20Verification-orange)](https://hunter.io)
[![Gemini](https://img.shields.io/badge/Gemini%201.5%20Flash-AI%20Scoring-blue)](https://aistudio.google.com)
[![Make.com](https://img.shields.io/badge/Make.com-Automation-blue)](https://make.com)

## 🎯 Problem
Founders spend 5+ hours weekly researching leads and guessing which ones are worth contacting. Manual review is slow, subjective, inconsistent. High-fit leads get buried among low-fit.

## ✅ Solution — 3-Part System

**Part 1: Sourcing (Day 15)**
- Apollo.io Free: Search "US e-commerce, 1-50 employees" → Export 15 leads
- Hunter.io Free: Verify 10 emails (25 searches/month free)
- Google Sheet `Lead Inbox`: Name, Company, Role, Website, Email, Notes

**Part 2: AI Scoring (Day 16)**
- Make.com: Watch New Rows → Gemini Prompt: "You are a lead qualifier. I sell automation to US e-commerce brands under 50 staff, founder-led. Score this lead 1-10. Name: {{Name}} — Company: {{Company}} — Website: {{Website}} — Notes: {{Notes}} — Output ONLY: SCORE: X/10 | REASON: 1 line"
- Sheets: Update Row → Write Score + Reason

**Part 3: Daily Digest (Day 16)**
- Make.com Schedule: Every day 7:30 AM → Search Rows where Score ≥8 → Gmail: Send Email "🎯 Daily digest: {{count}} high-fit leads" + list names/companies

## 🏗️ Architecture

```
[Google Sheets: Lead Inbox - 25 Leads]
        ↓
[Make.com: Watch New Rows]
        ↓
[Gemini: Score 1-10 Against ICP]
Prompt: "Score this lead 1-10 against: US e-commerce <50 staff, founder-led. Output SCORE: X/10 | REASON: 1 line"
        ↓
[Google Sheets: Update Row - Score + Reason]
        ↓
[Schedule: Daily 7:30 AM]
        ↓
[Google Sheets: Search Rows Score≥8]
        ↓
[Gmail: Daily Digest Email]
Subject: 🎯 Daily digest: 6 high-fit leads
Body: List of 8+/10 leads with reasons
```

## 📸 Screenshots (Add Yours)

- `lead-inbox.png` — Sheet with 25 leads (fake data)
- `scored-sheet.png` — Same sheet with Score + Reason columns filled by Gemini
- `scenario-scoring.png` — Make.com scoring scenario
- `scenario-digest.png` — Make.com daily digest scenario
- `digest-email.png` — Gmail digest showing 8+ leads

## 📈 Results

- **Before:** 5 hrs/week manual research + subjective guessing
- **After:** 15 min/day reviewing only 8+/10 leads
- **Quality:** AI scoring consistent, explains reasoning (REASON column)
- **Time Saved:** 4.5 hrs/week + higher conversion (focus on best leads)
- **Build Time:** 3 days (Day 15 sourcing, Day 16 scoring+digest, Day 17 case study)

## 🛠️ Tools Used

- Apollo.io Free (limited exports — enough for demo)
- Hunter.io Free (25 searches/month)
- Google Sheets (Lead Inbox + Score columns)
- Gemini 1.5 Flash via Google AI Studio (Free tier — 15 req/min)
- Make.com (Free tier — 1,000 ops/month)
- Gmail (Digest delivery)
- **Running Cost:** $0/month free tiers

## 🎥 Demo Video

**YouTube Unlisted Link:** `[Paste Link Here]`

**Demo Script (50 sec):**
- 0-5s: "Lead Scoring System — From 5 hrs/week to 15 min/day"
- 5-15s: Show Lead Inbox sheet with 25 leads
- 15-30s: Show Make.com scoring scenario run → Show Score + Reason columns populating
- 30-40s: Show digest scenario → Show Gmail digest email with 8+ leads only
- 40-50s: "AI removes boring 90%, human keeps judgment. Built with Apollo + Hunter + Gemini + Make.com"

## 🚀 How To Replicate

1. Apollo.io → Sign Up Free → Search: "US e-commerce, 1-50 employees, Founder" → Export 15 leads → Copy to Sheet
2. Hunter.io → Sign Up Free → Verify emails → Add verified to Sheet
3. Create Sheet `Lead Inbox` → Columns: Name, Company, Role, Website, Email, Notes, Score, Reason
4. Make.com → New Scenario → Sheets → Watch New Rows → Select Lead Inbox
5. Add Gemini → Generate Text → Model: gemini-1.5-flash → Prompt: template above → Map Name, Company, Website, Notes
6. Add Sheets → Update a Row → Find by Name → Write Score + Reason from Gemini output (parse SCORE: X/10)
7. Run Once → Should score all 25 leads → Screenshot
8. New Scenario → Schedule → Every day 7:30 AM → Sheets → Search Rows → Filter Score ≥8 → Gmail → Send Email → Digest template
9. Run Once → Check digest email arrives
10. Document + Loom

## 💼 Client Pitch

> "You don't need more leads — you need to know which leads are worth your time. This system scores every lead 1-10 against your ideal client profile and sends you only the 8+ leads every morning. Manual review: 5 hrs/week → 15 min/day. AI removes the boring 90%, you keep judgment on the best 10%."

## 🔒 Security

- No Apollo/Hunter/Gemini API keys in repo
- All leads are fake/demo data (Test Company, test@company.com) — never real scraped leads
- Real client ICP redacted if client work

## 📄 Case Study

See `case-study.md`

---
**Built by Isaac — aiagentbuilderhq | [Full Portfolio](https://github.com/aiagentbuilderhq/automation-portfolio) | Free Audit: [Calendar Link]**
