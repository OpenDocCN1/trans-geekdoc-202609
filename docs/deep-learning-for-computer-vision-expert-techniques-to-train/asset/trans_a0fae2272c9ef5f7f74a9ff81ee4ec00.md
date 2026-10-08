

## 相似性学习

这里是数据集中存在的图像示例：

![](img/48c861eac4dc634fbf2a09fdbe884beb_189_0.png)

由 Cao 等提出，并复自 http://www.robots.ox.ac.uk/~vgg/vgg_face2/web_page_img.png

每个唯一身份的图像数量最小、平均和最大值分别为 87、362.6 和 843。

## 计算脸部之间的相似性

脸部相似性的计算是一个多步问题。必须先检测脸，然后找到特征点（fiducial points）。根据特征点对人脸进行对齐以便比较。正如我之前提到的，人脸检测类似于目标检测。因此，为了找到人脸之间的相似性，我们首先通过以下代码导入所需的库以及 `facenet` 库：

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

## 第6 章

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

现在我们将处理图像路径以获取嵌入（embeddings）。相应的代码如下：

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

## 寻找最优阈值

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

## 第6 章

现在，使用以下代码从文件夹获取图像路径：

```python
def get_image_paths(image_directory):
    image_names = sorted(os.listdir(image_directory))
    image_paths = [os.path.join(image_directory, name) for name in image_names]
    return image_paths
```

人脸聚类是把同一个人的图像分组在一起的过程。可以提取脸部的嵌入，并可以使用像 kmeans 这样的算法算法进行聚类。TensorFlow 提供了一个名为 `tf.contrib.learn.kmeans` 的 API 用于 kmeans。

## 总结

在本章中，我们涵盖了相似性学习的基础。我们学习了度量学习、孪生网络和 FaceNet。我们还涵盖了对比损失和三元组损失。两个不同的领域——排序和推荐——也得到了涵盖。最后，通过理解检测、特征点、相似性评分等步骤，涵盖了人脸识别的逐步流程。

在下一章中，我们将理解循环神经网络及其在自然语言处理中的应用。稍后，我们将使用语言模型结合图像模型来进行图像描述。

## 图像描述

在本章中，我们将处理图像描述问题。这涉及到检测物体，并为图像找到对应的描述。图像描述曾被认为是一个非常困难的问题，但现在已经取得了相当不错的结果。本章使用了一个带有对应说明的数据集。

本章将涵盖以下内容：

- 理解不同的数据集以及评估它们的指标
- 理解用于自然语言处理问题的一些技术
- 向量模型的不同术语
- 图像描述的几种算法
- 不理想的结果和改进空间

## 理解问题和数据集

自动为图像生成描述是一项关键深度学习任务，因为它结合了语言和视觉两个世界。这个问题的独特性使其成为计算机视觉领域的主要问题之一。针对该问题的数据集较少。最著名的是第 4 章目标检测中过的 COCO 数据集的扩展。

