
函数（如前所述）。理想情况下，对于 tanh 和整流线性函数等激活函数，我们应该以略有不同的方式初始化权重和偏置。此问题将在下方的问题中进一步讨论。__init__ 方法以 self.params = [self.w, self.b] 结束。这是一种将与该层相关的所有可学习参数打包在一起的便捷方式。稍后，Network.SGD 方法将使用 params 属性来确定 Network 实例中哪些变量可以学习。

set_input 方法用于设置层的输入并计算相应的输出。我使用 inpt 而不是 input，因为 input 是 Python 的内置函数，而干扰内置函数往往会导致不可预测的行为和难以诊断的 bug。请注意，我们实际上以两种不同的方式设置输入：作为 self.inpt 和 self.inpt_dropout。这样做是因为在训练期间我们可能希望使用丢弃法（dropout）。如果是这种情况，我们希望移除比例为 self.p_dropout 的神经元。这就是 set_input 方法中倒数第二行的函数 dropout_layer 所做的事情。因此，self.inpt_dropout 和 self.output_dropout 在训练期间使用，而 self.inpt 和 self.output 用于所有其他目的，例如，在验证和测试数据上评估准确率。

ConvPoolLayer 和 SoftmaxLayer 类的定义与 FullyConnectedLayer 类似。事实上，它们非常接近，因此我不会在此处摘录代码。如果您感兴趣，可以在本节稍后部分查看 network3.py 的完整清单。

不过，有几个值得一提的细微差别。最明显的是，在 ConvPoolLayer 和 SoftmaxLayer 中，我们都以适合该层类型的方式计算输出激活值。幸运的是，Theano 使这变得容易，提供了用于计算卷积、最大池化和 softmax 函数的内置操作。

不太明显的是，当我们介绍 softmax 层时，从未讨论过如何初始化权重和偏置。在其他地方我们曾认为，对于 sigmoid 层，我们应该使用适当参数化的正态随机变量来初始化权重。但该启发式论证特定于 sigmoid 神经元（并且，经过一些修改，也适用于 tanh 神经元）。然而，没有特别理由该论证应适用于 softmax 层。因此，没有 *先验* 的理由再次应用该初始化。与其那样做，不如我将所有权重和偏置初始化为 0。这是一种相当 *即兴* 的程序，但在实践中效果足够好。

好了，我们已经查看了所有层类。那么 `Network` 类呢？让我们先看看 `__init__` 方法：

```python
class Network(object):

    def __init__(self, layers, mini_batch_size):
        """Takes a list of `layers`, describing the network architecture, and
        a value for the `mini_batch_size` to be used during training
        by stochastic gradient descent.

        ...
        """
        self.layers = layers
        self.mini_batch_size = mini_batch_size
        self.params = [param for layer in self.layers for param in layer.params]
        self.x = T.matrix("x")
        self.y = T.ivector("y")
        init_layer = self.layers[0]
        init_layer.set_input(self.x, self.x, self.mini_batch_size)
        for j in xrange(1, len(self.layers)):
            prev_layer, layer = self.layers[j-1], self.layers[j]
            layer.set_input(
                prev_layer.output, prev_layer.output_dropout, self.mini_batch_size)
        self.output = self.layers[-1].output
        self.output_dropout = self.layers[-1].output_dropout
```

这大部分不言自明，或几乎如此。代码行 `self.params = [param for layer in ...]` 将每层的参数打包到一个列表中。如前所述，`Network.SGD` 方法将使用 `self.params` 来确定 `Network` 中哪些变量可以学习。代码行 `self.x = T.matrix("x")` 和 `self.y = T.ivector("y")` 定义了名为 `x` 和 `y` 的 Theano 符号变量。这些将用于表示网络的输入和所需输出。

现在，这不是一个 Theano 教程，因此我们不会过于深入地探讨这些是符号变量*意味着什么。但大致意思是，这些代表数学变量，*而非* 显式值。我们可以对这些变量做所有通常的事情：相加、相减、相乘，应用函数，等等。事实上，Theano 提供了操作此类符号变量的许多方法，做诸如卷积、最大池化等事情。但最大的好处是能够使用反向传播算法的一种非常通用的形式进行快速符号微分。这对于将随机梯度下降应用于各种网络架构非常有用。特别是，the

> *Theano 文档提供了 Theano 的良好介绍。如果您卡住了，查看网上可用的其他教程之一可能会有所帮助。例如，本教程涵盖了许多基础知识。

接下来的几行代码定义了网络的符号输出。我们首先通过以下行设置初始层的输入：

```
init_layer.set_input(self.x, self.x, self.mini_batch_size)
```

