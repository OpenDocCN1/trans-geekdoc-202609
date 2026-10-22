
## 等离子体与磁流体力学

![](img/f5b5b8709fc3a81631262f22d3552c5e_717_0.png)

ʻ欧umuamua 是第一个被探测到穿过太阳系的星际天体。罗伯特·韦里克于 2017 年 10 月 19 日使用夏威夷哈雷阿卡拉天文台的 Pan-STARRS 望远镜发现了它。这距离 ʻ欧umuamua 于 9 月 9 日经过距太阳最近点大约 40 天。当它首次被观测时，它距离地球约 3300 万公里（0.22 天文单位，约是月球的 85 倍远），并且已经远离太阳而去。

图 6.50 显示 ʻ欧umuamua 是一个非常不寻常的天体。它的形状与围绕太阳运行数十亿年的行星、卫星、小行星和彗星都不同。这种极端的细长形状表明 ʻ欧umuamua 可能是 Ikelle (2023b) 第 3 章和 Ikelle (2023a) 第 1 章中描述的风化过程的结果，而非盘吸积。ʻ欧umuamua 的母系系外行星也可能由于这种内部风化过程而具有活跃的构造活动，就像地球一样。

当大量物质聚集在一起时，它们可以在一个致密的中心天体周围旋转并变平。如上所述，吸积盘是宇宙中强大的引擎。此外，吸积盘在宇宙中广泛存在。它们可以将引力能以高效率转化为辐射，效率可达 40%。这一过程可用于地球上制造巨型飞机和航天器，包括我们自己的诺亚方舟版本。这种设计也可以包括学习宇宙中可能形成的吸积盘。

![](img/f5b5b8709fc3a81631262f22d3552c5e_718_0.png)

图 6.50. ʻ欧umuamua 的艺术概念图。它是一个暗红色的、细长的高延展性金属或岩石物体，长约 1,000 英尺（400 米）。改编自 ESO/M. Kornmesser 的图像

其内部有巨大的空隙，就像我们的月球一样，具有显著的空隙（或均质空间），如 Ikelle (2023c 和 2024) 以及第 1 章所述。那么盘吸积过程如何容纳中心天体中间的空洞。如果您曾经尝试挖一个足够大的洞，并为泥土、土壤、碎石或任何东西试图填回洞而苦恼，您就已经知道答案了。引力会把物质拉入以填补空洞。就这么简单。它可能对星际旅行产生重大影响（Ikelle, 2024）。在给定时间内，自然总是选择能耗最小的路径。由于吸积盘广泛存在，我们可以说自然选择了它们作为最佳方法。现代科学技术旨在向自然学习并复制自然的做法。

## 6.5. 广义欧姆定律与磁重联

在介绍公式 (6.85) 时，我们提及了运动流体与静止流体的欧姆定律的差异。实际上，这就是广义欧姆定律与第 3 章中标准欧姆定律之间的区别。这是在理想 MHD（图 6.27）与非理想 MHD（图 6.28）之间的关键区别。本节推导广义欧姆定律。通过使用广义欧姆定律，我们还讨论磁重联和磁单极子。我们将从 MHD 角度重新推导标准欧姆定律，以便于比较两条定律。

### 6.5.1. 电导率的微观解释

让我们分别写出电子和离子的运动方程，即 (6.79)：

```
m_e [∂/∂t + v_e · ∇] (n_e v_e) = -∇p_e - n_e e (E + v_e × B) + m_e n_e ν_ei (v_i - v_e), (6.252)
```

```
m_i [∂/∂t + v_i · ∇] (n_i v_i) = -∇p_i + n_i e (E + v_i × B) - m_e n_i ν_ei (v_i - v_e), (6.253)
```

其中下标 e 用于电子，i 用于离子。我们使用了 ρ_e = m_e n_e、ρ_i = m_i n_i、ρ_e,e = -n_e e 和 ρ_e,i = Z_i n_i e 这一事实，并再次假设 Z_i = 1（即离子为质子）。公式 (6.252) 中的最后一项描述了离子与电子碰撞过程中动量转移的速率。它表示离子与电子之间转移的平均动量，ν_ei 为电子-离子碰撞频率。它与公式 (6.253) 中的最后一项大小相等符号相反，因为动量守恒要求两项符号相反。我们假设没有引力。我们在 (6.252) 和 (6.253) 中未包含离子-离子和电子-电子碰撞的影响，因为同类粒子碰撞不会改变总动量（对该类所有粒子取平均），而异类粒子碰撞会在物种之间交换动量。

现在假设等离子体静止或作匀速运动（粒子加速度为零），且压力和磁场为零。公式 (6.252) 中的运动方程简化为

```
0 = -n_e E - m_e n_e ν_ei v_e  ⇔  J = σ E , (6.254)
```

其中 J = -n_e e v_e = ρ_e,e v_e  且  σ = e² n_e / (m_e ν_ei)  (6.255)

σ 为电导率。该电导率公式使我们能够将第 3 章中定义的宏观量 σ 与微观尺度联系起来。通过增大公式 (6.255) 中的电子粒子数密度 n_e，我们提高等离子体电导率，而通过增大离子-电子碰撞频率 ν_ei，我们提高等离子体电阻率。很明显，定律 J = σ E 在 B ≠ 0、v 不是恒定矢量和/或 p 不是常数时不成立。

