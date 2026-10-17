

```
accuracy epoch 0:0.6649535894393921
accuracy epoch 1:0.665276825428009
accuracy epoch 2:0.6657131910324097
accuracy epoch 3:0.6659556031227112
accuracy epoch 4:0.6662949919700623
accuracy epoch 5:0.6666181683540344
accuracy epoch 6:0.6668121218681335
accuracy epoch 7:0.6671029925346375
accuracy epoch 8:0.6674585342407227
accuracy epoch 9:0.6678463816642761
accuracy epoch 10:0.6680726408958435
accuracy epoch 11:0.6682504415512085
accuracy epoch 12:0.6684605479240417
accuracy epoch 13:0.6687514185905457
accuracy epoch 14:0.6690422892570496
accuracy epoch 15:0.6692523956298828
accuracy epoch 16:0.6695109605789185
accuracy epoch 17:0.6697695255279541
accuracy epoch 18:0.6699796319007874
accuracy epoch 19:0.6702220439910889
accuracy epoch 20:0.6705452799797058
accuracy epoch 21:0.6708361506462097
accuracy epoch 22:0.6710785627365112
accuracy epoch 23:0.671385645866394
accuracy epoch 24:0.6716926693916321
Training phase finished
```

![png](2.3%20Introduction%20to%20Keras_28_1.png)

```
[1 5 5 ..., 2 1 1]
```

```
%%bash
python -m tensorflow.tensorboard --logdir=/tmp/logistic_logs
```

```
Process is terminated.
```

* * *

# 使用 Keras

```
from keras.models import Sequential
from keras.layers import Dense, Activation
```

```
dims = X_train.shape[1]
print(dims, 'dims')
print("Building model...")

nb_classes = Y_train.shape[1]
print(nb_classes, 'classes')

model = Sequential()
model.add(Dense(nb_classes, input_shape=(dims,), activation='sigmoid'))
model.add(Activation('softmax'))

model.compile(optimizer='sgd', loss='categorical_crossentropy')
model.fit(X_train, Y_train)
```

```
93 dims
Building model...
9 classes
Epoch 1/10
61878/61878 [==============================] - 3s - loss: 1.9845     
Epoch 2/10
61878/61878 [==============================] - 2s - loss: 1.8337     
Epoch 3/10
61878/61878 [==============================] - 2s - loss: 1.7779     
Epoch 4/10
61878/61878 [==============================] - 3s - loss: 1.7432     
Epoch 5/10
61878/61878 [==============================] - 2s - loss: 1.7187     
Epoch 6/10
61878/61878 [==============================] - 3s - loss: 1.7002     
Epoch 7/10
61878/61878 [==============================] - 2s - loss: 1.6857     
Epoch 8/10
61878/61878 [==============================] - 2s - loss: 1.6739     
Epoch 9/10
61878/61878 [==============================] - 2s - loss: 1.6642     
Epoch 10/10
61878/61878 [==============================] - 2s - loss: 1.6560     





<keras.callbacks.History at 0x123026dd8>
```

简单性非常令人印象深刻，对吧？ :)

**Theano**:

`shape = (channels, rows, cols)`

**Tensorflow**:

`shape = (rows, cols, channels)`

`image_data_format` : `channels_last | channels_first`

```
!cat ~/.keras/keras.json
```

```
{

    "epsilon": 1e-07,

    "backend": "tensorflow",

    "floatx": "float32",

    "image_data_format": "channels_last"

}
```

现在让我们来理解：

```
The core data structure of Keras is a model, a way to organize layers. The main type of model is the Sequential model, a linear stack of layers.
```

我们在这里所做的是堆叠一个从输入到输出的完全连接（`Dense`）可训练权重层，以及在权重层之上的一个 `Activation` 层。

##### Dense

```
from keras.layers.core import Dense

Dense(units, activation=None, use_bias=True, 
      kernel_initializer='glorot_uniform', bias_initializer='zeros', 
      kernel_regularizer=None, bias_regularizer=None, 
      activity_regularizer=None, kernel_constraint=None, bias_constraint=None)
```

