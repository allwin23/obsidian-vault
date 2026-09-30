

## 🎯 Exam Essentials

### 1. LLM Pricing Models

- **Concept:** The transcript presents two broad approaches for using LLMs:
    
    1. **Host the model yourself**
        
    2. **Pay based on tokens processed**
        
- **Self-hosting:**
    
    - You pay for the required computing infrastructure.
        
    - You may also need to pay licensing costs for the LLM.
        
    - You are responsible for infrastructure investment and maintenance.
        
    - Hardware and data-storage costs can be significant.
        
- **Token-based pricing:**
    
    - Cost is based on the **tokens processed**.
        
    - Pricing can account for both **input and output** tokens.
        
    - Pay-by-token can provide scalability because costs are associated with actual usage.
        
- **Important distinction:**  
    **Self-hosting → infrastructure/licensing responsibility**  
    **Token pricing → usage-based model**
    
- **Exam trigger:**
    
    > “Avoid investing in and maintaining dedicated model infrastructure; pay based on model usage”  
    > → **Token/usage-based pricing**
    

---

### 2. AWS Global Infrastructure and Availability

- **Concept:** AWS Global Infrastructure includes architectural components such as:
    
    - **Regions**
        
    - **Availability Zones**
        
    - **Edge locations**
        
- AWS services can have different levels of resilience, including:
    
    - Global resilience
        
    - Regional resilience
        
    - Availability Zone resilience
        
- Many AWS managed services provide **high availability** as part of the service design.
    
- **Exam trigger:**
    
    > “Choose AWS infrastructure components to improve availability/fault tolerance”  
    > → Consider **Regions, Availability Zones, and service resilience**.
    

---

### 3. AWS ML and AI Service Layers

The transcript describes a layered AWS technology stack:

1. **AWS Global Infrastructure**
    
    - Regions, Availability Zones, edge locations, and underlying infrastructure.
        
2. **AWS Machine Learning Services**
    
    - Example: **Amazon SageMaker**
        
3. **AWS AI Services**
    
    - Prebuilt AI capabilities, models, and services that applications can integrate through APIs.
        

- **Important distinction:** Many AWS AI services can be consumed without building or training ML models yourself. Developers can integrate capabilities using **APIs, code, and AWS SDKs**.
    

---

### 4. Amazon SageMaker JumpStart

- **Concept:** SageMaker JumpStart is a **model hub** that helps users quickly deploy available foundation models and integrate them into applications.
    
- Capabilities mentioned:
    
    - Fine-tuning models
        
    - Deploying models
        
    - Moving models toward production
        
    - Operating at scale
        
    - Example notebooks
        
    - Blogs and videos
        
- **Cost consideration:** JumpStart models may require **GPU compute** for fine-tuning and deployment.
    
- **Important cost practice:** Delete SageMaker model endpoints when they are no longer being used and monitor costs.
    
- **Exam trigger:**
    
    > “Quickly deploy/fine-tune a foundation model available through SageMaker”  
    > → **SageMaker JumpStart**
    

---

### 5. Amazon Bedrock

- **Concept:** Amazon Bedrock is a **managed AWS service** that provides API access to multiple foundation models.
    
- Models can include:
    
    - AWS-curated models
        
    - Third-party foundation models
        
- The transcript mentions third-party providers such as **Cohere** and **Stability AI**.
    
- **Key advantage:** Developers can build generative AI applications using existing FMs without having to build foundation models from scratch.
    
- The transcript also describes support for **importing custom model weights for supported architectures** and serving supported custom models using on-demand mode.
    
- **Pricing concept from the transcript:** On-demand usage avoids a time-based term commitment and follows a **pay-for-use** approach.
    
- **Exam trigger:**
    
    > “Access multiple foundation models through APIs without building the foundation models yourself”  
    > → **Amazon Bedrock**
    

---

### 6. Amazon Bedrock Model Selection

- **Concept:** Multiple foundation models can support similar use cases, so selecting the appropriate model requires experimentation and evaluation.
    
- **Amazon Bedrock Playgrounds** allow users to experiment with supported foundation models and compare how models respond to prompts.
    
- Different models can expose different **inference parameters**.
    
- Varying inference parameters can change generated completion results.
    
- **Exam trigger:**
    
    > “Experiment with different foundation models and inference settings before selecting a model”  
    > → **Amazon Bedrock Playgrounds / model evaluation**
    

---

### 7. PartyRock

- **Concept:** PartyRock is described in the transcript as a **playground built on Amazon Bedrock**.
    
- It can be used to experiment with generative AI application development and learn how foundation models respond to prompts.
    
