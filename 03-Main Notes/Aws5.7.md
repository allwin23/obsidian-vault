# Domain 5 — Task Statement 5.2: Recognize governance and compliance regulations for AI systems

## 🎯 Exam Essentials

### **1. AI Governance and Compliance Standards**

- **Concept:** Concerns about AI risks have led to the development of compliance standards for AI workloads.
    
- **Key distinction:** Following these standards helps protect the business and customers and supports **fairness in decision-making**.
    
- **Exam trigger:** A scenario asks why an organization follows AI governance or compliance standards → think **risk reduction, customer protection, and fair decision-making**.
    

### **2. Industry-Specific Compliance**

- **Concept:** Organizations may need to follow additional compliance standards depending on their **industry**.
    
- **Key distinction:** Compliance requirements are not necessarily identical across all organizations; industry can introduce additional standards.
    
- **Exam trigger:** A regulated-industry scenario asks why additional standards are required → consider **industry-specific compliance requirements**.
    

### **3. Audits and Inspections**

- **Concept:** Regular **audits or inspections** help determine whether an organization has met applicable standards.
    
- **Key distinction:** Compliance standards commonly contain security and operational controls that must be **tested and validated**.
    
- **Exam trigger:** A question describes an organization periodically checking whether controls satisfy a standard → think **audit/inspection**.
    

### **4. AWS Shared Responsibility Model and Compliance**

- **Concept:** The **AWS Shared Responsibility Model** applies to both **security and compliance**.
    
- **Key distinction:** AWS is responsible for meeting compliance requirements of the **cloud**, while customers are responsible for meeting compliance requirements for their **workloads in the cloud**.
    
- **Exam trigger:** Determine whether the requirement concerns AWS's underlying infrastructure or the customer's workload configuration.
    

### **5. AWS Responsibility for Compliance**

- **Concept:** AWS is responsible for compliance of the underlying physical infrastructure, including **data centers and infrastructure**.
    
- **Key distinction:** AWS maintains security and compliance certifications and attestations covering data center operations, technology, and security.
    
- **Exam trigger:** Physical data centers or underlying AWS infrastructure → **AWS responsibility**.
    

### **6. Customer Responsibility for Compliance**

- **Concept:** Customers are responsible for securing and configuring their workloads in AWS so that their workloads meet applicable compliance requirements.
    
- **Key distinction:** AWS's compliance does **not** automatically make the customer's workload compliant.
    
- **Exam trigger:** The scenario involves the customer's application, configuration, processes, or procedures → **customer responsibility**.
    

### **7. Compliance Controls and External Auditors**

- **Concept:** Compliance standards typically contain security and operational controls that are tested and validated by **external auditors**.
    
- **Key distinction:** AWS has applicable controls audited by third parties.
    
- **Exam trigger:** Look for **independent/external validation** of AWS controls.
    

### **8. Inherited Controls**

- **Concept:** Under the shared responsibility model, AWS customers can **inherit some compliance controls from AWS**.
    
- **Key distinction:** Customers don't need to independently recreate controls that are already covered by AWS's audited infrastructure controls.
    
- **Exam trigger:** A customer is trying to reduce the scope of its own compliance audit → consider **inherited AWS controls**.
    

### **9. AWS Auditor Reports**

- **Concept:** AWS makes third-party auditor reports available to customers.
    
- **Key distinction:** Customers can provide these reports to their own auditors even though customers cannot send their auditors directly into AWS data centers.
    
- **Exam trigger:** A customer's auditor needs evidence about AWS infrastructure compliance → **AWS auditor reports**.
    

### **10. AWS Artifact**

- **Concept:** **AWS Artifact** provides customers with compliance reports from third-party auditors.
    
- **Key distinction:** Artifact is the place to obtain AWS compliance documentation and reports rather than performing the AWS infrastructure audit yourself.
    
- **Exam trigger:** “Where can the customer obtain AWS compliance reports from third-party audits?” → **AWS Artifact**.
    

### **11. Reducing Audit Scope with AWS Artifact**

- **Concept:** AWS Artifact reports can reduce the scope of a customer's audit because certain AWS compliance controls are **inherited** by the customer.
    
- **Key distinction:** The customer's auditors can focus on the customer's own **processes and procedures** for workloads deployed on AWS.
    
- **Exam trigger:** Customer wants its auditors to focus on its own controls instead of re-auditing AWS infrastructure → **AWS Artifact + inherited controls**.
    

### **12. Global, Regional, and Industry-Specific Standards**

- **Concept:** AWS maintains compliance with a variety of **global, regional, and industry-specific** security standards and regulations.
    
- **Key distinction:** AWS operates globally, so its compliance obligations span multiple standards and geographic/industry contexts.
    
