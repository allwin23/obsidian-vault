

## 🎯 Exam Essentials

### 1. Model Scaling

Larger models generally have greater **model capacity** and can learn more complex patterns.

As models scale, three major factors become important:

- **Model size** → more parameters/capacity
    
- **Training data** → more information/patterns available
    
- **Compute** → more resources required for training
    

But:

> **More parameters ≠ automatically better model.**

Larger models can require dramatically more:

- Training compute
    
- Memory
    
- Time
    
- Data
    
- Infrastructure
    
- Cost
    

### Exam trigger

> “Increasing parameters requires substantially more compute and resources” → **model scaling tradeoff**

---

# 2. Pre-training

**Pre-training** is the initial large-scale training stage where a model learns general patterns from enormous datasets.

For LLMs, training data can include:

- Books
    
- Websites
    
- Articles
    
- Other text collections
    

During pre-training:

**Training data → model → prediction → loss → parameter updates**

The model's **weights/parameters are updated** to reduce the training objective/loss.

### Key distinction

**Pre-training** gives the model broad capabilities.

**Fine-tuning** adapts an already-trained model for a more specific task/domain.

---

# 3. Self-Supervised Learning

Large language models can be pretrained using **self-supervised learning**.

The training data itself provides the learning signal.

For example, the model may be trained to predict a missing/next token based on surrounding context.

No human needs to manually label every training example.

### Exam trigger

> “Labels are generated from the data itself / predict the next token” → **self-supervised learning**

---

# 4. Training Data Curation

Raw internet-scale data isn't automatically suitable for model training.

Data may need processing to:

- Remove low-quality content
    
- Remove harmful content
    
- Address duplicates
    
- Reduce unwanted bias
    
- Filter inappropriate material
    
- Improve overall data quality
    

This is an important part of building training datasets.

⚠️ **Accuracy note:** The transcript's “1%–3% of tokens are used after curation” is not a general AIF-C01 fact you should memorize. The usable fraction depends heavily on the dataset, filtering methodology, objectives, and deduplication process.

---

# 5. Unimodal vs Multimodal

### Unimodal

A model primarily works with **one modality**.

Examples:

- Text → text
    
- Image → image
    

A traditional text-only LLM is an example of a unimodal model.

### Multimodal

A model can process and/or generate **multiple modalities**.

Examples:

- Text → image
    
- Image → text
    
- Text + image → text
    
- Audio → text
    
- Text → audio
    

Possible modalities:

- Text
    
- Images
    
- Audio
    
- Video
    

### Exam trigger

> “Model works across text, image, audio, video” → **multimodal**

---

# 6. Important Multimodal Tasks

Know these patterns:

|Task|Input → Output|
|---|---|
|**Image captioning**|Image → Text|
|**Visual question answering**|Image + Question → Answer|
|**Text-to-image**|Text → Image|
|**Image generation**|Prompt → Image|
|**Speech recognition**|Audio → Text|
|**Image understanding**|Image → information/text|

The important exam concept is **cross-modal transformation**.

---

# 7. Diffusion Models

A **diffusion model** is a generative model that learns to generate data by reversing a gradual **noising process**.

The fundamental idea:

**Clean data → add noise → noisy data**

Then during generation:

**Noise → iterative denoising → generated data**

---

## 8. Forward Diffusion

During the forward process, noise is progressively added to the original data.

Conceptually:

```text
Original image
     ↓
slightly noisy
     ↓
more noisy
     ↓
mostly noise
```

The model learns the relationship between noisy and clean data during training.

---

## 9. Reverse Diffusion

Generation starts from noise and progressively removes it.

```text
Random noise
     ↓
less noisy
     ↓
more structured
     ↓
coherent image
```

The model predicts what noise should be removed at each step.

### Mental shortcut

> **Forward = add noise**  
> **Reverse = remove noise**

This is one of the most important things to remember from this lesson.

---

# 10. Stable Diffusion

**Stable Diffusion** is a diffusion-based image-generation model that operates in a **latent space** rather than directly performing the entire diffusion process in raw pixel space.

This makes generation more computationally efficient than performing diffusion directly over high-dimensional pixel representations.

### Exam trigger

> “Diffusion + latent space + text-to-image generation” → **Stable Diffusion**

AWS services such as **Amazon SageMaker AI / SageMaker JumpStart** can provide access to pretrained models such as Stable Diffusion.

---

# 11. Diffusion vs GANs vs VAEs

You don't need deep mathematical details for AIF-C01.

At a high level:

|Approach|Core idea|
|---|---|
|**Diffusion**|Learn to reverse a noise process|
|**GAN**|Generator competes with discriminator|
|**VAE**|Encode data into latent representation and decode/reconstruct/generate|

Diffusion models are widely used for high-quality generative applications, especially image generation.

⚠️ Don't memorize the transcript's claim that diffusion models are _always_ superior to GANs/VAEs. Performance depends on the task, model, data, and evaluation criteria.

---

# 🔑 Key Terms

