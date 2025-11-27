# Scenario: Prompt Engineering Best Practices

**Category:** Technical / Best Practices / Training
**Trigger:** Users are frustrated with GenAI tools. They get mediocre results, blame "the AI," and abandon it. The real problem: they don't know how to write effective prompts.

---

## 1. The Situation
An employee types into ChatGPT: "Write a marketing email."
The AI produces generic nonsense about "synergy" and "innovative solutions."
The employee concludes: "AI is useless for my work."

**Reality**: The prompt was terrible. The AI had zero context.

## 2. The Diagnosis
**Garbage Prompt In, Garbage Answer Out**: LLMs are incredibly powerful but they require specific, structured instructions to produce useful output.

## 3. The Alara Prompt Framework: "C.R.I.S.P."

### C - Context
Give the AI background information.

**Bad**: "Write a report."
**Good**: "I am a product manager at a B2B SaaS company. I need to write a quarterly business review for our CEO. Our product is a CRM tool."

### R - Role
Tell the AI what persona to adopt.

**Bad**: (No role specified)
**Good**: "Act as a senior marketing strategist with 15 years of experience in healthcare."

### I - Instruction
Be explicit about what you want.

**Bad**: "Help me with this."
**Good**: "Analyze this customer interview transcript. Extract: (1) pain points mentioned, (2) feature requests, (3) sentiment (positive/negative/neutral)."

### S - Structure
Specify the output format.

**Bad**: (No format specified)
**Good**: "Present your findings in a bulleted list. Use bold for key terms. Limit to 200 words."

### P - Polish
Iterate and refine.

**Bad**: Accept the first response.
**Good**: "This is good, but too formal. Rewrite it in a conversational tone. Add one specific example."

## 4. The Prompt Library (Examples by Use Case)

### Legal Contract Review
```
Role: You are a corporate attorney specializing in SaaS contracts.

Context: I am reviewing a Master Services Agreement (MSA) from a new vendor. 
Our company policy prohibits unlimited liability, requires Delaware governing law, 
and caps payment terms at Net 45.

Instruction: Review the attached contract and identify:
1. Clauses that violate our policies
2. Missing clauses we typically require (e.g., termination for convenience)
3. Ambiguous language that needs clarification

Structure: Use a table with columns: Clause, Issue, Recommendation.
```

### Marketing Content Generation
```
Role: You are a B2B copywriter specializing in financial services.

Context: We are launching a new fraud detection product targeted at mid-size banks 
(assets $1B-$10B). Our key differentiator is real-time detection with 50% fewer 
false positives than competitors.

Instruction: Write a 150-word website hero section that:
- Leads with a pain point (false positives costing banks millions)
- Introduces our solution
- Ends with a clear CTA (Request Demo)

Tone: Professional but not stuffy. Think "Wall Street Journal," not academic paper.

Constraints: Avoid jargon like "AI-powered" or "next-gen." Be specific.
```

### Data Analysis
```
Role: You are a business analyst specializing in retail.

Context: I have a CSV file with 50,000 transactions from our e-commerce site. 
Columns: date, product_id, category, revenue, customer_id, discount_used.

Instruction: Analyze the data and answer:
1. What are the top 5 products by revenue?
2. What % of transactions used a discount?
3. Is there a correlation between discounts and customer repeat purchase rate?

Structure: Start with a 3-sentence executive summary, then detailed findings with 
charts (describe the chart if you can't generate it).
```

### Code Generation
```
Role: You are a senior Python developer with expertise in data processing.

Context: I have a directory with 1,000 PDF files. Each file is a scanned invoice. 
I need to extract: invoice number, date, total amount, vendor name.

Instruction: Write a Python script that:
1. Uses OCR (tesseract or an API) to extract text
2. Uses regex or an LLM to parse structured data
3. Outputs a CSV file with all extracted data
4. Includes error handling for corrupted PDFs

Constraints: Prioritize readability over performance. Add comments. Use type hints.
```

## 5. Advanced Techniques

### Chain-of-Thought Prompting
For complex reasoning tasks, ask the AI to "think step by step."

**Example**:
```
I have $10,000 to invest. I'm 30 years old, moderate risk tolerance. 
Should I invest in stocks, bonds, or real estate?

Think step by step:
1. First, analyze my age and risk tolerance.
2. Then, compare expected returns of each option.
3. Then, consider liquidity needs.
4. Finally, make a recommendation with reasoning.
```

### Few-Shot Learning
Show the AI 2-3 examples of what "good" looks like.

**Example**:
```
I need you to categorize customer support tickets.

Examples:
Input: "My payment didn't go through"
Output: Category: Billing, Urgency: High

Input: "How do I reset my password?"
Output: Category: Technical, Urgency: Low

Now categorize these:
1. "The app keeps crashing when I upload files"
2. "I was charged twice for my subscription"
```

### Negative Prompting
Tell the AI what NOT to do.

**Example**:
```
Write a cold outreach email to a potential client.

DO NOT:
- Use phrases like "I hope this email finds you well"
- Write more than 100 words
- Mention pricing (that's for the next conversation)
```

## 6. The "Prompt Engineering" Training Program

### Level 1: Basics (1 Hour)
- Teach C.R.I.S.P. framework
- Show 5 before/after prompt examples
- Let them practice with their own use cases

### Level 2: Advanced (Half Day)
- Chain-of-thought reasoning
- Few-shot learning
- Multi-turn conversations (building context over multiple messages)

### Level 3: Custom GPTs (Full Day)
- How to build a custom GPT with pre-loaded instructions
- Creating a company-specific "Prompt Library"
- Integrating external data sources (RAG)

## 7. The Prompt Library System
We build a shared repository (Notion, Confluence, SharePoint):

```
├── Sales Prompts
│   ├── Cold Email Generator
│   ├── Meeting Prep Assistant
│   └── Objection Handler
├── Legal Prompts
│   ├── Contract Review Checklist
│   └── NDA Red-Liner
├── HR Prompts
│   ├── Job Description Writer
│   └── Interview Question Generator
└── Engineering Prompts
    ├── Code Reviewer
    └── Bug Report Summarizer
```

Each prompt includes:
- **Template**: The reusable prompt text
- **Instructions**: How to customize it
- **Example Output**: What good results look like

## 8. Measuring Success
**Before Training**: Track prompt quality (manually review a sample).
**After Training**: Users should see:
- 50% reduction in "retry" attempts (first prompt works)
- Higher satisfaction scores with AI output
- Increased daily active users of AI tools

## 9. The "Gotchas"
- **Over-Prompting**: 1,000-word prompts are usually worse than 200-word crisp ones. The AI gets confused.
- **The Template Trap**: If everyone uses the exact same prompt, all output sounds identical (no creativity).
- **Hallucination Blindness**: Better prompts don't eliminate hallucinations. Always verify facts.
