# Domain 5 — Task Statement 5.2: Recognize governance and compliance regulations for AI systems

## 🎯 Exam Essentials

### **1. Data Governance**

- **Concept:** **Data governance** is the combination of **people, process, and technology** used to manage the **availability, usability, integrity, and security** of enterprise data.
    
- **Key distinction:** Effective data governance aims to keep data **consistent and trustworthy** while preventing misuse.
    
- **Exam trigger:** A question asks about managing enterprise data through people, processes, and technology → **data governance**.
    

### **2. Three Major Parts of Data Governance**

- **Concept:** The transcript divides data governance into three major areas: **curation, discovery and understanding, and protection**.
    
- **Key distinction:** These cover managing valuable data, understanding its meaning and context, and balancing privacy/security/access.
    
- **Exam trigger:** Remember the three-part structure: **Curation → Discovery & Understanding → Protection**.
    

### **3. Data Curation**

- **Concept:** Data curation at scale means identifying and managing valuable data sources such as **databases, data lakes, and data warehouses**.
    
- **Key distinction:** Curation helps limit the proliferation and transformation of critical data assets.
    
- **Exam trigger:** Identifying and managing important enterprise data sources → **data curation**.
    

### **4. Data Quality Through Curation**

- **Concept:** Curating data also involves ensuring that data is **accurate, fresh, and free of sensitive information**.
    
- **Key distinction:** High-quality curated data increases confidence in data-driven decisions.
    
- **Exam trigger:** Data must be accurate, current, and appropriately handled before business decisions → **data curation/governance**.
    

### **5. Data Discovery and Understanding**

- **Concept:** Understanding data in context means allowing users to **discover and comprehend the meaning of their data** so they can use it confidently.
    
- **Key distinction:** The objective is not merely finding data, but understanding what the data means and how it can support business value.
    
- **Exam trigger:** Users need to find data and understand its meaning before using it → **discovery and understanding**.
    

### **6. Centralized Data Catalog**

- **Concept:** A **centralized data catalog** makes data easier to find.
    
- **Key distinction:** It allows users to discover data, request access, and use the data for business decisions.
    
- **Exam trigger:** “Users need to discover available datasets and request access” → **data catalog**.
    

### **7. Data Protection**

- **Concept:** Data protection involves balancing **data privacy, security, and access**.
    
- **Key distinction:** Effective governance must protect data without unnecessarily preventing legitimate access.
    
- **Exam trigger:** A scenario requires balancing privacy/security requirements with authorized data access → **data protection/governance**.
    

### **8. Data Governance as a Strategic Asset**

- **Concept:** Data governance treats organizational data as a **strategic asset**.
    
- **Key distinction:** Organizations need competencies, authority, and controls to use that asset effectively while meeting stakeholder expectations.
    
- **Exam trigger:** Data is being treated as an organizational asset requiring authority and control → **data governance**.
    

### **9. Data Domains**

- **Concept:** Organizations should start with the **data domains necessary to succeed with targeted business initiatives**.
    
- **Key distinction:** Governance should be connected to specific business priorities rather than attempting to govern every possible dataset simultaneously.
    
- **Exam trigger:** Deciding where to begin a governance program → focus on **data domains necessary for targeted initiatives**.
    

### **10. Data Governance Roles**

- **Concept:** Key data governance roles include **data owners, data stewards, and IT**.
    
- **Key distinction:** These roles have different responsibilities across policy, day-to-day data work, and technical systems/tools.
    
- **Exam trigger:** A question asks who should perform a particular governance responsibility → identify the role based on its responsibility.
    

### **11. Segregation of Duties**

- **Concept:** Organizations should consider **segregation of duties** when assigning governance responsibilities.
    
- **Key distinction:** Appropriate responsibilities should be assigned to appropriate individuals rather than concentrating incompatible responsibilities in one person.
    
- **Exam trigger:** Governance roles are being assigned and the scenario emphasizes separation of responsibilities → **segregation of duties**.
    

### **12. Data Steward**

- **Concept:** A **data steward** is a business person with detailed knowledge of the data needed to support targeted business initiatives.
    
- **Key distinction:** Data stewards are involved in the **day-to-day details of projects** and help identify data issues that could create challenges.
    
- **Exam trigger:** Business-level person handling day-to-day data issues and detailed data knowledge → **data steward**.
    

### **13. Data Owner**

- **Concept:** A **data owner** is an executive-level person who makes data policy decisions, including **regulatory and compliance policies**.
    
- **Key distinction:** The data owner determines policies such as **who should have access to particular types of data**.
    
- **Exam trigger:** Executive deciding data access policies or regulatory/compliance policies → **data owner**.
    

### **14. Data Owner vs. Data Steward**

