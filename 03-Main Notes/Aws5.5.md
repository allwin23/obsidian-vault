# Domain 5 — Task Statement 5.1: Explain methods to secure AI systems

## 🎯 Exam Essentials

### **1. Training Data Poisoning**

- **Concept:** An AI model learns its behavior from training data. If an attacker gains access to the training data and introduces malicious or incorrectly labeled data, they can change the model's predictions.
    
- **Key distinction:** The attack targets the **training data**, potentially causing the trained model to learn incorrect behavior.
    
- **Exam trigger:** Look for an attacker **modifying, corrupting, or injecting malicious examples into training data** to influence future predictions.
    

### **2. Fraud Detection Data Poisoning**

- **Concept:** A fraud model trained on transactions labeled as fraud/not fraud can be manipulated if an attacker adds fraudulent transactions labeled as **not fraud**.
    
- **Key distinction:** The attacker is manipulating the **training data labels**, not merely sending malicious input to an already deployed model.
    
- **Exam trigger:** A model starts incorrectly classifying a specific type of fraudulent transaction because its **training examples were deliberately corrupted**.
    

### **3. Adversarial Inputs**

- **Concept:** An attacker can make subtle, carefully designed modifications to input data that cause an AI model to produce an incorrect prediction.
    
- **Key distinction:** Unlike training-data poisoning, adversarial input attacks target the **input presented to an already operating model**.
    
- **Exam trigger:** Look for **small/subtle modifications to an image or other input designed to cause misclassification**.
    

### **4. Model Inversion**

- **Concept:** An attacker can repeatedly provide inputs to a model and study its outputs to infer information about the **training data**.
    
- **Key distinction:** The attacker is using the model's **outputs to infer information about training inputs**.
    
- **Exam trigger:** Look for repeated queries, output analysis, confidence scores, and attempts to **reconstruct or infer sensitive training information**.
    

### **5. Model Extraction / Reverse Engineering**

- **Concept:** With enough input/output pairs, an attacker can train another model based on the original model's outputs, creating a model that behaves similarly to the original.
    
- **Key distinction:** The goal described here is to **replicate the original model**, whereas model inversion focuses on inferring information about the original model's training data.
    
- **Exam trigger:** Look for an attacker collecting **many input/output pairs** and using them to create a copy or approximation of the original model.
    

### **6. Prompt Injection**

- **Concept:** Large language models can be attacked through **prompt injection**, where malicious instructions are included in a prompt to influence the model's behavior.
    
- **Key distinction:** The attacker manipulates the model through **instructions in the input prompt**, potentially causing it to ignore or alter its intended prompt template.
    
- **Exam trigger:** Phrases such as **"ignore previous instructions," "alter the prompt,"** or malicious instructions designed to make an LLM reveal sensitive information.
    

### **7. Least Privilege for AI Systems**

- **Concept:** AI systems should follow the **principle of least privilege**, meaning access to data, models, and resources should be limited to what is required.
    
- **Key distinction:** Security should apply not only to users but also to the **data and models** used by AI systems.
    
- **Exam trigger:** Scenario asks how to reduce unnecessary access to **AI data, models, or AWS resources**.
    

### **8. Encrypt AI Data and Artifacts**

- **Concept:** Data and model artifacts should be **encrypted** as an additional layer of protection.
    
- **Key distinction:** Encryption protects data/artifacts even if unauthorized access to the underlying storage occurs.
    
- **Exam trigger:** Scenario asks for an additional protection layer for **training data, model artifacts, or other AI assets**.
    

### **9. Restrict Model Access**

- **Concept:** Access to AI models should be limited and controlled to reduce the possibility of **reverse engineering**.
    
- **Key distinction:** Restricting access reduces the amount of information an attacker can gather about the model through repeated interactions.
    
- **Exam trigger:** An attacker is attempting to **study model behavior or replicate the model**.
    

### **10. Validate User Input**

- **Concept:** Input provided by users should be **inspected and validated** before being provided to the model.
    
- **Key distinction:** Input validation can help detect unusual patterns and malicious inputs before they influence the model.
    
- **Exam trigger:** Requirement involves detecting **malicious or unusual user input** before inference.
    

### **11. Prompt-Injection Detection**

- **Concept:** An LLM can be trained to recognize known **prompt-injection attack patterns** and respond with something such as **"prompt attack detected."**
    
- **Key distinction:** The model is being used to identify suspicious prompt patterns rather than blindly processing every user instruction.
    
