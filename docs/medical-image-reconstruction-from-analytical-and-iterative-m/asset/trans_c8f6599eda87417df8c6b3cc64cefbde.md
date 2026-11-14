

![](img/dd555effd38151c67af30d84800c554a_78_0.png)

图 3.13: 当扇束焦距很短时，均匀圆盘的短扫描扇束 FBP 重建。

![](img/dd555effd38151c67af30d84800c554a_78_1.png)

图 3.14: 由三段组成的扇束焦点轨迹。

## 3.5 算例

### 示例 1：以下扇束几何是否获取了足够的投影数据用于图像重建？扇束焦点轨迹由图 3.14 所示的三段不相交弧组成。

### 解答

是的。若在圆形物体上任意作一条直线，该直线至少与焦点轨迹相交一次。

![](img/dd555effd38151c67af30d84800c554a_79_0.png)

图 3.15: 扇束扫描中的冗余测量。

### 示例 2：在 $\gamma$-$\beta$ 平面上（类似于平行束投影的正弦图），识别扇束 $2\pi$ 扫描中的双重测量。

### 解答

从图 3.15 中，我们可以轻易找到扇束数据冗余条件，即

$$g(\gamma_1, \beta_1) = g(\gamma_2, \beta_2) \quad (3.28)$$

为

$$\gamma_2 = -\gamma_1 \quad (3.29)$$

以及

$$\beta_2 = \beta_1 + 2\gamma_1 + \pi. \quad (3.30)$$

利用这些条件，图 3.16 在 $\gamma$-$\beta$ 平面上描绘了扇束数据冗余，其中每条垂直线对应一条冗余的斜线。

![](img/dd555effd38151c67af30d84800c554a_79_1.png)

图 3.16: 在扇束数据的 $\gamma$-$\beta$ 平面表示中，每条垂直测量线与同色的斜线测量线相同。

### 示例 3：推导平面探测器扇束几何的 FBP 算法。

### 解答

我们从平行束 FBP 算法入手，使用极坐标 ($r, \varphi$) 而非笛卡尔坐标 $(x, y)$。则 $x = r \cos \varphi, y = r \sin \varphi$，且 $x \cos \theta + y \sin \theta = r \cos (\theta - \varphi)$。有

$f(r, \varphi) = \frac{1}{2} \int_0^{2\pi} \int_{-\infty}^\infty p(s, \theta) h(r \cos (\theta - \varphi) - s) ds d\theta. \quad (3.31)$

对于平面探测器扇束投影 $g(t, \beta) = p(s, \theta)$，扇束变量与平行束变量的关系由 $\theta = \beta + \tan^{-1} (t/D)$ 和 $s = D(t / \sqrt{D^2 + t^2})$ 给出。将平行束变量变换为扇束变量，雅可比行列式为 $D^3 / (D^2 + t^2)^{3/2}$，可得

$f(r, \varphi) = \frac{1}{2} \int_0^{2\pi} \int_{-\infty}^\infty g(t, \beta) h\left((\hat{t} - t) \frac{UD}{\sqrt{D^2 + t^2}}\right) \frac{D^3}{(D^2 + t^2)^{3/2}} dt d\beta, \quad (3.32)$

其中我们使用了 $r \cos(\theta - \varphi) - s = (\hat{t} - t)(UD / \sqrt{D^2 + t^2})$，并有

$U = \frac{D + r \sin(\beta - \varphi)}{D} \quad (3.33)$

以及

$\hat{t} = \frac{Dr \cos(\beta - \varphi)}{D + r \sin(\beta - \varphi)} \quad (3.34)$

（参见图 3.17）。

![](img/dd555effd38151c67af30d84800c554a_80_0.png)

图 3.17: 平面探测器扇束成像几何的符号说明。

这是一个扇束重建算法，但关于 $t$ 的内积分尚未采用卷积形式。利用斜坡滤波器 $h(at) = (1 / a^2) \ h(t)$ 的特殊性质可得

$$f(r, \varphi) = \frac{1}{2} \frac{1}{U^2} \int_0^{2\pi} \int_{-\infty}^{\infty} \frac{D}{\sqrt{D^2+t^2}} g(t, \beta) h(\hat{t}-t) dtd\beta.$$

这是一种扇束卷积后投影算法，其中 \( D / \sqrt{D^2+t^2} \) 为余弦预加权因子，关于 \( t \) 的积分为斜坡滤波卷积，而 \( 1/U^2 \) 为后投影中的距离相关加权因子。

注意：关系式 \( h(at) = (1/a^2) \ h(t) \) 对于*带窗*斜坡滤波器不成立。因此，当在斜坡滤波器上应用窗函数时，上述推导的扇束算法在实际重建图像中不具有均匀分辨率。

## 3.6 小结

- 扇束几何在 X-ray CT 成像中广泛应用。

- 扇束图像重建算法可通过变量变换从其平行束对应算法推导得到。

- 扇束探测器有两种类型：平面探测器和曲面探测器。每种探测器类型都有其自身的图像重建算法。

- 如果扇束焦点轨迹是整圆，则称为全扫描；如果轨迹是部分圆，则称为短扫描。即使对于短扫描，部分扇束射线也会被测量两次。图像重建过程中冗余测量需要进行适当加权。

