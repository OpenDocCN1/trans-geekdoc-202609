
我们依靠关于可用服务的信息，利用包括智能手机和平板电脑在内的智能设备来满足日常生活中的各种需求，因此，开发语音命令以搜索个人所需服务，对于通过机器学习技术利用这些智能设备筛选有用且准确的信息至关重要。人们可以要求智能设备搜索有用信息，以满足现代社会中的个人需求，从而造福日常生活。例如，在大流行期间，人们需要通过互联网获取可用服务和健康信息，以获取准确信息，许多人正在自我教育关于健康与预防、疾病与治疗选择、护理服务以及有益健康行为的知识，尤其是在当下的大流行期间。机器学习为改善智能设备提供的服务提供了有用信息。由于智能设备的普及。网络犯罪和网络赋能犯罪是现代社会的关键问题，这些网络犯罪的成本在全球范围内不断增加。在美国，应对这些网络安全问题的成本估计每年约为 1200 亿美元，每年影响超过 50 万个就业岗位 (Lewis 2018; Demirdjian and Mokatsian 2015)。基于社交媒体上的数字多媒体数据，不同年龄段的人群也面临着不同的网络安全威胁。机器学习和深度学习技术可以改善生活的不同方面。

## 参考文献

American Cancer Society. (2019). What Is Melanoma Skin Cancer? https://www.cancer.org/cancer/melanoma-skin-cancer/about/what-is-melanoma.html

Bovet, A., & Makse, H. A. (2019). Influence of fake news in Twitter during the 2016 US presidential election. Nature Communications , 10, 7. doi:10.1038/s41467-018-07761-2

Convolutional neural network. (2021). In Wikipedia. Available: https://en.wikipedia.org/wiki/Convolutional_neural_network

Demirdjian, Z. S., & Mokatsian, Z. (2015). The cost of cyber crimes to business and society. ASBBS Proceedings, 22(1), 104.

Geeks for Geeks. (2019). Removing stop words with NLTK in Python. Available at: https://www.geeksforgeeks.org/removing-stop-words-nltk-python/

Huber, H. (2017). The most beautiful home for sale in every state in America. Architectural Digest. https://www.architecturaldigest.com/gallery/most-beautiful-home-for-sale-in-every-state-in-america

IFRA. (2012). WAN. Available: http://www.wan ifra.org/microsites/world-press-trends

Kaggle. (2010). Your Machine Learning and Data Science Community. https://www.kaggle.com/

Lewis, J. A. (2018). Economic impact of cybercrime-no slowing down. https://a51.nl/sites/default/files/pdf/economic-impact-cybercrime.pdf

Mitchell, A., Gottfried, J., Barthel, M., & Shearer, E. (2016). How Americans get their news. Pew Research Center’s Journalism Project. Available: https://www.journalism.org/2016/07/07/pathways-to-news/

Myszczynska, M. A., Ojamies, P. N., Lacoste, A. M. B., Neil, D., Saffari, A., Mead, R., Hautbergue, G. M., Holbrook, J. D., & Ferraiuolo, L. (2020). Applications of machine learning to diagnosis and treatment of neurodegenerative diseases. Nature Reviews. Neurology , 16(8), 440–456. https://www.nature.com/articles/s41582-020-0377-8?13571

Natural language processing. (2021). In Wikipedia. Available: https://en.wikipedia.org/wiki/Natural_language_processing

Odden, M. C., & Melzer, D. (2019). Machine Learning in Aging Research. J Gerontol A. , 74(12), 1901–1902. doi:10.1093/gerona/glz074

Recurrent neural network. (2021). In Wikipedia. Available: https://en.wikipedia.org/wiki/Recurrent_neural_network

Shu, K., Wang, S., & Liu, H. (2019). Beyond news contents: The role of social context for fake news detection. Proceedings of the twelfth ACM international conference on web search and data mining. https://arxiv.org/pdf/1712.07709.pdf

The Breaking News Meme Generator. (n.d.). Break Your Own News. https://breakyourownnews.com/

Vectorizer. (2021). https://scikitlearn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html

Xiang, X., Lu, X., Halavanau, A., Xue, J., Sun, Y., Lai, P.H., & Wu, Z. (2021). Modern senicide in the face of a pandemic: an examination of public discourse and sentiment about older adults and COVID-19 using machine learning. The Journals of Gerontology: Series B, 76(4), e190-e200. doi: 10.1093/geronb/gbaa128

Zhang, J., Cui, L., Fu, Y., & Gouza, F. B. (2019). Fake News Detection with Deep Diffusive Network Model. arXiv preprint arXiv:1805.08751

# 第 2 章

**A. B. M. Rezbaul Islam**  

Sam Houston State University, USA

## 摘要

