# Task Statement 3.2 — Choose Effective Prompt Engineering Techniques

## 🎯 Exam Essentials

### **1. Latent Space and Prompting**

- **Concept:** A language model is trained on large text datasets that contain knowledge and patterns across many topics.
    
- **Examples mentioned:** RefinedWeb, Common Crawl, StarCoder data, BookCorpus, Wikipedia, and C4.
    
- **Key idea:** When a prompt is provided, the model uses patterns and knowledge encoded in its **latent space** to generate a response.
    
- **Exam trigger:** **Prompt → model accesses learned patterns/knowledge → generated response.**
    

---

### **2. Latent Space Has Limitations**

- **Concept:** The amount and quality of information represented in a model's latent space can vary.
    
- **Important point:** A smaller model may have insufficient information about a particular topic.
    
- **Consequence:** If the model lacks sufficient knowledge about the requested topic, it may produce a response based on the **closest statistical match**.
    
- **Exam trigger:** **Insufficient latent-space knowledge → increased hallucination risk.**
    

---

### **3. Hallucination and Latent-Space Limitations**

- **Concept:** The transcript explains that hallucinations can occur when a model does not have enough information about the requested topic.
    
- **Mechanism described:** The model may choose a statistically likely continuation even when it is **factually incorrect**.
    
- **Key distinction:** A response can be statistically plausible while being factually wrong.
    
- **Exam trigger:** If a model confidently produces an incorrect answer about an obscure topic, consider **limitations of its learned knowledge/latent space**.
    

---

### **4. Conditional Probability and Token Generation**

- **Concept:** The transcript explains that LLMs generate a sentence **one word at a time**, selecting from possible words based on conditional probability given surrounding context.
    
- **Key implication:** The model's output is generated statistically rather than through human-like reasoning.
    
- **Exam trigger:** If the question asks why an LLM can produce a fluent but incorrect answer, consider **probabilistic language generation**.
    

---

### **5. Assess the Model Before Prompt Construction**

- **Concept:** Effective prompt engineering requires understanding what the model knows well and where its limitations are.
    
- **Key consideration:** Assess the model's latent-space knowledge for the relevant topic before constructing prompts.
    
- **Why:** Prompting a model about topics it does not know well can increase the likelihood of hallucinations.
    
- **Exam trigger:** **Know the model's strengths/weaknesses before designing prompts.**
    

---

### **6. Specific and Clear Instructions**

- **Concept:** Prompt engineering should provide clear, specific instructions or specifications.
    
- **Useful details can include:**
    
    - Desired format
        
    - Examples
        
    - Comparisons
        
    - Style
        
    - Tone
        
    - Output length
        
    - Detailed context
        
- **Exam trigger:** If an LLM produces vague or inconsistent output, consider making the prompt **more specific and structured**.
    

---

### **7. Provide Examples**

- **Concept:** Examples can demonstrate the desired behavior or direction to the model.
    
- **Examples mentioned:** Sample texts, data formats, templates, code, graphs, and charts.
    
- **Purpose:** Help communicate what the expected output should look like.
    
- **Exam trigger:** **Show the desired behavior/output → provide examples.**
    

---

### **8. Iterative Prompt Experimentation**

- **Concept:** Prompt engineering is an iterative process.
    
- **Method:** Test prompts and observe how modifications change model responses.
    
- **Purpose:** Identify prompt structures that produce better results for the particular use case.
    
- **Exam trigger:** If a scenario asks how to improve a prompt systematically, consider **experimenting, modifying, and evaluating repeatedly**.
    

---

### **9. Know Model Strengths and Weaknesses**

- **Concept:** Prompt engineers should understand the capabilities and limitations of the model being used.
    
- **Why:** Prompting cannot fully compensate for knowledge or capability limitations in the underlying model.
    
- **Exam trigger:** If the model repeatedly fails on a specific topic or task, consider whether the issue is a **model limitation**, not merely poor prompt wording.
    

---

### **10. Balance Prompt Simplicity and Complexity**

- **Concept:** Prompts should contain enough information to guide the model without becoming unnecessarily complicated.
    
- **Risk of insufficient detail:** Vague or unrelated answers.
    
- **Risk of excessive/unhelpful complexity:** Unexpected or undesirable answers.
    
- **Exam trigger:** Aim for the appropriate level of **clarity and relevant detail** rather than simply making prompts longer.
    

---

### **11. Add Context Without Clutter**

- **Concept:** The transcript recommends using multiple comments to provide additional context without cluttering the main prompt.
    
- **Purpose:** Provide useful contextual information while maintaining a manageable prompt structure.
    
- **Exam trigger:** If additional context is needed but the main prompt is becoming cluttered, consider separating contextual information appropriately.
    

---

### **12. Guardrails**

