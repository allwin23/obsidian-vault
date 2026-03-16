## Distance and Similarity Metrics

### 1. L2 Distance (Euclidean Distance)

**Definition**: The L2 distance between two vectors aa and bb is the square root of the sum of the squared differences between corresponding elements:

L2(a,b)= ∑i=1n(ai−bi)2L2(a,b)= ∑i=1n​(ai​−bi​)2​

**Properties**:

- The L2 distance measures the straight-line distance between two points in Euclidean space, following the principles of the Pythagorean theorem.
- It is sensitive to both the magnitude and direction of the vectors, meaning that changes in either can significantly affect the calculated distance.
- This distance metric is commonly used in applications involving spatial or geometric data, such as image analysis, computer vision, and geographic mapping.

**Use Case**: A common use case for L2 distance is determining the closest point to a given location in two-dimensional (2D) or three-dimensional (3D) space. This approach is frequently used in computer vision tasks, where spatial proximity between features or objects plays a critical role.

### 2. Dot Product (Inner Product) Similarity and Distance

**Definition**: The dot product of two vectors is:

a⋅b=∑i=1naibia⋅b=∑i=1n​ai​bi​

**Alternative Calculation**: The dot product can also be calculated using magnitudes and angles:

a⋅b=∣∣a∣∣ ∣∣b∣∣cos(α)a⋅b=∣∣a∣∣ ∣∣b∣∣cos(α)

here ∣∣a∣∣=∑k=1nak2∣∣a∣∣=∑k=1n​ak2​​ is the L2 norm of vector aa, and αα is the angle between vectors aa and bb.

**Properties**:

- The dot product of two vectors can be positive, negative, or zero, depending on the angle between them.
- Larger dot product values typically indicate a higher degree of similarity between the vectors, especially when they are pointing in similar directions.
- If a **distance-like metric** is needed, the **negative of the dot product** can be used. In this case, larger (more negative) values correspond to greater dissimilarity or distance.
- The dot product is sensitive to both the magnitude and direction of the vectors, meaning that changes in either will affect the result.
- It is frequently used in machine learning models, such as in neural networks for computing activations or in matrix factorization for recommendation systems.

**Use Case**: When the length of the vector (representing something such as relevance, confidence, or quantity) is meaningful. For instance, in recommendation systems, the direction of vectors typically indicates two products are about the same topic, but larger magnitudes might indicate that a product is more popular. In this case using dot product similarity makes sense, because one would want to recommend the products that are not only about the same topic, but also popular.

### 3. Cosine Similarity and Distance

**Definition**: Cosine similarity measures the cosine of the angle between two vectors:

cosine_similarity(a,b)=a⋅b∣∣a∣∣ ∣∣b∣∣cosine_similarity(a,b)=∣∣a∣∣ ∣∣b∣∣a⋅b​

**Distance Conversion**: To convert cosine similarity to cosine distance:

cosine_distance(a,b)=1−cosine_similarity(a,b)cosine_distance(a,b)=1−cosine_similarity(a,b)

**Alternative Calculation with Normalized Vectors**: Cosine similarity can be calculated more efficiently if the vectors are normalized. To normalize a vector, divide it by its L2 norm:

norm(a)=a∣∣a∣∣norm(a)=∣∣a∣∣a​

A normalized vector has the property that the sum of the squared components sums to one:

∑i=1nnorm(a)i2=1∑i=1n​norm(a)i2​=1

Calculating cosine similarity between two normalized vectors is as easy as calculating the dot product between them:

cosine_similarity(a,b)=a⋅b∣∣a∣∣ ∣∣b∣∣=a∣∣a∣∣⋅b∣∣b∣∣=norm(a)⋅norm(b)cosine_similarity(a,b)=∣∣a∣∣ ∣∣b∣∣a⋅b​=∣∣a∣∣a​⋅∣∣b∣∣b​=norm(a)⋅norm(b)

**Properties**:

- Cosine similarity focuses on the orientation of vectors rather than their magnitude, measuring the cosine of the angle between them.
- It is particularly well-suited for high-dimensional, sparse data, such as text embeddings or term-frequency vectors in natural language processing.
- This metric is invariant to vector length, meaning that scaling a vector up or down does not affect the similarity score.

**Use Case**: A common use case for cosine similarity is measuring document similarity in natural language processing (NLP), where it helps identify texts with similar content regardless of their length.

### Choosing the Right Metric

|Metric|Sensitive to Magnitude|Normalized|Best For|
|---|---|---|---|
|L2 Distance|✅ Yes|❌ No|Spatial data, clustering|
|Cosine Distance|❌ No|✅ Yes|Text, embeddings, NLP|
|Dot Product|✅ Yes|❌ No|Neural networks, recommender systems|

### Practical Considerations

