# Sentence Embeddings and Vector Search with FAISS

This project explores sentence embeddings and similarity search using the `sentence-transformers` library and Facebook's FAISS (Facebook AI Similarity Search). It includes:

- Encoding sentences into dense vector representations
- Comparing them using cosine similarity
- Visualizing them with PCA/t-SNE
- Performing semantic search using FAISS

---

## 🔍 How Vector Search Works

Vector search, also known as similarity search or nearest neighbor search, is a technique used to find semantically similar items (like texts or images) in a large dataset.

### Steps Involved:
1. **Embedding Texts**: Sentences or documents are converted into fixed-size numerical vectors using pre-trained models like `all-MiniLM-L6-v2`.
2. **Indexing with FAISS**: These vectors are stored in a FAISS index, optimized for fast retrieval.
3. **Querying**: A new query is also embedded into a vector and compared to the indexed vectors using cosine similarity or dot product.
4. **Retrieving Results**: The top-k most similar vectors (and their associated text) are returned as search results.

This method captures semantic similarity, meaning it can retrieve relevant results even if the exact words don’t match.

---

## 🔬 Performance Comparison: FAISS Querying

We tested the FAISS index with different formulations of the same question (e.g., reworded or paraphrased queries). Here are some observations:

- **Consistent Retrieval**: FAISS was able to retrieve semantically similar chunks even when questions were phrased differently.
- **Subtle Variations in Ranking**: Slight changes in query phrasing (e.g., more specific vs. general wording) affected the top-k results' order.
- **Explanation**:
  - Embedding models encode meaning, but subtle semantic shifts can influence vector distances.
  - FAISS is sensitive to these changes because it ranks based on exact vector distances—even minor embedding differences matter.

In short, while vector search is robust to rewording, it’s not perfect and can rank results differently depending on how a query is framed.

---

