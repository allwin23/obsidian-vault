==

The course content focuses on Retrieval Augmented Generation (RAG) and its application in improving the accuracy and relevance of large language models (LLMs).

Understanding LLM Challenges

- LLMs can generate confident but incorrect answers, as illustrated by an anecdote about the number of moons in the solar system.
- Two main issues with LLMs are the lack of sourcing for information and the potential for outdated responses.

Retrieval Augmented Generation (RAG) Framework

- RAG enhances LLMs by incorporating a content store that retrieves relevant information before generating a response.
- This process allows the model to provide up-to-date and sourced answers, reducing the likelihood of hallucinations.

Benefits and Limitations of RAG

- RAG addresses the problem of outdated information by allowing updates to the content store without retraining the model.
- However, the effectiveness of RAG depends on the quality of the retrieval system; poor retrieval can lead to inadequate responses.
  ![[Pasted image 20260313230149.png]]



- **In-Memory Vector Databases**: These store vectors directly in memory, allowing for rapid read-and-write operations. They are ideal for applications requiring quick access, such as real-time analytics. Examples include RedisAI and Torchserve.
    
- **Disk-Based Vector Databases**: These store vectors on disk, making them suitable for large datasets that exceed memory capacity. They use sophisticated indexing techniques for efficient storage and retrieval. Examples include Annoy and Milvus.
    
- **Distributed Vector Databases**: These spread vector data across multiple nodes or servers, providing scalability and fault tolerance. They are designed for managing massive datasets and high-throughput tasks. FAISS is a notable example.
    
- **Graph-Based Vector Databases**: These model data as graphs, capturing complex relationships between data points. They are excellent for tasks like social network analysis. Neo4j is a well-known graph-based database.
    
- **Time-Series Vector Databases**: These manage data collected over time intervals, allowing for the analysis of temporal patterns. InfluxDB is an example that supports vector storage alongside time-stamped data.
  
  ### Chroma Db
- |Vector DB|Why used|
|---|---|
|**Pinecone**|Fully managed, production-scale vector DB|
|**Milvus**|Highly scalable distributed vector database|
|**Weaviate**|Strong hybrid search (vector + keyword)|
|**Qdrant**|High-performance open-source vector search|
|**Chroma**|Simple, lightweight, good for prototypes|
  Its not the greatest but easy at learn at inital
  
  
  Hierarchical Navigable Small World ​or HNSW for shor
  this i used 
  ### Creating Collections

Collections help organize your data in Chroma DB.

#### 🏗️ Create a Collection

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8
9. 9

10. `client = chromadb.Client()`
11. `collection = client.create_collection(`
12.     `name="filter_demo",`
13.     `metadata={"description": "Used to demo filtering in ChromaDB"},`
14.     `configuration={`
15.         `"embedding_function": ef`
16.     `}`
17. `)`
18. `print(f"Collection created: {collection.name}")`

Copied!Wrap Toggled!

**Output:**

1. 1

2. `Collection created: filter_demo`

Copied!Wrap Toggled!

---

### ➕ Adding Documents to Collections

Use `add` to insert documents with optional metadata.

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8
9. 9
10. 10
11. 11
12. 12
13. 13
14. 14
15. 15
16. 16
17. 17

18. `collection.add(`
19.     `documents=[`
20.         `"This is a document about LangChain",`
21.         `"This is a reading about LlamaIndex",`
22.         `"This is a book about Python",`
23.         `"This is a document about pandas",`
24.         `"This is another document about LangChain"`
25.     `],`
26.     `metadatas=[`
27.         `{"source": "langchain.com", "version": 0.1},`
28.         `{"source": "llamaindex.ai", "version": 0.2},`
29.         `{"source": "python.org", "version": 0.3},`
30.         `{"source": "pandas.pydata.org", "version": 0.4},`
31.         `{"source": "langchain.com", "version": 0.5},`
32.     `],`
33.     `ids=["id1", "id2", "id3", "id4", "id5"]`
34. `)`

Copied!Wrap Toggled!

### 🏷️ Filter using Metadata

The following finds all documents where the source is "langchain.com":

1. 1
2. 2
3. 3

4. `collection.get(`
5.     `where={"source": {"$eq": "langchain.com"}}`
6. `)`

Copied!Wrap Toggled!

