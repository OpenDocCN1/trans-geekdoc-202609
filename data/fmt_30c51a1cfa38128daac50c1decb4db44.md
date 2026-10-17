
如图 4.5 所示，使用高斯分布类型的体积热源作为外部施加的热源。模拟的热源被用于证明 `CNN` 方法论在估计组织温度和热剂量方面的适用性，并且它们可以被替换为不同尺寸和形状的热源，例如由不同的热消融方式引起的热源。

### 4.4.2 在利用 HIFU 进行肝肿瘤消融中的应用

![](img/6554116edbb19a8210b75a29243fd6ec_60_0.png)

**图 4.4** 用于仿真的患者特定解剖模型网格：模型由 CT 图像数据集构建（显示了一个 DICOM 切片），该数据集被分割并重建为肝脏和骨骼。

![](img/6554116edbb19a8210b75a29243fd6ec_60_1.png)

**图 4.5** 使用高斯分布类型的模拟体积热源作为热源，输入 Pennes 生物热传递方程以计算热剂量。

![](img/6554116edbb19a8210b75a29243fd6ec_61_0.png)

**图 4.6** 体积热源在肝脏中的几何布置，展示不同视角 (a)、(b) 和 (c)。

图 4.6 展示了模拟体积热源相对于患者特定解剖模型在肝脏中的几何布置。

热模拟应用了 5 秒（热源开启）和 5 秒（热源关闭）。肝脏使用的热材料属性为 `ρ = 1,060 [kg/m^3]`，`k = 0.518 [W/(m·K)]` 和 `C = 3,700 [J/(kg·K)]`。初始组织温度设定为 `T(0) = 37°C`。在模拟过程中，记录了热源中心的组织温度历史，如图 4.7 所示。模拟结束时造成组织热损伤的热剂量 `240 CEM_{43}` 如图 4.8 所示。

![](img/6554116edbb19a8210b75a29243fd6ec_62_0.png)

**图 4.7** 热源中心处的组织温度历史。

![](img/6554116edbb19a8210b75a29243fd6ec_62_1.png)

**图 4.8** 模拟结束（10 秒）时造成组织热损伤的 240 `CEM₄₃`：(a) 肝脏内诱导的病灶和 (b) 肝脏内的 3D 体积病灶；色标仅应用于热源区域，不适用于 CT 切片。

如前所述，肝肿瘤的热消融治疗可以通过各种方式实现，例如射频消融 (`RFA`)、微波消融 (`MWA`)、激光和 `HIFU`，通过产生热量诱导细胞热损伤以治疗癌症。与 `RFA`、`MWA` 和激光相比，`HIFU` 具有固有的优势，即不需要引入施械即可实现消融效果，并且是唯一一种无创选项。如图 4.9 所示，`HIFU` 治疗使用 `HIFU` 换能器诱发高强度超声波，聚焦于肿瘤区域，那里的机械振动能量以热的形式被组织吸收，作为热源通过完整的皮肤增加局部组织温度，导致肿瘤凝固性坏死。

![](img/6554116edbb19a8210b75a29243fd6ec_63_0.png)

**图 4.9** `HIFU` 消融原理示意图：`HIFU` 换能器放置在患者皮肤外，诱发高强度超声波聚焦于目标肿瘤，导致细胞凝固性坏死。

使用 `CNN` 进行了患者特定肝肿瘤 `HIFU` 治疗的计算机模拟。除了肝脏和骨骼外，CT 图像进一步被分割为皮肤、脂肪和肌肉；`HIFU` 换能器放置在患者皮肤外，其中介质被分割为水。超声波穿过水、皮肤、脂肪和肌肉传播并聚焦于肝肿瘤。超声波的传播使用非线性全波 `Westervelt` 方程 [58] 进行模拟，在占据 `121.3×65.3×65.3 mm` 计算域的均匀 `208×112×112` 网格上进行。模拟使用的 `HIFU` 换能器直径 `D = 60 mm`，曲率半径 `R = 75 mm`，工作频率 `f = 1 MHz`，表面压力为 0.3 MPa。表 4.1 列出了每种组织的典型声特性值。

