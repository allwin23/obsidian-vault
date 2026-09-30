

## 🎯 Exam Essentials

### 1. Tokenization

Before an LLM processes text, the text is **tokenized**.

**Text → tokens → token IDs → model representations**

A tokenizer converts text into tokens according to the model's vocabulary and maps those tokens to numerical IDs.

Example conceptually:

> `"AWS is great"` → `[token₁, token₂, token₃]` → `[IDs...]`

**Exam trigger:**

> “Converts text into tokens/token IDs/input IDs” → **Tokenizer**

⚠️ **Important correction:** Token IDs themselves are **not embeddings**. A token ID is an identifier/index. The model's embedding layer maps token IDs to dense numerical vectors called **embeddings**.

---

## 2. What Is a Vector?

A **vector** is an ordered collection of numbers.

In ML/GenAI, vectors are used to represent information numerically.

For example:

```text
[0.21, -0.73, 0.14, 0.92, ...]
```

The important idea isn't merely that it's a list of numbers.

A vector can represent a point in a **multidimensional mathematical space**, allowing relationships between represented items to be measured.

---

# 3. Embeddings

An **embedding** is a numerical vector representation that captures meaningful characteristics or semantic relationships of an entity.

Depending on the system, embeddings can represent:

- Words
    
- Tokens
    
- Sentences
    
- Documents
    
- Images
    
- Audio
    
- Other objects
    

### Core idea

Items with similar meanings can have **similar/nearby representations** in embedding space.

For example:

```text
King ───── Queen
 │           │
Man  ───── Woman
```

The exact geometry isn't something you need to memorize, but the key exam concept is:

> **Embeddings represent semantic relationships numerically.**

### Exam trigger

> “Represent semantic meaning as numerical vectors” → **Embeddings**

---

## 4. Token IDs vs Embeddings

This is a **very important distinction**.

|Token ID|Embedding|
|---|---|
|Integer/index|Dense numerical vector|
|Identifies a token|Represents learned information/meaning|
|Produced by tokenizer|Produced by embedding layer/model|
|Example: `15342`|Example: `[0.21, -0.73, ...]`|
|Not semantic by itself|Encodes useful relationships|

### Mental model

**Tokenizer:**

> `"cat"` → `token ID 1234`

**Embedding layer:**

> `1234` → `[0.18, -0.42, 0.71, ...]`

Don't say:

> “The tokenizer converts text directly into an embedding vector.”

The more accurate pipeline is:

**Text → tokenizer → token IDs → embedding layer → embeddings**

---

# 5. Transformer Self-Attention

One of the most important concepts from this lesson is **self-attention**.

Self-attention allows the model to determine which parts of the input are important when processing each token.

It helps capture:

- Context
    
- Relationships between tokens
    
- Long-range dependencies
    
- Word meaning based on surrounding words
    

### Example

Consider:

> “The animal didn't cross the road because **it** was tired.”

To understand what **“it”** refers to, the model needs to consider surrounding context.

Self-attention helps the model determine which other tokens are relevant when representing a particular token.

---

# 6. Query, Key, Value

Self-attention uses three representations:

- **Query (Q)**
    
- **Key (K)**
    
- **Value (V)**
    

At a high level:

1. Generate Q, K and V representations.
    
2. Compare queries with keys to determine relevance.
    
3. Convert those relationships into attention weights.
    
4. Use the weights to combine the value vectors.
    

Conceptually:

**Q + K → attention scores → weights → weighted V → output**

You **do not need to memorize the mathematical implementation** for AIF-C01.

### Exam-level understanding

> **Self-attention determines which tokens should receive more attention when constructing contextual representations.**

---

# 7. Positional Information

Transformers need information about **token order**.

Why?

Consider:

> “Dog bites man.”

versus

> “Man bites dog.”

The same words appear, but their **positions change the meaning**.

Transformers therefore use positional information so the model can distinguish tokens based on their position in a sequence.

