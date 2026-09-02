## 🎯 Exam Essentials

- **Machine Learning (ML):** A type of AI where algorithms learn patterns from data to make predictions or produce outputs **without being explicitly programmed for every outcome**.
- **Features:** Input characteristics used by an ML model to make predictions.
    - Example: In a house-price model → size, number of bedrooms, location.
    - Think **columns in structured data** or extracted characteristics from unstructured data.
- **Training:** The process of providing data to an ML algorithm and adjusting its internal **parameters** so that its outputs become closer to the expected results.
- **Inference:** Using a **trained model** on new, previously unseen data to generate predictions or outputs.
    - **Exam trigger:** "Use the trained model to make predictions on new data" → **Inference**
- **Model parameters:** Internal values adjusted during training to improve the model's predictions.
- **Algorithm vs. model:**
    - **Algorithm** → mathematical method/procedure used to learn.
    - **Model** → the result produced after training the algorithm on data.

### Data Types

- **Structured data:** Organized into rows and columns with a defined schema.
    - Examples: relational database tables, CSV files.
    - Common AWS services: **Amazon RDS, Amazon Redshift**
    - **Exam trigger:** "Rows and columns / relational tables / SQL" → **Structured data**
- **Semi-structured data:** Has some organization but doesn't require a fixed tabular schema.
    - Example: **JSON**
    - AWS examples: **Amazon DynamoDB, Amazon DocumentDB**
    - **Exam trigger:** "JSON / key-value pairs / flexible attributes" → **Semi-structured data**
- **Unstructured data:** Doesn't follow a predefined tabular structure.
    - Examples: images, videos, text documents, social media posts.
    - Often stored as objects in **Amazon S3**.
    - **Exam trigger:** "Images, videos, documents, free-form text" → **Unstructured data**
- **Time-series data:** Data points recorded sequentially with timestamps.
    - Useful for identifying trends and predicting future behavior.
    - Example: CPU utilization measured every minute.
    - **Exam trigger:** "Timestamped measurements / predict future trends" → **Time-series data**

### Amazon S3 and ML

- **Amazon S3:** Object storage commonly used to store datasets for ML workloads.
- S3 can store structured, semi-structured, and unstructured data.
- Don't confuse **where data is stored** with **what type of data it is**.

### Linear Regression

- **Linear regression:** A supervised ML technique used to predict a **continuous numerical value**.
- Basic relationship: `y = mx + b`
    - `m` = slope
    - `b` = intercept
    - `x` = input/independent variable
    - `y` = predicted/dependent variable
- Training adjusts parameters to minimize prediction error.
- Example: Predict **height from weight**.

**Exam trigger:** "Predict a numerical/continuous value" → **Regression**

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Machine Learning**|Learning patterns from data to make predictions/outputs|
|**Feature**|Input characteristic used by an ML model|
|**Training**|Learning model parameters from data|
|**Inference**|Using a trained model to generate predictions|
|**Model**|Trained representation of learned patterns|
|**Parameter**|Internal model value adjusted during training|
|**Structured data**|Data organized into predefined rows/columns|
|**Semi-structured data**|Data with flexible structure, such as JSON|
|**Unstructured data**|Data without a predefined tabular structure|
|**Time-series data**|Sequential data associated with timestamps|
|**Linear regression**|Predicts a continuous numerical value|
|**Tokenization**|Breaking text into smaller units such as words or phrases|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Structured data**|Tables, CSV, relational databases|Fixed rows/columns/schema|
|**Semi-structured data**|JSON, flexible records|Has structure but flexible attributes|
|**Unstructured data**|Images, video, documents, free-form text|No predefined tabular schema|
|**Training**|Building/learning the model|Model learns from data|
|**Inference**|Applying the trained model|Model produces predictions on new data|
|**Algorithm**|Defining how learning occurs|Mathematical procedure|
|**Model**|Making predictions|Trained result of the algorithm|

---

## 🧠 Exam Traps

- **Trap:** Training and inference are the same thing.
    - **Correct:** **Training** learns model parameters; **inference** uses the trained model to make predictions.
- **Trap:** S3 means the data is unstructured.
    - **Correct:** **S3 is storage**, not a data classification. Structured, semi-structured, and unstructured data can all be stored in S3.
- **Trap:** JSON is structured data because it has a defined format.
    - **Correct:** JSON is generally classified as **semi-structured** because records can have varying or missing attributes.
- **Trap:** Linear regression is primarily for predicting categories.
    - **Correct:** Linear regression predicts a **continuous numerical value**. Classification is used for categories.
- **Trap:** Features are the expected outputs.
    - **Correct:** **Features are inputs** used to make predictions. The expected output is the target/label in supervised learning.

---

## 📝 Exam Questions

### Question 1

A company has trained an ML model to predict whether a transaction is fraudulent. The company now sends a newly received transaction to the trained model to determine whether it is fraudulent.

What ML process is being performed?

A. Training  
B. Feature engineering  
C. Inference  
D. Parameter optimization

**Answer:** C

**Why:** **Inference** is using a trained model to generate predictions from new data.

---

### Question 2

A company stores customer information in a database using predefined rows and columns and queries the data using SQL.

What type of data is this?

A. Unstructured  
B. Semi-structured  
C. Structured  
D. Time-series

**Answer:** C

**Why:** Predefined rows, columns, and SQL-based relational data indicate **structured data**.

---

### Question 3

An application stores customer records as JSON objects. Different records can contain different attributes.

How should this data generally be classified?

A. Structured  
B. Semi-structured  
C. Unstructured  
D. Time-series

**Answer:** B

**Why:** JSON uses a recognizable structure but allows flexible or varying attributes, making it **semi-structured**.

---

### Question 4

A company wants to predict next week's CPU utilization using measurements collected every minute, with each measurement associated with a timestamp.

Which type of data is most appropriate for this task?

A. Structured data  
B. Semi-structured data  
C. Time-series data  
D. Unstructured data

**Answer:** C

**Why:** Sequential measurements associated with timestamps are **time-series data**, which is useful for forecasting future trends.

---

### Question 5

A company wants to predict the monthly electricity cost of a building based on its historical energy consumption.

Which ML approach is most appropriate?

A. Linear regression  
B. Classification  
C. Tokenization  
D. Clustering

**Answer:** A

**Why:** Electricity cost is a **continuous numerical value**, making regression appropriate.

---

### Question 6

During ML model training, what happens to model parameters?

A. They are adjusted to improve model predictions  
B. They are permanently fixed before training begins  
C. They are converted into database tables  
D. They are replaced by inference results

**Answer:** A

**Why:** Training iteratively adjusts model **parameters** to reduce prediction errors and improve the model.

---

### Question 7

A company has images, videos, and free-form text documents that it wants to use in an ML workload.

Which classification best describes this data?

A. Structured  
B. Semi-structured  
C. Unstructured  
D. Relational

**Answer:** C

**Why:** Images, videos, and free-form documents generally don't conform to a predefined tabular schema, so they are **unstructured data**.