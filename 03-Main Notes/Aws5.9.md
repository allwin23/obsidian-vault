# Domain 5 — Task Statement 5.2: Recognize governance and compliance regulations for AI systems

## 🎯 Exam Essentials

### **1. AWS Services for Customer Compliance**

- **Concept:** AWS provides services and features that help customers **audit, monitor, control, and report** on security controls that customers are responsible for configuring correctly.
    
- **Key distinction:** AWS provides the tools, but customers remain responsible for correctly configuring the controls relevant to their workloads.
    
- **Exam trigger:** A scenario asks which AWS capability helps a customer demonstrate or continuously assess compliance → identify whether the need is **audit, configuration monitoring, vulnerability assessment, safeguards, or best-practice recommendations**.
    

### **2. AWS Audit Manager**

- **Concept:** **AWS Audit Manager** maps compliance requirements to AWS usage data, collects evidence of compliance or noncompliance, and produces **assessment reports** that can be provided to auditors.
    
- **Key distinction:** Audit Manager is focused on **collecting and organizing compliance evidence** for assessments and audits.
    
- **Exam trigger:** “Collect evidence,” “assessment report,” “auditor,” or “demonstrate controls are working” → **AWS Audit Manager**.
    

### **3. Audit Manager Frameworks**

- **Concept:** An Audit Manager **framework** is a grouping of controls related to an audit.
    
- **Key distinction:** The assessment is created based on a selected framework.
    
- **Exam trigger:** A question asks what defines the collection of controls used for an Audit Manager assessment → **framework**.
    

### **4. Built-in Audit Manager Frameworks**

- **Concept:** Audit Manager includes built-in frameworks, including frameworks for **generative AI best practices** and **SOC 2**.
    
- **Key distinction:** Customers can use predefined frameworks rather than building every compliance framework from scratch.
    
- **Exam trigger:** Generative AI compliance assessment or SOC 2 controls using Audit Manager → consider its **built-in frameworks**.
    

### **5. Custom Audit Manager Frameworks**

- **Concept:** Customers can define their own **custom framework** tailored to the controls they specifically want to assess.
    
- **Key distinction:** Audit Manager supports both built-in frameworks and customer-defined frameworks.
    
- **Exam trigger:** Organization has unique controls not covered by a predefined framework → **custom framework**.
    

### **6. Audit Manager Assessment Workflow**

- **Concept:** When an assessment is created, Audit Manager automatically assesses resources in AWS accounts and services according to the controls defined in the selected framework.
    
- **Key distinction:** Audit Manager then collects relevant evidence, converts it into an **auditor-friendly format**, and attaches the evidence to the appropriate controls.
    
- **Exam trigger:** Scenario describes automatic evidence collection and attaching evidence to controls → **Audit Manager assessment**.
    

### **7. Audit Manager Assessment Reports**

- **Concept:** Before an audit, customers can review collected evidence and add it to an **assessment report**.
    
- **Key distinction:** The report helps demonstrate that the customer's controls are **working as intended**.
    
- **Exam trigger:** “Prepare evidence for an auditor” or “demonstrate controls are functioning” → **Audit Manager assessment report**.
    

### **8. Amazon Bedrock Guardrails**

- **Concept:** **Guardrails for Amazon Bedrock** provides application-specific safeguards based on the application's use cases and responsible AI policies.
    
- **Key distinction:** Guardrails operates around **user inputs and foundation model (FM) responses** to help prevent unwanted interactions.
    
- **Exam trigger:** A Bedrock application needs content filtering, denied topics, or PII handling → **Guardrails for Amazon Bedrock**.
    

### **9. Guardrails Content Filters**

- **Concept:** Guardrails provides configurable thresholds for filtering harmful content across categories including **hate, insults, sexual, and violence**.
    
- **Key distinction:** The thresholds can be configured according to the application's requirements.
    
- **Exam trigger:** Application needs to filter harmful content by category → **Guardrails content filters**.
    

### **10. Guardrails Denied Topics**

- **Concept:** Guardrails allows developers to define **topics to avoid** within an application's context using short natural-language descriptions.
    
- **Key distinction:** Example phrases can optionally be provided to help Guardrails recognize the restricted topics.
    
- **Exam trigger:** A company wants its model to avoid a specific subject such as investment advice → define a **denied topic**.
    

### **11. Guardrails Input and Output Filtering**

- **Concept:** Guardrails can detect and block restricted content in both **user inputs and FM responses**.
    
- **Key distinction:** Guardrails evaluates both sides of the interaction rather than only checking what the user sends.
    