- **Exam trigger:** A question distinguishes compliance requirements by geography or industry → consider **global, regional, and industry-specific standards**.
    

### **13. Compliance Report Validity**

- **Concept:** AWS Artifact reports include a description of their contents and the **reporting period** for which the documentation is valid.
    
- **Key distinction:** A compliance report is associated with a specific reporting period.
    
- **Exam trigger:** A question asks how to determine the period covered by an AWS compliance report → check the **reporting period**.
    

### **14. SOC Reports**

- **Concept:** A **Service Organization Controls (SOC) report** can be used to verify that a third party follows specified best practices.
    
- **Key distinction:** This information can be important before outsourcing a business function to that organization.
    
- **Exam trigger:** A company wants evidence that an external service organization follows appropriate controls → consider a **SOC report**.
    

### **15. SOC 2**

- **Concept:** **SOC 2** reports and controls address **security, availability, processing integrity, confidentiality, and privacy**.
    
- **Key distinction:** These are the specific areas identified by the transcript for SOC 2.
    
- **Exam trigger:** If a question asks which areas SOC 2 covers, recall the five categories above.
    

### **16. Using AWS SOC 2 for Customer Compliance**

- **Concept:** An organization seeking SOC 2 for its customers can use the **AWS SOC 2 report as a starting point**.
    
- **Key distinction:** The AWS report provides evidence for AWS-controlled portions; the customer's auditor still verifies that the customer's own responsible security controls are correctly configured.
    
- **Exam trigger:** Customer uses AWS SOC 2 evidence but still needs its own audit → think **AWS controls + customer controls**.
    

### **17. ISO 27001**

- **Concept:** **ISO 27001** is an international security management standard.
    
- **Key distinction:** The transcript describes it as specifying security management best practices and **comprehensive security controls**.
    
- **Exam trigger:** International security management standard → **ISO 27001**.
    

### **18. AWS Certification and Customer Certification**

- **Concept:** AWS's certification against applicable standards can help a customer's organization obtain its own certification.
    
- **Key distinction:** AWS's certification provides a foundation, but the customer still needs to demonstrate compliance for the controls and processes it is responsible for.
    
- **Exam trigger:** A customer wants to achieve a certification while using AWS → distinguish **AWS's certified controls** from the customer's own controls.
    

### **19. AWS Customer Compliance Center**

- **Concept:** The **AWS Customer Compliance Center** provides resources for learning about AWS compliance.
    
- **Key distinction:** It contains resources such as compliance stories, whitepapers, documentation, answers to compliance questions, risk and compliance information, and auditing/security checklists.
    
- **Exam trigger:** A question asks where customers can find AWS compliance resources and guidance → **Customer Compliance Center**.
    

### **20. Customer Compliance Stories**

- **Concept:** The Customer Compliance Center contains stories describing how companies in regulated industries have addressed **compliance, governance, and audit challenges** using AWS.
    
- **Key distinction:** These are examples and guidance about how organizations approach compliance challenges.
    
- **Exam trigger:** A regulated organization wants examples of how other companies addressed AWS compliance challenges → **customer compliance stories**.
    

### **21. Compliance Whitepapers and Documentation**

- **Concept:** The Customer Compliance Center provides **compliance whitepapers and documentation**.
    
- **Key distinction:** The resources cover topics such as AWS answers to key compliance questions, AWS risk and compliance, and auditing security checklists.
    
- **Exam trigger:** A customer needs compliance guidance or documentation → consider the **Customer Compliance Center**.
    

### **22. Auditor Learning Path**

- **Concept:** The Customer Compliance Center includes an **auditor learning path**.
    
- **Key distinction:** It is intended for individuals in **auditing, compliance, and legal roles** who want to understand how internal operations can use AWS to demonstrate compliance.
    
- **Exam trigger:** An auditor or compliance/legal professional wants AWS-specific compliance education → **auditor learning path**.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**AI compliance**|Standards and requirements used to address risks associated with AI workloads.|
|**AWS Shared Responsibility Model**|Divides security and compliance responsibilities between AWS and the customer.|
|**External auditor**|Independent party that tests and validates applicable controls.|
|**Inherited controls**|Compliance controls provided by AWS that customers can rely on as part of their own compliance scope.|
|**AWS Artifact**|Service providing AWS compliance reports from third-party auditors.|
|**SOC report**|Report used to verify that a service organization follows specified controls/best practices.|
|**SOC 2**|Controls/reports covering security, availability, processing integrity, confidentiality, and privacy.|
|**ISO 27001**|International security management standard with security management best practices and comprehensive controls.|
|**Customer Compliance Center**|AWS resources for understanding and demonstrating compliance.|
|**Compliance whitepapers**|AWS documentation addressing compliance and risk-related topics.|
|**Auditor learning path**|Learning resources for auditing, compliance, and legal professionals.|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**AWS Shared Responsibility Model**|Determining who is responsible for a security/compliance control|Divides responsibility between AWS and customer|
|**AWS Artifact**|Obtaining AWS compliance reports|Provides third-party auditor reports|
|**Customer Compliance Center**|Learning about AWS compliance|Broader collection of compliance resources and guidance|
|**SOC 2**|Demonstrating controls around specified trust-related areas|Covers security, availability, processing integrity, confidentiality, and privacy|
|**ISO 27001**|Security management certification/standard|International security management standard|
|**AWS auditor reports**|Providing evidence of AWS-controlled compliance to customer auditors|Helps customers demonstrate inherited AWS controls|

