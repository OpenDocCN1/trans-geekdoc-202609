
通过分析方法（如层次聚类）对无成型细胞结构材料进行处理。选用 Ward 方法（Ward's Method）对响应曲线进行聚类。图 9.3A 显示了聚类树图，以模拟总次数（168 次）为横轴，不相似性为纵轴。

插图比较了聚类 2 的两条载荷-位移曲线，表明了不同模式的行具有相似性。为了简单起见，我们选择了一个不相似性的截断值（虚线），导致了六个聚类（用不同颜色表示）。事实上，不同的截断值会导致不同数量的聚类。在极端情况下，当不相似性达到最大值时，所有 168 个模式可以归为一类。另一种极端情况是不相似性达到最小值时，每个模式将代表一个聚类，总共 168 类。图 9.3B 展示了聚类 1 和聚类 2 之间的几何分组。总共有 23 个模式具有三个填充：其中 20 个来自聚类 1（87%），3 个来自聚类 2（13%）。还发现具有两个和六个填充的模式分别仅来自聚类 1 和聚类 2 的数据。因此，每个组都包含来自聚类 ① 和 ② 的模式。

![](img/90ed165a39fa708ec438fcda79319c25_251_0.png)

图 9.3 三个单元的聚类分析。(A) 基于总共 168 次模拟得出的聚类树，以及给定截断值下的 4 种几何分类。(B) 聚类 1 和 2 中所有模式的几何分类。插图显示了四个任意模式。(C) 4 × 4 细胞模式的五类和八组的插图。(D) 来自不同聚类的所选模式的实验载荷-位移曲线。

FG 多孔复合结构。聚类分析提供了拓扑结构的心理分类分类，并为关联各种几何模式提供了见解。我们的结果仅是基于分类方法选定一组数据集的可能分类。

## 9.3.2 代表性 4× 4 单元的响应分类

在确定了 $3 \times 3$ 细胞模式的概率分类后，我们现在尝试实施学习到的物理原理来表征 $4 \times 4$ 单元（49.5, 49.5 mm），而无需进行聚类分析。与 $3 \times 3$ 模式的 512 次相比，响应域变得大得多，总计 65,536 次，对 $4 \times 4$ 单元进行所有模拟分析是不是不实际的。考虑到满/空行或列以及填充情况，我们在没有进行层次聚类分析的情况下定义了五类八组几何分组，如图 9.3C 所示。

为了将模式与响应联系起来，图 9.4A 画了所有 57 个模式（55 个任意模式、LB、LB 和 UB）响应曲线之前的屈曲区域图。填充数最少的 LB 模式与材料的总功能量有关，而 UB 模式具有最大值。在 LB 和 UB 模式之间，这 55 个模式按照预测形成了八个散点集，某些偏离的数据点可以归类到其他组。我们使用 3D 打印机制造了总 26 个（LB、UB、组 4、5 和 8）模式，并对所选模式进行了轴压。我们将实验响应与数值结果进行了比较，如图 9.4B 所示。图 9.4 显示，尽管模式的孔隙率各异，但我们的经验分组可以将具有相似响应特征的不同模式进行分类。

![](img/90ed165a39fa708ec438fcda79319c25_252_0.png)

图 9.4 $4 \times 4$ 细胞模式的几何分类。(A) 相同轴位移下 57 个模式的不同屈曲载荷响应图。(B) 所选聚类的实验与数值结果的比较。

## 9.3.3 机器学习建模与响应预测