- Example applications include:
    
    - Playlists
        
    - Trivia games
        
    - Recipes
        
- **Exam trigger:**
    
    > “Learn generative AI techniques by experimenting with applications and prompts in a Bedrock-based playground”  
    > → **PartyRock**
    

---

### 8. Cost Optimization for SageMaker

- **Concept:** Managed ML infrastructure can continue generating costs even when the application is not actively being used.
    
- The transcript specifically emphasizes:
    
    - Reviewing SageMaker pricing before selecting compute.
        
    - Deleting **model endpoints** when they are no longer needed.
        
    - Following cost-monitoring best practices.
        
- **Exam trigger:**
    
    > “A SageMaker endpoint is no longer required and is generating unnecessary cost”  
    > → **Delete the unused endpoint**.
    

---

### 9. Vector Databases and Embeddings

- **Concept:** Generative AI applications can use **vector databases** to store and index embeddings.
    
- **Embeddings** are vector representations of information.
    
- These vectors can be:
    
    - Stored
        
    - Compressed
        
    - Indexed
        
- They can support **advanced searches**.
    
- **Exam trigger:**
    
    > “Store vector representations and perform similarity/advanced searches”  
    > → **Embeddings + vector database**
    

---

### 10. Why Organizations Use Managed Generative AI Services

- Training an LLM from scratch can require:
    
    - Significant investment
        
    - Research
        
    - Large quantities of quality data
        
    - Data collection and cleaning
        
    - Significant time
        
    - Computational resources
        
- Hosting models independently also introduces:
    
    - Hardware expenses
        
    - Data-storage expenses
        
    - Infrastructure maintenance
        
- Managed AWS generative AI services can reduce the infrastructure burden and provide access to existing foundation models.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Token-based pricing**|Usage-based pricing determined by tokens processed|
|**Self-hosting**|Running a model on infrastructure that you provision/manage|
|**Region**|AWS geographic infrastructure area containing AWS resources|
|**Availability Zone**|Isolated infrastructure location within an AWS Region|
|**Edge location**|AWS infrastructure location used for edge services/content delivery|
|**Amazon SageMaker**|AWS managed ML service for building, training, and deploying ML models|
|**SageMaker JumpStart**|Model hub for quickly accessing, fine-tuning, and deploying models|
|**Amazon Bedrock**|Managed service providing API access to multiple foundation models|
|**Foundation Model**|Broad pretrained model that can serve as a starting point for generative AI applications|
|**On-demand**|Pay-for-use model without a time-based term commitment|
|**Inference parameter**|Parameter that can influence how a model generates output|
|**Bedrock Playground**|Environment for experimenting with foundation models and prompts|
|**PartyRock**|Bedrock-based playground for experimenting with generative AI applications|
|**Embedding**|Vector representation of information|
|**Vector database**|Database designed to store/index vectors for search|
|**Model endpoint**|Deployed endpoint through which a model can serve inference requests|
|**Price-performance**|Relationship between computational performance and cost|

---

## ⚔️ Important Comparisons

### Self-Hosted LLM vs Token-Based Usage

|Approach|Use when|Key distinction|
|---|---|---|
|**Self-hosted model**|Organization wants to run the model on its own infrastructure|Pays for infrastructure and potentially licensing; responsible for maintenance|
|**Token-based pricing**|Organization wants usage-based access to a model|Cost is based on tokens processed|

---

### SageMaker JumpStart vs Amazon Bedrock

|Service|Use when|Key distinction|
|---|---|---|
|**SageMaker JumpStart**|Quickly access, fine-tune, and deploy models through SageMaker|Model hub integrated with SageMaker ML workflows|
|**Amazon Bedrock**|Build generative AI applications using multiple FMs through APIs|Managed access to multiple foundation models|

---

### Bedrock Playground vs PartyRock

|Capability|Use when|Key distinction|
|---|---|---|
|**Bedrock Playground**|Experiment with supported foundation models, prompts, and inference parameters|Model experimentation environment within Bedrock|
|**PartyRock**|Learn/experiment with building generative AI applications|Playground built on Amazon Bedrock|

---

### Training vs Inference Cost

|Activity|Main resource consideration|Key distinction|
|---|---|---|
|**Training / fine-tuning**|Significant compute, potentially GPUs|Model learns/adapts from data|
|**Inference**|Compute required to serve model requests|Model generates predictions/output|

---

### Regions vs Availability Zones

|Component|Use when|Key distinction|
|---|---|---|
|**Region**|Deploying resources within a geographic AWS area|Geographic AWS infrastructure area|
|**Availability Zone**|Designing for isolation and availability within a Region|Separate infrastructure location within a Region|

