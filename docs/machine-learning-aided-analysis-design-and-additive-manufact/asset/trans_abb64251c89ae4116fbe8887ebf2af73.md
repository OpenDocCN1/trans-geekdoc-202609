
其中

```
$$A_{xx}, B_{xx}, D_{xx}, E_{xx}, F_{xx} = b \int \frac{h}{2} E(x,z)(1, z^1, z^2, z^3, z^4) dz$$
```

```
$$A_{xz}, D_{xz}, F_{xz} = b \int \frac{h}{2} G(x,z)(1, z^2, z^4) dz$$
```

(6.26)

如上所述，假设所有孔隙率分布关于梁的中截面对称，因为 $B_{xx}=E_{xx}=0$。此外，文献 [29] 显示弯曲、面内（$u$）和旋转（$\phi$）惯性可以忽略。因此，通过将应力结果（等式6.25）代入控制方程（等式6.21–6.23），可以得到关于参考平面的控制方程：

```
$$\delta u_{ic}: \frac{\partial A_{xx}}{\partial x}\frac{\partial u}{\partial x} + \frac{1}{2}\frac{\partial D_{xx}}{\partial x^2} + A_{xx}\frac{\partial A_{xu}}{\partial x}\frac{\partial \phi}{\partial x} + B_{xx}\frac{\partial B_{xu}}{\partial x}\frac{\partial \phi}{\partial x} = 0$$
```

(6.27)

```
$$\delta \phi: \frac{\partial F_{xx}}{\partial x}\frac{\partial \phi}{\partial x} + F_{xx}\frac{\partial^2 \phi}{\partial x^2} + \frac{\partial F_{xu}}{\partial x}\frac{\partial u}{\partial x} + F_{xu}\frac{\partial^2 u}{\partial x^2} - c_1\frac{\partial H_{xx}}{\partial x}\frac{\partial \phi}{\partial x} - c_1H_{xx}\frac{\partial^2 \phi}{\partial x^2} + c_3\frac{\partial^3 \phi}{\partial x^3} = 0$$
```

```
$$-ADF_{xz} \left(\phi + \frac{\partial w}{\partial x}\right)\frac{\partial A_{xz}}{\partial x} - c_1l_4\frac{\partial w}{\partial x}\frac{\partial \phi}{\partial x} = 0$$
```

(6.28)

```
$$\delta w: \frac{\partial A_{xz}}{\partial x}\frac{\partial w}{\partial x} + \frac{1}{2}\frac{\partial D_{xz}}{\partial x^2} + A_{xz}\frac{\partial A_{xw}}{\partial x}\frac{\partial \phi}{\partial x} + B_{xz}\frac{\partial B_{xw}}{\partial x}\frac{\partial \phi}{\partial x} + A_{xx}\frac{\partial A_{xu}}{\partial x}\frac{\partial w}{\partial x} + \frac{1}{2}\frac{\partial D_{xx}}{\partial x^2}\frac{\partial w}{\partial x} = 0$$
```

```
$$\frac{\partial F_{xz}}{\partial x}\frac{\partial w}{\partial x} + F_{xz}\frac{\partial^2 w}{\partial x^2} + c_1F_{xz}\frac{\partial \phi}{\partial x}\frac{\partial w}{\partial x} - c_1H_{xx}\frac{\partial^2 w}{\partial x^2}\frac{\partial \phi}{\partial x} - 2c_1^2\frac{\partial^2 \phi}{\partial x^2}\frac{\partial w}{\partial x} = 0$$
```

```
$$-c_1^2H_{ss}\frac{\partial^4 w}{\partial x^4} - p_z P_s \frac{\partial^2 w}{\partial x^2} = I_0\ddot{w} - c_1I_0\ddot{\phi} - c_1^2I_0\frac{\partial^2 \phi}{\partial x^2}$$
```

(6.29)

提高多孔梁的稳定性和振动响应

其中

```
$$DF_{xz} = D_{xx} - c_1F_{xx}FH_{xx} = F_{xx} - c_1H_{xx}$$
AD_{xz} = A_{xz} - 2c_2D_{xx} + c_2^2F_{xx}DF_{xx} = D_{xx} - 2c_1F_{xx} + c_1^2H_{xx}$$
```

## 6.4 求解方法

在本节中，采用伽尔金法（Galerkin technique）将控制非线性偏微分方程（等式6.27–6.29）简化一组关于时间的非线性常微分方程（ODE）。此处，当梁处于谐波垂直载荷和恒定轴向压缩载荷的作用下时，检查系统的主共。采用谐波平衡法（HBM）开发系统非线性基频和频率响应的闭式近似解。

## 6.4.1 伽尔金法

