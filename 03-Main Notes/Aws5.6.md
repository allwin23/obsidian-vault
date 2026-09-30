# Domain 5 — Task Statement 5.1: Explain methods to secure AI systems

## 🎯 Exam Essentials

### **1. Artifact Versioning and Tracking**

- **Concept:** To reproduce a model and satisfy **regulatory and control requirements**, all artifacts involved in model development must be **versioned and tracked**.
    
- **Key distinction:** Reproducibility requires tracking more than just the final model. Code, datasets, containers, training configurations, model outputs, and related metadata all contribute to the model.
    
- **Exam trigger:** Look for **reproducing a model, regulatory requirements, auditability, governance, or tracking everything used to produce a model**.
    

### **2. Version-Controlled Source Code**

- **Concept:** Code repositories such as **GitHub and AWS CodeCommit** retain versions of source code.
    
- **Key distinction:** The tracked code can include **training code, inference code, experiments, and notebooks**.
    
- **Exam trigger:** Scenario asks how to track different versions of **ML source code or notebooks**.
    

### **3. Dataset Version Identification**

- **Concept:** Datasets should be stored in **Amazon S3** and partitioned using prefixes to uniquely identify the training dataset.
    
- **Key distinction:** The dataset used for a particular model needs to be identifiable so the training process can be reproduced.
    
- **Exam trigger:** Look for requirements to **identify which exact training dataset** produced a model.
    

### **4. Amazon ECR Container Images**

- **Concept:** Container images stored in **Amazon Elastic Container Registry (Amazon ECR)** are uniquely identified and can also receive additional tags.
    
- **Key distinction:** Container artifacts are another component that must be tracked for reproducibility.
    
- **Exam trigger:** Scenario asks about tracking the specific **container image/artifact** used during model development or training.
    

### **5. SageMaker Training Job Metadata**

- **Concept:** SageMaker automatically gives each training job a **unique identifier** and stores metadata such as **hyperparameters, container identifier, dataset identifier, and model output identifier**.
    
- **Key distinction:** Training-job metadata connects the configuration and artifacts used to produce the trained model.
    
- **Exam trigger:** Look for a requirement to identify **which hyperparameters, dataset, container, or output** were associated with a training job.
    

### **6. SageMaker Model Registry**

- **Concept:** **SageMaker Model Registry** allows model versions to be cataloged in **model groups**.
    
- **Key distinction:** Each model package in a model group corresponds to a **trained model**.
    
- **Exam trigger:** Look for **model versioning, model catalogs, model groups, or managing multiple versions of a trained model**.
    

### **7. Model Metadata and Training Metrics**

- **Concept:** Model Registry allows metadata associated with models to be stored and viewed, including **training metrics**.
    
- **Key distinction:** The registry is not simply a storage location for model artifacts; it also maintains information about the model.
    
- **Exam trigger:** Scenario asks for a centralized location to **catalog models and view associated training information**.
    

### **8. Model Deployment from Model Registry**

- **Concept:** Models can be **deployed directly from SageMaker Model Registry**.
    
- **Key distinction:** Model Registry supports both model cataloging and the deployment workflow described in the transcript.
    
- **Exam trigger:** Requirement involves moving an approved/cataloged model from the registry into deployment.
    

### **9. Model Status in Model Registry**

- **Concept:** Model Registry allows the status of a model to be maintained, such as **pending, approved, or rejected**, according to the transcript.
    
- **Key distinction:** Status provides a governance mechanism for tracking where a model stands in the approval process.
    
- **Exam trigger:** Look for **model approval workflows, governance, or determining whether a model is approved for deployment**.
    

### **10. SageMaker Model Cards**

- **Concept:** **Amazon SageMaker Model Cards** document, retrieve, and share essential information about a model from **conception through deployment**.
    
- **Key distinction:** Model Cards focus on documenting important information about the model rather than primarily managing model versions.
    
- **Exam trigger:** Look for **model documentation, intended uses, risk ratings, training details, evaluation results, or sharing model information with stakeholders**.
    

### **11. Model Card Immutable Record**

- **Concept:** Model Cards can provide an **immutable record** containing information such as intended model uses, risk ratings, training details, and evaluation results.
    
- **Key distinction:** Model Cards support model documentation and governance throughout the model lifecycle.
    
- **Exam trigger:** Scenario emphasizes **documenting model risks, intended use, evaluation, or governance information**.
    

### **12. Model Cards Export**

- **Concept:** Model Cards can be exported to **PDF** and shared with relevant stakeholders.
    