- **Exam trigger:** The requirement includes filtering both prompts and generated responses → **Guardrails**.
    

### **12. Guardrails PII Detection**

- **Concept:** Guardrails can detect **personally identifiable information (PII)** in user inputs and FM responses.
    
- **Key distinction:** Depending on the use case, the application can selectively **reject inputs containing PII** or **redact PII in FM responses**.
    
- **Exam trigger:** PII detection, rejection, or redaction around a Bedrock application → **Guardrails**.
    

### **13. Guardrails Blocked-Interaction Messages**

- **Concept:** Guardrails allows separate messages to be configured for when a **prompt is blocked** and when a **model response is blocked**.
    
- **Key distinction:** The two situations can have different responses.
    
- **Exam trigger:** Scenario asks for different user-facing messages depending on whether input or output was blocked → **Guardrails blocked-input/blocked-output messages**.
    

### **14. AWS Config**

- **Concept:** **AWS Config** provides a detailed inventory of the current configuration of AWS resources.
    
- **Key distinction:** AWS Config operates primarily at the **resource configuration level**.
    
- **Exam trigger:** A question asks about tracking resource configurations or detecting configuration changes → **AWS Config**.
    

### **15. AWS Config Configuration History**

- **Concept:** When a resource configuration changes, AWS Config captures and records the change in a **configuration history snapshot**.
    
- **Key distinction:** This allows changes to resource configurations to be tracked over time.
    
- **Exam trigger:** “Who changed the resource configuration?” or “track configuration changes over time” → consider **AWS Config configuration history**.
    

### **16. AWS Config Rules**

- **Concept:** AWS Config evaluates resource configuration changes using **configuration rules**.
    
- **Key distinction:** Rules determine whether the current configuration complies with the specified requirements.
    
- **Exam trigger:** Resource configuration must be evaluated for compliance → **AWS Config rules**.
    

### **17. AWS Config Automatic Remediation**

- **Concept:** If a configuration change is noncompliant with a rule, it can be **automatically remediated** using an **AWS Systems Manager automation document**.
    
- **Key distinction:** AWS Config detects/evaluates the configuration issue, while Systems Manager automation can perform the remediation.
    
- **Exam trigger:** “Automatically fix a noncompliant AWS resource configuration” → **AWS Config + Systems Manager automation document**.
    

### **18. AWS Config Prebuilt and Custom Rules**

- **Concept:** Customers can use **prebuilt AWS Config rules** or create custom rules using an **AWS Lambda function**.
    
- **Key distinction:** Prebuilt rules provide ready-made checks; custom rules allow organization-specific compliance logic.
    
- **Exam trigger:** Need a compliance rule that doesn't exist as a predefined rule → **custom AWS Config rule using Lambda**.
    

### **19. AWS Config Conformance Packs**

- **Concept:** **Conformance packs** package AWS Config rules and remediation actions together to help deploy controls and remediations for compliance requirements.
    
- **Key distinction:** Instead of managing individual rules and remediations separately, a conformance pack groups them into a deployable collection.
    
- **Exam trigger:** Multiple AWS Config rules and remediation actions need to be packaged together → **conformance pack**.
    

### **20. Conformance Pack Templates**

- **Concept:** Customers can create their own conformance packs or select from a **library of conformance pack templates**.
    
- **Key distinction:** Templates provide predefined collections that can be used to address compliance needs.
    
- **Exam trigger:** Organization wants a ready-made collection of Config rules and remediations → **conformance pack template**.
    

### **21. AI/ML Conformance Packs**

- **Concept:** The transcript identifies two useful conformance packs:
    
    - **Operational best practices for AI and ML**
        
    - **Security best practices for Amazon SageMaker**
        
- **Key distinction:** These provide collections of configuration controls relevant to AI/ML or SageMaker security best practices.
    
- **Exam trigger:** AI/ML configuration compliance through AWS Config → consider these **AI/ML conformance packs**.
    

### **22. AWS Config vs. Amazon Inspector**

- **Concept:** **AWS Config monitors configurations at the resource level**, while **Amazon Inspector works at the application level**.
    
- **Key distinction:** Config focuses on **resource configuration compliance**; Inspector focuses on **application/container security vulnerabilities and deviations from security best practices**.
    
- **Exam trigger:** First determine whether the problem concerns **resource configuration** or **application/container vulnerabilities**.
    

### **23. Amazon Inspector**

- **Concept:** **Amazon Inspector** checks applications and containers for security vulnerabilities and deviations from security best practices.
    
- **Examples:** Open access to EC2 instances and vulnerable software versions.
    
