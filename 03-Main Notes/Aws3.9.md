# Task Statement 3.4 — Describe Methods to Evaluate Foundation Model Performance

## 🎯 Exam Essentials

### **1. Deployment Evaluation Starts With Application Requirements**

- **Concept:** Before integrating a foundation model, determine how it needs to function in deployment.
    
- **Key distinction:** Important considerations include **completion speed, compute budget, model performance, inference speed, and storage**.
    
- **Exam trigger:** Scenario asks what to consider before deployment → think **latency + compute + storage + performance tradeoffs**.
    

---

### **2. Inference Tradeoffs**

- **Concept:** Organizations may need to trade model performance for faster inference or lower resource requirements.
    
- **Key distinction:** A more capable/larger model may consume more compute and storage, while a smaller model can improve efficiency.
    
- **Exam trigger:** **Faster inference / lower storage vs model quality → optimization tradeoff.**
    

---

### **3. Deployment Environment Creates Inference Challenges**

- **Concept:** LLM deployment can occur on-premises, in the cloud, or on edge devices.
    
- **Key distinction:** The environment affects **compute, storage, and latency requirements**.
    
- **Exam trigger:** Edge deployment + limited resources + latency requirements → consider model optimization.
    

---

### **4. Reducing Model Size**

- **Concept:** Reducing the size of an LLM can improve inference performance.
    
- **Key distinction:** Smaller models generally load faster, potentially reducing inference latency, but **model performance can decrease**.
    
- **Exam trigger:** **Smaller model → faster loading/lower latency, but possible performance loss.**
    

---

### **5. Prompt Optimization**

- **Concept:** A more concise prompt can reduce the amount of information the model needs to process.
    
- **Key distinction:** Prompt size is itself an optimization factor.
    
- **Exam trigger:** If the problem is inference efficiency and the prompt contains unnecessary content → **make the prompt more concise**.
    

---

### **6. Retrieved-Context Optimization**

- **Concept:** Reduce both the **size and number of retrieved snippets** supplied to the model.
    
- **Key distinction:** This can improve application performance while retaining relevant contextual information.
    
- **Exam trigger:** RAG application with excessive retrieved context → **reduce snippet size/number**.
    

---

### **7. Generation Optimization**

- **Concept:** Generation can be reduced through inference parameters and prompt design.
    
- **Key distinction:** Optimization can affect the balance between **accuracy and performance**.
    
- **Exam trigger:** Need to reduce generated output or inference workload → consider **generation controls/inference parameters**.
    

---

### **8. Deterministic vs. Generative AI Evaluation**

- **Concept:** Traditional ML metrics such as accuracy and RMSE are easier to calculate when predictions are deterministic and can be directly compared with labels.
    
- **Key distinction:** Generative AI output is **non-deterministic**, making evaluation more difficult.
    
- **Exam trigger:** **Deterministic prediction → conventional metrics are straightforward; generative output → task-specific evaluation is often needed.**
    

---

### **9. ROUGE**

- **Concept:** ROUGE is a set of metrics/software package used for evaluating automatic summarization and machine translation in NLP.
    
- **Key distinction:** It evaluates how well the input/reference compares with the generated output.
    
- **Exam trigger:** **Summarization → ROUGE.**
    

---

### **10. BLEU**

- **Concept:** BLEU is an algorithm used for translation tasks.
    
- **Key distinction:** It evaluates the quality of machine-translated text between natural languages.
    
- **Exam trigger:** **Machine translation → BLEU.**
    

---

### **11. GLUE**

- **Concept:** GLUE is a benchmark containing multiple natural-language tasks.
    
- **Key distinction:** It was created to help evaluate how well models **generalize across multiple language tasks**.
    
- **Exam trigger:** **Multiple general language tasks → GLUE.**
    

---

### **12. SuperGLUE**

- **Concept:** SuperGLUE extends the benchmark approach with additional challenging tasks.
    
- **Key distinction:** The transcript specifically mentions **multi-sentence reasoning and reading comprehension**.
    
- **Exam trigger:** **GLUE + additional reasoning/reading-comprehension tasks → SuperGLUE.**
    

---

### **13. MMLU**

- **Concept:** Massive Multitask Language Understanding evaluates model knowledge and problem-solving capabilities.
    
