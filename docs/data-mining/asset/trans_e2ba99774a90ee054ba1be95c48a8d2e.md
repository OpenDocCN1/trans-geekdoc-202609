
[表 4.6](#Ch004_91-164_B9780443158889000054_a.xhtml#t0035) 给出了带有此额外属性的天气数据。基于 `ID code` 分支产生的树桩见 [图 4.5](#Ch004_91-164_B9780443158889000054_a.xhtml#f0030)。给定此属性值时指定类别所需的期望信息为
$\\frac{1}{14}({info}(\\left\\lbrack 0,1 \\right\\rbrack) + {info}(\\left\\lbrack 0,1 \\right\\rbrack) + {info}(\\left\\lbrack 1,0 \\right\\rbrack) + \\cdots + {info}(\\left\\lbrack 1,0 \\right\\rbrack) + {info}(\\left\\lbrack 0,1 \\right\\rbrack)),$<mml:math><mml:mfrac><mml:mrow><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mn>14</mml:mn></mml:mrow></mml:mfrac><mml:mo stretchy="false">(</mml:mo><mml:mi mathvariant="normal">info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>0,1</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>+</mml:mo><mml:mi mathvariant="normal">info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>0,1</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>+</mml:mo><mml:mi mathvariant="normal">info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>1,0</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>+</mml:mo><mml:mo>&#8943;</mml:mo><mml:mo>+</mml:mo><mml:mi mathvariant="normal">info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>1,0</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>+</mml:mo><mml:mi mathvariant="normal">info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>0,1</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>,</mml:mo></mml:math>
![方程](images/F000054si54.png)

### 表 4.6 带识别码的天气数据
| 识别码 || 天气状况 || 温度 || 湿度 || 有风 || 打球 |
| --- | --- | --- | --- | --- | --- |
| a || 晴天 || 炎热 || 高 || 否 || 否 |
| --- | --- | --- | --- | --- | --- |
| b || 晴天 || 炎热 || 高 || 是 || 否 |
| c || 阴天 || 炎热 || 高 || 否 || 是 |
| d || 雨天 || 温和 || 高 || 否 || 是 |
| e || 雨天 || 凉爽 || 正常 || 否 || 是 |
| f || 雨天 || 凉爽 || 正常 || 是 || 否 |
| g || 阴天 || 凉爽 || 正常 || 是 || 是 |
| h || 晴天 || 温和 || 高 || 否 || 否 |
| i || 晴天 || 凉爽 || 正常 || 否 || 是 |
| j || 雨天 || 温和 || 正常 || 否 || 是 |
| k || 晴天 || 温和 || 正常 || 是 || 是 |
| l || 阴天 || 温和 || 高 || 是 || 是 |
| m || 阴天 || 炎热 || 正常 || 否 || 是 |
| n || 雨天 || 温和 || 高 || 是 || 否 |

![图 4.5 识别码属性的树桩.](images/F000054f04-05-9780443158889.jpg)
图 4.5 `ID code` 属性的树桩。
这为零，因为 14 项中的每一项都为零。这并不令人惊讶；`ID code` 属性标识实例，该实例在没有任何歧义的情况下决定类别，正如 [表 4.6](#Ch004_91-164_B9780443158889000054_a.xhtml#t0035) 所示。因此，该属性的信息增益仅为根节点的信息，`info([9,5])` = 0.940 bits。这大于任何其他属性的信息增益，因此 `ID code` 不可避免地会被选为分裂属性。但基于识别码进行分支对于预测未知实例的类别没有好处。

总体效果是信息增益度量倾向于偏好可能取值数量大的属性。为补偿这一点，广泛使用一种称为 `gain ratio` 的度量修改方法。`gain ratio` 是通过考虑属性将数据集分裂成的子节点数量和大小来推导的，而不考虑任何关于类别的信息。在 [图 4.5](#Ch004_91-164_B9780443158889000054_a.xhtml#f0030) 所示的情况下，所有计数的值均为 1，因此分裂的信息值为
`Info([1,1,…,1])` = −1/14×log1/14×14<mml:math><mml:mi mathvariant="normal">Info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo stretchy="false">\[</mml:mo><mml:mn>1,1</mml:mn><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:mn>1</mml:mn><mml:mo stretchy="false">\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mo>&#8722;</mml:mo><mml:mn>1</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>14</mml:mn><mml:mo>&#215;</mml:mo><mml:mi>log</mml:mi><mml:mn>1</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>14</mml:mn><mml:mo>&#215;</mml:mo><mml:mn>14</mml:mn></mml:math>
![方程](images/F000054si55.png)
因为相同的分数 1/14 出现了 14 次。这相当于 log 14，或 3.807 bits，这是一个非常高的值。这是因为分裂的信息值是确定每个实例分配到哪个分支所需的比特数，分支越多，该值越大。`gain ratio` 是通过将原始信息增益，本例中为 0.940，除以属性的信息值 3.807 计算得出的，得出 `ID code` 属性的 `gain ratio` 值为 0.247。

回到 [图 4.2](#Ch004_91-164_B9780443158889000054.xhtml#f0015) 中的天气数据的树桩，`outlook` 将数据集分裂为大小为 5、4 和 5 的三个子集，因此具有固有信息值为
`Info([5,4,5])` = 1.577<mml:math><mml:mi mathvariant="normal">Info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>5,4,5</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mn>1.577</mml:mn></mml:math>
![方程](images/F000054si56.png)
而不考虑子集中涉及的类别。正如我们所见，这种固有信息值对于分支更多的属性，例如假设的 `ID code`，更大。同样，我们可以通过除以固有信息值来校正信息增益，从而得到 `gain ratio`。

[图 4.2](#Ch004_91-164_B9780443158889000054.xhtml#f0015) 的树桩的这些计算结果总结在 [表 4.7](#Ch004_91-164_B9780443158889000054_a.xhtml#t0040) 中。`Outlook` 仍然名列前茅，但 `humidity` 现在是一个更接近的竞争者，因为它将数据分裂为两个子集而不是三个。在此示例中，具有 `gain ratio` 为 0.247 的假设 `ID code` 属性仍将优于这四个属性。然而，其优势大大降低。在实际实现中，我们可以使用特设测试来防止在这种无用属性上进行分裂。

### 表 4.7 树桩的增益比计算
| 天气状况  || 温度 || 湿度 || 有风 |
| --- | --- | --- | --- |
| 信息： || 0.693 || 信息： || 0.911 || 信息： || 0.788 || 信息： || 0.892 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 增益：0.940–0.693 || 0.247 || 增益：0.940–0.911 || 0.029 || 增益：0.940–0.788 || 0.152 || 增益：0.940–0.892 || 0.048 |
| 分裂信息：`info([5,4,5])` || 1.577 || 分裂信息：`info([4,6,4])` || 1.557 || 分裂信息：`info([7,7])` || 1.000 || 分裂信息：`info([8,6])` || 0.985 |
| 增益比：0.247/1.577 || 0.156 || 增益比：0.029/1.557 || 0.019 || 增益比：0.152/1 || 0.152 || 增益比：0.048/0.985 || 0.049 |

不幸的是，在某些情况下，`gain ratio` 修改会过度补偿，并可能导致仅仅因为其固有信息远低于其他属性而偏好某个属性。标准修复方法是选择使 `gain ratio` 最大化的属性，前提是该属性的信息增益至少与所检查的所有属性的平均信息增益一样大。
