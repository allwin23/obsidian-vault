# AWS AIF-C01 — Task Statement 1.3

## MLOps Services & Model Evaluation Metrics

## 🎯 Exam Essentials

### 1. SageMaker Model Registry

**SageMaker Model Registry = centralized repository for trained ML models and their versions/history.**

Useful for managing the model lifecycle, including keeping track of different model versions.

**Exam trigger:**

> "Central repository for trained models, versions, and model history"

→ **SageMaker Model Registry**

---

### 2. Feature Store vs Model Registry

This distinction is important:

- **SageMaker Feature Store** → stores/reuses **ML features**
    
- **SageMaker Model Registry** → stores/manages **trained models and versions**
    

🧠 **Features → Feature Store**

🧠 **Models → Model Registry**

---

### 3. AWS Step Functions

**AWS Step Functions = visual workflow orchestration.**

It allows you to build workflows that:

- Connect different AWS services
    
- Execute application logic
    
- Define sequences of tasks
    
- Use serverless workflows
    

Think:

> **Step Functions = visually orchestrate a workflow across AWS services.**

---

### 4. Amazon Managed Workflows for Apache Airflow (MWAA)

**Apache Airflow** is an open-source workflow orchestration platform.

It lets you:

- Programmatically define workflows
    
- Schedule workflows
    
- Monitor workflows
    
- Use Python to define workflows
    

**Amazon MWAA** is the AWS managed offering, so AWS handles much of the underlying infrastructure management.

### 🧠 Distinction

**Step Functions → AWS-native visual workflow orchestration**

**Airflow/MWAA → Airflow-based, Python/programmatic workflow orchestration**

---

# Model Evaluation

## 5. Confusion Matrix ⭐⭐⭐

A **confusion matrix** summarizes the performance of a **classification model**, particularly binary classification.

It compares:

**Actual class ↔ Predicted class**

There are four outcomes:

||Predicted Positive|Predicted Negative|
|---|---|---|
|**Actually Positive**|**True Positive (TP)**|**False Negative (FN)**|
|**Actually Negative**|**False Positive (FP)**|**True Negative (TN)**|

### 🧠 The four terms

**True Positive**

> Actually positive + predicted positive

**True Negative**

> Actually negative + predicted negative

**False Positive**

> Actually negative + predicted positive

**False Negative**

> Actually positive + predicted negative

---

# 6. Accuracy

**Accuracy = proportion of all predictions that are correct.**

Accuracy=TP+TNTP+TN+FP+FNAccuracy = \frac{TP + TN}{TP + TN + FP + FN}

Example:

100 test examples:

- TP = 25
    
- TN = 40
    
- FP = 20
    
- FN = 15
    

Accuracy:

25+40100=65%\frac{25+40}{100}=65\%

### ⚠️ Important limitation

Accuracy can be misleading with **imbalanced datasets**.

Example:

100 patients:

- 95 don't have disease
    
- 5 have disease
    

A terrible model that predicts:

> "Nobody has the disease"

gets **95% accuracy**.

So high accuracy doesn't necessarily mean the model is useful.

---

# 7. Precision ⭐⭐⭐

**Precision asks:**

> **"Of everything the model predicted as positive, how much was actually positive?"**

Precision=TPTP+FPPrecision = \frac{TP}{TP+FP}

Think:

> **When the model says YES, how often is it right?**

Precision is particularly important when **false positives are costly**.

### Example

Spam detection:

The model says:

> "This email is spam."

You don't want legitimate emails incorrectly sent to spam.

→ **High precision is important.**

---

# 8. Recall ⭐⭐⭐

**Recall asks:**

> **"Of all the actual positives, how many did the model successfully find?"**

Recall=TPTP+FNRecall = \frac{TP}{TP+FN}

Think:

> **Of all the real YES cases, how many did we catch?**

Recall is especially important when **false negatives are costly**.

### Example

Disease detection:

A patient actually has a disease.

If the model says:

> "No disease."

that's a **false negative**.

Missing a real disease can be extremely costly.

→ **High recall is important.**

---

# 9. Precision vs Recall ⭐⭐⭐

This is one of the most important concepts from this lesson.

### Precision

Focuses on:

> **Avoiding false positives**

### Recall

Focuses on:

> **Avoiding false negatives**

|Business concern|Prioritize|
|---|---|
|Don't incorrectly flag legitimate email as spam|**Precision**|
|Don't miss patients who actually have a disease|**Recall**|
|Don't miss fraudulent transactions|**Recall**|
|Don't inconvenience legitimate customers by blocking valid transactions|**Precision**|

---

# 10. F1 Score

When you need a balance between **precision and recall**, use the **F1 score**.

It combines both into a single metric using their harmonic mean:

F1=2×Precision×RecallPrecision+RecallF1 = 2 \times \frac{Precision \times Recall}{Precision + Recall}

The important AIF-C01 concept isn't the calculation.

Remember:

