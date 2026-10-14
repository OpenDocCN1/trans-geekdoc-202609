
```python
cnn.compile(
    loss=keras.losses.CategoricalCrossentropy(),
    optimizer=tf.keras.optimizers.Adam(),
    metrics=["accuracy"]
)

cnn.summary()

#define callbacks
file_name = SAVE_PATH + 'lenet-weights-checkpoint.h5'
checkpoint = ModelCheckpoint(file_name, monitor='val_loss', verbose=1,
    save_best_only=True, mode='min')
reduce_lr = LearningRateScheduler(scheduler, verbose=1)
early_stopping = EarlyStopping(monitor='val_loss', min_delta=0.01,
    patience=16, verbose=1)
#tensor_board = TensorBoard(log_dir='./logs', write_graph=True)
callbacks_list = [checkpoint, reduce_lr, early_stopping]

hist = cnn.fit(x_train, y_train_label, batch_size=batch_size,
    epochs=num_epochs, callbacks=callbacks_list,
    validation_split=0.2)

test_scores = cnn.evaluate(x_test, y_test_label,
    verbose=2)

print("Test loss:", test_scores[0])
print("Test accuracy:", test_scores[1])

y_prob = cnn.predict(x_test)
y_pred = y_prob.argmax(axis=-1)

submission = pd.DataFrame(index=pd.RangeIndex(start=1, stop=10001,
    step=1), columns=['Label'])
submission['Label'] = y_pred.reshape(-1,1)
submission.index.name = "ImageId"
submission.to_csv(SAVE_PATH + '/lenet_pred.csv', index=True, header=True)

plt.figure()
plt.plot(hist.history['loss'], 'b', lw=2.0, label='train')
plt.plot(hist.history['val_loss'], '--r', lw=2.0, label='val')
plt.title('LeNet model')
plt.xlabel('Epochs')
plt.ylabel('Cross-Entropy Loss')
plt.legend(loc='upper right')
plt.show()

plt.figure()
plt.plot(hist.history['accuracy'], 'b', lw=2.0, label='train')
plt.plot(hist.history['val_accuracy'], '--r', lw=2.0, label='val')
plt.title('LeNet model')
plt.xlabel('Epochs')
plt.ylabel('Accuracy')
plt.legend(loc='upper left')
plt.show()
```

模型训练

模型评估

```python
DATA_PATH = "/content/drive/MyDrive/data/101_ObjectCategories/"

def get_closest_images(acts, query_image_idx, num_results=5):
    num_images, dim = acts.shape
    distances = []
    for image_idx in range(num_images):
        distances.append(distance.euclidean(acts[query_image_idx, :],
            acts[image_idx, :]))
    #end for
    idx_closest  = sorted(range(len(distances)), key=lambda k:
        distances[k])[1:num_results+1]

    return idx_closest

def get_concatenated_images(images, indexes, thumb_height):
    thumbs = []
    for idx in indexes:
        img = Image.open(images[idx])
        img = img.resize((int(img.width * thumb_height / img.height),
            int(thumb_height)), Image.ANTIALIAS)
        if img.mode != "RGB":
            img = img.convert("RGB")
        thumbs.append(img)
    concat_image = np.concatenate([np.asarray(t) for t in thumbs], axis=1)

    return concat_image

if __name__ == "__main__":
    num_images = 5000
    images = [os.path.join(dp,f) for dp, dn, filenames in
        os.walk(DATA_PATH) for f in filenames \
            if os.path.splitext(f)[1].lower() in ['.jpg','.png','.jpeg']]
    images = [images[i] for i in sorted(random.sample(range(len(images)),
        num_images))]

    #CNN encodings
    base_model = ResNet50(weights='imagenet')
    model = Model(inputs=base_model.input,
        outputs=base_model.get_layer('avg_pool').output)

    activations = []
    for idx, image_path in enumerate(images):
        if idx % 100 == 0:
            print('getting activations for %d/%d image...'
                %(idx,len(images)))
        img = image.load_img(image_path, target_size=(224, 224))
        x = image.img_to_array(img)
        x = np.expand_dims(x, axis=0)
        x = preprocess_input(x)
        features = model.predict(x)
        activations.append(features.flatten().reshape(1,-1))
```

在ImageNet上预训练的ResNet50模型

