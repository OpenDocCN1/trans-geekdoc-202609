

# 计算物理中的高级深度学习技术

## PINN 预测 | 基值 (Ground Truth)

![](img/020125e0e698f9771fbbd32f2ace1e80_163_0.png)

**图 5.1** 平行板电容器中解析解与 PINN 计算解的对比。

[20]（例如圆柱坐标系 [21]、球坐标系 [22]、抛物坐标系 [23] 等），并解决了一些典型的物理问题。由于不同坐标系下的梯度算子表达式需要进行修改。例如，在圆柱坐标系中，如果有一个平行板电容器，内部边界为 $r_i = 1, V_i = 1V$，外部边界为 $V_e = 0V$，则电势满足：

> $$\mathcal{L}_i = \sum_{i=1}^N ||u(x_i, t_i) - \mathbf{u}_0||^2$$

因此，方程可以修改为

```python
def loss_p(self, x):
    u = self.net(x)
    u_g = gradients(u, x) [0]
    u_rf = u_g[:, 0], u_g[:, 1]
    u_rr = gradients(u_f, x) [:, 0]
    u_ff = gradients(u_f, x) [:, 1]
    loss = u.sum(u.rr+u.ff/(x[:]**2)*2)+u.r/x[:],:0])
    return (loss**2).mean()
```

这是为了证明偏微分方程 (PDE) 的解析解：

> $$\Phi = -ln r + 1$$

图 5.1 展示了方程的解析解和 PINN 的计算结果。此外，该结构也适用于圆柱坐标系中的其他物理方程。图 5.2 显示了圆柱坐标系中的两种典型 PDE，即泊流和圆柱冷却。

# 150 基于深度学习的前向建模与反演技术

## 基值 | PINN 预测 | 泊流

![](img/020125e0e698f9771fbbd32f2ace1e80_164_0.png)

### 泊流 (Poiseuille Flow)
> 边界条件:
r=1, u=0
r=e, u=0
PDE:
dlu/dt = $-\nabla p + \mu\nabla²u$
解析解:
u = $(1-r²)e^{-(r²-1)/4}$

### 圆柱冷却 (Cylinder Cooling)
> 边界条件:
r=L, t=0
t=0, u=1-r²
PDE:
du/dt = $\alpha(1/r)d/dr(r du/dr)$
解析解:
t = $\sum J_0(\mu nr) e^{-\mu n^2t}$

图 5.2 泊流和圆柱冷却中解析解与计算解的对比。

解析解和 PINN 计算结果分别如图 5.2 (a) 和 (b) 所示。显而易见，PINN 可以快速获得圆柱坐标系中三类物理问题的高精度数值解。

### 5.1.1.2 球坐标系

PINN 也可以用于球坐标系。研究区域调查了球坐标系中的静电场。该区域作为球壳的一部分，满足以下要求：

```
r = 1, U = 2 \sin 2\theta \phi
```
```
r = 2, U = 33/8 \sin 2\theta \sin \phi
```
```
$\theta = \pi/6, U = \sqrt{3}/2 (r^2 + 1/r^3) \sin \phi$
```
```
$\theta = \pi/3, U = \sqrt{3}/2 (r^2 + 1/r^3) \sin \phi$
```
```
$\phi = 0, U = 0$
```

![](img/020125e0e698f9771fbbd32face1e80_165_0.png)

**图 5.3** 球坐标系中解析解与 PINN 计算解的对比。

在该区域，满足拉普拉斯方程：

$$\nabla^2 U = \frac{1}{r^2} \frac{\partial}{\partial r}(r^2 \frac{\partial U}{\partial r}) + \frac{1}{r^2 \sin \theta} \frac{\partial}{\partial \theta}(\sin \theta \frac{\partial U}{\partial \theta}) = 0$$

通过变量分离法可以获得解析解：
$$U = \frac{1}{\sqrt{3}} \sin 2\theta \sin \phi$$

5.3 显示了 PINN 获取的数值结果与解析解之间的对比，其中 (a)(bb)(c) 分别是基值、预测值和误差。显然，对于球坐标系，PINN 的性能仍然非常出色，误差可以忽略不计。

### 5.1.1.3 抛物坐标系

最后考虑抛物坐标系中的特殊 PDE。抛物坐标系与直角坐标系的关系为：

$$\xi = r(1 + \cos \theta) = \sqrt{x^2 + y^2} + z$$
$$\eta = r(1 - \cos \theta) = \sqrt{x^2 + y^2} - z$$
$$\phi = \arctan(y/x)$$

![](img/020125e0e698f9771fbbd32face1e80_166_0.png)

抛物坐标系中解析解与 PINN 计算解的对比。

拉普拉斯算子定义为：

```
\nabla^2u = \frac{4}{\xi+\eta}\left[\frac{\partial}{\partial\xi}\frac{\partial u}{\partial\xi} + \frac{\partial}{\partial\eta}\frac{\partial u}{\partial\eta}\right]+\frac{1}{(\xi+\eta)^2}\frac{\partial^2u}{\partial\phi^2} = 0
```

涉及的偏微分方程和边界条件表示为：

```
\frac{\partial^2u}{\partial\xi^2} + \frac{\partial^2u}{\partial\eta^2} + \frac{2}{\xi}\frac{\partial u}{\partial\xi} + \frac{2}{\eta}\frac{\partial u}{\partial\eta}-0.01(\xi+\eta)=0
```
```
u=y(\xi=0.4, \eta=0.4; \xi=2.5, \eta=2.5)
```

通过实现 PINN 和数值方法 FDM 获得的结果如图 5.4 所示。可以发现两者之间的差异微乎其微，这充分证明了 PINN 的强大预测能力。

### 5.1.2 基于卷积的 PINN

最近，卷积 PINN [24, 25] 由于参数共享内核、空间特征提取和轻量级权重而日益流行。与基于 FCNN 的 PINN 不同，基于 CNN 的框架不拟合算子，而是近似微分。在某种意义上，它类似于有限差分法。与 PINN 相比，CNN 架构体积更小泛化性能更好。

基于 CNN 的 PINN 由两部分组成，相应的内核分别为可训练和固定。可训练卷积内核传统的监督学习，而固定卷积内核用于计算 PDE 解。以二维拉普拉斯算子为例，不同阶的卷积内核如表 5.1 所示。

## 表 5.1 差分算子的矩阵表示。

| | $\nabla$ | | $\nabla^2$ |
|---|---|---|---|---|---|
| 一阶 | 0 | 1 | 0 | 0 | -1 | 0 |
| $1/2$ | -1 | 0 | 0 | 1 | -4 | 1 |
| | | 0 | -1 | 0 | 0 | 1 | 0 |
| 二阶 | 0 | -1 | 0 | 0 | 0 | 0 |
| $1/12$ | 0 | 8 | 0 | 0 | 16 | 0 |
| | | 0 | -8 | -1 | -16 | -60 | -1 |
| | | 0 | -8 | 0 | 0 | 16 | 0 |
| | | 0 | 0 | 0 | 0 | -1 | 0 |

