

## 🎯 Exam Essentials

### 1. Advantages of AWS Generative AI Services

- **Concept:** AWS generative AI services can reduce the effort required to build generative AI applications and provide infrastructure and managed capabilities that help organizations move faster.
    
- Key advantages from the transcript:
    
    - **Accessibility**
        
    - **Lower barrier to entry**
        
    - **Efficiency**
        
    - **Cost-effectiveness**
        
    - **Speed to market**
        
    - Ability to meet **business objectives**
        
- **Exam trigger:**
    
    > “Reduce the effort, expertise, infrastructure burden, or time required to build a generative AI application”  
    > → Consider **managed AWS generative AI capabilities**.
    

---

### 2. Transfer Learning

- **Concept:** Transfer learning uses knowledge learned by a pretrained model as the starting point for training on a new dataset/task rather than training a model completely from scratch.
    
- **Benefits:**
    
    - Can require **less training time**
        
    - Can work effectively with **smaller datasets**
        
    - Reuses knowledge already learned by the pretrained model
        
- **Important distinction:**  
    **Transfer learning ≠ training from scratch.**
    
- The pretrained model already contains learned information, so training focuses on adapting that existing knowledge to the new dataset/task.
    
- **Exam trigger:**
    
    > “Start with an existing pretrained model and adapt it to a new dataset/task”  
    > → **Transfer learning**
    

---

### 3. Amazon SageMaker JumpStart

- **Concept:** SageMaker JumpStart helps users discover and use existing **models, algorithms, datasets, projects, and solutions** to accelerate ML development.
    
- It provides resources based on **industry best practices** and can help users get started more quickly.
    
- **Exam trigger:**
    
    > “Quickly find pretrained models, algorithms, datasets, or ML solutions to accelerate development”  
    > → **SageMaker JumpStart**
    

---

### 4. AWS Cloud Adoption Framework for AI, ML, and Generative AI (CAF-AI)

- **Concept:** The AWS Cloud Adoption Framework for AI, ML, and Generative AI provides a **starting point and guide** for an organization's AI/ML/generative AI journey.
    
- It can support:
    
    - AI strategy discussions
        
    - Collaboration with teams
        
    - Collaboration with AWS Partners
        
- **Exam trigger:**
    
    > “Framework to guide an organization's AI/ML/generative AI adoption strategy”  
    > → **CAF-AI**
    

---

### 5. Generative AI Infrastructure Security

- **Concept:** Sensitive business information used by generative AI applications must be protected.
    
- Examples of sensitive data mentioned:
    
    - Personal data
        
    - Compliance data
        
    - Operational data
        
    - Financial information
        
    - Model weights
        
    - Data processed by models
        
- AWS considers security across **three layers of the generative AI stack**.
    

---

### 6. Three Layers of the Generative AI Stack

#### Layer 1 — Infrastructure

- Provides the underlying tools and infrastructure used to **build and train LLMs and foundation models**.
    
- Training and inference can require significant compute resources.
    
- Specialized hardware can provide improved **price-performance**.
    

Examples mentioned in the transcript:

- AWS Inferentia
    
- AWS Trainium
    
- GPU-based EC2 instances such as P4, P5, G5, and G6
    

**Exam trigger:**

> “Underlying compute/hardware for training or inference”  
> → **Infrastructure layer**

---

#### Layer 2 — Models and Development Tools

- Provides access to **models and tools** needed to build and scale generative AI applications.
    
- Includes capabilities for developing, deploying, training, and tuning AI/ML models.
    
- This layer consumes foundation-model capabilities and provides building blocks for applications.
    

**Exam trigger:**

> “Tools and model capabilities used to develop and scale generative AI applications”  
> → **Model/platform layer**

---

#### Layer 3 — Applications

- Contains applications that use LLMs and other foundation models.
    
- Applications can:
    
    - Generate content
        
    - Write or debug code
        
    - Derive insights
        
    - Take actions
        
    - Use prompt engineering
        
    - Implement architectures such as **RAG**
        

**Exam trigger:**

> “User-facing application that uses an LLM/FM to generate content or perform actions”  
> → **Application layer**

---

### 7. AWS Nitro System

- **Concept:** The AWS Nitro System uses specialized hardware and associated firmware designed to enforce security restrictions for workloads running on Amazon EC2.
    
- The transcript emphasizes protection against unauthorized access to workloads and data running on Nitro-based EC2 instances.
    
- The transcript specifically mentions Nitro-based instances using:
    
    - **AWS Inferentia**
        
    - **AWS Trainium**
        
    - GPUs such as **P4, P5, G5, and G6**
        
