can be adapted to analyse variants of the original AMP recursion that are geared towards more statistical problems. In this aspect, we focus on two canonical statistical settings, namely estimation of low-rank matrices in Section 3, and estimation in generalised linear models (GLMs) in Section 4. The former encompasses Sparse Principal Component Analysis (Deshpande and Montanari, 2014; Gataric et al., 2020; Jolliffe et al., 2003; Wang et al., 2016; Zou et al., 2006), submatrix detection (Ma and Wu, 2015), hidden clique detection (Alon et al., 1998; Deshpande and Montanari, 2015), spectral clustering (von Luxburg, 2007), matrix completion (Candès and Recht, 2009; Zhu et al., 2019), topic modelling (Blei et al., 2003) and collaborative filtering (Su and Khoshgoftaar, 2009). The latter provides a holistic approach to studying a suite of popular modern statistical methods, including penalised M-estimators such as the Lasso (Tibshirani, 1996) and SLOPE (Bogdan et al., 2015), as well as more traditional techniques such as logistic regression. A novel aspect of our presentation in Section 4 is that we formalise the connection between AMP and a broad class of convex optimisation problems, and then show how to systematically derive exact expressions for the asymptotic risk of estimators in GLMs. We expect that our general recipe can be applied to a wider class of GLMs than have been studied in the AMP literature to date.

To preview the statistical content in this tutorial and highlight some recurring themes, we now discuss two prototypical applications of AMP that form the basis of Sections 3 and 4 respectively. First, suppose that we wish to estimate an unknown signal \( v \in \mathbb{R}^n \) based on an observation

```
\( A = \frac{\lambda}{n} vv^\top + W, \)
```

where \( \lambda > 0 \) is fixed and \( W \in \mathbb{R}^{n \times n} \) is a symmetric Gaussian noise matrix. In this so-called spiked Wigner model (see Section 3.1 and the references therein), a popular and well-studied estimator of \( v \) is the leading eigenvector \( \hat{\varphi} \) of \( A \), which can be approximated via the power method, with iterates

```
\( v^{k+1} = \frac{Av^k}{\|Av^k\|}. \)
```