正如第 9.2 节所述，通过训练好的 DNN，我们可以从测试数据估计任何模式的响应曲线。在图 9.5A 和 B 中，我们展示了 20% 和 40% 训练比例的示例，其中每个蓝色点的坐标比较了 $f_{pred}$ 与对应的参考值 $f_{ref}$。点越靠近二分线（$y = x$），预测越准确。这些蓝色点的带宽反映了整体性能。低训练比例是可以接受的。在图 9.5C 中，我们绘制了每个训练比例的平均 PDF 并标记了相应的 $P_t < 1$。可以观察到，随着训练比例增加，PDF 会升高（更准确），但不受显著影响。我们对每个预测曲线和参考曲线进一步进行了回归分析。得到的回归系数是预测遵循趋势的良好估计。在图 9.5D 中，我们将所有数据分为五个子集，差异可能由几何填充和布局引起。我们展示了 NMSE 在 0 到 0.3 之间的数据，大多数子集的数据为 0 到 0.05，表明机器学习模型预测良好。在 MSE 0.05 以上（特别是 0.15 到 0.3 之间，见图 9.5D），可以看出 10–12（绿色）和 13–15（紫色）填充与其他子集相比占主地位，证实了预测误差主要由填充数量控制。

![](img/90ed165a39fa708ec438fcda79319c25_253_0.png)
![](img/90ed165a39fa708ec438fcda79319c25_253_1.png)
![](img/90ed165a39fa708ec438fcda79319c25_253_2.png)
![](img/90ed165a39fa708ec438fcda79319c25_253_3.png)

图 9.5 DNN 的机械响应。(A 和 B) 训练比例为 40% 和 20% 下的预测力与参考力的比较。(C) 训练比例下的归一化误差密度函数。(D) 填充数量对预测的影响。

## 9.4 结论

在本章中，我们研究了非均匀几何设计引起的复杂材料的响应复杂性。通过有限建模和聚类分析，我们发现了 $3 \times 3$ 细胞模式的几何特征（的布局和填充数）与其机械响应之间的隐藏联系。在几何规则的引导下，我们进一步**征的具有不同填充的$4 \times 4$ 细胞模式的响应，并通过实验验证的几何特征与其机械性能的的。随着设计领域的扩大和的机制变得复杂，2引入的机器学习方法（ML）来加速测试数据的模式响应。尽管我们只使用 $4 \6 4$ 的的的该框架，但我们认为基于机器学习的框架能够加速局部层面的材料设计，并在全局层面提高性能/或功能。

## 致谢

这项工作受中国自然科学基金（52008174）和广东省现代工程技术实验室（2021B1312400）资助。感谢所有支持来源。

## 参考文献

- [1] Speck T, Burget I. Plant stems: functional design and mechanics. Annu Rev Mater Res 2021;41:169–93.
- [2] Gibson LJ. The hierarchical structure and mechanics of plant materials. J R Soc Mater 1992;9:2749–66.
- [3] Overveld JTB, Shan S, Bertoldi C. Compaction through buckling in 2D periodic, soft porous structures: effect of pore shape. Adv Mater 2012;24:2337–42.
- [4] Fleigle R, Gong C, van Hecke M. Programmable mechanicalaterials. Phys Rev Lett 2014;113:175305.
- [5] Coulais C, Tony E, de Rees C, Shoker, van Hecke M. Combinatorial design of tuned metamaterials. Nature 2016:535:529.
- [6] Bertoldi K, Vitelli J, van Hecke M. Flexible mechanical materials. Nat Rev Mater 2017;2:1706.
- [7] Coulais C, Sabadini A, Vink F, van Hecke M. Multi-step guided pathways for shape-changing metamaterials. Nature 2018;556:512–15.
- [8] Jackson JA, Messina MC, Dudakovic NA, Smith WL, Bekker L, Moran B, et al. Field responsive materials. Sci Adv 2018;4:0469.
- [9] Kim Y, Yi R, Zhang R. Printing ferromagnetic domains for underying fast-transforming soft-metaterials. Nature 2018;558:274–9.
- [10] Kadic M, Milton GW, van Hecke M, Wegener M. 3 D metamaterials. Nat Phys 2019;15:198–23.
- [11] Hu N, Buragno R. Buckling-induced smart materials: recent advances and trends. Smart Mater 2015;24:06501.
- [12] Coulais C, Tony E, de Rees C, Shoker, van Hecke M. Combinatorial design of tuned metamaterials. Nature 2016:535:529.

