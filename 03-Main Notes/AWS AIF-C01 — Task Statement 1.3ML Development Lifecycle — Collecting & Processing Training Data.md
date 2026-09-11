# AWS AIF-C01 — Task Statement 1.3

## ML Development Lifecycle — Collecting & Processing Training Data

## 🎯 Exam Essentials

### 1. Data Collection Comes Before Training

Before training a model, determine:

- **What data is required?**
    
- **Where is it generated?**
    
- **Where is it stored?**
    
- Is it **batch or streaming data**?
    
- Is it **labeled or unlabeled**?
    
- How will it be repeatedly collected as new data arrives?
    

A good ML data pipeline must be **repeatable**, because models may need to be retrained with new data.

---

### 2. ETL — Extract, Transform, Load

**ETL** is the process of:

**Extract → Transform → Load**

- **Extract:** Collect data from one or more sources.
    
- **Transform:** Clean, modify, normalize, combine, etc.
    
- **Load:** Store the processed data in a target repository.
    

For example:

**Multiple data sources → AWS Glue → S3 → ML training**

**Exam trigger:**

> "Collect data from multiple sources, transform it, and load it into a centralized repository"  
> → **ETL**

---

### 3. Data Preparation

Before training, data may need:

- Missing values handled
    
- Anomalous/outlier values addressed
    
- Duplicate records removed
    
- Inconsistent schemas corrected
    
- PII masked or removed
    
- Data normalized/transformed
    
- Features selected/engineered
    

### EDA — Exploratory Data Analysis

EDA means examining and analyzing the dataset to understand:

- Patterns
    
- Distributions
    
- Relationships
    
- Anomalies
    
- Data quality issues
    

Visualization is commonly useful during EDA.

---

### 4. Training / Validation / Test Split

The transcript gives a common example:

|Dataset|Approx. amount|Purpose|
|---|--:|---|
|**Training**|80%|Train the model|
|**Validation/evaluation**|10%|Evaluate/tune the model during development|
|**Test**|10%|Final unbiased evaluation before production|

**Important:** The exact percentages are **not a universal AWS rule**. The important AIF-C01 concept is understanding the distinct purposes of training, validation/evaluation, and test datasets.

---

### 5. Features & Feature Engineering

A **feature** is an input characteristic used by an ML model.

Feature engineering involves selecting, transforming, combining, or creating useful features from raw data.

Example:

Raw data:

> Date of birth + current date

Possible feature:

> Age

Why reduce unnecessary features?

- Less memory
    
- Less computation
    
- Potentially faster training
    
- Can reduce irrelevant information
    
- Can simplify the model
    

**Exam trigger:**

> "Select only the relevant characteristics used as model inputs"  
> → **Feature selection**

> "Transform/combine raw data into useful model inputs"  
> → **Feature engineering**

---

# AWS Services for Data Collection & Preparation

## 6. AWS Glue

**AWS Glue = managed ETL service**

It can:

- Discover data
    
- Extract data
    
- Transform data
    
- Load data
    
- Work across multiple data sources
    
- Catalog data
    
- Generate ETL code
    

A common destination for processed ML data is **Amazon S3**.

### 🧠 AWS Glue mental model

**Glue = ETL**

If the question says:

> "Extract data from several sources, transform it, and load it into S3."

Think:

**AWS Glue**

---

## 7. AWS Glue Data Catalog

This is an extremely important distinction.

The **Glue Data Catalog stores metadata about data**, not the actual source data itself.

Metadata can include:

- Data location
    
- Schema
    
- Table definitions
    
- Related information/metrics
    

Think:

> **Data Catalog = map describing where the data is and what it looks like.**

Not:

> "The actual dataset is stored inside the Data Catalog."

---

### Glue Crawler

A **Glue crawler** can inspect data sources and automatically determine their schema using classifiers.

It then creates/updates tables in the **Glue Data Catalog**.

Mental model:

**Data source → Crawler → discovers schema → Data Catalog**

---

## 8. AWS Glue DataBrew

**DataBrew = visual, no-code/low-code data preparation**

It allows users to:

- Discover data
    
- Visualize data
    
- Clean data
    
- Normalize data
    
- Transform data
    
- Identify data-quality problems
    
- Create reusable transformation recipes
    
- Profile data
    
- Define data-quality rules
    

Examples of transformations:

- Remove nulls
    
- Replace missing values
    
- Remove duplicates
    
