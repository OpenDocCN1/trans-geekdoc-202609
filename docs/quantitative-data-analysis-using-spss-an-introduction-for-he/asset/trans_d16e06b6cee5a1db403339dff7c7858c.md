
-   [年龄]、[会话次数]、[满意度评分]。

观察这三个变量后，显而易见的相关性选择是[会话次数]和[满意度评分]，因为我们可能假设患者接受的会话次数越多，他们对咨询的满意度越高。但正如[第1章](#06_Chapter01.xhtml)所建议的，情况可能并非如此——也许更多的会话对应更多未解决的问题，从而导致满意度降低？让我们来看看数据。

78 Page 78 ![Figure 5.1Scatterplot for height and shoe size](Images/fig5-1.jpg)

**Figure 5.1**Scatterplot for height and shoe size

### 5.2.1Producing a scatterplot in SPSS

第一步是绘制数据的散点图。

1.  1From the menu click on **Graphs**, then **Chart Builder**。

2.  2Select **Scatter/Dot** from the **Gallery** to show the range of graphs available and then drag the first ‘simple scatter’ graph into the preview area。

3.  3Drag **satisfaction** into the Y-axis box and **sessions** into the X-axis box – as illustrated on the next page:79 Page 79

4.  4Click **OK**。

![Screenshot 5.1](Images/ufig5-1.jpg)

Screenshot 5.1

这将产生如下散点图输出（见 [Figure 5.2](#10_Chapter05.xhtml#fig5-2)）：

![Figure 5.2Scatterplot of sessions and satisfaction ratings](Images/fig5-2.jpg)

**Figure 5.2**Scatterplot of sessions and satisfaction ratings

80 Page 80 

注意：在SPSS v15中，您可能需要使用Chart Editor来调整Y轴刻度，以便为较低值提供5%的下边距：双击Y轴，在属性框中将下边距（%）从0改为5。

从散点图中可以立即看出，从左到右呈上升趋势，这表明两个变量呈正相关：接受更多咨询会话的患者报告了更高的满意度。

### 5.2.2The strength of a correlation

虽然绘制散点图可以直观判断两个变量是否似乎相关，但这只是故事的一半。下一步是对这些数据应用统计检验，以确定相关性的强度以及它是否具有统计学显著性（即不太可能是偶然发生的）。

相关性的强度在-1到+1的区间内表示，如[表5.1](#10_Chapter05.xhtml#tab5-1)所示：

**Table 5.1**The strength of a correlation

| Negative correlation  || Positive correlation |

| --- | --- |

| −**1** −.9 −.8 −.7 −.6 −.5 −.4 −.3 −.2 −.1**0** || .1.2.3.4.5.6.7.8.9+1 |

| --- | --- |

| Strong negativeWeak positive || Weak positiveStrong positive |

| --- | --- |

A scale ranging between negative 1 and positive 1 values indicates the negative and positive correlation. Points between negative 1 and negative 0.5 indicate strong negative correlation, and negative 0.4 to negative 0.1 indicate weak negative correlation. 0.1 to 0.5 indicates weak positive correlation, and 0.6 to 1 indicates strong positive correlation.

A value approaching zero indicates the absence of any relationship between two variables, in other words no correlation.

You would only find a perfect positive correlation (+1) where there is a one-to-one incremental relationship between the two variables, for example, number of cinema tickets sold and customers in audience (assuming no one has sneaked in without buying a ticket of course). Obviously this level of correlation (perfect correlation) is unlikely in health and social research.

So, the next question is how do we obtain this value for the strength of a correlation from SPSS? Well, for our two variables with interval data – counselling sessions and satisfaction ratings, the appropriate measure of correlation is the Pearson product-moment correlation coefficient.^()

#### Running the Pearson correlation

1.  1From the menu at the top of the screen click: **Analyze / Correlate / Bivariate** ( *bi* meaning two and *variate* meaning variable).

2.  2Move **sessions** and **satisfaction** into the variables box.

3.  3Ensure that the **Pearson** box is ticked.

4.  4Click **OK**。

![Screenshot 5.2](Images/ufig5-2.jpg)

Screenshot 5.2

82 Page 82 

这将产生如下输出表格，显示会话次数（sessions）与满意度（satisfaction）之间的Pearson相关系数为0.53。因此，我们可以得出两个变量之间存在**强正相关**。该行标记为**Sig. (2-tailed)**的信息表明，相关性在0.003水平上具有统计学显著性，也就是说它不太可能是偶然发生的（统计显著性的概念在[第4章](#09_Chapter04.xhtml)中讨论过）。^()

**Table 5.2**Pearson correlations between sessions and satisfaction

| Correlations  |

| --- |

|  || sessions || satisfaction |

| --- | --- | --- |

| sessions || Pearson Correlation || 1 || .530 |

|  || Sig. (2-tailed) || . || .003 |

|  || N || 30 || 30 |

| satisfaction || Pearson Correlation || .530 || 1 |

|  || Sig. (2-tailed) || . || .003 |

|  || N || 30 || 30 |

表5.2标题为“Correlations”，列出了会话次数（sessions）和满意度（satisfaction）变量的Pearson相关、双侧显著性值以及样本量（N）。第1列列出了对应的变量；第2列和第3列分别列出了相关系数和显著性值。

[\*\*](#10_Chapter05.xhtml#ch05tfn1)⋅ Correlation is significant at the 0.01 level (2-tailed).

当你在报告中撰写此分析结果时，应将Pearson相关系数的值称为‘r’，如下所示：

我们可以因此得出结论，两个变量之间存在**强正相关**（r = .53, p = .003），更多的会话次数与更高的满意度评分相关联。

### 5.2.3The coefficient of determination

但这‘强相关’的0.53实际意味着什么？也就是说，我们能在多大程度上预测一个值来自另一个值？换句话说，患者满意度评分与会话次数之间的关系有多强？

有一个简单的计算可以回答这个问题。它被称为**决定系数**（coefficient of determination，记作r²），通过简单地对相关系数进行平方来衡量一个变量‘预测’另一个变量的程度。

例如，如果你进行了月薪与年薪之间的相关性分析，这应该得到一个完美的正相关，即r = 1.0。如果你将这个数值平方（1 × 1 = 1），再乘以100，就会得到100%的可预测性：如果你知道月薪，就能准确预测年薪。

回到我们的咨询数据，首先，我们对0.53进行平方，得到0.28，然后将其乘以100，得到28%。因此，我们所谓的‘强相关’实际上只解释了满意度评分方差的28%。我们应当得出结论：满意度评分**与**会话次数相关，但这仅解释了方差的28%；还有其他因素在起作用。请参见[方框5.2](#10_Chapter05.xhtml#box5-2)获取相关性和决定系数的实际应用示例。

