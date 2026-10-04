

PFO || 层厚度

延迟时间

取向 || 48 || 否 || 开孔孔隙率 %

抗压强度 || 是

应使用 `k`-折验证 || [Asadi-Eydiv et al. (2016](#bodymatter-001.xhtml#b_9783110648195-001_ref_006)) |

| --- | --- | --- | --- | --- | --- | --- | --- | --- |

| 熔融电纺三维生物材料基质中细胞限制的机器学习计量学 || 2019 || SVM || 椭圆度 – 矩形度 – 细胞面积 – FA 大小 – FA 长宽比

细胞 E-斜率

细胞平均 G-函数 || 88 || 五折交叉验证 || 不同分类 || 是 || [Tourlomousis et al. (2019](#bodymatter-001.xhtml#b_9783110648195-001_ref_039)) |

| 基于分类的计算：使用支持向量回归分析的纳米纤维支架结构 || 2019 || SVR 和 SVM || 蛋白质的近似大小 || 15 || 否 || 纳米纤维支架的带强度 || 非常小的数据集和固定的训练/测试集划分会产生偏差结果 || [Adebileje et al. (2019](#bodymatter-001.xhtml#b_9783110648195-001_ref_001)) |

| 心肌再生支架设计中间充质干细胞的分离、表征和基于代理的建模 || 2019 || 多智能体系统 || 不适用 || 36 || 不适用 || 随时间变化的平均炎症

随时间变化的细胞群体 || 否 || [Ramírez López et al. (2019](#bodymatter-001.xhtml#b_9783110648195-001_ref_033)) |

| 微纤维碳基支架上成骨细胞生长的细胞自动机模拟 || 2014 || 2D 细胞自动机 || 结晶度

取向

表面粗糙度 || 18 || 不适用 || 成骨细胞生长 || 是 || [Czarnecki et al. (2014](#bodymatter-001.xhtml#b_9783110648195-001_ref_011)) |

| 细胞粘附和增殖的建模：基于细胞自动机的方法 || 2015 || 2D 细胞自动机 || 2D 支架 ||  || 不适用 || 细胞沉降时间

细胞粘附时间

细胞增殖时间 || 是，附带体外测试的显微照片 || [Vivas et al. (2015](#bodymatter-001.xhtml#b_9783110648195-001_ref_040)) |

需要考虑的一个关键方面是所用样本数量低（从 15 到 88），这严重阻碍了许多这些技术的应用，而这些技术通常需要数百到数千个样本。观察到一些重要的方法学问题，主要是只有部分工作使用了 `k`-折交叉验证，这是小数据集情况下改进结果和避免偏差的标准方法。在这方面，几项工作共享其（难以获得的）数据的完整列表以及实验的细节，这本身就是一项重要的贡献，因为未来的研究可以基于这些数据进行。

将元优化方法纳入以增强所使用的优化方法（例如第一项工作中 PSO 确定所用网络的拓扑结构和数量）是非常有用的工具，以改进结果并更好地利用数据。元优化方法会丢弃不必要的网络，减少需要训练的参数数量，更好地利用数据。

另一个经常被忽视但在骨支架中明显重要的方面是材料的力学性能、设计和形状。单轴抗压强度是骨骼情况下的关键特征（因为支架将被加载，并且根据植入物在体内的位置，负载会非常严重）。如所分析的第一项工作所示，在保持给定材料的孔隙率的同时，可以达到的最大抗压强度是有限的。如果抗压强度不足以承受身体特定位置和特定患者所期望的载荷，则必须使用另一种材料。这一方面以及支架形状的影响需要进一步研究，并且可以有效地由人工智能辅助，前提是收集关键数据。

最后，所使用的多种构建技术、材料和细胞需要不同的变量。需要进一步研究以确定和分类骨支架细胞粘附过程中涉及的所有变量，以及它们之间以及与可用不同数学模型之间的关系。孔隙率、开孔孔隙率和互连性已被研究，但主要是在有限的几何形状（主要是圆柱形和棱柱形）中，而待替换骨的形状会改变这些值，并在细胞粘附中发挥重要作用，这将需要进一步研究。作为未来的工作，显然有必要对最影响 BTE 支架细胞粘附的变量进行研究和调查，并收集现有数据，以便于未来将人工智能应用于此案例。BTE 仍是一个未被充分探索的领域，具有巨大的潜力。

## 致谢

本章所包含的工作是 María de Lourdes Sánchez 硕士论文的一部分，由 Dr. Adrián Will 和 Dr. Andrea Rodríguez 指导，Maestría en Ingeniería en Sistemas de Información, Universidad Tecnológica Nacional, Facultad Regional Tucumán, Tucumán, Argentina。

## 参考文献

Adebileje S.A., Aiyelabegan H.T., Adebileje T.A., and Olakunle T.O. Classification based computation: Nanofibrous scaffold architecture using support vector regression analysis. Acta Scientific Medical Sciences, (2019), 7, 93–98. [a](#bodymatter-001.xhtml#xref_d69967e1544), [b](#bodymatter-001.xhtml#xref_d69967e1902)

Alberts B., Johnson A., Lewis J., Raff M., Roberts K., and Walter P. Biología Molecular de LA CÉLULA – 5ta. edición, (2008), Ediciones Omega. [a](#bodymatter-001.xhtml#xref_d69967e1164), [b](#bodymatter-001.xhtml#xref_d69967e1173), [c](#bodymatter-001.xhtml#xref_d69967e1179)

Altamirano Valencia A.A., Vargas Becerril N., Vázquez F.C., Vargas Koudriavtsev T., Montesinos J.J., Alfaro Mayorga E., et al. Biocompatibilidad de andamios nanofibrilares con diferentes concentraciones de PLA/Hidroxiapatita. ODOVTOS-International Journal of Dental Sciences, (2016), 39–50. [a](#bodymatter-001.xhtml#xref_d69967e1100), [b](#bodymatter-001.xhtml#xref_d69967e1106)

Araujo P.B. and Rodríguez S.A. Tesis Doctoral: Patrones de Diseño Organizacionales para Sistemas Multiagentes, (2018). [→](#bodymatter-001.xhtml#xref_d69967e1608)

Arima Y. and Iwata H. Effect of wettability and surface functional groups on protein adsorption and cell adhesion using well-defined mixed self-assembled monolayers. Biomaterials, (2007), 28(20), 3074–3082. [→](#bodymatter-001.xhtml#xref_d69967e1207)

Asadi-Eydivand M., Solati-Hashjin M., Fathi A., Padashi M., and Osman N.A. Optimal Design of a 3D-Printed Scaffold Using Intelligent Evolutionary Algorithms Applied Soft Computing, (http://dx.doi.org/10.1016/j.asoc.2015.11.011), (2016), 36–47. [a](#bodymatter-001.xhtml#xref_d69967e1390), [b](#bodymatter-001.xhtml#xref_d69967e1832)

Biswal D., Kumar N.S., Yadav P., and Moharana A. Artificial intelligence in advancement of regenerative medicine & tissue engineering. 2nd International Conference on Tissue Engineering and Regenerative Medicine (ICTERM), (2013). [→](#bodymatter-001.xhtml#xref_d69967e1021)

Boccaccio A., Uva A.E., Fiorentino M., Lamberti L., and Monno G. A mechanobiology-based algorithm to optimize the microstructure geometry of bone tissue scaffolds. International Journal of Biological Sciences, (2016), 12(1), 1–17. [→](#bodymatter-001.xhtml#xref_d69967e1257)

Chang H.-I. and Wang Y. Cell responses to surface and architecture of tissue engineering scaffolds. Regenerative Medicine and Tissue Engineering – Cells and Biomaterials, (2011). [a](#bodymatter-001.xhtml#xref_d69967e1245), [b](#bodymatter-001.xhtml#xref_d69967e1248), [c](#bodymatter-001.xhtml#xref_d69967e1251)

