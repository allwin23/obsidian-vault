**# AWS Certified Cloud Practitioner (CLF-C02)

# Chapter 2 — IAM: Identity and Access Management

**Exam focus:** Very High  
**Primary CLF-C02 domain:** Domain 2 — Security and Compliance

This chapter covers the IAM material from your course and expands it into the concepts you need to recognize and reason through on the CLF-C02 exam.

---

# 1. Topic Overview

**AWS Identity and Access Management (IAM)** controls **who can access AWS resources and what they are allowed to do**.

The simplest mental model is:

```
WHO?
  ↓
IAM identity
  ↓
WHAT CAN THEY DO?
  ↓
IAM policy
  ↓
TO WHICH RESOURCE?
  ↓
AWS resource
```

For example:

```
Developer
   ↓
IAM User / Role
   ↓
Policy
   ↓
Allow:
ec2:DescribeInstances
   ↓
Amazon EC2
```

IAM is fundamentally about:

- Authentication
- Authorization
- Permissions
- Users
- Groups
- Roles
- Policies
- MFA
- Credentials
- Least privilege

AWS IAM is available at **no additional charge**. [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/security-iam.html?utm_source=chatgpt.com)

---

# 2. Authentication vs Authorization

This distinction is extremely important.

## Authentication

Authentication answers:

> **"Who are you?"**

Example:

```
Username + Password
        ↓
AWS verifies identity
        ↓
You are authenticated
```

---

## Authorization

Authorization answers:

> **"What are you allowed to do?"**

Example:

```
Authenticated user
       ↓
IAM policy
       ↓
Can:
  Read S3
  Start EC2

Cannot:
  Delete S3
```

### 🧠 Remember

> **Authentication = Who are you?**

> **Authorization = What can you do?**

IAM is heavily involved in both identity and access management.

---

# 3. IAM's Core Components

You need to clearly distinguish these:

```
IAM
│
├── Users
│
├── Groups
│
├── Roles
│
└── Policies
```

And security mechanisms around them:

```
MFA
Password policies
Access keys
Credential reports
Access Advisor
Least privilege
```

Let's break them down.

---

# 4. IAM Users

An **IAM user** represents an identity within an AWS account.

Historically, you can think of an IAM user as representing an individual person or application that needs long-term AWS credentials.

For example:

```
AWS Account
│
├── allwin
├── john
├── mary
└── developer1
```

Each user can have permissions associated with them.

AWS documentation describes IAM users as identities in an AWS account. A newly created IAM user does not automatically have permissions to access resources until permissions are granted. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_access-management.html?utm_source=chatgpt.com)

---

# 5. IAM User Example

Imagine a company has:

```
Alice → Developer
Bob   → Finance
Carol → Administrator
```

You could create:

```
IAM Users

Alice
Bob
Carol
```

Then give them appropriate permissions.

But there's a better way than manually attaching policies to every individual user.

That's where **groups** come in.

---

# 6. IAM Groups

An IAM group is a collection of IAM users.

Example:

```
Developers
│
├── Alice
├── Bob
└── Charlie
```

You can attach permissions to the group.

For example:

```
Developers Group
       ↓
Policy
       ↓
EC2 ReadOnly
```

Now members of the group inherit those permissions.

---

# 7. Why Groups Matter

Suppose you have:

```
100 developers
```

Without groups:

```
Alice → attach policy
Bob → attach policy
Charlie → attach policy
...
```

This is difficult to manage.

With a group:

```
Developers
    ↓
EC2ReadOnlyPolicy
    ↓
100 developers
```

Much easier.

### Exam clue

> "Give the same permissions to multiple users"

Think:

**IAM Group**

---

# 8. Users vs Groups

|IAM User|IAM Group|
|---|---|
|Represents an identity|Collection of users|
|Can authenticate|Users authenticate|
|Can have permissions|Permissions can be attached to group|
|Individual entity|Organizational mechanism|
|Example: Alice|Example: Developers|

### ⚠️ Important

An IAM group is **not an identity that signs in**.

A person signs in as an IAM user or through another supported identity mechanism.

---

# 9. IAM Roles

Roles are one of the most important concepts in IAM.

An IAM role is an identity that has permissions but is designed to be **assumed** rather than permanently associated with one person.

Unlike IAM users, roles don't have standard long-term credentials such as passwords or access keys. When a role is assumed, temporary security credentials are provided for the role session. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html?utm_source=chatgpt.com)

Think:

```
IAM User
   ↓
Long-term identity

IAM Role
   ↓
Temporary identity/permissions
   ↓
Assumed when needed
```

---

# 10. Why Roles Exist

Roles allow you to give temporary permissions to:

- AWS services
- Applications
- Users
- External identities
- Users from other AWS accounts

Examples:

```
EC2
 ↓
IAM Role
 ↓
S3 Read Access
```

or:

```
Developer
 ↓
Assume IAM Role
 ↓
Temporary permissions
```

or:

```
AWS Account A
      ↓
Assume role
      ↓
AWS Account B
```

AWS specifically identifies roles as useful for temporary access, cross-account access, federated access, and applications running on EC2. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/when-to-use-iam.html?utm_source=chatgpt.com)

---

# 11. IAM Role for EC2

This is one of the most important scenarios from your course.

