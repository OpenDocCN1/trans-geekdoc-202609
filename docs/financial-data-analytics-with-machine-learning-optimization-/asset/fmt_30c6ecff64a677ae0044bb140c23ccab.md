
### 3. 树分裂与停止条件

均方误差的减少（[13.21](#c13.xhtml#c13-disp-0057)）通过对当前节点进行额外分裂得到，将 ![script upper S](images/c13-i0464.png) 分裂为 ![script upper S Subscript minus Superscript left-parenthesis j right-parenthesis](images/c13-i0465.png) 和 ![script upper S Subscript plus Superscript left-parenthesis j right-parenthesis](images/c13-i0466.png)，使用任意特征变量 ![normal x Superscript left-parenthesis j right-parenthesis](images/c13-i0467.png)，只要仍小于预设阈值 ![epsilon](images/c13-i0468.png)，即：

![max Underscript j Endscripts left-parenthesis StartFraction 1 Over StartAbsoluteValue script upper S EndAbsoluteValue EndFraction left-parenthesis sigma-summation Underscript left-parenthesis bold-italic x Subscript i Baseline comma y Subscript i Baseline right-parenthesis element-of script upper S Endscripts left-parenthesis y Subscript i Baseline minus modifying above y with caret Subscript script upper S Baseline right-parenthesis squared minus left-parenthesis sigma-summation Underscript left-parenthesis bold-italic x Subscript i Baseline comma y Subscript i Baseline right-parenthesis element-of script upper S Subscript minus Superscript left-parenthesis j right-parenthesis Baseline Endscripts left-parenthesis y Subscript i Baseline minus y overbar Subscript script upper S Sub Subscript minus Sub Superscript left-parenthesis j right-parenthesis Subscript Baseline right-parenthesis squared plus sigma-summation Underscript left-parenthesis bold-italic x Subscript i Baseline comma y Subscript i Baseline right-parenthesis element-of script upper S Subscript plus Superscript left-parenthesis j right-parenthesis Baseline Endscripts left-parenthesis y Subscript i Baseline minus y overbar Subscript script upper S Sub Subscript plus Sub Superscript left-parenthesis j right-parenthesis Subscript Baseline right-parenthesis squared right-parenthesis right-parenthesis right-parenthesis less-than epsilon period](images/c13-math-0060.png)

回归树构建完成后，给定测试观测值的预测为该测试观测值所属区域 ![script upper D Subscript script l](images/c13-i0469.png) 中训练观测值的均值。

例如，[Figure 13.13](#c13.xhtml#c13-fig-0013) 展示了一个包含四个类别的数据集，仅含一个特征变量 ![normal x](images/c13-i0470.png) 和一个标签变量 ![normal y](images/c13-i0471.png)，均为实值。在根节点，根据 ![normal x less-than t 1](images/c13-i0472.png) 或 ![normal x greater-than-or-equal-to t 1](images/c13-i0473.png) 将数据集分为两组，然后计算两组的平均值 ![modifying above c with caret 1](images/c13-i0474.png) 和 ![modifying above c with caret 2](images/c13-i0475.png)。每个子组进一步根据分裂阈值 ![t 2](images/c13-i0476.png) 和 ![t 3](images/c13-i0477.png) 分为两个更小的组，最终每个簇对应其自身的标签。

回归树虽常用，但需注意其陷阱。具体而言，树构建过程是一种自顶向下、贪心的二元搜索，具有以下特点：

1. 每次分裂均基于前序节点的历史分裂做出最优选择；其仅在局部有效，但不一定是全局最优的。