---

## 🧠 Exam Traps

### Trap 1 — Token pricing means paying for the model license only ❌

**Correct:** Token-based pricing is based on the **tokens processed**, according to the applicable service/model pricing.

---

### Trap 2 — Self-hosting eliminates infrastructure costs ❌

**Correct:** Self-hosting requires you to pay for and maintain the **computing infrastructure**, and potentially model licensing.

---

### Trap 3 — Using a managed service means there are no costs ❌

**Correct:** Managed services reduce infrastructure-management burden but still have **usage/service costs**.

---

### Trap 4 — SageMaker JumpStart and Bedrock are the same service ❌

**Correct:**  
**JumpStart → model hub within SageMaker for accessing/fine-tuning/deploying models.**

**Bedrock → managed API access to multiple foundation models for generative AI applications.**

---

### Trap 5 — An unused SageMaker endpoint stops costing money automatically ❌

**Correct:** The transcript specifically recommends **deleting unused model endpoints** and following cost-monitoring practices.

---

### Trap 6 — Bedrock requires you to train your own foundation model ❌

**Correct:** Bedrock provides access to **existing foundation models through APIs**, allowing applications to be built without creating an FM from scratch.

---

### Trap 7 — PartyRock is a separate foundation model ❌

**Correct:** PartyRock is described as a **playground built on Amazon Bedrock** for experimenting with generative AI applications.

---

### Trap 8 — Embeddings are the same as raw text stored in a database ❌

**Correct:** Embeddings are **vector representations** of information that can be stored/indexed for advanced search.

---

### Trap 9 — Vector databases are primarily used to train foundation models ❌

**Correct:** In the context of this lesson, vector databases store and index **embeddings for advanced search**.

---

### Trap 10 — The AWS AI layer requires deep ML expertise to use ❌

**Correct:** The transcript emphasizes that developers can integrate prebuilt AWS AI services using **APIs, code, and the AWS SDK**, without necessarily building ML models themselves.

---

### Trap 11 — The cheapest compute option is always the best option ❌

**Correct:** Consider **price-performance** and the workload's requirements, not simply the lowest absolute compute price.

---

# 📝 Exam Questions

> **Question order is intentionally shuffled.** These questions combine pricing, infrastructure, AWS service selection, and cost-management concepts. Distractors are designed to be closely competing rather than obviously incorrect.

### Question 1

A startup wants to build a generative AI application but does not have the resources to train or host its own foundation model. The application should be able to access foundation models from multiple providers through APIs.

Which AWS service best matches this requirement?

A. Amazon SageMaker JumpStart  
B. Amazon Bedrock  
C. Amazon EC2  
D. Amazon SageMaker Model Registry

**Answer:** **B — Amazon Bedrock**

**Why:** Bedrock provides managed API access to **multiple foundation models**, including AWS and third-party models, without requiring the organization to build FMs from scratch.

---

### Question 2

A machine learning team uses SageMaker JumpStart to fine-tune a foundation model. After completing testing, the team stops using the deployed model but leaves its endpoint running.

The company wants to reduce unnecessary ongoing costs.

What should the team do?

A. Delete the unused SageMaker model endpoint  
B. Move the endpoint to a larger GPU instance  
C. Increase the model's inference parameters  
D. Store the endpoint configuration in a vector database

**Answer:** **A — Delete the unused SageMaker model endpoint**

**Why:** The transcript explicitly identifies deleting unused SageMaker endpoints as a **cost-optimization practice**.

---

### Question 3

A company must decide between running an LLM on infrastructure it manages and consuming an externally hosted model through a usage-based pricing model. The company wants to avoid purchasing and maintaining dedicated computing infrastructure and prefers costs that scale with actual model usage.

Which approach best matches the requirement?

A. Self-host the LLM and pay for dedicated infrastructure  
B. Use token-based pricing and pay according to model usage  
C. Purchase a perpetual infrastructure license for the LLM  
D. Deploy the LLM to an unused SageMaker endpoint to avoid variable costs

**Answer:** **B**

**Why:** Token-based pricing ties cost to **tokens processed**, whereas self-hosting introduces infrastructure and potentially licensing responsibilities.

---

### Question 4

An AI team is comparing several foundation models available through Amazon Bedrock. The models support similar application scenarios, but the team wants to experiment with each model and adjust the available inference parameters before selecting one.

Which capability should the team use?

A. SageMaker Model Registry  
B. Amazon Bedrock Playgrounds  
C. AWS Nitro System  
D. Amazon EC2 Auto Scaling

