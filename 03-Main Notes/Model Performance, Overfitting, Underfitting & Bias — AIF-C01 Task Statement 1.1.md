

## 🎯 Exam Essentials

### Overfitting

- **Overfitting:** A model performs **very well on training data but poorly on new/unseen data**.
    
- The model has learned the training data too closely, including patterns that may not generalize.
    
- **Noise:** Irrelevant/random patterns in training data that can cause overfitting.
    
- A common way to reduce overfitting is to train with **more diverse and representative data**.
    

**Exam trigger:**

> "High accuracy on training data but poor performance on new data" → **Overfitting**

**Example:**

The model is trained almost exclusively on fish **swimming underwater**.

It performs extremely well on those images but struggles when shown a fish **out of water**.

→ **Overfitting**

---

### Underfitting

- **Underfitting:** A model fails to learn a meaningful relationship between inputs and outputs.
    
- It performs **poorly on both training data and new data**.
    
- Possible causes include:
    
    - Insufficient training
        
    - Insufficient data
        
    - A model that is too simple for the problem
        

**Exam trigger:**

> "Poor performance on both training and test/new data" → **Underfitting**

---

### Overfitting vs Underfitting

Think about whether the model has **learned too little or too much**:

```text
Underfitting
     ↓
Learns too little
     ↓
Bad training performance
Bad new-data performance


Good fit
     ↓
Learns useful patterns
     ↓
Good training performance
Good new-data performance


Overfitting
     ↓
Learns training data too closely
     ↓
Excellent training performance
Poor new-data performance
```

### Bias & Fairness

- **Model bias:** Systematic differences in model performance or outcomes across groups.
    
- Bias can arise when training data is **not sufficiently diverse or representative**.
    
- A model can learn undesirable patterns from biased training data and reproduce those patterns in its predictions.
    
- Bias should be considered **early in the ML lifecycle**, not only after deployment.
    
- Models should be **continuously evaluated** for fairness.
    

**Exam trigger:**

> "Model performs differently for different demographic groups because the training data was not representative" → **Bias / fairness issue**

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Overfitting**|Model performs well on training data but poorly on unseen data|
|**Underfitting**|Model performs poorly on both training and unseen data|
|**Noise**|Irrelevant/random patterns in data that can negatively affect learning|
|**Bias**|Systematic disparity or skew in model outcomes/performance|
|**Fairness**|Ensuring model outcomes don't unfairly favor or disadvantage groups|
|**Diverse data**|Data representing a broad range of relevant cases/groups|
|**Generalization**|Model's ability to perform well on new, unseen data|
|**Training data**|Data used to teach the model|
|**Unseen data**|Data not used during training, used to evaluate/generalize the model|

---

## ⚔️ Important Comparisons

|Concept|Training data performance|New/unseen data performance|Main problem|
|---|---|---|---|
|**Underfitting**|Poor|Poor|Didn't learn enough|
|**Good fit**|Good|Good|Learned useful patterns|
|**Overfitting**|Very good|Poor|Learned training data too closely|

### Overfitting vs Bias

These are **not the same thing**.

- **Overfitting** → problem with **generalization** to unseen data.
    
- **Bias/fairness** → problem with **disparities or systematic unfairness**, often across groups.
    

A model can be:

- Overfit but fair
    
- Underfit but fair
    
- Accurate overall but biased against a particular group
    
- Both overfit **and** biased
    

---

## 🧠 Exam Traps

- **Trap:** "The model has 99% training accuracy, so it's a good model."
    
    - **Correct:** Not necessarily. If performance on unseen data is poor, the model is likely **overfitting**.
        
- **Trap:** Overfitting means the model performs badly on training data.
    
    - **Correct:** Overfit models generally perform **very well on training data** but poorly on new data.
        
- **Trap:** Underfitting means the model performs well on training data but poorly on new data.
    
    - **Correct:** That's **overfitting**. Underfitting generally performs poorly on **both**.
        
- **Trap:** Removing one demographic feature automatically eliminates model bias.
    
    - **Correct:** Bias can still exist through other correlated features or biased training data. **Removing a sensitive feature alone does not guarantee fairness.**
        
- **Trap:** Bias can be fixed only after deployment.
    
    - **Correct:** Bias should be considered during **data collection, model development, evaluation, and ongoing monitoring**.
        
- **Trap:** More training is always better.
    
    - **Correct:** Excessive training can contribute to **overfitting**. The goal is good generalization, not simply maximizing training-data performance.
        

---

## 📝 Exam Questions

### Question 1

A company develops an image classification model. The model achieves 98% accuracy on its training images but only 65% accuracy on images collected from real-world users.

What is the MOST likely problem?

A. Underfitting  
B. Overfitting  
C. Reinforcement learning  
D. Data encryption

**Answer:** B

**Why:** Excellent training performance combined with poor unseen-data performance is the classic sign of **overfitting**.

---

### Question 2

An ML model performs poorly when evaluated on both its training dataset and new production data.

Which issue is MOST likely occurring?

A. Overfitting  
B. Underfitting  
C. Batch inference  
D. Data labeling

**Answer:** B

**Why:** **Underfitting** occurs when the model fails to learn the underlying relationship, resulting in poor performance on both training and unseen data.

---

### Question 3

An organization trains a loan approval model using historical applications. The training dataset contains very few applications from a particular demographic group. After deployment, the model consistently produces worse outcomes for that group.

What is the PRIMARY concern?

A. Model bias  
B. Batch inference  
C. Overfitting only  
D. Tokenization

**Answer:** A

**Why:** Insufficiently representative training data can cause **bias and unfair outcomes across groups**.

---

### Question 4

A data scientist discovers that a model has learned random patterns that are specific to the training dataset and don't apply to real-world examples.

What is this behavior most closely associated with?

A. Underfitting  
B. Overfitting  
C. Classification  
D. Reinforcement learning

**Answer:** B

**Why:** Learning irrelevant patterns or **noise** in training data is associated with overfitting.

---

### Question 5

A company wants to reduce the risk that its image recognition model will fail when it encounters images different from those used during training.

Which approach is MOST appropriate?

A. Use more diverse and representative training data  
B. Remove all test data  
C. Train only on identical images  
D. Use fewer training examples

**Answer:** A

**Why:** More **diverse training data** can help the model generalize better to unseen real-world cases.

---

### Question 6

An ML team is developing a loan approval model. Before training, the team discovers that historical data contains very few examples from certain population groups.

What should the team do?

A. Ignore the issue because the model will automatically correct it  
B. Evaluate and address potential bias in the training data  
C. Train the model longer  
D. Use only the historical approval decisions without reviewing the data

**Answer:** B

**Why:** Training data should be examined for **potential bias and representativeness** before building the model.

---

## ⚡ 30-Second Revision

- **Overfitting = good training performance + bad new-data performance.**
    
- **Underfitting = bad training performance + bad new-data performance.**
    
- **Goal = good generalization**, not maximum training accuracy.
    
- **Noise = irrelevant patterns** that can contribute to overfitting.
    
- More **diverse/representative training data** can improve generalization.
    
- **Bias = systematic disparity/skew**, especially across groups.
    
- Poorly representative training data can produce **biased models**.
    
- **Fairness must be considered throughout the ML lifecycle.**
    
- **Overfitting ≠ bias:** overfitting concerns generalization; bias concerns systematic disparities/unfairness.