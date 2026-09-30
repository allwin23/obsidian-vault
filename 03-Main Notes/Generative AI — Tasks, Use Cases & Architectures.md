

## 🎯 Exam Essentials

### 1. Common Generative AI Tasks

Generative AI isn't limited to “creating something from scratch.” It can transform existing information as well.

High-value AIF-C01 use cases include:

- **Text generation**
    
- **Text rewriting/transformation**
    
- **Summarization**
    
- **Translation**
    
- **Question answering**
    
- **Information extraction**
    
- **Classification**
    
- **Code generation/completion**
    
- **Chatbots/conversational agents**
    
- **Content personalization**
    
- **Search and knowledge assistance**
    
- **Recommendation/personalized content**
    
- **Harmful-content detection/moderation**
    

### Important distinction

A GenAI model can perform tasks that look like **classification or extraction**, even though the underlying model is generative.

For example:

> “Read this customer review and output `Positive` or `Negative`.”

The **task** is classification, even if a generative model performs it.

---

# 2. Text Generation & Rewriting

GenAI can generate new text or transform existing text.

Example:

**Input:** Highly technical scuba-diving equipment documentation.

**Task:** Rewrite it for beginners.

The model doesn't necessarily need to be retrained. A sufficiently capable foundation model can often perform this through prompting.

### Exam trigger

> “Adapt technical information for a different audience/tone/style”  
> → **Text generation/rewriting**

---

# 3. Text Summarization

Summarization converts longer information into a shorter representation while attempting to preserve important information.

Possible inputs:

- Technical documents
    
- Financial reports
    
- News articles
    
- Legal documents
    
- Meeting transcripts
    
- Customer feedback
    

### Exam trigger

> “Long document → concise version retaining key points”  
> → **Summarization**

---

# 4. Information Extraction

GenAI can extract specific information from unstructured content.

Example:

Given:

> “Customer John Smith purchased a laptop for $1,200 on September 5.”

Extract:

```text
Customer: John Smith
Product: Laptop
Amount: $1,200
Date: September 5
```

This is useful when information exists in natural language but needs to be converted into structured information.

---

# 5. Question Answering

A model can receive a question and generate an answer.

Examples:

- Customer support questions
    
- Documentation questions
    
- Product questions
    
- Internal knowledge queries
    

⚠️ If the question requires **private, current, or enterprise-specific information**, simply using the model's pretrained knowledge may not be sufficient. Techniques such as **RAG** can provide relevant external context.

---

# 6. Code Generation

GenAI can generate or transform source code from natural-language instructions.

Common applications:

- Code completion
    
- Generate functions
    
- Generate code snippets
    
- Explain code
    
- Refactor code
    
- Translate between programming languages
    
- Generate tests/documentation
    

### AWS example

**Amazon Q Developer** provides AI-powered developer assistance, including code suggestions and generation.

⚠️ The transcript says Q Developer was “formerly Amazon CodeWhisperer.” That historical relationship is not the main AIF-C01 concept to memorize.

**Exam trigger:**

> “Developer wants AI assistance with coding”  
> → **Amazon Q Developer**

---

# 7. Generative AI Architecture Families

Know the broad purpose of these architectures:

### Transformers

Attention-based architecture widely used in modern LLMs and many GenAI systems.

**Strong association:**

> LLM → Transformer

### GANs — Generative Adversarial Networks

Two neural networks compete:

- **Generator** → creates samples
    
- **Discriminator** → tries to distinguish generated samples from real ones
    

The competition helps the generator produce increasingly realistic outputs.

**Mental model:**

> Generator creates → Discriminator critiques → Generator improves

---

### VAEs — Variational Autoencoders

VAEs learn a **latent representation** of data and can generate new samples by sampling from that latent space.

**Mental model:**

> Encode → latent representation → decode/generate

---

### Diffusion Models

Learn to generate data by reversing a gradual noise process.

**Mental model:**

> Noise → iterative denoising → generated output

---

# 🔑 Key Terms

