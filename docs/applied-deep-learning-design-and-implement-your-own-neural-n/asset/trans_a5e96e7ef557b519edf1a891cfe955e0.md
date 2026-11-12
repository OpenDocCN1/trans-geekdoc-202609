

现在，通过对 y(t) 应用 SoftMax 激活函数，可以确定字母出现的概率，如图 6.67 所示：

![](img/7e519fee1b702b91799cdf1664598392_473_0.png)

图 6.67: y(t) 即将出现的字母的概率

现在，如果我们观察前面的概率，最高概率是 0.42，对应字母 H，那么是否意味着 H 应该出现在字母 E 之后？

不，在这里，我们为字母 H 获得最高概率是因为网络只针对两个字母进行了训练，因此到目前为止网络什么也没学到。所以，我们迄今为止讨论的是 RNN 中的前向传播。

## RNN 中的反向传播

现在，让我们了解 RNN 中的反向传播，以了解 RNN 中权重更新的过程是如何进行的。

我们知道，在前向传播中，输入值进入网络，然后在每个时间戳只向前移动。但在使用反向传播时，我们会沿时间向后移动以更新权重，因此我们也称其为时间反向传播（BPTT）。请参阅图 6.68 了解示例：

![](img/7e519fee1b702b91799cdf1664598392_473_1.png)

图 6.68: RNN 在时间上的展开

假设 \( y_{(t)} \) 是我们进行预测后得到的值，\( Y(t) \) 是实际输出值；交叉熵损失可按如下计算：

\( E(t)[Y(t), y(t)] = -Y(t)log(y(t)) \) (6.11)
\( E(t)[Y, y] = -\Sigma Y(t)log(y(t)) \) (6.12)

因此，我们需要为所有输入时间戳计算此损失，然后将它们相加以得到总损失。这里，每个时间戳的权重相同。让我们简要概述 RNN 中反向传播应遵循的步骤：

![](img/7e519fee1b702b91799cdf1664598392_474_0.png)

图 6.69: 循环神经网络（多对多）

![](img/7e519fee1b702b91799cdf1664598392_474_1.png)

图 6.70: 时间反向传播（BPTT）

- 1. 首先，使用预测值和实际输出值计算交叉熵损失（误差）。
- 2. 必须对每个时间戳展开网络。
- 3. 必须对每个时间戳及其相应的权重参数计算梯度。
- 4. 这些梯度随时间不断减小。如果它们变得非常小，可能无法长时间记忆（见图 6.70 中的彩色线，这些线以反向表示，代表时间反向传播 [BPTT]）。图 6.70 中梯度从 $y_t$ 减小到 $y_1$。
- 5. 最后，更新 RNN 的权重。

![](img/7e519fee1b702b91799cdf1664598392_475_0.png)

图 6.71: 时间反向传播（BPTT）相对于循环关系参数（如公式 (6.5 到 (6.10)] 所示）。

让我们深入了解反向传播的过程。在进入 RNN 的反向传播之前，我们必须准确了解参数的维度。因此，让我们先按如下方式定义参数：

\(x_i \in R^n\)

其中 n 表示输入是 n 维实数：

\(s_i \in R^d\)

其中 d 表示 \(s_i\) 是 d 维实数：

\(y_i \in R^k\)

其中 k 表示输出有 k 个类别。因此，

\(U \in R^{n*d}\)

和

\(V \in R^{d*k}\)

和

\(W \in R^{d*d}\)

为了更好地理解这些参数，请观察图 6.72：

![](img/7e519fee1b702b91799cdf1664598392_476_0.png)

图 6.72: RNN 的参数

## 现在如何训练网络？

前面问题的答案是使用反向传播。让我们通过字符自动完成的一个示例来理解这一点。我们假设单词由词汇表中的四个字符组成，即 (d、e、p 和 <stop>)，如图 6.73 所示。这里 <stop> 表示单词已完成。

在每个时间戳，我们希望预测其中一个字母。这项任务最合适的输出函数是什么？（SoftMax）这项任务最合适的损失函数是什么？（交叉熵）。请参阅图 6.73：

![](img/7e519fee1b702b91799cdf1664598392_477_0.png)

现在，假设我们随机初始化 U、V 和 W 的值，并且 RNN 通过前向传播预测概率，如图 6.74 所示：

![](img/7e519fee1b702b91799cdf1664598392_478_0.png)

图 6.74: 下一个字母预测示例

我们还知道概率的实际值或真实值，如图 6.75 所示：

![](img/7e519fee1b702b91799cdf1664598392_478_1.png)

图 6.75: 下一个字母预测示例

那么，网络在这里产生的总损失是多少。我们如何进行反向传播以最小化此损失并在此更新权重参数（U、V 和 W）？

针对前面提到的问题，我们应该了解按以下方式描述的随时间变化的反向传播的基本现象。

因此，这里总损失是每个时间戳上所有损失的总和。损失表示如图 6.76 所示。

![](img/7e519fee1b702b91799cdf1664598392_479_0.png)

图 6.76: 下一个字母预测示例

因此，仔细观察前面的图，网络的总交叉熵损失按如下给出：

\( L(\theta) = \sum_{t=1}^{T} L_t(\theta) \)

时间戳 t 处的损失按如下给出：

\( L_t(\theta) = -log(y_{tc}) \)

这里，c 是时间戳 t 的真实类别

T 是时间戳的总数；

\(\gamma_{tc}\) 是时间戳 t 处字符的预测概率。

现在，对于反向传播，我们还需要找出关于 U、V 和 W 的梯度。

因此，首先，让我们看看损失函数 \(L(\theta)\) 关于 V 的导数，如下所示：

