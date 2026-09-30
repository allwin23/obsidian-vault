# Task Statement 3.3 — Preparing Data for Foundation Model Fine-Tuning

## 🎯 Exam Essentials

### **1. Fine-Tuning Data Preparation**

- **Concept:** Prepare the training data before fine-tuning a foundation model.
    
- **Key distinction:** Data preparation involves collecting, preprocessing, and organizing raw data for the model.
    
- **Exam trigger:** If a question asks what happens **before fine-tuning**, think **data preparation → dataset creation → train/validation/test splits**.
    

---

### **2. Prompt Template Libraries**

- **Concept:** Publicly available prompt-template libraries provide templates for different tasks and datasets.
    
- **Key distinction:** Templates help structure the instruction dataset used for fine-tuning.
    
- **Exam trigger:** If the scenario asks how to structure prompts for different fine-tuning tasks, look for **prompt templates**.
    

---

### **3. Dataset Splitting**

- **Concept:** Once the instruction dataset is ready, divide it into **training, validation, and test datasets**.
    
- **Key distinction:** Each split has a different purpose:
    
    - Training → update model weights.
        
    - Validation → evaluate during/through the fine-tuning process.
        
    - Test → final performance evaluation.
        
- **Exam trigger:** **Final unbiased evaluation → holdout test dataset.**
    

---

### **4. Fine-Tuning Using Prompt–Completion Pairs**

- **Concept:** Prompts from the training dataset are passed to the LLM to generate completions.
    
- **Key distinction:** Generated completions are compared with the training labels to calculate loss.
    
- **Exam trigger:** **Prompt → completion → compare with label → loss → update weights.**
    

---

### **5. Loss and Weight Updates**

- **Concept:** The loss between the model's completion distribution and the training-label distribution is used to update model weights.
    
- **Key distinction:** Repeated batches progressively adjust the model toward better performance on the target task.
    
- **Exam trigger:** If asked what drives weight updates during supervised fine-tuning → **calculated loss**.
    

---

### **6. Validation vs. Test Evaluation**

- **Concept:** Validation data is used for evaluation during the fine-tuning process; the test dataset is used for the final performance evaluation.
    
- **Key distinction:** **Validation ≠ final test evaluation.**
    
- **Exam trigger:** **Final reported performance → holdout test dataset → test accuracy.**
    

---

### **7. Amazon SageMaker Canvas for Low-Code Preparation**

- **Concept:** SageMaker Canvas can create data flows for ML data preprocessing.
    
- **Key distinction:** Designed for **low-code/no-code-style data preparation and feature engineering workflows**.
    
- **Exam trigger:** **Low-code data preparation → SageMaker Canvas.**
    

---

### **8. Apache Spark, Hive, and Presto for Scalable Preparation**

- **Concept:** Open-source frameworks such as Apache Spark, Apache Hive, and Presto can be used when data preparation needs to scale.
    
- **Key distinction:** These are associated in the transcript with **large-scale data preparation**.
    
- **Exam trigger:** **Scalable data processing → Spark/Hive/Presto.**
    

---

### **9. SageMaker Studio Classic + Amazon EMR**

- **Concept:** SageMaker Studio Classic provides built-in integration with Amazon EMR.
    
- **Key distinction:** EMR provides access to distributed data-processing capabilities such as Spark.
    
- **Exam trigger:** **SageMaker Studio Classic + scalable processing → Amazon EMR.**
    

---

### **10. AWS Glue Interactive Sessions**

- **Concept:** AWS Glue interactive sessions provide a serverless Apache Spark-based engine for data preparation.
    
- **Key distinction:** The transcript associates this option specifically with **serverless** data preparation.
    
- **Exam trigger:** **Serverless Spark-based data preparation → AWS Glue interactive sessions.**
    

---

### **11. JupyterLab for SQL-Based Preparation**

- **Concept:** JupyterLab in SageMaker Studio can be used when SQL is required for data preparation.
    
- **Key distinction:** The transcript specifically connects **SQL-based preparation in SageMaker Studio** with JupyterLab.
    
- **Exam trigger:** **SQL in SageMaker Studio → JupyterLab.**
    

---

### **12. SageMaker Feature Store**

- **Concept:** Feature Store provides a centralized repository for feature data.
    