### 表 4.1 异质组织的声学特性

| | 密度 [kg/m³] | 声速 [m/s] | 衰减 [dB/MHz/cm] | B/A |
|---|---|---|---|---|
| 水 | 998 | 1,482 | 0.00217 | 5.2 |
| 皮肤 | 1,090 | 1,615 | 0.35 | 7.9 |
| 脂肪 | 985 | 1,465 | 0.40 | 8.5 |
| 肌肉 | 1,055 | 1,575 | 0.60 | 7.0 |
| 肝脏 | 1,060 | 1,595 | 0.50 | 6.6 |

由于超声波在组织中的传播，形成了声压场，由于超声波在组织中以热的形式衰减，利用该声压场来获得 `HIFU` 诱导的热源。由于模拟的声场是非线性的，其中会出现更高的谐波频率，因此使用谐波分量来确定非线性热源 `H`，即：

$$H = \frac{1}{\rho c} \sum_{k=1}^{K} \alpha_k p_k^2 \qquad (4.25)$$

其中 `c` 是组织中的声速，`α_k` 是第 `k` 次谐波的衰减系数，其遵循形式为 `α = α_0 ω^y` [59] 的频率幂律（在我们的案例中 `y = 1.3`），`ω` 是角频率，`p_k` 是第 `k` 次谐波分量的声压，`K` 是谐波数量（在我们的案例中 `K = 3`，以平衡数值精度和计算资源）。计算出的热源 `H` 代入公式 (4.3) 以计算肝脏组织中的温度场。

图 4.10 说明了 `HIFU` 换能器的几何布置以及从超声压场计算得出的诱导热源。通过将聚焦超声换能器放置在几何焦点位于目标区域内且避免肋骨（骨组织和被困气体/空气腔体可能干扰 `HIFU` 模态并影响剂量传递）的方式，在目标区域内诱导热能。因此，必须相应地规划治疗。值得一提的是，由于 `HIFU` 换能器放置在肋骨之间（肋间窗口），这可能限制肝脏中期望的 `HIFU` 剂量的可达性，可能需要使用多个 `HIFU` 探头通过多个路径协同工作 [60,61]。

![](img/6554116edbb19a8210b75a29243fd6ec_64_0.png)

**图 4.10** (a) 通过将聚焦超声换能器放置在几何焦点位于目标区域内且超声波可通过肋间窗口（肋骨间隙）的方式，在目标区域内诱导热沉积；(b) (a) 的特写视图。

![](img/6554116edbb19a8210b75a29243fd6ec_65_0.png)

**图 4.11** 目标肝脏区域的 `HIFU` 诱导体积热源。

如图 4.11 所示，在目标肝脏区域内诱导了体积热源。

热模拟应用了 3.5 秒（热源开启）和 11.5 秒（热源关闭）。肝脏的热材料属性与第 4.4.1 节中提到的相同。初始组织温度设定为 `T(0)=37°C`。在模拟过程中，记录了换能器焦点处的组织温度历史，如图 4.12 所示。模拟结束时造成组织热损伤的热剂量 240 `CEM_{43}` 如图 4.13 所示。

### 4.5 讨论

与传统的数值方法相比，`CNN` 提供了一种快速求解生物热传递方程以进行热剂量建模的方法，这归功于细胞集体的和同时的计算活动。非线性生物热传递动力学由非线性细胞动力学来建模，以细胞局部相互作用和全局传播的方式随时间演变。软组织的异质性通过根据不同区域组织/肿瘤的材料属性将单元参数设置为不同值来容纳。

![](img/6554116edbb19a8210b75a29243fd6ec_66_0.png)

**图 4.12** 换能器焦点处的组织温度历史。

![](img/6554116edbb19a8210b75a29243fd6ec_66_1.png)

