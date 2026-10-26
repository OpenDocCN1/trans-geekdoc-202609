| word 1 | word 2 | similarity |
|---|---|---|
| love | sex | 6.77 |
| stock | jaguar | 0.92 |
| money | cash | 9.15 |
| development | issue | 3.97 |
| lad | brother | 4.46 |

Table 14.4: Subset of the WS-353 (Finkelstein et al., 2002) dataset of word similarity ratings (examples from Faruqui et al. (2016)).

GloVe ("global vectors") are a closely related approach (Pennington et al., 2014), in which the matrix to be factored is constructed from log co-occurrence counts, $M_{ij} = \log \text{count}(i, j)$. The word embeddings are estimated by minimizing the sum of squares,

$\min_{\boldsymbol{u},\boldsymbol{v},b,\tilde{b}} \sum_{i=1}^{V} \sum_{j \in C} f(M_{ij}) \left( \widehat{\log M_{ij}} - \log M_{ij} \right)^2$

s.t. $\widehat{\log M_{ij}} = \boldsymbol{u}_i \cdot \boldsymbol{v}_j + b_i + \tilde{b}_j$, \quad [14.25]

where $b_i$ and $\tilde{b}_j$ are offsets for word $i$ and context $j$, which are estimated jointly with the embeddings $\boldsymbol{u}$ and $\boldsymbol{v}$. The weighting function $f(M_{ij})$ is set to be zero at $M_{ij}=0$, thus avoiding the problem of taking the logarithm of zero counts; it saturates at $M_{ij}=m_{\max}$, thus avoiding the problem of overcounting common word-context pairs. This heuristic turns out to be critical to the method's performance.

The time complexity of sparse matrix reconstruction is determined by the number of non-zero word-context counts. Pennington et al. (2014) show that this number grows sublinearly with the size of the dataset: roughly $\mathcal{O}(N^{0.8})$ for typical English corpora. In contrast, the time complexity of WORD2VEC is linear in the corpus size. Computing the co-occurrence counts also requires linear time in the size of the corpus, but this operation can easily be parallelized using MapReduce-style algorithms (Dean and Ghemawat, 2008).

# 14.6 Evaluating word embeddings

Distributed word representations can be evaluated in two main ways. Intrinsic evaluations test whether the representations cohere with our intuitions about word meaning. Extrinsic evaluations test whether they are useful for downstream tasks, such as sequence labeling.