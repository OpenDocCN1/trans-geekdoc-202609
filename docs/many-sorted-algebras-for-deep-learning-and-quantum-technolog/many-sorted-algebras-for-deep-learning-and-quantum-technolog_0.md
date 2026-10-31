# 深度学习和量子技术的多排序代数

# 献词

致我的一切，Betty

# 图表列表

| 图 1.1 || 域结构的多元图。 || 4 |
| --- | --- | --- |
| 图 1.2 || 向量空间描述为多类代数。 || 8 |
| 图 1.3 || 内积或希尔伯特空间。 || 13 |
| 图 1.4 || (A) R² 中的原始数据和 (B) R³ 中的特征映射数据。 || 15 |
| 图 2.1 || 用于 NN 方波脉冲创建的矩阵结构。`NN`，神经网络。 || 26 |
| 图 2.2 || NN 节点内操作的符号模式。`NN`，神经网络。 || 27 |
| 图 2.3 || NN 方波脉冲创建的符号计算。`NN`，神经网络。 || 28 |
| 图 2.4 || 使用非连续激活的 NN 进行分类。`NN`，神经网络。 || 31 |
| 图 2.5 || 使用 sigmoid 激活的 NN 进行分类。`NN`，神经网络。 || 32 |
| 图 2.6 || 单节点 NN 的偏置和权重修改。`NN`，神经网络。 || 33 |
| 图 2.7 || 仿射空间的多元图。 || 36 |
| 图 2.8 || 循环神经网络的类型。(A) RNN，(B) LSTM，(C) GRU。 || 39 |
| 图 3.1 || 单位代数的多元图。 || 42 |
| 图 3.2 || 并行卷积算法。 || 45 |
| 图 3.3 || Banach 空间的多元图。 || 50 |
| 图 3.4 || Banach 代数中算子名称的多元图。 || 51 |
| 图 3.5 || Banach* 或 C* 代数中算子的多元图。 || 53 |
| 图 4.1 || 复化的多元图。 || 59 |
| 图 4.2 || 用于说明对偶空间创建的多元图。 || 61 |
| 图 4.3 || 关联 ket 和 bra 希尔伯特空间的图。 || 65 |
| 图 4.4 || 双对偶的典范同构映射。 || 65 |
| 图 4.5 || 说明外积的多元图。 || 67 |
| 图 4.6 || 张量向量空间。 || 72 |
| 图 4.7 || 涉及张量的运算。 || 75 |
| 图 4.8 || 希尔伯特空间的张量积。 || 76 |
| 图 5.1 || 涉及矩阵运算的多元图。 || 83 |
| 图 5.2 || 多元图中相同操作数的说明。 || 86 |
| 图 5.3 || 布洛赫球。 || 87 |
| 图 6.1 || 束缚态和散射态隧穿效应。(A) 束缚态，(B) 散射态，(C) 归一化束缚态解，(D) 隧穿效应。 || 108 |
| 图 6.2 || 库珀对隧穿。基于 (Frolov, 2014)，(A) Frolov Barrie，(B) Cooper Pair Tunneling，(C) 电压-电流死区。 || 118 |
| 图 6.3 || (A) 并联电路，(B) 余弦型边界内的能级。 || 120 |
| 图 6.4 || 遵循 Zwiebach 的绝热过程，(A) 哈密顿量，(B) 能量分离，(C) 路径交叉哈密顿量，(D) 非交叉路径。 || 126 |
| 图 7.1 || H1 ⊗ H2 中的简单元素和纯态。 || 138 |
| 图 8.1 || Banach 代数中子群的多元图。 || 150 |
| 图 8.2 || 连续谱。 || 156 |
| 图 8.3 || 左理想和右理想。 || 157 |
| 图 8.4 || 涉及 C* 代数的同态图。 || 158 |
| 图 8.5 || A C* 代数与希尔伯特空间之间的 GNS 构造。`GNS`，Gelfand-Naimark-Segal。 || 160 |
| 图 10.1 || 一般和特定的代数商空间。(A) 商空间中的映射，(B) 商空间，平面中的直线。 || 172 |
| 图 10.2 || 实数商空间的同胚。 || 174 |
| 图 10.3 || 涉及圆周区间的同胚。 || 175 |
| 图 10.4 || 非第一可数空间。 || 176 |
| 图 10.5 || 具有两个坐标图和过渡映射的流形。 || 177 |
| 图 10.6 || 莫比乌斯棍人。 || 178 |
| 图 10.7 || 莫比乌斯带。 || 179 |
| 图 10.8 || 纤维丛中的截面。 || 181 |
| 图 10.9 || 线丛中的平凡化。 || 182 |
| 图 10.10 || 两种类型的格。(A) 正方形图案格，(B) 更一般的格。 || 183 |
| 图 10.11 || Hopf 纤维化 S⁰ → S¹ → S¹。(A) 原始圆；(B) 对圆施加的扭转；(C) 折叠操作。 || 187 |
| 图 11.1 || 李代数 MSA 图。 || 192 |
| 图 11.2 || 李群 MSA 图。 || 198 |
| 图 11.3 || 路径连通性。 || 200 |
| 图 11.4 || 李群与李代数之间的映射。 || 208 |
| 图 12.1 || 同伦方块。 || 218 |
| 图 12.2 || 仅在原点相切的环的同伦示例。 || 218 |
| 图 12.3 || 环的等价类。 || 219 |
| 图 12.4 || 起始点等价。 || 220 |
| 图 12.5 || 基本群的多元图。 || 221 |
| 图 12.6 || 等价类是良定义的。 || 222 |
| 图 12.7 || 结合律的证明。 || 222 |
| 图 12.8 || 单位元条件。 || 223 |
| 图 12.9 || 逆函数方程恒等式。 || 224 |
| 图 12.10 || 数字八。 || 226 |
| 图 12.11 || 通用覆盖群。 || 228 |
| 图 13.1 || l¹ 中算子 L 的谱及其在 l^∞ 中的对偶。 || 236 |
| 图 14.1 || 典范超群多元图。 || 257 |
| 图 14.2 || 部分等距映射。 || 259 |
| 图 14.3 || 部分等距 [U, U*] 非零的多元图。 || 261 |
| 图 14.4 || 辛向量空间的多元图。 || 267 |
| 图 15.1 || Fock 空间的梯子算子。(A) 玻色 Fock 空间，(B) 费米 Fock 空间中允许的操作。 || 274 |
| 图 15.2 || 由 Maya 图得到的 Young 图（参见例 15.9）。 || 279 |
| 图 15.3 || 用于求 Maya 图的 Young 图。 || 282 |
| 图 16.1 || 希尔伯特群。 || 292 |
| 图 16.2 || CNOT 门。 || 297 |
| 图 16.3 || SWAP 门。 || 299 |



| 图 16.4 || 振幅放大的轨迹。(A) 均匀叠加，(B) 态`|x*>`的反射，(C) 振幅放大，(D) 再次应用一个半反射对，(E) 应用了两个反射对/。 || 304 |
| 图 16.5 || 反射操作：(A) 两个向量和反射 ket，(B) 反射操作的结果。 || 305 |
| 图 17.1 || Deutsch oracle。 || 307 |
| 图 17.2 || 表示 Deutsch oracle 的量子电路。 || 309 |
| 图 17.3 || Deutsch 算法。 || 309 |
| 图 17.4 || Deutsch-Jozsa 算法。 || 311 |
| 图 17.5 || Grover 反射操作。(A) 起始位置，(B) Oracle 的应用，(C) 应用反射，(D) 再次应用 Oracle，(E) 再次应用反射，(F) 应用 Oracle，(G) 应用反射。 || 314 |
| 图 17.6 || 椭圆曲线的类型。 || 322 |
| 图 18.1 || 通过仿射流形 shattering 一个、两个和三个点：(A) shattering 单个点；(B) shattering 两个点；(C) shattering 三个点。 || 331 |
| 图 18.2 || 通过矩形 shattering 四个点。 || 332 |
| 图 18.3 || K-最近邻分类。 || 334 |
| 图 18.4 || 卷积神经网络。 || 347 |
| 图 19.1 || 谐振子的前五个波函数。 || 350 |
| 图 B.1 || (A) 可测空间和 (B) 测度空间。 || 369 |
| 图 C.1 || 椭圆曲线加法。 || 373 |
| 图 C.2 || 椭圆曲线上垂直点的加法。 || 374 |
| 图 C.3 || 结合律的证明。 || 375 |
| 图 D.1 || Young 图。 || 378 |
| 图 E.1 || 置换群的 Young 图。 || 380 |

# 前言

Charles R. Giardina

多类代数（`MSA`）为描述和统一科学、工程和数学多个分支中的各种代数结构提供了一个严谨的平台。然而，使用该平台最自然的应用是在量子技术的所有领域。其中包括量子物理、量子力学、量子信息理论等最新领域，量子计算、量子神经网络和量子深度学习。事实上，在所有量子学科中，都存在大量的代数基础和技术。其中几种技术可直接应用于机器学习，并在本文中介绍。特别是，随着当前对量子卷积神经网络的兴趣，理解基础量子变得更加重要。尽管分析、拓扑、概率以及几何概念在这些学科中的许多方面都被采用，但代数展现了主要线索。该线索使用 `MSA` 暴露出来。

在所有量子领域中，复数域上的希尔伯特空间的基本设定都是必不可少的，而机器学习主要处理实数域。全局层面和局部层面的精确规范都描述在 `MSA` 中。事实上，由于不同的载体集合，局部层面的表征可能看起来非常不同，但在全局层面它们可能相同。`Banach*` 代数以及希尔伯特空间是这些系统的基础。从局部观点看，这些代数可能大不相同。例如，神经网络中 Banach 代数类型的双线性乘法运算可能涉及仿射映射，也可能是卷积。然而，在量子系统中，双线性运算通常采用其他形式。这些包括逐点乘法、函数复合、Lie 或 Poisson 括号，甚至同伦中路径等价类的串联。

在本文中提供了理论和实践结果。充当状态的希尔伯特空间射线以及量子位的深入描述得到了解释和说明。量子位在量子计算和量子机器学习中处于中心地位。形成群的酉算子用于状态转换，并在 `MSA` 中被描述为希尔伯特群和 Lie 群。酉算子中的参数允许在量子计算应用中进行优化。同时，`MSA` 中描述的 `C*` 代数包含可观测量结构。在所有情况下，`MSAs` 在说明这些与量子和机器学习学科中的各种其他代数结构之间的相互作用方面最有用。

# 致谢

我感谢 Ed Cooke 阅读了初步章节，并感谢审阅者提出的建设性改进。还要感谢 Elsevier 编辑部在整个过程中提供的帮助和指导。最后，我非常感激能够认识并向三位伟大的数学家/工程师以及曾经的贝尔电话实验室同事学习：David Jagerman、Charles Suffel 和 Frank Boesch。

# 第 1 章

## 量子多排序代数的介绍

### 摘要

本章首先提及了在文本后面各节中描述的几种代数结构，这些结构将被嵌入到多类代数的一个版本中。随后是对多类代数方法学的描述以及说明。利用多项图给出了涉及 `MSA` 的全局视图。这些有向图由具有多尾有向箭头的节点组成。一般的域结构在第 1.4 节中以 `MSA` 的形式描述。随后是量子和机器学习中的进一步代数结构。具体的量子和机器学习域连同支撑所有量子方法学的一般希尔伯特空间条件一起呈现。时间受限信号在内积空间条件下得到发展。这些信号是卷积神经网络的基本构造。核方法在量子和机器学习学科中都很有用，已在此介绍。在后面的章节中，核方法被证明是支持向量机的基本成分。本章以 `R` 模的描述和应用结束。这些结构具有与向量空间结构几乎相同的 `MSA` 描述。

#### 关键词

多类代数；多项图；神经网络；有界向量；核；`R`-Modules；有限域；向量空间；希尔伯特空间

## 1.1 量子多排序代数的介绍

本章首先提及了在文本后面各节中描述的几种代数结构，这些结构将被嵌入到多类代数的一个版本中。随后是对多类代数方法学的描述以及说明。利用由具有多尾有向箭头的节点组成的多项图给出了涉及 `MSA` 的全局视图。一般的域结构在 第 1.1.4 节 中以 `MSA` 的形式描述。随后是量子和机器学习中的进一步代数结构。具体的量子和机器学习域连同支撑所有量子方法学的一般希尔伯特空间条件一起呈现。时间受限信号在内积空间条件下得到发展。这些信号是卷积神经网络的基本构造。核方法在量子和机器学习学科中都很有用，已在此介绍。在后面的章节中，核方法被证明是支持向量机的基本成分。本章以 `R` 模的描述和应用结束。这些结构具有与向量空间结构几乎相同的 `MSA` 描述。

### 1.1.1 代数结构




在整个量子领域中，使用了极其广泛的代数结构，从最基本的正则对易关系（`CCR`）到求解椭圆曲线密码学的方法以及构建量子卷积神经网络的方法。本文的目的是提供嵌入这些代数结构中的底层原理的统一。实现这一统一的机制是多排序代数（`MSA`）（Goguen 和 Thetcler, 1973）。`MSA` 可被视为通用代数的扩展，如 Gratzer (1969) 所示。在这里，代数结构的各种类型以最一般化的方式描述，并通过态射显示对象之间的对应关系。量子学科中多排序或多种类型的代数概念的底层特征在 `MSA` 中通过严格规范以及复数图同时得到捕捉。本文受 Birkhoff 和 Lipson (1970) 及其异构代数的启发，以及 (Goguen 和 Meseguer, 1986) 对 `MSA` 的评述。

采用 `MSA` 呈现了全局层面和局部层面的精确规范。`MSA` 对于更好地理解量子及其与机器学习和量子神经网络技术的关系至关重要。从基本公理开始的希尔伯特空间概念以精确但高层次的方式详细说明（Halmos, 1958），而量子和机器学习的底层域则非常具体。在量子中，该域几乎总是复数；有时使用实数甚至四元数。然而，在机器学习中，主要使用的是实数域。这在支持向量机应用中尤其如此。

一般而言，量子希尔伯特空间可能是有限维的，可能由 ket 和 bra 组成，并且可能是相似希尔伯特空间的张量积，或如 `L²` 或 `l²` 那样的无限维（Halmos, 1957）。所有这些结构都将在局部层面得到精确探讨。这在指定将 `C*` 代数与希尔伯特空间联系起来的 Gelfand-Naimark-Segal（`GNS`）构造时再次显而易见（Gelfand 和 Naimark, 1943；Segal, 1947）。从实际观点来看，用于量子计算机的量子比特的希尔伯特空间被描述（Feynman, 1986）。其他应用包括量子神经网络和量子机器学习中的量子比特。

### 1.1.2 多排序代数方法论

为了开始描述 `MSA` 方法论，必须指定对象的排序集合。例如，术语 `scalar` 可能是该集合的一个元素。尽管术语 `scalar` 是通用的，它可能指的是来自实数或复数等域的元素。然而，它也可能代表四元数，即来自斜域或非交换域的元素。重要的是，对于每个排序，都有载体集合。正是这些集合唯一标识了所讨论元素的精确类型。例如，实域、复域、有理域或密码学中使用的有限域使用非常不同的载体集合。

一旦声明了排序，还必须给出操作符号。它们作为特定签名集合中的元素进行组织。这些集合用于识别符号之间的共同属性，如其 `arity`。操作符号表示诸如对称化、湮灭、产生等跨排序和内排序映射，以及基本运算：加法、乘法、求逆等等。

这些映射中实际使用的算子涉及与排序相对应的指定载体集合。这是在更低的视角下进行的。每个算子在定义域中使用来自指定载体集合的元素作为操作数。其值域也是如此。签名集合中的算子名称连同它们必须遵守的代数定律、规则、等式恒等式或关系一起列举。定律或等式恒等式包括对易规则、结合律、分配律、幂零规则，以及严格规范所必需的各种其他附加条件或关系。

使用由具有多尾有向箭头的节点组成的复数图，给出了涉及 `MSA` 的有用全局视图（Goguen 和 Meseguer, 1986）。箭头的全部实体都被标记。每个节点由一个圈注特定排序的圆圈表示。箭头附有算子名称，并如其签名集合中所声明的那样。箭头中尾部的数量对应于所讨论算子的 `arity`。`arity` 为零的算子没有尾部，并使用该排序的特殊元素的名称进行标记。这些包括 `zero`、`one` 和 `identity element`，以及 `top` 或 `bottom`。箭头的尾部从适当的签名集合中指定的定义域排序发出。箭头的单个头部指向算子的值域排序。简而言之，复数图提供了描述代数结构所需闭包运算的视觉描述。

`MSA` 中包含偏算子。这与在偏通用代数中所做的工作类似。然而，对于未在整个所表示的定义域排序上定义的运算，采用了特殊符号。其中大部分符号将在后面给出。包含依赖于定义域的算子在量子中至关重要，因为即使位置和动量算子也是无界的。无限维希尔伯特空间需要显式的定义域声明以及闭包条件。现在将给出一个算子未完全定义的更基本实例。在这里，域中的乘法逆元对除 `zero` 之外的所有值都有定义，因此它是一个偏算子。然而，该算子存在于 `MSA` 中。此外，在这种情况下，复数图描述中使用了带单个尾部的虚线箭头。

### 1.1.3 全局域结构

对应于域结构，只需要单一排序 `SCALAR`。存在多个签名集合。它们按 `arity` 组织。`Arity` 指的是给定签名集合中算子的操作数或参数的数量。`Arity` 也指复数箭头的尾部数量。对于二元算子，除非另有说明，否则它们应以任意顺序使用两个参数。对哪个参数先出现没有限制。

$\\begin{array}{l} \\left. {Binary}{operation}:{\\left\\{ {{ADD},{MULT}} \\right\\}}{each}{maps}{SCALAR} \\times {SCALAR}\\rightarrow{SCALAR} \\right. \\\\ \\left. {Unary}{operation}:{\\left\\{ {{MINUS},{INV}} \\right\\}}{each}{maps}{SCALAR}\\rightarrow{SCALAR} \\right. \\\\ {{Zero} - {ary}{operation}:{\\left\\{ {{ZERO},{ONE}} \\right\\}}{these}{are}{special}{elements}{of}{the}{sort}{SCALAR}.} \\\\ \\end{array}$

![方程](img/F000199si1.png)



# 域结构与代数恒等式

## 代数域的高层解释

请注意，即使 `INV` 是一个偏函数名，它也包含在与 `MINUS` 相同的签名集中；两者都是单目运算符名。图 1.1 提供了一个代数域高层解释的说明。该图表示封闭运算。例如，`ADD` 表示将两个来自 `SCALAR` 的值组合得到另一个 `SCALAR` 值，而 `MINUS` 则取一个 `SCALAR` 值并产生另一个这样的值。从 `ZERO` 指向 `SCALAR` 的箭头表示域中必须存在一个名为 `ZERO` 的元素。`ONE` 也是如此。如同在通用代数中，特定元数的运算名称数通常由一个非负整数的有限序列列出。对于一般的域结构，元数序列如下：`(2, 2, 2)`。确实，第一项指定零元运算的数量；这里为 2，而下一项为一元运算的数量=2，最后一项为二元运算的数量=2。这种列出程序类似于在 Fock 空间中记录费米子或玻色子占据数的方法。该空间将在后面的章节中描述。

![图 1.1 域结构的拟多项式图。](img/F000199f01-01-9780443136979.jpg)

图 1.1 域结构的拟多项式图。

## 域的等式恒等式

域的等式恒等式或定律如下所示。这里，为了方便，我们用代表性符号表示 sort，并用建议性符号表示所有运算名称。

* `SCALAR` 用 `a`、`b` 或 `c` 表示。
* `ADD` 用 `+` 表示
* `MULT` 用 `·` 表示
* `MINUS` 用 `-` 表示
* `INV` 用 `/` 表示
* `ZERO` 用 `0` 表示
* `ONE` 用 `1` 表示

域的等式恒等式、定律或约束方程如下：

1. 1) 加法结合律：`(a+(b+c))=((a+b)+c)`
2. 2) 零律：`0+a=a+0=a`
3. 3) 负律：对于任意 `a`，存在 `−a`，其中 `a−a=−a+a=0`
4. 4) 所有元素加法的交换律：`a+b=b+a`
5. 5) 乘法结合律：`(a·(b·c))=((a·b)·c)`
6. 6) 分配律：`a·(b+c)=a·b + a·c`；`(a+b)·c=a·c + b·c`
7. 7) 单位律：`1·a=a·1=a`
8. 8) 偏逆律，排除 0：对于任意 `a`，存在 `1/a`，其中：`a·1/a=(1/a)·a=1`
9. 9) 乘法交换律：`a·b=b·a`。

将给出抽象域 `F[3]` 的一个例子来说明封闭运算，这正是 图 1.1 的精髓。之前列出的九个等式约束也得到了说明。该例子对于准备开发椭圆曲线密码学以及后面章节中描述的 Shor 量子算法非常重要。

### 例 1.1

设 `SCALAR` 的载体集合为集合 `X={0, 1, 2}`。与签名集中命名的运算相对应的运算定义为模三。下表提供了二元 `ADD`、`MULT` 以及一元运算 `MINUS`，以及偏一元运算 `INV`；按以下顺序列出：

$\\begin{matrix} \\begin{matrix} + & 0 & 1 & 2 \\\\ 0 & 0 & 1 & 2 \\\\ 1 & 1 & 2 & 0 \\\\ 2 & 2 & 0 & 1 \\\\ \\end{matrix} & \\begin{matrix} \\cdot & 0 & 1 & 2 \\\\ 0 & 0 & 0 & 0 \\\\ 1 & 0 & 1 & 2 \\\\ 2 & 0 & 2 & 1 \\\\ \\end{matrix} & \\begin{matrix} x & {- x} \\\\ 0 & 0 \\\\ 1 & 2 \\\\ 2 & 1 \\\\ \\end{matrix} & \\begin{matrix} x & {1/x} \\\\ 1 & 1 \\\\ 2 & {2.} \\\\ \\end{matrix} \\\\ \\end{matrix}$

![方程](img/F000199si2.png)

要使用前两张表来找到要执行二元运算的左侧和上方的元素，结果分别位于右侧的行和下方的列中。对于右边两张表，使用第一列；然后一元运算可以读到所需元素的右边。

所有等式恒等式都成立。为了证明 (1)，必须使用 `a`、`b` 和 `c` 的所有可能值。这里有 27 种组合，但接下来只举一个例子。

1. 1) 加法结合律：`(2+(1+2))=(2+0)=2`；另外 `((2+1)+2)=0+2=2`
2. 2) 零律：从 `+` 表中，`0` 在左侧或上方与 `x` 相加时得到 `x`
3. 3) 负律：从 `—` 表中，例如，`1+2=2+1=0`，`−2=1`
4. 4) 加法交换律：`+` 表关于主对角线对称
5. 5) 乘法结合律：`(2·(1·2))=(2·2)=1`；另外 `((2·1)·2)=1`

在前四个恒等式成立的情况下，这表明加法结构是一个阿贝尔群。此外，它是具有三个元素的循环群的一个实例。加法循环 `2+1=0`。与结合律一样，分配律实际上需要全部 27 种排列才能完全验证。然而，如前所述，这里只举一个例子。

6. 6) 分配律：`(2 · (1 + 2))=(2 · 0)=0`；另外 `(2 · 1) + (2 · 2)=2 + 1=0`
7. 7) 单位律：从 `·` 表中，顶部或左侧的 `1` 与 `x` 相乘得到 `x`
8. 8) 偏逆律，排除 `0`，从最后一张表 `1/1=1`，且 `1/2=2`
9. 9) 乘法交换律：表 `·` 关于主对角线对称。

由于所有等式恒等式以及封闭运算都成立，这表明结构 `F[3]` 是一个域。该域称为有限域或伽罗瓦域。

### 1.1.4 量子和机器学习中的全局代数结构

为了节省空间并利用前面提到的一般域结构，我们提及域的重要子结构。该列表试图从最一般的结构、群胚，到最受限制的结构、域。所有结构都以 `SCALAR` 作为其 sort，并涉及为域提供的签名集中的运算名称。此外，以下大多数代数结构需要一些等式恒等式，`(1)` 到 `(9)`。这些已在前面列出，提供了代数域的全局描述。最后，这些结构的拟多项式图与域的相同，但可能删除了一些箭头。许多即将出现的结构经常出现在量子学科中，并将在后续章节中应用。下面的具体内容应作为这些结构全局定义的参考。

群胚是一个结构，仅有一个签名集，由 `ADD` 组成且无约束。满足约束 `(1)` 的群胚是半群。当同时存在 `ZERO` 以及约束 `(2)` 时，半群称为幺半群。如果此外存在 `MINUS` 且 `(3)` 成立，则幺半群是一个群。当 `(4)` 成立时，群称为阿贝尔群。当 `MULT` 也存在且 `(5)` 和 `(6)` 成立时，阿贝尔群称为环。如果 `ONE` 也存在且 `(7)` 成立，则环称为具有单位元的环。满足 `(9)` 的环称为交换环。当 `ONE` 存在且 `(7)` 和 `(9)` 成立时，环是具有单位元或幺元的交换环。具有幺元的交换环在不存在零因子时称为整环。零因子出现在两个非零元素的乘积等于 `ZERO` 时。当具有单位元的环也具有满足 `(8)` 的 `INV` 时，会出现斜域；该结构也称为除环。当 `(9)` 也成立时，斜域称为域。

这些结构中的许多说明在后续章节中描述，例如李群和李代数；四元数也提供了除环的一个实例。下面是一个重要的幺交换环但不是域的例子。这是一个容易理解的结构，但该载体集合对于在 R-模中使用至关重要。在后续章节中将看到，域之于向量空间，正如环之于 R-模。

### 例 1.2



考虑所有整数的载体集合 `Z`。如果采用通常的加法、取负和 `ZERO`，则该结构成为一个阿贝尔群。如果引入通常的乘法和 `ONE`，以及上面为域指定的所有等式恒等式，除了 (`#8`)，则该结构是一个幺半交换环。此外，图 1.1 中的多元图，经修改以适应环结构，可能去掉点线部分运算 `INV` 箭头。然而可能不去掉，因为在整数中，数字一和负一确实有逆元。

之前提到的所有群和群类结构都是加性群或群类。在量子和机器学习中，许多这些对应的结构是类似的代数。例如，它们通常是乘性群或乘性群类。

任何和每个域都可以用前面指定的方式描述。这就是高层次或大局观。再次，类型 `SCALAR` 和这些签名集合对有理域、实域、复域或任何伽罗瓦域或有限域都成立，如最后一节所示。现在将确定另外两个具体的域。

### 1.1.5 特定机器学习域结构

为了获得机器学习底层实域 (`R`)，与类型 `SCALAR` 相关的载体集合是实数。它提供了实际的底层、深入的视图。此外，对于签名集合中的每个运算符名称，都定义了一个相同元数的实际运算符或函数。所有等式约束和定律使用这些元素都成立。特别是，在这种情况下 `ZERO` 为 `0`，对于任意实数 `r`，`r+0=0+r=r`。另外 `ONE` 是数字 `1`，且 `1 · r=r · 1=r`。最后，任何实数 `r` 除 `0` 外的逆 `s` 可以找到，`s=1/r`。

### 1.1.6 特定量子域结构

为了获得大多数量子情况下希尔伯特空间底层的复域 (`C`)，类型 `SCALAR` 指的是复数。除了签名集合中的每个运算符名称外，还必须定义一个相同元数的实际运算符或函数。这里的载体集合是复数系统。它提供了实际的底层、深入的视图。`SCALAR` 的实际载体集合为 `{x+i·y also written as x+iy or x+yi, such that x and y are now real numbers and i is a nonreal number; it is a symbol having the property that i²\=−1}`。此外，加号只是一个字符，将两个实体连接在一起。图 1.1 中提供的闭包运算必须严格指定。例如，对于两个复数，`v=a + i·b` 和 `w=c + i·d`，`ADD (v, w)=(a + c) + i·(b + d)`。加法公式中有两个不同的加号。为了使事情更糟，我们将写 `ADD (v, w)=v + w=(a + c) + i·(b + d)`。现在，加号有三种用法。然而，为了不让记号变得疯狂，我们将继续这种做法。有时使用不同的记号如 `+[1]`、`+[2]` 和 `+[3]` 使事情更清晰。事实上，在后面的章节中，线性映射的希尔伯特空间采用全部三个加号。最后一个记号滥用是对于零元运算符 `ZERO` 使用 `0 + i·0=0`。现在对复域做一个更简短的解释。

所有等式约束和定律使用这些元素都成立。特别是，对于 `z=(x + i y)`，仅提及以下两个定律：
*   `# 3)` 负号定律：`MINUS (x+i y)=(−x−i y)`。
*   `# 8)` 非 `(0+0 i)` 的部分逆：`INV (x+i y)=x/(x²+y²)−i y/(x²+y²)`。

令 `z=x+iy`，则 `z` 的实部用 `Re(z)` 表示，为 `x`。同样，`z` 的虚部为 `Im(z)`，为 `y`。请注意它们都是实值。一个在复域中非常重要运算是共轭。它是一个运算，不能用签名集合中提及的其他运算导出。共轭的运算符符号为 `CON`。应用于复数时，它否定虚部。实际运算是 `*`，因此记号滥用如下：`CON(z)=CON (x + i y) =(x−i y)`。更精确地说，`z*=(x+i y)*=(x−i y)`。此外，共轭运算是一个对合；因此共轭的两次应用得到原始值。两次应用相当于恒等运算。因此可得 `(z*)*=((x+i y)*)*=(x+i y)=z`。复数 `z` 的绝对值是该数与其共轭的乘积的平方根。等价地，`|z|²\=z*z=z z*`。另请注意，`z` 的实部为 `Re(z)=(z+z*)/2`，而 `z` 的虚部为 `Im(z)=(z−z*)/2i`。这两个量都是实值。上述所有性质在涉及内积的后续示例以及描述伴随运算时都是必需的。最后，任意复值 `z=x+iy` 的极坐标形式可写为 `z=r e^(iθ)`，其中 `r=(x²+y²)^(1/2)` 且 `θ=arctan (y/x)`。如前所述，平方根应始终解释为产生非负结果。

### 1.1.7 向量空间作为多排序代数

向量空间由两种不同的对象类型组成。这些是 `SCALAR`，如域结构中，以及第二种类型 `VECTOR`。请参阅 图 1.2；在此图中，两种类型都已说明。然而，仅涉及类型 `SCALAR` 的运算符名称未显示。也就是说，来自 图 1.1 的多排序多元图箭头未重复。对应于向量空间结构，签名集合不仅按运算的元数组织，还按其类型组织。这是因为相同元数的几个运算具有混合类型的输入或输出。例如，可以在图中后面看到，元数为二的运算名称，即 `V-ADD` 和 `S-MULT`，将有两个不同的签名集合。具体来说，`V-ADD` 取两个 `VECTOR` 并返回一个 `VECTOR`，而 `S-MULT` 取一个 `SCALAR` 和一个 `VECTOR` 并返回一个 `VECTOR`。

![图 1.2 多排序代数描述的向量空间.](img/F000199f01-02-9780443136979.jpg)

图 1.2 向量空间作为多排序代数的描述。

这导致向量空间的元数序列为：`(1, 1, 2 (1, 1))`。对于 `MSA`，元数列表与通用代数相同。它按顺序标识 (零元、一元、二元、三元、… N 元) 运算名称的数量。然而，`MSA` 中相同元数的不同签名集合有特殊规则。元数序列中该元数的总数量后面跟着该元数的每个不同签名集合的数量。因此，序列中 2 之后的两个 1 显示存在两个不同的二元运算，所有运算具有不同的定义域或值域。向量空间的实际签名集合从较高元数开始按递减顺序如下：

$\\begin{array}{l} \\left. {Binary}{operation}{\\left\\{ {V - {ADD}} \\right\\}}, V - {ADD}{maps}{VECTOR} x{VECTOR}\\rightarrow{VECTOR} \\right. \\\\ \\left. \\quad\\quad\\quad\\quad\\quad\\quad\\quad\\left\\{ {S - {MULT}} \\right\\}, S - {MULT}{maps}{SCALAR} x{VECTOR}\\rightarrow{VECTOR} \\right. \\\\ \\left. {Unary}{operation}{\\left\\{ {V - {MINUS}} \\right\\}}, V - {MINUS}{maps}{VECTOR}\\rightarrow{VECTOR} \\right. \\\\ {{Zero} - {ary}{operation}{\\left\\{ {V - {ZERO}} \\right\\}}, V - {ZERO} - {is} a{special}{element}{of}{the}{sort}{VECTOR}.} \\\\ \\end{array}$

![方程](img/F000199si3.png)

如前所述，二元运算符以任一顺序使用其操作数。例如，对于标量 `a` 和向量 `v`，`S-MULT (a; v)=a·v=v·a`。



请注意，前面提到的只有三个签名集合具有仅使用类型 `VECTOR` 的操作名称。也就是说，这三个名称将运算符与类型 `VECTOR` 的定义域和值域关联起来。它们的元数为 0、1 和 2。仅这些集合内的相应运算符描述了向量空间内的加性阿贝尔向量群。这里必须同时满足提到的等式约束 `(1)−(4)`。该加性群的元数序列为 `(1, 1, 1)`。

向量空间的等式恒等式或定律如下给出。接下来，在下一节中，给出了内积或希尔伯特空间所需的额外等式恒等式。为方便起见，我们再次用代表性符号表示类型，并用暗示性符号表示所有操作名称。

* 用 `a`、`b` 或 `c` 表示 `SCALAR`。
* 用 `u`、`v` 或 `w` 表示 `VECTOR`
* 用 `1` 表示 `ONE`
* 用 `+` 表示 `V-ADD`
* 用 `−` 表示 `V-MINUS`
* 用 `0` 表示 `V-ZERO`
* 用 `·` 表示 `S-MULT`

1. `Associative for vector addition`: `(u+(v+w))=((u+v)+w)`
2. `Zero vector law`: `0+v=v+0=v`
3. `Minus vector law`: `v + (−v)=−v+v=0`
4. `Commutative vector law for addition`: `u+v=v+u`
5. `One law`: `1·v=v·1=v`
6. `Distributive law`: `a · (u + v)=a · u + a · v`
7. `Distributive law`: `(a + b)·u=a·u + b·u`
8. `Associative law`: `(a · b)·v=a·(b·v)`

这八条定律一般性地描述了任何向量空间。

接下来给出一个不构成向量空间的结构的有趣例子。

### 示例 1.3

设 `SCALAR` 的载体集合为所有实数 `R`，具有通常的实数域结构。然而，设 `VECTOR` 的载体集合为正实数 `V=R+={x, such that 0<x<∞}`，具有通常的乘法和除法。在此应用中，用向量的乘法代替向量加法。也就是说，采用正实数的乘法。由于两个正实数的乘积是正实数，此二元运算是封闭的。此情况下的乘法运算是有效的。对于一元减法运算，取倒数运算来替代。同样，此运算也是封闭的，因为对于表示向量的任意正实数，其倒数也是正实数。用数字一代替零向量在此结构中使用。所以 `V-ZERO` 是数字一。

最后，必须描述涉及向量的标量乘法。同样重要的标准是此运算是封闭的；也就是说，它必须满足向量空间中多值图在 图 1.2 中的封闭运算。此情况下的实际运算分两步执行。首先，形成标量实数值与正实数值向量的乘积。然后接下来，将此乘积用作 `e` 的幂的指数。应用此两步运算后，结果始终为正实数。因此，运算是封闭的，并且再次得到一个向量。前面描述的运算再次以更正式的方式给出。

首先：
* 用 `a`、`b` 和 `c` 表示 `SCALARS`；这些都是实数。
* 用 `u`、`v` 和 `w` 表示 `VECTORS`；这些都是正实数。

用实际的载体集合运算替换操作名称：
* 用 `v · w` 替换 `V-ADD (v,w)`
* 用 `1/v` 替换 `V-MINUS (v)`
* 用 `1` 替换 `V-ZERO`
* `S-MULT (a; v)=e^((aν))`，因此 `a` 和 `v` 相乘并成为 `e` 的指数。

识别出其签名集合仅包含类型 `VECTOR` 的操作名称会得到一个阿贝尔群结构。请注意，使用指定的载体集合时，所有等式恒等式都成立，其中名称 `ADD` 指代乘法：

1. `Associative for vector addition`: `(u·(v·w))=((u·v)·w)`
2. `Zero vector law`: `1·v=v·1=v`
3. `Minus vector law`: `v·1/v=(1/v)·v=1`
4. `Commutative vector law for addition`: `u·v=v·u`

因此，验证了阿贝尔群结构。然而，该结构并不满足定义向量空间的所有等式恒等式。事实上，它并不满足以下所有附加条件。因此，`e` 的实数幂始终为正实数，并且本身是该空间中的向量，并且存在封闭性。然而，对于向量空间结构，所有 `(5)−(8)` 等式恒等式也必须成立。

5. `One law`: `e^((1ν))=e^((ν1))=e^((ν))`，此式成立。
6. `Distributive law`: `e^((a(uν)))`，不等于 `e^((au))e^((aν))=e^(a(u+ν))` 且一般不成立。
7. `Distributive law`: `e^(((a+b)u))=e^((au))e^((bu))=e^((au+bu))`，此式成立。
8. `Associative law`: `e^((ab(ν)))`，不等于 `exp(a e^((bν)))` 且一般不成立。

下一个例子使用与前一个例子完全相同的载体集合，但仅在标量乘法的定义上做出改变。

### 示例 1.4

与上一个例子中的条件相同，但这次唯一的变化是重新定义标量乘法。因此 `SCALAR` 的载体集合再次为 `R`。`VECTOR` 的载体集合再次为 `R+`，即所有正实数。

* 用 `a`、`b` 和 `c` 表示 `SCALAR`，均为实数。
* 用 `u`、`v` 和 `w` 表示 `VECTOR`，均为正实数。
* 用实际的载体集合运算符替换操作名称：
* 用 `v·w` 替换 `V-ADD (v,w)`
* 用 `1/v` 替换 `V-MINUS (v)`
* 用 `1` 替换 `V-ZERO`
* `S-Mult (a; v)=v^(a)`。

上一个例子中改变的正是最后这一运算。在本例中，向量被提升为标量幂。由于正实数提升到任意实数幂后仍为正数，这验证了封闭条件。因此，向量空间图，即 图 1.2，是有效的，但仍需满足所有等式恒等式才能将此结构归类为向量空间。

因此为验证这是一个向量空间，注意以下所有式子都成立：

1. `Associative for vector addition`: `(u·(v·w))=((u·v)·w)`
2. `Zero vector law`: `1·v=v·1=v`
3. `Minus vector law`: `v·1/v=(1/v)·v=1`
4. `Commutative vector law for addition`: `u·v=v·u`
5. `One law`: `v¹=v`
6. `Distributive law`: `(vw)^(a)=v^(a) w^(a)`
7. `Distributive law`: `v^((a+b))=v^(a) v^(b)`
8. `Associative law`: `v^((ab))=(v^(a))^(b)`

就向量空间而言，迄今为止已为类型 `SCALAR` 定义了两个不同的载体集合：它们是实数 (`R`) 和复数 (`C`) 域。对于这些情况，当标量域为 `R` 时，向量空间称为实向量空间。当标量域为 `C` 时，称为复向量空间。因此，名称为 `S-MULT` 的运算必须取一个向量并用标量乘之，并在类型 `VECTOR` 的指定载体集合中得到一个向量。从某种意义上说，类型 `SCALAR` 的载体集合决定了向量空间的性质。

### 示例 1.5

最简单的实向量空间是 `VECTOR` 和 `SCALAR` 的载体集合都等于实数 `R` 时。这里，向量可以被视为尾部位于原点的 x 轴上的箭头。虽然标量乘法用于拉伸或收缩这些箭头，但负标量会使箭头逆转一百八十度，而标量零则会得到原点。

### 示例 1.6

另一个实向量空间是 `VECTOR` 的载体集合为复数 `C`，而 `SCALAR` 为实数 `R` 时。这里向量可以被视为尾部位于原点的 x−y 平面上的箭头。同样，标量乘法只会使它们伸长或缩短。当使用标量零时，箭头会变为原点。使用负数时，例如使用 `−1`，会对向量施加 180 度的旋转。

### 示例 1.7



一个复向量空间出现时，`VECTOR` 和 `SCALAR` 的两个载体集合都等于复数。如前例所示，向量可以被认为位于原点为尾部的 `x-y` 平面中。当标量乘法使用复数时：`z = x + i y = r e^{iθ}`，非零向量将按 `r = |z|` 拉伸或收缩，并按 `θ` 角度旋转。

### 1.1.8 MSA 在量子中的基本图示

关于可分 `Hilbert` 空间在复数域或实数域上的基本设定，后文将描述涉及 `MSA` 的高层视角。其代数基础是向量空间，加上内积运算和相应的等式约束。这些定义了内积空间。具体而言，前一节中的等式恒等式 (1)−(8) 必须成立，并且还需满足稍后指定的 (9)−(11)。

更具拓扑性的概念，例如描述切丛、其他丛以及李群和李代数所需的概念，将在 `MSA` 中指定。然而，为完整起见，我们快速描述内积空间成为前面提到的 `Hilbert` 空间的[content]
一个复向量空间出现时，`VECTOR` 和 `SCALAR` 的两个载体集合都等于复数。如前例所示，向量可以被认为位于原点为尾部的 `x-y` 平面中。当标量乘法使用复数时：`z = x + i y = r e^{iθ}`，非零向量将按 `r = |z|` 拉伸或收缩，并按 `θ` 角度旋转。

### 1.1.8 MSA 在量子中的基本图示

关于可分 `Hilbert` 空间在复数域或实数域上的基本设定，后文将描述涉及 `MSA` 的高层视角。其代数基础是向量空间，加上内积运算和相应的等式约束。这些定义了内积空间。具体而言，前一节中的等式恒等式 (1)−(8) 必须成立，并且还需满足稍后指定的 (9)−(11)。

更具拓扑性的概念，例如描述切丛、其他丛以及李群和李代数所需的概念，将在 `MSA` 中指定。然而，为完整起见，我们快速描述内积空间成为前面提到的 `Hilbert` 空间的高层拓扑或分析基础。首先，可分意味着 `Hilbert` 空间内存在一个可数稠密子集。这使得引入 `Schauder` 基成为可能，从而创建具有与 `Hamel` 基相似运算的无限维 `Hilbert` 空间。后者基在所有有限维向量空间中使用。向量按 `Schauder` 基元素的展开几乎与有限维情况相同。最后，`Hilbert` 空间的基本性质是每个 `Cauchy` 序列在范数下收敛；这是内积空间成为 `Hilbert` 空间的额外判据。另见附录 A.1，了解收敛性和完备性的深入描述。在本文档中，除非特别说明，否则假设为可分 `Hilbert` 空间。在有限维实数和复数向量空间情况下，这些拓扑和分析性质始终成立。

描述内积空间或 `Hilbert` 空间的类型集合为 {`SCALAR`, `VECTOR`}。与向量空间一样，类型集合中的每个元素在多值图中被描绘为圆形节点。签名集合中的每个元素在多值图中用箭头表示。多尾箭头用签名集合中特定元素的名称标记。`MSA` 描述从底层标量域的全局结构开始。如前所述，它是机器学习的基础实数和 `Hilbert` 空间量子理论中基本的复数的通用设定。此外，它也是有限域密码学中使用的底层结构。

内积空间或 `Hilbert` 空间的实际签名集合，从高阶到低阶依次给出如下。它们与向量空间相同，但包括了额外的算子名 `IN-PROD`：

$\\begin{array}{l} \\left. {Binary}{operation}{\\left\\{ {V - {ADD}} \\right\\}}, V - {ADD}{maps}{VECTOR} x{VECTOR}\\rightarrow{VECTOR} \\right. \\\\ \\left. \\quad\\quad\\quad\\quad\\quad\\quad\\quad\\left\\{ {S - {MULT}} \\right\\}, S - {MULT}{maps}{SCALAR} x{VECTOR}\\rightarrow{VECTOR} \\right. \\\\ \\left. \\quad\\quad\\quad\\quad\\quad\\quad\\quad\\left\\{ {{IN} - {PROD}} \\right\\},{IN} - {PROD}{maps}{VECTOR} x{VECTOR}\\rightarrow{SCALAR} \\right. \\\\ \\left. {Unary}{operation}{\\left\\{ {V - {MINUS}} \\right\\}}, V - {MINUS}{maps}{VECTOR}\\rightarrow{VECTOR} \\right. \\\\ {{Zero} - {ary}{operation}{\\left\\{ {V - {ZERO}} \\right\\}}, V - {ZERO} - {is} a{special}{element}{of}{the}{sort}{VECTOR}.} \\\\ \\end{array}$

![Equation](img/F000199si4.png)

这些算子名在 图 1.3 中示意。

![图 1.3 内积或希尔伯特空间。](img/F000199f01-03-9780443136979.jpg)

图 1.3 内积或 `Hilbert` 空间。

因此，内积空间或 `Hilbert` 空间的元数序列为 (1, 1, 3(1, 1, 1))。请注意，三个二元算子具有不同的输入或不同的输出。如前所述，当完备性公理成立时（每个 `Cauchy` 序列在范数下收敛），内积空间也成为 `Hilbert` 空间。以下三个等式约束为真时，向量空间成为内积空间，但首先，

* 使用 `a` 和 `b` 作为 `SCALAR`
* 使用 `u`、`v` 和 `w` 作为 `VECTOR`
* 用 `<|>` 或 `<, >` 表示 `IN-PROD`
* 9) 正定性：`< v|v >` 必须大于或等于 0 且 =0 当且仅当 `v=0`。
* 10) 共轭对称：`< v|w > = < w|v >*`，其中 `*` 是共轭运算
* 11) `Conjugate bilinear`：`⟨ a·(u+v) | w ⟩ = a*·⟨ u | w ⟩ + a*·⟨ v | w ⟩` 且 `⟨ u | b·(v+w) ⟩ = b·⟨ u | v ⟩ + b·⟨ u | w ⟩`。 ![Equation](img/F000199si5.png)

向量 `v` 的向量范数，用 `‖v‖[2]` 表示并由内积诱导，给出为 `< v|v >` 的平方根。等价地，`‖v‖[2]² = ⟨v|v⟩` ![Equation](img/F000199si6.png)。序列的收敛性和 `Hilbert` 空间中的 `Cauchy` 判据是参照此范数描述的。应提及的是，内积恒等式 (11) 中给出的共轭双线性律是物理学中通常使用且本文档中始终使用的律。即内积中的第一个参数是共轭线性的。在数学中，通常在 (11) 的第二个等式中使用标量共轭，而不是第一个等式。对于机器学习，共轭的重要性较小，因为标量最常为实数。在这种情况下，标量的共轭就是其本身。

### 1.1.9 有限时信号作为内积空间

考虑所有实值数字有限时信号或函数 `f`，其位于 `R^(Z)` 的子集中。这是对应于 `VECTOR` 的载体集合，而 `R^(Z)` 意味着这些函数定义域等于所有整数且结果为实值，`f: Z → R`。有限时意味着 `f` 只能在整数 `Z` 的某个有限子集上具有非零值。这些函数具有有限支撑，所有这些函数的空间将记为 `A`。请注意，`V-ZERO` 对应于 `A` 中的 0 向量。卷积神经网络（`CNNs`）采用有限时信号，既作为原始数据流，也作为滤波信号。应用包括一维声音、文本、数据、时间序列，以及 EKG 和 ECG 信号分类（Ribeiro et al., 2020）。

有界向量是 `A` 中 `f` 的便捷表示（Giardina, 1991）。`A` 中任何非零信号将在最小整数 `n` 处非零。在这种情况下，函数 `f` 的表示为 `(f(n) f(n+1) … f(n+k))[n]`，其中 `f(n+k)` 是 `f` 非零的最终值。有界向量可以全为零，但从实际观点看，`ZERO` 元素 `0` 将始终被采用。根据定义，此处的约定是 `k` 为非负整数。下标 `n` 是指向 `N` 中 `f` 第一个非零元素的指针。有界向量的通常逐点加法对应于名称 `V-ADD`。加号 `+` 以及 `V-ADD` 本身也将用于实际的逐点加法。如前所述，`V-ZERO` 表示 `A` 中的有界向量 `0`。对于前面提到的 `f`，有 `0 + f = f + 0 = f`。



So, for `g` also in `A` and not identically equal to zero, then `g=(g(m) g(m+1) …g(m+j))[*m*]` and `V-ADD(f,g)=(f(p)+g(p) f(p+1)+g(p+1) … f(p+q)+g(p+q))[*p*]`. So, when both `f` and `g` are not identically equal to zero, `p=min(m,n)`. In this case, `p+q` is the largest integer value for which `f` or `g` is nonzero. Also, `p+q=max(n+k,m+j)`. `S-MULT` in this context is just point-wise multiplication by a real number `r`. Thus, `S-MULT(r; f)=f · r=r · f=(r · f(n) r · f(n+1) … r · f(n+k))[*n*]`. Referring to 第 1.7 节, all the equational identities for a vector space hold true for `A`. Again, the sum or scalar product of a bound vector might be all zeros. In this case, use `ZERO` element.

For any `f` in `A`, the cozero set is defined to be the set of all points in `Z` for which `f` is nonzero. It is the complement of the set where all zeros appear and it is abbreviated as `COZ(f)`. For the function `0`, `COZ(0)` is the empty set. For all other signals `f` in `A`, `COZ(f)` has finite cardinality. Time-limited digital signals `f` and `g` in `A` form an inner product space with a usual ordered dot-type product on the intersection of `COZ(f)` and `COZ(g)`. For the empty set, zero should be used. The conjugate of a real number is itself; accordingly, only positive definite criteria must be shown. Here, `< f, f >` is the sum of squared terms. Therefore, the inner product is greater or equal to zero and will equal zero only for `f=0`. Thus, the inner product space criteria from the previous section hold for the class of bound vectors.

### Example 1.8
Consider the two signals `f` and `g` in `A` given by bound vectors: `f=(3 2 1)[0]`, and `g=(2–1)[0]`. Then `COZ(f)={0, 1, 2}` and `COZ(g)={0, 1}`. Here, the dot or inner product is `< f, g >=6–2=4`. Also, `< f, f >=14`, and `< g, g >=5`. Finally, `V-ADD(f, g)=f + g=(5 1 1)[0]`, `V-MINUS(f)=–f=(–3–2 –1)[0]`, and `S-MULT(f; 1.5)=1.5 (3 2 1)[0]\=(4.5 3 1.5)[0]`.

From the aforementioned example, it is seen that the algebraic operations involving bound vectors are somewhat identical to the usual vector space operations on real-valued vectors. The primary difference is in the subscript at the end of the vector specifying the location of the first nonzero element. In any case, the vector norm of `f`, denoted `‖f‖[2]`, induced by the inner product, is given by the square root of `< f|f >`. The square root will always use a radical `1/2` and will denote a nonnegative quantity, unless specified differently. Equivalently, `∥f∥[2]² = ⟨f|f⟩`![方程](img/F000199si7.png). Convergence of sequences and Cauchy criteria in a Hilbert space are described with reference to this norm. To see that this inner product space `A` is not a Hilbert space, use a sequence of bound vectors: `f[n]=(1 1/2 1/3 … 1/n)[0]`, `n=1, 2, ….` Notice that for `n > m` both are larger than some positive integer `N`, then, for instance, using the two norms in `l² : ∥f[n]−f[m]∥[2]² = 1/(n)² + … + 1/(m+1)²`![方程](img/F000199si8.png). Now, for `N` large enough, this quantity will be arbitrarily small. This shows the sequence of bound vectors `f[k]`, forms a CS. However, in the limit `f[k] → (1 1/2 1/3 …)[0]`, which is not a bound vector. Thus, `A` is not complete, and it is only an inner product space.

### 1.1.10 实希尔伯特空间中的核方法
Kernel methods are closely related to reproducing kernel Hilbert spaces (`RKHSs`), which is a topic in a later chapter. `RKHSs` are special Hilbert spaces where the elements are always functions. This space can be complex, real, or even quaternion. However, in machine learning applications, these spaces are almost always real. Kernels along with `RKHSs` form a central theme for support vector machines. Additionally, kernel methods are employed in statistical machine learning algorithms. In this case, they employ a feature map `Φ`![方程](img/F000199si9.png) that is often used in converting data into higher or infinite dimensions. Higher dimensions often enable simpler information retrieval and classification. Among the reasons for this is that data that cannot be separated in a linear manner may become linearly separable in a higher dimension. A typical contrived example illustrating the use of higher dimensions to linearize data is given next. See also 图 1.4A 和 B. The former illustration provides data in two dimensions. This is before the feature map is used. The latter diagram illustrates what happens after the feature map is utilized.

![图 1.4 (A) R2 中的原始数据和 (B) 特征映射后的数据在 R3 中。](img/F000199f01-04-9780443136979.jpg)

Figure 1.4 (A) Original data in `R²` and (B) feature mapped data in `R³`.

### Example 1.9
Refer to 图 1.4A. That is, in the left portion of this diagram are data points denoted by `o`. These points are within the unit circle and are close to either the `x` axis or the `y` axis in `R²`. The other data points in this diagram lie on or outside of the unit circle, and each point is denoted by `×`![方程](img/F000199si10.png). Moreover, all these points have their `x` coordinate about equal to their `y` coordinate in absolute value. Consider the feature map `Φ: R² → R³`, where `Φ((x y)′)=(x² xy y²)′=(X Y Z)'`. Note that the resulting vector in three dimensions has its second tuple, that is, the `Y` tuple, equal to the product of the tuples in `R²`. Then, in 图 1.4B, it is seen that the feature map transformed all the `o` points in an area near the plane `Y=0`. Concurrently, it transformed all the `×`![方程](img/F000199si11.png) points at least one unit away from the plane `Y=0`. It follows that affine planes close to, but also parallel to `Y=0`, would separate the `o` points from the `×`![方程](img/F000199si12.png) points.

Kernel methods are also useful in establishing independence and conditional dependence of random variables as well as separating signals from noise (Ravi 和 Kumar, 2013). An in-depth treatment of `RKHS` is provided in sections given in a later chapter.

Before the kernel method is described, another motivating example will be illustrated. It uses homogenous monomials of degree `d`, similar to the aforementioned example where `d=2`. More generally, monomials are formed from a product of all possible tuples within a single vector `v` or `w` located in a low dimension Hilbert space, `H[L]`. Each of these monomials is then used as the tuples for vectors in a higher dimensional Hilbert space, `H[H]`. The mapping that performs this operation is `Φ`![方程](img/F000199si13.png) and is again called the feature map, `Φ: H[L] → H[H]`. The kernel `K(v,w)` is given by the inner product of feature maps in the higher dimensional Hilbert space, `K(v,w)=< Φ(v). Φ(w) >`.

### Example 1.10
Consider the carrier set `H[L]=R²` with the vectors, `v=(v[1]v[2])′=(23)′`![方程](img/F000199si14.png), and `w=(w[1]w[2])′=(4−1)′`![方程](img/F000199si15.png). Let the feature map `Φ: R²→H[H]=R⁴`, where `Φ(v)=(v[1]² v[2]²v[1]v[2]v[2]v[1])′=(4966)′`![方程](img/F000199si16.png). Note that all possible monomials are formed, order matters, and all possibilities should be utilized. Similarly, operating on `w`, `Φ(w)=(w[1]² w[2]²w[1]w[2]w[2]w[1])′=(16 1−4−4)′`![方程](img/F000199si17.png). Here, all possible monomials of order two became the tuples of vectors in `R⁴`. Then, taking the inner product in `R⁴` of `Φ(v)` and `Φ(w)`, `K(v,w)=<Φ(v), Φ(w)> = <(v[1]² v[2]²v[1]v[2]v[2]v[1])′, (w[1]²w[2]²w[1]w[2]w[2]w[1])′> = <(4966)′, (16 1 −4 −4)′> = v[1]²w[1]² + v[2]²w[2]² + v[1]v[2]w[1]w[2] + v[1]v[2]w[1]w[2] = 25 = (<(v[1]v[2])′, (w[1]w[2])′>)² = (<(23)′,(4−1)′>)²`![方程](img/F000199si20.png).



因此可以看出，高维空间中的内积与低维空间中内积的 `d=2` 次幂相同。这是问题的关键；每当需要高维度的内积时，就无需利用特征映射。该结果只需在低维中将内积提高到 `d` 次幂即可得到，从而确定高维内积。
更一般地，核方法将希尔伯特空间 `H[L]`=`R^(n)` 中两个向量的点积映射到另一个希尔伯特空间 `H[H]`=`R[m]` 中两个相关向量的点积。当 `n`=`m` 时，出现线性核。在这种情况下，`K(v,w)`=`<v, w>`，且对于 `R` 中的 `a`，`<a v+u, w>`=`a` `<v, w>`+`<u, w>`。类似地，`<v, a w+u>`=`a` `<v, w>`+`<v, u>`。由于它是线性的，核为 `K(v,w)`=`v’w` 且特征映射 `Φ(v)`=`v`。该情况下的 Gram 矩阵是一个 `n` by `n` 矩阵，其条目由 `R^(n)` 中的向量的内积组成，具体而言对于 `R^(n)` 中的 {`v[1]`, …, `v[n]`}；则 `G` 中条目 `G[ij]` 等于 `<v[i], v[j]>`。

### 示例 1.11
再次考虑载体集合 `H[L]`=`R²`，其中向量 `v`=`(v[1] v[2])′`=`(2 3)′`，且 `w`=`(w[1] w[2])′`=`(4 –1)`。假设 `H[L]`=`H[H]` 且特征映射 `Φ` 为恒等映射；则 `v` 和 `w` 的 Gram 矩阵一般给出，并且再次使用 `v` 和 `w` 的实际元组值，`G`=
```
\begin{array}{l}
{\left| \left\langle v,v \right\rangle\quad\left\langle v,w \right\rangle \right| = \left| 13 5 \right|}
\left. \left| \left\langle w,v \right\rangle\left\langle w,w \right\rangle \right|\mspace{21mu} \middle| 5 17 \middle| .# \right.
\end{array}
```
![Equation](img/F000199si21.png)
当 `m` 大于 `n` 时，`m`=`n^(d)`；则 `R^(n)` 中的点积提高到正整数幂 `d` 后，将等于 `R^(m)` 中的点积。这称为多项式核方法或核技巧。这里，定义域空间 `R^(n)` 中的向量 `v` 和 `w` 为 `v`=`(v[1] v[2]…v[n])′` 和 `w`=`(w[1] w[2]…w[n])′`。映射函数 `Φ`: `R^(n)` → `R^(m)` 取向量例如定义域中的 `v` 的所有 `n` 个元组，并形成所有可能的 `d` 次齐次单项式。在形成这些单项式时，定义域向量中的元组需以不同顺序重复。这些不同的单项式随后成为 `R^(m)` 中相关向量的元组；也就是说，由 `v` 的元组形成的单项式成为 `Φ(v)` 中的元组。就元组而言，这是一种非线性映射。如果执行此过程，则 `m`=`n^(d)`。此外，核 `k` 满足 `k(v,w)`=`<Φ(v), Φ(w)>`=`(<v, w>)^(d)`。通过在高维空间中取内积可以看出这一结果：
```
\left\langle {\Phi\left( v \right),\Phi\left( w \right)} \right\rangle = {\sum\limits_{\mathit{j}1}}\cdots{\sum\limits_{\mathit{jd}}{v_{\mathit{j}1}\cdots v_{\mathit{jd}} \cdot w_{\mathit{j}1}\cdots w_{\text{jd},}}} = {\sum\limits_{\mathit{j}1}{v_{\mathit{j1}} \cdot w_{\mathit{j1}}\cdots}}{\sum\limits_{\mathit{jd}}{v_{\mathit{jd}} \cdot w_{\text{jd},}}} = \left\lbrack {\sum\limits_{\mathit{j}}{v_{\mathit{j}} \cdot w_{\mathit{j}}}} \right\rbrack^{d} = \left\langle {v,w} \right\rangle^{d}
```
![Equation](img/F000199si22.png).

### 示例 1.12
在此示例中，设 `n=2` 且 `d=3`。对于 `R²` 中的 `v`=`(v[1] v[2])′`，`Φ(v)` = (`v[1]³ v[2]³ v[1]² v[2] v[1] v[2]² v[2] v[1]² v[2] v[1]² v[1] v[2] v[1] v[2] v[1] v[2]`) , ![Equation](img/F000199si23.png) 是一个 `R⁸` 中的向量。若 `w`=`(w[1] w[2])'`，则三次齐次多项式可以填满 `Φ(w)` 的八个元组，就像它对 `Φ(v)` 所做的那样。假设已完成，则形成：
```
\begin{matrix}
{\left\langle {\Phi\left( v \right),\Phi\left( w \right)} \right\rangle = {\sum\limits_{\mathit{j}1}}\cdots{\sum\limits_{\mathit{jd}}{v_{\mathit{j}1}\cdots v_{\mathit{jd}} \cdot w_{\mathit{j}1}\cdots w_{\mathit{jd}}}} = {\sum\limits_{\mathit{j}1}{\sum\limits_{\mathit{j}2}{\sum\limits_{\mathit{j}3}{v_{\mathit{j}1}v_{\mathit{j}2}v_{\mathit{j}3}w_{\mathit{j}1}w_{\mathit{j}2}w_{\mathit{j}3}}}}}
{= {\sum\limits_{\mathit{j}1}{v_{\mathit{j}1}w_{\mathit{j}1}}}{\sum\limits_{\mathit{j}2}{v_{\mathit{j}2}w_{\mathit{j}2}}}{\sum\limits_{\mathit{j}3}{v_{\mathit{j}3}w_{\mathit{j}3}}} = {\lbrack{\sum_{j = 1}^{2}{v_{j} \cdot w_{j}}}\\rbrack}^{3} = \left\langle {v,w} \right\rangle^{3} = \left\lbrack {v_{1}w_{1} + v_{2}w_{2}} \right\rbrack^{3}}
{= v_{1}^{3}w_{1}^{3} + v_{2}^{3}w_{2}^{3} + 3v_{1}^{2}v_{2}w_{1}^{2}w_{2} + 3v_{1}v_{2}^{2}w_{1}w_{2}^{2}.#}
\end{matrix}
```
![Equation](img/F000199si24.png)
使用特征映射 `Φ` 的好处是不使用它。维度为 `n` 的数据可以在维度为 `m`=`n^(d)` 的希尔伯特空间中使用，而无需实际将数据转换到该维度。每当仅需要高维数据的内积时，这都是成立的。这里唯一需要的计算只是求 `<v, w>^(d)`。特征映射和核方法的应用将在后面的章节中给出，同时还将介绍几种特征映射和各种核。

### 1.1.11 R-模
再次，为了利用 MSA 中的深入高级定义，将描述一个向量空间子结构。它称为交换环 `R` 上的单位 R-模，具有幺元。类型与 MSA 向量空间和域描述中的完全相同。因此类型仍为 `SCALAR` 和 `VECTOR`。签名集合也是如此，除了偏操作名 `INV` 在交换幺环中不存在，在环中也不存在。因此，在如 图 1.1 的多值图 中，结果图将被修改。在这种情况下，`INV` 的虚线箭头将被完全移除。
R-模的实际签名集合与向量空间结构相同。因此，R-模的元数序列仍为 `(1, 1, 2(1, 1))`。签名集合如下：
```
\begin{array}{l}
\left. {Binary}{operation}{\left\{ {V - {ADD}} \right\}},V - {ADD}{maps}{VECTOR} \times {VECTOR}\rightarrow{VECTOR} \right.
\left. \quad\quad\quad\quad\quad\quad\quad\left\{ {S - {MULT}} \right\},S - {MULT}{maps}{SCALAR} \times {VECTOR}\rightarrow{VECTOR} \right.
\left. {Unary}{operation}{\left\{ {V - {MINUS}} \right\}},V - {MINUS}{maps}{VECTOR}\rightarrow{VECTOR} \right.
{{Zero} - {ary}{operation}{\left\{ {V - {ZERO}} \right\}},V - {ZERO} = 0.}
\end{array}
```
![Equation](img/F000199si25.png)
回顾向量空间结构的方程恒等式：`(1)–(8)`，它们对单位 R-模都成立。
请记住，约束 `(1)–(4)` 意味着所描述的结构，即单位 R-模，在向量加法下也是一个阿贝尔群。此外，有时在模的定义中会省略环的交换性。如果是这种情况，则约束 `(5)−(8)` 会相应调整。例如，约束 `(5)` 可能仅写为：`1 · v=v`。`1` 是单侧恒等元。此外，在这种情况下，在定义 `S-MULT` 时必须小心。它只能定义，同时考虑运算顺序。在 MSA 多值图中，使用斜杠标记多值箭头的尾部。在这种类型的图中，斜杠 `/` 用于第一个操作数，双斜杠 `//` 用于 `S-MULT` 的第二个参数。这种符号在描述左模或右模时很重要。当环为域时，所有这些都不重要。

### 示例 1.13



每一个阿贝尔群 `G` 都可以被视为一个单位 `R`-模，定义在具有单位元的交换环之上，即整数 `Z`。在这种情况下，`SCALAR` 具有一个载体集合，由所有整数组成。相应的签名集合与实数的情况相同，只是没有偏逆运算名称。`VECTOR` 具有载体集合 `G`，包含所有群元素。标量乘法与向量空间中的情况相同：

`S-MULT` maps `SCALAR` x `VECTOR` → `VECTOR`,

具体来说，`S-MULT (n; g)=g + g + … + g`，共 `n` 次，其中 `n` > 0。 当 `n`=−1 时，`S-MULT (n; g)=−g`，当 `n`=0 时，`S-MULT (n; g)=0`。

此外，减法运算与通常情况相同：

`V-MINUS` maps `VECTOR` → `VECTOR`,

然而，它是使用标量乘法运算定义的，即 `V-MINUS(g)=S-MULT(−1; g)=−g`。

零元运算是 `R`-模的一个元素，并且与其它运算一样，它是使用标量乘法定义的：

因此，`V-ZERO=S-MULT (0; g)=0`。

最后，加法运算与向量空间中之前的情况相同：

`V-ADD` maps `VECTOR` x `VECTOR` → `VECTOR`,

特别地，如果 `h=n · g` 且 `k=m · g`，其中 `n`、`m` 在 `Z` 中且 `g` 在 `G` 中。 则 `V-ADD(h, k)=S-MULT (n + m, g)=(n + m) · g=n · g + m · g`。

在量子学科中很重要的问题是模是否定义在除环之上，例如四元数。当使用除环时，总是存在一个 Hamel 基。当模不是定义在除环之上时，可能存在基也可能不存在。例如，`R²` 上的向量场存在 Hamel 基，但在两个球面上不存在向量场的基（Eisenberg 和 Robert, 1979）。Hamel 基的存在性在量子学科中很重要，因为无限维向量空间可能没有范数，因此 Schauder 基可能不存在。所有这些将在描述希尔伯特空间的张量积之后随后看到。

## 参考文献
*   Birkhoff 和 Lipson, 1970 Birkhoff G, Lipson B. 异构代数. *J Comb Theory*. 1970;8(1):115–133.
*   Eisenberg 和 Robert, 1979 Eisenberg M, Robert G. 毛球定理的一个证明. *Am Math Monthly*. 1979;86.
*   Feynman, 1986 Feynman R. 量子力学计算机. *Found Phys.* 1986;16(6):507–531 Springer Science and Business Media, LLC.
*   Gelfand 和 Naimark, 1943 Gelfand, I., Naimark, M., 1943. 关于将赋范环嵌入希尔伯特空间上的算子环. Google Books 3–20.
*   Giardina, 1991 Giardina C. *并行数字信号处理，一种统一的信号代数方法* Regency Publishing 1991;.
*   Goguen and Meseguer, 1986 Goguen J, Meseguer J. 关于多类代数可能为空载体集合的若干评注. *Bull EATCS*. 1986;30:66–73.
*   [Goguen 和 Thetcler, 1973 Goguen, J., Thetcler, J., 1973. 计算机科学与范畴论之间的一个交汇 I, IBM Research Report RC4526.
*   Gratzer, 1969 Gratzer G. *通用代数* New York: Van Nostrand Reinhold; 1969;.
*   Halmos, 1957 Halmos P. *希尔伯特空间导论* Published by Chelsea Publishing Company 1957;.
*   Halmos, 1958 Halmos P. *有限维向量空间* Van Nostrand Co 1958;.
*   Ravi 和 Kumar, 2013 Ravi B, Kumar T. 使用核和归一化核仿射投影算法的语音增强. *SIPIJ*. 2013;4.
*   Ribeiro 等, 2020 Ribeiro A, et al. 使用深度学习神经网络自动诊断 12 导联心电图. *Nat Commun.* 2020;11 Article number 1760.
*   Segal, 1947 Segal I. 算子代数的不可约表示. *Bull Am Math Soc.* 1947;53:73–88 [`doi.org/10.1090/s0002-9904-1947-08742.-5`](https://doi.org/10.1090/s0002-9904-1947-08742.-5).

# 第 2 章

## 深度学习的基础

### 摘要
本章首先对机器学习以及数据挖掘进行了描述。它回顾了机器学习的主要目标，即概括并应用自主检测或自主估计。提到了监督学习的实例以及说明和无监督学习的一个例子。提供了有关深度学习和量子技术的参考文献。这些参考文献涉及深度学习在解决量子多体问题以及纠缠问题中的应用。给出了量子神经网络发展的参考文献。下一节描述了当前神经网络节点中使用仿射变换的使用。随后提供了对当今神经网络整体结构的深入视图。接下来给出了在 NN 设计中有用的若干激活函数以及其中一些属性的列表。提到了凸性及其在确定代价函数中的用途。第 2.7 节对分类类型 NN 问题进行了深入描述并进行了说明。在下一节中，使用反向传播以及梯度技术的监督学习用若干示例进行了解释。随后给出了仿射空间的 MSA 描述。最后介绍了深度学习的首要示例。在这一节中，提供了卷积神经网络 (`CNNs`) 当前架构的概述。本章以对循环神经网络及其应用的简要描述结束。

#### 关键词
Affine operator; affine space; activation function; objective function; convex combination; homomorphism; backpropagation; recurrent neural networks

## 2.1 机器学习和数据挖掘
机器学习和数据挖掘是利用数据库寻找数据中关系、关联和结构例如模式的全球性概念（Wittick, 2014）。实际学习的是算法和函数，或在学习机器中编程的具有适当参数设置的运算。其基本哲学是以尽可能少的干预来开发这些程序。目标是采用学习过程对未来数据的特征进行分类、归类、检测或估计。分类型应用可能是二元的或具有更高元数。无论如何，待解决的共同问题是将数据区分并划分为元素具有共同属性的集合。估计过程可能涉及平滑、滤波或预测。平滑是指重新审视过去数据并对过去发生的情况做出最佳估计。滤波是指使用数据来确定现在的最佳估计。例如，自主车辆利用传感器数据作为学习机器的输入。它对数据进行滤波，随后向控制面发送信号。此应用可能涉及导航、制导或其它控制，例如紧急警觉。



一般而言，未来数据与训练数据集相关但有所区别。训练集始终存在；然而，其使用程度可概括为监督学习与无监督学习。监督学习利用训练数据来改进和确定训练算法中的参数。监督学习的一个常见属性是数据附带标签。这些标签通常根据预定特征对数据进行划分。利用监督学习的机器学习两大主要方法是神经网络和支持向量机。它们既用于检测也用于估计。支持向量机在 `Section 1.10` 中被提及，其中给出了核函数的介绍。这些机器将在后面的章节中详细介绍。神经网络通常被称为深度学习机器，是本章的主要主题。卷积神经网络（`CNNs`）也在本章中简要介绍。它们将在后面的章节中结合成像技术进行描述和说明。其他类型的神经网络也存在。特别是，后面的一节中将举例说明几种类型的循环神经网络（`RNNs`）。

无监督学习是一种算法自主地从数据中确定结构的技术。机器学习中这类技术众多。无监督学习始终采用领域知识和大量启发式参数设置。它们范围从诸如 `k-means` 或 `k-median` 技术等聚类的初级方法，到其他计算密集型的源编码特征值方法。特征值公式中包括主成分变换（`PCT`）和奇异值分解（`SVD`）。这些技术以及量子版本也是后面章节的主题。稍后将使用 `k-means` 举例说明无监督学习的一个简单过程。用于数据挖掘目的的该算法的量子版本将在后面的章节中给出（Kavitha 和 Kaulgud, 2022）。

`k-means` 方法是一种聚类技术。当应用于 `R^n` 中有限有序集合 `X` 的向量时，该过程形成 `X` 的一个划分。`k-medians` 方法几乎相同，其中采用数据的中值而不是均值或平均值。划分中子集的数量 `m`，`m>0`，是一个启发式参数，由领域知识决定且必须事先指定。每个有序子集 `S[i]`，`i=1, 2, …, m`，非空且包含一个子集领导者 `L[i]`。该值是子集中所有点的平均值。值 `L[i]` 本身通常不是 `S[i]` 中的元素。为开始该过程，在采用初始条件后计算此平均值。这些初始条件涉及初步猜测，以确定 `X` 的哪些元素是构成划分的子集的成员。

在此之后，递归步骤开始。

递归步骤首先为每个子集计算实际的平均值。具体而言，为每个子集 `S[i]` 找到均值 `L[i]`。请注意，每个 `L[i]` 通常是一个具有 n 个元组的向量，因为平均值是在每个元组中求得并记录的。然后在所有元素 `X` 与每个子集领导者 `L[i]` 之间找到一范数距离 `d[i]`。因此，对于 `X` 中每个定位的向量 `v`，对每个 `i=1, 2, …, m` 执行距离计算 `‖v−L[i]‖`。该计算也对 `X` 中的每个 `v` 执行，`v=(v[1] v[2] … v[n])′`，`‖v−L[i]‖[1]=|v[1]−L[i1]|+|v[2]−L[i2]|+ …+|v[n]−L[in]|`。该计算得到的值按向量位置输入到 `d[i]` 中。每个 `d[i]` 具有相同数量的条目，即 `X` 的基数。在一范数计算之后，对所有距离向量 `d[i]` 执行逐元组比较。找到最小距离的位置，并据此使用 `X` 中的元素和相同的值 `m` 执行聚类或重新分组。每个可能的新子集是通过使用最接近子集领导者的元素创建的。这些步骤反复进行，直到采用停止条件。停止条件是在执行完整递归步骤后划分不再发生变化时。

### 示例 2.1

例如，`X` 是 `R¹` 的一个子集，其中 `X=(1, 2, 3, 4, 7, 8, 9)`。该集合以这种方式书写，因为数据可以重复。为了开始，设 `m=2`，即只有两个集合构成划分。初始猜测的划分是 `S[1]=(1, 2, 3)`，且 `T[1]=(4, 7, 8, 9)`。下一步迭代开始时，计算这些预定分组的平均值作为子集领导者。这些值是实标量，因为集合 `X` 由实值元素组成。这些平均值分别为 `L[S[1]] = 2`，![方程](img/F000266si1.png) 和 `L[T[1]] = 7`。![方程](img/F000266si2.png) 接下来，必须找到 `X` 中每个点到两个子集领导者的 1 范数距离。在此情况下，1 范数就是绝对值。这些距离以有序元组给出 `d[S[1]] = (1,0,1,2,5,6,7)`，![方程](img/F000266si3.png) 和 `d[T[1]] = (6,5,4,3,0,1,2)`。![方程](img/F000266si4.png) 请注意，这与 `X` 中的数据顺序完全相同。执行逐元组比较以找到最小值，比较对象为 `d[S[1]]`![方程](img/F000266si5.png) 和 `d[T[1]]`![方程](img/F000266si6.png)。因此，首先，由于 `d[S[1]]`![方程](img/F000266si7.png) 中的数字 1 小于 `d[T[1]]`![方程](img/F000266si8.png) 中的数字 6，聚类 `S[1]` 将采用第一个元素。

此外，`d[S[1]]`![方程](img/F000266si9.png) 的第 2、第 3 和第 4 个元组也是最小的。然而，`d[T[1]]`![方程](img/F000266si10.png) 中的其他元组是最小的。现在利用这些信息，重新聚类开始，通过仍使用 `m=2` 创建新的划分。将最接近子集领导者的点分配到一个聚类中。新的划分是 `S[2]=(1, 2, 3, 4)` 和 `T[2]=(7, 8, 9)`，可以看出，这种新的聚类与之前的划分不同。

因此，必须执行该过程的另一个递归步骤。所以再次，对应的领导者，即平均值，这次是 `L[S[2]] = 2.5`，![方程](img/F000266si11.png) 和 `L[T[2]] = 8`。![方程](img/F000266si12.png) 接下来，再次计算 `X` 中所有点到每个子集领导者的距离。结果为 `d[S[2]] = (1.5,.5,.5,1.5,2.5,3.5,4.5)`，![方程](img/F000266si13.png) 和 `d[T[2]] = (7,6,5,4,1,0,1)`。![方程](img/F000266si14.png) 逐元组比较与之前类似执行；这次比较 `d[S[2]]`![方程](img/F000266si15.png) 和 `d[T[2]]`![方程](img/F000266si16.png)。这里可以看到，`d[S[2]]`![方程](img/F000266si17.png) 的第 1、第 2、第 3 和第 4 个元组是最小的，但 `d[T[2]]`![方程](img/F000266si18.png) 中的其他元组是最小的。重新聚类在这种情况下给出相同的划分。因此，由于 `S[3]=S[2]=(1, 2, 3, 4)` 且 `T[3]=T[2]=(7, 8, 9)`，采用停止条件。结果是 k-mean 划分。

## 2.2 深度学习



# 深度学习

深度学习是机器学习的一个主要子集，其中信息以并行方式分布并被处理。通常采用神经网络。它们由层或处理器列组成，每一层都根据不同的数据表示被指定不同的任务。进入第一层的数据，即节点的第一列，可能看起来有些随机。第一层节点中的算法通常确定重要特征并将这些特征传输到第二层的节点。经常形成管道型架构。在这里，数据被传输到后续层，通常产生更高的概念信息含量。最后一层，即输出层，产生极高的概念信息，例如人脸识别。Deep 指的是神经网络中存在许多层或列。经常存在大量混合的层，例如 `CNNs` 中使用的层。然而，靠近输出的层通常由采用仿射函数和激活函数的节点组成。这些节点通过传统的反向传播梯度方法进行训练。监督学习和半监督学习被用于深度学习过程。

## 2.3 深度学习与量子关系
十多年来，深度学习神经网络和人工神经网络一直处于研究和应用的前沿。特别是，`CNNs` 在二维或三维成像和机器视觉中被大量使用。如前所述，它们也被用于一维信号应用（Wu, 2021）。最近，`CNNs` 正与量子计算机和量子模拟器结合使用或辅助其工作。这项研究通常旨在解决量子多体问题或量子纠缠问题（Carlo and Troyer, 2022）。当前的基本目标是构建 CNN 的量子版本（`QCNN`）（Choi and Kim, 2020）。这涉及将量子技术与机器学习和神经网络（`NN`）技术合并。特别是，节点 `NN` 的仿射结构很大程度上被量子纠缠所取代。`MSA` 将有助于涉及机器学习和 `QCNN` 的应用的开发。

## 2.4 神经网络中节点的仿射变换
深度学习 `NN` 最简单的类型之一是多层感知器，由节点阵列组成。它已被用于线性可分模式的分类。在数学上，这些阵列在本文中描述，特别是在接下来的几节中，通过使用矩形矩阵组织来描述所有节点。神经网络在局部层面利用仿射变换。感知器、神经元或 `NN` 内的节点最常包含仿射处理设备。处理单元，即每个节点，涉及作为输入到达或来自其他节点的 `R^(n)` 中的列向量 `v`。节点内的计算形式为 `u=W v+b`，其中 `W` 是 1 by `n` 实值权重矩阵。对于 `b=0`，这是线性变换；否则，在所有情况下都是仿射变换。实值标量 `b` 对加权值 `Wv` 造成平移，称为偏置值。这些权重和偏置项可以被视为用于创建某种优化的参数。一旦使用仿射变换计算出值 `u`，该量通常会经历非线性操作 `T`，结果被发送到网络中的其他指定节点。后续章节提供了更多细节。

## 2.5 神经网络的全局结构
如前所述，在深度学习神经网络中，每个节点或神经元都使用仿射变换以及非线性操作。节点标记为 `N[ij]`，应被视为按 `n` by `m` 矩阵 `N` 组织，`n>0`，`m>0`。因此，`i` 表示节点 `Nij` 的行，`j` 表示列，贯穿全文。为了符合通常的 `NN` 协议，可以通过腾空特定节点从前面提到的矩阵型结构构建任意形状的阵列。在任何情况下，对应于每个连接节点的计算值为 `u[ij]`；在该节点，非空的非零节点在此情况下至关重要。

量 `n` 被称为深度，即行数。此外，`m` 是整体矩阵结构内的层数或列数。如前所述，使用深度学习一词时，这通常指的是具有大量层的神经网络。每个列向量或层标记为 `N[k]`，`k=1, 2, …, m`。隐藏层，如果存在，则用除 `N[1]` 和 `N[m]` 之外的所有标签表示。层 `k` 中的节点通常连接到层 `k+1` 中的众多节点，`k=1 to m−1`。一旦最终层 `N[m]` 输出其结果，该量会以某种方式与输入进行比较。因此，在此点创建性能度量。这将涉及目标或代价函数。对应关系可能是精确比较，也可能涉及输入和最终输出的重要特征。实际实现及示例见于 第 2.7 节 和 第 2.8 节。

该设备的输入可被视为 `n x 1` 列向量 `v`。输出如前所述，这里假设为最后 `m^(th)` 列，`N[m]` of `N`。该设备的目的是输入未知向量 `v`，然后通过得出 `N[m]` 的某个函数近似 `v` 来对该向量 `v` 进行分类、识别或确定。这是通过使用某种度量或接近度评估来执行的。节点 `N[ij]` 内的仿射函数涉及权重 `w[ij]` 和偏置 `b[ij]`，`i=1—>n`，`j=1→m`。偏置是实数，权重是实值行向量。它们的长度等于进入该特定节点的输入数量。如前所述，任何节点的输入均表示为列向量中的元组。在本节中，这些权重和偏置假定已知。然而，在通常的 `NN` 应用中，这些量的值以迭代方式找到。

迭代过程涉及优化目标函数以逐步更新权重和偏置参数。该方法通常在监督训练环境中通过反向传播执行。在此，`NN` 的预测输出使用损失或目标函数与期望输出进行比较。随后，该函数被优化以尝试找到最小值。该过程通常依赖于梯度下降进行优化。因此，实践中目标函数和所有激活函数必须连续可微。经过多次训练周期和迭代后，网络权重和偏置可能收敛。当它收敛时，`NN` 就准备好用于实际数据或更常见地用于测试数据集。整个方法在本章的以下各节中进行了描述和说明。



对于第一列或层 `N[1]`，每个节点 `N[*i*1]` 的值形式为 `u[*i*1]=T(w[*i*1] v[*i*] + b[*i*1])`，`i=1—>n`，其中 `T` 是称为激活函数的某种非线性函数。为了简单说明，`T` 可能是最大值，即 `u[*i*1]=max(w[*i*1] v[*i*]+b[*i*1], 0)`。对于第二列 `N[2]`，节点的操作与 `N[1]` 中的类似；这里 `u[*i*2]=T(w*i*2+b[*i*2])`。此时，权重 `w[*i*2]` 将其从列 `N[1]` 中连接节点获得的任何输入相乘。总连接并不总是必需的；列 `N[1]` 中的一些，甚至只有少数节点会连接到 `N[2]` 中的特定节点。该过程通常继续使用相同的非线性，直到来自 `N[*m*\-1]` 的输出进入最后一列 `N[*m*]`。在此最后一列中，通常可能会采用不同的非线性函数 `F`，但自变量仍然是仿射函数。因此，在节点 `N[*im*]` 处，`u[*im*]=F(w*im*+b[*im*])`。权重 `w[*im*]`，即这些行向量，按元组逐元组乘以所有输入到 `N[*im*]` 的输入并加上 `b[*im*]`。在此乘法和加法之后，激活函数 `F` 被计算。同样，只有来自列 `N[*m*−1]` 中指定节点的连接输出进入节点 `N[*im*]`，即网络不必完全连接。

如前所述，反向传播算法用于调整仿射变换中的指定参数。参数更新的值是使用梯度型算法获得的，以最大化/最小化所选目标函数。该过程以穷举迭代的方式执行。反复进行，直到 `NN` 完全学习，输出误差被最小化。通常，使用受控测试数据进行系统验证。对该过程的深入描述始于 第 2.7 节。

下一个示例说明了一个二乘二的 `NN` 结构。它用于说明一些基本的 `NN` 概念，例如仿射变换、激活函数，以及节点之间的数组结构和连接。本示例中未说明学习；此外，所使用的激活函数不仅不可微；甚至不连续。然而，这一特定应用表明，使用 `NN` 可以生成连续函数。单独来看，本示例提供了一个高度为 `h` 的简单方波脉冲，`h>0`，在实值 `a` 和 `b` 之间，`a<b`，在其他地方为零。此类脉冲的线性组合提供了一种阶梯型函数，可以逼近实数线上的任意连续函数。同样，在本示例中，所有参数都是固定的；`NN` 没有学习 (Nielsen 和 Chuang, 2000)。

### 示例 2.2

任意连续函数 `f: R→R` 都可以用阶跃函数逼近。这些函数在所有实连续函数集合 `C(R)` 中稠密。二乘二，`n=m=2`，神经网络将提供高度为 `h` 的单个阶跃，位置在区间 `(a, b\]` 内，在其他地方为零。在第一层 `N[1]` 中存在仿射变换。它们后面跟着激活函数 `T`。简而言之，第一层中每个节点的输出为 `u[*i*1]=1` 当 (`w[*i*1] v[*i*]+b[*i*1]`) > 0 时，而 `u[*i*1]=0` 否则，`i=1, 2`。产生这些结果的仿射函数和激活函数在下面给出。所有双下标标签与 `n` 乘 `m` 矩阵中的完全相同，`n, m>1`。

第一层 `N[1]` 有 `w[11]=1` 且 `b[11]=−a`。因此，`u[11]=T(w[11]x+b[11])=T(x−a)=sgn[max (x−a, 0)]`，因此当 `x` 大于 `a` 时，这给出 1；否则给出 0。这里 `sgn(.)` 是符号函数；对于正输入值它为 1，否则为 0。类似地，`w[21]=1` 且 `b[21]=−b`。`T(w[21]x+b[21])=T(x−b)` 当 `x>b` 时给出 1。在第二层，激活函数 `F=I`；在本例中它是恒等函数。此外，在第二层中 `N[12]` 的偏置项为零。在第二层中存在矩阵加权；它是一个由脉冲高度组成的 1×2 行向量，具体为 `w[12]=(h −h)`。行向量被采用是因为有两个输入到 `N[12]`。以向量形式，该节点的输入是列向量 `(y[1] y[2])′`。在当前的 `NN` 应用中，节点 `N[22]` 未使用。参见 图 2.1。

![图 2.1 用于 NN 方波脉冲创建的矩阵结构。NN，神经网络。](img/F000266f02-01-9780443136979.jpg)

图 2.1 用于 NN 方波脉冲创建的矩阵结构。`NN`，神经网络。

对于第一层，输入向量可以认为是列向量，`v=(x x)′`。实际上，实数 `x` 的值，以非常小的增量，可以同时输入到 `v` 的两个元组。通过将节点 11 的输出 `y[1]=u[11]` 作为节点 12 的输入，并将节点 21 的输出 `y[2]=u[21]` 也作为节点 12 的输入，可得到一个矩形脉冲。该脉冲位于 x 轴上，高度为 `h`，支集大约为 `(a,b\]`。请注意，图 2.1 提供了一个框图。它以严格的矩阵形式给出，说明了创建方波脉冲所需的运算。每个节点由矩形表示。每个活动节点包含一个仿射函数和一个激活运算。同样请注意，节点 `N[22]` 在创建方波脉冲时未被使用。#

为准备 第 2.7 节，其中 `NN` 将被更详细地描述，特别是对于监督学习方面，将给出更具图示性的介绍。这里，符号化地更详细地描述节点内的代数运算是方便的。本文提供的符号表示受 Petri 网启发 (Petri, 1962；Graff 和 Giardina, 2005)。这些网也称为位置和转换网。

在本例中，节点 `N[*ij*]` 内部的运算通过使用代表加法的三角形来说明。该符号用于将标量偏置 `b[*ij*]` 加到加权输入之和上以及创建该和。单个圆圈包围行向量 `w[*ij*]` 内的每个单独标量值权重。圆圈象征乘法运算。同样，行向量内的标量权重按元组逐元组乘以节点 `N[*ij*]` 的输入元组列向量。最后，使用正方形来标识激活函数 `T` 或 `F`。一般来说，激活函数在学习过程中是不变的。然而，激活函数 `T` 或 `F` 的输出通常会发生变化，因为输入到这些函数本身发生了变化。参见 图 2.2 和下面的示例 示例 2.3 以了解这种新符号的一个实例。在所引用的图中，说明了一个简单的节点 `N[*ij*]`。这里，多个输入乘以一个被圈起来的单独标量权重。每个单独的权重是行向量 `w[*ij*]` 内的一个不同元组。随后，所有乘积在三边形中与偏置 `b[*ij*]` 一起相加。最后，正方形表示该节点的激活函数。之前的示例将重复，这次使用 `NN` 节点内的新视觉符号运算。

![图 2.2 NN 节点内运算的符号模式。NN，神经网络。](img/F000266f02-02-9780443136979.jpg)

图 2.2 NN 节点内运算的符号模式。`NN`，神经网络。

### 示例 2.3



与前例一样，使用 `NN` 创建了一个矩形脉冲函数；这次它在 图 2.3 中进行了说明。如前所述，每个节点的内部结构用符号表示。节点 `N[1,1]` 和 `N[2,1]` 除了偏置符号相反外是相同的。同样，两个节点中的激活函数均为 `T(w[*j*1]x+b[*j*1])=sgn \[max (x−b[*j*1], 0)\]`。请注意，在节点 `N[1,2]` 中未使用激活函数；因此在方框内示出了恒等函数。此外，该节点有两个输入到来。因此使用了两个不同的权重，表示高度 `h` 和 `−h`。它们各自被包含在一个圆内。合在一起，这些权重是行向量 `w[12]=(h −h)` 中的条目或元组。最后，如前所述，节点 `N[2,2]` 在此 `NN` 中未被使用。

![图 2.3 用于 NN 方波脉冲创建的符号计算。NN，神经网络。](img/F000266f02-03-9780443136979.jpg)

图 2.3 用于 `NN` 方波脉冲创建的符号计算。`NN`，神经网络。

## 2.6 神经网络的激活函数和代价函数

常规 `NN` 的节点使用仿射函数后跟激活函数 `F`，后者几乎总是非线性的。激活函数的常见属性是，当仿射映射的输出作为 `F` 的输入时，`F` 通常返回 \[−1, 1\] 或 \[0, 1\] 中的值。在后一种情况下，输出被理解为概率值。更重要的是，当使用反向传播时，`F` 必须具有连续导数。当不是这种情况时，`F` 的不连续导数具有这样的性质：输入的极小变化可能导致输出导数值发生剧烈偏差。请参阅下面的示例。

### 示例 2.4

函数 `f: R→R`，其中当 `x` 非零时 `f(x)=x² sin(1/x)`，且 `f(0)=0`。该函数可微，且当 `x` 非零时 `f′(x)=2x sin(1/x)−cos(1/x)`，且 `f′(0)=0`。因此，例如，如果 `x[1]=0` 且 `x[2]=1/(1000π)`，则 `f′{x[1])=0`，但 `f′(x[2])` 为一。

激活函数通常必须选择为在使用反向传播时梯度不会消失或爆炸。当梯度变得太小时，权重和偏置或多或少保持不变。另一方面，梯度爆炸会导致不稳定，这几乎从不导致学习。这在 `RNN` 中是一个大问题，因为存在反馈；然而，第 2.11 节 中描述的修改后的 `RNN` 被创建来克服其中一些问题。

下面列出了几种常用的激活函数以及它们的取值范围和导数（当后者存在时）。这些函数在实数线上定义，
*   Sigmoid: `T(x)=1/(1+e^(−x))`；取值范围：(0, 1)；导数：`T′(x)=T(x) (1−T(x))`
*   双曲正切：`T(x)=2 (1–e^(−2x))^(−1)–1`，当 `x` 不为零时，且在零处为 −1；取值范围：\[−1, 1\]；导数：`T′(x)=(1–T²(x))`
*   ReLU：`T(x)=0` 当 `x < 0` 时且否则 `T(x)=x`；取值范围：\[0, ∞)；导数：`T′(x)=0` 当 `x<0` 时且 `T′(x)=1` 当 `x>0` 时；`T′(0)` 不存在。
*   Soft log：`T(x)=log(1+e^(x))`；取值范围：(0, ∞)；导数：`T′(x)=1/ (1+e^(−x))`
*   ArcTan：`T(x)=tan^(−1)(x)`；取值范围：(−1, 1)；导数：`T′(x)=(1+x²)^(−1)`。

用于多类分类的最常用的激活类型函数之一是 `Softmax`。它几乎总是用于 `NN` 的最后一层的输出。从这个角度来看，`Softmax` 可以被认为是一个伪节点。它是多输入到多输出的类型。因此，最后一层中所有 `n` 个节点 `N[m]` 的输出进入 `Softmax`。假设这些输出为 `x[1]`，…，`x[n]`；则
`Softmax (x_i) = (e^{x_i}) / (sum_j e^{x_j})`![方程](img/F000266si19.png)。此外，假设伪节点跟踪从所有最终节点 `N[i,m]` 发送的输入，并按顺序发送 `Softmax` 计算结果作为输出。在这种情况下，任何实际最终节点的输出本身也可以被认为是一个概率。因为在最终节点之后，输出值进入伪节点，它由 `Softmax` 计算并取 \[0, 1\] 中的值。而且所有最终节点输出经 `Softmax` 转换后的总和为一。

### 示例 2.5

假设 `NN` 中存在三个最终节点。每个这样的节点将其输出发送到伪节点 `Softmax`。如果每个最终节点的实际输出按顺序为 (2, 1, 0.5)，这些值进入伪节点。`Softmax` 操作被应用三次，并按顺序提供实际的概率类型向量，大约等于 (0.6, 0.25, 0.15)。从此输出中，最终节点一导致正确的分类。

在机器学习中采用各种目标或代价函数。大多数时候，这些函数是凸的。在 `R¹` 中，`f` 在区间 `[a, b]` 中是凸的，这意味着对于该区间中的 `x` 和 `y`，`x<y`，以及 `[0, 1]` 中的任意 `λ`，`f (λx+(1−λ) y)` 小于或等于 `λ f (x)+(1−λ) f (y)`。这意味着 `f` 在区间 `[x, y]` 中的弦大于或等于该区间内 `f` 的值。凸目标函数被使用，因为在这种情况下局部最小值也是全局最小值。在后面的章节中，使用模拟退火和特别是量子退火技术，采用非凸目标函数。退火型操作通常能够使全局最小化发生（Laarhoven and Aarts, 1987）。

### 示例 2.6

请参阅 示例 2.1，其中 k-means 过程使用一范数目标函数进行说明。在这种情况下，由于使用了来自 `R¹` 的数据，一范数为 `‖v‖[1]=|v|`。对于 `[0, 1]` 中的 `λ` 和 `R¹` 中的任意 `x` 和 `y`，`|λ x+(1−λ)|` 小于或等于 `λ|x| + (1−λ)|y|`，由三角不等式得出。因此该目标函数是凸的。

其他重要的凸代价函数是二次的，例如最小二乘法和涉及方差缩减的方法，如平方误差。

## 2.7 使用单节点神经网络的分类

回想一下，来自 第 2.5 节，`NN` 内的节点 `N[ij]` 的地址与矩阵中的条目完全相同；数量 `(i, j)` 分别表示第 i 行和第 j 列。

使用一个圆，每个圆包含一个标量值权重，表示为行向量 `w[ij]` 内的一个元组。此外，圆本身象征乘法运算。节点内，代表加法的三角形象征将标量偏置 `b[ij]` 加到节点 `N[ij]` 的加权输入之和上。最后，使用一个方框来标识激活函数 `T` 或 `F`，并使激活函数激活并提供标量输出。第 2.6 节 提供了几种激活函数的描述。在本节中，使用单节点 `NN`。对于这种情况，不使用下标；此外，输入值 `v` 将是指定区间内的实数。它将进入节点，然后进入包含指定权重的圆形图。权重的乘法在此发生。圆形图的输出标记为 `x` 并进入三角形，其中偏置值 `b` 加到 `x` 上。三角形的输出为 `y`，该值进入方形图。在这里，激活函数 `F` 被求值，且 `z=F(y)` 为输出值。整个场景在 示例 2.7 中进行了说明，并在 图 2.4 中进行了说明。

![图 2.4 使用具有不连续激活的 NN 进行分类。NN，神经网络。](img/F000266f02-04-9780443136979.jpg)



图 2.4 使用非连续激活的 `NN` 分类。`NN`，神经网络。

### 示例 2.7

目标是构建一个 `NN`，其输入可视为美元，`v` 在区间 \0, ∞) 内。输出 `z` 用于标记大于 50,000 的任何输入；在这种情况下，输出 `z` 设为一；否则设为零。执行此二元分类的单节点 `NN` 如 [图 2.4 所示。在此情况下，每当输入 `v` 进入时，它会被 `w=1` 相乘，因此 `x=v`；该值加上偏置 `b=−50,000`，得到值 `y=v−50,000`。该值用作激活函数的输入，`F(y)=sgn[max(y, 0)]=sgn[max(v−50,000, 0)]`。因此，当 `v>50,000` 时，`z` 出现一。否则，值 `z=0` 出现。这与 示例 2.2 和 2.3 中使用的完全相同的激活函数。#

早期示例中采用的激活函数通常不用于 `NN` 应用。首先，在此示例中，`max` 函数是连续的，但不可微。更糟的是，`sgn` 函数甚至不连续。如前所述，`NN` 应用通常需要连续可微函数。这是因为反向传播学习方面，这是所有情况下必不可少的。

由于 示例 2.7 中使用的激活函数几乎从未使用，示例将使用 sigmoid 函数再次进行。在这种情况下，输出 `z` 可理解为概率。同样，这是一个分类问题；现在 `z` 的值对于肯定输入将大于 1/2，即当输入大于 50,000 时。如果输入小于或等于 50,000，则值将为 1/2 或更小。

### 示例 2.8

再次假设输入为美元，`v` 来自区间 \0, ∞)。输出 `z` 在任何输入大于 50,000 时给出值 `z>1/2`；否则设为 1/2 或更小。执行此二元分类的单节点 `NN` 如 [图 2.5 所示。再次，每当输入 `v` 进入时，它会被 `w=1` 相乘，因此 `x=v`；该值加上偏置 `b=−50,000`，得到值 `y=v−50,000`。所得值是新激活函数的输入，`F(y)=1/(1+e^(-y))=1/(1+e^(-(v-50000)))`。因此，当 `v>50,000` 时，`z` 出现介于 1/2^+ 与一之间的数字。否则，`z` 为零与 1/2 之间的数字。#

![图 2.5 使用 sigmoid 激活的 NN 分类。NN，神经网络。](img/F000266f02-05-9780443136979.jpg)

图 2.5 使用 `NN` 进行 sigmoid 激活的分类。`NN`，神经网络。

## 2.8 神经网络学习的反向传播

本节中，最初假设完整 `NN` 的结构已定义，因此所有偏置和权重都完全已知。此外，这还包括所有激活函数 `T` 或 `F`，以及所选的误差准则 `C`。第 2.6 节 描述了几种众所周知的激活函数和误差度量。训练 `NN` 的反向传播过程是一种监督学习，其中必须执行大量的计算。它首先利用应用的领域知识，以便为每个节点中的每个权重和偏置值提供有根据的猜测。通常，当没有领域知识时，权重是随机选择的，偏置通常设为零。还需要训练数据。逐一地，每条训练数据 `x` 将进入并由 `NN` 执行或处理。最终，`NN` 出现输出 `z`。该输出也称为预测输出。值 `z` 用于成本或目标函数 `C`。然后将其与实际、真实或期望输出 `d` 进行比较。期望值在开始 `NN` 反向传播过程之前已知。值 `d` 取决于实际输入 `v`。计算成本会产生误差 `ϵ`![Equation](img/F000266si20.png)，当其不为零时，表示需要使用反向传播以及梯度下降方法重新校准权重和偏置。

对每个要更新的节点值，使用链式法则描述 `C` 的变化。这些变化 `ΔC` 是由于权重 `ΔW` 的变化或偏置 `Δb` 值变化引起的。需要更新值以应用梯度算法。链式法则的每个结果都成为梯度下降算法中斜率的值。然后，涉及 `C` 以及任何要更新的权重或偏置的梯度算法被采用。在所有情况下，`ΔW or Δb = -η grad(C)`，其中 `η`![Equation](img/F000266si22.png) 是一个正数，称为学习率，且是启发式找到的。减号用于梯度指向最大变化方向，但此处成本需最小化。梯度下降以索引 `k=0` 的初始条件开始。然后，对于 `k=0, 1, 2, …`，算法计算：`x[k+1]=x[k]-η[k] f′(x[k])`。如前所述，步长为 `η[k]`，且是启发式找到的。

在上述计算之后，整个过程重复；再次，将权重或偏置的新值代入，并用这些新值再次执行 `NN`，然后找到新的预测输出 `d`，计算成本，等等。将呈现一系列示例以说明反向传播和链式法则协议。所有这些示例都利用 示例 2.8 中给出的情况，其中实际解事先已知。在实际 `NN` 应用中，这永远不会发生。对此示例进行刻意的更改，一次一个地，一次一个地更改后续示例中的权重或偏置。通过这样做，反向传播和链式法则方法变得更易于理解，并且通过反向传播到达解的路径变得更明显。重申一下，将跟随几个示例，其中精确解是已知的。然而，在偏置或加权项上故意设置错误，反向传播和链式法则计算将在某种程度上纠正错误设置。

### 示例 2.9

请参阅 示例 2.8，其中输入 `v` 是区间 \0, ∞) 中的值。输出 `z` 应在任何输入大于 50,000 时为值 `z>1/2`；否则设为 1/2 或更小。但这次，拟议的输出将故意不出现。在 [图 2.5 中，本示例中使用的实际 `NN` 已修改，用于本示例以及接下来的两个示例。观察以下图，指示了三个不同的条件集。每组在权重或偏置值中都有一个故意错误。这些值按顺序列在图表中从圆圈到三角形的传输下方。这些值应应用于本示例，然后按顺序应用 示例 2.10，然后是 示例 2.11。




### 示例 2.9
在本示例中，当输入 `v` 进入时，保持正确的权重 `w=1`，因此 `x=v`。然而，这次令偏置设为 `b′=−51,000`。 图 2.6 说明了与前一个示例相同的 `NN`，但对于此问题使用了新的偏置值；它是 `b′=−51,000`，但权重保持不变；它是 `w=1`。使用新的偏置值得到值 `y=v−51,000`。因此，任何小于 51,000 的输入值都不会被此 `NN` 结构标记。据此，这可能导致误分类。例如，当值 50,999 进入时，预测输出得到的值更接近于零而不是一。这是通过将 `y=v−51,000=−1` 输入激活函数 `z=F(y)=1/(1+e^(−y))=1/(1+e)=0.27` 得出的。因此，在这种情况下，`NN` 的实际观测输出远小于 1。然而，由于输入为 `v>50,000`，期望输出为 `d=1`。采用目标函数 `C`，得到 `C=(d−z)²=0.53=ϵ`![Equation](img/F000266si23.png)。该目标函数的值是实际误差的另一个指示。然而，使用反向传播后，误差的新值将小于 0.53。

![图 2.6 单节点 NN 的偏置和权重修改。 NN，神经网络。](img/F000266f02-06-9780443136979.jpg)
图 2.6 单节点 `NN` 的偏置和权重修改。 `NN`，神经网络。

从成本函数开始并使用链式法则，目标是更新偏置以使成本函数减小。因此首先，需要偏置变化引起的成本函数变化；它是 `dC/db`。使用链式法则，向后进行，并参考上面提到的 图 2.6。此变化取决于成本函数相对于输出 `z` 变化如何减小。该输出来自 sigmoid 函数，具体为 `dC/dz`。请记住，sigmoid 函数的输出会因其输入 `y` 发生变化而变化；这概括为 `dz/dy`。最后，值 `y` 可以因偏置的变化而变化；因此 `dy/db` 象征此变化。利用链式法则得到所需的反向传播公式，`dC/db=dC/dz dz/dy dy/db`。代入实际值得到 `dC/dz=−2 (d−z)=−1.46` 且 `dz/dy=F′(y)=F(y) (1−F(y))=.27 · 0.73=0.2`。最后，`dy/db=1`，因此将这些全部相乘得到 `dC/dz=−0.3`。该值的负数将在梯度算法中使用。使用学习率 `η`![Equation](img/F000266si24.png)，设 `η=1000`，然后向当前偏置 `b′=−51,000` 增加 300 得到偏置的新值 `b′*=−50,700`。此计算为 `b′*=b′− η dC/dz`。

上述描述简要介绍了梯度下降算法。学习率 `η`![Equation](img/F000266si26.png) 的参数设置被采用；由于我们事先知道真实答案，所以作弊了。当偏置设为错误值时，即 `b′=−51,000`，则成本或损失函数被视为 `ϵ=0.53`，值得注意的是，由于本示例中设置的偏置值太小，算法给出了偏置变化的正向增加。如果再执行一次反向传播迭代，偏置会再增加一点。最终，偏置的真实值 `b=−50,000` 应该得到。

下一个示例将再次说明反向传播过程。这次，偏置 `b″` 被设为过大值。在这里，将看到该过程会提供偏置值的减小。

### 示例 2.10
再次参考 示例 2.8，输入 `v` 是区间 \0, ∞) 中的值。输出 `z` 应在任何输入大于 50,000 时为值 `z>1/2`；否则，设为 1/2 或更小。再次，当输入 `v` 进入时，保持正确的权重 `w=1`，因此 `x=v`。现在，将使用大于最优值的偏置，因此令 `b″=−49,000`，得到值 `y=v−49,000`。再次参见 [图 2.6，用于本示例的实际 `NN`；这里 `w=1` 且 `b″=−49,000`。因此，任何大于 49,000 的输入值都将被标记，值大于 1/2，即使不应该。这再次导致误分类。例如，当值 49,001 进入时，预测输出得到的值更接近一而不是零。计算是通过将 `y=v−49,000=1` 输入激活函数 `z=F(y)=1/(1+e^(−y))=1/(1+e^(−1))=0.73` 发生的。在当前情况下，由于输入为 `v<50,000`，期望输出为 `d=0`。我们使用目标函数 `C=(d−z)²=0.533=ϵ`![Equation](img/F000266si27.png)。此非零值也表明存在误差。因此，需要使用梯度算法以及反向投影。

再次使用链式法则，与前一个示例完全相同，`dC/db=dC/dz dz/dy dy/db`，其中 `dC/dz=−2 (d−z)=1.46` 且 `dz/dy=F′(y)=F(y)(1−F(y))=0.733·(1–0.73)=0.196`。最后，`dy/db=1`，因此将这些全部相乘得到 0.29。由于在梯度算法中使用 0.29 的负值，这自动提供了偏置的负向增加。偏置变得更接近期望值至关重要。由于已知真实答案，设学习率 `η=1000`；则偏置的新值由 `b″*=b″ – η dC/dz=–49,000–290=–49,290` 给出。

将给出最后一个示例，这次保持偏置在正确值但略微改变加权函数值。在这种情况下，采用过大的加权函数。反向传播和梯度技术将指出此误差并在某种程度上纠正它。然而，通常必须反复使用这些算法才能可能获得最优解。

### 示例 2.11
再次参考 示例 2.8，输入 `v` 是区间 \0, ∞) 中的值。输出 `z` 应在任何输入大于 50,000 时为值 `z>1/2`；否则，设为 1/2 或更小。与之前类似，提出的输出不会出现，这次是因为使用了错误的权重 `w′`，但仍采用正确的偏置。参见 [图 2.6 以了解说明本示例的 `NN`。当输入 `v` 进入时，使用了不正确的权重 `w′=1.1`，因此 `x=1.1· v`。偏置设为 `b=−50,000`。进行计算后，任何大于 45,454 且小于 50,000 的输入值使用此 `NN` 结构都会导致误分类。例如，当值 45,455 进入时，预测输出得到的值更接近一。请注意 `x=w · v=1.1· 45,454=50,001`。此外，通过将 `y=x−50,000=50,001−50,000=1` 输入激活函数，`z=F(y)=1/(1+e^(−y))=1/(1+e^(−1))=0.73`。在这种情况下，由于输入为 `v<50,000`，期望输出为 `d=0`。我们使用目标函数 `C=(d−z)²=0.53=ϵ`![Equation](img/F000266si29.png)。该值也表明需要梯度算法，随后给出反向投影。

根据链式法则，`dC/dw=dC/dz dz/dy dy/dw`，其中 `dC/dz=-2 (d−z)=1.46` 且 `dz/dy=F′(y)=F(y) (1−F(y))=0.73 · (1−0.73)=.96`。最后，`y` 因权重变化而变化与因偏置变化而变化不同。在这种情况下，涉及输入，`dy/dw=v=45,454`。最后，将这些全部相乘得到 63,709。然而，在梯度算法中使用该值的负数。这里，设学习率为 `η=.000001`。新的权重 `w″*=1.1−0.063709`，约为 1.036，是更接近真实值 `w` 的值。

## 2.9 仿射空间的多排序代数描述



仿射空间由一个非空集合 `A` 组成，其中包含元素 `a` 和 `b`，以及一个支撑向量空间 `V`；`V` 被称为 `A` 的平移空间。 对于 `A` 中任意两点之差，都存在一个对应的向量 `v` 在 `V` 中，即 `a−b=v`。 特别地，`a−a=0`。 有一种求逆的方式，写成 `b=v + a`。 该方程被解释为 `a` 沿向量 `v` 平移以得到点 `b`。 当 `v=0` 时，`b=a`，即没有平移。 在任何情况下，考虑映射 `+`：`A x V → A`。 因此，在这种情况下，向量空间作用于 `A` 中的点集。 `V` 中的向量移动 `A` 中的元素；也就是说，`V` 中的向量将 `A` 中的元素平移到新的位置（贝格, 1964）。

仿射空间 `A` 是向量空间 `V` 的主齐性空间；也就是说，`A` 非空，并且对于 `A` 中的 `a` 和 `b`，存在唯一的向量 `v` 在 `V` 中使得 `a + v=b`（朗和泰特, 1958）。 仿射空间具有 `V` 对 `A` 的自由且传递的作用。 该性质也称为 `V-torsor`；也就是说，向量空间 `V` 作为平移作用于 `A`，采用其加法群的左或右挠子。 在 MSA 方法中，实际上有三种类型：`SCALAR`、`VECTOR` 和 `ELEMENTS`。 然而，在 图 2.7 中，只显示了两种类型；也就是说，`SCALAR` 被省略。 如通常所说，`VECTOR` 指的是向量空间，但向量空间中签名集内的运算符名称在此图中未示出。 `ELEMENTS` 指非空仿射空间，直观上看起来像没有零的向量空间。 为了使 `A` 成为 `V-torsor`，需要一个签名集和一个单一的二元运算名称 `TRANS`。 它是这样的

![图 2.7 仿射空间的多元图.](img/F000266f02-07-9780443136979.jpg)

图 2.7 仿射空间的多元图。

`TRANS: A x V → A`.

此外，`TRANS` 必须遵守三个等式约束。 为了看这些，令 `v`、`w` 和 `0` 表示类型 `VECTOR`，并令 `a` 为 `ELEMENT`。 也使用 `+` 表示 `TRANS`。

1. 1) 零平移: `a + 0=0 + a=a`
2. 2) 结合性: `a + (v + w)=(a + v) + w`
3. 3) 同构映射: `A x V → A x A`, `(a, v) → (a, a + v)`

仿射空间 `A` 可以被视作向量空间 `V` 中不经过原点的一条线、平面或超平面。 例如，考虑 `V=R³`，`A` 中的元素 `u` 和 `v`；和 `u+v` 最常见的情况不在 `A` 中。 对于标量倍数 `a · u` 也是如此，其中 `a` 在 `R` 中。 任何这样的仿射空间都平行于经过原点的平面 `S`。 该平面 `S` 是 `V` 的子空间。 选择 `A` 中任意固定元素 `w`，差 `u−w` 在 `S` 中，以及 `v−w`。 这定义了 `A` 与 `S` 之间的一一对应关系。 从这种对应关系，可以在 `A` 上定义加法和标量乘法。 因此，使用 `A` 中的固定 `w`，则 `A` 中的 `V-ADD( u,v)` 表示 `u + v − 2w`，在 `S` 中。 同样，`A` 中的 `S-MULT( a; v )` 表示 `a v −a w`，在 `S` 中。

### Example 2.12

在 `V=R³` 中，考虑由满足方程 `2 x+3 y=0` 的点集 `(x, y)` 定义的子空间 `S`。 令仿射空间 `A` 由平面上的点集定义：`2 x+3 y=6`。 请注意，该仿射空间可以乘以任意非零标量。 例如，将最后一个方程乘以 2 得到 `4 x + 6 y=12`。 因此，存在仿射空间的等价类。 令 `w` 为 `A` 中的固定点 `(0, 2)`。 要对 `u=(3, 0)` 和 `v=(6,−2)`，两者都在 `A` 中，相加，使用 `u−w=(3, −2)` 在 `S` 中，以及 `v−w=(6, −4)` 也在 `S` 中。 要对 `u` 和 `v` 相加，参考上述公式，取 `a=b=1`；然后 `u + v −1 w=(9, −2)−(0, 2)=(9, −4)` 在 `A` 中。

### Example 2.13

令 `SCALAR` 和 `VECTOR` 的载体集均为实数域 `R`。 另请参阅示例 10.5，其中该结构在通常条件下是向量空间。 更进一步；然而，它是希尔伯特空间。 在这种情况下，可以形成内积。 `R` 中的向量 `v` 可以被认为是箭头，水平向右或向左，其尾部位于原点。 `V-ZERO` 是向量 `0`。 因此，例如，如果 `v=7` 且 `w=−3`，则 `V-ADD(v, w)=u=4`。 请注意点积或内积 `<v, w>=−21`，以及 `∥*w*∥[2]² = 9`![方程](img/F000266si30.png) 都是 `R` 中的标量。 另外，使用一范数，`w` 的长度为 `‖w‖[1]=3`。 最后，考虑仿射空间，其类型 `ELEMENT` 也为 `R`。 然后取点例如 `P[1]=8`，`TRANS(P[1]; v)=P[2]=15`。 该向量将实数线上的点从位置 8 移动到位置 15。

## 2.10 卷积神经网络概述

卷积神经网络是深度学习结构的首要示例。 `CNNs` 的应用用于解决识别以及分类问题。 然而，`CNNs` 大多用于具有局部相关结构的数据，对于随机型数据则不太有用（LeCunn 等, 1989）。 应用范围从人脸识别到在自驾车辆中使用三维数据。 后续章节提供了有关这些和其他图像类型应用的 `CNNs` 的更多细节和示例。 这里，主要简要描述单维 `CNNs`。 一维 `CNNs` 应用于声音、时间序列或数据流，例如股票市场价格。

前向传播是 `CNN` 的第一步，将在下面描述。 特定架构取决于应用，但通常涉及若干层卷积节点。 不同层应用不同的滤波器或核。 在每一层中，来自输入信号的绑定向量或来自前一节点的输出信号的卷积与指定的核进行卷积。 有时还会添加偏置，再次在节点内创建仿射型操作。 这些层通常堆叠，但以前馈方式应用。 为了获得更好的结果，有时会在修改卷积中使用的滤波器或核以及偏置（当它们未使用时）时采用反向传播。 这里，标准梯度技术与反向传播过程一起使用。

在执行卷积层之后，甚至有时在卷积层之间，通常会应用池化层。 这是一种压缩或源编码操作，也称为下采样。 它压缩或总结来自前一层的信息。 池化方法通常是对指定数据组的简单平均，并且该平均值代替数据组本身使用。 通常执行最大池化，其中为指定数据组选择的最大值用来替换数据组。 另外，有时使用截断方法进行归一化；例如，使用 `ReLU`。 该操作用于使所有值非负。 堆叠层涉及若干卷积、`ReLU` 或池化层按某种指定顺序排列。 在每种情况下，对于二维或更高维的应用都需要重塑操作。 该算子将无序信息转换为严格有序的信息向量，以输入到常规 `NN`。 最后，应用密集层，一个或多个全连接 `NN` 层。 它通过反向传播训练以确定每个节点内仿射变换中的最优值。 这涉及与前一节所述类似的操作。




超参数是为 `NN` 运行所需启发式确定的参数设置。它们来源于领域知识、试错或迁移知识。对于整体架构，超参数决策包括卷积层的数量、池化层的数量以及 `ReLU` 层的数量。此外，还需要为相关的连接深度 `NN` 提供参数，以及特征数量、核或滤波器的类型及其大小和步长的参数。后者参数处理在池化和卷积层中数据值之间插入的零的数量。步长在边界向量卷积过程中的提及在第 3.2 节中再次出现并附有示例。其他超参数包括层的类型、每层的数量以及应用顺序。

## 2.11 循环神经网络简要介绍

循环神经网络（`RNNs`）对于时间序列数据和其他顺序输入值流很有用。`RNNs` 的主要属性是其递归反馈特性。它能够利用过去和现在的数据进行数据预测或滤波。应用包括文本分类、文本生成、时间序列预测、金融应用和医学草图。`RNNs` 可以利用不同维度的数据，然而它们也有自身的问题。包括消失的 sigmoid 激活函数和梯度爆炸特性。因此，当经常使用反向传播时，该方法会很麻烦。每当 `NN` 权重大于一时，梯度就会爆炸。另一方面，当权重小于一时，梯度趋于零。梯度消失和爆炸使训练变得非常困难。部分解决方案是在梯度过大时进行裁剪，并在梯度过小时重新初始化不同的偏置。

针对梯度爆炸或消失的知名解决方案涉及对 `RNNs` 的两种修改。第一种是使用长短期记忆（`LSTM`）机器（Hochreiter and Schmidhuber, 1997）。另一种是使用门控循环单元（`GRUs`）。三种 `NN` 机器各由一个节点组成，示例如图 2.8。该图中使用的符号学在第 2.5 节中描述，并在图 2.2 中示意。每个圆圈包含一个权重，且输入到圆圈的所有输入都相乘。三角形将所有输入相加，指向三角形的箭头表示偏置，该偏置会加到其他输入上。方块表示激活函数，输入为自变量。图中 sigmoid 用 `σ` 表示，双曲正切用 `T` 表示。

![图 2.8 循环神经网络的类型。(A) RNN，(B) LSTM，(C) GRU.](img/F000266f02-08-9780443136979.jpg)

图 2.8 循环神经网络的类型。(A) RNN，(B) LSTM，(C) GRU。

`RNN` 机器的单个节点示例如图 2.8A。在该图中，反馈连接清晰地示出。在应用中，这些节点被复制，从而产生深度大于一的 `RNN`。在这些情况下，反馈连接被取消，并从一个节点到下一层深度相同节点建立新的连接。权重输出连接到下方节点带偏置 `b[1]` 的新三角形。

长短期记忆使用两条路径代替 `RNNs` 中使用的反馈回路。见图 2.8B。上方路径用于长期记忆，下方路径用于短期记忆。`LSTM` 节点中同时采用 sigmoid 和双曲正切激活函数。有关这些激活函数的描述，请参阅第 2.6 节。下面，单个 `LSTM` 节点被划分为五个阶段。每个阶段包含一个激活函数。输入在被修改时经过 sigmoid 函数，全部包含在第一阶段，常称为遗忘阶段。该阶段提供应被记住的长期记忆的百分比。下一阶段也使用 sigmoid 函数，用于指示应记住的潜在记忆的百分比。随后阶段涉及双曲正切激活函数并处理潜在长期记忆。它必须决定记住多少潜在记忆。记住的程度由输入控制。图中顶部传输所示的输入门指的是 `LSTM` 单元如何确定我们应如何更新长期记忆。最终阶段通过首先使用双曲正切激活函数来更新短期记忆。这里使用潜在短期记忆，该阶段称为输出门。输出门还具有输入，表示来自先前 sigmoid 激活函数的应记住的潜在记忆百分比。输入仅进入前四个阶段，并以间接方式被最终阶段利用。最终阶段输出长期记忆和短期记忆。`LSTM` 避免了梯度爆炸和消失。然而，由于在应用中必须有许多层 `LSTM` 节点，因此训练仍然困难。迁移学习在 `LSTM` 中也无用。

最后的示例如图 2.8C。它是一个 `GRU` 节点的示意图。该图提供了与 Cho et al. (2014) 给出的方程相对应的架构。下面给出这些方程，其中令 `F` 表示 sigmoid 激活函数，使用 `T` 表示双曲正切激活函数。在该图中，底部输入用 `x` 表示，顶部示出的先前状态输入为 `h′`。然后最左侧的 sigmoid 输出函数用 `r` 表示，其中 `r=F (w[1]·x+w[2]·h′+b[1])`。类似地，下一个 sigmoid 的输出为 `z`，其中 `z=F (w[3]·x+w[4]·h′+b[2])`。在该图中，计算 `z` 后，它乘以等于负一的权重。然后三角形将 `1−z` 相加。该数量随后乘以权重一和 `h′`。值 `z` 也乘以激活函数 `T` 的输出 `a`。因此，新状态输出 `h` 给出为旧状态 `h′` 与双曲正切激活函数输出 `a` 的凸组合。这里，图中描述的方程与参考文献中的方程之间存在细微差异。具体而言，输出状态 `h=(1−z)·h′+z·a` 且 `a=T (w[5]·x+w[6]·(r·h′)+b[3])`。在参考文献论文中，使用了不同的凸组合，`h=z·h′+(1−z)·a`。

## 参考文献

*   Berger, 1964 Berger M. *几何问题* Springer-Verlaine 1964;.

*   Carlo and Troyer, 2022 Carlo G, Troyer M. 用动脉近网络求解量子多体问题。 *Science*. 2022;.

*   Cho et al., 2014 Cho, K., et al., 2014. 门控循环神经网络在序列模型上的实证评估。 ArXiv:1412.3555.

*   Choi and Kim, 2020 Choi J, Kim J. 量子卷积神经网络（QCNN）教程。 *Quantum Phys.* 2020;.

*   Graff and Giardina, 2005 Graff C, Giardina C. 动态 Petri 网：传感器网络和分布式并发系统的新的建模技术。 *MILCOM* 2005;.



*   Hochreiter 和 Schmidhuber, 1997 Hochreiter S, Schmidhuber J. 长短期记忆。 *神经计算.* 1997;9.
*   Kavitha 和 Kaulgud, 2022 Kavitha, S.S., Kaulgud, N., 2022. 用于检测心脏病的量子 K-means 聚类方法，采用量子电路方法。 Soft Comput. 27.
*   Laarhoven 和 Aarts, 1987 Laarhoven P, Aarts E. *[`doi.org/10.1007/978-94-015-7744-1`](https://doi.org/10.1007/978-94-015-7744-1)* 1987; *模拟退火：理论与应用* Dordrecht: Reidel; 1987;.
*   LeCunn 等, 1989 LeCunn, Y., LeCun, B., Boser, J., Denker, D., Henderson, R., Howard, W., et al., 1989. 使用反向传播网络的手写数字识别，收录于 NIPS’89.
*   Lang 和 Tate, 1958 Lang S, Tate J. 阿贝尔簇上的主齐性空间。 *美国数学杂志.* 1958;80.
*   Nielsen 和 Chuang, 2000 Nielsen M, Chuang I. *量子计算与量子信息* Cambridge: Cambridge University Press; 2000;.
*   Petri, 1962 Petri, C., 1962. 与自动机通信 (博士论文). University of Bonn.
*   Wittick, 2014 Wittick, P., 2014. 量子机器学习，量子计算对数据挖掘的意义。 ISBN: 9780128100400.
*   Wu, 2021 Wu M. 利用 CNN 进行心电信号分类的心律失常研究。 *计算神经科学前沿* 2021;.

# 第 12 章
## 基本群与通用覆盖群
### 摘要
本章首先对同伦和同伦方块进行了深入描述。提供了若干使用同伦方块的示例。证明并说明了同伦中的初始点等价。随后给出了基本群的 MSA 描述。在同一节中，提供了涉及同伦类的群方程恒等式的证明。提供了群的所有方程恒等式的证明。描述了同伦等价，并给出了示例。随后说明了每个李代数都有一个特殊的关联单连通李群，从而得到通用覆盖群。
#### 关键词
基本群；环路；覆盖映射；通用覆盖群；Cornwell 映射
## 12.1 同伦的图形视图
请回忆，拓扑空间 `T` 在路径连通时称为单连通。也就是说，存在一个连续函数 `f: [0, 1]→T`，使得对于 `T` 中的任意两点 `x` 和 `y`，都有 `f(0)=x` 且 `f(1)=y`。对于另一个连续函数 `g: [0, 1]→T`，其中 `f(0)=g(0)` 且 `f(1)=g(1)`。那么，当它们可以在 `T` 中连续收缩到一点 `xo` 时，这两条路径就定义了一个环路。在这种情况下，`f(0)=f(1)=g(0)=g(1)`。它被称为两个连续函数 `f` 和 `g` 之间的同伦 `H`，提供了 `T` 中的环路（Whitehead, 1978）。同伦必须满足：
*   `H: [0, 1] x [0, 1]→T`，其中
*   `H(t, 0)=xo`，对于所有 `t` 在 `[0, 1]` 中；这里，`xo` 是 `T` 中的初始点也是终点；
*   `H(t, 1)=xo` 对于所有 `t` 在 `[0, 1]` 中；`t` 是定位 `T` 中环路的参数；
*   `H(0, s)=f(s)` 对于 `s` 在 `[0, 1]` 中，`t=0`；这定位了 `f`，并且通过改变 `s`，它创建了环路；
*   `H(1, s)=g(s)` 对于 `s` 在 `[0, 1]` 中，`t=1`；这定位了 `g`，并且改变 `s` 时，它创建了环路。
请参阅 图 12.1；单位同伦方块 `[0, 1] x [0, 1]` 执行同伦。`[0, 1] x [0, 1]` 内的垂直线映射并创建 `T` 中不同的连续环路。方块水平底部的 `t` 值定位了对应于环路的连续函数。这些值仅作为指向环路的指针。在同伦方块的极端垂直边缘，左侧 `t=0` 处，存在创建环路 A 的映射。它由连续函数 `f` 形成。它将被写成 `f(s)=A`，因此当 `s` 从零向上变化朝向方块顶部朝向 `s=1` 时，环路形成。在该方块的右侧，即 `t=1` 处，函数 `g` 被指示；它提供了环路 B。因此，`g(s)=B`。其他 `t` 值决定了其他环路，这些环路不一定在 `T` 中介于环路 A 和 B 之间。其他垂直线位于单位方块内部 `f` 和 `g` 的线之间。在图中，连续函数 `h(s)=C` 出现在 `t=1/3` 处。请注意曲线 C 与曲线 B 重叠。使用 `H(t, s)`，通过连续改变 `t` 并随后显示由 `H(t, s)` 形成的环路也从 `H(0, s)` 连续变化到 `H(1, s)` 来证明同伦。
![图 12.1 同伦方块.](img/F000254f12-01-9780443136979.jpg)
图 12.1 同伦方块。
### 示例 12.1
设 `T=R²`，并设 `xo` 为点 `(1, 0)`。假设 `f(s)=(cos(2*π*s), sin(2*π*s))`，对于 `s` 在区间 `[0, 1]` 中。在这种情况下，当 `s` 从零到一时，`f` 定义的环路是原点为中心的单位圆。它从 `xo=(1, 0)` 开始，遍历圆圈，回到 `xo`。
下一个示例提供了一个同伦，其中环路决定参数 `t` 确实产生了介于 `f` 和 `g` 给出的环路之间的环路。参见 图 12.2。
![图 12.2 仅在原点相交的环路的同伦示例.](img/F000254f12-02-9780443136979.jpg)
图 12.2 仅在原点相交的环路的同伦示例。
### 示例 12.2
再次设 `T=R²`。同时使用 `xo=(0, 0)`。设 `f` 为常数定点恒等映射，即对于所有 `s` 在 `[0, 1]` 中，`f(s)=(0, 0)`。同时设 `g(s)=(1−cos(2*π*s), sin(2*π*s))`。运算 `H` 显示 `f` 和 `g` 是同伦的。而且，通过从零连续变化 `t` 到一，函数 `H(t, s)` 提供了介于 `f` 和 `g` 给出的环路之间的连续不同环路。为了看到同伦，使用 `H(t, s)=(t(1−cos(2*π*s)), t sin(2*π*s))` 并连续地使 `t` 从零变化到一。通常，值 `t` 指向不同的环路。
## 12.2 环路的初始点等价
基本群通常用 `π`[1] 表示，仅使用涉及连通性的拓扑性质即可找到。然而，它是一个实际的代数群，描述拓扑形状。特别是，它指定了简单拓扑结构（如路径连通空间）内的孔洞。这将在随后说明。更高阶同伦群用于在更一般的拓扑结构（如高阶球面）内寻找孔洞。实际上，基本群由满足涉及可连续相互转换的环路的 RST 关系的等价类组成。参见 示例 12.3。这被指定为同伦；它先前已在关于路径和连通性的参考中定义。接下来将证明该同伦形成 RST 等价类。



为了证明自反性，即 `f` 在同伦方块中与自身同伦，令 `H(0, s)=H(1, s)=f(s)`，但也令 `H(t, s)=f(s)` 对所有 `t` 在 \[0, 1\]。这是一个常值映射，它以 `f(s)` 开始，并且当 `t: 0→1` 时，它保持在 `f(s)` 并最终到达 `f(s)`。接下来，为了证明对称性，如果 `f` 与 `g` 同伦，则存在一个同伦映射 `H(t, s)`。为了证明 `g` 与 `f` 相关，使用 `H(1−t, s)`。相应地，当 `t: 0→1` 时，`H(1, s)=g` 变为 `H(0, s)`，即为 `f`。最后，为了证明传递性，设 `F(t, s)` 提供从 `f(s)` 到 `g(s)` 的同伦。另设 `G(t, s)` 在 `g(s)` 与 `h(s)` 之间给出一个同伦。那么 `H(t, s)` 将在 `f(s)` 与 `h(s)` 之间给出一个同伦，当 `H(t, s)=F(2t, s)` 对 `t` 在 \[0, 1/2\] 时，且 `H(t, s)=G(2t−1, s)` 对 `t` 在 \[1/2, 1\] 时。注意在 `t=1/2` 时，`F(1, s)=G(0, s)`，它表示相同的点 `xo`。下一个例子将说明同伦的等价类。

### 示例 12.3

考虑 `R²` 中的 `x`、`y` 平面，但在 `(0, 0)` 处有一个针孔。这可以建模为原点处存在一根柱子，并使用绳子创建环。见 图 12.3。使用与 `(0, 0)` 不同的任意点 `xo` 作为起点和终点。不包围针孔的环与 `xo` 同伦；这起到了恒等的作用。这些环彼此同伦并形成一个记为 `\[I\]` 的等价类。稍后这个陪集将采用零的陪集代表元。属于 `\[I\]` 的环可以沿正方向，即逆时针，或沿反方向，即顺时针追踪。对于这个陪集，这并不重要；这些环都是等价的。所有这样的环都与 `xo` 同伦。这是因为所有这些环都可以连续收缩到 `xo`。与恒等不等价的环必须再次以 `xo` 为起点和终点，但现在还必须包围针孔。这些环与 `\[I\]` 中的环不同伦。从 `xo` 开始和结束并包围针孔的绳子的连续收紧永远不可能完全变形为点 `xo`，因为原点处的柱子在其内部。

![图 12.3 环的等价类。](img/F000254f12-03-9780443136979.jpg)

图 12.3 环的等价类。

环包围针孔的次数存在不同的等价类。针孔从水平表面向上指向。对于逆时针包围，这些等价类用 `\[1\]`、`\[2\]`、`\[3\]`、… 表示，表示环完全包围或完全绕过针孔的次数。因此存在无限多个等价类。此外，这里方向很重要。因此，如果环 `g` 顺时针绕行且仅包围针孔一次，它不能属于 `\[1\]`，因为在 `\[1\]` 中的 `f` 与 `g` 之间找不到同伦。在这种情况下，`g` 属于 `\[−1\]`。类似地，如果一个环顺时针包围针孔 `n` 次，则它属于等价类 `\[−n\]`。这在 图 12.3 中有所说明。结果是每个整数都存在一个等价类，其中整数 0 对应于 `\[I\]` 中的 `I`。

所有环的等价类集合在函数的拼接下形成一个群。对于道路连通空间，环不必出现在同一点 `xo`；在这里，起点不同的环是同伦的。在这种情况下，同伦是通过以两种方式遍历连接不同初始点的路径来显示的。图 12.4 说明了该过程。在此图中，从初始点 `x1` 到 `xo` 的路径由 `h` 遍历，而从 `xo` 返回到 `xo` 的环由 `f` 遍历。然后轨迹使用函数 `h^(−1)` 返回到点 `x1`。通过让 `x1` 连续接近 `xo` 可得到同伦。总路径由 `h x (f x h^(−1))` 或 `(h x f) x h^(−1)` 给出。利用群的结合性，这些路径在同伦意义下相同。结合律稍后证明。

![图 12.4 起点等价。](img/F000254f12-04-9780443136979.jpg)

图 12.4 起点等价。

对于李群，基本群总是交换的（Humphreys, 1997）。然而一般情况下并非如此；反例在 示例 12.10 中给出。

## 12.3 MSA 对基本群的描述

在 MSA 描述中，单一类型 `ELEMENT` 的载体集合是所有环的等价类集合。等价类应写为 `\[f\]`，表示与 `f` 同伦的所有环，但在本节中并非如此。应理解等价类在没有通常记号的情况下使用，即只使用 `f` 而不是 `\[f\]`。另外在图中，环及其定义函数均由表示连续函数 `f` 和 `g` 的符号表示，从而创建这些环。符号 `~` 用于表示等价。`MULT` 这里是拼接而不是函数的复合。因此，二元情况下的操作顺序是先使用左环或操作数；然后在 `MULT` 中使用右参数。多态图在 图 12.5 是提醒二元运算顺序的采用。如常，多态箭头的尾部对第一个操作数有一个单破折号。`MULT` 在多态箭头中的第二个尾部用两个斜线标记第二个操作数。签名集合内的所有群运算名称如下：

* `MULT(f, g)`: \[0, 1\] x \[0, 1\]→`T`，其中 `T` 是一个拓扑空间。
* `MULT(f, g)(s)=f(2 s)` 当 `s` 在 \[0, 1/2\] 时且 `=g(2 s -1)` 当 `s` 在 \[1/2, 1\] 时。
* `INV`: `f^(−1) (s)=f(1−s)` 当 `s` 在 \[0, 1\] 时。
* `IDENTITY`: `e(s)=xo` 对所有 `s` 在 \[0, 1\]。

![图 12.5 基本群的多态图。](img/F000254f12-05-9780443136979.jpg)

图 12.5 基本群的多态图。

通常的等式恒等式必须对群结构成立。这里，为方便起见，替换或使用：

* `ELEMENT` 用 `A`、`B`、`C` 代替。
* `MULT(A,B)` 用 `A x B` 代替。
* `IDENTITY` 用 `I` 代替。
* `INV(A)` 用 `A^(−1)` 代替。

等式恒等式以下写为严格恒等式，但它们实际上在涉及等价类的同伦下成立；除非巧合，否则它们不逐点成立：

1. 1) 结合律：`(A x (B x C))=((A x B) x C)`.
2. 2) 恒等条件：`I x A=A x I=A`.
3. 3) 逆元：`A^(−1) x A=I` 是左逆元，且 `A x A^(−1)=I` 是右逆元；两者都必须对群结构成立。

多态图在 图 12.5 说明了同伦中使用的运算符名称。

图 12.6 说明了如果 `f~f′` 且 `g~g′`，则 `MULT(f, g)(s)~MULT(f′, g′)(s)`。在此图中，有一个道路连通的拓扑空间 `T`，具有同等环 `f` 和 `f′` 与同伦 `H`，以及同等环 `g` 和 `g′` 与同伦 `K`。此外在此图中是同伦方块，`K` 在内部上方，位于 `s=1/2` 上方，而 `H` 在同伦方块内部的下半部分。左侧是上方为 `g` 下方为 `f`。右侧是上方为 `g′` 下方为 `f′`。这里，`MULT(f, g)(s)=f(2 s)` 当 `s` 在 \[0, 1/2\] 时，且 `=g(2 s −1)` 当 `s` 在 \[1/2, 1\] 时。这本质上表明对于等价类，拼接类型的乘法是良定义的。注意在 `s=1/2` 时，`f(1)` 等于 `g(0)`；这表明它们相等，事实上等于 `xo`。

![图 12.6 等价类是良定义的。](img/F000254f12-06-9780443136979.jpg)

图 12.6 等价类是良定义的。



结合律在 图 12.7 中得到证明。在此图中，存在一个拓扑空间 `T`，包含三个回路。这些实际上是等价类。连续函数 `f`、`g` 和 `h` 表示这些回路。在此情况下，`f(0)=f(1)=g(0)=g(1)=h(0)=h(1)`。观察同伦方形的两个不同的垂直边。在方形的左侧，`t=0`，乘积 `f x (g x h)` 被示出。在此侧，令 `H=f(2 s)` 对于 `s` 在 [0, 1/2] 中，`H=g (4 s − 2)` 对于 `s` 在 [1/2, 3/4] 中，且 `H=h(4 s − 3)` 对于 `s` 在 [3/4, 1] 中。在右侧，乘积 `(f x g) x h` 给出。这里，`K=f (4 s)` 对于 `s` 在 [0, 1/4] 中，`K=g(4 s − 1)` 对于 `s` 在 [1/4, 1/2] 中，且 `K=h (2 s − 1)` 对于 `s` 在 [1/2, 1] 中。再次，结合律对等价类成立，而不对单个函数 `f`、`g` 和 `h` 成立。它在同伦下成立，而非逐点成立。如果在 [0, 1] 中选取任意点 `t`，则该点决定构成同伦的具体函数。请注意，存在直线段分隔 `f`、`g` 和 `h`，它们是根据 `s` 和 `t` 定义的。此外，这些函数的自变量在很大程度上是非线性的。

![图 12.7 结合律的证明.](img/F000254f12-07-9780443136979.jpg)

图 12.7 结合律的证明。

在 `t=0` 时，在同伦方形的左侧，所示函数的求值与前面给出的 `H` 一致。右侧在 `t=1` 时同样如此；求值给出 `K`。此外，对于 (0, 1) 中的任意点 `t`，同伦存在，因为过渡是连续的。例如，如同伦方形所示，在 `t=1/3` 时，存在一条虚线垂直线。在这条虚线上，随着 `s` 从零垂直增加到一，存在三个不同的定义域范围。每个 `f`、`g` 和 `h` 各有一个定义域，使用自变量 `s`。对于 `f`，定义域为 [0, 5/12]。对于 `g`，定义域为 [5/12, 8/12]，对于 `h`，定义域为 [8/12, 1]。这些函数 `f`、`g` 和 `h` 的求值，当然是连接回路的等价类的代表，将显示同伦。在下倾斜线段上，且在 `t=1/3` 时，这里 `s=5/12`，求值 `f` 给出 `f((20/12)/(2–1/3))=f (1)`。对于同一点 (`t`, `s`)，求值 `g` 得到 `g(20/12 + 1/3–2)=g(0)`。请注意，`f(1)=g(0)` 在同伦意义下相等；它们代表最终点和初始点的相等。也就是说，它们表示 `T` 中同一点 `xo`。类似地，在 `t=1/3` 的上倾斜线段上，`s=8/12`。在此点，函数 `f` 和 `g` 的求值均给出 `g(1)=h(0)`。

等价类上恒等条件成立的证明在 图 12.8 中给出。图中仅显示了该恒等的一个部分，`f x I=f`。另一部分 (`I x f=f`) 以类似方式证明。图中示出的是同伦方形。左侧为 `f x I`，右侧仅为 `f(s)`。同伦首先通过考虑左侧获得，即 `t=0`。这里，`H=f(2 s)` 对于 `s` 在 [0, 1/2] 中，且 `H=f(1)`；也就是说，它对于 `s` 在 [1/2, 1] 中是常数。右侧为单独的 `f(s)`。对于 0 与 1 之间的任意 `t`，`f` 的下部区域的上边界等于倾斜线段，`s=(1 + t)/2`。在此区域，`f` 的自变量为 `2 s/(t +1)`；因此，对于任意 `t` 和倾斜线上的对应 `s`，`f` 的上边界值一致；它是 `f(1)`。这与倾斜线之上相同。

![图 12.8 单位元条件.](img/F000254f12-08-9780443136979.jpg)

图 12.8 单位元条件。

图 12.9 涉及 `f` 的逆函数。该图的目的是说明事实 `MULT(f, INV(f))=IDENTITY`。这是右侧恒等。左侧恒等关系可以以类似方式显示。拓扑图中的恒等是点 `xo`。该图中的任何回路都可以从 `xo` 完全到达 `xo`，然后解开并返回，表明逆函数。然而，这仅在 `t=0` 时发生。在所有其他情况下，路径将从 `xo` 开始，但会停滞。它本质上会停止，然后转身返回，再次到达 `xo`。这确实是 图 12.9 下图所示的情况。请注意，逆时针运动归因于 `f`，顺时针运动归因于 `INV(f)`。在左上角，小图说明了从 `xo` 到 `xo` 的完整旋转。其后是逆完整旋转。这仅与同伦方形的左边界 `t=0` 相关，且之前已解释。部分旋转在该图左上角下方示出。请注意，在此应用中 `INV(f)(s)=f(2–2 s)`。

![图 12.9 逆函数等式恒等式.](img/F000254f12-09-9780443136979.jpg)

图 12.9 逆函数等式恒等式。

同伦方形 `H` 也在图中给出。`H` 的左侧为 `f` 和 `f^(-1)`。具体而言，对于 `s` 在 [0, 1/2] 中，应用 `f(2 s)`。在区间 [1/2, 1] 中，使用 `f(2–2 s)`。同伦方形的右侧为 `f(0)`，表示恒等函数。对于 `t` 在 [0, 1] 中，存在倾斜线段 `s=1/2 + t/2` 和 `s=1/2 − t/2`，`s` 在 [0, 1] 中。这些线段为同伦函数 `f` 的自变量提供边界。对于固定的 `t`，`s` 在 [0, 1] 中的值导致 `f` 的回路或部分回路。特别地，在方形的极端处，左侧当 `s: 0→1/2` 时，`f` 逆时针做出从 `xo` 到 `xo` 的完整回路。对于 `s: 1/2→1`，回路以顺时针方式在其自身上回溯。这在同伦方形左侧的最上方图中示出。同伦方形的右侧边界为恒等，其中对于 `s` 在 [0, 1] 中，没有运动发生，回路保持在点 `xo`，对于所有 `s` 在 [0, 1] 中。然而，对于 `t` 在 (0, 1) 中，所有情况下都会发生运动。然而，它不会逆时针做出完整回路，运动会停滞并顺时针返回到 `xo`。

例如，在 `t=1/3` 时，图中有一条虚线垂直线。该线在两点处与 v 型倾斜线相交。在下倾斜线段上，相交点给出 `s=1/3`。在下部区域对 `s=1/3` 处函数 `f` 的求值给出 `f(2/3)`。再次求值，这次在中心区域对 `s=1/3`，得到 `f(1–1/3)=f(2/3)`，再次是相同的值。这对于连续性是必须的。在此情况下，未达到回路。随着 `s` 向上变化，没有运动，直到遇到上倾斜线段；也就是说，随着 `s` 增加，`s: 1/3→2/3`。在最上部区域，运动再次开始但为顺时针。它从点 (1/3, 2/3) 开始，提供值 `f(2–4/3)=f(2/3)`，与 v 形区域内 `f` 的值一致。在上部区域，逆时针运动占主导，最终 `f` 在 `f(1)` 处结束，即恒等。随着 `t: 0→1`，回路的创建发生连续变化，从完整回路及其撤销不断变化到仅一点。序列在 图 12.9 中的同伦方形极左处示出。

## 12.4 说明基本群

基本群将在几种情况下找到，特别是对于李群。这些群同构于众所周知的无限群，例如在加法下的 `Z`，或在乘法下的正实数。另一个无限基数的基本群在下面的例子中描述。这里，等价类再次使用通常的括号记号 `[]` 表示。

### 例 12.4



参考 `x`、`y` 平面在 `R²` 中，但在 `(0,0)` 处有一个针孔，如 例 12.3 所示。恒等元对应于所有不包围原点的环路的等价类 [`I`]，且与点 `xo` 同伦。逆时针包围原点 `n` 次的环路属于等价类 [`n`]。对于包含原点并顺时针包围它 `m` 次的那些环路，形成等价类 [−`m`]。相应的基本群同构于 `Z`，即在通常加法下的所有整数。例如，若 `f` 在 [2] 中且 `g` 在 [3] 中，则 `MULT(f, g)` 在 [5] 中。此外，若 `h` 在 [`I`] 中，则 `MULT(f, h)` 在 [2] 中，若 `k` 在 [−7] 中，则 `MULT(f, k)` 在 [−5] 中。最后，`INV(k)` 在 [7] 中。

接下来的几个例子以直观的方式呈现。有关严格的论述请参阅（Strom, 2011；Humphreys, 1972；Hatcher, 2002）。

### 例 12.5

对于李群 `SO(3,R)`，如例 11.28 中所述，已知半径为 `π` 的闭球是 `SO(3,R)` 的典型矩阵 `e^(i a X j)`![Equation](img/F000254si1.png) 的完整定义域。也就是说，对应于该群中任意元素的流形上的坐标位于此球内或其上。此外，在这两个点上存在相同的矩阵值，即在此球上任意一点与其对应的对径点。正是由于这一点，与 `SO(3,R)` 相关的基本群的元素比仅包含恒等元 `I` 的等价类更多。取任意两个环路 `f` 和 `g`，它们从内部点 `xo` 开始并结束，且保持在此球的开区域内，则 `f~g~I`。然而，对于任意环路 `h`，从 `xo` 开始如果它在任意点 `p` 处触及边界，则它返回到 `xo`，离开点为对径边界点，该点与点 `p` 直接相对。其原因是该点处矩阵的值与对径点处的值相同。它们代表群的同一元素。正因如此，形成一个新的等价类；假设它包含 -`I`。简而言之，基本群同构于 `Z2`。它有基数二。注意，从 `xo` 开始的两个不同路径触及球面会得到两个对径点。相应的路径随后返回到 `xo`，意味着它们属于等价类 [`I`]。

### 例 12.6

对于李群 `SU(2,C)`，如例 11.26 中所述，已知半径为 `2π` 的闭球是 `SU(2,C)` 的典型矩阵 `e^(i a j s j)`![Equation](img/F000254si2.png) 的完整定义域。此外，在此球的边界上每一点都只有一个对应的矩阵。`SU(2,C)` 中所有环路都满足恒同伦。即只有一个等价类；它是恒等元。取两个环路 `f` 和 `g`，它们都从 `xo` 开始并结束。并且假设 `f` 保持在球的内部并返回到 `xo`。然而，让 `g` 击中边界并返回到 `xo`，离开边界上某个任意点 `p`。在这种情况下，边界上的所有点都像一个点一样起作用。这是因为将边界坐标代入会得到一个群元素，即唯一的矩阵。相应的环路总能被带回到点 `p` 并分离。结论是 `g′~f′`。因此，基本群只包含一个等价类 [`I`]。此示例与上一个示例的区别在于，这里球上的点是相同的，因此沿边界的移动是允许的。在前一个示例中，一旦在球面上发生移动，这总是对应于对径点的相同类型的移动。

### 例 12.7

在 `R²`![Equation](img/F000254si3.png) 中，8 字形是两个圆的楔和。基本群是非交换自由群，由两个生成元组成。生成元 `a` 总是沿着 8 字形的同一半部分顺时针绕行，左侧部分。生成元 `b` 则在 8 字形的另一半部分逆时针绕行。这些是这些圆形型曲面上的正旋转。当 `a` 在左侧逆时针绕行时，它形成逆型字；一次完整旋转形成 `INV(a)=a^(−1)`；对于右侧圆与 `b` 也是如此。见 图 12.10。两个生成元的自由群由形如：(`v=a^(n1) b^(m1) …a^(nk) b^(mp)`) 的字或元素组成，`ni` 和 `mj` 为整数。这些形成字串，随着绕 8 字形的旋转而出现。`IDENTITY=a⁰=b⁰`，记为 `I`。例如，字串 `f=a²b³` 对应于向左顺时针旋转两次，随后向右逆时针旋转三次。现在假设乘法过程和求逆运算扩展到字串。则可得 `MULT(f, INV(f))=a²b³ x (b^(−3)a^(−2))=I`。

![Figure 12.10 Figure eight.](img/F000254f12-10-9780443136979.jpg)

图 12.10 八。

对由字串操作组成的代数的更深入描述见 第 14.4 节，题为 MSA For Partial Isometries。

## 12.5 拓扑空间的同伦等价

当 `F: X→Y`、`G: Y→X` 且 `G(F)=the identity on X`，并且 `F(G)` 是 `Y` 上的恒等元时，两个拓扑空间 `X` 和 `Y` 被称为同伦等价。当此条件成立时，给出 `F` 和 `G` 的记号为同伦等价，`F~G`。在此条件下，恒等式的等式分别由 `G(F)=Ix` 和 `F(G)=Iy` 给出。此等价服从 `RST` 关系。注意，此处的操作是函数复合而不是拼接。当复合时等于单侧恒等式的函数称为同伦逆。当两个拓扑空间同胚等价时，它们是同伦等价的。反之不成立。

### 例 12.8

考虑拓扑空间 `X=R^(n)`，并且说另一个空间 `Y` 只是 `R^(n)` 中的某一点，设 `Y={0}`。则 `F: X→Y`，因此 `R^(n)` 中的所有点都映射到 `0`，并且设 `G: Y→X` 使得 `G(Y)={0}`。于是 `G(F)=Ix` 且 `F(G)=Iy`。两个空间 `X` 和 `Y` 是同伦等价的而不是同胚的。

## 12.6 通用覆盖群

对于连通拓扑空间 `X`，存在单连通空间 `Y` 和映射 `f`，使得 `f: Y→X`。此映射称为覆盖映射。当 `X` 单连通时，它具有平凡的基本群并且是其自身的万有覆盖 (Hatcher, 2002)。对于连通李群 `H` 的万有覆盖群 `G` 是所有具有相同李代数 `h` 的群中唯一的单连通李群，如 `H`。这些群形成一个族，其李代数为 `h`。李代数有一个特殊的关联单连通李群，成为万有覆盖群。如同每个覆盖群一样，存在覆盖同态 `L` 的核 `K`。同态是连续的满群同态 `L: G→H`。此外，`K` 是 `G` 的离散正规子群，且 `H=G/K`。映射到 `H` 中 `p` 的点称为 `p` 上的纤维；它们是左陪集。此外，包围 `p` 的不相交开集，`H` 中的内部点，称为片。

### 例 12.9



考虑圆群 `T`。它是一个一维流形，并且是非零复数在乘法下的单参数子群。具体而言，`T = {z, such that z is in C, |z|=1}`。它是在复平面内唯一的（至同构）紧致且连通的李群。它与 `U(1)` 同构，即第一么正群。`T` 的覆盖群是 `R`，即带有通常加法群的实数。覆盖同态 `L: R → T`，其中 `L(r) = e^(2*irπ*) = cos(2r*π*) + i sin(2r*π*)`。`L` 是满射但不是 1–1。同态的核是所有整数 `Z` 的集合，因为 `T` 中单位元 `1` 的原像是整数，`R` 中的 `Z`。`T` 与 `R/Z` 同构。

寻找通用覆盖群的过程将针对李群进行描述，然后给出一个示例。这里假设存在多个共享同一李代数的李群（Gilmore, 1974）。首先要找到的是与每个李群相关联的基本群。其中一个群 `G` 必须是单的，因此同伦 `π1 = {I}`。如果一个李群的多个基本群都是单的，则相应的李群同构。接下来，找到李群 `G` 的离散不变子群 `D1`、`D2`、…、`DN`，也称为正规子群。`G` 是李代数 `A` 的通用覆盖群。`G` 的离散不变子群 `D` 是不变的；因此，`gD = Dg`。对于 `G` 中的所有 `g`，可写为 `g D g^(-1) = D`。此外，它们是离散的，即通常是有限的或可数无限的，没有聚点。接下来将看到，`D` 由于是离散的，加强了交换性。

李群 `G` 总是与 `D` 的每个元素 `d′` 和 `d″` 交换。这种交换性是通过在 `g d′ g^(-1) = d″` 中连续地将 `g` 移动到单位元得到的。因为 `D` 是一个离散群，这意味着 `d′ = d″`，因为 `d′` 和 `d″` 不能连续地不同；它们只能相差 delta 量。这是具有离散元素的直接结果。群 `D` 是 `G` 的中心；它是 `G` 的最大离散不变子群。所有其他离散不变子群 `Dj` 本身都是 `D` 的子群。最重要的是，该族中的所有其他李群都与 `G/D` 同构。不同的离散不变子群的数量决定了对应于单一李代数的一个族中不同的李群的数量。这里，当 `Di` 和 `Dj` 同构但不同时，每个可能对应族中的一个不同群。此外，该族中每个群 `G/Di` 都有一个基本拓扑群 `π1`，它与相应的代数离散不变群 `Di` 同构。这种关系在李群中提供了代数结构与拓扑结构之间的强联系。离散不变群 `Di` 是代数的，但基本群 `π1` 由于同伦而是一个群，这是拓扑性质；尽管如此，这些结构之间的同构控制着通用覆盖群的后果。

下一个示例将涉及三个李群的族，它们都具有相同的李代数 `h = su(2, C)`。这三个李群彼此局部相似，但并不相同。

### 示例 12.10

这可能是李群覆盖空间的最简单实例。它涉及三个不同的李群，如 图 12.11 所示。这三个群接下来给出。它们首先是特殊正交旋转李群 `SO(3)`。接下来是 `SLC(1, Q)`，它是四元数一维的特殊线性群。最后一个李群是特殊么正群 `SU(2)`。它们都具有共同的李代数 `su(2)`，尽管分别涉及三乘三矩阵、四元数标量，最后是二乘二矩阵。李群 `SU(2)` 是 `SO(3)` 通过 `Z2` 的扩张。所有这些群在线性化后给出相同的李代数。也就是说，线性化给出相同的李括号和生成元。另一方面，现在反过来。不同的表示在指数化时为唯一的李代数 `su(2)` 提供了这些不同的李群。

![图 12.11 通用覆盖群.](img/F000254f12-11-9780443136979.jpg)

图 12.11 通用覆盖群。

由于 `SU(2, C)` 的基本群是单的，即它只由等价类 `[I]` 组成。即 `π1) = [I]`。由此可知 `SU(2, C)` 是通用覆盖群。接下来，必须确定 `SU(2, C)` 的离散不变子群。注意到 `SU(2, C)` 的中心是 `D = {I, -I}`。它是 `SU(2, C)` 的最大子群，与 `SU(2, C)` 的所有元素交换。该子群可通过利用示例 11.26 中 `SU(2, C)` 的一般矩阵结构中的坐标找到。令所有项为零，除非首先令 `d = 2*π*` 然后使用 `d = 0`。唯一的另一个离散不变子群是 `{I}`。注意 `D` 与 `π1)` 同构。`SU(2, C)` 对 `{I, -I}` 的因子群与 `SO(3, R)` 同构。`SLC(1,Q)` 对 `{I}` 的因子群是它本身。此外，由于离散不变子群是 `{I}`，特殊四元数群 `SLC(1, Q)` 与特殊么正群 `SU(2, C)` 同构且同胚。

商空间 `SU(2, C) / {I, -I}` 由不可数多个元素组成，例如 `SU(2, C)` 中的 `a`、`b` 分区为陪集。所有陪集的集合形式为 `{I, -I}`、`{a, -a}` 和 `{b, -b}`，形成不可数多个，从而得到一个新的群。陪集的乘法 `[a] x [b] = [a x′ b]`，其中 `x′` 是 `SU(2, C)` 中的乘法，`x` 是 `SO(3, R)` 中的诱导乘法。`SU(2, C)` 是通过基本群 `Z2` 对 `SO(3, R)` 的扩张。

## 12.7 Cornwell 映射

从 `SU(2, C)` 到 `SO(3, R)` 的二对一同态映射 `T` 也被称为 Cornwell 映射（Cornwell, 1997）。

### 示例 12.11

对于下面给出的 `2x2` 矩阵 `U`，其中 `z`、`w` 在 `C` 中且 `|z|² + |w|² = 1`，

$\\begin{array}{ll} {|z} & {w|} \\\\ {|{- w \\ast}} & {{{z \\ast}|}.} \\\\ \\end{array}$

![方程](img/F000254si4.png)

这是在 `SU(2, C)` 中的典型矩阵。当用泡利矩阵表示时，它也称为低维旋量表示。`U` 的像由 `T(U)` 给出，即：

$\\begin{array}{lll} {|{{Re}\\left( {z^{2} - w^{2}} \\right)}} & {\\text{Im}\\left( {z^{2} - w^{2}} \\right)} & {{- 2{Re}\\left( {zw} \\right)}|} \\\\ {|{\\text{Im}\\left( {z^{2} - w^{2}} \\right)}} & {{Re}\\left( {z^{2} + w^{2}} \\right)} & {{\\mspace{20mu} 2\\text{Im}\\left( {zw} \\right)}|} \\\\ {|{2{Re}\\left( {\\text{zw} \\ast} \\right)}} & {2\\text{Im}\\left( {\\text{zw} \\ast} \\right)} & {{{|z|}^{2} - {|w|}^{2}}|} \\\\ \\end{array}$

![方程](img/F000254si5.png)

`T(U)` 在 `SO(3, R)` 中。

有趣的是，在上述示例中 `SO(3,R)` 中 `T(U)` 的表示被用于证明特殊正交群的 Solovay-Kitaev 定理的一个版本。该定理的 `SU(2,C)` 版本在即将到来的量子计算章节中进行了描述。

## 参考文献

* Cornwell, 1997 Cornwell J. *物理学中的群论：导论* Academic Press 1997;.
* Gilmore, 1974 Gilmore R. *李群、李代数及其某些应用* Courier corp 1974;.
* Hatcher, 2002 Hatcher A. *代数拓扑* Cambridge U. Press 2002;.
* Humphreys, 1972 Humphreys J. *李代数与表示论导论* Springer Verlag 1972;.



* Humphreys, 1997 Humphreys J. 978–3540900535 *李代数与表示论导论*. vol 9 2nd ed. Springer 1997;.
* Strom, 2011 Strom, J., 2011. 现代经典同伦论, vol 127. American Mathematical Society.
* Whitehead, 1978 Whitehead. GTM *同伦论基础*. Vol. 61 Springer-Verlag 1978;.

# 第 3 章

## 量子与神经网络机制的基础代数

### 摘要
本章首先描述向量空间如何成为代数。使用 MSA 方法论描述了若干不同的代数。提供了幺半代数以及结合代数和非结合代数的例子。在量子技术和深度学习学科中，底层代数结构不仅仅是向量空间或域。它非常经常是一个代数。特别地，引入了时限信号的代数。提供了大量例子以及有界向量表示。随后介绍了代数中的交换子，并再次提供了例子。第 3.4 节描述并说明了环绕数字信号的希尔伯特空间。该节随后是巴拿赫空间、巴拿赫代数以及 `C*` 代数的 MSA。所有这些代数都附有例子。

#### 关键词
幺半代数；交换子；赋范向量空间；巴拿赫空间；巴拿赫代数；伴随运算；`C*` 代数；环绕信号

## 3.1 从向量空间到代数
在 MSA 中引用任意向量和希尔伯特空间表示将允许以高层或全局视角描述这些结构的推广。首先，配备双线性运算的向量空间在满足若干等式恒等式时称为代数（Gratzer, 1969）。双线性运算通常定义为将两个向量相乘得到另一个向量。这种乘法可以根据被操作对象的载体集采取多种形式。载体集可能导致涉及函数空间中逐点类型乘法的签名集。它可以是算子的复合，即函数的函数。它可以是同伦中由路径组成的等价集的连接。此外，它可以是卷积或通常所称的群乘法。最后一种乘法是卷积神经网络（CNN）中采用的主要运算。与乘法类型无关，MSA 全局视图丰富了所有这些表示。

更精确地说，描述代数的类型包括 `VECTOR` 和 `SCALAR`，如同向量空间结构。在这种情况下，向量空间和域结构的所有相应签名集必须成立。然而，还包括一个额外的运算符名称。它是一个二元运算名称，并且完全涉及类型 `VECTOR`。该元素命名为 `BINE`，表示它是一个二元运算，并且满足如下条件。

`BINE` 映射 `VECTOR` x `VECTOR`→`VECTOR`；通常，相乘的运算元的顺序无关紧要。两个运算元在相乘时可以位于左侧或右侧。

当 `BINE` 包含在向量空间结构的签名集中时，代数的算子序列为 (1, 1, 3 (2, 1))。这里，排除内积后又有三个二元运算。其中三个运算中的两个属于同一个签名集，其算子名称的元数为二；它们是 `V-ADD` 和 `BINE`。另一个二元运算名称在它自己的签名集中；它是 `S-MULT`。有一个单一的一元运算符名称 `V-MINUS`，和一个单一的零元名称 `V-ZERO`。

在代数中，除向量空间和域结构外，还必须满足三个额外的约束方程。这些约束如下给出。为了更简洁地描述这些约束，记为：
* `SCALAR` 为：`a`, `b`
* `VECTOR` 为：`u`, `v`, `w`
* `V-ADD` 为 `+`
* `S-MULT` 为 `×`
* `BINE` 为 `·`

代数的等式恒等式如下：
1. 分配律：`(u + v)·w = u·w + v·w`。
2. 分配律：`w·(u + v) = w·u + w·v`。
3. 乘性齐次性：`a b × (u·v) = (a × u)·(b × v)`。
当满足额外约束 (4) 时，代数称为结合的：
4. 结合律：`((u·v)·w) = (u·(v·w))`。
此外，当与 `V-ZERO` 一起存在 `V-ONE` 时，代数称为幺半的，两者都属于 `VECTOR` 的零元签名集。而且，这些元素必须彼此不同，如多项式图中的单独箭头所示（图 3.1）。因此，幺半代数的算子序列为 (2, 1, 3 (2, 1))。这里，等式恒等式 (1)、(2)、(3) 和下面给出的 (5) 必须成立。为了方便，将 `V-ONE` 替换为 `I`，
5. `V-ONE` 律：`I·v = v·I = v`。
具有幺半元素的结合代数是满足上述所有恒等式的幺半结合代数。此外，当 (6) 成立时，代数也称为可交换或阿贝尔的。
6. 交换律：`v·w = w·v`。

![图 3.1 幺半代数的多项式图。](img/F000175f03-01-9780443136979.jpg)

图 3.1 幺半代数的多项式图。

当所有等式恒等式都成立时，幺半代数称为结合可交换幺半代数。所有非零元素都可逆的幺半结合代数称为除法代数。再次，幺半代数的多项式图在 图 3.1 中给出。在该图中，未显示仅涉及 `SCALAR` 的多类型多项式箭头。此外，如同向量空间或 R-模，`VECTOR` 与 `SCALAR` 之间的唯一联系或连接是通过 `S-MULT`。而且，`S-MULT` 运算应使用标量和向量以任意顺序使用。因此，该运算在某种程度上是可交换的，结果必须相同。

#### Example 3.1
设类型 `VECTOR` 的载体集为所有复值整函数的集合。整函数的许多等价刻画之一是它们具有无限收敛半径的幂级数表示。使用通常的逐点复加法和乘法提供了一个幺半可交换结合代数的例子。该代数对于全纯泛函演算的发展很重要，后者在后面的章节中提到的谱理论中有用。

整函数在处处解析，因此它们的和与积也是如此。一般而言，对于非零标量，它们的倒数是整的。幺半元素 `V-ONE` 是数 1。该代数包含所有多项式、`sin(z)`、`cos(z)`，以及双曲正弦和余弦，以及它们的和与积。例如，不包含在 `C` 中有极点的有理函数、在 `C` 原点有分支点的 `z^(1/2)`、在 `C` 中有本性奇点的 `exp(1/z)`，最后任何使用共轭 `z*` 的函数。然而，仅具有可去奇点的函数属于该幺半可交换代数。例如，`sin(z)/z` 在 0 处有奇点，可以去掉。

#### Example 3.2



考虑 `VECTOR` 类型的载体集合如下：所有 2×2 复值矩阵的集合 `M`，`M` 中的 `A` 和 `B`。通过使用通常的矩阵加法、复数标量乘法及相关规则得到向量空间结构。全零矩阵=`V-ZERO`。如果对 `BINE` 采用通常的矩阵乘法，则 `BINE(A, B)=C` 的结果是 `M` 中的另一个矩阵。`V-ONE` 是单位矩阵。所有幺半结合代数的等式恒等式 (1)–(5) 都成立。它不是交换代数。如果 `S` 是 `M` 中所有标量矩阵的子集，即主对角线外全为零的矩阵，则 `S` 是一个幺半交换结合代数。

### 例 3.3
再次考虑 `VECTOR` 类型的载体集合如下：所有 2×2 复值矩阵的集合 `M`。如前所述，使用通常的矩阵加法、复数标量乘法及相关规则得到向量空间结构。全零矩阵=`V-ZERO`。现在不采用通常的乘法，即两个矩阵 `C` 和 `D` 的通常乘积 `C·D`，令 `BINE(C, D)=(C·D + D·C)/2`。这与后面章节中描述的泊松括号类似。事实上，这种乘法是 第 19.2 节 中概述的约当代数的核心。在这种情况下，使用 `BINE` 的乘法可能被称为约当括号。

幺半代数图中多元箭头所说明的所有闭包条件都将被证明成立。乘法是封闭的，因为它是两个通常乘法的缩放和。单位元 `V-ONE` 是 `I`。然而，要证明这是一个代数，必须证明这种类型的乘法满足代数定义中的恒等式 (1)、(2) 和 (3)。这些限制接下来将被证明：

1. 1) 分配律：
注意 `BINE((E + F), G)=((E + F)·G + G·(E + F))/2=((E·G + F·G + G·E + G·F))/2=(E·G + G·E)/2 + (F·G + G·F)/2=BINE(E, G) + BINE(F, G)`。

2. 2) 分配律：类似成立

3. 3) 乘性齐次性：
`BINE(a × E, b × F)=(a × E·b × F + b × F·a × E)/2=ab × BINE(E, F)` 成立。

因此该结构是一个代数。

* 6) 交换律：
它也是交换的，因为 `BINE(E, F)=BINE(F, E)` 成立。
此外，它是幺半的，因为如果 `I` 是 2×2 单位矩阵，那么它也是代数的单位元，即满足等式约束 (5)，因为：

* 5) V-ONE 律：
`I·v=v·I=v`，且 `BINE(I, E)=(I·E + E. ·I)/2=BINE(E, I)=(E·I + I·E)/2=E`。
然而，如下所示，结合律不成立。采用这种乘法并忽略向量空间时，乘法结构只是一个半群 oid 而不是半群，

* 4) 结合律：
首先考虑 `BINE(BINE(E, F), G)=BINE((E·F + F·E)/2, G)=(E·F·G + F·E·G + G·E·F + G·F·E)/4`。其次考虑 `BINE(E, BINE(F, G))=BINE(E, (F · G + G·F)/2)=E·F·G + E·G·F + F·G·E + G·F·E)/4`。实际情况是第一个和第二个等式不一致。因此，整体结构是一个幺半、交换、非结合代数。

如前所述，最后一个例子将在关于约当代数和再生核希尔伯特空间的讨论中再次提及，见 第 19.2 节。

## 3.2 有限时信号的代数
如第 1.9 节所述，有限时信号 `A` 的内积空间将被证明构成一个代数。对于 `A` 中的 `f` 和 `g`，逐点卷积定义为 `${BINE}\\left( {f,g} \\right)\\left( n \\right) = \\left( {f \\star g} \\right)\\left( n \\right) = \\sum\_{k = - \\infty}^{\\infty}{f\\left( {n - k} \\right)g\\left( k \\right)} = \\sum\_{k = - \\infty}^{\\infty}{g\\left( {n - k} \\right)f\\left( k \\right)}$`![方程](img/F000175si1.png)。采用这种类型的乘法 `BINE`，向量空间 `A` 成为一个幺半、交换、结合代数。单位元函数是 `I=(1)[0]`，且 `I` ⋆ `f` = `f` ⋆ `I` = `f`![方程](img/F000175si2.png)。尽管前面提到的求和的极限是无限的，但非零项只有有限个。接下来将描述实际求和极限的更简洁表达式。

回顾，对于 `A` 中的任意 `f`，非零集定义为 `f` 不为零的 `Z` 中所有点的集合。该集合非常重要，因为 `COZ(f ⋆ g)` 是两个集合 `COZ(f)` 和 `COZ(g)` 的扩张的子集（Giardina, 1985）。扩张由 `D(COZ(f), COZ(g))=the union of all sets of integers {n+k}, where n is in COZ(f) and k is in COZ(g)` 给出。`f` 和 `g` 的卷积在此扩张集合之外为零。因此，卷积可使用以下公式计算：

`$\left( {f \star g} \right)\left( n \right) = {\sum\limits_{k \in COZ{(f)},{({n - k})}k \in COZ{(g)}}{f\left( k \right)g\left( {n - k} \right)}}$`

![方程](img/F000175si4.png)

一个例子将说明该逐点公式的使用。

### 例 3.4
考虑 `A` 中由有界向量给出的两个信号 `f` 和 `g`：`f=(3 2 1)[0]`，且 `g=(2–1)[0]`。则 `COZ(f)={0, 1, 2}` 且 `COZ(g)={0, 1}`。取这些集合中所有可能和的并集并去掉重复项得到扩张集：`{0, 1, 2, 3}`。`f` 和 `g` 的卷积在此扩张集之外为零。确实，`f ⋆ g=(6 1 0–1)[0]`，且在 `{0, 1, 2, 3}` 之外为零。接下来给出 `(f ⋆ g)(2)=0` 的快速检验。为验证这一点，首先注意到 `n=2` 在扩张集中。接下来，找到 `COZ(f)` 中的 `k`，使得 `n-k=2 - k` 在 `COZ(g)` 中。这发生在 `k=2` 和 `k=1` 时。将这些数值代入逐点卷积公式：`(f ⋆ g)(2)=f(2) g(0) + f(1) g(1)=1·2 + 2·(−1)=0`。

卷积可使用 图 3.2 所示的并行算法更易确定（Giardina, 1988）。该算法利用了第 1.7 节所述 MSA 中提及的两个运算，并在 图 1.2 的多元图中示出。这些运算是 `V-ADD` 和 `S-MULT`。然而，在此应用中，算子的参数是有界向量。它们不是逐点运算。该图中指定的另一个运算是 `TRAN`，它类似于仿射型运算。运算 `TRAN(f; k)` 将（整个）有界向量平移 `k` 个单位。它当 `k> 0` 时向右平移，当 `k<0` 时向左平移，当 `k=0` 时不平移。因此，对于 `f=(a[0], a[1], … a[m])[n]`，有 `TRAN(f; k)=(a[0], a[1], … a[m])[n+k]`。因此，使用此运算时，有界向量内的值保持不变，但向量被平移到 `k` 个单位。从另一个角度看，下标中的点 `n` 通过使用 `COZ(g)` 的元素对 `f` 进行加法群作用而变为点 `n + k`。

![图 3.2 并行卷积算法。](img/F000175f03-02-9780443136979.jpg)

图 3.2 并行卷积算法。

暂时地，在 图 3.2 中，将 `g` 的非零集视为栈 `coz(g)` 很方便。同时，将数据结构 `ran(g)` 视为栈，其值按顺序对应于 `coz(g)` 中的那些整数。因此 `ran(g)` 类似于 `g` 的非零值域。由于这种安排，当栈同步弹出时，函数 `g` 就会显现。以例 3.5 作为说明。

### 例 3.5
设 `A` 中的两个信号 `f` 和 `g` 由有界向量给出：`f=(3 2 1)[0]`，且 `g=(2–1)[0]`。目标是求卷积 `h`。在这种情况下，`coz(g)` 和 `ran(g)` 分别以栈的形式示出：



$\\begin{array}{l} {\\begin{array}{l} {| 0|} \\\\ {| 1|} \\\\ \\end{array}\\begin{array}{l} {| 2|} \\\\ {| - 1|} \\\\ \\end{array}} \\\\ {- - - - - -} \\\\ \\end{array}$

![Equation](img/F000175si8.png)

当这些栈被弹出时，`ran(g)` 中的值提供了在 `S-MULT` 中使用的标量值。同时，弹出 `coz(g)` 指定了 `f` 将被平移的单位数；这是前面提到的群作用。算法的一个应用首先给出一个乘以二的标量乘法以及零平移。接下来，其后跟随一个乘以负一的标量乘法和平移一。以向量加法 `V-ADD` 收尾，给出 `h=V-ADD(2 f, − (3 2 1)[1])=(6 4 2 0)[0] + (0–3 −2–1)[0]=(6 1 0–1)[0]`。

与标准卷积类似，扩张卷积可以在 `CNNs` 中使用。卷积可以逐点创建，也可以在并行中创建。再次，图 3.2 中描述的算法可以经过少量修改来执行扩张卷积。在这种类型的卷积中，一个称为滤波器的信号 `g` 被扩张，而另一个数据信号 `f` 则按原样使用。所有这些意味着零被填充或放置在 `g` 内的条目之间，从而产生另一个有界向量 `g’`。零的数量通常是一个小的正整数 `r`。这种情况下的逐点卷积是 `(f ⊛ g’)(n)=∑ f(k)g’(n−k)`。与往常一样，求和应针对 `k` 在 `COZ(f)` 中且 `n-k` 在 `COZ(g’)` 中。具体来说，对于原始有界向量，`g=(g(k) g(k+1) … g(k+p))[j]`；有界向量 `g’=(g(k) 0 .. 0 g(k+1) 0 … 0 g(k+p))[j]` 在卷积公式中使用。一个示例应使这一点更清晰。

### 示例 3.6

设 `f=(2 1 0–1)[0]` 且 `g=(2–1)[0]`；然后使用 `r=1`；也就是说，将在 `g` 的值之间插入一个零，从下标整数开始。在这种情况下，`g’=(2 0–1)[0]`，卷积结果为 `(f ⊛ g’)=(4 2–2 −3 0 1)[0]`。为了在单个点验证，例如 `n=3` 使用逐点卷积，在点 `n=3` 处 ⊛ 并得到 `(f ⊛ g’)(3)=−3`。要看到这一点，使用 `k` 在 `COZ(f)` 中且 `3-k` 在 `COZ(g’)` 中。这对 `k=1` 和 `k=3` 成立。因此 `(f ⊛ g’)(3)=f(1)g’(2) + f(3)g’(0)= −1–2=−3`。此外，并行算法也可以像以前一样应用。这次，使用集合 `COZ(g’)` 和 `RAN(g’)` 代替栈，这些有序集合分别为 `(0, 2)` 和 `(2, −1)`。按指定顺序使用这些集合中的元素给出 `f ⊛ g’=V-ADD [2 f, −1(2 1 0–1)[2]]=(4 2 0 –2 0 0)[0] + (0 0 –2 −1 0 1)[0]=(4 2–2 −3 0 1)[0]`。

在 `CNNs` 中经常使用的步幅型卷积中，数据信号 `f` 和滤波信号 `g` 都被扩张。这意味着通常固定数量 `r=1, 2, or 3` 的零被放置在 `f` 和 `g` 的条目之间。对两者使用相同的值 `r`，从而产生新的有界向量 `f’` 和 `g’`。然后 `f’` 和 `g’` 的卷积如前所述进行。

## 3.3 代数中的交换子

代数在量子力学中已被研究很长时间，特别是关于对易规则。(McCoy, 1929)。对于非交换代数 `A` 的子集 `B`，交换子 `Bc` 的概念是有用的。它被定义为与 `B` 的每个元素都对易的 `A` 的子集。子集 `Bc={a in A|a·b=b·a for all b in B}`。交换子的概念在下面的示例中得以说明。

### 示例 3.7

再次，考虑类型 `VECTOR` 的载体集为以下：所有 2 by 2 复值矩阵的集合 `A`。现在采用通常的矩阵加法标量乘法以及通常的矩阵乘法。可以看出该结构形成一个幺元结合代数，它不是交换的。为了说明交换子运算，使用 `A` 的子集 `B`，它由除第一行第二列位置外所有元素为零的 2 by 2 矩阵组成。也就是说，矩阵项 `b12` 是任意的。在这种情况下，交换子 `Bc` 是所有 2 by 2 矩阵的集合，使得 `a11=a22` 且 `a21=0`。此外，`a12` 是任意复数。`Bc` 中的典型矩阵是

$\\begin{array}{l} {|\\begin{array}{ll} c & a \\\\ \\end{array}|} \\\\ {{|\\begin{array}{ll} 0 & c \\\\ \\end{array}|}.} \\\\ \\end{array}$

![Equation](img/F000175si16.png)

在本例中更有趣的事实是 `Bc` 本身也是一个结合代数，具有恒等元，`a11=a22=1`，`a12=a21=0`；因此它是幺元的。而且，这次它是交换的。因此，如果 `C` 和 `D` 是 `Bc` 中的矩阵，则 `C·D=D·C`。交换子将在后面的章节中在 von Neumann 代数中再次出现。

交换子目前在希尔伯特空间碎片化和遍历性方面被 heavily 研究 (Moudgalya, 2022)。就目前而言，涉及代数的最后一个事实是，有时代数被定义为模块上的双线性映射，而不是向量空间上的。一个例子是 Grassmann 代数，也将在后面描述。

## 3.4 代数同态

代数同态涉及两个代数 `S` 和 `M`，可能在域上是幺元、结合或交换的，例如 `C`。同态是映射 `ϕ`![Equation](img/F000175si17.png)，其中 `ϕ`![Equation](img/F000175si18.png): `A→B` 且对于 `S` 中的任意 `A` 和 `D`，`M` 中的 `B`，以及 `C` 中的 `c`，以下条件成立：

1. 1) 加法性: `ϕ`![Equation](img/F000175si19.png) (`A` + `D`)=`ϕ`![Equation](img/F000175si20.png) (`A`) + `ϕ`![Equation](img/F000175si21.png) (`D`).

2. 2) 乘法性: `ϕ`![Equation](img/F000175si22.png) (`A` `D`)=`ϕ`![Equation](img/F000175si23.png) (`A`) `ϕ`![Equation](img/F000175si24.png) (`D`).

3. 3) 标量: `ϕ`![Equation](img/F000175si25.png) (`c` `A`)=`c` `ϕ`![Equation](img/F000175si26.png) (`A`).

4. 4) 恒等: `ϕ`![Equation](img/F000175si27.png) (`I[A]`)=`I[B]`, when there exist unital elements.

### 示例 3.8

再次考虑 `VECTOR` 的载体集为所有 2x2 复值矩阵，且对于 `SCALAR` 令载体集为 `C`。示例 3.2 说明了该结构 `M` 使用通常的矩阵运算是一个幺元结合代数。如果 `S` 是子代数 `M`，那么对于 `M` 中每个可逆矩阵 `B`，以及 `S` 中的 `A` 和 `D`，`ϕ`![Equation](img/F000175si28.png)(`A`)=`B^(−1)A B` 是一个幺元代数同态。这是因为：

1. 1) 加法性: `ϕ`![Equation](img/F000175si29.png) (`A` + `D`)=`B^(−1)(A + D) B`=`B^(−1)A B` + `B^(−1)D B`)=`ϕ`![Equation](img/F000175si30.png) (`A`) + `ϕ`![Equation](img/F000175si31.png) (`D`).

2. 2) 乘法性: `ϕ`![Equation](img/F000175si32.png) (`A` `D`)=`B^(−1)(A D) B`=`B^(−1)A B B^(−1)D B`=`ϕ`![Equation](img/F000175si33.png) (`A`) `ϕ`![Equation](img/F000175si34.png) (`D`).

3. 3) 标量: `ϕ`![Equation](img/F000175si35.png) (`c` `A`)=`B^(−1)c A B`=`c B^(−1)A B`=`c` `ϕ`![Equation](img/F000175si36.png) (`A`).

4. 4) 恒等: `ϕ`![Equation](img/F000175si37.png) (`I`)=`B^(−1)I B`=`B^(−1)B`=`I`.

当同态是一一且满的时，它被称为代数同构。

## 3.5 环绕数字信号的希尔伯特空间



不同类型的数字信号会产生载体集合，对于这些信号，相比于 `A` 中的那些信号，会应用更深层的结构。回想一下，`A` 由 `R^(*z*)` 中紧支撑的所有数字信号组成。现在，环绕数字信号将用环绕卷积来描述。该结构构成一个希尔伯特空间，以及一个结合的、交换的、含幺的代数。在这种情况下，类型 `SCALAR` 再次表示实数域。而 `VECTOR` 象征 `R^(*Zn*)` 中的有界向量 `f`，这里 `f`: `*Z**n*`![Equation](img/F000175si38.png)→`R`，其中 `*Z**n*`![Equation](img/F000175si39.png) 是由 {0, 1, 2, …, n-1} 组成的循环群，`n`> 1。可以认为这组整数位于一个圆上，因此 `n−1` 的后继是 0。0 的后继是 1，1 的后继是 2，等等。本文中循环群的最早实例见于示例 1.1。在这种情况下，伽罗瓦域中的加法群为模三。
在此环境中，有界向量始终写为 `f=(a b c … d)[*k*]^(*Wn*)`，其中 `a`、`b`、… `d` 是 `n` 个实数。因此，`V-ZERO=(0 0 … 0)[*k*]^(*Wn*)`。对于环绕有界向量，零向量始终以这种方式指定。此外，`*W**n*`![Equation](img/F000175si40.png) 表示该向量是 `R^(*Zn*)` 中的环绕有界向量，且 `k` 是 0 到 `n−1` 之间的整数。使用逐点加法，以及作为这些类型有界向量乘法的卷积，会得到一个含幺的、交换的和结合的代数结构。含幺有界向量 `V-ONE` 在 `R^(*Zn*)` 中为 `(1 0 … 0)[0]^(*Wn*)`。`R^(*Zn*)` 中有界向量的卷积基本上与先前对 `R^(*Z*)` 中有界向量描述的算法相同：与往常一样，与零向量的卷积产生零向量。因此，下面假设有界向量是非零的。
逐点卷积由下式给出：
$\\left( {f \\star g} \\right)\\left( n \\right) = {\\sum\\limits\_{k \\in COZ{(f)},{({n - k})} \\in COZ{(g)}}{f\\left( k \\right)g\\left( {n - k} \\right)}}$
![Equation](img/F000175si41.png)
环绕卷积是一种全卷积形式，其中 resulting 卷积与输入信号大小相同。先前描述的时限数字信号卷积可能称为扩展卷积。图 3.2 中所示的相同并行算法可以在 `R^(*Zn*)` 中使用。这里操作的名称相同，但由于载体集合不同，实际操作是不同的。接下来给出一个使之更清晰的例子。循环群使用 `TRAN` 对向量空间结构进行作用，就像向量在仿射空间中对仿射元素的作用一样。同样，由于 `MSA` 全局视图与 `R^(*Z*)` 中的相同，实际的低级操作是不同的。
### 示例 3.9
设 `f=(2–1 3 0 1)[0]^(*W*5)` 且 `g=(1–1 2 0 1)[0]^(*W*5)`。类似地，`COZ(g)={0, 1, 2, 4}` 且 `RAN(g)={1–1, 2, 1}`。并行卷积算法得到以下结果：`f ⋆`![Equation](img/F000175si42.png)` g=1· f – 1· (2–1 3 0 1)[1]^(*W*5) + 2·(2–1 3 0 1)[2]^(*W*5) 1· (2–1 3 0 1)[4]^(*W*5)`\=`f – (1 2–1 3 0)[0]^(*W*5) + 2 (0 1 2–1 3)[0]^(*W*5) + (−1 3 0 1 2)[0]^(*W*5)`\=`(0 2 8–4 9)[0]^(*W*5)`。现在，使用逐点公式验证 `(f ⋆`![Equation](img/F000175si43.png)` g)(3)= −4`。与之前一样，采用 `COZ(f)` 中的 `k` 值，同时 `3-k` 在 `COZ(g)` 中。这些值由 `k=1`、`k=2`，最后 `k=4` 给出。最后一个值适用是因为 `3–4=−1=4 modulo(5)`。也就是说，`R^(*Zn*)` 中的四号元组与负一号元组相同，如果存在这样的元组的话。因此，`(f ⋆`![Equation](img/F000175si44.png)` g)(3)=f(1)g(2) + f(2)g(1) + f(4)g(4)=(−1) × 2 + 3 × (−1) + 1 × 1=−4.#`
向量空间 `R^(*Zn*)` 也构成一个内积空间，同样使用非空零点集交集上的点积。否则为零。第 1.9 节提供了公理，且 图 1.3 说明了该结构的 `MSA` 表示的拟多项式图。`f=(a b c … d)[*k*]^(*Wn*)` 与 `g=(e h … m)[*k*]^(*Wn*)` 的内积，如常，显示所有 `n` 个条目时为=`a·e + b·h + … + d·m`。内积再次由 `<f, g>` 或 `<f|g>` 表示。如果使用复数域代替实数域，则在计算内积时值 `a`、`b`、…、`d` 需要取共轭。这是量子物理中使用的约定，并在第 1.8 节中说明。`R^(*Zn*)` 中的内积诱导出前面提到的二范数。该范数可由公式 `‖f ‖²\=<f|f>` 找到。在此范数下，`R^(*Zn*)` 是一个完备的内积空间，因此是希尔伯特空间；参见附录 A.1 证明。`R^(*Zn*)` 中有界向量序列的收敛与 `R^(*n*)` 中的收敛相似。
## 3.6 Banach 空间的多排序代数描述
Banach 空间是定义在复数或实数域上的带范数的向量空间。一些范数已经说明过。二范数由内积诱导，见第 1.8 节。此外，一范数在第 2.1 节示例 2.1 中的 k-means 无监督学习技术中使用。Banach 空间与希尔伯特空间相似，因为它对范数也是完备的。如常，范数是一种平移不变型距离函数。然而，与希尔伯特空间不同，可分性不足以保证 Schauder 基的存在 (Enflo, 1973)。因此，在无限维 Banach 空间中工作时将假设存在 Schauder 基。否则，如一般拓扑向量空间中，需要采用无条件基。接下来将给出 Banach 空间的 `MSA` 全局视图。
在 `MSA` 描述中，Banach 空间实体由两种类型组成，它们是 `SCALAR` 和 `VECTOR`。与 `SCALAR` 关联的所有签名集合与实数或复数域结构相同。`VECTOR` 类型的签名集合与向量空间完全相同，只是存在一个额外的 unary 操作名：`NORM`，在其自己的签名集合中。据此，Banach 空间的元数序列为 `(1, 2(1 1), 2(1 1))`。图 3.3 说明了 Banach 空间中使用的 `NORM` 操作名，以及签名集合中的常用向量空间操作名。仅与 `SCALAR` 关联的操作名被省略。`NORM` 满足：
`NORM:VECTOR→SCALAR`
![Equation](img/F000175si45.png)![Figure 3.3 Polyadic graph for a Banach space.](img/F000175f03-03-9780443136979.jpg)
图 3.3 Polyadic graph for a Banach space.
所说明的向量空间算子如下：
`V-ADD:VECTORxVECTOR→VECTOR`
![Equation](img/F000175si46.png)
`S-MULT:SCALARxVECTOR→VECTOR`
![Equation](img/F000175si47.png)
`V-MINUS:VECTOR→VECTOR`
![Equation](img/F000175si48.png)
`V-ZERO,0ElementinVECTOR`
![Equation](img/F000175si49.png)
如常，`S-MULT` 操作必须允许标量在乘法操作中位于向量的两侧。
`NORM` 必须满足三个条件。为此，首先替换：
* `SCALAR` 为 `a`
* `VECTOR` 为 `u`, `v`, `w`
* `S-MULT` 为 `·`
* `V-ADD` 为 `+`
* `NORM` 为 `‖‖`
`NORM` 需满足的条件如下：
1. 1) 正定性：`‖u‖> 0`，且 `‖u‖=0` 当且仅当 `u=0`。
2. 2) 齐次性：`‖a·u‖=| a|‖u‖=‖u·a‖`。
3. 3) 三角不等式：`‖u + v‖` 小于或等于 `‖ u ‖ + ‖ v ‖`。



Banach 空间 `B` 中的范数是连续的。由此可知，对于 `B` 中的 `T` 和 `T[*n*]`，如果 `T[*n*]`→`T`，则根据三角不等式，`| ‖T‖ − ‖T[*n*]‖ |` 小于或等于 `‖T − T[*n*]‖`。

有许多重要的 Banach 空间例子。它们包括定义在自然数上的序列空间，以及连续函数空间和算子空间。

### Example 3.10

考虑闭区间零到一上的连续函数空间：`B`=`C([0, 1])`，其中 `g` 的范数为 `‖g‖`=max|g|，x 在 `[0, 1]` 中。这是一致紧集上的所有连续函数的集合，在实数线上是一个闭且有界的集合。所有与 Banach 空间相关的公理都成立。例如，两个连续函数的和是连续的，标量积也是如此。给定的范数满足赋范向量空间的所有条件。因此，以 `f` 也在 `B` 中为例，可得：
* 3) 三角不等式：`‖f + g‖`=max |f + g| 小于或等于 max (|f| + |g|)，小于或等于 max |f| + max |g|= `‖f‖` + `‖g‖`。

## 3.7 作为多排序代数的 Banach 代数

Banach 代数是实数域或复数域上的幺元结合代数，同时也是 Banach 空间（Larsen, 1973）。该结构的元数序列为 (2, 2(1, 1), 3(2, 1))。由于它是幺元结合代数，它具有 `V-ONE` 和一个名为 `BINE` 的向量型乘法，（图 3.4）。然而，该运算不一定是可交换的。当它是可交换时，该代数称为交换 Banach 代数。

![图 3.4 Banach 代数中运算符名称的多元图。](img/F000175f03-04-9780443136979.jpg)

图 3.4 Banach 代数中运算符名称的多元图。

由于 Banach 代数也是 Banach 空间，它满足上面 Banach 空间的所有三个等式恒等式。此外，它还必须满足下面提到的第四个条件。该条件将 `NORM` 运算名称与二元运算名称 `BINE` 联系起来。后者是由 (·) 表示的向量乘法名称。约束条件在下面的方程 (4) 中给出。三角乘积不等式类型的约束使乘法成为连续运算。
* 4) 三角乘积不等式：`‖v·w‖` 小于或等于 `‖v‖` `‖w‖`。

如前所述，`BINE` 是 Banach 代数 `B` 中的连续运算。为了证明这一点，如果 `T[*n*]`→`T`，`S[*n*]`→`S`，并且 `T[*n*]`、`T`、`S[*n*]` 和 `S` 都在 `B` 中，则 `T[*n*] S[*n*]`→`T S`。这是因为 `‖T[*n*] S[*n*] − T S‖` 小于或等于 `‖(T[*n*] − T) S‖` + `‖T(S[*n*] − S) ‖`。由于 `S` 和 `T` 有界，则 `‖(T[*n*] − T) S‖` + `‖T(S[*n*] − S) ‖` 小于或等于 `‖(T[*n*] − T)‖` `‖ S‖`+`‖ T ‖` `‖(S[*n*] − S)‖`→0。

在 图 3.4 中给出了一个多元图，说明了 Banach 代数中运算符的名称。此图中未显示仅涉及类型 `SCALAR` 的运算符名称。

### Example 3.11

`VECTOR` 以及 `SCALAR` 的载体集合使用全体复数域。此向量空间在复数域上成为一个交换 Banach 代数，其 `NORM` (`z`)=`|z|`。通常，对于 `z`=`x` + i`y`，`|z|²`=x² + y²。

## 3.8 Banach\* 和 C\* 代数的多排序代数

Banach\* 代数是具有额外一元运算的实数域或复数域上的 Banach 代数。由此得到的元数序列为 (2, 3(2, 1), 3(2, 1))。额外的运算类似于共轭的对合。两次应用该一元函数会得到恒等式；它是自反的。此外，Banach\* 代数结构必须满足五个等式恒等式；这些在下面描述。

为了在 MSA 高层视图中描述 Banach\* 代数结构，首先存在两种类型；它们是 `SCALAR` 和 `VECTOR`。`SCALAR` 类型具有相应的载体集合，由复数域组成，所有运算都是复数域的运算。实数域也适用。`VECTOR` 类型的签名集合与 Banach 代数中的完全相同，只是有一个额外的 unary 运算名称：`ADJ`。这里，

`ADJ`: `VECTOR`→`VECTOR`.

![方程](img/F000175si50.png)

为了提供必须成立的等式恒等式，用符号替换类型并用暗示性字符表示运算符名称：
* `VECTOR` 用 `v`, `w` 表示
* `SCALAR` 用 `a` 表示
* `S-MULT` 用 × 表示
* `V-ADD` 用 + 表示
* `V-ONE` 用 `I` 表示
* `BINE` 用 · 表示
* `NORM` 用 ‖ ‖ 表示
* `ADJ` 用 * 表示

必须成立的五条定律如下：
1. 1) 对合性：`(v*)* = v`。
2. 2) 可加性：`(v + w)* = v* + w*`。
3. 3) 共轭线性：`(a × v)* = \overline{a} × v*`，这里，`\overline{a}` 表示 `a` 的共轭。
4. 4) 转置：`(v·w)* = w*·v*`。
5. 5) 等距性：`‖v*‖ = ‖v‖`。

Banach\* 代数中最重要的类型是 C\* 代数。它是 Banach\* 代数，同时还满足：
6. 6) C\* 恒等式：`‖v·v*‖ = ‖v‖²`。

图 3.5 使用多元图提供了 C\* 代数中运算的说明。此图中未显示仅涉及 `SCALAR` 的运算。

![图 3.5 Banach\* 或 C\* 代数中运算符的多元图。](img/F000175f03-05-9780443136979.jpg)

图 3.5 Banach\* 或 C\* 代数中运算符的多元图。

## 3.9 环绕数字信号的 Banach\* 代数

`R^(Zn)` 中的内积诱导出前面提到的二范数。在此范数下，`R^(Zn)` 是一个完备的内积空间，因此是希尔伯特空间。由于 `R^(Zn)` 是希尔伯特空间，它也是使用二范数的 Banach 空间。

此外，使用 `R^(Zn)` 中 `f` 的一范数，它也是一个 Banach 空间。而且，它是一个 Banach 代数，如 第 3.7 节 中使用 MSA 描述的那样。图 3.4 中给出的说明为该结构提供了一个多元图。Banach 代数结构是等式恒等式 #4 的结果，即 `R^(Zn)` 中卷积的三角乘积不等式成立。在这种情况下，`‖f ⋆ g‖[1] = Σ_n |(f ⋆ g)(n)| = Σ_n | Σ_k f(k)g(n-k) |` 小于或等于和：`Σ_n Σ_k |f(k)||g(n-k)| = Σ_k Σ_n |f(k)||g(n-k)| = Σ_k |f(k)| Σ_n |g(n-k)| = Σ_k |f(k)| ‖g‖[1] = ‖f‖[1] ‖g‖[1]`。一般来说，不等式成立。作为说明，使用一范数对前一个示例的结果，见 例 3.9 和 3.12：

### Example 3.12

设 `f`=(2–1 3 0 1)[0]^(W5) 且 `g`=(1–1 2 0 1)[0]^(W5)，`f ⋆ g`=(0 2 8–4 9)[0]^(W5)。现在说明 `‖f ⋆ g‖[1]` 小于或等于 `‖f‖[1]‖g‖[1]`。这是涉及 Banach 代数的三角乘积不等式。将上述卷积中条目的绝对值相加得到 `‖f ⋆ g‖[1]=23`；而 `‖f‖[1]=7` 且 `‖g‖[1]=5`，乘积 `‖f‖[1]‖g‖[1]` 为 35。

从前面提到的证明中请注意，只要有界向量 `f` 和 `g` 中的所有值都非负，三角乘积不等式中就会成立等号。

### Example 3.13



设 `f=(2 1 3 0 1)[0]^(*W*5)` 且 `g=(1 1 2 0 1)[0]^(*W*5)`，`f ⋆`![方程](img/F000175si66.png`) `g`=`V-ADD(f, g)`=`f + (1 2 1 3 0)[0]^(*W*5) + 2 (0 1 2 1 3)[0]^(*W*5) + (1 3 0 1 2)[0]^(*W*5)`=`(4 8 8 6 9)[0]^(*W*5)`。 这里，`‖f ⋆`![方程](img/F000175si67.png`) `g‖[1]`=`35`。 如前所述，`‖f‖[1]‖g‖[1]`=`35`。
最后，将对 Banach\* 代数和 C\* 代数进行应用，如 第 3.8 节 中所定义，以及 Banach\* 代数和 C\* 代数的多值图，这些图在 图 3.5 中给出。 空间 `R^(*Zn*)` 是一个 Banach\* 代数。 这是显然成立的，因为 图 3.5 中的一元运算符名称是 `ADJ`。 实数的伴随或共轭等于其本身。 然而，下一个例子表明 `R^(*Zn*)` 不是 C\* 代数；也就是说，方程 (6)，对于 C\* 恒等式：`‖v·v\*‖=‖v‖²`，不成立。 在这种情况下，`‖f ⋆`![方程](img/F000175si68.png`) `f\*‖[1]`=`‖f ⋆`![方程](img/F000175si69.png`) `f‖[1]` 不等于 `‖f‖[1]²`。
### 示例 3.14
考虑 `f=(1–1 1)[0]^(*W*3)` 在 `R^(*Z*3)` 中。 则 `f ⋆`![方程](img/F000175si70.png`) `f`=`f − (1 –1 1)[1]^(*W*3) + (1 –1 1)[2]^(*W*3)`=`f − (1 1 –1)[0]^(*W*3) + (−1 1 1)[0]^(*W*3)`=`(−1 –1 3)[0]^(*W*3)`。 因此 `‖f ⋆`![方程](img/F000175si71.png`) `f‖[1]`=`5`。 另一方面，`‖f‖[1]²`=`9`。 所以这个 Banach\* 代数不是 C\* 代数。
有趣的是，存在 `‖f ⋆`![方程](img/F000175si72.png`) `f‖[1]`=`‖f‖[1]²` 的情况，即使 `f` 不具有全部非负值。
### 示例 3.15
如果 `f=(−2 0 3 0–1)[0]^(*W*5)`，`f ⋆`![方程](img/F000175si73.png`) `f`=`−2 TRAN(f; 0) + 3 TRAN(f; 2) − 1 TRAN(f; 4)`=`(4 0–6 0 2)[0]^(*W*5) + (0–3 −6 0 9) [0]^(*W*5) + (0–3 0 1 2)[0]^(*W*5)`=`(4–6 −12 1 13)[0]^(*W*5)`。 所以 `‖f ⋆`![方程](img/F000175si74.png`) `f‖[1]`=`36`=`‖f‖[1]²`。
## 3.10 复值环绕数字信号
在提供量子应用之前，说明复数域结构的使用是很有启发性的。 在此方向上，考虑 `C^(*Zn*)`；这些是具有复数项的有界信号，它们也形成 Banach\* 代数，以及希尔伯特空间；证明见附录 A.1。 对于 Banach\* 和 C\* 代数，共轭运算在此实例中更为重要。 下一个例子说明了内积运算中的共轭运算。 函数的卷积也在其中找到，以及涉及共轭函数的卷积。 结果可以进行比较，以说明描述 Banach\* 代数所需的五个等式恒等式。
### 示例 3.16
考虑 `C^(*Zn*)` 中的两个有界向量 `f` 和 `g`，其中 `i=$\\sqrt{- 1}$`![方程](img/F000175si75.png`)，`f=(2 0 3i 2+i 0)[0]^(*W*5)`，且 `g=(2i 0 3+2i 0 i)[0]^(*W*5)`。 为了求 `f ⋆`![方程](img/F000175si76.png`) `g`，相同的并行算法再次可以使用。 确实，`f ⋆`![方程](img/F000175si77.png`) `g`=`g ⋆`![方程](img/F000175si78.png`) `f`=`2TRAN(g; 0) + 3i TRAN(g; 2) + (2 + i) TRAN(g; 3)`=`(4i 0 6+4i 0 2i)[0]^(*W*5) + (0–3 −6 0–6+9i)[0]^(*W*5) + (4+7i 0 –1+2i −2+4i 0)[0]^(*W*5)`=`(4+11i −3 –1+6i −2+4i −6+11i)[0]^(*W*5)`。 现在卷积 `f ⋆`![方程](img/F000175si79.png`) `g` 的共轭是 `(f ⋆`![方程](img/F000175si80.png`) `g)\*`=`(4–11i −3–1–6i −2–4i -6–11i)[0]^(*W*5)`。
接下来将确定 `f\*` 和 `g\*` 的卷积。 首先，`f\*`=`(2 0–3i 2−i 0)[0]^(*W*5)` 且 `g\*`=`(−2i 0 3–2i 0 −i)[0]^(*W*5)`；然后，`f\*⋆`![方程](img/F000175si81.png`) `g\*`=`−2j TRAN(f\*;0) + (3–2i) TRAN(f\*;2) - i TRAN(f\*;4)`=`( −4i 0–6 −2–4i 0)[0]^(*W*5)+(4–7i 0 6–4i 0–6–9i)[0]^(*W*5) + (0–3 −1–2i 0–2i)[0]^(*W*5)`=`(4–11i −3–1–6i −2–4i -6–11i)[0]^(*W*5)`。 所以，`(f ⋆`![方程](img/F000175si82.png`) `g)\*`=`f\*⋆`![方程](img/F000175si83.png`) `g\*`，这说明了 Banach\* 代数中的性质 #4。
接下来将求出复希尔伯特空间的内积，以及其他范数计算。 首先可知 `<f, g>`=`<(2 0 3i 2+i 0)[0]^(*W*5), (2i 0 3+2i 0 i)[0]^(*W*5)>`=`4i + (−3i) (3+2i)`=`4i −9i + 6`=`6–5i`。 最后，`f ⋆`![方程](img/F000175si84.png`) `f\*`=`2 f − 3i (2+i 0 2 0 3i)[0]^(*W*5) + (2−i) (3i 2+i 0 2 0)[0]^(*W*5)`=`(4 0 6i 4+2i 0)[0]^(*W*5) + (3–6i 0–6i 0 9)[0]^(*W*5)`\+ `(3+6i 5 0 4–2i 0)[0]^(*W*5)`=`(10 5 0 8 9)[0]^(*W*5)`。 所以，`‖f ⋆`![方程](img/F000175si85.png`) `f\*‖[1]`=`32` 且 `‖f‖[1]²`=`(5 + 5^(1/2))²`。 这说明了 Banach 代数的三角乘积不等式性质编号 (4) 成立。 它还表明 C\* 代数性质编号 (6) 不成立。
在 `C^(*Zn*)` 中，Banach 代数的三角乘积不等式一般成立，如前所述。 此外，Banach\* 代数的转置性质一般成立。 这是性质编号 (4)，第 3.7 节，相应地：`(f ⋆`![方程](img/F000175si86.png`) `g)\*`=`$\\sum\\limits\_{n}$`![方程(f ⋆`![方程](img/F000175si88.png`) `g)(n)`]`\*`=`$\\sum\\limits\_{n}$`![方程(g ⋆`![方程](img/F000175si90.png`) `f)(n)`]`\*`=`$\\sum\\limits\_{n}$`![方程](img/F000175si91.png`)(g\*⋆`![方程](img/F000175si92.png`) `f\*)(n)`=`g\*⋆`![方程](img/F000175si93.png`) `f\*`。 作为结果，`C^(*Zn*)` 是一个 Banach\* 代数，但不是 C\* 代数。
## 参考文献
* Enflo, 1973 Enflo P. Banach 空间逼近问题的反例。 *Acta Math.* 1973;130.
* Giardina, 1988 Giardina, C., 1988. 多维信号处理的并行算法，第 22 届 Asilomar 会议论文集。
* Giardina, 1985 Giardina CR. 基于多态代数的信号处理数据流语言。 *Int Conf Math Model., 5th* 1985;.
* Gratzer, 1969 Gratzer G. *通用代数* N.Y.: Van Nostrand Reinhold; 1969;
* McCoy, 1929 McCoy N. 关于量子力学代数中的交换规则，爱荷华大学。 *PNAS*. 1929;15(3):200–202.
* Moudgalya, 2022 Moudgalya S. *Hilbert 空间碎片化与交换子代数* Benasque: California Institute of Technology; 2022;.
第 4 章
# 量子希尔伯特空间及其构造
## 摘要
在下面的各节中，提供了创建特定希尔伯特空间的众多示例和方法。 这些包括复化、对偶空间、外积以及张量积。 这些结构使用多态代数 MSA 描述，并特别用多值图进行说明。 这些图指定了涉及运算名称的闭包性质。 还提供了大量示例以强化概念。 稍后将引入多线性形式和内积。 还给出了张量向量空间的 MSA 描述，以及张量代数的 MSA。 这在第 4.10 节之后接着给出了希尔伯特空间张量积的 MSA。 此外，在修正的希尔伯特空间中引入了若干状态和射线的定义。 本章以射影空间的描述以及反幺正算子的简要描述结束。
### 关键词
复化；外积；对偶空间；双对偶空间；多线性形式；交替形式；张量积；张量空间；射影空间
## 4.1 支撑量子技术的显式希尔伯特空间



在上一章中，数字信号和环绕数字信号分别被表述为内积空间和希尔伯特空间。量子基本公理在定义底层希尔伯特空间的类型时是模糊的。再次在更低的层次上，应做出相对于全局希尔伯特空间结构的精确规范。这里提供了实际元素；具体来说，给出了两种类型的载体集合，一种对应于 `SCALAR`，另一种对应于 `VECTOR`。实际运算本身将按照签名集合中的运算名称进行指定。

## 4.1

### Example 4.1

这或许是希尔伯特空间最简单的例子。这里，实数构成一个在实数域 `R` 上的向量空间 `V`。这一事实在示例 2.13 中已提及，说明了向量对仿射空间中元素的影响。`SCALAR` 的载体集合和 `VECTOR` 的载体集合都由实线上的元素组成。实数在涉及实数的通常运算和函数中扮演双重角色。所有公理都适用于内积空间，也适用于希尔伯特空间。该空间仅为单维。请注意，`IN-PROD` 只是任意两个向量的乘积，而在这种情况下它们是两个标量。希尔伯特空间方程约束 (9) 成立。参见第 1.8 节：

1. 9) 正定：`v·v` 大于或等于 0，且 =0 当且仅当 `v=0`。

接下来提供另一个具体例子。

### Example 4.2

这个例子与前一个例子非常相似。事实上，复数系统构成了在复数域 `C` 上的向量空间。由此可知，在这种情况下两种类型都是复数。同样两个载体集合相同；这次它们是复数。另见示例 1.7。该结构也为 Fock 空间形成一个非常重要的希尔伯特空间。它描述了真空空间。Fock 空间将在后面的章节中以多类代数 (`MSA`) 描述呈现。同样，注意 `v` 与 `w` 的 `IN-PROD` 产生通常的复数乘积，涉及第一个条目的共轭与第二个的内积：`<v|w> = v*·w`。内积空间的所有约束方程都成立；例如，编号 (9) 再次参见第 1.8 节：

1. 9) 正定：`v*·v` 大于或等于 0 且 =0 当且仅当 `v=0`。

另请注意，`v = (a + i b)` 的范数平方再次由乘积给出：`v*·v = (a − i b)(a + i b) = a² + b² = ‖v‖²`。

## 4.2 Complexification

创建希尔伯特空间的下一个方法涉及希尔伯特空间的复化，（Halmos, 1958）。对于在实数域上的希尔伯特空间 `Hr`，该过程得到用 `Hc` 表示的复希尔伯特空间。它的维数与 `Hr` 相同，但它是在复数域上。在这种情况下，向量的实数标量乘法被扩展为复数标量乘法。在执行复化的众多方法中，采用了张量积方法。该方法接下来描述。后面的章节在考虑流形上的量子化时将利用纤维切空间的复化。

在 `MSA` 全局视图中，必须给出与希尔伯特空间结构和域结构中已提及的类似的类型。这些类型建议性地定义为 `C-SCALAR`、`R-VECTOR` 和 `C-VECTOR`。复数域用 `C-SCALAR` 表示。实数标量域在复化中存在，但不再提及。实数上的希尔伯特空间由 `R-VECTOR` 给出。类似地，得到的复值希尔伯特空间是 `C-VECTOR`。确切地说，对于两种希尔伯特空间规范都采用相同类型的签名集合和相应的运算名称；再次参见第 1.8 节。然而，对于复化，存在一个额外的签名集合，其中包含一个二元元素。它包含二元运算符名称 `TENSOR`。在这种情况下：

`TENSOR maps C-SCALAR x R-VECTOR -> C-VECTOR`.

![方程](img/F000011si1.png)

关于张量的更多细节将在后续章节中给出，但就目前而言，这足以说明复化运算。对于 `C-SCALAR`，相应的载体集合将始终由复数域 `C` 组成。此外，名为 `TENSOR` 的实际运算将用 `⊗` 表示，且满足 `Hc = C ⊗ Hr`。此外，`V-ADD` 和 `S-MULT` 对应的运算以显而易见的方式定义如下。

对于 `R` 中的任意 `a` 和 `b` 以及 `Hr` 中的 `u`、`v`、`w` 和 `z`，有：

For `V-ADD`: `(u + i v) + (w + i z) = (u + w) + i (v + z)`.

![方程](img/F000011si4.png)

For `S-MULT`: `(a + i b) ⋅ (u + i v) = (a ⋅ u − b ⋅ v) + i (a ⋅ v + b ⋅ u)`.

![方程](img/F000011si5.png)

此外，`Hc` 中的每个向量 `(u + i v)` 实际上是 `1 ⊗ u + i ⊗ v` 的简写。

内积的复化源于显而易见的展开：

`IN-PROD`: `<u + i v | w + i z> = <u | w> + <v | z> + i (<u | z> − <v | w>)`

![方程](img/F000011si8.png)

此外，`Hc` 中 `u + i v` 的范数平方为 `‖u + i v‖² = ‖u‖² + ‖v‖²`。

`Hc` 的表达式本可以写成 `Hc = Hr ⊗ C` 的形式，从而得到相同的整体结果。然而，尽管它们是同构的表示，这仍不会被认为是正确的。此外，量子学科中的大多数运算都是非交换的。因此，多元图描述被修改以表示操作数实际使用的顺序。这之前已针对左或右 `R`-模提及。同样，对于操作数使用顺序很重要的运算符，其箭头尾部被修改。相应的箭头尾部带有斜线 (`/`) 标记表示顺序。因此，一个斜线 (`/`) 表示第一个操作数，两个斜线 (`//`) 表示第二个操作数，以此类推。就当前情况而言，运算符 `TENSOR` 的箭头有一个带有单个斜线的尾部从 `C-SCALAR` 发出，另一个带有两个斜线的尾部连接到 `R-VECTOR`。图 4.1 说明了这一事实。在此图中，先前在希尔伯特空间描述和域描述中使用的所有箭头均被省略。如果使用另一种复化方法，即 `Hc = Hr ⊗ C`，则下图中斜线的方向将被反转。

![图 4.1 复化的多元图。](img/F000011f04-01-9780443136979.jpg)

图 4.1 复化的多元图。

### Example 4.3

在此示例中，我们使用刚刚描述的复化，其载体集合为：`Hr = R`，即如 示例 4.1 中所述的实一维希尔伯特空间。在这种情况下，`Hc = C ⊗ R` 只是单维希尔伯特空间；真空空间 `Hc = C` 在 示例 4.2 中给出。

在此提醒一下，`SCALAR` 的类型决定向量空间是实数还是复数。例如，如果 `VECTOR` 的载体集合由所有复数组成，而 `SCALAR` 的载体集合为实数，并采用通常的运算，则该向量空间是实向量空间。

## 4.3 Dual space used in quantum



# 代数对偶空间

## 定义
代数对偶空间是指在复数域 `C` 上的有限维向量空间 `V` 的线性映射（泛函）从 `V` 到 `C` 的集合 `Vd`。这通常记作 `Hom(V, C)`。该记号表示从 `V` 到复数域的多线性映射的集合。除了代数对偶空间之外，还有涉及有界线性泛函的拓扑对偶空间，并在后续章节中描述和应用（Adler, 2015; Mac Land and Birkhoff, 1999）。

## MSA 全局视图
对于代数对偶空间的 MSA 全局视图，有两种类型：`SCALAR` 和 `VECTOR`。对于复数域和向量空间而言，所有签名集合与之前相同；然而，对于向量空间结构存在一个额外的签名集合。新的签名集合本身包含一个称为 `COVECT` 的单一集合。`COVECT` 的元素是映射名称 `FUNC1`、`FUNC2`、… `FUNCN`。这些表示泛函，且 `N` 是向量空间 `V` 的维数。无限维的对偶空间将在后面的章节中描述。如前所述，集合 `COVECT` 的每个元素都是一个一元线性映射名称，使得：
* `FUNCj`：将 `VECTOR` → `SCALAR`，对于所有 `j`=1,2,…, `N`。

![方程](img/F000011si12.png)

因此集合 `COVECT` 的基数为 `N`。当为集合 `COVECT` 中元素所关联的向量定义加法（`+`）和标量乘法（`·`）时，它成为 `C` 上的向量空间。其维数为 `N`，称为 `V` 的对偶空间，在本文档中记为 `Vd`。

## 符号集合与记号
此外，以下方程恒等式必须成立。描述这些约束的记号由符号给出：
* `SCALAR` 用 `a` 表示。
* `VECTOR` 用 `v` 和 `w` 表示。
* `COVECT` 中的泛函用 `f[i]` 和 `f[j]` 表示。

## 方程恒等式
描述基本向量空间运算的方程恒等式成立：
1. 向量加法：`(f[i] + f[j]) (v) = f[i] (v) + f[j] (v)`。
2. 标量乘法：`(a·f[j]) (v) = a·(f[j] (v))`。
3. 线性性：`f[j] (a·v + w) = a·f[j] (v) + f[j] (w)`。即 `f[j]` 在 `Hom(V, C)` 中。

所有向量空间的公理都源于这些方程恒等式。特别地，`Vd` 中的零就是零泛函。它将 `V` 中的每个元素映射到 `C` 中的零元素。前面呈现的全局视图对于所采用的域仍然成立；它不必是 `C`。例如，域可以是实数；在此情况下，`f[j]` 在 `Hom(V, R)` 中。

## 内积、等距同构与反同构
由于向量空间 `V` 和 `Vd` 具有相同的维数，其元素以一种称为半双线性形式的方式自然配对。该形式将导致内积，并且可以由 Riesz 表示定理（RRT）证明。然而，对于像 `V` 这样的有限维希尔伯特空间，很容易看出 `Vd` 中的任意泛函 `f` 都可以表示为内积。更具体地说，存在唯一的向量 `z` 在 `V` 中使得 `f (x) = < x | z >`。此外，对于 `V` 中的每个向量 `z`，都存在一个对应的泛函，即 `Vd` 中的向量 `f`，使得 `f (x) = < x | z >`。

现在将涉及 `Vd` 元素的内积定义。设 `g` 在 `Vd` 中，并且设向量 `w` 在 `V` 中使得 RRT 生效。然后，`Vd` 中的内积由恒等式给出：`<g | f> = <w | z>`。因此 `Vd` 中的内积继承自 `V` 中的原始内积。如 usual，`Vd` 上的范数由内积诱导，且范数得以保持：`‖f‖ = ‖z‖`。范数的识别称为等距同构，通常是保距离映射。这些结果对于有界线性泛函在无限维希尔伯特空间中也成立，并且在量子学科中至关重要。

在此定义下，前面提到的方程恒等式和内积的附加条件成立，从而使 `Vd` 成为内积空间。由于 `V` 是有限维的，它是希尔伯特空间。在无限维情况下，其中许多结果是不同的。两个空间 `Vd` 和 `V` 是反同构的；存在一个共轭 1–1、满射、等距、线性映射从 `V` 到 `Vd`（通过将向量 `f` 与 `z` 关联）。此外，`V` 与共轭空间 `Vd*` 同构。在 `Vd*` 中，标量 `a` 与向量 `v` 的乘法由 `a*·v` 给出。图 4.2 直观地说明了对偶空间 `Vd` 如何由 `N` 个泛函 `FUNC1`、…、`FUNCN` 产生。可以给出类似的程序和相应的图示，显示 `U = Hom(V, W) = {f: V → W, such that |f is linear}` 是一个向量空间，其中 `W` 也是与 `V` 同构的向量空间。

![图 4.2 用于说明对偶空间创建的多元图。](img/F000011f04-02-9780443136979.jpg)

图 4.2 用于说明对偶空间创建的多元图。

## 对偶基与双正交性
描述了三个不同的向量空间，全部维数为 `N`。将 `Vd` 的基与原始空间 `V` 的基联系起来很有趣。因此设 `E = {e[1], e[2], …, e[N]}` 为来自 `V` 的一组基向量。滥用记号，设 `F = {f[1], f[2], …, f[N]}` 为 `Vd` 的对应基。`Vd` 中的每个协向量 `h` 都可以用 `F` 的元素表示。特别地，`h = h (e[1]) f[1] + h (e[2]) f[2] + … + h (e[N]) f[N]`。现在将给出寻找 `F` 中实际协向量的方法。这些向量对应于 `V` 的基 `E` 内的向量。非零向量空间中有许多基，并且有几种构造方法。然而，双正交性程序是在有限维向量空间中构造对偶基的标准技术（Halmos, 1958）。

`E` 和 `F` 不必是正交或甚至正交的向量集；它们只需要是基即可。寻找 `F` 中实际协向量的程序首先要认识到每个 `f[j]` 也是一个泛函。当它应用于 `V` 中的向量时，会得到一个复数。接下来，这里描述的标准方法是取 `f[j]* (e[k])`，即使用 `f[j]` 的共轭并将其应用于基向量 `e[k]`，对于所有 `j` 和 `k` 在 `{1, 2, …, N}` 中。这会得到一个复标量。最后执行双正交性条件：即当 `j` 与 `k` 不同时将这些复数设为零，并在 `j = k` 时设为一。这产生了寻找 `F` 中向量的 `N` 个线性独立方程。所得基称为 `Vd` 的对偶基。

## 下层 MSA 视图与矩阵表示
将给出对偶空间的下层 MSA 视图以及该空间元素的简单表示。`COVECT` 的关联载体集是所有泛函映射的集合，通常称为协向量或一形式。`V` 中向量的简单表示是将其表示为 `N` by `1` 复值列向量。这有助于确定 `Vd` 中的协向量。在此程序中，第一步是以顺序将 `V` 的每个基元素表示为列向量。接下来，以顺序将每个协向量基元素表示为共轭未知元组的 `1` by `N` 行向量。简单地将每个行向量（协向量=`k`）乘以每个列向量（向量=`j`）。每次向量乘法提供一个复数。对所有向量和协向量执行此操作会得到 `N` 个方程和 `N` 个未知数。最后，将所得方程设为零，除非指标的顺序一致。在一致的情况下，即当且仅当 `j = k` 时，结果设为一；否则设为零。这是双正交性条件。求解结束程序。下面提供了该方法的说明。



下一个示例通常是学习量子学科的起点。该示例涉及利用 kets 和 bras。这些构造分别用 `|>` 和 `<|` 表示。按此顺序将 bra 与 ket 结合，结果为内积。这用 `<‖>` 表示，也称为 bra-ket。此外，在这种 bra-ket 记法中省略其中一条竖线是很常见的。因此，内积表示为 `<|>`，如前几节所示。如前所述，有时在内积中使用逗号，同样取代这两条竖线。这两种记法都是标准的，并在本文档中始终使用。在下一个示例中，底层希尔伯特空间是二维复数域 `C²`，以及其对偶空间。空间 `C²` 将被视为量子比特的空间。

## 示例 4.4
量子技术的一个基本希尔伯特空间是复希尔伯特空间 `C²`，即复数域上的二维复向量空间。对应于 `VECTOR` 的载体集合的元素称为量子比特。它们将表示为由复数组成的元组的 2×1 列向量。每个这样的列向量也被称为 ket。`SCALAR` 的载体集合再次是复数。特定的向量空间运算源于签名集合。它们是通常的 2×1 列向量加法和通常的标量乘法。这涉及复标量 `c` 与 2×1 列向量相乘。`C²` 的基通常由两个量子比特给出：`|0>=(1 0)′` 和 `|1>=(0 1)′`；这里 `(′)` 表示转置，结果是列向量的基

前例中提到的 kets 的线性组合或叠加涉及系数，其绝对值平方之和为一。也就是说，通常使用范数为一的 kets，从而得到简洁的 kets。这些更常被称为纯态，而非混合态。在此将遵循称这些向量为纯态的惯例，但随后会纠正，并在更正式地引入希尔伯特空间的张量积时再次纠正。为记录在案，态是希尔伯特空间上的算子，而非希尔伯特空间内的向量。严格来说，态 `ρ`![Equation](img/F000011si13.png) 是一个正线性迹类映射，`ρ`![Equation](img/F000011si14.png): `H` → `H`，使得 `Tr` (`ρ`![Equation](img/F000011si15.png))=1。当希尔伯特空间 `H` 中存在向量 `v` 使得 `ρ`[`v`] (`u`)=\[<v, u>/<v, v>\] `v` 时，它被称为纯态。因此纯态与希尔伯特空间中的元素相关联。如果态不是纯态，则称该态为混合态。此外，就 `C*` 代数而言，纯态是 `C*` 代数上的幺正、正泛函。无论如何，我们将继续使用传统的、操作性的和形式化的记号和描述。诸如迹类和正性等概念将在后续章节中阐明。

请注意，Ket `|w>=1/((2)^(1/2))·(| 0> + i·|1>)` 是另一个纯态的例子，因为其范数等于一。由前面提到的表示可知 `|w>=1/((2)^(1/2)) (1 i)′`。请注意 ket：`|w>` 的第二个元组为虚标量值。集合 `E={| 0>, |w>}` 应视为有序基，因为将引用这些 kets 在 `E` 中的位置。然而，它不是 `C²` 的正交基。无论如何，现在将求出相应的对偶空间基 `F`。该过程涉及逐一使用 `E` 中的两个向量。因此 Ket `|0>` 将用作基 `E` 中的第一个元素。

回想一下，协向量由行向量表示。它们的元组是列向量元组的复共轭值；它们是行向量。目标是在 `V` 中给定基 `E={|0>, |w>}` 的情况下找到协向量基 `F`。为此，设第一个协向量为 `f=(a* b*)`。此外，虽然现在未使用，设另一个协向量为 `g=(c* d*)`。将第一个协向量，即来自 `F` 的行向量与来自 `E` 的第一个列向量相乘；这样得到 `(a* b*)·(1 0)′=a*`。使用来自集合 `E` 和 `F` 的第一个向量，要求结果设为一，因此 `a*=1`。重复向量乘法，再次使用来自 `F` 的第一个协向量，但这次使用基 `E` 中的第二个向量。如果这样做，则将以下行向量与列向量 `(a* b*)·1/((2)^(1/2)) (1 i)′` 相乘意味着 `1/((2)^(1/2)) (a* + i·b*)=0`。由于 `a*=1`，我们可以求解 `b*` 得到 `b*=−1/i=i`。因此，对偶空间 `Vd` 的基 `F` 中的第一个协向量是行向量 `f=(1 i)`。

以类似的方式，我们现在将求出 `F` 中的第二个协向量 `g`，即 `(c* d*)`。这次，`(c* d*)·(1 0)′=0`。这意味着 `c*=0`。接下来，为求 `d*`，设 `(c* d*)·1/((2)^(1/2)) (1 i)′=1 / ((2)^(1/2)) i d*=1`。最后一个表达式中出现数字一，因为它涉及空间 `V` 和 `Vd` 中的第二个向量。由此可得 `d*=−i (2)^(1/2)`。因此，`g=(0 − i (2)^(1/2))`。请注意 `f` 和 `g` 未归一化；它们的两个范数平方为 `‖f‖²=(1 −i) (1 i)′=2` 和 `‖g‖²=2`。然而，它们仍然构成对偶空间的基，`F={f, g}`。

对偶空间中的任何协向量 `h` 都是 `F={f, g}` 中基元素的唯一线性组合。下面给出该线性组合的示例。

## 示例 4.5
给定 `Vd` 中的任意行向量 `h`，例如，设 `h=(2 1)`。那么 `h` 必须使用该空间的基表示，即 `F={f, g}`。这将通过使用本节开头给出的公式来说明：`h=h(e[1]) f + h(e[2]) g`。在这种情况下，使用 `e[1]=|v>=(1 0)′`，和 `e[2]=|w>=2^(−1/2) (1 i)′`，该向量此前已在 `V` 中使用。代入 `f=(1 i)`，`g=(0 −i 2^(1/2))`，如前所述。然后，根据公式，`h=[(2 1)·(1 0)′] (1 i) + [(2 1)·2^(−1/2) (1 i)′] (0 −i 2^(1/2))=[2] (1 i) + [2^(1/2)+ 2^(−1/2) i] (0 −i 2^(1/2))`。现在展开得到 `h=(2 2i) + (0–2^(−1/2)(2 + i) i (2)^(1/2))=(2 2i) + (0 −i (2 + i))`，从而再次得到期望的结果 `h=(2 1)`。

刚刚找到的对偶空间基仅用于说明其构造以及简单的计算，例如使用这些基构造线性组合，如 示例 4.5 中所示。它还提供了在未假设时证明两个空间 `V` 和 `Vd` 均为维度 `N` 的背景。此外，它有助于理解双对偶空间。否则，在量子力学中用处不大。这是由于刚刚找到的对偶基未归一化。因此，使用该基时，对应的 bras 的范数不是单位范数。在量子技术中，kets 和 bras 具有单位范数。因此，接下来给出一个更重要但更简单的对偶基。它是量子学科所需的基。

考虑 `C²` 的标准正交基 `{|0>, |1>}`，即 `E={(1 0)′, (0 1)′}`。相应的对偶空间基为 `F={f=(1 0), g=(0 1)}`。这是用于量子计算的对偶空间的基类型。与其像之前那样写出该基，将改用 bras。滥用记号，设余基 `F` 由 `{<f |=(1 0), <g|=(0 1)}` 给出，且 `E={|0>=(1 0)′, |1>=(0 1)}′`。现在可以在 `V` 的基元素之间使用 kets 进行内积运算，并在对偶空间中使用 bras。很容易看出双正交条件得到满足。使用 bras 和 kets 的内积在两个希尔伯特空间 `V` 和 `Vd` 之间诱导出额外的对应关系。



## 4.3 共轭线性映射

一个自然的共轭线性映射由 `K` 给出，从 kets 的希尔伯特空间到 bras 的希尔伯特空间。这里，`K(|v> + |w>)=<v| + <w|`，且 `K(a·|v>)=a*·<v|`，对于任意复标量 `a`，其中 `a*` 是 `a` 的共轭。另外，往另一个方向，映射 `B` 从 bras 的对偶空间到原始希尔伯特空间满足 `B(<f| + <g|)=|f> + |g>` 且 `B(a<f|)=a*|f>`。算子 `B` 和 `K` 是 `V` 与其对偶空间之间的 1–1、满、等距共轭映射。因为范数得以保持，所以它是等距映射。简而言之，`‖|f>‖=‖<f|‖`。等距映射也称为等距变换，详见后章。

该结果推广到任意具有 kets 和 bras 的有限维希尔伯特空间，特别是到一个 `n` 量子能级系统，即 `n` 维希尔伯特空间 `C^(n)`。此外，它以操作方式用于无限维拓扑对偶希尔伯特空间，以及巴拿赫空间。图 4.3 说明了使用运算 `B` 和 `K` 在 `V` 与其对偶空间 `Vd` 之间的共轭线性及等距映射。

![图 4.3 关联 ket 和 bra 希尔伯特空间的图。](img/F000011f04-03-9780443136979.jpg)

图 4.3 关联 ket 和 bra 希尔伯特空间的图。

## 4.4 双对偶希尔伯特空间

双对偶空间 `Vdd` 是 `V` 的 `Vd` 的对偶。因此，`Vdd=Hom(Vd, C)`；它是 `Vd` 到 `C` 的所有线性映射的集合。通过将 `Vd` 与 `V` 关联可知，两个空间 `Vdd` 和 `Vd` 之间也存在共轭线性、1–1、满、等距映射从 `Vdd` 到 `Vd`。可以说双对偶希尔伯特空间 `Vdd` 与 `V` 相同（哈尔莫斯, 1958）。双重共轭导致恒等映射。存在一个从 `Vdd` 到 `V` 的规范映射，给出在下一段中，并由 图 4.4 说明。稍后会给出更多细节。

![图 4.4 双对偶的规范同构映射。](img/F000011f04-04-9780443136979.jpg)

图 4.4 双对偶的规范同构映射。

设 `g` 在 `Vdd` 中，即 `g: Vd → C`。这是一个线性映射。将会证明 `g` 实际上将 `V` 中的向量 `v` 映射到 `C`。在上一节中，已看到当使用 `V` 的基向量集合 `E={e[1], e[2], …, e[N]}` 时，对应有一个集合 `F={f[1], f[2], …, f[N]}`，它是 `Vd` 中协向量的基。重要的是 `Vd` 中的每一个协向量 `h` 都可以用来自 `E` 的向量以及来自 `F` 的基元素表示为线性表达式。这在二维向量空间中于 例 4.5 中有所说明。一般表示如下：

对于 `h in Vd`，`h = h(e[1])f[1] + h(e[2])f[2] + … + h(e[N])f[N]`。

![方程](img/F000011si16.png)

接下来，由于 `g` 在 `Vdd` 中，将 `g` 应用于 `Vd` 中的 `h`：

`g(h) = g[h(e[1])f[1] + h(e[2])f[2] + … + h(e[N])f[N]]`。

![方程](img/F000011si17.png)

利用 `g` 的线性以及 `h(e[j])` 是 `C` 中的标量这一事实；则：

`g(h) = (h(e[1])g(f[1]) + h(e[2])g(f[2]) + … + h(e[N])g(f[N]))`。

![方程](img/F000011si18.png)

注意该和也在 `C` 中；即它是标量的和。因此用标量 `aj` 替换每个 `g(fj)` 并写成如下形式：

`g(h) = h(e[1])a[1] + h(e[2])a[2] + … + h(e[N])a[N]`。

![方程](img/F000011si19.png)

由于 `h` 是线性的，可知 `g(h)` 可写为 `g(h)=h(a[1]e[1] + a[2]e[2] + … + a[N]e[N])`。然而和 `a[1]e[1] + a[2]e[2] + … + a[N]e[N]` 是一个唯一元素 `v`，其中 `v` 在 `V` 中。可知通过取 `Vdd` 中的任意 `g`，协向量的求值产生 `V` 中的唯一元素 `v`。它满足 `g(h)=h(v)`；该映射由 图 4.4 说明。对于 `Vdd` 中每一个不同的 `g`，将对应一个不同的 `v` 在 `V` 中，反之亦然。这称为 `V` 与 `Vdd` 之间的规范同构映射。

原始空间 `V` 可与 `Hom(Vd, C)` 识别，因为通过取 `V` 中的任意向量 `v` 我们可以将其与 `Vdd` 中的线性求值映射 `gv` 关联。设 `gv: Vd → C` 且 `gv` 线性。因此，对于 `Vd` 中的 `h`，定义 `gv(h)=h(v)`，类似于前面使用 `g` 的情况。为了说明其线性，使用 `Vd` 中的 `h[1]` 和 `h[2]` 以及 `C` 中的 `a`；则有：

`gv(h[1]+h[2]) = (h[1] + h[2])(v) = h1 + h2 = gv(h[1]) + gv(h[2])`

![方程](img/F000011si20.png)

且

`gv(a h) = (a h)(v) = a (h)(v) = a gv(h)`。

![方程](img/F000011si21.png)

为证明代数同构，考虑 `F: Vdd → V`，其中 `F(g[1])=v[1]`，`F(g[2])=v[2]`，且 `F(g)=v`，使用 `Vd` 中的 `h`。

则 `(g[1] + g[2])(h)=g1 + g2=h(v[1]) + h(v[2])=h(v[1] + v[2])`。

另外 `(a g)(h)=a(g)(h)=a h(v)=h(a v)`。`V` 的自然同构元素可视为从 `Vdd` 到 `C` 的线性映射。

## 4.5 外积

向量与协向量的外积在量子研究中至关重要。该运算通常称为纯或简单张量。在有限维情况下，结果将是一个矩阵。将会看到 kets 和 bras 在描述该运算时很有用。首先，将在 MSA 中从有限维希尔伯特空间的全局层面给出外积的严格规范。

首先回顾，对于固定的 `n`，所有 `n` by `n`、`n=1, 2, 3, …` 矩阵的集合构成复数域上的结合幺代数。在此观点下，与 `VECTOR` 关联的载体集合是 `n` by `n` 矩阵的集合。所有通常的矩阵运算——标量乘法、矩阵乘法、矩阵加法、矩阵减法、矩阵偏逆、矩阵零、矩阵恒等——均源于签名集合内的运算名称：相应地，名称为 `S-MULT`、`BINE`、`V-ADD`、`V-MINUS`、`V-INVERSE` 和 `V-ZERO`，并且如前所述，单位矩阵由 `V-ONE` 得到。此外，所有结合幺代数的等式恒等式均成立。为描述外积，有用的是定义第三个排序 `MATRIX`。关联的载体集合是所有 `n` by `n` 矩阵的集合，所有通常的矩阵运算均源于结合幺代数构造。参见第 3.1 节，图 3.1。

描述外积的排序为 `VECTOR`、`SCALAR` 和 `MATRIX`。适用于希尔伯特空间、复数域和结合幺代数结构的全部签名集合及其所有附加条件均被假定成立。然而，存在一个包含单个算子名 `OUTER` 的额外签名集合。它是二元的且满足：

`OUTER: VECTOR x VECTOR -> MATRIX`。

![方程](img/F000011si22.png)

除希尔伯特空间、复数域和结合幺代数的约束外，还需要若干等式约束。

这里，排序的表示如下：

* `VECTOR` 用 `u`、`v` 和 `w` 表示。
* `SCALAR` 用 `c` 表示。
* `MATRIX` 用 `M` 表示。

签名集合的代表元素以建议符号给出：

* `V-ADD` 用 `+` 表示。
* `S-MULT` 用 `·` 表示。
* `OUTER` 用 `⊗` 表示。

附加约束如下：

1. 线性：`c·(v ⊗ u) = (c·v) ⊗ u = v ⊗ (c·u)`。
2. 分配律：`(v + w) ⊗ u = v ⊗ u + w ⊗ u`。
3. 分配律：`u ⊗ (v + w) = u ⊗ v + u ⊗ w`。



## 4.5 外积

` (u ⊗ v)'* = (v ⊗ u) `, 其中第一个项 `(u ⊗ v)` 先转置然后取共轭。

图 4.5 描述了外积运算两次，一次是一般情况，然后使用 kets 和 bras。类型 `SCALAR` 未作图示。此图中未图示其他运算。仅涉及希尔伯特空间、复数域或幺半结合代数的算符名称未显示。在下图示中，多元箭头第一个尾部对应于一个 ket，第二个对应于一个 bra。这与形成内积时使用的顺序相反。

![图 4.5 说明外积的多元图。](img/F000011f04-05-9780443136979.jpg)

图 4.5 说明外积的多元图。

对于 `C^n` 中的向量 `v` 和 `w`，外积 `u` 最容易通过形成 `u = v w'*` 得到。因此 `v` 的维数是 `n` 行一列，而 `w'*` 是 一行 `n` 列；因此外积是一个 `n` 行 `n` 列的矩阵。

### 例 4.6

外积的一个简单实例可以取 `VECTOR` 相关的载体集为 `C²`。`MATRIX` 的对应载体集是复数域上所有 2×2 矩阵的幺半结合代数。因此，例如，如果 `v = (a b)'` 和 `w = (c d)'` 在 `C²` 中，则可以使用算符 `⊗`，表示名称为外积的实际算符。对于选定的 `v` 和 `w`，`v ⊗ w` 是 2×2 矩阵：

$|\\begin{matrix} {\\text{ac} \\ast} & {\\text{ad} \\ast} \\\\ \\end{matrix}|$

![方程](img/F000011si38.png)

$|\\begin{matrix} {\\text{bc} \\ast} & {\\text{bd} \\ast} \\\\ \\end{matrix}|$

![方程](img/F000011si39.png)

如前所述，结果也可以使用 `v ⊗ w = v w'*` 找到，其中 `w'*` 是 `w` 的共轭转置。因此，`w'*` 是一个行向量，`w'* = (c* d*)`。然而，根据 bras 的定义，`<w| = (c* d*)`，以及 kets，`|v> = (a b)'`，可知 图 4.5 中的表示成立，即 `v ⊗ w = |v><w| = (a b)' (c* d*)`。

## 4.6 多线性形式、楔积和内积

在引入张量之前，将给出 n 线性或多线性形式的概念。对于此定义，笛卡尔积 `Π` 运算是 `Π[i] (Vi)` 表示乘积 `V1 x V2 x … x Vn`。在这种情况下，`{Vi} i=1, …, n` 是复数域上的向量空间集合，而 `Π` 表示该集合中所有 `n` 个向量空间的笛卡尔积。然后，运算 `M: ∏(Vi)→ C` 是多线性映射，当 `M` 在每个坐标上都是线性的时。即等式恒等式 (1) 和 (2) 成立：

1. `M (v1, v2, …, a vi, …, vn) = a M (v1, v2, …, vi, …, vn)`.

2. `M (v1, …, vi + v'i, …, vn) = M (v1, …, vi, …, vn) + M (v1, …, v'i, …,vn)`.

* 在前面提到的等式 (1) 中，向量 `vi` 被标量 `a` 乘以，结果是 `M`，其中 `M` 是多线性映射；类似地，在等式 (2) 中，向量 `vi` 和 `vi'` 相加，两者都在 `M` 中，结果是涉及 `M` 的和。

* 所有 n 个多线性映射 `M: P (Vi) → C` 的集合本身形成一个向量空间 `V`。多线性形式在交换、置换或转置任意两个向量时改变符号时称为交替。即：

1. `M (v1, v2, …, vi, …, vj,…, vn) = − M (v1, v2, …, vj,…, vi, …,vn)`.

所有交替 n 形式的集合也是一个向量空间，表示为 `AnV*`。该空间的对偶基记为 `{e^S, such that card(S)=n; that is, there are n elements in S}`。此外，`S` 本身是 `{1, 2, …, k}` 的子集，这使得跟踪基元素变得容易。对于 `k` 大于或等于 1 的情况，符号 `e^S` 定义为 `e^S = e^{j1} ∧ e^{j2} ∧ … ∧ e^{jn}` 使用 `S = {j1 < j2 < … < jn}`。这些 `jk` 上标不是幂；它们是表示对偶空间基的上标。楔 `∧` 在逻辑中表示“与”符号。

对于 `V` 的基集 `{ei1, …, ein}`，由于 `e^S` 是对偶空间，当 `e^S` 作用于 `V` 中的向量时，得到标量。在这种情况下，`e^S(ei1, …, ein) = 1, 0, or −1`。该值取决于 `V` 的基的索引集，即 `T = {i1 < … < in}`，是否涉及与 `S` 相同的 `n` 个对应基元素。顺序也必须相同。当如此时，得到 1。当使用相同的 `n` 个元素但进行置换时，对于偶数次转置，再次得到 1。对于奇数次转置，结果为 −1。否则，值为零。即当对偶基 `e^S` 涉及与其实参中不同的向量时，值为零。实参由 `V` 中的向量组成，即 `(ei1, …, ein)`。

### 例 4.7

使用上述记号，令 `k = 3`，但 `n = 2`。所有交替二形式集合 `A2V*` 的基必须有两个向量，但它们可以用集合 `{1, 2, 3}` 的上标标记。因此，假设此情况下的对偶基是集合 `{e¹, e³}`，即 `e^S = e^{1,3} = e¹ ∧ e³`。使用此对偶空间基，这些向量 `e^S` 可以作用于 `V` 中的向量，并且由于它们在对偶空间中，结果是标量。因此对于给定的对偶基，楔作用于 `e2` 和 `e3` 得到 `(e¹ ∧ e³)(e2, e3) = 0`。这是因为使用了不同标记的向量。接下来，`(e¹ ∧ e³)(e3, e1) = −1`；这是因为向量具有相同的标签，但在不同的单次转置顺序中。最后，`(e¹ ∧ e³)(e1, e3) = 1`，因为向量具有相同的标签和相同的顺序。

接下来，使用来自 `V` 的向量的线性组合，标量 `ai` 和 `bj` 在 `C` 中。对偶运算应用于说明线性方面。令 `v = Σ_{i = 1}^{3} ai ei` 的和，以及 `w = Σ_{j = 1}^{3} bj ej` 的和；则 `(e¹ ∧ e³)(v, w) = a1 b3 − a3 b1`。这是因为九项中的七项值为零。例如，`(e¹ ∧ e³)(a1 e1, b2 e2) = a1 b2 (e¹ ∧ e³)(e1, e2) = a1 b2·0 = 0`；这首先使用线性，即提取 `a1 b2`。然后注意到上标在 `{1, 3}` 中，但 `V` 中的向量标签在 `{1, 2}` 中。

对于交替 n 形式的向量空间 `AnV*`，其维数记为 `dim`，其维数使用 k 个事物然后 n 次的组合公式计算：`(k/n) = k!/(n! (k−n)!)`。由此可知 `dim(AkV*) = 1`，因为在这种情况下 `n = k`，即 k 个事物取 k 次，因此 `(k/k) = k!/(k! (k−k)!)` 等于一。此外，`AkV* = {0}` 对于 `n > k`。当 `n = k` 时，结果通常称为顶形式，因为使用更大的 `n` 值而不得到零是不可能的。另有 `A1V* = V*`。形式 `w` 的次数 `n` 记为 `deg(w)` 并由关系 `w` 是 `AnV*` 的元素定义。假设 `w` 和 `u` 的楔或外积分别是 `AnV*` 和 `AmV*` 的元素。这里，`w ∧ u` 是 `A(n+m)V*` 的元素，定义如下：`(w ∧ u)(v1, …, vn, v(n+1), …, v(n+m)) = sum over all permutations s of {1, …, n+m}, of the product: [sign(s) w(vs1, …, vsn) u(vs(n+1), …, vs(n+m)) ]`，并保持顺序：`s1 < … < sn`，以及 `s(n+1) < … < s(n+m)`，但求和还涉及实参的洗牌。



## 楔积

楔积是外代数中的乘积。它具有以下性质（斯皮瓦克，1990）：

1. 结合性：`u ∧ (w ∧ v) = (u ∧ w) ∧ v`。
2. 齐次性：`(c u) ∧ v = c (u ∧ v) = u ∧ (c v)`，其中 `c` 为标量。
3. 分配性：`(u + v) ∧ w = (u ∧ w) + (v ∧ w)`。
4. 分配性：`w ∧ (u + v) = (w ∧ u) + (w ∧ v)`。
5. 反交换性：`u ∧ v = (−1)^{n m} (v ∧ u)`，其中 `u` 在 `AnV*` 中且 `v` 在 `AmV*` 中。

### 例 4.8

对于 `n=1` 且 `m=2` 的情形，即 `w` 在交替 `A1V*` 空间中而 `u` 在 `A2V*` 中，楔积或外积 `w ∧ u` 在 `A3V*` 中。其在 `V` 中的自变量为 `(v1, v2, v3)`。以 `w` 为一元算子且 `u` 为二元算子，则 `w ∧ u` 的所有组合为
`(w ∧ u)(v1, v2, v3)=w(v1)u(v2,v3) + w(v2)u(v3,v1) + w(v3)u(v1,v2) − w(v1)u(v3,v2) − w(v2)u(v1,v3) − w(v3)u(v2,v1)`。`w(v1)u(v3,v2)` 的符号为负，因为在此元素中发生了 1、2、3 的一次换位。

### 例 4.9

对于 `w` 在 `A1R³` 中，`dim(A1R³)=3`，因为 `k=3` 且 `n=1`，即一次取三个事物为三个。在此空间中，`w=a1 e¹ + a2 e² + a3 e³` 为行向量，即 `w=(a1 a2 a3)`。更严格地说，此空间与 `R³` 之间存在同构。

### 例 4.10

这次考虑 `A2R³`；再次该空间的维数为三，因为两两取三个事物有三种方式。然而该空间的典型元素为 `w=a1(e² ∧ e³) + a2(e³ ∧ e¹) + a3(e¹ ∧ e²)`。这也可以等同于 `(a1 a2, a3)`。更重要的是，当 `w` 与 `u` 在 `A1R³` 中时，其中 `w` 为 `b_j e^{j}` 之和，即 `$w = \\sum_{j = 1}^{3}{b_j e}^{j}$`，且 `$u = \\sum_{j = 1}^{3}{c_j e}^{j}$`，则
`w ∧ u = (b2 c3 − b3 c2) (e² ∧ e³) + (b3 c1 − b1 c3) (e³ ∧ e¹) + (b1 c2 − c1 b2) (e¹ ∧ e²)`。在最后表达式中 `− c1 b2 (e¹ ∧ e²)` 出现的原因是 `(b2 e² ∧ c1 e¹)=b2 c1 (e² ∧ e¹)=c1 b2 (e² ∧ e¹)` 由线性性且标量可交换得到。最后，`c1 b2 (e² ∧ e¹)= − c1 b2 (e¹ ∧ e²)`，因为 `(e² ∧ e¹)= (e¹ ∧ e²)`。

设 `w` 与 `u` 被视为 `R³` 中的向量。在前述表达式中，注意楔积的标量系数是向量 `w` 与 `u` 的叉积的标量系数。这可以从描述 `w=(b1 b2 b3)′` 与 `u=(c1 c2 c3)′` 的叉积的行列式看出：

`[b2 c3 − b3 c2] i + [b3 c1 − c3 b1] j + [b1 c2 − c1 b2] k`。

最后将对二维中两个向量的楔积作说明。首先 `(w ∧ u)` 是 `w` 与 `u` 的张量积非交换性的度量。在此情形下，`w ∧ u = w ⊗ u + u ⊗ w`。相应地，`w` 与 `u` 的楔积可表示为方阵，其元素为 `(w ∧ u)[i j] = (w[i] u[j] − w[j] u[i])`。在三维中，`(w ∧ u)` 矩阵的主对角线元素为零。其他六个元素由 `w` 与 `u` 的叉积系数，或 `u` 与 `w` 的系数给出。

内积与外积或楔积相反。它与向量场 `v` 相关联。`v` 的内积是一个线性运算；它记为 `l_v` 且满足 `l_v: AnV* → A(n−1)V*`，其中 `(l_v w)(v2, …, vn)=w(v, v2, …, vn)`。这也称为 `w` 对 `v` 的收缩。这里，行向量 `(v, … vn)` 被映射到函数 `w(v, v2, …, vn)`，涉及 `n` 个自变量。关于 `A^(−1) V*` 的约定是令 `A^(−1) V*={0}`。内积是幂零的，即两次应用得到零。这意味着它是反对称的。内积还满足称为导子的莱布尼茨型规则。即，`l_v(w ∧ u) = (l_v w) ∧ u + (−1)^{deg(w)} w ∧ (l_v u)`。

### 例 4.11

这是 `R³` 中内积莱布尼茨规则的例证。设基集为 `{e1, e2, e3}`，且 `v=e1`；则求 `l_v(e¹ ∧ e² ∧ e³)`。这里 `e¹, e², e³` 是来自对偶空间的向量，即余基。首先，设 `w=e¹ ∧ e²` 且 `u=e³`。注意 `w` 的次数为二，因而 `(−1)^{deg(w)}=1`。那么莱布尼茨规则给出 `l_v(w ∧ u)=l_v(e¹ ∧ e²) ∧ u + 1 w ∧ (l_v u)=l_v(e¹ ∧ e²) ∧ u`。这是因为在 `(l_v u)=l_{e1}(e³)=e³(e1)=0` 中使用了不同的基元素。由于结果是 `l_v(w ∧ u)=l_v(e¹ ∧ e²) ∧ u`，将再次应用莱布尼茨规则。这次设 `w′=e¹` 且 `u′=e²`。可得 `l_v(e¹ ∧ e²) ∧ e³ = [(l_v w′)∧ u′ − w′ ∧ (l_v u′)] ∧ e³ = 1 u′ ∧ e³ = e² ∧ e³`。该结果成立因为 `deg(w′)=1`，因此之前使用了负号。另外，`l_v u′=u′(v)=e²(e1)=0`，最后 `l_v w′=w′(v)=e¹(e1)=1`。

## 4.7 张量向量空间的多排序代数

设 `V` 为复向量空间，现将其代数对偶空间记为 `V*`，如第 4.6 节所用。它在第 4.3 节中用 `Vd` 表示。如常，`V*` 由所有从 `V` 到 `C` 的线性映射 `f` 组成，也称为协向量。复数域上的 `(p, q)` 张量 `T` 是一个多线性形式：`T: V* x…x V* x V x…x V → C`，其中乘积空间中有 `p` 个 `V*` 的拷贝和 `q` 个 `V` 的拷贝。量 `p` 和 `q` 称为平衡数，它们的和为秩。



接下来给出的记号是对类型 `VECTOR` 的重新命名。当使用张量代替 `VECTOR` 时，所有 `p + q` 元张量的集合的更常见名称由一个非常长的表示给出，它是 `V ⊗ V ⊗ … ⊗ V x V* ⊗ V* ⊗….⊗ V*`。无论如何，该类型的相应载体集合为 `{T|T is a (p, q) tensor, and it is also a multilinear form}`。上述集合的名称现在将因其长度而缩写为 `Y` 表示。在集合的名称 `Y` 中，有 `p` 个 `V` 的拷贝和 `q` 个 `V*` 的拷贝。使用此记号 `Y` 的思想是 `V*` 的 `p` 个元素应用于 `V` 的 `p` 个元素。此外，`V` 的 `q` 个元素应用于 `V*` 的 `q` 个元素，从而得到一个复数。再次，这意味着当使用载体集合时，实际映射到标量域为 `T: V* x V* x … x V* x V x V x….x V. → C`。记号上的差异在 `MSA` 中使用，以强调使用 `x` 表示张量积名称，而 `⊗`![方程](img/F000011si125.png`) 作为实际运算。

如果该张量集合配备逐点加法，`(+)`，和标量乘法，`(.)`，则该集合在复数域上成为一个向量空间。复数域的所有算符名称和方程恒等式保持不变。然而，在此 `MSA` 对向量空间结构的描述中需要一个额外的签名集合。新的签名集合具有元数为 1 的元素并命名为 `TEN`，对应于实际的多线性算符 `T`，表示一个张量。向量空间结构签名集合中的所有其他元素仍然成立，其中一些名称定义得更具启发性。相关的签名集合的元素如下给出。在下面：`T-ADD` 表示张量加法；`ST-MULT` 表示张量与标量的乘法；`TEN` 表示张量乘法。

`T-ADD`：`Y x Y → Y`。注意此加法是针对固定平衡的张量定义的。

`ST-MULT`：`C-SCALAR x Y → Y`

![方程](img/F000011si126.png`)

`TEN`：`Y → C-SCALAR`

![方程](img/F000011si127.png`)

`T-MINUS`：`Y → Y`

![方程](img/F000011si128.png`)

`T-ZERO`，`Is in Y`

![方程](img/F000011si129.png`)

给出的在 图 4.6 中的多元图说明了这五个运算。没有仅涉及复数域结构的运算被说明。利用这些运算，与张量向量空间相关联的元数序列由 `(1, 2(1, 1), 2(1, 1))` 给出。这是因为有两个不同的签名集合各包含一元算符名称，两个不同的签名集合各包含二元算符名称，以及一个零元算符名称。

![图 4.6 张量向量空间。](img/F000011f04-06-9780443136979.jpg`)

图 4.6 张量向量空间。

如 `MSA` 低视图中之前所述，载体集合由所有 `(p, q)` 张量 `T` 组成。它们现在相应地表示为 `Tpq`。此外，向量空间本身将用 `Vpq` 表示。

### 示例 4.12

向量空间 `V00` 是标量域；在这种情况下，它是复数域 `C`。

向量空间 `V01=V*={f: V → C}`，因此该空间的元素是协向量。

### 示例 4.13

在有限维向量空间中，可知 `V10` 是所有向量的向量空间，即 `V10=V`。这源于 `V` 与 `V**` 之间的同构。也就是说，该空间由从 `V*` 到 `C` 的所有线性映射组成，因此它是 `V`。向量空间 `V11={T11: V* x V → C}=End (V*)`。实际的张量为 `T11={v ⊗`![方程](img/F000011si130.png`) `f, such that v is in V and f is in V*}`。

表达式 `End (V*)` 是 `V*` 上的自同态集合。在有限维向量空间中，也成立 `End (V*)=End (V)′`，其中撇号表示自同态代数在转置方面相同。因此，`V` 中的列向量对应于 `V*` 中的行向量。对于矩阵算符 `M` 和 `N`，注意数量 `(M N)*=N* M*`。另外如果 `M: V → C`，使得 `M v=w`，则 `v′ M′=w′` 因此 `M′: V* → C`。

### 示例 4.14

平衡为 `(0, 2)` 的张量 `f` 和 `g` 的例子通常被视为内积。对于 `V*` 中的 `f` 和 `g`，`f ⊗`![方程](img/F000011si131.png`) `g: V x V → C`。因此对于 `V` 中的 `v` 和 `w`，`f ⊗`![方程](img/F000011si132.png`) `g (v, w)=f(v)·g (w)`。后者乘积类似于点积。此外，该乘积不必是正定的。

此外，该张量是度量张量，它定义在流形或曲面上。它使得可以在这些结构上定义距离和角度。(Lee, 1997)。度量张量具有如下性质：

1. 1) 对称：`g (u, v)=g (v, u)`。
2. 2) 正半定：`g (u, u)> 0` 且 `g (u, u)=0` 当且仅当 `u=0`。

度量张量是在切空间流形上定义的一类张量。这些张量形成一个张量丛。

具有平衡 `(0, N)` 且向量空间维数为 `N` 的张量被称为 `N` 形式。它也称为顶形式、体积形式或行列式。这在下一节中描述。

## 4.8 行列式

行列式定义为 `N` 维向量空间上的自同态(Lang, 2002)。为了得到行列式，需要一个顶形式，下面定义它。首先，`n` 形式 `f` 是 `T0N` 张量且全反对称。这里，`n` 是整数且在 `[0, N]` 中。如果 `n=0`，则得到 `T00` 张量，即标量。否则，对于元素 `vi` 和 `vj` 的任意换位，`f (v1, v2, …, vn)` 的符号（正或负）发生变化。对于偶数次换位，用加 1 乘以 `f`；否则使用 −1。如果考虑 `k> N` 的 `k` 形式，它们为零。因此非平凡的 `k` 形式存在于 `k` 小于或等于 `N` 时。当 `k=N` 时，得到顶次形式。

顶形式是 `T0n` 形式，其中 `n=N`。当此条件成立时，存在非零的 `f` 和 `g`，两者均为顶形式；则存在标量 `c` 使得 `g=c f`。这成为一个等价类。选择这样一个顶形式 `f` 称为 `V0N` 上的体积。具有选定顶形式的向量空间称为具有体积的向量空间。当 `v1, v2, …, vN` 是 `V0N` 中的 `N` 个向量时，据定义，这些向量张成的体积为 `vol (v1, …, vN)=f (v1, …, vN)`。

行列式取自同态 `A` 并得到一个标量。它利用 `V0N` 的基底，例如 `e1, e2, … eN`，以及 `V0N` 上的某个体积形式 `f`。它定义为 `det A=f (A (e1), A (e2), …, A (eN))/ f (e1, e2, …, eN)`。(Lee, 1997; Sakai, 1995)

### 示例 4.15

考虑自同态 `A: C² → C²`，使用对角矩阵 `D` 定义，主对角线上有一个非零标量 `c`，随后为 1。所以 `D=`

```
$|\\begin{matrix} c & 0 \\\\ \\end{matrix}|$
```
![方程](img/F000011si133.png`)

```
$|\\begin{matrix} 0 & 1 \\\\ \\end{matrix}|$
```
![方程](img/F000011si134.png`)

对于任意 `v=(a b)′` 和 `w=(d e)′`，在 `C²` 中以及标量 `α`![方程](img/F000011si135.png`)，则 `D` 保持标量乘法和向量加法。也就是说，

```
D[αv+w]=D(αa+d αb+e)′=(cαa+cd αb+e)′=α(c a b)′+(c d e)′=α D v+ D w.
```
![方程](img/F000011si136.png`)

因此，这是一个向量空间自同态。行列式提供在基底变化下不变的结果。在这种情况下，对于酉矩阵 `U`，当它被使用且满足 `U U*=U*U=I` 时，`D` 的行列式为 `c=det(U D U*)`。

## 4.9 张量代数



张量和只能在具有相同平衡性的张量之间找到。而张量积则可以应用于任意张量。在此情况下，`MSA` 描述中有四种类型，它们是 `SCALAR`、`VECTOR1`、`VECTOR2` 和 `VECTOR12`。第一种类型如前所述表示复数域中的标量。接下来的三种类型再次表示向量空间中的向量；在此情况下，向量实际上是张量。张量积将利用来自张量空间 `VECTOR1` 和 `VECTOR2` 的张量，从而得到 `VECTOR12` 中的张量。

除了向量空间和域之前的所有签名集之外，还有一个额外的签名集。它有一个运算符名称，实际上是张量积；它是 `T-MULT`，元数为二。图 4.7 说明了此运算。`SCALAR` 的载体集由所有复数组成。`VECTOR1` 的载体集是 `Vpq` 中所有 `Tpq` 向量的集合，而 `VECTOR2` 的载体集是 `Vrs` 中所有张量 `Trs` 的集合。所有这些张量的向量空间是一个幺元结合的交换代数。在此情况下，`V-ADD` 运算用于具有完全相同平衡性的两个张量的加法。

![图 4.7 涉及张量的运算。](img/F000011f04-07-9780443136979.jpg)
图 4.7 涉及张量的运算。

实际的张量积 `T-MULT` 用 ⊗![方程](img/F000011si137.png) 表示。这里，`Tpq` ⊗![方程](img/F000011si138.png) `Trs` 是一个 (p + r, q + s) 张量。多值图 图 4.7 说明了张量上的这些运算。

```
(Tpq ⊗ Trs) (v1, v2,…,vp, …vp+r, f1, f2,…fq, …fq+s)=Tpq (v1, …, vp, f1, …, fjq) x Trs (vp+1, …, vp+r, fq+1, …, fq+s)
```
其中乘法在复数域中进行。这表明张量积运算是可交换的。此图中未显示复数域结构，以及 图 1.2 和 4.6 中已给出的所有向量空间和张量运算。

### 示例 4.16
考虑复数域上的两个 (1, 1) 张量 `S` 和 `T`。另外，设 `f` 是 `V*` 中的一个协向量，`v` 是 `V` 中的一个向量。还假设 `c` 是一个复数值。则 `V` ⊗![方程](img/F000011si140.png) `V*`={ `T`，使得 `T:V* x V→ C` }，由此可知 `V` ⊗![方程](img/F000011si141.png) `V*` 是一个向量空间：

(`S`+`T`) (`f`,`v`) = `S`(`f`,`v`) + `T`(`f`,`v`)

![方程](img/F000011si142.png)

(`c``T`) (`f`,`v`) = `c``T`(`f`,`v`)

![方程](img/F000011si143.png)

所有等式恒等式都成立，特别是 `T=0` 是零，即它是向量空间的 `T-ZERO` 或 `V-ZERO`。

在 `Vpq` 中，设维数有限，记为 `N`，则令 `e1`、`e2`、…、`eN` 为 `V=V10` 的基，`f1`、`f2`、…、`fN` 为 `V*=V01` 上先前找到的对偶基。请记住，此协向量对偶基是从双正交条件得到的。因此张量可以写成 `Tpq` (`f1`、`f2`、… `fp`、`e1`、`e2`、… `eq`)。此外，张量 `Tpq` 可以从其分量重构，使用 `r=e1 ⊗ e2 ⊗ … ⊗ep ⊗ f1 ⊗ f2 ⊗ … ⊗ fj`。更多细节以及张量运算的示例将在下一节给出。

## 4.10 希尔伯特空间张量积的多排序代数
接下来从高层视角给出希尔伯特空间 `H1` 与希尔伯特空间 `H2` 的张量积的 `MSA` 描述。它也是一个希尔伯特空间。类型以显而易见的方式给出；它们是 `SCALAR`、`VECTOR1`、`VECTOR2` 和 `VECTOR12`。签名集与希尔伯特空间的完全相同，只是需要一个额外的签名集来提供张量乘法。该签名集有一个名为 `T-MULT` 的二元运算符名称。它满足：

* `T-MULT`: `VECTOR1 x VECTOR2 → VECTOR12`.

与之前的 `MSA` 高层表示一样，记作：

* `V-ADD` by `+`
* `S-MULT` by `x`
* `T-MULT` by `⊗`![方程](img/F000011si144.png)
* `SCALAR` by `c`
* `VECTOR1` by `v1, w1`
* `VECTOR2` by `v2, w2`

此外，希尔伯特空间的所有等式恒等式在此结构中均成立，并附带额外的等式约束：

1. 1) 线性：`c x (v1 ⊗ v2)=(c x v1) ⊗ v2=v1 ⊗ (c x v2)`.
2. 2) 分配律：`(v1 + w1) ⊗ w2=v1 ⊗ w2 + w1 ⊗ v2`.
3. 3) 分配律：`v1 ⊗ (v2 + w2)=v1 ⊗ v2 + v1 ⊗ w2`.
4. 4) 内积：`<v1 ⊗ v2, w1 ⊗ w2>=< v1, w1> <v2, w2>`.

在这些约束下，`VECTOR12` 成为由 `H12` 表示的希尔伯特空间。多值图 图 4.8 说明了产生 `VECTOR12` 的运算 `T-MULT`。同样，类型 `SCALAR` 未显示，也没有涉及希尔伯特空间的任何运算名称，除了 `T-MULT`。此外，类型 `VECTOR1` 和 `VECTOR 2` 分别用 `H1` 和 `H2` 表示。

![图 4.8 希尔伯特空间的张量积。](img/F000011f04-08-9780443136979.jpg)
图 4.8 希尔伯特空间的张量积。

为准备张量希尔伯特空间的简单示例，考虑希尔伯特空间 `H1=H2=C²`={|v>}，即所有 ket 的集合。因此，此处的载体集是所有 2×1 复值列向量的集合。在 `C²` 中，该空间中最一般的归一化单量子比特由 ket 给出：`|v>=e^(iq) [cos (t/2)|0> + e ^(ip) sin (t/2)|1>]`，p、q 在 `0, 2 *π*![方程)`，t 在 `0, *π*![方程]`。在 `C²` 中，ket `|v>` 的二对一向量由 `|v>=(e^(iq) cos (t/2)e^(iq) e ^(ip) sin (t/2))′` 给出。

如前所述，请注意此 ket 的范数为一。使用内积可知范数平方为 `‖|v>‖²\=‖e^(iq) ‖² \[(cos (t/2)² + (sin (t/2))²\]=1`。该空间中的所有其他 ket 都等于此形式的两个不同 ket `|u>` 和 `|v>` 的线性组合。对于纯元素，结果 ket 的系数必须使用系数的绝对平方值之和为一。例如，设 `|w>=a |u> + b |v>`，其中 `a` 和 `b` 在 `C` 中；则 `|a |² + |b |²\=1`。这些元素出现在下一章所述的非常重要布洛赫球的表面上。利用 `H1 ⊗ H2` 的最具启发性的低层视图之一在下一个示例中给出。

### 示例 4.17
设 `VECTOR12` 的载体集为 `H1 ⊗ H2=C² ⊗ C²=C⁴`，它是两个量子比特的空间，也是四维复值列向量的空间。在 `H1` 中，使用基，`v1=1/2^(1/2) (|0> + |1>)=1/2^(1/2) (1 1)′`，且 `w1=|0>=(1 0)′`。也在 `H2` 中使用基，`v2=3/5 |0> −4i/5 |1>=(3/5 –4i/5)′`，且 `w2=i |1>=(0 i)′`。将求出来自 `H1` 和 `H2` 的单个基元素的张量积。因此将有四个这样的乘积。为简化表示，将采用 `C⁴` 中的表示。在此情况下，如果 `v = (a b )' ` 且 `w = ( c d )' ` 在 `C²` 中，则 `v` 和 `w` 的张量积 `u` 为 `u = ( ac\* ad\* bc\* bd\* )' ` 在 `C⁴` 中。星号表示复共轭。



结果在用 `C⁴` 表示时变得可理解。`C⁴` 中一个易于使用的基是 `|0 0>=(1 0 0 0)′`、`|0 1>=(0 1 0 0)'`、`|1 0>=(0 0 1 0)'` 和 `|1 1>=(0 0 0 1)'`。因此，`T-MULT(v1, v2) =` `v1` ⊗![方程](img/F000011si161.png) `v2` `=1/2^(1/2) (3/5 4i/5 3/5 4i/5)′`。此外，`w1` ⊗![方程](img/F000011si162.png) `w2` `=(0 −i 0 0)′`。另外，`v1` ⊗![方程](img/F000011si163.png) `w2` `=−i/2^(1/2) (0 1 0 1)′` 且 `w1` ⊗![方程](img/F000011si164.png) `w2` `=(3/5 4i/5 0 0)′`。所有先前的结果都可直接使用 ket 求得。请注意 `‖v1 ⊗ v2‖=1/2 [(3/5)² + |4i/5|² + (3/5)² + |4i/5|²]=1`。类似地，`‖w1` ⊗![方程](img/F000011si165.png) `w2‖=1`，对于之前指定的所有其他张量积也同样成立。

### 例 4.18

设 `VECTOR` 的载体集合为所有复值 2×1 列向量的集合，这再次是 `H1=C²`。涉及 `H1` ⊗![方程](img/F000011si166.png) `H1` 的张量也可以很容易地找到。`|u>=(1/ 2^(1/2)) (|0> + |1>)` 与 `|v>=(1/ 2^(1/2)) (|0> − |1>)` 的张量积将被确定。它是 `|u>` ⊗![方程](img/F000011si167.png) `|v>` `=1/2 (|0>` ⊗![方程](img/F000011si168.png) `|0>` `− |0>` ⊗![方程](img/F000011si169.png) `|1>` `+ (|1>` ⊗![方程](img/F000011si170.png) `|0>` `− |1>` ⊗![方程](img/F000011si171.png) `|1>`)`。这可以写成：`w=1/2 (|0, 0> − |0, 1> + |1, 0> − |1, 1>)`。请注意所得的张量积的范数也为一。这可以通过直接使用 bras 和 kets 并观察它们何时正交且归一化来看出。因此，`<w,w>=1/4 <<0, 0 | − <0, 1 | + <1, 0 | − <1, 1 |, |0, 0> − |0, 1> + |1, 0> − |1, 1>>`。这可以展开为十六个内积。十六个内积中的每一个随后将使用张量希尔伯特空间的等式恒等式编号四来计算。`4) Inner Product: <v1 ⊗ v2, w1 ⊗ w2>=< v1, w1> <v2, w2>`。

为了深入使用前面提到的内积来理解这一点，首先取第一个 bra 中的第一个元组，并将其与 ket 中的四个第一个元组中的每一个形成内积。结果为 `<0, 0>=1`、`<0, 0>=1`、`<0, 1>=0`，最后 `<0, 1>=0`。接下来形成第一个 bra 中第二个元组与 ket 中四个第二个元组中的每一个的内积。这给出 `<0, 0>=1`、`<0, 1>=0`、`<0, 0>=1` 和 `<0, 1>=0`。跟踪这两个结果然后按对应顺序相乘这些条目会得到除一项外全为零，即 `<0|0> <0|0>=1`。也就是说，其余三个乘积为零。对其他 bra 重复此过程将在按顺序相乘时在每个乘积中得到单一值 1。因此，`<w,w>=1/4 (<0|0><0|0> + <0|0><1|1> + <1|1><0|0> + <1|1><1|1>)=1`。

## 4.11 射线的希尔伯特空间

接下来两个希尔伯特空间的例子包含了状态的射线概念。这首先使用射影希尔伯特空间概念来描述。第二个例子利用了有序域和凸锥。两个例子都假设状态是纯态。

### 例 4.19

考虑一个固定的复希尔伯特空间 `H`。在 `H` 上的投影得到 `H` 的子集 `M`，`M={v, w, nonzero, such that v=a w for some nonzero constant, a in C}`。这将射线定义为等价类。该结构满足自反、对称、传递（RST）等价关系。为了说明这是一个关系，假设 `v`、`w` 和 `z` 均在 `M` 中非零；另设 `a` 和 `b` 在 `C` 中非零。以下约束均成立：

* 自反：`v=1 v`。
* 对称：`v=a w`，蕴含 `w=1/a v`，因为 `a` 非零。
* 传递：`v=a w`，`w=b z`，蕴含 `v=a b z`；因此所有 RST 关系均成立。

零向量不在此结构中，因此 `M` 不是子向量空间。它甚至不是加法群胚。这是因为如果 `v=a w` 和 `v=−a w` 同时相加，则会得到零向量。可能存在许多像 `M` 这样的子集，它们构成了希尔伯特空间 `H` 中的射线。

每个这样的射线可以被认为由一条直线的两个无限线段组成。该直线穿过 `H` 中的零点且不包含它，但包含该直线上的所有其他点。特别地，如果 `H=C²`，则该情况下的投影是复投影线，也称为布洛赫球，在下一章中描述。Hopf 纤维化也在后面描述，提供了与布洛赫球相关的结论的底层理论，并在关于纤维丛的 第 10 章 中提到。

将前一例的结果推广到 n 量子能级系统会得到等价类，可以被视为穿过但不包括 `C^(n)` 中原点的复直线。这些直线形成复射影空间 `CP^((n−1))`，即 `(C^(n) − {0}) / (v ~ av)`，其中 `a in C` 非零。`CP^((n−1))` 与 n 维量子系统之间存在一一对应关系。单个量子比特位于 `CP¹` 中。对射影空间的更深入介绍将在下一个例子中给出。它将涉及证明简单向量与其自身的外部乘积是半正定的，或称非负定的。

### 例 4.20

在此例中，考虑希尔伯特空间 `Hr`，其中类型 `SCALAR` 的载体集合为实域 `R`。实域是有序域。此外，对于 `R` 中任意两个元素 `a` 和 `b`，三种情况之一成立。或者 `a <b` 或 `b <a` 或 `a=b` 为真。此外，涉及关系小于或等于的排序是自反和传递的。而且它是反对称的，即如果 `a` 小于或等于 `b` 且 `b` 小于或等于 `a`，则 `a=b`。此外，使 `R` 成为有序域的定义等式不等式涉及以下约束：

1. `1) Additive: if a <b, then a + c <b + c`.
2. `2) Multiplicative: If 0 <a and 0 <b, then 0 <a ⋅`![方程](img/F000011si174.png)` b`.

回想一下，两个向量的外部乘积得到一个矩阵。现在，我们证明迹类算子、密度函数或纯态；`|v> <v|` 是一个实值非负定矩阵。这将通过证明该矩阵的关联二次型是非负定的来说明。

因此考虑 `C²` 中的量子比特 `|v>=(a b)′`，则 `|v> <v |=(a b)′ (a\* b\*)=M`，二次型 `Q=(x y) M (x y)′=(a a\* x + b a\* y a b\* x + b b\* y) (x y)′=a a\* x² + 2 Re (a b\*) x y + b b\* y²`，其大于或等于零。这表明矩阵 `M` 是半正定的。`M=| v> <v |=`

$|\\begin{matrix} {\\text{aa} \\ast} & {\\text{ab} \\ast} \\\\ \\end{matrix}|$

![方程](img/F000011si175.png)

$|\\begin{matrix} {\\text{ba} \\ast} & {\\text{bb} \\ast} \\\\ \\end{matrix}|$

![方程](img/F000011si176.png)

最后，`M` 也是 `Hr` 中凸锥中的一条射线。凸集是指包含集合内任意两点的线段也完全包含在集合内。锥是 `Hr` 有序域的一个子集。对于子集中的任意元素 `P` 和标量 `a`，其中 `a` 在 `R` 中非负，则 `a P` 在子集中。凸锥是指对于 `R` 中任意非负 `a`、`b` 以及锥中的任意 `P` 和 `Q`，`a P + b Q` 仍在锥中的锥。

## 4.12 射影空间



对于希尔伯特空间 `H`，在域 `C` 上，可以定义一个相关的射影空间 `PH`。它是 `H` 中所有射线 `L` 的集合，其中 `PH={L, such that L is a complex one-dimensional subspace of H}`。考虑 `H − {0}`，其从 `H` 继承的拓扑，并设 `T: (H − {0})→ PH`。然后，在每个射线 `L` 上选择一个非零点表明 `T` 是一个满映射。此外，选择 `PH` 关于 `T` 的终拓扑使得 `PH` 成为一个拓扑空间。这里，在终拓扑中，`PH` 中的开集 `U` 是那些 `T^(−1) (U)` 在 `H − {0}` 中开的集合。对于 `H − {0}` 中的 `v`、`w`，等价关系可以定义为 `v ~ w` 意味着 `v=aw`，其中 `a` 为 `C` 中的非零元。等价类在 例 4.19 中进行了说明。记商空间 `(H − {0})/~` 为 `H~`，并定义商映射 `T~: (H − {0}) → H~`。这产生了一个唯一的同胚 `M`，`M: H~ → PH`。`H − {0}` 中的元素通常被称为态矢量，而 `PH` 的元素 `L` 被称为射线。当存在单位范数时，它们被称为纯态。

射影希尔伯特空间从 `H` 继承了一个内积。在这种情况下，二元函数 `IN: PH x PH → [0, 1]`，并且对于 `H − {0}` 中的 `v`、`w`，则 `IN(v,w)=|<v,w>|/(‖v‖‖w|)|`。

### 例 4.21
当量子系统被制备为处于 `PH` 中的态 `v` 以进行测量且可观测量态为 `PH` 中的 `w` 时，则该事件的概率被解释为 `IN(v,w)²`。

当 `H` 的维数大于一时，`PH` 是一个完备的半度量空间，其半度量由 `d: PH x PH→ [0, infinity]` 给出，其中对于 `PH` 中的 `L`、`K`，距离 `d(L,K)=inf ‖v − w‖`，其中 `v` 在 `L` 中，`w` 在 `K` 中，且 `‖v‖=‖w‖=1`。

### 例 4.22
若 `H=C²`，射影空间 `PH` 是通过复平面 `C` 原点的所有直线集合。特别地，若 `L` 为 y 轴且 `K` 为 x 轴，则 `d(L,K)=2^(1/2)`。这是因为采用了单位长度，且点 `(1, 0)` 到点 `(0, 1)` 的距离为 `2^(1/2)`。

Fubini-Study 度量 `D` 在射影希尔伯特空间上定义（Sakai, 1995）。它是前一示例中 `d` 的等价度量。Fubini-Study 度量是这样的 `D: PH x PH → [0, infinity]`，其中 `D(L,K)=arccos(|L,K|)`。等价性由不等式表明：对于 `PH` 中所有的 `L` 和 `K`，`d(L,K)` 小于或等于 `D(L,K)`，即小于或等于 `2^(1/2) d(L,K)`。

可以在射影空间中定义等距映射。若 `PH1` 和 `PH2` 是射影空间，则 `A: PH1 → PH2` 被称为等距映射，只要它是保距的，`|<A(L), A(K)>|=|<L, K>|`，对所有 `L` 和 `K` 在 `PH1` 中成立。等距自同构是一个映射 `A`，其中 `A: PH → PH` 当 `A` 为 1–1、满等距时。这也称为 Wigner 自同构或量子系统的对称性（Chevalier, 2007）。存在许多类型的等距映射，如平移、旋转和反射，以及滑移反射，即关于一条线的反射后跟平移。这些对称性形成一个群。不同的等距映射被描述为线性，只要 `A` 满足：
1. 1) Additive: `A (L + K)=A (L) + A (K)`.
2. 2) Homogeneous: `A(aL)=a A(L)`, for `a` in `C`.
然而，如果 (1) 成立且
* 2′) Conjugate Homogeneous: `A(aL)=a\* A(L)`,
则等距映射被称为共轭线性。Wigner 的一个定理涉及维数大于一的希尔伯特空间中的等距映射。对于等距映射 `A: PH → PH`，存在一个线性或共轭线性的等距映射 `S` 使得 `S: H → H`。此外，`A=S′`，它是 `PH` 上的等距映射，将射线 `cv` 映射到射线 `cSv`，对于 `v` 在 `H−{0}` 中。

重要的是提及一个相关主题，即反幺正或共轭线性幺正运算。特别地，对于满足下面三个条件的双射 `T: H → H`，算子被称为反幺正映射；这里 `a` 和 `b` 在 `C` 中且 `v` 和 `w` 在 `H` 中：
1. 1) Adjoint Inverse: `T T*=T* T=I`.
2. 2) Additive: `T(v + w)=T(v) + T(w)`.
3. 3) Conjugate Homogeneous: `T(a v)=a\* T(v)`.
用内积表示，这通常被压缩为：
4. 4) Inner product, `<T(v), T(w)>=< v, w>*`.
然而，最后一种表示是有用的，但必须注意，因为本文档中的所有算子都被假定为线性，除非另有说明。

### 例 4.23
若 `T` 为反线性，则 `T^(−1)` 也是如此。对于非零，`T^(−1)(av) = w` 意味着 `av = T(w)`，或 `v = 1/a T(w) = T(1/a\* w)`。由此 `T^(−1)(v) = 1/a\* w`，或 `w = a\* T^(−1)(v)`，从而表明逆也是反线性的。还可得出 `T^(−1) (i) T=−i T^(−1)T=−i`。

## 参考文献
* Adler, 2015 Adler J. *线性代数应该这样做*. 978-3-319-11079-0: Springer; 2015;.
* Chevalier, 2007 Chevalier C. *Wigner 定理及其推广*. *量子逻辑与量子结构手册* Elsevier 2007;429.
* Halmos, 1958 Halmos P. 0-387-90093-4 *有限维向量空间* 1st ed. Van Nostrand 1958;.
* Lang, 2002 Lang S. 978-0-387-95385-4 *代数，研究生数学教材*. vol 211 Springer-Verlag 2002;.
* Lee, 1997 Lee J. 978-0387-98322-6 *黎曼流形* Springer Verlag 1997;.
* Mac Land and Birkhoff, 1999 Mac Land S, Birkhoff G. *代数*. 0-8218-1646-2: AMS Chelsea; 1999;.
* Sakai, 1995 Sakai T. Mathematical Monographs No. 149 *黎曼几何* American Mathematics Society 1995;.
* Spivak, 1990 Spivak M. *微分几何综合导论* Houston: Publish or Perish, Inc.; 1990;.

# 第 5 章

## 量子和机器学习应用涉及矩阵

## 摘要
在本章中，指定了涉及矩阵的若干运算，以及所涉及的种类和运算的 MSA 多元图描述。说明了量子位及其矩阵表示。定义了泡利矩阵以及涉及布洛赫球上旋转的应用。描述了交换子，即李代数中的乘法运算，并附有示例。引入了混合态的概念，以及它在布洛赫球内的位置。定义了具有复系数的量子位，再次强调布洛赫球。描述了楔积和内积及其应用。接下来，使用 Frobenius 协变式以及 Lagrange-Sylvester 方法来求矩阵的函数。随后是主成分变换，以及主成分变换中使用的核方法。本章的最后一节描述了奇异值分解，并提供了说明分解过程的示例。

### 关键词
Qubits; Bloch sphere; Bloch ball; Pauli matrices; Lie derivative; spectrum of matrices; Frobenius covariants; principal component analysis; singular value decomposition

## 5.1 矩阵运算
图 5.1 中的多元图提供了涉及种类 `MATRIX` 的若干运算名称的全局视图。这些名称是在 n×n 复值矩阵 `M` 的上下文中。图中包含 n 维复希尔伯特空间的 `KETS`，以及相同的或对偶空间的 `BRAS`，以及复 `SCALAR` 域。为了使图表不杂乱，图中省略了先前为希尔伯特空间以及复数域提及的所有运算名称。还省略了所有用于定义 `MATRIX` 的幺半结合代数结构的算子名称，如 图 3.1 中所述。

![图 5.1 涉及矩阵运算的多元图.](img/F000084f05-01-9780443136979.jpg)



## 图 5.1 涉及矩阵运算的多元图。

`MATRIX` 结构在当前情况下的算子序列为 (0, 7 (4, 3), 0,1) 且可与图 3.1 对应。存在七个一元运算名称和一个三元运算名称。这是三元算子名称的首次出现。事实是，使用三元算子可以给出许多其他运算。例如，即使量子技术中最基本的结构之一也可以这样定义。也就是说，可以利用单个三元运算定义一个阿贝尔群；在这种情况下，它通常被称为堆 (Hollings 和 Lawson, 2017)。

对于 `MATRIX` 结构，其签名集内的所有算子名称如下给出。我们从以下开始：

`TrinaryOpertation`: `TRI`: `BRA`×`MATRIX`×`KET`→`SCALAR`.

![Equation](img/F000084si1.png)

这是一个共轭三线性形式。在复数情况下，`TRI` 仅在其后两个参数上是线性的。在实数情况下特别重要的是当 bra 和 ket 相等时。在这种情况下的解释是使用 `v` 使得 `<v|=|v>∗`。结果得到一个二次型，`<v|M|v>`。无论如何，请注意在图中，对应箭头的尾部用斜线标记，对应于 `TRI` 的运算元顺序。顺序如下：首先是 `BRA`，然后是 `MATRIX`，最后是 `KET`。

接下来的四个运算名称都属于同一个签名集；它们在以下段落中描述。

`UnaryOperation`: `DET`: `MATRIX`→`SCALAR`.

![Equation](img/F000084si2.png)

行列式先前已在涉及向量空间自同态的 第 4.8 节 中引入。它将在后续章节中再次提及。自同态方法为行列式产生无分量求值公式。然而，在不太抽象的设置中，行列式也被称为（在标量乘法意义下唯一）交替多线性泛函。行列式在 Fock 空间中非常重要。这里，Slater 行列式用于提供费米子计数状态以及纠缠存在性。

接下来，另一个重要的矩阵运算对应于迹运算名称；它是这样的：

`UnaryOperation`: `TRACE`: `MATRIX`→`SCALAR`.

![Equation](img/F000084si3.png)

迹将在后续部分中从更全局的观点给出。它涉及张量积的收缩。矩阵的迹在量子领域中使用统计和概率方法时起着至关重要的作用。平均值基于使用密度矩阵的迹。后续章节提供了插图和示例。

永久运算名称是这样的：

`UnaryOperation`: `PERM`: `MATRIX`→`SCALAR`.

![Equation](img/F000084si4.png)

永久与行列式相似，但它不使用 Leibniz 规则中计算行列式时的一和负一交替符号。它保持所有符号等于正一。永久也在 Fock 空间中用于计算玻色子的数量。

范数具有以下给出的运算名称：

`UnaryOperation`: `NORM`: `MATRIX`→`SCALAR`.

![Equation](img/F000084si5.png)

这里，`NORM` 表示矩阵的范数。它是一个全局术语。然而，对于矩阵存在的许多不同的范数中，以下仅提及 Hilbert-Schmidt 或 Frobenius 范数。在这种情况下，‖`M`‖ 等于所有矩阵元素绝对值平方之和的平方根。该范数被选中的原因是它可用于说明载体集为 `MATRIX` 的 Banach 代数。

最后三个算子名称都是单目且都属于同一个签名集。

它们如下：

`TRAN`,`CONJ`,and`INV`theyllmap: `MATRIX`:→`MATRIX`.

![Equation](img/F000084si6.png)

`TRAN` 是矩阵的转置，`CONJ` 是共轭转置，而 `INV` 是部分逆，其真正定义域是行列式非零的那些矩阵。请注意 图 5.1 中的虚线箭头。如果 sort `MATRIX` 表示一般线性群 `GL` (`n`, `C`) 或 `GL` (`n`, `R`) 中的元素，即行列式非零的 n×n 矩阵，则它将是实线箭头。

应指出，转置（`TRAN`）一词仅适用于矩阵。一般而言，对于线性算子，伴随运算取代转置。这些事实稍后会再次提及。伴随将与转置类似地执行。对于矩阵 `M`，其中 `M`: `C^n` → `C^m` 且 `M` 是 m 行 n 列矩阵，则对于 `v` 在 `C^(*m*)` 中和 `w` 在 `C^(*n*)` 中，内积用作 `<v,Mw>=v∗Mw=(M′ v^(*c*))′ w=<M∗v,w>`。星号 (`∗`) 是共轭转置。指数 (`^(*c*)`) 是共轭。当使用实数标量域代替复数域时，任何实数的共轭是其本身且 (`∗`)=(`′`)。

下一个示例说明了涉及复数量的转置的使用。在此示例中，(`^(*c*)`) 指共轭运算。

### Example 5.1

设 `VECTOR` 的载体集为 `C²` 和 `C³`，且其中 `n=3` 且 `m=2`。设 `MATRIX` 的载体集为所有 2×3 复值矩阵，并设 `M`: `C³` → `C²`，其中 `M`=

$\\begin{array}{lll} {|0} & i & {2|} \\\\ {|1} & 0 & {0|} \\\\ \\end{array}$

![Equation](img/F000084si7.png)

对于 `v` 在 `C²` 中，其中 `v=(2i −1)′`，和 `w` 在 `C³` 中，`w=(3i −2i 1)′`，则 `<v, M w>=<(2i −1)′, (4 3i)′>=(−2i −1) (4 3i)′=−11i=v∗Mw`。量 `M′v^(*c*)\=(−1 2 –4i)′`，相应地，`(M′v^(*c*))′=(−1 2–4i)` 且 `(M′v^(*c*))′w=(−1 2 –4i) (3i −2i 1)′=−11i`。最后，`< (M′v^(*c*))^(*C*), w>=<M∗v, w>=<((−1 2 4i)′, (3i −2i 1)′>=−11i.#

## 5.2 Qubits and their matrix representations

如前所述，ket 后跟并乘以 bra 用于表示外积。例如，使用 `M`，一个二乘二复值矩阵且有记号滥用：`M=|v><w|`。下面的示例将说明量子中外积的使用。特别地，将观察到希尔伯特空间中一个归一化向量 `ρ` 写为 `|v><v|=ρ`。该量通常被称为迹类算子、密度函数，甚至纯态。更一般地，外积用作正交投影算子。这里范数为一的 ket `|v>` 使用 `|v><v|` 投影到由 `|v>` 张成的子空间。该重要运算的说明在 MSA 多元图中给出，见 图 5.2。这里使用特殊记号。箭头每个尾部上的一个点表示运算元是所选 sort 或同构 sort 的相同元素。对于手头的情况，相同元素意味着 `|v>=a∗<v|`。图中的算子 `K` 是 1-1、满射、等距、共轭运算，如 图 4.2 所示。ket 后跟 bra 运算在下一个示例中得到动机。在这种情况下，`VECTOR` 的载体集对应于具有通常运算的二维复值向量。作为结果，sort `MATRIX` 的载体集是所有 2×2 复值矩阵的集合。

![Figure 5.2 Illustration of identical operands in polyadic graph.](img/F000084f05-02-9780443136979.jpg)

图 5.2 Illustration of identical operands in polyadic graph.

### Example 5.2



# C² 中的外积

参考 `Example 4.6`，其中基本希尔伯特空间设定为 `C²`。也就是说，`VECTOR` 的载体集合是所有与 kets 相对应的 2×1 复列向量的集合。两个 ket `|r>=(a b)′` 与 `|s>=(c d)′` 的外积是一个 2×2 矩阵 `E`。`E` 的元素如下：`E11=ac∗`、`E12=ad∗`、`E21=bc∗`，以及 `E22=bd∗`。同样的结果也可以通过将 2×1 列向量 `|r>=(a b)′` 与对应于 `|s>` 的 bra 表示的 1×2 行向量 `<s|=(c∗ d∗)` 相乘得到。再次，`|r><s|=` 
$\\begin{matrix} {|{\\text{ac} \\ast}} & {{\\text{ad} \\ast}|} \\\\ {|{\\text{bc} \\ast}} & {{{\\text{bd} \\ast}|}.} \\\\ \\end{matrix}$
![方程](img/F000084si8.png)

考虑 `C²` 中任意三个向量 `u`、`v` 和 `w`。内积 `<w, v>` 乘以 ket `|u>` 等于外积 `|u> ⊗`![方程](img/F000084si9.png) `w>)|` 乘以 ket `v`。也就是说，`<w|v>|u>=(|u> ⊗`![方程](img/F000084si10.png) `w>)|v>`。这就是外积作为秩一算子的通常定义。现在将该恒等式举例说明：例如，设 `u=(a b)′`、`v=(e f)′`，且 `w=(c d)′`。则形成左手边得到 2×1 列向量，`<w|v>|u>=((c∗e +d∗f) a (c∗e + d∗f) b)′`。

接下来，形成右手边（`|u>⊗`![方程](img/F000084si11.png)`|w>)|v>`），它由下面的 2×2 矩阵（`|u>⊗`![方程](img/F000084si12.png)`|w>`）随后是列向量 `(e f)′` 给出，
$\\begin{array}{lll} \\left. \\middle| \\text{ac∗} \\right. & \\left. \\text{ad∗} \\middle| \\right. & \\left| e \\right| \\\\ \\left. \\middle| \\text{bc∗} \\right. & \\left. \\text{bd∗} \\middle| \\right. & {\\left| f \\right|.} \\\\ \\end{array}$
![方程](img/F000084si13.png)

将 2×2 矩阵乘以 2×1 列向量得到一个新的 2×1 向量：
$\\begin{array}{l} {|\\left( {\\text{ac} \\ast e + \\text{ad} \\ast f} \\right)|} \\\\ {{|\\left( {\\text{bc} \\ast e + \\text{bd} \\ast f} \\right)|}.} \\\\ \\end{array}$
![方程](img/F000084si14.png)

由此可知，恒等式（`|u>⊗`![方程](img/F000084si15.png)`|w>)|v>=<w|v>|u>` 成立。#

更一般地，任何列向量（n×1）乘以行向量（1×n），按此顺序，对应于外积。当使用 bras 和 kets 时，必须在 bra 的行表示中使用共轭。在任何情况下，乘法的结果都是 n×n 矩阵。相同阶数的任意 ket-bra 乘法在 n 维希尔伯特空间中提供外积。

以下示例继续使用希尔伯特空间 `C²`，但这次不包含原点，因为态永远不能为零，且任意相位因子被忽略。在量子领域，整体相位差无法检测。接下来提供了 MSA 中简单（纯）态的众多表示和低层视图。就量子应用而言，以下表示最为重要；它是庞加莱或布洛赫球。参见 图 5.3。它推广到李群。特别地，特殊酉群 `SU(2,C)` 是用于操作量子比特的 2×2 矩阵表示。这涉及泡利基以及交换子运算和反对称 Levi-Civita 符号。此外，在正交群 `O(3, R)` 中，纯态由具有不变单位范数的 3×1 列向量给出。关于李群和李代数的代数和拓扑基础的高层视图将在 forthcoming 章节中提供。

![图 5.3 布洛赫球。](img/F000084f05-03-9780443136979.jpg)
图 5.3 布洛赫球。

### Example 5.3

除任意相位外，本例描述了最一般的单量子比特。它是 2×1 向量：`|q>=(cos (t /2) e^(*ip*) sin (t 2))′`，其中 `p` 是 \[0, 2*π*) 中的实数，且 `t` 是 \[0, *π*\] 中的实值。相应地，它可以用 kets 的线性组合写成：`|q>=(cos (t /2)|0> + e^(*ip*) sin (t 2)|1>`。利用外积或投影运算：`|q><q|`，得到 2×2 自伴矩阵。它是正定的，迹为一，具有非负行列式。它是 `|q>` 的一种表示，称为密度矩阵，`ρ`=
$\\begin{array}{ll} {|{\\qquad\\cos^{2}\\left( {t/2} \\right)}} & {{\\sin\\left( {t/2} \\right)\\cos\\left( {t/2} \\right)e^{- ip}}|} \\\\ {|{\\sin\\left( {t/2} \\right)\\cos\\left( {t/2} \\right)e^{ip}}} & {{{\\qquad\\sin^{2}\\left( {t/2} \\right)\\mspace{52mu}}|}.\\#} \\\\ \\end{array}$
![方程](img/F000084si16.png)

上述示例提供了纯态、单量子比特的希尔伯特空间表示。前面提到过，最一般的量子比特已作说明；它由 `e^(*is*) |q>` 给出，其中 `s` 是 \[0, 2*π*) 中的实数，且 `|q>` 如前所述。接下来给出单量子比特最直观也是最重要的表示。它忽略了整体相位 `e^(*is*)`，但涉及布洛赫球并在下文描述。

布洛赫球表面上的点始终是纯态。该点由李群 `O(3)` 中的 3×1 向量 `q` 给出。它使用球坐标或在偏振识别中需要的归一化 Stokes 参数获得。单量子比特的这种表示称为量子比特的球面表示，是 3×1 列向量：`q=(sin (t) cos (p) sin (t) sin (p)cos (t))′`。这里，`t` 表示 \[0, *π*\] 中的（仰角、纬度类型）角度，且 `p` 是 \0, 2 *π*) 中的（经度类型）角度。特别重要的是北极和南极。它们分别通过使用 `t=0` 和 `t=*π*`、`p=0` 得到，从而分别得到 kets `|0>` 和 `|1>`。参见 [图 5.3。例如，使用 `|q>=(cos (t/2) e^(*ip*) sin (t 2))′`，当 `t=0` 时，得到 `|0>=(cos (0 /2) e^(*ip*) sin (0 2))′=(1 0)′` 在 `C²` 中。此外，该量子比特的球面表示为 `q=(sin (0) cos (p) sin (0) sin (p) cos (0))′=(0 0 1)′`。在三维中，这就是 x=0、y=0 且 z=1；它表示北极。对 `|1>` 可以给出类似的表示。在这种情况下，布洛赫球上的表示为 (0 0–1)，这就是南极。

下一个表示涉及三个泡利矩阵：`s1`、`s2` 和 `s3`。连同 2×2 单位矩阵，这四个矩阵构成了所有 2×2 复自伴矩阵希尔伯特空间的正交基。因此，对于任意自伴矩阵 `T`，即 `T=T∗`，有 `T=n[1] I + n[x] s1 + n[y] s2+ n[z] s3`，其中所有 `n[j]` 都是实数。

泡利矩阵按顺序 `s1`、`s2` 和 `s3` 给出如下：
$\\begin{array}{lll} {|{0 1}|} & {|{0 - i}|} & {|{1 0}|} \\\\ {|{1 0}|} & {|{i 0}|} & {|{0 - 1}|} \\\\ \\end{array}$
![方程](img/F000084si17.png)

前面提到的自伴矩阵 `T`，当泡利矩阵被代入时，由下式给出：
$\\begin{matrix} {|{n_{1} + n_{z}}} & {{n_{x} - {in}_{y}}|} \\\\ {|{n_{x} + {in}_{y}}} & {{{n_{1} - n_{z}}|}.} \\\\ \\end{matrix}$
![方程](img/F000084si18.png)

### Example 5.4



# 泡利矩阵密度表示

一般泡利矩阵 `T`，如上所述，将用作密度矩阵 `ρ`。由于 `ρ` 的迹等于一，因此可得 `trace`(`ρ`)=`n[1]` + n[`z`]\+ `n[1]`−n[`z`]\=2 `n[1]`；这意味着 `n[1]`\=1/2。相应地，进行替换，`ρ`\=1/2 `I` + n[`x`] `s1` + n[`y`] `s2` + n[`z`] `s3`。令 `r` 为以下列向量，即 `r`=(2 n[`x`] 2 n[`y`] 2 n[`z`])′。还使用 `s1`、`s2` 和 `s3` 构成泡利列 3 by 1 向量 `s`=(`s1` `s2` `s3`)′。该量实际上是一个 6 by 2 矩阵。当泡利矩阵实际代入列向量 `s` 时，其具有这些维度。另一个重要的表示是 `ρ`\=( `I` +< `r`, `s` >)/2；它是前面提到的 `ρ` 表示的凝缩版本。由于 `ρ` 是半正定的，其特征值非负，因此其行列式也是非负的。这里，`Det`(`ρ`) = `n[1]`² − `n[z]`² − `n[x]`² − `n[y]`²![方程](img/F000084si19.png) 大于或等于零。因此，1/4 大于或等于 `n[z]`² + `n[x]`² + `n[y]`²![方程](img/F000084si20.png)。这意味着 |`r`|² 小于或等于一。当 |`r`| = 1 时，得到纯态，且是布洛赫球面上的点。当 |`r`| < 1 时，这表示混合态，且是布洛赫球内部的点。示例 5.8 说明了布洛赫球中心的最大线性混合态。

### 示例 5.5

本示例将说明 `s2` 泡利矩阵作用于典型量子比特 `|q>`=(cos (`t`/2) e^( `ip` ) sin (`t`/2))′ 时的效果。该量子比特位于布洛赫球面上，因为其范数为一。第一步是形成矩阵 `s2` 乘以该向量：`s2` `|q>`=`s2` (cos (`t`/2) e^( `ip` ) sin (`t`/2))′=(−i e^( `ip` ) sin (`t`/2) i cos (`t`/2))′。整体相位无关紧要，所以提取出 −i e^( `ip` ) 给出 `s2` `|q>`=(sin (`t`/2)−e^(− `ip` ) cos (`t`/2))′ 当该整体相位被舍去时，即被忽略。该量可以写成 (cos ((`t`− `π`)/2)−e^(− `ip` ) sin ((`t` + `π`)/2))′=(cos ((`t`− `π`)/2) e^(− `ip` ) sin ((`t` + 3 `π`)/2))′=(cos ((`t`− `π`)/2) e^(− `ip` ) sin ((`t`− `π`)/2))′。

上述计算表明从应用 `s2`，`p` 变为 minus `p`，且 `t` 变为 `t`− `π`。在布洛赫球上，原量子比特 `|q>` 被变换为新量子比特 `s2`|q> 其新位置具有经度变化从角度 `p` 到 -`p`；此外，纬度变化为 180° 减去其原始角度。因此，对于对给定量子比特的应用 `s2`，存在从量子比特占据的原始半球的半球变化。例如，北极被变换为 `s2` `|0>`=(0 i)′，即南极。提取虚数后得到 `s2` `|0>`=i (0 1)。忽略整体相位给出新的 `t`= `π` 和 `p`=0。另一个例子，考虑原点为南极。所以，`s2` `|1>`=(-i 0)′。将其转换为 -i(1 0)，然后记住整体相位不相关，给出 `s2`|1>=`|0>`。

与上述示例类似，所有泡利矩阵都以涉及三个空间方向的类似方式作用。前面给出的所有泡利矩阵都是厄米对称的，即它们是自伴的并且是幺正矩阵。后一陈述意味着将其中一个矩阵在其任一侧乘以其共轭转置会得到单位矩阵。

### 示例 5.6

将提供一个说明，表明第二个泡利矩阵 `s2` 是自伴的并且是幺正矩阵，即 `s2`=`s2` ∗ 且 `s2` · `s2`∗′=`I`。请注意 `s2` 按顺序给出，下面依次是 `s2`∗ 和 `s2`∗′，其中 ∗ 表示共轭，撇号表示矩阵转置。

```
$\\begin{array}{lll} {|{0 - i}|} & {|{0 i}|} & {|{0 - i}|} \\\\ {|{i 0}|} & {|{- i 0}|} & {|{i 0}|} \\\\ \\end{array}$
```

![方程](img/F000084si21.png)

简单的矩阵乘法验证了 `s2`·`s2`∗′=`s2`∗′ `s2`=`I` 的说法。

现在要给出的 `q` 的最后一个表示是 2 by 2 矩阵 `M`。它是 `SU(2, C)` 李群中的一个元素。矩阵 `M` 涉及三 by one 球面向量 `q` 和三 by one 泡利向量 `s`，如前所述。在这种情况下，它是两个向量的内积。所以，<`q`, `s`>=`M`=sin (`t`) cos (`p`) `s1` + sin (`t`) sin (`p`) `s2` + cos (`t`) `s3`。上述结果中的条目 `sk` 都是 2 by 2 泡利矩阵；它们乘以正弦函数。将正弦函数与代入的 2 by 2 泡利矩阵相乘，将所有内容相加后得到 2 by 2 矩阵 `M`=

```
$\\begin{array}{ll} {|{\\cos\\left( t \\right)}} & {{e^{- ip}\\sin\\left( t \\right)}|} \\\\ {{|e^{ip}}\\sin\\left( t \\right)} & {{{- \\cos\\left( t \\right)}|}.} \\\\ \\end{array}$
```

![方程](img/F000084si22.png)

泡利矩阵通常与前面给出的定义略有不同。应提及，其对应的李代数 `su(2, C)` 就是其中一个例子。在这种情况下，泡利矩阵是归一化的：即 `Sj`=`sj`/2 对于 `j`=1, 2, 3。并且，在该代数中，使用的是交换子算子，而不是常规矩阵乘法。交换子运算为 \[`A` `B`]=`A` `B`-`B` `A`。矩阵乘法实际上在李代数中未定义；它是获得对易运算所需的一个元算子。

### 示例 5.7

作为交换子运算的应用，考虑泡利矩阵：\[`Si`, `Sj`]=`Si` `Sj`−`Sj` `Si`=i `E`[`i` `j` `k`]![方程](img/F000084si23.png) `Sk`。这里，结构常数，也称为反对称列维-奇维塔符号 `E`[`i` `j` `k`]![方程](img/F000084si24.png)，`ijk` 被采用。前面 `i` `E`[`i` `j` `k`]![方程](img/F000084si25.png) 符号中的第一个 `i` 是负一的平方根。符号 `E`[`i` `j` `k`]![方程](img/F000084si26.png) 等于一或负一，取决于 `ijk` 模式经历偶数次或奇数次换位。偶数次换位使用加一，否则使用减一。换位是涉及数值顺序 1、2 和 3 的两个条目的互换。

例如，\[`S[3]` `S[2]`]=`S[3]` `S[2]`−`S[2]` `S[3]`\=−i `S[1]`。首先，出现负号是因为换位数为奇数：1 2 3 变成 3 2 1；使用一次换位，互换 1 和 3。解涉及 `S[1]`，因为交换子使用了 `S[2]` 和 `S[3]`。4 `S[3]` `S[2]` 和 4 `S[2]` `S[3]` 以及 4 (`S[3]` `S[2]`\-`S[2]` `S[3]`) 的乘积按指定顺序说明如下：

```
$\\begin{array}{lll} {|{0 - i}|} & {|{0 i}|} & {|{0 - {2i}}|} \\\\ {|{- i 0}|} & {|{i 0}|} & {{|{- {2i} 0}|}.} \\\\ \\end{array}$
```

![方程](img/F000084si27.png)

将最后一个矩阵乘以 1/4 得到 –i `S[1]`。

混合态是纯态和其他混合态的凸组合。线性组合中的系数始终非负且在此情况下总和为一。这些系数被解释为概率。另一方面，纯态的概率为绝对平方标量系数。设 `|u>` 和 `|v>` 为纯态。此外，假设 `c` 和 `d` 大于或等于零。那么 `|z>`=`c`|u>` + `d`|v>`, 其中 `c` + `d`=1，被称为混合态，且 `c` 和 `d` 可视为概率。由此产生的混合态 ket 在此情况下是其他 kets 的凸组合。这些元素出现在布洛赫球内部。回想一下，布洛赫球是投影空间 `CP¹`=( `C²`−{0})/( `z` ~ `a` `z`) 的表示，其中 `a` 在 `C` 中非零。内部有时称为布洛赫球。于是，混合态位于布洛赫球内。布洛赫球内的原点具有对应于单位一半的状态。它被称为最大线性态。该态不携带关于量子比特的信息。

### 示例 5.8



如前所述，最简单且最重要的混合态示例是最大线性态，`|v> = 1/2 |0> + 1/2 |1> = 1/2 I`。就布洛赫球而言，前文已指出 `|v>` 位于该球的中心。在此情况下，`r = 0`，因为 `ρ = |v><v| = 1/2 I` 且 `ρ = (I + < r, s>)/2`，见 示例 5.4。

## 5.3 布洛赫球的复数表示

纯量子比特可以用 `C` 中的 `u` 和 `v` 表示为 `|q> = u |0> + v |1>`，其中 `|u|² + |v|² = 1`。该表示有时会代替前几节中给出的更流行的表示而使用：`|q> = (cos (t/2) |0> + e^(i p) sin (t/2) |1>`，`p` 在 `[0, 2π)` 中，且 `t` 在 `[0, π]` 中。这里忽略了整体相位，`ϕ` 在 `0, 2π)` 中，因此量子比特的完整描述为 `e^(i ϕ) |q>`。在布洛赫球表示中，`e^(i ϕ) |q>` 映射到 `R³` 中球面 `S²` 上的一个点。相位 `ϕ` 在布洛赫球上不出现。该点的坐标由先前描述的球坐标向量给出。现在它进一步用复系数 `u` 和 `v` 描述，

```
\begin{array}{l}
{X = \sin\left( t \right)\cos\left( p \right) = 2{Re}\left( {u \ast v} \right)}
{Y = \sin\left( t \right)\sin\left( p \right) = 2\text{Im}\left( {u \ast v} \right)}
{Z = \cos\left( t \right) = {|u|}^{2} - {|v|}^{2}}
\end{array}
```

![Equation 将 `u` 与 `cos(t/2)` 相对应，将 `v` 与 `e^(i p) sin (t/2)` 相对应，可为 `X`、`Y` 和 `Z` 恒等式提供依据。使用前面给出的 ket 的密度矩阵为 `ρ = |q><q| = (u |0> + v |1>) * (u |0> + v |1>) = |u|² |0><0| + |v|² |1><1| + u* v |0><1| + v* u |1><0|`。因此密度矩阵 `ρ =````\begin{matrix}{|{|u|}^{2}} & {{u \ast v}|}{|{v \ast u}} & {{{|v|}^{2}|}.}\end{matrix}```![Equation](img/F000084si33.png)

该矩阵的非对角项通常称为相干项。利用变换消除这些项的过程称为退相干。

令 `u = x + i y` 且 `v = z + i t`，其中 `x`、`y`、`z` 和 `t` 为实值，则球面 `S³` 定义如下：`x² + y² + z² + t² = 1`。等价地，`S³` 也可以用两个复数来定义，即使用 `u` 和 `v`，其中 `|u|² + |v|² = 1`。这表明单量子比特希尔伯特空间为 `S³`。在此空间中，`e^(i ϕ) |q>` 是参数 `ϕ` 在 `0, 2π)` 中的圆的方程。布洛赫球与射影空间 `CP¹` 或 `S²` 相对应。

最后，使用外积或投影运算：`|q><q|`，得到纯态密度矩阵的 2×2 矩阵表示，`ρ =`

```
\begin{array}{ll}
{|{\cos^{2}\left( {t/2} \right)}} & {{\sin\left( {t/2} \right)\cos\left( {t/2} \right)e^{- ip}}|}
{|{\sin\left( {t/2} \right)\cos\left( {t/2} \right)e^{ip}}} & {{~\sin^{2}\left( {t/2} \right)}|}
\end{array}
```

![Equation 布洛赫矢量可以写成密度矩阵；也就是说，`ρ` 也可以再次用球坐标表示为 `2 ρ =````\begin{matrix}{|{ 1 + Z}} & {{X - {iY}}|}{|{X + {iY}}} & {{{1 - Z}|}.}\end{matrix}```![Equation](img/F000084si37.png)

如前所述，证明归结为代入。例如，对于矩阵项 `ρ`，使用 `Z = cos(t)`，`1 + Z = 1 + cos(t) = cos² (t/2)/2`。

### 示例 5.9

泡利矩阵 `s1` 的特征值很容易求得，因为特征方程为 `λ² - 2 λ trace (s1) + det (s1) = λ² - 1 = 0`。因此，特征值为 `+1` 和 `-1`。泡利 `s1` 矩阵的本征态或本征向量为 `1/2^(1/2)(|0> + - |1>)`。相应的密度矩阵由 `2 ρ =` 给出

```
\begin{array}{ll}
{|1} & {+ - 1|}
{| + - 1} & {1|}
\end{array}
```

![Equation](img/F000084si42.png)

## 5.4 内导数、外导数和李导数

本节是 第 4.6 节 的延续。本节的主要内容是对李导数的描述。然而，首先将回顾内导数。之前未提及，内导数始终相对于向量场 `X` 指定。对于任意 `n` 形式 `w`，`n > 0`，`(l[X] w) (X2, X3, … Xn) = w(X, X2, … Xn)`。该运算作用于向量场序列 `X2, X3, … Xn`。这与内积相同。结果是一个 `n−1` 形式。对于函数，即零形式，内导数为零。

### 示例 5.10

设 `w` 为 `R²` 对偶空间上的二形式，其中 `w = e¹ ∧ e²`，且设 `X = e[2]`。内积 `(l[X] w) (v) = w (X, v) = (e¹ ∧ e²) (e[2], v) = e¹ (e[2]) e² (v) − e¹ (v) e² (e[2]) = 0 − e¹ (v) 1 = − e¹ (v)`。因此注意到将内导数应用于二形式的结果是一个一形式。

注意，外积，即前一章中描述的楔积，第 4.6 节，与外导数不同，外导数只是 `d` 运算。`n` 形式 `w` 的外导数 `d` 使次数增加一。对于次数分别为 `n` 和 `m` 的二形式 `v` 和 `u`，`w = v ∧ u` 的外导数为 `d w = (d v) ∧ u + (−1)^n v ∧ d(u)`。然而，内导数与外导数之间存在密切关系，下文将描述该关系。

外导数与内导数之间的对偶性由 Cartan 魔法公式 `L[X] w` 给出，其中 `L[X] w = d(l[X] w) + l[X] d w`（Zubelevich, 2012）。在该公式中，`X` 是向量场，`l[X]` 是内导数，`L[X]` 是李导数，`d` 是外导数。最后，对于 `w`，一个 `n` 形式，Cartan 公式可写为 `L[X] w = {d, l[X]} w`。括号 `{A, B}` 是泊松括号。回忆这些括号满足 `{A, B} = A B + B A`。该魔法公式通常用作微分形式空间上李导数 `L[X] w` 的定义。

对于向量场 `X` 上的函数 `f`，李导数是方向导数，`L[X] f = d f · X = X [f]`。沿 `X` 的向量场 `Y` 的李导数满足 `L[Y] X = [X, Y]`，因为 `[X, Y][f] = X [Y [f]] - Y [X [f]]`。此外，它是外导数与 `X` 的收缩，即 `L[X] w = I[X] d w + d(I[X] w)`，这再次是 Cartan 公式。注意李导数也满足莱布尼茨法则：对于 `w = v ∧ u` 且 `X` 为向量场，`L[X] w = (L[X] v) ∧ u + v ∧ (L[X] u)`。



Lie derivatives do not change the degree of the forms they act on. Another way of keeping the degree of the form invariant is to use both the interior and exterior operators since the former lowers the degree, while the latter raises the degree. The order of operation matters, and in any case, Cartan magic formula is an illustration of keeping the degree of the form invariant (Marsden, 2003).

For regular functions `f`, that is, 0 forms, both the exterior and Lie derivatives agree. However, the meaning of derivative is somewhat different for these two operators. A Lie derivative provides a rate of flow or change in a zero form, whereas the exterior derivative can be viewed as the inverse operation of integration (Yano, 1957).

## 5.5 矩阵的谱与 Frobenius 协变矩阵

In finite-dimensional Hilbert spaces `H`, the spectral characteristics of operators `T` are realized by matrices `M`. In particular, the spectral decomposition will be described for matrices with distinct eigenvalues. It involves a superposition of pairwise orthogonal projections onto the eigenspace `Va`, for eigenvalue `a`. So, `Va={a such that T v=a v, v nonzero in H}`.

Let `Pa` be an orthogonal projection onto `Va`. When `a1`, `a2`,…, `an` are the distinct eigenvalues of `T`, the spectral decomposition of `T` is `T=a1 Pa1+ a2 Pa2 +…+ an Pn`. Also, `T²\=a1² Pa1 + a2² Pa2 +…+ an² Pan`. This follows since `Paj` and `Pak` are orthogonal and projections are idempotent. Moreover, for any polynomial involving `T`, `p (T)=p (a1) Pa1 + p(a2) Pa2 +…+ p(an) Pan`. The functional calculus, indicated in later chapters, extends the decomposition from polynomials to continuous functions `f`. One of the most important formulas for functions of a matrix is given next.

The Lagrange-Sylvester interpolation formula is described for a matrix `A`, over the complex field. It is assumed that `A` is a `k` by `k` matrix with distinct eigenvalues. The objective is to find the function `f` of a matrix `A`, that is, `f (A)`. The value `f (A)` is the sum $\\sum\_{i = 1}^{k}{f\\left( {ai} \\right){Ai}}$![Equation](img/F000084si60.png`). In this sum, there appears the product of `f (ai)`, for distinct eigenvalues `ai` of `A`. This quantity multiplies the Frobenius covariants `Ai` (Horn and Johnson, 1991). Each of the `k` covariants `Ai` is found as a product `j=1` to `k` but `j` not equal to `i` of the quotient `(A−aj I)/(ai−aj)`.

### 示例 5.11

As an instance of this formula, consider `k=2` by 2 matrix `A`,

$\\begin{matrix} {|2} & {1|} \\\\ {|3} & {4|} \\\\ \\end{matrix}$

![Equation](img/F000084si61.png`)

The characteristic equation is `(2−*λ*) (4−*λ*)−3=*λ*²–6 *λ* + 5=0`. Then, the distinct eigenvalues are `a1=5` and `a2=1`. In this order, we will find the Frobenius covariants `A1` and `A2`. Since `k=2`, the product will only have one term for each Frobenius covariant. Thus for `A1`, `j` only will equal 2, and therefore `A1=(1/4)(A−I)`. In a similar fashion, for `A2`, `j` only equals 1, and consequently, `A2=−(1/4) (A−5I)`. These Frobenius covariants need to be calculated only once. From this, functions of `A` are found using `f (A)=f (5) A1 + f (1) A2`. This can be done for `f (A)` equal to *e*^(*A*)![Equation](img/F000084si62.png`), `sin (A)`, `cosh (A)`, and so on. As a simple check, `f (A)=A` will first be found. It is `5 A1–1 A2`. The corresponding Frobenius covariants are `4 A1` and `4 A2` given as follows in that order:

$\\begin{matrix} \\begin{matrix} {|\\begin{matrix} 1 & 1 \\\\ \\end{matrix}|} \\\\ {|\\begin{matrix} 3 & 3 \\\\ \\end{matrix}|} \\\\ \\end{matrix} & \\begin{matrix} {|\\begin{matrix} {- 3} & 1 \\\\ \\end{matrix}|} \\\\ {|\\begin{matrix} 3 & {- 1} \\\\ \\end{matrix}|} \\\\ \\end{matrix} \\\\ \\end{matrix}$

![Equation](img/F000084si63.png`)

Multiplying the first matrix above by `5/4` and the second matrix above by `−1/4` and adding them together sums to `A`.

As another simple example, *A*²![Equation](img/F000084si64.png`) will be found. It is `25 A1–1 A2=` $\\begin{array}{rrl} {\\left( {25/4} \\right){|{1 1}|}} & {- \\left( {1/4} \\right){|{- 3 1}|}} & {= \\ {|{7\\mspace{34mu} 6}|}} \\\\ {|{3 3}|} & {|{3 - 1}|} & {{|{18\\mspace{15mu} 19}|}.\\#} \\\\ \\end{array}$

![Equation](img/F000084si65.png`)

A similar formula involving the Frobenius covariants exists for the situation where there exists repeated eigenvalues (Horn and Johnson, 1991).

## 5.6 主成分分析

The Karhunen-Loeve transform (`KLT`), the Hotelling transform, and the principal component analysis (`PCA`) are different names for essentially the same transform method. In machine learning, the terminology is usually referred to as the `PCA`. It is a linear feature reduction technique, and it is often called an unsupervised decomposition algorithm. Being unsupervised, like the `k means` method illustrated in Example 2.1, 第 2.1 节, suggests that it needs an exhausting amount of computation in all applications. This is true. In general, `PCA` is a method for finding the vectors of greatest influence and then reducing the dimension of the data set by removing data related to less influential vectors. `PCA` is called an eigenproblem. The actual solution is centered about finding eigenvectors `v[j]`![Equation](img/F000084si66.png`) and their eigenvalues `λ[j]`![Equation](img/F000084si67.png`). All eigenvectors with the largest absolute value eigenvalues `λ[j]`![Equation](img/F000084si68.png`) are usually retained. Then, the method is to reduce the dimensionality of data by removing eigenvectors possessing small absolute valued eigenvalues. Actually, this is a form of data compression, also called source coding. From a statistical point of view, the `PCA` method is a method for determining the direction that maximizes the variance or correlation of the data.

The `PCA` was invented by Pearson (1901). Early on, the Hotelling transform was used in probability and statistics applications (Hotelling, 1933). Additionally, along with stochastic processes, the `KLT` (Loeve, 1977) found applications in engineering applications.

The reason for using eigenvectors is because they provide directions of principle components. Principal components are always orthogonal to each other, and intuitively they form orthogonal axes. The eigenvalues represent the units of spread captured by each principal components. The `PCA` does not just discard original data; it maps the data into a new feature space. It is in this space that the reduction is performed. As mentioned before, `PCA` is mainly used in dimension reduction, but it is sometimes used for data visualization as well as feature extraction. The algorithm helps identify variables that are dependent and remove them. That is, multicollinearity is identified and dealt with using `PCA`. `PCA` reduces the dimension set, but does not reduce much of the information content when components are discarded.



## 主成分分析概述

`PCA` 还用于降噪，以及异常检测，并作为加密设备。最后一种应用通过使用本文给出的特征向量方法体现出来，但保留所有特征向量，即不要丢弃任何特征向量。它作用类似于哈希编码。此外，如前所述，`PCA` 用于去除随机噪声。在这种情况下，先执行 `PCA`，然后创建逆 `PCA`。应用时，逆结果通常会比原始数据集产生更好的信息含量。异常检测是 `PCA` 的另一个有用应用。它再次涉及对 `PCA` 进行逆运算。执行此操作后，会进行比较以确定原始数据与重建数据之间的差异。当该差异大于应有的差异时，就会检测到异常。也就是说，该差异大于在不存在异常时利用先前比较得到的差异。这里的学习方面仍然是无监督的；无需对数据进行标记。

任意数据集都可以使用 `PCA` 进行降维，但对原始数据中所有数据的预归一化至关重要。通常数据集会被转换使其均值为零。数据集的每一列都被转换成为协方差矩阵。这通常在方差归一化之后发生。然后求出特征值和特征向量。由于协方差矩阵是对称的，其中许多特征向量已经正交。接下来，所有特征向量都被转换到一个 `ON` 系统，即正交且归一化的系统。

对于数据向量 `v[i]`![方程](img/F000084si69.png)，其在单位向量 `u` 上的投影为 `u′v[i]u`，而所有 `v[i]`![方程](img/F000084si70.png) 的平均值按样本型平均值计算，${1/N}\sum_{i = 1}^{N}{v_{i} = v^{-}}$![方程](img/F000084si71.png)。该平均值用 `v^-`![方程](img/F000084si72.png) 表示。因此，所有投影的平均值为 `u′ v^- u`![方程](img/F000084si73.png)，投影的长度为 `u′ v^-`![方程](img/F000084si74.png)。为使投影的方差最大化，最大化 $\\sum_{i = 1}^{N}{{1/N}\\left( {u\\prime v_{i} - u\\prime\\mathit{v}^{-}} \\right)^{2}} = {1/N}u\\prime\\sum_{i = 1}^{N}{\\left( {v_{i} - \\mathit{v}^{-}} \\right){\\left( {v_{i} - v^{-}} \\right)\\prime}u = u\\prime{Pu}}$![方程](img/F000084si75.png)。但存在约束：`u′ u=1`。因此，拉格朗日函数为 `L=u′Pu + λ(1−u′u)`；对 `L` 求导得到以下结果：`2Pu−λ 2 u=0`。求解该方程得到 `Pu=λ u`。这表明 `u` 是特征向量，`u’Pu=λ`；使 `u’Pu` 最大化意味着使特征值 `λ` 最大化。

`PCA` 最常置于概率设定中。目标是找到一个向量 `v[n]`，其来自正交归一集 `{v[1], …, v[r]}`，该向量使方差最大化：`C=v′∑ v`，其中 `v ⊥ {v[1],…,v[j−1]}`![方程](img/F000084si76.png) 且为协方差矩阵。它通常也由样本矩阵近似：$\\sum{= {1/n}}\\left\\lbrack {\\sum_{i = 1}^{n}{\\left( {v_{i} - {1/n}\\sum_{j = 1}^{n}v_{j}} \\right){\\left( {v_{i} - {1/n}\\sum_{j = 1}^{n}v_{j}} \\right)\\prime}}} \\right\\rbrack$![方程](img/F000084si77.png)。请注意，在此表达式中向量 `v[i]`![方程](img/F000084si78.png) 为列向量。

在求出归一化样本协方差矩阵后，应遵循以下步骤来估计此设定下的 `PCA`。求出 `Σ`![方程](img/F000084si79.png) 的所有特征值。它们是实数且可能重复。找到每个不同特征值对应的特征向量。这些特征向量是正交的，并且应归一化。对于重复的特征值，对这些线性无关向量使用 `Gram-Schmidt` 正交归一化过程。用 `w[1]`![方程](img/F000084si80.png) `w[2]`![方程](img/F000084si81.png) 和 `w[n]`![方程](img/F000084si82.png) 表示 n 个归一化特征向量。矩阵 `W` 由所有特征向量的转置组成，即按此顺序 `w[1]′ w[2]′, …, w[n]′`。如果仅使用其中 m 个向量作为矩阵 `W` 的行，则会发生压缩，其中 `m < n`。特征向量应排序。在这里，与最大特征值相关联的向量应置于具有较小特征值的特征向量之前。因此，`W` 的行由转置特征向量的行向量组成，相对于其特征值形成非递增序列。矩阵 `W` 的维度为 `m` × `n`。

实际的 `PCA` 应应用于随机向量 `v=(a b)′`，其中假设 `v` 具有底层概率分布函数 `F`。其均值存在且为零。此外，协方差矩阵必须存在，并且假设其等于样本协方差矩阵。最后，假设随机样本 `v[j]`![方程](img/F000084si83.png) 来自 `F`。在这种情况下，`PCA` 由 `V = W(v−v^-)`![方程](img/F000084si84.png) 给出。这意味着平均值应从向量本身中减去。

### 示例 5.12

设 `n=2`，且样本值给出 `v[1]=(5 9)′` 和 `v[2]=(1 3)′`。然后为归一化 `Σ`![方程](img/F000084si85.png)，形成经验平均值：$v^{-} = {1/n}\\sum_{j = 1}^{n}{x_{j} = {1/2}\\left\\lbrack {{\\begin{pmatrix} 5 & 9 \\\\ \\end{pmatrix}\\prime} + {\\begin{pmatrix} 1 & 3 \\\\ \\end{pmatrix}\\prime}} \\right\\rbrack} = {\\begin{pmatrix} 3 & 6 \\\\ \\end{pmatrix}\\prime}$![方程](img/F000084si86.png)。然后协方差矩阵由样本矩阵近似：$\\begin{matrix} {\\sum{= {1/n}}\\left\\lbrack {\\sum_{i = 1}^{n}{\\left( {v_{i} - {1/n}\\sum_{j = 1}^{n}v_{j}} \\right){\\left( {v_{j} - {1/n}\\sum_{j = 1}^{n}v_{j}} \\right)\\prime}}} \\right\\rbrack = {1/2}\\left\\{ {\\left\\lbrack {{\\begin{pmatrix} 5 & 9 \\\\ \\end{pmatrix}\\prime} - {\\begin{pmatrix} 3 & 6 \\\\ \\end{pmatrix}\\prime}} \\right\\rbrack{\\left\\lbrack {{\\begin{pmatrix} 5 & 9 \\\\ \\end{pmatrix}\\prime} - {\\begin{pmatrix} 3 & 6 \\\\ \\end{pmatrix}\\prime}} \\right\\rbrack\\prime}} \\right.} \\\\ {+ \\left. {\\left\\lbrack {{\\begin{pmatrix} 1 & 3 \\\\ \\end{pmatrix}\\prime} - {\\begin{pmatrix} 3 & 6 \\\\ \\end{pmatrix}\\prime}} \\right\\rbrack{\\left\\lbrack {{\\begin{pmatrix} 1 & 3 \\\\ \\end{pmatrix}\\prime} - {\\begin{pmatrix} 3 & 6 \\\\ \\end{pmatrix}\\prime}} \\right\\rbrack\\prime}} \\right\\} = {1/2}\\left\\{ {{\\begin{pmatrix} 2 & 3 \\\\ \\end{pmatrix}\\prime}\\begin{pmatrix} 2 & 3 \\\\ \\end{pmatrix} + \\begin{pmatrix} {- 2} & {- 3} \\\\ \\end{pmatrix}'\\begin{pmatrix} {- 2} & {- 3} \\\\ \\end{pmatrix}} \\right\\}} \\\\ {= \\begin{matrix} {|\\begin{matrix} 4 & 6 \\\\ \\end{matrix}|} \\\\ {|\\begin{matrix} 6 & 9 \\\\ \\end{matrix}|} \\\\ \\end{matrix}} \\\\ \\end{matrix}$![方程](img/F000084si87.png)

为求特征值，取 det (`∑−λI`) 并令其等于零，从而得到特征方程：`λ²–13λ=0`。特征值为零和 13。对应最大特征值的特征向量为 `w[1]=(a b)′`，其中 (`∑−13 I`) `w[1]=0`；这样得到两个方程两个未知数：`−9 a + 6 b=0` 和 `6 a−4 b=0`，但它们是相依方程。求解它们得到 `b=3/2 a`，但由于希望 `‖w[1]‖=1`，即 `a² + b²=1`，代入得到 `a² (1 + 9/4)=1`，所以 `a²=4/13` 且 `b²=9/13`。与特征值 `λ[1]=13` 相关联的归一化特征向量为 `w[1]=(2 3)′/13^(1/2)`。以类似方式对于特征值 `λ[2]=0`，归一化特征向量 `w[2]=(3 –2)′/13^(1/2)`。完整的矩阵 `W` 由这些特征向量的转置组成，`13^(1/2) ⋅ W=`![方程](img/F000084si88.png)

$\\begin{matrix} {|2} & {3|} \\\\ {|3} & {{{- 2}|}.} \\\\ \\end{matrix}$

![方程](img/F000084si89.png)



如前所述，`PCA` 应用于具有分布函数 `F` 的随机向量 `v=(a b)′`。另外，假设向量 `v[1]` 和 `v[2]` 使用 `F` 采样。那么，`PCA` 是 $V = W\\left( {v - v^{-}} \\right) = {\\begin{pmatrix} {a - 3} & {b - 6} \\\\ \\end{pmatrix}\\prime}$![Equation](img/F000084si90.png)。2×2 矩阵 `13^(1/2)`![Equation](img/F000084si91.png) `W` 如下给出，其后是 2×1 列向量 `(v−*v*^−)/ 13^(1/2.)`

$\\begin{array}{rrl} {|2} & {3|} & {{|{\\left( {a - 3} \\right)/13^{1/2}}|}} \\\\ {|3} & {{- 2}|} & {{|{\\left( {b - 6} \\right)/13^{1/2}}|}.} \\\\ \\end{array}$

![Equation](img/F000084si92.png)

所以，`V=1/13^(1/2) (2a+3b−24 3a−2b+3)’`。

如果需要压缩，则只保留矩阵 `W` 的第一列，然后 `V` 的第一个元组将存在。在这种情况下它将是一个标量。

t-分布随机邻域嵌入，`t-SNE` 方法与用于降维的 `PCA` 类似，它在分类方面更好。例如，它会扭曲或夸大聚类边界。它使用非线性运算来执行数据降维。

## 5.7 核主成分分析

直接的 `PCA` 方法对于随机数据或非线性流形类型数据没有用。这是因为 `PCA` 算法无法区分这两种类型的数据；它对它们的处理同样糟糕。然而，`PCA` 可以使用核来执行。这被简写为 `KPCA`，并且它使用 `Gram` 矩阵。当数据似乎位于流形上或紧贴流形时，`KPCA` 非常有用。对于线性核，该方法几乎与通常的 `PCA` 算法相同，特别是当该情况下的流形是线性的时。重要的是，使用核时可以发现额外的非线性结构。不使用 `KPCA` 的原因在于，在某些情况下，使用 `KPCA` 时可能会发生过拟合；此外，透明度通常会丢失。在这种情况下，该方法变为非参数的。此外，重建并不明显，因为使用 `KPCA` 时几乎不可能替换非主成分。最后，`KPCA` 中需要的超参数和实际核是有问题的。`KPCA` 通常需要多次运行以找到有用的参数和核设置（Schölkopf 等，1999）。

`KPCA` 技术采用特征映射来转换为非线性数据。尽管特征映射 `Φ`![Equation](img/F000084si93.png) 必须已知，但它们并未直接使用。如常，结果仅通过涉及原始内积以及核 `K` 获得。核主成分分析首先通过生成到更高维特征空间的映射来引入非线性。接下来概述了 `KPCA` 底层工作原理的基本思想。简而言之，就是使用核技巧转换原始数据，然后求解涉及核 `K` 的特征值和特征向量。这随后将这些特征值和特征向量映射为所需协方差矩阵 `C` 的特征值和特征向量。该程序背后的动机来自于 `K` 和 `C` 公式之间的相似性。相似性将在后面概述。

核矩阵本质上由 `K=XX′` 给出。例如，假设 `K` 是一个 `n`×`n` 矩阵，因此具有 `n` 个特征值。`K` 中的条目是涉及实际数据的标量积，因为 `X` 是一个向量。始终必须确保所有数据都已归一化，即均值为零，且特征向量的范数为一。归一化数据的协方差矩阵由 `C=X′X` 给出，它是一个 `d`×`d` 矩阵，具有 `d` 个特征值。通常的 `PCA` 方法直接从矩阵 `C` 找到特征值和特征向量。需要的是 `K` 的特征向量和特征值与 `C` 的特征向量和特征值之间的某种关系。为了获得对这种关系的某些见解，假设 `a` 是 `K` 的特征向量，`Ka=λa`，即 `XX′a=λa`。然后在左边乘以 `X′` 得到 `X′XX′a=λX′a`，`Cv=λv`，其中 `v=X′a`。这表明如果 `v` 不为零，则 `v` 是协方差矩阵 `C` 的特征向量。相反的关系也成立。

在推导中显示 `K` 可以替代相关矩阵 `C` 所需的关键恒等式如下给出。它显示了特征向量和特征值关系。该推导中的主要步骤是获得公式 `K² a=λ K a`。一旦获得该公式，就除以 `K`，即乘以 `K` 的逆。这可以在假设 `K` 为正定时的情况下完成。一般来说，`C` 和 `K` 仅为半正定。另一方面，将上述恒等式写为 `K (K a−λ a)=0` 显示了所需的结果，即 `a[k]` 是 `K` 的特征向量，其特征值为 `λ`，因为 `K` 不为零。如果需要压缩，则可以删除对应于特征值最小值的特征向量（Thompson，2014）。

通过投影到更高维空间，非线性可分数据可以变得线性。

### 示例 5.13

这是 `PCA` 从应用核和核技巧中受益的一个实例（Hornegger，2021）。假设特征向量 `x[1]`、`x[2]`、… `x[n]` 在 `R^(d)` 中。每个向量对应于具有 `1024²` 像素的图像。如果直接对特征向量执行 `PCA`，则处理的顺序为 `2²⁰` 步。然而，使用 `KPCA`，所需计算总量仅为 `^(50*x*50)` 步的顺序。

## 5.8 奇异值分解

奇异值分解（`SVD`）有着悠久的历史；它最好在 Stewart（1992） 中描述。`SVD` 是数值线性代数中许多程序的核心步骤，并且在描述欧几里得空间的几何形状时很重要。下面结合示例概述 `SVD` 程序。

`m`×`n` 矩阵 `A` 的 `SVD` 首先将该矩阵表示为形式 `A=U D V′`，其中撇号是转置运算。在此情况下 SCALAR 域为 `R`。这里，`U` 是一个 `m`×`m` 正交矩阵，其列由 `AA′` 的标准正交特征向量组成。由于后者矩阵是自伴的，其对应于不同特征值的特征向量是正交的，因此它们只需要归一化。`U` 的列按归一化特征向量从左到右排序。特征向量的排序对应于特征值的大小。特征值较大的特征向量位于特征值较小的特征向量左侧。当两个或多个特征值相等时，哪个特征向量占据哪个列并不重要。然而，这些特征向量不必正交，但它们总是线性无关的。因此，在将向量作为 `U` 的列输入之前，需要应用 `Gram-Schmidt` 正交归一化程序。

以类似的方式，应找到 `n`×`n` 正交矩阵 `V`。在这种情况下，`V` 的列由 `A′A` 的归一化、排序特征向量组成。排序与 `U` 完全相同。然而，在找到正交矩阵 `V` 之后，必须取转置。最后，稀疏对角矩阵 `D` 由主对角线上的特征值的平方根组成。这些按降序排列，对应于 `U` 或 `V` 列中特征向量的位置。使用哪个正交矩阵并不重要。这是因为两个矩阵中的特征向量都占据具有相同非零特征值的列位置。这可以如下看出。假设 `A′Av=λ v`，对于非零的 `λ` 和 `v`。那么，`AA′Av=λ Av`。因此，`AA′` 也具有特征值 `λ`，此时特征向量为 `Av`。反过来，如果 `AA′v=λv`，则 `A′AA′v=λA′v`，因此 `AA′` 的特征值也是 `A′A` 的特征值。

### 示例 5.14

考虑 2×3 矩阵 `A`，它如下给出，同时 `AA′` 在右侧给出：



$\\begin{array}{crrrr} {|{3}} & 1 & {1|} & {|11} & {1|} \\\\ {|{- 1}} & 3 & {1|} & {|{1}} & {11|} \\\\ \\end{array}$

![Equation](img/F000084si94.png)

通常，求解特征方程时会得到特征值。取 `det(AA' − λ I)` 并将其设为零得到以下特征方程：`λ² –22λ + 120=0`。因此，特征值为 `λ[1]`\=12 和 `λ[2]`\=10。对应的特征向量为 `v[1]`\=(a b)′ 和 `v[2]`\=(c d)′。对于较大的特征值，`[AA' –12·I]` `v[1]`\=0；这表明 `a`=`b`。利用所有特征向量必须归一化的事实 `a² + b²`\=1 可知 `v[1]` = (1/2^(1/2)1/2^(1/2))’![Equation](img/F000084si95.png)。类似地，第二特征向量为 `v[2]` = (1/2^(1/2)−1/2^(1/2))’![Equation](img/F000084si96.png)。注意这些特征向量是正交的。由于特征值 `λ[1]`![Equation](img/F000084si97.png) 最大，矩阵 `U` 使用 `v[1]`![Equation](img/F000084si98.png) 作为列，然后是 `v[2]`![Equation](img/F000084si99.png) 来求得。所以，2^(1/2)![Equation](img/F000084si100.png) `U`=
$\\begin{matrix} {|1} & {1|} \\\\ {|1} & {{- 1}|} \\\\ \\end{matrix}.$
![Equation](img/F000084si101.png)

为了求 `V`，必须确定 `A′A` 的特征值和特征向量，其为：
$\\begin{matrix} {|10} & 0 & {2|} \\\\ {|{0}} & 10 & {4|} \\\\ {|{2}} & 4 & {2|} \\\\ \\end{matrix}$
![Equation](img/F000084si102.png)
如前所述，特征方程 `det(A′A−λ I)=0` 的解为特征值。为求该方程，考虑行列式：
$\\begin{matrix} {|{10 - \\lambda}} & 0 & {{ 2}|} & {10 - \\lambda} & 0 \\\\ {|{ 0\\mspace{23mu}}} & {10 - \\lambda} & {{ 4}|} & 0 & {10 - \\lambda} \\\\ {|{ 2\\mspace{23mu}}} & 4 & {{2 - \\lambda}|} & 2 & 4 \\\\ \\end{matrix}$
![Equation](img/F000084si103.png)
将所有三个角上沿负 45°的元素相乘并相加得到 sum1。接下来，将沿正 45°的元素相乘并相加得到 sum2。最后用 sum1 减去 sum2，这就是行列式。计算行列式 (10 −`λ`)(10−`λ`)(2 −`λ`)−4(10 −`λ`)−16(10−`λ`)=0，据此 (10 −`λ`) \[(10−`λ`)(2 −`λ`)−20\]=0=(10−`λ`) \[`λ`²–12 `λ`\]=0。由此可知特征值为 `λ[1]`\=12，`λ[2]`\=10，最后 `λ[3]`\=0。对应的特征向量如前所述通过取 (`A′A−λ I`) v)=0 求得。对于 `v[1]`\=(a b c)′，令以下等于零：
$\\begin{array}{llll} {10 - \\lambda\_{1}} & { 0} & {{ 2}|} & {|a|} \\\\ {|0} & {10 - \\lambda\_{1}} & {{4|} \\cdot} & {{|b|} = 0} \\\\ {|2} & 4 & {{2 - \\lambda\_{1}}|} & {|c|} \\\\ \\end{array}$
![Equation](img/F000084si104.png)
这给出 −2 a + 2 c=0，−2 b + 4 c=0，以及 2 a.+ 4 b + 2 c=0；解为 a=1，b=2，c=1。归一化后得到特征向量 `v[1]` = 1/6^(1/2)![Equation](img/F000084si105.png) (1 2 1)′。类似地，在上述矩阵中使用 `λ[2]`\=10 代替 `λ[1]`![Equation](img/F000084si106.png) 得到相应的归一化特征向量 `v[2]` = 1/5^(1/2)![Equation](img/F000084si107.png) (2 –1 0)′。最后，使用第三个特征值得到最终特征向量 `v[3]` = 1/30^(1/2)![Equation](img/F000084si108.png) (1 2 –5)′。注意所有这些特征向量相互正交。这三个特征向量现在按给定顺序成为列 1、2 和 3，以形成正交矩阵 `V`。需要该矩阵的转置；因此 `V′`= 
$\\begin{array}{lll} {|{1/6}^{1/2}} & {2/6}^{1/2} & {{{ 1}/6}^{1/2}|} \\\\ {|{2/5}^{1/2}} & {{- 1}/5}^{1/2} & {{}0|} \\\\ {|{1/30}^{1/2}} & {2/30}^{1/2} & {{{- 5}/30}^{1/2}|} \\\\ \\end{array}$
![Equation](img/F000084si109.png)
唯一剩下的矩阵是 `D`。它由主对角线上的非零特征值的平方根组成，即从左上角开始沿负四十五度线。按从大到小，这些特征值的平方根填充该线。另一点是 `A`=`U D V′`；维度必须一致。由于矩阵维度为 `A` 为二乘三；`U` 为二乘二；`D` 为二乘二；最后 `V′` 为三乘三，因此需要一行或一列零来使维度成立。因此，在此示例中，SVD 需要额外一列零，所以 `D`= 
$\\begin{array}{lll} {|12^{1/2}} & 0 & {0|} \\\\ {|{0.}} & 10^{1/2} & {{0|}.} \\\\ \\end{array}$
![Equation](img/F000084si110.png)
这是 `A` 的奇异值分解。`U` 的列是左奇异向量，`V` 的列称为右奇异向量。

关于 SVD 的最后一点是它在对向量 x 操作时提供了有趣的几何解释。设 `A`=`U D V′`，为 m×n 向量。一个重要假设是 `U` 和 `V` 分别属于特殊正交李群 `SO(m, R)` 和 `SO(n, R)`。因此，它们表示旋转矩阵；其行列式等于一。在这种情况下，首先当 `U` 作用于 x 时，x 发生旋转。设 `U(x)=y`。接下来，当 `D` 作用于 y 时，如果 `D` 是标量矩阵，则 `D` 放大或缩小 y 并改变维度。否则，它放大 y 中的某些元组，压缩 y 中的其他元组，并改变维度。设 `D(y)=z`。最后，`V∗` 对 z 应用旋转，得到 w。因此，`V∗(z)=w`。最有趣的情况是当 n=m=2 时。在这种情况下可以图形化地提供该过程的说明。

## 参考文献
* Hollings 和 Lawson, 2017 Hollings C, Lawson M. *广义堆的 Wagner 理论* Springer books 2017;.
* Horn and Johnson, 1991 Horn R, Johnson C. 978-0521-46713-1 *矩阵分析专题* Cambridge U. Press 1991;.
* Hornegger, 2021. Hornegger, H., 2021. 模式识别实验室，讲座 模式识别。
* Hotelling, 1933 Hotelling H. 将一组统计变量分析为主要成分。 *J Educa Psychol.* 1933;24(6):417–441。
* Loeve, 1977 Loeve M. GTM *概率*. vol. 45 Springer 1977;.
* Marsden, 2003 Marsden. *微分形式与斯托克斯定理* Caltech 2003;.
* Pearson, 1901 Pearson, 1901. 关于空间点系的最佳拟合线和平面。 Philosophical Magazine.
* Scholkopf et al., 1999 Scholkopf, et al. *核主成分分析*. *核方法进展-支持向量学习* MIT Press 1999;.
* Stewart, 1992 Stewart, G., 1992. 关于奇异值分解的早期历史, IMA o reorient # 952.
* Thompson, 2014 Thompson, D., 2014. 非线性降维 KPCA, JPL-Caltech 虚拟暑期学校 大数据分析。
* Yano, 1957 Yano, K., 1957. 李导数理论及其应用, North=-Holland, 978-0-7204-2104-0.
* Zubelevich, 2012 Zubelevich O. *Cartan 魔法公式的初等证明* University of Texas 2012;.

# 第 6 章

# 量子退火与绝热量子计算

## 摘要



# 量子退火概述

Both `simulated annealing` 和 `quantum annealing (QA)` 主要用于组合优化。此处的优化通常涉及非线性目标函数，在机器学习应用中最为有用。基于能量的量子退火被证明比基于热力学的模拟退火快数个数量级。因此，本文仅描述量子退火。本章后面的章节将介绍其他类型的量子退火。特别是，数字退火的创建源于半导体的使用，最常见的是互补金属氧化物半导体（`CMOS`）电路。

本章从理解量子退火及其在量子技术中绝热过程中的作用所需的基本量子物理背景开始。主要工具是 `Schrödinger equation` 和 `Hamiltonian operator`。本节对量子系统的状态做出了基本描述。此外，还提供了涉及 `harmonic oscillator` 及其基态解的示例。本节第一部分提到了用于激发态解的 `ladder algebra` 的参考。

`QA` 和绝热量子计算（`AQC`）的基础在很大程度上参考了量子技术方面，例如量子干涉、量子叠加以及纠缠的作用进行了描述。这在 `Section 6.3` 中继续。 在这里，`QA` 和 `AQC` 中使用的主要量子特征被描述并加以说明。它是量子比特的隧穿。在下一节中，描述了量子存储的具有挑战性的方面。其后是不可克隆定理以及量子存储近期发展的简要列表。下一节提供了原子和离子的入门描述。下一节给出了量子比特制备的概述。接下来的两节涉及用于门式量子计算机的量子比特的两种主要创建方法。按顺序，囚禁离子方法在 `Section 6.7` 中描述，然后超导性和约瑟夫森结（`JJ`）量子比特创建方法在 `Section 6.8` 中介绍。下一节介绍了涉及量子点的概念；其后是对 `D-wave` 计算机以及使用二次无约束二元优化（`QUBO`）的计算的描述。最后一节描述了绝热定理，并以 Berry 连接的简要描述结束。

## 关键词

`Schrödinger equation`；`harmonic oscillator`；`adiabatic computing`；`tunneling`；`no-cloning`；`super-conductance`；`Josephson junction`；`quantum dots`；`adiabatic theorem`；`Berry connection`

## 6.1 薛定谔对量子特性的描述

薛定谔对量子的观点是波力学。他的量子愿景在制造量子比特、传感量子比特、控制量子比特以及传输它们方面最有用。因此，需要从薛定谔方程开始进行少量分析。该方程是表示孤立量子系统中波函数动力学和运动学的线性偏微分方程。在最简单的形式中，它涉及一维中的单个非相对论粒子。在这种情况下，方程为 `ih ∂Ψ(x, t)/∂t=−h²/(2 m) ∂²Ψ(x, t)/∂x∂x+V(x,t) Ψ(x,t)`。波函数 `Ψ: R x R→C`，其中 `C` 是复数域。在前面提到的波动方程前面，负一的平方根乘以 `h`。这里，`h` 是约化普朗克常数；它位于上面 `Ψ` 关于时间 `t` 的偏导数的左侧。粒子质量为 `m`，而 `V(x, t)` 是孤立系统中的势。在本章开始时，主要是运动学最为重要。因此，首先将采用时间无关的薛定谔方程。它是 `h²/2 m ∂²Ψ(x)/∂x∂x=V(x) Ψ(x)`。在本章后面的一个部分，具体为 `Section 6.11`，绝热定理是用时变的波函数描述的。

此外，在本章中，量子系统的状态假定为量子比特，或 ket，`|Ψ>`。它是一个来自可分希尔伯特空间 `H` 的元素。符号上，根据上下文，`|Ψ>` 和 `Ψ` 可互换使用。此外，该向量始终是归一化的，即 `‖Ψ‖²=<Ψ, Ψ>=1`。方程 `h²/2 m ∂²Ψ(x)/∂x∂x=V(x) Ψ(x)` 通常写成本征函数方程，即 `H |Ψ> = E |Ψ>`。在这种情况下，`E` 是系统的能量，而 `H` 是哈密顿算符。哈密顿算符将状态信息转换为能量信息。因此，对于该方程，`E` 被理解为本征值，而 `|Ψ>` 是本征向量；它永远不等于零。本征向量 `Ψ` 通常称为定态。稍后将给出哈密顿量和涉及时间无关薛定谔方程一个非常特殊情况的解的一个示例。

### 示例 6.1

谐振子描述了光子的本征函数方程；它涉及哈密顿量 `H` 和能量本征值 `E[n]`，`n=0, 1, 2, …`。方程如下：

`H Ψn=1/2 (−h²/m d²/dxdx + m(w[0] x)²) Ψn=E[n]Ψn`，其中 `Ψn` 是本征函数，而 `w[0]` 是振子的频率。目标是求解该方程以求 `Ψ[n]`，涉及所有非负整数 `n`。这些解将在本文件后面的一个章节中推导。解 `Ψ[n]` 涉及厄米多项式。厄米多项式在附录 A7 中以 Sturm-Liouville 微分方程的形式描述。最重要的是，解仅存在于离散能量水平 `E[n]`，它们是等间距的。具体而言，`E[n]=h w[0] (2 n+1)/2`，`n=0, 1, 2, …`。这些解是通过进行代换并使用阶梯算符以及对易关系找到的。算符涉及使用产生和湮灭函数的代数。然而，这些代数细节将在 MSA 框架中描述，也在后面的章节中。

仅最简单和最重要的状态，即基态 `Ψ[0]` 的解将被说明。也就是说，`n=0` 的解在此详细说明。基态的微分方程为 `x Ψ[0] + h/(m w[0]) dΨ[0]/dx=0`。这是一个线性一阶微分方程，并且是可分离的。因此，交叉相乘并写出，`dΨ[0]/Ψ[0]=[−x (m w[0])/h] dx`。然后对该方程的两边积分得到 `ln (Ψ[0])=− m w[0] x²/(2 h) + c`。因此，`Ψ[0]=A e^(− m w[0] x²/(2 h))`。常数 `A` 将被找到，因为如前所述，所有状态必须归一化。因此，`‖Ψ[0]‖²` 必须等于一。




## 6.1

此前未提及的是，在大多数分析设定中使用的希尔伯特空间是勒贝格平方可积函数 `L²` 的子空间。这些空间在 `MSA` 的下层视图中作为载体集合出现，并在后续章节中进行描述。然而简而言之，由于基态解是平凡的，归一化 `Ψ[0]` 的计算很容易得到：`∥Ψ[0]∥² = <Ψ[0>, Ψ[0]> = ∫Ψ[0]*Ψ[0]dx = ∫Ψ[0]Ψ[0]dx = A²∫e^(-m w[0] x² / h)dx`![方程](img/F000217si16.png)。请注意，这是一个高斯核。因此，它可以被归一化，从而高斯核的面积必须设为一。该核的方差涉及 `m`、`h` 和 `w[0]`。归一化后，通过代入即可轻松求出 `A` 的值。因此，最终结果是基态解为 `Ψ[0] = (m w[0] / (π h))^(1/4) e^(-m w[0] x² / (2 h))`。 ![方程](img/F000217si17.png)

### Example 6.2

本例将强化态向量必须具有范数为一这一事实。再次，希尔伯特空间是 `L²`，而 `SCALAR` 的载体集合是复数域。设波函数为 `Ψ(x) = a (x+1)`![方程](img/F000217si18.png) `χ[[-1,1]](x)`![方程](img/F000217si19.png)，其中 `a` 在 `C` 中。因此，波函数 `Ψ(x)`![方程](img/F000217si20.png) 在区间 `[-1, 1]` 上具有紧支集。伴随 `Ψ*(x) = a* (x+1) χ[[-1,1]](x)`![方程](img/F000217si22.png)，为求 `a`，令 `a ∫[-1]¹ |a|² (x+1)² dx = |a|² (x³/3 + x² + x) |[-1]¹ = |a|² 8/3`![方程](img/F000217si23.png)。将该量设为一得到 `|a| = (3/8)^(1/2)`![方程](img/F000217si24.png)。

## 6.2 退火和绝热量子计算的量子基础

绝热量子计算 (`AQC`) 用于求解优化问题。它使用一个制备态和一个哈密顿量，该哈密顿量缓慢演化使得系统保持在基态。最重要的是，被求解的问题必须表述为能量最小化方程。在这种情况下，量子退火器将尝试通过搜索技术最小化目标函数并实际最小化能量。`AQC` 检查问题空间，更准确地说，它遍历能量景观寻找能量极小值。该过程通常通过移动到问题空间的其他部分来避免陷入局部极小值。作用通过常规方法发生，同时也采用隧穿过程。当量子比特一起隧穿时，该过程称为关联长度隧穿。能量变化导致问题空间中的移动，而量子涨落指的是达到最低能量状态的过程。这通常对应于期望的最优解。下面给出 `AQC` 的稍详细描述。

如前所述，从具有哈密顿量 `H[0]` 的易于制备的基态开始，该态被绝热演化。因此，它被非常缓慢地转变为具有哈密顿量 `H[1]` 的新的期望最优态。在数学上，这可以表示为两个哈密顿量的凸组合。对于区间 `[0, 1]` 中的 `s` 值，凸组合结果为 `H = s H[0] + (1 - s) H[1]`。随着参数 `s` 缓慢且单调地从 0 增加到 1，`H[0]` 过渡到期望的最优哈密顿量 `H[1]`。实际上，哈密顿量 `H[1]` 对应于最低能量解。再次，它是基态。这是量子绝热原理的结果。`AQC` 利用量子环境。具体来说，`AQC` 利用量子干涉、量子叠加、多量子比特纠缠和隧穿。接下来将描述前三种量子效应，并附带示例。量子隧穿的说明在下一节 第 6.3 节 中给出。

量子干涉与粒子波函数可能相互增强或湮灭的可能性有关。干涉也与量子比特的叠加以及该效应的过早坍缩有关。由于粒子通常表示为波，如正弦和余弦波，干涉可以理解为波相互重叠。波具有不同的频率；它们可能随机地相加和相减。它们可以增强或抵消期望的效果。此外，环境中的噪声经常会导致量子干涉。下面给出量子干涉的一个例子。

### Example 6.3

量子干涉将对 `C²` 中的单个量子比特进行说明。从一个简单态开始，例如 `|0>`。在将量子比特暴露于环境之后，开始于 `|0>` 并最终再次处于态 `|0>` 的概率将被求出。模拟环境的一种众所周知的方法是对量子比特使用算符。在这里，该态经历各种幺正变换以模拟干涉的效果。例如，执行一个众所周知的操作序列将 `|0>` 转换为 `|0>` 和 `|1>` 的线性组合。

态 `|0>`，在该应用中，通常称为基态。此外，在这种情况下 `|1>` 被称为激发态。算符序列是哈达玛变换 `H`、`T` 或 phi 变换，然后再次进行哈达玛变换。按该顺序应用时，算符序列将处于态 `|0>` 的量子比特映射到态 `|q>`。第 16 章 和 第 17 章 专门用于描述量子门计算机中的理论和应用操作。这些包括 `H` 和 `T` 算符。无论如何，应用 `H-T-H` 变换后，结果为 `|q> = 1/2 [|0> + |1> + e^(i ϕ) (|0> - |1>)] = cos(ϕ/2) |0> - i sin(ϕ/2) |1>`。

在上述分析中最重要的是，所模拟的环境导致了叠加的发生。`|0>` 的概率幅最初等于一，经过变换后现在变为 `cos(φ/2)`。获得 `|0>` 的概率密度为 `P(|0>) = cos²(φ/2)`。因此，`|0>` 的概率现在可以根据余弦平方函数在零到一之间变化。如前所述，这是环境可能导致干涉并使观测概率可变的模拟效应。

在 `C²` 中的单个量子量子比特 `|q> = a |0> + b |1>`，`|a|² + |b|² = 1`，同时处于态 `|0>` 和 `|1>`。这称为量子叠加。叠加的说明已在前一个示例中给出。在那里，看到 `C²` 中的单个量子比特 `|q> = cos(ϕ/2) |0> - i sin(ϕ/2) |1>`。因此，该量子比特同时处于两种态，其比例由正弦函数的平方给出。

当存在多个量子比特时会出现量子比特的叠加。量子世界中的两个比特对应于 `C⁴` 中张量表示中的两个简单量子比特 `|p>` 和 `|q>`。即 `|w> = |p> ⊗ |q> = |p q>`。例如，在 `C⁴` 中，使用零一基，`|w> = a |0 0> + b |0 1> + c |1 0> + d |1 1>`。与之前类似，`|a|² + |b|² + |c|² + |d|² = 1`。叠加现在意味着 `|w>` 同时处于全部四个态。同样，`C⁸` 中的三重张量子比特同时处于八个态中的每一个。在所有这些情况下，玻恩规则适用。也就是说，当观察这些量子比特中的任何一个时，只会出现一个态以及相关的概率。这种现象归因于粒子的波动性。由于波干涉，获得单个期望态的机会增加。同时，波干涉降低了获得其他态的机会。



## 纠缠
纠缠是与两个量子比特或两个以上量子比特相关的属性。它总是意味着量子比特之间存在非常高的关联。通过观测单个纠缠量子比特，其他量子比特的属性也随之可知。从稍微更严格的观点来看，假设有两个量子比特 `|v>` 和 `|w>`，每个都在 `C²` 中。由 `|v>` 和 `|w>` 构成的量子比特 `|q>` 如果在 `C⁴`=`C²`⊗![Equation](img/F000217si27.png) `C²` 中，`|q>`；然而，该量子比特本身不能写成简单的张量积，`|v>` ⊗![Equation](img/F000217si28.png) `|w>`。在后续章节中，将从密度算符的角度给出更深入的解释。

### 例 6.4
一个在 `C⁴` 中纠缠的 `C²` 中两个向量的例子涉及 `|0>` 和 `|1>`。在 `C⁴` 中，考虑 `|q> = 1/2 (|0> ⊗ |1>) + 3^(1/2)/2 (|1> ⊗ |0>) = 1/2 (|0 1> + 3^(1/2)/2 |1 0>)`。如前所述，后续章节将说明纠缠张量具有这样的性质：乘积 `a11 a22` 不等于乘积 `a12 a21`，其中 `|q> = a11 |0 0> + a12 |0 1> + a21 |1 0> + a22 |1 1> = 1/2 (|0 1> + 3^(1/2)/2 |1 0>)`。该判据在第 7.4 节中描述。在当前情况下，对于 `|q>`，`a11 = 0`，`a12 = 1/2`，`a21 = 3^(1/2)/2`，最后 `a22 = 0`。所以 `a11 a22 = 0`，但 `a12 a21 = 3^(1/2)/4`，因此存在纠缠。

## 绝热量子计算
绝热量子计算可以执行量子退火 (`QA`)，并提供一种利用幺正门的量子计算替代方法。`AQC` 已被证明等价于量子计算的标准幺正门模型 (Aharonov 等，2014)。然而，这些方法非常不同。`AQC` 方法的目标是在绝热条件下找到全局最小值 (Krauss，2013)。从状态 `|ψ>` 的初始条件开始，薛定谔方程的连续时间演化被用于寻找最终观测值。这就是 `AQC` 的全部内容。如果环境控制不当，最终状态可能只是一个局部最小值。通常，薛定谔方程为 `iħ ∂|ψ>/∂t = H(t) |ψ>`。它在哈密顿量 `H` 的绝热条件下演化，`t` 在 `[0, T]` 中，其中 `T` 是总演化时间。
如前所述，绝热条件保证了哈密顿量的本征态不变。这里假设存在缓慢的时间演化。此外，假设被占据的本征态与其他所有激发能量态之间的能量间隙不会太小。该间隙决定了 `AQC` 的计算复杂度。较小的间隙导致更长的计算时间。`AQC` 已知在寻找最优解方面比传统算法提供二次加速。此外，它保持量子比特相干性，并提供比其他量子计算模型更好的抗噪声能力 (Childs 等，2001a,b)。
基本上，控制退火过程有两种方法：准静态控制和相干控制。准静态控制的退火时间大于热弛豫时间，导致在大部分演化过程中达到热平衡。在相干控制中，退火时间小于弛豫或退相干时间；此时薛定谔方程占主导。
超导电子学是实现 `AQC` 和 `QA` 的方法之一 (Wendin，2017)；在这种情况下，利用了约瑟夫森结。它利用隧道效应。囚禁离子技术也用于 `AQC` (Zhang 等，2018)。
这些输入被转换为电电流、电电压和磁场。电磁源控制量子比特，它们总是以叠加态开始。随着退火过程的进行，量子比特自旋演化以试图确定最低能量态。该过程利用了如前所述的量子干涉、叠加和纠缠。此外，这些量子比特采用 第 6.3 节 中描述的隧道方法。
对于任意粒子、量子比特或波函数 `Ψ`，概率幅为值 `Ψ`。此外，当 `Ψ` 被观测时，Born 规则被用于定义实际概率密度；它为 `P(ψ) = ‖Ψ‖²`。

## 6.3 δ函数势阱与隧道效应
本节的主要内容是隧道效应。简而言之，粒子可以走捷径并穿过势垒，而不是越过势垒。厚度无关紧要；粒子可以通过物质的速度比光在真空中传播的速度更快。本节存在两种情况。如果 `E < V` 状态，δ函数势会出现束缚态，而当不等式反转时，隧道效应发生。在后一种情况下，称存在自由粒子。它们通常不可归一化，因为它们一般不是平方可积的。此外，由于态未被束缚，能谱通常是连续的。本节基于优秀的来源 (Carson，2014)。
当 `|x|` 趋于无穷时，束缚态趋于零，并且它们是可归一化的。此外，它们具有通常量子化和离散的能级。这是使用定态薛定谔方程的边界条件的結果。从某种意义上说，束缚态的概念与发生隧道效应的散射态相反。在束缚态中，粒子在该态中的能量小于无穷远处的势能。此外，束缚态函数是驻波。有界态的能谱总是离散的。此外，对应的本征函数在 `|x|` 较大时呈指数衰减。这些概念将在后面通过束缚态的例子以及态的散射来描述。
定态薛定谔方程的解在分段解的边界处必须匹配。一般来说，波函数 `ψ` 必须连续。当没有δ函数时，导数 `dψ/dx` 也必须连续。然而，如果在某个离散点 `x[0]` 导数不存在，则如果 `V(x[0]) → ∞`，积分将导致解 (Zwiebach，2017)。
无限势阱在 图 6.1A 和 B 中示出。在原点，存在值为 −a 的δ函数，`V(x) = -a δ(x)`。有两种情况，取决于能量 `E` 为负还是正。在前一种情况下，如 图 6.1A 所示并在下一个示例中描述，是束缚态情况。相应地，能量 `E` 小于零。第二个示例说明了自由粒子解并演示了隧道过程。

![图 6.1 束缚态和散射态隧道效应。(A) 束缚态，(B) 散射态，(C) 归一化束缚态解，(D) 隧道效应。](img/F000217f06-01-9780443136979.jpg)

图 6.1 束缚态和散射态隧道效应。(A) 束缚态，(B) 散射态，(C) 归一化束缚态解，(D) 隧道效应。

### 例 6.5



束缚态解是通过求解定态薛定谔方程得到的：`−h²/(2 m)d²ψ/dx² = E ψ`![Equation](img/F000217si42.png)。这里，`V=0` 在原点左侧和右侧。并且 `E < 0`。作代换 `d²ψ/dx² = k² ψ`![Equation](img/F000217si43.png)，其中 `k = (−2 m E)^(1/2)/h`![Equation](img/F000217si44.png)，并且不要忘记 `E < 0`。在这种情况下，两个负号相乘为正。一般求解得 `ψ(x)=A e^( − k x)`![Equation](img/F000217si45.png) + `B e^(k x)`![Equation](img/F000217si46.png)。δ函数存在于原点；原点左侧的解为 `ψ`[1]![Equation](img/F000217si47.png)；原点右侧的解为 `ψ`[2]![Equation](img/F000217si48.png)。原点处的δ函数为 `−a δ(x)`。量 `B` 对于 `x>0` 必须为零，因为它会给出无界解。对于 `x<0`，标量 `A` 必须为零。

由于波形必须连续，应用边界匹配。因此，为保证连续性 `ψ`1=`B e^(k x)`![Equation](img/F000217si49.png) 必须等于 `ψ`[2].(x)=`A e^( − k x)`![Equation](img/F000217si50.png) 当 `x=0` 时；这意味着两个常数 `A` 和 `B` 相等，即 `A=B`。

导数匹配因δ函数无限势而失败。相反，将定态薛定谔方程从负的 epsilon 积分到 epsilon。并令 epsilon 趋于零。利用 `V(x)=−a δ(x)`，则 `∫[ − ϵ ]^(ϵ) −h²/(2m) d²ψ/dx²dx − ∫[ − ϵ ]^(ϵ) a δ(x) ψ(x)dx = ∫[ − ϵ ]^(ϵ) E ψ(x)dx`。积分并准备代入积分限得到 `− h²/(2 m) dΨ/dx |[ − ε ]^(ε) − a ψ(0) + E ψ(x) |[ − ε ]^(ε) = − h²/(2 m) dΨ/dx |[ − ε ]^(ε) − a Ψ(0) + 0`![Equation](img/F000217si57.png)。最后一个零来自积分中值定理。所以 `dψ/dx |[ − ϵ ]^(ϵ)`![Equation](img/F000217si58.png) =`−2 m a/h² ψ(0)`。考虑左右解并求导得到 `dψ1/dx |[ − ϵ ]`![Equation](img/F000217si59.png) =`B k e^(−k ϵ)` 且 `dψ[2].(x)/dx |^(ϵ)`![Equation](img/F000217si60.png) =`−B k e^(−k ϵ)`。用上极限减去下极限并令 `ϵ→0` 得到 `− 2 B k = −2 m a/h² ψ(0)`。令 `ψ(0)=B` 然后消去 `B`，所以 `k = m a/h²`，但 `k² = −2 m E/h`，这表明了量子化并允许求解量子化能量 `E = − m a²/(2 h²)`![Equation](img/F000217si61.png)。

最后，归一化波函数 `∫[ − ∞ ]^∞ ψ * ψ dx =1`，利用该事实它是一个高斯型核且曲线下的面积为一。这决定了 `B = (m a)^(1/2)`![Equation](img/F000217si63.png)。归一化的束缚态解由 `ψ(x) = (m a)^(1/2) e^( − m a |x| / h^(1/2))`，`E = − m a²/(2 h²)`![Equation](img/F000217si64.png) 描述。该解在 图 6.1C 中示出。

下面的下一个示例说明了自由粒子解并演示了隧穿过程。在这种情况下，能量 `E` 大于零。

### 示例 6.6

对 `E>0` 的情况散射自由粒子波解。值 `V` 在原点处除外处处为零。定态薛定谔方程为 `–h²/(2 m)d²ψ/dx² = E ψ`。这次，由于能量为正，令 `k² =2 m E/h²`；则 `d²ψ/dx² = −k² ψ`。同样，有两个独立的解，一个在δ函数左侧，一个在右侧。原点左侧的解为 `ψ1=A e^(i k x)`![Equation](img/F000217si65.png) + `B e^( − i k x)`![Equation](img/F000217si66.png)，原点右侧的解为 `ψ2=D e^(i k x)`![Equation](img/F000217si67.png) + `F e^( − i k x)`![Equation](img/F000217si68.png)。利用波函数解的连续性相当于在原点处将左手解等于右手解。这表明 `A + B = D + F`。

如前例所述，由于存在δ函数势，导数在原点处不必连续。因此与之前一样，积分薛定谔方程。如束缚态的情况，极限形成原点附近的一个小邻域。因此，积分为 `∫[ − ϵ ]^(ϵ) −h²/(2m) d²ψ/dx²dx − ∫[ − ϵ ]^(ϵ) a δ(x) ψ dx = ∫[ − ϵ ]^(ϵ) E ψ dx`。应用极限得到 `−h²/(2 m) dψ/dx |[ − ϵ ]^(ϵ) − a ψ(0) + E ψ(x) |[ − ϵ ]^(ϵ) = − h²/(2m) dψ/dx |[ − ϵ ]^(ϵ) − a ψ(0) + 0`。再次，最后的零来自积分的中值定理。对左右解求导并代入表明 `i k (D − F) − i k (A − B) = −2 m a/h² (A + B)`，其中 `ψ(0)` 任意选为等于 `ψ1=A + B`。定义一个常数来压缩解，其中 `β = m a/(k h²)`。所以，`D − F = A (1 + 2 i β) − B (1 − 2 i β)`。

现在可以应用启发式方法。假设散射仅从左侧发生。假设波 `ψ`![Equation](img/F000217si83.png) 从左向右传输。因此可以假设常数 `A` 已知。所以所有解都将涉及 `A`。此外，在这种情况下，`B` 可以被认为是反射波的系数。由于波是从左向右传播的，`F` 应设为零，因为它不能被反射。然而，`D` 可以被认为是隧穿波的系数。因此，整体解将用 `A` 表示。求解 `B` 和 `D` 得到 `B = i β/(1 − i β) A` 且 `D = 1/(1 − i β) A`。

反射系数定义为 `R = |B|²/|A|² = β²/(1+β²)`。同样，透射系数，即隧穿系数，为 `T = |D|²/|A|² 1/(1+β²)`。用 `m a/(k h²)` 替换 `β` 得到 `R = 1/(1 +2 h² E/(m a²))` 且 `T = 1/(1 + m a²/(2 h² E))`。而且，`F + T =1`。为说明量子隧穿，当 `E→∞` 时，`T→1`，即能量越大，粒子隧穿的可能性越大。另一方面，能量越接近零，粒子被反射的可能性越大。在非量子情况下，即经典情况下，这些值对于势阱等于 `T=1` 且 `R=0`。对于势垒，这些值也是 `T=0` 且 `R=1`。然而，在量子理论中，对于δ函数情况，它们具有相同的值。也就是说，如果在本问题中使用势垒代替量子阱，解将是相同的。也就是说，`T = 1/(1+β²)`，且 `R = β²/(1+β²)`。再次，这些量相加和为一，并被解释为概率。图 6.1D 说明了原始波、反射波以及隧穿波。

## 6.4 量子存储器与不可克隆定理

由于其相干时间，量子比特的存储是困难的。这是量子存储器在坍缩之前维持叠加所需的时间。



在量子计算中，多个量子比特对应着大量的状态。例如，`n` 个量子比特表示 `2^(n)` 个状态。存储这些量子比特又是另一回事，因为会受到包括温度在内的环境干扰，以及其他量子比特的干扰。简而言之，量子比特有坍缩或退相干的倾向。在这种情况下，量子比特的纠缠也会丢失。最关键的是，在观测或测量过程中，量子比特的信息往往会消失。如前所述，结果总是与之相关概率的单一状态。Holevo 定理还表明，即使可能存在 `2^(n)` 个状态，也只能利用 `n` 个数据位。最后，由于稍后详细说明的不可克隆定理，已存在于内存中的量子比特无法复制。

不可克隆定理规定，在秩大于一的有限维希尔伯特空间 `H` 中不能复制状态。具体来说，不存在线性映射 `T: H→H ⊗ H`，使得对所有 `ψ` 在 `H` 中，`T |ψ>` 产生倍数 `|ψ> |ψ>`。该结果可通过反证法轻松证明。因此，这里假设量子比特 `|ψ>` 可以使用 `T` 作为线性复制算符进行复制。考虑 `C − {0}` 中的标量 `a`，并设 `T |ψ> = a^(−1) |ψ> |ψ>`。在 `H` 中使用两个线性无关的向量 `|u>` 和 `|v>`，以及 `C` 中的标量 `b` 和 `c`。考虑这两个状态的叠加 `|ψ> = b |u> + c |v>`。

然后，根据 `T` 的假设复制性质和线性性，以下表达式相等，`a [T (b |u> + c |v>)] = (b |u> + c |v>) (b |u> + c |v>) = b² |u> |u> + b c |u> |v> b c |v> |u> + c² |v> |v>`。但是，由于 `T` 的线性性，下面成立：`a [T (b |u> + c |v>)] = a b T |u> + a c T |v> = b |u> |u> + c |v> |v>`。接下来，将该表达式与前一个表达式相等。然后令标量相等得到 `b² = b`、`c² = c`，且 `b c = 0`。因此，`c` 或 `b` 中至少有一个等于零。因此，这意味着 `|ψ>` 是 `|u>` 的倍数，或是 `|v>` 的倍数。无论如何，结果是 `|ψ>` 是单维的，即只存在单一维度。

### 示例 6.7
如果希尔伯特空间是 `H = C`，在复数域上，则线性映射 `T: H→H @ H`，使得对所有 `ψ` 在 `H` 中，`T |ψ>` 是 `|ψ> |ψ>` 的倍数。也就是说，不可克隆定理在 `H` 中不成立。因此，`C` 中的向量或复数可以被复制。这是由于对于 `C` 中的 `b`，`b T |ψ> = T b |ψ>`，从而 `b |ψ> |ψ> = b² |ψ> |ψ>`，意味着例如 `b = 1` 成立。也就是说，对于 `C` 中任意向量 `v` 或实际上标量 `v`，算符 `T` 复制该值，即 `T (v) = (v v)'` 在 `C²` 中。

尽管不可克隆定理成立，许多公司仍投资于创建量子存储设备。接下来描述几种近期在存储器开发方面的思路。

Qunnect 公司报道了按需电致透明量子型存储器（Finke, 2021）。这种量子存储的影响也将有助于解决除新设备开发和机器学习应用之外的其他问题。

单光粒子，即光子，常被用作量子比特，尤其是在网络中使用时。它们主要通过光纤用于量子比特的传输。光纤内的杂质会导致量子比特丢失和错误。此外，损耗是光纤长度的函数。量子存储有时利用光子。在这里，编码在光子中的量子比特在不进行观测或测量的情况下被存储。在这种情况下，在四开尔文的温度下，存储在电子上的光子信息被存储在硅原子核上（Stas, 2022）。

创建量子存储的不同方法包括稀薄原子气体和嵌入玻璃中的稀土离子。此外，硅空位中心（`SiVs`），即由单个硅原子周围的电子构成的量子比特，被嵌入钻石晶体中（Stas, 2022）。晶体用于存储光子量子比特。在这种情况下，固态量子存储实现了 20 毫秒的记录时长，且原子之间没有非纠缠（Ortu et al., 2022）。

## 6.5 原子与离子的基本结构
在描述原子的玻尔模型之前，应该提到原子内的原子位置并不精确；它们以概率来描述。这是薛定谔解释；量子粒子的位置形成电子云。电子不会沿固定路径移动；它们在称为电子云的区域中移动。围绕原子核的运动是波状的，是三维的，被称为轨道。

原子内部的能级是不均匀的。然而，它们大致用玻尔模型来描述。该模型解释了电子如何仅通过吸收或发射能量来跃迁轨道。玻尔有概率解释，但它是条件性的。也就是说，粒子与概率相关，但仅当粒子未被观测时。玻尔模型表明轨道内的能量量与其大小成正比。电子围绕中子和质子旋转；它们共同构成原子核。通常，它们在不发射或吸收能量的情况下旋转。能壳对应于具有不同轨道能级的能级。轨道标记为 `K`、`L`、`M` 和 `N`。定态轨道由稳定轨道内的电子组成。它们不辐射能量；轨道中的能量是固定的。只有某些轨道是稳定的；不稳定的轨道会产生辐射。电子在原子内永远不会静止；否则电子会落入原子核。电子离原子核越远，表示吸引力越小。电子势能与 `1/r` 成正比，其中 `r` 是到质子的距离。

当电子跃迁到较低能级时，会发射能量光子。光子的能量等于跃迁前后能级的差值。玻尔模型无法解释氢和氦光谱的细节。能量被归类为具有尖锐、主、弥散、基态（`SPDF`）电子。这是根据泡利不相容原理表征光谱线的方法。泡利不相容原理规定，如电子之类的费米子在同一状态中最多只能存在一个粒子。然而，两个粒子可以存在，但自旋不同。对于 `SPDF` 电子，亚壳层具有占据不同能级的轨道。`S` 中允许的最大数目为两个电子，`P` 中为六个电子，`D` 有十个电子，`F` 有 14 个。轨道按顺序标记为 `1`、`3`、`5` 和 `7`。乘以 2 得到每个壳层的最大电子数。



## 量子数和电子构型

量子数允许唯一识别特定电子。这些是按顺序给出的，`n`、`L`、`m[L]` 和 `m[s]`![方程](img/F000217si106.png)，分别代表能量、角动量、磁动量和角动量。主量子数是 `n`；它标识电子距离原子核的距离以及能量。轨道角动量量子数是 `L`；它标识轨道的形状。磁量子数是 `m[L]`，描述轨道的取向。电子自旋量子数是 `m[s]`![方程](img/F000217si107.png)；它表示顺时针或逆时针旋转。相应的自旋表示为 `1/2` 或 `−1/2`，也分别称为自旋下或自旋上。如前所述，同一轨道最多可容纳两个电子；此时一个自旋向上，另一个自旋向下。这是由泡利不相容原理导致的，该原理是费米子 Fock 空间中第 15.3 节的一个基本概念。

电子构型还使用亚壳层标记。它指定主量子数 `n`，标识电子壳层。其后跟字母 `S`、`P`、`D` 或 `F`，表示亚壳层内的轨道类型。最后有一个上标表示亚壳层内的电子数。电子先填充较低的壳层，然后再填充较高的壳层。这被称为构造原理或 Aufbau 原理（Scerri, 2013）。

失去或获得电子的原子称为离子。当原子失去外层电子时，原子带正电，称为阳离子或正离子。当原子获得电子时，它变成负离子，也称为阴离子。

接下来给出在囚禁离子量子比特制备中使用的离子示例。然而必须提到，在离子阱量子制造中，扩展量子比特数量是困难的。

### Example 6.8

`Ca+` 离子是钙离子。它由钙原子失去其第四壳层、价壳层的 一个或两个电子而产生。核内存在 20 个质子，表示原子序数。该离子用于囚禁离子量子比特制备。该离子的电子构型为 `1s² 2s² 2p⁶ 3s² 3p⁶`。指数表示每个亚壳层的电子数。简而言之，它是 2、8、8，因为 `1s²` 表示两个电子，`2s² 2p⁶` 显示八个电子，而 `3s² 3p⁶` 再次显示八个电子。因此该离子带正电，因为 `Ca²+` 中只有 18 个电子。如果价轨道只失去一个电子，则电子构型为 `1s² 2s² 2p⁶ 3s² 3p⁶ 4s¹`，即 2、8、8、1.#

### Example 6.9

镱 `Yb` 离子也用于囚禁离子量子比特制备。在那里它被称为 `Yb 171`，由于其质量数，它是一种具有 101 个中子的同位素。`Yb` 有 70 个质子和 103 个中子。`Yb` 本身具有轨道结构，2、3、28、32、8、2。`Yb` 离子失去一个或两个价电子并带正电。#

自从使用囚禁离子制造量子比特以来，早在 1990 年代，主要的想法是利用它们制造通用计算机。在这一方向上，许多公司遵循了 DiVincenzo 关于如何构建量子计算机的标准（DiVincenzo, 2013）。这些计算机通常不是用于专门用途，如主要用于优化目的的 QAC。它们用于通用计算机，这里称为门定向计算机。DiVincenzo 标准共有七条，五条涉及计算机，两条涉及信息传输和量子信道的需求。这些标准通常被称为构建量子计算机的黄金标准。DiVincenzo 标准的第一条是获得具有明确定义的量子比特的可扩展系统。下一个基准是确保设备可以初始化为初始基准态，例如 `|0000000>`。至关重要的是量子比特具有较长的退相干时间。即需要在完成计算所需的时间内保持状态。拥有用于执行计算的通用量子门集以及基础门也是必须的。最后，对于计算机而言，必须具备测量能力。其他标准涉及通信。

类似的一套准则被用于半导体型量子比特，以用于量子门计算机。早期的量子点量子比特采用了 `Ga` 和 `As`。其后，`Si` 和 `Ge` 在量子点型量子比特的创建中取代了它们的位置。

### Example 6.10

下面给出了一些最著名的半导体材料的电子结构：

硅 `Si` 是原子序数为 14 的中性原子。其电子构型为 `1s² 2s² 2p⁶ 3s² 3p²`。

锗 `Ge` 是一种化学元素，原子序数为 32。其电子构型为 `1s² 2s² 2p⁶ 3s² 3p⁶ 3d¹⁰ 4s² 4p²`。简而言之，电子分布为 2、8、18、4。

镓 `Ga` 的原子序数为 31。电子构型为 `1s² 2s² 2p⁶ 3s² 3p⁶ 3d¹⁰ 4s² 4p¹`。它可以以离子形式存在；此时为 `Ga+`，电子构型为 `1s² 2s² 2p⁶ 3s² 3p⁶ 3d¹⁰ 4s²`。它也可以构型为离子 `Ga+³`![方程](img/F000217si108.png)，电子构型为 `1s² 2s² 2p⁶ 3s² 3p⁶ 3d¹⁰`。

砷 `As` 的原子序数为 33。其电子构型为 `1s² 2s² 2p⁶ 3s² 3p⁶ 3d¹⁰ 4s² 4p³`。#

## 6.6 Overview of qubit fabrication

量子比特本质上以两种不同的方式构建：有非固态平台，如囚禁离子和光子方法。第二种方式是使用固态器件。在固态情况下，最重要的方法是超导体。其次最重要的是量子点方法。最后，还有利用原子内缺陷的方法，例如金刚石中的 `NV` 中心。

*   • 囚禁离子是创建量子比特的原始方法之一。这些量子比特用于生产通用、门定向量子计算机。如前所述，离子是带电粒子；通常它是失去一个或多个电子的原子。中期九十年代的第一个量子比特由单个铍囚禁离子制成。激光控制剩余电子的离散能级。通常，这些能级用 `0` 或 `1` 表示。电磁场确保电子保持有序，以便可以识别它们。激光和无线电波用于切换量子比特的 `0` 或 `1` 属性。退相干对囚禁离子不是严重问题，因为它们未暴露于环境中。这些量子比特通过保持在黑暗真空中而得到保护。囚禁离子量子比特的问题在于难以制造大量，如前一节所述。然而，在第 6.7 节中，提供了这种类型量子比特制备的更详细描述。一台门定向 40 量子比特计算机最近被报道（IonQ Staff, 2023）。

*   • 中性原子是正负电荷相等的原子。这些实体与囚禁离子相似，但使用光来捕获原子并将其保持在位置。如常，量子比特被创建并进入叠加态。使用中性原子还允许更灵活的二维构型，因为不会限制原子之间的可能连接。这导致了创建量子比特之间纠缠的更简单方法。



## Qubit Types

### Superconducting Qubits
许多公司采用超导体作为创建、控制和传输量子比特的主要方法。冷却时，超导体从具有电阻的正常状态转变为几乎所有电阻都消失的状态。从振荡电流开始，然后冷却，电路就像一个量子比特一样起作用。这些量子比特必须保持低温；否则，它们会退相干。量子比特映射到两种状态之一，0 和 1，对应不同的能级。状态选择由无线电波控制。通过脉冲无线电波，可产生量子叠加。一个重要属性是实际电路通常存在于小型微芯片上。

超导材料是通过在两种金属之间夹入一层非常薄的绝缘体制成的，称为 `Josephson junction (JJ)`。它像一个并联电容的非线性电感器。从电学角度看，这与 第 6.1 节 中简要讨论的谐振子类似。在该器件中，由于金属电极的氧化通常导致信息丢失，退相干是一个问题。超导量子比特的另一个缺点是需要严格控制零点温度。对超导量子比特的更深入描述在 第 6.8 节 中，其中强调了产生电子对隧穿的 Andreev 反射。

### Quantum Dot Qubits
量子点 (`QDs`) 使用半导体材料来制造量子比特，但与 `JJ` 量子比特非常不同。量子点量子比特是在电子或空穴被限制在半导体内的静态势阱中时创建的。量子比特具有对应于电子自旋的状态。例如，`|0>` 表示自旋向上，`|1>` 表示自旋向下。这些状态 `|v>` 的叠加与通常一样描述为 `|v>=a |0> + b |1>`，其中 `a` 和 `b` 是复数。最近的制造涉及硅、`Si`、衬底。量子阱也使用 `Si` 构建。这类量子比特的一个巨大优势是与互补金属氧化物半导体 (`CMOS`) 的兼容性。使用这种半导体的主要优势是功耗更低。

### Defect-Based Qubits
一些公司利用材料晶格结构中原子内的缺陷或空隙。这种缺陷可能会改变材料内部的电子运动。这些缺陷可能是物质中存在的异原子或缺失的原子。缺陷还可能吸引并从而捕获电子。这一过程使得电子自旋可控。自旋，即旋转动量，被用于根据自旋向上或向下对电子进行 1 或 0 编码。使用量子缺陷的一个结果是对低温控制需求很小，从而导致更长的相干时间。最突出的缺陷型量子比特之一是涉及 `NV` 中心的自旋型量子比特，即 `NV` 中心在金刚石量子比特。在这种情况下，氮原子取代碳原子。这就形成了 `NV` 中心。已创建模板来实现这些缺陷图案。使用它们后，相干时间有所增加。另一个好处是建立量子比特纠缠更容易。

在 `NV` 方法中，正使用更便宜的材料替代钻石。氮空位出现在氮化铝中。在这里，发现电子自旋是可以控制的。此外，碳化硅也有缺陷，可与钻石类似使用。

### Photon-Type Qubits
光子型量子比特通常涉及偏振 `|0>` 和 `|1>`。它们通过旋转类型来区分。这些是 `H`、`V`、`D`、`A`、`R` 和 `L`，分别缩写为水平、垂直、对角线、反对角线、顺时针旋转 `R`，最后 `L` 表示逆时针旋转。方向由垂直或水平电场的使用来控制。通过向某些晶体发送信号使用激光，导致两个量子比特光子作为最大纠缠对发射。

### Topological Qubits
拓扑量子比特和利用 `Majorana` 量子比特的拓扑计算也在被考虑。两个 `Majorana` 粒子被认为是费米子。该粒子本身被归类为 `Bogoliubov` 准粒子——一种携带空穴和电子电荷的电子空穴。`Majorana` 粒子存在于相对较大的距离处，导致较长的退相干时间，从而使拓扑计算非常有前景。`Majorana` 量子比特在 第 6.8 节 中再次被提及，参考了电子和空穴隧穿的 Andreev 效应。

不同公司采用不同的量子比特制造方法。Intel 制造了硅量子点。在这里，使用全光学光刻将图案转移到涉及光敏材料的衬底上。IBM 主要采用诸如铌和铝等半导体材料，用于硅衬底上。这种特定量子比特称为超导转单量子比特。

离子阱制造与其他量子比特创建方法相比有明显不同。离子阱寿命长，而超导量子比特通常寿命较短。然而，硅超导更容易制造，而离子阱具有较长的相干时间。离子阱门制造是一个漫长的过程，但它可能不会像其他方法那样受到外部噪声或泄漏的影响 (Blinov 等, 2004; DiVincenzo, 2013)。

## 6.7 Trapped ions
本节对制造离子量子比特的程序进行了稍详细的描述。首先选择一种原子，例如钙、`Ca` (Hui, 2019)。然后将原子加热形成蒸气。对于 `Ca`，在约 900 摄氏度时形成气态。通过用光子轰击物质，将价电子剥离出来。接下来，使用射频 (`RF`) 或 `Paul` 阱将原子保持在单一位置。此时，利用多普勒冷却来降低离子的动能。这些离子接近静止状态。微波、激光和 `RF` 场用于控制离子。通过使用预定频率的激光来观测量子比特状态。这些离子不能用静电保持在稳定静止平衡状态。这是 `Earnshaw’s theorem` (Simon 等, 1995)。因此，离子被捕获在电极之间，使用振荡 `RF` 以及直流电位。

囚禁离子技术假设钙离子价壳层中剩下一个电子。然后在过程中，为了构建光学量子比特，会做出任意选择。在这里，基态量子比特 `|0>` 优选对应于玻尔模型中的 `4s¹` 状态。它可能自旋向上或向下，每种概率相等。接下来，必须选择对应于 `|1>` 的激发态。通过参考钙原子的规格，列出并识别了从 `4s¹` 到最近的亚壳层或轨道的距离。例如，从 `4s¹` 到 `397 nm` 的距离定位了电子在 `4p` 轨道上的轨道。其他轨道距离也在该规格中列出。综合考虑距离和相干时间，将在定义 `|1>` 量子比特时做出选择。在电子跃迁过程中，光子能量被诱导或释放。因此，可能使用对应于光学波长的频率的激光来选择电子，例如在 `3D` 轨道中。所得到的量子比特被指定为 `|1>`。叠加是通过 `Ramon` 传输创建的。它采用两束激光束，导致两个量子比特的叠加，`|0> + b |1>`。



一般来说，这些量子比特具有较长的相干时间。它们被用于大规模量子计算机。

离子阱量子比特存在三种不同的类型；有 Zeeman 离子阱量子比特、前面描述的光学离子阱量子比特以及超精细量子比特。它们也是使用不同类型的离子制造的。不同原子具有不同的属性，这些属性不仅影响制造，而且还决定控制、对噪声的敏感性以及观测能力。在任何情况下，Zeeman 囚禁离子量子比特对于被囚禁的 `Ca+` 离子的电子自旋叠加态具有较长的寿命。更多信息可参见 Ruster 等 (2016)。

光学量子比特和超精细量子比特都易于测量，并且使用离子的电子态制成。它们的区别在于量子比特能量分裂能级以及耦合。前者使用两个基态能级。后者使用电子基态和由微波频率分隔的激发能级。与超精细量子比特相比，光学量子比特的寿命更短。

超精细量子比特是使用两个不同的能级创建的：`Yb 171` 离子的超精细 `S` 和 `F` 能级。使用两种不同的量子比特类型可实现量子错误预防。这最大限度地减少了串扰误差。这种误差与散射光子在量子比特的信息内容中造成误差有关（Mattel, 2021）。

## 6.8 超导性和约瑟夫森结

Cooper 对的概念被详细解释。之后，超导性和 `JJ` 以及隧穿的主要原因被描述。它被称为 Andreev 反射。Cooper 对是超导性存在的基础。这些对也称为 Bardeen-Cooper-Schrieffer (`BCS`) 对。它们由两个电子或其他费米子组成，在低温下暂时结合在一起。标准金属中电子之间的吸引力导致电子或费米子的配对态。这些配对电子纠缠在一起，并在极低温度下凝聚到基态。因此，它们在超导体内部以零电阻流动且无散射；这是 `BCS` 理论。当纠缠粒子通过与环境的相互作用退相干时，纠缠被破坏。破裂的 Cooper 对称为 Bogoliubov 准粒子。稍后提到的隧穿的主要原因称为 Andreev 反射。Cooper 对的隧穿可以解释为带负电的电子进入超导体，同时带正电的空穴退出所致。

Cooper 对的总自旋为零，质量和电荷是单个电子的两倍。Cooper 对中每个电子的动量大小相等、符号相反。它们的能量小于费米能量，因此热能可以破坏结合。因此，在低温下会发现大量 Cooper 对。因此，在常规超导性中，对被认为是束缚的，常规超导性由电子-光子相互作用引起。量子效应产生超导性。这种聚集或配对是 Cooper 或 `BCS` 配对，但结合较弱。因此，只有在低温下才存在大量 `BCS` 对（Frolov, 2014）。

约瑟夫森结的描述遵循参考文献：Frolov (2014)。该介绍基于夹着非超导势垒的超导材料之间的相位差。势垒由金属 `N`、电介质 `D` 或甚至真空 `V` 组成。该物质夹在两个超导体 `S[1]` 和 `S[2]` 之间。由此产生的超导器件分别表示为 `S[1] N S[2]`、`S[1] D S[2]` 或 `S[1] V S[2]`。此外，假设 `S[1]` 和 `S[2]` 之间的分离形成一个窄结。这在 图 6.2A 中有所说明，如 Frolov (2014) 中所述和推导。这里，左侧的超导器件由波函数 `ψ[1]` = `n` `e` ^ ( `i` `ϕ[1]` ) ![Equation](img/F000217si109.png) 标记，而右侧的波函数指定为 `ψ[2]` = `n` `e` ^ ( `i` `ϕ[2]` ) ![Equation](img/F000217si110.png)。超导材料可以被认为是在隧穿效应下产生散射波函数的催化剂，如 第 6.3 节 中的 图 6.1D 所示。在 `S[1] N S[2]` 图示中，波函数在势垒区域 `N` 中减小，但不会减小到 Cooper 对无法隧穿通过势垒区域的程度。相位差由 `Δ` = `ϕ[2]` ![Equation](img/F000217si111.png) − `ϕ[1]` ![Equation](img/F000217si112.png) 给出，可能不等于零。超导体的相位差将是控制涉及超导性的物理性质的主要量。在整个过程中，必须保持过程相位相干性。建立了超导电流；这称为约瑟夫森超导效应。它可以被认为是 Cooper 对隧穿的结果。

![图 6.2 Cooper 对隧穿。基于 (Frolov, 2014)，(A) Frolov 势垒，(B) Cooper 对隧穿，(C) 电压-电流死区。](img/F000217f06-02-9780443136979.jpg)

图 6.2 Cooper 对隧穿。基于（Frolov, 2014），(A) Frolov 势垒，(B) Cooper 对隧穿，(C) 电压-电流死区。

简单说明 `JJ` 效应涉及非交流电流与电压 `V` 的关系，见 图 6.2B 的图表。该说明提供了一个时间平均描述；在该图中，电压 `V` 与超电流 `I` 相对。当电流从负临界电流 − `I[c]` ![Equation](img/F000217si113.png) 扫到正临界电流 `I[c]` ![Equation](img/F000217si114.png) 时，其电压值为零。相位称为超电流态。达到临界电流后，电压跃升并最终变为正常态，在该态下它像电阻一样作用。第一个 `JJ` 方程涉及超电流 `I`。它由两个超导体之间的相位差产生，`I` = `I[c]` ![Equation](img/F000217si115.png) `sin` ( `Δ` ) ![Equation](img/F000217si116.png)。当 `Δ` ![Equation](img/F000217si117.png) 从零变为 `π/2` 时，超电流相位存在。




# 安德烈夫束缚态和约瑟夫森效应

## 安德烈夫反射和束缚态

安德烈夫束缚态会产生超导性。安德烈夫反射发生在电子从第一个超导体传输到第二个超导体时。在这种情况下，电子会被反射为一个空穴，并且能量为其原始能量的负值。它的路径将与其原始路径重合。同时，一个库珀对进入半导体。图 6.2C 说明了电子从 `S[1]` 旅行到 `S[2]` 以及空穴反向旅行的安德烈夫反射过程。在这种情况下，空穴将到达第一个超导体并也会被反射。然而，现在它变成了一个能量为 `E′` 的电子。当没有偏压时，这些能量是等价的，`E=E′`。反射过程可以持续很长时间，形成无限循环。这有时被称为交叉安德烈夫反射 (`CAR`)。该过程是对称的，因为入射空穴也会被反射为出射电子。正电荷空穴安德烈夫反射和电子安德烈夫反射之间存在对称性。粒子在半导体之间处于束缚态，类似于量子点。态由于两个半导体之间的限制而形成离散谱。这些能级是各自半导体的费米能级。

## 束缚态形成的条件

束缚态形成的条件包括一次完整跃迁中的总相位为 `2π` 的倍数。这意味着必须存在整数个波长。因此，相位差被建模为多个相位差的组合。特别地，`2π` = `ϕ`[2]![方程](img/F000217si118.png) – `ϕ`[1]![方程](img/F000217si119.png) + `L` (`k` – `k′`) – `2` `arcos`(`E`/`Δ′`)，其中 `Δ` = `ϕ`[2]![方程](img/F000217si120.png) – `ϕ`[1]![方程](img/F000217si121.png) 且 | `arcos`(`E`/`Δ′`) | << `L` (`k` – `k′`)。这里，`L` 是结的长度，`k` 和 `k′` 与电子和空穴之间的相位差有关。另外 `arcos`(`E`/`Δ′`) 是由于限制能隙。该能隙是一个在费米能附近缺乏态密度的区域。这也被称为赝能隙。如果空穴和电子之间存在对称性，则 `k=k′`，`E[k]` = +- `c` `cos`(`Δ`/2)。当这种情况发生时，会产生束缚态的能谱。当结很长 `L` 且 `k` 与 `k′` 不同时，能量线性增长，`E[n]` = `h` `v` `L`/2 (`2π` (`n` + ½) + - `Δ`)。如前所述，存在类空穴和类电子的安德烈夫束缚态。对于类空穴束缚态，使用负号。然而，总能量为零。

## 能量表达式

`S[1]` `N` `S[2]` 跃迁期间安德烈夫反射的能量，即半导体-金属-半导体跃迁的能量，由 `E` = +- `c` `cos`(`Δ`/2) 给出。对于 `S[1]` `D` `S[2]` 结构，能量中需要一个值 `τ`。它是一个描述隧穿效应的透射值，且 `E` = +- `c` (`1` - `τ` `sin`²(`Δ`/2))^(1/2)。存在高阶库珀对隧穿，`I(Δ)` = `I[c]` `sin(Δ)` + `I[c]′` `sin(2Δ)` + …. 第一项用于库珀隧穿，第二项用于两个库珀对隧穿，等等。还有一个马约拉纳分数 JJ 效应；它提供能量 `E` = +- `c′` `cos`(`Δ`/2)。这导致 JJ 效应中出现 `4π` 周期 (Frolov, 2014)。另见 Frolov (2019)。

## 约瑟夫森方程

第二个 JJ 方程为 `2 e V = h ∂(Δ)/∂t`。它涉及 JJ 的时间依赖性并显示 JJ 的正常态。在临界电流以上，相位仍在变化。使用两种 JJ 效应表明存在交流电流，因此产生辐射。为了观察辐射，使用微波驱动沙皮罗台阶 (Kopnin, 2009)。这些台阶出现在超导量子干涉中，可以在与之前所示类似的电流-电压图中看到。约瑟夫森频率为 `2 e V / h`。对于任何 JJ，存在约瑟夫森能量；它是在结内储存的自由能 `W`。`W = ∫ I V dt = h/(2e) ∫ I dΔ`。超电流 `I = 2e/h ∂(W)/∂(Δ)`，其中 `W = E (1 – cos(Δ))`。

## RSCJ 模型

参考 图 6.3A，并联电路的每个分支中都有三个电流：JJ 超电流 `I = I[c] sin(Δ)`，它是非线性的。正常电流 `I[nc] = h/(2eR) dΔ/dt`，电荷电流 `I[cc] = C dV/dt = hC/(2e) d²Δ/dt²`。流经电路的总电流通常称为 RSCJ 模型；它是 `I(d²Δ/dt², dΔ/dt, Δ)`，RSCJ 代表电阻-超导-电容结。在任何情况下，`I(d²Δ/dt², dΔ/dt, Δ) = I[cc] + I[nc] + I = hC/(2e) d²Δ/dt² + h/(2eR) dΔ/dt + I[c] sin(Δ)`。该方程类似于谐振子方程。然而，如前所述，谐振子具有彼此等距的能级。先前给出的 RSCJ 模型的能级是不等间距的。见 图 6.3B。在该图中，底部两个能级用 kets 表示，`|0>` 和 `|1>`。在大多数量子应用中，最低的两个能级是最重要的。最底部的能级是 `|0>`，称为基态。在此态之上是激发态 `|1>`。在此应用中，余弦波包含这些能级。

![图 6.3 (A) 并联电路，(B) 余弦型边界内的能级。](img/F000217f06-03-9780443136979.jpg)

图 6.3 (A) 并联电路，(B) 余弦型边界内的能级。

对于普通的 LC 电路，能量-磁通图中的能级间距始终相等。在这种情况下，能级之间的距离等于 (`L*C`)^(-1/2)![方程](img/F000217si122.png)。此外，对于典型 LC 电路的线性方程，能级在抛物线型边界内描述。在图中所示的 RSCJ 模型中，如前所述，不等距的能级位于余弦波内。此外，能级之间的差异随着能量越来越高而越来越接近。能级间距不相等的原因是为了解决控制量子比特的问题。如果能级等距，则无法使用微波或激光精确操纵态。量子比特倾向于跃迁到越来越高的能级。为了创建量子比特，通常只使用两个底部的能级。获得不等距能级是使用非线性元件（如 JJ）的理由。

## 拓扑量子比特和参考文献

在超导体之间夹入新材料以实现拓扑量子比特的应用描述于 Zhu et al. (2022)。另外，安德烈夫效应的严格描述见 Dolcini (2009)。



存在三种类型的约瑟夫森量子比特：电荷量子比特、磁通量子比特和相位量子比特，除此之外还有混合量子比特。这些量子比特可以被认为是由约瑟夫森电感和结电容产生的非线性谐振器构成。这些 `JJ` 量子比特之间的基本区别在于创建所需的不同电路。在电荷量子比特中，使用了两个 `JJ`。在其他量子比特中，仅使用一个 `JJ`。与通常情况一样，能级并非等间距排列，并被描述为非线性势曲线中的平行能级，如 图 6.3B 所示。为电荷量子比特、磁通量子比特和相位量子比特提供离散能级边界的非线性势曲线分别为三次、四次和余弦形状。后者的形状在 图 6.3B 中有所说明。电荷量子比特也被称为库珀对盒。

单一转蒙量子比特由两个能级组成；这些量子比特被安置在介电基底上，并带有读出谐振器。激光通常控制处于最低两个能级的原子。如前所述，制作量子比特有多种技术。转蒙量子比特是一种对电荷噪声不敏感的超导电荷量子比特。`TRANSMON` 代表 TRANSmissiON 线分流等离子体振荡器量子比特。一个基底带有两个板，中间由非线性电感 `JJ` 型桥连接。其中一个带正电，另一个带负电。尺寸以微米计。基本概念再次是库珀对的转移（Blais 等，2020；Gambetta 等，2017）。

## 6.9 量子点

量子点 (`QDs`) 是半导体材料的纳米晶体。这些是半导体量子比特，但与 `JJ` 量子比特非常不同。量子点量子比特是在电子或空穴被限制在半导体内的静态势阱中时产生的。这会产生量子化能谱。量子比特具有对应于电子自旋的状态。例如，`|0>` 表示自旋向上，`|1>` 表示自旋向下。这些状态 `|v>` 的叠加与通常情况一样被描述为 `|v>=a |0> + b |1>`，其中 `a` 和 `b` 是复数。最新的制造工艺涉及硅 (`Si`) 基底。量子阱也是使用 `Si` 构建的。在 `Si` 的两侧，采用硅锗基底。电场控制量子比特，与可扩展纳米技术一致。`QDs` 也被称为人工原子。

在 `QD` 制造初期，1998 年，使用其他材料夹在不同类型的半导体之间，最初使用了 `Ga` 和 `As`。`Ga` 和 `As` 原子存在两个主要问题。它们具有有限的核自旋，并且存在超精细随机相互作用，从而导致量子比特在 20 ns 内本征退相干。这意味着，例如，叠加态 `|v>` 可能在平均 20 ns 内坍缩为 `|1>` 或 `|0>`。另一个问题是在这些材料中创建精确的局域振荡场来控制单个量子比特是困难的。补救措施是使用 `Si` 和 `Ge` 代替 `Ga` 和 `As`，尽管新物质具有更复杂的能带结构。从一开始，`QD` 技术的目标就是在面向门的量子计算机中使用量子比特。这涉及 Loss 和 DiVincenzo 关于使用半导体材料制造计算机的提案。另请参阅 第 6.5 节。使用 `Si` 和 `Ge` 可实现紧凑的高相干性和 CMOS 兼容的电栅。

最初，电荷也被用来确定状态，但如前所述，退相干再次成为问题。退相干是由于能量变化导致相位变化而引起的，从而导致退相干。结果是自旋量子比特目前用于 `QDs`。然而，自旋被转换为电荷并测量电荷。简而言之，电荷表示自旋。测量电荷很简单，但直接测量自旋很困难。自旋仅与环境弱耦合 (Loss, 1998)。衡量环境干扰量子比特的速率的两个标准是弛豫率和退相干率。弛豫率的倒数是弛豫时间 `T[1]`。它是自旋量子比特保持其状态的平均时间，而无需有意改变状态。自旋向上量子比特不应转换为自旋向下，反之亦然。在当今设备中，`T[1]=1 minute`。相干时间 `T[2]=100 microseconds` 是保持叠加的平均时间（Danon，2021）。

## 6.10 D-wave 绝热量子计算机和计算

实际的 D-wave `AQC` 高度屏蔽，并保持在接近真空以及接近绝对零度 0.015 K 的环境中。所需的总功率主要用于制冷。在低温区域存在磁通型量子比特的网格。电压和磁场用于控制量子比特。此外，这些源具有读取磁通量子比特的能力。存在超导环的晶格，每个环都像自旋向上或向下的粒子一样作用。稍后描述的编程参数被转换为电电流、电压和磁场。电能使量子比特处于叠加态。受控能量通过希尔伯特空间结构中描述的加法和标量乘法创建量子比特的张量积。因此，量子比特自旋是纠缠的。

由于 D-wave 计算机是 `AQC`；它只解决优化类型问题。因此，在退火过程中，量子比特搜索问题空间的可行区域。在退火循环结束时，得到基态。观察自旋状态后，可以进行后处理。该过程可能重复数千次。最终产品无法判断是否存在解，甚至是否是最优全局解。它只提供一个解。

问题表述最常使用二次无约束二元优化 (`QUBO`) 模型进行。尽管也采用了其他不太数学化的模型，但 `QUBO` 模型要么最大化要么最小化仿射形式的目标函数 `w=v′Qv+d`。这里，`v` 是一个 `n` × 1 的实值向量。量 `Q` 是一个具有实数元素的 `n` × `n` 上三角矩阵。优化不涉及 `d`；它只涉及 `v′Qv`。在此表示中，`v` 中的所有元组都是幂等的，即 `v[j]² = v[j]`![方程](img/F000217si123.png)。退火过程导致绝热搜索，而不是在标准计算机上进行暴力计算。使用 `AQC` 的结果可能不是最优解。它可能是次优解，但获取解不会花费一周或更长时间。



使用量子退火，量子比特穿过势垒试图找到最低能量态。退火周期在求解优化类问题时约为一微秒。目标函数可以写成一个最小化问题，即最小化 `w = ∑ a[i] v[i] + ∑_{i < j} b[j,k] v[j] v[k]`。量 `a[i]` ![方程](img/F000217si129.png) 位于 `Q` 的主对角线上，被称为权重。值 `b[j,k]` ![方程](img/F000217si130.png) 被称为强度，位于 `Q` 的非对角线条目上。量子比特最终会稳定到两种最终态之一：{0, 1}。对 `v[j]` ![方程](img/F000217si131.png) `v[k]` ![方程](img/F000217si132.png) 被称为耦合器；它允许一个量子比特在纠缠中影响另一个量子比特。值 `a[i]` ![方程](img/F000217si133.png) 和 `b[j,k]` ![方程](img/F000217si134.png) 被映射为电压、电流和磁场，以便操纵量子比特以发现全局最小值。

量子隧穿 D-wave 芯片从基态的哈密顿量开始。该态与其它的激发态之间存在最小能隙。能隙的大小恰好使能量不足以跃迁到更高态。该过程进行得非常缓慢。D-wave 构建了一款芯片用于在最近邻模型下进行优化。在芯片上，QUBO 问题将被映射为二次优化问题。该架构使用集成电路的交叉开关技术。接下来，给出一个示例来说明 D-wave 使用的仿射目标函数。它还强调了 QUBO 软件中使用的幂等运算（O’Malley et al., 2017）。

### 示例 6.11

对于二维示例，使用涉及仿射表示的记号，`w = v' Q v + d`，其中 `v = (x y)'`，而 `Q` 是下面给出的上三角 2×2 矩阵，后跟 2×1 向量 `Qv`，

$\\begin{matrix} \\begin{matrix} \\left| a \\right. & \\left. c \\right| \\\\ \\left| 0 \\right. & \\left. b \\right| \\\\ \\end{matrix} & \\begin{matrix} \\left| {ax} + {cy} \\right| \\\\ \\left| by \\middle| . \\right. \\\\ \\end{matrix} \\\\ \\end{matrix}$

![方程](img/F000217si135.png)

量 `w = v' Q v = a x² + c x y + b y² + d`。但是，由于在 QUBO 中幂运算是幂等的，这意味着 `x² = x` 且 `y² = y`。因此可得 `w = a x + b y + c x y + d`，这在 QUBO 中被称为谱。

### 示例 6.12

这里有一个简单的例子，`x` 和 `y` 的取值在 {0, 1} 中。目标是找到 `z = (x + y) = 0 mod 2`。这是 `x` 和 `y` 相等的情况，也是逻辑中的等价运算。将构造一个真值表。在 Spectrum 列中，当逻辑运算为真时，该列放置零。零表示获得最低能量的目标，0 < 1。

$\\begin{matrix} x & y & {{Spectrum} = w} & \\\\ 0 & 0 & 0 & {{Lowest}{energy}} \\\\ 0 & 1 & 1 & \\\\ 1 & 0 & 1 & \\\\ 1 & 1 & 0 & {{Lowest}{energy}} \\\\ \\end{matrix}$

![方程](img/F000217si136.png)

浏览上方的真值表可得出解 `y = x`。利用前一个示例的结果，可以构造仿射映射。

在这种情况下，谱值由前一个示例得出，`w = a x + b y + c x y + d`。必须找到 `Q` 和 `d`。为此，按行遍历真值表。代入 `x` 和 `y` 的值并使用谱值 `w`。对于第一行，所有值 `x`、`y` 和 `w` 均为零。因此，`0 = w = a 0 + b 0 + c 0` 得出 `d = 0`。从第二行，`1 = w = a 0 + b 1 + c 0` 显示 `b = 1`。使用第三行 `1 = w = a 1 + c 0` 推导出 `a = 1`。最后，最后一行 `0 = w = a 1 + b 1 + c 1 1` 得到 `c = -2`。因此，`w = x + y - 2 x y`。作为结果，`d = 0` 且 `Q =`

$\\begin{array}{ll} {|1} & {{- 2}|} \\\\ {|0} & {{\\mspace{22mu} 1|}.\\#} \\\\ \\end{array}$

![方程](img/F000217si137.png)

使用 AQC 时，必须指定一个目标函数，为某些变量提供能量水平。当这些变量达到该能量水平时，就会出现解。它对应于低能量态或以高概率出现的最低能量态。量子比特的最终态代表解。

D-wave 编程模型：
* 量子比特，`v[i]`：该值参与退火过程并在 {0, 1} 中达到最终态。量子比特通常利用量子叠加发生干涉。
* 耦合器，`v[i]`，`v[j]`：该对允许单个量子比特影响另一个量子比特，从而产生纠缠。
* 权重 `a[i]`：权重是分配给每个量子比特的实标量。它影响量子比特坍缩为最终态。这些量是矩阵 `Q` 中的对角元素。
* 强度，`b[i j]` ![方程](img/F000217si138.png)：这是分配给每个耦合器的实标量。它影响一个量子比特对另一个量子比特的控制。这些是 `Q` 的非对角元素。
* 目标，`Obj` 成本函数，在退火周期中被最小化。这就是 `w`。

## 6.11 绝热定理

绝热过程是一种缓慢而渐进的变化事件，其中量子系统避免跃迁态或改变量子数。绝热不变量 `I` 是能量除以频率的商，`E / w`。作为绝热过程的一个实例，考虑谐振子。在 示例 6.1 中，能级被表述为 `E[n] = h w (2n + 1)/2`。由于谐振子情况下的绝热不变量涉及整数，连续变化是不可能的。该过程必须在变化中进行离散或量子跃迁。大量其他量子系统具有离散谱，它们对应的能级在数值上会跃迁。在这些情况下，尤其是在缓慢变化条件下，会避免变化。另一个主要例子是 Bohr-Sommerfield (Hall, 2013) 的微型太阳系量子模型。在这种情况下，存在量子化条件，使得量子数在缓慢变化条件下不希望改变。对绝热过程及其与 Berry’s phase 关系的最好读解释，后者将在后面介绍，见 Zwanziger et al. (1990)。

本文所述的绝热定理以正式形式给出。它遵循 Zwiebach (2018) 的优秀阐述。具体而言，证明了使状态为真的薛定谔解 `Ψ(t)` 与瞬时本征态 `ψ(t)` 之差的误差为 `O(1/T)` 量级。该关系在持续时间为 `T` 的绝热过程中成立。符号上，`‖Ψ(t) - ψ(t)‖` 为 `O(1/T)` 量级，`t` 在 `[0, T]` 中。时间长度 `T` 是绝热过程的持续时间。哈密顿量的瞬时本征态 `ψ(t)` 是一个波函数 `ψ(t)`，具有性质 `H(t) |ψ(t)> = E(t) |ψ(t)>`。这里，`H` 是哈密顿量，`E(t)` 是能量本征值。如前所述，在缓慢变化的过程中很难进行量子跃迁，因为能级通常是离散的。绝热定理的正式说明如下。




受时间无关薛定谔方程启发，`H(t) |ψk> = Ek |ψk>`，`k = 1, 2, …`。绝热条件为含时薛定谔方程提供了一个近似解。该解涉及瞬时本征值和涉及哈密顿量的本征态方程。在这种情况下，必须在过程中能量缓慢变化。还假设所有能级相距甚远，即 `Ek` 与所有其他离散能级明显分离。此外，假设相邻能级之间满足以下不等式，`Ek−1 < Ek < Ek+1`。绝热定理为真实态 `|Ψk>` 提供了近似。它说 `|Ψk>` 大致等于 `e^(iθ[k]) e^(iγ[k]) |ψk>`。另一个必要条件是初始条件的相等，即 `|Ψk> = |ψk>`。这里，薛定谔方程在零时刻的近似解等于零时刻的瞬时能量本征态解。近似中的指数将在下一段中描述，以下分析仅为形式上的。

实值量 `θ[k]` 是能量本征态的动力学相位。动态相位由 `θk = −1/h ∫[0]^(t) Ek dt′` 给出。另一个实值量是 Berry 相位 `v[k]`；它也是实值的。Berry 相位由近似波函数与其导数的内积给出。该内积为 `v[k] = i <ψk, dψk/dt>`。此外，令 `γk = ∫[0]^(t) vk dt′`。接下来，将研究一个类似于 Berry 相位的量。它被称为耦合项，并涉及不同的能量态。目标是了解耦合项如何与哈密顿量相关，以及耦合项在多大程度上影响绝热过程。

要了解耦合项 `<ψn, dψk/dt>` 如何与哈密顿量相关，首先考虑 k 与 n 不同时的瞬时本征函数条件，`H(t) |ψk> = Ek |ψk>`。对该本征函数方程求微分得到 `dH/dt |ψ[k]> + H |dψ[k]/dt> = dE[k]/dt |ψ[k]> + E[k] |dψ[k]/dt>`。这里，最后一个恒等式只是两次使用了本征函数方程。接下来，在最后一个恒等式的两边左侧应用 bra 运算 `<ψn|`。该运算将前一方程中的项夹在中间。这样得到 `<ψn | dH/dt |ψ[k]> + <ψn | H | dψ[k]/dt> = <ψn | dE[k]/dt |ψ[k]> + <ψn | E[k] | dψ[k]/dt>`。再次使用本征函数方程 `H |ψn> = E[n] |ψn>` 并将其转换为涉及 bras 的方程。为了做到这一点，使用共轭并记住标量场是实数；因此，`<ψn | H = E[n] <ψn |`。此外，注意当 k 和 n 不同时 `<ψn | dE[k]/dt = 0`。把这些全部放在一起得到 `<ψn | dH/dt |ψ[k]> + E[n] <ψ(t) | dψ[k]/dt> = E[k] <ψn | dψ[k]/dt>`。注意最后两项有一个共同的内积，这正是耦合项。求解该项可得 `<ψn | dψ[k]/dt> = <ψn | dH/dt |ψ[k]> / (E[k] − E[n])`。最终结果是 `<ψn | dψ[k]/dt> = (dH/dt)_{n,k} / (E[k] − E[n])`，其中如前所述 `E[k]` 和 `E[n]` 不同。量 `(dH/dt)^{(n,k)}` 是哈密顿量矩阵导数中的 n,k 项。结论是耦合项会破坏绝热近似。每当哈密顿量导数中的 n,k 项很小时，就会发生这种情况。以下示例序列遵循 (兹维巴赫，2018)。

### 示例 6.13

这是一个说明绝热近似误差的例子。它表明随着时间 T 增大，误差按 1/T 减小。考虑一个哈密顿量 `H(t) = H[0]` 当 `t < 0` 时，`H[0] + H[1] t/T`，当 t 在 `[0, T]` 内时，以及 `H[0] + H[1]`，当 `t > T` 时。这里，`0 < T` 且 `0 < H[0] < H[1]`。参见 图 6.4A。对于 `t` 在 `[0, T]` 内，`dH/dt = H[1]/T`。近似中的所有误差都像 `1/T` 一样消失。

![图 6.4 遵循 Zwiebach 的绝热过程，(A) 哈密顿量，(B) 能量分离，(C) 路径交叉哈密顿量，(D) 非交叉路径。](img/F000217f06-04-9780443136979.jpg)

图 6.4 遵循 Zwiebach 的绝热过程，(A) 哈密顿量，(B) 能量分离，(C) 路径交叉哈密顿量，(D) 非交叉路径。

Landau-Zener 转变描述了本征函数 `ψ1` 和 `ψ2` 的绝热以及可能的非绝热变化。它们代表了分子在固定核的情况下的两种不同的电子排列，使得它们相距 R。 在 图 6.4B 中，给出了与相应本征函数相关的能量的示意图。例如，在此图中，`E1` 可能是基态中本征态波的能量，而 `E2` 是激发态的能量。在此图中，具有非极性和极性区域的两个能量函数作为横坐标上的 R 的函数出现。这里假设态在 `R = R[0]` 处改变特性。对于本征函数 `ψ1`，它在 `R[0]` 处从极性转变为非极性。对于第二个本征函数 `Ψ2`，则相反。如果 R 快速增加，则 `ψ1 → ψ2`。这是非绝热变化发生，但如果 R 缓慢变化，则本征函数将保持在其原始轨迹上。

哈密顿量方程为 `H(R) ψi = Ei ψi`，`i = 1, 2`。如果对所有 R 求解，则瞬时能量本征态如绝热定理所述找到。假设 R 是时间 t 的函数，则哈密顿量 `H(R(t))` 也是如此。相应的本征函数方程变为 `H(R(t)) ψi) = Ei) ψi)`，`i = 1, 2`。如果对所有 R 求解上部方程，则含时方程对所有 t 也成立。因此，瞬时能量本征态和本征值可从上面给出的上部方程得知。

### 示例 6.14

该示例说明了一个哈密顿量 H，即使它们的路径交叉，态也会保持在其轨迹上。 图 6.4C 说明了在时间与能量图中的瞬时本征向量的图。令 `H =`

```
\begin{matrix}
{|{{ct}/2}} & {\quad{0|}} \\
{\mspace{-22mu}{|0}} & {{{\mspace{-22mu}{- {ct}}/2}|},}
\\
\end{matrix}
```

![方程](img/F000217si147.png)



其中 `c` 是一个非负标量，其特征向量为 (1 0)′ 和 (0 1)′。在 图 6.4C 中，这些特征向量位于 45 度线上。对应的能量值为 `E[1]=ct/2` 和 `E[2]=−ct/2`。注意 `Ψ[1]`![方程](img/F000217si148.png)(t)=`e`^(−`i`/`h`∫[0]^(t)`E[1]`(t′)`d`t′)! 方程 |1>=`e`^(−`i``c``t`²/(4`h`))![方程](img/F000217si150.png) |1> 且 `Ψ[2]`(t)=`e`^( `i`/`h`∫[0]^(t)`E[2]`(t′)`d`t′)! 方程 |2>=`e`^( `i``c``t`²/(4`h`))![方程](img/F000217si152.png) |2>。这些是瞬时本征函数解。然而，在此情况下它们也是薛定谔方程的精确解。即 `i h`∂`Ψ[1]`(t)/∂t=`H` `ψ[1]`(t) 且 `i h``ψ[2]`(t)/∂t=`H` `ψ[2]`(t)；直接代入即可说明这一点。例如，对于第一个特征向量，`i``h`∂`e`^(−`i``c``t`²/(4`h`))/∂`t`= `i``h`![方程](img/F000217si153.png) (−2`i``c``t`/(4 `h`))=`c``t`/2.#

在前面提到的示例中，`ψ[1]` 的轨迹永远保持在 (1 0)′ 上。即使路径相交，原点处也没有影响。`ψ[2]` 也是如此。下一个示例则讲述了不同的故事。

### 示例 6.15

这次，假设哈密顿矩阵的对角项相同，但存在以复值非对角项形式的相关性。注意，尽管如此，矩阵仍然是自伴的。所以，`H=H*`= 

```
$\\begin{array}{ll} {|{{ct}/2}} & {\\mspace{23mu} H_{12}|} \\\\ {|H_{12}^{\\ast}} & {{{- {ct}}/2}|} \\\\ \\end{array}$
```

![方程](img/F000217si154.png)

轨迹再次在时间与能量图中示出，这次在 图 6.4D 中。在此情况下，路径不相交；然而，它们可以无限接近彼此。当 `H[12]` 趋于零时就会出现这种情况。有趣的情况是是否存在能隙，以及能隙有多大。要分析这种情况，请参阅图 5.4D。有四个感兴趣的点。它们是矩形与横坐标和纵坐标相交的位置。在纵坐标处，矩形与抛物线型图形相切。高度为 +− |`H[12]` |；这些也是时间 0 时的能量本征值。在横坐标上，矩形相交于 + −2`τ[d]`![方程](img/F000217si155.png)。该矩形的形状决定了绝热或非绝热过程。即，这两个参数 |`H[12]`![方程](img/F000217si156.png) | 和 `τ[d]`![方程](img/F000217si157.png) 决定了瞬时能量本征态是否发生变化，极性到非极性，即 (0 1)→(1 0)，或相反。当能隙较大时，绝热过程占主导，轨迹没有变化。当能隙很小时，例如接近零时，拉比频率 `w[12]=|H[12]|/h` 出现在矩形中，并发生非绝热过程。非绝热跃迁的概率计算为 `P`= `e`^(−2`π``w[12]``τ[d]`)= `e`^(−2`π``H[12]`²/(`h``c`))![方程](img/F000217si159.png)。该解涉及超几何函数（Lahiri, 2006）。附录 A.7 用 Sturm-Liouville 微分方程描述了超几何函数。#

Berry 相位，`v[k]`![方程](img/F000217si160.png)，被理解为几何相位，而 `θ[k]`![方程](img/F000217si161.png) 通常是一个随时间变化的函数。可以理解，Berry 相位描述了几何路径，仅取决于空间的演化，而不取决于时间。因此，这导致了 Berry 联络 `Ak=i<Ψk |Δ[R] |Ψk>`。这里，`R` 是构型空间中的向量，具有 `N` 个分量，即 `R` 是 `R^(N)`![方程](img/F000217si162.png) 中的向量，而 `Δ` 是梯度运算。特征向量不是唯一的；特征向量的任意非零标量倍也是特征向量。然而，态的范数为一。这意味着 `Ψ[k]`![方程](img/F000217si163.png)(R)′=`e`^(−`i``b(R)`)`Ψ[k]`![方程](img/F000217si164.png)(R) 也是特征向量，前提是 `b(R)` 为实值。使用新的本征态的 Berry 联络。代入并使用梯度运算得到 `A[k]`![方程](img/F000217si165.png)(R)′=`i<Ψ[k]`![方程](img/F000217si166.png)(R)`e`^( `i``b(R)` )![方程](img/F000217si167.png) |`Δ[R]`![方程](img/F000217si168.png) |`e`^(−`i``b(R)` )![方程](img/F000217si169.png) `Ψ[k]`![方程](img/F000217si170.png)(R)>=`A[k]`![方程](img/F000217si171.png)(R) + `Δ[R]`![方程](img/F000217si172.png)`b(R)`。这是规范联络下的规范变换。直观上，规范变换改变了尺度，而规范联络提供了原始尺度与新尺度之间的补偿。将规范变换应用于 Berry 相位不是规范不变的。因为 `γ[k]`![方程](img/F000217si173.png)(t)=∫[0]^(t)`v[k]`![方程](img/F000217si174.png)(t′)dt′，它也可以仅用 `R^(N)`![方程](img/F000217si175.png) 中的几何路径来写。在这种情况下，=∫[Γ]`A[k]`![方程](img/F000217si176.png)(R)dR。使用新特征向量的 Berry 联络给出 `γ[k]`![方程](img/F000217si177.png)(t)′=∫[Γ]`A[k]`![方程](img/F000217si178.png)(R)′dR=∫[Γ]`A[k]`![方程](img/F000217si179.png)(R)dR + ∫[Γ]`Δ[R]`![方程](img/F000217si180.png)d(R)。这表明除非构型空间中的运动是一个回路，否则 Berry 相位无法被观测。因此，只有在 2`π` 的倍数处，Berry 联络才是规范不变的（Zwanziger et al., 1990）。

## 参考文献

* Aharonov et al., 2014 Aharonov, D. et al., 2014. 绝热量子计算等价于标准量子计算。载于：Proc of FOCS-04，45th Annual IEEE Symposium on Foundations of Computer Science.
* Blais et al., 2020 Blais, A., et al., 2020. 电路量子电动力学。arXiv:2005, 12667.
* Blinov et al., 2004 Blinov, B., et al., 2004. 利用囚禁离子超精细量子比特的量子计算。QIP vol. 3, no. 1–5.
* Carson, 2014 Carson, B., 2014. 势阱，Physics and Astronomy dept., Carthage.
* Childs et al., 2001a Childs, A., et al., 2001a. 绝热量子计算综述。arXiv link.
* Childs et al., 2001b Childs A, Farhi E, Preskill J. 绝热量子计算的鲁棒性。*Phys Rev A*. 2001b;65:012322.
* Danon, 2021 Danon, J., 2021. 固态自旋量子比特，Gemini Center for quantum. NTNU. lcrostaic gates Quasi 1D constrictions.
* DiVincenzo, 2013 DiVincenzo, D., 2013. 量子计算机，于 TEDxEutropis.
* Dolcini, F. 2009 Dolcini, F. 2009. Andreev 反射。载于：Lecture Notes for XXIII Physics GradDays. Heidelberg.
* Finke, 2021 Finke, 2021. The Qunnect Company reported on demand electromagnetically induced transparency quantum type memory Storage networking industry association, quantum computing report, SDC.
* Frolov, 2014 Frolov. *Quantum Transport Lecture 12 Spin Qubits* 2014;.
* Frolov, 2019 Frolov S. *Lange Lecture: “Status of the Search forMajorana Fermions in Semiconductor Nanowires”* U. Pittsburgh 2019;.




* Gambetta 等，2017 Gambetta J, et al. 在超导量子计算系统中构建逻辑量子比特。 *Npj Quantum Inf.* 2017;3(1):2.
* Hall，2013 Hall B. 978-1-4614-7115-8 *数学家的量子理论* GTM Springer 2013;.
* Hui，2019 Hui, J., 2019. QC-Hoot 用囚禁离子构建量子计算机 Medium？.
* IonQ Staff，2023 IonQ Staff. IonQ Forte：首台软件可配置量子计算机。 *Internet* 2023;.
* Kopnin，2009 Kopnin, N., 2009. 超导理论导论，Cryocourse.
* Krauss，2013 Krauss B. 量子信息专题。 In: DiVincenzo D, ed. 量子信息处理 2013; 第 44 届 IFF 春季学校讲义。
* Lahiri，2006 Lahiri, S., 2006. 次高斯 Berry 定理 报告号 ISU-Stat-2004-21.
* Mattel，2021 Mattel N. 使用镱 171 囚禁离子量子比特演示 Rag-flops。 *IJSRP*. 2021;11.
* O’Malley 等，2017 O’Malley D, Vesselinvov V, Alexandrov B, Alexandrov L. 使用 D-wave 量子退火器的非负/二进制矩阵分解。 *arXiv:1704-01605* 2017;.
* Ortu 等，2022 Ortu A, et al. 在稀土掺杂晶体中存储长达 20 ms 的光子时隙量子比特。 *Npc Quantum Inf.* 2022;8:29.
* Ruster 等，2016 Ruster T, et al. 长寿命 Zeeman 囚禁离子量子比特，Springer Link，快速通信。 *Appl Phys B*. 2016;122 article number 254.
* Scerri，2013 Scerri E. Aufbau 原理的困境。 *Education in Chemistry*. 2013;50 Royal Society of Chemistry.
* Simon 等，1995 Simon M, et al. 自旋稳定磁悬浮。 *AJP*. 1995;65(4):286–292.
* Stas et al., 2022 Stas P, et al. 具有集成错误检测的鲁棒多量子比特量子节点。 *Science* 2022; [`doi.org/10.1126/science.add9771`](https://doi.org/10.1126/science.add9771).
* Wendin，2017 Wendin G. 超导电路中的量子信息处理：综述。 *Rep Prog Phys.* 2017;80(10):106001.
* Zhang 等，2018 Zhang J, et al. 在离子阱系统中利用绝热捷径实现绝热量子搜索算法。 *Phys Rev A*. 2018;98(5):052323.
* Zhu 等，2022 Zhu Z, et al. Dirac 费米子在 Al-MoTe[2]\-Al 结中多 Andreev 反射的相位调谐及约瑟夫森超电流。 *PNAS*. 2022;119.
* Zwanziger et al., 1990 Zwanziger J, et al. *Berry 相位* Lawrence Berkeley Labs, UC of Berkely 1990;.
* Zwiebach，2017 Zwiebach B. *量子物理：绝热近似* MIT OpenCourseWare 2017;.
* Zwiebach, 2018 Zwiebach, B., 2018. MIT 课程资料。

## 进一步阅读
* Farhi, 2001 Farhi, 2001. 绝热量子优化框架。 Science, [arrive.org](http://arrive.org).
* King King, 量子退火理论 Google TechTalks (Nishimori, 2015). arXiv:2202.05847.
* Liu et al., 2018 Liu J, et al. 应用于深度学习网络的绝热量子计算。 *Entropy*. 2018;20(5):380.

# 第 7 章
## 希尔伯特空间上的算子
### 摘要
第一部分提供了由从一个向量空间到另一个向量空间的所有线性算子组成的向量空间的 MSA 视图。内积被证明是非线性运算。本节还包括数值范围的定义以及示例。闭算子在下一节中描述，随后是最重要的函数类，即希尔伯特空间 `H` 中的有界函数。有界函数被证明等价于 `H` 上的连续函数。纯态和纯张量连同密度算子一起给出。还提供了更严格的纠缠描述。第 7.5 节引入迹类算子。下一节描述 Hilbert-Schmidt 类算子，并且极其重要，Cauchy-Bunyakovsky-Schwarz 不等式给出了说明。章节的最后一部分提供了紧算子类描述。

#### 关键词
自同态；自同构；闭算子；有界算子；纯张量；纯态；纠缠；迹类；Hilbert-Schmidt 算子；紧算子

## 7.1 线性算子，MSA 视角
量子技术中采用的最基本算子之一是线性映射。除非另有说明，本文件中的所有算子均为线性。它们满足稍后提到的线性条件。这些映射的众多示例之前已见过；它们包括在两个自变量中都线性的线性映射。还包括多线性运算和张量映射。两者在其所有运算对象上都是线性的。然而，共轭不是线性的，因此内积也是非线性的；它仅在第二个自变量上是线性的。这种非线性，仅在第一个自变量上共轭线性而在第二个自变量上线性，被称为斜厄米。涉及复数域 `C` 或 `R` 上的向量空间 `V` 和 `W` 的所有线性映射的集合形成一个向量空间。在利用 `MSA` 的此描述中，可以得出存在四种类型：`V-VECTOR`、`W-VECTOR`、`C-SCALAR` 和 `L-VECTOR`，均使用建议性记号。特别是，最后一种类型表示所有线性映射 `L(V,W)` 的类型，从向量空间 `V` 到向量空间 `W`。

向量空间结构和域结构的所有签名集与之前相同，不再重复。然而，存在一个包含一元算子名 `LIN` 的新签名集，且为：

`LIN`: `V-VECTOR` → `W-VECTOR`

![Equation](img/F000205si2.png)

此外，要成为线性，必须满足一个约束。它涉及具有类型 `V-VECTOR` 和 `W-VECTOR` 的向量空间以及相应的标量乘法和向量加法运算名。为此，首先用建议符号替换所有名称，即

* `LIN` 用 `T` 表示
* `V-VECTOR` 用 `u`、`v` 表示
* `Vv-ADD` 用 `+` 表示
* `Sv-MULT` 用 `·` 表示
* `W-VECTOR` 用 `w` 表示
* `Vw-ADD` 用 `+[2]` 表示
* `Sw-MULT` 用 `·[2]` 表示
* `C-SCALAR` 用 `a` 表示

线性条件如下：

1. 1) Linear: `T (a · u + v)=a ·[2] T (u) +[2] T (v)`

如前所述，从 `V` 到 `W` 的所有线性映射的集合用名称 `L(V,W)` 表示。当在 `L(V,W)` 中定义逐点加法和标量乘法时，它本身成为一个向量空间。此外，对于这种第四种类型，即 `L-VECTOR`，还需要相应的等式恒等式以确保 `L(V,W)` 是一个真正的向量空间。如前所述，与 `L-VECTOR` 相关的签名集涉及标量乘法 `SL-MULT` 和向量加法 `VL-ADD`。

因此表示如下：

* `L-VECTOR` 用 `S`、`T` 表示
* `VL-ADD` 用 `+[3]` 表示
* `SL-MULT` 用 `·[3]` 表示

实际上，前面提到的 `S` 和 `T` 本身是从向量空间 `V` 到向量空间 `W` 的线性映射。

`L(V,W)` 中映射所需的向量空间条件如下：

1. 2) Linearity: `((a ·[3] S) +[3] T) (v)=a ·[2] (S (v)) +[2] T (v)`



这个向量空间 `L(V, W)` 常常也记作 `Hom(V, W)`，它是所有从 `V` 到 `W` 的同态的空间。载体集合可以被定义，例如在选定基时。在这种情况下，线性映射可以在有限维中用矩阵表示。这里，通常的矩阵和向量运算与签名集合中的算子名称相关。

取向量空间 `V` 和 `W` 以及 `L(V, W)` 中的算子 `T`。如果 `V` 中 `u` 与 `v` 不相等这一条件意味着 `T(u)` 与 `T(v)` 不相等，则从 `V` 到 `W` 的映射被称为一一对应或单射。当 `T` 的值域为整个 `W` 时，则该映射称为满射或上射。当两者都成立时，存在逆映射：`T^(-1): W → V`，它也是线性的。在此映射下，空间 `W` 与 `V` 也是同构的。

如果 `V=W`，当线性映射的复合被定义时，所有线性映射的向量空间成为一个代数。所得结构记作 `End(V)`，称为自同态集合。这些变换的定义域等于其值域，从而允许进行复合运算。这里 `S` 和 `T` 具有相同的定义域，定义域等于其值域，即它们将 `V` 映射到 `V`。复合运算 `C[S]` 本身是一个线性算子，定义为 `CS=S(T(.))`。也就是说，它为 `S` 和 `T` 创建映射的复合，这成为一种闭合、乘法类型的运算，但不一定是可交换运算。然而，当第 3.1 节中的恒等式 (1)、(2)、(3) 和 (4) 成立时，`End(V)` 成为一个含幺结合代数。含幺结合代数的多项图在图 3.1 中示出。假定 `End(V)` 中的所有算子都满足该图中所示的闭合运算。特别地，`V-ONE` 对应于恒等算子 `I`。就 `End(V)` 而言，含幺结合代数成立的等式恒等式涉及以下元素：

在 `End(V)` 中有 `S`、`T` 和 `P`，以及恒等映射 `I`。

在 `C` 中有标量 `a` 和 `b`

此外，与前面所述先使用算子 `T` 然后对 `V` 中的向量使用 `S`，即 `CS=S(T(.))` 不同，使用记号 `S·T`。该记号用于等式恒等式中：

1. 1) 结合律：`P·(S·T)=(P·S)·T`
2. 2) 分配律：`(a P + b S)·T=a P·T + b S·T`
3. 3) 分配律：`T·(a P + b S)=a T·P + b T·S`
4. 4) 恒等元：`I·T=T·I=T`

### Example 7.1

用在复合代替的乘法记号可能非常具有误导性，尤其是在无限维向量空间中。例如，对于 `End(V)` 中的 `S` 和 `T`，量 `S=T·T − 4 T − 5=T²–4 T − 5·I`，在因式分解时，或在使用 FOIL 法则时，需要有适当的证明。从算子演算的角度来看，`S=(T +1)(T − 5)`。然而，最后表达式是如何严格得到的尚不清楚。为了理解因式分解过程，写出 `S=T·T − 4 T − 5·I=T·T − 5 T + T − 5`。这仅使用向量空间运算。然后通过使用左分配律，编号 (3)，可得 `S=T·(T − 5) + 1 (T − 5)`。最后，使用前面提到的右分配律，编号 (2)，得到 `S=(T +1)(T − 5)`。

`End(V)` 中的单个元素 `T` 如果是一一对应且满射，即可逆，则称为 `V` 的自同构。因此，`T^(-1)· T=T·T^(-1)=I`。`V` 的所有自同构的集合构成一般线性群的一个实例，并用 `GL` 表示。该群将在涉及李群的后续章节中描述。在有限维中，`End(V)` 与 `n` 阶 `n` 阶复可逆矩阵的空间同构。

线性变换 `T` 的一个重要应用适用于某些希尔伯特空间。这一性质与半线性内积有关。在任意复希尔伯特空间 `H` 中最基本的结果是，只要对所有 `v` 在 `H` 中有 `<v, T v>=0`，则 `T=0`。这是因为对任意 `u` 在 `H` 中有 `<(u + v), T(u + v)>=0`，从而 `<v, T u>+<u, T v>=0`。这意味着 `<v, T u>=- <u, T v>`。重复此过程，这次使用虚数值，也得到 `<(u+iv), T(u +iv)>=0`，且 `<iv, T u>+<u, T i v>=0`。这意味着 `−<v, T u>+<u, T v>=0` 或 `<v, T u>=<u, T v>`，因此对所有 `u, v` 在 `H` 中有 `<u, T v>=0`，这意味着 `T=0`。对于实希尔伯特空间，该结果不成立，如下面的例子所示。

### Example 7.2

设希尔伯特空间 `H` 的载体集合为 `H=R²`，并使用由矩阵给出的线性算子 `T`：

$\\begin{matrix} {|0} & {{- 1}|} \\\\ {|1} & {\\mspace{20mu}{0|}} \\\\ \\end{matrix}.$

![Equation](img/F000205si3.png)

然后，对 `H` 中任意向量 `v=(a b)′`，有 `T(v)=(−b a)′`，且 `H` 中的内积为通常的点积，`(−b a)(a b)′=<v, T(v)>=0`，但 `T` 不为零。

### Example 7.3

另一个说明希尔伯特空间中线性算子 `A` 实用性的例子涉及数值域 `W`。数值域在刻画算子的谱方面非常重要。它用于量子计算中寻找特征值的粗略估计。数值域定义为 `W(A)={<v, A v>, such that ‖v‖=1, v in the domain of A}`。Toeplitz-Hausdorff 定理表明复平面上子集 `W(A)` 总是凸的（Gustafson, 1970）。

考虑 `H=C²`；目标是获得作为 2×2 矩阵给出的线性算子的数值域的信息，`A=`

$\\begin{matrix} {|2\\quad} & {i|} \\\\ {|{- i}} & {1|} \\\\ \\end{matrix}.$

![Equation](img/F000205si4.png)

`H` 中的单位向量首先代入 `W(A)=<v, A v>`，只是为了了解数值域提供什么信息。所以使用 `v=(i 0)′`，则 `A v=(2i 1)′` 且 `W(A)=<|q>, A||q>>=(−2i 1)(i 0)′=2`。类似地，如果 `w=(0 1)′`，则 `A w=(i 1)′` 且 `<w, A w>=(0 1)(i 1)′=1`。

为了获得数值域的更一般概念，考虑归一化的量子比特 `|q>`，给出为 2×1 列向量，`|q>=(cos(t/2) e^( *ip*) sin(t/2))′` 且 `t` 在 `[0, *π*]` 中，`p` 在 `[0, 2*π*)` 中。然后，2×1 向量 `A|q>=(2 cos(t/2) + i e^( *ip*) sin(t/2) −i cos(t/2) + e^( *ip*) sin(t/2))′`。内积 `<A|q>, |q>>=2 cos²(t/2) − i e^(− *ip*) sin(t/2) cos(t/2) + i cos(t/2) e^( *ip*) sin(t/2) + sin²(t/2)`。该量可以简化为 `W(|q>)=2 cos²(t/2) + sin²(t/2) + 2 sin(t/2) cos(t/2) sin(p)`。`W(|q>)=1 + cos²(t/2) + sin(t) sin(p)`。

通过绘制 `<A|q>, |q>` 随 `t` 和 `p` 在其定义域内变化的点轨迹，可以找到对应于 `W(A)` 的复平面子集。回想一下，前面给出的 `|q>` 是 `H` 中除任意相位外的最一般量子比特。然而，如果使用，全局相位在使用 `W(A)` 公式时会抵消。

对于任意复 `n`×`n` 矩阵 `A`，`W(A)={v* A v/(v * v), v nonzero in C}`，其中 `v*` 是 `v` 的共轭转置。这与前面提到的公式相同。此外，数值域的一个重要属性是内数值半径 `r(A)`。该量是从原点到 `W(A)` 边界的最短距离。即 `r(A)=min{|z|, such that z is on the boundary of W(A)}`。使用 math lab 模拟，对于此示例，`r(A)=0.382`。实际数值半径是 `W(A)` 中点 `z` 离原点的最远距离。即 `R(A)=max{|z| such that z is in W(A)}`。再次通过模拟，`R(A)=2.618`。在前面提到的示例中，由于数值域是实数，因此 `W(A)=[0.382, 2.618]`。这些值在后续章节中再次出现。



Hilbert 空间 `H` 中有以下两个重要的线性算子。增算子 `A` 满足其数值域的实部非负。也就是说，对 `A` 的定义域中的所有 `v`，`Re` (`<v, A v>`) 大于或等于零。作为增运算的一个实例，请参见前面的例子，因为 `W(A)` 本身是非负的。当 `-A` 为增算子时，称算子 `A` 为耗散的。这些算子在 Stone 定理的推导以及后文所述的 Lumer-Phillips 定理中都很重要。

## 7.2 Hilbert 空间中的闭算子

考虑算子 `T`，除非另有说明，否则它始终是线性的。设 `T` 属于 `L(D, H2)`。因此 `T: D → H2`，其中 `D` 是 `H1` 和 `H2` 的子空间，而 `H1` 和 `H2` 都是 Hilbert 空间。算子 `T` 称为闭算子，这意味着如果 `D` 中的 `vn` 收敛到 `v` 且 `Tvn` 在 `H2` 中收敛到 `w`，则 `v` 属于 `D` 且 `Tv=w`。子空间 `D` 是算子的定义域，记为 `dom(T)`。例如，在诸如全体复数 `C` 的域结构中，`dom(1/z)=C − {0 + 0i}`。算子为闭算子的等价定义涉及 `T` 的图。这里列向量是一个二元组；`(vn Tvn)′ → (v w)′` 蕴含 `(v w)′` 属于 `T` 的图。

算子为闭算子的更强条件意味着它是序列连续的。也就是说，对于收敛到 `v` 的 `H1` 中的每一个 `vn`，`Tvn` 在 `H2` 中收敛到 `w` 且 `Tv=w`。也就是说，算子 `T` 经常只定义在 `H1` 的子集的子空间上。当它在整个 `H1` 上定义并且是闭的时，它也是序列连续的。这是由闭图定理的推论，该定理实际上在 Banach 空间中成立（Rudin, 1991），另见附录 A.6。在欧几里得空间 `R^n` 中，`f: D → R^n`，其中 `D` 是 `R^n` 的子集，则 `f` 在 `D` 中的点 `v` 处连续当且仅当对所有满足 `vn → v` 的 `D` 中的序列 `vn` 都有 `f(vn) → f(v)`。因此在这些条件下，序列连续性确实蕴含连续性。

### 示例 7.4

设 `T: R → R`，其中 `T(0)=T0=0`，而在其他地方 `T(t)=1/t`，`T` 在 `R` 上不连续。然而它是闭算子。这可以通过取 `R` 中收敛到 `R` 中 `v` 的任意序列 `vn` 得到。显然，`+−∞` 不是任何此类收敛序列的极限。`R` 中除零外的任意点 `v` 都可能是 `vn → v` 的情况。因此自动有 `Tvn → w=1/v`。这意味着在 `R − {0}` 的所有点处序列连续。由于原点在图上是孤立点，这意味着 `T` 是闭算子。注意 `T` 在原点处不是序列连续的。全零序列确实收敛到零。`T0, T0, …` 序列也收敛到零。然而序列 `1, 1/2, 1/3` 收敛到零，但 `T1, T1/2, T1/3, …=1, 2, 3, …` 趋向于 ∞。

此外，由于收敛只涉及由 Hilbert 空间诱导的范数，`T` 通常定义在诸如 Banach 空间之类的赋范向量空间上。前述定义对无限维向量空间的这些扩展很重要，将在后面的章节中介绍。最后，前文提到的序列连续条件蕴含连续性，因而蕴含有界性。这些关系将在下一节中连同若干证明一起描述。

## 7.3 有界算子

或许，量子力学中最重要的线性算子是从一个 Hilbert 空间到另一个 Hilbert 空间的有界算子。即使位置和动量算子无界也是如此。设 `T` 属于 `L(H1, H2)`，其中 `H1` 和 `H2` 是 Hilbert 空间且 `T: H1 → H2`。则称 `T` 为有界，这意味着存在 `M > 0`，使得对 `H1` 中的所有 `v` 都满足范数不等式或 Lipschitz 条件：

1. 1) Lipschitz 条件：`‖T(v)‖` 小于或等于 `M ‖v‖`。

回忆 `<T(v), T(v)>=‖T(v)‖²`。所有此类 `M` 值的下确界称为 `T` 的算子范数，记为 `‖T‖`。有界的等价条件是线性算子序列连续；在这种情况下：

2. 2) 序列连续性：对于每一个序列，设 `v, v[n]` 在 `H1` 中，`n=0, 1, …` 若 `v[n] → v`，则 `T(v[n]) → T(v)`。

当 `T` 有界时，求 `‖T‖` 的另一个公式是取上确界

`‖T(v)‖/‖v‖` 对非零 `v`。等价地，可以对 `‖v‖=1` 的 `‖T(v)|` 取上确界。为此，使用 sup`‖T(v)‖/‖v‖=c`，对非零 `v`，则当 `‖v‖=1` 时，该 sup `‖T(v)‖` 也等于 `c`。反过来，如果 sup `‖T(v)‖/‖v‖` 对 `‖v‖=1` 等于 `c`，则任取非零向量 `w`。由于 `v` 的范数为一，设 `v=a w`。将 `v` 代入范数表达式，sup `‖T(v)‖/‖v‖=|a| sup ‖T(w)‖/(|a| ‖w‖)=|a|/|a| sup ‖T(w)‖/‖w‖=sup‖T(w)‖/‖w‖=c`。

该范数称为算子范数，在证明三角不等式时很有用。该不等式是证明所有有界算子的向量空间是赋范向量空间的关键结果。为此，设 `‖v‖=1`，其中 `v` 在 `H1` 中，且 `S` 和 `T` 是从 `H1` 到 `H2` 的有界算子。则 `‖S + T‖=sup ‖(S + T)(v)‖=sup ‖S(v) + T(v)‖`；这由线性性得出。现在后者的上确界是 Hilbert 空间 `H2` 中向量和的范数，且三角不等式在那里成立，由内积的定义可知。因此，`‖S + T‖` 小于或等于 sup `[‖S(v)‖ + ‖T(v)‖]`，而后者小于或等于 sup `‖S(v)‖` + sup `‖T(v)‖=`‖S‖ + `‖T|`，因为 `‖v‖=1|`。

在仅由 `V-ZERO` 组成的平凡向量空间中，任何算子的范数为零。文本中以下所有向量空间都假定不是 `V-ZERO`。从 `H1` 到 `H2` 的所有有界算子的集合记为 `B(H1, H2)`；此外，它是一个 Banach 空间。这意味着算子的每一个 Cauchy 序列都收敛，即该赋范向量空间是完备的。每当 Hilbert 空间是有限维时，所有线性算子都是有界的。此外，可以采用矩阵运算来处理来自相应载体集合的元素。下面给出一个例子。

### 示例 7.5

设 Hilbert 空间为 `H=C²`，并考虑算子 `T: H → H`，其中 `T` 由 2 x 2 复矩阵给出：

$\\begin{matrix} {|2} & {i|} \\\\ {|0} & {1|} \\\\ \\end{matrix}.$

![方程](img/F000205si5.png)

目标是使用 sup `‖T(v)‖` 对 `‖v‖=1` 求范数 `‖T‖`。单位范数的向量如前所述，由描述量子比特的 2×1 列向量定义，`v=|q>=(cos(t/2) e^(ip) sin(t/2))′`。这里的撇号表示转置。此外，值 `t` 在 `[0, π]` 中，`p` 在 `0, 2π)` 中。然后形成矩阵向量乘积 `T|q>=(2 cos(t/2) + i e^(ip) sin(t/2) e^(ip) sin(t/2))′`。使用 1×2 行向量乘以 2×1 列向量，从而形成内积，得到范数平方。这给出 `‖T|q>‖²`=(2cos(t/2) − i e^(−ip) sin(t/2) e^(−ip)sin ![方程 (t/2))·(2cos(t/2) + i e^(ip)sin ![方程](img/F000205si7.png) (t/2) e^(ip)sin ![方程](img/F000205si8.png) (t/2))′=4 (cos(t/2))² + 2i (−e^(−ip)sin ![方程](img/F000205si9.png) (t/2) cos(t/2) + e^(ip)sin ![方程](img/F000205si10.png) (t/2) cos(t/2)) + (sin(t/2))² + (sin(t/2))²=2 + 2(cos(t/2))² + 4 sin(p) sin(t/2) cos(t/2)=2 + 2(cos(t/2))² ![方程](img/F000205si11.png) + sin(p) sin(t)/2。因此，当 `p=π/2` 且 `t` 不远离零时，`‖T(v)‖²` 的最大值被得到，从而给出 `‖T‖` 约等于 2.25。

### 示例 7.6

算子范数将再次求出，算子为 `T: H → H`，其中 `H=C²`；`T` 再次由 2 x 2 复矩阵给出：

$\\begin{matrix} {|2} & {i|} \\\\ {|0} & {1|} \\\\ \\end{matrix}.$

![方程](img/F000205si12.png)



This time, the `SVD` described in Section 5.8, in a modified form will be applied. An important use of the `SVD` with the complex scalar field is in finding the operational norm of a matrix operator. Here, `‖T‖` is the square root of the largest eigenvalue of `T*T`. Calculating `T*T`, for the matrix above, yields:

$\\begin{matrix} {{|4}\\mspace{27mu}} & {{2i}|} \\\\ {|{- 2i}} & {{2|}} \\\\ \\end{matrix}.$

![方程](img/F000205si13.png)

The characteristic equation is `λ`²–6 `λ` + 4=0. The eigenvalues are about `λ[1]`=5.2 and `λ[2]`=0.76. So `‖T‖`=(5.2)^(1/2)![方程](img/F000205si14.png), which is (3 + 5^(1/2))^(1/2), and it is about 2.25 again.

### 示例 7.7

Consider the momentum-type differential operator `D` in `H=L² [0, 2π]`. This is the set of all complex-valued square-integrable functions on `[0, 2π]`. `D` is defined on the set `C¹` of continuously differentiable functions, which is dense in `H` since all polynomials are in this set. The sequence, `e^(tni)`, `n=0, 1, 2, …`, are in `C¹` along with their derivatives with respect to `t`. These derivatives are `D(e^(tni))=ni e^(tni)`. The values for the norms squared, in this case, are integrals of absolute value squared quantities. Therefore, using the inner product and conjugating the first entry in the integral whose limits are 0 to 2π gives `‖D (en^(tni)) ‖²=∫`![方程](img/F000205si15.png)`[−ni e^(−tni) ni e^(tni) dt]`, which equals 2π `n²`. Also, `‖e^(tni)‖²=∫`![方程](img/F000205si16.png)`[e^(−tni) e^(tni) dt]=2π` and `‖D (en^(tni))‖/‖en^(tni)‖=n`. This shows that the momentum operator is not bounded in `H`.

Bounded operators `T` and continuous operators are one and the same. In fact, bounded or continuous operators are Lipschitz continuous, which is even stronger than uniform continuity. To see this, let `T` be bounded, so that `‖T (v)‖` is less than or equal to `M ‖v‖` for all `v` in the Hilbert space `H`. Letting `v=w − z` gives the desired Lipschitz condition: `‖T (w−z)‖` is less than or equal to `M ‖w − z‖`. Going the other way, using the contrapositive, if `T` is not bounded, then it will be shown that `T` is not continuous. For every positive integer `n`, since `T` is assumed not bounded, there is a unit vector `v[n]` in `H` with `‖T(v[n])‖` greater than or equal to `n`. Taking the sequence `w[n]=(v[n] / n)`, which goes to zero as `n` goes to infinity, shows that `T` is not continuous at zero. This follows since `‖T(w[n])‖=‖T(v[n])‖/n` is greater than or equal to one, as `n` goes to infinity.

More often then not, bounded operators do not commute. An important related concept is intertwining, a concept needed when spectral theory is described. Let `P` and `S` be bounded and have the same domain, with domain equal to their codomain. A bounded operator `T`, in the same space, is said to intertwine `P` and `S`, which means that for all `v` and `w` in `H`, it follows that: If `P (v)=w`, then `S (T (v))=T (w)=T (P (v))`. When inverse operators exist for `P` and `S`, then `T` intertwines them also.

An additional property follows, namely that if `S` is in `B (H1, H2)` and `T` is in `B (H2, H3)`, where `H3` is also a Hilbert space, then `T S=T (S (.))` is in `B (H1, H3)`. Additionally, `‖T (S (v))‖[3]` is the norm involving `H3`. It is less than or equal to `‖T‖ ‖S (v)‖[2]`, where the latter norm is in `H2`. This quantity is less than or equal to `‖T‖ ‖S‖ ‖v‖[1]`, with the last norm in `H1`. Accordingly, `‖T S‖` is less than or equal to `‖T‖ ‖S‖`.

The next section provides a pragmatic view for the definition of states in a Hilbert space, but first, a precise definition is the following: A state is a positive linear functional `f`, on a `C*` algebra, `A`, where `f: A → C`, and `C` is the complex field of scalars. Moreover, for all `T` in `A`, `f (T*T)` must be greater than or equal to zero, and most importantly, this functional operating on the `C*` identity element must equal one, `f(I)=1`. In a later chapter, the most rigorous specifications such as these along with applications of states will be provided.

## 7.4 纯张量与纯态算子

Recall that a state `ρ`![方程](img/F000205si17.png) on the Hilbert space `H` is a positive linear trace class map: `H → H`, such that `Tr (ρ)=one`. It is pure when there exists a vector `v` in `H` such that `ρ`![方程](img/F000205si18.png) `(u)=[<v,u>/<v,v>] v`. Pure states are denoted here by `ρ[v]`.

An element `z` of Hilbert space `H1 ⊗`![方程](img/F000205si19.png)` H2` is said to be simple or called a pure tensor, which means that there exist vectors `v` in `H1` and `w` in `H2` such that `z=v ⊗`![方程](img/F000205si20.png)` w`. This is wrongly called a pure state or sometimes a separable state in quantum computing. 图 7.1 shows the formation of a simple element. The density operator is defined as a pure state. An operator `ρ[z]`,![方程](img/F000205si21.png) which maps a Hilbert space `H` into itself, is said to be a density operator, which means that `ρ[z]`![方程](img/F000205si22.png) is a linear trace class operator, `ρ[z]`![方程](img/F000205si23.png) `(-)=(<-, z>/<z, z>)z`. In short, a trace class operator is `T`, such that the sum of the series of inner products of the form `<ek, T ek>` converges to the same value for any ON basis `{ek}` of `H`. The next section describes trace class operators in more detail.

![图 7.1 Simple elements in H1 \otimesEquation H2 and pure states.](img/F000205f07-01-9780443136979.jpg)

图 7.1 Simple elements in `H1 ⊗`![方程](img/F000205si1.png)` H2` and pure states.

A general element `z` of `H1 ⊗`![方程](img/F000205si24.png)` H2` involves some basis from `H1` and `H2`, say

`z=a11 e1 ⊗`![方程](img/F000205si25.png)` f1 + a12 e1 ⊗`![方程](img/F000205si26.png)` f2 + a21 e2 ⊗`![方程](img/F000205si27.png)` f1 + a22 e2 ⊗`![方程](img/F000205si28.png)` f2`, where `{e1, e2}` and `{f1, f2}` are bases for `H1` and `H2`, respectively. The tensor is called pure if the designated products of coefficients are equal, namely `a11 a22=a12 a21`. Here, `| a11 |² + | a12 |² + | a21 |² + | a22 |²=1`, and `aij` are in `C`.

### 示例 7.8

The tensor `z=2^(−1/2) (|0 1> + |1 1>)=2^(−1/2) (|0 >⊗ |1> + |1> ⊗ |1>)`. In this case, `a11=0`, `a12=2^(−1/2)`, `a21=0`, and `a22=2^(−1/2)`; therefore, this is a pure tensor.

### 示例 7.9

Next, for instance, one of the Bell states (Nelson, 2010), `z=1/2^(1/2) (|0> ⊗`![方程](img/F000205si29.png)` |0> + |1> ⊗`![方程](img/F000205si30.png)` |1>)`, is a nonpure tensor or a nonsimple element of Hilbert space `H1 ⊗`![方程](img/F000205si31.png)` H2`. This follows since `a11=2^(−1/2)`, `a12=0`, `a21=0`, and `a22=2^(−1/2)`.

Additionally, any other basis utilized for describing this Bell state will again not satisfy the identity, `a11 a22=a12 a21`. The next example illustrates the construction of a pure state and the map, `ρ[z]`![方程](img/F000205si32.png)`: H → H`.

### 示例 7.10



设 `H`=`C²`，并考虑态矢 `|z>`=`1/(2 ^(1/2))` ⋅![Equation](img/F000205si33.png) (`|0>` +i ⋅![Equation](img/F000205si34.png)`|1>`)；目标是找到与该 `H` 中简单元素对应的纯态映射 `ρ[z]`![Equation](img/F000205si35.png)。利用伴矢：`<z|`=`1/(2 ^(1/2))` ⋅![Equation](img/F000205si36.png) (`<0|` + − i ⋅![Equation](img/F000205si37.png) `<1|`)，则 `<z, z>`=1，且 `ρ[z]`![Equation](img/F000205si38.png) 是一个纯态。现在将选取 `H` 的另一个简单元素，并观察 `|u>` 在 `ρ[z]`![Equation](img/F000205si39.png) 下的像。设 `|u>`=`1/(2 ^(1/2))` ⋅![Equation](img/F000205si40.png) (`|0>` + − 1 ⋅![Equation](img/F000205si41.png) `|1>`)，因为内积为 `<z, u>`=(1+ i)/2；由此可得 `ρ[z]`![Equation](img/F000205si42.png)(`u`)=((1+ i)/2) ⋅![Equation](img/F000205si43.png) `|z>`=((1+ i)/((2)^(3/2))) ⋅![Equation](img/F000205si44.png) (`|0>` + i ⋅![Equation](img/F000205si45.png) `|1>`)=(2 ^(1/2) `e`^( `i` `π`/4)![Equation](img/F000205si46.png)/((2)^(3/2))) ⋅![Equation](img/F000205si47.png) (`|0>` + i ⋅![Equation](img/F000205si48.png) `|1>`)=1/2 ⋅![Equation](img/F000205si49.png) (`|0>` + i ⋅![Equation](img/F000205si50.png) `|1>`).

以下为第 4.10 节中的等式恒等式。它们在描述纠缠和非纠缠时是必需的，如下所述。

希尔伯特空间张量积的等式恒等式：

1. 1) 线性：`c x (v1 ⊗ v2)`=`(c x v1) ⊗ v2`=`v1 ⊗ (c x v2)`.
2. 2) 分配律：`(v1 + w1) ⊗ w2`=`v1 ⊗ w2 + w1 ⊗ v2`.
3. 3) 分配律：`v1 ⊗ (v2 + w2)`=`v1 ⊗ v2 + v1 ⊗ w2`.
4. 4) 内积：`< v1 ⊗ v2, w1 ⊗ w2 >`=`<v1, w1> <v2, w2>`.

纯态 `ρ[z]`![Equation](img/F000205si61.png) 在希尔伯特空间 `H1 ⊗ H2` 中被称为非纠缠，这意味着存在在 `H1` 中作用的纯态 `ρ[v]`![Equation](img/F000205si62.png) 和在 `H2` 中作用的纯态 `ρ[w]`![Equation](img/F000205si63.png)，使得张量积：`ρ[v]⊗ρ[w]` = `ρ[z]`![Equation](img/F000205si65.png)。一个最重要的事实是，纯态 `ρ[z]`![Equation](img/F000205si66.png) 是非纠缠的当且仅当对于 `H1` 中的 `v` 和 `H2` 中的 `w`，有 `z`=`v ⊗ w`，即当 `z` 是 `H1 ⊗ H2` 的一个简单元素时。这可以通过参考希尔伯特空间张量积的定义来看到。利用等式恒等式：4) 内积，其中 `v1` 和 `w1` 在 `H1` 中，`v2` 和 `w2` 在 `H2` 中；则该恒等式为 `<v1 ⊗ v2, w1 ⊗ w2>`=`<v1, w1> <v2, w2>`，于是将其应用于纯态：`ρ[z]`=(<z, ->/<z, z>) `z`=(<v ⊗ w, ->/< v ⊗ w, v ⊗ w>) `v ⊗ w`=(<v, ->/<v, v>) (<w, ->/<w, w>) `v ⊗ w`。然后利用希尔伯特空间张量定义中的 1) 线性重新排列：(<v, ->/<v, v>) `v` ⊗ (<w, −>/<w, w>) `w`=`ρ[v]`![Equation](img/F000205si77.png) ⊗ `ρ[w]`![Equation](img/F000205si79.png)。

可以看出，纯态 `ρ[z]`![Equation](img/F000205si80.png) 在希尔伯特空间 `H1 ⊗ H2` 中被称为纠缠，这意味着不存在在 `H1` 中作用的纯态 `ρ[v]`![Equation](img/F000205si82.png) 和在 `H2` 中作用的纯态 `ρ[w]`![Equation](img/F000205si83.png)，使得张量积 `ρ[v]⊗ρ[w]` = `ρ[z]`![Equation](img/F000205si85.png) 成立。混合态当且仅当它不能写成形如 `ρ[z]` = `ρ[v]⊗ρ[w]`![Equation](img/F000205si87.png) 的纯态的凸组合时才是纠缠的。在下一个例子中，我们将展示希尔伯特空间中元素的张量积如何产生希尔伯特空间上的非纠缠态。

### 例 7.11

作为 `H1 ⊗ H2` 中非纠缠纯态 `ρ[z]`![Equation](img/F000205si88.png) 的例证，考虑 `ρ[u]`![Equation](img/F000205si90.png) 和 `ρ[v]`![Equation](img/F000205si91.png) 均为纯态，分别在 `H1`=`H2`=`C²` 中。假设 `ρ[z]` = `ρ[u]`![Equation](img/F000205si92.png) ⊗ `ρ[v]`![Equation](img/F000205si94.png)，且 `|u>`=(1/(1.414)) ⋅![Equation](img/F000205si95.png) (`|0>` + `|1>`)，而 `|v>`=(0.8 x `|0>` −0.6 x `|1>`)，其中 `|u>` 在 `H1` 中，`|v>` 在 `H2` 中。两个元素都是简单的，张量积 `|z>`= `|u> ⊗ |v>`=(1/(1.414)) ⋅![Equation](img/F000205si97.png) (0.8 ⋅![Equation](img/F000205si98.png) `|0, 0>` +0.8 ⋅![Equation](img/F000205si99.png) `|1, 0>` −0.6 ⋅![Equation](img/F000205si100.png) `|0, 1>` −0.6 ⋅![Equation](img/F000205si101.png) `|1, 1>`) 在 `H1 ⊗ H2` 中也是简单的。这表明纯态 `ρ[z]`![Equation](img/F000205si102.png) 是非纠缠的。 recall that the tensor is called pure iff `a11 a22`=`a12 a21`；否则，它是纠缠的。注意当这表示为 `C²` 中的向量时，可得 `|z>`=`|u> ⊗ |v>`=(1/(1.41)) ⋅![Equation](img/F000205si104.png) (0.8 ⋅![Equation](img/F000205si105.png) (1 0 0 0)′ +0.8 ⋅![Equation](img/F000205si106.png) (0 0 1 0)′ −0.6 ⋅![Equation](img/F000205si107.png) (0 1 0 0)′ −0.6 ⋅![Equation](img/F000205si108.png) (0 0 0 1)′)=

$\\begin{matrix} \\left( {1/1.41} \\right) & \\begin{matrix} \\left| .8 \\right| \\\\ \\left| - .6 \\right| \\\\ \\left| .8 \\right| \\\\ \\left| - .6 \\right| \\\\ \\end{matrix} \\\\ \\end{matrix}.$

![Equation](img/F000205si109.png)

`| z >` 的范数为 1。

对于希尔伯特空间 `H1 ⊗ H2` 中的 `z`，系数归一化时，`|a11|² + |a12|² + |a21|² + | a22 |²`=1，将 `ajk` 项替换为实部加 i 乘虚部得到七维球 `S⁷` 的方程。从前一节可知，单量子比特希尔伯特空间是 `S³`，因此双量子比特希尔伯特空间是 `S⁷`。Hopf 纤维化更详细地描述了这些球面。接下来，更一般地描述迹类算子。随后，这些算子被证明与希尔伯特-施密特算子密切相关。

## 7.5 跡类算子

迹类算子将迹运算从方阵推广到无限维。这些算子定义在希尔伯特空间上，所有迹类算子的集合构成一个巴拿赫空间。它们与紧算子空间以及有界算子空间密切相关。事实上，迹类算子的对偶空间是有界算子空间。此外，紧算子的对偶空间是迹类算子空间（Argerami, 2014）。

对于希尔伯特空间 `H` 上的线性算子 `T`，`T` 的迹是形如 `<ek, T ek>` 的内积之和的级数，其中 `{ek}` 是 `H` 的一个标准正交基。对于无限维希尔伯特空间，该级数必须收敛。通常，它是部分和序列的极限。在这种情况下，它记为 `Tr (T)`，结果必须与基无关。再次，要成为迹类，迹必须无论采用何种基都是有限的，并且定义和的所有极限必须相等。

### 例 7.12



# 希尔伯特空间算子

## 跡类算子

设 `H` 是一个有限的 `n` 维希尔伯特空间。对于任意 `n` by `n` 矩阵 `M`，前面定义的迹与矩阵上的通常迹运算一致。无论采用哪种 `ON` 基，都必须满足 `Tr(T)` 总是给出 `Trace(M)`。例如，使用载体集 `H=C²`。设基集为 `{i|0>, −1 |1>}={(i 0)′, (0 –1)′}`；然后使用这些 2 by 1 向量以及 `M`=

```
\begin{matrix} {|{4 - i}} & {{- 2}|} \\ {|3\mspace{27mu}} & {{- 2}|} \\ \end{matrix}
```

![Equation](img/F000205si110.png)

给出 `Tr(M)=<(i 0)′, M (i 0)′> + <(0 −1)′, M (0 −1)′ >`。所以：`Tr(M)=<(i 0)′, (4i+1 3i)′> + <(0 –1)′, (2 2)′>`。现在回忆内积是共轭线性的，因此左操作数应取共轭。因此，`Tr(M)=4 − i − 2=2 − i`。通过观察，`M` 的对角元素之和是 `M` 的迹。该结果与 `2 − i` 一致。

该例子的一个推广是，任何具有有限维值域的有界线性算子，即其值域为有限基数，是迹类的。然而，一般情况下，无限维情形可能不同。下一个例子适用于无限维希尔伯特空间，`H`。该例中的算子即使对于单个 `ON` 基给出有限迹，也不是迹类算子，但不适用于 `H` 的所有 `ON` 基。

### Example 7.13

设 `B={e0, e1, e2, …}` 是 `H` 的一个 `ON` 基。将证明算子 `T` 相对于基 `B` 的迹等于零，但相对于基 `F` 的值是无限的。设 `F={(1/ 2^(1/2)) (e1 − e0), (e2 − e1), (e3 − e2), …}`；它也是一个 `ON` 基。这可以通过形成内积来看出：`<fi, fj>=(1/ 2) <ei+1 − ei, ej +1 − ej>=1` 当 `i=j` 时和 `0` 否则。接下来，设 `T: H → H`，其中 `T` 通过转置相邻元素将基 `B` 映射到自身。它交换彼此相邻的偶数项和奇数项，反之亦然，即 `T(e2n)=e2n+1`，`T(e2n+1)=e2n`，`n=0, 1, 3, …`。注意无限和 `∑_i` ![Equation](img/F000205si111.png) `<(ei), T ei>=0`。但采用基 `F` 的无限和为 `∑_n` ![Equation](img/F000205si112.png) `<((1/ 2)^(1/2))(e2n+1 − e2n), (1/ 2)^(1/2)T(e2n+1 − e2n)>=` 无限和 `(1/ 2) ∑_n` ![Equation](img/F000205si113.png) `<e2n+1 − e2n, e2n - e2n+1>=` 无限和 `1/ 2 ∑_n` ![Equation](img/F000205si114.png) `− (‖e2n‖² + ‖e2n+1‖²)= −∞`。

迹类算子与下一节中定义的希尔伯特-施密特算子相似。

## 7.6 Hilbert-Schmidt operators

本节从希尔伯特空间中最重要的不等式之一开始。它是 Cauchy-Bunyakovsky-Schwarz 不等式，在整篇文档中简写为 `CBS` 不等式。该不等式对希尔伯特空间中的任意向量 `v` 和 `w` 都成立。然而，任何向量空间中正的半双线性形式也存在类似的不等式。

`CBS` 不等式是 `|<v, w>|`，它总是小于或等于乘积 `‖v‖ ‖w‖`。该结果通过考虑非负内积得出：`N=<v + a t w, v + a t w>`。这里，`a` 在 `C` 中且 `t` 在 `R` 中。为了看出该不等式成立，展开内积得到 `N=‖v‖² + a* t <w, v> + a t <v, w> + |a|² t² ‖w‖²`。接下来，将复常数 `a` 表示为 `a=<w, v>`，然后如果将该值代入上述 `N` 的表达式，则可得 `N=‖v‖² + 2 t | <v, w>|² + |<v, w>|² t² ‖w‖²`。注意 `N` 是一个二次多项式；它是关于 `t` 的抛物线。因为它是非负的，所以它最多在 x 轴上接触一次。因此，其判别式为负或零。所以，判别式 `4 | <v, w> |⁴–4 ‖v‖² | <v, w>|² ‖w‖²` 为负或零。注意如果 `<v, w>=0`，则无需处理。否则，提取 `|<v, w>|²` 可表明 `CBS` 不等式成立。此外，从 `N` 的初始表示可知，等号成立当且仅当 `v` 和 `w` 线性相关。接下来是 `CBS` 不等式的一个应用。

### Example 7.14

设 `v` 和 `w` 是希尔伯特空间 `H` 中的向量。使用算子范数类型的记号，将证明 `‖v‖=sup |<v, w>|` 其中 `‖w‖=1`。如果 `v` 为零，则结果立即成立。否则，设 `b=sup |<v, w>|` 其中 `‖w‖=1`。根据 `CBS` 不等式，可知 `|<v, w>|` 小于或等于 `‖v‖`，因此 `b` 小于或等于 `‖v‖`。接下来将证明 `b` 大于或等于 `‖v‖`。设 `w=a v`，则 `|<a v, v> |=| a | ‖v‖²`。由于 `b` 是利用 `|<v, w>|` 的上确界求得的，结果是 `b` 大于或等于 `|a| ‖v‖²`。最后，由于 `w=a v`，`|a|=‖w‖/‖v‖=1/‖v‖`，且 `‖v‖` 不为零，可得 `b` 大于或等于 `‖v‖`，因此 `b=‖v‖`。

以下算子与前面提到的迹类算子相似。这里，希尔伯特-施密特有界算子 `T` 在希尔伯特空间 `H` 中定义，当 `n` 为任意整数且 `vn` 为一个 `ON` 基时。在这种情况下，`A = ∑_{n = - ∞}^{∞}‖T vn‖²` ![Equation](img/F000205si115.png) 收敛。设 `wk` 和 `vk` 为相同的 `ON` 集，注意有界 `T` 的希尔伯特-施密特范数由 `‖T‖ = [∑_{n = - ∞}^{∞}‖T vn‖²]^{1/2}` ![Equation](img/F000205si116.png) 给出。该范数在前面用于矩阵范数，也称为 Frobenius 范数。见第 5.1 节。当 `T` 仅为线性算子时，定义和可能为正无穷。包含无穷点与 `0, ∞)` 得到一个指向集。

此外，恒等式成立，`‖T‖=‖T*‖`。这可以通过首先使用 `H` 中 `ON` 向量集 `wn` 涉及内积来表示算子 `T` 的范数 `‖T v‖` 来看出。因此，这导致 `‖T v‖²` 等于所有整数上的和 `∑_n |< wn, T v >|²` ![Equation。在下文中，除非另有说明，和始终从 `-∞` 到 `∞`，`‖T‖² = ∑_n` ![Equation](img/F000205si118.png) `∑_k` ![Equation](img/F000205si119.png) `| < vk, T wn> |² = ∑_n` ![Equation](img/F000205si120.png) `∑_k` ![Equation](img/F000205si121.png) `| < T* vk, wn > |² = ∑_k ∑_n` ![Equation](img/F000205si122.png) `| <T* vk, wn > |² = ∑_k` ![Equation](img/F000205si123.png) `‖ T* vk ‖² = ‖T*‖²`。因此，可得 `‖T‖=‖T*‖`。

还要注意，从 `CBS` 不等式可以看出 `‖T v‖²` 小于或等于 `‖T‖² ‖v‖² = ‖T*‖² ‖v‖²`。

再次使用 `CBS` 不等式将表明有界希尔伯特-施密特算子也是紧算子。设 `Tn` 为有限秩算子的序列。因此，对于 `H` 中的任意 `v`，每个 `T vn` 表示为有限和：`k=1, 2, 3, …, N` 的 `<wk, Tn v> wk`，其中 `wk` 如前所述是 `H` 中的 `ON` 基。构造量 `‖(T − TN)v‖²`，注意它是从截断的无限和 `k=N+1, N+2, …` 的 `|< wk, T v>|²` 得到。然后，使用 `CBS` 不等式，`‖(T −TN) v‖²` 小于或等于级数 `‖T* wk‖² ‖v‖²` 的尾部，但对于 `k=N+1, N+2, …`，`‖T* wk‖²` 的和趋于零。

所有希尔伯特-施密特算子的集合 `S` 和 `T` 构成一个向量空间，是有界算子的子空间。此外，以下内积可用，并可通过 `CBS` 不等式证实：`<S, T>=∑_n` ![Equation](img/F000205si124.png) `<S vn, T vn>`，其中 `vn` 是 `H` 中的 `ON` 基。此外，所有希尔伯特-施密特算子的向量空间构成一个希尔伯特空间（Conway, 1990）。

## 7.7 Compact operators



## 相对紧集与紧算子

相对紧集 `S` 在复希尔伯特空间 `H` 中的概念必须给出。它是这样的，对于取值在 `S` 中的任意序列 `vn`，必须存在 `vn` 的一个子序列收敛到 `S` 中的一个值。线性算子 `T`，`T: H1 → H2`，其中 `H1` 和 `H2` 为希尔伯特空间，当 `T(B(0, 1))` 在 `H2` 中相对紧时，称其为紧算子。这里，`B(0, 1)` 是 `H1` 中以 0 为中心、半径为 1 的开球。该结果可以在更一般的设定中定义；例如，该结果对前一章中引入的巴拿赫空间成立。之前已看到 `MSA` 为巴拿赫空间、巴拿赫代数和 `C*` 代数的性质提供了全局抽象的平台。这些代数构成了量子学科中使用的有界算子的基础。接下来给出一个闭集 `S` 的简单例子，该集合在希尔伯特空间中不是相对紧的。

### 例 7.15

考虑希尔伯特空间 `H` 中的闭有界单位球 `BC`。令 `e[1]`、`e[2]`、… 为 `H` 的 `ON` 序列，因为 `‖e[i]‖=1`；这是一组位于该球边界上的点。然而，使用不同的 `ON` 向量的内积给出 `< e[i] − e[k], e[i] − e[k] > = < e[i], e[i] > + <e[k], e[k] > =2`。因此这些点相距 `2^(1/2)`，因此不存在收敛子序列。于是 `BC` 不是紧的。

在有界线性变换中，当值域为有限维时，`T` 为有限秩。对于此类运算，`T(B)` 是 `C^(n)` 中的有界子集。其闭包是闭且有界的，因此它是紧的。由此可知有限秩算子是紧算子。后续章节将提供涉及紧算子的额外结果。特别是，涉及这些算子的谱定理最容易证明。

## 参考文献

* Argerami, 2014 Argerami, 2014. 堆栈交换。
* Conway, 1990 Conway J. 978-0-387-97245-9 *泛函分析教程* Springer-Verlag 1990;.
* Gustafson, 1970 Gustafson K. *线性算子的 Toeplitz-Hausdorff 定理* American Math Society 1970;.
* Nelson, 2010 Nelson M. ISBN9781139495486 *量子计算与量子信息* Cambridge U. Press 2010;.
* Rudin, 1991 Rudin W. *泛函分析，纯粹与应用数学国际丛书*. vol. 8 second ed. McFraw-Hill 1991;.

# 第 8 章：量子算子的空间与代数

## 摘要

本章首先给出巴拿赫空间中无界算子的例子。还给出了平行四边形法则和极化恒等式以及希尔伯特空间的例子。下一节引入了交换和非交换巴拿赫代数以及众多例子。特别是，给出了涉及 Frobenious 或 Hilbert-Schmidt 范数的 `MSA` 描述。还描述了动量和位置运算的非交换性。随后是对几乎周期函数的简短介绍。第 8.4 节致力于说明希尔伯特空间 `B(H, H)` 中有界函数的 `MSA`。在这里，给出了 `B(H, H)` 所需的所有 23 个等式恒等式。下一节使用了在希尔伯特空间上求逆运算的非常重要的判据。该判据由 Halmos（1957）提出，并提供了若干例子。第 8.6 节对巴拿赫代数中算子的谱类型进行了简要描述。下一节给出了巴拿赫代数中理想的描述。随后是 Gelfand-Naimark-Segal（GNS）构造，以及循环向量的描述。下一节描述了 `C*` 代数的生成元。本章的最后一节用于介绍求希尔伯特空间中有界算子谱半径的 Gelfand 公式。

### 关键词

秩；可逆运算；连续谱；几乎周期函数；理想；Gelfand-Nairmark-Segal 构造；`C*` 生成；Gelfand 公式

## 8.1 巴拿赫空间和希尔伯特空间的秩、有界性与 Schauder 基

本节首先再次表明巴拿赫空间上的部分算子，例如量子研究中的动量运算，是无界的。在 第 7 章 中，例 7.7 中已看到微分算子在希尔伯特空间 `L²[0, 2π]` 中是无界的。现在将证明它在连续函数巴拿赫空间中也是无界的。

### 例 8.1

考虑空间：`B=C([0, 1])`，其中 `g` 的范数为 `‖g‖=max|g(t)|`，`t` 在 `[0, 1]` 中。`B` 中的一个子空间将被用于 `B` 中的部分算子。因此，令微分算子为 `T=d/dt`。微分算子在此巴拿赫空间中未定义；相反，它在连续可微函数线性子空间 `C¹([0, 1])` 中定义，`C¹([0, 1])` 是 `B` 的子集。然而，`T` 是闭算子，因为如果 `f[n]→f` 且 `f'[n]→g`，则 `Tf=g=f'`。这是在上述收敛为 `[0, 1]` 上的一致收敛且 `f` 在 `C¹` 中的假设下成立的。为此，写出 `fn=fn+∫[0]^(t) f[n]'(x) dx` 并令 `n` 趋于无穷大时取极限。还将积分与极限互换。这是因为一致连续性成立。结果为 `f(t)=f(0)+∫[0]^(t) g(x) dx`。对上式求导得到 `f'(t)=g(t)`，这表明算子 `d/dt` 是闭算子。

应指出一致收敛的假设至关重要。看看当 `f'[n]→g` 仅逐点收敛时会发生什么。考虑 `fn=t/(1+n t²)→f=0`，对所有 `t` 在 `[0, 1]` 成立，因此 `f` 在 `C¹[0, 1]` 中且 `Tf=f'=0`。另一方面，`T f[n]=f'[n]=(1 - n t²)/(1+n t²)²→g`，其中 `g(t)=0=T f(t)`，对所有 `t` 在 `(0, 1]` 成立，但 `T fn=f'n=1` 且不等于 `T f(0)`。

接下来，将证明 `T` 不是有界的。

算子 `T` 是线性的，但不是连续算子，因为它不是有界的。这可以通过令 `f(x)=x^(n)` 来看到。则导数的范数 `‖T x^(n)‖=‖(x^(n))'‖=n‖x^(n−1)‖`。取 `x` 在 `[0, 1]` 中的最大值可知 `‖T‖` 的阶为 `n`，当 `n` 趋于无穷大时。

巴拿赫或希尔伯特空间 `V` 中的 Schauder 基是向量序列：`v1, v2,…`，使得对 `V` 中的任意 `v`，存在唯一的标量 `a1, a2,…`，其依赖于 `v`，并且 `v=a0·v0+a1·v1+a2·v2+…`，使得该级数按范数收敛。

巴拿赫空间可以成为希尔伯特空间当且仅当平行四边形恒等式成立，即 `‖u+v‖²+‖u−v‖²=‖u‖²+‖v‖²`。平行四边形法则本身不足以得到内积；因此需要更多。具体而言，极化恒等式提供了额外的判据，接下来定义它。它使得可以构造一个内积，使得所得空间为内积空间。复数域的极化恒等式为 `<u, v>=1/4 (‖v+u‖²−‖v−u‖²+i·‖v+i·u‖²−i·‖v−i·u‖²)`。对于实数域，仅出现前两项，即 `<u, v>=1/4 (‖v+u‖²−‖v−u‖²)`。

接下来给出一个不是希尔伯特空间的巴拿赫空间的例子。该例子还使用了量子设定中的基本位置算子。

### 例 8.2



## 8.1

考虑空间 `B=C([0, 1])`，其中 `B` 中 `g` 的范数由 `‖g‖=max |g(x)|` 给出，`x` 在 `[0, 1]` 中，如 示例 8.1 中所用。这次，我们证明该赋范向量空间不是内积空间。因此，它也是一个巴拿赫空间的例证，该空间不能成为希尔伯特空间。所采用的主要工具是平行四边形法则。首先，设 `f` 也是 `B` 中的一个向量。平行四边形法则不成立，因为恒等式 `‖f+g‖²+‖f−g‖²=‖f‖²+‖g‖²` 不成立。取 `f=g=x`，则 `‖g‖=max |g|=‖f‖=max|f|` 对 `x` 在 `[0, 1]` 中为一，但 `‖f+g‖²=4`。

从巴拿赫空间 `B1` 到巴拿赫空间 `B2` 的算子 `T` 被称为有限秩是指 `T` 的像是一个 `B2` 的有限维子空间。`B (B1, B2)` 中的任意算子是指 `T` 是从 `B1` 到 `B2` 的线性有界算子。如果它也是有限秩的，则 `T` 是紧算子。这里，`T` 的像是位于 `B2` 中以 `0` 为中心、半径为 `‖T‖` 的开球内。更一般地，从 `B1` 到 `B2` 的所有紧算子的集合本身是 `B (B1, B2)` 的一个向量空间子空间。此外，如果 `B (B1, B2)` 中有限秩算子的序列 `T0, T1, T2,…` 收敛于 `T`，则 `T` 是紧算子（Conway, 1990）。

特别地，当 `B (B1, B2)` 中的 `T` 为秩一时，则存在 `B1` 中范数为一的向量 `v`，使得存在唯一的泛函 `f (w)`，其中对所有 `w` 在 `B1` 中有 `T w=f (w) v`。`T` 的线性性表明 `f` 是线性的，并且 `|f (w) |=‖T w ‖` 小于或等于 `‖T‖ ‖w‖`，表明 `f` 有界。如果这也是一个希尔伯特空间 `H`，则由 RRT，即由里斯表示定理，该有界线性泛函也是一个内积；因此，对某个 `u` 在 `H` 中有 `f (w)=<u, w>`，从而 `T w=<u, w> v`。一般地，对于秩为 `n` 的有限算子 `T`，可使用 ON 集 `{v1, v2,…, vn}`，以及相应的泛函得到 `$T w = \\sum\_{k = 1}^{n}{< {uk},w > {vk}}$`![方程](img/F000059si3.png)。下面有一个非常有趣的例子。它表明在巴拿赫空间中存在有限秩的无界算子（Lacey, 1973）。

### 示例 8.3

设 `B1` 为 `C` 上的无限维巴拿赫空间。将给出一个无界算子 `T` 的例子，该算子具有有限秩。设 `M` 是 `B1` 的 Hamel 基。该基通过选择公理的应用总是存在，并且是不可数的。设 `L` 是 `M` 的一个可数无限子集 `{e[n], n=1, 2,…}`。设 `T: L→C`，其中 `T(e[n])=n·e[n]`，并且对所有 `v` 在 `M−L` 中有 `T(v)=0`。`(M−vL)` 的维数至少等于连续统。`T` 的值域维数为 1，因此是有限秩的但不是有界算子。

## 8.2 可交换与不可交换巴拿赫代数

尽管所有巴拿赫代数具有相同的整体 MSA 结构，但在这些代数的载体集合上出现了很大的差异。其中最大的区别因素之一是它们是否可交换。这由众多例子说明。

### 示例 8.4

设 `VECTOR` 的载体集合为所有 `n` 阶 `n` 复矩阵，`A`。它是复数域上的一个不可交换巴拿赫代数。设 `NORM` 利用该载体集合以及由复数组成的相应载体集合，以及所有通常的复矩阵运算。这里，设 `NORM` 的运算为 `A` 的所有绝对平方项之和的平方根。这就是 Frobenius 或 Hilbert-Schmidt 范数。另见 第 7.6 节。Frobenius 范数满足范数的四个约束方程。为此，首先替换：

* `MATRIX` 为 `A`, `B`
* `SCALAR` 为 `a`
* `C-MULT` 为 `x`
* `V-ONE` 为：`I`
* `BINE` 为 `·`
* `NORM` 为 `‖‖`

1. 1) 正定性：`‖A ‖> 0`，且 `‖A‖=0` 当且仅当 `A=0`。
2. 2) 齐次性：`‖a A‖=|a|‖A‖`
3. 3) 三角不等式：`‖A+B ‖` 小于或等于 `‖A‖+‖B‖`
4. 4) 三角乘积不等式：`‖A·B ‖` 小于或等于 `‖A ‖‖B‖`。

当 (4) 成立时，范数被称为次乘性的。

为看出 (4) 成立，使用 Frobenius 范数，设 `D=A·B` 在 `C^(n)` 中。则 `D` 中的典型元素为 `$d\_{ij} = \\sum\_{k = 1}^{n}a\_{ik} \\cdot b\_{kj}$`![方程](img/F000059si4.png)。另外，`${|d\_{ij}|}^{2} = {|{\\sum\_{k = 1}^{n}a\_{ik} \\cdot b\_{kj}}|}^{2}$`![方程](img/F000059si5.png) 由 CBS 不等式；结果是 `|d[i j]|`![方程](img/F000059si6.png)|² 小于或等于 `$\\left\\lbrack {\\left( {\\sum\_{k = 1}^{n}{|a\_{ik}|}^{2}} \\right) \\cdot \\left( {\\sum\_{k = 1}^{n}{|b\_{kj}|}^{2}} \\right)} \\right\\rbrack$`![方程](img/F000059si7.png)。因此，`‖D‖²=‖A·B‖²` 小于或等于 `$\\sum\_{i = 1}^{n}{\\sum\_{j = 1}^{n}{\\sum\_{m = 1}^{n}{\\sum\_{k = 1}^{n}{|a\_{im}|}^{2} \\cdot}}{|b\_{kj}|}^{2}) = \\left( {\\sum\_{i = 1}^{n}{\\sum\_{m = 1}^{n}{|a\_{im}|}^{2}}} \\right)} \\cdot \\left( {\\sum\_{j = 1}^{n}{\\sum\_{k = 1}^{n}{|b\_{kj}|}^{2}}} \\right) = \\left\\| A \\right\\|^{2} \\cdot \\left\\| B \\right\\|^{2}$`![方程](img/F000059si8.png)。

### 示例 8.5

一个重要结果是，对于 `B(H)` 中的 `T` 以及 `H` 中的单位向量 `v` 和 `u`，则有 `‖T‖=sup |<Tu, v>|`。该结果源于前一个例子，即将使用示例 7.14。在那里，证明了 `‖w‖=sup |<w, v>|` 其中 `‖v‖=1`。

因此通过注意到 `Tu` 是 `H` 中的一个向量来使用所引用的例子。相应地，设 `w=Tu`；则从前述例子可得，`‖Tu‖=sup|<Tu, v>|`，因为 `‖v‖=1`。使用算子范数 `‖T‖=sup|Tu|`，当 `‖u‖=1` 时。因此，通过回溯代入，`‖T‖=sup|sup|<Tu, v>||=sup|<Tu, v>|`，如所愿。

### 示例 8.6

一个可交换巴拿赫代数的简单例子涉及复平面上非空子集 `S` 中所有有界函数的载体集合。它记为 `A`。对于 `A` 中的任意函数 `f` 和 `g`，逐点加法运算 `(f+g) (z)=f (z)+g (z)` 是封闭的。标量乘法也是如此，其中标量 `a` 在 `C` 中，`a (f (z))=af (z)`。此外，所有等式恒等式对向量空间结构成立。此外，它是一个含幺结合代数，即 `f·g` 在 `A` 中。这是因为 `(f g) (z)=f (z) g(z)`，`V-ONE` 为 `1`，且 `|1|=1`。最后，它是使用范数 `‖f‖=sup|f (z)|` 的巴拿赫代数，`z` 在 `S` 中，并注意到三角乘积不等式平凡成立。事实上，它是等式，`|f·g|=|f|·|g|`。此外如同在 `C*` 代数中，`|f·g*|=|f|·|g*|`。

### 示例 8.7

位置 `P` 与动量 `M` 算子不可交换。以下仅是对结果的正式表述。参见后面提到的参考文献。`P` 与 `M` 的不可交换性可通过交换子运算 `[P, M|=P M −M P]` 看出，这是李代数的基础。可交换意味着该李括号为零。然而，它等于 `i` 乘以普朗克常数 `h` 再乘以恒等式 `I` 的运算。该结果通过取任意连续可微的 `f`，以及绝对平方可积函数希尔伯特空间 `L2` 中的 `x f` 得到。然后使用动量算子 `P` 和乘法算子 `M`。这里，`P` 使用 `Pf=−ihd(f(x))/dx` 定义，而乘法算子为 `Mf=xf(x)`。因此根据求导乘积法则，`PMf(x)=−ihd(x f(x))/dx=−ih(f(x))+x d(f(x))/dx=−hif+MPf(x)`，因此恒等式 `[P, M]= −ihI` 或 `[M, P]=ihI` 成立。该恒等式通常称为正则对易关系 (CCRs)（McCoy, 1929）。



这个 `CCR` 恒等式可用于证明 `P` 或 `M` 中的一个是无界算子。证明无界性时采用了标准的归纳技术。从 `[M^(n), P]=M^(n) P−P M^(n)=ih n M^(n−1)` 开始。当 `n=1` 时成立，`[M, P]=ihI` 成立，并且如果假设对 `n` 成立，则通过归纳必须证明对 `n+1` 成立。也就是说，必须证明以下表达式成立：`M^(n+1)P−P M^(n+1)=ih(n+1)M^(n)`。左边可以写成如下形式：`M^(n) (M P−P M)+(M^(n) P−P M^(n)) M=M^(n) ih+ih n M^(n−1) M=the right hand side, ih(n+1) M^(n)`。现在对右边进行估计：对于 `[M^(n), P]` 给出估计：`n ‖(M^(n−1)) ‖` 小于等于 `‖M^(n) ‖‖P‖+‖P ‖‖M^(n)‖`，因此提出 `‖M^(n−1)‖` 后得到 `n` 小于等于 `2 ‖M ‖‖P‖`。因此 `M` 或 `P` 中至少有一个不是有界的。

接下来给出一个实 Banach 代数的有趣例子，涉及连续实值函数的一个重要子集。它们是几乎周期函数，是周期函数的推广。其中最著名的是 Bohr 型一致几乎周期连续函数 `f`。这意味着对于每一个大于零的 `a`，存在 `R` 的一个相对稠密子集 `Da`，使得对所有 `t` 在 `Da` 中有 `sup|f(x+t)−f(x)|<a`。值 `t` 称为 `a` 平移数。直观上，这意味着即使可能不存在值 `t` 使得对所有实值 `x` 有 `f(x+t)=f(x)`，也可能存在使该关系近似成立的数。该概念最好由以下例子说明（Gelbaum 和 Olmsted, 2003）。

### Example 8.8
对于 `f: R→R`，考虑 `f (x)=sin (2πx)+sin (2^(1/2) 2π x)`；该函数不是周期的。然而，对于任意 `ε>0`，可以证明存在无穷多个整数值 `t`，使得 `2^(1/2)·t` 与另一个整数的差小于等于 `ε/(2π)`。此外，这样的两个连续整数之间的差是有界的，由 `δ` 给出。使用这样一个整数值 `t`，则 `f (x+t)=sin (2πx+2π t)+sin (2^(1/2) (2π x+2π t))=sin (2πx)+sin (2^(1/2) 2π x+δ ε)=f (x)+δ′ ε`，其中 `δ′` 是一个有界量。基本思想是 `f` 接近周期性，但它不是周期的。

几乎周期函数表现良好。它们是一致有界且一致连续的。此外，如果 `f[n]` 是几乎周期函数序列且一致收敛于 `f`，则 `f` 也是几乎周期的。所有几乎周期函数的空间是所有有界连续函数空间的闭子空间。在上确界范数下，它是一个 Banach 空间。利用函数的逐点乘法可知它是一个 Banach 代数。几乎周期函数空间的一个实例是所有三角多项式。它们是关于整数 `k` 的有限和，涉及正弦波的线性组合，(`b[k] cos(d[k] x)+c[k] sin(d[k] x)`)，其中 `b[k]`、`c[k]` 和 `d[k]` 在 `R` 中。

几乎周期函数的空间利用内积形成一个预希尔伯特空间：`<f, g>=limit as T goes to infinity of [1/2 T ∫[−T]^(T) f(x)*g(x) dx]`。

该空间完备化为类 `B²`，通常称为 Besicovitch 几乎周期函数类（Besicovitch, 1954）。

## 8.3 Banach 代数中的子群
Banach 代数 `A` 的一个重要子集是来自 `A` 的可逆元群 `G`。在这里，从 MSA 的角度来看，有一个单一的排序，`SUBG`。集中于 `A` 的代数性质，有三个签名集合，每个包含一个操作名。因此元数序列为 `(1, 1, 1)`。每个签名集合中的操作名与超集中的操作名一致，即 Banach 代数。此外，还有新的操作符名 `INV`。它以一种暗示性的方式给出。本例中没有偏操作符。具有对应操作名的元数如下：

`Arity`2:`BINE`:`SUBG x SUBG → SUBG`

![方程](img/F000059si10.png)

`Arity`1:`INV`:`SUBG → SUBG`

![方程](img/F000059si11.png)

`Arity`0 : `V-ONE`

![方程](img/F000059si12.png)

必须满足三个等式恒等式，因为这与向量空间内的加法群结构类似的代数。在再次给出这些恒等式之前，分配了几个符号来表示指定的排序。此外，还为操作名提供了暗示性符号。它们如下给出：

* `SUBG` 为 `u`, `v`, `w`
* `BINE` 为 `·`
* `INV` 为 `/`
* `V-ONE` 为 `I`

等式恒等式如下：

1. 1) 乘法结合律：`(u·(v·w))=((u·v)·w)`。
2. 2) 单位元律：`I·v=v·I=v`，`I` 是 `V-ONE`。
3. 3) 逆元律：使用 `1/v`，则 `v·1/v=1/v·v=I`。

在 图 8.1 中，Banach 代数子群中操作的名称被说明。Banach 代数 `A` 中可逆元群 `G` 的一个重要拓扑性质是 `G` 在 `A` 内是一个开集。这意味着 `G` 内每一点都是内点。存在以该点为中心、半径为 `ε` 的球或球体，使得该球完全位于 `G` 内。

![图 8.1 Banach 代数子群的多元图。](img/F000059f08-01-9780443136979.jpg)

图 8.1 Banach 代数子群的多元图。

接下来的几个例子说明了 Banach 代数 `A` 内的（子）群 `G` 与 `A` 本身之间的相互作用。下一个例子在谱分析中特别重要。它涉及恒等函数 `I`，以及群 `G` 从 Banach 代数 `A` 继承的许多性质。例如，来自 `A` 的范数和收敛性质贯穿整个子群 `G`。

### Example 8.9
设 `v` 在 Banach 代数中且 `A` 满足 `‖v ‖` 小于一，并设 `r=I – v`。则 `r` 有逆元。该结果源于幂级数论证。所涉及的级数通常称为 Neumann 级数。设 `w[n]=v+v²+…+v^(n)`；则部分和序列是 Cauchy 序列，因此收敛于 `A` 中的某个向量。注意 `(I −v) w[n]=w[n] (I – v)=(I – v^(n+1))`，并且当 `n` 趋于无穷时该量收敛于 `I`。同样，当 `n` 趋于无穷时，部分和序列收敛于设为 `w`。此外，`(I – v) w=w (I – v)=I`，即 `r w=w r=I`，由乘法的连续性可得。还有 `$w = I/r = 1/\\left( {1 - v} \\right)\\sum\_{n = 0}^{\\infty}v^{n}$`![方程](img/F000059si13.png) 将是存在逆元时的标准记号。

向量在 `A` 内具有逆元的标准的一个实例在以下例子中说明。

### Example 8.10
设 `v` 在 `G` 中且 `w` 在 Banach 代数 `A` 中。假设 `‖v – w‖` 小于 `1/‖v ^(−1)‖`；则 `w` 也在 `G` 中，即它是可逆的。为此，考虑 `A` 中的向量 `z`，其中 `z=I – v^(−1) w`。则 `‖z‖=‖I – v^(−1) w‖=‖v^(−1) (v−w)‖` 小于等于 `‖v^(−1)‖‖(v−w)‖`，而这小于 `‖v^(−1)‖/‖v^(−1)‖=1`。因为对于非负整数，`‖z^(n) ‖` 小于等于 `‖z ‖^(n)`，将证明求和 `∑_{n = 0}^{∞}z^{n}` 收敛于设为 `y` 的 `A` 中的元素。即部分和序列 `∑_{n = 0}^{N}{z^{n} = (I - z^{N + 1})/(I - z) = (I - (I - v^{- 1}w)^{N + 1})/(v^{- 1}w)}` 收敛于 `y=1/(1−z)`。因此，`y=1/(v^(−1) w)`。



为验证收敛性，将说明绝对收敛。注意 ‖I – y ‖ 小于或等于 $\\sum\_{n = 1}^{\\infty}{{|{|z|}|}^{n} = \\sum\_{n = 1}^{\\infty}{|{|{v^{- 1}\\left( {v - w} \\right)}|}|}^{n}}$![方程](img/F000059si17.png)，其小于或等于 $\\sum\_{n = 1}^{\\infty}{\\left( {\\left\\| v^{- 1} \\right\\|\\left\\| {v - w} \\right\\|} \\right)^{n} = 1/\\left\\lbrack {1 - \\left( {\\left\\| v^{- 1} \\right\\|\\left\\| {v - w} \\right\\|} \\right)} \\right\\rbrack} - I = \\left\\| v^{- 1} \\right\\|\\left\\| {v - w} \\right\\|)/\\left\\lbrack {1 - \\left\\| v^{- 1} \\right\\|\\left\\| {v - w} \\right\\|)} \\right\\rbrack$![方程](img/F000059si18.png)。

相乘，`y (I−z)=(1−z) y`，然后对 `z` 代入，`z=I – v^(−1)w`，得到 `y v^(−1)w=v^(−1) w y=I`。因此，`y (I−z)=(1−z) y=I`；这表明 `y` 和 `(1−z)` 可逆。此外，可推出 `v^(−1) w` 可逆，且 `v^(−1) w y=y v^(−1) w=I`。于是，`w=v y^(−1)` 且 `w^(−1)=y v^(−1)`，所以 `w` 在 `G` 中。

Banach 代数 `A` 的一个最终事实是，如果 `A` 中每个非零元素都可逆，则 `A` 与 `C` 等距同构。唯一既是复 Banach 代数又是除法代数的复 Banach 代数是复数域。这是 Gelfand-Mazur 定理（Bonsall 和 Duncan, 1973）。

## 8.4 Hilbert 空间上的有界算子

考虑将 Hilbert 空间 `H` 映射到自身的全部复值有界算子的集合 `B(H)`。所有这些算子的空间 `B(H)=B (H, H)` 是一个 `C*` 代数。它逐步说明如下：
1. A) 它是一个向量空间；
2. B) 它是一个含幺结合代数；
3. C) 它是一个 Banach 空间；
4. D) `B (H, H)` 是一个 Banach 代数；
5. E) 它是一个 Banach* 代数；
6. F) 最后，它是一个 `C*` 代数。

这里，`T` 具有算子范数：`‖T‖=sup {‖T w‖/‖w ‖|w in H, w nonzero}`。已看到 `‖T‖= sup[*∥*w*∥* = 1]`![方程](img/F000059si19.png) `‖T w ‖` 且对合是通常的伴随，`<T*v, w>=<v, T w>`。这是 `H` 上全部的 `B(H)` 态射的集合。

图 3.5 在第 3 章中说明了 `C*` 代数中的全部八个运算名称。这些实际上是 `B(H, H)` 的闭包运算：`V-ADD`，`+`；`S-MULT`，`·`；`V-MINUS`，`-`；`BINE`，`·`；`NORM`，`‖‖`；`ADJ`，`*`；`V-ZERO`，`0`；`V-ONE`，`1`。回顾一下，此代数中的 `BINE` 是函数复合。对于 `B(H, H)` 中的 `S` 和 `T`，`BINE(T, S)=T·S=T(S (.)),` 因此对于 `H` 中的 `v`，`BINE(T, S)(v)=T(S(v))`。先前提到的所有运算都是连续的。`NORM` 的连续性在 第 3.6 节 中证明，`BINE` 的连续性在 第 3.7 节 中证明。参考图中运算成立，即闭包要求得到满足，是 Lipschitz 条件的结果：`‖T (v) ‖` 小于或等于 `M ‖v‖`。回顾 `<T (v), T (v)>=‖T (v) ‖²`。所有此类 `M` 值的下确界称为 `T` 的算子范数，记为 `‖T‖`。例如，`V-ADD` 和 `S-MULT` 运算是封闭的，这是三角不等式的结果。也就是说，对于 `C` 中的 `a` 和 `H` 中的 `v` 和 `w`，注意 `‖a v+w ‖` 小于或等于`|a|‖v‖+‖w‖`。因此，`V-ADD[S-MULT(a; v), w]` 在 `B(H, H)` 中。

`B(H, H)` 满足以下 23 个等式恒等式。该列表给出了代数结构 (A) 到 (F) 所需的定律。这些是必须成立的等式恒等式，并在下面详细说明。在此列表中，设 `R`、`S` 和 `T` 为 `B(H, H)` 中的算子，且 `a` 和 `b` 为 `C` 中的标量。在列出所有等式约束之后，提供了一些此前未证明的证明。
1. A) `B (H, H)` 因为它是一个向量空间而成立的等式恒等式如下：
1. 1) 向量加法的结合性：`(S+(T+R))=((S+T)+R)`。
2. 2) 零向量律：`0+T=T+0=T`。
3. 3) 负向量律：`T−T=−T+T=0`。
4. 4) 加法的交换向量律：`S+T=T+S`。
5. 5) 单位律：`1·T=T·1=T`。
6. 6) 分配律：`a·(S+T)=a·S+a·T`。
7. 7) 分配律：`(a+b)·T=a·T+b·T`。
8. 8) 结合律：`(a·b)·T=a·(b·T)`。
2. B) `B (H, H)` 因为它是结合含幺代数而成立的等式恒等式如下：
1. 1) 分配律：`(S+T)·R=S·R+T·R`。
2. 2) 分配律：`R·(S+T)=R·S+R·T`。
3. 3) 乘法齐次性：`ab (S·T)=(a S)·(b T)`。
4. 4) 结合律：`((R·S)·T)=(R·(S·T))`。
5. 5) V-ONE 律：`I·T=T·I=T`。
3. C) `B (H, H)` 因为它是一个 Banach 空间而满足 `NORM` 的以下条件：
1. 1) 正定性：`‖T ‖> 0`，且 `‖T‖=0` 当且仅当 `T=0`。
2. 2) 齐次性：`‖a T‖=|a|‖u‖`。
3. 3) 三角不等式：`‖S+T ‖` 小于或等于 `‖S‖+‖T‖`。
4. D) 它因为是 Banach 代数而满足的附加条件如下：
1. 4) 三角乘积不等式：`‖S·T ‖` 小于或等于 `‖S ‖‖T‖`。
5. E) 此外 `B (H, H)` 是一个 Banach* 代数，因为满足以下定律：
1. 1) 对合性：`(T*) *=T`。
2. 2) 可加性：`(S+T)*=S*+T*`。
3. 3) 共轭线性：`(a T)*= $\\overline{a}$`![方程](img/F000059si20.png) `T*`。这里，`$\\overline{a}$`![方程](img/F000059si21.png) 表示 `a` 的共轭。
4. 4) 转置：`(S·T)*=T*·S*`。
5. 5) 等距性：`‖T*‖=‖T‖`。
6. F) `B (H, H)` 是 `C*` 代数，因为它是一个 Banach* 代数且还满足：
1. 6) `C*` 恒等式：`‖T·T*‖=‖T‖²`。

部分等式恒等式的证明：
* C 3) 三角不等式在 第 7.3 节 中展示。
* D 4) 三角乘积不等式 `‖S·T ‖` 小于或等于 `‖S ‖‖T ‖` 随后是函数复合 `‖S (T) (v)‖`。由于 `‖T (v) ‖` 小于或等于 `‖T ‖‖v‖`，对所有 `H` 中的 `v` 成立。使用 `w=T (v)`，则 `‖S (w) ‖` 小于或等于 `‖S ‖‖w‖`，这对所有 `H` 中的 `w` 成立。
* E 5) 要看到 Banach* 代数等距恒等式成立，使用 第 8.2 节 中 例 8.5 的结果。从该例可知，算子范数可写为`‖T‖=sup|<Tv, w>|`，其中 `v` 和 `w` 在 `H` 中均为单位范数。因此，`‖T*‖=sup|<T*v, w>|=sup|<v, Tw>|=sup|<Tw, v>*|=sup|<Tw, v>|=‖T‖`。
* F 6) 要证明 `C*` 恒等式，再次使用先前例子的结果。开始时 `‖T* T ‖` 小于或等于 `‖T* ‖‖T‖=‖T‖²`。接下来不等式将被反转。如等式 E 5) 中。对于 `H` 中的 `v` 和 `w`，每个均为单位范数 `‖T* T‖=sup|<T*T w, v>|=sup|<T w, Tv>|` 大于或等于 `sup|<T v, Tv>|=‖T‖²`。因此，`‖T* T‖=‖T‖²`。

## 8.5 Hilbert 空间上的可逆算子代数准则

考虑 `A` 中的有界算子 `T`，使得 `T: H→H`，即 `T` 在 `B (H, H)` 中。逆的概念在算子代数 `A` 中极其重要，因为 `T` 的谱取决于逆是否存在与否。特别地，该谱记为 `spT`，定义为所有复数 `c` 的集合，使得 `(c·I – T)` 不可逆；这里 `I` 是 `A` 中的单位元。明确地说，`A` 中的算子 `S` 可逆当且仅当其像或值域 `{Sv, such that v in H}` 在 `H` 中稠密，且存在常数 `a> 0`，使得对所有 `H` 中的向量 `v`，`‖Sv‖` 大于或等于 `a ‖v‖`（Halmos, 1957）。最后的准则被称为：`T` 有下界（Rubin，）。

验证当 `S` 可逆时这两个准则成立的说明如下，因为在这种情况下它是单射且满射。因此，注意 `S` 的像是整个 `H`，因此是稠密的。接下来，使用 `a=‖S^(−1)‖^(−1)`，则对所有 `H` 中的 `v`，`‖v‖=‖S^(−1)Sv‖` 小于或等于 `‖S^(−1)‖ ‖Sv‖`。因此 `‖Sv‖` 大于或等于 `‖v‖/‖S^(−1)‖=a·‖v‖`。



## 可逆性的证明
反过来，为了在两个性质成立的条件下证明 `S` 可逆，必须证明以下所有条件均成立。首先要证明 `S` 是满射。接下来，必须证明 `S` 是单射。随后要证明 `S^(-1)` 是线性的。最后，必须证明 `S^(-1)` 有界。首先将证明 `S` 的值域等于陪域 `H`，从而 `S` 是满射。由于 `S` 是稠密的，要证明其满射只需证明它是闭的。设 `w[n]` 是 `S` 值域中的一个柯西序列。设 `v[n]` 在 `S` 的定义域中，使得 `S v[n] = w[n]`。由此可知，由于 `‖w[n]−w[m]‖ = ‖S v[n]−S v[m]‖` 大于或等于 `a ‖v[n]−v[m]‖`，因此 `v[n]` 也是 `H` 中的柯西序列。于是，`v[n]` 在 `H` 中收敛到 `v`。由于范数是连续的，可得 `w[n] → S v`，从而值域是闭的。要证明 `S` 是 1–1，设 `S v[1] = S v[2]`，由于 `‖S v[1] – S v[2]‖ = 0` 且该量大于或等于 `a ‖v[1] – v[2]‖`。因此可得 `v[1] = v[2]`；相应地，`S` 是 1–1，从而 `S` 有逆。`S^(-1)` 的线性性可由 `S^(-1)(b[1] w[1]+w[2]) = S^(-1)(b S v[1]+S v[2]) = S^(-1)[S (b v[1]+v[2])] = S^(-1) S (b v[1]+v[2]) = I (b v[1]+v[2]) = b v[1]+v[2] = b S^(-1) w[1]+S^(-1) w[2]` 看出。最后，将证明 `S^(-1)` 是一个有界算子。利用 `‖S v‖ = ‖w‖` 大于或等于 `a ‖v‖ = a ‖S^(-1) w‖`，从而 `‖S^(-1) w‖` 小于或等于 `1/a ‖w‖`。

### 例 8.11
先前为希尔伯特空间 `H` 上的算子 `T` 给出的可逆的充要条件将被举例说明。如果 `S` 和 `T` 可逆，则 `S·T` 可逆，其中乘积实际上是函数复合。对于 `H` 中的 `v`，`(S·T)(v) = S(T(v))`。将证明 `S·T` 有下界且 `S·T` 的值域在 `H` 中稠密。首先注意 `T` 有下界意味着 `‖T v‖` 大于或等于 `a ‖v‖`。于是，设 `T(v) = w` 在 `H` 中，则由于 `S` 有下界，`‖S(T(v))‖ = ‖S(w)‖` 大于或等于 `b ‖w‖ = b ‖T v‖`，其大于或等于 `a b ‖v‖`。因此，`S·T` 有下界。接下来，证明 `S·T` 具有稠密值域。这源于基本定义，`S` 具有稠密值域意味着 `H` 中每个点 `h` 也在 `S` 的值域 ` {S(v) | v in H}` 中，或是该值域中点的极限点。因此存在不同情形。例如，`h` 在 `S` 的值域中；则由于 `T` 也有稠密值域，可得 `S·T` 具有稠密值域。另一方面，设 `h` 是 `S` 值域的极限点。这意味着 `h` 的每个邻域都包含来自 `S` 值域的点 `w[n]`。然而，这些点 `w[n]` 都位于 `H` 中。由于 `T` 也有稠密值域，每个点 `w[n]` 都在其值域中或本身是极限点。这意味着 `h` 也在 `S·T = {S(T(v)) | v in H}` 的值域中，或是该值域的极限点。因此，`S·T` 可逆。而且，`(S·T)^(-1) = T^(-1)·S^(-1)` 因为 `(S·T)·(S·T)^(-1) = S·T·T^(-1)·S^(-1) = S·I·S^(-1) = S·S^(-1) = I`。

### 例 8.12
所有可逆算子 `T: H → H` 的集合，其中 `H` 是希尔伯特空间，形成一个非交换乘法群。这里，乘法二元运算是函数复合，所以 `(S·T)(v) = S(T(v))`。`S·T` 可逆的证明在 例 8.11 中给出。一元运算是求逆运算，对于 `T` 它是 `T^(-1)`。零元是单位元 `I`。以下等式恒等式成立：
1. `1) Associative Law: R·(S·T) = (R·S)·T.`
2. `2) One Law: I·S = S·I = S.`
3. `3) Inverse Law: S^(-1)·S = S·S^(-1) = I.`
结合律成立。设 `v` 是 `H` 中的向量，则 `T(v) = w` 也在 `H` 中；最后 `S(w) = u` 再次在 `H` 中，以及 `R(u) = z` 在 `H` 中。`(S·T)(v) = S(T(v)) = S(w) = u`，于是 `(R·(S·T))(v) = R(u) = z`。反过来，`T(v) = w`，`(R·S)(w) = R(S(w)) = R(u) = z = ((R·S)·T)(v)`。

### 例 8.13
(Halmos, 1957)
假设 `‖T – I‖ < 1`，将通过说明它有下界且 `T` 的值域在 `H` 中稠密来证明 `T` 可逆。令 `a = 1 − ‖I – T‖`，这表明 `a > 0`。如果 `v` 在 `H` 中，则 `‖T v‖ = ‖v – (v – T v)‖` 大于或等于 `‖v‖ − ‖v – T v‖`，其大于或等于 `(1 − ‖I − T‖) ‖v‖ = a ‖v‖`。于是 `T` 被 `a` 下界。另请注意 `1 − a = ‖I – T‖`。
接下来，利用可逆性的第二个充分条件，必须证明 `T` 的像，记为 `M`，在 `H` 中稠密。考虑 `H` 中任意向量 `w`。将证明如果 `δ = inf { ‖w − v‖, where v is in M }`，则 `δ = 0`。用反证法，假设 `δ > 0`。在这种情况下，存在 `M` 中的向量 `z` 使得 `(1 − a) ‖z − v‖ < δ`。`z` 和 `T(w − z)`，以及 `z + T(w – z)` 都是 `M` 的元素。因此，`δ` 小于或等于 `‖w − [(z + T(w − z)))]‖`，因为 `δ` 是下确界。然而，`‖w − [(z + T(w − z))]‖ = ‖(w − z) − T(w − z)‖` 小于或等于 `‖I − T‖ ‖w − z‖ = (1 − a) ‖w − z‖ < δ`。导致矛盾。

### 例 8.14
假设 `‖S‖ < 1`；将利用 例 8.13 的结果证明 `S − I` 可逆。确实，在提及的例子中，用 `I − S` 替换 `T`。在该例子中对 `T` 代入可得 `‖(I − S) − I‖ < 1`，即 `‖S‖ < 1`；这意味着 `I − S` 可逆。

### 例 8.15
对于有界算子 `T`，如果它有下界，则其值域是闭的。该结果通过令 `w[n] = T(v[n])`，`n = 1, 2, …` 得到。令 `w[n]` 收敛到 `w` 在像中产生一个柯西序列 CS。如果证明 `w` 也在 `T` 的像中，这意味着像为闭。利用有下界准则以及 CS 准则，`‖T(v[n]) − T(v[m])‖` 大于或等于 `a ‖v[n] − v[m]‖`，表明 `v[n]` 也是一个 CS。该序列收敛到 `v`。利用 `T` 的连续性可得 `T(v) = w`，于是 `w` 在 `T` 的像中。

## 8.6 Banach 代数中的谱
对于 `B(H, H)` 中的算子 `T`，`T` 的谱是紧的，即 `spT` 是紧的。首先将证明 `spT` 是闭的，然后将证明它是 有界的。如前所述，在 Banach 代数 `A` 中，逆的概念极其重要。这是因为元素 `T` 在 `A` 中的谱取决于逆是否存在与否。特别地，该谱记为 `spT` 并定义为所有复数 `c` 的集合，使得 `(c I – T)` 不可逆；这里 `I` 是 `A` 中的单位元。将证明对于 `A` 的每个元素，谱永远不是空集，并且实际上是 `C` 中的一个紧集。由于这是复数域 `C`，这意味着 `spT` 总是闭且有界。证明将利用谱的补集 `C − spT`。
`spT` 在 `C` 中的补集称为预解集。预解集 `RsT` 定义为所有复数 `c` 的集合，使得 `(c I – T)` 可逆。因此，量 `(c I − T)^(-1)` 通常写为如下形式：`1/(c I − T)`。通过证明 `RsT` 是开的证明 `spT` 是闭的。选取 `RsT` 中的点 `z`，于是 `(T − z I)` 可逆。对于 `C` 中的 `λ`，注意 `‖I − (T − z)^(-1)(T − λ)‖ = ‖(T − z)^(-1)[(T − z) − (T − λ)]‖`，其小于或等于 `‖(T − z)^(-1)‖ |λ − z|`。量 `‖(T − z)^(-1)‖` 有界；因此使 `|λ − z|` 很小可确保 `‖I − (T − z)^(-1)(T − λ)‖` 可小于一。在这种情况下，可见 `(T − z)^(-1)(T − λ)` 可逆，见 例 8.13。于是，对于 `|λ − z|` 很小，这意味着 `(T − λ)` 也可逆。这意味着 `RsT` 是开的，因为对于 `RsT` 中 `z` 附近任意小半径内的所有点 `λ`，`(T − λ)` 可逆。因此，`T` 的谱 `spT` 是闭的。为了说明它是 有界的，将证明对于 `spT` 中的 `λ`，`|λ|` 小于或等于 `‖T‖`。由于 `T` 有界，可得 `spT` 是紧的。现在用反证法，如果 `|λ| > ‖T‖`，则 `‖T/λ‖ < 1`，这意味着 `(I − T/λ) = (λ − T)/λ` 可逆，这是一个矛盾。



谱和预解集由简单示例说明，并在后续章节中更深入地研究。

### 例 8.16

考虑 `T`=`I`，`A` 中的恒等元。 那么 `(c I−I)` 不可逆的唯一情况是 `c`=1，即单点 1。 这实际上是复平面中的点 (1, 0)。 所以 `spI`={1}，它是在 `C` 中的闭集。 该点称为点谱，将在随后描述。 此外，在这种情况下，预解集是 `RsT`，它是除去单点 1 的整个复平面。

### 例 8.17

考虑 Banach 代数 `A`，其载体集由实区间 \[0, 1\] 上所有复值连续函数 `f` 组成。 现在，`c I−f` 不可逆当量 `c−f (z)`=0，对所有 `z` 在 \[0,1\] 中。 因此，谱是 `spf`=`f` (\[0, 1\])；它是 `f` 的值域。 这称为连续谱；它由一个连续区间组成。 相应的预解集 `Rsf`= 去掉 `f` (\[0, 1\]) 的整个复平面。 例如，如果 `f (z)`=`e^(izπ)`，其中 `z` 在 \[0, 1\] 中，则 `Rsf`= 去掉以原点为中心半径为一的上半圆以及端点的整个复平面：即 (1, 0)、(−1, 0) 也被去掉。 参见 图 8.2 以了解该连续谱的说明。

![图 8.2 连续谱。](img/F000059f08-02-9780443136979.jpg)

图 8.2 连续谱。

### 例 8.18

这是一个连续谱的额外示例。 它还将说明近似特征值的概念，该概念将在后面严格描述。 此外，它涉及位置运算。 确实，在 `CL² \[0, 1\]` 中，复值绝对平方可积函数的希尔伯特空间，`M (f) (x)`=`x f (x)`。 没有点谱；然而，连续谱是闭区间 \[0, 1\]。

这将首先对 (0, 1) 中的点 `p` 显示，通过考虑以点 `p` 为中心宽度为 2`d` 且高度为 1/(2`d`) 的平方根的矩形脉冲 `h`。 在这种情况下，`h`=1/(2`d`)^(1/2)`χ`[`p−d,p+d`]。 所以高度的平方产生面积为一的矩形。 现在考虑 `‖(M−p)(h)‖²`。 然后，对于 `d` 的小值，使得矩形脉冲完全位于 (0, 1) 中，这成为积分 ∫[`p` − `d`]^(`p` + `d`)((*x*−*p*)²)/(2`d`)`d``x`。 积分的结果是 `‖(M−p) (h)‖²`=(`d²`)/3。 当 `d→0` 时，将在后续章节中看到 `p` 是近似特征值的示例。 该结果对开区间 (0, 1) 中的每一点 `p` 都成立。

在零和一处，通过修改 `h` 也能得到相同的结论。 也就是说，零和一也在 `M` 的谱中。 例如，在零处，使用 `p`=0，以及宽度为 `d` 且高度为 `d` 的平方根倒数的矩形 `h`，`d>` 0。 在这种情况下，`h`=1/(`d`)^(1/2)`χ`[\[0, 0 + `d`\]]。 然后`‖(M−0)(h)‖²`=`d²`，如前所述令 `d→0` 显示 0 也是近似特征值。 因此，闭区间 \[0, 1\] 构成 `M` 的连续谱。

存在三种不同的谱类型。 其中两种已在前面说明：点谱和连续谱。 第三种是剩余谱。 它稍后会说明，即使在量子中它的重要性不大。

为结束本节，提供了一个额外的示例，说明 Banach 代数中幂级数的用法。

### 例 8.19

设 `v` 在 Banach 代数 `A` 中。 载体集现在由多项式和形式幂级数展开组成。 定义 `w` 等于以下无限和表示：

`e^(v)`=`I`+`v`+`v²`/2+`v³`/3!+`v⁴`/4!+…. 由于该级数在该 Banach 代数中绝对收敛，`w` 也在 `A` 中。 而且，如果 `u` 也在 `A` 中且乘积可交换，即如果 `uv`=`vu`，则 `e^(u+v)`=`e^(u)` `e^(v)`。 (Muger, 2020)。

## 8.7 Banach 代数中的理想

对于 Banach 代数 `A`，`A` 中理想的概念涉及子集 `B`。 每当该子集满足对于 `A` 中的 `v` 和 `B` 中的 `w` 乘积 `v·w` 在 `B` 中时，则 `B` 称为 `A` 的左理想。 当对于所有 `v` 在 `A` 中 `w·v` 在 `B` 中时，子集 `B` 称为右理想。 当它既是左理想也是右理想时，称为双边理想，或简称理想。 图 8.3 使用 Venn 型图说明了左理想和右理想。 当 `B` 与 `A` 不同且与零不同时，理想称为真理想。 当 `B` 为真理想，且 `B` 不包含在另一个不同的真理想中时，`B` 称为极大。

![图 8.3 左理想和右理想。](img/F000059f08-03-9780443136979.jpg)

图 8.3 左理想和右理想。

接下来描述在交换 Banach 代数 `A` 中闭且极大的理想 `B` 的重要性。 在这种情况下，`B` 是一个向量空间，且商空间 `A/B` 本身是一个 Banach 代数。 `A/B` 中的结果元素是形式为 `[v]`=`v·B`={v·w, 使得 w 在 B} 的等价类 (Palmer, 1994)。 该 Banach 代数中的范数由 `‖[v]‖`=inf‖v·w‖ 给出，对于 w 在 B。 由 CBS 不等式可知 `‖[u] [v]‖` 小于或等于 `‖[u]‖` `‖[v]‖`。

一种特殊的 Banach 代数，即 Banach* 代数，已在 第 3.8 节 中描述。 下一个示例给出了星运算的用法说明。

### 例 8.20

设 `u` 和 `v` 在 `A` 中，其中 `A` 是 Banach* 代数。 假设 `v`=`v*`。 对于 `t` 在 `R` 中，考虑 `w`=`e^(ivt)` 其中 `w`=`e^(ivt)`=`I`+`ivt`+((`ivt`)²)/2 +…. 由于级数绝对收敛，该量也位于 `A` 中。 在极限中扩展 * 运算的性质 (1) 和 (2)，即使用上述求和；可知 (`e^(ivt)`)*=`e^(−ivt)`：

1. 1) 对合的：(`T*`)*=`T`

2. 2) 加性的：(`S+T`)*=`S*`+`T*`

这意味着 Banach* 代数`‖(e^(ivt)) e^(−ivt)‖`=1，因此`‖w‖`=1。

两个 C* 代数 `C1*` 和 `C2*` 之间的 * 同态是一个线性映射 `L`，使得：

`L`: `C1*`→`C2*` 满足三个方程恒等式：

1. 1) 恒等式：`L (I)`=`I`。

2. 2) 乘积：`L (S T)`=`L (S) L (T)`，对于 `C1*` 中的 `S` 和 `T`。

3. 3) 对合：`L (T*)`=`L (T)*`。

除了保持对合之外，该映射也是压缩的。 也就是说，该映射是范数小于或等于一的连续映射。 所以 `C1` 中 `T` 的范数大于或等于 `C2` 中 `L (T)` 的范数。 当 `L` 为单射时，该映射是等距的。 图 8.4 说明了两个 C* 代数之间的同态。

![图 8.4 涉及 C* 代数的同态的图。](img/F000059f08-04-9780443136979.jpg)

图 8.4 涉及 C* 代数的同态的图。

## 8.8 格尔范德-奈马克-塞加尔构造



一个 `C*` 代数 `A` 的表示由一个星同态和一个希尔伯特空间 `H` 组成，即 (`L`, `H`)，其中 `L`: `A`→`B`(`H`)，是 `H` 上所有有界算子的集合。表示 (`L`, `H`) 在 `L` 为 1–1 时称为忠实的；由于 `L` 是线性的，这等价于以下条件：如果 `L`(`f`)=0，则 `f`=0。表示被称为循环的当且仅当在 `H` 中存在循环向量 `v`。这意味着 (`L`(`H`) `v`) 的闭包 =`H`。等价地说，向量 `v` 对 `B`(`H`) 是循环的。直观上，循环向量是指对该向量依次反复进行算子型应用后得到整个空间。向量 `v` 的另一个定义是它是分离的。这里，当 `T` `v`=0 且 `T` 在 `B`(`H`) 中时，`v` 是分离的意味着 `v`=0。循环与分离概念之间的重要关系归因于 Gelfand-Naimark-Segal，并称为 `GNS` 构造。该关系在 `C*` 代数中成立。在这种情况下，向量 `v` 对 `B`(`H`) 是循环的当且仅当 `v` 对换子 `A′` 是分离的。换子在 第 3.3 节 中已有描述。它是与 `A` 中所有其他元素都交换的元素子集。循环向量的存在是 `GNS` 构造中的主要贡献之一。

说 `v` 对换子 `A′` 是分离的意味着 `A′` 的每个元素 `w` 都与 `v` 交换，即 `w` `v`=`v` `w`。这里，`A′` 是 von Neumann 代数。在本节中，代数应被视为仅由 `H` 上的所有有界算子组成的 `C*` 代数。关于 von Neumann 代数的额外事实将在下一章中描述。

对于循环的 `v`，所有这样的 `u` `v` 的集合在 `H` 中稠密。因此，`w` `u` `v`=0，从而 `u`=0 在 `H` 的一个稠密子集上成立。由连续性可知 `u`=0 处处成立，因而 `v` 是分离的。每当 `A` 也是一个 von Neumann 代数时，则在 `A` 中既循环又分离的向量也在 `A′` 中循环且分离 (Sakai, 1971)。接下来给出一个循环向量的有趣例子。

### 示例 8.21

作为循环向量 `v` 的一个例子，考虑载体集 `H`=`R^n`，类型为 VECTOR。在此希尔伯特空间中使用通常的内积和矩阵运算 (He’lein, 2014)。设 `L` 在 `B`(`H`) 中，并假设 `L` 是自伴的。则 `L` 可使用自伴 `ON` 基对角化。设特征向量集合为 {`e1`, `e2`,…, `en`}，以及全部实特征值集合 {`c1`, `c2`,…, `cn`}。每个特征值 `ck` 都在 `L` 的点谱中，即它在 `sppL` 中。因此可得 `L` `ek`=`ck` `ek`，对所有上述 `k` 成立。简而言之，`ck` 是特征值且 `ek` 是特征向量。此外，当所有特征值互不相同时，`v` 是循环的；否则不是。为此，将 `L` 表示为矩阵；则根据 Cayley-Hamilton 定理，`L` 满足其特征方程：`L^n`=tr(`L`) `L^{n−1}`+…+ (−1)^`n` det(`L`)。

由于 `H` 是有限维的，`v` 是循环的当且仅当 {`v`, `L` `v`,…, `L^{n−1}` `v`} 是 `H` 的一组基。利用前面提到的特征向量，`v`=`d1` `e1`+`d2` `e2`+…+`dn` `en`。现在，让 `L` 的幂作用于向量 `v`，`L^k` `v`=`d1` `L^k` `e1`+`d2` `L^k` `e2`+…+`dn` `L^k` `en`。将特征值代入该方程可得 `L^k` `v`=`d1` `c1^k` `e1`+`d2` `c2^k` `e2` +…+ `dn` `cn^k` `en`，其中 `k`=0, 1, 2,…, `n−1`。这些方程可以写成由 `L` 的特征值组成的 `n` by `n` 矩阵，乘以一个 `n` by one 列向量。该矩阵乘以 `n` by 1 列向量具有元组 `dj` `ej`，如下所示。其后是具有元组 `L^(j)`![方程](img/F000059si26.png) `v` 的结果 `n` by 1 列向量：

$\\begin{matrix} \\left| 1 \\right. & 1 & \\ldots & \\left. 1 \\right| & \\left| d1 e1 \\right| & & \\left| L^{0}v \\right| \\\\ \\left| {c1} \\right. & {c2} & \\ldots & \\left. \\text{cn} \\middle| \\right. & \\left| d2 e2 \\right| & = & \\left| L^{1}v \\right| \\\\ & \\ldots & & & \\ldots & & \\ldots \\\\ \\left| {c1}^{n - 1} \\right. & {c2}^{n - 1} & \\ldots & \\left. {cn}^{n - 1} \\right| & \\left| {dn}{en} \\right| & & \\left| L^{n - 1}v \\middle| . \\right. \\\\ \\end{matrix}$

![方程](img/F000059si27.png)

上面的 `n` by `n` 矩阵是 Vandermonde 矩阵，且当且仅当两列相等时它等于零。因此 `v` 是循环的当且仅当特征值互不相同。 (Horn et al., 1957).#

`C*` 代数中的范数是唯一的，且完全由其代数结构决定。另一个 `GNS` 结果是每个 `C*` 代数都与希尔伯特空间 `H` 上的有界线性算子 `B`(`H`) 的闭子反演代数等距且对合同构。这在 图 8.5 中有所说明。此外，当 `C*` 代数可分时，`B`(`H`) 也可以可分。此外，对于交换 `C*` 代数，它与在无穷远处消失的复值连续函数代数同构。这些函数定义在紧 Hausdorff 空间上。`GNS` 结果指定了 `C*` 代数 `A` 在希尔伯特空间 `H` 上的表示，有界函数 `B`(`H`)。这是一个星同态 `h`，`h`: `A`→`B`(`H`)。并且 `h`(`I`)=`I`。此外，对于 `C*` 中的态 `w`，存在 `A` 在希尔伯特空间 `H` 上的表示，其中 `H` 中有一个单位向量 `v`，使得对所有 `x` 在 `A` 中都有 `w`(`x`)=<`v`, `h`(`x`) `v`>。一般而言，使用纯态的 `GNS` 构造给出一个不可约表示；它不能分解为更简单表示的直和。混合态通常导致独立表示的直和。

![图 8.5 A C* 代数与希尔伯特空间之间的 GNS 构造。GNS，Gelfand-Naimark-Segal.](img/F000059f08-05-9780443136979.jpg)

图 8.5 GNS 构造在 A `C*` 代数与希尔伯特空间之间。`GNS`，Gelfand-Naimark-Segal。

当 `C*` 代数 `A` 为有限维时，它与由 `nk` by `nk` 复值矩阵 `Mnk` 的直和构成的 `C*` 代数同构，`k`=1, 2,…, `N`。`GNS` 构造表明在量子领域 `C*` 代数由可观测量生成。此外，当 `L` 是 `A` 在希尔伯特空间 `H` 上的表示且 `v` 是归一化的循环向量时，`f`→<`L`(`f`) `v`, `v`> 是 `A` 中的一个态。回想一下，态是 `A` 上的正泛函 `f` on `A`，`f`: `A`→`C`；对所有 `T` 在 `A` 中，`f`(`T*` `T`) 大于或等于零；且 `f`(`I`)=1。`A` 中的算子 `T` 也称为测量算子；它总是自伴的。此外，泛函 `f` 通常是期望算子。`A` 的子集 `J` 是 `A` 的左理想，其中 `J`={ `B` in `A` | `f`(`B*` `B`)=0 }。商空间 `V`=`A`/`J` 可通过对 `B`, `D` in `A` 使用 <[`B`], [`D`]> = `f`(`B*` `D`) 构成内积空间。经完备化后，`V` 成为希尔伯特空间 (Sakai, 1971)。

`GNS` 构造说明了 `C*` 代数与希尔伯特空间上有界函数之间的紧密联系。一个例子将展示这种关系。

### 示例 8.22

考虑所有复数上的二阶矩阵的幺结合代数 `A`。它也是一个 Banach 代数，因此在矩阵的伴随运算下，`A` 成为一个 `C*` 代数。下面给出的 `GNS` 构造涉及一个纯态，并将给出 `A` 与希尔伯特空间 `C²` 的有界函数子代数之间的同构。为此，取任意元素，即 `A` 的任意复值矩阵 `M`。然后定义一个态 `f`，`f`: `A`→`C`，其中 `f`(`M`) 是矩阵中的 (1,1) 项，对于下面的矩阵，`f`(`M`)=`a`，

$\\begin{matrix} {|a} & {b|} \\\\ {|c} & {d|} \\\\ \\end{matrix}.$

![方程](img/F000059si28.png)



这是态，因为它是线性的、非负的，并且 `f` 在单位矩阵上的取值是 `f(I)=1`。非负性由 `f(M*M)=a*a+c*c=|a|²+|c|²` 可知。对于 `GNS` 构造，可以在 `A` 上定义一个关于 `A` 中矩阵 `M` 和 `N` 的半双线性形式，其中 `N=` 
$\\begin{matrix} {|m} & {n|} \\\\ {|p} & {q|} \\\\ \\end{matrix}.$
![Equation](img/F000059si29.png)
因此令这两个矩阵的伪内积 `<M, N>=f(M*N)=ma*+pc*`。这给出了 `A` 上的一个半双线性形式。接下来，将找到 `A` 的一个子空间 `J`，使其成为 `A` 的左理想。对 `J` 使用 `J={M in A, such that f(M*M)=0}`。这里，由上式可知 `a=c=0`，且 `‖M‖²=<M, M>=0`。相应地，`J` 是 `A` 的子空间，其中 `M` 的第一列为零。对 `A` 中的矩阵 `N` 与 `J` 中的矩阵做一次快速乘法会得到 `J` 中的另一个矩阵，从而表明 `J` 是 `A` 的左理想。换句话说，对于 `A` 中的任意 `N`，`N` 与 `J` 中任意矩阵 `j` 的乘积会得到 `J` 中的另一个矩阵 `j′`。
对于 `GNS` 构造，通过令 `H=A/J`，商空间，得到一个希尔伯特空间。对商空间的深入 `MSA` 发展在 第 10.1 节 中给出。下面只需要商空间的基本事实。无论如何，`H` 中等价类相关的内积由上面的半双线性形式诱导。因此，两个等价类 `[M]` 和 `[N]` 的内积在 `H` 中由 `<[M], [N]>` 给出，其等于 `<M, N>=f(M*N)`。注意，对于 `H` 中的 `[M]`，陪集 `[M]` 等于 `A` 中的一个矩阵加上来自 `J` 的第一列为零的矩阵之和。这些矩阵按顺序如下给出：
$\\begin{matrix} \\begin{matrix} {|a} & {b|} \\\\ {|c} & {d|} \\\\ \\end{matrix} & \\begin{matrix} {|0} & {n|} \\\\ {|0} & {q|} \\\\ \\end{matrix} \\\\ \\end{matrix}.$
![Equation](img/F000059si30.png)
作为等价类 `[M]` 的代表，我们将使用以下矩阵作为陪集代表：
$\\begin{matrix} {|a} & {0|} \\\\ {|c} & {0|} \\\\ \\end{matrix}.$
![Equation](img/F000059si31.png)
注意 `f(M*N)=ma*+pc*`。这是因为 `M*` 和 `N` 按顺序给出：
$\\begin{matrix} \\begin{matrix} {|{a\*}} & {{c\*}|} \\\\ {|0} & {0|} \\\\ \\end{matrix} & \\begin{matrix} {|m} & {n|} \\\\ {|p} & {q|} \\\\ \\end{matrix} \\\\ \\end{matrix}.$
![Equation](img/F000059si32.png)
接下来令 `L` 为 `A` 在希尔伯特空间 `H` 上的一个表示，即令 `L: A→End(H)` 其中 `L(N): [M]→[N M]`，于是利用上面的 `N` 和 `[M]` 有 `L(N)(M)=`
$\\begin{matrix} {|{\\text{ma} + \\text{nc}}} & {0|} \\\\ {|{\\text{pa} + \\text{qc}}} & {0|} \\\\ \\end{matrix}.$
![Equation](img/F000059si33.png)
这是因为 `N`、 `[M]` 和 `N·[M]` 按顺序如下给出，
$\\begin{matrix} \\begin{matrix} \\left| m\\quad n \\right| & \\left| a\\quad 0 \\right| & \\left| \\text{ma} + \\text{nc}\\quad 0 \\right| \\\\ \\end{matrix} \\\\ \\begin{matrix} \\left| p\\mspace{27mu} q \\right| & \\left| c\\mspace{20mu} 0 \\right| & \\left| \\text{pa} + \\text{qc}\\mspace{23mu} 0 \\middle| . \\right. \\\\ \\end{matrix} \\\\ \\end{matrix}$
![Equation](img/F000059si34.png)
此外，注意 `A` 中的单位向量 `I` 在 `H` 中对应于 `v=[I]=`
$\\begin{matrix} {|1} & {0|} \\\\ {|0} & {0|} \\\\ \\end{matrix}$
![Equation](img/F000059si35.png)
向量 `v` 是 `H` 中的一个归一化循环向量。向量 `v` 生成 `H`。对于 `A` 中的任意 `N`，有 `f(N)=<v, L(N) v>`。这是因为 `f(N)=m`，且 `L(N) v=`
$\\begin{matrix} {|m} & {0|} \\\\ {|p} & {0|} \\\\ \\end{matrix}$
![Equation](img/F000059si36.png)
因此 `f(v* L(N) v)=m`。相应地，希尔伯特空间 `H` 与 `C²` 同构，其中该空间中的向量由来自表示 `L(N)` 的矩阵如 `N` 所作用。`GNS` 构造从 `C*` 代数 `A` ——所有复值二阶矩阵——出发产生了一个希尔伯特空间 `C²`。

## 8.9 生成 C\* 代数
对于包含单位元的 `C*` 代数 `A` 的任意子集 `S`，包含 `S` 的最小 `C*` 代数称为由 `S` 生成的 `C*` 代数。它记为 `B`，并通过取包含 `S` 的所有 `C*` 代数的交集得到。此外，对于 `B` 中的任意元素 `T`，`T` 在 `B` 中的谱等于 `T` 在 `A` 中的谱。

### 示例 8.23
使用来自 `A` 的向量集合 `S` 的元素生成 `C*` 代数 `B` 的准则听起来很容易做到。然而，注意到 `B` 中 `T` 的谱也必须在 `T` 在 `C*` 中的谱中，表明在寻找 `B` 时可能存在困难。确实如此。`C*` 代数 `B` 必须由集合 `S` 中的向量构建起来。`C*` 代数的全部闭包运算必须对 `B` 中的元素 `T` 成立。这意味着所有向量空间闭包运算都必须成立。因此，`S` 中向量的线性组合属于 `B`。这意味着用所有复数按比例缩放 `S` 中的向量，然后以所有可能的方式将它们相加必须属于 `B`。
由于 `C*` 结构是一个代数，乘法也必须封闭。因此，`S` 中向量的线性组合以及这些线性组合的倍数必须属于 `B`。此外，它是一个巴拿赫空间，这些倍数的范数必须存在，并且它必须是范数闭的。最后，这些元素的伴随也必须属于 `B`。总之，`B` 的元素具有形式，$\\sum\_{j = 1}^{n}\\left( {c\_{j}T\_{j,1} \\cdot T\_{j,2} \\cdot T\_{j,3}\\cdots T\_{j,k}} \\right)$![Equation](img/F000059si37.png)，对于所有非负 `n` 和 `C` 中的 `c[j]`，以及当 `n→∞` 时的极限![Equation](img/F000059si38.png)。这里，`T[j],[i]` 在 `S` 或 `S*` 中。前面提到的求和通常用 `{T[j],[i], T[j],[i]*}`^(n)，`n=0, 1, 2,…` 简写，且 `T[j],[i]` 在 `S` 中。此外，对于 `n=0`，这意味着恒等算子也在由 `S` 生成的代数中。
最平凡的例子之一是复数域上的二阶复值矩阵。如果 `S={I}`，则 `B={I}`^(n)；它仅由 `{c I}` 组成，对于所有复值 `c`。在这种情况下，结果是所有对角线元素相同的对角矩阵，即所有纯量矩阵。

## 8.10 格尔范德公式
有界算子 `T` 的谱半径公式在巴拿赫代数中给出：这里，`r(T)` 定义为 `B` 中的 `T`。它是 `r(T)=sup {|c|, such that c is in the spectrum of T}`。它也可以用格尔范德公式求得：取 `n=1, 2, 3,…` 时的 `inf‖T^(n)‖^(1/n)`，或取 `n` 趋于无穷时 `‖T^(n)‖^(1/n)=m` 的极限，非零。无论如何，级数 $\\sum\_{n = 0}^{\\infty}\\left\\lbrack {T^{n}z^{n}} \\right\\rbrack$![Equation](img/F000059si39.png) 当 `|z|<1/m` 时绝对收敛（Murphy, 1990）。

### 示例 8.24
作为格尔范德公式的说明，考虑由矩阵巴拿赫代数中具有通常运算的所有 2×2 矩阵组成的载体集合。矩阵 `M` 如下给出，连同 `M⁵` 和 `M⁷`。`M` 的特征值为 −1 和 5；这构成了 `M` 的点谱。
$\\begin{matrix} {M =} & \\left| 1 \\right. & \\left. 2 \\right| \\\\ & \\left| 4 \\right. & \\left. 3 \\right| \\\\ \\end{matrix}\\quad\\quad\\begin{matrix} {M^{5} =} & \\left| 1041 \\right. & \\left. 1042 \\right| \\\\ & \\left| 2084 \\right. & \\left. 2083 \\right| \\\\ \\end{matrix}\\quad\\quad\\begin{matrix} {M^{7} =} & \\left| 26041 \\right. & \\left. 26042 \\right| \\\\ & \\left| 52084 \\right. & \\left. 52083 \\right| \\\\ \\end{matrix}$
![Equation](img/F000059si40.png)
对于上面三个矩阵，给出了它们范数的相应根以及另外两个实例。`M` 的谱半径为 5，且对于 `‖M^(n)‖^(1/n)` 中较大的 `n` 值，值 5 正在被逼近：`‖M‖=5.391`，`‖M⁵‖^(1/5)=5.053`，`‖M⁷‖^(1/7)=5.037`，`‖M¹⁵‖^(1/15)=5.017`，且 `‖M²⁵‖^(1/25)=5.010`。



对于任意 `C*` 代数，若 `T` 是自伴的，则谱半径 `r(T)` = lim [`n` → ∞] ‖`T`^(2^( `n` ))‖^(2^(− `n` )) ![方程](img/F000059si41.png)。 这可由自伴性质推出，‖`T`²‖=‖`T* T`‖=‖`T`‖²。 然后通过数学归纳法，对任意正整数 `n`，可得 ‖`T`^(2^( `n` ))‖ = ‖`T`‖^(2^( `n` )) ![方程](img/F000059si42.png)，于是 ‖`T`^(2^( `n` )) ![方程](img/F000059si43.png) ‖^(2^(− `n` )) = (‖`T`‖^(2^( `n` )))^(2^(− `n` )) ![方程](img/F000059si44.png) = ‖`T`‖。 该结果可用于证明 `C*` 代数中的范数必须是唯一的（阿尔维森, 1976）。
结论结构是一个 Banach 代数。如前所述，除非另有说明，本文档中 Banach 代数被理解为幺元且结合的。这是 Banach 代数没有单位元的一个著名例子。

## 示例 8.25
这是交换但没有幺元的 Banach 代数的一个例证。 考虑 `L¹` 中所有复值、绝对可积的函数。 在此情况下，令 `BINE`(f, g)=f 与 g 的卷积。 因此，`conv`(f, g)(t)= ∫[0]^∞ ![方程](img/F000059si45.png) `f`(s) `g` (t−s) ds。 `L¹` 中没有函数作为恒等元。 然而，在运算演算中的广义函数中，`delta` 函数充当恒等元。 `delta` 函数的用法在 第 6.3 节 中用于隧穿效应作了说明。

## 参考文献
* 阿尔维森, 1976 Arveson W. *对 C\* 代数的邀请* Springer-Verlag 1976; 0-387-90176-0.
* 贝西科维奇, 1954 Besicovitch A. *几乎周期函数* Dover Publications 1954;.
* 邦萨尔和邓肯, 1973 Bonsall F, Duncan J. *完备赋范代数* Springer 1973; ISBN 978-3-642-65671-2.
* 康威, 1990 Conway J. *泛函分析教程*. vol. 96 second ed. Springer-Verlag 1990; 978-0-387-97245-9.
* 盖尔鲍姆和奥尔姆斯特德, 2003 Gelbaum, Olmsted. *数学分析中的反例* Courier Co 2003;.
* Halmos, 1957 Halmos P. *希尔伯特空间导论与谱重数理论* Chelsea Pub. Co. 1957;57–12834.
* 埃莱因, 2014 He’lein F. *谱理论*. 7 Paris: UMR CNRS, U Paris Didero; 2014;1014.
* 霍恩和约翰逊, 1957 Horn R, Johnson C. *矩阵分析专题* Cambridge University Press, 1991. Chelsea Pub. Co 1957;57–12834.
* 莱西, 1973 Lacey H. 任意无限维可分 Bench 空间的 Hamel 维数是 c。 *Am Math Mon.* 1973;80:298.
* 麦考伊, 1929 McCoy N. 量子力学代数中的对易公式。 *Transactons Am Math Soc.* 1929;31.
* 穆格, 2020 Muger M. *关于 Baker-Campbell-Hausdorff-Dynkin 定理的笔记* BCHD 2020;.
* 墨菲, 1990 Murphy G. *C\* 代数与算子理论* Academic Pres 1990;.
* 帕尔默, 1994 Palmer T. *Banach 代数与 \*-代数的一般理论* Cambridge U. Press 1994;.
* Sakai, 1971 Sakai S. *C\* 代数与 W\* 代数* Springer 1971; 3-540-63633-1.

# 第 9 章
## 冯·诺依曼代数
### 摘要
本章首先对算子拓扑进行描述。 特别是，给出了范数收敛、强算子收敛和弱算子收敛的概念。 其后是这些收敛过程之间的关系。 下一节引入冯·诺依曼代数并描述了该代数的两个非常重要的实例。 W\* 代数是希尔伯特空间上有界算子的 \* 代数，其在弱算子拓扑（WOT）下封闭并包含恒等算子。 W\* 代数的另一个实例是本质有界可测函数环，`L^∞(R)` ![方程](img/F000242si1.png)。 它是一个交换的冯·诺依曼代数，由在 `L²` ![方程](img/F000242si2.png) 函数的希尔伯特空间上作为逐点乘法的元素组成。 第 9.3 节陈述了双交换子定理。 双交换子使用与生成 C\* 代数时所采用的类似准则来说明。 接下来，格尔范德变换被描述为从交换 C\* 代数到 C(Δ(A)) 的映射，其中 C(Δ) 是 A 上所有复值连续泛函的代数。

#### 关键词
范数收敛; 强算子收敛; 弱算子收敛; 冯·诺依曼代数; 双交换子; 算子拓扑; 特征函数; 测度; σ-有限; 本质有界; 格尔范德变换

## 9.1 算子拓扑
弱算子拓扑（WOT）： 对所有 `v`、`w` 在 `H` 中，`Tk` → `T`，k=1, 2, … WOT 意味着收敛是相对于内积定义的，即当 k 趋于无穷时，`<v, Tk w>` → `<v, T w>`。 另一方面，强算子拓扑（SOT），SOT：`Tk` → `T`，意味着对所有 `v` 在 `H` 中，即当 k 趋于无穷时，范数 ‖`Tk v` − `T v`‖ → 0。 这种收敛类似于函数空间中的逐点收敛。 最强的收敛是在范数拓扑中：`Tk` → `T`，这意味着当 k 趋于无穷时算子范数 ‖`Tk` − `T`‖ → 0。 这种收敛类似于函数空间中的一致收敛。 范数收敛蕴含强算子收敛，而强算子收敛本身蕴含弱算子收敛。 对于 `T` 和 `T[n]` ![方程](img/F000242si3.png) 在 B(`H`) 中，对于 n=0, 1, 2, …，不等式序列成立； |<v, (`T[n]` − `T`) w>| 小于或等于 ‖(`T[n]` − `T`) w‖ ‖v‖，而后者小于或等于 ‖`T[n]` − `T`‖ ‖w‖ ‖v‖。 这表明范数收敛蕴含 SOT，而 SOT 又蕴含 WOT 收敛。 这些陈述的逆命题是错误的，并在接下来的几个例子中加以说明。

#### 示例 9.1
考虑希尔伯特空间，`H`=l²。 设等距 `T[n]` 将序列 (`v[0]`, `v[1]`, `v[2]`, …) 映射为新序列，前 n 个元组为零，并从第 n+1 个元组开始向右移动原始元组。 即，`T[n]`(`v[0]`, `v[1]`, `v[2]`, …)=(0, 0, … 0, `v[0]`, `v[1]`, `v[2]`, …)。 还考虑投影算子 `P[n]`，它只是用零替换 l² 中任意向量 `w` 的前 n 个元组。 即，`P[n]`(`w[0]`, `w[1]`, `w[2]`, …)=(0, 0, … 0, `w[n]`, `w[n+1]`, …)。 然后使用 l² 中的任意向量 `w` 和 `v`，绝对内积 |<w, `T[n]`v>|=|<`P[n]` w, `T[n]`v>|。 但该量小于或等于 ‖`P[n]` w‖ ‖`T[n]`v‖=‖`P[n]` w‖ ‖v‖ → 0，当 n → ∞ 时，因为 $\\left\\| {P\_{n}w} \\right\\|^{2} = \\sum\_{k = n}^{\\infty}\\left. {|w\_{k}|}^{2}\\rightarrow 0 \\right.$ ![方程](img/F000242si4.png) 当 k → ∞ 时。 因此 `T[n]` 在 WOT 中收敛于零。 然而，如前所述算子 `T` 是等距的，‖`T[n]`v‖=‖v‖，对所有 n 和 `H` 中的任意 v 成立，因此它在 SOT 中不收敛。 一般而言，弱收敛并不蕴含强收敛。

#### 示例 9.2



强收敛并不蕴含范数收敛。为说明这一点，令载体集再次为希尔伯特空间，`H`=`l²`。还使用投影算子 `P[*n*]`，它只是将 `l²` 中任意向量 `w` 的前 `n` 个元组替换为零。即，`P[*n*] (w[0], w[1], w[2], …)=(0, 0, … 0, w[*n*], w[*n*+1], …)`。`‖P[*n*] w‖² → 0`, as `n → ∞`![方程](img/F000242si5.png)，因为 $\\sum\_{k = n}^{\\infty}\\left. w\_{k}^{2}\\rightarrow 0 \\right.$![方程](img/F000242si6.png)。这表明 `SOT`。在这种情况下，不存在范数收敛。对于任意 `m > n`，考虑 (`P[*n*] − P[*m*]`) (`w[0], w[1], w[2], …`) = (0, 0, … 0, `w[*n*]`, `w[*n*+1]`, … `w[*m*]`, 0, 0, …)。然后，存在 `l²` 中的向量 `u`，使得 (`P[*n*] − P[*m*]`) `u`=`u`。因此，`‖P[*n*] − P[*m*]‖=1`，因此 `P[*n*]` 不是 `CS`，因而它在范数下不收敛。

## 9.2 两个基本的 von Neumann 代数
von Neumann 代数通常记为 `W*` 代数。它是希尔伯特空间上有界算子的星代数，在 `WOT` 下封闭且包含恒等算子。`W*` 代数的两个著名例子是本质有界可测函数环，`L^∞(R)`。它是一个交换的 von Neumann 代数，由在 `L²` 函数的希尔伯特空间上作为逐点乘法的元素组成。第二個例子由维数大于一的希尔伯特空间上的所有有界算子组成。该代数是非交换的。这些的证明可在 Jones (2010) 中找到，另见 Nelson (2017)。仅给出简要说明，以阐释前面提到的第一个结果证明中所需的某些概念。该证明表明该结构是一个 von Neumann 空间。首先，证明中假设了一个 σ 有限测度 (`X, Ω, μ`)。该结构在附录 A.2 中定义。还需要集合 `M=L^∞(R)`，它是 `R` 上本质有界可测函数的赋范向量空间，具有本质上确界范数 `‖f‖[∞]`。该范数等于 inf {`N`，非负 `N`，使得 | `f(x)` | 小于或等于 `N`，除了 `X` 中测度为零的集合 `A` 之外，即 `μ(A)` 为零}。以下是该范数的例子。

### 例 9.3
作为 `‖f‖[∞]` 范数的一个实例，考虑函数 `f`，其中 `f: R → R`，且 `f(t)=zero`，除在开区间 (2, 4) 内 `f(t)=1/ t` 外，并假设 `f(4)=5`。则 `‖f‖[∞]=1/2`，因为点四的测度为零，在使用该范数时无关紧要。在涉及 `L²` 空间上乘法的 von Neumann 代数证明中还指出了 `L²` 中有界函数的使用。在此，建立了 `L^∞(R) → B(L²(X, μ))` 的嵌入，其像为 `B(L²(X, μ))` 中的一个 von Neumann 代数。在此情况下，`μ` 为勒贝格测度。该空间由所有有界且绝对平方可积的函数组成。`L²` 中的函数并非全部有界，如下例所示。

### 例 9.4
使用实线上的函数序列，`f*n*=n^(1/2)`，对于 `t` 在区间 (`n`, `n+1/n`) 内，`n=1, 2, 3,…`，在 `R` 的其他地方为零。函数 `f*n*` 在 `B(L²(X, μ))` 中。然而，当 `n` 趋于无穷时该序列的极限不在 `B(L²(X, μ))` 中，即使它在 `L²(X, μ)` 中，值为一。

## 9.3 von Neumann 代数中的换位子
von Neumann 代数 `A` 由希尔伯特空间中有界算子的酉星子代数组成。因此，`I` 总在 `A` 中，连同 `A` 中任意元素的伴随。von Neumann 代数在弱算子拓扑下封闭。这与 `C*` 代数不同。`C*` 代数在范数拓扑下封闭。换位子 `A’` 也是一个 von Neumann 代数。换位子 `A’` 已在涉及矩阵的前一节中描述并举例说明。这里，`A’={v in B(H), such that v w=w v for all w in A}`。此外，`A` 与 `A’` 的交集 `Z(A)` 是称为 `A` 中心的 von Neumann 代数。每当 `Z(A)=A` 时，`A` 称为阿贝尔。双换位子是 `A’’=(A’)’`。对于希尔伯特空间 `H` 中的有界算子 `T`，双换位子可由生成集 `{T, T*}^(n)`，`n=0, 1, 2,…` 得到。这是 `C*` 代数 `A` 的子集 `S`，包含恒等式 `T⁰=I`。它是包含 `S` 的最小 `C*` 代数，可通过取 `T` 和 `T*` 的标量积、和、积以及积的和得到。有关生成集的例子见第 8.9 节。von Neumann 双对易子定理指出，当 `A` 是 `B(H)` 的子集，且是酉的并且是 `B(H)` 的星子代数时，则 `A` 在 `A″` 中强稠密 (Dixmier, 1981)。

### 例 9.5
考虑下面给出的希尔伯特空间 `H=C²` 中 `T` 的双换位子。其结果为复数域 `C` 上的所有二阶复值矩阵。这里给出了 `T` 以及 `T*`。
$\\begin{matrix} \\begin{matrix} {|0} & {1|} \\\\ \\end{matrix} & \\begin{matrix} {|0} & {0|} \\\\ \\end{matrix} \\\\ \\begin{matrix} {|0} & {0|} \\\\ \\end{matrix} & \\begin{matrix} {|1} & {0|} \\\\ \\end{matrix} \\\\ \\end{matrix}.$
![方程](img/F000242si7.png)
连同恒等式 `I`，量 `{T, T*}^(n)` 表示这些量的所有标量倍、和、积和线性组合，以及所有这些项的强算子闭包。这导致了复数上的二阶矩阵代数。在 von Neumann 代数 `V` 中，迹 `Tr` 是 `B(H)` 的子代数，针对正自伴算子。它涉及 `V+={A, such that A in V and <v, Av> is greater than or equal to zero for all v in H.}`。`V` 上的迹 (Nelson, 2017) 为 `Tr: M+ → [0, ∞]`，使得：
1. 1) 可加性：`Tr(A + B)=Tr(A) + Tr (B)`，对于 `A` 和 `B` 在 `V+` 中。
2. 2) 齐次性：`Tr (c A)=c Tr (A)` 对于 `A` 在 `V+` 中，`c` 大于或等于零。
3. 3) 忠实性：`Tr (A)=0` 蕴含 `A=0`。
4. 4) 正规性：对于 `V+` 中单调递增序列 `Ak` 在算子范数下收敛到 `V+` 中的 `A`，则 `Tr (Ak)` 收敛到 `Tr (A)`。
5. 5) 半有限性：对于所有 `A` 在 `V+` 中，`Tr (A)=sup {Tr (B), such that B is in V+, Tr (B) is finite, A − B is greater than or equal to zero}`。
更一般地，对于不一定为正的 `A`
6. 6) 迹性：`Tr(A A*)=Tr (A* A)` 对于 `A` 在 `V` 中。

### 例 9.6
设 von Neumann 代数为 `V=B(H)` 且 `A` 在 `V+` 中，则 `V` 的迹函数利用 `H` 的 ON 基 `{en}`，`n=1, 2,…`。`Tr (A)=sum $\\sum\_{n = 1}^{\\infty}{< {en},{Aen} >}$`![方程](img/F000242si8.png)。任何其他迹的形式为 `c Tr (A)`，其中 `c > 0`。

### 例 9.7
考虑希尔伯特空间 `H=C^(n)`，并令 `Mn(C)` 为构成 von Neumann 代数 `B(H)` 的所有 `nxn` 复矩阵的集合。迹 `Tr: Mn(C) → C`，其中对于 `A` 在 `Mn(C)` 中，则 `Tr(A)=sum $\\sum\_{j = 1}^{n}{Ajj}$`![方程](img/F000242si9.png)，其中 `Ajj` 为 `A` 中的对角元素。使用 `Mn(C)` 中的标准基 `{e1, e2n, …, en}`，`Tr(A)=sum, $\\sum\_{j = 1}^{n}{< {ej},{Aej} >}$`![方程](img/F000242si10.png)。对于 `Mn(C)` 中任意 ON 基 `{f1, f2, …, fn}`，`Tr(A)=< fj, Afj >`。设 `U` 为将列向量 `ej` 映射到 `fj` 的酉矩阵，即 `Uej=fj`，`j=1, 2,…, n`。Then `Tr(A)=sum, $\\sum\_{j = 1}^{n}{< {fj},{Afj} > = {sum}}$`![方程](img/F000242si11.png) $\\sum\_{j = 1}^{n}{< {Uej},{AUej} > = {Tr}\\left( A \\right) = {sum}}$`![方程](img/F000242si12.png) $\\sum\_{j = 1}^{n}{< {ej},U\*{AUej} > = {Tr}\\left( {U\*{AU}} \\right) = {Tr}\\left( {{AUU}\*} \\right) = {Tr}\\left( A \\right)}$`![方程](img/F000242si13.png)。

## 9.4 格尔范德变换



对于任意 Banach 代数 `A`，在 `C` 上，令 `Δ` 为 `A` 上所有乘性线性泛函的空间。这些也称为 `A` 的特征。其含义是线性泛函 `T` 是一个非平凡的代数同态，`T: A → C`。它具有性质 `T(v · w) = T(v) T(w)`，对于 `A` 中所有 `v` 和 `w`。`A` 上所有这些乘性线性泛函的集合在弱 * 拓扑中形成一个局部紧 Hausdorff 空间。此外，该集合是紧的，因为假设恒等元 `I` 在 `A` 中。紧 Hausdorff 空间 `Δ(A)` 称为特征空间。令 `C(Δ(A))` 为 `Δ` 中所有复值连续函数的代数。Gelfand 变换是 `G: A → C(Δ)`，其中 `v → G(v)`，`G(v)` 在 `C(Δ)` 中且定义为 `G(v) = v̂`![方程](img/F000242si14.png)，其中 `x̂(T) = T(v)`![方程](img/F000242si15.png)，对于 `Δ` 中所有 `T`。

在 `Δ` 中消失于无穷远的复值连续函数代数是 `C(Δ)` 的子代数，记为 `C0`。Gelfand 变换的像包含在 `C0` 中。GNS 构造在第 8.8 节中引入。它借助 Gelfand 公式推广到所有在 `C` 上的可交换 `C*` 代数 `A`。在这种情况下，`A` 与某个紧 Hausdorff 空间 `X` 的 `C0` * 同构。此外，Gelfand 变换 `G` 是 `A` 与 `C0` 之间的 * 同构。当 `C*` 代数中没有恒等元时，Hausdorff 空间只需局部紧。这是由 Banach-Alaoglu 定理的结果（Narici 和 Beckenstein, 2011）。Gelfand 变换是涉及绝对可积函数的众多变换方法的基础。以下是几个例子。

### 示例 9.8
考虑集合 `A`，它由实数线上的所有绝对可积函数组成。积分关于 Lebesgue 测度。该空间记为 `L¹(R)`。使用逐点加法和涉及卷积运算的乘法，`A` 成为没有恒等函数的 `C*` 代数。在任何情况下，它也称为群代数。卷积运算与使用有界矩阵定义的运算非常相似；然而，在当前情况下积分取代了求和符号。对于 `L¹(R)` 中的 `f` 和 `g`，乘法为 `f ⊛ g(t) = ∫[x = -∞]^∞ f(x) g(t - x) dx`。在这种情况下的 Gelfand 变换是傅里叶变换。对于 `L¹(R)` 中的 `f`，该变换产生一个复值函数 `F(ω)`，即 `F(ω) = ∫[x = -∞]^∞ f(x) e^(-i x ω) dx` 它是一致连续的并且具有 Riemann-Lebesgue 性质，即 `F(ω) → 0` 当 `|ω| → ∞`。这与 Gelfand 变换产生 `C0` 中的函数一致。也就是说，当自变量趋于正无穷或负无穷时趋于零的连续函数。

傅里叶变换及其性质的更深入处理在示例 19.10 中给出，在再生核希尔伯特空间的背景下。

### 示例 9.9
设 `A` 由非负实数线上的所有绝对可积函数组成。再次，积分关于 Lebesgue 测度。该空间记为 `L¹(R+)`。使用逐点加法和乘法为卷积运算，`A` 再次成为没有恒等函数的 `C*` 代数。该空间中两个函数的卷积为 `f ⊛ g(t) = ∫[x = 0]^∞ f(x) g(t - x) dx`。在这种情况下的 Gelfand 变换是涉及变量 `s` 的拉普拉斯变换。该标量是复值的，其实部大于或等于零。这里，`L(s) = ∫[t = 0]^∞ f(x) e^(-s t) dx`。结果是在绝对收敛区域内的解析函数。

## 参考文献
* Dixmier, 1981 Dixmier J. *冯·诺伊曼代数* North Holland Pub. Co 1981;.
* Jones, 2010 Jones VFR. *冯·诺伊曼代数* U. Ca. Berkeley 2010;.
* Narici and Beckenstein, 2011 Narici L, Beckenstein E. 978–1584888666 *拓扑向量空间* CRC Press 2011;.
* Nelson, 2017 Nelson B. *冯·诺伊曼代数* U. Ca. Berkeley 2017;.

# 第 10 章
## 纤维丛
### 摘要
本章开头描述了代数商空间的 multisorted algebra（MSA）描述。随后介绍了拓扑商空间的概念，并从传统以及 MSA 观点呈现。解释了流形的结构以及图册中图表的作用。图册包含许多图表，图表用于流形的局部表示。这些概念用于莫比乌斯带的构造。概述了该过程以及纤维丛截面的实现。复椭圆曲线的介绍构成了第 10.8 节的基础。在该节中，举例说明了群格、以及自同态和复乘法。如果以 MSA 的角度回顾附录 A3，则本节的材料最好理解。在准备本章最后几节提供的 Hopf 纤维丛之前，给出了四元数斜域的简要描述。最后三个部分专门讨论 Hopf 纤维丛：首先是一般描述，然后是一量子比特表示，最后是涉及 Hopf 纤维丛的二量子比特表示。

#### 关键词
商空间；同胚；图表；图册；纤维丛；莫比乌斯带；微分同胚；截面；复椭圆曲线；四元数

## 10.1 代数商空间的 MSA
在代数商空间的 MSA 描述中，存在四种类型；它们是 `VECT`、`SUBV`、`SCALAR` 和 `COSET`。通常，`SCALAR` 指代域，例如实数或复数以及四元数斜域。`VECT` 指代向量空间，`SUBV` 表示 `VECT` 内的固定子空间。最后，`COSET` 是商空间内所有向量的名称。实际上，`COSET` 中的向量 `v` 将由等价类组成并表示为 `[v]`。括号内的量 `v` 可视为陪集代表，将在后面更详细地描述。实际的签名集与描述向量空间和标量时完全相同。此外，向量空间的所有等式恒等式也必须成立。为了压缩记号，表示类型：
* `VECTOR` 用 `V` 表示
* `SCALAR` 用 `S` 表示
* `SUBV` 用 `N` 表示

利用表示算子名称的符号：
* `V-ADD` 用 `+` 表示
* `V-MINUS` 用 `−` 表示，在以下内容中，`−` 用作二元运算而不是写成 `+ (−)`。

如前几章所述的等价关系是一个 RST 关系。这里它在 `V` 上定义为说当 `v−w` 在 `V` 的子空间 `N` 中时 `v` 与 `w` 相关。子空间 `N` 是任意的且非空。该关系也可以如下描述：当 `v = w + n`，其中 `n` 在 `N` 中时，`v` 等价于 `w`。它用等价符号表示，`v~w`。这促使了陪集的记号，`[v] = {v + n where n is in N}`，并且在这种情况下，由上可知 `[v] = [w]`。而且，`[0] = {n is in N}`。因此，`N` 中的所有向量都像 `ZERO` 一样起作用。商空间 `V/N` 定义为由 `V` 上的关系 `~` 引起的全部等价类的集合。它也是由全部陪集组成的空间，即 `V/~`。当加法和标量乘法按下面给出定义时，商空间本身就是一个向量空间（Halmos, 1974）。然而，首先通过让以下内容进行记号滥用：
* 对于 `COSET`，使用 `[v]`、`[w]`。
* 对于 `SCALAR`，使用 `S` 中的 `a`。




*   对于 `V-ADD`，使用 `+`，用于 `V` 中的元素或向量。
*   对于 `V` 中的 `S-MULT`，使用 `·`；此乘法涉及 `S` 中的标量和 `V` 中的元素。
*   对于 `COSET` 中的元素，`V-ADD` 使用 `+′`。
*   对于 `S` 中的标量和 `COSET` 中的元素，`S-MULT` 使用 `·′`。

接下来提供了两个闭包运算。另请参阅 图 10.1A 中的多元图。这里出现了全部四个排序；然而，对于涉及 `V`、`N`、`COSET` 和 `S` 的 `V-ADD` 和 `S-MULT`，仅显示了一些多元箭头。子空间 `N` 应位于 `V` 的内部，但为了清晰地说明运算名称，它被单独描绘。在任何情况下，闭包要求如下：
1.  齐次：`a·′ [v]=[a·v]`。
2.  线性：`[v] +′ [w]=[v + w]`。

![图 10.1 一般和特定的代数商空间。(A) 商空间中的映射，(B) 商空间，平面中的直线。](img/F000047f10-01-9780443136979.jpg)

图 10.1 一般和特定的代数商空间。(A) 商空间中的映射，(B) 商空间，平面中的直线。

在此图中，描绘了当子空间 `N` 中的两个向量相加时，结果是商空间中的零等价类。因此这两个向量映射到 `COSET` 中的 `[0]`。当来自 `N` 的一个向量与来自 `V` 的另一个向量相加时，结果是 `COSET` 商空间中的一个陪集。该图还说明了一个标量 `a`；将 `COSET` 中的元素 `[v]` 相乘，即 `a·′ [v]`，乘积在 `COSET` 中。此外，结果由上述准则 (1) 给出 `a·′ [v]=[a·v]`。该图中还可以看到，商空间中的两个陪集，例如 `[v]` 和 `[w]`，被相加；和仍然是一个陪集。和也可以通过参考上述准则编号 (2) 找到 `[v] +′ [w]=[v + w]`。

### 示例 10.1

使用载体集合 `R²` 作为 `VECTOR` 的排序，并使用 `R` 作为 `SCALAR` 的排序。此外，让子空间排序 `SUBV` 的载体集合由 x、y 平面中 45 度线上的向量组成。在 图 10.1B 中，`SUBV`、子空间 `N` 以及一个典型的陪集的插图，该陪集由一条平行线组成，位于 `N` 的右侧。该线上的两个向量为 `v=(1 0)′` 和 `w=(0 –1)′`。该表达式中的撇号表示矩阵转置，因此这两个向量是列向量。在任何情况下，这两个向量之间的差是一个位于 `N` 中的向量。该向量在图中示出，差向量位于 `(1 1)′`。在这种情况下，陪集都是仿射空间，即平行于 `N` 的直线。

## 10.2 拓扑商空间

在拓扑中，商空间也通过使用等价类来定义，如上一节所述的代数。拓扑商空间中使用的集合 `X` 可以是任意集合；它不必是向量空间。拓扑 `Tx` 由 `X` 的子集的集合组成，称为开集。它们是这样的，空集和整个集合 `X` 都在拓扑中，以及有限交集和开集的任意并集。重述要求，`Tx` 确定 `X` 上拓扑中开的集合。它是这样的：
1.  `X` 和空集 `ϕ`![方程](img/F000047si1.png) 都在 `Tx` 中。
2.  `Tx` 中任意多个集合的并集必须在 `Tx` 中。
3.  `Tx` 中任意集合的有限交集也必须在 `TX` 中。

`Tx` 的量称为 `X` 上的拓扑，拓扑空间表示为 (`X`, `Tx`)（Munkres, 1999）。从 MSA 的角度来看，`Tx` 可以类似地看作 MSA 描述的 σ 域，如附录 A.2 所示。也就是说，在本例中，存在两个排序，`POWX` 和 `OPEN`。作为具体例子，`POWX` 是幂集 `2^(X)` 的名称。此外，`OPEN` 是拓扑中所有开集的符号。最后，包含一元运算 `Tx` 的单个签名集合完成了 MSA 方法中拓扑空间的高层视图。这里，`Tx: 2^(X)→OPEN`，因此在这种情况下 `Tx` 是一个部分恒等函数。它选择 `X` 的哪些子集是开的，始终遵守上述约束方程 (1) – (3)。

商空间 (`Y`, `Ty`) 是通过等价关系以及商拓扑 `Ty` 从另一个拓扑空间 (`X`, `Tx`) 获得的拓扑空间。后者拓扑是使满典范投影映射 `p: X→Y` 连续的最细拓扑。因此，子集 `U` 在 `Y` 中开当且仅当 `p^(−1) (U)` 在 `X` 中开。这定义了 `Y` 上的拓扑 `Ty`。它并不说明 `p` 是开映射，即如果 `V` 在 `Tx` 中，是 `X` 中的开集，则 `p(V)` 不一定是 `Y` 中的开集。使 `p` 连续的过程与纤维丛中使用的过程相反。在后一种情况下，它是最粗或初始拓扑。这里它是最终拓扑。再次，商映射 `p: X → Y` 始终为：
1.  满射。
2.  连续。
3.  对于 `Y` 中任意集合 `A`，如果 `p^(−1)(A)` 在 `X` 中开，则 `A` 必须在 `Y` 中开。

编号 (3) 中的准则对于典范映射始终成立。利用商拓扑，只要 `X` 中的开集 `A` 是等价类逆的并集，则 `A` 被称为饱和的。等价地，`A` 相对于 `p` 是饱和的，这意味着 `p^(−1) (U [.] )=A`。在这种情况下，`p(A)` 在 `Y` 中开，因此对于这种情况 `p` 是开映射，但它通常不是开映射。

### 示例 10.2

使用 `X=R` 并采用通常拓扑。设 `R` 中的点 `r` 和 `s` 相关，`r~s` 当且仅当差 `r-s` 为整数。因此，商空间 `Y=R/~` 将与单位圆同胚。在这种情况下，商空间 `Y=R/~={{0+/− n, for n in Z}, {t+/− n, for n in Z}, such that t in (0, 1)}}={[0], [t], such that t in (0, 1)}`。请参阅 图 10.2。这里，映射 `p` 将实数 `r` 映射到等价类 `[r]`。在商空间 `Y` 中，开集 `A` 在该图中示出。该图中还显示了逆运算 `p^(−1) (A)` 映射到 `R` 中的开集。这些无限多个集合是大小相同且不相交的开区间，相隔一个整数。

![图 10.2 实数商空间的同胚。](img/F000047f10-02-9780443136979.jpg)

图 10.2 实数商空间的同胚。

设 `f′: R→S¹`，其中 `S¹` 是单位圆，并使用参数化 `f′ (t)=(sin(2*π*t), cos(2*π*t))`。该函数是连续的，而且它还是一个开映射。后一个条件最容易从复分析中看出。非常数的全纯映射是开映射，并且当限制在实轴上时，它是开映射。此外，该映射是局部同胚，始终是开映射（Rudin, 1966）。定义 `f: Y→S¹`，由 `f([t])=f′ (t)` 给出。函数 `f′` 在所有整数处始终给出相同的值，从而表明 `f` 是良定义的。在图中，注意 `f′ (.)=f (p(.))`；该方程稍后会用到。



函数 `f` 将被证明是一个同胚。它是双射的，因为它是满射且一一对应的。满射性可通过选取 `S¹` 中的任意点得到；其形式为 `(sin(2*π*t′), cos(2*π*t′))`。这里使用的 `t′` 的值是 `R` 中的点 `t′`。然而，`Y` 中的 `[t′]` 对应于 `R` 中所有的点 `t′ + n`，其中 `n` 在 `Z` 中，这表明 `f` 是满射的。对于一一对应，若 `[t[1]]` 不等于 `[t[2]]`，则 `t[1]` 不等于 `t[2] + n`，其中 `n` 为整数。因此，`sin(2*π*t[1])` 不等于 `sin(2*π*(t[2] + n))`=`sin(2*π*t[2])`；相应地，`f([t[1]])` 不等于 `f([t[2]])`。接下来，由于 `p` 是商映射，故它是连续的。此外，`f′` 是连续的，因此对开集 `U`，`f′^(−1)(U)` 是开集。由于 `f′^(−1)`=`(f(p))^(−1)`=`p^(−1)(f^(−1))`，将其应用于 `S¹` 中的开集 `U`，`f′^(−1)(U)`=`p^(−1)(f^(−1))(U))` 是开集，这意味着 `f^(−1)(U)` 是开集，因为 `U` 在 `Y` 中是开的当且仅当 `p^(−1)(U)` 在 `X` 中是开的；这表明 `f` 是连续的。对于同胚，唯一剩下的要证明的是 `f` 是开映射。然而，这确实成立，因为 `f′` 是开映射。由于 `f(.)`=`f′(p^(−1)(.))`，将此映射应用于 `Y` 中的开集 `U`。则 `f(U)`=`f′(p^(−1)(U))`，这是开映射，因为 `p` 是连续的，且 `f′` 是开映射。因此，`Y` 与 `S¹` 的同胚关系得以建立。

### Example 10.3

考虑单位区间 `X`=`[0, 1]` 带有由实线诱导的子集拓扑 `Tx`。在 `X` 上使用等价关系 `0~1`。这意味着 `0` 和 `1` 被粘合在一起。设 `q`: `X`→`[0, 1]/~`=`Y` 为典范投影映射。这里，`[0, 1]/~` ={{`0, 1`}, `{t`}}，且 `{t}` 对于 `(0, 1)` 中的每个 `t` 都是单点集。相应地，对于 `(0, 1)` 中的任意 `t`，`q(t)`=`[t]`，但对于 `0` 或 `1`，`q(0)`=`q(1)`=`[0]`=`[1]`。采用商拓扑；这里，`U` 在 `Y` 中是开的当且仅当 `q^(−1)(U)` 在 `X` 中是开的。由于 `0` 和 `1` 相同，似乎该结构像一个圆。事实上，`Y` 也与 `S¹` 同胚。为此，首先设 `f′`: `X`→`S¹`，其中 `f′(t)`=`(sin(2*π*t), cos(2*π*t))`；它是连续映射。定义 `f`，其中 `f([t])`=`f′(t)`，对 `t` 在 `(0, 1)` 中，且 `f([0])`=`f′(0)`=`f′(1)`。参见 图 10.3。

![图 10.3 涉及圆周区间的同胚。](img/F000047f10-03-9780443136979.jpg)

图 10.3 涉及圆周区间的同胚。

为了证明 `f`: `Y`→`S¹` 是满射，取 `S¹` 中的一个特定点，设 `c`=`(sin(2*π*t′), cos(2*π*t′))`，则 `X` 中的点 `t′` 满足 `f′(t′)`=`c`。这意味着 `Y` 中的 `[t′]` 满足 `f([t′])`=`c`。为了看出 `f` 是 1–1，若 `[t[1]]` 不等于 `[t[2]]`，则 `t[1]` 与 `t[2]` 不同，且 `sin(2*π*t[1])` 不等于 `sin(2*π*t[2])`，因为它们相等仅当 `t[1]` 与 `t[2]` 相差一个整数，即在 `[0, 1]` 的端点处。由于它们在等价类 `Y` 中相同，故 1–1 得证。`f` 的同胚性可通过使用拓扑学中的一个定理得到 (Dugundji, 1975)。这里，从紧空间 `Y` 到 Hausdorff 空间的连续双射函数 `f` 是一个同胚。请注意 `S¹` 是 Hausdorff 空间，因为 `R²` 是 Hausdorff 空间。商空间 `Y`=`R/~` 是紧的。这可以看出，因为它是紧集的连续像的满射，即 `X` 是紧的，且同胚已得到证明。

### Example 10.4

映射 `q`: `(0, 1]`→`S¹`，其中 `q(t)`=`(sin(2*π*t), cos(2*π*t))` 不是同胚，因为 `q^(−1)` 不是连续的。为了证明这一点，考虑 `R²` 中点 `(0, 1)` 与 `(sin(2*π*t), cos(2*π*t))` 之间的距离。它是 `[sin(2*π*t)² + (1 − cos(2*π*t))²]` 的平方根 =`2 (1 −cos(2*π*t))`。因此对于 `2 (1 − cos(2*π*t))` 小于 delta，当 `t` 接近零时，这应意味着 `|t−1|` 小于 epsilon，但 `t` 与 1 之间存在间隙。更简洁地，要证明它们不同胚，可利用 `S¹` 是紧的，但 `(0, 1]` 在 `R` 中不是紧的这一事实。

### Example 10.5

再次考虑具有通常拓扑的实线。这次，考虑 `Y`=`R/~`，其中对于 `Z` 中的所有 `x` 和 `y`，`x~y` 表示 `x=y`。然而，对于所有非整数，即对于所有不在 `Z` 中的 `x`，`x~x`。这些点是单点集。所得商空间在 图 10.4 中示出，同时给出商映射 `q`。所得结构是非第一可数空间的一个极佳例子。点 `[0]`，它代表所有整数，没有可数基。设 `{Un}`，`n` 在 `N` 中，为 `[0]` 的邻域族。可以注意到下面定义的开集 `U` 不包含任何 `Un`。该结果可通过找到包含单个整数 `n`=`0`、`+/− 1`、`2`、… 的开区间 `U′n` 来看到，其中 `Un′` 是 `q^(−1)(Un)` 的真非空子集。令 `U`=`q`（所有 `Un′` 的并），则没有 `Un` 能在 `U` 中，因为如果有，则 `Un′` 不能是 `q^(−1)(Un)` 的真子集。

![图 10.4 非第一可数空间。](img/F000047f10-04-9780443136979.jpg)

图 10.4 非第一可数空间。

## 10.3 Basic topological and manifold concepts

流形 `M` 总是 Hausdorff 型特殊拓扑空间。这些空间具有任意两个不同点必须各自包含在彼此不相交的不同开集中的性质。此外，Hausdorff 空间必须处处局部同胚于 `R^(*n*)`。因此，这意味着它在局部看起来像欧几里得空间，即使整体结构可能高度非线性。同胚映射是双连续、一一对应且保持结构的满射映射。最后，大多数情况下，`M` 是第二可数的，这意味着存在一个可数基，它是开集的可数并集。从此以后假设具有此特征。第二可数蕴含第一可数；后者拓扑空间只需要具有局部可数基。非第一可数空间的例证见于 图 10.4。此例是病态的；此外，欧几里得空间既是 Hausdorff 空间也是第二可数空间。

流形 `M` 总是与一个图册 `A` 相关联。这是一组称为图的开集，用 `Ua` 表示。这些图描述流形内的区域。此外，它们的并集覆盖 `M`。因此在图册中流形的每一点必须在某个图内具有坐标。伴随图册中的这些图始终存在函数 `fa`。这些函数满足 `fa`: `M`→`R^(*n*)`，其中 `fa` 和 `fa^(−1)` 是同胚。图称为坐标域，`fa` 称为坐标映射。通常当 `fbfa^(−1)` 具有 `k` 个连续导数，`k`=`1, 2, …` 时，图册连同相应的流形称为光滑的。据此，它们属于 `C^(*k*)`。更常见的是，光滑意味着无限可微。在图内，各种群结构将被视为具有局部坐标的 `n` 维向量空间。对于局部坐标系，恒等式在后续章节中将发挥特殊作用。通常，整个流形的全局坐标系是不可行的。例如，使用球面，只能展示局部表示。



## 10.3 图表、图集与拓扑性质

两个图表 `Ua` 和 `Ub`，具有非空交集，位于流形 `M` 中。它们位于固定的图集中，并使用过渡函数 `T` 进行比较。参见 图 10.5。为了使图集可用，重叠区域必须不会相差太大。过渡函数满足如果 `fa`: `Ua`→`R`^(`n`)![Equation](img/F000047si2.png) 且同样 `fb`: `Ub`→`R`^(`n`)，则 `Tab`=`fb` `fa`^(−1)，即 `Tab`: `fa` (`Ua` intersect `Ub`)→`fb` (`Ua` intersect `Ub`)。注意 `T` 也是一个同胚，因为 `fa` 和 `fb` 都是同胚。流形可以有多个图集。最大图集是指不是另一个图集的真子集的图集。对于 `M` 上的每个光滑图集 `A`，在 `M` 上存在唯一的极大图集。流形上的微分结构，即全局定义的微分结构，是一个极大图集（Lee, 2006）。

![图 10.5 具有两个图表和过渡映射的流形。](img/F000047f10-05-9780443136979.jpg)

图 10.5 具有两个图表和过渡映射的流形。

连通拓扑空间 `T` 不能是两个或多个非空开集的不交并。当空间不连通时，在这些情况下，空间内存在连通的子集。它们称为连通分支。连通分支是拓扑空间 `T` 的最大连通子集。另一个连通性概念是道路连通。道路连通空间 `T` 的含义是存在连续函数 `f`: \0, 1|→`T`，使得对于 `T` 中的 `x`、`y`，有 `f(0)`=`x`、`f(1)`=`y`。道路连通蕴含连通。

拓扑空间在每个开覆盖都有有限子覆盖时是紧致的。极大紧子群是最大的紧子群。在 `R`^(`n`) 中，紧致性可以更简单地表述：这里，每个闭且有界的子集都是紧致的；这是 Heine-Borel 定理。此外，紧致流形具有特殊的重要性，因为存在仅包含有限个图表的图集。这是因为在紧致群中，每个开覆盖都有有限子覆盖，而图表是开集。

## 10.4 流形上的纤维丛

纤维丛通常由连续函数粘合在一起的流形组成。这些流形始终包括底空间 `B`，和纤维 `F`，纤维直观上类似于任意长度的细丝或棍棒。它们共同构成总空间 `E`。例如，如果 `B` 是圆 `S¹`，则放置火柴棍或区间 (0,1) 的线段，使其垂直于圆并直立环绕。这表示纤维 `F`，相应地产生一个圆柱体 `E`。它看起来像一个圆柱体或罐子，其壁构成纤维，底部为底空间。这里，总空间 `E`=`B` x `F`。使用类似技术会得到不同的结构，称为莫比乌斯带。从相同的底空间 `B`，即圆开始。再次使用棍棒或区间 (0,1) 环绕底圆来创建纤维 `F`。然而，现在在将线段或棍棒放置在底空间上时，采用 180 度的逐渐扭转。这在 [图 10.6 中有所说明。扭转并非在圆的某一点进行；而是均匀分布在整个圆上。然而，所提供的图表并不能很好地说明这一点。扭转可以看作是局部图表的扭转。圆柱体和莫比乌斯带这两种结构是相似的。它们在构造中使用相同的底空间和大致相同的纤维量。但由于参数化，最终结果截然不同。

![图 10.6 莫比乌斯棍棒图。](img/F000047f10-06-9780443136979.jpg)

图 10.6 莫比乌斯棍棒图。

莫比乌斯结构在局部是乘积空间，但在整体上不是乘积空间，而圆柱体是。直观上，莫比乌斯丛参数化的复杂性可通过水平传输看出。图 10.7 中提供的插图有助于描述这一现象。假设底空间是水平单位圆，并且初始时垂直纤维上的点 `u` 位于距底空间 1/3 的高度。这里假设纤维长 1 个单位，且水平角度以逆时针度数测量。`u` 的初始坐标为 (0, 1/3)。尽管纤维长度相同，但随着角度变化，由于翻转，它们不再保持垂直。然而，所有测量都是沿纤维从底空间开始进行的。如果点 `u` 通过 360 度的角度变化被传输，则点 `u` 现在位于高度 2/3 处并位于点 `w`。点 `u` 移动的轨迹在图中有所说明。

![图 10.7 莫比乌斯带。](img/F000047f10-07-9780443136979.jpg)

图 10.7 莫比乌斯带。

当莫比乌斯带的侧面可在正面视图中观察到时，使用带箭头的实线。带箭头的虚线用于描绘隐藏视图。再旋转 360 度，点 `u` 会回到其原始位置。等价地，设 `w` 的初始坐标为 (0, 2/3)，并将角度限制在零到 360 度之间。当 `w` 被传输时，其轨迹再次给出。这次在图中用实点表示可观察的轨迹，用非实心圆表示隐藏的轨迹来描绘。参见 图 10.7。请注意，点 `u` 和 `w` 的轨迹必须在某一点相交。因此，参数化不是全局的。路径交叉处的参数化没有明确定义。

圆柱体和莫比乌斯纤维丛之间最大的差异之一是构造中使用的结构群。这些群内的过渡函数是光滑的，并决定纤维如何粘合在一起。这些函数用于在需要时平滑地改变参数化。对于莫比乌斯带，过渡函数用于区分两种可能的参数化。直观上，参数的变化发生在路径相交的点。总之，这些代数群表征了纤维丛，并在后续章节中进一步描述。

更详细地说，纤维丛由三个集合组成：总空间 `E`、底空间 `B` 和纤维 `F`。如先前在简单情况下所见，`E`=`B` x `F`，即 `E` 只是乘积空间。在这种情况下，`B` 称为平凡丛。通常存在局部连续满射 `p`: `E`→`B`。该映射 `p` 也是一个开映射，因为乘积的投影是开映射。此外，该映射也被称为丛的浸没（Phillips, 1967）。在更复杂的空间中，该映射较为复杂；然而，在局部它仍然像投影一样作用，但通常不是 1–1。类似于短正合列，纤维丛由以下描述：

`F`→`E`–^(`p`)→`B`

![Equation](img/F000047si3.png)



对于 `B` 中任意点 `x`，`p^(−1)(x)` 必须与纤维 `F` 微分同胚。一般而言，局部平凡化对 `E` 中的任意 `u` 发生；这始于投影 `p(u)=x`，其中 `u` 是位于 `x` 上方纤维的元素。纤维丛是一组覆盖基流形的平凡化。可以利用映射 `h(u)=(x, f)`，其中对于 `B` 中任意开集 `U`，`h: p^(−1)(U)→U x F`。设 `h′` 为另一个平凡化：`h′(u)=(x, f′)`，其中 `h′: p^(−1)(U)→U x F`。当这两个平凡化重叠时，`h` 和 `h′` 与基于 `x` 的转移函数相关。此实例在 图 10.9 中有所说明。对于重叠部分，纤维丛的结构群 `G` 具有元素 `g`，取决于 `x`，使得 `f′=g f`。这是 `G` 对 `F` 的光滑左作用。转移函数将纤维映射到纤维中并且是微分同胚；它们属于结构群。该群是 `F` 上所有微分同胚的子集。回想一下，平凡纤维丛是纤维丛，其中处处 `E=B x F`。在这种情况下只需要一个丛图。

![图 10.9 线丛中的平凡化。](img/F000047f10-09-9780443136979.jpg)

图 10.9 线丛中的平凡化。

## 10.5 纤维丛中的截面

纤维丛的截面是从 `B` 到 `E` 的一种恒等型映射。截面包含位于基 `B` 中点 `x` 上方的 `F` 中的点，投影 `p` 应用于截面中的点时恢复原始基点 `x`。

### 例 10.6

参见上文给出的莫比乌斯纤维丛，特别是 图 10.7。`u` 在 `0, 2π)` 中的传输中的整个连续路径是一个截面。在这种情况下，假设路径中没有间隙，使得路径中每一点的投影恢复整个基 `S¹`。在图中，起始位置显示在条带的远端，而终点在条带背面顶部以极限的方式逼近。

### 例 10.7

与莫比乌斯纤维丛相比，这是一个更简单的平凡纤维丛的例子。将 `R²` 视为总空间 `E`。设基 `B` 仅为直线 `R¹`，即 `x` 轴。还设纤维为 `F=R¹`，其放置正交于原始直线 `B`，彼此平行，并构成一个平面。这是一个平凡丛，即 `E=B x F`。直观上将基视为 `x` 轴，纤维是沿 `y` 轴且全部平行的线条。此外，如果 `g: B→F`，其中 `g(x)=x³`，则 `g` 是一个截面。因此，投影映射 `p(g)(x)` 给出 `B` 上的所有点。这在 [图 10.8 中有所说明。

![图 10.8 纤维丛中的截面。](img/F000047f10-08-9780443136979.jpg)

图 10.8 纤维丛中的截面。

## 10.6 线丛和向量丛

一般而言，丛由覆盖纤维丛中基流形的平凡化集合组成。平凡化利用转移函数创建丛。线丛或秩一的向量丛具有一维复或实向量空间的纤维。此外，结构群在线性空间上线性作用。严格来说，它们是通过令 `L` 和 `B` 均为光滑流形且具有光滑满射投影 `p: L→B` 来定义的。对于 `B` 中的每个 `x`，`L` 在 `x` 上的纤维 `F`，即 `p^(−1)({x})`，是一个一维复向量空间。如前所述，对每个 `x` 存在一个平凡化。存在 `x` 的一个开邻域 `U`，使得微分同胚 `h: p^(−1)(U)→U x C`。此外，对于投影 `p1: U x C→U` 和 `p2: U x C→C`，首先令 `p(u)=p1(h(u))` 对所有 `U` 中的 `x` 成立。在这种情况下，`p2(h(u))` 是 `p^(−1)({x})` 与 `C` 的向量空间同构。图 10.9 说明了这些概念中的一些。

向量丛具有实或复 `n` 维向量空间的纤维。此外，结构群在线性空间上线性作用。转移函数也在纤维上进行 `n` 维运算。这些函数属于 `GL(n, R)` 或 `GL(n, C)` 中的子群；这两个群都是一般线性群，并在下一章中详细描述。

## 10.7 解析向量丛

设 `B` 为 `C` 上的复流形。秩为 `n` 的解析向量丛是全纯映射 `p: E→B`，使得对于 `B` 中任意点 `x`，原像 `Ex=p^(−1)(x)` 具有 `n` 维复向量空间结构。这里，`Ex` 是纤维。此外，映射 `p` 是局部平凡的。这意味着对于基 `B` 中任意点 `x`，存在一个开邻域 `Uj`，其中包含 `x` 以及一个双全纯映射 `fj: p^(−1)(Uj)→Uj x C^(n)`，其中投影 `p1: Uj x C^(n)→Uj=p(p^(−1)(Uj))`。此外，`fj` 是从 `Ex` 到 `{x} x C^(n)` 的同构映射，对 `Uj` 中每个 `x` 成立，也称为 `E` 在 `U` 上的平凡化。如前所述，一般线性群参与其中。对于任意一对平凡化 `fi` 和 `gj`，映射 `hij: Ui intersects Vj→GL(n, C)`，其中 `hij(x)=fi(gj^(−1))`，但 `gj` 的定义域限制为 `{x} x C^(n)`。该映射是全纯的，称为相对于平凡化 `fi` 和 `gj` 的 `E` 的转移函数。转移函数满足恒等式：

1. 逆：`hij(x) hji(x)=I` 对所有 `x` 在 `Ui intersect Uj` 中。

2. 上循环条件：`hij(x) hjk(x) hki(x)=I` 对所有 `x` 在 `Ui`、`Uj` 和 `Uk` 的交集中。

向量丛 `E` 可以使用转移函数 `hij: Ui intersect Uj→GL(n, C)` 创建，其中 `{Uk}` 是 `B` 的一个开覆盖。这采用了使用所有 `I` 的 `Ui X C^(n)` 的粘合构造，从而得到 `E=the disjoint union of (Ui x C^(n))/~`。这里，`~` 指等价类 `(x, v)~(x, hij(x)(v))`，对所有 `x` 在 `Ui intersect Uj` 中且 `v` 在 `C^(n)` 中。

### 例 10.8

秩为 `n` 的平凡解析向量丛使用投影映射 `p1: B x C^(n)→B`。对于 `B` 上的向量丛 `E`，设 `hij` 为转移函数，`{Uj}` 为 `B` 的一个开覆盖。对偶丛为 `E*`，由转移函数 `gij(x)=hij^(−1)(x)` 定义，对所有 `x` 在 `Ui intersect Uj` 中。对于 `B` 中的开集 `U`，`U` 上的全纯截面 `s` 为 `s: U→E`，且 `p(s(U))=U`。`E` 的整体截面是 `U=B` 的全纯截面。在这种情况下，所有此类整体截面形成一个向量空间，记为 `Ho(B, E)` (Chern, 1979)。

## 10.8 `C` 上的椭圆曲线

椭圆曲线在多个不同的域上定义。这些载体集合包括实数、有理数和伽罗瓦域，以及当前应用的复域。附录 A3 提供了关于涉及实域的椭圆曲线的加法群结构的 MSA 的介绍。后续章节将利用伽罗瓦域上的椭圆曲线用于加密目的。

对于 `C` 上的椭圆曲线 `E`，总存在一个格 `L`，是 `C` 的一个子集，在缩放或相似变换下是唯一的。相似变换保持关于中心的伸缩和收缩。对于每个格，都存在一个椭圆曲线。更具体地说，椭圆曲线是 `C` 对格的商空间。反之，`C` 对格的任何商空间都是椭圆曲线。此外，存在一个复分析和同构 `g`，`g: C/L→E` (Silverman, 2009)。这是复平面上椭圆曲线上的点集。它是李群的同构。均匀化定理提供了 `C` 上的椭圆曲线与格之间的联系。

### 例 10.9

椭圆曲线是三次曲线 `y²=x³ + a x + b`，其中 `a` 和 `b` 现在是复数。此外，`4 a³ + 27 b²` 不为零，使得曲线光滑。设 `E={(x, y), 其中 x 和 y 在 C 中且是椭圆曲线上的点}` 并上无穷远点 `∞`。在射影空间中，`∞=(0: 1: 0)` (Coxeter, 1989)。



## 格与同源映射
一个格 `L` 是 `C` 的离散阿贝尔加性群。它由略呈水平的平行线与略呈垂直的平行线相交的点组成。参见 图 10.10。

![图 10.10 两种格类型。 (A) 正方形图案格， (B) 更一般的格。](img/F000047f10-10-9780443136979.jpg)

图 10.10 两种格类型。 (A) 正方形图案格， (B) 更一般的格。

### 示例 10.10
最简单的格是 `L = Z[i]`，如图 图 10.10A 所示。它被定义为 `L = {v = n + mi, such that n and m are in Z}`。由此可知，在通常的复数域运算下，这是一个加性阿贝尔群。更典型的格如图 图 10.10B 所示。一般而言，格中的平行四边形都具有相同的维度和等间距。

同源映射 `h` 是椭圆曲线 `E1` 和 `E2` 的非零全纯群同态，使得 `h: E1 → E2`，其中 `g(0) = 0`。当 `E1 = E2 = E` 时，该同源映射称为从 `E` 到自身的自同态，并简写为 `End(E)`。 `E` 上的自同态环是 `E` 上的自同态，其中加法由群结构逐点定义，而乘法定义为函数复合。这表示为 `End(E)`。深入的论述可在 Silverman (1994) 中找到。

### 示例 10.11
如果对 `E` 中每一个 `p`，都有 `g(p) = n p`，其中 `n` 是 `Z` 中的某个点，则这是在 `E` 上的一个自同态。这称为乘以 `n` 映射。考虑椭圆曲线 `E[1]`，`y² = x³ − x`，以及椭圆曲线 `E[2]`：`y² = x³ + 4 x` 然后，映射 `g: E[1] → E[2]`，其中 `(x, y) → (y²/x², − y (1 + x²)/x²)`，以及 `h: E[2] → E[1]`，其中 `(x, y) → (y²/(4 x²), − y (4 + x²)/(8 x²))`。接下来，`g` 下的坐标像将被代入椭圆曲线 `E[2]`。即，`[−y (1 + x²)/x²]² = [y²/x²]³ + 4 [y²/x²]`，该量也可以写成如下形式：`[y² (1 + 2 x² + x⁴) x²] = y⁶ + 4 y² x⁴`，当 `x` 不为零时。再次写出此式得到结果：`y⁴ = x⁶ – 2 x⁴ + x² = (x³ − x)²`。一个分支给出椭圆曲线 `E[1]`。如果将 `h` 的像代入椭圆曲线 `E[1]`，也会得到类似的结论。所有这些的核心在于 `h(g)(.)` 是从 `E[1]` 到自身的乘以二映射。同样，`g(h)(.)` 是从 `E[2]` 到自身的乘以二映射（Lin, 2021）。

### 示例 10.12
映射 `z mod(Z[i] → i z mod(Z[i])` 是 `y² = x³ − x` 的一个自同态。由于 `g: (x, y) → (−x, i y)`，将其代入曲线得到 `(i y)² = (−x)³ − (−x)`，于是 `y² = x³ – x`，为同一曲线。请注意 `g⁴` 是恒等映射。然而，`g` 不是乘以 `n` 的映射。因为椭圆曲线中点 `(x, y)` 的顺序以及 `g` 的作用，它是 `(−x, i y)`，两者不同。为了看出 `g⁴` 给出恒等映射，反复四次应用替换 `(x, y) → (−x, i y)`。因此，`g⁴: (x, y) → (−x, i y) → (x, −y) → (−x, −i y) → (x, y)`。

椭圆曲线 `E` 具有复乘法 (CM)，这意味着 `Z` 并不是 `End(E)` 中唯一的自同态。前一个例子就是 CM 的说明。当 `E` 不具有 CM 时，则自同态是一个同构，即 `g: E → E`，`g(p) = n p`，其中 `n` 是 `Z` 中的固定值。

## 10.9 四元数
四元数可以用多种方式描述。它们构成实数域上的四维向量空间。此外，四元数构成一个斜域或除法代数。它也是实数域上的赋范、含幺、非交换结合代数。与复数系统类似，存在一种类似作用的共轭运算。事实上，对于四元数 `q = a + b i + c j + d k`，`q` 的共轭记为 `q*`，且等于 `a − b i − c j − d k`。此外，共轭是一个对合，即 `(q*)* = q` 且对于两个四元数 `(p q)* = q* p*`。

当 `|p| = 1` 时，四元数 `p` 是幺元。最重要的幺元四元数是单个单位四元数：`1`、`i`、`j` 和 `k`。`V-ONE = 1`。其余满足乘法恒等式：`i j = k`、`j k = i`、`k i = j`、`j i = −k`、`k j = −i`、`i k = −j`、`i i = −1`、`j j = −1`，以及 `k k = −1`。与复数域中的共轭不同，四元数的共轭可以利用 MSA 中为域给出的定义运算以及等式恒等式来执行。在这种情况下，被共轭的量 `q` 等于所有单个幺元四元数所涉及的和的负二分之一。这些幺元四元数在两侧乘以 `q`，得到公式 `q* = −(1/2) [1 q 1 + i q i + j q j + k q k]`。

### 示例 10.13
给定四元数 `q = 2 − j + 4 k`。共轭四元数为 `q* = 2 + j − 4 k`。然而，利用斜域规范内的运算，共轭也可以再次求得。因此，在一个冗长的计算中，`q* = −(1/2) [(2 − j + 4 k) + i (2 − j + 4 k) i + j (2 − j + 4 k) j + k (2 − j + 4 k) k]`。现在乘以左侧的单个四元数，`q* = −(1/2) [(2 − j + 4 k) + (2 i − k − 4 j) i + (2 j + 1 + 4 i) j + (2 k + i − 4) k]`。接下来乘以右侧的单个四元数，`q* = −(1/2) [(2 − j + 4 k) + (−2 − j + 4 k) + (−2 + j + 4 k) + (−2 − j − 4 k)]`。最后，将所有内容相加得到 `q* = −(1/2) [−4 – 2 j + 8 k] = 2 + j − 4 k`。

`p` 的范数为 `‖p‖`；它通常写成 `|p|`，且其平方等于 `a² + b² + c² + d²`。作为一个除法代数，每个非零元素在左边或右边都有逆元。因此，对于非零的 `p`，有 `p q^(−1)` 或 `q^(−1) p = 1`，其中 `q^(−1) = q* / ‖q‖² = (a − b i − c j − d k) / (a² + b² + c² + d²)`。

将会看到四元数在 3 球面上具有群结构，从而与特殊酉群 `SU(2)` 同构，以及与特殊正交群 `SO(3)` 相似。这些群先前已在布洛赫球的联系中提到。单位四元数与由行列式为一的酉矩阵组成的特殊酉群同构。整数或半整数四元数也用于描述正多面体的对称性。

每个四元数 `p` 都可以写成实部 `p0` 和三维向量部 `v`。这里，`v = b i + c j + d k`。一个单位四元数可以写成 `p = cos(t) + v sin(t)`，其中 `|v| = 1` 且 `t` 在 `[0, 2 * π)` 中。与复数域情况类似，`p` 的标量部为 `(1/2)(p + p*)` 而 `p` 的向量部为 `(1/2)(p − p*)`。设 `q = q0 + w`，其中 `w` 是向量部。那么两个四元数 `p = p0 + v` 与 `q` 的乘积等于 `(p0 q0 − <v, w>) + (p0 w + q0 v + v x w)`。这里，第一组括号是标量值，其中 `< v, w >` 是 `R³` 中的通常点积。第二组括号包含乘积 `p q` 的向量部。量 `v x w` 是 `R³` 中的叉积。四元数 `q` 的最终表示涉及复数 `c[1]` 和 `c[2]`。写四元数 `q = c[1] + c[2] j`，其中 `c[1] = a + b i` 且 `c[2] = c + d i`，则 `q = a + b i + c j + d k` 如前所述。

### 示例 10.14
四元数 `Q` 作为代数等，可以构成一个李代数 `LQ`，其中利用李括号。即，对 `Q` 中的 `p, q` 使用交换子：`[p q − q p]`。特别地，导子的李代数 `D` 是李代数 `R³`。下面显示了交换子与 `R³` 中的叉积的关系，`[p q − q p] = 2 p x q`。请注意 `LQ` 的中心是实数 `R`，因为对于任意实数，例如 `p0` 和任意四元数 `q`，有 `[p, q0] = q0 p − q0 p` 等于零。



标量与四元数可交换。据说实四元数组成四元数代数的中心。因此 `R` 也是核。接下来，形成商李代数 `LQ/R`。取李括号 `[p, q]`，其中 `v` 和 `w` 分别为 `p` 和 `q` 的向量部分。因此 `p q − q p = (po qo − <v, w>) + (po w + qo v + v x w) − (qo po − <v, w>) − (qo v + po w + w x v)`。注意实部等于零，以及除叉积项外的所有向量部分。结果为 `2 (v x w) = v x w − w x v`，如前例所述。

## 10.10 Hopf 纤维化

有四种不同的 Hopf 纤维化，全部仅涉及球面。纤维 `F`、底 `B` 以及总空间 `E` 都涉及球面。这四种纤维化用以下模式表示：

`F→E→B`

![方程](img/F000047si4.png)

`S⁰→S¹→S¹`

![方程](img/F000047si5.png)

`S¹→S³→S²`

![方程](img/F000047si6.png)

`S³→S⁷→S⁴`

![方程](img/F000047si7.png)

`S⁷→S¹⁵→S⁸`

![方程](img/F000047si8.png)

前面提到的第一个纤维化涉及一个点 `S⁰`，以及单位圆 `S¹`，并在下面的示例中进行了说明。第二个纤维化在推导纤维、底和整体结构之间关系的结果时使用了复数。该过程在下面展开，同时将纤维化与 Bloch 球联系起来。参见第 10.11 节。第三个纤维化构成了第 10.12 节的内容。在这种情况下，四元数被用于展示两个量子比特之间的希尔伯特空间关系及其可能的纠缠。最后，最后一个纤维化采用八元数，在此不予解释。

### Example 10.15

对于第一个纤维化，圆上的成对的对径点被映射到新圆上的一个点。该过程分两步进行，并在图 10.11 中进行了说明。原始点以及对径点位于图 10.11A 中。点对被标记为 `j` 和 `j′`，`j=1, 2, 3, 4, 5`。第一个操作在右侧的图 10.11B 中示出。在这里，原来的圆被扭成一个 8 字形。在此图中，除点 `5=5′` 外，对径点仍可识别。其次，将 8 字形的左半部分折叠到右半部分即可得到最终结果。这是一个圆，其中对径点被映射到新圆上的单点。这可以在图 10.11C 中看到。在下图中。所得空间是商空间 `S¹`。

![图 10.11 Hopf 纤维化 S0 → S1 → S1. (A) 原始圆；(B) 对圆施加扭转；(C) 折叠操作。](img/F000047f10-11-9780443136979.jpg)

图 10.11 Hopf 纤维化 `S⁰ → S¹ → S¹`。 (A) 原始圆；(B) 对圆施加扭转；(C) 折叠操作。

## 10.11 具有 Bloch 球 S² 的 Hopf 纤维化，一量子比特底

本演示完全基于 Mosseri 和 Dandoloff (2001)。它涉及映射 `S¹→S³→S²`。具体而言，以底 `B=S²` 为基础的 Hopf 纤维化是非平凡纤维化最重要的例子之一。在此结构中，`E=S³` 由大圆纤维化，`F=S¹`。由于非平凡性，`E` 不等于 `B x F` 处处成立，通常它们仅在局部相等。就量子比特而言，纤维与一般量子比特 `e^(iϕ) |q>` 的不确定整体相位 `ϕ` 相对应。底可以被认为是 Bloch 球，其中纯量子比特占据其表面，而混合量子比特位于内部。如前所述，纤维化将使用复值 `u` 和 `v` 在 `C` 中实现，其中 `u=x + iy` 且 `v=z + it`，`x, y, z,` 和 `t` 为实值。由于 `S³` 定义为 `x² + y² + z² + t²=1`，它可以用 `u` 和 `v` 表示为 `|u|² + |v|²=1`。在这种情况下，Hopf 纤维化将使用两个映射 `H` 后接 `K` 的复合来描述。第一个映射将 `S³` 送入扩展平面 `R²` 并集 `{∞}`。第二个映射使用逆立体投影将该扩展平面送入 `S²`。具体而言，这些映射为：

`H(u,v) = (u v^(−1))*`

`K((u v^(−1))*) = (X,Y,Z), X² + Y² + Z² = 1`

`S³` 中参数化为 `ϕ` 的大圆 `(u e^(i ϕ), v e^(i ϕ))` 被映射为单点，即 `H(u e^(i ϕ), v e^(i ϕ)) = (u v^(−1))*`。

代入第一个映射 `H (u, v) = (u v^(−1))* = (x − i y)/(z − i t) = [(x z + y t) + i (x t − y z)]/(z² + t²)`。

## 10.12 具有球面 S⁴ 的 Hopf 纤维化，两量子比特底

本演示完全基于 Mosseri 和 Dandoloff (2001)。涉及球面 `E=S⁷`、纤维 `F=S³` 和底 `S⁴` 的 Hopf 纤维化与 `S¹→S³→S²` 类似地发展。取而代之的是使用四元数。整个处理与第 10.11 节中给出的纤维化平行。在这种情况下，纤维化 `S³→S⁷→S⁴` 将被说明。该程序遵循所引用论文的方法。对于复数，`u[p] = x[p] + i y[p]`，且 `v[p] = z[p] + i t[p]`，其中 `x[p], y[p], z[p],` 和 `t[p]` 为实值，`p=1 or 2`；四元数 `q[p] = u[p] + v[p] j` 将用于 Hopf 纤维化。此外，`|q[1]|² + |q[2]|² = 1`，因此 `x[1]² + y[1]² + z[1]² + t[1]² + x[2]² + y[2]² + z[2]² + t[2]² = 1`，表明四元数对 `q[1]` 和 `q[2]` 表示位于 `S⁷` 表面上的状态。

在这种情况下，Hopf 纤维化仍将使用两个映射 `H` 后接 `K` 的复合来描述。第一个映射将 `S⁷` 送入扩展曲面 `R⁴` 并集 `{∞}`。第二个映射使用逆立体投影将该扩展曲面送入 `S⁴`。如前所述，该方法几乎 100% 与复数情况平行。主要区别在于本例中的维数更大，更重要的是，四元数形成一种非交换的域型结构。这两个映射如下：

`H(q[1], q[2]) = (q[1] q[2]^(−1))*`

`K((q[1] q[2]^(−1))*) = (X,Y,Z,U,V), X² + Y² + Z² + U² + V² = 1`



在展开第一个映射 `H` 时必须谨慎，因为一般情况下四元数不满足交换律。从第一个映射开始：`H`(`q`[1],`q`[2]) = (`q`[1]`q`[2]^(-1))^* = (`q`[2]^(-1))^* `q`[1]^* ![方程](img/F000047si24.png)。取 `q`[2]^(-1) ![方程](img/F000047si25.png) 得到 `q`[2]^(-1) = `q`[2]^* / ∥`q`[2]∥² = (`x`[2]−`y`[2]`i` − `z`[2]`j` − `t`[2]`k`)/( `x`[2]²+`y`[2]²+`z`[2]²+`t`[2]²) ![方程](img/F000047si26.png)。因此，(`q`[2]^(-1))^* = (`x`[2]+`y`[2]`i` + `z`[2]`j` + `t`[2]`k`)/( `x`[2]²+`y`[2]²+`z`[2]²+`t`[2]²) ![方程](img/F000047si27.png)。因此，`H`(`q`[1],`q`[2]) = (`q`[2]^(-1))^* `q`[1]^* = (`x`[2]+`y`[2]`i` + `z`[2]`j` + `t`[2]`k`)(`x`[1]−`y`[1]`i`−`z`[1]`j`−`t`[1]`k`)/( `x`[2]²+`y`[2]²+`z`[2]²+`t`[2]²) ![方程](img/F000047si28.png)。接下来，令 `D` = (`x`[2]²+`y`[2]²+`z`[2]²+`t`[2]²) ![方程](img/F000047si29.png)，并使用复数 `u`[`p`] = `x`[`p`] + `i``y`[`p`] ![方程](img/F000047si30.png)，以及 `v`[`p`] = `z`[`p`] + `i``t`[`p`] ![方程](img/F000047si31.png)，其中 `q`[`p`] = `u`[`p`] + `v`[`p`]`j` ![方程](img/F000047si32.png)，p=1, 2。这得到表达式：`H(q[1],q[2])=[(u[2] + v[2] j) (u[1]* − v[1]j)]/D=[(u[2] u[1]* + v[2] v[1]) + (v[2] u[1]* − u[2] v[1])j]/D=[(u[1]* u[2] + v[1] v[2]) + (u[1]* v[2] – v[1] u[2])j]/D`。在参考文献 (Mosseri and Dandoloff, 2001) 中，量 `u[1]*` 出现时没有共轭，且乘以 j 的项被设为零。在那里，他们将纯复数结果解释为或与简单张量的判据相关联，或在他们的情况下，与非纠缠态相关联。

## 参考文献
* Chern, 1979 Chern S. *没有势理论的复流形* Springer 1979;.
* Coxeter, 1989 Coxeter H. *几何学导论* Wiley 1989;.
* Dugundji, 1975 Dugundji J. 978-0697-006889-7 *拓扑学* Allyn and Bacon 1975;.
* Halmos, 1974 Halmos R. 0-387-90093-4 *有限维向量空间* Springer 1974;.
* Lee, 2006 Lee J. 978-0387-95448-6 *光滑流形导论* Springer-Verlag 2006;.
* Lin, 2021 Lin A. *复乘与椭圆曲线* Stanford.edu 2021;.
* Mosseri and Dandoloff, 2001 Mosseri R, Dandoloff R. 纠缠态的几何、Bloch 球面和 Hopf 纤维丛。 *J Phys A: Math Gen.* 2001;.
* Munkres, 1999 Munkres J. 0-13-181629-2 *拓扑学* Prentice Hall 1999;.
* Phillips, 1967 Phillips A. 开流形的浸没。 *Topology*. 1967;6.
* Rudin, 1966 Rudin W. 0-07-054234-1 *实分析和复分析* McGraw-Hill 1966;.
* Silverman, 1994 Silverman J. *椭圆曲线算术中的高级专题* Springer 1994;.
* Silverman, 2009 Silverman J. *椭圆曲线的算术* Springer 2009;.

# 第 11 章
## 李代数与李群

### 摘要
提供了李代数的多类型（MSA）高层描述。李代数是一个通常无单位元、非结合的代数。因此，它具有类似于乘法的二元运算；然而，它与之前提到的所有二元运算都不同。该乘法不是泛函演算类型，也不是卷积，更不是算子复合。它被称为李括号。李括号的使用，连同雅可比恒等式，将这种代数类型与其他代数区分开来。随后表明 `R³` 中的叉积为李代数低层 MSA 视图的载体集提供了一个范例。Campbell-Baker-Hausdorff 公式及其应用被给出。李代数中的理想构成本章的下一节。第 11.8 节构成本章的最大部分，其中描述了将李群与李代数联系起来的映射。李代数的复化构成了最后一节的内容。这种复化类似于实向量空间的复化，但将该技术扩展到了代数。

#### 关键词
`Lie algebra`; `Lie groups`; `Jacobi identity`; `tangent space`; `Lie–Trotter formula`; `ideals`; `matrix Lie groups`; `homotopy`; `simply connected`

## 11.1 代数结构
李代数是一个通常无单位元、非结合的代数。因此，它具有类似于乘法的二元运算；然而，它与之前提到的所有二元运算都不同。该乘法不是泛函演算类型，也不是卷积，更不是算子复合。它被称为李括号，是一种交替的双线性映射，必须满足超出向量空间或代数范围的若干等式约束。这些约束在下文的 MSA 全局视图中被严格指定。与希尔伯特空间的概念类似，存在无限多个不同的李代数。每个代数都有其对应的类型载体集，以及由签名集描述的算子。与希尔伯特空间一样，李代数除了代数结构外还具有拓扑结构以及其他数学结构。此外，在有限维情况下，每个李代数都可以与一个或多个李群相关联。一般而言，向量场上的李代数是流形微分同胚群的李代数。微分同胚是光滑流形的同构。它将一个流形映射到另一个流形，且其本身及其逆都是可微的。无论如何，李代数与群结构之间存在着紧密的联系。这种对应关系利用李代数更好地理解和分类所涉及的群。这种对应关系的大部分将在后面举例说明。

## 11.2 李代数的 MSA 视图
首先，MSA 中李代数的高层描述使用了两种类型：`SCALAR` 和 `VECTOR`。对应于 `SCALAR` 的载体集通常是复数或实数，签名集是域的签名集。因此，复数域或实数域在 MSA 中产生一个更低层的视图。当考虑李群时，类型 `SCALAR` 不仅包括复数和实数；它还将包括四元数。因此，在后一种情况下，签名集和等式恒等式将是斜域的。对于李代数，如结合或非结合代数，存在一个二元函数 `BINE`，使得：

`BINE`: `VECTOR` × `VECTOR` → `VECTOR`

![方程](img/F000126si1.png)

除了向量空间和代数的全部等式恒等式外，运算名 `BINE` 必须满足以下四个恒等式。首先，将类型和运算名替换为：

* `VECTOR` 用 `u`、`v`、`w` 替换。
* `SCALAR` 用 `a`、`b` 替换。
* `BINE` 用 `[.,.]` 替换，这通常称为李括号。
* `V-ADD` 用 `+` 替换。
* `S-MULT` 用 `·` 替换。

等式恒等式如下：

1. 1) 双线性: `[a·v + b·u, w]` = `a·[v, w]` + `b·[u, w]`.
2. 2) 双线性: `[w, a·v + b·u]` = `a·[w, v]` + `b·[w, u]`.
3. 3) 反交换: `[u, v]` = `−[v, u]`.
4. 4) 雅可比恒等式: `[u, [v, w]]` + `[v, [w, u]]` + `[w, [u, v]]` = `0`.




注意，使用 (3) 可推出 \[u, u\]=−\[u, u\] 蕴含 \[u, u\]=0。另请注意，通过使用两个双线性关系 (1) 和 (2)，代数的两个分配律得以保持。同样，代数的乘法齐次性条件也成立。它再次通过使用两个双线性条件而成立。可能的非结合性意味着 \[x, \[y, z\]\] 不一定等于 \[\[x, y\], z\]。图 11.1 说明了李代数的多项图。此图中未显示的是所有仅与类型 `SCALAR` 相关联的操作名称。

![图 11.1 李代数 MSA 图。](img/F000126f11-01-9780443136979.jpg)

图 11.1 李代数 MSA 图。

## 11.3 李代数的维数

李代数的维数是其在实数或复数域上的底层向量空间的维数。李代数 `L` 的子代数 `M` 是李括号封闭的子空间。因此，如果对 `M` 中所有的 `v` 和 `w`，存在 `M` 中的 `u` 使得 `u`=\[v, w\]；则 `M` 是子李代数（雅各布森，1979）。

### 例 11.1

李代数最简单的例子之一是类型 VECTOR 具有所有实值三维向量的载体集合的情况。在这种情况下，叉积运算 `x` 在 `R³` 中充当李括号。标准 `i`、`j` 和 `k` 坐标系在此应用中最常采用，其中 `i x j=k`、`j x k=i`、`k x i=j`。每当乘积中的运算元被转置时，结果会被否定。这确立了条件 (3) 反交换。此外，任何向量与其自身的叉积为零。雅可比恒等式立即成立，因为 (`i x (j x k)`)=`i x i`=0。例如，设向量为 `v`=1`i` + 2`j` + 3`k` 且 `w`=−1`i` + 4`j`−2`k`；则 `v x w` 可通过取行列式求得：

$\\begin{array}{lll} \\begin{array}{lll} {|i} & j & {\\mspace{20mu}{k|}} \\\\ {|1} & 2 & {\\mspace{20mu}{3|}} \\\\ {|{- 1}} & 4 & {{- 2}|} \\\\ \\end{array} & = & \\begin{array}{lllll} {|i} & j & {\\quad k|} & { i} & j \\\\ {|1} & 2 & {\\mspace{20mu}{3|}} & { 1} & 2 \\\\ {|{- 1}} & 4 & {{- 2}|} & {- 1} & 4 \\\\ \\end{array} \\\\ \\end{array}$

![方程](img/F000126si2.png)

因此结果为 `v x w`=−4`i`−3`j` + 4`k` + 2`k` −12`i` + 2`j`=−16`i` −`j` + 6`k`.#

可以采用基无关的标准证明 `R³` 是实数上的李代数。这里，我们利用 `R³` 是实值希尔伯特空间 `H` 这一事实。对于 `H` 中的 `u`、`v` 和 `w`，使用实值点积作为内积 <v, w>。在这种情况下，通过直接计算可得公式成立：`u x (v x w)`=`v` <w, u>−`w` <u, v>；然后将其代入雅可比恒等式的左边，得到 `u x (v x w)` + `w x (u x v)` + `v x (w x u)`=`v` <w, u>−`w` <u, v> + `u` <v, w>−`v` <w, u>+`w` <u, v>−`u` <v, w>=0.#

### 例 11.2

实数或复数域上的结合代数 `A` 通过引入李括号成为李代数。在这种情况下，它被称为交换子。交换子对 `A` 中的 `v` 和 `w` 定义为 \[v, w\]=`v`·`w`−`w`·`v`。乘法 `v`·`w` 和 `w`·`v` 是不一定可交换的结合代数 `A` 中的继承乘法。因此，现在存在两种类型的乘法：一种用于结合代数，另一种用于李代数。#

在有限维情况下，n×n 矩阵的李代数用李括号为交换子来描述。这些李代数根据域是复数还是实数记为 `gl(n,C)` 或 `gl(n, R)`。这些是对应于可逆矩阵的一般线性群的一般线性李代数。因此，这些矩阵的行列式非零。

李群与特定李代数之间存在众多性质。特别是，李群有一个单位元，通常是与李代数中零向量相关的矩阵。此外，李群是局部可逆的；单位元附近存在邻域，允许这些开集之间存在连续映射。将看到指数映射是从李代数到李群的映射。反之，从李群到李代数存在线性化或切向运算。本质上，切空间成为李代数。这些是关联李代数与特定李群以及关联李群与唯一李代数的方法。

### 例 11.3

Campbell-Baker-Hausdorff (`CBH`) 公式将显示李代数在确定李群单位元附近元素的局部行为方面的广泛应用。该公式作为可能不收敛的无穷级数给出，其表述是形式化的。在这种情况下，指数群的群乘法由李代数的括号决定。该公式涉及李括号以及 `exp` 和 `log` 的幂级数展开。`CBH` 公式涉及 `log((e^(*a*)) (e^(*b*)))`，其中 `a` 和 `b` 是不交换的李代数元素。对于 `log` (1 + `z`)，关于原点的泰勒展开，给出 `log` (1 + `z`)=`z`−`z`² / 2 + `z`³ / 3 – `z`⁴ /4 + …。该级数在 | `z` | <1 时收敛，仅用于原点的一个很小的邻域。另外，设 `e^(*z*)`\(=1 + `z` + `z`²/2 + …，它在 `C` 中处处收敛。这是指数 `e^(*z*)` 的通常幂级数展开。接下来，将求出两个指数乘积的对数的幂级数展开。项将按其多项式次数逐一说明。

对于 `log((e^(*a*)) (e^(*b*)))`，没有常数项，但：
* 有两个线性项，相加为 `a` + `b`。
* 二阶项为 `ab`/2−`ba`/2；这些项可使用李括号描述为 1/2 \[`a`, `b`]。
* 三阶项为 1/12 (`a`² `b` + `a` `s`² + `b`² `a` + `b` `a`²–2 `a` `b` `a`−2 `b` `a` `b`)。如前所述的低阶项所示，该表达式也可使用李括号书写。在这种情况下，它等于 1/12 (\[`a`, \[`a`, `b`]\] + \[`b`, \[`b`, `a`]\])。
* 有四阶项，它们为 1/24 \[`a`, \[`b`, \[`a`, `b`]\]\]。…#

`CBH` 公式表明展开的所有项都可以用李括号唯一地表示。此外，值得注意的是，Dynkin 公式使得在 `CBH` 公式的部分和级数中计算大量交换子项成为可能（霍尔，2015）。

### 例 11.4

考虑复平面中的单位圆，`S¹`\(=`U(1)`={z, 使得 z 在 `C` 中且 |z|=1}，则 `z`=`e^(*it*)`。李括号 \[`it`, `is`]=0，其中 `s` 和 `t` 为实数。因此根据 `CBH`，仅使用线性项，可得 `e^(*it*)` `e^(*is*)`\(=`e^(*i*(`s*+*t*))`。`CBH` 公式中的所有其他项均为零。在单位圆上点 (1, 0) 处取切线，这里相关的李代数与 (1, 0) 处的切线平行。为此，首先注意在时间 `t`=0 时，圆路径上的点为 (1, 0)。接下来，`z` 对参数 `t` 的导数为 `dz/dt`=`i` `e^(*i*),^(*t*)`，在 `t`=0 处求值得到 `i`。因此，复平面中的方向沿纵坐标的上部向上指向。将该向量平移到点 (1, 0) 再次得到一个向上指向的切向量。#

另一个与 `CBH` 公式相关的恒等式是 Lie–Trotter 公式。在这种情况下，它涉及 n×n 实数或复数矩阵幂的指数。简而言之，设矩阵为 `A` 和 `B`；则 `e^((*A*+*B*))`\(=lim[*k*→*∞*] \[`e^(*A*/*k*)` `e^(*B*/*k*)\]`^(1/*k*)。当使用有限的 `k` 值时，得到一个近似值。使用 `Suzuki-Trotter` 乘积公式可获得更好的近似：`e^((*A*+*B*))`，它近似等于 `e^(*B*/2)` `e^(*A*)` `e^(*B*/2)`。更高阶的近似可在 贝里（2006） 中找到。

## 11.4 李代数中的理想



# 李代数理想

李代数 `L` 中的理想是一个具有特殊性质的子代数 `M`。它不仅满足对所有 `v`、`w` 在 `M` 中，存在 `M` 中的 `u` 使得 `\[v, w\]=u`，而且对 `L` 中的每一个 `z` 和 `M` 中的每一个 `w`，都存在 `M` 中的 `v` 使得 `\[z, w\]=v`。`L` 中的所有理想都是双边的。另外，`L` 本身也是一个理想，以及 `L` 的核。商代数或因子代数是 `L / M`；它是由形如 `L + M=\[v + M, w + M\]=\[v, w\] + M` 的陪集构成的代数，对所有 `v` 和 `w` 在 `L` 中成立。因子代数使用李括号是一个李代数。李代数被称为单的，当且仅当 `L` 中的唯一理想是 `0` 和 `L`，前提是 `\[L, L\]` 不为零，即它不是可交换的。非单李代数的例子是一般线性代数，`gl(3,C)` 或 `gl(3,R)`。这些代数通常简称为 `gl(3)`。在任何情况下，很容易看出 `gl(3)` 中的所有标量矩阵构成一个子代数。此外，该子空间内的矩阵具有如下性质：对于标量 `a` 和 `b`，对角矩阵的交换子 `\[aI, bI\]=0`。

### 示例 11.5

在 `g(3)` 内，将描述一个特殊的子代数。在此情况下，类型 `VECTOR` 由所有上三角的三阶矩阵组成。类型 `SCALAR` 可以是实数或复数。在任何情况下，特征集对应于域上结合代数的通常运算。该结构 `S` 使用李括号是一个李代数：`\[A, X\]=A.X−X.A`，其中 `A` 和 `X` 是上三角矩阵，且 `A.X` 表示三阶矩阵结合代数中运算 `BINE` (`A`, `X`)。一个重要事实是，严格上三角矩阵的子李代数构成了 `S` 的一个理想。这类矩阵 `T` 仅在主对角线上方允许非零元素；因此，主对角线及下方全部为零。它们也被称为海森堡矩阵。因此，考虑 `S` 中的 `X` 和上述理想中的 `T`；那么，`\[X, T\]` 得到另一个海森堡矩阵。下面按顺序给出 `X`、`T` 以及交换子 `X.T−T.X`。

$\\begin{matrix} {|a} & b & {c|} & {|0} & x & {y|} & {|0} & {\\left( {a - d} \\right)x} & {{\\left( {a - f} \\right)y - {ex} + {bz}}|} \\\\ {|0} & d & {e|} & {|0} & 0 & {z|} & {|0} & 0 & {{\\mspace{45mu}\\left( {d - f} \\right)z}\\qquad|} \\\\ {|0} & 0 & {f|} & {|0} & 0 & {0|} & {|0} & 0 & {{\\mspace{81mu} 0\\mspace{54mu}|}.} \\\\ \\end{matrix}$

![方程](img/F000126si3.png)

这表明严格上三角矩阵在 `S` 内的所有上三角矩阵中构成一个理想。

### 示例 11.6

在本例中，将 `VECTOR` 的载体集视为所有迹为零的二阶实值矩阵。在此情况下，`SCALAR` 指实数域，矩阵也在实数域上。设李括号的运算 `BINE` 为交换子。对于该李代数，一个基由下面按各自顺序给出的三个矩阵 `u`、`v` 和 `w` 组成：

$\\begin{array}{rrrrrr} {|0} & {1|} & {|0} & {0|} & {|1} & {0|} \\\\ {|0} & {0|} & {|1} & {0|} & {|0} & {{- 1}|} \\\\ \\end{array}$

![方程](img/F000126si4.png)

特殊线性李代数 `sl(2, R)` 的任意元素 `x` 由下方左侧给出的迹为零形式的矩阵给出。它是上面三个矩阵 `u`、`v` 和 `w` 的线性组合。现在将使用前面提到的基矩阵来运用交换子。首先形成 `x` 与前面提到的前两个基元素的交换子。首先，使用 `u`，即前面提到的第一个基元素，得到 `y=\[u, x\]=(u.x−x.u)`。所得矩阵是 `y` 的矩阵，如中心图像所示。最后，再次使用交换子，设 `z=\[v, x\]=(v.x−x.v)`，其中 `x.v` 是 `sl(2,R)` 的一般元素 `x` 与前面提到的基矩阵 `v` 的通常矩阵乘积。这些矩阵 `x`、`y` 和 `z` 分别为，

$\\begin{array}{rrrrrr} {|a} & {c|} & {|b} & {{- 2a}|} & {|{- c}} & {0|} \\\\ {|b} & {{- a}|} & {|0} & {{- b}|} & {|{2a}} & {{c|}.} \\\\ \\end{array}$

![方程](img/F000126si5.png)

具有 `sl(2,R)` 中 `x` 结构的任意元素使用此交换子构成一个李代数。所有结构为 `y` 的元素集合构成 `sl(2,R)` 的子李代数，形式为 `z` 的所有元素也是如此。此外，这样的结构被称为 `sl(2,R)` 的内理想，因为李代数 `sl(2,R)` 是单的；除了零和 `sl(2,R)` 本身之外没有真正的理想。

一般来说，然而，存在甚至不是子代数的内理想（Benkart, 1977）。

上述说明简单李代数中内理想存在的例子在 `gl(2,C)` 中也成立；所有陈述保持不变。在此情况下，类型 `VECTOR` 将是所有迹为零的二阶复值矩阵的集合，而类型 `SCALAR` 将是复数。

### 示例 11.7

对于李代数 `gl(2,R)`、`gl(2,C)`、`sl(2,R)` 或 `sl(2,C)`，如前例所示，后两者李代数的一个基由矩阵 `u`、`v` 和 `w` 组成。它们按各自顺序在下面给出：

$\\begin{array}{rrrrrr} {|0} & {1|} & {|0} & {0|} & {|1} & {0|} \\\\ {|0} & {0|} & {|1} & {0|} & {|0} & {{{- 1}|}.} \\\\ \\end{array}$

![方程](img/F000126si6.png)

注意 `\[w, u\]=2u`、`\[w, v\]=−2 v` 且 `\[u, v\]=w`。这些涉及李括号的关系由任意 `k` 个 `k` 矩阵满足，`k=2, 3, …` 例如，设 `k=3`。

将这三个矩阵称为 `U`、`V` 和 `W`。设每个矩阵的九个元素按下面为 `U` 给出的方式恰好寻址。`U` 的元素用 `Uij` 表示，其中 `i` 是行指标 `i=1, 2, 3`，`j` 是列指标 `j=1, 2, 3`。然后对所有矩阵，假设所有元素除非另有说明否则等于零。对于 `U`，设 `U12=2`，并假设 `U23=1`。对于 `V`，设 `V21=1` 且 `V32=2`。对于 `W`，设 `W11=2` 并使用 `W33=−2`。以下三阶矩阵按顺序为 `U`、`V` 和 `W`

$\\begin{array}{rrrrrrrrr} {|0} & 2 & {0|} & {|0} & 0 & {0|} & {|2} & 0 & {0|} \\\\ {|0} & 0 & {1|} & {|1} & 0 & {0|} & {|0} & 0 & {0|} \\\\ {|0} & 0 & {0|} & {|0} & 2 & {0|} & {|0} & 0 & {{- 2}|} \\\\ \\end{array}$

![方程](img/F000126si7.png)

然后，与二阶情形类似，可得 `\[W, U\]=2U`、`\[W, V\]=−2V`、`\[U, V\]=W`。

对于 `k=4`，前两个矩阵 `X` 和 `Y` 分别再次为上三角和下三角，第三个矩阵 `Z` 再次为对角矩阵。使用与 `k=3` 相同的记号，设所有矩阵的元素均为 0，除以下矩阵元素外：`X12=3`、`X23=2`、`X34=1`、`Y21=1`、`Y32=2`、`Y43=3`、`Z11=3`、`Z22=1`、`Z33=−1`，最后 `Z44=−3`。如果使用李交换子括号，则如前所述 `\[Z, X |=2 X`、`\[Z, Y\]=−2Y` 且 `\[X, Y\]=Z`。

将前例的结果推广到 `n+1` 阶 `n+1` 矩阵，李括号关系再次成立。设 `A` 为上三角对角线，`B` 为下三角对角线，`C` 为对角线。再次所有矩阵元素均为零，除 `A12=n`、`A23=n−1` 和 `Ak(k+1)=n+1−k`、`k=1, 2, …, n` 外。接下来，`B21=1`、`B(k+1)k=k`、`k=1, 2, …, n`。最后，对于偶数 `n`，则 `C11=n`、`Ckk=n + 2 –2 k`、`k=1, 2, …, n/2`，且 `Cnn=−n`、`C(n−k+2)(n−k+2)=−n+2k −2`、`k=1, 2, …, n/2`，对于中心元素，`C(n/2+1)(n/2+1)=0`。最后，对于奇数 `n`，则 `C11=n`、`Ckk=n + 2 –2 k`、`k=1, 2, …, (n+1)/2`，且 `C(n+1)(n+1)=−n`、`C(n−k+2)(n−k+2)=−n+ 2k−2`、`k=1, 2, …, (n+1)/2`。有关此的有趣描述可在 Draper and Meulewaeter (2022) 中找到。



集合 `M` 的中心化子子李代数是一个集合 `CM`，其元素与 `M` 交换，即 `CM={v in L is such that for all w in M, [v, w]=0}`。`L` 的中心是 `L` 的中心化子。李代数 `L` 上的导子 `D` 是一个线性映射 `D: L → L`，使用伴随运算 `adu(v)=[u, v]` 定义。这些导子构成一个李子代数。此外，导子满足莱布尼茨法则：`D([u, v])=[D(u), v] + [u, D(v)]`。李代数同态 `h`，从一个代数到另一个代数，设 `h: Lie¹ into Lie²`，是一个线性映射，使得对所有 `u` 和 `v` 在 `Lie¹` 中有 `h([u, v])=[h(u), h(v)]`。

## 11.5 李代数的李群的表示与 MSA

李代数 `A` 的一个表示由一组自伴算子、斜自伴算子以及对称或斜对称算子构成。在下文中，将假设表示为一组自伴矩阵的族 `F`。对于 `A` 中的每个生成元 `Xi`，在 `F` 中对应一个矩阵 `Mi`。相同的交换代数成立 `[Xi, Xj]=[Mi, Mj]`。当使用任意 `Mj` 时列向量不存在平凡不变子空间时出现不可约表示。两个表示是等价的；即 `M` 和 `N` 等价意味着存在一个酉矩阵 `U` 使得 `N=U* M U`（Hall, 2013）。

李群与离散群不同之处在于总是有一些拓扑属性与群相关联或定义群。这些包括紧致性和连通性以及分离公理。此外，还涉及各种流形，如光滑、可微的，甚至全纯的。正如前面提到的，一般而言这些流形在小尺度上处处类似于欧几里得空间。群的元素是流形中的点。此外，连续性起着至关重要的作用。正如早期所建议的，这些群类似于加性向量群。然而，李群大多数时候是乘法型的，但它们不必是乘法的；参见例 11.11。无论如何，它们被称为连续参数群。它们通常用于建模连续对称性，特别是旋转对称性。各种类型的李群将被描述，包括实李群、矩阵李群和复李群。

最简单的李群是有限维实群。在 MSA 描述中，存在一种 `ELEMENT`，它是群成员的名称。如同任何群一样，元数结构是 `(1, 1, 1)`。存在三个不同的签名集，每个包含一个不同的元数算子名：
* 零元，`IDENTITY`，
* 一元，`INV`: `ELEMENT → ELEMENT`
* 二元，`MULT`: `ELEMENT x ELEMENT → ELEMENT`

然而，与离散群不同，存在额外的要求。`ELEMENTS` 将具有对应的载体集为流形 `M`，通常是欧几里得的。最重要的是，这些流形使得可以执行微积分型运算，例如微分切空间的创建。简而言之，李群代数运算必须至少是连续可微的。微分型运算通常在该类的最重要的元素附近进行，即 `IDENTITY`，`I`。对于群中的任意元素，可以找到一个映射将该非单位元变换为单位元。因此，可以自然地识别两个切空间，从而在群流形上得到一个非消失的向量场。在流形上存在光滑向量场被称为平行化。

此外，不仅必须存在对应于名称 `MULT` 和 `INV` 的元数分别为 2 和 1 的映射 `x` 和 `g`，而且它们还必须是光滑映射。光滑程度从可微性到解析性不等。如常，三个代数方程约束必须成立。设 `A`、`B` 和 `C` 在 `M` 中；则约束如下：
1. 结合律：`(A x (B x C))=((A x B) x C)`
2. 单位元条件：`I x A=A x I=A`
3. 单侧逆元：`g(A) A=I` 为左逆，且 `A g(A)=I` 为右逆；两者对李群都成立。图 11.2 说明了李群的多元图。

![图 11.2 李群 MSA 图。](img/F000126f11-02-9780443136979.jpg)

图 11.2 李群 MSA 图。

## 11.6 李群的拓扑流形性质简述

在给出例子之前，将提及李群所具有的一些拓扑和流形性质。流形 `M` 总是豪斯多夫型特殊拓扑空间，并假定为二可数。此外，豪斯多夫空间必须处处局部同胚于 `R^(n)`。空间在局部看起来像欧几里得空间，即使群结构可能高度非线性。同胚映射是双连续、一一对应、满射、保持结构的映射。欧几里得空间既是豪斯多夫空间也是二可数空间。

流形 `M` 是一组称为图表的开集 `Ua` 的集合；它们的并集覆盖 `M`。图表共同构成一个图册。函数或坐标映射 `fa` 使得 `fa: M → R^(n)`，连同 `fa^(-1)` 都是同胚。图表称为坐标域，`fa` 称为坐标映射。`fa` 和 `fa^(-1)` 都是连续的。当 `fb fa^(-1)` 在 `C^(k)` 中或更常见地在 `C^∞` 中时，这些映射被称为光滑。李群可以视为具有局部坐标的 n 维向量空间。图 10.5 在李群为流形 `M` 时完全适用。只需将 `M` 替换为李群。这里再次，转移函数是同胚 `T`，使得 `Tab=fb fa^(-1)`；它们将一个图表 `Ua` 中的元素映射到另一个图表 `Ub`。

再次，将第 10.3 节的一些简要概念回顾用于李群流形。这些流形是连通拓扑空间 `Tp`，当它们不能表示为两个或多个非空开集的不交并时。对于非连通空间，拓扑空间 `Tp` 存在最大连通子集，称为连通分支。道路连通空间 `Tp` 是存在连续函数 `f: [0, 1] → Tp`，其中对于 `Tp` 中的 `x`、`y`，有 `f(0)=x`，`f(1)=y`。道路连通蕴含连通。

拓扑空间在每个开覆盖都有有限子覆盖时是紧致的。由于图表是开覆盖，紧致流形需要仅用有限数量的图表构成的图册。紧致李群很重要，因为所有不可约表示都是有限维的且具有张量积构造（Johnson, 1976）。

### 例 11.8

在本例中，将描述一般线性群。首先将指定纯代数性质。然后将提及一些拓扑和子群性质。对于类 `ELEMENTS`，令载体集为实数域上 2×2 可逆矩阵。使用单位矩阵作为 `IDENTITY`，通常的矩阵乘法作为 `MULT`。令典型的矩阵求逆运算对应于 `INV`。如前所述，结构是一个幺结合代数，因此必然是一个乘法群。它用 `GL(2, R)` 表示，称为维数为四的一般线性群，并且是 `M(2, R)` 的子群，`M(2, R)` 是实数域上所有 2×2 矩阵的实向量空间。随后将描述相关的复值李群 `GL(2, C)` 以及它与莫比乌斯变换群的关系。





一般线性群 `GL(2, R)` 是一个四维的光滑流形；它是 `R⁴` 的一个非紧开子集。如前所述，该李群由 2×2 实值矩阵表示，其行列式非零。它是不连通的，并且有两个对应于行列式符号的连通分支。行列式为正的元素称为正分支，并包含 `IDENTITY`。它本身也是一个李群，记为 `GL+(2, R)`。`GL(2, R)` 和 `GL+(2, R)` 具有相同的李代数 `m(2, R)`。`m(2, R)` 中的李括号是代数乘法 \[A, B\]，其等于 `AxB−BxA`，例如当 `A=I` 时可以等于零。因此，李代数不是除法代数。`GL(2, R)` 的极大紧子群是 `O(2, R)`，即正交李群，其在后续章节中详细描述。对于 `GL+(2, R)`，极大紧子群是特殊正交群 `SO(2)` (Jacobson, 1979)。这些子群将在随后讨论。

拓扑空间 `T` 当它是道路连通的，并且 `T` 中的每条环路都可以连续收缩到一点时，称为单连通。严格来说，它是描述 `T` 中环路的两个连续函数 `f` 和 `g` 之间的同伦。设 `f: [0, 1] → T`，`g: [0, 1] → T`，`f(0)=g(0)`，`f(1)=g(1)`。那么，这两条路径定义了一个环路。环路的性质将在第 12 章中更详细地解释，其中同伦是主要概念。

李第三定理指出，每个有限维实李代数都是一个单连通李群的李代数。本质上，单连通性将是建立实情形下李群与李代数之间一一对应关系的判据。最后，当李群是连通的、非阿贝尔的，并且所有闭连通子群都是平凡的，即它们等于单位元或整个空间时，称其为单李群。

下图 图 11.3 展示了两条连续路径。这显示了道路连通性，但从分析或实际观点来看，单连通性是有问题的。这里设 `f(t)=t sin(π /(2t))` 对 `t` 在 `(0, 1]`，且 `f(0)=0`。那么 `f` 在区间 `[0, 1]` 中是连续的，因为它在原点满足条件 `|f(t)|` 小于或等于 `|t|`。因此 Lipschitz 条件对 `f` 在原点成立。另外，设 `g(t)=2t – t²`。由于 `f(0)=g(0)` 且 `g(1)=f(1)`，它们一起形成一个环路。然而，将此环路收缩到一点，例如零，需要做很多工作，因为函数 `f` 不是有界变差的。`[0, 1]` 中的总变差等于求和，$\\sum\_{n = 0}^{\\infty}{\\left( {1/\\left( {2n + 1} \\right)} \\right) = \\infty}$![方程](img/F000126si8.png)。因此，对应于该函数的曲线不可求长，直观上其弧长是无限的。

![图 11.3 路径连通性。](img/F000126f11-03-9780443136979.jpg)

图 11.3 路径连通性。

### 例 11.9

特殊李群 `SL(2, R)` 是 `GL(2, R)` 的子群。该子群 `SL(2, R)` 由所有行列式等于一的 2×2 矩阵组成。它是连通的、非紧的，并且是单群。`SL(2, R)` 不是单连通的；然而，`SL(2, C)`，即复特殊群，后续将被证明是单连通的。`SL(2, R)` 的维数是三，因为行列式的约束。极坐标形式参数化，及其他参数化，可以用于该群的元素。事实上，`SL(2, R)` 的元素可以写成正交旋转矩阵与具有正特征值和单位行列式的对称矩阵的乘积。相应的李代数 `sl(2, R)` 由所有实数上的迹为零的 2×2 矩阵 `A` 和 `B` 组成。二元运算通常是李括号交换子。因此，\[A, B\]=`AxB−BxA`。

涉及 `SL(2, R)` 中元素的众多应用之一是利用修正的偏心率参数 `e` 对圆锥曲线进行分类，参见 (SL2, 维基百科)。这涉及 Cayley-Hamilton 方程。每个矩阵都满足其特征方程。因此，对于 `SL(2, R)` 中的 `A`，`A` 的特征方程为 `x²−tr(A) x + det(A)=0`，并且由于 `det(A)=1`，特征方程变为 `x² −tr(A) x + 1=0`。二次公式给出特征方程的解 `x`：

*x* = (*t**r*(*A*)+−(*t**r*(*A*)²−4)^(1/2))/2.*L**e**t**t**i**n**g**e* = |*t**r*(*A*)|/2*t**h**e**n*:

![方程](img/F000126si9.png)

*   对于 `e <1`，`A` 是椭圆的，具有复数、单位和共轭特征值，用于旋转。

*   对于 `e=1`，`A` 是抛物线的，具有单个特征值 +1 和 −1，用于剪切操作。

*   对于 `e> 1`，`A` 是双曲的，具有实数倒数特征值，用于挤压操作。

前一示例中提到的双曲情形算子也来自射影线性李群 `PSL(2, R)`。它们在闵可夫斯基空间中用作洛伦兹提升。在此情形中采用双曲函数 `sinh` 和 `cosh`，提供了对称双曲空间。后一性质意味着 `cosh²–sinh²=1` (Bargmann, 1947)。

### 例 11.10

再次考虑 `SL(2, R)`。在 例 11.9 中，不太明确地提到与该群相关的流形由乘积流形 `R²` 和圆群 `S¹` 参数化。还提到存在其他参数化。例如，该群中每个点 `(a, b, c)` 属于 `R³`，并且当 `a` 非零时的参数化也可以由矩阵给出：

$\\begin{matrix} {|a} & {\\qquad{b\\mspace{31mu}|}} \\\\ {|c} & {{\\left( {1 + {bc}} \\right)/a}|} \\\\ \\end{matrix}$

![方程](img/F000126si10.png)

点 `a` 是一个奇点。然而，当标量 `a` 非零时，该矩阵的行列式为一。奇点在李群中大量存在且成问题。在任何情况下，在这些奇点处需要替代参数化，并且通常可以提供。

似乎在本文档的这一点上，所有已描述的李群都是矩阵李群。接下来给出一个非矩阵李群的例子 (Hall, 2013)。

### 例 11.11

再次考虑一个三维李群，其维数和构造与 `SL(2, R)` 相似。这次，该群中每个点 `(a, b, c)` 属于载体集：`R²×S¹`，其中 `S¹` 是圆群。因此在此情形中第三个元组是复值且长度为一。因此 `c` 非零。此示例中的实维数为四。给出了一个参数化，涉及平面 `R²` 中点的加法以及使用圆群 `S¹` 元素的旋转。具体而言，对于该流形中的两个元素 `v=(a, b, c)` 和 `w=(d, g, f)`，则

$\\begin{array}{l} {{MULT}\\left( {v,w} \\right) = \\left( {a + d,b + g,c f\\exp^{iag}} \\right)} \\\\ {{INV}\\left( v \\right) = \\left( {- a, - b,{1/c}} \\right),{note}{that}{MULT}\\left( {v,{INV}\\left( v \\right)} \\right) = \\left( {0,0,{c/c}} \\right) = {IDENTITY}} \\\\ {{IDENTITY} = \\left( {0,0,1} \\right)} \\\\ \\end{array}$

![方程](img/F000126si11.png)

可以证明 (Hall, 2013)，不存在对应于该抽象李群的矩阵李群。

## 11.7 矩阵李群的形式描述




许多李群的元素高度非线性，利用相应的李代数来更好地理解群结构是至关重要的。然而，李群的一个更简单的子集是矩阵李群。矩阵李群是 `M(n, C)` 的子集，其中 `M(n, C)` 是所有复值 `n` 阶 `n` 矩阵的集合。它的维数在复数上为 `n²`；在实数上，其维数为 `2n²`。`M(n, C)` 中的矩阵 `Ak`  said to converge to `A` in `M(n, C)`，这意味着 `Ak` 的 `n²` 个元素收敛到 `A` 的对应元素。`GL(n, C)` 是一个由可逆矩阵组成的李群。该群中所有矩阵 `A` 的集合构成 `M(n, C)` 的一个开子集，可视为实域上维数为 `2n²` 的流形。`GL(n, C)` 的子群 `G` 被称为李子群，这意味着 `G` 中的每个矩阵 `Ak` 要么收敛到 `G` 中的 `A`，要么不可逆。例如，`GL(n, R)` 是 `GL(n, C)` 的矩阵李子群，因为如果 `An` 是 `GL(n, R)` 中矩阵序列且收敛到 `A`，则其条目为实数，并且 `A` 要么不可逆，要么属于 `GL(n, R)`。

群 `G` 在 `GL(n, C)` 中是闭的，这意味着它作为 `GL(n, C)` 的子集是闭的。对于矩阵李群，连通性等价于道路连通性。后一种连通性的重要性在于它更容易验证。

### 示例 11.12
考虑 `n` 大于 1 时的特殊线性李群 `SL(n, R)`。这是所有行列式为一的 `n` 阶 `n` 矩阵 `A` 的群。由于行列式是连续的，行列式为一的矩阵序列将收敛到具有相同行列式值的矩阵，从而表明 `SL(n, R)` 是一个李矩阵群。矩阵 `A` 可以写成极坐标形式，即一个正交矩阵与一个行列式为一的对称矩阵的乘积。此李群的维数为 `n²–1`。

### 示例 11.13
李群 `U(n, C)` 是 `n` 阶 `n` 复值酉矩阵的群。它们的逆是伴随矩阵。维数在复数域上为 `n²`；在实数上，维数为 `2n²`。当 `n=1` 时，它是所有绝对值为一的复数的圆群 `S¹`。`U(n, C)` 中矩阵 `A` 的行列式也是绝对值为一的复数。一个重要的子群是 `SU(n, C)`；这些是行列式为一的酉矩阵。该群在量子门型计算机中具有极其重要的意义。与 `U(n, C)` 相关的李代数 `u(n, C)` 都是斜自伴矩阵，其李括号为交换子。

`U(n, C)` 中的矩阵 `A` 既连通又紧致。它是紧致的，因为在 `R^(2*n*²)` ![Equation](img/F000126si12.png) 中，`A` 是闭且有界的。它是闭的，因为 `A` 中元素的实部和虚部构成的点集满足恒等式 `U*U=I` 的同时方程。它是有界的，因为 `A` 的每一列的长度均为单位长度。

连通性可通过使用涉及矩阵的酉变换从道路连通性得出：`V* A V=diag (e^(ip1), …, e^(ipn))`。这里，`diag (e^(ip1), …, e^(ipn))` 是一个对角矩阵，每个对角元的长度为单位长度。因此，`A=V diag (e^(ip1), …, e^(ipn)) V*`。对于 `t` 在 `[0, 1]` 中，参数化 `A(t)=V diag (e^(ipt1), …, e^(iptn))` 成立，且当 `t=0` 时得到 `A=I`。因此，当 `t` 从 0 变到 1 时，`A(t)` 在 `U(n, C)` 中从 `I` 到 `A` 形成一条连续路径。

### 示例 11.14
考虑由 2×2 复值矩阵的特殊酉李群 `SU(2, C)` 的元素组成的载体集。这些矩阵的形式为 `A=` 
```
\begin{matrix} {|z} & {{- w \ast}|} \\ {|w} & {{\mspace{23mu} z \ast}|} \\ \end{matrix}
```
![Equation](img/F000126si13.png)
其中 `z` 和 `w` 是复数且 `|z|² + |w|²=1`。`SU(2, C)` 中的矩阵 `A` 是行列式为一的酉矩阵。`A` 的列构成一个标准正交集。两个列向量的内积为 `<(z w)′, (−w* z*)′>=(z* w*) (−w* z*)′=0`。此外，一旦第一列被定义，该群中矩阵 `A` 的结构就确定了。第二列可通过使用正交归一性和行列式等于一的事实唯一确定。`SU(2, C)` 与三维球面微分同胚。通过令 `z=a + bi`，且 `w=c + di` 可见这一点。则 `|z|² + |w|²=a² + b² + c²+ d²=1` 给出三维球面 `S³` 的方程。当 `S³` 的方程写成 `a² + b² + c²=1 – d²` 时，可以看出对于变化的 `d`，当 `d=1` 时它成为一个点的方程，以及当 `d` 在 `0, 1)` 中时有无数个球面。因此，`SU(2, C)` 既紧致又单连通。此外，`SU(2, C)` 与单位四元数同构：`q=a + bi + cj + dk`，其中 `a`、`b`、`c` 和 `d` 为实数，且它们的平方和等于一（[吉尔莫尔，1974）。

先前，利用 `SL(2, R)` 的载体集已用若干表示进行了说明。接下来将给出复二维特殊线性群的说明。第一个例子将使用从拓扑空间 `X=SL(2, C)` 到子空间的连续映射 `D`。该映射也将是一个收缩映射，其中算子 `D` 在子空间上如同恒等式。满足这些条件的子空间称为超空间的 retract。映射也将是形变收缩映射 `D`。这是一种收缩过程，其中 `D` 对原始空间进行操作，使其连续收缩到子空间。使用形变的目的在于将子空间的同伦性质关联或扩展到原始空间。因此，如果子空间具有某些同伦性质，则在成功执行该过程后，父空间也将具有这些性质。简而言之，形变 retract 是创建同伦等价的过程。同伦的目的是在拓扑空间中保持或识别在拉伸或收缩操作下不变的性质。下一章详细描述同伦。然而，存在形变收缩但不连续进行的空间，例如锯齿状图案。在这种情况下，同伦不被保持（哈彻，2002）。

### 示例 11.15
行列式为一的复数域上 2×2 矩阵的特殊线性群用 `SL(n, C)` 表示。当 `n=2` 时，维数为三，但在实数上为六。它是一个简单但不紧致的群。与 `SL(n, R)` 类似，这些矩阵也可以用极坐标形式参数化。在这种情况下，它们可以表示为特殊酉矩阵 `SU(2, C)` 中的乘积，以及行列式为一的正定自伴矩阵的乘积。为了证明 `SL(2, C)` 单连通，将证明存在一个形变 retract `D`，从 `SL(2, C)` 到特殊酉矩阵的子空间 `SU(2, C)`。该子空间在 示例 11.14 中被证明是单连通的。

下一个例子专门用于证明 `SL(2, C)` 单连通。这将通过说明存在一个形变 retract `D`，从 `SL(2, C)` 到特殊酉矩阵的子空间 `SU(2, C)` 来完成。

### 示例 11.16
由于 `SU(2, C)` 由酉矩阵组成，同伦将通过采用 `SL(2, C)` 中的任意矩阵并将其连续变换为酉矩阵来实现。这可以通过正交归一化矩阵的列来实现。因此，Gram-Schmidt 过程可用于列向量。例如，为了证明一个 retract，`SL(2, C)` 中下面的左矩阵的第二列向量将被变换为与第一列正交。原始矩阵如下给出，其后直接给出结果矩阵：
```
\begin{array}{rrrr} {|a} & {c|} & {|a} & {e|} \\ {|b} & {d|} & {|b} & {{f|}.} \\ \end{array}
```
![Equation](img/F000126si14.png)



详细地说，原矩阵的第二列（`c d`）′将通过涉及内积的投影映射到第二矩阵的第二列（`e f`）′。使用涉及第二列的 `Gram-Schmidt` 过程得到：

(`e` `f`)′ = (`c` `d`)′ − < (`a` `b`)′, (`c` `d`)′ > (`a` `b`)′/(‖`a`‖²+‖`b`‖²).

![Equation](img/F000126si15.png)

计算内积得到：

(`e` `f`)′ = (`c` `d`)′ − (`a` `b`)′(`c``a`*+`b`*`d`)/(‖`a`‖²+‖`b`‖²).

![Equation](img/F000126si16.png)

量 <(`a` `b`)′, (`c` `d`)′> (`a` `b`)′/(‖`a`‖² + ‖`b`‖²) 称为列 (`c` `d`)′ 在列 (`a` `b`)′ 上的投影，并记为 `proj` ((`c` `d`)′)

（`a` `b`）′ 与 （`e` `f`）′ 的内积也可由行向量与列向量的乘积给出：(`a`* `b`*) (`e` `f`)′，且其等于零，因为，

`a`* `e` + `b`* `f` = `a`* `c` + `b`* `d` − (‖`a`‖²+‖`b`‖²)(`c``a`*+`b`*`d`)/(‖`a`‖²+‖`b`‖²) = 0.

![Equation](img/F000126si17.png)

最后，在该过程中，二乘二矩阵中的每一列结果都应进行归一化。归一化如下所示，涉及归一化前的矩阵和归一化后的矩阵，按顺序给出：

```
\begin{array}{rrrr}
{|a} & {e|} & {|{a/\\left( {\\left\\| a \\right\\|^{2} + \\left\\| b \\right\\|^{2}} \\right)^{1/2}}} & {{e/\\left( {\\left\\| e \\right\\|^{2} + \\left\\| f \\right\\|^{2}} \\right)^{1/2}}|}
\\ {|b} & {f|} & {|{b/\\left( {\\left\\| a \\right\\|^{2} + \\left\\| b \\right\\|^{2}} \\right)^{1/2}}} & {{{f/\\left( {\\left\\| e \\right\\|^{2} + \\left\\| f \\right\\|^{2}} \\right)^{1/2}}|}.}
\\ \\end{array}
```

![Equation](img/F000126si18.png)

令 `x`=(‖`a`‖² + ‖`b`‖²)^(1/2)，`y`=(‖`e`‖² + ‖`f`‖²)^(1/2)，并且令：

`v`=(`c` `a`* + `b`* `d`)/(‖`a`‖²\+ ‖`b`‖²)；那么，最后的矩阵可更有效地写成 `A`=

```
\begin{matrix}
{|{a/x}} & {{e/y}|}
\\ {|{b/x}} & {{{f/y}|}.}
\\ \\end{matrix}
```

![Equation](img/F000126si19.png)

由于 `ad`−`bc`=1，`e`/`y`=(`c`−`a` `v`)/`y` 且 `f`/`y`=(`d`−`b` `v`)/`y`，因此乘积为：

(`a` `f`)/(`x` `y`)=(`a` `d`−`a` `b` `v`)/(`x` `y`) and (`b` `e`)/(`x` `y`)=(`b` `c`−`a` `b` `v`)/(`x` `y`)，相减得到行列式 (`a` `d`−`bc`)/(`x` `y`)=1/(`x` `y`)。然而，要看出行列式为一，只需简单计算 `A`* `A`=`I`，从而得到单位矩阵。

为了展示形变收缩 `D`，必须证明从 `SL(2, C)` 到 `SU(2)` 的收缩变换是连续发生的。这将使用 `A` 的列 `A1` 和 `A2` 来进行。考虑 `t` 在 [0, 1] 中，并 somewhat 反向使用 `Gram-Schmidt`；令 `F` (`A1`, `A2`)=(`A1`/‖`A1`‖^(`t`) `A2`/‖`A1`‖^(`t`)) 对于 `t`: 0 → 1。矩阵仍保持在 `SL(2, C)` 中，并最终得到归一化的第一列 `B1`。接下来，使用投影，令 `G`(`B1`, `A2`)=(`B1`, `A2`−`t` `proj`(`A2`))；该矩阵对所有 `t` 在 [0, 1] 中均在 `SL(2, C)` 中，且对于 `t`=1；第二列变得与第一列正交。`Gram-Schmidt` 正交归一方法通过 `H` 完成，即第二列的归一化，如同之前一样。最后，这三个映射的复合 `D`=`H` `G` `F` 显示了从 `SL(2, C)` 到 `SU(2, C)` 的同伦。因此，`SL(2, C)` 也是单连通的（吉尔莫尔，1974）。

### 示例 11.17

再次考虑由特殊酉李群 `SU(2, C)` 的元素组成的载体集合。以下是 `SU(2, C)` 中的典型矩阵 `A`，随后是 `X` 和 `Z` `Pauli` 矩阵：

```
\begin{matrix}
{|z} & {{- w \\ast}|} & {|0} & {1|} & {|1} & {\\quad 0|}
\\ {|w} & {{\\mspace{23mu} z \\ast}|} & {|1} & {0|} & {|0} & {{{- 1}|}.}
\\ \\end{matrix}
```

![Equation](img/F000126si20.png)

如果用极坐标替换矩阵 `A` 中的复数 `z` 和 `w`，则 `z`=`r` e^( `i a` ) 且 `w`=`s` i e^( `i b` )，其中 `r`、`s`、`a` 和 `b` 为实数。取 `r`=cos(`t`) 且 `s`=sin(`t`)，其中 `t` 在 0, 2*π*) 中，并注意 `r`² + `s`²\=1。则酉矩阵 `A` 可用 `Pauli` 矩阵 `X` 和 `Z` 表示为 `A`=cos(`t`) e^( `i a Z` ) + sin(`t`) `X` e^( `i b Z` )。由于 `Z` 是对角矩阵，因此 e^( `i a Z` ) 也是对角矩阵，e^( `i b Z` ) 亦然。矩阵 e^( `i a Z` ) 如下给出，随后是矩阵 `A`：

```
\begin{matrix}
{|e^{ia}} & {\\quad 0|} & {|{\\cos\\left( t \\right)e^{ia}}} & {{{isin}\\left( t \\right)e^{- ib}}|}
\\ {|0} & {e^{- ia}|} & {|{{isin}\\left( t \\right)e^{ib}}} & {{\\cos\\left( t \\right)e^{- ia}}|}
\\ \\end{matrix}
```

![Equatione^( `i a Z` ) 的矩阵表示的合理性最容易通过幂级数展开看出。矩阵的更复杂函数最好使用 Frobenius 协变式以及 Lagrange-Sylvester 展开来执行，详见第 5.5 节。### 示例 11.18 实元素 n×n 矩阵 `A` 的李群 `O(n, R)` 满足 `A A′`=`A′ A`=`I`。这里，`A′` 是 `A` 的转置。此外，`A` 的列构成一组标准正交集。`A` 在 `O(n, R)` 中的充要条件是对于所有 `v`、`w` 在 `R`^( `n` ) 中都有 <`A v`, `A w`>=<`v`, `w`>。该群是紧致的，但不连通。该群中矩阵的行列式取值为正负一；这两个值对应于两个分支中的每一个。其中一个包含单位元并导致子群 `SO(n, R)`。作为另一个连通分支中矩阵的例子，考虑载体集合 (`O(2, R)`−`SO(2, R)`)。设 `A` 在此集合中；则典型矩阵是反射，例如 `A`=```\begin{array}{ll}{|{- 1}} & {0|}\\ {|0} & {1|}\\ \\end{array}```![Equation](img/F000126si22.png)

那么，对于 `R`² 中的向量 `v`，其中 `v`=(`a` `b`)′，则 `A` `v`= (−`a` `b`)，这关于 x 轴的反射。

### 示例 11.19

特殊正交李群是 `SO(n, R)`；它是 `O(n, R)` 的子群，矩阵 `A` 的行列式为一。它是保持空间定向的子群，也称为直接等距。它也是紧致且连通的。但它不是单连通的（霍尔，2015）。作为具体例子，考虑载体集合 `SO(3, R)`，它是旋转群。拓扑上，该空间是实射影空间 `RP3`。该群有许多相关图表，产生不同的参数化，每种都导致三维旋转。一些参数化涉及四个参数，一些涉及三个，但不可能只有两个变量的参数化。欧拉定理规定 `R`³ 中的任意旋转都可以用三个参数产生。在这种情况下，两个角度给出旋转轴，第三个给出实际的旋转角度本身（Palais 等，2008）。

这些参数化在 `R`³ 流形上的局部使用是有效的，但在全局参数化时常伴随奇点。三参数实现之一是欧拉角矩阵。这些是三个矩阵，每个都产生关于坐标轴 x、y 和 z 的旋转，轴的参数分别称为欧拉角 `a`、`b` 和 `d`。这里给出的三个相应的欧拉矩阵按旋转轴 x、y 和 z 的顺序指定，如下所示：

```
\begin{array}{rrrrrrrrr}
{|1} & 0 & {0|} & {|{{cb}\\mspace{22mu}}} & 0 & {{sb}|} & {|{cd}} & {- \\text{sd}} & {0|}
\\ {|0} & {ca} & {{- {sa}}|} & {|0\\mspace{31mu}} & 1 & {0|} & {|{sd}} & {cd} & {0|}
\\ {|0} & {sa} & {{ca}|} & {|{- {sb}}} & {0.} & {{cb}|} & {|0} & 0 & {1|}
\\ \\end{array}
```

![Equation](img/F000126si23.png)



The notation specified here is `ca`, which is the cosine of `a`; `sa` represents the sine of `a`; and so on. All three of these rotation matrices are multiplied in some order providing a general rotation in `R³`. Distinct applications of these matrices use one of the 24 different combinations due to the choice of axes of rotation, as well as the order of application of the individual matrices. Usually, this is not a problem; however, the gimbal lock is. Gimbal lock is where singularities occur in the sense that a degree of freedom is lost due to a specific matrix configuration. Technically, it occurs due to the lack of a covering map relating the three Euler angles with the rotation space. Specifically, the mapping is not a homeomorphism at certain points. The loss of a degree of freedom is illustrated utilizing the three Euler angle matrices given earlier. Prior to multiplying these matrices in the exact order from left to right, as illustrated earlier, `x`, `y`, and then `z`, use in the matrix for `y` the angle for `b`, as `b=` `π` `/2`; this gives `cb` = `cos(b)` = 0 and `sb` = `sin(b)` = 1. Then multiplying these matrices, `x` `y` `z`, yields the matrix of the product, `Y`. The same result would occur if the three matrices were first multiplied, and then the angle for `b` was substituted. The result is `Y`, which is given as follows:

$\\begin{array}{lll} {|0} & 0 & {1|} \\\\ {|{s\\left( {a + d} \\right)}} & {c\\left( {a + d} \\right)} & {0|} \\\\ {|{- c\\left( {a + d} \\right)}} & {s\\left( {a + d} \\right)} & {{0|}.} \\\\ \\end{array}$

![方程](img/F000126si24.png)

As can be seen from the above matrix `Y`, the three degrees of freedom for rotation are gone. When there are changes in `b`, there is no effect; the matrix stays the same. A primary application for the use of these types of matrices is in strap-down inertial navigation using gyroscopes and accelerometers, but no gimbals. Each of the Euler matrices is employed for either a roll, pitch, or yaw action for the craft. All these actions could range from zero to three hundred and sixty degrees.

In this application, because of the singularities with Euler matrices, quaternions are often employed instead with `SCALAR` equal to the reals, and `VECTOR` being the quaternions. Here, the quaternion for `q = a + bi + cj + dk` is normalized, that is, ‖q‖²\=1; this type of quaternion is also called a versor. Also let `s = 1/‖q‖²`. Then, the quaternion four-parameter matrix for rotation replaces the Euler matrices. The well-known quaternion matrix for rotation is as follows:

$\\begin{array}{lll} {|{1 - 2s\\left( {c^{2} + d^{2}} \\right)}} & {2s\\left( {{bc} - {da}} \\right)} & {{\\mspace{31mu} 2s\\left( {{bd} + {ca}} \\right)}|} \\\\ {|{2s\\left( {{bc} + {da}} \\right)}} & {1 - 2s\\left( {b^{2} + d^{2}} \\right)} & {{\\mspace{31mu} 2s\\left( {{cd} - {ba}} \\right)}|} \\\\ {|{2s\\left( {{bd} + {ca}} \\right)}} & {2s\\left( {{cd} + {ba}} \\right)} & {{1 - 2s\\left( {b^{2} + c^{2}} \\right)}|} \\\\ \\end{array}$

![方程](img/F000126si25.png)

In the strap-down application just mentioned, this matrix takes the place of the mechanical gimbals. Moreover, the gyroscopes that are rigidly fastened to the craft provide the angular velocity in the form `ω` or actually small angle changes. This allows the quaternion matrix to change according to the derivative involving the quaternion equation: `dq/dt = −ω q` (Giardina, 1973).

## 11.8 李群与李代数之间的映射

Often, there correspond several Lie groups associated with a single Lie algebra. The correspondence is very exact; from all Lie groups, a linearization can be conducted to determine the unique Lie algebra, at least in a categorial manner. On the other hand, there is an exponential map involving the Lie algebra to distinguish each Lie group. Referring to 图 11.4, an illustration is given of a many-to-one mapping from Lie groups to a Lie algebra. In this figure, observe that there is a linear map `LIN`, which goes from each Lie group to the Lie algebra. Also, there is an exponential map from the Lie algebra `g` to each of the Lie groups, `G`.

![图 11.4 李群与李代数之间的映射。](img/F000126f11-04-9780443136979.jpg)

图 11.4 李群与李代数之间的映射。

One of the principal techniques for creating the Lie algebra `g` corresponding to a specific Lie group `G` will be described later in a formal manner. It involves a topologically closed subgroup `G` of the general linear group `GL(n, R)`. Closure in this development is extremely important. In this case, `g = {X, such that X is in gl(n, R) where e^(tX) is in G for all t in R}`. Moreover, `g` is the tangent vector space to `G` at `I`. Additionally, the mapping `exp: g → G` is locally invertible. This tangent space procedure is outlined next for general Lie matrix groups. This is similar to Example 11.4 where the tangent line is created for the circle `U(1)=S¹`. Examples are given in a formal manner, using the complex field, the real field, as well as over the quaternion skew field. Moreover, only matrix groups are considered, and all groups are assumed to be closed in the topology.

The linearization map `LIN` illustrated in 图 11.4 is obtained using the differentiation of smooth paths associated with the Lie group `G`. First is a smooth path `p: R¹ → G`, where `G` is the matrix Lie group, `p: [−r, r] → G` for some small value `r`. In addition, `p(0)=I`, the identity element in `G`. Next, the tangent space is formerly used. It is the set of all equivalence classes, each consisting of all smooth paths in `G` with the same derivative at `t=0`. In a nutshell, the tangent space will be a vector space; however, it is isomorphic to what is called the Lie algebra associated with the Lie group `G`. A rigorous presentation of this and the following description involving tangent spaces can be found in Hall (2013).

For a matrix Lie group `G`, the tangent space at the identity is denoted by `T(G)`. Let `p(t)` and `q(t)` be smooth paths in `G`. Assume that the derivatives evaluated at zero are given by `dp(0)/dt = v` and `dq(0)/dt = w`, with `p(0)=q(0)=1`. `T(G)` is a real vector space. This follows by first letting `v` and `w` be in `T(G)`. To see that `v + w` is in `T(G)`, consider `s(t)=p(t) q(t)` then differentiating, using Leibnitz’s rule: `s′=p′ q + p q′`. Here, the prime indicates the first derivative. Evaluating at zero gives `s′(0)=p′(0) + q′(0)=v + w`, so the sum is in `T(G)`. Equivalently, use `f(t)=e^(tv) e^(tw)` in `G` for all real `t` in `R`, where `f(0)=I`. Taking the derivative `df/dt` gives `v e + e^(tv) w e^(tw)`. Evaluating at zero gives `v + w`, again. To see that a real scalar `c` times `v` is in `T(G)`, consider `s(t)=p(ct)`, then `s′(t)=c p′(t)`, evaluating at `t=0` gives `c v`, showing this in `T(G)`. Alternately, consider `g(t)=e^(t c v)` in `G`; here `g(0)=I` and `dg/dt` evaluated at the origin gives `c v`; thus, `T(G)` is a vector space.

For any matrix Lie group `G`, the tangent space `T(G)` becomes a Lie algebra whenever the Lie bracket is the commutator: `[X, Y]=X Y−Y X`, for `X` and `Y` in `G`. The associated Lie algebra is denoted by `g`. To see this is a Lie algebra, the `CBH` formula will be employed so let `h(t)=e^(X t^(1/2)) e^(Y t^(1/2)) e^(−X t^(1/2)) e^(−Y t^(1/2))`![方程](img/F000126si26.png). Then using `CBH` gives `h(t)=e^(X t^(1/2)+Y t^(1/2)+1/2[X,Y]+O(t^(3/2))) e^(−X t^(1/2)−Y t^(1/2)+1/2[X,Y]+O(t^(3/2)))`![方程](img/F000126si27.png), the `t^(1/2)`![方程](img/F000126si28.png) terms cancel.



再次应用 CBH 得到 `h(t) = e^((t[X, Y] − t[X + Y, X + Y] + O(t^(3/2))))` ![方程](img/F000126si29.png)，但 `[X + Y, X + Y]=0`。现在对 `h(t) = e^((t[X, Y] + O(t^(3/2))))` ![方程](img/F000126si30.png) 求导得到 `h′(t) = ([X,Y]+O(t^(1/2)))e^((t[X, Y] + O(t^(3/2))))` ![方程](img/F000126si31.png)。在 `t=0` 处求值得到 `[X, Y]`。

提供若干示例说明重要李群的切空间和切向量计算。随后，对应于其中一些李群构造了李代数。

### Example 11.20
四元数构成一个李群 `SLC(1, Q)`。四元数在单位元处的切空间是所有向量部的集合。为说明这一点，设 `q(t)` 具有光滑路径且 `q(0)=1`。注意 `q(t) q*(t)=1`；然后求导得到 `q′ q*+q q*′=0`，于是代入 `t=0` 得到 `q′(0)+q*′(0)=0`。使用标量 `q0` 加向量 `v` 表示四元数。由此可得 `q′0(0) + v′(0) + q0*′(0) + v*′(0)=0`，但 `v′(0)=−v*′(0)`，因此 `q` 的实部为 0。所以在 `1` 处的切向量是 `q` 的向量部。

四元数的李代数 `g` 使用交换子李括号求得。由于 `[i, j]=2k`，`[j, k]=2i`，`[k, i]=2j`。这与 `R³` 中的叉积代数同构，`[i, j]=2 i x j`，`[j, k]=2 j x k`，`[k, i]=2 k x i`。

### Example 11.21
切向量经过单位元，即它们经过李群的单位元。在 `O(n, R)` 中，切向量使用具有光滑路径且 `A(0)=I` 的矩阵 `A(t)` 求得。由于对所有 `t` 都有 `A A*=I`，因此求导得到 `A′ A*+A A*′=0`，其中撇号再次表示导数。然后，代入 `t=0` 得到 `A′(0)+A*′(0)=0`。使用载体集合 `O(3, R)` 并作为示例采用下面给出的欧拉矩阵 `A`，以及导数 `A′` 和 `A′(0) + A*′(0)`。

按顺序显示，这些矩阵如下：

$\\begin{array}{lllllllll} {|{\\cos\\left( t \\right)}} & { - \\sin\\left( t \\right)} & {0|} & {|{ - \\sin\\left( t \\right)}} & {- \\cos\\left( t \\right)} & {0|} & {|0} & 0 & {0|} \\\\ {|{\\sin\\left( t \\right)}} & {\\cos\\left( t \\right)} & {0|} & {|{\\cos\\left( t \\right)}} & {- \\sin\\left( t \\right)} & {0|} & {|0} & 0 & {0|} \\\\ {|0} & 0 & {1|} & {|0} & { 0} & {0|} & {|0} & 0 & {{0|}.} \\\\ \\end{array}$

![方程](img/F000126si32.png)

设 `t=0` 处的切向量为 `v`，其中 `v=A′(0)`；无论如何，可得 `v + v*` 等于零。

### Example 11.22
对于李群 `U(n, C)` 通过单位元的切向量 `v`，使用具有光滑路径且 `B(0)=I` 的矩阵 `B(t)` 求得。由于对所有 `t` 都有 `B B*=I`，求导得到 `B′ B* + B B*′=0`；代入 `t=0` 得到 `B′(0) + B*′(0)=0`。同前，设 `t=0` 处的切向量为 `v`；它再次是一个 `n` by `n` 矩阵。这次 `v=B′(0)`；无论如何可得 `v + v*` 等于零。

### Example 11.23
与前两个示例类似，`SO(n, R)` 的切空间再次由 `n` by `n` 矩阵 `v` 组成，且 `v+v*=0`。这里的切空间记为 `T(SO(n, R))`，实际上是使用交换子的李代数。因此也考虑 `T(SO(n, R))` 中的 `w`；则 `w*=−w`；李括号也必须满足此恒等式。为说明这一点，则 `u*=[v, w]*=(v w)*−(w v)*=w*v*−v*w*=w v−v w=−[v, w]=−u`。这表明这是一个李代数，记为 `so(n, R)`。该代数的维数为 `n(n−1)/2`。

使用载体集合 `SO(3, R)`，并作为 `u* + u=0` 的示例，考虑下面给出的欧拉矩阵 `A`。随后是导数 `A′` 以及 `A′(0) + A*′(0)`，全部按顺序显示：

$\\begin{matrix} {|{\\cos\\left( t \\right)}} & {- \\sin\\left( t \\right)} & {0|} & {|{- \\sin\\left( t \\right)}} & {- \\cos\\left( t \\right)} & {0|} & {|0} & 0 & {0|} \\\\ {|{\\sin\\left( t \\right)}} & {\\cos\\left( t \\right)} & {0|} & {|{\\cos\\left( t \\right)}} & {- \\sin\\left( t \\right)} & {0|} & {|0} & 0 & {0|} \\\\ {|0} & 0 & {1|} & {|0} & 0 & {0|} & {|0} & 0 & {{0|}.} \\\\ \\end{matrix}$

![方程](img/F000126si33.png)

对于任意满足 `M + M*=0` 的 `n` by `n` 矩阵 `M`，存在矩阵函数 `A(t)=e^(tM)`，且它属于 `O(n, R)`。这可以形式上看出，因为 `M` 与 `M*` 可交换，因为 `M*=−M`。由幂级数展开可得 `(e^(M))*=e^(M*)`，因此 `e^(M) e^(M)* = e^((M+M*))=e⁰=I`。这表明 `e^(M)` 属于 `O(n, R)`。使用 `tM + tM*` 说明了所需结果。此外，由于 `A(t)` 连续，这意味着行列式也连续。因为 `A(t)` 在正交群中，行列式为一或负一。然而，`A(0)=I` 表明 `det(A(t))=1` 对所有 `t` 成立。

### Example 11.24
酉李群 `U(n, C)` 的切空间是所有满足 `M + M*=0` 的 `n` by `n` 矩阵 `M` 的向量切空间。此外，李代数 `u(n, C)` 是 `T(U(n, C))` 中所有满足李括号交换子运算的切向量。该空间的维数为 `n²`。

### Example 11.25
特殊酉群 `SU(n, C)` 的切空间由所有满足 `M + M*=0` 且迹 `M=0` 的 `n` by `n` 矩阵 `M` 组成。这可以通过令 `A(t)=e^(tM)` 看出。首先注意导数 `A′(t)=M e^(tM)`，代入 `t=0` 得到 `A′(0)=M`。考虑 `A(t) A*(t)=e^((tM+tM*))=e⁰=I`。这表明 `A(t)` 属于 `U(n, C)`。其次，由于 `det(e^(tM))=e^(tr(tM))=e⁰=1`，这表明 `A(t)` 属于 `SU(n, C)`。反过来，由于 `SU(n, C)` 是 `U(n, C)` 的子集，可得 `M + M*=0`。利用 `e^(M)` 属于 `SU(n, C)` 的事实，意味着 `det(e^(M))=I`。利用行列式与迹的关系得到 `e^(tr(M))=I`，因此 `tr(M)=0`。由此可知，所有此类矩阵 `M` 的空间使用交换子李括号构成李代数 `su(n, C)`。该代数的维数为 `n²–1`。

已知其李代数求得李群的过程比从给定李群求李代数更困难。首先，单个李代数可能对应多个李群。然而，更重要的是，该过程更复杂，因为它包含两个步骤。第一步是解决局部化问题。也就是说，关于李群已知的唯一信息是其矩阵维数。此外，它有一个单位元，记为 `I`，目标是找到 `I` 附近的其他群元素。此步骤涉及李代数中的一个元素和一个等距映射，该映射提供了单位矩阵附近无穷小矩阵的结构。下一步是寻找一般群元素。此步骤涉及李代数中的基元素以及指数函数的幂级数展开。对于简单情况，该级数使用标准微积分技术求和，从而得到矩阵李群中的一般元素。

下一个示例将说明李群 `SU(2, C)` 如何由 `su(2, C)` 得到。它从 `u(2, C)` 开始，然后用泡利矩阵表示群 `U(2, C)` 的局部表示。然后对行列式施加约束得到群 `SU(2, C)` 的局部表示。最后，指数映射提供全局表示。

### Example 11.26



# 李代数和李群示例

在本例中，首先使用 2×2 斜自伴矩阵的李代数 `u(2, C)`。为了确定具有 `u(2, C)` 作为其李代数的李群，取任意 2×2 矩阵 `M`，其元素可任意小。然后，`I + M = U` 是一个元素，即它是所求群单位元邻域中的一个矩阵。因此，设 `U* I U = I`；这等于 `I + M* + M + M* M = I`。这是保度量性质。乘积项很小，因此将其设为零得到 `M* = -M`。因此，矩阵 `M` 必须是斜厄米的，即斜自伴的。因此，使用小的实数：`p`、`q`、`a` 和 `b`，则 `M` 的形式如下所示，随后是 `-i M`，并且经过轻微修改后，仍由 `-i M` 给出。这些矩阵按顺序示出；然而，在最后一个表达式中对两个实数 `p` 和 `q` 进行了替换。它们写为 `p = c' + d'`、`q = c' - d'`，其中 `c'` 和 `d'` 为实数:-

$\\begin{array}{lll} \\begin{array}{ll} {|{pi}} & {{b - \\text{ai}}|} \\\\ {|{- b - \\text{ai}}} & {{\\mspace{23mu}{qi}.}|} \\\\ \\end{array} & \\begin{array}{ll} {|p} & {{- a - \\text{ib}}|} \\\\ {|{- a + \\text{bi}}} & {\\mspace{29mu}{q|}} \\\\ \\end{array} & \\begin{array}{ll} {|{c' + d'}} & {{- a - \\text{ib}}|} \\\\ {|{- a + {bi}}} & {{\\quad c' - d'}|} \\\\ \\end{array} \\\\ \\end{array}$

![方程](img/F000126si34.png)

最后一个矩阵将用 2×2 单位矩阵 `I` 以及前一章中指定的三个修正的泡利矩阵 `M1`、`M2` 和 `M3` 来描述。这些矩阵按顺序如下所示：`M1 = i s1`、`M2 = -i s2` 和 `M3 = i s3`。

$\\begin{array}{rrrrrr} {|0} & {i|} & {|0} & {{- 1}|} & {|i} & {0|} \\\\ {|i} & {0|} & {|1} & {0|} & {|0} & {{- 1}|} \\\\ \\end{array}$

![方程](img/F000126si35.png)

泡利矩阵将在另一次除以二时被修改，但首先注意 `-i M = c' I + a i M1 + i b M2 - d' i M3`。因此，`M = -c' i I + a M1 + b M2 - d' M3`。

群 `SU(2, C)` 是 `U(2, C)` 的子群，但其行列式等于一。取 `det(I + M)`，但仅保留线性项得到 `1 + p i + q i`。这导致 `p + q = 0`，即 `c' = 0`。因此，一阶时，矩阵 `M` 只涉及三个泡利矩阵，而不涉及单位矩阵。因此，`SU(2, C)` 只有三个实参数 `a`、`b` 和 `d'`。这些参数提供了李群流形上的坐标。矩阵 `M` 生成 `SU(2, C)` 中的任意无穷小元素。

为了执行指数映射，当需要 `SU(2, C)` 中的一般矩阵时，结构常数和爱因斯坦记号很有用。基本上，`M = a_j M_j` 是和 `M = a M1 + b M2 + d M3` 的简写。这里，`a1 = a`、`a2 = b` 和 `a3 = d`，均在 `C` 中。因此 `I + a_j M_j` 生成 `SU(2, C)` 中单位元 `I` 附近的任意元素。群的一般元素是 `e^(M)`，它是求和 $\\sum\_{n = 0}^{\\infty}\\left( {M^{n}/{n!}} \\right)$![方程](img/F000126si36.png)。在 `M` 中，代入三个修正的泡利矩阵，`M1 = (i s1) /2`、`M2 = (-i s2) /2` 和 `M3 = (i s3) /2`。回忆泡利矩阵 `s_j` 具有良好的性质；它们满足 `M² = - ((a² + b² + d'²)/2) I`。这因为泊松括号 `{s_i, s_j}=0` 当 i 不等于 j 时，否则为 1。接下来写 `M² = - d²/2 I`，其中 `d² = (a² + b² + d²')`。现在 `e^(M)` 的求和应分解为偶项和奇项，分别记为 `Even` 和 `Odd`。此外，求和的指标未显示，并采用爱因斯坦型记号。因此 `e^(M) = e^(i a_j s_j) = Even + Odd`。利用恒等式 `M² = - d²/2 I` 得到偶数情况 `= I cos(d/2)`，奇数情况 `= i (a_j s_j) sin(d/2) = i (a s1 + b s2 + d' s3) sin(d/2)`。将偶项和奇项表达式结合起来给出 `SU(2, C)` 的最一般元素。在代入泡利矩阵 `s_j` 后，这给出 `SU(2, C)` 的一般矩阵结构；称此矩阵为 `T`：

$\\begin{array}{ll} {|{\\cos\\left( {d/2} \\right) + \\text{id}'\\sin\\left( {d/2} \\right)}} & {{b\\sin\\left( {d/2} \\right) + {ia}\\sin\\left( {d/2} \\right)}|} \\\\ {|{b\\sin\\left( {d/2} \\right) + {ia}\\sin\\left( {d/2} \\right)}} & {{{\\cos\\left( {d/2} \\right) - \\text{id}'\\sin\\left( {d/2} \\right)}|}.} \\\\ \\end{array}$

![方程](img/F000126si37.png)

关于此矩阵的一个重要事实是当 `d = 0` 时，得到单位元。然而，当 `d = 2 * pi` 时，得到负单位元。单位元 `I` 和 `-I` 都与 `SU(2, C)` 中的任意矩阵交换。回忆子群 `{I, -I}` 称为 `SU(2, C)` 的中心；它是与 `SU(2, C)` 中所有元素交换的最大子群。群 `SU(2, C)` 也是紧致的，因为前面提到的该矩阵的所有可能取值都在三维流形中半径为 `2 * pi` 的闭球内实现。此外，在该球的边界上的任何位置，只有一个矩阵。也就是说，在球的所有边界点上，对应的矩阵都相等。

### 示例 11.27

为了求 `U(2, C)`，大部分工作已在前一示例中完成。这里唯一要做的是对李代数 `u(2, C)` 的四个基元素进行指数化。在前一示例中，已求得 `e^(M) = e^(i a_j s_j)`。在本例中，需要求 `e^(i/2 c' I + i a_j s_j)`![方程](img/F000126si38.png)。因为 `I` 与所有泡利矩阵交换，所以有 `e^(i/2 c' I + i a_j s_j) = e^(i/2 c' I) e^(i a_j s_j)`![方程](img/F000126si39.png)。现在唯一需要确定的是一次指数 `e^(i/2 c' I) =`![方程](img/F000126si40.png)

$\\begin{array}{ll} {|e^{{ic'}/2}} & {\\mspace{25mu} 0|} \\\\ {|0} & {{e^{{ic'}/2}|}.} \\\\ \\end{array}$

![方程](img/F000126si41.png)

将此矩阵与示例 11.26 的结果，即矩阵 `T` 相乘，得到 `U(2, C)` 的典型矩阵。

### 示例 11.28

现在，`SO(3, R)` 将从示例 11.25 中给出的同一李代数 `su(n, C)` 求得。再次，度量的变换必须是不变的。在本例中，由于使用实数域，变换是涉及正交矩阵 `O` 及其转置 `O'` 的相似变换。因此，存在正交矩阵 `O`，使得对于所求群中的任意矩阵 `B`，有 `O' B O = B`。再次，使用 3×3 矩阵 `M` 中的小元素并代入 `O = I + M` 得到 `M + M' = 0`，因此 `M` 是斜对称的。因此，使用小的实数值 `a`、`b` 和 `c`，可得 `M =`

$\\begin{array}{lll} {|0} & c & {{- b}|} \\\\ {|{- c}} & 0 & {\\mspace{22mu} a|} \\\\ {|b} & {- a} & {{\\mspace{22mu} 0|}.} \\\\ \\end{array}$

![方程](img/F000126si42.png)

该矩阵可以用斜对称基 `X1`、`X2` 和 `X3` 表示，如下所示。第一个涉及标量 `a`，下一个为值 `b`，最后为值 `c`：

$\\begin{array}{rrrrrrrrr} {|0} & 0 & {0|} & {|0} & 0 & {{- 1}|} & {|0\\mspace{22mu}} & 1 & {0|} \\\\ {|0} & 0 & {1|} & {|0} & 0 & {0|} & {|{- 1}} & 0 & {0|} \\\\ {|0} & {- 1} & {0|} & {|1} & 0 & {0|} & {|0\\mspace{22mu}} & 0 & {0|} \\\\ \\end{array}$

![方程](img/F000126si43.png)



`M=aX1 + bX2 + cX3`，或用爱因斯坦型记号表示 `M=aj Xj`。注意在此例中 `a1=a`、`a2=b` 且 `a3=c`。利用李括号得到 `\[Xi, Xj\]=−Eijk Xk`，其中再次使用了 Levi-Civita 符号。对于 `SO(3, R)`，行列式必须为一。取 `det(I + M)`，将其设为一并保留至线性项，仅得到一。因此不需要其他约束。再次使用爱因斯坦记号，利用指数得到一个实际的群元素，`e^(ajXj)`![方程](img/F000126si44.png`)。在展开之前，采用特征方程的 Cayley-Hamilton 形式得到 `M³ + d² M=0`，其中 `d²=(a² + b² +c²)`。与前一个问题类似，`M³=−d² M` 用于更快地对指数的级数求和。再次，对 `e^(ajXj)`![方程](img/F000126si45.png`) 的级数使用偶项和奇项。持续将 `–d² M` 代替 `M³`。可利用简单的幂级数近似来证明 `e^(ajXj)=I + ajXj sin(d) + (ajXj)²(1−cos(d))`。现在，代入基元素 `Xj`，记住 `ajXj=a X1 + b X2 + c X3`，且 `d²=(a² + b² + c²)`，最后对 `ajXj` 平方并代入得到 `e^(ajXj)`![方程](img/F000126si46.png`) 作为如下三乘三矩阵：
```
$\\begin{array}{lll} {|{1 - \\left( {b^{2} + c^{2}} \\right)\\left( {1 - \\cos\\left( d \\right)} \\right)}} & {{ab}\\left( {1 - \\cos\\left( d \\right)} \\right) + d^{3}\\sin\\left( d \\right)} & {{{ac}\\left( {1 - \\cos\\left( d \\right)} \\right) - d^{2}\\sin\\left( d \\right)}|} \\\\ {|{{ab}\\left( {1 - \\cos\\left( d \\right)} \\right) - d^{3}\\sin\\left( d \\right)}} & {1 - \\left( {a^{2} + c^{2}} \\right)\\left( {1 - \\cos\\left( d \\right)} \\right)} & {{{cb}\\left( {1 - \\cos\\left( d \\right)} \\right) + {dsin}\\left( d \\right)}|} \\\\ {|{{ac}\\left( {1 - \\cos\\left( d \\right)} \\right) + d^{2}\\sin\\left( d \\right)}} & {{cb}\\left( {1 - \\cos\\left( d \\right)} \\right) + {dsin}\\left( d \\right)} & {{ 1 + \\left( {b^{2} + a^{2}} \\right)\\left( {1 - \\cos\\left( d \\right)} \\right)}|} \\\\ \\end{array}$
```
![方程](img/F000126si47.png`)
这是 `SO(3, R)` 的一个一般元素。这里注意，当 `d=0` 时，得到单位矩阵 `I`。这对应于三维流形表示的原点。当 `d=π` 时，`e^(ajXj)=`
```
$\\begin{matrix} {|{1 - {({b^{2} + c^{2}})}{(2)}}} & {{ab}{(2)}} & {{\\mspace{72mu}{ac}{(2)}}|} \\\\ {|{{ab}{(2)\\mspace{76mu}}}} & {{1 - {({a^{2} + c^{2}})}{(2)}})} & {{\\mspace{72mu}{cb}{(2)}}|} \\\\ {|{{ac}{(2)\\mspace{76mu}}}} & {{cb}{(2)}} & {{{1 + {({b^{2} + a^{2}})}{(2)}}|}.} \\\\ \\end{matrix}$
```
![方程](img/F000126si48.png`)
该矩阵对流形中的对径点也成立。在此情况下，`d=π`，且坐标变量 `a`、`b` 和 `c` 现在均为负值。在这些条件下，当 `a`、`b` 和 `c` 为正时得到完全相同的矩阵。任何穿过原点的直线段都在半径为 `π` 的球面上与两个相反点相交。这些是对径点，且在这两个点处的矩阵 `e^(ajXj)`![方程](img/F000126si49.png`) 相同。此外，该李群是紧致的，因为一般矩阵的所有可能取值都可在该半径为 `π` 的闭球中得到。

### 示例 11.29
将会看到，一维四元数的特殊群 `SLC(1, Q)` 也具有与前述示例中给出的两个不同群相同的李代数。也就是说，`SU(2, C)` 和 `SO(3, R)`，以及群 `SLC(1, Q)` 全部具有相同的李代数 `su(2, C)`。对于 `SLC(1, Q)`，这里的元素是一乘一矩阵。四元数的单位元为 `I` 等于 `1`，因此 `q` 的向量部分 `v` 为零。接近单位元的矩阵为 `I + q`，其中 `q` 是绝对值很小的四元数，例如 `q=a0I + a1i +a2j + a3k`。在爱因斯坦记号中，`v=aksk`。李代数 `glc(1, Q)` 有四个基元素。这是一般线性代数。特殊李代数由归一化四元数组成。对该李代数进行基变换得到 `X1=−1/2i`、`X2=−1/2j` 和 `X3=−1/2k`。于是 `\[X1, X2\]=1/4(ij−ji)=1/2k=X3`。因此，`\[Xi, Xj\]= −EijkXk`。对于 `SLC(1, Q)`，需要范数为一，所以 `(1 + q) (1 + q)*=1`。相乘得到 `1 + q + q* + |q|²=1`，这意味着由于 `v=−v*` 且仅保留线性项得到 `a0=0`，仅保留小 `q` 的向量部分。
现在为了求 `SLC(1, Q)` 的一般元素，取 `e^((akXk))`![方程](img/F000126si50.png`)；这与前述示例中所做的工作类似。注意 `(ak Xk)²=(a1X1 + a2X2 + a3X3)²=(a1X1)² + (a2X2)² + (a3X3)²=−1/4 ((a1)² +(a2)² + (a3)²)= −1/4 d²`，其中 `d²=(a1)² + (a2)² + (a3)²)` 如前例所示。如前所述，使用幂级数的偶项和奇项得到 `e^(akXk)=cos(d/2) + 2akXk/d sin(d/2)=cos(d/2)−(a1i/d + a2j/d + a3k)sin(d/2)`。
如果需要 `GLC(1, Q)`，那么需要求得的就是 `e^(aOI + ajXj)`![方程](img/F000126si51.png`)；这将在下一个示例中进行。

### 示例 11.30
模仿示例 11.27 的结果，采用完全相同的程序。李群 `GLC(1, Q)` 可通过使用前面提到的 `glc(1, Q)` 中的四个基元素得到。结果通过相乘指数 `e^(aOI) e^(aXj)`![方程](img/F000126si52.png`) 找到；这得到表达式 `e^(aOI) e^(aXj)=a0(cos(d/2)−(a1i/d + a2j/d + a3k)sin(d/2))`。

## 11.9 李代数的复化
曾看到实向量空间可通过复化变为复向量空间。事实上，类型 SCALAR 的载体集合已从实数交换为复数。相应地，复数域被用于代替实数域。同时，类型 VECTOR 的载体集合被调整以包含虚部。来自签名集合中名为 S-MULT 和 V-ADD 的算子被用于根据其定义映射新元素。简而言之，标量乘法和向量加法在复运算下是封闭的。由于切空间是向量空间，向量空间复化适用。类似于希尔伯特空间的情况，tensor 积 `Hc=Hr ⊗ C` 适用。
对于李代数，李括号也必须被复化。在此情况下，对于李代数 `g` 中的 `A`、`B`、`D` 和 `E`，李括号的复化由类似于极化恒等式的形式给出：`\[A + i B, D + i E\]=[A, D]−[B, E] + i[A, E] + i[B, D]`（Humphreys, 1997）。最后，注意到矩阵 `A + Bi` 是 `A⊗1 + B⊗i` 的简写，其中 `⊗` 为张量积。因此，复化类似于仅对向量空间的复化。下面给出一个优秀的例子，使用一个被错误地假设为复代数的李代数。

### 示例 11.31
李代数 `su(n, C)` 是李括号为交换子的代数，由所有满足 `M*=−M` 的矩阵 `M` 组成。这些矩阵是斜厄米的，或斜对称且 `M` 的迹等于零。请注意该李代数不是复的；它是实的，因为作为向量空间它是实的。这可通过使用 `M`，然后 `(Mi)*=−M*i=Mi` 得到。参见向量空间定义。这里，SCALAR 类型决定向量空间是实还是复。无论如何，`su(2, C)` 中最一般的矩阵为 `M=`
```
$\\begin{array}{ll} {|{ix}} & {{- c \\ast}|} \\\\ {|c} & {{ - {ix}}|} \\\\ \\end{array}$
```
![方程](img/F000126si55.png`)
其中 `x` 为实数且 `c` 为复数。接下来给出该李代数的一个基，它们与泡利矩阵 `sj`、`j=1, 2, and 3` 相关。按顺序给出如下 `M1=is1`、`M2=−is2` 和 `M3=is3`。它们也分别记为 `X`、`Y` 和 `Z`：



$\\begin{array}{llllll} {|0} & { i|} & {|0} & {{- 1}|} & {|i} & {\\quad 0|} \\\\ {|i} & {0|} & {|1} & {\\mspace{20mu} 0|} & {|0} & {{- i}|} \\\\ \\end{array}$

![方程](img/F000126si56.png)

换位子 `\[M1, M2\]=2 M3`、`\[M2, M3\]=2 M1`，最后，`\[M3, M1\]=2 M2`。`\[Mi, Mj\]=2 Eijk Mk`。这里，列维-奇维塔符号 `Eijk` 再次被使用。李代数 `sl(2,C)=su(2,C) + su(2,C) i`。该表达式将给出 `su(2,C)` 的复化。特殊线性代数 `sl(2,C)` 中最一般的元素是 `N=`

$\\begin{matrix} {|{x + {iy}}} & {{\\mspace{22mu} u + {iv}}|} \\\\ {|{r + {is}}} & {{- x - {iy}}|} \\\\ \\end{matrix}$

![方程](img/F000126si57.png)

该矩阵具有复数值，且迹等于零。该李代数的一个基按 `N1`、`N2` 和 `N3` 的顺序如下给出：

$\\begin{array}{rrrrrr} {|1} & {0|} & {|0} & {1|} & {|0} & {0|} \\\\ {|0} & {{- 1}|} & {|0} & {0|} & {|1} & {0|} \\\\ \\end{array}$

![方程](img/F000126si58.png)

回到 `su(2, C)` 并现在利用上述基可知 `su(2, C)` 中最一般的矩阵是 `M=ixN1−c\*N2 + cN3`，因为 `M` 由以下给出：

$\\begin{matrix} {|{ix}} & {{- c \\ast}|} \\\\ {|c} & {{ - {ix}}|} \\\\ \\end{matrix}$

![方程](img/F000126si59.png)

这并不令人惊讶，因为 `su(2,C)` 是 `sl(n, C)` 的子李代数。目标是看到涉及 `su(2, C)` 复化的展开。现在考虑 `sl(2, C)` 中最一般的矩阵，它是 `N=−ixM3 + yM3−u/2 (M2 + i M1)−iv/2 (M2 + i M1) + r/2 (M2−iM1) + is/2 (M2−iM1)`。这表明两个李代数本质上是相同的。此外，注意描述 `N` 只需要 `su(2, C)` 的六个复化基元素。这六个矩阵是 `M1`、`M2`、`M3`、`iM1`、`iM2` 和 `iM3`。再次，这也是可以预期的，因为 `sl(2, C)` 在实数域上的维数是六。

## 参考文献

*   Bargmann, 1947 Bargmann V. 洛伦兹群的不可约酉表示。*Ann Math.* 1947;48n.
*   Benkart, 1977 Benkart G. 关于李代数的内理想和 ad-幂零元。*Trans Am Math Soc.* 1977;.
*   Berry, 2006 Berry, D., 2006. 用于模拟稀疏哈密顿量的高效量子算法，arXiv:quant-ph/0508139.
*   Draper and Meulewaeter, 2022 Draper C, Meulewaeter J. 实单李代数的内理想。*Bull Malaysian Math Sci Soc.* 2022;45.
*   Giardina, 1973 Giardina, C., 1973. 使用 Cayley 变换和四元数的 strapdown 导航，Singer Kearfott，报告。
*   Gilmore, 1974 Gilmore R. *李群、李代数及其某些应用* J Wiley & Sons 1974;.
*   Hall, 2013 Hall B. *数学家的量子理论*. 978-1461471158  *GTM*. Vol. 267 Springer 2013;.
*   Hall, 2015 Hall B. 978-3319134666  *李群、李代数与表示*. Vol. 222 second ed. Springer 2015;.
*   Hatcher, 2002 Hatcher A. 0-521-79540-0 *代数拓扑* Cambridge U. Press 2002;.
*   Humphreys, 1997 Humphreys J. 978-3540900535  *李代数与表示论导论*. Vol. 9 second ed. Springer 1997;.
*   Jacobson, 1979 Jacobson N. 9978-0486-63832-4 *李代数* Dover 1979;.
*   Johnson, 1976 Johnson R. 紧群在拓扑向量空间上的表示：一些注记。*Proc Am Math Soc.* 1976;61.
*   Palais et al., 2008 Palais B, et al. 对欧拉旋转轴定理的一种令人困惑的审视。*Am Math Monthly*. 2008;116(10):200.

# 第 13 章
## 算子的谱

### 摘要

展示谱存在性的判据已得到回顾。Lumer-Phillips 定理在 Banach 空间中对伴随算子和对偶算子的谱应用已给出。对点谱、连续谱以及 Banach 空间和 Hilbert 空间中的剩余谱给出了描述和示例。Hellinger-Toeplitz 定理针对无界算子陈述并举例说明，包括动量算子和距离算子。数值域相对于谱值以及耗散算子和增生算子进行了描述。给出了对称算子为自伴算子的条件。近似特征值概念连同其在紧算子上的应用被描述。Cauchy 积分定理被用于确定预解集。本章以谱测度和谱理论的介绍结束。此外，在最后一节中，举例说明了 Stieltjes 积分。并且，投影值测度相对于谱定理进行了描述。

#### 关键词

Lumer-Phillips 定理; Hellinger-Toeplitz 定理; 一参数半群; 耗散算子; 增生算子; Stieltjes 积分; 剩余谱; 近似谱; saltus

## 13.1 有界算子的谱分类

本节是 第 8.5 节 和 第 8.6 节 的延续。本章主要早期部分的主要参考文献是 Halmos (1957) 和 He’lein (2014)。在 第 8 章 中，源自第一参考文献的判据 Halmos, 1957 已给出用于说明谱的存在，具体为 Hilbert 空间 `H` 中的谱 `spT`。必要充分条件在此重复。对于算子 `T`，在 `B(H,H)` 中，`spT={c, such that c in C, and (c I−T) is not invertible iff both 1) and 2) hold}`：

1. 1) `T` 的像在 `H` 中稠密，且
2. 2) 存在标量 `a> 0` 使得对所有 `v` 在 `H` 中 `‖Tv‖>a‖v‖`。

在前面给出的第二参考文献中，判据 (1) 被称为弱满射，而第二判据 (2) 被暗示为强单射。

对于 `T`，在 `B(H,H)` 中，`T` 的谱已被证明非空并在 `C` 中形成紧集。此外，预解集 `RsT` 是 `C` 中的开集。该集合 `RsT` = {`λ`![方程](img/F000138si3.png)，其中 `λ`![方程](img/F000138si4.png) 在 `C` 中，且使得 (`T−λI`) 是单射且满射，(`T−λI`) ^(−1)![方程](img/F000138si5.png) 有界}。逆的有界性也由有界逆定理得出。该定理可在附录 A.6 中找到。此外，`spT` 的一个划分由三个不相交集合 `sppT`、`spcT` 和 `sprT` 提供。简要地，谱将对 `T` 进行描述，`T` 是不同于 `{0}` 的复 Banach 空间 `X` 上的有界算子。内积对于此发展不是必要的；因此使用 Banach 空间。提供了众多示例，并在无界情形下以形式方式给出。不考虑定义域问题。

1. 1) 点谱 `sppT={λ in C such that (T−λI) is not one to one on X}`。
2. 2) 连续谱 `spcT={λ in C such that (T−λI) is one to one on X, but it is not onto X; however, it has ran (T−λI) dense in X}`。
3. 3) 剩余谱 `sprt={λ in C such that (T−λI) is one to one and not onto, but with ran (T−λI) not dense in X}`。




## 谱类型

### 1) 点谱
对于 `sppT`，`Ker(λ I−T)` 不是 `{0}`；必须存在 `X` 中的非零向量 `f` 使得 `T f = λ f`，`f → (T−λ I)f`。该映射在 `X` 中不是一一对应的；`f` 的任意非零倍数都满足此条件，因为特征向量的任意非零标量倍仍是特征向量。在复 n 维空间中，`dim(Ran(T)) + dim(Ker(T)) = n`。此外，`X` 中的 `f` 称为特征向量，而 `λ` 称为特征值。在有限维希尔伯特空间中，仅存在这种点谱。点谱的若干例子已在有限维 Banach 或希尔伯特空间的矩阵运算中得到说明。无限维空间中点谱的最简单说明见示例 8.16。无限维希尔伯特空间中具有点谱的额外例子见 示例 13.1 和 13.2。

### 2) 连续谱
对于 `spcT`，`Ker(λ I−T)` 为 `{0}`，且 `λ I−T` 的像在 `H` 中稠密，但 `Im(λ I−T)` 不等于 `X`。等价地，`λ I−T` 在 `H` 中稠密当且仅当 `ker(λ I−T)* = {0}`。由于 `Ker(λ I−T)` 为 `{0}`，`(λ I−T)(f[1] – f[2]) = 0`；这意味着 `f[1] = f[2]`，因此 `(T−λ I)` 在 `X` 上是一一对应的。它不是满射，因为如果它是满射则 `Im(λ I−T) = X`。该谱的实例见示例 8.17 和 8.18。

### 3) 剩余谱
`Ker(λ I−T)` 为 `{0}`，`λ I−T` 的像在 `H` 中不稠密，且 `Im(λ I−T)` 不等于 `H`；则 `λ` 属于剩余谱。这意味着具有剩余谱的算子 `T` 与满射相去甚远。相关谱记为 `sprT`。非空剩余谱的例子见 示例 13.3（Stack Exchange，2016）。

### 示例 13.1
考虑 `l^(p)`，其中 `p` 在 `[1, ∞)` 中，标量在 `C` 中。对于 `C` 中有界的 `λ[1]`、`λ[2]`、`λ[3]`、…，即 `sup|λ[n]| < ∞`。设 `T` 为无限标量矩阵 `T: l^(p) → l^(p)`，`T` 在主对角线上按顺序取 `λ[n]` 的值。利用标准基可得 `T v[n] = λ[n] v[n]`，其中特征向量为 `v[n] = (0 0 … 0 1 0…)`，且 1 位于第 n 个分量位置。因此 `sppT` 是集合 `spT` 的子集。也就是说，`v[n]` 是对应于特征值 `λ[n]` 的特征向量。

在所有特征值的集合的闭包中，可能存在 `C` 中的点 `c`，且该点属于谱。如果对于所有 `λ[n]` 的集合存在极限点 `c`，则 `c` 不能在 `sppT` 中，但 `c` 在 `spT` 中。这将在所有特征值集合的闭包中发生。例如，若 `λ[n] = 1/n`，则 `0` 将属于 `T` 的谱，即它是 `sprT` 或 `spcT`。

### 示例 13.2
设 `T: l² → l²` 在复数域上。对于 `l²` 中的任意 `v`，有 `T(v1, v2, v3, …) = (v1, v2/2, v3/3, …)`。点谱为 `{1, 1/2, 1/3, …}`。这可通过写出主对角线上取值为 `1/n` 的无限标量矩阵轻松看出。利用标准基可得 `T v[n] = λ[n] v[n]`，其中特征向量为 `v[n] = (0 0 … 0 1 0…)`，且 1 的值位于第 n 个分量位置。因此 `sppT` 是集合 `spT` 的子集。也就是说，`v[n]` 是对应于特征值 `λ[n]` 的特征向量。零是特征值的极限点。因此零也属于 `spT`。

### 示例 13.3
这是一个剩余谱非空的例子。设希尔伯特空间 `H` 的载体集为 `l²`，即所有具有复数项的平方绝对可和序列的空间。对于 `T: l² → l²`，考虑 `T(v1, v2, v3, …) = (0, v1, v2/2, v3/3, …)`。这是一个右移操作。`Ker(c I - T) = {0}`。`T v1 = 0`，`T v2 = v1`，`T v3 = v2/2` …. 因此谱不为空，且零是谱点，因为不可逆准则。`T` 不是满射，因为值域中的第一个分量是固定的。若 `vn` 是第 n 个位置为 1，其余位置为 0 的单位向量，则 `T vn ---> 0`。见 Stack Exchange（2016）。注意对偶算子 `T*` 满足 `<T* w, v> = <w, T v>`。由于 `T(v1, v2, v3, …) = (0, v1, v2/2, v3/3, …)`，将其代入左侧内积得 `w1' * v1 + w2' * v2 + w3' * v3 + … = w1 ·` 接下来展开另一个内积得到 `0 + w2 v1 + w3 v2/2 + …`。这里，`wj' * = T* wj`。接下来令 `vj` 的系数相等可得 `w1' * = w2`，`w2' * = w3/2`，…. 因此，`T* (w1, w2, w3, …) = (w2, w3/2, …)`。这是一种左移型操作。

## 13.2 Banach 空间上算子的谱
当伴随算子存在时，其谱通常与原算子的谱相关。`Lumer-Phillips` 定理是确定希尔伯特和 Banach 空间中伴随算子谱的有用工具（Lumer 和 Philips，1961）。该定理在 He’lein（2014） 中被用来说明 Banach 空间中有界算子的不同谱类型。以下各节中重复了许多相同的例子。然而，首先，`Lumer-Phillips` 定理指出，在 Banach 空间 `A` 中，`T'` 为 `A` 中 `T` 的对偶算子时，谱 `spT = spT'`。此外，对于 resolvent 集 `Rs(T)` 中的 `c`，resolvent 算子 `Rc(T)' = Rc(T')`。另外，对于具有伴随 `T*` 的希尔伯特空间中的 `T`，可得 `spT* = (spT)* = {c* | c in the spectrum of T, that is, c in spT}`。最后，对于 resolvent 集 `Rs(T)` 中的 `c`，resolvent 算子：`Rc*(T*) = (Rc(T))*`。



# Banach 空间 `l¹` 及其对偶

Banach 空间 `l¹` 具有对偶空间 `l^∞`；此外，存在从 `l^∞` 到 `l¹` 对偶空间的连续同构。考虑一个连续线性算子 `ϕ`![Equation](img/F000138si15.png)，`ϕ`![Equation](img/F000138si16.png)：`l^∞`→`C`。设 `en`，`n`=0, 1, 2, …，在 `l¹` 中为基，其中 `en`=(0, 0, …0, 1, 0, …) 且在第 n 个分量处为 1，其余处为零。对于 `l¹` 中的 `v`，其中 `v`=(v0, v1, v2, …)，差的范数 $\\left\\| {v - \\sum\_{n = 0}^{N}\\left( {{vn} \\cdot {en}} \\right)} \\right\\|$![Equation](img/F000138si17.png) 小于或等于 $\\sum\_{N + 1}^{\\infty}\\left| {vn} \\right|$![Equation](img/F000138si18.png)，当 `N` 趋于无穷时趋于零，因为 `vn` 可绝对求和。现在利用 `ϕ`![Equation](img/F000138si19.png) 并运用连续性条件得到 $\\phi\\left( v \\right) = \\lim\_{N\\rightarrow\\infty}\\phi\\left. \\lbrack{\\sum\_{n = 0}^{N}\\left( {{vn} \\cdot {en}} \\right)} \\right\\rbrack = \\lim\_{N\\rightarrow\\infty}\\sum\_{n = 0}^{N}{\\left( {{vn} \\cdot \\phi\\left\\lbrack {en} \\right\\rbrack} \\right) =}\\sum\_{n = 0}^{\\infty}\\left( {{vn} \\cdot \\phi\\left\\lbrack {en} \\right\\rbrack} \\right)$![Equation](img/F000138si20.png)。由于 `ϕ`![Equation](img/F000138si21.png) 对 `l¹` 中所有 `w` 连续且 `ϕ`![Equation](img/F000138si22.png) 有界，‖`ϕ`![Equation](img/F000138si23.png)‖ 小于或等于 `c`，其中 `c`> 0。此外，|`ϕ`(`w`)| 小于或等于 ‖`ϕ`![Equation](img/F000138si24.png)‖ ‖`w`‖。特别地，|`ϕ`(`en`)| 小于或等于 ‖`ϕ`![Equation](img/F000138si25.png)‖ ‖`en`‖=`c`。因此 `ϕ`(`en`) 有界，其结果是级数 $\\phi\\left( v \\right) = \\sum\_{n = 0}^{\\infty}\\left( {{vn} \\cdot \\phi\\left\\lbrack {en} \\right\\rbrack} \\right)$![Equation](img/F000138si26.png) 绝对收敛；$\\sum\_{n = 0}^{\\infty}\\left| {{vn} \\cdot \\phi\\left\\lbrack {en} \\right\\rbrack} \\right|$![Equation](img/F000138si27.png) 小于或等于 `c` $\\sum\_{n = 0}^{\\infty}\\left| {vn} \\right|$![Equation](img/F000138si28.png)。由此可得 ∥`ϕ`∥![Equation](img/F000138si29.png) 小于 ∥`ϕ`(`e` `n`)∥![Equation](img/F000138si30.png) 因为有界算子范数是 Lipschitz 常数 `M` 的下确界，其中 ∥`ϕ`(`v`)∥![Equation](img/F000138si31.png) 小于或等于 `M`‖`v`‖。这意味着 ∥`ϕ`∥ = ∥`ϕ`(`e` `n`)∥![Equation](img/F000138si32.png)。

随后若干例子 (He’lein, 2014) 涉及 Banach 空间 `l¹` 及其对偶空间 `l^∞`。下文中，算子 `T` 的值域和像可互换使用。即 `ranT`=`imT`；它们相同。此外，算子的闭包记为 `closT`。

### 例 13.4
考虑所有绝对可求和的复值序列 `v`=(v1, v2, …) 的 Banach 空间 `l¹`。设 `L` 为左移算子 `L` (`v`)=(v2, v3, …)。对偶算子记为 `L∗`，而非记为 `L′` 以提高可读性。它在对偶空间 `I^∞` 中作用，该空间是有界序列 `w`=(w1, w2, …) 的空间。尽管内积不适用，但它将被用作运算演算工具以快速求伴随算子。因此形式上，取内积 <`w`, `L` (`v`)>=w1∗v2+w2∗v3+…. 接下来，为求 `L∗`，使用 <`L∗` (`w`), `v`> 并将该结果与前面写出的和相等，即 <`L∗` (`w`), `v`>=w1′∗v1+w2′∗v2+w3′∗v3+…，其中撇号，即 wn′∗，表示 `L∗`(`w`) 的第 n 个分量。令涉及 <`L∗` (`w`), `v`> 和 <`w`, `L` (`v`)> 的 `vk` 系数相等，并求解 wk′∗，得到 w1′∗=0, w2′∗=w1∗, w3′∗=w2∗, …. 这表明对偶算子 `L∗` (`w`)=(0, w1, w2, …)。所得运算为右移。

注意 ∥`L`^(`n`)∥ = ∥(`L*`)^(`n`)∥ = 1![Equation](img/F000138si33.png)，且范数对 `L` 和 `L∗` 均等于谱半径。来自 第 8.10 节 的 Gelfand 公式表明了这一点。这里极限 `n`→∞，∥`L`^(`n`)∥^(1/`n`)\=*r*(`L`)=1=*l**i**m**i**t* `n`→∞![Equation](img/F000138si34.png)，∥(`L*`)^(`n`)∥^(1/`n`) = *r*(`L*`) = 1![Equation](img/F000138si35.png)。由于该结果，`L` 和 `L∗` 的谱位于以原点为中心、半径为一的开球的闭包中。该球记为 `clos(O(0,1))`。其中 `clos` 表示闭包运算。开球的所有点都是特征值，即 `O(0,1)` 是 `sppL` 的子集。若 `v`=(1, 0, 0, …)，则 `v` 是 `L` 的特征向量，`c`=0 为特征值，因为 `L`(`v`)=0 `v`。`O(0,1)` 中的其他点 `c` 也在 `sppL` 中。为此，设 `v` = (1,`c`,`c`²,…)![Equation](img/F000138si36.png) 则 `L`(`v`) = (`c`,`c`²,`c`³,…) = `c`(1,`c`,…) = `c` `v`![Equation](img/F000138si37.png)。相应地，以上所述结果表明开单位球由 `L` 的特征值组成。*

### 例 13.5
再次考虑 Banach 空间 `l¹`，如 例 13.4 所示。该空间由所有绝对可求和的复值序列 `v`=(x1, x2, …) 组成，其中 `L` 为左移算子 `L` (`v`)=(x2, x3, …)。在该例中已看到对偶算子 `L∗` 在对偶空间 `l^∞`![Equation](img/F000138si38.png) 中作用，该空间是有界序列 `w`=(y1, y2, …) 的空间。此外，对偶算子 `L∗` (`w`)=(0, y1, y2, …) 为右移算子。已看到 `L` 和 `L∗` 的谱位于以原点为中心半径为一的开球的闭包中，`clos(O(0,1))`。包含关系成立：`O(0,1)` 包含于 `sppL` 中，后者包含于 `spL` 中，而 `spL` 包含于 `clos(O(0,1))` 中。然后，由于 `spL` 是紧的，根据 Lume-Phillips 定理，`spL`=`clos(O(0,1))`=`spL∗`。在 例 13.4 中，证明了 `O(0,1)` 是 `sppL` 的子集。最终将看到 `O(0,1)`=`sppL`，即开单位球是 `L` 的点谱。

首先注意 `O(0,1)` 的边界不在 `sppL` 中。即边界点不是特征值。边界由 {`c`，满足|`c`|=`1`} 组成。设 `c` 在 `ker(c−L)` 中且不等于 {0}。这是反证法。设 `v`=(x1, x2, …)，则 (`c`−`L`) `v`=0。即 (`c` x1, `c` x2, …)=(x2, x3, …)。该恒等式的推论是一组递推方程。具体地，递推必须成立，x(n+1)=`c` xn，`n`=1, 2,…. 通过反向代入求解，得到 `v` = `c` `x`1(1,`c`,`c`²,…)![Equation](img/F000138si39.png)。由于|`c`|=`1`，`v` 不在 `I¹`![Equation](img/F000138si40.png) 中，除非 x1 为零。由此可知边界不在 `sppL` 中，因此整个点谱为 `sppL`=`O(0,1)`。

接下来将看到 `L∗` 的点谱为空。再次假设不成立，即存在复值 `c` 使得 (`c`−`L∗`) `w`=0 对向量 `w`=(y1, y2, …) 在 `l^∞`![Equation](img/F000138si41.png) 中成立。即 (`c` y1, `c` y2, …)=(0, y1, y2, …)；这也导致一组方程，即：`c` y1=0，`c` yk=y(k-1)，`k`=2, 3, …. 当 `c`=0 时，则 `w`=0 且不能为特征向量。否则，当 `c` 不为零时，由上述方程可得 y1=0，然后通过递推，yk=0 对所有 `k`=2, 3, … 成立。这意味着 `w`=0，且它不能为特征向量。因此，`sppL∗` 为空，迄今为止所知的是对伴随算子；以原点为中心的闭球是 `L` 的谱。*

### 例 13.6




参考示例 13.4 和 13.5。右移算子 `L∗` 在对偶空间 `l^∞`![Equation](img/F000138si42.png) 中作用，其中对于 `w`=(`y1`, `y2`, …)，`L∗` (`w`)=(0, `y1`, `y2`, …)。将会看到开球 `O(0,1)` 在 `sprL∗` 中。对于 `O(0,1)` 中的 `c` 或 `c∗`，令 `v` = (1,`c`,`c`²,…)![Equation](img/F000138si43.png)，则 `v` 在 `l¹`![Equation](img/F000138si44.png) 中，对于包含 `c` 的共轭的向量也同样成立。要使 `L∗` 处于剩余谱中，只需证明以下内容：`ker` (`c∗ I−L∗`) 为 {0}，且 `c∗I−L∗` 的像在 `H` 中不是稠密的。这些准则唯一地刻画了 `sprL`。考虑 `l^∞`![Equation](img/F000138si45.png) 中的任意向量 `w`，并再次仅以形式上的方式使用形如 `f`: `w`→< `w`, `v` > 的映射。因此，`f`: (`c∗−L∗`) `w`→< (`c∗−L∗`) `w`, `v` >=< `w`, (`c−L`) `v` >=< `w`, `c v−L v` >。使用算子 `L` 的定义，并注意到 `c v−Lv`=0，因为开球中所有的点 `c` 都是特征值。这表明 `ker`(`c∗−L∗`)={0}，且 `c∗−L∗` 的像不是稠密的，因为对于 `l^∞`![Equation](img/F000138si46.png) 中的任意 `w`，`f`: (`c∗−L∗`) `w`=0；因此，`clos` `f`(`c−L∗`) 不能在 `l^∞`![Equation](img/F000138si47.png) 中稠密。这表明开球 `O(0,1)` 在 `sprL∗` 中。

接下来，将证明 `L∗` 的剩余谱等于闭单位球，即 `sprL∗`=clos(`O(0,1)`)。取任意模长为 1 的复数 `c` 以及 `l^∞`![Equation](img/F000138si48.png) 中的向量 `u`，和 `C` 中的 `w`。使用向量分量构成由以下恒等式产生的方程组：(`c−L∗`) `w`=`u`。展开该恒等式得到 `c w1`=`u1`，且 (`c w2−w1`) =`u2`，…，`c wk−w(k-1)`=`uk`，`k`=2, 3，…。求解向量 `w`：`w1`=`c∗u1`，`w2`=`c∗` (`w1+u2`)，…，`wk`=`c∗` (`uk+w(k-1)`)。回代得到结果：`w_k` = `c∗ u_k` + `c^(∗2) u(k−1)` + … + `c^(∗k) u1`。`u` = (1, `c∗`,`c^(∗2)`, …)![Equation](img/F000138si49.png) 在 `l^∞`![Equation](img/F000138si50.png) 中，因为标量 `c` 的模长为 1 且 `u` 有界。将 `u` 的分量代入 `wk` 的表达式得到 `w_k`=`c^(∗n)`+`c^(∗n)`+…+`c^(∗n)`=`k c^(∗n)`→∞![Equation](img/F000138si51.png) 当 `k`→∞![Equation](img/F000138si52.png) 时，因此向量 `w` 不在 `l^∞`![Equation](img/F000138si53.png) 中。因此，`u` = (1,`c∗`,`c^(∗2)`,…)![Equation](img/F000138si54.png) 不在 (`c−L∗`) 的像中。这表明单位圆边界上的点不是 `L∗` 的特征值。到目前为止，这表明单位圆的边界可能属于 `L∗` 的连续谱或剩余谱。接下来，将证明 `ran`(`cI−L∗`) 在 `l^∞`![Equation](img/F000138si55.png) 中不是稠密的。因此，这些点将被证明属于 `L∗` 的剩余谱。

为此，将证明 `O` (`u`, 1/2) 与 `im`(`cI−L∗`) 相交且在 `l^∞`![Equation](img/F000138si56.png) 中为空。对于 `O` (`u`, 1/2) 中的 `v`，有 `v`=`u+w`，其中 `l^∞`![Equation](img/F000138si57.png) 范数 ‖`w`‖ 小于 1/2。考虑方程：(`cI−L∗`) `z`=`v`=`u+w`。这里，`z`=(`z1`, `z2`, …) 是复值分量的向量，是上述方程的待求解。由此可得 `c z1` − 0 = 1 + `w1`，`c z2` − `z1` = `c∗` + `w2`，…，`c z_k` − `z(k−1)` = `c^(∗k−1)` + `w_k`，`k` = 3, 4, ….![Equation](img/F000138si58.png) 再次通过回代，按分量求解复向量 `z` 得到 `${zn} = c^{\\ast n} + \\sum\_{j = 1}^{n}\\left( {c^{\\ast n + 1 - j}{wj}} \\right)$`![Equation](img/F000138si59.png)。现在利用 `c` 和向量 `w` 的界可知 |`z_n` − `c^(∗n)`![Equation](img/F000138si60.png)| 小于等于 `|{\\sum\_{j = 1}^{n}\\left( {c^{\\ast n + 1 - j}{wj}} \\right)}|`![Equation](img/F000138si61.png)，这表明 |`z_n` − `c^(∗n)`| < `n`/2![Equation](img/F000138si62.png)。向量 `zn` 不是有界的，因此不在 `l^∞`![Equation](img/F000138si63.png) 中。这是因为 |`z_n` − `c^(∗n)`![Equation](img/F000138si64.png)| 大于等于 |`c^(∗n)`| − |`z_n`| = `n` − |`z_n`|*o*r|`z_n`|![Equation](img/F000138si65.png) 大于等于 `n` − |`z_n` − `c^(∗n)`| > `n`/2![Equation](img/F000138si66.png)。这表明 (`cI−L∗`) 的闭包不是 `l^∞`![Equation](img/F000138si67.png)。因此，`sprL∗`=| `c` |。而且，`sprL∗` 是 `C` 中的整个闭单位圆盘。#

### Example 13.7

对于左移算子 `L`，在 示例 13.4 中，将看到剩余谱为空。由于在 示例 13.5 中已证明 `O(0,1)`=`sppL`，只需考虑单位球的边界。因此取一个模为 1 的复数 `c`。`c` 属于 `sppL∗` 是错误的，因为 示例 13.6 表明 `sppL∗` 在边界|`c`|=`1` 上为空。`L` 和 `L∗` 的连续谱利用三个谱类型互不相交且并集为每个算子的全谱这一事实求得，这表明 `spcL∗` 为空。利用 `sppL∗` 在|`c`|=`1` 上为空这一事实。另外，应用 He’lein, (2014) 中的命题 6.3 (ii)。它指出如果 `ran` (`cI−L`) 在巴拿赫空间中不是稠密的，则 `c` 属于 `sppL∗`。由该命题的逆否命题可知，如果 `sppL∗` 在 |`c`|=`1` 上为空，则 `ran` (`cI−L`) 在 `l¹`![Equation](img/F000138si68.png) 中稠密；这意味着 `spcL` 等于 `O(0,1)` 的边界。所以，单位球的边界是 `L` 的连续谱。#

示例 13.5–13.8 的结果总结出现在 图 13.1 中（He’lein, 2014）。在该图中，闭单位圆盘出现了两次，一次在左侧，对应左移算子 `L`，一次对应其对偶算子 `L∗`。`L` 的谱由 `C` 中开单位圆盘内的点谱 `sppL` 组成。在该圆盘的边界上是连续谱 `spcL`。右侧图表中所示的伴随算子表明，在闭圆盘的每个地方，`L∗` 都有剩余谱 `sprL∗`。

![图 13.1 算子 L 在 l^{1} 中的谱及其对偶在 l^{\\infty} 中的谱。](img/F000138f13-01-9780443136979.jpg)

图 13.1 算子 `L` 在 `l¹`![Equation](img/F000138si1.png) 中的谱及其对偶在 `l^∞`![Equation](img/F000138si2.png) 中的谱。

## 13.3 Symmetric, self-adjoint, and unbounded operators

在量子技术中，自伴算子具有主要的重要性，因为它在观测过程中被唯一地使用。本节和接下来的几节用于回顾、扩展和说明关于有界和无界情况下自伴算子的众多事实。已展示了自伴算子的若干例证，主要以矩阵算子的形式给出。下面给出无限维希尔伯特空间上自伴算子的一个简单例子。

### Example 13.8



这个自伴算子的一个实例扩展了 示例 13.1 中给出的结果。令 `T`: `l²`→`l²`![Equation](img/F000138si69.png) 在复数域上。对于 `l²` 中的任意 `v`，![Equation](img/F000138si70.png) 使用映射，`Tv`=`T(v1, v2, v3, …)`=`(v1, v2/2, v3/3, …)`。属于 `l²`![Equation](img/F000138si71.png) 的含义是和 $\\sum\_{n = 1}^{\\infty}\\left( {vn} \\right)^{2}$![Equation](img/F000138si72.png) 收敛。考虑 `l²`![Equation](img/F000138si73.png) 中的 `w`，其中 `w`=`(w1, w2,… )`，则内积 `<w, Tv>`=`w1∗v1+w2∗v2/ 2+w3∗v3/3+….` 涉及内积的伴随算子的定义是 `<T∗w, v>`=`w1′∗v1+w2′∗v2+w3′∗v3 +….` 这里，`wj′∗` 是 `T∗wj`。然后为了看 `T` 与 `T∗` 之间是否存在关系，令包含 `vn` 的系数相等。这给出 `w1′∗`=`w1∗`，`w2∗′`=`w2∗/2`，`w3′∗`=`w3∗/3….` 因此，`T∗w1`=`w1`，`T∗w2`=`w2/2`，`T∗w3`=`w3/ 3`，…. 据此可得 `T∗`=`T`，因此算子 `T` 是自伴的。

### 示例 13.9
令 `T`: `l²`→`l²`![Equation](img/F000138si74.png) 在复数域上。对于任意 `v`=`(v0, v1, v2, v3, …)`，在 `l²`![Equation](img/F000138si75.png) 中，令 `Tv`=`(v1, v2/2, v3/3, …)`。为了求 `T∗`，注意到对于 `l²`![Equation](img/F000138si76.png) 中的 `w`，`<w, Tv>`=`w0∗v1+w1∗v2/2+….` 另外形成 `<T∗w, v>`=`w0′∗v0+w1′∗ v1+….` 然后将两个内积表达式相等并令 `vn` 的系数彼此相等可得：`w0′∗`=`0`，`w1′∗`=`w0∗`，`w2′∗`=`w1∗/2`，…. 因此，`T∗w`=`(0, w0, w1/2, w2/3, …)`。因此在此例中 `T∗` 不等于 `T`，所以它不是自伴的。另请注意 `<T∗w, v>`=`0+w0∗v1+w1∗v2/2+….` 相应地，`<T∗w, v>` 不等于 `<w, Tv>`，因此 `T` 和 `T∗` 甚至不是对称的，而这在此情况下是必须的。

在前一个例子中，由于算子 `T` 不是自伴的，可自动得出算子不是对称的。该结果对于无界算子不成立，而无界算子实际上在量子力学中最为重要。对于希尔伯特空间 `H` 上不一定是有界的算子，`T` 的定义域 `domT` 是 `H` 的子集。伴随算子 `T∗` 的定义域为 `domT∗`，它也是 `H` 的一个子空间，其向量 `w` 满足存在 `H` 中的向量 `v` 使得 `<v, Tu>`=`<w, u>`。通过令 `T∗w`=`v`，定义伴随算子 `T∗`。

`T` 的图为 `graph(T)`=`{(v, Tv) such that v is in domT}`。算子 `S` 扩展 `T` 的含义是 `graph(T)` 是 `graph(S)` 的子集。对于对称算子 `T`，`graph(T)` 是 `graph(T∗)` 的子集。算子 `T` 在 `graph(T)`=`graph(T∗)` 时是自伴的。在此情况下，`domT`=`domT∗` 且 `T`=`T∗`。具有 `domT`=`dom T∗` 的对称算子是自伴的。

量子力学中的一个关键定理是 Hellinger-Toeplitz 定理，其陈述为当 `T` 在希尔伯特空间上对所有 `v`、`w` 在 `H` 中定义且满足 `<Tv, w>`=`<v, T w>` 时，则 `T` 必须是 有界的（Teschl, 2009）。由于在 `H` 上处处定义的对称算子也是自伴的，因此可推出对于自伴无界算子 `T`，其定义域必须是 `H` 的真子集。在此情况下，算子 `T` 必须是 `H` 上的部分定义算子。

在量子力学的多个领域中，算子有时在希尔伯特空间或巴拿赫空间的子集上定义。这最常出现在伴随运算以及闭运算中。首先，对于伴随，`T` 在 `dom(T)` 上定义，`dom(T)` 是希尔伯特空间 `H`[1]![Equation](img/F000138si77.png) 的子集，且 `T`: `dom{T)`→`H`[2]![Equation](img/F000138si78.png)。`H`[2]![Equation](img/F000138si79.png) 是另一个希尔伯特空间。在此情况下，`T∗` 由 `T∗(u)`=`v` 定义，这意味着对所有 `w` 在 `dom(T)` 中有 `<v, w>`=`<u, T w>`。在上述内积中，第一个内积在 `H`[1]![Equation](img/F000138si80.png) 中，第二个在 `H`[2]![Equation](img/F000138si81.png) 中取。假设 `T∗` 是闭算子且 `dom(T)` 在 `H`[1]![Equation](img/F000138si82.png) 中稠密。当此成立时，对 `v` 在 `dom(T)` 中且 `u` 在 `dom(T∗)` 中，有 `<u, T v>`=`<T∗ u, v>`。类似地，假设 `B`[1]![Equation](img/F000138si83.png) 和 `B`[2]![Equation](img/F000138si84.png) 是巴拿赫空间，并考虑 `L (B[1],B[2])`![Equation](img/F000138si85.png) 中的 `T`。当 `vn` 在 `dom (T)` 中收敛到 `v`，且 `Tvn` 在 `B`[2]![Equation](img/F000138si86.png) 中收敛到 `w` 时，`T` 在 `dom(T)` 上称为闭算子，`dom(T)` 是 `B1` 的子空间，则 `w`=`Tv`。

当 `dom(T)` 在 `B`[1]![Equation](img/F000138si87.png) 中稠密时，称算子 `T` 为稠密定义的。`T` 在 `dom(T)`=`B`[1]![Equation](img/F000138si88.png) 时完全定义。算子 `T` 的闭包意味着存在闭算子 `S`，使得 `dom(T)` 是 `dom(S)` 的子集，且 `S` 在 `dom(T)` 上等于 `T`。此外，`dom(T)` 上的图范数对 `v` 在 `dom(T)` 中给出，‖`v`‖=`‖v‖+‖T v‖`；第一个范数在 `dom(T)` 中取，第二个在 `B`[1]![Equation](img/F000138si89.png) 中，第三个在 `B`[2]![Equation](img/F000138si90.png) 中。

对于希尔伯特空间 `H` 上的无界算子 `T`，当其图是闭的时它是闭算子。`T` 的图是笛卡尔积 `H x H` 的子集。它是一个向量空间。`T` 的图为 `Gr(T)`=`{<v, T v>|v is in dom(T)}`。闭图定理指出，具有闭图的处处定义线性映射是连续的。参见附录 A.6。具有闭图的部分定义线性映射可以不连续。

### 示例 13.10
考虑希尔伯特空间 `H`=`l²`![Equation](img/F000138si91.png)，即所有收敛的复值绝对和平方序列。令 `dom(T)` 等于所有使得和 ∑|`n` `v`n|²![Equation](img/F000138si92.png) 收敛的序列。令 `T`: `dom (T)`→`H` 由 `Tv`=`T (v1, v2, v3, …)`=`(v1, 2v2, 3v3, …)` 给出。`dom(T)` 的闭包=`H`，因此 `dom(T)` 在 `H` 中稠密。这是因为 `dom(T)` 包含所有至多只有有限多个非零项的序列。`T` 不是单射，因为非零项的有限数量。值域中两个相同的有限向量元组串对应于定义域中无穷多个不同的项，其像为相同的有限元组序列。此外，`T` 是无界的，但它是自伴的，因为 `<T∗w, v>`=`w1′∗v1+w2′∗v2+…` 且 `<w, Tv>`=`w1∗v1+w2∗2v2 +….` 这里 `wk′∗` 是来自 `T∗w` 的元组。然后令 `vk` 的系数相等可得 `wk′∗`=`wk/k`。这意味着 `T∗w`=`(w1, 2w2, 3w3, …)`。此外，`T` 的谱是点谱：`sppT`=`{1, 2, 3, …}` 因为 `Tvn`=`n vn`。

### 示例 13.11
对于无界算子 `T`，在希尔伯特空间 `H` 中具有伴随算子 `T∗` 且 `T`: `dom(T)`→`H`。令 `c∗` 在 `sppT∗` 中。即，`c∗` 在 `T∗` 的点谱中。可以看出 `c` 将在 `sppT` 与 `sprT` 的并集中，具体而言，即它将在其中之一中。由于 `c∗` 是 `T∗` 的特征值，存在 `dom(T∗)` 中的特征向量 `v` 使得 `T∗v`=`c∗ v`。对于所有 `w` 在 `dom(T)` 中，可得 `<v, Tw>`=`<T∗v, w>`=`<c∗v, w>`=`c <v, w>`。因此，`<v, c w>`−`<v, Tw>`=`0`，并且由于这对所有 `w` 成立，这意味着 `<v, (cI−T) w>`=`0` 对所有 `w` 在 `dom(T)` 中成立。因此可得 `ran(cI−T)` 不是稠密的，因此谱不可能是连续的。

### 示例 13.12
即使位置算子 `Q` 在 `H`=`L²(R)`![Equation](img/F000138si93.png) 中是无界的，它仍然是自伴的。`H` 中 `f` 与乘积 `x·g` 的内积，其中 `g` 也在 `H` 中，由积分 ∫[ − ∞]^∞![Equation](img/F000138si94.png) `f∗·(x·g) dx)`=`<f, x·g>` 给出。可以看出该量等于 `<x·f, g>`。后者内积是积分 ∫[ − ∞]^∞![Equation](img/F000138si95.png) `(x·f∗)·g dx)`=`<x·f, g>`。因此 `Q(f)`=`x·f`，因此乘法算子 `Q` 是自伴的。

### 示例 13.13



动量算子也是无界的，但在 `H` = `L²(R)` 中它也是自伴的![Equation](img/F000138si96.png)。这种情况下的内积是 `<f, -i d/dx g>`；它是积分 `∫[-∞]^∞`![Equation](img/F000138si97.png) `f*·(-i d/dx g) dx`。这里假定导数是可积的。现在分部积分得到 `(f*·g)` 在负无穷到正无穷之间求值，以及积分 `∫[-∞]^∞`![Equation](img/F000138si98.png) `(i d/dx f*)·g dx`。假设乘积 `(f*·g)` 趋于零；那么用内积表示的结果是 `<-i d/dx f, g>`，从而表明该算子也是自伴的。

## 13.4 有界算子与数值域

如在 第 7.1 节 中提到，数值域在刻画 Hilbert 空间上有界算子所关联的谱类型方面非常有用。为了说明这一点，考虑 Banach 空间或实际上 C∗ 代数 `B(H)` 中的算子 `T`。算子 `T` 的数值域为 `sup[‖v‖=1]`![Equation](img/F000138si99.png) `<v, T v>`。假设 `cI - T` 不是可逆的，甚至不是单射的。那么在 `H` 中存在非零的 `v` 使得 `(T - I c) v = 0`。利用该恒等式 `T v = c v`，并与 `v` 形成内积，`<v, T v> = c <v, v>`，其中 `‖v‖ = 1`。这表明特征值 `c` 在数值域中。因此，点谱 `sppT` 是数值域的子集。

现在假设 `(c - T)` 的值域在 `H` 中不是稠密的；这意味着闭包 `clos(c - T)` 是 `H` 的真子集 `A`。那么在 `A^⊥`![Equation](img/F000138si100.png) 中存在单位向量 `w`，使得内积 `<w, (T - c) w> = 0`，即 `<w, T w> = c`。所以再次 `c` 在数值域中。因此，剩余谱 `sprT` 是 `T` 的数值域的一部分。

最后，假设 `(T - c)` 的值域在 `H` 中稠密，但不等于 `H`。在这种情况下，存在归一化向量序列 `w[n]`![Equation](img/F000138si101.png) 在 `H` 中使得 `(T - c) w[n] → 0`![Equation](img/F000138si102.png)。必须存在一个趋于零的序列。否则，`(T - c)` 将是有界下方的，如在 第 7.6 节 中所见以及本章前面所述，稠密且有界下方意味着 `(T - c)` 是可逆的。利用序列 `w[n]`![Equation](img/F000138si103.png) 与其内积给出 `<w[n]`![Equation](img/F000138si104.png), `(T - c) w[n]>` = `<w[n]`![Equation](img/F000138si105.png), `T w[n]`![Equation](img/F000138si106.png) > − `c` < `w[n]`![Equation](img/F000138si107.png), `w[n]` > → 0![Equation](img/F000138si108.png)。因此，这次 `c` 在数值域的闭包中。在这种情况下，连续谱 `spcT` 是数值域闭包的子集。

数值域 `W(T)` 对于 `n` 阶 `n` 复值矩阵的性质列表如下提供（Gustafson 和 Rao, 1997）：
1. `W(T)` 是 `C` 的紧子集。
2. `W(T)` 是 `C` 中的凸集，由 Hausdorff-Toeplitz 定理得出。
3. `W(T)` 包含 `T` 的谱。
4. 如果 `T = T*`，则 `W(T)` 是实数线上的闭区间。此外，它由两个特征值构成的端点组成。

下一个例子说明了使用特征值来求数值域。 它还说明了性质 4)。 这个相同的例子在 Example 7.3 中已通过数值模拟求解，其中最一般的 `C²`![Equation](img/F000138si109.png) 中的量子比特被代入数值域公式。

### Example 13.14

自伴矩阵 `T =` 的特征值
```
\begin{matrix}
{|2} & {i|} \\
{|{- i}} & {1|} \\
\end{matrix}
```
![Equation](img/F000138si110.png)
是从特征方程的解得到的：`t² − 3t + 1 = 0`![Equation](img/F000138si111.png)。特征值是 `(3 + -5^(1/2))/2. = .382, 2.618`![Equation](img/F000138si112.png)。数值域是 `W(T) = [.382, 2.618]`。

更一般地，对于 Hilbert 空间 `H` 上的算子 `T`，数值域还有若干其他性质（Shapiro, 2004）。
1. `W(T)` 在酉相似下不变。
2. `W(T)` 位于以原点为中心、半径为 `‖T‖` 的闭圆盘中。
3. `W(T*) = {c* for all c in W(T)}`。
4. `W(I) = {1}`。
5. 对于 `a, b` 在 `C` 中，且 `T` 在 `B(H)` 中，`W(a T + b I) = a W(T) + b`。
6. 如果 `T` 是幂零的，即 `T^(n+1) = 0`![Equation](img/F000138si113.png)，则 `T` 的谱为零在 `clos W(T)` 中。

### Example 13.15

以 2×2 复值矩阵 `T` 的代数作为载体集。如果 `T` 是除第一行第二列项外全为零的矩阵，这里令项 `T[1,2]`![Equation](img/F000138si114.png) 等于一，`T =`
```
\begin{matrix}
{|0} & {1|} \\
{|0} & {0|} \\
\end{matrix}
```
![Equation](img/F000138si115.png)
则 `sp(T) = 0` 且 `‖T‖ = 1`。此外，`T` 是二阶幂零的，因为 `T² = 0`。

对于无界算子，谱与数值域之间的关系如下：（StackExchange, 2015）。
1. 如果 `T` 是正规的，则 `T` 的整个谱位于 `clos W(T*)` 中。
2. 如果 `T` 是对称的，包含于 `clos T` 包含于 `T*`，则谱不一定是实的，但 `clos W(T)` 是 `R` 的子集。
3. 如果 `T` 不是闭算子，且 `T` 是 `clos T = T**` 的子集，则谱是复的并且包含 `clos W(T)`。

对于 `H` 上的自伴有界算子 `T`，数值域 `W(T)` 与 `T` 的特征值之间存在关系。当 `a = inf <v, T v>` 对所有 `‖v‖ = 1` 时，则 `a` 在 `sp T` 中（Gustafson 和 Rao, 1997）。

如前所述，Hilbert 空间 `H` 中耗散算子 `T` 的实部是这样的，对于 `H` 中所有 `v`，数值域的实部为非正。也就是说，`Re <v, T v>` 为非正，其中 `‖v‖ = 1`。接下来的几个例子将说明这一概念。

### Example 13.16

设 Hilbert 空间的载体集为 `H = R^(n)`![Equation](img/F000138si116.png)，具有通常的内积，如果 `T = -I`，即对角单位矩阵的负值；那么对于 `H` 中所有 `v`，`<v, T v> = -‖v‖²`![Equation](img/F000138si117.png)，因此 `T` 是耗散的。

### Example 13.17

另一个耗散算子 `T` 的实例，这次在 `L²(R)`![Equation](img/F000138si118.png) 与 `C_o¹(R)`![Equation](img/F000138si119.png) 相交。这是由具有紧支集的光滑可微函数组成的空间，它们是绝对平方可积的。令 `T` 为动量型算子，`T = d/dt`。

则 `<T f, f> = integral, ∫[t = -∞]^∞`![Equation](img/F000138si120.png) `f′* f dt`，其中撇号表示导数。现在分部积分得到 `<T f, f> = ∫[t = -∞]^∞`![Equation](img/F000138si121.png) `-f* f′ dt = - <f, T f> = - <T f, f> *`。所以 `<T f, f>` 的实部为 0，因为当 `z = - z*` 时，`z` 为纯虚数。因此 `T` 是耗散的。

在 Banach 空间 `A` 中，算子 `T` 为耗散的定义被推广，因为不一定存在内积。在这种情况下，如果对于所有 `c > 0` 和所有 `v` 在 `dom(T)` 中，`‖(c - T) v‖` 大于或等于 `c ‖v‖`；则 `T` 是耗散的。Banach 空间中耗散算子的相当完整的汇编见 Lumer 和 Philips (1961) 和 Engel 和 Nangel (2000)。这些性质在证明先前提到的 Lumer-Phillips 定理时是必需的，该定理将算子的谱与其对偶算子的谱联系起来。




每当 `Re <v, Tv>` 非负，且 `‖v‖ = 1` 时，`T` 被称为增算子。关于这些算子以及耗散算子的应用在于构造一参数半群，很像 Stone 定理中的情况。在本例中，当利用耗散算子时，半群由 Banach 空间中形式为 `e^(t T)` ![方程](img/F000138si122.png) 的算子组成。当生成元是增算子 `T` 时，Banach 空间中相应的算子形式为 `e^(-t T)` ![方程](img/F000138si123.png)。然而，其中许多算子是部分定义的（Delaubenfels, 1988）。

## 13.5 自伴算子

如前所述，本节和下一节提供了与自伴算子相关的概念的回顾以及扩展。在量子学科中最为重要的是，可观测量是 C∗ 代数 `A` 中的算子。它们是自伴算子 `T`，使得 `T = T∗`。此外，这些算子是可测的，并通过 `RRT` 定义，类似于寻找对偶空间的过程。该方法与之前考虑 `T: H → H` 情形时伴随 `T∗` 的构造非常相似。

假设 `T: H1 → H2`，其中 `H1` 和 `H2` 是希尔伯特空间。此外暂时假设 `T` 有界，即 `T` 在 `B(H1, H2)` 中。如对偶空间的构造一样，将定义一个泛函 `f`。它满足对于 `H2` 中固定的 `w`，`f: H1 → C`，其中对于 `H1` 中任意的 `v` 有 `f(v) = <w, T v>`。该泛函是线性的且有界的，因为 `T` 有界且 `|f(v)|` 小于或等于 `‖w‖ ‖T v‖`。该不等式是 `CBS` 不等式的直接结果。此外，由于 `T` 有界，最后的表达式小于或等于 `‖w‖ ‖T‖ ‖v‖`。而且 `f` 在 `H1` 的对偶空间中。

使用 `RRT`，对于 `H2` 中的每一个 `w`，存在唯一的 `u` 在 `H1` 中使得 `f(v) = <u, v>` 对所有 `v` 在 `H1` 成立。这定义了一个映射：`T∗: H2 → H1`，它被称为 `T` 的伴随算子，在上一节中已提及。映射 `T∗` 由 `T∗(w) = u` 给出。简而言之，`T∗` 的定义性质是 `<w, T v> = <T∗ w, v>`，对所有 `v` 在 `H1` 和 `w` 在 `H2` 成立。前面提到的第一个内积在 `H2` 中，第二个在 `H1` 中。由于假设 `T` 有界，可知 `T∗` 也是线性的且有界的，即 `T∗` 在 `B(H2, H1)` 中。此外，`T` 和 `T∗` 满足以下性质。

1. 范数相等：`‖T∗‖ = ‖T‖`。
2. 对合：`(T∗)∗ = T`。
3. 交换范数：`‖T T∗‖ = ‖T∗ T‖ = ‖T‖²` ![方程](img/F000138si124.png)。
4. 逆：若 `T` 可逆，则 `T∗` 亦可逆且 `(T^(-1))∗ = (T∗)^(-1)`。
5. 可加性：`(S + T)∗ = S∗ + T∗`，其中 `S` 也在 `B(H1, H2)` 中。
6. 反交换：`S∗ T∗ = (T S)∗`。

对于有界算子 `T` 可以做出涉及自伴算子的唯一表示。设 `Q` 和 `S` 是 C∗ 代数 `A` 中的自伴算子；则 `T` 可表示为 `T = Q + i S`。因此 `T∗ = Q - i S`。将 `T` 加上 `T∗` 然后用 `T` 减去 `T∗` 得到 `Q = (T + T∗)/2` 且 `S = (T - T∗)/(2i)`。算子 `Q` 和 `S` 可被视为 `T` 的实部和虚部，按此顺序。

若 `K` 是 `H` 的闭子空间，则 `K` 本身就是一个希尔伯特空间。在此情况下，`H` 中任意向量 `v` 可写成 `u + w`，其中 `<u, w> = 0` 且 `u` 在 `K` 中。与 `K` 中向量正交的所有向量的空间称为 `K perp`，即写成 `perp(K)` 或 `K^⊥` ![方程](img/F000138si125.png)。可将投影算子 `P` 与此过程关联。事实上，设 `P: H → K`，其中 `P(v) = u`。这样的运算既是幂等的又是自伴的。注意 `(I - P)(v) = w`。如果还有 `v' = u' + w'` 且 `u'` 在 `K` 中而 `w'` 在 `perp(K)` 中，则 `<P(v), v'> = <u, u'> = <v, u'> = <v, P(v')>`。此外，`<u, w> = <P(v), (I - P)(v)> = <v, P(I - P)(v)> = 0`。当 `K` 是 `H` 的闭子空间时，`perp(K)` 也是闭的。希尔伯特空间 `H` 的向量子空间 `K` 的一个重要性质是 `K` 的闭包等于 `perp(perp(K))`。如果 `K` 是 `H` 的闭子空间，则再次有 `K = perp(perp(K))`。而且，`K` 是闭的当且仅当 `K = (K^⊥)^⊥` ![方程](img/F000138si126.png)。为此，首先假设 `K = (K^⊥)^⊥` ![方程](img/F000138si127.png)。然后选取一个序列 `v[n] → v` ![方程](img/F000138si128.png)，其中 `v[n]` ![方程](img/F000138si129.png) 在 `K` 中而 `v` 在 `H` 中。将证明 `v` 在 `K` 中。取 `w` 在 `K^⊥` ![方程](img/F000138si130.png) 中，则 `<w, v[n]> = 0` ![方程](img/F000138si131.png) 对所有 n 成立，然后利用内积的连续性：`lim[n → ∞] <w, v[n]> = <w, lim[n → ∞] v[n]> = <w, v> = 0`。这表明 `v` 在 `K = (K^⊥)^⊥` ![方程](img/F000138si135.png) 中，因此 `K` 是闭的。

反之，若 `K` 是 `H` 的闭子空间，则将证明 `K = (K^⊥)^⊥` ![方程](img/F000138si136.png) 将被证明。取 `K` 中的 `v` 与 `K^⊥` ![方程](img/F000138si137.png) 中的任意 `w` 的内积得到 `<v, w> = <w, v>∗ = 0`，从而表明 `v` 也在 `(K^⊥)^⊥` ![方程](img/F000138si138.png) 中。因此 `K` 是 `(K^⊥)^⊥` ![方程](img/F000138si139.png) 的子集。为看相反的集合包含，设 `v` 在 `(K^⊥)^⊥` ![方程](img/F000138si140.png) 中。然后表示 `v = w + z`，其中 `w` 在 `K` 中且 `z` 在 `K^⊥` ![方程](img/F000138si141.png) 中。利用线性性，`0 = <v, z> = <w, z> + <z, z> = 0 + <z, z> = ‖z‖²`，这意味着 `z = 0`。相应地，`v = w`，因此 `(K^⊥)^⊥` ![方程](img/F000138si142.png) 是 `K` 的子集，因而它们相等。

当 `T` 有界时，核与伴随运算的像之间存在关系，即 `Ker(T) = perp(Im(T∗))` 且 `Im(T∗)` 的闭包 `= perp(ker(T))`。此外，若 `K` 是闭的，则 `perp(K) = perp(closure(K)) = closure(perp(K))`。另外，`perp(perp(K)) = closure(K)`。对于闭子空间 `K`，可得 `perp(perp(K)) = K`。而且，利用 `w = u + v`，则对于 `P` 在 `B(H)` 中且 `P(w) = u`，有 `‖P(w)‖² = ‖w‖² - ‖w - u‖²` ![方程](img/F000138si143.png)；这是因为 `w - u = v` 且 `<u, v> = 0`。因此，`‖u‖² = ‖w - v‖² = ‖w‖² - ‖v‖²` ![方程](img/F000138si144.png)。

伴随算子与核之间的关系如下：

1. `Ker(T∗) = perp(ran(T))`.
2. `Perp(ker(T∗)) = clos(ran(T))`.

将给出一个例子，使用动量算子的基，即微分运算。它将说明希尔伯特空间子空间上的闭算子，其中该算子不是有界的。

### 示例 13.18

考虑 `[0, 1]` 上平方绝对值可积的复值函数的勒贝格空间。它记为 `L[2]` ![方程](img/F000138si145.png) `[0, 1]`。再次设无界动量型算子 `T` 被采用，其中 `T = d/dx`。则 `T` 的定义域为 `D(T)`，其中 `D(T) = { f in L[2]` ![方程](img/F000138si146.png) `[0, 1]`，使得 `f` 绝对连续，其中 `d f/dx` 在 `L[2]` ![方程](img/F000138si147.png) `[0, 1]` 中且 `f(0) = 0}`。则 `T` 在 `D(T)` 中是闭的（Park, 2013）。它在 Banach 空间 `C[0, 1]` 中不是闭的。即它在定义域 `{ f in C[0, 1]` 中不是闭的，使得 `d f/dx` 在 `C [0, 1]` 中且 `f(0) = 0}`。详见示例 8.1。



在有限维希尔伯特空间中，伴随算子由 `RRT` 保证存在；然而，在无限维希尔伯特空间 `H` 中，伴随算子可能根本不存在。有时它会存在但用处不大。首先，伴随算子存在当且仅当 `T` 是稠密定义的。这样，`RRT` 可以用于内积，证明伴随运算的存在性和唯一性。当伴随算子本身 `T∗` 是稠密定义时，伴随算子非常有用，而这正是 `T` 可闭合的时候。伴随算子的定义如下：对于所有 `v` 在 `dom(T)` 中以及所有 `u` 在 `dom(T∗)` 中，则内积相等，`<u, Tv>=<T∗u, v>`。因为 `T` 的定义域的闭包=`clos(dom(T))`=`H`，因此 `T∗` 将唯一地被找到，对于 `u` 在 `dom(T∗)` 中。

考虑 `H` 中的向量 `u`；如果存在 `w` 在 `H` 中使得 `<u, Tv>=<w, v>` 对所有 `v` 在 `dom(T)` 中成立，则 `<u, Tv>` 是 `dom(T)` 上的连续线性形式。当 `<u, Tv>` 在 `dom(T)` 上连续时，它可以通过连续性延拓到整个 `H`。接下来，可以应用 `RRT` 证明存在唯一的 `w` 在 `H` 中使得 `<u, Tv>=<w, v>`。该结果成立当且仅当 `dom(T)` 在 `H` 中稠密。这表明当 `T` 有界时伴随算子存在且唯一。

## 13.6 正规算子与无界算子

有界算子的谱是紧且非空的；因此，它在复平面中是闭且有界的。由于这些性质，谱半径 `r (T)` 可以对 `A` 中的 `T` 定义。它是 `r (T)=sup {|c|, such thatc is in the spectrum of T}`。此外，上确界半径在 `sp(T)` 中的某个 `c` 处取得，并且 `r (T)` 小于或等于`‖T‖`。此外，谱可以使用 Gelfand 公式求得：`r (T)=limit as n goes to infinity for ∥*T*^(*n*)∥^(1/*n*)`![方程](img/F000138si148.png)。当算子 `T` 是正规时，可得谱半径等于范数，即 `r (T)=‖T‖`。作为推论，如果 `T` 在 `C∗` 代数中，则`‖T‖²\=r (T∗ T)`。

### 示例 13.19

因为自伴算子 `T`，`H:→H` 是正规的，`T` 的谱半径等于其范数，即 `r (T)=‖T‖`。因此，例如，如果 `spT=0`，这意味着 `T=0`。注意算子 `T`=

$\\begin{matrix} {|0} & {1|} \\\\ {|0} & {0|} \\\\ \\end{matrix}$

![方程](img/F000138si149.png)

谱 `spT=0`，但 `T` 不是零，也不是正规算子。#

一般而言，谱半径可能小于范数，例如使用幂零算子即可看出。

过去对于 `C∗` 代数 `A` 中的有界算子 `T`，`T` 可以用两个自伴算子 `Q` 和 `S` 表示为 `T=Q+iS`。因此，`T∗=Q−iS`。将 `T` 乘以其伴随 `T∗` 得到 `T T∗=Q²+i(S Q−Q S)+S²`。接下来乘以 `T∗ T=Q²+i(−S Q+Q S)+S²`。所以只要 `S Q−Q S=−S Q+Q S`，即当 `S Q=Q S` 时，可得 `T` 是正规算子。关于正规算子的另一个有趣性质在下面的例子中给出。

### 示例 13.20

如果 `T` 是 `C∗` 代数中的正规算子，则 `‖T²‖=‖T‖²`。为此，使用 `C∗` 恒等式 `‖T∗ T‖=‖T‖²` 来自 第 3.8 节；然后可得 `‖(T∗ T)²‖=‖T‖⁴`。另一方面，对 `‖T²‖` 平方得到 `‖T²‖²`，并将 `C∗` 恒等式应用于该量导致方程 `‖T²‖²\=‖(T∗)² T²‖`。运用正规性条件最终得到 `‖T²‖²\=‖(T∗ T)²‖`。所以`‖T‖⁴\=‖T²‖²`，取平方根完成证明。

一个不同的证明使用谱半径。如前所述，令 `*r* = *l*i*m*i*t*[*n* → ∞]`![方程](img/F000138si150.png) `∥*T*^(*n*)`![方程](img/F000138si151.png) `∥^(1/*n*)`![方程](img/F000138si152.png)。对于大于零的整数 `n`，`∥*T*^(2^(*n*))`![方程](img/F000138si153.png) `∥² = ∥(*T*^(2^(*n*))) \* *T*^(2^(*n*))∥ = ∥(*T*\**T*)^(2^(*n*))∥ = ∥*T*∥^(2^(*n* + 1))`![方程](img/F000138si154.png)。所以，由数学归纳法 `∥*T*^(2^(*n*))∥ = ∥*T*∥^(2^(*n*))`![方程](img/F000138si155.png)，对所有大于零的 `n` 成立。根据 Gelfand 公式，`*r* = *l*i*m*i*t*[*n* → ∞]∥*T*^(2^(*n*))∥^(2^( − *n*)) = ∥*T*∥`![方程](img/F000138si156.png)。#

对于正规算子 `T`，剩余谱，即 `sprT` 不存在 (Conway, 1990)。所以谱仅由点谱和连续谱组成。这将在后面的章节再次看到。此外，正规算子的数值半径与谱半径相同。`C∗` 代数中非零正规算子 `T` 与 `C∗` 代数中的态之间存在密切关系。对于每一个这样的算子 `T`，存在一个态 `g` 使得 `*g*(*T*\**T*) = ∥*T*∥²`![方程](img/F000138si157.png) 且 `|g (T)|=‖T‖`。对于 `A` 中每一个这样的非零正规算子 `T`，存在一个纯态 `g` 使得 `|g (T)|=‖T‖`。

`H` 上所有紧算子的集合构成一个 `C∗` 代数。在无限维情形下它是无单位的。然而，可以发展近似单位元，因为该结构同构于平方可和序列空间，`*l*²`![方程](img/F000138si158.png) (Murphy, 2014)。

对于 `H` 上的两个无界算子 `S` 和 `T`，当 `dom(S)` 是 `dom(T)` 的子集且对所有 `v` 在 `dom(S)` 中有 `S (v)=T (v)` 时，`T` 是 `S` 的扩张。这里，`S` 被称为 `T` 的限制。所以，如果 `S` 具有闭扩张 `T`，则称 `S` 可闭。闭算子 `T` 的核心是子空间 `X` 包含在 `dom(T)` 中，当 `T` 是闭包延拓 `dom(T)` 与 `X` 相交时。核心也称为本质定义域；它具有这样的性质：对于 `v` 在 `dom(T)` 中，存在序列 `vn` 在 `X` 中使得`‖v−vn‖+‖Tv−Tvn‖→0` 当 `n→∞`![方程](img/F000138si159.png) (Reed and Simon, 1980)。

对于 `H` 上也是可闭的任意无界算子 `T`，`T` 的闭包记为 `closT` 定义为最小的闭扩张。它由包含 `T` 的所有闭集的交集给出，并且此外，`closT` 是唯一的。对于在 `H` 中在 `dom(T)` 上稠密定义的 `T`，`T` 被称为对称的，这意味着 `<u, Tv>=<Tu, v>` 对所有 `u` 和 `v` 在 `dom(T)` 中成立。一个对称稠密定义的无界算子 `T` 具有闭包：`closT=T∗∗`。非对称算子不一定可闭。对于闭对称算子 `T` 的自伴准则，使用一个测试很容易。它是 `T` 的预解集与 `R` 的交集非空 (Woozy, 2017)。

`H` 上的算子 `T` 是对称的，这意味着 `<T x, y>=<x, T y>` 对所有 `x` 和 `y` 在 `dom(T)` 中成立。这意味着 `dom(T)` 包含在 `dom(T∗)` 中。对称算子具有 `T` 是 `T∗∗` 的子集，而 `T∗∗` 本身是 `T∗` 的子集。算子 `T` 也是对称的当且仅当 `T` 的数值域是实数，即 `W (T)` 是 `R` 的子集。当 `T` 有界且对所有 `v, w` 在 `H` 中 `<v, T w>` 为实数时，`T` 是对称的。对于闭对称算子，以下成立：`T=T∗∗` 是 `T∗` 的子集。涉及所有重要定义域问题的严格处理可以在 Hall (2013) 中找到。

可闭算子 `T` 当且仅当它具有自伴闭包时称为本质自伴。它本质上是自伴的当且仅当它是对称的、稠密定义的并且存在非实复数 `c`，使得 `c−T` 和 `c∗−T` 具有稠密值域。对于具有最小谱值 `a` 和最大谱值 `b` 的有界自伴算子 `T`，可得 `a=−‖T‖`，或 `b=‖T‖`。此外，数值域的闭包=`[a, b]`。此外，当 `W (T)` 或 `spT` 位于非负实轴上时，自伴算子 `T` 为正。`C∗` 代数 `A` 中所有正算子的集合是实向量空间 `V={T in A, such that T=T∗|` 中的凸锥。



对于自伴算子 `T`，在希尔伯特空间 `H` 上，有 `ker(T+−i)={0}`。为了看到这一点，首先假设 `Tv=iv`。则 `<v, Tv>=<v, iv>=i <v, v>`，并且 `<Tv, v>=<iv, v>=−i <v, v>`，但由于 `T` 是自伴的，故可推出 `ker(T+−i)={0}`。对于 `T∗` 也是如此，即 `ker(T∗+−i)={0}`。当 `T` 是对称且闭的且 `ker(T+−i)={0}` 时，则 `ran(T+−i)=H`。将证明 `ran(T+−i)` 在 `H` 中稠密。对于 `v` 在 `perp(ran(T+i))` 中且对所有 `w` 在 `dom(T)` 中。 可推出 `<v, (T+i)w>=0`。因此，在这种情况下，`<v, Tw>=<−iv, w>`。对于 `v` 在 `dom(T∗)` 中且 `(T∗+i)v=0`，因此 `v` 在 `ker(T∗+i)` 中。另请注意 `∥(T+i)v∥² = <(T+i)v, (T+i)v> = ∥Tv∥² + ∥v∥²`![方程](img/F000138si160.png)。因此，如果 `(T+i)vn` 是 `CS`，则可推出 `Tvn` 是 `CS` 且 `vn` 也是 `CS`。当 `vn` 收敛到 `v` 时，由于 `T` 是闭的，`v` 在 `dom(T)` 中且 `Tvn→Tv`。

无界算子应是闭的且稠密定义的。如前所述，闭图定理及其相关概念在确定算子的闭包方面发挥着重要作用。作为闭图定理确定闭包的一个实例，请考虑以下示例。

### Example 13.21

对于稠密定义的自伴算子 `T=T∗`，可推出 `T` 是闭的。从恒等式 `<T∗ u, v>=<u, T v>` 开始。就关系而言，`(u, w)` 在 `T∗` 的图上，这意味着 `<w, v>=<u, Tv>` 对所有 `v` 在 `dom(T)` 中成立。利用连续性 `w→<w, v>` 和 `u→<u, Tv>` 可知 `T∗` 中所有 `(u, w)` 的集合是闭的。因此，`T∗` 是闭的，但 `T=T∗`，所以 `T` 也是闭的。

稠密定义的对称算子 `T`，其 `dom(T)` 是 `H→H` 的子集，当且仅当 `ran(T+iI)=ran(T−iI)=H` 时是自伴的。首先注意对称意味着 `dom(T)` 包含于 `dom(T∗)`。假设涉及值域等于 `H` 的恒等式成立。接下来证明 `dom(T∗)` 包含于 `dom(T)`。设 `w` 在 `dom(T∗)` 中。我们必须证明 `w` 也在 `dom(T)` 中。则存在 `H` 中的元素 `v`，使得对任意 `u` 在 `dom(T)` 中，`<w, (T+i)u>=<v, u>`。现在由于 `ran(T−i)=H`，可推出 `v=(T−i)z` 对某个 `z` 在 `dom(T)` 中成立。由于 `T` 是对称的且 `u` 也在 `dom(T)` 中，可推出 `<w, (T+i)u>=<v, u>=<(T−i)z, u>=<Tz, u>+i<z, u>=<z, Tu>+<z, iu>=<z, (T+i)u>`，但 `ran(T+i)=H`；这意味着 `w=z` 因为 `z` 在 `dom(T)` 中；于是 `w` 在 `dom(T)` 中。所以 `dom(T)=dom(T∗)`。

在希尔伯特空间 `H` 上的对称稠密定义算子 `T`，只要 `T+−i` 是单射就可以是自伴的；此时 `T∗+−iI` 成为一个扩张，即从 `dom(T)` 到 `H` 的双射。这里 `T=T∗`。`T` 仅对称而不自伴的问题在于 `T+−iI` 不一定是满射。只要 `T` 的亏指数相等，就存在 `T` 的自伴扩张，且仅在此情况下。这些指数由 `dim(ran(perp(T+iI)))` 和 `dim(ran(perp(T−iI)))` 给出，并在偏等距的上下文中再次提及。偏等距是希尔伯特空间之间的线性映射。它在其核的正交补上是等距的。每当指数相同时，这些扩张可以通过使用线性等距或使用前面提到的 Cayley 变换来参数化（Hall, 2013）。

对于对称算子 `T`，`X=dim(perp(T+i))` 与 `Y=dim(perp(T−i))` 之间存在关系，以及 `T` 的唯一自伴或本质自伴扩张。当 `X=Y=0` 时，这些扩张存在。当 `X=Y` 大于或等于一时，则 `T` 有无穷多个自伴扩张。当 `X` 与 `Y` 不同时，则 `T` 没有自伴扩张。在任何情况下，只要 `T` 是本质自伴的，则 `T` 的闭包 `clos(T)` 是 `T` 的唯一自伴扩张。这可以看出，因为如果 `S=S∗`，则由于自伴算子总是闭的，可推出 `dom(S∗)` 是 `dom(clos(T))` 的子集，而后者是 `dom(S)` 的子集。由于 `S` 是自伴的，三个定义域相等，因此 `S=clos(T)`。

正算子 `P` 的平方根是一个自伴算子 `T`，使得 `P = T²`![方程](img/F000138si161.png)。对于任意有界算子 `P`，存在唯一的正平方根，记为 `|T|`，它是 `T∗T` 的正平方根。还可进行极分解，涉及唯一的偏等距 `U` 和 `|T|`。这里，`T=U|T|`，且 `ker(T∗)` 是 `Ker(U)` 的子集。只要无界算子是闭的且稠密定义的，相同的结果也成立。在这种情况下，`|T|` 可能无界。它是非负自伴算子，与 `T` 具有相同的定义域。`U` 也是一个偏等距，使得 `U=0` 在 `perp(Im(T))` 上。然而在有限维情况下，`U` 可以延拓为酉算子（Wells and Williams, 2012）。在无限维情况下，偏等距不能延拓为酉运算。例如，左移算子 `L: l² → {(x[2], x[3],…)`![方程](img/F000138si162.png) 在 `l²}`![方程](img/F000138si163.png) 上是子空间 `S={x in l²`![方程](img/F000138si164.png)，其中 `x[1]=0}`![方程](img/F000138si165.png) 上的等距。所以 `L:S→l²`![方程](img/F000138si166.png) 且是满射。

有界自伴算子 `T` 的一个简单结果推广了自伴或厄米矩阵的特征值和特征向量推论。事实上，设 `a` 和 `b` 在 `T` 的点谱中，`sppT`。相关的特征向量 `v` 和 `w` 非零且满足 `Tv=av` 和 `Tw=bw`。当 `a` 不同于 `b` 时；则 `v` 与 `w` 正交，因为 `<T v, w>=a <v, w>=<v, T w>=b <v, w>`，且 `(a−b) <v, w>=0`，但 `a−b` 不为零。因此，`<v, w>=0`。对于任意自伴算子，可推出 `T=T∗=T∗∗`。此外，闭对称算子是自伴的当且仅当 `T∗` 是对称的。

## 13.7 Spectral decomposition

接下来将描述复希尔伯特空间 `H` 上有界自伴算子 `T` 的谱分解。这些算子在量子力学中是基本的，因为所有可观测量都是这种形式。对于在 `T` 的谱上定义的连续函数 `f` 和 `g`，以及实标量 `a` 和 `b`，涉及 `T` 的以下恒等式必须成立：

1. 1) Linear: `(a f+b g)(T)=a f(T)+b g(T)`.
2. 2) Product: `(f g)(T)=f(T) g(T)`.
3. 3) Identity: `I(T)=I`.
4. 4) Adjoint: `f∗(T)=f(T)`.
5. 5) Spectral Invariance: For eigenvalue `c` of `T` and `v` in `H`, if `T v=c v`, then this implies that `f(T) v=f(c) v`.
6. 6) Spectrum: The spectrum of `f(T)={f(c) is such that c is in the spectrum of T}`.
7. 7) Positive: `f` greater or equal to zero implies `f(T)` is greater or equal to zero.

### Example 13.22

这是在希尔伯特空间 `H` 中涉及有界算子 `T` 的剩余谱的另一个示例。它构成了一个有趣的特征向量示例。在这种情况下，如果 `c` 在 `sprT` 中，则共轭值 `c∗` 在 `sppT∗` 中。首先，由于 `c` 在 `T` 的剩余谱中，则 `ran(cI−T)` 既不稠密也不等于 `H`；它是子空间。然后，必须存在 `H` 中非零向量 `v`，它不在 `clos(cI−T)` 中。该元素在 `(c∗I−T∗)` 的零空间中，且对于任意 `w` 在 `H` 中，`<v, (cI−T) w>=<(c∗I−T∗) v, w>=0`。由于 `w` 是任意的，`(c∗I−T∗) v=0`，意味着 `c∗` 是 `T∗` 的特征值，因此 `c∗` 在 `sppT∗` 中。

### Example 13.23

设 `T: l²→l²`![方程](img/F000138si167.png)，其中 `T(v0, v1, v2, …)=(v0, 0, v1, 0, v2, …)`。算子 `T` 在复数域上产生一种拉伸类型的运算。此运算也称为扩张或步幅。`T` 的谱是 `C` 中的闭单位圆盘。为了看到这一点，首先考虑伴随算子。观察它对第 k 个基向量 `vk` 的作用，其中 `vk=(0, 0, 0, …0, 1, 0, 0, …)`，1 在第 k 个元组处。因此对于任意 `w` 在 `l²`![方程](img/F000138si168.png) 中，根据伴随的定义：`<T∗vk, w>=<vk, T w>=T(wk)=0` 对所有奇数 `k` 成立，而对于偶数 `k`，可推出 `T(wk)=w(k/2)`。同样，`T∗vk=0` 对奇数 `k` 成立且对偶数 `k` 等于 `v(k/2)`。



为了确定伴随算子是什么，在 *l*² 中取 `w`![方程](img/F000138si169.png)。取 `<w, Tv>=w0∗v0+w1∗ 0+w2∗v1+w3∗ 0+w4∗v2+….` 该表达式等于 `<T∗w, v>=w′0∗v0+w′1∗v1+w′2∗ v2+w′3∗v3+w′4∗ 0+w′5∗v2+….` 使 `vk` 的元组系数相等，其中 `k=0, 1, 2, ….` 这意味着 `T∗(v0, v1, v2, …)=(v0, v2, v4, …)`。任意满足 `|c|<1` 的 `c` 都是 `T∗` 的特征值。为了看到这一点，使用 $v\\left( c \\right) = {sum},\\sum\_{k = 0}^{\\infty}{c^{k}v2^{k}}$![方程](img/F000138si170.png)；然后 `T∗v(c)=T∗v1+the sum`，$\\sum\_{k = 1}^{\\infty}{c^{k}T \\ast v2^{k}}$![方程](img/F000138si171.png)。首先，`T∗v1=0`，因为 1 是奇数。$T \\ast v(c) = {sum},\\sum\_{k = 1}^{\\infty}{c^{k}v2^{k - 1})} = {cv}(c)$![方程](img/F000138si172.png)。由此可知 `c` 是 `T∗` 的特征值。因此，对于每一个满足 `|c|<1` 的 `c`，该值都是特征值。但是，由于谱总是闭的并且 `‖T∗‖=1`，因此 `sp(T∗)=sp(T)=闭单位圆盘`。

对于 `H` 上任意闭算子 `T`，`T∗` 的谱是集合 `{c∗, such that c is in spT}`；此外算子 `T∗` 在 `c` 处的预解算子满足 `Rz(c∗)=Rz (c)∗`。其中 `T` 在 `c` 处的预解算子为 `Rz (c)`。该结果类似于 `Lumer-Phillips` 结果。

## 13.8 自伴、正则和紧算子的谱

已知对于 `B(H)` 中的自伴算子，不存在剩余谱，而且谱总是实数。`B(H)` 中算子的近似特征值满足：对于任意 *ϵ*![方程](img/F000138si173.png)\> 0，存在 `H` 中的单位向量 `v`，使得 `‖Tv−λv‖<ϵ`![方程](img/F000138si174.png)。将 `v` 替换为 `w /‖w‖`（`w` 不为零），等价条件如下：对于任意 *ϵ*![方程](img/F000138si175.png)\> 0，存在 `H` 中的非零向量 `w`，使得 `‖Tw−λw‖<![ε](img/epsi_1013.png)‖w‖`；则 `λ`![方程](img/F000138si176.png) 是 `T` 的近似特征值。所有这样的 `λ`![方程](img/F000138si177.png) 的集合称为 `T` 的近似谱。记为 `A(T)`。如果 `T` 有特征值，则它属于 `A(T)`，因为 `Tv−λv` 恒等于零。此外，`A(T)` 是一个真正的谱，因为 `A(T)` 是 `spT` 的子集。该结果可由反证法得到。如果 `λ`![方程](img/F000138si178.png) 不在 `spT` 中，则 `T−λI` 可逆。这意味着 `∥v∥=∥(T−λI)^(−1)`![方程](img/F000138si179.png) `(T−λI) v∥` 小于或等于 `∥(T−λI)^(−1)∥∥Tv−λv∥`![方程](img/F000138si180.png)，对每个向量 `v` 成立，即 `∥Tv−λv∥`![方程](img/F000138si181.png) 大于或等于 `1/∥(T−λI)^(−1)∥∥v∥`![方程](img/F000138si182.png)。令 `ϵ=1/∥(T−λI)^(−1)`![方程](img/F000138si183.png)‖ 可知 `‖Tv−λ`![方程](img/F000138si184.png) `v‖` 有下界，因此 `λ`![方程](img/F000138si185.png) 不在 `A(T)` 中，这是一个矛盾。所以结论是 `A(T)` 总是 `spT` 的子集。

对于有界正规算子，除了前面提到的结果之外，还有更多结论成立；这里 `spT=A(T)`，这之前已提到。也就是说，对于正规算子 `T`，所有特征值都是近似的。需要证明的是 `spT` 是 `A(T)` 的子集。再次使用反证法。先假设 `spT` 中存在特征值 `λ`![方程](img/F000138si186.png)，它不在 `A(T)` 中。那么对于某个 `ϵ`![方程](img/F000138si187.png)\> 0，该特征值满足对所有非零 `v`，`‖Tw−λw‖` 大于或等于 ![ε](img/epsi_1013.png)‖w‖。由于 `T` 是正规的，可知 `‖T∗w−λ∗w‖` 大于或等于 ![ε](img/epsi_1013.png)‖w‖ 对所有非零 `v` 成立。因此 `‖Tw−λw‖` 和 `‖T∗w−λ∗w‖` 都有下界，见 第 13.1 节。如果能证明它们的值域是稠密的，则会产生矛盾，因为特别地，`Tw−λw` 将是可逆的。而不是证明值域稠密，等价于证明值域的正交补是 `{0}`。这因为 `ran(u)^⊥=ker(u*)`![方程](img/F000138si188.png)，或 `ker(u*)^⊥=clos(ran(u))`![方程](img/F000138si189.png)。所以如果 `v` 与 `Tw−λw` 正交，即 `<v, Tw−λw>=0` 对所有 `w` 成立，利用伴随算子，这等价于 `<T∗v- λ∗v, w>=0` 对所有 `w` 成立。后一个等式意味着 `T∗w−λ∗w=0`。然而，利用之前的有下界性质 `∥T∗w−λ∗w∥`![方程](img/F000138si190.png) 大于或等于 `ϵ`![方程](img/F000138si191.png)‖w‖ 可知 `w=0`。

对于正规算子，`T` 与 `T∗` 的特征值之间的关系很容易证明。下面的例子说明了这一事实

### 例 13.24

对于 `B(H)` 中的正规算子 `T`，如果 `T v = λ v`![方程](img/F000138si192.png) 对 `H` 中的非零 `v` 成立，则 `T∗ v = λ∗ v`![方程](img/F000138si193.png)。这可通过令 `A` 由 `T` 的所有特征向量组成，其中 `λ`![方程](img/F000138si194.png) 是特征值来得到。然后由于 `T(T∗v)=T∗(Tv)=T∗ (λ v)=λ (T∗v)`，可知 `T∗v` 在 `A` 中。考虑内积 `<u, T∗v−λ∗v>`，假设 `u` 也在 `A` 中。由此可得 `<u, T∗v−λ∗v>=<u, T∗v>−<u, λ∗v>=<T u, v>−λ∗<u, v>=<λ u, v>−<λ u, v>=<T u−λ u, v>=0`。由于 `T∗v` 在 `A` 中，以及 `v` 的任意非零常数倍，可知 `T∗v−λ∗v` 在 `A` 中。进而可得 `T∗v=λ∗v`。

对于希尔伯特空间 `H` 上的紧自伴算子 `T`，其谱是实值的点谱，最多例外为零。零点可能是聚点，因此可能不在点谱中。在这种情况下，它属于连续谱。再次，算子 `T` 可表示为向特征子空间 `{an, such that Tv=an, for v nonzero in H}` 的投影的收敛和。也就是说，`Pn` 是向该特征子空间和 `an` 的投影，且 `T` 是和 `∑`![方程](img/F000138si195.png) `(an Pn)`。另外，对于 `H` 中的任意 `w`，有 `Tw` 等于和 `∑`![方程](img/F000138si196.png) `(an Pn(w))`。

### 例 13.25

考虑希尔伯特空间 `H` 上的紧自伴算子 `T`。这种算子可能只有点谱，且特征值为 0。因此，在这种情况下，0 不是聚点；它是孤立点。根据正规紧算子的投影定理，`perp(ker(T))` 不能是无限的。因为如果它有一个无限的 `ON` 基 `{ek}` 且 `Tek=ck ek`，并且 `ck→0`，则 0 不是孤立的（Conway, 1990）。因此，`perp(ker(T))` 是有限的，所以 `Ker(T)=0` 有无限维。并且可知存在可数无限个向量，它们的特征值都为 0。

如果 `T` 和 `S` 是 `H` 上的紧算子，则乘积 `TS` 和 `ST` 是紧的，伴随算子 `S∗` 和 `T∗` 也是紧的。此外，`T∗T` 是自伴且正的；因此它有非负特征值 `an`。当 `T` 的一范数有限时，紧算子 `T` 称为迹类算子。一范数是 `‖T‖`，它满足 `T∗T` 的特征值 `an` 的平方根之和是有限的。

对于迹类算子 `T`，迹定义如前：`Tr (T)` 是内积之和：`<en, T en>`，其中 `en` 是 `H` 上的 `ON` 基。此外，该级数必须绝对收敛且与所用的 `ON` 基无关。当 `T` 也是自伴时，则 `Tr (T)=T 的实特征值之和`。另外，对于 `H` 上的酉算子 `U`，有迹：`Tr(T)=Tr(U^(−1)T U)`![方程](img/F000138si197.png)。见 第 7.5 节。

## 13.9 纯态与密度函数



最重要的迹类算子之前给出的是纯态 `Rz`。它也被称为密度算子，因为在形成期望值时它像概率密度函数一样起作用。因此，它是非负的且 `Tr(Rz)=1`。`Rz` 的特征值 `an` 在 `(0, 1\]` 中。投影 `Pn` 到特征空间是 `Rz`，且它等于和 ∑![方程](img/F000138si198.png) (`an Pn`)，其中所有 `an` 的和等于一。

态被定义为 C∗ 代数 `A` 上的线性泛函 `g`。即，`g: A→C`。它还必须满足：
1. 1) 非负：`g(T* T)` 对所有 `T` 在 `A` 中大于或等于零。
2. 2) 单位元：`g(I)=1`。

可以证明如果 `g` 是 `A` 上的线性泛函，其中 `g(I)=‖g‖=1`，则 `g` 是一个态。即，非负性可以从 `g` 的范数等于一得到 (Murphy, 2014)。

关于 C∗ 代数 `A` 上任意非负线性泛函 `g` 的一些有用事实将被列出。这里，`T` 和 `S` 是 `A` 中的算子，通常称为可观测量，且 `I` 是 `A` 中的单位算子：
1. 1) CBS 型不等式：`|g(T* S)|²`![方程](img/F000138si199.png) 小于或等于 `g(T* T) g(S* S)`。
2. 2) 共轭：`g(S*)=g(S)*`。
3. 3) 一律：`g(I)=‖g‖`。
4. 4) 范数界：`g(T* S* S T)` 小于或等于 `‖S‖² g(T* T)`![方程](img/F000138si200.png) (Murphy, 2014)。

范数界是一种 CBS 不等式。纯态之前已以几种不同的方式描述。其中一种涉及向量空间内的凸集中的射线。回想一下，凸集 `S` 具有这样的性质：对于 `S` 中任意两个向量 `u` 和 `v`，连接这两个向量的线段完全位于 `S` 中。即，`a v+(1−a) u` 对所有 `a` 在 `[0, 1]` 中属于 `S`。当 `a v+(1−a)u=w` 且对所有 `a` 在 `(0, 1)` 中 `u=v=w` 时出现极值点。因此，凸线段上的极值点是该线段的端点。在 C∗ 代数中，极值点的集合称为纯态，属于希尔伯特空间上的有界算子空间。一个例子将被给出。

### 示例 13.26
C∗ 代数 `A` 上的迹是一个正线性泛函 `f: A→C`，使得对所有 `T` 和 `S` 在 `A` 中：
1. 1) 迹性质成立 `f(TS)=f(ST)`。
2. 2) 正性意味着 `f(T* T)` 对 `T` 在 `A` 中大于或等于零。而且，只要 `f(T* T)=0` 仅当 `T=0` 时，迹被称为忠实的。忠实意味着对于正映射 `g`，如果 `S` 大于或等于零且 `g(S)=0`，则必须有 `S=0`。

所有 `n` 阶复值矩阵的单位结合代数是一个 C∗ 代数，且迹是对角元素的和，`Tr(|a><b|)=<b, a>`。所以，例如，在 `C²`![方程](img/F000138si201.png) 中，如果 `a=(2 i)′` 且 `b=(3 4i)′`，则 `<b, a>=10`。外积 `T=a><b` 给出如下，其中 `T* T` 是具有正迹的共轭对称矩阵：

$\\begin{matrix} \\left| 100 \\right. & \\left. - 80i \\right| & \\left| 45 \\right. & \\left. - 60i \\right| \\\\ \\left| 80i \\right. & \\left. 80 \\right| & \\left| 60i \\right. & {\\left. 80 \\right|.\\#} \\\\ \\end{matrix}$

![方程](img/F000138si202.png)

## 13.10 谱和预解集
解析泛函演算将在 Banach 代数 `B` 中算子 `T` 的谱和预解集上进行研究。回想一下，预解集 `RsT` 是 `C` 中 `T` 的谱 `spT` 的补集。对于 `RsT` 中任意复变量 `z`，算子 `(z−T)` 是可逆的。它定义了 `T` 的预解算子，记为 `Rz(T) = (z−T)^(-1)`![方程](img/F000138si203.png)。只要 `|z|` 大于 `T` 的谱半径 `r(T)`，就可以对 `(z - T)^{-1} = z^{-1}(1 - T/z)^{-1} = sum, sum_{k = 0}^{∞} z^{-1} T^{k} z^{-k}`![方程](img/F000138si204.png) 作 Laurent 展开。预解算子在 `|z|> r(T)` 时是解析的。

`T` 的预解公式对于点 `z` 给出为 `Rz(T) = (z−T)^(-1)`![方程](img/F000138si205.png)。因此，单位元 `I=(z−T) Rz(T)=Rz(T) (z−T)`。对于点 `w`，也有 `I=(w−T) Rw(T)=Rw(T) (w−T)`。据此，可以写出 `Rz(T)−Rw(T)=Rz(T) (w−T) Rw(T)−Rz(T) (z−T) Rw(T)=Rz(T) (w−T)−(z−T) Rw(T)=Rz(T) (w−z) Rw(T)=(w−z) Rz(T) Rw(T)`。因此，`Rz(T)−Rw(T)=(w−z) Rz(T) Rw(T)`。通过完全相同的论证，可得 `Rw(T)−Rz(T)=(z−w) Rw(T) Rz(T)`。由这两个恒等式可得结论 `Rz(T) Rw(T)=Rw(T) Rz(T)`。

现在，复多项式 `p(z)` 将再次被考虑。这次将采用 Cauchy 积分定理 CIT。该积分通常利用开集内的闭路径。它必须包围来自 Banach 代数的算子 `T` 的谱 `spT`。预解集是开的，且 `spT` 是非空紧集。由于预解算子是解析的，乘积 `p(z) Rz(T)=p(z)/(z−T)` 是解析的。而且，积分的闭路径位于 `RsT` 中。CIT 给出 `p(T)=1/(2π i) ∫`![方程](img/F000138si206.png) `(p(z)/(z-T)) dz`。所有积分都是沿闭路径进行的。对于单条围道积分，取向在有限 `z` 平面中为逆时针。在这些假设下，可以给出如下界：`‖p (T)‖` 小于或等于 `(1/2π) max |p| sup ‖(T−z)^(-1)‖ ∫ d|z|`![方程](img/F000138si207.png)。

可以使用整函数执行前面提到的相同过程。所有多项式情形中的假设必须成立。由于积分路径是闭合、可求长、有向曲线，多项式或任何解析函数就其本身而言的最大值将在边界上。因此，当使用任何整函数时，同样类型的界成立。一般而言，亚纯函数尚不能处理。然而，对于任何有理函数，由于至多只有有限个极点，过程与之前相同。在这种情况下，分母的零点必须包含在其各自的闭合积分路径内，从而得到谱分解。部分分式展开以及 CIT 或留数理论的使用将提供解。再次微妙地使用了预解算子的可交换性，即 `Rz(T) Rw(T)=Rw(T) Rz(T)`。

对于谱 `spT` 邻域上的解析函数 `f(z)`，可得 `f(spT)=spf(T)`，其中 `T` 在 Banach 空间 `X` 中有界。这称为谱映射定理，其基于 Riesz-Dunford 演算。关于该定理的众多推广见 Haase (2005)；这里考虑了无界的可逆算子以及复平面的不同区域。

## 13.11 非有界算子的谱
非有界函数可能使其谱包含无穷远点。这里，我们将复平面视为在 Riemann 球面上扩展。该球面在几何上由立体投影给出，在拓扑上由局部紧 Hausdorff 空间的单点紧化给出。而且，它是一个复一维流形。在任何情况下，都可以使用包围无穷远点的 CIT 和其他闭路径积分。在这种情况下，积分路径的取向必须反转。积分路径始终为逆时针包围奇点。



为继续进行，令 `w=1/z`。在下面，暂时略去常数 `1/(2*π*i)`，并记住所有积分都是闭合的。从 `CIT` 开始，`CIT=integral`，∫![Equation](img/F000138si208.png) (`f(w) / (w−a) dw`)。然后，积分元由 `dw = -1/z² dz`![Equation](img/F000138si209.png) 给出。`CIT` 中的被积函数：`f(w) / (w−a)=f(1/z)/(1/z−a)`。接下来在新的被积函数上使用部分分式：`f(1/z)/(z−a z²)=f(1/z)/z + z f(1/z)/(1−z a)=f((1/z)/z+f(1/z)/(a^(−1)−z)`![Equation](img/F000138si210.png)。这必须以相反的方向积分。因此必须包含一个负号；也就是说，结果为 `-f(evaluated at infinity)=1/(2πi)∫f(1/z)/(z−a^(−1))`![Equation](img/F000138si211.png)。后一个积分要么通过柯西公式为 0，要么通过 `CIT` 等于 `f(a)`。换句话说，积分的值取决于 `a^(−1)`![Equation](img/F000138si212.png) 是否在积分路径之外。
将考虑无界算子的谱。首先回顾，对于有界算子，在 Banach 代数中预解集是开的。另外，预解式是解析的。谱总是非空且紧的。对于无界闭算子，谱将是闭的。然而，在这种情况下，谱可能是 `C` 的全部或空集。回忆一下，空集和全集既是开的也是闭的。如有界情形一样，闭算子的预解式公式可交换。对于无界算子，无穷远点（黎曼球面上的北极）可能在谱中。因此，无穷点也可以是解析点。

### 示例 13.27
这是谱为空的算子 `T` 的一个例证。该算子已在 示例 13.18 中说明。它在 `L²[0, 1]` 上稠密定义且是闭算子。令 `T=d/dt`，其中定义域 `T={f absolutely continuous. such that f′ in L²[0,1]`![Equation](img/F000138si213.png)，且 `f(0)=0}`。为了证明 `spT=empty set`，将证明预解集是整个复平面，即 `RsT=C`。对于 `g in L²[0,1]`![Equation](img/F000138si214.png)，微分方程 `f′−λ`![Equation](img/F000138si215.png) `f=g`，`f(0)=0` 的解通过参数变异求得为：`f(t)=∫[0]^(t) e^(λ(t−x)) g(x) dx`![Equation](img/F000138si216.png)。预解式对所有 `λ`![Equation](img/F000138si217.png) ∈ `C` 都存在，因为 `RsT(g)=(T−λI)^(−1)(g)=∫[0]^(t) e^(λ(t−x)) g(x) dx`![Equation](img/F000138si218.png)。这可以验证：
```
g = (d/dt−λ)∫[0]^(t) e^(λ(t−x)) g(x) dx = e^(λ(t−t)) g(t) + λ∫[0]^(t) e^(λ(t−x)) g(x) dx − λ∫[0]^(t) e^(λ(t−x)) g(x) dx = g(t)
```
![Equation](img/F000138si219.png)。对于 `T` 的定义域 `dom(T)` 中的 `f`，`f(t)=∫[0]^(t) e^(λ(t−x)) g(x) dx`![Equation](img/F000138si220.png) 对应于 `L²[0,1]`![Equation](img/F000138si221.png) 上的有界算子，对所有 `λ`![Equation](img/F000138si222.png) ∈ `C` 成立。

### 示例 13.28
设 `T` 是希尔伯特空间 `H` 上的正规算子，可能无界。则 `spT` 非空。若假设相反，则 `T^(−1)`![Equation](img/F000138si223.png) 是有界算子，其谱 `sp T^(−1)`![Equation](img/F000138si224.png) 至多为 `{0}`。这可由 `λ`![Equation](img/F000138si225.png) 不等于零时 `(T^(−1)−λI)=(I−λT)T^(−1)=λ(I/λ I−T)T^(−1)=X`![Equation](img/F000138si226.png) 得到。算子 `X` 有有界逆：`X^(−1)=1/λ T (1/λ I−T)^(−1)`![Equation](img/F000138si227.png)。有界正规算子的范数与谱半径相同，这意味着 `T^(−1)=0`![Equation](img/F000138si228.png)，从而产生矛盾。如果 `T` 是谱为空的无界算子，则 `T^(−1)`![Equation](img/F000138si229.png) 有界且零在预解集中。

## 13.12 谱测度和谱定理的简要描述
谱定理有许多版本。首先给出一个最强大的版本，Haase (2018) 称之为希尔伯特空间 `H` 上正规算子 `T` 的乘性版本。在这种情况下，`T` 与半有限测度空间中某个 `L²`![Equation](img/F000138si230.png) 空间上的乘法算子酉等价。半有限测度在附录 A.2 中描述。快速回顾一下，若对测度空间 `M` 中每个 `E`，其测度 `μ`![Equation](img/F000138si231.png) (`E`)=∞![Equation](img/F000138si232.png)，存在可测集 `F` 是 `E` 的子集使得 `0 < μ(F) < ∞`![Equation](img/F000138si233.png)，则称该测度为半有限。σ-有限测度总是半有限测度。
希尔伯特空间 `H` 中正规算子 `T` 的谱定理指出，存在酉算子 `U`，使得 `T:H→L²(S), T*=U^(−1) M U`![Equation](img/F000138si234.png)。这里，`S` 是半有限测度空间，可以是局部紧空间中的 Radon 测度。`M` 表示 `L²(S)`![Equation](img/F000138si235.png) 中的连续乘法运算。该谱定理表明希尔伯特空间中的正规算子在 `L²`![Equation](img/F000138si236.png) 中具有乘性表示；然而，它们不是唯一的。对于自伴算子 `T`，存在实值可测函数 `f`，对应于酉算子的乘法：`U:H→L²`![Equation](img/F000138si237.png)，涉及测度空间 `M`，其中 `U T U^(−1)`![Equation](img/F000138si238.png)。该乘法算子涉及 `f`，其定义域为 `{g in L²`![Equation](img/F000138si239.png)，使得 `f g in L²}`。当 `H` 可分时，如无特别说明所假设的那样，可以采用有限测度空间。
将对有界自伴算子 `T`，`T: H→H`，其中 `H` 是 `C` 上的希尔伯特空间，简要描述谱定理的一个更简单的版本。这里，`T` 由投影值测度 `PVM` 给出。`T=∫ λ dE[λ]`![Equation](img/F000138si240.png)。在这种情况下，积分被理解为 Stieltjes 积分（Apostle, 1974；Rudin, 1987），这里，`E[λ]`![Equation](img/F000138si241.png) 称为积分器，是投影到由 `T[λ]^+ = 1/2{(T−λI)+[(T−λI)*(T−λI)]^(1/2)}`![Equation](img/F000138si242.png) 的正部组成的零空间。由于 `T` 是自伴的，平方 `(T−λI)²`![Equation](img/F000138si243.png) 的正平方根可以出现，代替括号部分。最后，积分限从下限开始，下限等于最小特征值 `m` 的最小值，或连续谱的下确界，到上限，上限为最大特征值 `M` 与连续谱上确界中较大者。此外，形式为 `f(T)=∫ f(λ) dE[λ]`![Equation](img/F000138si244.png) 的泛函演算积分将在 第 19 章 中考虑。

### 示例 13.29




本例的目的是说明 Stieltjes 积分在 `R` 中的应用。本例中的被积函数是连续的，例如 `f(x) = x³`![方程](img/F000138si245.png)。积分器 `F(x)` 在 `x=1` 处不连续，且在 `0, 1)` 上等于 `x²`![方程，在 `[1, 2]` 上等于 `2x`。积分 `L = ∫[x=0]² x³ dF(x) = ∫[x=0]¹ 2x⁴ dx + 1³ + ∫[x=1]² 2x³ dx`![方程](img/F000138si247.png)。中间项涉及 saltus 或在 `t=1` 处从左极限到右极限的跳跃量。另外，Riemann 积分是通过 `dF(x)=2 x dx` 在 `[0, 1)` 上得到的。而 `dF(x)=2` 在 `[1, 2]` 上。也可以使用 delta 函数代替 Stieltjes 积分。在任何情况下，继续计算得到 `L=2/5+1+8–1/2`。

## 参考文献
*   Apostle, 1974 Apostle T. *数学分析* 2 版. Pearson Pub Co 1974;.
*   Conway, 1990 Conway J. 978-0-387-97245-9  *泛函分析教程*. vol. 96 Springer-Verlag 1990;.
*   Delaubenfels, 1988 Delaubenfels R. 全增算子. *Proc AMS*. 1988;103.
*   Engel and Nangel, 2000 Engel K, Nangel R. *线性发展方程的一参数半群* Springer 2000;.
*   Gustafson and Rao, 1997 Gustafson K, Rao D. *数值范围 线性算子与矩阵的值域* Springer 1997;.
*   Haase, 2018 Haase, M., 2018. 泛函分析讲义. In: 21st International Internet Seminar.
*   Haase, 2005 Haase M. *全纯函数演算的光谱映射定理* London Math Sci 2005;.
*   Hall, 2013 Hall B. *数学家的量子理论* Springer 2013;.
*   Halmos, 1957 Halmos P. *希尔伯特空间导论与谱重数理论* Dover 1957;.
*   He’lein, 2014 He’lein F. *谱理论* U. of Paris 2014;.
*   Lumer and Philips, 1961 Lumer G, Philips R. Banach 空间中的耗散算子. *Pac J Math.* 1961;11.
*   Murphy, 2014 Murphy G. *C∗ 代数与算子理论* Academic Press 2014;.
*   Park, 2013 Park E. *希尔伯特空间中的无界算子* Texas Christian University 2013;.
*   Reed and Simon, 1980 Reed M, Simon B.  *现代数学物理方法*. vol 1 Academic Press 1980;.
*   Rudin, 1987 Rudin W. *0070542341 数学分析原理* Mc Graw Hill 1987;.
*   Shapiro, 2004 Shapiro J. *数值范围讲义* CARMA 2004;.
*   Stack Exchange, 2016 Stack Exchange, 2016. 近似点谱与剩余谱之间的非空交集，分部积分。
*   StackExchange, 2015 StackExchange, 2015. Mathematics, Summary: Spectrum vs Numerical Range.
*   Teschl, 2009 Teschl G. 978-0-8218-4660-5 *量子力学中的数学方法* AMS 2009;.
*   Wells and Williams, 2012 Wells J, Williams L. *分析中的嵌入与扩张* Springer 2012;.
*   Woozy, 2017 Woozy S. *对称算子的自伴扩张* University of Konstanz 2017;.

# 第 14 章
## 正则对易关系
### 摘要
在 `C*` 代数中描述了多种保距离映射，包括等距映射和酉映射。本章提供了多排序代数 (`MSA`) 中正则超群的描述以及应用。Cayley 变换用于将酉算子与自伴算子联系起来。引入了涉及希尔伯特空间初始空间和终结空间的部分等距映射。这导致了涉及等距映射串的 `MSA` 描述。给出了 `C*` 中有界算子为部分等距的等价判据并予以证明。具体提供了伪逆判据。伪逆在后面的章节中用作估计工具。陈述了关于一参数群的 Stone 定理，并在角动量以及李群 `SO(3,R)` 上进行了说明。正则对易关系 (`CCR`) 特有的位置和动量运算是本章中的重要主题。随后给出了 Heisenberg 群的描述以及量子力学等价性的回顾。下一节给出了 `MSA` 方法在辛向量空间中的发展。本章以 Weyl `CCR` 公式结束。
#### 关键词
正则超群；部分等距；伪逆；Stone 定理；Weyl 的 CCR

## 14.1 等距与酉运算
设 `U` 是 `C*` 代数 `A=B(H)` 的一个元素。`U` 在保持范数时称为等距，即 `‖U v‖=‖v‖`，对所有 `v` 在 `H` 中成立。在这种情况下，将证明 `U* U=I`。此外，当 `U` 为满射时，它成为酉算子，然后它也是可逆的，即 `U` 有逆。然而，等距不一定是酉的。这在 示例 14.1 中得以说明。也是一个涉及广义位移或平移算子及超群的例子。超群是涉及多值运算的超结构。在超群中，有一种二元型运算，将来自非空集合 `H` 的元素对映射到 `H` 的子集，且该子集非空。该运算有时称为加法。非常经常，集合 `H` 具有额外的结构，例如 `C*` 代数或希尔伯特空间等等。下一节使用 `MSA` 引入正则超群结构。量子中的应用将在后面的章节中说明 (Corsini and Leoreanu, 2003)。
### 示例 14.1
设 `U` 在载体集 `H = l²`![方程](img/F00028Xsi1.png) 上作用，即所有复数序列的希尔伯特空间，使得项的绝对值平方之和收敛。因此如果 `U: l²→l²` 其中算子 `U` 将项向右平移：`U: (a0, a1, a2,…)=(0, a0, a1,…)`, 则 `U` 是等距，因为范数被保持：`‖(a0, a1, a2,…) ‖=‖ (0, a0, a1,…)‖`。但 `U` 不是酉算子。注意 `(1, 0, 0,…)` 不在 `U` 的值域中。因此，如果要为 `U` 定义逆，只能在其值域上定义，而不能在整个 `H` 上定义。`U` 不是满射，因此 `U` 不是酉运算。
注意只要 `U` 是希尔伯特空间 `H` 上的算子且是等距，则对任意 `v` 和 `w` 在 `H` 中，若 `‖U v‖=‖v‖` 则 `<U v, U w>=<v, w>` 成立。作为推论，等距同时保持内积和范数。这将通过证明两个内积的实部和虚部相等来看到。首先考虑，`‖U (v+w)‖² = ‖v‖²+‖w‖²+2 Re (<U v, U w>) = ‖(v+w)‖²`, 且通过代入 `‖U (v+w)‖² = ‖v‖²+‖w‖²+2 Re (<v, w>)`。因此，`Re (<U v, U w>) = Re (<v, w>)`。再次形成范数平方，但这次使用 `‖U (v+i w)‖² = ‖v‖²+‖w‖²+2 im (<U v, U w>) = ‖(v+i w)‖² = ‖v‖²+‖w‖²+2 im (<v, w>)`。在这种情况下，可得 `im(<U v, U w>) = im (<v, w>)`。由于实部和虚部都相等，这意味着 `<U v, U w> = <v, w>`。



## 14.1 等距映射、酉算子与正性

设 `U` 是希尔伯特空间 `H` 上的一个算子，并假设它是等距映射。也就是说，对于 `H` 中的任意 `v` 和 `w`，有 `<U v, U w>` = `<v, w>`。利用伴随的定义，即 `<U v, U w>` = `<U* U v, w>`，据此 `U*U` = `I`，因此 `U*U` 在 `C*` 代数中如同恒等式。注意这是一个单侧恒等式。再次设 `U` 是 `C*` 中的等距映射，作用于希尔伯特空间 `H` 中的元素，`v` 和 `w` 在 `H` 中。它总是 1–1，即 `U` 是单射。这是因为 `‖U v−U w‖` = `‖v−w‖`，所以 `U v` = `U w` 当且仅当 `v` = `w`。当 `U` 也是满射，即满射时，它是可逆的，因此 `U U*` 也等于恒等式 `I`。在这种情况下，`U` 是酉算子，`U*U` = `U U*` = `I`。相应地，`U` 也是正规算子；换句话说，`U` 与其伴随 `U*` 可交换。此外，对于 `H` 中非零的 `v`，`‖U*U v‖` = `‖v‖` 大于或等于零，因此 `U*U` 是正算子。正算子的谱始终位于实数轴的非负部分。酉算子的谱始终位于 `C` 中的单位圆上。因此，`U U*` 的谱只是点一。

### 示例 14.2

对于 `T`: `H`→`H`，其中 `H` 如常为复可分希尔伯特空间且 `T` 为正算子，即 `<v, T v>` 大于或等于零对所有 `v` 在 `H` 中成立。由此可知 `T` 也是自伴的。这里必须证明 `T` = `T*`。由于 `T` 为正，则意味着 `<v, T v>` 为实值，因而 `<v, T v>` = `<v, T v>*` = `<T v, v>` = `<T* v, v>`。现在设 `S` = `T` − `T*`，于是 `<S v, v>` = `<(T − T*) v, v>` = 0，但这并不能说明 `T` = `T*`，因为该内积表达式中只涉及单个向量 `v`。要得出 `T` = `T*` 的验证，需要极化恒等式，并使用 `v` 和 `w`。设 `<S v, w>` = 1/4 { `<S(v+w), v+w>` − `<S(v−w), v−w>` + i `<S(v+ i w), v+ i w>` − i `<S(v− i w), v− i w>` } = 0。这对所有 `v` 和 `w` 在 `H` 中成立，从而证明 `T` = `T*`。

### 示例 14.3

与前例类似，设 `T` 为正算子，即 `<v, T v>` 大于或等于零对希尔伯特空间 `H` 中的所有 `v` 成立。这次，假设 `H` 为实希尔伯特空间，等于 `R²`。因此希尔伯特空间的载体集现在是实向量空间。由此可知 `T` 不是对称的。为此设 `T` =

$\\begin{matrix} {|0} & {{- 1}|} \\\\ {|1} & {0|} \\\\ \\end{matrix}.$

![方程](img/F00028Xsi2.png)

然后，若对 `H` 中任意向量 `v` 有 `v` = `(a b)'`，则 `<v, T v>` = `<(a b)', (−b a)'>` = 0，但 `T` 不等于 `T*`。

### 示例 14.4

Cayley 变换可用于关联自伴算子与酉算子。特别地，对于希尔伯特空间 `H` 上的自伴算子 `T`，Cayley 变换 `(z−i)/(z+i)` 是来自复变量的一种特殊 Möbius 变换。此运算将 x 轴映射到单位圆上。除在 −i 处有一个简单极点外，它是解析的。具体地，将 Möbius 变换用作一参数群：`f(z)` = `(z + i t)/(z − i t)`，其中 `t` 为实数。因此，`[(T + i t)/(T − i t)]*` = `(T − i t)/(T + i t)` = `[(T + i t)/(T − i t)]^(−1)`，从而表明 `f(T)` 是酉的。

与前例中的说明类似，第 14.5 节 专门用于关联自伴算子与酉算子。事实上，这里 Stone 定理说明了酉算子的一参数族与自伴算子之间的关系。

此外，von Neumann 代数已在 第 9 章 中描述。然而，在这方面将等距映射与酉变换联系起来是很有趣的。这里，von Neumann 代数 `V` 是 `B(H)` 的子集，当且仅当所有等距映射都是酉变换时它是有限维的（Sakai, 1971）。

## 14.2 规范超群——多排序代数视角

超群是一种多值运算，具有一种二元型运算，将集合 `H` 中的元素对映射到 `H` 的子集。因此它将一对点映射到一个集合。它是一个集合值函数。从规范超群的 MSA 视角来看，存在两种排序，分别是 `ELEMENTS` 和 `SUB`。第一种排序表示来自非空集合 `H` 的元素；该集合不必是希尔伯特空间。第二种排序 `SUB` 表示来自 `H` 的所有非空子集。与群类似，存在三个签名集，每个算子名各一个，元数为 0、1 和 2：`ZERO`、`MINUS` 和 `ADD`。第二种排序 `SUB` 是 `H` 的非空幂集。由于 `SUB` 不包含空集，它由 `2^(H')` 表示 ![方程](img/F00028Xsi3.png)。撇号表示 `2^(H')` = `2^(H)` − `ϕ` ![方程](img/F00028Xsi4.png)。因此，用相应的符号替换以下算子名：

* `ZERO`，0 在 `H` 中。
* `MINUS`: `H`→`H`。
* `ADD`: `H x H`→`2^(H')` ![方程](img/F00028Xsi5.png)。因此对于 `H` 中的 `a` 和 `b`，`ADD(a,b)` = `S`，其中 `{a+b}` 是 `S` 的子集。

多值图为规范超群的这些闭包运算提供了一个说明。参见 图 14.1。算子序列再次为 (1, 1, 1)，与群相同。然而，等式恒等式与常规群相比大不相同。

![图 14.1 规范超群多值图.](img/F00028Xf14-01-9780443136979.jpg)

图 14.1 规范超群多值图。

相应的算子被扩展以允许集合运算。因此令 `ZERO` 用 0 表示，`MINUS` 用 − 符号化，而对于 `ADD`，使用 +。另设 `A` 和 `B` 为 `H` 的非空子集；则 `A+B` = `{a+b, for all a in A and b in B}`。注意顺序；一般而言，超群可能不可交换。为强调这一点，设 `x+A` = `{x+a, where a is in A}` 且 `A+x` = `{a+x, where a is in A}`，因此 `A+x` 不一定等于 `x+A`。

为了使等式恒等式成立，设 `A`、`B`、`C` 和 `X` 为 `H` 的非空子集，并设 `x`、`y` 和 `z` 为 `H` 中的元素，则：

1. 1) 结合性：`A+(B+C)` = `(A+B)+C`。这应理解为对所有 `a` 在 `A` 中，对所有 `b` 在 `B` 中，最后对所有 `c` 在 `C` 中，以下成立：`a+(b+c)` = `(a+b)+c`。

2. 2) 零元性质：`0+x` = `x+0` = `{x}`。其含义是当二元算子对 `x` 应用且其一个参数为零时，则出现单例型子集，即 `{x+0}` = `{x}`。

3. 3) 负元性质：`x+(−x)` = `(−x)+x` = `X`，其中 0 是 `X` 的元素。这表明 `H` 的子集 `X` 将在 `ADD` 的任一运算元为另一运算元的负数时包含 `H` 中的 `ZERO`。

4. 4) 循环性质：对于 `x` 在 `{y+z}` 中，这意味着 `z` 在 `{x−y}` 中。这里在使用减法作为二元运算时采取了自由。事实上 `{x−y}` = `{x+MINUS(y)}`。

如果再加上等式恒等式 (5) 成立，则超群称为阿贝尔。

5. 5) 交换性：`A+B` = `B+A`。这应理解为对所有 `a` 在 `A` 中和所有 `b` 在 `B` 中，以下成立：`a+b` = `b+a`。

### 示例 14.5

考虑集合 `H` = `{0, 1, 2}` mod 3。使用该载体集的通常 mod 3 加法结构，这里 −2 = 1 在 `H` 中且 −1 = 2 在 `H` 中。因此，`2+1` = `{0}`。此外，说明循环性质，2 在集合 `{1+1}` 中；作为结果，1 在集合 `{2−1}` 中。这表明超群由模三加法运算产生，使用 `H` 和 `2^(H)'` = `{{0}, {1}, {2}, {0, 1}, {0, 2}, {1, 2}, {0, 1, 2}}`。

超群的下一个例子来自 Linzi and Stojalowska (2020)。

### 示例 14.6

设 `H` = `{0, −1, 1}`，并考虑下面给出的加法；这定义了所谓的符号超群。

`(−1) + (−1)` = `(−1) + 0` = `0 + (−1)` = `{−1}`

![方程](img/F00028Xsi6.png)

`0 + 0` = `{0}`

![方程](img/F00028Xsi7.png)

`1 + 1` = `1 + 0` = `0 + 1` = `{1}`

![方程](img/F00028Xsi8.png)

`1 + (−1)` = `(−1) + 1` = `H`.

![方程](img/F00028Xsi9.png)



请注意 `MINUS(1)=−1`，`MINUS(−1)=1`，且 `MINUS(0)=0`。此外，2) 成立是因为 `ZERO` 加到任何东西上都是那个东西。此外，3) 成立，因为例如 `1+(−1)={0, −1, 1}`，而 `0` 在此集合中。与常规群不同，`ZERO` 元素必须位于 `1+(−1)` 所在集合中，但它不必是 `{0}`。最后，请注意 4) 成立；例如，`x=1` 在集合 `{1+1}` 中，参照 4)，`y=1` 且 `z=1`；因此，`z` 在 `{x−y}`=`{1−MINUS(1)}`=`{1+1}`=`{1}` 中。

## 14.3 部分等距
对于 `H` 上的有界算子，部分等距 `U` 指的是当 `U` 限制在 `perp(ker(U))` 上时 `U` 是等距的。也就是说，`U`：`perp(ker(U))`→ `U` 的值域。为了对部分等距算子 `U` 获得一些直观认识，最好将其视为从 `H` 中的闭子空间 `A` 到 `H` 的另一个闭子空间 `B` 的映射。通常，在这种情况下，`A` 被称为初始空间，而 `B` 被称为终空间。`A` 是通过取核的正交补得到的，而 `B` 是通过取值域得到的。参见 图 14.2。同时，伴随算子 `U*` 执行相反的映射。它将子空间 `B` 映射到子空间 `A`。此外，有用的是认为在域 `A` 和 `B` 的补集中，所有值都等于零。`U*U` 是子空间 `A` 上的投影，也称为初始投影，而 `UU*` 是子空间 `B` 上的投影，称为值域投影。这些映射用于判断对称算子是否存在自伴扩张。此外，如果存在扩张，这些映射对于确定这些扩张很有用。

![图 14.2 部分等距映射.](img/F00028Xf14-02-9780443136979.jpg)

图 14.2 部分等距映射。

### 示例 14.7
设 `L` 为 *l*^(*p*)![方程](img/F00028Xsi10.png) 中的左移算子，其中 `L(v1, v2,…)=(v2, v3,…)`, 则 `L` 是部分等距。因为 `ker(L)={(v1, 0, 0, 0,…)}`, 它由所有映射为零的 *l*^(*p*)![方程](img/F00028Xsi11.png) 中的向量组成。`Perp(ker(L))={(v2, v3,…)}=ran(L)`。

### 示例 14.8
设 `VECTOR` 排序的载体集合为二维复值域。因此，这里在希尔伯特空间 `H`= `C`²![方程](img/F00028Xsi12.png) 中，考虑部分等距 `Ua`=

```
\begin{matrix} {|0} & {1|} \\\\ {|0} & {0|} \\\\ \\end{matrix}
```

![方程](img/F00028Xsi13.png)

然后，`Ua` 的初始空间为 `A`= `C` 与 `{0}` 的直和。这是因为 `ker(Ua)`=所有列向量 `(z 0)′` 的集合，其中 `z` 是任意复数。`Ua` 乘以该向量得到零。因此初始空间由所有二乘一列向量组成，第一元组在 `C` 中，第二元组为零。`Perp(ker(Ua))`=所有形如 `(0 w)′` 的向量的集合，其中 `w` 是任意复数。这也是 `Ua` 的值域。终空间 `B` 是 `{0}` 与 `C` 的直和。

参照 `H` 中从子空间 `A` 到 `B` 的部分等距。记 `Ua` 为从 `A` 到 `B` 的部分等距。`Ua` 的亏指数分别由 `perp(A)` 和 `perp(B)` 的维数给出。只有当这些指数相等时，`Ua` 才能扩展为 `H` 上的酉算子。首先，当这些指数相等时，将证明 `U` 是到整个 `H` 的扩张。`U` 将等于 `Ua` 与 `Up` 的直和，其中 `Up` 是从 `perp(A)` 到 `perp(B)` 的酉算子。该算子将 `H` 映射到自身，其定义域等于 `A` 与 `perp(A)` 的直和，值域为 `B` 与 `perp(B)` 的直和。由于两个希尔伯特空间当且仅当它们具有相同维数时同构，这表明 `U` 是一个扩张。另一方面，如果 `U` 扩展 `Ua`，则 `U(perp(A))=perp(U(A))=perp(Ua(A))=perp(B)`；由于 `U` 是酉的，`dim(perp(A))=dim(perp(B))` 且指数相等。

在 示例 14.4 中提到的 Cayley 变换在 `T` 为闭且对称算子时在 `H` 中提供了 `ran(T+iI)` 与 `ran(T−iI)` 之间的部分等距。此外，在这些条件下，该变换在 `H` 上是酉的当且仅当 `T` 是自伴的。von Neumann 的一个定理指出，对于闭且对称的 `T`，`T` 具有自伴扩张当且仅当其 Cayley 变换的亏指数相等。此外，`T` 具有自伴扩张当且仅当 `ker(T*−iI)` 和 `ker(T*+iI)`，或 `ran(T+iI)` 和 `ran(T−iI)`，具有相同的维数（Conway, 1999）。

在希尔伯特空间中，部分等距与投影之间存在密切关系。有界算子 `U` 在 `UU*` 是有界投影时称为部分等距。此外，当 `U=UU*U` 时，或当 `U*` 是部分等距且全部属于 `B(H)` 时，它也称为部分等距。前面提到的第一个恒等式与伪逆运算有关。这些关系将在下一节中得到验证。此外，伪逆运算在第 18.4 节的机器学习环境中得到说明，即回归应用。之前提到过，但不是以相同的方式，使用函数复合，如果 `Ua`: `A→B`，则 `Ua*`: `B→A` 然后 `Ua*Ua=I` 在 `A` 上，即它是希尔伯特空间 `A` 上的恒等算子。类似地，`UaUa*=I` 在 `B` 上，是 `B` 上的恒等算子。部分等距与生成 von Neumann 代数以及证明希尔伯特空间中有界算子的酉等价性内在相关（Pearcy, 1964）。

## 14.4 部分等距的多排序代数
`C*` 代数中提到的 `B(H)` 算子的部分等距可以用几种等价方式描述：

1. 1) 幂等：若 `v=UU*`，则 `v²=v`![方程](img/F00028Xsi14.png)。
2. 2) 伪逆：`UU*U=U`。
3. 3) 伪逆：`U*UU*=U*`。
4. 4) 幂等：若 `w=U*U`，则 `w²=w`![方程](img/F00028Xsi15.png)。

为证明 (1)→(2)，设 `u=U−UU*U` 然后计算 `uu*=(U−UU*U)(U*−U*UU*)`=`UU*−UU*UU*−UU*UU*+UU*UU*UU*`=`v−v²−v²+v³`=0。因为 `v³=v²v=v²`，且 `uu*=‖u‖²`。接下来，为证明 (2)→(3)，取伴随。为证明 (3)→(4) 由于 `U*UU*=U*` 且 `w=U*U`，将方程 `U*UU*=U*` 在右侧乘以 `U` 可得 `w²=w`![方程](img/F00028Xsi16.png)。最后，为证明 (4)→(1)，设 `u=U*−U*UU*`；接下来在左侧乘以 `U` 得到 `v²=v`![方程](img/F00028Xsi17.png)。接下来将看到在 `MSA` 中，部分等距的高层观点是幂等半群。

在本文件中多次看到并非所有算子都在其定义域上完全定义。例如，在域中对逆运算给予了特别注意和记号，对于希尔伯特空间上的动量和距离算子也是如此。将零元素的逆包含在域中会使定义域扩大以包含无穷远点。这导致一个有尖点的集合，并产生一种新的代数结构，但它不是域。在函数复合下，部分等距 `U` 通常不能跟随自身。也就是说，`U²`![方程](img/F00028Xsi18.png) 除非 `U*U=UU*` 否则未定义，且 `U*` 也是如此（Paterson, 1999）。因此，乘法二元运算，实际上是函数复合，在 `MSA` 中被修改以容纳这类部分等距。此外，与之前结构一样，这些算子可以执行的顺序存在。参数不一定可交换。对于这些情况，如前所述，多元图具有斜线，表示从指定排序中参数利用的顺序。在本应用中也是如此，并带有稍后描述的额外限制；另见 图 14.3。



## 部分等距与多元图

![图 14.3 部分等距 \[U, U\*\] 的多元图非零。](Images/F00028Xf14-03-9780443136979.jpg)

图 14.3 部分等距 [`U`, `U*`] 的多元图非零。

就本情况而言，当对二元算子 `MULT` 的第一个操作数或参数进行应用时，该操作没有限制。假设在此情况下，多元箭头的尾部有一个单划线。然而，多元箭头的第二个尾部用两条斜线标记。然而，在当前情况下，用于的操作数存在限制。为了解释这一点，必须确定单一类型载体集 `STRING`。`STRING` 为 {`U`, `U*`}! 并定义为包含 `U` 或 `U*` 的所有字符串的集合，其长度为任意有限非零，但字符串内不包含两个或更多相邻的相同元素。因此，带星号的元素与不带星号的元素必须交替出现。它们在任何字符串中都不能相邻。例如，`UU*UU*` 是允许的；它是一个长度为四的交替字符串。字符串的后部 `b` 是最左边的元素；然而，在函数复合中它是最后应用的。字符串的前部 `f` 是字符串的最右边元素。对于长度为二的字符串，它在函数复合中首先被应用。该结构使用字符串的连接二元运算构成一个半群。然而，即使在此代数中乘法是算子本身的连接，如前所述，当应用于希尔伯特空间中的元素时，它们被用于函数复合。从右到左，而不是从左到右。这种顺序与之前描述的基本群不同。参见 第 12.4 节。

部分等距是一个幂等元，使用一元运算名称伴随 `ADJ`，以及后面给出的三个等式约束。首先，描述使字符串有效的原因。

`MULT:STRINGxSTRING→STRING`

![方程](img/F00028Xsi19.png)

`ADJ:STRING→STRING`

![方程](img/F00028Xsi20.png)

以下记号：
* `Mult` 为 `·`
* `ADJ` 为 `*`
* `STRING` 为由 {`U`, `U*`}! 中的元素连接而成。再次说明，这是由一个或多个 `U` 或 `U*` 组成且始终交替的集合。

二元运算是部分的，因为第二个输入字符串的前部必须是第一个输入字符串的后部的伴随。形式上：`f2=(b1)*`。这防止了两个或更多相同的元素 `U` 相互相邻。`U*` 亦然。例如，假设第一个参数为 →`U*UU*UU*`；则 `b1` 为 `U*`，箭头指向它。因此，第二个参数必须具有前项 `U`，且无 `*`。于是假设第二个输入为 `U*U`，这是一个有效输入；那么 `MULT` 操作的结果为 `U*U·U*UU*UU*=U*UU*UU*UU*`，是一个长度为七的字符串。更一般地，存在的一个有效字符串例如记作 `T=u.v.w.y.z`，其中 `z` 为第一个字符串。它之所以有效，是因为 `y` 中的前项等于 `z` 中最后一项的伴随。这表示为 `fy=bz*`。因此，由于单个字符串 `y` 和 `z` 相乘得到新字符串 `yz`，`T=u·v·w·yz`，然后乘法确保 `w` 的前部具有字符串 `yz` 的后部的伴随值。符号上，`fw=b(yz)*=b(y)*z`，得到 `T=u·v·wyz`；再次，`fv=b(wyz)*=b(w)*yz` 因此 `T=u·vwyz`；最后，`fu=b(vwyz)*=b(v)*wyz` 给出 `T=uvwyz`。

对于多元图，第二个输入不仅被双斜线标记，而且在其旁边还有伴随符号 `*`。这是提醒第二个参数必须是一个字符串，其第一个符号是第一个参数的最后一个符号的伴随。作为另一个提醒，第一个参数位于第二个参数的右侧，如函数复合中那样，而不是连接。图 14.3 说明了其中许多事实。幂等半群的等式约束如下：
1. 1) 幂等伴随：(`U*`)*=`U`。
2. 2) 幂等：(`UU*`)² = `UU*·UU*` = `UU*` ![方程](img/F00028Xsi21.png)。
3. 3) 结合律：(`x·(y·z)`)=`((x·y)·z)`；这将在下文证明。

使用正式但具有启发性的记号：从 3)的左边开始，(`x·(y·z)`)。如前所述，令 `f` 表示第二个输入的前部，`b` 表示第一个输入字符串的后部。则 `fy=(bz)*`，`fx=(byz)*`，这与 `fx=b(y)*z` 完全相同。这是由于 `yz` 的后部与 `y` 的后部相同。因此，(`x·(y·z)`)=`xyz`。反过来 (`(x·y)·z`)，由于 `fx=(by)*`，现在 `f(xy)=x f y=(bz)*` 给出 (`(x·y)·z`)=`xyz`。因此，结合律成立；因此，该结构不仅仅是一个群胚；它是一个幂等半群。

希尔伯特空间上的幂部分等距是 `U`，使得对于所有正整数 `U^(n)` ![方程](img/F00028Xsi22.png) 它也是一个部分等距。所有等距及其伴随都是幂等距。非等距幂部分等距的一个重要例子是下一个示例中的截断移位运算。

### 示例 14.9

截断移位 `T_n : C^(n) → C^(n)` ![方程](img/F00028Xsi23.png)，其中当 `j < n` 时 `T_n(e_j)=e(j+1)`，否则为零。这里，`{e1, e2,…, en}` 是 `C^(n)` ![方程](img/F00028Xsi24.png) 的基集。因此，例如，若 `n=3`，则 `T3(e1)=e2`。此外，(`T3`)²(`e1`) = `e3`，(`T3`)³(`e1`) = `0` ![方程](img/F00028Xsi25.png)。在所有情况下，`perp(ker(T))=ran(T)`。

一般而言，部分等距的复合很少本身是部分等距。已证明如果 `S` 和 `T` 是部分等距，则 `ST` 也是部分等距，当且仅当 `SS*` 和 `TT*` 交换。此外，即使对于幂部分等距，它们也与酉算子的直和酉等价。这些是 `l²` 上的单边移位 `S` 及其伴随的拷贝。此外，还有前一示例中给出的截断移位 `T_n` 的拷贝，但对于所有正整数 `n`（Hoover and Lambert, 1974）。

## 14.5 Stone 定理

简而言之，Stone 定理在希尔伯特空间 `H` 中的自伴算子与一参数酉算子族之间建立了一一对应关系。一参数酉算子族构成一个群。这些算子 `U` 依赖于一个实参数，且对于 `R` 中的 0、`s` 和 `t`。
1. 1) 恒等 `U(0)=I`
2. 2) 转移 `U(s+t)=U(s)+U(t)`。

该定理中的一参数群在 `H` 中是强连续的。这是 SOT，意味着当 `s→t` 时，极限 `‖U(s)v−U(t)v‖=0`，对所有 `H` 中的向量 `v` 和 `R` 中的 `t` 成立。由于本文档中的希尔伯特空间是可分的，除非另有说明，弱连续就足够了。即 WOT 且当 `s→t` 时极限 `<(U(s)−U(t))v, v>=0`，对所有 `H` 中的向量 `v` 和 `R` 中的 `t` 成立。在 第 9.1 节 中，提供了 SOT 和 WOT 的描述及示例。不可分希尔伯特空间将在后续章节中考虑。参见 第 9.1 节，其中涉及算子拓扑。在引用的章节中提供了 SOT 和 WOT 的示例以及反例。

最重要的是，Stone 定理建立了希尔伯特空间 `H` 中具有稠密定义域的非有界自伴算子 `T` 生成一参数连续酉算子群：`U(t)=e^(i t T)` ![方程](img/F00028Xsi26.png)。此外，所有这些酉群都是以这种方式生成的。即存在 `H` 上稠密定义的自伴算子 `T`，使得 `U(t)=e^(i t T)` ![方程](img/F00028Xsi27.png)。对于 `R` 中的 `t′` 和 `H` 中的 `v`，极限 `t→t′` 时 `U(t)v=U(t′)v`。此外 `U(t+t′)=U(t)U(t′)`。



此外，`T` 当且仅当本定理中的单参数群在 `H` 中范数连续时有界（Hall, 2013）。Cayley 变换将被用于关联希尔伯特空间 `H` 上在稠密子集 `dom(T)` 上的算子 `T` 与由 `U=(T−iI)/(T+iI)` 给出的算子 `U`。以下成立：
1. 1) 算子 `U` 是闭的当且仅当算子 `T` 是闭的。
2. 2) 算子 `U` 是酉的当且仅当算子 `T` 是自伴的。

### 示例 14.10
角动量可以被视为旋转的生成元。它是一个酉变换的单参数群，根据 Stone 定理，它是执行旋转群 `SO(3,R)` 在 `X = L²(R³)` 上的自然作用的无穷小生成元![方程](img/F00028Xsi28.png)。关于某轴的有限旋转可以通过对该轴施加连续的无穷小旋转得到。例如，在 `R³`![方程](img/F00028Xsi29.png) 中，关于 z 轴旋转角度 `ϕ`![方程](img/F00028Xsi30.png) 的旋转 `R(ϕ)` 可以使用 `R(ϕ)=limit as n→∞ of [1−i(Jϕ)/(n h)]^(n)`![方程](img/F00028Xsi31.png) 找到。取对数后，该极限可利用基本微积分求得。极限为 `n→∞ of n·ln [1−i(J ϕ)/(n h)]` 等于 `limit as n→∞, ln[1−i(J ϕ)/(n h)]/(1/n)` 等于 `limit as n→∞ [i(J ϕ)/(n² h)]/(−1/n²)=−i(J ϕ)/(h)`。这里，`J` 是一个无穷小对称旋转算子。对 `e` 提高到涉及最后一个极限的幂次得到 `R(ϕ)=e^(−iJϕ/h)`![方程](img/F00028Xsi32.png)。#

## 14.6 位置与动量
正则对易关系 (CCR) 表达了量子中两个主要可观测量——位置和动量之间的关系。动量产生直接通过平移变化影响位置的操作。连接背后的基本理论是位置的无穷小变化由动量生成。Stone-von Neumann 定理表达了位置与动量对易关系与 Weyl 指数关系之间的关系，是基本基石。

### 示例 14.11
考虑最简单的希尔伯特空间 `H`，其中 SCALAR 和 VECTOR 的载体集均为一维实数域。设 `v` 为 `H` 中的一个简单元素，通常称为态，因此 `‖v‖=1`。在此示例中，位置与动量之间的基本关系将利用 CBH 构造的本质来说明。粒子的平均初始位置由其期望值给出：`xo=<v|Y|v>`。当发生 `x` 的平移时，相应地由动量 `P` 生成产生一个新态 `w`。此外，期望值导致新的位置。在这种情况下，`w = e^((−i x P/h))`![方程](img/F00028Xsi33.png)，而新的位置为 `X = < v| e^((i x P/h)) Y e^((−i x P/h)) |v>`![方程](img/F00028Xsi34.png)。接下来对每个指数利用幂级数。随后在 CBH 中尽可能用李括号 `[P, Y]=−i h` 代入，见示例 11.3。这给出：
`X=<v|Y+[i x P/h, Y]+1/2! [i x P/h, [i x P/h, Y]]+…|v>`。所有高阶项都有李括号嵌套在李括号中，就像 1/2! 项一样。由于李括号始终等于 `−i h`，一个常数，于是 `[i x P/h, i h]=0`，因此 `X=<v|Y+x+0+…|v>=x_o+x` 且粒子从 `x_o` 移动到 `x_o` 加上 `x`。上述等式中的常数 `h` 是约化普朗克常数。#

在 CCR 结构中，假设动量算子 `P` 和乘法或距离函数 `Q` 在可分希尔伯特空间 `H` 中定义在共同的稠密定义域 `D` 上。它们都是自伴算子。此外，对于本节的其余部分，去掉 `h` 因子将生效。因此，可得 `[P, Q]=−i I` 在 `D` 上。用于 Fock 空间的产生 `a†` 和湮灭 `a` 算子将在下一章详细描述。目前，这些算子将利用 `P` 和 `Q` 表示。当描述谐振子时在 第 19.1 节 中也是如此。事实上，设产生算子由 `a† = (Q−i P)/2^(1/2)`![方程](img/F00028Xsi35.png) 给出，而湮灭算子 `a = (Q+i P)/2^(1/2)`![方程](img/F00028Xsi36.png)。于是 `[a, a†]`![方程](img/F00028Xsi37.png)`=1`，可利用李括号 `[(Q+i P)/2^(1/2), (Q−i P)/2^(1/2)] = (Q+i P)/2^(1/2)(Q−i P)/2^(1/2) − (Q−i P)/2^(1/2)(Q+i P)/2^(1/2) = 1/2 i (P Q−Q P−Q P+P Q) = i [P,Q] = I`![方程](img/F00028Xsi38.png) 看到这一点。类似地，`[a,a]=[a†,a†]=0`![方程](img/F00028Xsi39.png)。

这些恒等式对于描述 CCR C∗ 代数中的玻色子粒子很重要。玻色子粒子包括光子、声子、介子、引力子以及若干其他粒子。类似地，费米子在正则反对易关系 C∗ 代数中描述。在这种情况下，Poisson 型括号被用于展示产生 `b†` 与湮灭操作 `b` 之间的关系。这里，`{b,b†}=b b† + b† b =1`![方程](img/F00028Xsi40.png)。此外，`{b,b}={b†,b†}=0`![方程](img/F00028Xsi41.png)，并且算子 `b` 和 `b†`![方程](img/F00028Xsi42.png) 是有界的，而不像 `a` 和 `a†`![方程](img/F00028Xsi43.png)。费米子族包括电子、质子、中子、缪子、中微子以及若干其他粒子。

## 14.7 正则对易关系的 Weyl 形式与 Heisenberg 群
CCR 的 Weyl 形式与 Stone 定理和 CBH 推导都相关。Weyl 结构利用两个与 Stone 定理类似的单参数酉群 `U(t)` 和 `V(s)`。泛函演算建立了对于 `t` 和 `s`，实值 `e^(i s P)`![方程](img/F00028Xsi44.png) 和 `e^(i t Q)`![方程](img/F00028Xsi45.png) 是酉且有界算子的事实（Putman, 1967）。最后，从使用 `U(t)=e^(i t Q)`![方程](img/F00028Xsi46.png)、`V(s)=e^(i s P)`![方程](img/F00028Xsi47.png) 的 CBH 型形式计算可得，对于所有实值 `t` 和 `s`，有 `U(t)V(s)=e^(−i s t)V(s)U(t)`![方程](img/F00028Xsi48.png)。Stone-von Neumann 结果的实质随之而来。它断言在可分希尔伯特空间 `H` 上满足 CCR 的 Weyl 形式的所有不可约单参数酉群对 `U(t)` 和 `V(s)` 在酉意义下等价。在这种情况下，存在酉算子 `W : L²→H`![方程](img/F00028Xsi49.png)，使得 `W* U(t) W = e^(i t Q)`![方程](img/F00028Xsi50.png) 且 `W* V(s) W = e^(i s P)`![方程](img/F00028Xsi51.png)。

### 示例 14.12
Heisenberg 代数 `h` 与 CCR 密切相关。它是与实数域上的 3×3 上三角矩阵的连续幂零 Heisenberg 群相关的李代数。该李群记为 `H(3,R)`。将看到 Stone-von Neumann 定理描述了 `H(3,R)` 的唯一（至同构）不可约表示。代数 `h` 具有基 `X`、`Y` 和 `Z`，它们服从与位置和动量相似的对易关系。基如下给出。这里 `X`、`Y` 和 `Z` 如下：

$\\begin{matrix} \\begin{matrix} {|0} & 1 & {0|} \\\\ {|0} & 0 & {0|} \\\\ {|0} & 0 & {0|} \\\\ \\end{matrix} & \\begin{matrix} {|0} & 0 & {0|} \\\\ {|0} & 0 & {1|} \\\\ {|0} & 0 & {0|} \\\\ \\end{matrix} & \\begin{matrix} {|0} & 0 & {1|} \\\\ {|0} & 0 & {0|} \\\\ {|0} & 0 & {0|} \\\\ \\end{matrix} \\\\ \\end{matrix}.$

![方程](img/F00028Xsi52.png)

对易关系如下：`[X, Y]=X Y−Y X=Z`，`[X, Z]=0`，且 `[Y, Z]=0`。李代数 `h` 也是幂零的。#



在所有海森堡群中，最基本的对应群接下来将被描述。

## Example 14.13
海森堡群 `H(3,R)` 是所有上三角矩阵 `A` 的非交换群，定义在实数域上并采用通常的矩阵运算。因此 `IDENTITY`=`I`。群的所有等式恒等式都成立。下面是矩阵 `A` 及其逆 `INV(A)`，按此顺序：
$\\begin{matrix} \\begin{matrix} {|1} & a & {b|} \\\\ {|0} & 1 & {c|} \\\\ {|0} & 0 & {1|} \\\\ \\end{matrix} & \\begin{matrix} {|1} & {- a} & {{{ac} - b}|} \\\\ {|0} & 1 & {{- c}|} \\\\ {|0} & 0 & {1|} \\\\ \\end{matrix} \\\\ \\end{matrix}.$
![方程](img/F00028Xsi53.png)
下面是 `H(3,R)` 中的矩阵 `B` 以及乘积 `MULT(A,B)`
$\\begin{matrix} \\begin{matrix} {|1} & d & {e|} \\\\ {|0} & 1 & {f|} \\\\ {|0} & 0 & {1|} \\\\ \\end{matrix} & \\begin{matrix} {|1} & {a + d} & {{b + e + a f}|} \\\\ {|0} & 1 & {{c + f}|} \\\\ {|0} & 0 & {1|} \\\\ \\end{matrix} \\\\ \\end{matrix}.$
![方程](img/F00028Xsi54.png)
更一般地，存在维数为 `2n+1` 的海森堡矩阵，`n=1, 2, 3,…`。它们构成一个由 `(n+2)` 乘 `(n+2)` 矩阵组成的单连通李群。一个典型的矩阵是 `A`：
$\\begin{matrix} \\left| 1 \\right. & {v'} & \\left. b \\right| \\\\ \\left| 0 \\right. & {In} & \\left. w \\right| \\\\ \\left| 0 \\right. & 0 & \\left. 1 \\right| \\\\ \\end{matrix}.$
![方程](img/F00028Xsi55.png)
这里，`v` 和 `w` 是 `n`×1 列向量；`v′` 是 `v` 的转置，是一个行向量，而 `In` 是 `n`×`n` 单位矩阵。

## 14.8 Stone-von Neumann 与量子力学等价性
Stone-von Neumann 定理在证明海森堡量子力学表述与薛定谔表述之间的等价性方面很重要。特别地，海森堡表述保持态矢量不随时间变化，而可观测量和其他算符是时间相关的。薛定谔表述的特点是态矢量随时间演化。幺正算符 `U(t, to)` 产生从时间 `to` 到稍后时间 `t` 的态矢 `|v(to)>` 的时间演化。它使用跃迁操作发生：`|v(t)>=U(t, to)|v(t)>`。薛定谔方程涉及哈密顿量 `H`，为 `i h∂|v>/∂t`，即 `ih∂ (| v(t)>)/∂t=H |v(t)>`。当存在时间无关性时，`H` 对 `t` 的偏导数为零。时间演化算符 `U(t)` 必须满足 `ih∂(|U(t))/∂t=HU(t)`。由于 `P` 和 `Q` 是无界的，因此必须陈述域问题，因此将更深入地描述 `CCR` 的薛定谔表述。Stone 和 von Neumann 都证明了该表述在幺正等价意义下是唯一的（Hall, 2013）。
在薛定谔表述中，函数 `f` 的域为 `S`，它是 `L²(R)` 的一个子空间，由快速衰减函数组成，例如 Schwarz 函数 `S(R)`。它也可以是具有连续 n 阶导数的函数，`C^(n)`![方程](img/F00028Xsi56.png)，甚至是绝对连续函数 `AC`。例如，对于动量算符 `P`，`P: S →`![方程](img/F00028Xsi57.png)` S`，绝对连续性已足够，且几乎处处存在的导数也在 `L²`![方程](img/F00028Xsi58.png) 中。`P` 的另一个域是 `Dp`，它是 `L²(R)` 中所有函数 `p(x)` 的集合，使得 `wF(p)(w)` 在 `L²(R)`![方程](img/F00028Xsi59.png) 中，其中 `F(p)(w)` 是 `p(x)` 的傅里叶变换。此外，对于位置算符 `Q`，`Q: S →`![方程](img/F00028Xsi60.png)` S`，还需要乘法运算 `t f(t)` 在 `L²`![方程](img/F00028Xsi61.png) 中。因此，同时处理这两个算符时，必须采用这些类型域的交集 `D`。此外，假设 `Q` 和 `P` 在该域闭包上是自伴的或只是本质自伴的。算符 `P` 和 `Q` 在该域上满足 `CCR`，即 `[P, Q] (f)=−if` 在 `D` 上成立。此外，`[P, P]=[Q, Q]=0`。

### Example 14.14
考虑域 `D` = `C¹`![方程](img/F00028Xsi62.png) 中的 `f`，如前所述。使用湮灭操作 `a` 对 `f` 作用得到 `a f = (Q + i P) f / 2^(1/2) = (t f + f') / 2^(1/2) = 0`![方程](img/F00028Xsi63.png)。结果是一个一阶线性微分方程，其解为 `f = c e^(−t²/2)`![方程](img/F00028Xsi64.png)。此外，该解与谐振子的基态相关。参见 第 6.1 节。
真空态 `|0>` 是能量最低的态。它也被称为基态或零点场。这里，湮灭操作在此态中的期望值为零。电场和磁场以及矢势也是如此；它们的期望值为零。然而，场算符平方的期望值不为零。在场论中，真空是没有粒子的矢量。此外，在 Garding-Wightman 公理中，真空态被假设为唯一的、Poincare 不变态（Wightman, 1976）。此外，真空被假设为循环矢量。真空态是一个相干态；这意味着它是湮灭操作 `a` 的唯一本征态，对应的本征值为 `a^`，即 `a^|a> = a|a>`。换句话说，相干态在场效应的湮灭下保持不变。

## 14.9 辛向量空间——多类型代数方法
辛向量空间是具有额外二元运算 `SKEW` 的实向量空间或复向量空间。域和向量空间的所有其他算符和等式恒等式仍然成立。新的算符是双线性的，且满足：
`SKEW: VECTOR x VECTOR → SCALAR`.
![方程](img/F00028Xsi65.png)
该结构的多项图在 图 14.4 中给出，其中仅说明了涉及类型 `VECTOR` 的箭头。附加的等式恒等式首先通过替换给出：
* `VECTOR` 用 `u, v` 替换。
* `SKEW` 用 `S` 替换。
![图 14.4 辛向量空间的多项图。](img/F00028Xf14-04-9780443136979.jpg)
图 14.4 辛向量空间的多项图。
恒等式如下：
1. 1) 交替 `S (u, u)=0`。
2. 2) 非退化 `S (u, v)=0`，对所有 `v` 成立则推出 `u=0`。
注意 `S (u, v)=− S (v, u)`。这可通过使用 `S (u+v, u+ v)=S (u, u) + S (u, v)+S (v, u)+S (v, v)=0` 得到，所以 `S (u, v)+S (v, u)=0`。

### Example 14.15
可从辛向量空间 `V` 形成海森堡群的抽象。这里，对于实值向量空间，乘积空间 `V x R` 是定义域。对于 `V` 中的 `v` 和 `w` 以及 `R` 中的 `t` 和 `r`，群律为 `(v, t) x (w, r)=(v+w, t+r+S (v, w)/2)`，其中 `S` 是对应于 `SKEW` 的运算。根据 MSA 表征：
`IDENTITY = (0,0)`
![方程](img/F00028Xsi66.png)
`INVERSE (v, t)=(−v,−t)`，因为 `S (v,−v)=− S (v, v)=0`，这是双线性性的结果。
`MULT ((v, t), (w, r))=(v+w, t+r+S (v, w)/2)`，注意 `MULT ((v, t), (−v,−t))=(v−w, t−t+S (v, −v)/2)=(0, 0)`。
作为载体集，考虑类型 `VECTOR` 为 `V=R²`，具有对应于向量空间签名集的通常运算。此外，假设与 `SKEW` 相关的运算为 `S (v, w)=v′ H w`。这里，`v` 和 `w` 是 2×1 实向量，`v′` 是 `v` 的转置，而 `H` 是主对角线元素为零的斜对称 2×2 矩阵；因此 `H′=−H`。

### Example 14.16



# 抽象海森堡代数

抽象海森堡代数可以由辛向量空间 `V` 形成。这里，对于实值向量空间，乘积空间 `V` x′ `R` 是定义域，其中 x′ 表示直积。对于 `V` 中的 `v` 和 `w` 以及 `R` 中的 `t` 和 `r`，换位律为 `[(v, t), (w, r)]=(0, S(v, w))`，其中 `S` 是辛向量空间 `SKEW` 中二元运算对应的运算。

强算子拓扑在海森堡群的表示中起着重要作用；参见第 9.1 节。该表示从海森堡群连续到希尔伯特空间 `H` 上的酉算子拓扑群。薛定谔表示构成海森堡群的一族不可约无限维表示。对于海森堡代数，表示是涉及希尔伯特空间 `H` 的稠密子空间的斜对称自同态的李代数同态。当 `H` 不为 `{0}` 且 `H` 的所有不变闭子空间都是 `H` 或 `{0}` 子空间时，表示是不可约的。海森堡群和代数的全部薛定谔表示都是不可约的（Hall, 2013）。

## 14.10 Weyl 正则对易关系 C∗ 代数

Weyl 算子决定了称为 Weyl CCR C∗ 代数的 C∗ 代数；它涉及实辛希尔伯特空间 `H`，由元素 `{W(f)|f is in H}` 生成且满足以下等式恒等式：

1. `W(0)=1`.
2. `W(f)` unitary.
3. `W*(f)=W(- f)`, `f` in `H`.
4. `W(f)W(g)=e^((-i Im(<f, g>)/2))W(f+g)` ![方程](img/F00028Xsi67.png), `g` 也在 `H` 中。注意 `S(f, g)=(-i Im(<f, g>)/2)` 是一个辛双线性形式。例如，由于 `<f, f>=||f||²` ![方程](img/F00028Xsi68.png) 为实数，虚部等于零。此外，当 `<f, g>=0` 对 `H` 中所有 `g` 成立时，则 `f` 也必须等于零。

Weyl 版本的 CCR C∗ 代数在 ∗ 同构意义下是唯一的（Slawny, 1972）。此外，已证明对于 `f` 不等于 `g`，`||W(f)-W(g)||` 大于或等于 `2^(1/2)` ![方程](img/F00028Xsi69.png)。因此这里的酉群不能是范数连续的，且 C∗ 代数不可分。该 C∗ 代数在对称福克空间上忠实表示。该空间有一个称为真空向量的 distinguished 向量。如前所述，它被湮灭算子操作所湮灭，并且相对于产生算子是循环的。回顾在此上下文中循环性质意味着产生算子的连续应用会产生所有态。玻色福克空间在下一章中描述。

Weyl 用酉运算和酉群重写了 CCR。回顾薛定谔表示。对于位置算子 `Q(f)=t f`，以及动量 `P(f)=-i f'`，它们都在 `H` 中定义域 `D` 的闭包上本质自伴。相应的有界酉算子为 `U(t)=e^(i t P)` ![方程](img/F00028Xsi70.png) 和 `V(s)=e^(i Q s)` ![方程](img/F00028Xsi71.png)。涉及有界酉算子的关键关系为 `(U(t)f)(x)=f(x+t), and (V(s)f)(x)=e^(i s x)f(x)` ![方程](img/F00028Xsi72.png)。这些恒等式可以通过在原点处使用泰勒级数形式验证。进行此操作，并使用 `O` 表示假设为小的项的余项，得到以下结果：首先，`(U(t)f)(x)=[1+i t P+O]f(x)=[f(x)+t f'(x)+O]=f(x+t)=[f(x)+f'(x)t/1!+O]`；其次，`V(s)f)(x)=[1+i Q s+O]f(x)=[f(x)+i s x f(x)]=e^(i s x)f(x)=[1+i s x+O]f(x)` ![方程](img/F00028Xsi73.png)。

应用前面找到的两个恒等式。使用 `V` 对第一个近似值进行操作可得 `(V(s)U(t)f)(x)=(V(s)f)(x+t)=e^(i s (x+t))f(x+t)` ![方程](img/F00028Xsi74.png)。接下来对前面提到的第二个近似值应用 `U` 得到 `(U(t)V(s)f)(x)=e^(i s x)(U(t)f)(x)=e^(i s x)f(x+t)` ![方程](img/F00028Xsi75.png)。比较这两个结果得到期望的结论：`e^(i s t)V(s)U(t)=U(t)V(s)` ![方程](img/F00028Xsi76.png)，即 CCR 的 Weyl 关系。这种形式发展归因于薛定谔。

Weyl 关系是在希尔伯特空间上的强连续酉群；表示是不可约的且在酉等价意义下唯一。这意味着在 `H` 中不存在子希尔伯特空间 `K` 具有以下性质：这里 `K` 非零，不等于 `H`；`U(t)K` 是 `H` 的子空间；且对所有实数 `s` 和 `t`，`V(s)K` 是 `H` 的子空间。当基发生变化时，在 `H'` 上形成新的表示 (`U'`, `V'`)。但由于酉等价，存在酉算子 `W`，`W: H→H'` 使得 `U(t)=W* U'(t) W` 且 `V(s)=W* V'(s) W`。CCR 的所有 Weyl 关系表示都酉等价于薛定谔表示的至多可数直和。Weyl 关系的不可约表示酉等价于薛定谔表示（Slawny, 1972）。

Weyl CCR C∗ 代数通常记为 `CCR(H)` 或 `CCR(H, s)`，其中 `H` 表示希尔伯特空间，`s` 表示辛空间，`Im(<f, g>)`。`CCR(H)` 是一个单 C∗ 代数，即它没有双边理想。此外，设 `T` 为等距映射使得 `T: H→H`，并假设它保持辛结构。即 `s(T f, T g)=s(f, g)`，对 `H` 中的 `f` 和 `g` 成立。在这些条件下，`T` 可以实现为从 `CCR(H)` 到 `CCR(H)` 的星自同构 `A`。此外，存在唯一的自同构 `B`，从 `CCR(H)` 到 `CCR(H)` 使得 `B(W(f))=B(W(T f))`。

## 参考文献

* Conway, 1999 Conway J. 0-8218-2065-6 *算子理论教程* AMS Bookstore 1999;.
* Corsini and Leoreanu, 2003 Corsini P, Leoreanu V. *超结构理论的应用* Dordrecht: Kluwer; 2003;.
* Hall, 2013 Hall B. 978-146471158 *数学家的量子理论*. vol 267 Springer 2013;.
* Hoover and Lambert, 1974 Hoover T, Lambert A. Equivalence of power partial isometries. *Duke Math J.* 1974;41.
* Linzi and Stojalowska, 2020 Linzi, A., Stojalowska, H., 2020. Hyper valuations on hyper fields and ordered canonical hypergroups. arXiv:2009.08954v1.
* Paterson, 1999 Paterson A. *0-8176-4051-7 Groupies, Inverse Semigroups, and Their Operator Algebras* Birkhäuser 1999;.
* Pearcy, 1964 Pearcy C. On certain von Neumann algebras which are generated by partial isometries. *JSTOR*. 1964;15 AMS.
* Putman, 1967 Putman C. *希尔伯特空间算子的对易性质* Springer-Verlag 1967;.
* Sakai, 1971 Sakai S. 3-540-63633-1 *C∗ 代数和 W∗ 代数* Springer 1971;.
* Slawny, 1972 Slawny J. *正则对易关系的代数* Project Euclid 1972;.
* Wightman, 1976 Wightman A. *希尔伯特第六问题：物理公理的数学处理*. Vol 28 AMS 1976;.

# 第 15 章

## 福克空间

### 摘要



玻色子和费米子粒子构成 Fock 空间结构。描述并举例说明了操作这些粒子的代数。本章早期就从玻色子占据数算符以及梯子算符开始。后者算符包括产生算符和湮灭算符。这些算符在一般意义上被描述，并与动量和距离的实际算符相关，后者在前一章中简要提及。强调了真空态中产生算符的循环性质，以及相干态。对费米子 Fock 空间的产生湮灭和数算符作了平行描述。随后简要描述了 Slater 行列式和复 Clifford 空间。Maya 图及其与 Young 图和费米子 Fock 空间的关系是第 15.5 节的主题。下一节描述了 CCR 的同构型变换，以及 CCR 的非阿贝尔版本 CAR 的变换。该变换由 Bogoliubov 提出。其后简要提及了 Segal–Bargmann–Fock 运算。本章以多体系统结束。

## 关键词
产生算符；湮灭算符；Fock 空间；梯子算符；数算符；真空态；Weyl CCR；Segal–Bargmann–Fock 运算；Bogoliubov 变换；Maya 图；Young 图

## 15.1 Fock 空间内的粒子和 Fock 空间结构
Fock 空间是希尔伯特空间张量积的直和。它用于表示全同粒子希尔伯特空间`H`的各种态。在固定的 Fock 空间中，所有元素彼此不可区分。Fock 空间中描述的主要粒子类型是玻色子和费米子。其他粒子，如带负电的离子，像任意子粒子，在此空间中未被描述。对于玻色子，采用了`n`个单粒子希尔伯特空间的对称化张量积之和。零粒子态、单粒子态、双粒子态，……。这些都是`H`与其自身的张量积。所有这些乘积都存在于 Fock 空间中。玻色子 Fock 空间是 Weyl 代数的一种表示。对于费米子，使用了单粒子希尔伯特空间的反对称化张量积。费米子 Fock 空间为 Clifford 代数提供表示。在这两种情况下，形成这些张量积的直和时都使用了希尔伯特空间完备化。Fock 空间中元素的内积定义为各个希尔伯特空间内积的和与积。

### 例 15.1
对于希尔伯特空间`H1`中的向量`v1`和`w1`以及希尔伯特空间`H2`中的向量`v2`和`w2`，张量积`H1⊗H2`中向量的内积由`<v1⊗v2, w1⊗w2>=<v1, w1> <v2, w2>`给出。这是从各个希尔伯特空间相乘得到的内积，如第 7.4 节所示。#

一般而言，Fock 空间的形式为`F`=直和，$\\sum\_{n = 0}^{\\infty}\\left\\lbrack {S\\left( {\\otimes H} \\right)^{n}} \\right\\rbrack$![Equation](img/F000291si1.png)。这里，`S`是一个函数，根据它们是玻色子还是费米子，对张量执行对称或反对称操作。量`(⊗ H)^(*n*)`是`H`的张量积，`n`次。简言之，Fock 空间`F`在本节中将以以下方式书写：它是`F`=(+) \[`S` (⊗ `H`)^(*n*)\]。这里，`n`=0, 1, 2,…, 且算符 (+) 表示从 0 到无穷的直和。因此，将上述表达式更详细地展开得到`F`=`C`+`H`+`S` (`H`⊗`H`)+`S` (`H`⊗`H`⊗`H`)+…. 在此表示中，`+`用于两个单独项的直和。量`C`是表示真空态的复数域，缩写为`vac`。`Vac`是不含粒子的态。希尔伯特空间`H`是单粒子的态，而`S` (`H`⊗`H`)描述两个全同粒子的态。两个全同粒子态也用`S` `H2`表示。类似地，`S` (`H`⊗`H`⊗`H`)描述三个全同粒子的态，将被记为`S` `H3`，以此类推。

需要上述代数直和的希尔伯特空间完备化。在此方向上，(+) `Hn`={(x0, x1, x2, …)}，其中`xj`在`Hj`中。此外，和`x0`+`x1`+`x2`+…必须满足和$\\sum\_{n = 0}^{\\infty}\\left\\| {xn} \\right\\|^{2} =$![Equation](img/F000291si2.png) 和$\\sum\_{n = 0}^{\\infty}\\left\\langle {{xn},{xn}} \\right\\rangle,$![Equation](img/F000291si3.png)，且该和小于无穷。最后，用第 j 个元组(0, 0,…, 0, `v`, 0, …)来识别`Hj`中的向量`v`，并使用记号`v`=`vj`。此外，当`j`不等于整数值`i`时，空间`Hj`与空间`Hi`正交。后一陈述意味着不同`n`值的`n`粒子子空间是正交的。

提供 Fock 空间态的额外但相关的概念是有用的。从对称 Fock 空间开始；它必须始终是无限维的。对于有限维希尔伯特空间`H1`，考虑具有特征向量`|ej>`、`j`=1, 2,…, `n`的可观测量，以及相应的特征值`aj`。当单个粒子占据第 k 个态时，这意味着特征态 ket，`|ek>`=`|0, 0,…, 0, 1, 0, … 0>`，且 1 出现在第 k 个位置。相应地，在类似假设下，双粒子空间`H2`可能有两个粒子处于同一态，或一个粒子处于`n`个态中的两个不同态。例如，在玻色子 Fock 空间中，两个粒子处于同一态的可能性是两者都在第一态，`|2, 0,…, 0>`，或两者都在第二态，`|0, 2, 0,…, 0>`，依此类推到最后态`|0,…, 0, 2>`。此外，在任何 Fock 空间中，两个粒子可以分离：`|1, 1, 0 …, 0>`、`|1, 0, 1, 0,…, 0>`、…、`|0, … 0, 1, 1>`。这些都是两个粒子的所有可能态占据。需要认识到的重要一点是`H2`不是`H1`和`H1`的张量积。它同构于张量积的对称化直和，即`H`=`S` (`H1`⊗ `H1`)。简言之，在此情况下，`S` (`ha`⊗`hb`)=(`ha`⊗`hb`)+(`hb`⊗`ha`)。类似地，在`H3`中将有三个阶乘张量积的直和，即六种可能性。乘积态的线性组合是 Fock 空间中的一般态。

### 例 15.2
考虑`H2`；这是使用不同 ket `{|0>, |0′>}`的双粒子希尔伯特空间。如前所述，涉及这两个 ket 的四个可能态存在；这些不同态由 `{|0 0>, |0 0′>, |0′ 0′>, |0′ 0>}`给出。每个态都有相等的被组装但未被观测的概率。存在三个对称可观测态和一个反对称态。按顺序为`|0 0>`、`|0′ 0′>`、`|0 0′>+|0′ 0>`，以及`|0 0′>−|0′ 0>`。前三个是玻色子态；它们类似于形式，`S` (`ha`⊗`hb`)=(`ha`⊗`hb`)+(`hb`⊗`ha`)。最后一个表达式将被证明是费米子态。#

## 15.2 玻色子占据数和梯子算符
在 Fock 空间中，不同粒子数子空间之间存在粒子跃迁。因此，粒子数不被保持；粒子可以被产生或湮灭，即被湮灭。这些元素可以从任何给定能量态中添加或移除。对应于这些功能的算符称为梯子操作。这些算符的实例见于第 14.8 节。在量子力学中，由梯子算符引起的这些跃迁被称为第二量子化，涉及希尔伯特子空间`Hn`和`H(n+−1)`的混合。梯子算符用于物理学的多个领域中提高和降低能量特征函数，以及改变角动量数的单位。算符的参数是像光子或准粒子像声子那样的粒子。



# 玻色 Fock 空间代数

玻色 Fock 空间代数在希尔伯特空间 `H` 上允许所有态被 `n` 占据，其中 `n` 是任意有限的粒子数。也就是说，`n=0, 1, …`。在此空间中，数算符 `Nj` 给出第 `j` 个本征态的粒子数计数。该算符追踪位于每个态中的粒子数量。对于可观测量 `A`，占据数 `nj` 具有非负整数本征值，使得 `Nj (|n0, n1, n2,…, nj,…, nk>)=nj |n0, n1,…, nj,…, nk>`。相应地，对于算符 `Nj`，本征矢量是 `|n0, n1, n2,…, nj,…, nk>`，而对应的本征值是占据数 `nj`。可观测量 `A` 可以写成和，$\\sum\\limits\_{j}{({{cj}{Nj}})}$![方程](img/F000291si4.png)，其中 `cj` 为标量。

在 Fock 空间中采用产生操作来在规定的量子态 `j` 中添加一个粒子。该算符记为 `a_j^\dagger`![方程](img/F000291si5.png)；它仅关注第 `j` 个态并将该态的占据数增加一。对量子态的此操作是外积或对称乘法。具体而言，`a_j^\dagger`![方程](img/F000291si6.png) (`|…, nj, …>`) = `(nj+1)^(1/2) (|…, nj+1, …>)`。在下文中，这些算符的括号通常会被省略。与产生算符相反的是湮灭算符 `a_j`。CCR 中使用了这两个算符的例子。参见第 14.8 节。在那里，产生算符由 `a^\dagger=(Q−iP)/2^(1/2)` 给出，涉及位置算符 `Q` 和动量算符 `P`。类似地，湮灭算符 `a` 由 `a=(Q+iP)/2^(1/2)` 给出。

一般而言，产生算符无论粒子是否存在都会添加一个粒子。对于非空态，湮灭会使占据数减少一。然而，当第 `j` 个态为空时，对该态执行湮灭算符将得到零。当湮灭算符作用于真空态 `C`，即 `vac` 时，结果也为零。湮灭算符执行的操作是对态的一种内积型操作。综上所述，对于非空态，`a_j |…, nj, …>=n_j^(1/2)`![方程](img/F000291si7.png) `|…, nj−1,…,>`，当 `nj` 为正时，否则得到零。图 15.1A 说明了玻色 Fock 空间中的阶梯算符。

![图 15.1 Fock 空间的阶梯算符。(A) 玻色 Fock 空间，(B) 费米子 Fock 空间中的允许操作。](img/F000291f15-01-9780443136979.jpg)

图 15.1 Fock 空间的阶梯算符。(A) 玻色 Fock 空间，(B) 费米子 Fock 空间中的允许操作。

阶梯算符以及湮灭操作 `a` 和产生操作 `a^\dagger`![方程](img/F000291si8.png) 的矩阵表示在下面以相应顺序以矩阵形式给出。这些矩阵提供了在指定态中允许的粒子减少或增加的标量倍数。在上面的矩阵顶部，每一列是执行操作的态数。所使用的标量倍数是通过识别列数找到的，从零开始。当使用湮灭算符 `a` 时，对应的行数少一。当使用产生算符 `a^\dagger`![方程](img/F000291si9.png) 时，使用多一行，即额外一行。请记住所有态都从零态开始。下面按以下顺序给出湮灭操作 `a` 的矩阵，随后是产生算符 `a^\dagger`![方程](img/F000291si10.png) 的矩阵：

$\\begin{array}{lllllllll} \\left( 0 \\right. & 1 & 2 & 3 & \\left. {4\\ldots} \\right) & \\left( 0 \\right. & 1 & 2 & \\left. {3\\ldots} \\right) \\\\ {|0} & 1 & 0 & 0 & {{0\\ldots}|} & {|0} & 0 & 0 & {{0\\ldots}|} \\\\ {|0} & 0 & 2^{1/2} & 0 & {{0\\ldots}|} & {|1} & 0 & 0 & {{0\\ldots}|} \\\\ {|0} & 0 & 0 & 3^{1/2} & {{0\\ldots}|} & {|0} & 2^{1/2} & 0 & {{0\\ldots}|} \\\\ {|0} & 0 & 0 & 0 & {{4^{1/2}..}|} & {|0} & 0 & 3^{1/2} & {{0..}|} \\\\ \\end{array}$

![方程](img/F000291si11.png)

### Example 15.3

这是使用前面提到的矩阵来找到从指定态产生和湮灭粒子的标量倍数的应用。假设产生算符是 `a_2^\dagger`![方程](img/F000291si12.png)，即态二要增加一个额外粒子。转到上面的第二列并到前面提到的右侧矩阵的第三行，找到标量项 `3^(1/2)`![方程](img/F000291si13.png)。例如，在应用操作之前，假设空间占据为 `ϕ=|3, 0, 6, 4, 0,…, nk>`；则 `a_2^\dagger`![方程](img/F000291si14.png)(`ϕ`)=`3^(1/2) |3, 0, 7, 4, 0,…, nk>`。接下来，假设要对涉及 `ϕ`![方程](img/F000291si15.png) 的第三态执行湮灭操作。要找到 `a_3(ϕ)`，使用前面提到的第一个矩阵的第三列第二行得到 `3^(1/2)`![方程](img/F000291si16.png)，所以 `a_3(ϕ)=3^(1/2) |3, 0, 6, 3, 0,…, nk>`。如果需要 `a_1(ϕ)`，则答案为零，因为在 `ϕ` 中没有粒子可以从态一取走。

前面提到的矩阵可以用数基本征矢量 `ψ[i]`![方程](img/F000291si17.png) 和 `ψ[j]`![方程](img/F000291si18.png) 使用。这将在第 19.1 节 中出现，在那里对所有能量值描述了谐振子解。在任何情况下，以下恒等式成立：`a[i,j]=<ψ[i]`![方程](img/F000291si19.png) `|a |ψ[j]`![方程](img/F000291si20.png)`>` 和 `a[i,j]^\dagger=<ψ[i]`![方程](img/F000291si21.png) `|a^\dagger`![方程](img/F000291si22.png) `|ψ[j]`![方程](img/F000291si23.png)`>`。

产生算符 `a^\dagger`![方程](img/F000291si24.png)、湮灭算符 `a` 和数算符 `N` 之间存在众多关系。其中一些关系已在上一节中说明。在确定额外关系之前，将假设产生操作和湮灭操作互为伴随算符。也就是说，`a^\dagger=a*` 且 `(a^\dagger)*=a`。这些事实在玻色 Fock 空间的 Banach 空间完备化的 C* 代数中得到证明（Townsend, 2000）。现在使用具有 `n` 个粒子的非真空且占据的态。这里，`a^\dagger a |n> = n^(1/2) a^\dagger |n−1> = n^(1/2) n^(1/2) |n> = N |n>`![方程](img/F000291si25.png)。因此，数算符与产生和湮灭操作之间的等同是 `N = a^\dagger a`![方程](img/F000291si26.png)。类似地，`a a^\dagger |n> = (n+1)^(1/2) a |n+1> = (n+1)^(1/2) (n+1)^(1/2) |n> = (n+1) |n>`![方程](img/F000291si27.png)。由此可知 `a a^\dagger`![方程](img/F000291si28.png) 像 `(N+I)` 一样作用。这是数算符加上恒等映射。交换关系是前面给出的恒等式的推论。换位子，`[a,a^\dagger]=a a^\dagger − a^\dagger a = (N+I) − N = I`![方程](img/F000291si29.png)。此外，`[N,a^\dagger]=N a^\dagger − a^\dagger N = a^\dagger a a^\dagger − a^\dagger a^\dagger a = a^\dagger (a a^\dagger − a^\dagger a) = a^\dagger (I) = a^\dagger`![方程](img/F000291si30.png)。类似地，`[N,a]=N a − a N = a^\dagger a a − a a^\dagger a = (a^\dagger a − a a^\dagger) a = − a`![方程](img/F000291si31.png)。

### Example 15.4



零的基态可利用梯子算符在算符 `a` 和 `a†` ![Equation](img/F000291si32.png) 互为伴随这一事实下进行代数解释。 这里，对于湮灭操作的能量，特征态只能降低到零，且永远不会小于此值。 要看到最小本征数为零，考虑 `N` = `a†a` ![Equation](img/F000291si33.png)，且 `N phi[n] = n phi[n]`。 则 `<phi[n]|N phi[n]> = <phi[n]|a†` ![Equation](img/F000291si34.png) `a phi[n]> = <a phi[n]|a phi[n]> = , ||a|phi[n]>||²`，它是非负的，且当且仅当 `a |phi[n]> = 0` 时等于零，因此对于 `n = 0`，再次证明 `a |phi[0]> = 0`。

含 `n` 个玻色子的基本 Fock 态由产生操作的循环性质给出：(`a†`)^(`n`) |0> ![Equation](img/F000291si35.png)，其中 `n` 为正整数。 这些 Fock 态通常不包含关于相位的任何信息。 然而，玻色相干态 `v` 本质上是一个高斯波包。 它是一种特殊的玻色态，涉及湮灭算符 `a`。 具体来说，它是 `a` 的本征态。 因此，`a v = r v`，其中 `r` 是本征值，且由于 `v` 是一个态；假定 `||v|| = 1`。 相干态具有与经典振荡轨迹相似的动力学，并与量子谐振荡相关 (Gazeau, 2009)。

相干态由涉及占据数的无限求和给出。 它定义为 $v = e^{- {1/2}{|r|}^{2}}\\sum\_{n = 0}^{\\infty}{{{r^{n}/{({n!}^{1/2})}}|}n > ,}$ ![Equation](img/F000291si36.png)，其中 |n> 是数算符。 为此，令 `v = the sum`，$\\sum\_{n = 0}^{\\infty}{{{cn}|}n >}$ ![Equation](img/F000291si37.png)，其中 `cn` 为复标量。 然后对 `v` 使用湮灭操作，`a v = the sum`，$\\sum\_{n = 1}^{\\infty}{{{{cn} a}|}n > =}$ ![Equation](img/F000291si38.png) 求和，$\\sum\_{n = 1}^{\\infty}{{{{cn} n^{1/2}}|}n - 1 > =}$ ![Equation](img/F000291si39.png) 求和，$\\sum\_{n = 0}^{\\infty}{{{c\\left( {n + 1} \\right)\\left( {n + 1} \\right)^{1/2}}|}n >}$ ![Equation](img/F000291si40.png)。 使用上文对 `v` 的定义，将 `r v` 设等于求和，$\\sum\_{n = 0}^{\\infty}{{{{cn} r}|}n >}$ ![Equation](img/F000291si41.png)。 用 bra 数算符 `<n |` 对这两个量形成内积。 然后使用正交性条件 `<n, n′> = 0`，除非 `n = n′`；在这种情况下，结果为一。 由此可得 `c(n+1) (n+1)^(1/2) = cn r` 或 `c(n+1) = cn r / (n+1)^(1/2)`。 对该差分方程采用逐次代入可得 `cn = c(n−1) r / n^(1/2)`，于是 `c(n−1) = c(n−2) r / (n−1)^(1/2)`；代入得 `cn = c(n−2) r² / (n (n−1))^(1/2) = c(n−3) r³ / (n (n−1) (n−2))^(1/2) = … = co r^(n) / n!^(1/2)`。 因此，`v = the sum`，$\\sum\_{n = 0}^{\\infty}{{{cn}|}n >} =$ ![Equation](img/F000291si43.png) 求和，$\\sum\_{n = 0}^{\\infty}{\\left( {{{{co} r^{n}}/{n!}^{1/2}}|} \\right.n >}$ ![Equation](img/F000291si44.png)。 由于 `||v|| = 1`，则 `<v, v> = 1`。 形成此内积得到 `v = the sum`，$\\sum\_{n = 0}^{\\infty}{({{{|{co}|}^{2}{|r|}^{2n}}/{n!}})}$ ![Equation](img/F000291si45.png)；这是因为当 `n, n′` 不同时 `<n, n′> = 0`。 因此，`⟨v, v⟩ = |co|² e^(|r|²)` ![Equation](img/F000291si46.png)。 将该量设为一得到 `|co|² = e^(−|r|²), or co = e^(−1/2|r|²)` ![Equation](img/F000291si47.png)。 这表明相干态 `v = e^{- {1/2}{|r|}^{2}}\\sum\_{n = 0}^{\\infty}{r^{n}/{\\left( {n!}^{1/2} \\right){|{n >}}}}$ ![Equation](img/F000291si48.png)。

### Example 15.5

### 示例 15.5

考虑两个相干态 `v` 和 `w`，其中 `v` 由上述表达式给出，而 `w` 以与 `v` 相同的方式给出，例如，`w = e^(−1/2|s|²)` ![Equation](img/F000291si49.png) $\\sum\_{n' = 0}^{\\infty}{\\left( {s^{n'}/\\left( {n'!}^{1/2} \\right)} \\right){|{n' >}}}$ ![Equation](img/F000291si50.png)。 则 `⟨w, v⟩ = e^(−1/2|r|²) e^(−1/2|s|²) e^(r s*)` ![Equation](img/F000291si51.png)。 该表达式通过将 `w` 和 `v` 代入内积得到。 然后，唯一需要证明的项是 `e^(r s*)` ![Equation](img/F000291si52.png)，因为其他项是标量。 最后一项由 `w` 和 `v` 的泰勒级数展开得出。 然后注意到 `<n′, n> = 0`，除非 `n′ = n`，此时为一。 这将双重求和化为单重求和。 在这种情况下，展开式变为求和，$\\sum\_{n = 0}^{\\infty}{\\left( {r s \\ast} \\right)^{n}/{n!}}$ ![Equation](img/F000291si53.png)，最终形式上由 `e^(r s*)` ![Equation](img/F000291si54.png) 给出。 出现特殊情况：对于 `r = s`，则 `<w, v> = 1`。 另外，对于 `r = −s`，则 `⟨−w, v⟩ = e^(−2|r|²)` ![Equation](img/F000291si55.png)。 对于更大的 `|r|`，`v` 和 `w` 变得接近正交。

现在，将求出伴随算符差分方程的解。 回想 `a† |n − 1> / n^(1/2) = |n>` ![Equation](img/F000291si56.png)，并且从真空态可以找到任意占据数的解并不令人惊讶。 因此，`|n> = a^(† n) / n!^(1/2) |0>` ![Equation](img/F000291si57.png)。 为此，如前所述，迭代 `a† |n − 2> / (n−1)^(1/2) = |n − 1>` ![Equation](img/F000291si58.png)；然后将 `|n−1>` 代入方程 `a† |n − 1> / n^(1/2) = |n>` ![Equation](img/F000291si59.png)，得到 `a^(† 2) |n − 2> / (n (n−1)^(1/2))` ![Equation](img/F000291si60.png)。 继续迭代和代入可通过归纳法得到所需结果。

## 15.3 The fermionic Fock space and the fermionic ladder operators

## 15.3 费米子 Fock 空间和费米子梯子算符

在费米子 Fock 空间的情况下，占据数是平凡的，因为 `N` 只能为零或一。 要么在给定态中存在粒子，要么不存在。 占据算符在费米子 Fock 空间中是一个二元函数。 费米子 Fock 空间中的梯子算符 `a†` ![Equation](img/F000291si61.png) 和 `a` 与玻色子 Fock 空间中的类似。 直观上，如前所述，产生算符 `a†` ![Equation](img/F000291si62.png) 向一个态添加一个粒子，但在该空间中该态必须为空。 湮灭算符从一个态中移除一个粒子，前提是存在一个待湮灭的粒子。 这也在 图 15.1B 中有所说明。 提供费米子 Fock 空间代数的反交换关系由泊松括号给出：`{ai, aj} = ai aj + aj ai = 0`，对所有态 `i` 和 `j` 成立，此外 `{a_i†, a_j†} = 0` ![Equation](img/F000291si63.png)，最后，`{a_i, a_j†} = 0` ![Equation](img/F000291si64.png)，除非 `i = j` 时等于一。 作为前两个恒等式的推论，可得 `a a = a† a† = 0` ![Equation](img/F000291si65.png)。 与玻色情况一样，数算符由 `N = a† a` ![Equation](img/F000291si66.png) 给出。 然而，由于 `{a a† + a† a} = 1` ![Equation](img/F000291si67.png)，则 `a a† = 1 − N` ![Equation](img/F000291si68.png)。 由此，`N (1 − N) = a† a a a† = 0` ![Equation](img/F000291si69.png)。 因此 `N` 的本征值要么为零要么为一。 这证实了泡利原理，即占据数为零或一。 可以看出，`N` 的本征态为 `a†` ![Equation](img/F000291si70.png) `|0>` 和 `a |1>`，其对应本征值分别为 1 和 0。 这些结果源于 `(1 − N) a† |0> = a a† a† |0> = 0`，以及 `N a |1> = a† a a |1> = 0`。



在二维希尔伯特空间中，具有标准正交基 {` |0>` , ` |1>` }。由此可得 `a |0>=a^† |1>=0`，`a^† |0>=|1>`；最后，`a |1>=|0>`。注意 `a=|0><1|`，因为 `a |0>=|0><1|0>=0`，并且 `a |1>=|0><1|1>=|0>`。相应地，对于产生算符 `a^†=|1><0|`，由于 `a^† |1>=|1><0|1>=0`，且 `a^† |0>=|1><0|0>=|1>`。此外，`a a=|0><1|0><1|=0`，且 `a^† a^†=|1><0|1><0|=0`。因此，`a` 和 `a^†` 都不是自伴的；然而，它们是共轭伴随的。即 `(a)*=a^†`，因为 `(|0><1|)*=|1><0|`；类似地，`(a^†)*=a`。

在希尔伯特空间 `C²` 中，已知 `|0>` 和 `|1>` 的表示分别由列向量 (1 0)′ 和 (0 1)′ 给出。在此空间中，产生算符 `a^†` 和湮灭算符 `a` 的二乘二矩阵按以下顺序给出：

```
$\\begin{array}{llll} {|0} & {0|} & {|0} & {1|} \\\\ {|1} & {0|} & {|0} & {{0|}.} \\\\ \\end{array}$
```

![Equation](img/F000291si71.png)

使用这些矩阵和上面的列向量，同样可以看出 `a^† |0>=(0 1)′=|1>`，`a^† |1>=0`，`a |0>=0`，且 `a |1>=(1 0)′=|0>`。

在具有 `n` 个态的费米子希尔伯特空间中，存在 2^(*n*) 维。此外，每个元素的转置都会导致整体符号反转。这源于产生算符 `a^†j` 和 `a^†k` 的反对易关系。即交换 `j` 和 `k` 会产生相反的符号，从+到−或反之。例如，`|nj, nk>=aj^†ak^† |vac>=- |nk, nj>`。这里 `vac` 是真空态。

### Example 15.6

在 `H3` 中，这是一个具有三个不同允许态的费米子费米子 Fock 空间。希尔伯特空间包含可能存在的三个全同费米子。因此，`|nj, nk, nm>` 张成该空间。在此情况下，不同的可能性共有八种。它们是 `|0, 0, 0>`、`|0, 0, 1>`、`|0, 1, 0>`、`|1, 0, 0>`、`|0, 1, 1>`、`|1, 1, 0>`、`|1, 0, 1>`，以及 `|1, 1, 1>`。又由于 `|nj, nk, nm>=aj^†ak^†am^† |vac>`，则 `ak^†aj^† am^†|vac>=- aj^†ak*am^† |vac>`。然而，注意到 `|ak^†am^†aj^†|vac>=aj^†ak^†am^†|vac>`，因为有两次转置。在此情况下，符号改变两次。

对于一般的费米子 Fock 态 `|f>=|n1, n2,…, nj,…, nk, …>`，产生算符满足当 `nj=0` 时 `aj^† |f>=|n1, n2,…, nj+1, …>`，否则结果为零。利用上面的 `|f>`，湮灭算符满足 `aj |f>=|n1, n2,…, nj−1, …>`；这仅在 `nj=1` 时发生，否则结果为零。为了将粒子位置从第 `j` 个位置移动到空位置例如 `k`，则必须对第 `j` 位置的粒子执行湮灭，并在第 `k` 位置产生一个粒子。按此严格顺序，且不要忘记，这里所有的粒子都是全同的。因此，`ak^†aj |f>=|n1, n2,…, nj −1, … nk +1, …>=|g>`。注意 `aj ak^† |f>=- ak^† aj |f>=-|g>`。

### Example 15.7

在费米子 Fock 空间 `H2` 中，恒等式的分辨由 `I={a, a^†}=a a^†+ a^† a=|0><1|1> <0|+|1> <0|0><1|=|0><0|+|1><1|` 给出。注意 `a a^† I=a |1><0|(|0><0|+|1><1|)=a |1><0|=|0><1|1><0|=|0><0|`；这是对 `I` 的第一分量的投影。同样，`a^† a I=a^† |0><1|(|0><0|+|1><1|)=a^† |0><1|=|1><0|0><1|=|1><1|`；这是对 `I` 的第二分量的投影。

考虑 `C²`，但这次令 `|0>=(1 0)′` 表示真空态。并令 `|1>=(0 1)′` 表示该 Fock 空间中的占据态。数算符 `n`、产生算符 `a^†` 和湮灭算符 `a` 都以以下顺序给出的 2×2 矩阵表示：

```
$\\begin{array}{llllll} {|0} & {0|} & {|0} & {0|} & {|0} & {1|} \\\\ {|0} & {1|} & {|1} & {0|} & {|0} & {{0|}.} \\\\ \\end{array}$
```

![Equation](img/F000291si72.png)

注意 `a^†a=n`，通过将上面的第二个矩阵乘以第三个矩阵得到第一个矩阵。泊松括号算符给出 `{a, a^†}=aa^†+a^†a=I`。以及 `a^†|0>=|1>`，`a^† |1> 0`，`a |0>=0`，最后 `a |1>=|0>`。

## 15.4 The Slater determinant and the complex Clifford space

费米子 Fock 空间中的向量可以用称为 Slater 行列式的行列式来表示。反对称性源于行列式的定义。从二维空间开始，将进行记号的回顾。`H2` 中的两粒子态可以涉及两个单粒子态 `|n1>` 和 `|n2>` 来写出。首先，假设粒子 `r1=1` 处于态 `|1>` 且粒子 `r2=2` 处于态 `|2>`；则写为如下形式：`(r1|n1)(r2 |n2)=f(r1)f(r2)`。类似地，假设粒子 `r2` 处于态 `|1>` 且粒子 `r1` 处于态 `|2>`；则写为如下形式：`(r1|n2)(r2 |n1)=f(r2)f(r1)`。这里，粒子不可区分，并且由于它们是反对称的，允许的表示为 `|v>=1/2^(1/2)![Equation](img/F000291si73.png) (|n1>|n2>−|n2>|n1>)=1/2^(1/2)![Equation](img/F000291si74.png) (f1(r1)f2(r2)−f2(r1)f1(r2))`。后一个方程是行列式。具体而言，后一个表示可以写成 2×2 Slater 矩阵 `S 2`，其在前面带有标量 2^(1/2)![Equation](img/F000291si75.png)，因此 2^(1/2)*S*2 = :![Equation](img/F000291si76.png)

```
$\\begin{matrix} {|{f1\\left( {r1} \\right)}} & {{f1\\left( {r2} \\right)}|} \\\\ {|{f2\\left( {r1} \\right)}} & {{{f2\\left( {r2} \\right)}|}.} \\\\ \\end{matrix}$
```

![Equation](img/F000291si77.png)

推广到 N 粒子反对称波函数由 N×N Slater 行列式 `S N` 给出（斯莱特, 1929）。这些态张成的子空间是费米子 Fock 空间。矩阵 `S N` 给出为 *N*!^(1/2)![Equation](img/F000291si78.png) `SN=`

```
$\\begin{matrix} \\begin{array}{lllll} {|{f1\\left( {r1} \\right)}} & \\cdot & \\cdot & \\cdot & {{f1\\left( {rN} \\right)}|} \\\\ \\end{array} \\\\ \\begin{matrix} \\cdot & \\cdot & \\cdot \\\\ \\end{matrix} \\\\ \\begin{array}{lllll} {|{{fN}\\left( {r1} \\right)}} & \\cdot & \\cdot & \\cdot & {{{{fN}\\left( {rN} \\right)}|}.} \\\\ \\end{array} \\\\ \\end{matrix}$
```

![Equation](img/F000291si79.png)

Slater 矩阵提供涉及 `n` 个粒子和 `n` 个轨道的基态。交换任意两个粒子时它是反对称的。

Clifford 代数， over `C`，是一个含幺结合代数 `A`，涉及一个线性映射 `f`，从其底层向量空间 `V` 到 `A`。它满足对于 `V` 中的 `v`，存在一个二次泛函 `Q`，其中 `f(v)²=Q(v) I`，且 `I` 是 `A` 中的恒等元。这些代数用于描述二维空间中的自旋 1/2 粒子。此外，它们在四元数向量空间的表示中很有用。Clifford 代数的其他表示涉及量子化并导致星代数以及扩展到 `C*` 代数。重要的是，Fock 空间的表示是 Clifford 代数是由 `Z+1/2` 上的产生和湮灭元生成的含幺结合代数。同样受通常的泊松括号约束的约束。关于使用 Clifford 代数的物理应用的非常深入的论述可以在 博斯特尼克和尼尔森 (2021) 中找到。

如前所述，Clifford 代数的 Fock 空间表示 `F`，与其对偶空间 `F*` 存在。这些空间都具有唯一的真空态 `|0>` 和 `<0>`。真空态也被称为 Dirac 海（罗格斯物理, 2018）。通常，费米子态使用产生算符产生：`aj1^† … ajn^† |0>`。

## 15.5 Maya diagrams



Maya 图由位于实数线上每个半整数处的黑白卵石、点或其他小物体的直线图案组成。这里，0 表示白色，X 表示黑色，均位于点 `Z+1/2` 处。它们被用作费米子 Fock 空间的自由表示。在 Maya 图中，存在一个负整数 `m`，使得对于所有点 `j`，小于或等于 `m` 时，仅出现白点。类似地，存在一个正整数 `n`，使得对于所有点 `j`，大于或等于 `n` 时，仅出现黑点。一般来说，还必须有不止一次的颜色转换。Maya 图与 Young 图之间存在 1–1 且满的对应关系，参见附录 A.4。该对应关系涉及两个图的临界参数。对于 Maya 图，首先将指定两个参数。它们是两个正半整数 `w` 和 `b`，`w < b`。也就是说，`w` 和 `b` 在 `Z+1/2` 中，其中 `w` 是最大的白点位置，使得在小于 `w` 的点上不存在任何黑点。类似地，令 `b` 为黑点的最小位置，使得没有白点具有更大的位置。还需要的是在开区间 (`w`, `b`) 中存在的黑点总数 `nb`； along with this, 需要的是在 (`w`, `b`) 中白点的总数 `nw`。下面给出一个 Maya 图的示例。

## Example 15.8

考虑以下 Maya 图，其中 0 表示白点，X 表示黑点：

$\\begin{matrix} \\ldots & {{- 11}/{2.}} & {{- 9}/{2..}} & {{- 7}/{2..}} & {{- 5}/{2..}} & {{- 3}/{2..}} & {{- 1}/{2..}} & {1/{2\\ldots}} & {3/{2\\ldots}} & {5/{2\\ldots}} & {7/2} & {9/{2..}} & {11/{2..}} & {13/{2..}} & {15/{2..}} & {17/{2\\ldots}} \\\\ \\ldots & 0 & {X.} & {0.} & {X.} & {X.} & {X.} & {0.} & {X.} & {X.} & {0.} & {X.} & {X.} & {X.} & {0.} & {X\\ldots} \\\\ \\end{matrix}$

![方程](img/F000291si80.png)

在上述 Maya 图的插图中，可以得出 `w=−11/2`，因为假设在 `w` 之下不存在黑点。同样出于类似原因，`b=17/2`。开区间 (`w`, `b`) 中的黑点数为九，该区间中的白点数为四。

这些 Maya 图与 Young 图之间的双射是通过利用以下构造性程序得到的。令 `M` 表示 Maya 图，`Y` 表示 Young 图，如附录 A.4 中所述。如附录所示，或观察 图 15.2，所有 Young 图都是水平条形图。条形在顶部行最大，然后随着条形向下，长度单调保持不变或减小。首先将证明，给定 `M`，唯一的 `Y` 将被找到。相应地，将描述逆过程。从附录 A.4 开始，`Y` 由 (*n*1′,*n*2,′…,*n**k*′)[(*p*, *q*)]![方程](img/F000291si81.png) 唯一确定，其中 (`p`, `q`) 是下标，提供 Young 图的左上部。这被给出为有界矩阵记号（Dourgherty and Giardina, 1987）。这里，正整数 `nj′` 用于表示 `Y` 中的实际行长。对于稍后给出的程序，将消除冗余行。也就是说，现在每行将具有唯一的尺寸，记为 `nj`，`j=1, 2,…, r`。将给出单独的规则来指示 `Y` 中行的重复。假设 `M` 参数 `w`、`b`、`nw` 和 `nb` 已如前所述已知。利用这些量，将找到 `p`、`q` 和 `nj`。首先，`p=(b 的整数部分)` 减去 `nb`。类似地，`q=(w 的上取整函数)` 加上 `nw`。这确定了 `Y` 结构的左上角。此外，第一块也是最大块由 `n1=nb` 给出。如果有的话，随后的块在 `Y` 中相邻放置在下方。

![图 15.2 从 Maya 图得到的 Young 图（参见示例 15.9）。](img/F000291f15-02-9780443136979.jpg)

图 15.2 从 Maya 图得到的 Young 图（参见示例 15.9）。

当存在其他块时，它们是从 `M` 中通过注意区间 (`w`, `b`) 中黑点簇以及分隔白点的数量得到的。黑点簇由连续的黑点串组成，其长度应计算为 `c1`、`c2`、… `cr`，其中 `c1` 是最左边的簇，其余的如果有则按顺序排列。白点也应注意。一个分隔两个黑点簇的单个白点表示左侧簇具有唯一长度。当 `k`、`k> 1` 个白点分隔两个黑点簇时，这意味着 `Y` 中的单元格块在彼此下方重复 `k` 次。另外，注意 `j=1` 到 `r` 的和 `cj=n1`。`Y` 中的第二个唯一行使用 `n2=n1−cr` 找到。此外，如果 `cr` 和 `c(r−1)` 黑点簇之间分隔的白点多于一个，则该行再次重复。在任何情况下，下一个唯一行使用 `n3=n2−c(r−1)` 找到。再次检查白点的数量。一般来说，`nk=n(k−1)−c(r−k+2)`，`k=2, 3,…, r`。结束条件是 `Y` 的最后一个唯一块大小为 `nr=n(r−1)−c2=c1`。最后，检查 `M` 的前两个簇之间的白点数；如果只有一个白点，则 `Y` 完成。否则，具有 `nr` 个单元格的最后一个块必须重复 `k` 次；`k` 是白点的数量。

## Example 15.9

考虑以下 Maya 图，其中 0 表示白点，X 表示黑点：

$\\begin{matrix} \\ldots & {{- 11}/{2.}} & {{- 9}/{2..}} & {{- 7}/{2..}} & {{- 5}/{2..}} & {{- 3}/{2..}} & {{- 1}/{2..}} & {1/{2\\ldots}} & {3/{2\\ldots}} & {5/{2\\ldots}} & {7/2} & {9/{2..}} & {11/{2..}} & {13/{2..}} & {15/{2..}} & {17/{2\\ldots}} \\\\ \\ldots & 0 & {X.} & {0.} & {0.} & {X.} & {X.} & {0.} & {X.} & {X.} & {0.} & {X.} & {X.} & {X.} & {0.} & {X\\ldots} \\\\ \\end{matrix}$

![方程](img/F000291si82.png)

还假设不存在其他颜色转换。因此，`w=−11/2`，因为所有白点从负无穷到包括 `w` 出现。同样，`b=17/2`，因为在此点及以后仅出现黑点。最后 `nb=8` 且 `nw=5`；这些是黑点和白卵石的数量，始终排除边界。从此信息，将创建一个唯一的 Young 图，参见 图 15.2。其起点为 (`p`, `q`)，其中 `p` 是 `w` 的整数部分等于 `17/2` 的整数部分减去 `nb`；因此 `p=8–8=0`。另外 `q` 等于 `w=−11/2+` 的上整数部分 `nw`；因此，`q=−5 +5=0`。在这种情况下，Young 图完全存在于第四象限，并且在 y 轴的负部分左对齐。最后的评论意味着 `Y` 中的所有条形都具有位于 y 轴上的左垂直边界。

如 图 15.2 所示，紧贴 x 轴的具有 `n1` 个单元格的第一块有 `n1=nb=8` 个单元格长。`Y` 中的下一个较低块具有唯一长度 `n2`，因为 `M` 的最后一个簇 `c4` 由单个白点分隔；因此 `n2=n1−c4=8–3=5`。类似地，由于单个点分隔第二和第三簇，这意味着 `Y` 中的 `n3` 是唯一的并且为 `n3=n2−c3=5–2=3`。然而，由于 `M` 中左侧、第一个和第二个簇之间分隔了两个点，块 `n4` 和 `n5` 相等且长度为 `n3−c2=3–2=1`。这与 `Y` 中最底部块的长度和 `M` 中第一个簇的长度一致。



## 从 Young 图形构造

现在反过来，给定一个 `Young diagram`，对应的唯一的 `Maya diagram` 将被构造。 该过程在初始化或设置之后给出。 再次参阅 `Appendix A.4`。 `M` 由 `(p, q)` 描述，其在 `R²` 中的整数位置，以及每个块的长度 `nj`，每个块彼此相邻且位于下方，左对齐。 回想一下，块从上到下形成一个有限的非递增长度序列。 这里，`nj` 可以等于 `n(j+1)`，也就是说，块长度可以在彼此下方重复。 构造带线的水平线和垂直线是有用的。 这些线在 `(p, q)` 处相互正交相交。 带线标记在水平方向上增加，在垂直方向上减少，均以相同的单位，即单元格边的大小。 `Y` 结构左对齐，通常位于第四象限。 所有带线都与构成每个条的单元格大小兼容。 直观地说，`Y` 中的所有垂直线段象征 `M` 中的白色点，而 `Y` 中的水平线段表示黑色点。

设置至关重要；它为确定 `M` 的初始、递归和最终阶段提供了环境。 `M` 中所有更小的半单位点也为白色的最大白色点 `w` 位置很容易找到。 它位于半个单位，在垂直方向上，正好在 `Y` 的底部条下方。 因此，`Y` 中底部条的最左单元格为 `(p, p+1\] x \[−h, −h+1)`；然后 `w = - h -1/2`。 这里 `h` 是构成 `Y` 的条的总数量；它是 `nj` 的数量。 在 `M` 中在 `w` 处以及 `w` 左侧的所有半整数点放置白色点。

接下来，`Y` 的轮廓从左到右、从下到上遍历。 这是下边界和左边界线段。 在轮廓沿线遍历的 `Y` 中每个单元格的每段水平线段，在 `M` 中放置黑色点。 在轮廓中向上移动时，对每个垂直单元格壁在 `M` 中放置白色点。 `M` 中这些点的每个位置从 `w` 开始并累积找到，即对于每个单元格向右的每段线段，在 `M` 的位置上增加一个黑色点。 另外，在 `Y` 的轮廓中向上移动的每段线段增加一个白色点。 因此，点将被分配到位置 `w+1`、`w+2` 等。 第一个黑色点是在遍历最底部和最左边的单元格 `(p, p+1\] x \[− h,−h+1)` 时找到的，向水平方向移动，从而在 `w+1 = 1/2 - h` 处标记一个黑色点。 下一个点放置在 `w+2`；如果底部条有多个单元格，则通过水平移动它将是一个黑色点，但如果底部块只有一个单元格，则方向向上，并在 `w+2` 处放置一个白色点。 下一个点放置在 `w+3`；对于轮廓中遍历的每个单位线段，水平移动为黑色，垂直移动为白色。 轮廓中的最后一段线段必须是垂直的。 它对应于单元格 `(p+n1–1, p+n1\] x \q−1, q)` 的右侧垂直边缘，表示应在 `p+n1–1/2` 处放置一个白色点。 最后，`b = p+n1+1/2`，并且在 `b` 以及所有更大的半整数点处，应有黑色点。

### 例 15.10

考虑 [图 15.3 中说明的 `Young diagram`。 从该图可以看出，`Y` 结构位于 `(p, q) = (0, 1)`，并且条的长度由有限序列给出：`(n1, n2, n3, n4) = (5, 3, 3, 1)`，并且 `h = 4` 因为 `Y` 中存在 4 个条。 作为边界向量，`Y` 为 `(5,3,3,1)[(0, 1)]`![方程](img/F000291si83.png)。

![图 15.3 用于求 Maya 图形的 Young 图形。](img/F000291f15-03-9780443136979.jpg)

图 15.3 用于求 Maya 图形的 Young 图形。

在最低条下方半个单位得到 `w = -3 1/2`。 该值可以通过代数方法使用 `w = q - h -1/2 = 1 - 4 -1/2` 找到。 也就是说，它可以从边界向量中找到，其长度为四，并且从 `(0, 1)` 开始。 y 分量为一。 无论如何，此点应标记为白色，同时小于 `w` 的所有半整数值也应标记。 所以：

$\\begin{matrix} {11/{2.}} & {{- 9}/{2..}} & {{- 7}/{2..}} & {{- 5}/{2..}} & {{- 3}/{2..}} & {{- 1}/{2..}} & {1/{2\\ldots}} & {3/{2\\ldots}} & {5/{2\\ldots}} & {7/{2\\ldots}} & {9/{2..}} & {11/{2..}} & {13/{2..}} & {15/{2..}} & {17/{2\\ldots}} \\\\ 0 & 0 & {0.} & & & & & & & & & & & & \\\\ \\end{matrix}$

![方程](img/F000291si84.png)

接下来，遇到由单个单元格组成的底部条；它是水平的，因此在位置 `-5/2` 绘制一个黑色点，比 `w` 多一个单位。 由于边界向量中的最后一个元组为一，因此出现一个黑色点。 在 `Y` 的轮廓上沿底部条向上移动，产生 `-3/2` 处的白色点。 现在以水平方式遇到倒数第二个条。 由于涉及两个单元格，因此在点 `-1/2` 和 `1/2` 处发出两个黑色点。 这两个黑色点出现是因为边界向量中倒数第二个元组与最后一个元组之间的差为二。 因此，在这一点上，`M` 图形如下：

$\\begin{matrix} {11/{2.}} & {{- 9}/{2..}} & {{- 7}/{2..}} & {{- 5}/{2..}} & {{- 3}/{2..}} & {{- 1}/{2..}} & {1/{2\\ldots}} & {3/{2\\ldots}} & {5/{2\\ldots}} & {7/{2\\ldots}} & {9/{2..}} & {11/{2..}} & {13/{2..}} & {15/{2..}} & {17/{2\\ldots}} \\\\ 0 & {0.} & {0.} & {X.} & {0.} & {X.} & X & & & & & & & & \\\\ \\end{matrix}$

![方程](img/F000291si85.png)

在轮廓中对块 3 和 2 向上移动会在位置 `3/2` 和 `5/2` 诱导出白色点。 同样，这两个连续的白色点可以从边界向量中看出，因为这两个元组具有相同的数字，三。 然后在块 1 上水平移动产生 `7/2` 和 `9/2` 处的黑色点。 如前所述，使用第一个和第二个元组之间的差值可提供黑色点的数量。 最后，轮廓遍历以在 `11/2` 处提供一个白色点结束。 从 `13/2` 开始，包括在内，所有点均为黑色。 最终的 `M` 结构为：

$\\begin{matrix} {11/{2.}} & {{- 9}/{2..}} & {{- 7}/{2..}} & {{- 5}/{2..}} & {{- 3}/{2..}} & {{- 1}/{2..}} & {1/{2\\ldots}} & {3/{2\\ldots}} & {5/{2\\ldots}} & {7/{2\\ldots}} & {9/{2..}} & {11/{2..}} & {13/{2..}} & {15/{2..}} & {17/{2\\ldots}} & \\\\ 0 & {0.} & {0.} & {X.} & 0 & X & X & {0.} & {0.} & {X.} & {X.} & 0 & {X.} & X & X & {.\\#} \\\\ \\end{matrix}$

![方程](img/F000291si86.png)

## 15.6 Maya 图形对费米子 Fock 空间的表示

费米子 Fock 空间作为向量空间 `V = direct sum complex-valued basis indexed by the half-integers`。 对于该空间中的元素 `w`，它可以在基中展开：`w = ej1 & ej2 & …`，其中 `jk` 是半整数的严格递增序列。 另外，`&` 是楔形，或与类型乘积。 每个楔形都可以可视化为一个 `Maya diagram`。 此外，费米子 Fock 空间可以被视为所有 `Maya diagrams` 在 `C` 上的自由张成。 该空间的标准基是 `Maya diagrams`。 真空态 (`vac`) 在每个正半区间仅具有白色点。 一般来说，如果仅在某个半整数 `n` 之外存在黑色点，则该图形被称为在 `n` 水平具有真空。 这也称为 `Fermi level`。



对于固定的 Maya 图 `M`，`k` 平移算子将黑点向左移动 `k` 个单位。它这样做，前提是 `M` 中不存在黑点当前占据半整数位置。具体而言，对于平移算子 `s_k` = 和，*Σ*(−1)^(*j*(*M*, *M*^′))![方程](img/F000291si87.png)。平移结束于 Maya 图 `M′`，并涉及从 `M` 开始连续的所有 Maya 图。它产生所有黑点向左移动 `k` 个空格的图，并带有正负号。函数 `j(M, M′)` 表示在 `M` 中当可用黑点重新定位时绕过的黑点数量。平移操作可以表示为涉及产生 `f^†` 和湮灭操作 `f` 的卷积型算子。事实上，`s_k` 等于以下和，${sk} = \\sum\\limits\_{\\mathit{ninZ} + 1/2}f^{\\dagger}\\left( k + n \\right)f\\left( n \\right)$![方程](img/F000291si88.png)。然而，函数 `j` 必须被用来跟踪跳过的点数 (Bouttier, 2019)。对于下一个例子，使用 `v(a/2)`，其中 `a` 是整数作为黑点的表示。这些是将会向左重新定位的点。

## Example 15.11
在本例中，原标准基由 Maya 图 `M` 给出，如下所示。它涉及楔积给出，`v(−5/2)` & `v(−1/2)` & `v(1/2)` & `v(7/2)` & `v(9/2)` & `v(13/2)` …. 如前所述，每个 `v(a/2)` 表示一个黑点位置。所有其他位置可视为空白或白点。设需求平移减去三个单位，即 `s(−3) M`。提供 `M` 中可重新定位的黑点位置列表是有用的，即它们不包含黑点，该列表是固定的。还应创建 `j(M,M′)` 值的对应列表。第一个列表是 {−5,2, −1/2, 9/2, 17/2}。这些是将向左平移的四个黑点。转换是使用该列表一次一个操作按左到右进行的。请注意，位置 1/2 处的黑点不可重新定位，因为向左 −3 个单位处被位置 −5/2 处的黑点占据。跳过黑点数 `j(M,M′)` 的对应有序列表是 {0, 1, 1, 2}。该列表中的最后一个数字 2 是 `M` 中介于 11/2 和 17/2 之间的黑点数。这是当位置 17/2 处的黑点向左重新定位三个单位时需要跳过的黑点数。对于该基 `M`，所得基 `M′` 将是四个下图的和或差。`M` 正下方是 `v(−5/2)` 的平移；它向左移动三个单位，抵达 −11/2。所得 Maya 图，记为 `M+`，为正，因为 `j(M,M+)=0`。下一个平移是 `v(−1/2)` 的，Maya 图出现在 `M+` 下方。然而它带有负号，因为在该平移中该黑点必须跳过 `M` 中的另一个黑点才能到达 −7/2。`M′` 是底部四个 Maya 图的和：

![](img/F000291u15-01-9780443136979.jpg)

有趣的是以卷积方式使用产生和湮灭公式，${sk} = \\sum\\limits\_{\\mathit{ninZ} + 1/2}f^{\\dagger}\\left( k + n \\right)f\\left( n \\right)$![方程](img/F000291si89.png)，来执行上述平移。在本例中，`k=−3`。因此，`s(−3)` 等于对 `n` 在 `Z+1/2` 中求和的 `f^†(n−3) f(n)`。从 `M` 开始处理将提供与前面提到的相同的 `M′`。从其初始位置 −5/2 开始，以 `M` 中第一个可用的黑点 `X` 开始。湮灭操作 `f` 去除 −5/2 处的黑点；这是 `f(−5/2)`。该黑点可用，因为重新定位位置 −3+(−5/2)= −11/2 没有被黑点占据。并且 `jMM′=0`，因为在当前位置与可重新定位位置之间没有黑点。因此，当使用产生操作 `f^†(−11/2)` 时采用正号，它重新定位起始黑点。

下一个可重新定位列表上的黑点 `X` 位于 `M` 中的 `n=−1/2`。在这种情况下，该点被 `f(−1/2)` 湮灭，从而去除黑点并将其替换为空，即白点。接下来，检查 `M` 中位置 −3 1/2 未被占据，并且由于是这种情况，产生算子，然后 `f^†(−7/12)`，在 `M′` 中该位置放置一个点 `X`。然而，在这种情况下重新定位过程中跳过了一个点，导致在 `M′` 中包含负号。类似地，对于位置 9/2 处的黑点 `X`，`f(9/2)` 执行 `X` 的湮灭，而 `f*(3/2)` 以整体负号在 3/2 处创建一个新的黑点，因为跳过了一个黑点。最后，位置 17/2 处的后黑点首先被湮灭，并在 11/2 处创建一个新的黑点，但这次带有正号，因为在过程中跳过了两个黑点。使用卷积得到的结果与之前相同。

## 15.7 Young diagrams representing quantum particles
对于具有哈密顿量 `H` 的置换不变性的 `n` 个全同粒子的系统，则不同置换的本征函数共享相同的本征值 `E`。设 `P` 为置换算子，`e(x1, x2, … xn)` 为本征值为 `E` 的本征函数。则 `Pe=Ee`。对称化操作为 `S=(1/n!) sum P`，而反对称化操作为 `A=(1/n!) sum P dp`；这里，所有求和都在 `Sn` 上，即 `n` 个对象的置换群。宇称 `dp` 对于 `P` 偶为 1，对于 `P` 奇为 −1。请注意 `dp=(−1)^(*t*)`，其中 `t` 是 `P` 中的对换数；另外 `d_p` = (−1)^((*n* − *c*))![方程](img/F000291si90.png)，其中 `P` 由 `c` 个循环组成。玻色子态由 Young 表的单行表示，其中态完全对称。同样，费米子态由 Young 表的单列表示，其中态完全反对称 (Yong, 2007)。Young 表是带有单元内标记以跟踪构型的 Young 图。

### Example 15.12
设 `u` 和 `v` 为正交单粒子态，`w` 为两粒子态，`w=u v`。更精确地，`w=u(x1) v(x2)`。由上可知，对于两个粒子，对称化操作 `S12=1/2 (I+P12)`，其中 `I` 是对称群 `S2` 中的恒等算子。对于 `w`，该算子投影对称部分；因此：`S12w=1/2 [u(x1) v(x2)+v(x1) u(x2)]`。反对称化操作为 `A12=1/2 (I−P12)`，于是 `A12w=1/2 [u(x1) v(x2)−v(x1) u(x2)]`。

与这些粒子构型相关的 Young 图包含两个单元。这些图具有相邻的两个水平单元或上下两个单元。前者图对应于两个一循环对称态的类，后者对应于两个循环即对换且因此反对称的态。两个水平单元对应于任意态：`u(x1) u(x2)`，`v(x1) v(x2)`，`1/2[u(x1) v(x2)+v(x1) u(x2)]`。最后一个量可写为 `1/2 [u1 v2+v1 u2]`。而垂直条对应于态 `1/2 [u(x1) v(x2)−v(x1) u(x2)]`，这也可以写为 `1/2 [u1 v2−v2 u1]`。

### Example 15.13
对于三粒子态的情况，Young 图的构造变得有点更复杂。`u`、`v` 和 `z` 三个单粒子态的排列将被利用。存在六个线性无关函数，将根据对称性性质描述。首先，完全对称模式 `w=1/3! [uvw+vwu+wuv+vuw+uwv+vuw]`。这再次对应于三个 1 循环，并且是 `V` 中的单水平条。它再次是恒等表示。完全反对称构型为 `w=1/3! [uvw−wvu+wuv−uwv+vwu−vuw]`。在 `Y` 中，这存在为单列。此外，这为 `S3` 生成另一个不可约表示。



除了 `bosonic` 和 `fermion` 之外，在三态量子粒子环境中还存在另外四种函数。这些具有混合对称性；首先，两个粒子可以被对称化，然后两个粒子可以被反对称化。这些粒子被称为夸克味本征态。四个夸克态的 `Y` 描述始终具有顶部两格的条和底部一格的条。就夸克味而言，可以说明重子波函数的生成，导致 `SU(3)` 的 27 维表示。这里可以找到由 `SU(3)` 不可约表示组成的 `Clebsch-Gordon` 级数。它们可以用 `Y` 和 `Weyl` 图来描述，并在角动量耦合中出现 (Messiah, 1981)。

## 15.8 Bogoliubov transform

`Bogoliubov` 变换是 `CCR` 或 `CAR` 的同构。具体来说，这些变换提供了将产生和湮灭操作变换为一组新的等价操作的条件。设原始的产生和湮灭操作分别为 `f^†` 和 `f`。新的操作为 `a^†` 和 `a`。`Bogoliubov` 变换 `T` 满足 `(a^† a)′`=`T` `(f^† f)′`，其中 `T` 满足对 `A`= 

```
\\begin{matrix} {|0} & {1|} \\\\ {|1} & {0|} \\\\ \\end{matrix}
```

![方程](img/F000291si91.png)

`TAT′` = `A`.

![方程](img/F000291si92.png)

### Example 15.14

设 `T` 如下给出，同时给出 `T`、`T A` 以及 `T′`，顺序如下：

```
\\begin{array}{llllll} {|i} & {0|} & {|0} & {i|} & {|i} & {0|} \\\\ {|0} & {{- i}|} & {|{- i}} & {0|} & {|0} & {{- i}|} \\\\ \\end{array}
```

![方程](img/F000291si93.png)

乘积 `T A T′`=`A`。因此，在此情况下，新的产生和湮灭操作由原始操作给出 `a^†`=i `f^†`，`a`=`−i` `f`。

## 15.9 Parafermionic and parabosonic spaces

这些空间建立在不可约表示支配波函数变换的置换群的前提之上。特别是，粒子态在广义对称性下变换。态存在于玻色态和费米态之间。精确的表示使用 Young 图给出。Quons 是一种理论上被认为同时表现出对称性和反对称性的粒子。处理 quons 的代数涉及来自玻色以及费米 Fock 空间的算符。具体来说，该算符是李括号和泊松括号的凸组合。事实上，对于 `r` 在区间 \[−1, 1\] 中，算符同时涉及湮灭 `a` 和产生操作 `a^†`，并且为 `(1+r)/2 [am, an^†]+(1−r)/2 {am, an^†}=dmn`，其中 `dmn`=0，除非 `m=n`；此时它等于一。真空态的定义与 Fock 空间中相同且 `am|0>`=0 如前所述。对于 `r`=1，玻色 Fock 空间在上述公式中被描述。类似地，对于 `r`=−1，费米 Fock 空间操作适用。描述 quons 的态时，对称群的不可约表示被加权。

## 15.10 Segal–Bargmann–Fock operations

全纯函数在量子力学中的一个应用是描述在 `R^(n)` 中运动的量子粒子的相空间。这里采用了 Segal–Bargmann–Fock (`SBF`) 空间 (Guillemin, 1984)。它是一个希尔伯特空间，其内积构造使得产生 `aj^†` 和湮灭算符 `ak` 彼此对易，并且 `aj^†` 是 `aj` 的伴随。`C^(n)` 中两个全纯函数 `F` 和 `G` 的内积对于 `L²(C^(n))` 中的函数为 `<F, G>`，其等于积分，∫(`F`(*z*) \* `G`(*z*)*e*^( − |*z*|²))*d**z*![方程](img/F000291si94.png) 其中 `dz` 是 *C*^(*n*) 上的 2n 维勒贝格测度![方程](img/F000291si95.png)。该表示是高斯型积分。

Fock 观察到复变量中的共轭坐标操作服从对易关系。因此，共轭坐标操作是解析性柯西-黎曼准则的一种形式。这些方程涉及偏导数：`∂ /∂zj*`=1/2 (`∂/∂xj`+i`∂/∂yj`) 和 `∂/∂zj`=1/2 (`∂/∂xj`−i`∂ ∂/∂yj`)。全纯函数永远不能是 `z*` 的函数，因此任意解析函数 `F` 的偏导数满足 `∂F/∂zj*`=0。忽略普朗克常数并将 `zj` 与乘法型操作等同，将偏导数 `∂/∂zk` 与动量操作等同，则对易子：[`zj`, `zk`]=[`∂/∂zj`, `∂/∂zk`]=0，且 [`∂/d∂zj`, `zk`]=0 对于 `j` 不等于 `k`，相等时为一。这里，`aj*` 是提升或产生操作，而 `aj` 是降低或湮灭操作，其定义域为全纯多项式，这是一个 `SBF` 的稠密子空间。

## 15.11 Many-body systems and the Landau many-body expansion

二次量子化为多体量子系统提供了基础。Fock 空间提供了基本设定以及玻色和费米产生和湮灭操作。一体算符的表示被给出。这些算符操纵 N 维希尔伯特空间中的单个粒子。类似地，描述了二体算符，说明了粒子之间的相互作用。

Landau 提出了一个展开，涉及由具有相互作用自变量的各种元数算符产生的相互作用粒子数。对于元数为一的算符，也称为单体或单粒子算符，它们用 `T1` 表示。元数为二且其操作数相互作用的算符称为两粒子或二体算符，用 `T2` 表示。元数为三且其操作数相互作用的算符称为三粒子或三体算符，用 `T3` 表示。依此类推。

展开如下：Sum，

```
\\sum\\limits\\_{j}{{T1j} + {Sum}},{\\sum\\limits\\_{j < k}{{T2jk} + {Sum}},{\\sum\\limits\\_{j < k < m}{{T3jkm} + \\ldots}}
```

![方程](img/F000291si96.png)

在二次量子化中，该展开涉及玻色或费米产生算符 `a^†`![方程](img/F000291si97.png) 和 `c^†`![方程](img/F000291si98.png)，以及相应的湮灭算符 `a` 和 `c`。在这种情况下，展开如下：Sum，

```
\\sum\\limits\\_{j,k}{\\left. {{T1aj}^{\\dagger}{ak}} \\right) + {1/2}{({Sum}}},{\\sum\\limits\\_{j,k,m,n}{{{{T2aj}^{\\dagger}{ak}^{\\dagger}{an}{am}})} + \\ldots}}
```

![方程](img/F000291si99.png) 该展开用于玻色子，但相同的展开也适用于费米子。产生和湮灭操作接下来给出，并应用于二次量子中的单体和二体问题。

## 15.12 Single-body operations

单粒子或一体算符在 N 粒子 Fock 空间中定义为求和，

```
\\sum\\_{k = 1}^{N}{bk}
```

![方程](img/F000291si100.png)，其中 `bk` 是作用于第 k 个粒子态的算符。最重要的算符是数算符 `nk`，它是位置 k 处的粒子数。量 `nk`=`ak^†ak`；这里给出玻色子的情况。回忆数算符的本征态 (`ak^†`)^(*k*) |vac> 的本征值为 k，即 `nk` (`ak^†`)^(*k*) |vac>=k (`ak^†`)^(*k*) |vac>。此外，产生算符 `aj^†` (|…, `nj`, …>)=( `nj+1`)^(1/2) (|…, `nj+1`, …>)，而湮灭算符满足 `aj` |…, `nj`, …>= `nj^(1/2)` |…, `nj−1`,…>。对于费米 Fock 空间，数算符为 `nk`=`ck^†ck`。此时产生算符为 `cj^†`(|…, `nj`, …>)=(1−`nj`)^(1/2) (|…, 1−`nj`, …>)，而湮灭算符满足 `cj` (|…, `nj`, …>)=( `nj`)^(1/2) (|…, 1−`nj`, …>)。玻色算符与费米算符之间的主要区别在于前者在产生两个粒子时是对称的，而后者是反对称的。即，`aj^†ak^†|0>`=`ak^†aj^†|0>`=`|1j 1k>`，但 `cj^†ck^†|0>`=`− ck^†cj^†|0>`=`|1j 1k>`=`− |1k 1j>`。



## 单体操作
单体操作 `T1` 将粒子从态 `v` 转移到态 `v′`，概率为 `<v |T1|v′>`，其中 `T1` = 求和，$\\sum\_{j = 1}^{N}{Tj}$ ![Equation](img/F000291si101.png)，且 `Tj` 仅作用于粒子 `j`。公式为 `T1` = 求和，$\\sum\\limits\_{v,v^{\\prime}} < {v|T|v}\\prime > {av} \\ast {av}\\prime$ ![Equation](img/F000291si102.png)。

### 例 15.15
`N` 个粒子的系统的动能为 `T`，求和，$\\sum\_{j = 1}^{N}{{pj}^{2}/\\left( 2m \\right)}$ ![Equation](img/F000291si103.png)，其中 `p_j` 为动量，`m` 为粒子质量。单体操作的二次量子化为 `T1` = 求和，$\\sum\\limits\_{u,v} < {u|}p^{2}/\\left( 2{m)|v} > {au}^{\\dagger}{av} \\right.$ ![Equation](img/F000291si104.png)。该公式变为 `T1` = 求和，$\\sum\\limits\_{k,s}h^{2}k^{2}/\\left( 2m \\right){aks}^{\\dagger}{aks}$ ![Equation](img/F000291si105.png)。这里 `k` 表示动量矢量，`s` 为自旋。记号可通过注意到数算符，在本例中为 `n_k_s` = `a_k_s†` ![Equation](img/F000291si106.png) `a_k_s` 来概括，它计数具有动量 `k` 和自旋 `s` 的粒子数。

## 15.13 双体操作
与单体算符类似，双粒子算符守恒粒子数。
双体相互作用的公式为 `T2` = 1/2 求和对 `v`、`v′`、`u` 和 `u′` 的 `<u, v |T| u′, v′>` `au†` `av†` `av′` `au′`。量 `<u, v |T| u′,v′>` 表示涉及 `T` 的双粒子积分（Hall, 2013）。

## 参考文献
* Borstnik and Nielsen, 2021 Borstnik N, Nielsen H. *Clifford 代数如何为具有统一自旋、电荷和族的第二量子化费米子以及超出标准模型的矢量和标量规范场指明道路* Department of Physics, University of Ljubljana 2021;.
* Bouttier, 2019 Bouttier, J., 2019. Fermions in Combinatorics: Random Permutations and Partitions. 可从 [fermions.sciencesconf.org](http://fermions.sciencesconf.org) 获取。
* Dourgherty and Giardina, 1987 Dourgherty E, Giardina C. 0-13-453283-X *从连续到离散的图像处理* Prentice-Hall 1987;.
* Gazeau, 2009 Gazeau J. *量子物理中的相干态* Wiley 2009;.
* Guillemin, 1984 Guillemin V. n 维的 Toeplitz 算子。 *Int Eq Op Theory*. 1984;7.
* Hall, 2013 Hall B. *数学家的量子理论* Springer 2013;.
* Messiah, 1981 Messiah A. *量子力学*. 卷 1 ISBN 10: 0720400449: North Holland; 1981;.
* Rutgers Physics, 2018 Rutgers Physics, 2018. 第 10 章，Clifford 代数。
* Slater, 1929 Slater J. 复杂谱的理论。 *Phys Rev.* 1929;34.
* Townsend, 2000 Townsend J. 1-891389-13-0 *量子力学的现代方法* University Science Books 2000;.
* Yong, 2007 Yong A. 什么是杨表。 *Notices AMS*. 2007;54.

# 第 16 章
## 量子计算的底层理论
## 摘要
本章首先描述了 `Hilbert group`，即构建量子门和电路的基本群。以下各节提供了大量单量子位量子门的示例。此外，这些门的分类是用么正李群 `U(2,C)` 以及特殊李群 `SU(2,C)` 术语给出的。下一节推导并说明了 `Pauli rotation matrices`。随后是对多输入门 `CNOT` 门的深入处理。以下各节描述了交换门，然后是通用门集的概念。接下来简要介绍了 `Haar` 测度。随后描述了量子计算中最重要的结果 `Solovay–Kitaev` 定理。随后一节提供了 `quantum Fourier transform` 的描述以及示例。接下来的两节用于准备解释和求解 `Grover` 问题。均匀叠加和幅度放大在下一节中进行了解释和说明。本章以反射原理结束。

### 关键词
`Hilbert group`；`CNOT` gate；`Hadamard` gate；幅度放大；`Solovay–Kitaev` 定理；`Grover` 问题；`Quantum Fourier transform`；`Pauli rotation matrices`；`Haar` 测度

## 16.1 量子计算和量子电路
量子计算可以像涉及输入和输出的电路的常规计算一样进行。它也可以作为一种专门的优化类型，即绝热计算进行。在任何情况下，本章或以下章节中提到的所有方法都具有大于常规计算机的加速。然而，量子计算相对于阶为 `N` 的常规计算的加速永远不会超过二次方。已证明 (Bennett et al., 1997) 量子计算的阶为 `N` 平方根是尽可能最优的。量子电路型计算机和常规计算机在某些方面相似；然而，它们在许多方面也不同。
关于量子电路最根本的是输入必须是从某个希尔伯特空间的量子位。此外，这些电路的描述类似于工程学科中的输入-输出块型图示。在工程中，不同的输入通常彼此不相关；它们之间没有关系。然而在量子中，这些图示通常表示张量在一起的输入量子位，并且它们进入电路，通常以这种结构方式链接。此外，量子电路的输出数量始终等于输入数量。通常，计算以测量多个输出量子位的张量积结束。结果是波函数的坍缩。这将在后面描述的所有量子算法中都是如此。此外，对量子位执行的所有操作 `T` 必须是线性么正操作。后一要求为 `T T* = T* T = I`。将量子位的希尔伯特空间映射到自身的全部么正算符集合形成一个群，称为 `Hilbert group`。`Hilbert group` 的 MSA 描述在 图 16.1 中给出。这里，如通常一样，多元图说明了来自签名集的闭包操作。附带有一份等式恒等式的列表，用于严格指定群。
![Figure 16.1 Hilbert group.](img/F000060f16-01-9780443136979.jpg)
图 16.1 Hilbert group.
在量子电路中证明算符 `T` 为么正的最简单方法是证明矩阵与其伴随的乘积为单位矩阵。`T` 为么正算符的一个充分条件是它既是对合又是正规的。即分别证明 `T² = I` 和 `T T* = T* T`。这一结果是有限维正规算符谱定理的推论。如果 `T` 是正规的，则 `T = A D A*`，其中 `D` 是由 `T` 的特征值组成的对角矩阵，重复多次，`A` 为么正。如果 `T` 是对合，则 `D² = I`，因此所有特征值都是正负一。这表明 `D` 既是自伴又是么正的，因为 `T = A D A*` 且 `A` 为么正表明 `T` 也是么正的。ket 表示为布洛赫球上的唯一点。

### 例 16.1




考虑将载体集设为 `C²`，以及算子 `T`：`C²→C²`。请注意，如果 `T²=I`，即如果 `T` 是对合，则这不足以验证 `T` 是幺正的。仅仅证明一个操作是可逆的不足以证明该操作是幺正的。为说明这一点，设对合矩阵 `T`=

$\\begin{matrix} {|{- 1}} & {1|} \\\\ {|{ 0}} & {1|} \\\\ \\end{matrix}$

![Equation](img/F000060si1.png)

然后 `T` 即使 `T²=I` 也不是幺正矩阵，因为 `T T*` 不等于 `I`。

## 16.2 单量子比特量子门

量子电路中的幺正操作称为量子门。因此，量子电路由量子门组成。量子门通常具有单量子比特输入，但某些门具有多量子比特输入。当单量子比特作为门的输入时，这最常使用 `C²` 中的表示来执行，如前述示例所示。以下示例再次涉及作用于以 `C²` 表示的量子比特的线性算子。所有这些算子都属于前面提到的希尔伯特群，但此外所有这些算子还属于特定的李群。作为提醒，某些李群的重要代数规范将快速回顾。特别是，特殊幺正李群 `SU(n,C)` 是一个实李群，由行列式为一的幺正 n×n 矩阵组成。一般幺正实李群 `U(n,C)` 由行列式绝对值等于一的 n×n 幺正矩阵组成。一般来说，量子比特 `|v>` 的整体相位被忽略。更严格地说，量子比特属于射影空间 `P^n(C)=CP^n`，但这一事实不会被强调。在任何情况下，对于 `[0, 2π)` 中的实数 `p` 和 `[0, π]` 中的实值 `t`，`C²` 中的一般 ket 为 `|v>`，并且它可以用 kets 的叠加写成：`|v>=(cos(t/2))|0> + e^(ip) sin(t/2)|1>`。前述表示中仅省略了整体相位。

### 示例 16.2

Hadamard 门 `H` 的输入为单量子比特，设 `|v>=a|0>+b|1>=(a b)'`，在 `C²` 中，其中 `|a|²+|b|²=1`。该门由矩阵 `H` 指定，给出为

$\\begin{matrix} {{1/2}^{1/2}{|1}} & {{ 1}|} \\\\ {{|1}} & {{- 1}|} \\\\ \\end{matrix}$

![Equation](img/F000060si2.png)

该矩阵是对合，即 `H²=I`。检查表明它是对称的，因此是自伴的，因而是正规的。因此，`H` 也是幺正的。乘法 `H|v>` 给出列向量，`1/2^(1/2)`![Equation](img/F000060si3.png) `(a+b a−b)'`。再次利用 ket 表示法，可得 `H|v> = 1/2^(1/2)[(a+b)|0>+(a−b)|1>]`![Equation](img/F000060si4.png)。特别地，`H|0> = 1/2^(1/2)[|0>+|1>] = |+>`![Equation](img/F000060si5.png) 并称为正态。类似地，`H|1> = 1/2^(1/2)[|0>−|1>] = |−>`![Equation](img/F000060si6.png) 并称为负态。这两个量子比特位于布洛赫球表面上的 x 轴上，见 图 5.3。

Hadamard 矩阵的不同表示是使用涉及 ket 和 bra 量子比特的外积；事实上，`H = 1/2^(1/2)(|0><0|+|0><1|+|1><0|−|1><1|)`![Equation](img/F000060si7.png)。该表示很有用，因为无需使用 `C²` 中的向量作为表示。简而言之，kets 和 bras 可以直接由前面描述的 `H` 操作。接下来说明如何求值 `H` 作用于输入量子比特。例如，要找到 Hadamard 矩阵作用于南极量子比特，`H|1>`。利用线性可得 `H|1> = 1/2^(1/2)(|0><0|1>+|0><1|1>+|1><0|1>−|1><1|1>) = 1/2^(1/2)(|0>−|1>)`![Equation](img/F000060si8.png)。最后结果成立是因为 `|0>` 和 `|1>` 各自具有单位长度并且彼此正交，所以例如 `<0|1>=0` 且 `<0|0>=1`。最后，注意 `H` 的行列式为负一。这表明 `H` 在李群 `U(2, C)` 中，但不在李群 `SU(2, C)` 中。然而，经常使用修正的 Hadamard 矩阵，例如使用 `iH`。在这种情况下，矩阵 `iH` 在 `SU(2,C)` 中，因为 `(iH)(iH)*=(iH)(-iH)=H²=I`。

### 示例 16.3

NOT 门也具有单量子比特输入；在这种情况下，输出只是交换零量子比特和一量子比特，反之亦然。因此，对于如前例中的量子比特 `|v>`，`|v>=a|0>+b|1>=(a b)'`，在 `C²` 中，其中 `|a|²+|b|²=1`。使用 NOT 进行求值 `|v>=NOT(a|0>)+NOT(b|1>)=a NOT|0>+b NOT|1>=a|1>+b|0>`，正如所示，这说明了该算子的线性性质。还展示了使用括号以获得更清晰的表示，例如使用 `NOT(a|0>)`，但不要使用 `NOTa|0>`。在任何情况下，在希尔伯特空间 `C²` 中操作，NOT 操作的矩阵如下：

$\\begin{matrix} {|0} & {1|} \\\\ {|1} & {0|} \\\\ \\end{matrix}$

![Equation](img/F000060si9.png)

该矩阵既对称又是 involution，因此 NOT 是幺正操作。NOT 门可以描述为外积的线性组合。因此，`NOT=(|0><1|+|1><0|)`。由于 NOT 的行列式为负一，与 Hadamard 矩阵一样，NOT 在 `U(2, C)` 中，而不在 `SU(2, C)` 中。

### 示例 16.4

恒等门 `I`，其中 `I: C²→C²`，如下所示：

$\\begin{matrix} {|1} & {0|} \\\\ {|0} & {1|} \\\\ \\end{matrix}$

![Equation](img/F000060si10.png)

它用外积 bras 和 kets 表示为 `I=|0><0|+|1><1|`。因此，任何输入到该门的 `|v>` 均未改变地退出。由于行列式为一，`I` 在 `SU(2,C)` 中。

下一个单量子比特操作的示例涉及一个单一的但著名的相位门。

### 示例 16.5

`π/8` 相位门也称为 T 操作，是 Hadamard、H、T 门集的一部分。相应地在 `C²` 中操作的矩阵如下：

$\\begin{array}{ll} {|e^{{- i\\pi}/8}} & {0|} \\\\ {|0} & {e^{{i\\pi}/8}|} \\\\ \\end{array}$

![Equation](img/F000060si11.png)

请注意该矩阵不是对合。然而重要的是 T 矩阵是幺正矩阵且行列式为一。因此，`T` 是李群 `SU(2, C)` 的成员。通常，在量子领域，T 门定义略有不同。这里，它表示为上述 T 门乘以 `e^(iπ/8)`![Equation](img/F000060si12.png)，有时还如下所示：

$\\begin{matrix} {|i} & {0|} \\\\ {|0} & {{e^{{i\\pi}/4}|}.\\#} \\\\ \\end{matrix}$

![Equation](img/F000060si13.png)

### 示例 16.6

上述 T 门的推广是 PHI 门，涉及非零角度 `ϕ`![Equation](img/F000060si14.png)，该角度有不可数无限多个取值。具体地，`PHI`=

$\\begin{matrix} {|1} & {0|} \\\\ {|0} & {{e^{i\\phi}|}.\\#} \\\\ \\end{matrix}$

![Equation](img/F000060si15.png)

在量子计算中使用具有可采用不可数多个角度的灵活性的算子是必须的。这是因为所涉及的李群是具有不可数多个元素的拓扑空间。下一个量子门 S 是 Clifford+T 集合的成员。算子 T 在示例 16.5 中说明。

### 示例 16.7

S 门称为相位移门。它表示为将希尔伯特空间 `C²`![Equation](img/F000060si16.png) 映射到自身的矩阵。`S`=

$\\begin{matrix} {|1} & {0|} \\\\ {|0} & {i|} \\\\ \\end{matrix}$

![Equation](img/F000060si17.png)



这个矩阵是幺正的，但行列式等于 `i`；因此，`S` 是幺正李群 `U(2, C)` 的成员。它不在 `SU(2, C)` 中。请注意，这是上面指定的 `PHI` 门的特例，其中 `ϕ`=`π`/2。该算符连同 `T` 算符以及 `H`，构成了 `Clifford+T` 有限群。Clifford 单量子比特群在后续章节中描述。已证明 Clifford +T 集合是通用的，并且该集合中的某些矩阵串可以用具有代数数元素的矩阵表示。此外，`SU(2, C)` 中条目 `U` 关于 `H`、`S` 和 `T` 的某些近似是形式为：{`T` 或空} {`HT` 或 `HST`} 的矩阵串。

### 示例 16.8
这是一个例子，说明 `S` 门如何作用于量子比特 `|q>`=(cos (`t`/2) e^(`i` `p`) sin (`t`/2))′，在布洛赫球上。首先形成 `S`|q>=(cos (`t`/2) `i` e^(`i` `p`) sin (`t`/2))；然后由于 `i` = `e`^(`i` `π`/2) ![方程](img/F000060si18.png)，可得 `S`|`q>` = (cos(`t`/2) `e`^(`i`(`p` + `π`/2)) sin(`t`/2)) ![方程](img/F000060si19.png)。参考布洛赫球，应用 `S` 后的新量子比特现在位于新的经度，但与 `|q>` 相同的纬度。它相对于 `|q>` 绕 z 轴逆时针旋转 90 度。z 轴指向上方。达布向量是常用于表示引起旋转的角速度向量的名称。

## 16.3 泡利旋转算符
下一个门集合涉及之前指定的三个泡利矩阵，并在下面再次给出，按顺序为 `X`、`Y` 和 `Z`：
```
$\begin{matrix} {|0} & {1|} & {|0} & {{- i}|} & {|1} & {0|} \\ {|1} & {0|} & {|i} & {0|} & {|0} & {{{- 1}|}.} \\ \end{matrix}$
```
![方程](img/F000060si20.png)
这些矩阵被指数化，得到泡利旋转算符。它们在下一个示例中进行了说明。所有旋转算符都可以使用 Frobenius 协变式与 Lagrange-Sylvester 插值来求得，或使用幂级数方法。参见 第 5.5 节，关于 Frobenius 协变式与 Lagrange-Sylvester 插值。

### 示例 16.9
与泡利矩阵对应的三个旋转矩阵如下：`RX` = `e`^( − `i` `t` `X`/2 )，`RY` = `e`^( − `i` `t` `Y`/2 ) ![方程](img/F000060si21.png)，以及 `RZ` = `e`^( − `i` `t` `Z`/2 ) ![方程](img/F000060si22.png)。这些旋转矩阵按顺序如下所示：
```
$\begin{matrix} {|{{c t}/2}} & {{{- \text{is} t}/2}|} & {|{{c t}/2}} & {{{- s t}/2}|} & {|e^{{- it}/2}} & {0|} \\ {|{{- \text{is} t}/2}} & {{{c t}/2}|} & {|{{s t}/2}} & {{{c t}/2}|} & {|0} & {e^{{- it}/2}|} \\ \end{matrix}$
```
![方程](img/F000060si23.png)
这里，`c t/2` 表示 cos(`t`/2)，而 `s t/2` 表示 sin(`t`/2)。对于应用这些矩阵的单量子比特，它们使量子比特绕布洛赫球对应的 x-、y- 或 z- 轴旋转。所有三个矩阵都在 `SU(2, C)` 中。
为了推导 `RX` = `e`^( − `i` `t` `X`/2 ) ![方程](img/F000060si24.png)，请注意 `RX` = `c` `t`/2 `I` − `i` `s` ![方程](img/F000060si25.png) `t`/2 `X`，其中 `I` 是单位 2×2 矩阵，`X` 是第一个泡利矩阵。根据余弦和正弦表达式，通过代入即可立即得出结果。更一般地，`RX` 的表达式也可以如前所述通过使用 `X` 的特征值来求得。这是 第 5.5 节 中指定的方法。利用 Frobenius 协变方法，由于 `X` 的特征值是 `x1`=1 和 `x2`=-1，Frobenius 协变式为 `X1`=1/2 (`X`+`I`) 和 `X2`=-1/2 (`X`-`I`)。`RX` = `e`^( − `i` `t` `X`/2 ) 的 Lagrange-Sylvester 插值公式为 = `e`^( − `t` `i`/2 ) `X1` + `e`^( `t` `i`/2 ) `X2` = 1/2[(`e`^( − `t` `i`/2 )+`e`^( `t` `i`/2 ))`I`+(`e`^( − `t` `i`/2 )−`e`^( `t` `i`/2 ))`X`] ![方程](img/F000060si26.png)。代入 `I` 和 `X` 得到与之前给出的相同解。
重要的是泡利旋转矩阵中角度 `t` 的含义。`R(t)` 中的该角度 `t` 是根据布洛赫球球坐标系采用的角度。以下是一个示例。

### 示例 16.10
在布洛赫球表面，球坐标向量 `q` 定位纯量子比特 `|q>`。例如，沿 x 轴 `q[x]`=(1 0 0) 是量子比特的位置，`|q[x]>`=1/2^(1/2) (`|0>`+`|1>`) =(cos(`π`/4) sin(`π`/4))′=1/2^(1/2) (1 1)′。此外，沿 x 轴，注意 `q[-x]`=(−1 0 0) 是量子比特的位置，`|q[-x]>` ![方程](img/F000060si27.png) =1/2^(1/2) (`|0>`−`|1>`) =(cos(`π`/4) −sin(`π`/4))′。最后，`q[y]`=(0 1 0) 定位量子比特 `|q[y]>`=1/2^(1/2) (`|0>`+`i`|1>`) =(cos(`π`/4) `i` sin(`π`/4))’。请注意，将 `RZ` 应用于 `|q[x]>` 得到 (−`i` cos(`π`/4) `i` sin(`π`/4))’=−`i`|q[-x]>`，其中整体相位 −`i` 与单量子比特处于射影空间 `CP¹` 无关。接下来，`RZ` 乘以 `|q[x]>` 得到 1/2 (1−`i` 1+`i`)′=1/2 ((1−`i`) cos(`π`/4) (1+`i`) sin(`π`/4))′=(1−`i`)/2^(1/2) (cos(`π`/4) (1+`i`)/(1−`i`) sin(`π`/4))’=`|q[y]>`。再次，整体相位无关紧要。最后，使用 `RY`，乘以 `|q[x]>` 得到南极量子比特 `|1>`。2^(1/2) 的矩阵表示
```
$R_{Y}(\pi/2) = \begin{matrix} {|1} & {{- 1}|} \\ {|1} & {{1|}.} \\ \end{matrix}$
```
![方程](img/F000060si28.png)
将 `RY` 乘以列向量 `|q[x]>`=1/2^(1/2) (1 1)′，得到表示南极的量子比特 `|1>`。
泡利旋转算符具有一种通用性质，即对于 `U(2, C)` 中的任意 `U`，存在实数 `a`、`b`、`c` 和 `d`，使得幺正算符可以用三个泡利算符表示：`U`=e^(`i` `a`) `RZ` `RY` `RZ`（Nielsen 和 Chuang, 2000）。

### 示例 16.11
请注意，哈达玛门 `H` 可以用上述表达式表示，即 `H`=e^(`i` `a`) `RZ` `RY` `RZ`。这里，`RZ`=`I`，下面给出 `RY`、`RZ` ![方程](img/F000060si29.png) 以及 `RY` `RZ` ![方程](img/F000060si30.png)，顺序如下：
```
$\begin{array}{llllll} {|{{c\pi}/4}} & {{- s\pi}/4} & {|{- i}} & {0|} & {|{{- i}/2}^{1/2}} & {{{- i}/2}^{1/2}|} \\ {|{{s\pi}/4}} & {{{c\pi}/4}|} & {|0} & {i|} & {|{{- i}/2}^{1/2}} & {{{{- i}/2}^{1/2}|}.} \\ \end{array}$
```
![方程](img/F000060si31.png)
令 e^(`i` `a`)=`i`，即 `a`=`π`/2，上面的最右矩阵为 `H`。上一节中的其他门用泡利旋转算符表示甚至更容易。例如，相移门 `S` = `e`^( `i` `π`/4 ) ![方程](img/F000060si32.png) `RZ` ![方程](img/F000060si33.png)。
Clifford 单量子比特群由哈达玛矩阵和相移矩阵 `H` 和 `S` 生成。该群定义为幺正矩阵 `U` 的集合，当其作用于泡利矩阵 `P` 时，`U` `P` `U*` 该量再次得到泡利矩阵。该群的基数为 24。

### 示例 16.12
注意 `S` `X` `S*`=`Y`，`S` `Z` `S*`=`Z`，`H` `X` `H*`=`Z`，以及 `H` `Z` `H*`=`X`。对于最后一个恒等式，注意量 2^(1/2) ![方程](img/F000060si34.png) `H` `Z` 和 `H` `Z` `H*` 按顺序给出且等于：
```
$\begin{matrix} {|1} & {{- 1}|} & {|0} & {1|} \\ {|1} & {1|} & {|1} & {{0|}.} \\ \end{matrix}$
```
![方程](img/F000060si35.png)

## 16.4 多量子比特输入门



如前所述，涉及多个量子位的运算通常将这些量子位张量在一起输入。对于涉及两个量子位的情况，运算 `X`：`H` ⊗![方程](img/F000060si36.png) `H`→`H` ⊗![方程](img/F000060si37.png) `H`。其实例是算符 `X`=`CNOT`。最常见的是，对于多量子位门，第一量子位用作控制量子位。这意味着实际运算作用于另一个，即第二个量子位。这里，第二个量子位的状态取决于第一个量子位的状态，第二个量子位称为目标。下文将详细介绍此类运算的示例。

考虑 `CNOT` 门，也称为条件非运算。该运算的输入为 `|x>` ⊗![方程](img/F000060si38.png) `|y>`，其中 ⊗![方程](img/F000060si39.png) 表示张量运算。张量积更简写为 `|x y>`，其中 `x` 是第一个或上方的量子位，第二个是 `y`。`x` 和 `y` 只能取零或一的值。该门在 图 16.2 中示出。

![图 16.2 CNOT 门。](img/F000060f16-02-9780443136979.jpg)

图 16.2 `CNOT` 门。

如该图可见，第一量子位 `|x>` 保持不变地通过。底部输出为量子位 `|y (+) x>`，其中 `(+)` 表示 `mod2` 运算或异或。因此 `|y (+) x>`=0 当且仅当 `x`=`y`；否则等于 1。`CNOT` 运算在 `C⁴`![方程](img/F000060si40.png) 中由矩阵给出：

$\\begin{matrix} {|1} & 0 & 0 & {0|} \\\\ {|0} & 1 & 0 & {0|} \\\\ {|0} & 0 & 0 & {1|} \\\\ {|0} & 0 & 1 & {{0|}.} \\\\ \\end{matrix}$

![方程](img/F000060si41.png)

上述 `CNOT` 矩阵是对称的且是对合；这表明 `CNOT` 运算是幺正的。在利用张量积后，该矩阵将 `|x y>` 作为列向量在 `C⁴`![方程](img/F000060si42.png) 中相乘。该输入有四种可能；如下所示：`|0 0>`=`|0>` ⊗![方程](img/F000060si43.png) `|0>`=`(1 0)`′ ⊗![方程](img/F000060si44.png) `(1 0)`′，`|0 1>`=`(1 0)`′ ⊗![方程](img/F000060si45.png) `(0 1)`′，`|10>`=`(0 1)`′ ⊗![方程](img/F000060si46.png) `(1 0)`′，最后，`|11>`=`(0 1)`′ ⊗![方程](img/F000060si47.png) `(0 1)`′。4x1 向量表示按对应顺序给出为列向量：

$\\begin{matrix} {|1|} & {|0|} & {|0|} & {|0|} \\\\ {|0|} & {|1|} & {|0|} & {|0|} \\\\ {|0|} & {|0|} & {|1|} & {|0|} \\\\ {|0|} & {|0|} & {|0|} & {{|1|}.} \\\\ \\end{matrix}$

![方程](img/F000060si48.png)

矩阵 `CNOT` 作用于这些向量且顺序完全相同时的结果如下：

$\\begin{matrix} {|1|} & {|0|} & {|0|} & {|0|} \\\\ {|0|} & {|1|} & {|0|} & {|0|} \\\\ {|0|} & {|0|} & {|0|} & {|1|} \\\\ {|0|} & {|0|} & {|1|} & {|0|} \\\\ \\end{matrix}$

![方程](img/F000060si49.png)

现在这些结果向量必须以张量 ket 的形式解释。

将上述 4x1 向量按顺序用 ket 表示，得到 `|0 0>`、`|0 1>`、`|1 1>`，最后是 `|1 0>`。因此，当第一个量子位为零时，输出为 `|x y>` 且保持不变。当第一个量子位为一时，第二个量子位翻转，即输出变为 `|x (1−y)>`。`CNOT` 的行列式为负一，因此它属于李群 `U(4, C)`，但不属于李群 `SU(4, C)`。

请注意，`CNOT` 算符是纠缠器，同时也是解纠缠器。例如，`CNOT`(1/2^(1/2) (`|0 0>`+`|1 0>`))=1/2^(1/2) (`|0 0>`+`|1 1>`)；最后的量子位对是纠缠的。它是贝尔态之一。为此，首先注意 `|+0>`=1/2^(1/2) (`|0>`+`|1>`) ⊗![方程](img/F000060si50.png) `|0>`，因此 `CNOT` 的输入未纠缠。最后，要看出输出是纠缠的，注意最一般的 `|0>` 和 `|1>` 量子位张量积为 `z`=`a11`|0>` ⊗![方程](img/F000060si51.png) `|0>`+`a12`|0>` ⊗![方程](img/F000060si52.png) `|1>`+`a21`|1>` ⊗![方程](img/F000060si53.png) `|0>`+`a22`|1>` ⊗![方程](img/F000060si54.png) `|1>`。张量称为纯张量当且仅当 `a11 a22`=`a12 a21`；否则它是纠缠的。这里 `a21`=0，但 `a11`=`a22`=1。有关纠缠的更多信息，请参阅 第 7.4 节。

最后，`Pauli` 矩阵 `X`、`Y` 和 `Z` 如下：

$\\begin{matrix} {|0} & {i|} & {|0} & {{- 1}|} & {|i} & {0|} \\\\ {|i} & {0|} & {|1} & {0|} & {|0} & {{- i}|} \\\\ \\end{matrix}$

![方程](img/F000060si55.png)

`CNOT` = `|0>`  `<` `0`| ⊗ `I` + `|1>`  `<` `1`| ⊗ `X` = (`I`+`Z`) ⊗ `I` + (`I`−`Z`) ⊗ `X`/2

![方程](img/F000060si56.png)

在更高维的希尔伯特空间中，幺正算符可以用 `U(4,C)` 中的 `CNOT` 门以及 `U(2,C)` 中的单量子位门来替代（Nielsen and Chuang, 2000）

`n` 个量子位上的 `Pauli` 群由 `{1, −1, i, −i} x {I, X, Y, Z}^(@*n*)` 组成，其中最后一组涉及 `Pauli` 矩阵张量在一起 `n` 次。与单量子位情况类似，Clifford `n` 量子位群由所有幺正矩阵 `U` 组成，使得对于 `n` 量子位 `Pauli` 群中的 `P` 和 `P′`，有 `U P U*`=`P′`。

### 示例 16.13

对于两量子位情况，注意当按顺序通过相乘以下三个矩阵 `CNOT`、(`Z` ⊗![方程](img/F000060si57.png) `I`)、`CNOT*` 进行运算时，结果为 `Z` ⊗![方程](img/F000060si58.png) `I`。即 `CNOT`.(`Z` ⊗![方程](img/F000060si59.png) `I`). `CNOT*`=`Z` ⊗![方程](img/F000060si60.png) `I`。 likewise，`CNOT`.(`I` ⊗![方程](img/F000060si61.png) `Z`). `CNOT*`=`Z` ⊗![方程](img/F000060si62.png) `Z`，`CNOT`.(`I` ⊗![方程](img/F000060si63.png) `X`). `CNOT*`=`I` ⊗![方程](img/F000060si64.png) `X`，和 `CNOT`.(`X` ⊗![方程](img/F000060si65.png) `I`). `CNOT*`=`X` ⊗![方程](img/F000060si66.png) `X`。对于最后一个恒等式，注意 `X` ⊗![方程](img/F000060si67.png) `I`、`CNOT`.(`X` ⊗![方程](img/F000060si68.png) `I`) 和 `X` ⊗![方程](img/F000060si69.png) `X` 按顺序如下所示：

$\\begin{matrix} {|0} & 0 & 1 & {0|} & {|0} & 0 & 1 & {0|} & {|0} & 0 & 0 & {1|} \\\\ {|0} & 0 & 0 & {1|} & {|0} & 0 & 0 & {1|} & {|0} & 0 & 1 & {0|} \\\\ {|1} & 0 & 0 & {0|} & {|0} & 1 & 0 & {0|} & {|0} & 1 & 0 & {0|} \\\\ {|0} & 1 & 0 & {0|} & {|1} & 0 & 0 & {0|} & {|1} & 0 & 0 & {{0|}.} \\\\ \\end{matrix}$

![方程](img/F000060si70.png)

## 16.5 交换操作

`CNOT` 门在创建其他重要门时也很有用。特别是，交换门是通过连续使用三个 `CNOT` 门设计的。参见 图 16.3。交换门的符号为 `SWAP`。使用时 `SWAP`: `H`[`A`]⊗`H`[`B`]→`H`[`B`]⊗`H`[`A`]![方程](img/F000060si71.png)。对于输入态 `|x y>`，交换门给出 `SWAP`(`|x y>`) = `|y x>`。它以第一个位作为第一个 `CNOT` 中的控制位开始。然后第二个位在第二个 `CNOT` 中用作控制位，最后在最后一个 `CNOT` 中，第一个位再次用作控制位。以下序列说明了交换操作，其中单个箭头表示使用 `CNOT` 运算：`|x y>`→![方程](img/F000060si72.png) `|x, x (+) y>`→![方程](img/F000060si73.png) `|x (+) x (+) y, x (+) y>`=`|y, x (+) y>`→![方程](img/F000060si74.png) `|y, x (+) y (+) y>`=`|y x>`。

![图 16.3 SWAP 门。](img/F000060f16-03-9780443136979.jpg)

图 16.3 `SWAP` 门。

## 16.6 通用量子门集



## 通用量子门集

直观上，通用量子门集（`UQGS`）是一组固定、有限数量的幺正算符，依次应用时可以逼近 `SU(2, C)` 中的任意幺正操作。算符按从左到右的复合方式应用。然而，它们被表示为操作串的连接，按顺序标记。设 `G = {g[1], g[2], …, g[m]}` 是 `SU(2, C)` 的有限子集。长度为 `n` 的词为 `w[n] = g[1] g[2] …, g[n]`，其中 `g[i]` 在 `G` 中且 `n` 大于或等于 1。由 `G` 生成的长度不超过 `n` 的所有词的集合记为 `G[n]`。所有 `n < ∞` 时的 `G[n]` 的并集记为 `<G>`。当 `<G>` 在 `SU(2, C)` 中稠密时，一组门是 `UQGS`。也就是说，对于 `SU(2, C)` 中的任意 `U`，以及 `ϵ > 0`，存在 `<G>` 中的算符串 `g`，使得距离 `d(U, g)` 小于 `ϵ`。该度量由迹范数诱导，`‖A‖ = tr[(A* A)^(1/2)]`。迹范数满足等式恒等式和不等式：
1. 三角不等式：`‖A + B‖ ≤ ‖A‖ + ‖B‖`。
2. 次乘性：`‖A B‖ ≤ ‖A‖ ‖B‖`。
3. 幺正不变性：`‖U A V‖ = ‖A‖` 对于所有幺正算符 `U` 和 `V`。

算符范数也被使用；它为 `‖A‖ = sup |A v|`，其中 `‖v‖ = 1`。对于 `U(2, C)` 中的 `U` 和 `V`，`U` 逼近 `V` 的含义是 `d(U, V) = sup ‖(U − V) v‖ < ϵ`，其中 `‖v‖ = 1`。对于两个量子门串 `U = U[1] U[2] …, U[n]` 和 `V = V[1] V[2] …, V[n]`，则有 `d(U, V) ≤ Σ d(U[i], V[i])`。这可通过 `n = 2` 的情况得到，并可由数学归纳法证明。对于 `n = 2`，`d(U[1] U[2], V[1] V[2]) = sup ‖(U[2] U[1] – V[2] V[1]) v‖ = sup ‖(U[2] U[1] – V[2] U[1] + V[2] U[1] – V[2] V[1]) v‖ ≤ sup ‖(U[2] U[1] – V[2] U[1]) v‖ + sup ‖(V[2] U[1] – V[2] V[1]) v‖ = sup ‖(U[2] – V[2]) U[1] v‖ + sup ‖V[2] (U[1] – V[1]) v‖ = d(U[2], V[2]) + d(U[1], V[1])`。注意此处可用 `max` 代替 `sup`，并且算符的操作顺序与字符串记法相反。

最受欢迎的 `SU(2, C)` 的 `UQGS` 由哈达玛门 `H` 和 `π/8` 门 `T` 组成。证明使用了泡利旋转算符。第 16.3 节 说明哈达玛门是泡利旋转算符的乘积。另外，`T = RZ`。在证明 `{H, T}` 是 `UQGS` 时，`T` 门和 `HTH` 门串被依次使用。在以任意精度产生逼近时，一个重要的恒等式是 `T H T H = RZ RX`。更一般的 `UQGS` 在 Lloyd (1995) 中有所解释。

## 16.7 Haar 测度

Haar 测度 `u` 最好理解为左 `G` 不变测度（Nachbin, 1965）。这里 `G` 是一个局部紧拓扑群。对于乘法二元运算，不变测度满足 `u(x V) = u(V)`，其中 `x` 是群 `G` 的元素，`V` 是 Borel 可测集。附录 A.2 提供了相关测度论概念的概述。

历史上，Haar 测度最初被表述为基于单位测度的绝对测度的近似。Haar 测度的单位测度使用 `E` 作为 `G` 的 Borel 子集，`V` 是 `G` 的非空开子集。然后令 `(E: V)` 表示覆盖 `E` 所需的 `V` 的左平移的最小数量。因此，`(E: V) = inf {cardinality of A such that E is a subset of the union of x V, for x in A, A a subset of G}`。因此 `(E: V)` 可视为 `E` 的相对测度。

固定一个预紧开子集 `Eo`，并将其测度指定为一。预紧意味着该集合的闭包是紧的。然后将以下式子作为 `E` 的绝对测度的近似：`(E: V) / (Eo: V)`。注意对所有 `x` 在 `G` 中，`(E: V) / (Eo: V) = (E x: V) / (Eo: V)`，且该运算是左 `G` 不变的。当 `V` 收缩到单位元时取极限可知 Haar 测度被定义为该极限。于是，`u(E) = limit [(E: V) / (Eo: V)]`，当 `V → I`。

对于 `G`，一个局部紧拓扑群，Haar 定理断言存在一个在 `G` 的 Borel 子集上的可数可加测度，至多相差一个正乘性标量，使得
1. 测度如前所述是左不变的。
2. 对于 `G` 的紧子集 `K`，`u(K) < ∞`。
3. 该测度在 `G` 的 Borel 集上外正则，在 `G` 的开集 `U` 上内正则，分别有 `u(S) = inf {u(U) such that S is a subset of an open set, U in G}`，且 `u(U) = sup {u(K) such that K is a subset of U and K is compact}`。

### 例 16.14

设 `G` 的载体集为正实数 `R+`，在乘法下，具有实数线上的通常拓扑。那么对于 `R` 中的任意 Borel 子集 `B`，可使用通常的 Cauchy-Riemann、Riemann 或 Lebesgue 积分构造 Haar 测度：`u(B) = ∫[B] 1/x dx`。对于任意 Borel 集，例如区间 `[2, 4]`，相应的测度为 `u([2, 4]) = ln(4) − ln(2) = ln(2)`。另外，对于 `R+` 中的任意正实数，例如三，将区间乘以三，则 Haar 测度 `u([6, 12]) = ln(12) − ln(6) = ln(2)` 再次成立。这说明了使用包含 `R+` 中元素的乘法群的 Haar 测度的不变性。

## 16.8 Solovay–Kitaev 定理

`SU(2, C)` 中的幺正算符被幺正算符串 `S[1] S[2] … S[n]` 逼近的概念在 第 16.6 节 中有所描述。该串构成一个 `UQGS`，并以 `{H, T}`、哈达玛门和 `π/8` 门集为重点进行了说明。在本节中，逼近的接近程度与幺正算符串中元素个数 `n` 相关。

Solovay–Kitaev 定理（`SK`）给出了用物理可实现幺正门的串来逼近任意行列式为一的 2x2 幺正矩阵的构造性方法。逼近精度在 `ϵ > 0` 以内。该串是来自通用门集 `S` 的门的有限乘积。`SK` 结果表明所需门乘积串的长度为 `O(log⁴(1/ϵ))` 量级。为使这些逼近成立，门集 `S` 必须在 `G` 中稠密。

更精确地说，考虑 `SU(2, C)` 的有限子集 `S`，它包含逆元且在 `SU(2, C)` 中稠密。那么存在常数 `c`，在 `[1, 4]` 中，使得对于任意这样的 `S` 和 `ϵ > 0`，可选择 `n`，其中 `n = O(log^c (1/ϵ))`，使得 `S^n` 是 `SU(2, C)` 的 `ϵ` 网。对于 `SU(2, C)` 中的任意 `U`，存在 `S^n` 中的门串 `S[1] S[2] … S[n]`，使得 `d(S[1] S[2] … S[n], U) < ϵ`。距离度量 `d` 由迹范数诱导。即 `d(A, B) = ‖A − B‖`。因此对于 `SU(2, C)` 中的 `A, B`，`‖A‖ = Tr[(A A*)^(1/2)]`，这也等于 `A` 的两个特征值的绝对值之和。简而言之，`SU(2, C)` 的 `ϵ` 网意味着 `SU(2, C)` 是以 `S^n` 中的串 `S[1] S[2] … S[n]` 为中心、半径为 `ϵ` 的开球并集的有限子集。因此，对于 `SU(2, C)` 中的每一个幺正算符，都存在来自 `S^n` 的门串，其结果与之相差 `ϵ` 以内。



The `SK` 逼近中接近性的判据与逼近算子串长度的增加成反比。群交换子 \[U, V\][*G*]\=UVU\*V\* 在 `SK` 的证明中被采用。它用于确定幺正算子与恒等算子 `I` 的接近程度。群交换子与 `SU(2, C)` 中 `U`、`V` 的通常李括号有关，如下：\[U, V\]=0，则 \[U, V\][*G*]\=I。这是因为 \[U,V\]=0，这意味着 `UV=VU`；然后在群交换子中，\[U, V\][*G*]\=UVU\*V\*，用 `VU` 替换 `UV` 得到 \[U, V\][*G*]\=VUU\*V\*，这就是恒等式。

因此，群交换子接近恒等式当且仅当两个算子可交换。反复应用此交换子关系使得可以对恒等元做出 ![ent](img/epsi_1013.png`)net 逼近。最后通过平移，可以看出该逼近对 `SU(2, C)` 中的任意幺正算子都成立。`SK` 定理的大多数证明采用收缩引理，指定使用更长串获得恒等式的更好逼近。对恒等式的邻域做出越来越小的 ![ent](img/epsi_1013.png`)net 逼近。证明的最后一步是利用距离的双不变性将 ![ent](img/epsi_1013.png`)nets 平移到逼近 `SU(2, C)` 中的其他元素。深入的细节在 Zarapico (2018) 中提供。对于具有代数项的 `UQGS` 中的 `S` 且 ![ent](img/epsi_1013.png`) > 0，`n` 可以选择为 `n=0(log^(*c*) (1/![ent](img/epsi_1013.png`)))`，其中 `c=1` (Holevo, 2003; Bourgian and Gamburd, 2001)。

## 16.9 量子傅里叶变换与相位估计

量子傅里叶变换 (`QFT`) 用 `F` 表示，将复希尔伯特空间 `C^(*N*)` 中的向量映射回 `C^(*N*)`，其中通常 `N` 是正整数 `2^(*n*)`。具体而言，对于 ${|{x > = \\sum\_{j = 0}^{N - 1}x\_{j}}|}j >$![Equation](img/F000060si84.png`)，`QFT`，$F\\left( {|{x >}} \\right) = \\sum\_{j = 0}^{N - 1}y\_{j}{|j} >$![Equation](img/F000060si85.png`)，其中 $y\_{j} = 1/N^{1/2}\\sum\_{k = 0}^{N - 1}{x\_{k}\\left( w\_{N} \\right)^{km}}$![Equation](img/F000060si86.png`)，对于 m=0, 1, 2, …, N−1。另有，*w*[*N*] = *e*^((2*i**π*)/*N*)![Equation](img/F000060si87.png`)。逆 `QFT` 也有类似定义。它同样将复希尔伯特空间 *C*^(*N*)![Equation](img/F000060si88.png`) 中的向量映射回 *C*^(*N*)![Equation](img/F000060si89.png`)。在这种情况下，$x\_{j} = 1/N^{1/2}\\sum\_{k = 0}^{N - 1}{y\_{k}\\left( w\_{N} \\right)^{- km}}$![Equation](img/F000060si90.png`)，对于 m=0, 1, 2, …, N−1。`QFT` 及其逆可以作为幺正矩阵 *U*[*N*]![Equation](img/F000060si91.png`) 实现，作用于量子态向量。

### 示例 16.15

在希尔伯特空间 `C²` 中，`QFT`，`F=H`，即哈达玛变换。这是因为 *w*[*N*] = *e*^((2*i**π*)/*N*) = *w*[2] = *e*^((2*i**π*)/2) =  − 1![Equation](img/F000060si92.png`)。因此，${|{x > =}}\\sum\_{j = 0}^{1}x\_{j}{|j} > ,F\\left( {|{x >}} \\right) = \\sum\_{j = 0}^{1}{y\_{j}{|j}} >$![Equation](img/F000060si93.png`)，其中 $y\_{j} = 1/2^{1/2}\\sum\_{k = 0}^{1}{x\_{k}\\left( w\_{2} \\right)^{km}}$![Equation](img/F000060si94.png`)，对于 m=0, 1。*F*(|*x*\>) = 1/2^(1/2)\*x*[0⁰+*x*1⁰\]|0 >  + 1/2^(1/2)\*x*[0⁰+*x*1¹\]|1 >  = 1/2^(1/2)\[*x*[0]+*x*[1]\]|0 >  + 1/2^(1/2)\[*x*[0]−*x*[1]\]|1>![Equation](img/F000060si95.png`)。因此可得 `F` (|x>)=`H` (x[0] x[1])′.#

### 示例 16.16

在 `C⁴` 中，设 ${|{x > =}}\\sum\_{j = 0}^{N - 1}{x\_{j}{|j}} >$![Equation](img/F000060si96.png`) = 1/3(|0>+2*i*|2>−2|3>) = 1/3(|00>+2*i*|10>−2|11>)![Equation](img/F000060si97.png`)。注意范数‖|x>‖=1。目标是求 `QFT`，`F` (|x>)。这将使用幺正矩阵 *U*[4]![Equation](img/F000060si98.png`) 计算。下面给出 2*U*[4]![Equation](img/F000060si99.png`)，随后是向量 3|x> 表示为 *C*⁴![Equation](img/F000060si100.png`) 中的四乘一列向量，

$\\begin{matrix} {|1} & 1 & 1 & {1|} \\\\ {|1} & i & {- 1} & {{- i}|} \\\\ {|1} & {- 1} & 1 & {{- 1}|} \\\\ {|1} & {- i} & {- 1} & {i|} \\\\ \\end{matrix}\\quad\\quad\\begin{matrix} {|1|} \\\\ {|0|} \\\\ {|{2i}|} \\\\ {{|{- 2}|}.} \\\\ \\end{matrix}$

![Equation](img/F000060si101.png`)

将四乘四矩阵 2*U*[4]![Equation](img/F000060si102.png`) 与 *C*⁴![Equation](img/F000060si103.png`) 中的四乘一向量 3|x> 相乘，得到 `F` (|x>)=1/6 (−1+2i 1 3+2i 1–4i)′。注意 `F` (|x>) 的范数为 1。这必须如此，因为幺正映射始终是等距映射；因此它保持向量的长度。#

执行 `QFT` 的量子电路涉及输入每个量子位，然后首先使用哈达玛矩阵，随后使用若干受控旋转矩阵的序列，其形式为：

$\\begin{matrix} {|1} & {0|} \\\\ {|0} & {e^{{2i\\pi}/{{(2^{k})}x\_{j}}}|} \\\\ \\end{matrix}$

![Equation](img/F000060si104.png`)

这对每个输入量子位都采用。

## 16.10 均匀叠加与振幅放大

在量子算法中，哈达玛门的重要应用之一是对几乎每个输入都使用它。通常，输入的数量为 `n`，并且全部是|0> 量子位。在这种情况下，该操作称为扩散操作。假设哈达玛算子并行应用于每个输入，它表示为 $H^{@n}\\left( {|{0 >^{@n}}} \\right) = 1/2^{n/2}\\sum\_{x = 0}^{N - 1}{{|x} >}$![Equation](img/F000060si105.png`)，其中 *N* = 2^(*n*)![Equation](img/F000060si106.png`)，张量积用 @ 表示。因此，均匀叠加中任何向量|x> 的相关概率为 1/2^(*n*)![Equation](img/F000060si107.png`)。由于所有振幅相同，任何|x> 的平均高度也为 1/2^(*n*)![Equation](img/F000060si108.png`)。

### 示例 16.17

考虑双输入系统，$H^{@2}\\left( {|{0 >^{@2}}} \\right) = 1/2\\sum\_{x = 0}^{3}{{|x} >}$![Equation](img/F000060si109.png`)。从数学上讲，这是因为 *H*|0 >  = 1/2^(1/2)(|0>+|1>) = | + >![Equation](img/F000060si110.png`)，并且由于有两个并行的哈达玛门，计算为 *H*^(@2)(|0>^(@2))![Equation](img/F000060si111.png`)。因此形成 |+> 与自身的张量积，即给出 |+> @|+>=1/2 \[|0 0>+|0 1>+|1 0>+|1 1>\]。将每个 ket |x> 按二进制解释，提供相同的结果，即 $1/2\\sum\_{x = 0}^{3}{{|x} >}$![Equation](img/F000060si112.png`)。简单的计算表明，均匀叠加中的这些向量各自长度为单位且彼此正交。最后这一性质最好通过 *C*⁴![Equation](img/F000060si113.png`) 中的表示来看。在这种情况下，每个 ket 由一个四乘一向量表示。每个向量包含除不同位置的单个一之外的所有零值元组。#



# 振幅放大

设 `|w>` 为 `N` = 2^(`n`) ![Equation](img/F000060si114.png) 个态 ${|{w > = 1/2^{n/2}}}\\sum\_{x = 0}^{N - 1}{{|x} >}$ ![Equation](img/F000060si115.png) 的均匀叠加。 然后这些向量通常在条形图中表示，横坐标上有 `N` 个垂直线段条目，高度均为 1/2^(`n`/2) ![Equation](img/F000060si116.png)。 见 图 16.4A。 均匀叠加通常是振幅放大算法的初始态。 其典型例子是 Grover 搜索，描述在下一章中。 在最简单的形式中，该搜索利用对 {`R[W]`, `U[f]`}，由两个反射算符组成，用于在 `|w>` 中找到单个向量 `|x*>`。 第一个反射 `U[f]` 的一次应用否定 `|x*>` 的值或将其关于横坐标反射。 也就是说，它变为 −`|`x*>`，或图形上它在线段图中反射态 `|x*>`；见 图 16.4B。 该算符也称为预言机。 在此图中，一条虚水平线表示 `U[f]|w>` 中所有态的概率振幅的新较低平均值 `u`。 概率振幅的整体较低平均值或整体较低均值出现的原因是 `U[f]` 的应用保持所有态不变但它否定了 `|x*>`。 因此这种单一否定会略微拉低整体平均振幅。 该平均值与涉及实际概率的真实平均值无关。 这是因为 `|x*>` 和 −`|`x*>` 的实际概率相同。 振幅的绝对值平方给出真实概率，因此该量不变。

![图 16.4 振幅放大的轨迹。 (A) 均匀叠加，(B) 态|x*> 的反射，(C) 振幅放大，(D) 再次应用一个半反射对，(E) 应用两个反射对/.](img/F000060f16-04-9780443136979.jpg)

图 16.4 振幅放大的轨迹。 (A) 均匀叠加，(B) 态 `|x*>` 的反射，(C) 振幅放大，(D) 再次应用一个半反射对，(E) 应用两个反射对/。

下一个反射操作 `R[W]` 在此定义为均值的反射，或实际上是振幅的平均值 `u`。 因此，对于任意向量 `a[y]|y>`，其中 `|y>` 在 {0, 1}^(`n`) 中，关于该均值 `u` 的反射操作满足 `R[W] (a[y]|y>) = (2 u - a[y])|y>`。 通过从高度 `a[y]` 中减去 `u`，得到 (`a[y] - u`) 来证明该等式成立。 然后将该量关于 x 轴反射，如同 `U[f]` 的一次应用。 该操作仅否定该量。 因此结果为 (`u - a[y]`)，最后抬升，即再次加上 `u` 提供所需结果。

由于对于 `U[f]|w>` 中的所有向量 `U[f]|x>`，均值较小，除了 `U[f]|x*>`，应用算符 `R[W]` 会使这些振幅变得更小。 然而，`R[W] U[f]|x*>` 的振幅将变为其原始值的约三倍。 见 图 16.4C，图示并非按比例。 振幅放大是指利用一对反射算符如 `R[W]` 和 `U[f]` 连续应用的过程。 如果再次应用反射对，则首先，`U[f] R[W] U[f]|w>` 如 图 16.4D 所示，而 `R[W] U[f] R[W] U[f]|w>` 如 图 16.4E 所示。 无论如何，反射对的重复应用会产生所有态振幅的递减平均值，同时增加期望态的概率振幅。 这种有益的增加前提是 `π`/4`N`^(1/2) ![Equation](img/F000060si117.png) 次 `R[W]U[f]` ![Equation](img/F000060si118.png) 的应用未被超过。

这些反射是 Grover 搜索的基石。 该搜索对于诸如寻找最有效路径和类似优化问题等物流应用很有用。 它也用于机器学习算法，特别是分类问题。 此外，难以计算但易于验证的单向函数使用 Grover 搜索方法可提供良好结果。

## 16.11 反射

在有限希尔伯特空间 `H = C²` 中，反射具有精确的含义。 反射被用作线性算符 `R[W]`，`R[W]`: `H` → `H`。 该算符始终应用于非零向量 `|v>`。 通过这样做，它将该向量 `|v>` 关于指定的非零向量 `|w>` 反射。 见 图 16.5A，其中 `|v>` 和 `|w>` 连同反射的 ket `R[W]|v>` 一并示出。 最终结果用虚线书写。 其最简单的实例是当 `|w> = |0> = (1 0)'` 在计算基中，且 `|v> = (a b)'` 时。 那么 `R[W]|v> = (2|0><0| - I)|v> = (a -b)'`。 该操作也称为 Householder 反射 (Householder, 1958)。 如上一节所述，使用扩散算符表示 `|w> = H^(@n) (|0>^(@n))`。 那么 `R[W]|v> = H^(@n) [2|0^(@n)><0^(@n)| - I] H^(@n)|v> = (2|w><w| - I)|v>`。

![图 16.5 反射操作。: (A) 两个向量和反射 ket，(B) 反射操作的结果。](img/F000060f16-05-9780443136979.jpg)

图 16.5 反射操作。: (A) 两个向量和反射 ket，(B) 反射操作的结果。

因此，关于 `w` 执行反射的算符由 `R[W] = (2|w><w| - I)` 给出，其中 `I` 是恒等操作。

### 示例 16.18

设 `|w> = |0>` 为执行反射的简单向量。 如果待反射的向量为 `|v> = (3/5)^(1/2)|0> + (4/5)^(1/2)|1> = ((3/5)^(1/2)(4/5)^(1/2))` ![Equation](img/F000060si119.png)′ 在 `C²` ![Equation](img/F000060si120.png) 中，则执行反射的算符涉及纯密度函数 `|w><w|` 的两倍，以及恒等函数的负值。 因此 `R[W] =` ![Equation](img/F000060si121.png)

$\\begin{matrix} {|1} & {0|} \\\\ {|0} & {{{- 1}|}.} \\\\ \\end{matrix}$

![Equation](img/F000060si122.png)

将该算符应用于向量 `|v>` 给出 `R[W]|v> = (3/5)^(1/2)|0> - (4/5)^(1/2)|1> = ((3/5)^(1/2) - (4/5)^(1/2)))` ![Equation](img/F000060si123.png)′ 在 `C²` ![Equation](img/F000060si124.png) 中。 见 图 16.5B。#

反射算符是 Grover 搜索方法中的关键操作。 该算符与符号交替操作一起反复执行以执行该搜索。

## 参考文献

* Bourgian and Gamburd, 2001 Bourgian, J., Gamburd, 2001. SU(d) 中的一个特殊间隙定理. arXiv: 1108.6264.
* Bennett et al., 1997 Bennett C, Bernstein E, Brassard G, Vazirani U. 量子计算的优势与劣势. *SIAM J Comput.* 1997;26(5):1510–1523.
* Holevo, 2003 Holevo A. 受约束输入的量子信道的经典容量. *Probab Theory Appl.* 2003;48:359 (quant–ph)/(0211179).
* Householder, 1958 Householder A. 非对称矩阵的酉三角化. *J ACM* 1958;.
* Lloyd, 1995 Lloyd S. 几乎任何量子逻辑门都是通用的. *Phys Rev Lett.* 1995;75.
* Nachbin, 1965 Nachbin L. *Haar 积分* Van Nostrand 1965;.
* Nielsen and Chuang, 2000 Nielsen MA, Chuang IL. *量子计算与量子信息* Cambridge: Cambridge University Press; 2000;.




* Zarapico, 2018 Zarapico, J., 2018. 量子计算中的有效酉近似：索洛韦-基塔耶夫定理（论文）。巴塞罗那大学。

# 量子计算应用

## 摘要
本章首先对 Deutsch 问题进行了深入描述，该问题是最早具有量子解优于经典解的问题之一。下一节描述了 Deutsch oracle，随后给出了量子解的细节。接下来的章节描述了 Deutsch-Jozsa 问题以及提供相应解的量子电路。量子计算中第二重要的算法是 Grover 算法。它在许多应用中被使用，特别是在机器学习中。问题及其解均有描述。它相对于经典方法提供了二次的运行时间改进。第 17.8 节从代数角度描述了 Shor 密码问题。接下来的章节提供了椭圆曲线（EC）密码学以及在比特币中的应用的细节。MSA 观点在描述 EC 中阿贝尔群的基础时得以延续。随后给出了在伽罗瓦域上 EC 上点加法的代数描述。下一节概述了 Shor 的量子解。本章以简要描述涉及 EC 的 Diffie–Hellman 密钥交换结束。

### 关键词
Deutsch 问题；Deutsch oracle；Deutsch-Jozsa 问题；Shor 算法；椭圆曲线密码学；欧拉 totient 函数；Diffie–Hellman 密钥交换；弦倍增；点加法；Weierstrass 标准型

## 17.1 Deutsch 问题描述
Deutsch 问题是最早具有量子解优于经典解的问题之一。该问题涉及一个函数 `f`，`f: {0, 1}→{0, 1}`，目标是确定该函数是常数还是平衡的。常数意味着输出始终相同，不论输入值如何。平衡意味着输出对一个输入值是零，对另一个输入值是一。下面的五个列说明了所有可能性。第一列提供了函数 `f` 的输入；它以元组形式为零或一。接下来的两列给出了 `f` 的输出，说明了常数概念。最后两列是平衡函数 `f` 的输出。

$\\begin{matrix} {|0|} & {|0|} & & {|1|} & {|0|} & & {|1|} \\\\ {|1|} & {|0|} & & {|1|} & {|1|} & & {|0|} \\\\ {INPUT} & ˄ & {CONSTANT} & ˄ & ˄ & {BALANCED} & ˄ \\\\ \\end{matrix}$

![方程](img/F000023si1.png)

经典上要确定 `f` 是常数还是平衡，显然需要两次查询。首先必须对输入值，例如零，计算 `f`，然后必须对另一个输入值一进行计算。这在上面用常数函数的两种可能性和平衡函数的两种可能性表示。量子解只需一次查询即可确定 `f` 是否为常数或平衡。细节涉及使用 oracle，即酉变换 `U`，它作为黑盒表示，示例如 图 17.1 所示。

![图 17.1 Deutsch oracle.](img/F000023f17-01-9780443136979.jpg)

图 17.1 Deutsch oracle。

## 17.2 Deutsch 问题解的 Oracle
在 图 17.1 中，oracle 给出为黑盒；唯一已知的是 `U` 将四个维度映射到自身。`U: C² (x) C²→C² (x) C²`，其中 `U` 是一个操作，使得 `U (|x> |y>)=|x>|(y(+) f(x))>`，对于所有 `x`、`y`、`f(x)` 在 `{0, 1}` 中。加法 `(+)` 是 `mod(2)` 操作，与逻辑中的异或相同。因此每当 `y` 和 `f(x)` 为相同值时，结果为零；否则结果为一。只允许酉操作。证明 `U` 是酉算子通过证明 `U` 是对合，即 `U²=I`，恒等函数。还要求 `U` 是正规算子，即 `U*U=UU*`。首先，通过连续两次应用 `U` 显示对合，所以 `U²(|x>,|y>)=|x> |(y(+) f(x) (+) f(x))>=|x> |y>`；这表明对合，因为 `f(x) (+) f(x)=0`。一旦黑盒或 oracle 被识别为对称矩阵 `U=`，`U` 的正规性将立即成立

$\\begin{array}{llll} {|{1 - f(0)}} & {f(0)} & 0 & {0|} \\\\ {|{f(0)}} & {1 - f(0)} & 0 & {0|} \\\\ {|0} & 0 & {1 - f(1)} & {{f(1)}|} \\\\ {|0} & 0 & {f(1)} & {{1 - f(1)}|} \\\\ \\end{array}$

![方程](img/F000023si2.png)

将第二个输入量子位 `|y>`，表示在 `C⁴` 中，与 `U` 相乘始终提供 oracle 的第二个输出。稍后给出说明。

矩阵 `U` 包含了涉及一对输入量子位的所有四种情况，`|x>` 为控制，`|y>` 为目标，以及输出量子位对 `|x>` 和 `|y (+) f(x)>`，其中 `x`、`y` 和 `f(x)` 为 0 或 1，且 `(+)` 为 mod 2。这些四种不同场景在最后四列中列出。第一列表示 `|x y>` 的输入量子位对值。最后四列给出 `|x y(+) f(x)` 的输出值，使用四种情况：1) `f(0)=f(1)=0`；2) `f(0)=0, f(1)=1`；3) `f(0)=1, f(1)=0`；4) `f(0)=f(1)=1`。这些按顺序给出，其中情况 1) 和 4) 对应常数 `f`，情况 2) 和 3) 为平衡 `f`。检查所有情况下的第二列，即右手列，提供结果。

$\\begin{matrix} & {1)} & {2)} & & {3)} & {4)} \\\\ 00 & 00 & 00 & & 01 & 01 \\\\ 01 & 01 & 01 & & 00 & 00 \\\\ 10 & 10 & 11 & & 10 & 11 \\\\ 11 & 11 & 10 & & 11 & 10 \\\\ {INPUT} & {CONSTANT} & ˄ & {BALANCED} & ˄ & {CONSTANT} \\\\ \\end{matrix}$

![方程](img/F000023si3.png)

与 `U` 相关联的矩阵有四个，所有矩阵均由涉及恒等矩阵或 Pauli x，或 Pauli s1，矩阵的 2 x 2 块子矩阵组成。例如，对于情况 3)，矩阵 `U` 在左上角有 Pauli x 矩阵，并在右下角有二乘二恒等矩阵，`U=`

$\\begin{matrix} {|0} & 1 & 0 & {0|} \\\\ {|1} & 0 & 0 & {0|} \\\\ {|0} & 0 & 1 & {0|} \\\\ {|0} & 0 & 0 & {1|} \\\\ \\end{matrix}$

![方程](img/F000023si4.png)

如前所述，当该矩阵乘以表示输入量子位 `|y>` 的 `C⁴` 中的输入向量时，即 `(0 1 0 1)′`，结果为 `(1 0 0 1)′`，这是情况 3) 中的第二个输出。

图 17.2 为前面提到的四种情况中的每一种提供了量子电路。在情况 2) 和 3) 的电路中，有 `CNOT` 门。在情况 3) 和 4) 中，有单量子位 `NOT` 门。

![图 17.2 量子电路表示 Deutsch oracle.](img/F000023f17-02-9780443136979.jpg)

图 17.2 量子电路表示 Deutsch oracle。

## 17.3 Deutsch 问题的量子解
存在大量用于求解 Deutsch 问题的量子解；然而，它们都涉及 Deutsch oracle。也许最简单的解如 图 17.3 所示。这里，图示电路的实际输入都是相同的量子位 `|1>`。使用张量积得到输入 `|1> @ |1>=|11>`。参考该图，在对第一和第二量子位进行第一次 Hadamard 操作后，得到状态值 `|v1>=1/2 (|00>−|10>−|01>+|11>)`，这是输入所有可能组合的叠加，但不是纠缠的。确定 `|v1>` 的计算是涉及 Hadamard 变换的张量积：`(H|1>)@(H|1>)=1/2 (|0> −|1>)@ (|0>−|1>)=1/2 (|00>−|10>−|01>+|11>)`。

![图 17.3 Deutsch 算法.](img/F000023f17-03-9780443136979.jpg)

图 17.3 Deutsch 算法。




下一个状态值，在经过 oracle `U` 之后，给出量：`|v2>=1/2(|0 f(0)>−|1 f(1)>)−|0 1(+)f(0)>+|1 1(+)f(1)>`。现在如果 `f` 是常数，即 `f(0)=f(1)`，则 `|v2>=1/2 (|0>−|1>)(|f(0)>−|1(+)f(0)>)`。另一方面，如果 `f` 是平衡的，则 `f(0)=1(+)f(1)`；在这种情况下，`|v2>=1/2(|0>+|1>)(|f(0)>−|1(+)f(0>))`。最后，利用第一个量子比特上的 `Hadamard` 和第二个量子比特上的恒等变换得到的结果是 `|v3>=|1> (|f(0)>−|1(+)f(0>))` 当 `f` 为常数时出现。此外，`|v3>=|0> (|f(0)>−|1(+)f(0>))`，当 `f` 为平衡时。接下来测量第一个寄存器的内容时，当 `f` 为常数时得到 `|1>`。此外它对 `f` 平衡给出观测值 `|0>`。仅需一次循环执行即可获得此结果。

## 17.4 Deutsch-Jozsa 问题描述

该问题是最早具有量子解法优于经典解法的问题之一。该问题涉及函数 `f`，`f: {0, 1}^(*n*)→{0, 1}`，`n>1`，目标是确定函数是常数还是平衡。由于输出是单一值，常数意味着输出始终相同，无论输入值如何。平衡意味着输出对一半输入为零，对另一半输入为一。此外，保证这些是唯一的输出类型；不存在其他类型。问题是确定函数 `f` 是否为常数或平衡。量子解法仅使用一次求值。

为分析情况，假设输入连续使用 `2^(*n*)` 次以获得由 `2^(*n*)` 个零或一组成的输出字符串。对于 `2^(*n*)` 个不同的可能输入值，只有两种常数输出字符串；它们是全零或全一字符串。相应地，零和一混合数量的字符串有 `2^(2^(*n*))` 种可能。`![方程](img/F000023si5.png)` 其中只有部分字符串包含相等数量的零和一。对于 `f` 为平衡的情况，字符串长度的一半必须包含零，另一半必须包含一，顺序不限。由于输出字符串长度为 `2^(*n*)`，`![方程](img/F000023si6.png)` 由此数量的不同对象组成的排列可以是 `(2^(*n*))!` 中的一个。也就是说，可能的输出数量只有 `2^(*n*)` 阶乘。然而，对于平衡情况，输出字符串的一半或 `2^(*n* − 1)` 个值必须为零，另一半必须为一。`![方程](img/F000023si7.png)` 因此，平衡输出字符串的数量为 `(2^(*n*))!/[(2^(*n* − 1))! (2^(*n* − 1))!]`。`![方程](img/F000023si8.png)` `![方程](img/F000023si9.png)` 例如，如果 `n=3`，则仍然只有两个常数输出字符串，但平衡输出字符串有 `8!/[4! 4!]=70` 个。在任何情况下，如果所有输出字符串出现的可能性相等，则对于 `n=3`，得到常数字符串的概率为 `1/35`。随着 `n` 变大，该概率趋于零，但结果并不确定。要在经典方法中确定，必须检查前 `2^(*n* − 1)` 个输出字符串。`![方程](img/F000023si10.png)` 在此之后，并且如果它们全部具有相同值，则下一个 `2^(*n* − 1) + 1` 字符串将确定 `f` 是否为常数或平衡。`![方程](img/F000023si11.png)`

### 示例 17.1

使用 `n=2`，将说明 Deutsch-Jozsa 问题。在此情况下，输入由两个张量积量子比特组成。但与这对输入量子比特对应的输出是一个量子比特，如 Deutsch 问题中所述。下方左列为所有可能的量子比特输入对。这些量子比特不使用 ket 表示法表示，输出字符串以列形式呈现。接下来的两列显示唯一可能的常数输出值；它们分别是长度为四的全零和全一输出字符串。最后六列显示平衡情况，输出字符串一半为零一半为一。输出字符串总数为 `2(2²)=16`，但仅显示相关部分。被省略的输出字符串具有非常数或非平衡的零和一数量。使用上文给出的公式，`n=2` 时平衡输出字符串的数量为 `(2²)!/[2! 2!]=4!/4=6`。

```
$\\begin{array}{lll} \\begin{array}{l} 00 \\\\ 01 \\\\ 10 \\\\ 11 \\\\ {INPUT} \\\\ \\end{array} & \\begin{array}{ll} 0 & 1 \\\\ 0 & 1 \\\\ 0 & 1 \\\\ 0 & 1 \\\\ {CONSTANT} & \\\\ \\end{array} & \\begin{array}{llllll} 0 & 0 & 0 & 1 & 1 & 1 \\\\ 1 & 1 & 0 & 1 & 0 & 0 \\\\ 1 & 0 & 1 & 0 & 1 & 0 \\\\ 0 & 1 & 1 & 0 & 0 & 1 \\\\ ˄ & & {BALANCED} & & & {˄.\\#} \\\\ \\end{array} \\\\ \\end{array}$
```

`![方程](img/F000023si12.png)`

## 17.5 Deutsch-Jozsa 问题的量子解法

使用量子电路求解 Deutsch-Jozsa 问题仅涉及一次查询。它一次性给出解。实现该解法的电路在 `图 17.4` 中给出。该解法与标准 Deutsh 问题非常相似。如图所示，输入由 `|0>@|0>@ …@|0>=|00… 0>` 组成，即 `n` 重张量的控制量子比特，以及一个 `|1>` 作为目标输入。经过 Hadamard 变换后，得到量子态 `|v1>`。该结果由 `|v1> = 1/2^((n+1)/2)| + + … + − >` 给出，`= 1/2^(n/2) sum, $\\sum\\limits_{x}$|x>@|−>`，对于 `x` 在 `{0,1}^(*n*)` 中 `|x>@|−>`。在下一步，在使用 oracle 之前，注意 `|x−>` 对于 oracle `U` 表现得像一个特征向量；确实，考虑量子比特对 `|x−>`。然后 `U|x−>=|x−(+) f(x)>=1/2^(1/2) [|x 0 (+) f(x)>−|x 1 (+) f(x)>]=1/2^(1/2) (−1)^(f(x)) |x|−>`。与该特征向量对应的特征值为 `1/2^(1/2) (−1)^(f(x))` (`Jozsa, 1994`)。

`![图 17.4 Deutsch-Jozsa 算法.](img/F000023f17-04-9780443136979.jpg)`

`图 17.4` Deutsch-Jozsa 算法。

在应用 oracle 之后，量子比特 `|v2>` 处，可得 `|v2>` 等于对于 `x` 在 `{0,1}^(*n*)` 中的和，`∑ 1/2^(n/2) [(−1)^(f(x)) |x>|−>]`。在求得 `|v3>` 之前，注意作用于 `x=|0>` 或 `|1>` 的单个 Hadamard 算符可写为 `H|x> = 1/2^(1/2) sum, ∑(−1)^(x z)|z>`，对于 `z` 在 `{0,1}` 中。当 `x` 是基态的张量积时，类似公式成立 `H@^n|x> = 1/2^(n/2) sum, ∑ (−1)^(<x,y>) |z>`，对于 `z` 在 `{0,1}^(*n*)` 中。这里，`<x, z>` 是模 2 的按位内积。

在量子比特 `|v3>` 处，这是对 `|x>` 应用 `n` 重 Hadamard 门并对 `|−>` 应用恒等变换之后。在此情况下，`|v3>` 等于对于 `x` 在 `{0,1}^(*n*)` 中 `1/2^(*n*) sum, ∑ [for z in {0,1}^(*n*), sum, ∑((−1)^(f(x)) (−1)^(<x,y>)|z>@|−>)]`。这些是最终输出量子比特。最后在控制量子比特 `|z>` 上按标准基进行测量。找到 `|z>=|0>` 的概率涉及振幅绝对值的平方。该概率为 `|for x in {0,1}^(*n*), 1/2^(*n*) sum ∑(−1)^(f(x)) |²`。对于 `f` 常数，求和概率为一。对于 `f` 平衡，由于部分和交替，得到零。在任何情况下，得到该结果仅需一次执行周期。

## 17.6 Grover 搜索问题

Grover 问题是一个无结构搜索问题，涉及正整数 `N=2^(*n*)` 个项目。该应用的底层希尔伯特空间为 `C^(*N*)`。例如，该搜索问题的典型结构为 `f: {0, 1}^(*n*)→{0, 1}`，并且假设只有一种输出实例为一；其余均为零。目标是找到项目 `x*`，即长度为 `n` 的字符串，使得 `f (x*)=1`。

### 示例 17.2



在这种情况下，Grover 问题是要在 `N=2³` 且 `f: {0, 1}³→{0, 1}` 的条件下找到数字六。以二进制表示，如果 `x*=110`，则 `f(x*)=1`，这就是所求的答案。否则，`f(x)=0`。可以认为，对于整数 `0` 到 `7` 的每个二进制表示，都附带一个标志，除了 `110` 之外的所有字符串都标记为零；它标记为一。下面按顺序给出这些字符串；通常情况并非如此；顺序可能是随机的。此外，通常每个字符串的长度为正整数 `n`。

$\\begin{matrix} 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 \\\\ 000 & 001 & 010 & 011 & 100 & 101 & 110 & 111 \\\\ 0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 \\\\ \\end{matrix}$

![方程](img/F000023si19.png)

有时用二进制数系统将张量 `|110>` 写成 `|6>` 很方便。

使用传统计算机，解决此问题需要 `N` 次查询。在所有情况下，这个数字都能保证找到标记为数字一的字符串。也就是说，需要搜索每一项才能找到解。这类似于知道一个人的电话号码并通过电话簿查找该号码的拥有者。当采用随机搜索程序解决此问题时，只需要大约 `N/2` 次查询。然而，使用量子算法（Grover, 1996），只需要 `N^(1/2)`![方程](img/F000023si20.png) 次查询即可确定标记为一的字符串。因此，如果 `N` 约为一百万，而不是使用暴力法，采用量子算法仅需一千次应用即可解决此搜索问题。如前所述，量子计算所能达到的最好情况是 `N^(1/2)`![方程](img/F000023si21.png) 量级的复杂度，而传统计算需要 `N` 量级的复杂度。Grover 算法表明该结果是尖锐的。

一般而言，量子计算被称为有界误差量子概率（`BQP`）计算。该计算类包括传统的 `P`，即在多项式时间内求解问题。它还包括一部分非确定性多项式（`NP`）计算，例如因子分解。`NP` 复杂度类是指可以在多项式时间内验证解，但解本身无法在多项式时间内找到。`BQP` 不包括 `NP`-hard 或 `NP`-complete 问题。`NP`-complete 包括 `NP` 以及可在多项式开销下转换为它的 `NP` 中的其他问题（Encyclopedia Britannica）。

## 17.7 Grover 搜索问题的解

Grover 算法以输入的均匀叠加开始。存在 `N` 个输入每个状态为 `|0>`，通过应用 Hadamard 变换得到 ${|{w > = 1/N^{1/2}}}\\sum\_{x = 0}^{N - 1}{|{x >}}$![方程](img/F000023si22.png)，其中再次 `x` 是由零或一组成的长度为 `n` 的字符串。以二进制表示，此字符串表示位于 \[0, N −1\] 中的整数 `k`。因此，这些张量各自的概率幅为 `1/N^(1/2)`![方程](img/F000023si23.png)。如果进行测量，其中一个张量以概率 `1/N` 被找到。这对每个 `x` 包括 `x*` 都成立。Grover 算法中的下一步是 oracle；它将否定 `x*` 的符号。

Grover 搜索问题的解涉及一个 oracle，`U[f]`![方程](img/F000023si24.png)，它是一个幺正门。该门具有翻转符号的性质，即当布尔函数 `f(x)=1` 时否定输入向量 `|x>`。因此，`U[f]|x> = (-1)^{f(x)}|x> = -|x>`![方程](img/F000023si25.png) 当 `f(x)=1` 时，且当 `f(x)=0` 时等于 `|x>`。目标是利用 oracle 找到唯一的 `x*` 使得 `f(x*)=1`。在矩阵表示中，一个 `N` by `N` 对角矩阵将表示 oracle。在主对角线上，该矩阵的所有元素均为一，除了对应于 `x*` 的位置，在那里会出现值减一。该矩阵的一次应用将条目 `x*` 相对于所有其他条目 `x` 进行反射。下一步是使用幅度放大，解释在 第 16.10 节 中并随后举例说明。它增加 `x*` 的概率幅，并以少量减小所有其他元素 `x` 的概率幅。这是因为 `N` 很大且所有条目的总概率必须等于一。

幅度放大算法涉及 `U[f]`![方程](img/F000023si26.png) 以及关于 `|w>` 的反射操作 `R[W] = (2|w><w| - I)`![方程](img/F000023si27.png)。这里 `I` 是恒等操作连同反射对，算子即 `R[W]`![方程](img/F000023si28.png) 在 `U[f]`![方程](img/F000023si29.png) 之前。这些两个操作按顺序执行将产生二维旋转。在 Grover 搜索算法中，两个向量 `|x*>` 和 `|w>` 张成 `C^(N)`![方程](img/F000023si30.png) 中的二维子空间。这两个向量几乎正交，因为内积 `<x*,w> = 1/N^(1/2)`![方程](img/F000023si31.png)，且 `N` 很大。可以通过从 `|w>` 中减去 `|x*>` 并重新缩放找到向量 `|s>`。由此得到 `|s>` 与 `|x*>` 正交。参见 图 17.5A。在此图中存在三个向量：沿垂直轴的是 `|x*>`，垂直于 `|x*>` 的是 `|s>`，在 `|s>` 上方角度为 `θ`![方程](img/F000023si32.png) 的是原始均匀叠加态 `|w>`。这里 `cos(θ)=<s, w>`。注意 `|w>` 由 `N = 2^(n)`![方程](img/F000023si33.png) 个态的和组成，每个态的概率幅为 `1/N^(1/2)`![方程](img/F000023si34.png)。此外，`|s>` 由 `2^(n)-1` 个态组成，每个态的概率幅为 `1/(N-1)^(1/2)`![方程](img/F000023si35.png)。因此，内积 `<s, w>` 等于 `1/[N^(1/2)(N-1)^(1/2)][2^(n)-1]`![方程](img/F000023si36.png)；这意味着 `cos(θ)=[(2^(n)-1)/2^(n)]^(1/2)`![方程](img/F000023si37.png)； consequently，`sin(θ)=[1/2^(n)]^(1/2)`。对于较大的 `n`，`θ`![方程](img/F000023si38.png) 约等于 `1/2^(n/2)`，因为小角度的正弦近似等于该角度。

![图 17.5 Grover 反射操作。(A) 起始位置，(B) 应用 Oracle，(C) 应用反射，(D) 再次应用 Oracle，(E) 再次应用反射，(F) 应用 Oracle，(G) 应用反射。](img/F000023f17-05-9780443136979.jpg)

图 17.5 Grover 反射操作。(A) 起始位置，(B) 应用 Oracle，(C) 应用反射，(D) 再次应用 Oracle，(E) 再次应用反射，(F) 应用 Oracle，(G) 应用反射。



先应用预言机 `U[f]` 到 `|w>` 上，通过关于 `|s>` 轴的反射会得到一个新的向量。所得向量 `U[f] |w>` 如 图 17.5B 所示，最后，利用实际的反射算子 `R[W]`![Equation](img/F000023si39.png) 对 `U[f]`![Equation](img/F000023si40.png) `|w>` 进行操作得到一个新的向量，`R[W]`![Equation](img/F000023si41.png) `U[f]`![Equation](img/F000023si42.png) `|w>`，它位于 `|s>` 轴上方 3 `θ`![Equation](img/F000023si43.png) 的角度处。角度之所以如此，是因为 `R[W]`![Equation](img/F000023si44.png) `U[f]`![Equation](img/F000023si45.png) `|w>` 相对于 `U[f]`![Equation](img/F000023si47.png) `|w>` 处于 2 `θ`![Equation](img/F000023si46.png) 上方的角度。参见 图 17.5C。接下来，图 17.5D 展示了 `U[f]`![Equation](img/F000023si48.png) `R[W]`![Equation](img/F000023si49.png) `U[f]`![Equation](img/F000023si50.png) `|w>`，其中再次应用了预言机。然后如果预言机后跟随反射算子 `R[W]`![Equation](img/F000023si51.png)，则得到一个新的向量 `R[W]`![Equation](img/F000023si52.png) `U[f]`![Equation](img/F000023si53.png) `R[W]`![Equation](img/F000023si54.png) `U[f]`![Equation](img/F000023si55.png) `|w>`=`[`R[W]`![Equation](img/F000023si56.png) `U[f]`]`![Equation](img/F000023si57.png) ² `|w>`，它与 `|s>` 轴的夹角为 5 `θ`![Equation](img/F000023si58.png)。这可以在 图 17.5E 中看到。下一个图表，图 17.5F，显示了沿 x 轴的反射，其后是另一个 `R[W]`![Equation](img/F000023si59.png) 的应用，如 图 17.5G 所示。这些向量的角度似乎以逆时针方式单调递增至九十度，即 `x*` 的位置。然而，需要停止条件。这确保应用足够多的算子对 `R[W]`![Equation](img/F000023si60.png) `U[f]`![Equation](img/F000023si61.png) 以使向量足够接近 `x*`，但又不会过度超出。

在 Grover 搜索算法中，两个向量 `|x*>` 和 `|s>` 是正交的并张成平面。从几何或使用内积，`<s, w>`=`cos(`θ`)` 且 `<x*, w>`=`sin (`θ`)`。如前所述，将反射对 `R[W]`![Equation](img/F000023si62.png) `U[f]`![Equation](img/F000023si63.png) 应用于初始叠加向量 `|w>` 可使所得向量逼近解向量 `|x*>`。令 `Ψ(r)`=`(`R[W]U[f]`)(r)`|w>`![Equation](img/F000023si64.png) 为采用 `r` 次反射对应用后得到的向量。因此，对于 `r`=0，`ψ[0]`![Equation](img/F000023si65.png) 与 `|s>` 成 `θ`![Equation](img/F000023si66.png) 的角度。对于 `r`=1，`ψ[1]`![Equation](img/F000023si67.png) 与 `|s>` 成 3 `θ`![Equation](img/F000023si68.png) 的角度。对于 `r`=2，`ψ[2]`![Equation](img/F000023si69.png) 与 `|s>` 成 5`θ` 的角度。现在的目标是找到 `r`，使得 `ψ[r]`![Equation](img/F000023si70.png) 与 `|s>` 成 (2 `r`+1)`θ` 的角度。再次从几何或使用内积，`<s, ψ[r]`![Equation](img/F000023si71.png)>`=`cos((2 `r` +1) `θ`)` 且 `<x*, ψ[r]`![Equation](img/F000023si72.png)>`=`sin ((2 `r` +1) `θ`)`。目标是使 `|ψ[r]`![Equation](img/F000023si73.png)>` 尽可能接近 `|x*>`，而发生的概率为 `sin²`![Equation](img/F000023si74.png) (2 `r` +1) `θ`)`。由于 `sin²`![Equation](img/F000023si75.png) (2 `r` +1) `θ`) 在 (2 `r` +1) `θ`=`π`/2 时最大，使用 `θ`=1/2^(n/2)![Equation](img/F000023si76.png)，如前所述，意味着 `r`=[(`π`/2) 2^(n/2)–1] / 2。因此 `r` 的值约为 (`π`/4) 2^(n/2)。要找到 `x`，`N^(1/2)` 次尝试就足够了。如果有 `k` 个值为 1 的项，则 (`N/k`)^(1/2) 次尝试就足够了。Grover 算法中使用的反射操作的量子电路图可以在 Nielsen 和 Chiangmai (2000) 中找到。

### 示例 17.3

Grover 问题在此情况下的解是找到数字 6，其中 `N`=2³，且 `f`: {0, 1}³→{0, 1}。在二进制表示中如果 `x*`=110，则 `f` (`x*`)=1，这就是所求的答案。假设输入状态 `|0>`，并且 Hadamard 变换提供均匀叠加态 ${|{w > = 1/8^{1/2}}}\\sum\_{x = 0}^{8 - 1}{|{x >}}$![Equation](img/F000023si77.png)。如前所述，每个 `x` 都是长度为三的字符串，如 示例 17.2 所示。下一步是找到状态 `|s>`，它与 `|x*>`=`|110>` 正交。如前所述，该向量是通过用 `|x*>` 减去 `|w>` 并重新缩放使所得向量长度为一而找到的。因此，${|{s > = 1/7^{1/2}}}\\sum\_{x = 0,not6}^{8 - 1}{|{x >}}$![Equation](img/F000023si78.png)。要应用的反射对 (`R[W]U[f]`)(r)![Equation](img/F000023si79.png) 的数量 `r` 由 `r`=π/42^(3/2)![Equation](img/F000023si80.png) 给出，约为 2。并且 `θ`=1/2^(n/2)，在此情况下约为 0.35。因此，对 `|w>` 第一次应用对 (`R[W]`![Equation](img/F000023si81.png) `U[f]`![Equation](img/F000023si82.png)) 将角度从 `|s>` 增加到 `R[W]`![Equation](img/F000023si83.png) `U[f]|w>`![Equation](img/F000023si84.png) 约为 0.95。这在 图 17.5 中示出。对该反射对的下一次应用提供了 `|s>` 与 (`R[W]U[f]`)²`|w>`![Equation](img/F000023si85.png) 之间的角度约为 1.75，这接近 π/2.#

## 17.8 从代数视角看 Shor 密码学问题

Shor 问题旨在破解传统公钥密码学中的代码。几乎所有密码学方法都利用一个非常大的整数 `N`，它生成为两个大素数的乘积。虽然 `N` 可能已知，但素因子 `p` 和 `q` 极难找到。Shor 问题的目标是找到这些素数 `p` 和 `q`，使得 `p` · `q`.= `N`。确定这些因子是所有传统密码学方法的关键点。它用于 RSA 以及所有当前方法，如 Diffie–Hellman 公钥和私钥交换，以及更先进的方法，包括椭圆曲线 (EC) 密码学。在所有这些情况下，都大量使用代数和数论来开发和描述这些密码学方法。然而，关键步骤始终是找到乘积为 `N` 的两个素数。通过传统方法对 `N` 进行因式分解涉及使用素数一次一个地进行实际乘法，`p` 从 2 到约 `N^(1/2)`![Equation](img/F000023si86.png)，大约需要 `N^(1/2)`![Equation](img/F000023si87.png) 步。当 `N` 由 `d` 个十进制数字表示时，难度等级在 `d` 上呈指数增长。涉及数域筛法的最佳已知数论方法提供了一个复杂度为 `d^(1/3)`![Equation](img/F000023si88.png) 的指数。Shor 算法的运行时间复杂度是 `d` 的多项式。



Shor 的贡献（Shor, 1997）主要在于将此因式分解问题转化为在循环群中寻找生成元周期的一个问题。周期的值也称为群的阶。在前一节中，循环群 `Z[n]`![Equation](img/F000023si89.png) 已在环绕信号的上下文中引入。现在，它将在介绍 Shor 周期性问题的方向上更正式地描述。以下内容刻意避免使用等价类，直到本节末尾描述划分为止。代数和数论背景将现在概述。从正整数 `N > 1` 开始，欧拉 totient 函数 `ϕ(N)` (Landau, 1966) 是介于 1 和 `N` 之间（含）且与 `N` 互质或相对素数的全部整数集合的基数。重要情况是当 `N` 是两个素数 `p` 和 `q` 的乘积时，即 `N = p·q`。欧拉 phi totient 集合将使用载体集描述，`Φ(N) = {n, such that n is an integer less than or equal to N, n > 0, gcd(n, N) = 1}`。通常，`gcd` 是最大公约数，且该集合由与 `N` 互质或互素的整数 `n` 组成。

重要的是，`Φ(N)` 中的元素集合在模 `N` 乘法下形成阿贝尔群型代数结构。以下呈现中称其为欧拉 totient 群。对于 `Φ(N)` 中的 `x` 和 `y`，`x·y` 也在 `Φ(N)` 中，因为 `gcd(x·y, N) = 1`，因此模 `N` 的乘法运算满足闭包。结合律和交换律源于整数的类似性质。数字 1 是 `Φ(N)` 中的单位元，且 `x` mod `N` 的乘法逆元是 `Φ(N)` 中的整数 `y`，使得 `x·y = 1 mod N`。逆元性质的证明依赖于 Bezout 引理 (Ore, 1948)。由 `ϕ(N)` 推导出的一个重要结果是 `Φ(N)` 的基数，即欧拉 totient 群的基数，是 `(p−1)(q−1)` 的乘积，其中 `p·q = N`，且 `p` 和 `q` 为素数。

### 示例 17.4
如果 `N = 14`，则载体集由 `Φ(14) = {1, 3, 5, 9, 11, 13}` 给出。注意 9 在 `Φ(14)` 中，因为同时整除 9 和 14 的最大整数是 1，而 8 不在此集合中，因为 `gcd(8, 14) = 2`。此外，说明阿贝尔乘法群结构，观察到 `9·3 mod 14 = 13`，因为 27 除以 14 的余数为 13。还有，`1/11 mod 14` 等同于求解问题 `11·? = 1 mod 14`，其中“？”必须在载体集 `Φ(14)` 中。解为 `1/11 = ? = 9`，因为 `9·11 = 99`，除以 14 后余数为 1。该阿贝尔群的单位元是 1。最后，`Φ(14)` 中元素的个数是 `(7−1)(2−1) = six`，这是 totient 函数的值。

所需且前面提到的循环群是 `Φ(N)` 的一个子群 `G[a]`![Equation](img/F000023si90.png)。循环群由欧拉 totient 群中的元素 `a` 生成。循环群在模 `N` 下是乘法的，由 `{1, a¹, a², …, a^(r)}` 组成。使 `a^(r) = 1`![Equation](img/F000023si91.png) 成立的最小正整数 `r` 最为重要，因为 `r` 称为 `a` 的周期，或循环子群的阶。值 `a` 称为循环群 `G[a]`![Equation](img/F000023si92.png) 的生成元。最无聊的情况是如果 `a = 1`，则默认周期为 `r = 0`。

### 示例 17.5
对于 `N = 15`，欧拉 totient 群 `Φ(15) = {1, 2, 4, 7, 8, 11, 13, 14}`。这是一个非常重要的例子，因为它首次被用于用量子技术实验性地求解 Shor 问题 (Vandersypen et al., 2001)。为说明周期性，令 `a = 4`，则 `G[4] = {1,4}`![Equation](img/F000023si93.png)，且 `a` 的周期为二，因为 `4² = 16`，但此值 mod 15 为 1，因为 16 除以 15 的余数为 1。考虑 `G[7] = {1, 7, 4, 13}`。在这种情况下，周期为四。它是 `Φ(15)` 的该子群中元素的个数。

为说明周期性，如余弦波或正弦波的图像，考虑函数 `f: Z[+] → G[a]`，对于 `Φ(N)` 中某个非单位元 `a`。这里，`Z[+]` 是所有非负整数，且 `f(n) = a^(n)`。绘制 `n` 与 `f(n)` 的关系图会很有用。

### 示例 17.6
再次参考 示例 17.5。这次使用 `f(n) = 7^(n)`。则 `f: Z[+] → G[7]`，在 `Φ(15)` 中，给出如下非负整数 `n` 在上方，对应的值 `f(n)` 在下方：

```
$\\begin{matrix} 0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9 & {10\\ldots} \\\\ 1 & 7 & 4 & 13 & 1 & 7 & 4 & 13 & 1 & 7 & {4.\\ldots} \\\\ \\end{matrix}$
```

![Equation](img/F000023si94.png)

在上图中，可以明显看出周期为四；即模式每四次重复一次并形成 `Z[+]` 的划分，从而产生四个等价类。

## 17.9 Shor 问题 的 解法
涉及整数因式分解的密码学问题由 Shor 用量子计算在多项式时间内解决。如前所述，这比传统解法快指数级。过程大致分为两个阶段：首先，类似于 Deutsch-Jozsa 算法，利用量子并行性和建设性干涉来确定函数的周期性，而不是看其是否平衡。接下来，使用 `QFT` 找到循环群生成元 `a` 的周期。从工程角度看，`QFT` 用于确定频率 = 1/周期。无论如何，正是后一个过程在使用 Shor 算法时产生了指数级加速。此外，实际上采用了量子相位估计与幺正操作。随机选择这些算子的本征值可导致确定所需的周期 `r`。

Shor 提出用于确定 `N` 的因子 `p` 或 `q` 的实际步骤总结如下。它们将以欧拉 totient 群 `Φ(N)` 的术语描述；因此，所有计算均在模 `N` 下进行，`N` 为非常大的正整数。另为设定密码学类型操作的背景，假设 `N = p·q`，其中 `p` 和 `q` 为素数。按顺序执行步骤：

1. 1) 选择 `(1, N)` 中的随机整数 `a`；幸运的猜测是该值不属于欧拉 totient 群 `Φ(N)`。
2. 2) 计算 `k = gcd(a, N)`；欧几里得算法是标准程序。
3. 3) 如果 `k` 不同于一，则它必须是 `p` 或 `q`，搜索结束，否则继续。
4. 4) 找到所选值 `a` 的周期 `r`，即找到循环群 `G[a]`![Equation](img/F000023si95.png) 的阶。
5. 5) 如果 `r` 为奇数，选择区间 `(1, N)` 中的不同元素 `a`，并从步骤 2) 的计算开始重复步骤，否则继续。
6. 6) 乘积 `(a^(r/2) + 1)·(a^(r/2) − 1) = 0`，因此 `N` 的因子是 `gcd(a^(r/2) + 1, N)` 和 `gcd(a^(r/2) − 1, N)`。这两个数可能是 `p` 和 `q`，但以低概率它们可能是 1 和 `N`。这些是因子。然而，如果后者发生，则从步骤 1) 开始并重复该过程。

### 示例 17.7
再次令 `N = 15`。注意在 示例 17.5 中欧拉 totient 群为 `Φ(15) = {1, 2, 4, 7, 8, 11, 13, 14}`。如前所述，幸运的猜测是不在 `Φ(15)` 中的数 `a`。Shor 的求 `N` 素因子步骤如下：

1. 1) 设 `a = 6`，选择一个不在 `Φ(15)` 中的数。
2. 2) 计算 `gcd(6, 15)`，
```
$\\begin{array}{ll} {{Euclids}{algorithm}:} & {15 \\ast = 6 \\ast \\times 2 + 3 \\ast} \\\\ & {6 \\ast = 3 \\ast \\times 2 + 0,{yields}\\gcd\\left( {6,15} \\right) = 3} \\\\ \\end{array}$
```
![Equation](img/F000023si96.png)



3. 3) 由于 `k=3`，过程以 `p=3` 结束，并且一个简单的计算总能给出另一个因子；在本例中，它是 `q=5`。

### 示例 17.8

再次令 `N=15`；欧拉的简化剩余系为 `Φ(15)`={1, 2, 4, 7, 8, 11, 13, 14}。

1. 1) 设 `a=4` 被选定。

2. 2) 计算 `gcd(4, 15)`，$\\begin{array}{ll} {\\text{Euclid}'s{algorithm}:} & {15 \\ast = 4 \\ast \\times 3 + 3 \\ast} \\\\ & {4 \\ast = 3 \\ast \\times 1 + 1,{yields}\\gcd\\left( {4,15} \\right) = 1} \\\\ \\end{array}$![Equation](img/F000023si97.png)

3. 3) 由于 `k=1`，必须按顺序继续。

4. 4) 为求 `a` 的周期，或循环群 `G[4]`={1, 4} 的阶，其为 `r=2`。

5. 5) 值 `r` 不是奇数。

6. 6) 乘积 `(4+1)·(4–1)=0`，因为 15 除以 15 的余数为零。在本例中，`gcd(4–1, 15)=3` 且 `gcd(4+1, 15)=5`。因此这些是 15 的素因子。

实现类似上述指定的算法的实际量子电路可在 Nielsen 和 Chiangmai (2000) 以及 贝厄雷加德（2002） 中找到。

## 17.10 椭圆曲线密码学

椭圆曲线密码学（`ECC`）采用伽罗瓦域，`F[q]`![Equation](img/F000023si98.png)，也称为有限域。这些域在下面描述。`ECC` 比其他现有的密码系统更高效、更安全。例如，在使用 `RSA` 的常规密钥信息传输中密钥为 3072 位，则使用 `ECC` 只需 256 位即可达到相同的[content]
3. 3) 由于 `k=3`，过程以 `p=3` 结束，并且一个简单的计算总能给出另一个因子；在本例中，它是 `q=5`。

### 示例 17.8

再次令 `N=15`；欧拉的简化剩余系为 `Φ(15)`={1, 2, 4, 7, 8, 11, 13, 14}。

1. 1) 设 `a=4` 被选定。

2. 2) 计算 `gcd(4, 15)`，$\\begin{array}{ll} {\\text{Euclid}'s{algorithm}:} & {15 \\ast = 4 \\ast \\times 3 + 3 \\ast} \\\\ & {4 \\ast = 3 \\ast \\times 1 + 1,{yields}\\gcd\\left( {4,15} \\right) = 1} \\\\ \\end{array}$![Equation](img/F000023si97.png)

3. 3) 由于 `k=1`，必须按顺序继续。

4. 4) 为求 `a` 的周期，或循环群 `G[4]`={1, 4} 的阶，其为 `r=2`。

5. 5) 值 `r` 不是奇数。

6. 6) 乘积 `(4+1)·(4–1)=0`，因为 15 除以 15 的余数为零。在本例中，`gcd(4–1, 15)=3` 且 `gcd(4+1, 15)=5`。因此这些是 15 的素因子。

实现类似上述指定的算法的实际量子电路可在 Nielsen 和 Chiangmai (2000) 以及 贝厄雷加德（2002） 中找到。

## 17.10 椭圆曲线密码学

椭圆曲线密码学（`ECC`）采用伽罗瓦域，`F[q]`![Equation](img/F000023si98.png)，也称为有限域。这些域在下面描述。`ECC` 比其他现有的密码系统更高效、更安全。例如，在使用 `RSA` 的常规密钥信息传输中密钥为 3072 位，则使用 `ECC` 只需 256 位即可达到相同的[content]
3. 3) 由于 `k=3`，过程以 `p=3` 结束，并且一个简单的计算总能给出另一个因子；在本例中，它是 `q=5`。

### 示例 17.8

再次令 `N=15`；欧拉的简化剩余系为 `Φ(15)`={1, 2, 4, 7, 8, 11, 13, 14}。

1. 1) 设 `a=4` 被选定。

2. 2) 计算 `gcd(4, 15)`，$\\begin{array}{ll} {\\text{Euclid}'s{algorithm}:} & {15 \\ast = 4 \\ast \\times 3 + 3 \\ast} \\\\ & {4 \\ast = 3 \\ast \\times 1 + 1,{yields}\\gcd\\left( {4,15} \\right) = 1} \\\\ \\end{array}$![Equation](img/F000023si97.png)

3. 3) 由于 `k=1`，必须按顺序继续。

4. 4) 为求 `a` 的周期，或循环群 `G[4]`={1, 4} 的阶，其为 `r=2`。

5. 5) 值 `r` 不是奇数。

6. 6) 乘积 `(4+1)·(4–1)=0`，因为 15 除以 15 的余数为零。在本例中，`gcd(4–1, 15)=3` 且 `gcd(4+1, 15)=5`。因此这些是 15 的素因子。

实现类似上述指定的算法的实际量子电路可在 Nielsen 和 Chiangmai (2000) 以及 贝厄雷加德（2002） 中找到。

## 17.10 椭圆曲线密码学

椭圆曲线密码学（`ECC`）采用伽罗瓦域，`F[q]`![Equation](img/F000023si98.png)，也称为有限域。这些域在下面描述。`ECC` 比其他现有的密码系统更高效、更安全。例如，在使用 `RSA` 的常规密钥信息传输中密钥为 3072 位，则使用 `ECC` 只需 256 位即可达到相同的[content]
3. 3) 由于 `k=3`，过程以 `p=3` 结束，并且一个简单的计算总能给出另一个因子；在本例中，它是 `q=5`。

### 示例 17.8

再次令 `N=15`；欧拉的简化剩余系为 `Φ(15)`={1, 2, 4, 7, 8, 11, 13, 14}。

1. 1) 设 `a=4` 被选定。

2. 2) 计算 `gcd(4, 15)`，$\\begin{array}{ll} {\\text{Euclid}'s{algorithm}:} & {15 \\ast = 4 \\ast \\times 3 + 3 \\ast} \\\\ & {4 \\ast = 3 \\ast \\times 1 + 1,{yields}\\gcd\\left( {4,15} \\right) = 1} \\\\ \\end{array}$![Equation](img/F000023si97.png)

3. 3) 由于 `k=1`，必须按顺序继续。

4. 4) 为求 `a` 的周期，或循环群 `G[4]`={1, 4} 的阶，其为 `r=2`。

5. 5) 值 `r` 不是奇数。

6. 6) 乘积 `(4+1)·(4–1)=0`，因为 15 除以 15 的余数为零。在本例中，`gcd(4–1, 15)=3` 且 `gcd(4+1, 15)=5`。因此这些是 15 的素因子。

实现类似上述指定的算法的实际量子电路可在 Nielsen 和 Chiangmai (2000) 以及 贝厄雷加德（2002） 中找到。

## 17.10 椭圆曲线密码学

椭圆曲线密码学（`ECC`）采用伽罗瓦域，`F[q]`![Equation](img/F000023si98.png)，也称为有限域。这些域在下面描述。`ECC` 比其他现有的密码系统更高效、更安全。例如，在使用 `RSA` 的常规密钥信息传输中密钥为 3072 位，则使用 `ECC` 只需 256 位即可达到相同的[content]
3. 3) 由于 `k=3`，过程以 `p=3` 结束，并且一个简单的计算总能给出另一个因子；在本例中，它是 `q=5`。

### 示例 17.8

再次令 `N=15`；欧拉的简化剩余系为 `Φ(15)`={1, 2, 4, 7, 8, 11, 13, 14}。

1. 1) 设 `a=4` 被选定。

2. 2) 计算 `gcd(4, 15)`，$\\begin{array}{ll} {\\text{Euclid}'s{algorithm}:} & {15 \\ast = 4 \\ast \\times 3 + 3 \\ast} \\\\ & {4 \\ast = 3 \\ast \\times 1 + 1,{yields}\\gcd\\left( {4,15} \\right) = 1} \\\\ \\end{array}$![Equation](img/F000023si97.png)

3. 3) 由于 `k=1`，必须按顺序继续。

4. 4) 为求 `a` 的周期，或循环群 `G[4]`={1, 4} 的阶，其为 `r=2`。

5. 5) 值 `r` 不是奇数。

6. 6) 乘积 `(4+1)·(4–1)=0`，因为 15 除以 15 的余数为零。在本例中，`gcd(4–1, 15)=3` 且 `gcd(4+1, 15)=5`。因此这些是 15 的素因子。

实现类似上述指定的算法的实际量子电路可在 Nielsen 和 Chiangmai (2000) 以及 贝厄雷加德（2002） 中找到。

## 17.10 椭圆曲线密码学

椭圆曲线密码学（`ECC`）采用伽罗瓦域，`F[q]`![Equation](img/F000023si98.png)，也称为有限域。这些域在下面描述。`ECC` 比其他现有的密码系统更高效、更安全。例如，在使用 `RSA` 的常规密钥信息传输中密钥为 3072 位，则使用 `ECC` 只需 256 位即可达到相同的[content]
3. 3) 由于 `k=3`，过程以 `p=3` 结束，另因子易得；本例为 `q=5`。

### 示例 17.8

再次令 `N=15`；欧拉剩余群 `Φ(15)`={1, 2, 4, 7, 8, 11, 13, 14}。

1. 1) 设 `a=4`。

2. 2) 计算 `gcd(4, 15)`，$\\begin{array}{ll} {\\text{Euclid}'s{algorithm}:} & {15 \\ast = 4 \\ast \\times 3 + 3 \\ast} \\\\ & {4 \\ast = 3 \\ast \\times 1 + 1,{yields}\\gcd\\left( {4,15} \\right) = 1} \\\\ \\end{array}$![Equation](img/F000023si97.png)

3. 3) 因 `k=1`，须继续。

4. 4) 求 `a` 的周期即循环群 `G[4]`={1, 4} 的阶，为 `r=2`。

5. 5) `r` 不是奇数。

6. 6) 乘积 `(4+1)·(4–1)=0`，因 15 除以 15 余零。本例 `gcd(4–1, 15)=3` 且 `gcd(4+1, 15)=5`，即 15 的素因子。

类似算法的实际量子电路见 Nielsen 和 Chiangmai (2000) 及 贝厄雷加德（2002）。

## 17.10 椭圆曲线密码学

椭圆曲线密码学（`ECC`）使用伽罗瓦域 `F[q]`![Equation](img/F000023si98.png)，即有限域。`ECC` 比现有密码系统更高效安全。如 `RSA` 用 3072 位密钥，`ECC` 只需 256 位即可同等安全。绝密传输中 `ECC` 密钥 384 位，`RSA` 需 7680 位。`ECC` 提升速度与安全。

`ECC` 广泛用于区块链加密货币，如 Bitcoin 和 Ethereum，使用 `secp256k1`（Cook, 2018）。区块链中会找到 EC 上的已知特殊点，称基点或本原元。点为 (`x`,`y`)，属于 `F[q]`![Equation](img/F000023si99.png) x `F[q]`![Equation](img/F000023si100.png)，即 `F[q]`![Equation](img/F000023si101.png) 的笛卡尔积。该点对由所有用户共享，称共享密钥或公钥。加密币中用 130 十六进制数字表示。所有加密应用均使用点加法和倍点。Bitcoin 和 Ethereum 的 `ECC` 使用 EC `y²=x³+7 mod p`，其中 `p=2²⁵⁶–232−977`。私钥为基点阶，整数 `n`，用 60 十六进制数字表示。私钥 `n` 与本原元相加 `n` 次，基于下述交换群加法规则，得 `n−1` 个 EC 点对。`n` 为用户专属隐藏数，即私钥。基点 (`x`, `y`) 共享，连同 `n` 倍基点，但 `n` 不共享。`n` 称密钥，不共享。`ECC` 基于底层伽罗瓦域，下述总结。

伽罗瓦域仅存在于 `q=p^(n)`，`p` 为素数，`n` 为正整数。记为 `GF(q)` 或 `F[q]`。域的阶为 `p^(n)`。特征为 `p`，在 `F[q]`![Equation](img/F000023si102.png) 中任一元素加 `p` 次为零。`F[q]`![Equation](img/F000023si103.png) 的非零元构成乘法循环群 `G[a]`![Equation](img/F000023si104.png)。循环群至少有一个生成元 `a`，其幂遍历 `G[a]`![Equation](img/F000023si105.png)。此时 `a` 亦称 `F[q]`![Equation](img/F000023si106.png) 的本原元。密码学中最重要域为素域 `F[p]` = `Z/pZ`![Equation](img/F000023si107.png)，但 `p` 很大。`F[p]`![Equation](img/F000023si108.png) 为模 `p` 整数，加乘为模 `p` 运算。`F[p]`![Equation](img/F000023si109.png) 元表示为载体集 {0,1,2,…, `p−1`} 的整数，实际为等价类。载体元为各类的代表。等价类构成 `Z` 的划分。另见 示例 17.6。

### 示例 17.9

考虑伽罗瓦域 `F[5]`![Equation](img/F000023si110.png)。载体集为 {0,1,2,3,4}，阶为 5。特征 `p=5`，如把 2 加五次得 10 mod 5 余 0。若 `a=3` 为循环群 `G[a]`![Equation](img/F000023si111.png) 的生成元，则 `a⁰=1`、`a¹=3`、`a²=4`、`a³=2`。`G[3]` 载体集为 {1,2,3,4}，`a=3` 为本原元。对 `F[5]`![Equation](img/F000023si112.png) 用 `G[3]`![Equation](img/F000023si113.png) 得整数的划分。图中上行为整数 `n`，下行为幂 `3^(n)`![Equation](img/F000023si114.png)：

$\\begin{matrix} {\\ldots - 2} & {- 1} & 0 & 1 & 2 & 3 & 4 & 5 & 6 & {7\\ldots} \\\\ {\\ldots 4} & 2 & 1 & 3 & 4 & 2 & 1 & 3 & 4 & {2\\ldots} \\\\ \\end{matrix}$

![Equation](img/F000023si115.png)

如上图，`3^(−1) mod 5` 意味着 `3·(?)=1 mod 5`，解为 `?=2`。故 −1 与 3、7 等同类，周期 `p−1=4`。

目前密码多在素 `p` 的 `F[p]`![Equation](img/F000023si116.png) 中进行，为完整起见，给出 `F[q]`![Equation](img/F000023si117.png) 的例子，其中 `q = p^(m)`![Equation](img/F000023si118.png)，`m>1`。此类域未来或被采用。

### 示例 17.10

本例伽罗瓦域载体集为四个元素，`F[4] = {0,1,a,a+1}`![Equation](img/F000023si119.png)。域结构所需六个运算见前文，算子名见 图 1.1。零元算子为 `ZERO` 元 0，`ONE` 为 1。二元运算 `ADD` 用 `+` 表示，`MULT` 用 `·` 表示，元素可并排。运算最好参考下表。表如矩阵，载体元位于每表顶行和左列。域为阿贝尔，两表关于主对角线对称。



$\\begin{array}{ll} \\left. \\\_\\\_ + \\\_\\\_\\\_ \\middle| \\\_\\\_\\\_ 0\\\_\\\_\\\_\\\_\\\_ 1\\\_\\\_\\\_\\\_\\\_ a\\\_\\\_\\\_ 1 + a\\\_\\\_ \\right.\\\_ & \\left. \\\_ \\cdot \\\_\\\_\\\_ \\middle| \\\_\\\_ 0\\\_\\\_\\\_\\\_\\\_ 1\\\_\\\_\\\_\\\_\\\_ a\\\_\\\_\\\_ 1 + a \\right.\\\_ \\\\ \\left. \\\_\\\_ 0\\\_\\\_\\\_ \\middle| \\\_\\\_\\\_ 0\\\_\\\_\\\_\\\_\\\_ 1\\\_\\\_\\\_\\\_\\\_ a\\\_\\\_\\\_\\\_ 1 + a\\\_\\\_ \\right.\\\_ & \\left. \\\_ 0\\\_\\\_\\\_ \\middle| \\\_\\\_ 0\\\_\\\_\\\_\\\_\\\_ 0\\\_\\\_\\\_\\\_\\\_ 0\\\_\\\_\\\_\\\_\\\_ 0\\\_\\\_ \\right.\\\_ \\\\ \\left. \\\_\\\_ 1\\\_\\\_\\\_ \\middle| \\\_\\\_\\\_ 1\\\_\\\_\\\_\\\_\\\_ 0\\\_\\\_\\\_ 1 + a\\\_\\\_\\\_ a\\\_\\\_ \\right.\\\_ & \\left. \\\_\\\_ 1\\\_\\\_\\\_ \\middle| \\\_\\\_ 0\\\_\\\_\\\_\\\_\\\_ 1\\\_\\\_\\\_\\\_\\\_ a\\\_\\\_\\\_ 1 + a \\right.\\\_ \\\\ \\left. \\\_\\\_ a\\\_\\\_\\\_ \\middle| \\\_\\\_\\\_ a\\\_\\\_\\\_ 1 + a\\\_\\\_\\\_ 0\\\_\\\_\\\_\\\_\\\_ 1\\\_\\\_ \\right.\\\_ & \\left. \\\_\\\_ a\\\_\\\_\\\_ \\middle| \\\_\\\_ 0\\\_\\\_\\\_\\\_\\\_ a\\\_\\\_\\\_ 1 + a\\\_\\\_\\\_ 1 \\right.\\\_ \\\\ \\left. \\\_ 1 + a\\\_ \\middle| \\\_ 1 + a\\\_\\\_\\\_ a\\\_\\\_\\\_\\\_\\\_ 1\\\_\\\_\\\_\\\_\\\_ 0\\\_\\\_ \\right.\\\_ & \\left. \\\_ 1 + a\\\_ \\middle| \\\_\\\_ 0\\\_\\\_\\\_ 1 + a\\\_\\\_\\\_ 1\\\_\\\_\\\_\\\_\\\_ a\\\_\\\_. \\right. \\\\ \\end{array}$

![方程](img/F000023si120.png)

例如，在加法表中，使用左列的底部条目和顶部的最右条目，显示 `(1+a)+(1+a)=0`。在乘法表中使用相同的条目可得 `(1+a)·(1+a)=a`。另一方面，`(1+ a)·(1+ a)=1+2 a+a²`，但根据同一张表 `a²=a+1`，所以 `(1+a)·(1+a)=2+3 a`；然而，`2=0`，根据加法表，`1+1=0`，且 `2 a=0`，来自同一张表；因此，`(1+a)·(1+a)=a`，如前所述。在描述一元运算之前，应提及 `F[4]` 的载体集为 `{0, 1, a, a+1}`。任何其他数字，如 `2` 或 `a²`，都可以被视为属于一个等价类，其中陪集代表元在载体集中。因此，不使用表示陪集的括号 `[]`，我们直接令 `2=0` 且 `a²=a+1`。

一元运算再次由这些表得出。对于 MINUS，使用符号−。从加法表来看，要找到 `−x`，先在左列中找到 `x`。然后使用包含值 `x` 的行，在该行中找到值 `0`。现在，包含该零的列，其最顶部的条目也是 `−x` 的值。例如，`−a=a`。换句话说，`−a` 是加到 `a` 上得到零的数。因此在加法表中找到左列中的 `a`，在包含 `a` 的行中应找到数字零。在找到零元素的列中，使用顶部元素可知 `−a=a`。最后一个一元运算是部分运算；它是 INV，用 `/` 或 `(.)^(−1)` 等表示。再次使用乘法表，但这次是为了找到 `1/x=x^(−1)`，其中 `x` 不为零。使用左列找到 `x`，然后在该行中找到值 `1`。解可通过包含该 1 的列的顶部值找到。例如，`1/a=1+a`。不要忘记 `a^(−1)` 表示 `a·(?)=1`；确实，`a·(1+a)=a+a²=a+1+a=1`。所有等式恒等式都成立。对于域结构，一些恒等式已在前面举例说明，并且由于该域是有限的，每个恒等式都可以轻松验证。

### 示例 17.11

参考前面的例子，使用 `F[4]`，所有非零元素构成一个与 `Z[3]` 同构的循环群。这里，`G[a]={1, a, 1+a}={1, a, a²}`。

## 17.11 有限域上椭圆曲线的 MSA

`EC` 在本文的多个章节中有所介绍。底层域结构为复数域、实数域以及有理数域。此外，它们还在射影空间中进行了描述。而且，已证明曲线上的某些点可用于在指定的加法、减法和零运算下生成阿贝尔群。这一事实说明了阿贝尔簇的概念，其中群在代数上被描述，尽管运算是由几何考虑所驱动的。此外，在附录 A.3 中已证明结合律对 `EC` 群结构成立。此外，无穷远点 `∞`![方程](img/F000023si121.png) 是群中的单位元。因此，`∞`![方程](img/F000023si122.png)+`(x, y)`=`(x, y)`+`∞`![方程](img/F000023si123.png)`=`(x, y)`。包含无穷远点使代数结构成为一个点集。`EC` 的载体集是一个包含 `∞`![方程](img/F000023si124.png) 的交换群结构，而底层域的载体集是一个有限域。现在，`EC` 将在伽罗瓦域结构内进行说明，从一个例子开始。

### 示例 17.12

考虑 `EC`：`y²=x³+2x+12`，在伽罗瓦域 `F[17]`![方程](img/F000023si125.png) 上。此例的目标仅在于说明如何在该曲线上找到一个点对。所找到的点可以作为基点并在密码学应用中用作共享密钥。例如，若 `x=16`，则代入 `EC` 得 `y²=4096+32+12=4140`。由于底层域为 mod 17，数字 4140 必须映射到域的载体集 `{0, 1, 2, …, 16}` 中的一个数。该集合中的元素也称为陪集代表元。也就是说，4140 必须除以 17 并找到最小的非负余数。通常，计算通过欧几里得算法进行：`4140=17·243+9`。因此，余数是所需数字 9，所以 `y²=9`。相应地，该曲线上有两个对应的点对：`(16, 3)` 和 `(16,−3)`。

本节始终采用短 Weierstrass 标准形式。这意味着 `EC` 的最一般形式始终为 `y²=x³+ax+b`，其中 `a` 和 `b` 在 `F[q]`![方程](img/F000023si126.png) 中。没有更一般形式的原因是以下所用域的特征大于 3。`F[q]`![方程](img/F000023si127.png) 的特征是数字 1 必须加到自身多少次才能得到零的最小次数。如果不存在这样的数，则特征定义为零。注意，从 示例 17.10 可知，在 `F[4]`![方程](img/F000023si128.png) 中，特征为 2。此外，实数域 `R` 的特征为零。

此外，`EC` 必须满足方程 `4a³+27b²` 不为零。这保证了 `EC` 不是奇异的，即没有尖点，因此曲线是光滑的。对于 `EC`，偏导数不应同时等于零。此外，曲线应是简单的，即它不与自身相交。不同 `EC` 的插图见于 图 17.6。如图所示，本质上存在两种类型的 `EC`；共同特征是曲线关于 x 轴对称。此外，所有曲线都在一处或三处与 x 轴相交。插图，不好的曲线没有线段。

![图 17.6 椭圆曲线类型。](img/F000023f17-06-9780443136979.jpg)

图 17.6 椭圆曲线类型。



## 椭圆曲线点运算

虽然 `ECC` 的阿贝尔群结构和群运算是最重要的，但在 `ECC` 中有两种在应用中占主导地位的运算。这些是点或弦加法和点倍加运算。两种方法都源于使用基本微积分技术来描述几何方法。对于点加法，使用两个点 `(x1, y1)` 和 `(x2, y2)`，两者都在 `EC` 上并由 `EC` 上的一条直线非垂直线连接。然后，第三个点 `(x3, −y3)` 位于同一条直线上，并且也在 `EC` 上。当该点关于 x 轴反射时，结果 `(x3, y3)` 被称为前两个点的点加法。接下来，点上的倍加运算是通过找到 `EC` 上一点 `(x1, y1)` 的一条非垂直切线来实现的。该线将与 `EC` 相交于一点，其关于 x 轴的反射产生 `(x3, y3)`。结果称为原切点的倍加。点加法和倍加运算在附录 A.3 中有详细图形描述。现在这些运算可从基本微积分中得出，并相对于 `EC` 的短 Weierstrass 标准形式 `y²=x³+ax+b` 在代数上给出。

对于弦加法或两点加法：
* 斜率为 `s=(y2−y1)/(x2−x1)`。
* x 坐标为 `x3=s²−x1−x2`。
* y 坐标为 `y3=s(x1−x3)−y1`。

对于倍加或双切线方法：
* 斜率为 `s=(3x1²+a)/(2y1)`。
* x 坐标为 `x3=s²−x1−x1`。
* y 坐标为 `y3=s(x1−x3)−y1`。

一个示例将说明这些方程的使用。

### 示例 17.13

考虑 `EC` `y²=x³+6x+2` 在 `F[7]` 上。这里，`a=6`，且 `b=2`。首先，注意 `4a³+27b²=864+108=972`。现在将该数量除以 7 并保留最小非负余数得到 `F[7]` 中的 6，因此它不为零，且 `EC` 不是奇异的。首先将采用两点弦方法。使用 `(0, 3)` 和 `(1, 3)` 作为要相加的两个不同的点对。这些点在 `EC` 上。使用 `(0, 3)` 并代入 `EC` 可知 `y²=2`。该平方有解 `y=3`，以及 `y=4`，因为将两者平方都得到 2，从而提供载体集 `F[7]` ![方程](img/F000023si129.png) 中的唯一数字。在任何情况下，使用这两个点，即 `(0, 3)` 和 `(1, 3)`，得到斜率 `s=0`，`x3=−1=6`，`y3=−3`。因此，点加法得到 `(6, −3)`，该点在曲线上。代入 `EC` 得到 `(−3)²=2`，且 `y²=6³+6·6+2=216+36+2=254=36·7+4=2`。接下来，将使用 `EC` 上的点 `(2, 1)` 说明切线倍加方法。快速代入 `EC` 可知 `1²=2³+6·2+2=22=1`。斜率为 `s=(3·2²+6)/(2)=9=2`。因此，x 坐标为 `x3=2²−2−2=0`。y 坐标为 `y3=2(2−0)−1=3`。因此，新的点为 `(0, 3)`。如前所述，该点在 `EC` 上。此示例中的 `EC` 如 图 17.6B 所示。这里，点加法和切点倍加的相应过程大致以图形方式说明。

在一般情况下，其中 `EC` 为 `y²=x³+ax+b`，接下来将描述一些未被上述方程涵盖的代数计算。对于点加法，使用两个点 `(x1, y1)` 和 `(x2, y2)` 由一条直线连接，该直线在 `EC` 上为垂直线，结果为无穷远处的单位元 `∞` ![方程](img/F000023si130.png)。这也可以看出，因为在这种情况下，`(x2, y2)=−(x1, y1)=(x2, −y2)`，导致单位元，第三个点 `(x3, y3)` 为 `∞` ![方程](img/F000023si131.png)。对于切线倍加方法也是如此：如果切线是垂直的，第三个点为 `∞` ![方程](img/F000023si132.png)。最后，如前所述，当点 `∞` ![方程](img/F000023si133.png) 加到 `EC` 上的任何其他点 `z` 上，包括其自身，结果为 `z`。

### 示例 17.14

再次考虑 `EC` `y²=x³+6x+2` 在 `F[7]` 上。参考 图 17.6B 给出的图表。在该图表中，两个点 `(1, 3)` 和 `(1, −3)=−(1, 3)=(1, 4)` 被说明，并且穿过这两个点的垂直线得到点 `∞` ![方程](img/F000023si134.png)。

对于具有伽罗瓦域 `F[p]` ![方程](img/F000023si135.png) 的 `EC` `E`，元素形成一个阿贝尔群。群的阶，即其基数 `#E`，必须被精确知道，在 `ECC` 中就是这种情况。然而，一般情况下，模 `p` 上的 Hasse 定理为 `#E` 提供了界限（Cassels, 1991）。这些是下界和上界；具体来说，`p+1−2p^(1/2)` ![方程](img/F000023si136.png) 小于或等于 `#E`，而 `#E` 又小于或等于 `p+1+2p^(1/2)` ![方程](img/F000023si137.png)。这些界限将通过一个示例来说明。

### 示例 17.15

考虑 `EC` `E: y²=x³+1`，使用伽罗瓦域 `F[11]` ![方程](img/F000023si138.png)。由于 `p=11`，Hasse 定理表明 `E` 的基数 `#E` 是位于区间 `[11+1−2·11^(1/2), 11+1+2·11^(1/2)]=[5.4, 18.6]` 中的整数。对于该曲线，载体集为 `E={∞` ![方程](img/F000023si139.png)`, (10, 0), (0,10), (0, 1), (9, 2), (9,9), (6, 3), (6, 8), (8,4), (8, 7), (3, 5), (3, 6)}`。实际基数为 `#E=12`。为了验证点 `(0, 10)`，即验证该点是否在 `E` 中，注意当 `x=0` 时 `y²=1`。如果 `y=10`，`y²=100`，并且当该数除以 11 时，最小的正余数为 1；注意 `−10=1`。

回到 `ECC`，称为 `ECDLP` 的离散对数问题利用具有本原元素 `a` 的 `EC`，即 `EC` 上的点对 `(x, y)`。该元素使用点加法和切线倍加运算生成 `EC` 上的所有点。特别地，点 `t=c+c+…+c` 是 `EC` 上 `n` 次跳跃。起始点 `c` 是公钥 `c`，是 `EC` 上的点对。整数 `n` 是秘密或私钥；它是整数且未知。然而，`n` 与 `c` 的乘积，即 `t`，为所有用户所知。在区块链等实际应用中，使用的大素数非常大，如前所述。`E` 的载体集的基数 `#E` 非常大，`n` 也是如此。由于 `n` 仅为私有用户所知，值 `n·c` 可使用下面指定的算法有效地求出。然而，已知 `c` 和 `n·c`，几乎不可能找到 `n`。如 第 17.9 节 中所述量子计算机的使用使破解代码变得更简单。

快速算法来求 `n·c` 需要正整数 `n` 的二进制表示。这里，最左边的位是最重要的且为 1。从下一个最重要的位开始并工作到最低有效位，如果出现 1，则首先对 `c` 执行倍加切线运算；然后随后执行两点加法运算。如果二进制表示中出现 0，则仅采用倍加切线运算。一个示例将说明该方法。

### 示例 17.16

由于 `n` 为私有用户所知，`n·c` 可由上述算法确定。这里假设 `n=1·2⁵+1·2⁴+1·2¹+1=51`，且其二进制表示为 `(1 1 0 0 1 1)`。从 `EC` 上的点对 `c` 开始，倍加得到 `2·c`，随后点加法得到 `3·c`。下一个二进制数字为零，因此仅使用倍加，得到 `6·c`。再次，下一个数字为倍加，因此结果为 `12·c`。下一个数字为一，因此必须执行两个 `EC` 运算。首先倍加得到 `24·c`，随后点加法得到 `25·c`。最后一位为一，因此倍加提供 `50·c`，点加法给出最终结果 `51·c`。

## 17.12 Diffie–Hellman EEC 密钥交换



# EC Diffie–Hellman 密钥交换
EC Diffie–Hellman 密钥交换接下来进行描述。它由两个阶段组成：设置和交换。对于设置，有两个用户，需要 ECC 的参数。这些是 `a`、`b`、`p`，以及本原点对 `c=(x, y)`。在第二阶段，双方 1 和 2 就 EC 和 `p` 达成一致。方 1 选择一个随机数作为 {2, 3, …`#E` −1} 中的私钥，称为 `d`。方 1 计算 `D=d·c=(x1,y1)`。方 2 也随机找到一个数 `f` 在 {2, 3, …`#E` −1} 中并计算 `F=f·c=(x2,y2)`；他们交换公开已知的数值 `D` 和 `F`。然而，在接收后双方都用其秘密数相乘，并得到 `R=d·F=f·D`。值 `R` 是私有的，并可借助此地址以及哈希技术进行通信。哈希技术使用 `h` 将任意长度的签名型字符串映射为长度为 `m` 的大固定大小二进制字符串。这里，`h: {0, 1}*→{0, 1}^(*m*)`。它是一个单向函数，即已知原始字符串，使用算法可找到固定长度的二进制字符串。然而，使用二进制字符串几乎不可能恢复签名（Dorey et al., 2016）。

## References
*   Beauregard, 2002 Beauregard S. *使用 2n+3 个量子比特的 Shor 算法电路* Cornell U 2002;.
*   Cassels, 1991 Cassels J. *椭圆曲线讲义*。  *伦敦数学学会学生教材*。 24 Cambridge University Press 1991;.
*   Cook, 2018 Cook, J., 2018. 两个椭圆曲线的故事。Elliptic curves secp256k1 and secp256r1, Internet.
*   Dorey et al., 2016 Dorey K, et al. TLS 中持久的 Diffie-Hellman 后门。 *Cryptology* 2016;.
*   Grover, 1996 Grover L. *数据库搜索的快速量子力学算法* Proc 28th Annual ACM Meeting 1996;.
*   Jozsa, 1994 Jozsa R. 混合量子态的保真度。 *J Mod Opt.* 1994;41.
*   Landau, 1966 Landau E., 1966. 分析基础, 4th ed. Chelsea.
*   Nielsen and Chiangmai, 2000 Nielsen M, Chiangmai I. *量子计算和量子信息* Cambridge University Press 2000;.
*   Ore, 1988 Ore, O., 1948. 数论及其历史。Dover books.
*   Shor, 1997 Shor P. 量子上素数分解和离散对数的多项式时间算法。 *SIAM J Comput.* 1997;:26.
*   Vandersypen et al., 2001 Vandersypen, et al. *使用核磁共振实验实现 Shor 的量子因数分解算法* Nature 2001;.

## Further reading
*   Bennett et al., 1997 Bennett C, Bernstein E, Brassard G, Vazirani U. 量子计算的优势与劣势。 *SAIM J Comput*. 1997;26(5):1510–1523.
*   Landau and Lifshitz, 1996 Landau L, Lifshitz E. *量子力学-非相对论* Pergamon Press 1996;.

# 第 18 章 机器学习与数据挖掘
## Abstract
总结了量子机器学习应用中的若干最新应用。第二部分回顾了学习类型和数据结构的简要描述。下一节描述了 probably approximately correct 学习和 Vapnik-Chervonenkis (VC) 维。提供了若干涉及 sheltering 的 VC 维示例。以下各节描述了回归以及 k-最近邻方法并附有示例。支持向量机方法使用 Lagrange 乘子进行详细说明。下一节涉及核方法。第 18.11 节专门讨论有界矩阵以及 wraparound 有界矩阵。后者结构是与 wraparound 有界矩阵结构相似的 Banach \* 代数。主要目标是对卷积以及并行卷积方法进行深入描述。最后一节说明了卷积神经网络架构。

### Keywords
PAC learning; VC dimension; bound matrix; regression; Ridge regression; cozero set; Radial kernel; Lagrange multiplier; shatter

## 18.1 量子机器学习应用
使用绝热量子计算 (`AQC`) 和量子退火 (`QA`) 的机器学习采用监督和无监督方法直接从数据集发现模式和相关性。全局或亚全局优化技术加速了学习过程中的训练时间。描述量子在数据挖掘领域许多应用的优秀书籍是 Wittek (2014) 的文本。该文本在说明量子与数据挖掘的接口方面早于其时代。现在机器学习环境中许多更多应用采用量子门型计算机以及绝热计算机。下面将描述其中若干应用。
人脸模式是通过 `QA` 过程获得的 (O’Malley et al., 2018)。此外，更近期的，使用量子模拟器进行面部表情识别的研究也已开展 (Mengoni, 2021)。在此研究中，采用了若干机器学习技术。量子干涉被用来执行类似于 k-最近邻 (`KNN`) 分类算法的分类。在此研究中，图像首先使用 `R`² 中的 68 个点元组 (`x`, `y`) 进行识别![Equation](img/F000163si1.png`)。随后进行三角剖分程序和图论方法，导致邻接矩阵。三角化程序用于提供非完全的网格图，同时不损害信息含量。随后，量子态通过将邻接向量中的元组编码为量子态的振幅来定义。该工作的结论是，当使用完全图时，经典识别方法提供了更好的结果。然而，当采用网格图时，量子分类器产生了可比较的结果。
现代汽车公司与 Ion Q 量子合作用于自动驾驶汽车 (IonQ Staff, 2023)。另请参阅由 IonQ 开发的离子阱技术，描述于 第 6.7 节。过去的研究涉及量子计算机在建模电池性能以改善自动驾驶汽车使用方面的应用。目前，量子计算用于增强自动驾驶汽车的安全性和人机工程学方面。具体目标涉及盲点警告、紧急制动、车道控制以及车内舒适度，以使旅行更加悠闲。
IonQ 为现代汽车的量子计算主要集中在两个领域：道路标志的图像识别和第二、目标检测。在前一种情况下，量子机器学习模拟器中使用了四十三种不同的道路标志。仅使用了 16 个量子比特；然而，这允许估计使用更多量子比特时图像识别将如何改善。关于目标检测也研究了容错程序。在这种情况下，量子计算机必须基于这些图像区分物体。图像中感知到的物体周围的框被用作图像分割程序。框被用于预测物体的位置。然而，若干框可能重叠且大小各异。下一个任务是在每个框内识别物体。



AQC 和 QA 方法用于分类应用以及玻尔兹曼机的训练。这些机器是一种类型的 `NN` (Liu 和 Rebentrost, 2018)。

一个分布式特征提取语音识别系统使用量子卷积神经网络 (`QCNNs`) 开发 (Yang 等, 2021)。采用了量子电路编码器以及量子特征提取器。还本地采用了循环 `NN` (`RNN`) 来确定最终识别结果。`QCNN` 模型在识别中显示出超过九十五%的准确率。该文章报告的结果略优于使用之前的集中式 `RNN` 系统。频谱图特征用作量子电路层的输入。正是由这个量子电路学习并编码语音模式。`QCNN` 的前端执行编码并将输入组织成二乘二的块，从而使量子电路能够处理数据。量子电路对数据进行处理后，进入解码过程。该过程涉及将量子比特投影到一组张成量子态中。

为量子机器学习应用创建大型数据集的工作在 Perrier 等 (2022) 中得到发展。`QDataSet` 由 52 个公开可用数据集组成，这些数据集源自涉及一到两个量子比特的模拟。`QDataSet` 中的一些数据包含噪声，而一些数据则没有噪声。每个数据集包含 10,000 个样本，可用于机器学习算法开发。具体而言，该数据集旨在用于诸如量子计算、量子控制、量子光谱学以及量子层析成像等机器学习应用。这些数据集在量子控制算法基准测试中具有特别重要的意义，同时也有助于解决涉及量子数据的约束优化问题。

## 18.2 学习类型和数据结构

机器学习利用各种数据类型。向量是最基本的数据结构之一。向量中的元组构成指定实体的属性记录值，以及可能的关联。例如，医生办公室中的每个患者可能都有一个相关向量。这里，对于患者 X，向量可能由身高、体重、血压、母亲血型、…、吸烟者等元组值组成。其他数据结构包括矩阵、图像、视频、列表、集合、树、图、字符串，以及由这些数据类型中的几种组成的宏结构。作为示例，自动驾驶车辆可能利用所有这些结构，其中自然语言字符串被转换为导航和引导规则。实时图像、声音和视频观测被发送到深度学习机器。这些经过处理，并将控制信号发送到适当的控制面。

实际观测转换为控制信号通常采用估计和分类技术。深度学习机器需要解决的一些直观描述的问题，最常见的是分类问题。特别是，二元分类涉及为 `y` 确定两个随机量之一的选择。在此应用中，假设存在标签以进行识别。随机量可能是位置，例如，将一组带标签的对象划分为或分离到两个隔离位置中的一个。在多分类中，需要对多个随机量进行选择。同样，将对象划分为多个部分是机器学习的关键应用。标记是机器学习中的重要问题。有时，标签可能很明确，有时可能不明确。在后一种情况下，具有这些标签的对象被移除，通常称为擦除。此外，有时标签包含更多信息，并且可以以有益的方式加以利用。回归是极其重要的机器学习工具。在这种情况下，利用某种先验模型来估计或检查观测结果，并用于确定异常值。不同类型机器学习的直观描述如下：

1. 在线学习通常由一对序列 (`x[i]`, `y[i]`) 组成，目标是在观察 `x` 值时实时估计 `y[i]`。这也称为顺序滤波。当给出这样一对序列以及 `y` 序列的过去值时，需要估计 `y[i-k]`；这称为顺序平滑。同样，如果需要估计未来值 `y[i+k]`，则称为顺序预测。存在缺失 `x` 数据的估计通常称为擦除估计、插值估计或存在缺失变量的估计。
2. 批量学习再次使用二元组对 (`x[i]`, `y[i]`)，其中 `y` 值需要估计，但 `x` 观测值通常预先组装在一个集合中。当这些 `x` 值用于模型构建时，这称为主动学习。如果存在两个相关性较强的 `x` 型观测集合，并且已进行可能的协方差偏移校正，则会产生协同训练。

## 18.3 概然近似正确学习和 Vapnik-Chervonenkis 维数

概然近似正确 (`PAC`) 学习 (Valiant, 1984) 涉及某个类中的函数或一组函数。它们被称为可学习，这意味着在有监督的随机样本上训练后，该函数可用于以低误差估计测试集。因此，当测试数据与训练数据具有相同分布时，泛化误差很小。一般来说，好的学习器将以高概率学习到对测试数据的接近近似。更正式地，设 `X` 为所有样本的集合，也称为实例空间。与 `X` 相关联的是所有标签的集合。待学习的函数是 `c: X→Y`，称为概念。此外，设 `H` 为所有概念的集合。假设样本 `S` 由大小为 `m` 的同分布独立随机变量组成，从分布 `D` 中抽取。目标是找到一个算法，产生 `H` 中的概念 `h`，也称为假设。基本思想是确定或最小化泛化误差 `R`，即 `h` 与 `c` 相差多远。该数量将取决于分布 `D`，以及确定 `h` 如何选择的样本 `S`。此外，它还取决于要学习的概念 `c`。这里，广义误差 `R` 定义为 `c` 与 `h` 不同的概率，即 `R=P(c is not equal to h)`。



# PAC 可学习性与 VC 维

概念类 `H` 被称为 PAC 可学习，当且仅当存在一种算法，对于 `X` 上的每个分布 `D`、 `H` 中的每个概念 `c`，以及所有小的量 `ϵ`![Equation](img/F000163si2.png) 和 `δ`![Equation](img/F000163si3.png) 在 \[0, 1\] 中，如下所述。然后概率 `P`（`R` 小于或等于 ![ent](img/epsi_1013.png)）大于或等于 1 −`δ`。这必须对所有 `m` 成立，`m` 大于或等于 1/![ent](img/epsi_1013.png)、1/`δ` 的多项式有序函数。此外，还考虑了使用 `X` 中的 `x` 和表示目标概念 `c` 的计算成本。Valiant 提出的[content]
# PAC 可学习性与 VC 维

概念类 `H` 被称为 PAC 可学习，当且仅当存在一种算法，对于 `X` 上的每个分布 `D`、 `H` 中的每个概念 `c`，以及所有小的量 `ϵ`![Equation](img/F000163si2.png) 和 `δ`![Equation](img/F000163si3.png) 在 \[0, 1\] 中，如下所述。然后概率 `P`（`R` 小于或等于 ![ent](img/epsi_1013.png)）大于或等于 1 −`δ`。这必须对所有 `m` 成立，`m` 大于或等于 1/![ent](img/epsi_1013.png)、1/`δ` 的多项式有序函数。此外，还考虑了使用 `X` 中的 `x` 和表示目标概念 `c` 的计算成本。Valiant 提出的[content]
# PAC 可学习性与 VC 维

概念类 `H` 被称为 PAC 可学习，当且仅当存在一种算法，对于 `X` 上的每个分布 `D`、 `H` 中的每个概念 `c`，以及所有小的量 `ϵ`![Equation](img/F000163si2.png) 和 `δ`![Equation](img/F000163si3.png) 在 \[0, 1\] 中，如下所述。然后概率 `P`（`R` 小于或等于 ![ent](img/epsi_1013.png)）大于或等于 1 −`δ`。这必须对所有 `m` 成立，`m` 大于或等于 1/![ent](img/epsi_1013.png)、1/`δ` 的多项式有序函数。此外，还考虑了使用 `X` 中的 `x` 和表示目标概念 `c` 的计算成本。Valiant 提出的[content]
# PAC 可学习性与 VC 维

概念类 `H` 被称为 PAC 可学习，当且仅当存在一种算法，对于 `X` 上的每个分布 `D`、 `H` 中的每个概念 `c`，以及所有小的量 `ϵ`![Equation](img/F000163si2.png) 和 `δ`![Equation](img/F000163si3.png) 在 \[0, 1\] 中，如下所述。然后概率 `P`（`R` 小于或等于 ![ent](img/epsi_1013.png)）大于或等于 1 −`δ`。这必须对所有 `m` 成立，`m` 大于或等于 1/![ent](img/epsi_1013.png)、1/`δ` 的多项式有序函数。此外，还考虑了使用 `X` 中的 `x` 和表示目标概念 `c` 的计算成本。Valiant 提出的[content]
# PAC 可学习性与 VC 维

概念类 `H` 被称为 PAC 可学习，当且仅当存在一种算法，对于 `X` 上的每个分布 `D`、 `H` 中的每个概念 `c`，以及所有小的量 `ϵ`![Equation](img/F000163si2.png) 和 `δ`![Equation](img/F000163si3.png) 在 \[0, 1\] 中，如下所述。然后概率 `P`（`R` 小于或等于 ![ent](img/epsi_1013.png)）大于或等于 1 −`δ`。这必须对所有 `m` 成立，`m` 大于或等于 1/![ent](img/epsi_1013.png)、1/`δ` 的多项式有序函数。此外，还考虑了使用 `X` 中的 `x` 和表示目标概念 `c` 的计算成本。Valiant 提出的[content]
测试



根据 Wittek (2014)，`VC` 维可能是无限的。 为了解释这一点，设点集为 `R²` 中 `x` 轴上的所有奇整数。 任意一点，例如 `x-y` 平面中的点 `(1, 0)`，将被 `sin(π/2 x)` 在 `x` 属于 `[0, 2)` 时所打散。 这里 `B[1]` 表示正弦曲线下方的点，而正弦曲线上方的点由 `B[0]` 表示。 为了得到奇整数中的所有单点集，使用 `A` 中的参数。 这里使用 $\\sum\_{n = - \\infty}^{\\infty}{|{\\sin{({\\pi/2 x})}}}$![Equation](img/F000163si14.png)|*χ*[\[2*n*, 2*n* + 2)]![Equation](img/F000163si15.png)。 为了得到所有相邻的奇点集，使用 $\\sum\_{n = - \\infty}^{\\infty}{|{\\sin{({\\pi/2 x})}}}$![Equation](img/F000163si16.png)|*χ*[\[2*n*, 2*n* + 4)]![Equation](img/F000163si17.png)。 为了得到包含每隔一个奇点的每两个点集，使用 $\\sum\_{n = - \\infty}^{\\infty}\\left\\lbrack {{|{\\sin\\left( {\\pi/2 x} \\right){|{\\chi\_{\\lbrack{2n,2n + 2})} +}}}}{|{\\sin\\left( {\\pi/2 x} \\right){|{\\chi\_{\\lbrack{2n + 4,2n + 6})} +}}}}} \\right\\rbrack$![Equation](img/F000163si18.png)。 如此等等。 这表明所有奇整数都被 `f` 打散，使用 `A` 中的参数。

在 Vapnik 引用的论文中，`VC` 维被用于预测分类模型中测试误差的上限。 这些界限涉及独立同分布的随机变量，且训练数据和测试数据具有相同的底层概率分布函数。

## 18.4 回归

Ridge 回归是一种最小二乘技术，主要用于变量被认为高度相关时。 在这种情况下，当使用 Ridge 回归而不是通常的最小二乘时，方差或最小二乘误差有时会更小。 在超定系统的通常线性最小二乘回归中，伪逆提供了解。 见 第 14.3 节，14.4，其中描述了偏等距。 在此方法中，观测到的 `k·1` 向量 `y` 被投影到 `k·n` 设计矩阵 `H` 上，其中 `k> n` 或 `k=n`，且为满秩。 期望形式为 `x = B y` 的估计量，其中模型方程为 `y = H x + u`，而 `u` 是由噪声或松弛变量组成的向量。 此外，假设对向量 `u` 一无所知，只是它被用来使方程自洽。 通过投影方法，或通过对最小二乘损失求微分，估计量为伪逆：`x = (H′H)^(−1) H′ y`。 撇号表示转置运算。 如果已知 `u` 的更多信息，可以采用更好的估计量。

当 `H` 的列相关时，由于多重共线性，逆可能不准确，这会影响矩阵 `H′H` 的条件数。 在这种情况下，通常使用 Ridge 回归。 它也是一个线性估计量； 这里：`x = (H′H + λ I)^(−1) H′ y`。

值 `λ > 0` 通常很小； 它是启发式确定的。 此外，单位矩阵 `I` 为 `n·n`。 一个简单的例子用于说明该技术。

### 示例 18.5

对于 `y = H x + u`，使用 `y = (1.1 1 0.8)′`，`u = (u[1] u[2] u[3])`，且 `H =`

$\\begin{matrix} {|1} & {1|} \\\\ {|1} & {.9|} \\\\ {|1} & {1|} \\\\ \\end{matrix}$

![Equation](img/F000163si19.png)

然后 `H′H`，`(H′H)^(−1)`，和 `(H′H)^(−1) H′` 分别如下给出：

$\\begin{matrix} \\begin{matrix} {|3} & {2.9|} \\\\ {|2.9} & {2.81|} \\\\ \\end{matrix} & \\begin{matrix} {|140.5} & {{- 145}|} \\\\ {|{- 145}} & {150|} \\\\ \\end{matrix} & \\begin{matrix} {|{- 4.5}} & 10 & {{- 4.5}|} \\\\ {|5} & {- 10} & {5|} \\\\ \\end{matrix} \\\\ \\end{matrix}$

![Equation](img/F000163si20.png)

线性最小二乘估计为 `x = (1.45 −0.5)`。 残差、松弛或噪声向量为 `u = y − H x = (1.1 1 0.8)′ − (.95 1 0.95)′ = (.6 0 −0.15)′`。

如果使用 `λ = 0.1` 的 Ridge 回归，仅为说明方法，则 `H′H + 0.1 I`，`(H′H + 0.1 I)^(−1)`，和 `(H′H + 0.1 I)^(−1) H′` 分别如下给出：

$\\begin{matrix} \\begin{matrix} {|3.1} & {2.9|} \\\\ {|2.9} & {2.91|} \\\\ \\end{matrix} & \\begin{matrix} {|4.76} & {{- 4.75}|} \\\\ {|{- 4.75}} & {5.07|} \\\\ \\end{matrix} & \\begin{matrix} {|.01} & .5 & {.01|} \\\\ {|.32} & {- .2} & {.32|} \\\\ \\end{matrix} \\\\ \\end{matrix}.$

![Equation](img/F000163si21.png)

Ridge 估计 `x = (.52 −0.18)`。 残差、松弛或噪声向量为 `u = y – H x = (1.1 1 0.8)′ – (.34 0.35 0.34)′ = (.75 0.65 0.46)′`。

在最后一个例子中，与常规最小二乘相比，岭回归表现不佳。 然而，正如许多机器学习学科一样，必须设置启发式参数。 在这种情况下，`λ` 的值可以一遍又一遍地改变。

接下来说明一个有趣的应用，当特征空间为区间 `[−1, 1]` 且回归涉及该区间内的多项式时。 使用伪逆形式的最小二乘估计量，观测数据为 `y = (x[1], x[2], …, x[n])′`。 在这种情况下，Vandermonde 矩阵 `V` 被用于伪逆构造，即 `H = V`，且 `x = (V′ V)^(−1) V′ y`，其中 `V =`

$\\begin{matrix} {|1} & {x\_{1}\\ldots} & {x\_{1}^{m}|} \\\\ {|1} & {x\_{2}\\ldots} & {x\_{2}^{m}|} \\\\ \\cdot & \\cdot & \\cdot \\\\ {|1} & {x\_{n}\\ldots} & {x\_{n}^{m}|} \\\\ \\end{matrix}$

![Equation](img/F000163si22.png)

Vandermonde 矩阵也在循环向量的上下文中出现在示例 8.21 中。 然而，在此回归应用中，Vandermonde 矩阵通常不稳定。 增加稳定性的流行解决方案是在 Vandermonde 矩阵中使用 Chebyshev 正交多项式。 在附录 A.7 中，Chebyshev 多项式被证明为一组正交多项式，因为它们是 Sturm-Liouville 微分方程的解。

## 18.5 K-最近邻分类

机器学习最基础的例子之一是 `KNN`，类似于第 2.1 节中描述的 `K-means` 方法。 `KNN` 也是分类和聚类的技术。 它通常用作批学习的例子。 该方法涉及设置和实现阶段。 为了使用 `KNN`，必须存在整数 `N > 0` 的元组对 `(x[i], y[i])`，并且目标是在观察 `x` 值数据集时实时估计 `y[i]`。 该数据集是预训练的，其标签 `y` 假定为分类且二值，取值为 `{0, 1}`。 值 `K = 1, 2, …, N` 事先选择。 它指的是数据集中用于对查询或测试值 `x` 的距离做出决策的点的数量。 距离函数也必须在实现前选择。 应选择一种范数，并且在随后的示例中将使用一范数距离。

该方法是计算所有 `N` 个点 `x[i]` 到 `x` 的距离。 然后按距离升序对这些距离以及相应的元组值进行排序。 接下来选择前 `K` 个条目。 分类是通过使用 `K` 个条目的标签的众数值来执行的。 该方法的一些实际方面如下。 通常 `K` 取为奇整数。 而且它通常远小于 `N`。 另外，通常会使用多个 `K` 值，并尝试找到最佳 `K`。 这里，度量可能涉及成功分类的条目数作为 `K` 的函数。 对于由两个元组组成的小问题，将未知测试点置于图的原点，数据集的元素在其周围，这很有用，可以制作可视化图。 这在 图 18.3 中有所说明。

![图 18.3 K-最近邻分类。](img/F000163f18-03-9780443136979.jpg)

图 18.3 K-最近邻分类。

### 示例 18.6



考虑 图 18.3 所示的数据。这里有 `N=6` 个数据点：标签为 0 的正方形和标签为 1 的三角形。原点处是待分类的项目 `x`。距离 `|x−x[*i*]|`，`i=1, 2, …, 6`，被计算并按从小到大的距离列出，同时给出其二元组向量表示。由于此情况下 `K=3`，仅检查排序表中的前三个条目以确定出现次数最多的标签。由于有两个 1 和一个 0，众数是 1。因此未知项被分类为三角形。误差在于，在 `K=3` 个最近距离中，只有其中一项未被归入已分类的条目中。

使用较小的 `K` 值会使 `KNN` 技术不稳定，即可能出现误分类。另一方面，更大的 `K` 值会因多数投票协议，即使用众数，而使方法更稳定。通常该方法先使用相对较小的 `K` 值进行，然后逐渐增大 `K` 的值。当与已分类项不同的项目数量变得过大时，这种增加就会停止。该方法很容易扩展到二元分类以外的分类。此外，该过程适用于 `n` 维的数据集，即每个向量中有 `n+1` 个元组。最后一个元组再次是一个分类标签。它可以是二元的、三元的等。

## 18.6 K 近邻回归

`KNN` 回归与 `KNN` 分类在许多方面不同。首先，它用于向量 (`x[*i*]`, `y[*i*]`)，其中标签 `y[*i*]` 可以取连续值，例如在 `R` 中。此外，首先假设数据集 {`x[*i*]`} 为实值且单调，`x[*i*]` < `x[*i* + 1]`![Equation](img/F000163si23.png)，对于 `i=1, 2, …, N`。而且，对于每个 `x[*i*]`![Equation](img/F000163si24.png)，关联一个正整数 `m[*i*]`![Equation](img/F000163si25.png)，即标签数。因此存在 (`x[i]`, `y[*i*[1]]`)![Equation](img/F000163si26.png)、(`x[*i*]`, `y[*i*[2]]`)![Equation](img/F000163si27.png)、…、(`x[*i*]`, `y[*i*[*m[*i*]]]`)![Equation](img/F000163si28.png) 向量。实际的回归过程相当于在数据集 {`x[*i*]`}![Equation](img/F000163si29.png) 上形成一个函数 `f`。它满足 `f` : {`x[*i*]`}→`R`![Equation](img/F000163si30.png)，其中使用经验均值估计量，$\\left. f \\right.\\hat{}\\left( x\_{i} \\right) = 1/K\\overset{K}{\\underset{j = 1}{\\sum^{}}}y\_{i\_{j}}$![Equation](img/F000163si31.png)。此外，在求和中使用的 `K` 个值 `y[*i*[*j*]]`![Equation](img/F000163si32.png) 使用某种度量或聚类算法彼此最接近。或者，为每个 `x[*i*]`![Equation](img/F000163si34.png) 选择一个名义的、测试值 `y[*i*]`![Equation](img/F000163si33.png)，并使用 `K` 个 `y[*i*[*j*]]`![Equation](img/F000163si35.png) 值在平均值中使用，所有这些值都最接近 `y[*i*]`![Equation](img/F000163si36.png)。

值 `K` 必须小于 `m[*i*]`![Equation](img/F000163si37.png)。在任何情况下，`K` 始终可以等于一，但在这种情况下回归会过拟合。 resulting function would be very good for the trained data, but not so good using different data. 一般来说，标签非常丰富，在这种情况下，`K` 可以设为所有 `m[*i*]`![Equation](img/F000163si38.png) 的最小值或更小。与分类 `KNN` 类似，使用不同的 `K` 值来确定最佳拟合函数。

### 示例 18.7

假设认为数据集 {`x[*i*]`}![Equation](img/F000163si39.png) 的标签大致遵循平方律路径，即 `f`(`x[*i*]`) = `y[*i*]` = `x[*i*]`²![Equation](img/F000163si40.png)。如果选择一个数据点，例如 `x[*i*]` = 1![Equation](img/F000163si41.png) 及其标签，向量为 (`x[*i*]`, `y[*i*[1]]`)![Equation](img/F000163si42.png)、(`x[*i*]`, `y[*i*[2]]`)![Equation](img/F000163si44.png)、…、(`x[*i*]`, `y[*i*[*m[*i*]]]`)![Equation](img/F000163si46.png)。假设这些向量为 (1, 1.3)、(1, 0.7)、(1, 0.3)、(1, 1.4)、(1, 1.2)。这里，`m[*i*]` = 5![Equation](img/F000163si47.png)，并且设 `K=3`。然后由于 `y[*i*]` = `x[*i*]`² = 1![Equation](img/F000163si48.png)，在此示例中必须像通常的 `KNN` 方法一样找到 1 与全部五个标签的距离。同样，只选择最近的三个。在这种情况下，三个向量为 (1, 1.3)、(1, 0.7) 和 (1, 1.2)。用于形成平均值的[content]
考虑 图 18.3 所示的数据。这里有 `N=6` 个数据点：标签为 0 的正方形和标签为 1 的三角形。原点处是待分类的项目 `x`。距离 `|x−x[*i*]|`，`i=1, 2, …, 6`，被计算并按从小到大的距离列出，同时给出其二元组向量表示。由于此情况下 `K=3`，仅检查排序表中的前三个条目以确定出现次数最多的标签。由于有两个 1 和一个 0，众数是 1。因此未知项被分类为三角形。误差在于，在 `K=3` 个最近距离中，只有其中一项未被归入已分类的条目中。

使用较小的 `K` 值会使 `KNN` 技术不稳定，即可能出现误分类。另一方面，更大的 `K` 值会因多数投票协议，即使用众数，而使方法更稳定。通常该方法先使用相对较小的 `K` 值进行，然后逐渐增大 `K` 的值。当与已分类项不同的项目数量变得过大时，这种增加就会停止。该方法很容易扩展到二元分类以外的分类。此外，该过程适用于 `n` 维的数据集，即每个向量中有 `n+1` 个元组。最后一个元组再次是一个分类标签。它可以是二元的、三元的等。

## 18.6 K 近邻回归

`KNN` 回归与 `KNN` 分类在许多方面不同。首先，它用于向量 (`x[*i*]`, `y[*i*]`)，其中标签 `y[*i*]` 可以取连续值，例如在 `R` 中。此外，首先假设数据集 {`x[*i*]`} 为实值且单调，`x[*i*]` < `x[*i* + 1]`![Equation](img/F000163si23.png)，对于 `i=1, 2, …, N`。而且，对于每个 `x[*i*]`![Equation](img/F000163si24.png)，关联一个正整数 `m[*i*]`![Equation](img/F000163si25.png)，即标签数。因此存在 (`x[i]`, `y[*i*[1]]`)![Equation](img/F000163si26.png)、(`x[*i*]`, `y[*i*[2]]`)![Equation](img/F000163si27.png)、…、(`x[*i*]`, `y[*i*[*m[*i*]]]`)![Equation](img/F000163si28.png) 向量。实际的回归过程相当于在数据集 {`x[*i*]`}![Equation](img/F000163si29.png) 上形成一个函数 `f`。它满足 `f` : {`x[*i*]`}→`R`![Equation](img/F000163si30.png)，其中使用经验均值估计量，$\\left. f \\right.\\hat{}\\left( x\_{i} \\right) = 1/K\\overset{K}{\\underset{j = 1}{\\sum^{}}}y\_{i\_{j}}$![Equation](img/F000163si31.png)。此外，在求和中使用的 `K` 个值 `y[*i*[*j*]]`![Equation](img/F000163si32.png) 使用某种度量或聚类算法彼此最接近。或者，为每个 `x[*i*]`![Equation](img/F000163si34.png) 选择一个名义的、测试值 `y[*i*]`![Equation](img/F000163si33.png)，并使用 `K` 个 `y[*i*[*j*]]`![Equation](img/F000163si35.png) 值在平均值中使用，所有这些值都最接近 `y[*i*]`![Equation](img/F000163si36.png)。

值 `K` 必须小于 `m[*i*]`![Equation](img/F000163si37.png)。在任何情况下，`K` 始终可以等于一，但在这种情况下回归会过拟合。 resulting function would be very good for the trained data, but not so good using different data. 一般来说，标签非常丰富，在这种情况下，`K` 可以设为所有 `m[*i*]`![Equation](img/F000163si38.png) 的最小值或更小。与分类 `KNN` 类似，使用不同的 `K` 值来确定最佳拟合函数。

### 示例 18.7

假设认为数据集 {`x[*i*]`}![Equation](img/F000163si39.png) 的标签大致遵循平方律路径，即 `f`(`x[*i*]`) = `y[*i*]` = `x[*i*]`²![Equation](img/F000163si40.png)。如果选择一个数据点，例如 `x[*i*]` = 1![Equation](img/F000163si41.png) 及其标签，向量为 (`x[*i*]`, `y[*i*[1]]`)![Equation](img/F000163si42.png)、(`x[*i*]`, `y[*i*[2]]`)![Equation](img/F000163si44.png)、…、(`x[*i*]`, `y[*i*[*m[*i*]]]`)![Equation](img/F000163si46.png)。假设这些向量为 (1, 1.3)、(1, 0.7)、(1, 0.3)、(1, 1.4)、(1, 1.2)。这里，`m[*i*]` = 5![Equation](img/F000163si47.png)，并且设 `K=3`。然后由于 `y[*i*]` = `x[*i*]`² = 1![Equation](img/F000163si48.png)，在此示例中必须像通常的 `KNN` 方法一样找到 1 与全部五个标签的距离。同样，只选择最近的三个。在这种情况下，三个向量为 (1, 1.3)、(1, 0.7) 和 (1, 1.2)。用于形成平均值的



本文中还给出了涉及质心量子位和数据量子位的张量积。还涉及一个辅助量子位 `|0>`。它们以 `|0 Ψϕ>` 的顺序输入电路。对辅助量子位应用 `Hadamard` 门，从而得到 `1/2^(1/2)` `[|0 Ψϕ> + |1 Ψϕ>]`。随后使用 `controlled swap` 门将每个状态分配到其最近的簇。结论是，经典方法和量子方法之间取得了相当的结果。然而，量子系统的执行时间更少。

## 18.8 支持向量分类器

支持向量分类 (`SVC`) 是一种二元分类过程，可扩展到多类分类。用机器语言来说，训练集由 `n` 对向量组成：{(`v[1]`, `y[1]`), (`v[2]`, `y[2]`), …, (`v[*n*]`, `y[*n*]`)}, 其中 `v[*i*]` 在 `H=R^(*N*)` 中，而 `y[*i*]` 在 {−1, 1} 中。目标是通过找到线性决策超平面 `A` 以及一个间隔来对 `v[*i*]` 进行分类。从技术上讲，间隔由一对超平面组成，每个超平面都与 `A` 平行并且与 `A` 等距。这些间隔也称为沟槽或路缘。此外，它们之间的区域被认为是街道，`A` 为中心线。位于路缘上的点称为支持向量，这也是 SPV 机器得名的方式。SPV 机器通常被称为最大间隔分类器，通常在数据可分离时。另一种名称是硬间隔分类器。软间隔分类器允许出现一些误分类类型的错误。这是因为它们采用交叉验证。这导致整体分类更好。

数学上，仿射分类超平面为 `A=min(|<w, v[*i*]>+b|)`，其中 `i=1, 2, …, n`。令 `y[*i*]=1` 当且仅当 `y[*i*]` 在 `A^+`= `{v[*i*]![方程](img/F000163si50.png) 在 H 中，使得 <w, v[*i*]![方程](img/F000163si51.png)>+b 大于或等于零}` 中。同样地，令 `y[*i*]![方程](img/F000163si52.png)` 等于 −1，当 `y[*i*]![方程](img/F000163si53.png)` 在 `A^-`![方程](img/F000163si54.png)`={v[*i*]![方程](img/F000163si55.png) 在 H 中，使得 <w, v[*i*]![方程](img/F000163si56.png)>+b 小于零}` 中时。在可分离的情况下可以采用归一化。假设缩放已调整并且归一化在以下进行。回想一下 `A={v in H, such that <w, v>+b=0}`。现在两个沟槽，即与 `A` 相距一个单位的平行仿射空间，由以下给出：`A^+`![方程](img/F000163si57.png)`={v in H, such that <w, v>+b=1}` 和 `A^-`![方程](img/F000163si58.png)`={v in H, such that <w, v>+b=−1}`。此外，通过缩放，最小化为 `|<w, v[*i*]>+b|=1`。通过要求间隔尽可能大，这可以转换为最大化问题。首先，通过注意到对于 `y[*i*] (<w, v[*i*]>+b)`，它对于所有 `y[*i*]` 在 `A^+`![方程](img/F000163si59.png)` 中以及在 `A^-`![方程](img/F000163si60.png)` 中都大于或等于一。

利用上述事实，求解约束凸最大化问题将找到 `A` 以及最大间隔。在下文中，假设数据是线性可分的。如果不是这种情况，该方法会失败。此外，该方法称为硬间隔分类器。最后，将使用拉格朗日乘子技术来最大化或最小化具有约束的目标函数。这将导致二次优化，通常几乎需要近似数值解。然而，下面提供了一个非常简单的例子，但在这种情况下也需要大量计算。

首先，求 `||w||^(−1)`![方程](img/F000163si61.png)` 的最大值，约束条件为：`y*i*`![方程](img/F000163si62.png)` 大于或等于一，对所有 `y[*i*]`![方程](img/F000163si63.png)` 成立`。此最大化问题可以替换为求 `||w||²/2`![方程](img/F000163si64.png)` 的最小值，约束条件相同。因此，第一步是形成拉格朗日函数：`L=1/2 <w, w>−∑`![方程](img/F000163si65.png)` a[*i*][y[*i*]`![方程](img/F000163si66.png)` (<w, v[*i*]`![方程](img/F000163si67.png)`>+b)−1]`。这里，`a[*i*]`![方程](img/F000163si68.png)` 被称为拉格朗日乘子；它们也需要求出。接下来，对 `w`、`b` 以及所有 `a[*i*]`![方程](img/F000163si69.png)` 求偏导数或梯度，然后全部设为零。首先用 `∂`![方程](img/F000163si70.png)` L/∂w=w−∑`![方程](img/F000163si71.png)` a[*i*] y[*i*] v[*i*]=0`，然后 `∂`![方程](img/F000163si72.png)` L/∂b=∑`![方程](img/F000163si73.png)` a[*i*] y[*i*]=0`。将量 `w=∑`![方程](img/F000163si74.png)` a[*i*] y[*i*] v[*i*]` 代回 `L` 得到长表达式 `L=1/2 <∑`![方程](img/F000163si75.png)` a[*i*] y[*i*] v[*i*], ∑a[*j*]y[*j*]v[*j*]> − ∑a[*i*]y[*i*][<∑a[*j*]y[*j*]v[*j*], v[*i*]>] − ∑a[*i*]y[*i*]b + ∑a[*i*]`![方程](img/F000163si76.png)`。接下来使用 `∑a[*i*]y[*i*]=0`![方程](img/F000163si77.png)` 并简化方程得到 `L = − ∑a[*i*] − 1/2∑∑a[*i*]a[*j*]y[*j*]y[*i*] <v[*i*], v[*j*]>`![方程](img/F000163si78.png)`。现在使用关于 `w` 的决策规则，`<w, v>+b`，即其与一的关系，`w = ∑a[*i*]y[*i*]v[*i*]`，`∑a[*i*]y[*i*] <v[*i*], u> + b`。`L = − ∑a[*i*] − 1/2∑∑a[*i*]a[*j*]y[*j*]y*i*`![方程](img/F000163si79.png)`。

### 示例 18.8

考虑训练集：{(`v[1]`, `y[1]`), (`v[2]`, `y[2]`), (`v[3]`, `y[3]`)}, 其中 `v[*i*]` 在 `H=R²` 中而 `y[*i*]` 在 {1, −1} 中。为了找到 `SVC` `A`，其中 `A={v in H, such that <w, v>+b=0}`。在 `A` 上方应为 `y[*i*]=1` 的那些向量，而在 `A` 下方应为 `y[*i*]= −1` 的那些向量。设 `y[*i*]=1` 的向量 `v[*i*]` 为 `v[1]=(−1 0)′` 和 `v[2]=(0 1)′`，而 `y[*i*]= −1` 的为 `v[3]=(0–1)′`。形成内积 Gram 矩阵 `G`，其元素为 `<v[*i*], v[*j*]>`，`i=1, 2, 3` 作为行指标，`j=1, 2, 3` 作为列指标。矩阵如下所示：

$\\begin{matrix} {|1} & 0 & {0|} \\\\ {|0} & 1 & {{- 1}|} \\\\ {|0} & {- 1} & {1|} \\\\ \\end{matrix}$

![方程](img/F000163si80.png)

该问题的拉格朗日函数为 `L=− ∑`![方程](img/F000163si81.png)` a[*i*]−1/2 ∑∑`![方程](img/F000163si82.png)` a[*i*] a[*j*] y[*j*] y[*i*] (<v[*i*], v[*j*]>)`。特别地，展开后得到 `L = − (a[1]+a[2]+a[3]) − 1/2(a[1]²+a[2]²+a[2]a[3]+a[3]a[2]+a[3]²)`![方程](img/F000163si83.png)`。这里，内积 `<v[*i*], v[*j*]>` 使用 Gram 矩阵 `G` 中的值进行替换。对 `L` 求偏导数：`∂L/∂a[1]=−1−a[1]=0`；`∂L/∂a[2]=−1 – a[2] – a[3]`；`∂L/∂a[3]=−1 – a[3] – a[2]`。由此可知 `a[1]=−1`。另外两个方程是相关的，`a[2]+a[3]=−1`。然而，使用约束条件 `∑`![方程](img/F000163si84.png)`a[*i*]y[*i*]=0`，这意味着 `a[2]−a[3]=1`。因此，`a[2]=0` 且 `a[3]=−1`。最后，使用 `w=∑`![方程](img/F000163si85.png)` a[*i*] y[*i*] v[*i*]`，可得 `w=−v[1]+v[3]=(1 0)′+(0–1)′=(1–1)′`。因此，仿射线分类器恰好是 `R²`![方程](img/F000163si86.png)` 的一个子空间，在 x-y 坐标中；它是 `y=x`。这里的间隔为 `1/2^(1/2)`![方程](img/F000163si87.png)`，且支持向量为 `v[1]=(−1 0)′` 和 `v[3]=(0–1)′`。



当数据不是线性可分时，通常引入松弛变量以使约束方程不那么严格。约束现在变为如下：`y[i] (<w, v[i]>+b)` 大于或等于一减去松弛值 `s[i]`，通常取为非负的。因此，目标再次是最小化 `min ‖w‖²/2`，但 `s[i]`![方程](img/F000163si88.png) 不能过大。提出了一个修正的拉格朗日问题：`min[‖w‖²/2 + C/n ∑ s[i]]`，其中最小化针对 `w`、`b` 和 `s[i]`。常数 `C` 是一个正参数，`n` 是数据点的数量，且求和从 1 到 `n`。值 `C` 在正则化的重要性和正确匹配训练集的重要性之间取得平衡。当 `C` 过大时，训练集匹配良好；如果 `C` 过小，则有利于过拟合。在后一种情况下，这对训练可能有好处，但对未见的真实数据可能就不太好。`C` 被称为误分类的惩罚参数。

利用约束方程得到 `L` 的公式，其中 `a[i]`![方程](img/F000163si90.png) 和 `c[i]`![方程](img/F000163si91.png) 是拉格朗日乘子。`L = ‖w‖²/2 + C/n ∑ s[i] + ∑ a[i] (1 - s[i] - y[i] (<w, v[i]>+b)) - ∑ s[i] c[i]`。如前所述，对 `L` 关于 `w`、`b` 和 `s[i]` 求偏导数或梯度，并令其等于零得到 `∂L/∂w = w - ∑ a[i] y[i] v[i] = 0`；`∂L/∂b = - ∑ a[i] y[i] = 0`；`∂L/∂s[i] = C/n - a[i] - c[i] = 0`。与严格间隔分类器类似，将这些偏导数代入 `L` 得到下面的对偶目标函数，因此需要最大化它或最小化其负值。因此，约束最小化为：`min 1/2 ∑∑ a[i] a[j] y[j] y[i] <v[i], v[j]> - ∑ a[j]`，最小化针对 `a[i]`![方程](img/F000163si98.png)，约束为 `∑ a[i] y[i] = 0`，且 `a[i]` 大于或等于零，但小于或等于 `C/n`。这是 `C/n - a[i] - c[i] = 0` 且 `c[i]` 大于或等于零的结果。

如前所述，解涉及一个二次规划问题。与前述示例不同，Gram 矩阵 `G` 不会被显式使用。这里将使用一个 `n`×`n` 矩阵 `H`，其元素为 `H[i j] = y[j] y[i] <v, c, v[j]>`![方程](img/F000163si100.png)。请注意，如果采用向量矩阵记号，则二次最小化为 `min 1/2 a' H a - a' I`。其满足 `a' y = 0`，且 `0` 小于或等于 `a[i]`![方程](img/F000163si101.png) 小于或等于 `C/n`。在这种情况下，`a` 是 `a[i]`![方程](img/F000163si102.png) 的向量，`y` 是 `y[i]`![方程](img/F000163si103.png) 的向量，且 `I` 是单位向量。

## 18.9 核方法

本节是第 1.10 节和第 5.7 节的延续。回顾一下，在机器学习算法中，核被直接使用，而无需计算特征变换 `Φ`![方程](img/F000163si104.png)，它将原始空间中的向量映射。这里利用了恒等式 `K(v,w) = < Φ(v), Φ(w)> = (<v, w>) ^(d)`。一个有趣的应用，未曾展示过，涉及非齐次多项式核。具体而言，`K(v,w) = (<v, w> + a)^(d)`，其中 `a` 是一个实数。根据二项式展开：`(<v,w> + a)^d = ∑_{k = 0}^{d} d!/(k! (d - k)!) <v,w>^k a^{d - k}`![方程](img/F000163si105.png)。下面给出一个说明该核的例子。

### 例 18.9

设 `v` 和 `w` 在 `R²`![方程](img/F000163si106.png) 中且 `a` 在 `R` 中；则令 `A = (<v,w>+a)² = (v[1]² w[1]² + 2 v[1] v[2] w[1] w[2] + w[2]² v[2]²) + 2 a (v[1] w[1] + w[2] v[2]) + a²`![方程](img/F000163si107.png)。重新排列：`A = (v₁² w₁² + w₂² v₂²) + 2 (v₁ v₂ w₁ w₂) + a (v₁ w₁ + w₂ v₂) + a² = ∑_{i=1}^{2} v_i² w_i² + ∑_{i=1}^{2} ∑_{j=1}^{i-1} (2^{1/2} v_i v_j) (2^{1/2} w_i w_j) + ∑_{i=1}^{2} (2a)^{1/2} v_i (2a)^{1/2} w_i + a².`![方程](img/F000163si108.png)![方程](img/F000163si108a.png) 该表示很重要，因为它可以很容易地推广到更高维度。它还将使 `Φ`![方程](img/F000163si109.png) 能够被找到。这里，核 = `< Φ(v), Φ(w)>`。内积中的两个自变量相同，因此因式分解将得到 `Φ(v)`。

因此，在本例中采用映射 `Φ : R² → R⁶`![方程](img/F000163si110.png)。特征映射 `Φ`![方程](img/F000163si111.png) 使用 `v = (v[1] v[2])'` 的两个元组，在 `R²`![方程](img/F000163si113.png) 中。它将它们映射到所有可能的二阶、`d=2`、非齐次单项式，得到 `Φ(v) = (v[1]² v[1]² 2^{1/2} v[1] v[2] (2a)^{1/2} v[1] (2a)^{1/2} v[2] a)'`![方程](img/F000163si114.png)′。请注意，这里交换律无关紧要。然而，如果采用与齐次情形相同的协议，则映射为 `Φ : R² → R⁷`![方程](img/F000163si115.png)，其中不同的标记很重要，即尽管 `v[1] v[2] = v[2] v[1]`![方程](img/F000163si116.png)，每个都占据一个不同的元组。因此：`Φ(v) = (v[1]² v[1]² v[1] v[2] v[2] v[1] (2a)^{1/2} v[1] (2a)^{1/2} v[2] a)'`![方程](img/F000163si117.png)′。

回顾一下，核是一个涉及非空集合 `X` 的函数，使得 `K: X x X → R`。它与映射相关：`Φ: X → H`，其中 `H` 是实数上的希尔伯特空间。此外，对于 `x` 和 `y` 在 `X` 中，且 `K` 由内积定义：`K(x,y) = < Φ(x), Φ(y)>`，函数 `Φ` 被称为特征映射。此外，`K` 被称为特征核，而 `H` 有时被称为特征空间。`H` 不必是 RKHS。另一方面，RKHS 中的核也是特征核。特征核是对称且半正定的：设 `i` 和 `j` 在任意有限正整数集合中，且 `x[i]`![方程](img/F000163si118.png)、`x[j]`![方程](img/F000163si119.png) 在 `X` 中且 `a[i] a[j]`![方程](img/F000163si120.png) 为实值，则 `∑_{i,j} a_i a_j K(x_i,x_j) = ∑_i ∑_j a_i a_j < Φ(x_i), Φ(x_j)> = ∑_i a_i < Φ(x_i), ∑_j a_j Φ(x_j)> = < ∑_i a_i Φ(x_i), ∑_j a_j Φ(x_j)> = || ∑_j a_j Φ(x_j) ||²`![方程](img/F000163si121.png) 大于或等于零。用向量表示，`a' K a` 大于或等于零，其中 `a` 是由所有 `a[i]`![方程](img/F000163si122.png) 组成的列向量，`a'` 是 `a[i]`![方程](img/F000163si123.png) 的行向量，且 `K` 是 Gram 矩阵。



核由 `l²` 中的序列定义![Equation](img/F000163si124.png)。核方法为涉及支持向量型分类的机器学习提供了坚实的基础。在这种分类中，通常在二分类中使用超平面。这些平面用于分离两个不同的数据类或对象。事实上，这些平面通常不通过原点，并且是仿射变换的实例。此类变换保持直线并保持平行线平行。此外，它们还保持凸性以及极值点。它们不保持距离或角度。在机器学习中，它们也很有用，因为它们是仿射空间的自同构；它们保持维度和子空间。要分为两组的数据首先假定是线性可分的。这预设存在一个超平面可以将数据分为两部分。对于数据非线性可分的情况给出软分类。软分类是指数据是边缘不可分的，即存在偶发异常值。此外，核在回归分析中也有应用。在这里，参数设置被确定以最小化回归曲线对数据的过拟合或欠拟合。

某些特征映射的组合也是特征映射。特别是，特征映射的和与积连同非负标量积也是特征映射。然而，两个特征映射之差可能不是特征映射。这些性质在后面描述的构造中使用。

考虑一个非空集合 `X`，以及一个序列 `Φ[1]`![Equation](img/F000163si125.png)，`Φ[2]`![Equation](img/F000163si126.png)，`Φ[3]`…![Equation](img/F000163si127.png)，为 `l²`![Equation](img/F000163si128.png) 函数，使得 `Φ[i]`![Equation](img/F000163si129.png)：`X`→`R`。那么 `Φ(x)` = (`Φ[1]Φ[2]Φ[3]…`)![Equation](img/F000163si130.png) 是特征映射，且 $K\\left( {x,y} \\right) = \\overset{\\infty}{\\underset{i = 1}{\\sum^{}}}\\Phi\_{i}\\left( x \\right)\\Phi\_{i}\\left( y \\right)$![Equation](img/F000163si131.png) 是 `X` 上的核。这可由 CBS 不等式得出，即 $\\left| K\\left( {x,y} \\right) \\middle| = \\middle| \\overset{\\infty}{\\underset{i = 1}{\\sum^{}}}\\Phi\_{i}\\left( x \\right)\\Phi\_{i}\\left( y \\right) \\right|$![Equation](img/F000163si132.png) 小于或等于 $\\left. \\overset{\\infty}{\\underset{i = 1}{\\sum^{}}} \\middle| \\Phi\_{i}\\left( x \\right)|^{2}\\overset{\\infty}{\\underset{i = 1}{\\sum^{}}} \\middle| \\Phi\_{i}\\left( y \\right)|^{2} \\right.$![Equation](img/F000163si133.png)。

超平面 `A` 将在此处在有限实内积空间 `H` = `R`^(`n`)![Equation](img/F000163si134.png) 中描述。这些平面将是 `H` 的度小于 `n` 的仿射子集。对于 `R` 中的 `b`，以及 `H` 中的 `w`，`A`={ `v` in `H`, such that <`w`, `v`>+`b`=0}。

### 示例 18.10

设 `H` = `R`²![Equation](img/F000163si135.png)，对于 `b`=2，且 `w`=(1 4)′ 在 `H` 中，`A` = {`v`=(`v[1]v[2]`)![Equation](img/F000163si136.png)′ 在 `H` 中，使得  < (14)′, (`v[1]v[2]`)′>+2=0}![Equation](img/F000163si137.png)。相应地，`A` 是直线仿射线：`v[1]` + 4`v[2]` =  − 2![Equation](img/F000163si138.png)。

支持向量机是监督学习，需要训练数据。核技巧将数据变换到更高维度，进行分类，然后再变换回来。空间中的点具有称为特征的元组。超平面将 `H` 分成两个半平面：`A^+`![Equation](img/F000163si139.png)\={ `v` in `H`|<`w`, `v`>+`b` 大于或等于 0} 和 `A^-`![Equation](img/F000163si140.png)\={ `v` in `H`|<`w`, `v`>+`b` <0}，从而使超平面成为二分类的决策边界。`H` 是度量空间，因为它是内积空间，因此它也是赋范向量空间。事实上，内积提供了一个自然度量 `d`。`H` 中 `v` 与 `w` 之间的距离是 `d(v,w)` =  < `v` − `w`, `v` − `w`\>^(1/2) = ∥`v` − `w`∥![Equation](img/F000163si141.png)。最后一个量是由内积诱导的范数。对于向量集合，`X` = {`v[1]`, `v[2]`, …, `v[n]`}![Equation](img/F000163si142.png) 在 `H` 中，集合中单个点 `v[i]`![Equation](img/F000163si143.png) 到仿射分类器 `A` 的距离由 | < `w`, `v[i]` >  + `b`|/∥`w`∥![Equation](img/F000163si144.png) 给出。`X` 中向量到 `A` 的最小距离由最小化该表达式给出。乘以常数的仿射空间，即将 `w` 和 `b` 乘以相同的常数，不会改变空间 `A`；实际上这两个空间是等价的。因此最小距离可以通过 min (|<`w`,`v[i]`\>+`b`|)![Equation](img/F000163si145.png) 对于 `i`=1, 2, …, `n` 找到。参见涉及仿射空间的第 2.9 节。

### 示例 18.11

与前一个示例类似，将创建超平面。然后将找到从 `A` 到集合 `X` 中最近向量的距离。再次设 `H` = `R`²![Equation](img/F000163si146.png)，偏置 `b`=3，且 `w`=(1 2)′ 在 `H` 中，`A` = {`v`=(`v[1]v[2]`)![Equation](img/F000163si147.png)′ 在 `H` 中，使得 <(1 2)′, (`v[1]v[2]`)![Equation](img/F000163si148.png)′>+3=0}。考虑集合 `X`={(0 0)′, (2 3)′, (−2–4)′}。超空间线是 `v[1]` + 2`v[2]` =  − 3![Equation](img/F000163si149.png)。从 (0 0)′ 到 `A` 的距离是|<`w`, (0 0)′>+`b`|/‖`w`‖=|0+3|/5^(1/2)\=3/5^(1/2)。

从 (2 3)′ 到 `A` 的距离是|<`w`, (2 3)′>+`b`|/‖`w`‖=|8+3|/ 5^(1/2)\=11 / 5^(1/2)。

从 (−2–4)′ 到 `A` 的距离是|<`w`, (−2–4)′>+`b`|/‖`w`‖=|−10+3|/ 5^(1/2)\=7 / 5^(1/2)。对 `X` 中所有点的分类得出以下结果：(0 0)′ 和 (2 3)′ 在 `A^+`![Equation](img/F000163si150.png) 中；也 (−2–4)′ 在 `A^-`![Equation](img/F000163si151.png) 中。在任何情况下，零向量是最接近的。记住仿射空间可以缩放，因此乘以权重 `w` 的绝对范数值，距离公式被归一化，距离分别变为 3、11 和 5。通过知道最小距离，可以采用进一步的缩放。事实上，按 3‖`w`‖ 缩放会使结果归一化。

## 18.10 径向基函数核

径向基函数（RBF）核使用，例如 `v`=(x y)′ 在 `R`²![Equation](img/F000163si152.png) 中，以及映射 `ϕ`![Equation](img/F000163si153.png)(`v`) 提供无限维向量 `Φ(v)` = (1*x* *y* *x*y* *y*x* *x²*y²*x²*y*y²*x*…)![Equation](img/F000163si154.png)′。核方法避免计算 `Φ`![Equation](img/F000163si155.png)(`v`)，它产生 `v` 的元组之间的单次、双次、三次交互等。相反，内积在 `R²` 中执行，然后是核：`k(v,w)` =  < `Φ(v)`, `Φ(w)` >  = `e`^( − 1/2*∥*`v` − `w`*|*|²)![Equation](img/F000163si156.png)。为了形式上证明这是一个内积核，写 `e`^( − 1/2*∥*`v` − `w`*|*|²) = `e`^( − 1/2\[(`v` − `w`)^′(`v` − `w`)\]) = `e`^( − 1/2\[`v`^′`v` − 2`v`^′`w` + `w`^′`w`\]) = `e`^( − 1/2\[`v`^′`v` + `w`^′`w`\])*`e`^(`v`^′`w`)![Equation](img/F000163si157.png)。令 `C` = `e`^( − 1/2\[`v`^′`v` + `w`^′`w`\])![Equation](img/F000163si158.png)。那么 `e`^( − 1/2*∥*`v` − `w`*|*|²) = `C`*`e`^(`v`^′`w`) = `C`*`e`^(`v`^′`w` + 1)*`e`^( − 1) = `C′`*`e`^(`v`^′`w` + 1)![Equation](img/F000163si159.png) 其中 `C′` 是新常数。于是 $e^{- 1/2{\\|{v - w}\\|}^{2}} = \\sum\_{n = 0}^{\\infty}{\\left( {1 + \\left. {v'w} \\right\\}} \\right.^{n}/n!}$![Equation](img/F000163si160.png) 这表明 RBF 核包含所有非齐次多项式核。该核投影到无限维空间。它在数据之间执行无限多次交互。




RBF 模型建立在利用空间中点与点之间的距离之上。如果数据由对 (`x[*n*]`, `y[*n*]`) 组成，则它基于 `‖x−x[*n*]‖` 影响 `h(x)`。标准形式为 $h\\left( x \\right) = \\sum\_{n = 1}^{N}{w\_{n}e^{- \\gamma{\\|{x - x\_{n}}\\|}^{2}}}$![方程](img/F000163si161.png)。该表达式是假设的函数形式。在大多数情况下，目标是基于数据 `D=(x[*n*], y[*n*])` 找到由元组 `w[*n*]` 组成的 `w`，其中 `n=1, 2,… N`。为求解 `w`：$\\overset{N}{\\underset{n = 1}{\\sum^{}}}w\_{n}e^{- \\gamma||x - x\_{n}||^{2}} = y\_{m}$![方程](img/F000163si162.png) 对于 `x` = `x[*m*]`![方程](img/F000163si163.png)′。因此 `Φ`![方程](img/F000163si164.png) `w`=`y`。解为 `w` = `Φ`^( − 1)`y`![方程](img/F000163si165.png)，类似于回归。对于分类，使用 $h\\left( x \\right) = {sgn}{({\\overset{N}{\\underset{n = 1}{\\sum^{}}}w\_{n}e^{- \\gamma||x - x\_{n}||^{2}}})}$![方程](img/F000163si166.png)。令 $s = \\overset{N}{\\underset{n = 1}{\\sum^{}}}w\_{n}e^{- \\gamma||x - x\_{n}||^{2}}$![方程](img/F000163si167.png)。

## 18.11 有界矩阵

类似于第 1.9 节中描述的时限信号，二维时限矩阵构成一个内积空间（Alotto et al., 1998; Dougherty and Giardina, 1987）。这些是具有有限支撑的实值函数 `f`，位于 `R`^( `Z` `x` `Z` )![方程](img/F000163si168.png)。这是对应于 `VECTOR` 的载体集合，而对于 `SCALAR`，则采用实数。函数 `f` 在 `R`^( `Z` `x` `Z` )![方程](img/F000163si169.png) 中意味着 `f`: `Z` x `Z`→`R`，但所有这些由有界矩阵描述的函数在有限的格点子集上具有非零值。它们将用 `A` 表示。请注意 `V-ZERO` 对应于 `A` 中的 0 实体。`A` 中的信号或函数使用逐点运算构成实值向量空间。与所引用的章节一样，`A` 也构成一个内积空间，使用这些矩阵交集上的点积，但同样，它不是希尔伯特空间。此外，对于 `A` 中的 `f`，零的补集、非零集记为 `COZ(f)`。该有限集合由所有格点 (`n`, `m`) 组成，`n`, `m` 在 `Z` x `Z` 中，其中 `f` (`n`, `m`) 与 `V-ZERO` 不同。

对于 `A` 中任意信号 `f`，且 `COZ(f)` 非空的一种方便表示，类似于第 15.7 节中的 Young 图。事实上，关键格点 (`p`, `q`) 是包围 `f` 所有非零值的任意矩阵的最左、上元素的位置。例如，找到点 (`p`, `q`) 等于最小值 `n`，使得 `f` (`n`, ·) 非零的位置，并且最大 `m` 值，使得 `f` (·, `m`) 非零的位置。接下来，采用一种矩阵型结构来包围 `f` 的所有非零值以及 (`p`, `q`)。后一点本身可能是零。这类似于最小包围矩形，尽管矩阵不必是最小的。然而，一般来说，矩阵中必须至少有一个非零值，且外部没有非零值。一旦确定最左坐标 `p` 和最上值坐标 `q`，值 (`p`, `q`) 将用作矩阵右下侧的指针。这种数据结构称为有界矩阵。在整个过程中，至少最初假设非零集是非空的。一个例子可能有所帮助。

### 示例 18.12

考虑 `A` 中的二维数字信号 `f`，其中 `f` 除在 `COZ(f)`={(0, 0), (−1, 1), (1, 2), (1, 0), (1, 1)} 上外为零。另设 `f` (0, 0)=5，`f` (−1, 1)=3，`f` (1, 2)=2，`f` (1, 0)= −3，最后 `f` (1, 1)=6。`COZ(f)` 的第一个 x 坐标集合由 `Z` 中的点组成，即 {0, −1, 1}，最小值为 `p`=−1。第二个 y 坐标集合为 {0, 1, 2}；最大值为 `q`=2。因此，表示函数 `f` 的两个有界矩阵结构如下所示：

$\\begin{matrix} \\begin{matrix} {|0} & 0 & {2|} \\\\ {|3} & 0 & {6|} \\\\ {|0} & 5 & {{- 3}|}\_{- 1,2} \\\\ \\end{matrix} & \\begin{matrix} {|0} & 0 & 0 & 0 & 2 & {0|} \\\\ {|0} & 0 & 3 & 0 & 6 & {0|} \\\\ {|0} & 0 & 0 & 5 & {- 3} & {0|} \\\\ {|0} & 0 & 0 & 0 & 0 & {0|}\_{- 3,2} \\\\ \\end{matrix} \\\\ \\end{matrix}\\operatorname{.\\#}$

![方程](img/F000163si170.png)

因此可以看出，存在表示 `A` 中函数的有界矩阵的等价类，但此方向将不予追究。然而，在上述示例中，展示了一种压缩形式。左侧的有界矩阵称为最小有界矩阵，因为没有比这个三乘三矩阵更小的矩阵能够捕获 `f` 的所有非零值。

内积空间 `A` 也构成一个代数。对于 `f` 和 `g` 在 `A` 中，逐点乘法定义为卷积

`BINE(f, g)`(`n`,`m`)=(`f`⋆![方程](img/F000163si171.png)`g`) (`n`,`m`)=$\\sum\_{k = - \\infty}^{\\infty}{\\sum\_{j = - \\infty}^{\\infty}{g\\left( {n - k,m - j} \\right)f\\left( {k,j} \\right)}}$![方程](img/F000163si172.png)。使用这种乘法 `BINE`，`A` 成为一个幺元、交换、结合代数。幺元函数 `V-ONE` 为 `I` = (1)[(0, 0)]![方程](img/F000163si173.png)，且 `I`![ent](img/sstarf_8902.png)`f`=`f`![ent](img/sstarf_8902.png)`I`=`f`。尽管上述求和中的极限是无限的，但非零项只有有限个。实际求和极限的更简洁表达式涉及非零集。特别地，`COZ(f`![ent](img/sstarf_8902.png)`g)` 是两个集合 `COZ(f)` 和 `COZ(g)` 的扩张的子集。扩张由 `D(COZ(f),COZ(g))` 给出。该量等于所有整数对集合 {(`n`+`k`, `m`+`j`)} 的并集，其中 (`n`, `m`) 在 `COZ(f)` 中且 (`k`, `j`) 在 `COZ(g)` 中。`f` 和 `g` 的卷积在此扩张集合之外为零。因此扩张为卷积提供了支撑区域。因此，卷积可使用以下方法计算

(`f`⋆`g`) (`n`,`m`) = ∑`f`(`n`−`k`,`m`−`j`)`g`(`k`,`j`),

![方程](img/F000163si174.png)

其中 (`k`, `j`) 在 `COZ(g)` 中且 (`n`−`k`, `m`−`j`) 在 `COZ(f)` 中。求 (`f`![ent](img/sstarf_8902.png)`g`) (`n`,`m`) 的过程首先是找到扩张集 `D(COZ(f),COZ(g))`。只有当 (`n`,`m`) 在此集合中时，才使用 `COZ(g)` 中的 (`k`, `j`)；如果 (`n`−`k`, `m`−`j`) 在 `COZ(f)` 中，则将 `f`(`n`−`k`, `m`−`j`) 与 `g`(`k`,`j`) 相乘。必须对所有可能性进行计算，然后求和。该结果是 (`n`, `m`) 处的卷积。由于该和可能等于零，这表明扩张集可能不是卷积的非零集。

### 示例 18.13

考虑 `A` 中的两个有界矩阵 `f` 和 `g`，分别由最小有界矩阵结构给出：

$\\begin{matrix} \\begin{matrix} {|0} & {1|} \\\\ {|2} & {3|}\_{0,2} \\\\ \\end{matrix} & \\begin{matrix} {|2} & {0|} \\\\ {|{- 1}} & {4|}\_{1,3} \\\\ \\end{matrix} \\\\ \\end{matrix}$

![方程](img/F000163si175.png)

`COZ(f)`={(1, 2), (0, 1), (1, 1)} 且 `COZ(g)`={(1, 3), (1, 2), (2, 2)}。这两个集合的扩张为 `D(COZ(f),COZ(g))`={(2, 5), (2, 4), (3, 4), (1, 4), (1, 3), (2, 3), (3, 3)}。该格点集合仅为卷积提供支撑区域。在此区域之外，格点处全部为零。从该集合中的第一个元素开始，(`n`, `m`) =(2, 5)，使用 `COZ(g)` 中的 (`k`, `j`) =(1, 3)，然后检查 (`n`−`k`, `m`−`j`) =(1, 2) 是否在 `COZ(f)` 中。是的，存在，因此求乘积，`f`(1, 2)·`g` (1, 3)=1·2=2。接下来，该集合中的第二个元素 (`n`, `m`) =(2, 4)，使用 `COZ(g)` 中的 (`k`, `j`) =(1, 3)，然后检查 (`n`−`k`, `m`−`j`) =(1, 1) 是否在 `COZ(f)` 中。是的，存在，因此求乘积，`f`(1, 1)·`g` (1, 3)=3·2=6。但 (`k`, `j`) =(1, 2) 也适用，即 (`n`−`k`, `m`−`j`) =(1, 2) 在 `COZ(f)` 中；因此 `f`(1, 2)·`g` (1, 2)=1·(−1)=−1。这些必须相加；因此 (`f`![ent](img/sstarf_8902.png)`g`)(2, 4)=6–1=5。



接下来，该集合中的第三个元素 `(n, m)=(3, 4)`，在 `COZ(g)` 中使用 `(k, j)=(1, 3)`，然后检查 `(n−k, m−j)=(2, 1)` 是否在 `COZ(f)` 中。否，然后尝试 `COZ(g)` 中的 `(k, j)=(1, 2)`；然后检查 `(n−k, m−j)=(2, 2)` 是否在 `COZ(f)` 中。再次否，然后尝试 `COZ(g)` 中的 `(k, j)=(2, 2)`；然后检查 `(n−k, m−j)=(1, 2)` 是否在 `COZ(f)` 中。是的，它在，所以求乘积，`f(1, 2)·g(2, 2)=1·4=4`。接下来，该集合中的第四个元素 `(n, m)=(1, 4)`，在 `COZ(g)` 中使用 `(k, j)=(1, 3)`，然后检查 `(n−k, m−j)=(0, 1)` 是否在 `COZ(f)` 中。是的，它在，所以求乘积，`f(0, 1)·g(1, 3)=2·2=4`。接下来，该集合中的第五个元素 `(n, m)=(1, 3)`，在 `COZ(g)` 中使用 `(k, j)=(1, 2)`，然后检查 `(n−k, m−j)=(0, 1)` 是否在 `COZ(f)` 中。是的，它在，所以求乘积，`f(0, 1)·g(1, 2)=2·(−1)= −2`。

接下来是扩张集合中的第六个元素，`(n, m)=(2, 3)`，在 `COZ(g)` 中使用 `(k, j)=(1, 2)`，然后检查 `(n−k, m−j)=(1, 1)` 是否在 `COZ(f)` 中。是的，它在，所以求乘积，`f(1, 1)·g(1, 2)=3·−1=−3`。然而，`(k, j)=(2, 2)` 也成立，因为 `(n−k, m−j)=(0, 1)` 在 `COZ(f)` 中。然后 `f(0, 1)·g(2, 2)=2·4=8`。相加得到 `−3+8=5`。最后，扩张集合中的最后一个值是 `(n, m)=(3, 3)`，并且 `(k, j)=(2, 2)` 成立，因为 `(n−k, m−j)=(1, 1)` 在 `COZ(f)` 中。因此，`f(1, 1)·g(2, 2)=3·4=12`。

因此，`f ⋆ g` 的有界矩阵如下：

$\\begin{matrix} {|0} & 2 & {0|} \\\\ {|4} & 5 & {4|} \\\\ {|{- 2}} & 5 & {12|}\_{1,5} \\\\ \\end{matrix}\\operatorname{.\\#}$

![方程](img/F000163si176.png)

正如第 3.2 节中关于有界向量的描述那样，存在一种用于求有界矩阵卷积的并行算法。它也在 图 3.2 中有所说明。简而言之，该方法是

`f` ⋆ `g` = `ADD`[`SCALAR`(`g(n,m)`, `TRAN(f; n,m)`), for (`n,m`) in `COZ(g)`].

![方程](img/F000163si177.png)

`SCALAR` 只是将 `f` 矩阵的平移与位于 `(n, m)` 处的 `g` 的值相乘。`TRAN` 只是通过改变矩阵右下角外部的位置指针来平移 `f` 矩阵。该变化是通过相加发生的，结果为 `(p+n, q+m)`。仅使用此操作时，矩阵内部的值不会改变。前面提到的并行卷积方程与所引用图之间的差异为零。`SCALAR` 和 `TRAN` 操作可交换！

### 例 18.14

参见例 8.13，其中 `COZ(g)={(1, 3), (1, 2), (2, 2)}`，并且 `g(1, 3)=2`，`g(1, 2)= −1`，`g(2, 2)=4`。然后 `f` 如下给出，其后是 `g(1, 3)·TRAN(f; 1, 3)`，随后应用 `g(1, 2)·TRAN(f; 1, 2)`，最后乘以 `g(2, 2)·TRAN(f; 2, 2)`：

$\\begin{matrix} \\begin{matrix} {|0} & {1|} \\\\ {|2} & {3|}\_{0,2} \\\\ \\end{matrix} & \\begin{matrix} {|0} & {2|} \\\\ {|4} & {6|}\_{1,5} \\\\ \\end{matrix} & \\begin{matrix} {|0} & {{- 1}|} \\\\ {|{- 2}} & {{- 3}|}\_{1,4} \\\\ \\end{matrix} & \\begin{matrix} {|0} & {4|} \\\\ {|8} & {{12|}\_{2,4}.} \\\\ \\end{matrix} \\\\ \\end{matrix}$

![方程](img/F000163si178.png)

重写最后三个有界矩阵，使其具有共同的位置指示符，得到如下结果：

$\\begin{matrix} \\begin{matrix} {|0} & 2 & {0|} \\\\ {|4} & 6 & {0|} \\\\ {|0} & 0 & {0|}\_{1,5} \\\\ \\end{matrix} & \\begin{matrix} {|0} & 0 & {0|} \\\\ {|0} & {- 1} & {0|} \\\\ {|{- 2}} & {- 3} & {0|}\_{1,5} \\\\ \\end{matrix} & \\begin{matrix} {|0} & 0 & {0|} \\\\ {|0} & 0 & {4|} \\\\ {|0} & 8 & {{12|}\_{1,5}.} \\\\ \\end{matrix} \\\\ \\end{matrix}$

![方程](img/F000163si179.png)

将上述三个有界矩阵相加得到的结果与先前在 例 18.13 中给出的结果完全相同。#

当 `f` 和 `g` 在 `A` 中时，可以找到 `f ⋆ g` 的最小支撑有界矩阵。假设卷积不等于零。首先求 `D(COZ(f),COZ(g))`。然后在此集合中找出第一个元组的最小值和第二个元组的最大值；称其为 `(p, q)`。将其用作卷积有界矩阵中左上最靠前条目的位置。实际支撑有界矩阵为 `N` 行 `M` 列，其中 `N=p′−p,+1`，其中 `p′` 是扩张集合中第一个元组的最大值，而 `M=q−q′+1`，其中 `q′` 是扩张集合中第二个元组的最小值。

### 例 18.15

再次参见 例 18.13，其中 `D(COZ(f),COZ(g))={(2, 5), (2, 4), (3, 4), (1, 4), (1, 3), (2, 3), (3, 3)}`。则 `(p, q)=(1, 5)`，并且由于 `p′=3` 且 `q′=3`，则 `N=3–1+1=3`，`M=5–3+1=3`。#

类似于 第 3.9 节 中描述的环绕有界向量，环绕有界矩阵也构成一个 Banach\* 代数。在此情况下，使用 `R^{Z[r]xZ[r]}` 中的函数 `f`。这些是定义域为 `{0, 1, … r−1} x {0, 1, … r−1}`、值域为实数的函数。此外，`Z[r]` 具有模 `r` 的循环群结构。所有这些函数对于固定的正整数 `r` 的集合将记为 `A[r]`。有界矩阵为 `A[r]` 中的元素提供了方便的表示。逐点加法、标量乘法等表明该结构成为实值向量空间，其中 `V-ZERO` 为全零的有界矩阵。此外，卷积乘法给出了幺元、交换且结合的代数结构。单位元 `V-ONE` 是全零的有界矩阵，除了在 `(0, 0)` 位置有一个 1。最后，使用 `l²` 范数创建了希尔伯特空间结构。完备性如附录 A.1 中所述。

正如环绕有界向量的 一维情况一样，对于模 `r` 有界矩阵，上标 (`W[r]`) 将出现在右上角。它还表示正在使用 `r²` 大小的有界矩阵。此外，右下侧外部的下标表示环绕有界矩阵的左上条目。一个例子应该有助于使这些概念更易于理解。

### 例 18.16

考虑环绕有界矩阵 `f` 在 `A[3]` 中；它如下所述给出。其后是 `f` 的 2 倍标量倍，即 `SCALAR(f; 2)`。最后，下面第三个矩阵是该实际三乘三矩阵的更紧凑表示：#

$\\begin{matrix} \\begin{matrix} \\left| \\begin{matrix} 0 & 2 & {- 1} \\\\ \\end{matrix} \\right|^{W3} \\\\ \\left| \\begin{matrix} 0 & 0 & {- 3} \\\\ \\end{matrix} \\right| \\\\ \\left| \\begin{matrix} 0 & 0 & 0 \\\\ \\end{matrix} \\right|\_{0,3} \\\\ \\end{matrix} & \\begin{matrix} \\left| \\begin{matrix} 0 & 4 & {- 2} \\\\ \\end{matrix} \\right|^{W3} \\\\ \\left| \\begin{matrix} 0 & 0 & {- 6} \\\\ \\end{matrix} \\right| \\\\ \\left| \\begin{matrix} 0 & 0 & 0 \\\\ \\end{matrix} \\right|\_{0,2} \\\\ \\end{matrix} & \\begin{matrix} \\left| \\begin{matrix} 2 & {- 1} \\\\ \\end{matrix} \\right|^{W3} \\\\ \\left| \\begin{matrix} 0 & {- 3} \\\\ \\end{matrix} \\right|\_{1,3} \\\\ \\end{matrix} \\\\ \\end{matrix}$

![方程](img/F000163si187.png)

此外，`f` 的二范数为 `‖f‖[2] = (4+1+9)^(1/2) = 14^(1/2)`，而一范数为 `‖f‖[1] = 6`。#



余零集 `f` 在 `A[r]` 中![Equation](img/F000163si190.png) 由 {(`n`, `m`) in `Z[r]`x`Z[r]`![Equation](img/F000163si191.png) 使得 `f`(`n`, `m`) in `R`−{0}} 组成。如前所述，`A[r]` 中两个函数的膨胀集![Equation](img/F000163si192.png) 在计算卷积时至关重要。膨胀集是卷积的支持区域，因此只有该集合内的点才应在此操作中使用。卷积可使用以下公式计算：
`(`f`⋆`g`)`(`n`,`m`) = ∑`f`(`n`−`k`,`m`−`j`)`g`(`k`,`j`)`,
![Equation](img/F000163si193.png)
其中 (`k`, `j`) 在 `COZ`(`g`) 中，且 (`n`−`k`, `m`−`j`) 在 `COZ`(`f`) 中。求 (`f`⋆`g`) (`n`,`m`) 的过程与之前相同，首先求膨胀集 `D`(`COZ`(`f`),`COZ`(`g`))。只有当 (`n`,`m`) 在此集合中时，才使用 `COZ`(`g`) 中的 (`k`, `j`)；如果 (`n`−`k`, `m`−`j`) 在 `COZ`(`f`) 中，则将 `f`(`n`−`k`, `m`−`j`) 与 `g`(`k`,`j`) 相乘。必须对所有可能性进行计算，然后求和。此结果即为在 (`n`, `m`) 处的卷积。在给出示例之前，最好先介绍并行算法。
寻找环绕边界矩阵卷积的并行算法在 图 3.2 中示出。如前所述，该方法为：
`f`⋆`g` = `ADD`[`SCALAR`(`g`(`n`,`m`),`TRAN`(`f`; `n`,`m`)), `f` `for` (`n`,`m`) in `COZ`(`g`)].![Equation](img/F000163si194.png)
再次说明，在此公式中，`SCALAR` 是 `f` 矩阵的平移的乘法。乘法因子是位于 (`n`, `m`) 处的 `g` 的值。这与边界矩阵情况下的乘法类似。`TRAN` 只是通过改变矩阵右下角外部的位置指针来平移 `f` 的矩阵，但此操作按模 `r` 执行。变化是通过加法实现的。结果为 (`p`+`n`, `q`+`m`)，所有运算均按模 `r`。仅通过此操作，矩阵内的值不会发生变化。
### Example 18.17
再次考虑前一示例中的环绕函数 `f` 在 `A[3]`![Equation](img/F000163si195.png) 中。它在下面再次给出，随后是同样在 `A[3]`![Equation](img/F000163si196.png) 中的 `g`。目标是求 `f`⋆`g`。该操作将使用并行算法执行，然后使用逐点计算检查一两个值。
$\\begin{matrix} \\begin{matrix} {|2} & {{- 1}|}^{W3} \\\\ {|0} & {{- 3}|}\_{1,2} \\\\ \\end{matrix} & \\begin{matrix} {|1} & {4|}^{W3} \\\\ {|0} & {{5|}\_{1,2}.} \\\\ \\end{matrix} \\\\ \\end{matrix}$
![Equation](img/F000163si197.png)
首先求余零集，`COZ`(`f`)={(1, 2), (2, 2), (2, 1)}，且 `COZ`(`g`)={(1, 2), (2, 2), (2, 1)}。膨胀为 `D`(`COZ`(`f`), `COZ`(`g`))={(2, 4), (3, 4), (3, 3), (4, 4), (4, 3), (4, 2)}={(2, 1), (0, 1), (0, 0), (1, 1), (1, 0), (1, 2)}。最后的整数对集合出现的原因是所有域运算均按模三执行。读取矩阵 `g` 的值得到 `g`(1, 2)=1，`g`(2, 2)=4，`g`(2, 1)=5。为并行算法做准备，首先给出下面的 `f`。随后是 `g`(1, 2)·`TRAN`(`f`; 1, 2)。接下来是 `g`(2, 2)·`TRAN`(`f`; 2, 2)。最后使用 `g`(2, 1)·`TRAN`(`f`; 2, 1)。
$\\begin{matrix} {|\\begin{matrix} 2 & {- 1} \\\\ \\end{matrix}|}^{W3} & {|\\begin{matrix} 2 & {- 1} \\\\ \\end{matrix}|}^{W3} & {|\\begin{matrix} 8 & {- 4} \\\\ \\end{matrix}|}^{W3} & {|\\begin{matrix} 10 & {- 5} \\\\ \\end{matrix}|}^{W3} \\\\ {|\\begin{matrix} 0 & {- 3} \\\\ \\end{matrix}|}\_{1,2} & {|\\begin{matrix} 0 & {- 3} \\\\ \\end{matrix}|}\_{2,1} & {|\\begin{matrix} 0 & {- 12} \\\\ \\end{matrix}|}\_{0,1} & {{|\\begin{matrix} 0 & {- 15} \\\\ \\end{matrix}|}\_{0,0}.} \\\\ \\end{matrix}$
![Equation](img/F000163si198.png)
将最后三个矩阵重写为具有共同指针的形式：
$\\begin{matrix} \\begin{matrix} {|0} & 0 & {0|}^{W3} \\\\ {|{- 1}} & 0 & {2|} \\\\ {|{- 3}} & 0 & {0|}\_{0,2} \\\\ \\end{matrix} & \\begin{matrix} {|0} & 0 & {0|}^{W3} \\\\ {|8} & {- 4} & {0|} \\\\ {|0} & {- 12} & {0|}\_{0,2} \\\\ \\end{matrix} & \\begin{matrix} {|0} & {- 15} & {0|}^{W3} \\\\ {|0} & 0 & {0|} \\\\ {|10} & {- 5} & {{0|}\_{0,2}.} \\\\ \\end{matrix} \\\\ \\end{matrix}$
![Equation](img/F000163si199.png)
与之前的更紧凑表示相比，这些相加很简单。因此，结果为 `f`⋆`g`。=
$\\begin{matrix} {|0} & {- 15} & {0|}^{W3} \\\\ {|7} & {- 4} & {2|} \\\\ {|7} & {- 17} & {{0|}\_{0,2}.} \\\\ \\end{matrix}$
![Equation](img/F000163si200.png)
作为检验，考虑 `f`⋆`g`(0, 0)=`f`(1, 2)·`g`(2, 1)+`f`(2, 1)·`g`(1, 2)=2·5+(−3)·1=7。另有 `f`⋆`g`(0, 1)=`f`(1, 2)·`g`(2, 2)+`f`(2, 2)·`g`(1, 2)=2·4+(−1)·1=7。#
## 18.12 卷积神经网络与量子卷积神经网络
卷积神经网络 (`CNN`) 中的主要操作是卷积。此操作通常在 `CNN` 架构的多个层中执行。图 18.4 提供了在成像中使用的 `CNN` 内操作的典型说明。非常经常地，在卷积操作之间会执行某种类型的压缩。这些操作在图中示出并称为池化层。在这些操作中，通常呈矩形模式的一小部分像素被转换为单个标量值。这通常通过最大池化完成，其中所有像素值中的最大值为代表。有时计算并采用平均值或中值。在任何情况下，都已发生源编码，结果是计算负担减轻。最后的操作是典型的全连接 `NN` 层。通常执行反向传播以调整涉及卷积核的关键参数。过去的卷积核通常是手工制作的。然而，随着后端 `NN` 的频繁使用，更有用的核可以机器学习。
![Figure 18.4 Convolutional neural network.](img/F000163f18-04-9780443136979.jpg)
图 18.4 卷积神经网络。
在所引用的图中，`C` 表示卷积层。例如，最左边的卷积层可能寻找边缘或纹理的低级特征。邻近 `C` 的是表示池化层的 `P`。该层可能降低噪声水平。下一个卷积层可能用于识别更复杂的结构。最后一层通常是全连接 `NN`。
在 `CNN` 中，存在一个观测图像 `f`，例如由边界矩阵表示的 `N`×`M` 像素。卷积过程涉及一个启发式确定的较小的 `n`×`m` 边界矩阵 `g`，称为与 `f` 卷积的核。在这种情况下，观测图像被称为被 `g` 过滤。通常，滤波矩阵需要适合于观测图像的内部。由于这种安排， resulting 卷积的维度为 `N`−`n`+1 by `M`−`m`+1。为防止缩小，通常通过添加边界来扩大观测图像。



最近，关于卷积神经网络的量子版本 QCNN 的论文和文章激增，QCNN（Hur 等, 2022）。它们被用于经典机器学习分类情境并利用纠缠。QCNN 也被用于常规图像处理应用，例如空间滤波、边缘检测以及手写符号识别（Wei 等, 2022）。与过去一样，研究仍在继续使用机器学习设备对物理中的高能事件进行分类。此研究的实例是文章 Chen 等, (2022)。此类应用的另一实例可在 Hermann 等 (2022) 中找到。在本报告中，QCNN 被用于超导量子处理器以识别量子相。一些论文解释了如何使用量子电路实现 QCNN（Zheng 等, 2022）。在本文中，提出了一种通用 QCNN 模型，由全部三部分组成：卷积层、池化层和全连接神经网络层。已出现多篇关于使用 QCNN 的医学类应用的论文（Magallanes 等, 2022）。

## References
* Alotto 等, 1998 Alotto L, Giardina C, Luo H. 一种统一的信号代数方法用于二维信号处理。 *Pure Appl.* 1998;Math 210 Marcel Dekker.
* Benlamine 等, 2020 Benlamine, et al. 量子协同 k 均值。 *IJCNN* 2020; IEEE.
* Chen 等, 2022 Chen S, et al. 用于高能物理数据分析的 QCNN。 *Phys Rev Res* 2022;.
* Date 等, 2021 Date P, Arthur D, Pusey-Nazzaro L. 用于训练机器学习模型的 QUBO 形式化。 *Sci Rep.* 2021;11 10029.
* Dougherty and Giardina, 1987 Dougherty E, Giardina C. *0-13-453283-X*. *从连续到离散的图像处理*。 1 Prentice-Hall 1987;.
* Flick 等, 2017 Flick J, Ruggenthaler M, Appel H, Rubio A. 原子与分子在腔中，从量子电动力学化学中的弱耦合到强耦合。 *Proc Natl Acad Sci.* 2017;114(12):3026–3030.
* Hermann 等, 2022 Hermann J, et al. 在超导量子处理器上实现 QCNN 以识别量子相。 *Nature* 2022;.
* Hur 等, 2022 Hur T, et al. *用于经典数据分类的 QCNN* Springer Link 2022;.
* IonQ Staff, 2023 IonQ Staff, 2023. 用量子使能的道路标志描绘未来。
* Kavitha, 2022 Kavitha, S.S., Kaulgud, N., 2022. 用于支持向量机分类的量子机器学习。 Evol. Intell. 1–10.
* Khan, 2019 Khan, H. 2019. 超导体-绝缘体转变中的量子涨落。 The Ohio State University.
* Liu, 2018 Liu, N., Rebentrost, P., 2018. 用于量子异常检测的量子机器学习。 Phys. Rev. A. 97 (4), 042315.
* Magallanes 等, 2022 Magallanes E, et al. Expert systems with applications *用于 X 射线冠状动脉造影中狭窄检测的混合经典 QCNN* Elsevier 2022;.
* Mengoni, 2021 Mengoni R. 在量子计算机上进行面部表情识别。 *Quantum Mach Intell.* 2021; article 3 no. 8.
* O’Malley 等, 2018 O’Malley D, et al. 使用 D-Wave 量子退火器的非负/二进制矩阵分解。 *PLoS One*. 2018;13e0206653 [`doi.org/10.1371/journal.pone.0206653`](https://doi.org/10.1371/journal.pone.0206653).
* Perrier 等, 2022 Perrier, et al. QDataSet，用于机器学习的量子数据集。 *Sci Data* 2022;.
* Shah, 2019 Shah, R., Gorard, J., 2019. 量子细胞自动机、黑洞热力学和量子复杂性定律。 arXiv preprint arXiv:1910.00578.
* Singh, 2021 Singh, P., Bose, S.S., 2021. 用于 COVID-19 CT 扫描图像分割的量子聚类优化方法。 Expert Syst. Appl. 185, 115637.
* Valiant, 1984 Valiant L. 可学习性的理论。 *Commun ACM*. 1984;27.
* Vapnik, 2000 Vapnik V. *统计学习理论的本质* Springer 2000;.
* Vapnik and Chervonenkis, 1971 Vapnik V, Chervonenkis A. 事件相对频率与其概率的均匀收敛性。 *Theory Probab Appl.* 1971;16.
* Wei 等, 2022 Wei S, et al. *NISQ 设备上的 QCNN* Springer Link 2022;.
* Wittek, 2014 Wittek P. *量子机器学习* Google Books 2014;.
* Yang 等, 2021 Yang C, et al. 使用量子卷积神经网络进行自动语音识别的特征提取去中心化。 *ICASS* 2021;.
* Zheng 等, 2022 Zheng J, et al. 量子电路上 QCNN 的设计。 Elsevier *J Frankl Inst* 2022;.

# 第 19 章

## 再现核及其他希尔伯特空间

### Abstract
本章以谐振子的代数解开始。解的关键在于产生阶梯算子的循环性质。这导致了 Hermite 多项式解。第 19.2 节开始描述复数域上的再现希尔伯特空间。Hardy 圆盘代数也在本节中引入，以及 Bargmann 核和 Jordan 代数。下一节说明实数域上的再现希尔伯特空间。下一节专门介绍 Mercer 定理以及第二类 Fredholm 型积分方程的例子。下一节描述了涉及投影值测度的谱定理。其后是 Riesz-Markov 定理。下一节提供了不可分希尔伯特空间的例子。特别是，几乎周期函数的不可分希尔伯特空间 được 说明。本章以证明所有可分希尔伯特空间都与 `l²` 等距同构结束。

#### Keywords
圆盘代数; Hardy 空间; Mittag-Leffler 函数; Jordan 代数; Bargmann-Fock 空间; Mercer 定理; Riesz-Markov 定理; 带限函数; Szegő 核; Siegel-Bergman 核

## 19.1 谐振子的代数解




In 第 6.1 节, the ground-state solution to the harmonic oscillator is shown to be equal to `Ψ[0]` = (`m w[0]`/(`π h`))^(1/4) `e`^(− `m w[0] x²`/(2 `h`))![Equation](img/F000278si1.png). 该解是通过求解一阶微分方程并归一化高斯型核得到的。归一化涉及求 `N`=`(m w[0]/(π h))^(1/4)`。对于一般的量子谐振子，定态薛定谔方程如下：− `h`²/(2 `m`)∂² `Ψ`(`x`)/∂ `x`∂ `x` + 1/2 `m w[0]² x² Ψ(x)` = `E Ψ(x)`![Equation](img/F000278si2.png)。目标是找到允许的能量态 `E`，作为特征值及其对应的特征函数，`Ψ`![Equation](img/F000278si3.png) (`x`)。这些函数应归一化，并且关于 `x`=0 对称或反对称。此外，概率密度函数，|`Ψ(x)`|²![Equation](img/F000278si4.png)，必须在区间 (−∞, ∞) 上有限。

Following the excellent presentation provided in Hall (2013), the solutions for higher energy, that is, the solutions for excited state levels, will be found in a purely algebraic manner. 在所引用的文本中，可以找到与本发展中使用的无界产生和湮灭算符有关的重要定义域问题。从代数观点看，关键恒等式涉及基态，`Ψ[0]`![Equation](img/F000278si5.png)。首先，使用湮灭操作 `a` yields `a |Ψ[0]> = 0`![Equation](img/F000278si6.png)。其次，存在产生操作 `a†` 的循环性质：(`a†`)^(`n`) |`Ψ[0]`> = `Ψ[n]`![Equation](img/F000278si7.png)，其中 `n` 为非负整数。有关 `a†` 的循环性质的细节请参阅 第 15.2 节。循环性质的结果是激发态 `Ψ[n] = H[n] Ψ[0]`![Equation](img/F000278si8.png)。这里，`H[n]`![Equation](img/F000278si9.png) 是一个次数为 `n` 的多项式，可通过归纳法求得，从 `H[0] = 1`![Equation](img/F000278si10.png) 开始。此外，这些多项式称为厄米多项式。它们在 (−∞, ∞) 上正交，这是其为 Sturm-Liouville 微分方程解的后果。参见附录 A.7。使用厄米多项式的 Rodrigues 公式：`H[n] = (−1)^(n) e^(x²) d^(n) e^(− x²)/d x^(n)`![Equation](img/F000278si11.png)，`n`=0, 1, 2, … gives, for instance, `H[0]=1`, `H[1]=2 x`, `H[2]=4 x²–2`, and `H[3]=8 x³–12 x`, …

Accordingly, the wave function solutions are `Ψ[n] = N Hn e^(− (b x)²/2)`![Equation](img/F000278si12.png)，其中 `b = [(m w[0])/h]^(1/2)`![Equation](img/F000278si13.png)。这些解具有相应的特征值，由允许的离散能级给出 `E[n] = (2 n+1) h w[0]/2`，`n = 0, 1, 2, …`![Equation](img/F000278si14.png) 图 19.1 说明了偶数波函数的偶对称性和奇数波函数的奇对称性。此外，当水平坐标为零时，每个波函数要么存在极值点，要么存在零交叉。零交叉以 `Ψ[0]` 为起点按 mod2 出现，局部极大值按 mod4 出现，局部极小值也是如此。

![Figure 19.1 The first five wave functions for the harmonic oscillator.](img/F000278f19-01-9780443136979.jpg)

图 19.1 谐振子的前五个波函数。

## 19.2 复数域上关于 C 的再生核希尔伯特空间和圆盘代数

首先，`H` 是 `X` 上的再生核希尔伯特空间（RKHS）的一个有用且直观的定义意味着 `H` 是非空集合 `X` 上复值连续函数的希尔伯特空间。因此，`H` 是 `C^(X)`![Equation](img/F000278si15.png) 的子集。此外，对于 `H` 中的所有函数或向量，`f` 和 `g`，以及 `ϵ`![Equation](img/F000278si16.png)> 0，存在一个 `δ`![Equation](img/F000278si17.png)> 0，使得如果 ‖`f−g`‖<`δ`![Equation](img/F000278si18.png)，则 |`f(x)−g(x)`|<`ϵ`![Equation](img/F000278si19.png)。相应地，这意味着函数是逐点连续的。使用 RKHS，有界性和连续性无关。为了说明这是微妙的要求，请考虑以下示例。

### 示例 19.1

设 `H` 为 [0, 1] 上复值绝对平方函数的希尔伯特空间。考虑该闭区间上的两个函数 `f=t` 以及 [0, 1) 上的 `g=t` 且 `g(1)=4 + 3i`。在这种情况下，‖`f−g`‖=0；然而，sup |`f−g`|=5。这些函数是有界的，但不连续。#

在前面的例子中，表明希尔伯特空间中的有界性在逐点计算中对于连续性而言不起作用。函数 `K`: `X²→C` 被称为 `H` 的再生核，只要 `H` 包含 `X` 中 `x` 的所有一元函数，其中 `K[x]` (`y`)=`K` (`x`, `y`)，并且对于 `X` 中的每个 `x` 和 `H` 中的 `f`，则 `f` (`x`)=<`f`, `K[x]`>。最后一个性质是实际的再生性质。

构建 RKHS 并将其与再生性质联系起来的严格方法的关键是 Riesz 表示定理（`RRT`）：对于具有内积 <·,·>: `H x H→C` 的希尔伯特空间 `H` 和 `H*` 中的任意连续线性泛函 `ϕ`![Equation](img/F000278si20.png)，存在 `H` 中唯一的向量 `f[ϕ]`![Equation](img/F000278si21.png) 使得 `ϕ(v) = < v, f[ϕ] >`![Equation](img/F000278si22.png)，对所有 `v` ∈ `H` 成立。此外，范数相等，即 ∥`f[ϕ]`∥ = ∥`ϕ`∥![Equation](img/F000278si23.png)。第一个范数在 `H` 中，第二个范数在 `H*` 中，其中‖`ϕ`![Equation](img/F000278si24.png)‖=inf {`C`> 0 使得 |`ϕ`![Equation](img/F000278si25.png) (`v`)|< `C`‖`v`‖ 对所有 `v` ∈ `H` 成立}。

回到 RKHS，存在线性求值泛函 `E[x]:H→C`![Equation](img/F000278si26.png)（或下一节中的 `R`），使得 `Ex = f(x)`![Equation](img/F000278si27.png) 有界。根据 `RRT`，每个有界线性泛函都由与 `H` 中唯一向量的内积给出；因此对于 `X` 中的每个 `x`，存在 `H` 中唯一的函数 `K[x]`![Equation](img/F000278si28.png) 使得对所有 `g` ∈ `H`，`g(x) = < g, K[x] >`![Equation](img/F000278si29.png)。根据 Putnam (2019)，`K[x]`![Equation](img/F000278si30.png) 被称为点 `x` 处的再生核。`H` 的再生核为 `K`: `X x X→H`，定义为 `K(x,y) = < k[y], k[x] >`![Equation](img/F000278si31.png)。此外，|`E[x]`|² = < `k[x]`, `k[x]` > = ∥`k[x]`∥² = `K(x,x)`![Equation](img/F000278si32.png)。因此，复数域上的再生希尔伯特空间 `H` 包含再生核 `K`，具有再生性质，<`K(., x)`, `f`>=`f(x)`，对所有 `x` ∈ `X` 和 `f` ∈ `H` 成立。此外，如果存在再生核，则 `H` 为 RKHS。即线性求值函数 `E[x]`![Equation](img/F000278si33.png) 有界。这里，`Ex = < K(.,x), f > = f(x)`![Equation](img/F000278si34.png)，因此根据 CBS 不等式，可得 |`Ex`|![Equation](img/F000278si35.png) 小于或等于 ∥`K(.,x)`∥∥`f`∥ = < `K(.,x)`, `K(.,x)` >^(1/2)∥`f`∥ = `K(x,x)^(1/2)`![Equation](img/F000278si36.png)‖`f`‖，因此 `Ex`![Equation](img/F000278si37.png) 有界且 |`E[x]`|![Equation](img/F000278si38.png) 小于或等于 `K(x,x)^(1/2)`![Equation](img/F000278si39.png)。




The kernel is self-reproducing and positive semidefinite. Use `<K(., x), K(., y)> = K(y, x) = <K(., y), K(., x)>*`. To see that the property, positive semidefiniteness holds, let `i` and `j` be in any finite set of positive integers. Then $\\left. \\left. {\\sum\\limits\_{i,j}a\_{i}^{\*}}a\_{j}K{({x\_{i},x\_{j}})} = {\\sum\\limits\_{i}a\_{i}^{\*}} < K\\left( {.,x\_{i}} \\right),{\\sum\\limits\_{j}{a\_{j}K{({.,x\_{j}})} > = < {\\sum a\_{i}^{\*}}K\\left( {.,x\_{i}} \\right)}},{\\sum\\limits\_{j}{a\_{j}K{({.,x\_{j}})}}} > = \\right\\|{\\sum\\limits\_{j}{a\_{j}K{({.,x\_{j}})}}} \\middle| |^{2} \\right.$![方程](img/F000278si40.png) which is greater than or equal to zero. This holds for all `a[i]`![方程](img/F000278si41.png) in `C` and `x[i]`![方程](img/F000278si42.png) in `X`. Kernels having these properties are sometimes called Mercer kernels. There is a converse to this result. It says whenever a symmetric positive semidefinite kernel `K` on a set `X` exists, then there is a unique Hilbert space `H` for which `K` produces a `RKHS`. This theorem is due to Moore-Aronszajn (Aronszajn, 1950). An outline of the results from this paper follows. For any `x` in `X`, let `K(x,.)` be an operator `K[x]`![方程](img/F000278si43.png). Define the set of all `K[x]`![方程](img/F000278si44.png) as `a`, the linear span for a vector space comprised of all linear combinations of such operators over `C`. An inner product can be defined for two such linear combinations as $< \\overset{n}{\\underset{i = 1}{\\sum^{}}}a\_{i}K\_{xi},\\overset{m}{\\underset{j = 1}{\\sum^{}}}a\_{j}K\_{yj} > = \\overset{n}{\\underset{i = 1}{\\sum^{}}}\\overset{m}{\\underset{j = 1}{\\sum^{}}}a\_{j}a\_{i}^{\*}K(x\_{i},x\_{j})$![方程](img/F000278si45.png). The properties of an inner product hold since the kernel is symmetric and positive definite. Let `H` be the completion of this inner product space. This shows that `H` consists of functions $f(x) = \\overset{n}{\\underset{i = 1}{\\sum^{}}}a\_{i}K\_{xi}(x)$![方程](img/F000278si46.png) such that the limit supremum as n goes to infinity and positive nonzero m> n, $\\left\\| \\overset{n + m}{\\underset{i = n}{\\sum^{}}}a\_{i}K\_{xi} \\right\\| = 0$![方程](img/F000278si47.png).

To see that the reproducing property holds, <f, $K\_{x} > = < \\sum\_{i = 1}^{n}{a\_{i}K\_{xi}\\left( x \\right),K\_{x} > = \\sum\_{i = 1}^{n}{a\_{i} < K\_{xi},K\_{x} > = \\sum\_{i = 1}^{n}{a\_{i}K\\left( {x\_{xi},x} \\right) = f\\left( x \\right)}}}$![方程](img/F000278si48.png). In order to determine that the Hilbert space is unique, let `H!` be another Hilbert space of functions having `K` as a reproducing kernel; then for every `x` and `y` in `X`, this other Hilbert space would have inner product  < `K[x i]`![方程](img/F000278si49.png), `K[x]`\>![方程](img/F000278si50.png), which again is `K(x[x i],x)`![方程](img/F000278si51.png). Using linearity, both inner products are the same on the span using all `K[x]`![方程](img/F000278si52.png). Also assume that the completion is performed as before, but for `H!`. This shows that `H` is a closed subset of `H!`. To prove that the inclusion goes the other way, use `f` in `H!`, and write `f` = `f[H]` + `f[H]^⊥`![方程](img/F000278si53.png), where `f[H]`![方程](img/F000278si54.png) is in `H` and `f[H]^⊥`![方程](img/F000278si55.png) is in `H^⊥`![方程](img/F000278si56.png). Because `K` is the reproducing kernel for both `H` and `H!`, it follows using inner products in `H!` that `f(x)` =  < `K[x]`![方程](img/F000278si57.png), `f` >  =  < `K[x]`![方程](img/F000278si58.png), `f[H]` >  +  < `K[x]`![方程](img/F000278si59.png), `f[H]^⊥` >  =  < `K[x]`![方程](img/F000278si60.png), `f[H]`\>![方程](img/F000278si61.png). Because,  < `K[x]`![方程](img/F000278si62.png), `f[H]^⊥`![方程](img/F000278si63.png)\>=0 and since `K[x]`![方程](img/F000278si64.png) is in `H`, it follows that the inner product of `K[x]`![方程](img/F000278si65.png) with `f[H]^⊥`![方程](img/F000278si66.png) in `H!` is zero. Therefore, the inner product in `H!` equals the inner product in `H`, showing that  < `K[x]`![方程](img/F000278si67.png), `f[H]` >  = `f[H]`![方程](img/F000278si68.png), and so `H=H!`.

If `H` is the space of functions from `X` to `C`, then a functional on this space can be found for `x` in `X`; write `E[x]f` = `f(x)`![方程](img/F000278si69.png). Given a set `X`, a `RKHS` `H` is the space of functions from `X` to `C`; the evaluation functionals for each `x` in `X`, `E[x]`![方程](img/F000278si70.png): `H→C`, are bounded, as originally stated.

## Example 19.2

The Hardy space is a Hilbert space, `H^∞`![方程](img/F000278si71.png); it consists of all analytic functions `f`, on the open unit disk, `D` in `C`. The mean square value of these functions on any circle of radius `r` is bounded as `r` approaches one from the interior. That is, ∥`f`∥²\=sup\[1/(2*π*)∫[0]^(2*π*)|*f*(*r**e*^(*i**θ*)|²*d**θ*\]<∞![方程](img/F000278si72.png), where the supremum is taken over all 0 <r <1 (Katznelson, 1976). As a result of Fatou’s theorem (Krantz, 2007), the analytic function can be extended to a function in `L²`![方程](img/F000278si73.png) on the boundary of the disk. It becomes the point-wise limit almost everywhere. The limit is always taken from the interior and never a tangential limit. Also, using the uniform norm for `f`, that is,‖`f`‖=max {`f` (z) such that z is in clos(`D`)}, `H^∞`![方程](img/F000278si74.png) is a commutative Banach algebra. For `f(z)` in `H^∞`![方程](img/F000278si75.png), $f\\left( z \\right) = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}}a\_{n}z^{n}$![方程](img/F000278si76.png) analytic in unit disk `D`, and such that $\\left. \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}} \\middle| a\_{n}|^{2} < \\infty \\right.$![方程](img/F000278si77.png). This is called the disk algebra.



# Hardy RKHS 构造

为了构造 Hardy RKHS，令 `L`: `H`^∞→`l`²![Equation](img/F000278si78.png)，其中 `L`(`f`) = (`a`[0] `a`[1]…)![Equation](img/F000278si79.png)。Hardy 空间 `H`^∞![Equation](img/F000278si80.png) 与 `l`²![Equation](img/F000278si81.png) 相同。因为 `L` 是线性的并且是 `H`^∞![Equation](img/F000278si82.png) 与 `l`²![Equation](img/F000278si83.png) 之间的等距同构，这意味着 `H`^∞![Equation](img/F000278si84.png) 是一个希尔伯特空间。利用形式幂级数内积，令 $f\\left( z \\right) = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}}a\_{n}z^{n}$![Equation](img/F000278si85.png) 和 $g\\left( z \\right) = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}}b\_{n}z^{n}$![Equation](img/F000278si86.png) 在单位圆盘 `D` 中解析。内积为 $< f,g > = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}}a\_{n}^{\*}b\_{n}$![Equation](img/F000278si87.png)。此后所有求和都从零到无穷。由 CBS 不等式，|∑^()``a``[`k`]^(\*)*b*[*k*]|²![Equation](img/F000278si88.png) 小于或等于 ∑|``a``[`k`]|²∑|``b``[`k`]|²![Equation](img/F000278si89.png)。因此对于 `D` 中每一个 `z`[0]![Equation](img/F000278si90.png)，`g`[`z`[`o`]](`z`) = ∑`z`[0]\*^(`n`)`z`^(`n`) = 1/(1−`z`[0]\*`z`)![Equation](img/F000278si91.png)。注意 <f, `g`[`z`[`o`]] >  = ∑`a`[`k`]`z`[0]\*^(`n`) = `f`(`z`[0])![Equation](img/F000278si92.png)，并且 |<f, `g`[`z`[`o`]]![Equation](img/F000278si93.png)\>| 小于或等于 ∥`f`∥∥`g`[`z`[`o`]]∥![Equation](img/F000278si94.png)。这些结果将导出一个求值泛函。诱导范数为 $\\left\\| f \\middle| |^{2} = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}} \\middle| a\_{n}|^{2} \\right.$![Equation](img/F000278si95.png)。为了看到每个幂级数同时收敛到 `D` 上的一个函数，考虑求值泛函 `E``z`![Equation](img/F000278si96.png)。目标然后是证明它是有界的，对于 `D` 中的 z，令 $E\_{z}\\left( f \\right) = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}}a\_{n}z^{n}$![Equation](img/F000278si97.png)。这是一个复数，所以 `E`[`z`]![Equation](img/F000278si98.png) 是一个泛函。绝对值 $\\left| E\_{z}\\left( f \\right) \\middle| = \\middle| \\sum\_{n = 0}^{\\infty}{a\_{n}z^{n}} \\right.$![Equation](img/F000278si99.png) | 小于或等于 $\\left. \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}} \\middle| a\_{n} \\right\\| z|^{n}$![Equation](img/F000278si100.png) 小于或等于 $\\left\\lbrack \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}} \\middle| a\_{n}|^{2}\\overset{\\infty}{\\underset{n = 0}{\\sum^{}}} \\middle| z|^{2n} \\right\\rbrack^{1/2}$![Equation](img/F000278si101.png) 即小于或等于 ‖f‖ \[1/(1−|z|²)\]^(1/2)。相应地，‖E[`Z`]‖ 被 \[1/(1−|z|²)\]^(1/2) 所限制，并且 `H`^∞![Equation](img/F000278si102.png) 是 `X`=`D` 上的一个 RKHS。对于 `D` 中一点 w 的核，在本例中是 Szego 核：`K`(`z`,`w`) = `K``w` = 1/(1+`w`*`z`)![Equation](img/F000278si103.png)。为了看到这一点，使用内积的定义对于 $g\\left( z \\right) = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}}w^{n\_{\\ast}}z^{n}$![Equation](img/F000278si104.png) 和 $f\\left( z \\right) = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}}a\_{n}z^{n}$![Equation](img/F000278si105.png)，两者都在 `H`^∞![Equation](img/F000278si106.png) 中。这里 $< g,f > = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}}w^{n}a\_{n} = f\\left( w \\right)$![Equation](img/F000278si107.png)。这意味着 g 是 `X`=`D` 中 w 的再生核，因此，对 $g = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}}w^{n\_{\\ast}}z^{n}$![Equation](img/F000278si108.png) 的级数求和给出 Szego 核 K(w, z)=1/(1−w\*z)。另外，‖E[`Z`]‖²\=K(z, z)=1/(1−z\*z)=1/(1−|z|²)。

对于 `X` 中的每一个 x，存在一个 `K`[`x`]![Equation](img/F000278si109.png) 在 H 中，使得对所有 f 在 H 中 <f, `K`[`x`]![Equation](img/F000278si110.png)\>=f(x)。函数 `K`(`x`,`y`) =  < `K`[`x`]![Equation](img/F000278si111.png), `K`[`y`]![Equation](img/F000278si112.png)\> 称为对应于 H 的核函数。K 是正定的，即对于 `X` 中所有有限的向量集合 v1… vj，格拉姆型矩阵是正定的。核函数 x 在 `X` 中的一个替代定义，以及特征映射 `Φ`:*X*→*l*²![Equation](img/F000278si113.png)，由 m 元组 (`Φ`[1]…`Φ`[`m`])![Equation](img/F000278si114.png) 给出，其中 ∑|`Φ`[`k`]|² < ∞![Equation](img/F000278si115.png)。在本例中， < `Φ`(`x`), `Φ`(`y`) >  = ∑`Φ``k` \* `Φ``k` = `K`(`x`,`y`)![Equation](img/F000278si116.png)。从 H²→`Φ``k` = `z`^(`k` − 1)![Equation](img/F000278si117.png)。每一个核函数都可以写成一个特征空间。

### 示例 19.3

对于定义域在 `D` 中的多项式向量空间，这里 `D` 是 C 中的单位圆盘，且在 L² 中的闭包是希尔伯特空间。对于在 `D` 中解析的 z^(`n`) 和 z^(`m`) 的相关内积由  < `z`^(`n`), `z`^(`m`) >  = ∫[`D`]`z`^(`n`[\*])`z`^(`m`)d**x**d**y** = ∫[0]^(2*π*)∫[0]¹r^(`n`)*e*^( − *i***n***θ*)*r*^(`m`)*e*^(*i***m***θ*)*r**d**r**d***θ*![Equation](img/F000278si118.png) 给出。它对于所有 m 不等于 n 的情况等于零，并且当它们相等时，<z^(`n`), z^(`m`)\>=*π*![Equation](img/F000278si119.png)/(n + 1)。

Bergman 核为 K(z, u)=1/\[*π* (1−z\* u)²\]，其中|z|<1 且|u|<1。这通过使用幂级数得出，并且所有求和都采用从零到无穷的指标变量。首先，注意 K (z, u)=∑ \[1/*π* (n + 1) z^(`n`)\* u^(`n`)\] 应该是再生核。形式上进行，考虑 `f`(`u`) = ∑`a***m* *u*^(`m`)![Equation](img/F000278si120.png)，在 `D` 中解析；然后 <K(z, u), f(u)>=<K(z, u), ∑ an u^(`m`)\>=∑ ∑an \[1/*π* (n + 1) <z^(`n`)\* u^(`n`), u^(`m`)\>\]=∑ ∑an \[1/*π* (n + 1) z^(`n`) <u^(`n`), u^(`m`)\>\]=∑an z^(`n`)\=f (z)。由于 ∑w^(`n`)\=1/(1−w)，对上式关于 w 求导得到以下结果：和 ∑n w^(`n`−1)\=1/(1− w)² 或和 ∑(n + 1) w^(`n`)\=1/(1−w)²。现在将 w 代入得到 ∑ \[1/*π* (n + 1) z^(`n`)\* u^(`n`)\]=1/(1−z\* u)²。

### 示例 19.4

阶为 q> 0 的 Mittag-Leffler 实值 RKHS 由 $F = \\left\\{ f\\left( z \\right) = \\sum\_{n = 0}^{\\infty}{a\_{n} z^{qn}} \\right.$![Equation](img/F000278si121.png) 中的函数组成，使得 $\\sum\_{n = 0}^{\\infty}\\left. {|a\_{n}|}^{2}\\Gamma\\left( {{qn} + 1} \\right) < \\infty \\right\\}$![Equation](img/F000278si122.png)，其中伽马函数为 *Γ*(*z*) = ∫[0]^∞*t*^(*z* − 1)*e*^( − *t*)*d**t*![Equation](img/F000278si123.png)。核由 Mittag-Leffler 函数给出：`K``q` = `E``q`, *t*^(`q*))![Equation](img/F000278si124.png)，其中 $E\_{q}\\left( z \\right) = \\overset{\\infty}{\\underset{n = 0}{\\sum^{}}}z^{n}/{\\lbrack{\\Gamma{({{qn} + 1})}}\\rbrack}$![Equation](img/F000278si125.png)。该函数是整函数并推广了指数函数。当 q=1 时，`E`1 = *e*^(*z*)![Equation](img/F000278si126.png)；此外，当 Bargmann-Fock 空间限制在正 x 轴上时，Mittag-Leffler 实值 RKHS 是其结果。另一方面，Mittag-Leffler 实值 RKHS 的复化将产生一个推广 Bargmann-Fock 空间的整函数 Mittag-Leffler 空间（Rosenfeld 等，2018）。

### 示例 19.5



## Drury-Arveson 空间

Drury-Arveson 空间是 `H[n]²`![Equation](img/F000278si127.png)，其中 `B` 为 `C^(n)`![Equation](img/F000278si128.png) 中的开单位球，对于 `n` 大于或等于二。当 `n=2` 时，该空间是 `B` 上解析函数的希尔伯特空间，具有再生核 `KZ=1/(1−<z, w>)`。它是一个 RKHS，其内积为 $< f,g > = {\\sum\\limits\_{ainZ\_{+}^{n}}{\\left( {a!/{|a|}!} \\right)b\_{a}c\_{a}}}$![Equation](img/F000278si129.png),* 其中 $f\\left( z \\right) = \\underset{ainZ\_{+}^{n}}{\\sum^{}}b\_{a}z^{a},g\\left( z \\right) = \\underset{ainZ\_{+}^{n}}{\\sum^{}}c\_{a}z^{a}$![Equation](img/F000278si130.png)。这是一个 Hardy RKHS 的推广（Jury 和 Martin, 2018）。

### 例 19.6

Bargmann-Fock 空间是全函数 `F` 的 RKHS，位于希尔伯特空间 `L²`![Equation](img/F000278si131.png) 中，具有高斯测度，即 `C^(n)`![Equation](img/F000278si132.png) 中的内积由  < `f`, `g` >  = `π`^( − `n`)∫`f`(`z`) \* `g`(`z`)*e*^(( − *|**z*|²))*d**z*![Equation](img/F000278si133.png) 给出。具体而言，$F = \\left\\{ f\\left( z \\right) = \\sum\_{n = 0}^{\\infty}{a\_{n}z^{n}} \\right.$![Equation](img/F000278si134.png)，使得 $\\sum\_{n = 0}^{\\infty}\\left. {|a\_{n}|}^{2}n! < \\infty \\right\\}$![Equation](img/F000278si135.png)。再生核为 `K(z,w)=e^(w*z*)`![Equation](img/F000278si136.png)，因此，`π^(−n)∫^()*e^(w*z*)*g(z)*e^((−|z|²))*d*z*=g(w)`![Equation](img/F000278si137.png)（Hall, 2013；Barbier, 2013）。

在上面提到的第二篇参考文献中，Jordan 代数被用于探索 Fock 空间以及 Bargmann 变换。在该参考文献中，所涉及的代数是实值对称矩阵。有趣的是，在本文中，在例 3.3) 中得到一个 Jordan 型代数。这发生在该例中使用实值对称矩阵的子代数时。一般而言，Jordan 代数是一个幺元、交换且通常非结合的代数，除 第 3.1 节 中提供的 MSA 恒等式外，还满足一个额外的约束。该等式约束涉及使用 `BINE` 或· 的乘法。它由

```
Jordan identity: BINE (u, BINE (BINE (u, u), v))=BINE (BINE (u, u), BINE (u, v)).
```

给出。再次，Jordan 恒等式：`u·(u²·v)=u²·(u·v)`。更简洁的记号可能更容易理解。该约束是一种关联型律。

### 例 19.7

根据之前的说明，考虑所有 2×2 实值对称矩阵的载体集合 `J`，`u` 和 `v`。使用 `BINE (u, v)=(u v + v u)/2`，如例 3.3) 中所示，则通过代入，不仅该结构是一个幺元、交换、非结合代数，而且它也是一个 Jordan 代数。

### 例 19.8

(Barbier, 2013)

再次参考例 3.3) 中给出的 `C` 上的原始幺元、交换、非结合代数 `M`。有趣的是，如果 `u` 在 `M` 中，且 `M` 中存在 `v` 使得 `BINE (u, v)=BINE (v, u)=I`，则称 `v` 为 `u` 的逆元。例如，使用下面提供的 `u` 和 `v`，以及 `u v` 和 `v u`，

$\\begin{matrix} {|\\begin{matrix} 1 & 0 \\\\ \\end{matrix}|} & {|\\begin{matrix} 1 & a \\\\ \\end{matrix}|} & {|\\begin{matrix} 1 & a \\\\ \\end{matrix}|} & {|\\begin{matrix} 1 & {- a} \\\\ \\end{matrix}|} \\\\ {|\\begin{matrix} 0 & {- 1} \\\\ \\end{matrix}|} & {|\\begin{matrix} a & {- 1} \\\\ \\end{matrix}|} & {|\\begin{matrix} {- a} & 1 \\\\ \\end{matrix}|} & {|\\begin{matrix} a & 1 \\\\ \\end{matrix}|} \\\\ \\end{matrix}.$

![Equation](img/F000278si138.png)

然后，`BINE (u, v)=(u v + v u)/2=the identity I`。对于 `C` 中 `a` 的每一个取值，`u` 都存在逆元。

## 19.3 关于 R 的再生核希尔伯特空间

函数 `k: X x X→R` 是核当且仅当存在希尔伯特空间 `H` 和映射 `Φ: X→H` 使得 `<Φ(x), Φ(y)>`。给定 `X` 和一个核函数、一个标量积以及一个映射 `Φ: X→H` 使得 `k(x,y)=<Φ(x), Φ(y)>`。为此，给定 `X` 和 `k`，存在一个映射，`Φ: X→H`，其中 `k(x,y)=<Φ(x), Φ(y)>`。这对 `X` 中的所有 `x` 和 `y` 都成立。RKHS 是一个函数空间。对于 `X` 中的任意 `x`，使用 `k[x]=Φ(x)=k(x,·)`，其中我们将 `x` 用作参数，并令 `k[x]: X→R`，因此 `k[x]` 是一个泛函。然而，`X` 中的每个点都被映射为一个函数。设 `S` 为 {`k[x]`，其中 `x` 在 `X` 中} 的值域或像。取所有线性组合的集合，即这些函数的张成使 `S` 成为一个向量空间。定义内积 `<k*x*, k[y]>=<k(x,·), k(y,·)>=k(x, y)`。该内积可以推广到任意函数 `f` 和 `g`，其中 `f=$\\sum\\limits\_{i}$![Equation](img/F000278si139.png) a[i] k(x[i],·)` 且 `g=$\\sum\\limits\_{j}$![Equation](img/F000278si140.png) b[j] k(y[j],·)`。这里，`< f,g > = \\underset{i,j}{\\sum^{}}a\_{i}b\_{j}k{({x\_{i},y\_{j},})}$![Equation](img/F000278si141.png)，并令 `S′` 为所得的内积空间。如果进行完备化，使每个柯西序列通过添加极限点而收敛，则得到一个 RKHS `H`。

核是自再现的且正半定的。使用 `<K(., x), K(., y)>=K(y, x)=<K(., y), K(., x)>*`。因此对于实数情形，核是对称的。

### 例 19.9

RKHS 最简单的例子之一是 `l²`![Equation](img/F000278si142.png)。这里，这些是从正整数 `N` 到实数的全部函数，并且是平方可和的。这些函数构成一个向量空间和一个希尔伯特空间，其诱导的范数平方为 `∥f∥²=∑|f(n)|²`![Equation](img/F000278si143.png)。评估泛函 `E[n]: l²→R`![Equation](img/F000278si144.png)，对于 `N` 中的每个 `n`，为 `En=f(n)=<f, e[n]>`![Equation](img/F000278si145.png)，其中 `e[n]`![Equation](img/F000278si146.png) 在 `l²`![Equation](img/F000278si147.png) 中满足 `en=1`![Equation](img/F000278si148.png)，并且对于 `N` 中的所有其他值，`en=0`![Equation](img/F000278si149.png)。此外，`|En|`![Equation](img/F000278si150.png) 小于或等于 `‖f‖`，因此它是有界泛函。例如，设 `f (n)=1/n`；则 `f` 在 `l²`![Equation](img/F000278si151.png) 中。作为评估泛函，注意 `E[3]=1/3,a n d‖f‖=π/6^(1/2)`![Equation](img/F000278si152.png)。

### 例 19.10

考虑仿射函数 `f(t)=a + bt` 的向量空间，其中 `a` 和 `b` 在 `R` 中。使用 `L²(0, 1)` 中的内积，即 `<f, g>=∫[0]¹f`![Equation](img/F000278si153.png) `g`。然后为了找到再生仿射函数的核 `K(t,s)`，即 `a + bt=∫[0]¹`![Equation](img/F000278si154.png) `(a + b s) K(t,s) ds`，首先使用 `1=∫[0]¹K(t,s)`![Equation](img/F000278si155.png) `ds`，然后使用 `t=∫[0]¹s`![Equation](img/F000278si156.png) `K(t,s) ds`。将 `K(t,s)=a(t) + b(t) s` 代入最后两个方程得到 `1=a(t) + b(t)/2` 且 `t=a(t)/2 + b(t)/3`。求解 `a(t)` 和 `b(t)` 得到 `1–2 t=−b(t)/6`，因此 `b(t)= −6 +12t` 且 `a(t)=4–6t`。核为 `K(t,s)=4–6 (s + t) +12st`。为验证结果，注意 `∫[0]¹`![Equation](img/F000278si157.png) `(a + b s) K(t,s) ds.=4a −3a −6at + 6at +2b −2b −3bt +4bt=a + bt`。

### 例 19.11

考虑 `L²`![Equation](img/F000278si158.png) 中的带限函数 `f(t)`，其傅里叶变换 `F(w)=∫^()[−∞]^∞f(t)e^(−i w t)d t`![Equation](img/F000278si159.png) 在 `[−a, a]` 上具有紧支撑，`a> 0`。因为 `F(w)` 也在 `L²`![Equation](img/F000278si160.png) 中且具有有限支撑，则 `F(w)` 也在 `L¹`![Equation](img/F000278si161.png) 中。因此 `f(t)` 具有众多性质；参见优秀参考文献（Goldberg, 1961）：



### 1) 逆傅里叶变换
`f(t)` = 1/(2`π`)∫^[−∞]^∞ `F(w)` `e^(i w t)` `d w` = 1/(2`π`)∫^[−a]^(a) `F(w)` `e^(i w t)` `d w` ![Equation](img/F000278si162.png)

### 2) 一致连续
对任意 `ϵ` ![Equation](img/F000278si163.png) > 0，存在 `δ` ![Equation](img/F000278si164.png) > 0 使得 |t−t′|<`δ` ![Equation](img/F000278si165.png) 蕴含 |`f(t)`−`f(t′)`|<`ϵ` ![Equation](img/F000278si166.png)。

### 3) 有界
|`f(t)`| 小于或等于 1/(2`π`)‖`F`‖[1]

### 4) Riemann-Lebesgue 引理
当 |t|→∞ 时的极限 蕴含 `f(t)`→0。

内积 `<f(t), g(t)>` = ∫^[−∞]^∞ ![Equation](img/F000278si167.png) `f*(x)` `g(x)` dx。 由于 `f` 是连续的，泛函 `Ex` = `f(x)` ![Equation](img/F000278si168.png) 被定义，且由 3) 可知它是 有界的。 所以 H 是一个 RKHS。 再现核是 `K(x,y)` = `sin[a(x−y)]/[π(x−y)]`。

sinc 函数 `g(t)` = `sin(t)/t` 的傅里叶变换 由 Cauchy 广义积分 lim[`R` → ∞]∫^[−R]^(R) `g(t)` `e^(−i w t)` dt = `π χ−1,1` ![Equation](img/F000278si169.png) 给出。 通过使用傅里叶变换的缩放和平移性质，可知 `K(x,y)` 的傅里叶变换是 `e^(−w i x)` ![Equation](img/F000278si170.png) `χ−a,a` ![Equation](img/F000278si171.png)。 最后，由 Plancherel 定理，`<K(x,y),f>` = ∫^[−∞]^∞ ![Equation](img/F000278si172.png) `K(x,y)* f(y)` dy = 1/(2`π`) ∫^[−a]^(a) `F(w)` `e^(i w x)` `d w` = `f(x)` ![Equation](img/F000278si173.png)。#

## 19.4 Mercer 定理

对于 `K`，在 `L²` ![Equation](img/F000278si174.png) 中，`K`: X x X→R 被称为正定核，前提是 `K` 是对称的。 即，`K(x, y)` = `K(y, x)`，且它是半正定的；这意味着对于 `L²` ![Equation](img/F000278si175.png) 中任意非零函数 `f`，有 ∫∫ ![Equation](img/F000278si176.png) `f(x)` `K(x,y)` `f(y)` dx dy 大于或等于零。 当 ∫∫ ![Equation](img/F000278si177.png) `f(x)` `K(x,y)` `f(y)` dx dy > 0 时它是正定的。 将假设 `K` 具有有限迹性质；这里 `K` 是连续的，并且积分 ∫∫ `K(x,y)²` ![Equation](img/F000278si178.png) dx dy 是有限的。

特征值和特征函数出现的情形与 Fredholm 型积分方程类似。 具体来说，`ϕ` ![Equation](img/F000278si179.png) 是核 `K` 的特征函数，如果 ∫ ![Equation](img/F000278si180.png) `K(x,y)` `ϕ(y)` dx = `λ ϕ(x)`。 这里，`λ` ![Equation](img/F000278si181.png) 是特征值。 该方程记为内积：`<K, ϕ>` = `λ ϕ`。 特征值和特征函数为学习机器中出现的误差提供估计。

Mercer 的一个定理指出，如果 `K` 是一个具有有限迹的正定核，则存在一个可数无限的特征函数集合，{`ϕ[i]`}，其对应的特征值为 `λ[i]` ![Equation](img/F000278si182.png)，其中 `λ[1]` ![Equation](img/F000278si183.png) 大于或等于 `λ[2]` ![Equation](img/F000278si184.png)，而 `λ[2]` 大于或等于 `λ[3]` ![Equation](img/F000278si185.png) … 大于零。 最后，`K(x,y)` = Σ_{n=1}^{∞} `λ_n` `ϕ_n(x)` `ϕ_n(y)` ![Equation](img/F000278si186.png)，并且可以证明收敛是绝对且一致的。 对于 `L²` 中的 `f`，![Equation](img/F000278si187.png) 特征函数可以被运用，其方式与傅里叶级数计算非常相似。 这里，∫ `f(y)` `ϕn` `d x` = < `f`, `ϕ[n]` > = `f[n]` ![Equation](img/F000278si188.png)，其中 `ϕ[n]` ![Equation](img/F000278si189.png) 是与核 `K` 相关联的特征向量，而 `λ[n]` ![Equation](img/F000278si190.png) 是对应的特征值。 在这种情况下，可以在核空间中创建涉及函数 `f` 和 `g` 的内积；该内积定义如下：`< f,g >` = Σ_{n=1}^{∞} (`f_n` ⋅ `g_n`) / `λ_n` ![Equation](img/F000278si191.png)。

特征映射可以通过 Mercer 定理的帮助创建。 这里，特征空间是 `l²` ![Equation](img/F000278si192.png)，并且特征映射：`X` → `l²` ![Equation](img/F000278si193.png)，且 `Φ(x)` = `λ^(1/2)` (`ϕ1`, `ϕ2`,…) ![Equation](img/F000278si194.png)。

只要且仅当 N 个特征值为正时，特征映射：`X` → `R^(N)` ![Equation](img/F000278si195.png)。 形成 `l²` ![Equation](img/F000278si196.png) 内积将提供核的公式，`< Φ(x),Φ(y) >` = Σ_{n=1}^{∞} (`λ_n^(1/2) ϕ_n(x)`) (`λ_n^(1/2) ϕ_n(y)`) = Σ_{n=1}^{∞} `λ_n ϕ_n(x) ϕ_n(y)` = `K(x,y)` ![Equation](img/F000278si197.png)。

### 例 19.12
这是一个第二类 Fredholm 型积分方程的实例，因为未知函数出现在积分之外，并且在被积函数的一部分之内：∫ ![Equation](img/F000278si198.png) `K(x,y)` `ϕ` ![Equation](img/F000278si199.png) (y) dy = `λ ϕ(x)`。 第一类 Fredholm 积分仅在被积函数内具有未知 `ϕ` ![Equation](img/F000278si200.png)。 无论如何，对于 ∫[y=0]¹ `x y ϕ(y)` dy = `λ ϕ(x)` + `x`，将找到 `ϕ(x)` 的解。 该积分方程可以通过对 `x` 求微分来求解。 相反，首先将整个方程乘以 `x`。 然后再次从零积分到一，这次关于 `x`。 然后假设 `ϕ` ![Equation](img/F000278si202.png) (y) 足够光滑以使 Fubini 定理成立，关于 `x` 的积分和关于 `y` 的积分可以互换。 因此，可得 ∫[y=0]¹ `y ϕ(y)` dy ∫[x=0]¹ `x²` dx = `λ` ![Equation](img/F000278si206.png) ∫[x=0]¹ `x` ![Equation](img/F000278si207.png) `ϕ(x)` dx + ∫[x=0]¹ ![Equation](img/F000278si208.png) `x²` dx。 这在积分并重新排列后变为 `[1/3−λ]` ∫[y=0]¹ ![Equation](img/F000278si209.png) `y ϕ(y)` dy = 1/3，所以 ∫[y=0]¹ ![Equation](img/F000278si211.png) `y ϕ(y)` dy = 1/[1–3 λ]。 将其代回原方程得到 `x/[1–3 λ]` = `λ ϕ(x)` + `x`，因此 `ϕ(x)` = `x/[λ (1–3 λ)]` − `x/λ`。 为了验证这是一个解，将其代入原方程得到 ∫[y=0]¹ `x` ![Equation](img/F000278si213.png) `y` {`y/[λ (1–3 λ)]` − `y/λ`} dy = `λ` {`x/[λ (1–3 λ)]` − `x/λ`} + `x`。 积分后得到 `x/[3 λ (1–3 λ)]` − `x/(3 λ)` = `x/[(1–3 λ)]` − `x` + `x` = `x/[(1–3 λ)]`。 但左边是 `x/[3 λ (1–3 λ)]` − `x/(3 λ)` = `x/(1–3 λ)` + `x/(3 λ)` − `x/(3 λ)`。 从而证明两侧相等。#

### 例 19.13



### 例 19.13
这可能是 Mercer 定理最重要的例子。对于实值函数 `f(x)`，周期为 2π，基本定义域为 \[−`π`, `π`\], 傅里叶级数将把此函数延拓到整个实数轴。在这种情况下，$f\\left( x \\right) = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}f\_{k}e^{ikx}$![方程](img/F000278si214.png`) 其中 `f`[`k`]![方程](img/F000278si215.png`) 是傅里叶系数。积分：${\\int^{}}\_{- \\pi}^{\\pi}f\\left( x \\right)e^{- inx}{dx} = {\\int^{}}\_{- \\pi}^{\\pi}\\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}f\_{k}e^{ikx}e^{- inx}{dx}$![方程](img/F000278si216.png`)，交换求和与积分，这给出 $\\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}f\_{k}{\\int^{}}\_{- \\pi}^{\\pi}e^{ikx}e^{- inx}{dx} = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}f\_{k}{\\int^{}}\_{- \\pi}^{\\pi}e^{ix(k - n)}{dx} = 2\\pi f\_{k}$![方程](img/F000278si217.png`) 当 n=k 时，且其他情况为零。因此，`f`[`k`] = 1/(2`π`)∫^()[ − `π`]^(`π`)`f`(`x`)`e`^( − `i``k``x`)`d``x`![方程](img/F000278si218.png`)。指数函数在 \[−`π`, `π`\ ] 上构成一个正交归一基。由于 `f(x)` 为实值，傅里叶系数共轭对称，`f`[`k`] \*  = `f`[ − `k`]![方程](img/F000278si219.png`)。如果假设 `f(x)` 为偶函数，则 `f`[`k`] = `f`[ − `k`]![方程](img/F000278si220.png`)。还假设核的形式为 `K(x, y)`=`K(x−y)` 并具有上述性质。设核的傅里叶表示为 $K\\left( x \\right) = \\sum\_{k = - \\infty}^{\\infty}{k\_{k}e^{ikx}}$![方程](img/F000278si221.png`)。
现在考虑 `L²`![方程](img/F000278si222.png`) 内积 $f\\left( x \\right) = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}f\_{k}e^{ikx}$![方程](img/F000278si223.png`) 和 $g\\left( x \\right) = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}g\_{k}e^{ikx}$![方程](img/F000278si224.png`)；则 $< f,g > = < \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}f\_{n}^{\*}e^{- inx},\\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}g\_{k}e^{ikx} > = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}f\_{n}^{\*}g\_{n}$![方程](img/F000278si225.png`)。接下来 `L²`![方程](img/F000278si226.png`) 的一个子空间 `H` 将通过定义内积 $< f,g >\_{H} = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}\\left( {f\_{n}^{\*}g\_{n}} \\right)/k\_{n}$![方程](img/F000278si227.png`) 成为一个 RKHS。`H` 中的诱导范数是 $\\left. \\left\\| f \\right\\| H = < f,f >\_{H} = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}\\left( {f\_{n}^{\*}f\_{n}} \\right)/k\_{n} = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}} \\middle| f\_{n}|^{2}/k\_{n} \\right.$![方程](img/F000278si228.png`)。因此在此 RKHS `H` 中，必须有 $\\left. \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}} \\middle| f\_{n}|^{2} \\right.$![方程](img/F000278si229.png`) 收敛。再生性质必须使用 $K\\left( x \\right) = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}k\_{k}e^{ikx}$![方程](img/F000278si230.png`) 来证明，因此 $K{({x - y})} = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}k\_{k}e^{ik{({x - y})}}$![方程](img/F000278si231.png`)。对于 `H` 中的函数 `f`，<K(, y), $f >\_{H} = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}{({k\_{n}e^{- iny}})}{\\ast f}\_{n})/k\_{n} = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}f\_{n}e^{iny} = f{(y)}$![方程](img/F000278si232.png`)。

### 例 19.14
本例将从前一个例子 例 19.13 继续。从那里，可以看到核 `K({x,y})` = `K({x - y})` = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}k\_{k}e^{ik{({x - y})}} = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}e^{ikx}k\_{k}e^{- iky}$![方程](img/F000278si233.png`)。类似地 `K(x - z)` = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}e^{ikx}k\_{k}e^{- ikz}$![方程](img/F000278si234.png`)。现在将看到核本身可以被再生：$\\begin{array}{l} {< K{({.,y})},K\\left( {.,z} \\right) >\_{H} = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}{\\lbrack{K{({.,y})}\*,K\\left( {.,z} \\right)}\\rbrack}/k\_{n} = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}{\\lbrack{{({k\_{k}e^{- iky}})} \\ast {({k\_{k}e^{- ikz}})}}\\rbrack}/k\_{n}} \\\\ {= \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}{\\lbrack{{({k\_{k}e^{kiy}})}{({k\_{k}e^{- ikz}})}}\\rbrack}/k\_{n} = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}{\\lbrack{({k\_{k}^{2}e^{kiy - ikz}})}\\rbrack}/k\_{n} = \\overset{\\infty}{\\underset{k = - \\infty}{\\sum^{}}}{({k\_{k}e^{kiy - ikz}})} = K{({y - z})}} \\\\ \\end{array}$![方程](img/F000278si235.png`)。最后，将确定特征映射。再次写出内积，$< K{({,y})},f >\_{H} = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}{({{({k\_{n}e^{- iny}})}{\*f}\_{n}})}/k\_{n}$![方程](img/F000278si236.png`)。使用特征映射 `ϕk` = (`k[n]`*e*^( − *i*n*x*))![方程](img/F000278si237.png`)。为了看到特征映射满足再生性质，使用内积 $< \\phi\_{k}\\left( x \\right),\\phi\_{k}{(y)} > = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}{({{({k\_{n}e^{- inx}})}{\*k}\_{n}e^{- iny}})}/k\_{n} = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}k\_{n}{({e^{inx}e^{- iny}})} = \\overset{\\infty}{\\underset{n = - \\infty}{\\sum^{}}}k\_{n}e^{in{({x - y})}} = K{({x,y})}$![方程](img/F000278si238.png`)。

## 19.5 谱定理
在 第 13.1 节 中已看到，有界算子具有非空紧谱，由特征值谱、连续谱或剩余谱组成。在有限维 `n` 中，每个矩阵只有特征值谱，其基数在 1 和 `n` 之间。这是代数基本定理的结果。在这种情况下，特征方程总是有复根。第 13 章 的主要结果之一是，对于自伴算子 `T`，在 `B(H,H)` 中，则所有特征值都是实数。对应于不同特征值的特征向量总是正交的。最后，特征值位于 `R` 的区间 [`m`, `M`] 中。此外，从数值范围的推导，`m`=inf <v, `T` v> 且 `M`=sup <v, `T`v>，两者都在 ‖v‖=1，v 在 `H` 上取值。最后剩余谱 `sprt` 为空；此外，对于更大的算子类，正规算子，剩余谱也是空的。



# 谱定理

再次为了激励涉及 `T` 的谱定理，`T` 是 `B(H,H)` 中的自伴算子，考虑载体集 `R^n`![Equation](img/F000278si239.png)。另外，让 `T` 是 `H` 上的矩阵，具有不同的特征值，即 `T` 具有非退化的离散谱。假设 `sppT` 中的值是有序的，即 `m = λ[1] < λ[2] < … < λ[n] = M`。相应的特征向量应被归一化，从而形成一个 `ON` 基。定义投影算子 `P[j]`![Equation](img/F000278si240.png)，使得 `P[j] v = < v[j], v > v[j] = a[j] v[j]`![Equation](img/F000278si241.png)，其中 `v[j]`![Equation](img/F000278si242.png) 是 `T` 的第 j 个特征向量且 `a[j]`![Equation](img/F000278si243.png) 在 `R` 中。由于 `H` 中的任意向量都是基元素的叠加，则 $v = \\overset{n}{\\underset{j = 1}{\\sum^{}}}a\_{j}v\_{j}$![Equation](img/F000278si244.png)，于是 $v = \\overset{n}{\\underset{j = 1}{\\sum^{}}}P\_{j}v$![Equation](img/F000278si245.png)。作为结果，$\\overset{n}{\\underset{j = 1}{\\sum^{}}}P\_{j}$![Equation](img/F000278si246.png) 可以被认为等于恒等元 `I`。这种情况下投影之和通常称为恒等式的分解。运算 `T v` 可以写成 ${Tv} = \\overset{n}{\\underset{j = 1}{\\sum^{}}}\\lambda\_{j}P\_{j}v$![Equation](img/F000278si247.png)。相应地，当 `v` 非零时，算子 $T = \\overset{n}{\\underset{j = 1}{\\sum^{}}}\\lambda\_{j}P\_{j}$![Equation](img/F000278si248.png)。

在此阶段，是时候从工程角度提供谱理论的本质了。基本上在这种情况下，将解释在谱 `spT` 上积分的含义是什么。首先暂时忘掉投影，并考虑位于每个特征值处的 delta 函数，`δ(t−λ[j])` 对于 `j=1, 2,…, n`。对于实数线上的连续函数 `f`，`f` 的一种谱积分是 $\\int\_{- \\infty}^{\\infty}{f\\left( t \\right)\\sum\_{j = 1}^{n}{\\delta{({t - \\lambda\_{j}})}}}{dt}$![Equation](img/F000278si249.png)。这里积分从负无穷到正无穷。它也可以只到有限的上界，例如 `R` 中的 `x`。在这种情况下，只有小于或等于 `x` 的特征值才会被包含在积分中。该积分运算从实数映射到实数；具体来说，它将 `T` 的谱映射到 `R`。

### Example 19.15

在 `C²`![Equation](img/F000278si250.png) 中，考虑自伴矩阵 `T`=

$\\begin{matrix} {|4} & {6|} \\\\ {|6} & {9|} \\\\ \\end{matrix}$

![Equation](img/F000278si251.png)

特征值是 `λ[1]=0` 和 `λ[2]=13`。因此出现一种谱积分，∫[−∞]^∞![Equation](img/F000278si252.png) `f(t)` [`δ(t) + δ(t−13)`] `dt` = `f(0) + f(13)`.#

回到实际的投影运算，`P[j] v=<v[j], v> v[j]=a[j] v[j]`，其中 `v[j]` 是 `T` 的第 j 个特征向量，且 `a[j]` 在 `R` 中。下一个例子的目标是实际求出这些投影算子。

### Example 19.16

参考前一个例子，并使用算子 `T` 以及相关的特征值。相应的 `ON` 特征向量是 `v[1]=1/13^(1/2) (−3 2)′` 和 `v[2]=1/13^(1/2) (2 3)′`。`C²` 中的投影算子使得对于 `C²` 中的任意 `v`，`P[j] v=<v[j], v> v[j]`，对于 `j=1, 2`。所以令 `P` 表示一般的投影矩阵，并令 `v` 为 `C²` 中的任意向量。下面示出的是 `P`，然后在 `P` 之后是二乘一列向量 `v`。最后，2×1 列向量乘积 `P v` 给出在下面的第三位置：

$\\begin{matrix} {|x} & {y|} & {|a|} & {|{\\text{xa} + \\text{yb}}|} \\\\ {|w} & {z|} & {|b|} & {|{\\text{wa} + \\text{zb}}|} \\\\ \\end{matrix}.$

![Equation](img/F000278si253.png)

首先，`P[1]`![Equation](img/F000278si254.png) 将被确定。但首先，只会找到该矩阵的顶行 `x` 和 `y`。将 `P[1] v`![Equation](img/F000278si255.png) 的第一个分量 `[x a + y b]` 设等于第一个特征向量与向量 `v` 的内积，全部乘以第一个特征向量的第一个分量，`1/13^(1/2)`![Equation](img/F000278si256.png) `[(−3 2) (a b)′]` `(-3/13^(1/2))`。形成上述内积并使 `a` 和 `b` 的系数相等，其中 `[x a + y b]= -3/13 [−3 a + 2 b]`。最后求解 `x` 和 `y` 得到 `x=9/13` 和 `y=−6/13`。该计算提供了 `P[1]`![Equation](img/F000278si257.png) 的第一行。

`P[1]`![Equation](img/F000278si258.png) 的第二行以类似的方式找到，但使用 `P v` 的底部分量以及第一个特征向量的底部分量。因此，`[w a + z b]=1/13^(1/2) [(−3 2) (a b)′] (2/13^(1/2))`。现在使 `a` 和 `b` 的系数相等，其中 `[w a + z b]=2/13 [−3 a + 2 b]`，并求解 `x` 和 `y` 得到 `w=−6/13` 和 `y=4/13`。以完全相同的方式，可以使用第二个特征向量执行两步程序来找到第二个投影矩阵 `P[2]`。`13 P[1]` 和 `13 P[2]` 如下所示。

$\\begin{matrix} {|9} & {{- 6}|} & {|4} & {6|} \\\\ {|{- 6}} & {4|} & {|6} & {9|} \\\\ \\end{matrix}$

![Equation](img/F000278si259.png)

注意 `P[1] + P[2]=I`。另外，$T = \\overset{2}{\\underset{j = 1}{\\sum^{}}}\\lambda\_{j}P\_{j}$![Equation](img/F000278si260.png)。这通过代入特征值和投影的值得出；这样做得到 `T = 0 P[1] + 13 P[2]`![Equation](img/F000278si261.png) #

继续投影算子，这些算子用于将 `T` 的谱映射到 `B(H,H)`。考虑由投影之和构成的阶梯型函数，$E\_{\\lambda} = \\underset{\\lambda > = \\lambda\_{j}}{\\sum^{}}P\_{j}$![Equation](img/F000278si262.png)。注意 `E[λ]=0` 对于 `λ < λ[1]`，并且对于 `λ`![Equation](img/F000278si263.png) 在区间 `[λ[1],λ[2])` 中，`E[λ] = P[1]`![Equation](img/F000278si264.png)；另外对于 `λ`![Equation](img/F000278si265.png) 在区间 `[λ[2], λ[3])` 中，`E[λ] = P[1] + P[2]`![Equation](img/F000278si266.png)。依此类推，直到 `λ`![Equation](img/F000278si267.png) 的值大于或等于 `λ[n]`![Equation](img/F000278si268.png)；然后 `E[λ] = I`![Equation](img/F000278si269.png)。算子 `E[λ]`![Equation](img/F000278si270.png) 可以被认为是一个阶梯型函数，在每个特征值处从右连续且具有 saltus `s[j]`![Equation](img/F000278si271.png)。也就是说，在每个特征值 `λ[j]`![Equation](img/F000278si272.png) 处，当 `λ = λ[j]`![Equation](img/F000278si273.png) 时，跳跃值是 `P[j] − P[j − 1] = s[j]`![Equation](img/F000278si274.png)。一般来说，`s[j] = E[λ[j]] − E[λ[j−]]`![Equation](img/F000278si275.png)，其中 `E[λ[j−]]=limit as λ→λ[j]`![Equation](img/F000278si276.png)，从左侧。

现在，将以下结论与示例 13.29 中说明的 Stieltjes 积分进行比较。对于实数线上的连续函数 `f`，`f` 的谱积分形式上由 $\\int\_{- \\infty}^{\\infty}{f\\left( t \\right)d E\_{\\lambda} = \\sum\_{j = 1}^{n}{f{(\\lambda\_{j})}{({P\_{j} - P\_{j - 1}})},P\_{0} = 0}}$![Equation](img/F000278si277.png) 给出。在引用的例子中，除了离散谱之外还有更多内容。随后将看到连续谱可以像该例子中涉及的计算那样建模。首先，将举一个关于谱上的积分的例子，其结果在 `B(H,H)` 中为算子值。

### Example 19.17




参考 例 19.16，$E_{\lambda} = \underset{\lambda > = \lambda_{j}}{\sum^{}}P_{j}$![Equation](img/F000278si278.png)。然后，E[*λ*]\=0 当 *λ*![Equation](img/F000278si279.png) <*λ*[1] = 0![Equation](img/F000278si280.png) 时，且当 *λ*![Equation](img/F000278si281.png) 在区间 [*λ*[1], *λ*[2])=\[0, 13) 中时，*E*[*λ*] = *P*[1]![Equation](img/F000278si282.png)，也当 *λ*![Equation](img/F000278si283.png) 大于或等于 *λ*[2]\=13 时，*E*[*λ*] = *P*[1] + *P*[2] = *I*![Equation](img/F000278si284.png)。描述 E[*λ*] 的最佳方式是将 R 分成三个区域：第一，所有 *λ*![Equation](img/F000278si285.png) <0，第二 *λ*![Equation](img/F000278si286.png) 在 \0, 13) 中，第三 *λ*![Equation 大于或等于 13。现在使用特征函数，*χ*[*A*]\=1 当 *λ*![Equation](img/F000278si288.png) 在 A 中时，否则等于零。点集 A 将被表示为点本身。然后 E[*λ*] 在每个区域中被描述为由四个函数组成的 2×2 矩阵；这些函数矩阵按顺序列出：
$\\begin{matrix} {|{0\\chi_{({- \\infty,0})}}} & {{0\\chi_{({- \\infty,0})}}|} & {|{9/13\\chi_{\\lbrack 0,13)}}} & {{- 6/13\\chi_{({0,13})}}|} & {|{1\\chi_{({13,\\infty})}}} & {{0\\chi_{({13,\\infty})}}|} \\\\ {|{0\\chi_{({- \\infty,0})}}} & {{0\\chi_{({- \\infty,0})}}|} & {|{- 6/13\\chi_{\\lbrack 0,13)}}} & {{4/13\\chi_{\\lbrack 0,13)}}|} & {|{0\\chi_{({13,\\infty})}}} & {{1\\chi_{({13,\\infty})}}|} \\\\ \\end{matrix}.$
![Equation](img/F000278si289.png)
在特征值处的 saltus 给出在 0 和 13；这些是跳跃值。用二阶函数矩阵表示，这些值由
$\\begin{matrix} {|{9/13\\chi_{0}}} & {{- 6/13\\chi_{0}}|} & {|{4/13\\chi_{13}}} & {{6/13\\chi_{13}}|} \\\\ {|{- 6/13\\chi_{0}}} & {{4/13\\chi_{0}}|} & {|{6/13\\chi_{13}}} & {{9/13\\chi_{13}}|} \\\\ \\end{matrix}.$
![Equation](img/F000278si290.png)
给出。
因此，在第一个特征值 *λ*[1]\=0 处，saltus 矩阵为 s[1]\=P[1]–0=P[1]，且上面的第一个矩阵为 P[1] *χ*[0]![Equation](img/F000278si291.png)。在 *λ*[2]\=13 处，saltus 矩阵为 s[2]\=P[2] – P[1]\=I−P[1]，且上面的第二个矩阵为 (I – P[1]) *χ*[13]![Equation](img/F000278si292.png)。saltus 矩阵与 saltus 函数矩阵是同构的；因此，在本例中，此后仅使用 saltus 矩阵。然后，∫[ − ∞]^∞*f*(*λ*)*d* *E*[*λ*] = *f*(0)*P*[1] + *f*(13)(*I*−*P*[1])![Equation](img/F000278si293.png)。该积分得到 B(H,H) 中算子的线性组合。它也可以写成 ∫[ − ∞]^∞*f*(*λ*)*d* *E*[*λ*] = *f*(0)*E*[*λ*[1]] + *f*(13)(*E*[*λ*[2]] − *E*[*λ*[1]]) = *f*(0)*E*[0] + *f*(13)(*E*[13] − *E*[0]) = *f*(0)*s*[0] + *f*(13)*s*[13]![Equation](img/F000278si294.png)。例如，若 *f*(*λ*) = *λ**e*^(*λ*)![Equation](img/F000278si295.png)，则 ∫[ − ∞]^∞*λ**e*^(*λ*)*d* *E*[*λ*]\=![Equation](img/F000278si296.png)
$\\begin{matrix} {|{4e^{13}}} & {{6e^{13}}|} \\\\ {|{6e^{13}}} & {{9e^{13}}|} \\\\ \\end{matrix}.\\#$
![Equation](img/F000278si297.png)
暂时假设 T 具有非退化的离散谱。f 的谱积分形式上由 ${\\int^{}}\_{- \\infty}^{\\infty}f\\left( \\lambda \\right)d E_{\\lambda} = \\overset{n}{\\underset{j = 1}{\\sum^{}}}f{(\\lambda_{j})}{({P_{j} - P_{j - 1}})},P_{0} = 0$![Equation](img/F000278si298.png) 给出。可以看出，该形式积分可以写成 saltus 算子的求和，即 ${\\int^{}}\_{- \\infty}^{\\infty}f\\left( \\lambda \\right)d E_{\\lambda} = \\overset{n}{\\underset{j = 1}{\\sum^{}}}f\\left( \\lambda_{j} \\right)s_{j}$![Equation](img/F000278si299.png)。此外，使用 $T = \\sum_{j = 1}^{n}{\\lambda_{j}P}$![Equation](img/F000278si300.png) 的额外谱表示为 $T = \\overset{n}{\\underset{j = 1}{\\sum^{}}}\\lambda_{j}s_{j}$![Equation](img/F000278si301.png)。上面的积分只是对求和的符号表示。为了获得积分的更常见含义，对 H 中任意 v 和 w 形成内积。也就是说，使用 $< v,T w > = \\overset{n}{\\underset{j = 1}{\\sum^{}}}\\lambda_{j} < v,s_{j}w >$![Equation](img/F000278si302.png)。在这种情况下，内积可以由真正的 Stieltjes 积分给出：<v, T w>=∫[ − ∞]^∞![Equation](img/F000278si303.png) *λ*![Equation](img/F000278si304.png) d g (*λ*)，其中 *g*(*λ*) =  < *v*, *E*[*λ*]*w*\>![Equation](img/F000278si305.png)。这里积分器 g 是一个实值阶梯型函数，这就是算子 T 的谱定理。

### 例 19.18
为了得到实际 Stieltjes 积分 ∫[ − ∞]^∞![Equation](img/F000278si306.png) *λ*![Equation](img/F000278si307.png)dg (*λ*)=<v, $T w > = \\sum_{j = 1}^{n}{\\lambda_{j} < v,s_{j}w >}$![Equation](img/F000278si308.png) 的一个简单例子，考虑 例 19.17。这里，特征值 0 和 13 以及算子 T、s[0] 和 s[13] 已指定。令 v=|0> 且 w=|1>。则 <v, T w>=(1 0) (6 9)′=6。另有 <v, s[13] w>=(1 0) (6/13 9/13)′=6/13，因此 $\\sum_{j = 1}^{2}{\\lambda_{j} < v,s_{j}w > = 0 + 13 \\cdot 6/13 = 6}$![Equation](img/F000278si309.png)。#
希尔伯特空间上自伴有界算子的谱定理几乎与上一个例子之前提到的完全相同。主要区别在于 saltus 被测度所取代。测度的详细描述见附录 A.2。如前所述，积分是谱上的 Stieltjes 积分。需要谱测度是因为连续谱以及由离散谱点簇产生的极限点也可以包含在谱积分中。这有点像例 13.29 中所示的积分过程。
对于自伴有界且谱为 spT 的 T，存在对应的谱测度 u。它满足，对于希尔伯特空间 H 中的所有 v 和 w，内积  < *v*, *T**w* >  = ∫[*s**p**T*]*λ**d* < *v*, *u*[*λ*]*w*\>![Equation](img/F000278si310.png)。
上述概念的推广导致投影值测度 PVM。这些测度的值为自伴投影。如 usual，测度定义在可测空间上。涉及 PVM 的谱定理将 PVM 与 B(H,H) 中的任意自伴算子 T 关联。这里 *T* = ∫*λ**d**E*[*λ*]![Equation](img/F000278si311.png)。积分被理解为实线上的 Stieltjes 或 Lebesgue 积分。关于 PVM 以及直接积分的严谨且解释清楚的描述可在 Hall (2013) 中找到。

### 例 19.19
设 T 为载体集 H=R² 上的有界自伴算子。此外，假设 |v> 是 H 中的单位向量且 f 在 BM 中，即 f 有界且可测。内积 <v|f(T) v> 是谱 spT=*σ*(T) 上的正泛函。因此存在与 |v> 关联的唯一谱测度 *u*[*v*]![Equation](img/F000278si312.png)。在紧集 *σ*(T) 上有以下等式，其中  < *v*|*f*(*T*)*v* >  = ∫[*σ*(*T*)]*f*(*λ*)*d**u*|*v*\>[*v*]![Equation](img/F000278si313.png)，且积分是 Lebesgue 型。取 |v>=2^(−1/2)(|0> + |1>)，它也在 R² 中，是列向量 2^(−1/2) (1 1)′。假设 f(t)=t² 且 T 由以下矩阵给出：
$\\begin{matrix} {|4} & {0|} \\\\ {|0} & {2|} \\\\ \\end{matrix}$
![Equation](img/F000278si314.png)



因此，`spT`=`sppT`=`σ`(`T`)={4, 2}。在这种情况下，`<v|f(T) v>`= `<2^(−1/2) (1 1)′, T² 2^(−1/2) (1 1)′>`=10。投影值测度为 ∫[`σ`(`T`)]`f`(`λ`)d`u`[`v`]|`v`> = \`f`(4)`u`[`v` + `f`(2)`u``v`\]|`v`>![方程](img/F000278si315.png)。这里，f(4)=16 且 f(2)=4；投影 `u``v`![方程](img/F000278si316.png) 和 u`v` 如下所示：

$\\begin{matrix} \\begin{matrix} {|1} & {0|} \\\\ {|0} & {0|} \\\\ \\end{matrix} & \\begin{matrix} {|0} & {0|} \\\\ {|0} & {1|} \\\\ \\end{matrix} \\\\ \\end{matrix}.$

![方程](img/F000278si317.png)

将这些值代入 ∫[`σ`(`T`)]`f`(`λ`)d`u`[`v`]|`v`> = 16`u``v`2^(−1/2)(11)′ + 4`u``v`2^(−1/2)(11)′ = 2^(−1/2)(164)′![方程](img/F000278si318.png)。注意本例中的 Borel 集在 {`ϕ`,{4},{2},{4,2}} = 2^(`σ`(`T`))![方程](img/F000278si319.png) 中。#

本节将以一个易于理解的最重要的谱定理结束。它适用于希尔伯特空间 `H` 中的自伴紧算子 `T`。利用 `N`，即 `T` 的零空间，则 `N`^⊥![方程](img/F000278si320.png) 的维数至多可数，并具有 `T` 的特征向量的 `ON` 基 `ϕ`[`n`]，`n` = 1, 2, …![方程](img/F000278si321.png)。这里，`T``ϕ`[`n`] = [`n`]`ϕ`[`n`]![方程](img/F000278si322.png)，其中对每个 `n` 都有一个非零特征值。此外，如果 `N`^⊥![方程](img/F000278si323.png) 不是有限的，则特征值 `λ`[`n`]![方程](img/F000278si324.png) 趋于零，即 `λ`[`n`],→0![方程](img/F000278si325.png) 当 `n`→∞ 时，且这是唯一的聚点。此外，非零特征值的特征空间是有限维的。

由于非零特征值在复平面上是孤立点，柯西积分定理给出一个 Riesz 投影 `E`(`λ`)。这是通过在 `SCROC` 上积分实现的，仅包围单个特征值 `λ`![方程](img/F000278si326.png)。`SCROC` 是一个简单闭可求长定向曲线。这些算子是谱投影，并且 `E`(`λ`)·`E`(`μ`)=`E` (`λ`) 当 `λ`=`μ` 时，否则为零（Conway, 1990）。

## 19.6 Riesz-Markov 定理

设 `X` 是一个局部紧 Hausdorff 空间，具有 `C`⁰(`X`,`R`) 中的态 `S`![方程](img/F000278si327.png)。则存在唯一的 Borel 概率测度 `u`[`S`]![方程](img/F000278si328.png)，使得对所有 `f` ∈ `C`⁰(`X`,`R`)![方程](img/F000278si329.png) 都有 `S`(`f`) = ∫[`X`]`f` d `u`[`S`]![方程](img/F000278si330.png)。此外，泛函 `S`(`f`) 可以被视为态 `S` 中可观测量 `f` 的期望值。因此，`S`(`f`) 可以被认为是平均值。同样条件方差 `σ`[`S`]² = `S`((`f`−`S`(`f`))²) = `S`(`f`²) − `S`(`f`)²![方程](img/F000278si331.png)。

### 例 19.20

海森堡不确定性原理：对于固定态 `S`，以及可观测量 `p` 和 `q`，`σ``S``σ``S`![方程](img/F000278si332.png) 大于或等于 `h`/2。这里 `p` 和 `q` 分别表示位置和动量。在不失一般性的情况下，假设 `p` 和 `q` 的均值为零。因此，`σ`[`S`]²(`p`)`σ`[`S`]²(`q`) = `S`(`p`²)`S`(`q`²)![方程](img/F000278si333.png)。由于所有可观测量都是自伴的，因此对所有 `a`、`b` ∈ `R` 有 (`a``p`+i`b``q`)*=`a``p`−i`b``q`。由于态是正的，表达式 `S`[( `a``p`−i`b``q`) (`a``p`+i`b``q`)]=`a`² `S`(`p`²)−i`b``a``S`(`q``p`)+i`a``b``S`(`p``q`)+`b`²`S`(`q`²) 大于或等于零。涉及 `i` 的项可以用对易子表示，即可以写成 i`a``b``S`([`p`, `q`])。设 `v` 为列向量 (`a` `b`)′，且 `M`=

$\\begin{array}{ll} \\left| S\\left( p^{2} \\right) \\right. & \\left. 1/2S\\left( {i\\left\\lbrack {p,q} \\right\\rbrack} \\right) \\right| \\\\ \\left| 1/2S\\left( {i\\left\\lbrack {p,q} \\right\\rbrack} \\right) \\right. & \\left. S\\left( q^{2} \\right) \\right| \\\\ \\end{array}.$

![方程](img/F000278si334.png)

由此，前述不等式可以写成 `v`′ `M` `v`，它大于或等于零，因此 `M` 是正定的。因此，`M` 的行列式大于或等于零，即 `S`(`p`²)`S`(`q`²) − 1/4(`S`(`i`[`p`,`q`]))²![方程](img/F000278si335.png) 大于或等于零。因此，`S`(`p`²)`S`(`q`²)![方程](img/F000278si336.png) 大于或等于 1/4(`S`(`i`[`p`,`q`]))²![方程](img/F000278si337.png)。最后，见第 8.7 节，其中 [`p`, `q`]=i`h`，因此 `σ``S``σ``S`![方程](img/F000278si338.png) 大于或等于 `h`/2。这就是海森堡不确定性原理。#

## 19.7 一些不可分希尔伯特空间

在本文档中，所有希尔伯特空间都被假定为可分的。也就是说，希尔伯特空间具有可数稠密子集，因此它具有 Schauder 基。不可分希尔伯特空间在凝聚态物理中使用。在量子场论中，去掉曲率的 Poincare 不变性会导致不可分希尔伯特空间。此外，在 第 14.10 节 中，已证明 Weyl 版本的 CCR C\* 代数不是可分的。该 C\* 代数在对称 Fock 空间上得到忠实表示。

下面给出另外几个不可分希尔伯特空间的例子。在下一节中，关于可分希尔伯特空间的最重要事实之一被证明。

### 例 19.21

考虑 `l`²(`R`)![方程](img/F000278si339.png) 的一个修改，即所有收敛平方可和实数序列的希尔伯特空间。设 `f`: `R`→`R`，其中 `f`(`x`)=0 对所有 `x` 成立，除去一个可数集，这里 `f`(`x`)² 对所有 `x` 的和![方程](img/F000278si340.png) 是有限的。那么实数 `R` 中单个点 `p` 或 `q` 的特征函数，`p` 不等于 `q`，分别记为 `χ`[`p`]![方程](img/F000278si341.png) 和 `χ`[`q`]![方程](img/F000278si342.png)。设 `f`(`x`)=`g`(`x`)=0，除非 `f`(`x`) = `χ`[`p`]![方程](img/F000278si343.png) 且 `g`(`x`) = `χ`[`q`]![方程](img/F000278si344.png)。这些函数在此希尔伯特空间中，且它们的各自平方和为一。然而它们之间的距离是 ${d\\left( f\\left( x \\right),g\\left( x \\right) \\right) =}\\left\\lbrack {{the}{sum},\\underset{x}{\\sum^{}}\\left( {f\\left( x \\right) - g\\left( x \\right)} \\right)^{2}} \\right\\rbrack^{1/2} = \\left\\lbrack \\left( f\\left( p \\right) - g\\left( p \\right) \\right)^{2} + \\left( f\\left( q \\right) - g{\\left( q \\right))} \\right.^{2} \\right\\rbrack^{1/2} = \\left\\lbrack \\chi\_{p}^{2} + \\chi\_{q}^{2} \\right\\rbrack^{1/2} = 2^{1/2}$![方程](img/F000278si345.png)。这个空间不可能有可数稠密子集。因为对于 `f` 处半径小于 2^(1/2)![方程](img/F000278si346.png) 的任意开集，它仅包含 `f` 本身，且存在不可数多个这样的点。#

### 例 19.22

所有 Bohr 几乎周期函数构成的空间形成一个不可分希尔伯特空间。内积 <`f`, `g`> 等于极限 `T`→∞![方程](img/F000278si347.png)，1/(2 `T`) ∫[−`T`]^(`T`)![方程](img/F000278si348.png) (`f`(`t`) * `g`(`t`)) dt。对于 `R` 中非零的 `w`，不可数集 {`e`^(`i``w``t`)}![方程](img/F000278si349.png) 是该空间中一组标准正交向量族。它们是周期性的，而且极限 `T`→∞,1/(2`T`)∫[−`T`]^(`T`)`e`^(−`i``a``t`)`e`^(`i``b``t`)d`t` = 1![方程](img/F000278si350.png) 当 `a`=`b` 时等于 1，否则等于零。完备化是一个不可分希尔伯特空间。#

## 19.8 可分希尔伯特空间与 `l`²![方程](img/F000278si351.png) 等距同构

每个可分希尔伯特空间 `H` 与 `l`²![方程](img/F000278si352.png) 等距同构这一事实的证明在以下八个步骤中给出，并且在 `SCALAR` 为实数时证明。




# 等距同构证明

## 1) 由于 `H` 可分，它具有 Schauder 基：`{e[n]}` ![方程](img/F000278si353.png)，`n`=1, 2, ….

## 2) 对于 `H` 中的 `v` 以及满足 `T`: `H` → `l²` ![方程](img/F000278si354.png) 的 `T`，令 `T(v)` 为 `v` 与正交归一基 `{e[n]}` ![方程](img/F000278si355.png) 的内积构成的序列。记该序列为 `(e[n])` ![方程](img/F000278si356.png)。于是，`T(v)` = < `v`, `e[1]` >, < `v`, `e[2]` >, … = (< `v`, `e[n]` >) ![方程](img/F000278si357.png)。

## 3) 利用下面给出的 Bessel 不等式可知 `T(v)` = (< `v`, `e[n]` >) ![方程](img/F000278si358.png) 属于 `l²` ![方程](img/F000278si359.png)。
Bessel 不等式对任意内积空间成立。它涉及正交归一基 `{e[n]}` ![方程](img/F000278si360.png) 以及 `v`。首先，以下求和从 `n`=1 到 `N`，‖`v`−sum, ∑(<`v`, `e[n]`> `e[n]`)‖² = < `v` − sum, ∑(<`v`, `e[n]`> `e[n]`) ![方程](img/F000278si361.png), (`v`−sum,∑(<`v`, `e[n]`> `e[n]`) > = ‖`v`‖² − sum, ∑| < `v`, `e[n]` > |² ![方程](img/F000278si362.png) 大于或等于零，因此 ‖`v`‖² ![方程](img/F000278si363.png) 大于或等于 sum, ∑| < `v`, `e[n]` > |² ![方程](img/F000278si364.png)。接下来令 `N` → ![方程](img/F000278si365.png) ∞ ![方程](img/F000278si366.png)。这表明 ‖`T(v)`‖[2] ![方程](img/F000278si367.png) <∞ ![方程](img/F000278si368.png)，所以 `T(v)` = (<`v`, `e[n]`>) ![方程](img/F000278si369.png) 属于 `l²` ![方程](img/F000278si370.png)。从此以后，所有极限和指标均从 `n`=1 到 ∞ ![方程](img/F000278si371.png)。

## 4) 接下来为证明 `T` 是线性的，对于 `H` 中的 `v` 和 `w` 以及 `R` 中的 `a`，注意到 `T(v + a w)` = (<`v + a w`, `e[n]`>) = (<`v`, `e[n]`> + `a` <`v`, `e[n]`>) = (<`v`, `e[n]`>) + `a` (<`v`, `e[n]`>) = `T(v)` + `a` `T(w)`

## 5) 使用正交归一基 `{e[n]}`，唯一的表示 `v` = sum, ∑ ![方程](img/F000278si372.png) (<`v`, `e[n]`> `e[n]`) 成立。求和从 1 到 ∞ ![方程](img/F000278si373.png)，‖`v`‖² = <sum, ∑ ![方程](img/F000278si374.png) (<`v`, `e[n]`> `e[n]`), sum, ∑ ![方程](img/F000278si375.png) (<`v`, `e[k]`> `e[k]`)> = sum, ∑ ![方程](img/F000278si376.png) (<`v`, `e[k]`>² <`e[k]`, `e[k]`>) = sum, ∑ ![方程](img/F000278si377.png) (<`v`, `e[k]`>²) = ‖`T(v)`‖²。这表明 `T` 有界，而且它是等距映射。

## 6) `T` 是 1–1，因为如果 `T(v)` = `T(w)`，则 (<`v`, `e[n]`>) – (<`w`, `e[n]`>) = 0，且 (<`v` – `w`, `e[n]`>) = 0，并且由于对所有 `n`，<`v` – `w`, `e[n]`> = 0；这意味着 `v` = `w`。

## 7) `T` 是满射，因为如果 (`z[n]`) 是 `l²` 中的任意元素，则考虑 `z` = sum, ∑ ![方程](img/F000278si378.png) (`z[n]` `e[n]`)；将会看到 `z` 属于 `H` 且 `T(z)` = (`z[n]`)。二范数平方，‖`z`‖² = <`z`, `z`> = sum, ∑ ![方程](img/F000278si379.png) (|`z[n]`|²) <∞ ![方程](img/F000278si380.png)。所以，`T(z)` = (<`z`, `e[k]`>) = (<sum, ∑ ![方程](img/F000278si381.png) (`z[n]` `e[n]`), `e[k]`>) = (`z[k]` ‖`e[k]`‖) = (`z[k]`)。

## 8) 最后，利用有界逆定理，参见附录 A.6。也就是说，如果 `A`: `X` → ![方程](img/F000278si382.png) `Y`，其中 `X` 和 `Y` 为 Banach 空间且 `A` 为 1–1 且满射，则 `A^(-1)`: `Y` → ![方程](img/F000278si383.png) `X` 也是有界的。由于所有这些条件都适用，`T` 具有有界逆。因此，`T` 是 `H` 与 `l²` 之间的等距同构。

## 参考文献

* Aronszajn, 1950 Aronszajn N. 再生核理论。*Trans Amer Math Soc.* 1950;.
* Barbier, 2013 Barbier S. *利用 Jordan 代数的量子力学 Segal-Bargmann 变换* Universiteit Gent 2013;.
* Conway, 1990 Conway J. GTM *泛函分析教程* Springer 1990;.
* Goldberg, 1961 Goldberg R. *傅里叶变换* Cambridge University Press 1961;.
* Hall, 2013 Hall B. *数学家的量子理论* Springer 2013;.
* Jury and Martin, 2018 Jury M, Martin R. *Drury-Arveson 空间的极值乘子* University of Florida 2018;.
* Katznelson, 1976 Katznelson Y. 978-0-486-63331-2 *调和分析导论* Dover Pub 1976;.
* Krantz, 2007 Krantz S. 全纯函数的边界行为：整体与局部结果。*Asian J Math.* 2007;11.
* Putnam, 2019 Putnam, I., C\* 代数的讲义, 2019.
* Rosenfeld et al., 2018 Rosenfeld, J., Russo, B., Dixon, W., 整个函数和分析函数的 Mittag Leffler 再生核希尔伯特空间。J. Math., Elsevier, 2018; 463: 576-592.

## 附录 A

### 环绕数字信号的希尔伯特空间

所有环绕数字有界向量和有界矩阵的集合都构成希尔伯特空间。内积在它们零集的交集上求值。对于空交集，该积为零。完备性利用 Cauchy 序列 (`CSs`) 得出。在这些情况下，已证明它们形成有界向量或有界矩阵 `f[n]` 的 `CSs`。目标是证明 `f[n]` 收敛，设收敛到 `f`，在一范数下；其他范数以相同方式得出。首先要注意的是，如果 `f[n]` → `f`，则 `f[n]` 内的每个元素 `v[n]` 将收敛到设为 `v`。元素 `v[n]` 是有界向量内的元组，或有界矩阵 `f[n]` 内的矩阵项 `v[n]`。这种收敛成立是因为 || `f[n]` − `f` || 大于或等于特定项值差 | `v[n]` − `v` |。反之，如果每个元组元素都收敛，这意味着 `f[n]` 收敛，因为构成有界向量或有界矩阵结构的有元组数量是固定的有限数。如前所述，以下将采用一范数，但结果对任意范数均成立。事实序列已证明（Apostle, 1974; Rudin, 1987）：
1. 每个实数序列都有单调子序列。
2. 每个 `CS` 都有界。
3. 有界实数单调序列总是收敛。
4. 每个实数 `CS` 都收敛。
5. 环绕有界向量和矩阵的空间是完备的，因此构成 Banach 空间也是希尔伯特空间。
6. 每个实数序列 `v[n]` 都有单调子序列。这一结果通过使用峰值得出。峰值 `v[m]` 是序列中的一个元素，使得 `v[m]` 大于序列中 `n` > `m` 的所有元素 `v[n]`。如果存在无限多个峰值，则这是一个由峰值组成的子序列且严格递减。另一方面，假设仅存在有限个峰值。令 `v[m]` 为最后一个峰值。然后从第 `m+1` 个值 `v[m+1]` ![方程](img/F00014Xsi1.png) 开始在序列中。该值必须小于或等于序列中以下所有值，除了有限个，否则它也将是一个峰值。利用归纳法，令 `v[k]` 为序列中 `k` > `m+1` 的成员，且 `v[k]` 大于或等于 `v[m+1]` ![方程](img/F00014Xsi2.png)。现在 `v[k]` 不是峰值，因此存在值 `p` > `k` 使得 `v[p]` 大于或等于 `v[k]`。继续这样，序列：`v[m+1]` ![方程](img/F00014Xsi3.png) `v[k]` `v[p]` … 形成 `v[n]` 的子序列，且单调递增。

例 A.1
序列：1 0 1/2 0 1/3 0 1/4 …。该序列在每个奇数位置都有峰值，因此得到单调递减子序列，1 1/2 1/3 1/4 …。

例 A.2




考虑实数序列：3, 1, 2, −1*, −1/2, −1/3, −1, −1, −1/2**, −1/3, −1/4,…, −1/`n`,.… 则峰值存在于值 3 和 2，且仅此而已；从这一点开始，之后不再有峰值。从 `v[4]` 开始，值 −1* 小于或等于序列中所有后续项。元素 `v[9]`=−1/2** 大于 `v[4]`=−1*。此外值 `v[9]`=−1/2** 不是一个峰值，因此大于 9 的索引值将被视为单调递增序列的一部分。由此可找到 `v[n]` 的单调递增子序列。这里，该子序列为 `v[m+1]` ![方程](img/F00014Xsi4.png) `v[k]` `v[p]` …,=`v[4]` `v[9]` `v[10]` …=−1* −1/2** −1/3 …−1/`n` …

## 2. 接下来，假设 `v[n]` 是 CS 则容易看出它是 有界的
这可以看出，因为对于任意正整数 `n`，`k > N-1`，其中 `N` 是固定的，则 `| v[n]–v[k] |` 小于或等于 ![ε](img/epsi_1013.png)。特别地，然后根据三角不等式，`| v[n] |−| v[N] |` 小于或等于 `| v[n]–v[N] |`，因为 `| v[n] |=| (v[n]–v[N])+v[N] |` 小于或等于 `| (v[n]–v[N]) | + | v[N] |`。因此，`| v[n] |` 小于或等于 `| v[N] | +` ![ε](img/epsi_1013.png)，对于所有 `n > N-1`，而对于 `n < N`，`n` 的取值是有限的。总体界限将采用有限个值的最大值，即使用 `max(| v[N] | +` ![ε](img/epsi_1013.png)`, | v[1] |, | v[2] |, …, | v[N-1]|)`。

## 3. 在下面，将证明有界的实数单调序列 `v[n]` 总是收敛
假设序列 `v[n]` 是单调递增的。则令 `s = v[n]` 的上确界；则对于每一个 ![ε](img/epsi_1013.png)>0，存在 `N >0`，使得 `v[N] > s -` ![ε](img/epsi_1013.png)。这是正确的，因为否则，`s -` ![ε](img/epsi_1013.png) 将是 `v[n]` 的上确界。利用单调性意味着 `v[n]` 大于或等于 `v[N]`，并且对于 `n > N`，`s -` ![ε](img/epsi_1013.png) `< v[n] < s +` ![ε](img/epsi_1013.png)，这就是序列收敛的定义，从而证明 `v[n]` 收敛到 `s`。

## 4. 接下来，证明每个实数的 CS 都收敛
注意到 `| v[n]–v[k_i] | <` ![ε](img/epsi_1013.png) 对于 `v[k_i]` 成立，其中 `v[k_i]` 是 `v[n]` 的单调子序列，因为序列是 CSs。利用三角不等式得到 `| v[n]−s |`，它小于或等于 `| v[n]–v[k_i] | + | v[k_i]−s |`。对于足够大的 `N`，且 `n, k_i > N`，由于第一个表达式小于 ![ε](img/epsi_1013.png) 因为它是 CS，且第二个绝对值项也小于 ![ε](img/epsi_1013.png)，利用上文 (3) 得到 `| v[n]−s | < 2` ![ε](img/epsi_1013.png)。

## 5. 最后，对于 `Wn` 中的有界向量
设 `f[j] = (a[j] b[j] … d[j])[k]^(Wn)` ![方程](img/F00014Xsi5.png)。令 `f[j]` 构成有界向量的 CS。所以对于足够大的 `N` 且 `j, m > N`，则有 `|| f[j]–f[m] || <` ![ε](img/epsi_1013.png)。

使用一范数 `|| f[j]–f[m] ||[1] = | a[j]–a[m] | + | b[j]–b[m] | + … + | d[j]–d[m] |` 显示每个元组本身都是一个 CS。由于这些是实数序列，它们都收敛。设 `a[j] → a`，`b[j] → b`，…，`d[j] → d`。则，`f[j] → f = (a b … d)[k]^(Wn)` ![方程](img/F00014Xsi6.png)。对于有界绕环矩阵，完全相同的证明也成立。这些结构因此是 Banach 空间。

二范数也提供了相同的结论。因此，这些结构构成 Hilbert 空间。此外，上面的证明对复值绕环有界向量和有界矩阵也成立。验证只需使用复数量的实部和虚部。

## 参考文献
* Apostle, 1974 Apostle T. *数学分析* 2ed. Pearson Pub Co 1974;.
* Rudin, 1987 Rudin W. 0070542341 *数学分析原理* Mc Graw Hill 1987;.

# 附录 B
## 多值代数用于可测空间和测度空间的描述

测度论在多值代数 MSA 中的公理化框架本质上与通常在实分析和积分理论中使用的模型相同。然而，在 MSA 描述的情况下做了一点修改。对于可测空间的概念，首先取 `X` 为非空集合。令 `S` 为 `X` 的所有子集的集合。即 `S = 2^(X)`。令 `M` 为构成 `X` 子集的 σ 代数的类。这些是被指定并且是 `S` 中的特殊子集。可测空间通常写成 `(X, M)`。多值图在 图 B.1A 中说明了可测空间描述中涉及的两个类型。接下来给出这些类型以及描述和缩写。类型如下：

![图 B.1 (A) 可测空间和 (B) 测度空间。](img/F000035bm01-9780443136979.jpg)

图 B.1 (A) 可测空间和 (B) 测度空间。

`SUBSET-S`，即 `X` 的所有子集，因此 `S = 2^(X)`。

`M-SET-E`，即稍后描述的 σ 代数中的所有集合，并且是来自 `S` 的特殊元素。`M-SET` 是可测集合的缩写。

可测空间中存在一个单一的一元函数，它被称为 σ 代数或 σ 域，`σField`。它满足

`σField: SUBSET → M-SET`。

![方程](img/F000035si2.png)

该函数和相关类型更易于用 `σF: S → M` 描述。它是一个部分（恒等）函数，缩写为 `σF`。它选择 `M` 中哪些元素或子集被称为可测的。这类似于域结构的逆函数。后者部分算子选择非零元素使其具有逆。请注意在多值图中，`σF` 的箭头是虚线，表示部分运算。

等式恒等式必须对 `M` 中的所有元素 `E` 成立：

1. 空集 `E = ϕ` 在 `S` 中必须在 `M` 中，即 `σF(ϕ) = ϕ`。
2. 对于满足 `σF(E) = E` 的 `E`，`X` 中 `E` 的补集，即 `X−E`，`σF(X−E)` 也在 `M` 中，所以 `σF(X−E) = (X−E)`。
3. 如果 `E[k]` 在 `S` 中，且 `σF(E[k])` 在 `M` 中，其中 `k = 1, 2, 3, …`，即 `σF(E[k]) = E[k]`，则 `σF(所有 E[k] 的并集) = 所有 E[k] 的并集`。

请注意，通过使用 (1) 和 (2)，`X` 也是一个可测集合，即 `σF(X) = X`。

根据 De Morgan 定律，对于 `σF(E[k])` 在 `M` 中，`σF(所有 E[k] 的交集)` 也在 `M` 中。点 (3) 连同该结果说明 `(X, M)` 在可数并集和可数交集下封闭。下一个例子说明了所有 Lebesgue 积分理论的基础可测空间（Halmos, 1950）。

## 例 B.1




设 `X` 为局部紧 Hausdorff 空间。Borel 集 `E` 是 `X` 的子集，使得 `E` 是使用 `X` 中闭集的最小 `σF` 的像。这些被称为属于由 `X` 的闭集生成的最小 `σ` 代数的 Borel 集。为了使例子更具体，设 `X` 为实直线 `R`。Borel 集 `E` 是 `X` 的子集，或 `S=2^(X)` 的元素，具有 `σF(E)` 属于 `M` 的性质。空集和整个实直线 `R` 都属于 `M`。闭区间 `[0, 1]` 属于 `M`，因为 `[0, 1]` 是 `R` 中的闭集。同理，区间 `[1.5, 2]` 也属于 `M`。此外，利用约束条件 (3)，这两个集合的并集属于 `M`。请记住 `σF` 类似于一个部分恒等函数；它选择 `X` 的幂集 `2^(X)` 中哪些类型的集合为可测集。然后，利用约束条件所规定的并、差、交闭包条件，可以找到所有其他可测集。然而，约束条件 (3) 不仅对有限情形成立，也必须对可数无限情形成立。因此可推出 `[0, 1)` 也是一个 Borel 可测集。注意，使用 Borel 可测集 `E[k]=[0, 1–1/k]`，`k=1, 2, …`，然后取 `E[k]` 的无限并集即可得到所需结果。据此，所有开集、半开半闭集也都属于 `M`，因此是 Borel 可测的。

在 `R^(n)` 或 `C^(n)` 中，使用实情形中的闭集，并在复情形中使用这些集合的实部和虚部，类似的结论也成立。

## Example B.2

再次设 `X` 为局部紧 Hausdorff 空间。Baire 可测集 `X` 是属于由 `Ω` 的特定紧集 `K` 生成的最小 `σ` 代数的 `X` 的子集。这些紧集 `K` 被规定为 `X` 中可数多个开集的交集。再次为了提供一个更具体的例子，设 `X=R`。那么，在此 `σ` 代数中用于生成 Baire 可测集的典型紧集是闭有界集 `K=所有 A[k]=(0–1/k, 1+1/k)` 的交集，`k=1, 2, …` 交集得到紧集 `K=[0, 1]`。当 `X` 的拓扑是 first countable 时，即存在局部可数基时，Baire 和 Borel sigma 代数相等。除极少数例外外，可数基总是存在，因此在大多数实际情况下，Baire 和 Borel sigma 代数是相同的（Arveson, 1996）。

Figure 10.4 给出了一个非 first countable 空间的实例。在此图中，原点处存在无限多个环。直观上，这使得在该区域内找不到包含原点的开球。

对于一个测度空间，存在三种类型：`SUBSET`、`M-SET` 和 `R+^∞`![Equation](img/F000035si3.png)；这里，前两种类型与可测空间中相同。第三种类型是 `R+^∞=[0, ∞]`。测度空间的 MSA 描述涉及两个签名集，忽略了与扩展非负实数线中实数相关的签名集的严格全序。第一个签名集如上所述，包含 `σField`。第二个签名集具有一元运算符名称 `μMeasure`。它满足

`μMeasure` 是从 `M-SET` 到 `R+^∞` 的映射。这在 图 B.1B 中有所说明。

接下来，用 `μ` 代替 `μMeasure`；测度 `μ` 必须满足等式关系和恒等式。

1. `μ(X)` 属于 `[0, ∞]`

2. 对于 `M` 中的 `E[k]`，其中 `k=1, 2, 3, …` 且它们两两不相交，即它们的交集为空，`μ(∪E[k]) = ∑μ(E[k])`![Equation](img/F000035si4.png)。

测度 `μ`![Equation](img/F000035si5.png) 被称为 sigma finite，这意味着对于 `M` 中的任意 `E`，`E` 等于可数个 `E[k]` 的并集，其中 `E[k]` 属于 `M`，且 `μ(E[k])<∞`![Equation](img/F000035si7.png)，对所有 `k=1, 2, 3, …` 成立。测度 `μ`![Equation](img/F000035si8.png) 当 `μ(X)<∞`![Equation](img/F000035si10.png) 时称为有限。如果对于 `M` 中每个满足 `μ(E)=∞` 的 `E`，都存在可测集 `F` 是 `E` 的子集，使得 `0<μ(F)<∞`![Equation](img/F000035si12.png)，则称其为半有限。sigma finite 测度总是半有限测度。这一断言可通过反证法得到。假设 `μ`![Equation](img/F000035si13.png) 不是半有限的。于是存在 `M` 中的集合 `E` 使得 `μ(E)=∞`，并且不存在 `E` 的子集 `F` 满足 `0<μ(F)<∞`![Equation](img/F000035si15.png)。然后对于 `μ`![Equation](img/F000035si16.png)，由于它是 sigma finite 的，存在一列可测集 `E[k]`，使得 `X` 等于 `E[k]` 的可数并。由此可得 `E` 等于 `[E intersect E[k]]` 的可数并。这意味着 `μ(E)` 小于等于 `∑_{k = 1}^{∞} μ(E intersect E_k)`![Equation](img/F000035si18.png)。此外，`μ(E intersect E[k])` 小于等于 `μ(E[k])`，后者是有限的。但根据假设，`E` 的任何子集的测度都为零，而 `(E intersect E[k])` 是 `E` 的子集；于是 `μ(E intersect E[k])` 必须等于零。由此可得 `μ(E)=0`，产生矛盾。

## Example B.3

考虑可测空间 `(X, M)`。其中 `X` 非空，`M=2^(X)`，且 `f: X → [0, ∞]`。函数 `f` 在 `M` 上确定一个测度 `μ`![Equation](img/F000035si19.png)，其中 `μ(E) = ∑_{x in E} f(x)`![Equation](img/F000035si20.png)。当且仅当对所有 `x` 属于 `X`，`f(x)<∞`![Equation](img/F000035si21.png) 时，这是一个半有限测度。由此可知，如果 `f(x)=∞`，则 `{x}` 属于 `M`，而单点没有真子集。在这种情况下，找不到有限测度的子集。假设对所有 `x` 属于 `X`，`f(x)` 是有限的。如果 `μ(E)=∞`，那么对于 `E` 中的单点 `x`，可得 `{x}` 是 `E` 的子集，且 `μ({x}) = ∑_{x} f(x) < ∞`![Equation](img/F000035si23.png)。

## Example B.4

实直线上的 Lebesgue 测度是 sigma finite 的，但不是有限的。使用所有整数 `n` 的 Borel 可测集 `n, n+1)`。这提供了可数多个单位 Borel 区间的互不相交的并，覆盖整个实直线。因此 Lebesgue 测度是 sigma finite 的。

### References

* [Arveson, 1996 Arveson W. *局部紧空间上的测度与积分笔记* 伯克利：加州大学；1996；.

* Halmos, 1950 Halmos P. *测度论* Springer 1950；.

# Appendix C

## Elliptic curves and Abelian group structure

在处理椭圆曲线 (`ECs`) 时，目标是找到 `R²` 中该三次方程的所有整数或有理数解。考虑以下式子：`b²c=4a³–4ac²+c³`，其中 `c` 非零。设 `x=a/c` 且 `y=b/c`，则方程变为椭圆方程：`y²=4x³–4x+1`（参见 图 C.1）。因式分解得到方程 `(y−1)(y+1)=4x(x+1)(x−1)`。该方程的解，即曲线上的点，包括 `(0,1)`、`(0,−1)`、`(1,1)`、`(1,−1)`、`(−1,1)`、`(−1,−1)`。其他解（如果存在）可通过作一条穿过两个不同解点的直线，然后求解第三个交点来找到。由于方程关于 `x` 轴对称，因此对于任意解，关于同一横坐标值的相反分支也将是解。选择两个点来确定第三点的过程产生了一个二元运算；为方便起见，将其称为加法。



# 椭圆曲线加法

### 图 C.1 椭圆曲线加法

![图 C.1 椭圆曲线加法。](img/F000114bm01-9780443136979.jpg)

图 C.1 椭圆曲线加法。

参照图，直线 `y=2x+1` 经过 `(0,1)` 和 `(−1,−1)` 并与椭圆曲线相交于 `(2,5)`。相应地，`(2,-5)` 也是曲线上的一个点。反射点是解，被称为 `(0,1)` 和 `(−1,−1)` 的加法。因此 `(0,1)` 与 `(−1,−1)` 的和为 `(2,−5)`（参见 图 C.1）。这次，通过 `(0,1)` 和 `(2,−5)` 的直线给出 `y=−3x+1`，求交点得到 `(1/4,1/4)`。因此点 `(1/4.−1/4)` 是解。于是 `(0,1)` 加上 `(2,−5)=(1/4.−1/4)`。继续，直线 `y=x` 经过 `(−1,−1)` 和 `(1,1)` 并如前所述得到 `(1/4.1/4)`。

椭圆曲线阿贝尔群结构的机制如下：曲线上两点的和是通过利用经过这两点的直线的方程来找到的，然后找到它再次与曲线相交的位置，从而确定该直线上第三个点，最后将该找到的点关于 `x`-轴反射。如果两点连线是垂直的，则第三点为 `∞`![方程](img/F000114si1.png)，而无穷远点因此是和。因此，通过包含无穷远点，结构是一个点集。对曲线的切线以类似方式处理；在此情况下，切点被自身相加。如果切线第三次与曲线相交，则和为该点应用负纵坐标值。当与曲线没有交点时，使用无穷远点 `∞`![方程](img/F000114si2.png)。在此二元运算下点的集合目前是一个群胚（参见 图 C.2）。

### 图 C.2 椭圆曲线上垂直点的加法

![图 C.2 椭圆曲线上垂直点的加法。](img/F000114bm02-9780443136979.jpg)

图 C.2 椭圆曲线上垂直点的加法。

要证明它是半群，必须满足结合律。这里，回到射影直线和射影空间，应用一个定理（Cassels, 1991）：每当一个三次曲线经过与另外两个三次曲线相交的九个交点中的八个时，则必须包含第九个交点。这通常被称为九点引理或 Cayley–Bacharach 定理。结合律的证明源于这一结果（Cayley, 1889）（参见 图 C.3）。

### 图 C.3 结合律的证明

![图 C.3 结合律的证明。](img/F000114bm03-9780443136979.jpg)

图 C.3 结合律的证明。

基本思想是找到两个曲线 `C1` 和 `C2`，它们与给定曲线 `C` 共享八个不同的点，然后证明这些曲线是三次的且不等于 `C`，然后应用上述定理说明第九个点同时在 `C1` 和 `C2` 中。通过审慎地以战略模式配置八个点，第九点的包含将证明结合律。在此图中，符号 (?) 应该是第九个点。所有六条直线共有的八个点是：`A`、`P`、`Q`、`R`、`B`、`Q+R`、`Z` 和 `P+Q`。直线上的点表示仿射空间中的直线。总体目标是证明 `(P+Q)+R=P+(Q+R)`；这将成立因为直线 `L2` 和直线 `M2` 在 `?` 处相交。三条直线 `L1`、`L2` 和 `L3` 各自可以用一次齐次多项式给出：`|1 = |2 = |3 = 0`![方程](img/F000114si3.png)。在此情况下，`C1 = |1|2|3`![方程](img/F000114si4.png) 描述了一个退化的三次曲线。类似地令 `C2=m1m2m3`，其中 `m1=m2=m3=0` 是描述 `M1`、`M2` 和 `M3` 的一次齐次多项式。因此给定椭圆曲线 `C`，包括这八个点，应用 Cayley–Bacharach 定理表明第九个点 (?) 被包含并且在 `L2` 与 `M2` 的交点中。这表明结构是一个半群。接下来证明结构是一个幺半群。

必须找到一个 ZERO 并证明它满足零律以得到一个幺半群。零是无穷远点 `∞`![方程](img/F000114si5.png)。它满足零律，因为如果你取任意一个点 `p`，则 `p+Z` 的和是通过取垂直线并连接这两个点找到的。然后对于一个非切点 `p`，在此同一条直线上存在第三个点 `q`，因此和为 `−q`。然而 `−q` 是 `p`。当 `p` 是一个切点且切线是垂直的时，则 `p+Z=p`。接下来要证明的是该结构是一个群。对于一个群，需要一个 MINUS，且必须满足负逆恒等式。然而对于点 `p=(a, b)`，`MINUS(p)=(a, −b)` 简记为 `−p`。此外，当这两个点用直线连接时，直线总是垂直的，所以 `p+(−p)=∞`![方程](img/F000114si6.png) 如所期望。由于只有一个无穷远点，`MINUS(Z)=∞`![方程](img/F000114si7.png)。最后，群是阿贝尔的，因为选择两点 `p` 和 `q` 在一条线上的顺序不会改变同一条线上得到的第三点 `r`，该点被反射从而 `p+q=−r=q+p`。

最后，Mordell 的一个定理规定了有理系数椭圆曲线上有理解的群结构。它断言只要它是非奇异的，即具有不同的根，它就是一个有限生成的阿贝尔群（Silverman, 1986）。因此根据该定理，存在该群中有限个点 `Pj`，使得该群中每一个点 `P` 都可以表示为 `P=summation j=1 to n of nj Pj`，其中 `nj` 在 `Z` 中。此外，该群的结构已被 Mazur 证明（Dumber, 2019）为 `T x Z x Z x … x Z` 的形式，其中 `T` 是一个挠子群，其阶数至多为 16，且 `T` 总是十五种可能之一中的一种。此外，上面有 `r` 个 `Z` 的拷贝，它被称为秩。最后，对于椭圆曲线 `y²\=x³\+ ax+b`，其中 `a` 和 `b` 在 `Z` 中，Siegel (Lang, 1978) 表明相关联的群具有有限个整数坐标的点。

## 参考文献

* Cassels, 1991 Cassels J. 伦敦数学学会学生教材 24 *椭圆曲线讲义* 剑桥大学出版社 1991；
* Cayley, 1889 Cayley A. *关于曲线的相交* 剑桥大学出版社 1889；
* Dumber, 2019 Dumber S. *椭圆曲线上的挠性与 Mazur 定理* 芝加哥大学教育 2019；
* Lang, 1978 Lang S. *椭圆曲线*. 卷 231 Springer 1978； 3-540-08489-4.
* Silverman, 1986 Silverman J. 0-387-96203-4 *椭圆曲线的算术*. 卷 106 Springer-Verlag 1986；

# 附录 D

## 杨图




# 杨图
存在多种版本的 `Young diagrams`，但几乎所有版本都像条形图一样构造，采用有限数量的单元或单位正方形（Yong, 2007）。这些图在 `Fock` 空间的表示以及夸克味本征态中都很重要（Bouttier, 2019；Sagan, 2001）。这里采用的图通常位于第四象限，并且始终涉及单位正方形 `(0, 1\]×\[−1, 0)` 的积分平移。结构形成连续的水平条，均左对齐，通常沿 y 轴。结构在 `Z×Z` 中有一个起点 `(p,q)`。这是第一个正方形左上角所在的位置。最常见的是该点为 `(0, 0)`。水平方向上有 `n1` 个连续单元形成长度为 `n1` 的块或条，位于 `(p, p+n1\]×\[q−1, q)`，其中 `n1` 大于或等于 1。在其下方，可能还有另一个长度为 `n2` 的条，其大小小于或等于 `n1`。该条由 `n2` 个单元构成，为 `(p, p+n2\]×\[q−2, q−1)`。这种模式以非递增的 `nj` 单元继续，一个在另一个之下。不是绘制杨图，它们被指定为 `(p,q)`、`(n1, n2, …, nk)`，后者是一组有限的非负数 `nj`，构成一个非递增序列。杨图的轮廓是由位于结构右侧和下部的分段连续的水平和垂直线段构成的边界点。此外，对于杨图，高度 `h` 是非零 `nj` 值的数量。简而言之，杨图可以表示为一个 `k` 元组有界向量，`(n1, n2, …, nk)[(p,q)]`。

## 示例 D.1
考虑 图 D.1 中的杨图。它由 `(p, q)=(0, 0)` 和 `(n1, n2, n3, n4, 0, …)=(5, 3, 2, 1, 0 …)` 给出。该结构的轮廓由一条路径连通的线段集合组成：它从左下角开始并沿左水平线段行进，`{(x, y) | y=−4, x in (0, 1\]`。然后在 `x=1`，`y in \[−4,−3)`，`y=−3`，`x in \[1, 2\]`，`x=2`，`y in \[−3, −2)`，`y=−2`，`x in \[2, 3\]`，`x=3`，`y in \[−2, −1)`，`y=−1`，`x in \[3, 4)`，`y=−1`，`x in \[4, 5\]`，`x=5`，`y in (−1, 0\]`。最后，该结构的高度为 `h=4`。由于 `q=0`，`−h=−4` 是该结构达到的最小值。有界向量表示唯一指定了该图：`(5, 3, 2, 1) (0, 0)`，其中最后的整数对指定图的左上角，通常写成下标。有关该表示的额外用途，请参阅第 1.9 节。杨图的标记从 `x=0` 轴开始，在底部单元下方半个单位处为 `−9/2`。随后在轮廓中每个单元的两侧各加一。这些标记对于确定 Maya 图很重要。如果点 `(p, q)` 是任意的，则会出现杨图的等价类。此外，在这种情况下，原点可以被视为陪集代表。#

![图 D.1 杨图.](img/F000151bm01-9780443136979.jpg)

图 D.1 杨图。

## 参考文献
* Bouttier, 2019 Bouttier, J., *组合学中的费米子：随机置换与分拆*, [`http://fermions.sciencesconf.org`](http://fermions.sciencesconf.org). 2019.
* Sagan, 2001 Sagan B. `0-387-95067-2` *对称群* Springer 2001;.
* Yong, 2007 Yong A. 什么是杨表。 *Not AMS*. 2007;54.

# 附录 E
## 杨图与对称群
对称群 `Sn` 在群论中很重要，主要是因为 Cayley 定理。也就是说，对称群 `Sn` 包含与任何不超过 `n` 个元素的群同构的所有子群。这用于描述 `Fock` 空间。将会看到附录 A.4 中描述的杨图提供了 `Sn` 的不可约表示的视觉描述。重要的是，除了 `Sn` 的元素由元素的对换乘积组成外，它还可以表示为不相交的循环生成元的乘积。每个循环都有有限长度，即循环中元素的数量。该数是正数且小于或等于 `n`。`Sn` 的类由 `n` 个数 `w1`, `w2`, …, `wn` 指定，其中 `wj` 表示长度为 `j` 的 `Sn` 循环的数量。由于循环的不相交性，可得和 $\sum_{j = 1}^{n}{j{wj} = n}$ (Sagan, 2001)。

## 示例 E.1
考虑下面矩阵型图中提供的对称置换群 `S7`。使用该图追踪路径，从而确定对称群中的特定循环。从顶部数字 `x` 开始，确定数字 `x` 正下方垂直的数字，并称其为 `y`。然后如果 `y` 出现在顶部，重复上一步；一直做到 `x` 再次出现在顶部为止。对于特定 `x` 执行此上下过程的次数指示循环的长度。所涉及的不同元素构成一个循环群：

$\\begin{array}{lllllll} {\\left| 1 \\right.} & {2} & {3} & {4} & {5} & {6} & \\left. 7 \\right| \\\\ {\\left| 7 \\right.} & {6} & {4} & {5} & {3} & {2} & {\\left. 1 \\right|.} \\\\ \\end{array}$

![方程](img/F000096si2.png)

从 1 开始，1 → 7 → 1，所以这是一个长度为二的循环。接下来，对于 2，2 → 6 → 2，这也是长度为二的循环。最后，对于 3，3 → 4 → 5 → 3，这是一个长度为三的循环。群 `Sn` 可以写成循环的乘积：`{1 7) (2 6) (3 4 5),` 其中顺序无关紧要。`S7` 的类用 `wk` 表示。这里，`k` 是循环的长度，`wk` 指定长度为 `k` 的循环有多少个。在这种情况下，`w1=0`，`w2=2`，`w3=1`，且 `w4=w5=w6=w7=0`。这正是因为存在两个长度 `k=2` 的循环和一个长度 `k=3` 的循环。此外，和 `2 · w2 + 3 · w3=2 · 2 + 3 · 1=7`。#

分拆用 `p=(p1, p2, …, pn, …)` 表示。它是有限或无限序列的非递减非负数 `pj` 的任意和，即每个 `pj` 小于或等于 `p(j+1)`。每个 `pj` 称为 `p` 的一个部分。各部分之和为 `| p |`，称为权重。当权重为 `n` 时，`p` 称为 `n` 的一个分拆。由于某些对称群 `Sn` 存在单例循环 `w1`，这些循环可以有 `n` 个，因为没有更大的循环。另外，对于 `n>1`，存在 `Sn` 具有一个二循环 `w2`，其余为一个循环，等等，考虑所有可能性。最后，一些 `Sn` 由 `n` 个元素的单个循环 `wn` 描述。因此，对于任意 `Sn`，涉及类的 `n` 的分拆的所有可能性为 `p1=w1 + w2 + … + wn`，`p2=w2 + w3 +… + wn`，…，`pn=wn`。每当存在 `k` 大于或等于 `j` 且存在 `wk` 时，就使用一个 `pj`。这些量可以按从最大 `p1` 到最小 `pn` 的顺序排列在彼此上方的行中。每行由 `pj` 个单位正方形单元组成，形成一种称为杨图的结构。行数等于 `h`，即非零 `pj` 的数量。在此应用中，杨图表示左对齐，并在 `x, y` 平面的第四象限原点开始。

## 示例 E.2




## 例 E.1

在 例 E.1 中，可见存在 `w2`=2 个二循环和一个三循环 `w3`。相应地，`n`=7 的划分将被给出，但仅针对非零项的 `wj`。相应地，`p1`=`w2`+`w3`=2+1=3，`p2`=`w2`+`w3`=3，`p3`=`w3`=1，因此这些之和为 `n`=7。划分是 (`p1`, `p2`, `p3`, … `p7`)=(3, 3, 1, 0, 0, 0, 0,)=(3, 3, 1)。相关的 Young 图有七个格子。它有三行，顶行由三个格子组成。下面是第二行，包含三个格子。最后，底行有一个格子。所有行均左对齐。作为边界向量，该结构为 (`3 3 1`) [(0,0)]（参见 图 E.1）。

![图 E.1 置换群的 Young 图。](img/F000096bm01-9780443136979.jpg)

图 E.1 置换群的 Young 图。

`Sn` 的不可约表示与 Young 图之间存在一一对应。Young 图能够简单地识别不可约表示的乘积。为了更好地用这些图识别表示，使用了 Young 表。这是一个 Young 图，其 `n` 个格子唯一地填入整数 1, 2, …, `n`。对于这样的表，存在 `n!` 种编号格子的方法。当编号按行从左到右递增，继续到下一行时，这称为正规表。当数字在行或列中仅递增时，这称为标准 Young 表。标准 Young 表由使用置换的正规表得到。

## 参考文献

* Sagan, 2001 Sagan B. *对称群* Springer 2001; 0-387-95067-2.

# 附录 F

## 泛函分析中的基本定理

下面提供了泛函分析的基本定理列表。连同这些定理，还有与定理本身相关的几个定义（Apostle, 1974；Narici & Beckenstein, 2011；Rudin, 1973）。

### 魏尔斯特拉斯逼近定理

任何定义在 `R` 的紧区间 [`a`, `b`] 上的连续函数 `f`，都可以用多项式 `p` 在任意 *ϵ*![方程](img/F000229si1.png)，*ϵ*![方程](img/F000229si2.png)>0 的范围内一致逼近。一致逼近意味着 `sup[x] | f(x) - p(x) | < ϵ`![方程](img/F000229si3.png)。使用 Bernstein 多项式可以在 Achieser (1956) 和 Narici (2004) 中找到一个最优雅的证明。

### 斯通-魏尔斯特拉斯定理

设 `X` 为局部紧 Hausdorff 空间，且 `A` 为 Banach 代数 `C0` 的子代数，具有上确界范数。这里，`C0` 由 `X` 上的连续实值函数 `f(x)` 组成，当 | `x` | → ∞![方程](img/F000229si4.png) 时趋于零。然后如果它分离点且处处不消失，则 `A` 在 `C[0]` 中稠密。

函数集 `S` 的 `f: A → B` 在 `A` 中被称为分离点，当且仅当 `S` 中存在至少一个函数 `h` 是单射，即它是 1–1。对所有 `x`、`y` 在 `A` 中，`x` 不同于 `y`，这意味着 `h(x)` 不同于 `h(y)`。函数集被称为处处不消失或在 `A` 的任意点都不消失，这意味着对于 `A` 的每一点 `x`，都存在 `S` 中的函数 `f` 使得 `f(x)` 非零。

## 例 F.1

函数集：`S[1]`={ `f(x)=1`, `g(x)=x²` } 在定义域 `A`=[-2, 2] 上不分离点，因为在 `x`=1 和 `x`=-1 时，`f=g`。然而，`S[2]`={ `f(x)=1`, `g(x)=x²`, `h(x)=x` } 确实分离 `A` 中的点，因为 `S[2]` 包含一个函数 `h`，它在 `A` 上是 1–1。

## 例 F.2

函数集：`S[1]`={ `f(x)=1`, `g(x)=x²` } 在定义域 `A`=[-2, 2] 上确实处处不消失。然而，`S[3]`={ `g(x)=x²`, `h(x)=x` } 在此定义域上不处处不消失，因为在零点该集合中没有函数是非零的。

### 斯通-魏尔斯特拉斯定理

对于任意紧集 `K`，设 `A` 为连续函数 `f: K → C` 的可能非么、结合自伴代数，它在 `K` 中分离点。如果此外 `A` 在 `K` 的任意点都不消失，或 `A` 是么，则 `A` 在 `C(K)` 中关于一致范数稠密。

### 阿泽拉-阿斯科利定理

设 `{f[n]}`，`n`=0, 1, 2, … 为 `R` 中紧集 [`a`, `b`] 上的实值函数序列。如果该序列既一致有界又等度连续，则存在子序列 `{f[n[k]]}`![方程](img/F000229si5.png)，它在 [`a`, `b`] 上一致收敛。当 `{f[n]}` 的每个子序列都在 [`a`, `b`] 上一致收敛时，则 `{f[n]}` 既一致有界又等度连续。

当存在常数 `M`>0，使得对于 [`a`, `b`] 中的所有 `x` 和所有非负整数 `n`，满足 | `f[n]` | < `M`，则连续函数序列 `f[n]` 称为一致有界。

序列 `{f[n]}` 在 `ϵ`![方程](img/F000229si6.png) > 0 时，对所有 `x` 和 `y` 在 [`a`, `b`] 中，以及非负 `n`，存在 `δ`![方程](img/F000229si7.png)>0，使得如果 | `x−y` | < `δ`![方程](img/F000229si8.png)，则 | `fn−fn` | < `ϵ`![方程](img/F000229si9.png) 时，称为一致等度连续。

### 哈恩-巴拿赫定理

设 `f` 为赋范向量空间 `X` 的向量子空间 `M` 上的连续线性泛函。在这种情况下，`f` 具有到整个 `X` 的连续线性扩张 `F`，而且 `|| f ||`=`|| F ||`。在 Narici (2004) 的研究中出现了出色的历史记述。

### 开映射定理

对于满、连续、线性算子 `T`，`T: A—->B`，其中 `A` 和 `B` 为 Banach 空间；则 `T` 是开映射。因此，对于 `A` 中的任意开集 `U`，`T(U)` 是 `B` 中的开集。

### 一致有界性原理

设 `B(X,Y)` 为从 Banach 空间 `X` 到赋范向量空间 `Y` 的所有有界算子的空间，并设 `F` 为 `B(X,Y)` 的子集。如果 `sup[TinF]||T(x)|| < ∞`![方程](img/F000229si10.png) 对所有 `x` 在 `X` 中成立，则令 `c`= `sup[TinF]||T(x)||` 当 `|| x ||`=1 时，可得 `c`= `sup[TinF]|| T ||`。

### 有界逆定理

对于 `X` 和 `Y` 为 Banach 空间，如果 `T: X → Y` 有界且可逆，则 `T^(-1)` 也是有界的。

### 巴雷尔纲定理

拓扑空间 `T` 的子集 `S` 是第二纲的，如果 `S` 不能写成 `T` 中无处稠密集的可数并。这意味着并集中的至少一个集合的闭包具有非空内部。

### 巴拿赫-斯坦豪斯定理

设 `X` 和 `Y` 均为拓扑向量空间，且 `Γ`={ `T[a]` }`ainR`，其中 `T[a]` 是从 `X` 到 `Y` 的连续线性映射。设 `B` 表示 `X` 中所有轨道 `Γ(x)`={ `Ta`，使得 `T[a]` 在 `Γ` 中 } 在 `Y` 中有界的点 `x` 的集合。如果 `B` 在 `X` 中是第二纲的，则 `B`= `X`，且函数集合 `Γ`![方程](img/F000229si11.png) 是等度连续的。由 Stover (2023) 提供了出色的阐述。

### 闭图定理

对于线性算子 `T`，`T: A → B`，其中 `A` 和 `B` 为 Banach 空间，则 `T` 有界当且仅当 `T` 的图是闭的。等价地，当给定 `v[n] → v`，全部在 `A` 中，且也给定 `T v[n] → w`，全部在 `B` 中，如果 `Tv=w`，则 `T` 有界。

笛卡尔积 `A×B` 称为乘积空间。它具有乘积拓扑，也称为 Tychonoff 拓扑或最粗拓扑。它是使用连续投影 `p[a]` 和 `p[b]` 时包含最少开集的拓扑，其中 `p[a]: A×B → A` 且 `p[b]: A×B → B`。



`T` 的图是 `graph(T)={(v, Tv) such that v is in domT}`。映射 `T: A → B` 在图 `A×B` 中是闭的，当且仅当它是具有 `Tychonoff` 拓扑的乘积空间 `A×B` 的闭子集。等价地，假设 `v[n] → v`，对于所有 `v[n]` 和 `v` 在 `A` 中，并且也假设 `T v[n] → w`，对于所有 `T v[n]` 和 `w` 在 `B` 中，若 `Tv=w`，则 `T` 有界。

### 参考文献
* Achieser, 1956 Achieser N. 0–8044-4019-0 *逼近理论* Unger 1956;.
* Apostle, 1974 Apostle T. *数学分析* 2ed. Pearson Pub Co 1974;.
* Narici, 2004 Narici, L., 关于 Hahn-Banach 定理，第二届国际数学分析课程论文集，格拉纳达，2004。
* Narici and Beckenstein, 2011 Narici L, Beckenstein E. 978–1584888666 *拓扑向量空间，纯粹与应用数学* 2nd ed. CRC press 2011;.
* Rudin, 1973 Rudin W. 0–07-054236-8 *泛函分析* McGraw-HIll 1973;.
* Stover Stover, C., 2023. Banach-Steinhaus 定理，来自 [MathWorld.wolfram.com](http://MathWorld.wolfram.com)。

## 附录 G
### Sturm–Liouville 微分方程及其推论
Sturm–Liouville 方程是一个二阶线性微分方程（DE），涉及函数 `p`、`q` 和 `r` 以及参数 `λ`![Equation](img/F000102si1.png)。该 DE 由 `(p(x)y')' + (q(x) + λ r(x)) y = 0` 给出。撇号表示导数。Sturm–Liouville 问题由上述 DE 以及一个定义域组成，例如区间 `(a, b)`。它还包含该区间闭包端点处的边界条件。此外，假设 `p`、`p'`、`q` 和 `r` 在定义域上连续，其中 `p'` 表示 `p` 的导数，且函数 `p > 0`，在该定义域上。函数 `r` 通常表示为 `w` 并称为权重。参数 `λ`![Equation](img/F000102si3.png) 并非先验指定。它作为非平凡解的一部分被找到，在这种情况下称为特征值。DE 的解称为对应于特征值的特征向量或特征函数。

DE 可以重构为函数希尔伯特空间 `H` 中的自伴算子。`H` 中的内积定义如下：`< f , g > = ∫[a]^[b] f* g dx`![Equation](img/F000102si4.png)。主要参考文献是 Bochner (1929) 和 Birkhoff and Rota (1978)。Sturm–Liouville DE 的解在各种边界条件下存在，特别是当它们被称为可分离时。在这种情况下，存在实值标量 `c[1]`、`c[2]`、`d[1]` 和 `d[2]`，使得 `c[1]² + c[2]² > 0`![Equation](img/F000102si5.png)，且 `d[1]² + d[2]² > 0`![Equation](img/F000102si6.png)，其中边界条件成立：`c[1] y(a) + c[2] y'(a) = 0` 且 `d[1] y(b) + d[2] y'(b) = 0`。Sturm–Liouville DE 连同上述边界值（BVs）构成一个系统，其中 DE 和 BV 具有

1. 解，由区间 `(a, b)` 中的特征函数 `yn` 组成。它们在标量倍数意义下唯一。区间可能在一个或两个方向上延伸到无穷大。相应的特征函数在此区间内有 `n-1` 个零点。
2. 特征值；每个特征函数都有一个唯一的实特征值，并且它们按顺序排列 `λ[1] < λ[2] < λ[3] < …`
3. 加权希尔伯特空间。归一化特征函数构成加权 L² 希尔伯特空间中函数的 ON 基。内积 `<y[n], y[m]>` 由加权积分给出：`∫[a]^[b] yn ym u(x) dx = zero`![Equation](img/F000102si7.png)，除非 `n = m`，此时积分在归一化后等于一。

从实际角度来看，找到权重 `u(x)` 是最重要的标准，因为它定义了 L² 中希尔伯特空间的内积。简而言之，对于线性算子：`L(y) = a y'' + b y' + c y`，权重函数为 `u = e^(∫ (b - a')/a dx)`![Equation](img/F000102si8.png)。下面将对此进行说明，针对几个重要的多项式类。在开发所有权重函数之后，Hermite 多项式和 Laguerre 多项式将详细介绍。

#### 示例 G.1
Legendre 多项式：`L(y) = (1 - x²) y'' - 2x = λ y`。则 `u = e^(∫ (b - a')/a dx) = e⁰ = 1`![Equation](img/F000102si9.png)。对于区间 `[-1, 1]` 上的这些函数，使 `L` 自伴不需要边界条件。Legendre 多项式 `y[n]` 构成一个 ON 基，内积为 `∫[-1]¹ yn ym dx = zero`![Equation](img/F000102si10.png)，除非 `n = m`；此时积分可以归一化为一。将特征值代入后的 DE 为 `(1 - x²) y'' - 2x - n (n+1) = 0`。

#### 示例 G.2
Hermite 多项式：`H(y) = y'' - 2x y' = -λ y`。则 `u = e^(∫ (b - a')/a dx) = e^(∫ (-2x) dx) = e^(-x²)`![Equation](img/F000102si11.png)。对于 `(-∞, ∞)` 上的这些函数，Hermite 多项式构成一个 ON 基 `∫[-∞]^∞ yn ym e^(-x²) dx = zero`![Equation](img/F000102si12.png)，除非 `n = m`；此时积分可以归一化为一。

#### 示例 G.3
Laguerre 多项式：`L(y) = x y'' + (1 - x) y' = -λ y` 在 `0, ∞)` 上。则 `u = e^(∫ (b - a')/a dx) = e^(∫ (-1) dx) = e^(-x)`![Equation。它们构成一个 ON 基 `∫[0]^∞ yn ym e^(-x) dx = zero`![Equation](img/F000102si14.png)，除非 `n = m`；此时积分可以归一化为一。

#### 示例 G.4
谐振子：`H(y) = 1/2 (-h²/m y'' + m (w[0] x)²) y = λ y`。则解构成一个 ON 集。权重 `u = e^(∫ (b - a')/a dx) = e⁰ = 1`![Equation](img/F000102si15.png)。在这种情况下，特征函数在 L² 中。因此，在这种情况下权重函数为一。

#### 示例 G.5
合流超几何方程：`L(y) = x y'' + (c - x) y' = λ y`。权重为 `u = e^(∫ (b - a')/a dx) = e^(∫ (c - x - 1)/x dx) = |x|^(c - 1) e^(-x)`![Equation](img/F000102si16.png)。DE 为 `x y'' + (c - x) y' + n y = 0`。

#### 示例 G.6
Chebyshev 多项式：`L(y) = (1 - x²) y'' - x y' = λ y`，`L(y) = (1 - x²) y'' - 3 x y' = λ y`。首先，它在 `[-1, 1]` 上是自伴的。权重 `u = e^(∫ (b - a')/a dx) = e^(∫ x/(1 - x²) dx) = 1/(1 - x²)^(1/2)`![Equation](img/F000102si17.png)。`∫[-1]¹ yn ym / (1 - x²)^(1/2)`![Equation](img/F000102si18.png) `dx = zero`，除非 `n = m`；此时积分可以归一化为一。将特征值代入 DE 后的 DE 为 `(1 - x²) y'' - x y' + n² y = 0`。

#### 示例 G.7
Jacobi 多项式：`L(y) = (1 - x²) y'' + (e x + g) y' = λ y`，在 `[-1, 1]` 上。权重 `u = e^(∫ (b - a')/a dx) = e^(∫ (e x + g - 2x)/(1 - x²) dx)`![Equation](img/F000102si19.png)。对于 `g = -1, -2, -3` 且 `e = 0`，Jacobi 多项式分别变为 Legendre 和 Chebyshev 多项式。如果 `-e < g < e`，则 DE 为 `(1 - x²) y'' + (e x + g) y' + [n (n - 1) - n e] y = 0`。

许多特殊函数类可以用几种不同的方式定义或描述。对于 Hermite 多项式，它们满足以下条件：

1. 微分方程：`h'' - 2 x h' + 2 n h = 0`，或以 Sturm–Liouville 微分方程形式，`e^(-x²) h'' - 2 x e h' + 2 n e^(-x²) h = 0`
2. Rodrigues 公式：`h_n = (-1)^n e^(x²) d^n e^(-x²) / dx^n`，`n = 0, 1, 2, …`。
3. 差分方程：`h(n+1) - 2 x h_n + 2 n h(n-1) = 0`




4. 生成函数：`e^((2*x*t - t²))` ![方程](img/F000102si24.png) 乘以和 ∑ ![方程](img/F000102si25.png) `(t^(k) / k! Hk)`，k=0, 1, 2, …

当它们被归一化时，它们用 `Hn` 表示，成为 `L2` 的一个 ON 基（非加权且不再是多项式），并且由 `Hn = e^(-1/2*x²) h_n / (2^(n) n! (pi)^(1/2))^(1/2)` ![方程](img/F000102si26.png) 给出。这些被称为 Hermite ON 函数。

对于拉盖尔多项式，`y = Ln(x)`，它们满足以下条件：

1. 微分方程：`x y'' + (1 - x) y' + n y = 0`，x 在 `[0, infinity)` 中，或用 Sturm–Liouville 表示 `(e^(-x) x y')' + n e^(-x) y = 0`。

2. 罗德里格斯公式：`Ln(x) = [(d/dx - 1)^(n)] x^(n) / n!`。

3. 差分方程：`L(n+1)(x) = [(2 n + 1 - x) Ln(x) - n L(n - 1)(x)] / (n + 1)`，对于 n=1, 2, 3, 4, …

4. 生成函数：和，`∑ t^(n) L_n(x) = (1 - t)^(-1) e^(-t x / (1 - t))` ![方程](img/F000102si27.png)，n=0, 1, 2, …

二阶线性齐次微分方程可以通过定义积分因子 `p` 表示为 Sturm–Liouville 微分方程。方法如下所述，更为严格。对于线性算子，`L(y) = a y'' + b y' + c y`，如果 `p = e^(∫ (b - a') / a dx)` ![方程](img/F000102si28.png) 在区间 `I` 上有限，并且 `V` 是函数向量空间，使得

1. `V` 在 `L` 下是不变的。
2. 对于 `V` 中的每个 `y`，`p y²` 在 `I` 上的积分是有限的。
3. 对于 `V` 中的 `u` 和 `y`，`p a (u' y - u y') = p a (u' y - u y')` 在 `I` 的端点处求值的差为零，则 `L` 关于内积 `<y, u> = ∫ p y u dx` 是自伴的。

### 参考文献
* 伯克霍夫和罗塔，1978 Birkhoff G, Rota G-C. *常微分方程* 3rd ed. John Wiley and Sons 1978;.
* 博赫纳，1929 Bochner S. Uber Sturm-Liouville. *Plansysteme Math Z.* 1929;29.

# 索引
*注意*：页码后跟“*f*”指的是图表。

## A
*   A\* 同态，158
*   阿贝尔群，6，10
    *   结构，321–322，374
*   绝对收敛，151
*   吸收集算子，134，241
*   激活函数，25，27–28
    *   用于神经网络，28–30
*   主动学习，329
*   加法，255
*   绝热量子计算 (AQC)，105–107，327，328
*   绝热定理，103，124–128
*   仿射线，330–331
*   仿射空间，多类代数描述，35–37
*   神经网络内节点的仿射变换，24
*   谐振子的代数解，349–350
*   代数结构，1–2，191
*   几乎周期函数，148–149
*   交替多线性泛函，84
*   振幅放大，303–304，304，313–314
*   解析函数，251
*   解析泛函演算，250
*   解析向量丛，182–183
*   安德烈耶夫效应，120
*   安德烈耶夫反射，117，119
*   角动量，264
*   阴离子，113
*   退火型操作，29–30
*   湮灭算子，273，273–274，274–275，276
*   异常检测，95
*   反对称列维-奇维塔符号，90
*   反幺正线性幺正运算，81
*   反幺正映射，81
*   近似谱，248
*   任意数据集，95
*   任意元素，196
*   元数，3
*   砷 (As)，114
*   阿尔泽拉-阿斯科利定理，384
*   结合、交换幺元代数，42–43
*   结合代数，193
*   结合律，154，222
*   结合性，374
*   图册，177
*   原子，基本结构，111–114
*   构造原理，112
*   自同构，133
*   自动驾驶车辆，21

## B
*   反向传播
    *   算法，25
    *   用于神经网络学习，31–35
*   回代，234
*   巴雷尔纲定理，384
*   巴雷尔可测集，371
*   巴拿赫代数，163
    *   理想，157–158
    *   作为多类代数，51–52
    *   谱，155–157
    *   子群，149–151
*   巴拿赫空间，135，241
    *   多类代数描述，49–51
    *   秩，145–147



*   算子上的谱, 233–236
*   Banach* 代数, 158
    *   多排序代数用于, 52–53
    *   环绕数字信号的, 53–54
*   Banach-Alaoglu 定理, 168–169
*   Banach–Steinhaus 定理, 384–385
*   带限函数, 355
*   巴丁-库珀-施里弗对（BCS 对）, 117
*   Bargmann–Fock 空间, 353
*   基本 Fock, 275
*   基无关准则, 193
*   批量学习, 329
*   BCS 对, *参见* 巴丁-库珀-施里弗对（BCS 对）
*   贝尔态, 139
*   Bergman 核, 353
*   Berry 联络, 128
*   Berry 相位, 128
*   Besicovitch 类, 149
*   偏置值, 24
*   双线性运算, 41
*   二分类函数, 330
*   二元运算, 262
*   二元算子, 8
*   BINE, 41, 44, 52, 192, 342–343, 354
*   比特币, 318–319
*   黑点, 280, 281–282
*   Bloch 球, 91
*   Bloch 球面, 78, 87–88, 89, 91, 296
    *   复数表示, 91–92
*   Bock 向量, 92
*   Bogoliubov 准粒子, 117
*   Bogoliubov 变换, 286
*   玻尔原子模型, 111–112
*   Borel 集, 370
*   玻恩规则, 106, 107
*   玻色子 Fock 空间, 271, 272–273
*   玻色子占据数, 272–276
*   玻色子粒子, 265
*   有界矩阵, 341–346, 342, 343–344, 344
*   束缚态, 108
*   有界向量, 14, 48
*   边界值（BVs）, 387
*   有界误差量子概率（BQP）, 313
*   有界逆定理, 384
*   有界正规算子, 248
*   有界算子, 135–138, 239–241, 252, 260
    *   在希尔伯特空间上, 151–153
    *   谱分类, 231–233
*   有界自伴算子, 361
*   有界性, 145–147
*   BQP, *参见* 有界误差量子概率（BQP）
*   构建原理, 112
*   BVs, *参见* 边界值（BVs）
## C
*   C* 代数, 162–163
    *   多排序代数用于, 52–53
*   C-SCALAR, 58
*   C-VECTOR, 58
*   钙离子（Ca+ 离子）, 113
*   Campbell-Baker-Hausdorff 公式（CBH 公式）, 193–194
*   正则对易关系（CCRs）, 1–2, 148, 264
    *   正则超群, 257–258
    *   等距映射与酉运算, 255–257
    *   部分等距映射的多排序代数, 260–263
    *   部分等距映射, 259–260
    *   位置与动量, 264–265
    *   Stone-von Neumann 与量子力学等价, 266–267
    *   Stone 定理, 263–264
    *   结构, 264–265
    *   辛向量空间, 267–268
    *   Weyl 正则对易关系 C* 代数, 269–270
    *   正则对易关系的 Weyl 形式与海森堡群, 265–266
    *   CCR 的 Weyl 形式与海森堡群, 265–266
*   正则超群, 257–258
*   正则同构映射, 66
*   正则映射, 173–174
*   CAR, *参见* 交叉安德烈夫反射（CAR）
*   载体集, 2, 57–58, 85



# 索引

*   Cartan 魔法公式, 93
*   笛卡尔积, 385
*   阳离子, 113
*   柯西准则, 13, 14–15
*   柯西积分定理, 361
*   柯西序列 (CS), 150, 155, 365–367
*   柯西-布尼亚科夫斯基-施瓦茨不等式 (CBS 不等式), 142
*   柯西积分定理 (CIT), 251
*   凯莱变换, 256–257, 260
*   凯莱-哈密顿定理, 159
*   凯莱定理, 379
*   凯莱-巴哈拉赫定理, 374, 374–375
*   CBH 公式, *参见* 坎贝尔-贝克-豪斯多夫公式 (CBH 公式)
*   CBS 不等式, *参见* 柯西-布尼亚科夫斯基-施瓦茨不等式 (CBS 不等式)
*   CCRs, *参见* 正则对易关系 (CCRs)
*   链式法则, 34, 35
*   特征空间, 168
*   特征方程, 99, 201
*   电荷量子比特, 121
*   图, 177, 199
*   切比雪夫多项式, 333, 388–389
*   CIT, *参见* 柯西积分定理 (CIT)
*   Clifford 代数, 278
*   Clifford 单量子比特群, 295, 297
*   可闭算子, 245
*   闭图定理, 238, 385
*   希尔伯特空间中的闭算子, 135
*   CMOS, *参见* 互补金属氧化物半导体 (CMOS)
*   CNNs, *参见* 卷积神经网络 (CNNs)
*   CNOT 门, 297, 299
*   CNOT 矩阵, 298
*   CNOT 算子, 298
*   最粗拓扑, 385
*   相干性, 91
*   相干控制, 107
*   相干态, 275
*   代数中的交换子, 47
*   冯·诺伊曼代数中的交换子, 167–168
*   对易运算, 90
*   对易关系, 265
*   交换巴拿赫代数, 147–149
*   对易子, 193, 195–196
*   紧 Hausdorff 空间, 168
*   紧李群, 199
*   紧流形, 178
*   紧算子, 143–144
    *   谱, 248–249
*   紧自伴算子, 248–249
*   互补金属氧化物半导体 (CMOS), 115
*   复 Clifford 空间, 278
*   复多项式, 251
*   复值环绕数字信号, 54–55
*   复化, 58–59
    *   李代数的, 215–216
*   压缩, 96, 97
*   合流超几何方程, 388
*   共轭坐标运算, 287
*   共轭线性酉运算, 81
*   连通分支, 177–178, 199
*   连通拓扑空间, 227
*   约束方程, 338
*   连续函数, 26, 217, 222
*   连续线性算子, 233
*   连续算子, 137
*   连续谱, 156, 156*f*
*   传统计算机, 312
*   传统神经网络, 28–29
*   收敛, 365–367
*   凸组合, 40
*   凸锥, 79
*   凸目标函数, 29–30
*   卷积, 342–343, 345
*   卷积神经网络 (CNNs), 13, 21, 23–24, 37–38, 41, 346–347, 346–347, 347*f*
*   库珀对, 117, 121



## C
* 坐标域, 177, 199
* 坐标映射, 177, 199
* Cornwell 映射, 229–230
* 神经网络的成本函数, 28–30
* 协方差矩阵, 96
* COVECT, 60
* 协向量, 62, 63, 71
* 覆盖映射, 227
* 余零集, 341–342, 345, 346
* 产生算符, 273
* 跨安德烈夫反射 (CAR), 119
* 密码学问题, 317
* 晶体, 111
* CS, *参见* 柯西序列 (CS)
* 循环群, 316
* 循环向量, 158–159

## D
* D-wave 绝热量子计算机和计算, 122–124
* 达布向量, 295
* 数据挖掘, 21–23
  * 有界矩阵, 341–346
  * CNN 和量子卷积神经网络, 346–347
  * K 近邻分类, 334–335
  * K 近邻回归, 335–336
  * 核方法, 339–341
  * 学习类型和数据结构, 328–329
  * PAC 学习和 Vapnik-Chervonenkis 维数, 329–332
  * 量子 K 均值应用, 336
  * 量子机器学习应用, 327–328
  * 径向基函数核, 341
  * 回归, 332–333
  * SVC, 336–338
* DE, *参见* 微分方程 (DE)
* 德摩根律, 370
* 退相干, 91, 115, 122
* 去中心化特征提取语音识别系统, 328
* 深度学习, 23
  * 神经网络的激活函数和成本函数, 28–30
  * 神经网络内节点的仿射变换, 24
  * 神经网络学习的反向传播, 31–35
  * 单节点神经网络分类, 30–31
  * 卷积神经网络, 37–38
  * 神经网络的全局结构, 24–28
  * 机器学习和数据挖掘, 21–23
  * 仿射空间的多排序代数描述, 35–37
  * 循环神经网络, 38–40
  * 以及与量子的关系, 23–24
* 缺陷, 115
* δ函数势阱, 107–110
* 密度函数, 249–250
* 密度矩阵, 88, 91
* 密度算符, 249
* 导数型运算, 198
* 行列式, 73–74
* Deutsch 预言机, 307*f*
* Deutsch 问题
  * 描述, 307
  * Deutsch 预言机, 307*f*
  * 预言机, 308–309
  * 量子解, 309–310
* Deutsch-Jozsa 问题, 310–311
  * 描述, 310–311
  * 量子解, 311–312
* Deutsh-Jozsa 算法, 317
* 微分同胚, 180, 191
* 微分方程 (DE), 387
* 微分算符, 145
* Diffie–Hellman EEC 密钥交换, 324
* 扩散操作, 303
* 数字信号, 57
* 扩张卷积, 46
* 扩张, 44–45, 247
* 狄拉克海, 278
* 直接等距, 206
* 离散对数问题, 324
* 圆盘代数, 350–354
* 耗散算符, 240
* 不同的等距, 80
* 分配律, 5
* DiVincenzo 准则, 113
* 除法代数, 42–43
* 双对易子, 167
* 双对偶希尔伯特空间, 64–66
* 双对偶空间, 64
* 双切线方法, 322
* 加倍, 322
  * 运算, 321–322
* 下采样, 37–38



## D
* Drury-Arveson 空间, 353
* `Vd` 的对偶基, 61–62
* 对偶丛, 182–183
* 对偶空间
  * 基, 64
  * 用于量子, 60–64
* Dynkin 公式, 194

## E
* Earnshaw 定理, 116
* ECC, *参见* 椭圆曲线密码学 (ECC)
* ECs, *参见* 椭圆曲线 (ECs)
* 特征函数, 356, 387
* 特征值问题, 94–95
* 特征值, 95, 232, 356, 387
* 特征向量, 94–95, 96, 98–99, 99, 103–104, 387
* 电子自旋量子数, 112
* 电子, 112
* 椭圆曲线密码学 (ECC), 4–5, 318–319, 318–320, 318
* 椭圆曲线 (ECs), 183–184, 315, 373
  * 在...上的垂直点加法, 374*f*
  * 有限域上椭圆曲线的 MSA, 321–324
* 自同态, 73, 84, 132, 184
* 纠缠, 106, 139
* 方程约束, 67
* 等价关系, 171–172
* 本质有界可测函数, 166
* 以太坊, 318–319
* 欧拉角矩阵, 206–207
* 欧拉函数, 315–316
* 欧拉函数群, 316, 316, 317–318
* 扩展卷积, 49
* 外微分, 92–93

## F
* 面部模式, 327
* 因式分解, 373
* Fatou 定理, 352
* 特征核, 339
* 特征映射, 15–16, 17, 97–98, 340
* 费米能级, 283
* 费米子 Fock 空间, 276–277
  * Maya 图表示, 283–284
* 费米子 Fock 态, 277
* 费米子希尔伯特空间, 277
* 费米子梯子算符, 276–277
* 费米子, 265
* 纤维丛
  * 解析向量丛, 182–183
  * 基本拓扑和流形概念, 176–178
  * 椭圆曲线, 183–184
  * Hopf 纤维化, 186–187
    * 与布洛赫球, 187
    * 与球面 `S⁴`, 188
  * 线丛和向量丛, 181–182
  * 来自流形, 178–180
  * 代数商空间的 MSA, 171–173
  * 四元数, 184–186
  * 中的截面, 180–181, 181*f*
  * 拓扑商空间, 173–176
* 滤波, 21
* 终空间, 259
* 有限概念类, 330
* 有限域, 318
  * 在...上的椭圆曲线 MSA, 321–324
* 有限维希尔伯特空间, 243, 272
* 一阶微分方程, 349
* 通量量子比特, 121
* Fock 空间, 3–4, 57–58, 84, 377, 379
  * Bogoliubov 变换, 286
  * 玻色子占据数和梯子算符, 272–276
  * 费米子 Fock 空间和费米子梯子算符, 276–277
  * 多体系统和 Landau 多体展开, 287–288
  * 费米子 Fock 空间的 Maya 图表示, 283–284
  * Maya 图, 278–283
  * 准费米子和准玻色子空间, 286–287
  * Fock 空间内的粒子和 Fock 空间结构, 271–272
  * SBF 操作, 287



*   单体操作, 288
*   斯莱特行列式和复 Clifford 空间, 278
*   双体操作, 288
*   表示量子粒子的杨图, 285–286
*   FOIL 规则, 133
*   前向传播, 37
*   傅里叶变换, 355
*   Fredholm 积分, 356
*   自由粒子解, 108
*   弗罗贝尼乌斯范数, 147
*   Frobenius 协变式, 94, 206, 295
    *   矩阵, 93–94
*   Frobenius 范数, 142–143
*   Fubini-Study 度量, 80
*   泛函分析, 383–385
*   泛函演算, 93
*   基本群, 226
    *   Cornwell 映射, 229–230
    *   拓扑空间的同伦等价, 226–227
    *   同伦, 217–218
    *   说明, 225–226
    *   圈的起点等价, 219–220
    *   MSA 描述, 220–224
*   未来数据, 21

## G
*   规范变换, 128
*   镓 (Ga), 114
*   Galois 域, 319, 320, 323
*   Garding-Wightman 公理, 267
*   门控循环单元 (GRUs), 38
*   高斯核, 104
*   Gelfand 公式, 163
*   Gelfand 变换, 168–169
*   Gelfand-Naimark-Segal (GNS), 2
    *   构造, 158–162
*   通用计算机, 113
*   广义误差, 329
*   锗 (Ge), 114
*   万向节锁死, 207
*   滑移反射, 80
*   全局场结构, 3–5
    *   在量子和机器学习中, 5–6
*   GNS, *参见* 盖尔范德-奈马克-塞加尔 (GNS)
*   梯度下降算法, 34
*   Gram 矩阵, 16–17
*   Gram-Schmidt 正交归一化过程, 96
*   Gram-Schmidt 过程, 204
*   Grassmann 代数, 47
*   群胚, 6
*   Grover 算法, 313
*   Grover 搜索
    *   算法, 314–315
    *   问题, 312–313
        *   的解, 313–315
*   GRUs, *参见* 门控循环单元 (GRUs)
*   陀螺仪, 207

## H
*   Haar 测度, 300–301
*   Hadamard 门, 293, 296
*   Hahn–Banach 定理, 384
*   Hamilton 方程, 126–127
*   Hamilton 算符, 103–104
*   Hardy RKHS, 352
*   Hardy 空间, 352
*   谐振子, 104, 388
    *   代数解, 349–350
*   Hasse 定理, 323
*   Hausdorff 空间, 175–176
*   堆, 83–84
*   Heisenberg 代数, 265
*   Heisenberg 群, 266
    *   Weyl 形式的 CCR 和, 265–266
*   Heisenberg 矩阵, 195
*   Heisenberg 不确定性原理, 362
*   Hellinger–Toeplitz 定理, 237
*   Hermite 正交归一函数, 389
*   Hermite 多项式, 104, 388, 388, 389
*   启发式, 110
*   Hilbert 群, 291
*   Hilbert 空间, 2, 12, 12–13, 57, 58, 104, 111, 133, 238, 253, 255, 256, 272, 273, 276, 277, 302
    *   上的有界算子, 151–153
    *   中的闭算子, 135



## H
* 高维的, 298
* 可逆算子代数判据于, 153–155
* 的张量积的多类代数, 76–78
* 秩, 145–147
* 射线的, 78–79
* 环绕数字信号的, 48–49, 365–367
* Hilbert-Schmidt 有界算子, 142–143
* Hilbert-Schmidt 范数, 147
* Hilbert-Schmidt 算子, 142–143
* Holevo 定理, 110
* 全纯函数, 287
* 全纯泛函演算, 43
* Hom (V, C), 60
* 同胚映射, 176–177, 198–199
* 同胚
  * 涉及圆周区间, 175*f*
  * 实数商空间的, 174*f*
* 同态, 47–48
* 位似变换, 183
* 拓扑空间的同伦等价, 226–227
* 同伦逆, 226–227
* 同伦, 200, 203–204, 217–218, 223, 227–228
  * 平方, 222–223, 224
* Hopf 纤维化, 186–187
  * 带有布洛赫球, 187
  * 带有球面 S⁴, 188
* Hotelling 变换, 94–95
* Householder 反射, 304–305
* 超精细量子比特, 117
* 超群, 255, 257
* 超参数, 38
* 超平面, 339–340
* 现代公司, 327

## I
* 理想
  * 在巴拿赫代数中, 157–158
  * 在李代数中, 194–197
* 恒等门, 294
* 单位向量, 162
* 无限维希尔伯特空间, 3, 141, 243
* 循环的初始点等价, 219–220
* 初始投影, 259
* 初始空间, 259
* 内积空间, 12–13
* 实例空间, 329
* 积分器, 253
* 干涉, 105
* 内部导数, 92–93
* 内积, 68–71
* 交织, 138
* 逆傅里叶变换, 355
* 逆立体投影, 187
* 希尔伯特空间上的可逆算子代数判据, 153–155
* 离子阱制备, 116
* IonQ 为现代的量子计算, 327–328
* 离子的基本结构, 111–114
* 同源, 184
* 等距映射, 60–61, 80, 255–257
* 迭代过程, 25

## J
* Jacobi 恒等式, 192–193
* Jacobi 多项式, 389
* JJ, *参见* 约瑟夫森结 (JJ)
* Jordan 代数, 43, 353
* Jordan 恒等式, 354
* 约瑟夫森频率, 119–120
* 约瑟夫森结 (JJ), 107, 115, 117–121
* 约瑟夫森量子比特, 121
* 约瑟夫森超导效应, 118

## K
* K perp, 242
* k-means 过程, 30
* k-means 技术, 21–22
* k-median 技术, 21–22
* k-近邻 (KNN), 327
  * 分类, 334–335
  * 回归, 335–336
* Karhunen-Loeve 变换 (KLT), 94–95
* 核主成分分析 (KPCA), 97–98
* 核, 339–340
  * 矩阵, 98
  * 方法, 1, 339–341
    * 在实希尔伯特空间中, 15–17
* 动能, 288
* KLT, *参见* Karhunen-Loeve 变换 (KLT)
* KNN, *参见* k-近邻 (KNN)
* KPCA, *参见* 核主成分分析 (KPCA)

## L
* 梯子操作, 272–273




## L
* 阶梯算符, 272–276, 273–274
* 拉格朗日乘子, 337, 337
* 拉格朗日-西尔维斯特展开, 206
* 拉格朗日-西尔维斯特插值公式, 94, 296
* 拉盖尔多项式, 388, 388
* 朗道多体展开, 287–288
* 朗道-曾纳跃迁, 126
* 晶格 L, 183, 183–184
* 学习
  * 速率, 32
  * 类型和数据结构, 328–329
* 勒贝格积分理论, 370
* 勒贝格测度, 372
* 平方绝对值可积复值函数的勒贝格空间, 243
* 勒贝格平方可积函数, 104
* 左移算符, 236
* 左侧恒等关系, 223
* 勒让德多项式, 388
* 莱布尼茨法则, 209
* 莱布尼茨法则, 71, 84, 93
* 列维-奇维塔符号, 213–214
* 李代数, 186, 191
  * 关于李群拓扑流形性质的简述, 198–202
  * 李代数的复化, 215–216
  * 维数, 192–194
  * 矩阵李群的形式描述, 202–207
  * 其中的理想, 194–197
  * 李群与李代数之间的映射, 208–215
  * MSA 观点, 191–192
  * 李群的表示和 MSA, 197–198
* 李括号, 191
* 李导数, 92–93
* 李群, 193, 197, 225, 225–226, 228, 228–229
* 李-特洛特公式, 194
* 线丛, 181–182
* 线性组合, 62–63
* 线性映射, 131, 132
* 线性算符, 131–134
* 线性, 132, 146
  * 条件, 132
* 线性化, 208
* 利普希茨条件, 136, 200
* 长短期记忆（LSTM）, 38, 39–40
* 环
  * 环的等价类, 219*f*
  * 的初始点等价, 219–220
* LSTM, *参见* 长短期记忆（LSTM）
* 卢默-菲利普斯定理, 233

## M
* 机器学习, 21–23, 327, 328
  * 算法, 339
  * 界矩阵, 341–346
  * CNN 和量子卷积神经网络, 346–347
  * K 近邻分类, 334–335
  * K 近邻回归, 335–336
  * 核方法, 339–341
  * 学习类型和数据结构, 328–329
  * PAC 学习和瓦普尼克-钦宁恩科维奇维数, 329–332
  * 量子 K-means 应用, 336
  * 量子机器学习应用, 327–328
  * 径向基函数核, 341
  * 回归, 332–333
  * SVC, 336–338
* 磁量子数, 112
* Majorana 分数 JJ 效应, 119
* Majorana 粒子, 116
* 流形
  * 关于李群拓扑流形性质的简述, 198–202
  * 概念, 176–178
  * 纤维丛, 178–180
* 多体系统, 287–288
* 多排序代数（MSA）, 1–2, 57–58
  * 作为巴拿赫代数, 51–52
  * 对于巴拿赫* 和 C* 代数, 52–53
  * 仿射空间的描述, 35–37
  * 巴拿赫空间的描述, 49–51
  * 量子中 MSA 的基本例证, 12–13
  * 方法论, 2–3
  * 希尔伯特空间张量积的, 76–78
  * 张量向量空间的, 71–73




## M
* 李群与李代数之间的映射, 208–215
* 矩阵, 83
  * 用于代数商空间, 171–173
  * 刻画, 268
  * 布洛赫球的复表示, 91–92
  * 基本群的描述, 220–224
  * 有限域上椭圆曲线, 321–324
  * 内微分、外微分和李导数, 92–93
  * 核主成分分析, 97–98
  * 李群, 201
    * 形式描述, 202–207
  * 运算, 83–85
  * 主成分分析, 94–97
  * 量子比特与矩阵表示, 85–91
  * 矩阵和 Frobenius 协变矩阵的谱, 93–94
  * SVD, 98–101
* 最大池化, 37–38
* 最大图册, 177
* 最大间隔分类器, 336–337
* Maya 图, 278–283, 377–378
  * 费米子 Fock 空间的表示, 283–284
* 可测空间, 369, 370
* 测度空间, 369
* 测量算子, 160
* Mercer 定理, 355–357
* 度量张量, 73
* 最小界矩阵, 342
* 闵可夫斯基空间, 201
* Mittag-Leffler 实值 RKHS, 353
* Mittag–Leffler 函数, 353
* 混合态, 91
* Möbius 带, 178–179
* Möbius 带, 178–179
* Möbius 结构, 179
* Mobius 变换, 256–257
* 动量, 264–265
* 动量算子, 239
* 动量型微分算子, 137
* 幺半群, 6
* 单调子序列, 365–366
* MSA, *参见* 多排序代数 (MSA), 多排序代数 (MSA)
* 多层感知器, 24
* 多线性形式, 68–71
* 多量子比特输入门, 297–299
* 乘法, 193
  * 因子, 346
* 乘法版本, 252–253
* 多排序代数 (MSA), 369
  * 用于描述可测空间和测度空间, 369
* 部分等距的多排序代数, 260–263
## N
* Neumann 级数, 150
* 神经网络 (NNs), 21, 23–24, 24
* 中性原子, 114
* 第九点引理, 374
* NNs, *参见* 神经网络 (NNs)
* 无克隆定理, 110–111
* 无界函数, 251
* 无界算子, 238, 243–246
  *另见* 有界算子
  * 谱, 251–252
* 非交换 Banach 代数, 147–149
* 非常值全纯映射, 174
* 非凸目标函数, 29–30
* 非确定性多项式 (NP), 313
* 非空集, 340
* 非纠缠, 139
* 非负性, 161
* 不可分希尔伯特空间, 362–363
* 非零特征值, 361
* NORM, 50–51, 85
* 范数界, 250
* 范数收敛, 165
* 正规算子, 243–246, 248
  * 谱, 248–249
* 正规子群, 227–228
* 归一化, 37–38
* 归一化束缚态解, 109
* 归一化循环向量, 162
* 归一化特征向量, 96–97
* NOT 门, 293
* NP, *参见* 非确定性多项式 (NP)
* 数算子, 273, 274–275, 276, 277
* 数值域, 134, 239–241
## O
* 目标函数, 25
* 可观测量, 249–250



## O
* 占据算符, 276
* 单体操作, 288
* 单体算符, 288, 288
* 单参数半群, 241
* 在线学习, 329
* 开映射定理, 384
* 运算符号, 2
* 算子, 237
  * 有界算子, 135–138
  * Hilbert 空间中的闭算子, 135
  * 紧算子, 143–144
  * Hilbert-Schmidt 算子, 142–143
  * 线性算子, 131–134
  * 范数, 300
  * 纯张量 *与*. 纯态算符, 138–140
  * 拓扑, 165–166
  * 迹类算子, 141–142
* 光学离子阱量子比特, 117
* 预言机, 303–304
  * 用于 Deutsch 问题求解, 308–309
* 轨道角动量量子数, 112
* 轨道, 112
* 轨道, 112
* 正交矩阵, 99
* 正交单粒子态, 285
* 标准正交基, 64
* 外积, 66–68

## P
* PAC 学习, *参见* 概然近似正确学习（PAC 学习）
* 抛玻色空间, 286–287
* 抛费米空间, 286–287
* 并行算法, 345
* 并行卷积算法, 45
* 平行四边形法则, 146
* 参数化, 201
* 部分等距, 259–260, 262
  * 用于多排序代数, 260–263
* 部分算子, 3
* 部分转数, 223
* Fock 空间中的粒子与 Fock 空间结构, 271–272
* 分区, 380
* 路径连通性, 200, 200*f*, 202
* 路径连通空间, 177–178, 199, 219, 220
* 路径连通拓扑空间, 221
* Paul 阱, 116
* Pauli 基, 87–88
* Pauli 不相容原理, 112
* Pauli 群, 298–299
* Pauli 矩阵, 88, 89–90, 90, 205, 212, 297, 298
* Pauli 原理, 276
* Pauli 旋转矩阵, 296
* Pauli 旋转算符, 295–297, 296
* PCA, *参见* 主成分分析（PCA）
* PCT, *参见* 主成分变换（PCT）
* 峰值, 365–366
* 周期函数, 148–149, 149
* Petri 网, 27
* 相位估计, 302–303
* 相位量子比特, 121
* 相移门, 294–295
* 光子型量子比特, 116
* 光子, 111
* 置位网, 27
* Plancherel 定理, 355
* 点加法, 321–322
* 点谱, 156, 157
* 逐点卷积公式, 45, 48–49
* 极化恒等式, 146
* 多元箭头, 67–68
* 多元图, 3
* 多元图, 6, 221, 257, 262, 267–268
  * 仿射空间的, 36*f*
  * 用于复化, 59*f*
  * 用于对偶空间构造, 61*f*
  * 涉及 C\*代数的同态的, 158*f*
  * 矩阵运算, 83*f*
  * Banach 代数中子群的, 150*f*
  * 辛向量空间的, 267*f*
* 位置, 264–265
* 幂部分等距, 262–263
* 预 Hilbert 空间, 149
* 预测, 21



## P
* 本原元, 319
* 主成分分析 (PCA), 94–97
* 主成分变换 (PCT), 21–22
* 主成分, 95
* 主量子数, 112
* 可能近似正确学习 (PAC learning), 329, 329–332
* 处理单元, 24
* 积空间, 385
* 投影算子, 165–166, 358, 358, 359
* 射影空间, 78–79, 79–81
* 投影值测度 (PVM), 360–361
* 伪逆运算, 260
* 纯态算子, 138–140
* 纯态, 62–63
* 纯张量, 138–140
* PVM, *参见* 投影值测度 (PVM)

## Q
* QA, *参见* 量子退火 (QA)
* QCNN, *参见* 卷积神经网络的量子版本 (QCNN)
* QCNNs, *参见* 量子卷积神经网络 (QCNNs)
* QDataSet, 328
* QDs, *参见* 量子点 (QDs)
* QFT, *参见* 量子傅里叶变换 (QFT)
* 二次无约束二值优化模型 (QUBO 模型), 122
* 量子算法, 303
* 量子退火 (QA), 107, 327
  * 基础, 105–107
  * 方法, 328
* 量子线路, 291–292, 303, 336
* 量子计算, 328
* 量子计算, 313
  * 应用
    * Deutsch 问题描述, 307
    * Deutsch-Jozsa 问题描述, 310–311
    * Diffie–Hellman EEC 密钥交换, 324
    * ECC, 318–320
    * Grover 搜索问题, 312–313
    * 有限域上椭圆曲线的 MSA, 321–324
    * Deutsch 问题解的 oracle, 308–309
    * Deutsch-Jozsa 问题的量子解, 311–312
    * Deutsch 问题的量子解, 309–310
    * 从代数观点看 Shor 的密码学问题, 315–317
    * Grover 搜索问题的解, 313–315
    * Shor 问题解, 317–318
  * Haar 测度, 300–301
  * 多量子比特输入门, 297–299
  * Pauli 旋转算子, 295–297
  * QFT 与相位估计, 302–303
  * 与量子线路, 291–292
  * 反射, 304–305
  * 单量子比特量子门, 292–295
  * Solovay–Kitaev 定理, 301–302
  * 交换操作, 299
  * 均匀叠加与振幅放大, 303–304
  * UQGS, 299–300
* 量子控制, 328
* 量子卷积神经网络 (QCNNs), 328, 346–347
* 量子点 (QDs), 115, 121–122
* 量子场论, 362
* 量子傅里叶变换 (QFT), 302–303, 302
* 量子门, 292–293
* 量子希尔伯特空间, 2
  * 复化, 58–59
  * 行列式, 73–74
  * 双对偶希尔伯特空间, 64–66
  * 量子中使用的对偶空间, 60–64
  * 量子技术背后的显式希尔伯特空间, 57–58
  * 射线希尔伯特空间, 78–79
  * 希尔伯特空间张量积的多类代数, 76–78
  * 张量向量空间的多类代数, 71–73
  * 多线性形式、楔积和内积, 68–71
  * 外积, 66–68
  * 射影空间, 79–81
  * 张量代数, 74–75
* 量子干涉, 105
* 量子 K-means 应用, 336
* 量子 K-means 聚类, 336
* 量子机器学习应用, 327–328
* 量子多类代数, 1–19
  * 代数结构, 1–2
  * 量子中 MSA 的基本例证, 12–13



# 索引

*   全局域场结构, 3–5
    *   在量子和机器学习中, 5–6
*   实希尔伯特空间中的核方法, 15–17
*   多排序代数方法论, 2–3
*   R-模, 17–19
*   特定机器学习域场结构, 6–7
*   特定量子场结构, 7
*   有限时信号作为内积空间, 13–15
*   向量空间作为多排序代数, 8–11
*   量子力学等价, 266–267
*   量子存储器, 110–111
*   量子粒子，杨图表示, 285–286
*   量子解, 307
    *   对 Deutsch 问题, 309–310
    *   对于 Deutsch-Jozsa 问题, 311–312
*   量子光谱学, 328
*   量子态, 327
*   量子叠加, 106
*   量子技术, 236, 316
*   卷积神经网络的量子版本 (QCNN), 23–24
*   夸克味本征态, 285–286
*   准静态控制, 107
*   四元数, 184–186, 207
*   量子比特, 62, 105, 110
    *   制造, 114–116
    *   和矩阵表示, 85–91
*   QUBO 模型, *参见* 二次无约束二元优化模型 (QUBO 模型)
*   商映射, 173
*   商空间, 171–172, 172, 173, 229

## R

*   R-模, 17–19
*   R-向量, 58
*   拉比频率, 127
*   径向基函数 (RBF), 341
*   径向基函数核, 341
*   射频 (RF), 116
*   范围投影, 259
*   秩, 146, 375
*   RBF, *参见* 径向基函数 (RBF)
*   实值函数, 356–357
*   重新聚类, 23
*   矩形脉冲函数, 28
*   循环神经网络 (RNNs), 21, 38–40, 328
*   递归步骤, 22
*   反射, 80, 304–305
    *   操作, 305*f*
    *   算子, 305
*   自反、对称、传递等价关系 (RST 等价关系), 78
*   回归, 328–329, 332–333
*   迁移过程, 284
*   再生核希尔伯特空间 (RKHSs), 15, 350
    *   在 C 和圆盘代数上, 350–354
    *   在 R 上, 354–355
*   剩余谱, 157, 232–233, 235, 244
*   解析集 (RsT), 155–156
*   解析集, 250–251
*   RF, *参见* 射频 (RF)
*   岭回归, 332
*   Riemann-Lebesgue 引理, 355
*   Riesz 表示定理 (RRT), 60, 146, 241–242, 350
*   Riesz–Markov 定理, 361–362
*   右移算子, 235
*   RKHSs, *参见* 再生核希尔伯特空间 (RKHSs)
*   RNNs, *参见* 循环神经网络 (RNNs)
*   旋转, 80
    *   矩阵, 295
*   RRT, *参见* Riesz 表示定理 (RRT)
*   RsT, *参见* 解析集 (RsT)
*   RST 等价关系, *参见* 自反、对称、传递等价关系 (RST 等价关系)

## S

*   S-MULT 操作, 45, 50
*   Saltus 矩阵, 253, 360
*   SBF 空间, *参见* Segal–Bargmann–Fock 空间 (SBF 空间)
*   标量, 344, 346
*   标量系数, 70–71
*   标量乘法, 10, 11
*   Schauder 基, 49–50, 145–147



# 索引

*   薛定谔方程, 103, 107, 109–110, 266
*   薛定谔对量子的表征, 103–104
*   施瓦茨函数, 266–267
*   SCROC, 361
*   二次量子化, 272–273, 287, 287–288
*   纤维丛中的截面, 180–181, 181*f*
*   Segal–Bargmann–Fock 空间 (SBF 空间), 287, 287
*   自伴有界算子, 240
*   自伴矩阵, 88–89, 98–99
*   自伴算子, 236–239, 241–243, 243, 245, 246
    *   谱, 248–249
*   半群, 241
*   可分希尔伯特空间, 363
*   序列连续性, 136
*   序列预测, 329
*   斜线性形式, 60, 161
*   尖锐、主、弥散、基电子 (SPDF 电子), 112
*   破碎, 331–332
*   破碎过程, 330, 330–331
*   Shor 算法, 315
*   Shor 的贡献, 315–316
*   从代数观点看的 Shor 密码学问题, 315–317
*   Shor 问题，解, 317–318
*   Shor 量子算法, 4–5
*   σ-代数, 370
*   σ-域, 370
*   σ-有限, 166, 371–372
*   符号超群, 258
*   签名集, 8–9, 60, 66–67, 67, 76, 131
*   硅 (Si), 114
*   碳化硅, 115–116
*   硅空位中心 (SiVs), 111
*   单连通李群, 200
*   单一 transmon 量子比特, 121
*   单体操作, 288
*   单体算子, 287
*   单节点神经网络分类, 30–31
*   单粒子算子, 287, 288
*   单粒子态, 271
*   单量子比特量子门, 292–295
*   奇点, 201
*   奇异值分解 (SVD), 21–22, 98–101
*   SiVs, *参见* 硅空位中心 (SiVs)
*   SK 定理, *参见* Solovay–Kitaev 定理 (SK 定理)
*   松弛变量, 338
*   Slater 行列式, 84, 278
*   Slater 矩阵, 278
*   平滑, 21
*   软分类, 339–340
*   Softmax, 29, 29
*   Solovay–Kitaev 定理 (SK 定理), 230, 301, 301–302
*   SOT, *参见* 强算子拓扑 (SOT)
*   稀疏对角矩阵, 99
*   SPDF 电子, *参见* 尖锐、主、弥散、基电子 (SPDF 电子)
*   特定机器学习场结构, 6–7
*   特定量子场结构, 7
*   矩阵的谱, 93–94
*   算子的谱
    *   有界算子与数值范围, 239–241
    *   正规算子与无界算子, 243–246
    *   纯态与密度函数, 249–250
    *   自伴算子, 241–243
    *   Banach 空间上算子的谱, 233–236
    *   自伴、正规和紧算子的谱, 248–249
    *   有界算子的谱分类, 231–233
    *   谱分解, 246–247
    *   谱测度与谱定理, 252–253
    *   谱与预解集, 250–251
    *   无界算子的谱, 251–252
    *   对称、自伴和无界算子, 236–239
*   有界算子的谱分类, 231–233
*   谱分解, 246–247



## S
* 谱映射定理, 251
* 谱测度, 252–253
* 谱定理, 252–253, 357–361, 360, 361
    * 对于正规算子, 253
* 频谱图, 328
* 谱, 250–251
    * 在 Banach 代数中, 155–157
    * 对于无界算子, 251–252
* 自旋下, 112
* 自旋上, 112
* 自旋, 115, 122
* 堆叠层, 37–38
* 堆栈, 46, 46
* 标准归纳技术, 148
* 态, 249–250
* Stieltjes 积分, 253
* Stone-von Neumann 等价, 266–267
* Stone-von Neumann 定理, 264, 265
* Stone 定理, 263–264
* Stone–Weierstrass 定理, 383–384, 384
* 步幅, 247
* 步幅型卷积, 47
* 强算子收敛, 165
* 强算子拓扑 (SOT), 165
* Sturm-Liouville 微分方程, 104, 127
* Sturm–Liouville 方程, 387
* Banach 代数中的子群, 149–151
* 子空间, 203–204
* 超导电性, 117–121
* 超导电子学, 107
* 超导材料, 115
* 超导量子比特, 115
* 超导体, 115
* 超电流态, 118–119
* 叠加, 62–63
* 量子比特叠加, 106
* 监督学习, 21
* 支持向量分类 (SVC), 336–337
* 支持向量机, 21, 340
* SVC, *参见* 支持向量分类 (SVC)
* SVD, *参见* 奇异值分解 (SVD)
* 交换操作, 299
* 对称 Fock 空间, 272
* 对称群, 379
* 对称算子, 236–239, 246
* 量子系统的对称性, 80
* 辛向量空间, 267–268
    * 空间的多项图, 267*f*
* Szego 核, 352
## T
* T-MULT, 76
* 切空间, 209, 210
* 切向量, 209, 210
* 张量代数, 74–75
* 张量积方法, 58
* 张量空间, 74
* 张量向量空间，多型代数用于, 71–73
* 时间无关薛定谔方程, 109, 349
* 时限信号, 341–342
    * 的代数, 44–47
    * 作为内积空间, 13–15
* Toeplitz-Hausdorff 定理, 134
* 拓扑量子比特, 116
* 拓扑商空间, 173–176
* 拓扑空间, 199, 200, 217
    * 的同伦等价, 226–227
* 迹类算子, 85–86, 141–142
* 迹函数, 168
* 矩阵的迹, 84
* 过渡函数, 182
* 转换网, 27
* 平移, 80
* 转置 (TRAN), 85
    * 矩阵的, 100
* 转置, 90
* 囚禁离子, 114, 116–117
    * 技术, 107, 116–117
* 三角不等式, 136
* 三角乘积不等式, 153
* 平凡丛, 180
* 线丛中的平凡化, 182*f*
* 截断移位, 263
* 隧穿, 107–110
* 逐元比较, 23
* 两体操作, 288



## T
* 双体算符, 287
* 二乘二函数矩阵, 360
* 二维数字信号, 342
* 二维希尔伯特空间, 276
* 二维时限矩阵, 341–342
* 双粒子希尔伯特空间, 272
* 双粒子算符, 287, 288
* 双粒子态, 271
* 双到一同态映射, 229
* Tychonoff 拓扑, 385

## U
* 一元运算, 320
* 无界算符, 236–239, 238, 240, 245
* 一致有界性原理, 384
* 一致连续, 355
* 均匀叠加, 303–304
* 均匀化定理, 183
* 单位圆, 194
* 单位向量, 134
* 单位代数, 42
* 单位结合代数, 250
* 酉矩阵, 205–206, 297
* 酉运算, 255–257
* 通用覆盖群, 227–229
  * Cornwell 映射, 229–230
  * 拓扑空间的同伦等价, 226–227
  * 同伦, 217–218
  * 说明基本群, 225–226
  * 圈的初始点等价, 219–220
  * MSA 对基本群的描述, 220–224
* 通用量子门集 (UQGS), 299–300, 299–300
* 无监督学习, 21–22
* UQGS, *参见* 通用量子门集 (UQGS)

## V
* V-ADD 运算, 45
* 真空态, 267, 283, 286–287
* 价电子, 116
* Vandermonde 矩阵, 160, 333, 333
* Vapnik-Chervonenkis 维数 (VC 维数), 329–332, 330
* VC 维数, *参见* Vapnik-Chervonenkis 维数 (VC 维数)
* 向量, 278, 328
  * 丛, 181–182
  * 空间, 1
    * 到代数, 41–44
    * 条件, 132
    * 图, 10–11
    * 作为多排序代数, 8–11
    * 算符, 50
* 旋量, 207
* 冯·诺依曼代数, 159, 166–167, 257
  * 其中的交换子, 167–168
  * 算子拓扑, 165–166

## W
* 波函数, 104
  * 解, 349–350
* 弱算符收敛, 165
* 弱算符拓扑 (WOT), 165
* 楔, 68–71
* Weierstrass 逼近定理, 383
* Weierstrass 标准型, 321
* Weyl 正则对易关系 C\* 代数, 269–270
* Weyl CCR C\* 代数, 270
* Weyl 形式的 CCR 与海森堡群, 265–266
* Weyl 关系, 269
* Wigner 自同构, 80
* WOT, *参见* 弱算符拓扑 (WOT)
* 环绕界矩阵, 345
* 环绕界向量, 345, 345
* 环绕卷积, 49
* 环绕数字信号, 57
  * Banach\* 代数, 53–54
  * 复值, 54–55
  * 希尔伯特空间, 48–49, 365–367

## Y
* Young 图, 282, 377, 380–381
  * 量子粒子, 285–286
* 镱 (Yb), 113

## Z
* Zeeman 离子阱量子比特, 117
* 零元素, 320
* 零律, 375
* 零粒子态, 271