---

# 🧠 Exam Traps

### **1. AWS compliance means the customer's workload is automatically compliant.**

- **Trap:** Assuming AWS's certifications automatically make the customer's application compliant.
    
- **Correct:** AWS handles compliance responsibilities for the **cloud**, while the customer remains responsible for compliance of its **workloads in the cloud**.
    

### **2. Customers must independently audit AWS data centers.**

- **Trap:** Assuming a customer can send its auditors into AWS data centers.
    
- **Correct:** AWS provides **third-party auditor reports** through **AWS Artifact**.
    

### **3. AWS Artifact performs the customer's compliance audit.**

- **Trap:** Treating Artifact as a customer auditing service.
    
- **Correct:** Artifact provides AWS compliance reports so customers and their auditors can use evidence of AWS's controls.
    

### **4. Inherited controls eliminate all customer compliance responsibilities.**

- **Trap:** Assuming AWS's audited controls mean the customer no longer needs an audit.
    
- **Correct:** The customer still needs to demonstrate that its own responsible **processes, procedures, and controls** are compliant.
    

### **5. SOC 2 only covers security.**

- **Trap:** Treating SOC 2 as exclusively a security standard.
    
- **Correct:** The transcript identifies **security, availability, processing integrity, confidentiality, and privacy**.
    

### **6. ISO 27001 is an AWS-specific compliance framework.**

- **Trap:** Assuming ISO 27001 is an AWS service or AWS-created standard.
    
- **Correct:** It is described as an **international security management standard**.
    

### **7. Customer Compliance Center and AWS Artifact are the same thing.**

- **Trap:** Choosing Artifact whenever a question mentions compliance.
    
- **Correct:** **Artifact** focuses on AWS compliance reports; the **Customer Compliance Center** provides broader compliance resources, stories, whitepapers, and learning materials.
    

### **8. AWS compliance reports are valid indefinitely.**

- **Trap:** Assuming an AWS report has no time boundary.
    
- **Correct:** AWS Artifact reports identify the **reporting period** for which the documentation is valid.
    

---

# 📝 Exam Questions

### **Question 1**

A company is preparing for a compliance audit of an application deployed on AWS. Its auditor wants evidence that AWS's underlying infrastructure controls have already been independently tested. The company also wants to avoid having its auditor re-audit controls that AWS is responsible for.

Which AWS service should the company use?

A. AWS Customer Compliance Center

B. AWS Artifact

C. AWS Audit Manager

D. AWS Config

**Answer: B — AWS Artifact**

**Why:** AWS Artifact provides compliance reports from third-party auditors. These reports can provide evidence for AWS-controlled infrastructure and help reduce the customer's audit scope through inherited controls.

---

### **Question 2**

An organization is pursuing compliance for an application running on AWS. AWS has already undergone an external audit for controls associated with the underlying cloud infrastructure.

Which statement best describes the customer's remaining responsibility?

A. The customer can inherit all compliance responsibilities because AWS has been certified.

B. The customer must independently reproduce AWS's infrastructure audit before deploying the application.

C. The customer remains responsible for its own workload controls, processes, and procedures.

D. The customer can transfer its compliance responsibilities to AWS by using AWS Artifact.

**Answer: C — The customer remains responsible for its own workload controls, processes, and procedures.**

**Why:** The shared responsibility model divides compliance responsibilities. AWS covers the compliance of the cloud, while the customer is responsible for its workload in the cloud.

---

### **Question 3**

A compliance manager wants documentation showing the specific period during which an AWS compliance report is valid.

Where should the manager look?

A. The report's reporting-period information in AWS Artifact

B. The IAM policy attached to the customer's compliance role

C. The customer's AWS CloudTrail event history

D. The application's deployment configuration

**Answer: A — The report's reporting-period information in AWS Artifact**

**Why:** The transcript states that each AWS Artifact report includes a description of its contents and the **reporting period** for which the documentation is valid.

---

### **Question 4**