The original Transformer paper used **positional encoding**.

⚠️ Modern transformer architectures can use different mechanisms for representing position, so don't assume every modern model uses exactly the original positional encoding method.

---

# 8. Why Transformers Matter

Before transformers, architectures such as **RNNs** were widely used for sequence processing.

Transformers introduced an attention-based architecture that can model relationships between tokens without requiring the sequential recurrence of RNNs.

One major advantage:

> Transformer training can be highly parallelized across sequence positions.

This contributed significantly to the scalability of modern LLMs.

### Exam trigger

> “Attention-based architecture used by modern LLMs” → **Transformer**

---

# 9. Encoder and Decoder

The original Transformer architecture described in **“Attention Is All You Need”** contains:

- **Encoder**
    
- **Decoder**
    

At a conceptual level:

### Encoder

Processes the input sequence and creates contextual representations.

### Decoder

Uses representations/context to generate output sequences.

⚠️ **Exam trap:** Not every modern LLM has both an encoder and decoder.

Common architectural patterns include:

- **Encoder-only** → understanding/representation tasks
    
- **Decoder-only** → autoregressive text generation
    
- **Encoder-decoder** → sequence-to-sequence tasks
    

For modern generative LLMs such as GPT-style models, **decoder-only transformers** are common.

---

# 10. Pre-training vs Inference

### Pre-training

The model learns general patterns from massive datasets.

### Fine-tuning

The model's parameters can be adapted to a more specific task/domain.

### Inference

The trained model is used to generate output for a prompt.

Think:

**Pre-training → broad capabilities**

**Fine-tuning → specialization**

**Inference → use the model**

---

# 🔑 Key Terms

|Term|Exam-level meaning|
|---|---|
|**Tokenizer**|Converts text into tokens/token IDs|
|**Token**|Unit of text processed by an LLM|
|**Token ID / Input ID**|Numerical identifier corresponding to a token|
|**Vector**|Ordered numerical representation|
|**Embedding**|Dense vector representation capturing useful relationships/meaning|
|**Embedding layer**|Maps token IDs into learned vector representations|
|**Vector space**|Mathematical space in which vectors/embeddings can be compared|
|**Semantic similarity**|Similarity in meaning|
|**Self-attention**|Mechanism that determines relevance among tokens|
|**Query**|Attention representation used to seek relevant information|
|**Key**|Attention representation compared with queries|
|**Value**|Information combined according to attention weights|
|**Positional encoding/information**|Represents token position/order|
|**Transformer**|Attention-based neural-network architecture|
|**Encoder**|Produces contextual representations of input|
|**Decoder**|Generates output using contextual information|
|**RNN**|Earlier sequence architecture based on recurrent processing|

---

# ⚔️ Important Comparisons

### Tokenization vs Embedding

||Tokenization|Embedding|
|---|---|---|
|Purpose|Convert text into tokens/IDs|Convert tokens/IDs into dense vectors|
|Output|Token IDs|Numerical vectors|
|Captures semantic meaning?|❌ Not by itself|✅|
|Main component|Tokenizer|Embedding layer/model|

**Mental shortcut:**

> **Tokenizer = “What token is this?”**  
> **Embedding = “How is this token represented mathematically?”**

---

### Token ID vs Embedding

Suppose:

```text
"cat" → 4217 → [0.13, -0.72, 0.44, ...]
```

- `4217` = **token ID**
    
- `[0.13, -0.72, ...]` = **embedding**
    

The number `4217` doesn't inherently mean that “cat” is semantically similar to “dog.” The learned embedding representation carries useful semantic relationships.

---

### Self-Attention vs Positional Information

|Self-attention|Positional information|
|---|---|
|Determines relationships/relevance|Represents order/position|
|“What should I pay attention to?”|“Where does this token occur?”|
|Q/K/V mechanism|Positional encoding/other position mechanisms|

