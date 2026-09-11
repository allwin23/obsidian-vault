



## 🎯 Exam Essentials

### Amazon Polly

- **Amazon Polly:** Converts **text → natural-sounding speech**.
    
- Uses deep learning to synthesize speech.
    
- Common use cases:
    
    - Read articles aloud
        
    - Voice responses in IVR systems
        
    - Accessibility applications
        

**Exam trigger:**

> "Convert written text into spoken audio" → **Amazon Polly**

### 🔥 Remember

> **Polly = Text → Speech**

---

### Amazon Kendra

- **Amazon Kendra:** Intelligent enterprise **search** service.
    
- Uses ML/NLP to understand natural-language questions and find relevant information from enterprise content.
    
- The important idea is **searching an organization's information using natural-language queries**.
    

Example:

> "How do I connect my Echo Plus to my network?"

Kendra interprets the meaning of the question and searches enterprise content for relevant answers.

**Exam trigger:**

> "Employees need to search company documents/information using natural-language questions" → **Amazon Kendra**

---

### Amazon Personalize

- **Amazon Personalize:** Creates **personalized recommendations** for customers.
    
- Uses customer behavior/preferences to generate recommendations.
    
- Common examples:
    
    - "You might also like"
        
    - Product recommendations
        
    - Content recommendations
        
    - Customer segmentation for marketing
        

**Exam trigger:**

> "Recommend products/content specifically for each customer" → **Amazon Personalize**

### 🔥 Remember

> **Personalize = personalized recommendations**

---

### Amazon Translate

- **Amazon Translate:** Converts text from **one language to another**.
    
- Uses neural machine translation to produce fluent translations.
    
- Can be used for:
    
    - Multilingual applications
        
    - Real-time chat translation
        
    - Translating text between languages
        

**Exam trigger:**

> "Translate customer messages from one language to another" → **Amazon Translate**

### 🔥 Remember

> **Translate = Language A → Language B**

---

### Amazon Fraud Detector

- **Amazon Fraud Detector:** Helps identify **potentially fraudulent online activities**.
    
- Example use cases:
    
    - Online payment fraud
        
    - Fake account creation
        
    - Account takeover
        
    - Suspicious online activities
        

**Exam trigger:**

> "Detect potentially fraudulent online transactions/accounts" → **Amazon Fraud Detector**

---

# 🤖 Amazon Bedrock

### What is Amazon Bedrock?

**Amazon Bedrock** is a **fully managed AWS service for building generative AI applications using foundation models**.

You can choose from foundation models provided by various model providers and use them to build GenAI applications without managing the underlying model infrastructure yourself.

**Exam trigger:**

> "Build a generative AI application using foundation models" → **Amazon Bedrock**

---

### Bedrock + Foundation Models

Instead of training a huge model from scratch, you can use an existing **foundation model (FM)** as the starting point.

Conceptually:

```text
Your application
       ↓
   Amazon Bedrock
       ↓
Foundation Model
       ↓
Generated output
```

This makes Bedrock particularly useful when you want to **build GenAI applications without managing the underlying ML infrastructure yourself**.

---

### RAG — Retrieval-Augmented Generation

This is **very important for AIF-C01**.

A foundation model has knowledge learned during its training.

But suppose your company has private information:

> "What is our company's employee leave policy?"

That information may not be in the model's training data.

With **RAG**, the application retrieves relevant information from an external knowledge source and provides it to the model so the model can generate a response grounded in that information.

Conceptually:

```text
User question
      ↓
Retrieve relevant information
      ↓
External knowledge source
      ↓
Foundation model
      ↓
Generated answer
```

**Exam trigger:**

> "Use a company's private/current documents to provide information to a GenAI model" → **RAG**

### 🔥 Critical distinction

> **RAG = retrieve information at inference time**

It does **not** mean retraining the foundation model with your documents.

---

# 🧑‍💻 Amazon SageMaker

### What is SageMaker?

**Amazon SageMaker AI** is AWS's managed platform for **building, training, deploying, and operating custom ML models**.

Think:

> **Bedrock → use foundation models to build GenAI applications**

> **SageMaker → build/customize/train/deploy ML models and workflows**

SageMaker supports ML workflows such as:

- Data preparation
    
- Model development
    
- Training
    
- Model deployment
    
- Inference
    
- Using pretrained models as starting points
    

**Exam trigger:**

> "Data scientists need to build and train a customized ML model" → **Amazon SageMaker AI**

---

## ⚔️ Important Comparisons

### AWS AI Services vs Bedrock vs SageMaker

|Service|Use when|Key distinction|
|---|---|---|
|**Rekognition**|Images/video|Computer vision|
|**Textract**|Documents|Extract text/forms/tables|
|**Comprehend**|Text|NLP analysis|
|**Polly**|Text → speech|Speech synthesis|
|**Transcribe**|Speech → text|Speech recognition|
|**Translate**|Language translation|Text → another language|
|**Lex**|Chatbots/conversation|Voice/text conversational interfaces|
|**Kendra**|Enterprise search|Intelligent search|
|**Personalize**|Recommendations|Personalized content/products|
|**Fraud Detector**|Online fraud|Fraud detection|
|**Bedrock**|GenAI applications|Access/use foundation models|
|**SageMaker AI**|Custom ML|Build/train/deploy customized ML models|

---

### Bedrock vs SageMaker AI — ⭐ VERY IMPORTANT

||Amazon Bedrock|Amazon SageMaker AI|
|---|---|---|
|Primary purpose|Build **GenAI applications**|Build **custom ML solutions**|
|Main focus|Foundation models|ML development/training/deployment|
|Model training from scratch|Not the primary use case|✅ Supported|
|Foundation models|✅ Core capability|Can use pretrained models|
|Best exam scenario|"Build a GenAI app using an FM"|"Build/train/customize an ML model"|

