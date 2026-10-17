
- **人脸识别 (Facial recognition)**: 该 `Python` 库模型在“Labeled Faces in the Wild”基准数据上的准确率达到 99.38%。在 `Python` 中识别和处理脸部是最简单的任务，它通过单幅图像标记输入高效工作。该库是世界上最常用且最简单的库。人脸识别库是使用深度学习构建的 `C++` 工具包的。人脸识别库还提供了一个简单的命令行工具，可以使用命令行对图像文件夹进行人脸识别。深度信息对于改进人脸检测系统起着关重要的作用（Burgin et al., 2011）。

我们使用 `OpenCV` 提供的 `Haar` 级联和 `Python` 人脸识别库来获得最准确的人脸识别结果。在此，我们根据检测脸脸的准确性比较了 `Haar` 级联的所有分类器。分类器用于眼睛、鼻子、正脸、侧脸和侧侧。

### 3.3.4 Haar 级联及其分类器

`Haar` 级联是机器学习中常用的一种检测算法（Padilla et al., 2012）。它有助于识别对象，无论该对象是非生物、人类还是其他物体。

根据 Singh 等人（2013）的观点，`Haar` 级联算法中通常包含四个步骤：

- 选择对象的特征
- 数据收集（制作数据集）
- 模型训练
- 输出结果（根据数据集识别对象）

在第一步中，我们选择对象的特定特征，通过这些特征我们可以识别特定对象。例如，在人脸中，这些特征是眼睛、鼻子、微笑、整个正脸或侧脸。

在第二步中，在计算机视觉（主要通过摄像头）的帮助下，我们拍摄许多上一步中关注的特征图像，并记住图像越多，识别时的准确性越高。

在第三步中，我们根据作为输入收集的图像数量对系统进行训练。

在第四步中，如果系统识别了它经过训练的对象，则定义输出为完美。

对于这项工作，我们使用 `Haar` 级联不同分类器的输出来比较它们识别特定脸部的准确性。这些分类器使用人脸的特征：眼睛、鼻子、微笑、正脸和侧脸。为了检查特定时间的准确性，我们为某次测试选取特定数量图像，然后更改另一个测试的图像数量（Le, 2011; Yang and Wang, 2016）。

# AI 在现代医疗保健领域的崛起

#### 3.3.4.3 分类器之间的比较

测试 1：我们选取 200 张某人特定脸部特征的图像制作数据集，然后训练系统并比较表 3.3 中描述的所有分类器的准确性。

测试 2：我们选取 500 张某人特定脸部特征的图像制作数据集，然后训练系统并比较表 3.4 中描述的所有分类器的准确性。

### 表 3.3

训练图像数量为 200 时的分类器比较

| 分类器 | 数据收集 | 训练数据集 | 最终测试 | 准确率 |
| --- | --- | --- | --- | --- |
| 眼睛 | [image] | [image] | [image] | -47% |
| 正脸 | [image] | [image] | [image] | 40% |
| 微笑 | [image] | [image] | [image] | -44% |
| 侧脸 | [image] | [image] | [image] | 42% |
| 鼻子 | [image] | [image] | [image] | -88% |

### 表 3.4

训练图像数量为 500 时的分类器比较

| 分类器 | 数据收集 | 训练数据集 | 最终测试 | 准确率 |
| --- | --- | --- | --- | --- |
| 眼睛 | [image] | [image] | [image] | 30% |
| 正脸 | [image] | [image] | [image] | 43% |
| 微笑 | [image] | [image] | [image] | -15% |
| 侧脸 | [image] | [image] | [image] | 43% |
| 鼻子 | [image] | [image] | [image] | -88% |

测试 3：我们选取 1000 张某人特定脸部特征的图像制作数据集，训练系统并比较表 3.5 中描述的所有分类器的准确性。

#### 3.3.4.4 人脸识别库

人脸识别库是一个主要用于识别不同人脸的 `Python` 库。它的编程方式使其能够自动检测和识别脸部；我们只需为其创建数据集并导入该库。准确率

### 表 3.5

