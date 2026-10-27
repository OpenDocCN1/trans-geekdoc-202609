
```python
nclasses=6

def myModel(x):

    # input patches: 16x16x4
    conv1 = tf.layers.conv2d(inputs=x, filters=16, kernel_size=[5,5],
                             padding="valid", activation=tf.nn.relu)
    # conv1 out size: 12x12x16
    pool1 = tf.layers.max_pooling2d(inputs=conv1, pool_size=[2, 2],
                                    strides=2)
    # pool1 out: 6x6x16
    conv2 = tf.layers.conv2d(inputs=pool1, filters=16, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv2 out size: 4x4x16
    pool2 = tf.layers.max_pooling2d(inputs=conv2, pool_size=[2, 2],
                                    strides=2)
    # pool2 out: 2x2x16
    conv3 = tf.layers.conv2d(inputs=pool2, filters=32, kernel_size=[2,2],
                             padding="valid",activation=tf.nn.relu)
    # conv3 out: 1x1x32

    # Features
    features = tf.reshape(conv3, shape=[-1, 32], name="features")

    # Neurons for classes
    estimated = tf.layers.dense(inputs=features, units=nclasses,
        activation=None)
    estimated_label = tf.argmax(estimated, 1, name="prediction")

    return estimated, estimated_label

""" Main """
if len(sys.argv) != 2:
    print("Usage: output_directory_for_SavedModel")
    sys.exit(1)

# Create the TensorFlow graph
with tf.Graph().as_default():

    # Placeholders
    x = tf.placeholder(tf.float32, [None, None, None, 4], name="x")
    y = tf.placeholder(tf.int32, [None, None, None, 1], name="y")
    default_lr = tf.constant(0.0002, dtype=tf.float32, shape=[])
    lr = tf.placeholder_with_default(default_lr, shape=[], name="lr")

    # Output
    y_estimated, y_label = myModel(x)

    # Loss function
    cost = tf.losses.sparse_softmax_cross_entropy(labels=tf.reshape
        (y, [-1, 1]), logits=tf.reshape(y_estimated,
        [-1, nclasses]))
```

```python
# Optimizer
optimizer = tf.train.AdamOptimizer(learning_rate=lr,
    name="optimizer").minimize(cost)
```

```python
# Initializer, saver, session
init = tf.global_variables_initializer()
saver = tf.train.Saver( max_to_keep=20 )
sess = tf.Session()
sess.run(init)
```

```python
# Create a SavedModel
CreateSavedModel(sess=sess,
    inputs=["x:0", "y:0"],
    outputs=["features:0", "prediction:0"],
    directory=sys.argv[1])
```

**重要提示**
Python 语法对缩进非常敏感：在块（如函数）内的每一行，必须保留相同的缩进。如果你复制/粘贴或修改所提供的代码，请注意缩进。我们建议克隆 GitHub 仓库，而不是使用复制/粘贴。

要运行该 Python 脚本，只需输入：

```bash
# Add otbtf python directory to PYTHONPATH
export PYTHONPATH=$PYTHONPATH:/work/otb/otb/Modules/Remote/otbtf/python/
```

```bash
# Generate the model (you might need to provide the correct path
# to the "create_model1.py" file if you have downloaded elsewhere)
# The "create_model1.py" file can be downloaded from:
# https://github.com/remicres/otbtf_tutorials_resources.git
python3 create_model1.py "model1"
```

当然，如果你希望将模型目录（"model1"）写入当前目录以外的位置，你可以更改它。

## 5.5 从头训练模型

如果你查看 SavedModel 目录，你会看到一个 .pb 文件（protobuf）和一个 Variables 文件夹。protobuf 文件序列化计算图，而 Variables 文件夹包含模型权重的值（核等）。正如你在 Python 脚本中可能注意到的，模型权重在导出 SavedModel 之前就已经初始化。我们将使用 TensorflowModelTrain 应用从初始化状态训练 CNN，更新其权重以完成图像分类任务。对于每个数据集（训练数据和验证数据），**Tensorflow-ModelTrain** 应用的验证步骤包括计算以下指标：

- 混淆矩阵
- 总体准确率指数
- Kappa 指数
- 对于每个类别：
  - 精确率
  - 召回率
  - F 分数

根据训练所用源的占位符名称和评估所用源的名称，如何检测哪个源用作模型输入，或用作计算评估指标的基线，在图 5.3 中予以说明。

![](img/f70619500c7a30b0babf83918d56ad93_50_0.png)

## 图 5.3

