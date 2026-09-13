# ML Model Evaluation Metrics & Business Metrics

## 🎯 Exam Essentials

### 1. False Positive Rate (FPR)

Measures how often the model **incorrectly predicts positive** among cases that are actually negative.

FPR=FPFP+TNFPR = \frac{FP}{FP+TN}

**Mental shortcut:**

> “Of all actual negatives, how many did we falsely call positive?”

Example: Of all images that are **not fish**, how many were incorrectly classified as fish?

---

### 2. True Negative Rate (TNR / Specificity)

Measures how often the model correctly identifies negative cases among all actual negatives.

TNR=TNTN+FPTNR = \frac{TN}{TN+FP}

Also called **specificity**.

**Mental shortcut:**

> “Of all actual negatives, how many did we correctly reject?”

Important relationship:

TNR=1−FPRTNR = 1-FPR

---

### 3. Classification Threshold

A probability-producing classifier can convert a probability into a discrete class using a **threshold**.

Example:

- Model predicts `fish probability = 0.72`
    
- Threshold = `0.60`
    
- Prediction → **Fish**
    

If threshold increases:

**Fewer positive predictions → generally fewer FP but more FN.**

If threshold decreases:

**More positive predictions → generally more TP but more FP.**

⚠️ The threshold is a **decision setting**, not something that changes the underlying model's learned parameters.

---

### 4. ROC Curve and AUC

The **ROC curve** plots:

- **True Positive Rate (TPR / Recall)** on the Y-axis
    
- **False Positive Rate (FPR)** on the X-axis
    

across different classification thresholds.

**AUC = Area Under the ROC Curve.**

AUC provides an aggregate measure of how well a binary classifier separates the two classes **across thresholds**.

|AUC|Interpretation|
|--:|---|
|1.0|Perfect discrimination|
|0.5|Approximately random discrimination|
|< 0.5|Worse than random; may indicate reversed ranking|

⚠️ **Exam precision:** AUC is better described as a measure of **ranking/discrimination ability**, not simply “accuracy.”

**Key trigger:**

> “Evaluate a probability-based binary classifier across different thresholds” → **ROC/AUC**

---

### 5. MSE — Mean Squared Error

Used for **regression**.

MSE=1n∑(ypred−yactual)2MSE = \frac{1}{n}\sum(y_{pred}-y_{actual})^2

Properties:

- Always ≥ 0
    
- Lower is generally better
    
- Squares errors
    
- Therefore **large errors/outliers have disproportionately high impact**
    

Example:

Actual = 100  
Predicted = 110  
Error = 10  
Squared error = 100

---

### 6. RMSE — Root Mean Squared Error

RMSE=MSERMSE = \sqrt{MSE}

The major exam advantage:

> **RMSE is expressed in the same units as the target variable.**

If predicting height in inches:

- MSE → square inches
    
- RMSE → inches
    

Like MSE, RMSE gives **more weight to large errors**.

---

### 7. MAE — Mean Absolute Error

MAE=1n∑∣ypred−yactual∣MAE = \frac{1}{n}\sum|y_{pred}-y_{actual}|

Instead of squaring errors, MAE uses their absolute values.

Therefore:

- Lower MAE → generally better
    
- Same units as target
    
- **Less sensitive to outliers than MSE/RMSE**
    

**Critical distinction:**

> MSE/RMSE → emphasize large errors  
> MAE → treats errors proportionally through absolute magnitude

---

## 🔑 Key Terms

|Term|Meaning|Main use|
|---|---|---|
|**FPR**|FP / (FP + TN)|Measures false positives among actual negatives|
|**TNR / Specificity**|TN / (TN + FP)|Measures correctly identified negatives|
|**Threshold**|Probability cutoff used for class decision|Binary classification|
|**TPR / Recall / Sensitivity**|TP / (TP + FN)|Measures actual positives detected|
|**ROC curve**|TPR vs FPR across thresholds|Binary classification|
|**AUC**|Area under ROC curve|Overall discrimination across thresholds|
|**MSE**|Average squared error|Regression|
|**RMSE**|√MSE|Regression, same units as target|
|**MAE**|Average absolute error|Regression, less outlier-sensitive|
|**Business metric**|Measures business value/outcome|ML project success|
|**Cost allocation tag**|Tag assigned to AWS resources for cost tracking|Cost attribution|

---

## ⚔️ Important Comparisons

### Classification metrics

|Metric|Formula|Main question|
|---|---|---|
|**Precision**|TP / (TP + FP)|“When I predicted positive, was I right?”|
|**Recall / TPR**|TP / (TP + FN)|“How many actual positives did I catch?”|
|**FPR**|FP / (FP + TN)|“How many actual negatives did I incorrectly flag?”|
|**TNR / Specificity**|TN / (TN + FP)|“How many actual negatives did I correctly reject?”|
|**AUC**|Area under ROC|“How well does the classifier discriminate across thresholds?”|

