 # Domain 5 — Task Statement 5.1: Explain methods to secure AI systems

## 🎯 Exam Essentials

### **1. Identity Federation**

- **Concept:** **Identity federation** allows users to authenticate through an external **identity provider**, such as Active Directory, and then receive **temporary AWS credentials**.
    
- **Key distinction:** Instead of creating and managing an IAM user for every person in the AWS account, authentication can be handled through an existing identity system.
    
- **Exam trigger:** Look for **Active Directory, external identity provider, existing corporate identities, or temporary AWS credentials**.
    

### **2. AWS IAM Identity Center**

- **Concept:** **AWS IAM Identity Center** allows organizations to authenticate users through an external identity provider or through a directory created within IAM Identity Center.
    
- **Key distinction:** IAM Identity Center provides centralized management of workforce identities and their access across **multiple AWS accounts**.
    
- **Exam trigger:** Multiple AWS accounts + centralized user/access management → **IAM Identity Center**.
    

### **3. Workforce Users / Workforce Identities**

- **Concept:** IAM Identity Center refers to its users as **workforce users** or **workforce identities**.
    
- **Key distinction:** These identities are managed through IAM Identity Center rather than requiring separate IAM users in every AWS account.
    
- **Exam trigger:** If the question uses **workforce identity/user**, connect it to **IAM Identity Center**.
    

### **4. IAM Identity Center Access Portal**

- **Concept:** After authentication, workforce users are directed to a **portal** where they can choose an AWS console to access or obtain temporary access keys for AWS accounts where they have permissions.
    
- **Key distinction:** The portal provides a centralized entry point for accessing multiple AWS accounts.
    
- **Exam trigger:** User authenticates once and then chooses among **multiple AWS accounts or AWS console access**.
    

### **5. Centralized Multi-Account Access**

- **Concept:** IAM Identity Center is particularly useful for organizations with **multiple AWS accounts** because users can be managed centrally instead of creating IAM users separately in each account.
    
- **Key distinction:** IAM Identity Center centralizes both users and permissions across accounts.
    
- **Exam trigger:** Scenario involves an organization managing **many AWS accounts** and wanting one centralized identity/access system.
    

### **6. Permission Sets**

- **Concept:** IAM Identity Center allows users to be organized into **groups** and **permission sets** to define their access.
    
- **Key distinction:** Permission sets can be assigned at the **group level**, making it easier to manage access consistently.
    
- **Exam trigger:** Look for **groups + centralized permissions + multiple AWS accounts**.
    

### **7. IAM Identity Center Uses Roles**

- **Concept:** IAM Identity Center uses **roles to grant temporary permissions**.
    
- **Key distinction:** This avoids relying on long-lived credentials for workforce access.
    
- **Exam trigger:** If the requirement emphasizes **temporary access** and avoiding **long-lived credentials**, recognize the role-based approach.
    

### **8. AWS Recommendation for User Management**

- **Concept:** The transcript states that AWS recommends using **IAM Identity Center for managing users instead of IAM**.
    
- **Key distinction:** IAM Identity Center provides centralized workforce identity management, especially useful across multiple AWS accounts.
    
- **Exam trigger:** Scenario asks for a recommended approach to centrally manage workforce users across AWS accounts.
    

### **9. AWS CloudTrail**

- **Concept:** **AWS CloudTrail** captures API calls and related events made by or on behalf of an AWS account.
    
- **Key distinction:** CloudTrail provides an audit trail of actions performed against AWS resources.
    
- **Exam trigger:** Look for requirements to **log, review, audit, or investigate user/API activity**.
    

### **10. CloudTrail Log Delivery**

- **Concept:** CloudTrail delivers its log files to an **Amazon S3 bucket** specified by the customer.
    
- **Key distinction:** CloudTrail is the service capturing the events; S3 is where the transcript says the log files are delivered.
    
- **Exam trigger:** Scenario asks where CloudTrail log files are delivered or stored.
    

