# Scenario: Marketing Brand Voice Consistency

**Category:** Marketing / Content
**Trigger:** The CMO is rejecting AI-generated content because "It sounds like a robot" or "It doesn't sound like *us*." The marketing team is secretly using ChatGPT anyway, resulting in a schizophrenic brand voice.

---

## 1. The Situation
The company wants to scale content production (blogs, social, emails) 10x using AI. But the output is generic, uses words like "delve" and "tapestry," and lacks the brand's specific wit or authority.

## 2. The Diagnosis
Standard models (GPT-4) have a "default voice" which is polite but bland. They haven't been "grounded" in the brand's specific style guide.

## 3. The Alara Playbook

### Phase 1: The Style Extraction (Week 1)
1.  **Corpus Analysis**: We take the brand's top 50 performing pieces of content (whitepapers, best blogs).
2.  **Voice Definition**: We use AI to analyze the AI. "Analyze these texts and define the tone, sentence structure, and vocabulary."
    - *Result*: "The voice is authoritative but conversational. Uses short sentences. Avoids jargon. Never uses the passive voice."

### Phase 2: The "Brand GPT" (Week 2-3)
1.  **Custom Instructions**: We build a custom GPT or system prompt that includes:
    - The Voice Definition.
    - A "Negative Constraints" list (Words to never use).
    - Few-Shot Examples (Show the AI 3 examples of "Good" vs "Bad" rewrites).

### Phase 3: The Workflow Integration
1.  **The "Remix" Pattern**: Don't ask AI to write from scratch. Ask humans to write bullet points, and AI to "Draft in our Brand Voice."
2.  **The "Editor" Bot**: A separate AI agent that critiques content *before* a human sees it. "This paragraph is too passive. Rewrite it."

## 4. The "Gotchas"
- **Over-fitting**: The AI tries too hard to be "witty" and becomes cringe-worthy. We need to dial back the "temperature" (creativity) setting.
- **Fact Checking**: The AI writes a beautiful, on-brand blog post about a product feature that doesn't exist. Human review for *facts* is mandatory.
