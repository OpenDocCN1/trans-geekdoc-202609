

一个冗长的递归函数需要大量的内存，因为需要将所有数据压入栈中。为了防止溢出，Python 将默认最大递归限制设置为 1000。

同样，RNN 的处理需求会随着每个新阶段的增加而增加。正如 Python 设置了最大递归限制一样，每个 RNN 都有一个固定的可处理阶段数。

将递归函数转换为基于循环的函数的过程称为 *展开*。为了更好地可视化 RNN，你可以通过为每个待处理的阶段插入节点来展开它。例如，假设 [Figure 9-1](#14_9788126592555-ch09.xhtml#c09-fig-0001) 中的 RNN 有三个阶段。展开后 RNN 的样子如图 [Figure 9-2](#14_9788126592555-ch09.xhtml#c09-fig-0002) 所示（为清晰起见已移除权重）。

![FIGURE 9-2: Unrolling an RNN makes it easy to visualize its operation.](images/9788126592555-fg0902.png)

[FIGURE 9-2:](#14_9788126592555-ch09.xhtml#rc09-fig-0002) Unrolling an RNN makes it easy to visualize its operation.

如 [Figure 9-2](#14_9788126592555-ch09.xhtml#c09-fig-0002) 所示，`y(2)` 依赖于当前输入（`x[i](2)` 的加权和）以及前一阶段的输出。开发者将过去阶段的组合结果称为节点的 *状态*。

简单来说，RNN 与普通神经网络的区别在于 RNN 的一个或多个节点具有状态。如果节点具有状态，它就可以将前一阶段的结果应用于当前阶段。这种使用过去结果的能力解释了为什么 RNN 在处理语言和其他序列数据时如此受欢迎。

### Training RNNs

如本章前面 [Figure 9-2](#14_9788126592555-ch09.xhtml#c09-fig-0002) 所示，展开 RNN 会得到一个前馈网络，该网络在不同阶段接收输入（`x[i](0)`、`x[i](1)` 等）。这种行为意味着 RNN 可以像普通前馈网络一样进行训练。一种流行的训练方法称为时间反向传播（backpropagation through time，BPTT），它将反向传播方法应用于 RNN。[Chapter 7](#12_9788126592555-ch07.xhtml) 讨论了反向传播的基本理论。

随着你设计具有更多处理阶段的 RNN，节点数量会急剧增长。因此，RNN 遭受着困扰所有复杂神经网络的两个问题：梯度消失和梯度爆炸。[Chapter 7](#12_9788126592555-ch07.xhtml) 解释了这些问题以及它们如何降低神经网络的性能。

为了弥补 BPTT 的不足，研究人员设计了替代训练方法。截断时间反向传播（Truncated backpropagation through time，TBPTT）使用有限数量的阶段进行训练。实时递归学习（Real-time recurrent learning，RTRL）不展开 RNN，而是使用网络输出和状态相对于其权重的偏导数进行训练。

与其专注于新的训练方法，一些研究人员发明了 RNN 的全新变体。这些变体提供了 RNN 的所有优点，但不易受梯度消失和梯度爆炸的影响。最流行的变体是长短期记忆（long short-term memory，LSTM）单元和门控循环单元（gated recurrent units，GRUs）。本章讨论这两种变体并演示如何使用它们。

## Creating RNN Cells

正如普通神经网络由节点组成一样，RNN 由 *单元* 组成。在大多数 RNN 文献中，单元是 RNN 的一部分，它接收输入并产生单个输出值。

TensorFlow RNN 的单元没那么简单。根据文档，TensorFlow RNN 的“单元是任何具有状态并执行某种操作的实体，该操作接受输入矩阵。此操作产生输出矩阵……”。换句话说，RNN 单元具有状态，对输入矩阵进行操作，并产生输出矩阵。

在 TensorFlow 应用中，构建 RNN 的过程从创建单元开始。具体来说，该过程包括三个步骤：

1. **使用每个单元的单元数创建 RNN 单元类的实例。**

   每个单元类都是 `tf.nn.rnn_cell.RNNCell` 的子类。

2. **调用一个函数，例如 `tf.nn.static_rnn`，该函数基于单元创建 RNN。**

   此函数接受输入张量的列表并返回 RNN 的输出和状态。

3. **使用步骤 2 的输出计算损失。**

   通过在会话中启动优化器来最小化损失。

`RNNCell` 类在本次讨论中起着核心作用。它不能在代码中实例化，但很重要，因为它是 TensorFlow RNN 单元类的基类，其中包括 `BasicRNNCell`、`BasicLSTMCell`、`LSTMCell` 和 `GRUCell`。[Figure 9-3](#14_9788126592555-ch09.xhtml#c09-fig-0003) 展示了继承自 `RNNCell` 的七个 TensorFlow 类。

![FIGURE 9-3: Each subclass of RNNCell represents a different kind of RNN cell.](images/9788126592555-fg0903.png)

[FIGURE 9-3:](#14_9788126592555-ch09.xhtml#rc09-fig-0003) Each subclass of RNNCell represents a different kind of RNN cell.

`RNNCell` 类定义了可通过其实例访问的属性和方法。[Table 9-1](#14_9788126592555-ch09.xhtml#c09-tbl-0001) 列出了 `RNNCell` 的八个属性。

[TABLE 9-1](#14_9788126592555-ch09.xhtml#rc09-tbl-0001) Properties of the RNNCell Class

| **Property** || **Description** |

| --- | --- |

| `state_size` || The shape(s) of the cell's state(s) |

| --- | --- |

| `output_size` || The shape of the cell’s output |

| `graph` || Graph of operations contained in the cell |

| `losses` || Losses to be applied to the cell's processing |

| `update` || Tensors used to update the cell’s weights |

| `variables` || List of the cell's variables |

| `weights` || List of the cell’s weights |

| `scope_name` || Name of the scope containing the variables |

`RNNCell` 的状态可以用一个或多个张量表示。因此，应用程序可以将 `state_size` 分配为整数、`TensorShape`、整数元组或 `TensorShape` 元组。应用程序必须将 `output_size` 分配为整数或 `TensorShape`。

[Table 9-1](#14_9788126592555-ch09.xhtml#c09-tbl-0001) 中其余属性很直接。`losses` 属性标识一个张量或张量列表/元组，标识单元在其处理期间应应用的损失。表中最后三个属性提供了对单元变量和变量作用域的访问。

除了属性外，`RNNCell` 类还定义了一组方法，其中大多数自定义单元的行为。[Table 9-2](#14_9788126592555-ch09.xhtml#c09-tbl-0002) 列出了四个特别有用的方法并提供了每个方法的描述。

[TABLE 9-2](#14_9788126592555-ch09.xhtml#rc09-tbl-0002) Methods of the RNNCell Class

| **Method** || **Description** |

| --- | --- |

| `add_loss(losses, inputs=None)` || Add loss tensors |

| --- | --- |

| `add_update(updates, inputs=None)` || Add updates to the cell's weights |

| `add_variable(name, shape, dtype=None,`` initializer=None, regularizer=None,`` trainable=true)` || Adds a new variable to the layer |

| `zero_state(batch_size, dtype)` || Returns a zero-filled tensor for initializing the cell's state |

在列出的方法中，`zero_state` 特别受欢迎。它创建一个零填充的张量或零填充张量的列表，适用于初始化 RNN 的状态。返回值形状取决于方法 `batch_size` 参数和单元的 `state_size` 属性。

### Creating a basic RNN

`RNNCell` 的最简单子类是 `BasicRNNCell`。其构造函数如下所示：

```
BasicRNNCell(num_units, activation=tf.nn.tanh, reuse=None)
```