- **Key distinction:** It supports **feature discovery, retrieval, and standardized storage** for model training.
    
- **Exam trigger:** **Search/discover/retrieve/store ML features → SageMaker Feature Store.**
    

---

### **13. SageMaker Clarify for Bias Detection**

- **Concept:** SageMaker Clarify can analyze data to detect potential biases.
    
- **Key distinction:** It can identify issues such as **imbalanced representation and labeling bias** across groups.
    
- **Exam trigger:** **Training-data bias/fairness analysis → SageMaker Clarify.**
    

---

### **14. SageMaker Ground Truth for Data Labeling**

- **Concept:** Ground Truth manages data-labeling workflows for training datasets.
    
- **Key distinction:** It is about **creating/managing labeled training data**, not detecting bias.
    
- **Exam trigger:** **Need to label training data → SageMaker Ground Truth.**
    

---

### **15. Continuous Pre-Training**

- **Concept:** Continuous pre-training continues training a foundation model using additional data.
    
- **Key distinction:** Unlike task-specific fine-tuning, the transcript emphasizes using **unlabeled data across different topics, genres, and contexts** to expand model knowledge and adaptability.
    
- **Exam trigger:** **Broaden knowledge/adaptability using additional unlabeled data → continuous pre-training.**
    

---

### **16. Continuous Pre-Training and Generative AI Evaluation**

- **Concept:** Generative AI outputs are non-deterministic, making validation more difficult.
    
- **Key distinction:** Evaluation therefore requires carefully selected **metrics, benchmarks, and datasets**.
    
- **Exam trigger:** **Non-deterministic GenAI output + evaluation → appropriate metrics/benchmarks/datasets.**
    

---

### **17. Continuous Pre-Training and Broader Knowledge**

- **Concept:** Training across different topics, genres, and contexts can increase the model's knowledge and adaptability.
    
- **Key distinction:** The goal described here is broader capability rather than narrowly optimizing one task.
    
- **Exam trigger:** **Wider knowledge + adaptability → continuous pre-training.**
    

---

### **18. Amazon Bedrock Continuous Pre-Training**

- **Concept:** The transcript states that continuous pre-training in Amazon Bedrock can be used to customize Amazon Titan Text Express and Amazon Titan Text Lite FMs.
    
- **Key distinction:** The customization described uses **your own unlabeled data** in a secure, managed environment.
    
- **Exam trigger:** **Titan Text Express/Lite + own unlabeled data → continuous pre-training.**
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Instruction dataset**|Dataset containing task-oriented prompts/examples used for fine-tuning|
|**Training dataset**|Data used to calculate loss and update model weights|
|**Validation dataset**|Holdout data used to evaluate model performance during fine-tuning|
|**Test dataset**|Holdout data used for final performance evaluation|
|**Prompt–completion pair**|Input prompt paired with expected/target completion|
|**Loss**|Difference between model output distribution and training-label distribution|
|**Data preparation**|Collecting, preprocessing, and organizing raw data|
|**SageMaker Canvas**|Low-code data preparation and feature-engineering workflows|
|**Amazon EMR**|Integrated scalable data-processing option in SageMaker Studio Classic|
|**AWS Glue interactive sessions**|Serverless Apache Spark-based data-processing environment|
|**JupyterLab**|Environment associated in the transcript with SQL-based preparation|
|**SageMaker Feature Store**|Centralized repository for discovering and storing feature data|
|**SageMaker Clarify**|Detects potential bias in data|
|**SageMaker Ground Truth**|Manages data-labeling workflows|
|**Continuous pre-training**|Continued training using additional data to expand knowledge/adaptability|
|**Non-deterministic output**|GenAI output can vary, making evaluation/validation more difficult|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**SageMaker Canvas**|Low-code data preparation|Data flows + little/no coding|
|**Apache Spark / Hive / Presto**|Scalable data preparation|Large-scale processing frameworks|
|**AWS Glue interactive sessions**|Serverless data preparation|Serverless Apache Spark-based engine|
|**SageMaker Feature Store**|Feature discovery/storage|Centralized feature repository|
|**SageMaker Clarify**|Bias analysis|Detects potential data bias|
|**SageMaker Ground Truth**|Data labeling|Manages labeling workflows|
|**Validation dataset**|Evaluation during fine-tuning|Used before final test evaluation|
|**Test dataset**|Final evaluation|Holdout data for final performance|
|**Fine-tuning**|Improve performance on specific tasks|Uses task-specific training data and updates weights|
|**Continuous pre-training**|Broaden knowledge/adaptability|Uses additional data across topics/contexts; transcript specifies unlabeled data|

