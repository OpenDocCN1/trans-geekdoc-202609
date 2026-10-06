

# FG 多孔复合结构

![](img/90ed165a39fa708ec438fcda79319c25_208_0.png)

71 对称孔隙率分布 72 非对称孔隙率分布 73 对称孔隙率分布

图 7.2 由随机 $\alpha$ 显示的各种分布。

同样，梯度 GPL 模式通过调整 GPL 体积分分数的函数来实现：

```
$$\begin{aligned} c_{l1} &= 1 - \cos\left(\frac{\pi}{h}\right) & P1 \\ c_{l2} &= 1 - \cos\left(\frac{\pi}{2h}\right) & P2 \\ V_{GPL}^f \cong c_{l3} &= 1 - \cos\left(\frac{\pi}{4h}\right) & (7.4) \ P3 \\ c_{l4} &= 1 - \cos\left(\frac{\pi}{2}\right) & P4 \end{aligned}$$
```

$\beta$ 是 GPL 的随机幂因子。参数 $c_{l1}, c_{l2}, c_{l3},$ 和 $c_{l4}$ 是对于不同的孔隙率分布和 GPL 分散模式组合，多孔纳米复合梁 GPL 体积分数的最大值。

采用 Halpin-Tsai 微观力学模型，多孔纳米复合梁的最大杨模量 $E_{max}$ 可以写为：

```
$E_{max} = E_m \times \frac{1 + \eta_L \mu_L V_{GPL}}{1 - \mu_L V_{GPL}} + 0.625 \times \frac{1 + \eta_T \mu_T V_{GPL}}{1 - \mu_T V_{GPL}} \eqno (7.5)$
```

其中 $\eta_l = 2l_{GPL}/h_{GPL}, \eta_T = 2w_{GPL}/h_{GPL}$ 分别是 GPL 纳米纤维平均长度 $l_{GPL}$、宽度 $w_{GPL}$ 和厚度 $h_{GPL}$ 之间的关系。$E_m$ 是金属泡沫的杨模量。$V^{GPL}$ 是纳米复合梁总体积 $V$ 的比例值。材料系数 $\mu_L, \mu_T$ 可以进一步表示为：

```
$$\mu_L = \frac{E_{GPL} - E_m}{E_{GPL} + \eta_L}, \mu_T = \frac{E_{GPL} - E_m}{E_{GPL} + \eta_T} \eqno (7.6)$$
```

其中 $E_{GPL}$ 表示 GPL 的杨模量。

FGGER 梁的质量密度和泊松比表示为：

```
$$\rho_{max} = \rho_{GPL}^{GPL} + \rho_{m}(1 - V_{f}^{GPL}) \\ v_{max} = v_{GPL}^{GPL} + v_{m}(1 - V_{f}^{GPL})$$ (7.7)
```

其中 $\rho_{m}$ 和 $v_{m}$ 分别是基体和 GPL 的质量密度和泊松比。这两个组分的体积分数关系为 $V^{GPL} + V^{m} = 1$。为了比较不同的孔隙率分布和 GPL 模式，保持质量 $M$ 固定，因此 GPL 的体积 $V_{GPL}$ 可以写为：

```
$V_{GPL} = \frac{V_{f}^{GPL}}{\rho_{max}}, M = \int_{-h/2}^{h/2} \rho(z)dz$ (7.8)
```

此外，GPL 的体积分数由混合法则确定，其表达式为：

```
$V_{GPL} = \frac{V_{f}^{GPL}}{V_{GPL} + V_{m}} = \frac{\Delta_{GPL}}{\Delta_{GPL} + (1 - \rho_{GPL}/\rho_{m})}$ (7.9)
```

其中 $\Delta_{GPL}$ 是基体内部增强体的质量分数，在某些研究中也标记为 wt。通过将等.(7.9) 代入等.(7.8)，然后结合等.(7.4)，可以推导出对于不同孔隙率分布和分散组合的多孔纳米材料的参数 $c_{s1}, c_{s2}, c_{s3}$ 和 $c_{s4}$：

```
$c_{s1} = \int_{-h/2}^{h/2} [1 - \cos(\frac{\pi z}{h})] \frac{\rho(z)}{\rho_{max}}dz \\ c_{s2} = \int_{-h/2}^{h/2} [1 - \cos(\frac{\pi z}{2h})] \frac{\rho(z)}{\rho_{max}}dz \\ c_{s3} = \int_{-h/2}^{h/2} [1 - \cos(\frac{\pi z}{4})] \frac{\rho(z)}{\rho_{max}}dz \\ c_{s4} = \int_{-h/2}^{h/2} \frac{\rho(z)}{\rho_{max}}dz \\ \Delta_{GPL}^{h/2}^{h/2} = \int_{-h/2}^{h/2} (1 - e_{m}(\rho(z)))dz \Delta_{GPL} + (1 - \rho_{GPL}/\rho_{m})}$ (7.10)
```

其中 $e_m$ 是金属泡沫的密度。通过高斯模型引入杨模量与质量密度之间的关系：

```
$E_{max} = \frac{E(z)}{\varphi(z)} + \frac{1}{\rho_{max}}$
```

将等.(7)代入等.(1)，可以得到：

```
$e_m = \frac{1 - \sqrt{\varphi(z)}}{\varphi(z)}$
```

此外，均匀孔隙率的系数 $\varphi_0$ 可以推导为：

```
$\varphi_0 = \frac{1}{e_0} \left[1 - (\frac{M}{\rho_{max}} + \frac{1}{\rho_{max}})\right]$
```

## 7.3 轴理论形成

梁沿 $x$ 和 $z$ 轴的位移 $U(x,t)$ 和 $W(x,t)$ 表示为：