**图 4.13** 模拟结束（15 秒）时造成组织热损伤的 `240 CEM_{43}`：(a) 肝脏内诱导的病灶和 (b) 肝脏内的 3D 体积病灶；色标仅应用于热源区域，不适用于 CT 切片。

与 `CNN` 传统的应用领域（主要用于图像处理）相比，本文提出的 `CNN` 被制定为融入生物热传递机制，以有效和高效地计算软组织温度场，并用于计算机辅助热消融癌症治疗。

热剂量的计算（公式 4.1）表明，热剂量受组织热暴露历史的影响，这与组织温度和加热持续时间相关。随着变化

组织温度的变化由生物热传递方程决定，其中的激励输入是由各种热模态诱导产生的热源，操作员可以通过消融仪器的功率和加热时间控制热剂量。在组织中的同一点上，相同的热剂量可以通过以下两种途径实现：（1）高功率输入配合短加热时间，或（2）低功率输入配合长加热时间；然而，热剂量分布（如图 4.8 和 4.13 所示）在情况（1）和（2）下可能有所不同，因为较长的加热期间热剂量的变化更容易受到热扩散和血液灌注效应的影响，而当加热时间较短时，这些效应则不明显。此外，值得注意的是，组织加热是一个动态过程，由于与温度相关的材料特性 [62] 和组织变形（如器官运动 [63] 以及热胀冷缩效应），组织的材料属性和物理几何形状会发生动态变化，对这两者进行补偿可能会带来更精确的热剂量计算。

虽然射频消融（`RFA`）和微波消融（`MWA`）等微创热模态在治疗肝肿瘤方面是有效的，并提供了比肝切除术更安全的选项，但它们也表现出一些局限性。例如，`RFA` 的主要并发症发生率约为 `≈4%`，死亡率较低，`≤1%` [64]。大多数并发症，如肠穿孔或胆管损伤，是由于肝脏邻近器官组织受热损伤所致，特别是对于被膜下肿瘤以及靠近肝门和胆囊的肿瘤 [65]。术中 `RFA` 已被用来避免这些并发症，但这种方案侵入性更强，可能导致更多的并发症和副作用。此外，由于血液灌注产生的热沉效应限制了达到热消融所需高温的能力，大血管附近的肿瘤难以被完全消融。实验研究 [66,67] 表明，如果热源以高能量强度和短加热时间（`≤ 2` 秒）诱导，这个问题就不太明显，因为加热会迅速进行，较少受到热扩散和血液灌注效应的影响。

正如 4.4.2 节所述，与 `RFA` 和 `MWA` 相比，高强度聚焦超声（`HIFU`）肿瘤消融代表了非侵入性肝癌治疗手段的优势；然而，另一方面，它要求精确追踪器官运动，以便将 `HIFU` 换能器的焦点区域与目标肿瘤同步，从而准确诱导所需的热损伤水平 [68]。由于肝脏的生理运动，主要由呼吸循环 [69] 引起，并在较小程度上由心脏运动和肠道运动引起，目标肿瘤会不断移动和变形，这使得精确且有效的 `HIFU` 能量沉积变得复杂。因此，最近的方法侧重于连续目标追踪技术，可以在运动周期内将超声波束锁定在目标上，从而实现连续的能量沉积。实时磁共振成像（`MRI`）和诊断超声已被证明是可行的追踪模态 [70,71]。此外，由于器官运动，计算热剂量时必须考虑软组织变形 [72,73]，软组织温度场必须基于组织的变形状态进行计算，才能准确计算组织变形下的热剂量 [74]。

### 4.6 结论

这项工作提出了一种基于 `CNN` 的方法，用于快速计算和分析热消融治疗中管理肝肿瘤所需的软组织温度和热剂量。为了避免复杂且昂贵的非线性数值求解过程，通过将非线性生物热传递公式化为 `CNN` 中非线性的集体且同时发生的局部和全局细胞活动，开发了 `CNN` 模型，从而在二维和三维规则及非规则网格上建立了嵌入生物热传递机制的神经网络模型，以便在计算机辅助热消融治疗中进行快速温度计算。通过一种与临床相关的场景——即在患者特定的 `HIFU` 治疗中针对肝癌进行肿瘤管理的剂量化建模，展示了 `CNN` 模型的应用。

