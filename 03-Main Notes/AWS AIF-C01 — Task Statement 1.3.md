

## ML Development Lifecycle — Deploying Models for Inference

## 🎯 Exam Essentials

### 1. Deployment = Make the Trained Model Available

After a model has been:

**Trained → Tuned → Evaluated**

the next step is to **deploy it so applications/users can send inference requests**.

The first major decision is:

> **What type of inference does the workload require?**

For AIF-C01, remember the four SageMaker inference options:

1. **Batch**
    
2. **Asynchronous**
    
3. **Serverless**
    
4. **Real-time**
    

---

# 2. Batch Inference

**Batch inference = process a large amount of data offline when you don't need an immediate response.**

Example:

> A retailer collects the previous day's sales and wants predictions every morning.

Workflow:

**Large dataset → Batch inference → Results later**

Characteristics:

- Offline
    
- Large datasets
    
- No persistent endpoint required
    
- Results can wait
    
- Often more cost-effective when inference happens periodically
    

### 🧠 Exam trigger

> "Process thousands/millions of records overnight"  
> "No immediate response required"  
> "Large dataset"  
> → **Batch inference / SageMaker Batch Transform**

---

# 3. Real-Time Inference

**Real-time inference = persistent endpoint that responds immediately to requests.**

Example:

> A web application sends a customer request and needs the model's prediction immediately.

Workflow:

**Client → REST API → Endpoint → Model → Response**

Characteristics:

- Immediate/low-latency responses
    
- Persistent endpoint
    
- Suitable for interactive applications
    
- Suitable for sustained traffic
    

### 🧠 Exam trigger

> "User needs an immediate prediction"  
> "Interactive application"  
> "Low-latency response"  
> → **Real-time inference**

---

# 4. Asynchronous Inference

**Asynchronous inference = queue inference requests and process them asynchronously.**

Useful when:

- Requests can wait
    
- Payloads are large
    
- Processing can take a long time
    
- You don't need an immediate synchronous response
    

A major benefit mentioned in the lesson:

> SageMaker can **scale the endpoint down to zero** when there are no requests, reducing idle compute costs.

### 🧠 Exam trigger

> "Large payload + long processing time + response doesn't need to be immediate"  
> → **Asynchronous inference**

---

# 5. Serverless Inference

**Serverless inference = real-time inference without managing ML compute instances directly.**

SageMaker runs the inference workload using **AWS Lambda**.

Useful when:

- Traffic is intermittent
    
- There may be periods with no requests
    
- You don't want to provision/manage instances
    
- Workload doesn't justify continuously running instances
    

### 🧠 Exam trigger

> "Real-time inference + unpredictable/intermittent traffic + don't want to manage instances"  
> → **Serverless inference**

---

# ⚔️ The Four SageMaker Inference Options ⭐⭐⭐

|Type|Best for|Endpoint behavior|Key clue|
|---|---|---|---|
|**Batch Transform**|Large offline datasets|No persistent endpoint required|"Process overnight"|
|**Asynchronous**|Large/long-running requests|Queues requests; can scale down|"Large payload / long processing"|
|**Serverless**|Intermittent real-time traffic|Lambda-based|"Traffic varies / idle periods"|
|**Real-time**|Interactive, sustained traffic|Persistent endpoint|"Immediate response"|

### 🧠 Easiest way to remember

**Batch → Wait**

**Async → Queue**

**Serverless → Intermittent**

**Real-time → Immediate**

---

# 6. REST API & Inference

Applications commonly communicate with deployed models through an **API**.

A simplified flow:

**Client application**

↓ HTTP request

**REST API**

↓

**Inference endpoint**

↓

**Model**

↓

**Prediction**

↓

**HTTP response**

For example, a web application could send a **POST** request containing input data.

---

# 7. Amazon API Gateway + Lambda

The lesson gives an example architecture:

**Client → Amazon API Gateway → AWS Lambda → Model**

- **API Gateway** can provide the HTTP/API interface.
    
- **Lambda** executes the backend code.
    

This is a general AWS architecture pattern.

### ⚠️ Exam distinction

Don't automatically assume:

> "API Gateway = ML inference service."

API Gateway is an **API management/interface service**.

The model itself runs on an appropriate compute/inference platform.

---

# 8. Containers for Model Deployment

Inference code and model artifacts can commonly be packaged into **Docker containers**.

Containers can run on many AWS compute services, including:

- Amazon ECS
    
- Amazon EKS
    
- Amazon EC2
    
- AWS Lambda
    
- AWS Batch
    

But using these services may require you to manage more infrastructure, such as:

- Scaling
    
- Patching
    
- Updates
    
- Networking
    
- Routing
    
- Security
    

---

# 9. SageMaker Managed Endpoints ⭐

Instead of managing all of this infrastructure yourself, you can use **Amazon SageMaker AI** to host the model.

You provide SageMaker with:

- **Model artifacts** → typically in Amazon S3
    
- **Container image** → typically in Amazon ECR
    
- Desired inference configuration
    

SageMaker manages the endpoint infrastructure for you.

### Mental model

**S3 model artifacts + ECR container → SageMaker → managed inference endpoint**

This reduces operational overhead.

---

# 10. SageMaker Inference Recommender

**Inference Recommender** helps determine an appropriate deployment configuration for your model.

It can test different configurations so you can select an option that provides an appropriate balance of:

- Performance
    
- Cost
    
- Resource configuration
    

### 🧠 Exam trigger

