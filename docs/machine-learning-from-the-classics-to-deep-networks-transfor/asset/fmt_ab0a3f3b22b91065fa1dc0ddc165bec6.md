
![Equation](images/B9780443292385000172/si400.png)

*   and *ρ* ≥ 0 is left as a free variable, giving rise to the *ν*-SVM; *ν* is an extra parameter that controls the importance of *ρ* in the associated cost function. It has been shown [23] that the *ν*-SVM and the formulation discussed above, which is sometimes referred to as the *C*-SVM, lead to the same solution for appropriate choices of *C* and *ν*. However, the advantage of *ν*-SVM lies in the fact that *ν* can be directly related to bounds concerning the number of support vectors and the corresponding error rate (see also [123]).

*   • **Reduced convex hull interpretation**: In [58], it has been shown that for linearly separable classes, the SVM formulation is equivalent to finding the nearest points between the convex hulls formed by the data in the two classes. This result was generalized for overlapping classes in [33]; it is shown that in this case the *ν*-SVM task is equivalent to searching for the nearest points between the *reduced convex hulls* (RCHs) associated with the training data. Searching for the RCH is a computationally hard task of combinatorial nature. The problem was efficiently solved in [73–75,121], which came up with efficient iterative schemes to solve the SVM task, via nearest point searching algorithms. More on these issues can be obtained from [66,122,123].

*   • **ℓ₁ Regularized versions**: The regularization term, which has been used in the optimization tasks discussed so far, has been based on the ℓ₂ norm. A lot of research effort has been focused on using ℓ₁ norm regularization for tasks treating the linear case. To this end, a number of different loss functions have been used in addition to the squared error, hinge loss, and *ϵ*-insensitive versions, as for example the logistic loss. The solution of such tasks comes under the general framework discussed in Chapter [8](#Chp008_343-416_B9780443292385000147.xhtml). As a matter of fact, some of these methods have been discussed there. A related concise review is provided in [131].

*   • **Multitask learning**: In multitask learning, two or more related tasks, for example, classifiers, are jointly optimized. Such problems are of interest in, for example, econometrics and bioinformatics. In [40], it is shown that the problem of estimating many task functions with regularization can be cast as a single task learning problem if a family of appropriately defined multitask kernel functions is used.

### Example 11.4

In this example, the performance of the SVM is tested in the context of a two-class two-dimensional classification task. The data set comprises *N* = 150 points uniformly distributed in the region [−5, 5] × [−5, 5]. For each point **x**[*n*] = [*x*[*n*, 1], *x*[*n*, 2]]^(*T*), *n* = 1, 2, …, *N*, we compute

*y*[*n*] = 0.05*x*[*n*, 1]³ + 0.05*x*[*n*, 1]² + 0.05*x*[*n*, 1] + 0.05 + *η*,

where *η* stands for zero mean Gaussian noise of variance *σ*[*η*]² = 4. The point is assigned to either of the two classes, depending on the value of the noise as well as its position with respect to the graph of the function

*f*(*x*) = 0.05*x*³ + 0.05*x*² + 0.05*x* + 0.05
