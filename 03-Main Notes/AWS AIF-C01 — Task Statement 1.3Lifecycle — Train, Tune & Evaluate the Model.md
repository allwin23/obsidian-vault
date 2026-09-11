
## 🎯 Exam Essentials

### 1. Training = Learning the Model Parameters

During **model training**, the ML algorithm learns by adjusting numerical values called:

- **Parameters**
    
- **Weights**
    

The goal is to adjust these values so that the model's predictions become closer to the expected outputs.

Basic mental model:

**Input → Model → Prediction → Compare with expected output → Calculate error → Adjust parameters → Repeat**

This happens iteratively.

---

### 2. Training Is Iterative

A model generally doesn't learn everything in one pass.

The training process repeatedly:

1. Makes predictions
    
2. Measures error
    
3. Adjusts parameters/weights
    
4. Makes new predictions
    
5. Measures the new error
    
6. Repeats
    

Training can stop when:

- A predefined number of iterations is reached, or
    
- The improvement/change in error becomes sufficiently small.
    

**Exam trigger:**

> "Model repeatedly adjusts weights to reduce prediction error"  
> → **Training / iterative optimization**

---

## 3. Parameters vs Hyperparameters ⭐

This is a **very important exam distinction**.

### Parameters

**Learned by the model during training.**

Examples:

- Neural-network weights
    
- Model coefficients
    

You don't manually specify the final parameter values.

---

### Hyperparameters

**Set/configured before or during training by the data scientist/system.**

They control how the training process/model operates.

Examples:

- Learning rate
    
- Number of training iterations
    
- Number of neural-network layers
    
- Number of nodes
    
- Other algorithm-specific settings
    

The optimal hyperparameters are usually discovered through **experimentation/tuning**.

### 🧠 Memorize:

> **Parameters = learned**  
> **Hyperparameters = configured**

---

# 4. Experiments

There usually isn't one guaranteed best algorithm or configuration.

Data scientists can run multiple training jobs using different:

- Algorithms
    
- Hyperparameters
    
- Data configurations
    

Then they compare the resulting models.

This is called **running experiments**.

Example:

|Experiment|Algorithm|Learning rate|Result|
|---|---|--:|--:|
|1|Algorithm A|0.01|82%|
|2|Algorithm A|0.001|87%|
|3|Algorithm B|0.01|84%|
|4|Algorithm B|0.001|91%|

The objective is to identify the configuration that performs best according to the selected evaluation metric.

---

# 5. Amazon SageMaker AI Training Jobs

With **Amazon SageMaker AI**, you create a **training job**.

You specify things such as:

- Training data location
    
- Compute resources
    
- Model artifact output location
    
- Training algorithm/container
    
- Hyperparameters
    

A simplified workflow:

**Training data in S3**

↓

**SageMaker AI training job**

↓

**ML compute**

↓

**Training algorithm**

↓

**Trained model**

↓

**Model artifacts stored in S3**

---

### Amazon ECR

**Amazon Elastic Container Registry (ECR)** can store Docker container images containing:

- SageMaker-provided algorithms/containers
    
- Deep learning containers
    
- Custom training algorithms
    

So a custom training workflow can use a container image from **Amazon ECR**.

### 🧠 Exam trigger

> "SageMaker needs a container image containing the training algorithm"  
> → **Amazon ECR**

---

# 6. Model Artifacts

After training, SageMaker saves the resulting **model artifacts** to the specified S3 location.

Remember:

**Training data → S3**

**Trained model artifacts → S3**

This is why S3 commonly appears in both the input and output portions of a SageMaker training workflow.

---

# 7. Amazon SageMaker Experiments

ML experimentation can generate a huge number of training runs and model versions.

**SageMaker Experiments** helps you:

- Create experiments
    
- Manage experiments
    
- Track training runs
    
- Compare runs
    
- Analyze results
    
- Identify the best-performing model
    

An experiment can contain multiple training runs with different:

- Inputs
    
- Parameters
    
- Hyperparameters
    
- Configurations
    

### 🧠 Mental shortcut

> **Experiments = track and compare training runs**

---

# 8. Automatic Model Tuning (AMT)

**Amazon SageMaker Automatic Model Tuning (AMT)** is also called **hyperparameter tuning**.

Its purpose:

> **Find hyperparameter values that produce the best-performing model.**

You specify:

- Algorithm
    
- Training dataset
    
- Hyperparameters to tune
    
- Range of possible values
    
- Objective metric
    

AMT runs multiple training jobs using different hyperparameter combinations and evaluates their results.

### Example

Suppose you want to maximize **AUC** for a binary classification model.

AMT might test:

- Learning rate = 0.01
    
- Learning rate = 0.001
    
- Different tree depths
    
- Different regularization values
    

It evaluates the resulting models and identifies the configuration producing the best AUC.

---

# 🔑 Key Terms

|Term|Meaning|Exam clue|
|---|---|---|
|**Parameter**|Value learned by model during training|Weights|
|**Hyperparameter**|Configuration chosen for training|Learning rate, layers|
|**Training**|Process of learning model parameters|Reduce prediction error|
|**Training job**|SageMaker execution of model training|Train using compute|
|**Experiment**|Collection of training runs|Compare model versions|
|**SageMaker Experiments**|Track/manage/compare experiments|Many training runs|
|**Automatic Model Tuning (AMT)**|Automatically searches for good hyperparameters|Hyperparameter optimization|
|**Model artifact**|Output generated by training|Stored in S3|
|**Amazon ECR**|Container image registry|Training container|
|**AUC**|Evaluation metric often used for classification|Optimize classification performance|