- **Normalization**: Normalize vectors if you expect to only need to calculate cosine similarity. For many natural language processing tasks and text embedding models, this is the default option.
- **High-Dimensional Data**:
    - L2 distance can suffer from the "curse of dimensionality." Consider using a different metric or using a dimensionality reduction technique if the data exhibits high dimensionality.
    - Cosine distance often performs better in high dimensions, and is the default choice in many natural language processing and text-based tasks.
    - Dot product can be computed efficiently using matrix operations, and can be used to calculate cosine similarity if the vectors are normalized.

## Vector Databases versus Traditional Databases

|**Function**|**Traditional Databases**|**Vector Databases**|
|---|---|---|
|**Data Representation**|Structured format using tables, rows, columns|Multi-dimensional vectors encoding complex/unstructured data|
|**Data Search**|SQL queries for structured data|Similarity searches for vectorized data|
|**Indexing**|B-trees for efficient retrieval|Specialized indices such as the graph-based HNSW for approximate nearest neighbor search|
|**Scalability**|Resource augmentation or data sharding|Distributed architectures for horizontal scaling|
|**Applications**|Business applications, transactional systems|Context-aware AI applications, similarity search, NLP, multimedia analysis|

## Vector Database Fundamentals

**Vector Database**: Specialized database designed to store and query vectorized data rapidly. Data is represented as vectors in multi-dimensional space, where each vector dimension corresponds to a specific attribute.

**Vector Libraries vs Vector Databases**:

- **Vector Libraries**: In-memory with similarity capabilities
- **Vector Databases**: Full CRUD operations (create, read, update, delete) + enterprise production deployments

## Chroma DB Key Tips and Best Practices

### Filtering Best Practices

- **Document filtering is case-sensitive** in Chroma DB - searching for "Pandas" will not find "pandas"
- Combine metadata and document filters for precise results using both `where` and `where_document` parameters
- Use `$and` and `$or` operators for complex filtering logic
- Use `$in` and `$nin` for list-based filtering

### Key Chroma DB Features

- **Dual-filtering approach**: Supports both metadata filtering (structured attributes) and document filtering (full text search)
- **Metadata filtering**: Similar to SQL `WHERE` clauses, but more flexible and can be combined with vector search
- **Document filtering**: Comparable to SQL's `CONTAINS` or `LIKE` operators, but more powerful when integrated with vector search
- **Full text search**: Document filtering is also referred to as full text search in Chroma DB

## Chroma DB Setup & Configuration

### Basic Setup

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

11. `import chromadb`
12. `from chromadb.utils import embedding_functions`

13. `# Define embedding function`
14. `ef = embedding_functions.SentenceTransformerEmbeddingFunction(`
15.     `model_name="all-MiniLM-L6-v2"`
16. `)`

17. `# Create client`
18. `client = chromadb.Client()`

Copied!Wrap Toggled!

### Collection Creation with Typical HNSW Configuration

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

11. `collection = client.create_collection(`
12.     `name="my_collection_name",`
13.     `metadata={"topic": "query testing"},`
14.     `configuration={`
15.         `"hnsw": {`
16.             `"space": "cosine",    # Distance metric`
17.         `},`
18.         `"embedding_function": ef`
19.     `}`
20. `)`

Copied!Wrap Toggled!

### What is a Vector Index?

Finding semantically similar vectors using brute-force comparison (checking every vector in the database) becomes inefficient at scale. **Vector indexes** solve this by using specialized data structures that enable algorithms to compute similarity scores with only a small subset of vectors, significantly speeding up search while still returning exact or near-optimal results.

A **vector index** organizes high-dimensional embeddings to reflect the geometry of the vector space, clustering similar vectors together or linking them through proximity-based graphs. This allows the search algorithm to **prune large portions of the dataset** early in the search process, enabling scaling to millions or billions of vectors while maintaining low-latency performance.

### What is HNSW?

**HNSW** (Hierarchical Navigable Small World) is a fast, scalable graph-based vector index designed for **approximate nearest neighbor (ANN)** search in high-dimensional spaces. It is the sole indexing method supported by Chroma DB and is widely adopted in other vector databases due to its performance and reliability.

**How It Works**: HNSW builds a **multi-layered graph** where:

- The **upper layers** contain a sparse overview of the data for fast navigation.
- The **bottom layer** holds all vectors for detailed search.
- Each vector connects to a few nearby neighbors, forming a **"small world" network**—meaning most vectors can be reached in just a few steps.

**Search Process**: The algorithm starts at the top layer and moves closer to the query vector as it descends, refining the search at each level. This structure allows it to skip most of the dataset and still find highly similar vectors quickly.

**Why Use HNSW?**:

- **Fast**: Avoids scanning the entire dataset
- **Accurate**: Delivers near-exact results
- **Scalable**: Handles millions to billions of vectors
- **Versatile**: Works with various similarity metrics

### HNSW Distance Metric Parameters

- **`space`**: Distance metric options
    - `l2`: Squared L2 (Euclidean) distance (default)
    - `ip`: Inner (dot) product distance
    - `cosine`: Cosine distance

