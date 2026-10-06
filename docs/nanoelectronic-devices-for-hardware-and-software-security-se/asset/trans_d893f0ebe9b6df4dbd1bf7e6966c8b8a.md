

# 14 • 用于安全应用的光探测器

$NEP = \frac{\sqrt{\Delta f}}{D} W/\text{Hz}^{1/2}$ (14.8)

其中 $A$ 和 $\Delta f$ 分别表示有效面积和带宽。

## 14.5.3 噪声

噪声是指通过半导体器件的电流或电压自发波动。散噪声（量子噪声）和约翰逊-尼奎斯特噪声（热噪声）[69]是光探测器的主要噪声源。散噪声由于流过器件的电载子的离散行为产生。另一方面，热噪声由于电载子的随机热运动产生。由于其在所有频率上的功率谱密度相等，因此被称为白噪声[65]。因此，散噪声电流 ($i_i$) 和约翰逊-尼奎斯特噪声电流 ($i_j$) 通过公式 [64] 进行估算。

$i_i = \sqrt{2q(J_{\text{light}}+J_{\text{dark}})\Delta f}$ (14.9)

$i_j = \sqrt{\frac{4KT}{(RA)_{\text{NET}}}}$ (14.10)

总噪声电流 ($i_n$) [69] 和信噪比 (SNR) [9], [64] 给出如下

$i_n = i_i + i_j$ (14.11)

$SNR = 10\log \left( \frac{1(Q_{\text{ext}}P_n/\lambda/1.24)}{i_n} \right) dB$ (14.12)

通常情况下，一个理想的高性能光探测器应该具有低暗电流密度、高灵敏度、高量子效率、高探测速度、高选择性、高响应率、低等噪声功率、低待机功耗、低噪声水平以及要求的电压偏置[15]。

## 14.6 应用

光探测器的发展主要专注于追求漏电流、低噪声、短响应时间、高均匀性、宽以及高增益带宽的小型化光探测器[15], [31]。光探测的实现得于光敏材料的光电效应以及大规模制造和集成技术[70]。不同光谱区域的光探测器由于其在生活、军事、工业和农业等领域的多种应用，引起了广泛的研究兴趣。

根据应用的不同，不同的光谱区域经常被用于光探测，如图14.10所示[34]。紫外（UV）光探测器在环境监测、空间科学、军事调查、杀菌、领土入侵方面发现了潜在应用，而可见光探测器已用于视频成像、显示、工业安全、光电存储等[31], [71]。红外（IR）光探测器应用于多个领域，例如热力和生物医学污染检测，

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_308_0.png)

图 14.10了从紫外到红外和太赫兹的不同光谱区域光探测器的潜在应用。

成像、遥感、、导弹制导、运动检测、电信、安防、自由空间通信、化学分析等[23], [74]。

如前所述，HgCdTe半导体材料可调的光电特性使其成为开发宽带光探测器极具前景的选择[21], [53], [59], [75]。目前已有报道了在低温下工作的具有不同器件结构的HgCdTe基高性能红外光探测器，例如p-n [22]、p-i-n [74] 以及双频红外光探测器[23]。HgCdTe技术仍主要用于军事和民用相关的安全应用，用于目标探测[78]。另一个常见应用是用于家用系统的红外敏感运动检测。另一方面，超高迁移率和由于较低产生率带来的更高工作频率导致了具有优性能石墨烯/HgCdTe基p-n [39]、p-i-n [42] 和势垒型[63] 光探测器架构的发展，用于弱信号检测和安全相关应用。

## 14.7 结论

总结，本章介绍了光探测器及其各种光探测机制、不同类型、所用材料、特性及其各种应用。光探测器是用于探测入射辐射的光电组件。根据光敏材料吸收的光量，光探测器可以在紫外、可见光和红外光谱范围内找到潜在应用。在材料属性方面，HgCdTe是军事相关应用中最常用的材料之一。基于HgCdTe的光探测器工作限于低温。为了解决这一问题，石墨烯与HgCdTe的异质结将是在近室温生产高性能光探测器的显著解决方案。

REFERENCES

