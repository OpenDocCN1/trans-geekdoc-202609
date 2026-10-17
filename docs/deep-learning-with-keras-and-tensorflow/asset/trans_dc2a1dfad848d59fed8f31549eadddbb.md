

# 卷积自编码器训练与应用

## 数据预处理

```python
from keras import backend as K

if K.image_data_format() == 'channels_last':
    shape_ord = (28, 28, 1)
else:
    shape_ord = (1, 28, 28)

(x_train, _), (x_test, _) = mnist.load_data()

x_train = x_train.astype('float32') / 255.
x_test = x_test.astype('float32') / 255.

x_train = np.reshape(x_train, ((x_train.shape[0],) + shape_ord))  
x_test = np.reshape(x_test, ((x_test.shape[0],) + shape_ord))
```

查看训练数据形状：

```python
x_train.shape
```

输出结果：

```
(60000, 28, 28, 1)
```

## 模型训练

导入 `TensorBoard` 回调并设置训练参数：

```python
from keras.callbacks import TensorBoard

batch_size = 128
steps_per_epoch = np.int(np.floor(x_train.shape[0] / batch_size))
conv_autoencoder.fit(x_train, x_train, epochs=50, batch_size=128,
                     shuffle=True, validation_data=(x_test, x_test),
                     callbacks=[TensorBoard(log_dir='./tf_autoencoder_logs')])
```

训练过程输出如下：

```
Train on 60000 samples, validate on 10000 samples
Epoch 1/50
60000/60000 [==============================] - 8s - loss: 0.2327 - val_loss: 0.1740
Epoch 2/50
60000/60000 [==============================] - 7s - loss: 0.1645 - val_loss: 0.1551
Epoch 3/50
60000/60000 [==============================] - 7s - loss: 0.1501 - val_loss: 0.1442
Epoch 4/50
60000/60000 [==============================] - 7s - loss: 0.1404 - val_loss: 0.1375
Epoch 5/50
60000/60000 [==============================] - 7s - loss: 0.1342 - val_loss: 0.1316
Epoch 6/50
60000/60000 [==============================] - 7s - loss: 0.1300 - val_loss: 0.1298
Epoch 7/50
60000/60000 [==============================] - 7s - loss: 0.1272 - val_loss: 0.1301
Epoch 8/50
60000/60000 [==============================] - 7s - loss: 0.1243 - val_loss: 0.1221
Epoch 9/50
60000/60000 [==============================] - 7s - loss: 0.1222 - val_loss: 0.1196
Epoch 10/50
60000/60000 [==============================] - 7s - loss: 0.1207 - val_loss: 0.1184
Epoch 11/50
60000/60000 [==============================] - 7s - loss: 0.1188 - val_loss: 0.1162
Epoch 12/50
60000/60000 [==============================] - 7s - loss: 0.1175 - val_loss: 0.1160
Epoch 13/50
60000/60000 [==============================] - 7s - loss: 0.1167 - val_loss: 0.1164
Epoch 14/50
60000/60000 [==============================] - 7s - loss: 0.1154 - val_loss: 0.1160
Epoch 15/50
60000/60000 [==============================] - 7s - loss: 0.1145 - val_loss: 0.1159
Epoch 16/50
60000/60000 [==============================] - 7s - loss: 0.1132 - val_loss: 0.1110
Epoch 17/50
60000/60000 [==============================] - 7s - loss: 0.1127 - val_loss: 0.1108
Epoch 18/50
60000/60000 [==============================] - 7s - loss: 0.1118 - val_loss: 0.1099
Epoch 19/50
60000/60000 [==============================] - 7s - loss: 0.1113 - val_loss: 0.1106
Epoch 20/50
60000/60000 [==============================] - 7s - loss: 0.1108 - val_loss: 0.1120
Epoch 21/50
60000/60000 [==============================] - 7s - loss: 0.1104 - val_loss: 0.1064
Epoch 22/50
60000/60000 [==============================] - 7s - loss: 0.1094 - val_loss: 0.1075
Epoch 23/50
60000/60000 [==============================] - 7s - loss: 0.1088 - val_loss: 0.1088
Epoch 24/50
60000/60000 [==============================] - 7s - loss: 0.1085 - val_loss: 0.1071
Epoch 25/50
60000/60000 [==============================] - 7s - loss: 0.1081 - val_loss: 0.1060
Epoch 26/50
60000/60000 [==============================] - 7s - loss: 0.1075 - val_loss: 0.1062
Epoch 27/50
60000/60000 [==============================] - 7s - loss: 0.1074 - val_loss: 0.1062
Epoch 28/50
60000/60000 [==============================] - 7s - loss: 0.1065 - val_loss: 0.1045
Epoch 29/50
60000/60000 [==============================] - 7s - loss: 0.1062 - val_loss: 0.1043
Epoch 30/50
60000/60000 [==============================] - 7s - loss: 0.1057 - val_loss: 0.1038
Epoch 31/50
60000/60000 [==============================] - 7s - loss: 0.1053 - val_loss: 0.1040
Epoch 32/50
60000/60000 [==============================] - 7s - loss: 0.1048 - val_loss: 0.1041
Epoch 33/50
60000/60000 [==============================] - 7s - loss: 0.1045 - val_loss: 0.1057
Epoch 34/50
60000/60000 [==============================] - 7s - loss: 0.1041 - val_loss: 0.1026
Epoch 35/50
60000/60000 [==============================] - 7s - loss: 0.1041 - val_loss: 0.1042
Epoch 36/50
60000/60000 [==============================] - 7s - loss: 0.1035 - val_loss: 0.1053
Epoch 37/50
60000/60000 [==============================] - 7s - loss: 0.1032 - val_loss: 0.1006
Epoch 38/50
60000/60000 [==============================] - 7s - loss: 0.1030 - val_loss: 0.1011
Epoch 39/50
60000/60000 [==============================] - 7s - loss: 0.1028 - val_loss: 0.1013
Epoch 40/50
60000/60000 [==============================] - 7s - loss: 0.1027 - val_loss: 0.1018
Epoch 41/50
60000/60000 [==============================] - 7s - loss: 0.1025 - val_loss: 0.1019
Epoch 42/50
60000/60000 [==============================] - 7s - loss: 0.1024 - val_loss: 0.1025
Epoch 43/50
60000/60000 [==============================] - 7s - loss: 0.1020 - val_loss: 0.1015
Epoch 44/50
60000/60000 [==============================] - 7s - loss: 0.1020 - val_loss: 0.1018
Epoch 45/50
60000/60000 [==============================] - 7s - loss: 0.1015 - val_loss: 0.1011
Epoch 46/50
60000/60000 [==============================] - 7s - loss: 0.1013 - val_loss: 0.0999
Epoch 47/50
60000/60000 [==============================] - 7s - loss: 0.1010 - val_loss: 0.0995
Epoch 48/50
60000/60000 [==============================] - 7s - loss: 0.1008 - val_loss: 0.0996
Epoch 49/50
60000/60000 [==============================] - 7s - loss: 0.1008 - val_loss: 0.0990
Epoch 50/50
60000/60000 [==============================] - 7s - loss: 0.1006 - val_loss: 0.0995
```

