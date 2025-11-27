# Scenario: AI Ethics & Bias Mitigation Program

**Category:** Ethics / Compliance / Risk / DEI
**Trigger:** A company faces public backlash or lawsuit after their AI system discriminates (denying loans to minorities, biased hiring, unfair content moderation). They need a comprehensive ethics program.

---

## 1. The Situation
**Real-World Examples**:
- Amazon scrapped hiring AI (2018): Penalized resumes mentioning "women's" colleges.
- Apple Card (2019): Gave women lower credit limits than men with same financials.
- Healthcare AI (2019): Prioritized white patients over Black patients for care.
- COMPAS recidivism AI: Predicted Black defendants were higher risk than white defendants with similar histories.

**The Problem**: AI inherits and amplifies biases in training data. Without intervention, it perpetuates systemic discrimination.

## 2. The Diagnosis: Sources of Bias

### Bias Type A: Historical Bias
**Definition**: Training data reflects past discrimination.
- *Example*: Hiring AI trained on 10 years of hires (90% male engineers) → Learns "male = engineer."

### Bias Type B: Representation Bias
**Definition**: Training data under-represents certain groups.
- *Example*: Facial recognition trained mostly on white faces → 35% error rate on Black faces.

### Bias Type C: Measurement Bias
**Definition**: Data collection methods are biased.
- *Example*: Arrest records overrepresent minorities (due to biased policing), but AI uses arrests as "crime" metric.

### Bias Type D: Aggregation Bias
**Definition**: One model for all groups ignores group-specific differences.
- *Example*: Medical AI trained on adults fails on children.

### Bias Type E: Evaluation Bias
**Definition**: Testing doesn't include all groups.
- *Example*: Chatbot tested only in English → Fails in Spanish.

### Bias Type F: Deployment Bias
**Definition**: System used in ways it wasn't designed for.
- *Example*: Resume screener designed for Fortune 500 used by small startups (different talent pools).

## 3. The Alara AI Ethics Framework

### Principle 1: Fairness
**Definition**: AI treats all groups equitably.

**Fairness Metrics** (Choose based on context):
1.  **Demographic Parity**: Equal acceptance rates across groups.
    - 50% of men and 50% of women get hired.
2.  **Equal Opportunity**: Equal true positive rates.
    - Of qualified applicants, same % of men and women are hired.
3.  **Predictive Parity**: Equal precision across groups.
    - Of people hired, same % of men and women succeed.

**The Impossibility Theorem**: You can't satisfy all fairness definitions simultaneously. You must choose based on your values and legal requirements.

### Principle 2: Transparency
**Definition**: Users understand how AI makes decisions.

**Implementation**:
- Disclose AI is being used.
- Provide explanations (SHAP, LIME).
- Publish model cards (data sources, limitations).

### Principle 3: Accountability
**Definition**: Clear ownership when AI fails.

**Implementation**:
- Designate an "AI Ethics Officer."
- Audit trail for all decisions.
- Complaint mechanism for affected individuals.

### Principle 4: Privacy
**Definition**: Minimize data collection and protect sensitive info.

**Implementation**:
- Differential privacy.
- Federated learning.
- Data minimization (don't collect what you don't need).

### Principle 5: Safety & Robustness
**Definition**: AI fails gracefully and doesn't cause harm.

**Implementation**:
- Adversarial testing (red-teaming).
- Human-in-the-loop for high-stakes decisions.
- Kill switches.

## 4. The Alara Playbook: Building an Ethics Program

### Phase 1: Assessment & Audit (Month 1-2)

#### Step 1: Inventory All AI Systems
Create a registry:
| System | Use Case | Risk Level | Protected Classes Involved | Last Audit |
|--------|----------|------------|---------------------------|------------|
| Resume Screener | Hiring | High | Race, Gender, Age | Never |
| Fraud Detector | Finance | High | Race, Location | 2023-Q4 |
| Chatbot | Customer Service | Low | None | 2024-Q1 |

#### Step 2: Bias Testing
For each high-risk system:
1.  **Dataset Analysis**: What % of training data is each demographic?
2.  **Model Analysis**: Does the model treat groups differently?
3.  **Outcome Analysis**: In production, are outcomes fair?

