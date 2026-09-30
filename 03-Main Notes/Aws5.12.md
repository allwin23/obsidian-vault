# Domain 5, Task Statement 5.2: Governance and Compliance (Steps for Implementing an AI Governance Strategy)

This is part 2 of 5.2. The transcript ends by introducing the "ninth walkthrough question" without including it, so there is nothing to extract for that.

> ⚠️ Uncertain: The transcript refers to a visual (the Generative AI Security Scoping Matrix, "left to right") that isn't shown in the text. It groups scopes 1-2 and scopes 3-5 but does not define scopes 3, 4, and 5 individually or map specific AWS services to specific scope numbers. I have not filled that in, so the questions avoid scope-by-scope distinctions.

---

## 🎯 Exam Essentials

### **1. Step 1: Identify the Scope of Your Responsibility**

- **Concept:** An AI governance strategy begins by identifying your scope of responsibility. This covers **governance and compliance**, **legal and privacy**, **risk management**, **implementing security controls**, and **model resilience**.
- **Key distinction:** Scoping comes **first**, before documenting policies.
- **Exam trigger:** "First step," "begins with," "identify the scope of responsibility."

### **2. Generative AI Security Scoping Matrix: Scopes 1 and 2**

- **Concept:** Scopes 1 and 2 carry the **least responsibility** because you are **consuming a third-party consumer or enterprise application**.
- **Key distinction:** You consume a finished application. You do not build your own AI solution.
- **Exam trigger:** "Third-party consumer or enterprise application," "least responsibility," "third-party model already has all the data and functionality needed."

### **3. Generative AI Security Scoping Matrix: Scopes 3, 4, and 5**

- **Concept:** You are **building your own AI solution**. Your data can be used in **training, fine-tuning, or output** of the model.
- **Key distinction:** You are responsible for **classifying data and model for risk**, **threat modeling**, **limiting access**, **implementing security controls**, and **assuring the model endpoint's resilience**.
- **Exam trigger:** "Building your own AI solution," "our data is used in fine-tuning," "who is responsible for endpoint resilience."

### **4. Minimize Scope: Look Left to Right**

- **Concept:** Search for a solution **left to right**:
    - **Fully trained AI services** (e.g., **Amazon Comprehend**, **Amazon Translate**)
    - **Pre-trained models** (e.g., **Amazon Bedrock**), which can be enhanced with **RAG**
    - **Pre-trained models fine-tuned with your own data** (e.g., **SageMaker JumpStart**)
- **Key distinction:** Move right only if the option to the left doesn't meet your needs.
- **Exam trigger:** "Minimize governance and compliance responsibility," "which option should be evaluated first."

### **5. Why Minimizing Scope Matters**

- **Concept:** Minimizing scope **minimizes your responsibilities** for governance and compliance, legal and privacy, risk management, security controls, and model resilience.
- **Key distinction:** The benefit is reduced **responsibility**, not just cost or convenience.
- **Exam trigger:** "Reduce the company's governance burden," "reduce compliance responsibility."

### **6. Step 2: Document Policies and Train Employees**

- **Concept:** Once scope is determined, **document AI governance policies** and **train employees** on their responsibilities **according to job role and level of access**.
- **Key distinction:** The policy establishes standards for **data governance**, **access requests**, and **model transparency**.
- **Exam trigger:** "Next step after scope is determined," "responsibilities based on job roles and level of access."

### **7. Use Required Compliances and Certifications to Guide Policies**

- **Concept:** Use the **compliances and certifications the business requires** to guide **policies and best practices**.
- **Key distinction:** They **guide policies and best practices**. They do not determine scope.
- **Exam trigger:** "Business is required to meet certification X," "align policy with compliance requirements."

### **8. Monitor Performance, Compliance, and Bias with Pre-Defined Thresholds**

- **Concept:** Define mechanisms to **monitor AI systems' performance, compliance, and bias**, and **determine actions based on pre-defined thresholds**.
- **Key distinction:** Monitoring with **pre-defined thresholds** is distinct from the later **review and revision** of policies.
- **Exam trigger:** "Bias exceeds acceptable limit," "actions triggered by thresholds," "monitor performance, compliance, and bias."

### **9. Frequently Review and Revise Policies**

