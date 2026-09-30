# Task Statement 3.1 — Design Considerations for Applications That Use Foundation Models

## 🎯 Exam Essentials

### **1. RAG Has Two Core Components**

- **Concept:** Retrieval-Augmented Generation (RAG) combines a **retriever** and a **generator**.
    
- **Retriever:** Searches a knowledge base for relevant information.
    
- **Generator:** Produces the final output using the retrieved information.
    
- **Exam trigger:** **Retriever = finds information; Generator = produces response.**
    

---

### **2. Purpose of RAG**

- **Concept:** RAG allows foundation models/LLMs to access **up-to-date and domain-specific knowledge** beyond their original training data.
    
- **Key benefit:** External information can be incorporated into the generation process.
    
- **Exam trigger:** If a scenario requires an LLM to use **current, organization-specific, or domain-specific information**, consider RAG.
    

---

### **3. RAG Query Flow**

- **Step 1:** User provides a prompt/query.
    
- **Step 2:** The query is passed to a **query encoder**.
    
- **Step 3:** The query is encoded/embedded into the same format as the external data.
    
- **Step 4:** The embedding is passed to the **vector database**.
    
- **Step 5:** The vector database searches for similar embeddings.
    
- **Step 6:** The **retriever** retrieves the relevant information.
    
- **Step 7:** Retrieved information is combined with/augments the original prompt.
    
- **Step 8:** The augmented prompt is sent to the **LLM**.
    
- **Step 9:** The LLM generates the final completion.
    
- **Exam trigger:** Remember the chain: **Query → Embedding → Vector search → Retrieve → Augment → LLM → Response.**
    

---

### **4. RAG and Hallucinations**

- **Concept:** Generative LLMs can produce **believable but factually incorrect responses**, called hallucinations.
    
- **RAG's role:** RAG complements the LLM with an **external knowledge base**.
    
- **Knowledge base:** The transcript describes it as typically being built using a vector database containing vector-coded knowledge articles.
    
- **Exam trigger:** **Hallucination risk + external factual knowledge → RAG.**
    

---

### **5. RAG Use Cases**

- **Applications mentioned:**
    
    - Question-answering
        
    - Dialogue systems
        
    - Content generation
        
- **Key requirement:** External knowledge can be used to provide more accurate and contextually relevant responses.
    
- **Exam trigger:** If an LLM application needs to generate responses using external knowledge, RAG is relevant.
    

---

### **6. Vector Database Options on AWS**

- **Services mentioned in the transcript:**
    
    - Amazon OpenSearch Service
        
    - Amazon Aurora
        
    - Redis
        
    - Amazon Neptune
        
    - Amazon DocumentDB with MongoDB compatibility
        
    - Amazon RDS for PostgreSQL
        
- **Exam trigger:** If a question asks which AWS services can store embeddings/vector data, recognize these as options mentioned in the lesson.
    

---

### **7. Amazon OpenSearch Service**

- **Concept:** OpenSearch provides search capabilities including **low-latency search and aggregations**.
    
- **Additional capabilities mentioned:**
    
    - OpenSearch Dashboards
        
    - Visualization/dashboarding
        
    - Alerting
        
    - Fine-grained access control
        
    - Observability
        
    - Security monitoring
        
    - Vector storage and processing
        
- **Exam trigger:** When a scenario combines **search + vector capabilities + semantic search/RAG**, OpenSearch Service is highly relevant based on this transcript.
    

---

### **8. OpenSearch for Semantic Search**

- **Concept:** Semantic search uses **language-based embeddings** to improve search results.
    
- **Key distinction:** Rather than relying only on keyword matching, embeddings can be used to represent the meaning of search documents.
    
- **Example mentioned:** BERT is used to generate vectors, with Amazon SageMaker hosting the model and OpenSearch storing them.
    
- **Exam trigger:** **Embeddings + improved search relevance → semantic search.**
    

---

### **9. OpenSearch Serverless Vector Engine**

- **Concept:** The vector engine in Amazon OpenSearch Serverless provides **vector storage and search**.
    
- **Key benefit:** Helps build ML-augmented search and generative AI applications without managing the vector database infrastructure.
    
- **Exam trigger:** If the scenario emphasizes **managed vector storage/search without managing vector-database infrastructure**, consider OpenSearch Serverless vector capabilities.
    

---

### **10. Amazon Bedrock Knowledge Bases and RAG**

- **Concept:** Knowledge Bases for Amazon Bedrock provide a managed RAG capability.
    
- **Purpose:** They can securely connect foundation models to company data.
    
- **Architecture described:** Company data is stored as embeddings in the vector engine and retrieved to provide more relevant, context-specific responses.
    
- **Key benefit:** The transcript states this can improve responses **without continuously retraining the foundation model**.
    
