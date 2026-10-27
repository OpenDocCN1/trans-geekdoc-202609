

## 12.2.2 实现

让我们更仔细地看一下代码：

```python
#
# Do not forget to add the otbtf/python directory to your PYTHONPATH.
# Else "tricks" can't be imported.
# In the OTBTF Docker image, tricks.py is located in the following
# path: /work/otb/otb/Modules/otbtf
#
# Works with OTBTF 1.7
#
from tricks import *
import sys

nclasses=2

# Convolution block with strides 2 ("downsampling")
def _conv(inp, n, k_size=3, strides=2, activ=tf.nn.relu):
    return tf.layers.conv2d(inputs=inp,
                            filters=n,
                            kernel_size=[k_size, k_size],
                            padding="same",
                            strides=(strides, strides),
                            activation=activ)

# Transposed convolution block with strides 2 ("upsampling")
def _dconv(inp, n, k_size=3, strides=2, activ=tf.nn.relu):
    return tf.layers.conv2d_transpose(inputs=inp,
                                      filters=n,
                                      strides=(strides,strides),
                                      kernel_size=[k_size, k_size],
                                      padding="same",
                                      activation=activ)

def myModel(x):

    depth = 16

    # Encoding
    conv1 = _conv(x, 1*depth) # 64 x 64 --> 32 x 32 (31 x 31)
    conv2 = _conv(conv1, 2*depth) # 32 x 32 --> 16 x 16 (15 x 15)
    conv3 = _conv(conv2, 4*depth) # 16 x 16 --> 8 x 8 ( 7 x 7)
    conv4 = _conv(conv3, 4*depth) # 8 x 8 --> 4 x 4 ( 3 x 3)

    # Decoding (with skip connections)
    deconv1 = _dconv(conv4, 4*depth) # 4 x 4 --> 8 x 8 ( 5 x 5)
    deconv2 = _dconv(deconv1 + conv3, 2*depth) # 8 x 8 --> 16 x 16
                                                  # ( 9 x 9)
    deconv3 = _dconv(deconv2 + conv2, 1*depth) # 16 x 16 --> 32 x 32
                                                  # (17 x 17)
    deconv4 = _dconv(deconv3 + conv1, 1*depth) # 32 x 32 --> 64 x 64
                                                  # (33 x 33)

    # Neurons for classes
    estimated = tf.layers.dense(inputs=deconv4, units=nclasses,
                                activation=None)

    return estimated

""" Main """
# check number of arguments
if len(sys.argv) != 2:
    print("Usage: output_directory_for_SavedModel")
    sys.exit(1)

# Create the graph
with tf.Graph().as_default():

    # Placeholders
    x = tf.placeholder(tf.float32, [None, None, None, 4], name="x")
    y = tf.placeholder(tf.int32, [None, None, None, 1], name="y")
    default_lr = tf.constant(0.0002, dtype=tf.float32, shape=[])
    lr = tf.placeholder_with_default(default_lr, shape=[], name="lr")

    # Output neurons of the model
    y_estimated = myModel(x)

    # Prediction output
    y_class = tf.argmax(y_estimated, axis=3)

    # Add the 4th dimension to have (#, :, :, 1) so the OTBTF apps
    # know that the output image has 1 component
    y_pred = tf.expand_dims(y_class, axis=-1, name="prediction")

    # Prediction output (FCN)
    y_pred_fcn = tf.identity(y_pred[:, 16:-16, 16:-16, :],
                             name="prediction_fcn")

    # Loss function
    cost = tf.losses.sparse_softmax_cross_entropy(labels=tf.reshape
                 (y, [-1, 1]), logits=tf.reshape(y_estimated, [-1, nclasses]))

    # Optimizer
    optimizer = tf.train.AdamOptimizer(learning_rate=lr,
                                       name="optimizer").minimize(cost)

    # Initializer, saver, session
    init = tf.global_variables_initializer()
    saver = tf.train.Saver(max_to_keep=20)
    sess = tf.Session()
    sess.run(init)

    # Create a SavedModel
    CreateSavedModel(sess=sess,
                     inputs=["x:0", "y:0"],
                     outputs=["prediction:0", "prediction_fcn:0"],
                     directory=sys.argv[1])
```

可以看到，我们使用卷积和转置卷积，它们保留了输出特征的尺寸（*padding="same"*），这意味着在卷积中使用了零填充。我们应该理解，如果要在全卷积模式下使用该模型，就不能直接使用最后一层计算出的特征：对于每个处理块，只有一部分是精确的（即相似的），这与输入区域无关。使用这些输出会产生由卷积中的零填充引起的块状伪影。

