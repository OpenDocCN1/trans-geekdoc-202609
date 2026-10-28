
（要得到常数 8，选择足够大的绝对常数 $C$ 即可。）

现在通过对
$$|T_k| \cdot |T_{k-1}| \le |T_k|^2 \le 2^{2^{k+1}}$$
个 $(\pi_k(t), \pi_{k-1}(t))$ 对取并集界，来解除对 $t \in T$ 的固定。同样地，通过对所有 $k \in \mathbb{N}$ 取并集界，来解除对 $k$ 的固定。则 **(8.49)** 对所有 $t \in T$ 和 $k \in \mathbb{N}$ 同时成立，概率至少为
$$1 - \sum_{k=1}^{\infty} 2^{2^{k+1}} \cdot 2\exp(-8u^2 2^k) \ge 1 - 2\exp(-u^2).$$
若 $u > c$。（请检验最后一个不等式！）

**步骤 3：对增量求和。** 在界 **(8.49)** 对所有 $t \in T$ 和 $k \in \mathbb{N}$ 成立的事件中，我们可以将所有 $k \in \mathbb{N}$ 的不等式相加，并将结果代入链式和 **(8.47)**。我们得到
$$|X_t - X_{t_0}| \lesssim u \sum_{k=1}^{\infty} 2^{k/2} d(\pi_k(t), \pi_{k-1}(t)), \qquad (8.50)$$
其中记号 $\lesssim$ 隐藏了一个绝对常数因子。由三角不等式，
$$d(\pi_k(t), \pi_{k-1}(t)) \le d(t, \pi_k(t)) + d(t, \pi_{k-1}(t)).$$

利用该界、重新编号并代入 **(8.46)**，我们得到 **(8.50)** 的右端至多为 $Cu\gamma_2(T,d)$，即
$$|X_t - X_{t_0}| \lesssim u\gamma_2(T,d).$$
（检验！）对 $t\in T$ 取上确界得
$$\sup_{t \in T}|X_t - X_{t_0}| \lesssim u\gamma_2(T,d).$$
由于这对任意 $u > c$ 以至少 $1 - 2\exp(-u^2)$ 的概率成立，我们得到
$$\left\|\sup_{t \in T}|X_t - X_{t_0}|\right\|_{\psi_2} \lesssim \gamma_2(T,d).$$

这很快推出定理 **8.5.2** 的结论（检验！）

□

**注记 8.5.3**（泛链：增量的上确界）。与 Dudley 不等式（注记 **8.1.5**）类似，泛链实际上给出
$$\mathbb{E}\sup_{t,s \in T}|X_t - X_s| \le CK\gamma_2(T,d),$$
即使在没有零均值假设 $\mathbb{E}X_t = 0$ 的情况下也成立。

**注记 8.5.4**（泛链：高概率界）。定理 **8.5.2** 只给出期望界，但泛链实际上给出高概率界——我们已在 Dudley 不等式（注记 **8.1.6**）中见到过这一逻辑。假设 $T$ 有限，⁸ 对每个 $u\ge 0$，事件
$$\sup_{t,s\in T}|X_t-X_s|\le CK\left[\gamma_2(T,d)+u\cdot\operatorname{diam}(T)\right]$$
以至少 $1-2\exp(-u^2)$ 的概率成立。尝试习题 8.35 来证明这一点！对于高斯过程，你可以直接从高斯集中性推出它。

⁸ 与往常一样，我们假设 $T$ 有限以避免可测性问题；一般情形通常可通过逼近得到。

作为练习，尝试将泛链应用于经验过程（习题 8.36）。

### 8.5.3 优测度与比较定理

$\gamma_2$ 泛函（定义 8.5.1）通常比 Dudley 不等式（定理 8.1.3）中的覆盖数更难计算。但这往往值得付出努力——与 Dudley 不同，泛链在常数意义下是精确的：

**定理 8.5.5**（Talagrand 优测度定理）。*设 $(X_t)_{t\in T}$ 是集合 $T$ 上的零均值高斯过程，配备如 (7.1) 中的典范度量 $d(t,s)=\|X_t-X_s\|_{L^2}$。则*
$$c\gamma_2(T,d)\le \mathbb{E}\sup_{t\in T}X_t\le C\gamma_2(T,d).$$