- **Exam trigger:** **Company data + Bedrock + RAG + no continuous FM retraining → Knowledge Bases.**
    

---

### **11. Amazon RDS for PostgreSQL and pgvector**

- **Concept:** Amazon RDS for PostgreSQL supports the **pgvector extension**.
    
- **Purpose:** pgvector can be used to store embeddings and perform efficient searches.
    
- **Exam trigger:** **PostgreSQL + embeddings/vector search → pgvector.**
    

---

### **12. Foundation Models vs. Real-World Actions**

- **Concept:** Foundation models can understand and respond to queries based on their pre-trained knowledge.
    
- **Limitation described:** By themselves, they cannot complete real-world tasks such as **booking a flight or processing a purchase order**.
    
- **Reason:** These tasks require organization-specific **data, workflows, and custom programming**.
    
- **Exam trigger:** If the question requires the model to **take an action in an external system**, think beyond the foundation model itself.
    

---

### **13. Agents for Amazon Bedrock**

- **Concept:** Agents for Amazon Bedrock are a **fully managed AI capability** for building applications using foundation models.
    
- **Purpose:** Agents help applications perform multi-step tasks and interact with external systems.
    
- **Exam trigger:** **Multi-step task + external systems/actions → Agents.**
    

---

### **14. Agents Orchestrate Multi-Step Workflows**

- **Concept:** Agents are additional software that orchestrates workflows involving:
    
    - User requests
        
    - Foundation models
        
    - External data sources
        
    - External applications
        
- **Capabilities described:** Agents can automatically break down tasks and generate orchestration logic or custom code.
    
- **Exam trigger:** If a task requires multiple coordinated steps rather than simply generating text, consider an **agent**.
    

---

### **15. Agents and APIs**

- **Concept:** Agents can securely connect to databases through APIs.
    
- **Action capability:** Agents can automatically **call APIs to take actions**.
    
- **Example:** An agent could process a reservation workflow for a scuba-diving vacation.
    
- **Exam trigger:** **Need to perform an external action through an API → agent.**
    

---

### **16. Agents and Knowledge Bases**

- **Concept:** Agents can invoke knowledge bases to supplement information needed for actions.
    
- **Architecture:** The agent can combine retrieved knowledge with foundation-model reasoning/orchestration and external API actions.
    
- **Exam trigger:** **Knowledge retrieval + multi-step action → agent can orchestrate both.**
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**RAG**|Technique that retrieves external information and uses it to augment model generation|
|**Retriever**|RAG component that searches a knowledge base and retrieves relevant information|
|**Generator**|RAG component that produces output using retrieved information|
|**Query encoder**|Component that encodes/embeds the user's query into the representation used for retrieval|
|**Vector database**|Stores/indexes vector embeddings and supports similarity-based retrieval|
|**Embedding**|Numerical representation used to represent meaning/relationships in data|
|**Hallucination**|Believable but factually incorrect model-generated response|
|**Semantic search**|Search using language-based embeddings to improve retrieval relevance|
|**OpenSearch Service**|AWS search service with search, aggregation, and vector capabilities described in the transcript|
|**OpenSearch Serverless vector engine**|Managed vector storage and search capability|
|**Knowledge Bases for Amazon Bedrock**|Managed capability for connecting foundation models to external/company data for RAG|
|**pgvector**|PostgreSQL extension used to store embeddings and perform efficient searches|
|**Agent**|Software that orchestrates interactions between users, foundation models, data sources, and applications|
|**Orchestration**|Coordinating multiple steps, services, data sources, and actions in a workflow|
|**API**|Interface that agents can call to take actions in external systems|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Retriever**|Relevant external information must be found|Searches the knowledge base and retrieves information|
|**Generator**|Final response must be produced|Generates output using retrieved information|
|**RAG**|LLM needs external/current/domain-specific information|Retrieval augments generation|
|**Foundation model alone**|Generating responses from pre-trained knowledge|Does not inherently perform organization-specific external actions|
|**Vector database**|Storing/searching embeddings|Provides vector storage and retrieval|
|**Semantic search**|Improving search based on meaning|Uses embeddings rather than relying only on keyword matching|
|**OpenSearch Service**|Search + vector capabilities|Provides search, aggregation, dashboards, and vector capabilities|
|**OpenSearch Serverless vector engine**|Managed vector storage/search|Reduces the need to manage vector-database infrastructure|
|**Bedrock Knowledge Bases**|Building managed RAG applications using company data|Connects foundation models to external data for retrieval|
|**RDS for PostgreSQL + pgvector**|PostgreSQL-based embedding storage/search|Uses the pgvector extension|
|**Foundation model**|Understand/generate responses|Provides model intelligence based on pre-trained knowledge|
|**Bedrock Agent**|Multi-step workflows requiring actions|Orchestrates the FM, knowledge bases, APIs, and external applications|

