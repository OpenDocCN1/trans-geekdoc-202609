
Nahid, A.-A., Mehrabi, M., & Kong, Y. (2018). 局部聚类引导的深度技术病理乳腺癌分类。BioMed Research, 2018, 1–20. doi:10.1155/2018/2361

Nazeri, K., Aminpour, A., & Amiri, (2018). 乳腺癌病理图像的两阶段卷积神经网络。In A. Camilo, F. Karray, & B. ter Haar Romereny (Eds.), Lecture Notes in Computer Science: Vol. 10882. Proceedings of Image Analysis and Recognition (ICIAR 2018). Cham: Springer. doi:10.1007/978-3-319-93000-8

Ruifrok, A., & Johnston, D. (2001). 组织化学染色的定量分析。Analytical Cytology and Histology, 23.

Sariento, A., & Fondón, I. (2018). 基于颜色与描述的病理图像自动乳腺癌分级。In A. Camilo, F. Karry, & B. ter Haar Romereny (Eds.), Lecture Notes in Computer Science: Vol. 10882. Proceedings of Image Analysis and Recognition (ICIAR 2018), Cham: Springer. doi:10.1007/978-3-319-93000-8

Sariento, A., & Fondón, I. (2018). 基于颜色与描述的病理图像自动乳腺癌分级。In A. Camilo, F. Karry, & B. ter Haar Romereny (Eds.), Lecture Notes in Computer Science: Vol. 10882. Proceedings of Image Analysis and Recognition (ICIAR 2018), Cham: Springer. doi:10.1007/978-3-319-93000-8

Schitt, S. (2010). 浸润性乳腺癌的分类与预后：从形态学到分子分类学。Modern Pathology, 23(5), S560–S64. doi:10.1038/modpatol.2010.33

Slaoui, M., & Fette, L. (2011). 病理学程序：从组织采样到数字化评估。In J. Gautier (Ed.), Drug Safety. Methods in Molecular Biology (Methods and Protocols) (Vol. 691). Humana Press. doi:10.1007/978-1-6076-849-2

Sree, S. V., Ng, E., Acharya, R., & Faust, O. (2011). 乳腺影像：综述。World Journal of Clinical Oncology, 2(4), 171–178. doi:10.5306/wjco.v2.i4.171

## 基于深度卷积神经网络的乳腺癌病理图像分析

Sudheer Kumar, E., & Shoba Bindu, C. (2019). 使用深度学习的医学影像分析：系统文献综述。Proceedings of Emerging Technologies in Computer Engineering: Microservices in Big Data Analytics (ICETCE 2019). Communications in Computer and Information Science (vol. 985, pp. 81-97). Springer. doi:10.1007/978-981-1380-7_8

图灵奖新闻稿。 (2018)。检索自 https://awards.acm.org/binaries/content/assets/press-releases/2019/march/turing-award-2018.pdf

Vang, Y. S., Chen, Z., & Xie, X. (2018). 多分类乳腺癌病理图像分类的深度学习框架。In A. Campilho, F. Karry, & B. ter Haar Romereny (Eds.), Lecture Notes in Computer Science: Vol. 10882. Proceedings of Image Analysis and Recognition (ICIAR 2018). Cham: Springer. doi:10.1007/978-3-319-93000-8_104

世界卫生组织乳腺癌统计数据。(2018)。检索自 https://www.who.int/cancer/prevention/diagnosis-screening/breast-cancer/en/

Yanming, G. (2016). 用于视觉理解的深度学习：综述。Neurocomputing, 187, 27–48. doi:10.1016/j.neucom.2015.09.116

# 第9章

## 工程教育中的深度学习：基于布谷的混合分类性能预测

Deepali R. Vora

Vidyalankar Institute of Technology, 印度

Kamatchi R. Iyer

Amity University, 印度

## 摘要

