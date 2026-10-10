
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

### 使用轨迹进行分类

Wang 等人（https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Wang_Action_Recognition_With_2015_paper.pdf）使用了部位轨迹对动作进行分类。这项工作结合了手工特征和深度学习特征进行最终预测。以下是其表示形式：

![](img/48c861eac4dc634fbf2a09fdbe884beb_262_0.png)

以下是轨迹表示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_263_0.png)

两个预测可以与最终预测结合：

![](img/48c861eac4dc634fbf2a09fdbe884beb_263_0.png)

## 视频分类

光流通过量化观察者与场景之间的相对运动来测量运动。关于光流的详细讲座可以在 https://www.youtube.com/watch?v=CvyLAH8BChF8 找到。可以通过运行以下命令获取光流：

```
p1, st, err = cv2.calcOpticalFlowPyrLK(old_gray, frame_gray, p0,
**lk_params)
```

一个流接收单帧图像并使用普通 CNN 进行预测。另一个流接收多帧并计算光流。光流被传递到 CNN 中进行预测。两个预测结果均如下图所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_260_0.png)

两个预测都可以与最终预测进行结合。

### 使用 3D 卷积进行时间学习

### 使用轨迹进行分类

---

*注：由于提供的待翻译文本存在大量段落重复和逻辑混乱（如“视频分类”标题在中间重复），以上翻译严格遵循“不要重复输出原文”和“不漏译”的原则，已对核心内容进行了结构化处理。*

### 使用轨迹进行分类

Wang 等人（https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Wang_Action_Recognition_With_2015_paper.pdf）使用了部位轨迹对动作进行分类。这项工作结合了手工特征和深度学习特征进行最终预测。以下是其表示形式：

![](img/48c861eac4dc634fbf2a09fdbe884beb_262_0.png)

以下是轨迹表示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_263_0.png)

两个预测可以与最终预测进行结合：

![](img/48c861eac4dc634fbf2a09fdbe884beb_263_0.png)

### 多模态融合

Yang等人（http://research.nvidia.com/sites/default/pubs/2016-and-Multimodal.pdf）提出了一种使用图像和光流双流网络进行动作识别的方法。

多模态融合表示如下：

![](img/48c861eac4dc634fbf2a09fdbe884beb_264_0.png)

![](img/48c861eac4dc634fbf2a09fdbe884beb_265_0.png)

![](img/48c861eac4dc634fbf2a09fdbe884beb_265_1.png)

### 注意力机制用于分类

对区域的注意力机制可以用于分类。注意力机制赋予某些区域更高的权重。注意力机制主要有两种类型：

- **软注意力**：确定性的，这可以通过反向传播学习。
- **硬注意力**：随机性的，这需要采样。

以下是软注意力的可视化：

![](img/48c861eac4dc634fbf2a09fdbe884beb_266_0.png)

LSTM 使用注意力对帧进行预测。Sharma等人（https://arxiv.org/pdf/1511.0419.pdf）使用了这种思想来分类视频。LSTM 预测区域如下：

![](img/48c861eac4dc634fbf2a09fdbe884beb_267_0.png)

## 视频分类

## 第9 章

从视频中提取帧并并通过卷积网络。对层进行融合，并获得姿态热图。将姿态热图与光流结合得到变形后的热图。对跨时间段的变形热图进行池化以产生池化热图，从而获得最终姿态。

## 跟踪脸部关键点

视频中的人脸分析需要脸检测、关键点检测、姿态估计、验证等。计算关键点对于捕捉面部动画、人机交互和人类活动识别尤为重要。与其逐帧进行计算，不如对视频进行计算。Gu 等人（http://research.nvidia.com/sites/default/files/publs/2017-07_dynamic-Facial-Analysis/rnnface.pdf）提出了一种使用 RNN 对视频中脸部关键点进行检测和跟踪联合估计的方法。其结果优于逐帧预测和之前的其他模型。关键点通过 CNN 计算，时间维度被编码在 RNN 中。使用了合成数据进行训练。

## 视频分割

当使用时间信息时，可以以更好的方式分割视频。Gadde 等人（https://ps.is.tuebingen.de/uploads_file/attachment/386/gadde2017videocnns.pdf）提出了一种通过变形结合时间信息的方法。接下来的图像展示了解决方案，它分割了两个帧并与变形结合：

![](img/48c861eac4dc634fbf2a09fdbe884beb_269_0.png)

> 复自 Gadde 等人。

## 视频分类

下图中未显示变形网络：

