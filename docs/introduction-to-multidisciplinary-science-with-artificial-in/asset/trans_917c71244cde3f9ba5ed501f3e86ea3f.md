
动量方程 : $\frac{\partial \delta \mathbf{v}}{\partial t} + \rho_0 \nabla (\delta \Psi) + \nabla \delta p + \underbrace{2\Omega \times \delta \mathbf{v}}_{\text{Coriolis}} + \underbrace{\Omega \times (\Omega \times \mathbf{x})}_{\text{centrifugal}} = 0$

泊松方程 : $\nabla^2 \delta \Psi = 4\pi G_0 \delta \rho$

其中 $\rho_0 = \text{constant}$, $\mathbf{v}_0 = 0$, 且 $p_0 = 0$, $\mathbf{\Omega}$ 为旋转矢量。 后者左手边的第二项和第三项分别代表由于旋转产生的科里奥利效应和离心力。 $\mathbf{\Omega} = [0,\Omega_y,\Omega_z]^T$, 且 $\nabla \delta p = [0,0,\partial \delta p / \partial z]^T$。 假设扰动仅沿 $z-$ 轴传播。 我们随后得到扰动方程且

$\frac{\partial \delta \rho}{\partial t} + \rho_0 \frac{\partial \delta v_z}{\partial z} = 0 \Longleftrightarrow \omega \delta \rho - \rho_0 k \delta v_z = 0$

$\frac{\partial \delta v_x}{\partial t} + 2\Omega_y v_z - 2\Omega_z v_y = 0 \Longleftrightarrow \omega v_x - 2i\Omega_z v_y + 2i\Omega_y v_z = 0$

$\frac{\partial \delta v_y}{\partial t} + 2\Omega_z v_x = 0 \Longleftrightarrow 2i\Omega_z v_x + \omega v_y = 0$

$\frac{\partial \delta v_z}{\partial t} + \frac{1}{\rho_0} \frac{\partial \delta p}{\partial z} + \frac{\partial \delta \Psi}{\partial z} - 2\Omega_y v_x = 0 \Longleftrightarrow -2i\Omega_y v_x + \omega v_z - \frac{c^2 k}{\rho_0} v_z + k \delta \rho = 0$

$\frac{\partial^2 \delta \Psi}{\partial z^2} = 4\pi G_0 \delta \rho \Longleftrightarrow 4\pi G_0 \delta \rho - k^2 \delta \Psi = 0$

或以矩阵形式表示为

$\begin{pmatrix} \omega & -2i\Omega_z & 2i\Omega_y & 0 & 0 \\ 2i\Omega_z & \omega & 0 & 0 & 0 \\ 2i\Omega_y & 0 & \omega & -(c^2 k_z)/\rho_0 & k_z \\ 0 & 0 & -\rho_0 k_z & \omega & 0 \\ 0 & 0 & 0 & 4\pi G_0 & -k_z^2 \end{pmatrix} \begin{pmatrix} v_x \\ v_y \\ v_z \\ \delta \rho \\ \delta \Psi \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 0 \\ 0 \end{pmatrix}$

令 5 x 5 系数矩阵的行列式等于零以满足其非平凡性，我们得到长期方程 我们寻找非平凡解。这意味着行列式必须为零。这导致关于 $\omega$ 的二二次方程用于色散关系

$\omega^4 - (4\Omega^2 + c^2 k_z^2 - 4\pi G_0 \rho_0) \omega^2 + 4\Omega^2 (c^2 k_z^2 - 4\pi G_0 \rho_0) \cos^2 \theta = 0 , \qquad (B.14)$

其中 $\theta$ 为扰动传播方向 $\mathbf{k}$ 与旋转轴 $\mathbf{\Omega}$ 之间的夹角。 利用韦达关系，我们可以得到求解该方程的 $\omega$ 的以下两个方程：

$\omega_1^2 + \omega_2^2 = 4\Omega^2 + c^2 k_z^2 - 4\pi G_0 \rho_0 \quad \text{and} \quad \omega_1^2 \omega_2^2 = 4\Omega^2 (c^2 k_z^2 - 4\pi G_0 \rho_0) \qquad (B.15)$

第二种情况是重要的特殊情况，其中 $\theta = 90^\circ$, 即旋转轴与扰动相互垂直。色散关系取简化的形式：

$\omega^2 [\omega^2 - (4\Omega^2 + c^2 k_z^2 - 4\pi G_0 \rho_0)] = 0 , \qquad (B.16)$

显然，额外的旋转项起稳定作用。 对于足够大的旋转，在垂直于旋转轴的方向上，旋转可以使重力坍缩的较大尺度稳定下来。 这无非是角动量是恒星形成的敌人这一事实，并且云不再坍缩成一点，而是必须坍缩成盘。

如果我们考虑旋转盘，科里奥利力与气体收缩相抗衡 ⟹ 不稳定性条件发生变化 (Toomre, 1964)。 为了推导出更现实的不稳定性判据，有必要考虑旋转。 在旋转参考系中，有必要在流体动力学方程中加入科里奥利和离心加速度。

## 木星是褐矮星吗？

褐矮星是质量小于 80 m_Jupiter 但至少大于 13 m_Jupiter 的失败恒星——也就是说，木星的质量小于 0.075 m_Brown−dwarf。 木星太小而不能成为褐矮星，甚至作为正文所述的气态巨行星也太小。 此外，木星太冷而不能成为褐矮星。 换句话说，如果木星是褐矮星，它会比现在更热更亮。

## 确定 1 kg 入射物质落到 (1) 白矮星 m_wd = 0.85 m_sun 且 r_wd = 6.6 × 10^6 m = 0.0095 r_sun 以及 (2) 中子星 m_ns = 1.5 m_sun 且 r_ns = 10 km 上所释放的能量。

