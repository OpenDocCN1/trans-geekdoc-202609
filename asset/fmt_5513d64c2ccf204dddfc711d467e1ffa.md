
近年来，针对信号和图像处理的研究已开展多年，旨在提高图像的质量和分辨率，以便在文本或图形转换为数字格式以实现更好的用户交互后能够更好地理解。Medhavi Malik \[6\] 探讨了数字图像处理的机制，概述了检索、识别和恢复图像以创建精美的二维图形所涉及的步骤。创建图像进一步分为两个阶段：通过模拟信号处理创建二维图像，以及通过数字图像处理创建所需图像。还涵盖了更多方法来描述如何在模拟到数字或数字到模拟格式中处理图像，包括图像增强、图像分割、聚类、压缩和采集。本文有助于理解处理后增强图像质量所需的方法 \[3\]。Chithra 和 Bhavani \[2\] 提出了一系列图像处理技术以获得良好的结果。通过应用去噪滤波器、对图像进行预处理以及图像采集，将基础二维图像转换为更好格式的过程。利用 `SVM` 分类器进行数字图像分类以产生决策边界，以及使用 `KNN` 算法来识别最接近的匹配以生成图像。本文的结论指出，虽然图像可以使用多种方法进行修改以提供准确性，但图像的质量始终由其清晰度决定。因此，为了改善用户交互，优先选择能够产生清晰准确图像视图的算法而不是其他算法 \[4\]。Akanska Singh 和其他作者 \[7\] 提出了一项关于文本到数字图像转换的研究。本文的目标是通过将其转换为易于理解的图片来简化用户的文本理解。`GAN-CLS` 用于训练判别器，使其不会被生成器创建的假图像欺骗，从而帮助将数据库中的文本与正确的图像匹配。此外，`PySimpleGUI` 提供的交互式技术用于处理文本以生成准确的图像，这是一种使文本对用户友好的图形用户界面。因此，使用 `GAN-CLS` 和 GUI 实现转换过程相对容易，以成功将转换后的图像与其正确文本匹配 \[1\]。Guo-Shiang Lin 与其合著者一起解释了如何结合不同技术将二维图像生成令人信服的三维图像。他们使用基于分割的前景提取技术将图像中的前景物体与背景分离，从而提取需要在三维空间中操作的对象。为了使场景具有深度感，使用基于深度线索的前景深度估计来计算物体与观察者之间的相对距离。利用神经网络进行深度剖面分类提高了区分前景和背景物体的能力，并促进了更精确的深度估计。用于立体感知的色彩增强是修改图像颜色以使其更适合三维观看的过程。为了实现更身临其境的视觉体验，研究结论涉及精确估计场景中物体的深度并有选择地增强其外观 \[5\]。在本研究中，我们利用 AIML 结合多种数据科学算法，直接从文本和绘图生成三维模型。`GAN` 结合矢量成像、`OCR`、`CNN` 的 `RPN` 和稳定扩散是为此目的使用的算法之一。通过使用这些算法和技术，可以创建一个桥梁，处理和转换手写文本和绘图为可由用户在三维查看器中查看的数字三维图像。

## 3. 材料与方法

### 3.1. 卷积神经网络

深度学习是机器学习 (`ML`) 的一个分支，其算法基于人类大脑的架构，其基础是 `CNN`。`CNN` 接收数据，学习识别数据中的模式，然后为一组新的相似数据预测结果。`CNN` 用于解决对象检测和计算机视觉相关的问题。

卷积神经网络中有 3 层，分别是：

* 卷积层
* Relu 层
* 池化层
* 全连接层

**卷积层：** 为了生成总结输入中观察到的特征存在的特征图，对输入应用滤波器。它提取基本特征，如对角线或水平的边缘。以下层接收此输出并使用它来识别更复杂的特征。

**Relu 层：** 在此层（Figure 31.1）中，我们从被滤波的图像中删除所有负值并将其替换为零。

![Figure 31.1: Relu layer (Removal of negative values).](img/fig31_1_C.jpg)

Figure 31.1: Relu layer (Removal of negative values).

**池化层：** 池化层（Figure 31.2）的目标是减小图像大小。该层通过减小维度来降低复杂性并提高 `CNN` 的效率。池化有两种类型：平均池化和更多池化。

![Figure 31.2: Pooling layer (Reduction of image size).](img/fig31_2_C.jpg)

Figure 31.2: Pooling layer (Reduction of image size).

**全连接层：** 这是图像分类发生的层（Figure 31.3）。我们使用卷积和池化层的工作公式。

![Figure 31.3: Fully connected layer (Classification of image).](img/fig31_3_C.jpg)

Figure 31.3: Fully connected layer (Classification of image).

### 3.2. 区域建议网络 (RPN)

在 `RCNN` 系列中，区域建议网络 (`RPN`) 的主要功能是对象检测。我们已经学习了如何在 R-CNN 中使用选择性搜索来提取多个区域。区域建议网络是在 faster R-CNN 中创建的，用于使用小型网络生成区域建议。`RPN` 中的分类器可以返回区域的概率。此外，它还具有一个回归器，可返回边界框坐标。

