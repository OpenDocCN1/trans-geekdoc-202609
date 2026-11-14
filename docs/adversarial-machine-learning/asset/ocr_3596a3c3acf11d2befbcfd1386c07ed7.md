Remark 7.28 Equivalently this result can be written as follows. For any \(C > 0\), \(\beta > 0\), and \(N > 1\), if a mechanism \(\hat{M}\) is \((\epsilon, \delta)\)-useful and \(\beta\)-differentially private, then either \(\epsilon \ge \frac{\sqrt{C}}{2N}\) or \(\delta \ge \exp(-\beta)\).

We have now presented both upper bounds (Corollary 7.23 with \(L = 1\)) and lower bounds on the optimal differential privacy for the case of the linear SVM with hinge loss. Ignoring constants and using the scaling of \(C\) (see Remark 7.5) we have that

```
\(\Omega \left( \log \frac{1}{\delta} \right) = \beta^* = \mathcal{O} \left( \frac{1}{\epsilon \sqrt{N}} \log \frac{1}{\delta} \right).\)
```

It is noteworthy that the bounds agree in their scaling on utility confidence \(\delta\), but that they disagree on linear and square-root terms in their dependence on \(\epsilon\) and \(N\), respectively. Moreover under the appropriate scaling of \(C\), the lower bound holds only for \(\epsilon = \mathcal{O} \left( N^{-0.75} \right)\); under which the upper asymptotic bound becomes \(\mathcal{O} \left( N^{0.25} \log(1/\delta) \right)\). Finding better-matching bounds remains an interesting open problem.

We refer the reader to Rubinstein et al. (2012) for a similar lower bound under the RBF kernel. There a negative sensitivity result is achieved not through a pair of neighboring databases that induce very different SVM results, but through a sequence of \(K\) pairwise-neighboring databases whose images under SVM learning form an \(\epsilon\)-packing.

# 7.8 Summary

In this chapter we presented mechanisms for private SVM learning due to Chaudhuri et al. (2011) and Rubinstein et al. (2012), which release a classifier based on a privacy-sensitive database of training data. The former approach is one of objective perturbation while the latter performs output perturbation, calibrated by the algorithmic stability of regularized ERM—a property that is typically used in learning theory to prove risk bounds of learning algorithms.

In addition to measuring the training data differential privacy preserved by the output perturbation mechanisms, we also focused on their utility: the similarity of the classifiers released by private and nonprivate SVM. This form of utility implies good generalization error of the private SVM. To achieve utility under infinite-dimensional feature mappings, both families of approach perform regularized empirical risk minimization (ERM) in a random reproducing kernel Hilbert space whose kernel approximates the target kernel. This trick, borrowed from large-scale learning, permits the mechanisms to privately respond with a finite representation of a maximum-margin hyperplane classifier. We explored the high-probability, pointwise similarity between the resulting function and the nonprivate SVM classifier through a smoothness result of regularized ERM with respect to perturbations of the RKHS.

Interesting directions involve extending the ideas of this chapter to other learning algorithms:

QUESTION 7.1 Can the mechanisms and proof techniques used for differentially private SVM by output perturbation be extended to other kernel methods?