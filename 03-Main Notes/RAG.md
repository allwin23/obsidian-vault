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
rch in Chroma DB is generally straightforward, but there are a few important nuances to understand in order to use it effectively for information retrieval. Before exploring those details, it's helpful to first understand what a vector index is.

## What is a Vector Index?

Finding the most semantically similar vectors to a query is mathematically straightforward. For example, to compute cosine similarity, you normalize the embeddings of all documents and the query, then calculate the dot product between the query embedding and each document embedding. This yields the cosine similarity scores. Identifying the most similar document is simply a matter of finding the one with the highest score.

However, this brute-force approach is inefficient—it requires comparing the query against every vector in the database, which becomes slow at scale. To address this, **vector indexes** are used. These are specialized data structures that enable algorithms to compute similarity scores with only a small subset of vectors, significantly speeding up the search while still returning exact or near-optimal results.

A **vector index** is specifically designed to store and organize high-dimensional embeddings for fast similarity and nearest neighbor searches. This organization is what enables vector indexes to scale to millions or even billions of vectors while maintaining low-latency performance. Instead of treating the dataset as a flat list, the index structures the data in a way that reflects the geometry of the vector space—clustering similar vectors together or linking them through proximity-based graphs. This allows the search algorithm to **prune large portions of the dataset** early in the search process, focusing only on the most promising regions.

### What is a Hierarchical Navigable Small World (HNSW)?

**HNSW** is a fast, scalable graph-based vector index designed for **approximate nearest neighbor (ANN)** search in high-dimensional spaces. It is the sole indexing method supported by Chroma DB and is widely adopted in other vector databases due to its performance and reliability.

#### How It Works

HNSW builds a **multi-layered graph** where:

- The **upper layers** contain a sparse overview of the data for fast navigation.
- The **bottom layer** holds all vectors for detailed search.

Each vector connects to a few nearby neighbors, forming a **"small world" network**—meaning most vectors can be reached in just a few steps.

#### Search Process

The algorithm starts at the top layer and moves closer to the query vector as it descends, refining the search at each level. This structure allows it to skip most of the dataset and still find highly similar vectors quickly.

#### Why Use HNSW?

- **Fast**: Avoids scanning the entire dataset.
- **Accurate**: Delivers near-exact results.
- **Scalable**: Handles millions to billions of vectors.
- **Versatile**: Works with various similarity metrics.

## Setting Up HNSW in Chroma DB

In Chroma DB, the HNSW vector index is configured during collection creation. Since HNSW is an _approximate_ nearest neighbor algorithm, it's important to understand how its configuration affects both accuracy and performance. Parameters such as search speed, memory usage, and recall can all be tuned through the index settings. The example below demonstrates how to configure HNSW using the `hnsw` key:

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
18. 18
19. 19
20. 20
21. 21
22. 22

23. `# Setup`
24. `import chromadb`
25. `from chromadb.utils import embedding_functions`
26. `ef = embedding_functions.SentenceTransformerEmbeddingFunction(`
27.     `model_name="all-MiniLM-L6-v2"`
28. `)`

29. `# Collection creation`
30. `client = chromadb.Client()`
31. `collection = client.create_collection(`
32.     `name="my_collection_name",`
33.     `metadata={"topic": "query testing"},`
34.     `configuration={`
35.         `"hnsw": {`
36.             `"space": "cosine",`
37.             `"ef_search": 100,`
38.             `"ef_construction": 100,`
39.             `"max_neighbors": 16`
40.         `},`
41.         `"embedding_function": ef`
42.     `}`
43. `)`

Copied!Wrap Toggled!

The key configuration parameters are:

- `space`: selects the distance metric. Possible options include:
    - `l2`: squared L2 (Euclidean) distance (default)
    - `ip`: inner (dot) product distance
    - `cosine`: cosine distance
- `ef_search`: the size of the candidate list used to search for nearest neighbors when a nearest neighbor search is performed. The default value is 100. Higher values improve both accuracy and recall, but at the cost of slower performance and increased computatuonal cost.
- `ef_construction`: the size of the candidate list used to select neighbors when a node is inserted during index construction. The default value is 100. Higher values improve the quality of the index and accuracy, but at the cost of slower performance and increased memory usage.
- `max_neighbors`: the maximum number of connections each node can have during construction. The defualt value is 16. Higher values lead to denser graphs that perform better during searches at the cost of higher memory usage and construction time.

We can categorize the performance-based parameters into two types:

