![](bbox=[0.11, 0.11, 0.94, 0.26])

Figure 23.4: An overview of the pipeline for random-walk graph embedding methods. Reprinted with permission from [God18].

where ⊙ is the element-wise matrix multiplication operator. Therefore, GF also learns a low-rank factorization of the adjacency matrix W measured in Frobenius norm. We note that this is a sparse operation (summing only over edges which exist in the graph), and so the method has computational complexity O(M).

The methods described so far are all symmetric, that is, they assume that W_ij = W_ji. This is a limiting assumption when working with directed graphs as some relationships are not reciprocal. The GraRep method of [CLX15] overcomes this limitation by learning two embeddings per node, a source embedding Z^s and a target embedding Z^t, which capture asymmetric proximity in directed networks. In addition to asymmetry, GraRep learns embeddings that preserve k-hop neighborhoods via powers of the adjacency matrix and minimizes a graph reconstruction loss with:

\widehat{W}^{(k)} = Z^{(k),s} Z^{(k),t}^\top \tag{23.15}
\mathcal{L}_{G,RECON}(W, \widehat{W}^{(k)}; \Theta) = ||D^{-k} W^k - \widehat{W}^{(k)}||_F^2, \tag{23.16}

for each 1 ≤ k ≤ K. GraRep concatenates all representations to get source embeddings Z^s = [Z^{(1),s} ... Z^{(K),s}] and target embeddings Z^t = [Z^{(1),t} ... Z^{(K),t}]. Unfortunately, GraRep is not very scalable, since it uses a matrix power, power, D^{-1}W, making it increasingly more dense. This limitation can be circumvented by using implicit matrix factorization [Per+17] as discussed below.

# 23.3.5 Outer product-based: Skip-gram methods

Skip-gram graph embedding models were inspired by research in natural language processing to model the distributional behavior of words [Mik+13c; PSM14b]. Skip-gram word embeddings are optimized to predict words in their context (the surrounding words) for each target word in a sentence. Given a sequence of words (w1, ..., wT), skip-gram will minimize the objective:

\mathcal{L} = - \sum_{-K \le i \le K, i \ne 0} \log \mathbb{P}(w_{k-i} | w_k),