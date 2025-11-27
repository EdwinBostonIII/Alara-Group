# Scenario: M&A Due Diligence (Buying or Selling AI Assets)

**Category:** Strategy / M&A / Valuation
**Trigger:** A private equity firm is buying a company with "AI-powered" products. They need to know: Is the AI real? Is it valuable? What are the technical risks?

---

## 1. The Situation
**Buyer's Perspective**: "The target company claims their 'proprietary AI' is their competitive moat. We need to validate this before paying a premium."

**Seller's Perspective**: "We've invested $5M in AI. How do we prove its value to maximize our exit multiple?"

## 2. The Diagnosis (What Makes AI Due Diligence Hard)
Unlike traditional software, AI has hidden risks:
- **Model Dependency**: Does the AI rely on OpenAI's API? What if pricing 10x's?
- **Data Ownership**: Who owns the training data? Can it transfer to a new owner?
- **Talent Risk**: Is the "AI" just one PhD who's planning to leave?
- **IP Claims**: Did they train on scraped web data? (Copyright risk.)

## 3. The Alara AI Due Diligence Framework

### Phase 1: The Technical Audit (Week 1-2)

#### A. Model Architecture Review
**Questions**:
1. Is this a custom model or a wrapper around GPT-4?
   - *Custom*: Higher IP value, but maintenance burden.
   - *Wrapper*: Low differentiation, but faster to market.
2. What's the training data source?
   - *Proprietary*: Valuable.
   - *Public datasets*: Low moat.
3. Model performance: What are accuracy, latency, cost metrics?

**Red Flags**:
- No performance benchmarks documented.
- Can't demonstrate the model running live.
- "It's proprietary, we can't share" (often means it doesn't exist).

#### B. Infrastructure & Scalability
**Questions**:
1. Where is the model hosted? (On-prem, AWS, GCP, Azure?)
2. What's the cost structure? ($/API call, $/compute hour)
3. Can it scale 10x without rewriting everything?

**Red Flags**:
- Hardcoded to a single server (no load balancing).
- No monitoring or alerting systems.
- Tech debt: "It works, but we need to refactor it."

#### C. Data Assets
**Questions**:
1. How much data exists? (GB, TB, records count)
2. Data quality: Is it labeled? Clean? Current?
3. Data rights: Can the company legally use this data post-acquisition?

**Red Flags**:
- Training data includes customer data without consent.
- Data is scraped from competitors' websites (legal risk).
- No data pipeline (they trained once and never updated).

### Phase 2: The Business Audit (Week 2-3)

#### A. Customer Validation
**Questions**:
1. Do customers actually use the AI feature?
2. Is AI the reason customers buy, or is it "nice to have"?
3. If the AI broke, would customers leave?

**Method**: Interview 5-10 customers. Ask: "If [Company] removed the AI feature, would you churn?"

#### B. Revenue Attribution
**Questions**:
1. How much revenue is directly attributable to AI?
2. What's the pricing model? (Flat fee, per-prediction, usage-based?)
3. Can you prove ROI to customers?

**Red Flags**:
- "All our revenue is AI-driven" (vague, unverifiable).
- No pricing differentiation between AI and non-AI tiers.
- Customers don't know the AI exists.

### Phase 3: The Legal & IP Audit (Week 3-4)

#### A. IP Ownership
**Questions**:
1. Does the company own the model weights?
2. Are there any open-source components? (What's the license?)
3. Did contractors build it? (Who owns the IP?)

**Red Flags**:
- Model was built by an external vendor who retained IP.
- Open-source licenses are "copyleft" (GPL) requiring code disclosure.
- Patents are pending but not granted (weak protection).

#### B. Regulatory Compliance
**Questions**:
1. Is the AI used in regulated industries? (Healthcare, Finance, Government)
2. Does it comply with GDPR, CCPA, HIPAA?
3. Has it been audited for bias?

**Red Flags**:
- No bias testing on protected classes.
- Personal data is training data (GDPR violation).
- Claims "FDA approved" without documentation.

### Phase 4: The Risk Assessment (Week 4)

#### A. Key Person Risk
**Questions**:
1. Who are the core AI engineers?
2. Are they under non-compete agreements?
3. If they leave, can the model be maintained?

**Red Flags**:
- Only 1-2 people understand the model.
- No documentation ("it's all in their head").
- Engineers have LinkedIn profiles saying "Open to offers."

#### B. Vendor Dependency
**Questions**:
1. What happens if OpenAI 10x's their pricing?
2. What happens if a key data provider shuts down?
3. Are there alternative vendors?

**Red Flags**:
- 100% dependent on a single API (OpenAI, AWS Bedrock).
- No contract with the vendor (month-to-month).
- Vendor is a startup that might go bust.

## 4. The Valuation Impact

### High-Value AI (Premium Multiple)
- Custom model trained on proprietary data.
- Defensible IP (patents, trade secrets).
- Proven ROI with customer testimonials.
- Low vendor dependency.

### Low-Value AI (No Premium)
- Thin wrapper around GPT-4.
- Generic use case (anyone can replicate).
- No proof of customer adoption.
- High technical debt.

**Rule of Thumb**: If the "AI" can be replaced with a $500/month ChatGPT Enterprise subscription, it's not worth a premium.

## 5. The Alara Deliverable: "AI Due Diligence Report"

**Structure**:
1. **Executive Summary**: (2 pages) Buy/Don't Buy recommendation with key risks.
2. **Technical Deep Dive**: (10 pages) Architecture, data, performance.
3. **Business Case**: (5 pages) Revenue analysis, customer validation.
4. **Risk Matrix**: (1 page) Likelihood x Impact of key risks.
5. **Recommendations**: (3 pages) "If you buy, you must do X, Y, Z in the first 90 days."

## 6. Post-Acquisition Integration (The First 100 Days)
If the deal closes, we help with:
1. **Talent Retention**: Golden handcuffs for key AI engineers.
2. **IP Protection**: Move model weights to buyer's infrastructure.
3. **Quick Wins**: Identify 2-3 improvements to show value.
4. **Risk Mitigation**: Address the top 3 risks from the due diligence report.

## 7. The "Gotchas"
- **The "AI Washing" Trap**: Sales decks say "AI-powered" but it's just if-then rules.
- **The "Lab vs. Production" Gap**: The demo works great, but the production version is broken.
- **The "Data Time Bomb"**: Training data includes copyrighted or biased content that surfaces post-acquisition.
