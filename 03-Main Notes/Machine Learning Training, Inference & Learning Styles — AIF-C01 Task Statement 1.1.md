

## 🎯 Exam Essentials

### Model Artifacts & Deployment

- **Model artifacts:** Output of the training process. Typically contain:
    
    - Trained parameters
        
    - Model definition
        
    - Metadata
        
- **Amazon S3:** Commonly used to store model artifacts.
    
- **Inference code:** Software that loads/uses the model artifacts to perform inference.
    

### Real-Time vs Batch Inference

|Concept|Use when|Key distinction|
|---|---|---|
|**Real-time inference**|Predictions must be returned quickly|Persistent endpoint; low latency|
|**Batch inference**|Large amounts of data are available upfront and immediate results aren't required|Processes data together; compute runs when needed|

- **Real-time:** Best for online applications requiring **low latency** and potentially sustained request traffic.
    
- **Batch:** Best for **offline processing** of large datasets where waiting for results is acceptable.
    
- Batch inference can be **more cost-effective** when a persistent endpoint isn't needed.
    

**Exam trigger:**

- "User expects an immediate prediction" → **Real-time inference**
    
- "Process millions of records overnight/monthly" → **Batch inference**
    
- "No need for an always-available endpoint" → **Batch inference**
    

---

### Supervised Learning

- **Supervised learning:** Training with **labeled data**, where both inputs and expected outputs are provided.
    
- The model learns the relationship between features and the known target/label.
    
- Common uses include **classification** and **regression**.
    
- Classification models may output a **probability/confidence** rather than simply a guaranteed category.
    

**Exam trigger:** "Historical data contains the correct answers/labels" → **Supervised learning**

### Amazon SageMaker Ground Truth

- **Amazon SageMaker Ground Truth:** AWS service for **data labeling** to create labeled datasets for ML.
    
- Can use human workers to label data.
    
- The transcript mentions **Amazon Mechanical Turk** as a crowdsourcing option.
    

**Exam trigger:** "Need humans to label a large dataset for ML training" → **SageMaker Ground Truth**

---

### Unsupervised Learning

- **Unsupervised learning:** Training with **unlabeled data**.
    
- The algorithm discovers patterns or structure within the data.
    
- Common applications:
    
    - **Clustering**
        
    - Pattern recognition
        
    - Anomaly detection
        
    - Grouping similar data
        

**Exam trigger:** "No labels; automatically find groups/patterns" → **Unsupervised learning**

**Example:** Grouping network traffic into different behavioral patterns or detecting unusual sensor readings.

---

### Reinforcement Learning

- **Reinforcement learning (RL):** An **agent** learns which actions to take in an **environment** to achieve a defined goal.
    
- Learning occurs through **trial and error**.
    
- Actions receive **rewards** or unfavorable outcomes based on how well they move toward the goal.
    
- RL does **not require labeled training examples**.
    
- Exploration is important: the agent may try actions that don't immediately produce rewards.
    

**AWS DeepRacer example:**

- Agent → race car
    
- Environment → racetrack
    
- Actions → car movements
    
- Goal → complete the track efficiently/stay on track
    
- Reward → feedback encouraging desirable behavior
    

**Exam trigger:** "Agent takes actions, receives rewards, and learns toward a goal" → **Reinforcement learning**

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Model artifact**|Trained model components, including parameters and model definition|
|**Inference code**|Software that uses model artifacts to perform inference|
|**Real-time inference**|Immediate prediction through a persistent endpoint|
|**Batch inference**|Offline inference over a dataset without requiring a persistent endpoint|
|**Supervised learning**|Learning from labeled input/output examples|
|**Unsupervised learning**|Finding patterns/groups in unlabeled data|
|**Reinforcement learning**|Agent learns actions through rewards and trial/error|
|**Label**|Known expected output associated with training data|
|**Clustering**|Grouping similar data points without predefined labels|
|**Agent**|Entity that takes actions in an RL environment|
|**Environment**|Context in which an RL agent operates|
|**Reward**|Feedback indicating how desirable an RL action was|
|**Exploration**|Trying different actions to discover better strategies|

---

## ⚔️ Important Comparisons

### Learning Styles

|Learning style|Training data|Main idea|Typical use|
|---|---|---|---|
|**Supervised**|Labeled|Learn input → known output relationship|Classification, regression|
|**Unsupervised**|Unlabeled|Discover patterns/structure|Clustering, anomaly detection|
|**Reinforcement**|No labeled examples required|Learn actions through rewards|Autonomous decision-making|

### Inference Types

|Type|Best for|Infrastructure|
|---|---|---|
|**Real-time**|Immediate predictions|Persistent endpoint|
|**Batch**|Large offline workloads|Compute runs when batch is processed|