Notice:

**Recall uses actual positives as its denominator.**  
**FPR uses actual negatives as its denominator.**

That's a very common exam trap.

---

### Regression metrics

|Metric|Outlier sensitivity|Same units as target?|
|---|---|---|
|**MSE**|High|❌|
|**RMSE**|High|✅|
|**MAE**|Lower|✅|

---

### Model metrics vs business metrics

|Model metric|Business metric|
|---|---|
|Precision|Customer retention|
|Recall|Fraud losses avoided|
|RMSE|Revenue impact|
|AUC|Conversion improvement|
|FPR|Cost from unnecessary investigations|
|—|AWS operating cost|
|—|ROI|

A model can have excellent ML metrics but still be a **bad business solution** if its operating cost exceeds its value.

---

## 💰 Business Metrics, Cost & ROI

The ML lifecycle doesn't end at:

> **“The model has good accuracy.”**

You need to ask:

1. Did the model achieve the original business objective?
    
2. What value did it create?
    
3. What did it cost to build?
    
4. What does it cost to operate?
    
5. What risks/errors does it introduce?
    
6. What is the resulting ROI?
    

Possible business metrics:

- Cost reduction
    
- Increased sales
    
- Increased users
    
- Improved customer satisfaction
    
- Reduced fraud losses
    
- Reduced operational time
    

### AWS Cost Allocation Tags

You can tag AWS resources associated with an ML project, for example:

`MLProject = FraudDetection`

Then use **AWS Cost Explorer** to analyze the AWS costs associated with those tagged resources.

**Exam trigger:**

> “Management wants to determine how much AWS infrastructure a particular ML project actually costs.”

→ **Cost allocation tags + Cost Explorer**

---

# 🧠 Exam Traps

### Trap 1 — FPR vs Recall

If the question says:

> “Of the images that were actually NOT fish, how many were incorrectly classified as fish?”

That's **FPR**, not recall.

---

### Trap 2 — TNR vs Precision

If it asks:

> “Of all actual negative cases, how many were correctly identified?”

→ **TNR / Specificity**

If it asks:

> “Of all cases predicted positive, how many were actually positive?”

→ **Precision**

---

### Trap 3 — AUC ≠ Accuracy

AUC evaluates discrimination across classification thresholds. It isn't simply the percentage of correct predictions at one chosen threshold.

---

### Trap 4 — MSE vs RMSE

Don't choose MSE just because the question says “regression.”

If the question emphasizes:

> “metric should be expressed in the same units as the predicted variable”

→ **RMSE or MAE**

If it emphasizes:

> “strongly penalize large errors/outliers”

→ **MSE/RMSE**

---

### Trap 5 — MAE isn't “better” universally

MAE is preferable when large errors **shouldn't receive disproportionate weight**.

MSE/RMSE may be preferable when large errors are particularly important to penalize.

---

### Trap 6 — Model metric ≠ business success

A model's technical performance does not automatically demonstrate business value.

The final evaluation should connect:

**Model performance → business outcome → cost → ROI**

---

# 📝 Exam Questions

### Q1 — Very Hard

A fraud classifier produces probabilities. The security team wants to evaluate how well the model separates fraudulent from legitimate transactions **without committing to one particular probability cutoff**. Which metric is most appropriate?

A. F1 score  
B. ROC-AUC  
C. Specificity  
D. Precision

**Answer: B — ROC-AUC**

**Why:** ROC-AUC evaluates discrimination across the range of classification thresholds rather than evaluating performance at one fixed threshold.

---

### Q2 — Exam Trap

A medical screening model evaluates 10,000 patients who do **not** have the disease. The model incorrectly flags 300 of them as positive. Which metric directly measures this behavior?

A. False negative rate  
B. False positive rate  
C. Positive predictive value  
D. True positive rate

**Answer: B — False Positive Rate**

**Why:** The denominator consists of actual negatives:

FPR=FPFP+TNFPR=\frac{FP}{FP+TN}

The question specifically asks about incorrectly identifying actual negatives as positive.

---

### Q3 — Hard

A regression model predicts delivery time in minutes. Two candidate metrics are MSE and RMSE. The operations team wants the metric to be directly interpretable as an error measured in **minutes**, while retaining greater sensitivity to unusually large errors. Which should they use?

A. MAE  
B. MSE  
C. RMSE  
D. AUC

**Answer: C — RMSE**

**Why:** RMSE is the square root of MSE, so it retains MSE's sensitivity to large errors while returning to the target's original units.

---

### Q4 — Very Hard

A binary classifier currently uses a probability threshold of 0.50. The business raises the threshold to 0.80. Assuming predictions otherwise remain comparable, which change is generally expected?

