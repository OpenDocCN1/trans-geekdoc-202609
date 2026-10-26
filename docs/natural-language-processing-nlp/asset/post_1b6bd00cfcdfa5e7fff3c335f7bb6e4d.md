

![](img/ba66a8f6f22adeb28512d560b999a231_351_0.png)

(a) Continuous bag-of-words (CBOW)

![](img/ba66a8f6f22adeb28512d560b999a231_351_1.png)

(b) Skipgram

Figure 14.3: The CBOW and skipgram variants of WORD2VEC. The parameter U is the matrix of word embeddings, and each v_m is the context embedding for word w_m.

the words at the beginning of the algorithm. For more details on the algorithm, see Liang (2005).

## 14.5 Neural word embeddings

Neural word embeddings combine aspects of the previous two methods: like latent semantic analysis, they are a continuous vector representation; like Brown clusters, they are trained from a likelihood-based objective. Let the vector u_i represent the K-dimensional embedding for word i, and let v_j represent the K-dimensional embedding for context j. The inner product u_i · v_j represents the compatibility between word i and context j. By incorporating this inner product into an approximation to the log-likelihood of a corpus, it is possible to estimate both parameters by backpropagation. WORD2VEC (Mikolov et al., 2013) includes two such approximations: continuous bag-of-words (CBOW) and skipgrams.

### 14.5.1 Continuous bag-of-words (CBOW)

In recurrent neural network language models, each word w_m is conditioned on a recurrently-updated state vector, which is based on word representations going all the way back to the beginning of the text. The continuous bag-of-words (CBOW) model is a simplification: the local context is computed as an average of embeddings for words in the immediate neighborhood m − h, m − h + 1, …, m + h − 1, m + h,

\[
\overline{v}_m = \frac{1}{2h} \sum_{n=1}^{h} \left( v_{w_{m+n}} + v_{w_{m-n}} \right). \tag{14.14}
\]

Thus, CBOW is a bag-of-words model, because the order of the context words does not matter; it is continuous, because rather than conditioning on the words themselves, we condition on a continuous vector constructed from the word embeddings. The parameter h determines the neighborhood size, which Mikolov et al. (2013) set to h = 4.

| word 1 | word 2 | similarity |
|---|---|---|
| love | sex | 6.77 |
| stock | jaguar | 0.92 |
| money | cash | 9.15 |
| development | issue | 3.97 |
| lad | brother | 4.46 |

Table 14.4: Subset of the WS-353 (Finkelstein et al., 2002) dataset of word similarity ratings (examples from Faruqui et al. (2016)).

GloVe ("global vectors") are a closely related approach (Pennington et al., 2014), in which the matrix to be factored is constructed from log co-occurrence counts, $M_{ij} = \log \text{count}(i,j)$. The word embeddings are estimated by minimizing the sum of squares,

$\min_{\boldsymbol{u},\boldsymbol{v},b,\tilde{b}} \sum_{i=1}^{V} \sum_{j \in C} f(M_{ij}) \left( \widehat{\log M_{ij}} - \log M_{ij} \right)^2$

s.t. $\widehat{\log M_{ij}} = \boldsymbol{u}_i \cdot \boldsymbol{v}_j + b_i + \tilde{b}_j$, \quad [14.25]

where $b_i$ and $\tilde{b}_j$ are offsets for word $i$ and context $j$, which are estimated jointly with the embeddings $\boldsymbol{u}$ and $\boldsymbol{v}$. The weighting function $f(M_{ij})$ is set to be zero at $M_{ij}=0$, thus avoiding the problem of taking the logarithm of zero counts; it saturates at $M_{ij}=m_{\max}$, thus avoiding the problem of overcounting common word-context pairs. This heuristic turns out to be critical to the method's performance.

The time complexity of sparse matrix reconstruction is determined by the number of non-zero word-context counts. Pennington et al. (2014) show that this number grows sublinearly with the size of the dataset: roughly $\mathcal{O}(N^{0.8})$ for typical English corpora. In contrast, the time complexity of WORD2VEC is linear in the corpus size. Computing the co-occurrence counts also requires linear time in the size of the corpus, but this operation can easily be parallelized using MapReduce-style algorithms (Dean and Ghemawat, 2008).

## 14.6 Evaluating word embeddings

Distributed word representations can be evaluated in two main ways. Intrinsic evaluations test whether the representations cohere with our intuitions about word meaning. Extrinsic evaluations test whether they are useful for downstream tasks, such as sequence labeling.

