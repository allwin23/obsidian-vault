   # Domain 5 — Task Statement 5.1: Explain methods to secure AI systems

## 🎯 Exam Essentials

### **1. IAM Policies**

- **Concept:** An **IAM policy** is a JSON document that **allows or denies permissions** to AWS services and resources.
    
- **Key distinction:** Policies determine **what actions an identity is permitted or denied to perform**.
    
- **Exam trigger:** Look for a scenario involving **customizing a user's access** to specific AWS resources or actions.
    

### **2. Principle of Least Privilege**

- **Concept:** Grant users or identities **only the permissions required to complete a task**.
    
- **Key distinction:** Least privilege is about minimizing unnecessary access rather than simply granting broad permissions for convenience.
    
- **Exam trigger:** Phrases such as **"only the permissions necessary," "minimum required access,"** or **"reduce unnecessary permissions."**
    

### **3. IAM Groups**

- **Concept:** An **IAM group** is a collection of IAM users. A policy attached to the group grants the specified permissions to the users in that group.
    
- **Key distinction:** Groups simplify permission management when many users need similar access.
    
- **Exam trigger:** A company has **many users with similar job responsibilities** and wants to manage their permissions collectively.
    

### **4. Organizing IAM Groups by Job Function**

- **Concept:** IAM groups can be organized according to **job functions**, such as developers, QA testers, and administrators.
    
- **Key distinction:** Instead of attaching the same policy separately to hundreds or thousands of users, policies can be attached to the appropriate groups.
    
- **Exam trigger:** Scenario describes **developers, testers, administrators, or other teams** requiring different permission sets.
    

### **5. IAM Group Membership Rules**

- **Concept:** IAM groups can contain **many users**, and an IAM user can belong to **many groups**.
    
- **Key distinction:** **IAM groups cannot belong to other IAM groups.**
    
- **Exam trigger:** Questions testing the structural relationships between **users and groups**.
    

### **6. Group Policies vs. User Policies**

- **Concept:** The recommended approach is to attach policies to **groups** and attach policies directly to users only when they require **unique permissions**.
    
- **Key distinction:** Common permissions → group; exceptional/unique permissions → user.
    
- **Exam trigger:** Look for a large organization where most users share a permission set but a few users need additional unique access.
    

### **7. Long-Lived Credentials**

- **Concept:** Policies associated with IAM users and groups use **long-lived credentials** to access AWS resources.
    
- **Key distinction:** Long-lived credentials can remain valid until changed/revoked, creating a security concern if they are exposed.
    
- **Exam trigger:** Scenario describes AWS credentials being **embedded in source code, accidentally shared, or compromised**.
    

### **8. IAM Roles**

- **Concept:** An **IAM role** is an identity that a person or AWS service can assume to obtain **temporary access** to AWS resources or services.
    
- **Key distinction:** Assuming a role provides **temporary security credentials** that automatically expire.
    
- **Exam trigger:** Look for requirements involving **temporary access**, avoiding long-lived credentials, or allowing an AWS service/person to assume an identity.
    

### **9. IAM Role Trust Policy**

- **Concept:** Every IAM role has an associated **trust policy** that determines which entities can **assume the role**.
    
- **Key distinction:** The trust policy determines **who/what can assume the role**, rather than simply defining what the role can access.
    
- **Exam trigger:** If the question asks **"who can assume this role?"**, think **trust policy**.
    

### **10. Who Can Assume an IAM Role**

- **Concept:** According to the transcript, an IAM role can be assumed by an **IAM user, an AWS service, or a user authenticated by an external identity provider**.
    
- **Key distinction:** The role provides temporary credentials after the role is assumed.
    
- **Exam trigger:** A scenario requires an **AWS service or externally authenticated user** to obtain temporary AWS access.
    

### **11. Identity-Based Policies**

- **Concept:** Permissions policies associated with **IAM users, groups, and roles** are called **identity-based policies**.
    
- **Key distinction:** These policies are associated with an **identity**, rather than directly with the resource.
    
- **Exam trigger:** If the policy is attached to a **user, group, or role**, identify it as identity-based.
    

### **12. Resource-Based Policies**

- **Concept:** A permissions policy can also be applied directly to an AWS **resource**. The transcript uses an **S3 bucket** as an example.
    
- **Key distinction:** Resource-based policies control which users or services can access the **resource and its objects**.
    
- **Exam trigger:** The policy is attached to or defined at the **resource level**, such as an S3 bucket.
    

### **13. Identity-Based vs. Resource-Based Permissions**