请注意，输入是一次一个小批量地设置的，这就是为什么那里有小批量大小的原因。另请注意，我们传入了两次输入 self.x：这是因为我们可能以两种不同的方式使用网络（使用或不使用 dropout）。然后 for 循环将符号变量 self.x 通过 Network 的各层向前传播。这使我们能够定义最终的 output 和 output_dropout 属性，它们在符号上表示网络的输出。

既然我们了解了如何初始化 Network，现在让我们看看如何使用 SGD 方法进行训练。代码看起来很长，但其实结构相当简单。代码后面有解释性注释。

```python
def SGD(self, training_data, epochs, mini_batch_size, eta,
    validation_data, test_data, lmbda=0.0):
    """Train the network using mini-batch stochastic gradient descent."""
    training_x, training_y = training_data
    validation_x, validation_y = validation_data
    test_x, test_y = test_data

    # compute number of minibatches for training, validation and testing
    num_training_batches = size(training_data)/mini_batch_size
    num_validation_batches = size(validation_data)/mini_batch_size
    num_test_batches = size(test_data)/mini_batch_size

    # define the (regularized) cost function, symbolic gradients, and updates
    l2_norm_squared = sum([(layer.w**2).sum() for layer in self.layers])
    cost = self.layers[-1].cost(self)+
    0.5*lmbda*l2_norm_squared/num_training_batches
    grads = T.grad(cost, self.params)
    updates = [(param, param-eta*grad)
               for param, grad in zip(self.params, grads)]

    # define functions to train a mini-batch, and to compute the
    # accuracy in validation and test mini-batches.
    i = T.lscalar() # mini-batch index
    train_mb = theano.function(
        [i], cost, updates=updates,
        givens={
        self.x:
        training_x[i*self.mini_batch_size: (i+1)*self.mini_batch_size],
        self.y:
        training_y[i*self.mini_batch_size: (i+1)*self.mini_batch_size]
        })
    validate_mb_accuracy = theano.function(
        [i], self.layers[-1].accuracy(self.y),
        givens={
        self.x:
        validation_x[i*self.mini_batch_size: (i+1)*self.mini_batch_size],
        self.y:
        validation_y[i*self.mini_batch_size: (i+1)*self.mini_batch_size]
        })
test_mb_accuracy = theano.function(
    [i], self.layers[-1].accuracy(self.y),
    givens={
        self.x:
        test_x[i*self.mini_batch_size: (i+1)*self.mini_batch_size],
        self.y:
        test_y[i*self.mini_batch_size: (i+1)*self.mini_batch_size]
    })

self.test_mb_predictions = theano.function(
    [i], self.layers[-1].y_out,
    givens={
        self.x:
        test_x[i*self.mini_batch_size: (i+1)*self.mini_batch_size]
    })

# Do the actual training
best_validation_accuracy = 0.0
for epoch in xrange(epochs):
    for minibatch_index in xrange(num_training_batches):
        iteration = num_training_batches*epoch+minibatch_index
        if iteration
        print("Training mini-batch number {0}".format(iteration))
        cost_ij = train_mb(minibatch_index)
        if (iteration+1)
        validation_accuracy = np.mean(
            [validation_mb_accuracy(j) for j in xrange(num_validation_batches)])
        print("Epoch {0}: validation accuracy {1:2.2"
        epoch, validation_accuracy))
        if validation_accuracy > best_validation_accuracy:
        print("This is the best validation accuracy to date.")
        best_validation_accuracy = validation_accuracy
        best_iteration = iteration
        if test_data:
        test_accuracy = np.mean(
            [test_mb_accuracy(j) for j in xrange(num_test_batches)])
        print("The corresponding test accuracy is {0:2.2"
        test_accuracy))
print("Finished training network.")
print("Best validation accuracy of {0:2.2"
best_validation_accuracy, best_iteration))
print("Corresponding test accuracy of {0:2.2"
```

前几行很直接，将数据集分为 x 和 y 组件，并计算每个数据集中使用的小批量数量。接下来的几行更有趣，展示了使用 Theano 的一些乐趣。让我们明确地摘录这些行：

```python
# define the (regularized) cost function, symbolic gradients, and updates
l2_norm_squared = sum([(layer.w**2).sum() for layer in self.layers])
cost = self.layers[-1].cost(self)+
0.5*lmbda*l2_norm_squared/num_training_batches
grads = T.grad(cost, self.params)
updates = [(param, param-eta*grad)
for param, grad in zip(self.params, grads)]
```

在这几行中，我们在符号上设置了正则化对数似然代价函数，在梯度函数中计算相应的导数以及相应的参数更新。Theano 让我们只需几行就能完成所有这些。唯一隐藏的是，计算代价涉及对 cost 的调用。
