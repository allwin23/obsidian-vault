# Task Statement 3.3 — Describe the Training and Fine-Tuning Process for Foundation Models

## 🎯 Exam Essentials

### **1. Key Elements of Foundation Model Training**

- **Concept:** The transcript identifies three key elements:
    
    - **Pre-training**
        
    - **Fine-tuning**
        
    - **Continuous pre-training**
        
- **Exam trigger:** If asked about the major training stages for foundation models, remember these **three elements**.
    

---

### **2. Pre-Training**

- **Concept:** Pre-training is the large-scale initial training process used to develop the capabilities of a foundation model.
    
- **Data:** Uses huge amounts of **unstructured data**.
    
- **Learning approach:** Uses **self-supervised learning**.
    
- **Scale mentioned:** Millions of GPUs, compute hours, terabytes/petabytes of data, trillions of tokens, experimentation, and significant time.
    
- **Exam trigger:** **Huge unstructured dataset + self-supervised learning → Pre-training.**
    

---

### **3. What Pre-Training Gives the Model**

- **Concept:** During pre-training, generative AI models learn their fundamental capabilities.
    
- **Examples of training data mentioned:** Documents, videos, images, files, audio files, and other data.
    
- **Key limitation:** Even after extensive pre-training, a foundation model may require additional training or instructions for a particular domain, dataset, task, or human-oriented behavior.
    
- **Exam trigger:** **General capabilities → pre-training; specialized behavior → consider fine-tuning.**
    

---

### **4. Fine-Tuning**

- **Concept:** Fine-tuning extends the training of a pre-trained model to improve generation for a **specific task**.
    
- **Learning approach:** The transcript describes fine-tuning as **supervised learning**.
    
- **Data:** Uses a dataset containing **labeled examples**.
    
- **Effect:** Updates model weights to adapt the foundation model to custom datasets and use cases.
    
- **Exam trigger:** **Labeled examples + specific task + weight updates → Fine-tuning.**
    

---

### **5. Pre-Training vs. Fine-Tuning**

- **Pre-training:**
    
    - Large-scale training
        
    - Huge amounts of unstructured data
        
    - Self-supervised learning
        
    - Develops general model capabilities
        
- **Fine-tuning:**
    
    - Extends training of a pre-trained model
        
    - Uses labeled examples
        
    - Supervised learning
        
    - Adapts the model to specific tasks/use cases
        
- **Exam trigger:** **General capability → pre-training; task-specific adaptation → fine-tuning.**
    

---

### **6. Instruction-Based Fine-Tuning**

- **Concept:** Instruction-based fine-tuning uses **labeled examples** to improve performance on specific tasks.
    
- **Purpose:** Helps the model learn to respond appropriately to task instructions.
    
- **Exam trigger:** **Labeled task instructions/examples → Instruction-based fine-tuning.**
    

---

### **7. Single-Task Fine-Tuning**

- **Concept:** A foundation model capable of many tasks can be fine-tuned to improve performance on a particular task.
    
- **Benefit:** Specializes the model for a specific application/use case.
    
- **Tradeoff:** Specializing too heavily can lead to **catastrophic forgetting**.
    
- **Exam trigger:** **One specific task + specialized performance → Single-task fine-tuning.**
    

---

### **8. Catastrophic Forgetting**

- **Concept:** Catastrophic forgetting occurs when fine-tuning modifies the original LLM's weights and improves performance on the target task while degrading performance on other tasks.
    
- **Key tradeoff:** Better specialization can come at the expense of generalization.
    
- **Important consideration:** If the application only requires reliable performance on one task, degradation of other capabilities may be less concerning.
             
- **Exam trigger:** **Fine-tuning improves one task but degrades previously learned tasks → Catastrophic forgetting.**
    

---

### **9. Full Fine-Tuning**

- **Concept:** During full fine-tuning, **every parameter** in the model is updated through supervised learning.
    
- **Resource consideration:** Training/tuning requires memory for:
    
    - Model parameters
        
    - Optimizer
        
    - Gradients
        
    - Forward activations
        
    - Temporary memory
        
- **Impact:** These requirements increase GPU memory usage and can increase compute costs.
    
