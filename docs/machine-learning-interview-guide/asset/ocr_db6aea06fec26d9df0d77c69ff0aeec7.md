+   - **Significance**: Focuses on the overlap relative to the size of the smaller set.
+   - **BM25 (Best Matching 25) similarity:** A modified version of TF-IDF that accounts for document length and term frequency.
+     - **Formula:** Combines term frequency, inverse document frequency, and document length normalization.
+     - **Significance:** Effective for measuring similarity in information retrieval tasks.
+   - **Word Mover's Distance (WMD):** Measures the dissimilarity between two text documents based on the minimum cumulative *distance* needed to transport words from one document to another.
+     - **Significance:** Incorporates word semantics and can be useful when documents have different lengths.
+   - **Bhattacharyya Distance:** Measures the similarity between two probability distributions.
+     - **Formula:**
+       $$Bhattacharyya\ Distance(A,B) = -ln\left(\sum_{i=1}^{n} \sqrt{A_i \cdot B_i}\right)$$
+     - **Significance:** Commonly used when representing documents as probability distributions over terms.

The significance of document similarity in NLP is described as follows:

+   - **Information retrieval:** Finding documents similar to a given query.
+   - **Clustering:** Grouping similar documents.