- **Concept:** Guardrails provide **safety and privacy controls** for generative AI applications.
    
- **Capabilities mentioned:**
    
    - Define undesirable topics
        
    - Block specific words
        
    - Configure filtering thresholds
        
    - Filter harmful categories
        
    - Address jailbreak and prompt-injection attacks
        
    - Filter inputs containing sensitive data
        
- **Exam trigger:** **Safety/privacy controls around model interaction → Guardrails.**
    

---

### **13. Prompt Injection**

- **Concept:** Prompt injection is an attack involving **prompt manipulation**.
    
- **Scenario described:** A trusted developer-created prompt is combined with untrusted user input designed to produce a malicious, undesired, or illicit response.
    
- **Exam trigger:** **Untrusted input manipulates/interferes with the intended prompt → Prompt injection.**
    

---

### **14. Jailbreaking**

- **Concept:** Jailbreaking occurs when an attacker attempts to **bypass established safety measures or guardrails**.
    
- **Key distinction:** The target is the application's **safety controls**.
    
- **Exam trigger:** **Bypass safety restrictions/guardrails → Jailbreaking.**
    

---

### **15. Hijacking**

- **Concept:** Hijacking is an attempt to **change or manipulate the original prompt with new instructions**.
    
- **Exam trigger:** **Original prompt replaced/manipulated with new instructions → Hijacking.**
    

---

### **16. Poisoning**

- **Concept:** Poisoning is a prompt-engineering risk in which **harmful instructions are embedded in external content**.
    
- **Examples mentioned:** Messages, emails, web pages, and similar sources.
    
- **Exam trigger:** **Harmful instructions embedded in external content → Poisoning.**
    

---

### **17. Key Attack Distinctions**

- **Prompt injection:** Manipulation involving untrusted input and a trusted prompt.
    
- **Jailbreaking:** Attempts to bypass safety measures/guardrails.
    
- **Hijacking:** Attempts to manipulate the original prompt with new instructions.
    
- **Poisoning:** Harmful instructions embedded in content such as emails, messages, or web pages.
    
- **Exam trigger:** Carefully identify **what is being manipulated and where the malicious instruction originates**.
    

---

### **18. AWS Services for Prompt Engineering**

- **Services mentioned:** **Amazon Bedrock and Amazon Titan**.
    
- **Capabilities described:** Pre-trained language models that can be customized and controlled through prompt engineering.
    
- **Additional capabilities mentioned:** APIs and tools for constructing/refining prompts and monitoring/analyzing outputs.
    
- **Exam trigger:** If a scenario asks about AWS services supporting prompt-based generative AI applications, these services are relevant according to the transcript.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Latent space**|Encoded knowledge/patterns and relationships learned by a language model|
|**Conditional probability**|Statistical basis described for selecting the next word based on surrounding context|
|**Hallucination**|Factually incorrect output that may nevertheless appear believable or statistically plausible|
|**Prompt engineering**|Designing and refining input prompts to guide an LLM toward desired outputs|
|**Guardrails**|Safety and privacy controls used to manage generative AI interactions|
|**Prompt injection**|Attack involving manipulation of prompts using untrusted input|
|**Jailbreaking**|Attempt to bypass established safety controls or guardrails|
|**Hijacking**|Attempt to change/manipulate the original prompt with new instructions|
|**Poisoning**|Embedding harmful instructions in external content such as messages or web pages|
|**Prompt specification**|Detailed requirements given to guide the model's desired output|
|**Iterative prompting**|Repeatedly testing and modifying prompts to improve results|
|**Model strengths**|Tasks/topics where the model performs effectively|
|**Model weaknesses**|Tasks/topics where the model has limitations or insufficient knowledge|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Prompt injection**|Untrusted input manipulates the intended prompt|Attack involves prompt manipulation through untrusted input|
|**Jailbreaking**|Attacker tries to bypass safety controls|Targets guardrails/safety measures|
|**Hijacking**|Original prompt is manipulated with new instructions|Focus is changing the original prompt|
|**Poisoning**|Harmful instructions are embedded in external content|Malicious instructions can come from messages, emails, web pages, etc.|
|**Guardrails**|Application needs safety/privacy controls|Controls/filtering designed to manage model interactions|
|**Specific prompt**|Model needs precise direction|Explicitly defines task, format, style, context, etc.|
|**Few-shot examples**|Desired behavior needs demonstration|Examples communicate expected behavior/output|
|**Iterative prompting**|Prompt needs optimization|Test → modify → observe response → refine|
|**Latent space**|Understanding model's learned knowledge|Represents encoded patterns/knowledge within the model|
|**External knowledge source**|Model needs information outside its learned knowledge|Information comes from an external source rather than latent knowledge|

---