为了求解非线性运动方程，首先使用伽尔金法将一组非线性偏微分方程转换为一组非线性常微分方程。广义位移的展开形式如下：

```
$$u = \sum_{n=1}^{\infty} \hat{u}_n(x)\hat{w}_n(t)$$
```

```
$$\phi = \sum_{n=1}^{\infty} \hat{\phi}_n(x)\hat{\phi}_n(t)$$
```

```
$$w = \sum_{n=1}^{\infty} \hat{w}_n(x)\hat{w}_n(t)$$
```

其中 $\hat{u}_n, \hat{\phi}_n$ 和 $\hat{w}_n$ 是需要满足问题边界条件（此处为铰支）的特征函数。同时，$\hat{u}_n, \hat{\phi}_n$ 和 $\hat{w}_n$ 是未知广义坐标。将 $u, \phi, w$ 代入控制方程并应用伽尔金法，得到一组非线性常微分方程：

```
$(k_{1,1} + k_{1,2})\hat{u}_n + (k_{1,3} + k_{1,4})\hat{w}_n^2 = 0$$
```

$(k_{2,1} + k_{2,2} - k_{2,3})\dot{\phi}_n - (k_{2,4} + k_{2,5} + k_{2,6})\ddot{w}_n = -m_{2,1}\frac{d^2\hat{w}_n}{dt^2} \quad (6.35)$

$k_{3,1}\hat{u}_n\hat{w}_n + (k_{3,2} + k_{3,3} + k_{3,4} + k_{3,5})\dot{\phi}_n + (k_{3,7} + k_{3,8} - k_{3,9} - k_{3,10} - k_{3,11})\hat{w}_n + k_{3,12}\frac{d^2\hat{w}_n}{dt^2} = (m_{3,1} - m_{3,2})\ddot{P}_z + \dot{P}_z\dot{w}_n \quad (6.36)$

其中刚度(k)和质量(n)系数定义在附录中。对于等式(34)和(36)，分别将 $u_n$ 和 $\phi_n$ 代入控制方程。随后，通过将 $u_n$ 和 $\phi_n$ 代入控制方程，得到一个降阶常微分方程：

```
$$M\frac{d^2w_n}{dt^2} + (K_i + K_{it})w_n = p_z\ddot{P}_z + \dot{P}_z\dot{w}_n \quad (6.37)$$
```

其中 $K_i, K_{it}$ 和 $M$ 分别是系统的线性刚度、非线性刚度和质量。对于等式(37)，可以得到线性频率：

```
$$\omega_n = \sqrt{\frac{K_i}{M}} \quad (6.38)$$
```

## 6.4.2 谐波平衡法

由于外部载荷是周期性的，可以如下应用用于获取非运动周期解的谐波平衡法（HBM）：

```
$$\hat{w}_n = \sum_{i=1}^{\infty} A_i\cos(i\omega t) + B_i\sin(i\omega t) \quad (6.39)$$
```

将等式(39)代入等式(37)并分离谐波分，可以得到系统的非线性自然频率：

```
$$\Omega = \sqrt{\frac{K_i}{M} \left(1 + \frac{3K_{it}}{4(K_i - P_s)}\right)} \quad (6.40)$$
```

提高多孔梁的稳定性和振动响应

```
$$DF_{xz} = D_{xx} - c_1F_{xx}FH_{xx} = F_{xx} - c_1H_{xx}$$
AD_{xz} = A_{xz} - 2c_2D_{xx} + c_2^2F_{xx}DF_{xx} = D_{xx} - 2c_1F_{xx} + c_1^2H_{xx}$$
```

## 6.5 数值结果与讨论

首先，对文献中的案例进行对比研究以确保当前求解方法的准确性。随后，给出数值示例以研究孔隙分布对双向和单向分布多孔梁稳定性载荷以及自由和响应的影响。假设多孔梁由铝制成，$E_0=702GPa, \nu_0=0.33, \rho_0=2700kg/m3$。此外，考虑了受限边界条件。对于受迫振动情况，所有图均针对第一振型绘制。

### 6.5.1 对比研究

为了证明当前方法的准确性，将单向孔隙分布（UPD）多孔梁的基频与Chen等人[10]在表6.1中报告的结果进行比较。此外，轴向载荷下梁的频率响应曲线与Shojaei等人[46]在图6.3中报告的结果进行比较。材料属性、梁尺寸和无方向参数可以在上述参考文献中找到。这些对比研究表明，当前方法在谐波横向载荷和恒定轴向载荷复合作用下获取梁的线性非线性自然频率及频率响应曲线方面具有良好的准确性。

### 6.5.2 参数研究

图6.4展示了考虑不同类型孔隙分布时自然频率随轴向载荷的变化。