- **Exam trigger:**
    
    > “Protect EC2 workloads using specialized hardware and firmware that enforce security restrictions”  
    > → **AWS Nitro System**
    

---

### 8. AI System Security

The transcript identifies three critical components of an AI system:

1. **Input**
    
2. **Model**
    
3. **Output**
    

Security policies, standards, guidelines, and clearly defined roles/responsibilities should be established to protect AI workloads.

- **Exam trigger:**
    
    > “Identify the fundamental components that need protection in an AI system”  
    > → **Input → Model → Output**
    

---

### 9. AI-Specific Security Vulnerabilities

The transcript specifically identifies:

- **Prompt injection**
    
- **Data poisoning**
    
- **Model inversion**
    

These are vulnerabilities that organizations need to consider when securing AI systems.

- **Prompt injection:** An attacker attempts to manipulate model behavior through crafted input/prompts.
    
- **Data poisoning:** Malicious or manipulated data is introduced into data used by an AI/ML system.
    
- **Model inversion:** Attempts to derive sensitive information about training data through model behavior.
    

**Exam trigger:**

> “Attacker manipulates instructions sent to an LLM” → **Prompt injection**

**Exam trigger:**

> “Malicious data is introduced into ML training data” → **Data poisoning**

---

### 10. AI Security Controls

The transcript highlights:

- **Encryption**
    
- **Multi-factor authentication (MFA)**
    
- **Continuous monitoring**
    
- Security policies and standards
    
- Defined roles and responsibilities
    
- Alignment with organizational risk tolerance and frameworks
    

These controls help reduce risks such as:

- Privacy breaches
    
- Data manipulation
    
- Abuse
    
- Compromised decision-making
    

---

### 11. Security Across the AI Stack

- **Concept:** AI security should not focus only on the model.
    
- Security needs to account for:
    
    - Infrastructure
        
    - Models and development tools
        
    - Applications
        
    - Inputs
        
    - Outputs
        
    - Data
        
- **Important distinction:** Protecting the model alone does not secure the entire AI system.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Transfer learning**|Adapting knowledge from a pretrained model to a new dataset/task|
|**Pretrained model**|Model that has already learned from existing training data|
|**SageMaker JumpStart**|Helps discover and use models, algorithms, datasets, and ML solutions|
|**CAF-AI**|AWS framework for guiding AI/ML/generative AI adoption|
|**Foundation model**|Broadly trained model used as a starting point for applications|
|**AWS Nitro System**|Specialized hardware/firmware infrastructure designed to enforce EC2 security restrictions|
|**AWS Trainium**|AWS ML accelerator mentioned for model training workloads|
|**AWS Inferentia**|AWS ML accelerator mentioned for inference workloads|
|**Prompt injection**|Attack that attempts to manipulate an AI system through crafted prompts/input|
|**Data poisoning**|Introducing manipulated or malicious data into ML data|
|**Model inversion**|Attempt to derive sensitive information from model behavior|
|**Input**|Data/instructions provided to an AI system|
|**Model**|AI/ML component that processes inputs|
|**Output**|Content or result generated by the AI system|
|**MFA**|Authentication requiring multiple verification factors|
|**Price-performance**|Relationship between computational performance and cost|
|**RAG**|Generative AI architecture that retrieves relevant information to augment model generation|

---

## ⚔️ Important Comparisons

### Training From Scratch vs Transfer Learning

|Approach|Use when|Key distinction|
|---|---|---|
|**Training from scratch**|Building a model without relying on an existing pretrained model|Model learns from the training process starting without transferred pretrained knowledge|
|**Transfer learning**|Adapting an existing pretrained model to a new dataset/task|Reuses knowledge already learned by the pretrained model|

---

### Three Generative AI Stack Layers

|Layer|Use when|Key distinction|
|---|---|---|
|**Infrastructure**|Training/inference compute and underlying hardware|Provides computational foundation|
|**Models & tools**|Developing, training, tuning, deploying, and scaling AI applications|Provides model capabilities and development tools|
|**Applications**|Building user/business-facing AI functionality|Uses LLMs/FMs to generate content, insights, code, or actions|

---

### AI Security Vulnerabilities

|Vulnerability|Use when|Key distinction|
|---|---|---|
|**Prompt injection**|Attacker manipulates model behavior through input|Attack targets instructions/prompts|
|**Data poisoning**|Training data is manipulated|Attack targets ML data|
|**Model inversion**|Sensitive information is inferred from model behavior|Attack targets information leakage from the model|

---

### Trainium vs Inferentia

|Technology|Use when|Key distinction|
|---|---|---|
|**AWS Trainium**|ML model training|AWS ML training accelerator|
|**AWS Inferentia**|ML model inference|AWS inference accelerator|

---

## 🧠 Exam Traps

