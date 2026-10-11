
\mathbb{P}\left(\left|\sum_{n=1}^N\left(X_n - \mathbb{E}[X_n]\right)\right| \geq \varepsilon\right) &= \mathbb{P}\left(\left|\sum_{n=1}^N\left(X_n - \mathbb{E}[X_n]\right)\right|^2 \geq \varepsilon^2\right) \\
&\leq \frac{\mathbb{E}\left[\left|\sum_{n=1}^N\left(X_n - \mathbb{E}[X_n]\right)\right|^2\right]}{\varepsilon^2} .
\end{align*} \tag{12.12}

$$
此外，注意到 $X_n: \Omega \rightarrow [a_n, b_n]$，$n \in \{1, 2, \ldots, N\}$，是独立变量这一假设以及引理 12.1.5 表明
$$

\begin{align*}
\mathbb{E}\left[\left|\sum_{n=1}^N\left(X_n - \mathbb{E}[X_n]\right)\right|^2\right] &= \sum_{n, m=1}^N \mathbb{E}\left[\left(X_n - \mathbb{E}[X_n]\right)\left(X_m - \mathbb{E}[X_m]\right)\right] \\
&= \sum_{n=1}^N \mathbb{E}\left[\left(X_n - \mathbb{E}[X_n]\right)^2\right] \leq \frac{\sum_{n=1}^N\left(b_n - a_n\right)^2}{4} .
\end{align*} \tag{12.13}
$$

将此与 (12.12) 结合，建立
$$ \mathbb{P}\left(\left|\sum_{n=1}^{N}\left(X_{n}-\mathbb{E}\left[X_{n}\right]\right)\right|\geq \varepsilon\right) \leq \frac{\sum_{n=1}^{N}\left(b_{n}-a_{n}\right)^{2}}{4 \varepsilon^{2}} \quad (12.14) $$
至此，引理 12.1.6 的证明完成。 $\square$

### 12.1.3 矩生成函数

**定义 12.1.7 (矩生成函数)。** 设 $(\Omega, \mathcal{F}, \mathbb{P})$ 是一个概率空间，且设 $X: \Omega \rightarrow \mathbb{R}$ 是一个随机变量。则我们用 $\mathbb{M}_{X, \mathbb{P}}: \mathbb{R} \rightarrow[0, \infty]$（记作 $\mathbb{M}_{X}: \mathbb{R} \rightarrow[0, \infty]$）表示满足对于所有 $t \in \mathbb{R}$ 有
$$ \mathbb{M}_{X, \mathbb{P}}(t)=\mathbb{E}\left[e^{t X}\right] \quad (12.15) $$
的函数，并称 $\mathbb{M}_{X, \mathbb{P}}$ 为 $X$ 关于 $\mathbb{P}$ 的矩生成函数（称 $\mathbb{M}_{X, \mathbb{P}}$ 为 $X$ 的矩生成函数）。

#### 12.1.3.1 独立随机变量和的矩生成函数

**引理 12.1.8.** 设 $(\Omega, \mathcal{F}, \mathbb{P})$ 是一个概率空间，设 $t \in \mathbb{R}$，$N \in \mathbb{N}$，且设 $X_{n}: \Omega \rightarrow \mathbb{R}$，$n \in\{1,2, \ldots, N\}$，是独立的随机变量。则
$$ \mathbb{M}_{\sum_{n=1}^{N} X_{n}}(t)=\prod_{n=1}^{N} \mathbb{M}_{X_{n}}(t) . \quad (12.16) $$

*引理 12.1.8 的证明。* 注意，富比尼定理（Fubini's theorem）保证了对于所有 $t \in \mathbb{R}$ 有
$$
\begin{aligned}
\mathbb{M}_{\sum_{n=1}^{N} X_{n}}(t) &= \mathbb{E}\left[e^{t\left(\sum_{n=1}^{N} X_{n}\right)}\right] = \mathbb{E}\left[\prod_{n=1}^{N} e^{t X_{n}}\right] = \prod_{n=1}^{N} \mathbb{E}\left[e^{t X_{n}}\right] \\
&= \prod_{n=1}^{N} \mathbb{M}_{X_{n}}(t) .
\end{aligned} \quad (12.17)
$$
至此，引理 12.1.8 的证明完成。 $\square$

### 12.1.4 切尔诺夫界（Chernoff bounds）

#### 12.1.4.1 越过障碍的概率