训练图像数量为 1000 时的分类器比较

| 分类器 | 数据收集 | 训练数据集 | 最终测试 | 准确率 |
|---|---|---|---|---|
| 眼睛 | ![image]() | ![image]() | ![image]() | 42% |
| 正脸 | ![image]() | ![image]() | ![image]() | 48% |
| 微笑 | ![image]() | ![image]() | ![image]() | 1% |
| 侧脸 | ![image]() | ![image]() | ![image]() | 46% |
| 鼻子 | ![image]() | ![image]() | ![image]() | 27% |

通过该库进行人脸识别的准确率在许多研究中被认为约为 99%。它分析摄像头前的实时视频流，并将脸部匹配到存储的图像数据。对于这种人脸识别，使用 128 维输出特征向量来量化脸。因此，训练可以通过三元组进行。对于人脸识别库，我们通过以下方式训练网络：

- 将单幅图像作为输入
- 将图像分类作为输出

## 58 通过 AI 重塑流程

因此，通过应用 `OpenCV` 和深度学习，我们通过以下步骤完成人脸识别过程：

- 人脸检测
- 计算 128 维脸部嵌入（embedding），通过此对脸部进行量化
- 训练用于嵌入的机器
- 进行人脸识别

对于人脸识别库，我们首先创建图像数据集；在数据集中，如图 3.7 所示，仅使用特定脸的单一图像。然后，借助该单一图像作为数据集，它就能识别图 3.8 所示的人脸。

根据图 3.9 的图表，我们发现对于 `Haar` 级联（`Haar` cascade），我们需要输入大量的图像（图像数据集），以便在脸识别过程中获得更高的准确率。在分类器的比较中，我们发现正面脸和侧脸分类器在脸识别方面的准确率远高于任何其他分类器。

![](img/b43ebe8eccbdc43447aca82fb7658570_74_0.png)

**图 3.7** 包含单个图像的数据集。

![](img/b43ebe8eccbdc43447aca82fb7658570_74_1.png)

**图 3.8** 人脸识别。

### AI 在现代医疗领域的兴起

![](img/b43ebe8eccbdc43447aca82fb7658570_75_0.png)

图 3.9 `Haar` 级联分类器的比较。

我们还发现人脸识别库仅需单一输入（图像数据集），并在脸识别过程中提供更准确的结果。我们还可以用它来实时识别脸。

`AI` 技术在医疗领域具有广泛的应用领域，例如针对身体或视觉残障患者，以及其他使用模式识别进行药物发现和使用回归方法进行早期疾病检测。

## 参考文献

