
如下：

$$\tilde{x}_b = x_b + \frac{i}{\omega}\int_0^{x_b} d_b(\eta)d\eta \quad (b=1,2,3), \tag{A.101}$$

其中 $d_b(x_b)$ 为衰减因子。我们假设衰减因子在主计算域内为零 [即 $d_b(x_b)=0$]，在吸收区为正 [即 $d_b(x_b)>0$]。衰减因子的典型形式为

$$d_b(x_b) = \left(\frac{x_b}{L}\right)^2 d_0 \tag{A.102}$$

其中

$$d_0 = \frac{3V_{P,\max}\log(R_c)}{2L}, \tag{A.103}$$

其中 $L$ 为 PML 层的厚度，$R_c$ 为目标理论反射系数，通常取为 0.001。

通过如下方式写出应力与质点速度方程 (A.43) 和 (A.44) 的空间导数：

$$\frac{\partial}{\partial\tilde{x}_b} = \frac{1}{\varepsilon_b}\frac{\partial}{\partial x_b}, \tag{A.104}$$

其中

$$\varepsilon_b(x_b,\omega) = 1 + i\frac{d_b(x_b)}{\omega}, \tag{A.105}$$

并对方程 (A.43) 和 (A.44) 关于时间进行傅里叶变换，我们得到

$$-i\omega v_a(\mathbf{x},\omega) = \sigma(\mathbf{x})\frac{1}{\varepsilon_b(x_b,\omega)}\frac{\partial\tau_{ab}(\mathbf{x},\omega)}{\partial x_b} \tag{A.106}$$

$$-i\omega\tau_{\alpha\beta}(\mathbf{x},\omega) = c_{\alpha\beta\eta\zeta}(\mathbf{x})\frac{1}{\varepsilon_\eta(x_\eta,\omega)}\frac{\partial\nu_\zeta(\mathbf{x},\omega)}{\partial x_\eta}. \tag{A.107}$$

请注意，我们并未为傅里叶变换后的物理量定义新的符号，而是使用带不同参数的同一符号，因为上下文已明确指示当前考虑的量。例如，$v_a(\mathbf{x},\omega)$ 是 $v_a(\mathbf{x},t)$ 关于时间的傅里叶变换。我们将在本节剩余部分使用此约定。最后，请注意，我们在此未包含源项，因为它们在吸收区通常为零。

为了便于 (A.106) 和 (A.107) 中 PML 方程的代数运算，我们发现重新定义应力场很方便，使得 (A.43) 和 (A.44) 中的方程组与 (A.106) 和 (A.107) 中的方程组具有相同的数学结构。换句话说，我们可以将方程 (A.106) 和 (A.107) 重写如下：

$$-i\omega v_a(\mathbf{x},\omega) = \frac{1}{\varepsilon_1\varepsilon_2\varepsilon_3}\sigma(\mathbf{x})\frac{\partial\tilde{\tau}_{ab}(\mathbf{x},\omega)}{\partial x_b} \tag{A.108}$$

$-i\omega\tilde{\tau}_{\alpha\beta}(\mathbf{x},\omega)=\frac{\varepsilon_1\varepsilon_2\varepsilon_3}{\varepsilon_\beta\varepsilon_\eta}c_{\alpha\beta\xi\eta}(\mathbf{x})\frac{\partial v_\zeta(\mathbf{x},\omega)}{\partial x_\eta}$ , (A.109)

其中

$\tilde{\tau}_{ab}(\mathbf{x},\omega)=\frac{\varepsilon_1\varepsilon_2\varepsilon_3}{\varepsilon_b}\tau_{ab}(\mathbf{x},\omega)$ . (A.110)

请注意张量 $\tilde{\tau}$ 是非对称的（即 $\tilde{\tau}_{ab}\neq\tilde{\tau}_{ba}$）。我们还可以注意到 $\tilde{\tau}=\tau$ 跨越非 PML 区与 PML 区之间的边界，这意味着 $\tilde{\tau}$ 只是 $\tau$ 在 PML 区中的延续。因此，我们可以在方程 (A.108)-(A.109) 中用 $\tau$ 替换 $\tilde{\tau}$，并得到以下 PML 方程：

$-i\omega v_a(\mathbf{x},\omega)=\frac{1}{\varepsilon_1\varepsilon_2\varepsilon_3}\sigma(\mathbf{x})\frac{\partial\tau_{ab}(\mathbf{x},\omega)}{\partial x_b}$ (A.111)

