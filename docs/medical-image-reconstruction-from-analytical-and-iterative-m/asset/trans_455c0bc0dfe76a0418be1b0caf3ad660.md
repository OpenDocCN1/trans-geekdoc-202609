

## Bibliography

[1] Bellini S, Piacenti M, Caffario C, Rocca F (1979) 发射断层扫描中组织吸收的补偿. IEEE Trans Acoustics Speech, Signal Process ASSP 27:213–218.

[2] Bukhgeim AA, Kazantsev SG (2002) 单位圆盘内扇束衰减Radon变换的反演公式, 俄罗斯科学院西伯利亚分院索博列夫数学研究所.

[3] Guillement JP, Novikov R (2004) 单光子发射计算机断层扫描数据的噪声特性分析. Inverse Probl 20:175–198.

[4] Gullberg GT (1979) 衰减Radon变换：医学和生物学中的理论与应用，博士论文，加州大学伯克利分校劳伦斯伯克利实验室，伯克利，加利福尼亚州.

[5] Gullberg GT, Budinger TF (1981) 在单光子发射计算机断层扫描中使用滤波方法补偿恒定衰减. IEEE Trans Biomed Eng 28:142–157.

[6] Hawkins WG, Leichner PK, Yang NC (1988) 用于SPECT重建的圆谐波变换及正弦图傅里叶变换的边界条件. IEEE Trans Med Imaging 7:135–148.

[7] Hsieh J (2003) 计算机断层扫描：原理、设计、伪影与最新进展，SPIE，华盛顿州贝灵厄姆.

[8] Huang Q, Zeng GL, Wu J (2006) 衰减扇束投影Bukhgeim和Kazantsev反演公式的另一种证明. Med Phys 33:3983–3987.

[9] Huang Q, You J, Zeng GL, Gullberg GT (2009) 使用DBH方法从均匀衰减的SPECT投影数据中进行重建. IEEE Trans Med Imaging 28:17–29.

[10] Inouye T, Kose K, Hasegawa A (1988) 均匀衰减单光子发射计算机断层扫描的图像重建算法. Phys Med Biol 34:299–304.

[11] Kunyansky LA (2001) 基于Novikov显式反演公式的新型SPECT重建算法. Inverse Probl 17:293–306.

[12] Markoe A (1984) 衰减X射线变换的傅里叶反演. SIAM J Math Anal 15:718–722.

[13] Metz CE, Pan X (1995) 二维指数Radon变换反演精确方法的统一分析及其对SPECT噪声控制的影响. IEEE Trans Med Imaging 17:643–658.

[14] Natterer F (2001) 衰减Radon变换的反演. Inverse Probl 17:113–119.

[15] Noo F, Wagner JM (2001) 180°采集下的二维SPECT图像重建. Inverse Probl 17:1357–1371.

[16] Novikov RG (2002) 衰减X射线变换的反演公式. Ark Math 40:145–167.

[17] Pan X, Kao C, Metz CE (2002) π方案指数Radon变换族及其反演的唯一性. Inverse Probl 18:825–836.

[18] Puro A (2001) 指数Radon变换的Cormack型反演. Inverse Probl 17:179–188.

[19] Rullgård H (2002) 基于180°数据的指数Radon变换显式反演公式. Ark Math 42:145–167.

[20] Rullgård H (2004) 带180°数据的衰减Radon变换反问题的稳定性. Inverse Probl 20:781–797.

[21] Tang Q, Zeng GL, Gullberg GT (2007) 基于180°采集数据的带恒定衰减补偿的SPECT傅里叶重建算法. Phys Med Biol 52:6165–6179.

[22] Tretiak O, Metz CE (1980) 指数Radon变换. SIAM J Appl Math 39:341–354.

[23] You J, Zeng GL, Liang Z (2005) 衰减扇束投影的FBP算法. Inverse Probl 21:1179–1192.

[24] Wang G, Lin T, Cheng P, Shinozake DM, Kim HG (1991) X射线微断层扫描的扫描锥束重建算法. Proc SPIE 1556:99–112.

[25] Wang G, Yu H, DeMan B (2008) X射线CT研究与发展的展望. Med Phys 35:1051–1064.

[26] Webster JG (1998) 医学仪器：应用与设计，第3版，Wiley，纽约.

[27] Wolbarst AB (1993) 放射物理学，Appleton and Lange，康涅狄格州诺沃克.