---

## 🧠 Exam Traps

### **1. RAG Is Just a Vector Database**

**Trap:** RAG and vector databases are interchangeable.

**Correct:** A **vector database provides storage/retrieval**, while **RAG is the overall retrieval + generation technique**.

---

### **2. Retriever vs. Generator**

**Trap:** The generator searches the knowledge base for relevant information.

**Correct:** The **retriever searches and retrieves**; the **generator produces the response**.

---

### **3. RAG Requires Retraining**

**Trap:** A foundation model must be continuously retrained whenever the company's knowledge changes.

**Correct:** The transcript describes RAG as providing external information **without continuously retraining the foundation model**.

---

### **4. RAG Eliminates Hallucinations Completely**

**Trap:** Adding RAG guarantees that an LLM will never hallucinate.

**Correct:** The transcript says RAG **solves/complements this problem by providing external knowledge**; do not interpret this as an absolute guarantee.

---

### **5. Semantic Search = Keyword Search**

**Trap:** Semantic search simply searches for exact matching words.

**Correct:** Semantic search uses **language-based embeddings** to improve retrieval based on meaning.

---

### **6. Embedding Creation vs. Storage**

**Trap:** OpenSearch or a vector database creates the embeddings itself.

**Correct:** An embedding/model process creates the vectors; the vector database **stores and retrieves** them.

---

### **7. OpenSearch Serverless**

**Trap:** OpenSearch Serverless requires you to manage all vector-database infrastructure yourself.

**Correct:** The transcript highlights its vector engine as providing vector storage/search **without managing the vector database infrastructure**.

---

### **8. Knowledge Bases = Foundation Model**

**Trap:** Bedrock Knowledge Bases are themselves foundation models.

**Correct:** Knowledge Bases provide a **repository/data retrieval capability** that can support RAG with foundation models.

---

### **9. RDS PostgreSQL and Embeddings**

**Trap:** PostgreSQL cannot be used for vector embeddings.

**Correct:** The transcript states that **RDS for PostgreSQL supports pgvector** for storing embeddings and performing efficient searches.

---

### **10. Foundation Models Can Execute Any Task**

**Trap:** A foundation model can independently book flights or process purchase orders simply because it understands natural language.

**Correct:** These real-world tasks require **organization-specific data, workflows, and custom programming**.

---

### **11. Agent vs. Foundation Model**

**Trap:** An agent is simply another name for a foundation model.

**Correct:** An **agent is additional software that orchestrates interactions** between the user, foundation model, external data, and applications.

---

### **12. Agent vs. RAG**

**Trap:** RAG alone automatically performs external actions such as booking a reservation.

**Correct:** RAG provides **retrieved information**. Agents can additionally **orchestrate workflows and call APIs to take actions**.

---

### **13. Agents Only Generate Text**

**Trap:** Agents are useful only for generating more sophisticated responses.

**Correct:** Agents can break down tasks, orchestrate workflows, invoke knowledge bases, and **call APIs to take actions**.

---

# 📝 Exam Questions

### **Q1.**

A company's customer-support LLM frequently needs information from an internal knowledge repository that was updated after the foundation model's original training.

Which architecture best addresses this requirement?

**A.** Continuously retrain the foundation model whenever the repository changes  
**B.** Use RAG to retrieve relevant information and augment the model's generation  
**C.** Increase the foundation model's parameter count to include newer information  
**D.** Increase the model's response length so it can generate more current information

**Answer: B**

**Why:** RAG allows the model to use **external, up-to-date information** without continuously retraining the foundation model.

---

### **Q2.**

A user submits a question to an application. The application converts the question into an embedding and searches a vector database for similar embeddings before sending the retrieved information along with the question to an LLM.

Which component is responsible for searching the knowledge base and retrieving the relevant information?

**A.** Generator  
**B.** Retriever  
**C.** Foundation model  
**D.** API orchestrator

**Answer: B**

**Why:** The **retriever** searches the knowledge base and returns relevant information.

---

### **Q3.**

A company wants to improve search relevance by representing documents using language-based embeddings rather than relying only on keyword matching.

Which capability described in the transcript is most relevant?

**A.** Semantic search  
**B.** Response-length control  
**C.** Agent orchestration  
**D.** Model fine-tuning

**Answer: A**

**Why:** Semantic search uses **language-based embeddings** to improve the relevance of retrieved results.

---

### **Q4.**

An organization already uses Amazon RDS for PostgreSQL and wants to store embeddings and perform efficient vector searches without replacing its database technology.

Which capability should the organization consider?