- **Concept:** Effective permissions can result from either an **identity-based policy**, a **resource-based policy**, or both.
    
- **Key distinction:** An action can be allowed by either policy type, but an **explicit deny overrides an allow**.
    
- **Exam trigger:** Scenario contains multiple policies and asks whether an action is ultimately allowed or denied.
    

### **14. Explicit Deny Overrides Allow**

- **Concept:** If an action is explicitly denied in either an identity-based or resource-based policy, the explicit deny **overrides an allow**.
    
- **Key distinction:** An allow in one policy does not overcome an explicit deny in another applicable policy.
    
- **Exam trigger:** Look for wording such as **"allowed by one policy but explicitly denied by another."**
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**IAM policy**|JSON document that allows or denies permissions.|
|**Least privilege**|Grant only the permissions required for a task.|
|**IAM group**|Collection of IAM users managed collectively.|
|**IAM role**|Identity that can be assumed to obtain temporary credentials.|
|**Temporary security credentials**|Credentials obtained through assuming a role that automatically expire.|
|**Trust policy**|Determines which entities can assume an IAM role.|
|**Identity-based policy**|Policy associated with a user, group, or role.|
|**Resource-based policy**|Policy applied at the resource level.|
|**Long-lived credentials**|Credentials associated with users/groups that can present a security risk if compromised.|
|**Explicit deny**|A denial that overrides an applicable allow.|
|**Resource-based access**|Access controlled through a policy attached at the resource level.|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**User policy**|A specific user needs permissions|Directly associated with an IAM user|
|**Group policy**|Multiple users need common permissions|Manage shared permissions centrally|
|**IAM role**|Temporary access is required|Provides temporary credentials that expire|
|**IAM role trust policy**|Determining who can assume a role|Controls role assumption|
|**Identity-based policy**|Permissions are associated with an identity|Attached to user, group, or role|
|**Resource-based policy**|Access is controlled at resource level|Applied to a resource such as an S3 bucket|
|**Long-lived credentials**|User/group access uses persistent credentials|Greater exposure if credentials are compromised|
|**Temporary credentials**|Role is assumed for access|Credentials automatically expire|
|**Allow**|An action is permitted|Can be overridden by an explicit deny|
|**Explicit deny**|An action must be denied|Overrides an applicable allow|

---

## 🧠 Exam Traps

### **1.**

**Trap:** Attach the same policy individually to thousands of IAM users because each user needs the same permissions.

**Correct:** Use an **IAM group** and attach the common policy to the group.

### **2.**

**Trap:** An IAM group can contain other IAM groups to create a hierarchy.

**Correct:** IAM groups **cannot belong to other groups**.

### **3.**

**Trap:** If two users need identical permissions, they should always share one IAM user.

**Correct:** Users should retain individual identities. Put users with common permissions into an **IAM group**.

### **4.**

**Trap:** IAM roles provide permanent credentials that users keep using indefinitely.

**Correct:** Assuming a role provides **temporary security credentials** that automatically expire.

### **5.**

**Trap:** A role's trust policy determines which AWS resources the role can access.

**Correct:** The **trust policy determines which entities can assume the role**.

### **6.**

**Trap:** An IAM role can only be assumed by an IAM user.

**Correct:** The transcript states that a role can be assumed by an **IAM user, AWS service, or externally authenticated user**.

### **7.**

**Trap:** A policy attached to an S3 bucket is an identity-based policy because it controls user access.

**Correct:** A policy applied at the **resource level**, such as an S3 bucket, is a **resource-based policy**.

### **8.**

**Trap:** If an identity-based policy allows an action, the action is always permitted.

**Correct:** An **explicit deny** in an applicable identity-based or resource-based policy overrides the allow.

### **9.**

**Trap:** Least privilege means giving users enough permissions to perform their job, including permissions they might need eventually.

**Correct:** Grant **only the permissions required to complete the task**.

### **10.**

**Trap:** Group policies eliminate the need for any user-specific policies.

**Correct:** The recommended approach is to attach common policies to groups and give users direct policies only for **unique permissions** they require.

---

# 📝 Exam Questions

### **Question 1**

A company has 3,000 AWS users. Developers, QA engineers, and administrators each require different sets of permissions. Security wants to minimize the administrative effort required when permissions change for an entire job function. Which approach best fits the requirement?

A. Create separate IAM policies for every individual user and update each policy whenever the job function changes.

B. Create IAM groups based on job functions and attach the appropriate policies to each group.

C. Create one IAM role for every employee and permanently assign the role's credentials to each employee.

