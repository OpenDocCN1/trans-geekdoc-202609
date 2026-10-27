

### 练习 3.7.
假设正面朝上的概率由 $r$ 给出，我们在 $N$ 次抛掷中观察到 $y$ 次正面，并且 $r$ 带有参数为 $\alpha$ 和 $\beta$ 的 Beta 先验，则后验密度是参数为 $\delta=\alpha+y$ 和 $\gamma=\beta+N-y$ 的 Beta 密度。边际似然为：

$$p(y_N\mid\alpha,\beta)=\binom{N}{y_N}\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)}\frac{\Gamma(\alpha+y_N)\Gamma(\beta+N-y_N)}{\Gamma(\alpha+\beta+N)}.$$

获胜概率为：

$$\mathbf{E}_{p(r\mid y_N)}\{P(Y_{\mathrm{new}}\leq 6\mid r)\}=1-\sum_{y_{\mathrm{new}}=7}^{y_{\mathrm{new}}=10}\mathbf{E}_{p(r\mid y_N)}\{P(Y_{\mathrm{new}}=y_{\mathrm{new}}\mid r)\}$$

其中

$$\mathbf{E}_{p(r\mid y_N)}\{P(Y_{\mathrm{new}}=y_{\mathrm{new}}\mid r)\}=\binom{N_{\mathrm{new}}}{y_{\mathrm{new}}}\frac{\Gamma(\delta+\gamma)}{\Gamma(\delta)\Gamma(\gamma)}\frac{\Gamma(\delta+y_{\mathrm{new}})\Gamma(\gamma+N_{\mathrm{new}}-y_{\mathrm{new}})}{\Gamma(\delta+\gamma+N_{\mathrm{new}})}$$

根据题意，$y_N=9$，$N=20$。

场景 1：$\alpha=\beta=1$。后验密度参数为 $\delta=\alpha+y_N=10$，$\gamma=\beta+N-y_N=1+20-9=12$。边际似然为：0.0476。获胜概率为：0.84812。

场景 2：$\alpha=\beta=50$。后验密度参数为 $\delta=\alpha+y_N=59$，$\gamma=\beta+N-y_N=50+20-9=61$。边际似然为：0.1486。获胜概率为：0.83162。

场景 3：$\alpha=5,\beta=1$。后验密度参数为 $\delta=\alpha+y_N=14$，$\gamma=\beta+N-y_N=1+20-9=12$。边际似然为：0.0135。获胜概率为：0.7211。

### 练习 3.8.
代码如下（`scenarios.m`）：

```matlab
clear all;
close all;
% Define an array to hold the three scenarios
% Each row is alpha,beta for one scenario
hypers = [1,1;50,50;5,1];

scenario = 1; % Change this to look at different ones

% Generate the 100 tosses
N = 100;
toss = rand(N,1)<0.7;
Nheads = sum(toss);
Ntails = N - Nheads;

% Compute the posterior
alpha = hypers(scenario,1);
beta = hypers(scenario,2);
postalpha = alpha + Nheads;
postbeta = beta + Ntails;
```

![](img/4c6eb9ed1cdfcf169bfa1a2b6a72e99a_23_0.png)

### 练习 3.11.
代码如下（marglike.m）：

```matlab
clear all;close all;
% Generate the data
N = 100;
x = rand(N,1)*10^-5;
x = sort(x);
ss = 100;
f = 5*x.^3 - x.^2 + x;
t = f + randn(size(f))*sqrt(ss);

% Choose sigma_0^2
ss0 = 0.3; % Try increasing this

% Loop over model orders
order = [1:7];
X = repmat(1,size(x));
for i = 1:length(order)
    mu0 = zeros(order(i)+1,1);
    S0 = ss0*eye(order(i)+1);
    X = [X x.^order(i)];

    mlmean = X*mu0;
    mlcov = ss*eye(N) + X*S0*X';

    logml(i) = -(N/2)*log(2*pi) - (N/2)*log(det(mlcov)) - ...
        0.5*(t-mlmean)'*inv(mlcov)*(t-mlmean);

% Note that the non log value may be numerically instable.
ml(i) = exp(logml(i));
end
```

