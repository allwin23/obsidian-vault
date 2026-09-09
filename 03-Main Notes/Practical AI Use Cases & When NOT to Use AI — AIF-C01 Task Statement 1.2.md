

## 🎯 Exam Essentials

### When Should AI/ML Be Considered?

AI is particularly useful when a problem involves:

- **Large volumes of data**
    
- **High-speed data processing**
    
- **Pattern recognition**
    
- **Fraud or anomaly detection**
    
- **Forecasting**
    
- **Repetitive tasks**
    
- Tasks that benefit from automation and can operate continuously
    

**Exam trigger:**

> "Analyze huge amounts of data to identify patterns or anomalies" → **AI/ML is a strong candidate**

### Common AI Use Cases

|Business problem|AI/ML benefit|
|---|---|
|Fraud detection|Identify unusual patterns|
|Demand forecasting|Predict future demand|
|Waste reduction|Forecast resource/product requirements|
|Repetitive tasks|Automate routine work|
|Large-scale data analysis|Find patterns humans may miss|
|Customer insights|Analyze large amounts of customer data|

---

### ⚠️ AI Is Not Always the Best Solution

Before choosing AI, consider:

1. **Business value** — What measurable benefit will AI provide?
    
2. **Cost** — Training, inference, infrastructure, and ongoing maintenance can be expensive.
    
3. **Complexity** — Is AI actually necessary?
    
4. **Compliance** — Does the decision require transparency or explainability?
    
5. **Determinism** — Must identical inputs always produce exactly the same output?
    

**Exam trigger:**

> "The cost of building/training/maintaining the model exceeds the expected business benefit"  
> → **Don't use AI / choose a simpler solution.**

---

## Deterministic vs Probabilistic Systems

### Deterministic

A **deterministic system** produces the **same output for the same input**, assuming the rules/system haven't changed.

Example:

> IF credit score ≥ 750 AND loan ≤ $10,000 → approve

Same input → same result.

**Rule-based systems are generally deterministic.**

**Exam trigger:**

> "Same input must always produce exactly the same output" → **Deterministic/rule-based system**

---

### Probabilistic

ML models generally produce outputs based on **learned probabilities/likelihoods** rather than fixed rules.

Example:

> Loan approval probability = 87%

The model is estimating the likelihood of an outcome rather than following a simple fixed rule.

**Exam trigger:**

> "Predict likelihood/probability" → **Probabilistic ML**

---

## Interpretability vs Model Complexity

- **Interpretability:** How easily humans can understand **why a model produced a particular prediction**.
    
- Complex models, especially deep neural networks, can be difficult to interpret.
    
- This creates a potential tradeoff between:
    
    - **Model complexity/performance**
        
    - **Interpretability/transparency**
        

For decisions with strict **compliance or transparency requirements**, a simpler model or even a **rule-based system** may be more appropriate.

### Important nuance

Don't memorize:

> "Complex model = always better performance."

That's not guaranteed.

The exam-relevant idea is:

> **More complex models can be harder to interpret.**

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**AI use case**|Business problem where AI can provide useful automation, prediction, or pattern recognition|
|**Deterministic**|Same input produces the same output|
|**Probabilistic**|Output represents likelihood/probability rather than a fixed rule|
|**Interpretability**|Ability to understand why a model made a prediction|
|**Transparency**|Ability to understand/communicate how a system operates or reaches outcomes|
|**Rule-based system**|Uses explicitly defined rules rather than learned ML patterns|
|**Forecasting**|Predicting future values/events using historical patterns|
|**Pattern recognition**|Identifying meaningful patterns in data|
|**Anomaly detection**|Identifying unusual patterns or observations|

---

## ⚔️ Important Comparisons

|System|How it makes decisions|Same input → same output?|Best when|
|---|---|---|---|
|**Rule-based**|Explicit predefined rules|✅ Generally yes|Deterministic, transparent decisions|
|**ML model**|Learned patterns/probabilities|Not necessarily guaranteed|Prediction/pattern recognition|

### AI vs Rule-Based System

**Use AI/ML when:**

- Patterns are difficult to explicitly define.
    
- Large datasets are available.
    
- Prediction or pattern recognition is needed.
    
- The business benefit justifies the cost.
    

**Consider rule-based systems when:**