- **Exam trigger:** **Every model parameter updated → Full fine-tuning.**
    

---

### **10. Parameter-Efficient Fine-Tuning (PEFT)**

- **Concept:** PEFT is a set of techniques that preserves/freezes the original LLM parameters and trains only a **small number of task-specific parameters or adapter layers**.
    
- **Purpose:** Reduce the compute and memory requirements of fine-tuning.
    
- **Key distinction:** PEFT does not require updating the entire model.
    
- **Exam trigger:** **Freeze most original parameters + train small task-specific components → PEFT.**
    

---

### **11. LoRA**

- **Concept:** Low-Rank Adaptation (**LoRA**) is a popular PEFT technique.
    
- **Mechanism described:** Preserves/freezes the original foundation-model weights and introduces **trainable low-rank matrices** into layers of a transformer architecture.
    
- **Purpose:** Adapt the model while training a smaller set of parameters.
    
- **Exam trigger:** **Frozen original weights + trainable low-rank matrices → LoRA.**
    

---

### **12. PEFT and LoRA Modify Weights, Not Representations**

- **Concept:** The transcript explicitly states that **PEFT and LoRA modify model weights but not representations**.
    
- **Exam trigger:** If asked to distinguish weight-based adaptation from representation-based adaptation, this is the key distinction given in the transcript.
    

---

### **13. Representation Fine-Tuning (ReFT)**

- **Concept:** ReFT is a fine-tuning process that **freezes the base model** and learns task-specific interventions on its **hidden representations**.
    
- **Key distinction:** Unlike PEFT/LoRA, the focus is on **representations rather than modifying model weights**.
    
- **Exam trigger:** **Frozen base model + interventions on hidden representations → ReFT.**
    

---

### **14. Linear Representation Hypothesis**

- **Concept:** The transcript states that the linear representation hypothesis proposes that concepts are encoded in **linear subspaces of representations** within a neural network.
    
- **Exam trigger:** **Concepts encoded in linear subspaces → Linear Representation Hypothesis.**
    

---

### **15. Multitask Fine-Tuning**

- **Concept:** Multitask fine-tuning extends fine-tuning beyond a single task.
    
- **Data:** Requires examples containing inputs and outputs for **multiple tasks**.
    
- **Examples mentioned:** Reviews/ratings, summarization, code translation, and other tasks.
    
- **Outcome:** Produces an **instruction-tuned model** capable of performing multiple tasks.
    
- **Exam trigger:** **Multiple tasks + labeled input/output examples → Multitask fine-tuning.**
    

---

### **16. Multitask Fine-Tuning and Catastrophic Forgetting**

- **Concept:** The transcript states that losses can be calculated from examples and used to update model weights.
    
- **Key benefit:** Multitask training can help **mitigate and avoid catastrophic forgetting**.
    
- **Reason:** Training across multiple tasks helps preserve broader task capabilities rather than specializing exclusively in one task.
    
- **Exam trigger:** **Multiple tasks + maintaining broader capabilities → Multitask fine-tuning.**
    

---

### **17. Domain Adaptation Fine-Tuning**

- **Concept:** Domain adaptation fine-tuning adapts a pre-trained foundation model to **specific domain data**.
    
- **Data requirement:** Can use a **limited amount of domain-specific data**.
    
- **Examples:** Industry jargon, technical terminology, and specialized information.
    
- **Exam trigger:** **Specialized domain language/data → Domain adaptation fine-tuning.**
    

---

### **18. Amazon SageMaker JumpStart Fine-Tuning**

- **Concept:** The transcript states that Amazon SageMaker JumpStart can fine-tune large language models, particularly text-generation models, using **domain-specific custom datasets**.
    
- **Purpose:** Improve model performance for specific domains.
    
- **Exam trigger:** **SageMaker JumpStart + custom/domain-specific dataset + LLM fine-tuning → JumpStart fine-tuning.**
    

---

### **19. Reinforcement Learning from Human Feedback (RLHF)**

- **Concept:** RLHF uses reinforcement learning to fine-tune an LLM using **human feedback data**.
    
- **Purpose:** Improve model performance and align the model with **human preferences**.
    
