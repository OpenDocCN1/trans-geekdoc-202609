
For large-scale learning problems or big data problems in machine learning, number of data points and/or number of features are large, which lead to high per-iteration complexity for the iterative algorithms. To deal with the large-scale problems or big data problems in machine learning, stochastic approximation and coordinate descent are very effective. Stochastic approximation randomly samples one or few data points during each iteration and makes each iteration independent of number of data points in the dataset. It has been widely and successfully used with first and second order methods.

Similarly, coordinate descent (CD) approach samples one or block of features as variables and rest as constants, which makes each iteration independent of number of features. So, CD is very effective to deal with the high dimensional problems. It is clear that SA and CD are very effective to deal with big data problems. Now, it is interesting to study these techniques together because they can make each iteration independent of `n` and `l` and that can provide an efficient and scalable solution. The combination of SA and CD has been studied for first order methods, e.g., \[133, 140, 146, 152\], and to the best of our knowledge not studied for second order methods. We studied it and proposed BBOF (batch block optimization framework) and SAAG-I and II (stochastic average adjusted gradient methods) to work with BBOF \[23\]. We observed that SA and CD approaches do not work well together \[28\]. This is because of the extra computational overhead to implement, dominates the advantage of using SA and CD together.

In this chapter, we have studied SA and CD together with second order method. We observe similar results as observed with first order methods. The advantage of low and controllable per-iteration complexity is lost in the extra-overhead to implement the learning algorithm due to double sampling, i.e., sampling of data and features, and associated implementation issues.

### 6.1.1 Contributions

The contributions of the chapter are given below:

*   We have studied mini-batch block-coordinate setting, i.e., BBOF framework with second order methods, with an intention to solve the issues related with the Newton method.

*   Empirical results have proved that BBOF does not help with second order methods, i.e., proposed reduced per iteration complexity is not able to get the overall benefit in training on a large-scale problem.

## 6.2 MBN

MBN (mini-batch block-coordinate Newton) method is based on the best of SA and CD approaches with Newton method to solve problem (6.1). The idea of the method is to reduce the per-iteration complexity and make it controllable by using subsampling of data points and features. This looks to solve the major issues with the Newton method, as is clear from the update rule of MBN.

$$
\begin{array}{l}
\begin{array}{l}
{w_{k + 1} = w_{k} - \alpha_{k}\left\lbrack {\nabla_{C_{k}}^{2}F_{B_{k}}{(w_{k})}^{- 1}\nabla_{C_{k}}F_{B_{k}}(w_{k})} \right\rbrack e_{C_{k}},}
\\
\end{array}
\\
\end{array}
$$

(6.3)

where