- **Key distinction:** This supports communicating model information outside the immediate SageMaker environment.
    
- **Exam trigger:** Requirement involves **sharing documented model information with stakeholders in PDF form**.
    

### **13. SageMaker ML Lineage Tracking**

- **Concept:** **Amazon SageMaker ML Lineage Tracking** automatically creates a graphical representation of the elements involved in an end-to-end ML workflow.
    
- **Key distinction:** Lineage focuses on the **relationships and dependencies between ML workflow artifacts**.
    
- **Exam trigger:** Look for **workflow relationships, provenance, reproducibility, governance, or discovering which artifacts were used together**.
    

### **14. Lineage Tracking for Governance and Reproducibility**

- **Concept:** Lineage Tracking can establish **model governance, reproduce workflows, and maintain a record of work history**.
    
- **Key distinction:** Instead of manually recording every relationship, SageMaker automatically tracks entities and their relationships.
    
- **Exam trigger:** Scenario requires understanding **how a model was produced and which artifacts were involved**.
    

### **15. Lineage Entities**

- **Concept:** Lineage Tracking automatically creates tracking entities for **trial components and their associated trials and experiments**.
    
- **Key distinction:** Lineage information represents relationships among components of the ML workflow.
    
- **Exam trigger:** Question asks about automatically tracking **trials, experiments, processing, training, or batch-transform relationships**.
    

### **16. Lineage Across SageMaker Jobs**

- **Concept:** Lineage Tracking can be used with SageMaker jobs such as **processing jobs, training jobs, and batch transform jobs**.
    
- **Key distinction:** It provides a connected view across different stages of an ML workflow.
    
- **Exam trigger:** Scenario involves tracing artifacts across **processing → training → batch transformation**.
    

### **17. Querying Lineage**

- **Concept:** Lineage data can be queried to discover relationships between entities.
    
- **Key distinction:** You can trace dependencies in either direction—for example, finding models that use a particular dataset or datasets associated with a container artifact.
    
- **Exam trigger:** Question asks **"Which models used this dataset?"** or **"Which datasets are associated with this container?"**
    

### **18. SageMaker Feature Store**

- **Concept:** **Amazon SageMaker Feature Store** is a centralized store for **features and associated metadata**.
    
- **Key distinction:** Feature Store focuses on making features **discoverable, reusable, and manageable** for ML development.
    
- **Exam trigger:** Look for requirements involving **centralized feature storage, feature reuse, or reducing repeated feature-processing work**.
    

### **19. Feature**

- **Concept:** A **feature** is a data property used as an input to train a model or make predictions. The transcript gives a column in a data table as an example.
    
- **Key distinction:** A feature is an input property used by the ML model, rather than the entire dataset itself.
    
- **Exam trigger:** Question asks what an individual **input property/column used for ML** represents.
    

### **20. Feature Store Feature Processing**

- **Concept:** Feature Store can support workflows that convert **raw data into features** and add those features to feature groups.
    
- **Key distinction:** It reduces repetitive data-processing and curation work involved in preparing features.
    
- **Exam trigger:** Scenario involves repeatedly transforming raw data into **reusable ML features**.
    

### **21. Feature Group Lineage**

- **Concept:** Feature Store allows users to view the **lineage of a feature group**, including execution code, data sources, and how data was ingested.
    
- **Key distinction:** Feature lineage explains **where a feature came from and how it was produced**.
    
- **Exam trigger:** Look for requirements to trace a feature back to its **processing code or source data**.
    

### **22. Point-in-Time Feature Queries**

- **Concept:** Feature Store supports **point-in-time queries**, allowing retrieval of the state of each feature at a historical time of interest.
    
- **Key distinction:** This enables retrieving the feature values corresponding to a particular point in time rather than simply retrieving the current state.
    
- **Exam trigger:** Scenario asks for the **historical state of features at a particular time**.
    

### **23. SageMaker Model Dashboard**

- **Concept:** **SageMaker Model Dashboard** is a centralized portal in the SageMaker console where you can **view, search, and explore models** in an account.
    
- **Key distinction:** The dashboard aggregates model-related information from multiple SageMaker features, including **Model Monitor and Model Cards**.
    
- **Exam trigger:** Look for a requirement for a **centralized view of models and their related information**.
    

### **24. Model Dashboard and Lineage**

- **Concept:** The Model Dashboard allows users to **visualize workflow lineage** and track endpoint performance.
    
