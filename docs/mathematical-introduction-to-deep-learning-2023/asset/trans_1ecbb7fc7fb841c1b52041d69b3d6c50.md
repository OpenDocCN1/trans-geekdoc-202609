
## 6.3.3 带动量的 GD 优化的误差分析

在本小节中，我们将在下文第 6.3.3.2 节中提供关于二次目标函数（参见第 6.3.3.2 节中的命题 6.3.11 以获取精确陈述）的一类情况下带动量的 GD 优化方法的误差分析。在这种特定情况下，我们还在下文第 6.3.3.3 节中提供了普通 GD 优化方法与带动量 GD 优化方法收敛速度的比较。特别是，我们大致证明了，在考虑的这类二次目标函数的情况下，带动量 GD 优化方法优于普通 GD 优化方法；有关精确陈述，请参见第 6.3.3.3 节中的推论 6.3.13。为了比较普通 GD 优化方法与带动量 GD 优化方法，我们采用了一种针对所考虑的这类二次目标函数的普通 GD 优化方法的精细化误差分析。这种精细化误差分析是下一节（下文第 6.3.3.1 节）的主题。

在文献中，例如可以在 [48, 第 7.1 节] 和 [337] 中找到关于带动量 GD 优化方法的类似误差分析。

### 6.3.3.1 二次目标函数情况下 GD 优化的误差分析

**引理 6.3.7**（二次目标函数情况下 GD 优化方法的误差分析）。设 $d \in \mathbb{N}$，$\xi \in \mathbb{R}^d$，$v = (v_1, \dots, v_d) \in \mathbb{R}^d$，$\kappa, K, \lambda_1, \lambda_2, \dots, \lambda_d \in (0, \infty)$ 满足 $\kappa = \min\{\lambda_1, \lambda_2, \dots, \lambda_d\}$ 且 $K = \max\{\lambda_1, \lambda_2, \dots, \lambda_d\}$，设 $\mathcal{L}: \mathbb{R}^d \to \mathbb{R}$ 满足对于所有 $\theta = (\theta_1, \dots, \theta_d) \in \mathbb{R}^d$ 有

$$
\mathcal{L}(\theta) = \frac{1}{2} \left[ \sum_{i=1}^d \lambda_i |\theta_i - v_i|^2 \right], \quad (6.223)
$$

且设 $\Theta: \mathbb{N}_0 \to \mathbb{R}^d$ 满足对于所有 $n \in \mathbb{N}$ 有

$$
\Theta_0 = \xi \quad \text{且} \quad \Theta_n = \Theta_{n-1} - \frac{2}{(\kappa+K)} (\nabla \mathcal{L})(\Theta_{n-1}). \quad (6.224)
$$

则对于所有 $n \in \mathbb{N}_0$，有

$$
\|\Theta_n - v\|_2 \leq \left[ \frac{K-\kappa}{K+\kappa} \right]^n \|\xi - v\|_2 \quad (6.225)
$$

（参见定义 3.3.4）。

**引理 6.3.7 的证明。** 在整个证明过程中，设 $\Theta^{(1)}, \Theta^{(2)}, \dots, \Theta^{(d)}: \mathbb{N}_0 \to \mathbb{R}$ 满足对于所有 $n \in \mathbb{N}_0$ 有 $\Theta_n = (\Theta_n^{(1)}, \Theta_n^{(2)}, \dots, \Theta_n^{(d)})$。注意，(6.223) 意味着对于所有 $\theta = (\theta_1, \theta_2, \dots, \theta_d) \in \mathbb{R}^d$，$i \in \{1, 2, \dots, d\}$，有

$$
\left(\frac{\partial \mathcal{L}}{\partial \theta_i}\right)(\theta) = \lambda_i(\theta_i - v_i). \quad (6.226)
$$

将此与 (6.224) 结合，确保对于所有 $n \in \mathbb{N}$，$i \in \{1, 2, \dots, d\}$，有

