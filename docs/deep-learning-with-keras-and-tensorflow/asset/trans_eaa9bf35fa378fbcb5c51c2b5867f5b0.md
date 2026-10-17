

# 6.1. 自动编码器与嵌入

## 无监督学习

### 自动编码器

自动编码器是一种用于学习高效编码的人工神经网络。

自动编码器的目标是为一组数据学习表示（编码），通常用于降维。

![](autoencoder.png)

无监督学习是一种机器学习算法，用于从仅包含输入数据且没有标记响应的数据集中得出推论。最常见的无监督学习方法是聚类分析，用于探索性数据分析，以在数据中发现隐藏的模式或分组。

### 参考

基于 [https://blog.keras.io/building-autoencoders-in-keras.html](https://blog.keras.io/building-autoencoders-in-keras.html)

## 介绍 `Keras Functional API`

Keras 函数式 API 是定义复杂模型（如多输出模型、有向无环图或具有共享层的模型）的首选方法。

所有函数式 API 都依赖于这样一个事实：每个 `keras.Layer` 对象都是一个 `callable` 对象！

有关详细信息，请参阅 [8.2 多模态网络](../8.%20Extra/8.2%20Multi-Modal%20Networks.ipynb)。

* * *

```
TRAINING = True
with K.get_session() as sess:
    shp = [10, 200, 200, 3]
    shp1 = [10, 7, 7, 80]
    inp = K.placeholder(shp)
    inp1 = K.placeholder(shp1)
    queue = tf.FIFOQueue(20, [tf.float32, tf.float32], [shp, shp1])
    x1, y1 = queue.dequeue()
    enqueue = queue.enqueue([inp, inp1])
    model = keras.applications.ResNet50(False, "imagenet", x1, shp[1:])
    for i in range(3):
        model.layers.pop()
        model.layers[-1].outbound_nodes = []
        model.outputs = [model.layers[-1].output]
    output = model.outputs[0]  # 7x7
    # Reduce filter size to avoid OOM
    output = Conv2D(32, (1, 1), padding="same", activation='relu')(output)
    output3 = Conv2D(5 * (4 + 11 + 1), (1, 1), padding="same", activation='relu')(
        output)  # YOLO output B (4 + nb_class +1)
    cost = tf.reduce_sum(tf.abs(output3 - y1))
    optimizer = tf.train.RMSPropOptimizer(0.001).minimize(cost)
    sess.run(tf.global_variables_initializer())

    def get_input():
        # Super long processing I/O bla bla bla
        return np.arange(prod(shp)).reshape(shp).astype(np.float32), np.arange(prod(shp1)).reshape(shp1).astype(
            np.float32)

    def generate(coord, enqueue_op):
        while not coord.should_stop():
            inp_feed, inp1_feed = get_input()
            sess.run(enqueue_op, feed_dict={inp: inp_feed, inp1: inp1_feed})

    start = time.time()
    for i in tqdm(range(10)):  # EPOCH
        for j in range(30):  # Batch
            x,y = get_input()
            optimizer_, s = sess.run([optimizer, queue.size()], 
                                     feed_dict={x1:x,y1:y, K.learning_phase(): int(TRAINING)})
    print("Took : ", time.time() - start)

    coordinator = tf.train.Coordinator()
    threads = [threading.Thread(target=generate, args=(coordinator, enqueue)) for i in range(10)]
    for t in threads:
        t.start()
    start = time.time()
    for i in tqdm(range(10)):  # EPOCH
        for j in range(30):  # Batch
            optimizer_, s = sess.run([optimizer, queue.size()], 
                                     feed_dict={K.learning_phase(): int(TRAINING)})
    print("Took : ", time.time() - start)

    def clear_queue(queue, threads):
        while any([t.is_alive() for t in threads]):
            _, s = sess.run([queue.dequeue(), queue.size()])
            print(s)

    coordinator.request_stop()
    clear_queue(queue, threads)

    coordinator.join(threads)
    print("DONE Queue")
```

```
from keras.layers import Input, Dense
from keras.models import Model

from keras.datasets import mnist

import numpy as np
```

```
Using TensorFlow backend.
```

```
# this is the size of our encoded representations
encoding_dim = 32  # 32 floats -> compression of factor 24.5, assuming the input is 784 floats

# this is our input placeholder
input_img = Input(shape=(784,))
# "encoded" is the encoded representation of the input
encoded = Dense(encoding_dim, activation='relu')(input_img)

# "decoded" is the lossy reconstruction of the input
decoded = Dense(784, activation='sigmoid')(encoded)

# this model maps an input to its reconstruction
autoencoder = Model(input_img, decoded)
```

```
# this model maps an input to its encoded representation
encoder = Model(input_img, encoded)
```

```
# create a placeholder for an encoded (32-dimensional) input
encoded_input = Input(shape=(encoding_dim,))
# retrieve the last layer of the autoencoder model
decoder_layer = autoencoder.layers[-1]
# create the decoder model
decoder = Model(encoded_input, decoder_layer(encoded_input))
```

```
autoencoder.compile(optimizer='adadelta', loss='binary_crossentropy')
```

```
(x_train, _), (x_test, _) = mnist.load_data()

x_train = x_train.astype('float32') / 255.
x_test = x_test.astype('float32') / 255.
x_train = x_train.reshape((len(x_train), np.prod(x_train.shape[1:])))
x_test = x_test.reshape((len(x_test), np.prod(x_test.shape[1:])))
```

```
#note: x_train, x_train :) 
autoencoder.fit(x_train, x_train,
                epochs=50,
                batch_size=256,
                shuffle=True,
                validation_data=(x_test, x_test))
```

