# Scenario: Model Performance Degradation ("It used to work fine")

**Category:** Technical / Operations / Monitoring
**Trigger:** A production AI system that was 95% accurate three months ago is now 70% accurate. Customer complaints are rising. Something changed.

---

## 1. The Situation
A claims processing AI is suddenly categorizing "water damage" as "fire damage." A chatbot that gave helpful answers now loops in circles. The data science team is confused because "nothing changed in the code."

## 2. The Diagnosis (Root Causes)

### A. Concept Drift
**What happened**: The world changed, but the model didn't.
- *Example*: A fraud model trained pre-pandemic doesn't recognize "lots of online purchases" as normal post-pandemic behavior.

### B. Data Drift
**What happened**: The input data distribution changed.
- *Example*: The insurance company started selling in a new state. The model never saw home values that high.

### C. Label Drift
**What happened**: The definition of "correct" changed.
- *Example*: The company changed its refund policy, but the AI still uses the old rules.

### D. Upstream Data Pipeline Issues
**What happened**: A data source broke or changed format.
- *Example*: The CRM updated, and the "State" field now says "California" instead of "CA". The model doesn't recognize it.

## 3. The Alara Playbook

### Phase 1: Forensic Analysis (Days 1-3)
1.  **Time-Series Analysis**: Plot model accuracy by day/week. When exactly did it drop?
2.  **Input Distribution Comparison**: Compare input data from "3 months ago" vs. "today."
    - Are there new categories appearing?
    - Are value ranges different?
3.  **Error Pattern Analysis**: What *types* of errors are happening?
    - Random errors → Model quality issue.
    - Systematic errors (always wrong on X) → Data issue.

### Phase 2: Immediate Mitigation (Week 1)
1.  **Confidence Thresholding**: If the model's confidence score is <80%, route to human review automatically.
2.  **Rollback (if possible)**: If you have the old model version, temporarily revert while you investigate.
3.  **Circuit Breaker**: Set up alerts. If error rate > 20% in an hour, auto-disable the model.

### Phase 3: Long-Term Fix (Weeks 2-6)
**Option A: Retraining**
- Retrain the model on recent data (last 6 months, not 3 years ago).
- Schedule regular retraining (e.g., monthly).

**Option B: Online Learning**
- Implement continuous learning where the model updates daily based on human corrections.

**Option C: Ensemble Models**
- Run multiple models (an old one + a new one) and use a voting system.

## 4. Prevention System

### The "Model Health Dashboard"
We build a real-time monitoring system:
- **Accuracy by Segment**: Not just "overall accuracy," but accuracy by product type, geography, customer segment.
- **Drift Detection**: Statistical tests (Kolmogorov-Smirnov) to detect when input distributions shift.
- **Prediction Confidence**: Track average confidence scores. Sudden drops are red flags.

### The "Human Feedback Loop"
- When a human corrects an AI decision, log it.
- If corrections > 15% in a week, trigger a retraining review.

## 5. The "Gotchas"
- **Overfitting to Recent Data**: If you retrain only on the last month, you lose "memory" of rare events.
- **Seasonal Effects**: Retail sales spike in December. Don't retrain in January; your model will forget about holiday patterns.
- **The Silent Killer**: Sometimes accuracy only drops for a tiny segment (e.g., transactions in Japanese Yen), but that segment is super valuable.
