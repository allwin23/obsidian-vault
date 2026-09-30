

## 🎯 Exam Essentials

Generative AI is a **general-purpose technology**. It can support many different business functions rather than being limited to one application.

The major advantages emphasized here are:

### 1. Adaptability

A foundation model can often be adapted to many tasks through:

- Prompt engineering
    
- In-context learning
    
- Fine-tuning
    
- Additional context/data
    

The same model can potentially summarize, classify, translate, generate, rewrite, and answer questions.

### 2. Responsiveness

GenAI can respond dynamically to natural-language instructions rather than requiring a separate rigid application for every task.

Example:

> “Rewrite this technical document for a beginner audience.”

The user can change the instruction without rebuilding the entire system.

### 3. Simplicity

Foundation models and managed GenAI services can reduce the amount of ML infrastructure and model-building work required.

Instead of:

> Collect huge dataset → train model → build infrastructure → deploy model

a business may be able to:

> Select foundation model → prompt/customize → evaluate → deploy

This can reduce development time and potentially cost.

⚠️ **Important:** “Potentially lower cost” does not mean GenAI is always cheaper. Inference, customization, model hosting, data preparation, evaluation, and monitoring can still be expensive.

---

# 2. What Can an LLM Do Without Additional Training?

A useful mental model is:

> **Can the task be completed from the information and instructions provided in the prompt?**

If yes, a capable foundation model may be able to perform the task through prompting alone.

### Example

**Task:**

> Read this email and determine whether it is a complaint.

The prompt contains the information required to perform the task.

→ An LLM can potentially do this with prompting.

---

### Different situation

> “Write a detailed article about an AWS service that was just released yesterday.”

If the model hasn't been given information about that new service, it cannot reliably know the specific details merely because it is an LLM.

You could provide:

> Official announcement + documentation + prompt

Now the model has relevant information to work with.

### Exam principle

> **GenAI can transform/generate information well when the required knowledge is available through its learned knowledge or supplied context.**

---

# 3. Foundation Model Knowledge vs Context

This distinction is extremely important.

A foundation model has knowledge/patterns learned during training.

But a prompt can provide **additional context** at inference time.

Example:

```text
Foundation model
      +
Company policy document
      +
User question
      ↓
Relevant response
```

The model doesn't need to have memorized the company's policy during pre-training if the relevant policy is supplied as context.

This is one reason **RAG** is useful for enterprise applications.

---

# 4. LLMs Don't Automatically Learn From Every Conversation

The transcript uses the analogy that every prompt is like asking a different child.

The exam-level concept is:

> **A normal inference request does not automatically update the model's parameters.**

If you tell the model:

> “Our company always uses this writing style.”

that instruction can affect the current interaction/context, but it does **not automatically retrain the underlying model**.

To systematically adapt model behavior, you may use techniques such as:

- Fine-tuning
    
- Other model customization methods
    
- Carefully designed prompts
    
- Persistent external context/memory mechanisms at the application layer
    

### Critical distinction

**Prompting:**

> Influence the current inference.

**Fine-tuning:**

> Update/adapt model parameters using additional training.

---

# 5. Generative AI Limitations

GenAI is powerful but isn't appropriate for every problem.

Important limitations include:

### Hallucinations

The model may generate plausible-sounding but incorrect information.

### Knowledge limitations

The model may not know:

- Newly released information
    
- Private company information
    
- Information outside its training data
    

Unless that information is supplied through an appropriate mechanism.

### Reliability

For high-stakes applications, outputs may require:

- Validation
    
- Human review
    
- Guardrails
    
- Retrieval
    
- Deterministic tools
    

### Reasoning limitations

LLMs can struggle with some:

- Complex reasoning
    
- Exact calculations
    
- Multi-step logic
    

### Cost

Large models can require significant:

- Inference compute
    
- Token processing
    
- Storage
    
- Infrastructure
    
- Evaluation/monitoring
    

### Responsible AI

Systems need to consider:

- Bias
    
- Fairness
    
- Privacy
    
- Security
    
- Safety
    
- Transparency
    
- Human oversight
    

---

# 🔑 Key Terms