(1) ΔU = G m / r = 1.71 × 10^13 J (2) ΔU = G m / r = 1.86 × 10^16 J.

## 参考文献

Achten, C., and Andersson, J.T., 2015, 多环芳香化合物的概述 (PAC), *Polycycl Aromat Compd.*, **35**, 177–186.

Acuna, M.H. and Ness, N.F., 1976, 木星的主磁场, *J. Geophys. Res.*, **81**, 2917–2922.

Airy, G.B., 1855, 关于计算山体质量吸引力对大地测量站视天文纬度的影响, *Phil. Trans. R. Soc. London*, **145**, 101–104.

Alfvén, H., *宇宙电动力学*, Oxford Univ. Press, New York, 1950.

Alfvén, H., and Fälthammar, C.-G., *宇宙电动力学，基本原理*, Oxford Univ. Press, New York, 1963.

Altamimi et al., 2016: ITRF2014: 国际地球参考框架的新版本，模拟非线性站点运动, *J. Geophys. Res. Solid Earth*, **121**.

Altamimi, Z. and Gross, R., 2017, *大地测量学*, In: Teunissen P, Montenbruck O (eds), Springer Handbook of Global Navigation Satellite Systems, Springer, Heidelberg, chap 36, 1039–1059.

Alvarez, L.W., Alvarez, W., Asaro, F., and Michel, H., 1980, 白垩纪/第三纪灭绝的外星原因: *Science*, **208**, 1095–1108.

Aoki, I., 1991, 人类发展、生长和衰老的熵原理, *J. Theor. Biol.*, **150**, 215–223.

Argus, D.F., Gordon, R.G., Heflin, M.B., et al., 2010, 板块角速度和地球中心速度来自空间大地测量 *Geophysical Journal International*, **180**, 913–960.

Armstrong, J.A., Bloembergen, N., Ducuing, J., and Pershan, P.S., 1962, 非线性电介质中光波之间的相互作用, *Phys. Rev.*, **127**, 1918–1939.

Arnett, D., 1996, *超新星和核合成*, Princeton University Press.

Aspect, A., Grangier, P., and Roger, G., 1982, 爱因斯坦-波多尔斯基-罗森-玻姆思想实验的实验实现：贝尔不等式的新违反, *Phys. Rev. Lett.*, **49**, 91–94.

Azevedo, F.A., Carvalho, L.R., Grinberg, L.T., Farfel, J.M., Ferretti, R.E., et al., 2009, 神经元和非神经元细胞数量相等使人类大脑成为等距放大的灵长类大脑, *J Comp Neurol.*, **513**, 532–541.

Babcock, H.W., 1939, 仙女座星云的旋转, *Lick Observatory Bulletin*, **19**, 41–51.

Balbus, S., and Hawley, J., 1991, 吸积盘中的不稳定性、湍流和增强输运, *Astrophys. J.*, **376**, 214.

Ball, P., 2011, 纠缠钻石一起振动, *Nature*, **332**.

Barnes, R., and Raymond, S.N., 2004, 预测已知系外行星系统中的行星。I. 测试粒子模拟, *The Astrophysical Journal*, **617**, 569–574.

Baule, G., and McFee, R., 1963, 心脏磁场的检测, *American heart journal*, **66**, 95–96.

Baur, O., and Grafarend, E.W., 2006, 高性能、基于重力梯度张量不变量和运动学轨道信息的 GOCE 重力场恢复. In: Flury, J., Rummel, R., Reigber, C., Rothacher, M., Boedecker, G., Schreiber, U. (eds.): Observation of the Earth System from Space. Springer, New York, NY

Becker, E.D., 1969, *高分辨率核磁共振*, Academic Press.

Beckman, J.E., and Mahoney, T.J., 1998, 默冬极小期与气候变化：历史记录是否促进了当前研究？ *ASP Conference Series*, **153**, 212.

Bell, J.S., 1964, 关于爱因斯坦-波多尔斯基-罗森悖论, *Physics*, **1**, 195–200.

Benabid, A.L., 2007, 深部脑刺激的未来展望, *Exp. Rev. Med. Devices*, **4**, 895–903.

Bentridi, S.E., Gall, B., Hidaka, H., Amrani, N., Gauthier-Lafaye, F., 奥克洛天然核反应堆形成和演化中黏土和中子吸收剂作用的研究

Ben-Naim, A., 2007, *基于信息的统计热力学*, World Scientific.

Blakley, J., 1995, *重力与磁学中的位势理论*, Cambridge University Press, New York.

Bock, Y., and Melgar, D., 2016, GPS 大地测量的物理应用：综述, *Reports on Progress in Physics*, **79**.

Bodu, R., et al., 1972, 关于在加蓬铀中发现的同位素异常的存在, *CR Académie des Sciences Paris*, **275**, 1731.

Bogovalov, S., and Borman, V., 2016, 优化并流气体离心机的分离能力, *Nuclear Engineering and Technology*. Elsevier BV., **48**, 719–726.

Boltzmann, L.E., 1974, *热力学第二定律（理论物理与哲学问题）*, Springer-Verlag, NY, USA.

Bondeson, A., Iacono, R., and Bhattacharjee, A.H., 1987, 具有剪切平衡流的圆柱等离子体的局部磁流体不稳定性, *Phys. Fluids*, **30**, 2167–2180.

Boto, E., Holmes, N., Leggett, J., Roberts, G., et al., 2018, 通过可穿戴系统将脑磁图向现实世界应用推进, *Nature*, **555**, 657–6612.
