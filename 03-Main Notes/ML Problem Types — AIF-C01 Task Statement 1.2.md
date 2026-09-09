

## 🎯 Exam Essentials

The **first question** to ask when identifying an ML problem is:

> **Does the training data have labels/target values?**

### 1. Supervised Learning

- Training data contains **features + known target/label**.
    
- The model learns the relationship between inputs and the known output.
    
- Two major problem types:
    
    - **Classification** → target is a category.
        
    - **Regression** → target is a continuous numerical value.
        

**Exam trigger:**

> "Historical data contains the correct answer/target for each example" → **Supervised learning**

---

### 2. Classification

Classification predicts a **discrete category/class**.

#### Binary Classification

Exactly **two mutually exclusive classes**.

Examples:

- Fraud / Not fraud
    
- Disease / No disease
    
- Spam / Not spam
    
- Fish / Not fish
    

**Exam trigger:**

> "Yes or no", "fraud or legitimate", "disease or healthy" → **Binary classification**

#### Multiclass Classification

Predicts **one class from several predefined classes**.

Example:

A document is classified as:

- Finance
    
- Politics
    
- Religion
    
- Technology
    

**Exam trigger:**

> "Choose one of several predefined categories" → **Multiclass classification**

⚠️ **Important:** Don't confuse multiclass classification with clustering. In multiclass classification, the categories are **known/predefined** during supervised training.

---

### 3. Regression

Regression predicts a **continuous numerical value**.

Examples:

- House price → $350,000
    
- Temperature → 31.5°C
    
- Sales → 12,450 units
    
- Height → 175.3 cm
    

**Exam trigger:**

> "Predict the amount, price, temperature, revenue, demand, or other continuous number" → **Regression**

### Linear Regression

Predicts a continuous value using a linear relationship between inputs and output.

- **Simple linear regression:** one independent variable.
    
    - Example: weight → height
        
- **Multiple linear regression:** multiple independent variables.
    
    - Example: bedrooms + bathrooms + square footage → house price
        

---

### Logistic Regression ⚠️

Despite its name, **logistic regression is generally used for classification**, not ordinary continuous-value regression.

- Produces a value between **0 and 1** representing the estimated probability of an outcome.
    
- Commonly used for **binary classification**.
    
- Example:
    
    - Fraud probability = 0.92
        
    - Not fraud probability = 0.08
        

**Exam trigger:**

> "Predict probability of fraud/disease/churn occurring" → **Logistic regression**

---

### 4. Unsupervised Learning

- Training data contains **features but no known target labels**.
    
- The model tries to discover patterns or structure by itself.
    
- Two important problem types:
    

**Clustering**  
→ Find **groups of similar data**.

**Anomaly detection**  
→ Find **unusual/outlier data points**.

**Exam trigger:**

> "No labels and discover natural groups" → **Clustering**

> "Find unusual/rare/deviant events" → **Anomaly detection**

---

### 5. Clustering

- Groups data points based on **similarity**.
    
- The groups are called **clusters**.
    
- Example: Segment customers based on purchasing behavior into different groups.
    

The key idea:

> **Similar within a group, different between groups.**

**Exam trigger:**

> "Customer segmentation without predefined categories" → **Clustering**

---

### 6. Anomaly Detection

- Identifies **rare or unusual observations** that significantly differ from normal data.
    
- Examples:
    
    - Detecting failed sensors
        
    - Detecting unusual transactions
        
    - Identifying potential medical errors
        

**Exam trigger:**

> "Find outliers / unusual behavior / abnormal observations" → **Anomaly detection**

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Feature**|Input attribute used by an ML model|
|**Label/Target**|Known expected output used in supervised learning|
|**Supervised learning**|Learning from labeled data|
|**Unsupervised learning**|Finding patterns in unlabeled data|
|**Classification**|Predicting a discrete category|
|**Binary classification**|Classification between two classes|
|**Multiclass classification**|Classification among multiple predefined classes|
|**Regression**|Predicting a continuous numerical value|
|**Linear regression**|Regression using a linear relationship|
|**Logistic regression**|Estimates probability of an outcome; commonly used for binary classification|
|**Clustering**|Grouping similar unlabeled data|
|**Anomaly detection**|Finding unusual/outlier observations|
|**Independent variable**|Input/predictor used to make a prediction|
|**Dependent variable**|Target/output being predicted|

---

## ⚔️ Important Comparisons

### The AIF-C01 Decision Tree

Use this mental flow:

```text
                 Do you have labels?
                    /          \
                  YES           NO
                   ↓             ↓
              SUPERVISED     UNSUPERVISED
                /     \          /      \
               /       \        /        \
        Category?    Number?  Groups?   Outliers?
           ↓            ↓       ↓          ↓
    CLASSIFICATION   REGRESSION CLUSTERING ANOMALY
       /      \
    2 classes  >2 classes
       ↓          ↓
    BINARY     MULTICLASS
```

This is **extremely useful for AIF-C01 scenario questions**.

---

### Classification vs Regression

||Classification|Regression|
|---|---|---|
|Output|Category|Continuous number|
|Example|Fraud / Not fraud|House price|
|Learning|Supervised|Supervised|
|Target|Discrete|Continuous|
|Key question|"Which class?"|"What value?"|

