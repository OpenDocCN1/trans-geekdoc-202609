![](bbox=[0.35, 0.13, 0.6, 0.33])

Figure 10.10: Example of a term-document matrix, where raw counts have been replaced by their TF-IDF values (see Sec. 10.4.3.2). Darker cells are larger values. From https://bit.ly/2kByLQl. Used with kind permission of Christoph Carl Kling.

(We often normalize each row as well.) This provides a more meaningful representation of documents, and can be used as input to many ML algorithms. See tfidf_demo.py for an example.

# 10.4.3.3 Word embeddings

Although the TF-IDF transformation improves the vector representation of words by placing more weight on “informative” words and less on “uninformative” words, it does not overcome the fundamental issue that semantically similar words, such as “man” and “woman”, may be further apart (in vector space) than semantically dissimilar words, such as “man” and “banana”. Thus the assumption that points that are close in input space should have similar outputs, which is implicitly made by logistic regression models, is invalid.

The standard way to solve this problem is to use **word embeddings**, in which we map each sparse one-hot vector, $\mathbf{x}_{n,t} \in \{0,1\}^V$, to a lower-dimensional dense vector, $\mathbf{e}_{n,t} \in \mathbb{R}^K$ using $\mathbf{e}_{nt} = \mathbf{E}\mathbf{x}_{nt}$, where $\mathbf{E}$ is learned such that semantically similar words are placed close by. There are many ways to learn such embeddings, as we discuss in Sec. 19.5.

Once we have an embedding matrix, we can represent a variable-length text document as a bag **bag of word embeddings**. We can then convert this to a fixed length vector by summing (or averaging) the embeddings:

$\bar{\mathbf{e}}_n = \sum_{t=1}^{T} \mathbf{e}_{nt} = \mathbf{E}\tilde{\mathbf{x}}_n$ (10.101)

where $\tilde{\mathbf{x}}_n$ is the bag of words representation from Eq. (10.99). Thus the overal model has the form $p(y|\mathbf{x}_n, \theta) = \mathrm{Cat}(y|\mathcal{S}(\mathbf{W}\mathbf{E}\tilde{\mathbf{x}}_n))$ (10.102)

We often use a **pre-trained word embedding** matrix $\mathbf{E}$, in which case the overall model is linear in $\mathbf{W}$. See Sec. 13.2.4.3 for a nonlinear extension of this model.