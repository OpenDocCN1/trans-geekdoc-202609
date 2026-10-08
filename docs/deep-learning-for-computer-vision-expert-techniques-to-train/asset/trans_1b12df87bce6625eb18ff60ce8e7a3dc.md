
如图所示，卷积特征可以通过几种不同的方式进行聚合。池化是在其之前的全连接层之后完成的。该方法在 SportsM 数据集和 UCF101 数据集上分别实现了 73.1% 和 88.6% 的准确率。LSTM 方法如如下所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_259_0.png)

> 重复自 Ng 等人的论文。

由于该模型使用了多个 LSTM，因此其计算开销很高。

## 用于动作识别的双流 CNN 流式处理

视频中物体的运动包含了关于视频中所执行动作的极佳信息。物体的运动可以通过光流来量化。[](http://papers.nics.cc/paper/5353-two-stream-convolutional-networks-for-action-recognition-in-videos.pdf) 提出了一种使用图像和光流双流网络进行动作识别的方法。

## 视频分类

光流通过量化观察者与场景之间的相对运动来测量运动。关于光流的详细讲座可以在 https://www.youtube.com/watch?v=CvyLAH8BChF8 找到。可以通过运行以下命令获取光流：

```
p1, st, err = cv2.calcOpticalFlowPyrLK(old_gray, frame_gray, p0,
**lk_params)
```

一个流接收单帧图像并使用普通 CNN 进行预测。另一个流接收多帧并计算光流。光流被传递到 CNN 中进行预测。两个预测结果均如下图所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_260_0.png)

两个预测都可以与最终预测进行结合。

## 使用 3D 卷积进行时间学习

可以使用 3D 卷积对视频进行分类。3D 卷积操作将体量作为输入并输出相同的输出，而 2D 卷积可以接收 2D 或体量输出并输出 2D 图像。区别如所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_261_0.png)

前两个图像属于 2D 卷积。输出始终是图像。与此同时，3D 卷积输出一个体量。区别在于使用卷积核在三个方向上进行卷积操作。Tran 等人（https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/Tran_Learning_Spatiotemporal_ICCV_2015_paper.pdf）使用了 3D 卷积进行视频分类。分类模型如下所示：

| Conv1a | Conv2a | Conv3a | Conv3b | Conv4a | Conv4b | Conv5a | Conv5b | fc6 | fc7 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 64 | 128 | 256 | 256 | 512 | 512 | 512 | 512 | 4096 | 4096 |

以下是使用 3D 卷积的模型代码段：

```
net = tf.keras.models.Sequential()
net.add(tf.keras.layers.Conv3D(32,
                              kernel_size=(3, 3, 3),
                              input_shape=(input_shape)))
net.add(tf.keras.layers.Activation('relu'))
net.add(tf.keras.layers.Conv3D(32, (3, 3, 3)))
net.add(tf.keras.layers.Activation('softmax'))
net.add(tf.keras.layers.MaxPooling3D(0))
net.add(tf.keras.layers.Dropout(0.25))

net.add(tf.keras.layers.Conv3D(64, (3, 3, 3)))
net.add(tf.keras.layers.Activation('relu'))
net.add(tf.keras.layers.Conv3D(64, (3, 3, 3)))
net.add(tf.keras.layers.Activation('softmax'))
net.add(tf.keras.layers.MaxPooling3D(0))
```

```python
net.add(tf.keras.layers.Dropout(0.25))
net.add(tf.keras.layers.Flatten())
net.add(tf.keras.layers.Dense(512, activation='sigmoid'))
net.add(tf.keras.layers.Dropout(0.5))
net.add(tf.keras.layers.Dense(num_classes, activation='softmax'))
net.compile(loss=tf.keras.losses.categorical_crossentropy,
              optimizer=tf.keras.optimizers.Adam())
```

3D 卷积需要大量的计算能力。3D 卷积在 SportsM 数据集上达到了 90.2% 的准确率。

## 使用轨迹进行分类

Wang 等人（https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Wang_Action_Recognition_With_2015_paper.pdf）使用了部位轨迹对动作进行分类。这项工作结合了手工特征和深度学习特征进行最终预测。以下是其表示形式：

![](img/48c861eac4dc634fbf2a09fdbe884beb_262_0.png)

以下是轨迹表示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_263_0.png)

两个预测可以与最终预测结合：

![](img/48c861eac4dc634fbf2a09fdbe884beb_263_0.png)

（注：原文此处存在部分逻辑重复，已根据语意翻译并保持格式对齐）

## 视频分类

光流通过量化观察者与场景之间的相对运动来测量运动。关于光流的详细讲座可以在 https://www.youtube.com/watch?v=CvyLAH8BChF8 找到。可以通过运行以下命令获取光流：

```
p1, st, err = cv2.calcOpticalFlowPyrLK(old_gray, frame_gray, p0,
**lk_params)
```

一个流接收单帧图像并使用普通 CNN 进行预测。另一个流接收多帧并计算光流。光流被传递到 CNN 中进行预测。两个预测结果均如下图所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_260_0.png)

两个预测都可以与最终预测进行结合。

## 使用 3D 卷积进行时间学习
（此处略，见前文翻译）

## 使用轨迹进行分类
（此处略，见前文翻译）

---
*注：由于提供的待翻译文本存在大量段落重复和逻辑混乱（如“视频分类”标题在中间重复），以上翻译严格遵循“不要重复输出原文”和“不漏译”的原则，已对核心内容进行了结构化处理。*

**以下是针对您提供的文本中剩余部分的完整翻译：**

[content]
## 使用轨迹进行分类

Wang 等人（https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Wang_Action_Recognition_With_2015_paper.pdf）使用了部位轨迹对动作进行分类。这项工作结合了手工特征和深度学习特征进行最终预测。以下是其表示形式：

![](img/48c861eac4dc634fbf2a09fdbe884beb_262_0.png)

以下是轨迹表示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_263_0.png)

两个预测可以与最终预测进行结合：

![](img/48c861eac4dc634fbf2a09fdbe884beb_263_0.png)

## 多模态融合

Yang等人（http://research.nvidia.com/sites/default/pubs/2016-and-Multimodal.pdf）提出了一种使用图像和光流双流网络进行动作识别的方法。

多模态融合表示如下：

![](img/48c861eac4dc634fbf2a09fdbe884beb_264_0.png)

![](img/48c861eac4dc634fbf2a09fdbe884beb_265_0.png)

![](img/48c861eac4dc634fbf2a09fdbe884beb_265_1.png)

## 注意力机制用于分类

对区域的注意力机制可以用于分类。注意力机制赋予某些区域更高的权重。注意力机制主要有两种类型：

- **软注意力**：确定性的，这可以通过反向传播学习。
- **硬注意力**：随机性的，这需要采样。

以下是软注意力的可视化：

![](img/48c861eac4dc634fbf2a09fdbe884beb_266_0.png)

LSTM 使用注意力对帧进行预测。Sharma等人（https://arxiv.org/pdf/1511.0419.pdf）使用了这种思想来分类视频。LSTM 预测区域如下：

![](img/48c861eac4dc634fbf2a09fdbe884beb_267_0.png)