*   `units`: int > 0.

*   `init`: 用于层权重的初始化函数名称（请参阅初始化），或者用于权重初始化的 Theano 函数。仅当您不传递 weights 参数时，此参数才相关。

*   `activation`: 要使用的激活函数名称（请参阅激活函数），或者元素级 Theano 函数。如果您不指定任何内容，则不应用激活（即“线性”激活：a(x) = x）。

*   `weights`: 用于设置初始权重的 NumPy 数组列表。列表应包含 2 个元素，分别为权重和偏置的 (input_dim, output_dim) 和 (output_dim,) 形状。

*   `kernel_regularizer`: WeightRegularizer 的实例（例如 L1 或 L2 正则化），应用于主权重矩阵。

*   `bias_regularizer`: WeightRegularizer 的实例，应用于偏置。

*   `activity_regularizer`: ActivityRegularizer 的实例，应用于网络输出。

*   `kernel_constraint`: 约束模块的实例（例如 maxnorm、nonneg），应用于主权重矩阵。

*   `bias_constraint`: 约束模块的实例，应用于偏置。

*   `use_bias`: 是否包含偏置（即使层为仿射而非线性）。

## (some) others `keras.core.layers`

*   `keras.layers.core.Flatten()`

*   `keras.layers.core.Reshape(target_shape)`

*   `keras.layers.core.Permute(dims)`

```
model = Sequential()
model.add(Permute((2, 1), input_shape=(10, 64)))
# now: model.output_shape == (None, 64, 10)
# note: `None` is the batch dimension
```

*   `keras.layers.core.Lambda(function, output_shape=None, arguments=None)`

*   `keras.layers.core.ActivityRegularization(l1=0.0, l2=0.0)`

![](dl_overview.png)

Credits: Yam Peleg ([@Yampeleg](https://twitter.com/yampeleg))

##### Activation

```
from keras.layers.core import Activation

Activation(activation)
```

**支持的激活函数** : \[[https://keras.io/activations/](https://keras.io/activations/)\]

**高级激活函数**: \[[https://keras.io/layers/advanced-activations/](https://keras.io/layers/advanced-activations/)\]

##### Optimizer

如果需要，您可以进一步配置优化器。Keras 的核心原则是使事物合理简单，同时在需要时允许用户完全控制（终极控制是源代码的易于扩展性）。这里我们使用 `SGD`（随机梯度下降）作为可训练权重的优化算法。

![](90db9ff6.gif)

来源与参考：[http://sebastianruder.com/content/images/2016/09/saddle\_point\_evaluation\_optimizers.gif](http://sebastianruder.com/content/images/2016/09/saddle_point_evaluation_optimizers.gif)

# 稍微深入“数据科学”此示例

我们在这里所做的很好，但在现实世界中由于过拟合而无法使用。让我们尝试用交叉验证来解决它。

##### 过拟合

在过拟合中，统计模型描述的是随机误差或噪声，而不是底层关系。当模型过于复杂（例如相对于观测数量拥有过多参数）时，就会发生过拟合。

过拟合模型的预测性能较差，因为它会对训练数据中的微小波动做出过度反应。

![](overfitting.png)

```
To avoid overfitting, we will first split out data to training set and test set and test out model on the test set.
Next: we will use two of keras's callbacks EarlyStopping and ModelCheckpoint
```

* * *

让我们先看看我们实现的模型

```
model.summary()
```

```
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
dense_1 (Dense)              (None, 9)                 846       
_________________________________________________________________
activation_1 (Activation)    (None, 9)                 0         
=================================================================
Total params: 846
Trainable params: 846
Non-trainable params: 0
_________________________________________________________________
```

```
from sklearn.model_selection import train_test_split
from keras.callbacks import EarlyStopping, ModelCheckpoint
```