|Term|Meaning|
|---|---|
|**Text generation**|Creating new text from an input/instruction|
|**Text rewriting**|Transforming existing text into a desired style/audience|
|**Summarization**|Producing a shorter representation preserving important information|
|**Information extraction**|Extracting useful structured information from unstructured content|
|**Question answering**|Generating answers to user questions|
|**Code generation**|Producing source code from instructions/examples|
|**Code completion**|Generating likely continuation of existing code|
|**GAN**|Generator + discriminator adversarial architecture|
|**VAE**|Encoder-decoder architecture using latent representations|
|**Transformer**|Attention-based architecture used extensively in modern GenAI|
|**Diffusion model**|Generative model based on iterative denoising|
|**Amazon Bedrock**|Managed service for building GenAI applications with foundation models|
|**Amazon Q Developer**|AWS generative-AI assistant for software development|

---

# ⚔️ Important Comparisons

### GenAI Use Case → Task

|Scenario|Likely task|
|---|---|
|Technical document → beginner-friendly version|Rewriting/transformation|
|50-page report → 5 key points|Summarization|
|Customer email → extract order number|Information extraction|
|“What is AWS Lambda?”|Question answering|
|“Write a Python function that…”|Code generation|
|Existing code → suggested continuation|Code completion|
|English → German|Translation|
|Customer conversation → category|Classification|
|Generate product description|Text generation|
|Generate personalized advertisement|Personalized content generation|

---

### GAN vs VAE vs Transformer vs Diffusion

|Architecture|Core idea|Strong association|
|---|---|---|
|**GAN**|Generator competes with discriminator|Adversarial generation|
|**VAE**|Encoder → latent space → decoder|Latent representation|
|**Transformer**|Attention mechanism|LLMs/language|
|**Diffusion**|Iterative denoising|Image generation|

---

# 🧠 Exam Traps

### Trap 1 — “Generative AI only creates brand-new content”

Too narrow.

GenAI can also:

- Rewrite
    
- Summarize
    
- Translate
    
- Extract
    
- Classify
    
- Transform
    
- Complete
    

---

### Trap 2 — Classification means you must use a traditional classifier

Not necessarily.

A generative model can perform classification through prompting or other techniques.

The **task** and **model architecture** are separate concepts.

---

### Trap 3 — All GenAI = Transformers

No.

GenAI architectures include:

- Transformers
    
- GANs
    
- VAEs
    
- Diffusion models
    
- Other architectures
    

---

### Trap 4 — GANs and VAEs are interchangeable

No.

**GAN:** adversarial generator/discriminator training.

**VAE:** encoder/latent-space/decoder framework.

---

### Trap 5 — Code generation and code completion are identical

They're closely related but not identical.

- **Code generation:** create code from a description/problem.
    
- **Code completion:** generate a likely continuation of existing code.
    

---

### Trap 6 — Amazon Q Developer = general-purpose foundation model

No.

**Amazon Q Developer** is an AWS AI assistant/product for software development tasks.

---

# 📝 Exam Questions

### Q1 — Very Hard

A company has a 120-page technical manual and wants employees to receive a concise response containing the major decisions, risks, and conclusions without reading the entire document.

Which generative AI capability most directly addresses the requirement?

A. Information extraction  
B. Text summarization  
C. Text classification  
D. Code completion

**Answer: B — Text summarization**

**Why:** The objective is to produce a shorter representation while retaining important information from a longer document.

---

### Q2 — Hard

A software engineer writes:

> “Create a Python function that validates whether an email address conforms to our required format.”

The AI system produces a new function based on this natural-language instruction.

Which use case is being demonstrated?

A. Code completion  
B. Code generation  
C. Code classification  
D. Code translation

**Answer: B — Code generation**

**Why:** The developer is asking the model to create new source code from a description.

---

### Q3 — Exam Trap

A developer is typing an existing function and an AI assistant automatically proposes the next several lines based on the surrounding code.

Which use case most directly describes this behavior?

A. Code completion  
B. Information extraction  
C. Text summarization  
D. Model fine-tuning

**Answer: A — Code completion**

**Why:** The system is generating a continuation of existing code rather than creating a program from a high-level specification.

---

