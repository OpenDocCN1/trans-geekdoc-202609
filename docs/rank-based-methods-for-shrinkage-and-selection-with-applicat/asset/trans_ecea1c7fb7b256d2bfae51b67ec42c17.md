


ADL_2\text{-risk}(\hat{\theta}_n^{*\text{ridge}}(\lambda)) = \eta^2 \left( 1 + \frac{\tilde{\varkappa}_n^2}{Q} \frac{1}{(1+\lambda)^2} (1 + \lambda^2 \Delta^2) \right).

- 3.6. 推导截距参数 $\hat{\theta}_{n,\text{SR}}^{\text{PTR}}$ 的 ADL$_2$-风险。
- 3.7. 推导截距参数 $\hat{\theta}_{n,\text{SR}}^{*\text{ridge}}$ 的 ADL$_2$-风险。
- 3.8. 考虑表 3.5 和图 3.5 中所示的结果。注意位置参数和截距参数结果的相似性，比较问题 3.4、3.5、3.6 和 3.7 中的不同估计量。哪个是最好的，哪个是三个中最差的？

- 3.9. (PROJECT) 位置参数 $\theta$ 的离散函数给出为

  $D_n(\Theta) = \sum_{i=1}^n |y_i - \theta| \alpha_n^+(R_{n_i}^+(\Theta)).$

  估计量给出为

  \(\hat{\theta}_n^{\text{UR}} = \underset{\theta \in \mathbb{R}}{\text{argmin}}\{D_n(\Theta)\}.\)

- (a) 使用以下 R 代码生成 $n = 64$ 的数据集：

  ```r
  set.seed(123)
  #Pick 64 random points
  n <- 64
  y <- rnorm(n)+0.97194 #adjust to make median = 1
  ```

- (b) 使用以下无限制秩估计量来求估计值。它使用位置参数的离散函数。基于代码结果，$\hat{\theta}_n^{\text{UR}}$ 是多少？

  ```r
  minimize.Dn <- function(theta, y) {
  n <- length(y)
  abs_diff <- abs(y-theta)
  rank_abs_diff <- rank(abs_diff,
  ties.method = "first")
  an_plus <- sqrt(3.0)*(rank_abs_diff)/(n+1.)
  Dnsum <- sum(abs_diff*an_plus)/n
  return(Dnsum)
  }
  
  op.result <- optim(2.0,
  fn = minimize.Dn,
  method = "BFGS",
  y = y)

  thetaUR <- op.result$par
  thetaUR
  ```

### 3.10. (PROJECT) 函数 \( T_n(\theta) \) 被描述用于对 \( \mathcal{H}_o : \theta = 0 \) 与 \( \mathcal{H}_A : \theta \neq 0 \) 进行梯度检验。检验统计量是 \( T_n(0)/A_n \)。针对上一问题的数据集计算该统计量，并在显著性水平 0.05 下进行假设检验。以下 R 代码可用于计算检验统计量：

```r
Tn <- function(theta, y ) {
  n <- length(y)
  diff <- y-theta
  abs_diff <- abs(diff)
  sgn_diff <- sign(diff)
  rank_abs_diff <- rank(abs_diff,
           ties.method = "first")
  an_plus <- sqrt(3.) * rank_abs_diff / (n+1.)
  Tnsum <- sum(sgn_diff*an_plus)/sqrt(n)
  return(Tnsum)
}
```

```r
# Obtain Tn(0)
Tn0 <- Tn(0.0, y = y)
Tn0
```

修改上述 R 代码以获取 \( A_n^2 = n^{-1} \sum_{i=1}^n [a_n^+(i)]^2 \)。计算检验统计量并决定是否拒绝原假设。

### 3.11. (PROJECT) 在本题中，目标是为位置参数实现岭回归、LASSO 和弹性网 R-估计量，并使用问题 3.9(a) 中给出的相同数据集绘制 \( \lambda \) 的迹线图。

```r
set.seed(123)
#Pick 64 random points
n <- 64
y <- rnorm(n)+0.97194 #adjust to make median = 1
```

- (a) 使用以下 R 代码实现岭惩罚函数，并绘制 \( \lambda \) 函数的岭迹线图。