### **11. CloudTrail and SageMaker**

- **Concept:** Amazon SageMaker is integrated with **CloudTrail**. CloudTrail captures SageMaker API calls except for **invoking endpoints**, according to the transcript.
    
- **Key distinction:** Creating a SageMaker training job or notebook instance is logged, while endpoint invocation is specifically excluded in this lesson.
    
- **Exam trigger:** Look for SageMaker actions such as **creating training jobs or notebook instances** and requirements to audit them.
    

### **12. Information Available Through CloudTrail**

- **Concept:** CloudTrail information can be used to determine details about a request made to SageMaker, including **what request was made, the source IP address, who made the request, when it was made, and additional details**.
    
- **Key distinction:** CloudTrail is useful for reconstructing **who did what, from where, and when**.
    
- **Exam trigger:** Investigation/audit scenario asking **who, when, where, or what API action** occurred.
    

### **13. Protecting AI Training Data and Artifacts**

- **Concept:** Under the shared responsibility model, customers are responsible for managing access to their data, including keeping **training data and artifacts private and secure**.
    
- **Key distinction:** AWS secures the underlying cloud infrastructure, but customers must control access to their own AI-related data.
    
- **Exam trigger:** Scenario involves protecting **training datasets, model artifacts, or customer-owned data**.
    

### **14. Amazon S3 Block Public Access**

- **Concept:** **S3 Block Public Access** can be used to block public access to S3 objects.
    
- **Key distinction:** It can be enabled at the **bucket or account level**.
    
- **Exam trigger:** Requirement says **prevent S3 data from becoming publicly accessible**.
    

### **15. Account-Level vs. Bucket-Level S3 Block Public Access**

- **Concept:** When enabled at the **account level**, no buckets—existing or new—can grant public access. When enabled at the bucket level, the protection applies to that bucket.
    
- **Key distinction:** Account-level configuration provides broader protection across the account.
    
- **Exam trigger:** Compare whether protection is needed for **one bucket** or **all buckets in an account**.
    

### **16. S3 Block Public Access Overrides Public Permissions**

- **Concept:** S3 Block Public Access overrides public permissions granted through **bucket policies or access control lists (ACLs)**.
    
- **Key distinction:** A public permission does not make an object publicly accessible when Block Public Access prevents that access.
    
- **Exam trigger:** Scenario contains a **public bucket policy/ACL** but Block Public Access is enabled.
    

### **17. SageMaker Role Manager**

- **Concept:** **SageMaker Role Manager** simplifies creating IAM roles for ML activities by providing **pre-configured role personas and predefined permissions**.
    
- **Key distinction:** Instead of manually constructing every IAM permission policy, Role Manager provides predefined activities that can be selected and customized.
    
- **Exam trigger:** Scenario asks for a simpler way to create appropriate IAM roles for **SageMaker ML activities**.
    

### **18. SageMaker Role Manager Personas**

- **Concept:** The transcript identifies three pre-configured personas: **Data Scientist, MLOps, and SageMaker Compute**.
    
- **Key distinction:** Each persona is designed around a different type of ML responsibility.
    
- **Exam trigger:** Question describes a specific ML role and asks which SageMaker Role Manager persona fits it.
    

### **19. Data Scientist Persona**

- **Concept:** The **Data Scientist** persona is intended for someone using SageMaker for **general machine learning development and experimentation**.
    
- **Key distinction:** Its focus is ML development and experimentation.
    
- **Exam trigger:** General **ML development + experimentation** → Data Scientist persona.
    

### **20. MLOps Persona**

- **Concept:** The **MLOps** persona is for someone managing **models, pipelines, experiments, and endpoints**, but who does not need access to data in Amazon S3.
    
- **Key distinction:** The important distinction is managing ML resources without needing direct S3 data access.
    
- **Exam trigger:** **Models + pipelines + experiments + endpoints**, but **no S3 data access** → MLOps persona.
    

### **21. SageMaker Compute Persona**

