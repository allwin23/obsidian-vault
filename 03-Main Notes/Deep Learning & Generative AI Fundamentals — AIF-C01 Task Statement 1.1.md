#
## 🎯 Exam Essentials

### Deep Learning

- **Deep learning (DL)** is a subset of **machine learning** that uses **neural networks with multiple layers**.
    
- A deep neural network generally contains:
    
    - **Input layer** → receives input features
        
    - **Hidden layers** → learn increasingly complex patterns
        
    - **Output layer** → produces the prediction/output
        
- During training, the model adjusts **weights** to reduce the difference between predicted and actual outputs.
    
- Deep learning is especially useful for **complex, high-dimensional, unstructured data**, such as:
    
    - Images
        
    - Video
        
    - Audio
        
    - Text
        

**Exam trigger:**

> "Neural networks / multiple hidden layers / automatically learns features from images or text" → **Deep learning**

---

### Traditional ML vs Deep Learning

||Traditional ML|Deep Learning|
|---|---|---|
|Typical data|Structured/tabular|Unstructured|
|Feature engineering|Often requires more human involvement|Can automatically learn useful features|
|Model|Many possible algorithms|Neural networks|
|Compute requirements|Generally lower|Generally higher|
|Example|Customer churn prediction|Image recognition|
|Example data|Customer records|Images/text/video|

**Important:** This is a **general rule, not an absolute rule**. Modern ML systems can work with many data types.

---

### Neural Networks

- Neural networks consist of interconnected **nodes** arranged in layers.
    
- Nodes apply learned **weights** to inputs.
    
- Information flows through the network from input toward output during **forward propagation**.
    
- During training, weights are adjusted to reduce prediction error.
    

**Core idea to remember:**

> **Training → adjust weights → reduce error → better predictions**

---

## 🤖 Generative AI

- **Generative AI (GenAI):** AI that can **generate new content** such as text, images, audio, video, or code.
    
- Modern GenAI commonly uses **deep learning models** trained on very large datasets.
    
- **Foundation models (FMs):** Large pretrained models that can be adapted to perform many different tasks.
    
- **Large language models (LLMs):** Foundation models specialized in processing and generating language.
    
- **Transformers:** Neural-network architecture widely used for modern foundation models and LLMs.
    

### Transformer

The transcript's key exam point is that transformers can process sequence information **in parallel**, making large-scale training much more efficient than architectures that process tokens strictly one at a time.

**Exam trigger:**

> "Architecture behind modern LLMs/foundation models" → **Transformer**

---

### Prompt → Response

In a generative AI application:

**Prompt → Model → Generated response**

A **prompt** is the input/instruction provided to the model.

Example:

> Prompt: "Summarize this article."

> Output: A generated summary.

---

### What LLMs Can Do

Because LLMs are trained on extremely large language datasets, they can perform tasks such as:

- Text generation
    
- Summarization
    
- Translation
    
- Question answering
    
- Code generation
    
- Classification of text
    
- Content creation
    

The important exam concept isn't memorizing every capability. Understand that **one foundation model can support many different tasks**.

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Deep Learning**|ML using multi-layer neural networks|
|**Neural Network**|Model composed of interconnected computational nodes organized in layers|
|**Node**|Computational unit within a neural network|
|**Weight**|Learned value determining the influence of an input|
|**Hidden Layer**|Intermediate neural-network layer that learns representations/patterns|
|**Feature Engineering**|Selecting/transforming useful input features|
|**Generative AI**|AI that generates new content|
|**Foundation Model**|Large pretrained model adaptable to many tasks|
|**LLM**|Foundation model focused primarily on language|
|**Transformer**|Neural-network architecture used extensively for modern GenAI models|
|**Prompt**|Input/instruction given to a generative AI model|
|**Inference**|Using a trained model to produce an output|

---

## ⚔️ Important Comparisons

### AI → ML → Deep Learning → Generative AI

Think of these as related concepts, **not four completely separate technologies**:

```text
Artificial Intelligence
        ↓
   Machine Learning
        ↓
   Deep Learning
        ↓
Generative AI
```

⚠️ This hierarchy is useful for understanding relationships, but **Generative AI is not simply "the deepest level of AI."** GenAI refers to the capability of generating content and can be implemented using different model architectures.

---

### Traditional ML vs Deep Learning

|Scenario|Likely choice|Why|
|---|---|---|
|Customer churn from structured customer records|Traditional ML|Structured/tabular data|
|Predict numerical sales value|Traditional ML|Often effective and efficient|
|Image classification|Deep learning|Complex visual patterns|
|Natural language processing|Deep learning|Complex language relationships|
|Video analysis|Deep learning|High-dimensional unstructured data|

---

### Foundation Model vs LLM