计算机视觉是计算机科学的一个研究领域，它赋予了计算机人类感知的能力。计算机视觉的目标是理解图像及其内容。计算机视觉已从简单的模式识别发展到解决各种复杂的现实问题。如今，计算机视觉已应用于科学领域的各个域，不局限于计算机科学。它也广泛用于医学、生物学、物理学和化学等领域。计算机视觉近期的飞速发展归功于机器学习 (ML) 的影响。ML 是人工智能的一个子领域。机器学习是一种让计算机从提供的数据中学习并随时间提高其性能的方法。计算机视觉问题复杂，需要正确选择算法。在本章中，将讨论一些在计算机视觉中广泛使用的机器学习算法。理论概念与现实世界的计算机视觉问题相关，例如人类皮肤检测。

## 引言

机器学习是过去几十年计算机视觉研究中被引用最多的词汇。海量数据的可用性以及对数据分析的需求，使得机器学习成为每位数据科学家的必选项。如今，很难找到一项未使用机器学习进行的数据分析。机器学习为高性能数据分析开启了新纪元，有时甚至超越人脑，这实在非同寻常 (Steinberg, 2017)。与其他研究领域类似，计算机视觉受益于机器学习，因此许多计算机视觉研究人员在研究中使用机器学习。在计算机视觉中，问题域差异很大。图像分割、分类、识别、特征提取是一些最常用的问题域。在机器学习兴起之前，其他技术——滤波、波长分析、直方图处理、傅里叶变换、形态学算法——被用于特定任务。尽管如此，图像差异很大，这些方法在执行特定工作时各有其局限性。

### 机器学习并非新概念

1949 年，唐纳德·赫布在名为《行为的组织》的书中提出了这一概念。在书中，作者介绍了一种基于人脑细胞相互作用的模型。赫布写道：“当一个细胞反复协助激发另一个细胞时，第一个细胞的轴突会在与第二个细胞胞体接触的地方发展出突触小瘤（如果已存在则将其扩大）。”（Keith, 2019）。然而，神经生理学家麦卡洛克和数学家沃尔特·皮茨早在 1943 年就发明了人脑神经元的概念。著名的艾伦·图灵利用同一概念创建了“图灵测试”。弗兰克·罗森布拉特于 1958 年设计了第一个人工神经网络——“感知机”，用于模式和形状识别。与其他突破性技术不同，机器学习在 1980 年代和 1990 年代处于休眠状态。IBM 等科技巨头和研究实验室——AT&T 贝尔实验室——在 21 世纪初让机器学习重获新生。在 21 世纪，利用机器学习实现的最重大的计算机视觉突破是 AlexNet（Krizhevsky, 2012）和 GoogleBrain（2012）。AlexNet 是 ImageNet 竞赛的获胜者。值得一提的是，ImageNet 是一个拥有庞大图像数据库的图像分类竞赛。赛后，许多计算机视觉研究人员将其视为契机，利用机器学习开发各种计算机视觉应用模型。本章将重点关注机器学习算法及其在计算机视觉中的各种实现。此外，还将简要讨论与预先存在方法的相关对比。

### 计算机视觉

人们理所当然会问什么是计算机视觉，以及为什么机器学习是计算机视觉应用的宝贵工具。计算机视觉是计算机科学的一个领域，它处理数字图像和视频以处理和理解视觉数据。计算机视觉的重点是发现模式、物体及其各种属性。为了发现这些属性，研究人员试图构建一个类似于人类视觉过程的计算机模型。计算机视觉的核心概念是“教导”或训练计算机系统理解图像或视频的最小部分，并理解该部分。基于这种理解，特定算法解释结果。研究结果常用于图像和物体识别、分割、语音生成、自动驾驶汽车、人脸识别、增强现实和混合现实以及医学图像处理。尽管如此，计算机视觉的任务并非易事。其中涉及多个挑战。模仿人类视觉是最大的挑战，因为我们并不完全确定人类视觉是如何处理事物的——让计算机“看”原来非常困难。发明一种像我们一样“看”的机器是一项欺骗性的棘手任务，不仅因为让计算机做到这一点很难，还因为我们首先并不完全确定人类视觉是如何工作的。研究生物视觉需要了解感知器官（如眼睛）以及大脑感知的解释。虽然在绘制这一过程和发现系统使用的技巧与捷径方面已取得很大进展，但像任何涉及大脑的研究一样，前路漫漫。

图像和视频是计算机视觉的主要可用数据。目前，人人都能接触到相机；人们拍摄大量照片并录制视频。这种海量的图像和视频数据可用于各种目的。例如，执法人员可能利用这些数据识别关注人员；计算机科学家可能想为身体有障碍的人开发基于手势的计算机访问方式；农民可能想通过拍摄患病作物的照片来识别作物病害。实现清单可以很长，且新的挑战性问题每天都在涌现。这些需求要求某种能精准解决问题的高效方法。解决棘手计算机视觉问题的努力之一就是使用机器学习算法。

### 机器学习

机器学习是一个训练计算机系统解决现实问题的过程，重点关注图像分类、物体检测、分割等。机器学习通常分两步：训练和测试。在训练阶段，机器学习方法从输入数据中“学习”某些特征，所学知识用于在测试数据上执行任务。