---

# ⚔️ Important Comparisons

## Parameters vs Hyperparameters ⭐⭐⭐

||Parameters|Hyperparameters|
|---|---|---|
|Who determines them?|**Learned by algorithm**|**Set/configured**|
|When?|During training|Before/during training configuration|
|Example|Neural-network weights|Learning rate|
|Purpose|Represents what the model learned|Controls how the model learns/operates|
|Optimized through|Training|Hyperparameter tuning/experiments|

### 🧠 Exam shortcut

**Parameter → model learns it.**

**Hyperparameter → you tune it.**

---

## SageMaker Experiments vs Automatic Model Tuning

|SageMaker Experiments|Automatic Model Tuning|
|---|---|
|Tracks and compares experiments|Searches for better hyperparameters|
|Helps analyze training runs|Automatically runs training jobs|
|Broad experimentation management|Specifically hyperparameter optimization|
|"Which run performed best?"|"Which hyperparameters perform best?"|

This distinction is **very likely to be useful for scenario questions**.

---

# 🧠 Exam Traps

### Trap 1 — Hyperparameters are learned weights ❌

No.

**Weights = parameters.**

**Learning rate/layers/etc. = hyperparameters.**

---

### Trap 2 — AMT trains only one model ❌

AMT runs **multiple training jobs** with different hyperparameter configurations to find a better-performing configuration.

---

### Trap 3 — SageMaker Experiments automatically chooses hyperparameters ❌

Its main role is **managing, tracking, analyzing, and comparing experiments/runs**.

AMT specifically performs **automatic hyperparameter tuning**.

---

### Trap 4 — ECR stores the trained model ❌

ECR is primarily a **container image registry**.

SageMaker model artifacts can be stored in **S3**.

---

### Trap 5 — More training runs automatically mean a better model ❌

Experiments help you **compare alternatives**. The best model depends on the chosen evaluation metric and business requirements.

---

### Trap 6 — AUC is the model itself ❌

AUC is an **evaluation metric**. AMT can optimize a selected objective metric such as AUC.

---

# 📝 Exam Questions

### Q1

During neural-network training, the algorithm repeatedly changes numerical values associated with connections between neurons. What are these values?

A. Hyperparameters  
B. Parameters/weights  
C. Features  
D. Labels

**Answer: B — Parameters/weights**

---

### Q2

A data scientist specifies the learning rate before starting training. What type of value is the learning rate?

A. Parameter  
B. Hyperparameter  
C. Label  
D. Feature

**Answer: B — Hyperparameter**

---

### Q3

A company wants to compare hundreds of training runs using different algorithms and configurations and identify which model performed best. Which SageMaker capability is most relevant?

A. SageMaker Experiments  
B. SageMaker Ground Truth  
C. SageMaker Feature Store  
D. Amazon ECR

**Answer: A — SageMaker Experiments**

---

### Q4

A data scientist wants AWS to automatically search different hyperparameter values and find the combination that maximizes AUC. Which capability should they use?

A. SageMaker Experiments  
B. SageMaker Automatic Model Tuning  
C. SageMaker Ground Truth  
D. AWS Glue

**Answer: B — SageMaker Automatic Model Tuning**

---

### Q5

A SageMaker training job needs access to a Docker container containing a custom training algorithm. Where could the container image be stored?

A. Amazon ECR  
B. Amazon Lex  
C. SageMaker Feature Store  
D. AWS Glue Data Catalog

**Answer: A — Amazon ECR**

---

### Q6

Which statement correctly describes ML training?

A. The model's parameters are adjusted iteratively to reduce error  
B. Hyperparameters are automatically converted into labels  
C. Training only occurs after production deployment  
D. Training consists of storing data in S3

**Answer: A**

---

### Q7

A company runs thousands of training jobs with different hyperparameter configurations and wants to automatically select the configuration producing the best value for a chosen metric. What should it use?

A. Amazon ECR  
B. SageMaker Automatic Model Tuning  
C. SageMaker Ground Truth  
D. AWS Glue DataBrew

**Answer: B**

---

### Q8

After completing a SageMaker training job, where can the resulting model artifacts be stored?

A. Amazon S3  
B. Amazon Lex  
C. AWS Glue Crawler  
D. Amazon Transcribe

**Answer: A — Amazon S3**

---

# ⚡ 30-Second Revision

1. **Training = model learns parameters/weights.**
    
2. **Parameters = learned.**
    
3. **Hyperparameters = configured/tuned.**
    
4. **Training is iterative → prediction → error → adjust → repeat.**
    
5. **Experiments = compare multiple training runs/configurations.**
    
6. **SageMaker Experiments = track/manage/analyze experiments.**
    
7. **AMT = automatically tune hyperparameters.**
    
8. **AMT runs multiple training jobs.**
    
9. **AUC can be an objective metric for tuning classification models.**
    
10. **SageMaker training data → commonly S3.**
    
11. **SageMaker model artifacts → commonly S3.**
    
12. **Training containers → can be stored in Amazon ECR.**
    

### 🧠 The 4-word memory trick

**Parameters = Learned**  
**Hyperparameters = Tuned**  
**Experiments = Compared**  
**AMT = Optimized**