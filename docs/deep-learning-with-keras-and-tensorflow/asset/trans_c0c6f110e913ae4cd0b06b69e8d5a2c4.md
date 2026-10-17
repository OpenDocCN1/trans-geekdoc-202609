

# 你的回合！

## 实操 - Keras 全连接网络

花几分钟时间，尝试调整层数和每层的参数数量，以获得最佳效果。

```
model = Sequential()
model.add(Dense(100, input_shape=(dims,)))

# ...
# ...
# 随意尝试！添加你想要的任意层数！尝试以获得更好的结果。

model.add(Dense(nb_classes))
model.add(Activation('softmax'))
model.compile(optimizer='sgd', loss='categorical_crossentropy')

model.summary()
```

```
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
dense_4 (Dense)              (None, 100)               9400      
_________________________________________________________________
dense_5 (Dense)              (None, 9)                 909       
_________________________________________________________________
activation_3 (Activation)    (None, 9)                 0         
=================================================================
Total params: 10,309
Trainable params: 10,309
Non-trainable params: 0
_________________________________________________________________
```

```
model.fit(X_train, Y_train, validation_data = (X_val, Y_val), epochs=20, 
          batch_size=128, verbose=True)
```

```
Train on 52596 samples, validate on 9282 samples
Epoch 1/20
52596/52596 [==============================] - 1s - loss: 1.2107 - val_loss: 0.8821
Epoch 2/20
52596/52596 [==============================] - 1s - loss: 0.8204 - val_loss: 0.7798
Epoch 3/20
52596/52596 [==============================] - 1s - loss: 0.7577 - val_loss: 0.7393
Epoch 4/20
52596/52596 [==============================] - 0s - loss: 0.7280 - val_loss: 0.7176
Epoch 5/20
52596/52596 [==============================] - 1s - loss: 0.7097 - val_loss: 0.7028
Epoch 6/20
52596/52596 [==============================] - 1s - loss: 0.6973 - val_loss: 0.6929
Epoch 7/20
52596/52596 [==============================] - 1s - loss: 0.6883 - val_loss: 0.6858
Epoch 8/20
52596/52596 [==============================] - 1s - loss: 0.6813 - val_loss: 0.6804
Epoch 9/20
52596/52596 [==============================] - 1s - loss: 0.6757 - val_loss: 0.6756
Epoch 10/20
52596/52596 [==============================] - 1s - loss: 0.6711 - val_loss: 0.6722
Epoch 11/20
52596/52596 [==============================] - 1s - loss: 0.6672 - val_loss: 0.6692
Epoch 12/20
52596/52596 [==============================] - 0s - loss: 0.6641 - val_loss: 0.6667
Epoch 13/20
52596/52596 [==============================] - 0s - loss: 0.6613 - val_loss: 0.6636
Epoch 14/20
52596/52596 [==============================] - 0s - loss: 0.6589 - val_loss: 0.6620
Epoch 15/20
52596/52596 [==============================] - 0s - loss: 0.6568 - val_loss: 0.6606
Epoch 16/20
52596/52596 [==============================] - 0s - loss: 0.6546 - val_loss: 0.6589
Epoch 17/20
52596/52596 [==============================] - 0s - loss: 0.6531 - val_loss: 0.6577
Epoch 18/20
52596/52596 [==============================] - 0s - loss: 0.6515 - val_loss: 0.6568
Epoch 19/20
52596/52596 [==============================] - 0s - loss: 0.6501 - val_loss: 0.6546
Epoch 20/20
52596/52596 [==============================] - 0s - loss: 0.6489 - val_loss: 0.6539



<keras.callbacks.History at 0x1285bae80>
```

构建问答系统、图像分类模型、神经图灵机、word2vec 词嵌入器或任何其他模型同样快速。深度学习背后的理念很简单，那么其实现为什么应该痛苦呢？

#### 深度的理论动机

> 关于神经网络深度的研究已有很多。数学上\[1\] 和经验上都已证明，卷积神经网络受益于深度！

\[1\] - 深度学习的表达能力：张量分析 - Cohen 等，2015 年

#### 深度的理论动机

一个广为引用的关于神经网络的定理指出：

> 通用近似定理指出\[1\]，带有单个隐藏层且包含有限数量神经元（即多层感知机）的前馈网络，可以在激活函数满足温和假设的条件下，近似 $\\mathbb{R}^n$ 紧子集上的连续函数。该定理因此指出，当给定适当参数时，简单的神经网络可以表示各种有趣的函数；然而，它并未涉及这些参数的算法可学性。

\[1\] - 多层前馈网络的近似能力 - Kurt Hornik 1991

## 附录

[2.3.1 Keras Backend](2.3.1%20%20Keras%20Backend.ipynb)

# 2.3.1 Keras Backend

# Keras Backend

在本笔记本中，我们将使用 [Keras 后端模块](http://keras.io/backend/)，它提供了对 Theano 和 Tensorflow 的抽象。

让我们尝试使用 `keras.backend` API 重新实现逻辑回归模型。

以下代码将与我们在 Theano 或 Tensorflow 中编写的代码非常相似（*唯一的区别*是它可以同时在两个后端上运行）。

```
import keras.backend as K
import numpy as np
import matplotlib.pyplot as plt

%matplotlib inline
```

```
Using TensorFlow backend.
```

```
from kaggle_data import load_data, preprocess_data, preprocess_labels
```

```
X_train, labels = load_data('../data/kaggle_ottogroup/train.csv', train=True)
X_train, scaler = preprocess_data(X_train)
Y_train, encoder = preprocess_labels(labels)

X_test, ids = load_data('../data/kaggle_ottogroup/test.csv', train=False)

X_test, _ = preprocess_data(X_test, scaler)

nb_classes = Y_train.shape[1]
print(nb_classes, 'classes')

dims = X_train.shape[1]
print(dims, 'dims')
```

```
9 classes
93 dims
```

```
feats = dims
training_steps = 25
```

