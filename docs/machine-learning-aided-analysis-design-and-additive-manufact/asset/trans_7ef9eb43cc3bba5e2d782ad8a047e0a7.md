

![](img/90ed165a39fa708ec438fcda79319c25_424_0.png)

图 16.12 标称应变为为 0.4 时薄壁管与轴向梯度泡沫在介尺度上的相互作用：(A) "GFFT-12-6" 和 (B) "GFFT-6-12"。

## 16.5 梯度泡沫填充管的预测模型

### 16.5.1 泡沫填充管的现有预测模型

如上所述，FFT 的承载能力由三个部分支撑：薄壁管、泡沫以及两者之间的相互作用。因此，开发了一个模型来预测 FFT 的压缩力，其中薄壁管部分与其构型有关，泡沫部分与其相对密度有关，而相互作用部分则与薄壁管和泡沫的承载能力有关。Hansen 等人 [25] 提出了一个广泛的 FFT 压缩力预测模型：

$$F_{avg} = F_{avg}^0 + \sigma_t \pi \left(\frac{b_n}{2}\right)^2 + C_{avg}\sqrt{\sigma_t\sigma_b}bm \quad (16.1)$$

$F_{avg}^0$ 是空心管的贡献，中间项和最后一项分别描述单个泡沫的阻力和相互作用效应。b$ 和 $h$ 分别是管的外截面直径和壁厚。b_m=b-h$ 和 $h_m=b-2h$ 分别是中间截面直径和泡沫的直径。$\sigma_t$ 是泡沫的平台应力。$\sigma_b$ 是管材料的特征应力，定义为管材料屈服强度和极限强度的平均值。

### 16.5.2 梯度泡沫填充管的新预测模型

虽然等式 (16.1) 提供了一种预测 FFT 平均压缩力的可靠方法，但很难将该模型直接应用于 GFFT。如式 16.8 所示，GF 的强度随着压力的进行而逐渐增大。式 (16.1) 中泡沫的强度随应变的增加而变化。对于 GFFT，本章提出了以下预测模型：

$$F_{GFFT} = F_{avg}^0 + \sigma^* \pi \left(\frac{b_n}{2}\right)^2 + C_{avg}\sqrt{\sigma^*\sigma_b}bm \quad (16.2)$$

式 (16.2) 的第一项可以像 [25] 写法：

$$F_{avg}^0 = \kappa_D \sigma_b bm^{1/3}h^{5/3} \quad (16.3)$$

$\kappa_D$ 是表示空心管变形方法的无量纲常数。在本章中，$\sigma_0, b_m,$ 和 $h$ 分别确定为 52.86 MPa、60.4 mm 和 0.4 mm。$\kappa_D$ 可以通过数据拟合确定为2.572。此外，发现平台应力遵循与泡沫密度的幂律 [34,51]。通过将实验数据拟合到幂律方程，可以得到式 (16.4)：

$$\frac{\sigma_{ys}^*}{\sigma_{ys}} = 0.903 \left(\frac{\rho^*}{\rho_l}\right)^{1.787} \quad (16.4)$$

$\sigma_{ys}^*$ 和 $\sigma_{ys}$ 分别是泡沫和基材料的平台应力。屈服强度 $\sigma_{ys}$ 为 52.86 MPa。这里使用能量吸收方向法来确定 UF 的平台应力。能量吸收效率定义为到标称应变 $\varepsilon_a$ 的吸收能量除以相应的应力 $\sigma(\varepsilon_a)$，如下：

$$\eta(\varepsilon_a) = \frac{\int_0^{\varepsilon_a}\sigma(\varepsilon)d\varepsilon}{\sigma(\varepsilon_a)} \quad (16.5)$$

如图 16.13 所示，当能量吸收效率达到最大值时，相应的应变值定义为密化应变 $\varepsilon_D$。然后，平台应力 $\sigma_{pl}$ 由式确定：

$$\sigma_{pl} = \frac{\int_0^{\varepsilon_{cr}}\sigma(\varepsilon)d\varepsilon}{\varepsilon_D - \varepsilon_{cr}} \quad (16.6)$$

式 (16.4) 给出了均匀泡沫应力与相对密度之间的关系。根据第 15 章第 15.5.2 节，梯度泡沫的标称应变与相对密度梯度的关系可以通过 $\rho(\rho^{-1}(\varepsilon))$ 确定。因此，对于 GF，压缩应力定义为：

$$\sigma^*(\varepsilon) = \sigma_{pl}(\rho(\rho^{-1}(\varepsilon))) \quad (16.7)$$

![](img/90ed165a39fa708ec438fcda79319c25_426_0.png)

**图 16.13** 泡沫材料典型应力-应变曲线的力学参数定义。

![](img/90ed165a39fa708ec438fcda79319c25_427_0.png)

**图 16.14** GFFT-6-12 实验数据与预测的对比。结合式 (16.2)、(16.3) 和 (16.7)，GFFT 的压缩力计算如下：

$$F_{avg} = F_{avg}^0 + \sigma_t \pi \left(\frac{b_n}{2}\right)^2 + C_{avg}\sqrt{\sigma_t\sigma_b}bm \quad (16.8)$$

相互作用系数 $C_{avg}$ 与泡沫和管之间的界面变形有关。在本章中，通过数据拟合确定 $C_{avg}$ 为 2.572。此外，如图 16.14 所示，验证了该预测模型的准确性。

## 16.6 结论

本章对不同密度的 FFT 和不同构型的 GFFT 进行了实验和数值研究。阐述了泡沫与管之间的内部相互作用机制。结果显示，由于引入了泡沫，FFT 具有更高的负载能力，包含了挤挤出和泡沫的支撑。此外，尽管 GF 和 UF 密度相似，但 FFT 显示出明显的硬化而非平台。提出了一种包含三项（管、泡沫及其相互作用）的预测模型。

致谢

本工作受中国自然科学基金（项目编号：211021, 22078）、高等教育学科创新项目（0710）以及中国博士后科学基金（项目编号：2021M6278）资助。

参考文献

- [1] Guillermo SR, Lu G, Grizeta RH. Quasi-static axial compression of thin-walled tubes. Int J Mech Sci 2001;42:2103–23
- [2] Bintaraj A, Salih M, Shah S. On the crashworthiness of thin-walled energy absorbers: recent advances and future developments. Thin-Walled Structures 2017;118:37–63.
- [3] Wang M, Yu X, Zhang J, Qin Q. Point-bending of asymmetrically metallic sandwich beams with foam core: failure behavior and optimal design. Comp Struct 2022;280:112475.
- [4] Duan Y, Bi S, Shi X, Li Y. Quasi-static and dynamic compressive properties and deformation mechanics of 3D printed cellular structures with Kelvin cells. Int J Mater Eng 2019;132:103003.
- [5] Sun G, Wang Z, Hu H, Zheng Li Q. Numerical and experimental investigation into the crashworthiness of metal-foam-composite hybrid structures. Comp Struct 2019:535–547.
- [6] Luo H, Han Y, Meng X, Jin C. Failure analysis and energy-absorbing experiment of composite tubes under axial dynamic impact. Compos B Eng 2016;87:1–11.
- [7] Legendre J, Le Gnecque P, Douard C, Moyne S. Numerical, and experimental study of the plastic buckling of thick cylindrical tubes under axial

