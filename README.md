# n8n Automation Portfolio

Production-ready n8n workflows that replace expensive SaaS tools with custom automation. Every project below is **fully working code** — clone the repo, import the workflow, add your API key, and you're running.

All workflows use **DeepSeek** as the LLM (35× cheaper than GPT-4 for the same JSON-output quality), but they're drop-in compatible with OpenAI / Claude / Gemini if you prefer.

**About me:** I'm a freelance n8n + AI automation engineer based in Czechia. I build production workflows that save businesses hours per week and replace $99–500/month SaaS subscriptions. Find me on [Fiverr](https://fiverr.com/alexkinis).

---

## ⭐ Flagship: AI Acquisition Engine

> **An 8-workflow sales automation system that replaces a $500-1,500/month SaaS stack (Apollo + Lemlist + Calendly + HubSpot) and the work of one SDR.**

#### [n8n-acquisition-engine](https://github.com/ortholeshkin-oss/n8n-acquisition-engine)

Drop a list of company URLs in. Get back enriched leads, personalized outreach drafts in your Gmail, classified replies in Slack, calendar invites for the prospects who say yes, and a weekly executive report on what worked. All for $5-15/month in API costs. Run it from your phone via a Telegram bot.

The 10 workflows below are **smaller pieces of the same playbook**. Acquisition Engine connects them into one orchestrated system with shared Postgres state, a Telegram control panel, and an analytics layer. Read [`ARCHITECTURE.md`](https://github.com/ortholeshkin-oss/n8n-acquisition-engine/blob/main/ARCHITECTURE.md) to see how it's wired.

- **Tech:** 8 workflows · 6-table Postgres schema · Telegram bot · DeepSeek throughout
- **Replaces:** Apollo $99/mo + Lemlist $59/mo + Calendly $20/mo + HubSpot $50/mo + 1 SDR ($60-80k/yr)
- **License:** PolyForm Noncommercial 1.0.0 — free for personal, education, research, noncommercial. Commercial use requires a paid license ([DM me on Fiverr](https://fiverr.com/alexkinis)).

For a custom build adapted to your CRM and outbound process: $1,500-3,000, 7-14 day turnaround.

---

## The 10 building-block workflows

These are smaller, single-purpose workflows. Each one is MIT-licensed and works on its own. They're also the components that ship inside the Acquisition Engine flagship above.

### 🎯 Sales / Lead generation

#### [n8n-lead-enrichment-pipeline](https://github.com/ortholeshkin-oss/n8n-lead-enrichment-pipeline)
Send a list of company URLs. Get back enriched leads: company name, industry, employee size, funding stage, buyer persona, B2B SaaS fit score, **personalised cold-outreach pitch angle**, contact emails. Single URL or batch up to 50.
- **Cost:** ~$0.0007 per enriched lead
- **Replaces:** Apollo ($99/mo), Clay ($99-149/mo), Lavender ($29/mo)
- **ROI:** 1,000 leads = $0.70 vs $99/mo = **140× cheaper**

#### [n8n-cold-email-generator](https://github.com/ortholeshkin-oss/n8n-cold-email-generator)
Send your business pitch + target URLs. Get back personalised cold emails (subject + body + LinkedIn DM + day-4 follow-up) per target. Locked to your actual pitch — no generic AI substitutions.
- **Cost:** ~$0.0011 per personalised email
- **Replaces:** Apollo Sequences ($59/mo), Lavender ($29/mo), SDR labour
- **ROI:** 200 emails/mo = $0.22 vs $59 Lavender = **268× cheaper**

#### [n8n-social-listening-bot](https://github.com/ortholeshkin-oss/n8n-social-listening-bot)
Track keywords on Reddit. Each post classified by sentiment (positive/neutral/negative), intent (buying signal / bug report / complaint / praise / comparison), action priority, and competitor mentions. Detects buying signals in real time.
- **Cost:** ~$0.0005 per keyword check
- **Replaces:** Brand24 ($99-399/mo), Mention.com ($41-149/mo)
- **ROI:** Hourly tracking of 5 keywords = $1.80/mo vs $99/mo Brand24 = **55× cheaper**

### 💬 Customer ops

#### [n8n-customer-support-bot](https://github.com/ortholeshkin-oss/n8n-customer-support-bot)
Telegram-ready support bot with grounded RAG over your docs. Cited answers, confidence-aware escalation, intent classification (`pricing|technical|billing|...`), Slack handoff for uncertain queries. No hallucinations — refuses to make things up when KB doesn't cover the question.
- **Cost:** ~$0.0004 per conversation
- **Replaces:** Intercom AnswerBot ($99-895/mo), Zendesk Answer Bot ($50-200/mo)
- **ROI:** 10,000 conversations = $4 vs $99-895/mo = **250× to 2,000× cheaper**

#### [n8n-inbox-zero-ai](https://github.com/ortholeshkin-oss/n8n-inbox-zero-ai)
Email triage for executives. Send a batch of emails (up to 30). Get back priority (urgent/action_needed/fyi/newsletter/spam/automated), summary, suggested Gmail label, action items, **ready-to-send draft replies** for actionable emails, deadline detection, sentiment.
- **Cost:** ~$0.000175 per email
- **Replaces:** Superhuman ($30/mo, no AI), Sanebox ($7-35/mo, no drafts), an EA ($1,500-4,000/mo)
- **ROI:** 4,000 emails/mo = $0.70 vs Superhuman $360/yr = saves hours/day

### 📁 Finance / Ops

#### [n8n-invoice-automation](https://github.com/ortholeshkin-oss/n8n-invoice-automation)
Send any invoice (PDF text or email body). Get back fully structured data: vendor, dates, line items, taxes, bank details, payment methods, urgency, red flags, one-line bookkeeper summary. Detects non-invoices and refuses to extract.
- **Cost:** ~$0.0005 per invoice
- **Replaces:** Veryfi ($50-200/mo), Mindee ($0.10-0.50/inv), Bill.com ($79-149/mo + per-bill)
- **ROI:** 200 invoices/mo = $0.10 vs Veryfi $99/mo = **990× cheaper**

#### [n8n-shopify-restock-alerter](https://github.com/ortholeshkin-oss/n8n-shopify-restock-alerter)
Daily inventory health check. Send SKUs with stock + velocity + lead time + price. Get back urgency-tagged alerts (stockout_now / critical / high / medium / low / safe), days until stockout, recommended order quantity, **revenue at risk in dollars**, **pre-drafted supplier emails**, executive summary. Works with Shopify, WooCommerce, BigCommerce, Amazon.
- **Cost:** ~$0.0007 per inventory check
- **Replaces:** Stocky ($10-99/mo), Inventory Planner ($99-349/mo), Cogsy ($129-449/mo)
- **ROI:** 1,000 SKUs daily = $21/mo vs Inventory Planner $199/mo = **9× cheaper**

### ⚡ Productivity

#### [n8n-content-repurpose-engine](https://github.com/ortholeshkin-oss/n8n-content-repurpose-engine)
Paste a podcast transcript / video transcript / webinar / sales call / article. Get back **17 platform-native content pieces in 30-45 seconds**: 1 SEO blog post (~1000 words structured), 5 LinkedIn posts (different angles), 10 tweets (10 distinct angles), 1 newsletter (subject + preheader + body), 3 quote-worthy pull lines, primary themes.
- **Cost:** ~$0.0014 per long-form source
- **Replaces:** Repurpose.io ($30/mo, audio only), Castmagic ($23-99/mo), $500-2,000 from a content agency
- **ROI:** 4 episodes/mo at agency = $2,000 vs **$0.05 in DeepSeek + your time** = pays for itself on episode 1

#### [n8n-meeting-notes-to-tasks](https://github.com/ortholeshkin-oss/n8n-meeting-notes-to-tasks)
Paste a meeting transcript. Get back structured action items with **owners and due dates** (auto-converted from "next Wednesday" to YYYY-MM-DD), decisions, open questions, risks, blocker dependencies, next-meeting agenda, and meeting health scores (clarity + actionability).
- **Cost:** ~$0.0006 per meeting
- **Replaces:** Otter.ai ($30/mo), Fireflies.ai ($18-29/mo), Fellow ($7-12/mo), Granola ($19/mo)
- **ROI:** 10-meeting/wk team of 10 = $3,600/yr Otter vs **$1/mo this workflow** = **$3,500+ saved**

#### [n8n-competitor-pricing-monitor](https://github.com/ortholeshkin-oss/n8n-competitor-pricing-monitor)
Track competitor pricing pages on a schedule. Extracts plans, prices (monthly/annual), key features, free trials. **Auto-detects changes vs. previous snapshot** — flags price up/down with %, plans added/removed, free trial changed.
- **Cost:** ~$0.0018 per check
- **Replaces:** Prisync ($99/mo), Crawlmetric ($49/mo), Competera ($200+/mo), manual VA ($320/mo)
- **ROI:** Daily check of 20 competitors = $1.10/mo vs Crawlmetric $49/mo = **45× cheaper**

---

## Why these workflows are dramatically cheaper than the SaaS they replace

The math behind it is simple:

1. **n8n + DeepSeek does the actual work.** SaaS tools wrap the same functionality with marketing, sales, and 80%+ gross margins.
2. **DeepSeek is 35× cheaper than GPT-4** for structured-JSON tasks like extraction and classification, with comparable accuracy.
3. **You pay once for the build, run forever at marginal cost.** No per-seat fees, no per-message charges, no contracts.
4. **The 10 component workflows are yours under MIT.** Modify, fork, sell, white-label — all permitted. (The Acquisition Engine flagship uses a different license — see its README.)

A typical SaaS company charging $99/month for one of these features has a cost-of-goods of <$2/month per user. The other $97 is sales, marketing, support, and profit margin.

This portfolio shows what those products *actually* do under the hood — and how to ship the same outcome at the cost-of-goods price.

---

## Common shape across all 10 building-block workflows

Each repo has the same structure for easy onboarding:

```
repo/
├── README.md         # full docs with live curl examples and ROI math
├── workflow.json     # importable n8n workflow (drop into your n8n)
├── test.html         # standalone web UI for testing
├── docs/setup.md     # step-by-step setup guide
├── LICENSE           # MIT
└── .gitignore
```

**To run any one of them:**

1. Clone the repo
2. Import `workflow.json` into n8n (Workflows → Import from File)
3. Get a DeepSeek API key (~$2 covers thousands of runs)
4. Add a Header Auth credential `Authorization: Bearer sk-YOUR_KEY` to the DeepSeek node
5. Activate the workflow
6. Open `test.html` in a browser, or use the curl examples in the README

Total setup time: 5–10 minutes per workflow.

---

## Want a customised version?

Each workflow ships as a generic foundation. For your specific use case — your CRM, your accounting database, your supplier portal, your domain knowledge — I do custom adaptations on Fiverr.

| Tier | Scope | Price | Turnaround |
|---|---|---|---|
| Single workflow adaptation | One of the 10 building blocks adapted to your stack | $90-450 | 3-7 days |
| Multi-workflow integration | 3-4 workflows wired together | $600-1,200 | 5-7 days |
| **Full Acquisition Engine** | All 8 workflows custom-built for your CRM and outbound process | **$1,500-3,000** | **7-14 days** |
| Hosted-on-our-VPS | Managed hosting + monitoring | $200-300/mo | recurring |

Find me on [Fiverr](https://fiverr.com/alexkinis) — search for "n8n automation" or DM me directly with your use case for a no-cost feasibility check before you order.

---

## Tech stack used across the portfolio

- **n8n** (open-source, self-hosted) — the workflow engine
- **DeepSeek** API — primary LLM (`deepseek-chat`, ~$0.14/$0.28 per 1M input/output tokens)
- **Optional swaps**: OpenAI, Claude, Gemini, Groq, MiniMax — same prompts, just different endpoints
- **No vendor lock-in** — every workflow is a JSON file you control

---

## License

- **The 10 building-block workflows:** MIT — use freely in personal and commercial projects, fork them, sell them — just don't claim you wrote them.
- **AI Acquisition Engine flagship:** PolyForm Noncommercial 1.0.0 — free for personal, education, research, noncommercial. Commercial use requires a paid license ([contact via Fiverr](https://fiverr.com/alexkinis)).

---

Built by **Oleksii Kinishenko** — [GitHub](https://github.com/ortholeshkin-oss) · [Fiverr](https://fiverr.com/alexkinis)