- **Key distinction:** It goes beyond basic language understanding and covers domains such as **history, mathematics, law, and computer science**.
    
- **Exam trigger:** **Broad world knowledge + problem solving across subjects → MMLU.**
    

---

### **14. BIG-bench**

- **Concept:** Beyond the Imitation Game Benchmark evaluates models on a broad collection of challenging tasks.
    
- **Key distinction:** Tasks include **math, biology, physics, bias, linguistics, reasoning, childhood development, and software development**.
    
- **Exam trigger:** **Broad/challenging tasks designed beyond current model capabilities → BIG-bench.**
    

---

### **15. HELM**

- **Concept:** Holistic Evaluation of Language Models is a benchmark designed to improve model transparency.
    
- **Key distinction:** It combines multiple metrics across tasks such as **summarization, question answering, sentiment analysis, and bias detection**.
    
- **Exam trigger:** **Holistic evaluation + transparency + multiple metrics → HELM.**
    

---

### **16. Human Evaluation**

- **Concept:** Human workers can manually evaluate model responses.
    
- **Key distinction:** Humans can compare responses from SageMaker JumpStart models and, according to the transcript, models outside AWS.
    
- **Exam trigger:** When automated metrics do not adequately capture response quality → **human evaluation** can be used.
    

---

### **17. SageMaker Clarify for LLM Evaluation**

- **Concept:** SageMaker Clarify can evaluate LLMs and create model evaluation jobs.
    
- **Key distinction:** The transcript associates model evaluation jobs with evaluating and comparing **quality and metrics for text-based foundation models from SageMaker JumpStart**.
    
- **Exam trigger:** **SageMaker JumpStart text FMs + evaluation job → SageMaker Clarify.**
    

---

### **18. Amazon Bedrock Evaluation**

- **Concept:** Amazon Bedrock provides an evaluation module for comparing generated responses.
    
- **Key distinction:** The transcript states that it can calculate a **semantic similarity-based score, BERTScore**, against a human reference.
    
- **Exam trigger:** **Bedrock + generated response vs human reference + BERTScore → Bedrock evaluation.**
    

---

### **19. Evaluating Faithfulness and Hallucinations**

- **Concept:** The Bedrock evaluation capability described can be used for text-generation tasks involving **faithfulness and hallucinations**.
    
- **Key distinction:** The evaluation compares generated responses against a human reference using the described semantic-similarity approach.
    
- **Exam trigger:** **Text generation + hallucination/faithfulness evaluation → Bedrock evaluation module.**
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Inference latency**|Time required for the model to generate a response|
|**Model optimization**|Techniques used to improve performance/resource efficiency|
|**ROUGE**|Metrics used for tasks such as automatic summarization|
|**BLEU**|Algorithm used to evaluate machine translation|
|**GLUE**|Benchmark for evaluating generalization across multiple language tasks|
|**SuperGLUE**|Extended benchmark with more challenging language tasks|
|**MMLU**|Benchmark for knowledge and problem-solving across many subjects|
|**BIG-bench**|Broad benchmark containing challenging tasks beyond basic language capabilities|
|**HELM**|Holistic benchmark focused on model evaluation and transparency|
|**Human evaluation**|Manual assessment/comparison of model responses|
|**BERTScore**|Semantic similarity-based score against a human reference, as described|
|**Faithfulness**|Evaluation concern related to whether generated text is supported/correct relative to the reference/context|
|**Hallucination**|Incorrect/unsupported generated information; evaluated here using the described Bedrock approach|
|**Model evaluation job**|SageMaker Clarify mechanism for evaluating model quality/metrics|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**ROUGE**|Summarization|Evaluates generated output against reference/input text|
|**BLEU**|Machine translation|Evaluates machine-translated text|
|**GLUE**|General language-task evaluation|Measures generalization across multiple language tasks|
|**SuperGLUE**|More challenging language evaluation|Adds tasks such as multi-sentence reasoning and reading comprehension|
|**MMLU**|Knowledge/problem-solving evaluation|Tests many academic/professional subject areas|
|**BIG-bench**|Broad challenging evaluation|Covers diverse tasks beyond basic language understanding|
|**HELM**|Holistic evaluation/transparency|Combines multiple metrics across multiple tasks|
|**Human evaluation**|Manual response assessment|Humans directly judge/compare generated responses|
|**SageMaker Clarify**|Evaluate JumpStart text FMs|Creates model evaluation jobs|
|**Amazon Bedrock evaluation**|Evaluate generated text|Can compare responses and calculate BERTScore against human reference|

