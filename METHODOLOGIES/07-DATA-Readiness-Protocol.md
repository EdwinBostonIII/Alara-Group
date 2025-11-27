# Methodology: Data Readiness Protocol

**Phase:** Pre-Implementation / Foundation
**Goal:** Ensure data is clean, accessible, legal, and sufficient before AI touches it.
**Duration:** 2-12 weeks (assessment) + 3-24 months (remediation, if needed)
**Critical Principle:** "Data preparation is 80% of AI project work. Rush it, regret it."

---

## 1. The "Garbage In, Garbage Out" Reality

**The Brutal Truth:**
- AI models are only as good as the data they access
- Most organizations have "Swamp Data": messy, duplicated, siloed, unlabeled, undocumented
- **70% of AI project failures are due to data issues, not algorithm issues** (Gartner)
- Data remediation is unglamorous, expensive, and time-consuming but non-negotiable

**Common Data Delusions:**
- ❌ "We have tons of data!" (Volume ≠ Quality)
- ❌ "It's all in our database." (Accessibility ≠ Availability)
- ❌ "We've been collecting it for years." (Age ≠ Relevance)
- ❌ "Our IT team handles data." (Stewardship ≠ Governance)

**Our Philosophy:**
We'd rather delay a project 6 months to fix data than launch a doomed initiative. We've turned down $500K+ engagements because the client's data wasn't ready and they wouldn't invest in remediation.

---

## 2. The Comprehensive Data Audit Framework

### Phase 1: Discovery (Weeks 1-2)

#### A. Data Landscape Mapping
**Objective:** Identify all data sources and repositories

**Inventory Template:**
| System Name | Type | Owner | Data Volume | Update Frequency | Integration Method | Criticality |
|-------------|------|-------|-------------|------------------|-------------------|-------------|
| Salesforce CRM | SaaS | Sales | 500K records | Real-time | REST API | High |
| Oracle ERP | On-prem DB | Finance | 50M transactions | Batch (nightly) | ODBC | Critical |
| SharePoint | Document repo | Multiple | 2TB docs | Real-time | Graph API | Medium |
| Excel Files | File shares | Varies | Unknown | Ad hoc | Manual | Low |

**Discovery Methods:**
1. **Interviews:** IT leadership, data engineers, business analysts
2. **Architecture Review:** System diagrams, data flow charts
3. **Shadow IT Detection:** Survey employees ("Where do you keep data?")
4. **Access Audit:** Which systems can talk to which systems?

**Red Flags:**
- "We're not sure where all our data is" (common in orgs with M&A history)
- Critical data still in legacy mainframe with no modern access layer
- "Excel files on network drives" as primary data repository
- No CMDB (Configuration Management Database) or data catalog exists

#### B. Structure Assessment
**Objective:** Classify data by structure type and AI readiness

**The Data Structure Spectrum:**

**1. Structured Data (AI-Ready with minimal prep):**
- **Examples:** SQL databases, CSV files, Excel (clean), API JSON
- **Characteristics:** Fixed schema, queryable, consistent formats
- **AI Use Cases:** Predictive modeling, classification, forecasting
- **Typical Issues:** Missing values, inconsistent coding, duplicates

**2. Semi-Structured Data (Moderate prep needed):**
- **Examples:** JSON, XML, HTML, logs, email (with metadata)
- **Characteristics:** Some organization, but flexible schema
- **AI Use Cases:** Log analysis, web scraping, email categorization
- **Typical Issues:** Schema variations, nested structures, parsing complexity

**3. Unstructured Data (Heavy prep or specialized AI needed):**
- **Examples:** PDFs, Word docs, images, audio, video, free-text
- **Characteristics:** No inherent structure, human-interpretable
- **AI Use Cases:** NLP (text), computer vision (images), speech-to-text (audio)
- **Typical Issues:** OCR errors, inconsistent formatting, context dependence

