# Scenario: Voice AI Call Center Deployment

**Category:** Operations / Customer Experience / Technical
**Trigger:** A contact center wants to deploy AI voice agents to handle tier-1 support calls, but previous pilots failed due to poor call quality, angry customers, and agent resistance.

---

## 1. The Situation
The company receives 50,000 calls per month. Average handle time is 12 minutes. Labor costs are $1.8M annually. They piloted a voice AI, but:
- Customers hung up in frustration (AI didn't understand accents).
- Agents felt threatened (fear of job loss).
- Call quality dropped (AI couldn't handle emotional customers).

## 2. The Diagnosis
Voice AI is harder than chatbots because:
- **Real-time constraints**: Can't make customers wait 10 seconds for a response.
- **Emotion detection**: Must recognize frustration, anger, urgency.
- **Ambient noise**: Background chatter, poor phone connections.
- **Natural conversation**: Humans don't speak in perfect sentences.

## 3. The Alara Playbook

### Phase 1: The "Co-Pilot" Model (Month 1-2)
Don't replace agents immediately. Augment them first.

**Implementation**:
1.  **Live Transcription**: AI listens to the call and transcribes it in real-time.
2.  **Suggested Responses**: AI shows the agent 3 suggested responses on their screen as the customer talks.
3.  **Knowledge Retrieval**: AI searches the knowledge base and surfaces relevant articles.

**Benefit**: Agents get faster, more confident. No one loses their job yet.

### Phase 2: The "Low-Stakes" Handoff (Month 3-4)
Identify the simplest, most repetitive calls for full automation.

**Criteria for Automation**:
- ✅ "What's my account balance?"
- ✅ "When is my payment due?"
- ✅ "Track my order"
- ❌ "I want to cancel my subscription" (emotional, retention risk)
- ❌ "Your product broke and I'm furious" (escalation required)

**Flow**:
```
Caller → AI Greeting → Intent Detection
   ├─ Simple Query? → AI handles it → Call ends
   └─ Complex/Emotional? → Transfer to human agent (with context)
```

### Phase 3: The Voice Stack (Technical)
**Components**:
1.  **ASR (Automatic Speech Recognition)**: Converts speech → text.
    - *Options*: Deepgram, AssemblyAI, Google Cloud Speech-to-Text.
2.  **NLU (Natural Language Understanding)**: Understands intent.
    - *Options*: GPT-4, Claude, Rasa.
3.  **TTS (Text-to-Speech)**: Converts AI response → speech.
    - *Options*: ElevenLabs, Play.ht, AWS Polly.
4.  **Voice Activity Detection**: Knows when the customer stopped talking.

**Integration**:
```
[Phone System (Twilio/Five9)]
         ↓
   [ASR Engine]
         ↓
   [LLM (GPT-4)]
         ↓
   [TTS Engine]
         ↓
  [Back to Phone]
```

### Phase 4: The "Guardrails" System (Month 4-6)
**Safety Features**:
1.  **Emotion Detection**: If sentiment < -0.7 (very negative), auto-transfer to human.
2.  **Silence Detection**: If customer goes silent for 5 seconds, AI asks: "Are you still there?"
3.  **Loop Detection**: If AI asks the same question 3 times, transfer to human.
4.  **Profanity Filter**: If customer swears, AI says: "I understand you're frustrated. Let me connect you to a specialist."

### Phase 5: The "Human Takeover" Protocol
When a call transfers from AI → Human:
1.  **Context Handoff**: Agent sees full transcript, detected intent, customer emotion.
2.  **No Re-Introduction**: Customer doesn't have to repeat themselves.
3.  **Warm Transfer**: AI says "Let me connect you to [Agent Name] who specializes in this."

## 4. The Change Management Strategy

### For Agents (Preventing Resistance)
**Messaging**: "AI handles the boring calls so you can focus on helping customers with real problems."

**Incentives**:
- Agents who use the co-pilot tool get higher customer satisfaction scores → bonuses.
- Career path: "AI Trainer" role (teaching the AI how to handle edge cases).

### For Customers (Preventing Rage)
**Opt-Out Option**: "To speak to a human agent immediately, say 'agent' or press 0."

**Transparency**: "You're speaking with an AI assistant. If you prefer a human, I can transfer you anytime."

## 5. The KPIs (What to Measure)

| Metric | Goal | Risk Threshold |
|--------|------|----------------|
| Containment Rate | 60% (AI resolves without human) | <40% (not valuable) |
| Avg Handle Time | 3 min (vs. 12 min human) | >8 min (too slow) |
| Customer Satisfaction | 4.2/5 | <3.5/5 (customers hate it) |
| Transfer Rate | <40% | >60% (AI failing too often) |
| First Call Resolution | 85% | <70% (quality issue) |

## 6. Industry-Specific Considerations

### Healthcare
- **HIPAA**: All recordings must be encrypted. Transcripts are PHI.
- **Verification**: AI must verify identity before discussing health info.

### Finance
- **PCI Compliance**: AI can't process credit card payments directly. Must pause recording or transfer to IVR.
- **Fraud Alerts**: If AI detects suspicious activity, flag for human review immediately.

### Utilities (Electric, Gas, Water)
- **Emergency Routing**: "Gas leak" or "power outage" keywords trigger immediate human transfer.
- **Multilingual**: Must support Spanish, often Chinese/Vietnamese in certain markets.

## 7. The "Gotchas"
- **Accent Bias**: ASR models perform worse on non-native English speakers. Test extensively with diverse callers.
- **The "Uncanny Valley"**: If the voice sounds *almost* human but not quite, it creeps people out. Either go fully robotic or hire voice actors to train the TTS.
- **Background Noise**: Kids screaming, traffic sounds, dogs barking—AI struggles. Use noise cancellation preprocessing.
- **The "Hold Music" Problem**: If AI puts someone on hold, they assume they're being transferred and hang up.

## 8. Cost Analysis
**Before AI**:
- 50,000 calls/month × 12 min × $0.50/min (agent cost) = $300K/month

**After AI (60% containment)**:
- 30,000 calls handled by AI × 3 min × $0.10/min (AI cost) = $9K/month
- 20,000 calls to humans × 12 min × $0.50/min = $120K/month
- **Total**: $129K/month
- **Savings**: $171K/month ($2M annually)

**ROI**: Even after $500K implementation cost, payback in 3 months.
