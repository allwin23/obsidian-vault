## Unknow  THINGS 
**AWS Glue DataBrew / SageMaker Data Wrangler** is about **preparing and transforming data**. It isn't the ML model itself and it doesn't "serve" the training/validation/test sets.

For **SageMaker Data Wrangler**, the workflow is roughly:

```
Raw Data
   ↓
SageMaker Data Wrangler
   ↓
Clean / transform / analyze
   ↓
Prepared dataset
   ↓
Split into
 ┌────────────┬──────────────┬────────────┐
 ↓            ↓              ↓
Training   Validation       Test
 ↓            ↓              ↓
Model       Tune model    Final evaluation
```


Provisioned Throughput = you reserve dedicated model capacity for your application.

### Exam memory trick

> **Supervised = labeled only**  
> **Unsupervised = unlabeled only**  
> **Semi-supervised = small labeled + large unlabeled**

Pseudo-labeling → Propagation → Spreading → Consistency → Co-training
|Service|Main purpose|Think|
|---|---|---|
|**Audit Manager**|Compliance & audit evidence|🧾 **"Are we compliant?"**|
|**Amazon Inspector**|Vulnerability detection|🛡️ **"What's vulnerable?"**|
|**CloudTrail**|Activity/API logging|🕵️ **"Who did what?"**|

| Concept              | What's happening?                               | Think                                     |
| -------------------- | ----------------------------------------------- | ----------------------------------------- |
| **Prompt leaking**   | Hidden system instructions are exposed          | 🔓 **Steal the prompt**                   |
| **Prompt poisoning** | Malicious instructions/data influence the model | ☠️ **Poison the input/context**           |
| Amazon Q capability  | Who / what?                                     | Main purpose                              |
| **Q Business**       | 👨‍💼 Employees                                 | Enterprise knowledge & business questions |
| **Q Developer**      | 👨‍💻 Developers                                | Code, development, AWS, debugging         |
| **Q in AWS**         | ☁️ AWS users                                    | AWS help/troubleshooting                  |
| **Q in QuickSight**  | 📊 Analysts/business users                      | Natural-language BI & analytics           |
| **Q in Connect**     | 🎧 Customer-service agents                      | Customer-service assistance               |



||**High Bias**|**High Variance**|
|---|---|---|
|Model|Too simple|Too complex|
|Training performance|Poor|Very good|
|Test performance|Poor|Poor|
|Problem|Underfitting|Overfitting|
|Learns noise?|❌ Usually not enough pattern|✅ Yes|
|Sensitivity to training data|Low|High|

| Bias               | What is wrong?                                         | Easy memory       |
| ------------------ | ------------------------------------------------------ | ----------------- |
| **Algorithmic**    | Model/algorithm produces systematic unfairness         | 🤖 Algorithm      |
| **Sampling**       | Sample doesn't represent population                    | 👥 Sample         |
| **Selection**      | Data-selection process creates systematic distortion   | 🎯 Selection      |
| **Measurement**    | Feature/label measurement is systematically inaccurate | 📏 Measurement    |
| **Label**          | Training labels themselves are biased                  | 🏷️ Labels        |
| **Historical**     | Historical data reflects existing inequalities         | 📜 History        |
| **Representation** | Some groups are inadequately represented               | 👥 Representation |


| If question asks...                          | Think                       |
| -------------------------------------------- | --------------------------- |
| **Detect bias in ML data/model**             | 🟢 **SageMaker Clarify**    |
| **Explain why model made prediction**        | 🟢 **SageMaker Clarify**    |
| **Feature importance / SHAP**                | 🟢 **SageMaker Clarify**    |
| Monitor model/data after deployment          | **SageMaker Model Monitor** |
| Build ML model                               | **SageMaker**               |
| Prepare/transform ML data                    | **SageMaker Data Wrangler** |
| Collect compliance evidence                  | **AWS Audit Manager**       |
| Find infrastructure/software vulnerabilities | **Amazon Inspector**        |
| Record who performed AWS API actions         | **CloudTrail**              |

|Metric|Main question|Use when|
|---|---|---|
|**Accuracy**|How many predictions are correct?|Balanced classes|
|**Precision**|Of predicted positives, how many are actually positive?|False positives matter|
|**Recall**|Of actual positives, how many did we find?|False negatives matter|
|**F1**|How well do precision & recall balance?|Both matter / imbalance|
|**MAE**|How far off are predictions on average?|Regression|
|**MSE**|How large are squared errors?|Penalize large errors|
|**RMSE**|How large are errors, emphasizing big errors?|Regression + large errors matter|
|**R²**|How much target variation does model explain?|Regression|
|**ROC-AUC**|How well can model distinguish classes?|Binary classification / ranking|


