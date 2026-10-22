
ical 谐波计算。还请注意，木星的总半径几乎为 70,000 公里。

与其被分解，云层在木星大气中可持续数千年甚至数百万年。这是因为木星大气非常寒冷，约为 -110 摄氏度。在该温度下，气体分子几乎不移动，原子移动也很缓慢。此外，木星具有较大的重力（即 g_jupiter ≈ 2.5g_earth），它会将大气拉拢在一起。泰坦能够维持相当大的大气，因为其大气非常寒冷，-180 摄氏度。尽管其重力较低，泰坦仍能做到这一点。很明显，木星磁层对其大气免受太阳风侵袭的屏蔽作用以及其远离太阳的距离（木星与太阳的距离是太阳与地球距离的 9 倍）对于维持木星大气中云层数千年至关重要。吹动木星云层的太阳风在该距离下要弱得多，再加上其磁屏蔽。

## 6.4.4. 对流不稳定性与恒星中的能量传输

如第 2 章所述，我们经常遇到从下方加热的流体，因此上方更冷（例如，地球核心加热地球地幔底部；地球大气从地球表面受热；太阳辐射区加热太阳对流区底部等）。这一过程导致温度梯度：底部较轻/较热。与下一小节将讨论的吸积类似，对流是天体中的基本过程。例如，对流是恒星内部能量传输的核心。这里的问题是，在什么条件下这种逆温度梯度变得不稳定，产生被称为热对流的翻转运动。请注意，RTI 是对流不稳定性的一个例子（Kruskal and Schwarzschild, 1954）；在此我们将 RTI 计算推广到连续分层的 MHD 流体。即

```
ρ = ρ₀(z) + δρ , p = p₀(z) + δp , B = B₀(z) + δB , and v = δv   (6.222)
```

```
-1 (dρ₀/dz + dB₀²/dz) = g  ⇌  -1 dρ₀/dz = g ,   (6.223)
```

```
∂/∂t (p / ρ^γ) = 0  ⇒  ρ₀ (α² + k²) 1/ρ₀ ∂ρ/∂t = γ/ρ₀ ∂ρ/∂t  ⇒  δp/ρ₀ = γ δρ/ρ₀ ,   (6.224)
```

### WKB 近似。

这些扰动产生拉格朗日垂直位移 ξ，描述于 (6.184)。正如我们在先前推导不稳定性时所做的那样，我们希望通过对 (6.184) 关于 z 取傅里叶变换并消除 ξ = ξ_z 的导数来确定该方程的色散关系，并利用所得色散仅依赖于 ω² 这一事实，该值必须为正，否则我们会有不稳定性（即 ω² < 0）。不幸的是，此处这样的计算并不容易进行，因为背景等离子体是深度依赖的，因此 (6.184) 中背景量与垂直位移的乘积会在 k_z 波数上产生不期望的卷积。我们可以数值求解 (6.184)。或者，通过假设 ξ 在与背景尺度相比的极小尺度上变化，我们可以使用 WKB（Wentzel–Kramers–Brillouin）近似（Dingle, 1973; Bleistein, 1984; Ikelle et al., 1988; and Ikelle, 1995; and Ikelle and Amundsen, 2005）来求解该方程；即