|Concept|Meaning|
|---|---|
|**Foundation model**|Broad pretrained model that can support many tasks/modalities|
|**LLM**|Foundation model designed primarily for language|

**Remember:**  
**LLM ⊂ Foundation Models** is a useful mental model, although foundation models can also specialize in images, audio, multimodal inputs, etc.

---

## 🧠 Exam Traps

- **Trap:** Deep learning and machine learning are completely separate technologies.
    
    - **Correct:** **Deep learning is a subset of machine learning.**
        
- **Trap:** Deep learning always requires humans to manually select every feature.
    
    - **Correct:** Deep neural networks can **learn useful features automatically**, reducing manual feature engineering.
        
- **Trap:** Neural networks are used only for image recognition.
    
    - **Correct:** They are also heavily used for **language, speech, video, and other tasks**.
        
- **Trap:** Every ML problem should use deep learning because it is more advanced.
    
    - **Correct:** Traditional ML can be more efficient and effective for many **structured/tabular-data** problems.
        
- **Trap:** An LLM can perform only text generation.
    
    - **Correct:** LLMs can support many language tasks, including **summarization, translation, classification, question answering, and code generation**.
        
- **Trap:** Generative AI and LLM mean exactly the same thing.
    
    - **Correct:** **Generative AI is the broader concept** of generating content. LLMs are models specialized in language and can be used for GenAI.
        
- **Trap:** Transformers process every token strictly one after another.
    
    - **Correct:** Transformers use mechanisms that allow sequence elements to be processed much more **in parallel** during training.
        

---

## 📝 Exam Questions

### Question 1

A company needs to classify millions of images of products into different categories. The company wants a model that can automatically learn useful visual features from the images.

Which approach is MOST appropriate?

A. Traditional SQL queries  
B. Deep learning using neural networks  
C. Manual rule-based classification only  
D. Relational database indexing

**Answer:** B

**Why:** Deep learning neural networks are highly suitable for learning complex patterns and features from **unstructured image data**.

---

### Question 2

A company wants to predict customer churn using structured customer records containing age, contract length, monthly spending, and previous churn history.

Which approach would generally be an appropriate starting point?

A. Traditional machine learning  
B. Transformer-based image generation  
C. Computer vision  
D. Reinforcement learning

**Answer:** A

**Why:** Customer records are **structured/tabular data**, where traditional ML algorithms can be efficient and effective.

---

### Question 3

During training of a neural network, the model's predictions contain errors. The training process repeatedly changes learned weights to reduce those errors.

What is the PRIMARY purpose of adjusting the weights?

A. To increase database storage capacity  
B. To improve the model's predictions  
C. To convert structured data into JSON  
D. To create additional training labels

**Answer:** B

**Why:** Neural-network weights are learned during training to improve the model's ability to produce accurate outputs.

---

### Question 4

A developer wants to build an application that accepts natural-language instructions and generates responses, summaries, and computer code.

Which technology is MOST directly suited to this requirement?

A. Large language model  
B. Relational database  
C. Object storage  
D. Traditional clustering algorithm

**Answer:** A

**Why:** **LLMs** are designed to understand and generate human language and can perform tasks such as summarization and code generation.

---

### Question 5

A company wants to use a large pretrained model as the starting point for multiple AI applications rather than training a separate model from scratch for every task.

What type of model should the company consider?

A. Foundation model  
B. Database index  
C. Regression model only  
D. Rule-based system

**Answer:** A

**Why:** **Foundation models** are large pretrained models that can be adapted for many different tasks.

---

### Question 6

A developer provides the instruction "Summarize the following customer feedback" to a generative AI model.

What is the instruction provided to the model called?

A. Feature  
B. Label  
C. Prompt  
D. Weight

**Answer:** C

**Why:** The input instruction given to a generative AI model is a **prompt**.

---

### Question 7

An organization wants to analyze large amounts of natural-language text and generate human-like responses. The solution uses a neural-network architecture designed for modern language models.

Which architecture is MOST likely being used?

A. Transformer  
B. Linear regression  
C. Decision tree  
D. K-means clustering

**Answer:** A

**Why:** **Transformers** are the dominant architecture underlying modern LLMs and many foundation models.

---

## ⚡ 30-Second Revision

- **Deep learning = ML using multi-layer neural networks.**
    
- Neural networks learn by adjusting **weights** during training.
    
- Deep learning can **automatically learn useful features** from complex data.
    
- Traditional ML is often efficient for **structured/tabular data**.
    
- Deep learning is especially powerful for **images, video, audio, and language**.
    
- **Generative AI → generates new content.**
    
- **Foundation model → large pretrained model adaptable to many tasks.**
    
- **LLM → foundation model focused on language.**
    
- **Transformer → key architecture behind modern LLMs/GenAI.**
    
- **Prompt → input/instruction; inference → model generates the output.**