

如果`![alpha equals 0](images/c13-i0396.png)<math display="inline" overflow="scroll"><mi>&#945;</mi><mo>=</mo><mn>0</mn></math>`，则不需要剪枝，因为没有来自终端叶子数量的惩罚`![script upper T overTilde](images/c13-i0397.png)<math display="inline" overflow="scroll"><mover accent="true"><mrow><mi mathvariant="script">T</mi></mrow><mo>&#732;</mo></mover></math>`，所以`![script upper T equals script upper T overTilde](images/c13-i0398.png)<math display="inline" overflow="scroll"><mi mathvariant="script">T</mi><mo>=</mo><mover accent="true"><mrow><mi mathvariant="script">T</mi></mrow><mo>&#732;</mo></mover></math>`。当`![alpha right-arrow infinity](images/c13-i0399.png)<math display="inline" overflow="scroll"><mi>&#945;</mi><mo>&#8594;</mo><mi>&#8734;</mi></math>`时，树的大小超过了分类误差`![upper R left-parenthesis ModifyingAbove script upper T right-parenthesis With tilde](images/c13-i0400.png)<math display="inline" overflow="scroll"><mi>R</mi><mo stretchy="false">(</mo><mover accent="true"><mrow><mi mathvariant="script">T</mi><mo stretchy="false">)</mo></mrow><mo>&#732;</mo></mover></math>`，因此我们将剪枝`![script upper T](images/c13-i0401.png)<math display="inline" overflow="scroll"><mrow><mi mathvariant="script">T</mi></mrow></math>`直到到达根节点，从而得到一个单节点树，大小为`![upper T overTilde equals 1](images/c13-i0402.png)<math display="inline" overflow="scroll"><mover accent="true"><mi>T</mi><mo>&#732;</mo></mover><mo>=</mo><mn>1</mn></math>`。

有关预剪枝和后剪枝的更多讨论，读者可以参考各种文章，例如`[4](#c13.xhtml#c13-bib-0004)`、`[5](#c13.xhtml#c13-bib-0005)`、`[11](#c13.xhtml#c13-bib-0012)`。

## 13.7 PYTHON 和 R 中的分类树

一般来说，对于 Python 和 `R`，分类树是基于特征变量`![normal x Superscript left-parenthesis j right-parenthesis](images/c13-i0403.png)<math display="inline" overflow="scroll"><msup><mi mathvariant="normal">x</mi><mrow><mo stretchy="false">(</mo><mi>j</mi><mo stretchy="false">)</mo></mrow></msup></math>`的二进制分割构建的，一次一个，对于某些`![j equals 1 comma 2 comma ellipsis comma p](images/c13-i0404.png)<math display="inline" overflow="scroll"><mi>j</mi><mo>=</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>p</mi></math>`。由于此方法将搜索由所有特征变量引起的所有可能的分割，构建树在计算上密集且耗时。通常，一旦分类树构建完成，给定一个精心选择的超参数`![alpha](images/c13-i0405.png)<math display="inline" overflow="scroll"><mrow><mi>&#945;</mi></mrow></math>`（用于剪枝），将选择最小化`([13.16](#c13.xhtml#c13-disp-0048))`的子树作为最终树，然后可以轻松读取一组简单的分类规则。

在 Python 中，分类树由著名的 `sklearn` 包下的 Python 类 `tree` 中的 `DecisionTreeClassifier` 实现；请参阅`[Programme 13.1](#c13.xhtml#c13-sec-3001)`。

这里的 `plot_tree()` 是一个帮助绘制由 `DecisionTreeClassifier` 获得的结果树的函数，`export_text()` 是另一个返回其分类规则文本报告的函数。虽然 Python 类 `DecisionTreeClassifier` 非常易于使用，但这个类中隐藏着许多选项。特别是，`ccp_alpha` 是用于成本复杂度剪枝的超参数`![alpha](images/c13-i0406.png)<math display="inline" overflow="scroll"><mrow><mi>&#945;</mi></mrow></math>`，默认值为 `0`；`criterion` 选择使用的不纯度度量函数，默认为 `gini`，用于`([13.11](#c13.xhtml#c13-disp-0035))`中的 Gini 指数，其他选择包括 `entropy`，用于`([13.2](#c13.xhtml#c13-disp-0002))`中的 Shannon 熵，以及 `log_loss`，用于`([13.4](#c13.xhtml#c13-disp-0006))`中的微分熵。