**Assessment Matrix:**
```
Data Source: Claims Forms (PDF)
├─ Structure Type: Unstructured (text) + Semi-structured (forms)
├─ Variability: High (10+ template versions over time)
├─ Quality Issues: Handwritten text (20%), poor scan quality (5%)
├─ Volume: 500K documents (2015-2024)
├─ Remediation Path: 
│  ├─ Option A: OCR + Template detection → Extract to JSON → $80K, 12 weeks
│  ├─ Option B: Manual data entry (outsource) → $200K, 20 weeks
│  └─ Option C: AI-first approach (use LLM to parse) → $40K, 6 weeks [RECOMMENDED]
```

#### C. Quality Audit
**Objective:** Measure data quality across 7 dimensions

**The "7 Pillars of Data Quality":**

**1. Completeness**
- **Metric:** % of required fields populated
- **Target:** >95% for critical fields, >80% for optional fields
- **Assessment Method:** SQL queries counting NULLs
- **Example Issue:** "Customer email" field is 40% NULL (can't do email outreach use case)

**2. Accuracy**
- **Metric:** % of records matching ground truth
- **Target:** >98% for high-stakes data (financial, medical)
- **Assessment Method:** Manual spot-checks (sample 100-500 records)
- **Example Issue:** Address data is 15% inaccurate (misspellings, outdated)

**3. Consistency**
- **Metric:** % of records following standardized formats
- **Target:** >95%
- **Assessment Method:** Regex pattern matching, value distributions
- **Example Issue:** Phone numbers in 8 different formats: (555) 123-4567, 555-123-4567, 5551234567, +1-555-123-4567, etc.

**4. Timeliness**
- **Metric:** Data lag (time from event to database record)
- **Target:** <24 hours for operational systems, <1 hour for real-time systems
- **Assessment Method:** Compare timestamp fields
- **Example Issue:** Sales data updated weekly, but sales team needs daily forecasts

**5. Uniqueness**
- **Metric:** Duplication rate
- **Target:** <2%
- **Assessment Method:** Fuzzy matching algorithms
- **Example Issue:** Same customer in system 3 times with slight name variations

**6. Validity**
- **Metric:** % of records within valid ranges/domains
- **Target:** >99%
- **Assessment Method:** Constraint checks, referential integrity tests
- **Example Issue:** Dates in future, negative ages, amounts exceeding max policy limit

**7. Lineage/Provenance**
- **Metric:** % of fields with documented source and transformation logic
- **Target:** 100% for regulated industries, >70% for others
- **Assessment Method:** Data dictionary review, interviews
- **Example Issue:** "Customer_Score" field exists, but no one knows how it's calculated

**Quality Scorecard Template:**
```
Data Source: Customer Database
┌────────────────┬────────┬────────┬──────────────────────┐
│ Dimension      │ Score  │ Target │ Gap                  │
├────────────────┼────────┼────────┼──────────────────────┤
│ Completeness   │ 72%    │ 95%    │ 23% - CRITICAL       │
│ Accuracy       │ 94%    │ 98%    │ 4% - Moderate        │
│ Consistency    │ 68%    │ 95%    │ 27% - CRITICAL       │
│ Timeliness     │ 100%   │ 95%    │ ✓ Exceeds            │
│ Uniqueness     │ 89%    │ 98%    │ 9% - Moderate        │
│ Validity       │ 99%    │ 99%    │ ✓ Meets              │
│ Lineage        │ 40%    │ 70%    │ 30% - CRITICAL       │
├────────────────┼────────┼────────┼──────────────────────┤
│ OVERALL        │ 80.3%  │ 92.9%  │ NOT READY FOR AI     │
└────────────────┴────────┴────────┴──────────────────────┘

Recommendation: 3-month Data Quality Sprint required before AI pilot
```

### Phase 2: Legal & Ethical Review (Weeks 2-3)

#### A. Consent & Privacy Audit
**Objective:** Ensure legal right to use data for AI

**The "Can We?" Checklist:**
- ✅ Do we have consent to use this data for automated decision-making?
- ✅ Does our privacy policy cover AI use cases?
- ✅ Have we completed a Privacy Impact Assessment (PIA)?
- ✅ Is data retention period defined and enforced?
- ✅ Can users request deletion? (GDPR "Right to be Forgotten")
- ✅ Do we have Data Processing Agreements (DPAs) with all vendors?

**Common Privacy Pitfalls:**
- **Re-identification Risk:** "Anonymous" data can often be de-anonymized
  - Example: Anonymized medical records + ZIP code + age + gender = 87% re-identifiable
- **Purpose Creep:** Data collected for one purpose, used for another
  - Example: Customer service transcripts used for AI training without consent
- **Third-Party Leakage:** Sending data to AI vendors (OpenAI, Google) without proper agreements
  - Solution: Enterprise agreements, private instances, or on-prem models

**Regulated Industry Requirements:**

**Healthcare (HIPAA):**
- ✅ Business Associate Agreement (BAA) with all AI vendors
- ✅ PHI encrypted at rest (AES-256) and in transit (TLS 1.3)
- ✅ Access controls (role-based, minimum necessary principle)
- ✅ Audit logs retained for 6 years
- ✅ De-identification via Safe Harbor or Expert Determination method

**Finance (GLBA, SOX):**
- ✅ Model Risk Management (SR 11-7 guidance)
- ✅ Algorithm transparency for credit decisions
- ✅ Adverse action notices (explain AI-driven denials)
- ✅ Annual model validation by independent party

**Defense (ITAR, CMMC):**
- ✅ Data residency (no foreign cloud regions)
- ✅ FedRAMP-authorized cloud services only
- ✅ Controlled Unclassified Information (CUI) markings enforced
- ✅ Foreign ownership restrictions on AI vendors

#### B. Bias & Fairness Analysis
**Objective:** Identify and mitigate discriminatory patterns in data

**Protected Attributes:** (Varies by jurisdiction, but commonly includes)
- Race/Ethnicity
- Gender
- Age
- Disability Status
- Religion
- National Origin
- Sexual Orientation

**Bias Detection Methods:**

**1. Direct Representation Analysis:**
- Are protected groups underrepresented or overrepresented?
- Example: Training data for hiring AI is 80% male resumes → model learns male bias

**2. Outcome Disparate Impact:**
- Do outcomes differ significantly by protected class?
- Legal Standard (US): If selection rate for protected group < 80% of highest group, it may violate Equal Employment Opportunity law
- Example: Loan approval AI approves 60% of white applicants, 40% of Black applicants → 40/60 = 66.7% < 80% threshold → FAIL

**3. Proxy Feature Detection:**
- Are there features highly correlated with protected attributes?
- Example: ZIP code is strong proxy for race; using it in model = indirect discrimination risk

**Mitigation Strategies:**
- **Fairness Constraints:** Force model to have equal error rates across groups
- **Re-sampling:** Balance training data across protected classes
- **Adversarial Debiasing:** Train model to make predictions independent of protected attributes
- **Human Oversight:** Require manual review for borderline decisions

**Case Study: Amazon Hiring AI (2018)**
- Trained on 10 years of resume data (mostly male candidates)
- Model learned to penalize resumes with "women's" keywords
- Result: Scrapped after 1 year of failed debiasing attempts
- Lesson: Biased data → biased AI, even with good intentions

### Phase 3: Integration & Access Analysis (Week 3)

#### A. API Maturity Assessment
**Objective:** Evaluate ease of data access for AI systems

**The API Maturity Model:**

**Level 0 - Manual Only:**
- Data requires manual export (SQL query, Excel download)
- No programmatic access
- **AI Feasibility:** RED (blocker)
- **Remediation:** Build basic REST API (3-6 months, $50K-$150K)

**Level 1 - Read-Only Batch:**
- Scheduled data dumps (nightly CSV files)
- No real-time access
- **AI Feasibility:** YELLOW (possible for batch ML, not real-time)
- **Use Cases:** Forecasting, historical analysis
- **Remediation:** Add real-time API (2-4 months, $30K-$80K)

**Level 2 - Read-Only API:**
- RESTful API with authentication
- Query data on-demand
- **AI Feasibility:** GREEN for most use cases
- **Limitation:** Can't write back (AI insights don't update source system)