- **Concept:** The data owner establishes policies that guide the work performed by the data steward.
    
- **Key distinction:** **Data owner = policy and authority. Data steward = day-to-day execution and detailed data knowledge.**
    
- **Exam trigger:** If the question asks who sets the policy → **owner**. If it asks who handles day-to-day data work → **steward**.
    

### **15. IT Role in Data Governance**

- **Concept:** IT roles help navigate systems that **produce and consume data** and provide data stewards with appropriate tools and capabilities.
    
- **Key distinction:** IT supports the technical implementation of governance rather than owning the business policies described for data owners.
    
- **Exam trigger:** Managing or deploying data governance tools in AWS → **IT role**.
    

### **16. Data Profiling**

- **Concept:** **Data profiling** systematically examines data to determine whether anything is wrong and to understand its characteristics.
    
- **Key distinction:** Profiling focuses on understanding the existing characteristics and quality of the dataset.
    
- **Exam trigger:** Systematically examining a dataset for problems and characteristics → **data profiling**.
    

### **17. Data Catalog vs. Data Profiling**

- **Concept:** A **data catalog** makes data available and discoverable for people who need access, while **data profiling** examines the data itself.
    
- **Key distinction:** **Catalog = find/access data. Profiling = examine data characteristics and potential problems.**
    
- **Exam trigger:** “Where can I find the dataset?” → catalog. “What is wrong with this dataset?” → profiling.
    

### **18. Data Lineage**

- **Concept:** **Data lineage** identifies where specific data elements originated and how they were **moved, transformed, and stored**.
    
- **Key distinction:** Lineage provides the history and flow of data through different entities.
    
- **Exam trigger:** A user asks where reported data originated or what transformations occurred → **data lineage**.
    

### **19. AWS Glue DataBrew**

- **Concept:** **AWS Glue DataBrew** is a visual data preparation tool that allows users to **clean and normalize data without writing code**.
    
- **Key distinction:** In this transcript, DataBrew is particularly relevant to governance because of its **data profiling and data lineage** capabilities.
    
- **Exam trigger:** No-code visual data preparation plus profiling/lineage → **AWS Glue DataBrew**.
    

### **20. DataBrew Data Profiling**

- **Concept:** DataBrew can run **profiling jobs** against a dataset to create a data profile.
    
- **Key distinction:** The profile describes the existing shape of the data, including the **content context, structure, and relationships**.
    
- **Exam trigger:** Need a visual profile describing dataset characteristics → **DataBrew data profile**.
    

### **21. Data Quality Rules in DataBrew**

- **Concept:** DataBrew allows users to define **data quality rules** that are validated during profiling.
    
- **Key distinction:** These rules help detect problems with the data during the profiling process.
    
- **Exam trigger:** Dataset must be checked against defined quality requirements → **DataBrew data quality rules**.
    

### **22. DataBrew Supported Data Sources**

- **Concept:** DataBrew can analyze datasets stored in **Amazon S3**, relational databases, and data warehouses.
    
- **Key distinction:** DataBrew's profiling capability can operate across multiple types of data sources.
    
- **Exam trigger:** Scenario involves profiling data from S3, relational databases, or data warehouses → **DataBrew**.
    

### **23. DataBrew Data Lineage**

- **Concept:** DataBrew provides a visual representation of **data lineage** showing how data flows through different entities from its origin.
    
- **Key distinction:** The lineage view can show the data's origin, entities that influenced it, what happened to it over time, and where it was stored.
    
- **Exam trigger:** Need to trace data from origin through transformations and storage → **DataBrew data lineage**.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Data governance**|People, processes, and technology used to manage enterprise data availability, usability, integrity, and security.|
|**Data curation**|Identifying and managing valuable data sources while controlling critical data assets.|
|**Data discovery**|Finding available data and understanding where it can be accessed.|
|**Data understanding**|Comprehending the meaning and context of data.|
|**Data protection**|Balancing privacy, security, and access.|
|**Data domain**|Area of data relevant to a targeted business initiative.|
|**Data owner**|Executive-level role responsible for data policy decisions.|
|**Data steward**|Business role with detailed data knowledge and day-to-day data responsibilities.|
|**Data profiling**|Systematic examination of data characteristics and potential problems.|
|**Data catalog**|Centralized mechanism for discovering and accessing data.|
|**Data lineage**|Origin and movement/transformation history of data.|
|**AWS Glue DataBrew**|Visual, no-code data preparation tool with profiling and lineage capabilities described in the transcript.|
|**Data profile**|Description of the shape, context, structure, and relationships within a dataset.|
|**Data quality rule**|Rule validated during profiling to detect data problems.|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Data curation**|Managing valuable enterprise data sources|Focuses on managing critical data assets|
|**Data discovery & understanding**|Finding and comprehending data|Focuses on meaning, context, and accessibility|
|**Data protection**|Securing and governing access to data|Balances privacy, security, and access|
|**Data owner**|Setting organizational data policies|Executive-level policy authority|
|**Data steward**|Managing day-to-day data activities|Detailed business/data knowledge|
|**IT**|Supporting governance technology|Manages/deploys governance tools and systems|
|**Data catalog**|Finding and accessing datasets|Discovery and access|
|**Data profiling**|Examining dataset characteristics|Identifies problems and describes data|
|**Data lineage**|Tracing data origins and transformations|Shows data flow/history|
|**DataBrew profiling**|Creating a data profile|Examines data characteristics and validates quality rules|
|**DataBrew lineage**|Understanding data origin and flow|Visualizes how data moves through entities|