## 致谢

感谢澳大利亚国家健康与医学研究理事会（`NHMRC`）项目资助计划 `APP1093314` 的资金支持。

## 参考文献

- 1. D. J. Breen, and R. Lencioni, “Image-guided ablation of primary liver and renal tumours,” *Nat Rev Clin Oncol*, vol. 12, no. 3, pp. 175–86, 2015.
- 2. Y. Fang, W. Chen, X. Liang, D. Li, H. Lou, R. Chen, K. Wang, and H. Pan, “Comparison of long-term effectiveness and complications of radiofrequency ablation with hepatectomy for small hepatocellular carcinoma,” *J Gastroenterol Hepatol*, vol. 29, no. 1, pp. 193–200, 2014.
- 3. M. W. Lee, S. S. Raman, N. H. Asvadi, S. Siripongsakun, R. M. Hicks, J. Chen, A. Worakitsitisatorn, J. McWilliams, M. J. Tong, R. S. Finn, V. G. Agopian, R. W. Busuttil, and D. S. K. Lu, "Radiofrequency ablation of hepatocellular carcinoma as bridge therapy to liver transplantation: A 10-year intention-to-treat analysis," *Hepatology*, vol. 65, no. 6, pp. 1979–1990, 2019.
- 4. M. Moche, H. Busse, J. J. Fuetterer, C. A. Hineastrosa, D. Seider, P. Brandmaier, M. Kolesnik, S. Jenniskens, R. Blanco Sequeiros, G. Komar, M. Pollari, M. Eibisberger, H. R. Portugaller, P. Voglreiter, R. Flanagan, P. Mariappan, and M. Reinhardt, "Clinical evaluation of in silico planning and real-time simulation of hepatic radiofrequency ablation (ClinicIMMPACT Trial)," *Eur Radiol*, pp. 1–9, 2019.
- 5. V. Lopresto, R. Pinto, L. Larina, and M. Cavanaro, "Treatment planning in microwave thermal ablation: Clinical gaps and recent research advances," *Int J Hyperthermia*, vol. 33, no. 1, pp. 83–100, 2017.
- 6. E. Li, G. R. Liu, V. Tan, and Z. C. He, "Modeling and simulation of bio-heat transfer in the human eye using the 3D alpha finite element method (`αFEM`)," *Int J Numer Method Biomed Eng*, vol. 26, no. 8, pp. 955–976, 2010.
- 7. E. Li, G. R. Liu, and V. Tan, "Simulation of hyperthermia treatment using the edge-based smoothed finite-element method," *Numer Heat Transfer A: Appl*, vol. 57, no. 11, pp. 822–847, 2010.
- 8. P. Rattanadecho, and P. Keangin, "Numerical study of heat transfer and blood flow in two-layered porous liver tissue during microwave ablation process using single and double slot antenna," *Int J Heat Mass Transfer*, vol. 58, no. 1–2, pp. 457–470, 2013.
- 9. C. Rieder, T. Kroger, C. Schumann, and H. K. Hahn, "GPU-based real-time approximation of the ablation zone for radiofrequency ablation," *IEEE Trans Vis Comput Graph*, vol. 17, no. 12, pp. 1812–1821, 2011.
- 10. P. C. Johnson, and G. M. Saidel, "Thermal model for fast simulation during magnetic resonance imaging guidance of radio frequency tumor ablation," *Ann Biomed Eng*, vol. 30, no. 9, pp. 1152–1161, 2002.
- 11. M. Schwenske, J. Georgii, and T. Preusser, "Fast numerical simulation of focused ultrasound treatments during respiratory motion with discontinuous motion boundaries," *IEEE Trans Biomed Eng*, vol. 64, no. 7, pp. 1455–1468, 2017.