**Level 3 - Full CRUD API:**
- Create, Read, Update, Delete capabilities
- **AI Feasibility:** GREEN (full bidirectional integration)
- **Use Cases:** AI updates records, triggers workflows

**Level 4 - Event-Driven Architecture:**
- Webhooks, message queues, streaming
- AI reacts to events in real-time
- **AI Feasibility:** GREEN (ideal for mission-critical systems)
- **Example:** Customer opens email → Event → AI personalizes next touchpoint

**Integration Complexity Score:**
```
System: Claims Processing Database
├─ API Maturity: Level 2 (Read-Only REST API)
├─ Authentication: OAuth 2.0 ✓
├─ Rate Limits: 1,000 requests/hour (may be insufficient at scale)
├─ Documentation: Swagger/OpenAPI ✓
├─ Latency: p95 = 250ms ✓
├─ Uptime SLA: 99.5% (8 hours downtime/year)
├─ Breaking Change History: 3 breaking changes in past year ⚠️
│
└─ Integration Risk: MODERATE
   Recommendation: Negotiate rate limit increase to 10K/hour before pilot
```

#### B. Data Warehouse/Lake Assessment
**Objective:** Evaluate centralized data infrastructure

**The Modern Data Stack:**
```
                    ┌─────────────────┐
                    │  BI & Analytics │
                    │  (Tableau, etc) │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │  Data Warehouse │
                    │ (Snowflake/BQ)  │◄───── AI Models query here
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │   Data Lake     │
                    │ (S3, Azure Blob)│
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
         ┌────▼───┐     ┌────▼───┐    ┌────▼───┐
         │ Source │     │ Source │    │ Source │
         │ System │     │ System │    │ System │
         │   #1   │     │   #2   │    │   #3   │
         └────────┘     └────────┘    └────────┘
```

