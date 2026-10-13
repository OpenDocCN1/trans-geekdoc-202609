
其合理性由 (a) *大数定律* 和 (b) *中心极限定理* [32] 保证。我们用 `𝔼[f(x)] = μ[f]` 表示期望，相应的方差记为 `var[f(x)] := 𝔼 [(f(x) − 𝔼[f(x)])²] = σ[f]²`。那么，上述两个定理保证了对于较大的 `N` 值，

```
\lim\limits_{N\rightarrow\infty}{\overline{\mathbb{E}}}_{f,N} = \mu_{f},
```
(14.3)

以及

```
p\left( {\overline{\mathbb{E}}}_{f,N} \right) \approx \mathcal{N}\left( {\overline{\mathbb{E}}}_{f,N} \middle| \mu_{f}, \frac{\sigma_{f}^{2}}{N} \right).
```
(14.4)

公式 [(14.3)](#Chp014_717-754_B9780443292385000202.xhtml#deq3) 中的极限指的是*几乎必然收敛*的概念，即

```
{Prob} \left\{ \lim\limits_{N\rightarrow\infty} \middle| {\overline{\mathbb{E}}}_{f,N} - \mu_{f} \middle| = 0 \right\} = 1.
```

公式 [(14.4)](#Chp014_717-754_B9780443292385000202.xhtml#deq4) 中的近似高斯分布保证了：随着 `N` 的增加，所得估计值 `{\overline{\mathbb{E}}}_{f,N}` 在真实值 `μ[f]` 周围的方差（随着 `N` 个样本集合的改变而变化）会减小。