$$\frac{d}{dz}\left[ f'(z,\omega^2)\frac{d\xi}{dz}\right] - g'(z,\omega^2)\xi \approx \left[\alpha^2 f'(z,\omega^2)+g'(z,\omega^2)\right]\xi ,\tag{6.225}$$

under the assumption that ξ has the following form

$$\xi(z,\omega)=\beta(z,\omega)\exp\left[-i\int_{z_0}^{z}\alpha(s)ds\right] ,\tag{6.226}$$

where f'(z,ω²) and g'(z,ω²) are two arbitrary functions, α represents a local “wavenumber” in the z-direction and β represents the amplitude of ξ. The implication in (6.225) leads to a local dispersion equation. This approximation is valid here because the equilibrium state allows us to assume that the background pressure and density variations are very smooth. We will first study them in HD and then in MHD.

### HD Schwarzschild 对流稳定判据。

与 (6.170) 相关的局部色散方程，例如，简化为

$$\alpha^2 = -\frac{g'}{f'} = \frac{-k_0^2\rho_0\left(\omega^2 - N_B^2\right)}{\rho_0\omega^2}\tag{6.227}$$

which implies that

$$\omega^2 = \frac{k_0^2}{k_0^2 + \alpha^2} N_B^2 ,\tag{6.228}$$

where N_B is the Brunt–Väisälä frequency in (6.171). So instability just appears to depend on the square of the Brunt–Väisälä frequency: N_B² ≥ 0. It is assumed that the magnetic field is zero and that fluid is incompressible and static in order to reach this result.

验证 (6.234) 中结果的有效方法是通过基于热力学论证的第 2 章中的类似结果进行比较。理想气体服从 p = (ℛ/μ)ρT。如果我们将气体团块向上移动一小段距离 dz，则压力的变化为

$$\frac{dp_0}{dz}= \frac{p_0}{T}\frac{dT}{dz}+ \frac{p_0}{\rho_0}\frac{d\rho_0}{dz} \iff \frac{1}{\rho_0}\frac{dp_0}{dz}= \frac{1}{p_0}\frac{dp_0}{dz} - \frac{1}{T}\frac{dT}{dz} .\tag{6.229}$$

By substituting (6.229) in (6.171) and assuming that μ is constant, we obtain

```
N_B² = -g (1/ρ₀ dρ₀/dz - 1/γρ₀ dρ₀/dz)
= -g (1/ρ₀ dρ₀/dz - 1/T dT/dz - 1/γρ₀ dρ₀/dz)
= g/T [dT/dz - (1 - 1/γ) T dρ₀/dz / ρ₀] . (6.230)
```

The last equality here allows us to express the Brunt-Väisälä frequency in terms of the equilibrium temperature gradient. We can see that

```
N_B² ≥ 0 ⇒ dT/dz ≥ (1 - 1/γ) T dρ₀/dz / ρ₀ or (1/T) dT/dz ≥ (1 - 1/γ) (1/ρ₀) dρ₀/dz . (6.231)
```

如第 2 章所述，我们得到对流稳定性的 Schwarzschild 判据。它比较天体（例如恒星）的热梯度与绝热梯度。如果该不等式成立，则所考虑的天体区域内没有对流。对流开始于该不等式被违反时；N_B² < 0。换句话说，N_B² ≥ 0 实际上是对流稳定性的 Schwarzschild 判据。例如，在太阳的外层，冷却如此强烈，以至于温度梯度的绝对值超过绝热温度梯度。这是 Schwarzschild 对流稳定判据给出的阈值。因此，对流不稳定性的条件是

```
dlnρ₀ / dlnT < γ / (γ - 1) . (6.232)
```

对于单原子气体，γ = 5/3 且 dlnρ₀/dlnT < 2.5。

### MHD Schwarzschild 静止等离子体对流稳定判据。

我们现在加入磁场以寻求 Schwarzschild 稳定判据的修正版本，使用 (6.174) 而不是 (6.170)。与 (6.174) 相关的局部色散为

```
α² = -g'/f = -k₀² (ω² - ω_A² - N_M²) / ρ₀ (ω² - ω_A²) (6.233)
```

which implies that

```
ω² = ω_A² + k₀² N_M² / (k₀² + α²) , (6.234)
```

where N_M is the magnetically modified Brunt-Väisälä frequency in (6.172) because it now contains magnetic contribution. Two conditions must be fulfilled to reach convection instability:

```
N_M² < 0 and |N_M| > ω_A (6.235)
```

is a cross-over of two branches of the local dispersion equation with the solutions.

### MHD Schwarzschild 定常等离子体对流稳定判据

我们现在考虑天体的运动以及磁场。我们寻求 Schwarzschild 稳定判据的修正版本，使用 (6.176)。与 (6.176) 相关的局部色散方程为

```
\alpha^2 = -\frac{g'}{f'} = \frac{-k_0^2 \rho_0 (\tilde{\omega}^2 - \omega_A^2 - N_M^2)}{\rho_0 (\tilde{\omega}^2 - \omega_A^2)}
```

which implies that

```
\tilde{\omega}^2 = \omega_A^2 + \frac{k_0^2 N_M^2}{k_0^2 + \alpha^2}
```

or

```
\omega = k_0 v \pm \sqrt{k_0^2 v^2 + \omega_A^2 + \frac{k_0^2 N_M^2}{k_0^2 + \alpha^2}}
```

where $N_M$ is the magnetically modified Brunt-Väisälä frequency in (6.172) because it now contains magnetic contribution. Two conditions must be fulfilled to reach convection instability:

```
N_M^2 < 0 \quad \text{and} \quad |N_M^2| > k_0^2 v^2 + \omega_A^2
```

is a cross-over of two branches of the local dispersion equation with the solutions.

## 6.4.5. 吸积盘与磁旋转不稳定性（MRI）

如 Box 6.1 所述，围绕致密重中央引力天体（例如恒星、行星、中子星和黑洞）的吸积盘由这样一个空间区域组成，其中在旋转物质的引力场中快速旋转的材料在缓慢向内螺旋时将能量和角动量损失给中央天体（见图 6.45）。这些旋转物质包括气体、尘埃和其他已接近中央天体但未落入其中的恒星碎屑。围绕中央天体，吸积物质形成一个扁平带。因此，朝向巨大中央天体运动的气体趋向于圆化，形成盘，并向内向外扩散。这种构型被称为吸积盘（或盘）。天体物理学中的盘的例子包括行星环（例如土星环）、原行星盘（例如 HL Tau）和螺旋盘（例如星系盘）。

吸积盘中的中央天体可以是年轻原恒星（其中 $m_{\rm star} \approx m_{\rm sun}$）、中子星（其中 $m_{\rm star} \approx 1.5 m_{\rm sun}$）和黑洞（其中 $m_{\rm star} \approx 10^9 \times m_{\rm sun}$）——令人难以置信的是，如此范围的天体可以基于我们稍后将看到的相同公式。这些系统之间存在若干显著差异，但它们都涉及吸积。聚变反应堆共享这一吸积特征。实验室聚变装置（托卡马克、恒星器等）以及天体（恒星日冕、吸积盘、星系螺旋臂等）中等离子体的宏观动力学均可由相同的磁流体动力学（MHD）方程描述，该方程是尺度无关的。尽管 MHD 方程的尺度无关性允许通过
