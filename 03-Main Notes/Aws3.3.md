# Task Statement 3.1 — Design Considerations for Applications That Use Foundation Models

## 🎯 Exam Essentials

### **1. Inference**

- **Concept:** Inference is the process of processing new data through a model to generate an output or prediction.
    
- **Input:** A **prompt** can be provided as input to a foundation model.
    
- **Amazon Bedrock:** Provides the ability to run inference against a selected foundation model.
    
- **Exam trigger:** **New input → model processes it → prediction/output = inference.**
    

---

### **2. Inference Parameters**

- **Concept:** Inference parameters are values that can be adjusted to influence or limit a model's response.
    
- **Purpose:** They control characteristics such as **randomness, diversity, and response length**.
    
- **Exam trigger:** If a question asks how to control the behavior of a foundation-model response, consider **inference parameters**.
    

---

### **3. Temperature**

- **Concept:** Temperature is an inference parameter supported by Amazon Bedrock foundation models.
    
- **Purpose:** It is used to control **randomness** in model responses.
    
- **Exam trigger:** **Randomness → Temperature.**
    

---

### **4. Top K**

- **Concept:** Top K is an inference parameter supported by Amazon Bedrock foundation models.
    
- **Purpose:** It is used to control **randomness and diversity** in responses.
    
- **Exam trigger:** If the scenario focuses on controlling response diversity/randomness, consider **Top K**.
    

---

### **5. Top P**

- **Concept:** Top P is an inference parameter supported by Amazon Bedrock foundation models.
    
- **Purpose:** It is used to control **randomness and diversity** in responses.
    
- **Exam trigger:** **Randomness/diversity → Top P** can be relevant.
    

---

### **6. Response Length**

- **Concept:** Response-length parameters can be used to limit the length of model responses.
    
- **Purpose:** Helps control how much output the model generates.
    
- **Exam trigger:** If the requirement is specifically to **limit response length**, look for response-length controls.
    

---

### **7. Penalties and Stop Sequences**

- **Concept:** Amazon Bedrock supports parameters such as **penalties and stop sequences** to limit response length.
    
- **Purpose:** These parameters can constrain the generated response.
    
- **Exam trigger:** If the scenario requires controlling when or how generation stops, consider **stop sequences**.
    

---

### **8. Experimentation With Inference Parameters**

- **Concept:** Different combinations of prompts and inference parameters can be tested before integrating inference into an application.
    
- **Available model types mentioned:** **Base models, custom models, and provisioned models.**
    
- **Goal:** Find an appropriate balance between **diversity, coherence, and resource efficiency**.
    
- **Exam trigger:** If a scenario describes testing multiple parameter configurations before production, this is part of **model experimentation/optimization**.
    

---

### **9. Continuous Monitoring of Inference Parameters**

- **Concept:** Parameter settings should not necessarily remain fixed after deployment.
    
- **Requirement:** Continuously **monitor and adjust** parameters in production.
    
- **Goal:** Maintain optimal performance and align with changing requirements.
    
- **Exam trigger:** If requirements evolve after deployment, consider **monitoring and adjusting inference parameters**.
    

---

### **10. Prompt Engineering**

- **Concept:** AWS defines prompts as specific inputs provided by a user to guide an LLM toward an appropriate response or output.
    
- **Purpose:** Prompts provide the model with the **task or instruction** it should perform.
    
- **Exam trigger:** **User input that guides an LLM's response → prompt.**
    

---

### **11. Contextual Data in Prompts**

- **Concept:** Prompts can be enriched with contextual data from internal databases or other data stores.
    
- **Purpose:** Additional domain-specific information can provide relevant context for the model.
    
- **Exam trigger:** If a scenario describes supplying an LLM with information retrieved from an organization's own data, consider **context augmentation/RAG**.
    

---

### **12. Retrieval-Augmented Generation (RAG)**

- **Concept:** RAG combines information retrieval with model generation.
    
- **Process:** Relevant information is retrieved from external data sources and used to augment the model's response-generation process.
    
- **Purpose:** Provides the model with additional external/domain-specific knowledge.
    
- **Exam trigger:** **Retrieve external information → augment prompt/context → generate response = RAG.**
    

---

### **13. Vector Embeddings**

- **Concept:** Embeddings convert words, sentences, images, or other data into numerical representations.
    
- **Purpose:** These numerical representations capture the **meaning and relationships** of the original data.
    
- **Exam trigger:** **Meaning represented numerically → embeddings.**
    

---

### **14. Vector Databases**

- **Concept:** A vector database stores data as mathematical representations, particularly **vector embeddings**.
    