区域建议网络涉及以下步骤：

* 卷积神经网络
* 生成锚框
* 将锚框分类为前景/背景
* 边界框回归调整

### 3.3. 光学字符识别

光学字符识别 (`OCR`) 是一种将文本图像转换为计算机可读文本格式的过程。例如，如果你扫描表格或收据，你的计算机将扫描保存为图像文件。文本编辑器无法用于修改、查找或计算图像文件中的单词。或者，你可以使用 `OCR` 将图像转换为文本文档并存储其中的文本数据。

**OCR 遵循以下步骤：**

* 图像获取
* 预处理
* 文本识别
* 模式匹配
* 特征提取
* 后处理

### 3.4. 矢量成像

由矢量图形组成的艺术被称为矢量艺术。这些基于数学公式的点、线、曲线和形状被称为图形。由于缩放不会导致分辨率低或质量损失，因此矢量图片文件可以调整到你所需的任何大小。

### 3.5. 生成对抗网络 (GAN)

生成对抗网络 (`GANs`) 是一类强大的神经网络，用于无监督学习。

A discriminator and a generator are components of GANs. The generator attempts to trick the discriminator by creating fake samples of data (such as images, sounds, etc.). Conversely, the Discriminator attempts to differentiate between the authentic and fraudulent samples. Neural networks, such as the generator and discriminator, compete with one another throughout the training phase (Figure 31.4). The procedure is repeated multiple times, and with each iteration, the generator and discriminator become increasingly proficient at their respective tasks.

![Figure 31.4: Working of Generative adversarial networks.](img/fig31_4_C.jpg)

Figure 31.4: Working of Generative adversarial networks.

### 3.6. Stable diffusion

Deep learning and neural networks are used to extract relevant features and spatial information from the input photographs in order to create 3D models from 2D images. The depth and structure of the objects in the image are then estimated using these extracted features, leading to the reconstruction of a 3D render (Figure 31.5).

![Figure 31.5: Stable diffusion process.](img/fig31_5_C.jpg)

Figure 31.5: Stable diffusion process.

Stable diffusion modals use cutting edge methods to produce both image and audio. Diffusion is commonly used in text-to-image, text-to-video, and text-to-3D applications viewer.

### 3.7. Proposed method

The following illustration depicts a schematic approach to 3D image modeling that is used to convert a scanned image into a similar 3D image with a single click. The GAN used in this model is the core of this project that is used to generate a 3D image from a 2D image and is also used in various aspects for the proper operation of this model. Another tool we used to improve the model’s performance is regional proposal network (RPN), which is faster than R-CNN and uses a cross entropy loss function to classify image regions as either object or background. We also used various vision API approaches and dependencies to ensure the software’s smooth performance and to assist the system in combat-ing security threats. We are confident that this model will be a great achievement in the field of 3D modeling, and that it will be the best approach for drawing any image without taking too much time, as opposed to the traditional drawing method, which involves first drawing on paper diagrams and then manually drawing that in the digital drawing tools. This model is outfitted with every possible algorithm and technology that can assist people in saving the time they waste in manual traditional drawing methods.

## 4. Flow Chart

### 4.1. Working principle

The front end of the software is connected to the Tenser Flow and offers multiple data tools to help you consolidate, clean, and pre-process data at scale. It aids us in detecting, locating, and tracing an object from an image. The authors developed a model by combining various approaches that has the ability to produce a 3D of any image scanned, whether it is on paper, hand drawn, or clicked. Dependencies have been added, which makes it easier for developers to manage and maintain software by preventing conflicts, errors, and other problems. Now, the scanning process begins when the user scans or captures an image using the camera module connected to the software. If the image is of an object, it will be transferred to the CNN layer, and if text is detected, it will be transferred to the RPN/OCR layer, where OCR is the process that converts an image of text into a machine-readable text format, and RPN returns the coordinates of bounding boxes, and this processed data will be transferred. To use a GAN for 3D model reconstruction, we first train it on a set of 2D images of an object from various perspective. The generator is then used to generate new 2D images of the object from novel viewpoints not included in the training data. Researchers can reconstruct a 3D model of the object by matching these 2D images to known viewpoints. This data will be transferred to the stable diffusion layer (Figure 6). Stable diffusion is a model for text-to-image conversion. Its primary purpose is to generate detailed images from text descriptions. Diffusion enables anyone with a decent computer and GPU to generate and view almost any type of image they can imagine. The modal class is then created to store data on the cloud, and the stored data is then moved to the recycler view, making your model more efficient in both time and space, because it recycles existing structures rather than constantly creating new ones. The recycler view allows the user to edit, modify, or move the content as desired. The finalized obtained data will now be displayed by the software’s 3D viewer.

![Figure 31.6: Flowchart of proposed method.](img/fig31_6_C.jpg)

Figure 31.6: Flowchart of proposed method.

## 5. Conclusions