- Fix schema inconsistencies
    
- Create calculated columns
    

### 🧠 Glue vs DataBrew

|AWS service|Primary purpose|
|---|---|
|**AWS Glue**|ETL + data catalog|
|**AWS Glue DataBrew**|Visual data cleaning/preparation|

**Exam trigger:**

> "Clean and transform data visually without writing code"  
> → **Glue DataBrew**

---

# 9. SageMaker Ground Truth

**SageMaker Ground Truth = build labeled training datasets**

Supervised ML requires **labeled data**.

Ground Truth can use **active learning** to:

1. Automatically label data when the model can confidently do so.
    
2. Send uncertain cases to human workers.
    

Human labeling can involve:

- Private workforce
    
- External workforce options such as Amazon Mechanical Turk
    

### 🧠 Mental model

**Need labels → Ground Truth**

This is particularly important when high-quality labeled data doesn't already exist.

---

# 10. SageMaker Data Wrangler

SageMaker Data Wrangler provides tools for:

- Selecting/importing data
    
- Data preparation
    
- Data transformation
    
- Feature engineering
    
- Analyzing data
    

It provides a visual interface to make data preparation easier.

---

# 11. SageMaker Canvas

**SageMaker Canvas** provides a visual/no-code-oriented interface for ML workflows and can help with:

- Data preparation
    
- Feature engineering
    
- Data analysis
    
- Building ML solutions
    

For this transcript, remember it primarily as a **visual tool that simplifies data preparation and feature engineering**.

---

# 12. SageMaker Feature Store

**SageMaker Feature Store = centralized store for ML features and their metadata.**

It helps organizations:

- Store features
    
- Discover features
    
- Reuse features
    
- Share features
    
- Manage features
    

Why is this useful?

Without a feature store, different ML projects may repeatedly perform the same raw-data processing.

Feature Store helps make features **reusable and consistently managed**.

### 🧠 Mental model

**Raw data → processing → features → Feature Store → ML models**

**Exam trigger:**

> "Centralized repository for reusable ML features"  
> → **SageMaker Feature Store**

---

# 🔑 Key Terms

|Term|Meaning|Exam Trigger|
|---|---|---|
|**ETL**|Extract, transform, load|Move/process data|
|**EDA**|Explore and understand data|Visualization/patterns|
|**Feature**|Input characteristic used by model|Model input|
|**Feature engineering**|Create/transform useful model features|Raw data → useful inputs|
|**Feature selection**|Choose relevant existing features|Remove unnecessary inputs|
|**Data labeling**|Assign target labels to training examples|Supervised ML|
|**AWS Glue**|Managed ETL service|Extract/transform/load|
|**Glue Data Catalog**|Metadata repository|Schema/location|
|**Glue Crawler**|Discovers data/schema|Automatically catalog data|
|**Glue DataBrew**|Visual data preparation|No-code cleaning|
|**SageMaker Ground Truth**|Training-data labeling|Need labeled dataset|
|**SageMaker Data Wrangler**|Data selection/preparation/transformation|Prepare ML data|
|**SageMaker Canvas**|Visual ML/data workflow|Visual/no-code ML|
|**SageMaker Feature Store**|Centralized feature repository|Reuse ML features|
|**PII**|Personally identifiable information|Mask/remove sensitive data|

---

# ⚔️ Important Comparisons

### AWS Glue vs Glue DataBrew

||AWS Glue|Glue DataBrew|
|---|---|---|
|Main purpose|ETL|Data preparation|
|Interface|ETL jobs/workflows|Visual|
|Coding|Can generate/use ETL code|Designed for visual preparation|
|Catalog|**Yes — Data Catalog**|No primary catalog role|
|Exam clue|"ETL from multiple sources"|"Clean/transform visually"|

---

### Ground Truth vs Feature Store

|SageMaker Ground Truth|SageMaker Feature Store|
|---|---|
|Creates **labels**|Stores **features**|
|Used before/during dataset preparation|Used to manage/reuse features|
|Human + ML-assisted labeling|Centralized feature repository|
|"Label my images"|"Store and reuse my features"|

---

### Feature Selection vs Feature Engineering

**Feature selection**

> Choose which existing features are useful.

Example:

`Age, Income, Height, FavoriteColor → Age + Income`

**Feature engineering**

> Create or transform features.

Example:

`Date of birth + current date → Age`

---

# 🧠 Exam Traps

