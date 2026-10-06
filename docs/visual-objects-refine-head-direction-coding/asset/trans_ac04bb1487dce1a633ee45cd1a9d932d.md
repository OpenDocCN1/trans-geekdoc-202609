

# 研究论文

视角，仅在点头部方向指出的位置或至少在线索处（θ < 45°）。正如文所述，标记了开启（On）和关闭（Off）的头部方向并计算了归一化的视觉响应。根据实验设置，我们将与物体对齐的偏好方向（270°指向细胞）与偏好方向与同形角对齐的细胞细胞（90°指向细胞）进行了比较。然而，偏好方向不对齐的细胞在某些情况下（0° 和 180°指向细胞）是相同的。

这由一个在 θ<sub>min</sub> = 0 处的计数、具有高 V<sub>max</sub> 和幅度的 M 不确定分量组成。我们假设头部的 I 和 M 单元受到刺激的驱动强度相等。

每个神经元的最终发放率是其取向的幂律函数。

```
$V(θ) = V_{max}e^{-|θ-θ₀|}$
```

参数取自 (46) 中的定义（见表 S7）。为了测试结果的稳健性，从均匀分布中采样了 12250 个具有不同权重的神经元群体（见表 S7）。对于每个输入 HD (0°) 的神经元，通过输入的小变化 (Δθ=) 计算了与 HD (0°, HD-场) 对齐以及与该 HD (180°) 对齐的神经元速率变化。

# 响应延迟

对于每个 HD，均呈现所有的试验和刺激以获得神经元的整体响应。响应延迟定义为神经元发放率上升到前一次标准差两倍的点。

# 灌注与组织学处理

在电生理实验结束后，使用戊比巴（100 mg/kg）和尿素（16 mg/kg）对动物进行深灌注，然后用 4% 甲醛固定的 0.5% 磷酸缓冲盐溶液同时灌注。

在慢性记录的情况下，撤回电极以移除探针。将大脑取出并在更换溶液为 30% 蔗糖磷酸缓冲盐溶液后保存 4 小时。在 -20°C 下冻结后，使用冷冻切片机以 50μm 的厚度对大脑进行冷冻切片。

切片用 DAPT 染色并置于 Mifogli 培养基。含有探针的切片与抗 IIIβ 一抗体 (1:200) 和标记有荧光团 488 的二抗体在 4°C 下孵育过夜，随后——

使用荧光显微镜获取神经元的图像和硅探针的轨迹。

在急性记录的情况下，神经元收集在 ACSF 溶液中。大脑经过清洗并包埋在 4% ACSF 中。使用振动切片机（Vibrotome TX）切成厚度 100μm 的冠状切并用 DAPT 染色。

使用带有 20x 物镜的 Leica TCS 激光共聚焦显微镜捕捉图像。使用 LAS 软件和 Adobe Photoshop 进行处理。

# SSN 模型

上层环状网络模型 (46)，细胞连接网络 N=50 和 N=51 神经元被放置在 θ = [-π, π] 的环周围。以下方程描述了

```
$V_i = V_{rest} + V_{max} - \sum_{j} W_{ij}(V_j)$
```

其中 $V_i$ 和 $V_j$ 分别指在 θ₀ 和 θ 处的单元神经元的膜电位和电流，$V_{max}$ 是外部输入，$W_{ij}$ 是从 θ₀ 到 θ 的突触连接强度，其固定值使得权重 $W_{ij}$、$W_{ji}$ 和 $I$ 的之和为

```
$I_{h}(\theta_0) = I(t) + I_{max} \left[ \frac{\cos(\theta - \theta_0)}{\sin^2\theta} \right]$
```

# 参考文献