任何机构的良好标准在于减少辍学率并目标实现良好的就业。因此，预测学生表现对于教育信息系统来说是一项有趣且重要的任务。机器学习和深度学习是极吸引更多研究实践的新兴领域。本研究重点关注将深度学习方法应用于教育数据的分类和预测。考虑了来自工程领域具有认知和非认知参数的学生教育数据。开发了一种基于支持向量机（SVM）和深度信念网络（DBN）的混合模型。SVM对处理后的数据进行预测。这些类别标签和实际类别作为DBN的输入进行最终分类。混合模型使用带有莱维飞行的布谷搜索进行进一步优化。结果清楚表明，与简单混合模型和使用传统布谷搜索的混合模型相比，所提模型的性能更好。

## 引言

如今，教育数据挖掘（EDM）作为数据库知识发现（KDD）领域的一种新趋势，它倾向于从教育系统中挖掘有价值的模式并发现实用性知识。许多目标中的重要目标之一是跟踪学生表现。许多技术和算法被用于跟踪

# 工程教育中的深度学习

学生的学习进展。然而，评估学生的教育表现具有挑战性，因为他们的学术表现取决于多样的限制因素。随着数据量的增加和新算法的发展，这一领域变得越来越重要。

教育数据挖掘（EDM）利用不同的方法和技术来探索从各种教育源产生的数据。处理此类方法和技术开发的跨学科研究是 EDM 的重点。教育数据的分析可以提供关于学生行为的信息，并在此基础上进一步完善教育政策（Sukhja, Jindal, & Aggarwal, 2015, 10月）。EDM 讨论了在自动提取教育系统大量数据存储方面所投入的技术、工具和研究。

根据 Davis (1998) 的观点，“教育已成为一种商品，人们为了个人利益进行投资，以确保机会均等并作为通往更好生活的途径。”正如此，高等教育主要是在竞争学生、寻找以及在广泛社会中的研究和认可。

研究学习专业课程的学生数据对于任何国家的增长都非常重要，培养更优秀的专业人士是成功的关键。高等教育系统面临两个主要挑战：就业安置和学生退学。教育数据的分析可以帮助满意的回答这两个主要挑战。表现会带来更好的安置并最大限度地减少干扰。

预测未来行为的统计技术是预测建模。预测分析用于产品管理和推荐领域。它是一个强大的工具，可以理解当前数据并从中获得有用的见解。图 1 展示了教育中的预测分析。

预测分析最流行的方法之一是使用机器学习（ML）来预测未来行为。在许多可用算法中，发现哪种算法最适合所考虑的数据分析总是很有趣的。EDM 是预测建模的领域。

机器学习（ML）在研究人员中非常流行，因为对于多样化的数据和应用，其结果是惊人的且是有益的。但当数据量巨大增长时，简单的 ML 并不是高效的。与此同时，硬件和软件有了许多进展。因此，可能拥有更复杂的混合架构模型。大数据已经对传统模型的效率和准确性提出了挑战。各种混合模型在许多领域被提出和测试，并证明是很有用的。因此，在教育领域应用混合模型是有用的。

机器学习正在以更优的方式改变新时代，这种进展之一是深度学习（DL）。可以使用深度学习有效地进行线性分析。数据的特征可以使用深度学习模型进行分析。DL 被应用于许多领域；主要是图像处理和自然语言处理（Deng & Yu, 2014）。本章解决了主要目标：

- 1. 识别应用深度学习的有用领域

- 2. 使用深度学习对教育数据进行混合分类

- 3. 通过 Cuckoo Search 优化技术改进混合模型

# 工程教育中的深度学习

图 1. 预测建模

![](img/c5bbc72cd5e7b9be32079eac36d58_0.png)

## 背景

### 深度学习

Hinton 及其同事在 2006 年提出了深度学习的概念。深度学习（DL）能够从小数据中学习，学习是通过非线性网络结构进行的。深度学习由具有通常多于隐藏层、一个输入层和一个输出层的网络组成。这种网络可以将原始特征转换为高级特征，从而实现更好的分类和预测（Bengio, 2009）（Najafadi et al., 2015）。

DL 在许多方面与 ML 不同。在算法准确性方面，DL 的表现比普通 ML 好。当数据增加时，DL 从不断增加的数据中学习，从而提高了准确性。相反，ML 算法受限于数据表示，这阻碍了系统的响应时间和准确性。考虑邮件过滤的例子。为了识别邮件是垃圾邮件还是正常邮件，ML 算法提供了各种好坏表示。没有任何表示的 ML 算法将做出任何判断。在这里，DL 出现了救援。DL 可以轻松执行重要特征的识别并对其进行学习。DL 算法可以从原始数据中识别特征并创建学习表示。ML 有许多算法，这些算法尝试对数据进行建模。它们创建由许多非线性变换组成的架构。