```
$U(x,t) = u_0(t) + z\psi(t) \\ W(x,t) = w_0(t)$
```

其中 $u_0(t)$ 和 $w_0(t)$ 是纵向和横向位移。$\psi$ 是梁截面的旋转。线性应变 $\varepsilon_{xx}$ 和剪切应变 $\gamma_{xz}$ 可以推导为：

```
$\varepsilon_{xx} = \frac{\partial u_0}{\partial x} + z\frac{\partial\psi}{\partial x}, \gamma_{xz} = \frac{\partial w_0}{\partial x} + \frac{\partial\psi}{\partial x}$
```

对应的正应力 $\sigma_{xx}$ 和剪切应力 $\tau_{xz}$ 为：

```
$\sigma_{xx} = \frac{E(z)}{1-v(z)^2}\varepsilon_{xx}, \tau_{xz} = G(z)\gamma_{xz}$
```

采用哈密顿原理：

```
$$\int_{0}^{\tau} (\delta U_k - \delta U_s + \delta U_d)dt = 0 \quad (7.17)$$
```

其中 $\delta U_k, \delta U_s,$ 和 $\delta U_d$ 分别表示动能、应能以及外力势能。得到的 FG 增强梁的控制方程如下：

```
$$\delta u : \frac{\delta N_s}{\delta x} = I_0 \frac{\partial^2 u_0}{\partial t^2} + I_1 \frac{\partial^2 \psi}{\partial t^2} \\ \delta w : \frac{\delta Q_s}{\delta x} = -P_x \frac{\partial^2 w_0}{\partial x^2} + \frac{\partial^2 \psi}{\partial t^2} \\ \delta \psi : \frac{\delta M_s}{\delta x} = I_1 \frac{\partial^2 u_0}{\partial x^2} + I_2 \frac{\partial^2 \psi}{\partial t^2} \quad (7.18)$$
```

其中 $N_s, M_s,$ 和 $Q_s$ 可以表示为：

```
$N_s = A_{11} \frac{\partial u_0}{\partial x} + B_{11} \frac{\partial \psi}{\partial x} \\ M_s = B_{11} \frac{\partial u_0}{\partial x} + D_{11} \frac{\partial \psi}{\partial x} \\ Q_s = A_{55} (\frac{\partial w_0}{\partial x} + \frac{\partial \psi}{\partial x})$
```

刚度分量计算为：

```
$A_{11}, B_{11}, D_{11} = \int_{-h/2}^{h/2} \frac{E(z)}{1-v(z)^2} dz \\ A_{55} = \int_{-h/2}^{h/2} G(z)dz \quad (7.20)$
```

其中 $b$ 是梁的宽度，$k$ 表示剪切修正因子，在本研究中取 $k=5/6$。代入等.(7.18),等.(7.19)，GPL 增强梁的控制方程重写为：

```
$A_{11} \frac{\partial^2 u_0}{\partial x^2} + B_{11} \frac{\partial^2 \psi}{\partial x^2} = I_0 \frac{\partial^2 u_0}{\partial t^2} + I_1 \frac{\partial^2 \psi}{\partial t^2} \\ A_{55} (\frac{\partial^2 w_0}{\partial x^2} + \frac{\partial^2 \psi}{\partial x^2}) = -P_x \frac{\partial^2 w_0}{\partial x^2} + I_2 \frac{\partial^2 \psi}{\partial t^2} \quad (7.21)$
```

其中惯性项由给出：

```
$(I_0, I_1, I_2) \approx \int_{-h/2}^{h/2} \rho(z)(1, z, z^2)dz \quad (7.22)$
```

## 7.4 求解方法与方程

### 7.4.1 离散卷积算法

采用 DSC 定理 [28]，函数 $F(x)$ 关于 $x_i$ 的 $n$ 阶导数表示为：

```
$$F^{(n)}(x_i) = \sum_{j=i-M}^{i+M} \phi_{\Delta}^{(n)}(x_i - x_j)F(x_j), \quad (n=0, 1, 2 \dots) \quad (7.23)$$
```

$x_i$ 代表以其为中心的一组等间距网点。此外，$\delta_{\Delta}^{(n)}(x_i - x_j)$ 代表迪利克雷类型的 DSC 核。选择 Shannon 核如下：

```
$$\delta_{\Delta, \sigma}(x_i - x_j) = \frac{\sin(\pi/\Delta)}{(\pi/\Delta)(x_i - x_j)} \exp\left(-\frac{1}{2}\left\{(x_i - x_j)/\sigma\right\}^2\right) \quad (7.24)$$
```

$\sigma$ 和 $\Delta$ 分别是正则参数和网间距。它们的比例由离散参数固定（$r=\sigma/\Delta$）。可以通过等.(7.25)获得合适的 $r$，该式由 Wei 等人 [28] 提出：

```
$$r(\pi - B\Delta) > \sqrt{4.6\mu}, M/r > \sqrt{4.6\mu} \quad (7.25)$$
```

通过 DSC 方法，$F(x)$ 关于 $x_i$ 的一阶和二阶导数写如下：

```
$$F^{(1)}(x_i) = F_i^{(1)} \approx \sum_{j=i-M}^{i+M} \phi_{\Delta}^{(1)}(x_i - x_j)F(x_j) = \sum_{j=i-M}^{i+M} A_{ij}F_j \quad (7.26)$$
```

```
$$F^{(2)}(x_i) = F_i^{(2)} \approx \sum_{j=i-M}^{i+M} \phi_{\Delta}^{(2)}(x_i - x_j)F(x_j) = \sum_{j=i-M}^{i+M} B_{ij}F_j$$
```

关于 DSC 方法的更多细节，请查看参考文献 [17] 和 [28]。

