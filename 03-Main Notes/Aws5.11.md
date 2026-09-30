# Domain 5, Task Statement 5.2: Governance and Compliance (Data Governance, Data Quality, Lake Formation, S3 Lifecycle)

The transcript is part 1 of 5.2 ("I'm going to pause this lesson here"), so the questions below cover only what it stated.

---

## 🎯 Exam Essentials

### **1. Data Quality Management (root cause first)**

- **Concept:** Addresses data quality issues found in **data profiling** or other means. Get to the **root cause**, which requires business and technical knowledge of the data.
- **Key distinction:** If the problem is at the **source**, alert and report to the **data steward** and business users who can fix it. The fix is not applied downstream.
- **Exam trigger:** "Issues found in profiling," "source data is wrong," "who should be notified."

### **2. Data Integration**

- **Concept:** Collecting and merging data from a variety of sources so they **link together coherently** and give a more complete picture.
- **Key distinction:** Integration is about **coherent linking/combining**. Quality is about **fixing issues**. Governance is about **control vs. access**.
- **Exam trigger:** "Combine data from multiple sources," "complete picture."

### **3. AWS Glue Data Catalog**

- **Concept:** Stores **metadata** about data sources: locations, schemas, data types, table definitions. Populate it **manually** or with an **AWS Glue crawler job** that scans sources automatically.
- **Key distinction:** It stores **metadata, not the data itself**. The crawler is the automatic population method.
- **Exam trigger:** "Metadata," "schemas," "automatically discover and populate."

### **4. AWS Glue Data Quality**

- **Concept:** Evaluates objects stored in the **Glue Data Catalog**. Helps **non-coders** set up quality rules, **recommends rules**, and uses **ML to detect anomalies**.
- **Key distinction:** Workflow: define rule set → run a **Glue Data Quality job** → review console results showing which rules **passed or failed**.
- **Exam trigger:** "Non-coders," "recommend data quality rules," "detect data anomalies," "which rules passed."

### **5. Data Security (role-based, temporary access)**

- **Concept:** Defining **who** can access data and **when**. The **data steward** enables **role-based and temporary access**, guided by policy decisions from the **data owner**.
- **Key distinction:** Owner **decides policy**. Steward **enables access** by implementing it.
- **Exam trigger:** "Customer service or sales roles need access," "temporary access."

### **6. Compliance Roles**

- **Concept:** Understanding government regulations and ensuring adherence. **Data owners** work with **security and legal teams** to make policy decisions for sensitive data domains. Rules require **interpretation and judgment**.
- **Key distinction:** Compliance policy is a **cross-functional decision** (owner + security + legal), not purely a technical or steward task.
- **Exam trigger:** "Sensitive data domains," "government regulations," "who makes the policy decision."

### **7. Data Governance (control vs. access balance)**

- **Concept:** Making data available to the **right people and applications when needed**, while keeping it safe with appropriate controls.
- **Key distinction:** Too much control → **siloed** data, hard to use for insights. Too little → data and business **at risk**.
- **Exam trigger:** "Balance between control and access," "data locked in silos."

### **8. AWS Lake Formation**

- **Concept:** **Fine-grained access control** for a data lake built in **Amazon S3** and cataloged with **AWS Glue Data Catalog**. Enforced at **column, row, and cell** levels across AWS analytics and ML services.
- **Key distinction:** Integrated engines (**Athena, AWS Glue, Amazon EMR, Amazon Redshift**) go through the Glue Data Catalog, which **checks permissions with Lake Formation before granting access**.
- **Exam trigger:** "Column/row/cell-level permissions on a data lake," "break down silos," "centralized repository of structured and unstructured data."

### **9. Amazon S3 Storage Classes (by access pattern)**

- **Concept:** Storage classes are optimized for cost based on access frequency. Training data may not be needed again after training but must still be **retained for compliance**.
- **Key distinction:**
    - **S3 Standard** → frequently accessed
    - **S3 Standard-IA / One Zone-IA** → less frequent, but **quickly retrievable**. Cheaper storage, **costlier retrieval** than Standard.
    - **S3 Intelligent-Tiering** → **unknown or changing** access patterns. Automatically moves less-accessed objects to lower-cost tiers.
    - **S3 Glacier classes** → **rarely accessed**, long-term archive for retention/compliance. Different classes offer different retrieval speeds.
- **Exam trigger:** "Retain for compliance," "unknown access patterns," "rarely accessed."

### **10. S3 Lifecycle Rules**