### 12.2.2.1 精确输出

为了解决这个问题，我们创建一个专门用于计算*prediction*输出张量*精确*部分的输出。为此，我们只需从输出的边缘移除几个像素，因为卷积会在每一层“污染”边缘，如[图12.10](#figure-12-10)所示。

![](img/f70619500c7a30b0babf83918d56ad93_106_0.png)

**图12.10**  
在每一层，特征图都会受到卷积零填充的污染。橙色边框的块：特征；橙色填充的块：特征图的有效部分。最终输出特征图的*精确*部分是其中心区域。

[表12.1](#table-12-1)显示了如何计算需要从最后一个特征图（即*prediction*输出张量）边缘移除的像素数。由于填充，每一层的卷积都会污染特征图。我们可以计算特征图的中心部分，该部分是*精确*的，即未被填充污染。由于所有卷积核的大小均为3，因此很容易计算最终需要裁剪的像素数。例如：第1层，卷积输出为32（输入为64，我们使用步长为2的卷积），但我们的卷积核为3×3，因此输出特征图的实际有效部分大小为31×31。

**表12.1**  
卷积输出（即特征图）的有效部分

| 层 | 特征大小 | 有效部分 |
|---|---:|---:|
| / | 64 | 64 |
| 1 | 32 | 31 |
| 2 | 16 | 15 |
| 3 | 8 | 7 |
| 4 | 4 | 3 |
| 1 | 8 | 5 |
| 2 | 16 | 9 |
| 3 | 32 | 17 |
| 4 | 64 | 33 |

如[表12.1](#table-12-1)所示，最终特征图的有效部分大小为33×33个元素。然后我们从边缘移除16个元素，以输出32×32个元素的有效张量。

### 12.2.2.2 表达场

在OTBTF中，模型为**output.names**中指定的张量所输出的空间部分被称为*表达场*。如前所述，模型将大小为64×64的基本输入图像转换为大小为32×32的基本输出预测标签图像。因此，后续我们将使用64×64的感受野（网络“看到”的输入体积）和32×32的表达场（网络“填充”的输出体积）。

## 12.2.3 生成SavedModel

要生成该模型，请使用`create_model4.py` Python脚本。

```bash
# Generate the model

# The "create_model4.py" file can be downloaded from:
# https://github.com/remipierre/otbtf_tutorials_resources.git
python3 ~/python/create_model4.py "model4"
```

> **重要提示**
> 
> 正如您所注意到的，我们为将在OTBTF应用程序中使用的输出张量仔细设置了4个维度。目前，OTBTF将输出张量的最后一个维度解释为输出图像的分量数。这就是我们使用`tf.expand_dims()`使*prediction*输出张量的最后一个维度为1的原因。

## 12.3 训练模型

使用**TensorflowModelTrain**应用程序训练模型：

```bash
# Since the TensorflowModelTrain uses n+1 sources
export OTB_TF_NSOURCES=1

# Train the deep learning model
otbcli_TensorflowModelTrain \
-training.source1.il amsterdam_Spot7_patches_A.tif \
-training.source1.patchsize 64 \
-training.source1.patchsizey 64 \
-training.source1.placeholder "x" \
-training.source2.il amsterdam_labelimage_patches_A.tif \
-training.source2.patchsize 64 \
-training.source2.patchsizey 64 \
-training.source2.placeholder "y" \
-model.dir model4 \
-training.targetnodes optimizer \
-validation.mode "class" \
-validation.source1.il amsterdam_Spot7_patches_B.tif \
-validation.source1.name "x" \
-validation.source2.il amsterdam_labelimage_patches_B.tif \
-validation.source2.name "prediction" \
-model.saveto model4/variables/variables
```

## 12.4 推理

如第12.2.1节所述，我们设置了大小为64×64的输入感受野和大小为32×32的输出表达场。我们要求**TensorflowModelServe**应用程序以全卷积模式生成模型的*prediction_fcn*输出张量。

让我们在子集图像上运行该模型：

```bash
# Produce the map
otbcli_TensorflowModelServe \
-source1.il IMG_SPOT7_amsterdam_PMS_norm.tif \
-source1.rfieldx 64 \
-source1.rfieldy 64 \
-source1.placeholder "x" \
-model.dir model4 \
-model.fullyconv on \
-output.efieldx 32 \
-output.efieldy 32 \
-output.names "prediction_fcn" \
-out "classif_model4.tif?&box=6000:4000:2000:2000" uint8
```

