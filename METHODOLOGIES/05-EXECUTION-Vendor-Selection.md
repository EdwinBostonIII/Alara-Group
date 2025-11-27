# Methodology: Vendor Selection Matrix

**Phase:** Strategy / Procurement
**Goal:** Choose the right tool without getting locked in or ripped off.

---

## 1. The "Build vs. Buy" Decision

**BUY (SaaS)** if:
- It's a commodity function (e.g., HR chatbot, Meeting recorder).
- Speed is critical.
- You don't have engineering talent.

**BUILD (Custom/Wrapper)** if:
- It's your core competitive advantage.
- You have unique, sensitive data.
- You need total control over the model/security.

## 2. The Vetting Framework (The "Alara 10")

Ask these 10 questions to every AI vendor:

1.  **Data Usage**: "Do you use our data to train your models?" (Answer must be NO for enterprise).
2.  **Model Ownership**: "If we leave, do we keep the fine-tuned model?"
3.  **Hallucination Rate**: "How do you measure and mitigate accuracy errors?"
4.  **Security**: "Are you SOC2 Type II compliant?"
5.  **Interoperability**: "Do you have an open API?"
6.  **Pricing Model**: "Is it per-seat, per-token, or flat fee?" (Beware token-based pricing for high volume).
7.  **Dependency**: "Which underlying model do you use? (GPT-4, Claude, Llama) Can we switch?"
8.  **Liability**: "Do you indemnify us against IP copyright claims?"
9.  **Roadmap**: "What features are coming in 6 months?"
10. **References**: "Let me talk to a client in my industry."

## 3. The Scoring Matrix

Create a spreadsheet with these columns:
- **Functional Fit** (40%)
- **Security/Compliance** (30%)
- **Cost** (20%)
- **Ease of Use** (10%)

## 4. Red Flags

- Vendor cannot explain how their AI works ("It's magic").
- Vendor claims "100% accuracy".
- Vendor has no API.
- Vendor is 2 people in a garage (Risk of going bust).

## 5. Contract Negotiation Tips

- **Opt-Out**: Ensure a clause explicitly opting out of data training.
- **Cap Increases**: Cap annual price increases (AI costs are dropping, software shouldn't skyrocket).
- **Exit Strategy**: Ensure you can export your data easily.
