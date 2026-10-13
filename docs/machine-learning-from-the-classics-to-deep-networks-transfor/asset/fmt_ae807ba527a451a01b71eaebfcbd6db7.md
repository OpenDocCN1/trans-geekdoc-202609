
**ϕ** = [*ϕ*₁(**x**), …, *ϕ*ₗ(**x**)]^(*T*).

Example 5.2
The aim of this example is to demonstrate the pair of Eqs. [(5.32)](#Chp005_177-248_B9780443292385000111.xhtml#deq58) and [(5.33)](#Chp005_177-248_B9780443292385000111.xhtml#deq59), which characterize the convergence properties of the stochastic gradient scheme.

Data samples were first generated according to the regression model

*y*[*n*] = **θ**^(*T*)**x**[*n*] + *η*[*n*],

where **θ** ∈ ℝ² was randomly chosen and then fixed. The elements of **x**[*n*] were i.i.d. generated via a normal distribution 𝒩(0, 1) and *η*[*n*] are samples of a white noise sequence with variance equal to *σ*² = 0.1. Then the observations (*y*[*n*], **x**[*n*]) were used in the recursive scheme in Eq. [(5.34)](#Chp005_177-248_B9780443292385000111.xhtml#deq61) to obtain an estimate of **θ**. The experiment was repeated 200 times and the mean and variance of the obtained estimates were computed for each iteration step. [Fig. 5.12](#Chp005_177-248_B9780443292385000111.xhtml#f0065) shows the resulting curve for one of the parameters (the trend for the other one being similar). Observe that the mean values of the estimates tend to the true value, corresponding to the red line, and the standard deviation keeps decreasing as *n* grows. The step size was chosen equal to *μ*[*n*] = 1/*n*.

![Figure 5.12 The red line corresponds to the true value of the unknown parameter. The black curve corresponds to the average over 200 realizations of the experiment. Observe that the mean value converges to the true value. The bars correspond to the respective standard deviation, which keeps decreasing as n grows.](images/B9780443292385000111/gr012.jpg)

[Figure 5.12](#Chp005_177-248_B9780443292385000111.xhtml#cf0555) The red line corresponds to the true value of the unknown parameter. The black curve corresponds to the average over 200 realizations of the experiment. Observe that the mean value converges to the true value. The bars correspond to the respective standard deviation, which keeps decreasing as *n* grows.

## 5.5 The least-mean-squares adaptive algorithm

The stochastic gradient descent algorithm in Eq. [(5.34)](#Chp005_177-248_B9780443292385000111.xhtml#deq61) converges to the optimal MSE solution provided that *μ*[*n*] satisfies the two convergence conditions. Once the algorithm has converged, it “locks” at the obtained solution. In a case where the statistics of the involved variables/processes and/or the unknown parameters start changing, the algorithm cannot track the changes. Note that if such changes occur, the error term

*e*[*n*] = *y*[*n*] − **θ**[*n* − 1]^(*T*)**x**[*n*]

will attain larger values; however, because *μ*[*n*] is very small, the increased value of the error will not lead to corresponding changes of the estimate at time *n*. This can be overcome if one sets the value of *μ*[*n*] to a preselected *fixed* value, *μ*. The resulting algorithm is the celebrated least-mean-squares (LMS) algorithm [102].

### Algorithm 5.1: The LMS algorithm

*   Initialize