- **Key distinction:** Inspector performs automated security assessments at the application level.
    
- **Exam trigger:** Vulnerable software, application/container vulnerabilities, or security findings → **Amazon Inspector**.
    

### **24. Amazon Inspector Security Assessments**

- **Concept:** Amazon Inspector runs **automated security assessments** to help improve application security and compliance.
    
- **Key distinction:** After an assessment, Inspector provides security findings rather than a general compliance evidence report.
    
- **Exam trigger:** Automated vulnerability/security assessment → **Amazon Inspector**.
    

### **25. Amazon Inspector Findings**

- **Concept:** Inspector produces a list of **security findings** after an assessment.
    
- **Key distinction:** Findings are prioritized by **severity level** and include descriptions of security issues and recommendations for remediation.
    
- **Exam trigger:** Scenario asks for prioritized security vulnerabilities and remediation recommendations → **Inspector findings**.
    

### **26. AWS Trusted Advisor**

- **Concept:** **AWS Trusted Advisor** evaluates an AWS environment against best practices.
    
- **Key distinction:** It provides recommendations to optimize the AWS environment across multiple operational areas rather than serving specifically as a compliance evidence collection service.
    
- **Exam trigger:** A question asks for AWS best-practice checks and recommendations across cost, performance, resilience, security, operational excellence, and service limits → **Trusted Advisor**.
    

### **27. Trusted Advisor Categories**

- **Concept:** Trusted Advisor continuously evaluates the environment using best-practice checks across:
    
    - **Cost optimization**
        
    - **Performance**
        
    - **Resilience**
        
    - **Security**
        
    - **Operational excellence**
        
    - **Service limits**
        
- **Key distinction:** Trusted Advisor spans multiple operational dimensions.
    
- **Exam trigger:** Multiple AWS optimization/best-practice categories in one scenario → **Trusted Advisor**.
    

### **28. Trusted Advisor Remediation Recommendations**

- **Concept:** Trusted Advisor recommends actions to remediate deviations from AWS best practices.
    
- **Key distinction:** It identifies deviations and provides recommended actions rather than functioning as the primary compliance evidence repository.
    
- **Exam trigger:** “AWS environment deviates from best practices; what service recommends corrective actions?” → **Trusted Advisor**.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**AWS Audit Manager**|Collects compliance evidence and produces assessment reports for auditors.|
|**Framework**|Grouping of controls related to an audit.|
|**Assessment**|Audit Manager evaluation based on a selected framework.|
|**Assessment report**|Auditor-friendly report demonstrating evidence about controls.|
|**Guardrails for Amazon Bedrock**|Application-specific safeguards for Bedrock use cases and responsible AI policies.|
|**Content filter**|Guardrails mechanism for filtering harmful content using configurable thresholds.|
|**Denied topic**|Topic defined in Guardrails that the application should avoid.|
|**PII detection**|Guardrails capability for detecting personally identifiable information in inputs and outputs.|
|**AWS Config**|Resource configuration inventory and compliance monitoring service.|
|**Configuration history**|Record of resource configuration changes captured by AWS Config.|
|**Config rule**|Rule used to evaluate resource configurations for compliance.|
|**Systems Manager automation document**|Mechanism identified in the transcript for automatically remediating noncompliant Config findings.|
|**Conformance pack**|Package containing AWS Config rules and remediation actions.|
|**Amazon Inspector**|Automated security assessment service for application/container vulnerabilities and security best-practice deviations.|
|**Security finding**|Inspector result describing a security issue, severity, and remediation recommendation.|
|**AWS Trusted Advisor**|Best-practice evaluation service covering cost, performance, resilience, security, operational excellence, and service limits.|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**AWS Audit Manager**|Preparing compliance evidence for an audit|Collects evidence and produces assessment reports|
|**Amazon Bedrock Guardrails**|Controlling AI application interactions|Filters harmful content, denied topics, and PII|
|**AWS Config**|Monitoring AWS resource configuration|Resource-level configuration/compliance|
|**Amazon Inspector**|Finding application/container security vulnerabilities|Application-level automated security assessments|
|**AWS Trusted Advisor**|Checking AWS environment against best practices|Broad recommendations across operational categories|
|**Config rule**|Evaluating resource configuration|Determines whether configuration meets a rule|
|**Conformance pack**|Deploying multiple compliance controls together|Packages Config rules + remediation actions|
|**Audit Manager framework**|Defining controls for an audit assessment|Groups related audit controls|
|**Guardrails content filter**|Filtering harmful interaction categories|Threshold-based filtering|
|**Guardrails denied topic**|Blocking specific subjects|Natural-language topic definition|

