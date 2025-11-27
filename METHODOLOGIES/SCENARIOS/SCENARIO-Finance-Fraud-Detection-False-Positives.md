# Scenario: Fraud Detection False Positives (Finance)

**Category:** Finance / Risk
**Trigger:** A fintech or bank is using a legacy rules-based system to stop fraud. It's blocking 15% of legitimate transactions (False Positives), causing customers to rage-quit.

---

## 1. The Situation
The current system has rules like "If transaction > $5,000 and location = Foreign, BLOCK."
This blocks a loyal customer buying a watch on vacation. The fraud team is overwhelmed reviewing these blocked transactions manually.

## 2. The Diagnosis
Rules are binary (Yes/No). AI is probabilistic (Risk Score 0-100). AI can look at *context*: "This user travels every July, buys luxury goods, and logged in from their usual iPhone."

## 3. The Alara Playbook

### Phase 1: The Shadow Model (Month 1-2)
1.  **Feature Engineering**: We create thousands of data points (Time since last login, device battery level, typing speed).
2.  **Training**: Train an XGBoost or Neural Network on historical fraud data.
3.  **Shadowing**: Run the model alongside the Rule Engine. Don't block anything yet. Just compare. "The Rule blocked this, but the AI said it was safe."

### Phase 2: The Hybrid Approach (Month 3)
1.  **The "Grey Zone"**:
    - *Clear Fraud*: Auto-Block.
    - *Clear Safe*: Auto-Allow.
    - *Grey Zone*: Send to Human Review.
2.  **Goal**: The AI shrinks the "Grey Zone" by being more precise than the rules.

### Phase 3: Feedback Loop
1.  **Active Learning**: When a human reviewer says "This was actually safe," the model updates immediately to learn that pattern.

## 4. The "Gotchas"
- **Explainability**: You must tell the customer *why* you blocked them (in some jurisdictions). "Black box" neural networks are hard to explain. We use SHAP values to say "Blocked because location changed + device ID is new."
- **Concept Drift**: Fraudsters change tactics weekly. The model must be retrained constantly.