**Maturity Assessment:**

**Scenario A: No Data Warehouse (40% of mid-market companies)**
- Data lives in source systems only
- Reporting = manual queries + Excel
- **AI Impact:** Every AI project becomes a data integration project
- **Remediation:** Build data warehouse (6-18 months, $200K-$1M)
- **Fast-Track Option:** Modern tools (Fivetran + Snowflake) can go live in 8-12 weeks

**Scenario B: On-Prem Data Warehouse (30% of enterprises)**
- SQL Server, Oracle, Teradata
- Limited scalability, high maintenance
- **AI Impact:** May lack compute for ML workloads
- **Remediation:** Cloud migration OR hybrid architecture

**Scenario C: Cloud Data Warehouse (20% of companies)**
- Snowflake, BigQuery, Redshift, Databricks
- Elastic compute, modern SQL
- **AI Impact:** IDEAL for most AI use cases
- **Optimization:** Tune for cost (queries can get expensive)

**Scenario D: Data Lake Only (10% of companies)**
- S3, Azure Data Lake, HDFS
- Raw files, no structure
- **AI Impact:** Need processing layer (Spark, Databricks) to use data
- **Remediation:** Add warehouse on top (Lakehouse architecture)

---

## 3. Remediation Strategies: "Clean House" vs. "Wrapper"

When data quality is insufficient, we have two philosophical approaches:

### Strategy A: The "Clean House" (Long-Term Foundation)
**Philosophy:** Fix the root cause. Build a proper data infrastructure.
**Timeline:** 6-18 months
**Investment:** $200K-$1M+
**Best For:** Organizations with multiple AI use cases planned, or where data quality impacts non-AI operations too

**The Playbook:**
1. **Months 1-3: Architecture & Tooling**
   - Select modern data stack (Fivetran + Snowflake + dbt, or equivalent)
   - Set up cloud infrastructure
   - Define data models and schemas

2. **Months 4-9: ETL Pipeline Build**
   - Connect source systems (start with 5-10 most critical)
   - Build transformation logic (dbt models)
   - Implement data quality monitoring (Great Expectations, Monte Carlo)

3. **Months 10-12: Governance & Rollout**
   - Data catalog (Alation, Collibra, or Atlan)
   - Access controls and permissions
   - Train business users on self-service analytics

4. **Months 13-18: Expansion**
   - Add remaining data sources
   - Advanced use cases (ML feature stores, real-time streams)
   - AI projects can now launch from clean foundation

**Pros:**
- ✅ Solves data problems for all use cases (AI and non-AI)
- ✅ Enables self-service analytics (not just AI team benefits)
- ✅ Scales to enterprise-wide AI strategy
- ✅ Attracts and retains top data talent (modern stack)