### HNSW Performance Parameters: Key Trade-offs

- **Higher `ef_search`**: Better accuracy, slower performance
- **Higher `ef_construction`**: Better index quality, longer build time
- **Higher `max_neighbors`**: Better search performance, more memory usage

## Data Operations

### Adding Documents

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

12. `collection.add(`
13.     `documents=[`
14.         `"Document text 1",`
15.         `"Document text 2"`
16.     `],`
17.     `metadatas=[`
18.         `{"source": "source1", "category": "type1"},`
19.         `{"source": "source2", "category": "type2"}`
20.     `],`
21.     `ids=["id1", "id2"]`
22. `)`

Copied!Wrap Toggled!

### Retrieving Documents

1. 1
2. 2
3. 3
4. 4
5. 5
6. 6
7. 7

8. `# Get all documents`
9. `all_items = collection.get()`

10. `# Get with metadata filter`
11. `filtered_items = collection.get(`
12.     `where={"source": "source1"}`
13. `)`

Copied!Wrap Toggled!

## Filtering in Chroma DB

### Metadata Filtering Operators

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

15. `# Basic equality`
16. `where={"key": "value"}`
17. `# Equivalent to`
18. `where={"key": {"$eq": "value"}}`

19. `# Comparison operators`
20. `"$eq"   # equal to (string, int, float)`
21. `"$ne"   # not equal to`
22. `"$gt"   # greater than (int, float)`
23. `"$gte"  # greater than or equal to`
24. `"$lt"   # less than (int, float)`
25. `"$lte"  # less than or equal to`
26. `"$in"   # in list`
27. `"$nin"  # not in list`

Copied!Wrap Toggled!

### Complex Filters with Logical Operators

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

20. ``# AND operation; you can replace `$and` with `$or` to make this an OR operation``
21. `collection.get(`
22.     `where={`
23.         `"$and": [`
24.             `{"source": {"$eq": "langchain.com"}},` 
25.             `{"version": {"$lt": 0.3}}`
26.         `]`
27.     `}`
28. `)`

29. `# Using a list to perform an OR operation on the values of a metadata key`
30. `collection.get(`
31.     `where={`
32.         `"$and": [`
33.             `{"source": {"$in": ["langchain.com", "llamaindex.ai"]}},` 
34.             `{"version": {"$lt": 0.3}}`
35.         `]`
36.     `}`
37. `)`

Copied!Wrap Toggled!

### Document Content Filtering

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

14. `# Contains text`
15. `where_document={"$contains": "pandas"}`

16. `# Does not contain text`
17. `where_document={"$not_contains": "library"}`

18. `# Combined with logical operators`
19. `where_document={`
20.     `"$or": [`
21.         `{"$contains": "LangChain"},`
22.         `{"$contains": "Python"}`
23.     `]`
24. `}`

Copied!Wrap Toggled!

## Similarity Search

### Basic Query

1. 1
2. 2
3. 3
4. 4

5. `results = collection.query(`
6.     `query_texts=["search term"],`
7.     `n_results=3  # Number of results to return`
8. `)`

Copied!Wrap Toggled!

### Query with Filters

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

22. `# With metadata filter`
23. `results = collection.query(`
24.     `query_texts=["polar bear"],`
25.     `n_results=1,`
26.     `where={'topic': 'animals'}`
27. `)`

28. `# With document filter`
29. `results = collection.query(`
30.     `query_texts=["polar bear"],`
31.     `n_results=1,`
32.     `where_document={'$not_contains': 'library'}`
33. `)`

34. `# Combined filters`
35. `results = collection.query(`
36.     `query_texts=["polar bear"],`
37.     `n_results=1,`
38.     `where={'topic': 'animals'},`
39.     `where_document={'$not_contains': 'library'}`
40. `)`

Copied!Wrap Toggled!

## Common Workflow Pattern

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
23. 23

24. `# 1. Setup`
25. `import chromadb`
26. `from chromadb.utils import embedding_functions`

27. `# 2. Create embedding function and client`
28. `ef = embedding_functions.SentenceTransformerEmbeddingFunction(model_name="all-MiniLM-L6-v2")`
29. `client = chromadb.Client()`

30. `# 3. Create collection with configuration`
31. `collection = client.create_collection(`
32.     `name="collection_name",`
33.     `configuration={"hnsw": {"space": "cosine"}, "embedding_function": ef}`
34. `)`

35. `# 4. Add documents`
36. `collection.add(documents=texts, metadatas=metadata, ids=ids)`

37. `# 5. Perform similarity search`
38. `results = collection.query(query_texts=["query"], n_results=5)`

39. `# 6. Process results`
40. `for i, (doc_id, score, text) in enumerate(zip(results['ids'][0], results['distances'][0], results['documents'][0])):`
41.     `print(f"Rank {i+1}: {doc_id}, Score: {score:.4f}, Text: {text}")`

Copied!Wrap Toggled!

## Author(s)