**A.** pgvector  
**B.** OpenSearch Dashboards  
**C.** Bedrock Agents  
**D.** Top P

**Answer: A**

**Why:** The transcript specifically states that **RDS for PostgreSQL supports the pgvector extension** for storing embeddings and performing efficient searches.

---

### **Q5.**

A development team wants vector storage and search capabilities while avoiding the operational burden of managing the vector-database infrastructure.

Which capability from the transcript most directly addresses this requirement?

**A.** Amazon OpenSearch Serverless vector engine  
**B.** Amazon RDS for PostgreSQL without extensions  
**C.** Foundation-model inference parameters  
**D.** Bedrock prompt engineering

**Answer: A**

**Why:** The transcript specifically describes the **OpenSearch Serverless vector engine** as providing vector storage/search without managing the vector-database infrastructure.

---

### **Q6.**

A company wants its application to retrieve current internal information before generating an answer. The retrieved information should be combined with the user's original prompt before being sent to the LLM.

Which sequence best represents the described RAG workflow?

**A.** Prompt → LLM → vector database → retriever → response  
**B.** Prompt → query embedding → vector search → retrieval → prompt augmentation → LLM  
**C.** Prompt → retraining → embedding → LLM → vector database  
**D.** Prompt → generator → training dataset → vector database → response

**Answer: B**

**Why:** The transcript describes the flow as **query encoding → vector search → retrieval → augmentation → LLM generation**.

---

### **Q7.**

A travel company wants an AI application that can understand a customer's request, retrieve relevant company information, and then call an API to actually create a reservation.

Which capability best fits this requirement?

**A.** A foundation model alone  
**B.** A vector database alone  
**C.** An Amazon Bedrock agent  
**D.** A semantic search engine alone

**Answer: C**

**Why:** The transcript describes agents as orchestrating **foundation models, knowledge bases, and APIs**, including taking real-world actions.

---

### **Q8.**

A foundation model produces convincing answers that occasionally contain facts that are incorrect. The organization wants to provide the model with relevant information from its own knowledge repository during generation.

Which approach from the transcript is most directly applicable?

**A.** RAG using an external knowledge base  
**B.** Increasing response length  
**C.** Increasing model complexity  
**D.** Changing the semantic search algorithm without adding external knowledge

**Answer: A**

**Why:** The transcript connects RAG with addressing **hallucination risk** by complementing the LLM with an external knowledge base.

---

### **Q9.**

An organization wants an application that can retrieve information from a knowledge base but also perform a sequence of actions across external applications.

Which distinction is most important?

**A.** RAG retrieves information, while agents can orchestrate workflows and call APIs to take actions.  
**B.** RAG performs all API actions, while agents only generate text.  
**C.** Vector databases perform external actions, while RAG only stores embeddings.  
**D.** Foundation models perform external actions automatically without additional software.

**Answer: A**

**Why:** The transcript distinguishes **RAG's retrieval role** from the **agent's orchestration and action-taking role**.

---

### **Q10.**

A company wants to connect its foundation model securely to company data and use that data to provide context-specific responses without continuously retraining the foundation model.

Which capability described in the transcript is most directly aligned?

**A.** Amazon Bedrock Knowledge Bases  
**B.** Amazon Bedrock temperature  
**C.** Amazon Bedrock stop sequences  
**D.** Amazon Bedrock model parameters

**Answer: A**

**Why:** The transcript describes **Knowledge Bases for Amazon Bedrock** as a managed RAG capability for securely connecting foundation models to company data.

---

## ⚡ 30-Second Revision

**1. RAG = Retriever + Generator.**

**2. Retriever →** searches the knowledge base and retrieves relevant information.

**3. Generator →** produces the output using retrieved information.

**4. RAG →** gives FMs access to **up-to-date/domain-specific external knowledge**.

**5. RAG flow →** Query → Embedding → Vector Search → Retrieve → Augment → LLM → Response.

**6. Hallucination →** believable but factually incorrect model response.

**7. RAG →** external knowledge can help address hallucination risk.

**8. Semantic search →** embeddings improve search relevance based on meaning.

**9. OpenSearch →** search + aggregation + vector capabilities.

**10. OpenSearch Serverless vector engine →** managed vector storage/search without managing vector infrastructure.

**11. RDS PostgreSQL →** **pgvector** supports embedding storage/search.

**12. Bedrock Knowledge Bases →** managed RAG + company data.

**13. Foundation model alone →** generates/understands responses but doesn't inherently execute organization-specific workflows.

**14. Agent →** orchestrates **user + FM + knowledge base + APIs + external applications**.

**15. Agent + API →** can take real-world actions.

**16. Core distinction →** **RAG retrieves knowledge; agents orchestrate knowledge + actions.**