---

## 🧠 Exam Traps

### **1. Trap: Using accuracy for every generative AI task**

**Correct:** Accuracy is straightforward when deterministic predictions can be directly compared with labels. Generative AI is non-deterministic, so evaluation is more difficult and often task-specific.

---

### **2. Trap: Confusing ROUGE and BLEU**

**Correct:**  
**ROUGE → summarization**  
**BLEU → machine translation**

---

### **3. Trap: Choosing MMLU because the scenario mentions language**

**Correct:** MMLU is specifically associated with **knowledge and problem-solving across many subjects**, including mathematics, history, law, and computer science.

---

### **4. Trap: Confusing GLUE with MMLU**

**Correct:**  
**GLUE → generalization across multiple language tasks.**  
**MMLU → broad knowledge + problem-solving across subjects.**

---

### **5. Trap: Assuming BIG-bench only evaluates mathematics**

**Correct:** BIG-bench contains diverse tasks including biology, physics, bias, linguistics, reasoning, childhood development, and software development.

---

### **6. Trap: Assuming HELM is a single metric**

**Correct:** HELM is described as a **benchmark combining multiple metrics** across multiple tasks.

---

### **7. Trap: Assuming a smaller model always performs better**

**Correct:** Reducing model size can reduce inference latency, but it **might decrease model performance**.

---

### **8. Trap: Optimizing only the model itself**

**Correct:** Application performance can also be improved through **more concise prompts, smaller/fewer retrieved snippets, and reduced generation**.

---

### **9. Trap: Confusing SageMaker Clarify with Bedrock evaluation**

**Correct:** In this lesson:

- **SageMaker Clarify → model evaluation jobs for text-based SageMaker JumpStart FMs**
    
- **Bedrock evaluation → compare generated responses and calculate semantic similarity/BERTScore against a human reference**
    

---

### **10. Trap: Assuming automated metrics completely replace humans**

**Correct:** Human workers can manually evaluate and compare model responses, including responses from SageMaker JumpStart and models outside AWS.

---

### **11. Trap: Treating latency and model quality as independent**

**Correct:** Model optimization often involves a **tradeoff between accuracy/performance and inference efficiency**.

---

### **12. Trap: Assuming more retrieved context is always better**

**Correct:** The transcript specifically identifies reducing the **size and number of retrieved snippets** as an optimization technique.

---

## # 📝 Exam Questions

### **Q1.**

A company deploys an LLM-powered application to edge devices with limited compute and storage. Users also require fast responses. The team wants to improve inference latency while accepting a possible reduction in model quality. Which approach most directly matches the lesson?

**A.** Increase the number of retrieved snippets so the model has more contextual information.  
**B.** Reduce the size of the deployed model to allow it to load more quickly.  
**C.** Replace the model evaluation benchmark with human evaluation.  
**D.** Increase the prompt length to provide additional task context.

**Answer: B**

**Why:** Reducing model size can improve loading speed and inference latency, although it may reduce model performance.

---

### **Q2.**

An organization evaluates an LLM used specifically to generate summaries. The generated summaries are compared with reference text using a task-specific evaluation metric. Which metric from the lesson is most directly associated with this task?

**A.** BLEU  
**B.** MMLU  
**C.** ROUGE  
**D.** GLUE

**Answer: C**

**Why:** **ROUGE** is associated with automatic summarization evaluation.

---

### **Q3.**

A research team wants to compare several LLMs across a broad collection of subjects, including mathematics, history, law, and computer science. The goal is to assess both knowledge and problem-solving capabilities. Which benchmark best matches this requirement?

**A.** GLUE  
**B.** MMLU  
**C.** HELM  
**D.** BLEU

**Answer: B**

**Why:** **MMLU** evaluates broad knowledge and problem-solving across many subject areas.

---

### **Q4.**

An engineering team observes that its RAG application spends significant time processing context returned by retrieval. The retrieved results contain many large snippets, several of which are unnecessary. Which optimization is most directly supported by the lesson?

