# Case Study: AI Lead Scoring System with Daily Digest

**Client Type:** Founder doing manual lead research 5+ hrs/week
**Timeline:** 3 days (sourcing → scoring → digest → case study)
**Tools:** Apollo.io Free, Hunter.io Free, Google Sheets, Gemini 1.5 Flash, Make.com, Gmail
**Cost to Run:** $0/month (free tiers)

### Problem
A founder spent 5+ hours weekly researching e-commerce brands, guessing which were worth contacting. No scoring system. High-fit leads buried among low-fit. Follow-up inconsistent. Time wasted on leads that would never buy.

**Impact:** 5 hrs/week lost + low conversion because best leads not prioritized.

### Solution
Built 3-part lead system:

**1. Sourcing (Free Tools):**
- Apollo.io Free: Search "US e-commerce, 1-50 employees, founder-led" → Export 15 leads
- Hunter.io Free: Verify emails (25 free searches/month)
- Sheet `Lead Inbox`: Name, Company, Role, Website, Email, Notes, Score, Reason

**2. AI Scoring (Gemini):**
- Make.com watches new rows
- Gemini prompt: "You are a lead qualifier. I sell automation to US e-commerce brands under 50 staff, founder-led. Score this lead 1-10. Name: {{Name}} — Company: {{Company}} — Website: {{Website}} — Notes: {{Notes}} — Output ONLY: SCORE: X/10 | REASON: 1 line"
- Score + Reason written back to Sheet

**3. Daily Digest:**
- Scheduled daily 7:30 AM
- Searches Sheet for Score ≥8
- Sends Gmail digest: "🎯 Daily digest: 6 high-fit leads" + list with reasons

**Example Output:**
`SCORE: 9/10 | REASON: Founder-led DTC brand, 12 staff, Shopify, hiring for ops — perfect fit`
`SCORE: 3/10 | REASON: 200+ staff, enterprise — out of ICP`

### Results
- **Review Time:** 5 hrs/week → 15 min/day (only 8+ leads)
- **Lead Quality:** Up — focus on high-fit only
- **Consistency:** AI scoring same criteria every time, no mood bias
- **Conversion:** Higher — time spent on best leads
- **Client Quote:** "This is the first time I opened my inbox and knew exactly who to email first."

### What Client Gets
- Sourcing system (Apollo + Hunter free tier setup guide)
- Scoring scenario + digest scenario + blueprints (sanitized)
- Lead Inbox sheet template with Score/Reason columns + parsing formula
- Loom walkthrough (5 min): how scoring works, how to adjust ICP, how to change threshold from 8 to 7
- Documentation: how to add new leads, how digest works, how to edit prompt for different ICP
- 7 days support

### Tools & Cost
- Apollo Free (limited exports), Hunter Free (25 searches), Sheets Free, Gemini Free Tier (15 req/min), Make Free (1,000 ops), Gmail Free
- Running cost $0 — client pays for build + documentation + upkeep

### Retainer Angle
"Lead criteria change as your business changes — new products, new ICP, new disqualifiers. Monthly plan means I update scoring prompt as your ICP evolves, add new sources, fix when Apollo/Hunter connections expire, and adjust digest timing. Otherwise, you handle it yourself — fully documented."

---
Demo: [Add Link] | Portfolio: github.com/aiagentbuilderhq/automation-portfolio
