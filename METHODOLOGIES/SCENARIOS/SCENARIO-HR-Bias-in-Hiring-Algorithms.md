# Scenario: HR Bias in Hiring Algorithms

**Category:** Ethics / Compliance / HR
**Trigger:** A candidate complains they were rejected by an AI; or an internal audit reveals the AI is rejecting 80% of female applicants for technical roles.

---

## 1. The Situation
The company bought a "Resume Screening AI" to handle 10,000 applications. It seemed to work great, saving recruiters thousands of hours. But now, data shows it's replicating historical biases (e.g., penalizing "gap years" or "women's colleges").

## 2. The Diagnosis
**Training Data Bias**: The model was trained on the company's *past* successful hires. If the company historically hired mostly men named "Matt", the AI learned that "Matt" is a feature of a good candidate.

## 3. The Alara Playbook

### Phase 1: The "Black Box" Audit (Week 1)
1.  **Stop the Auto-Reject**: Switch the AI to "Recommendation Only" mode. No candidate is rejected without human eyes.
2.  **Feature Importance Analysis**: Use explainability tools (SHAP values) to see *why* it's making decisions.
    - *Red Flag*: Is it weighting zip codes? (Proxy for race).
    - *Red Flag*: Is it weighting "Lacrosse"? (Proxy for wealth).

### Phase 2: Remediation (Week 2-4)
1.  **Blind Screening**: Configure the tool to strip names, addresses, and graduation years before the AI analyzes the text.
2.  **Counterfactual Testing**: Take a rejected resume. Change the name from "Mary" to "Mark". Does the score change? If yes, the model is broken.

### Phase 3: Governance (Ongoing)
1.  **The "Human-in-the-Loop" Rule**: AI can rank candidates, but only a human can reject.
2.  **NYC Local Law 144 Compliance**: If the client is in NYC (or EU), they legally need an annual independent bias audit. We structure this audit.

## 4. The "Gotchas"
- **Vendor Blame**: The vendor says "Our model is unbiased." But if you trained it on *your* data, the bias is yours, not theirs.
- **Proxy Variables**: Removing "Gender" isn't enough if you leave in "Women's Rugby Team Captain".
