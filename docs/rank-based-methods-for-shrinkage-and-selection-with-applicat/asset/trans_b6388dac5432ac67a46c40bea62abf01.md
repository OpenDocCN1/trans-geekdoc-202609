

+\lambda^2(1-\alpha)^2\delta_1^\top\left[\mathcal{X}_1+\lambda(1-\alpha)\boldsymbol{I}_{p_1}\right]^{-2}\delta_1.\quad (4.9.8)

否则，nEnetRE 优于 HTRE。因此，HTRE 和 nEnetRE 两者中没有一种始终优于另一种。

### 4.9.13 Comparison of nEnetRE with SSRE

The ADL$_2$-risk difference of the Stein–Saleh-type R-estimator and nEnetRE is given by

\(\eta^2\left[\mathrm{tr}(\mathcal{K}_2)-(p_2-2)\mathrm{tr}(\mathcal{K}_2)\left(\mathbb{E}\left[\chi_{p_2+2}^{-2}(\Delta^2)\right]\right.\right.\)
\(\left.\left.+\Delta^2\mathbb{E}\left[\chi_{p_2+2}^{-4}(\Delta^2)\right]\right)+(p_2^2-4)\Delta_L^2\mathbb{E}\left[\chi_{p_2+4}^{-4}(\Delta^2)\right]\right]\)
\(-\eta^2\left[\mathrm{tr}(\mathcal{K}_1)-\left\{\mathrm{tr}(\boldsymbol{I}_{p_1}+\lambda(1-\alpha)\mathcal{K}_1)^{-2}\mathcal{K}_1\right.\right.\)
\(\left.\left.+\lambda^2(1-\alpha)^2\delta_1^\top\left[\mathcal{K}_1^{-1}+\lambda(1-\alpha)\boldsymbol{I}_{p_1}\right]^{-2}\delta_1+\Delta^2\mathrm{Ch}_{min}(\mathcal{K}_2)\right\}\right]\ge 0.\)

That means

\(\mathrm{ADL}_2\text{-risk}(\hat{\beta}_{in}^{SSR})+\eta^2\Delta_L^2\ge\eta^2\left[\mathrm{tr}(\mathcal{K}_1)-\mathrm{tr}(\boldsymbol{I}_{p_1}+\lambda(1-\alpha)\mathcal{K}_1)^{-2}\mathcal{K}_1\right.\)
\(\left.+\lambda^2(1-\alpha)^2\delta_1^\top\left[\mathcal{K}_1^{-1}+\lambda(1-\alpha)\boldsymbol{I}_{p_1}\right]^{-2}\delta_1\right]\ge 0.\)

Hence, the nEnetRE performs better than SSRE uniformly.

### 4.9.14 Comparison of Ridge-type vs. nEnetRE

In this case, the ADL$_2$-risk difference is given by

\(\eta^2\left[\left\{\mathrm{tr}(\mathcal{K}_1)+\frac{(\mathrm{tr}(\mathcal{K}_2))\Delta_L^2}{\mathrm{tr}(\mathcal{K}_2)+\Delta_L^2}\right\}-\left\{\mathrm{tr}(\boldsymbol{I}_{p_1}+\lambda(1-\alpha)\mathcal{K}_1)^{-2}\mathcal{K}_1\right.\right.\)
\(\left.\left.+\lambda^2(1-\alpha)^2\delta_1^\top\left[\mathcal{K}_1^{-1}+\lambda(1-\alpha)\boldsymbol{I}_{p_1}\right]^{-2}\delta_1+\Delta_L^2\right\}\right]\)
\(=\eta^2\left[\mathrm{tr}(\mathcal{K}_1)-\left(\mathrm{tr}\left((\boldsymbol{I}_{p_1}+\lambda(1-\alpha)\mathcal{K}_1)^{-2}\mathcal{K}_1\right)\right.\right.\)
\(\left.\left.+\lambda^2(1-\alpha)^2\delta_1^\top[\mathcal{K}_1^{-1}+\lambda(1-\alpha)]^{-2}\delta_1\right)\right.\)
\(\left.+\Delta_L^2\left(1+\frac{\mathrm{tr}(\mathcal{K}_1)}{\mathrm{tr}(\mathcal{K}_2)+\Delta_L^2}\right)\right]\ge 0.\quad (4.9.9)\)