- **Exam trigger:** Scenario asks how an LLM can identify **known prompt-attack patterns**.
    

### **12. Limit Model Output**

- **Concept:** Avoid providing unnecessary information in model outputs because excessive output can give attackers information that helps them **infer details about the model**.
    
- **Key distinction:** Security applies to both **inputs and outputs**.
    
- **Exam trigger:** Scenario involves an attacker analyzing detailed model responses to learn about the underlying model.
    

### **13. Adversarial Training**

- **Concept:** Models can be trained using **adversarial inputs** to help them avoid being tricked by adversarial examples.
    
- **Key distinction:** The defensive technique deliberately exposes the model to adversarial inputs during training.
    
- **Exam trigger:** Requirement is to make a model more resistant to **carefully manipulated inputs**.
    

### **14. Frequent Retraining**

- **Concept:** Training models frequently on new data can help undo damage caused by **corrupted training data**.
    
- **Key distinction:** Retraining addresses damage that may have entered the training process; it is different from simply monitoring the deployed model.
    
- **Exam trigger:** Scenario involves a model potentially affected by **corrupted/poisoned training data** and asks how to recover.
    

### **15. Separate Validation Dataset**

- **Concept:** Keep a **separate dataset for validation** and validate the model after each retraining before deploying it.
    
- **Key distinction:** The validation data provides an independent basis for evaluating the retrained model before it reaches production.
    
- **Exam trigger:** Scenario describes **retraining followed by a requirement to validate before deployment**.
    

### **16. Training Data Quality Monitoring**

- **Concept:** Training data should be routinely scanned and monitored for **quality issues and anomalies before being used for training**.
    
- **Key distinction:** Detecting anomalies before training can prevent corrupted data from influencing the model.
    
- **Exam trigger:** Requirement is to detect **data-quality problems before training begins**.
    

### **17. Investigating Prediction Changes**

- **Concept:** If a model's predictions change from their historical pattern, the change should be investigated to determine whether the cause is **low data quality or an attack**.
    
- **Key distinction:** A change in model behavior does not automatically mean an attack; the root cause needs investigation.
    
- **Exam trigger:** Model predictions suddenly **deviate from historical behavior**.
    

### **18. SageMaker Model Monitor**

- **Concept:** **Amazon SageMaker Model Monitor** monitors the quality of SageMaker ML models in production.
    
- **Key distinction:** It provides continuous monitoring for **model quality, data quality, drift, and anomalies** as described in the transcript.
    
- **Exam trigger:** Look for a deployed SageMaker model that needs **continuous production monitoring**.
    

### **19. Model Monitor and Data Drift**

- **Concept:** SageMaker Model Monitor can set up automated alerts for deviations in model quality, including **data drift or anomalies**.
    
- **Key distinction:** Drift represents a change in the data pattern relative to the established baseline.
    
- **Exam trigger:** A production model's input data begins **deviating from its expected baseline**.
    

### **20. Model Monitor Baselines**

- **Concept:** SageMaker Model Monitor compares current data/model information with **baselines**, generating statistics and metrics.
    
- **Key distinction:** The baseline establishes the expected characteristics against which current behavior can be evaluated.
    
- **Exam trigger:** Scenario describes comparing **current production data against historical/training baseline statistics**.
    

### **21. Model Monitor and CloudWatch**

- **Concept:** Model Monitor generates statistics and metrics that can be viewed in **SageMaker Studio** and sent to **Amazon CloudWatch**.
    
- **Key distinction:** SageMaker Model Monitor performs the monitoring; CloudWatch provides monitoring/logging and alerting capabilities around the resulting information.
    
- **Exam trigger:** Scenario combines **model monitoring + metrics + CloudWatch alerts/logs**.
    

### **22. Data Capture**

- **Concept:** To use SageMaker Model Monitor for **data quality monitoring**, data capture must be enabled.
    
- **Key distinction:** Data capture collects inference inputs and outputs from an inference endpoint or batch transform job and stores the data in **Amazon S3**.
    
- **Exam trigger:** Question asks what must be enabled before monitoring **production inference data quality**.
    

### **23. Data Quality Baseline**

- **Concept:** A training dataset can usually be used to create a **data-quality baseline**.
    
- **Key distinction:** The baseline represents expected characteristics against which the current dataset is evaluated.
    
- **Exam trigger:** Data-quality monitoring scenario asks what dataset can be used to establish the baseline.
    

### **24. Model Performance Monitoring**

