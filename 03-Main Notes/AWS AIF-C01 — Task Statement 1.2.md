

## Practical Use Cases for AI & Real-World Applications

## 🎯 Exam Essentials

### 1. Fraud Detection — Mastercard

- **AI/ML use case:** Detect potentially fraudulent transactions in real time.
    
- Each transaction can receive a **fraud probability/risk score**.
    
- ML can improve:
    
    - **Fraud detection rate**
        
    - **False-positive reduction**
        
- Generative AI can supplement traditional fraud models by using contextual information such as **transaction history** to assess whether a transaction is consistent with a customer's behavior.
    

**Exam trigger:**

> "Detect fraudulent transactions / suspicious payments / account takeover" → **Fraud detection with ML/AI**

**Important distinction:**  
Traditional ML fraud detection and GenAI can be **combined**; GenAI does not necessarily replace the underlying fraud model.

---

### 2. Natural-Language IVR — DoorDash

DoorDash replaced a touch-tone IVR system with a conversational system using **Amazon Lex**.

- Old system → "Press 1, press 2..."
    
- New system → customer **speaks naturally**
    
- Amazon Lex supports **voice and text conversational interfaces**.
    

Benefits:

- Better customer experience
    
- Lower hold times
    
- Greater self-service adoption
    

**Exam trigger:**

> "Customer speaks to a chatbot/IVR instead of pressing numbers" → **Amazon Lex**

---

### 3. Predictive Maintenance & Environmental Monitoring — Laredo Petroleum

Sensors continuously collect operational data such as:

- Pressure
    
- Temperature
    
- Flow rate
    

ML models analyze this data to identify potential problems.

Use cases:

- **Predictive/proactive maintenance**
    
- Detect leaks
    
- Identify abnormal operational behavior
    
- Reduce potential flaring/venting
    
- Focus maintenance resources where they are most needed
    

AWS components mentioned:

- Data streaming → continuously moves sensor data
    
- **Amazon SageMaker AI** → build/deploy ML models
    

**Exam trigger:**

> "Sensor data + detect problems before failure" → **Predictive maintenance / anomaly detection**

---

### 4. Recommendations + GenAI — Booking.com

Booking.com uses ML to provide **booking recommendations**.

Its AI Trip Planner uses GenAI to interact with customers through natural language.

A simplified flow:

**Customer request → GenAI understands intent → recommendation API retrieves relevant information → GenAI generates response**

The retrieval of external information for use by a generative model is an example of **RAG (Retrieval-Augmented Generation)**.

**Exam trigger:**

> "GenAI retrieves external/current/company information before generating an answer" → **RAG**

### ⚠️ Important RAG clarification

RAG does **not** retrain the foundation model.

Instead:

**Retrieve relevant information → provide it as context → generate answer**

This allows responses to incorporate information that isn't contained in the model's original training data.

---

### 5. Computer Vision + Product Search — Pinterest Lens

Pinterest Lens allows a user to:

**Take a picture → identify/similar objects → find matching products**

This is a **computer vision** use case.

Pinterest maintains labeled product images and retrains its ML model as new objects/products need to be recognized.

Data-labeling tools mentioned:

- **Amazon S3** → store image datasets
    
- **SageMaker Ground Truth** → data labeling
    
- Amazon Mechanical Turk → human workers can assist with labeling
    

**Exam trigger:**

> "Image → identify object/product → find similar products" → **Computer vision**

---

## 🔑 Key Terms

|Term|Meaning|Exam clue|
|---|---|---|
|**Fraud detection**|Identify potentially fraudulent activity|Suspicious transaction|
|**False positive**|Legitimate activity incorrectly classified as fraud|"Valid transaction flagged as fraud"|
|**Amazon Lex**|Builds voice/text conversational interfaces|Chatbot, conversational IVR|
|**Predictive maintenance**|Use data/ML to identify problems before failure|Sensors + prevent breakdown|
|**Anomaly detection**|Identify unusual patterns/behavior|Abnormal sensor reading|
|**Computer vision**|AI/ML applied to images/video|Identify objects in images|
|**SageMaker AI**|Build/train/deploy ML models|Custom ML|
|**SageMaker Ground Truth**|Data-labeling capability|Label training data|
|**RAG**|Retrieve external information and give it to a GenAI model as context|Current/private/external knowledge|
|**GenAI**|Generates new content|Natural-language generation|

---

## ⚔️ Important Comparisons

### Predictive Maintenance vs Fraud Detection

||Predictive Maintenance|Fraud Detection|
|---|---|---|
|Data|Sensor/operational data|Transaction/customer data|
|Goal|Find potential equipment problems|Find potentially fraudulent activity|
|Typical technique|Prediction/anomaly detection|Classification/risk scoring|
|Example|Detect a failing oil well|Flag suspicious payment|

### RAG vs Retraining

|RAG|Retraining/Fine-tuning|
|---|---|
|Retrieves external information|Changes/adapts model parameters|
|Information supplied at inference time|Training process modifies model|
|Good for changing/current/private knowledge|Used to customize model behavior/knowledge|
|Does not inherently modify model weights|Changes model through additional training|