- Rules are simple and explicit.
    
- Decisions must be deterministic.
    
- Full transparency is required.
    
- AI doesn't provide enough additional business value.
    

---

## 🧠 Exam Traps

- **Trap:** AI should be used whenever a problem involves a large amount of data.
    
    - **Correct:** Large data volumes make AI potentially useful, but you must also consider **cost, business value, requirements, and alternatives**.
        
- **Trap:** ML models are deterministic because the same model receives the same inputs.
    
    - **Correct:** ML is generally **probabilistic**, whereas rule-based systems are typically deterministic.
        
- **Trap:** A more complex AI model is always the best choice.
    
    - **Correct:** Complexity can make models **harder to interpret** and may be inappropriate when transparency is critical.
        
- **Trap:** If a loan decision requires complete explainability, use the most complex neural network available.
    
    - **Correct:** Consider a **simpler/interpretable model or rule-based approach** when complete transparency is required.
        
- **Trap:** AI automatically makes every business process cheaper.
    
    - **Correct:** AI has **training, inference, infrastructure, and maintenance costs**. The expected business benefit should justify those costs.
        

---

## 📝 Exam Questions

### Question 1

A company receives millions of transactions every day and wants to identify unusual transaction patterns that could indicate fraud.

Why is AI/ML a good candidate for this use case?

A. AI can analyze large amounts of data and identify patterns  
B. AI guarantees every transaction will be classified correctly  
C. AI eliminates the need for training data  
D. AI always costs less than rule-based systems

**Answer:** A

**Why:** Pattern recognition across large datasets is a strong AI/ML use case.

---

### Question 2

A company is considering building an ML model to reduce product waste. The expected annual savings are $20,000, but building and maintaining the system is estimated to cost $100,000 per year.

What should the company do FIRST?

A. Build the model because AI is always beneficial  
B. Increase the model's complexity  
C. Evaluate whether the business benefits justify the cost  
D. Replace all existing systems with AI

**Answer:** C

**Why:** AI should be selected based on **business value versus total cost**, not simply because the technology is available.

---

### Question 3

A company's compliance requirements state that a loan application must always produce the exact same decision when the same input values are provided.

Which type of solution is MOST appropriate?

A. Probabilistic ML model  
B. Rule-based deterministic system  
C. Generative AI model  
D. Randomized neural network

**Answer:** B

**Why:** A deterministic rule-based system can ensure **consistent outputs for identical inputs**.

---

### Question 4

A financial institution wants to use AI for loan decisions but has a strict requirement that decision logic must be completely understandable to auditors.

Which consideration is MOST important when selecting the model?

A. Maximizing model complexity  
B. Interpretability  
C. Increasing randomness  
D. Increasing training time

**Answer:** B

**Why:** **Interpretability** is critical when humans need to understand and explain model decisions.

---

### Question 5

A company wants to automate a process governed by a small number of clearly defined business rules. The same input must always produce the same result.

Which approach is MOST appropriate?

A. Generative AI  
B. Deep learning  
C. Rule-based system  
D. Unsupervised learning

**Answer:** C

**Why:** Clearly defined rules combined with a requirement for deterministic behavior make a **rule-based system** a strong choice.

---

### Question 6

A company wants to forecast the amount of inventory it will need next month based on historical sales patterns.

Which AI/ML capability is MOST relevant?

A. Forecasting  
B. Tokenization  
C. Image classification  
D. Speech synthesis

**Answer:** A

**Why:** Predicting future demand from historical patterns is a **forecasting** use case.

---

## ⚡ 30-Second Revision

- **AI shines:** repetitive work, huge datasets, pattern recognition, fraud detection, forecasting.
    
- Don't use AI automatically—compare **business benefit vs cost**.
    
- **Deterministic → same input = same output.**
    
- **Rule-based systems → generally deterministic + transparent.**
    
- **ML → generally probabilistic**, producing likelihoods/predictions.
    
- **Interpretability → can humans understand why the model made its decision?**
    
- Complex models can be **harder to interpret**.
    
- If **determinism** is mandatory → consider a **rule-based system**.
    
- If **complete transparency** is mandatory → consider a **simpler/interpretable model or rules**.
    
- **Exam mindset:** Choose AI because it solves the business problem better—not simply because AI is available.