- 1. J. Keck, and J. Harvey. 猕猴皮层在自由运行期间活动的空间图。Nature 274(5681): 317–321 (1986). doi: 10.1038/274317a
- 2. S. J. Rau, U. B. Müller, and J. Banks. 小鼠下顶盖下区的头部方向细胞。Science 281(5379): 925–928 (1998). doi: 10.1126/science.2819925
- 3. T. Haft, M. Simon, G Müller, M. E. Moser, and I. Strohl. 猕猴视觉皮层的空间和方向选择性。Nature 436(7052): 806–809 (2005). doi: 10.1038/nature03721
- 4. E. C. Taylor, M. Gauss, and R. Jensen, L. E. Moser, and M. B. 猕猴视觉皮层的头部调调。Nature 441(7094): 763–768 (2006). doi: 10.1038/nature0532
- 5. S. J. Burgess, R. Jensen, and L. E. Moser. 猴类导航期间的头部方向细胞。Nature 425(6981): 247–250 (2003). doi: 10.1038/nature0113
- 6. Y. J. Yang and S. Y. Chen. 视觉皮层的功能图。Science 313(5790): 2055–2060 (2006). doi: 10.1126/science.112934
- 7. G. J. Glyn, M. J. Hassler, and P. B. Matley. 从物体到地标：下顶盖下区的视觉信息。Journal of Front. Neurosci. 3(4): 1093–1100 (2009). doi: 10.3189/jnnc.2009.13
- 8. R. K. Müller, J. Keck. 海马复合体发放率的变化。Science 271(5249): 1958–1961 (1995). doi: 10.1126/science.271529
- 9. U. B. Müller. 下顶盖下区的头部方向细胞。Journal of Neurosciences 28(12): 4442–4450 (2008). doi: 10.1553/JNEURO.0424-07
- 10. K. J. Leavy. 海马形成的学习与稳定性。Nature 377(6536): 667–668 (1995). doi: 10.1038/377668
- 11. A. K. Ainhauer, S. Pétrigl, and A. D. Okan. 内嗅皮层和海马中的视觉现实和 theta 锁定细胞。Nature Commun. 13(1): 5432 (2022). doi: 10.1038/s41467-022-3351
- 12. L. F. Fisher, R. Jensen, E. Buluk, and F. Haft. 内嗅皮层的视觉信息表示。eLife 9(5): e09518 (2014). doi: 10.7751/elife.09518
- 13. J. J. Decardi, C. Ortiz, and N. Rust. 大脑如何解决方向问题？Nature Communications 10(1): 2216 (2019). doi: 10.1038/s41467-019-1216
- 14. L. Winter, M. Mishkin, and A. Vidal. 视觉皮层的神经编码。Cell 168(5): 1003–1012 (2017). doi: 10.1016/j.cell.2017.0402

# 研究论文

