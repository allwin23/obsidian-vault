# Generative AI — Basic Concepts

## 🎯 Exam Essentials

### 1. What is Generative AI?

**Generative AI (GenAI)** is AI that can **generate new content** based on patterns learned from training data.

It can generate:

- Text
    
- Images
    
- Audio
    
- Video
    
- Code
    

### Critical distinction

|Traditional AI/ML|Generative AI|
|---|---|
|Predicts, classifies, detects|Generates new content|
|“Is this spam?”|“Write an email.”|
|“What is the house price?”|“Generate a house description.”|
|“Is this image a cat?”|“Create an image of a cat.”|

**Exam trigger:**

> “Create, generate, compose, synthesize, produce new content” → **Generative AI**

⚠️ **Accuracy note:** GenAI is commonly built using deep learning, but saying it is _strictly_ a subset of deep learning is an oversimplification. For AIF-C01, understand the relationship as **modern GenAI is predominantly powered by deep-learning models**.

---

## 2. Foundation Models

A **foundation model (FM)** is a large pretrained model that can be adapted to perform many different tasks.

Typical characteristics:

- Trained on very large datasets
    
- Large numbers of learned parameters
    
- General-purpose capabilities
    
- Can often be adapted using prompting, fine-tuning, or other customization techniques
    

### Important distinction

**Foundation model ≠ LLM**

An LLM is a type of foundation model specialized primarily for language.

Foundation models can operate across modalities such as:

- Text
    
- Images
    
- Audio
    
- Video
    

---

## 3. Parameters

**Parameters are values learned by the model during training.**

Examples include neural-network weights.

Do not confuse:

- **Parameters** → learned by the model
    
- **Hyperparameters** → configured/tuned by practitioners
    

⚠️ **Exam trap:** More parameters generally means a larger model, but **more parameters does not automatically mean better performance**.

The transcript's statement that more parameters directly give a model “more memory” is imprecise. A larger parameter count generally means **more model capacity and greater memory/compute requirements**.

---

## 4. LLMs and Transformers

Modern LLMs commonly use the **Transformer architecture**.

Transformers rely heavily on **attention mechanisms** to model relationships between tokens.

The influential 2017 paper:

> **“Attention Is All You Need”**

introduced the Transformer architecture.

### Why transformers matter

They enabled highly capable models that can process relationships between elements of a sequence efficiently, particularly during training.

**Exam trigger:**

> “Attention mechanism + modern LLM architecture” → **Transformer**

---

## 5. Tokens

LLMs generally don't process raw sentences as individual “words.”

Text is converted into **tokens**.

A token can represent:

- A complete word
    
- Part of a word
    
- Punctuation
    
- Other pieces of text
    

Example conceptually:

`unbelievable`

might be represented as multiple tokens rather than one token.

The model operates on numerical representations of these tokens.

---

## 6. Prompt → Inference → Completion

This is one of the most important chains to remember:

**Prompt → Inference → Completion**

### Prompt

The **input/instruction** provided to the generative model.

Example:

> “Summarize this article in three bullet points.”

### Inference

The process of using the trained model to generate an output for a given input.

### Completion

The model's **generated output** in response to the prompt.

For an LLM, generation is fundamentally based on predicting likely next tokens given the context.

---

# 7. Context Window

The **context window** is the amount of information the model can consider as context during an interaction.

It can contain things such as:

- User instructions
    
- Previous conversation
    
- Examples
    
- Documents/text supplied to the model
    
- Other input tokens
    

### Exam trigger

> “Maximum amount of input/context the model can process at once” → **Context window**

Don't confuse:

**Context window** → information available to the model during inference.

**Training data** → data used to train the model.

---

# 8. Prompt Engineering

**Prompt engineering** is the practice of designing and refining prompts to obtain more useful/reliable model outputs.

It can involve:

- Clear instructions
    
- Constraints
    
- Desired output format
    
- Relevant context
    
- Examples
    
- Role/task specification
    

The goal is to make the intended task clearer to the model.

---

# 9. In-Context Learning

**In-context learning** means providing examples or additional information **inside the prompt/context** so the model can perform the requested task.

Crucially:

> **The model is not retrained.**

You are giving the model information/examples at inference time.

### Example

Instead of:

> Classify this review: “Amazing product!”

You provide examples:

> “Terrible product” → Negative  
> “Excellent product” → Positive  
> “Amazing product!” → ?

The examples help establish the desired pattern.

---

