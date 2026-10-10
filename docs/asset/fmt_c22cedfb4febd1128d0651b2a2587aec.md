
`glasses_input = tf.placeholder(tf.float32, shape=[None, no_glasses_classes])`

`headpose_input = tf.placeholder(tf.float32, shape=[None, no_headpose_classes])`

```
接下来，按照如下代码构建卷积层的主模型：
```

```
image_input_reshape = tf.reshape(image_input, [-1, image_size, image_size],
name='input_reshape')

convolution_layer_1 = convolution_layer(image_input_reshape, 16)

pooling_layer_1 = pooling_layer(convolution_layer_1)

convolution_layer_2 = convolution_layer(pooling_layer_1, 48)

pooling_layer_2 = pooling_layer(convolution_layer_2)

convolution_layer_3 = convolution_layer(pooling_layer_2, 64)

pooling_layer_3 = pooling_layer(convolution_layer_3)

convolution_layer_4 = convolution_layer(pooling_layer_3, 64)

flattened_pool = tf.reshape(convolution_layer_4, [-1, 64],
name='flattened_pool')

dense_layer_bottleneck = dense_layer(flattened_pool, 1024)

dropout_bool = tf.placeholder(tf.bool)

dropout_layer = tf.layers.dropout(
inputs=dense_layer_bottleneck,
rate=0.4,
training=dropout_bool)
```

```
接下来，使用以下代码为所有任务创建 logits 分支：
```

```
landmark_logits = dense_layer(dropout_layer, 10)

smile_logits = dense_layer(dropout_layer, 2)

glass_logits = dense_layer(dropout_layer, 2)

gender_logits = dense_layer(dropout_layer, 2)

headpose_logits = dense_layer(dropout_layer, 5)
```

```
如下代码单独计算所有面部特征的损失：
```

```
landmark_loss = 0.5 * tf.reduce_mean(
tf.square(landmark_input - landmark_logits))

gender_loss = tf.reduce_mean(
tf.softmax_entropy_with_logits(
labels=gender_input, logits=gender_logits))

smile_loss = tf.reduce_mean(
tf.softmax_entropy_with_logits(
labels=smile_input, logits=smile_logits)

glass_loss = tf.reduce_mean(
tf.softmax_entropy_with_logits(
labels=glasses_input, logits=glass_logits)

headpose_loss = tf.reduce_mean(
tf.softmax_entropy_with_logits(
labels=headpose_input, logits=headpose_logits)
```

```
loss_operation = landmark_loss + gender_loss +
smile_loss + glass_loss + headpose_loss
```

```
现在，我们将按照如下代码初始化优化器并开始训练：
```

```
optimizer = tf.train.AdamOptimizer().minimize(loss_operation)

session = tf.run(tf.initialize_all_variables())

fiducial_test_data = fiducial_data.test

for batch_no in range(batches):
    fiducial_data_batch = fiducial_data.train.next_batch(batch_size)
    loss, landmark_loss, _ = session.run(
        [loss_operation, landmark_loss, optimizer],
        feed_dict={
            image_input: fiducial_data_batch.images,
            landmark_input: fiducial_data_batch.landmarks,
            gender_input: fiducial_data_batch.gender,
            smile_input: fiducial_data_batch.smile,
            glasses_input: fiducial_data_batch.glasses,
            headpose_input: fiducial_data_batch.pose,
            dropout_bool: True
        })
    if batch_no % 10 == 0:
        loss, _landmark_loss, _ = session.run(
            [loss_operation, landmark_loss],
            feed_dict={
                image_input: fiducial_test_data.images,
                landmark_input: fiducial_test_data.landmarks,
                gender_input: fiducial_test_data.gender,
                smile_input: fiducial_test_data.smile,
                glasses_input: fiducial_test_data.glasses,
                headpose_input: fiducial_test_data.pose,
                dropout_bool: False
            })
```

此过程可以用于检测面部特征以及关键点。

![](img/48c861eac4dc634fbf2a09fdbe884beb_187_0.png)

## 人脸识别

人脸识别或面部识别是从数字图像或视频中识别身份的过程。让我们在接下来的章节中学习人脸识别可用的数据集。

### 野标签人脸 (LFW) 数据集

`LFW` 数据集包含 13,233 张脸，涉及 5,749 个独立人物，被认为是人脸验证数据集的标准数据集。可以通过链接 `http://vis-www.cs.umass.edu/lfw/` 访问。

### YouTube 人脸数据集

`YouTube` 人脸数据集包含 3,425 个视频片段，涉及 1,595 个独立人物。这些视频采集自 `YouTube`。该数据集每个人人至少有两个视频。该数据集被认为是视频人脸验证的标准数据集。可以通过链接 `https://www.cs.tau.ac.il/~wolf/ytffaces/` 访问。

