# Industry Playbook: Insurance

**Focus Areas**: P&C (Property & Casualty), Life, Health.

---

## 1. High-Value Use Cases

### A. Underwriting Assistant (The "Bionic Underwriter")
- **Problem**: Underwriters spend 70% of time gathering data from PDFs, emails, and spreadsheets.
- **Solution**: AI extracts data from submissions, flags risks (e.g., "Building is in a flood zone"), and drafts a risk memo.
- **Methodology**:
    - Use OCR + LLM to parse unstructured submissions.
    - Human underwriter makes the final decision (Compliance requirement).
    - **ROI**: 40% reduction in time-to-quote.

### B. Claims Triage & Processing
- **Problem**: Claims intake is slow; simple claims get stuck behind complex ones.
- **Solution**: AI analyzes First Notice of Loss (FNOL).
    - *Simple (Windshield crack)*: Auto-approve or fast-track.
    - *Complex (Bodily injury)*: Route to senior adjuster immediately.
    - *Suspicious*: Flag for SIU (Fraud unit).
- **Risk**: Bias in fraud detection. Requires rigorous fairness testing.

### C. Policyholder Service
- **Problem**: Call centers overwhelmed during catastrophe events.
- **Solution**: Voice AI or Chatbot handles "What is my deductible?" and "Status of my claim?" queries.

## 2. Regulatory Considerations (NAIC / State DOI)

- **Explainability**: If AI denies a claim or rates a policy higher, we must provide the specific reason (e.g., "Roof age > 20 years"). "The model said so" is not a legal defense.
- **Data Privacy**: Strict handling of PII.

## 3. Implementation Roadmap

1.  **Month 1-2**: Data cleanup. Digitizing paper files.
2.  **Month 3-4**: Pilot "Underwriting Assistant" with 5 senior underwriters.
3.  **Month 5**: Refine based on feedback.
4.  **Month 6**: Roll out to department.

## 4. Common Objections & Rebuttals

**Objection**: "AI can't replace the intuition of a 30-year underwriter."
**Rebuttal**: "Agreed. We don't want to replace intuition. We want to remove the data entry so the underwriter has *more* time to use their intuition on the complex risks."