$$
\begin{array}{l}
{e_{C_{k}}[i] = \left\{ \begin{array}{l}
{1\quad\quad\text{if}\,\, i \in C_{k}} \\
{0\quad\quad\text{else}} \\
\end{array}~\right.,}
\\
\end{array}
$$

$$
\begin{array}{l}
\begin{array}{l}
{\nabla_{C_{k}}^{2}F_{B_{k}}\left( w_{k} \right) = \frac{1}{| B_{k} |}{\sum\limits_{i \in B_{k}}\nabla_{C_{k}}^{2}}f_{i}\left( w_{k} \right),} \\
{\nabla_{C_{k}}F_{B_{k}}\left( w_{k} \right) = \frac{1}{| B_{k} |}{\sum\limits_{i \in B_{k}}\nabla_{C_{k}}}f_{i}\left( w_{k} \right),} \\
\end{array}
\\
\end{array}
$$

(6.4)

∇[*C*[*k*]]*F*[*B*[*k*]](*w*[*k*]) represents partial gradient over the selected block *C*[*k*] and ∇[*C*[*k*]]²*F*[*B*[*k*]](*w*[*k*]) represents partial Hessian over *C*[*k*] and is of size |*C*[*k*]|×|*C*[*k*]|. Thus, the per-iteration complexity of (6.3) is *O*(|*C*[*k*]|[2]|*B*[*k*]|+|*C*[*k*]|[3]) which is much smaller and controllable than per-iteration complexity of Newton method. MBN looks to solve the problems related to Newton method and is presented using the [Algorithm 15](#09chap_06.xhtml#algorithm_15). This algorithm is similar to BBOF when used with Newton method. The algorithm samples a mini-batch of data points and a block of features during each iteration and formulates a reduced subproblem, which is then solved using parameter update rule similar to Newton's method. Since it works with a subsample of data with subsample of features, this leads to reduction in per-iteration complexity. The size of Hessian used in the subproblem is |*C*[*k*]|², which is much smaller and controllable.

![](Images/algo15.jpg)

## 6.3 Experiments

In this section, we present the experimental results. We have used following datasets: mushroom and real-sim, whose details are given in the Table 1.1, and compared the following methods:

**MBN:** This is the proposed method.

**SNewton:** This is subsampled Newton method which uses progressive subsampling for gradient and Hessian calculations.

**Newton:** This is exact Newton method.

**TRON:** This is trust region Newton method which uses PCG (preconditioned conjugate gradient) method to solve the trust region subproblem. This is one of the widely used method to solve large-scale classification problems and is available in LIBLINEAR library \[38\].

**SVRG-SQN:** This is a stochastic quasi-Newton method \[[99](#bib.xhtml#refbib_99)\].

### 6.3.1 Experimental Setup

The regularization parameter is set as *λ* = 1/*l* for all the methods and learning rate is determined using stochastic backtracking line search for subsampled methods, i.e., MBN, SNewton and SVRG-SQN, and deterministic backtracking line search is used with Newton method. MBN and SNewton methods use progressive subsampling with initial mini-batch size of 10%. SVRG-SQN uses sample size of 10% and memory size (M) and update frequency (L) are set to a value of 10. All the methods are implemented using MATLAB and executed on MacBook Air (8 GB 1600 MHz DDR3, 1.6 GHz Intel Core i5 and 256GB SSD).

![FIGURE 6.1 Comparison of MBN, SNewton, TRON, Newton and SVRG-SQN on mushroom dataset.](Images/fig6_1.jpg)

FIGURE 6.1 Comparison of MBN, SNewton, TRON, Newton and SVRG-SQN on mushroom dataset.

![FIGURE 6.2 Comparison of MBN, SNewton, TRON, Newton and SVRG-SQN on real-sim dataset.](Images/fig6_2.jpg)

FIGURE 6.2 Comparison of MBN, SNewton, TRON, Newton and SVRG-SQN on real-sim dataset.

### 6.3.2 Comparative Study

Results compare MBN, SNewton, Newton, TRON and SVRG-SQN by plotting cost and test accuracy against training time (in seconds) and epochs. [Figures 6.1](#09chap_06.xhtml#f6_1)–6.2 depict the results on two different datasets. For mushroom dataset (Fig. 6.1), MBN performs similar to Newton for results on epochs and outperform all other methods but lags behind other methods on training time. SNewton beats all methods in terms of training time. For real-sim ([Fig. 6.2](#09chap_06.xhtml#f6_2)), we observe similar results where Newton and MBN outperform others on epochs but lags on the training time.

## 6.4 Conclusion

We have proposed to use Newton methods with best of stochastic approximation, i.e., mini-batching and best of coordinate descent, i.e., block-coordinates, with hope to reduce the per-iteration complexity and develop scalable and efficient method. But it is observed that inspite of reduced and controllable per-iteration complexity, MBN failed to perform as per the expectations due to double sampling of data points and features and associated overhead of implementation, and lags behind (singly) sampled stochastic Newton and pure Newton method. Thus, it is not suitable to use stochastic approximation and coordinate descent approaches together until we find a way to reduce the overhead associated with double sampling.