- **Key distinction:** The training signal comes from human feedback rather than simply labeled examples for a specific task.
    
- **Exam trigger:** **Human feedback + reinforcement learning + alignment with human preferences → RLHF.**
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Pre-training**|Large-scale initial training using huge amounts of unstructured data and self-supervised learning|
|**Fine-tuning**|Extending training of a pre-trained model for a specific task/use case|
|**Continuous pre-training**|One of the three training elements identified in the transcript; no further details are provided here|
|**Self-supervised learning**|Learning approach identified for pre-training using large amounts of unstructured data|
|**Supervised learning**|Learning approach identified for fine-tuning using labeled examples|
|**Instruction-based fine-tuning**|Fine-tuning using labeled examples for improved performance on specific tasks|
|**Catastrophic forgetting**|Degradation of previously learned capabilities after task-specific fine-tuning|
|**Full fine-tuning**|Updating every parameter in the model|
|**PEFT**|Parameter-efficient fine-tuning; trains a small set of task-specific parameters while preserving most original parameters|
|**LoRA**|PEFT technique using trainable low-rank matrices while preserving original model weights|
|**ReFT**|Representation fine-tuning that learns task-specific interventions on hidden representations|
|**Representation**|Encoded semantic information within model hidden representations|
|**Multitask fine-tuning**|Fine-tuning using examples for multiple tasks|
|**Instruction-tuned model**|Model trained to perform multiple tasks through instruction-based examples|
|**Domain adaptation fine-tuning**|Adapting a foundation model to specialized domain-specific data|
|**RLHF**|Reinforcement learning using human feedback to align model behavior with human preferences|
|**Linear representation hypothesis**|Hypothesis that concepts are encoded in linear subspaces of neural-network representations|
|**Adapter layers**|Small task-specific components trained in PEFT approaches|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Pre-training**|Building general foundation-model capabilities|Huge unstructured data + self-supervised learning|
|**Fine-tuning**|Adapting a pre-trained model to a task|Labeled examples + supervised learning|
|**Instruction-based fine-tuning**|Improving task performance through instructions|Uses labeled instruction examples|
|**Full fine-tuning**|Adapting the entire model|Updates every model parameter|
|**PEFT**|Need task adaptation with lower compute/memory|Freezes/preserves most parameters and trains a small subset|
|**LoRA**|Applying a specific PEFT approach|Adds trainable low-rank matrices to transformer layers|
|**PEFT / LoRA**|Weight-based adaptation|Modifies weights, not representations|
|**ReFT**|Adapting model behavior through representations|Freezes base model and intervenes on hidden representations|
|**Single-task fine-tuning**|Optimizing for one specific task|Can increase risk of catastrophic forgetting|
|**Multitask fine-tuning**|Maintaining performance across multiple tasks|Uses examples for multiple tasks and can mitigate catastrophic forgetting|
|**Domain adaptation**|Specialized industry/domain language or data|Uses limited domain-specific data|
|**RLHF**|Aligning model behavior with human preferences|Uses reinforcement learning with human feedback|

---

## 🧠 Exam Traps

### **1. Pre-Training vs. Fine-Tuning**

**Trap:** Both pre-training and fine-tuning use the same type and scale of training data.

**Correct:** The transcript distinguishes them:

- **Pre-training →** huge amounts of unstructured data + self-supervised learning.
    
- **Fine-tuning →** labeled examples + supervised learning for specific tasks.
    

---

### **2. Fine-Tuning Creates the Foundation Model**

**Trap:** Fine-tuning is the initial process that gives a foundation model its general capabilities.

**Correct:** **Pre-training** develops the general capabilities; fine-tuning adapts the pre-trained model for specific tasks/use cases.

---

### **3. Full Fine-Tuning**

**Trap:** Full fine-tuning updates only the parameters relevant to the target task.

**Correct:** **Every parameter** in the model is updated during full fine-tuning.

---

### **4. PEFT**

**Trap:** PEFT requires updating the entire foundation model.

**Correct:** PEFT freezes/preserves most original parameters and trains a **small number of task-specific parameters or adapter layers**.

---

### **5. LoRA**