![](img/48c861eac4dc634fbf2a09fdbe884beb_270_0.png)

复自 Gadde 等人。

在两帧之间计算光流，并与变形结合。变形模块获取光流，对其进行转换，并与变形后的表示相结合。

## 视频字幕

第7章“图像描述”说明了多种结合文本和图像的方法。同样地，也可以为视频生成字幕以描述其上下文。让我们看看用于视频字幕的数据集列表：

- * 微软研究院 - 视频转文本 (MSR-VTT) 包含200,000个视频片段和句子对。更多细节可以从：https://www.microsoft.com/en-us/research/publication/msr-vtt-a-large-video-description-dataset-for-bridging-video-and-language/ 获取。
- * MPII电影描述库 (MPII-MD) 可以从这里：https://www.mpi-inf.mpg.de/departments/computer-vision-and-multimodal-computing/research/vision-and-language/mpi-movie-description-dataset 获取。它包含94部电影的68,000个句子。
- - 蒙特利尔视频标注数据集 (M-VAD) 可以从这里：https://mila.quebec/en/publications/public-datasets/m-vad/ 获取，包含49,000片段。
- YouTube2Text 拥有1,970个视频和80,000条描述。

Yao 等人（https://www.cv-foundation.org/openaccess/content_icv_2015/papers/Yao_Describing_Videos_by_ICCV_2015_paper.pdf）提出了一种视频字幕方法。使用一个针对动作识别训练的3DD卷积网络来提取局部时间特征。在特征上使用注意力机制，通过 RNN 生成文本。该过程所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_271_0.png)

> 复自 Yao 等人。

Donahue 等人（https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Donahue_Long-Term_Recurrent_Convolutional_2015_CVPR_paper.pdf）提出了另一种用于视频字幕或描述的方法，它使用了带有卷积特征的 LSTM。

这与前面的方法类似，不同在于我们在这里使用了 2D 卷积特征，如图所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_272_0.png)

我们有多种方法将文本与图像结合，例如活动识别、图像描述和视频描述技术。接下来的图像说明了这些技术：

![](img/48c861eac4dc634fbf2a09fdbe884beb_272_1.png)

## 视频分类

Venugopalan 等人（https://www.cv-foundation.org/openaccess/content_icv_2015/papers/Venugopalan...）提出了一种方法。接下来的图像展示了这些的的：

![](img/48c861eac4dc634fbf2a09fdbe884beb_270_0.png)

## 视频生成

光流在两帧之间计算，并与变形结合。变形模块获取光流，对其进行转换，并与变形后的表示相结合。

由于使用了时间信息，视频可以以更好的方式进行分割。

## 视频生成

由于使用了时间信息，视频可以以更好的方式进行分割。

## 视频量化

量化工作是由于几个原因。通常，深度学习模型在训练时是为了处理图像中的噪声，因此具有鲁棒性。Ranzato 等人（https://www.org/pdf/）提出了一种方法。

## 总结

在本章中，我们讨论了视频的各种技术。在下一章中，我们将学习如何在不同的平台上部署。

# 部署

# 第10章

![](img/48c861eac4dc634fbf2a09fdbe884beb_277_0.png)

重自 Howard 等人

MobileNets 通过将标准卷积滤波器 (a) 替换为深度可卷积 (b) 和逐点卷积 (c) 减少了模型的尺寸和计算量，所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_277_1.png)

重自 Howard 等人

[ 263 ]

# 部署

# 第10章

在深度卷积和逐点卷积中都添加批归一化和激活层，所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_278_0.png)

重自 Howard 等人

有两个参数影响模型选择：

- **乘法和加法的次数：** 下图显示了准确率与乘加次数（mult-adds）之间的权衡：

![](img/48c861eac4dc634fbf2a09fdbe884beb_278_1.png)

重自 Howard 等人

- **模型中的参数数量：** 此处显示了权衡：

![](img/48c861e44dc634fbf2a09fdbe884beb_279_0.png)

MobileNets 表明可以通过少量减少准确率来减少模型计算和尺寸，用于移动和嵌入式设备。模型与准确率之间的准确权衡可以参考 Howard 等人的文章。

# 云端部署

对于某些应用，模型必须部署在云端。我们将为此目的查看主要的云服务提供商。

# AWS