- **Concept:** The **SageMaker Compute** persona is used to create a role that SageMaker compute resources can use for tasks such as **training and inference**.
    
- **Key distinction:** This persona is designed for **SageMaker compute resources**, rather than a human ML job function.
    
- **Exam trigger:** SageMaker compute resources need permissions to perform **training or inference** → SageMaker Compute persona.
    

### **22. Customizing SageMaker Role Manager Roles**

- **Concept:** When creating a role with SageMaker Role Manager, the appropriate activities are preselected based on the chosen persona, but the activities can be **customized**.
    
- **Key distinction:** Role Manager does not force the predefined configuration; you can modify enabled activities and add additional IAM policies.
    
- **Exam trigger:** Scenario requires a predefined ML role with **additional or customized permissions**.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Identity federation**|Authentication through an external identity provider followed by temporary AWS access.|
|**Identity provider**|External system used to authenticate users, such as Active Directory.|
|**IAM Identity Center**|Centralized workforce identity and access management across AWS accounts.|
|**Workforce identity**|User identity managed through IAM Identity Center.|
|**Permission set**|Defines permissions assigned to users/groups through IAM Identity Center.|
|**AWS CloudTrail**|Captures AWS API calls and related events for auditing.|
|**CloudTrail log**|Record of API activity delivered to an S3 bucket.|
|**S3 Block Public Access**|Prevents public access to S3 objects.|
|**SageMaker Role Manager**|Simplifies creation of IAM roles for ML activities.|
|**Data Scientist persona**|Role configuration for general ML development and experimentation.|
|**MLOps persona**|Role configuration for managing models, pipelines, experiments, and endpoints without S3 data access.|
|**SageMaker Compute persona**|Role configuration for SageMaker compute resources performing tasks such as training and inference.|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**IAM users**|Managing individual AWS identities|Users are created and managed within AWS accounts|
|**IAM Identity Center**|Centralized workforce access|Centralizes identities and access across multiple AWS accounts|
|**Identity federation**|Existing external identity system is used|Users authenticate through an external identity provider|
|**IAM Identity Center permission sets**|Defining workforce access|Permissions can be assigned to groups across accounts|
|**Long-lived credentials**|Persistent user credentials|Greater concern if credentials are compromised|
|**Temporary role credentials**|Temporary AWS access|Credentials automatically expire|
|**CloudTrail**|Auditing AWS activity|Captures API calls and related events|
|**S3 Block Public Access**|Preventing public S3 access|Overrides public permissions from bucket policies/ACLs|
|**Data Scientist persona**|ML development/experimentation|Focused on general ML development|
|**MLOps persona**|Managing ML operational resources|Models, pipelines, experiments, endpoints; no S3 data access according to transcript|
|**SageMaker Compute persona**|SageMaker compute needs permissions|Used for compute resources performing training/inference|

---

## 🧠 Exam Traps

### **1.**

**Trap:** Identity federation means users receive permanent AWS credentials after authenticating through Active Directory.

**Correct:** According to the transcript, users receive **temporary credentials** after authenticating through the identity provider.

### **2.**

**Trap:** IAM Identity Center is primarily useful only when an organization has a single AWS account.

**Correct:** A major advantage described in the transcript is **centralized management across multiple AWS accounts**.

### **3.**

**Trap:** IAM Identity Center requires you to create individual IAM users in every AWS account.

**Correct:** IAM Identity Center allows workforce identities and permissions to be managed **centrally** rather than managing IAM users separately in each account.

### **4.**

**Trap:** IAM Identity Center relies on long-lived credentials for workforce access.

**Correct:** IAM Identity Center uses **roles to grant temporary permissions**.

### **5.**

**Trap:** CloudTrail is primarily used to block unauthorized access to AWS resources.

**Correct:** CloudTrail is used to **capture API calls and related events**, supporting logging, auditing, and investigation.

### **6.**

**Trap:** Every SageMaker action is captured by CloudTrail according to this lesson.

