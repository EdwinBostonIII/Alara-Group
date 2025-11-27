# Scenario: The "Shadow AI" Leak (Security)

**Category:** Security / IP Protection
**Trigger:** IT discovers that engineers are pasting proprietary code into ChatGPT, or HR is pasting employee performance reviews into a public PDF summarizer.

---

## 1. The Situation
The CISO (Chief Information Security Officer) sees traffic logs showing gigabytes of data going to `api.openai.com` or `chatgpt.com` from corporate devices. There is panic that trade secrets are now training data for a public model.

## 2. The Diagnosis
Employees aren't malicious; they are trying to be productive. The company failed to provide a **safe** alternative, so employees found their own.

## 3. The Alara Playbook

### Phase 1: The "Amnesty" Audit (Week 1)
1.  **No Witch Hunt**: Announce that no one will be fired for past usage. We need honesty to assess exposure.
2.  **Traffic Analysis**: Identify the top 5 tools being used (ChatGPT, Claude, Grammarly, Otter.ai).
3.  **Data Classification**: Was it PII (Customer names)? IP (Source code)? Strategy (M&A plans)?

### Phase 2: The "Walled Garden" (Week 2-4)
1.  **Enterprise License Procurement**: Immediately buy ChatGPT Enterprise or Microsoft Copilot. These contracts explicitly state *zero data training*.
2.  **The "Safe Sandbox"**: Deploy a private internal chat interface (e.g., "CompanyGPT") hosted on Azure/AWS.
    - *Feature*: It looks and feels like ChatGPT.
    - *Reality*: It runs in your private cloud VPC.

### Phase 3: Policy & Blocking (Month 2)
1.  **CASB Rules**: Update the firewall to block consumer AI sites (personal Gmail, free ChatGPT).
2.  **Browser Extensions**: Push a group policy to block unauthorized browser extensions (often the biggest leak source).

## 4. The "Gotchas"
- **Blocking without Replacing**: If you block ChatGPT without giving them a tool, they will just use their personal phones. You lose all visibility.
- **The "Grammarly" Blindspot**: Everyone focuses on Chatbots, but "Writing Assistants" read every keystroke.