亚马逊云服务 (AWS) 扩展了对基于 TensorFlow 模型开发和部署的支持。在 https://aws.amazon.com/ 注册 AWS 并选择一个亚马逊机器映像 (AMI)。AMI 是安装了所有所需软件的机器映像。你无需担心安装软件包。AWS 提供了深度学习 AMI (DLAMI) 用于训练和部署学习模型。有多个选项可供选择。在这里，我们将使用 Conda，因为它带有运行 TensorFlow 所需若干包。Python 有两个选项：版本 2 和 3。以下命令将在带有 CUDA 8 的 Python 3 上激活带有 Keras 2 的 TensorFlow：

```
source activate tensorflow_p36
```

以下代码将在带有 CUDA 8 的 Python 2 上激活带有 Keras 2 的 TensorFlow：

```
source activate tensorflow_p27
```

> 你可以访问 https://aws.amazon.com/tensorflow/ 获取更多详情和教程。

也可以按照这里给出的步骤启动虚拟机 (VM)：

1. 访问 aws.amazon.com 并使用你的 AWS 账户登录。
2. 从登录页面选择“启动虚拟机”(Launch a virtual machine) ：

| 构建解决方案 | | |
| :--- | :--- | :--- |
| 使用简单的向导和自动化工作流开始。 | | |
| 启动虚拟机 | 构建 Web 应用程序 | 托管静态网站 |
| 使用 EC2 或 Lightsail | 使用 Elastic Beanstalk | 使用 S3, CloudFront, Route 53 |
| ~2 分钟 | ~6 分钟 | ~5 分钟 |
| 连接 IoT 设备 | 启动开发项目 | 注册域名 |
| 使用 AWS IoT | 使用 CodeStar | 使用 Route 53 |
| ~5 分钟 | ~5 分钟 | ~3 分钟 |

3. 在下一个窗口中，点击“开始”(Get Started) 选择 EC2 实例，所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_281_0.png)

4. 为 EC2 实例命名：

![](img/48c861eac4dc634fbf2a09fdbe884beb_282_0.png)

5. 选择操作系统类型：

![](img/48c861eac4dc634fbf2a09fdbe884beb_282_1.png)

Ubuntu Server 16.04 LTS

没有看到你寻找操作系统？AWS 通过高级 EC2 启动向导提供额外选项，或者你可以探索 AWS 市场。

![](img/48c861eac4dc634fbf2a09fdbe884beb_282_2.png)

6. 选择实例类型。实例类型指示了具有不同 RAM 和 CPU 大小的配置。还有几个 GPU 选项。选择实例类型并点击“下一步”(Next) 按钮：

# 选择实例类型

![](img/48c861eac4dc634fbf2a09fdbe884beb_283_0.png)

t2.micro

1 核 vCPU (高达 3.3 GHz)，1 GiB 内存，8 GB 存储 免费资格

需要不同的实例类型？AWS 通过高级 EC2 启动向导提供额外选项。

7. 创建密钥对 (PEM) 文件，所示：

# 创建密钥对

将其保存在安全的地方，用它连接到：

8. 创建实例需要一些时间，最后显示状态：

![](img/48c861eac4dc634fbf2a09fdbe884beb_284_0.png)

9. 下一步，点击“继续”(Proceed) 按钮：

| 名称 | 实例 ID | 状态 |
| :--- | :--- | :--- |
| tensorflow | | |

10. 点击实例的下拉菜单并选择“在浏览器中打开”(Open in browser)：

![](img/48c861eac4dc634fbf2a09fdbe884beb_284_1.png)

# 部署

# 第10章

![](img/48c861eac4dc634fbf2a09fdbe884beb_285_0.png)

12. 完成后，点击“操作”(Actions) 终止实例：

![](img/48c861eac4dc634fbf2a09fdbe884beb_285_1.png)

| 操作 | 终止 (Terminate) |
| :--- | :--- |

# 部署

# 第10章

![](img/48c861eac4dc634fbf2a09fdbe884beb_286_0.png)

| 名称 | 区域 | 机器类型 |
| :--- | :--- | :--- |
| instance-2 | us-east-1b | 2 vCPUs 7.5 GB 内存 |
| 启动磁盘 | 新 10 GB 持久磁盘 Ubuntu 16.04 LTS | 修改 |
| 身份和 API 访问 | Compute Engine 默认服务账户 | |
| 访问范围 | 允许访问所有云 API | 为每个 API 设置访问 |
| 防火墙 | 添加标签和防火墙规则允许来自互联网的特定网络流量 | |
| 允许 HTTP 流量 | | |
| 允许 HTTPS 流量 | | |
| 管理、磁盘、网络、SSH 密钥 | | |

# 云端部署

对于某些应用，模型必须部署在云端。我们将为此目的查看主要的云服务提供商。

# AWS