> **F1 = balance between precision and recall.**

---

# 🔑 Key Terms

|Term|Meaning|Exam clue|
|---|---|---|
|**Model Registry**|Repository for trained models and versions|Model version management|
|**Feature Store**|Repository for reusable ML features|Feature management|
|**Step Functions**|Visual workflow orchestration|Connect AWS services|
|**Apache Airflow**|Open-source workflow orchestration|Python/programmatic workflows|
|**MWAA**|Managed Apache Airflow on AWS|Airflow without infrastructure management|
|**Confusion matrix**|Classification-performance summary|TP/TN/FP/FN|
|**True Positive**|Positive correctly predicted|Actual + / Predicted +|
|**True Negative**|Negative correctly predicted|Actual − / Predicted −|
|**False Positive**|Negative incorrectly predicted positive|False alarm|
|**False Negative**|Positive incorrectly predicted negative|Missed positive|
|**Accuracy**|Overall percentage of correct predictions|TP + TN / all|
|**Precision**|Correct positives among predicted positives|Avoid FP|
|**Recall**|Correct positives among actual positives|Avoid FN|
|**Sensitivity**|Another name for recall|True positive rate|
|**F1 score**|Combines precision and recall|Balance FP/FN concerns|

---

# ⚔️ Important Comparisons

## Precision vs Recall — The Most Important Distinction

Imagine a disease detection system.

### Precision

The model says **100 people have the disease**.

Only **80 actually have it**.

Precision:

80/100=80%80/100 = 80\%

It asks:

> **"When the model says positive, how often is it correct?"**

---

### Recall

There are actually **100 people who have the disease**.

The model successfully detects **80**.

Recall:

80/100=80%80/100 = 80\%

It asks:

> **"Of all the people who actually have the disease, how many did we find?"**

---

### 🧠 The easiest memory trick

**Precision → Predicted Positive**

> "Of my YES predictions, how many were correct?"

**Recall → Real Positives**

> "Of all the real YES cases, how many did I catch?"

---

# Accuracy vs Precision vs Recall

|Metric|Core question|Main concern|
|---|---|---|
|**Accuracy**|How many total predictions were correct?|Overall correctness|
|**Precision**|When I predict positive, how often am I correct?|False positives|
|**Recall**|Of actual positives, how many did I detect?|False negatives|
|**F1**|How well do precision and recall balance?|Both|

---

# 🧠 Exam Traps

### Trap 1 — Precision means "overall correctness" ❌

That's **accuracy**.

Precision only looks at **predicted positives**.

---

### Trap 2 — Recall means "percentage of predictions that were correct" ❌

That's accuracy.

Recall focuses on **actual positives that were successfully detected**.

---

### Trap 3 — High accuracy always means good model ❌

Not necessarily.

Accuracy can be misleading with **imbalanced datasets**.

---

### Trap 4 — False positive and false negative are interchangeable ❌

Remember:

**False Positive → predicted positive when actually negative.**

**False Negative → predicted negative when actually positive.**

---

### Trap 5 — Precision is always more important than recall ❌

It depends on the **business cost of errors**.

If false positives are expensive → prioritize precision.

If false negatives are expensive → prioritize recall.

---

### Trap 6 — F1 maximizes accuracy ❌

F1 specifically combines **precision and recall**.

---

### Trap 7 — Model Registry stores features ❌

**Feature Store → features**

**Model Registry → models**

---

### Trap 8 — Step Functions and SageMaker Pipelines are identical ❌

Both can orchestrate workflows, but:

- **SageMaker Pipelines** → specifically designed for ML workflows.
    
- **Step Functions** → general AWS workflow orchestration across services.
    

---

# 📝 Exam Questions

These are intentionally **harder and shuffled**. The options are designed to look similarly plausible, so you'll need the exact concept rather than keyword matching.

### Q1

A hospital evaluates a binary disease-detection model. The hospital considers failing to identify a patient who actually has the disease significantly more harmful than incorrectly referring a healthy patient for additional testing. Which evaluation objective should receive the greatest emphasis?

A. Maximize precision so that most patients classified as positive actually have the disease  
B. Maximize recall so that the model identifies the greatest possible proportion of actual positive cases  
C. Maximize accuracy so that the overall proportion of correct classifications is as high as possible  
D. Maximize the F1 score so that the model gives equal importance to positive and negative classifications

**Answer: B — Recall**

**Why:** The critical error is a **false negative**—missing a patient who actually has the disease. Recall measures how many actual positives are detected.

---

### Q2

An ML team wants to maintain a centralized history of trained models so that it can identify different model versions and manage them throughout their lifecycle. Which capability most directly addresses this requirement?

A. SageMaker Feature Store  
B. SageMaker Model Registry  
C. SageMaker Model Monitor  
D. SageMaker Experiments

**Answer: B — SageMaker Model Registry**

**Why:** Model Registry is specifically designed for centralized model/version management.

---

### Q3