### 练习 3.12.
假设 **w** 固定，并且对 $\sigma^2$ 有以下逆伽马先验：

$$p(\sigma^2\mid\alpha,\beta)=\frac{\beta^\alpha}{\Gamma(\alpha)}(\sigma^2)^{-\alpha-1}\exp\left\{-\frac{\beta}{\sigma^2}\right\}.$$

似然是标准高斯似然：

$$p(\mathbf{t}\mid\mathbf{w},\mathbf{X},\sigma^2)=\frac{1}{(2\pi)^{N/2}(\sigma^2)^{N/2}}\exp\left\{-\frac{1}{2\sigma^2}(\mathbf{t}-\mathbf{Xw})^{\mathsf T}(\mathbf{t}-\mathbf{Xw})\right\}.$$

因此，$\sigma^2$ 的后验密度正比于这两个密度的乘积。合并同类项得：

$$p(\sigma^2\mid\mathbf{w},\mathbf{X},\alpha,\beta)\propto(\sigma^2)^{-\alpha-N/2-1}\exp\left\{-\frac{1}{\sigma^2}\left(\beta+\frac{1}{2}(\mathbf{t}-\mathbf{Xw})^{\mathsf T}(\mathbf{t}-\mathbf{Xw})\right)\right\}.$$

这是另一个逆伽马分布，参数 $\alpha^*$ 和 $\beta^*$ 由下式给出：

$$\alpha^*=\alpha+\frac{N}{2}$$
$$\beta^*=\beta+\frac{1}{2}(\mathbf{t}-\mathbf{Xw})^{\mathsf T}(\mathbf{t}-\mathbf{Xw}).$$

这将是高斯近似的均值，我们已经可以看到它等于后验均值 $\mu$。

为了求协方差矩阵，我们对 $g$ 求二阶导数：

$$\frac{\partial^2 g}{\partial \mathbf{w}\partial \mathbf{w}^\mathsf{T}} = -(\mathbf{I}_D + \mathbf{X}^\mathsf{T}\mathbf{X})$$

因此，拉普拉斯近似的协方差为：

$$(\mathbf{I} + \mathbf{X}^\mathsf{T}\mathbf{X})^{-1}.$$

这与后验协方差矩阵完全一致，从而证实该近似在这种情况下是精确的。

### 练习 4.2.
我们感兴趣的是对后验 $p(r|N, y, \alpha, \beta)$ 的拉普拉斯近似。第一步是找到 $r$ 的 MAP 值。对数后验为（去掉常数项）：

$$g = (\alpha - 1) \log r + (\beta - 1) \log(1 - r) + y \log r + (N - y) \log(1 - r).$$

对 $r$ 求偏导得到：

$$\frac{\partial g}{\partial r} = \frac{\alpha + y - 1}{r} - \frac{\beta + N - y - 1}{1 - r}.$$

整理该表达式得到 $r$ 的 MAP 解：

$$\hat{r} = \frac{\alpha + y - 1}{\alpha + \beta + N - 2}.$$

这将是高斯近似的均值。方差由下式给出：

$$\sigma^2 = - \left( \frac{\partial^2 g}{\partial r^2} \right)^{-1} = - \left( - \frac{\alpha + y - 1}{r^2} - \frac{\beta + N - y - 1}{(1 - r)^2} \right)^{-1}$$

### 练习 4.3.
下图展示了一个示例，其中 $\alpha = \beta = 2$，$y = 2$，$N = 10$。

![](img/4c6eb9ed1cdfcf169bfa1a2b6a72e99a_27_0.png)

### 练习 4.4.
这是一个很好的例子，用以说明采样的威力。想象从 -0.5 到 0.5 之间的均匀分布中抽取成对的值。这些值将均匀分布在下图所示的正方形内：

这些点之一落在圆内的概率一定等于圆面积与正方形面积之比。我们可以通过生成 N 对（即 N 个点），然后计算落在圆内的对数（s），得到该值的经验估计。于是：

$$\frac{s}{N} \approx \frac{\pi r^{2}}{1 \times 1} = 0.5^{2}\pi.$$

整理该表达式即可得到 π 的近似值：