## What is Data Lineage?

> **Data lineage = the history and journey of data from its original source to its final destination.**

It tells you:

**Where did this data come from? → What happened to it? → Where did it go?**


| Workload                       | Think                     |
| ------------------------------ | ------------------------- |
| Normal application/server      | **General-purpose EC2**   |
| CPU-intensive workload         | **Compute optimized (C)** |
| ML model **training**          | **Trainium / GPU**        |
| ML model **inference**         | **Inferentia / GPU**      |
| Very demanding GPU ML training | **P-series GPU**          |
| GPU inference / graphics       | **G-series GPU**          |
BERT is a pretrained, Transformer encoder-based language model that learns bidirectional contextual representations and can be fine-tuned for NLP tasks such as classification, NER, and question answering.


**Exploratory Data Analysis (EDA)**

The company is in the Exploratory Data Analysis (EDA) phase, which involves examining the data through statistical summaries and visualizations to identify patterns, detect anomalies, and form


||**SageMaker JumpStart**|**SageMaker Ground Truth**|
|---|---|---|
|Main purpose|Find/use models|Label data|
|Focus|**Models**|**Data**|
|Provides|Pretrained/FMs/algorithms|Labeled datasets|
|Human labeling?|❌|✅|
|Helps with|Model development|Data preparation|
|Think|🚀 **START WITH A MODEL**|🏷️ **CREATE LABELS**|


**SageMaker Model Monitor = detects problems automatically.**  
**SageMaker Model Dashboard = gives you a central place to view model information and monitoring results.**



model input is learned by the outputs then it is inversion 
extracted ouptu is used to train osme other model is output 


ROUGE → summarization.**
    
9. **BLEU → machine translation.**
    
10. **GLUE → generalization across language tasks.**
    
11. **SuperGLUE → harder language tasks, including reasoning/reading comprehension.**
    
12. **MMLU → knowledge + problem solving across many subjects.**
    
13. **BIG-bench → broad, challenging, diverse tasks.**
    
14. **HELM → holistic evaluation + multiple metrics + transparency.**
    
15. **Human evaluation → manually compare/judge model responses.**
    
16. **SageMaker Clarify → evaluation jobs for SageMaker JumpStart text FMs.**
    
17. **Bedrock evaluation → generated response vs human reference + BERTScore.**
    
18. **Faithfulness/hallucinations → Bedrock evaluation capability described in this les

> **Intrinsic = explainable by design**  
> **Post-hoc = explain it afterward**

And connect this with what we just discussed:

**SHAP / LIME / PDP → post-hoc explainability**

- **SHAP** → usually local explanation: _Why THIS prediction?_
- **PDP** → global explanation: _How does this feature affect predictions overall?_

So don't confuse **local/global** with **intrinsic/post-hoc**:

> **Local vs Global = scope of explanation**  
> **Intrinsic vs Post-hoc = how/when explanation is obtained**



# ⚡ 30-Second Revision

**1. Three training elements →** **Pre-training + Fine-tuning + Continuous pre-training.**

**2. Pre-training →** huge unstructured data + **self-supervised learning** + general capabilities.

**3. Fine-tuning →** labeled examples + **supervised learning** + task-specific adaptation.

**4. Full fine-tuning →** **every parameter updated**.

**5. PEFT →** freeze/preserve most parameters + train small task-specific components.

**6. LoRA →** PEFT technique using **trainable low-rank matrices**.

**7. PEFT/LoRA →** modify **weights**, not representations.

**8. ReFT →** freeze base model + intervene on **hidden representations**.

**9. Single-task fine-tuning →** specialization but possible **catastrophic forgetting**.

**10. Multitask fine-tuning →** multiple tasks + labeled examples → instruction-tuned model.

**11. Domain adaptation →** specialized domain language/data + limited domain-specific data.

**12. RLHF →** reinforcement learning + human feedback → human-preference alignment.

**13. Full fine-tuning memory →** parameters + optimizer + gradients + activations + temporary memory.

**14. Core distinction →** **Pre-training creates general capabilities; fine-tuning adapts them; PEFT reduces adaptation cost; ReFT works on representations.**
||**AWS Artifact**|**AWS Audit Manager**|
|---|---|---|
|Main purpose|Access **AWS compliance documents**|**Collect and organize evidence** for your own audits|
|Focus|AWS's compliance|**Your AWS environment's compliance**|
|Provides|SOC reports, ISO certificates, PCI reports, etc.|Evidence from your AWS services|
|Question it answers|**“What compliance certifications does AWS have?”**|**“Can I prove my environment meets this compliance requirement?”**|
|Example|Download AWS SOC 2 report|Collect CloudTrail/configuration evidence for an audit|