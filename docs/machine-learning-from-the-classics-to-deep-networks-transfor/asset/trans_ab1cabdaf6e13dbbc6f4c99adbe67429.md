

### 11.16

考虑书中 SVM 示例中描述的二分类二维分类任务。数据集包含 `N = 150` 个点，`x[n] = [x[n, 1], x[n, 2]]^T`，`n = 1, 2, …, N`，均匀分布在 `[-5, 5] × [-5, 5]` 中。对每个点，计算

```
y[n] = 0.05 * x[n, 1]^3 + 0.05 * x[n, 1]^2 + 0.05 * x[n, 1] + 0.05 + η
```

1.  其中 `η` 表示方差为 `σ[η]^2 = 4` 的零均值高斯噪声。然后，如果 `x[n, 2] ≥ y[n]`，将其分配给 `ω[1]`，如果 `x[n, 2] < y[n]`，则分配给类别 `ω[2]`。

    1.  **(a)** 绘制点 `[x[n, 1], x[n, 2]]`，每个类别使用不同颜色。

    2.  **(b)** 使用 `libsvm` 或其他相关的 MATLAB® 包获取 SVM 分类器。使用高斯核，设 `σ = 10` 和 `C = 1`。绘制分类器和间隔（对于后者，可使用 MATLAB® 的 `contour` 函数）。此外，找出支持向量（即具有非零拉格朗日乘子并对分类器展开有贡献的点），并将它们绘制为圆圈点。

    3.  **(c)** 重复步骤 11.16b，使用 `C = 0.5, 0.1` 和 `0.05`。

    4.  **(d)** 重复步骤 11.16b，使用 `C = 5, 10, 50` 和 `100`。

    5.  **(e)** 对结果进行评论。

### 11.17

考虑第 [11.15](#Chp011_519-582_B9780443292385000172.xhtml#s0175) 节中描述的作者身份识别问题。

1.  **(a)** 使用数据集中姓名以“T”开头的作者的训练文本，利用文本的 `n`-gram 图表示和 VS 作为核函数，执行 10 折交叉验证。

2.  **(b)** 使用相同的数据子集，创建文本的向量空间模型表示，并应用高斯核进行分类。将结果与 (a) 的结果进行比较。

## 参考文献

*   [1] D. Achlioptas, F. McSherry, B. Schölkopf, Sampling techniques for kernel methods, *Advances in Neural Information Processing Systems*. *NIPS*. 2001.
*   [2] A. Argyriou, C.A. Micchelli, M. Pontil, When is there a representer theorem? Vector versus matrix regularizers, *J. Mach. Learn. Res.* 2009;10:2507–2529.
*   [3] N. Aronszajn, Theory of reproducing kernels, *Trans. Am. Math. Soc.* 1950;68(3):337–404.
*   [4] F.R. Bach, Consistency of the group LASSO and multiple kernel learning, *J. Mach. Learn. Res.* 2008;9:1179–1225.
*   [5] K. Bache, M. Lichman, UCI Machine Learning Repository, University of California, Irvine, School of Information and Computer Sciences [http://archive.ics.uci.edu/ml](http://archive.ics.uci.edu/ml); 2013.

