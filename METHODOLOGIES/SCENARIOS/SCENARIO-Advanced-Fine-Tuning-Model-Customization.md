# Scenario: Fine-Tuning & Model Customization

**Category:** Technical / Data Science / MLOps
**Trigger:** Generic pre-trained models (GPT-4, Claude) aren't accurate enough for the client's specific domain (legal jargon, medical terminology, internal company processes). They need a custom model.

---

## 1. The Situation
**Example Problems**:
- Legal AI keeps hallucinating case law that doesn't exist.
- Medical AI doesn't recognize abbreviations used in this hospital's EHR.
- Customer support AI doesn't understand company-specific product names.
- Code completion AI doesn't follow the company's coding standards.

**The Solution**: Fine-tune or train a custom model on domain-specific data.

## 2. The Diagnosis: When to Fine-Tune vs. Other Approaches

| Problem | Solution | Cost | Complexity |
|---------|----------|------|------------|
| Model doesn't know my data | RAG (Retrieval) | Low | Low |
| Model needs better prompts | Prompt engineering | Very Low | Very Low |
| Model needs specific format | Few-shot learning | Low | Low |
| Model needs domain expertise | Fine-tuning | Medium | Medium |
| Model needs new capabilities | Pre-training from scratch | Very High | Very High |

**Decision Tree**:
1.  Try prompt engineering first (cheapest).
2.  If that fails, add RAG (retrieval from your docs).
3.  If still insufficient, fine-tune.
4.  Only train from scratch if you have $1M+ budget and massive proprietary data.

## 3. The Alara Playbook

### Phase 1: Data Collection & Preparation (Week 1-4)

#### Step 1: Gather Training Data
You need **high-quality examples** of:
- **Inputs**: What users ask or what the model sees.
- **Outputs**: The "gold standard" correct response.

**Minimum Dataset Size**:
- GPT-3.5/4 fine-tuning: 50-500 examples (small, specific tasks).
- Open-source model fine-tuning: 1,000-10,000 examples (more robust).
- Full pre-training: 1M+ examples (almost never necessary).

**Data Sources**:
- Historical logs (if you have an existing system).
- Expert labeling (hire domain experts to create examples).
- Synthetic data (use GPT-4 to generate training data).

#### Step 2: Format the Data
**OpenAI Fine-Tuning Format** (JSONL):
```jsonl
{"messages": [{"role": "system", "content": "You are a legal assistant."}, {"role": "user", "content": "Summarize this contract."}, {"role": "assistant", "content": "This is a 5-year lease..."}]}
{"messages": [{"role": "system", "content": "You are a legal assistant."}, {"role": "user", "content": "What is force majeure?"}, {"role": "assistant", "content": "Force majeure is a clause..."}]}
```

**For Open-Source Models** (Instruction Format):
```json
[
  {
    "instruction": "Summarize this medical note.",
    "input": "Patient presents with chest pain...",
    "output": "Patient is a 55yo male with acute chest pain..."
  }
]
```

#### Step 3: Data Cleaning & Quality Control
**Red Flags**:
- Duplicate examples (model overfits).
- Inconsistent formatting.
- Incorrect labels (teach the model bad habits).
- PII in training data (privacy violation).

**Cleaning Process**:
- Deduplicate.
- Anonymize PII (replace names with [PERSON], dates with [DATE]).
- Have 2-3 experts review a sample for quality.

### Phase 2: Model Selection & Fine-Tuning (Week 5-8)

#### Option A: Fine-Tune a Proprietary Model (OpenAI, Anthropic)
**OpenAI Fine-Tuning**:
1.  Upload training file via API.
2.  Start fine-tuning job (takes 1-3 hours).
3.  Get a custom model ID (e.g., `ft:gpt-3.5-turbo:company:model:abc123`).
4.  Use it like any other model, but with your custom behavior.

**Cost**:
- Training: $0.008 per 1K tokens.
- Inference: 2-8x more expensive than base model.

**Pros**: Easy, no infrastructure.
**Cons**: Expensive at scale, vendor lock-in.

