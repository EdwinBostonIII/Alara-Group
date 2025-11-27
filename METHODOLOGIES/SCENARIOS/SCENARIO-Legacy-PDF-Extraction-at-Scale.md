# Scenario: Legacy PDF Extraction at Scale

**Category:** Technical / Data Engineering
**Trigger:** An insurance company or law firm has 5 million scanned PDF pages (claims, contracts, blueprints) on a shared drive. They need to query this data but can't because it's "dead pixels".

---

## 1. The Situation
The client wants to ask: "How many claims in 2010 involved water damage in Florida?"
The answer is in the files, but the files are scanned images of paper documents. Traditional OCR (Optical Character Recognition) is 80% accurate but fails on handwriting or complex tables.

## 2. The Diagnosis
Standard OCR reads text line-by-line. It loses context. It reads a table row as a jumbled sentence. It cannot understand that a checkmark in a box means "Yes".

## 3. The Alara Playbook

### Phase 1: The Pipeline Build (Week 1-2)
1.  **Vision-Language Models (VLM)**: We don't use simple OCR. We use models like GPT-4o or Claude 3.5 Sonnet which can "see" the page.
2.  **Preprocessing**:
    - *De-skewing*: Straightening crooked scans.
    - *Denoising*: Removing coffee stains/scan lines.

### Phase 2: Structured Extraction (Week 3-6)
1.  **Schema Definition**: Define the JSON output we want.
    - `{ "claim_id": "123", "damage_type": "water", "amount": 5000.00 }`
2.  **Batch Processing**: Run the 5 million pages through the pipeline.
3.  **Confidence Scoring**: The AI assigns a confidence score to each extraction.
    - *Score > 95%*: Auto-save to database.
    - *Score < 95%*: Send to "Human Review Queue".

### Phase 3: The "Chat with Data" Interface (Month 2)
1.  **Vector Indexing**: Load the extracted JSON and text into a Vector Database.
2.  **RAG Interface**: Build a chat tool where analysts can ask questions in plain English.

## 4. The "Gotchas"
- **Cost**: Processing 5 million pages with GPT-4 is expensive ($50k+). We optimize by using cheaper models for simple pages and expensive models only for complex handwritten forms.
- **Hallucination**: The AI might "invent" a number if the scan is blurry. We enforce "Null" outputs if the text is unreadable.
