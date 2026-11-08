
To motivate the introduction of these techniques let us examine the relationship between the original LSA method and singular value decomposition. Imagine a term by document matrix `X`, with `t` rows and `d` columns, each element of which contains the number of times the word associated with its row occurs in the document associated with its column. LSA decomposes `X` into a product `X = U S V^T`, where `U` and `V` have orthogonal columns and `S` is a diagonal matrix containing the singular values, which are conventionally sorted in decreasing order. This factorization is known as the singular value decomposition, and it has the property that for every value `k` if all but the `k` largest singular values are discarded the data matrix can be reconstructed in a way that is optimal in a least squares sense. For any given approximation level `k` we can write `X ≈ X~ = U_k S_k V_k^T`.

[Fig. 14.3](#Ch015_516-570_B9780443158889000157.xhtml#f0020) illustrates how this works. The `U[k]` matrix can be thought of as `k` orthogonal “topics” that are combined according to the appropriate proportions for each document, encoded in the `k × d` matrix `V[k]^T`. The matrix `A = S[k] V[k]^T` represents the activity level of the topics associated with each document. Thus the learning phase of LSA simply performs singular value decomposition on the data matrix.

![Fig. 14.3 The singular value decomposition of a `t` by `d` matrix.](images/F000157f14-03-9780443158889.jpg)

[Fig. 14.3](#Ch015_516-570_B9780443158889000157.xhtml#Bf0020) The singular value decomposition of a `t` by `d` matrix.

The dot (or scalar) product of any two columns of the approximated data matrix `X~` provides a measure of the similarity of term usage in the two documents. The dot products between all pairs of documents used to compute the singular value decomposition are

`X~^T X~ = V_k S_k^2 V_k^T`.

To analyze a new document (or query) `x[q]` that is not in the original collection used for the decomposition, it can be projected into the semantic space of topic activity defined by the model using

`a[q] = S[k]^(-1) U[k]^T x[q]`. (14.3)

### Using Principal Component Analysis for Dimensionality Reduction

The singular value decomposition is widely used to project data into a space of reduced dimensions, often before applying other analysis techniques. For instance, data can be projected into a lower dimensional space to effectively apply nearest neighbor techniques, which tend to break down in high dimensional spaces.

LSA is in fact a form of principal component analysis. When viewed as a probability model the projection of a document into a lower dimensional semantic space is, in effect, a latent variable representation for the document. The equivalent quantity in PPCA is given by the expected value of the posterior distribution over the hidden variables. This gives an intuitive view of what it means to project a document or query vector into a lower dimensional space.