- **Key distinction:** It brings model-related information together rather than requiring users to inspect each feature independently.
    
- **Exam trigger:** Scenario requires a centralized place to see **lineage + model information + endpoint performance**.
    

### **25. Model Deployment Tracking**

- **Concept:** The Model Dashboard can track which models are deployed for inference and whether models are being used in **batch transform jobs or hosted on endpoints**.
    
- **Key distinction:** This provides visibility into how models are being used in production.
    
- **Exam trigger:** Look for questions about **which model is deployed, where it is hosted, or whether it is used for batch inference**.
    

### **26. Model Dashboard Monitoring Results**

- **Concept:** When Model Monitor is configured, the Model Dashboard can track model performance on **live data**.
    
- **Key distinction:** The dashboard aggregates monitoring results alongside other model information.
    
- **Exam trigger:** Scenario combines **model inventory + production monitoring results**.
    

### **27. Monitoring Threshold Violations**

- **Concept:** The Model Dashboard can identify models that violate configured thresholds for **data quality, model quality, bias, and explainability**.
    
- **Key distinction:** It can also help identify models that **do not have these metrics configured**.
    
- **Exam trigger:** Look for centralized identification of models violating **quality/bias/explainability thresholds** or lacking monitoring configuration.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Artifact**|Any component involved in producing a model, such as code, data, containers, or model outputs.|
|**Reproducibility**|Ability to recreate a model/workflow using the tracked artifacts and metadata.|
|**Amazon ECR**|Stores container images used by ML workflows.|
|**SageMaker training job**|Training execution with a unique identifier and associated metadata.|
|**SageMaker Model Registry**|Catalogs model versions in model groups.|
|**Model group**|Collection containing different versions of a model.|
|**Model package**|Represents a trained model within a model group.|
|**Model Cards**|Documents essential model information throughout its lifecycle.|
|**ML Lineage Tracking**|Tracks relationships among ML workflow entities and artifacts.|
|**Feature**|Data property used as model-training or prediction input.|
|**Feature Store**|Centralized store for features and associated metadata.|
|**Feature group**|Collection of related features managed by Feature Store.|
|**Point-in-time query**|Retrieves feature state at a specified historical time.|
|**Model Dashboard**|Centralized SageMaker portal for viewing and exploring models and related information.|
|**Model Monitor**|Provides production model/data monitoring information used by the dashboard.|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Code repository**|Versioning ML source code|Tracks training/inference code, experiments, notebooks|
|**Amazon S3**|Storing training datasets|Dataset identification/version organization through prefixes|
|**Amazon ECR**|Tracking container artifacts|Container images have unique identifiers and tags|
|**Model Registry**|Managing model versions|Catalogs trained models in model groups|
|**Model Cards**|Documenting model information|Intended use, risks, training details, evaluation results|
|**ML Lineage Tracking**|Understanding artifact relationships|Graphical representation of end-to-end ML workflow|
|**Feature Store**|Managing reusable ML features|Centralized feature storage and metadata|
|**Model Dashboard**|Centralized model visibility|Aggregates model, monitoring, lineage, and deployment information|
|**Model Registry vs. Model Cards**|Model lifecycle management vs. documentation|Registry catalogs/versions models; Model Cards document model information|
|**Lineage Tracking vs. Feature Store lineage**|Workflow provenance vs. feature provenance|Lineage Tracking covers ML workflow entities; Feature Store tracks feature-processing lineage|
|**Data quality monitoring vs. Model Dashboard**|Monitoring data vs. central visibility|Model Monitor provides monitoring; Dashboard aggregates results|

---

## 🧠 Exam Traps

### **1.**

**Trap:** Tracking only the final model artifact is sufficient to reproduce a model.

**Correct:** Reproduction requires tracking **all relevant artifacts**, including code, datasets, containers, training configuration, metadata, and model outputs.

### **2.**

**Trap:** Model Registry is primarily a tool for documenting intended use and risk ratings.

**Correct:** **Model Registry** catalogs and manages model versions. **Model Cards** document intended use, risks, training details, and evaluation results.

### **3.**

**Trap:** Model Cards are primarily used to version source code.

**Correct:** Code repositories track **source-code versions**; Model Cards document important **model information and governance details**.

### **4.**

**Trap:** ML Lineage Tracking is simply another model-version storage mechanism.

**Correct:** Lineage Tracking represents **relationships between ML workflow entities and artifacts**, supporting governance and reproducibility.

### **5.**

**Trap:** Lineage information can only be viewed manually and cannot be queried.

