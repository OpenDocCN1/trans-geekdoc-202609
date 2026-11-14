
& Rubinstein 2014; Zhang, Rubinstein, & Dimitrakakis 2016) and sampled settings (Wang et al. 2015). Other work develops generic mechanisms for function release under differential privacy: Hall, Rinaldo, & Wasserman (2013) add Gaussian process noise, yielding a weaker form of differential privacy, without general results on utility rates; Wang, Fan, Zhang, & Wang (2013) release privatized projections, in a trigonometric basis, of functions that are separable in the training data, similar to Zhang et al. (2012); Alda & Rubinstein (2017) propose the Bernstein mechanism as a functional form of the Laplace mechanism for vector release, which achieves differential privacy and strong utility guarantees under general conditions of smoothness of the nonprivate function, by using iterated Bernstein polynomial approximation.

## Practical Privacy-Preserving Learning (Mostly) via Subset Sums

Most work in differential privacy has focused on the deep analysis of mechanisms for relatively simple statistics (with histograms and contingency tables as explored by Blum et al. 2005 and Barak et al. 2007, respectively, as examples) and learning algorithms (e.g., interval queries and halfspaces as explored by Blum et al. 2008), or on constructing learning algorithms that can be decomposed into subset-sum operations (e.g., perceptron, k-NN, ID3 as described by Blum et al. 2005, and various recommender systems as shown by McSherry & Mironov 2009). Some early work in function release focuses on functions separable (expressable as sums) over training data (Zhang et al. 2012; Wang et al. 2013). By contrast, this chapter explores the more practical goal of SVM learning, which does not generally decompose into a subset sum (Rubinstein et al. 2012; Appendix A). It is also notable that the mechanisms here run in polynomial time.

## The Privacy-Utility Tradeoff

Like several early studies, we explore here the tradeoff between privacy and utility. Barak et al. (2007) present a mechanism for releasing contingency tables that guarantees differential privacy and also guarantees a notion of accuracy: with high probability all marginals from the released table are close in \(\ell_1\)-norm to the true marginals. As mentioned earlier, Blum et al. (2008) develop a private noninteractive mechanism that releases anonymized data such that all predicate queries in a VC class take on similar values regardless of whether they are taken over the anonymized data and original data. Kasiviswanathan et al. (2008) consider utility as corresponding to PAC learning: with high probability the response and target concepts are close, averaged over the underlying measure.

Early negative results show that any mechanism providing overly accurate responses cannot be private (Dinur & Nissim 2003; Dwork & Yekhanin 2008; Beimel et al. 2010; Hardt & Talwar 2010). Dinur & Nissim (2003) show that if a noise of rate only \(o(\sqrt{N})\) is added to subset-sum queries on a database of bits, then an adversary can reconstruct a \(1 - o(1)\) fraction of the bits. This threshold phenomenon says that if accuracy is too great, privacy cannot be guaranteed at all. A similar negative result can be shown for the case of private SVM learning: i.e., requiring very high accuracy with respect to the SVM prevents high levels of privacy. De (2012) summarizes approaches to lower-bounding utility under differential privacy such as the volumetric packing approach used here.

The results presented here are qualitatively closer to those of Hardt & Talwar (2010) and Beimel et al. (2010). The former work finds almost matching upper and lower bounds for the tradeoff between differential privacy and accuracy through the lens of convex geometry, in the following setting that encompasses releasing histograms and recommender systems. Queries submitted to the interactive mechanism are linear mappings on a private database of reals. Nonprivate responses are the vector image of the query applied to the database, the mechanism’s responses are a randomized version of this target image, and the mechanism’s accuracy is the expected Euclidean distance between nonprivate and private responses. Beimel et al. (2010) focus on the notion of private learning (Kasiviswanathan et al. 2008) in which a private learner not only PAC learns but the release of its hypothesis is differentially private with respect to the training data. Beimel et al. (2010) delve into the sample complexity of private learning—and demonstrate separation results between proper and improper private learning—which do not exist for nonprivate PAC learning—and between efficient and inefficient proper private learners. Both papers consider negative results on the tradeoff between notions of utility and differential privacy. In SVM learning, concept classes are not necessarily linear or have finite VC-dimension.

The ε-packing proof technique used in the lower bound for SVM learning with the RBF kernel, although discovered independently, is similar to the technique used by Hardt & Talwar (2010) to establish lower bounds for their setting of privately responding to linear map queries. See also (De 2012) for a general account.