$-i\omega\tau_{\alpha\beta}(\mathbf{x},\omega)=\frac{\varepsilon_1\varepsilon_2\varepsilon_3}{\varepsilon_\beta\varepsilon_\eta}c_{\alpha\beta\xi\eta}(\mathbf{x})\frac{\partial v_\zeta(\mathbf{x},\omega)}{\partial x_\eta}$ . (A.112)

由于我们的有限差分模拟在时域进行，我们必须通过对时间进行逆傅里叶变换将方程 (A.111)-(A.112) 转换回时域。由于系数 $\varepsilon_j=\varepsilon_j(x_j,\omega)$ 的频率依赖性，结果方程中会出现时域卷积算子。这些时域卷积算子必须被消除或修改，以适应我们此处有限差分解在时间上是递归的这一事实（即在给定时间波场的计算显式依赖于更早时间的波场值），而标准时域卷积运算不是递归的。它们是对时间的求和。消除 PML 方程中的时域卷积算子的一种方法是把方程 (A.111)-(A.112) 分解为新的方程，每个方程中只有一个因子 $\varepsilon_b$。为了说明这种方法，让我们考虑以下表达式：

$w_{ab}(\mathbf{x},\omega)=\varepsilon_b(x_b,\omega)v_a(\mathbf{x},\omega)=\left[1+i\frac{d_b(x_b)}{\omega}\right]v_a(\mathbf{x},\omega)$ , (A.113)

这在时域中是一个卷积。通过将此表达式乘以 $-i\omega$，我们消除了卷积算子；即

$-i\omega w_{ab}(\mathbf{x},\omega)=-i\omega v_a(\mathbf{x},\omega)+d_b(x_b)v_a(\mathbf{x},\omega)$ , (A.114)

这对应于

$\frac{\partial w_{ab}(\mathbf{x},t)}{\partial t}=\frac{\partial v_a(\mathbf{x},t)}{\partial t}+d_b(x_b)v_a(\mathbf{x},t)$ . (A.115)

这一思想由 Oskooi 和 Johnson (2011) 针对 Maxwell 方程的 PML 解提出。为了将这一思想推广到弹性情况，我们需要对方程 (A.111)-(A.112) 进行分解。虽然 (A.111) 的分解是显而易见的，但 (A.112) 的分解需要更多注意，因为该方程中存在阻尼因子的比值。实际上，该比值是两个阻尼因子的乘积；即

$$\frac{\varepsilon_1\varepsilon_2\varepsilon_3}{\varepsilon_\eta} = \varepsilon'_\eta\varepsilon''_\eta = \begin{cases} \varepsilon_2\varepsilon_3 & \text{if } \eta = 1 \\ \varepsilon_3\varepsilon_1 & \text{if } \eta = 2 \\ \varepsilon_1\varepsilon_2 & \text{if } \eta = 3 \end{cases}$$ (A.116)

其中 $\varepsilon'_\eta \equiv \{\varepsilon_2, \varepsilon_3, \varepsilon_1\}$ 且 $\varepsilon''_\eta \equiv \{\varepsilon_3, \varepsilon_1, \varepsilon_2\}$。这一思想由 Oskooi 和 Johnson (2011) 针对 Maxwell 方程的 PML 解提出。利用方程 (A.111)-(A.112)，我们可以将方程 (A.111) 和 (A.112) 分解如下：

$$-i\omega\varepsilon_1 w_{a1}(\mathbf{x},\omega) = \sigma(\mathbf{x})\frac{\partial \tau_{ab}(\mathbf{x},\omega)}{\partial x_b} ,$$ (A.117)

$$-i\omega\varepsilon_2 w_{a2}(\mathbf{x},\omega) = -i\omega w_{a1}(\mathbf{x},\omega) ,$$ (A.118)

$$-i\omega\varepsilon_3 v_a(\mathbf{x},\omega) = -i\omega w_{a2}(\mathbf{x},\omega) ,$$ (A.119)

$$-i\omega e_{\xi\eta;1}(\mathbf{x},\omega) = -i\omega\varepsilon'_\eta\frac{\partial v_\zeta(\mathbf{x},\omega)}{\partial x_\eta} ,$$ (A.120)

$$-i\omega e_{\xi\eta;2}(\mathbf{x},\omega) = -i\omega\varepsilon''_\eta e_{\xi\eta;1}(\mathbf{x},\omega) ,$$ (A.121)

$$-i\omega\varepsilon_\beta \tau_{\alpha\beta}(\mathbf{x},\omega) = c_{\alpha\beta\zeta\eta}(\mathbf{x}) e_{\xi\eta;2}(\mathbf{x},\omega) .$$ (A.122)