# 10. Zero-Shot, One-Shot & Few-Shot

These describe how many examples are provided in the prompt.

|Technique|Examples provided|
|---|--:|
|**Zero-shot**|0|
|**One-shot**|1|
|**Few-shot**|A small number|

### Zero-shot

Give the task without examples.

> “Classify this review as positive or negative.”

### One-shot

Provide **one example**.

> “Great product!” → Positive  
> “This product is okay.” → ?

### Few-shot

Provide **multiple examples**.

**Key distinction:** These are prompting/in-context techniques, **not model retraining**.

---

# 🔑 Key Terms

|Term|Exam-level meaning|
|---|---|
|**Generative AI**|AI that generates new content|
|**Foundation model**|Large pretrained general-purpose model adaptable to many tasks|
|**LLM**|Foundation model primarily designed for language|
|**Transformer**|Neural-network architecture using attention, widely used in modern GenAI|
|**Parameter**|Learned model value/weight|
|**Token**|Unit of text processed by an LLM|
|**Prompt**|Input/instruction supplied to a model|
|**Inference**|Using a trained model to produce an output|
|**Completion**|Generated response/output|
|**Context window**|Amount of context the model can consider|
|**Prompt engineering**|Designing prompts to improve desired outputs|
|**In-context learning**|Supplying examples/information within the prompt|
|**Zero-shot**|No examples|
|**One-shot**|One example|
|**Few-shot**|Multiple examples|

---

# ⚔️ Important Comparisons

### Prompting vs Fine-Tuning vs Pre-training

||Prompting / In-context|Fine-tuning|Pre-training|
|---|---|---|---|
|Main purpose|Guide model at inference|Adapt model to a task/domain|Build broad model capabilities|
|Changes model weights?|❌ No|✅ Yes|✅ Yes|
|Examples supplied in prompt?|Often|Not the defining characteristic|No|
|Typical data requirement|Low|Less than pre-training|Extremely large|
|When occurs|Inference|Customization/training|Initial model training|

**Very important:**  
**In-context learning ≠ fine-tuning.**

---

### Zero-shot vs One-shot vs Few-shot

||Examples in prompt|
|---|--:|
|Zero-shot|0|
|One-shot|1|
|Few-shot|Several|

---

### Parameters vs Tokens

|Parameter|Token|
|---|---|
|Learned model value|Unit of input/output text|
|Exists inside model|Represents input/output content|
|Learned during training|Created during tokenization|
|Example: neural-network weight|Example: word/subword/punctuation|

---

# 🧠 Exam Traps

### Trap 1 — “The model learned from my examples”

If examples are merely placed inside the prompt:

→ **In-context learning**

Not fine-tuning.

---

### Trap 2 — “LLM = Foundation Model”

Incorrect.

**LLM is a type of foundation model.**

A foundation model can also specialize in other modalities.

---

### Trap 3 — “Prompt = output”

No.

**Prompt = input**  
**Completion = output**

---

### Trap 4 — “Inference = training”

No.

**Training** → learns parameters.  
**Inference** → uses the trained model to generate predictions/content.

---

### Trap 5 — “More parameters always means better”

Not necessarily.

More parameters generally increase model capacity, but performance depends on many factors including:

- Training data
    
- Training quality
    
- Architecture
    
- Model design
    
- Task
    
- Evaluation methodology
    

---

### Trap 6 — Context window vs model knowledge

A context window determines what information the model can process **in the current inference context**.

It isn't the same thing as the model's entire learned knowledge.

---

# 📝 Exam Questions

Questions are deliberately shuffled and use closely related distractors.

### Q1 — Very Hard

A developer provides a foundation model with four labeled examples inside the prompt before asking it to classify a fifth item. No model training or weight updates occur.

Which technique is being used?

A. Parameter-efficient fine-tuning  
B. Few-shot in-context learning  
C. Continued pre-training  
D. Transfer learning

**Answer: B — Few-shot in-context learning**

**Why:** Multiple examples are supplied within the prompt at inference time. The model's parameters aren't updated.

---

### Q2 — Hard

An organization wants a model that can perform summarization, question answering, and text generation using a single pretrained model rather than developing a separate model from scratch for every task.

Which type of model best matches this requirement?

A. Foundation model  
B. Classification model  
C. Regression model  
D. Feature-extraction model

**Answer: A — Foundation model**

**Why:** Foundation models are pretrained broadly and can be adapted to multiple downstream tasks.

---

### Q3 — Exam Trap