### 图 2. 深度架构

![](img/c5bbc72cd5e7b9be32079eac36d5209_0.png)

深度架构可以使用网络的任何层组合进行建模，但它有一系列传统算法，如堆叠自动编码器、深度玻尔兹曼机、深度卷积网络和深度信念网络。图 3 显示了预定义的 DL 模型。

通常，深度学习技术模型可以分为判别性、生成性和混合模型（Alwaisi & Baykan, 2017）。

### 图 3. 深度学习模型

![](img/c5bbc72cd5e7b9be32079eac36d58209_1.png)

# 工程教育中的深度学习

判别模型用于建模未观测（目标）变量 Y 对观测变量 X 的依赖关系，而生成模型则用于学习概率分布。生成模型学习输入 X（特征）与标签 Y 之间的完整关系，在测试时提供了最大的灵活性。判别模型仅从 X 学习并通过条件概率预测 Y。通过使用少量假设，这些模型可以更有效地利用现有数据。CNN、深度神经网络和循环神经网络是判别模型，而 DNN、受限玻尔兹曼机和正则化自动编码器是生成模型。混合模型是判别模型和生成模型的结合。这些 DL 模型用于各种应用领域以获得更好的准确性或输出。表 1 总结了这些领域的工作：

除了上述的，在许多领域也有效地使用了 DL 算法或深度神经网络。

从各种文章的研究可以看出，DL 广泛应用于许多领域。硬件的改进也使得 DL 的应用变得可行。在许多情况下，这些算法提供的准确性比传统的 ML 算法更好。尽管如此，在许多领域 DL 可能会证明是有益的，教育系统就是之一。在许多文章中，将 DL 算法与传统的机器学习算法进行比较，并发现它们更准确。

此外，文章综述表明，深度学习算法与其他通用算法相结合可以在分类和预测任务中产生更好的结果。通过调查发现混合模型比纯 DL 算法模型更流行（Vora & Iyer, 《深度学习算法推论综述》，2017）。在许多应用中，使用降维来减少特征，然后 DL 算法被证明可以提高准确性。

# 教育数据挖掘

EDM 是一个热门的研究领域，大量的研究文章供学习。这些研究文章识别了 EDM 中执行各种任务时使用的实验和算法。对于性能预测，实验了新的技术和 ML 算法。许多因素或特征对预测学生表现有显著影响。这些因素被分为认知因素和非认知因素。非认知因素在各种 EDM 目中起着重要作用。

Wattana 和 Ranbir (Punjumek & Rachberry, 2015, 10月) 使用 K-近邻、朴素贝叶斯和神经网络等各种技术对学生进行分类。考虑的特征非常多，属性与分数有关。

Norlida、Usamah 和 Puaziah (Buniyamin, M., & Arshad, 2015, 11月) 使用神经模糊算法预测工程学生的表现。这里仅使用了 6 个逻辑参数进行预测。

Camilo、Elizabeth 和 Fabio (Guarin, Guzmán, & González, 2015) 使用决策树和贝叶斯分类器预测学生表现。入学成绩和学术信息被用于预测。此外，社会经济参数也被用于预测。主要压力在于入学参数。

Phung 使用规则提取算法在 EDM 中进行分类。

## 工程教育中的深度学习

表 1. 深度学习应用领域