A fraud model identifies 1,000 transactions as fraudulent. Investigation reveals that only 700 of those transactions were actually fraudulent. Which metric directly measures the quality of the model's positive predictions?

A. Recall  
B. Accuracy  
C. Precision  
D. F1 score

**Answer: C — Precision**

**Why:** Precision asks how many of the cases **predicted positive** were actually positive.

---

### Q4

A company has a dataset in which 99% of transactions are legitimate and 1% are fraudulent. A model predicts every transaction as legitimate and achieves 99% accuracy. Which conclusion is most appropriate?

A. The model has demonstrated strong fraud-detection performance because its overall accuracy is high  
B. The model should be considered reliable because accuracy is calculated across both classes  
C. The accuracy may be misleading because the dataset is highly imbalanced and the model detects no fraudulent cases  
D. The model has high precision because nearly all of its predictions correspond to legitimate transactions

**Answer: C**

**Why:** A highly imbalanced dataset can produce deceptively high accuracy even when the model completely fails to detect the minority class.

---

### Q5

An ML team wants a workflow engine that can coordinate data preparation, training, evaluation, and deployment specifically as part of an ML pipeline. Which capability is the most directly specialized for this requirement?

A. AWS Step Functions  
B. SageMaker Pipelines  
C. Amazon Managed Workflows for Apache Airflow  
D. SageMaker Model Registry

**Answer: B — SageMaker Pipelines**

**Why:** All listed options can participate in broader workflows, but SageMaker Pipelines is specifically designed to orchestrate ML pipeline steps.

---

### Q6

A binary classifier produces the following results on a test set:

- 80 true positives
    
- 20 false positives
    
- 10 false negatives
    
- 90 true negatives
    

Which metric is calculated as `80 / (80 + 20)`?

A. Recall  
B. Accuracy  
C. Precision  
D. F1 score

**Answer: C — Precision**

---

### Q7

A company uses a model to identify legitimate customers who may have been incorrectly classified as fraudulent. Management considers these incorrect fraud classifications especially costly because they cause legitimate customers to be blocked. Which metric should the team prioritize?

A. Recall, because it measures the proportion of actual fraudulent customers detected  
B. Precision, because it measures the proportion of positive predictions that are actually fraudulent  
C. Accuracy, because it directly measures the frequency of incorrect fraud classifications  
D. F1 score, because it always minimizes false-positive classifications

**Answer: B — Precision**

**Why:** The business wants to minimize **false positives**. Precision is the metric most directly associated with the quality of positive predictions.

---

### Q8

A company wants to use Python to programmatically define, schedule, and monitor a complex sequence of tasks. It prefers the Apache Airflow ecosystem but does not want to manage the underlying infrastructure. Which AWS service best fits?

A. AWS Step Functions  
B. Amazon Managed Workflows for Apache Airflow  
C. SageMaker Pipelines  
D. Amazon EventBridge

**Answer: B — Amazon MWAA**

---

### Q9

A model has high precision but relatively low recall. Which interpretation is most accurate?

A. Most cases predicted as positive are genuinely positive, but the model misses a relatively large number of actual positive cases  
B. Most actual positive cases are detected, but a relatively large proportion of positive predictions are incorrect  
C. The model makes very few errors overall, but its performance is affected by an imbalanced dataset  
D. The model has successfully balanced false positives and false negatives through optimization of a single metric

**Answer: A**

**Why:** High precision → few false positives among positive predictions. Low recall → many actual positives are being missed.

---

### Q10

A team wants a single metric that reflects both its ability to avoid false-positive errors and its ability to detect actual positive cases. Which metric is specifically designed for this purpose?

A. Accuracy  
B. Precision  
C. Recall  
D. F1 score

**Answer: D — F1 score**

**Why:** F1 combines precision and recall into a single metric.

---

# ⚡ 30-Second Revision

1. **Feature Store → features.**
    
2. **Model Registry → models + versions/history.**
    
3. **SageMaker Pipelines → ML workflow orchestration.**
    
4. **Step Functions → general AWS workflow orchestration.**
    
5. **MWAA → managed Apache Airflow.**
    
6. **Confusion matrix → TP, TN, FP, FN.**
    
7. **Accuracy → `(TP + TN) / all predictions`.**
    
8. **Precision → `TP / (TP + FP)` → avoid false positives.**
    
9. **Recall → `TP / (TP + FN)` → avoid false negatives.**
    
10. **Recall = sensitivity = true positive rate.**
    
11. **F1 → balances precision + recall.**
    
12. **Accuracy can be misleading on imbalanced datasets.**
    

### 🧠 The one distinction you absolutely need

> **Precision:** "When I say **YES**, am I usually right?"

> **Recall:** "Of all the real **YES** cases, did I find them?"

If the question says **"don't falsely accuse/flag/block" → Precision.**

If it says **"don't miss/fail to detect" → Recall.**

If it says **"balance both" → F1.**