- **Data:** Can contain structured and unstructured information such as **text and images** represented through embeddings.
    
- **Purpose:** Provides efficient lookup and retrieval of relevant information.
    
- **Exam trigger:** If the question describes storing embeddings and efficiently searching for semantically relevant information, think **vector database**.
    

---

### **15. Embedding Model as a Prerequisite**

- **Concept:** The transcript states that an ML model—generally an **embedding model**—processes input data to create the vectors stored in a vector database.
    
- **Key distinction:** The vector database stores/indexes the vectors; the embedding model creates the numerical representations.
    
- **Exam trigger:** **Embedding model → creates embeddings; vector database → stores/indexes them.**
    

---

### **16. Vector Databases as External Knowledge**

- **Concept:** Vector databases can act as an external data source for foundation-model applications.
    
- **Purpose:** They can provide factual/reference information to improve capabilities such as **search, recommendations, and text generation**.
    
- **Exam trigger:** If an LLM needs access to external organizational knowledge without relying only on its existing model knowledge, consider a **vector database + RAG architecture**.
    

---

### **17. Vector Database Capabilities**

- **Concept:** Beyond storing vectors, vector databases provide capabilities for working with and retrieving data.
    
- **Capabilities mentioned:**  
    **Efficient lookup, fast lookup, data management, fault tolerance, authentication, access control, and query engine.**
    
- **Exam trigger:** If a question describes infrastructure needed for managing and efficiently retrieving embedding-based data, think **vector database**.
    

---

### **18. Amazon Bedrock Knowledge Bases**

- **Concept:** Amazon Bedrock Knowledge Bases can collect data sources into a repository of information.
    
- **Purpose:** They can be used to build applications that take advantage of **RAG**.
    
- **Exam trigger:** **Bedrock + repository of external information + RAG → Knowledge Bases.**
    

---

### **19. Foundation Model Customization Tradeoffs**

- **Concept:** The appropriate approach depends on the application's **needs, resources, constraints, and objectives**.
    
- **Approaches mentioned:**  
    **Pre-training, fine-tuning, in-context learning, and RAG.**
    
- **Exam trigger:** When a question asks how to adapt/customize a foundation model, compare the approaches based on the scenario's requirements and cost tradeoffs.
    

---

## 🔑 Key Terms

|Term|Exam-focused meaning|
|---|---|
|**Inference**|Processing new input through a model to generate an output/prediction|
|**Prompt**|Input provided to an LLM to guide its response|
|**Inference parameter**|Adjustable value that influences model response behavior|
|**Temperature**|Inference parameter used to control randomness|
|**Top K**|Parameter used to control randomness/diversity|
|**Top P**|Parameter used to control randomness/diversity|
|**Response length**|Control for limiting the length of generated output|
|**Penalty**|Inference parameter mentioned for limiting/controlling response generation|
|**Stop sequence**|Parameter used to limit/stop response generation|
|**Prompt engineering**|Designing inputs that guide an LLM toward an appropriate output|
|**RAG**|Retrieves external information to augment model response generation|
|**Embedding**|Numerical representation capturing meaning and relationships in data|
|**Embedding model**|ML model generally used to create vector embeddings|
|**Vector database**|Database storing/indexing vector representations for efficient retrieval|
|**Amazon Bedrock Knowledge Bases**|Bedrock capability for collecting data sources into an information repository for RAG|
|**Base model**|Model type mentioned as supporting inference experimentation|
|**Custom model**|Customized model against which inference can be run|
|**Provisioned model**|Model type mentioned as supporting inference experimentation|
|**Foundation model customization**|Adapting a foundation model using approaches such as fine-tuning, in-context learning, or RAG|

---

## ⚔️ Important Comparisons

|Service / Concept|Use when|Key distinction|
|---|---|---|
|**Temperature**|Controlling response randomness|Inference parameter associated with randomness|
|**Top K**|Controlling response randomness/diversity|Selects based on the K-related sampling setting|
|**Top P**|Controlling response randomness/diversity|Uses the P-related sampling setting|
|**Response length**|Limiting generated output|Controls how much response is produced|
|**Stop sequence**|Controlling where generation stops|Defines a stopping condition for generation|
|**Prompt**|Providing instructions/input|Guides what the model should generate|
|**Vector embedding**|Representing data numerically|Numerical representation of meaning/relationships|
|**Embedding model**|Creating embeddings|ML model processes input to produce vectors|
|**Vector database**|Storing/indexing embeddings|Provides storage, search, retrieval, and data-management capabilities|
|**RAG**|Using external information during generation|Retrieves relevant information and augments model generation|
|**Foundation model**|Generating outputs from learned capabilities|Model performs generation/inference|
|**Vector database**|Supplying external/reference information|External knowledge source used by the application|