**Cons:**
- ❌ Expensive and time-consuming
- ❌ Requires executive buy-in and patience
- ❌ Risk of project stalling midway (18 months is a long commitment)
- ❌ AI benefits delayed

**When to Choose This Path:**
- C-suite has already identified "data quality" as strategic initiative
- Multiple departments want AI/analytics capabilities
- Current data infrastructure is 10+ years old
- Budget and timeline allow for foundational work

### Strategy B: The "Wrapper" (Short-Term Agile)
**Philosophy:** Build an AI layer that can handle messy data. Fix data "good enough" for the specific use case.
**Timeline:** 2-8 weeks
**Investment:** $20K-$80K
**Best For:** Urgent business need, pilot projects, proof-of-concept before committing to full remediation

**The Playbook:**
1. **Week 1: Scope Definition**
   - Identify minimum viable data (what data is absolutely necessary?)
   - Accept that data won't be perfect
   - Define "good enough" thresholds

2. **Weeks 2-3: Data Wrangling Pipeline**
   - **For PDFs:** OCR + LLM-based extraction (e.g., GPT-4 with vision)
   - **For Inconsistent Formats:** LLM normalization ("Clean this address to standard format")
   - **For Missing Data:** Imputation rules or AI-based inference
   - **For Duplicates:** Fuzzy matching + manual review queue

