# Task Statement 3.2 — Choose Effective Prompt Engineering Techniques

## 🎯 Exam Essentials

### **1. Prompt**

- **Concept:** A prompt is a specific set of inputs provided by the user to guide an LLM toward an appropriate response or output.
    
- **Purpose:** It communicates the task or instruction the LLM should perform.
    
- **Exam trigger:** **User input that guides an LLM toward a desired output → Prompt.**
    

---

### **2. Components of a Prompt**

- **Concept:** A prompt can contain multiple components depending on the task and available data.
    
- **Key components:**
    
    - **Task/instruction** — what the LLM should perform.
        
    - **Context** — information needed to understand the task.
        
    - **Input text** — text/data that the model should process.
        
- **Key distinction:** Not every prompt must contain every component.
    
- **Exam trigger:** If a question asks what information should be included in a prompt, consider **instruction + context + input**, depending on the use case.
    

---

### **3. Few-Shot Prompting**

- **Concept:** Few-shot prompting provides the LLM with **a few examples** of the desired task/output.
    
- **Purpose:** Helps the model better perform the task and **calibrate its output to expectations**.
    
- **Exam trigger:** **A few examples provided → Few-shot prompting.**
    

---

### **4. Zero-Shot Prompting**

- **Concept:** Zero-shot prompting performs a task **without providing examples** in the prompt.
    
- **Example from transcript:** Sentiment classification with no examples provided.
    
- **Exam trigger:** **No examples → Zero-shot.**
    

---

### **5. Few-Shot vs. Zero-Shot**

- **Few-shot:** Prompt contains a small number of examples.
    
- **Zero-shot:** Prompt contains **no examples**.
    
- **Exam trigger:** When a scenario emphasizes whether examples are supplied, distinguish **few-shot vs. zero-shot**.
    

---

### **6. Prompt Templates**

- **Concept:** Prompt templates provide a reusable structure for prompts across different use cases.
    
- **May include:**
    
    - Instructions
        
    - Few-shot examples
        
    - Specific content
        
    - Questions
        
- **Purpose:** Adapt a consistent prompt structure to different inputs/use cases.
    
- **Exam trigger:** If the same prompt structure needs to be reused with different content, consider a **prompt template**.
    

---

### **7. Chain-of-Thought Prompting**

- **Concept:** Chain-of-thought prompting can be used for more complex tasks by breaking the reasoning process into **intermediate steps**.
    
- **Purpose:** The transcript states that this can improve the **quality and coherence** of the final output.
    
- **Exam trigger:** **Complex task + intermediate reasoning steps → Chain-of-thought prompting.**
    

---

### **8. Prompt Tuning**

- **Concept:** Prompt tuning replaces the actual prompt text with a **continuous embedding vector** that is optimized during training.
    
- **Key distinction:** The rest of the model parameters remain **frozen**.
    
- **Purpose:** Fine-tune prompting for a specific task while potentially being more efficient than full fine-tuning.
    
- **Exam trigger:** **Continuous embedding + optimized during training + model parameters frozen → Prompt tuning.**
    

---

### **9. Prompt Tuning vs. Full Fine-Tuning**

- **Prompt tuning:** Optimizes a continuous prompt embedding while keeping the rest of the model parameters frozen.
    
- **Full fine-tuning:** The transcript contrasts prompt tuning with full fine-tuning in terms of efficiency but does not provide further mechanics here.
    
- **Key distinction:** Prompt tuning changes the **prompt representation**, rather than updating all model parameters.
    
- **Exam trigger:** If the question says **"keep model parameters frozen while optimizing a prompt representation" → Prompt tuning.**
    

---

### **10. Prompt Engineering**

- **Concept:** AWS defines prompt engineering as the practice of **crafting and optimizing input prompts**.
    
- **Includes:** Selecting appropriate:
    
    - Words
        
    - Phrases
        
    - Sentences
        
    - Punctuation
        
    - Separator characters
        
- **Purpose:** Effectively use LLMs for a wide variety of applications.
    
- **Exam trigger:** If a scenario involves systematically improving the wording/structure of inputs to improve LLM responses, think **prompt engineering**.
    

---