$$\pi \approx \frac{s}{0.5^{2}N}.$$

例如，对 100 个点进行一次随机抽样得到的值为：

$$\pi \approx 3.240.$$

正如我们所预期，平均而言，随着抽样次数增多，该近似会变得更加准确。10000 次抽样后的一个例子是：

$$\pi \approx 3.129.$$

### 练习 4.5.
按如下方式重新整理：

$$P(T_{\text{new}}=1|\mathbf{x}_{\text{new}},\widehat{\mathbf{w}}) = \frac{1}{1+\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})}$$
$$0.5 = \frac{1}{2}=\frac{1}{1+\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})}$$
$$2 = 1+\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})$$
$$1 = \exp(0)=\exp(-\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}})$$

因此 $\widehat{\mathbf{w}}^{\mathsf{T}}\mathbf{x}_{\text{new}}=0.$

### 练习 4.6.
假设一个高斯先验：

$$p(\mathbf{w}) = \mathcal{N}(\mathbf{0},\mathbf{I}_{D}),$$

并且：

$$v_{n}=\exp\{\mathbf{w}^{\mathsf{T}}\mathbf{x}_{n}\}$$

对数后验正比于：

$$g = -\frac{1}{2}\mathbf{w}^{\mathsf{T}}\mathbf{w} + \sum_{n}(t_{n}\log v_{n} - v_{n}).$$

对 $\mathbf{w}$ 求偏导即可得到梯度：

$$\frac{\partial g}{\partial \mathbf{w}} = -\mathbf{w} + \sum_{n}\frac{t_{n}}{v_{n}}\frac{\partial v_{n}}{\partial \mathbf{w}} - \frac{\partial v_{n}}{\partial \mathbf{w}}.$$

现在，

$$\frac{\partial v_n}{\partial \mathbf{w}}=\mathbf{x}_n v_n$$

因此：

$$\frac{\partial g}{\partial \mathbf{w}}=-\mathbf{w}+\sum_n\mathbf{x}_n(t_n-v_n).$$

Hessian 矩阵通过再次求导得到。如果这一步看起来有困难，你不妨以（比如）$D=2$ 为例，逐个计算矩阵的每个元素：

$$\frac{\partial^2 g}{\partial\mathbf{w}\partial\mathbf{w}^{\mathsf T}}=-\mathbf{I}-\sum_n v_n\mathbf{x}_n\mathbf{x}_n^{\mathsf T}$$

给定 $\mathbf{w}$ 的某个初始值，优化方案按如下方式反复更新 $\hat{\mathbf{w}}$，直到它收敛到最大值：

$$\mathbf{w}\leftarrow\mathbf{w}-\left(-\mathbf{I}-\sum_n v_n\mathbf{x}_n\mathbf{x}_n^{\mathsf T}\right)^{-1}\left(-\mathbf{w}+\sum_n\mathbf{x}_n(t_n-v_n)\right)$$

### 练习 4.7.
根据上一练习的结果，这一题很直接。拉普拉斯近似是一个高斯分布，其均值 $\boldsymbol{\mu}$ 和协方差 $\boldsymbol{\Sigma}$ 分别为：$\boldsymbol{\mu}=\hat{\mathbf{w}}$，即上一练习中用 Newton-Raphson 方案得到的最大值；协方差为：

$$\boldsymbol{\Sigma}=-\left(-\mathbf{I}-\sum_n\hat{v}_n\mathbf{x}_n\mathbf{x}_n^{\mathsf T}\right)^{-1},$$

其中：

$$\hat{v}_n=\exp\{\hat{\mathbf{w}}^{\mathsf T}\mathbf{x}_n\}.$$

### 练习 4.8.
示例代码如下（`poisscount.m`）：

```matlab
%% Laplace and Metropolis-Hastings for a Poisson Counts model
% Simon Rogers, August 2011
clear all;
close all;

% Generate the 'true' data.
N = 200; % Number of data objects
x = [repmat(1,N,1) randn(N,1)];
w = randn(2,1);

temp = exp(x*w);

t = poissrnd(temp);

truew = w;
%% Newton Raphson
% Initialise w
w = rand(2,1)*5;
wall = [];
```