定理 8.5.5 中的上界直接来自泛链（定理 8.5.2）。下界更为棘手；其证明可视为 Sudakov 不等式（定理 7.4.1）的一个精细的多尺度推广，此处不再展开。

由定理 8.5.2 可知，上界不仅对高斯过程成立，而且对所有*次高斯*过程成立。因此，结合上界与下界，我们可以用高斯过程来界定任意次高斯过程：

**推论 8.5.6**（Talagrand 比较不等式）。*设 $(X_t)_{t\in T}$ 是集合 $T$ 上的零均值随机过程，$(Y_t)_{t\in T}$ 是零均值高斯过程。假设*
$$\|X_t-X_s\|_{\psi_2}\le K\|Y_t-Y_s\|_{L^2}\quad\text{for all }t,s\in T.$$
*则*
$$\mathbb{E}\sup_{t\in T}X_t\le CK\,\mathbb{E}\sup_{t\in T}Y_t.$$

*证明* 考虑 $T$ 上的典范度量 $d(t,s)=\|Y_t-Y_s\|_{L^2}$。现在只需使用泛链界（定理 8.5.2），然后使用优测度定理 8.5.5 中的下界：
$$\mathbb{E}\sup_{t\in T}X_t\lesssim K\gamma_2(T,d)\lesssim K\,\mathbb{E}\sup_{t\in T}Y_t.\quad\square$$

**注记 8.5.7**（Sudakov-Fernique）。推论 8.5.6 将 Sudakov-Fernique 不等式（定理 7.2.8）推广到次高斯过程——而这次推广的代价仅是一个绝对常数因子！

我们将推论 8.5.6 应用于集合 $T\subset\mathbb{R}^n$ 上的典范高斯过程 $Y_x=\langle g,x\rangle$，其中 $g\sim N(0,I_n)$。回顾第 7.5 节，
$$w(T)=\mathbb{E}\sup_{x\in T}\langle g,x\rangle$$
是集合 $T$ 的*高斯宽度*。我们立即得到：

**推论 8.5.8**（Talagrand 比较不等式：几何形式）。*设 $(X_x)_{x\in T}$ 是子集 $T\subset\mathbb{R}^n$ 上的零均值随机过程。假设*
$$\|X_x-X_y\|_{\psi_2}\le K\|x-y\|_2 \quad\text{for all }x,y\in T.$$
*则*
$$\mathbb{E}\sup_{x\in T}X_x\le CKw(T).$$

**注记 8.5.9**（次高斯宽度 $\lesssim$ 高斯宽度）。一个很好的推论：若 $X$ 是 $\mathbb{R}^n$ 中的次高斯随机向量，则
$$\mathbb{E}\sup_{t\in T}\langle X,t\rangle\le CKw(T) \quad\text{for any bounded set }T\subset\mathbb{R}^n,$$
其中 $K=\|X\|_{\psi_2}$。只需将推论 8.5.8 应用于过程 $(\langle X,x\rangle)_{x\in T}$，根据次高斯随机向量的定义，其增量满足 $\|\langle X,x\rangle-\langle X,y\rangle\|_{\psi_2}\le K\|x-y\|_2$。

作为练习，尝试证明 Talagrand 比较的几个版本（习题 8.37），并用它得到次高斯向量 $\ell^p$ 范数的精确界（习题 8.38）。

## 8.6 Chevet 不等式

Talagrand 比较不等式（更一般地，泛链）是一个在广泛情境中适用的强大工具。让我们用它来获得随机二次型的一个非常一般的统一界：
$$\sup_{x\in T,\,y\in S}\langle Ax,y\rangle\le ?$$
其中 $A$ 是随机矩阵，$T,S$ 是任意有界集合。

当 $T$ 和 $S$ 是欧几里得球时，一个特殊情形导致 $A$ 的算子范数，我们已在定理 4.4.3 和 7.3.1 中研究过。现在让我们一般化，考虑任意集合，目标仅用两个几何量来界定事物：*高斯宽度*和*半径*，定义为
$$\operatorname{rad}(T):=\sup_{x\in T}\|x\|_2. \tag{8.51}$$