Both contribute to contextual understanding.

---

### Encoder vs Decoder

|Encoder|Decoder|
|---|---|
|Processes input|Generates output|
|Builds contextual representation|Produces sequence|
|Common in encoder-only models|Common in generative decoder-only models|
|Example use: representation/classification|Example use: autoregressive generation|

---

# 🧠 Exam Traps

### Trap 1 — Token IDs are embeddings

❌ Incorrect.

**Token ID → embedding layer → embedding vector**

---

### Trap 2 — Embeddings are just arbitrary numbers

Not quite.

They are numerical representations **learned/constructed to capture useful relationships**, allowing semantic similarity and other relationships to be represented geometrically.

---

### Trap 3 — Self-attention means “the model focuses on the entire sentence equally”

No.

Self-attention computes **different relevance/attention weights** between tokens.

---

### Trap 4 — Transformers process tokens without positional information

Incorrect.

The model needs some mechanism for representing sequence position/order.

---

### Trap 5 — Every Transformer has encoder + decoder

❌ No.

The **original Transformer** had both.

Modern models can be:

- Encoder-only
    
- Decoder-only
    
- Encoder-decoder
    

---

### Trap 6 — RNNs can't model long-range relationships

Too absolute.

RNNs **can** model dependencies across sequences, but standard recurrent architectures can struggle with long-range dependencies and sequential computation. Transformers improved scalability and long-range contextual modeling through attention.

---

### Trap 7 — Embedding = vector database

No.

An **embedding** is a vector representation.

A **vector database** is a system used to store/search vector representations.

---

# 📝 Exam Questions

### Q1 — Very Hard

An application receives the text:

> “Amazon Bedrock helps developers build generative AI applications.”

Before the model processes the text, the system converts portions of the text into numerical identifiers corresponding to entries in the model's vocabulary.

What operation is being described?

A. Embedding generation  
B. Tokenization  
C. Self-attention  
D. Positional encoding

**Answer: B — Tokenization**

**Why:** Tokenization converts text into tokens and corresponding token IDs. The IDs can subsequently be mapped into embeddings.

---

### Q2 — Exam Trap

A developer observes the following conceptual processing sequence:

> Text → tokenizer → integer IDs → dense numerical vectors

Which component is responsible for producing the dense vectors from the token IDs?

A. Tokenizer  
B. Embedding layer  
C. Decoder  
D. Softmax layer

**Answer: B — Embedding layer**

**Why:** The tokenizer produces token IDs. The embedding layer maps those IDs to learned dense vector representations.

---

### Q3 — Extremely Difficult

Two sentences contain the same words but arrange them differently, resulting in different meanings. Which transformer capability is most directly necessary to distinguish the sequences?

A. Tokenization  
B. Positional information  
C. Vocabulary expansion  
D. Increasing the number of output classes

**Answer: B — Positional information**

**Why:** The same tokens can have different meanings when their order changes. Positional information allows the model to represent sequence order.

---

### Q4 — Hard

An LLM processes the token “bank” in two different sentences. In one sentence, nearby tokens indicate a financial institution; in another, they indicate a river bank.

Which transformer mechanism most directly helps the model use the surrounding tokens to construct a context-dependent representation?

A. Self-attention  
B. Tokenization  
C. Positional encoding alone  
D. Model quantization

**Answer: A — Self-attention**

**Why:** Self-attention allows the representation of a token to incorporate information from relevant tokens in its context.

---

### Q5 — Very Hard

A team stores numerical representations of documents so that semantically similar documents can be located near one another in a vector search system.

Which statement best describes what they are storing?

A. Token IDs that uniquely identify every word  
B. Embeddings that numerically represent semantic information  
C. Attention weights that encode the model's learned parameters  
D. Positional encodings that identify document topics

**Answer: B — Embeddings**

**Why:** Embeddings are numerical vector representations that can capture semantic relationships and can be stored in vector databases for similarity search.

