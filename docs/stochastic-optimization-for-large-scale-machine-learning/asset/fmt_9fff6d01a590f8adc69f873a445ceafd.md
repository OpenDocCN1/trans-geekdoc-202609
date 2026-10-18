
The training time of models has two major components time to access the data and time to process (learn from) the data. So far, the research has focused only on the second part, i.e., learning from the data. In this chapter, we have proposed one possible solution to handle the big data problems in machine learning. The idea is to reduce the training time through reducing data access time by proposing systematic sampling and cyclic/sequential sampling to select mini-batches from the dataset. To prove the effectiveness of proposed sampling techniques, we have used empirical risk minimization, which is commonly used machine learning problem, for strongly convex and smooth case. The problem has been solved using `SAG`, `SAGA`, `SVRG`, `SAAG-II` and `MBSGD` (Mini-batched SGD), each using two step determination techniques, namely, constant step size and backtracking line search method. Theoretical results prove similar convergence for systematic and cyclic sampling as the widely used random sampling technique, in expectation. Empirical results with benchmarked datasets prove the efficacy of the proposed sampling techniques and show up to six times faster training.

## 5.1 Introduction

Nowadays, the major challenge is to develop efficient and scalable learning algorithms for dealing with big data problems, as discussed in detail in [Section 3.1](#05chap_03.xhtml#sec3_1). The training time of models have two major components \[[144](#bib.xhtml#refbib_144)\] as:

$$
\begin{array}{l}
{\text{training~time} = \text{time~to~access~data} + \text{time~to~process~data}.}
\\
\end{array}
$$

(5.1)

As it is known that for processing any data or running any program, it should be first brought into memory, more precisely into `RAM` (Random Access Memory), from hard disk. The time taken in bringing the data or program from hard disk into memory is called access time. Access time has, further, three components, namely, seek time (it is the time taken by the reading head to move from current position up to the track containing the data), rotational latency time (it is the time taken by the reading head from the current position to reach up to the sector/block containing the data) and transfer time (it is the time taken to transfer data from sector/block over the disk to memory). Moreover, data is not read content wise rather block-wise, where each block can have multiple sectors. Now, it is interesting to note that for data stored on the contiguous memory or in the close proximity, has lesser data access time as compared with the data dispersed far away from each other. This is due to lesser seek, latency and transfer times. In case of `SSD` (Solid State Disk) and `RAM` (Random Access Memory), there are no seek and latency times because they do not have moving parts and they are based on direct access mechanism, but transfer time still plays its role. Since data are read/written block-wise so for contiguous data access, there would be one or two transfer times but dispersed data access would require more number of transfer times. Moreover, cache memory strategies also favor the contiguous memory access and make it faster as compared to dispersed data access. Thus, contiguous data access time is faster than dispersed data access, in all the cases whether data is stored on `RAM`, `SSD` or `HDD`. But the difference in access time would be more prominent for `HDD`.

The second component of training time is processing (learning) time which is the time taken by the `CPU` (Central Processing Unit) to process the data to solve for model parameters. Due to mini-batching and iterative learning algorithms, the accessing and processing of data is intermixed and occurs quite frequently. The data access time is dependent on the sampling technique and processing time is dependent on the method used to solve the problem. Till this date, to improve the training time, most of the focus is given only to improve the processing time by using different methods. The training time is dependent on both data accessing time and data processing time, and this is to be noted that, generally, data access time is very high as compared to the data processing time. Thus, efforts should be equally done to improve the data accessing time. This chapter has tried to reduce the training time for big data problems by reducing the data access time using systematic sampling technique \[[93](#bib.xhtml#refbib_93), [94](#bib.xhtml#refbib_94)\] and cyclic sampling to select mini-batches of data points from the dataset.

### 5.1.1 Optimization Problem

Empirical risk minimization (`ERM`) problem \[[111](#bib.xhtml#refbib_111)\] is a commonly used problem in machine learning and statistics, which typically consists of a loss function and a regularization term. In this chapter, `l2`-regularized `ERM` problem with the assumptions of strong convexity and smoothness, is used for demonstrating the effectiveness of proposed sampling techniques. For the training data {(`x`[1],`y`[1]),(`x`[2],`y`[2]),...,(`x`[`l`],`y`[`l`])}, where `x`[`i`] ∈ ℝ^(`n`), `y`[`i`] ∈ ℝ, and for loss functions `f`[1],`f`[2],...`f`[`l`]: ℝ^(`n`)→ℝ, model parameter vector `w` ∈ ℝ^(`n`) and regularization coefficient `C` > 0, `l2`-regularized `ERM` problem is given by

$$
\begin{array}{l}
\begin{array}{l}
{\underset{w}{\min}\,\,\ f(w) = \frac{1}{l}{\sum\limits_{i = 1}^{l}f_{i}}(w) + \frac{C}{2}\| w\|^{2},}
\\
\end{array}
\\
\end{array}
$$

(5.2)

where first term is the data fitting term and second term is used for avoiding the over-fitting of data. Commonly used loss functions are the square loss (`w`^(`T`)`x`[`i`]−`y`[`i`])², the logistic loss log(1+`e`^`exp`(−`y`[`i`]`w`^(`T`)`x`[`i`])) and the hinge loss max(0,1−`y`[`i`]`w`^(`T`)`x`[`i`]). In this chapter, experimentation uses logistic loss function. When problem represented by eq.(5.2) is a large-scale or big data problem then per iteration complexity of learning algorithms with traditional methods like Gradient Descent is `O`(`n`*`l`) which is very high. This is because, such problems have large number of data points (`l`) or large number of features (`n`), or both, and each iteration updates `n` variables over `l` data points. Because of this high computational complexity per iteration it would be very expensive or even infeasible for single machine to process a single iteration of learning algorithm. Stochastic approximation approach is widely used for handling such cases (e.g., \[148, 63, 35, 19, 115, 23\]), which uses one data point or mini-batch of data points during each iteration. The reduced subproblem with mini-batch `B`[`j`] of data points for `j`^(`t`h) inner iteration is given by

$$
\begin{array}{l}
\begin{array}{l}
{\underset{w}{\min}\,\,\frac{1}{\left| B_{j} \right|}{\sum\limits_{i \in B_{j}}f_{i}}(w) + \frac{C}{2}\| w\|^{2},\quad j = 1,2,...,m.}
\\
\end{array}
\\
\end{array}
$$

(5.3)

The iteration complexity for solving this reduced subproblem is `O`(`n`) (for one data point) or `O`(`n`|`B`[`j`]|) (for mini-batch of data points) where |`B`[`j`]| is the size of mini-batch, which is very low and independent of `l`. Since it is easier to solve the problem (5.3) and this is widely used approach to handle large-scale problems so the chapter uses this reduced subproblem approach.

### 5.1.2 Literature Review