---

# 🧠 Exam Traps

### **1. Data governance is only about security.**

- **Trap:** Assuming governance means protecting data from unauthorized access only.
    
- **Correct:** Data governance combines **people, process, and technology** to manage availability, usability, integrity, and security.
    

### **2. Data governance has only two parts: security and access.**

- **Trap:** Reducing governance to protection.
    
- **Correct:** The transcript identifies **curation, discovery and understanding, and protection** as the three major parts.
    

### **3. Data curation means simply storing data.**

- **Trap:** Treating curation as basic data storage.
    
- **Correct:** Curation involves identifying and managing valuable data sources and controlling proliferation/transformation of critical data assets.
    

### **4. A data catalog examines whether data is accurate.**

- **Trap:** Confusing cataloging with profiling.
    
- **Correct:** A **data catalog** makes data discoverable and accessible; **data profiling** examines the data and its characteristics.
    

### **5. Data lineage tells users where they can access a dataset.**

- **Trap:** Confusing lineage with discovery.
    
- **Correct:** Lineage identifies where data originated and how it was **moved, transformed, and stored**.
    

### **6. The data steward is the executive who sets data policy.**

- **Trap:** Reversing owner and steward responsibilities.
    
- **Correct:** The **data owner** makes policy decisions; the **data steward** handles day-to-day data activities and has detailed data knowledge.
    

### **7. The data owner performs all daily data-management tasks.**

- **Trap:** Assuming the executive owner handles operational work.
    
- **Correct:** The **data steward** performs day-to-day project data work under policies established by the data owner.
    

### **8. IT owns the organization's data policies.**

- **Trap:** Treating IT as the policy authority.
    
- **Correct:** The transcript assigns **data policy decisions** to the data owner; IT helps manage systems and governance tools.
    

### **9. Data profiling and data lineage are the same thing.**

- **Trap:** Both involve examining data, so they can appear interchangeable.
    
- **Correct:** **Profiling** examines data characteristics and problems; **lineage** traces origin, movement, transformation, and storage.
    

### **10. DataBrew requires writing code for data preparation.**

- **Trap:** Assuming AWS Glue DataBrew is a code-first data-processing service.
    
- **Correct:** The transcript describes DataBrew as a **visual data preparation tool** for cleaning and normalizing data **without writing code**.
    

### **11. DataBrew lineage only shows the original data source.**

- **Trap:** Limiting lineage to the starting point.
    
- **Correct:** The visual lineage can show the **origin, influencing entities, changes over time, and storage location**.
    

### **12. Data quality rules are separate from DataBrew profiling.**

- **Trap:** Assuming profiling only describes data.
    
- **Correct:** DataBrew can validate **data quality rules during profiling** to detect problems.
    

---

# 📝 Exam Questions

### **Question 1**

An organization wants to establish a program that combines people, processes, and technology to ensure enterprise data remains available, usable, trustworthy, and secure while preventing misuse.

Which concept best describes this program?

A. Data lineage

B. Data governance

C. Data profiling

D. Data curation

**Answer: B — Data governance**

**Why:** Data governance combines **people, process, and technology** to manage enterprise data availability, usability, integrity, and security.

---

### **Question 2**

A company wants to make datasets easier for employees to discover and understand before they use them for business decisions. It also wants employees to be able to request access to the data.

Which capability most directly addresses this requirement?

A. Data lineage

B. Data profiling

C. Centralized data catalog

D. Data quality rules

**Answer: C — Centralized data catalog**

**Why:** The transcript describes a centralized data catalog as making data easier to find, allowing access to be requested, and supporting business use.

---

### **Question 3**

A business unit needs an individual who understands the detailed characteristics of its data and works with data-related issues during projects every day.

Which governance role best matches this responsibility?

A. Data owner

B. Data steward

C. Executive auditor

D. IT policy owner

**Answer: B — Data steward**