## 🧠 Exam Traps

### **1. Prompt Injection vs. Jailbreaking**

**Trap:** Prompt injection and jailbreaking are exactly the same attack.

**Correct:** The transcript distinguishes them. **Prompt injection** involves manipulation through untrusted input, while **jailbreaking** specifically targets/bypasses safety measures and guardrails.

---

### **2. Jailbreaking**

**Trap:** Any incorrect LLM answer is a jailbreak.

**Correct:** Jailbreaking involves attempting to **bypass established safety measures or guardrails**.

---

### **3. Hijacking**

**Trap:** Hijacking means stealing the model or its training data.

**Correct:** In this transcript, hijacking means attempting to **change or manipulate the original prompt with new instructions**.

---

### **4. Poisoning**

**Trap:** Poisoning only occurs when the model's original training dataset is modified.

**Correct:** The transcript describes poisoning in prompt-engineering risks as **harmful instructions embedded in messages, emails, web pages, and other content**.

---

### **5. Guardrails Are Prompting Techniques**

**Trap:** Guardrails are primarily used to improve the creativity or quality of an LLM's response.

**Correct:** Guardrails provide **safety and privacy controls** for generative AI applications.

---

### **6. More Prompt Detail Is Always Better**

**Trap:** The longer and more complicated a prompt is, the better the result will be.

**Correct:** Prompt engineering requires balancing **simplicity and complexity** to avoid vague, unrelated, or unexpected answers.

---

### **7. Prompt Engineering Fixes Every Model Limitation**

**Trap:** A sufficiently detailed prompt can compensate for any lack of model knowledge.

**Correct:** The transcript emphasizes understanding the model's **strengths, weaknesses, and latent-space limitations**.

---

### **8. Hallucination Means the Model Is Broken**

**Trap:** If an LLM produces a fluent but factually incorrect answer, it necessarily indicates a malfunction.

**Correct:** The transcript explains that the model may be functioning according to its statistical generation process while lacking sufficient knowledge about the requested topic.

---

### **9. Latent Space Is an External Database**

**Trap:** The model queries an external database called latent space whenever it receives a prompt.

**Correct:** The transcript describes latent space as **encoded knowledge/patterns within the model**.

---

### **10. Iteration Is Unnecessary**

**Trap:** The first carefully written prompt should be sufficient for production.

**Correct:** Effective prompt engineering involves **experimenting, testing modifications, and observing how responses change**.

---

### **11. Examples Are Only for Few-Shot Prompting**

**Trap:** Examples have no purpose outside formally defining few-shot prompting.

**Correct:** The transcript recommends examples more broadly to communicate **desired behavior and direction**, including sample texts, formats, templates, code, graphs, and charts.

---

### **12. External Content Is Always Trusted**

**Trap:** Information from emails, web pages, or messages can safely be included in prompts.

**Correct:** External content can contain **embedded harmful instructions**, creating poisoning or prompt-manipulation risks.

---

# 📝 Exam Questions

### **Q1.**

An LLM receives a question about a highly specialized topic for which its learned knowledge is limited. Instead of indicating that it lacks sufficient information, it generates a fluent answer that appears plausible but contains incorrect facts.

According to the transcript, what is the most relevant explanation?

**A.** The model has necessarily suffered a prompt-injection attack.  
**B.** The model's latent space may not contain sufficient information about the topic.  
**C.** The model's guardrails have prevented it from accessing its training data.  
**D.** The prompt has automatically converted the model into a zero-shot system.

**Answer: B**

**Why:** The transcript explains that insufficient knowledge in the model's **latent space** can cause it to choose the closest statistical match, increasing hallucination risk.

---

### **Q2.**

A developer notices that an LLM produces better results when given explicit requirements for output format, tone, length, and context.

Which prompt-engineering principle does this demonstrate?

**A.** Use specific and clear instructions.  
**B.** Always minimize the number of prompt components.  
**C.** Replace prompting with full model training.  
**D.** Remove contextual information to avoid influencing the model.

**Answer: A**

**Why:** The transcript recommends being **specific and providing clear instructions or specifications**, including format, style, tone, length, and context.

---

### **Q3.**

A team repeatedly modifies a prompt, tests the resulting response, analyzes the change, and modifies the prompt again until the desired behavior is achieved.

Which technique is being applied?

**A.** Prompt poisoning  
**B.** Iterative prompt experimentation  
**C.** Model hijacking  
**D.** Latent-space expansion

**Answer: B**

**Why:** The transcript explicitly recommends an **iterative process of experimenting with prompts and observing how modifications alter responses**.

---

### **Q4.**

An application receives user-generated text that is combined with a trusted developer-created prompt. A malicious user attempts to manipulate the combined input so that the model produces an unintended response.

