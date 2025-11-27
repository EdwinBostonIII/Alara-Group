# Scenario: Legacy Code Migration (COBOL to Java/Python)

**Category:** Technical / IT Modernization
**Trigger:** A bank or government agency runs on a mainframe from 1980. The engineers who wrote the COBOL code are retiring. They need to modernize before the system collapses.

---

## 1. The Situation
There are 2 million lines of COBOL code. No one fully understands the business logic buried in it. Rewriting it manually would take 5 years and cost $50M.

## 2. The Diagnosis
Manual migration fails because humans make translation errors. AI is excellent at translation, but it struggles with *context* (dependencies between files).

## 3. The Alara Playbook

### Phase 1: The "Rosetta Stone" Mapping (Week 1-4)
1.  **Dependency Graphing**: We don't just feed code to an LLM. We map the entire codebase to understand how Program A calls Subroutine B.
2.  **Documentation Generation**: We run the AI over the COBOL first to *explain* what it does. "This function calculates interest based on 1985 tax laws."

### Phase 2: The AI Translation Factory (Month 2-6)
1.  **Iterative Translation**:
    - *Input*: COBOL snippet.
    - *Prompt*: "Translate to Java Spring Boot. Use modern variable names. Add comments."
    - *Output*: Java code.
2.  **Unit Test Generation**: The AI writes tests for the *old* code and the *new* code. If the new code fails the old tests, it's wrong.

### Phase 3: Human Review & Integration
1.  **The 80/20 Rule**: AI gets 80% right. Senior Engineers spend their time fixing the complex 20%, not typing boilerplate.
2.  **Parallel Running**: Run the Mainframe and the Cloud App side-by-side for 6 months. Compare outputs down to the penny.

## 4. The "Gotchas"
- **"Spaghetti Code"**: AI translates bad COBOL into bad Java. We need a refactoring step, not just a translation step.
- **Hallucinated Libraries**: The AI might import a Python library that doesn't exist. We use a "linter" to verify all imports.