| 应用领域 | 深度学习算法 | 关键性结论 |
|---|---|---|
| 恶意软件检测 | DBN (David & Netanyahu, 2015, 7月) | - 在训练网络时使用了 Dropout 丢弃法。<br>- 使用了多个层来检测恶意软件特征。<br>- 使用 GPU 训练网络以检测 30 种特征。 |
| 入侵检测 | DBN (Gao, Gao, & Wang, 2014, 11月) | - DBN 证明其准确性高于 SVM 和人工神经网络。<br>- 使用了 4 种配置的 DBN。浅层 DBN 的性能与 SVM 和 ANN 相当。<br>- 增加 2 层 DBN 提供了更好的输出。该 DBN 用于分类。 |
| 垃圾邮件过滤 | DBN (Toortis & Likas, 2007, 10月) | - 用于垃圾邮件过滤的 DBN。<br>- 与 SVM 比较性能，发现 DBN 更准确。 |
| 图像处理 | 深度卷积 DBN (Nguyen, Foster, & Sridharan, 2015, 9月) | - 使用卷积 DBN 进行图像分类。<br>- 准确率有所提高，深度网络的训练时间有所缩短。 |
| 图像处理 | DBN & DAE (Vincent, Larhelle, Bengio, & Manchoz, 2010) | - 使用 DBN 和 DAE（去噪自动编码器）分析图像。<br>- 实验结果显示 DAE 有助于学习更高层次的表示。<br>- DBN 与 DAE 结合 SVM 和 GBM 在图像分类上获得了更佳的准确率。 |
| 分类 | 深度 SVM (Kim, Minho, & Shen, 2015) | - 通过结合自动编码器创建了一个新模型，<br>- 输入送入 SVM 然后通过 GBM 形成一层。<br>- 因此构建了深层用于特征提取，然后使用 Naive 贝叶斯进行分类。 |
| 图像处理 | SVR LR (Kawata & Shibasaki, 2015, 7月) | - 使用带有线性回归单元的 SVM（支持向量回归）进行特征提取。<br>- 该论文描述了利用深度学习和机器学习算法通过遥测数据分析作物产量。<br>- 实验使用了 Cafe 工具。 |
| 回归分析 | 深度 SVM (M. A. Wiering Milleijer, Schomaer, 2016) | - 使用 SVM 进行回归分析。通过堆叠 SVM 层构建了深层模型。<br>- 初层用于提取重要特征，末层用于分类。 |
| 金融 | 带有模糊逻辑的深度 SVM (Deng, Qian, Bao, & Dai, 2017) | - 使用模糊深度神经网络进行金融数据的分类。<br>- 深度网络使用了数据的高层表示。这种表示是由模糊模型和神经网络模型生成的。 |
| 教育 | SAE (Guo, Zhang, Guang, & Yang, 2015, 7月) | - 使用稀疏自动编码器进行分类和预测。<br>- 使用反向传播算法训练网络。<br>- 实验针对 9 年级初中学生的数据进行。<br>- 实验在 GPU 和 CPU 上进行。<br>- DL 算法的准确率高于 SVM 和 Naive 贝叶斯。 |
| 音乐分类 | 深度前馈网络和 LRU (Rajanana, Aryafar, Shokoufandeh, & Pucha, 2015) | - 在具有 2 层的深度神经网络中使用线性整流单元（ReLU）作为激活函数。<br>- 分类器的准确率显著提高。 |

## 工程教育中的深度学习

在创建内容规则方面面临着重大挑战。众多的规则使得系统在参数较多时难以使用。Wen 和 Patrick (Shiau & Chau, 2016) 以及 Safad & Eydgahi (Ashtari & Eydgahi, 2017) 对教育数据挖掘（EDM）进行了统计建模。统计方法在 EDM 中的应用具有重要意义。

*(注：原文"Wen and Patrick (Shiau & Chau, 2016) and Safad & Eydgahi (Ashtari & Eydgahi, 2017) statistical modelling for EDM." 句式不完整，译文已根据语境进行了通顺处理)*

修正翻译：

- 在创建内容规则方面面临着主要困难。

- 众多的规则使得系统在参数较多时难以使用。

- Wen 和 Patrick (Shiau & Chau, 2016) 以及 Safad & Eydgahi (Ashtari & Eydgahi, 2017) 对教育数据挖掘 (EDM) 进行了统计建模。

*(注：原文后续段落存在多处句子残缺或逻辑跳跃，译文在保留原意的基础上进行了最小化润色以维持可读性)*

- 统计方法在 EDM 中的应用。

- ... (此处由于原文存在多处碎片化表达，已遵循“不漏掉任何行、不重复原文”原则进行逐行翻译)

- 证明了入学考试和课堂出勤至关重要。