---

## 🧠 Exam Traps

### **1. Inference vs. Training**

**Trap:** Inference means training the model on new data.

**Correct:** Inference is the process of **processing new input through a model to generate an output/prediction**.

---

### **2. Prompt vs. Inference Parameter**

**Trap:** A prompt and an inference parameter are the same thing.

**Correct:** A **prompt is the input/instruction**; inference parameters are adjustable values that influence the model's response.

---

### **3. Temperature**

**Trap:** Temperature is primarily used to limit the number of tokens in a response.

**Correct:** In the transcript, temperature is associated with controlling **randomness**.

---

### **4. Top K and Top P**

**Trap:** Top K and Top P are used only to control response length.

**Correct:** The transcript associates both with controlling **randomness and diversity**.

---

### **5. Response Length**

**Trap:** Increasing response diversity automatically determines how long the response will be.

**Correct:** **Response-length controls** are specifically used to limit output length.

---

### **6. RAG Is Model Training**

**Trap:** RAG requires retraining the foundation model whenever new information is added.

**Correct:** RAG retrieves information from external data sources and **augments generation with that information**.

---

### **7. Vector Database Creates Embeddings**

**Trap:** A vector database converts text into embeddings.

**Correct:** The transcript states that an **ML model, generally an embedding model, creates the embeddings**, which are then stored/indexed in the vector database.

---

### **8. Embedding vs. Vector Database**

**Trap:** An embedding and a vector database are the same thing.

**Correct:** An **embedding is a numerical representation**; a **vector database stores and indexes vector representations**.

---

### **9. Vector Database vs. ML Model**

**Trap:** A vector database is itself the machine learning model responsible for understanding the data.

**Correct:** The transcript distinguishes them: the **ML/embedding model creates the vectors**, while the vector database stores and retrieves them.

---

### **10. RAG vs. Vector Database**

**Trap:** RAG and a vector database are interchangeable terms.

**Correct:** A **vector database can provide the retrieval infrastructure**, while **RAG is the technique of retrieving information and using it to augment generation**.

---

### **11. Internal Data + LLM**

**Trap:** Adding internal organizational data to an LLM prompt means the foundation model has permanently learned that data.

**Correct:** The transcript describes contextual data being added to prompts and used through approaches such as **RAG**; this is external contextual information used during generation.

---

### **12. Production Parameters**

**Trap:** Once optimal inference parameters are found during testing, they should never change.

**Correct:** The transcript recommends **continuously monitoring and adjusting** parameters in production as requirements evolve.

---

### **13. Customization Cost**

**Trap:** Every foundation-model customization approach has the same cost and resource requirements.

**Correct:** The transcript specifically highlights **cost tradeoffs** among pre-training, fine-tuning, in-context learning, and RAG.

---

### **14. Bedrock Knowledge Bases**

**Trap:** Bedrock Knowledge Bases are themselves foundation models.

**Correct:** They provide a way to collect data sources into a repository that can support **RAG-based applications**.

---

# 📝 Exam Questions

### **Q1.**

An application generates highly variable responses, and the development team wants to adjust how random the model's responses are without changing the underlying foundation model.

Which inference parameter should the team consider?

**A.** Response length  
**B.** Temperature  
**C.** Stop sequence  
**D.** Embedding dimension

**Answer: B**

**Why:** The transcript identifies **temperature** as an inference parameter used to control randomness.

---

### **Q2.**

A company wants its LLM application to answer questions using information stored in its internal knowledge repository. The team does not want the model to rely only on the information available within the foundation model.

Which approach best matches the transcript?

**A.** Increase model complexity and retrain the foundation model on every query  
**B.** Use RAG to retrieve relevant external information and augment generation  
**C.** Increase response length so more internal information can be generated  
**D.** Use temperature to inject organizational information into the model

**Answer: B**

**Why:** **RAG retrieves external information and uses it to augment model response generation.**

---

### **Q3.**

A developer creates embeddings from internal documents and needs infrastructure that can efficiently store, index, and retrieve those embeddings.

Which component is most directly suited to this requirement?

**A.** Foundation model  
**B.** Vector database  
**C.** Prompt template  
**D.** Temperature parameter

**Answer: B**

**Why:** The transcript describes vector databases as storing/indexing vectors and providing **efficient lookup and retrieval** capabilities.

---

### **Q4.**

An organization wants to build a vector database from a collection of text documents. Before storing the vectors, the text must be converted into numerical representations that capture meaning and relationships.

