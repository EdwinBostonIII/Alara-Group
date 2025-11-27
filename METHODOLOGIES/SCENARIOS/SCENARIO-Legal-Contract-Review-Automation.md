# Scenario: Legal Contract Review Automation

**Category:** Legal / Operations
**Trigger:** The General Counsel is blocking deals because the legal team takes 2 weeks to review a standard NDA or MSA (Master Services Agreement). Sales is furious.

---

## 1. The Situation
Highly paid lawyers are spending hours reading standard contracts to check for simple things like "Is the jurisdiction New York?" or "Is the payment term Net 30 or Net 60?".

## 2. The Diagnosis
This is a "High Volume, Low Complexity" task. Perfect for AI. Lawyers should focus on the "High Complexity" negotiation, not the redlining of standard terms.

## 3. The Alara Playbook

### Phase 1: The Playbook Definition (Week 1-2)
We sit with the General Counsel to define the "Golden Rules":
- *Rule*: "We never accept unlimited liability."
- *Rule*: "Governing law must be Delaware or New York."
- *Rule*: "Payment terms cannot exceed 60 days."

### Phase 2: The AI Redliner (Week 3-6)
1.  **System Prompting**: We configure an LLM with the Golden Rules.
2.  **Workflow**:
    - Sales uploads a PDF contract.
    - AI reads it and compares it to the Rules.
    - AI generates a "Redline Report": "Clause 4.2 violates our liability policy. Suggested edit: [Insert Standard Clause]."

### Phase 3: The "Human-in-the-Loop" Review
1.  **The Traffic Light**:
    - *Green*: Contract matches all rules. Auto-approve (or fast-track).
    - *Yellow*: Minor deviations. Junior Lawyer review.
    - *Red*: Major risks. Senior Counsel review.

## 4. The "Gotchas"
- **Hallucinated Case Law**: Never ask the AI to "cite legal precedent" (it makes cases up). Only ask it to "compare text against our policy."
- **Data Privacy**: Contracts contain confidential info. We must use a Zero-Retention API (data is processed and immediately deleted).