### Simple memory trick:

> **Bedrock = Foundation Models + GenAI**

> **SageMaker = Custom ML**

---

## 🧠 Exam Traps

- **Trap:** Amazon Polly converts speech into text.
    
    - **Correct:** **Polly = text → speech**.
        
    - **Transcribe = speech → text**.
        
- **Trap:** Amazon Kendra is primarily a generative AI model.
    
    - **Correct:** Kendra is an **intelligent enterprise search service**.
        
- **Trap:** Amazon Personalize translates customer content into different languages.
    
    - **Correct:** Personalize is for **personalized recommendations**. Translate handles language translation.
        
- **Trap:** RAG means retraining the foundation model on company documents.
    
    - **Correct:** RAG **retrieves external information and provides it to the model during generation**.
        
- **Trap:** Bedrock and SageMaker are interchangeable.
    
    - **Correct:** **Bedrock** is primarily for building GenAI applications with foundation models; **SageMaker AI** is for broader/custom ML development, training, and deployment.
        
- **Trap:** You should always build a custom model with SageMaker instead of using a pre-trained AWS AI service.
    
    - **Correct:** For common AI tasks, first check whether a **pre-trained AWS AI service** already solves the problem.
        
- **Trap:** Kendra and RAG are exactly the same.
    
    - **Correct:** **Kendra is a search service**. RAG is an **architecture/pattern** in which retrieved information is supplied to a generative model to improve/ground its response.
        

---

## 📝 Exam Questions

### Question 1

A company wants to make its online articles accessible to customers who prefer listening rather than reading.

Which AWS service is MOST appropriate?

A. Amazon Transcribe  
B. Amazon Polly  
C. Amazon Translate  
D. Amazon Comprehend

**Answer:** B

**Why:** **Amazon Polly converts text into natural-sounding speech**.

---

### Question 2

A large company wants employees to ask natural-language questions and quickly find relevant information across internal company documents.

Which AWS service is MOST appropriate?

A. Amazon Personalize  
B. Amazon Kendra  
C. Amazon Polly  
D. Amazon Rekognition

**Answer:** B

**Why:** **Amazon Kendra** provides intelligent enterprise search using natural-language understanding.

---

### Question 3

An ecommerce company wants to display personalized product recommendations based on each customer's previous behavior.

Which AWS service should the company use?

A. Amazon Translate  
B. Amazon Personalize  
C. Amazon Kendra  
D. Amazon Fraud Detector

**Answer:** B

**Why:** **Amazon Personalize** is designed for personalized recommendations.

---

### Question 4

A global company has a chat application where customers communicate in different languages. The company wants to automatically translate messages between languages.

Which AWS service is MOST appropriate?

A. Amazon Comprehend  
B. Amazon Polly  
C. Amazon Translate  
D. Amazon Transcribe

**Answer:** C

**Why:** **Amazon Translate** provides machine translation between languages.

---

### Question 5

A company wants to build a generative AI application that uses an existing foundation model rather than developing a large language model from scratch.

Which AWS service is MOST appropriate?

A. Amazon Rekognition  
B. Amazon Bedrock  
C. Amazon Kendra  
D. Amazon Fraud Detector

**Answer:** B

**Why:** **Amazon Bedrock** provides access to foundation models for building generative AI applications.

---

### Question 6

A company's employees want to ask a generative AI assistant questions about internal policies stored in private company documents. The model should use those documents when generating its answers.

Which approach is MOST appropriate?

A. RAG  
B. Classification  
C. Regression  
D. Clustering

**Answer:** A

**Why:** **RAG retrieves relevant external/private information and provides it to the generative model** when generating the answer.

---

### Question 7

A data science team needs to prepare data, train a customized ML model, deploy it, and create an inference endpoint.

Which AWS service is MOST appropriate?

A. Amazon Polly  
B. Amazon Bedrock  
C. Amazon SageMaker AI  
D. Amazon Translate

**Answer:** C

**Why:** **SageMaker AI** provides capabilities across the custom ML lifecycle, including preparation, training, deployment, and inference.

---

### Question 8

A company wants to identify potentially fraudulent online payment activity and suspicious new account creation.

Which AWS service is MOST appropriate?

A. Amazon Fraud Detector  
B. Amazon Personalize  
C. Amazon Kendra  
D. Amazon Comprehend

**Answer:** A

**Why:** **Amazon Fraud Detector** is designed to identify potentially fraudulent online activities.

---

## ⚡ 30-Second Revision

- **Polly → Text → Speech** 🔊
    
- **Transcribe → Speech → Text** 🎙️
    
- **Translate → Language → Language** 🌎
    
- **Kendra → Intelligent enterprise search** 🔎
    
- **Personalize → Personalized recommendations** 🎯
    
- **Fraud Detector → Online fraud detection** 🚨
    
- **Bedrock → Build GenAI apps using foundation models** 🤖
    
- **RAG → Retrieve external/private information → give it to GenAI model**
    
- **SageMaker AI → Build/train/deploy custom ML models** 🧑‍💻
    
- **Big distinction:** **Bedrock = GenAI + foundation models; SageMaker AI = custom ML lifecycle**
    

### 🔥 AWS Service Memory Chain

> **See → Rekognition**  
> **Read document → Textract**  
> **Understand text → Comprehend**  
> **Talk → Polly**  
> **Listen → Transcribe**  
> **Translate → Translate**  
> **Chat → Lex**  
> **Search company info → Kendra**  
> **Recommend → Personalize**  
> **Fraud → Fraud Detector**  
> **GenAI → Bedrock**  
> **Custom ML → SageMaker AI**