### Trap 1 — Transfer learning means training a model completely from scratch ❌

**Correct:** Transfer learning **starts with a pretrained model** and adapts its learned knowledge to a new dataset/task.

---

### Trap 2 — Transfer learning is useful only when huge datasets are available ❌

**Correct:** One benefit described in the transcript is that transfer learning can produce effective models with **smaller datasets and less training time**.

---

### Trap 3 — SageMaker JumpStart is itself a foundation model ❌

**Correct:** JumpStart helps users **find and use models, algorithms, datasets, and solutions** to accelerate development.

---

### Trap 4 — CAF-AI is an AI model ❌

**Correct:** CAF-AI is an **AWS adoption framework** that can guide organizational AI/ML/generative AI strategy and adoption.

---

### Trap 5 — Nitro System is an AI model security feature ❌

**Correct:** Nitro is underlying **EC2 infrastructure technology using specialized hardware and firmware** to enforce security restrictions.

---

### Trap 6 — Securing the model automatically secures the AI application ❌

**Correct:** Security needs to cover the **input, model, and output**, as well as the broader infrastructure and application layers.

---

### Trap 7 — Prompt injection means poisoning training data ❌

**Correct:**  
**Prompt injection → manipulates model behavior through crafted input/prompts.**

**Data poisoning → manipulates data used by the ML system.**

---

### Trap 8 — Model inversion means modifying the model's weights ❌

**Correct:** Model inversion concerns attempts to **derive sensitive information from model behavior**.

---

### Trap 9 — Trainium and Inferentia are interchangeable ❌

**Correct:** In the context presented here:

**Trainium → training**

**Inferentia → inference**

---

### Trap 10 — Generative AI security only concerns customer information ❌

**Correct:** Sensitive AI data can include **personal, compliance, operational, financial data, model weights, and data processed by models**.

---

### Trap 11 — AWS infrastructure only provides computational capacity ❌

**Correct:** The transcript emphasizes infrastructure benefits including **security, compliance, responsibility, safety, and price-performance**, in addition to compute.

---

### Trap 12 — Encryption and MFA solve every AI-specific security vulnerability ❌

**Correct:** Encryption and MFA are important security controls, but AI systems also require consideration of **AI-specific threats such as prompt injection, data poisoning, and model inversion**.

---

# 📝 Exam Questions

> **Question order is intentionally shuffled.** The questions do not follow the transcript sequence. Distractors are deliberately closely related so that the scenario's exact requirement matters.

### Question 1

A machine learning team has only a relatively small dataset for a new classification task. Instead of creating and training a model from the beginning, the team wants to reuse knowledge learned by an existing pretrained model and adapt it to the new dataset.

Which approach best matches this requirement?

A. Train a new model from scratch using only the new dataset  
B. Use transfer learning to adapt the pretrained model to the new task  
C. Use model inversion to extract the pretrained model's learned features  
D. Use prompt injection to provide the model with the new dataset during inference

**Answer:** **B — Transfer learning**

**Why:** Transfer learning uses an existing **pretrained model as the starting point**, potentially reducing training time and data requirements.

---

### Question 2

A company wants to quickly identify pretrained models, algorithms, datasets, and existing ML solutions that it can use as starting points for a new project rather than developing everything independently.

Which AWS capability most directly addresses this requirement?

A. AWS Cloud Adoption Framework for AI, ML, and Generative AI  
B. Amazon SageMaker JumpStart  
C. AWS Nitro System  
D. Amazon EC2 Auto Scaling

**Answer:** **B — Amazon SageMaker JumpStart**

**Why:** JumpStart provides access to **models, algorithms, datasets, projects, and solutions** intended to accelerate ML development.

---

### Question 3

An organization is designing security controls for an AI application. The security team identifies three areas that could be attacked: malicious instructions supplied to the model, manipulated training data, and attempts to infer sensitive information from model behavior.

Which mapping is correct?

A. Prompt injection → manipulated training data; data poisoning → malicious prompts; model inversion → encryption failure  
B. Prompt injection → malicious instructions; data poisoning → manipulated training data; model inversion → sensitive information inferred from model behavior  
C. Prompt injection → sensitive information inference; data poisoning → unauthorized authentication; model inversion → malicious instructions  
D. Prompt injection → model hardware compromise; data poisoning → output formatting; model inversion → workflow orchestration

**Answer:** **B**

**Why:** The three threats map directly to the definitions presented in the transcript.

---

### Question 4

A company is selecting infrastructure for an ML workload. The team wants specialized AWS hardware for computational workloads and is specifically evaluating an accelerator intended for **model training**.

Which technology should the team consider?