---

### Q6 — Exam Trap

Which statement most accurately distinguishes a token ID from an embedding?

A. A token ID is a learned dense representation, while an embedding is an integer vocabulary index  
B. A token ID identifies a vocabulary token, while an embedding is a learned numerical vector representation  
C. Both are identical representations produced directly by the tokenizer  
D. An embedding identifies a token, while a token ID captures semantic similarity

**Answer: B**

**Why:** Token IDs identify tokens. Embeddings are dense numerical representations used by the model to encode useful information.

---

### Q7 — Extremely Difficult

During self-attention, the model computes relationships between representations associated with the current token and other tokens before combining information to produce a contextual representation.

Which sequence best describes the conceptual role of Q, K and V?

A. Query and Key determine relevance; Value supplies information that is weighted and combined  
B. Query supplies vocabulary IDs; Key determines token position; Value generates probabilities  
C. Query performs tokenization; Key generates embeddings; Value determines the context window  
D. Query and Value determine position; Key supplies the final generated token

**Answer: A**

**Why:** Queries and keys determine attention relationships/scores, while values provide the information that is combined according to those weights.

---

### Q8 — Hard

An engineer says:

> “The original Transformer architecture demonstrates that every modern LLM must contain both an encoder and decoder.”

Which correction is most accurate?

A. Transformers cannot contain decoders because generation is performed outside the architecture  
B. The original Transformer used encoder and decoder components, but modern transformer models can use different configurations  
C. All modern LLMs are encoder-only because decoding is handled by tokenizers  
D. Encoder-decoder architecture was introduced only after GPT models

**Answer: B**

**Why:** The original Transformer was encoder-decoder, but modern models may be encoder-only, decoder-only, or encoder-decoder.

---

### Q9 — Very Hard

A team wants to understand why transformers can capture relationships between tokens that are far apart in a sequence without relying on the recurrent step-by-step processing characteristic of RNNs.

Which capability is most directly relevant?

A. Self-attention  
B. Token ID assignment  
C. Vocabulary lookup  
D. Output softmax

**Answer: A — Self-attention**

**Why:** Self-attention allows tokens to directly incorporate information from other positions, supporting long-range relationships and highly parallelizable computation during training.

---

### Q10 — Exam-Trap

A developer says:

> “Because two embeddings are close together in vector space, the first token ID must be numerically close to the second token ID.”

Which response is most accurate?

A. Correct, because token IDs preserve semantic distance  
B. Correct, because token IDs are generated from embedding coordinates  
C. Incorrect, because token IDs are identifiers while semantic relationships are represented in embedding space  
D. Incorrect, because embeddings cannot represent semantic relationships

**Answer: C**

**Why:** Token IDs are vocabulary identifiers. Their numerical values don't inherently encode semantic similarity. The **embedding vectors** capture useful semantic relationships.

---

# ⚡ 30-Second Revision

Memorize this pipeline:

**Text → Tokenizer → Token IDs → Embedding Layer → Embeddings → Self-Attention → Transformer → Output**

Then remember:

1. **Tokenizer** → text → tokens/token IDs.
    
2. **Token ID** → vocabulary identifier.
    
3. **Embedding** → dense numerical representation.
    
4. **Embedding space** → relationships/similarity can be represented geometrically.
    
5. **Self-attention** → determines which tokens are relevant to each other.
    
6. **Q/K** → determine attention relationships.
    
7. **V** → information being weighted/combined.
    
8. **Positional information** → tells the model about token order.
    
9. **Transformer** → attention-based architecture central to modern GenAI.
    
10. **Original Transformer** → encoder + decoder.
    
11. **Modern LLMs** → may be encoder-only, decoder-only, or encoder-decoder.
    
12. **Vector ≠ embedding ≠ token ID ≠ vector database.**
    
13. **Embedding** = representation; **vector database** = storage/search system for vectors.