```python
print('computing PCA...')
acts = np.concatenate(activations, axis=0)
pca = PCA(n_components=300)
pca.fit(acts)
acts = pca.transform(acts)

print('image search...')
query_image_idx = int(num_images*random.random())
idx_closest = get_closest_images(acts, query_image_idx)
query_image = get_concatenated_images(images, [query_image_idx], 300)
results_image = get_concatenated_images(images, idx_closest, 300)

plt.figure()
plt.imshow(query_image)
plt.title("query image (%d)" %query_image_idx)
plt.show()

plt.figure()
plt.imshow(results_image)
plt.title("result images")
plt.show()
```

降低激活维度

图10.7展示了一把椅子的查询图像（左侧）和检索到的最近邻图像（右侧）。检索到的图像与查询图像高度相似。在下一节中，我们将介绍用于序列数据的神经网络。

![](img/325742126d3ff007c6c385f4ffb5c3be_252_0.png)

图10.7 ResNet50图像搜索结果

## 10.3 循环神经网络

循环神经网络（RNN）被设计用于处理序列数据。RNN维护过去时刻的内部状态，并提供一种将序列（Seq）编码为向量（Vec）及其逆转换的自然方式。RNN的应用范围从语言生成（Vec2Seq）、序列分类（Seq2Vec）到序列翻译（Seq2Seq）。在本节中，我们将重点讨论使用双向LSTM进行序列分类，以及使用预训练词嵌入计算序列相似性。

RNN使用一个隐藏层，该层将当前输入$x_t$和先前状态$h_{t-1}$结合起来。

$$h_t = f(W_{hh}h_{t-1} + W_{xh}x_t + b_h)$$  
(10.10)

这里，$W_{hh}$是隐藏层到隐藏层的权重，$W_{xh}$是输入到隐藏层的权重，$b_h$是偏置项。可选地，每一步都可以产生输出$y_t$。

$$y_t = g(W_{hy}h_t + b_y)$$  
(10.11)

整体架构如图10.8所示。让我们在下一小节中看看RNN的一些应用。

![](img/325742126d3ff007c6c385f4ffb5c3be_253_0.png)

图10.8 LSTM循环神经网络架构

### 10.3.1 LSTM序列分类

在本节中，我们的目标是判断IMDb电影评论的情感倾向。我们首先对评论中的每个单词进行分词，并通过可训练的嵌入层将其转换为向量。词向量序列构成前向LSTM模型的输入，该模型将序列编码为向量。与此同时，我们将序列输入到后向LSTM模型中，并将其向量输出与前向模型的输出拼接，从而生成电影评论的潜在表示。

$$h_t^{\rightarrow} = f(W_{hh}^{\rightarrow}h_{t-1}^{\rightarrow} + W_{xh}^{\rightarrow}x_t + b_h^{\rightarrow})$$
$$h_t^{\leftarrow} = f(W_{hh}^{\leftarrow}h_{t-1}^{\leftarrow} + W_{xh}^{\leftarrow}x_t + b_h^{\leftarrow})$$
$$h_t = [h_t^{\rightarrow}, h_t^{\leftarrow}]$$  
(10.12)

这里，$h_t$同时考虑了来自过去和未来的信息。这两个LSTM组合起来称为双向LSTM，它们处理输入数据时，仿佛时间在正向和反向同时流动。图10.9展示了双向RNN的架构。

在将评论编码为向量后，我们对多个带有L2正则化和dropout的全连接层取平均，以通过输出层的sigmoid

![](img/325742126d3ff007c6c385f4ffb5c3be_254_0.png)

激活函数来判断情感为正面还是负面。让我们看一下基于Keras/TensorFlow库的LSTM序列分类代码。

### 清单10.4 用于情感分类的双向LSTM

```python
import numpy as np
import pandas as pd

import tensorflow as tf
from tensorflow import keras

from keras.models import Sequential
from keras.layers import LSTM, Bidirectional
from keras.layers import Dense, Dropout, Activation, Embedding

from keras import regularizers
from keras.preprocessing import sequence
from keras.utils import np_utils

from keras.callbacks import ModelCheckpoint
from keras.callbacks import TensorBoard
from keras.callbacks import LearningRateScheduler
from keras.callbacks import EarlyStopping

import matplotlib.pyplot as plt

tf.keras.utils.set_random_seed(42)

SAVE_PATH = "/content/drive/MyDrive/Colab Notebooks/data/"

def scheduler(epoch, lr): # Learning rate schedule
    if epoch < 4:
        return lr
    else:
        return lr * tf.math.exp(-0.1)

if __name__ == "__main__":

    #load dataset
```