**Example Test**:
- Resume screener: Test with identical resumes, change only the name (Mary vs. Jamal).
- Expected: Same score.
- Reality: Jamal scores 20% lower → Bias detected.

#### Step 3: Impact Assessment
Document potential harms:
- **Who could be harmed?** (Specific groups)
- **How severe?** (Denied loan vs. slower chatbot response)
- **How likely?** (Probability of harm occurring)

### Phase 2: Mitigation Strategies (Month 3-6)

#### Strategy A: Pre-Processing (Fix the Data)
**Technique 1: Reweighting**
- Oversample underrepresented groups in training data.
- *Example*: If dataset is 90% men, duplicate women's data to achieve 50/50 balance.

**Technique 2: Resampling**
- Ensure equal representation across demographics.

**Technique 3: Synthetic Data**
- Generate synthetic examples for underrepresented groups.

#### Strategy B: In-Processing (Fix the Model)
**Technique 1: Fairness Constraints**
- During training, penalize the model for discriminatory outputs.
- *Example*: "Maximize accuracy subject to demographic parity constraint."

**Technique 2: Adversarial Debiasing**
- Train two models: Main model + Adversary.
- Adversary tries to predict protected attributes from main model's decisions.
- Main model learns to hide demographic info from adversary.

#### Strategy C: Post-Processing (Fix the Outputs)
**Technique 1: Threshold Adjustment**
- Use different decision thresholds for different groups to achieve fairness.
- *Example*: Accept top 50% of Group A, top 60% of Group B (to equalize acceptance rates).

**Technique 2: Calibration**
- Ensure predicted probabilities match actual outcomes for all groups.

### Phase 3: Governance & Policy (Month 3-6)

#### Component A: The AI Ethics Board
**Composition**:
- CTO (technical expertise)
- Legal Counsel (compliance)
- DEI Officer (equity perspective)
- Product Lead (business context)
- External Ethicist (independent view)

**Responsibilities**:
- Review high-risk AI systems before launch.
- Approve bias mitigation strategies.
- Investigate complaints.
- Publish annual ethics report.

#### Component B: The AI Use Policy
**Prohibited Uses**:
- Social scoring (China-style citizen scores).
- Emotion detection for hiring decisions (pseudoscience).
- Facial recognition for mass surveillance.

**High-Risk Uses (Require Board Approval)**:
- Hiring, promotion, termination.
- Credit, insurance underwriting.
- Criminal justice (bail, sentencing).
- Healthcare diagnostics.

**Low-Risk Uses (Standard Review)**:
- Content recommendation.
- Spam filtering.
- Productivity tools.

#### Component C: The Model Card
Publish a "nutrition label" for each AI system:
```
Model Card: Resume Screening AI v2.3

Intended Use: Screen resumes for software engineering roles.

Training Data: 50,000 resumes from 2020-2024.
Demographics: 70% male, 30% female; 60% white, 20% Asian, 10% Black, 10% Hispanic.

Limitations:
- May underperform on non-traditional backgrounds (bootcamp grads, career changers).
- Not suitable for non-technical roles.

Bias Testing:
- Demographic parity: Pass (within 5% across gender, race).
- Equal opportunity: Pass (within 3% across groups).

Last Updated: 2024-11-15
Next Review: 2025-05-15
```

### Phase 4: Monitoring & Continuous Improvement (Ongoing)

#### Real-Time Dashboards
Track fairness metrics in production:
```
┌────────────────────────────────────────┐
│ Hiring AI: Weekly Fairness Report     │
├────────────────────────────────────────┤
│ Acceptance Rate by Gender:            │
│   Male:   42% (850/2,000 applicants)  │
│   Female: 39% (390/1,000 applicants)  │
│   Delta:  -3% ⚠️ (threshold: ±5%)    │
├────────────────────────────────────────┤
│ Acceptance Rate by Race:              │
│   White:     45%                       │
│   Black:     38% ⚠️ (-7%)             │
│   Hispanic:  40%                       │
│   Asian:     50%                       │
└────────────────────────────────────────┘

Action: Alert sent to AI Ethics Board.
```

