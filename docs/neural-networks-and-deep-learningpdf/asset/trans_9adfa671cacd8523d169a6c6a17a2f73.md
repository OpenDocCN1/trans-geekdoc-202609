

## 四个基本方程的证明（可选）

我们现在来证明四个基本方程 (BP1)-(BP4)。这四个方程都是多元微积分中链式法则的推论。如果你对链式法则很熟悉，那么我强烈建议你在继续阅读之前先尝试自己推导一遍。

让我们从方程 (BP1) 开始，它给出了输出误差 \(\delta^L\) 的表达式。要证明这个方程，请回顾，按定义

\(\delta_j^L = \frac{\partial C}{\partial z_j^L}.\) (36)

应用链式法则，我们可以将上面的偏导数用关于输出激活值的偏导数来重新表示，

\(\delta_j^L = \sum_k \frac{\partial C}{\partial a_k^L} \frac{da_k^L}{dz_j^L},\) (37)

其中求和是对输出层中所有神经元 \(k\) 进行。当然，第 \(k\) 个神经元的输出激活值 \(a_k^L\) 仅在第 \(j\) 个神经元的输入权重 \(z_j^L\) 为 \(k=j\) 时才依赖于它。因此，当 \(k \neq j\) 时，\(da_k^L/dz_j^L\) 消失。结果，我们可以将前一个方程简化为

\(\delta_j^L = \frac{\partial C}{\partial a_j^L} \frac{da_j^L}{dz_j^L}.\) (38)

