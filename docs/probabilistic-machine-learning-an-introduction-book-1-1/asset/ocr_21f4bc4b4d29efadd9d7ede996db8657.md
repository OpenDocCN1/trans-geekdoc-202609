# 19.5 Word embeddings

![](bbox=[0.12, 0.1, 0.88, 0.48])

We define u_i to be the embedding for word i, and s ⊙ v_j to be the embedding for context j.

We can use these embeddings for document retrieval. The idea is to compute an embedding for the query words using u_i, and to compare this to the embedding of all the documents or contexts v_j. This is known as latent semantic indexing or LSI [Dee+90].

In more detail, suppose the query is a bag of words w₁,…,w_B; we represent this by the vector q = 1/B ∑_{b=1}^B u_{w_b}, where u_{w_b} is the embedding for word w_b. Let document j be represented by v_j. We then rank documents by the cosine similarity between the query vector and document, defined by

sim(q, d) = q^T d / (||q|| ||d||)

(19.14)

where ||q|| = √∑_i q_i² is the ℓ₂-norm of q. This measures the angles between the two vectors, as shown in Fig. 19.9. Note that if the vectors are unit norm, cosine similarity is the same as inner product; it is also equal to the squared Euclidean distance, up to a change of sign and an irrelevant additive constant:

||q - d||² = (q - d)^T (q - d) = q^T q + d^T d - 2 q^T d = 2(1 - sim(q,d))

(19.15)



Now suppose we define context more generally to be some local neighborhood of words j ∈ {1, …, M^h}, where h is the window size. Thus C_{ij} is how many times word i occurs in a neighborhood of type j. We can compute the SVD of this matrix as before, to get C ≈ ∑_{k=1}^K u_{ik} s_k v_k. We define u_i to be the embedding for word i, and s ⊙ v_j to be the embedding for context j. This is known as latent semantic analysis or LSA [Dee+90].

For example, suppose we compute C on the British National Corpus.³ For each word, let us retrieve the K nearest neighbors in embedding space ranked by cosine similarity (i.e., normalized