Hence, the ridge-type R-estimator outperforms nEnetRE uniformly.

## 4.10 Summary

This chapter opened with the ANOVA model and described issues of robustness and partitioning. In particular, rank and LASSO can be effectively used to partition the treatments into subgroups, if the null hypothesis is rejected using a robust ANOVA. The variance of the treatments are instrumental in separating the different parameters into subgroups. If sparsity is suspected, then the parameters can be divided into two subgroups: “zero” and “non-zero”. To identify the sparse parameters, one of the subset selection penalties can be applied. After partitioning, the estimation can be carried out using one of several shrinkage estimators.

本章以 ANOVA 模型开篇，并描述了鲁棒性和分区问题。特别是，若使用鲁棒 ANOVA 拒绝原假设，则可有效地运用秩和 LASSO 将处理分组为子组。处理的方差对于将不同参数分离至子组起着关键作用。若怀疑存在稀疏性，则可将参数分为两个子组：“零”和“非零”。为识别稀疏参数，可应用一种子集选择惩罚。分区后，估计可利用多种收缩估计量之一进行。

A comparison of the different shrinkage estimators using ADL2-risk produced the following results:

- (i) Ridge regression as a shrinkage estimator dominates all other estimators uniformly.
- (ii) The multi-dimensional preliminary test estimator and the Stein–Saleh estimator have similar performance characteristics to the one-dimensional PTE and Stein–Saleh estimators. That is, ADL2-risk(\(\hat{\theta}_n^{SSR+}\)) \(\le\) ADL2-risk(\(\hat{\theta}_n^{SSR}\)) \(\le\) ADL2-risk(\(\hat{\theta}_n^{UR}\)) uniformly.
- (iii) None of the other estimators dominate over each other uniformly as seen in the previous chapter.

使用 ADL2 风险对不同收缩估计量进行比较，得出了以下结果：

- (i) 作为收缩估计量的岭回归始终优于所有其他估计量。
- (ii) 多维初步检验估计量和 Stein–Saleh 估计量与一维 PTE 和 Stein–Saleh 估计量具有相似的性能特征。即，ADL2 风险（\(\hat{\theta}_n^{SSR+}\)）≤ ADL2 风险（\(\hat{\theta}_n^{SSR}\)）≤ ADL2 风险（\(\hat{\theta}_n^{UR}\)）始终成立。
- (iii) 如前一章所示，其他估计量之间没有一种始终均优于另一种。

These results are similar in nature and consistent with the results presented in Chapter 3 where the single location problem was studied. Chapter 3 also addressed the simple linear model in detail. The next step is to solve a number of simple linear problems simultaneously and this is the subject of Chapter 5.

这些结果在性质上相似，并与第 3 章中研究的单一位置问题所呈现的结果一致。第 3 章还详细讨论了简单线性模型。下一步是同时求解多个简单线性问题，这是第 5 章的主题。

## 4.11 Problems

- 4.1. Derive ADV(\(\hat{\theta}_n^{UR}\)) to complete Theorem 4.1. (Hint: see Eq. (4.4.3)).
- 4.2. Show the steps needed to derive \(\mathcal{L}_{n_j} = \kappa_j T_{n_j}^2(0)/A_{n_j}^2\).
- 4.3. Qualitatively compare and contrast the preliminary test, Stein–Saleh, positive-rule Stein–Saleh and ridge R-estimators. Quantitatively compare them by plotting graphs of the ADL2-risk as a function of \(\Delta^2\). Compare your results with those given in Section 4.9.
- 4.4. Tabulate the ADRE values in Eq. (4.7.6) against \(\Delta^2\) based on \(\lambda^2 = 2 \ln(\text{tr}(\mathcal{K}_2))\).