---

## 🧠 Exam Traps

### **1. Trap: Confusing validation and test datasets**

**Correct:** Validation data is used during the fine-tuning/evaluation process; the **holdout test dataset** provides the final performance evaluation.

---

### **2. Trap: Assuming training data directly becomes model weights**

**Correct:** Prompts generate completions → completions are compared with labels → loss is calculated → loss drives weight updates.

---

### **3. Trap: Using Ground Truth for bias detection**

**Correct:** **Ground Truth → data labeling.**  
**Clarify → bias analysis.**

---

### **4. Trap: Using Clarify to label data**

**Correct:** **SageMaker Clarify** analyzes data for potential bias; **Ground Truth** manages labeling workflows.

---

### **5. Trap: Confusing Feature Store with a general training dataset**

**Correct:** Feature Store focuses on **discovering, retrieving, and centrally storing feature data** in a standardized format.

---

### **6. Trap: Choosing Canvas for large-scale distributed processing**

**Correct:** The transcript associates **SageMaker Canvas** with low-code preparation. For scalable preparation, it points to frameworks such as **Spark, Hive, and Presto**.

---

### **7. Trap: Confusing Glue interactive sessions with EMR**

**Correct:** The key clue is **serverless Apache Spark-based engine → AWS Glue interactive sessions**.  
The transcript associates **SageMaker Studio Classic integration → Amazon EMR**.

---

### **8. Trap: Assuming continuous pre-training requires labeled task examples**

**Correct:** This transcript specifically describes continuous pre-training with **your own unlabeled data** for Titan Text Express/Lite.

---

### **9. Trap: Assuming continuous pre-training is simply another name for task-specific fine-tuning**

**Correct:** The transcript distinguishes the goals: fine-tuning improves a specific task, while continuous pre-training can broaden knowledge and adaptability across topics, genres, and contexts.

---

### **10. Trap: Ignoring evaluation difficulty in generative AI**

**Correct:** GenAI output is **non-deterministic**, so selecting appropriate **metrics, benchmarks, and datasets** is particularly important.

---

### **11. Trap: Thinking more training data automatically means better evaluation**

**Correct:** The transcript emphasizes selecting appropriate evaluation **metrics, benchmarks, and datasets**, including checking that the model does not produce harmful outputs.

---

## # 📝 Exam Questions

### **Q1.**

A team has completed an instruction dataset for fine-tuning an LLM. They want to determine the model's final performance after training is complete. Which approach best matches the described process?

**A.** Evaluate against the training dataset after each batch and report its accuracy.  
**B.** Evaluate against the validation dataset and use that result as the final accuracy.  
**C.** Evaluate against the holdout test dataset after fine-tuning is complete.  
**D.** Compare the prompt distribution with the validation distribution before training.

**Answer: C**

**Why:** The transcript explicitly distinguishes validation evaluation from the **final evaluation using the holdout test dataset**.

---

### **Q2.**

A company needs to prepare ML data using a serverless Apache Spark-based processing environment. Which option best matches the requirement?

**A.** SageMaker Canvas data flows  
**B.** AWS Glue interactive sessions  
**C.** SageMaker Feature Store  
**D.** SageMaker Ground Truth

**Answer: B**

**Why:** The key clue is **serverless + Apache Spark-based engine**.

---

### **Q3.**

During supervised fine-tuning, an LLM generates a completion for each training prompt. What happens next in the process described by the lesson?

**A.** The completion is stored in Feature Store and retrieved during inference.  
**B.** The completion is compared with the training label to calculate loss.  
**C.** The completion is sent to Ground Truth to determine whether it is biased.  
**D.** The completion replaces the foundation model's original training dataset.

**Answer: B**

**Why:** The generated completion is compared with the training label, producing a **loss used to update model weights**.

---

### **Q4.**

An ML team suspects that its training dataset contains unequal representation and labeling bias across demographic groups. Which AWS capability from the lesson directly addresses this requirement?

