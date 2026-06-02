# FAISS Theory Questions

## Q1: What is the difference between IndexFlatL2 and IndexFlatIP in FAISS? When would you use each?

### IndexFlatL2

IndexFlatL2 uses Euclidean (L2) distance to measure similarity between vectors.

Formula:

L2 Distance = √Σ(xᵢ - yᵢ)²

Smaller distance indicates greater similarity.

Use Cases:
- When Euclidean distance is the desired similarity metric.
- Useful when vector magnitude is important.

---

### IndexFlatIP

IndexFlatIP uses Inner Product.

Formula:

x · y

Higher values indicate greater similarity.

Use Cases:
- Semantic search
- Retrieval-Augmented Generation (RAG)
- Recommendation systems

When embeddings are normalized, Inner Product behaves like Cosine Similarity.

---

## Q2: Why do we normalize embeddings before adding them to FAISS when we want cosine similarity?

Cosine similarity measures the angle between vectors rather than their magnitude.

Formula:

Cosine Similarity = (A · B) / (||A|| ||B||)

Normalization converts every vector to unit length.

After normalization:

||A|| = ||B|| = 1

Therefore:

Cosine Similarity = A · B

This allows FAISS to perform cosine-style searches efficiently.

---

## Q3: FAISS uses ANN (Approximate Nearest Neighbour) search. What does "approximate" mean here and why is it acceptable?

Approximate Nearest Neighbour (ANN) search tries to find vectors that are very close to the true nearest neighbours without checking every vector.

Advantages:

- Much faster search
- Lower memory usage
- Scales to millions or billions of vectors

Trade-Off:

- Results may not always be the exact nearest neighbour.
- Results are usually extremely close to the exact answer.

This trade-off is acceptable because retrieval systems prioritize speed while maintaining high accuracy.