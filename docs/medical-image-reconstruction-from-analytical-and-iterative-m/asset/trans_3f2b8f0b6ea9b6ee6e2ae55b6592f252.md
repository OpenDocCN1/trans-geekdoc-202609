

因此，

\(\gamma = 2 \sin^{-1} \left( \frac{\sin \psi}{\sqrt{1 - \left( \frac{\omega_v \sin \theta}{\sqrt{\omega_u^2 + \omega_v^2}} \right)^2}} \right) = 2 \sin^{-1} \left( \frac{\sqrt{\omega_u^2 + \omega_v^2} \sin \psi}{\sqrt{\omega_u^2 + \omega_v^2 - \omega_v^2 \sin^2 \theta}} \right) = 2 \sin^{-1} \left( \frac{\sqrt{\omega_u^2 + \omega_v^2} \sin \psi}{\sqrt{\omega_u^2 + \omega_v^2 \cos^2 \theta}} \right), \quad (5.24)\)

这直接导出了 (5.13)。

![](img/dd555effd38151c67af30d84800c554a_125_0.png)

**Fig. 5.22:** 傅里叶域坐标系对应于图 5.20 所示的两个三维坐标系。一个特殊点标记为 \(\vec{w}\)。

## 5.4.3 三维 Radon 反演公式 (FBP 算法)

三维 Radon 反演公式仅适用于三维平面积分数据：

\(f(x,y,z) = \frac{-1}{8\pi^2} \int\int_{4\pi} \frac{\partial^2 p(s, \vec{\theta})}{\partial s^2} \Big|_{s=\vec{x}\cdot\vec{\theta}} \sin \theta \, d\theta \, d\phi, \quad (5.25)\)

其中 \(\vec{\theta} = (\sin \theta \cos \phi, \sin \theta \sin \phi, \cos \theta)\)，\(\vec{x} = (x, y, z)\)。坐标系如图 5.23 所示。如果对 \(2\pi\) 立体角进行反投影，则应将 \(-1/(8\pi^2)\) 替换为 \(-1/(4\pi^2)\)。

## 5.4.4 针对 Radon 数据的三维反投影-滤波算法

令反投影图像为

b(x,y,z) = \iint_{2\pi} p(s, \overline{\theta}) \bigg|_{s=x \cdot \overline{\theta}} \sin\theta d\theta d\phi.

对于三维 Radon 情况，投影/反投影 PSF 的傅里叶变换为 \(1/(\omega_x^2 + \omega_y^2 + \omega_z^2)\)。因此，图像 \(f(x, y, z)\) 的傅里叶变换可表示为

F(\omega_x, \omega_y, \omega_z) = B(\omega_x, \omega_y, \omega_z) \times (\omega_x^2 + \omega_y^2 + \omega_z^2).

在空间域中，针对 Radon 数据的反投影-滤波算法可表示为

f(x,y,z) = \Delta b(x,y,z) = \frac{\partial^2 b(x,y,z)}{\partial x^2} + \frac{\partial^2 b(x,y,z)}{\partial y^2} + \frac{\partial^2 b(x,y,z)}{\partial z^2},

其中 \(\Delta\) 是拉普拉斯算子。

![](img/dd555effd38151c67af30d84800c554a_126_0.png)

Fig. 5.23: 三维 Radon 反演公式的坐标系。

## 5.4.5 Feldkamp 算法

首先，让我们写下平面探测器扇束 FBP 重建算法，并用极坐标表示图像（参见图 5.24）：