在 `R` 中，分类树由内置库 `rpart` 中的 `rpart()` 函数实现。

同样，`rpart()` 函数包含几个选项：例如，可以通过插入参数 `parms=list(split="information")` 来采用微分熵，而 `"gini"` 用于 Gini 指数作为默认模式。此外，虽然默认值`![alpha equals 0.01](images/c13-i0407.png)<math display="inline" overflow="scroll"><mi>&#945;</mi><mo>=</mo><mn>0.01</mn></math>`用于相应的成本复杂度剪枝参数，用户可以选择任何非负值的`![alpha](images/c13-i0408.png)<math display="inline" overflow="scroll"><mrow><mi>&#945;</mi></mrow></math>`，例如`![alpha equals 0.05](images/c13-i0409.png)<math display="inline" overflow="scroll"><mi>&#945;</mi><mo>=</mo><mn>0.05</mn></math>`，通过参数：`control=rpart.control(cp=0.05)`。还有一个重要选项需要提及：`rpart` 中的 method 选项可以是 "`class`"、`"anova"`、`"poisson"` 或 "`exp"` 之一。对于分类问题，目标变量是分类变量，因此使用 `method="class"`；同时，对于常规回归树，我们使用 `method="anova"`，它试图最小化所有终端节点处的平均平方误差之和。还值得一提的是，"`poisson`" 方法用于 Poisson 回归。最后但同样重要的是，"`exp`" 方法用于构建具有指数缩放的回归树，例如当`![y Subscript i](images/c13-i0410.png)<math display="inline" overflow="scroll"><msub><mi>y</mi><mi>i</mi></msub></math>` 的数据是生存分析中的数据时。这样的树通常被称为 *survival trees*，它们是著名的半参数 *Cox proportional hazards model* 的非参数替代方案。

### I. HSI 数据集：

让我们首先使用我们的 `fin-ratio.csv` 文件进行说明，该文件包含 2002 年的股票数据，未经过异常值检测，用于 HSI 分类。请参阅`[Programme 13.3](#c13.xhtml#c13-sec-3003)` 了解 Python 版本，参阅`[Programme 13.4](#c13.xhtml#c13-sec-3004)` 了解 `R` 版本。

`[Figure 13.8](#c13.xhtml#c13-fig-0008)` 中的分类非常简单。数据集根据变量 `ln_MV` 的值分为 `0` 和 `1` 两个类。分类规则和相应的质量度量如下所示：

1. R1：如果`![monospace ln bar MV less-than 9.478](images/c13-i0411.png)<math display="inline" overflow="scroll"><mtext mathvariant="monospace">ln\_MV</mtext><mo>&#60;</mo><mn>9.478</mn></math>`，则返回类别为 `0`（非 HSI）（644/3）。

2. R2：如果`![monospace ln bar MV greater-than-or-equal-to 9.478](images/c13-i0412.png)<math display="inline" overflow="scroll"><mtext mathvariant="monospace">ln\_MV</mtext><mo>&#8805;</mo><mn>9.478</mn></math>`，则返回类别为 `1`（HSI）（4/29）。

![FIGURE 13.8 Classification trees for the 2002 data without removing outliers.](images/c13f008.png)

[**FIGURE 13.8**](#c13.xhtml#R_c13-fig-0008) Classification trees for the 2002 data without removing outliers.

终端节点中的数字表示案例的数量。例如，在 `ln_MV9.478` 的组中，有 644 个“零”和 3 个“一”；而在 `ln_MV9.478` 的组中，有 4 个“零”和 29 个“一”。Programmes 13.3 和 13.4 的输出显示了每个节点的详细信息：