\[
\frac{\partial L(\theta)}{\partial V}
\]

这里，V 是一个矩阵，因此我们可以按如下方式写出：

\[
\nabla_V L(\theta)
\]

因此，我们在前一章的反向传播部分讨论过如何进行此导数。因此，我们可以写出如下内容：

\[
\frac{\partial L(\theta)}{\partial V} = \sum_{t=1}^T \frac{\partial L_t(\theta)}{\partial V} \quad (6.13)
\]

求和中的每一项都是损失函数关于输出层权重的导数。现在，让我们看看损失函数关于 W 的导数，如下所示：

\[
\frac{\partial L(\theta)}{\partial W}
\]

可以按如下给出：

\[
\frac{\partial L(\theta)}{\partial W} = \sum_{t=1}^T \frac{\partial L_t(\theta)}{\partial W} \quad (6.14)
\]

- 现在，根据导数的链式法则，\(\frac{\partial L_t(\theta)}{\partial W}\) 的值可以通过将从 \(L_t(\theta)\) 到 W 的所有路径的梯度相加来确定。
- 那么，你能说出连接 W 与损失函数 \(L_t(\theta)\) 的所有路径是什么吗？因此，这里我们将有 t 条路径。
- 现在，让我们先考虑这里的最后一条路径 \(L_4(\theta)\)。
- 这里我们知道，\(L_4(\theta)\) 的值取决于 S4 的值；

S4 的值取决于 S3 的值和 W 的值；

S3 的值取决于 S2 的值和 W 的值；

S2 的值取决于 S1 的值和 W 的值；

S1 的值取决于 S0 的值和 W 的值；

其中 S0 是固定的起始状态。

![](img/7e519fee1b702b91799cdf1664598392_481_0.png)

图 6.77: 对前序状态的依赖

因此，如果我们观察前面的图，可以说网络是有序的。当我们谈论有序网络时，这里每个状态的值是按顺序逐个计算的，例如 S1-S2-S3-S0 等等。

因此，根据链式法则，我们有：

\(\frac{\partial L_4(\theta)}{\partial W} = \sum_{t=1}^{T} \frac{\partial L_t(\theta)}{\partial S4} \frac{\partial S4}{\partial W}\)

现在，\(\frac{\partial L_t(\theta)}{\partial s4}\) 我们在前一章的反向传播部分已经讨论过了。现在，让我们找出 \(\frac{\partial S4}{\partial W}\) 的值

因此，我们知道：

\(S4 = \sigma(W(S3 + B))\)

现在，S4 的最终导数，即 \(\frac{\partial S4}{\partial W}\) 可以分为以下两部分：

**显式导数**：在计算 \(\frac{\partial S4}{\partial W}\) 的显式导数时，我们可以将所有其他输入视为常数。

**隐式导数**：在此部分中，我们将所有连接 S4 与 W 的间接路径相加。

因此，我们可以将前面的总导数写为显式导数和隐式导数之和，如下所示：

\(\frac{\partial S4}{\partial W} = \frac{\partial^* S4}{\partial W} + \frac{\partial S4}{\partial S3} \frac{\partial S3}{\partial W}\)

其中 \(\frac{\partial^* S4}{\partial W}\) 是显式导数，\(\frac{\partial S4}{\partial S3} \frac{\partial S3}{\partial W}\) 是隐式导数。显式导数中的 * 号表示我们仅对 W 求导，并将所有其他参数视为常数。

因此，我们现在有

\(\frac{\partial S4}{\partial W} = \frac{\partial^* S4}{\partial W} + \frac{\partial S4}{\partial S3} \frac{\partial S3}{\partial W}\)

同样，\(\frac{\partial S3}{\partial W}\) 可以分为显式和隐式两部分，如以下方程所示：

\(\frac{\partial S4}{\partial W} = \frac{\partial^* S4}{\partial W} + \frac{\partial S4}{\partial S3}\left(\frac{\partial^* S3}{\partial W} + \frac{\partial S3}{\partial S2} \frac{\partial S2}{\partial W}\right)\)

同样，\(\frac{\partial^* S3}{\partial W}\) 是显式导数，\(\frac{\partial S3}{\partial S2} \frac{\partial S2}{\partial W}\) 是隐式导数。同样，我们有 \(\frac{\partial S2}{\partial W}\)，可以进一步分为显式和隐式部分，如下所示：

\(\frac{\partial S4}{\partial W} = \frac{\partial^* S4}{\partial W} + \frac{\partial S4}{\partial S3} \frac{\partial^* S3}{\partial W} + \frac{\partial S4}{\partial S3} \frac{\partial S3}{\partial S2}\left(\frac{\partial^* S2}{\partial W} + \frac{\partial S2}{\partial S1} \frac{\partial S1}{\partial W}\right) \quad (6.14)\)

因此，这里 \(\frac{\partial^* S2}{\partial W}\) 又是显式导数，\(\frac{\partial S2}{\partial S1} \frac{\partial S1}{\partial W}\) 是隐式导数。

现在，我们可以再次按如下方式写出：

\(\frac{\partial S4}{\partial W} = \frac{\partial^* S4}{\partial W} + \frac{\partial S4}{\partial S3} \frac{\partial^* S3}{\partial W} + \frac{\partial S4}{\partial S3} \frac{\partial S3}{\partial S2} \frac{\partial^* S2}{\partial W} + \frac{\partial S4}{\partial S3} \frac{\partial S3}{\partial S2} \frac{\partial S2}{\partial S1}\left(\frac{\partial^* S1}{\partial W}\right)\)

因此，前面的方程显示了计算最终导数的完整公式。现在，为了简化计算，我们对网络中的一些路径进行了短路；因此，我们可以按如下方式写出：