Suppose your application is running on EC2.

The application needs to read from S3.

### Bad approach

Put AWS access keys directly inside the application:

```
EC2
 ↓
Application
 ↓
Hard-coded Access Key
 ↓
S3
```

This creates a credential-management problem.

### Better approach

```
EC2
 ↓
IAM Role
 ↓
Temporary credentials
 ↓
S3
```

AWS recommends IAM roles for applications running on EC2 so that long-term credentials don't have to be distributed to the instance. [AWS Documentation](https://docs.aws.amazon.com/us_en/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html?utm_source=chatgpt.com)

### 🔥 Exam clue

> "An EC2 application needs access to S3 without storing credentials."

Answer:

**IAM role**

---

# 12. Policies

A policy defines permissions.

Think:

> **Policy = permission rules**

Example concept:

```
Allow
  ↓
Read
  ↓
S3
```

IAM policies are generally represented as JSON documents.

AWS evaluates policies when a principal makes an AWS request. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_access-management.html?utm_source=chatgpt.com)

---

# 13. Policy Mental Model

A policy essentially answers:

```
EFFECT:
Allow or Deny

ACTION:
What operation?

RESOURCE:
Which AWS resource?

CONDITION:
Under what circumstances?
```

Example:

```
Allow
   ↓
s3:GetObject
   ↓
specific S3 bucket
```

---

# 14. Basic IAM Policy Structure