**定理 8.6.1**（次高斯 Chevet 不等式）。*设 $A$ 是 $m\times n$ 随机矩阵，其行 $A_i$ 独立、零均值、次高斯。设 $T\subset\mathbb{R}^n$ 和 $S\subset\mathbb{R}^m$ 是任意有界集合。则*
$$\mathbb{E}\sup_{x\in T,\,y\in S}\langle Ax,y\rangle\le CK\big[w(T)\operatorname{rad}(S)+w(S)\operatorname{rad}(T)\big]$$
*其中 $K = \max_i \|A_i\|_{\psi_2}$。若将“行”替换为“列”，结论同样成立。*

*定理 8.6.1 的证明* 我们将遵循定理 7.3.1 的证明，但使用 Talagrand 比较不等式代替 Sudakov-Fernique 不等式。

不失一般性，设 $K=1$。我们需要界定随机过程
$$X_{uv}=\langle Au,v\rangle,\quad u\in T,\ v\in S.$$

为了检验增量是次高斯的，固定 $(u,v),(w,z)\in T\times S$，写出
$$X_{uv}-X_{wz}=X_{uv}-X_{wv}+X_{wv}-X_{wz}=\langle A(u-w),v\rangle+\langle Aw,v-z\rangle.$$

利用三角不等式和次高斯假设（见习题 3.34——如果你跳过了它，现在做一下），我们得到
$$\begin{aligned}\|X_{uv}-X_{wz}\|_{\psi_2} &\le \|\langle A(u-w),v\rangle\|_{\psi_2}+\|\langle Aw,v-z\rangle\|_{\psi_2}\\ &\lesssim \|u-w\|_2\|v\|_2+\|v-z\|_2\|w\|_2\\ &\le \|u-w\|_2\,\operatorname{rad}(S)+\|v-z\|_2\,\operatorname{rad}(T).\end{aligned}\tag{8.52}$$

让我们为 Talagrand 比较不等式（推论 8.5.6）选择一个更简单的高斯过程 $(Y_{uv})$。增量界 (8.52) 指引我们做出一个好的选择：
$$Y_{uv}:=\langle g,u\rangle\operatorname{rad}(S)+\langle h,v\rangle\operatorname{rad}(T),$$
其中 $g\sim N(0,I_n)$ 和 $h\sim N(0,I_m)$ 相互独立。该过程的增量为
$$\|Y_{uv}-Y_{wz}\|_{L_2}^2=\|u-w\|_2^2\operatorname{rad}(S)^2+\|v-z\|_2^2\operatorname{rad}(T)^2.$$
（像定理 7.3.1 的证明中那样检验！）与 (8.52) 比较，我们得到
$$\|X_{uv}-X_{wz}\|_{\psi_2}\lesssim \|Y_{uv}-Y_{wz}\|_{L_2},$$
其中我们用到了不等式 $a+b\le\sqrt{2(a^2+b^2)}$。应用 Talagrand 比较不等式（推论 8.5.6），我们完成证明：
$$\begin{aligned}\mathbb{E}\sup_{u\in T,v\in S}X_{uv} &\le \mathbb{E}\sup_{u\in T,v\in S}Y_{uv}\\ &=\mathbb{E}\sup_{u\in T}\langle g,u\rangle\operatorname{rad}(S)+\mathbb{E}\sup_{v\in S}\langle h,v\rangle\operatorname{rad}(T)\\ &=w(T)\operatorname{rad}(S)+w(S)\operatorname{rad}(T).\end{aligned}$$

**注记 8.6.2**（随机矩阵的算子范数）。对于特殊情形 $T=S^{n-1}$ 和 $S=S^{m-1}$，Chevet 不等式给出我们熟悉的算子范数精确界：
$$\mathbb{E}\|A\|\le CK(\sqrt{n}+\sqrt{m}),$$
我们之前在第 4.4.2 节用 $\varepsilon$-网证明了它。但这种新方法更灵活。例如，选取 $T$ 和 $S$ 为 $\ell^p$ 球，就给出随机矩阵的 $\|A\|_{p\to q}$ 范数——尝试习题 8.41！
