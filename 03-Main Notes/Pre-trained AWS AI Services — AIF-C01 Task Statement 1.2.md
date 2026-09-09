

## 🎯 Exam Essentials

### Core Exam Strategy

Before building and training a custom ML model, check whether **AWS already provides a pre-trained AI service** for the required task.

**Exam trigger:**

> "Common AI capability needed without building/training a custom model" → **Look for an AWS pre-trained AI service**

---

### Amazon Rekognition

- **Amazon Rekognition:** Pre-trained deep learning service for **computer vision**.
    
- Works with:
    
    - Images
        
    - Videos
        
    - Streaming video
        
- Important capabilities:
    
    - **Face detection/recognition**
        
    - Object detection and labeling
        
    - Custom Labels for proprietary objects
        
    - Image/video content moderation
        
    - Text detection in images
        

**Exam triggers:**

> "Identify/recognize faces" → **Amazon Rekognition**

> "Detect objects in images or video" → **Amazon Rekognition**

> "Detect inappropriate/explicit content in uploaded images/videos" → **Amazon Rekognition**

> "Analyze streaming video for objects/faces" → **Amazon Rekognition**

---

### Amazon Textract

- **Amazon Textract:** Extracts information from **documents**.
    
- Can extract:
    
    - Printed text
        
    - Handwriting
        
    - Forms
        
    - Tables
        
- Think of Textract as:
    

> **Document → usable text/data**

**Exam trigger:**

> "Extract text, handwriting, forms, or tables from scanned documents" → **Amazon Textract**

---

### Amazon Comprehend

- **Amazon Comprehend:** NLP service for discovering insights and relationships in **text**.
    
- Important use cases:
    
    - **Sentiment analysis**
        
    - Entity detection
        
    - **PII detection**
        
    - Text classification
        
- Can provide **confidence scores** for detected entities/results.
    

**Exam triggers:**

> "Determine whether customer feedback is positive/negative/neutral" → **Amazon Comprehend**

> "Find names, addresses, phone numbers, or other PII in text" → **Amazon Comprehend**

---

### Textract + Comprehend

These services can be used **together**.

Example:

```text
Scanned customer document
        ↓
Amazon Textract
        ↓
Extract text
        ↓
Amazon Comprehend
        ↓
Analyze sentiment / detect entities / identify PII
```

**Exam trigger:**

> "Extract text from a document and then analyze the extracted text" → **Textract + Comprehend**

---

### Amazon Lex

- **Amazon Lex:** Builds **voice and text conversational interfaces**.
    
- Common use cases:
    
    - Customer service chatbots
        
    - Interactive voice response (IVR)
        
    - Conversational interfaces
        

**Exam trigger:**

> "Build a chatbot that interacts with customers through text or voice" → **Amazon Lex**

---

### Amazon Transcribe

- **Amazon Transcribe:** Automatic **speech-to-text** service.
    
- Converts live or recorded audio/video into text.
    
- Useful for:
    
    - Transcription
        
    - Captions
        
    - Search and analysis of spoken content
        

**Exam trigger:**

> "Convert recorded/live speech or audio into text" → **Amazon Transcribe**

> **Speech → Text = Transcribe**

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Pre-trained AI service**|AWS service with models already trained for common AI tasks|
|**Computer vision**|AI for understanding images/video|
|**NLP**|AI for processing and understanding human language|
|**Face recognition**|Identifying/matching faces in images or video|
|**Object detection**|Identifying objects in images/video|
|**Content moderation**|Detecting potentially inappropriate/unsafe visual content|
|**Sentiment analysis**|Determining sentiment expressed in text|
|**PII**|Personally identifiable information|
|**OCR**|Optical character recognition; extracting text from images/documents|
|**Entity**|A meaningful item detected in text, such as a person or organization|
|**Confidence score**|Model's estimated confidence in a detected result|
|**Speech recognition**|Converting spoken language into text|

---

## ⚔️ Important Comparisons

### AWS AI Service Selection

|Service|Use when|Key distinction|
|---|---|---|
|**Amazon Rekognition**|Images/video|Computer vision|
|**Amazon Textract**|Documents|Extract text, forms, tables, handwriting|
|**Amazon Comprehend**|Text|NLP, sentiment, entities, PII|
|**Amazon Lex**|Conversations|Build voice/text chatbots|
|**Amazon Transcribe**|Speech/audio/video|Speech → text|

### 🔥 Most Important Memory Table

|Scenario wording|Answer|
|---|---|
|👁️ Analyze image/video|**Rekognition**|
|👤 Recognize a face|**Rekognition**|
|🚨 Detect inappropriate image/video content|**Rekognition**|
|📄 Extract text from scanned document|**Textract**|
|📊 Extract tables/forms|**Textract**|
|😊 Analyze sentiment|**Comprehend**|
|🔐 Detect PII in text|**Comprehend**|
|💬 Build chatbot|**Lex**|
|🎙️ Speech → text|**Transcribe**|