- `ef_search` directly controls the breadth of the search at query time, making it the most direct lever for search quality (recall) vs. query speed.
- `ef_construction` and `max_neighbors` affect the quality of the built index. A higher-quality, denser index (achieved with higher `ef_construction` and `max_neighbors`) provides a better foundation for searches, potentially leading to better accuracy. However, this quality comes at the cost of significantly longer index build times and higher memory consumption during construction and for storing the index.

## Performing Similarity Searches in Chroma DB

### Add data

Before performing a similarity search, we must add data to our collection:

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

16. `collection.add(`
17.     `documents=[`
18.         `"Giant pandas are a bear species that lives in mountainous areas.",`
19.         `"A pandas DataFrame stores two-dimensional, tabular data",`
20.         `"I think everyone agrees that pandas are some of the cutest animals on the planet",`
21.         `"A direct comparison between pandas and polars indicates that polars is a more efficient library than pandas.",`
22.     `],`
23.     `metadatas=[`
24.         `{"topic": "animals"},`
25.         `{"topic": "data analysis"},`
26.         `{"topic": "animals"},`
27.         `{"topic": "data analysis"},`
28.     `],`
29.     `ids=["id1", "id2", "id3", "id4"]`
30. `)`

Copied!Wrap Toggled!

As shown in the code above, all four documents mention "pandas." However, documents `id1` and `id3` refer to pandas as animals, while `id2` and `id4` refer to the Python library. Although the word "pandas" appears in every document, its meaning differs. This dataset is useful for evaluating whether a semantic search system can distinguish between these different meanings based on context.

### Querying in Chroma DB

Once a collection is created and populated, performing a similarity search is as simple as querying the database. In Chroma DB, the results are returned using an approximate nearest neighbor search powered by the HNSW algorithm, based on the distance metric specified during collection creation.

Let's query our collection using the query `cats`:

1. 1
2. 2
3. 3
4. 4

5. `collection.query(`
6.     `query_texts=["cats"],`
7.     `n_results=10,`
8. `)`

Copied!Wrap Toggled!

Note that querying the database involves passing the query, in a list, to the `query_texts` parameter in the `.query()` method. The optional parameter `n_results` controls the number of results to retrieve. In this case, `n_results` was set to 10, which exceeds the number of documents in the collection. Consequently, in this case, all results will be retrieved, ranked from most similar to the query to the least similar. The following presents the output of the above query:

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

18. `{'ids': [['id3', 'id1', 'id2', 'id4']],`
19.  `'embeddings': None,`
20.  `'documents': [['I think everyone agrees that pandas are some of the cutest animals on the planet',`
21.    `'Giant pandas are a bear species that lives in mountainous areas.',`
22.    `'A pandas DataFrame stores two-dimensional, tabular data',`
23.    `'A direct comparison between pandas and polars indicates that polars is a more efficient library than pandas.']],`
24.  `'uris': None,`
25.  `'included': ['metadatas', 'documents', 'distances'],`
26.  `'data': None,`
27.  `'metadatas': [[{'topic': 'animals'},`
28.    `{'topic': 'animals'},`
29.    `{'topic': 'data analysis'},`
30.    `{'topic': 'data analysis'}]],`
31.  `'distances': [[0.7380143404006958,`
32.    `0.8351750373840332,`
33.    `0.8634340167045593,`
34.    `0.9299634695053101]]}`

Copied!Wrap Toggled!

Note that, as expected, all four results got retrieved. However, the top two retrieved texts, those that resulted in the lowest cosine distance to the search query, were:

1. "I think everyone agrees that pandas are some of the cutest animals on the planet" and
2. "Giant pandas are a bear species that lives in mountainous areas."

Obviously, these two documents were retrieved because they relate to an animal as opposed to a programming library, and the query (cats) absent any other context likely refers to cats as animals as well. Moreover, the top search result was a document that discussed the cuteness of pandas, and, since cats are generally considered to be cute, likely resulted in that document being chosen over the more general one about pandas that referred to them living in mountainous areas.

These two documents were likely retrieved because they relate to animals rather than the Python programming library. Given that the query was simply "cats", with no additional context, it's reasonable to assume it refers to cats as animals. Moreover, the top retrieved document focused on the cuteness of pandas, which likely aligned more closely with the query "cats", a word also associated with cuteness, than a more general document about pandas' natural habitat.

### Querying with filters

Suppose we wanted to find the document that aligns most closely with the query `polar bear` using the following code:

