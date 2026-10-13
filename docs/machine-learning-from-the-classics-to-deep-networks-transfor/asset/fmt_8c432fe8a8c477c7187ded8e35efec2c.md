
## 8.12 Online learning and big data applications: a discussion

Online learning algorithms have been treated in Chapters [4](#Chp004_119-175_B978044329238500010X.xhtml), [5](#Chp005_177-248_B9780443292385000111.xhtml), and [6](#Chp006_249-291_B9780443292385000123.xhtml). The purpose of this section is to first summarize some of the findings and at the same time present a discussion related to the performance of online schemes compared to their batch relatives.

Recall that the ultimate goal in obtaining a parametric predictor,

$$\hat{y} = f_{\boldsymbol{\theta}}(\boldsymbol{x})$$

is to select $\boldsymbol{\theta}$ so that to optimize the *expected loss/risk* function in Eq. [(8.65)](#Chp008_343-416_B9780443292385000147.xhtml#deq139). For practical reasons, the corresponding empirical formulation in Eq. [(8.66)](#Chp008_343-416_B9780443292385000147.xhtml#deq140) is most often adopted instead. From the learning theory's point of view, this is justified provided the respective class of functions is sufficiently restrictive [94]. The available literature is quite rich in obtaining performance bounds that measure how close the optimal value obtained via the expected loss is to that obtained via the empirical one, as a function of the number of points $N$. Note that as $N \to \infty$, and recalling well-known arguments from probability theory and statistics, the empirical risk tends to the expected loss (under general assumptions). Thus, for very large training data sets, adopting the empirical risk may not be that different from using the expected loss. However, for data sets of shorter lengths, a number of issues occur. Besides the value of $N$, another critical factor enters the scene; this is the *complexity* of the family of the functions in which we search a solution. In other words, the generalization performance critically depends not only on $N$ but also on how large or small this set of functions is. A related discussion for the specific case of the MSE was presented in Chapter [3](#Chp003_65-117_B9780443292385000093.xhtml), in the context of the bias–variance tradeoff. The roots of the more general theory go back to the pioneering work of Vapnik–Chervonenkis; see [31,95,96], and [88] for a less mathematical summary of the major points.

### Strongly Convex Loss Functions

*   Tighter regret bounds can be derived when the loss function is strongly convex [43]. A function $f: \mathcal{X} \subseteq \mathbb{R}^l \mapsto \mathbb{R}$ is said to be $\sigma$-*strongly convex* if, $\forall \boldsymbol{y}, \boldsymbol{x} \in \mathcal{X}$,

    $$f(\boldsymbol{y}) \geq f(\boldsymbol{x}) + \boldsymbol{g}^{T}(\boldsymbol{y} - \boldsymbol{x}) + \frac{\sigma}{2}||\boldsymbol{y} - \boldsymbol{x}||^{2},$$

    for any subgradient $\boldsymbol{g}$ at $\boldsymbol{x}$. It also turns out that a function $f(\boldsymbol{x})$ is strongly convex if $f(\boldsymbol{x}) - \frac{\sigma}{2}||\boldsymbol{x}||^{2}$ is convex (Problem [8.30](#Chp008_343-416_B9780443292385000147.xhtml#o0180)).

*   For $\sigma$-strongly convex loss functions, if the step size of the subgradient algorithm is diminishing at a rate $\mathcal{O}(\frac{1}{\sigma n})$, then the average cumulative loss is approaching the average loss of the optimal predictor at a rate $\mathcal{O}(\frac{\ln N}{N})$ (Problem [8.31](#Chp008_343-416_B9780443292385000147.xhtml#o0185)). This is the case, for example, for the PEGASOS algorithm, discussed in Section [8.10.3](#Chp008_343-416_B9780443292385000147.xhtml#s0125).

*   In [4,5], $\mathcal{O}(1/N)$ convergence rates are derived for a set of non-strongly convex smooth loss functions (e.g., squared error and logistic regression) even for the case of constant step sizes. The analysis method follows statistical arguments.