训练完成后返回对象：

```
<keras.callbacks.History at 0x7fd1bebacfd0>
```

## 重构结果可视化

使用 `conv_autoencoder.predict` 对测试集进行重构，并可视化前 10 个样本：

```python
decoded_imgs = conv_autoencoder.predict(x_test)

n = 10
plt.figure(figsize=(20, 4))
for i in range(n):
    # display original
    ax = plt.subplot(2, n, i+1)
    plt.imshow(x_test[i].reshape(28, 28))
    plt.gray()
    ax.get_xaxis().set_visible(False)
    ax.get_yaxis().set_visible(False)

    # display reconstruction
    ax = plt.subplot(2, n, i + n + 1)
    plt.imshow(decoded_imgs[i].reshape(28, 28))
    plt.gray()
    ax.get_xaxis().set_visible(False)
    ax.get_yaxis().set_visible(False)
plt.show()
```

![png](6.1.%20AutoEncoders%20and%20Embeddings_29_0.png)

## 编码器中间表示可视化

我们也可以查看 `128-`维的编码中间表示：

```python
conv_encoder = Model(input_img, encoded)
encoded_imgs = conv_encoder.predict(x_test)

n = 10
plt.figure(figsize=(20, 8))
for i in range(n):
    ax = plt.subplot(1, n, i+1)
    plt.imshow(encoded_imgs[i].reshape(4, 4 * 8).T)
    plt.gray()
    ax.get_xaxis().set_visible(False)
    ax.get_yaxis().set_visible(False)
plt.show()
```

![png](6.1.%20AutoEncoders%20and%20Embeddings_31_0.png)

## 预训练编码器

自编码器的一个强大功能是利用编码器从特征向量生成有意义的表示。

使用编码器来预训练分类器：

```python
# Use the encoder to pretrain a classifier
```

* * *

## 应用于图像去噪

将卷积自编码器应用于图像去噪问题。很简单：我们将训练自编码器将噪声数字图像映射到干净数字图像。

生成合成噪声数字的方法如下：只需应用高斯噪声矩阵并将图像裁剪到 0 和 1 之间。