A simplified policy looks like:

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::example-bucket/*"
    }
  ]
}
```

You don't need to become an IAM policy-writing expert for CLF-C02.

But you **should understand what the major elements mean**.

---

# 15. Policy — Version

```
"Version": "2012-10-17"
```

This identifies the policy language version.

### Exam importance

Low-to-medium.

Don't confuse this with:

> The date the policy was created.

It identifies the version of the policy language syntax.

---

# 16. Policy — Statement

```
"Statement": [...]
```

A policy contains one or more statements.

Each statement defines a permission rule.

Example:

```
Policy
│
├── Statement 1
│      └── Allow EC2 read
│
└── Statement 2
       └── Allow S3 read
```

---

# 17. Policy — Effect

```
"Effect": "Allow"
```

or:

```
"Effect": "Deny"
```

AWS supports the values **Allow** and **Deny**. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_effect.html?utm_source=chatgpt.com)

Conceptually:

```
Allow → permission granted
Deny  → permission denied
```

AWS evaluates explicit denies specially: an explicit deny overrides an allow.

### 🔥 Exam clue

> "Explicit deny"

Think:

**Deny wins over Allow.**

---

# 18. Policy — Action

The `Action` element specifies what operation the principal can perform.

Example:

```
"Action": "s3:GetObject"
```

Meaning:

> Allow the S3 GetObject operation.

Another example:

```
"Action": "ec2:StartInstances"
```

Meaning:

> Allow starting EC2 instances.

AWS services expose their own sets of actions. [AWS Documentation](https://docs.aws.amazon.com/us_en/IAM/latest/UserGuide/reference_policies_elements_action.html?utm_source=chatgpt.com)

---

# 19. Policy — Resource

`Resource` specifies the AWS resource to which the policy applies.

Example:

```
"Resource":
"arn:aws:s3:::my-bucket/*"
```

Resources are generally identified using **Amazon Resource Names (ARNs)**. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_resource.html?utm_source=chatgpt.com)

You don't need to memorize ARN formats for every service for CLF-C02.

Just understand:

> **Resource = what AWS resource does this permission apply to?**

---

# 20. Policy — Principal

`Principal` identifies who or what is allowed or denied access in a **resource-based policy**.

Examples include:

- AWS accounts
- IAM roles
- IAM users
- Federated identities
- AWS services [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_principal.html?utm_source=chatgpt.com)

### Important CLF-C02 distinction

For an ordinary **identity-based policy** attached to a user/group/role, you generally don't specify `Principal`; the identity to which the policy is attached is implied.

`Principal` is important in resource-based policies and IAM role trust policies. [AWS Documentation](https://docs.aws.amazon.com/us_en/IAM/latest/UserGuide/access_policies.html?utm_source=chatgpt.com)

For Cloud Practitioner, don't overcomplicate this.

Remember:

> **Principal = who is making/receiving the access decision in a resource-based policy.**

---

# 21. Policy — Condition

A policy can also contain a `Condition`.

This lets permissions depend on circumstances.

Conceptually:

```
Allow access
ONLY IF
condition is satisfied
```

For example, conditions can restrict access based on contextual information such as:

- IP address
- Time
- MFA status
- Tags

You don't need to memorize advanced condition syntax for CLF-C02.

---

# 22. IAM Policy Summary

|Element|Meaning|
|---|---|
|Version|Policy language version|
|Statement|Permission rule(s)|
|Effect|Allow or Deny|
|Action|Operation being controlled|
|Resource|Resource affected|
|Principal|Who/what is specified in resource-based access|
|Condition|Conditions under which rule applies|

### Memory trick

```
E-A-R

Effect
Action
Resource
```

Then remember:

```
Principal
Condition
```

when relevant.

---

# 23. Managed vs Inline Policies

Your course mentions inline policies.

At Cloud Practitioner level, understand the basic distinction.

## Managed Policy

A standalone policy that can be attached to multiple identities.

Example:

```
ReadOnlyPolicy
       ↓
Developers Group
       ↓
Many users
```

AWS provides AWS managed policies, and customers can also create customer managed policies.

---

## Inline Policy

A policy embedded directly into a specific identity.

Conceptually:

```
IAM User
   │
   └── Inline Policy
```

It is tightly associated with that identity.

### Exam-level takeaway

> **Managed policy = reusable standalone policy**

> **Inline policy = embedded directly into one identity**

For most normal reusable permission management, managed policies are generally preferred over inline policies.

---

# 24. Least Privilege

🔥 **Extremely important.**

Least privilege means:

> Give an identity only the permissions it actually needs.

Bad:

```
Developer
 ↓
AdministratorAccess
 ↓
Everything
```

Better:

```
Developer
 ↓
Required permissions only
 ↓
Specific services/resources/actions
```

AWS explicitly recommends granting only the permissions required to perform a task. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?utm_source=chatgpt.com)

---

# 25. Least Privilege Example

Suppose a developer only needs to view EC2 instances.

Don't give:

```
ec2:*
```

if the developer doesn't need to modify anything.

Instead conceptually:

```
ec2:DescribeInstances
```

### Exam clue

> "Users should have only the permissions necessary to perform their jobs."

Answer:

**Least privilege**

---

# 26. Administrator Access vs Least Privilege

Your hands-on course has you assigning administrator access.

That's useful for learning IAM, but don't take this as a production best practice.

```
AdministratorAccess
```

provides broad permissions.

For production:

> Start with the minimum permissions required.

### ⚠️ Exam Trap

A question may describe:

> "Give developers full administrative permissions so they can work efficiently."

That is generally **not** the least-privilege answer.

---

# 27. IAM MFA

**MFA = Multi-Factor Authentication**

MFA adds another authentication factor beyond the primary credential.

Instead of:

```
Password
   ↓
Access
```

you have:

```
Password
+
MFA factor
   ↓
Access
```

AWS recommends MFA, and current IAM guidance recommends phishing-resistant methods such as passkeys/security keys where possible. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?utm_source=chatgpt.com)

---

# 28. Why MFA Matters

Suppose an attacker steals your password.

Without MFA:

```
Stolen password
      ↓
Potential account access
```

With MFA:

```
Stolen password
      ↓
Need second factor
      ↓
Attack becomes harder
```

Therefore:

> MFA provides an additional authentication factor.

---

# 29. MFA Methods

AWS supports various MFA options, including:

- Virtual authenticator applications
- Hardware devices
- Security keys/passkeys depending on the authentication scenario

For the CLF-C02 exam, the key idea is:

> **MFA adds another authentication factor.**

Don't waste time memorizing every device model.

---

# 30. Root User

When an AWS account is created, it has a **root user**.

The root user has extremely broad permissions.

### Best practice

> **Do not use the root user for everyday AWS operations.**

AWS specifically recommends protecting root credentials and avoiding routine use of the root user. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?utm_source=chatgpt.com)

---

# 31. Root User MFA

One of the most important security recommendations:

> **Enable MFA for the root user.**

Think:

```
AWS Account
     ↓
Root User
     ↓
Protect strongly
     ↓
MFA
```

---

# 32. What Should You Use Instead of Root?

For normal administration, create appropriate administrative identities rather than operating as root.

Modern AWS environments may also use **IAM Identity Center** for centralized workforce access, especially across multiple AWS accounts.

For the specific IAM-user material in your course, the basic lesson is:

```
Root
 ↓
Emergency / account-level tasks
 ↓
Not daily operations
```

---

# 33. Password Policy

IAM can enforce account password requirements for IAM users.

Depending on configuration, requirements can include:

- Minimum password length
- Character requirements
- Password expiration
- Password reuse prevention

Your course specifically demonstrates:

```
Minimum length
+
Character requirements
+
90-day changes
+
Prevent password reuse
```

These are **configuration examples**, not universal AWS requirements.

### ⚠️ Exam Trap

Don't assume:

> "AWS requires every IAM password to expire every 90 days."

That's a configurable password-policy setting, not a universal AWS rule.

---

# 34. Access Keys

Access keys are credentials used for **programmatic access**.

They consist of:

```
Access Key ID
+
Secret Access Key
```

They are different from the username/password used for console sign-in.

---

# 35. Three Ways to Access AWS

Your course identifies three important access methods:

```
             AWS
              │
      ┌───────┼────────┐
      ↓       ↓        ↓
   Console    CLI      SDK
```

---

## 35.1 AWS Management Console

Browser-based graphical interface.

Example:

```
Browser
 ↓
AWS Console
 ↓
IAM / EC2 / S3 / etc.
```

---

## 35.2 AWS CLI

Command-line interface.

Example:

```
aws ec2 describe-instances
```

You interact with AWS through commands.

---

## 35.3 AWS SDK

Software development kits allow applications to interact programmatically with AWS.

For example:

```
Python application
       ↓
AWS SDK
       ↓
AWS API
```

AWS SDKs exist for multiple programming languages.

---

# 36. CLI vs SDK

|CLI|SDK|
|---|---|
|Command-line tool|Programming library|
|Human/operator friendly|Application/developer friendly|
|Commands|Code|
|`aws s3 ls`|Python/JavaScript/etc. API calls|

### Exam clue

> "Application needs to programmatically call AWS services."

Think:

**SDK**

---

# 37. Access Keys — Security Warning

Access keys are long-term credentials when used as IAM user access keys.

Therefore:

> **Protect them like passwords.**

Never:

```
GitHub
 ↓
Access Key
 ❌
```

Never hard-code them into public source code.

AWS recommends using temporary credentials where possible and avoiding long-term access keys when they aren't necessary. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?utm_source=chatgpt.com)

---

# 38. Why IAM Roles Are Preferred for AWS Workloads

Suppose:

```
EC2 application
```

Needs AWS access.

Bad:

```
EC2
 ↓
Hard-coded access keys
```

Better:

```
EC2
 ↓
IAM Role
 ↓
Temporary credentials
```

The role eliminates the need to distribute long-term credentials to the workload. [AWS Documentation](https://docs.aws.amazon.com/us_en/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html?utm_source=chatgpt.com)

### 🔥 Exam clue

> "Application running on EC2 needs AWS permissions."

Think:

**IAM role**

Not:

**Create an IAM user and hard-code its access keys.**

---

# 39. AWS CLI Configuration

The course demonstrates:

```
aws configure
```

This can configure credentials and default settings for CLI usage.

Conceptually:

```
aws configure
      ↓
Access credentials
      +
Default region
      +
Output format
```

For learning purposes, understand what the command does.

You don't need to memorize every local AWS CLI configuration-file detail for CLF-C02.

---

# 40. CLI Permissions

An important concept from your hands-on lesson:

> **The CLI doesn't bypass IAM permissions.**

If an identity has:

```
IAM permissions
```

those permissions determine what it can do through the CLI as well.

Similarly:

```
Console
CLI
SDK
```

ultimately interact with AWS APIs.

The access method does not magically grant additional authorization.

---

# 41. AWS CloudShell

**AWS CloudShell** provides a browser-based shell environment that you can use to run AWS CLI commands.

Think:

```
Browser
   ↓
AWS Console
   ↓
CloudShell
   ↓
Terminal
   ↓
AWS CLI
```

This is useful because you don't necessarily need to install the AWS CLI locally to execute CLI commands from the CloudShell environment.

Your course also demonstrates file persistence and upload/download capabilities.

### Exam clue

> "Browser-based shell environment inside AWS for running CLI commands."

Think:

**AWS CloudShell**

---

# 42. CloudShell vs Local CLI

||CloudShell|Local AWS CLI|
|---|---|---|
|Location|AWS-hosted shell environment|Your computer|
|Installation|No local CLI installation required|Install CLI|
|Access|Browser|Terminal|
|AWS CLI|Available|Installed locally|
|Useful for|Quick AWS CLI access|Local automation/development|

---

# 43. IAM Roles for AWS Services

This is a major exam concept.

Suppose:

```
Lambda
 ↓
Needs S3 access
```

Instead of storing credentials inside Lambda:

```
Lambda
 ↓
IAM Role
 ↓
S3
```

The AWS service assumes/uses the role according to its trust relationship and permissions.

Examples:

- EC2 → IAM role
- Lambda → IAM role
- CloudFormation → IAM role

---

# 44. Two Things to Understand About a Role

A role has two conceptual permission questions:

### 1. Who can assume this role?

This is controlled by the **trust policy**.

### 2. What can the role do?

This is controlled by the **permissions policy**.

Think:

```
                 IAM ROLE
                    │
          ┌─────────┴─────────┐
          ↓                   ↓
    Trust Policy       Permissions Policy
          ↓                   ↓
   WHO can assume?       WHAT can it do?
```

AWS describes a role's trust policy as defining which principals can assume the role, while identity-based permissions policies define what the role can do. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/when-to-use-iam.html?utm_source=chatgpt.com)

---

# 45. Trust Policy vs Permissions Policy

🔥 Very useful distinction.

### Trust policy

```
WHO?
```

Example:

```
EC2 service
      ↓
Can assume this role
```

### Permissions policy

```
WHAT?
```

Example:

```
Allow
s3:GetObject
```

Therefore:

```
Trust policy
→ Who can assume me?

Permissions policy
→ What can I do?
```

---

# 46. IAM Role Example

Imagine:

```
EC2
 │
 │ assumes
 ↓
EC2-S3-ReadRole
 │
 ├── Trust policy
 │     ↓
 │   EC2 can assume
 │
 └── Permissions policy
       ↓
     s3:GetObject
```

Then:

```
EC2 application
      ↓
Temporary credentials
      ↓
S3
```

---

# 47. Credentials Report

IAM provides a **credential report** for the AWS account.

It provides information about IAM users and credential status, including:

- Password status
- Access keys
- MFA devices
- Credential usage information

AWS documentation states that the report lists IAM users and the status of various credentials, including passwords, access keys, and MFA devices. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_getting-report.html?utm_source=chatgpt.com)

---

# 48. Why Use a Credential Report?

Imagine an organization has:

```
50 IAM users
```

Security administrators want to know:

- Who has a password?
- Who has MFA?
- Which users have access keys?
- How are credentials being used?

The credential report helps audit these credential states.

### Exam clue

> "Generate a report showing users' password, MFA, and access-key status."

Think:

**IAM Credential Report**

---

# 49. IAM Access Advisor

Access Advisor helps you review **service access activity**.

Conceptually:

```
IAM identity
     ↓
What AWS services has it accessed?
     ↓
Last accessed information
```

This can help identify permissions that may no longer be required and support least-privilege refinement.

AWS recommends reviewing last-accessed information to identify unused permissions, users, roles, and credentials. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?utm_source=chatgpt.com)

---

# 50. Credential Report vs Access Advisor

🔥 **Classic comparison**

||Credential Report|Access Advisor|
|---|---|---|
|Main purpose|Credential status|Service access activity|
|Looks at|Passwords, MFA, access keys|Services accessed|
|Security question|"How are credentials configured?"|"What services has this identity used?"|
|Helps with|Credential auditing|Least privilege|

### Memory trick

```
Credential Report
→ Credentials

Access Advisor
→ Access
```

---

# 51. IAM Best Practices

These are extremely exam-relevant.

## 1. Don't use root for everyday tasks

Use appropriate identities instead.

---

## 2. Enable MFA

Especially protect privileged identities.

---

## 3. Use least privilege

Only grant required permissions.

---

## 4. Don't share credentials

Each person should have appropriate individual access.

---

## 5. Protect access keys

Don't expose them in:

- GitHub
- Source code
- Public files
- Chat messages
- Client applications

---

## 6. Prefer roles and temporary credentials for workloads

Especially for AWS resources such as EC2 and Lambda.

---

## 7. Review unused permissions

Use access information and IAM tools to refine access.

AWS's current IAM best-practices guidance emphasizes MFA, least privilege, temporary credentials where possible, protecting root credentials, and regularly removing unused credentials and permissions. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?utm_source=chatgpt.com)

---

# 52. Individual Users vs Shared Credentials

Bad:

```
Company
   ↓
One IAM user
   ↓
Everyone shares password
```

Why bad?

You can't properly determine:

> "Who performed this action?"

Better:

```
Company
│
├── Alice
├── Bob
└── Charlie
```

Each person has appropriate individual access.

### Exam clue

> "Improve accountability by identifying which employee performed an action."

Think:

**Individual identities / don't share credentials.**

---

# 53. IAM and the Shared Responsibility Model

IAM itself also follows the shared responsibility model.

### AWS manages

The underlying AWS infrastructure and security of the IAM service itself.

### Customer manages

Depending on the setup, the customer controls things such as:

- Users
- Groups
- Roles
- Policies
- Permissions
- MFA configuration
- Credentials
- Access management
- Monitoring access

The course's simplified framing is:

```
AWS
 ↓
IAM service infrastructure

Customer
 ↓
IAM configuration
 ↓
Users
 ↓
Policies
 ↓
Roles
 ↓
MFA
 ↓
Credentials
```

---

# 54. Very Important: IAM Is Global

For Cloud Practitioner purposes, remember:

> **IAM is a global AWS service.**

You don't create separate IAM users independently in every Region.

For example:

```
AWS Account
     │
     └── IAM
          │
          ├── Users
          ├── Groups
          ├── Roles
          └── Policies
```

Then those identities can be used to control access to resources in AWS Regions.

### Exam clue

> "IAM is global."

This is a common infrastructure question.

---

# 55. IAM Does Not Control Everything About Network Traffic

Don't confuse IAM with network security.

IAM answers:

> Who can access AWS resources and what API operations are allowed?

Network controls such as security groups and network ACLs address network traffic.

For example:

```
IAM
 ↓
Can this identity call EC2 APIs?

Security Group
 ↓
Can this network traffic reach the instance?
```

These solve different problems.

---

# 56. IAM vs Security Groups

|IAM|Security Group|
|---|---|
|Identity/access management|Network traffic control|
|Controls API/resource permissions|Controls inbound/outbound traffic|
|User/role oriented|Resource/network oriented|
|Policies|Rules|
|Example: Can user stop EC2?|Can traffic reach EC2 port 443?|

🔥 Don't mix these up on the exam.

---

# 57. IAM vs Root User

||Root User|IAM Identity|
|---|---|---|
|Created automatically|Yes|Created/configured as needed|
|Permissions|Extremely broad|Can be restricted|
|Daily use|❌ Avoid|✅ Preferred|
|MFA|Strongly protect with MFA|Strongly recommended|
|Credential sharing|Never|Never|
|Best use|Account-level/root-only tasks|Normal operations|

---

# 58. IAM User vs IAM Role

🔥 One of the most important comparisons.

||IAM User|IAM Role|
|---|---|---|
|Represents|Identity/user|Assumable identity|
|Long-term password|Can have|No|
|Long-term access keys|Can have|No standard long-term credentials|
|Credentials|Long-term possible|Temporary credentials when assumed|
|Common use|Human identity in legacy/direct IAM-user scenarios|AWS services, workloads, temporary/cross-account access|
|Example|Alice|EC2-S3 role|

AWS currently recommends using IAM roles for human users and workloads where possible to use temporary credentials. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?utm_source=chatgpt.com)

---

# 59. IAM User vs Group vs Role vs Policy

This is the **mental model you should memorize**.

```
USER
= WHO

GROUP
= COLLECTION OF USERS

ROLE
= WHO/WHAT CAN ASSUME TEMPORARY PERMISSIONS

POLICY
= WHAT THEY ARE ALLOWED TO DO
```

Or:

```
Alice
  ↓
Developer Group
  ↓
Policy
  ↓
Allow EC2 ReadOnly
```

Versus:

```
EC2
  ↓
IAM Role
  ↓
Policy
  ↓
Allow S3 Read
```

---

# 60. The Complete IAM Architecture

Put everything together:

```
                         AWS IAM
                            │
          ┌─────────────────┼──────────────────┐
          │                 │                  │
        USERS             GROUPS             ROLES
          │                 │                  │
          │                 │                  │
          └────────────┬────┴────────────┬─────┘
                       │                 │
                       ▼                 ▼
                    POLICIES       TRUST POLICY
                       │                 │
                       ▼                 ▼
                 WHAT CAN THEY      WHO CAN
                    DO?             ASSUME ROLE?
                       │
                       ▼
                  AWS RESOURCES
```

Security around this:

```
MFA
Least Privilege
Credential Protection
Access Reviews
Credential Reports
Access Advisor
```

---

# 61. AWS Console vs CLI vs SDK

Another useful exam comparison:

|Method|Interface|Typical user|
|---|---|---|
|Console|Browser GUI|Human|
|CLI|Command line|Administrator/developer|
|SDK|Programming code|Application/developer|
|CloudShell|Browser-based terminal|Human using AWS CLI in AWS|

All of these ultimately interact with AWS services through AWS APIs.

---

# 62. "If the Question Says..." — IAM Keyword Recognition

|Question wording|Think|
|---|---|
|"Who can access AWS?"|IAM|
|"What can a user do?"|IAM policy|
|"Collection of users"|IAM group|
|"Temporary credentials"|IAM role|
|"EC2 needs S3 access"|IAM role|
|"Application needs AWS permissions"|IAM role|
|"Don't store credentials on EC2"|IAM role|
|"Only required permissions"|Least privilege|
|"Second authentication factor"|MFA|
|"Protect root account"|MFA + avoid daily use|
|"Programmatic access"|CLI / SDK|
|"Application makes AWS API calls"|SDK|
|"Command-line AWS management"|CLI|
|"Browser-based terminal"|CloudShell|
|"Credential status for all IAM users"|Credential report|
|"Which services did this identity access?"|Access Advisor|
|"Who can assume this role?"|Trust policy|
|"What can this role do?"|Permissions policy|
|"Password complexity/expiration"|IAM password policy|
|"Don't share credentials"|Individual identities|
|"Reusable permissions"|Managed policy|
|"Policy embedded in identity"|Inline policy|
|"Security of IAM configuration"|Customer responsibility|

---

# 63. ⚠️ CLF-C02 Exam Traps

## Trap 1 — IAM User vs Role

> "EC2 needs permissions to access S3."

Don't choose:

❌ Create an IAM user and put access keys on EC2.

Prefer:

✅ IAM role.

---

## Trap 2 — IAM Group can log in

❌ False.

A group is a collection of users.

---

## Trap 3 — Role has a permanent password

❌ False.

Roles provide temporary credentials when assumed.

---

## Trap 4 — Policy = identity

❌ False.

A policy defines permissions.

---

## Trap 5 — Authentication = authorization

❌ False.

```
Authentication → Who?
Authorization → What can they do?
```

---

## Trap 6 — AdministratorAccess = best practice

❌ False.

Least privilege is the security principle.

---

## Trap 7 — Root should be used for daily work

❌ False.

Avoid routine root usage.

---

## Trap 8 — MFA replaces a password

Usually ❌.

MFA adds another authentication factor.

---

## Trap 9 — Access key = password

Not exactly.

Access keys are credentials for programmatic access.

---

## Trap 10 — CLI bypasses IAM

❌ Absolutely not.

The same authorization model applies.

---

## Trap 11 — Credential Report tells you exactly what services users accessed

❌ Not its primary purpose.

Credential report:

> Credential status.

Access Advisor:

> Service access/last accessed information.

---

## Trap 12 — Trust policy tells you what a role can access

❌ Wrong.

Trust policy:

> Who can assume the role.

Permissions policy:

> What the role can do.

---

## Trap 13 — IAM controls network ports

❌ Not primarily.

IAM controls identity/resource permissions.

Security groups/NACLs address network traffic.

---

# 64. 🔥 MUST MEMORIZE

### IAM

> Controls access to AWS resources.

### Authentication

> Who are you?

### Authorization

> What can you do?

### User

> Individual IAM identity.

### Group

> Collection of IAM users.

### Role

> Assumable identity providing temporary credentials.

### Policy

> Defines permissions.

### Least privilege

> Grant only required permissions.

### MFA

> Additional authentication factor.

### Access key

> Programmatic access credential.

### IAM Role for EC2

> Give applications permissions without embedding long-term credentials.

### Trust policy

> Who can assume the role?

### Permissions policy

> What can the role do?

### Credential report

> Credential status.

### Access Advisor

> Service access/last accessed information.

### Root

> Don't use for everyday operations; protect strongly with MFA.

### IAM

> Global service.

---

# 65. Scenario Recognition

## Scenario A

A developer's EC2 application needs to read objects from S3 without storing AWS credentials in the application.

### Answer

**IAM role attached to the EC2 instance.**

### Reasoning

```
EC2 workload
 ↓
Needs AWS permissions
 ↓
Avoid long-term credentials
 ↓
IAM role
```

---

## Scenario B

A company has 100 developers who all need the same read-only EC2 permissions.

### Answer

**Create an IAM group and attach an appropriate policy.**

```
Developers
    ↓
EC2 ReadOnly
    ↓
100 users
```

---

## Scenario C

A security administrator wants to identify IAM users that don't have MFA enabled.

### Answer

**IAM credential report** can help audit MFA status.

---

## Scenario D

An organization wants to determine which AWS services an IAM identity has recently accessed.

### Answer

**IAM Access Advisor / last accessed information.**

---

## Scenario E

An EC2 application has an AWS access key hard-coded in its source code.

### Problem

Long-term credentials are being exposed to a workload.

### Better approach

**Use an IAM role and temporary credentials.**

---

## Scenario F

A company wants developers to access only the AWS services necessary for their job.

### Answer

**Least privilege.**

---

## Scenario G

An administrator wants to require passwords to contain certain characters and have a specific minimum length.

### Answer

**IAM password policy.**

---

## Scenario H

A role should only be assumable by EC2.

### Relevant concept

**Trust policy.**

---

# 66. 🧠 HARD EXAM SIMULATION

Try these **before looking at the answer key**.

---

### Question 1

A company runs an application on an EC2 instance. The application must read objects from an S3 bucket. The company wants to avoid storing long-term AWS credentials on the instance.

What should the company use?

A. IAM group  
B. IAM role  
C. IAM user with AdministratorAccess  
D. Root user

---

### Question 2

A company has 50 employees who all need the same read-only permissions for Amazon EC2.

What is the most efficient IAM design?

A. Create one shared IAM user  
B. Give every employee root access  
C. Create individual IAM users and place them in an IAM group with the required policy  
D. Create 50 separate inline policies

---

### Question 3

A security administrator wants to identify which IAM users have MFA enabled and whether access keys are present.

Which IAM feature is most appropriate?

A. Access Advisor  
B. Credential report  
C. Security group  
D. IAM role

---

### Question 4

A developer wants to determine which AWS services an IAM identity has accessed and when they were last accessed.

Which capability is most relevant?

A. Credential report  
B. Access Advisor  
C. IAM password policy  
D. Security group

---

### Question 5

A company wants to restrict an employee so they can perform only the AWS operations necessary for their job.

Which principle should the company apply?

A. High availability  
B. Least privilege  
C. Elasticity  
D. Fault tolerance

---

### Question 6

Which component of an IAM role determines who or what can assume the role?

A. Permissions policy  
B. Trust policy  
C. Password policy  
D. Access key

---

### Question 7

Which statement correctly describes an IAM role?

A. It is permanently associated with a single human and always requires a password.  
B. It provides temporary credentials when assumed.  
C. It is a collection of IAM users.  
D. It is an AWS networking firewall.

---

### Question 8

An organization wants to prevent an attacker who obtains an IAM user's password from immediately accessing AWS resources.

What additional security control should the organization use?

A. MFA  
B. CloudShell  
C. IAM group  
D. Access Advisor

---

### Question 9

A developer needs to write a program that makes calls to Amazon S3 using Python.

Which method is most appropriate for programmatic interaction with AWS from the application?

A. AWS Management Console  
B. AWS SDK  
C. IAM group  
D. CloudShell only

---

### Question 10

An administrator wants to run AWS CLI commands without installing the AWS CLI on their local computer.

Which AWS capability can provide a browser-based shell environment?

A. IAM  
B. CloudShell  
C. Access Advisor  
D. AWS Artifact

---

### Question 11

Which statement is correct?

A. IAM groups can authenticate directly.  
B. IAM policies define permissions.  
C. IAM roles require permanent passwords.  
D. IAM policies are used only by the AWS Management Console.

---

### Question 12

A company discovers that an EC2 application contains an access key in its source code. What is the best general improvement?

A. Give the access key AdministratorAccess  
B. Share the key with the development team  
C. Use an IAM role with temporary credentials  
D. Put the key into a public repository so AWS can detect it

---

### Question 13

A company wants to define a policy that allows an identity to read objects from one specific S3 bucket.

Which policy elements are most directly relevant?

A. Effect, Action, Resource  
B. Region, AZ, Edge Location  
C. Username, password, MFA  
D. CPU, memory, storage

---

### Question 14

Which statement about IAM policies is correct?

A. An explicit Deny can be overridden by an Allow.  
B. Effect can specify Allow or Deny.  
C. Action identifies the person signing in.  
D. Resource identifies the password used for authentication.

---

### Question 15

A security administrator wants to know whether a role's permissions can be reduced because some granted services have never been used.

Which IAM capability can help?

A. Access Advisor / last accessed information  
B. CloudShell  
C. MFA  
D. AWS Console UI

---

# 67. Answer Key

|#|Answer|Tested Concept|
|---|---|---|
|1|**B**|IAM roles for EC2|
|2|**C**|Users + groups|
|3|**B**|Credential report|
|4|**B**|Access Advisor|
|5|**B**|Least privilege|
|6|**B**|Trust policy|
|7|**B**|Temporary role credentials|
|8|**A**|MFA|
|9|**B**|SDK|
|10|**B**|CloudShell|
|11|**B**|Policies|
|12|**C**|Roles vs long-term keys|
|13|**A**|Policy structure|
|14|**B**|Effect|
|15|**A**|Access Advisor / last accessed|

---

# 68. Detailed Reasoning for the Hard Questions

### Q1 — Why IAM Role?

The critical clues are:

> EC2 + S3 + don't store long-term credentials.

That is the classic:

```
EC2
 ↓
IAM Role
 ↓
Temporary credentials
 ↓
S3
```

AWS specifically recommends roles for applications running on EC2. [AWS Documentation](https://docs.aws.amazon.com/us_en/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html?utm_source=chatgpt.com)

---

### Q2 — Why Group?

The critical phrase:

> "50 employees need the same permissions."

Don't create a shared user.

Instead:

```
Individual users
       ↓
IAM group
       ↓
Shared policy
```

This maintains individual identities while making permission management easier.

---

### Q3 — Why Credential Report?

The question asks about:

> MFA + passwords + access keys + credential status.

That's exactly what the credential report is designed to help audit. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_getting-report.html?utm_source=chatgpt.com)

---

### Q4 — Why Access Advisor?

The question asks:

> "Which AWS services has this identity accessed?"

That's access/last-accessed information.

Therefore:

**Access Advisor.**

---

### Q5 — Why Least Privilege?

The phrase:

> "Only the permissions necessary."

is practically the definition of least privilege. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?utm_source=chatgpt.com)

---

### Q6 — Why Trust Policy?

Remember:

```
Trust policy
→ WHO?

Permissions policy
→ WHAT?
```

That's one of the most useful IAM distinctions for the exam.

---

### Q12 — Why Role?

An access key embedded in application code creates a long-term credential exposure problem.

Better:

```
Application
 ↓
IAM Role
 ↓
Temporary credentials
```

---

# 69. Final IAM Mental Model

This is the part I'd **actually memorize**.

```
                         IAM
                          │
        ┌─────────────────┼──────────────────┐
        ↓                 ↓                  ↓
      USER              GROUP              ROLE
       │                  │                  │
       │                  │                  ├── Trust Policy
       │                  │                  │       ↓
       │                  │                  │   WHO can assume?
       │                  │                  │
       └─────────┬────────┘                  └── Permissions
                 │                               ↓
                 └──────────────┐            WHAT can it do?
                                ↓
                             POLICY
                                ↓
                       AWS permissions
                                ↓
                          AWS resources
```

Security layer:

```
MFA
 ↓
Protect identities

Least privilege
 ↓
Minimize permissions

Credential report
 ↓
Audit credentials

Access Advisor
 ↓
Review service usage

IAM Roles
 ↓
Temporary credentials

Access keys
 ↓
Programmatic access
```

---

# 70. Last-Day IAM Cheat Sheet

|If you see...|Think...|
|---|---|
|Individual identity|IAM User|
|Collection of users|IAM Group|
|Temporary credentials|IAM Role|
|EC2 application needs AWS access|IAM Role|
|Lambda needs AWS access|IAM Role|
|"Who can assume role?"|Trust Policy|
|"What can role do?"|Permissions Policy|
|Permissions|IAM Policy|
|Only required permissions|Least Privilege|
|Second authentication factor|MFA|
|Programmatic credentials|Access Keys|
|Command line|AWS CLI|
|Application code|AWS SDK|
|Browser terminal|CloudShell|
|Password requirements|IAM Password Policy|
|MFA/access-key/password status|Credential Report|
|Services accessed/last accessed|Access Advisor|
|Daily AWS administration|Don't use Root|
|Protect root|MFA|
|Shared employee password|❌ Don't do it|
|Network ports|Security Groups/NACLs, not IAM|
|`Allow` / `Deny`|Effect|
|AWS operation|Action|
|AWS resource|Resource|
|Who in resource policy|Principal|
|Conditions|Condition|

---

## The 10 IAM facts I'd prioritize for your CLF-C02

If you don't want to memorize this entire chapter equally, prioritize these:

1. **IAM controls authentication and authorization for AWS resources.**
2. **Users = identities; groups = collections of users.**
3. **Roles provide temporary credentials and are heavily used by AWS services/workloads.**
4. **Policies define permissions.**
5. **Least privilege = only grant required permissions.**
6. **MFA adds an additional authentication factor.**
7. **Don't use the root user for everyday tasks; protect it with MFA.**
8. **Use IAM roles instead of embedding long-term access keys in EC2/Lambda workloads.**
9. **Credential Report = credential status; Access Advisor = service access/last accessed.**
10. **Trust policy = who can assume a role; permissions policy = what the role can do.**

Those ten ideas cover a **huge percentage of the IAM reasoning you'll need at Cloud Practitioner level**. Current AWS guidance also strongly emphasizes MFA, least privilege, temporary credentials, protecting root credentials, and reviewing unused permissions. [AWS Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?utm_source=chatgpt.com)**