**Correct:** The transcript states that you can **run queries against lineage data** to discover relationships between entities.

### **6.**

**Trap:** Feature Store is primarily a model registry.

**Correct:** Feature Store is a centralized store for **features and associated metadata**, designed to make features discoverable and reusable.

### **7.**

**Trap:** A feature is the same thing as an entire training dataset.

**Correct:** A feature is an individual **data property used as an input** for training or prediction, such as a column in a data table.

### **8.**

**Trap:** Point-in-time queries return only the latest feature values.

**Correct:** Point-in-time queries retrieve the **state of features at a historical time of interest**.

### **9.**

**Trap:** Model Dashboard replaces all other SageMaker model-management features.

**Correct:** The dashboard **aggregates information** from features such as Model Monitor and Model Cards and provides centralized visibility.

### **10.**

**Trap:** Model Dashboard only shows models that are currently deployed to endpoints.

**Correct:** The dashboard can track models used for **inference, batch transform jobs, and hosted endpoints**.

### **11.**

**Trap:** SageMaker automatically tracks every artifact relationship without requiring any lineage functionality.

**Correct:** The transcript specifically identifies **SageMaker ML Lineage Tracking** as the capability that automatically creates representations of ML workflow relationships.

### **12.**

**Trap:** Model Dashboard monitoring is limited to model accuracy.

**Correct:** The transcript describes tracking thresholds for **data quality, model quality, bias, and explainability**.

---

# 📝 Exam Questions

### **Question 1**

A financial organization must be able to reproduce an AI model several years after it was deployed to satisfy regulatory requirements. The organization wants to ensure that the exact source code, dataset, container, training configuration, and resulting model can be identified. Which approach best matches the requirement?

A. Track only the final model in SageMaker Model Registry and reconstruct the remaining artifacts when required.

B. Version and track the complete set of artifacts used in model development, including code, datasets, containers, and training metadata.

C. Store the final model in S3 and rely on CloudWatch logs to reconstruct the training environment.

D. Document the intended model use in Model Cards and assume that the documented information is sufficient for reproduction.

**Answer: B — Version and track the complete set of artifacts used in model development, including code, datasets, containers, and training metadata.**

**Why:** The lesson emphasizes that reproducibility requires tracking **all artifacts** involved in producing the model, not just the final model.

### **Question 2**

An ML team wants to maintain multiple versions of a trained model, associate training metrics and metadata with those models, and manage their lifecycle status. Which SageMaker capability best matches this requirement?

A. SageMaker Model Cards

B. SageMaker Model Registry

C. SageMaker Feature Store

D. SageMaker ML Lineage Tracking

**Answer: B — SageMaker Model Registry.**

**Why:** Model Registry catalogs models in **model groups**, associates metadata such as training metrics, and maintains model status.

### **Question 3**

A company's risk-management team needs an immutable record documenting a model's intended uses, risk rating, training details, and evaluation results. The record must also be shareable with stakeholders as a PDF. Which capability should they use?

A. SageMaker Model Registry

B. SageMaker Model Dashboard

C. SageMaker Model Cards

D. SageMaker Feature Store

**Answer: C — SageMaker Model Cards.**

**Why:** Model Cards are specifically described as documenting model information such as **intended use, risk ratings, training details, and evaluation results**, and they can be exported to PDF.

### **Question 4**

An ML engineer needs to determine which trained models were produced using a particular dataset and which datasets are associated with a particular container artifact. Which SageMaker capability most directly supports these queries?

A. SageMaker Model Registry

B. SageMaker ML Lineage Tracking

C. SageMaker Model Cards

D. SageMaker Model Dashboard

**Answer: B — SageMaker ML Lineage Tracking.**

**Why:** Lineage Tracking allows queries against lineage data to discover relationships between entities, such as **models, datasets, and container artifacts**.

### **Question 5**

A data science team repeatedly transforms raw data into features for several ML projects. The team wants a centralized location where features and their metadata can be discovered and reused to reduce repeated data-processing work. Which service best matches the requirement?

A. SageMaker Model Registry

B. Amazon SageMaker Feature Store

C. Amazon ECR

D. SageMaker Model Cards

**Answer: B — Amazon SageMaker Feature Store.**

**Why:** Feature Store is a centralized store for **features and associated metadata**, designed to simplify feature discovery, sharing, and reuse.

### **Question 6**

An ML team needs to reproduce the exact feature values that existed at a particular historical point in time when a model was trained. Which Feature Store capability described in the lesson is most relevant?