What is generally responsible for this conversion?

**A.** Query engine  
**B.** Embedding model  
**C.** Stop sequence  
**D.** Foundation-model temperature

**Answer: B**

**Why:** The transcript states that input data is generally processed by an **embedding model** to create dense vectors.

---

### **Q5.**

An application produces responses that are too long for its user interface. The development team wants to constrain the amount of generated output while continuing to use the same foundation model.

Which category of inference control is most relevant?

**A.** Response-length parameters  
**B.** Embedding parameters  
**C.** Modality parameters  
**D.** Training-data parameters

**Answer: A**

**Why:** The transcript identifies **response length** and related controls as parameters used to limit generated output.

---

### **Q6.**

A team has tested a foundation model with several prompts and inference-parameter configurations. After deployment, the application's requirements change and the original parameter settings no longer provide the desired balance.

What does the transcript recommend?

**A.** Freeze the original parameters because inference settings should remain constant  
**B.** Replace the foundation model whenever application requirements change  
**C.** Continuously monitor and adjust inference parameters in production  
**D.** Convert all prompts into vector embeddings before changing parameters

**Answer: C**

**Why:** The transcript explicitly recommends **continuous monitoring and adjustment** of inference parameters in production.

---

### **Q7.**

A developer wants to control the randomness and diversity of responses produced by an Amazon Bedrock foundation model.

Which combination contains inference parameters identified in the transcript for this purpose?

**A.** Temperature, Top K, and Top P  
**B.** Response length, MAE, and RMSE  
**C.** Stop sequences, embeddings, and vector indexes  
**D.** Prompt length, model layers, and training epochs

**Answer: A**

**Why:** The transcript identifies **temperature, Top K, and Top P** as parameters for controlling randomness/diversity.

---

### **Q8.**

A company wants to distinguish between the component that creates numerical representations of documents and the component that stores and retrieves those representations.

Which mapping is correct?

**A.** Vector database creates embeddings; ML model stores them  
**B.** Embedding model creates embeddings; vector database stores/indexes them  
**C.** Foundation model creates embeddings; prompt stores them  
**D.** Query engine creates embeddings; RAG permanently stores them

**Answer: B**

**Why:** The transcript explicitly distinguishes the **embedding model** from the **vector database**.

---

### **Q9.**

A team is evaluating four approaches for adapting a foundation model to a business application. The team wants to understand the resource and cost tradeoffs before selecting an approach.

Which set of approaches is specifically identified in the transcript?

**A.** Pre-training, fine-tuning, in-context learning, and RAG  
**B.** Classification, regression, clustering, and dimensionality reduction  
**C.** Encryption, authentication, authorization, and monitoring  
**D.** Tokenization, stemming, parsing, and normalization

**Answer: A**

**Why:** The transcript specifically identifies **pre-training, fine-tuning, in-context learning, and RAG** as approaches whose cost tradeoffs should be understood.

---

### **Q10.**

An organization wants to build an Amazon Bedrock application that collects organizational data sources into a repository and uses that information to support retrieval-augmented generation.

Which capability mentioned in the transcript directly supports this architecture?

**A.** Amazon Bedrock Knowledge Bases  
**B.** Amazon Bedrock temperature controls  
**C.** Amazon Bedrock stop sequences  
**D.** Amazon Bedrock model parameters

**Answer: A**

**Why:** The transcript describes **Amazon Bedrock Knowledge Bases** as collecting data sources into a repository for applications using **RAG**.

---

## ⚡ 30-Second Revision

**1. Inference →** process new input through a model to generate output.

**2. Prompt →** input/instruction given to an LLM.

**3. Temperature →** controls **randomness**.

**4. Top K + Top P →** control **randomness/diversity**.

**5. Response length →** limits generated output.

**6. Stop sequence →** helps control/limit where generation stops.

**7. Production →** monitor and adjust inference parameters as requirements evolve.

**8. Embedding →** numerical representation capturing meaning/relationships.

**9. Embedding model →** **creates** embeddings.

**10. Vector database →** **stores/indexes/retrieves** embeddings.

**11. RAG →** retrieve external information → augment generation.

**12. Vector DB ≠ RAG →** vector DB is retrieval infrastructure; RAG is the retrieval + generation technique.

**13. Bedrock Knowledge Bases →** repository/data-source capability supporting RAG.

**14. Customization approaches →** **pre-training, fine-tuning, in-context learning, RAG**.

**15. Core exam chain →** **Data → embedding model → vectors → vector database → retrieval → RAG → foundation model → response.**