

然而，这种朴素方法面临与[第 7.1 节](#c07.xhtml#c07-sec-0002)和[第 7.2 节](#c07.xhtml#c07-sec-0003)中描述的方差率估计不准确问题相同的问题。根据那里的讨论，我们将首先从([7.18](#c07.xhtml#c07-disp-0032))和([7.19](#c07.xhtml#c07-disp-0033))中获取第 `n` 天的 `cov Subscript n plus 1` 和 `normal rho Subscript n plus 1` 的当前估计值，并选择合理的 `m`（既不太短也不太长）。然后，`cov Subscript n plus t` 和 `normal rho Subscript n plus t` 的估计值可以每天更新，对于 `t equals 0 comma 1 comma 2 comma ellipsis`，可以使用 EWMA 或 GARCH(`1 comma 1`) 模型，如下所示。对于 EWMA 模型，

[(7.20)](#c07.xhtml#R_c07-disp-0035) `cov Subscript n plus t Baseline equals lamda cov Subscript n plus t minus 1 Baseline plus left-parenthesis 1 minus lamda right-parenthesis normal x Subscript n plus t minus 1 Baseline normal y Subscript n plus t minus 1 Baseline and normal rho Subscript n plus t Baseline equals StartFraction cov Subscript n plus t Baseline Over normal sigma Subscript normal x comma n plus t Baseline normal sigma Subscript normal y comma n plus t Baseline EndFraction comma`

其中，`normal sigma Subscript normal x comma n Superscript 2` 和 `normal sigma Subscript normal y comma n Superscript 2` 根据 EWMA 模型使用([7.4](#c07.xhtml#c07-disp-0006))进行更新，整个过程中 `lamda` 的值相同。对于 GARCH(`1 comma 1`) 模型，

[(7.21)](#c07.xhtml#R_c07-disp-0036) `cov Subscript n plus t Baseline equals omega plus alpha normal x Subscript n plus t minus 1 Baseline normal y Subscript n plus t minus 1 Baseline plus beta cov Subscript n plus t minus 1 Baseline and normal rho Subscript n plus t Baseline equals StartFraction cov Subscript n plus t Baseline Over normal sigma Subscript normal x comma n plus t Baseline normal sigma Subscript normal y comma n plus t Baseline EndFraction comma`

其中，`normal sigma Subscript normal x comma n Superscript 2` 和 `normal sigma Subscript normal y comma n Superscript 2` 根据 GARCH(`1 comma 1`) 模型使用([7.13](#c07.xhtml#c07-disp-0018))进行更新，整个过程中 `omega`、`alpha` 和 `beta` 的参数值相同。

在 `p` 种证券的一般情况下，可以构建类似的 GARCH(`1 comma 1`) 模型。在金融中，对相应的动态相关性运动分析的标准化版本进行了考虑，文献中称为 *Dynamic Conditional Correlation GARCH* (DCC-GARCH) 模型 [[13]](#c07.xhtml#c07-bib-0012)。DCC-GARCH(`1 comma 1`) 的实现将推迟到 [子节 7.4.6.2](#c07.xhtml#c07-sec-0014)。

![](images/c07-gra-0033.png)![](images/c07-gra-0034.png)![](images/c07-gra-0035.png)