分别对训练数据集和验证数据集执行分类指标的计算。

应用参数如下：

- **training.source1** 是第一个源的参数组，即图像补丁（用于学习）
  - **training.source1.il** 是输入图像文件名
  - **training.source1.patchsizex** 是补丁宽度
  - **training.source1.patchsizey** 是补丁高度
  - **training.source1.placeholder** 是图像补丁的占位符名称
- **training.source2** 是第二个源的参数组，即标签补丁（用于学习）
- **training.source2.il** 是输入图像文件名
- **training.source2.patchsizex** 是标签宽度
- **training.source2.patchsizey** 是标签高度
- **training.source2.placeholder** 是标签补丁的占位符名称
- **model.dir** 是包含 TensorFlow *SavedModel* 的目录
- **training.targetnodes** 是在训练步骤中计算梯度下降的算子名称。在我们的模型中，梯度下降通过名为 **“optimizer.”** 的 adam 优化器执行。
- **validation.mode** 是验证模式。**“class”** 验证模式能够对训练数据和验证数据都计算分类指标。
- **validation.source1** 是补丁源（用于验证）。由于验证源的名称（**validation.source1.name**）与训练时同一源的占位符名称（**training.source1.placeholder**）相同，因此该源被视为模型的输入，并在验证步骤中送入相应的占位符。
- **validation.source2** 是标签源（用于验证）。由于该源的名称（**validation.source2.name**）不同于训练时同一源的占位符名称（**training.source2.placeholder**），因此该源被视为参考，在验证步骤中与具有相同张量名称的模型输出进行比较。
- **model.saveto** 使我们能够将模型变量（即权重）导出到文件。

与上述描述对应的命令行如下：

```bash
# Train the deep learning model
otbcli_TensorflowModelTrain \
-training.source1.il Sentinel-2_B4328_10m_patches_A.tif \
-training.source1.patchsizex 16 \
-training.source1.patchsizey 16 \
-training.source1.placeholder "x" \
-training.source2.il Sentinel-2_B4328_10m_labels_A.tif \
-training.source2.patchsizex 1 \
-training.source2.patchsizey 1 \
-training.source2.placeholder "y" \
-model.dir model1 \
-training.targetnodes "optimizer" \
-validation.mode "class" \
-validation.source1.il Sentinel-2_B4328_10m_patches_B.tif \
-validation.source1.name "x" \
-validation.source2.il Sentinel-2_B4328_10m_labels_B.tif \
-validation.source2.name "prediction" \
-model.saveto model1/variables/variables
```

如你所见，training.source1.placeholder 和 validation.source1.name 是相同的（“x”），而 training.source2.placeholder 和 validation.source2.name 是不同的（“y”与“prediction”）。这使得占位符 x 既用于训练也用于验证，但占位符 y 仅用于训练，而占位符 prediction 用于验证，如图 5.3 所述。

我们可以通过 training.userplaceholders 参数调整学习率（如 Python 代码中所提到的，其默认值为 0.0002）：

```
...
-training.userplaceholders "lr=0.005" \
...
```

运行 TensorflowModelTrain 应用。训练轮次结束后，记下 kappa 和总体准确率指数（在验证数据集上应分别约为 0.7）。浏览文件系统，查看 data/results/model1/variables/ 目录：你可以注意到该应用已经更新了两个文件：

- *model_variables_cnn.index* 是已保存变量的摘要，
- *model_variables_cnn.data-00000-of-00001* 是已保存的变量 1，在训练过程结束时保存。

## 5.6 与随机森林的比较

在这里，我们将我们的小型深度网络与随机森林（RF）分类器进行比较。我们使用从混淆矩阵导出的指标。我们使用 OTB 的机器学习框架来训练和评估 RF 分类器的性能。首先，我们使用与深度网络训练和验证完全相同的样本，以提取图像的像素值：

```bash
# Extract the pixels values at samples locations (Learning data)
otbcli_SampleExtraction \
-in Sentinel-2_B4328_10m.tif \
-vec terrain_truth_epsg32654_A_pos.shp \
-field "class" \
-out terrain_truth_epsg32654_A_pixelvalues.shp
```

然后，我们对 terrain_truth_epsg32654_B_pos.shp 矢量数据（验证数据）进行同样操作。

```bash
# Extract the pixels values at samples locations (Validation data)
otbcli_SampleExtraction \
-in Sentinel-2_B4328_10m.tif \
-vec terrain_truth_epsg32654_B_pos.shp \
-field "class" \
-out terrain_truth_epsg32654_B_pixelvalues.shp
```