A model receives a probability distribution over possible next tokens and generates a response one token at a time based on the available context.

Which process is occurring?

A. Pre-training  
B. Fine-tuning  
C. Inference  
D. Tokenization

**Answer: C — Inference**

**Why:** The already-trained model is being used to generate an output from an input/context.

---

### Q4 — Extremely Difficult

A team wants to provide 12 examples of desired input/output behavior to an LLM for a particular request. The examples should influence the response, but the underlying model must remain unchanged.

Which approach most directly satisfies the requirement?

A. Few-shot prompting  
B. Fine-tuning  
C. Continued pre-training  
D. Parameter optimization

**Answer: A — Few-shot prompting**

**Why:** Examples placed in the prompt influence the model at inference time without modifying model parameters.

---

### Q5 — Hard

An engineer notices that an LLM can process only a bounded amount of conversation history and supplied documents during a single interaction. They want to identify the model characteristic responsible for this limitation.

Which concept is most directly relevant?

A. Vocabulary size  
B. Context window  
C. Parameter count  
D. Completion length

**Answer: B — Context window**

**Why:** The context window defines how much contextual information can be considered during an inference request.

---

### Q6 — Very Hard

A team compares two GenAI models. Model A contains substantially more learned parameters than Model B. The team concludes that Model A must therefore produce better results for every task.

Which statement most accurately challenges this conclusion?

A. Parameter count has no relationship to model capacity  
B. Larger models cannot perform inference efficiently  
C. Parameter count alone does not guarantee better task performance  
D. Models with more parameters cannot be fine-tuned

**Answer: C**

**Why:** Parameter count is one characteristic of a model, but data quality, architecture, training, task alignment, and other factors also affect performance.

---

### Q7 — Exam Trap

A customer sends an instruction and supporting text to an LLM. The model then generates a response based on that input.

Which mapping is correct?

A. Instruction/supporting text = completion; generated response = prompt  
B. Instruction/supporting text = prompt; generated response = completion  
C. Instruction/supporting text = inference; generated response = tokenization  
D. Instruction/supporting text = fine-tuning; generated response = parameter

**Answer: B**

**Why:** The prompt is the model input; the generated result is the completion.

---

### Q8 — Extremely Difficult

A company wants to adapt a pretrained language model to consistently follow a specialized task pattern. It is willing to use a dedicated training process that modifies model parameters using task-specific data.

Which approach is most consistent with this requirement?

A. Few-shot in-context learning  
B. Zero-shot prompting  
C. Fine-tuning  
D. Context-window expansion

**Answer: C — Fine-tuning**

**Why:** The decisive clue is **modifying/adapting model parameters using task-specific training data**. Prompting does not modify the model's weights.

---

### Q9 — Hard

Which statement best distinguishes a token from a model parameter?

A. A token is learned during training, while a parameter is supplied by the user  
B. A token represents a unit of input/output content, while a parameter is a learned value within the model  
C. A token controls model behavior, while a parameter determines vocabulary boundaries  
D. A token is part of the model architecture, while a parameter exists only during inference

**Answer: B**

**Why:** Tokens represent pieces of input/output text; parameters are learned numerical values that determine model behavior.

---

### Q10 — Exam-Trap

An LLM receives no examples and only the instruction:

> “Classify this customer review as positive, negative, or neutral.”

Which approach is being used?

A. One-shot inference  
B. Few-shot inference  
C. Zero-shot inference  
D. In-context fine-tuning

**Answer: C — Zero-shot inference**

**Why:** The task is specified, but **no examples** are included.

---

# ⚡ 30-Second Revision

Remember this chain:

**GenAI → Foundation Models → LLMs → Transformers → Tokens → Prompts → Inference → Completions**

And these distinctions:

1. **GenAI** → generates new content.
    
2. **Foundation model** → broadly pretrained and adaptable.
    
3. **LLM** → language-focused foundation model.
    
4. **Transformer** → major architecture behind modern LLMs.
    
5. **Parameter** → learned model value.
    
6. **Token** → unit of text processed by the model.
    
7. **Prompt** → input.
    
8. **Completion** → generated output.
    
9. **Inference** → using the trained model.
    
10. **Context window** → amount of context available during inference.
    
11. **Zero-shot = 0 examples.**
    
12. **One-shot = 1 example.**
    
13. **Few-shot = several examples.**
    
14. **In-context learning = examples in prompt, no weight updates.**
    
15. **Fine-tuning = training that adapts model parameters.**