A. Model group versioning

B. Point-in-time queries

C. Model package approval

D. Endpoint metadata tracking

**Answer: B — Point-in-time queries.**

**Why:** Feature Store supports point-in-time queries to retrieve the **historical state of each feature** at a specified time.

### **Question 7**

A machine learning engineer wants to understand how a feature group was created. Specifically, they need to identify the processing code, source data, and how the data was ingested into the feature group. Which capability described in the lesson provides this information?

A. Feature Store feature-group lineage

B. Model Registry model status

C. Model Cards

D. Model Dashboard endpoint tracking

**Answer: A — Feature Store feature-group lineage.**

**Why:** Feature Store lineage includes the **execution code, data sources, and ingestion information** associated with feature processing.

### **Question 8**

An organization wants a single location in the SageMaker console where engineers can search for models, inspect workflow lineage, view endpoint performance, and see information aggregated from Model Monitor and Model Cards. Which capability matches this requirement?

A. SageMaker Model Dashboard

B. SageMaker Model Registry

C. SageMaker Feature Store

D. SageMaker ML Lineage Tracking

**Answer: A — SageMaker Model Dashboard.**

**Why:** The Model Dashboard is described as a **centralized portal** that aggregates model-related information from multiple SageMaker capabilities.

### **Question 9**

A security team wants to identify deployed models whose monitoring configuration shows that they have exceeded configured thresholds for data quality, model quality, bias, or explainability. Which SageMaker capability described in the lesson is most directly suited to providing this centralized view?

A. SageMaker Model Registry

B. SageMaker Model Dashboard

C. Amazon ECR

D. SageMaker Feature Store

**Answer: B — SageMaker Model Dashboard.**

**Why:** The dashboard can identify models that violate configured thresholds for **data quality, model quality, bias, and explainability**.

### **Question 10**

A company wants to determine exactly which container image, dataset, hyperparameters, and model output were associated with a particular SageMaker training execution. Which information source described in the lesson most directly provides this relationship?

A. SageMaker training job metadata

B. SageMaker Model Cards

C. S3 Block Public Access

D. SageMaker Feature Store

**Answer: A — SageMaker training job metadata.**

**Why:** SageMaker uniquely identifies training jobs and stores metadata including **hyperparameters and identifiers for the container, dataset, and model output**.

### **Question 11**

An organization needs to understand the complete relationship between processing jobs, training jobs, batch transform jobs, experiments, and their associated artifacts so that it can reproduce a workflow. Which capability is most directly designed for this purpose?

A. SageMaker ML Lineage Tracking

B. SageMaker Model Registry

C. SageMaker Model Cards

D. Amazon ECR

**Answer: A — SageMaker ML Lineage Tracking.**

**Why:** ML Lineage Tracking creates a graphical representation of the **end-to-end ML workflow** and its relationships, supporting governance and reproducibility.

### **Question 12**

A governance team wants to manage the approval lifecycle of different trained model versions. It needs to identify whether each model is pending, approved, or rejected before deployment. Which SageMaker capability described in the lesson best fits this requirement?

A. SageMaker Feature Store

B. SageMaker Model Cards

C. SageMaker Model Registry

D. SageMaker Model Monitor

**Answer: C — SageMaker Model Registry.**

**Why:** Model Registry allows model versions to be cataloged and their **status** to be maintained, including the approval states described in the transcript.

---

# ⚡ 30-Second Revision

1. **Reproducibility →** Version and track **all model-production artifacts**, not just the final model.
    
2. **Code →** GitHub/CodeCommit retain versions of training/inference code, experiments, and notebooks.
    
3. **Dataset →** Store in **S3** and uniquely identify the training dataset.
    
4. **Containers →** **ECR** uniquely identifies container images.
    
5. **Model Registry →** Catalogs model versions in **model groups** with metadata and status.
    
6. **Model Cards →** Document **intended use, risks, training details, and evaluation results**.
    
7. **Lineage Tracking →** Shows relationships across the **end-to-end ML workflow**.
    
8. **Feature Store →** Centralized, reusable **features + metadata**.
    
9. **Point-in-time query →** Retrieve a feature's **historical state**.
    
10. **Model Dashboard →** Centralized view of **models, lineage, endpoints, and monitoring information**.
    
11. **Training job metadata →** Tracks hyperparameters + **dataset/container/model-output identifiers**.
    
12. **Dashboard thresholds →** Can identify violations involving **data quality, model quality, bias, and explainability**.