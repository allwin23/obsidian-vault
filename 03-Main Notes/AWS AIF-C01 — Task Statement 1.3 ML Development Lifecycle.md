

## Describe the ML Development Lifecycle — ML Pipelines

## 🎯 Exam Essentials

### 1. ML Pipeline = ML Lifecycle

An ML pipeline is a sequence of stages that takes you from a **business problem → deployed ML model → ongoing monitoring/improvement**.

Core lifecycle:

**Business goal → Data → Training → Deployment → Monitoring → Retraining/adjustment → Repeat**

The key exam idea is that ML is **not a one-time process**.

After deployment, the model may need to be:

- Re-evaluated
    
- Retrained with new data
    
- Monitored for drift
    
- Checked for bias
    
- Adjusted or rebuilt
    

Therefore, think **ML lifecycle**, not simply "build a model once."

---

### 2. Start With the Business Goal

Before choosing an ML algorithm or AWS service:

1. Define the **business problem**
    
2. Define the desired **business outcome**
    
3. Establish measurable **success criteria**
    
4. Align stakeholders
    
5. Determine whether ML is actually the right solution
    

The important question isn't:

> "Can we use ML?"

It's:

> **"Is ML the best cost-effective and scalable way to achieve the business objective?"**

---

### 3. Define the ML Problem

Translate the business problem into:

- **Inputs** → What data does the model receive?
    
- **Desired output** → What should it predict/generate?
    
- **Performance metric** → How will success be measured?
    

Also consider:

- Data availability
    
- Data quality
    
- Accuracy requirements
    
- Cost
    
- Scalability
    

---

### 4. Start With the Simplest Solution

Before building a complex custom ML system:

**Evaluate simpler options first.**

A useful decision hierarchy from this lesson is:

**Existing AWS AI service → Customize existing/pre-trained model → Build custom model → Train from scratch**

Why?

Because complexity increases:

- Development effort
    
- Cost
    
- Operational responsibility
    
- Security/compliance responsibility
    

---

### 5. AWS Pre-trained AI Services

AWS provides fully managed, pre-trained AI services for common use cases.

Examples from earlier lessons:

- **Amazon Comprehend** → NLP/text analysis
    
- **Amazon Rekognition** → image/video analysis
    
- **Amazon Textract** → document extraction
    
- **Amazon Transcribe** → speech → text
    
- **Amazon Polly** → text → speech
    
- **Amazon Lex** → conversational interfaces
    

These can be preferable to building your own model because AWS handles much of the underlying ML infrastructure.

**Exam trigger:**

> "A common AI use case can be solved using an existing AWS managed AI service"  
> → **Prefer/evaluate the managed AI service first.**

---

### 6. Customize a Managed AI Service

Sometimes a pre-trained service doesn't exactly fit the business requirement.

Example:

**Amazon Comprehend → Custom Classifier**

You can supply your own labeled training data and create categories specific to your business.

So the progression can be:

**Generic managed service → customize it if necessary**

---

### 7. Start With a Pre-trained Model

If a managed AI service isn't sufficient, another option is to start from an existing **pre-trained model** rather than creating one from zero.

Examples:

- **Amazon Bedrock** → foundation models for generative AI applications
    
- **Amazon SageMaker AI / JumpStart** → pre-trained models for various ML tasks
    

This can dramatically reduce:

- Training cost
    
- Development time
    
- Data requirements
    
- Technical effort
    

---

### 8. Transfer Learning

**Transfer learning** means starting with a model that has already learned from existing data and adapting it to a new/specific task using additional training.

Mental model:

**Pre-trained model + your data → adapted model**

Example:

A model already trained to understand images can be adapted using your own labeled images for a specialized classification task.

### ⚠️ Important

The transcript describes fine-tuning a foundation model as transfer learning. That's broadly reasonable, but don't memorize **"transfer learning = only fine-tuning."**

Transfer learning is the broader concept of **reusing knowledge learned by a model for another related task**.

---

### 9. SageMaker JumpStart

**Amazon SageMaker JumpStart** provides pre-trained models that can be used as starting points for ML development.

It includes models for areas such as:

- Computer vision
    
- NLP
    
- Foundation models
    
- Other ML tasks
    

You can use a pre-trained model and adapt it to your own requirements.

**Exam trigger:**

> "Developer wants to quickly start ML development using an existing pre-trained model"  
> → **SageMaker JumpStart**

---

### 10. Training From Scratch

Training a model from scratch is generally the **most complex and resource-intensive** option.

It requires greater responsibility for things such as:

- Training infrastructure
    
- Data
    
- Model development
    
- Security
    
- Compliance
    
- Evaluation
    
- Operations
    

Therefore, don't jump to training from scratch when a suitable managed service or pre-trained model exists.

---

## 🔑 Key Terms

|Term|Meaning|Exam clue|
|---|---|---|
|**ML pipeline**|Sequence of ML development/operation stages|Business goal → deployment|
|**ML lifecycle**|Pipeline continues through monitoring and repeated improvement|Retraining after deployment|
|**Success criteria**|Measurable definition of business/model success|"How do we know it worked?"|
|**Pre-trained model**|Model already trained on existing data|Starting point for development|
|**Transfer learning**|Reuse learned knowledge for a related task|Adapt existing model|
|**Fine-tuning**|Additional training to adapt a pre-trained model|Customize model behavior|
|**SageMaker JumpStart**|Collection of pre-trained models/tools for starting ML projects|"Start quickly with existing model"|
|**Custom classifier**|Model customized for your categories/classes|Comprehend custom classification|
|**Model drift**|Model performance/relationship changes as real-world data changes|Monitor after deployment|
|**Bias**|Systematic differences/skew in model outcomes|Monitor fairness|