- 4.1. 推导 ADV（\(\hat{\theta}_n^{UR}\)）以完成定理 4.1。（提示：参见公式 (4.4.3)）。
- 4.2. 展示推导 \(\mathcal{L}_{n_j} = \kappa_j T_{n_j}^2(0)/A_{n_j}^2\) 所需的步骤。
- 4.3. 定性地比较和对比初步检验、Stein–Saleh、正则 Stein–Saleh 和岭 R 估计量。通过绘制 ADL2 风险作为 \(\Delta^2$ 函数的图表来定量比较它们。将你的结果与第 4.9 节给出的结果进行比较。
- 4.4. 根据 \(\lambda^2 = 2 \ln(\text{tr}(\mathcal{K}_2))$ 将公式 (4.7.6) 中的 ADRE 值与 \(\Delta^2$ 进行表格对照。

### 4.5. (PROJECT) In this problem, the LASSO R-estimator will be used to partition the ANOVA table in Section 4.3.

### 4.5. （项目）本题将使用 LASSO R 估计量来分区第 4.3 节中的 ANOVA 表。

(a) Generate the data shown in Table 4.1 using the following R code.

```
set.seed(123)
n <- 6
fert1 <- rnorm(n)*20+150
set.seed(123)
n <- 14
fert2 <- rnorm(n)*30+60
set.seed(123)
n <- 8
fert3 <- rnorm(n)*170+175
set.seed(123)
n <- 11
fert4 <- rnorm(n)*150+30
set.seed(123)
n <- 12
fert5 <- rnorm(n)*200+10
set.seed(123)
n <- 9
fert6 <- rnorm(n)*300+0
```

(b) Enter the R code for the functions needed to compute the estimates as a function of \(\lambda\).

```
minimize.DnLassoV <- function(theta,lambda) {
  sum1 <- minimize.DnLasso(theta[1],fert1,lambda)
  sum2 <- minimize.DnLasso(theta[2],fert2,lambda)
  sum3 <- minimize.DnLasso(theta[3],fert3,lambda)
  sum4 <- minimize.DnLasso(theta[4],fert4,lambda)
  sum5 <- minimize.DnLasso(theta[5],fert5,lambda)
  sum6 <- minimize.DnLasso(theta[6],fert6,lambda)
  Dnsum <- sum1+sum2+sum3+sum4+sum5+sum6
  return(Dnsum)
}
minimize.DnLasso <- function(theta, y,lambda) {
  n <- length(y)
  abs_diff <- abs(y-theta)
  rank_abs_diff <- rank(abs_diff,
                        ties.method = "first")
  an_plus <- sqrt(3.)*((rank_abs_diff)/(n+1.))
  Dnsum <- sum(abs_diff*an_plus)/n
  penalty <- lambda * abs(theta)
  return(Dnsum+penalty)
}
```

(c) Run the optimizer and generate the plots.

```
p <- 6
lambda_grid = seq(0,1.5, length = 30)
penalty_mat_opt = matrix(0,nr = p,
nc = length(lambda_grid))
for(i in 1:length(lambda_grid)){
op.result <- optim(par= c(1,2,3,4,5,6),
fn = minimize.DnLassoV,
method = "BFGS",
lambda = lambda_grid[i])

penalty_mat_opt[,i] <- op.result$par
}

plot(lambda_grid,penalty_mat_opt[1,], type = "l",
col = 1, ylim = c(0,220), xlab = "lambda",
ylab = "thetaLASSOR")
points(lambda_grid, penalty_mat_opt[2,], type = "l",
col = 2, xlab = "lambda", ylab = "thetaLASSOR")
points(lambda_grid,penalty_mat_opt[3,], type = "l",
col = 3, xlab = "lambda", ylab = "thetaLASSOR")
points(lambda_grid,penalty_mat_opt[4,], type = "l",
col = 4, xlab = "lambda", ylab = "thetaLASSOR")
points(lambda_grid, penalty_mat_opt[5,], type = "l",
col = 5, xlab = "lambda", ylab = "thetaLASSOR")
points(lambda_grid,penalty_mat_opt[6,], type = "l",
col = 6, xlab = "lambda", ylab = "thetaLASSOR")
```

(d) Identify the “non-zero” and “zero” subgroups.

(d) 识别“非零”和“零”子组。

### 4.6. (PROJECT) Assuming that the previous problem has been completed, it is rather straightforward to run ANOVA in R, which is the purpose of this problem. Run the following R code to obtain the comparison of standard ANOVA using aov() and the robust ANOVA using oneway.rfit().

```
yield <- c(fert1,fert2,fert3,fert4,fert5,fert6)
fertilizer <- c(rep("fert1",6),rep("fert2",14),
rep("fert3",8),rep("fert4",11),
rep("fert5",12),rep("fert6",9))

anova.mod <- aov(yield ~ fertilizer)
summary(anova.mod)
boxplot(yield ~ fertilizer)
library(Rfit)
anovafit<- oneway.rfit(yield,fertilizer)
qqnorm(rstudent(anovafit$fit))
oneway.rfit(yield,fertilizer)
```

### 4.6. （项目）假设前一题已完成，在 R 中运行 ANOVA 相当简单，这也是本题的目的。运行以下 R 代码，以使用 aov() 获取标准 ANOVA 与使用 oneway.rfit() 的鲁棒 ANOVA 的比较。

Comment on the results based on an examination of the boxplot , Q-Q plot and the p-values of the two approaches.

根据对箱线图、Q-Q 图和两种方法的 p 值的检查，对结果进行评论。

### 4.7. (PROJECT) In this problem, we will compare the LASSO trace of fertilizer 3 of the ANOVA table using $\mathcal{L}_{n_\delta}$, and the positive-rule Stein–Saleh estimator. The code below assumes that the code in Problem 4.6 has been executed.

### 4.7. （项目）本题将使用 $\mathcal{L}_{n_\delta}$ 与正则 Stein–Saleh 估计量比较 ANOVA 表中肥料 3 的 LASSO 跟踪。以下代码假设已执行问题 4.6 中的代码。

- (a) Compute the unrestricted estimates using the following R code.

```
op.result <- optim(par= c(1,2,3,4,5,6),
                   fn = minimize.DnLassoV,
                   method = "BFGS",
                   lambda = 0.0)
thetaUR <- op.result$par
```

- (a) 使用以下 R 代码计算无限制估计量。

- (b) Use the following codes to obtain $T_n(\theta)$ and $A_n^2$.

```
Tn <- function(theta, y ) {
  n <- length(y)
  diff <- y-theta
  abs_diff <- abs(diff)
  sgn_diff <- sign(diff)
  rank_abs_diff <- rank(abs_diff,
                        ties.method = "first")
  an_plus <- sqrt(3.)*(rank_abs_diff)/(n+1.)
  Tnsum <- sum(sgn_diff*an_plus)/sqrt(n)
  return(Tnsum)
}
```

```
An2 <- function(theta, y ) {
  n <- length(y)
  diff <- y-theta
  abs_diff <- abs(diff)
  sgn_diff <- sign(diff)
  rank_abs_diff <- rank(abs_diff,
                        ties.method = "first")
  an_plus <- sqrt(3.)*(rank_abs_diff)/(n+1.)
  An2sum <- sum((an_plus)^-2)/(n)
```

- (b) 使用以下代码获取 $T_n(\theta)$ 和 $A_n^2$。