A company is evaluating an external organization before outsourcing an important business function to it. The company's compliance team wants evidence that the organization follows specified controls and best practices.

Which type of report is most directly relevant?

A. ISO 27001 certification

B. SOC report

C. AWS Artifact report

D. Customer Compliance Center story

**Answer: B — SOC report**

**Why:** The transcript describes a SOC report as a way to verify that a third party is following specified best practices.

---

### **Question 5**

An organization wants to understand how companies in regulated industries have addressed governance, compliance, and audit challenges when using AWS.

Which resource is designed for this purpose?

A. AWS Artifact

B. AWS Customer Compliance Center

C. AWS IAM Identity Center

D. AWS Security Hub

**Answer: B — AWS Customer Compliance Center**

**Why:** The Customer Compliance Center includes customer compliance stories describing how companies in regulated industries have addressed compliance, governance, and audit challenges.

---

### **Question 6**

An auditor is reviewing a company's SOC 2 compliance while the company uses AWS infrastructure. The auditor wants to use AWS's existing evidence where applicable while still verifying the company's own controls.

What approach is consistent with the transcript?

A. Use AWS's SOC 2 report as a starting point and have the auditor verify the customer's responsible controls.

B. Use AWS's SOC 2 report as complete evidence that eliminates the customer's own audit.

C. Ignore AWS's SOC 2 report because compliance controls cannot be inherited.

D. Require AWS to configure and operate all controls associated with the customer's application.

**Answer: A — Use AWS's SOC 2 report as a starting point and have the auditor verify the customer's responsible controls.**

**Why:** The transcript explicitly describes using the AWS SOC 2 report as a starting point while an auditor verifies the customer's own responsible security controls.

---

### **Question 7**

A security professional needs to identify the appropriate responsibility for a compliance control involving the physical AWS data center infrastructure.

Who is primarily responsible under the AWS Shared Responsibility Model?

A. The customer, because the workload runs in the customer's AWS account.

B. AWS, because the control concerns the underlying cloud infrastructure.

C. The customer's external auditor, because the control requires validation.

D. The application developer, because the application consumes the infrastructure.

**Answer: B — AWS, because the control concerns the underlying cloud infrastructure.**

**Why:** AWS is responsible for meeting compliance requirements of the **cloud**, including the underlying physical data centers and infrastructure.

---

### **Question 8**

A compliance professional wants AWS resources covering compliance whitepapers, customer compliance stories, AWS risk and compliance information, and auditing security checklists.

Which resource should they use?

A. AWS Artifact

B. AWS Customer Compliance Center

C. AWS CloudTrail

D. AWS Organizations

**Answer: B — AWS Customer Compliance Center**

**Why:** These resources are specifically identified as contents of the Customer Compliance Center.

---

### **Question 9**

A company's legal and compliance team wants AWS-specific educational material explaining how internal operations can use AWS Cloud capabilities to demonstrate compliance.

Which resource is most directly relevant?

A. AWS Artifact reporting period documentation

B. AWS Customer Compliance Center auditor learning path

C. AWS SOC 2 report

D. AWS infrastructure certification

**Answer: B — AWS Customer Compliance Center auditor learning path**

**Why:** The transcript specifically identifies the auditor learning path for people in auditing, compliance, and legal roles.

---

### **Question 10**

A company operates in a heavily regulated industry and is designing its AWS compliance program. Its compliance manager says that meeting AWS's general security requirements should be sufficient because every AWS customer follows the same standards.

Which concept from the lesson challenges this assumption?

A. AWS Artifact reports have defined reporting periods.

B. Compliance requirements can include industry-specific standards.

C. SOC 2 covers processing integrity and privacy.

D. AWS provides customer compliance stories.

**Answer: B — Compliance requirements can include industry-specific standards.**

**Why:** The transcript states that organizations may need to uphold standards specific to their industry in addition to broader compliance requirements.

---

# ⚡ 30-Second Revision

1. **Shared responsibility applies to security AND compliance.**
    
2. **AWS = compliance/security of the cloud.**
    
3. **Customer = compliance/security of workloads in the cloud.**
    
4. **External auditors test and validate compliance controls.**
    
5. **AWS customers can inherit some controls from AWS.**
    
6. **AWS Artifact = third-party AWS compliance reports.**
    
7. **Artifact reports can reduce customer audit scope.**
    
8. **SOC 2 = security + availability + processing integrity + confidentiality + privacy.**
    
9. **ISO 27001 = international security management standard.**
    
10. **Customer Compliance Center = compliance stories, whitepapers, documentation, checklists, and learning resources.**
    
11. **Auditor learning path = auditing, compliance, and legal professionals.**
    
12. **AWS compliance does NOT automatically make the customer's workload compliant.**