```r
minimize.penaltyR <- function(theta, y, lambda ) {
  n <- length(y)
  abs_diff <- abs(y-theta)
  rank_abs_diff <- rank(abs_diff,
           ties.method = "first")
  an_plus <- sqrt(3.) * rank_abs_diff / (n+1.)
  Dnsum <- sum(abs_diff*an_plus)
  eta <- 0.8
#ridge penalty
penalty <- sqrt(n)*eta*lambda* theta*theta/2
return(Dnsum + penalty)
}
p <- 1
lambda_grid = seq(0,20, length = 50)
penalty_mat_opt = matrix(0,nr = p,
nc = length(lambda_grid))
for(i in 1:length(lambda_grid)){
  op.result <- optim(0.0,
                     fn = minimize.penaltyR,
                     method = "BFGS",
                     y = y,
                     lambda = lambda_grid[i])
  penalty_mat_opt[,i] <- op.result$par
}
plot(lambda_grid,penalty_mat_opt[1,],
     type = "l", col = 1, ylim = c(-1,1),
     xlab = "lambda", ylab = "thetapentaltyR")
```

- (b) 替换惩罚函数以实现 LASSO，并按如下方式重新运行 R 代码：

```r
#ridge penalty
#penalty <- sqrt(n)*eta*lambda* theta*theta/2
#LASSO penalty
penalty <- lambda * abs(theta)*eta*sqrt(n)
```

- (c) 修改惩罚函数以实现弹性网，并按如下方式重新运行 R 代码：

```r
#ridge penalty
#penalty <- sqrt(n)*eta*lambda* theta*theta/2
#LASSO penalty
#penalty <- lambda * abs(theta)*eta*sqrt(n)
#Enet penalty
alpha = 1.0 #adjust alpha from 0 to 1 manually
penalty <- lambda *alpha*abs(theta)*eta*sqrt(n)+
eta*sqrt(n)*lambda * ((1-alpha)* theta*theta/2)
```

### 3.12. (PROJECT) 使用之前使用的相同数据集实现 Saleh 类型估计量。

```r
set.seed(123)
#Pick 64 random points
n <- 64
y <- rnorm(n)+0.97194 #adjust to make median = 1
```

- (a) 首先运行以下硬阈值估计器的代码。

```r
pts <- 100
eta <- 0.8
n = 64
thetaUR <- 1.0
Ln <- n*thetaUR^2/eta^2
thetaShrink <- rep(0,pts)
lambda <- rep(0,pts)
#HTR
for (lambda in 0:pts) {
  lambda2 <- lambda/5
  thetaShrink[lambda+1] <- thetaUR*
    ( Ln > lambda2*lambda2)
  lambda[lambda+1] <- lambda2
}
plot(lambda,thetaShrink, ylab="thetaHTR",
     xlab="lambda",ylim=c(-1,1),
     col="black",type="l")
points(c(-0.1,20.1),c(-0.0,-0.0),
     col="gray",type="l")
```

- (b) 接下来，运行生成 Saleh R-估计量迹线的 R 代码。

```r
#SR
for (lambda in 0:pts) {
  lambda2 <- lambda/5
  thetaShrink[lambda+1] <- thetaUR*
    (1- lambda2/sqrt(Ln) )
  lambda[lambda+1] <- lambda2
}
plot(lambda,thetaShrink, ylab="thetaSR",
     xlab="lambda",ylim=c(-1,1),
     col="black",type="l")
points(c(-0.1,20.1),c(-0.0,-0.0),
     col="gray",type="l")
```

- (c) 最后，运行生成正则 Saleh 类型 R-估计量迹线的 R 代码。

```r
# SR+
for (lambda in 0:pts) {
  lambda2 <- lambda/5
  thetaShrink[lambda+1] <- thetaUR*
    (1- lambda2/sqrt(Ln) )*
    ( Ln > lambda2*lambda2)
  lambda[lambda+1] <- lambda2
}
plot(lambda,thetaShrink, ylab="thetaSR+",
xlab="lambda",ylim=c(-1,1),
col="black",type="l")
points(c(-0.1,20.1),c(-0.05,-0.05),
col="gray",type="l")
```

- (d) 对问题 3.9 和 3.10 中获得的不同迹线进行评论，并将其与图 3.1 的结果进行比较。

## 4 方差分析（ANOVA）

### 4.1 引言

