
s.t. $A(i, k) \ge 0$, $Z(k, j) \ge 0$,

where $[AZ](i, j)$ is the $(i, j)$ element of matrix $AZ$, and $i, j, k$ run over all possible values. Besides the Frobenius norm, other costs have also been suggested (see, e.g., [168]).

Once the problem has been formulated, the major issue rests at the solution of the optimization task. To this end, a number of algorithms have been proposed, for example, Newton-type or gradient descent-type algorithms. Such algorithmic issues, as well as a number of related theoretic ones, are beyond the scope of this book, and the interested reader may consult, for example, [54, 67, 178]. More recently, regularized versions, including sparsity promoting regularizers, have been proposed (see, for example, [55]).

## 20.8 Learning low-dimensional models: a probabilistic perspective

In this section, the emphasis is on looking at the dimensionality reduction task from a Bayesian perspective. Our focus will be more on presenting the main ideas and less on algorithmic procedures; the latter depend on the specific model and can be dug out from the palette of algorithms that have already been presented in Chapters [12](#Chp012_583-634_B9780443292385000184.xhtml) and [13](#Chp013_635-716_B9780443292385000196.xhtml). Our path to low-dimensional modeling traces its origin to the so-called *factor analysis*.

### 20.8.1 Factor analysis

Factor analysis was originally proposed in the work of Charles Spearman [169]. Charles Spearman (1863–1945) was an English psychologist who has made important contributions to statistics. Spearman was interested in human intelligence and developed the method in 1904 for analyzing multiple measures of cognitive performance. He argued that there exists a general intelligence factor (the so-called g-factor) that can be extracted by applying the factor analysis method on intelligence test data. However, this notion has also been disputed, as intelligence comprises a multiplicity of components (see, e.g., [84]).

Let $\mathbf{x} \in \mathbb{R}^{(l)}$. The factor analysis model assumes that there are $m < l$ underlying (latent) zero mean variables or *factors* $\mathbf{z} \in \mathbb{R}^{(m)}$ so that

$$
x_i - \mu_i = \sum_{j=1}^{m} a_{ij} z_j + \epsilon_i, \quad i = 1, 2, \ldots, l,
$$

or compactly written using the vector notation,

$$
\mathbf{x} - \boldsymbol{\mu} = A\mathbf{z} + \boldsymbol{\epsilon},
$$