**Correct:** The transcript specifically states that CloudTrail captures SageMaker API calls **except invoking endpoints**.

### **7.**

**Trap:** Customers are not responsible for protecting AI training data because AWS secures the cloud.

**Correct:** Customers remain responsible for keeping **training data and artifacts private and secure**.

### **8.**

**Trap:** S3 Block Public Access only works by removing public bucket policies and ACLs.

**Correct:** The transcript states that Block Public Access **overrides public permissions** granted by bucket policies or ACLs.

### **9.**

**Trap:** Account-level S3 Block Public Access protects only the buckets that existed when it was enabled.

**Correct:** According to the transcript, when enabled at the account level, **no existing or new buckets can grant public access**.

### **10.**

**Trap:** The MLOps persona is intended for a data scientist who needs broad access to S3 training data.

**Correct:** The transcript describes MLOps as managing **models, pipelines, experiments, and endpoints without needing access to S3 data**.

### **11.**

**Trap:** The SageMaker Compute persona is primarily intended for a human ML developer.

**Correct:** It is used for roles that **SageMaker compute resources** can use for tasks such as training and inference.

### **12.**

**Trap:** SageMaker Role Manager automatically creates an inflexible role that cannot be modified.

**Correct:** Role Manager preselects appropriate activities based on the persona, but you can **customize activities and add additional IAM policies**.

---

# 📝 Exam Questions

### **Question 1**

A company operates 15 AWS accounts and currently creates and manages separate IAM users in every account. The security team wants employees to authenticate using the company's existing identity provider and centrally manage access across all AWS accounts. Which approach best matches the requirements described in the lesson?

A. Create IAM users in each AWS account and synchronize their credentials with the corporate directory.

B. Use AWS IAM Identity Center with the organization's external identity provider and centrally assign access.

C. Create a separate IAM group in every AWS account and assign the same user policies to each group.

D. Create IAM roles in every account and distribute long-lived credentials for each role to employees.

**Answer: B — Use AWS IAM Identity Center with the organization's external identity provider and centrally assign access.**

**Why:** IAM Identity Center supports external identity providers and centralized workforce access across multiple AWS accounts.

### **Question 2**

An organization's security team needs to investigate an unexpected SageMaker training job. They need to determine who made the request, the source IP address, when the request occurred, and details about the API request. Which capability should they use?

A. Amazon S3 Block Public Access

B. SageMaker Role Manager

C. AWS CloudTrail

D. IAM Identity Center permission sets

**Answer: C — AWS CloudTrail.**

**Why:** CloudTrail captures API calls and related events and provides information such as the requester, IP address, timestamp, and request details.

### **Question 3**

A company wants employees to authenticate using its corporate Active Directory and then obtain temporary access to AWS accounts according to their assigned permissions. The company also wants to avoid maintaining separate IAM users in every AWS account. Which solution most directly addresses these requirements?

A. IAM Identity Center

B. S3 Block Public Access

C. SageMaker Role Manager

D. CloudTrail

**Answer: A — IAM Identity Center.**

**Why:** IAM Identity Center can use an external identity provider such as Active Directory and centrally manage workforce access across AWS accounts using temporary role-based permissions.

### **Question 4**

An organization has a bucket policy that allows public access to objects in an S3 bucket. The security team enables S3 Block Public Access for the account. What does the lesson state will happen?

A. The bucket policy continues to grant public access because resource-based policies take precedence.

B. The public permission is overridden by S3 Block Public Access.

C. Only newly created objects become inaccessible publicly.

D. The bucket policy is automatically deleted from the account.

**Answer: B — The public permission is overridden by S3 Block Public Access.**

**Why:** S3 Block Public Access overrides public permissions granted through bucket policies or ACLs.

### **Question 5**

A machine learning team wants to create an IAM role for a user who performs general machine learning development and experimentation in SageMaker. Which SageMaker Role Manager persona most directly matches the requirement?

A. MLOps

B. SageMaker Compute