[28] Zeng GL, Gullberg GT (2009) 带截断透射数据的精确发射SPECT重建. Phys Med Biol 54:3329–3340.

## 5 三维图像重建

本章主要研究三维断层成像。在三维中，我们将分别考虑平行线积分投影、平行平面积分投影和锥束线积分投影。对于三维平行线积分投影和平行平面积分投影，存在中心切片定理，图像重建算法可由此推导。然而，对于锥束投影，情况则不同；锥束不存在中心切片定理。我们必须以某种方式建立锥束投影与三维图像本身之间的关系。由于锥束图像重建是一个活跃的研究领域，本章在讨论锥束重建算法上投入了大量精力，其中Katsevich算法是最新且最好的一种。

### 5.1 平行线积分数据

在许多情况下，如果投影射线可以分为若干组，且每组仅包含局限于某个横断切片内的射线，则三维图像重建可分解为一系列逐层切片的二维图像重建（参见图5.1，左侧）。

在其他情况下，投影射线穿过横断切片，此时逐层切片的二维重建方法不再适用（参见图5.1，中间和右侧）。

二维平行束图像重建的基础（第2.2节）。三维中的中心切片定理指出，三维函数 \(f(x, y, z)\) 的投影 \(P(u, v, \vec{\theta})\) 的二维傅里叶变换 \(P(\omega_u, \omega_v, \vec{\theta})\) 等于该函数三维傅里叶变换 \(F(\omega_x, \omega_y, \omega_z)\) 过原点且与探测器平行的一个切片（参见图5.2）。这里，\(\vec{\theta}\) 是 \(u\)-\(v\) 平面和 \(\omega_u\)-\(\omega_v\) 平面的法向方向。方向 \(\vec{\theta}\) 表示一组与 \(\vec{\theta}\) 平行的射线。

基于这一中心切片定理，我们可以确定 \(\vec{\theta}\) 的一些特定轨迹，从而填满 \((\omega_x, \omega_y, \omega_z)\) 傅里叶空间。图5.3给出了其中一种选择，其中 \(\vec{\theta}\) 的轨迹是一个大圆。大圆是位于单位球表面的半径为单位长度的圆（参见图5.4）。大圆上的每个单位向量 \(\vec{\theta}\) 对应于 \((\omega_x, \omega_y, \omega_z)\) 傅里叶空间中的一个已测量 \(P(\omega_u, \omega_v, \vec{\theta})\) 平面。当单位向量 \(\vec{\theta}\) 绕完整个大圆后，已测量的 \(P(\omega_u, \omega_v, \vec{\theta})\) 平面即填满整个 \((\omega_x, \omega_y, \omega_z)\) 傅里叶空间。事实上，由于对称性，如果单位向量 \(\vec{\theta}\) 仅完成大圆的 *一半*，即可获得完整的数据集。

上述示例可推广，如Orlov条件所述：如果每个大圆都与平行射线方向的单位向量 \(\vec{\theta}\) 的轨迹相交，则可获得完整的数据集。该轨迹可以是球面上的曲线，也可以是球面上的区域。图5.5展示了 \(\vec{\theta}\) 轨迹的一些示例（以红色阴影表示），其中前三个满足Orlov条件，而后两个不满足。

图像重建算法取决于方向向量 \(\vec{\theta}\) 轨迹的几何特征。基础算法开发可遵循以下准则。

![](img/dd555effd38151c67af30d84800c554a_108_0.png)

![](img/dd555effd38151c67af30d84800c554a_108_1.png)

图5.1：测量射线可以位于垂直于轴向方向的平面内，也可以位于倾斜平面内。

图5.2：三维线积分投影的中心切片定理。

![](img/dd555effd38151c67af30d84800c554a_109_0.png)

![](img/dd555effd38151c67af30d84800c554a_109_1.png)

![](img/dd555effd38151c67af30d84800c554a_109_2.png)

![](img/dd555effd38151c67af30d84800c554a_109_3.png)

图5.3：一个测量方向在傅里叶空间中给出一个已测量平面。大圆轨迹提供了完整的傅里叶空间测量。

![](img/dd555effd38151c67af30d84800c554a_109_4.png)

图5.4：大圆是单位球上的单位圆。

#### 5.1.1 后投影-然后滤波

如果数据测量充分，三维图像可以被精确重建。如同二维图像重建，图像重建可以先执行后投影，也可以最后执行后投影。如果先执行后投影，则该算法为后投影-然后滤波算法，其步骤如下所述：

