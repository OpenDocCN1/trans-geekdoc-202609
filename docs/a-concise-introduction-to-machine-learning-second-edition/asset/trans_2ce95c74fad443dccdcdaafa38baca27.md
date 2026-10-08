

# Matern 核 $k(\mathbf{x,y}) = \frac{\sqrt{2\nu}}{\Gamma(\nu)l^{2\nu-1}} K_{\nu}\left(\frac{\sqrt{2\nu}}{l}\|\mathbf{x}-\mathbf{y}\|\right)$

其中 $l$ 再次是长度尺度，$\Gamma(\cdot)$ 是伽马函数，$K_{\nu}$ 是修正贝塞尔函数。参数 $\nu$ 控制平滑度。$\nu$ 越小，函数越平滑。对于 $\nu = 3/2$，核是一阶可微的；对于 $\nu = 5/2$，它是二阶可微的。对于 $\nu = 1/2$，Matern 核退变为：

## 指数核 $k(\mathbf{x,y}) = \exp\left(-\frac{\|\mathbf{x}-\mathbf{y}\|}{l}\right)$，它是不可微的。

## 有理二次核 $k(\mathbf{x,y}) = \left(1+\frac{\|\mathbf{x}-\mathbf{y}\|^2}{2l^2}\right)^{-\alpha}$，$l$ 是长度尺度，$\alpha > 0$ 是尺度混合参数。对于 $\alpha = 1/2$，此核退变为：

## 逆多尺度核 $k(\mathbf{x,y}) = \left(1+\frac{\|\mathbf{x}-\mathbf{y}\|^2}{\ell^2}\right)^{-1/2}$。

所有核都包含一个乘法参数 $\theta$，称为*标准差*。

如第 5.2 节所示，核的和、乘积或指数会产生另一个核。对核应用多项式结果的仍然是核。可以根据用例构建不同的组合。

如果核包含一个正的加性常数，则高斯过程的均值可以假设为零，正偏置对应于常数基函数，即包含在模型中的*偏置*（bias）。

列表 8.3 实现了六个核函数，并演示了如何从给定核的高斯过程中抽取样本。虽然从高斯过程中抽取的样本是一个函数，但后者生成的是密集的点值。这些是具有所需协方差矩阵的分布采样，该协方差矩阵是给定点和核 $\mathbf{x}_1,\dots,\mathbf{x}_n$ 的 Gram 矩阵 $\mathbf{K}$。计算 Cholesky 分解 $\mathbf{K} = \mathbf{LL}^T$。从标准多变量正态分布中抽取长度为 $n$ 的向量 $\mathbf{v}$。然后我们从协方差为 $\mathbf{K}$ 的分布中采样。将 $\mathbf{f}$ 的点值作为函数绘制出来。图 8.12 显示了每个已实现核的四次抽取结果。

本节的这一结论结束了从高斯过程中抽取函数的讨论。现在，一旦观测到某些对 $(\mathbf{x}_1, f_1),\dots,(\mathbf{x}_n, f_n)$，我们将注意力转到从高斯过程的后验分布（posterior）中抽取函数。令 $\mathbf{x}_*$ 是任意的且不同于 $\mathbf{x}_n$ 的点，$n=1,\dots,N$。记得我们使用的测量具有均值为零、方差为 $\sigma^2$ 的加性正态分布噪声，即

$f_* = f(\mathbf{x}_*) + \epsilon_*$。