#### Incident Response Protocol
**Scenario**: User files complaint ("AI rejected me unfairly").

**Response**:
1.  **Acknowledge** (24 hours): "We received your complaint and are investigating."
2.  **Investigate** (7 days): Pull logs, recreate decision, test for bias.
3.  **Resolve** (14 days): 
    - If bias found: Overturn decision, compensate if appropriate.
    - If no bias found: Explain decision with transparency.
4.  **Prevent** (30 days): If systemic issue, retrain model or adjust policy.

## 5. Legal & Regulatory Compliance

### US: Equal Employment Opportunity Commission (EEOC)
- AI hiring tools must not discriminate based on race, color, religion, sex, national origin, age, disability, genetic information.
- **Requirement**: Regular audits, ability to explain decisions.

### EU: AI Act (2024)
- **High-Risk AI**: Hiring, credit scoring, law enforcement → Requires conformity assessment.
- **Transparency**: Users must be informed they're interacting with AI.
- **Fines**: Up to €30M or 6% of global revenue.

### NYC: Local Law 144 (2023)
- **Requirement**: Annual bias audit by independent auditor.
- **Disclosure**: Candidates must be told if AI is used in hiring.

### California: CCPA & CPRA
- **Requirement**: Consumers can request data deletion (complicates training data management).

## 6. Industry-Specific Considerations

### Finance: Fair Lending (ECOA, FCRA)
- Cannot discriminate in lending based on race, color, religion, sex, marital status, age.
- **Explainability**: Must provide "adverse action notices" with specific reasons.

### Healthcare: Bias in Clinical AI
- **Risk**: AI trained on majority populations fails on minorities.
- **Example**: Pulse oximeters (used by AI) are less accurate on darker skin tones.
- **Mitigation**: Stratified validation (test across all demographics).

### Criminal Justice: Algorithmic Sentencing
- **Risk**: COMPAS-style tools reproduce racial disparities.
- **Best Practice**: Many jurisdictions now ban or heavily restrict these tools.

## 7. The ROI of Ethics

**Cost of Doing Nothing**:
- Legal fees: $500K-5M per lawsuit.
- Reputation damage: Unmeasurable (customers leave, talent refuses to join).
- Regulatory fines: Up to $30M (EU AI Act).

**Cost of Ethics Program**:
- Initial setup: $100K-500K (audits, bias testing, policy).
- Ongoing: $200K/year (monitoring, audits).

**ROI**:
- Avoid a single lawsuit → 10x return on investment.
- Brand differentiation: "Certified Fair AI" attracts customers.
- Talent acquisition: Engineers want to work for ethical companies.

## 8. The "Gotchas"

### Gotcha A: "We Don't Collect Race, So We're Fair"
**Problem**: Even without explicit race data, AI can infer it from proxies (ZIP code, names, speech patterns).

**Solution**: Test for disparate impact, even without protected attribute labels.

### Gotcha B: "Our Model Is Accurate, So It's Fair"
**Problem**: A model can be 95% accurate overall but 60% accurate on a minority group.

**Solution**: Measure accuracy *by subgroup*, not just overall.

### Gotcha C: "We Fixed Bias in Training, So We're Done"
**Problem**: Bias creeps back in production (deployment bias, data drift).

**Solution**: Continuous monitoring, not one-time fixes.

## 9. The Alara Certification Program

We offer clients a "Certified Fair AI" badge:
1.  **Independent audit** of AI systems.
2.  **Public report** on fairness testing results.
3.  **Remediation plan** for any issues found.
4.  **Annual re-certification**.

**Benefit**: Market differentiation, regulatory compliance, stakeholder trust.

## 10. The Future: AI Bill of Rights

**US White House AI Bill of Rights (2022)** proposes:
1.  Right to safe and effective systems.
2.  Protection against algorithmic discrimination.
3.  Data privacy.
4.  Notice and explanation.
5.  Human alternatives and fallback.

**The Alara Position**: Ethics is not optional. It's a competitive advantage. Companies that build fair AI will win in the long run.