#### Option B: Fine-Tune an Open-Source Model (Llama, Mistral)
**Popular Models**:
- Llama 3 8B/70B (Meta)
- Mistral 7B (Mistral AI)
- Falcon 40B (TII)

**Process**:
1.  Download pre-trained weights from Hugging Face.
2.  Use LoRA (Low-Rank Adaptation) or QLoRA for parameter-efficient fine-tuning.
3.  Train on your data (requires GPUs: A100, H100).
4.  Save the adapter weights.
5.  Deploy via Ollama, vLLM, or TGI (Text Generation Inference).

**Cost**:
- Training: $50-500 (depending on GPU hours).
- Inference: $0.001-0.01 per 1K tokens (self-hosted).

**Pros**: Full control, cheap at scale.
**Cons**: Requires ML expertise, infrastructure management.

### Phase 3: Evaluation & Testing (Week 9-10)

#### Metric A: Accuracy
Test on a held-out validation set (10-20% of your data).
- **Exact Match**: Output matches gold standard exactly.
- **BLEU/ROUGE**: Similarity to reference (for text generation).
- **F1 Score**: For classification tasks.

#### Metric B: Human Evaluation
Have domain experts review 50-100 model outputs:
- Is it correct?
- Is it helpful?
- Would you trust this in production?

#### Metric C: Comparative Testing
Run the same queries through:
1.  Base model (GPT-4).
2.  Fine-tuned model.
3.  Side-by-side comparison.

**Question**: Is fine-tuning worth the cost?

### Phase 4: Deployment & Monitoring (Week 11+)

#### Deployment Options
**Cloud**:
- OpenAI API (fine-tuned model).
- AWS SageMaker, Azure ML, GCP Vertex AI.

**Self-Hosted**:
- Docker container with vLLM.
- Kubernetes cluster for auto-scaling.

#### Monitoring
Track:
- **Accuracy drift**: Is performance degrading over time?
- **Latency**: Response time.
- **Cost**: $/1K tokens.
- **User feedback**: Thumbs up/down on outputs.

**Re-training Cadence**:
- Every 3-6 months with new data.
- Or trigger-based (if accuracy drops below threshold).

## 4. Advanced Techniques

### Technique A: LoRA (Low-Rank Adaptation)
**Problem**: Fine-tuning a 70B parameter model is expensive (requires 280GB VRAM).

**Solution**: Only train a small "adapter" layer (1% of parameters).
- Base model stays frozen.
- Adapter learns task-specific behavior.
- Saves 90% of memory and compute.

### Technique B: QLoRA (Quantized LoRA)
**Problem**: Even LoRA requires expensive GPUs.

**Solution**: Quantize the model to 4-bit precision.
- Fits 70B model on 24GB GPU (consumer-grade RTX 4090).
- Slight accuracy loss (<2%).

### Technique C: RLHF (Reinforcement Learning from Human Feedback)
**Problem**: Model is accurate but "sounds robotic" or doesn't follow nuanced preferences.

**Solution**: Train a reward model based on human rankings.
1.  Generate 2-4 outputs for the same input.
2.  Humans rank them (best to worst).
3.  Train a reward model to predict human preferences.
4.  Use RL (PPO) to optimize the LLM to maximize the reward.

**Use Case**: ChatGPT uses RLHF to be helpful, harmless, and honest.

### Technique D: Distillation
**Problem**: Your fine-tuned 70B model is too slow/expensive.

**Solution**: Train a small model (7B) to mimic the large one.
1.  Use the 70B model to generate outputs for 10,000 inputs.
2.  Train the 7B model on these outputs.
3.  Result: 70% of the performance, 10x faster.

## 5. Use Case Deep Dives

### Use Case A: Medical Note Summarization
**Challenge**: EHR notes are cryptic ("Pt c/o SOB, +JVD, -edema").

**Solution**:
1.  Collect 2,000 real EHR notes + expert summaries.
2.  Fine-tune Llama 3 8B on this data.
3.  Result: Model learns hospital-specific abbreviations and format.