```matlab
x <- (5:0,1:5); % 每行都是一个样本。

k = Gaussian(x,x, [1 1]);
% 注意有时需要加上 1e-15*eye(size(x))
% 以确保正定性。
L = chol(k, 'lower');
figure
f1 = L*normrnd(0,1,size(x));
plot(f1,'k--o');
f2 = L*normrnd(0,1,size(x));
plot(f2,'k--o');
f3 = L*normrnd(0,1,size(x));
plot(f3,'k--o');

% x 和 y 的每一行都是数据样本。
% 下函数计算特定核的协方差矩阵。

```matlab
% 常数核。
function k = Constant(x,y,param)
k = param*2 + ones(size(x,1),size(y,1));
```

```matlab
% 线性核。
function k = linear(x,y,params)
% x 的每一行与 y 的每一行的内积矩阵
% 由 x*y' 给出。
k = params(1)*2 + params(2)*x*y';
```

```matlab
% 二次核。
function k = quadratic(x,y,params)
k = (params(1)*2 + params(2)*x*y')^2;
```

```matlab
% 高斯核。
function k = gaussian(x,y,params)
% 计算 x 的某行与自身内积加上 y 的某行与自身内积
% 再去这两行内积的两倍。
sd = repmat(dot(x,x),size(y,1),1) + 
repmat(dot(y,y),size(x,1),1) - 2*repmat(dot(x,y),size(y,1),1);
k = params(1)*exp(-sd/(2*params(2)));
```

```matlab
% 逆二次核。
function k = inverseQuadratic(x,y,params)
so = repmat(dot(x,x),size(y,1),1) + 
repmat(dot(y,y),size(x,1),1) - 2*repmat(dot(x,y),size(y,1),1);
k = params(1).^2./sqrt(1+so/(params(2)));
```

列表 8.3: MATLAB 中不同核的高斯过程抽取。Python 请访问 https://github.com/ACF/Regression

![img/c6c76bf52016db78a5e30d47ef81_293_0.png] (a) 常数核。
![img/c6c76bf52016db78a5e30d47ef81_293_1.png] (b) 线性核，$k(\mathbf{x}, \mathbf{y}) = 1 + \mathbf{x}^T\mathbf{y}$。
![img/c6c76bf52016db78a5e30d47ef81_293_2.png] (c) 二次核，$k(\mathbf{x}, \mathbf{y}) = (1 + \mathbf{x}^T\mathbf{y})^2$。
![img/c6c76bf52016db78a5e30d47ef81_293_3.png] (d) 高斯核，$\theta=1$。
![img/c6c76bf52016db78a5e30d47ef81_293_4.png] (e) 指数核，$\theta=1$。
![img/c6c76bf52016db78a5e30d47ef81_293_5.png] (f) 逆多尺度核，$\theta=1$。

图 8.12: 不同核的高斯过程抽取。我们假设 $f$ 是从核 $k$ 均值为零的高斯过程中抽取的。因此，向量 $(t_1, \dots, t_n, t_*)$ 从均值为零的正态分布，协方差矩阵为

$$\begin{pmatrix} C & k(\mathbf{x}_*)^T \\ c(\mathbf{x}_*) \end{pmatrix}$$

其中向量 $k(\mathbf{x}_*)$ 的元素为 $k(\mathbf{x}_n, \mathbf{x}_*)$，$n = 1, \dots, N，$c(\mathbf{x}_*) = k(\mathbf{x}_*, \mathbf{x}_*) + \sigma^2$，且 $C$ 的 $(i, j)$ 元素为

$C_{ij} = k(\mathbf{x}_i, \mathbf{x}_j) + \sigma^2\delta_{ij},$

其中 $\delta_{ij}$ 在 $i \neq j$ 时为0，在 $i = j$ 时为1，称为克罗内克符号（Kronecker delta）。

![img/c6c76bf52016db78a5e30d47ef81_294_0.png] (a) 高斯核，$\theta=1$。
![img/c6c76bf52016db78a5e30d47ef81_294_1.png] (b) 指数核，$\theta=1$。
![img/c6c76bf52016db78a5e30d47ef81_294_2.png] (c) 逆多尺度核，$\theta=1$。

图 8.13: 不同核的后验高斯过程抽取。使用 A.1.1 中块矩阵的求逆公式，该分布的精度矩阵（precision matrix）

$$\begin{aligned} C^{-1} + \frac{C^{-1}k(\mathbf{x}_i)k(\mathbf{x}_j)^T C^{-1}}{c(\mathbf{x}_i)-k(\mathbf{x}_i)^T C^{-1}k(\mathbf{x}_i)} &= \frac{-C^{-1}k(\mathbf{x}_j)}{c(\mathbf{x}_i)-k(\mathbf{x}_i)^T C^{-1}k(\mathbf{x}_i)} &+ \frac{k(\mathbf{x}_i)^T C^{-1}k(\mathbf{x}_j)}{c(\mathbf{x}_j)-k(\mathbf{x}_j)^T C^{-1}k(\mathbf{x}_j)} \end{aligned}$$