**Why:** A data steward is a business person with detailed knowledge of relevant data who participates in **day-to-day project activities**.

---

### **Question 4**

An executive must decide which employees should have access to claims data and customer data and must establish policies related to regulatory and compliance requirements.

Which role should make these decisions?

A. Data steward

B. IT administrator

C. Data owner

D. Data catalog administrator

**Answer: C — Data owner**

**Why:** The transcript defines the **data owner** as an executive-level person responsible for data policy decisions, including regulatory and compliance policies.

---

### **Question 5**

A data consumer sees a value in a business report and wants to know where the underlying data originated, which entities influenced it, what transformations occurred, and where the data was stored.

Which capability should the consumer use?

A. Data catalog

B. Data profiling

C. Data lineage

D. Data curation

**Answer: C — Data lineage**

**Why:** Data lineage traces the **origin, movement, transformation, and storage** of data.

---

### **Question 6**

A data engineering team wants to examine a dataset systematically to identify problems and understand its structure, content context, and relationships. It also wants to validate predefined data quality rules during this process.

Which capability best matches the requirement?

A. DataBrew data profiling

B. DataBrew data lineage

C. Centralized data catalog

D. Data owner policy management

**Answer: A — DataBrew data profiling**

**Why:** DataBrew profiling jobs create a data profile describing the data's characteristics and can validate **data quality rules** during profiling.

---

### **Question 7**

An organization wants to balance data privacy and security with legitimate access so that data remains protected without preventing authorized users from using it.

Which major area of data governance does this describe?

A. Curation

B. Discovery and understanding

C. Protection

D. Data profiling

**Answer: C — Protection**

**Why:** The transcript describes data protection as striking the right balance between **privacy, security, and access**.

---

### **Question 8**

A company wants to understand how a dataset moved from its original source through multiple processing entities and where it was ultimately stored. The company wants to view this flow visually without writing code.

Which AWS capability described in the lesson should it use?

A. AWS Glue DataBrew data lineage

B. AWS Glue DataBrew data catalog

C. AWS Config configuration history

D. Amazon Inspector

**Answer: A — AWS Glue DataBrew data lineage**

**Why:** DataBrew provides a visual lineage view showing the data's **origin, influencing entities, changes over time, and storage**.

---

### **Question 9**

A company is assigning data governance responsibilities and wants to ensure that incompatible responsibilities are not concentrated in one person.

Which principle should the organization consider?

A. Data proliferation

B. Segregation of duties

C. Data profiling

D. Centralized cataloging

**Answer: B — Segregation of duties**

**Why:** The transcript explicitly says to take **segregation of duties** into account when assigning governance roles.

---

### **Question 10**

An organization wants to clean and normalize datasets through a visual interface without writing code. The same team also wants to create data profiles and examine lineage.

Which AWS service described in the lesson best matches these requirements?

A. AWS Glue DataBrew

B. AWS Audit Manager

C. AWS Config

D. AWS Trusted Advisor

**Answer: A — AWS Glue DataBrew**

**Why:** DataBrew is described as a **visual, no-code data preparation tool** with data profiling and lineage capabilities relevant to governance.

---

### **Question 11**

A governance team is deciding which data to prioritize for a new business initiative. It wants to focus its governance program on the data areas necessary to achieve the initiative's objectives.

What approach matches the lesson?

A. Govern every organizational dataset equally before beginning the initiative.

B. Start with the data domains necessary for the targeted business initiatives.

C. Start exclusively with datasets stored in Amazon S3.

D. Begin by assigning all governance responsibilities to IT.

**Answer: B — Start with the data domains necessary for the targeted business initiatives.**

**Why:** The transcript recommends starting with the **data domains necessary to succeed with targeted business initiatives**.

---

# ⚡ 30-Second Revision

1. **Data governance = people + process + technology.**
    
2. Goal → **availability + usability + integrity + security**.
    
3. Three parts → **Curation + Discovery/Understanding + Protection**.
    
4. **Curation → manage valuable data sources and critical data assets.**
    
5. **Discovery/Understanding → find and comprehend data.**
    
6. **Protection → balance privacy, security, and access.**
    
7. **Data owner → executive-level policy authority.**
    
8. **Data steward → detailed data knowledge + day-to-day work.**
    
9. **IT → systems + governance tools/capabilities.**
    
10. **Data catalog → discover/access data.**
    
11. **Data profiling → examine data characteristics/problems.**
    
12. **Data lineage → origin + movement + transformation + storage.**
    
13. **DataBrew → visual, no-code data preparation.**
    
14. **DataBrew profiling → data profile + quality-rule validation.**
    
15. **DataBrew lineage → visual data flow from origin through entities.**
    
16. **Segregation of duties → consider when assigning governance roles.**