通过对这些方程关于时间进行逆傅里叶变换，我们可以推导出时域中的 PML 方程；即

$$\frac{\partial w_{a1}(\mathbf{x},t)}{\partial t} + d_1(x_1) w_{a1}(\mathbf{x},t) = \sigma(\mathbf{x})\frac{\partial \tau_{ab}(\mathbf{x},t)}{\partial x_b} ,$$ (A.123)

$$\frac{\partial \tau_{\alpha\beta}(\mathbf{x},t)}{\partial t} + d_{\beta}(x_{\beta})\tau_{\alpha\beta}(\mathbf{x},t) = c_{\alpha\beta\gamma\eta}(\mathbf{x})e_{\gamma\eta;2}(\mathbf{x},t) , \tag{A.128}$$

其中 d' = [d₂(x₂), d₃(x₃), d₁(x₁)]ᵀ 且 d'' = [d₃(x₃), d₁(x₁), d₂(x₂)]ᵀ。这些方程可使用 (A.54) 和 (A.59) 中的有限差分算子求解，就像我们之前对非 PML 方程 (A.43) 和 (A.44) 所做的那样。

现在让我们看一个 PML 边界条件的数值例子。我们首先回顾由 Cerjan et al. (1985) 引入的吸收边界，直到最近它一直是首选方法。我们回顾该解的原因是，Cerjan 解与 PML 解之间的对比很好地表明了 PML 解的精度和有效性。Cerjan 边界条件，也称为阻尼边界条件，是通过在数值模型周围包围一层网格条带创建的。应力和质点速度场乘以因子

$$G(i) = \exp\left\{ -\left[\frac{\alpha}{iabmax}(iabmax - i)\right]^2\right\} \quad \text{for } 1 \le i \le iabmax , \tag{A.129}$$

其中 iabmax 为网格点数表示的条带宽度，α 为通过试错确定的常数，用于获得最佳吸收边界条件。对于 iabmax = 60 个网格点，α 的最佳值为 0.3。图 A.4 中的结果基于这些值。该例中的模型为二维，线源。

现在转向 PML 边界条件。首先，我们注意到在二维介质且线源的情况下，方程 (A.123)-(A.128) 简化为

$$\frac{\partial w_1(\mathbf{x},t)}{\partial t} + d_1(x_1)w_1(\mathbf{x},t) = \sigma(\mathbf{x})\left[ \frac{\partial \tau_{11}(\mathbf{x},t)}{\partial x_1} + \frac{\partial \tau_{13}(\mathbf{x},t)}{\partial x_3} \right] \tag{A.130}$$

$$\frac{\partial w_3(\mathbf{x},t)}{\partial t} + d_1(x_1)w_3(\mathbf{x},t) = \sigma(\mathbf{x})\left[ \frac{\partial \tau_{31}(\mathbf{x},t)}{\partial x_1} + \frac{\partial \tau_{33}(\mathbf{x},t)}{\partial x_3} \right] \tag{A.131}$$

$$\frac{\partial v_1(\mathbf{x},t)}{\partial t} + d_3(x_3)v_1(\mathbf{x},t) = \frac{\partial w_1(\mathbf{x},t)}{\partial t} \tag{A.132}$$ $$\frac{\partial v_3(\mathbf{x},t)}{\partial t} + d_3(x_3)v_3(\mathbf{x},t) = \frac{\partial w_3(\mathbf{x},t)}{\partial t} \tag{A.133}$$ $$\frac{\partial e_{11}(\mathbf{x},t)}{\partial t} = \frac{\partial}{\partial t}\left[ \frac{\partial v_1(\mathbf{x},t)}{\partial x_1} \right] + d_3(x_3)\left[ \frac{\partial v_1(\mathbf{x},t)}{\partial x_1} \right]$$ $$\frac{\partial e_{13}(\mathbf{x},t)}{\partial t} = \frac{\partial}{\partial t}\left[ \frac{\partial v_1(\mathbf{x},t)}{\partial x_3} \right] + d_1(x_1)\left[ \frac{\partial v_1(\mathbf{x},t)}{\partial x_3} \right]$$ $$\frac{\partial e_{31}(\mathbf{x},t)}{\partial t} = \frac{\partial}{\partial t}\left[ \frac{\partial v_3(\mathbf{x},t)}{\partial x_1} \right] + d_3(x_3)\left[ \frac{\partial v_3(\mathbf{x},t)}{\partial x_1} \right] \tag{A.134}$$