---

# 🧠 Exam Traps

### **1. Audit Manager and AWS Config perform the same job.**

- **Trap:** Choosing either service whenever “compliance” appears.
    
- **Correct:** **Audit Manager** focuses on collecting and organizing compliance evidence for assessments; **AWS Config** focuses on resource configurations and configuration compliance.
    

### **2. Audit Manager is only for SOC 2.**

- **Trap:** Assuming Audit Manager only supports traditional compliance frameworks.
    
- **Correct:** The transcript says it has built-in frameworks including **generative AI best practices and SOC 2**, and customers can also create custom frameworks.
    

### **3. A framework is the assessment report.**

- **Trap:** Treating these as interchangeable.
    
- **Correct:** A **framework** is a grouping of controls; an **assessment** uses that framework to evaluate resources and collect evidence.
    

### **4. Guardrails only filters user prompts.**

- **Trap:** Assuming model-generated responses are not evaluated.
    
- **Correct:** Guardrails evaluates **both user queries and FM responses**.
    

### **5. Guardrails only filters harmful language.**

- **Trap:** Limiting Guardrails to hate, insults, sexual, and violence categories.
    
- **Correct:** Guardrails also supports **denied topics and PII detection**, including rejecting PII-containing inputs or redacting PII in FM responses.
    

### **6. Denied topics require a machine-learning model to be trained.**

- **Trap:** Assuming custom topic blocking requires model training.
    
- **Correct:** The transcript describes defining denied topics using **short natural-language descriptions**, with optional example phrases.
    

### **7. AWS Config performs application vulnerability scanning.**

- **Trap:** Choosing Config for vulnerable software or application/container security issues.
    
- **Correct:** **Amazon Inspector** works at the application level and checks applications and containers for vulnerabilities.
    

### **8. Amazon Inspector tracks resource configuration history.**

- **Trap:** Choosing Inspector because it performs security assessments.
    
- **Correct:** **AWS Config** captures resource configuration changes and maintains configuration history.
    

### **9. Config automatically fixes every noncompliant resource by itself.**

- **Trap:** Treating Config's detection and remediation mechanisms as the same component.
    
- **Correct:** Config evaluates the configuration; the transcript identifies **AWS Systems Manager automation documents** for automatic remediation.
    

### **10. Conformance packs are individual Config rules.**

- **Trap:** Treating a conformance pack as one rule.
    
- **Correct:** A conformance pack packages **AWS Config rules and remediation actions**.
    

### **11. Trusted Advisor is primarily an audit evidence service.**

- **Trap:** Choosing Trusted Advisor whenever the question says “compliance.”
    
- **Correct:** Trusted Advisor evaluates AWS environments against **best practices** and recommends remediation actions.
    

### **12. Inspector and Trusted Advisor provide the same findings.**

- **Trap:** Treating both as generic security scanners.
    
- **Correct:** Inspector performs automated **application/container security assessments**, while Trusted Advisor evaluates broader AWS **best-practice checks**.
    

---

# 📝 Exam Questions

### **Question 1**

A compliance team needs to prepare evidence for an upcoming audit. The team wants an AWS service to map compliance requirements to AWS usage data, automatically collect relevant evidence, organize it against controls, and produce an auditor-friendly assessment report.

Which service should the team use?

A. AWS Config

B. AWS Audit Manager

C. Amazon Inspector

D. AWS Trusted Advisor

**Answer: B — AWS Audit Manager**

**Why:** Audit Manager maps compliance requirements to AWS usage data, collects evidence, attaches it to controls, and produces assessment reports.

---

### **Question 2**

A company wants to assess a set of controls that are unique to its internal compliance program. None of the available predefined frameworks exactly matches its requirements.

What should the company use?

A. A custom AWS Audit Manager framework

B. A custom Amazon Inspector assessment

C. An AWS Config configuration history snapshot

D. A Trusted Advisor security check

**Answer: A — A custom AWS Audit Manager framework**

**Why:** Audit Manager allows customers to define their own framework tailored to the controls they want to assess.

---

### **Question 3**

A Bedrock-powered customer-support assistant must prevent users from requesting investment advice. The development team wants to define the restricted subject using a short natural-language description rather than retraining the model.

Which capability should they use?

A. AWS Config custom rule

B. Amazon Inspector finding

C. Guardrails denied topic

D. Audit Manager custom framework

**Answer: C — Guardrails denied topic**

**Why:** Guardrails allows application-specific **denied topics** to be defined using natural-language descriptions.