## Connections between Stability and Differential Privacy

To prove differential privacy in this chapter, a proof technique is borrowed from algorithmic stability. In passing, Kasiviswanathan et al. (2008) predict a possible relationship between algorithmic stability and differential privacy; however, they do not describe in detail how to exploit this. Since then, Wang et al. (2016) have drawn connections between stability, learnability, and privacy.

## 7.3 Support Vector Machines: A Brief Primer

Empirical risk minimization (ERM) can lead to overfitting or poor generalization (risk of the minimizer), so in theory and practice it is more desirable to perform regularized empirical risk minimization, which minimizes the sum of the empirical risk and uses a regularization term that imposes a soft smoothness constraint on the classifier. A well-known example is the soft-margin support vector machine that has the following primal program, for convex loss ℓ (·, ·),

```
\min_{\mathbf{w} \in \mathbb{R}^d} \frac{1}{2} \|\mathbf{w}\|_2^2 + \frac{C}{N} \sum_{i=1}^N \ell \left(y^{(i)}, f_{\mathbf{w}}(\mathbf{x}^{(i)})\right) ,
```

3 A proper learner outputs a hypothesis from the target concept class.

where for chosen feature mapping \(\phi : \Re^D \rightarrow \Re^F\) taking points in input space \(\Re^D\) to some (possibly infinite) \(F\)-dimensional feature space, and hyperplane normal \(\mathbf{w} \in \Re^F\), we define

\(f_{\mathbf{w}}(\mathbf{x}) = \langle \phi(\mathbf{x}), \mathbf{w} \rangle.\)

Parameter \(C > 0\) is the soft-margin parameter that controls the degree of regularization. Let \(\mathbf{w}^*\) denote an optimizing weight vector. Then predictions are taken as the sign of \(f^*(\mathbf{x}) = f_{\mathbf{w}^*}(\mathbf{x})\). We will refer to both \(f_{\mathbf{w}}(\mathbf{x})\) and \(\text{sign}(f_{\mathbf{w}}(\mathbf{x}))\) as classifiers, with the exact meaning apparent from the context.

An overview of the relevant details on learning follows (for full details, see, for example Burges 1998; Cristianini & Shawe-Taylor 2000; Schölkopf & Smola 2001; Bishop 2006). In order for the primal to be convex and the process of SVM learning to be tractable, \(\ell(y, \hat{y})\) is chosen to be a loss function that is convex in \(\hat{y}\). A common convex surrogate for the 0-1 loss and the loss most commonly associated with the SVM, is the hinge loss \(\ell(y, \hat{y}) = \max[1 - y\hat{y}, 0]\) that upper bounds the 0-1 loss and is non-differentiable at \(y\hat{y} = 1\). Other example losses include the square loss \((1 - y\hat{y})^2\) and the logistic loss \(\log(1 + \exp(-y\hat{y}))\). We consider general convex losses in this chapter, and a detailed case study of private SVM learning under the hinge loss in Section 7.7.1.

**Remark 7.5** We say that a learning algorithm is *universally consistent* if for all distributions \(\mu\) it is *consistent*: its expected risk converges to the minimum achievable (Bayes) risk with increasing sample size (Devroye, Györfi, & Lugosi 1996). For universal consistency, the SVM's parameter \(C\) should increase like \(\sqrt{N}\).

When \(F\) is large the solution may be more easily obtained via the dual. For example, the following is the dual formulation on the \(N\) dual variables for learning with hinge loss:

\(\max_{\alpha \in \Re^N} \sum_{i=1}^N \alpha_i - \frac{1}{2} \sum_{i=1}^N \sum_{j=1}^N \alpha_i \alpha_j y^{(i)} y^{(j)} k(\mathbf{x}^{(i)}, \mathbf{x}^{(j)})\) (7.1)
\(\text{s.t. } 0 \le \alpha_i \le \frac{C}{N} \forall i \in [N],\)

where \(k(\mathbf{x}, \mathbf{z}) = \langle \phi(\mathbf{x}), \phi(\mathbf{z})\rangle\) is the kernel function.

The vector of maximizing duals \(\alpha^*\) parametrizes the function \(f^* = f_{\alpha^*}\) as

\(f_{\alpha}(\cdot) = \sum_{i=1}^N \alpha_i y^{(i)} k(\cdot, \mathbf{x}^{(i)}).\)

The space of SVM classifiers endowed with the kernel function forms a reproducing kernel Hilbert space \(\mathcal{H}\).