D. Create nested IAM groups for each job function and attach permissions to the parent groups.

**Answer: B — Create IAM groups based on job functions and attach the appropriate policies to each group.**

**Why:** IAM groups allow common permissions to be managed centrally for users with similar job functions.

---

### **Question 2**

A developer accidentally includes AWS credentials in application source code that is later shared publicly. The security team wants future application access to avoid relying on credentials that remain valid for long periods. Which capability described in the lesson most directly addresses this concern?

A. IAM group policies

B. Resource-based policies

C. IAM roles with temporary security credentials

D. User-level identity-based policies

**Answer: C — IAM roles with temporary security credentials.**

**Why:** IAM roles provide temporary credentials that automatically expire, reducing reliance on long-lived credentials.

---

### **Question 3**

An organization creates an IAM role for an internal application. The security team wants to specify which entities are permitted to assume that role. Which policy controls this requirement?

A. The role's permissions policy

B. The role's trust policy

C. The user's resource-based policy

D. The IAM group's permissions policy

**Answer: B — The role's trust policy.**

**Why:** The transcript specifically states that each IAM role has a **trust policy determining which entities can assume the role**.

---

### **Question 4**

A security administrator needs to give 200 developers the same permissions while allowing five senior developers to receive one additional permission that the rest of the developers do not need. Which approach is most consistent with the recommended IAM management practice?

A. Attach all common and unique permissions directly to each developer.

B. Create separate IAM users for the five senior developers and remove them from the developer group.

C. Attach common permissions to the developer group and attach the unique permissions directly to the five users.

D. Create a nested group for the five senior developers and place that group inside the developer group.

**Answer: C — Attach common permissions to the developer group and attach the unique permissions directly to the five users.**

**Why:** The transcript recommends **group policies for common access** and user-level policies only for **unique permissions**.

---

### **Question 5**

An AWS administrator is evaluating two policies affecting access to an S3 bucket. An identity-based policy allows a user to perform an action, while an applicable resource-based policy explicitly denies that same action. What result does the lesson describe?

A. The identity-based allow takes precedence because it is attached to the authenticated user.

B. The resource-based allow takes precedence because it is attached directly to the resource.

C. The action is allowed because at least one applicable policy grants permission.

D. The action is denied because an explicit deny overrides an allow.

**Answer: D — The action is denied because an explicit deny overrides an allow.**

**Why:** The transcript explicitly states that an **explicit deny in either policy type overrides an allow**.

---

### **Question 6**

A company wants an AWS service to obtain temporary access to another AWS resource without embedding long-lived AWS credentials in the service's application code. Which capability from the lesson most directly matches this requirement?

A. IAM group membership

B. IAM role assumption

C. User-level IAM policy attachment

D. Resource-based policy attachment

**Answer: B — IAM role assumption.**

**Why:** The transcript states that an **AWS service can assume an IAM role** and receive temporary security credentials that automatically expire.

---

### **Question 7**

A security team wants to determine whether a particular policy is identity-based or resource-based. The policy is associated with an IAM role and specifies permissions the role can exercise. How should the policy be classified?

A. Resource-based policy

B. Identity-based policy

C. Trust policy

D. Group-based resource policy

**Answer: B — Identity-based policy.**

**Why:** Policies associated with **IAM users, groups, and roles** are identity-based policies.

---

### **Question 8**

A company wants to reduce unnecessary permissions granted to its AI development team. Developers currently have permissions to perform many AWS actions that are unrelated to their assigned tasks. Which security principle should guide the redesign?

A. Resource-based authorization

B. Identity federation

C. Principle of least privilege

D. Role inheritance

**Answer: C — Principle of least privilege.**

**Why:** Least privilege means granting **only the permissions required to complete a task**.

---

# ⚡ 30-Second Revision

1. **IAM policy →** JSON document that **allows or denies permissions**.
    
2. **Least privilege →** Grant **only required permissions**.
    
3. **IAM group →** Collection of users; attach common policies to groups.
    
4. **IAM groups →** Users can belong to multiple groups; groups **cannot contain groups**.
    
5. **IAM role →** Provides **temporary credentials** that automatically expire.
    
6. **Trust policy →** Determines **who/what can assume a role**.
    
7. **Identity-based policy →** Attached to **user, group, or role**.
    
8. **Resource-based policy →** Applied directly at the **resource level**.
    
9. **Allow vs. deny →** An **explicit deny overrides an allow**.
    
10. **Credential security →** Prefer temporary role credentials over risky **long-lived credentials** when the scenario calls for temporary access.