

组织温度的变化由生物热传递方程决定，其中的激励输入是由各种热模态诱导产生的热源，操作员可以通过消融仪器的功率和加热时间控制热剂量。在组织中的同一点上，相同的热剂量可以通过以下两种途径实现：（1）高功率输入配合短加热时间，或（2）低功率输入配合长加热时间；然而，热剂量分布（如图 4.8 和 4.13 所示）在情况（1）和（2）下可能有所不同，因为较长的加热期间热剂量的变化更容易受到热扩散和血液灌注效应的影响，而当加热时间较短时，这些效应则不明显。此外，值得注意的是，组织加热是一个动态过程，由于与温度相关的材料特性 [62] 和组织变形（如器官运动 [63] 以及热胀冷缩效应），组织的材料属性和物理几何形状会发生动态变化，对这两者进行补偿可能会带来更精确的热剂量计算。

虽然射频消融（RFA）和微波消融（MWA）等微创热模态在治疗肝肿瘤方面是有效的，并提供了比肝切除术更安全的选项，但它们也表现出一些局限性。例如，RFA 的主要并发症发生率约为 $\approx4\%$，死亡率较低，$\leq1\%$ [64]。大多数并发症，如肠穿孔或胆管损伤，是由于肝脏邻近器官组织受热损伤所致，特别是对于被膜下肿瘤以及靠近肝门和胆囊的肿瘤 [65]。术中 RFA 已被用来避免这些并发症，但这种方案侵入性更强，可能导致更多的并发症和副作用。此外，由于血液灌注产生的热沉效应限制了达到热消融所需高温的能力，大血管附近的肿瘤难以被完全消融。实验研究 [66,67] 表明，如果热源以高能量强度和短加热时间（$\leq 2$ 秒）诱导，这个问题就不太明显，因为加热会迅速进行，较少受到热扩散和血液灌注效应的影响。

正如 4.4.2 节所述，与 RFA 和 MWA 相比，高强度聚焦超声（HIFU）肿瘤消融代表了非侵入性肝癌治疗手段的优势；然而，另一方面，它要求精确追踪器官运动，以便将 HIFU 换能器的焦点区域与目标肿瘤同步，从而准确诱导所需的热损伤水平 [68]。由于肝脏的生理运动，主要由呼吸循环 [69] 引起，并在较小程度上由心脏运动和肠道运动引起，目标肿瘤会不断移动和变形，这使得精确且有效的 HIFU 能量沉积变得复杂。因此，最近的方法侧重于连续目标追踪技术，可以在运动周期内将超声波束锁定在目标上，从而实现连续的能量沉积。实时磁共振成像（MRI）和诊断超声已被证明是可行的追踪模态 [70,71]。此外，由于器官运动，计算热剂量时必须考虑软组织变形 [72,73]，软组织温度场必须基于组织的变形状态进行计算，才能准确计算组织变形下的热剂量 [74]。

## 4.6 结论

这项工作提出了一种基于 CNN 的方法，用于快速计算和分析热消融治疗中管理肝肿瘤所需的软组织温度和热剂量。为了避免复杂且昂贵的非线性数值求解过程，通过将非线性生物热传递公式化为 CNN 中非线性的集体且同时发生的局部和全局细胞活动，开发了 CNN 模型，从而在二维和三维规则及非规则网格上建立了嵌入生物热传递机制的神经网络模型，以便在计算机辅助热消融治疗中进行快速温度计算。通过一种与临床相关的场景——即在患者特定的 HIFU 治疗中针对肝癌进行肿瘤管理的剂量化建模，展示了 CNN 模型的应用。

## 致谢

感谢澳大利亚国家健康与医学研究理事会（NHMRC）项目资助计划 APP1093314 的资金支持。

## 参考文献

