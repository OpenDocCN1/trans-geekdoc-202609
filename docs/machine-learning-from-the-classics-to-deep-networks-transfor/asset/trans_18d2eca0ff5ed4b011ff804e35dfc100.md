
# LSTM 网络：信息流控制

LSTM 网络具有内置能力，可通过称为 `gates`（门）的非线性元件来 `control`（控制）信息流入和流出系统的 `memory`（记忆/存储单元）。这些门通过 logistic sigmoid 非线性函数和一个乘法器来实现。从算法角度来看，这些门等同于对相关信息流施加 `weighting`（加权）。权重位于 `[0,1]` 范围内，并取决于激活 sigmoid 非线性函数的相关变量的值。换句话说，信息的加权（控制）是在 `context`（上下文）中进行的。根据这种基本原理，网络具有敏捷性，能够遗忘已被使用且不再需要的信息。

基本 LSTM 单元/单位如 [图 18.36](#Chp018_885-995_B978044329238500024X.xhtml#f0195) 所示。它围绕两组变量构建，这两组变量堆叠在向量 `**s**` 中，称为细胞状态或单元状态，以及向量 `**h**` 中，称为隐藏变量向量。LSTM 网络建立在该基本单元的连续 `concatenation`（拼接/串联）之上。对应于时间 `n` 的单元，除了接收输入向量 **x**[n] 外，还从上一阶段接收 **s**[n − 1] 和 **h**[n − 1]，并将 **s**[n] 和 **h**[n] 传递给下一阶段。

![Figure 18.36 The LSTM unit. Note that in this case, there are two types of memory-related variables that are propagated, i.e., the cell state vector, s, and the hidden variables vector, h. The involved bias vectors are not shown to unclutter notation.](images/B978044329238500024X/gr036.jpg)

[图 18.36](#Chp018_885-995_B978044329238500024X.xhtml#cf1805) LSTM 单元。请注意，在这种情况下，有两类与记忆相关的变量被传播，即细胞状态向量 `***s***` 和隐藏变量向量 `***h***`。为使符号表示简洁明了，未显示涉及的偏置向量。

相关的更新方程总结如下，
