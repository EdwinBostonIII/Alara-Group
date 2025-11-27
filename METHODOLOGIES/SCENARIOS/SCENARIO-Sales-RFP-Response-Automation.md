# Scenario: RFP Response Automation (Sales)

**Category:** Sales / Operations
**Trigger:** The Sales Engineering team is drowning in RFPs (Requests for Proposals). They spend 20 hours answering the same security questionnaires over and over, missing opportunities to pitch new deals.

---

## 1. The Situation
RFPs are repetitive. "Do you have SOC2?" "How do you handle data encryption?" The answers exist in previous RFPs, but they are scattered across Sharepoint and Google Drive.

## 2. The Diagnosis
This is a "Knowledge Retrieval" problem. The knowledge exists, but the retrieval latency is high (searching through folders).

## 3. The Alara Playbook

### Phase 1: The Knowledge Base Assembly (Week 1-2)
1.  **Data Gathering**: Collect the last 50 completed RFPs, the Security Whitepaper, and the Technical Specs.
2.  **Cleaning**: Remove "Client Specific" data (e.g., "We offer you, Acme Corp, a 10% discount"). We want only the reusable facts.
3.  **Chunking**: Break the Q&A pairs into a database.

### Phase 2: The RAG Agent (Week 3-4)
1.  **The "RFP Bot"**: A tool where a salesperson pastes a question from a new RFP.
    - *Input*: "Describe your disaster recovery plan."
    - *AI Action*: Searches the database for the best previous answer. Checks if it's up to date.
    - *Output*: "Here is our standard DR answer. Last updated: Jan 2025."
2.  **Auto-Fill**: For Excel-based RFPs, we build a script to iterate through rows and suggest answers automatically.

### Phase 3: The Feedback Loop
1.  **The "Stale Data" Flag**: If an answer is >6 months old, the AI flags it for review by a Subject Matter Expert (SME).
2.  **New Q&A**: When a human writes a *new* answer to a *new* question, it is automatically added to the database for next time.

## 4. The "Gotchas"
- **The "Yes" Trap**: The AI might answer "Yes" to a requirement we don't meet because it saw "Yes" in a different context.
- **Formatting Nightmares**: RFPs come in terrible formats (merged cells in Excel). The ingestion pipeline needs to be robust.