### Lex vs Other AWS AI Services

|Requirement|Service|
|---|---|
|Conversational chatbot/voice IVR|**Amazon Lex**|
|Speech → text|**Amazon Transcribe**|
|Text → speech|**Amazon Polly**|
|Analyze text sentiment/entities/PII|**Amazon Comprehend**|
|Image/video analysis|**Amazon Rekognition**|
|Document text/forms/tables extraction|**Amazon Textract**|

---

## 🧠 Exam Traps

1. **RAG ≠ retraining**
    
    - RAG retrieves information and supplies it as context.
        
2. **Amazon Lex ≠ Amazon Transcribe**
    
    - Lex → conversational interaction.
        
    - Transcribe → converts speech to text.
        
3. **Predictive maintenance ≠ simply collecting sensor data**
    
    - The important part is using ML/analytics to identify potential problems **before they become failures**.
        
4. **SageMaker Ground Truth ≠ model training**
    
    - Ground Truth is primarily associated with **data labeling**.
        
5. **S3 ≠ ML model**
    
    - S3 can store training datasets, images, and model artifacts, but it isn't itself an ML service.
        
6. **Computer vision ≠ NLP**
    
    - Images/video → computer vision.
        
    - Text/language → NLP.
        
7. **False positives matter in fraud detection**
    
    - A system that flags too many legitimate transactions creates customer friction and operational costs.
        

---

# 📝 Exam Questions

### Q1

A financial institution wants to analyze every payment in real time and assign a probability that the payment is fraudulent. Which AI use case is this?

A. Recommendation  
B. Fraud detection  
C. Machine translation  
D. Text summarization

**Answer: B — Fraud detection**

**Why:** The system evaluates transactions for potential fraudulent activity.

---

### Q2

A company wants customers to interact with its telephone support system by speaking naturally rather than selecting numbers using their phone keypad. Which AWS service is most appropriate?

A. Amazon Transcribe  
B. Amazon Polly  
C. Amazon Lex  
D. Amazon Comprehend

**Answer: C — Amazon Lex**

**Why:** Lex supports conversational voice and text interfaces.

---

### Q3

An oil company collects temperature, pressure, and flow-rate data from equipment. It wants to identify equipment problems early so maintenance teams can intervene before failures occur. What is the primary AI use case?

A. Predictive maintenance  
B. Machine translation  
C. Recommendation  
D. Sentiment analysis

**Answer: A — Predictive maintenance**

---

### Q4

A GenAI travel assistant receives a customer's request, retrieves relevant hotel information and reviews from an external database, and then generates a response using that information. What technique is being used?

A. Fine-tuning  
B. RAG  
C. Supervised learning  
D. Reinforcement learning

**Answer: B — RAG**

**Why:** External information is retrieved and supplied to the generative model as context.

---

### Q5

A retailer wants customers to photograph an object and receive visually similar products from its catalog. Which AI capability is most relevant?

A. Natural language processing  
B. Computer vision  
C. Speech recognition  
D. Time-series forecasting

**Answer: B — Computer vision**

---

### Q6

A company has thousands of unlabeled product images and needs humans to label objects within them before training an ML model. Which AWS capability is relevant?

A. Amazon Lex  
B. SageMaker Ground Truth  
C. Amazon Polly  
D. Amazon Translate

**Answer: B — SageMaker Ground Truth**

---

### Q7

Which statement best describes RAG?

A. It permanently modifies a foundation model's parameters  
B. It retrieves relevant external information and provides it to a generative model  
C. It converts speech into text  
D. It labels training images automatically

**Answer: B**

---

### Q8

A fraud detection system incorrectly blocks many legitimate purchases. What problem is the company experiencing?

A. Underfitting  
B. False positives  
C. Data labeling  
D. Clustering

**Answer: B — False positives**

**Why:** Legitimate transactions are incorrectly classified as fraudulent.

---

# ⚡ 30-Second Revision

Memorize these:

1. **Fraudulent transactions → Fraud detection**
    
2. **Conversational voice/text IVR → Amazon Lex**
    
3. **Sensors + detect failures early → Predictive maintenance**
    
4. **GenAI + retrieved external information → RAG**
    
5. **Image → identify/find similar object → Computer vision**
    
6. **Label training data → SageMaker Ground Truth**
    
7. **S3 → common storage for datasets/model artifacts**
    
8. **RAG supplies information at inference time; it doesn't inherently retrain the model.**
    
9. **False positive = legitimate activity incorrectly flagged.**
    
10. **SageMaker AI = build/train/deploy custom ML models.**
    

### 🧠 One-line mental map

**Fraud → Detect | Voice → Lex | Sensors → Predict | External knowledge → RAG | Images → Vision | Labels → Ground Truth**

This transcript is primarily giving you **scenario recognition**. For AIF-C01, you don't need to memorize the company statistics; memorize **the AI problem → technique/service → business outcome** mapping.