**Answer:** **B — Amazon Bedrock Playgrounds**

**Why:** Bedrock Playgrounds allow teams to **experiment with supported foundation models, prompts, and inference parameters** before selecting an appropriate model.

---

### Question 5

A company wants to experiment with simple generative AI applications such as a recipe generator and trivia application while learning how foundation models respond to different prompts. The company does not want to build the entire application infrastructure itself.

Which option best matches the lesson?

A. Amazon SageMaker Model Registry  
B. Amazon Bedrock custom model import  
C. PartyRock  
D. AWS Trainium

**Answer:** **C — PartyRock**

**Why:** PartyRock is described as a **playground built on Amazon Bedrock** for experimenting with generative AI applications.

---

### Question 6

An organization stores vector representations of documents so that an application can efficiently search for information that is relevant to a user's query.

Which combination best describes the technology involved?

A. Model endpoints and Availability Zones  
B. Embeddings and vector databases  
C. Tokens and SageMaker endpoints  
D. GPUs and AWS Regions

**Answer:** **B — Embeddings and vector databases**

**Why:** The transcript describes embeddings as **vector representations** that can be stored and indexed in vector databases for advanced searches.

---

### Question 7

A company wants to fine-tune a model using SageMaker JumpStart. The engineering team is comparing compute options and wants to select infrastructure that provides an appropriate balance between computational capability and cost.

Which concept should be emphasized when making this decision?

A. Exact token count alone  
B. Price-performance  
C. Number of Bedrock providers  
D. Number of Availability Zones in the account

**Answer:** **B — Price-performance**

**Why:** The lesson specifically emphasizes **price-performance** when considering compute resources for AI workloads.

---

### Question 8

A company wants to build a generative AI application using an existing foundation model. It does not want to manage the underlying model infrastructure and wants API-based access to models from AWS and third-party providers.

Which option provides the closest match?

A. Amazon Bedrock  
B. SageMaker JumpStart only  
C. Self-hosted Amazon EC2 instances  
D. AWS Global Accelerator

**Answer:** **A — Amazon Bedrock**

**Why:** Bedrock is the managed service described as providing **API access to multiple foundation models** from AWS and third-party providers.

---

### Question 9

A company deploys an application across AWS infrastructure and wants to understand which infrastructure component represents an isolated infrastructure location **within an AWS Region**, helping support availability and fault isolation.

Which component is being described?

A. Edge location  
B. Availability Zone  
C. Region  
D. SageMaker endpoint

**Answer:** **B — Availability Zone**

**Why:** An **Availability Zone** is an isolated infrastructure location within an AWS Region. The distinction matters when reasoning about regional architecture and availability.

---

### Question 10

An organization is considering whether to train and host its own large language model. The engineering team estimates that the project would require substantial computing resources, data storage, maintenance, and potentially model licensing. Management asks why a managed generative AI service could be preferable.

Which response best reflects the tradeoff described in the lesson?

A. Managed services eliminate all model-related costs regardless of usage  
B. Managed services can reduce infrastructure and maintenance responsibilities while providing access to existing foundation models  
C. Managed services guarantee that every foundation model will outperform a self-hosted model  
D. Managed services remove the need to evaluate models for the application's requirements

**Answer:** **B**

**Why:** The lesson emphasizes that training and hosting models independently can require significant **compute, data, hardware, storage, research, and maintenance**, while managed services provide access to existing models with less infrastructure burden.

---

## ⚡ 30-Second Revision

1. **Self-hosting → pay for compute + potentially licensing + maintenance.**
    
2. **Token pricing → pay based on tokens processed; usage-based scalability.**
    
3. **AWS Global Infrastructure → Regions + Availability Zones + edge locations.**
    
4. **SageMaker → AWS ML service; JumpStart provides a model hub.**
    
5. **JumpStart → quickly access, fine-tune, deploy models; watch GPU and endpoint costs.**
    
6. **Bedrock → managed API access to multiple AWS and third-party foundation models.**
    
7. **Bedrock Playgrounds → experiment with models, prompts, and inference parameters.**
    
8. **PartyRock → Bedrock-based playground for learning/building simple generative AI apps.**
    
9. **Unused SageMaker endpoint → delete it to avoid unnecessary ongoing cost.**
    
10. **Embeddings → vector representations; vector databases → store/index them for advanced search.**
    
11. **Managed generative AI → reduces infrastructure burden compared with training/hosting your own model.**
    
12. **Cost decisions → consider usage, compute requirements, price-performance, and business needs.**