$$
\begin{aligned}
\Theta_n^{(i)} - v_i &= \Theta_{n-1}^{(i)} - \frac{2}{(\kappa+K)} \left(\frac{\partial \mathcal{L}}{\partial v_i}\right)_{n-1}(\Theta_{n-1}) - v_i \\
&= \Theta_{n-1}^{(i)} - v_i - \frac{2}{(\kappa+K)} \left[\lambda_i(\Theta_{n-1}^{(i)} - v_i)\right] \\
&= \left(1 - \frac{2\lambda_i}{(\kappa+K)}\right)(\Theta_{n-1}^{(i)} - v_i). \quad (6.227)
\end{aligned}
$$

因此，我们得到对于所有 $n \in \mathbb{N}$，有

$$
\begin{aligned}
\|\Theta_n - v\|_2^2 &= \sum_{i=1}^d \|\Theta_n^{(i)} - v_i\|^2 \\
&= \sum_{i=1}^d \left[1 - \frac{2\lambda_i}{(\kappa+K)}\right]^2 \left[\|\Theta_{n-1}^{(i)} - v_i\|^2\right] \\
&\leq \left[\max\left\{\left[1 - \frac{2\lambda_1}{(\kappa+K)}\right]^2, \dots, \left[1 - \frac{2\lambda_d}{(\kappa+K)}\right]^2\right\}\right] \left[\sum_{i=1}^d \|\Theta_{n-1}^{(i)} - v_i\|^2\right] \\
&= \left[\max\left\{\left|1 - \frac{2\lambda_1}{(\kappa+K)}\right|, \dots, \left|1 - \frac{2\lambda_d}{(\kappa+K)}\right|\right\}\right]^2 \|\Theta_{n-1} - v\|_2^2 \quad (6.228)
\end{aligned}
$$

（参见定义 3.3.4）。此外，注意对于所有 $i \in \{1, 2, \dots, d\}$ 有 $\lambda_i \geq \kappa$ 这一事实，意味着对于所有 $i \in \{1, 2, \dots, d\}$ 有

$$
1 - \frac{2\lambda_i}{(\kappa+K)} \leq 1 - \frac{2\kappa}{(\kappa+K)} = \frac{\kappa+K-2\kappa}{\kappa+K} = \frac{K-\kappa}{\kappa+K} \geq 0. \quad (6.229)
$$

另外，观察对于所有 $i \in \{1, 2, \dots, d\}$ 有 $\lambda_i \leq K$ 这一事实，意味着对于所有 $i \in \{1, 2, \dots, d\}$ 有

$$
1 - \frac{2\lambda_i}{(\kappa+K)} \geq 1 - \frac{2K}{(\kappa+K)} = \frac{\kappa+K-2K}{\kappa+K} = -\left[\frac{K-\kappa}{\kappa+K}\right] \leq 0. \quad (6.230)
$$

结合这一点和 (6.229)，确保对于所有 $i \in \{1, 2, \dots, d\}$ 有

$$
\left|1 - \frac{2\lambda_i}{\kappa+K}\right| \leq \frac{K-\kappa}{\kappa+K}. \quad (6.231)
$$

将此与 (6.228) 结合，证明了对于所有 $n \in \mathbb{N}$ 有

$$
\begin{aligned}
\|\Theta_n - v\|_2 &\leq \left[\max\left\{\left|1 - \frac{2\lambda_1}{\kappa+K}\right|, \dots, \left|1 - \frac{2\lambda_d}{\kappa+K}\right|\right\}\right] \|\Theta_{n-1} - v\|_2 \\
&\leq \left[\frac{K-\kappa}{\kappa+K}\right] \|\Theta_{n-1} - v\|_2. \quad (6.232)
\end{aligned}
$$

因此，归纳法确立了对于所有 $n \in \mathbb{N}_0$ 有

$$
\|\Theta_n - v\|_2 \leq \left[\frac{K-\kappa}{\kappa+K}\right]^n \|\Theta_0 - v\|_2 = \left[\frac{K-\kappa}{\kappa+K}\right]^n \|\xi - v\|_2. \quad (6.233)
$$

至此，引理 6.3.7 的证明完成。 $\square$

上述引理 6.3.7 大致建立了目标函数 (6.223) 情况下 GD 优化方法的收敛速率 $\frac{K-\kappa}{K+\kappa}$（有关精确陈述请参见上文 (6.225)）。下一个结果，下文引理 6.3.8，基本上在引理 6.3.7 的情况下证明了这种收敛速率无法通过改变学习率的选择而得到改善。