A. More observations will be classified positive, increasing both FP and TP  
B. Fewer observations will be classified positive, generally reducing FP while increasing FN  
C. Fewer observations will be classified positive, generally reducing FN while increasing TP  
D. The model's learned parameters will change, reducing both FP and FN

**Answer: B**

**Why:** A higher threshold makes positive classification harder. This generally reduces positive predictions, which tends to reduce FP but increase FN.

---

### Q5 — Exam Trap

A company chooses MAE instead of RMSE for a forecasting model because a few extreme prediction errors should **not dominate the evaluation metric**. Which property explains this choice?

A. MAE converts errors into probabilities before averaging  
B. MAE uses absolute errors rather than squared errors  
C. MAE evaluates classification performance independently of thresholds  
D. MAE removes extreme observations before evaluation

**Answer: B**

**Why:** Squaring causes large errors to grow disproportionately. Absolute error does not amplify them in the same way.

---

### Q6 — Hard

A model correctly identifies 9,700 legitimate transactions but incorrectly labels 300 legitimate transactions as fraudulent. The fraud team wants to measure the proportion of **actual legitimate transactions that were incorrectly flagged**. Which metric should they calculate?

A. Precision  
B. Recall  
C. False positive rate  
D. True positive rate

**Answer: C — False Positive Rate**

**Why:** The question conditions on the actual negative population. FPR measures incorrect positive predictions among actual negatives.

---

### Q7 — Very Hard

An ML model has excellent ROC-AUC and acceptable recall in production. However, after deployment, the company discovers that the model's AWS inference and monitoring costs exceed the financial benefit produced by the automation. Which conclusion is most appropriate?

A. The model should be considered successful because ROC-AUC is high  
B. The model should be considered unsuccessful because technical model metrics are irrelevant to business evaluation  
C. The model has strong predictive performance but may fail the business objective because its total cost outweighs its value  
D. The model should automatically be retrained until the AWS costs decrease

**Answer: C**

**Why:** Technical model quality and business success are different dimensions. A strong model can still have negative ROI.

---

### Q8 — Exam Trap

A project manager wants to determine the actual AWS expenditure attributable to a specific ML pipeline after it has been deployed. The team has tagged the AWS resources used by that project consistently. Which AWS capability is most directly useful?

A. AWS CloudTrail  
B. Amazon CloudWatch  
C. AWS Cost Explorer  
D. AWS Config

**Answer: C — AWS Cost Explorer**

**Why:** Cost allocation tags allow costs to be associated with resources/projects, and Cost Explorer can analyze those AWS charges.

---

### Q9 — Extremely Difficult

Consider two binary classifiers evaluated across all possible probability thresholds. Model A has an AUC of 0.91, while Model B has an AUC of 0.74. However, at the company's chosen operating threshold, Model B happens to have better precision.

Which statement is most accurate?

A. Model B must have better overall classification performance because its precision is higher at the operating threshold  
B. Model A has stronger overall discrimination across thresholds, although Model B may be preferable at the chosen operating point  
C. Model A must have higher recall because AUC is always numerically greater than recall  
D. Model B must have lower FPR because precision is directly equivalent to specificity

**Answer: B**

**Why:** AUC summarizes discrimination across thresholds, while precision evaluates performance at a particular prediction setup. A model can have higher AUC yet be less attractive at a specific operating threshold.

---

### Q10 — Exam-Trap / Business Reasoning

A company deploys a regression model that reduces average prediction error substantially. After deployment, however, the company discovers that the model requires expensive infrastructure and produces only a small reduction in operational costs.

Which evaluation is most appropriate?

A. The model is successful because lower prediction error proves positive ROI  
B. The model is unsuccessful because regression metrics should never be used for business decisions  
C. The technical improvement should be evaluated together with implementation/operating costs and measurable business outcomes  
D. The company should replace RMSE with AUC to determine whether the model is economically viable

**Answer: C**

**Why:** ML evaluation has two levels: **technical model performance** and **business value**. ROI requires comparing measurable benefits against actual costs.

---

# ⚡ 30-Second Revision

1. **FPR = FP / (FP + TN)** → false alarms among actual negatives.
    
2. **TNR = TN / (TN + FP)** → correctly identified actual negatives.
    
3. **TNR = 1 − FPR.**
    
4. **Higher classification threshold** → generally fewer FP, more FN.
    
5. **ROC** plots TPR against FPR across thresholds.
    
6. **AUC** measures discrimination across thresholds; **0.5 ≈ random, 1.0 = perfect**.
    
7. **MSE/RMSE** emphasize large errors; **MAE** is less sensitive to outliers.
    
8. **RMSE** has the same units as the target; MSE does not.
    
9. **Technical model quality ≠ business success.**
    
10. **Business success = measurable outcome + costs + risks → ROI.**
    
11. **Cost allocation tags + Cost Explorer** → attribute AWS costs to ML projects.