**命题 12.1.9.** 设 $(\Omega, \mathcal{F}, \mathbb{P})$ 是一个概率空间，设 $X: \Omega \rightarrow \mathbb{R}$ 是一个随机变量，且设 $\varepsilon \in \mathbb{R}$。则
$$ \mathbb{P}(X \geq \varepsilon) \leq \inf _{\lambda \in[0, \infty)}\left(e^{-\lambda \varepsilon} \mathbb{E}\left[e^{\lambda X}\right]\right)=\inf _{\lambda \in[0, \infty)}\left(e^{-\lambda \varepsilon} \mathbb{M}_{X}(\lambda)\right) . \quad (12.18) $$

#### 12.1.4.2 低于障碍的概率

*命题 12.1.9 的证明.* 注意，引理 12.1.1 确保对于所有 $\lambda \in [0,\infty)$，有
$$
\mathbb{P}(X \geq \varepsilon) \leq \mathbb{P}(\lambda X \geq \lambda\varepsilon) = \mathbb{P}(\exp(\lambda X) \geq \exp(\lambda\varepsilon)) \leq \frac{\mathbb{E}[\exp(\lambda X)]}{\exp(\lambda\varepsilon)} = e^{-\lambda\varepsilon}\mathbb{E}[e^{\lambda X}].
$$
(12.19)
命题 12.1.9 的证明至此完成。

**推论 12.1.10.** 设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为概率空间，设 $X: \Omega \rightarrow \mathbb{R}$ 为随机变量，且 $c, \varepsilon \in \mathbb{R}$。则
$$
\mathbb{P}(X \geq c + \varepsilon) \leq \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{X-c}(\lambda)).
$$
(12.20)

*推论 12.1.10 的证明.* 在本证明中，设 $Y: \Omega \rightarrow \mathbb{R}$ 满足
$$
Y = X - c.
$$
(12.21)
注意到命题 12.1.9 和 (12.21) 确保
$$
\mathbb{P}(X - c \geq \varepsilon) = \mathbb{P}(Y \geq \varepsilon) \leq \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{Y}(\lambda)) = \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{X-c}(\lambda)).
$$
(12.22)
推论 12.1.10 的证明至此完成。

**推论 12.1.11.** 设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为概率空间，设 $X: \Omega \rightarrow \mathbb{R}$ 为随机变量且 $\mathbb{E}[|X|] < \infty$，并设 $\varepsilon \in \mathbb{R}$。则
$$
\mathbb{P}(X \geq \mathbb{E}[X] + \varepsilon) \leq \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{X-\mathbb{E}[X]}(\lambda)).
$$
(12.23)

*推论 12.1.11 的证明.* 注意到推论 12.1.10（在推论 12.1.10 的记号中取 $c \triangleq \mathbb{E}[X]$）建立了 (12.23)。推论 12.1.11 的证明至此完成。

#### 12.1.4.2 低于障碍的概率

**推论 12.1.12.** 设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为概率空间，设 $X: \Omega \rightarrow \mathbb{R}$ 为随机变量，且 $c, \varepsilon \in \mathbb{R}$。则
$$
\mathbb{P}(X \leq c - \varepsilon) \leq \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{c-X}(\lambda)).
$$
(12.24)

*推论 12.1.12 的证明.* 在本证明中，设 $\mathfrak{c} \in \mathbb{R}$ 满足 $\mathfrak{c} = -c$，并设 $\mathfrak{X}: \Omega \rightarrow \mathbb{R}$ 满足
$$
\mathfrak{X} = -X.
$$
(12.25)
注意到推论 12.1.10 和 (12.25) 确保
$$
\begin{aligned}
\mathbb{P}(X \leq c - \varepsilon) &= \mathbb{P}(-X \geq -c + \varepsilon) = \mathbb{P}(\mathfrak{X} \geq \mathfrak{c} + \varepsilon) \\
&\leq \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{\mathfrak{X}-\mathfrak{c}}(\lambda)) \\
&= \inf_{\lambda \in [0,\infty)} (e^{-\lambda\varepsilon}\mathbb{M}_{\mathfrak{c}-X}(\lambda)).
\end{aligned}
$$
(12.26)
推论 12.1.12 的证明至此完成。

#### 12.1.4.3 独立随机变量之和