---

## ⚔️ Important Comparison

### Four Levels of ML Solution

|Approach|Complexity|Typical cost/effort|When to consider|
|---|--:|--:|---|
|**Managed AI service**|Lowest|Lowest|Common AI use case|
|**Customize managed service**|Low–medium|Low–medium|Generic service isn't sufficient|
|**Pre-trained model + adaptation**|Medium|Medium|Need more control/customization|
|**Train from scratch**|Highest|Highest|Existing options don't meet requirements|

### 🧠 Memorize This

**Don't build what AWS already built.**  
**Don't train what you can reuse.**  
**Don't add complexity unless the business requirement demands it.**

---

## 🧠 Exam Traps

### Trap 1 — ML ends after deployment ❌

Wrong.

Deployment is followed by **monitoring and continuous evaluation**.

---

### Trap 2 — Always build a custom model ❌

Not necessarily.

First investigate whether an existing AWS AI service solves the problem.

---

### Trap 3 — Pre-trained model = finished solution ❌

A pre-trained model is often a **starting point**. It can potentially be adapted using your own data.

---

### Trap 4 — JumpStart trains every model from scratch ❌

JumpStart is specifically useful for **pre-trained models that accelerate development**.

---

### Trap 5 — RAG = fine-tuning ❌

These solve different problems:

- **RAG** → retrieve information and provide it as context.
    
- **Fine-tuning** → additional training that adapts model behavior/parameters.
    

---

### Trap 6 — Technical feasibility is enough ❌

The project should also satisfy **business objectives, measurable success criteria, cost, and scalability requirements**.

---

# 📝 Exam Questions

### Q1

A company wants to implement AI to solve a business problem. Before selecting an ML algorithm, what should it do first?

A. Purchase GPU infrastructure  
B. Define the business goal and measurable success criteria  
C. Train a model from scratch  
D. Deploy a SageMaker endpoint

**Answer: B**

**Why:** The ML lifecycle begins by establishing the business problem, desired outcome, and measurable success criteria.

---

### Q2

A company needs sentiment analysis and discovers that Amazon Comprehend already provides the required functionality. What should it generally consider before developing its own ML model?

A. Training from scratch  
B. Building a neural network  
C. Using the managed AWS AI service  
D. Collecting millions of new records

**Answer: C**

**Why:** Managed AI services should be evaluated before taking on the cost and complexity of custom ML development.

---

### Q3

A company uses Amazon Comprehend but needs the model to classify customer messages into categories specific to its business. What capability could it use?

A. Custom classifier  
B. Amazon Polly  
C. Amazon Transcribe  
D. Amazon Kendra

**Answer: A**

---

### Q4

A data scientist wants to build an image classification solution but wants to avoid training a model from scratch. Which capability can provide a pre-trained model as a starting point?

A. SageMaker JumpStart  
B. Amazon Lex  
C. Amazon Translate  
D. Amazon Polly

**Answer: A**

---

### Q5

A deployed ML model initially performs well, but customer behavior changes over time. What should the organization do?

A. Assume the model will remain accurate  
B. Stop monitoring the model after deployment  
C. Monitor performance and retrain or adjust the model when necessary  
D. Delete the training data

**Answer: C**

**Why:** ML models can degrade as real-world data changes, so monitoring and potentially retraining are part of the lifecycle.

---

### Q6

Which approach generally requires the greatest development effort and responsibility?

A. Using an existing managed AI service  
B. Using a pre-trained model  
C. Customizing a managed service  
D. Training a model from scratch

**Answer: D**

---

### Q7

A company takes an existing pre-trained model and uses its own dataset to adapt the model for a specialized task. What concept does this represent?

A. Transfer learning  
B. Data deletion  
C. Batch inference  
D. Clustering

**Answer: A**

---

### Q8

Which sequence best represents the general ML lifecycle?

A. Deploy → define goal → collect data → train  
B. Define business goal → prepare data → train → deploy → monitor  
C. Train → collect data → define goal → deploy  
D. Monitor → deploy → define goal → train

**Answer: B**

---

# ⚡ 30-Second Revision

1. **ML lifecycle = business goal → data → training → deployment → monitoring → repeat.**
    
2. **Start with the business problem, not the ML algorithm.**
    
3. Define **inputs, outputs, and performance metrics**.
    
4. Check whether **ML is actually the best solution**.
    
5. **Managed AWS AI service first** for common use cases.
    
6. If needed, **customize the managed service**.
    
7. Otherwise consider a **pre-trained model**.
    
8. **SageMaker JumpStart = pre-trained models to accelerate ML development.**
    
9. **Transfer learning = reuse learned knowledge for a related task.**
    
10. **Training from scratch = highest complexity/cost/responsibility.**
    
11. **Deployment is not the end**—monitor for performance, drift, and bias.
    
12. **ML is a lifecycle, not a one-time project.**
    

### 🧠 Ultimate exam mental model

**Business need → Can AWS managed service solve it? → Can I customize it? → Can I reuse a pre-trained model? → Only then consider building/training from scratch.**