- **Concept:** SageMaker Model Monitor can also monitor **model performance** by comparing inferences against labeled data.
    
- **Key distinction:** Model performance monitoring requires **labeled data** to evaluate whether predictions are correct.
    
- **Exam trigger:** Scenario provides actual labels and asks to evaluate **prediction performance**.
    

### **25. Ground Truth for Model Performance**

- **Concept:** For model quality monitoring, the transcript describes comparing inferences with label data from **SageMaker Ground Truth** for the same inputs.
    
- **Key distinction:** **Data quality monitoring** evaluates characteristics of the data, while **model performance monitoring** evaluates predictions against labeled outcomes.
    
- **Exam trigger:** Look for **labeled data + predictions + evaluating model performance**.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Training data poisoning**|Manipulating training data to change model behavior/predictions.|
|**Adversarial input**|Carefully modified input designed to cause model misclassification.|
|**Model inversion**|Inferring training-data information by repeatedly querying and analyzing model outputs.|
|**Model extraction / reverse engineering**|Using input/output pairs to create a model similar to the original.|
|**Prompt injection**|Malicious instructions inserted into an LLM prompt to influence its behavior.|
|**Adversarial training**|Training models with adversarial inputs to improve resistance to attacks.|
|**Data drift**|Change in production data relative to the established baseline.|
|**Anomaly**|Unusual behavior or data pattern requiring investigation.|
|**SageMaker Model Monitor**|Monitors SageMaker model/data quality in production.|
|**Data capture**|Captures inference inputs and outputs for monitoring and stores them in S3.|
|**Baseline**|Reference dataset/statistics used to compare current data or model behavior.|
|**Data quality monitoring**|Monitoring the quality/characteristics of inference data.|
|**Model performance monitoring**|Evaluating predictions against labeled data.|
|**SageMaker Ground Truth**|Source of label data used in the described model-quality monitoring process.|
|**Amazon CloudWatch**|Receives monitoring metrics/log information and provides threshold-based notifications.|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Training data poisoning**|Attacker modifies training data|Attack targets the **training dataset**|
|**Adversarial input**|Attacker manipulates an inference input|Attack targets the **model input**|
|**Model inversion**|Attacker wants information about training data|Uses model outputs to **infer training information**|
|**Model extraction**|Attacker wants a copy of the model|Uses input/output pairs to **replicate model behavior**|
|**Prompt injection**|Attacker targets an LLM with malicious instructions|Manipulates **prompt instructions**|
|**Adversarial training**|Defending against adversarial inputs|Trains the model using adversarial examples|
|**Data quality monitoring**|Checking production input data|Requires **data capture** and compares data against a baseline|
|**Model performance monitoring**|Checking prediction quality|Uses **labeled data** to evaluate predictions|
|**SageMaker Model Monitor**|Continuous production model monitoring|Generates statistics/metrics and detects deviations|
|**SageMaker Studio**|Viewing Model Monitor results|Displays monitoring statistics and metrics|
|**CloudWatch**|Monitoring/alerting|Receives monitoring information and can notify when thresholds are reached|
|**Data baseline**|Establishing expected data characteristics|Usually based on the **training dataset**|
|**Model-performance baseline**|Establishing expected model performance|Uses **labeled data**|

---

## 🧠 Exam Traps

### **1.**

**Trap:** Training data poisoning and adversarial input attacks are essentially the same because both cause incorrect predictions.

**Correct:** **Training data poisoning** corrupts the data used to train the model; **adversarial inputs** manipulate input presented to the model.

### **2.**

**Trap:** Model inversion is primarily about stealing a copy of the model itself.

**Correct:** Model inversion is described as using model outputs to **infer information about the training data**.

### **3.**

**Trap:** Model extraction is the same as model inversion.

**Correct:** The transcript distinguishes them: model extraction uses **input/output pairs to create a similar model**, while model inversion attempts to infer **training input information**.

### **4.**

**Trap:** Prompt injection requires modifying the model's training dataset.

**Correct:** Prompt injection targets an LLM by providing **malicious instructions in the prompt**.

### **5.**

**Trap:** Limiting model outputs is unrelated to security because only inputs can leak information.

**Correct:** The transcript warns that unnecessary output can provide attackers with information that helps them **infer details about the model**.

### **6.**

**Trap:** If model predictions suddenly change, the cause must be an attack.

**Correct:** The change should be investigated to determine whether it results from **low data quality or an attack**.

### **7.**