---

## 🧠 Exam Traps

- **Trap:** Unsupervised learning and reinforcement learning are basically the same because neither requires labeled data.
    
    - **Correct:** Both can operate without labeled training data, but **unsupervised learning discovers patterns**, while **reinforcement learning learns actions toward a predetermined goal using rewards**.
        
- **Trap:** Batch inference is always cheaper than real-time inference.
    
    - **Correct:** Batch **can** be more cost-effective when immediate results and a persistent endpoint aren't required.
        
- **Trap:** Real-time inference means the model is continuously training.
    
    - **Correct:** Real-time inference means the **trained model is continuously available to process requests**. Training and inference are separate processes.
        
- **Trap:** Supervised learning requires only input features.
    
    - **Correct:** Supervised learning uses **labeled training data**, meaning the expected output is known.
        
- **Trap:** Reinforcement learning requires a labeled dataset containing the correct action for every situation.
    
    - **Correct:** RL learns through **actions, environmental feedback, and rewards**, rather than conventional labeled examples.
        
- **Trap:** Clustering requires predefined categories.
    
    - **Correct:** Unsupervised clustering **discovers groups** in unlabeled data.
        

---

## 📝 Exam Questions

### Question 1

An online fraud detection application must return a prediction to a customer transaction within milliseconds. The model receives a continuous stream of requests.

Which inference approach is MOST appropriate?

A. Batch inference  
B. Real-time inference  
C. Unsupervised learning  
D. Reinforcement learning

**Answer:** B

**Why:** Real-time inference uses a persistent endpoint designed for **low-latency online predictions**.

---

### Question 2

A retailer has millions of historical sales records and wants to run inventory forecasts once a month. The results do not need to be available immediately.

Which approach is MOST appropriate?

A. Real-time inference  
B. Batch inference  
C. Reinforcement learning  
D. Online training

**Answer:** B

**Why:** The data is available upfront and immediate results aren't required, making **batch inference** appropriate.

---

### Question 3

A company has 100,000 images and wants to train a model to distinguish defective products from non-defective products. Each image has already been labeled as "defective" or "non-defective."

Which learning approach should the company use?

A. Unsupervised learning  
B. Reinforcement learning  
C. Supervised learning  
D. Clustering

**Answer:** C

**Why:** The training data contains **known labels**, which is the defining characteristic of supervised learning.

---

### Question 4

A company has a large collection of network traffic records without labels. It wants an ML system to automatically discover groups of similar traffic patterns.

Which approach is MOST appropriate?

A. Supervised learning  
B. Unsupervised learning  
C. Reinforcement learning  
D. Batch inference

**Answer:** B

**Why:** **Unsupervised learning** can discover patterns and clusters in unlabeled data.

---

### Question 5

An organization wants an ML system to control an autonomous device. The system should learn which actions are most effective by receiving positive feedback when it moves closer to a defined objective.

Which ML approach should be used?

A. Supervised learning  
B. Unsupervised learning  
C. Reinforcement learning  
D. Regression

**Answer:** C

**Why:** An **agent learning actions through rewards toward a goal** is the classic reinforcement learning scenario.

---

### Question 6

A company needs thousands of people to label images so that the resulting dataset can be used to train an ML model.

Which AWS service is designed to help with this requirement?

A. Amazon SageMaker Ground Truth  
B. Amazon Transcribe  
C. Amazon Polly  
D. Amazon Rekognition

**Answer:** A

**Why:** **SageMaker Ground Truth** supports creating labeled training datasets through data-labeling workflows.

---

### Question 7

An ML model has finished training. The trained parameters and model definition are stored as model artifacts. The company now wants to generate predictions for new customer data.

What process is being performed?

A. Training  
B. Inference  
C. Labeling  
D. Clustering

**Answer:** B

**Why:** Applying a trained model to new data to produce predictions is **inference**.

---

## ⚡ 30-Second Revision

- **Training →** learns model parameters; produces model artifacts.
    
- **Inference →** uses trained model to make predictions.
    
- **Real-time →** persistent endpoint + low latency + online requests.
    
- **Batch →** large offline dataset + results can wait + no persistent endpoint required.
    
- **Supervised →** **labeled data** → classification/regression.
    
- **Unsupervised →** **unlabeled data** → discover patterns/clusters/anomalies.
    
- **Reinforcement →** **agent + environment + actions + rewards + goal**.
    
- **SageMaker Ground Truth →** data labeling for ML.
    
- **S3 →** commonly stores model artifacts and training data.
    
- **Big exam distinction:** Unsupervised **discovers patterns**; reinforcement learning **learns actions toward a goal**.