---

### Classification vs Clustering

||Classification|Clustering|
|---|---|---|
|Learning|Supervised|Unsupervised|
|Labels|✅ Required|❌ Not required|
|Categories|Known beforehand|Discovered from data|
|Example|Classify email as spam/not spam|Group customers by behavior|

**This is a very common exam distinction.**

---

### Linear vs Logistic Regression

||Linear Regression|Logistic Regression|
|---|---|---|
|Main use|Predict continuous value|Estimate probability/class|
|Output|Numerical value|0–1 probability|
|Example|House price|Fraud probability|
|Typical problem|Regression|Classification|

---

## 🧠 Exam Traps

- **Trap:** "Regression always means predicting a number, so logistic regression is regression."
    
    - **Correct:** Although named regression, **logistic regression is commonly used for classification**, especially binary classification.
        
- **Trap:** Classification means grouping unlabeled customers into categories.
    
    - **Correct:** If categories aren't predefined and the model discovers groups, that's **clustering**.
        
- **Trap:** Multiclass classification means creating groups automatically.
    
    - **Correct:** Multiclass classification uses **predefined classes**.
        
- **Trap:** Binary classification means predicting a number between 0 and 1.
    
    - **Correct:** The **final task** is choosing between two classes. A model such as logistic regression may produce a probability between 0 and 1 before converting it into a class.
        
- **Trap:** Anomaly detection means classifying every data point into a predefined category.
    
    - **Correct:** Anomaly detection focuses on identifying **unusual/outlier observations**.
        
- **Trap:** Clustering requires labeled examples showing the correct group for each customer.
    
    - **Correct:** Clustering is **unsupervised** and discovers groups from unlabeled data.
        

---

## 📝 Exam Questions

### Question 1

A bank has historical transactions labeled **fraud** or **not fraud**. It wants to train a model to classify future transactions.

What type of ML problem is this?

A. Clustering  
B. Binary classification  
C. Regression  
D. Anomaly detection

**Answer:** B

**Why:** There are **two predefined labels**, fraud and not fraud, making this supervised binary classification.

---

### Question 2

A retailer wants to predict the exact dollar amount a customer will spend next month using historical customer information.

Which ML problem is MOST appropriate?

A. Binary classification  
B. Multiclass classification  
C. Regression  
D. Clustering

**Answer:** C

**Why:** The target is a **continuous numerical value**, so this is regression.

---

### Question 3

A company has customer purchase histories but has not assigned customers to any categories. It wants the ML system to discover naturally occurring customer groups.

Which approach is MOST appropriate?

A. Binary classification  
B. Regression  
C. Clustering  
D. Logistic regression

**Answer:** C

**Why:** There are **no predefined labels**, and the goal is to discover groups → clustering.

---

### Question 4

A healthcare organization has diagnostic data labeled with whether each patient has a particular disease. It wants to predict whether new patients have the disease.

What type of ML problem is this?

A. Binary classification  
B. Clustering  
C. Regression  
D. Anomaly detection

**Answer:** A

**Why:** The target has two classes: **disease / no disease**.

---

### Question 5

A company wants to categorize support tickets into one of five predefined categories: billing, technical support, account access, shipping, and other.

Which ML problem is this?

A. Binary classification  
B. Multiclass classification  
C. Clustering  
D. Regression

**Answer:** B

**Why:** The model chooses among **multiple predefined categories**, making it multiclass classification.

---

### Question 6

An oil company collects temperature readings from equipment. It wants to identify readings that are significantly different from normal operating behavior.

Which ML problem is MOST appropriate?

A. Multiclass classification  
B. Regression  
C. Clustering  
D. Anomaly detection

**Answer:** D

**Why:** Identifying observations that significantly differ from normal behavior is **anomaly detection**.

---

### Question 7

A company wants to estimate the probability that a customer will cancel their subscription based on their usage history, account age, and support interactions.

Which approach is MOST appropriate?

A. Logistic regression  
B. Clustering  
C. Linear regression  
D. Multiclass classification

**Answer:** A

**Why:** Logistic regression can estimate the **probability of an outcome**, such as customer churn, and is commonly used for binary classification.

---

### Question 8

A real estate company wants to predict house prices using square footage, number of bedrooms, number of bathrooms, and location.

Which type of ML problem is this?

A. Binary classification  
B. Anomaly detection  
C. Regression  
D. Clustering

**Answer:** C

**Why:** House price is a **continuous numerical target**, making this a regression problem.

---

## ⚡ 30-Second Revision

- **Labels present → Supervised learning.**
    
- **No labels → Unsupervised learning.**
    
- **Supervised + category → Classification.**
    
- **2 categories → Binary classification.**
    
- **Several predefined categories → Multiclass classification.**
    
- **Supervised + continuous number → Regression.**
    
- **Linear regression → predicts continuous values.**
    
- **Logistic regression → probability of an outcome; commonly binary classification.**
    
- **Unsupervised + discover groups → Clustering.**
    
- **Unsupervised + find unusual/outlier data → Anomaly detection.**
    

### 🔥 One-line memory trick

> **Known category = Classification | Known number = Regression | Unknown groups = Clustering | Weird/outlier = Anomaly detection**