C. Data Scientist

D. Workforce Identity

**Answer: C — Data Scientist.**

**Why:** The Data Scientist persona is intended for general ML development and experimentation.

### **Question 6**

An ML operations engineer needs to manage SageMaker models, pipelines, experiments, and endpoints but should not have access to the organization's data stored in Amazon S3. Which predefined SageMaker Role Manager persona matches this requirement?

A. Data Scientist

B. MLOps

C. SageMaker Compute

D. Identity Federation

**Answer: B — MLOps.**

**Why:** The transcript specifically describes the MLOps persona as managing models, pipelines, experiments, and endpoints without needing S3 data access.

### **Question 7**

A company wants SageMaker compute resources to have the permissions required to perform model training and inference. The company wants to use SageMaker Role Manager rather than manually constructing the entire permissions policy. Which persona should it select?

A. Data Scientist

B. MLOps

C. SageMaker Compute

D. Workforce User

**Answer: C — SageMaker Compute.**

**Why:** The SageMaker Compute persona is designed for roles used by SageMaker compute resources to perform tasks such as training and inference.

### **Question 8**

A security administrator wants to use SageMaker Role Manager to create a role for a predefined ML persona but discovers that the selected persona does not include one activity required by the organization's workflow. What does the lesson indicate the administrator can do?

A. The administrator must abandon Role Manager and manually create the entire IAM role.

B. The administrator can customize the enabled activities and add additional IAM policies.

C. The administrator can only switch to the MLOps persona because predefined personas cannot be modified.

D. The administrator must create a new IAM user and attach the missing permission directly to that user.

**Answer: B — The administrator can customize the enabled activities and add additional IAM policies.**

**Why:** SageMaker Role Manager preselects activities based on the chosen persona, but the activities can be customized and additional IAM policies can be added.

### **Question 9**

A security architect wants workforce users to access several AWS accounts without distributing permanent AWS credentials. Which mechanism described in the lesson provides the relevant access model?

A. IAM Identity Center using roles and temporary permissions

B. IAM users using long-lived credentials

C. S3 bucket policies using public access permissions

D. CloudTrail using API activity records

**Answer: A — IAM Identity Center using roles and temporary permissions.**

**Why:** IAM Identity Center uses roles to provide temporary permissions, avoiding the long-lived credential model described for IAM users.

### **Question 10**

A company wants to protect its SageMaker training datasets and model artifacts from accidental public exposure through Amazon S3. Which capability from the lesson most directly addresses the public-access portion of this requirement?

A. AWS CloudTrail

B. IAM Identity Center

C. Amazon S3 Block Public Access

D. SageMaker Role Manager

**Answer: C — Amazon S3 Block Public Access.**

**Why:** The lesson identifies S3 Block Public Access as the mechanism for blocking public access to S3 objects, including through public bucket policies or ACLs.

---

# ⚡ 30-Second Revision

1. **Identity federation →** External identity provider authenticates users → **temporary AWS credentials**.
    
2. **IAM Identity Center →** Centralized workforce identity/access across **multiple AWS accounts**.
    
3. **Permission sets →** Define access and can be assigned to **groups**.
    
4. **IAM Identity Center →** Uses **roles + temporary permissions**, avoiding long-lived credentials.
    
5. **CloudTrail →** Captures AWS API calls/events for **auditing and investigation**.
    
6. **SageMaker + CloudTrail →** SageMaker API calls are captured **except endpoint invocation**, according to the transcript.
    
7. **S3 Block Public Access →** Blocks public access and **overrides public bucket-policy/ACL permissions**.
    
8. **Data Scientist →** General SageMaker **ML development + experimentation**.
    
9. **MLOps →** Models, pipelines, experiments, endpoints; **no S3 data access** according to the transcript.
    
10. **SageMaker Compute →** SageMaker compute resources performing **training/inference**.
    
11. **Role Manager →** Preconfigured personas/activities can be **customized**, with additional IAM policies added.