### CeleFaces 属性数据集 (CelebA)

`CelebA` 数据集标注了身份，以及 5 个人脸关键点和 40 种属性。数据库中有 10,177 个独立人物和 202,599 张脸部图像。它是人脸验证、检测、关键点和属性识别问题最大的数据集之一。图像具有良好的面部变化和多样化的标注。可以通过链接 `http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html` 访问。

## 相似性学习

这里是数据集中存在的图像示例：

![](img/48c861eac4dc634fbf2a09fdbe884beb_189_0.png)

由 `Cao` 等提出，并复自 `http://www.robots.ox.ac.uk/~vgg/vgg_face2/web_page_img.png`

每个唯一身份的图像数量最小、平均和最大值分别为 87、362.6 和 843。

### 计算脸部之间的相似性

脸部相似性的计算是一个多步问题。必须先检测脸，然后找到特征点（`fiducial points`）。根据特征点对人脸进行对齐以便比较。正如我之前提到的，人脸检测类似于目标检测。因此，为了找到人脸之间的相似性，我们首先通过以下代码导入所需的库以及 `facenet` 库：

```python
import scipy.misc
import tensorflow as tf
import numpy as np
import os
import facenet
print(facenet)
from facenet import load_model, prewhiten
import align.detect_face
```

## 相似性学习

### 第6 章

图像可以所示所示加载和对齐：

```python
def load_and_align_data(image_paths, image_size=160, margin=24,
    gpu_memory_fraction=1.0):
    minsize = 20
    threshold = [0.6, 0.7, 0.7]
    factor = 0.709
    print('Creating networks and loading parameters')
    with tf.Graph().as_default():
        gpu_options = tf.GPUOptions(per_process_gpu_memory_fraction=gpu_memory_fraction)
        sess = tf.Session(config=tf.ConfigProto(gpu_options=gpu_options,
            device_placement=False))
        with sess.as_default():
            pnet, rnet, onset = align.detect_face.create_mtcnn(sess, None, None)
    nrof_samples = len(image_paths)
    img_list = [None] * nrof_samples
    for i in range(nrof_samples):
        img = misc.imread(os.path.expanduser(image_paths[i]), mode='RGB')
        img_size = np.array(img.shape)[0:2]
        bounding_boxes = align.detect_face.detect_face(img, minsize,
            pnet, rnet, threshold, factor)
        det = np.squeeze(bounding_boxes[0, 0:4])
        bb = np.zeros(4, dtype=np.int32)
        bb[0] = np.maximum(det[0] - margin / 2, 0)
        bb[1] = np.maximum(det[1] - margin / 2, 0)
        bb[2] = np.minimum(det[2] + margin / 2, img_size[1])
        bb[3] = np.minimum(det[3] + margin / 2, img_size[0])
        cropped = img[bb[1]:bb[3], bb[0]:bb[2], :]
        aligned = misc.resize(cropped, (image_size, image_size),
            interp='bilinear')
        prewhitened = prewhiten(aligned)
        img_list[i] = prewhitened
    images = np.stack(img_list)
    return images
```

## 相似性学习

现在我们将处理图像路径以获取嵌入（`embeddings`）。相应的代码如下：

```python
def get_face_embeddings(image_paths, model='/20170512-110547/'):
    images = load_and_align_data(image_paths)
    with tf.Graph().as_default():
        with tf.Session() as sess:
            load_model(model)
            images_placeholder = tf.get_default_graph().get_tensor_by_name("input:0")
            embeddings = tf.get_default_graph().get_tensor_by_name("embeddings:0")
            phase_train_placeholder = tf.get_default_graph().get_tensor_by_name("phase_train:0")
            feed_dict = {images_placeholder: images, phase_train_placeholder: False}
            emb = sess.run(embeddings, feed_dict=feed_dict)
    return emb
```

现在我们将使用以下代码计算嵌入之间的距离：

```python
def compute_distance(embedding_1, embedding_2):
    dist = np.sqrt(np.sum(np.square(np.subtract(embedding_1,
embedding_2)))
    return dist
```

此函数将计算嵌入之间的欧几里得距离。

### 寻找最优阈值

使用前面的函数可以计算该系统的准确率。以下代码可用于计算最优阈值：

```python
import sys
import argparse
import os
import re
from sklearn.metrics import classification_report
from sklearn.metrics import accuracy_score
```

## 相似性学习

### 第6 章

现在，使用以下代码从文件夹获取图像路径：

```python
def get_image_paths(image_directory):
    image_names = sorted(os.listdir(image_directory))
    image_paths = [os.path.join(image_directory, name) for name in image_names]
    return image_paths
```
