
# M-Class Problem Generalization

What was said before for the two-class task can be generalized to the more general *M*-class problem. The separating hypersurfaces of two contiguous regions ℛ[*i*], ℛ[*j*] associated with classes *ω*[*i*], *ω*[*j*] obey the same arguments as the ones adopted before. For example, assuming that all covariance matrices are the same, the regions are partitioned via hyperplanes, as illustrated in [Fig. 7.6](#Chp007_293-342_B9780443292385000135.xhtml#f0040). Note that the decision lines (full red) bisect the segments (dotted lines) joining the mean values of the three classes. Moreover, each region ℛ[*i*], *i* = 1, 2, …, *M*, is convex (Problem [7.2](#Chp007_293-342_B9780443292385000135.xhtml#o0015)); in other words, joining any two points within ℛ[*i*] with a line segment, all the points lying on the respective segment lie in ℛ[*i*] as well.

![Figure 7.6 When data are distributed according to the Gaussian distribution and they share the same covariance matrix in all classes, the feature space is partitioned via hyperplanes, which form polyhedral regions. Note that each region is associated with one class and it is convex.](images/B9780443292385000135/gr006.jpg)

[Figure 7.6](#Chp007_293-342_B9780443292385000135.xhtml#cf0275) When data are distributed according to the Gaussian distribution and they share the same covariance matrix in all classes, the feature space is partitioned via hyperplanes, which form polyhedral regions. Note that each region is associated with one class and it is convex.

Two special cases are of particular interest, leading to a simple classification rule. The rule will be expressed for the general *M*-class problem.

## Minimum Distance Classifiers

There are two special cases, where the optimal Bayesian classifier becomes very simple to compute and it also has a strong geometric flavor.

### Minimum Euclidean Distance Classifier

Under the assumptions of (a) Gaussian distributed data in each one of the classes, i.e., Eq. [(7.16)](#Chp007_293-342_B9780443292385000135.xhtml#deq29), (b) equiprobable classes, and (c) common covariance matrix in all classes of the special form *Σ* = *σ*²*I* (individual features are independent and share a common variance), the Bayesian classification rule becomes equivalent to

```
Assign x to class ω_i: i = argmin_j (x - μ_j)^T (x - μ_j), j = 1,2,... M.
```

*   This is a direct consequence of the Bayesian rule under the adopted assumptions. In other words, the Euclidean distance of **x** is computed from the mean values of all classes and it is assigned to the class for which this distance becomes smaller.

*   For the case of the two classes, this classification rule corresponds to the full black line of [Fig. 7.5](#Chp007_293-342_B9780443292385000135.xhtml#f0035). Indeed, recalling our geometry basics, any point that lies on the left side of this hyperplane that *bisects* the segment **μ**[1] − **μ**[2] is closer to **μ**[1] than to **μ**[2], in the Euclidean distance sense. The opposite is true for any point lying on the right of the hyperplane.

### Minimum Mahalanobis Distance Classifier

Under the previously adopted assumptions, but with the covariance matrix being of the more general form *Σ* ≠ *σ*²*I*, the rule becomes