|Term|Exam-level meaning|
|---|---|
|**General-purpose technology**|Technology applicable across many domains/use cases|
|**Adaptability**|Ability to apply/adapt a model to different tasks|
|**Responsiveness**|Ability to respond dynamically to natural-language instructions|
|**Prompting**|Providing instructions/context at inference time|
|**Foundation model**|Broadly pretrained model adaptable to many tasks|
|**Context**|Information supplied to the model during inference|
|**Hallucination**|Plausible but incorrect/unsupported generated content|
|**Fine-tuning**|Additional training that adapts model parameters|
|**RAG**|Retrieves external information and provides it as model context|
|**Human oversight**|Human review/intervention where appropriate|
|**Responsible AI**|Designing/using AI with safety, fairness, privacy, etc.|

---

# ⚔️ Important Comparisons

### Prompting vs Fine-Tuning

||Prompting|Fine-Tuning|
|---|---|---|
|Changes weights?|❌|✅|
|Training required?|❌|✅|
|Adds examples/context?|Yes|Through training data|
|Typical complexity|Lower|Higher|
|Useful for quick adaptation|✅|Less immediate|

---

### Model Knowledge vs Supplied Context

|Model knowledge|Supplied context|
|---|---|
|Learned during training|Provided during inference|
|Relatively static after training|Can be updated dynamically|
|Broad knowledge/patterns|Specific/current/private information|
|Can't automatically know new events|Can provide new information|

**Exam shortcut:**

> **Need current/private information? Think external context/RAG rather than assuming the model knows it.**

---

# 🧠 Exam Traps

### Trap 1 — “LLM knows everything”

❌ No.

The model's knowledge is constrained by its training and available context.

---

### Trap 2 — “Giving information in a prompt trains the model”

❌ No.

Providing information in a prompt affects the current inference/context. It doesn't automatically update model parameters.

---

### Trap 3 — “Fine-tuning is necessary for every new task”

❌ No.

A foundation model may perform many tasks through prompting or in-context learning without fine-tuning.

---

### Trap 4 — “GenAI always reduces costs”

❌ No.

It can reduce development effort and time, but model inference, customization, and infrastructure can still be expensive.

---

### Trap 5 — “If an LLM doesn't know something, it should say it doesn't know”

Not guaranteed.

A model can **hallucinate** an answer rather than reliably acknowledge that information is unavailable.

---

### Trap 6 — “A prompt can permanently teach the model”

❌ Not through ordinary inference.

Persistent model adaptation requires an appropriate mechanism such as fine-tuning, while persistent application context can be implemented externally.

---

# 📝 Exam Questions

### Q1 — Very Hard

A company wants an LLM to classify incoming customer emails as complaints or non-complaints. Each email contains enough information to make the classification, and the team doesn't need the model to permanently learn anything new.

Which approach is most appropriate to try first?

A. Train a foundation model from scratch  
B. Fine-tune the model immediately  
C. Use prompting or in-context learning with an existing foundation model  
D. Perform reinforcement learning from human feedback before testing the task

**Answer: C**

**Why:** The task can be performed from the information supplied in the prompt, so a pretrained model should be evaluated with prompting before more expensive customization.

---

### Q2 — Exam Trap

A company asks an LLM:

> “Write a detailed technical article about a product that was released yesterday.”

The model was trained before the product existed and is not given any product documentation.

What is the primary limitation?

A. The model cannot generate text without fine-tuning  
B. The model may lack the required factual knowledge and could generate unsupported information  
C. The model can only perform classification tasks  
D. The model cannot process natural-language instructions

**Answer: B**

**Why:** The required information isn't necessarily in the model's learned knowledge or current context. The model may hallucinate plausible but incorrect details.

---

### Q3 — Extremely Difficult

An organization supplies its current internal security policy as context whenever employees ask questions about company procedures. The foundation model itself has not been retrained.

What is the most accurate description?

A. The policy has permanently become part of the model's parameters  
B. The model is being fine-tuned on the policy during every question  
C. The policy is being supplied as inference-time context  
D. The model has performed additional pre-training on the policy

**Answer: C**

**Why:** The policy is provided at inference time. Supplying context does not modify the model's learned parameters.

---

### Q4 — Hard

A company wants to use GenAI to summarize reports, rewrite documents for different audiences, answer questions, and generate marketing content using the same underlying foundation model.

Which characteristic of GenAI does this scenario primarily demonstrate?

A. Adaptability  
B. Deterministic execution  
C. Parameter isolation  
D. Data normalization