- 15. S. Tadmori et al. 侧额皮层视觉刺激转换的效率。Nature 574, e22974 (2019). doi: 10.1038/s41586-019-2263-7
- 16. E. Miller et al. 大脑中的视觉。2020.05289 (预印本 (2021)); https://doi.org/10.21504/ebvo.2020.05289
- 17. J. Y. Shin, H. Sharma, C. R. Smith. 侧视觉区运动和特征的选择性表示。Brain 138, 2810–2820 (2015). doi: 10.1093/brain/aw066
- 18. R. Tong et al. 视觉大脑。2021.03365 (预印本 (2023)); https://doi.org/10.21504/ebvo.2021.03365
- 19. D. Zocan, N. Itzelberg, J. Duncan, D. C. Cohen. 人类视觉刺激的生成模型。Proc. Natl. Acad. Sci. U.S. 116, 935–940 (2019). doi: 10.1073/pnas.18093316
- 20. J. H. Ivory, V. Weber, M. C. Milner. 晚记忆捕捉期间视觉驱动注意力控制。Brain 236, 2046–2052 (2023). doi: 10.1093/brain/awac019
- 21. E. Macht et al. 视觉系统的功能组织。Nat. Neurosci. 8, 662–674 (2005). doi: 10.1038/nn10113
- 22. C. Bruner et al. 人类脸体识别中的功能性视觉整合。Proc. Natl. Acad. Sci. U.S. 117, 19447–19452 (2020). doi: 10.1073/pnas.191811417
- 23. 灵长类中的双极视觉整合通路。PLOS ONE 12, e0183364 (2017). doi: 10.1371/journal.pone.0183364
- 24. S. D. Oshman. 人类视觉中视觉处理的层次结构。Nature 414, 67–71 (2001). doi: 10.1038/350700
- 25. Y. Yao et al. 灵长类皮层的空间表示。Nature 508, 1038–1043 (2014). doi: 10.1038/s41586-014-2290
- 26. N. R. Luck, J. Duncan. 人类视觉搜索中的注意力。Science 313, 969–972 (2006). doi: 10.1126/science.112952
- 27. J. J. Rich et al. 决策期间视觉的后向整合。Neuron 32, 1019–1028 (2012). doi: 10.1016/j.neuron.2012.062
- 28. A. N. Duncan. 谐波相位血流的空间分辨率。J. Neurosci. 30, 2758–2790 (2010). doi: 10.1523/JNEURO.0443-09
- 29. K. H. Seo, M. K. Sargent. 猕猴眼手运动协调。Nature Communications 14, 3918 (2023). doi: 10.1038/s41467-023-3770
- 30. R. Liu. 基底节对眼动运动的自主控制。Neuroscience 27, 772–778 (2004). doi: 10.1038/nn3633
- 31. Y. J. Kim et al. 基底节对眼动运动的控制。Brain 136, 2111–2125 (2013). doi: 10.1093/brain/awt190
- 32. S. S. Cardoso et al. 基底节在注意力中的作用。Nature Reviews Neuroscience 8, 675–686 (2007). doi: 10.1038/nron511
- 33. J. R. Miller et al. 猕猴前额皮层的侧侧运动组织。Nature 411, 716–720 (2001). doi: 10.1038/35073
- 34. D. B. Sun et al. 运动运动皮层对运动控制的作用。Nature 15, 1250–1261 (2012). doi: 10.1038/nn2506
- 35. G. Yamashita et al. 前额皮层中多巴胺信号的动力学。Nature 9, 846–850 (2006). doi: 10.1038/nn511
- 36. N. A. Sato et al. 猕猴运动计划的功能性表示。Science 287, 3268–3273 (2000). doi: 10.1126/science.28753
- 37. D. Keeler, E. T. Akay, and G. Wagner. 猴类社会行为的视觉方面。Brain 131, 509–524 (2008). doi: 10.1093/brain/aw364
- 38. E. J. Miller et al. 人类追视中的眼头协调。Brain 130, 3431–3445 (2007). doi: 10.1093/brain/aw042
- 39. A. H. E. McNaughton. 自由运动中视线控制的动力学。Eye 125, 7554–7568 (2019). doi: 10.1098/eye.19.54
- 40. C. J. Liu et al. 左半球维持的人类视觉行为。Eye 108, e70308 (2020). doi: 10.1016/j.eye.2020.e7038
- 41. B. Cohen et al. 面部区：人脸的模型。Nature Neuroscience 17, 4302–4317 (2014). doi: 10.1038/nn3933
- 42. A. D. Hey, R. S. Stanley, A. D. Anderson, and M. E. Moser. 环状回路的物体视觉控制。Nature 454, 1038–1043 (2008). doi: 10.1126/science.11538
- 43. B. Brunner et al. 猕猴区内人脸和注意力的环状回路的功能性整合。Brain 138, 871–886 (2015). doi: 10.1093/brain/aw290
- 44. T. N. Han, J. W. Hu, J.-H. Shin, and C. M. Kim. 猕猴视觉区视觉注意的MRI响应。Nature Neuroscience 11, 2254–2262 (2008). doi: 10.1038/nn2172
- 45. E.-H. Galález, M. 人类导向注意力的行为与调制。Nature Neuroscience 27, 223–238 (2014). doi: 10.1038/nn3863
- 46. S.-L. Ding. 人类注意和记忆中前额叶下弓、下齿和旁海马的解剖学。J. Neurosci. 52, 9993–10000 (2002). doi: 10.1523/JNEURO.52.9
- 47. A. S. Alexander, P. Rice, J. M. Staristi, and E. R. Ditch. 视扫动和注意力的视网膜表示。Nature Neuroscience 11, 1155–1160 (2008). doi: 10.1038/nn1155
- 48. J. P. Petty, et al. 人类眼动运动中的地标导向头部方向。Nature Neuroscience 23, 2781–2798 (2020). doi: 10.1038/s41593-020-1118
- 49. K. H. Kim, J. J. Donnelly. 前额叶和顶顶叶对头部方向系统的地标控制。Brain 128, 2018–2033 (2005). doi: 10.1093/brain/aw001
- 50. S. G. Müller, I. E. Regter. 前额叶对视扫运动的区域控制。Nature Neuroscience 5, 1454–1460 (2002). doi: 10.1038/nn766
- 51. J. S. Taube. 头部方向信号和感觉运动整合。Nature Neuroscience 19, 17411–17428 (2016). doi: 10.1038/nn4396
- 52. F. Galgó, et al. 皮层中位置、方向和速度的功能表示。Science 312, 758–762 (2006). doi: 10.1126/science.112557