- **Concept:** **Frequently review results** and **revise existing policies** as necessary to keep alignment with **business goals and AI safety**.
- **Key distinction:** This is an ongoing governance activity, not a one-time policy write-up.
- **Exam trigger:** "Alignment with business goals and AI safety," "policies revised as necessary."

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Generative AI Security Scoping Matrix**|Shows increasing levels of scope (and responsibility) depending on how AI is consumed or implemented|
|**Scopes 1 and 2**|Consuming a third-party consumer or enterprise application. Least responsibility|
|**Scopes 3, 4, and 5**|Building your own AI solution. Data may be used in training, fine-tuning, or output|
|**Model resilience / model endpoint resilience**|Responsibility you assume when building your own solution|
|**Threat modeling**|One of the responsibilities when building your own AI solution|
|**Fully trained AI services**|Leftmost option: e.g., Amazon Comprehend, Amazon Translate|
|**Pre-trained models (Amazon Bedrock)**|Middle option: can be enhanced with retrieval augmented generation (RAG)|
|**SageMaker JumpStart**|Pre-trained models that can be fine-tuned with your own data|
|**Pre-defined thresholds**|Trigger points for actions when monitoring performance, compliance, and bias|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Scopes 1-2**|A third-party application already has the data and functionality you need|Consuming an application, so the least responsibility|
|**Scopes 3-5**|You are building your own AI solution|You classify data/model for risk, threat model, limit access, implement security controls, assure endpoint resilience|
|**Amazon Comprehend / Amazon Translate**|A fully trained AI service meets the need|Evaluate **first** when minimizing scope|
|**Amazon Bedrock (+ RAG)**|Fully trained services don't meet your needs|Pre-trained model, enhanced with RAG|
|**SageMaker JumpStart**|You need a pre-trained model fine-tuned with your own data|Furthest right, so the most scope of the three|
|**Monitoring with thresholds**|You need defined actions when performance, compliance, or bias crosses a limit|Ongoing detection with pre-defined triggers|
|**Review and revise policies**|You need alignment with business goals and AI safety|Frequent review of results, revising policies as needed|

---

## 🧠 Exam Traps

### **1.**

**Trap:** Using a third-party application means you have no governance responsibility.

**Correct:** Scopes 1 and 2 carry the **least** responsibility, not none.

### **2.**

**Trap:** Start with fine-tuning so the model fits your data best.

**Correct:** Look **left to right**: fully trained AI services first, then pre-trained models (Bedrock with RAG), then fine-tunable models (SageMaker JumpStart).

### **3.**

**Trap:** Minimizing scope is mainly a cost-saving tactic.

**Correct:** It minimizes **responsibilities** for governance and compliance, legal and privacy, risk management, security controls, and model resilience.

### **4.**

**Trap:** Your data only matters during training.

**Correct:** Data can be used in **training, fine-tuning, or output** of the model.

### **5.**

**Trap:** Required certifications determine your scope on the matrix.

**Correct:** Certifications **guide policies and best practices**. Scope is determined first, by how AI is consumed or implemented.

### **6.**

**Trap:** One training and policy set applies uniformly to all employees.

**Correct:** Train employees on responsibilities **according to their job roles and level of access**.

### **7.**

**Trap:** Monitoring and policy review are the same activity.

**Correct:** **Monitoring** measures performance, compliance, and bias against **pre-defined thresholds** to determine actions. **Review** revises policies to stay aligned with business goals and AI safety.

### **8.**

**Trap:** The five responsibility areas of AI governance scoping are the same as the data management areas (quality, integration, security, compliance, lifecycle) from part 1.

**Correct:** Scoping covers **governance and compliance, legal and privacy, risk management, security controls, and model resilience**.

---

# 📝 Exam Questions

### **Question 1**

A company runs a generative AI system in production. Leadership wants defined actions to follow whenever measured bias, compliance status, or performance moves beyond acceptable limits set in advance. Which governance element addresses this requirement most directly?

A. Documenting standards for data governance, access requests, and model transparency  
B. Defining mechanisms to monitor performance, compliance, and bias, with actions determined by pre-defined thresholds  
C. Frequently reviewing results and revising policies to align with business goals and AI safety  
D. Training employees on responsibilities according to job role and level of access

**Answer: B — Defining mechanisms to monitor performance, compliance, and bias, with actions determined by pre-defined thresholds**

**Why:** The clue is **pre-defined limits that trigger actions**. Review (C) is periodic policy revision, not threshold-driven action.

---

### **Question 2**

A company currently uses a third-party enterprise AI application. It decides to build its own solution where its proprietary data will be used in fine-tuning. Which set of responsibilities newly applies to the company?