- 1. D. J. Breen, and R. Lencioni, “Image-guided ablation of primary liver and renal tumours,” *Nat Rev Clin Oncol*, vol. 12, no. 3, pp. 175–86, 2015.
- 2. Y. Fang, W. Chen, X. Liang, D. Li, H. Lou, R. Chen, K. Wang, and H. Pan, “Comparison of long-term effectiveness and complications of radiofrequency ablation with hepatectomy for small hepatocellular carcinoma,” *J Gastroenterol Hepatol*, vol. 29, no. 1, pp. 193–200, 2014.
- 3. M. W. Lee, S. S. Raman, N. H. Asvadi, S. Siripongsakun, R. M. Hicks, J. Chen, A. Worakitsitisatorn, J. McWilliams, M. J. Tong, R. S. Finn, V. G. Agopian, R. W. Busuttil, and D. S. K. Lu, "Radiofrequency ablation of hepatocellular carcinoma as bridge therapy to liver transplantation: A 10-year intention-to-treat analysis," *Hepatology*, vol. 65, no. 6, pp. 1979–1990, 2019.
- 4. M. Moche, H. Busse, J. J. Fuetterer, C. A. Hineastrosa, D. Seider, P. Brandmaier, M. Kolesnik, S. Jenniskens, R. Blanco Sequeiros, G. Komar, M. Pollari, M. Eibisberger, H. R. Portugaller, P. Voglreiter, R. Flanagan, P. Mariappan, and M. Reinhardt, "Clinical evaluation of in silico planning and real-time simulation of hepatic radiofrequency ablation (ClinicIMMPACT Trial)," *Eur Radiol*, pp. 1–9, 2019.
- 5. V. Lopresto, R. Pinto, L. Larina, and M. Cavanaro, "Treatment planning in microwave thermal ablation: Clinical gaps and recent research advances," *Int J Hyperthermia*, vol. 33, no. 1, pp. 83–100, 2017.
- 6. E. Li, G. R. Liu, V. Tan, and Z. C. He, "Modeling and simulation of bio-heat transfer in the human eye using the 3D alpha finite element method ($\alpha$FEM)," *Int J Numer Method Biomed Eng*, vol. 26, no. 8, pp. 955–976, 2010.
- 7. E. Li, G. R. Liu, and V. Tan, "Simulation of hyperthermia treatment using the edge-based smoothed finite-element method," *Numer Heat Transfer A: Appl*, vol. 57, no. 11, pp. 822–847, 2010.
- 8. P. Rattanadecho, and P. Keangin, "Numerical study of heat transfer and blood flow in two-layered porous liver tissue during microwave ablation process using single and double slot antenna," *Int J Heat Mass Transfer*, vol. 58, no. 1–2, pp. 457–470, 2013.
- 9. C. Rieder, T. Kroger, C. Schumann, and H. K. Hahn, "GPU-based real-time approximation of the ablation zone for radiofrequency ablation," *IEEE Trans Vis Comput Graph*, vol. 17, no. 12, pp. 1812–1821, 2011.
- 10. P. C. Johnson, and G. M. Saidel, "Thermal model for fast simulation during magnetic resonance imaging guidance of radio frequency tumor ablation," *Ann Biomed Eng*, vol. 30, no. 9, pp. 1152–1161, 2002.
- 11. M. Schwenske, J. Georgii, and T. Preusser, "Fast numerical simulation of focused ultrasound treatments during respiratory motion with discontinuous motion boundaries," *IEEE Trans Biomed Eng*, vol. 64, no. 7, pp. 1455–1468, 2017.
- 12. G. Kalantzis, W. Miller, W. Tichy, and S. LeBlang, "A GPU accelerated finite differences method of the bioheat transfer equation for ultrasound thermal ablation," *Software Engineering, Artificial Intelligence, Networking and Parallel/Distributed Computing*, Roger Lee, Ed. pp. 45–55: Springer, Switzerland, 2016.
- 13. J. Zhang, J. Hills, Y. Zhong, B. Shirinzadeh, J. Smith, and C. Gu, "Gpu-accelerated finite element modeling of bio-heat conduction for simulation of thermal ablation," *Journal of Mechanics in Medicine and Biology*, vol. 18, no. 07, p. 1840012, 2018.
- 14. J. Zhang, J. Hills, Y. Zhong, B. Shirinzadeh, J. Smith, and C. Gu, "Modeling of soft tissue thermal damage based on GPU acceleration," *Comput Assist Surg (Abingdon)*, vol. 24, no. supl, pp. 5–12, 2019.

