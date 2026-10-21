# TABLE 11.1

# Adopted Similarity and Dissimilarity Measures

| Dissimilarity/Similarity Measure | Equation |
|---|---|
| Euclidean distance | $D_{Euclidean}(a,b)=\left(\sum_{i=1}^{n}|a_i-b_i|^2\right)^{1/2}$ |
| Manhattan distance | $D_{Manhattan}(a,b)=\sum_{i=1}^{n}|a_i-b_i|$ |
| Canberra distance | $D_{Canberra}(a,b)=\sum_{i=1}^{n}\frac{|a_i-b_i|}{|a_i+b_i|}$ |
| Chi-square distance | $D_{\chi^2}(a,b)=\sum_{i=1}^{n}\frac{(a_i-b_i)^2}{b_i}$ |
| Cosine similarity | $D_{Cosine}(a,b)=\frac{a\cdot b}{||a||\,||b||}$ |
| Jaccard distance | $D_{Jaccard}(a,b)=\frac{\sum_{i=1}^{n}(a_i*b_i)}{\sum_{i=1}^{n}a_i+\sum_{i=1}^{n}b_i-\sum_{i=1}^{n}(a_i*b_i)}$ |

a and b are two feature vectors, and n is the size of these vectors.

of each document [23]. Figure 11.7 shows the samples from the original and cropped corpuses.

# 11.5.1 EVALUATION CRITERIA

Two typical performance measures for information retrieval systems are used. The first is the TOP-N precision, which is the most commonly used criterion [3,5,6]. It corresponds to the percentage of correct documents among the N most similar documents to the query. Since each writer is represented by eight documents, we consider the retrieval from TOP-2 to TOP-7.

The second criterion is the mean average precision (MAP). It allows a global evaluation of the Writer Retrieval system, since it considers the mean of the average precision (AP), which is calculated for all query documents. Considering only the ranks where documents are relevant, the AP is calculated as follows:

AP = $\frac{\sum_{k=1}^{M}[P@k]\times rel(k)}{M}$ (11.10)