**Before Fine-Tuning**: "What is SOB?" → "I don't know."
**After Fine-Tuning**: "SOB = Shortness of Breath."

### Use Case B: Code Generation for Internal Framework
**Challenge**: Company uses a proprietary Python framework. GitHub Copilot doesn't know it.

**Solution**:
1.  Collect 5,000 code examples from internal repos.
2.  Fine-tune CodeLlama or StarCoder.
3.  Result: Model suggests code in company style.

**Before**: Suggests generic pandas code.
**After**: Suggests framework-specific methods.

### Use Case C: Customer Support for SaaS Product
**Challenge**: Generic chatbot doesn't understand product-specific terms ("What is a workspace?" vs. "What is a project?").

**Solution**:
1.  Export 1,000 past support tickets (Q&A pairs).
2.  Fine-tune GPT-3.5-turbo.
3.  Result: Chatbot speaks in company's voice, knows product features.

## 6. The Cost-Benefit Analysis

**Investment**:
- Data labeling: $5,000-20,000 (for 1,000 examples at $5-20 each).
- Compute: $500-5,000 (GPU hours).
- Engineering time: 2-4 weeks.
- **Total**: $10K-50K.

**Return**:
- Improved accuracy: 20-40% fewer errors.
- Better user experience: 30% higher satisfaction.
- Reduced support load: $100K/year savings (fewer escalations).

**Breakeven**: 3-6 months for most use cases.

## 7. When NOT to Fine-Tune

### Red Flag 1: Not Enough Data
If you have <50 examples, fine-tuning will overfit.
- *Alternative*: Use few-shot learning or RAG.

### Red Flag 2: Data is Changing Rapidly
If your domain changes weekly (stock market, news), fine-tuned models go stale fast.
- *Alternative*: RAG with real-time data feeds.

### Red Flag 3: Generic Task
If the task is "summarize any document," pre-trained models already excel.
- *Alternative*: Prompt engineering is enough.

### Red Flag 4: No Clear Success Metric
If you can't measure "better," you can't validate fine-tuning worked.
- *Alternative*: Define metrics first, then decide.

## 8. The "Gotchas"

### Gotcha A: Catastrophic Forgetting
**Problem**: Fine-tuned model forgets general knowledge.
- *Example*: After fine-tuning on legal docs, the model can't write poems anymore.

**Solution**: Use "continual learning" techniques or mix general data with fine-tuning data.

### Gotcha B: Overfitting to Training Data
**Problem**: Model memorizes training examples but fails on new inputs.

**Solution**: More diverse training data, regularization, early stopping.

### Gotcha C: Bias Amplification
**Problem**: If training data has bias, fine-tuning makes it worse.
- *Example*: Hiring AI trained on biased past decisions.

**Solution**: Audit training data, balance classes, test for fairness.

## 9. The Alara Implementation Checklist

### Pre-Fine-Tuning
- [ ] Tried prompt engineering? (Yes/No)
- [ ] Tried RAG? (Yes/No)
- [ ] Have >100 quality examples? (Yes/No)
- [ ] Have clear success metrics? (Yes/No)
- [ ] Have budget approval? (Yes/No)

### During Fine-Tuning
- [ ] Data cleaned and anonymized.
- [ ] Validation set held out (not used in training).
- [ ] Baseline performance measured.
- [ ] Human evaluation plan ready.

### Post-Fine-Tuning
- [ ] Model performance > baseline by 20%+.
- [ ] Deployment pipeline tested.
- [ ] Monitoring dashboard live.
- [ ] Re-training schedule defined.

## 10. The Future: Automated Fine-Tuning

**Vision**: AI systems that fine-tune themselves.
- User corrects an output → System logs correction.
- After 100 corrections → Auto-trigger fine-tuning.
- New model deployed automatically.

**Example**: Customer support bot gets smarter every week based on agent feedback.

**The Alara Philosophy**: Fine-tuning is not a one-time event. It's a continuous process of model improvement.