- **Concept:** Used when you **know the access pattern**. Each rule specifies the **target storage class** and **days after creation** for transition. Rules can also **delete** data when retention is no longer needed.
- **Key distinction:** Lifecycle rules are for **known** patterns. Intelligent-Tiering is for **unknown/changing** patterns.
- **Exam trigger:** "Transition after N days," "delete after retention period." Transcript example: Standard → Standard-IA at **5 days** → Glacier Deep Archive at **120 days** → delete at **5 years**.

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Data profiling**|Activity that surfaces data quality issues|
|**Data steward**|Receives source-issue reports. Enables role-based and temporary access per the owner's policy|
|**Data owner**|Makes policy decisions. Works with security and legal teams on sensitive domains|
|**AWS Glue Data Catalog**|Metadata store: locations, schemas, data types, table definitions|
|**AWS Glue crawler job**|Scans data sources and populates the catalog automatically|
|**AWS Glue Data Quality**|No-code rule setup, rule recommendations, ML anomaly detection on cataloged objects|
|**AWS Lake Formation**|Fine-grained (column/row/cell) access control for an S3 data lake|
|**Data lifecycle management**|Intentional storage for straightforward access and optimized cost|
|**S3 Intelligent-Tiering**|For unknown or changing access patterns. Auto-moves objects to infrequent-access tiers|
|**S3 Glacier**|Rarely accessed, long-term archive for retention/compliance|
|**Lifecycle rule**|Bucket rule: target storage class + days after creation, optionally deletion|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Glue Data Catalog**|You need to store metadata (locations, schemas, tables)|Metadata only. Populated manually or by a crawler|
|**Glue Data Quality**|You need rules/anomaly detection on cataloged data, especially for non-coders|Evaluates objects **in the Data Catalog** and reports rule pass/fail|
|**Lake Formation**|You need column/row/cell-level permissions on an S3 data lake|Access control layer. The Data Catalog checks with it before granting access|
|**S3 Intelligent-Tiering**|Access patterns are unknown or changing|Automatic movement to lower-cost tiers|
|**S3 lifecycle rule**|Access patterns are known|You define target class and days after creation|
|**S3 Standard-IA / One Zone-IA**|Infrequent access, but quick retrieval needed|Cheaper storage, costlier retrieval than Standard|
|**S3 Glacier**|Rarely accessed, compliance retention|Multiple classes offer different retrieval speeds|
|**Data owner**|Deciding policy for sensitive data|Sets policy with security and legal teams|
|**Data steward**|Implementing access and handling source data issues|Enables role-based and temporary access per the owner's policy|

---

## 🧠 Exam Traps

### **1.**

**Trap:** The data steward decides who gets access to sensitive data.

**Correct:** The **data owner** makes the policy decisions. The **data steward** enables role-based and temporary access guided by those decisions.

### **2.**

**Trap:** Data quality problems traced to the source should be fixed downstream in the pipeline.

**Correct:** If the problem involves the source, **alert and report** it to the **data steward and business users** who can correct it.

### **3.**

**Trap:** Glue Data Quality and the Glue Data Catalog do the same job.

**Correct:** The Catalog stores **metadata**. Glue Data Quality **evaluates objects stored in the Catalog** against rules.

### **4.**

**Trap:** Lake Formation permissions apply only at the table level.

**Correct:** They are enforced at the **column, row, and cell** levels.

### **5.**

**Trap:** Use Intelligent-Tiering whenever you want to save cost.

**Correct:** Intelligent-Tiering fits **unknown or changing** access patterns. If you **know** the pattern, create **lifecycle rules**.

### **6.**

**Trap:** Standard-IA is cheaper than Standard on every dimension.

**Correct:** Storage is cheaper, but **retrieval is more costly** than S3 Standard.

### **7.**

**Trap:** Compliance is a purely technical decision made by engineers or the steward.

**Correct:** Data owners work with **security and legal teams**. The rules need **interpretation and judgment**.

### **8.**

**Trap:** Stronger governance always means locking data down.

**Correct:** Governance is a **balance**. Too much control creates silos, and too little puts data and business at risk.

---

# 📝 Exam Questions

### **Question 1**

A company stores training data in Amazon S3. Access to the data is unpredictable: some months it is queried heavily, and other months it is untouched. The company does not want to manually predict when to move objects to lower-cost tiers. Which S3 option best fits?

A. S3 lifecycle rule transitioning to S3 Standard-IA after 30 days  
B. S3 One Zone-IA  
C. S3 Intelligent-Tiering  
D. S3 Glacier

**Answer: C — S3 Intelligent-Tiering**

**Why:** Intelligent-Tiering is for **unknown or changing access patterns** and automatically moves less-accessed objects to lower-cost tiers. A lifecycle rule (A) requires known patterns.

---

### **Question 2**

A data team wants a no-code way to define quality rules against tables that are registered in their catalog. They also want the service to suggest rules and use machine learning to flag anomalies. Which capability meets this?

A. AWS Glue crawler job  
B. AWS Glue Data Quality  
C. AWS Lake Formation  
D. AWS Glue Data Catalog

**Answer: B — AWS Glue Data Quality**

**Why:** It offers non-coders a way to set up rules, recommends rules, and uses ML for anomaly detection. The crawler and Catalog handle metadata. Lake Formation handles access control.

---

### **Question 3**