### **11. Prompt Quality Affects Output Quality**

- **Concept:** The quality of prompts provided to an LLM can affect the quality of its responses.
    
- **Key consideration:** Prompt strategy depends on both the **task and the available data**.
    
- **Exam trigger:** If two applications have different tasks/data, do not assume they should use identical prompting strategies.
    

---

### **12. Common LLM Tasks**

The transcript identifies several tasks that LLMs on Amazon Bedrock can support:

- **Classification**
    
- **Question answering with context**
    
- **Question answering without context**
    
- **Summarization**
    
- **Open-ended text generation**
    
- **Code generation**
    
- **Math**
    
- **Reasoning / logical thinking**
    
- **Exam trigger:** When given an application requirement, identify which LLM task it represents.
    

---

### **13. Latent Space**

- **Concept:** The transcript describes latent space as the **encoded knowledge of language in an LLM**.
    
- **Description given:** It represents stored patterns of data that capture relationships and can be used to reconstruct/generate language when prompted.
    
- **Exam trigger:** **Encoded knowledge/patterns and relationships used by the model to generate outputs → Latent space.**
    

---

### **14. Latent Space Is Not the Same as an External Database**

- **Concept:** The transcript uses a "database of statistics" as an analogy for latent space.
    
- **Important distinction:** The analogy is describing **stored patterns/relationships learned by the model**, rather than an ordinary external database that the model queries.
    
- **Exam trigger:** If the scenario describes knowledge encoded within the model itself, think **latent space**; if it describes an external repository being queried, think **knowledge base/vector database**.
    

---

### **15. Prompting Strategy Depends on Task and Data**

- **Concept:** There is no single prompting strategy that is appropriate for every application.
    
- **Key factors:** The appropriate strategy depends on:
    
    - The **task**
        
    - The **available data**
        
- **Exam trigger:** If a scenario changes the task or available contextual data, reconsider the prompting technique rather than automatically reusing the same approach.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Prompt**|User-provided input that guides an LLM toward a desired response/output|
|**Prompt engineering**|Crafting and optimizing input prompts to effectively use LLMs|
|**Prompt component**|Part of a prompt such as instruction, context, or input text|
|**Instruction**|Describes the task the LLM should perform|
|**Context**|Information that helps the LLM understand the task|
|**Input text**|Text/data that the model should process|
|**Few-shot prompting**|Providing a few examples to guide/calibrate the model's output|
|**Zero-shot prompting**|Performing a task without providing examples|
|**Prompt template**|Reusable prompt structure that can contain instructions, examples, content, and questions|
|**Chain-of-thought prompting**|Breaking complex reasoning into intermediate steps|
|**Prompt tuning**|Optimizing a continuous prompt embedding while keeping model parameters frozen|
|**Latent space**|Encoded model knowledge/patterns representing relationships used to generate outputs|
|**Classification**|Assigning input to categories/classes|
|**Summarization**|Producing a condensed representation of input information|
|**Open-ended generation**|Generating unrestricted text based on a prompt|
|**Code generation**|Generating code from instructions/input|
|**Reasoning**|Performing logical thinking to solve a task|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Zero-shot prompting**|No examples are provided|Model performs the task from the instruction alone|
|**Few-shot prompting**|A few examples can guide the model|Examples calibrate the expected output|
|**Prompt template**|Prompt structure needs to be reused|Provides a reusable structure containing instructions/examples/content/questions|
|**Chain-of-thought prompting**|Task requires complex reasoning|Breaks reasoning into intermediate steps|
|**Prompt tuning**|Prompt needs task-specific optimization|Optimizes continuous prompt embeddings while model parameters remain frozen|
|**Prompt engineering**|Improving LLM behavior through input design|Crafts/optimizes words, phrases, punctuation, separators, etc.|
|**Latent space**|Model needs to use learned patterns/relationships|Represents knowledge encoded within the model|
|**External knowledge base**|Model needs external/contextual information|Information exists outside the model and can be supplied to it|

---

## 🧠 Exam Traps

### **1. Few-Shot vs. Zero-Shot**

**Trap:** Few-shot prompting means providing one example.