**Trap:** Retraining alone guarantees that a poisoned model will be fixed.

**Correct:** The transcript recommends **frequent retraining**, maintaining separate validation data, and **validating after retraining before deployment**.

### **8.**

**Trap:** Data quality monitoring and model performance monitoring use exactly the same baseline information.

**Correct:** The transcript describes data-quality monitoring using a **training dataset baseline**, while model-performance monitoring uses **labeled data** to evaluate predictions.

### **9.**

**Trap:** Data capture is optional when using SageMaker Model Monitor for data quality monitoring.

**Correct:** The transcript explicitly states that **data capture must be enabled** for data quality monitoring.

### **10.**

**Trap:** SageMaker Model Monitor only monitors model accuracy.

**Correct:** According to the transcript, Model Monitor can monitor **data quality, model quality, data drift, and anomalies**.

### **11.**

**Trap:** CloudWatch performs the actual model-quality comparison instead of SageMaker Model Monitor.

**Correct:** **SageMaker Model Monitor** compares data/model information against baselines and generates metrics; CloudWatch receives monitoring information and provides threshold-based notifications.

### **12.**

**Trap:** You should monitor only the deployed model and not the training data.

**Correct:** The transcript recommends routinely scanning and monitoring **training data quality and anomalies before training**.

---

# 📝 Exam Questions

### **Question 1**

A fraud detection model is retrained periodically using financial transactions labeled as fraudulent or legitimate. An attacker gains access to the training dataset and changes the labels of selected fraudulent transactions to "legitimate." After retraining, the model frequently classifies similar fraudulent transactions as legitimate. Which attack best describes the scenario?

A. Adversarial input attack

B. Model inversion

C. Training data poisoning

D. Model extraction

**Answer: C — Training data poisoning.**

**Why:** The attacker deliberately corrupted the **training data and labels** so that the trained model would learn incorrect behavior.

### **Question 2**

An attacker repeatedly submits slightly modified facial images to an employee-recognition model. By analyzing the model's names and confidence scores, the attacker gradually constructs an image that produces a high-confidence identification of a particular employee. Which attack does this scenario most closely represent?

A. Training data poisoning

B. Model inversion

C. Prompt injection

D. Model extraction

**Answer: B — Model inversion.**

**Why:** The attacker is repeatedly querying the model and analyzing its outputs to **infer information about the training data**.

### **Question 3**

A competitor has no access to a company's trained AI model or training dataset. However, it can send queries to the model and observe the corresponding outputs. After collecting a large number of input/output pairs, it trains its own model that behaves similarly to the company's model. Which attack is being described?

A. Model inversion

B. Adversarial input

C. Model extraction

D. Training data poisoning

**Answer: C — Model extraction.**

**Why:** The attacker is using **input/output pairs to create a model similar to the original**, which matches the model-extraction/reverse-engineering description.

### **Question 4**

An organization deploys an LLM that uses a predefined prompt template to process customer requests. An attacker includes malicious instructions designed to cause the LLM to ignore or alter the intended prompt template and reveal sensitive information. Which vulnerability is most directly involved?

A. Model inversion

B. Prompt injection

C. Training data poisoning

D. Adversarial image input

**Answer: B — Prompt injection.**

**Why:** The attack directly manipulates the LLM through **malicious instructions contained in the prompt**.

### **Question 5**

A company wants to make an image-classification model more resistant to carefully modified inputs designed to cause misclassification. Which approach described in the lesson directly addresses this goal?

A. Train the model using adversarial inputs.

B. Increase the number of IAM users accessing the model.

C. Disable data capture on the inference endpoint.

D. Store the model artifacts in an unencrypted S3 bucket.

**Answer: A — Train the model using adversarial inputs.**

**Why:** The transcript recommends **adversarial training** to help models avoid being tricked by adversarial inputs.

### **Question 6**

A production SageMaker model has recently started producing predictions that differ significantly from its historical pattern. The security team wants to determine whether the change is caused by poor-quality input data or an attack. Which approach is most consistent with the lesson?

A. Immediately assume the model has been extracted and replace it.

B. Investigate the deviation and use production monitoring to identify data drift or anomalies.

C. Disable all model outputs permanently and delete the training dataset.

D. Increase the model's output detail so the attacker can be identified.

**Answer: B — Investigate the deviation and use production monitoring to identify data drift or anomalies.**

**Why:** The lesson explicitly says prediction changes should be investigated to determine whether the root cause is **low data quality or an attack**, and Model Monitor can identify deviations such as drift and anomalies.