- Bansanje, Sanathi, Shyamala, Pooja, Dash, Chandra, Sharath, & Chavan, Bhushan. “A self-governing wheelchair for severely disabled patients in an indoor environment utilizing EEG and laser technologies.” In Emerging Trends and Innovations in Engineering and Technical Research (ICIETR) 2018 International Conference, p. 1–5 (2018).
- Bi, Luzheng, Fan-An & Liu, Yili. “EEG-brain-controlled mobile robots: A survey.” IEEE Transactions on Human-Machine Systems, 43(2), 161–176 (March 2013). doi:10.1109/TSMCC.2012.2219046.
- Bini, S. A. “Artificial machine learning, deep learning and cognitive computing: What do these mean and how will they impact health care?” The Journal of Arthroplasty, 33(8), 2358–2361 (2018).
- Burgin, Walker, Pantofaruoy, Carole & Smart, William D. “Using depth information to improve face detection.” In 2011 6th ACM/IEEE International Conference on Human-Robot Interaction (HRI) (2011).
- Chellapa, R., Wilson, C. L. & Sirohey, C. "Human and machine recognition of faces: A survey." Proceedings of IEEE, 83(5), pp. 705–740 (May 1995).
- Dorner, J., Kozák, S. & Dietze, F. "Object recognition by effective methods and means of computer vision." In IEEE, Stribse, Slovakia (June 9–12, 2015).
- Fabiani, G. E., McFarland, D. J., Jalpaw, J. R. & Pirtscheller, G. "Conversion of EEG activity into cursor movement by a Brain-Computer Interface (BCI)." IEEE Transactions on Neural Rehabilitation and Rehabilitation, 12(3), 331–338 (September 2004).
- Galton, Francis. "Personal identification and detection." Nature, 173–177 (June 21, 1888).
- Gulshan, V. et al. "Development and validation of a deep learning algorithm for detection of diabetic retinopathy in retinal photographs." JAMA, 316, 2402–2410 (2016).
- Jadav, N. K. & Mohan, B. "Eye pattern controlled using wearable EEG." In 2013 3rd IEEE International Conference on Recent Trends in Electronics, Information & Communication Technology (REICT), Bangalore, India, pp. 2382–2386.
- Khurana, Pal, Sharma, Asha, Singh, Shailendra Narayan, Pradeep Kumar. "Survey on object recognition and segmentation techniques." In IEEE, New Delhi (March 16–18, 2016).
- Le, T. H. "Applying artificial neural networks for face recognition." Advances in Artificial Neural Systems, 2011, pp. 1–16.
- Le Nguyen, T. "Artificial intelligence in healthcare: A new technology for both patients and doctors." In 2019 Portland International Conference on Management of Engineering and Technology (PICMET), pp. 1–15.
- Liew, C. "The future of radiology with artificial intelligence: A strategy for success." European Journal of Radiology, 152–156 (2018).
- Mason, S. G. & Bricht, G. "A general framework for brain-computer interface." IEEE Transactions on Neural Rehabilitation and Rehabilitation, 11, 70–85 (March 2003).
- McCarthy, J., McKinsey, M. L., Rochester, N., & Shannon, C. "A proposal for the summer project on artificial intelligence." AI Magazine, 27(4), p. 12 (1955).
- Murthy, S., Kumar, J. & Reddy, B. "Implementation of counterfeit detection." In 2016 Online International Conference on Green Engineering and Technology (GET), pp. 1–6.
- Mussen, A., Middleton, B. & Greens, R. Shortcliffe, E. & Cimino, J. Bioinformatics, pp. 643–674 (Springer, London, 2014).
- Niem, Kristen Dremstra, Alvaro Ventura & Nascimento, O. "EEG based brain computer—Towards a better interface at Aalborg university." IEEE Transactions on Neural Systems and Rehabilitation, 14(2), Article ID 16429, pp. 202–204 (2006).
- Padilla, R., Filho, C. & Costa, M. "Evaluation of Haar cascade classifiers for face detection." Journal of WASET, 6(4), pp. 323–326 (2012).
- Picot, A., Charbonnier, S. & Caplier, A. "On-line detection of drowsiness using visual information." IEEE Transactions on Systems, Man., and Cybernetics—Part A: Systems and Humans, 42(3), pp. 764–775 (May 2012).
- Rakshit, Pushpendu & Sharma, Ravindra. "Building Healthcare 4.0 with smart workforce." In Proceedings of the International Conference on Management & Technovation 2020, pp. 91–94.
- Rana, G. & Sharma, R. "Emerging human resource management practices in Industry 4.0." Strategic HR Review, 18(4), 176–181 (2019).
- Shortliffe, E. Computer-Based Medical Consultations: MYCIN Vol. 2 (Elsevier, New York, 2012).
- Singh, V., Shokeen, V. & Singh, B. "Face detection by Haar cascade classifier with simple and complex backgrounds using OpenCV implementation." International Journal of Advanced Technology in Engineering and Science, 1(12), pp. 33–38 (2013).
- Tsalakanidou, F., Malassiotis, S. & Strintis, M. G. "Face recognition." In Furht, B. (eds.), Encyclopedia of Multimedia (Springer, Boston, MA, 2008).
- Yang, H. & Wang, X. A. "Cascade classifier for face detection." Journal of Algorithms & Computational Technology, 10(3), pp. 187–197 (2016).

![](img/b43ebe8eccbdc43447aca82fb7658570_78_0.png)

# 制造业中的人工智能

V. Harish, D. Krishnaveni, and A. Mansurali

## 目录