---

### **Question 4**

A Bedrock application should prevent personally identifiable information from being included in model interactions. The organization wants to reject user inputs containing PII while redacting PII from model-generated responses.

Which capability matches this requirement?

A. Amazon Inspector

B. AWS Audit Manager

C. Amazon Bedrock Guardrails

D. AWS Trusted Advisor

**Answer: C — Amazon Bedrock Guardrails**

**Why:** Guardrails can detect PII in both inputs and FM responses and can selectively **reject inputs** or **redact PII in responses**.

---

### **Question 5**

An administrator needs to determine whether an AWS resource became noncompliant after its configuration changed. The administrator also wants a historical record of configuration changes.

Which service is most directly suited to this requirement?

A. Amazon Inspector

B. AWS Config

C. AWS Audit Manager

D. AWS Trusted Advisor

**Answer: B — AWS Config**

**Why:** AWS Config maintains an inventory of resource configurations and records configuration changes in configuration history.

---

### **Question 6**

An organization has an AWS Config rule that detects a noncompliant resource. It wants the violation to automatically trigger a predefined remediation workflow.

Which capability described in the lesson should it use?

A. AWS Systems Manager automation document

B. Amazon Inspector security finding

C. AWS Audit Manager assessment report

D. Amazon Bedrock Guardrails

**Answer: A — AWS Systems Manager automation document**

**Why:** The transcript states that noncompliant Config changes can be automatically remediated using an **AWS Systems Manager automation document**.

---

### **Question 7**

A company wants to deploy a collection of AWS Config rules together with associated remediation actions to satisfy a compliance requirement.

Which capability should it use?

A. AWS Audit Manager framework

B. AWS Config conformance pack

C. Amazon Inspector assessment

D. Trusted Advisor check

**Answer: B — AWS Config conformance pack**

**Why:** Conformance packs package **AWS Config rules and remediation actions** together.

---

### **Question 8**

A security team needs to identify vulnerable software versions and open access configurations affecting applications and containers. After the assessment, the team wants findings prioritized by severity with recommendations for remediation.

Which service best matches this requirement?

A. AWS Config

B. AWS Audit Manager

C. Amazon Inspector

D. AWS Trusted Advisor

**Answer: C — Amazon Inspector**

**Why:** Inspector performs automated security assessments of applications and containers and produces prioritized **security findings** with remediation recommendations.

---

### **Question 9**

An organization wants a service that continuously evaluates its AWS environment against best-practice checks covering cost optimization, performance, resilience, security, operational excellence, and service limits.

Which service should it use?

A. AWS Config

B. AWS Audit Manager

C. Amazon Inspector

D. AWS Trusted Advisor

**Answer: D — AWS Trusted Advisor**

**Why:** Those six categories are the best-practice check categories identified for **Trusted Advisor** in the transcript.

---

### **Question 10**

A Bedrock application must prevent harmful interactions. The organization wants configurable thresholds for hate, insults, sexual, and violence categories and wants filtering applied to both user prompts and model responses.

Which capability should the organization configure?

A. AWS Config conformance packs

B. Amazon Bedrock Guardrails content filters

C. Amazon Inspector security assessments

D. AWS Audit Manager frameworks

**Answer: B — Amazon Bedrock Guardrails content filters**

**Why:** Guardrails provides configurable content-filter thresholds and evaluates both **user queries and FM responses**.

---

# ⚡ 30-Second Revision

1. **Audit Manager → compliance evidence + assessment reports.**
    
2. **Audit Manager framework → grouping of audit controls.**
    
3. **Audit Manager → built-in frameworks + custom frameworks.**
    
4. **Guardrails → application-specific Bedrock safeguards.**
    
5. **Guardrails → harmful-content filtering.**
    
6. **Guardrails → denied topics.**
    
7. **Guardrails → PII detection, rejection, and redaction.**
    
8. **Guardrails evaluates both input AND FM response.**
    
9. **AWS Config → resource configuration monitoring.**
    
10. **Config → configuration history + compliance rules.**
    
11. **Config noncompliance → Systems Manager automation can remediate.**
    
12. **Conformance pack → Config rules + remediation actions.**
    
13. **AI/ML conformance packs → operational AI/ML best practices + SageMaker security best practices.**
    
14. **Amazon Inspector → application/container vulnerabilities.**
    
15. **Inspector → security findings + severity + remediation recommendations.**
    
16. **Trusted Advisor → broad AWS best-practice checks.**
    
17. **Trusted Advisor categories → cost, performance, resilience, security, operational excellence, service limits.**