**Trap:** LoRA replaces the original foundation-model weights.

**Correct:** LoRA **preserves/freezes the original weights** and adds trainable low-rank matrices.

---

### **6. PEFT/LoRA vs. ReFT**

**Trap:** PEFT, LoRA, and ReFT all modify the same part of the model.

**Correct:**

- **PEFT/LoRA →** modify weights.
    
- **ReFT →** learns interventions on hidden representations while freezing the base model.
    

---

### **7. Catastrophic Forgetting**

**Trap:** Catastrophic forgetting means the model performs worse on the task it was fine-tuned for.

**Correct:** It occurs when task-specific fine-tuning **improves the target task but degrades performance on other previously learned tasks**.

---

### **8. Single-Task Fine-Tuning**

**Trap:** Catastrophic forgetting is always unacceptable.

**Correct:** If the application only requires reliable performance on a **single task**, degradation of other capabilities may not be a major concern.

---

### **9. Multitask Fine-Tuning**

**Trap:** Multitask fine-tuning means training multiple independent models.

**Correct:** It uses one model with training examples for **multiple tasks**, producing an instruction-tuned model capable of performing those tasks.

---

### **10. Domain Adaptation**

**Trap:** Domain adaptation fine-tuning requires rebuilding the foundation model from scratch.

**Correct:** It uses a **pre-trained foundation model** and adapts it using limited domain-specific data.

---

### **11. RLHF**

**Trap:** RLHF means simply adding more labeled examples for supervised fine-tuning.

**Correct:** RLHF uses **reinforcement learning with human feedback data** to better align the model with human preferences.

---

### **12. Training Resources**

**Trap:** GPU memory during fine-tuning is needed only for the model parameters.

**Correct:** The transcript identifies additional memory requirements for the **optimizer, gradients, forward activations, and temporary memory**, increasing resource and compute requirements.

---

### **13. Larger Model = Always Better**

**Trap:** A larger model automatically eliminates the need for fine-tuning.

**Correct:** The transcript states that foundation models may still need additional training/instructions for **specific domains, datasets, human tasks, or reasoning**.

---

# 📝 Exam Questions

### **Q1.**

An organization wants to adapt a pre-trained foundation model to understand specialized terminology used in the medical-device industry. The organization has a relatively small dataset containing industry-specific examples.

Which fine-tuning approach from the transcript is most directly suited to this requirement?

**A.** Full fine-tuning using the original foundation-model training corpus  
**B.** Domain adaptation fine-tuning using domain-specific data  
**C.** Multitask fine-tuning using unrelated general-purpose tasks  
**D.** Pre-training using a large unstructured internet-scale dataset

**Answer: B**

**Why:** Domain adaptation fine-tuning adapts a pre-trained model using **limited domain-specific data**, such as specialized terminology.

---

### **Q2.**

A company wants to adapt a large language model to a specific task but has limited GPU memory. The engineers want to preserve most of the original model parameters and train only a small task-specific component.

Which approach best matches the requirement?

**A.** Full fine-tuning  
**B.** PEFT  
**C.** Pre-training  
**D.** Continuous pre-training

**Answer: B**

**Why:** **PEFT** preserves/freezes most original parameters and trains a small number of task-specific parameters, reducing memory and compute requirements.

---

### **Q3.**

An ML team performs full fine-tuning on a foundation model. Which statement accurately describes what happens?

**A.** Only newly added adapter parameters are updated.  
**B.** Only hidden representations are modified while weights remain frozen.  
**C.** Every parameter in the model is updated through supervised learning.  
**D.** The model is trained from scratch using unlabeled data.

**Answer: C**

**Why:** The transcript explicitly defines **full fine-tuning** as updating every parameter through supervised learning.

---

### **Q4.**

A team uses LoRA to specialize a transformer-based foundation model. The team wants to preserve the original model while introducing a small number of trainable components.

Which mechanism is consistent with LoRA?

**A.** Replace all original weights with newly initialized weights.  
**B.** Freeze the original weights and introduce trainable low-rank matrices.  
**C.** Retrain the model from scratch using unstructured data.  
**D.** Modify only the model's hidden representations without adding trainable matrices.