|Term|Exam-level meaning|
|---|---|
|**Model scaling**|Increasing model capacity, often through more parameters|
|**Pre-training**|Large-scale initial training to learn general capabilities|
|**Self-supervised learning**|Training where the data provides its own learning signal|
|**Training objective**|Task the model is optimized to perform|
|**Loss**|Measure of error used during training|
|**Parameter/weight**|Learned model value updated during training|
|**Unimodal**|Primarily works with one data modality|
|**Multimodal**|Works across multiple modalities|
|**Modality**|Type of data, such as text, image, audio, video|
|**Diffusion model**|Generative model based on reversing a noise process|
|**Forward diffusion**|Progressively adds noise|
|**Reverse diffusion**|Progressively removes noise|
|**Latent space**|Lower-dimensional learned representation space|
|**Stable Diffusion**|Latent diffusion-based generative model|
|**Image captioning**|Image → text|
|**Visual QA**|Image + question → answer|
|**Text-to-image**|Text prompt → image|

---

# ⚔️ Important Comparisons

### Pre-training vs Fine-tuning vs Inference

||Pre-training|Fine-tuning|Inference|
|---|---|---|---|
|Purpose|Learn broad capabilities|Adapt to specific task/domain|Generate output|
|Parameters updated?|✅|✅|❌|
|Typical data size|Very large|Smaller task-specific dataset|Input/request|
|Main activity|Learn general patterns|Specialize|Use trained model|

---

### Unimodal vs Multimodal

|Unimodal|Multimodal|
|---|---|
|One modality|Multiple modalities|
|Text-only LLM|Text + image model|
|Image-only model|Image + text reasoning|
|Simpler modality scope|Cross-modal capabilities|

---

### Forward vs Reverse Diffusion

|Forward|Reverse|
|---|---|
|Add noise|Remove noise|
|Clean → noisy|Noise → structured output|
|Used to define/train diffusion process|Used for generation|
|Corrupts data progressively|Denoises progressively|

**Shortcut:**  
**Forward = destroy structure**  
**Reverse = create structure**

---

### Diffusion vs GAN vs VAE

||Diffusion|GAN|VAE|
|---|---|---|---|
|Core mechanism|Iterative denoising|Generator + discriminator|Encoder + decoder|
|Key concept|Noise/reverse diffusion|Adversarial competition|Latent representation|
|Common use|Image generation|Image/data generation|Generation + representation|

---

# 🧠 Exam Traps

### Trap 1 — More parameters always means better

❌ No.

More parameters can increase capacity, but performance also depends on:

- Data
    
- Architecture
    
- Training quality
    
- Compute
    
- Task
    
- Evaluation
    

---

### Trap 2 — Self-supervised = unsupervised

They're related but shouldn't be treated as identical.

**Self-supervised learning creates a learning signal from the data itself.**

Example:

> Predict the next token.

---

### Trap 3 — Multimodal means “multiple outputs”

Not necessarily.

Multimodal refers to **multiple types/modalities of data**, such as text, image, audio, and video.

---

### Trap 4 — Forward diffusion generates the image

❌ No.

**Forward diffusion adds noise.**

**Reverse diffusion generates/recovers structured output by denoising.**

---

### Trap 5 — Stable Diffusion operates directly on raw pixels throughout

❌ Not the key idea.

Stable Diffusion uses a **latent-space diffusion approach**.

---

### Trap 6 — Whisper is a diffusion model

⚠️ **Transcript correction:** Whisper is a speech-recognition model, not a diffusion model. It uses an encoder-decoder Transformer architecture.

Similarly, **AudioLM is a generative audio language-model approach**, not something you should classify as a diffusion model simply because it generates audio.

For the exam, keep:

> **Stable Diffusion → diffusion-based image generation**

---

### Trap 7 — Every multimodal model generates every modality

Not necessarily.

A model can be multimodal because it **accepts multiple modalities**, **generates multiple modalities**, or supports particular combinations of input/output modalities.

Always examine the specific input/output capability described in the question.

---

# 📝 Exam Questions

### Q1 — Very Hard

An organization is deciding whether to increase the parameter count of its foundation model. The engineering team expects this change to improve capacity but recognizes that training will require substantially more computational resources.

Which statement best describes the tradeoff?

A. Increasing parameters necessarily improves every task while reducing training cost per example  
B. Increasing parameters can increase model capacity, but may substantially increase compute, memory, data, and training costs  
C. Increasing parameters primarily affects the tokenizer vocabulary rather than model capacity  
D. Increasing parameters eliminates the need for additional training data because the model can infer missing information

**Answer: B**

**Why:** Larger models can provide greater capacity, but scaling creates substantial compute, memory, data, and cost requirements. More parameters don't guarantee universally better results.

---

### Q2 — Exam Trap

A language model is trained on enormous quantities of text. For each training example, the learning signal can be derived from the text itself by asking the model to predict the next token.

What type of learning is this?

A. Reinforcement learning  
B. Unsupervised clustering  
C. Self-supervised learning  
D. Few-shot learning

**Answer: C — Self-supervised learning**

**Why:** The training signal is derived from the data itself rather than requiring manually assigned labels.

---

### Q3 — Extremely Difficult