属于一般线性假设类的一个重要模型是方差分析（ANOVA）模型。本章中，我们以最简单形式考虑 ANOVA 模型，即，我们从 $p$ 个维度中收集 $p$ 个不同样本量的样本 $n_1, \dots, n_p$，

$F(y_{ij} - \theta_i), \quad j = 1, \dots, n_i, \quad i = 1, \dots, p$

其中 $\theta = (\theta_1, \dots, \theta_p)^\top$ 是未知的 $p$ 个处理效应向量。在传统方法中，检验 $p$ 个处理相等的假设，即

$\theta_1 = \dots = \theta_p = \theta_0 \quad (\text{unknown}).$

在我们的情况中，我们试图发现一个包含相对于补集的显著处理的处理子集。

在本章中，我们考虑 (i) 无限制 R-估计量，以及 (ii) 受限制 R-估计量，以及一些惩罚估计量，即 (iii) 子集选择规则，(iv) LASSO 类型，(v) aLASSO 类型，(vi) 岭类型，(vii) 弹性网类型估计器，连同传统的缩减估计器，如 (viii) 初步检验，以及 (ix) Stein–Saleh 估计器，在非参数设置中研究其渐近分布 L2-风险特性。

### 4.2 模型、估计与检验

考虑 ANOVA 模型

$$
Y = B\theta + \varepsilon, \quad (4.2.1)
$$

其中
$$
Y = (y_{11}, \dots, y_{1n_1}, y_{21}, \dots, y_{2n_2}, \dots, y_{p1}, \dots, y_{pn_p})^\top,
$$

$$
\varepsilon = (\varepsilon_{11}, \dots, \varepsilon_{1n_1}, \varepsilon_{21}, \dots, \varepsilon_{2n_2}, \dots, \varepsilon_{p1}, \dots, \varepsilon_{pn_p})^\top,
$$

$$
B = \text{block-diagonal vectors}(\mathbf{1}_{n_1}, \dots, \mathbf{1}_{n_p}), \mathbf{1}_{n_i} = (1, \dots, 1) - \text{an } n_i \text{ tuple of 1s},
$$

$$
n = n_1 + \dots + n_p
$$

$$
\mathcal{K}_n = \text{Diag}(\frac{n_1}{n}, \dots, \frac{n_p}{n}).
$$

我们假设

$$
F(\varepsilon) = \prod_{l=1}^p \prod_{j=1}^{n_l} F_0(y_{ij} - \theta_i), \quad \theta = (\theta_1, \dots, \theta_p)^\top,
$$

其中

- (i) \( F_0 \) 属于绝对连续、对称累积分布函数（c.d.f.）的类，具有绝对连续概率密度函数（p.d.f.）、\( f_0 \)，且具有有限 Fisher 信息量 \( I(f_0) \)。
- (ii) \( I(f_0) = \int_{-\infty}^{\infty} \left\{ -\frac{f_0'(x)}{f_0(x)} \right\}^2 f_0(x) \mathrm{d}x < \infty. \)
- (iii) \( \lim_{n \to \infty} \frac{n_i}{n} = \kappa_i \ (0 < \kappa_i < 1), \quad \mathcal{K} = \text{Diag}(\kappa_1, \dots, \kappa_p) = \lim_{n \to \infty} \mathcal{K}_n. \)
- (iv) 得分函数 \( a_n(i) \) 由一种技术 \( \phi(u), 0 < u < 1 \) 生成，该技术是非恒定、非递减且可平方积分的，其中

  \( \phi^+(u) = \phi \left( \frac{1+u}{2} \right), \quad \phi(u) + \phi(1-u) = 0. \)

  然后，\( a_{n_i}^+(i) = \mathbb{E}[\phi^+(U_{n_i:i})] \text{ 或 } \phi \left( \frac{i}{n_i+1} \right), 1 \le i \le n_i \text{ 且 } 0 < U_{n_i,1} \le \dots \le U_{n_i,n_i} < 1 \) 是来自 \( U(0, 1) \) 大小为 \( n_i \) 的样本的序统计量。

### 4.3 多重位置模型概述

本章的设置相当于求解若干相关的位置问题。位置估计量向量可用于假设检验，如同在 ANOVA 中一样，也可用于缩减估计，如本章后面所述。此处的结果是第 3 章所涵盖材料的扩展。

