

```python
# Hidden layer activation
y = self.hidden_activation(y)

# Decode to produce output
z = self.output_layer(y)
z = self.output_activation(z)

return z

@property
def model(self):
    inputs = {
        "items": Input((None,), sparse=True, dtype=tf.int64),
        "weights": Input(
            (None,), sparse=True, dtype=tf.float32,
        ),
    }
    model = Model(inputs, self.call(inputs))

    return model
```

- **__init__ (第 9–25 行):** 此方法初始化模型类。它保存多个模型配置参数，并初始化激活层和输出密集层。

- **build (第 27–37 行):** 此方法创建两个权重，embedding（即嵌入查找表）和 bias（即添加到密集层的偏置项）。请注意，两个权重均可训练 (trainable=True)。在 Keras 中，使用 build 方法是初始化其他可训练权重的首选方式。

- **call (第 39–61 行):** 此方法实现自编码器模型的主要逻辑。

  - 第 40–44 行检索项索引（项的整数表示）及其对应的权重。如果 weights 无法从 inputs 字典中获取，则假设所有权重均等于 1。

  - 第 47–49 行使用 tf.nn.embedding_lookup_sparse 执行嵌入查找。这将生成隐藏层输出。此处，我们假设从前面步骤检索到的输入为左对齐的稀疏张量。或者，如果我们选择使用带填充的项索引密集表示（由于 0 默认用作填充，这必然需要基于 1 的索引），那么我们也可以使用 keras.layers.Embedding 层并在初始化时设置 mask_zero=True。这也是在 PyTorch 中实现嵌入查找的方式。

  - 第 52 行添加偏置项。

  - 第 55–59 行通过应用激活函数并将隐藏层的结果传递到输出层（输出层将由另一个激活函数激活）来完成自编码器的实现。

- **model 属性 (第 63–73 行):** 此属性用于检查我们的实现是否可以编译为图。我们可以使用 print(model.model.summary()) 打印模型架构，结果如下：

模型："model_5"

| 层 (类型) | 输出形状 | 参数数 | 连接到 |
|---|---|---|---|
| items (InputLayer) | [(None, None)] | 0 | [] |
| weights (InputLayer) | [(None, None)] | 0 | [] |
| tf.compat.v1.nn.embedding_lookup_sparse (TFOpLambda) | (None, 128) | 0 | ['items[0][0]', 'lookup_sparse_5', 'weights[0][0]'] |
| tf.___operators___.add_5 (TFOpLambda) | (None, 128) | 0 | ['tf.compat.v1.nn.embedding_lookup_sparse_5[0][0]'] |
| hidden_activation (Activation) | (None, 128) | 0 | ['tf.___operators___.add_5[0][0]'] |
| output_layer (Dense) | (None, 1000) | 129000 | ['hidden_activation[0][0]'] |
| output_activation (Activation) | (None, 1000) | 0 | ['output_layer[0][0]'] |

总参数量: 129000 (503.91 KB)
可训练参数量: 129000 (503.91 KB)
不可训练参数量: 0 (0.00 Byte)

None

我们可以按如下方式测试我们的实现

```python
inputs = {
   "items": tf.ragged.constant([[1, 2], [3, 0, 4]]).to_sparse(),
   "weights": tf.ragged.constant([[1.3,2.7], [2.1,4.6,0.8]]).to_sparse()
}

model = Autoencoder(num_items=1000, emb_size=128)
z = model(inputs) # use the input to produce output, (2, 1000)
```

PyTorch 实现如下