现在转向广义欧姆定律的推导：n_i = n_e = n。将方程 (6.252) 乘以 -e/m_e 并加上乘以 e/m_i 的方程 (6.253)，忽略惯性项，即 (v_e · ∇)v_e 和 (v_i · ∇)v_i，我们得到

```
∂/∂t [e n (v_i - v_e)] = - (e/m_i) ∇p_i + (e/m_e) ∇p_e + e² n (1/m_e + 1/m_i) E + e² [ (v_e × B)/m_e + (v_i × B)/m_i ] - e n ν_ei [ (v_i - v_e) - (m_e / m_i) (v_i - v_e) ] . (6.256)
```

由于 $m_i \gg m_e$，则 $e/m_e \gg e/m_i$ 且 $n_e e^2/m_e \gg n_i e^2/m_i$，我们忽略 $m_e/m_i$ 比值量级的微小项。此外，在热平衡下，电子动压与离子压相似（即 $p_e \approx p_i$）。省去这些项后，我们得到广义欧姆定律（Rossi and Olbert, 1970；以及 Greene, 1973），即

$$\frac{\partial \boldsymbol{J}}{\partial t}=\frac{e^2 n}{m_e}[\boldsymbol{E}+(\boldsymbol{v}\times\boldsymbol{B})]-\frac{e}{m_e}(\boldsymbol{J}\times\boldsymbol{B})-\nu_{ei}\boldsymbol{J}+\frac{e}{m_e}\nabla p_e\ ,\qquad (6.257)$$

$$\boldsymbol{J}=\sigma[\boldsymbol{E}+(\boldsymbol{v}\times\boldsymbol{B})]-\frac{\Omega_g^{(e)}}{\nu_{ei}}\frac{\boldsymbol{J}\times\boldsymbol{B}}{B}-\frac{1}{\nu_{ei}}\frac{\partial \boldsymbol{J}}{\partial t}+\frac{e}{m_e}\nabla p_e\ ,\qquad (6.258)$$

或

$$\boldsymbol{E}=-\boldsymbol{v}\times\boldsymbol{B}+\frac{1}{\sigma}\boldsymbol{J}+\frac{\boldsymbol{J}\times\boldsymbol{B}}{e n_e}-\frac{1}{n_e e}\nabla p_e+\frac{m_e}{n e^2}\frac{\partial \boldsymbol{J}}{\partial t}\ ,\qquad (6.259)$$

其中 $\Omega_g^{(e)}=eB/m_e$ 是先前引入的电子回旋运动的电子回旋频率。广义欧姆定律，或更一般地磁流体力学，解释了变化的流动、压力梯度或惯性应力会产生电流。

假设 $\boldsymbol{B}=\mathbf{0}$、电流密度缓慢变化且 $p_e$ 为常数时，广义欧姆定律简化为标准欧姆定律 $\boldsymbol{J}=\sigma\boldsymbol{E}$。如果 $\boldsymbol{B}\neq\mathbf{0}$，但电流密度缓慢变化且 $p_e$ 为常数，广义欧姆定律简化为 (6.85)。在理想 MHD 中，等离子体被假设为理想导电，没有电子压力梯度，且电流密度被假设仅缓慢变化。广义欧姆定律简化为 $\boldsymbol{E}=-\boldsymbol{v}\times\boldsymbol{B}$。

假设压力 $p_e$ 为常数且电流密度 $\boldsymbol{J}$ 平滑，方程 (6.258) 变为

$$\boldsymbol{J}=\sigma[\boldsymbol{E}+(\boldsymbol{v}\times\boldsymbol{B})]-\frac{\Omega_g^{(e)}}{\nu_{ei}}\frac{\boldsymbol{J}\times\boldsymbol{B}}{B}\ .\qquad (6.260)$$

可以验证 (6.260) 的解为

$$\boldsymbol{J}=\sigma\boldsymbol{E}_{\parallel}^{(\mathrm{eff})}+\sigma_{\perp}\boldsymbol{E}_{\perp}^{(\mathrm{eff})}+\sigma_{H}\boldsymbol{b}\times\boldsymbol{E}_{\perp}^{(\mathrm{eff})}\qquad (6.261)$$

其中

$$\sigma_{\perp}=\sigma\left[1+\left(\frac{\Omega_g^{(e)}}{\nu_{ei}}\right)^2\right]^{-1}\quad\text{and}\quad\sigma_{H}=\sigma\frac{\Omega_g^{(e)}}{\nu_{ei}}\left[1+\left(\frac{\Omega_g^{(e)}}{\nu_{ei}}\right)^2\right]^{-1}\ ,$$

且 $\boldsymbol{E}^{(\mathrm{eff})}=\boldsymbol{E}+\boldsymbol{v}\times\boldsymbol{B}$，$\boldsymbol{b}=\boldsymbol{B}/B$ 为沿磁场的单位矢量，$\boldsymbol{E}_{\parallel}^{(\mathrm{eff})}$ 为 $\boldsymbol{E}^{(\mathrm{eff})}$ 平行于 $\boldsymbol{b}$ 的分量，$\boldsymbol{E}_{\perp}^{(\mathrm{eff})}$ 为 $\boldsymbol{E}^{(\mathrm{eff})}$ 垂直于 $\boldsymbol{b}$ 的分量。我们可以看到，等离子体中磁场的存在不仅改变电导率的大小。当 $\sigma\neq\sigma_{\perp}$ 时，它还导致等离子体电导率随方向变化。这里的第三项是霍尔电流。
