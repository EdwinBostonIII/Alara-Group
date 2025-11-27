# Scenario: Explainability for Regulators (The Audit)

**Category:** Compliance / Risk / Legal
**Trigger:** The FDA, CFPB, or EU regulator asks: "Explain why your AI denied this customer." The engineering team responds: "It's a neural network, we can't." That's not an acceptable answer.

---

## 1. The Situation
A bank's loan underwriting AI denies 10,000 applications per month. A regulator picks 50 random denials and demands a written explanation for each decision within 30 days.

Alternatively, a medical device company uses AI for diagnosis support. The FDA is auditing them before approving a 510(k) clearance.

## 2. The Diagnosis (Why This Is Hard)
**Black Box Problem**: Deep learning models (neural networks) have millions of parameters. Even data scientists struggle to explain individual decisions.

**Regulatory Standards**:
- **FCRA (Fair Credit Reporting)**: Must provide "adverse action" notices with specific reasons.
- **GDPR (EU)**: Right to explanation for automated decisions.
- **FDA**: Medical AI must have "clinical validation" and interpretability.
- **EU AI Act**: High-risk AI requires transparency and auditability.

## 3. The Alara Playbook

### Phase 1: Model Architecture Assessment (Week 1)
**The Interpretability Spectrum**:
| Model Type | Interpretability | Accuracy |
|------------|-----------------|----------|
| Linear Regression | Perfect (coefficients tell you everything) | Low |
| Decision Trees | High (you can draw the tree) | Medium |
| Random Forest | Medium (feature importance) | High |
| Neural Network | Low (black box) | Very High |
| Large Language Model | Very Low | Varies |

**Question**: Do you need a neural network, or can a decision tree get you 90% of the way there?

### Phase 2: Explainability Layer Integration (Week 2-4)
If you must use a black box model, add an explanation layer:

**Option A: SHAP (SHapley Additive exPlanations)**
- Calculates each feature's contribution to a prediction.
- *Example Output*: "Loan denied because: Credit Score (-120 points), DTI Ratio (-80 points), Late Payments (-50 points)."

**Option B: LIME (Local Interpretable Model-agnostic Explanations)**
- Builds a simple "local" model around the specific prediction.
- *Output*: "For this customer, income was the most important factor."

**Option C: Attention Visualization (for LLMs)**
- Shows which words/phrases the model focused on.
- *Example*: Highlighting "bankruptcy" and "eviction" in a credit report.

### Phase 3: The Audit Trail System (Month 2)
Build a system that logs every decision with:
1.  **Input Data**: Exact data the model saw (with timestamps).
2.  **Model Version**: Which version of the model made the decision.
3.  **Explanation**: SHAP values or alternative explanation.
4.  **Human Override Log**: If a human overruled the AI, why?

**Storage**: This must be immutable and searchable. Use append-only databases or blockchain for audit-proof logs.

### Phase 4: The "Plain English" Translation (Ongoing)
Regulators and customers don't understand "SHAP values."

**Translation Layer**:
- *Technical*: "Feature X contributed -0.35 to the decision."
- *Plain English*: "Your application was declined primarily due to a high debt-to-income ratio (65%, while our threshold is 43%)."

We create templates for common decision patterns:
- **Template 1**: "Declined due to insufficient credit history."
- **Template 2**: "Declined due to recent delinquencies on existing accounts."

## 4. The "Human-in-the-Loop" Mandate
For high-risk decisions, some regulators require:
- **Human Review**: A person must review the AI decision before it's final.
- **Override Capability**: The human can disagree with the AI and document why.

**Implementation**:
- *Low-confidence decisions* (AI score 45-55%) → Automatic human review.
- *All denials* → Human spot-check 10% randomly.

## 5. The Regulator Meeting Prep
When the auditor shows up:

**Day 1: The Overview**
- Walk them through the model development lifecycle.
- Show the training data sources and bias testing results.

**Day 2: The Deep Dive**
- They pick 20 random decisions from last quarter.
- You pull up the audit log and explain each one using SHAP + plain English.

**Day 3: The Stress Test**
- "What happens if the model sees corrupted data?"
- "What if a data source goes offline?"
- You show them the circuit breakers and fallback procedures.

## 6. The "Gotchas"
- **Post-Hoc Rationalization**: SHAP can sometimes generate explanations that sound good but aren't actually how the model works. Validate explanations with domain experts.
- **Contradictory Rules**: Sometimes SHAP says Feature A was important, but your policy document says Feature A shouldn't matter. That's a red flag.
- **The "Too Honest" Problem**: Explaining that the AI weighted someone's zip code (a proxy for race) creates legal liability. You might need to remove problematic features, not just explain them.