**Correct:** The transcript defines few-shot prompting as providing **a few examples**. Zero-shot provides **no examples**.

---

### **2. Zero-Shot Means No Instructions**

**Trap:** Zero-shot prompting means giving the model no instructions.

**Correct:** Zero-shot means **no examples are provided**. The prompt can still contain an instruction/task.

---

### **3. Prompt Template**

**Trap:** A prompt template is simply one fixed prompt that cannot change.

**Correct:** A template provides a **reusable structure** that can include instructions, examples, content, and questions for different use cases.

---

### **4. Chain-of-Thought**

**Trap:** Chain-of-thought is primarily about adding more examples to a prompt.

**Correct:** The transcript associates it with **breaking complex reasoning into intermediate steps**.

---

### **5. Prompt Tuning**

**Trap:** Prompt tuning means rewriting the prompt manually until the output improves.

**Correct:** The transcript describes prompt tuning as replacing prompt text with a **continuous embedding vector optimized during training**.

---

### **6. Frozen Model Parameters**

**Trap:** Prompt tuning requires updating all foundation-model parameters.

**Correct:** Prompt tuning keeps the **rest of the model parameters frozen**.

---

### **7. Prompt Engineering vs. Prompt Tuning**

**Trap:** Prompt engineering and prompt tuning are identical techniques.

**Correct:** Prompt engineering involves **crafting/optimizing input prompts**; prompt tuning optimizes a **continuous prompt embedding during training** while keeping model parameters frozen.

---

### **8. Latent Space**

**Trap:** Latent space is an external database that the LLM queries during inference.

**Correct:** The transcript describes latent space as **encoded knowledge/patterns within the model**.

---

### **9. Prompt Components**

**Trap:** Every prompt must contain task, context, and input text.

**Correct:** The transcript says a prompt should combine **one or more** of these components depending on the use case, data availability, and task.

---

### **10. Same Prompting Strategy Everywhere**

**Trap:** One prompting technique should be used for every LLM application.

**Correct:** Prompt engineering strategy depends on the **task and available data**.

---

### **11. Prompt Quality**

**Trap:** Prompt wording has little effect on the model's output.

**Correct:** The transcript states that **prompt quality can affect response quality**.

---

### **12. Latent Space vs. Vector Database**

**Trap:** The "database of statistics" analogy means latent space is literally an external database.

**Correct:** In the transcript's framing, latent space represents **encoded patterns and relationships learned by the model**, whereas a vector database is an external storage/retrieval system.

---

# 📝 Exam Questions

### **Q1.**

An application asks an LLM to classify customer reviews as positive, neutral, or negative. The prompt contains the classification instruction but provides no example reviews or expected classifications.

Which prompting approach is being used?

**A.** Few-shot prompting  
**B.** Zero-shot prompting  
**C.** Prompt tuning  
**D.** Chain-of-thought prompting

**Answer: B**

**Why:** The prompt provides **no examples**, which is the defining characteristic of zero-shot prompting in the transcript.

---

### **Q2.**

A developer wants an LLM to perform a classification task and provides several example inputs together with their expected outputs before presenting the actual input.

Which technique is being used?

**A.** Zero-shot prompting  
**B.** Few-shot prompting  
**C.** Prompt tuning  
**D.** Latent-space retrieval

**Answer: B**

**Why:** Providing **a few examples** to calibrate the model's expected output is few-shot prompting.

---

### **Q3.**

A team needs to repeatedly use the same general prompt structure for different customer requests. The structure contains an instruction, several examples, variable content, and a question.

Which approach best describes this design?

**A.** Prompt template  
**B.** Zero-shot prompting  
**C.** Latent-space encoding  
**D.** Model fine-tuning

**Answer: A**

**Why:** A prompt template provides a **reusable structure** that can contain instructions, examples, content, and questions.

---

### **Q4.**

An application needs an LLM to solve a complex reasoning task. The team designs the prompt so the model works through the problem using intermediate reasoning steps before producing its final output.

Which technique does this scenario describe?

**A.** Few-shot prompting  
**B.** Prompt tuning  
**C.** Chain-of-thought prompting  
**D.** Zero-shot classification

**Answer: C**