---

## 🧠 Exam Traps

- **Trap:** Textract performs sentiment analysis on documents.
    
    - **Correct:** **Textract extracts information** from documents. **Comprehend analyzes text**.
        
- **Trap:** Rekognition converts speech to text.
    
    - **Correct:** **Transcribe** converts speech/audio to text. Rekognition focuses on **images/video**.
        
- **Trap:** Comprehend extracts tables and forms from scanned documents.
    
    - **Correct:** **Textract** extracts document content such as forms and tables.
        
- **Trap:** Lex is primarily a document OCR service.
    
    - **Correct:** **Lex builds conversational interfaces/chatbots**.
        
- **Trap:** If a company needs to build a custom ML model for sentiment analysis, it must start from scratch.
    
    - **Correct:** Check **Amazon Comprehend** first because sentiment analysis is a built-in NLP capability.
        
- **Trap:** PII detection automatically means removing PII.
    
    - **Correct:** **Comprehend can detect PII**; an application can then use that result in a workflow to redact/remove it.
        
- **Trap:** "Text" always means Amazon Comprehend.
    
    - **Correct:** If the text is **inside a scanned document and needs to be extracted**, think **Textract first**. If you need to **analyze the extracted text**, think **Comprehend**.
        

---

## 📝 Exam Questions

### Question 1

A company wants to automatically identify faces and objects in videos uploaded by customers.

Which AWS service is MOST appropriate?

A. Amazon Comprehend  
B. Amazon Rekognition  
C. Amazon Transcribe  
D. Amazon Textract

**Answer:** B

**Why:** Rekognition provides **computer vision** capabilities for images and videos, including faces and objects.

---

### Question 2

A financial company receives thousands of scanned loan documents. It needs to automatically extract handwritten information, tables, and form fields.

Which AWS service should it use?

A. Amazon Lex  
B. Amazon Comprehend  
C. Amazon Textract  
D. Amazon Rekognition

**Answer:** C

**Why:** **Textract** is designed to extract text, handwriting, forms, and tables from documents.

---

### Question 3

A company wants to analyze customer reviews to determine whether customers are positive, negative, or neutral toward its products.

Which AWS service is MOST appropriate?

A. Amazon Comprehend  
B. Amazon Textract  
C. Amazon Transcribe  
D. Amazon Rekognition

**Answer:** A

**Why:** **Sentiment analysis of text** is a core Amazon Comprehend use case.

---

### Question 4

A company wants to automatically identify names, addresses, phone numbers, and credit card information contained in customer emails.

Which AWS service is MOST appropriate?

A. Amazon Lex  
B. Amazon Rekognition  
C. Amazon Comprehend  
D. Amazon Transcribe

**Answer:** C

**Why:** Amazon Comprehend can identify **PII entities in text**.

---

### Question 5

A company wants to create a customer-service application that allows customers to communicate with a virtual assistant using text and voice.

Which AWS service is MOST appropriate?

A. Amazon Lex  
B. Amazon Textract  
C. Amazon Rekognition  
D. Amazon Transcribe

**Answer:** A

**Why:** **Amazon Lex** is designed for building conversational voice and text interfaces.

---

### Question 6

A media company wants to automatically convert recorded interviews into searchable text.

Which AWS service should it use?

A. Amazon Comprehend  
B. Amazon Rekognition  
C. Amazon Transcribe  
D. Amazon Lex

**Answer:** C

**Why:** **Transcribe converts speech/audio into text**.

---

### Question 7

A company wants to extract text from scanned documents and then determine the sentiment of the extracted customer comments.

Which combination is MOST appropriate?

A. Rekognition + Lex  
B. Textract + Comprehend  
C. Transcribe + Rekognition  
D. Lex + Transcribe

**Answer:** B

**Why:** **Textract extracts the document text**, then **Comprehend analyzes the text**, including sentiment.

---

### Question 8

A social media platform wants to automatically detect potentially inappropriate or violent content in user-uploaded videos before sending suspicious content to human reviewers.

Which AWS service is MOST appropriate?

A. Amazon Comprehend  
B. Amazon Textract  
C. Amazon Rekognition  
D. Amazon Transcribe

**Answer:** C

**Why:** Rekognition provides **image/video content moderation** capabilities and can flag content for further review.

---

## ⚡ 30-Second Revision

- **Before custom ML → check AWS pre-trained AI services.**
    
- **Rekognition → images/video → faces, objects, content moderation.**
    
- **Textract → documents → text, handwriting, forms, tables.**
    
- **Comprehend → text → sentiment, entities, PII.**
    
- **Lex → conversational interfaces → chatbots/voice bots.**
    
- **Transcribe → speech → text.**
    
- **Textract + Comprehend:** extract document text → analyze that text.
    
- **Speech → Text = Transcribe.**
    
- **Image/Video → Rekognition.**
    
- **Document → Textract.**
    
- **Text analysis → Comprehend.**
    
- **Chatbot → Lex.**