An analyst queries a data lake through Amazon Athena. The company needs users in a customer-service role to see only specific columns and rows. Which mechanism enforces this when the query runs?

A. The AWS Glue Data Catalog checks permissions with AWS Lake Formation before granting access  
B. An AWS Glue crawler job filters the columns at scan time  
C. S3 lifecycle rules restrict the visible objects  
D. AWS Glue Data Quality rules block the columns

**Answer: A — The AWS Glue Data Catalog checks permissions with AWS Lake Formation before granting access**

**Why:** Integrated engines go through the Data Catalog, which checks Lake Formation permissions (column, row, cell) before granting access.

---

### **Question 4**

A data profiling exercise shows that a field is repeatedly populated incorrectly. Investigation shows the errors originate in the upstream source system. What is the most appropriate action?

A. Add an AWS Glue Data Quality anomaly rule and ignore the source  
B. Alert and report the issue to the data steward and business users who can correct the source  
C. Move the data to S3 Glacier to prevent further use  
D. Have the data owner remove the field from the catalog

**Answer: B — Alert and report the issue to the data steward and business users who can correct the source**

**Why:** Source-related quality problems are reported to those who can fix them. Rules can detect the problem but don't resolve its root cause.

---

### **Question 5**

A company must retain model training data for several years for compliance. The data will rarely, if ever, be accessed, and it can be retrieved on demand, with retrieval speed varying by option. Which storage choice best fits?

A. S3 Standard-IA  
B. S3 One Zone-IA  
C. S3 Intelligent-Tiering  
D. An S3 Glacier storage class

**Answer: D — An S3 Glacier storage class**

**Why:** Glacier classes are for rarely accessed data kept in a long-term archive for retention or compliance. IA classes are for infrequent access that still needs quick retrieval.

---

### **Question 6**

A company's customer-service team needs temporary, role-based access to certain customer data. Who typically enables that access, and under whose policy decisions?

A. Data owner enables it, guided by the data steward  
B. Data steward enables it, guided by the data owner's policy decisions  
C. Security team enables it, guided by the data steward  
D. Business users enable it, guided by Lake Formation

**Answer: B — Data steward enables it, guided by the data owner's policy decisions**

**Why:** The steward helps enable role-based and temporary access, following policies established by the owner.

---

### **Question 7**

An organization knows its data is accessed heavily for the first few days, rarely afterward, and never needed after five years. It wants automated transitions and eventual deletion at defined times. What best fits?

A. S3 Intelligent-Tiering  
B. S3 lifecycle rules with target storage classes and days after creation  
C. S3 One Zone-IA only  
D. AWS Glue Data Quality rules

**Answer: B — S3 lifecycle rules with target storage classes and days after creation**

**Why:** With known patterns, lifecycle rules specify the target class and the number of days, and can delete data at the end of retention.

---

### **Question 8**

A team wants to keep sensitive data protected but is concerned that heavy restrictions have left data trapped in departmental silos and blocked insight generation. Which governance principle does this describe?

A. Too much control reduces access and creates silos  
B. Insufficient control creates business risk  
C. Poor data integration between sources  
D. Weak data lifecycle management

**Answer: A — Too much control reduces access and creates silos**

**Why:** Governance is a balance between control and access. Excess control locks data in silos.

---

### **Question 9**

A company wants to automatically discover the schemas and table definitions of its S3 and database sources and register them without manual entry. Which is the best fit?

A. AWS Glue Data Quality job  
B. AWS Lake Formation permissions  
C. AWS Glue crawler job populating the Data Catalog  
D. S3 lifecycle rule

**Answer: C — AWS Glue crawler job populating the Data Catalog**

**Why:** A crawler scans data sources and populates the Catalog automatically. The Catalog can also be populated manually.

---

# ⚡ 30-Second Revision

1. **Data quality issue at the source → report to the data steward and business users**, not fixed downstream.
2. **Data owner = policy decisions** (with security and legal for compliance). **Data steward = enables role-based, temporary access**.
3. **Glue Data Catalog = metadata** (locations, schemas, data types, tables). **Crawler = automatic population**.
4. **Glue Data Quality = no-code rules, rule recommendations, ML anomaly detection**, run as a job, results show pass/fail.
5. **Lake Formation = column, row, and cell-level access control** for an S3 data lake. The Data Catalog checks with it before Athena, Glue, EMR, or Redshift get access.
6. **Governance = balance of control vs. access.** Too much → silos. Too little → risk.
7. **S3 Standard** = frequent. **Standard-IA / One Zone-IA** = infrequent but quick retrieval (cheaper storage, costlier retrieval). **Intelligent-Tiering** = unknown/changing. **Glacier** = rarely accessed archive for compliance.
8. **Known access pattern → lifecycle rules** (target class + days after creation, optional delete). Transcript example: Standard-IA at 5 days, Glacier Deep Archive at 120 days, delete at 5 years.