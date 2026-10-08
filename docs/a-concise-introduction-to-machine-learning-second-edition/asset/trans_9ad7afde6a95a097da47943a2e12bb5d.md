

在 $a_k^{(L)}$ 直接依赖于 $u_{ji}^{(L)}$ 的情况下。我们稍后会详细讨论这一点。首先，我们来看可能的机器学习任务。

如果神经网络执行的是二分类，则只有一个输出神经元。我们在正向传播的最后一步，即最终激活函数的应用，在第 $n$ 阶误差函数中显式地给出：

```
$E_n(\mathbf{w}) = -t_n \log \frac{1}{1+\exp(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))}
$-(t_n) \log \left(1-\frac{1}{1+\exp(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))}\right)
= t_n \log \left(1-\frac{\exp(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))}{1+\exp(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))}\right)
$-(t_n) \log \frac{\exp(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))}{1+\exp(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))}}
= \log (1+\exp(-a^{(L)}(\mathbf{x}_n, \mathbf{w)})) + (1-t_n)a^{(L)}(\mathbf{x}_n, \mathbf{w}),$
```

由于 $\log a/b = \log a - \log b$。对 $w_{ji}^{(i)}$ 求导得到：

```
$$\frac{\partial}{\partial w_{ji}^{(i)}}E_n(\mathbf{w}) = \frac{\exp(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))}{1+\exp(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))} \frac{\partial}{\partial w_{ji}^{(i)}}(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))
+(1-t_n)\frac{\partial}{\partial w_{ji}^{(i)}}(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))
-\frac{1}{1+\exp(-a^{(L)}(\mathbf{x}_n, \mathbf{w}))}-1}\frac{\partial}{\partial w_{ji}^{(i)}}a^{(L)}(\mathbf{x}_n, \mathbf{w})
+(1-t_n)\frac{\partial}{\partial w_{ji}^{(i)}}a^{(L)}(\mathbf{x}_n, \mathbf{w})
=y(\mathbf{x}_n, w_n)-t_n\frac{\partial}{\partial w_{ji}^{(i)}}a^{(L)}(\mathbf{x}_n, \mathbf{w}),$
```

其函数形式与 (9.1) 相同，其中 $K=1$。利用 $K$ 个并行二分类任务的误差是各个二分类问题误差之和的这一事实，第 $n$ 个贡献对 $w_{ji}^{(i)}$ 的导数在这种情况下也具有 (9.1) 的形式。

最后，通过对 $K$ 多类进行分类，当 $t_n$ 具有 $1-K$ 表示形式时。当 $k_n$ 为零时，$t_n$ 中等于一的部分对误差函数的贡献为：

```
$E_n(\mathbf{w}) = - \log \frac{\exp(a^{(L)}(\mathbf{x}_n, \mathbf{w}))}{1+\sum_{k=1}^K \exp(a^{(L)}(\mathbf{x}_n, \mathbf{w}))}
= \log \left(\sum_{k=1}^K \exp(a^{(L)}(\mathbf{x}_n, \mathbf{w}))\right)-a_{h_n},$
```

对 $w_{ji}^{(i)}$ 的导数为：

```
$$\frac{\partial}{\partial w_{ji}^{(i)}} E_n(\mathbf{w}) = \sum_{r=1}^K \exp(a_r^{(L)}(\mathbf{x}_n, \mathbf{w})) \frac{\partial}{\partial w_{ji}^{(i)}} a_r^{(L)}(\mathbf{x}_n, \mathbf{w}) - \frac{\partial}{\partial w_{ji}^{(i)}} a_k^{(L)}(\mathbf{x}_n, \mathbf{w})$$
$ = \sum_{r=1}^K y_r(\mathbf{w}) \frac{\partial}{\partial w_{ji}^{(i)}} a_r^{(L)}(\mathbf{x}_n, \mathbf{w}) - t_{nr} \frac{\partial}{\partial w_{ji}^{(i)}} a_r^{(L)}(\mathbf{x}_n, \mathbf{w})$$
$ = \sum_{r=1}^K (y_r(\mathbf{w}) - t_{nr}) \frac{\partial}{\partial w_{ji}^{(i)}} a_r^{(L)}(\mathbf{x}_n, \mathbf{w}),$
```

其中我们使用了 $\mathbf{t}_n$ 的独热（one-hot）表示。这再次具有相同的函数形式。

(9.1) 中所有误差函数第 $n$ 个贡献的导数的这一事实，是激活函数与误差函数之间的规范链接。

需要使用链式法则，直到到达与 $w_{ij}$ 有直接依赖关系的层。令 $s$ 为任意大于或等于 $l$ 的层。我们将通过归纳法证明：

```
$$\frac{\partial}{\partial w_{ji}^{(i)}} E_n(\mathbf{w}) = \sum_{m=1}^{M_{s-1}} g_m^{(s)} \frac{\partial}{\partial w_{ji}^{(i)}} a_m^{(s)}(\mathbf{x}_n, \mathbf{w}), \quad (9.2)$$
```

对于适当选择的 $\delta_m^{(s)}$。

由于 (9.1)，当 $s=L$ 且设置 $M_L=K$ 并定义：

```
$$\delta_k^{(L)} = y_k(\mathbf{x}_n, \mathbf{w}) - t_{nk},
```

这是 $k$ 类输出的情况。我们假设 (9.2) 在某个 $s > l$ 时成立，并证明它在 $s-1$ 时成立。

```
$$\alpha_m^{(s)}(\mathbf{x}_n, \mathbf{w}) = \sum_{r=1}^{M_{s-1}} w_{mr}^{(s-1)} a_r^{(s-1)} = \sum_{r=1}^{M_{s-1}} w_{mr}^{(s-1)} a_r^{(s-1)},
```

对 $w_{ji}^{(i)}$ 的导数为：

```
$$\frac{\partial}{\partial w_{ji}^{(i)}} a_m^{(s)}(\mathbf{x}_n, \mathbf{w})$$
```

（此处逻辑衔接）

将此代入 (9.2)，得到：

```
$$\frac{\partial}{\partial w_{ji}^{(i)}} E_n(\mathbf{w}) = \sum_{m=1}^{M_{s-1}} \delta_m^{(s)} \frac{\partial}{\partial w_{ji}^{(i)}} a_m^{(s)}(\mathbf{x}_n, \mathbf{w}),$$
```

其中 $\delta_m^{(s)} = y_m(\mathbf{x}_n, \mathbf{w}) - t_{nm}$。