3. **Week 4-6: AI Integration**
   - Build data prep as part of AI pipeline (happens automatically)
   - User doesn't see the messy data, only clean AI outputs
   - Cache cleaned data (don't reprocess every time)

4. **Week 7-8: Testing & Iteration**
   - Spot-check quality (is cleaned data good enough?)
   - Tune extraction prompts based on errors
   - Deploy

**Example: Insurance Claims Form Processing**
```
Problem: 500K claim PDFs in 10 different formats, handwritten notes, poor scan quality

Traditional Approach (Clean House):
- Hire data entry team to manually re-key all forms
- Build standardized forms for future claims
- 12 months, $500K

Wrapper Approach:
- Use GPT-4 Vision to read PDFs and extract structured JSON
- Prompt: "Extract claim_number, incident_date, claimant_name, damage_description from this form. If handwritten, do your best. Output as JSON."
- Human review queue for low-confidence extractions (20% of cases)
- 6 weeks, $40K

Result: 80% auto-processed, 20% human-reviewed. Good enough to pilot AI claim assessment.
```

**Pros:**
- ✅ Fast to deploy (weeks, not months)
- ✅ Lower upfront cost
- ✅ Proves value before major investment
- ✅ Leverages modern AI's ability to handle messy inputs

**Cons:**
- ❌ Not scalable to dozens of use cases (each needs custom wrapper)
- ❌ Ongoing costs (AI processing of messy data is expensive)
- ❌ Doesn't fix underlying data problems
- ❌ May hit accuracy limits (garbage in, slightly-less-garbage out)

**When to Choose This Path:**
- Pilot project with tight deadline
- Single use case focus
- Uncertain if AI will provide ROI (de-risk with quick test)
- Plan to eventually do Clean House, but need quick win first

### Strategy C: Hybrid Approach (Pragmatic)
**Our Recommendation for Most Clients:**

**Phase 1 (Months 1-3): Wrapper for Pilot**
- Get AI use case live quickly with data wrappers
- Prove ROI and build momentum
- Identify which data sources are most problematic

**Phase 2 (Months 4-12): Selective Clean House**
- Invest in modernizing the 3-5 most critical data sources
- Leave edge cases with wrappers
- Build incrementally, not all at once

**Phase 3 (Year 2+): Continuous Improvement**
- Migrate additional systems as they become priorities
- Decommission wrappers as proper pipelines replace them
- Balance speed-to-value with long-term sustainability

---

## 4. Vector Databases & RAG for GenAI Use Cases

For Generative AI applications, we don't "train" models on client data (too expensive, too slow, data privacy concerns). We "ground" them using Retrieval Augmented Generation (RAG).

### The RAG Architecture
```
User Question: "What is our return policy for electronics?"
         ↓
[1. Vectorization]
   Convert question to numerical embedding (1,536 dimensions for OpenAI)
         ↓
[2. Similarity Search]
   Query vector database for most relevant document chunks
   Returns: Top 5 chunks from policy documents
         ↓
[3. Context Assembly]
   Combine retrieved chunks into single context
         ↓
[4. LLM Prompt]
   System: "You are a customer service assistant. Answer based on context."
   Context: [Retrieved policy chunks]
   User Question: "What is our return policy for electronics?"
         ↓
[5. LLM Response]
   "Per our policy document updated March 2024, electronics can be returned..."
```

### Document Processing Pipeline

**Step 1: Ingestion**
- Collect documents (PDFs, Word, HTML, plain text)
- Extract text (OCR for scanned documents)
- Typical volume: 1,000 - 100,000 documents

**Step 2: Chunking**
*Breaking documents into smaller pieces*

**Naive Chunking (Don't do this):**
- Every 500 tokens regardless of meaning
- Sentences cut mid-phrase
- Context lost

**Semantic Chunking (Better):**
- Chunk by sections/paragraphs (preserve meaning units)
- Size: 250-750 tokens per chunk
- Overlap: 50-100 tokens between chunks (preserves context at boundaries)

**Hybrid Chunking (Best):**
- Metadata-aware: Preserve document structure (headers, sections)
- Use AI to identify natural breakpoints
- Variable chunk size (key sections can be larger)

**Example:**
```
Document: Employee Handbook (50 pages)
├─ Chunk 1: "Vacation Policy - Section 3.2" (meta + content)
├─ Chunk 2: "Sick Leave Policy - Section 3.3"
├─ Chunk 3: "Remote Work Policy - Section 4.1"
...
└─ Chunk 47: "Termination Procedures - Section 12.5"

Each chunk stored with:
- Text content
- Source document
- Page number
- Section title
- Last updated date
```

**Step 3: Embedding**
- Convert each chunk to a vector (array of numbers)
- Model options:
  - OpenAI `text-embedding-3-large`: 3,072 dimensions, $0.13/M tokens
  - OpenAI `text-embedding-3-small`: 1,536 dimensions, $0.02/M tokens
  - Open source (sentence-transformers): Free, but need hosting
- Cost example: 10,000 chunks × 500 tokens avg = 5M tokens = $0.10 (small) to $0.65 (large)

**Step 4: Indexing in Vector Database**
- Store vectors + metadata
- Build index for fast similarity search (HNSW, IVF, or similar algorithm)

**Vector Database Options:**
| Option | Best For | Pricing Model | Performance |
|--------|----------|---------------|-------------|
| Pinecone | Simplicity, SaaS | $70/mo + usage | Excellent |
| Weaviate | Open-source, self-host | Infrastructure cost | Excellent |
| Qdrant | High performance | Open or Cloud | Excellent |
| pgvector | Postgres extension | Existing DB cost | Good |
| Chroma | Local/dev use | Free/infrastructure | Good |

**Step 5: Retrieval (at query time)**
- User asks question → Embed question → Search vector DB → Return top K chunks
- Typical K: 3-10 (more chunks = better context but higher LLM cost)

**Step 6: Re-Ranking (Optional but Recommended)**
- Initial retrieval is fast but approximate
- Re-rank results using cross-encoder model (more accurate but slower)
- Reduces K from 20 to 5 (keep only most relevant)

### RAG Quality Optimization

**Problem: Retrieval Returns Irrelevant Results**
**Symptoms:** AI says "I don't have information" when you know the data exists
**Fixes:**
1. Improve chunking (smaller, more focused chunks)
2. Add metadata filtering (e.g., "only search 2024 documents")
3. Tune similarity threshold (require higher match score)
4. Hybrid search (combine vector similarity + keyword matching)

**Problem: AI Still Hallucinates Despite RAG**
**Symptoms:** AI invents facts not in retrieved context
**Fixes:**
1. Strengthen system prompt: "ONLY use the provided context. Never add information not explicitly stated."
2. Citation requirement: "Include document name and page number for every claim."
3. Confidence scoring: "If confidence < 80%, say 'I'm not certain' instead of guessing."

**Problem: Too Slow (>10 seconds per query)**
**Fixes:**
1. Cache frequent queries (50% of queries are repeats in many use cases)
2. Reduce top_k (retrieve fewer chunks)
3. Use faster embedding model (small vs large)
4. Upgrade vector database infrastructure

### Data Governance for RAG Systems

**Access Control:**
- User A can only retrieve documents they have permission to see
- Implement row-level security in vector DB (filter by user_id)
- Audit log: Who searched what, when

**Data Freshness:**
- How often to re-index documents? (Daily? Weekly? On-update?)
- Version control: Track which version of a document was retrieved
- Expiration policy: Remove outdated documents from index

**Privacy:**
- PII in documents? Redact before embedding or filter from results
- Compliance: Ensure vector DB meets same standards as source systems (encryption, access logs, etc.)

---

## 5. Data Governance Roles & Responsibilities

**Why Governance Matters:**
- Without clear ownership, data quality degrades over time
- "Everyone's responsibility" = no one's responsibility
- AI amplifies bad data decisions (bad data → bad insights → bad business outcomes)

### The "RACI" Model for Data Governance

**Data Owner (Responsible)**
- **Who:** Business unit leader (VP of Sales, CMO, Head of Claims, etc.)
- **Role:** 
  - Defines what data means (business glossary)
  - Sets quality standards for their domain
  - Approves who can access data
  - Budget authority for data quality initiatives
- **Example:** CMO owns "Customer" data definition

**Data Steward (Accountable)**
- **Who:** Mid-level manager or senior analyst
- **Role:**
  - Day-to-day data quality monitoring
  - Enforces data standards
  - Triages data issues
  - Coordinates with IT on fixes
- **Example:** Marketing Ops Manager ensures CRM data stays clean

**Data Custodian (Consulted)**
- **Who:** IT/Engineering team
- **Role:**
  - Builds and maintains data systems
  - Implements access controls
  - Executes technical changes requested by owners/stewards
  - Ensures security and compliance
- **Example:** Data Engineer builds ETL pipeline for marketing data

**Data User (Informed)**
- **Who:** End users (analysts, data scientists, business users)
- **Role:**
  - Use data for analysis and decisions
  - Report data quality issues
  - Follow data usage policies
- **Example:** Analyst querying customer data for campaign

### Governance Framework Components

**1. Data Catalog**
- Searchable inventory of all data assets
- Includes: Table/field definitions, data lineage, quality metrics, ownership
- Tools: Alation, Collibra, Atlan, Apache Atlas (open source)

**2. Data Dictionary**
- Standardized definitions for business terms
- Example: "What is a 'Customer'? Someone who bought once? Signed up for newsletter? Visited website?"
- Resolves ambiguity (Sales and Marketing may define "Lead" differently)

**3. Data Quality Metrics**
- Automated quality checks (Great Expectations, dbt tests)
- Dashboard showing quality trends over time
- Alerts when quality drops below threshold

**4. Data Access Policy**
- Who can access what data?
- Classification levels: Public, Internal, Confidential, Restricted
- Principle of Least Privilege

**5. Data Retention & Deletion**
- How long to keep data?
- Legal requirements (SOX: 7 years for financial records)
- Privacy requirements (GDPR: Delete upon request)
- Practical considerations (storage costs)

### Example Governance Structure for AI Project

**Use Case:** Claims Processing AI

**Governance Committee:**
- **Sponsor:** VP of Claims (approves budget, sets priorities)
- **Data Owner:** Director of Claims Operations (defines "valid claim")
- **Data Steward:** Claims Data Manager (monitors quality daily)
- **AI Lead:** Alara Group engagement team (builds models, ensures ethics)
- **Legal Counsel:** (reviews for compliance)
- **InfoSec Rep:** (reviews for security)

**Cadence:**
- Weekly: Steward reviews quality metrics, flags issues
- Monthly: Committee reviews AI performance, user feedback, risks
- Quarterly: Executive briefing, strategic decisions

**Decision Rights:**
- Sponsor: Can halt AI system if business risk identified
- Data Owner: Can revoke data access if misuse detected
- AI Lead: Can pause model updates if quality degrades

---

## 6. Common Data Readiness Scenarios

### Scenario A: "We Have Tons of Data!" (But It's Useless)
**Signals:**
- Petabytes of log files, clickstream data, sensor data
- No structure or documentation
- "Data graveyard" - stored but never accessed

**Response:**
1. Identify high-value data subset (focus on 5% that matters)
2. Define specific use case first (don't boil the ocean)
3. Build minimum viable data pipeline for that use case
4. Ignore the rest for now

**Key Principle:** Volume without accessibility = liability, not asset

### Scenario B: "Our Data Is Perfect!" (Famous Last Words)
**Signals:**
- IT team insists everything is clean
- No recent quality audit
- "We haven't had complaints"

**Response:**
1. Trust but verify: Conduct independent quality assessment
2. Often discover: Data is clean for *current* use cases (reporting), not clean for AI
3. Example: Fields that humans interpret easily (abbreviations, shorthand) but AI struggles with

### Scenario C: "We Don't Have Any Data" (Usually False)
**Signals:**
- Startup or new initiative
- "We're data-driven but haven't collected anything yet"

**Response:**
1. Audit for hidden data: Emails, support tickets, surveys, financials
2. Third-party data purchase (if legal and ethical)
3. Data collection sprint (6-12 months before AI)
4. Synthetic data generation (for training, not production)

### Scenario D: "Data Is Spread Across 50 Systems" (Common in M&A)
**Signals:**
- Multiple acquisitions, each kept their own systems
- No master data management (MDM)
- Same customer in 5 different databases with 5 different IDs

**Response:**
1. MDM implementation (deduplicate, create golden records)
2. API layer to federate queries across systems (don't necessarily consolidate)
3. Or accept limitation: Start AI in one business unit with clean data

### Scenario E: "Legal Says We Can't Use Our Data for AI"
**Signals:**
- Strict consent language in current terms of service
- Collected data before AI use cases existed
- Risk-averse legal team

**Response:**
1. Re-consent campaign (ask users to opt-in to AI uses)
2. Anonymization or aggregation (use data in non-identifiable form)
3. Synthetic data (train on fake data that mimics real patterns)
4. Accept limitation and pivot to different data source

---

## 7. Data Readiness Checklist (Decision Tool)

Use this scorecard to determine if data is ready for AI:

| Criteria | RED (Stop) | YELLOW (Proceed with caution) | GREEN (Ready) |
|----------|-----------|-------------------------------|---------------|
| **Volume** | <1,000 samples | 1,000-10,000 samples | >10,000 samples |
| **Quality** | <70% complete/accurate | 70-90% | >90% |
| **Access** | Manual only | Batch API | Real-time API |
| **Legal** | No consent, high risk | Consent unclear | Clear consent & DPAs |
| **Structure** | Unstructured, messy | Semi-structured | Structured or clean |
| **Governance** | No ownership | Informal ownership | Clear RACI |
| **Freshness** | >1 month lag | 1 day - 1 month lag | <1 day lag |

**Scoring:**
- 5+ RED: STOP. Fix data before any AI work.
- 3-4 RED: Scoped remediation (3-6 months), then pilot.
- 0-2 RED, 3+ YELLOW: Agile pilot with "wrapper" approach.
- All GREEN: Proceed to pilot immediately.

---

## 8. Why Data Readiness Matters (ROI Perspective)

**Case Study: Failed AI Project Due to Bad Data**
- **Company:** Mid-size healthcare provider
- **Use Case:** Predict patient no-shows to optimize scheduling
- **Data Issue:** Appointment cancellations not recorded consistently (20% missing)
- **Result:** Model trained on biased data, predicted no-shows incorrectly, overbooking chaos
- **Cost:** $300K spent on AI development, $0 ROI, project scrapped
- **Lesson:** $50K data remediation upfront would have saved $300K failure

**Case Study: Successful AI Project With Proper Data Prep**
- **Company:** Insurance carrier (auto)
- **Use Case:** Fraud detection
- **Data Prep:** 6 months cleaning historical claims data, removing duplicates, standardizing codes
- **Investment:** $150K in data work
- **Result:** 92% accurate fraud detection, $8M annual savings
- **ROI:** 53x return in Year 1

**The Bottom Line:**
- Good data = AI success is likely
- Bad data = AI failure is certain
- Data readiness is not optional, it's foundational