A. Legal and privacy responsibilities only, because the vendor secures the model  
B. Maintaining the third-party provider's compliance certifications  
C. Classifying the data and model for risk, threat modeling, limiting access, implementing security controls, and assuring the model endpoint's resilience  
D. Documenting model transparency standards only, with no change to security responsibilities

**Answer: C — Classifying the data and model for risk, threat modeling, limiting access, implementing security controls, and assuring the model endpoint's resilience**

**Why:** Scopes 3-5 involve building your own solution, where your data can be used in training, fine-tuning, or output, and these responsibilities apply.

---

### **Question 3**

A company needs to translate documents between languages. Leadership wants to minimize governance and compliance responsibility. Following the recommended approach, what should the team evaluate first?

A. A fully trained AI service such as Amazon Translate  
B. A pre-trained model in Amazon Bedrock enhanced with RAG  
C. A SageMaker JumpStart model fine-tuned with company data  
D. A custom model trained from scratch

**Answer: A — A fully trained AI service such as Amazon Translate**

**Why:** Look for solutions **left to right**, beginning with fully trained AI services. Move right only if they don't meet the need.

---

### **Question 4**

A business must meet specific compliances and certifications required by its industry. How should these be used when implementing its AI governance strategy?

A. To determine the company's scope of responsibility on the scoping matrix  
B. To replace monitoring of performance, compliance, and bias  
C. To decide which pre-trained model to fine-tune  
D. To guide policies and best practices

**Answer: D — To guide policies and best practices**

**Why:** Required compliances and certifications guide policies and best practices. Scope is determined by how AI is consumed or implemented.

---

### **Question 5**

When identifying the scope of its responsibility for AI governance, which set of areas does the transcript's approach cover?

A. Governance and compliance, legal and privacy, risk management, implementing security controls, and model resilience  
B. Governance and compliance, legal and privacy, cost optimization, operational excellence, and model resilience  
C. Governance and compliance, legal and privacy, risk management, implementing security controls, and model explainability  
D. Data quality, data integration, data security, compliance, and data lifecycle management

**Answer: A — Governance and compliance, legal and privacy, risk management, implementing security controls, and model resilience**

**Why:** C swaps in explainability for resilience, and D lists the data management areas from part 1 of 5.2.

---

### **Question 6**

A team found that a pre-trained Amazon Bedrock model enhanced with RAG still does not meet its needs. It now requires a pre-trained model adapted using its own data. Which is the next option along the recommended progression?

A. Amazon Comprehend  
B. A pre-trained SageMaker JumpStart model fine-tuned with the company's own data  
C. Amazon Translate  
D. Amazon Bedrock with RAG using additional documents

**Answer: B — A pre-trained SageMaker JumpStart model fine-tuned with the company's own data**

**Why:** The progression is fully trained AI services → pre-trained models (Bedrock with RAG) → pre-trained models fine-tuned with your own data (JumpStart). A and C are earlier in the progression.

---

### **Question 7**

A team has just determined its scope of responsibility for a new AI solution. What is the next step in implementing its governance strategy?

A. Define monitoring mechanisms with pre-defined thresholds for bias and performance  
B. Frequently review results and revise existing policies  
C. Document AI governance policies and train employees on responsibilities by job role and level of access  
D. Re-evaluate the available services to further minimize scope

**Answer: C — Document AI governance policies and train employees on responsibilities by job role and level of access**

**Why:** Once scope is determined, the next step is documenting policies and training employees. Monitoring and review come after.

---

# ⚡ 30-Second Revision

1. **Step 1 → identify scope of responsibility:** governance and compliance, legal and privacy, risk management, security controls, model resilience.
2. **Scopes 1-2 → consuming a third-party consumer or enterprise application → least responsibility.**
3. **Scopes 3-5 → building your own AI solution → data in training, fine-tuning, or output.** You classify data and model for risk, threat model, limit access, implement security controls, and assure endpoint resilience.
4. **Search left to right:** fully trained AI services (Comprehend, Translate) → pre-trained models (Bedrock + RAG) → fine-tunable pre-trained models (SageMaker JumpStart).
5. **Minimizing scope → minimizes governance, legal and privacy, risk, security, and resilience responsibilities.**
6. **After scope → document policies and train employees by job role and level of access.** Standards cover data governance, access requests, and model transparency.
7. **Required compliances and certifications → guide policies and best practices.**
8. **Monitor performance, compliance, and bias → actions based on pre-defined thresholds.**
9. **Frequently review results and revise policies → alignment with business goals and AI safety.**