**A.** Amazon SageMaker Ground Truth  
**B.** Amazon SageMaker Feature Store  
**C.** Amazon SageMaker Clarify  
**D.** Amazon SageMaker Canvas

**Answer: C**

**Why:** **Clarify** is specifically associated with analyzing data for potential bias.

---

### **Q5.**

A team wants to create a centralized repository where standardized feature data can be discovered, retrieved, and stored for model training. Which service best fits?

**A.** SageMaker Feature Store  
**B.** SageMaker Ground Truth  
**C.** SageMaker Clarify  
**D.** SageMaker Canvas

**Answer: A**

**Why:** Feature discovery, retrieval, and centralized feature storage are the stated roles of **Feature Store**.

---

### **Q6.**

An organization wants to increase a foundation model's knowledge and adaptability by continually exposing it to data spanning different topics, genres, and contexts. Which approach best matches the lesson?

**A.** Single-task fine-tuning  
**B.** Continuous pre-training  
**C.** Holdout testing  
**D.** Feature engineering

**Answer: B**

**Why:** The lesson describes continuous pre-training as a way to accumulate wider knowledge and adaptability across different types of data.

---

### **Q7.**

A data scientist wants to prepare ML data with minimal coding by creating preprocessing and feature-engineering data flows. Which service should they consider based on the lesson?

**A.** Amazon EMR  
**B.** Amazon SageMaker Canvas  
**C.** AWS Glue interactive sessions  
**D.** Amazon SageMaker Ground Truth

**Answer: B**

**Why:** **Canvas** is the low-code data-preparation option described in the transcript.

---

### **Q8.**

A team has completed fine-tuning and wants to report its final model performance. Which dataset should remain untouched as a holdout until this stage?

**A.** Training dataset  
**B.** Prompt-template dataset  
**C.** Validation dataset  
**D.** Test dataset

**Answer: D**

**Why:** The transcript identifies the **holdout test dataset** as the source for final performance evaluation.

---

### **Q9.**

A company wants to customize Amazon Titan Text Express using its own unlabeled organizational data in a managed environment. Which approach is described in the lesson?

**A.** Continuous pre-training in Amazon Bedrock  
**B.** SageMaker Ground Truth labeling  
**C.** Validation-based fine-tuning  
**D.** SageMaker Feature Store retrieval

**Answer: A**

**Why:** The lesson specifically describes **continuous pre-training in Amazon Bedrock** for Titan Text Express and Titan Text Lite using **own unlabeled data**.

---

### **Q10.**

A team is designing an evaluation strategy for a generative AI model and notices that repeated runs can produce different outputs. Which implication is most directly supported by the lesson?

**A.** Validation should be eliminated because accuracy cannot be measured.  
**B.** The model should only be evaluated using its training dataset.  
**C.** Metrics, benchmarks, and datasets should be carefully selected to evaluate capabilities and harmful outputs.  
**D.** Continuous pre-training should always be replaced with supervised fine-tuning.

**Answer: C**

**Why:** The lesson connects **non-deterministic GenAI output** with the need for appropriate **metrics, benchmarks, and datasets**.

---

# ⚡ 30-Second Revision

1. **Fine-tuning preparation:** collect → preprocess → organize → create instruction dataset.
    
2. **Dataset split:** training → validation → test.
    
3. **Training loop:** prompt → completion → compare with label → loss → weight update.
    
4. **Validation:** evaluate during the fine-tuning process.
    
5. **Test:** final performance evaluation.
    
6. **Low-code preparation:** **SageMaker Canvas**.
    
7. **Scalable processing:** **Spark / Hive / Presto**.
    
8. **Serverless Spark:** **AWS Glue interactive sessions**.
    
9. **Feature discovery/storage:** **SageMaker Feature Store**.
    
10. **Bias detection:** **SageMaker Clarify**.
    
11. **Data labeling:** **SageMaker Ground Truth**.
    
12. **Continuous pre-training:** additional data → broader knowledge + adaptability.
    
13. **GenAI evaluation:** non-deterministic output → carefully choose metrics, benchmarks, datasets.
    
14. **Bedrock:** transcript states continuous pre-training can customize **Titan Text Express/Lite using unlabeled data**.