### **Question 7**

A company deploys a SageMaker inference endpoint and wants to monitor the quality of its production input data. It plans to compare incoming inference data against a baseline. What must be enabled to support the monitoring process described in the lesson?

A. Model extraction

B. Data capture

C. Prompt injection detection

D. IAM Identity Center

**Answer: B — Data capture.**

**Why:** The transcript states that **data capture must be enabled** for SageMaker Model Monitor to monitor data quality. The captured inference input/output is stored in S3.

### **Question 8**

A company wants to monitor whether production inference data is deviating from the characteristics of the data used to establish its expected baseline. Which SageMaker capability described in the lesson is most directly applicable?

A. SageMaker Model Monitor

B. SageMaker Role Manager

C. SageMaker Ground Truth

D. SageMaker Serverless Inference

**Answer: A — SageMaker Model Monitor.**

**Why:** Model Monitor compares current data against baselines and can detect **data drift and anomalies**.

### **Question 9**

A company wants to evaluate whether a deployed model's predictions remain accurate. It has labeled data corresponding to the same inputs that were sent to the model. Which monitoring approach described in the lesson should it use?

A. Data quality monitoring using an unlabeled production baseline

B. Model performance monitoring using labeled data

C. Prompt-injection monitoring using CloudTrail

D. Model inversion monitoring using S3 Block Public Access

**Answer: B — Model performance monitoring using labeled data.**

**Why:** The transcript describes model-performance monitoring as comparing **inferences against label data** for the same inputs.

### **Question 10**

A team wants to continuously monitor a production SageMaker model and receive an alert when model quality deviates beyond a predefined threshold. Which combination best matches the workflow described in the lesson?

A. SageMaker Model Monitor with CloudWatch notifications

B. SageMaker Role Manager with IAM user credentials

C. Amazon Macie with S3 Block Public Access

D. AWS KMS with VPC interface endpoints

**Answer: A — SageMaker Model Monitor with CloudWatch notifications.**

**Why:** Model Monitor generates monitoring statistics/metrics, while CloudWatch can receive the information and notify when **preset thresholds** are reached.

### **Question 11**

An ML team wants to reduce the likelihood that corrupted training data will permanently affect a model. The team also wants to ensure that a retrained model is safe to deploy. Which approach best matches the lesson?

A. Retrain frequently, maintain a separate validation dataset, and validate the model after each retraining.

B. Retrain only when a user reports an incorrect prediction and immediately deploy the new model.

C. Use only production inference data as the validation dataset and deploy every retrained model automatically.

D. Increase model output detail so that corrupted predictions can be identified by users.

**Answer: A — Retrain frequently, maintain a separate validation dataset, and validate the model after each retraining.**

**Why:** These are the specific defensive practices described for reducing the impact of corrupted training data and preventing unvalidated models from reaching production.

### **Question 12**

A company wants to reduce the amount of information an attacker can obtain by repeatedly interacting with its model. Which security practice from the lesson most directly addresses the information exposed through model responses?

A. Provide as much model output information as possible so attackers can be identified.

B. Avoid providing unnecessary information in model outputs.

C. Disable all model monitoring after deployment.

D. Remove validation datasets after each retraining cycle.

**Answer: B — Avoid providing unnecessary information in model outputs.**

**Why:** Excessive output can give attackers information that helps them **infer details about the model**.

---

# ⚡ 30-Second Revision

1. **Training-data poisoning →** Attacker corrupts training data to change model behavior.
    
2. **Adversarial input →** Carefully modified input causes **misclassification**.
    
3. **Model inversion →** Analyze outputs to **infer training-data information**.
    
4. **Model extraction →** Use input/output pairs to **replicate the model**.
    
5. **Prompt injection →** Malicious instructions manipulate an **LLM's behavior**.
    
6. **Defenses →** Least privilege + encryption + restricted model access + input validation.
    
7. **Adversarial training →** Train with adversarial inputs to improve resistance.
    
8. **Retraining →** Frequent retraining can help undo damage from corrupted training data.
    
9. **Model Monitor →** Production monitoring for **model/data quality, drift, and anomalies**.
    
10. **Data quality monitoring →** Requires **data capture** + baseline comparison.
    
11. **Model performance monitoring →** Uses **labeled data** to evaluate predictions.
    
12. **CloudWatch →** Receives monitoring information and can alert when **thresholds are exceeded**.