1. 1
2. 2
3. 3
4. 4

5. `collection.query(`
6.     `query_texts=["polar bear"],`
7.     `n_results=1,`
8. `)`

Copied!Wrap Toggled!

The above code produces the following output:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8

9. `{'ids': [['id4']],`
10.  `'embeddings': None,`
11.  `'documents': [['A direct comparison between pandas and polars indicates that polars is a more efficient library than pandas.']],`
12.  `'uris': None,`
13.  `'included': ['metadatas', 'documents', 'distances'],`
14.  `'data': None,`
15.  `'metadatas': [[{'topic': 'data analysis'}]],`
16.  `'distances': [[0.6243703365325928]]}`

Copied!Wrap Toggled!

**What went wrong?**  
In this case, the word **`polar`** in the query was mistakenly matched with the term **`polars`**, referring to the Python data processing library mentioned in the document. As a result, the semantic search failed to retrieve documents about polar bears.

There are several ways to address this issue. One option is to refine the query by adding more context. Another is to try a different embedding model that may better capture the intended meaning. However, a simpler and more effective solution might be to apply **filters** to narrow the search results to a subset of the documents.

Consider the following code that enhances our original query by adding a metadata filter that narrows the search to documents about a specific topic:

1. 1
2. 2
3. 3
4. 4
5. 5

6. `collection.query(`
7.     `query_texts=["polar bear"],`
8.     `n_results=1,`
9.     `where={'topic': 'animals'}`
10. `)`

Copied!Wrap Toggled!

The updated query now returns the correct result—a document about bears, rather than one related to Python libraries:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7
8. 8

9. `'ids': [['id1']],`
10.  `'embeddings': None,`
11.  `'documents': [['Giant pandas are a bear species that lives in mountainous areas.']],`
12.  `'uris': None,`
13.  `'included': ['metadatas', 'documents', 'distances'],`
14.  `'data': None,`
15.  `'metadatas': [[{'topic': 'animals'}]],`
16.  `'distances': [[0.7096824645996094]]}`

Copied!Wrap Toggled!

Alternatively, instead of using a metadata filter, we could perform a full-text search to include or exclude documents based on specific words or phrases. For example, the following query excludes all documents that contain the word "library":

1. 1
2. 2
3. 3
4. 4
5. 5

6. `collection.query(`
7.     `query_texts=["polar bear"],`
8.     `n_results=1,`
9.     `where_document={'$not_contains': 'library'}`
10. `)`

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

9. `'ids': [['id1']],`
10.  `'embeddings': None,`
11.  `'documents': [['Giant pandas are a bear species that lives in mountainous areas.']],`
12.  `'uris': None,`
13.  `'included': ['metadatas', 'documents', 'distances'],`
14.  `'data': None,`
15.  `'metadatas': [[{'topic': 'animals'}]],`
16.  `'distances': [[0.7096824645996094]]}`

Copied!Wrap Toggled!

Finally, it should be noted that there is nothing wrong with combining metadata filtering and full text search in Chroma DB:

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6

7. `collection.query(`
8.     `query_texts=["polar bear"],`
9.     `n_results=1,`
10.     `where={'topic': 'animals'},`
11.     `where_document={'$not_contains': 'library'}`
12. `)`

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

9. `'ids': [['id1']],`
10.  `'embeddings': None,`
11.  `'documents': [['Giant pandas are a bear species that lives in mountainous areas.']],`
12.  `'uris': None,`
13.  `'included': ['metadatas', 'documents', 'distances'],`
14.  `'data': None,`
15.  `'metadatas': [[{'topic': 'animals'}]],`
16.  `'distances': [[0.7096824645996094]]}`

Copied!Wrap Toggled!

## Conclusion

In this reading, you gained a foundational understanding of how similarity search works in Chroma DB, with a focus on vector indexes and the Hierarchical Navigable Small World (HNSW) algorithm. Key topics covered include:

- **Vector indexes fundamentals** – how they structure high-dimensional data to enable efficient similarity searches.
- **The HNSW algorithm** – its use of a multi-layered graph to perform fast, scalable approximate nearest neighbor (ANN) searches.
- **Configuring HNSW in Chroma DB** – including key parameters like `ef_search`, `ef_construction`, and `max_neighbors`, and how they affect performance and accuracy.
- **Executing similarity searches** – from adding documents and querying semantically to interpreting results in context.
- **Refining search results** – using metadata filters and full-text constraints to enhance relevance and reduce