训练阶段至关重要。机器学习算法的性能深度依赖于训练。每种机器学习方法都有其独特的训练方式。训练阶段可以用一个简单的例子来解释：假设我们想训练一个婴儿识别苹果。婴儿没有关于苹果的任何先验知识。更具体地说——苹果长什么样、苹果的形状和颜色。要让婴儿识别苹果，我们可以给婴儿看一个苹果。婴儿会看一眼苹果，然后尝试学习苹果的形状、颜色和纹理等特征。之后，如果我们把苹果放进水果篮，问婴儿哪个是苹果，婴儿就能认出苹果。基于训练过程，所有机器学习可分为：监督学习、无监督学习和半监督学习。这些方法各有优缺点，根据问题领域选择使用。

#### 监督学习

监督学习使用标记数据进行训练。标记数据包含已知的知识，用于训练机器学习模型。监督机器学习技术如今很普遍。许多模型被开发并用于图像分类、物体检测。然而，目前有大量可用数据——文本、图像、视频、时间序列——但极少数是标记的。标记数据需要领域专家知识，且耗时昂贵。

##### 半监督学习

半监督机器学习结合了监督和无监督机器学习的优势。它在半监督学习中使用少量标记数据和大量未标记数据。因此，它不依赖于标记数据的可用性。

##### 无监督学习

无监督机器学习不需要任何标记数据。因此，这种方法寻找给定数据的潜在模式。聚类就是此类机器学习技术的一个例子。

##### 表 1. 机器学习算法分类法

| 机器学习算法类别 | 机器学习算法示例 | 在计算机视觉中的实现 |
| --- | --- | --- |
| 监督学习 | 线性回归 | 预测 |
|  | 神经网络 | 分类、检索、检测、分割、识别 |
|  | 支持向量机 | 分类、回归、异常值检测 |
|  | 随机森林 | 分类、回归 |
|  | 朴素贝叶斯 | 分类、预测 |
| 无监督学习 | K-means 聚类 | 基于图像数据特征的聚类 |
|  | 谱聚类 | 将未标记数据分配到组 |
|  | 层次聚类 | 通过迭代分组创建聚类树 |
|  | 主成分分析 | 降低数据复杂度并识别相似性 |
| 半监督学习 |  | 使用未标记数据训练模型 |

### 监督机器学习

#### 监督学习

监督学习是一种机器学习技术，用于从带标签的训练数据中获取信息（模式、特征）（Rieke, 1997）。通常，训练数据包含一组带标签/已知的数据实例。例如，在图像分类问题中，模型旨在对图像进行分类，训练数据将包含已知类别的实例。监督机器学习算法分析训练数据，从中学习，然后利用该学习成果执行各种任务。监督算法还可以通过将新实例与训练阶段获得的学习知识进行映射，来给未见过的实例打标签。然而，这需要在归纳偏置的帮助下对训练数据进行泛化。监督算法广泛应用于各种应用中。将监督算法应用于问题领域的过程需遵循以下步骤。

##### 训练数据选择

监督算法高度依赖训练数据。性能与训练数据的选择有关。选择正确的训练数据集至关重要。例如，在动物图像分类中，训练数据可能是单一动物（猫、狗等）或同类型的多种动物。然而，训练数据集应能代表现实世界的实例。收集一组输入实例，并确定相应的输出。此过程可借助统计度量或人工专家参与来完成。

##### 特征选择

选择训练数据后，需要选择一些特征作为学习函数。这些特征将被监督算法学习，并用于未来的预测。当监督算法能从训练数据集中更好地学习时，将表现出高准确性。通常，训练数据会被转换为特征向量，以表示可用特征的数量。特征数量的选择应谨慎，因为数据可能具有多个维度，这会增加算法为获得更好预测而学习的复杂度。

##### 学习函数结构

鉴于存在各种监督算法，学习函数结构需要预先确定。完成这些后，算法需要通过训练数据进行训练。此外，一些监督算法在训练阶段提供选择特定参数的灵活性。这些参数因问题而异，需要自适应调整。监督算法的性能评估可通过与训练数据集不同的测试集来衡量。这将指示算法的学习准确性。

##### 监督算法的工作原理

监督学习使用已知数据集通过特征训练算法以进行预测。该已知数据集也称为训练数据，与期望输出相关联。监督学习通过学习特征与输出之间的关系来建立模型，随后用于对新数据集（测试数据集）进行预测。

| 图 1. 监督学习概览 |
| --- |
| ![Figure978-1-7998-7776-9.ch002.f01](img/ch002.f01.png) |

给定形式为 `{(t1,f1)………(tn,fn)}` 的实例训练集，其中 `ti` 是训练样本的第 `i` 个特征向量，`fi` 是标签（已知类别）。监督算法试图映射一个函数：`T → F`。该函数称为假设空间。有时它也用作评分函数，即函数返回最大分值。存在各种监督学习算法，它们借助条件概率使用概率模型，例如朴素贝叶斯。目前有许多可用于不同目的的监督学习算法。为正确的问题领域选择合适的学习算法非常重要。选择监督学习算法需要更多考量。

##### 偏差-方差权衡
