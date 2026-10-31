
[28] A.M. Tripathi, A. Upadhyay, A.S. Rajput, A.P. Singh, and B. Kumar, "使用图像处理自动检测股骨骨折", 2017 International Conference on Innovations in Information, Embedded and Communication Systems (ICHECS), pp. 1-5, 2017. [http://dx.doi.org/10.1109/ICHECS.2017.8275843]

[29] M. M. Saii and A. M. Mayya, "使用图像处理的手部和手指骨折检测与类型分类." Int. J. Computer Sci. Trends Technol., (IJCST). vol. 6, no. 4, 2018.

[30] W.W. Myint, K.S. Tun, and H.M Tun, "使用 X 射线图像的腿部骨折检测与分类分析", Machine Learning Research, vol. 3, no. 3, pp. 49-59, 2018. [http://dx.doi.org/10.1648/j.mlr.20180303.11]

[31] E. Castro-Gutierrez, L. Estacio-Cerquin, J. Gallegos-Guillen, and J.D. Obando, "使用聚焦于噪声图像的 X 射线成像和处理方法的髋臼骨折检测", 2019 Amity International Conference on Artificial Intelligence (AICAI), pp. 296-302, 2019. [http://dx.doi.org/10.1109/AICAI.2019.8701297]

[32] M. Donnelley and G. Knowles, "计算机辅助长骨骨折检测," in ISSPA, pp. 175-178, 2005. [http://dx.doi.org/10.1109/ISSPA.2005.1580224]

[33] A. Salam, F. Ullah, M. Imad, and M. A. Hassan, "使用机器学习方法诊断皮肤镜图像用于黑色素瘤检测," in 2020 IEEE 23rd International Multitopic Conference (INMIC), pp. 1-5, 2020.

[34] M. Imad, S.I. Ullah, A. Salam, W.U. Khan, F. Ullah, and M.A. Hassan, "基于 X 射线图像使用机器学习技术自动检测人体内的子弹", Int. J. Comput. Sci. Inf. Secur., vol. 18, no. 6, 2020.

[35] M. Imad, N. Khan, F. Ullah, M. A. Hassan, and A. Hussain, "基于胸部 X 射线图像使用机器学习技术的 COVID-19 分类," Journal of Computer Science and Technology Studies, vol. 2, no. 2, pp. 01-11, 2020.

[36] A. Hussain, M. Imad, A. Khan, and B. Ullah, 使用定制高效神经网络在 X 射线图像中识别 COVID-19 的多类分类. AI and IoT for Sustainable Development in Emerging Countries, 2022, pp. 473-486. [http://dx.doi.org/10.1007/978-3-030-90618-4_23]

[37] M. Imad, A. Hussain, M. Hassan, Z. Butt, and N. Sahar, 基于物联网的机器学习和深度学习平台用于 COVID-19 预防和控制：系统综述. AI and IoT for Sustainable Development in Emerging Countries, 2022, pp. 523-536. [http://dx.doi.org/10.1007/978-3-030-90618-4_26]

## 健康相关疾病识别的机器学习方法综述

Muhammad Yaseen Ayub¹,*, Farman Ali Khan¹, Syeda Zillay Nain Zukhraf² and Muhammad Hamza Akhlaq³

¹ 巴基斯坦伊斯兰堡 COMSATS 大学阿托克校区

² 塞浦路斯尼科西亚塞浦路斯大学电气与计算机工程系卓越研究与创新中心 KIOS

³ 巴基斯坦伊斯兰堡阿里格尔穆斯林大学开放大学

Abstract: 医学领域是人类历史上最受尊敬和最古老的职业之一。它对人类生活有直接影响。本章的主要目的是介绍先进的计算机科学技术，如机器学习在疾病检测过程中的应用。本章还讨论了在疾病检测过程中使用的不同机器学习算法。它还指出哪些算法具有更好的准确性。本章列出了检测各种危及生命疾病的主要和最常用的机器学习库。最后，对未来可用于疾病检测和病毒性疾病控制的技术趋势进行了讨论。

Keywords: 疾病检测, IoMT, 机器学习, IoMT 中的机器学习.

## INTRODUCTION

目前，计算技术几乎应用于生活的各个领域。医疗领域被认为是其中之一。在过去几年中，该领域进行了大量研究，利用机器学习方法尽早识别和治疗疾病。由于机器学习可以有效地执行人类认知功能，因此它成为疾病检测和治疗的更合适方法。最近，已进行了大量研究来开发机器学习中的专业方法，这些方法可以在检测各种疾病时具有高度准确性。然而，由于环境高度异构，我们仍然难以检测和诊断多种危及生命的疾病 [1]。如果在早期阶段检测到，多种危及生命的疾病是可以治疗的，如图 (1) 所示。因此，疾病的早期检测至关重要。

![](img/12e321fe66dd89993b17a8d73b64bd0c_157_0.png)

Fig. (1). 早期检测可以挽救人们免受致命疾病的侵害。

在过去几十年中，人们在开发能够执行人类认知任务的机器学习算法方面进行了大量研究。医疗领域从中受益匪浅；研究人员开发了机器学习模型，可以准确检测或预测肿瘤、囊肿、肺炎等疾病。他们使用 MRI 和 CT 扫描 X 射线图像结合计算机视觉技术在非常早期阶段检测或预测高风险疾病。机器学习算法还可作用于通过不同类型传感器获得的数值和布尔值 [2]。通过使用机器学习，计算机可以模仿人类认知行为并识别不同模式。然后计算机可以有效地检测这些模式中的任何异常并分类患者是否患有特定疾病。机器学习有两种主要方法：监督学习和无监督学习（这两种方法的混合体半监督学习也存在）。图 (2) 显示了不同类型机器学习技术的图形表示。

### Supervised Learning

监督机器学习在训练阶段提供标记数据集。模型根据训练期间提供的示例学习将输入映射到输出。监督学习的例子是分类和逻辑回归。分类算法用于根据对测试数据进行的学习分配不同的标签。例如，分类算法可以不同地对狗和猫进行分类。有各种分类算法，如 *Naïve Bayes*、*KNN*、*Decision Tree*、*Support Vector Machines* 等 [3]。

回归算法用于估计因变量和自变量之间的关系。它们用于预测数值。例如，许多公司使用线性回归模型来预测成本、利润、损失等。有几种类型的回归模型：线性回归、逻辑回归、岭回归、多项式回归等 [4]。

### Unsupervised Learning

无监督学习是一种学习类型，计算机不提供标记数据集。相反，计算机自行找到不同的模式。它基于模式识别，而不像监督学习那样提供任何目标属性。它在数据中发现隐藏的模式和见解。当我们没有用于训练的标记数据并且想要获得该数据的有用见解和模式时，可以使用它。无监督学习的例子是聚类，其中模型根据相似性对数据进行分组。有不同类型的聚类算法，如 *Partition based clustering*、*Fuzzy clustering algorithms*、*Model-based clustering algorithms*、*Density-based Clustering Algorithms*、*K-Means Clustering* 等 [5]。

![](img/12e321fe66dd89993b17a8d73b64bd0c_158_0.png)

Fig. (2). 不同机器学习算法及其用途。

本论文章节组织如下，文献研究中的后续部分介绍了各种危及生命疾病的详细信息。文献研究后跟一个讨论用于疾病检测的各种算法的章节。它列出了用于特定疾病检测的算法。随后是一个展示用于疾病检测的各种不同工具和库的章节。最后一节提供了结论和疾病检测的未来趋势。

## MOTIVATION

医学科学直接影响生命。随着人类人口以爆炸性速度增长，我们面临着资源限制的关键问题。为了使疾病检测变得容易、快速和经济实惠，我们需要在当前医疗保健系统中采用最新的人工智能和机器学习算法。最近的研究表明，机器学习算法可以快速准确地检测疾病。一些高死亡率疾病，如心脏相关疾病，需要早期诊断 [6]。

## LITERATURE STUDY

在过去二十年中，人们在调整现有算法以适用于医疗保健环境以及开发专门用于不同类型疾病特征提取和预测的新算法方面做了大量工作。研究表明，使用机器学习技术可以检测到各种疾病，例如脑肿瘤、心血管疾病、肺癌、肝功能、血液癌等。

根据使用的方法，疾病检测分为两组。一些疾病可以通过图像数据如 X 射线图像、CT 扫描、超声、MRI 扫描等更好地、更容易地检测到，而一些疾病不能通过图像数据很容易检测到；对于它们，我们使用特定传感器，然后为我们提供数值数据，然后将这些数据输入计算机系统进行分析和检测任何异常。有时也会使用两种技术的混合组合来检测某些疾病。图 (3) 显示了基于机器学习的系统的工作原理。基于机器学习的系统需要将输入样本传递给人工智能或机器学习系统，后者对其进行分析并检测任何异常，然后给出输出。

### Heart Diseases Detection

根据世界卫生组织，心脏相关问题是全球每年数百万人死亡的主要死因 [7]。研究人员已在心脏相关异常检测上使用了各种机器学习算法，例如 ANN SVM Logistic Regression、kNN、Classification Tree Naïve Bayes 等。
