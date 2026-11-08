
$\\begin{matrix} {{Gain}\\left( \\mathit{outlook} \\right) = 0.247{bits}} \\\\ {{Gain}\\left( \\mathit{temperature} \\right) = 0.029{bits}} \\\\ {{Gain}\\left( \\mathit{humidity} \\right) = 0.152{bits}} \\\\ {{Gain}\\left( \\mathit{windy} \\right) = 0.048{bits,}} \\\\ \\end{matrix}$<mml:math><mml:mtable width="336pt"><mml:mtr><mml:mtd columnalign="center"><mml:mi mathvariant="normal">Gain</mml:mi><mml:mo>(</mml:mo><mml:mi mathvariant="italic">outlook</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mn>0.247</mml:mn><mml:mi mathvariant="normal">bits</mml:mi></mml:mtd></mml:mtr><mml:mtr><mml:mtd><mml:mi mathvariant="normal">Gain</mml:mi><mml:mo>(</mml:mo><mml:mi mathvariant="italic">temperature</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mn>0.029</mml:mn><mml:mi mathvariant="normal">bits</mml:mi></mml:mtd></mml:mtr><mml:mtr><mml:mtd columnalign="left"><mml:mi mathvariant="normal">Gain</mml:mi><mml:mrow><mml:mo>(</mml:mo><mml:mi mathvariant="italic">humidity</mml:mi><mml:mo>)</mml:mo></mml:mrow><mml:mo>=</mml:mo><mml:mn>0.152</mml:mn><mml:mi mathvariant="normal">bits</mml:mi></mml:mtd></mml:mtr><mml:mtr><mml:mtd columnalign="left"><mml:mi mathvariant="normal">Gain</mml:mi><mml:mo>(</mml:mo><mml:mi mathvariant="italic">windy</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mn>0.048</mml:mn><mml:mi mathvariant="normal">bits,</mml:mi></mml:mtd></mml:mtr></mml:mtable></mml:math>

![方程](images/F000054si39.png)

因此我们选择 `outlook` 作为树的根节点的分裂属性。希望这与你的直觉一致，即它是最佳选择。它是唯一一个子节点完全纯净的选择，这使其相对于其他属性具有相当大的优势。`Humidity` 是第二好的选择，因为它产生了一个几乎完全纯净的较大子节点。

然后我们继续，递归地进行。[图 4.3](#Ch004_91-164_B9780443158889000054.xhtml#f0020) 显示了在 `outlook` 为 `sunny` 时到达的节点上进一步分支的可能性。显然，对 `outlook` 再次进行分裂不会产生任何新信息，因此我们只考虑其他三个属性。每个属性的信息增益如下

$\\begin{matrix} {{Gain}\\left( \\mathit{temperature} \\right) = 0.571{bits}} \\\\ {{Gain}\\left( \\mathit{humidity} \\right) = 0.971{bits}} \\\\ {{Gain}\\left( \\mathit{windy} \\right) = 0.020\\text{bits},} \\\\ \\end{matrix}$<mml:math><mml:mtable width="336pt"><mml:mtr><mml:mtd columnalign="center"><mml:mi mathvariant="normal">Gain</mml:mi><mml:mo>(</mml:mo><mml:mi mathvariant="italic">temperature</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mn>0.571</mml:mn><mml:mi mathvariant="normal">bits</mml:mi></mml:mtd></mml:mtr><mml:mtr><mml:mtd columnalign="center"><mml:mi mathvariant="normal">Gain</mml:mi><mml:mo>(</mml:mo><mml:mi mathvariant="italic">humidity</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mn>0.971</mml:mn><mml:mi mathvariant="normal">bits</mml:mi></mml:mtd></mml:mtr><mml:mtr><mml:mtd columnalign="center"><mml:mi mathvariant="normal">Gain</mml:mi><mml:mo>(</mml:mo><mml:mi mathvariant="italic">windy</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mn>0.020</mml:mn><mml:mtext>bits</mml:mtext><mml:mo>,</mml:mo></mml:mtd></mml:mtr></mml:mtable></mml:math>

![方程](images/F000054si40.png)![图 4.3 天气数据的扩展树桩。](images/F000054f04-03-9780443158889.jpg)

[图 4.3](#Ch004_91-164_B9780443158889000054.xhtml#Bf0020) 天气数据的扩展树桩。

因此我们在此选择 `humidity` 作为分裂属性。这些节点无需进一步分裂，因此该分支结束。

持续应用同样的思路可得到天气数据的决策树 [图 4.4](#Ch004_91-164_B9780443158889000054.xhtml#f0025)。理想情况下，过程在所有叶节点纯净时终止，即它们包含的实例全部具有相同的分类。然而，可能无法达到这种理想情况，因为训练集可能包含具有相同属性集但类别不同的两个示例。因此，当数据无法再进一步分裂时我们停止。或者，可以在信息增益为零时停止。这稍微保守一些，因为可能遇到数据可分裂为具有相同类别分布的子集的情况，这将使信息增益为零。

![图 4.4 天气数据的决策树。](images/F000054f04-04-9780443158889.jpg)

[图 4.4](#Ch004_91-164_B9780443158889000054.xhtml#Bf0025) 天气数据的决策树。

### 计算信息

现在是时候解释如何计算用于评估不同分裂的基础信息度量了。我们在本节中描述基本思想，然后在下一节中探讨通常为抵消选择具有大量可能取值属性时的偏差而进行的修正。

在研究计算指定示例类别所需信息量的详细公式之前——该示例到达树节点时具有一定数量的 `yes`’s 和 `no`’s——首先考虑我们期望该数量具有的性质：

*   • 当 `yes`’s 或 `no`’s 的数量为零时，信息为零；
*   • 当 `yes`’s 和 `no`’s 的数量相等时，信息达到最大值。

此外，该度量应适用于多类情况，而不仅仅是二类情况。

信息度量与通过做出决策而获得的信息量相关，并且可以通过考虑决策的本质来推导出信息的一个更微妙的性质。决策可以单阶段做出，也可以分多个阶段做出，两者的信息量是相同的。例如，涉及的决策

`Info([2,3,4])`<mml:math><mml:mi mathvariant="normal">Info</mml:mi><mml:mo>(</mml:mo><mml:mo>\[</mml:mo><mml:mn>2,3,4</mml:mn><mml:mo>\]</mml:mo><mml:mo>)</mml:mo></mml:math>

![方程](images/F000054si41.png)

可以分为两个阶段进行。首先判断它是第一种情况还是其他两种情况之一：

`Info([2,7])`<mml:math><mml:mi mathvariant="normal">Info</mml:mi><mml:mo>(</mml:mo><mml:mo>\[</mml:mo><mml:mn>2,7</mml:mn><mml:mo>\]</mml:mo><mml:mo>)</mml:mo></mml:math>

![方程](images/F000054si42.png)

然后判断另外两种情况中的哪一种：

`Info([3,4])`<mml:math><mml:mi mathvariant="normal">Info</mml:mi><mml:mo>(</mml:mo><mml:mo>\[</mml:mo><mml:mn>3,4</mml:mn><mml:mo>\]</mml:mo><mml:mo>)</mml:mo></mml:math>

![方程](images/F000054si43.png)

在某些情况下，第二步决策不需要做出，即当决策结果为第一种情况时。考虑到这一点，得出方程

`Info([2,3,4]) = info([2,7]) + (7/9) × info([3,4])`.<mml:math><mml:mi mathvariant="normal">Info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>2,3,4</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mi mathvariant="normal">info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>2,7</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>+</mml:mo><mml:mo stretchy="false">(</mml:mo><mml:mn>7</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>9</mml:mn><mml:mo stretchy="false">)</mml:mo><mml:mo>&#215;</mml:mo><mml:mi mathvariant="normal">info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>3,4</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>.</mml:mo></mml:math>

![方程](images/F000054si44.png)

当然，这些特定数字没有什么特别之处，类似的关系应不论实际取值如何都成立。因此我们可以将进一步的标准添加到前面列出的列表中：