**output**:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8
9. 9

10. `{'ids': ['id1', 'id5'],`
11.  `'embeddings': None,`
12.  `'documents': ['This is a document about LangChain',`
13.   `'This is another document about LangChain'],`
14.  `'uris': None,`
15.  `'included': ['metadatas', 'documents'],`
16.  `'data': None,`
17.  `'metadatas': [{'source': 'langchain.com', 'version': 0.1},`
18.   `{'version': 0.5, 'source': 'langchain.com'}]}`

Copied!Wrap Toggled!

The above produced correct output, but suppose we were only interested in LangChain documents with versions less than 0.3. The following finds all documents where the source is "langchain.com" with versions less than 0.3:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8

9. `collection.get(`
10.     `where={`
11.         `"$and": [`
12.             `{"source": {"$eq": "langchain.com"}},` 
13.             `{"version": {"$lt": 0.3}}`
14.         `]`
15.     `}`
16. `)`

Copied!Wrap Toggled!

**Output**:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7

8. `{'ids': ['id1'],`
9.  `'embeddings': None,`
10.  `'documents': ['This is a document about LangChain'],`
11.  `'uris': None,`
12.  `'included': ['metadatas', 'documents'],`
13.  `'data': None,`
14.  `'metadatas': [{'source': 'langchain.com', 'version': 0.1}]}`

Copied!Wrap Toggled!

Now, let's make an even more complicated filtering rule, one that combines logical operators with lists in filters. The following retrieves all documents about LangChain and LlamaIndex with a version less than 0.3:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8

9. `collection.get(`
10.     `where={`
11.         `"$and": [`
12.             `{"source": {"$in": ["langchain.com", "llamaindex.ai"]}},` 
13.             `{"version": {"$lt": 0.3}}`
14.         `]`
15.     `}`
16. `)`

Copied!Wrap Toggled!

**Output**:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8
9. 9

10. `{'ids': ['id1', 'id2'],`
11.  `'embeddings': None,`
12.  `'documents': ['This is a document about LangChain',`
13.   `'This is a reading about LlamaIndex'],`
14.  `'uris': None,`
15.  `'included': ['metadatas', 'documents'],`
16.  `'data': None,`
17.  `'metadatas': [{'source': 'langchain.com', 'version': 0.1},`
18.   `{'source': 'llamaindex.ai', 'version': 0.2}]}`

Copied!Wrap Toggled!

### 📝 Filter using Document Content

Suppose we wanted to find documents that include the word "pandas" in the text. The following performs a full text search for such documents:

1. 1
2. 2
3. 3

4. `collection.get(`
5.     `where_document={"$contains":"pandas"}`
6. `)`

Copied!Wrap Toggled!

**Output**:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7

8. `{'ids': ['id4'],`
9.  `'embeddings': None,`
10.  `'documents': ['This is a document about pandas'],`
11.  `'uris': None,`
12.  `'included': ['metadatas', 'documents'],`
13.  `'data': None,`
14.  `'metadatas': [{'source': 'pandas.pydata.org', 'version': 0.4}]}`

Copied!Wrap Toggled!

> 💡 Document filtering is case-sensitive in Chroma DB. Therefore, searching for "Pandas" will not find any documents.

### 🏷️ + 📝 Combine Metadata and Document Content Filters

Of course, we can combine metadata and document filters. The following looks for all documents containing "LangChain" or "Python" with version numbers greater than 0.1:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8
9. 9

10. `collection.get(`
11.     `where={"version": {"$gt": 0.1}},`
12.     `where_document={`
13.         `"$or": [`
14.             `{"$contains": "LangChain"},`
15.             `{"$contains": "Python"}`
16.         `]`
17.     `}`
18. `)`

Copied!Wrap Toggled!

**Output**:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8
9. 9

10. `{'ids': ['id3', 'id5'],`
11.  `'embeddings': None,`
12.  `'documents': ['This is a book about Python',`
13.   `'This is another document about LangChain'],`
14.  `'uris': None,`
15.  `'included': ['metadatas', 'documents'],`
16.  `'data': None,`
17.  `'metadatas': [{'version': 0.3, 'source': 'python.org'},`
18.   `{'source': 'langchain.com', 'version': 0.5}]}`

Copied!Wrap Toggled!

## ✅ Wrap-up