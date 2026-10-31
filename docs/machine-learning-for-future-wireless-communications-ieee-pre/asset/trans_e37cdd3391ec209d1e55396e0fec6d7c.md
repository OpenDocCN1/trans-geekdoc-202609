
(8.5)![等式](`images/c08-math-0005.png`)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable columnalign="left"> <mtr> <mtd columnalign="right"> <mi mathvariant="normal">&#916;</mi> <mtext>SINR</mtext> <mo stretchy="false">(</mo> <mi>t</mi> <mo stretchy="false">)</mo> <mo>=</mo> <mover accent="true"> <mtext>SINR</mtext> <mo>&#175;</mo> </mover> <mo stretchy="false">(</mo> <mi>t</mi> <mo>,</mo> <mi>t</mi> <mo>+</mo> <mi>&#964;</mi> <mo stretchy="false">)</mo> <mo>&#8722;</mo> <mtext>SINR</mtext> <mo stretchy="false">(</mo> <mi>t</mi> <mo stretchy="false">)</mo> </mtd> <mtd/> </mtr> </mtable> </mrow> </math>

`pCAT` 的传输概率结果显示在 [图 8.5](#c08.xhtml#c08-fig-0005) 中。可以观察到 `pCAT` 正式满足定义的任务：如果预期信道质量会改善则延迟传输，如果预期会下降则提前执行。进一步的实证评估结果在 Pillmann 等 ([2017](#c08.xhtml#c08-bib-0020)) 中描述。

![图 8.5 基于 SINR 的 pCAT 在不同图像值下的分析传输概率（图像）](`images/c08f005.jpg`)

[图 8.5](#c08.xhtml#R_c08-fig-0005) 基于 `SINR` 的 `pCAT` 的分析传输概率，不同值下 ![图像](`images/c08-i0013.png`)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="normal">&#916;</mi><mtext>SINR</mtext><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></math>（![图像](`images/c08-i0014.png`)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>&#945;</mi><mo>=</mo><mn>4</mn></mrow></math>）。

### 8.2.3 基于 ML 的 CAT

由于信道特性高度动态，信道属性在传输过程中很可能发生变化。因此，信道评估的意义有限，尤其对于较大的数据包大小而言。此外，即使在较高的信道相干时间内，传输层相互依赖性（如传输控制协议 (`TCP`) 的慢启动）也会影响所得数据速率。尽管这些因素的复杂性超出了分析系统描述的限制，`ML` 能够揭示不同类型上下文信息之间的隐藏相互依赖关系。除了 `SINR` 之外，LTE 还提供可用于实现更好信道质量评估的进一步网络质量指标，如 `RSRP`、`RSRQ` 和 `CQI`。因此，`CAT` 可以扩展为 `ML-CAT`，它使用基于 `ML` 的数据速率预测作为传输度量。

首先，`CAT` 的概率传输方案被推广，因为对于 `CAT` 和 `pCAT`，度量计算隐式地归一化到 `SINR` 的值范围。因此，引入了一个抽象度量 ![图像](`images/c08-i0015.png`)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="normal">&#934;</mi></mrow></math>，其值范围由定义的 ![图像](`images/c08-i0016.png`)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi mathvariant="normal">&#934;</mi><mrow><mi>min</mi></mrow></msub></mrow></math> 和 ![图像](`images/c08-i0017.png`)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi mathvariant="normal">&#934;</mi><mrow><mi>max</mi></mrow></msub></mrow></math> 值指定。每个测量值 ![图像](`images/c08-i0018.png`)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="normal">&#934;</mi><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></math> 被转换为 `normed current metric` ![图像](`images/c08-i0019.png`)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="normal">&#920;</mi><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></math>，其公式为

(8.6)![等式](`images/c08-math-0006.png`)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable columnalign="left"> <mtr> <mtd columnalign="right"> <mi mathvariant="normal">&#920;</mi> <mo stretchy="false">(</mo> <mi>t</mi> <mo stretchy="false">)</mo> </mtd> <mtd columnalign="left"> <mo>=</mo> <mfrac> <mrow> <mi mathvariant="normal">&#934;</mi> <mo stretchy="false">(</mo> <mi>t</mi> <mo stretchy="false">)</mo> <mo>&#8722;</mo> <msub> <mi mathvariant="normal">&#934;</mi> <mi>min</mi> </msub> </mrow> <mrow> <msub> <mi mathvariant="normal">&#934;</mi> <mi>max</mi> </msub> <mo>&#8722;</mo> <msub> <mi mathvariant="normal">&#934;</mi> <mi>min</mi> </msub> </mrow> </mfrac> </mtd> </mtr> </mtable> </mrow> </math>

然后计算所得传输概率 ![图像](`images/c08-i0020.png`)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>p</mi><mrow><mi mathvariant="normal">&#934;</mi><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msub></mrow></math> 为

(8.7)![等式](`images/c08-math-0007.png`)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable columnalign="left"> <mtr> <mtd columnalign="right"> <msub> <mi>p</mi> <mrow> <mi mathvariant="normal">&#934;</mi> <mo stretchy="false">(</mo> <mi>t</mi> <mo stretchy="false">)</mo> </mrow> </msub> <mo>=</mo> <mfenced open="{" close="" separators=""> <mrow> <mtable columnalign="left"> <mtr> <mtd class="array"> <mn>0</mn> </mtd> <mtd class="array"> <mo>:</mo> <mi mathvariant="normal">&#916;</mi> <mi>t</mi> <mo>&#8804;</mo> <msub> <mi>t</mi> <mi>min</mi> </msub> </mtd> </mtr> <mtr> <mtd class="array"> <mi mathvariant="normal">&#920;</mi> <msup> <mrow> <mo stretchy="false">(</mo> <mi>t</mi> <mo stretchy="false">)</mo> </mrow> <mi>&#945;</mi> </msup> </mtd> <mtd class="array"> <mo>:</mo> <msub> <mi>t</mi> <mi>min</mi> </msub> <mo>&#60;</mo> <mi mathvariant="normal">&#916;</mi> <mi>t</mi> <mo>&#60;</mo> <msub> <mi>t</mi> <mi>max</mi> </msub> </mtd> </mtr> <mtr> <mtd class="array"> <mn>1</mn> </mtd> <mtd class="array"> <mo>:</mo> <mi mathvariant="normal">&#916;</mi> <mi>t</mi> <mo>&#62;</mo> <msub> <mi>t</mi> <mi>max</mi> </msub> </mtd> </mtr> </mtable> </mrow> </mfenced> </mtd> <mtd/> </mtr> </mtable> </mrow> </math>

Sliwa 等 ([2018b](#c08.xhtml#c08-bib-0028)) 进一步分析了车辆场景中上行数据速率预测的不同 `ML` 模型的性能。分析表明，对于所有考虑的模型，`M5` 回归树能够提供最高的预测精度，同时仍能够以非常资源高效的方式实现，以便在嵌入式设备上进行在线执行。

基于这些观察，上下文信息的处理管道在 [图 8.6](#c08.xhtml#c08-fig-0006) 中得出。预测特征是信道上下文参数 `RSRP`、`RSRQ`、`SINR` 和 `CQI`。进一步的信息由当前车辆速度和数据包的有效载荷大小提供。在训练阶段，活动传输的所得数据速率提供预测的标签。

[图 8.7](#c08.xhtml#c08-fig-0007) 显示了真实世界评估中所提出的数据速率预测机制的时间行为示例。可以看出，有效载荷大小对整体性能有严重影响，因为预期数据速率在每次传输后显著下降，这会清空当前传输缓冲区。对于低有效载荷大小，`TCP` 的慢启动具有主导影响；对于非常高的有效载荷大小，信道动态成为整体行为的主要影响因素。

![图 8.6 使用不同类型上下文参数的基于 M5 的数据速率预测学习管道](`images/c08f006.jpg`)