**Why:** The transcript associates chain-of-thought prompting with **breaking complex tasks into intermediate steps**.

---

### **Q5.**

An ML team wants to specialize a model for a particular task. Instead of updating the model's existing parameters, they optimize a continuous embedding representation of the prompt while keeping the model parameters frozen.

Which technique is being used?

**A.** Few-shot prompting  
**B.** Prompt tuning  
**C.** Chain-of-thought prompting  
**D.** Prompt templating

**Answer: B**

**Why:** This is the defining mechanism of **prompt tuning** described in the transcript.

---

### **Q6.**

Two teams are designing LLM applications. Team A focuses on selecting appropriate words, punctuation, phrases, sentences, and separators in the input. Team B optimizes a continuous prompt embedding during training while keeping model parameters frozen.

Which distinction is correct?

**A.** Team A uses prompt engineering; Team B uses prompt tuning.  
**B.** Team A uses prompt tuning; Team B uses few-shot prompting.  
**C.** Team A uses zero-shot prompting; Team B uses prompt templates.  
**D.** Team A uses chain-of-thought; Team B uses zero-shot prompting.

**Answer: A**

**Why:** The transcript defines **prompt engineering** around crafting/optimizing input prompts and **prompt tuning** around optimizing continuous prompt embeddings.

---

### **Q7.**

An LLM application must generate a response using patterns and relationships encoded within the model itself. No external knowledge repository is queried during the process.

Which concept from the transcript most closely describes the model's encoded knowledge?

**A.** Vector database  
**B.** Latent space  
**C.** Prompt template  
**D.** Knowledge base

**Answer: B**

**Why:** The transcript describes latent space as the **encoded knowledge and stored patterns/relationships within the LLM**.

---

### **Q8.**

A developer designs a prompt for a question-answering application. Depending on the use case, the prompt may contain the task instruction, relevant context, and the input question.

Which statement best reflects the transcript?

**A.** Every prompt must contain all three components.  
**B.** Prompts should contain only the input text because instructions are implicit.  
**C.** Prompts can combine one or more components depending on the task and available data.  
**D.** Context can only be included through model fine-tuning.

**Answer: C**

**Why:** The transcript explicitly states that prompts can combine **one or more components** depending on the task and data availability.

---

### **Q9.**

A company uses an LLM for two applications. One performs summarization, while another performs code generation. The team plans to use exactly the same prompting strategy for both applications.

What should the team consider?

**A.** Prompting strategy should depend on the task and available data.  
**B.** All LLM applications should use few-shot prompting.  
**C.** Code generation always requires zero-shot prompting.  
**D.** Prompt strategy is independent of the underlying task.

**Answer: A**

**Why:** The transcript states that the prompt-engineering strategy depends on **both the task and the data**.

---

### **Q10.**

An organization wants to improve the quality of an LLM's responses without changing the underlying model. The team begins systematically refining the wording, punctuation, phrases, and structure of the inputs.

Which practice does this represent?

**A.** Prompt engineering  
**B.** Prompt tuning  
**C.** Full model fine-tuning  
**D.** Vector indexing

**Answer: A**

**Why:** AWS defines prompt engineering as **crafting and optimizing input prompts**, including words, phrases, punctuation, and separators.

---

# ⚡ 30-Second Revision

**1. Prompt →** input that guides an LLM.

**2. Prompt components →** **instruction + context + input text** as applicable.

**3. Zero-shot →** **no examples**.

**4. Few-shot →** **a few examples**.

**5. Prompt template →** reusable prompt structure.

**6. Chain-of-thought →** intermediate reasoning steps for complex tasks.

**7. Prompt tuning →** optimize **continuous prompt embedding** while model parameters remain frozen.

**8. Prompt engineering →** craft/optimize words, phrases, punctuation, sentences, separators.

**9. Prompt quality →** can affect response quality.

**10. Strategy →** depends on **task + data**.

**11. LLM tasks →** classification, Q&A, summarization, text generation, code, math, reasoning.

**12. Latent space →** encoded knowledge/patterns and relationships within the model.

**13. Core distinction →** **Prompt engineering changes the input design; prompt tuning optimizes a continuous prompt representation during training.**