A company wants to build an application that accepts a photograph and a natural-language question such as “What objects are visible in this image?” and returns a text response.

Which characteristic is most directly demonstrated?

A. Unimodal text generation  
B. Multimodal processing  
C. Diffusion-based generation  
D. Self-supervised tokenization

**Answer: B — Multimodal processing**

**Why:** The application combines an image modality with text and produces a textual answer.

---

### Q4 — Hard

A diffusion model begins its generation process from random noise and repeatedly transforms the representation toward a coherent image.

Which process is primarily being described?

A. Forward diffusion  
B. Reverse diffusion  
C. Tokenization  
D. Adversarial discrimination

**Answer: B — Reverse diffusion**

**Why:** Generation proceeds from noisy representation toward structured output through iterative denoising.

---

### Q5 — Very Hard

An engineer describes a diffusion system as follows:

> “During one process, progressively more Gaussian noise is applied to an image. During generation, the learned model performs the opposite process to recover a coherent sample.”

Which mapping is correct?

A. Forward diffusion adds noise; reverse diffusion removes noise  
B. Forward diffusion removes noise; reverse diffusion adds noise  
C. Forward diffusion performs tokenization; reverse diffusion performs embedding  
D. Forward diffusion generates the final image; reverse diffusion creates the training dataset

**Answer: A**

**Why:** This is the fundamental conceptual distinction between the two diffusion directions.

---

### Q6 — Exam Trap

A team is choosing between a conventional pixel-space diffusion implementation and Stable Diffusion for an image-generation application. The team specifically wants to understand what distinguishes Stable Diffusion.

Which characteristic is most relevant?

A. It eliminates the need for a denoising process  
B. It performs the diffusion process in a learned latent representation rather than directly throughout raw pixel space  
C. It replaces diffusion with adversarial generator-discriminator training  
D. It generates images without requiring a text or other conditioning signal

**Answer: B**

**Why:** Stable Diffusion uses **latent diffusion**, operating in a reduced latent representation rather than performing the entire process directly in pixel space.

---

### Q7 — Extremely Difficult

A model has been pretrained on a very large general-purpose dataset. A company subsequently trains it using a smaller dataset containing examples from its specialized domain to adapt the model's behavior.

Which lifecycle stage is most directly described by the second training phase?

A. Inference  
B. Tokenization  
C. Fine-tuning  
D. Forward diffusion

**Answer: C — Fine-tuning**

**Why:** The model already has broad pretrained capabilities and is now being adapted using domain-specific training data.

---

### Q8 — Hard

Which scenario is **most clearly multimodal**?

A. An LLM summarizes a 10,000-word text document  
B. A text model translates English text into French text  
C. A model receives an image and a question about that image and generates a textual answer  
D. A classifier predicts whether a text review is positive or negative

**Answer: C**

**Why:** The system combines image and text modalities. The other examples are text-only.

---

### Q9 — Very Hard

A team argues that because its foundation model has twice as many parameters as another model, it must necessarily have superior performance on every downstream task.

Which response is most accurate?

A. Correct, because parameter count is the sole determinant of model quality  
B. Correct, provided both models use the same tokenizer  
C. Incorrect, because parameter count can affect capacity but performance also depends on data, architecture, training, and task alignment  
D. Incorrect, because parameter count has no effect on a model's capability

**Answer: C**

**Why:** Parameter count matters, but it isn't the sole determinant of model quality.

---

### Q10 — Exam-Trap

A course describes Stable Diffusion, Whisper, and AudioLM together as examples of diffusion models. Which correction should an exam candidate make when evaluating that statement?

A. All three are diffusion models because all three can generate or process non-text data  
B. Stable Diffusion is diffusion-based, while Whisper is primarily a speech-recognition Transformer and AudioLM is an audio language-model approach  
C. Whisper is a diffusion model, but Stable Diffusion is a GAN  
D. AudioLM is a diffusion model because all audio generation requires diffusion

**Answer: B**

**Why:** The commonality is that these systems involve generative/multimodal applications, not that they all use diffusion architectures. **Stable Diffusion** is the diffusion-specific example here.

---

# ⚡ 30-Second Revision

1. **Scaling** → more parameters can increase capacity but increases compute/memory/cost.
    
2. **Pre-training** → learn broad capabilities from massive datasets.
    
3. **Self-supervised learning** → learning signal comes from the data itself.
    
4. **Fine-tuning** → adapt a pretrained model to a specific task/domain.
    
5. **Unimodal** → one modality.
    
6. **Multimodal** → multiple modalities such as text + image + audio.
    
7. **Image captioning** → image → text.
    
8. **Visual QA** → image + question → answer.
    
9. **Text-to-image** → text → image.
    
10. **Forward diffusion** → progressively **add noise**.
    
11. **Reverse diffusion** → progressively **remove noise** to generate structured output.
    
12. **Stable Diffusion** → latent-space diffusion, commonly used for image generation.
    
13. **Diffusion ≠ GAN ≠ VAE.**
    
14. **Whisper is not a diffusion model.**
    
15. **More parameters ≠ automatically better performance.**