**引理 6.3.8**（二次目标函数情况下 GD 收敛速率的下界）。设 $d \in \mathbb{N}$，$\xi = (\xi_1, \xi_2, \ldots, \xi_d) \in \mathbb{R}^d$，$v = (v_1, v_2, \ldots, v_d) \in \mathbb{R}^d$，$\gamma, \kappa, K, \lambda_1, \lambda_2, \ldots, \lambda_d \in (0, \infty)$ 满足 $\kappa = \min\{\lambda_1, \lambda_2, \ldots, \lambda_d\}$ 且 $K = \max\{\lambda_1, \lambda_2, \ldots, \lambda_d\}$，设 $\mathcal{L}: \mathbb{R}^d \rightarrow \mathbb{R}$ 满足对于所有 $\theta = (\theta_1, \theta_2, \ldots, \theta_d) \in \mathbb{R}^d$ 有

$$
\mathcal{L}(\theta) = \frac{1}{2} \left[ \sum_{i=1}^d \lambda_i |\theta_i - v_i|^2 \right], \quad (6.234)
$$

且设 $\Theta: \mathbb{N}_0 \rightarrow \mathbb{R}^d$ 满足对于所有 $n \in \mathbb{N}$ 有

$$
\Theta_0 = \xi \quad \text{且} \quad \Theta_n = \Theta_{n-1} - \gamma \left( \nabla \mathcal{L} \right)(\Theta_{n-1}). \quad (6.235)
$$

则对于所有 $n \in \mathbb{N}_0$，有

$$
\begin{aligned}
\| \Theta_n - v \|_2 &\geq \left[ \max\{\gamma K - 1, 1 - \gamma \kappa\} \right]^n \left[ \min\{ |\xi_1 - v_1|, \ldots, |\xi_d - v_d| \} \right] \\
&\geq \left[ \frac{K-\kappa}{K+\kappa} \right]^n \left[ \min\{ |\xi_1 - v_1|, \ldots, |\xi_d - v_d| \} \right] \quad (6.236)
\end{aligned}
$$

（参见定义 3.3.4）。

**引理 6.3.8 的证明。** 在整个证明过程中，设 $\Theta^{(1)}, \Theta^{(2)}, \ldots, \Theta^{(d)}: \mathbb{N}_0 \rightarrow \mathbb{R}$ 满足对于所有 $n \in \mathbb{N}_0$ 有 $\Theta_n = (\Theta_n^{(1)}, \Theta_n^{(2)}, \ldots, \Theta_n^{(d)})$，且设 $\iota, \mathcal{I} \in \{1, 2, \ldots, d\}$ 满足 $\lambda_{\iota} = \kappa$ 且 $\lambda_{\mathcal{I}} = K$。注意，(6.234) 意味着对于所有 $\theta = (\theta_1, \theta_2, \ldots, \theta_d) \in \mathbb{R}^d$，$i \in \{1, 2, \ldots, d\}$，有

$$
\left( \frac{\partial \mathcal{L}}{\partial \theta_i} \right)(\theta) = \lambda_i (\theta_i - v_i). \quad (6.237)
$$

将此与 (6.235) 结合，意味着对于所有 $n \in \mathbb{N}$，$i \in \{1, 2, \ldots, d\}$，有

$$
\begin{aligned}
\Theta_n^{(i)} - v_i &= \Theta_{n-1}^{(i)} - \gamma \left( \frac{\partial \mathcal{L}}{\partial \theta_i} \right)(\Theta_{n-1}) - v_i \\
&= \Theta_{n-1}^{(i)} - v_i - \gamma \lambda_i (\Theta_{n-1}^{(i)} - v_i) \\
&= (1 - \gamma \lambda_i)(\Theta_{n-1}^{(i)} - v_i). \quad (6.238)
\end{aligned}
$$

因此，归纳法证明了对于所有 $n \in \mathbb{N}_0$，$i \in \{1, 2, \ldots, d\}$，有

$$
\Theta_n^{(i)} - v_i = (1 - \gamma \lambda_i)^n (\Theta_0^{(i)} - v_i) = (1 - \gamma \lambda_i)^n (\xi_i - v_i). \quad (6.239)
$$