**推论 12.1.13.** *设* $(\Omega, \mathcal{F}, \mathbb{P})$ *为概率空间，设* $\varepsilon \in \mathbb{R}$，$N \in \mathbb{N}$，*且设* $X_n \colon \Omega \rightarrow \mathbb{R}$，$n \in \{1, 2, \dots, N\}$，*为独立随机变量，满足* $\max_{n \in \{1,2,\dots,N\}} \mathbb{E}[|X_n|] < \infty$。*则*
$$
\mathbb{P}\left[\left|\sum_{n=1}^N (X_n - \mathbb{E}[X_n])\right| \geq \varepsilon\right] \leq \inf_{\lambda \in [0,\infty)}\left(e^{-\lambda \varepsilon} \prod_{n=1}^N \mathbb{M}_{X_n - \mathbb{E}[X_n]}(\lambda)\right).
$$
(12.27)

*推论 12.1.13 的证明.* *在本证明中，设* $Y_n \colon \Omega \rightarrow \mathbb{R}$，$n \in \{1,2,\dots,N\}$，*满足对于所有* $n \in \{1,2,\dots,N\}$，有
$$
Y_n = X_n - \mathbb{E}[X_n].
$$
(12.28)
注意到命题 12.1.9、引理 12.1.8 和 (12.28) 确保
$$
\begin{align*}
\mathbb{P}\left(\left|\sum_{n=1}^N (X_n - \mathbb{E}[X_n])\right| \geq \varepsilon\right) &= \mathbb{P}\left(\left|\sum_{n=1}^N Y_n\right| \geq \varepsilon\right) \leq \inf_{\lambda \in [0,\infty)}\left(e^{-\lambda \varepsilon} \mathbb{M}_{\sum_{n=1}^N Y_n}(\lambda)\right) \\
&= \inf_{\lambda \in [0,\infty)}\left(e^{-\lambda \varepsilon} \prod_{n=1}^N \mathbb{M}_{Y_n}(\lambda)\right) = \inf_{\lambda \in [0,\infty)}\left(e^{-\lambda \varepsilon} \prod_{n=1}^N \mathbb{M}_{X_n - \mathbb{E}[X_n]}(\lambda)\right).
\end{align*}
$$
(12.29)
推论 12.1.13 的证明至此完成。

### 12.1.5 霍夫丁不等式

#### 12.1.5.1 有界随机变量的矩生成函数

**引理 12.1.14.** *设* $(\Omega, \mathcal{F}, \mathbb{P})$ *为概率空间，设* $\lambda, a \in \mathbb{R}$，$b \in (a, \infty)$，$p \in [0,1]$ *满足* $p = \frac{a}{(b-a)}$，*设* $X \colon \Omega \rightarrow [a,b]$ *为随机变量且* $\mathbb{E}[X] = 0$，*并设* $\phi \colon \mathbb{R} \rightarrow \mathbb{R}$ *满足对于所有* $x \in \mathbb{R}$，有* $\phi(x) = \ln(1 - p + pe^x) - px$。*则*
$$
\mathbb{E}[e^{\lambda X}] \leq e^{\phi(\lambda(b-a))}.
$$
(12.30)

*引理 12.1.14 的证明.* *注意到对于所有* $x \in \mathbb{R}$，有
$$
\begin{align*}
x(b-a) &= bx - ax = [ab - ax] + [bx - ab] = [a(b-x) + b(x-a)] \\
&= a(b-x) + b[b - a - b + x] = a(b-x) + b[(b-a) - (b-x)].
\end{align*}
$$
(12.31)
因此，我们得到对于所有 $x \in \mathbb{R}$，有
$$
x = a\left(\frac{b-x}{b-a}\right) + b\left[1 - \left(\frac{b-x}{b-a}\right)\right].
$$
(12.32)
这意味着对于所有 $x \in \mathbb{R}$，有
$$
\lambda x = \left(\frac{b-x}{b-a}\right) \lambda a + \left[1-\left(\frac{b-x}{b-a}\right)\right] \lambda b.
$$
(12.33)
事实 $\mathbb{R} \ni x \mapsto e^x \in \mathbb{R}$ 是凸的，从而证明了对于所有 $x \in [a, b]$，有
$$
e^{\lambda x} = \exp \left(\left(\frac{b-x}{b-a}\right) \lambda a + \left[1-\left(\frac{b-x}{b-a}\right)\right] \lambda b\right) \leq \left(\frac{b-x}{b-a}\right) e^{\lambda a} + \left[1-\left(\frac{b-x}{b-a}\right)\right] e^{\lambda b}.
$$
(12.34)
假设 $\mathbb{E}[X] = 0$ 因此确保了
$$
\mathbb{E}\left[e^{\lambda X}\right] \leq \left(\frac{b}{b-a}\right) e^{\lambda a} + \left[1-\left(\frac{b}{b-a}\right)\right] e^{\lambda b}.
$$