回顾 \(a_j^L = \sigma(z_j^L)\)，右边的第二项可以写为 \(\sigma'(z_j^L)\)，方程变为

\(\delta_j^L = \frac{\partial C}{\partial a_j^L} \sigma'(z_j^L),\) (39)

这正是 (BP1) 的分量形式。

接下来，我们将证明 (BP2)，它给出了误差 \(\delta^l\) 关于下一层误差 \(\delta^{l+1}\) 的方程。为此，我们希望将 \(\delta_j^l = \partial C/\partial z_j^l\) 重新表示为关于 \(\delta_k^{l+1} = \partial C/\partial z_k^{l+1}\) 的形式。我们可以使用链式法则来做到这一点，

\d
elta_j^l = \frac{\partial C}{\partial z_j^l} \tag{40}
= \sum_k \frac{\partial C}{\partial z_k^{l+1}} \frac{\partial z_k^{l+1}}{\partial z_j^l} \tag{41}
= \sum_k \frac{\partial z_k^{l+1}}{\partial z_j^l} \delta_k^{l+1}, \tag{42}

在最后一行中，我们交换了右边两项的顺序，并代入了 \(\delta_k^{l+1}\) 的定义。要计算最后一行的第一项，请注意

\(z_k^{l+1} = \sum_j w_{kj}^{l+1} a_j^l + b_k^{l+1} = \sum_j w_{kj}^{l+1} \sigma(z_j^l) + b_k^{l+1}.\) \tag{43}

对两边求导，我们得到

\(\frac{\partial z_k^{l+1}}{\partial z_j^l} = w_{kj}^{l+1} \sigma'(z_j^l).\) \tag{44}

将其代回 (42) 中，我们得到

\(\delta_j^l = \sum_k w_{kj}^{l+1} \delta_k^{l+1} \sigma'(z_j^l).\) \tag{45}

这正是 (BP2) 的分量形式。

我们想证明的最后两个方程是 (BP3) 和 (BP4)。它们也遵循链式法则，其证明方式与上面两个方程类似。我将它们作为练习留给你。

## 练习

- 证明方程 (BP3) 和 (BP4)。

这就完成了反向传播四个基本方程的证明。证明看起来可能很复杂。但实际上，它只是仔细应用链式法则的结果。不那么简洁地说，我们可以把反向传播看作一种通过系统地应用多元微积分中的链式法则来计算代价函数梯度的方法。反向传播的全部内容就是这样——其余都是细节。

## 反向传播算法

反向传播方程为我们提供了一种计算代价函数梯度的方法。让我们将其显式地写成算法形式：

- 1. **输入 x：** 为输入层设置相应的激活值 \(a^l\)。

- 2. **前向传播：** 对每个 \(l = 2, 3, ..., L\)，计算 \(z^l = w^l a^{l-1} + b^l\) 和 \(a^l = \sigma(z^l)\)。

- 3. **输出误差** \(\delta^L\)：计算向量 \(\delta^L = \nabla_a C \odot \sigma'(z^L)\)。

- 4. **误差回传：** 对每个 \(l = L - 1, L - 2, ..., 2\)，计算 \(\delta^l = ((w^{l+1})^T \delta^{l+1}) \odot \sigma'(z^l)\)。

- 5. **输出：** 代价函数的梯度由 \(\frac{\partial C}{\partial w_{jk}^l} = a_k^{l-1} \delta_j^l\) 和 \(\frac{\partial C}{\partial b_j^l} = \delta_j^l\) 给出。

审视这个算法，你就能明白为什么它被称为反向传播。我们从最后一层开始，逆向计算误差向量 \(\delta^l\)。逆向遍历网络看起来可能很奇怪。但如果你思考反向传播的证明，逆向移动是代价函数是网络输出函数这一事实的结果。要理解代价函数如何随更早的权重和偏置而变化，我们需要反复应用链式法则，逆向通过各层来得到可用的表达式。

## 练习

- **带单个修改神经元的反向传播** 假设我们修改前馈网络中的单个神经元，使得该神经元的输出由 \(f(\sum_j w_j x_j + b)\) 给出，其中 \(f\) 是除 Sigmoid 以外的某个函数。在这种情况下，我们应该如何修改反向传播算法？

- **带线性神经元的反向传播** 假设我们在整个网络中将通常的非线性 \(\sigma\) 函数替换为 \(\sigma(z) = z\)。请针对这种情况重写反向传播算法。

正如我上面描述的，反向传播算法计算单个训练样本的代价函数梯度，$C = C_x$。在实际中，通常将反向传播与随机梯度下降等学习算法相结合，我们会对许多训练样本计算梯度。特别是，给定一个包含 \(m\) 个训练样本的小批量，下面的算法基于该小批量执行一次梯度下降学习步骤：

- 1. **输入一组训练样本**

- 2. **对每个训练样本** \(x\)：设置相应的输入激活值 \(a^{x,1}\)，并执行以下步骤：

  - **前向传播**：对每个 \(l = 2, 3, ..., L\)，计算 \(z^{x,l} = w^l a^{x,l-1} + b^l\) 和 \(a^{x,l} = \sigma(z^{x,l})\)。
  - **输出误差** \(\delta^{x,L}\)：计算向量 \(\delta^{x,L} = \nabla_a C_x \odot \sigma'(z^{x,L})\)。
  - **误差回传**：对每个 \(l = L-1, L-2, ..., 2\)，计算 \(\delta^{x,l} = ((w^{l+1})^T \delta^{x,l+1}) \odot \sigma'(z^{x,l})\)。

- 3. **梯度下降**：对每个 \(l = L, L-1, ..., 2\)，根据规则 \(w^l \to w^l - \frac{\eta}{m} \sum_x \delta^{x,l} (a^{x,l-1})^T\) 更新权重，并根据规则 \(b^l \to b^l - \frac{\eta}{m} \sum_x \delta^{x,l}\) 更新偏置。

当然，在实际中实现随机梯度下降，你还需要一个生成训练样本小批量的外层循环，以及一个遍历多个训练轮次的外层循环。为了简洁，我已省略这些内容。

## 反向传播的代码

抽象地理解了反向传播后，我们现在可以理解上一章中用于实现反向传播的代码。回顾上一章，代码包含在 Network 类的 update_mini_batch 和 backprop 方法中。这些方法的代码是上述算法的直接翻译。特别是，update_mini_batch 方法通过计算当前 mini_batch 训练样本的梯度来更新 Network 的权重和偏置：

```
class Network(object):
    ...
    def update_mini_batch(self, mini_batch, eta):
        """Update the network's weights and biases by applying
gradient descent using backpropagation to a single mini batch.
The "mini_batch" is a list of tuples "(x, y)", and "eta"
is the learning rate."""
nabla_b = [np.zeros(b.shape) for b in self.biases]
nabla_w = [np.zeros(w.shape) for w in self.weights]
for x, y in mini_batch:
    delta_nabla_b, delta_nabla_w = self.backprop(x, y)
    nabla_b = [nb+dnb for nb, dnb in zip(nabla_b, delta_nabla_b)]
    nabla_w = [nw+dnw for nw, dnw in zip(nabla_w, delta_nabla_w)]
self.weights = [w-(eta/len(mini_batch))*nw
    for w, nw in zip(self.weights, nabla_w)]
self.biases = [b-(eta/len(mini_batch))*nb
    for b, nb in zip(self.biases, nabla_b)]
```

大部分工作由这一行 `delta_nabla_b, delta_nabla_w = self.backprop(x, y)` 完成，它使用 `backprop` 方法来计算偏导数 \(\partial C_x / \partial b^l_j\) 和 \(\partial C_x / \partial w^l_{jk}\)。`backprop` 方法密切遵循上一节的算法。有一处小变化——我们使用略有不同的层索引方式。此变化是为了利用 Python 的一个特性，即使用负列表索引从列表末尾开始倒数，例如，`l[-3]` 是列表中倒数第三个条目。`backprop` 的代码如下，连同几个辅助函数，这些函数用于计算 \(\sigma\) 函数、其导数 \(\sigma'\) 以及代价函数的导数。包含这些内容后，你应该能够以自包含的方式理解代码。如果有什么让你困惑，查阅代码的原始描述（和完整清单）可能会有所帮助。

```
class Network(object):
    ...
    def backprop(self, x, y):
        """Return a tuple "(nabla_b, nabla_w)" representing the
gradient for the cost function C_x.  "nabla_b" and
"nabla_w" are layer-by-layer lists of numpy arrays, similar
to "self.biases" and "self.weights."""
        nabla_b = [np.zeros(b.shape) for b in self.biases]
        nabla_w = [np.zeros(w.shape) for w in self.weights]
        # feedforward
        activation = x
        activations = [x] # list to store all the activations, layer by layer
        zs = [] # list to store all the z vectors, layer by layer
        for b, w in zip(self.biases, self.weights):
            z = np.dot(w, activation)+b
            zs.append(z)
            activation = sigmoid(z)
            activations.append(activation)
        # backward pass
        delta = self.cost_derivative(activations[-1], y) * \
            sigmoid_prime(zs[-1])
        nabla_b[-1] = delta
        nabla_w[-1] = np.dot(delta, activations[-2].transpose())
        # Note that the variable l in the loop below is used a little
        # differently to the notation in Chapter 2 of the book.  Here,
        # l = 1 means the last layer of neurons, l = 2 is the
        # second-last layer, and so on.  It's a renumbering of the
        # scheme in the book, used here to take advantage of the fact
        # that Python can use negative indices in lists.
        for l in xrange(2, self.num_layers):
```