- 对于某些扇束图像重建算法，后投影器包含距离相关加权因子。当对斜坡滤波器应用窗函数时，该因子未被窗函数妥善处理，因此得到的扇束 FBP 不再严格（即重建图像具有非均匀分辨率和强度）。若焦距很短，短扫描扇束 FBP 算法可能导致明显误差。

- 基于导数和希尔伯特变换的现代算法能够以正确方式对短扫描冗余数据进行加权。

- 本章中，读者应理解如何从平行束算法得到扇束算法。

## 习题

### 问题 3.1

曲面探测器扇束成像几何的数据冗余条件为

$$g(\gamma, \beta) = g(-\gamma, \beta + 2\gamma + \pi).$$

平面探测器扇束几何的数据冗余条件是什么？

### 问题 3.2

本章中，我们假设 X 射线源（即扇束焦点）沿圆形轨道绕物体旋转。如果焦点轨道不是圆形，则焦距 $D$ 是旋转角 $\beta$ 的函数。将本章中开发的扇束图像重建算法扩展到焦点轨道为非圆形的情况。

### 问题 3.3

本章讨论的开发图像重建算法的方法并不局限于扇束成像几何。例如，我们可以考虑变焦距扇束成像几何，其中焦距 $D$ 可以是 $t$ 的函数，$t$ 是如下图所示的检测单元坐标。将本章中的扇束图像重建算法扩展到这种变焦距扇束成像几何。

![](img/dd555effd38151c67af30d84800c554a_82_0.png)

## 参考文献

- [1] Besson G (1996) 导致不变滤波的 CT 扇束参数化。Inverse Probl 12:815–833.
- [2] Chen GH (2003) 从扇束投影进行图像重建的新框架。Med Phys 30:1151–1161.
- [3] Chen GH, Tokalkanajalli R, Hsieh J (2006) 基于局部补偿滤波后投影 (LCFBP) 等权重方案的精确扇束重建算法的开发与评价。Med Phys 33:475–481.
- [4] Dennerlein F, Noo F, Hornegger J, Lauritsch G (2007) 无后投影权重的扇束滤波后投影重建。Phys Med Biol 52:3227–3240.
- [5] Gullberg GT (1979) 通过滤波后投影重建扇束数据。Comput Graph Image Process 10:30–47.
- [6] Hanajer C, Smith KT, Solomon DC, Wagner SL (1980) 发散束 X 射线变换。Rocky Mt J Math 10:253–283.
- [7] Natterer N (1993) 扇束断层扫描中的采样。SIAM J Appl Math 53:358–380.
- [8] Horn BKP (1979) 扇束重建方法。Proc IEEE 67:1616–1623.
- [9] Noo F, Defrise M, Clackdoyle R, Kudo H (2002) 少于短扫描的扇束投影图像重建。Phys Med Biol 47:2525–2546.
- [10] Pan X (1999) 扇束计算机断层扫描图像中的最优噪声控制与快速重建。Med Phys 26:689–697.
- [11] Pan X, Yu L (2003) 具有随位变滤波的图像重建及其对扇束断层扫描中噪声和分辨率特性的影响。Med Phys 30:590–600.
- [12] Parker DL (1982) 扇束 CT 最优短扫描卷积重建。Med Phys 9:254–257.
- [13] Silver MD (2000) 计算机断层扫描中包含冗余数据的一种方法。Med Phys 27:773–774.
- [14] You J, Liang Z, Zeng GL (1999) 基于指数 Radon 变换 Cormack 类型反演的平行束和变焦距扇束准直器的统一重建框架。IEEE Trans Med Imaging 18:59–65.
- [15] You J, Zeng GL (2007) 基于希尔伯特变换的扇束 CT 全扫描和部分扫描 FBP 算法。IEEE Trans Med Imaging 26:190–199.
- [16] Yu L, Pan X (2003) 具有改进噪声和分辨率特性的半扫描扇束计算机断层扫描。Med Phys 30:2629–2637.
- [17] Wang J, Lu H, Li T, Liang Z (2005) 扇束 FBP 图像重建中非均匀噪声传播问题的替代解法。Med Phys 32:3389–3394.
- [18] Wei Y, Hsieh J, Wang G (2005) 扇束断层扫描的通用公式。Phys Rev Lett 95:258102.
- [19] Wei Y, Wang G, Hsieh (2005) CT 中滤波后投影算法与后投影算法的关系。IEEE Signal Process Lett 12:633–636.
- [20] Wesarg S, Ebert M, Borffeld T (2002) 重访 Parker 权重。Med Phys 29:372–378.
- [21] Zeng GL (2015) 扇束短扫描 FBP 算法不精确。Phys Med Biol 60:N131–N139.
- [22] Zeng GL, Gullberg (1991) 非圆形探测器轨道的短扫描扇束算法。SPIE Med Imaging V Conf, San Jose, CA, 332–340.
- [23] Zou Y, Pan X, Sidky EY (2005) 基于缩减扇束扫描中截断投影的感兴趣区域图像重建。Phys Med Biol 50:13–28.
- [24] Zeng GL (2004) 在扇束计算机断层扫描中使用斜坡滤波器的非均匀噪声传播。IEEE Trans Med Imaging 23:690–695.