Which risk most directly matches this scenario?

**A.** Prompt injection  
**B.** Model maintenance failure  
**C.** Semantic search  
**D.** Latent-space compression

**Answer: A**

**Why:** The transcript defines prompt injection around **untrusted input manipulating/interfering with a trusted prompt**.

---

### **Q5.**

An attacker discovers that an AI application's guardrails prevent certain responses. The attacker constructs inputs specifically designed to bypass those safety restrictions.

What is this attack called?

**A.** Poisoning  
**B.** Hijacking  
**C.** Jailbreaking  
**D.** Few-shot prompting

**Answer: C**

**Why:** **Jailbreaking** specifically targets and attempts to bypass the application's **safety measures/guardrails**.

---

### **Q6.**

An application processes incoming web pages and emails before using their contents as context for an LLM. An attacker embeds harmful instructions inside one of those documents.

Which risk described in the transcript is most relevant?

**A.** Poisoning  
**B.** Zero-shot prompting  
**C.** Model tuning  
**D.** Semantic search

**Answer: A**

**Why:** The transcript describes poisoning as embedding **harmful instructions in messages, emails, web pages, and similar content**.

---

### **Q7.**

A prompt engineer wants to improve an LLM's performance on a customer-support task. The engineer is considering making the prompt extremely long by adding every piece of available information.

What should the engineer consider?

**A.** More information is always better regardless of relevance.  
**B.** Prompts should balance simplicity and complexity to avoid vague, unrelated, or unexpected responses.  
**C.** Prompt length has no relationship to response quality.  
**D.** The model should always be given the entire training dataset in the prompt.

**Answer: B**

**Why:** The transcript recommends balancing **simplicity and complexity** rather than simply making prompts longer.

---

### **Q8.**

A developer is creating prompts for an LLM but repeatedly asks the model questions about topics for which the model has very limited learned knowledge.

Which action is most consistent with the transcript's prompt-engineering guidance?

**A.** Assess the model's strengths and latent-space knowledge for the topic before constructing prompts.  
**B.** Add increasingly complex punctuation until the model knows the topic.  
**C.** Disable all guardrails so the model can access more knowledge.  
**D.** Assume the model will reason its way to the correct answer.

**Answer: A**

**Why:** The transcript emphasizes understanding the model's **latent-space knowledge and limitations** before constructing prompts.

---

### **Q9.**

A security team wants to prevent users from discussing certain prohibited topics, block specific words, filter harmful content, and detect prompt attacks.

Which capability described in the transcript is designed for this purpose?

**A.** Guardrails  
**B.** Few-shot prompting  
**C.** Latent-space analysis  
**D.** Prompt templates

**Answer: A**

**Why:** The transcript describes **guardrails** as providing safety/privacy controls including topic restrictions, word blocking, thresholds, and prompt-attack filtering.

---

### **Q10.**

A developer observes that an LLM generates fluent text by selecting likely words based on the surrounding context. When the model lacks sufficient knowledge about a topic, it produces a statistically plausible but factually incorrect answer.

Which concept best explains this behavior?

**A.** The model uses conditional probability to generate language based on learned patterns.  
**B.** The model always performs explicit human-like reasoning before generating an answer.  
**C.** The model queries an external vector database for every response.  
**D.** The model's guardrails automatically replace missing knowledge.

**Answer: A**

**Why:** The transcript describes LLM generation as selecting words based on **conditional probability and surrounding context**, which can produce plausible but factually incorrect outputs when knowledge is insufficient.

---

# ⚡ 30-Second Revision

**1. Latent space →** encoded knowledge, patterns, and relationships learned by the model.

**2. Limited latent knowledge →** higher chance of hallucination.

**3. Hallucination →** statistically plausible but factually wrong output.

**4. LLM generation →** transcript describes selecting words based on **conditional probability and context**.

**5. Prompt engineering →** design + refine inputs to guide desired outputs.

**6. Good prompts →** be **specific, clear, contextual, and appropriately detailed**.

**7. Examples →** demonstrate desired behavior/output.

**8. Iterate →** **test → modify → observe → refine**.

**9. Know the model →** understand its strengths, weaknesses, and latent-space limitations.

**10. Balance →** avoid both vague prompts and unnecessarily complex/cluttered prompts.

**11. Guardrails →** safety + privacy controls.

**12. Prompt injection →** untrusted input manipulates/interferes with a trusted prompt.

**13. Jailbreaking →** attempts to bypass guardrails/safety measures.

**14. Hijacking →** manipulates the original prompt with new instructions.

**15. Poisoning →** harmful instructions embedded in external content.

**16. Core security distinction →** **Injection = manipulate prompt; Jailbreak = bypass safety; Hijack = alter original prompt; Poison = embed harmful instructions in content.**