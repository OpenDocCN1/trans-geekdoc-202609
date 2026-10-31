
(8.9)![equation](images/c08-math-0009.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable columnalign="left"> <mtr> <mtd columnalign="right"> <mi>z</mi> <mo>=</mo> <mfenced open="{" close="" separators=""> <mrow> <mtable columnalign="left"> <mtr> <mtd class="array"> <mi mathvariant="normal">max</mi> <mfenced open="(" close=")" separators=""> <mrow> <mfenced open="|" close="|" separators=""> <mrow> <mi mathvariant="normal">&#916;</mi> <mi mathvariant="normal">&#934;</mi> <mo stretchy="false">(</mo> <mi>t</mi> <mo stretchy="false">)</mo> <mo>&#183;</mo> <mfenced open="(" close=")" separators=""> <mrow> <mn>1</mn> <mo>&#8722;</mo> <mi mathvariant="normal">&#920;</mi> <mo stretchy="false">(</mo> <mi>t</mi> <mo stretchy="false">)</mo> </mrow> </mfenced> <mo>&#183;</mo> <mi>&#946;</mi> </mrow> </mfenced> <mo>,</mo> <mn>1</mn> </mrow> </mfenced> </mtd> <mtd class="array"> <mo>:</mo> <mi mathvariant="normal">&#916;</mi> <mi mathvariant="normal">&#934;</mi> <mo>&#62;</mo> <mn>0</mn> </mtd> </mtr> <mtr> <mtd class="array"> <msup> <mrow> <mfenced open="(" close=")" separators=""> <mrow> <mi mathvariant="normal">max</mi> <mfenced open="(" close=")" separators=""> <mrow> <mfenced open="|" close="|" separators=""> <mrow> <mi mathvariant="normal">&#916;</mi> <mi mathvariant="normal">&#934;</mi> <mo stretchy="false">(</mo> <mi>t</mi> <mo stretchy="false">)</mo> <mo>&#183;</mo> <mi mathvariant="normal">&#920;</mi> <mo stretchy="false">(</mo> <mi>t</mi> <mo stretchy="false">)</mo> <mo>&#183;</mo> <mi>&#946;</mi> </mrow> </mfenced> <mo>,</mo> <mn>1</mn> </mrow> </mfenced> </mrow> </mfenced> </mrow> <mrow> <mo>&#8722;</mo> <mn>1</mn> </mrow> </msup> </mtd> <mtd class="array"> <mo>:</mo> <mi mathvariant="normal">&#916;</mi> <mi mathvariant="normal">&#934;</mi> <mo>&#8804;</mo> <mn>0</mn> </mtd> </mtr> </mtable> </mrow> </mfenced> <mo>.</mo> </mtd> <mtd/> </mtr> </mtable> </mrow> </math>

## 8.3 实际性能评估的方法

在本节中，实际性能评估的方法论设置进行了介绍。此外，还描述了功耗分析的过程。

### 8.3.1 评估场景

测量使用现成的基于 `Android` 的 `UE` 进行，该设备运行 `CAT` 应用并执行在线 `ML` 基于的数据速率预测。有关该框架的进一步信息已在 Sliwa 等人 ([2018c](#c08.xhtml#c08-bib-0029)) 中发表。一个虚拟传感器应用程序每秒生成固定量的传感器数据，该数据存储在本地缓冲区中。概率传输方案每 ![images](images/c08-i0022.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>t</mi><mi>p</mi></msub></mrow></math> 评估一次信道，并为整个缓冲区计算传输概率。所有原始测量数据（Sliwa ([2018](#c08.xhtml#c08-bib-0025))）和开发的测量应用程序以开源方式提供（可在 [`https://github.com/BenSliwa/MTCApp`](https://github.com/BenSliwa/MTCApp) 获取）。总体而言，数据集包含超过 7500 次传输，这些传输是在超过 2000 公里的行驶范围内完成的。

传输方案在真实场景中使用公共蜂窝网络基础设施进行评估。[图 8.11](#c08.xhtml#c08-fig-0011) 显示了评估场景的地图。驾驶测试在不同类型的道路（郊区和高速公路）上进行，具有不同的速度特性。

[表 8.1](#c08.xhtml#c08-tbl-0001) 显示了所考虑的评估场景的参数。![images](images/c08-i0023.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi mathvariant="normal">&#934;</mi><mtext>SINR</mtext></msub></mrow></math> 表示 `CAT` 和 `pCAT` 的传输指标。![images](images/c08-i0024.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi mathvariant="normal">&#934;</mi><mtext>ML</mtext></msub></mrow></math> 用于 `ML-CAT` 和 `ML-pCAT`。创建连接地图所需的信息基于 Sliwa 等人 ([2018b](#c08.xhtml#c08-bib-0028)) 中的实验获得的数据。

### 8.3.2 功耗分析

除了传输效率（在下一节中以实现的数据速率为代表）之外，改变的传输行为很可能对能源效率产生严重影响。虽然与通信相关的电池消耗对于汽车来说几乎可以忽略不计，但它对小型空中飞行器的飞行时间潜力具有至关重要的影响。随着这类车辆越来越多地融入道路交通场景（Menouar 等人 ([2017](#c08.xhtml#c08-bib-0019))），将基于 `CAT` 的数据传输应用于基于 `UAV` 的数据供给是一种提高可能飞行时间的很有前景的选择。

![ Table 8.1 Parameters of the evaluation scenario.](images/c08-i0025.png)

[表 8.1](#c08.xhtml#R_c08-tbl-0001) 评估场景的参数。

测量数据传输对移动设备功耗的影响是一项非平凡的任务，因为它涉及将运行进程与系统其余部分隔离。因此，为了评估所考虑的传输方案的能源效率，我们依赖于在后处理步骤中执行的顺序过程：

*  **`ML` 基于的传输功率估计**：Falkenberg 等人 ([2018](#c08.xhtml#c08-bib-0013)) 的模型被用于根据被动下行指示符预测每次传输所应用的 ![images](images/c08-i0033.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>P</mi><mrow><mi>T</mi><mi>X</mi></mrow></msub></mrow></math> 值，类似于 [`第 8.2.3 节`](#c08.xhtml#c08-sec-0008) 中描述的过程。由于 ![images](images/c08-i0034.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>P</mi><mrow><mi>T</mi><mi>X</mi></mrow></msub></mrow></math> 与基站距离存在很强的相关性，`RSRP` 为学习过程提供了有意义的指标。

* **设备特定特征的确定**：![images](images/c08-i0035.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>P</mi><mrow><mi>T</mi><mi>X</mi></mrow></msub></mrow></math> 与实际功耗之间的关系对 `UE` 来说高度特定，并且取决于其不同的功率放大器。因此，这种依赖关系通过在实验室环境中对 ![images](images/c08-i0036.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>P</mi><mrow><mi>T</mi><mi>X</mi></mrow></msub></mrow></math> 进行受控变化来捕捉（Falkenberg 等人 ([2017b](#c08.xhtml#c08-bib-0012))）。

* **基于模型的分析**：最后，基于状态的上下文感知功耗模型 (`CoPoMo`)（Dusza 等人 ([2013](#c08.xhtml#c08-bib-0008))）被应用于计算 `UE` 在不同可能传输状态下的平均功耗。

## 8.4 实际性能评估结果

在本节中，经验性能评估的结果将被介绍和讨论。首先讨论所测量的网络质量指标的行为。随后分析所考虑的传输方案的结果，最后提供总体总结。

### 8.4.1 网络质量指标的统计特性

