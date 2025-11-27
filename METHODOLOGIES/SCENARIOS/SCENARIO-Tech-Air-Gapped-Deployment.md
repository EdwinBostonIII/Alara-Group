# Scenario: Air-Gapped Deployment (No Internet)

**Category:** Technical / Defense / Infrastructure
**Trigger:** A defense contractor or intelligence agency wants Generative AI capabilities but their network (SIPRNet/JWICS) has absolutely zero connection to the internet. They cannot call OpenAI's API.

---

## 1. The Situation
The client sees the value of AI for summarizing intelligence reports or analyzing sensor data. But "Cloud" is a dirty word. The data cannot leave the building. The model must run on their own servers.

## 2. The Diagnosis
Most modern AI is SaaS-based. Bringing it on-prem requires a completely different stack: hardware, model selection, and maintenance.

## 3. The Alara Playbook

### Phase 1: Hardware Procurement (Month 1-2)
1.  **The GPU Rig**: You can't run this on CPUs. We spec out NVIDIA H100 or A100 clusters.
2.  **Storage**: High-speed NVMe storage for model weights and vector indices.

### Phase 2: Model Selection (Open Weights)
1.  **Llama 3 (Meta)** or **Mistral (France)**: These are the top "open weights" models.
2.  **Quantization**: We compress the model (from 16-bit to 4-bit) to make it run faster on limited hardware with minimal accuracy loss.

### Phase 3: The "Sidecar" Architecture
1.  **Containerization**: We package the Model, the Vector DB (Milvus), and the UI (Streamlit) into Docker containers.
2.  **Deployment**: Deploy via Kubernetes (K8s) or OpenShift into the secure environment.
3.  **Updates**: Since there is no internet, updates must be "sneaker-netted" (brought in on secure hard drives) after rigorous scanning.

## 4. The "Gotchas"
- **Performance**: It will be slower than ChatGPT. Managing expectations is key.
- **Talent**: You need engineers who understand Linux/GPU drivers, not just API callers.
- **License Compliance**: Ensure the "Open Source" license allows for government/military use (some have restrictions).