> "Test different instance/configuration options to determine the best deployment configuration"  
> → **SageMaker Inference Recommender**

---

# 🔑 Key Terms

|Term|Meaning|Exam clue|
|---|---|---|
|**Inference**|Using a trained model to produce predictions|New input → prediction|
|**Batch inference**|Offline inference over a dataset|Large dataset, can wait|
|**Batch Transform**|SageMaker capability for batch inference|Offline processing|
|**Asynchronous inference**|Queue requests for later processing|Large payload/long processing|
|**Serverless inference**|Real-time inference without managing instances|Intermittent traffic|
|**Real-time inference**|Persistent endpoint for immediate responses|Interactive/low latency|
|**Inference endpoint**|Interface where applications send inference requests|Model API|
|**API Gateway**|Managed API/HTTP interface|Client API|
|**Amazon ECR**|Container image registry|Docker image|
|**Inference Recommender**|Tests deployment configurations|Choose configuration|
|**Auto scaling**|Adjust compute capacity based on workload|Variable traffic|

---

# 🧠 Exam Traps

### Trap 1 — Batch = real-time ❌

Batch is specifically for situations where **you can wait**.

---

### Trap 2 — Serverless means no real-time inference ❌

Serverless inference **can provide real-time inference**.

The difference is that you don't directly provision/manage ML compute instances.

---

### Trap 3 — Asynchronous = batch ❌

Both can tolerate waiting, but they're different:

- **Batch** → process a dataset as a batch.
    
- **Async** → individual requests can be queued and processed asynchronously, particularly useful for large payloads/long processing.
    

---

### Trap 4 — Real-time always means unlimited traffic ❌

Real-time inference is appropriate when **immediate responses** are required. Capacity still depends on the endpoint configuration and scaling.

---

### Trap 5 — SageMaker doesn't create the model ❌

In this context, SageMaker is hosting/deploying the **already trained model**.

---

### Trap 6 — ECR stores model artifacts ❌

- **ECR → container images**
    
- **S3 → model artifacts/data**
    

---

### Trap 7 — API Gateway runs the ML model ❌

API Gateway provides the API interface. The actual model executes on the selected compute/inference environment.

---

# 📝 Exam Questions

### Q1

A retailer wants to run predictions against 500 GB of sales data every night. The predictions do not need to be available immediately. Which inference option is most appropriate?

A. Real-time inference  
B. Serverless inference  
C. Batch Transform  
D. Amazon Lex

**Answer: C — Batch Transform**

**Why:** Large offline datasets where results can wait are a classic batch inference workload.

---

### Q2

A mobile application requires an immediate prediction whenever a customer submits a request. The application receives sustained traffic throughout the day. Which option is most appropriate?

A. Batch Transform  
B. Real-time inference  
C. Asynchronous inference  
D. Offline processing

**Answer: B — Real-time inference**

---

### Q3

An application sends large inference requests that can take several minutes to process. The user does not require an immediate response. Which SageMaker option is appropriate?

A. Real-time inference  
B. Asynchronous inference  
C. Batch Transform only  
D. Serverless inference

**Answer: B — Asynchronous inference**

---

### Q4

A company has an inference workload that receives requests only occasionally. It wants real-time responses but does not want to manage or provision ML compute instances. Which option should it consider?

A. Serverless inference  
B. Batch Transform  
C. Real-time inference with permanently provisioned instances  
D. SageMaker Ground Truth

**Answer: A — Serverless inference**

---

### Q5

A company wants SageMaker to host its trained model while minimizing the amount of infrastructure management required by its developers. What should it use?

A. SageMaker managed endpoint  
B. Amazon S3 alone  
C. Amazon ECR alone  
D. AWS Glue

**Answer: A**

---

### Q6

A company has a trained model and wants to evaluate different deployment configurations to determine which provides an appropriate performance/cost configuration. Which SageMaker capability can help?

A. Ground Truth  
B. Feature Store  
C. Inference Recommender  
D. DataBrew

**Answer: C — Inference Recommender**

---

### Q7

A web application sends a POST request to an HTTP endpoint. The request is forwarded to backend code that executes model inference and returns the prediction. What role can API Gateway play?

A. Training the model  
B. Providing the API interface for clients  
C. Labeling training data  
D. Storing model weights

**Answer: B**

---

### Q8

Which pairing is correct?

A. ECR → model artifacts; S3 → container images  
B. ECR → container images; S3 → model artifacts  
C. ECR → labels; S3 → hyperparameters  
D. ECR → predictions; S3 → API requests

**Answer: B**

---

# ⚡ 30-Second Revision

1. **Batch → large dataset + can wait.**
    
2. **Real-time → immediate interactive response.**
    
3. **Async → queued requests + large payloads/long processing.**
    
4. **Serverless → real-time + intermittent traffic + no instance management.**
    
5. **SageMaker can provide fully managed inference endpoints.**
    
6. **S3 → model artifacts.**
    
7. **ECR → Docker/container images.**
    
8. **API Gateway → API interface, not the ML model itself.**
    
9. **Inference Recommender → test deployment configurations.**
    
10. **Batch Transform → offline batch inference.**
    

### 🧠 Ultimate decision tree

**Need immediate response?**

→ **YES** → Is traffic sustained?

→ **YES → Real-time**

→ **NO / intermittent → Serverless**

**NO, can wait?**

→ Large dataset processed together → **Batch**

→ Individual/large/long-running requests → **Asynchronous**