### Trap 1 — Glue Data Catalog stores the actual data ❌

It stores **metadata**, such as schema and data location.

The actual data can remain in places such as S3.

---

### Trap 2 — Ground Truth trains the final model ❌

Ground Truth primarily helps create **high-quality labeled training datasets**.

---

### Trap 3 — Feature Store stores raw datasets ❌

Its purpose is to store and manage **ML features and associated metadata**.

---

### Trap 4 — ETL means only moving data ❌

ETL includes **extraction + transformation + loading**.

---

### Trap 5 — Every ML dataset must use exactly 80/10/10 ❌

80/10/10 is a common example, not a universal requirement.

Know the **purpose of each split**, not the number as an absolute rule.

---

### Trap 6 — More features are always better ❌

Irrelevant features can increase computation and potentially hurt model performance.

Feature selection/engineering aims to retain **useful inputs**.

---

# 📝 Exam Questions

### Q1

A company needs to extract data from several databases, transform it, and load the resulting dataset into Amazon S3. Which AWS service is most appropriate?

A. Amazon Lex  
B. AWS Glue  
C. Amazon Polly  
D. SageMaker Ground Truth

**Answer: B — AWS Glue**

---

### Q2

An organization wants to automatically discover the schema of datasets stored in its data sources and record that information for use by ETL jobs. What should it use?

A. AWS Glue Crawler and Data Catalog  
B. Amazon Polly  
C. SageMaker Feature Store  
D. Amazon Rekognition

**Answer: A**

---

### Q3

A developer asks where the actual source dataset is stored in the AWS Glue Data Catalog. What is the correct explanation?

A. The Data Catalog stores the complete dataset  
B. The Data Catalog stores metadata describing the data  
C. The Data Catalog stores only model weights  
D. The Data Catalog stores only labels

**Answer: B**

---

### Q4

A business analyst wants to clean and transform datasets using a visual interface without writing code. Which service is most appropriate?

A. AWS Glue DataBrew  
B. Amazon Kendra  
C. SageMaker Ground Truth  
D. Amazon Transcribe

**Answer: A — AWS Glue DataBrew**

---

### Q5

A company needs thousands of labeled images to train a supervised computer vision model. Which AWS capability is specifically designed to help create labeled datasets?

A. SageMaker Ground Truth  
B. SageMaker Feature Store  
C. AWS Glue Data Catalog  
D. Amazon Polly

**Answer: A**

---

### Q6

A company wants to centrally store reusable ML features so that multiple ML projects can discover and reuse them. Which service should it consider?

A. Amazon S3  
B. SageMaker Feature Store  
C. SageMaker Ground Truth  
D. AWS Glue DataBrew

**Answer: B**

---

### Q7

A data scientist combines a customer's purchase frequency and average purchase amount into a new metric used by an ML model. What is this an example of?

A. Data labeling  
B. Feature engineering  
C. Data cataloging  
D. Inference

**Answer: B — Feature engineering**

---

### Q8

Why should an ML data collection process be repeatable?

A. Models never need new data  
B. Models may need to be retrained as new data becomes available  
C. AWS requires all datasets to be processed twice  
D. Feature Store automatically retrains every model

**Answer: B**

---

# ⚡ 30-Second Revision

1. **ETL = Extract → Transform → Load.**
    
2. **AWS Glue = managed ETL.**
    
3. **Glue Data Catalog = metadata, NOT actual data.**
    
4. **Glue Crawler = discovers schema → Data Catalog.**
    
5. **Glue DataBrew = visual data cleaning/preparation.**
    
6. **Ground Truth = labeling training data.**
    
7. **Data Wrangler = visual data selection/preparation/transformation.**
    
8. **Feature Store = centralized reusable ML features.**
    
9. **Feature engineering = create/transform useful model inputs.**
    
10. **Feature selection = choose relevant features.**
    
11. **Supervised ML needs labeled data.**
    
12. **Data pipeline should be repeatable because models may be retrained.**
    
13. **Handle missing/anomalous data and protect PII before training.**
    
14. **80/10/10 is a common split example, not an absolute rule.**
    

### 🧠 Ultimate AWS service map

**Move/transform data → Glue**  
**Catalog metadata → Glue Data Catalog**  
**Discover schema → Glue Crawler**  
**Clean visually → Glue DataBrew**  
**Create labels → Ground Truth**  
**Prepare features → Data Wrangler**  
**Store/reuse features → Feature Store**