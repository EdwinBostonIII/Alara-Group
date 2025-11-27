# Scenario: Executive Dashboard & Reporting

**Category:** Strategy / Executive Alignment / Communication
**Trigger:** The CEO asks, "What are we getting from our $2M AI investment?" The data science team shows them a confusion matrix. The CEO's eyes glaze over.

---

## 1. The Situation
The technical team is excited about improving model accuracy from 87% to 91%. The CFO wants to know how that translates to dollars saved or revenue gained. The communication gap is killing buy-in for Phase 2 funding.

## 2. The Diagnosis
**Misaligned Metrics**: Technical teams measure what they can control. Executives care about business outcomes.

| What Engineers Report | What Executives Hear |
|-----------------------|----------------------|
| "F1 Score improved 4%" | "I don't know what that means" |
| "Latency reduced to 200ms" | "Is that good?" |
| "We implemented RAG with a vector DB" | "Sounds expensive" |

## 3. The Alara Playbook

### Phase 1: Define Executive-Level KPIs (Week 1)
Work backwards from business goals:

**For a Sales AI**:
- ❌ Technical: "Suggestions accepted 60% of the time."
- ✅ Business: "Sales cycle shortened by 12 days (from 45 to 33)."

**For a Customer Support AI**:
- ❌ Technical: "Bot handles 70% of queries."
- ✅ Business: "Support costs reduced by $180K annually. Customer satisfaction up 8 points."

**For a Fraud Detection AI**:
- ❌ Technical: "Precision 95%, Recall 88%."
- ✅ Business: "Caught $4.2M in fraud while reducing false declines by 40%."

### Phase 2: The "One-Page" Executive Dashboard (Week 2)
Design a single-screen view (no scrolling) with three sections:

**Section 1: The Headline (Top)**
```
+--------------------------------------------------+
| AI Initiative: Customer Service Chatbot          |
| Status: ✅ On Track                              |
| ROI: $850K savings in Year 1 (vs. $500K invested)|
+--------------------------------------------------+
```

**Section 2: Business Impact Metrics (Middle)**
```
┌─────────────────┬──────────────┬──────────────┐
│ Metric          │ Before AI    │ After AI     │
├─────────────────┼──────────────┼──────────────┤
│ Avg Handle Time │ 8.5 min      │ 5.2 min ⬇39%│
│ Customer Sat    │ 72/100       │ 81/100 ⬆9   │
│ Agent Turnover  │ 35% annually │ 22% ⬇13%    │
└─────────────────┴──────────────┴──────────────┘
```

**Section 3: Risk Indicators (Bottom)**
```
⚠️ Risks to Watch:
• Model accuracy declined 2% this month (investigating)
• 15% of agents still not using the tool regularly
```

### Phase 3: The Narrative, Not Just Numbers (Ongoing)
Executives remember stories, not statistics.

**Bad Reporting**: "The AI processed 50,000 claims with 92% accuracy."

**Good Reporting**: "The AI processed a catastrophic hurricane event in 48 hours. This task previously took our team 3 weeks. We closed claims faster, customers got paid sooner, and our Net Promoter Score hit an all-time high."

### Phase 4: The Quarterly Business Review Format (Every 90 Days)
**Structure the meeting**:

**1. Recap (5 min)**: What we promised last quarter.
**2. Results (10 min)**: What we delivered (with business metrics).
**3. Impact Stories (10 min)**: 2-3 specific examples with customer/employee quotes.
**4. Lessons Learned (5 min)**: What didn't work (own the failures).
**5. Next Quarter Plan (10 min)**: What we're doing next and why it matters.

**Total**: 40 minutes. Executives will actually attend.

## 4. Advanced: The "AI Investment Portfolio" View
For organizations with multiple AI initiatives, create a portfolio view:

```
┌────────────────────────────────────────────────┐
│ AI Investment Portfolio - Q4 2025              │
├─────────────────┬────────┬─────────┬──────────┤
│ Initiative      │ Invest │ Return  │ ROI      │
├─────────────────┼────────┼─────────┼──────────┤
│ Chatbot         │ $500K  │ $850K   │ 170% ✅  │
│ Underwriting    │ $800K  │ $1.2M   │ 150% ✅  │
│ Code Assistant  │ $300K  │ $200K   │ 67%  ⚠️  │
│ Marketing Gen   │ $150K  │ $50K    │ 33%  🔴  │
└─────────────────┴────────┴─────────┴──────────┘
```

This view helps executives make "kill vs. double-down" decisions.

## 5. The Communication Cadence
**Weekly**: Technical team updates (Slack/email).
**Monthly**: Operational dashboard shared with VPs (automated email with dashboard link).
**Quarterly**: Executive presentation (live, with Q&A).
**Annually**: Board of Directors deck (high-level strategy and competitive positioning).

## 6. Red Flags That Kill AI Programs
These are the phrases that make CFOs want to shut down AI:
- **"We need more time to see results."** (No clear timeline.)
- **"It's too technical to explain."** (You don't understand it yourself.)
- **"Trust us, it's working."** (No data to back it up.)
- **"Everyone else is doing it."** (FOMO isn't a strategy.)

## 7. The "Gotchas"
- **Vanity Metrics**: "10,000 users signed up!" means nothing if only 100 are active.
- **Lagging Indicators**: Revenue might not change for 6 months after AI launch. Use leading indicators (pipeline velocity, customer satisfaction).
- **Attribution Problems**: Did sales go up because of AI or because the economy improved? Use control groups if possible.

## 8. Tools We Use
- **Dashboarding**: Tableau, Power BI, Looker (connected to real-time data).
- **Narrative Reports**: Notion, Confluence (for the "story" component).
- **ROI Calculators**: Custom Excel/Google Sheets models with sensitivity analysis.
