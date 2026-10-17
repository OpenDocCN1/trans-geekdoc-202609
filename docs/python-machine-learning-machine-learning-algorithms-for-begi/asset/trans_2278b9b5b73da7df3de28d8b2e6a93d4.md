

在“bias”命名的阶段中，如图 4.3 所示，我们可以注意到权重被求和并添加了一个偏置。这个和随后通过一个激活函数。激活函数形成一个开合的门。激活函数可以输出 1 或 0，基于阈值进行判断，或者生成概率。关于概率部分，它可能使用 sigmoid 或整流线性函数。关于激活函数的更多内容将在本章后面讨论。

激活函数的输出是神经网络的加权、预测输出。它在上图中表示为 ![image](d2d_images/image047.png)。![image](d2d_images/image047.png)可能是回归、二进制或分类值，具体取决于数据集的性质和所需的输出。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.4 激活函数

![image](d2d_images/chapter_title_below.png)

在本节中，我们将快速回顾用于 ANN 的常见激活函数。

\- 阈值或阶跃函数：如果权重和输入的和低于特定阈值，则为零；如果高于阈值，则为一。回顾我们之前讨论的门类比。

\- Sigmoid 函数：它是最广泛使用的激活函数。它看起来像阈值函数，但更平滑。Sigmoid 激活函数适合生成概率。这意味着该函数的输出范围始终在零和一之间。例如，如果我们正在调查一张图片，输出将是它是猫还是狗的概率？！

\- 双曲正切：这个函数是 sigmoid 函数的拉伸版本，因为它的范围是 -1 到 1。当我们需要更深的梯度和更陡的导数时，会选择这个函数。因此，sigmoid 函数和双曲正切函数之间的选择取决于梯度强度要求。

\- 整流线性单元 (RELU)：这个函数通常应用于强化学习应用。从其名称来看，它是一个经过整流的线性函数。这意味着它在负域中的值为零，并且线性增加，即对于正输入 x，它给出输出 x，否则为零。RELU 的一个主要优点是与双曲正切和 sigmoid 函数相比的简单性。这是设计深度神经网络时需要考虑的一个主要点。

根据我们试图近似的函数的特征，我们可以选择能实现更快近似的激活函数，这意味着更快的学习过程。例如，sigmoid 函数在分类问题中表现优于 RELU。这意味着更快的训练过程和更快的收敛。可以使用自定义函数。但是，如果我们试图学习的函数的性质不太清楚，那么最好从 RELU 作为通用近似器开始，然后逆向工作。表 4.1 总结了所提及的激活函数及其图形表示和方程。

| 激活函数 || 方程 || 图形 |

| --- | --- | --- |

| 阶跃单元 || ![image](d2d_images/image087.png) || ![image](d2d_images/image043.png) |

| Tanh || ![image](d2d_images/image112.png) || ![image](d2d_images/image070.png) |

| Sigmoid || ![image](d2d_images/image072.png) || ![image](d2d_images/image006.png) |

| 双曲正切 || ![image](d2d_images/image014.png) || ![image](d2d_images/image029.png) |

| 平滑 ReLU || ![image](d2d_images/image100.png) || ![image](d2d_images/image118.png) |

表 5.1 激活函数

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.5 工作示例

![image](d2d_images/chapter_title_below.png)

在本节中，我们将给出一个示例，翻译前几节中解释的一些概念。假设我们有一个训练好的神经网络，如图 4.4 所示。这意味着我们有优化后的权重，如图所示。输入层包含一组特征：年龄、到医院的距离、性别和收入。另一方面，输出是依赖于输入特征的变量。它是一个人住院的概率。如果我们以年龄为例，可以说人越老，越有可能住院。就性别而言，统计上男性比女性更有可能住院。收集的数据可以用于根据输入特征进行多种预测，这就是神经网络工作的实现。本示例中的隐藏层被视为一个黑盒，包含产生住院概率的神经元和权重。机器可以被训练以预测到医院的距离与住院概率之间的关系。因此，神经网络必须首先尝试在数据中找到模式，并找出这些不同模式之间的关系。这是在进行其他处理或决策之前对数据的一种理解。一旦训练完成，我们就可以输入从目标数据集中提取的不同特征。例如，一条记录可以是这样的：年龄 65 岁，性别为女性，到医院的距离适中，收入高。神经网络是一种神奇的方法，它以一种模仿人类神经元的聪明方式处理特征后，来预期和预测所需的结果。

神经网络根据神经网络架构估计输入特征的不同组合，以识别数据集中的模式。它可以被视为一个黑盒，但更深入的观察使我们能够看到权重、输入和隐藏层之间的模式。

![image](d2d_images/image061.png)

图 5.4 神经网络，住院概率示例

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.6 学习过程（权重如何工作）

![image](d2d_images/chapter_title_below.png)

我们通常需要机器学习，因为我们有大量数据需要处理和分析。因此，如果我们有一个大型数据集，我们将其输入馈入神经网络以进行预测。第一步是确定神经元的权重。它们可以基于初始假设确定，也可以根据应用特征和所需输出预定义。

神经网络的正常流向输出 ![image](d2d_images/image047.png)。也就是说，输入特征被馈入隐藏层，在那里进行计算。然后，网络流继续，直到我们得到所需的输出。这种流被称为：前向传播。此时，智能错误处理出现。得到的 ![image](d2d_images/image047.png)与实际值进行比较。目标是使它们之间的差异尽可能小，即最小化错误。如果我们想象一个孩子学习数学的类比，这会更清晰。如果他对一个特定问题回答 8，而准确答案是 5，那么我们就有 3 的错误。在这种情况下，计算必须重新执行，直到我们尽可能接近 8。

