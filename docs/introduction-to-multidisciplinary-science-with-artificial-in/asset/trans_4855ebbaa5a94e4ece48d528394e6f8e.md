

利用 (3.130)，磁矢势可以写成

$$\begin{aligned}
\boldsymbol{A}(\boldsymbol{x}) &= \frac{\mu_0 I}{4\pi} \oint_C d\boldsymbol{l}' \frac{1}{|\boldsymbol{x} - \boldsymbol{x}'|} \\
&= \frac{\mu_0 I}{4\pi} \left\{ \sum_{n=0}^{\infty} \left[ \frac{1}{r^{n+1}} \oint_C (r')^n P_n^0(\cos\gamma) d\boldsymbol{l}' \right] \right\} \\
&= \frac{\mu_0 I}{4\pi} \left\{ \frac{1}{r} \oint_C d\boldsymbol{l}' + \frac{1}{r^2} \oint_C r' \cos\gamma \, d\boldsymbol{l}' \right. \\
&\quad + \left. \frac{1}{r^3} \oint_C (r')^2 \left( \frac{3}{2} \cos^2\gamma - \frac{1}{2} \right) d\boldsymbol{l}' + \dots \right\} .
\end{aligned}$$

式 (3.131) 中的最后一个等式以多极展开的形式给出，是在假设距离 $|\boldsymbol{x} - \boldsymbol{x}'|$ 很大时得到的。第一项称为单极项，因为对任意闭合回路 $d\boldsymbol{l}'$ 的线积分都为零，所以它为零。第二项称为偶极项，通常是多极展开中的主导项。第三项称为四极项。偶极项产生的矢势为

$$\boldsymbol{A}_{\text{dipole}}(\boldsymbol{x}) = \frac{\mu_0}{4\pi} \frac{\boldsymbol{m} \times \boldsymbol{x}}{|\boldsymbol{x}|^2} \Longrightarrow \boldsymbol{B}_{\text{dipole}}(\boldsymbol{x}) = \nabla \times \boldsymbol{A}_{\text{dipole}}(\boldsymbol{x}) , \qquad (3.131)$$

其中 $\boldsymbol{m}$ 称为电流回路的磁偶极矩。其定义为

$$\boldsymbol{m} = \frac{1}{2} I \oint_C (\boldsymbol{x}' \times d\boldsymbol{l}') . \qquad (3.132)$$

对于相对于回路尺寸很远的点，偶极近似是很好的。因此，磁矢势与标量引力势和电势的一个重要区别是，磁矢势不包含单极项。这也是另一种证实地球表面我们仍然无法找到磁单极子的方式。

为完整起见，我们也可以用体积分代替线积分来得到磁多极。利用表 3.1 和 3.10 中定义的电流密度 $\boldsymbol{J}$，我们可以将磁势改写为电流密度 $\boldsymbol{J}$ 的体积分，并展开结果以得到磁多极；即，

$$\begin{aligned}
A_i(\boldsymbol{x}) &= k_M \int \frac{J_i(\boldsymbol{x}')}{|\boldsymbol{x} - \boldsymbol{x}'|} dV(\boldsymbol{x}') \\
&\approx \underbrace{\frac{k_M}{|\boldsymbol{x}|} \left[ \int_V J_i(\boldsymbol{x}') dV(\boldsymbol{x}') \right]}_{\text{Monopole}} + \underbrace{\frac{k_M}{|\boldsymbol{x}|^2} \left[ \int_V J_i(\boldsymbol{x}') x^{(j)'} dV(\boldsymbol{x}') \right] \mathbf{i}_j}_{\text{Dipole}} \\
&\quad + \underbrace{\frac{k_M}{2|\boldsymbol{x}|^3} \left[ \int_V J_i(\boldsymbol{x}') \left( 3 x_i^{(j)'} x_i^{(k)'} - \delta_{jk}|\boldsymbol{x}'_i|^2 \right) dV(\boldsymbol{x}') \right] \mathbf{i}_j \mathbf{i}_k + \dots}_{\text{Quadrupole}}
\end{aligned}$$

其中 k_M = μ0/(4π) 且 A_i 是矢量 A 的 i 分量。因此我们可以看出，磁矢势的领先阶贡献由下式给出

$A_i \approx k_M \int_V J_i(\mathbf{x}') dV(\mathbf{x}') = k_M \int_V [\nabla \cdot (x'_i \mathbf{J}) - x'_i \nabla \cdot \mathbf{J}] dV(\mathbf{x}') = 0.$

我们在这些推导中使用了连续性方程（即 ∇·J = 0）。这是单极项；单极矩只是总电流。对于静态电流分布，总电流总是消失的，因为否则电荷会随时间产生净移动。因此，不仅不存在磁单极子，而且也不可能建立一个产生 1/|x| 磁矢势的静态电流分布。对于静态电流分布，磁矢势总是按 1/|x|^2 或更快衰减。偶极项为

$A_i \approx \frac{k_M}{|\mathbf{x}|^2} \left[ \int_V J_i(\mathbf{x}') x^{(j)\prime} dV(\mathbf{x}') \right] \mathbf{i}_j . \tag{3.133}$

方括号中的对象是一个二阶张量；它有两个自由指标：i 和 j。这个二阶张量是磁偶极矩。同样，磁四极矩是一个三阶张量；它有三个自由指标：i、j 和 k。

### 示例：圆形电流回路产生的磁场。
考虑 x−y 平面内半径为 a 的圆形回路通有恒定电流 I，如图 3.22b 所示。利用图 3.22b 中的定义，我们有

$\mathbf{l}' = a(\cos\theta \mathbf{i}_1 + \sin\theta \mathbf{i}_2) \implies d\mathbf{l}' = a d\theta(-\sin\theta \mathbf{i}_1 + \cos\theta \mathbf{i}_2) \tag{3.134}$

并且

$\frac{(\mathbf{x} - \mathbf{x}')}{|\mathbf{x} - \mathbf{x}'|^3} = \frac{-a\cos\theta \mathbf{i}_1 - a\sin\theta \mathbf{i}_2 + z \mathbf{i}_3}{[a^2 + z^2]^{3/2}} , \tag{3.135}$

其中 $\mathbf{x} = [0,0,z]^T$ 且 $\mathbf{x}' = a[\cos\theta, \sin\theta, 0]^T$。由 (3.124) 可推导出半径为 a、电流为 I 的圆形回路轴线上距离 z 处的磁场如下：

$\mathbf{B} = \frac{\mu_0 I}{4\pi} \int_0^{2\pi} d\theta \frac{(-\sin\theta \mathbf{i}_1 + \cos\theta \mathbf{i}_2) \times (-\cos\theta \mathbf{i}_1 - \sin\theta \mathbf{i}_2 + z \mathbf{i}_3)}{a[1 + (z/a)^2]^{3/2}} = \frac{\mu_0 a I}{4\pi} \int_0^{2\pi} d\theta \frac{z\cos\theta \mathbf{i}_1 + z\sin\theta \mathbf{i}_2 + a \mathbf{i}_3}{a[1 + (z/a)^2]^{3/2}} = \mathbf{i}_3 \frac{\mu_0 I}{2a[1 + (z/a)^2]^{3/2}} . \tag{3.136}$

记住 $\mathbf{i}_1 \times \mathbf{i}_3 = -\mathbf{i}_2$，$\mathbf{i}_2 \times \mathbf{i}_3 = \mathbf{i}_1$，且 $\mathbf{i}_2 \times \mathbf{i}_1 = -\mathbf{i}_3$。$\mathbf{B}$ 的 x 和 y 分量为零。因此，我们看到 $B_z$ 是磁场的唯一非零分量。这一结论也可以通过对称性论证得到。

### 示例：螺线管（螺旋线圈）产生的磁场。
考虑长度为 l、匝数为 N（圈）的螺线管。螺线管可以被视为堆叠

![](img/f5b5b8709fc3a81631262f22d3552c5e_379_0.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_379_1.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_379_2.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_379_3.png)

图 3.22. (a) 单根导线的磁场。载有电电流的长直导线周围磁场的形状。(b) 将导线环绕会使磁场变为环形（甜甜圈）形状。(c) 缠绕在螺线管上的线圈。(d) 基于式 (3.122) 中安培定律计算理想无限长螺线管内部磁场强度的矩形路径示意图。

沿 z 轴的圆形线圈，如图 3.22c 所示。z 与 z + dz 之间的匝数为 N dz / l = n dz，其中 n 为缠绕在半径为 a 的圆柱管上的单位长度匝数。这些匝数所承载的电流为 n I dz。根据前一示例的结果，P 点处由

$z$ 与 $z+dz$ 之间的匝数产生的场为

$$d\boldsymbol{B}=\boldsymbol{i}_3\frac{\mu_0 a^2}{2[a^2+(z-h)^2]^{3/2}}(n I dz)\tag{3.137}$$

根据图 3.22c 中的定义，我们有

$$z-h=\frac{a}{\tan\theta}\Longrightarrow dz=-\frac{a}{\sin^2\theta}d\theta\tag{3.138}$$

并且

$$\frac{a^2}{[a^2+(z-h)^2]^{3/2}}=\frac{\sin^3\theta}{a}\tag{3.139}$$

将 (3.137) 在螺线管全长上积分，我们得到

$$\boldsymbol{B}=\boldsymbol{i}_3\frac{\mu_0 n I}{2}\int_{-l/2}^{l/2}\frac{a^2}{[a^2+(z-h)^2]^{3/2}}dz$$

$$= -\boldsymbol{i}_3\frac{\mu_0 n I}{2}\int_{\theta_1}^{\theta_2}\sin\theta\,d\theta=\boldsymbol{i}_3\frac{\mu_0 n I}{2}[\cos\theta_1-\cos\theta_2]\tag{3.140}$$

对于无限长螺线管，$\theta_1=0$ 且 $\theta_2=\pi$，我们得到

$$\boldsymbol{B}=\boldsymbol{i}_3\mu_0 n I=\boldsymbol{i}_3\frac{\mu_0 N I}{l}\tag{3.141}$$

这些结果对螺线管内部的点有效，但在螺线管外部 $|\boldsymbol{B}|=0$。

我们也可以利用式 (3.122) 中的安培定律计算理想无限长螺线管内部的磁场强度。我们选择一条长度为 $l$、宽度为 $w$ 的矩形路径，如图 3.22d 所示，部分路径在螺线管内部，部分在外部。沿此回路的 $\boldsymbol{B}$ 线积分为

$$\oint_C \boldsymbol{B}(\boldsymbol{x})\cdot d\boldsymbol{l}(\boldsymbol{x})=\int_h^i \boldsymbol{B}(\boldsymbol{x})\cdot d\boldsymbol{l}(\boldsymbol{x})=B l\tag{3.142}$$

假设 $\boldsymbol{B}$ 场为常数。沿路径 $ij$ 和 $kh$ 的贡献为零，因为沿这些路径 $\boldsymbol{B}$ 与 $d\boldsymbol{l}$ 正交。我们假设外部路径 $jk$ 相对于螺线管直径足够远，以至于对于理想螺线管——无限长且匝数紧密排列——场近似为零。我们可以推导出

$$\oint_C[\boldsymbol{B}(\boldsymbol{x})\cdot d\boldsymbol{l}(\boldsymbol{x})]=\mu_0 N I\Longrightarrow B=\frac{\mu_0 N I}{l}\tag{3.143}$$

我们利用了穿过积分路径所限定面积的总电流为 $N I$，其中 $N$ 为匝数，$I$ 为回路电流这一事实。因此安培定律的右端为 $\mu_0 N I$。

如图 3.23b 所示，一个回路产生偶极形磁场，许多回路形成螺线管形状也产生偶极形磁场（见图 3.23b），与 Ikelle (2023b) 中描述的条形磁铁相似。因此电荷（电流）的运动是磁性的唯一来源，而变化的磁