f(r, \varphi) = \frac{1}{2} \int_0^{2\pi} \left(\frac{D}{D-s}\right)^2 \int_{-\infty}^{\infty} \frac{D}{\sqrt{D^2+l^2}} g(l, \beta) h(l'-l) dl d\beta,

其中 \(h(l)\) 是斜坡滤波的卷积核，\(D\) 是焦距，\(g(l, \beta)\) 是扇束投影，\(l\) 是探测器上的线性坐标，\(s = r \sin(\varphi - \beta)\)，且 \(l' = \frac{D r \cos(\varphi - \beta)}{D - r \sin(\varphi - \beta)}\)。在此公式中，\(D/\sqrt{D^2+l^2}\) 是入射角的余弦。实现该算法时，我们先将投影乘以此余弦函数。然后对预缩放数据应用斜坡滤波。最后，执行带有距离相关加权 [D/(D-s)]\(^2\) 的扇束反投影，其中 s 是重建点到虚拟探测器的距离，该虚拟探测器为方便起见被放置在旋转中心。

Feldkamp 算法与此扇束算法几乎相同，区别在于反投影为锥束反投影。斜坡滤波按逐行方式进行。轴向不进行滤波。令轴向为 z 方向（参见图 5.25），则

\( f(r, \phi, z) = \frac{1}{2} \int_{0}^{2\pi} \left( \frac{D}{D-s} \right)^2 \int_{-\infty}^{\infty} \frac{D}{\sqrt{D^2 + l^2 + \tilde{z}^2}} g(l, \tilde{z}, \beta) h(l' - l) dl d\beta. \) (5.30)

在此公式中，\(g(l, \tilde{z}, \beta)\) 是锥束投影，\(D/\sqrt{D^2 + l^2 + \tilde{z}^2}\) 是入射角的余弦，且 \(\tilde{z}\) 和 \(l'\) 在图 5.25 中定义。

![](img/dd555effd38151c67af30d84800c554a_127_0.png)

**Fig. 5.24:** 平面探测器扇束成像几何的坐标系。

## 5.4.6 Tuy 关系

Tuy 于 1983 年发表了一篇论文。在该论文中，他建立了锥束数据与原始图像之间的关系，该关系在作用上类似于中央切片定理。让我们在本节推导此关系。

待成像物体为 f：设锥束焦点轨迹由向量 \(\vec{\Phi}\) 表示，并设 \(\vec{a}\) 为单位向量，表示投影射线的方向。因此，锥束数据可由以下表达式给出：

![](img/dd555effd38151c67af30d84800c554a_128_0.png)

Fig. 5.25: Feldkamp 锥束算法的坐标系。

$g(\bar{\Phi}, \bar{\alpha}) = \int_0^\infty f(\bar{\Phi} + t\bar{\alpha}) dt, ||\bar{\alpha}|| = 1.$

我们现在将单位向量 \(\bar{a}\) 替换为一般三维向量 \(\bar{x}\)，上述二维投影变为扩展的三维函数：

$g(\bar{\Phi}, \bar{x}) = \int_0^\infty f(\bar{\Phi} + t\bar{x}) dt.$

对该函数对 \(\bar{x}\) 进行三维傅里叶变换，并用 \(\bar{\beta}\) 表示频域变量，可得

$G(\bar{\Phi}, \bar{\beta}) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} g(\bar{\Phi}, \bar{x}) e^{-2\pi i x \cdot \bar{\beta}} d\bar{x} = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{0}^{\infty} f(\bar{\Phi}, t\bar{x}) e^{-2\pi i x \cdot \bar{\beta}} dt d\bar{x}.$

令 \(\bar{y} = \bar{\Phi} + tx\)，\(dy = |t|^3 d\bar{x}\)。上述表达式变为

$G(\bar{\Phi}, \bar{\beta}) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{0}^{\infty} f(\bar{y}) e^{\frac{-2\pi i}{t^3} (\bar{y} - \bar{\Phi}) \cdot \bar{\beta}} \frac{1}{|t|^3} dt d\bar{y}.$

令 \(s = 1/t\)，\(ds = (1/t^2) dt\)。则有

G\left(\overline{\Phi}, \overline{\beta}\right) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(\overline{y}) e^{-2\pi i s(\overline{y}-\overline{\Phi})\cdot\overline{\beta}} |s|^3 \frac{1}{s^2} d\overline{y} ds, \tag{5.35}

G\left(\overline{\Phi}, \overline{\beta}\right) = \int_{-\infty}^{\infty} \left( \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(\overline{y}) e^{-2\pi i \overline{y}\cdot(\overline{s}\beta)} d\overline{y} \right) |s| e^{2\pi i s(\overline{\Phi}\cdot\overline{\beta})} ds. \tag{5.36}

认识到内层三重积分是 f 的三维傅里叶变换，即，

F(s) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(\overline{y}) e^{-2\pi i \overline{y}\cdot(\overline{s}\beta)} d\overline{y}, \tag{5.37}

则有

G\left(\overline{\Phi}, \overline{\beta}\right) = \int_{-\infty}^{\infty} F\left(\overline{s}\beta\right) |s| e^{2\pi i s(\overline{\Phi}\cdot\overline{\beta})} ds. \tag{5.38}

接下来，将积分限从 \([0, \infty)\) 改为 \((-\infty, \infty)\)，得到

G\left(\overline{\Phi}, \overline{\beta}\right) = \int_{-\infty}^{\infty} F\left(s\overline{\beta}\right) |s| e^{2\pi i s(\overline{\Phi}\cdot\overline{\beta})} ds + \int_{-\infty}^{\infty} F\left(s\overline{\beta}\right) \frac{is}{i} e^{2\pi i s(\overline{\Phi}\cdot\overline{\beta})} ds. \tag{5.39}

利用三维 Radon 变换的中央切片定理，\(F(s\overline{\beta})\) 是原始图像 f 沿 \(\overline{\beta}\) 方向的平面积分的傅里叶变换。因子 \(|s|\) 是傅里叶域中的斜坡滤波器，因子 \((is)\) 对应于空间域中的导数。上述表达式右侧的两项均为逆傅里叶变换的形式，实际上是卷积。

因此，

G\left(\overline{\Phi}, \overline{\beta}\right) = p_{\overline{\beta}}^{-}(t) * h(t) - ip_{\overline{\beta}}^{-}(t) * \delta'(t), \tag{5.40}

其中 \(i = \sqrt{-1}\)，\(t = \overline{\Phi} \cdot \overline{\beta}\)，\(h(t)\) 是斜坡滤波卷积核

h(t) = \int_{-\infty}^{\infty} |s| e^{2\pi i st} ds \tag{5.41}

且原始图像 f 的 Radon 变换定义为

p_{\overline{\beta}}(t) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(\overline{x}) \delta\left(\overline{x} \cdot \overline{\beta} - t\right) d\overline{x}. \tag{5.42}

式 (5.40) 的左侧与锥束投影相关，右侧与原始图像的平面积分相关。