```python
import torch

class Autoencoder(torch.nn.Module):
    def __init__(self, num_items, emb_size):
        super().__init__()
        self.embed = torch.nn.Embedding(
            num_items, emb_size, padding_idx=0
        )
        self.bias = torch.nn.Parameter(torch.zeros([1, emb_size]))
        self.decoder = torch.nn.Sequential(
            torch.nn.ReLU(),
            torch.nn.Linear(emb_size, num_items),
            torch.nn.Sigmoid()
        )

    def forward(self, items, weights=None):
        if weights is None:
            # equal weights
            weights = torch.ones([items.shape[0], 1], dtype=torch.float32)

        # Implement the sparse dense layer (batch_size, emb_size)
        embed = self.embed(items)
        # Apply weights
        embed *= weights[:, :, None]
        # Sum together embeddings
        embed = embed.sum(dim=1)

        # Add bias
        y = embed + self.bias

        # Hidden layer activation
        z = self.decoder(y)

        return z
```

- **__init__ (第 4–14 行):** 此方法初始化模型类。与 Keras 模型不同，我们使用 torch.nn.Embedding 初始化嵌入查找，它接受带 0 填充的密集张量 (pad_idx=0)。偏置项也在此方法中指定，而不是像 Keras 那样在单独的方法中指定。隐藏层之后的其余层被组合成一个 Sequential 层（Keras 也有此容器层类，因此在 Keras 实现中也可以选择将这些层组合在一起）。

- **forward (第 16–34 行):** 此方法实现自编码器的主要逻辑。与使用稀疏输入不同，此方法假设 items 和 weights 均使用带 0 填充的密集张量来表示左对齐的不规则张量。在第 22–26 行，我们首先将项列表传递给嵌入查找，然后沿前两个维度（批次和序列）应用权重，最后通过求和对序列维度进行汇聚。

同样，我们可以使用一些伪输入来测试我们的实现。请注意，与 Keras 相比，items 使用基于 1 的索引，0 作为填充。items 和 weights 均为相同形状的密集张量。

```python
inputs = {
    "items": torch.tensor([[2, 3, 0], [4, 1, 5]]),
    "weights": torch.tensor([[[1.3, 2.7, 0.0], [2.1, 4.6, 0.8]]]),
}
model = Autoencoder(num_items=1000, emb_size=128)
z = model(**inputs)
```

使用 `print(model)` 打印模型会给出

```
Autoencoder(
    (embed): Embedding(1000, 128, padding_idx=0)
    (decoder): Sequential(
        (0): ReLU()
        (1): Linear(in_features=128, out_features=1000, bias=True)
        (2): Sigmoid()
    )
)
```

## Bibliography

Martin Abadi, Ashish Agarwal, Paul Barham, Eugene Brevdo, Zhifeng Chen, Craig Citro, Greg S. Corrado, Andy Davis, Jeffrey Dean, Matthieu Devin, Sanjay Ghemawat, Ian Goodfellow, Andrew Harp, Geoffrey Irving, Michael Isard, Yangqing Jia, Rafal Jozefowicz, Lukasz Kaiser, Manjunath Kudlur, Josh Levenberg, Dan Mané, Rajat Monga, Sherry Moore, Derek Murray, Chris Olah, Mike Schuster, Jonathon Shlens, Benoit Steiner, Ilya Sutskever, Kunal Talwar, Paul Tucker, Vincent Vanhoucke, Vijay Vasudevan, Fernanda Viegas, Oriol Vinyals, Pete Warden, Martin Wattenberg, Martin Wicke, Yuan Yu, and Xiaoqiang Zheng. TensorFlow RaggedTensor. https://www.tensorflow.org/api_docs/python/tf/RaggedTensor, 2023.

Denis Baylor, Eric Breck, Heng-Tze Cheng, Noah Fiedel, Chuan Yu Foo, Zakaria Haque, Salem Haykal, Mustafa Ispir, Vihan Jain, Levent Koc, Chiu Yuen Koo, Lukasz Lew, Clemens Mewald, Akshay Naresh Modi, Neoklis Polyzotis, Sukriti Ramesh, Sudip Roy, Steven Euijong Whang, Martin Wicke, Jarek Wilkiewicz, Xin Zhang, and Martin Zinkevich. TensorFlow Transform Sparse Left Align. https://////

