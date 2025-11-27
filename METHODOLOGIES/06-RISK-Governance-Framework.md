# Methodology: AI Governance & Risk Framework

**Phase:** Strategy / Ongoing
**Goal:** Protect the organization from legal, reputational, and operational risk.

---

## 1. The Three Lines of Defense

We implement a standard risk management structure adapted for AI.

1.  **First Line (Development Teams)**: Responsible for testing bias, security, and accuracy *during* build.
2.  **Second Line (Risk/Compliance)**: Sets the policies and reviews high-risk models before deployment.
3.  **Third Line (Audit)**: Periodically audits the entire system to ensure policies are followed.

## 2. The AI Policy Template (What we customize for clients)

### A. Acceptable Use
- **Public AI (ChatGPT, Claude)**: Never put PII, IP, or code into public, free versions. Use Enterprise versions only.
- **Shadow AI**: Employees cannot purchase AI tools on credit cards without IT review.

### B. Data Privacy
- **Training Data**: Client data must not be used to train vendor models (unless explicitly agreed).
- **Data Residency**: Data must stay within specific geographies (EU/US) for compliance.

### C. Transparency
- **Disclosure**: If a customer is chatting with an AI, it must identify itself as an AI immediately.
- **Explainability**: For high-stakes decisions (loans, hiring, insurance), we must be able to explain *why* the model made the decision.

## 3. Risk Assessment Protocol (The "Traffic Light" System)

Every proposed AI use case is categorized:

**🔴 RED (Prohibited / High Scrutiny)**
- Facial recognition for surveillance.
- Automated hiring/firing decisions without human review.
- Social scoring.
*Action: Requires Board-level approval or is banned.*

**🟡 YELLOW (High Risk - Managed)**
- Credit underwriting.
- Medical diagnosis support.
- Legal contract review.
*Action: Requires "Human-in-the-Loop", rigorous testing, and ongoing monitoring.*

**🟢 GREEN (Low Risk)**
- Internal knowledge search.
- Marketing copy drafting.
- Meeting summarization.
*Action: Fast-track approval with standard security checks.*

## 4. Crisis Response Plan (What to do when it goes wrong)

**Scenario**: The chatbot swears at a customer or promises a refund it shouldn't.
1.  **Kill Switch**: Immediate ability to take the bot offline and revert to human support.
2.  **Incident Log**: Document exactly what prompt caused the error.
3.  **Communication**: Template apology for PR/Customer Service.
4.  **Remediation**: Update the system prompt (instructions) to explicitly forbid the behavior and add regression tests.
