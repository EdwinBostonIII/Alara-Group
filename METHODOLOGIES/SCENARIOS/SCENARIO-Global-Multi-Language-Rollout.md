# Scenario: Multi-Language Global Rollout

**Category:** Technical / Localization / Strategy
**Trigger:** A successful English-language AI chatbot or document processor needs to work in Spanish, Mandarin, Arabic, and French to support global operations.

---

## 1. The Situation
The US division loves the AI. Now the CEO wants it deployed in EMEA and APAC offices. But a naive translation breaks everything because language isn't just words; it's culture, idioms, and data formats.

## 2. The Diagnosis (What Makes This Hard)

### A. Language Models Have Bias
- GPT-4 is strongest in English. Its Spanish is good. Its Tagalog is mediocre.
- Open-source models (Llama, Mistral) often perform poorly in non-European languages.

### B. Cultural Context
- *Example*: A German customer expects formal "Sie," not informal "du."
- *Example*: Arabic reads right-to-left. UI design breaks.
- *Example*: Date formats: US (MM/DD/YYYY) vs. EU (DD/MM/YYYY).

### C. Data Availability
- If your training data or RAG documents are English-only, translating the UI doesn't help.

## 3. The Alara Playbook

### Phase 1: Language Prioritization (Week 1)
Don't launch all languages at once. Prioritize:
1.  **Transaction Volume**: Which languages represent the most customers?
2.  **Complexity**: Romance languages (Spanish, French, Italian) are easier than tonal languages (Mandarin).
3.  **Risk Tolerance**: Launch in a "low-stakes" language first (internal tool, not customer-facing).

### Phase 2: Model Selection (Week 2-4)
**Option A: Multilingual LLM**
- Use GPT-4 or Claude (both handle 50+ languages).
- Test the target language extensively. Measure accuracy.

**Option B: Specialized Models**
- For Chinese: Use Alibaba's Qwen or Baidu's ERNIE.
- For Arabic: Fine-tune on Arabic-specific data.

**Option C: Translation Layer**
- Translate input to English → Process → Translate output back.
- *Warning*: Loses nuance. Use only if accuracy isn't critical.

### Phase 3: Localization, Not Just Translation (Month 2)
1.  **Prompt Localization**: The system prompt must be culturally appropriate.
    - *English*: "Please describe the issue."
    - *Japanese*: More formal, hierarchical tone.
2.  **Data Localization**: Your knowledge base must exist in each language.
    - Machine translate docs → Human review → Load into vector DB.
3.  **UI Localization**: Buttons, error messages, date pickers.

### Phase 4: Testing & QA (Month 3)
1.  **Native Speaker Testing**: Never rely solely on engineers. Hire local testers.
2.  **Edge Cases**:
    - Right-to-left languages (Arabic, Hebrew).
    - Emoji usage (common in Asia, rare in Germany).
    - Currency and number formats.
3.  **Offensive Content Check**: Words that are fine in English might be slurs in another language.

## 4. The ROI Calculation
Don't assume "more languages = more revenue."
- **Cost**: Each language adds 20-30% dev time and ongoing maintenance.
- **Benefit**: Only valuable if you actually have customers in that market.

**Decision Matrix**:
| Language | Customer % | Dev Cost | Priority |
|----------|-----------|----------|----------|
| Spanish  | 25%       | Medium   | High     |
| Mandarin | 15%       | High     | Medium   |
| German   | 5%        | Medium   | Low      |

## 5. The "Gotchas"
- **The "Spanglish" Trap**: US Hispanic customers often code-switch. The model must handle mixed-language input.
- **Legal Compliance**: EU AI Act requires transparency in all official EU languages (24 languages).
- **The "Google Translate" Smell**: Users can tell when content is machine-translated. It destroys trust.