### Q4 — Extremely Difficult

An organization wants to automatically identify the invoice number, customer name, purchase date, and total amount from thousands of unstructured invoice descriptions.

Which generative AI capability most directly matches the requirement?

A. Text generation  
B. Information extraction  
C. Text summarization  
D. Personalized content generation

**Answer: B — Information extraction**

**Why:** The objective is to identify specific fields and convert information embedded in unstructured content into structured values.

---

### Q5 — Very Hard

A team is selecting a generative architecture for a system in which one network generates candidate samples while another network attempts to distinguish generated samples from real samples.

Which architecture matches this design?

A. Variational autoencoder  
B. Transformer  
C. Generative adversarial network  
D. Diffusion model

**Answer: C — GAN**

**Why:** The defining characteristic of a GAN is the adversarial relationship between the generator and discriminator.

---

### Q6 — Exam-Trap

A model uses an encoder to map data into a latent representation and a decoder to reconstruct or generate data from that representation.

Which architecture is most consistent with this description?

A. GAN  
B. VAE  
C. Transformer decoder  
D. Diffusion model

**Answer: B — VAE**

**Why:** Encoder → latent representation → decoder is the defining high-level structure of a variational autoencoder.

---

### Q7 — Very Hard

A company wants an AI assistant that can answer questions about its internal documentation, but the information changes frequently and is not necessarily present in the foundation model's training data.

Which consideration is most important?

A. Increase the number of parameters in the foundation model  
B. Provide the model with relevant external context, such as through a retrieval-based architecture  
C. Replace the foundation model with a GAN  
D. Increase the temperature to force the model to access newer information

**Answer: B**

**Why:** Current/private knowledge should be supplied as context, commonly through **RAG**, rather than assuming the pretrained model already knows it.

---

### Q8 — Hard

A marketing team provides a highly technical product specification and asks a generative model to produce an easy-to-understand explanation for customers with no technical background.

Which capability is primarily being used?

A. Text rewriting/transformation  
B. Information retrieval  
C. Code completion  
D. Regression

**Answer: A — Text rewriting/transformation**

**Why:** Existing content is being transformed for a different audience and level of technical complexity.

---

### Q9 — Extremely Difficult

A company is evaluating architectures for different generative applications. Which mapping is most accurate?

A. GAN → adversarial generator/discriminator; VAE → latent representation; Transformer → attention-based sequence modeling; Diffusion → iterative denoising  
B. GAN → iterative denoising; VAE → adversarial training; Transformer → latent-space sampling; Diffusion → discriminator competition  
C. GAN → tokenization; VAE → classification; Transformer → database search; Diffusion → reinforcement learning  
D. GAN → encoder-only architecture; VAE → discriminator-only architecture; Transformer → noise predictor; Diffusion → vocabulary classifier

**Answer: A**

**Why:** Each architecture is matched with its defining high-level mechanism.

---

### Q10 — Exam-Trap

A company wants AWS-managed generative AI assistance specifically for software developers, including code suggestions based on comments and existing source code.

Which AWS offering most directly matches this requirement?

A. Amazon Kendra  
B. Amazon Q Developer  
C. Amazon Rekognition  
D. Amazon Textract

**Answer: B — Amazon Q Developer**

**Why:** Q Developer is designed to assist developers with software-development tasks, including code generation and suggestions.

---

# ⚡ 30-Second Revision

1. **GenAI can generate AND transform content.**
    
2. **Summarization** → long information → concise key information.
    
3. **Rewriting** → adapt content for audience/style/tone.
    
4. **Information extraction** → unstructured content → specific structured information.
    
5. **Question answering** → question → generated answer.
    
6. **Code generation** → description → new code.
    
7. **Code completion** → existing code → likely continuation.
    
8. **GAN** → generator vs discriminator.
    
9. **VAE** → encoder → latent space → decoder.
    
10. **Transformer** → attention; modern LLMs.
    
11. **Diffusion** → iterative denoising.
    
12. **Amazon Q Developer** → developer/code assistance.
    
13. **Architecture choice depends on the objective and data**, not simply “GenAI = Transformer.”