**Answer: A — Adaptability**

**Why:** The same general-purpose model can be applied to multiple tasks through appropriate instructions/context.

---

### Q5 — Very Hard

A team argues:

> “Because GenAI can reduce the amount of custom ML development required, deploying a large foundation model will always reduce the company's total AI costs.”

Which response is most accurate?

A. Correct, because managed foundation models eliminate inference costs  
B. Correct, because larger models require less evaluation  
C. Incorrect, because GenAI can simplify development while still introducing inference, customization, infrastructure, and monitoring costs  
D. Incorrect, because GenAI always costs more than traditional ML

**Answer: C**

**Why:** GenAI can reduce development complexity, but total cost depends on the complete lifecycle and workload.

---

### Q6 — Exam-Trap

A user tells an LLM during an inference request:

> “From now on, always write our company's reports in this exact style.”

The model follows the instruction during the current interaction. What can be concluded?

A. The model's weights have been permanently updated  
B. The model has undergone fine-tuning  
C. The instruction can influence the current inference, but ordinary prompting doesn't permanently retrain the model  
D. The model has performed self-supervised learning

**Answer: C**

**Why:** Prompt instructions affect inference behavior/context but do not automatically modify model parameters.

---

### Q7 — Extremely Difficult

A business needs an LLM to answer questions about rapidly changing internal inventory data. The team wants the answers to reflect the latest database state without repeatedly retraining the foundation model.

Which architectural approach is most directly relevant?

A. Provide current data as external context during inference, such as through a retrieval-based architecture  
B. Increase the model's parameter count  
C. Use zero-shot prompting without providing inventory information  
D. Train the foundation model from scratch every day

**Answer: A**

**Why:** Current external data can be retrieved and supplied as context, avoiding repeated model retraining.

---

### Q8 — Hard

Which scenario most clearly demonstrates a limitation rather than a capability of a generative AI model?

A. Rewriting a technical document for beginners  
B. Summarizing a long report  
C. Generating a response using supplied documentation  
D. Reliably knowing confidential information that was never included in training or provided as context

**Answer: D**

**Why:** A model cannot be expected to know private information that it neither learned during training nor received through context/tools.

---

### Q9 — Very Hard

A customer-service application uses a highly capable foundation model. The model occasionally provides confident but factually incorrect answers even when the prompt is well written.

Which limitation should the team primarily consider?

A. Tokenization failure  
B. Hallucination  
C. Lack of multimodality  
D. Insufficient classification labels

**Answer: B — Hallucination**

**Why:** A confident but unsupported or incorrect generated response is characteristic of hallucination.

---

### Q10 — Exam-Trap

A company is comparing two approaches:

**Approach A:** Use a foundation model with carefully designed prompts.

**Approach B:** Fine-tune the model using thousands of company-specific examples.

The task is simple and Approach A already meets the required quality threshold.

Which consideration most strongly supports choosing Approach A?

A. Prompting guarantees zero hallucinations  
B. Fine-tuning always decreases model quality  
C. The simpler approach may meet requirements while avoiding unnecessary training complexity and cost  
D. Foundation models cannot be fine-tuned

**Answer: C**

**Why:** The goal isn't to maximize customization; it's to meet the business requirement efficiently. If prompting already works, additional training may be unnecessary.

---

# ⚡ 30-Second Revision

### Capabilities

1. **GenAI is general-purpose** → many business applications.
    
2. **Adaptability** → one foundation model can perform many tasks.
    
3. **Responsiveness** → natural-language instructions dynamically change behavior.
    
4. **Simplicity** → managed foundation models can reduce custom ML development.
    

### Limitations

5. **Hallucination** → plausible but incorrect information.
    
6. **Knowledge cutoff/limitations** → model may not know new information.
    
7. **Private data** → model doesn't automatically know company-specific information.
    
8. **Reasoning/calculation limitations** → exact tasks may require external tools/validation.
    
9. **Cost** → large-model inference and customization can be expensive.
    
10. **Responsible AI** → fairness, safety, privacy, security, and human oversight matter.
    

### Most important mental model

> **Prompting gives the model instructions/context.**  
> **Fine-tuning changes/adapts the model.**  
> **RAG supplies external/current knowledge.**

And the exam trap to remember:

> **An LLM sounding confident does NOT mean the information is correct.**