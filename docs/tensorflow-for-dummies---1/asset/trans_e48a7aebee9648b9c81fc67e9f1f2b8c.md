

![images](images/eq06020.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>&#963;</m:mi><m:msub><m:mrow><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mn>0</m:mn></m:msub><m:mo>=</m:mo><m:mfrac><m:mrow><m:msup><m:mi>e</m:mi><m:mrow><m:msub><m:mi>x</m:mi><m:mn>0</m:mn></m:msub></m:mrow></m:msup></m:mrow><m:mrow><m:mstyle displaystyle="true"><m:munderover><m:mo>&#8721;</m:mo><m:mrow><m:mi>i</m:mi><m:mo>=</m:mo><m:mn>0</m:mn></m:mrow><m:mn>4</m:mn></m:munderover><m:mrow><m:msup><m:mi>e</m:mi><m:mrow><m:msub><m:mi>x</m:mi><m:mi>i</m:mi></m:msub></m:mrow></m:msup></m:mrow></m:mstyle></m:mrow></m:mfrac><m:mo>=</m:mo><m:mfrac><m:mrow><m:msup><m:mi>e</m:mi><m:mrow><m:mn>3.2</m:mn></m:mrow></m:msup></m:mrow><m:mrow><m:mrow><m:mo>(</m:mo><m:mrow><m:msup><m:mi>e</m:mi><m:mrow><m:mn>3.2</m:mn></m:mrow></m:msup><m:mo>+</m:mo><m:msup><m:mi>e</m:mi><m:mrow><m:mo>&#45;</m:mo><m:mn>2.6</m:mn></m:mrow></m:msup><m:mo>+</m:mo><m:msup><m:mi>e</m:mi><m:mrow><m:mn>1.7</m:mn></m:mrow></m:msup><m:mo>+</m:mo><m:msup><m:mi>e</m:mn></m:msup><m:mo>+</m:mo><m:msup><m:mi>e</m:mi><m:mrow><m:mn>4.9</m:mn></m:mrow></m:msup></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow></m:mfrac><m:mo>=</m:mo><m:mn>0.14835</m:mn></m:mrow></m:math>

每个 `N` 值都标识了数据点属于对应类别的概率。点属于类别 0 的概率为 0.14835。

### 使用交叉熵计算损失

如果 `h(x)` 是一个模型且 `y[i]` 标识一个类别，你可以按以下方式计算给定 `x` 值时 `y[i]` 的似然：

![images](images/eq06021.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>L</m:mi><m:mrow><m:mo>(</m:mo><m:mrow><m:msub><m:mi>y</m:mi><m:mi>i</m:mi></m:msub></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>=</m:mo><m:mi>h</m:mi><m:msup><m:mrow><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mrow><m:msub><m:mi>y</m:mi><m:mi>i</m:msub></m:mrow></m:msup><m:msup><m:mrow><m:mrow><m:mo>\[</m:mo><m:mrow><m:mn>1</m:mn><m:mo>&#45;</m:mo><m:mi>h</m:mi><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mo>\]</m:mo></m:mrow></m:mrow><m:mrow><m:mrow><m:mo>(</m:mo><m:mrow><m:mn>1</m:mn><m:mo>&#45;</m:mo><m:msub><m:mi>y</m:mi><m:mi>i</m:msub></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow></m:msup></m:mrow></m:math>

似然的概念可以扩展到具有两个以上结果的系统。如果分类器需要在 `N` 个类别之间进行选择，`y[i]` 可以取 0 到 `N-1` 之间的任意值。如果模型表示为 `h(x)`，你可以用以下方程表示似然：

![images](images/eq06022.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>L</m:mi><m:mrow><m:mo>(</m:mo><m:mrow><m:msub><m:mi>y</m:mi><m:mn>0</m:mn></m:msub><m:mo>,</m:mo><m:msub><m:mi>y</m:mi><m:mn>1</m:mn></m:msub><m:mo>,</m:mo><m:mo>&#8230;</m:mo><m:msub><m:mi>y</m:mi><m:mrow><m:mi>N</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:msub></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>=</m:mo><m:mi>h</m:mi><m:msup><m:mrow><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mrow><m:msub><m:mi>y</m:mi><m:mn>0</m:mn></m:msub></m:mrow></m:msup><m:mi>h</m:mi><m:msup><m:mrow><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mrow><m:msub><m:mi>y</m:mi><m:mn>1</m:mn></m:msub></m:mrow></m:msup><m:mo>&#8943;</m:mo><m:mi>h</m:mi><m:msup><m:mrow><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mrow><m:msub><m:mi>y</m:mi><m:mrow><m:mi>N</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:msub></m:mrow></m:msup><m:mo>=</m:mo><m:mstyle displaystyle="true"><m:munderover><m:mo>&#8719;</m:mo><m:mrow><m:mi>i</m:mi><m:mo>=</m:mo><m:mn>0</m:mn></m:mrow><m:mrow><m:mi>N</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:munderover><m:mrow><m:mi>h</m:mi><m:msup><m:mrow><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mrow><m:msub><m:mi>y</m:mi><m:mi>i</m:mi></m:msub></m:mrow></m:msup></m:mrow></m:mstyle></m:mrow></m:math>

同样，如果 `h(x)` 总是正确，则似然等于 1；如果 `h(x)` 总是错误，则似然等于 0。为了将似然转换为合适的损失函数，统计学家取负对数并得到以下表达式：

![images](images/eq06023.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>l</m:mi><m:mi>o</m:mi><m:mi>s</m:mi><m:mi>s</m:mi><m:mo>=</m:mo><m:mo>&#45;</m:mstyle displaystyle="true"><m:munderover><m:mo>&#8721;</m:mo><m:mrow><m:mi>i</m:mi><m:mo>=</m:mo><m:mn>0</m:mn></m:mrow><m:mrow><m:mi>N</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:munderover><m:mrow><m:msub><m:mi>y</m:mi><m:mi>i</m:msub><m:mi>log</m:mi><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>h</m:mi><m:mrow><m:mo>(</m:mo><m:mi>x</m:mi><m:mo>)</m:mo></m:mrow></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow></m:mstyle></m:mrow></m:math>

在机器学习文献中，该结果被称为 *交叉熵*。该术语来自信息论，它指的是使用对数来确定表示消息应使用多少比特。以下代码通过调用 `tf.nn.softmax` 定义模型，然后使用交叉熵计算损失。

```
model = tf.nn.softmax(tf.matmul(x, m) + b)
loss = tf.reduce_mean(-tf.reduce_sum(y * tf.log(model))
```

为了提高性能，TensorFlow 提供了将 softmax 函数和交叉熵结合起来的函数。该函数是 `tf.nn.softmax_cross_entropy_with_logits`，其签名如下：

```
softmax_cross_entropy_with_logits(labels=None, logits=None, dim=-1, name=None)
```

你必须按名称标识传递给此函数的每个参数。`logits` 设置为将传递给 softmax 的张量，`labels` 设置为包含相关标签的张量。`logits` 和 `labels` 必须具有相同的大小。

TensorFlow 还提供了将 sigmoid 函数和交叉熵结合起来的函数：`sigmoid_cross_entropy_with_logits`。其签名如下：

```
sigmoid_cross_entropy_with_logits(_sentinel=None, labels=None, logits=None, name=None)
```

`labels` 和 `logits` 接受的值与 `softmax_cross_entropy_with_logits` 的对应参数相同。

### 将理论付诸实践

`ch6/multi_regression.py` 中的代码演示了如何使用多项式回归加载并对 MNIST 数据集中的图像进行分类。 [Listing 6-4](#11_9788126592555-ch06.xhtml#c06-fea-0004) 展示了代码。

[LISTING 6-4](#11_9788126592555-ch06.xhtml#rc06-fea-0004) 多项式逻辑回归

```
# Read MNIST data
dataset = learn.datasets.mnist.read_data_sets('MNIST-data', one_hot=True)

# Placeholders for MNIST images
image_holder = tf.placeholder(tf.float32, [None, 784])
label_holder = tf.placeholder(tf.float32, [None, 10])

# Variables
m = tf.Variable(tf.zeros([784, 10]))
b = tf.Variable(tf.zeros([10]))

# Compute loss
loss = tf.reduce_mean(
    tf.nn.softmax_cross_entropy_with_logits(
        logits=tf.matmul(image_holder, m) + b, labels=label_holder))

# Create optimizer
learning_rate = 0.01
num_epochs = 25
batch_size = 100
num_batches = int(dataset.train.num_examples/batch_size)
optimizer = tf.train.GradientDescentOptimizer(learning_rate).minimize(loss)

# Initialize variables
init = tf.global_variables_initializer()

# Launch session
with tf.Session() as sess:
    sess.run(init)

    # Loop over epochs
    for epoch in range(num_epochs):

        # Loop over batches
        for batch in range(num_batches):
            image_batch, label_batch = dataset.train.next_batch(batch_size)
            _, lossVal = sess.run([optimizer, loss],
                feed_dict={image_holder: image_batch, label_holder: label_batch})

        # Display the final loss
        print('Final loss: ', lossVal)
```