**A.** Increase model size to improve contextual reasoning.  
**B.** Increase the number of retrieved snippets to improve recall.  
**C.** Reduce the size and number of retrieved snippets.  
**D.** Replace the evaluation benchmark with GLUE.

**Answer: C**

**Why:** The lesson explicitly identifies reducing the **size and number of retrieved snippets** as an application optimization technique.

---

### **Q5.**

A company wants to evaluate whether its model generalizes across multiple natural-language tasks, including sentiment analysis and question answering. Which benchmark from the lesson was specifically created for this purpose?

**A.** GLUE  
**B.** MMLU  
**C.** BIG-bench  
**D.** HELM

**Answer: A**

**Why:** **GLUE** contains multiple natural-language tasks and was created to help evaluate generalization across tasks.

---

### **Q6.**

An organization wants an evaluation framework that combines multiple metrics and covers tasks such as summarization, question answering, sentiment analysis, and bias detection, with an emphasis on model transparency. Which benchmark should the team consider?

**A.** SuperGLUE  
**B.** HELM  
**C.** BLEU  
**D.** MMLU

**Answer: B**

**Why:** **HELM** is described as a holistic benchmark combining metrics across these types of tasks and supporting transparency.

---

### **Q7.**

A team evaluates several text-based foundation models from SageMaker JumpStart and wants to create formal model evaluation jobs to compare model quality and metrics. Which AWS capability described in the lesson should they use?

**A.** Amazon SageMaker Clarify  
**B.** Amazon SageMaker Feature Store  
**C.** Amazon Bedrock evaluation module  
**D.** Amazon SageMaker Ground Truth

**Answer: A**

**Why:** The lesson specifically associates **SageMaker Clarify model evaluation jobs** with evaluating and comparing SageMaker JumpStart text-based foundation models.

---

### **Q8.**

A team wants to evaluate generated text by comparing model responses against a human reference and calculating a semantic-similarity-based BERTScore. Which capability described in the lesson matches this requirement?

**A.** SageMaker Clarify  
**B.** Amazon Bedrock evaluation module  
**C.** SageMaker Feature Store  
**D.** SuperGLUE

**Answer: B**

**Why:** The lesson explicitly associates **Amazon Bedrock's evaluation module** with generated-response comparison and BERTScore against a human reference.

---

### **Q9.**

A machine translation system generates text from English into another natural language. The team wants an evaluation algorithm specifically designed for machine translation quality. Which should they select?

**A.** ROUGE  
**B.** BLEU  
**C.** GLUE  
**D.** HELM

**Answer: B**

**Why:** **BLEU** is the translation-focused evaluation algorithm described in the lesson.

---

### **Q10.**

An organization wants to evaluate an LLM using a benchmark containing challenging tasks spanning mathematics, biology, physics, bias, linguistics, reasoning, and software development. Which benchmark best matches the description?

**A.** MMLU  
**B.** BIG-bench  
**C.** SuperGLUE  
**D.** ROUGE

**Answer: B**

**Why:** **BIG-bench** contains the broad and diverse set of challenging tasks described.

---

# ⚡ 30-Second Revision

1. **Deployment evaluation:** latency + compute + storage + model quality.
    
2. **Smaller model:** faster loading/lower latency, but potentially lower performance.
    
3. **Prompt optimization:** make prompts more concise.
    
4. **RAG optimization:** reduce retrieved snippet **size and number**.
    
5. **Generation optimization:** control generation through prompts/inference parameters.
    
6. **Deterministic ML:** accuracy/RMSE are easier to calculate.
    
7. **Generative AI:** non-deterministic → evaluation is harder and more task-specific.
    
8. **ROUGE → summarization.**
    
9. **BLEU → machine translation.**
    
10. **GLUE → generalization across language tasks.**
    
11. **SuperGLUE → harder language tasks, including reasoning/reading comprehension.**
    
12. **MMLU → knowledge + problem solving across many subjects.**
    
13. **BIG-bench → broad, challenging, diverse tasks.**
    
14. **HELM → holistic evaluation + multiple metrics + transparency.**
    
15. **Human evaluation → manually compare/judge model responses.**
    
16. **SageMaker Clarify → evaluation jobs for SageMaker JumpStart text FMs.**
    
17. **Bedrock evaluation → generated response vs human reference + BERTScore.**
    
18. **Faithfulness/hallucinations → Bedrock evaluation capability described in this lesson.**