A. AWS Inferentia  
B. AWS Trainium  
C. AWS Nitro System  
D. Amazon SageMaker JumpStart

**Answer:** **B — AWS Trainium**

**Why:** The transcript identifies **Trainium** as an ML accelerator associated with training, while Inferentia is associated with inference.

---

### Question 5

An enterprise wants its AI strategy discussions to follow an AWS framework that provides guidance for adopting and advancing its AI, ML, and generative AI capabilities. The company wants to use the framework when discussing strategy with internal teams and AWS Partners.

Which resource best matches this requirement?

A. SageMaker JumpStart  
B. AWS Nitro System  
C. AWS Cloud Adoption Framework for AI, ML, and Generative AI  
D. Amazon EC2

**Answer:** **C — AWS Cloud Adoption Framework for AI, ML, and Generative AI**

**Why:** CAF-AI is described as a **starting point and guide for an organization's AI, ML, and generative AI journey**, including strategy discussions and collaboration.

---

### Question 6

An organization hosts sensitive model weights and data processed by an AI workload on Nitro-based EC2 instances. The security team wants underlying infrastructure designed with specialized hardware and firmware that enforce restrictions intended to protect EC2 workloads and data from unauthorized access.

Which AWS technology is most directly relevant?

A. AWS Cloud Adoption Framework  
B. Amazon SageMaker JumpStart  
C. AWS Nitro System  
D. Amazon SageMaker Model Registry

**Answer:** **C — AWS Nitro System**

**Why:** Nitro uses specialized hardware and associated firmware to enforce security restrictions for **Nitro-based EC2 workloads**.

---

### Question 7

An organization is designing a generative AI platform and separates it into three layers. The first layer provides computational resources for training and inference, the second provides models and tools used to build and scale AI applications, and the third contains applications that users interact with.

Which layer contains the organization's RAG-powered customer application?

A. Infrastructure layer  
B. Model and development-tools layer  
C. Application layer  
D. Hardware acceleration layer

**Answer:** **C — Application layer**

**Why:** The transcript places applications using LLMs/FMs—including **RAG applications**—in the top/application layer.

---

### Question 8

A security team discovers that an attacker is attempting to influence an LLM by inserting specially crafted instructions into user-provided content. The attacker is not modifying the model's training dataset.

Which vulnerability is most directly represented?

A. Data poisoning  
B. Model inversion  
C. Prompt injection  
D. Infrastructure misconfiguration

**Answer:** **C — Prompt injection**

**Why:** The defining clue is **manipulation through crafted input/instructions**. Data poisoning instead involves manipulated ML data.

---

### Question 9

A company is deciding whether to build its own generative AI infrastructure. The team is concerned about the computational requirements of training and inference and wants infrastructure that can provide better price-performance than relying only on traditional CPUs or GPUs.

Which consideration from the lesson most directly addresses this requirement?

A. Using specialized AWS ML hardware accelerators  
B. Using human feedback to align model outputs  
C. Using CAF-AI to define organizational strategy  
D. Using model inversion to inspect model behavior

**Answer:** **A**

**Why:** The transcript specifically discusses **specialized hardware** as a way to address large compute requirements and improve price-performance.

---

### Question 10

A security architect is reviewing an AI system and wants to ensure that security policies address the complete flow of information rather than only protecting the trained model.

According to the lesson, which three fundamental components should the architect consider?

A. Dataset, hyperparameters, and optimizer  
B. Input, model, and output  
C. Infrastructure, database, and API  
D. Training, validation, and deployment

**Answer:** **B — Input, model, and output**

**Why:** The transcript explicitly identifies **input, model, and output** as the three critical components of an AI system that need appropriate security policies and controls.

---

## ⚡ 30-Second Revision

1. **Transfer learning → pretrained model + new dataset/task; less data/time may be required.**
    
2. **SageMaker JumpStart → models + algorithms + datasets + solutions for faster ML development.**
    
3. **CAF-AI → AWS framework for AI/ML/generative AI adoption and strategy.**
    
4. **Generative AI stack → Infrastructure → Models/tools → Applications.**
    
5. **Nitro System → specialized EC2 hardware/firmware enforcing security restrictions.**
    
6. **Trainium → training accelerator.**
    
7. **Inferentia → inference accelerator.**
    
8. **AI system security → Input + Model + Output.**
    
9. **Prompt injection → malicious/manipulative instructions through input.**
    
10. **Data poisoning → manipulated training/ML data.**
    
11. **Model inversion → attempt to derive sensitive information from model behavior.**
    
12. **Security controls → encryption + MFA + continuous monitoring + policies/roles.**
    
13. **AWS generative AI infrastructure → accessibility, efficiency, cost-effectiveness, speed to market, security, and business objectives.**