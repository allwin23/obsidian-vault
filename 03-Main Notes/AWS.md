| Phase                 | What to Know (Checklist)                                                                                                                                                                                                   | Status |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| **Cloud Basics**      | Cloud computing basics; IaaS / PaaS / SaaS; Public vs Private vs Hybrid cloud; Benefits (scalability, elasticity, pay-as-you-go); AWS Global Infrastructure; Regions vs AZs vs Edge locations; Shared Responsibility Model | ⬜      |
| **Compute**           | EC2 (virtual servers); Lambda (serverless); Elastic Beanstalk (app deployment)                                                                                                                                             | ⬜      |
| **Storage**           | S3 (object storage); EBS (block storage); EFS (file storage)                                                                                                                                                               | ⬜      |
| **Databases**         | RDS (relational); DynamoDB (NoSQL)                                                                                                                                                                                         | ⬜      |
| **Networking**        | VPC (basic idea); Route 53 (DNS); CloudFront (CDN)                                                                                                                                                                         | ⬜      |
| **Security**          | IAM users, roles, policies; Root user best practices; MFA; Encryption at rest vs in transit; AWS Shield; AWS WAF; Compliance basics                                                                                        | ⬜      |
| **Billing & Pricing** | Pay-as-you-go; Free Tier; On-Demand vs Reserved vs Spot; Pricing Calculator; Cost Explorer; AWS Support plans                                                                                                              | ⬜      |
| **Practice**          | Topic-wise MCQs; 2–3 full practice exams; Review wrong answers; Score ≥70% consistently                                                                                                                                    | ⬜      |
| **Final Prep**        | Flashcards; Service comparisons; Official AWS Practice Exam; Book exam; Exam-day revision                                                                                                                                  | ⬜      |

### BASICS 


### **Compliance (Simple Meaning)**

- Compliance means following **laws, regulations, and industry standards**
    
- Ensures **data security, privacy, and controlled access**
    
- In cloud, compliance decides:
    
    - Where data can be stored
        
    - How data must be protected
        
    - Who can access the data
        

---

### **Deployment Scenarios Based on Compliance**

#### **Scenario 1: Healthcare Application (HIPAA / patient data)**

- **Deployment:** Private Cloud
    
- **Why:** Medical data is highly sensitive and legally restricted
    
- **Characteristics:**
    
    - Private VPC with private subnets
        
    - Encryption at rest and in transit
        
    - Strict IAM roles and MFA
        
    - No public internet access
        

---

#### **Scenario 2: Banking / FinTech Platform (PCI-DSS)**

- **Deployment:** Hybrid Cloud
    
- **Why:** Financial data needs strong compliance + cloud scalability
    
- **Characteristics:**
    
    - Core payment systems in private VPC or on-prem
        
    - Public cloud used for analytics and dashboards
        
    - Logging, monitoring, auditing enabled
        
    - Encryption and access controls enforced
        

---

#### **Scenario 3: Startup Website / Mobile App (non-sensitive data)**

- **Deployment:** Public Cloud
    
- **Why:** Focus on scalability, speed, and cost efficiency
    
- **Characteristics:**
    
    - Managed services (S3, CloudFront, Lambda, DynamoDB)
        
    - Public internet access allowed
        
    - Minimal compliance constraints
        
    - Pay-as-you-go pricing
        

---

### **Quick Cheatcodes (Exam-Friendly)**

- Highly regulated data → **Private Cloud**
    
- Mixed sensitive + scalable workloads → **Hybrid Cloud**
    
- Public apps / startups / cost-first systems → **Public Cloud**
    
- Law-driven requirements → **Private**
    
- Business growth-driven needs → **Public**
    
- Law + business together → **Hybrid**
    

---

## Shared Responsibility Model 

The **Shared Responsibility Model** is a cloud computing framework that clearly defines the division of security and operational responsibilities between the **cloud service provider** and the **customer**. It ensures that both parties understand what they are accountable for when using cloud services, thereby reducing security risks and operational confusion.

Under this model, the **cloud service provider** is responsible for **security _of_ the cloud**. This includes managing and securing the physical data centers, networking infrastructure, servers, storage systems, and the underlying virtualization layer. The provider also ensures physical security, hardware maintenance, and availability of the cloud platform.

The **customer**, on the other hand, is responsible for **security _in_ the cloud**. This involves managing user access, configuring network security controls such as firewalls, protecting data through encryption, managing operating systems and applications (depending on the service model), and ensuring compliance with organizational and regulatory requirements.

The exact division of responsibilities varies based on the cloud service model—**Infrastructure as a Service (IaaS)**, **Platform as a Service (PaaS)**, and **Software as a Service (SaaS)**. As organizations move from IaaS to SaaS, more responsibilities shift from the customer to the cloud provider.

Overall, the Shared Responsibility Model promotes accountability, improves security posture, and enables organizations to securely adopt cloud computing by clearly defining roles and responsibilities.


---- 
### EC2