[1] R. P. Feynman, "There is plenty of room," Engineering and Science, vol. 23, no. 5, pp. 22–36, 1959.
[2] G. E. Moore, "Cramming more into integrated circuits," Proceedings of the IEEE, vol. 86, no. 1, pp. 82–85, 1998.
[3] A. L. Rogach, E. Echmüller, S. G. Hickey, and S. V. Kershaw, "Infrared nanocrystals: Synthesis, spectroscopy, and applications," Small, vol. 3, no. 4, pp. 536–557, 2007.
[4] L. Merahi, Hybrid Nanocomposites for Nanotechnology, Boston, MA: Springer, 2009.
[5] J. Wang and S. Lee, "Ge photodetectors for silicon optoelectronics," Sensors, vol. 11, no. 1, pp. 99–114, 2018.
[6] G. Keister, Optical Fiber Communications, New Delhi: McGraw-Hill Publishing Limited, 2008.
[7] B. Jalali, S. Yeganarayanan, T. Yoon, T. Yoshimoto, I. Rendina, and F. Coppinger, "Advantages in silicon-insulator optoelectronics," IEEE Journal of Selected Topics in Quantum Electronics, vol. 4, no. 6, pp. 938–947, 1998.
[8] B. Jalali, M. Pannicia, and G. Reed, "Silicon photons," IEEE Magazine, vol. 7, 58–68, 2006.
[9] J. M. Senior, Optoelectronic Fiber Communications Principles and Practice, Third Edition. Pearson Education Limited, 2009.
[10] S. J. Koester, S. Member, J. D. Schaub, G. Deblinger, and J. O. Chu, "Germanium-on-Si photodetectors for integrated optoelectronics," Advanced Journal of Quantum Electronics, vol. 12, no. 6, pp. 1489–1502, 2006.
[11] Y. Kang, P. Mages, A. R. Clawson, P. K. Yu, B. Bitter, Z. Pan, A. Pauchard, and Y. H. Luo, "InGaAsAs photodiodes with low-noise performances," IEEE Photonics Technology Letters, vol. 14, no. 11, pp. 1593–1595, 2002.
[12] X. Zhang, D. Wu, and H. G, "Heterojunction on II-VI compound semiconductor one-dimensional nanostructures and their optoelectronic applications," Crystals, vol. 7, no. 1, pp. 1–24, 2017.
[13] M. Long, P. Wang, H. Fang, and W. Hu, "Progress, challenges, and opportunities for 2D material photodetectors," Advanced Journal of Optical Electronics, vol. 19, no. 18, 180381–180387, 2018.
[14] P. Bhattacharya, Semiconductor Optoelectronics, New Delhi: Prentice-Hall India, 2004.
[15] P. C. Eng, S. Song, and B. Ping, "State-of-the-art photodetectors for optoelectronic wavelength," Nanophoton, vol. 4, no. 3, pp. 277–302, 2015.
[16] J. Brouckart, G. Roelkens, D. Van Thouort, and R. Baets, "Thin-film III-V photodetectors on silicon-on-insulator ICs," Journal of Lightwave Technology, vol. 25, no. 4, pp. 1053–1060, 2007.
[17] L. Shi and S. Nanishian, "Comparative study of silicon-based ultraviolet photodetectors," IEEE Sensors, vol. 12, no. 7, pp. 2453–2459, 2012.
[18] M. Casalino, "Recent advances in silicon photodetectors based on the emission effect," In Research on Silicon: Properties, Technology, V. I. Talanin (Eds.), Rijeka, Croatia: InTech, 2017.
[19] ... InP-based high-speed photodetectors," Journal of Lightwave Technology, vol. 27, no. 3, pp. 343–355, 2009.
[20] Y. Chen and B. Chen, "Design of InP-based high-speed photodiode for 2-µm wavelength," Journal of Quantum Electronics, vol. 55, no. 1, pp. 1–8, 2019.
[21] A. Rogalski, "HgCdTe infrared detector: history, status and outlook," Reports on Progress in Physics, vol. 68, no. 10, pp. 2267–2336, 2005.