**Answer: B**

**Why:** LoRA preserves/freezes the original weights and creates **trainable low-rank matrices** in transformer layers.

---

### **Q5.**

A foundation model performs many tasks well. After being fine-tuned heavily for a single specialized task, its performance on several other tasks decreases.

Which phenomenon does this describe?

**A.** Domain adaptation  
**B.** Catastrophic forgetting  
**C.** Representation fine-tuning  
**D.** Continuous pre-training

**Answer: B**

**Why:** **Catastrophic forgetting** occurs when task-specific fine-tuning improves the target task while degrading previously learned capabilities.

---

### **Q6.**

An organization wants one model to perform summarization, translation, code-related tasks, and review classification. Its training dataset contains labeled input/output examples for all of these tasks.

Which approach is most appropriate according to the transcript?

**A.** Single-task fine-tuning  
**B.** Multitask fine-tuning  
**C.** Full pre-training  
**D.** Domain adaptation using only one task

**Answer: B**

**Why:** **Multitask fine-tuning** uses examples for multiple tasks and can produce an instruction-tuned model capable of performing them.

---

### **Q7.**

An engineer wants to adapt a foundation model while keeping its base parameters frozen. Instead of adding trainable weight matrices, the engineer learns task-specific interventions on hidden representations.

Which technique is being used?

**A.** LoRA  
**B.** PEFT  
**C.** ReFT  
**D.** Full fine-tuning

**Answer: C**

**Why:** **ReFT** freezes the base model and learns task-specific interventions on **hidden representations**.

---

### **Q8.**

A company is building a new foundation model and plans to train it using enormous amounts of unstructured data with a self-supervised learning approach.

Which stage is being described?

**A.** Fine-tuning  
**B.** Domain adaptation  
**C.** Pre-training  
**D.** RLHF

**Answer: C**

**Why:** **Pre-training** uses huge amounts of unstructured data with self-supervised learning to develop general model capabilities.

---

### **Q9.**

A team wants its model to better align with human preferences. Instead of relying solely on labeled examples for supervised fine-tuning, it plans to use human feedback with reinforcement learning.

Which technique should the team use?

**A.** LoRA  
**B.** RLHF  
**C.** ReFT  
**D.** Domain adaptation

**Answer: B**

**Why:** **RLHF** uses reinforcement learning with human feedback data to better align the LLM with human preferences.

---

### **Q10.**

An engineering team is estimating the GPU memory required for full fine-tuning. They initially account only for storing the model parameters.

Which additional resources identified in the transcript should they consider?

**A.** Only the tokenizer and inference endpoint  
**B.** Optimizer, gradients, forward activations, and temporary memory  
**C.** Only the model's training dataset  
**D.** Only additional inference prompts

**Answer: B**

**Why:** The transcript identifies memory requirements for the **optimizer, gradients, forward activations, and temporary memory** in addition to model parameters.

---

# ⚡ 30-Second Revision

**1. Three training elements →** **Pre-training + Fine-tuning + Continuous pre-training.**

**2. Pre-training →** huge unstructured data + **self-supervised learning** + general capabilities.

**3. Fine-tuning →** labeled examples + **supervised learning** + task-specific adaptation.

**4. Full fine-tuning →** **every parameter updated**.

**5. PEFT →** freeze/preserve most parameters + train small task-specific components.

**6. LoRA →** PEFT technique using **trainable low-rank matrices**.

**7. PEFT/LoRA →** modify **weights**, not representations.

**8. ReFT →** freeze base model + intervene on **hidden representations**.

**9. Single-task fine-tuning →** specialization but possible **catastrophic forgetting**.

**10. Multitask fine-tuning →** multiple tasks + labeled examples → instruction-tuned model.

**11. Domain adaptation →** specialized domain language/data + limited domain-specific data.

**12. RLHF →** reinforcement learning + human feedback → human-preference alignment.

**13. Full fine-tuning memory →** parameters + optimizer + gradients + activations + temporary memory.

**14. Core distinction →** **Pre-training creates general capabilities; fine-tuning adapts them; PEFT reduces adaptation cost; ReFT works on representations.**