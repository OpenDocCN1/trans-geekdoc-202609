# R 机器学习使用指南

致我的父母
*Shri Sanjay Kumar Singh and Smt. Tara Singh*
和
我的另一半
*Ranjita Gupta*.
—Kumar Rahul

致那位说
*“你自己，和宇宙中的任何人一样，  
值得你的爱和关怀”*。
—U. Dinesh Kumar

## 前言

*接受赞美和批评*。
*花儿的成长需要阳光和雨水*。
—禅语

人工智能（AI）已成为一个决定性的专业领域，在各个行业领域都有应用。机器学习（ML）是人工智能的一个子集，是用于解决多种分析问题的算法重要集合。AI 和 ML 是工程、科学和管理领域每位毕业生为职业发展所需的重要技能。航空航天、电子商务、银行和金融、医疗保健、制造业和零售等各行业的公司正在计划构建和提供基于 AI 的解决方案以保持竞争力。这些公司需要大量 AI 和 ML 领域的专家来构建产品和解决方案。根据国际数据公司（IDC），2021 年全球人工智能市场收入为 3275 亿美元。该市场预计到 2024 年将突破 5000 亿美元。¹ 根据 Zita（2021 年），数据科学职位增长了 650%。²

我们多年来一直在印度管理学院班加罗尔为 MBA 学生以及印度多家领先企业教授商业分析与机器学习。本书汇集了我们在企业和学术界从事多个 ML 项目超过 20 年的经验，以及我们使 ML 概念对学生和从业者更简单的承诺。

本书的目的是讨论使用 R 作为统计计算软件的 ML 模型开发。R 是众多组织用于分析各种数据并构建统计和机器学习模型的流行语言之一。许多大学和机构已开设商业分析的本科和研究生课程，其中核心课程之一是数据科学和机器学习的技能开发。尽管数据科学和机器学习在学术界和工业界蓬勃发展，但实用、结构化且高质量的内容仍然匮乏。如果我们使用机器学习技术解决现实生活中的商业问题，机器学习的复杂性将成倍增加。本书旨在创建结构化且高质量的内容，将一些数据科学概念应用于实际的商业用例。这是一本从业者书籍，学生和行业专业人士均可使用它来理解和掌握使用 R 进行机器学习的技能。本书中涵盖的概念和示例将帮助中级和高级用户加强对数据准备、特征工程和算法的了解，以及将算法应用于现实生活商业问题的应用。尽管经验丰富的从业者可以单独阅读各章，但每章都建立在前几章所涵盖的概念之上。数据科学领域的初学者如果在每章中注意细节，并愿意花时间理解商业用例的细微差别、数据科学概念以及 R 中函数和包的详细理解，将会受益。

为了更好地理解，我们从《Business Analytics: The Science of Data-Driven Decision Making》一书中复现了许多概念和示例（由 U. Dinesh Kumar 编著，Wiley 于 2017 年出版）。我们建议读者与本书合著者 U. Dinesh Kumar 的这本书一起阅读。

各章中使用的几乎所有数据集均来自我们在 IIMB 进行的咨询工作。所用数据集的详细信息可通过注册获得：https://www.wileyindia.com/Instructor_Manuals/Register/login.php

各章中的练习问题可能包含公开可用的数据集。在认为必要时，我们已承认用于解释数据科学概念的数据来源。我们感谢数据集的原始创建者。

### Features of the Book
为了使学习更有效，本书融入了多个特色。

#### Learning Objectives
学习目标提供了关键要点和本章将讨论的关键概念的总结。

![](img/pagex-01.png)

#### Important Concepts
此功能指出额外的见解以便更好地理解，并为读者注意的其他重要事实。它还提供了对所讨论概念的清晰理解，以使读者思考它。

![](img/pagex-02.png)

#### Useful Tip
为了加强概念理解，此功能旨在帮助读者推断本章所述概念的一般思想。

![](img/pagex-03.png)

#### Tables



根据表中提供的信息，读者可以使用提供的代码加载数据。

![](img/pagexi-01.png)

## RStudio 控制台

RStudio 是一个集成开发环境（IDE）。它可以直观地称为界面，并且与语言无关。用户可以使用 RStudio 通过 R 脚本、Python 脚本等分析数据。

![](img/pagexi-02.png)

## 练习

书中的练习涉及各种数据集，读者可以利用这些数据集回答问题。

![](img/pagexi-03.png)

### 补充材料

#### 教师资源

以下资源可应教师要求提供。如需注册，请登录 `https://www.wileyindia.com/Instructor_Manuals/Register/login.php`

• 教师解答手册

• PowerPoint 讲义幻灯片

• PDF 讲义幻灯片

• 数据集

• 代码

#### 学生资源

学生可通过 `https://www.wileyindia.com/student-resources` 访问以下资源

• 学生解答手册

• R 代码

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

¹Anon (2021)，“*IDC 预测 2021 年 AI 市场增长改善*”，可在 `https://www.idc.com/getdoc.jsp?containerId=prUS47482321` 获取，于 2021 年 9 月 4 日访问。

²Zita C (2021)，“*数据科学在 2021 年是否仍是一个新兴职业——考察数据科学行业的需求、供给和增长，以判断其在 2021 年是否仍是一个新兴职业*”，可在 `https://towardsdatascience.com/is-data-science-still-a-rising-career-in-2021-722281f7074c` 获取，于 2021 年 9 月 4 日访问。

## 作者简介

![](img/pagexiii-01.png)

Kumar Rahul 是印度理工学院 Jaipur 分校的工程学毕业生，也是印度管理学院班加罗尔分校（IIMB）的校友。目前，他正在印度管理学院 Kozhikode 分校攻读定量方法和运营管理博士学位。他的职业生涯在企业和学术领域已超过 16 年。Rahul 热衷于使用各种工具和技术探索数据。他曾与以下公司合作

Satyam Computers、Nokia Siemens 和 Deloitte Consulting，并曾是数家初创企业的创始成员。他是 AwesomeStats Consulting 的创始成员，该公司主要专注于数据科学领域培训和咨询。

在过去 7 多年里，他一直在 IIMB 的数据中心和分析实验室担任顾问。他为大型企业执行了多个分析项目。他在分析领域的少数任务包括（a）为卡纳塔克邦合作银行预测信用评分、为一家印度零售公司解决毁约/流失问题、为一家知名医疗设备制造商计算净推荐值以及为一家领先的美国汽车制造商解决设计问题；（b）为一家领先的汽车制造商预测销售和保修；以及（c）为一家总部位于美国的纸质消费品公司检测异常以及公司盈余管理中的欺诈。哈佛商业出版公司已将其中多个项目作为案例研究出版。

他在 IIMB 的教师发展项目以及短期和长期项目中教授分析学。他合作过的一些知名企业客户有 GE-Wipro、Cisco、Deloitte Consulting、United Health Group、HSBC、Flipkart、Fidelity Investments、General Motors、JP Morgan、TVS Motors、Raukten、Hudson Bay 等。

![](img/pagexiv-01.png)

Dr. U. Dinesh Kumar 是 IIM 班加罗尔决策科学教授兼 MBA（商业分析）主席。自 2020 年 1 月起，他也是 IIMB 卓越主席。Dr. Dinesh Kumar 拥有超过 25 年的教学和研究经验。他在领先的学术期刊上发表了 70 多篇研究论文。他基于印度和跨国组织的 40 个商业分析案例研究已在哈佛商业出版公司（HBP）案例门户上发表。其中九个案例研究是 HBP 的畅销书。他著有四本书；他之前的书 *商业分析：数据驱动决策的科学* 于 2017 年由 Wiley 出版，是亚马逊畅销书。Dr. Dinesh Kumar 已为 The Boston Consulting Group (India) Private Limited、Kimberly Clark、Cartesian Consulting、GE Healthcare、Group One Holding Pvt Ltd、Hindustan Aeronautics Limited、Qatar Airways、Mission Hospital、Manipal Hospitals、Scalene Works、SMNet Serve、TVS Motors、Wipro Limited、UNIBIC 和世界卫生组织等组织开展预测性和规范性分析咨询项目。

Dr. Dinesh Kumar 已为 Accenture、Aditya Birla Group、Ashok Leyland、Asian Paints、Bank of America、Blue Ocean Market Intelligence、Cisco、Fidelity、Hindustan Aeronautics Limited、Honeywell、Infosys、ITC Info Tech、Madhya Pradesh Agency for Promotion of Information Technology (MAPIT)、National Academy for Defence Production、Ocwen Financial Services、Sony 等多家公司开展分析培训项目。他开展企业分析培训项目，已在分析领域培训了超过 1000 名专业人士。他是印度分析学会（ASI）的创始主席。Dr. Dinesh Kumar 于 2003 年获得印度管理学院协会颁发的最佳青年教师奖。他于 2014 年被 *Analytics India Magazine* 列为印度十大分析学者之一。他于 2021 年被 *Analytics India Magazine* 授予数据科学杰出教授奖。

## 致谢

IIMB 为本书汇集思想所提供的环境再也没有比它更有利和充满活力的了。与来自学术界和工业界最聪明的头脑互动的机会促进了思考，最终将数十年的咨询工作编织成一本书。

没有 IIMB 同事和朋友的支持与鼓励，本书就不可能完成。我们在此过程中感谢 Aayushi Kalra、Abirami B、Gowri K P、Naveen Kumar Bhansali、Purvi Tiwary、Pooja Balasubramanya、Sangeetha A、Satyabala Hariharan、Shailaja Grover、Sharada Sringeswara、Sumithra G 和 Sunil S 的帮助。我们感谢 Kavita Kumar 和 Kaushik 在校对和编辑本书方面的努力。最后但同样重要的是，特别感谢 Manaranjan Pradhan 在撰写本书过程中提供的宝贵指导。

我们谨向 Meenakshi Sehrawat（Wiley India 副出版人）对本书的优质贡献表示感谢。特别感谢 Rupnarayan Das（Wiley India 开发编辑）对本书整体顺利出版的贡献。

**Kumar Rahul**

**U. Dinesh Kumar**

# 机器学习与 R

## 1

*没有任何事物完全孤立存在。一切都与其它事物相互关联*。

**——佛陀**

### 学习目标

阅读本章后，你将能够：

• 理解机器学习的概念和各种机器学习算法。

• 理解机器学习算法如何在现实世界中用于解决问题。

• 了解为什么 R 编程语言被广泛采用作为构建机器学习模型的平台？

• 学习如何开始设置 R、RStudio 和/或 Anaconda 平台。学习 R 语言的基本特性以开始机器学习任务。

• 了解 R 中的关键库及其在数据分析中的应用。

## 1.1 | 分析与机器学习简介

分析是一组用于从数据中创造价值的技术和工具。技术包括人工智能（AI）、机器学习（ML）、统计学习（SL）和深度学习（DL）算法等概念，其定义如下：



## 定义

### 人工智能
表现出类人智能的算法。

### 机器学习
AI 的子集，可学习执行预测和分类等任务，并随着额外数据和/或模型而提升性能。

### 统计学习
用于通过统计推断解决问题的算法。

### 深度学习
机器学习的子集，模仿人类大脑的运作来解决问题。

AI、ML 和 DL 之间的关系可视化如下图所示 图 1.1。这种结构并非分析领域所有人都接受。有一种观点认为 AI 和 ML 是不同的（即 ML 不是 AI 的子集），两者存在一定的重叠。关键点在于它们都是算法，而算法不过是用于解决商业和社会问题的指令集。本书的重点在于机器学习算法以及使用 `R` 平台为 ML 问题生成解决方案。

![](img/page2-01.png)

机器学习是一组算法，能够利用数据有效学习执行预测、预测和分类等任务。学习是通过额外数据和/或额外模型实现的。当算法在执行任务时能够在性能指标上有所改进时，可称为学习算法，例如欺诈和客户流失等分类的准确率。在接下来的几节中，我们将讨论各种机器学习算法以及使用 ML 算法解决的一系列问题。

机器学习算法可分为以下四类（Kumar, 2017）：

### 1. 监督学习算法
这些算法需要同时知道结果变量（因变量）和特征（自变量或输入变量）的知识（或值）。算法通过定义损失函数进行学习（即估计模型参数或特征权重的值），该损失函数通常是使用 ML 预测值与结果变量实际值之间差异的函数。线性回归、逻辑回归和判别分析等算法都是监督学习算法的例子。在多元线性回归的情况下，回归参数是通过最小化残差平方和估计的，其公式为 ![](img/pageIn_ch1-01.png) 其中 `y[i]` 是结果变量的实际值，而 ![](img/pageIn_ch1-02.png) 是结果变量的预测值。预测值可以是数据中特征（自变量）的线性或非线性函数。预测是通过（估计特征权重）并利用结果变量的实际值知识实现的，因此称为监督学习算法。也就是说，监督是通过训练数据中结果变量值的知识实现的。

### 2. 无监督学习算法
这些是一组算法，它们在数据集中没有结果变量的知识。算法必须找到结果变量的可能值。聚类和主成分分析等算法是无监督学习算法的例子。由于训练数据中结果变量的值未知，因此无法利用该知识进行监督。

### 3. 强化学习算法
在许多数据集中，输入变量和输出变量都可能存在不确定性。考虑各种文本编辑器中的拼写检查情况。如果某人在 Microsoft Word 中输入 ‘buutiful’，拼写检查会立即将其识别为拼写错误，并给出 ‘beautiful’、‘bountiful’ 和 ‘dutiful’ 等选项。预测不是单一值，而是一组值，其中任何一个都可能是正确的词（用户想要使用的词）。拼写检查和用于预测人们在智能手机上发送消息时可能使用的下一个词的词预测是强化学习算法的良好例子，其中输入和输出值都存在不确定性。强化学习算法的另一种定义是处理用户必须采取顺序行动（决策）以最大化累积奖励的上下文的算法。马尔可夫链和马尔可夫决策过程等技术是强化学习算法的例子。

### 4. 进化学习算法
进化算法模仿自然进化来解决问题。遗传算法和蚁群优化等技术属于此类。

在本书中，我们将讨论几种监督和无监督学习算法，并使用 `R` 开发模型。

## 1.2 为什么使用机器学习算法？
世界各地的组织使用投资回报率（ROI）、市场份额、客户保留率、销售增长、客户满意度等绩效指标来进行量化、监控、基准比较和改进。他们希望了解关键绩效指标（KPIs）与对 KPI 产生重大影响的因素之间的关联，以便有效管理。对 KPI 与因素之间关系的了解将为决策者提供适当的行动项目（Kumar, 2017）。机器学习算法可用于识别影响 KPI 的因素，这些因素可进一步用于决策和价值创造。亚马逊、苹果、Capital One、通用电气、谷歌、IBM、Facebook、宝洁及其同类公司使用 ML 算法创建新产品和解决方案。Marshall（2016）和 MacKenzie 等人（2013）报道，亚马逊的推荐系统使销售额增加了 35%。

典型的 ML 算法采用以下步骤（Pradhan and Kumar, 2019）：
1. 确定价值创造的问题或机会。
2. 确定数据源（主要和次要数据源）并创建数据湖（来自不同来源的原始数据集成集）。
3. 对数据进行预处理，以解决缺失和错误数据等问题。生成派生变量（特征工程）并准备数据用于 ML 模型构建。
4. 将数据集划分为训练数据集和验证数据集的子集。
5. 构建 ML 模型并使用验证数据中的模型性能识别最佳模型。
6. 实施解决方案/决策/开发产品。

## 1.3 机器学习算法开发框架
ML 算法开发框架可分为五个集成阶段：问题和机会识别、相关数据收集、数据预处理、ML 模型构建和模型部署。这些阶段的各种活动在 图 1.2 中表示（Kumar, 2017）。ML 项目的成功取决于数据的使用创新程度，而非机械使用 ML 工具。尽管存在客户细分、聚类、预测等常规 ML 项目，但高度成功的公司将创新与 ML 算法相结合。

在接下来的几节中，我们将讨论 `R` 作为 ML 模型开发的软件，`RStudio` 和 `Anaconda Navigator` 作为集成开发环境（IDE），它简化了脚本编写，以及如何开始使用 `R`。

## 1.4 R 简介



# R 简介

根据全面的 `R` 档案网络 (`CRAN`)，¹ `R` 是 `S` 编程语言的实现，结合了受 `Scheme` 启发的词法作用域语义 (`S` 语言)。 `S` 由 John Chambers 于 1976 年在贝尔实验室创建。 Ross Ihaka 和 Robert Gentleman 在新西兰奥克兰大学创建了 `R`。该项目构想于 1992 年，1995 年发布了初始版本，2000 年发布了稳定测试版 (Anon 2021)。 `R` 的名称部分基于前两位 `R` 作者的名字 (Robert Gentleman 和 Ross Ihaka)。

![](img/page4-01.png)

`R` 是一种编程语言和开源软件平台，专为统计计算和图形设计。它由 `R` 基金会支持，该基金会是由 `R` 核心开发团队成立的非营利组织。 `R` 语言在统计学家和机器学习专家中被广泛使用，用于开发基于机器学习算法的模型。作为一种解释型语言，`R` 允许使用函数进行模块化编程，并通过抽象细节为用户提供灵活性，如同典型的编程语言。²

`R` 拥有超过 12,000 个软件包，适用于几乎任何类型的统计或机器学习分析。强大的用户社区不断更新并创建新的库。

![](img/page5-01.png)

也有可用于构建深度学习模型的软件包。一些用于统计和机器学习的实用软件包在 **表 1.1** 中提及。

表 1.1 中的列表并非详尽无遗，读者可能会发现其他软件包对数据分析和构建机器学习模型有用。

## 1.5 | R 的流行度指数

The Importance of Being Earnest (`TIOBE`) 编程指数是衡量编程语言接受度的重要指标。 `TIOBE` 指数由荷兰埃因霍温的 `TIOBE` 公司创建和维护。根据 `TIOBE` (Anon, 2021)，“该指数是根据包含语言名称的查询的搜索引擎结果数量计算得出的（**表 1.2**）”。语言的流行度应结合 `TIOBE` 的免责声明来理解：

![](img/page6-01.png)

**1.** 根据 `TIOBE` 网站，`TIOBE` 指数“并非关于最佳编程语言或编写了最多代码行的语言”。

**2.** 根据 `TIOBE` 网站，“该指数涵盖了 Google、Google 博客、MSN、Yahoo!、Baidu、Wikipedia 和 YouTube 的搜索，并每月更新一次”（Anon, 2021）。

**3.** 该网站声称，搜索结果的网页数量可能反映了全球熟练工程师、学生、提供的课程数量以及该技能的就业市场。

从 表 1.2 可以看出，`Python` 是首选语言，排名第四，而 `R` 占据第 18 位。最新排名可在 `TIOBE` 网站上找到。³ 截至 2020 年 8 月的最新 `TIOBE` 指数排名将 `R` 排在第八位。⁴

排名差异也由于 `Python` 是一种通用编程语言，可用于其他软件开发任务，而 `R` 更适合作为统计计算和机器学习的语言 (Pradhan and Kumar, 2019)。

在热门网站上对 `SAS`、`Python` 和 `R` 等各种语言的职位数量进行搜索，⁵ 显示了 **图 1.3** 中的趋势。很明显，`R` 仍然是机器学习的第二佳语言，自 2016 年以来需求不断增长。

![](img/page7-01.png)

## 1.6 | R 安装 - 入门

在本节中，我们讨论 `R` 的安装以及如何开始使用 `R`。 `R` 是一个开源（免费）的统计分析和图形软件环境，可在 `UNIX`、`Windows` 和 `MacOS` 等操作系统和平台上使用。 `R` 提供了执行多种统计和机器学习模型的软件包。

综合 `R` 档案网络 (`CRAN`) 是一个存储库，托管 `R` 软件以及可能需要的数千个软件包，用于执行统计计算和图形。 `R` 主页的快照显示在 **图 1.4** 中。

![](img/page7-02.png)

要下载 `R`，请执行以下步骤：

**1.** 前往 [`https://cloud.r-project.org`](https://cloud.r-project.org)

**2.** 根据您机器的操作系统选择下载链接。

**3.** 点击下载的文件并按照步骤在您的机器上下载兼容版本。

直接在 `R` 软件上工作可能不是一个方便的选择，因此交互式开发环境 (`IDEs`) 为数据科学家提供了一个集成框架，以便更轻松地编写和调试代码。 `IDEs` 通常是语言无关的，这意味着同一个 `IDE` 可能让数据科学家能够使用 `IDE` 支持的任何语言编写代码。

## 1.7 | RStudio

`RStudio` 就是这样一个 `IDE`，它使 `R` 编程语言更易于使用。 `RStudio` 由控制台、用于直接代码执行的语法高亮编辑器以及图形、调试和工作区管理工具组成。当前版本的 `RStudio` (`Version 1.2.1335`) 使用户能够在同一个代码编辑器中编写 `R` 代码或 `Python` 代码或执行命令行脚本。

`RStudio` 提供两种选项：

**1.** **RStudio 桌面版：** 这是开源版，提供本地访问 `RStudio` 的系统。它具有语法高亮、代码补全和智能缩进。一些实用功能包括（*来源*: rstudio.com）：

• 能够直接从源编辑器执行 `R` 代码

• 易于使用的函数定义

• 使用项目管理多个工作目录的便利性

• 集成 `R` 帮助和文档

• 交互式且用户友好的调试器，可轻松诊断和修复错误

• 强大的软件包开发工具。这是独立用户进行统计计算的首选版本。

**2.** **RStudio 服务器版：** 它具有桌面版的所有功能。它是商业许可版本，适用于因内部政策无法使用开源许可版本的组织。它提供优先电子邮件支持，并在工作时间内八小时响应。

要下载 `RStudio`，请执行以下步骤：

**1.** 前往 [`https://www.rstudio.com/products/RStudio`](https://www.rstudio.com/products/RStudio)/。`RStudio` 主页的快照显示在 **图 1.5** 中。

**2.** 点击链接下载 `RStudio` 桌面版。

**3.** 在后续页面中，点击链接下载与您机器操作系统兼容的免费桌面版。

**4.** 点击下载的文件并按照步骤在您的机器上安装兼容版本。

请注意 `RStudio` 与 `R` 软件之间的版本兼容性。下载 `RStudio` 的第 3 步将说明在尝试下载 `RStudio` 之前需要预先安装哪个版本的 `R`。⁶

有关 `RStudio` 的更多信息可在 [`http://docs.rstudio.com/ide/server-pro`](http://docs.rstudio.com/ide/server-pro)/ 找到。

![](img/page9-01.png)

## 1.8 | 了解 RStudio IDE

**图 1.6** 突出了 `RStudio` 的四个主要模块：

**1.** 编辑器

**2.** 控制台

**3.** 环境管理器

![](img/page9-02.png)

**4.** 内容查看器

• 文件

• 图表

• 软件包

• 帮助

• 查看器



## 5. Editor
`Editor` 块用于编写 R 脚本。脚本可以保存在目录中，并在稍后打开执行。在编辑器中编写脚本并不意味着脚本会被执行。脚本编辑器上方的 `Run` 命令可用于执行 R 脚本。

## 6. Console
`Console` 用于查看已执行脚本的结果。执行脚本时出现的任何错误/警告也会出现在控制台中。它可用于编写少量 R 命令以查看即时结果，或进行基本的代码调试。

你可以在控制台上使用以下命令检查机器上安装的 R 版本：

![](img/page10-01.png)

本书中的代码是在 R 版本 3.5.1 上编写的。你可以使用控制台上的以下命令检查 R 会话中安装的特定包，例如 `stats` 的版本：

![](img/page10-02.png)

‘stats’ 包的版本与 R 软件相同。这意味着 `stats` 是一个基础包，并在安装 R 软件时一起安装。我们可以在控制台中使用 `sessionInfo()` 来获取有关基础包的信息。

![](img/page10-03.png)![](img/page11-01.png)

附加的基础包中的函数，即 `stats`、`graphics`、`grDevices`、`utils`、`datasets`、`methods`、`base`，可以在不显式加载这些包的情况下访问。这意味着用户无需显式给出命令 `library(stats)` 或一般 `library(<package-name>)` 即可使用这些包中定义的函数。

默认情况下，基础包已附加在搜索路径中，因此这些包中的函数可以在不调用这些包的情况下使用。我们可以在控制台输入 `search()` 来了解搜索路径中附加的包。

![](img/page11-02.png)

从 `search()` 函数的上述输出中，我们可以看到搜索路径中有 9 个元素。当用户在 RStudio 控制台输入函数名或命令时，R 会在全局命名空间中查找，即 `.GlobalEnv`。如果在 `.GlobalEnv` 中找不到该函数，则会依次扫描 `search()` 的元素，即 “`package::stats`”、“`package::graphics`” 等，以查找函数定义。如果在整个搜索空间中找不到该函数/命令，R 会显示错误消息。

RStudio 是一个集成开发环境（IDE）。它可以直观地称为界面，并且与语言无关。可以使用 RStudio 通过 R 脚本、Python 脚本等分析数据。

未在 R 会话中显式加载的包可以通过命令 `library(<package-name>)` 调用。该命令提示 R 将包加载到内存中并将其附加到 `search()` 路径中。在尝试调用它之前，请确保特定包已安装在你的机器上。

可以注意到，搜索路径不会列出通过命令 `sessionInfo()` 显示为通过命名空间加载（但未附加）的包。这意味着这些包已加载到内存中，但未附加到搜索路径。因此，R 软件和基础包可以访问这些包中定义的函数，但用户无法访问。

用户可以通过使用 `<pkg-name>::<function-name>` 来访问通过命名空间加载的包的函数。例如，如果我们想访问 `tools` 包的 `package_dependencies` 函数来检查包 `stats` 是否依赖于其他任何包：

![](img/page11-03.png)![](img/page12-01.png)

输出为 ‘NULL’，这意味着包 `stats` 不依赖于其他包。

## 1. Global environment
全局环境显示在进行任何数据分析项目时加载或创建到内存中的对象。这些对象可以称为全局变量，并在全局环境中列为 ‘Data‘、‘Functions‘ 或 ‘Values‘。

• Data 指的是在从任何文件格式读取数据文件时创建的对象。这些对象被创建为 `data.frame`、`data.table`、`tibble` 等。

• Functions 指的是作为用户定义函数创建的对象。

• Values 指的是原始以及复杂数据类型（如 `int`、`float`、`list`、`matrices` 等）的对象。

在使用 RStudio 编写和执行 R 脚本之前，必须安装 R 软件。

图 1.7 描述了全局环境，显示了 ‘Data’ 和 ‘Values’ 的快照。当我们将值赋给变量 ‘age‘ (`age = 20`) 或从系统读取逗号分隔值（csv）文件 (`read_csv = read.csv(<file-name>)`) 时，变量 `age`（列为 values）和 `read_csv`（列为 data）会在全局环境中创建。

R 中的环境也有更深层的含义。例如，`functions` 会创建自己的求值环境，函数调用期间创建的对象存储在局部环境中，而不是全局环境中。全局环境中的对象在整个 R 会话中都可用，而局部环境中的对象仅在函数创建的局部环境中可用。

### Content viewer
内容查看器有五个基本子标签页：

#### 1. Files
列出当前工作目录中的所有文件。默认情况下，当前工作目录是主目录。

#### 2. Plots
进行数据分析时生成的所有图表都可以在 plots 标签页中查看。

#### 3. Packages
R 中的包可以通过 packages 标签页安装。图 1.8 显示了通过在 ‘package’ 标签页中点击 install 按钮来安装包的一种方法。我们可以将包视为元数据或字典，或是一组预定义函数，其中包含调用函数时应执行步骤的信息。

例如，当我们输入 `read.csv` 时，R 解释器必须有某种方式理解该函数用于读取 csv 文件。包含此定义的包是 ‘`utils`‘。‘`utils`‘ 包有一组此类函数，可识别在编辑器中编写函数时应执行的逻辑操作。在 图 1.8 中，我们看到 package 标签页列出了机器上安装的所有包。当前会话中加载的包在相应框中会有复选标记。控制台中的 `installed.packages()` 命令也会返回 R 中安装的所有包。

![](img/page13-01.png)

#### 4. Help
任何函数或命令的帮助都可以通过 help 标签页查看。例如，要获取 `read.csv` 的帮助，请在控制台输入 `? read.csv`。结果将出现在 help 标签页中，如 图 1.9 所示。

#### 5. Viewer
RStudio 包含一个 Viewer 面板，可用于探索本地网页内容。例如，使用 `GoogleVis`、`htmlwidgets` 和 `rCharts` 等包生成的网页图形和图表，甚至使用 `Shiny`、`Rook` 或 `OpenCPU` 等包创建的本地 Web 应用程序。

![](img/page13-02.png)

## 1.9 | Anaconda
Anaconda 是另一个集成开发环境，可让数据科学家访问 Python 和 R 中最流行的数据科学发行版。实际上，Anaconda 是一个发行版管理系统和一个包含 1,000 多个开源包的集合。Anaconda 发行版使用 `conda` 来管理包、依赖项和环境。

根据 Conda 的官方网站，⁷ “它是一个开源的包管理与环境管理系统，可在 Windows、macOS 和 Linux 上运行。`Conda` 可快速安装、运行和更新包及其依赖项。`Conda` 可轻松在本地计算机上创建、保存、加载和切换环境。它最初为 Python 程序创建，但可打包和分发任何语言的软件”。Anaconda IDE 主要用于使用 Python 进行数据科学，提供了使用 R 执行数据分析所需的所有支持。`Conda` 是包管理器，而 Anaconda 是一组约一百个包的集合，包括 `Conda`、`Numpy`、`Scipy`、`Ipython notebook` 等。

Anaconda 提供了两种选项：



## Anaconda 发行版

此版本是开源版，提供访问 1000+ 数据科学包。此版本主要由独立用户用于进行统计计算。

## Anaconda 企业版

它是一个多用户协作平台，可一键部署模型、笔记本和仪表板，并提供 IT 团队所需的所有安全性和治理功能。它对组织和协作开发很有用。

## 下载 Anaconda

要下载 Anaconda，请执行以下任务：

1. 对于 Windows，请访问 [`docs.anaconda.com/anaconda/install/windows.html`](https://docs.anaconda.com/anaconda/install/windows.html)
2. 对于 MacOs，请访问 [`docs.anaconda.com/anaconda/install/mac-os`](https://docs.anaconda.com/anaconda/install/mac-os)
3. 对于 Linux，请访问 [`docs.anaconda.com/anaconda/install/linux`](https://docs.anaconda.com/anaconda/install/linux)

有关 Anaconda 的更多信息可在 [`docs.anaconda.com`](https://docs.anaconda.com) 找到

## Anaconda Navigator

在本节中，我们讨论 Anaconda Navigator 的各种功能。本节内容摘自 Anaconda 官方网站。Anaconda Navigator 官方网站⁹ 称，“它是一个桌面图形用户界面（GUI），包含在 Anaconda 发行版中，允许用户启动应用程序并轻松管理 conda 包、环境和频道，而无需使用命令行命令。它是 conda 包和环境管理器的 GUI”。Navigator 具有在 Anaconda Cloud 或本地 Anaconda 仓库中搜索包的能力。它适用于 Windows、macOS 和 Linux。

以下应用程序默认在 Anaconda Navigator 中可用：

1. Jupyter Lab
2. Jupyter Notebook
3. Orange App
4. QTConsole
5. Glueviz
6. Vscode
7. RStudio

以上所有应用程序都是 IDE。然而，本书将仅限于 RStudio 应用程序。成功安装 Anaconda 后，启动 Anaconda Navigator 并点击 RStudio 安装选项卡。这将安装一套集成工具，包括用于在 R 平台上工作的 R 核心包和笔记本。

Jupyter Notebook 是另一个流行的 IDE，如 R Studio，可用于编写和执行 R 脚本。安装 Anaconda 框架也会安装 Jupyter Notebook。

可以通过以下两种选项之一编写 R 代码：

1. 从 Anaconda Navigator 启动 RStudio IDE。这将打开 RStudio 桌面版，可用于编写 R 脚本。
2. 从 Anaconda Navigator 启动 Jupyter Notebook。Jupyter Notebook 是一个流行的系统，它将 R 和 Python 代码、描述性文本、模型输出、图表和交互式界面组合到一个可在 Web 浏览器中编辑和使用的单个笔记本文件中。

然而，要使用 Jupyter Notebook 进行 R 脚本编写，我们需要将现有的 R 内核指向 Jupyter Notebook IDE。为此，打开 R 控制台（或在 Mac 中通过终端打开 R）。输入以下命令：

1. 安装包 :- `IRkernel`: `install.packages('IRkernel')`
2. 调用包: - `library(IRkernel)`
3. 使 Jupyter Notebook 指向 R 内核: - `IRkernel::installspec()`
4. 打开 Jupyter Notebook，您可以使用 R 内核编写 R 脚本。

`installspec()` 有一个 ‘`USER`’ 参数，其默认路径用于在 Jupyter Notebook 中安装 `IRkernel`。如果 `IRkernel` 安装不成功，请更改路径选项。建议使用上述步骤安装和使用 Jupyter Notebook 中的 R。

`Rkernel` 也可以通过在 Anaconda 提示符/终端上使用命令 `conda install -c r r-irkernel`¹⁰ 来安装。此外，通过在终端上输入 conda 命令安装 R 包¹¹ 到当前环境：`conda install -c r package-name`。请注意，在命令 `conda install -c r package-name` 中，必须将 `package-name` 替换为实际的包名。例如，要安装包 `ggplot2`，命令应为 `conda install -c r ggplot2`。要搜索包，可以使用命令 `conda search -f EXACTNAME`。我们必须将单词 `EXACTNAME` 替换为所需的 R 包名称。许多 CRAN 包已被重建并作为 conda 包提供。根据官方网站¹²，“Anaconda 不提供整个 CRAN 仓库的构建，因此 CRAN 中有些包不可作为 conda 包使用。与逐个安装每个 R 语言包相比，可以使用 R Essentials 捆绑包安装约 100 个 R 编程语言最流行的科学包”。我们可以在终端上使用命令 `conda install -c r r-essentials` 安装 R Essentials 捆绑包。Anaconda Navigator¹³ 文档提供了有关管理包以及创建虚拟环境的许多详细信息。¹⁴

也可以单独安装 Jupyter Notebook，而无需安装 Anaconda，并将其与 R 软件链接以编写和执行 R 脚本。

## 摘要

• R 是一个用于统计计算的强大应用程序。使用 IDE 可使在 R 平台上工作变得简单。RStudio 和 Anaconda 是众多可用 IDE 中的两个。在 RStudio 和 Anaconda 之间，工具的选择基于用户便利性。如果您不是开发熟练者，Anaconda 环境的使用起初可能会让人不知所措。RStudio 本身对不太懂技术的开发者来说友好且方便，但仍能提供无缝工作的全部功能。

• 本书各章节均使用 Jupyter Notebook 版本 5.6.0 作为 IDE 编写。使用的 Anaconda Navigator 版本为 1.8.7，R 软件版本为 3.5.1 和 4.0.3。我们可以在 RStudio IDE 中使用相同的脚本并执行它们。

## 参考书目

1. Anaconda Inc (2020), “*端到端数据科学平台*”, Anaconda Inc, 网址： [`www.anaconda.com/products/enterprise`](https://www.anaconda.com/products/enterprise), 访问于 2020 年 11 月 19 日。
2. Anon (2021), “*R 概述*”, 网址： [`www.datasciencemadesimple.com/learn-r-what-is-r`](https://www.datasciencemadesimple.com/learn-r-what-is-r)/, 访问于 2021 年 9 月 11 日。
3. Anon (2021), “*TIOBE 指数*” 网址： [`www.tiobe.com/tiobe-index`](https://www.tiobe.com/tiobe-index), 访问于 2021 年 1 月 26 日。
4. Anon (2020), “*R 文档*”, 网址： [`www.rdocumentation.org`](https://www.rdocumentation.org), 访问于 2020 年 11 月 19 日。
5. Anon (2020), “*综合 R 档案网络*”, 出版者：维也纳经济大学统计与数学研究所, 网址： [`cran.r-project.org`](https://cran.r-project.org), 访问于 2020 年 11 月 19 日。
6. Anon (2021), “*R 概述*”, 网址： [`sceweb.sce.uhcl.edu/helm/WEBPAGE-R/my_files/TableContents/Module-2/module2page.hml`](https://sceweb.sce.uhcl.edu/helm/WEBPAGE-R/my_files/TableContents/Module-2/module2page.hml), 访问于 2021 年 1 月 15 日。
7. Anon (2014), “*2014 DC 地区技术统计*”, 网址： [`agileengine.com/2014-dc-area-tech-stats`](https://agileengine.com/2014-dc-area-tech-stats), 访问于 2021 年 1 月 15 日。
8. Anon (2016), “*Swift 的现状*”, 网址： [`www.thomashanning.com/the-current-state-of-swift`](http://www.thomashanning.com/the-current-state-of-swift), 访问于 2021 年 1 月 15 日。
9. Chollet F 和 Allair J J (2018), “*用 R 进行深度学习*”, Manning Publications, United Kingdom。
10. Kumar U D (2017), “*商业分析 - 数据驱动决策的科学*”, Wiley, New Delhi。





**11.** Finkler S A, Smith D L and Thad D (2018), “*公共、健康和非营利组织的财务管理*” Sage, Los Angeles.

**12.** Pradhan M and Kumar U D (2019), “*使用 Python 进行机器学习*”, Wiley, New Delhi.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

¹[`www.r-project.org`](https://www.r-project.org)/

²[`cran.r-project.org/doc/FAQ/R-FAQ.html#What-is-R\_003f`](https://cran.r-project.org/doc/FAQ/R-FAQ.html#What-is-R_003f)

³[`www.tiobe.com/tiobe-index`](https://www.tiobe.com/tiobe-index)/

⁴[`www.tiobe.com/tiobe-index/r`](https://www.tiobe.com/tiobe-index/r)/

⁵[`blog.revolutionanalytics.com/2017/02/job-trends-for-r-and-python.html`](https://blog.revolutionanalytics.com/2017/02/job-trends-for-r-and-python.html)

⁶如果您正在安装 *RStudio Desktop 1.1.442*，它会提示‘RStudio 需要 R 3.0.1+’，该版本应已安装在桌面上。版本不兼容会影响某些统计计算或软件包的安装。

⁷[`conda.io/en/latest`](https://conda.io/en/latest)/

⁸[`www.anaconda.com/enterprise`](https://www.anaconda.com/enterprise)/

⁹[`docs.anaconda.com/anaconda/navigator/user-guide`](https://docs.anaconda.com/anaconda/navigator/user-guide)

¹⁰[`anaconda.org/r/r-irkernel`](https://anaconda.org/r/r-irkernel)

¹¹[`repo.continuum.io/pkgs/r`](http://repo.continuum.io/pkgs/r)/

¹²来源：[`docs.anaconda.com/anaconda/packages/r-language-pkg-docs`](https://docs.anaconda.com/anaconda/packages/r-language-pkg-docs)/

¹³[`docs.anaconda.com/anaconda/navigator`](https://docs.anaconda.com/anaconda/navigator)/

¹⁴[`docs.anaconda.com/anaconda/navigator/tutorials`](https://docs.anaconda.com/anaconda/navigator/tutorials)/

# 2 数据预处理

*你越安静，你听到的就越多*。

**—佛陀**

## 学习目标

阅读本章后，您将能够：

• 理解整洁数据的概念及其在数据准备和可视化中的用途。

• 理解 `data.table` 的概念以及在 R 中使用 `data.table`。

• 学习使用 `data.table` 加载结构化数据，并使用 `data.table` 包的语法执行数据查询。

• 学习数据准备活动，例如创建新特征、子集化、过滤、分组、排序和数据集连接。

• 理解为什么在 R 中，`data.table` 在数百万条记录上比基本的 `data.frame` 提供更快的加载和数据查询时间。

• 学习使用 `DT`（Data Tables）包将 `data.table` 和 `data.frame` 渲染为 HTML 表格。

## 2.1 使用 R 中 `data.frame` 进行数据预处理和描述性分析

数据预处理是机器学习（ML）项目生命周期中耗时的一项活动。据轶事证据表明，高达 80% 的 ML 项目时间花费在数据准备上。数据预处理涉及处理来自不同来源的数据集成以及处理缺失信息、不正确数据等活动。除了预测性和规范性之外，描述性分析构成了分析的第三个组成部分。它是描述过去数据并捕捉给定上下文中“发生了什么”的科学。描述性分析的主要目标是通过数据汇总、基本统计指标和可视化来理解数据。

数据科学家在大多数数据分析活动中处理结构化数据，并熟悉标准查询语言（`SQL`）表的概念。SQL 表以行和列表示数据，使查询和对数据执行操作变得方便。类似的数据呈现结构在 R 中通过 `data.frame` 得到支持，可将其想象为内存中的 SQL 表，即表格格式的数据。

![](img/page18-01.png)

`data.frame` 是一种非常高效的二维数据结构，如 **图 2.1** 所示。Data.frames 在结构上是扁平的，并按可索引或命名的行和列排列。

`data.frame` 在满足以下三个相互关联的规则时称为整洁 `data.frame`：

**1.** 每个变量都有自己的列。

**2.** 每个观察值（或记录）都有自己的行。

**3.** 每个值都有自己的单元格。

似乎很明显，每个 `data.frame` 的结构都会遵循上述三点。然而，并非总是如此。变量可能分布在多个列中，或者观察值可能分布在多行中。**表 2.1** 显示了一个不遵循整洁 `data.frame` 条件 的 `data.frame`。

**表 2.1** 中的数据表示 2000 年至 2018 年公司（ABC、XYZ 和 DEF）的流失率。这不是一个整洁的 `data.frame`，因为变量年份分布在多个列中。**表 2.1** 中数据的整洁 `data.frame` 显示在 **表 2.2** 中。

当 `data.frame` 满足上述三个条件时，执行下游任务（例如过滤、聚合、分组和绘制数据等）变得容易。为了演示 `data.frame` 的使用，我们将使用 IPL 数据集（在下一节中描述）加载数据并执行描述性分析，使用 `data.table` 和 `ggplot2` 来促进数据整理。

## 2.2 IPL 数据集描述

印度 Premier League（IPL）是由 BCCI（印度板球控制委员会）于 2008 年创办的职业 Twenty20 板球联赛，拥有八支由世界各地球员组成的特许经营球队。首次 IPL 拍卖于 2008 年举行，球队拥有权为期 10 年，底价为 5000 万美元。特许经营球队通过每年举行的英式拍卖获得球员。然而，存在多项规则，其中包括每支特许经营球队购买球员可花费的资金上限。

![](img/page18-02.png)![](img/page19-01.png)

球员的表现可以通过多种指标衡量。虽然 IPL 是一项 20 局比赛的锦标赛，但其他形式的比赛（如测试赛和一日国际赛）的表现也可能影响定价。一些球员拥有出色的测试赛记录，但他们的 Twenty20 记录并不那么令人印象深刻。该数据集包含 130 名球员的表现，通过各种绩效指标衡量，例如击球打击率、投球经济率等。特征列表提供在 **表 2.3** 中（数据文件名：`ipl.csv`）。

## 2.3 将数据集加载到 R

名为 `utils` 的基础包具有以下文件格式的选项，可将数据作为 `data.frame` 读取：

**1.** `read.table()` - 读取表格格式的文件。它也可以用于从统一资源定位符（URL）读取文件。

**2.** `read.csv()` - `read.table()` 上的包装函数，可读取 ‘ 分隔文件

**3.** `read.csv2()` - `read.table()` 上的包装函数，可读取 ; 分隔文件

**4.** `read.delim()` - `read.table()` 上的包装函数，可读取 \\t 分隔文件

**5.** `read.ftable()` - 读取“扁平”列联表

**6.** `read.fwf()` - 读取定宽格式（fwf）文件。它也可以用于从 URL 读取 fwf 文件




函数 `read.table()` 及其所有相关函数如 `read.csv()` 等，会将所有列读取为字符列，并通过函数 `type.convert()` 将列转换为适当的数据类型（`logical`、`numeric`、`integer`、`complex` 或 `factor`）。将数值列的每个不同值存储为字符字符串，相比将其存储为整数可能占用多达 14 倍的内存空间。因此，在尝试读取大型数据文件时，所有这些函数都可能非常缓慢。通过在 `read.table()` 中设置以下某些参数，可以更高效地处理大型数据集：

### 表 2.3 | IPL 数据特征描述

| 数据代码 || 描述 |

| --- | --- |

| AGE || 球员在拍卖时的年龄，分为三个类别：类别 1（L25）包括 25 岁以下的球员；2 表示年龄在 25 至 35 岁之间（B25-35）；类别 3 为 35 岁及以上的球员（A35） |

| --- | --- |

| RUNS S || 球员得分的跑分数量 |

| RUNS C || 球员失分的跑分数量 |

| HS || IPL 中击球手取得的最高得分 |

| AVE B || IPL 中击球手平均得分 |

| AVE BL || IPL 中投球平均分（失分数/取得 wickets 数） |

| SR B || IPL 中击球打击率（得分数与面对球数之比） |

| SR BL || IPL 中投球打击率（投球数与取得 wickets 数之比） |

| SIXERS || 球员在 IPL 中击出的六分球数量 |

| WKTS || 球员在 IPL 中取得的 wickets 数量 |

| ECON || 投球手经济率（每局投球手失分数）在 IPL 中 |

| CAPTAINCY EXP || 曾担任 T20 或国家队的队长 |

| ODI SR B || 一日国际赛中的击球打击率 |

| ODI SR BL || 一日国际赛中的投球打击率 |

| ODI RUNS S || 一日国际赛中得分 |

| ODI WKTS || 一日国际赛中取得的 wickets |

| T RUNS S || 测试赛中得分 |

| T WKTS || 测试赛中取得的 wickets |

| PLAYER SKILL || 球员主要技能（击球手、投球手或全能选手） |

| COUNTRY || 球员原籍国（AUS：澳大利亚；IND：印度；PAK：巴基斯坦；SA：南非；SL：斯里兰卡；NZ：新西兰；WI：西印度群岛；OTH：其他国家） |

| YEAR A || IPL 拍卖年份 |

| IPL TEAM || 球员在 IPL 中效力过的球队（CSK：金奈超级国王；DC：迪坎要塞；DD：德里恶魔；KXI：旁遮普国王 XI；KKR：加尔各答骑士骑兵；MI：孟买印度人；PWI：浦那勇士印度；RR：拉贾斯坦皇家；RCB：班加罗尔皇家挑战者）。“+”号用于表示球员效力过多个球队。例如，CSK+ 表示该球员曾效力 CSK 以及一个或多个其他球队。 |

**1.** `colClasses`: 指定每列的类别。可能的值为 `logical`、`integer`、`numeric`、`complex`、`character`、`raw`、`factor`、`date`。

**2.** `nrows`: 数据中行的估计值。轻微高估可能有用。

**3.** `comment.char`: 此参数的默认值是 `#`。这意味着在读取文件时，如果函数在任何行中遇到 `#`，整行将被丢弃。将默认值从 `#` 改为 `""` 将使文件读取更快。

扩展包 `data.table`，首次发布于 2006 年¹，已成为快速高效处理大型数据集的流行选择。`data.table` 中的 `fread()` 广泛用于从 csv 或 txt 文件读取数据。`fread()` 相对于 `utils` 包中的传统 `read.table()` 的优势在于它提供快速且内存高效的文件读取操作。`fread()` 通过自动检测 `colClasses` 和 `nrows` 参数来实现这一点，从而避免了先将值读取为字符再转换为正确数据类型的需求。为了说明处理大型数据集的效率，我们使用 `utils` 包中的 `read.csv()` 函数测试了 `data.table` `fread()` 函数的读取操作。我们使用了西雅图公共图书馆的馆藏数据²，其维度为 29,6,28,772 * 13（约 3000 万条观测值，跨 13 个变量；9GB 大小）。使用 `fread()` 加载该数据集的读取时间约为 120 秒，而在相同机器配置下，使用 `read.csv()` 加载相同数据大约需要 400 秒。

`data.table` 包还允许高效实现写入、聚合、更新、等值连接、非等值连接等操作，`data.table` 本质上是一个 `data.frame`，因此与期望 `data.frame` 的 R 函数和包兼容。我们可以使用 `setDT()` 和 `as.data.table()` 将 `data.frames` 和列表转换为 `data.table`，用于其他对象。

数据表对象在直观上与使用原生 R（使用 `base` 包）或使用 Python（使用 `pandas` 包）脚本创建的数据框对象相同。然而，与数据框相比，数据表在处理和查询大型数据集方面非常高效。

### 2.3.1 安装用于数据整理的包

让我们先使用 `fread()` 加载 IPL 数据集，然后使用包 `ggplot2` 执行基本的数据整理操作和可视化。但是，在使用 `data.table` 和 `ggplot2` 包的函数之前，请确保该包已安装在您的机器上。`install_packages` 是一个用户定义的函数，可用于安装 `data.table` 和 `ggplot2`。

![](img/page21-01.png)

请注意，函数的用法已通过在函数定义时立即在双引号内插入注释来描述。然而，像注释或帮助这样的元数据也可以使用上面使用的 `attr()` 函数编写。其优点是这些元数据如果需要可以使用 `attribute(<function-name>)` 函数突出显示，例如，`attributes(install_packages)`。下面的代码行将使用上面定义的函数并安装所需的包。

![](img/page21-02.png)

### 2.3.2 调用包

现在我们准备好使用下面的代码将包加载到内存中：

![](img/page21-03.png)

`data.table` 中的 `fread()` 可用于在 R 平台中加载文件。`fread()` 的前四个参数可用于读取不同类型的文件。我们已插入了这些四个参数的描述（Chomsky and Lifshitz, 2021），摘自 `fread()` 的帮助部分：

- `input`: 使用单个字符字符串。值会被检查并分配给 `file=`（如果没有 `\n`）、`text=`（如果至少有一个 `\n`）或 `cmd=`（如果没有 `\n`、至少有一个空格，并且不是文件名）。
- `file`: 工作目录中的文件名，或通过 `path.expand` 的文件路径，或以 http://、file:// 等开头的 URL。
- `text`: 输入数据本身作为字符向量，例如由 `readLines()` 返回。
- `cmd`: 预处理文件的 shell 命令；例如 `fread(cmd=paste("grep",word,"filename"))`。

在同一调用中应且仅应使用 `input=`、`file=`、`text=` 或 `cmd=` 中的一个。虽然 `fread()` 函数内部的大多数参数/参数设置为默认值，但我们强调了四个可能需要更改默认设置的<|message|> 参数：

**1.** `na.strings`: 接受一个字符串向量，以表示应读取为 NA 的值。在下面的代码块中，单个空格和 #NA 应读取为“NA”。我们可以指定所有希望读取为 NA 的字符串。请注意，R 将 NA 视为缺失值，因此需要将数据集中所有不需要的值标记为 NA。

**2.** `stringsAsFactors`: 是否需要将字符列转换为因子，或简单地作为字符读取。默认设置为 FALSE。在处理数据框时，例如使用 `read.csv()` 函数，字符列默认读取为因子。



## 3. `data.table`
是否将读取文件后创建的变量视为 `data.table` 还是 `data.frame`。默认值为 `data.table`，并且会保持不变，因为此选项有助于将其同时视为 `data.table` 和 `data.frame`。

## 4. `logical01`
是否将包含 0 和 1 的列读取为逻辑数据类型还是整数数据类型。默认读取为整数。

我们可以通过在 R Studio 控制台输入 `?fread` 来阅读 `fread()` 的所有参数。

![](img/page22-01.png)

表 2.4 显示了数据的前五个观测值的快照。请注意，表 2.4 未显示数据集的所有特征，以保持数据的可读性。

![](img/page22-02.png)

## 有用提示 1

### Jupyter Notebook

如果我们使用 Jupyter Notebook，默认打印显示 60 行（前 30 行和后 30 行）和 20 列（前 10 列和后 10 列）。我们可以使用 R 的 `getOption("repr.matrix.max.rows")` 和 `getOption("repr. matrix.max.cols")` 函数来检查默认选项。我们也可以使用 `.Options` 或不带任何参数的 `options()` 来获取所有可能的默认值列表。

![](img/page23-01.png)

要显示所有行和列，我们可以通过 `repr.matrix.max.rows=Inf` 和 `repr.matrix.max.cols=Inf` 来更改设置。我们也可以传递我们希望打印的具体行数和列数，例如 `repr.matrix.max.rows=100` 和 `repr.matrix.max.cols=16`。

## 有用提示 2

### RStudio

如果我们使用 RStudio 运行上述代码，`data.table` 的默认打印为 120 行。如果数据集中记录数超过 120 行，则显示顶部的前 5 行和底部的后 5 行。

同样，我们也可以使用 R 的 `getOption()` 函数来检查默认选项。我们可以使用 `options()` 将这些参数设置为我们希望显示的值。

![](img/page23-02.png)

我们可以通过使用 `options()` 并传递我们想要更改设置的所需参数来修改 RStudio 中的默认选项。假设，如果我们想打印 `ipl_dt` 中的所有行，我们必须传递 `"data.table.print.nrows"` = 130。

## 2.4 | data.table 上的操作

使用 `data.table` 而非 `data.frame` 的优势在于可以在 `data.table` 内部进行多次查询，而 `data.frame` 仅便于对行进行子集化和选择列。`data.table` 的基本形式如图 图 2.2 所示：

![](img/page23-03.png)

在 图 2.2 中，`DT` 是使用 `fread()` 创建的变量的名称。在我们的例子中，我们将其命名为 `ipl_dt`。我们可以将 图 2.2 读作“取 `data.table` `DT`，按 `i` 选择行，然后选择列 `j` 或对列 `j` 执行某些操作并按其他列分组”。

可以通过在 RStudio 控制台使用 `?data.table` 查看 `data.table` 参数的完整描述。与 SQL 语句类似，`data.table` 中的列可以像变量一样引用。另外，请注意 R 中的索引从 1 开始而不是 0。

我们将使用 `data.table` 进行数据整理，以根据球员统计数据了解球队的构成。以下是根据表现排名的 IPL 2011 前四支球队：

1. CSK
2. MI
3. KKR
4. RCB

虽然我们可以分析全部八支球队的构成，但我们选择将范围限制在 IPL 2011 期间的前四名。

1. CSK 与 RCB 之间的资格赛 1 由 CSK 获胜。
2. MI 与 KKR 之间的淘汰赛由 MI 获胜。
3. RCB 与 MI 之间的资格赛 2 由 RCB 获胜。
4. CSK 与 RCB 之间的决赛由 CSK 获胜。

我们将分析这四支球队球员的过往表现以及他们在拍卖中的价格。请注意，该数据集反映的不是球员在 IPL 2011 中的表现，而是在之前的 T20、一天赛和测试赛中的表现。值得注意的是，该数据集包含可供拍卖并随后售出的球员。它不代表被其特许经营权保留的球员，因此未进入拍卖。在分析球队构成之前，我们将熟悉使用 `data.table` 的基本行和列操作。

一般来说，`data.table` 的语法可读作“有条件或无条件地选择行和/或列；对列执行某些计算并应用聚合操作，如基于其他列的分组”。

### 2.4.1 使用 R 的基本操作

我们将在 `ipl_dt` 上执行一些基本操作。让我们尝试打印前六条记录、后六条记录、`ipl_dt` 的数据类型和汇总统计信息。我们还将讨论如何重命名列、删除列和添加新特征。要获取前六条记录，我们可以写 `head(ipl_dt,6)`。表 2.5 显示了 `ipl_dt` 中前十个特征的顶部六个观测值。表 2.6 显示了 `ipl_dt` 中前十个特征的底部六个观测值。

![](img/page24-01.png)

结构 `str()` 显示数据集中每个特征的数据类型和前几个观测值。数据维度可以使用 `dim()` 获得。让我们看看 `ipl_dt` 的维度和其中一个特征的结构。

![](img/page24-02.png)![](img/page25-01.png)![](img/page25-02.png)

维度显示 `ipl_dt` 有 130 个观测值（记录）和 27 个特征（变量）。变量 `AGE` 的结构显示数据类型为 `int`，并打印 `AGE` 列的前 10 个观测值。

`summary()` 用于获取数据集中前 5 个特征的基本汇总。

![](img/page25-03.png)

表 2.7 显示了 `ipl_dt` 前五个特征的汇总统计信息：对于数值特征，我们得到以下汇总统计信息：

1. 数值特征的汇总包括：‘Min’、‘1^(st) Quartile’、‘Median’、‘Mean’、‘3^(rd) Quartile’ 和 ‘Max’。
2. 由于 `data.table` 的 ‘fread’ 方法将分类特征类型转换为 ‘Character column’，汇总统计信息仅包含观测计数（‘Length’）。

我们可以使用 `data.table` 包中的 `setnames()` 来重命名任何列。其优点是它通过引用更改名称，而无需复制整个数据集。我们将把 `RUNS_S` 重命名为 `PAST_RUNS_IPL`，并将 `WKTS` 重命名为 `PAST_WKT_IPL`。

![](img/page25-04.png)![](img/page26-01.png)

### 2.4.2 基本行子集操作

在 `data.table` 中，我们可以使用逻辑表达式、行号和 `order()` 创建行的子集。

例如，下面的代码片段创建了 表 2.8，其中我们可以看到 `ipl_dt` 的第五行和第四行以及前十个变量。

![](img/page26-02.png)

`ipl_dt[5:4,]` 也会产生上述结果，但包含所有变量。`ipl_dt[5:4,]` 中的逗号（`,`）是可选的。

下面的代码片段创建了 表 2.9，其中我们可以观察到除第 2:5 行外的所有行以及 `ipl_dt` 的前十个变量。

![](img/page26-03.png)

下面的代码片段也可以用来创建 表 2.9。

![](img/page26-04.png)

让我们按 `COUNTRY` 对数据集进行排序并显示前六条记录。以下代码可用于按国家/地区排列记录，结果显示在 表 2.10 中。

![](img/page26-05.png)![](img/page26-06.png)![](img/page26-07.png)![](img/page27-01.png)

在 `ipl_dt[order(COUNTRY, decreasing = TRUE)]` 中调用 `order` 函数并使用 `decreasing=TRUE` 将返回一个 `data.table`，其中国家按逆时序标记。



为了选择所有测试赛得分大于 5,000 的球员的行，我们可以使用下面提供的代码片段生成输出 **表 2.11**。

![](img/page27-02.png)

下面的代码片段选择所有测试赛得分大于 5,000 且测试赛 wickets 数超过 100 的行。如 **表 2.12** 所示，Jacques Kallis 是 IPL 2011 中唯一取得这一成就的球员。

![](img/page27-03.png)

### 2.4.3 基本列子集操作

在 `data.table` 中，可以轻松执行多个列操作。例如，下面的代码块将返回一列 (`PLAYING_ROLE`) 作为向量。

![](img/page27-04.png)![](img/page27-05.png)![](img/page27-06.png)

**表 2.13** | 来自 IPL 数据的比赛角色的前六个观测值

| ROLE |

| --- |

| Allrounder |

| --- |

| Bowler |

| Bowler |

| Bowler |

| Batsman |

| Batsman |

**表 2.13** 通过使用以下代码将上述结果显示为 `data.table`：

![](img/page28-01.png)

“.()“ 在上述代码中只是 `list` 的别名。这意味着我们可以在 `.()` 内命名列，并将列表命名为 ‘`ROLE`’，并使用 `head()` 显示前六行。如果列未命名，则默认会命名为 `V1`。

我们可以从 `data.table` 内部对列应用某些数学运算。假设我们想获得所有特许经营商花费的总金额。下面的代码片段将帮助我们获得该数字，为 $6.7 million。

![](img/page28-02.png)

**表 2.14** 给出了 IPL 中代表的国家列表以及每个国家球员的数量。

![](img/page28-03.png)

除印度外，澳大利亚、南非、斯里兰卡和巴基斯坦是 IPL 2011 中代表最多的前四个国家。

**表 2.15** 显示了 `data.table` 的前五行和前 10 个特征的快照。

![](img/page28-04.png)

**表 2.14** | 按国家统计的球员人数

| COUNTRY || Freq |

| --- | --- |

| AUS || 22 |

| --- | --- |

| BAN || 1 |

| ENG || 3 |

| IND || 53 |

| NZ || 7 |

| PAK || 9 |

| SA || 16 |

| SL || 12 |

| WI || 6 |

| ZIM || 1 |

![](img/page29-01.png)![](img/page29-02.png)

下面的代码可用于生成 **表 2.16**，它显示了数据集的前五行，其中包含 `PLAYER_NAME`、`AGE`、`COUNTRY` 和 `TEAM`：

![](img/page29-03.png)

让我们选择列 `PAST_IPL_WKTS`（在 IPL 中取得的 wickets）和列 `T_WKTS`（在测试赛中取得的 wickets），并计算一个新列 `TOTAL_WKTS`，它是 `PAST_IPL_WKTS` 和 `T_WKTS` 的总和。**表 2.17** 显示了下面代码片段的结果：

![](img/page29-04.png)

请注意，代码片段创建了一个新的 `data.table`，但并未在 `ipl_dt` 中插入新的列 `TOTAL_WKTS`。这也意味着在编写上述语句时创建了 `ipl_dt` 的副本。这效率低下，在处理大型数据集时可能会产生大量开销并消耗更多内存。

`data.table` 提供了 `:=` 运算符，可用于添加/更新/删除列。请注意，这只能用于列 `j`，但可以与 `data.table` 的查询语法结合使用，即 `DT[i,j, by + other arguments]`。‘`:=`‘ 的语法是 `LHS := RHS`

![](img/page29-05.png)![](img/page30-01.png)

`LHS` 接受列名的字符向量，而 `RHS` 是一个值列表。

**表 2.18** 使用下面的代码在 ‘`ipl_dt`‘ 中添加了一个新列 `TOTAL_WKTS`。

![](img/page30-02.png)

请注意，**表 2.18** 未显示 `TOTAL_WKTS`，因为我们显示的是 ‘`ipl_dt`‘ 的前 10 列。**表 2.18** 也可以通过以函数形式编写查询获得，如下所示：

![](img/page30-03.png)

假设我们想删除列 `Ln(soldp)`。**表 2.19** 将是下面代码片段的结果。列 `Ln(soldp)` 将从 **表 2.19** 中消失（**注意：** 变量 `Ln(soldp)` 在数据中位于第 10 列之后，因此不会出现在 **表 2.18** 和 **2.19** 中）。

![](img/page30-04.png)

我们可以使用 `: =` 运算符替换列中的值。假设在 T20 板球中投球手的击球率（strike rate）为零，我们希望将其替换为该投球手在 ODIs 中的击球率。**表 2.20** 显示 `ipl_dt` 中只有一个这样的案例。

![](img/page30-05.png)![](img/page30-06.png)![](img/page31-01.png)

而且，Abdur Razzak 在 ODI 比赛中的击球率是

![](img/page31-02.png)

对于此类操作，如果我们使用 `:=` 运算符，它将对原始的 `ipl_dt` 本身进行更改。出于许多原因，我们可能不希望在原始 `data.table` 中进行更改。`copy()` 函数可以帮助创建 `ipl_dt` 的副本，我们将在其上使用 `:=` 运算符。

![](img/page31-03.png)

我们可以看到 T20 投球击球率已被 ODI 投球击球率替换。

![](img/page31-04.png)

让我们添加一个新列，显示每个 `PLAYING_ROLE`、`TEAM` 组合的最大售价。**表 2.21** 显示了下面代码片段的结果：

![](img/page31-05.png)

### 2.4.4 基本行和列选择与计算操作

在本节中，我们将了解行和列选择的使用以及对所选行和列应用某些计算。

例如，让我们创建一个 IPL 2011 前四支球队中来自澳大利亚、南非、斯里兰卡和巴基斯坦的所有球员的表格。请记住，前四支球队是 `CSK`、`MI`、`KKR` 和 `RCB`。

![](img/page31-06.png)![](img/page32-01.png)

**表 2.22** 显示了来自澳大利亚、南非、斯里兰卡或巴基斯坦的 `CSK` 球员。

![](img/page32-02.png)

**表 2.23** 显示了来自澳大利亚、南非、斯里兰卡或巴基斯坦的 `MI` 球员。

![](img/page32-03.png)

鼓励读者为 `KKR` 和 `RCB` 创建类似的表格。

从 **表 2.22** 有趣的是，`CSK` 在其阵容中有六名来自澳大利亚和南非的球员，但没有来自斯里兰卡或巴基斯坦的球员。在 `data.table` 中，像 `ipl_dt[COUNTRY == 'SA']` 这样的查询在内部被优化为使用二进制搜索，并在大型数据集上提供更快的結果。

然而，对于创建 **表 2.22** 和 **表 2.23** 所使用的更复杂的查询，`data.table` 提供了使用参数 ‘`on`’ 的功能。该参数有助于使用连接进行快速子集设置。下面的代码片段实现了 ‘`on`’ 来查询来自 `AUS`、`SA`、`SL` 和 `PAK` 的 `CSK` 球员，并将给出 **表 2.24** 中所示的输出。

![](img/page32-04.png)

如 **表 2.24** 所示，无匹配返回 `NA`，这意味着没有来自斯里兰卡和巴基斯坦的球员为 `CSK` 效力。为了抑制无匹配结果，我们可以执行下面的代码片段，这将导致 **表 2.25**。

![](img/page32-05.png)![](img/page32-06.png)![](img/page33-01.png)![](img/page33-02.png)

我们现在将尝试获取 IPL 前四支球队球员在之前 IPL 赛季中取得的总 wickets 数量。为此：



`1.` 我们将按如下方式子集行，即在 `TEAM` 上使用 `C(“CSK’”,MI”,KKR”,RCB’)`。使用 `on` 操作符会产生二分搜索，因此与写 `TEAM == ‘CSK’ & TEAM == ‘MI’ & TEAM == ‘KKR’ & TEAM == ‘RCB’` 相比速度更快。

`2.` 在列 `j` 上执行操作，即按 `TEAM` 分组计算 `TOTAL_WKTS`，其为 `PAST_IPL_WKT` 的总和，使用以下代码。

**表 2.26** 显示了下面代码的结果：
![](img/page33-03.png)
根据这些数据，似乎投球手之前的经验水平也对 IPL 2011 中球队的表现有所贡献。我们可以使用特殊关键字 `.EACHI` 重写导致 **表 2.26** 的查询，该关键字将遍历 `i` 的每个子集。
![](img/page33-04.png)

### 表 2.26 | 队伍 CSK、MI、KKR 和 RCB 在之前的 IPL 赛季中取得的总 wickets 数量
| TEAM || TOTAL_WKTS |
| --- | --- |
| CSK || 202 |
| --- | --- |
| MI || 178 |
| KKR || 46 |
| RCB || 58 |

### 表 2.27 | 各球队在之前的 IPL 赛季中得分的总 runs
| TEAM || TOTAL_IPL_RUNS |
| --- | --- |
| CSK || 8,649 |
| --- | --- |
| CSK+ || 1,118 |
| MI || 3,460 |
| MI+ || 4,855 |
| KKR || 278 |
| KKR+ || 7,322 |
| RCB || 3,952 |
| RCB+ || 7,187 |

**表 2.27** 使用以下代码显示了前四支球队球员的 IPL 得分：
![](img/page34-01.png)
在 **表 2.27** 中，`CSK+` 表示球员除了为 `CSK` 效力外还为其他球队效力。请注意，以上统计数据仅基于本数据集中 130 名球员的样本进行表示。实际上，数据可能远超这些统计数据。为了证实这一事实，让我们根据球员在过去 T20 比赛中的得分来查看 `MI` 的击球阵容（**表 2.28**）。
![](img/page34-02.png)
`MI` 的最高得分由印度球员取得（**表 2.28**）。**表 2.29** 显示了根据 `COUNTRY`、`PLAYING_ROLE` 和 `RUN_S` 的 `MI` 球员名单
![](img/page34-03.png)![](img/page34-04.png)![](img/page35-01.png)
`data.table` 中的 `on` 参数可用于对列执行高效的条件过滤操作。
`on` 参数内部使用连接以在大数据集上提供更快的結果。
`.EACHI` 是一个内置符号，可在 `by` 操作符中使用，对使用 `on` 操作符过滤的每个唯一值执行列的计算操作。
显而易见，这并不是为 `MI` 效力的球员的完整名单。我们还有一个 `MI+` 球队，其中包含过去为其他球队效力的人。
让我们深入研究投球部门。代表 `CSK`、`MI`、`KKR` 和 `RCB` 的来自前四国（基于 IPL 赛季球员数量）的球员拿下了多少 wickets？**表 2.30** 显示了 `AUS`、`SA`、`SL` 和 `PAK` 球员为 `CSK` 球队取得的 wickets。
![](img/page35-02.png)
哇！！！`CSK` 取得的总共 202 个 wickets 中，113 个来自 `AUS` 和 `SA` 的球员。表 2.31 显示了为 `CSK` 效力的这两个国家的投球手名单。
![](img/page35-03.png)
**表 2.31** 也可以通过下面的查询获得：
![](img/page35-04.png)![](img/page35-05.png)![](img/page35-06.png)

## 2.5 | 分组操作
基于特征列表的数据制表可以在 `data.table` 内完成。我们将使用以下代码计算球员在过去 IPL 出场中的平均 wickets。
![](img/page36-01.png)
在上面的查询中，我们可以使用 `min()`、`quantile()`、`mean()`、`median()` 和 `max()` 来获取数值列的特定汇总统计量。**表 2.32** 显示了按 `PLAYING_ROLE` 分组的球员取得的 T20 wickets 平均数量
![](img/page36-02.png)
**表 2.33** 显示了按 `AGE` 类别（25 岁以下、25 至 35 岁之间、35 岁以上）和 `PLAYING_ROLE` 分组的 T20 wickets 平均数量：
![](img/page36-03.png)
为了按列对结果排序，我们可以使用下面的查询。请注意，**表 2.33** 和 **表 2.34** 相同，但结果按 `PLAYING_ROLE` 排序。
![](img/page36-04.png)

### 表 2.32 | 过去 IPL 赛季中按 Playing role 取得的平均 wickets
| PLAYING_ROLE || AVERAGE_WKT_T20 |
| --- | --- |
| Allrounder || 19.028571 |
| --- | --- |
| Bowler || 32.818182 |
| Batsman || 3.128205 |
| W. Keeper || 0.000000 |
![](img/page36-05.png)![](img/page37-01.png)
请注意，`keyby` 参数不仅对 `data.table` 进行排序，还将列设置为键。键的概念及其在快速搜索中的用途将在后面讨论。
**表 2.35** 显示了按 `AGE`、`COUNTRY`、`TEAM` 和 `PLAYING_ROLE` 分组的 T20 wickets 平均数量。
![](img/page37-02.png)
2009 年拍卖的球员中有多少人仍在 `CSK`？
![](img/page37-03.png)
上面的查询也可以用 `.N` 编写，`.N` 是一个内置符号，表示当前组中的观测值数量。
![](img/page37-04.png)![](img/page37-05.png)![](img/page38-01.png)
**表 2.36** 显示了特定 playing role `Bowler` 的每个国家-球队组合的球员总数。
![](img/page38-02.png)
**表 2.37** 以排序后的顺序显示 **表 2.36**。结果按国家升序、球队降序排序
![](img/page38-03.png)
在上面的查询中，投球手计数被存储在变量 `bowler_count_dt` 中，然后在下一行进行排序。我们可以通过链接上述两个查询来避免临时变量。下面的代码片段也会导致 **表 2.37**。
![](img/page38-04.png)
`data.table` 的 `by` 参数可以接受列名和表达式。**表 2.38** 显示了在 T20 板球中取得超过五 wickets、在一日国际赛中取得超过 10 wickets、以及在 Test 板球中取得超过 20 wickets 的球员数量。
![](img/page38-05.png)
在 **表 2.38** 中，第一行对应于 `T20_5W >5 = TRUE`、`ODI_10W>10 = FALSE`、`TEST_20W>20=FALSE`，满足此标准的记录总数为 15 名球员。
**表 2.39** 显示了同时满足全部三个条件的计数：
![](img/page38-06.png)![](img/page38-07.png)![](img/page39-01.png)

### 表 2.39 | 取得超过五 wickets 在 T20 板球中、超过 10 wickets 在一日国际赛中、以及超过 20 wickets 在 Test 板球中的球员数量（全部条件满足）
| Condition || N |
| --- | --- |
| FALSE || 89 |
| --- | --- |
| TRUE || 41 |
`data.table` 中另一个有用的内置符号是 `.SD`，代表数据的子集。`.SD` 本身是一个 `data.table`，它保存使用 `data.table` 的 `by` 参数定义的子集数据。**表 2.40** 显示了使用 `.SD` 符号打印的 `ipl_dt`。
![](img/page39-02.png)
`.SD` 符号可以与 `lapply()` 函数一起使用，同时遍历多个列并计算我们感兴趣的统计量。让我们计算球员在所有三种比赛形式中取得的平均 wickets 数量和平均得分。为了做到这一点：
`1.` 我们使用 `lapply()` 来遍历列。



### 2.
我们已按 `AGE`、`PLAYING_ROLE` 对球员进行了分组。未使用 `by`，而是使用了返回有序集合的 `keyby`。

### 3.
我们已将想要计算平均统计量的列名传递到 `.SDcols` 中

**表 2.41** 显示了上述步骤通过以下代码片段应用后的结果：

![](img/page39-03.png)![](img/page39-04.png)![](img/page40-01.png)

`by` 运算符可用于按某些列相对于其他列对计算操作进行分组。此参数也可以接受条件表达式。

`.N` 是一个内置符号，表示当前组中的观测值数量。可用于根据行上的条件过滤器获取观测值的计数。

`.SD` 代表数据的子集，与 `.SDcols` 一起是另一个内置符号，可用于对 `.SDcols` 下指定的列应用计算操作，例如计算均值、中位数、标准差等。

**表 2.42** | 基于比赛角色的每位球员的 T20 wickets 和 test wickets

| PLAYING_ROLE || WICKETS_TAKEN |
| --- | --- |
| Allrounder || 15 |
| --- | --- |
| Allrounder || 19 |
| Allrounder || 47 |
| Allrounder || 73 |
| Allrounder || 5 |
| Allrounder || 2 |

`.SDcols` 是可选的。然而，在这种情况下，`lapply` 会抛出错误，因为数据集还包含字符列，而对字符变量计算均值是不成立的。

`data.table` 中对列的计算操作非常灵活。甚至可以使用 `data.table` 查询语法对列进行扁平化操作。例如，**表 2.42** 按比赛角色连接每位球员的 T20 wickets 和 test wickets：

![](img/page40-02.png)

## 2.6 | 键和基于二进制搜索的子集
在 `data.table` 中使用键可使其在子集化和处理后续下游活动时更加高效。键可以直观地被认为是 base R `data.frame` 的 `row.names`，但有以下例外：

**1.** 键可以设置在多个列上，且列可以是不同的数据类型。

**2.** 键中不强制唯一性

在 `data.table` 中设置键

**1.** 根据作为键提供的列名重新排列行。排序始终为升序。

**2.** 通过将名为 `sorted` 的属性设置为 `data.table` 来标记用作键列的列。

![](img/page41-01.png)

使用键时需要注意的一点是查询结构不会改变。这意味着第 2.4 和 2.5 节中讨论的所有查询语法仍可使用键进行，同时在处理大型数据集时具有速度和效率的优势。

让我们将 `COUNTRY` 和 `TEAM` 设置为 `ipl_dt` 中的键（**表 2.43**）

![](img/page41-02.png)

我们可以从 **表 2.43** 注意到 `ipl_dt` 按 `COUNTRY` 的升序排列，然后按 `TEAM` 排列。我们可以根据 `COUNTRY` 或 `TEAM` 或两者组合对 `ipl_dt` 进行子集化。**表 2.44** 显示了通过筛选来自澳大利亚且效力于 Chennai Super Kings 的球员得到的数据子集。

![](img/page41-03.png)

在上述子集查询中，`AUS` 在第一个键列 `COUNTRY` 中被查找。在匹配 `AUS` 的行中，`CSK` 与第二个键列 `TEAM` 匹配。由于我们未对 `j` 提供任何操作，查询返回了与这些行索引对应的所有列。

**表 2.45** 显示了来自斯里兰卡且效力于孟买印度人的球员取得的 wickets 数量。

![](img/page41-04.png)![](img/page41-05.png)

**表 2.45** | 国家为 SL 且效力于球队 MI 的球员取得的 wickets

| PLAYING_ROLE || WICKETS_TAKEN |
| --- | --- |
| Allrounder || 13 |
| --- | --- |
| Bowler || 17 |
| Bowler || 83 |

请注意，`ipl_dt` 的键设置为 `COUNTRY` `TEAM`

![](img/page42-01.png)

而在上述查询中，`data.table` 的键设置为 `PLAYING_ROLE`

![](img/page42-02.png)

使用键查询与向量扫描相比执行二进制搜索。如果未设置键，当我们编写类似 `ipl_dt[COUNTRY == 'AUS' & TEAM == 'CSK']` 的查询时，它会执行向量扫描。

为了理解这一点，假设 `ipl_dt` 是一个包含一百万条记录的大型数据集。当我们编写 `ipl_dt[COUNTRY == 'AUS' & TEAM == 'CSK']` 时，内部执行的操作如下：

**1.** 对列 `COUNTRY` 按行搜索值 `AUS`。结果将是一个大小为一百万的逻辑向量，标记为 TRUE、FALSE 或 NA。

**2.** 对列 `TEAM` 按行搜索值 `CSK`。结果将是一个大小为一百万的逻辑向量，标记为 TRUE、FALSE 或 NA。

**3.** 对步骤 1 和步骤 2 返回的上述两个逻辑向量执行逐元素 `&` 操作。只要两个逻辑向量的操作结果为 TRUE，就返回该值。

在执行相同的查询时，即通过将 `COUNTRY` 和 `TEAM` 设置为键执行 `ipl_dt[.( 'AUS', 'CSK' )]`，由于数据已按 `COUNTRY` 和 `TEAM` 排序，操作量将被减半。内部执行的操作将是：

**1.** 将排序后列 `COUNTRY` 的中间元素与值 `AUS` 进行比较。由于值 `AUS` 小于中间元素，搜索空间将被设置为该列的上半部分。

**2.** 再次将列 `COUNTRY` 上半部分的中间元素与值 `AUS` 进行比较，并继续迭代直到找到值 `AUS`。

**3.** 上述两个步骤将对列 `TEAM` 重复，以找到值 `CSK`。

**4.** 对上述两个逻辑向量执行 `&` 操作，只要表达式求值为 TRUE，就返回该值。

因此，与向量扫描相比，对大型数据集进行二进制搜索会快得多。我们可以看到，二进制搜索将搜索空间几乎减半，因此在查询大型数据集时速度极快。

## 2.7 | 连接操作
我们可能需要将多个数据帧的列合并到一个单一数据帧中。在这种情况下，两个数据帧都需要有一个公共列。然后可以从两个数据帧中检索剩余的列值并连接起来，在结果数据帧中创建一行。

要合并两个数据帧，可以使用带有 `on` 参数的 `data.table` 查询语法。它可以调用在其中一个数据帧上，另一个数据帧可以作为参数传递给它。参数 `on` 是数据帧中的公共列或键，应同时存在于两个数据帧中。

**1.** `X[Y, on=*]` 是一个连接操作，使用 `on=*` 提供的 `Y` 的列名或 `Y` 的键值作为索引查找 `X` 的行。这返回 `Y` 中所有与 `X` 匹配记录的行。

**2.** `Y[X, on=*]` 是一个连接操作，使用 `on=*` 提供的 `X` 的列名或 `X` 的键值作为索引查找 `Y` 的行。这返回 `X` 中所有与 `Y` 匹配记录的行。

数据帧可以根据多个公共列进行连接。连接类型可以是内连接、外连接、左连接或右连接，应在 `how` 参数中指定。

让我们创建两个代表 Chennai Super Kings 和 Mumbai Indians 的 `data.table`。我们已使用以下代码片段将 `COUNTRY` 和 `TEAM` 设置为键：

![](img/page43-01.png)

使用以下代码片段，**表 2.46** 显示了基于仅键名为 `TEAM` 的 `CSK` 球员。

![](img/page43-02.png)

在 **表 2.46** 中，`ipl_csk_dt` 的键将与 `ipl_dt` 相同，即 `COUNTRY` 和 `TEAM`。



如果我们想为 `ipl_csk_dt` 设置不同的键，就必须使用 ‘`keyby`’ 参数。然而，‘`keyby`’ 或 ‘`by`’ 要求提供列 ‘`j`’。我们可以使用内置运算符 `.SD` 来传递所有列，或提供特定的列名。**表 2.47**，使用下面的代码片段生成，显示了 TEAM CSK 的所有匹配行，并按 `AGE` 和 `PLAYING_ROLE` 分组选择列 `TEAM`、`COUNTRY` 和 `SOLD_PRICE`：

![](img/page43-03.png)![](img/page43-04.png)![](img/page44-01.png)

**表 2.48**，使用下面的代码片段生成，显示了 TEAM MI 的所有匹配行，并按 `AGE` 和 `PLAYING_ROLE` 分组选择列 `TEAM`、`COUNTRY` 和 `SOLD_PRICE`：

![](img/page44-02.png)

让我们将 `ipl_csk_dt`，即 **表 2.47** 与 `ipl_mi_dt`，即 **表 2.48** 使用它们的键进行连接。当我们写 `ipl_csk_dt[ipl_mi_dt]` 时，连接操作将使用 `ipl_mi_dt` 的 `AGE` 和 `PLAYING_ROLE` 键查找 `ipl_csk_dt`。

1. 在 **表 2.48** 中，`AGE==2` 且 `PLAYING_ROLE==BOWLER` 时，`ipl_mi_dt` 有三条记录。我们在 **表 2.47** 中也看到，对应于 `AGE==2` 且 `PLAYING_ROLE==BOWLER` 有两条记录。`ipl_csk_dt` 的每条记录都将与 `ipl_mi_dt` 组合出现。这将构成连接后 `data.table` 中的前六条记录。
2. 在 **表 2.48** 中，`AGE==3` 且 `PLAYING_ROLE==Allrounder` 时，有两条记录。我们在 **表 2.47** 中也看到，没有对应于 `AGE==3` 且 `PLAYING_ROLE==Allrounder` 的记录。因此，连接操作将从 `ipl_csk_dt` 报告 NA 值并将其与 `ipl_mi_dt` 组合显示。这将构成连接后 `data.table` 中的接下来的两条记录。

![](img/page44-03.png)

3. 在 **表 2.48** 中，`AGE==3` 且 `PLAYING_ROLE==Batman` 时，`ipl_mi_dt` 有一条记录。我们在 **表 2.47** 中也看到，对应于 `AGE==3` 且 `PLAYING_ROLE==Batsman` 有三条记录。`ipl_csk_dt` 的每条记录都将与 `ipl_mi_dt` 组合出现。这将构成连接后 `data.table` 中的最后三条记录。

这是一个右连接，输出显示在 **表 2.49** 中。

![](img/page45-01.png)

注意，`ipl_csk_dt[ipl_mi_dt, on =.(AGE,PLAYING_ROLE)]` 是可选的。我们没有提供键，因此连接是基于为 `ipl_csk_dt` 和 `ipl_mi_dt` 设置的键进行的。

我们可以抑制 NA 记录，这将类似于内连接，如 **表 2.50** 所示：

![](img/page45-02.png)

如果我们想创建类似 `ipl_mi_dt[ipl_csk_dt]` 的连接呢？此操作将使用 `ipl_csk_dt` 的键值查找 `ipl_mi_dt`。

1. 如 **表 2.47** 所示，`AGE==1` 且 `PLAYING_ROLE==Batsman` 时，`ipl_csk_dt` 有一条记录。在 `ipl_mi_dt` 中没有对应于 `AGE==1` 且 `PLAYING_ROLE==Batsman` 的记录（**表 2.48**）。因此，连接操作将从 `ipl_mi_dt` 报告 NA 值并将其与 `ipl_csk_dt` 组合显示。这将构成连接后 `data.table` 中的第一条记录。

![](img/page45-03.png)![](img/page45-04.png)

2. `ipl_csk_dt`（**表 2.47**）中接下来的三个 `AGE` 和 `PLAYING_ROLE` 组合，即

• `AGE==1` 和 `PLAYING_ROLE==Bowler`

• `AGE==2` 和 `PLAYING_ROLE==Allrounder`

• `AGE==2` 和 `PLAYING_ROLE==Batsman`

在 `ipl_mi_dt`（**表 2.48**）中也没有对应的匹配。因此，结果 `data.table` 的接下来的七条记录将是对应于 `ipl_mi_dt` 的 NA 记录，并将与 `ipl_csk_dt` 组合显示。
3. 如 **表 2.47** 所示，`AGE==2` 且 `PLAYING_ROLE==BOWLER` 时，`ipl_csk_dt` 有两条记录。我们也看到 `ipl_mi_dt` 有三条对应于 `AGE==2` 且 `PLAYING_ROLE==BOWLER` 的记录（**表 2.48**）。`ipl_mi_dt` 的每条记录都将与 `ipl_csk_dt` 组合出现。这将构成连接后 `data.table` 中的接下来的六条记录。
4. 在 **表 2.47** 中，`AGE==2` 且 `PLAYING_ROLE==W.Keeper` 时，`ipl_csk_dt` 有一条记录。`ipl_mi_dt` 没有对应于 `AGE==2` 且 `PLAYING_ROLE==W.Keeper` 的记录（**表 2.48**）。因此，连接操作将从 `ipl_mi_dt` 报告 NA 值并将其与 `ipl_csk_dt` 组合显示。这将构成连接后 `data.table` 中的下一条记录。
5. 最后，如 **表 2.47** 所见，`AGE==3` 且 `PLAYING_ROLE==Batman` 时，`ipl_csk_dt` 有三条记录。我们在 **表 2.48** 中也看到 `ipl_mi_dt` 有一条对应于 `AGE==3` 且 `PLAYING_ROLE==Batsman` 的记录。`ipl_mi_dt` 的该记录将与 `ipl_csk_dt` 组合出现。这将构成连接后 `data.table` 中的最后三条记录。

![](img/page46-01.png)

**表 2.51** 显示了按照上述步骤连接后的表：

**表 2.52** 显示了抑制表，去除了无匹配记录，使其成为内连接（左表在右表中有匹配行）。

![](img/page46-02.png)

下面显示了更多连接操作。**表 2.53** 显示了 `ipl_mi_dt` 对 `ipl_csk_dt` 的连接操作以及每个键的 `SOLD_PRICE`：

![](img/page46-03.png)

**表 2.54** 显示了 `ipl_csk_dt` 中所有在 `ipl_mi_dt` 中没有匹配记录的记录。这相当于查找 `ipl_csk_dt` 中在 `ipl_mi_dt` 中不存在的 `AGE` 和 `PLAYING_ROLE` 组合：

![](img/page46-04.png)![](img/page47-01.png)![](img/page47-02.png)![](img/page47-03.png)

如果我们想用未设为键的列名连接两个 `data.tables` 呢？这可以通过在 `on = *` 参数中显式传递列名来完成。**表 2.55** 显示了 `ipl_csk_dt` 与 `ipl_mi_dt` 基于 `ipl_mi_dt` 中存在的国家名称的连接。

连接操作可以通过使用语法 ‘`Table1[Table2]`’ 来合并数据表。此语法中表的顺序决定了结果表是左连接还是右连接。用于匹配的列使用 ‘`on`’ 操作指定。如果未指定 ‘`on`’ 操作符，则连接基于表的键进行。

![](img/page48-01.png)![](img/page48-02.png)![](img/page48-03.png)

## 2.8 | 数据表、数据框和包 DT

让我们看看以下内容的基本区别：

1. `data.table` 和 `data.frame`
2. 包 `data.table` 和包 `DT`

### 2.8.1 数据表 vs. 数据框

有经验的 R 用户了解创建 `data.table` 相对于读取为 `data.frame` 的优势。在这里，我们将重点介绍使用 `fread()` 读取文件（创建 `data.table`）和使用 `read.table()` 读取文件（创建 `data.frame`）之间一个重要的区别。使用基础 R 的 `read.table()` 将文件读取为 `data.frame` 时，我们会得到一个行名，我们也称之为索引列。为演示目的，我们使用 `read.table()` 读取 `ipl.csv` 文件并创建新的 `data.frame`，如 **表 2.56** 所示。

![](img/page49-01.png)![](img/page49-02.png)




在上面的代码块中，我们使用了 `row.names` 参数来传递一个特定的列，我们希望将其用作 `rownames`。如果不使用此参数，`rownames` 将默认为编号。

![](img/page49-03.png)![](img/page50-01.png)

我们可以使用 `rownames` 对行进行子集化。

![](img/page50-02.png)

上面代码片段的输出显示在 **表 2.57** 中。因此 `row.names` 就像 `data.frame` 行的索引，但其局限性在于：

**1.** 每行只能由一个 `row.name` 标识。

**2.** `row.name` 要求唯一值。

但一个玩家可以通过 `PLAYER.NAME`、`COUNTRY` 以及可能更多的属性唯一识别。这就是 `data.table` 中键的概念提供了一种高效处理此类情况的方法。`rowname`/`index` 和 `key` 之间一个根本区别是 `rowname` 必须是唯一的，但键的唯一性不受强制。我们可以通过使用 `fread()` 的 `key` 参数或在用 `fread()` 读取数据后使用 `setkey()` 来设置 `data.table` 中的键。

由于 `data.table` 继承自 `data.frame`，`data.table` 也有 `rowname` 属性但从不使用此属性。我们可以通过使用 `setDT()` 或 `as.data.table()` 将 `data.frame` 转换为 `data.table`。

![](img/page50-03.png)![](img/page50-04.png)![](img/page51-01.png)

在 **表 2.58** 中，我们可以看到 `rownames` 已被重置，原始的 `rownames`，即 “`PLAYER.NAME`” 已丢失。如果想在将数据框转换为 `data.table` 时保留 `rownames`，可以在 `as.data.table()` 或 `setDT()` 中设置参数 `keep.rownames=TRUE`。这将创建一个名为 `rn` 的新列，其中包含原始 `data.frame` 的行名。默认情况下，`keep.rownames=FALSE`，这将把 `rownames` 重置为默认编号，并且原始 `data.frame` 的任何索引列信息都将丢失。

![](img/page51-02.png)

### 2.8.2 Data.table 包与 DT 包

`DT` 包与用于读取 `IPL.csv` 文件的 `data.table` 包不同。`DT` 包可用于在 HTML 页面上以过滤、分页、排序等选项呈现 `data.tables` 以及 `data.frames`。

**图 2.3** 是下面代码块的结果。它将 `data.table` ‘`ipl_dt`’ 呈现为 `DT` 数据表。

![](img/page51-03.png)![](img/page51-04.png)![](img/page52-01.png)

上面代码片段中使用的 `datatable()` 函数来自 `DT` 包，不应与来自 `data.table` 包的 `data.table()` 函数混淆。

**图 2.3** 也可以修改以获取生成 csv、excel 或 pdf 文件的选项。**图 2.4** 是使用下面代码片段生成的，它显示了使用 `extensions` = ‘Buttons 的这些额外选项。

![](img/page52-02.png)

`options` 参数提供了修改数据表的外观和感觉的灵活性。

![](img/page52-03.png)

### 摘要

• 数据预处理的目的是通过数据汇总、基本统计指标和可视化来实现对数据的简单理解。

• 整洁格式的数据集有助于更轻松地处理数据以及可视化。

• `Data.table` 可视化为内存中的结构化查询语言（SQL）表，是用于加载和操作结构化数据而广泛使用的数据结构。

• `Data.table` 为 `DataFrame` 及其操作提供了出色的支持。过滤、分组、聚合、排序、连接等操作在该库中可直接使用。

• 在数据查询时，`Data.table` 有助于执行二分搜索而不是向量扫描，因此在处理非常大的数据集时速度非常快。

### 练习题

#### 使用宝莱坞数据集回答问题 1 至 9

数据文件 `bollywood.csv`（数据集链接在前言中提供）包含 2013-2015 年期间上映的电影的票房收入和社会媒体推广信息。以下是列及其描述。

• `SlNo` - 发行日期

• `MovieName` - 电影名称

• `ReleaseTime` - 提及特别发行时间。LW（长周末）、FS（节日季）、HS（假日季）、N（正常）

• `Genre` - 电影类型，如浪漫、惊悚、动作、喜剧等。

• `Budget` - 电影制作预算

• `BoxOfficeCollection` - 票房收入

• `YoutubeViews` - YouTube 预告片的观看次数

• `YoutubeLikes` - YouTube 预告片的点赞数

• `YoutubeDislikes` - YouTube 预告片的点踩数

#### 使用 R 代码回答以下问题

**1.** 数据集中有多少条记录？打印数据集的元数据信息。

**2.** 每个 `Genre` 发布了多少部电影？哪个类型发布的电影数量最多？按每个类型的发行数量降序排序。

**3.** 每个类型在不同的发行时间（如长周末、节日季等）发布了多少部电影？（注意：在 `Genre` 和 `ReleaseTime` 之间做交叉表。）

**4.** 一年中哪个月份电影发行数量最多？（注意：从 `ReleaseDate` 列中提取名为 `month` 的新列。）

**5.** 一年中哪个月份通常会发行最多的高预算电影，即预算为 25 亿卢比或以上的电影？

**6.** 投资回报率（`ROI`）最高的 10 部电影是哪几部？计算投资回报率（`ROI`）为 `(*BoxOfficeCollection - Budget*)/*Budget*`。

**7.** 如果电影在节日季或长周末发行，`ROI` 是否更高？计算不同发行时间的平均 `ROI`。

**8.** 比较喜剧类型电影和剧情片的 `ROIs` 分布。哪个类型通常具有更高的 `ROIs`？

#### 使用 SAheart 数据集回答问题 9 和 10

数据集 `SAheart.data` 取自以下链接：

[`www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data`](http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data)

数据集 `SAheartData.txt` 包含南非西开普省心脏病高风险地区男性回顾性样本。冠状动脉心脏病（CHD）病例约有两名对照。许多 CHD 阳性男性在 CHD 事件后接受了降压治疗和其他降低危险因素的项目。在某些情况下，测量是在这些治疗后进行的。这些数据取自 Rousseauw 等人（1983 年）描述的更大数据集，*South African Medical Journal*。它是一个制表符分隔文件，包含以下列（来源：*[`www-stat.stanford.edu`](http://www-stat.stanford.edu)*）

`sbp` - 收缩压

`tobacco` - 累计烟草（kg）

`ldl` - 低密度脂蛋白胆固醇

`adiposity`

`famhist` - 心脏病家族史（存在、缺席）

`typea` - A 型行为

`obesity`

`alcohol` - 当前酒精消费

`age` - 发病年龄

`chd` - 反应，冠状动脉心脏病

**9.** 数据集中有多少条记录？打印数据集的元数据信息。

**10.** 从 `age` 列派生名为 `age group` 的新列，其中不同年龄范围的人被归类如下：

(0-15): 年轻

(15-35): 成人

(35-55): 中年

(55-): 老年

### 参考文献

**1.** Anon (2020)，“*数据表选项*”，网页地址：[`rstudio.github.io/DT/options.html`](https://rstudio.github.io/DT/options.html)，访问于 2020 年 11 月 9 日。

**2.** Anon (2020)，“*DT：数据表库的 R 接口*”，网页地址：[`rstudio.github.io/DT`](https://rstudio.github.io/DT)，访问于 2020 年 11 月 19 日。




**3.** Weschools (2020), “*SQL 连接*”, 出版者: w3schools, 网址: [`www.w3schools.com/sql/sql_join.asp`](https://www.w3schools.com/sql/sql_join.asp), 访问于 2020 年 11 月 19 日.

**4.** Anon (2020), “*使用包入门*”, 网址: [`docs.racket-lang.org/pkg/getting-started.html`](https://docs.racket-lang.org/pkg/getting-started.html), 访问于 2021 年 1 月 14 日.

**5.** Anon (2019), “`setuptools`” 网址: [`github.com/pypa/setuptools/issues/1724`](https://github.com/pypa/setuptools/issues/1724), 访问于 2021 年 1 月 14 日.

**6.** Anon (2015), “*使用 R 进行数据分析的基础*”, 网址: [`www.slideshare.net/RsquaredIn/r-programming-importing-data-in-r`](https://www.slideshare.net/RsquaredIn/r-programming-importing-data-in-r), 访问于 2021 年 1 月 14 日.

**7.** Chomsky E and Lifshitz A (2021), “使用 `fread()` 读取 csv/tsv” 网址: [`tanaylab.github.io/tgutil/reference/fread_rownames.html?cv=1`](https://tanaylab.github.io/tgutil/reference/fread_rownames.html?cv=1), 访问于 2021 年 9 月 8 日.

**8.** Pradhan M and Kumar UD (2019), “*使用 Python 进行机器学习*”, Wiley, New Delhi.

_________________________

¹来源: [r-data.table.com](http://www.r-data.table.com)

²来源: [`www.kaggle.com/city-of-seattle/seattle-library-collection-inventory`](https://www.kaggle.com/city-of-seattle/seattle-library-collection-inventory)

# 数据可视化

## 3

*当学生准备好时，老师就会出现。当学生真正准备好时，老师就会消失。*

**—老子**

### 学习目标

阅读本章后，你将能够：
• 理解 R 中可视化的语法以及各种可视化图表背后的概念。
• 学习数据可视化以及使用数据进行讲故事的重要性。
• 学习准备诸如条形图、直方图、分布图、箱线图、散点图、趋势图和热图等图表以发现洞察。

## 3.1 | R 中的数据可视化

数据可视化在机器学习模型的构建和部署中发挥着重要作用。它帮助数据科学家有效地传达机器学习模型的输出和洞察。可视化通过协助特征工程等模型构建阶段，帮助数据科学家构建机器学习模型。

数据可视化也是商业智能（BI）不可或缺的组成部分。创新性的视觉效果被用于仪表板中，这些仪表板是公司生成报告的一部分，用于利用各种关键绩效指标了解其绩效。

包 `ggplot` 是 R 中用于可视化的强大包。`ggplot` 的基础基于 Wickham (2010) 提出的图形语法。¹ 图形语法是一种工具，有助于描述图形的构建块，并提供与图表不同层交互的灵活性。图表分层的概念使 `ggplot` 相对于其他可视化包具有优势。`ggplot` 包基于图形语法的坚实基础。为了演示 `ggplot` 的使用，我们将依赖 IPL 数据集（在下一节中描述）将数据加载到 `data.frame` 中并执行描述性分析。我们将使用 `data.table` 和 `ggplot2` 进行数据整理。

## 3.2 | IPL 数据集描述

印度 Premier League (IPL) 是由 BCCI 于 2008 年创立的职业 Twenty20 板球联赛，拥有八支由来自世界各地的球员组成的特许经营队。首次 IPL 拍卖于 2008 年举行，球队所有权期限为 10 年，底价为 5000 万美元。

各特许经营权通过每年举行的英式拍卖获得球员。然而，存在多项规则，其中包括特许经营权购买球员可花费的资金上限。

球员的表现可以通过多种指标来衡量。尽管 IPL 是一项 20 局制的锦标赛，但板球的其他形式（如测试赛和一日国际赛）中的表现也可能影响定价。少数球员的测试赛记录非常出色，但他们的 Twenty20 记录并不那么令人印象深刻。该数据集包含 130 名球员的表现，通过击球率、投球经济率等各种表现指标衡量。特征列表（文件名 `ipl.csv`）在 **表 3.1** 中提供 (Pradhan and Kumar, 2019)。

**表 3.1** | IPL 数据描述

| 数据代码 || 描述 |
| --- | --- |
| `AGE` || 拍卖时球员的年龄分为三类：类别 1 (L25) 表示球员年龄小于 25 岁，2 表示年龄在 25 至 35 岁之间 (B25-35)，类别 3 表示年龄大于 35 岁 (A35) |
| --- | --- |
| `RUNS S` || 球员得分的跑数 |
| `RUNS C` || 球员失分的跑数 |
| `HS` || IPL 中击球手取得的最高得分 |
| `AVE B` || IPL 中击球手平均得分 |
| `AVE BL` || 投球平均分（失分数/取得的 wickets 数）在 IPL 中 |
| `SR B` || 击球率（得分数与面对球数之比）在 IPL 中 |
| `SR BL` || 投球击球率（投球数与取得 wickets 数之比）在 IPL 中 |
| `SIXERS` || 球员在 IPL 中击出的六分球数量 |
| `WKTS` || 球员在 IPL 中取得的 wickets 数 |
| `ECON` || 投球手经济率（每局投球手失分数）在 IPL 中 |
| `CAPTAINCY EXP` || 曾担任 T20 队伍或国家队队长 |
| `ODI SR B` || 一日国际赛中的击球率 |
| `ODI SR BL` || 一日国际赛中的投球击球率 |
| `ODI RUNS S` || 一日国际赛中得分的跑数 |
| `ODI WKTS` || 一日国际赛中取得的 wickets 数 |
| `T RUNS S` || 测试赛中得分的跑数 |
| `T WKTS` || 测试赛中取得的 wickets 数 |
| `PLAYER SKILL` || 球员的主要技能（击球手、投球手或全能球员） |
| `COUNTRY` || 球员的原籍国（AUS：澳大利亚；IND：印度；PAK：巴基斯坦；SA：南非；SL：斯里兰卡；NZ：新西兰；WI：西印度群岛；OTH：其他国家） |
| `YEAR A` || IPL 拍卖年份 |
| `IPL TEAM` || 球员在 IPL 中效力过的队伍（CSK：Chennai Super Kings；DC：Deccan Chargers；DD：Delhi Daredevils；KXI：Kings XI Punjab；KKR：Kolkata Knight Riders；MI：Mumbai Indians；PWI：Pune Warriors India；RR：Rajasthan Royals；RCB：Royal Challengers Bangalore）。“+”号用于表示球员效力过多个队伍。例如，CSK+ 表示该球员曾效力于 CSK 以及一个或多个其他队伍。 |

## 3.3 | 安装包

以下代码可用于安装用于生成各种图表的包。

![](img/page57-01.png)

## 3.4 | 调用包

安装包后，我们准备好将包加载到内存中并使用以下提供的代码显示数据的快照。 **表 3.2** 显示了数据集的快照（10 列和 6 行）。

![](img/page57-02.png)![](img/page58-01.png)

## 3.5 | 使用可视化探索数据

在本节中，我们将讨论使用 `ggplot2` 包可以绘制的各种图表，该包实现了图形语法并可与 `data.frame` 或 `data.table` 无缝协作。

为了理解图形语法的基础知识，让我们以三个变量的简单示例为例：过去 IPL 比赛中投球平均分 (`AVE_BL`)、过去 IPL 比赛中投球击球率 (`SR_BL`)，以及来自 `ipl_dt` 的所有投球手所属的队伍 (`TEAM`)。特征的定义如下：

**1.** 投球平均分 (`AVE_BL`) 为失分数/取得的 wickets 数。投球平均分越低，表现越好。



## 2. 投球打击率 (`SR_BL`)

`SR_BL` 为投球数/取得 wickets 数。打击率越低，其表现越好。

下面的代码片段从 `ipl_dt` 中选择投球平均值、打击率和队伍，其中比赛角色为 'Bowler'。`head()` 函数用于打印前六个观测值，如 表 3.3 所示。

![](img/page58-02.png)

表 3.3 总结了不同 `TEAMS` 的投手的 `AVE_BL` 和 `SR_BL`。请注意，如果一名投手首次参加 IPL，`AVE_BL` 和 `SR_BL` 可能是零。如果我们想从上述数据生成 `AVE_BL` 和 `SR_BL` 之间的散点图，我们将为每个观测值绘制一个点。该点将根据 `AVE_BL` 在水平方向（横轴）定位，根据 `SR_BL` 在垂直方向（纵轴）定位。另外，假设我们想根据 `TEAM` 为点着色（红色、绿色、橙色等）。

生成散点图时，必须遵循以下步骤：

### 1. 创建新数据集

创建一个新数据集，该数据集反映了 `AVE_BL` 到横轴、`SR_BL` 到纵轴的映射，第三维度 `TEAM` 可以分配一个形状（例如点）。横轴、纵轴和形状（点）被称为图形的美学，即我们在图形上看到的东西。可以从上述数据生成许多美学。我们可以绘制折线图，在这种情况下形状将是线而不是点。我们也可以从上述数据生成条形图（美学为条形）。因此，点、线或条可以称为几何对象。

![](img/page58-03.png)

### 2. 转换数字

将数字，即 `AVE_BL` 和 `SR_BL` 转换为计算机可以显示的物理单位。我们可以通过线性缩放和使用笛卡尔坐标系来实现。这些转换需要对每个美学进行——横轴、纵轴和形状。在这种情况下，它也适用于 `TEAM`（将 `CSK` 映射为绿色，将 `DD` 映射为红色等）。这些转换被称为缩放。

### 3. 渲染上述数据

渲染上述数据以创建可在屏幕上显示的图形对象。此步骤将数据（由几何对象表示）、比例尺、坐标系和绘图注释（标题、背景、轴名等）结合起来。

根据步骤 2 中完成的转换/缩放想要生成的图表类型，可以实现许多图表变体。在散点图的示例中，这只是一个恒等变换，我们按数据中出现的样子绘制点。然而，可以在绘图前对数据进行分箱或聚合，它们可以被视为统计转换（直方图、箱线图、轮廓图、密度图、抖动图等）。

从变量到美学和几何对象的映射、缩放和转换以及渲染构成了图表的一层。一个图表可以有多个图层。图层组件是数据的物理表示，可在屏幕上看到。包含 stat 和 geom 组合的图层定义了许多熟悉的图形和图表，例如散点图、直方图、轮廓图、条形图等。

`ggplot2` 有助于实现下面描述的图形语法。

`ggplot` 包基于图形语法并遵循图表分层的概念。函数 `ggplot()` 创建一个空的绘图区域，直观上可以将其视为准备绘画的画布。

### 1. `ggplot()`

它创建一个坐标系统（空图），可以向其添加不同的图层。

### 2. `geom_objects`

`geom` 是绘图用于表示数据的几何对象。`geom_point()` 添加一个点的图层，从而创建散点图。

`ggplot2` 带有许多 `geom` 对象，每个对象向绘图添加不同类型的图层。

### 3.5.1 散点图

散点图是用点云表示的两个变量的图，显示两个数值变量的联合分布，其中每个点表示数据集中的一个观测值。散点图帮助数据科学家了解两个变量之间是否存在关联关系。关系可能是线性的或非线性的。散点图也有助于评估关系的强度并查找数据中是否存在异常值。散点图在构建回归模型期间用于决定是否将变量纳入回归模型。

以下代码片段可用于使用 `ggplot` 包创建 `AVE_BL` 和 `SR_BL` 之间的散点图。由于 表 3.2 中的数据要在不应用转换的情况下绘制，`stat` 和 `position` 参数取值为 "identity"。

![](img/page59-01.png)![](img/page60-01.png)

在 图 3.1 中，`ggplot()` 创建了一个绘图对象，然后向其添加了一个图层。在图层中，我们指定了数据和映射。我们还指定几何对象为点（以散点图形式显示各种记录）。

然而，使用 `ggplot` 时，`ggplot()` 中设置了许多默认值：

#### 1. Geom 默认值

当我们指定 `geom` 时，无需指定 `stats`，因为几何对象已预设默认转换，反之亦然。`ggplot` 定义了许多几何函数。例如，对于 `geom="point"`，`ggplot` 有 `geom_point()`，对于 `geom="bar"`，`ggplot` 有 `geom_bar()` 等。

#### 2. 美学映射

数据和美学映射可以在 `ggplot()` 本身中提供。然而，并非所有美学都适用于所有几何函数。在添加多个 `geom` 函数图层时，需要注意适用于该图层的美学。如果美学在 `geom` 函数内部传递，它将覆盖在 `ggplot()` 中传递的美学。

#### 3. 默认比例尺

根据变量类型和美学映射将添加默认比例尺。这意味着在上述绘图中默认使用 `scale_x_continuous()` 和 `scale_y_continuous()`。如果需要更改默认值，可以提及比例尺。例如，缩放为对数（`scale_x_log10()` 和 `scale_y_log10()`）等。

#### 4. 坐标系统

默认使用笛卡尔坐标系统。

图 3.1 中的散点图可以通过简化代码生成。我们还可以指定颜色美学来生成散点图并按 `TEAM` 着色。

![](img/page60-02.png)

请注意，我们已使用绘图注释来命名横轴、纵轴和标题（默认左对齐）。从 图 3.2 可以得出，这两个变量之间存在正相关。随着投球平均值的上升（即投手每取一 wicket 失分更多），打击率也会上升（即他每取一 wicket 投球数更多）。我们可以添加另一个图层 `geom_smooth()`，它将为数据拟合一条平滑线。图 3.3 显示了下面代码片段生成的图形。

![](img/page61-01.png)![](img/page61-02.png)![](img/page61-03.png)

请注意，美学变量在 `ggplot()` 中使用，而不是在 `geom` 函数内部。由于两个 `geom` 函数都使用了 `x` 和 `y` 美学，我们可以在更高级别使用它，而不是在 `geom` 函数内部。然而，存在无法在更高级别传递的 `geom` 函数级美学。例如，`geom_point()` 可以具有 `shape` 美学，根据变量 `TEAM` 为点赋予不同形状。然而，`geom_line()` 不能具有 `shape` 美学。因此，`shape` 美学不能传递给更高级别的函数 `ggplot()`。



在继续进行其他图表之前，我们将了解 `theme()` 函数的使用，该函数可对图表注释提供更多控制。以下代码片段使用 `theme()` 来更改标题、x 轴和 y 轴的文字颜色，并使标题居中对齐。

![](img/page62-01.png)![](img/page62-02.png)

**图 3.4** 显示了 ggplot2 默认绘图主题更改后的散点图。然而，图形的背景颜色以及主要和次要坐标轴仍然存在。我们可以进一步自定义图形。**图 3.5** 显示了使用以下代码片段得到的结果。

![](img/page62-03.png)![](img/page63-01.png)![](img/page63-02.png)

在上述代码片段中，可在 `element_text` 中使用的参数如下：

**1.** `family`: 字体族

**2.** `face`: 字体样式。可选值为 ‘plain, ‘italic’, ‘bold’, 和 ‘bold.italic’

**3.** `colour`: 文字颜色

**4.** `size`: 文字大小（pt）

**5.** `hjust`: 水平对齐（介于 0 和 1 之间。0 = 左对齐，0.5 = 居中对齐，1 = 右对齐）

**6.** `vjust`: 垂直对齐（介于 0 和 1 之间。0 = 左对齐，0.5 = 居中对齐，1 = 右对齐）

**7.** `lineheight`: 行高。在多行文本中，行高参数用于更改行与行之间的间距

请查阅 `?ggplot2::theme` 和 `?ggplot2::element_text` 的帮助信息，它们与 `theme` 协同工作。

我们可以通过在 `theme()` 中使用 `element_blank()` 来移除标题和坐标轴标签。存在内置主题，如 `theme_bw()`、`theme_classic()`、`theme_dark()`、`theme_grey()`、`theme_light()`、`theme_minimal()` 等，可直接应用于绘图。以下代码片段用于设置本章所有代码片段中使用的自定义主题。

![](img/page63-03.png)![](img/page64-01.png)

### 3.5.2 条形图

条形图是定性变量（或分类变量）的频数图。当变量为定性时，不能使用直方图（在 第 3.5.3 节 中讨论）。条形图可用于评估数据集中出现频率最高和最低的类别（Kumar, 2017; Roshan, 2020）。绘制条形图时，我们可以：

**1.** 使用 `geom_bar()`，它使条形的高度与每个类别或组中的案例数量成比例（如果提供了 `weight` 美学属性，则对其求和）。

**2.** 使用 `geom_col`，如果我们希望条形的高度代表实际值。数据框应作为 `data` 参数传入。**图 3.6** 显示了为每个年龄类别的球员计数创建的条形图。

`geom_bar()` 默认使用 `stat_count()`，因此会统计每个水平（`x`）位置的记录数。`geom_col()` 使用 `stat_identity()`，它绘制来自数据中的实际值。

由于 `data.table` 将 `AGE` 读取为整数变量，我们将在绘制条形图之前将其类型转换为 `factor` 变量。要按年龄获取球员计数，我们可以使用以下代码：

![](img/page64-02.png)

从 **图 3.6** 可以观察到，大多数球员属于 25-35 岁年龄组（`AGE` 2）。要绘制不同 `AGE` 组 `SOLD_PRICE` 的总和并显示每个年龄类别的总售价，我们应将 `SOLD PRICE` 作为 `weight` 参数传入，将 `AGE` 作为 `x` 参数（水平轴）传入。

请注意，为了以美元显示纵轴值，我们已在 `scale_y_continuous` 函数中传入了 `labels` 参数。它可以取三个值，即 `scales::percent`、`scales::dollar` 和 `scales::comma`。

![](img/page64-03.png)![](img/page65-01.png)![](img/page65-02.png)

我们可以使用 `geom_col` 如以下所示创建 **图 3.7**。

![](img/page65-03.png)

我们还可以创建可按第三个变量分组的条形图。在 **图 3.8** 中，我们按年龄类别显示总售价，但按比赛角色分组。`fill` 参数将第三个变量作为 groupby 参数。在此情况下，我们将 `PLAYING ROLE` 作为 `fill` 参数传入。

![](img/page66-01.png)![](img/page66-02.png)

如果我们想显示每个 `AGE` 组中的相对比例，可以使用 `position = position_fill()`，它会堆叠条形，然后将每个条形标准化为相同的高度。

![](img/page66-03.png)

在 **图 3.9** 中，我们可以比较三个不同年龄组击球手的售价，并得出结论击球手在 `AGE` 组 1 中的售价最高，其次是 `AGE` 组 3 和 `AGE` 组 2。默认情况下，`geom_bar` 或 `geom_col` 会生成堆叠条形图。**图 3.10** 显示了条形处于并排位置。我们将 `position` 参数设置为 `position = position_dodge()`。

![](img/page66-04.png)![](img/page67-01.png)![](img/page67-02.png)

如果我们想显示每个 `AGE` 组的平均售价，我们将首先使用以下代码创建包含该统计数据的 `data.table`。各年龄组的平均售价显示在 **表 3.4** 中。

**表 3.4** | 按年龄的平均售价

| `AGE` || `AVG_SOLD_PRICE` |

| --- | --- |

| 1 || 720,250.0 |

| --- | --- |

| 2 || 484,534.9 |

| 3 || 520,178.6 |

![](img/page67-03.png)![](img/page68-01.png)

以下代码块可用于创建 **图 3.11**：

![](img/page68-02.png)

从 **图 3.11** 可以看出，年龄类别 1 的平均售价更高。另请注意，`fill` 作为美学属性在 `mapping` 参数之外传入，因为我们希望在所有年龄组中使用相同的颜色填充。

我们可以创建可按第三个变量分组的条形图。在下面的示例 **(图 3.12)** 中，我们按年龄类别显示平均售价，但按比赛角色分组 **(表 3.5)**。

![](img/page68-03.png)

`fill` 参数将第三个变量作为分组变量。在此情况下，我们将 `PLAYING ROLE` 作为 `hue` 参数传入。

![](img/page69-01.png)![](img/page69-02.png)![](img/page69-03.png)

从 **图 3.12** 可以看出，在年龄类别 1 和 2 中，击球手的薪水最高，而在年龄类别 3 中，全能选手吸引的资金最多。

### 3.5.3 直方图

直方图是显示一组连续变量频率分布的图表。它提供了对变量的潜在分布（例如正态分布）、异常值、偏度等的洞察。要绘制直方图，我们使用 ggplot2 的 `geom_histogram()` 函数。以下是如何为 `SOLD PRICE` 绘制直方图并了解其分布的示例 **(图 3.13)**。

![](img/page69-04.png)![](img/page70-01.png)![](img/page70-02.png)

**图 3.13** 中的直方图显示 `SOLD PRICE` 右偏。大多数球员的拍卖价格在 250,000 至 500,000 的低价区间，而少数球员的薪水非常高，超过 1 百万美元。默认情况下，它会尝试估计覆盖数据范围的箱。要创建更多箱，可以在 `geom_histogram()` 方法中设置 `bins` 参数，如 **图 3.14** 所示。

![](img/page70-03.png)![](img/page71-01.png)![](img/page71-02.png)

我们可以使用 `fill` 美学属性来显示不同比赛角色球员售价的直方图。**图 3.15** 表示相同内容。

![](img/page71-03.png)



Unlike in **图 3.14**, in **图 3.15** fill aesthetic is being passed inside the mapping. This helps map the `PLAYING_ROLE` as an aesthetic and gives different colours to the bars by applying different `PLAYING_ROLE`.

`geom_histogram` displays the counts with bar. However, if we want to display the counts with lines, we can use frequency polygons with the geometrical object named `geom_freqpoly`. Frequency polygons are more suitable to compare the distribution across the levels of a categorical variable **(图 3.16).**

![](img/page71-04.png)![](img/page72-01.png)![](img/page72-02.png)

Let us say we want to show the relationship between two numeric variables. In 第 3.5.1 节, we saw that scatter plot was the obvious choice to get a plot between two numeric variables. However, when the data size is huge, scatter plot may not help in bringing out any pattern due to overlapping of points and the clutter which will show up.

**图 3.17** shows scatter plot between `SOLD_PRICE` and `BASE_PRICE` using the `geom_point`.

![](img/page73-01.png)

Though the data size is not huge in the current example, **图 3.17** shows overlapping points and does not bring out any relationship between the two variables. This issue can be overcome with 2D histogram.

So far, all the plots in this section have used straight-line segments (bins) to show the count of observations in each bin. This is because, in one-dimension, straight-line segments are the only possible shape for bin in a histogram. However, when we have two dimensions in the data, bins can take a more general shape (rectangular/Hexagon). This brings us to the two-dimensional histogram (2d histogram) implemented via `geom_bin2d` or through `geom_hex`. It can be useful to show the relationship between two numeric features when the data size is huge.

Imagine the scatter plot in **图 3.17** being filled with rectangular boxes (where the boxes represent the bins in horizontal and vertical directions). The count of values in each of the bins can be coloured with gradient fill.

**图 3.18** depicts the plot `SOLD_PRICE` and `BASE_PRICE` using the `geom_bin2d`. `bins` define the number of bins in horizontal and vertical direction. Lesser the number of bins, bigger the size of the hexagons. We will also use `scale_fill_gradient2` which creates a three-colour gradient fill(low-mid-high). In general:

**1.** `scale_*_gradient` creates a two-colour gradient (low-high). *可以设置为 fill 或 colour.

![](img/page73-02.png)

**2.** `scale_*_gradient2` creates a diverging colour gradient (low-mid-high). *可以设置为 fill 或 colour.

**3.** `scale_*_gradientn` creates an n-colour gradient. *可以设置为 fill 或 colour.

![](img/page74-01.png)

Scatter plot can be represented in a more appealing plot by hexagon shapes, and the count of points falling in each hexagon can be used to fill the shape.

**图 3.19** depicts the plot `SOLD_PRICE` and `BASE_PRICE` using the `geom_hex`. `bins` define the number of bins in the horizontal and vertical directions. Lesser the number of bins, bigger the size of the hexagons.

![](img/page74-02.png)

The darker shade reflects a count of 10 or more players in the hexagonal bin who were sold at their base price. The lighter shade reflects a count of less than five players in the bin, some of whom were sold for over $150,000, though their base price was approximately $50,000-100,000. below, **图 3.20** represents the same hexagon plot as shown above, but by filling the hexagons based on playing role.

![](img/page74-03.png)![](img/page75-01.png)![](img/page75-02.png)

Allrounders went for much more than their base price, reiterating the importance of that breed in T20 cricket.

### 3.5.4 分布或密度图

Before understanding the density plot, we need to understand basic terminology which is used to define the construction of density plot:

**概率密度函数（PDF）：** PDF is a limiting value of probability that a continuous random variable `X` takes in a small interval `x` and `x` + `8x`, when `8x` -> 0. That is, PDF of a continuous random variable `f(x)` is shown in 公式 3.1.

![](img/page75-03.png)

**1.** PDF satisfies the following properties:

• PDF is non-negative.

• PDF is real-valued.

• Equation 3.2 shows that the value of the function’s definite integral over the support dataset is equal to 1

![](img/page76-01.png)

In machine learning, random variables that follow uniform distribution, normal distributions and exponential distribution are used frequently to model business contexts to gain insights. In this section, we will focus on plotting density plot from IPL data.

A kernel is a special type of PDF with the additional property that it must be even. A kernel is a function with the following properties (Anon, 2020):

• Function is non-negative.

• Function is real-valued.

• Function’s definite integral over the support dataset is equal to 1.

• Function is even `f(x)` = `f(-x)`, for example, some theoretical PDFs such as uniform and standard normal distribution satisfy the properties of kernel functions.

**密度图：** It plots a smooth curve depicting the PDF or distribution of data. The peak of the curve helps in visualizing where the values are concentrated in any given data. Density plots are not affected by the number of bins and discover the distribution shape of the variable from the sample data. They also offer insight into what the distribution shape of the population is. The kernel density plot is arrived at by using kernel density estimation.

**核密度估计（KDE）：** It is a non-parametric method which can be used to estimate the PDF of a continuous variable (Anon, 2013). At every data point (observation), a kernel function is created with the observation at its centre. The kernel function generally used is gaussian curve (normal distribution). The observation is kept in the centre to ensure the kernel is symmetric about the observation. The PDF is then estimated by adding all kernel functions and dividing by the number of data points (Anon, 2013). This is done to ensure that the properties of PDF are satisfied.

Intuitively, a KDE can be perceived as a sum of ‘humps’ (bulged point). A ‘hump’ is assigned to every observation, and the size of the ‘hump’ represents the probability assigned at the neighbourhood of values around that observation. In `ipl_dt`, the `SOLD_PRICE` has six observations at `x` = $500,000 and one observation at `x` = $525,000 so the ‘hump’ at `x` = $500,000 will be six times the ‘hump’ at `x` = $525,000.

Apart from the observation being treated as the centre of the kernel, each kernel has a parameter called `bandwidth()`. Bandwidth of the kernel determines the range of the neighbourhood values to which probability will be assigned. We can think of bandwidth as the standard deviation of the smoothening kernel which is to be used to estimate the PDF. A bigger bandwidth results in a shorter and wider ‘hump’, which spreads out farther from the centre and assigns more probability to the neighbouring values (Cai, 2013). By default, in `density()` and `stat_density()`, the bandwidth parameter is set to `bw.nrd0`, and implements a rule-of-thumb for choosing the bandwidth of a Gaussian kernel density estimator. More details on the rule can be found with function `?stats::bw.nrd`.

The following steps are used in estimating KDE:

**1.** Replace each observation with a normal (Gaussian) curve with the observation being the centre of the curve.



2. 将 `curves` 的各个值相加，以计算给定 `dataset` 中每个点的 `density` 值。这将得到一条整体密度曲线。

3. 对所得曲线进行归一化，使其下方面积等于 1。

4. 所得曲线是核 PDF 或密度，并由密度图表示。

绘制密度图时，我们可以使用 `geom_density`，它计算并绘制核密度估计。`geom_density()` 内部使用 `stat_density()`，其中一些在估计 PDF 时起重要作用的参数默认设置为：

1. `kernel="gaussian"`。在控制台输入 `?density` 可获取可传递的所有核的列表。

2. `bandwidth="nrd0"`

3. `adjust = 1`。可用于调整带宽的乘法因子。

4. `n=512`。用于估计密度的等间距点数，`n` 的值应为 2 的幂，可使用 `?density` 获取更多详细信息。

在对 KDE 有了上述理解后，让我们生成一些密度图的变体。结果变量 `SOLD PRICE` 的密度图显示在 **图 3.21** 中。

![](img/page77-01.png)

**图 3.22** 显示了按每个 `PLAYING_ROLE` 的售价密度图。

![](img/page77-02.png)![](img/page77-03.png)![](img/page78-01.png)![](img/page78-02.png)

**图 3.23** 通过设置参数 `position="fill"` 显示了按 `PLAYING_ROLE` 填充的条件密度图。

![](img/page78-03.png)![](img/page79-01.png)

**密度图** 是理解数值变量分布的更可靠的可视化工具。分布是使用核密度估计技术估计的。变量可以作为美学映射中的 `x` 参数传递。

条件密度描述了分类变量与数值变量的条件分布。在 **图 3.23** 中，`PLAYING_ROLE== W.Keeper` 以 $100,000 被售出的概率约为 0.14，而 `PLAYING_ROLE== Bowler` 的概率约为 0.37。

两种不同连续变量的分布可以通过为两个连续变量分层两个 `geom_density` 来显示。**图 3.24** 显示了 `SOLD_PRICE` 和 `BASE_PRICE` 的密度图。

![](img/page79-02.png)

### 3.5.5 箱线图

箱线图（又称箱须图）是对数值数据的图形表示，可用于了解数据的变异性和异常值的存在情况。本节将讨论用于生成箱线图的代码。让我们考虑球员的变量 `SOLD_PRICE`。可用于生成箱线图并识别数据中异常值的步骤如下：

1. 按升序排列数据。按时间顺序（升序）排列的 `SOLD_PRICE` 中的观测值数量为

![](img/page79-03.png)![](img/page80-01.png)

排序数据中观测值的计数为 130。

![](img/page80-02.png)

2. 计算数据的中位数。这称为（四分位数 2）。如果数据中的观测值数量为 `n`，则中位数按以下逻辑计算，其中数据按升序排列：

• 如果 `n` 为奇数，则中间值是排序数据中第 `(n+1)/2` 个位置的观测值。

• 如果 `n` 为偶数，则中间值是中间两个数的平均值，即第 `floor((n+1)/2)` 个位置和第 `ceiling((n+1)/2)` 个位置的观测值。

由于 `SOLD_PRICE` 中的数据有 130 个观测值（偶数），它属于第二条规则。中间值是索引位置 65 `floor((obs + 1)/2)` 和索引位置 66 `ceiling((obs + 1)/2)` 处值的平均值。

![](img/page80-03.png)

3. 计算数据前半部分的中位数。这是 `Q1`（四分位数 1）。在 `ipl_sorted_dt` 中，前半部分观测值的数量为 64。由于这是偶数个观测值，因此适用步骤 2 的第二条规则。

![](img/page80-04.png)![](img/page81-01.png)

4. 计算数据后半部分的中位数。这是 `Q3`（四分位数 3）。在 `ipl_sorted_dt` 中，后半部分观测值的数量为 64。由于这是偶数个观测值，因此适用步骤 2 的第二条规则。

![](img/page81-02.png)

5. 箱体连接 `Q1` 到 `Q3`（包含中间 50% 的数据）。计算的其他统计量如下：

1. 四分位距 (`IQR`) 是第 3^(rd) 四分位数和第 1^(st) 四分位数之间的距离（差值）。箱体的长度相当于 `IQR`。`IQR` 计算为 `IQR = Q3 - Q1`。

2. 下限界 `LIF = Q1 - 1.5*IQR`

3. 上限界 `UIF = Q3 + 1.5*IQR`

![](img/page81-03.png)

6. 在 `ipl_sorted_dt` 中，大于或等于 `LIF` 的最小观测值为 20,000（下须）且小于或等于 `UIF` 的最大观测值为 135,000（上须）。须从下须延伸到 `Q1`，并从 `Q3` 延伸到上须。所有位于下须和上须之外的观测值称为异常值。

![](img/page82-01.png)

在 `ipl_sorted_dt` 中，下须侧没有异常值，因为没有点位于下须之外。然而，有四个唯一值大于上须。它们是 1,500,000；1,550,000；1,600,000；1,800,000。

箱线图的解释：

1. 如果图中有宽箱体和长须，则数据变化很大。

2. 如果箱体较小且须较短，则数据变化较小且聚集在一起。

3. 如果箱体较小而须较长，则数据可能变化较小，但可能存在一些“异常值”。

`ipl_dt` 上的箱线图可以使用 `geom_boxplot` 创建。**图 3.25** 显示了 `SOLD_PRICE` 的箱线图。上须之上的异常值用黑色点标记。

![](img/page82-02.png)

箱线图可以根据另一个分类特征进行拆分。**图 3.26** 显示了按 `PLAYING_ROLE` 的箱线图。

![](img/page82-03.png)

**图 3.26** 表明 `PLAYING_ROLE` 为 Batsman 时有三个异常点，`PLAYING_ROLE` 为 W. Keeper（守门员）时有一个异常点。

![](img/page83-01.png)

### 3.5.6 相关性和热图

本节将讨论相关性和热图。第一步是获取 `ipl_dt` 中所有数值特征的列表，可使用以下代码片段获得。

![](img/page83-02.png)

**表 3.6** 显示了一个 5 by 5 相关矩阵。我们可以使用以下代码片段找到数值特征之间的相关性：

![](img/page83-03.png)![](img/page83-04.png)

**表 3.7** 通过使用来自基础包的 `upper.tri()` 函数显示了一个下三角矩阵。

![](img/page84-01.png)![](img/page84-02.png)

**热图**，使用 `ggplot` 的 tile 对象，可用于可视化一个数字的方阵，该方阵可以作为美学映射中的 `x` 参数传递。数字的颜色代码可以是渐变填充，较低值采用较浅的色调，较高值采用较深的色调。

我们可以使用 `geom_tile()` 生成热图。由于相关系数范围为 −1 到 1，函数 `scale_fill_gradient2` 的参数 `limit` 设置为 `limit = c(-1,1)`。`coord_fixed()` 确保水平轴上的一个单位与垂直轴上的一个单位长度相同。

![](img/page84-03.png)



**图 3.27** 显示了 `ipl_dt` 中所有数值特征之间的相关性热力图。某些特征如总得分 (`TOTAL_RUNS`) 与测试板球得分 (`T_RUNS`) 和 ODI (`ODI_RUNS_S`) 中的得分高度相关。

### 3.5.7 趋势图
趋势图用于了解一段时间内值的变化。让我们绘制在不同拍卖年份中球员的平均 `SOLD_PRICE`。**表 3.8** 显示了在 `ipl_dt` 中在不同年份被拍卖的球员数量。

![](img/page84-04.png)![](img/page85-01.png)

这些球员的平均售价显示在 **表 3.9：**

![](img/page85-02.png)

**TABLE 3.9** | 平均售价

| `AUCTION_YEAR` || `AVG_SOLD_PRICE` |
| --- | --- |
| 2009 || 458,400 |
| --- | --- |
| 2008 || 492,067 |
| 2011 || 604,762 |
| 2010 || 290,000 |

我们将使用 `geom_line()`，它按 `x` 轴上变量的顺序连接观测值。

**1.** 如果我们使用 `geom_path()`，它会按数据中出现的顺序连接观测值。

**2.** `geom_step()` 创建阶梯图，突出显示变化的确切发生时间。

![](img/page85-03.png)![](img/page86-01.png)

**图 3.28** 显示了不同拍卖年份球员平均售价的趋势。请注意，数据是来自不同年份的球员样本，可能无法代表实际趋势。**图 3.29** 显示了使用 `geom_path()` 的平均售价，它按数据中出现的顺序连接观测值。

![](img/page86-02.png)![](img/page86-03.png)![](img/page87-01.png)

**图 3.30** 显示了使用 `geom_step()` 的平均售价，它创建阶梯图并突出显示变化发生的时间。

![](img/page87-02.png)

### 3.5.8 在网格中布局面板
我们可以使用 `ggplot` 中的 `facet_grid()` 创建绘图面板。Facet 一般意味着‘某事物的特定方面或特征’。当我们说想要创建一个以 `AGE` 和 `PLAYING_ROLE` 为分面变量的图时，意味着我们希望将 `AGE` 和 `PLAYING_ROLE` 作为数据的另外两个维度来可视化该图。

`facet_grid()` 形成由行和列分面变量定义的面板矩阵 (Anon, 2021)。当数据中有两个离散变量且变量的所有组合都存在时，它最有用。让我们取 第 3.5.5 节 中的箱线图，并以 `AGE` 和 `PLAYING_ROLE` 作为分面变量创建分面网格。

![](img/page87-03.png)![](img/page88-01.png)

从 **图 3.31** 可以看出，年龄组 2 类别（25 至 35 岁之间的球员）中有三个异常值：

**1.** 1 名 `PLAYING_ROLE` 为 Allrounder 的球员

**2.** 1 名 `PLAYING_ROLE` 为 Batsman 的球员

**3.** 1 名 `PLAYING_ROLE` 为 W. Keeper 的球员

我们还拥有年龄组 3 类别的异常值（年龄大于 35 岁的球员），其 `PLAYING_ROLE` 属于 Batsman。让我们绘制散点图并以 `AGE` 和 `PLAYING_ROLE` 对其进行分面。

![](img/page88-02.png)

**图 3.32** 显示了不同 `PLAYING_ROLE` 和 `AGE` 组之间投球平均值和打击率的散点图。有趣的是，W. Keeper 似乎在之前的比赛中投过球（投球平均值和打击率是投球手的表现衡量指标）。

![](img/page89-01.png)

### Summary
• 描述性分析的目标是通过数据汇总、基本统计量和可视化对数据进行简单理解。
• 使用 `ggplot` 实现的图形语法可用于创建直方图、分布图、箱线图、散点图、热力图等图。

### Exercises
#### 使用宝莱坞数据集回答问题 1 至 12
数据文件 `bollywood.csv`（数据集链接在前言中提供）包含 2013-2015 年期间上映的电影的票房收入和社交媒体推广信息。以下是列及其描述。
• `SlNo` - 上映日期
• `MovieName` - 电影名称
• `ReleaseTime` - 提及特殊上映时间。LW（长周末），FS（节日季），HS（假期季），N（正常）
• `Genre` - 电影类型，如浪漫、惊悚、动作、喜剧等。
• `Budget` - 电影制作预算
• `BoxOfficeCollection` - 票房收入
• `YoutubeViews` - YouTube 预告片的观看次数
• `YoutubeLikes` - YouTube 预告片的点赞数
• `YoutubeDislikes` - YouTube 预告片的点踩数

#### 使用 R 代码回答以下问题
**1.** 数据集中有多少条记录？打印数据集的结构信息（使用 `str()`）。
**2.** 每个类型上映了多少部电影？哪个类型上映数量最多？按降序排列每个类型的上映数量。
**3.** 每个类型中有多少部电影在不同的上映时间如长周末、节日季等上映？（注意：对 `Genre` 和 `ReleaseTime` 进行交叉制表。）
**4.** 一年中哪个月份的电影上映数量最多？（注意：从 `ReleaseDate` 列中提取名为 `month` 的新列。）
**5.** 一年中哪个月份通常上映高预算电影最多，即预算为 25 亿卢比或以上的电影？
**6.** 投资回报率（ROI）最高的 10 部电影是哪几部？按 `(BoxOfficeCollection - Budget)/Budget` 计算投资回报率（ROI）。
**7.** 如果电影在节日季或长周末上映，ROI 是否更高？计算不同上映时间的平均 ROI。
**8.** 绘制直方图和分布图以了解电影预算的分布。解释图表以得出结论：大多数电影是高预算还是低预算电影。
**9.** 比较喜剧类型电影和剧情片之间 ROI 的分布。哪个类型通常具有更高的 ROI？
**10.** 票房收入和 YouTube 点赞数之间是否存在相关性？相关性是正的还是负的？
**11.** 哪个类型的电影通常获得更多 YouTube 点赞？为每个电影类型绘制箱线图进行比较。
**12.** `Budget, BoxOfficeCollection, YoutubeView, YoutubeLikes, YoutubeDislikes` 这些变量中哪些高度相关？注意：绘制成对散点图。

### Bibliography
**1.** Anon (2020), “图形的分层语法 - Hadley WICKHAM”，网址：[`vita.had.co.nz/papers/layered-grammar.pdf`](http://vita.had.co.nz/papers/layered-grammar.pdf)，访问于 10 May 2021.
**2.** Anon (2021), “核密度估计”，网址：[`en.wikipedia.org/wiki/Kernel_density_estimation`](https://en.wikipedia.org/wiki/Kernel_density_estimation)，访问于 2021.
**3.** Anon (2021), “Facet_wrap 标签”，网址：[`www.xspdf.com/resolution/52295281.html`](https://www.xspdf.com/resolution/52295281.html)，访问于 10 May 2021.
**4.** Cai E (2013), “探索性数据分析：核密度估计 - 概念基础 | The Chemical Statistician (wordpress.com)’，网址：[`chemicalstatistician.wordpress.com/2013/06/09/exploratory-data-analysis-kernel-density-estimation-in-r-on-ozone-pollution-data-in-new-york-and-ozonopolis`](https://chemicalstatistician.wordpress.com/2013/06/09/exploratory-data-analysis-kernel-density-estimation-in-r-on-ozone-pollution-data-in-new-york-and-ozonopolis)/，访问于 10 May 2021.



5. Kumar UD 和 Ranjan K (2012)，“印度板球超级联赛球员定价”，印度管理学院，班加罗尔，可在哈佛商业出版案例门户获取，网址：[`hbsp.harvard.edu/product/IMB379-PDF-ENG?Ntt=Pricing+of+players+in+the+Indian+premier+league&itemFindingMethod=Search`](https://hbsp.harvard.edu/product/IMB379-PDF-ENG?Ntt=Pricing+of+players+in+the+Indian+premier+league&itemFindingMethod=Search)”，访问于 2021 年 5 月 10 日。

6. Roshan B (2020)，“使用 R 进行数据可视化”，可在 Part 4: Data Visualization with R | Kaggle 获取，网址：[`www.kaggle.com/benroshan/part-4-data-visualization-with-r`](https://www.kaggle.com/benroshan/part-4-data-visualization-with-r)，访问于 2021 年 5 月 5 日。

7. Pradhan M 和 Kumar UD (2019)，“使用 Python 的机器学习”，Wiley，新德里。

8. Wilkinson L (2005)，*“图形语法”* (2^(nd) ed.)。统计与计算，Springer，纽约。

9. Wilkinson L, Anand A 和 Grossman R (2005)，“基于图论的 Scagnostics”，载于 IEEE 信息可视化研讨会，157-164。

________________________

¹图形语法：[`vita.had.co.nz/papers/layered-grammar.pdf`](http://vita.had.co.nz/papers/layered-grammar.pdf)

²来源：[`r4ds.had.co.nz/data-visualisation.html`](https://r4ds.had.co.nz/data-visualisation.html)

# 概率与分布

## 4

*一朵花凋落，即使我们爱它；一株杂草生长，即使我们不爱它。*

—道元禅师

### 学习目标

阅读本章后，你将能够：

• 理解概率论的基本概念。
• 学习随机变量和概率分布的概念。
• 理解二项分布、正态分布等不同概率分布及其在分析中的应用。
• 学习如何从均值、方差、概率分布函数、置信区间等概念中得出洞察。
• 学习如何制定和执行假设检验，如单样本 Z 检验、t 检验、双样本 t 检验、配对 t 检验、卡方检验和方差分析（ANOVA）。

## 4.1 概述

概率论是分析学和机器学习算法的构建基石之一。分析应用涉及预测事件发生的概率、检验假设、构建模型以解释对企业重要的关键绩效指标（`KPI`）的变化，例如盈利能力、市场份额、需求等。分析中的许多重要任务都涉及不确定事件，因此必须理解用于衡量和预测不确定事件发生的概率论。本章介绍随机变量和概率分布的概念以及它们如何应用于解决组织问题。我们还将探讨各种离散和连续分布的概念、概率质量函数、概率密度函数和累积分布函数。最后，我们将讨论假设检验及其在 `ML` 算法中特征选择中的重要性，了解显著性（`a`）值、概率值（`p-value`）的概念以及 Z 检验、各种 t 检验和卡方拟合优度检验等各种假设检验。

## 4.2 概率论 - 术语

本节将讨论概率论中使用的各种术语。

### 4.2.1 随机实验

在机器学习中，我们主要处理不确定事件。随机实验是一种结果不确定的试验。也就是说，随机实验的输出无法确定性地预测（Pradhan and Kumar, 2019）。产品的收入产生、贷款违约以及体育赛事的结果都是随机实验的例子。

### 4.2.2 样本空间

样本空间是包含随机实验所有可能结果的通用集合。它通常用字母 `S` 表示，单个结果称为基本事件。样本空间可以是有限的或无限的。下面描述了一些随机实验及其样本空间（Kumar, 2017）：

实验：大学申请的结果。相应的样本空间 = `S = {admitted, not admitted}`

实验：预测单个客户层面的客户流失。相应的样本空间 = `S = {Churn, No Churn}`

实验：电视节目的电视收视率点（TRP）以及相应的样本空间 = `S = X | X ∈ R,0 ≤ X ≤ 100`；也就是说，`X` 是一个实数，可以取 0 到 100 百分比之间的任何值。

### 4.2.3 事件

事件（`E`）是样本空间的子集，概率通常相对于事件计算。事件的例子包括（Kumar, 2017）：

1. 在电子商务门户网站上下的订单取消百分比超过 10%。
2. 欺诈性信用卡交易百分比超过 1%。
3. 资本设备的寿命少于 1 年。
4. 在保修期为 2 年的 2,000 辆车车队中，汽车制造商的保修索赔数量少于 100 起。

## 4.3 随机变量

随机变量在描述、衡量和分析不确定事件（如客户流失、员工流失、产品需求等）方面发挥着重要作用（Kumar）。它是一个函数，将样本空间中的每个结果映射到一个实数，并提供描述事件的灵活性。随机变量可以根据其取值分为离散型或连续型。如果随机变量 `X` 只能取有限或可数无限集合的值，则称为离散随机变量。离散随机变量的例子有：

1. 信用评级（通常分为低、中、高等不同类别，或使用 AAA、AA、A、BBB 等标签）。
2. 电子商务零售商收到的订单数量，可以是可数无限的。
3. 客户流失 [随机变量取二值：（a）流失和（b）不流失]。
4. 欺诈 [随机变量取二值：（a）欺诈交易和（b）真实交易]。

可以取无限集合值的随机变量 `X` 称为连续随机变量。连续随机变量的例子如下：

1. 公司市场份额（取 0 到 100% 之间无限集合中的任意值）。
2. 组织员工中的流失百分比。
3. 工程系统的失效时间。
4. 在电子商务门户下单完成所需的时间。

离散随机变量使用概率质量函数（`PMF`）和累积分布函数（`CDF`）描述。`PMF` 是随机变量 `X` 取特定值 k 的概率；例如，电子商务平台上的欺诈交易数量等于 10，写为 `P(X = 10)`。`CDF` 是随机变量取值小于或等于 10 的概率，写为 `P(X ≤ 10)`。

连续随机变量使用概率密度函数（`PDF`）和 `CDF` 描述。`PDF` 是连续随机变量在 `x` 的小邻域内取值的概率，给出为：

![](img/page93-01.png)

连续分布的 `CDF` 是随机变量取值小于或等于值 ‘a 的概率。数学上，

![](img/page93-02.png)



`CDF` 描述于 式 (4.2) 是 `PDF` 曲线下至 `X` = `a` 的面积。请注意 `PDF` 不是概率值。相反，它是概率的极限值，因此可以取大于 1 的值。`CDF` 另一方面是一个概率，其值介于 0 和 1 之间。在以下章节中，我们将讨论各种离散和连续分布的概念以及如何将其应用于现实世界场景。

## 4.4 | 二项分布

二项分布是离散概率分布，在许多商业环境中具有多种应用。当随机变量 `X` 满足以下条件时（Kumar, 2017）：

**1.** 随机变量只能有两个结果 - 成功和失败（也称为伯努利试验）。

**2.** 目标是求在 `n` 次试验中得到 `x` 次成功的概率。

**3.** 成功的概率为 `p`，因此失败的概率为 (1 - `p`)。

**4.** 概率 `p` 是常数，在试验之间不会改变。

成功和失败是二项分布中使用的通用术语，我们必须根据上下文推断成功和失败：

**1.** 客户流失，其中结果为：(a) 客户流失 和 (b) 无客户流失。

**2.** 欺诈性保险索赔，其中结果为：(a) 欺诈性索赔 和 (b) 真实索赔。

**3.** 客户贷款偿还违约，其中结果为：(a) 违约 和 (b) 未违约。

二项分布的 PMF（成功次数恰好为 `x` 的概率，`n` 次试验中）由下式给出

![](img/page93-03.png)

其中，

![](img/page93-04.png)

二项分布的累积分布函数由下式给出

![](img/page94-01.png)

### 4.4.1 使用 R 的二项分布示例

Fashion Trends Online (FTO) 是一家销售女装的电子商务公司。观察发现，其 10% 的客户因多种原因（尺寸、颜色和材质不匹配）退回已购买的商品。在某一天，20 名客户从 FTO 购买了商品。计算：

**1.** 恰好有五名客户退回商品的概率。

我们必须使用 式 (4.3) 来计算此概率。相应的 R 代码为

![](img/page94-02.png)

`dbinom()` 接受三个参数：

**1.** 预期成功试验次数 (5)

**2.** 试验次数 (20)

**3.** 成功概率 (0.1)

注意，括号中的值表示上述示例中参数的值。恰好有五名客户退回商品的概率约为 3%。

**2.** 最多有五名客户退回商品的概率。

我们必须使用 式 (4.4) 来计算此概率，相应的 R 代码为

![](img/page94-03.png)

`pbinom` 当 `lower.tail` = TRUE 时返回 `P`(`X` ≤ `x`)。

**3.** 退回其购买商品的客户超过五名的概率。在这种情况下，我们必须计算 1 - `F`(`x`)。相应的代码为

![](img/page94-04.png)

`pbinom` 当 `lower.tail` = FALSE 时返回 `P`(`X` > `x`)。

**4.** 可能退回商品的客户平均数以及退货数量的方差和标准差。

**1.** 二项分布的平均值由 `n` * `p` 给出

**2.** 二项分布的方差由 `n` * `p` * (1 - `p`) 给出

![](img/page95-01.png)

## 4.5 | 泊松分布

在许多情况下，我们可能有兴趣计算一段时间内可能发生的事件数。例如，电子商务门户网站客户取消订单的数量、客户投诉数量、ATM 取款次数、书籍中打字错误的数量、班加罗尔道路上的坑洞数量等，都涉及在一段时间内对事件进行计数（Kumar, 2017）。为了求事件数量的概率，我们使用泊松分布。泊松分布的概率质量函数由下式给出

![](img/page95-02.png)

其中 `λ` 是每单位测量（在许多情况下测量单位很可能是时间）的事件发生率。

相应的累积分布函数 `F`(`x`) 由下式给出

![](img/page95-03.png)

### 4.5.1 使用 R 的泊松分布示例

呼叫中心收到的呼叫数量服从每小时 10 次的泊松分布。

**1.** 计算呼叫数量最多为五次的概率。

我们必须使用 式 (4.6) 其中 `x` = 5 且 `λ` = 10。相应的 R 代码为

![](img/page95-04.png)

**2.** 计算三小时期间呼叫数量超过 30 的概率。

由于每小时平均呼叫次数为 10（`λ` = 10），并且我们关注的是 3 小时内的呼叫，3 小时内的呼叫平均数为 `λ`*`t`* = 30。呼叫次数超过 30 的概率由下式给出

![](img/page95-05.png)

## 4.6 | 指数分布

指数分布是一种单参数连续分布，传统上用于模拟电子元件的失效时间。它表示事件以恒定速率连续且独立发生的过程（Kumar, 2017）。

概率密度函数由下式给出

![](img/page96-01.png)

累积分布由下式给出

![](img/page96-02.png)

其中，

**1.** 参数 `l` 是尺度参数，表示事件发生的速率

**2.** 指数分布的均值由 1/`A` 给出。

### 4.6.1 使用 R 的指数分布示例

航空电子系统的失效时间服从指数分布，其平均故障间隔时间（MTBF）为 1,000 小时（`X` *\=* 1/1,000）。

**1.** 计算系统在 1,000 小时前失效的概率。

我们必须计算 `F`(`x`)，其中 `x` = 1,000 且 `λ` = 1/1,000。相应的 R 代码为

![](img/page96-03.png)

**2.** 计算其在 2,000 小时内不会失效的概率。

我们必须计算 1 - `F`(`x`)，其中 `x` = 2,000 且 `λ` = 1/1,000。相应的 R 代码为

![](img/page96-04.png)

## 4.7 | 正态分布

正态分布，也称为高斯分布，是分析领域最流行的连续分布之一，尤其由于其在多个上下文中的使用。它通常被称为钟形曲线。正态分布的 PDF 和 CDF 在方程 4.9 和 4.10 中给出。

![](img/page96-05.png)![](img/page96-06.png)

在 式 (4.9) 中，`µ` 和 `σ` 分别为均值和标准差。

### 4.7.1 正态分布示例

为了理解正态分布及其应用，我们将使用在 BSE（孟买证券交易所）交易的股票的日收益率。设想一个场景，投资者在投资前希望了解与各种股票相关的风险和回报（Pradhan and Kumar, 2019）。对于此分析，我们将评估两只股票：

**1.** Pfizer: [`in.finance.yahoo.com/quote/PFE`](https://in.finance.yahoo.com/quote/PFE)/

**2.** Glaxo: [`in.finance.yahoo.com/quote/GLAXO.NS`](https://in.finance.yahoo.com/quote/GLAXO.NS)/

首先，我们将在回到正态分布的应用之前加载和准备数据。

![](img/page97-01.png)

Date 列将被视为因子（特征）变量。**表 4.1** 显示 Pfizer 数据，其中 ‘Date’ 列已转换为正确的数据类型。该表还具有 ‘Month’ 和 ‘Year’ 列从 Date 变量中提取。然而，**表 4.1** 仅出于可读性的考虑显示了前五列。

![](img/page97-02.png)



Pfizer raw data, has records from June 1972 **(表 4.1)**，而葛兰素史克股票数据可从 2002 年 7 月获得。为了从同一时间线比较两只股票，我们将使用辉瑞数据框中的匹配子集，使其股票价格从 2002 年 7 月开始。此外，我们的分析仅涉及每日收盘价，因此我们将从数据框中选择 `Date` 和 `Close` 列。让我们执行以下操作来准备数据：
1. 对 `raw_pfizer_df` 进行子集化，以从 2002 年 7 月起获取 `Date` 和 `Close` 价格
2. 删除包含 `NA` 值 的行
3. 将 `Close` 列重命名为 `pfizer_close`
4. 对 `pfizer_close` 列进行缩放

![](img/page97-03.png)![](img/page98-01.png)

**表 4.2** 给出了使用以下代码片段应用的四个操作的快照：

![](img/page98-02.png)

**表 4.3** 给出了使用以下代码读取的葛兰素史克数据的快照：

![](img/page98-03.png)

让我们执行一些操作来准备数据：
1. 对 `raw_glaxo_df` 进行子集化以获取 `Date` 和 `Close` 价格。
2. 删除包含 `NA` 值 的行。
3. 将 `Close` 列重命名为 `glaxo_close`。
4. 对 `glaxo_close` 列进行缩放。

**表 4.4** 显示了应用上述四个步骤后的数据集：

![](img/page98-04.png)![](img/page98-05.png)

**表 4.4** | 葛兰素史克数据

| `Date` || `glaxo_close` |
| --- | --- |
| 2002-07-01 || 182.600 |
| --- | --- |
| 2002-07-02 || 183.000 |
| 2002-07-03 || 183.700 |
| 2002-07-04 || 185.750 |
| 2002-07-05 || 182.375 |

### 4.7.2 可视化数据
可视化每日收盘价将显示股票价格随时间的变化。为了显示收盘价的趋势，记录应按时间排序（Pradhan and Kumar, 2019）。由于数据框具有日期列，我们将使用 `dplyr` 包来连接 `pfizer_df` 和 `glaxo_df`。

![](img/page99-01.png)

`dplyr` 使用 SQL 风格的数据库语法进行连接操作。它支持不同的连接操作，我们将使用左连接操作。

左连接将包含左数据框中的所有内容以及右数据框中匹配的所有行。如果连接列具有相同的名称，则查询为 `left_join(x, y)`。如果列没有相同的名称，则需要 ‘by’ 参数，例如 `left_join(x, y, by = c("df1ColName" = "df2ColName"))`。**表 4.5** 显示了合并后数据框的快照：

![](img/page99-02.png)

我们将在同一图表中可视化两只股票的价格（辉瑞和葛兰素史克）。为此，我们将使用 `tidyr` 包展平 **表 4.5**。**表 4.6** 显示了展平后的数据的前五个观测值。

![](img/page99-03.png)![](img/page99-04.png)![](img/page100-01.png)

我们将使用 `ggplot` 包来可视化 **表 4.6** 中的数据。

![](img/page100-02.png)

可以从 **图 4.1** 观察到，在 2007-2010 年期间，葛兰素史克的收盘价呈上升趋势。辉瑞在同一时期呈下降趋势，随后自 2011 年以来呈上升趋势。

### 4.7.3 分析股票数据
如果我是短期（日内）投资者，有兴趣了解这些股票的以下特征？
1. 这些股票的预期日回报率是多少？
2. 就日回报而言，哪些股票风险或波动性更高？
3. 95% 置信区间的预期回报范围是多少？

![](img/page100-03.png)

4. 哪只股票实现日回报率达 2% 或更高的概率更高？
5. 哪只股票出现日亏损（风险）达 2% 或更高的概率更高？

要回答上述问题，我们必须找出这些股票的日回报行为（我们此后将称之为“收益”）。使用 式 4.11，**表 4.7** 和 **表 4.8** 显示了按收盘价相对于前一日收盘价的百分比变化计算的收益。

![](img/page101-01.png)

以下代码片段用于生成 **表 4.7**（葛兰素史克收益）和 **表 4.8**（辉瑞收益）：

![](img/page101-02.png)

第一天的收益显示为 `NA`，因为没有前一天可供计算。我们可以使用 `na.omit()` 方法删除此记录。**表 4.9** 显示了删除 `NA` 记录并合并 **表 4.7** 和 **表 4.8** 后的数据。注意，**表 4.9** 仅显示五个列以提高可读性。

![](img/page101-03.png)![](img/page101-04.png)![](img/page101-05.png)![](img/page102-01.png)

展平 **表 4.9** 后得到 **表 4.10**。**表 4.10** 仅包含两只股票的收益列（注意：**表 4.10** 是一个展平的文件，显示前五个观测值）。展平 **表 4.9** 的原因是使其可用于绘制图表。

![](img/page102-02.png)

我们可以使用以下代码片段使用 `ggplot` 包可视化 **表 4.10** 中的数据。

![](img/page102-03.png)

**图 4.2** 显示日收益高度随机，并在 0.00 附近波动。收益大多保持在很小的范围内。

我们可以绘制辉瑞和葛兰素史克股票收益的分布图以获得更好的洞察。

![](img/page102-04.png)

收益 **(图 4.3)** 对于两只股票似乎呈正态分布，均值在 0.00 左右。葛兰素史克的方差似乎高于辉瑞。（注意：该分布有长尾，但为简单起见，我们将假设正态分布。）

![](img/page102-05.png)![](img/page103-01.png)![](img/page103-02.png)

### 4.7.4 均值和方差
正态分布有两个参数：分布的均值 µ 和方差 σ²。正态分布的均值可使用 式 (4.12) 从样本中估计。

![](img/page103-03.png)

样本数据正态分布的方差由下式给出

![](img/page104-01.png)

标准差是方差的平方根，用 σ 表示。数据框列上的方法 `mean()` 和 `sd()` 分别返回均值和标准差。

![](img/page104-02.png)

从 **图 4.3**，我们可以推断两只股票的预期日回报率（收益）约为 0%。此外，从上面的代码片段中，我们看到葛兰素史克股票的风险更高，因为葛兰素史克的标准差为 4%，而辉瑞的标准差为 2%。

### 4.7.5 置信区间
置信区间是在一定概率（通常为 95%）下平均回报可能所在的区间。要找到回报的 95% 置信区间，我们需要在分布的两侧计算均值两侧两个标准差的收益值，即 µ ± 2σ。在正态分布下，均值两侧两个标准差下的面积（即 µ ± 2σ）约为 95%。我们可以使用 `gmodels` 包来获得置信区间（`install.packages('gmodels')`）。

![](img/page104-03.png)

葛兰素史克 95% 置信区间收益的回报介于 −3.316506 × 10^(−06) 和 2.395655 × 10^(−03) 之间。辉瑞 95% 置信区间的回报为 (−0.00051, 0.00098)。

![](img/page105-01.png)

### 4.7.6 累积概率分布



为了理解收益高于 2% 或更高的概率，我们需要找出收益取值大于 0.02（即 2%）的概率。概率密度函数 `f(x[i])` 定义为随机变量 `X` 的取值位于由 `x[i]` 和 `x[i] + δx` 定义的无限小区间内的概率。相应的方程在 公式 4.9 中给出。累积分布函数 `F(a)` 是概率密度函数在 `X` = `a` 之下的面积（公式 4.10）。累积密度函数，正态变量，如 **图 4.4** 所示。

要计算股票收益小于或等于 0.02 的概率，可以使用累积分布函数来计算从极左点到 0.02 的分布面积。`pnorm()` 返回正态分布的累积分布。`pnorm` 中的参数 `lower.tail` 默认设置为 TRUE。这意味着计算的概率为 `P[X ≤ x]`。由于我们要查找收益大于 0.02 的概率，我们将设置 `lower.tail = FALSE`（意味着 `P[X > x]`）。

![](img/page105-02.png)

累积分布函数值表明葛兰素有 32% 的机会，而辉瑞只有 14% 的机会实现 2% 或更高的收益。

![](img/page105-03.png)

概率分布对统计学而言是基础，就像数据结构对计算机科学一样。除了已讨论的分布外，以下是一些其他重要的分布（Pradhan and Kumar, 2019）：

**1.** `Beta Distribution`：它是一种连续分布，其取值介于 0 和 1 之间。

**2.** `Gamma Distribution`：它被用作复杂的等待时间模型。我们可以使用 Gamma 分布来模拟下一个 `n` 次事件发生所需的时间。

**3.** `Weibull Distribution`：指数分布是 Weibull 分布的特例。在指数分布中，事件发生的速率是恒定的。但使用 Weibull 分布，我们可以对事件随时间变化的递增（或递减）发生速率进行建模。

**4.** `Geometric Distribution`：如果二项分布关乎‘有多少次成功？’，那么几何分布关乎‘在一次成功之前有多少次失败？’

## 4.8 | 中心极限定理

样本均值 ![](img/pageIn_ch4-01.png)由重复抽样得到，来自均值为 `m`、标准差为 `σ` 的总体，将服从均值为 ![](img/pageIn_ch4-02.png) 且标准差为 ![](img/pageIn_ch4-03.png) 的正态分布，样本量 `n` > 30 时。 从总体中抽取的不同样本的均值分布称为抽样分布。

让我们使用辉瑞股票数据的收盘价来演示中心极限定理。让我们绘制收盘价的密度图。

![](img/page106-01.png)

**图 4.5** 是辉瑞股票数据收盘价的密度图，似乎不是正态分布。让我们从 `pfizer_df` 计算收盘价的均值和标准差。平均收盘价为 28.065，标准差为 1.3452。

![](img/page106-02.png)![](img/page107-01.png)

让我们从 `pfizer_df` 抽取 500 个随机样本，每个样本 30 个观测值（收盘价），并将 500 个样本生成的收盘价平均值存储在 `samDist` 中：

![](img/page107-02.png)

接下来我们将计算样本均值和标准差。

![](img/page107-03.png)

我们可以从输出中推断出抽样分布的均值为 28.11，标准差为 1.3579。也就是说，中心极限定理在辉瑞股票数据上成立。一般来说，当重复抽样生成的样本 >30 时，中心极限定理对任何数据都成立。随着样本量的增加和重复样本数量的增加，样本均值将趋近于总体均值。

我们将绘制 `samDist`。

**中心极限定理** 是假设检验和许多其他统计学习算法技术的构建基石。

![](img/page107-04.png)

从 **图 4.6** 可以得出结论，样本均值近似服从正态分布。

## 4.9 | 假设检验

假设是一个主张。假设检验的目标是借助新收集的证据或样本来拒绝或保留原假设（现有知识或信念）。假设检验由两个互补的陈述组成，称为原假设和备择假设。原假设代表无关系或无差异（即代表现有知识或信念），而备择假设是我们打算用证据（样本）来建立的。备择假设也称为研究假设。假设检验大致分为参数检验和非参数检验。参数检验涉及分布的总体参数，如均值、比例、标准差等。非参数检验不涉及参数，而是涉及其他特征，如独立事件或数据服从某些分布（如正态分布）。原假设的一些示例如下：

![](img/page108-01.png)

**1.** 喝健康饮品 Complan（印度 Heinz 拥有的健康饮品）的儿童更有可能长得更高。

**2.** 女性比男性自拍更多（Freier, 2016）。

**3.** 素食者错过航班较少（Siegel, 2016）。

**4.** 吸烟者是更好的销售人员。

以下步骤用于假设检验（Kumar, 2017）：

**1.** 定义原假设和备择假设。在参数假设检验中，假设是用总体参数描述的，即均值、标准差等。通常，`H[0]` 用于表示原假设，`H[a]` 用于表示备择假设。

**2.** 确定用于检验原假设有效性的检验统计量，例如 `Z-test` 或 `t-test`。

**3.** 决定拒绝和保留原假设的标准。这称为显著性值或 `α`。`α` 通常使用的值为 0.05。

**4.** 计算 `p-value`（概率值），即在原假设为真时观察到检验统计量值的条件概率。我们将为此使用 `scipy.stats` 模块提供的函数。`P-value` 充当指标，较小的 `p-value` 表明存在反对原假设的有力证据。

**5.** 根据 `p-value` 和显著性值 `α` 决定拒绝或保留原假设。当 `p-value` 小于显著性值时，拒绝原假设。当 `p-value` 大于或等于显著性值时，保留原假设（未能拒绝）。

要详细了解假设检验，请参阅 U. Dinesh Kumar（2017）所著书籍 *商业分析：数据驱动决策科学* 的 第 6 章。

我们将使用以下符号：

**1.** `m` - 总体均值

**2.** `a` - 总体标准差

**3.** `X` - 样本均值

**4.** `S` - 样本标准差

**5.** `n` - 样本量

在接下来的几个部分中，我们将使用一些示例进行假设检验。

### 4.9.1 单样本 Z 检验

单样本 `Z-test` 用于以下情况：

**1.** 检验总体均值的值，当总体标准差已知时。

**2.** 总体为正态分布，对于大样本（`n` > 30），正态分布的假设可以放宽。

`Z-Statistic` 计算为

![](img/page109-01.png)

**例 4.1**




A passport office claims that passport applications are processed within 30 days of submitting all necessary documents. The file `passport.csv` **(表 4.11)** contains processing time of 40 passport applicants. The population standard deviation of the processing time is 12.5 days. Conduct a hypothesis test at significance level `α` = 0.05 to verify the claim made by the passport office.

![](img/page109-02.png)

**表 4.11** | 护照数据

| 处理时间 |
| --- |
| 16 |
| --- |
| 16 |
| 30 |
| 37 |
| 25 |
| 22 |

Let’s first define the hypothesis, if `m` is population mean, that is, mean processing time of passports, then:

**1.** `H[0]` : `µ` ≥ 30

**2.** `H[a]` : `µ` < 30

We will conduct a `Z`-test for this hypothesis test. `Z`-test is not available as a function in `r` base and thus below is the custom function to calculate the `Z` statistic value and corresponding `p-value`.

![](img/page109-03.png)![](img/page110-01.png)

As the `p-value` is more than 0.05, the null hypothesis is retained, that is, the mean processing time is more than 30 days.

In this example, we see there is a 6.77% probability of observing a random sample at least as extreme as the observed sample. Since 6.77% is greater than significance value 5%, there is not enough evidence to reject null hypothesis. The null hypothesis is retained, and it can be concluded that the average processing time of passports is greater than or equal to 30 days.

### 4.9.2 单样本检验
The one-sample `t`-test is used when the population standard deviation is unknown and is estimated from the sample. The `t`-statistic value is given by:

![](img/page110-02.png)

**例 4.2**

Aravind Productions (AP) is a newly formed movie production house based out of Mumbai, India. AP was interested in understanding the production cost for a Bollywood movie. The industry believes the production house will require at least INR 500 million (50 crore) on average. It is assumed that the Bollywood movie production cost follows normal distribution. Production costs of 40 Bollywood movies in millions of rupees are given in `bollywoodmovies.csv` file **(表 4.12).** Conduct an appropriate hypothesis test at `α` = 0.05 to check whether the belief about average production cost is correct.

![](img/page110-03.png)

Let’s first define the hypothesis, if `m` is population mean then:

**1.** `H[0]` : `/j`≤ 500

**2.** `H[a]` : `v` > 500

We will conduct a `t`-test for this hypothesis test using `t`-test function in `r` base.

![](img/page110-04.png)

**表 4.12** | 宝莱坞数据

| 生产成本 |
| --- |
| 601 |
| --- |
| 627 |
| 330 |
| 364 |
| 562 |
| 353 |

This returns −2.2845 value for `t`-statistics and 0.0278 for `p-value`. This implies the sample mean is less than (to the left of) population mean and has only a 2.7% probability of being part of the distribution with a population mean of 500. As `p-value` is less than 0.05, we can conclude that sample mean rejects that the production cost is at least 500.

### 4.9.3 双样本 t 检验
Two-sample `t`-test is used to test the difference between two population means, in which standard deviations of populations are unknown. The parameters are estimated from the samples.

**例 4.3**

A company makes a claim that children (in the age group 7 to 12) who consume their health drink will grow taller by 1.2 cm more compared to children who don’t. Data in **表 4.13** and **表 4.14** shows average increase in height over a 1-year period from two groups: one drinking the health drink, the other not doing so. At `α` = 0.05, test whether the increase in height for children who drink the health drink is different from those who do not.

Let’s read the files and calculate the average height of children in the two samples.

![](img/page111-01.png)

**表 4.13** | 保健饮料（是）

| 身高增长 |
| --- |
| 8.6 |
| --- |
| 5.8 |
| 10.2 |
| 8.5 |
| 6.8 |
| 9.4 |

![](img/page111-02.png)

**表 4.14** | 保健饮料（否）

| 身高增长 |
| --- |
| 5.3 |
| --- |
| 9.0 |
| 5.7 |
| 5.5 |
| 5.4 |
| 7.2 |

![](img/page112-01.png)

The height difference in the mean value of the two samples is 1.48. Let us perform a two-sample `t`-test to understand if they are statistically different. The hypothesis is

**1.** `H[0]`: The average increase in height for children who drink health drink is the same as the average increase in height for children who do not drink health drink, that is, `µ[diff]` = 0

**2.** `H[a]`: The average increase in height for children who drink health drink is different from the average increase in height for children who do not drink health drink, that is, `µ[diff]` ≠ 0

![](img/page112-02.png)

Since the `p-value` is less than the threshold (0.05), we reject the null hypothesis. Thus, the average increase in height for children who drink health drink is different from the average increase in height for children who do not drink health drink.

### 4.9.4 配对样本 t 检验
In many contexts, we would like to analyze whether an intervention (or treatment) such as training programs, marketing promotions, treatment for specific illness, and lifestyle changes may have significantly changed population parameter values such as mean before and after the intervention. The objective in this case is to check whether the difference in the parameter values is statistically significant before and after the intervention or between two different types of interventions. This is called paired sample `t`-test and is used to compare two different interventions applied on the same samples. Consider the following example for a paired `t`-test:

The file `breakups.csv` contains alcohol consumption before and after the break-up **(表 4.15).** Conduct a paired `t`-test to check whether alcohol consumption is more after the break-up at 95% confidence (`α` = 0.05).

![](img/page112-03.png)

**表 4.15** | 分手数据

| 分手前 || 分手后 |
| --- | --- |
| 470 || 408 |
| --- | --- |
| 354 || 439 |
| 496 || 321 |
| 351 || 437 |
| 349 || 335 |
| 449 || 344 |

![](img/page113-01.png)

The alcohol consumption difference in the two samples is 11.5. Let’s perform a paired two-sample `f-test` to understand if they are statistically different. The hypothesis is:

**1.** `H[0]`: The average alcohol consumption before break-up is same as the average alcohol consumption after break-up, that is, `µ[diff = 0]`

**2.** `H[a]`: The average alcohol consumption before break-up is not same as the average alcohol consumption after break-up, that is, `µ[diff]` ≠ 0

![](img/page113-02.png)

Since the `p-value` is more than the threshold (0.05), we retain the null hypothesis. There is no change in alcohol consumption pattern before and after break-up.

### 4.9.5 卡方拟合优度检验与独立性检验
Chi-square goodness of fit test is a non-parametric test used to compare the observed distribution of data with the expected distribution of data to decide whether there is any statistically significant difference between the observed distribution and a theoretical distribution. Chi-square statistics is given by (Kumar, 2017):

![](img/page113-03.png)

where, `O[i]` is observed frequency and `E[i]` is expected frequency of the `i`^(th) category. Expected frequency is calculated based on the hypothesized distribution. Chi-square of independence checks whether two variables dependent or independent **(例 4.4).**

**例 4.4**




Hanuman Airlines (HA) operated daily flights to several Indian cities. One of the hypotheses in catering operations is that food preferences of passengers from different zones in India are different. Captain Cook, the operations manager of HA, collected a sample of 2,500 passengers to analyze food preferences **（表 4.16）。**

Conduct a chi-square test to check whether food preferences are statistically different is true at `α = 0.05`.

![](img/page114-01.png)

Let us frame the null and alternate hypotheses:

**1.** `H[0]`: Food preference does not change with zone, that is, food preference and zone are independent.

**2.** `H[a]`: Food preference is dependent on the zone.

![](img/page114-02.png)

The expected values are computed and stored:

![](img/page114-03.png)

Using 公式 4.16, we can see that the expected number of cases for `Veg_North` should be `940*546/2500 = 205.30`. If we want to know the most contributing observation to the overall chi-square value, we can calculate chi-square statistics for each observation:

![](img/page114-04.png)

where `r` is the Pearson residual.

![](img/page114-05.png)![](img/page114-06.png)

A value of 2.9 suggests that South zone’s preference of vegetarian food is higher whereas they do not prefer diabetic food (−2.77). Let us see the final result:

![](img/page115-01.png)

The degree of freedom is calculated as `(row-1)*(col-1)`. In the `meals_df` we have four rows and as many columns. The `p`-value is less than 0.05, which implies that food preference is dependent on the zone.

## 4.10 | 方差分析（ANOVA）

Sometimes, it may be necessary to conduct a hypothesis test to compare mean values simultaneously for more than two groups (samples) created using a factor (or factors). For example, a marketer might desire to understand the impact of three different discount values (such as 0%, 10%, and 20% discount) on average sales (Kumar, 2017).

ONE-WAY ANOVA (Analysis of Variance) can be used to study the impact of a single treatment (also known as factor) at different levels (thus forming different groups) on a continuous response variable (or outcome variable). The null and alternative hypotheses for one-way ANOVA for comparing three groups are given by

**1.** `H[0]`: `μ[1]` = `μ[2]` = `μ[3]`

**2.** `H[A]`: Not all `m` values are equal

where `μ[1]`, `μ[2]`, `μ[3]` are mean of each group. Note that the alternative hypothesis, not all `μ` values are equal, implies that some of them could be equal. An important assumption of ANOVA test is that the data is normally distributed and the variance across groups is homogeneous.

### 例 4.5

Ms Rachael Khanna, the brand manager of ENZO detergent powder at the ‘one stop’ retail, was interested in understanding whether price discounts have any impact on the quantum of sales. To that end, discounts of 0% (no discount), 10%, and 20% were offered on randomly selected days. The quantity (in kilograms) of ENZO sold in a day under different discount levels is shown in **表 4.17.** Conduct a one-way ANOVA to check whether discount had any significant impact on the average sales quantity at `α = 0.05` (file name: `onestop.csv`).

![](img/page115-02.png)![](img/page115-03.png)

**表 4.18** | 一站式扁平化数据

| 折扣百分比 || 销售数量 |

| --- | --- |

| discount_0 || 39 |

| --- | --- |

| discount_0 || 32 |

| discount_0 || 25 |

| discount_0 || 25 |

| discount_0 || 37 |

| discount_0 || 28 |

The below code snippet flattens the **表 4.17** which results in **表 4.18:**

![](img/page116-01.png)

From the plot **（图 4.7）**, it seems the distributions are not same. But it is not conclusive, and only one-way ANOVA test will ensure if they are same or not. `aov()` conducts oneway ANOVA and returns `F`-statistics and `p`-value. Let us formulate the hypothesis:

**1.** `H[0]`: The average quantity sold is same for different discount percentage.

**2.** `H[a]`: The average quantity sold is different for different discount percentage.

If `p`-value is less than 0.05, the null hypothesis can be rejected, and we can conclude that the mean of each groups is not the same.

![](img/page116-02.png)

As `p`-value is less than 0.05, we reject the null hypothesis and conclude that mean sales quantity values under different discounts are different. However, we need to check if the assumption for ANOVA is satisfied. The residual vs. fitted plot can help check that assumption **（图 4.8）。**

![](img/page116-03.png)![](img/page117-01.png)![](img/page117-02.png)

From **图 4.9**, we see that solid line is close to the dotted horizontal line. Thus, we can conclude that the assumption of “homogeneity of variance” across different groups is satisfied. **图 4.9** shows that the dots are very close to the reference line, and thus normality of data is evident.

In case the assumption gets violated, we could have performed Welch one-way test (which relaxes this assumption). `oneway.test` from `stats` package can help implement one-way test when normal distribution assumption is not satisfied.

One-way ANOVA test can only suggest that some discount level leads to significant difference in the average quantity of detergent sold. But we do not know which pair of discount level leads to this change.

Since the ANOVA test is significant, we can compute Tukey HSD (Tukey Honest Significant Differences) for performing multiple pairwise-comparison between the means of groups. The function `TukeyHD()` from `stats` package can be used to perform pairwise comparison. It takes the fitted ANOVA as an argument.

![](img/page118-01.png)![](img/page118-02.png)

From the `p`-value, we can conclude that all three discounts lead to significant changes in the quantity of detergent sold.

## 摘要

The chapter introduced the basic concepts of probability distributions, its parameters, and how they can be applied in the real world to solve problems. Some of the distributions explored are normal distribution, exponential distribution, binomial and Poisson distribution, and their applications. The objective of hypothesis testing is to either reject or retain a claim with the help of evidences collected from samples. The existing belief is called null hypothesis and new claim is called alternative hypothesis in a hypothesis test. `Z`-test can be used when:

• the value of population mean and population standard deviation is known or

• sample size is large (`n > 30`) and population variance is known.

The `t`-test is used when the population standard deviation is unknown and is estimated from the sample. Chi-square goodness of fit tests are hypothesis tests that are used for comparing the observed distribution of data with expected distribution of the data to decide whether there is any statistically significant difference between the observed distribution and a theoretical distribution. Chi-square test of independence is used for checking independence between two variables.

## 练习

### 用 R 编写代码回答问题 1-8

**1.** The number of customers’ returns in a retail chain per day follows a Poisson distribution at a rate of 25 returns per day. Write code to answer the following questions:

(a) Calculate the probability that the number of returns exceeds 30 in a day.

(b) If the chance of fraudulent return is 0.05, calculate the probability that there will be at least 2 fraudulent returns in any given day.




## 2.
一名学生申请美国八所大学的研究生课程，并认为她在每所大学被录取的概率恒定且独立，为 0.42。编写代码回答以下问题：

### (a)
她收到至少三所大学录取通知的概率是多少？

### (b)
她收到恰好四所大学录取通知的概率是多少？

## 3.
机器的失效时间服从指数分布，其平均故障间隔时间（`MTBF`）估计为 85 小时。编写代码回答以下问题：

### (a)
计算系统在 85 小时前失效的概率。

### (b)
计算其在 150 小时内不会失效的概率。

## 4.
根据对约 10 英亩葡萄农田的 1,000 名葡萄种植农户使用农药的调查发现，葡萄农户每周平均喷洒 38 升农药，对应的标准差为 5 升。假设每周农药喷洒量服从正态分布。编写代码回答以下问题：

### (a)
有多少比例的农户每周喷洒农药超过 50 升？

### (b)
有多少比例的农户每周喷洒农药少于 10 升？

### (c)
有多少比例的农户每周喷洒农药在 30 升到 60 升之间？

## 5.
一台装瓶机将水灌入 5 升（5000 cm³）瓶中。公司希望检验零假设，即机器灌入瓶中的平均水量至少为 5000 cm³。随机抽取了 60 瓶机器生产出的瓶子并记录其确切含量。样本均值为 4,998.1 cm³。根据经验，已知总体标准差为 1.30 cm³。假设总体服从标准差为 1.30 cm³ 的正态分布。编写代码在 `a` 为 5% 时检验假设。解释结果。

## 6.
一家纺织品制造商希望了解其生产的纺织品的缺陷比例。其车间员工一直声称纺织品的缺陷百分比不超过 18%。他希望检验车间员工的说法是否正确。他随机抽取了 100 件纺织品，发现其中 22 件有缺陷。使用 `a` = 0.05 编写代码检验缺陷组件百分比小于 18% 的假设。

## 7.
假设 ABC 电池制造商希望证明其电池的平均使用寿命比竞争品牌长至少 60 分钟。从两个品牌各随机抽取 100 节电池的独立样本，并连续使用电池。ABC 样本平均寿命为 450 分钟。竞争品牌电池的平均寿命为 368 分钟，样本标准差分别为 82 分钟和 78 分钟。提出假设并编写代码在 95% 显著性水平下检验 ABC 的主张。

## 8.
一家培训机构希望检查其培训项目的有效性以及受训人员在培训后的成绩是否提高。抽取了 30 名学生的样本，并在培训前后计算了他们的成绩。文件 `frainingscores.csv` 包含培训前后学生的成绩。提出假设并编写代码检验该培训机构培训有效性的假设。

## Bibliography
1. Anon (2021), “辉瑞数据” available at [`in.finance.yahoo.com/quote/PFE`](https://in.finance.yahoo.com/quote/PFE)/, Yahoo Finance, accessed on 29 January 2021.
2. Anon (2021), “葛兰素数据” available at [`in.finance.yahoo.com/quote/GLAXO.NS`](https://in.finance.yahoo.com/quote/GLAXO.NS)/, Yahoo Finance, accessed on 29 January 2021.
3. Anon (2021), “R 文档”, Web Address: [`www.rdocumentation.org/packages/stats/versions/3.6.1`](https://www.rdocumentation.org/packages/stats/versions/3.6.1), accessed on 10 May 2021.
4. Kumar UD (2017), *“商业分析 - 数据驱动决策科学”,* Wiley, New Delhi.
5. Pradhan M and Kumar UD (2019), *“使用 Python 的机器学习”,* Wiley, Indian Institute of Management, Bangalore.

| 

## 监督学习算法：线性回归

 || 

## 5

 |

| --- | --- |

*在你的生活中冒险，如果你赢了，你可以引领；如果你输了，你可以指导。*

**—斯瓦米·维维卡南达**

## LEARNING OBJECTIVES

阅读本章后，你将能够：

• 了解简单线性回归和多元线性回归的概念及其在预测分析中的应用。
• 学习使用 `R` 中的 `caret` 包构建简单线性回归和多元线性回归模型。
• 学习执行诸如 1. 将数据集拆分为训练数据和验证数据，2. 使用 `R` 包在训练数据集上构建回归模型并在验证数据集上测试 等任务。
• 学习如何在回归模型中纳入分类（定性）变量。
• 了解使用 `t`-检验、`F`-检验和回归模型诊断的统计显著性；并执行诸如残差分析、识别异常值和有影响观测值 等任务。

## 5.1 | 简单线性回归

简单线性回归（`SLR`）是一种统计学习算法，用于寻找因变量（又称响应变量或结果变量）与自变量（又称解释变量、预测变量或特征）之间关联关系是否存在。利用 `SLR`，我们可以确定结果变量（`Y`）值的变化与特征 `X` 值变化相关。即回归技术不能用于建立两个变量之间的因果关系。它是预测分析中最受欢迎的监督学习算法之一。回归模型需要在训练数据集中同时了解结果变量和特征变量。下面列出了一些简单和多元回归问题的例子（Pradhan and Kumar, 2019）：
1. 医院可能有兴趣了解患者的总体治疗费用与其体重之间的关联。
2. 保险公司希望了解医疗费用与年龄之间的关联。
3. 产品产生的收入与价格、促销花费、竞争对手价格和促销费用等特征之间的关系。
4. 餐厅希望了解顾客下单后等待时间与收入之间的关系。
5. 亚马逊、BigBasket 和 Flipkart 等电子商务公司希望了解诸如 1. 客户访问其门户的次数、2. 产品点击次数、3. 促销商品数量和 4. 平均折扣百分比 等特征与结果变量收入之间的关联关系。
6. 银行和其他金融机构希望了解失业率、婚姻状况、银行账户余额、降雨量等变量对不良资产（NPA）百分比的影响。

## 5.2 | 回归模型构建步骤

构建回归模型使用的以下步骤。回归模型构建是一个迭代过程；在得出适当模型之前可能需要多次迭代（Kumar 2017；Pradhan and Kumar 2019）：
1. **步骤 1：收集/提取数据：** 构建回归模型的第一个步骤是从不同的数据源收集和/或提取因变量（结果变量）和自变量（特征变量）的数据。即使组织拥有设计良好的企业资源规划（`ERP`）系统，数据收集也可能耗时且昂贵。



## 第 2 步：预处理数据
在构建模型之前，确保数据在可靠性、完整性、有用性、准确性、缺失数据和异常值等方面质量至关重要。可以使用数据插补技术来处理缺失数据。描述性统计和可视化（例如箱线图和散点图）可用于识别数据集中异常值和变异性的存在。可以派生出许多新变量（例如变量的比率或乘积）（即特征工程）并用于模型构建。分类数据在使用回归模型之前必须使用虚拟变量进行预处理（特征工程的一部分）。请注意，在 R 中，一些算法（例如使用 `stats` 包中的 `lm()` 函数进行回归）会隐式执行虚拟变量编码。

## 第 3 步：将数据划分为训练集和验证数据集
在此阶段，数据被划分为两个子集（有时多于两个）：训练数据集和验证集或测试数据集。训练数据集的比例通常占数据的 70% 到 80%；剩余部分作为验证数据处理。子集可使用随机/分层抽样程序创建。这是在用于模型构建的数据之外衡量模型性能的重要步骤。检查模型的任何过拟合也很重要。在许多情况下，可以使用多个训练集和多个测试集（称为 k 折交叉验证）。

## 第 4 步：执行描述性分析或数据探索
在转向预测分析模型构建之前，执行描述性分析始终是一个良好的实践。描述性统计将帮助我们了解特征中的变异性以及数据的可视化，例如通过箱线图，可用于识别数据中是否存在异常值。另一种可视化技术散点图，也可能揭示所考虑的两个变量之间是否存在明显关系。散点图有助于描述因变量或结果变量与特征之间的函数关系。

## 第 5 步：构建模型
使用训练数据集构建模型以估计回归参数。使用普通最小二乘法 (`OLS`) 来估计回归参数。`OLS` 在本章后面会进行解释。

## 第 6 步：执行模型诊断
回归经常被误用，因为在应用模型之前往往没有进行必要的诊断测试。在应用之前，必须验证模型是否满足所有模型假设，包括结果变量与特征之间的函数形式定义。如果模型假设被违反，必须采取补救措施。

## 第 7 步：验证模型并衡量模型准确性
分析中的主要问题是过拟合，即模型在训练数据集中表现非常好，但在验证数据集中表现很差。确保模型在验证数据集中的性能与在训练数据集中一样一致非常重要。事实上，模型可以使用多个训练和测试数据集进行交叉验证。

## 第 8 步：决定模型部署
回归模型的最后一步是制定部署策略，以可操作的项目和业务规则的形式呈现，供组织使用。

## 5.3 | 构建简单线性回归模型
简单线性回归 (`SLR`) 是一种统计模型，其中只有一个自变量（特征），并且因变量与回归系数之间的函数关系是线性的（Kumar, 2017）。线性回归意味着函数相对于回归参数是线性的。结果变量与特征之间的关系可能是非线性的。`SLR` 的一种函数形式如下所示：

![](img/page123-01.png)

对于具有 `n` 个观测值 (`X[i]`、`Y[i]`) 的数据集，其中 `i` = 1, 2, `n`，上述函数形式可以写成如下形式：

![](img/page123-02.png)

在 公式 (5.2)

1. `Y[i]` 是样本中因变量（结果变量）第 `i`^(th) 个观测值的值。
2. `X[i]` 是样本中自变量或特征变量第 `i`^(th) 个观测值的值。
3. `ϵ[i]` 是预测 `Y[i]` 值时的随机误差（也称为残差）。
4. `β[0]` 和 `β[1]` 是回归参数（或回归系数）。

公式 (5.2.) 中所述的回归关系是一种统计关系，因此不像数学关系那样精确，因此存在误差项 `e[;]`。 公式 (5.2) 可以写成

![](img/page123-03.png)

通过最小化误差平方和 (`SSE`) 来估计回归参数 `β[0]` 和 `β[1]`。

![](img/page123-04.png)

通过对 `SSE` 关于 `β[0]` 和 `β[1]` 求偏导数并求解方程，我们得到 `β[0]` 和 `β[1]` 的估计值。

![](img/page123-05.png)![](img/page123-06.png)

其中 ![](img/pageIn_ch5-01.png) 和 ![](img/pageIn_ch5-02.png) 是回归参数 `β[0]` 和 `β[1]` 的估计值。上述过程称为普通最小二乘法 (`OLS`)。使用 `OLS` 的估计给出回归参数的最佳线性无偏估计 (`BLUE`)。我们也可以通过将 公式 (5.1) 重写为矩阵形式来估计 ![](img/pageIn_ch5-03.png) 和 ![](img/pageIn_ch5-04.png)

![](img/page124-01.png)

公式 (5.7) 可以写成

![](img/page124-02.png)

公式 (5.8) 可以写成

![](img/page124-03.png)

其中 ![](img/pageIn_ch5-05.png) 是表示 ![](img/pageIn_ch5-06.png) 和 ![](img/pageIn_ch5-07.png) 的向量。

以下是线性回归模型的假设（Kumar, 2017）。

1. 误差或残差 `ϵ[i]` 假定服从正态分布，误差的期望值 `E(ϵ[i])` = 0。
2. 误差的方差 `VAR(e[;])` 对于自变量 `X` 的不同取值是恒定的，称为同方差性。当方差不恒定时，称为异方差性。
3. 误差与自变量不相关。
4. 结果变量与特征之间的函数关系定义正确。

以下是简单线性回归的性质（Kumar, 2017）：

1. 给定 `X[i]` 时，`Y[i]` 的均值由 ![](img/pageIn_ch5-08.png) 给出
2. `Y[i]` 是均值为 ![](img/pageIn_ch5-09.png) 且方差为 `VAR(ϵ[i])` 的正态分布。

## 5.4 | 示例：根据 10 年级成绩预测 MBA 薪资
表 5.1 包含 2016 年某商学院 50 名毕业 MBA 学生的薪资及其在 10 年级对应的百分比成绩（文件名：`MBA Salary.csv`）。我们将开发一个简单线性回归 (`SLR`) 模型，以了解并根据 10 年级的成绩百分比预测薪资（Kumar, 2017）。

#### 使用 R 构建回归模型的步骤
1. 导入 `stats` 和 `caret` 包。
2. 将数据集加载到 `dataframe` 中。
3. 确定并设置用于建模的 `X`（特征）和 `Y`（结果）变量。
4. 将数据集拆分为训练集和验证集。
5. 使用 `OLS()` 方法构建回归模型。
6. 打印模型摘要并进行模型诊断。

### 5.4.1 安装包
让我们首先使用 `stats` 包中的 `read.csv()` 加载 `MBA Salary.csv` 数据集，然后按照构建回归模型的步骤进行。然而，在使用 `stats` 和 `caret` 包的函数之前，请确保该包已安装在您的计算机中。




![](img/page125-01.png)![](img/page125-02.png)![](img/page126-01.png)

### 5.4.2 数据导入与操作

收集的数据存储在一个 csv 文件中。`read.csv` 函数用于从当前工作目录读取数据集。如果你不确定文件将从哪个当前工作目录读取，可以使用

1. `getwd()` 函数获取你的工作目录和
2. `setwd()` 函数设置你的工作目录。

默认情况下，`read.csv` 文件仅期望文件名路径。然而，此外，我们还使用了另外两个参数：
1. `na.strings()` 用于在数据集中存在空白或 NA 的地方嵌入 `NA`。空白或 NA 值使用 `c("", " ", "NA")` 找到。此操作之所以执行，是因为 R 将 `NA` 识别为缺失值而不是空白。此嵌入 `NA` 的操作也可以在数据作为 `data.frame` 加载后执行。然而，在读取数据集时执行此步骤更容易。
2. `check.names()` 检查语法上正确的名称。如果列名中存在空白，它会在空白处嵌入一个 ‘.’。在下面的代码中，我们通过将 `check.names()` 设置为 FALSE 来覆盖它，然后使用 `gsub()` 替换列名中的空白。 表 5.2 显示了使用 `read.csv()` 方法读取的数据集。

![](img/page126-02.png)

我们现在可以使用下面的代码块查看数据的类型和描述性统计。`str()` 函数显示 `mba_salary_df` 有 50 个观测值，跨三个变量。变量为 `Sl_No`、`Percentage_in_Grade_10` 和 `Salary`。

![](img/page126-03.png)![](img/page127-01.png)

表 5.3 使用 `summary()` 函数生成。它汇总了数据框中的所有变量。在进一步分析之前，我们将从变量列表中删除 Sl. No.。

下面的代码块使用列子集删除数据框的第一列并创建新的 `new_mba_df`（表 5.4）。

![](img/page127-02.png)

在上面的代码块中，我们还使用 `na.omit` 函数执行了按行删除缺失值的额外任务。请注意，在加载数据时嵌入 `NA` 的使用是为了实现此步骤，即在任一列中没有数据可用时删除行。在 `new_mba_df` 中，此步骤不会删除数据框中的任何观测值，因为没有缺失值。然而，在处理存在缺失信息的数据集时，此步骤很有用。

*应注意，按行删除缺失值应在尝试使用插补技术填补缺失情况之后进行。*

![](img/page127-03.png)

**表 5.4** | 清洁的 MBA 数据

| Percentage\_in\_Grade\_10 || Salary |
| --- | --- |
| 62.00 || 270,000 |
| --- | --- |
| 76.33 || 200,000 |
| 72.00 || 240,000 |
| 60.00 || 250,000 |
| 61.00 || 180,000 |
| 55.00 || 300,000 |

### 5.4.3 创建特征集(x) 和结果变量 (Y)

让我们编写一个通用函数从数据集中提取预测变量和响应变量。

![](img/page128-01.png)

### 5.4.4 创建训练集和验证集

`caret` 包中的 `createDataPartition()` 函数提供了将数据集随机拆分为训练集和验证数据集的能力。
1. 该函数期望传递一个向量，在我们的例子中，我们将名为 `salary` 的一个变量传递给它。
2. 它还期望进入训练集的数据百分比，我们将其设置为 0.80。
3. 最后，通过将 `list` 标记为 `FALSE`，我们期望 `train_index` 包含一个矩阵，其行数等于 `floor(0.80 * length(Salary))` 乘以列数，即 2。

然而，即使在调用 `createDataPartition()` 之前，我们也使用了 `set.seed()` 函数来保持结果的可重复性和可再现性。在执行任何涉及随机划分或随机生成数字的操作之前，这是一个重要步骤。

*我们鼓励读者在下面的代码中注释掉 sef.seed 函数。观察每次执行时进入 `train` 和 `test` 数据框的记录。*

![](img/page128-02.png)

### 5.4.5 模型构建：使用 Caret 包

可以使用 `caret` 包构建许多模型。然而，需要注意的是，除了具有特定函数外，`caret` 是一个包装包。这意味着 `caret` 包的开发者设计了一个通用的建模框架，该框架调用其他 R 包中的不同函数。

![](img/page129-01.png)

1. 要实现线性回归，可在 `caret` 包中使用的方法是 `lm()`。然而，`lm()` 函数构建在 `stats` 包下。但通过 `caret` 包，我们可以调用 `lm()` 方法并开发回归模型。
2. 要实现随机森林，可在 `caret` 包中使用的其中一种方法是 `rf()`。然而，`rf()` 函数构建在 `randomForest` 包下。但通过 `caret` 包，我们可以调用 `rf()` 方法并开发随机森林模型。

下面的代码块给出了通过 `caret` 包实现的所有方法名称。

表 5.5 显示了 `caret` 包中的前 100 种方法。

![](img/page129-02.png)

该列表非常庞大，人们可能不了解上面列出所有方法的用途。因此，要获取特定方法的详细信息，我们可以运行下面的代码块。下面的代码显示 `lm` 方法用于构建回归模型。

![](img/page130-01.png)

使用 `caret` 包开发模型的标准化方式有三个主要组成部分。这些组件试图简化建模和评估过程。

1. `trainControl()`：此组件试图控制模型训练环境。`trainControl` 函数中的 `method` 参数提供了在模型构建前应用各种采样技术的很大灵活性。目前包含的一些重采样策略有 ‘boot’、‘cv, ‘LOOCV’、‘LGOCV, ‘repeat-edcv’、‘timeslice’、‘none’ 和 ‘oob’。除了 `method` 参数外，还可以传递多个其他参数，但大多数是可选参数且具有默认值。完整的参数列表及其默认设置如下所示（Anon, 2020）：

```
trainControl(method = ‘boot’, number = ifelse(grepl(‘cv’, method), 10, 25), repeats = ifelse(grepl(‘cv’, method), 1, number), p = 0.75, search = ‘grid’,initialWindow = NULL, horizon = 1, fixedWindow = TRUE, verboseIter = FALSE, returnData = TRUE, returnResamp = ‘final’, savePredictions = FALSE, classProbs = FALSE, summaryFunction = defaultSummary, selectionFunction = ‘best’, preProcOptions = list(thresh = 0.95, ICAcomp = 3, k = 5) , sampling = NULL, index = NULL, indexOut = NULL, indexFinal = NULL, timingSamps = 0, predictionBounds = rep(FALSE, 2), seeds = NA, adaptive = list(min = 5, alpha = 0.05, method = ‘gls’, complete = TRUE), trim = FALSE, allowParallel = TRUE)
```

表 5.6 显示了 `trainControl` 函数的各个参数的描述。对于高级机器学习中的模型微调，可能需要更改 表 5.6 中显示的一些参数的默认值。为了线性回归的目的，我们将 `method` 设置为 none 并继续。

2. `train()`：`train` 函数可用于
• 使用重采样评估模型调参参数对性能的影响。
• 在这些参数中选择“最优”模型。
• 从训练集估计模型性能。

下面是 `train` 函数的结构以及可以传递给 `train` 函数的参数列表




`train(x, y, method = ‘rf’, preProcess = NULL,..., weights = NULL,metric = ifelse(is.factor(y), ‘Accuracy’, ‘RMSE’), maximize = ifelse(metric %in% c(‘RMSE’, ‘logLoss’), FALSE, TRUE), trControl = trainControl(), tuneGrid = NULL, tuneLength = 3)`

表 5.7 显示了 `train` 函数的各个参数的描述。

### 3. `expand.grid()`
这是一个用于微调机器学习算法某些超参数的高级函数。`expand.grid()` 函数内部的参数根据模型而变化。¹

## 表 5.6 | `trainControl()` 函数参数列表 (Anon, 2019, 2020, 2021; Source: https://www.rdocumentation.org/)

| 参数 | 定义 |
|---|---|
| `method` | 重采样方法：‘boot, ‘boot632, ‘cv’, ‘repeatedcv’, ‘LOOCV’, ‘LGOCV’（用于重复的训练/测试分割），‘none’（仅将一个模型拟合到整个训练集），‘oob’（仅适用于随机森林、袋装树、袋装 earth、袋装灵活判别分析或条件树森林模型），‘adaptive_cv’、‘adaptive_boot’ 或 ‘adaptive_LGOCV’ |
| `number` | 表示折数或重采样迭代次数 |
| `repeats` | 仅用于重复 k 折交叉验证：要计算的完整折集合的数量 |
| `verboseIter` | 用于打印训练日志的逻辑值。 |
| `returnData` | 用于保存数据的逻辑值 |
| `returnResamp` | 一个字符字符串，指示应保存多少重采样汇总指标。值可以是‘final、‘all 或 ‘none’ |
| `savePredictions` | 指示应保存每个重采样的保留预测的多少。值可以是‘all、‘final’ 或 ‘none’。也可以使用逻辑值，转换为‘all’（对于 true）或 ‘none’（对于 false）。‘final’ 保存最优调参的预测。 |
| `P` | 用于留组交叉验证：训练百分比 |
| `search` | ‘grid’ 或 ‘random’，描述调参网格的确定方式。 |
| `initialWindow, horizon, fixed-Window` | 创建时间切片的可能参数 |
| `classProbs` | 一个逻辑值；在每次重采样中是否应为分类模型计算类别概率（连同预测值）？ |
| `summaryFunction` | 用于计算重采样间性能指标的函数。函数的参数应与 defaultSummary 中的相同。 |
| `selectionFunction` | 用于选择最优调参的函数。可以是函数名称或函数本身。有关详细信息和其他选项，请参阅 best。 |
| `preProcOptions` | 要传递给 preProcess 的选项列表。预处理的类型（例如，中心化、缩放等）通过 train 中的 preProc 选项传入。 |
| `sampling` | 描述重采样后进行的额外采样类型的单个字符值（通常用于解决类别不平衡）。值包括‘none’、‘down’、‘up’、‘smote’ 或 ‘rose’。后两个值分别需要 DMwR 和 ROSE 包。此参数也可以是列表以便于自定义采样，详细信息可在 caret 包网站的采样（下方链接）中找到。 |
| `index` | 具有每个重采样迭代元素的列表。每个列表元素是对应于该迭代中用于训练的行整数向量。 |
| `indexOut` | 一个列表（与 index 长度相同），指定每个重采样保留的数据（以整数表示）。如果为 NULL，则使用不包含在 index 中的唯一样本集。 |
| `indexFinal` | 一个可选的整数向量，指示重采样后用于拟合最终模型的样本。如果为 NULL，则使用整个数据集。 |
| `timingSamps` | 将用于测量预测样本时间的训练集样本数（零表示不应估计预测时间。 |
| `predictionBounds` | 一个逻辑值或长度为 2 的数值向量（仅回归）。如果为逻辑值，预测可以被限制在训练集结果的范围内。例如，值 c(TRUE, FALSE) 仅限制预测的下端。如果为数值，可以使用特定边界。例如，如果为 c(10, NA)，低于 10 的值将被预测为 10（上侧无约束）。 |
| `seeds` | 一组可选的整数，将在每次重采样迭代时用于设置种子。当模型并行运行时很有用。NA 值将阻止在工作进程中设置种子，而 NULL 值将使用一组随机整数设置种子。或者，可以使用列表。列表应有 B+1 个元素，其中 B 是重采样次数，除非 method 为 ‘boot632’，此时 B 为重采样次数加 1。列表的前 B 个元素应为长度为 M 的整数向量，其中 M 为正在评估的模型数。列表的最后一个元素只需要一个整数（用于最终模型）。 |
| `adaptive` | 当 method 为 ‘adaptive_cv、‘adaptive_boot 或 ‘adaptive_LGOCV’ 时使用的列表。 |
| `trim` | 一个逻辑值。如果为 TRUE，object$finalModel 中的最终模型可能会删除对象的某些组件以减小保存对象的大小。predict 方法仍可工作，但模型的某些其他功能可能无法使用。修剪仅在已实现此功能的模型中进行。 |
| `allowParallel` | 如果已加载并可用的并行后端，函数是否应使用它？ |

## 表 5.7 | 训练函数参数列表 (Anon 2019, 2020, 2021; Source: https://www.rdocumentation.org/)

| 参数 | 描述 |
|---|---|
| `x` | 一个对象，其中样本在行中，特征在列中。这可以是简单的矩阵、数据框或任何其他类型（例如稀疏矩阵）。 |
| `y` | 一个包含每个样本结果的数值或因子向量。 |
| `weights` | 案例权重的数值向量。此参数仅影响允许案例权重的模型。 |
| `…` | 传递给分类或回归例程的参数（如 randomForest）。如果在此处传递调参的值，将会出错。 |
| `preProcess` | 定义预测变量数据预处理的字符串向量。当前可能性包括‘BoxCox’、‘YeoJohnson、‘expoTrans、‘center、‘scale’、‘range’、‘knnImpute、‘bagImpute、‘medianImpute’、‘pca’、‘ica 和 ‘spatialSign’。默认无预处理。有关程序及如何调整，请参阅 preProcess 和 trainControl。预处理代码仅设计用于 x 为简单矩阵或数据框时。 |
| `metric` | 指定将用于选择最优模型的汇总指标的字符串。默认情况下，可能的值为回归的‘RMSE’和‘Rsquared’以及分类的‘Accuracy’和‘Kappa’。如果使用自定义性能指标（通过 trainControl 中的 summaryFunction 参数），metric 的值应与其中一个参数匹配。如果不匹配，将发出警告并使用 summaryFunction 给出的第一个指标。（注意：如果给出，此参数必须命名。） |
| `maximize` | 一个逻辑值：指标应最大化还是最小化？ |
| `trControl` | 定义此函数行为的值列表。参阅 trainControl 和 http://topepo.github.io/caret/training.html#custom。（注意：如果给出，此参数必须命名。） |
| `tuneGrid` | 包含可能调参值的数据框。列名与调参参数相同。使用 getModelInfo 获取每个模型的调参参数列表，或参阅 http://topepo.github.io/caret/available-models.html。（注意：如果给出，此参数必须命名。） |



| `tuneLength` || 一个表示调参网格精细程度的整数。默认情况下，此参数是 `train` 应生成的每个调参参数的水平数。如果 `trainControl` 的选项为 `search = 'random'`，则这是随机搜索将生成的调参组合的最大数量。（注意：如果给出，此参数必须命名。） |

上述三个函数的调用按 `expand.grid()`、`trainControl()` 和 `train()` 的顺序进行。算法步骤如下²：

**1.** 在 `expand.grid()` 中定义要评估的模型参数值集合。对每个参数，设置 **执行：**

• 对 `trainControl()` 中的每次重采样迭代 **执行：**

**1.** 保留特定样本。

**2.** \[可选\] 使用 `train()` 预处理数据。

**3.** 使用 `train()` 在剩余数据上拟合模型。

**4.** 预测保留样本。

• 计算保留预测的平均性能

**2.** 确定最优参数集。

**3.** 使用最优参数集在训练数据上拟合最终模型。

`caret` 包是一个包装包，提供了一个标准化的框架来实现大多数高级机器学习算法。

对于简单和多元线性回归，唯一需要微调的超参数是 `b[0]`，即建立带常数项或不带常数项的模型。我们可以使用 `modelLookup` 检查是否可以使用 `caret` 包微调模型参数。

函数 `expand.grid()`、`trainControl()` 和 `train()` 可用于实现各种采样策略以及应用不同的机器学习算法。

![](img/page133-01.png)

本章我们将不使用 `expand.grid()`。我们还将在 `trainControl()` 函数中设置 `method='none'`。

![](img/page133-02.png)

### 5.4.6 估计回归系数

在了解了 `caret` 包的方法后，让我们深入探讨 R 中回归系数是如何估计的。我们从 式 (5.9) 知道，我们可以使用正规方程法求解 ![](img/pageIn_ch5-10.png)。在 R 中，可以使用两个函数求解，即 `crossprod()` 和 `solve()`。

**1.** `crossprod()`：给定矩阵 `X` 和 `Y` 作为参数，`crossprod()` 返回矩阵叉积。这等价于调用 `t(X) %*% Y`。`t(X)` 表示转置矩阵 `X`。如果参数 `Y` 留空，函数将 `Y` 取为与 `X` 相同的矩阵，即函数将计算 `X^T X`。

**2.** `solve()`：像 式 (5.9) 这样的方程组可以使用此函数求解。因此 ![](img/pageIn_ch5-11.png)可以求解 ![](img/pageIn_ch5-12.png)，其中 `Y` 可以是向量或矩阵。如果 `Y` 缺失，则 `Y` 被视为单位矩阵，`solve` 将返回 `X` 的逆。

因此，[式 \[5.9\]](#13_Chapter05.xhtml#eq5.9) 可以通过调用求解

![](img/page133-03.png)

然而，如果特征数量很大，`solve()` 在数值上是不稳定的。因此，使用 QR 分解将变量矩阵 `X` 分解为正交矩阵 `Q` 和非奇异上三角矩阵 `R.` 然后使用 QR 矩阵来估计 ![](img/pageIn_ch5-13.png)正规方程法中的参数。

将 `X = QR` 代入 [式 \[5.8\]](#13_Chapter05.xhtml#eq5.8) 得到

![](img/page133-04.png)

重写 [式 \[5.10\]](#13_Chapter05.xhtml#eq5.10) 得到

![](img/page133-05.png)

利用 `Q^T Q = I` 的事实，我们得到 式 (5.12) 为

![](img/page133-06.png)

将 式 (5.12) 的两边乘以 `(R^T)^(-1)` 得到

![](img/page133-07.png)

因此，[式 \[5.13\]](#13_Chapter05.xhtml#eq5.13) 变为

![](img/page133-08.png)

由于 `R` 是上三角矩阵，[式 \[5.14\]](#13_Chapter05.xhtml#eq5.14) 可以通过使用函数 `backsolve(R, crossprod(Q,Y))` 轻松求解 ![](img/pageIn_ch5-14.png)。

实际上，`caret` 包中 `method=lm` 的 `train()` 函数使用上述描述的 QR 分解技术来获得参数的 OLS 估计，并将模型信息返回到对象 `mba_reg_model` 中。`train()` 函数返回的对象包含 `β` 的估计值、准确度度量和残差值等详细信息。

![](img/page134-01.png)

可以使用 `summary()` 对 `mba_reg_model` 对象来打印估计参数。

![](img/page134-02.png)

估计模型可以写为

**MBA 薪资 = 61234 + 3106 *（10 年级百分比）**

该方程可以解释如下：10 年级百分比每增加一个单位，MBA 学生的薪资平均将增加 3,106 个单位。

## 5.5 模型诊断

在模型用于实际应用之前，验证回归模型以确保其有效性和拟合优度非常重要。以下度量用于验证简单线性回归模型（Kumar, 2017）：

**1.** 决定系数（R 平方）。

**2.** 假设检验以检查回归系数的统计显著性。

**3.** 方差分析用于整体模型有效性（更适用于多元线性回归）。

**4.** 残差分析以验证回归模型假设，如正态性和同方差性。

**5.** 异常值分析。

### 5.5.1 决定系数（R 平方或 R²）

回归的主要目标是利用 `X` 的知识解释 `Y` 的变化（Kumar, 2017）。决定系数（或 `R`-square 或 `R²`）衡量模型（`β[0]` + `β[1]` `X`）解释的 `Y` 变化的百分比。简单线性回归模型可以分解为模型解释的变化和未解释的变化，如 式 (5.15) 所示：

![](img/page135-01.png)

总变化、解释变化和未解释变化之间的关系如下：

![](img/page135-02.png)

可以从数学上证明，总变化的平方和等于解释变化的平方和加上未解释变化的平方和（证明请参阅 Kutner *et al.* (2013)，第 65 页）：

![](img/page135-03.png)

其中 `SST` 是总变化的平方和，`SSR` 是回归模型引起的解释变化的平方和，`SSE` 是未解释变化的平方和。决定系数（`R` square）由下式给出

![](img/page135-04.png)

决定系数（`R` square）具有以下性质（Kumar, 2017）：

**1.** `R` 平方的值介于 0 和 1 之间。

**2.** 从数学上讲，`R` 平方（`R²`）是相关系数的平方（`R²` = `r²`），其中 `r` 是 Pearson 相关系数。

**3.** `R` 平方越高表示拟合越好。然而，应注意虚假关系。

### 5.5.2 回归系数的假设检验

回归系数（`β[1]`）捕捉结果变量与特征之间线性关系的存在。如果 `β[1]` = 0，我们可以得出两个变量之间不存在统计显著的线性关系。可以证明 `β[1]` 的抽样分布是 `t` 分布（Kutner et al. 2013, Kumar, 2017）。原假设和备择假设为

![](img/page135-05.png)

相应的检验统计量由下式给出

![](img/page135-06.png)

回归系数估计的标准误差由下式给出

![](img/page136-01.png)

其中 `S[e]` 是 `Y[i]` 估计值的标准误差和残差，由下式给出

![](img/page136-02.png)



假设检验是双尾检验。 公式 (5.19) 服从自由度为 `n` - 2 的 `t` 分布（由于估计两个回归参数 `β[0]` 和 ![](img/pageIn_ch5-15.png) 而损失了两个自由度），是回归系数的标准误差。

### 5.5.3 回归分析中的方差分析（ANOVA）
我们可以在具有 `k` 个特征的多元线性回归模型的情况下使用 ANOVA 来检验回归模型的整体有效性。 零假设和备择假设由 (Kumar, 2017) 给出：
![](img/page136-03.png)
对应的 `F` 统计量由 给出
![](img/page136-04.png)
其中 `MSR (= SSR/k)` 和 `MSE (= SSE/(n - k - 1))` 分别是均方回归和均方误差。 `F` 检验用于检验整体回归模型是否具有统计显著性。

### 5.5.4 模型诊断：回归模型摘要
回归模型摘要帮助我们验证上述模型诊断。
![](img/page136-05.png)
从摘要输出显示，我们可以推断出以下内容：
**1.** 模型的 `P` 方值是 0.1344；即 13.4% 的薪资变异由模型解释。
**2.** `t` 检验的 `p` 值是 0.01562，这表明特征 **十年级百分比** 与 **薪资** 之间存在统计显著关系。
**3.** 此外，模型的 `F` 统计量的概率值是 0.01562，这表明整体模型具有统计显著性。
请注意，在简单线性回归中，`t` 检验和 `F` 检验的 `p` 值将相同，因为假设相同（`F` = `t`²）。

### 5.5.5 残差分析
残差或误差是结果变量的实际值与预测值之间的差异。 残差（误差）分析对于检验回归模型假设是否得到满足很重要。 它用于检验以下内容 (Kumar, 2017)：
**1.** 残差呈正态分布。
**2.** 残差的方差恒定（同方差性）。
**3.** 回归的函数形式被正确指定。

### 残差正态分布的检验（正态 Q_Q 图）
残差的正态性可以使用分位数-分位数图（`Q-Q plot`）或 P-P 图（概率-概率图）来检验。 `Q-Q plot` 将两个概率分布的累积分布函数相互比较（Kumar, 2017）。 在当前背景下，我们使用 `Q-Q plot` 来检验残差的分布是否与正态分布相匹配。 图中的对角线代表正态分布的累积分布。
回归对象 `model` 的 `plot()` 生成 `Q-Q plot`。 该图显示误差是否呈正态分布。 在正态分布的情况下，点应接近对角线，偏差不大。

### 同方差性检验（Scale-Location 图）
回归模型的一个重要假设是残差在预测值（`Y`）的不同取值下具有恒定方差（同方差性）。 这可以通过绘制残差图来观察，该图是在标准化残差与标准化预测值之间绘制的。 如果存在异方差性（残差方差非恒定），则在特征变量为连续时残差图可能出现漏斗形。 残差的非恒定方差称为异方差性。
回归对象 `model` 的 `plot()` 给出 Scale-Location 图。 它显示残差是否在特征值的范围内均匀分布。 理想情况下应看到一条水平直线，点随机分布。 这是一种目视检查，即使直线不完全水平但点不显示任何特定形状，假设在实际目的上也可认为得到满足。

### 回归的函数形式（残差与拟合值）
预测变量（`X`s）与结果变量（`Y`）之间可能存在非线性关系。 这种非线性关系可能在 **残差与拟合值图** 中显示出来，该图使用回归对象的 `plot()` 生成。 理想情况下应看到一条水平直线，点随机分布。 这是一种目视检查，即使直线不完全水平但点不显示任何特定形状，假设在实际目的上也可认为得到满足。 **图 5.1** 绘制了本节讨论的诊断指标。
![](img/page138-01.png)![](img/page138-02.png)
对于 MBA 薪资预测，残差图可解释为：
**1.** 从残差与拟合值来看，我们可以得出回归的函数形式被正确指定。
**2.** 从 `Q-Q plot` 来看，我们可以得出残差遵循近似正态分布（我们只需要近似正态分布）。
**3.** 从 Scale-Location 图来看，残差是随机的且没有漏斗形状，这意味着它们具有恒定方差（同方差性）。
**4.** 从残差与杠杆值来看，可以观察到没有观测值落在 Z 分数 3 之外。 然而，观测值编号 9、16 和 25 似乎具有较高的杠杆值或较高的 Cook 值。 杠杆值和 Cook 值将在下一节讨论。
当数据点超过 Cook 距离的截止分数并位于残差与杠杆值图的右上角或右下角（Cook 距离为 0.5 及以上）时，这样的点可标记为对回归结果有影响。 如果从训练集中排除此类情况，回归结果将被改变。 在 **图 5.1** 中，没有任何观测值位于残差与杠杆值图的右上或右下。

### 5.5.6 异常值分析
异常值是其值与均值偏差较大的观测值。 异常值的存在会对回归系数值产生显著影响。 因此，识别数据中异常值的存在非常重要（Kumar, 2017）。
以下距离度量有助于识别异常观测值：
**1.** 异常值 - Z 分数
**2.** 高杠杆值 - 杠杆值
**3.** 有影响的 - Cook 距离

### 异常值 - Z 分数
`Z` 分数是观测值与其均值的标准化距离。 对于因变量 `Y` 的预测值，Z 分数由 (Kumar, 2017) 给出为
![](img/page139-01.png)
其中
![](img/pageIn_ch5-16.png) 是第 `i^(th)` 个观测值的 `Y` 的预测值，
`Y[i]` 是 `Y` 的实际值， 且
`σ[Y]`- `Y` 的标准差。
绝对值大于 3 的 Z 分数的任何观测值都可能被标记为异常值。

### 杠杆值
回归线可能受 `Y` 中的极值（异常值）或 `X` 中极值的数据点（高杠杆值）的影响。 观测值的杠杆值衡量该观测值对回归函数整体拟合的影响，并与马哈拉诺比斯距离相关。 该统计量以 `.hat` 即帽值保存在回归模型对象中。 `.hat` 值大于 `3(p + 1)/n` 的观测值被视为高度有影响的观测值，其中 `p` 是模型中的特征数，`n` 是样本量。
回归对象 `model` 的 `plot()` 给出残差与杠杆值图。 在图中，寻找右上角或右下角的异常值。 高杠杆情况将在同一图中突出显示，并对这些情况标记编号。

### Cook 距离和 DFBETA



即使数据存在极值，也可能不足以改变回归系数。反之，一些案例即使看起来不是异常值（极值），也可能非常有影响力。有影响力的案例由 Cook 距离识别，它结合了观测值的杠杆和残差信息。

Cook 距离衡量当某个观测值从样本中排除用于估计回归参数时，样本中所有观测值的因变量预测 `y` 值平均变化的程度。该统计量在回归模型对象中保存为 `.cooksd`。

`DFBETA` 是衡量有影响力案例的另一个统计量，确定如果删除相关观测值，参数估计会变化多少。

构建预测模型时，Cook 距离可能更为重要，而 `dfbeta` 在解释性建模中更为重要。

经验法则是，如果 `.cooksd` 超过 `4/(n - p - 1)`（Bruce and Bruce, 2017），则观测值具有高度影响力，其中 `n` 是观测值数量，`p` 是预测变量数量。然而，普遍共识是 Cook 距离值大于 1 表示高度有影响力的观测值，但大于 0.5 的值也应重新审视。

**图 5.2** 绘制 Cook 距离以可视化本节讨论的诊断指标。

![](img/page139-02.png)![](img/page139-03.png)

在讨论多元线性回归时，我们将重新审视残差和异常值分析图，并构建逻辑以突出违反模型诊断阈值的观测值。

## 5.6 | 做出预测并衡量准确性

理想情况下，预测应在验证（或测试）数据上进行，并应评估预测的准确性（Pradhan and Kumar, 2019）。

`predict()` 用于在新数据集上获取预测响应（Roshan, 2020）。如果测试数据包含训练集中不存在的新水平，则可能会收到错误消息。这通常发生在数据具有多个水平分类变量时。**表 5.8** 显示了预测值（`fit`）、下限（`lwr`）和上限（`upr`）。

![](img/page140-01.png)

### 5.6.1 寻找 R-Squared 和 RMSE

可以采用多种指标来衡量预测的准确性。均方误差（`MSE`）、均方根误差（`RMSE`）和平均绝对百分比误差（`MAPE`）是常用的指标。`RMSE` 显示模型在进行预测时平均产生的误差。`RMSE` 值越小越好。

下面的代码块将 `MAPE` 实现为衡量测试集上模型性能的指标。

![](img/page140-02.png)

## 5.7 | 多元线性回归

多元线性回归（`MLR`）是一种监督学习算法，用于寻找因变量（又称响应变量或结果变量）与多个自变量（又称解释变量或预测变量或特征）之间关联关系是否存在。

![](img/page140-03.png)

`MLR` 的函数形式由下式给出

![](img/page141-01.png)

回归系数 `β[1]`、`β[2]`、...、`β[k]` 称为偏回归系数，因为解释变量与响应（结果）变量之间的关系是在剔除（或控制）模型中所有其他解释变量（特征）的影响后计算的。

`MLR` 模型所做的假设如下（Kumar, 2017）：

**1.** 回归模型在回归参数（`β` 值）上是线性的。

**2.** 残差服从正态分布，且残差的期望值（均值）为零。

**3.** 在时间序列数据中，残差被假设为不相关。

**4.** 残差的方差对所有 `X[i]` 值都是常数。当残差的方差对不同的 `X[i]` 值保持不变时，称为同方差性。残差方差非恒定称为异方差性。

**5.** 模型中自变量之间不存在高度相关性（称为多重共线性）。多重共线性会使模型不稳定并导致回归参数估计错误。

在这种情况下，偏回归系数再次通过最小化误差平方和（`SSE`）来估计。我们将使用印度板球超级联赛拍卖定价的例子来解释 `MLR` 模型。

## 5.8 | 预测印度板球超级联赛球员的售价（拍卖价）（Kumar, 2017）

印度板球超级联赛（IPL）是由 BCCI 于 2008 年创办的职业 Twenty20 板球联赛，由八支由世界各地球员组成的特许经营队组成。首届 IPL 拍卖于 2008 年举行，用于球队 10 年的拥有权，底价为 5000 万美元。特许经营队通过每年举行的英式拍卖获得球员。然而，存在多项规则。例如，只有国际球员和受欢迎的印度球员会被拍卖。

球员的表现可以通过多个指标衡量。虽然 IPL 是一项 20 局制的比赛，但板球其他形式如测试赛和一日国际赛的表现也可能影响定价。一些球员拥有出色的测试赛记录，但他们的 Twenty20 记录并不那么令人印象深刻。通过各种表现指标衡量的在 IPL（2008-2011）至少打过一个赛季的 130 名球员的表现数据在 **表 5.9** 中提供。

## 5.9 | 开发多元线性回归模型

本节将讨论使用 `R` 开发多元回归所涉及的各个步骤（Pradhan and Kumar, 2019）。

我们将使用 `caret` 包来演示多元线性回归。

![](img/page141-02.png)

**表 5.9** | IPL 数据描述

| 数据代码 || 描述 |

| --- | --- |

| AGE || 拍卖时球员年龄分为三类。类别 1（L25）表示球员年龄小于 25 岁，2 表示年龄在 25 至 35 岁之间（B25-35），3 表示年龄大于 35 岁（A35）。 |

| --- | --- |

| RUNS.S || 球员得分的跑分数量 |

| RUNS.C || 球员失分的跑分数量 |

| HS || IPL 中击球手取得的最高得分 |

| AVE.B || IPL 中击球手平均得分 |

| AVE.BL || 投球平均分（IPL 中失分数/取得 wickets 数） |

| SR.B || 击球打击率（IPL 中得分数与面对球数之比） |

| SR.BL || 投球打击率（IPL 中投球数与取得 wickets 数之比） |

| SIXERS || 球员在 IPL 中击出的六分球数量 |

| WKTS || 球员在 IPL 中取得的 wickets 数量 |

| ECON || 投球手经济率（IPL 中投球手每局失分数） |

| CAPTAINCY.EXP || 曾担任 T20 队伍或国家队队长 |

| ODI.SR.B || 一日国际赛中的击球打击率 |

| ODI.SR.BL || 一日国际赛中的投球打击率 |

| ODI.RUNS.S || 一日国际赛中得分的跑分 |

| ODI.WKTS || 一日国际赛中取得的 wickets |

| T.RUNS.S || 测试赛中得分的跑分 |

| T.WKTS || 测试赛中取得的 wickets |

| PLAYER.SKILL || 球员主要技能（击球手、投球手或全能选手） |

| COUNTRY || 球员原籍国（AUS：澳大利亚；IND：印度；PAK：巴基斯坦；SA：南非；SL：斯里兰卡；NZ：新西兰；WI：西印度群岛；OTH：其他国家） |

| YEAR.A || IPL 拍卖年份 |





| `IPL.TEAM` || 玩家在 IPL 中效力过的球队（CSK: Chennai Super Kings；DC: Deccan Chargers；DD: Delhi Daredevils；KXI: Kings XI Punjab；KKR: Kolkata Knight Riders；MI: Mumbai Indians；PWI: Pune Warriors India；RR: Rajasthan Royals；RCB: Royal Challengers Bangalore）。使用 + 号表示球员效力过不止一支球队。例如，CSK+ 表示该球员效力过 CSK 以及一个或多个其他球队。 |

### 5.9.1 导入数据集
收集的数据存储在 csv 文件中。`read.csv` 函数用于从当前工作目录读取数据集。如果您不确定文件将从哪个当前工作目录读取，您可以使用
1. `getwd()` 函数用于获取您的工作目录和
2. `setwd()` 函数用于设置您的工作目录。
默认情况下，`read.csv` 文件仅期望文件名的路径。然而，我们使用额外的参数 `na.strings()` 在数据集中存在垃圾值的地方嵌入 `NA`。查找的垃圾值为 `c("", " ", "NA")`。执行此操作是因为 `R` 将 `NA` 识别为缺失值而不是空白。此嵌入 `NA` 的操作也可以在数据之后执行。然而，在开始时执行此步骤要高效得多。**表 5.10** 显示了数据的快照。
![](img/page142-01.png)![](img/page143-01.png)
一旦数据集加载到数据框中，我们可以使用下面的代码块查看数据类型。
![](img/page143-02.png)
`str()` 函数显示 `ipl_df` 有 130 个观测值，跨 27 个变量。`dim(ipl_df)` 函数也可以用来显示数据框的维度。`summary(ipl_df)` 将返回数据的摘要。
`ipl_df` 的摘要显示 `COUNTRY` 中包含一些出现频率较低的国家/地区的观测值。使用 `table()` 函数进行制表可揭示更多细节。
![](img/page144-01.png)
我们将把其中一些国家合并到名为 `OTHERS` 的新标签中。合并标签的原因是为了避免在训练和测试数据创建（本章后面）中出现问题。低频计数也可能导致创建交叉验证（CV）集时出现问题，因为在某些 CV 集中可能没有对应于少数国家/地区的观测值。
![](img/page144-02.png)
我们可以构建模型来了解哪些球员特征影响其‘SOLD PRICE’以及球员价格是否可以在未来预测。然而，`ipl_df` 中的所有列都不能用于模型构建。例如，`Sl. NO.` 是标识符而不是特征！！！另请注意，变量 `AGE` 被识别为数值变量，但元数据定义将其视为分类变量。这意味着需要对变量进行类型转换以转换为正确的数据类型。下面的代码块使用 `as.factor()` 函数对 `AGE` 和 `CAPTAINCY_EXP` 变量进行类型转换。
我们将在进行任何进一步分析之前从变量列表中删除 `SL. No.`。我们还使用 `na.omit` 函数执行了按行删除缺失值的额外步骤。请注意，在加载数据时嵌入 `NA` 的使用是为了实现此步骤，即在任一列中没有数据可用时删除行。此步骤不会删除数据框中的任何观测值，因为没有缺失值。然而，在处理存在缺失信息的数据集时，此步骤很有用。
应该注意的是，按行删除缺失值应在尝试使用插补技术填补缺失情况之后进行。**表 5.11** 显示了准备好的数据。
![](img/page144-03.png)![](img/page145-01.png)

### 5.9.2 创建特征集 (X) 和结果变量 (Y)
让我们编写一个通用函数从数据集中提取预测变量和响应变量。
![](img/page145-02.png)
让我们确定我们不希望作为模型构建中独立特征的特征。其中三个特征是 `PLAYER_NAME`、`TEAM` 和 `AUCTION_YEAR`。我们还将 `BASE_PRICE` 保留在特征列表之外。下面的代码块从预测变量列表中删除这些特征。
![](img/page145-03.png)
我们还可以分别获取数值和分类预测变量。
![](img/page146-01.png)
大多数情况下，R 会在内部对分类变量执行 **编码**。然而，对于一些高级机器学习算法，必须显式地对分类变量进行编码。

### 5.9.3 编码分类特征
IPL 数据集包含定量和定性变量。定性或分类变量在纳入回归模型之前需要使用虚拟变量进行编码。如果一个分类变量有 `n` 个类别，则需要 `n - 1` 个虚拟水平来表示这 `n` 个类别。虚拟变量是取值为 0 和 1 的二元变量。
`read.csv()` 方法默认将分类变量视为因子变量。因子变量根据字母顺序分配一组整数代码。然后 R 使用 `model.matrix()` 方法，自动创建虚拟变量编码，并将参考类别（基类别）分配给按字母顺序首先出现的标签。
让我们以 IPL 数据集中的变量 `PLAYING.ROLE` 为例来理解虚拟变量编码的概念。假设数据中‘PLAYING.ROLE’变量有四个类别（batsman、bowler、wicket keeper 和 allrounder）。
![](img/page146-02.png)
**表 5.12** 显示了 `PLAYING.ROLE` 所有标签的 0-1 编码。在这种情况下，我们有四个标签，因此创建了四列，并在对应于标签存在的列中标记一个。
然而，如果我们从 **表 5.12** 中删除列名 `PLAYING_ROLE(Allrounder)` 并创建新的 **表 5.13**，我们仍然能够表示所有四个标签。标签‘Allrounder’由‘0 0 0’表示，被称为基类别。
**虚拟变量编码**是在应用任何机器学习技术之前表示分类变量的一种流行技术。使用虚拟变量编码的弊端是，当分类变量中的标签数量很大时，它会增加数据的维度。
![](img/page146-03.png)![](img/page147-01.png)
还有其他 **高级编码技术**，如序数编码、二进制编码、特征哈希、word-to-vec 等，当数据量很大且分类特征中的标签数量太多时，这些技术可能是分类变量的有用表示。
**模型构建**是一个迭代过程。选择构建模型的正确特征集可能需要业务干预以及模型选择策略，如赤池信息准则（AIC）。
创建 (`n - 1`) 个虚拟变量编码列来表示 `n` 个标签的原因是，在回归方程中包含所有类别的虚拟变量和常数将产生完全多重共线性（稍后会讨论）。
由于 R 使用 `model.matrix()` 方法并自动创建虚拟变量编码，因此它将按字母顺序首先出现的标签标记为基类别。这意味着对于 `PLAYING.ROLE` 变量，标签 *‘Allrounder’* 将被视为基类别。
请注意，对于某些算法，我们可能需要显式创建虚拟变量编码列。我们可以使用 `stats` 包中的 `model.matrix()` 方法或 `caret` 包中的 `dummyVars()` 方法创建虚拟变量编码列。

### 5.9.4 创建训练集和测试集




`createDataPartition()` 函数来自 `caret` 包，提供将数据集随机拆分为训练集和验证数据集的能力。

**1.** 该函数期望传入一个向量，在我们的案例中，我们向其传入名为 `salary` 的其中一个变量。

**2.** 它还期望训练集应包含的数据百分比，我们将其设置为 0.80。

**3.** 最后，通过设置 `list = FALSE`，我们期望 `train_index` 包含一个矩阵，其行数等于 `floor(0.80 * length(Salary))` 乘以列数，即为二。

然而，即使在调用 `createDataPartition()` 之前，我们也使用了 `set.seed()` 函数来保持结果的可重复性和可再现性。在执行任何涉及随机划分或随机数生成的操作之前，这是一个重要步骤。

我们鼓励你注释掉 `set.seed()` 函数并多次运行下面的代码块。注意每次执行时进入 `train` 和 `test` 数据框的观测值。

![](img/page147-02.png)

我们创建了两个新的数据框，其中仅包含将用于模型构建的特征。

### 5.9.5 模型构建：使用 Caret 包

让我们使用 第 5.4.5 节 中描述的 `caret` 包来构建多元线性回归模型。

![](img/page147-03.png)![](img/page148-01.png)

根据 p 值（<0.05），只有特征 `COUNTRYENG` 显示为显著。在 p 值为 0.05 的模型解释中，表明其他特征均不以 5% 的显著性影响 `SOLD_PRICE`。对一些变量的更仔细观察表明了一些有趣的见解：

**1.** 打击率带有负估计值（`SR_B` 的估计值为 −784）。这表明球员的 `SOLD_PRICE` 将随着击球率每增加一个单位而减少 784 个单位。

**2.** 投球手受影响最大，如果投球打击率（`ODI_SR_BL`）提高一个单位，投球手的 `SOLD_PRICE` 将减少 1829 个单位。

对回归结果中的其他变量也可以看到类似的解释。这些结果似乎违反直觉，可能是变量多重共线性效应导致的结果。我们将讨论多重共线性产生的问题以及处理方法。然而，另一个需要注意的点是，对于分类变量 ‘`AGE`’、‘`COUNTRY`’、‘`CAPTAINCY_EXP`’ 和 ‘`PLAYING_ROLE`’，哑变量编码是自动完成的。

### 5.9.6 多重共线性的重要性

当数据集具有大量自变量（特征）时，这些自变量（特征）中可能有几个高度相关（Pradhan and Kumar, 2019）。自变量之间存在高度相关性称为多重共线性。多重共线性的存在会使多元回归模型不稳定。因此，有必要识别多重共线性的存在并采取纠正措施。多重共线性可能对模型产生以下影响：

**1.** 估计的标准误差，![](img/pageIn_ch5-17.png)，被夸大了。

**2.** 统计上显著的特征变量可能被标记为统计上不显著。这是由于当估计的标准误差被夸大时，可能导致 f 统计量值被低估。

**3.** 回归系数的符号可能不同，即回归系数本应为负值时，我们可能得到正回归系数，反之亦然。

**4.** 添加或删除一个变量甚至一个观测值都可能导致回归系数估计出现较大变化。

### 方差膨胀因子（VIF）

方差膨胀因子（`VIF`）衡量的是估计回归系数的方差相较于预测变量不线性相关时的膨胀程度。例如，考虑两个自变量 `X[1]` 和 `X[2]` 及其之间的回归。

![](img/page149-01.png)

设 `R[12]` 为该模型的 R 平方值。那么 `VIF`，即多重共线性的度量，可以表示为

![](img/page149-02.png)

`VIF` 越高，共线性越高。![](img/pageIn_ch5-18.png) 是标准误差被膨胀的值。假设 `VIF` 的平方根为 2.5。这意味着该预测变量系数的标准误差是其与其它预测变量不相关时的 2.5 倍。

`VIF` 值大于 4 需要进一步调查以评估多重共线性的影响。

**1.** ![](img/pageIn_ch5-19.png)不相关

**2.** ![](img/pageIn_ch5-20.png)中度相关

**3.** ![](img/pageIn_ch5-21.png)高度相关

为每个解释变量计算一个 `VIF`，并移除具有高值的变量。

![](img/page150-01.png)

如果加权线性模型中的所有项都有 1 `df,` 则计算通常的 `VIF`s。如果加权线性模型中的任何项有超过 1 `df`，则计算广义方差膨胀因子（`GVIF`s）并根据自由度进行调整。`GVIF^(1/(2*df))` 是调整后的 `VIF`，其中 `df` 表示与该项相关的自由度。

### 识别相关特征

通常，如果在模型构建之前已分析特征之间的相关性并从数据中剔除相关变量中的一个，则多重共线性问题可能不会出现。我们将使用 `cor()` 函数在数值变量之间构建相关矩阵，**表 5.14**。

![](img/page150-02.png)

由于 **表 5.14** 中对角线元素上方和下方的值相同，我们可以使用基础包中的 `upper.tri()` 和 `lower.tri()` 函数返回上三角和下三角矩阵。

![](img/page150-03.png)![](img/page151-01.png)

使用 **表 5.14**，我们将绘制相关性热力图。

![](img/page152-01.png)

**图 5.3** 中的对角线表示特征与其自身的相关性，可以忽略。对于其他特征，较深的色调反映了高度相关的特征（正相关和负相关）。从 **图 5.3** 中，我们可以看到高度相关的特征，例如 `AVE_BL` 和 `SR_BL`。

### 处理多重共线性

当特征集较大时，阅读相关矩阵并找出高度相关的变量变得困难。`caret` 包有一个函数 `findCorrelation()`，它将相关矩阵作为输入。在用户定义的截止值下，该函数将打印与其它变量在指定截止值下相关的变量名称。

![](img/page152-02.png)![](img/page153-01.png)

在相关性截止值为 0.6 时，从 **表 5.14** 中，我们可以得出结论，板球运动员在 IPL 中取得的最高得分（`HS`）与以下高度相关：

**1.** 板球运动员在 IPL 中平均得分（`AVE_B`）

**2.** 球员在 IPL 中得分总数（`RUNS_S`）

**3.** 在 IPL 中击出的六分球数量（`SIXERS`）。

然而，正如 `findCorrelation()` 结果所示，在四个相关特征中，特征 `SIXERS` 未被打印出来。这是因为 `findCorrelation()` 函数会查看每个变量的平均绝对相关性（`MAC`）并移除具有最大 `MAC` 的变量。例如，‘`HS`’ 的 `MAC` 从 **表 5.15** 计算为 0.448。

**表 5.16** 列出了四个变量的 `MAC`。



如图所示，应剔除的变量为 `HS`、`AVE_B` 和 `RUNS_S`，因为它们具有最高的 MAC 值。同样，根据 **表 5.14**，球员在 ODIs 中得分的数量 (`ODI_RUNS_S`) 与在 Test 板球中得分的数量 (`T_RUNS`) 高度相关（>0.60）。MAC 值显示在 **表 5.17：**
因此应剔除的变量为 `ODI_RUNS_S`。同样，
• **表 5.18** 显示了 IPL 中投球打击率 (`SR_BL`)、投球平均分 (`AVE_BL`) 和 IPL 经济率 (`ECON`) 之间的 MAC。
• IPL 中取得的 wickets 数量 (`WKTS`) 与 IPL 中失分 (`RUNS_C`) 高度相关。MAC 显示在 **表 5.19。**
• ODIs 中取得的 wickets (`ODI_WKTS`) 与 Tests 中取得的 wickets (`T_WKTS`) 高度相关。**表 5.20** 显示了这些变量之间的 MAC。
根据 **表 5.18、5.19** 和 **5.20**，我们可以得出结论：
**1.** 第一种情况下应剔除的变量为 `SR_BL` 和 `AVE_BL`。
**2.** 第二种情况下应剔除的变量为 `WKTS`。
**3.** 第三种情况下应剔除的变量为 `ODI_WKTS`。
因此 `HS`、`AVE_B`、`RUNS_S`、`ODI_RUNS_S`、`SR_BL`、`WKTS`、`AVE_BL` 和 `ODI_WKTS` 是由 `findCorrelation()` 函数识别并标记为移除的变量。尽管上述变量已被 `findCorrelation()` 函数突出显示并建议移除，但保留或移除变量的最终决定取决于对数据和领域的理解。在实际业务场景中，在确定最终不具有多重共线性的变量集之前，可能需要多次迭代。因此最终确定的变量集为 `HS`、`AVE_B`、`RUNS_S`、`T_RUNS`、`AVE_BL`、`ECON`、`RUNS_C`、`T_WKTS`、`SR_BL`、`SR_B` 和 `ODI_SR_B`。

### 5.9.7 重建模型：使用 Caret 包
现在我们将通过移除上述部分中确定的排除变量来构建新的 IPL 训练集和测试集。让我们重新审视上一节中创建的预测变量列表并移除更多特征。
![](img/page154-01.png)![](img/page155-01.png)
我们将使用新的训练集运行回归模型。
![](img/page155-02.png)![](img/page156-01.png)
估计系数的 `p`-值显示变量是否在统计上显著影响响应变量。如果 `p`-值小于显著性值（α），则该特征在统计上显著；否则不显著。α 的值通常选为 0.05。然而，它可以根据问题的背景进行选择。
利用 VIF 的理解，我们可以推断 `ipl_new_reg_model` 中的变量均不存在多重共线性，因此可以确定估计系数的标准误差不会被夸大。
![](img/page156-02.png)![](img/page156-03.png)
**表 5.17** | ODI 得分与测试得分之间的 MAC 值
| `ODI_RUNS_S` || `T_RUNS` |
| --- | --- |
| 0.371 || 0.331 |
| --- | --- |
![](img/page156-04.png)
**表 5.19** | IPL 中 wickets 取得数与失分之间的 MAC 值
| `WKTS` || `RUNS_C` |
| --- | --- |
| 0.341 || 0.339 |
| --- | --- |
**表 5.20** | ODI wickets 取得数与测试赛 wickets 取得数之间的 MAC 值
| `ODI_WKTS` || `T_WKTS` |
| --- | --- |
| 0.2642 || 0.2628 |
| --- | --- |

### 使用 AIC 进行模型选择
根据使用 `ipl_new_reg_model` 对象报告的 `p`-值，只有变量 `COUNTRYENG` 和 `SIXERS` 在统计上显著。对 `SOLD_PRICE` 的这些特征的解释如下：
**1.** 平均而言，与来自澳大利亚（基准类别）的球员相比，来自英格兰的球员的 `SOLD_PRICE` 上涨 $562,423。
**2.** 平均而言，随着击出的 sixes 数量每增加一个单位，球员的 `SOLD_PRICE` 上涨 $4,683。
然而，回归结果中还有其他变量，其 `p`-值大于 0.05。这些变量也会影响显著变量的 beta 系数估计。我们必须移除这些不显著的变量并再次运行回归，以找到显著变量的真实 beta 估计。此外，移除不显著变量必须通过评估其移除对所有其他变量的影响来进行。这种评估是必要的，因为所有自变量之间总会存在一定程度的相关性，这会使某些显著变量变得不显著。另一种看法是，每增加或删除一个变量就意味着创建一个新模型，因此有许多模型可供选择最佳模型。这看起来像是一个迭代过程，可能需要许多步骤才能移除所有不显著的变量。
为了克服迭代运行回归模型的问题，`caret` 包提供了一种方法 `lmStepAIC()`，它通过查看 **赤池信息准则** (AIC) 来实现变量选择和剔除的策略。
顾名思义，`lmStepAIC()` 是一个逐步函数，使用 AIC 作为模型选择的准则。AIC 估计给定变量集下每个模型相对于其他模型的优劣。因此，AIC 提供了一种通过保留较少的预测变量来建立简单模型的方法。
AIC 并未提供关于原假设的模型检验，因此它不对模型的绝对质量发表意见，只说明模型相对于其他模型的优劣。
计算 AIC 的公式为
![](img/page157-01.png)
在 公式 (5.27) 中，
• `n` 是数据中的观测值数量。
• `RSS` 是回归平方和。
• `k` 是惩罚因子。通常计算 AIC 时使用 `k` = 2。`k` = log(`n`) 有时被称为贝叶斯信息准则 (BIC)。
• `P` 是模型中的参数数量。
下面的代码块使用 `lmStepAIC()` 方法和向后剔除策略实现回归模型。`lmStepAIC()` 方法调用 `MASS` 包中的 `stepAIC()` 函数。
![](img/page157-02.png)![](img/page158-01.png)![](img/page159-01.png)

### 理解 AIC 步骤
让我们首先使用 [公式 \[5.27\]](#13_Chapter05.xhtml#eq5.27) 计算初始 AIC 值。我们将使用 `ipl_new_reg_model` 对象，该对象使用 `caret` 包中的 `lm()` 方法开发，用于计算初始 AIC。
![](img/page159-02.png)
让我们理解 `ipl_aic_reg_model` 对象，它是 `lmStepAIC` 的结果，并产生了四次迭代：
• 第 1 次迭代：
– `ipl_aic_reg_model` 的起始 AIC 值为 2702.4。该值表示所有自变量均已包含在模型中。我们使用 `lm()` 方法创建的 `ipl_new_reg_model` 对象手动计算了该值，发现该值相同，即 2702.4。
– `ipl_aic_reg_model` 中的 ‘none’ 类别对应于包含所有变量的模型。换句话说，没有变量被移除，对应的 AIC 值为 2702.4。
– `PLAYING_ROLE`：这构建了一个在保留所有其他变量的同时移除 `PLAYING_ROLE` 变量的模型。在 `ipl_aic_reg_model` 中，移除 `PLAYING_ROLE` 变量后的 AIC 值为 2699.7。让我们使用 `lm()` 方法手动重现此 AIC 值。
![](img/page159-03.png)![](img/page160-01.png)
我们发现 AIC 值与 2699.7 相同。
• 第 1 次迭代继续：



### 第 1 次迭代
– `ODI_SR_BL`：这构建了一个模型，其中移除了 `ODI_SR_BL` 变量并保留所有其他变量。移除 `ODI_SR_BL` 后模型的 AIC 值为 2700.8。让我们使用 `lm()` 方法手动重现此 AIC 值。

![](img/page160-02.png)

### 第 1 次迭代继续
– `WKTS`：这构建了一个模型，其中移除了 `WKTS` 变量并保留所有其他变量。移除 `WKTS` 后模型的 AIC 值为 2701.1。我们建议您通过修改上面的代码块手动检查此值。
– 第 1 步在所有变量单独移除并使用剩余变量构建模型后完成。
– 第 1 次迭代的结果表中包含每个模型的 AIC。
– 在这种情况下，我们看到从变量列表中排除 `PLAYING_ROLE` 的模型给出了最小的 AIC 值（2699.7）。

让我们看第 2 次迭代。

### 第 2 次迭代
– 起始模型的 AIC 为 2699.7。这是 `PLAYING_ROLE` 变量被排除在模型之外作为起点时的模型。
– ‘none’ 类别对应于包含除 `PLAY-ING_ROLE` 之外的所有变量的模型。
– `ODI_SR_BL`：这构建了一个模型，其中移除了 `ODI_SR_BL` 变量并保留所有其他变量。移除 `ODI_SR_BL` 后模型的 AIC 值为 2697.7。让我们手动重现此 AIC 值。

![](img/page161-01.png)

### 第 2 次迭代继续
– `WKTS`：这构建了一个模型，其中移除了 `WKTS` 变量并保留所有其他变量。移除 `WKTS` 后模型的 AIC 值为 2698.7。我们建议您通过修改上面的代码块手动检查此值。
– 第 2 次迭代在所有变量单独移除并使用剩余变量构建模型后完成。
– 第 2 步的结果表中包含每个模型的 AIC。选择 AIC 值最低的模型用于第三步。
– 在这种情况下，我们看到从变量列表中排除 `ODI_SR_BL` 的模型具有最低的 AIC 值（2697.7）。

上一步中 AIC 值最小的模型每次都成为后续步骤的起始模型。第 1 次迭代和第 2 次迭代中解释的逻辑同样适用于第 3 次迭代。因此，我们进入最后一次迭代，即第 4 次迭代。

### 第 4 次迭代
– 起始模型的 AIC 为 2696.7。这是 `WKTS` 变量被排除在模型之外作为起点时的模型。
– ‘none’ 类别对应于包含除 `WKTS` 之外的所有变量的模型。
– `CAPTAINCY_EXP`：这构建了一个模型，其中移除了 `CAPTAINCY_EXP` 变量并保留所有其他变量。移除 `CAPTAIN-CY_EXP` 后模型的 AIC 值为 2696.8。我们建议您通过修改上面的代码块手动检查此值。
– 第 4 次迭代在所有变量单独移除并使用剩余变量构建模型后完成。
– 第 4 次迭代的结果表中包含每个模型的 AIC。选择 AIC 值最低的模型用于下一步。
– 然而，在这种情况下，我们看到没有模型的 AIC 值低于初始模型（AIC：2697.7）

因此，最佳模型在第 4 次迭代中找到。`stepAIC()` 的起点是一个完整模型，在每一步中，使用除一个变量外的所有变量构建模型，并为每个模型计算 AIC 值。选择 AIC 值最小的模型用于后续步骤。

### 5.9.8 模型摘要
对象 `ipl_aic_reg_model` 具有最终模型。该模型对象的 `summary()` 显示了其中保存的一些统计信息。

![](img/page162-01.png)

从摘要输出中，我们可以推断出以下内容：
模型的调整 *R*-square 值为 0.3987，调整 *R*-square 值是通过用相应的自由度归一化 `SSE` 和 `SST` 计算得出的。如 `ipl_aic_reg_model` 对象的摘要所示，最终模型中保留的变量为：
**1.** `COUNTRY`
**2.** `ODI_WKTS`
**3.** `ODI_RUNS_S`
**4.** `SIXERS`

然而，需要注意的是，模型中保留的变量仍可能包含不显著的变量。这是因为 `lmstepAIC()` 基于 AIC 选择模型，而不是 *p*-values。目标是通过在范围内移除或添加变量来找到 AIC 最小的模型。如果使用 AIC 进行模型选择，即使 *p*-values 大于 0.05，也最好考虑最终模型中保留的所有变量。

控制变量选择的其中一个参数是惩罚因子，默认设置为 2（`MASS` 包中 `stepAIC()` 参数设置中的 `k` = 2）。由于模型中的每个变量都以 2 的因子进行惩罚，我们在最终模型中有些变量的 *p*-value > 0.05。为了仅报告最终模型中 *p*-value < 0.05 的变量，我们必须将步骤函数中的 *k* 参数设置为 3.84（~ 4）。然而，*k* 值的这种更改通常不会进行。示例代码更改如下所示：

```
ipl_aic_k_3.84_reg_model = train(ipl_train_df[new_predictors], ipl_train_df [response], method = "lmStepAIC", k = 3.84, trControl = obj_control, metric = "Rsquared")
summary(ipl_aic_k_3.84_reg_model$finalModel)
```

## 5.10 模型诊断
在将多元线性回归模型用于实际应用之前，验证其有效性和拟合优度非常重要。以下度量用于验证简单线性回归模型：
**1.** Co-efficient of determination (R-square).
**2.** Hypothesis test for the regression coefficient.
**3.** Analysis of variance (ANOVA) for overall model validity (relevant more for multiple linear regression).
**4.** Residual analysis to validate regression model assumptions.
**5.** Outlier analysis.

我们在简单线性回归中讨论了上述要点。简单线性回归模型指标的所有验证检查同样适用于多元线性回归。我们可以使用 `broom` 包中的 `augment()` 来增强 `ipl_train_df` 数据以添加拟合值和残差。由此产生的 data.frame，例如 `diagnostic_metrics`，包含多个对模型诊断有用的指标。当在回归对象模型上使用 `plot()` 函数时，它实际上使用 `diagonstic_metrics` 来提供对残差分析和异常值分析有用的各种图。

![](img/page163-01.png)

`.outcome` 是 `ipl_train_df` 中的 `SOLD_PRICE`。`diagonstic_metrics` 还包含最终模型的一部分的所有特征。然而，并非所有列和行都显示在 **表 5.21** 中（为保持可读性）。`diagnostic_metrics` 中的其他列如下：

![](img/page164-01.png)
**1.** `.fitted`: fitted values (predicted values)
**2.** `.resid`: residual errors (`.outcome` - fitted)
**3.** `.hat`: to detect high leverage points (or extreme values in the predictors `X` variables)
**4.** `.cooksd`: Cook’s distance, used to detect influential values, which can be an outlier or a high leverage point. A Cook’s distance of 0.013 for observation *X*[6] suggests that removing this observation from the training data would have changed the predicted value of *Y* by 0.013 (on an average).
**5.** `.std.resid`: Standardized residuals. This is arrived at by dividing residuals by their standard errors. `.std.resid` is used to detect outliers (or extreme values in the outcome *y* variable).

### 5.10.1 线性假设
**图 5.4** 显示了线性假设。

![](img/page164-02.png)

如果红线在零处大致水平，则可以假设函数形式被正确指定。模式的存在可能表明线性模型的某些方面存在问题。



从 `ipl_train_df` 中的残差 vs. 拟合图，我们可以得出回归的函数形式（`X` 与 `Y` 之间的线性关系）可能不正确。

![](img/page164-03.png)

### 5.10.2 正态性假设

![](img/page165-01.png)

从 **图 5.5** 的 Q-Q 图可以看出，残差近似服从正态分布（我们只需要近似正态分布即可）。

### 5.10.3 同方差性假设

![](img/page165-02.png)

从 **图 5.6** 的尺度-位置图来看，残差并非随机分布，似乎在图表左下角聚集，这意味着残差不具有恒定方差（同方差性）。

### 5.10.4 异常值和高杠杆点

观察残差 vs. 杠杆图可以识别出 Z 分数高和杠杆值高的观测值。

![](img/page165-03.png)![](img/page165-04.png)![](img/page166-01.png)

默认情况下，图仅突出显示杠杆值高或 Z 分数更高的前三个点。要突出显示前十个点，我们可以在 `plot()` 中使用 `id.n=10`。

![](img/page166-02.png)

在 **图 5.7** 中，横轴显示观测值 `Xs` 的杠杆值和 Cook 距离，纵轴显示 Z 分数。

**图 5.8** 突出了 Z 分数高、杠杆值高或 Cook 距离高的前 10 个观测值。然而，这些观测值不一定具有

**1.** `.std.resid` (`z-score`) > 3

**2.** `.hat` (`leverage`) >= `3(p + 1)/n` 其中 `p` 是预测变量的数量，`n` 是观测值的数量。

**3.** `.cooksd` (`cook’s distance`) >= 0.5 or `.cooksd` (`cook’s distance`) >= `4/(n-p-1)` 其中 `p` 是预测变量的数量，`n` 是观测值的数量。

在 `mba_train_df` 中，没有任何观测值位于残差 vs. 杠杆图的右上或右下区域（**图 5.7** 中 0.5 及以上的虚线区域）。因此，没有任何案例对回归结果产生影响。

![](img/page166-03.png)

使用杠杆阈值计算公式 `3(p + 1)/n`，让我们计算稍后将使用的 `leverage_threshold`。

![](img/page167-01.png)

### 5.10.5 有影响的值

基于 Cook 距离阈值的异常值可以通过检查 Cook 距离图以及上一节讨论的残差 vs. 杠杆图来识别。

默认情况下，Cook 距离图突出显示前三个有影响的点。要突出显示前十个观测值，我们可以在 `plot()` 中使用 `id.n=10`。以下图表说明了我们模型的 Cook 距离和杠杆值：

![](img/page167-02.png)

**图 5.8** 突出了 Cook 距离得分高的前十个观测值。然而，这些观测值不一定具有大于 `4/(n - p - 1)` 的 `.cooksd` 值，其中 `p` 是预测变量的数量，`n` 是观测值的数量。

![](img/page167-03.png)

我们将在下一节中使用 Cook 阈值来识别有影响的案例。

### 5.10.6 在数据框中识别异常值案例

在 5.10.4 和 5.10.5 节中，我们查看了图表以直观地识别可能为异常值的案例。但这些可视化仅限于识别前 `n` 个案例。让我们尝试识别所有 Z 分数、杠杆值或 Cook 距离较高的案例。我们已将所有统计数据保存在 `diagonstic_metrics` `data.frame` **(表 5.21)** 中。它显示了该数据框的前 7 列以提高可读性。

**表 5.22** 显示了所有 Z 分数高的案例（`Z-score` > 3）。由于 **表 5.22** 没有记录，很明显没有任何案例超过 Z 分数阈值。

![](img/page167-04.png)

我们在 第 5.10.4 节 中计算了 `leverage_threshold`。**表 5.23** 显示了所有杠杆值高的案例（`.hat` > `leverage_threshold`）

![](img/page167-05.png)![](img/page168-01.png)![](img/page168-02.png)![](img/page168-03.png)

我们在 第 5.10.5 节 中计算了 `cooks_threshold`。然而，我们将采用通常接受的 0.5 及以上的 `cooks_threshold`。让我们获取所有 Cook 距离高的案例（`.cooksd` > `cooks_threshold`）。

![](img/page169-01.png)

从 **表 5.24** 可以看出，没有 Cook 距离为 0.5 及以上的案例，因此 `ipl_train_df` 中没有有影响的案例。

我们将把移除有影响的观测值后构建模型的下一步留给读者自行练习。

### 5.10.7 转换响应变量

转换是通过推导新的因变量和/或自变量来识别回归模型正确函数形式的过程（Kumar, 2017）。例如，因变量 `Y` 在模型中可以用 `ln(Y)`、`1/Y` 等替换；同样，自变量 `X` 可以用 `ln(X)`、`1/X` 等替换。MLR 中的转换用于解决以下问题：

**1.** 拟合不佳（`R-squared` 值低）。

**2.** 残差分析中出现模式，表明因变量与自变量之间存在潜在的非线性关系。

**3.** 残差不服从正态分布。

**4.** 残差不是同方差的。

使用 `R` 进行转换并创建新变量可以在数据框中进行。下面的代码块创建了一个名为 `SQRT_SOLD_PRICE` 的新变量。我们将使用此变量创建新模型并分析模型假设是否得到满足。

![](img/page169-02.png)![](img/page170-01.png)

### 5.10.8 模型摘要 - 转换后的变量

![](img/page170-02.png)![](img/page171-01.png)

从 **图 5.9** 可以看出，变量的转换似乎略微改善了模型，但并未带来显著变化。我们将使用此模型对测试集进行预测。

误差项的正态性和同方差性，以及使用 `z-score`、Cooks distance 等理解数据中的异常值和有影响的值，是 **模型构建阶段** 中的重要诊断步骤。

![](img/page171-02.png)

## 5.11 | 进行预测和衡量准确性

在根据我们的要求构建最终模型并且模型通过所有诊断测试后，我们可以将其应用于验证数据以预测 SOLD PRICE（Pradhan and Kumar, 2017）。由于我们构建的模型预测的是 SOLD PRICE 的平方根，因此我们需要对预测值进行平方以得到球员的实际售价。

`predict` 函数用于在新数据集上获取预测响应。如果测试数据包含训练集中没有的新类别，则可能会收到错误消息。这通常发生在数据具有多个水平分类变量时。

![](img/page172-01.png)

**表 5.25** 显示了对测试数据的预测结果。有多种衡量预测准确性的指标。`MLmetrics` 包提供了用于衡量回归和分类算法性能的评估指标集合。`caret` 也有内置的评估函数，如用于 R-squared 的 `R2()`，以及用于计算均方根误差的 `RMSE()`。这些函数期望将观测值和预测值作为参数传入。

![](img/page172-02.png)

验证集上的准确度（`R-squared`）值为 0.36，相当低，但与模型在训练数据集上报告的 `R-squared`（0.39）相当。

![](img/page172-03.png)

## 摘要




在本章中，我们学习了如何使用 `R` 构建、诊断、理解和验证简单线性回归模型和多元线性回归模型。

**1.** 多元线性回归模型用于寻找因变量与一个以上自变量之间是否存在关联关系。

**2.** 在 MLR 中，回归系数称为偏回归系数，因为它们衡量在模型中所有其他自变量保持不变的情况下，自变量每变化一个单位时因变量值的变化。

**3.** 在构建 MLR 模型时，具有 `n` 个类别的分类变量应被 (`n - 1`) 个虚拟（二元）变量替代，以避免模型设定错误。

**4.** 除了检查正态性和异方差性之外，每个 MLR 模型都应检查是否存在多重共线性，因为多重共线性会使其不稳定。

**5.** 可以对变量进行转换以提高准确性或消除异方差性并增强模型拟合度。

### 练习

#### 使用以下数据集回答问题 1-4。开发 R 代码来回答以下问题：

数据集 `country.csv` 包含 20 个国家的腐败感知指数和基尼指数。腐败感知指数接近 100 表示腐败程度低，接近 0 表示腐败程度高。基尼指数是衡量一个国家公民之间收入分配的指标（基尼系数越高表示不平等程度越高）。腐败指数取自透明国际，而基尼指数来源于维基百科。

**1.** 在腐败感知指数（`Y`）和基尼指数（`X`）之间建立一个简单线性回归模型（`Y = b[0] + b[1] X`）。基尼指数每增加一个单位，腐败感知指数会发生怎样的变化？

**2.** 基尼指数解释了腐败感知指数变异的比例是多少？

**3.** 在 alpha 值为 0.1 时，腐败感知指数与基尼指数之间是否存在统计学上的显著关系？

**4.** 计算回归系数 `b[1]` 的 95% 置信区间。

#### 使用以下数据集回答问题 5-13。开发 R 代码来回答以下问题：

数据集 DAD 医院（`dad_hospital.csv`）包含患者的治疗费用数据。它还包含患者的人口统计和健康参数信息。以下是数据集中各列的描述。

| 序号 | 描述 |
|---|---|
| `AGE` | 患者的年龄 |
| `GENDER` | M 表示男性，F 表示女性 |
| `MARITAL_STATUS` | 患者是否已婚或未婚 |
| `KEY_COMPLAINTS_CODE` | 患者投诉的代码。患者接受治疗的关键健康状况。 |
| `BODY_HEIGHT` | 身体高度 |
| `HR_PULSE` | 心率 |
| `BP_HIGH` | 收缩压 |
| `BP_LOW` | 舒张压 |
| `RR` | 呼吸频率 |
| `PAST_MEDICAL_HISTORY_CODE` | 患者病史代码，例如糖尿病、高血压等。 |
| `HB` | 血红蛋白计数 |
| `UREA` | 尿素计数 |
| `CREATININE` | 血液和尿液中的肌酐计数 |
| `MODE_OF_ARRIVAL` | 到达方式，例如救护车、步行入院 |
| `STATE_AT_THE_TIME_OF_ARRIVAL` | 到达时的患者状态 |
| `TYPE_OF_ADMSN` | 入院类型择期、急诊 |
| `TOTAL_COST_TO_HOSPITAL` | 医院实际成本 |
| `TOTAL_AMOUNT_BILLED_TO_THE_PATIENT` | 开具给患者的实际金额 |
| `CONCESSION` | 开票时给予的优惠 |
| `ACTUAL_RECEIVABLE_AMOUNT` | 医院实际收到的金额 |
| `TOTAL_LENGTH_OF_STAY` | 患者在医院住院的天数 |
| `LENGTH_OF_STAY_ICU` | 患者在 ICU 住院的天数 |
| `LENGTH_OF_STAY_WARD` | 患者在医院病房住院的天数 |
| `IMPLANT_USED_Y_N` | 是否使用植入物 |
| `COST_OF_IMPLANT` | 所用植入物的成本 |

**5.** DAD 医院希望了解影响医院成本的关键因素。医院希望在入院时向患者提供治疗套餐（固定价格合同）。医院能否利用历史数据建立模型来估算治疗费用？

**6.** 在 `R` 中将 DAD 医院数据作为 `DataFrame` 读取。构建数据集中所有数值特征之间的相关矩阵。报告相关系数截止值为 0.70 的特征。对于高度相关的特征，你将采取什么措施？

**7.** 使用身高和体重（体重与身高的比率）构建名为 `BMI` 的新特征。将此作为问题 6 中创建的 `DataFrame` 的一部分包含在内。

**8.** 选择可用于构建模型以估算医院成本的特征。

**9.** 识别哪些特征是数值型的，哪些是分类型的。使用所选的数值特征和分类特征创建一个新的 `DataFrame`。

**10.** 哪些特征表现出多重共线性的症状，需要从模型中删除？

**11.** 将数据拆分为训练集和测试集。使用 80% 的数据进行模型训练，20% 用于模型测试。

**12.** 使用 `caret` 包构建回归模型来估算医院的总成本。你如何解释模型结果？

**13.** 使用 `Z` 分数和 Cook 距离查找数据集中的异常值。如有必要，从数据集中删除这些观测值。

### 参考文献

**1.** A Hayes (2021)，“将统计对象转换为整洁的 Tibbles”，可在 [`www.rdocumentation.org/packages/broom/versions/0.5.2`](https://www.rdocumentation.org/packages/broom/versions/0.5.2) 获取，访问日期为 21 January 2021。

**2.** Anon (2019)，“R caret 仅在 trainCon-trol 中指定 indexOut”，2021，网页地址：R caret only specify indexOut in trainControl - Stack Overflow，访问日期为 10 May 2021。

**3.** Anon (2019)，“Train：针对不同的调优参数拟合预测模型”，2021，网页地址：[`rdrr.io/cran/caret/man/train.html`](https://rdrr.io/cran/caret/man/train.html)，访问日期为 10 May 2021。

**4.** Anon (2020)，“TrainControl.R”，2021，网页地址：caret/ trainControl.R at master topepo/caret GitHub，访问日期为 10 May 2021。

**5.** Anon (2021)，“Stats v3.6.2”，可在 [`www.rdocumentation.org/packages/stats/versions/3.6.2`](https://www.rdocumentation.org/packages/stats/versions/3.6.2) 获取，访问日期为 21 January 2021。

**6.** Ben Roshan (2020)，“使用 R 进行线性回归”，2021，可在 Part 7: Linear Regression using R | Kaggle 获取，网页地址：[`www.kaggle.com/benroshan/discussion?sortBy=mostVotes&group=topics`](https://www.kaggle.com/benroshan/discussion?sortBy=mostVotes&group=topics)，访问日期为 10 May 2021。

**7.** Khun M (2021)，“Caret 包”，可在 [`topepo.github.io/caret/index.html`](http://topepo.github.io/caret/index.html) 获取，访问日期为 21 January 2021。

**8.** Khun M (2021)，“Caret 包”，可在 [`www.rdocumentation.org/packages/caret/versions/6.0-84`](https://www.rdocumentation.org/packages/caret/versions/6.0-84) 获取，访问日期为 27 January 2021。

**9.** Kuhn M (2020)，“Caret v6.0-86 - 分类和回归训练”，网页地址：[`cran.r-project.org/web/packages/caret/index.html`](https://cran.r-project.org/web/packages/caret/index.html)，访问日期为 10 May 2021。

**10.** Kumar UD 和 Ranjan K (2012)，“印度板球超级联赛球员定价”，印度管理学院，班加罗尔。

**11.** Kutner M H, Nachtsheim C J, Neter J 和 Li W (2005)，“应用线性模型” 第 5 版，McGraw Hill，纽约。

**12.** Pedersen，“ggplot2 v3.3.3”，可在 [`www.rdocumentation.org/packages/ggplot2/versions/3.2.1`](https://www.rdocumentation.org/packages/ggplot2/versions/3.2.1) 获取，访问日期为 21 January 2021。



**13.** Pradan M 和 Kumar UD (2019)，《使用 Python 进行机器学习》，Wiley，印度管理学院班加罗尔分校。

**14.** Wicham H，(2021)，“reshape2 v1.4.4 - 灵活重塑数据：重塑包的重启动”，可获取于 [`www.rdocumentation.org/packages/reshape2/versions/1.4.3`](https://www.rdocumentation.org/packages/reshape2/versions/1.4.3)，访问于 2021 年 1 月 21 日。

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

¹[`topepo.github.io/caret/available-models.html`](https://topepo.github.io/caret/available-models.html).

²[`topepo.github.io/caret/model-training-and-tuning.html#model-training-and-parameter-tuning`](https://topepo.github.io/caret/model-training-and-tuning.html#model-training-and-parameter-tuning)

# 分类问题

## 6

*知者不言，言者不知。*

—老子

### 学习目标

阅读本章后，你将能够：

• 理解分类问题的概念及其在不同行业中的应用。

• 学习使用 `caret` 包构建逻辑回归和决策树模型。

• 学习执行以下活动，例如

• 将数据集拆分为训练集和验证集，

• 在训练数据集上使用 `caret` 包构建模型并在验证数据集上测试。

• 学习使用混淆矩阵、灵敏度（召回率）、特异度、精确度、接收者操作特征（`ROC`）曲线和受试者工作特征曲线下面积（`AUC`）来衡量模型准确性。

• 学习特征的统计显著性、模型诊断以及在逻辑回归中寻找分类的最佳截止概率。

## 6.1 分类概述

分类问题是分析中的一个重要问题类别，其中结果变量或响应变量 (`Y`) 取离散值 (Kumar, 2017)。分类模型的主要目标是预测观测值属于某一类别的概率，称为 `class probability`。以下是一些分类问题的例子：

**1.** 银行希望根据风险将客户分类为低风险或高风险客户。

**2.** 组织希望预测客户是否可能流失。

**3.** 医疗服务提供者可以根据诊断结果将患者分类为阳性（疾病存在）或阴性（疾病不存在）。

**4.** 公司的 HR 部门可能想预测应聘者是否会接受 offer。

**5.** 板球协会可能想预测测试赛的结果对主队来说是胜、负还是平。

**6.** 客户对产品或服务的情感可能被分类为积极、消极、中性以及讽刺。

**7.** 根据植物的图像，可以预测其是否感染特定疾病。

分类预测可能具有二元或多个结果或类别。具有二元结果的问题称为二分类问题，具有多个类别结果的问题称为多分类问题。用于解决分类问题的技术包括逻辑回归、分类树、判别分析、K 近邻（`KNN`）、神经网络和支持向量机。本章中，我们将重点关注 Logistic Regression 和 Classification Tree 用于构建和评估分类模型。

## 6.2 二元逻辑回归

逻辑回归是一种统计学习算法，其中结果变量取离散值，而解释变量可以是连续或离散的 (Kumar, 2017)。如果结果变量仅取两个值，则问题称为二分类问题，对应的逻辑回归模型称为二元逻辑回归模型。假设结果变量的值称为阳性（通常编码为 `Y = 1`）和阴性（通常编码为 `Y = 0`）。则二元逻辑回归模型由下式给出

![](img/page176-01.png)

在 公式 (6.1) 中，`Z` 的值由下式给出

![](img/page176-02.png)

在 公式 (6.2) 中，`X[1]`、`X[2]`、…、`X[m]` 是独立变量或特征。公式 (6.1) 中定义的逻辑函数具有 S 形曲线（也称为 `Sigmoid` 函数），并给出特定特征变量值下观测值属于标记为 1 的类别的类别概率，即 `P(Y = 1|X)`。公式 (6.1) 可以重写为

![](img/page176-03.png)

公式 (6.3) 的左边是几率的自然对数，称为 `logit` 函数。右边是一个线性函数。这类模型称为广义线性模型（`GLMs`）。在 `GLM` 中，误差可能不服从正态分布，并且存在结果变量的变换函数，其取线性函数形式，如 公式 (6.3) 所示。

二元逻辑回归中特定观测值 `Y[i]`（`Y[i] = 0` 或 `Y[i] = 1`）的概率（似然）函数由 (Kumar, 2017) 给出

![](img/page176-04.png)

如果数据有 `n` 个观测值，`Y[1]`、`Y[2]`、… `Y[n]`，则似然函数，即结果观测值的联合概率 `L = P(Y[1],Y[2],...,Y[n])` 对于特定 `Z = β[0] + β[1] * X[1] + β[2] * X[2] +… + β[m] * X[m]`，由下式给出

![](img/page176-05.png)

取自然对数，公式 (6.5) 可以重写为

![](img/page176-06.png)![](img/page177-01.png)

当我们将 公式 (6.6) 中的 `LL` 乘以 −2（即 `-2LL`）时，我们得到 Deviance，它衡量与完美模型的偏差。目标是找到使 公式 (6.6) 最大化的 `β` 系数，即我们需要找到使对数似然函数最大化的 `β` 系数。逻辑回归的损失函数由下式给出

![](img/page177-02.png)

考虑一个对患有心脏病和未患心脏病的人进行分类的例子。也就是说，我们感兴趣的是找到患心脏病的概率作为年龄的函数。结果变量是某人是否患有心脏病，而自变量（特征）是年龄。然后，可以拟合逻辑或 `Sigmoid` 函数来解释相对于年龄患心脏病的概率，如 **图 6.1** 所示。

对应的逻辑回归函数由下式给出

![](img/page177-03.png)

在本章中，我们将使用 HR 数据集来预测离职（文件 `HR_Attrition.csv`）。数据集描述将在下一节提供。让我们安装将用于数据分析和模型构建的相关包。

![](img/page177-04.png)![](img/page178-01.png)

## 6.3 使用逻辑回归预测哪些员工会离开组织

组织中员工的离职是人力资源部门面临的巨大挑战。保留在组织中培养的人才不仅能提高业务效率（降低成本和精力），还能创造一支更了解组织并为其客户和其他利益相关者提供增值服务的员工队伍。然而，根据 KPMG 进行的年度薪酬趋势调查¹，各行业离职情况如 **图 6.2** 所示。

我们将使用其中一个行业的数据并构建逻辑回归模型来预测离职。**表 6.1** 显示了数据集中 (`HR_Attrition.csv`) 可用的特征。





### 6.3.1 数据导入与数据预处理

在本节中，我们将讨论使用 R 开发二元逻辑回归所涉及的各个步骤，从数据导入、数据预处理、模型构建、模型解释和验证开始。

![](img/page178-02.png)

**表 6.1** | 人力资源流失数据

| 数据代码 || 描述 |

| --- | --- |

| 员工代码 || 已随机化的唯一标识符 |

| --- | --- |

| 部门 || 员工工作的部门 |

| 员工类别 || 员工的角色 |

| 当前年龄 || 员工在当前时间戳的年龄（当前日期 – 出生日期） |

| 入职时的年龄 || 入职公司时的年龄（入职日期 – 出生日期） |

| 星座 || 基于出生日期的星座 |

| 任期 || 员工工作年限。对于在职员工：1. 当前日期 – 入职日期。对于已离开组织的员工：2. 最后工作日期 – 入职日期。 |

| 之前工作经验 || 加入本组织前的工作经验 |

| 性别 || 男性，女性 |

| 婚姻状况 || 员工的婚姻状况 |

| 平均加权绩效 || 在职期间的绩效评估，1 为最高，5 为最低。0 表示未进入绩效评估周期（新员工） |

| PL、CL、SL || 过去 2 年内享受的个人假（PL）、 casual 假（CL）和病假（SL）次数 |

| 上季度工作天数 || 上季度工作天数 |

| 上季度产假/陪产假 || 员工上季度是否休产假或陪产假 |

| CTC 2014_2015 || 2014–2015 年员工薪资 |

| CTC 2015_2016 || 2015–2016 年员工薪资 |

| 入职奖金 || 是否发放入职奖金（是或否） |

| 学位类型 || 员工的资格 |

| 最高教育学位 || 员工的最高教育程度 |

| 在家乡工作 || 员工的永久地址是否与当前工作地址相同 |

| 雇佣类型 || 雇佣类型：试用、合同、在册、永久 |

| 确认状态 || 组织确认的员工（通常在培训期后发生） |

| 直属经理年龄 || 员工汇报经理（RM）的年龄 |

| RM 下属人数 || RM 的男性下属人数 |

| RM 女性下属 || RM 的女性下属人数 |

| 最后工作日期 || 员工的最后工作日。如果员工仍在职，则日期记为 31-Dec-68 |

| 工作状态 || 是 – 员工目前在组织中  
否 – 员工已离开组织 |

### 导入数据集

收集的数据存储在 csv 文件中。可以使用 `data.table` 中的 `fread()` 函数从当前工作目录读取数据集。如果您不确定文件将从哪个当前工作目录读取，可以使用以下代码：
**1.** `getwd()` 函数获取您的工作目录和
**2.** `setwd()` 函数设置您的工作目录。
以下代码可用于读取数据并显示摘要数据，如 **表 6.2** 所示。

![](img/page180-01.png)

`summary(raw_dt)` 将返回数据的摘要。`dim(raw_dt)` 函数可用于显示数据框的维度。

![](img/page180-02.png)

`dim()` 函数显示 `raw_dt` 有 16,501 个观测值，跨 33 个变量。此外，`str()` 函数显示 `LAST_WORKING_DATE` 被识别为因子变量，其中数据类型应为 Date。

![](img/page180-03.png)

以下代码可用于更改 `LAST_WORKING_DATE` 的数据类型

![](img/page180-04.png)

请注意，在 `as.Date` 的 format 参数中，我们传递了 `%d-%b-%y`。
**1.** `%d` 用于识别月份中的日期 01–31
**2.** `%b` 用于识别缩写月份，即 Jan、Feb 等。
**3.** `%y` 用于识别无世纪的年份 00–99

![](img/page180-05.png)

然而，日期格式可能有多种不同的形式。要了解更多可传递给 `as.Date` 函数的选项，我们可以使用 `?as.Date` 或 `?strptime` 获取帮助。

我们可以构建一个模型来了解员工的哪些特征影响其 `WORKING_STATUS`，以及这些特征是否可用于预测员工未来在组织中工作的概率。但并非所有列都是特征。例如，`EMPLOYEE_CODE` 是一个标识符而不是特征。我们还可以基于 `raw_dt` 中可用的特征派生新特征。

### 特征工程

ML 模型构建最重要的方面之一是从原始数据中派生不可用的特征。在 `HR_Attrition` 数据中，我们可以看到有许多派生特征。例如，`CURRENT_AGE` 是基于当前日期 - 出生日期派生的。同样，`ZODIAC_SIGN`、`AGE_DURING_DOJ`、`TENURE`、`AVG_WEIGHTED_PERFORMANCE`、`WORKING_IN_NATIVE_PLACE` 等特征也是派生特征，可能不会直接作为原始数据的一部分存在。所有这些特征均源自原始数据，但由于某些特征的敏感性（个人身份信息）在此未显示。然而，下面是一些仍可从 `raw_dt` 的给定特征列表中派生的特征：
**1.** `CHANGE_IN_CTC = (CTC_CURRENT_YEAR - CTC_PREVIOUS_YEAR)/CTC_PREVIOUS_YEAR`
**2.** `AGE_DIFFERENCE = RM_AGE - EMPLOYEE_AGE_DURING_DOJ`
**3.** `EMPLOYEE_AGED_OVER_MANAGER = ifelse((RM_AGE - EMPLOYEE_AGE_DURING_DOJ) < 0, "Yes", "No")`
**4.** `LEAVES_PREVIOUS_YEAR = PL2014+CL2014+SL2014`
**5.** `LEAVES_CURRENT_YEAR = PL2015+CL2015+SL2015`
**6.** `LEAVE_OVER_LAST_YEAR = LEAVES_CURRENT_YEAR/LEAVES_PREVIOUS_YEAR`
**7.** `FEMALE_TO_MALE_REPORTEE = RM_REPORTEE_FEMALE/RM_REPORTEE_MALE`

如 第 2 章 中所述，我们将使用 `data.table` 的 `:=` 运算符来添加/更新/删除列，以便将这些特征作为原始 `raw_dt` 的一部分可用。在进行进一步分析之前，我们还将从特征列表中删除 `EMPLOYEE_CODE`。

![](img/page181-01.png)

**特征工程** 为数据增加了新的维度，并有助于减少原始数据中变化和异常值的影响。

这七个新特征已附加到 `raw_dt`。然而，我们可能希望将 `WORKING_STATUS`，即结果变量作为最后一列。我们可以使用 `data.table` 中的 `setcolorder()` 来实现此目的。如果我们想将某列，例如 `WORKING_STATUS` 移至第一列，我们可以直接使用下面的代码。

![](img/page182-01.png)

在上面的代码中，我们可以传递一个我们希望移至前面的列名向量。然而，我们希望将 `WORKING_STATUS` 移至最后一列。我们将使用下面的代码重新排序并显示摘要数据 **(表 6.3)**。

![](img/page182-02.png)

让我们从 `raw_dt` 中删除 `EMPLOYEE_CODE`

![](img/page182-03.png)

在数值特征之间创建比率是应用 **特征工程** 的众多方法之一。还可以通过分类特征和数值特征之间的交互创建新特征。

让我们对 `raw_dt` 进行子集化，以便新的 data.table 包含组织中的所有在职员工以及在 2015 年和 2016 年离开组织的员工。这是因为
**1.** 诸如 `PL2015`、`CL2015`、`SL2015`、`PL2014` `CL2014`、`SL2014` 等特征，表示员工请假次数，仅在 2014 年和 2015 年可用。
**2.** `DAYS_WORKED_IN_LAST_QUARTER` 对于所有在 2014 年前离开组织的员工均为零。
**3.** `PATERNITY_MATERNITY_LEAVE_LAST_QUARTER` 对于所有 2014 年前的员工均标记为 No。




上述特征可能导致报告近零方差特征的问题（将在后面讨论），并会导致整个特征被丢弃。

因此我们创建了 `raw_dt` 的一个副本，其中包括在职员工以及在 2015 年和 2016 年离开组织的员工（表 6.4）。`filter_dt` 被创建为副本，以便原始数据在需要进一步操作时保持完整。

![](img/page182-04.png)![](img/page182-05.png)![](img/page183-01.png)

对数值特征进行分箱、对数值特征进行对数转换、对数值特征进行缩放、合并分类特征中出现频率低的标签是在应用某些机器学习模型之前减少数据变异的另外一些方法。

如果我们写 `filter_dt = raw_dt`，则由于 R 的复制时修改机制，`filter_dt` 仍将指向与 `raw_dt` 相同的内存位置。因此，修改 `filter_dt`，例如添加新列或设置新键，也会修改 `raw_dt`。为避免这种情况，我们必须显式写：`filter_dt = copy(raw_dt)`

## 创建特征集 (X) 和结果变量 (Y)

我们将使用与第 5 章中类似的方法来创建特征列表

![](img/page183-02.png)![](img/page184-01.png)

我们还可以使用以下代码分别获取数值型和分类型预测变量：

![](img/page184-02.png)![](img/page185-01.png)

比较并注意数值型和分类型特征列表在第 4 章中是如何创建的差异。

## 分析特征集 (X)

模型中的特征在构建过程中可能导致多个问题。我们需要在进行模型构建之前识别特征中的问题。我们将讨论一些基本问题以及识别和移除问题的方法。

识别并移除显示近零方差、线性依赖以及与其他特征相关性的特征是在**数据预处理阶段**中的重要考虑因素。

### 零和近零方差 (NZV) 特征²

**1.** 数据生成机制可能会创建只能具有单一唯一值的预测变量（即“零方差预测变量”）。

**2.** 预测变量可能只有少数几个唯一值，且出现频率非常低。当数据使用交叉验证 (`CV`)/自助法进行分割时，这可能会造成问题。

为了识别这类预测变量，可以计算以下两个指标（Khun, 2007）：

**1.** **频率比：** 最常见值的频率除以第二常见值的频率。对于表现良好的预测变量，频率比接近 1；对于高度不平衡的数据则非常大。

**2.** **唯一值百分比：** 唯一值的数量除以样本总数（乘以 100）。随着数据粒度增加，该值会趋近于零。

`caret` 包中的 `nearZeroVar()` 可用于识别显示 NZV 的特征。我们可能将预测变量视为近零方差：

**1.** 如果频率比大于预先指定的阈值（默认值 95/5 = 19）。

**2.** 且唯一值百分比小于阈值（默认值 10%）。

![](img/page185-02.png)

如表 6.5 所示，显示近零值问题的特征如下：

**1.** `PATERNITY_MATERNITY_LEAVE_LAST_QUARTER` 和 `JOINING_BONUS`。

**2.** `LAST_WORKING_DATE` 也显示 NZV 问题。我们无论如何会在模型构建前丢弃日期列。

让我们计算 `PATERNITY_MATERNITY_LEAVE_LAST_QUARTER` 的频率比和唯一值百分比。

**1.** 对于 `PATERNITY_MATERNITY_LEAVE_LAST_QUARTER`，最常见的值是 *N*，出现了 7,444 次。第二个最常见的值是 *Y*，出现了 101 次。因此，频率比为 7,444/101 = 73.70。此外，在总共 7,545 个观测值中，`PATERNITY_MATERNITY_LEAVE_LAST_QUARTER` 的唯一值有 2 个。因此，唯一值百分比为 (2/7,545)*100 = 0.02650762。由于频率比大于 19（默认值）且唯一值百分比小于 10%，`PATERNITY_MATERNITY_LEAVE_LAST_QUARTER` 被标记为 NZV 特征。

![](img/page186-01.png)

如果我们没有通过包含具有 `LAST_WORKING_DATE` 的员工记录为 2014 年、2016 年和 2015 年创建 `filter_dt`（表 6.4）；变量 `SL2015` 也会显示为 NZV 特征，如下：

**2.** 在 `raw_dt` 中，`SL2015` 的最常见值是 0 天休假，出现了 11,793 次。第二个最常见的值是 60 天休假，出现了 604 次。因此，频率比为 19.52。此外，在总共 16,501 个观测值中，`SL2015` 的唯一值为 66。因此，唯一值百分比为 (66/16,501) = 0.0039。由于频率比大于 19（默认值），且唯一值百分比小于 10%，`SL2015` 将被标记为 NZV 特征。

我们将在模型构建前丢弃所有显示 NZV 的特征。

### 线性依赖

一个常见问题是特征之间的线性依赖。如果存在一组标量并非全为零，使得线性组合为零向量，则称一组特征是线性相关的。在流失数据中，我们有三个特征，即 `RM_REPORTEES_COUNT`、`RM_REPORTEE_MALE`、`RM_REPORTEE_FEMALE`，它们是线性相关的。

**1.** `RM_REPORTEES_COUNT` - (`RM_REPORTEE_MALE` + `RM_REPORTEE_FEMALE`) = 0

在尝试估计回归建模中的贝塔系数时，线性相关的特征会导致奇异矩阵，从而其中一个线性相关特征的贝塔系数可能无法估计。

请注意，如果矩阵的行列式为零，则称该矩阵为奇异矩阵，因此矩阵的逆无法计算。矩阵逆用于估计贝塔系数。线性相关特征可能产生的另一个问题是多重共线性。多重共线性将在下一节讨论。

`caret` 包中的 `findLinearCombos()` 函数使用矩阵的 QR 分解来枚举线性组合的集合。

![](img/page187-01.png)

有两个特征列表是线性相关的。

**1.** 特征编号 16、17 和 18 分别是 `RM_REPORTEES_COUNT`、`RM_REPORTEE_MALE` 和 `RM_REPORTEE_FEMALE`。

**2.** 特征编号 2、15 和 20 分别是 `EMPLOYEE_AGE_DURING_DOJ`、`RM_AGE` 和 `AGE_DIFFERENCE`：

**3.** 特征编号 23（`LEAVE_PREVIOUS_YEAR`）是 `CL2014`、`PL2014` 和 `SL2014` 的总和。

**4.** 特征编号 24（`LEAVE_CURRENT_YEAR`）是 `CL2015`、`PL2015` 和 `SL2015` 的总和。

我们在进行模型构建前必须丢弃其中一个或多个特征。

### 多重共线性

让我们分析变量之间的相关性并丢弃高度相关的特征。我们将使用 `cor()` 函数在数值变量之间构建相关矩阵（表 6.6）。我们将绘制相关矩阵以进行视觉检查，并使用 `findCorrelation()` 函数报告在 0.70 截止值下高度相关的特征名称。

![](img/page188-01.png)

相关性热图显示在图 6.3 中。对角线表示特征与其自身的相关性，可以忽略。对于其他特征，较深的色调反映了高度相关的特征（正相关和负相关）。从图 6.3 中，我们可以看到存在高度相关的特征。

**1.** `AGE_DIFFERENCE` 与 `EMPLOYEE_CURRENT_AGE`、`EMPLOYEE_AGE_DURING_DOJ` 和 `RM_AGE` 高度相关



**2.** `INCREMENT_FROM_LAST_YEAR` 与 `AVG_WEIGHTED_PERFORMANCE`、`PL`、`CL`、`SL` 以及 `DAYS_WORKED_IN_LAST_QUARTER` 似乎高度相关

**3.** `DAYS_WORKED_IN_LAST_QUARTER` 与 `AVG_WEIGHT-ED_PERFORMANCE`、`PL`、`CL` 和 `SL` 高度相关

**4.** `PL`、`CL`、`SL` 彼此之间都高度相关。

**5.** `CTC_CURRENT_YEAR` 与 `CTC_PREVIOUS_YEAR` 高度相关

![](img/page188-02.png)![](img/page189-01.png)

热力图中还有其他高度相关的特征。然而，当特征集较大时，很难通过相关矩阵或热力图找出高度相关的变量。`caret` 包有一个函数 `findCorrelation()`，它将相关矩阵作为输入。在用户自定义的截止值下，该函数将打印在指定截止值下与其他变量相关的变量名称。有关 `findCorrelation()` 的详细说明，请参阅 第 5 章：

![](img/page189-02.png)

请注意，特征之间的线性依赖关系和相关性并不相同。特征之间高度相关并不一定意味着无法求出矩阵的逆。

本节中识别出的特征将从预测变量中移除。此外，在构建第一个模型后，由于其在预测中的不显著性，诸如 `AVG_WEIGHTED_PERFORMANCE`、`MARITAL_STATUS`、`CONFIRMATION_STATUS`、`GENDER` 和 `TENURE` 等特征也被移除。

添加或移除特征是一个迭代过程，在获得最终模型中将使用的特征列表之前可能需要多次模型运行。

![](img/page190-01.png)

#### 创建训练集和测试集

来自 `caret` 包的 `createDataPartition()` 函数提供了将数据集随机拆分为训练集和验证集的能力。以下代码可用于划分数据：

![](img/page190-02.png)

#### 模型构建：使用 caret() 包

为了构建逻辑回归模型，`caret` 包提供了一种方法 `glmStepAIC`，它通过查看赤池信息准则（AIC）来实现变量选择和剔除策略。

AIC 估计每个模型相对于给定变量集的其它模型的质量。因此，AIC 提供了一种通过保留较少的预测变量来构建简单模型的方法。

AIC 并不能提供关于原假设的模型检验，因此它并不能说明模型的绝对质量，而只能说明相对于其他模型的质量。

计算 AIC 的公式为

![](img/page191-01.png)

由于 −2 * `LL` 等于偏差。上式可改写为

![](img/page191-02.png)

其中

• 偏差为 −2* 对数似然估计，衡量与完美模型的偏差。

• `k` 是惩罚因子。只有 `k` = 2 时为 AIC，`k` = log(`n`) 有时被称为贝叶斯信息准则（BIC）。

• `P` 是模型中的参数数量。

下面的代码块使用 `glmStepAIC()` 方法实现逻辑回归模型。此方法调用来自 `MASS` 包的 `stepAIC()` 函数。

![](img/page191-03.png)![](img/page192-01.png)![](img/page193-01.png)![](img/page194-01.png)

需要注意的是，`glmStepAIC` 使用的是向后消除（默认）策略进行特征选择。如果我们想使用向前选择或向前选择和向后消除策略，可以指定 `direction = forward` 或 `direction = both`。

##### 理解 AIC 步骤

使用 `glmStepAIC` 构建的 `logistic_model` 产生了七次迭代。第一次迭代以初始 AIC 值为 3360.8 开始。让我们使用 [公式 \[6.9\]](#14_Chapter06.xhtml#eq6.9) 计算初始 AIC 值。为此计算，我们将使用 `glm` 方法创建一个完整模型对象。

![](img/page194-02.png)![](img/page195-01.png)

如图所示，初始 AIC 值与第 1 次迭代的起始 AIC 值相匹配。第 1 次迭代继续进行，其中每个特征都被从特征列表中剔除，并记录了由此产生的模型的 AIC 值。在第 1 次迭代中，`ZODIAC_SIGN` 被剔除。最后一次迭代产生了具有最小 AIC 值的最终模型。

有关 AIC 迭代的详细说明，请参阅 第 5 章。让我们使用向前选择、向后消除（`direction = both`）策略构建模型并用于模型诊断。我们还使用参数 `trace = 0` 来抑制迭代结果。

![](img/page195-02.png)

在进行模型诊断之前，让我们查看方差膨胀因子（VIF），它将显示是否存在多重共线性问题。查看 `step_logistic_model` 中的 VIF，我们可以推断模型中的变量均不存在多重共线性（值接近 1）。

![](img/page195-03.png)

#### 模型摘要

对象 `step_logistic_model` 包含最终模型。该模型对象的 `summary()` 显示了一些用于验证模型所需的统计信息。

![](img/page195-04.png)![](img/page196-01.png)

参考 [公式 \[6.1\]](#14_Chapter06.xhtml#eq6.1) 的函数形式，我们知道逻辑回归建模的是 `Y` = 1|`X` 的概率，即编码为 1（阳性）的事件的概率。在二分类问题中，`caret` 将第一个水平编码为阳性类别。在此场景中，`levels(train_dt$WORKING_STATUS)` 显示 `WORKING_STATUS` 有两个水平，即‘No’和‘Yes’。第一个水平（No）将被编码为阳性类别，即模型输出员工离职的概率。

`step_logistic_model` 的摘要打印了多个细节。让我们逐一描述它们：

**1.** 偏差残差汇总了训练数据中每个数据点计算的偏差。

**2.** 模型方程可以写成

![](img/page196-02.png)

其中 `Z = -3.53 + 0.71 * EMPLOYEECATEGORY[Operations] - 0.21 * EMPLOYEECATEGORY[Sales] + 0.03 * AGEDIFFERENCE - 0.06 * LEAVES_CURRENT_YEAR -0.09 * LEAVE_OVER_LAST_YEAR`

**3.** 空偏差对应于对数似然函数的 −2 倍（−2*`LL`[0]）。`LL`[0] 对应于没有自变量的似然函数，即在没有特征的情况下观察到结果的概率（似然）。在此数据（`train_dt`）中，总观测数为 6,037；阳性案例为 1,649（`Y` = 1 表示 No）；阴性案例为 4,388（`Y` = 0 表示 Yes）。

− `P(Y = 1)` = `π(Z)` = 1649 / 6037 = 0.2731 and

− `P(Y = 0)` = 1 − `π(Z)` = 4388 / 6037 = 0.7268.

使用 公式 (6.5) 的似然函数并代入 `π(Z)` 和 1 − `π(Z)` 的值，

![](img/page197-01.png)

**4.** 残差偏差对应于添加特征后对数似然函数的 −2 倍（−2*`LL`）*。`LL` 对应于具有自变量的似然函数，即在存在特征的情况下观察到结果的概率（似然）。在此场景中，包含自变量使偏差降至 3,304.4。残差偏差减少了 3,775.4 个单位（7,079.8 − 3,304.4）。在进行模型诊断时，我们将使用空偏差（−2`LL`[0]）和残差偏差（−2`LL`）执行似然比检验以找到模型的统计显著性。

**5.** Fisher Scoring 是牛顿-拉夫逊方法的一种派生，用于数值求解最大似然估计（MLE）函数，即找到最佳 `β` 系数。Fisher 值为 6 表示找到最佳 beta 系数、即模型收敛花费了六次迭代。Fisher 统计量在模型诊断中没有其他意义。

系数的符号可用于模型解释。



(a) 估计值前的正号意味着事件 (`Y` = 1) 的概率增加，即随着特征值的增加，员工离开组织的可能性增大。

(b) 估计值前的负号意味着事件 (`Y` = 1) 的概率随着特征值的增加而下降。

让我们阅读 `step_logistic_model` 的模型摘要，并对显著的特征/水平（`p`-value < 0.05）进行结果解释。在其他特征保持不变的情况下：

1. 在 Operation 角色（`EMPLOYEE_CATEGORY`）的员工中，离开组织的概率高于在非销售角色（基准类别）中离开组织的员工的概率。

2. 拥有本科学位（`DEGREE_TYPE`）的员工更有可能离开组织，相比于拥有研究生学位的员工。

3. `PRIOR_WORK_EXP` 每增加一个单位，员工离开组织的概率就会上升。这表明加入组织的经验丰富的员工拥有良好的背景，市场对他们的需求也更高。

4. 上一年薪资（`CTC_PREVIOUS_YEAR`）每增加一个单位，员工离开组织的可能性就会增加。模型并不意味着不应为员工加薪，而只是反映了经验丰富的员工获得更高薪资，而经验丰富的员工离开组织的可能性更大。

5. 从上一年到当年 CTC 的变化（`CHANGE_IN_CTC`）每变动一个单位，员工离开组织的可能性就会增加。这与前面的陈述也有关系。

6. 上季度工作天数（`DAYS_WORKED_IN_LAST_QUARTER`）每增加一个单位，员工离开组织的可能性就会增加。这可能是由于额外的工作压力，影响了员工的工作与生活平衡，并促使他寻找外部更好的机会。轻松地说，这符合“All work and no play makes Jack a dull boy. 的说法。

7. 上一年休假天数（`LEAVE_OVER_LAST_YEAR`）每增加一个单位，以及当年休假天数（`LEAVES_CURRENT_YEAR`）每增加一个单位，员工离开组织的可能性就会下降。这正好呼应了前面的陈述，并证实了工作与生活平衡在保持员工参与度方面发挥着重要作用。

**模型选择策略**有助于在最终模型中选择特征。诸如前向选择、后向消除或两者结合等策略的工作方式是，在模型构建阶段的每次迭代中报告的 `AIC` 或 `deviance` 都会下降。当模型的 `AIC` 或 `deviance` 在添加或移除特征时不再减少时，模型收敛。

8. 管理者下属女性人数（`RM_REPORTEE_FEMALE`）每增加一个单位，员工离开组织的概率就会下降。似乎团队中的多样性在员工保留方面发挥了一定作用。

9. 管理者与员工之间的年龄差异（`AGE_DIFFERENCE`）每增加一个单位，员工离开组织的可能性就会增加。这可能与代沟有关，似乎符合“Employees leave their manager and not the organisation. 的假设。

## 6.4 | 模型诊断

在实际应用之前，验证逻辑回归模型以确保其有效性和拟合优度非常重要。以下指标用于验证逻辑回归模型（Pradhan and Kumar, 2019）：

1. `Wald's test` 用于检验单个预测变量（特征）的统计显著性（相当于 MLR 模型中的 f 检验）。

`step_logistic_model` 返回了在显著性水平 `α` = 0.05 下统计显著的特征集合。请注意，分类特征中的某些水平并不显著。然而，可能不需要删除该特征，因为特征选择是使用 `AIC` 进行的。该特征有助于降低整体 `AIC` 值。

2. `Likelihood Ratio (LR)` 检验用于检验整体模型的统计显著性。LR 检验相当于执行 `χ2` 检验，其中

(a) 卡方值是模型[null deviance] 与模型[residual deviance] 之间的差值（`step_logistic_model$finalModel$null.deviance-step_logis-tic_mo del$ finalMo del$ deviance`）

(b) 相应的自由度是 `df`[null] 与 `df`[residual] 之间的差值（`step_logistic_model$finalModel$df.null-step_logistic_model$final-Model$df.residual`）

LR 检验也可用于变量（特征）选择。使用 `pchisq()` 函数的 LR 检验如下：

![](img/page198-01.png)

在此情况下，`χ2` 检验的结果 `p`-value 为零，这表明包含预测变量的模型与不包含任何预测变量的模型存在显著差异。因此，整体模型方程是有效的。

3. `Pseudo R²`：`Pseudo R²` 是衡量模型优度的指标。对于二元逻辑回归，`Pseudo R²` 值可使用以下方法得出

![](img/page198-02.png)

这被称为 McFadden Pseudo `R²`。该模型的 McFadden Pseudo `R²` 为 0.53：

![](img/page198-03.png)

它被称为伪 `R²`，因为它与 MLR 模型中的 `R²` 的解释不同。

### 6.4.1 测试数据上的预测

我们将使用 `step_logistic_model` 对测试数据进行结果预测。`predict()` 函数的 `type` 参数可以返回预测概率、logit 尺度上的预测概率以及预测类别。

1. 当 `type` = ‘link’ 时，`predict()` 返回 logit 尺度上的预测概率，即根据 式 (6.3)。

![](img/page199-01.png)

2. 当 `type` = ‘response’ 或 `type` = ‘prob’ 时，`predict()` 返回预测概率，即根据 式 (6.1)。**表 6.7** 显示了测试集上的预测概率。

![](img/page199-02.png)

逻辑模型的输出是类别概率值 `P`(`Y` = 1)。需要将该概率转换为类别值，以便了解模型在多少个观测中被正确分类，在多少个观测中未被正确分类。为了将概率值转换为类别，需要假设一个截止概率。默认情况下，截止概率假定为 0.50。所有预测概率大于 0.50 的观测将被预测为正类（本例中为 No）。

在 `predict()` 中传递 `type` = ‘raw’ 将在 0.50（默认值）的截止值下返回预测类别。

![](img/page199-03.png)

`test_predicted_class` 的前六个观测值将为 ‘No’。我们将在本章后面讨论可用于找到最佳截止概率的技术。然而，可以从实际类别（即结果特征 `WORKING_STATUS`）和预测类别（即使用 `predict()` 的结果）看出，一些分类是正确的，一些是错误的。为了获得更深入的见解，我们将从分类矩阵（也称为混淆矩阵）中计算一些统计数据。混淆矩阵是衡量真假分类的指标。

**表 6.7** | 测试预测概率

| 否 || 是 |
| --- | --- |
| 0.81 || 0.19 |
| --- | --- |
| 0.80 || 0.20 |
| 0.60 || 0.40 |
| 0.91 || 0.09 |
| 0.86 || 0.14 |
| 0.82 || 0.18 |

### 6.4.2 创建混淆矩阵



# 混淆矩阵

混淆矩阵（也称为误差矩阵或分类表）是通过检查数据中观测值的实际值和预测值针对特定分类截止概率而形成的矩阵。创建混淆矩阵时，我们将使用来自 `caret` 的 `confusionMatrix` 函数。该函数期望：

1. 预测类别和实际类别作为前两个参数传入。
2. 参数 `positive` 在 `confusionMatrix()` 中是可选的，并将使用实际类别中的第一个水平，即 (`test_dt$WORKING_STATUS`) 作为阳性结果（本例中为 No）。如果我们希望将模型解释为以 Yes 作为阳性类别，则可以将其更改为 Yes。
3. `mode=everything` 用于报告所有统计信息（默认值为 ‘`sens_spec`’）。

![](img/page200-01.png)

使用 `confusionMatrix()` 函数的混淆矩阵返回一个矩阵，其中行代表预测类别，而列代表实际类别。**表 6.8** 显示了测试集上的混淆矩阵。

![](img/page201-01.png)

大多数情况下，矩阵是倒置的，即行代表实际类别，列代表预测类别。`confusionMatrix()` 报告了许多统计信息，我们将在下一节讨论。需要注意以下几点：

1. 左上象限表示实际状态为 ‘No’（阳性类别）且正确分类为 ‘No。 这称为真阳性 (`TP`)。
2. 左下象限表示实际状态为 ‘No’ 但错误分类为 ‘Yes’。这称为假阴性 (`FN`)。
3. 右上象限表示实际状态为 ‘Yes’ 但错误分类为 ‘No’。这称为假阳性 (`FP`)。
4. 右下象限表示实际状态为 ‘Yes’ 且正确分类为 ‘Yes’。这称为真阴性 (`TN`)。

### 6.4.3 衡量模型准确性

在分类中，模型性能通常使用灵敏度、特异性、精确度、F 分数等概念来衡量。我们将在下面讨论 `confusionMatrix()` 报告的大多数统计信息。

### Accuracy

从分类矩阵可知，在 412 (`304+108`) 名离职员工中，有 304 例被正确分类。我们还知道，在 1,096 (`53+1043`) 名仍在组织的员工中，有 1,043 例被分类为在职。

整体模型准确率衡量的是总正确分类数占总案例数的比例。

![](img/page201-02.png)

`confusionMatrix()` 的输出报告整体模型准确率为 89%。它还报告了整体模型准确率的 95% 置信区间为 (0.88, 0.91)。

### No Information Rate

如果查看 HR 离职测试数据，‘Yes’ 的比例为 (`1096/1508`) * 100 = 72.7，‘No’ 的比例为 (`412/1508`) * 100 = 27.3。假设我们被给出测试数据并被要求在不使用任何模型的情况下预测每个案例的 `WORKING_STATUS`。假设凭借人类智能，我们将所有案例都预测或猜测为 Yes。那么在这种情况下模型的准确率竟然为 72.7%（不算差）。这意味着在对数据一无所知的情况下，我们的预测相当准确。这称为无信息率 (`NIR`)。`NIR` 指的是在没有任何数据（特征）情况下构建的模型的准确率。在许多情况下，我们希望使用数据构建的模型的准确率高于 `NIR`。我们有 89% 的模型准确率，但我们也想检验它是否显著大于 `NIR`。

1. `H[o]`: 模型准确率与 `NIR` 相同。
2. `H[a]`: 模型准确率与 `NIR` 不同。

对应上述假设，`confusionMatrix()` 报告的 `p-value` 为 2.2e-16。由于 2.2e-16 < 0.05，我们可以统计上说‘模型准确率优于 `NIR`’，即拒绝原假设。注意，上述假设检验等同于进行两样本比例检验。

### Kappa

从分类矩阵可知，`TP` 案例为 304，`TN` 案例为 1,043。然而，这些观察到的 `TP` 和 `TN` 案例可能是偶然发生的（由于测试样本）。我们如何确定正确分类不太可能偶然发生？Kappa 是一种考虑因偶然而正确分类的准确性度量。Kappa 值使用观察计数和期望计数按如下方式计算：

![](img/page202-01.png)![](img/page202-02.png)

在 公式 (6.15) 中，期望计数的分子为

1. (`TP` + `FP`) * (`TP` + `FN`) = `row_sum` * `column_sum` for `TP` cases in classification matrix
2. (`TN` + `FN`) * (`TN` + `FP`) = `row_sum` * `column_sum` for `TN` cases in classification matrix

公式 (6.15) 中的分母是分类矩阵中所有案例的总和，即 `TP+FP+TN+FN` = `margin`。

![](img/page202-03.png)

让我们使用测试数据上 `confusionMatrix()` 的结果计算 公式 (6.14)、(6.15) 和 (6.16) 的值。Kappa 值的范围为 (−1, 1)。

![](img/page202-04.png)

1. Kappa 值 > 0 表示分类优于随机分类。
2. Kappa 值 < 0 表示分类不优于随机分类。
3. Kappa 值为 1 为完美分类。
4. Kappa 值为 0 表示纯随机分类。

Kappa 值高于 0.70 表示分类准确性良好，低于 0.40 表示分类准确性较差。在本例中，测试数据上的 Kappa 值为 0.72，表明分类准确性合理。

### McNemar's Test

McNemar 检验是一种假设检验（*χ*² 独立性检验，*df* = 1），用于检验被错误分类案例中的计数（`FP` 和 `FN`）是否存在显著差异。换句话说，如果测试数据发生变化，被错误分类案例的比例（误差）是否会保持不变或不同。

1. `H[o]` = 被错误分类案例的比例将保持不变。
2. `H[a]` = 被错误分类案例的比例将不同。

检验统计量由下式给出

![](img/page203-01.png)![](img/page203-02.png)

使用卡方和 McNemar 检验计算的 p 值相同。然而，`confusionMatrix()` 函数报告的是带连续性校正的 McNemar 检验：

![](img/page203-03.png)

`confusionMatrix()` 报告的 McNemar 检验 P 值为 2.083e-5。这意味着如果测试数据发生变化，被错误分类案例的比例将显著不同（拒绝 `H[o]`）。该统计检验在训练和测试时间计算成本较高的深度学习模型中可能变得更加相关。

McNemar 检验也可以用于比较两个不同的二元分类模型。目标将是检验：‘在测试集的同一实例上，两个模型的被错误分类案例（误差）比例是否相同或不同’。

### Sensitivity (Recall or True Positive Rate)

灵敏度（也称为召回率或真阳性率）是在实际类别为阳性的条件下预测类别为阳性的条件概率（Kumar, 2017）。灵敏度和召回率是相同的统计量。数学上，灵敏度由下式给出

![](img/page203-04.png)

模型报告的灵敏度为 0.74。这意味着在所有离职员工中，模型正确分类了 74%。

### Specificity (True Negative Rate)

特异性是在实际类别为阴性的条件下预测类别为阴性的条件概率。数学上，灵敏度由下式给出

![](img/page204-01.png)



The model reported a sensitivity of 0.95. This means that of all the employees who are still working in the organization, the model classified 95% of them correctly. The terminologies sensitivity and specificity originated in medical diagnostics (Kumar, 2017; Anon, 2021).

### 精确率（阳性预测值）
Precision, also known as Positive Predicted Value (PPV), is the conditional probability that the actual value is positive given that the prediction by the model is positive (Pradhan and Kumar, 2019).

![](img/page204-02.png)
The model reported a precision of 0.85 which means that of all the positive predictions (‘No’) by the model, 85% were correct.

### F 分数
F-score is a measure that combines precision and recall (harmonic mean between precision and recall). Mathematically, F-score is given by

![](img/page204-03.png)
where `β` = 1 for `F1` score (weights precision and recall in the same way). Thus

![](img/page204-04.png)
This model reported a `F1` score of 0.79, which also suggests that both precision and recall will be reasonably good. `F1` score can be used to compare and select models with higher `F1` score.

We will also find reference to `F2` and `F0.5` score.
1. `F2` is obtained by setting `β` = 2 (weighs recall higher than precision).
2. `F0.5` is obtained by setting `β` = 0.5 (weighs precision higher than recall).

`F2` or `F0.5` scores may be desirable in case of applications where we want a model to have a higher recall compared to precision and vice versa.

### 其他度量
There are more statistics reported in the confusion matrix. We will summarize them here:
1. **患病率：** Proportion of positive cases in the actual data (`test_dt`). In this dataset, we have 412/1,508 = 0.2732.
2. **检出率：** The predicted positives as a proportion of overall cases. From the classification matrix, the value is 304/1,508 = 0.2016.
3. **检出患病率：** Total predicted positives (`TP` and `FP`) as a proportion of overall cases. The value is 357/1,508 = 0.2367. If detection rate and detection prevalence are close to each other, it means the model has misclassified a smaller number of positive cases.
4. **负预测值（Negative Predicted Value）：** Conditional probability that the actual value is negative (`TN`) given that the prediction by the model is negative (`TN+FN`). From the classification matrix, the value is 1,043/(1,043+106) = 0.9077.
5. **阳性预测值：** This is same as precision.
6. **平衡准确率：** ![](img/pageIn_ch6-01.png). The corresponding value is 0.8448.

### 6.4.4 接收器操作特性（ROC）与 ROC 曲线下面积
Receiver Operating Characteristic (ROC) curve can be used to understand the overall performance (worth) of a logistic regression model (and, in general, for binary classification models) and for model selection. The term has its origin in electrical engineering, when electrical signals were used to identify enemy objects (such as submarines and aircraft) during World War-II. ROC curve is a plot between sensitivity (true positive rate) in the vertical axis and 1 – specificity (false positive rate) in the horizontal axis (Kumar, 2017).

`ROCR` package can be used to evaluate the model performance on the train data. The same package can also be used to get the model performance on the test data. The function `prediction` and `performance` from `ROCR` package is used to get the plot of ROC.
1. `prediction()` expects the prediction object, that is, `predicted_prob` (calculated earlier on `test_dt` using `predict()`) and true class label, that is, `test_dt$WORKING_STATUS` as parameters. Note that the function goes with the default label ordering of R (‘No’<‘Yes’), that is, it will treat No = 0 (negative class) and Yes = 1 (positive class). However, the `confusionMatrix()` function from the `caret` package marked No =1 (positive class). So, in order to get the correct ROC curve, we will use the parameter `label.ordering = c('Yes','No')` to treat ‘No’ as the positive class.

Intuitively, the `prediction()` function calculates predicted class labels and classification matrix using the input parameter (`predicted_prob`, true class label) and a set of 100 cut-off values in the range (0.00, 1.00). For every cut-off value, the function calculates below measures (counts) and stores them as list.
1. `n.pos` and `n.neg`: number of positive and negative samples in the data
2. `tp`, `fp`, `tn`, `fn`: number of true positive, false positive, true negative, and false negative at a specific cut-off
3. `n.pos.pred` and `n.neg.pred`: number of samples predicted as positive and negative at a specific cut-off

The cut-offs at which calculated measures are same is removed from the list returned by `prediction()` function.

Let us get the ROC curve and AUC using the `ROCR` package. First, we used the `prediction` function to compute various measures. The data type of `rocr_prediction` object is a list which contains various measures discussed above.

![](img/page205-01.png)
These measures are used by `performance()` function of `ROCR` package to get various plots like ROC, Gain Chart, Lift Chart, custom charts, etc.
2. `performance()` takes input from the prediction object and uses it to compute various statistics and plots like “auc”, “roc plot”, precision recall plot“,”lift chart”, etc.

We can use the `performance()` function and pass the `test_rocr_prediction` object as a parameter. Since ROC is a plot between true positive rate (`tpr`) and false positive rate (`fpr`), the performance function will calculate the statistics. In order for performance to compute `tpr` and `fpr`, we will pass them as parameters as well.

![](img/page205-02.png)![](img/page206-01.png)
In **图 6.4**, the diagonal line represents the case of not using a model (no discrimination between positive and negative classes); the area below the diagonal line is equal to 0.5 (it is a right-angle triangle, area of right-angle triangle is 0.5 `ab`, where `a` and `b` are the length of the sides, which is equal to 1 in this case). Sensitivity and/or specificity is likely to change when the cut-off probability is changed. The line above the diagonal line captures how sensitivity and (1 − specificity) change when the cut-off probability is changed. A Model with a higher AUC is preferred and AUC is frequently used for model selection. Since we also want to report AUC, we will again call the `performance` function and pass `AUC` as a parameter to report area under the ROC curve. AUC can be interpreted as the probability of correctly classifying a random pair of positive and negative class records.

![](img/page206-02.png)
As a thumb rule, AUC of at least 0.7 is required for practical application of the model. AUC of greater than 0.9 implies an outstanding model. Caution should be used while selecting models based on AUC, especially when the data is imbalanced (i.e., dataset which has less than 10% positives). In case of imbalanced datasets, the AUC may be very high (greater than 0.9). However, either sensitivity or specificity values may be poor.

For this example, the approximate value of AUC is 0.91 which implies that ‘picked at random, an employee who left the organization and one who is currently working in the organization, the model will be correctly able to classify both of them correctly, 91% of the times.

### 6.4.5 寻找最佳分类截断值
While using logistic regression model, one of the decisions a data scientist has to make is to choose the right classification cut-off probability. The overall accuracy, sensitivity, and specificity will depend on the chosen cut-off probability. The following two methods are used for selecting the cut-off probability.
1. Youden’s Index
2. Cost-based approach

### Youden 指数



## Youden 指数

敏感性和特异性在我们改变截止概率时会发生变化。Youden 指数（Youden, 1950）是使以下函数最大化的分类截止概率（也称为 /-统计量）：

![](img/page207-01.png)

也就是说，选择使 `tpr+tnr−1` 最大化的截止概率。`tpr` 为真阳性率，`tnr` 为真阴性率。

请注意，在尝试寻找最佳截止值时，我们必须使用 `train_dt` 而不是 `test_dt`。我们将使用 `prediction()` 创建 `train_rocr_prediction` 对象，然后使用计算 `tpr` 和 `tnr` 所需的指标。

![](img/page207-02.png)

`表 6.9` 显示了 `train_rocr_prediction_measures` 数据框中的前六个观测值。

让我们通过将 `train_rocr_prediction` 参数传递给 `performance()` 来计算 `tpr` 和 `fpr`。`表 6.10` 显示了 `train_rocr_performance` 数据框中的前六个观测值。

![](img/page207-03.png)![](img/page207-04.png)

**表 6.10** | 训练 ROCR 性能指标

| Fpr || tpr |
| --- | --- |
| 0.0000000 || 0.0000000 |
| --- | --- |
| 0.0000000 || 0.0042450 |
| 0.0002279 || 0.0806549 |
| 0.0006837 || 0.2395391 |
| 0.0015953 || 0.3917526 |
| 0.0018232 || 0.4863554 |

让我们使用 `cbind()` 函数将 `train_rocr_prediction_measures` 和 `train_rocr_performance_measures` 绑定。`表 6.11` 显示了合并后的数据框。

![](img/page208-01.png)

由于假阳性率 (`fpr`) = 1 − 真阴性率 (`tnr`)，我们可以将 Youden 指数计算为 `tpr-fpr`。`表 6.12` 显示了使用下面代码片段计算的 Youden 指数。

![](img/page208-02.png)

`表 6.13` 显示 0.26 是使 `train_dt` 上的 Youden 指数最大化的截止值。之前我们使用 `predict()` 在 `test_dt` 上保存了 `test_predicted_prob`。让我们在 `test_dt` 上使用 `best_cutoff` 并构建分类矩阵。

![](img/page208-03.png)![](img/page208-04.png)![](img/page209-01.png)![](img/page209-02.png)

我们可以将截止值为 0.26 时的上述结果与默认截止值 0.50 时的结果（在 第 6.4.2 节 中）进行比较。我们可以得出结论，0.26 的截止值提高了敏感性。

### 基于成本的方法

在基于成本的方法中，我们为正例和负例的误分类分配惩罚成本。假设假阳性率 (`FPR`) 的成本为 `C1`，假阴性率 (`FNR`) 的成本为 `C2`。那么，惩罚定义为

![](img/page209-03.png)

最优截止概率是使总惩罚最小化的概率。让我们为 HR 流失问题构建一个成本矩阵。在这里，人力资源的主要目标是拥有一个模型，即使模型将一些仍在工作的员工的案例误分类，也能正确分类可能离开组织的员工。

**微调截止概率**是在部署模型结果用于决策时需要考虑的重要因素。Youden 指数、误分类成本等技术用于微调二元逻辑回归模型的截止概率。

![](img/page210-01.png)![](img/page210-02.png)

按照上述目标，我们可以制定一个成本矩阵，其中将“否”误分类为“是”的惩罚是将其误分类为“否”的两倍。

![](img/page210-03.png)

让我们使用上述成本矩阵和 `optimal_cutoff_df` 根据 公式 (6.23) 计算惩罚。`表 6.14` 显示了包含误分类成本列的结果表。

![](img/page210-04.png)

我们发现，在 `train_dt` 上使惩罚最小化的最佳截止值为 0.16 **（表 6.15）**。请注意，基于 Youden 指数的截止值被发现为 0.26 **（表 6.13）**。

之前我们使用 `predict()` 在 `test_dt` 上保存了 `test_predicted_prob`。让我们在 `test_dt` 上使用 `best_cutoff` 并构建分类矩阵。

![](img/page210-05.png)![](img/page211-01.png)

我们可以将上述混淆矩阵（截止值为 0.16）与混淆矩阵（Youden 指数截止值为 0.26，在 第 6.4.5 节 中）进行比较。我们可以得出结论，与截止值为 0.26 时的敏感性相比，截止值为 0.16 的敏感性有所提高。

## 6.5 | 增益图和提升图

增益图和提升图（Kumar, 2017）是衡量使用逻辑回归模型（一般分析模型）的益处的两个指标，并用于目标营销等商业场景。在目标营销或营销活动中，客户对活动的响应通常非常低（在许多情况下，响应营销活动的客户不到 1%）。另一个低响应的例子是互联网广告（如 Google Adwords 和移动广告）。组织将为每次客户联系产生成本，因此希望在尽量减少营销活动成本的同时实现客户的期望响应水平。增益图和提升图是通过以下步骤获得的：

**1.** 使用 LR 模型预测正响应概率（`Y` = 1），并按预测概率的降序排列观测值 [即 `P(Y = 1)`]。

**2.** 将数据集分为十分位。计算每个十分位中正例（`Y` = 1）的数量以及到该十分位为止的正例累计数量。

**3.** 增益是到某一十分位为止的正观测值累计数量与数据中正观测值总数之间的比率。增益图是在纵轴为增益、横轴为十分位的图表。

![](img/page212-01.png)

让我们将增益图应用于 HR 流失数据。从 `test_dt` 我们知道有 27% 的正例，即 No（`Y` = 1）。`test_dt` 中的案例总数为 1,508。如果我们使用随机模型从 1,508 个案例中挑选 10%，我们将大约有 41 名员工的 `WORKING_STATUS` = No，即正例。我们可以说随机模型的正预测率为 27%。让我们看看 LR 模型相对于随机模型提供了多少增益。

![](img/page212-02.png)

在随机模型将挑选 27% 正预测率（`Y` = ‘No’）的水平上，`step_logisitic_model` 将给出大约 79% 的正预测率 **（表 6.16）**。**图 6.5** 显示了使用 `performance()` 返回的增益对象绘制的增益图。

![](img/page212-03.png)

**4.** 提升是使用 LR 模型到十分位 *i* 的正观测值数量与基于随机模型（不使用模型）到该十分位 *i* 的预期正例数量之比。提升图是在纵轴为提升、横轴为相应十分位的图表。

![](img/page212-04.png)![](img/page212-05.png)![](img/page213-01.png)

让我们在 `test_dt` 上使用提升。

![](img/page214-01.png)

在随机模型将挑选 27% 正预测率（`Y` = ‘No’）的水平上，`step_logisitic_model` 将产生随机模型的 2.96 倍，即正例率约为 79% **（表 6.17）**。**图 6.6** 显示了使用 `performance()` 返回的提升对象绘制的提升图。

![](img/page214-02.png)![](img/page215-01.png)![](img/page216-01.png)![](img/page216-02.png)



在对 HR 离职数据进行的所有分析之后，我们可以得出结论，逻辑回归模型将有助于 HR 获得以下几个方面的洞察：

**1.** 该模型可用于了解员工离开组织的原因。HR 可以采取果断行动留住对业务至关重要的员工。

**2.** 该模型可用于预测员工在一定时间段内的行为（`WORKING_STATUS`）。预测结果还可以为对业务至关重要的员工制定备份策略提供依据。

**3.** 在组织层面，增益图和提升图可用于了解各部门员工的行为。可以对各部门进行政策层面的变更以留住员工（例如，销售岗位的员工每季度可休假等）。

诸如**模型的增益和提升**之类的指标是理解模型有效性的又一种有力方式。它有助于理解模型在决策中相对于不使用任何模型做决策所能带来的增量收益。

二元逻辑回归是处理分类问题的一种有用技术。在下一节中，我们将讨论决策树，这是处理同类问题的另一种流行技术。

## 6.6 | 决策树学习

决策树学习或决策树是一组分而治之的解决问题策略，使用树状结构（根在顶部的倒置树）来预测结果变量的值（Kumar, 2017）。树从包含完整数据的根节点开始，然后使用智能策略将节点（父节点）拆分为多个分支（从而创建子节点）。原始数据被划分为同质子集。这样做是为了在子节点处创建更同质的组。它是用于生成业务规则的最强大的预测分析技术之一。分类与回归树（`CART`）是分类树（当因变量为离散时使用）和回归树（当因变量为连续时使用）的通用术语。分类树在分类问题中利用诸如基尼不纯度指数和熵等各种不纯度度量来分割节点（Kumar, 2017）。另一方面，回归树分割使平方误差和（`SSE`）最小化的节点。生成分类树和回归树的步骤如下，

**1.** 在根节点开始时使用完整的训练数据。

**2.** 确定不纯度度量，即基尼不纯度指数或熵。搜索在父节点拆分为子节点时使不纯度最小化的预测变量。这发生在原始数据使用预测变量划分为两个子集时，从而在因变量为离散的情况下实现不纯度的最大减少，或在因变量为连续的情况下实现 `SSE` 的最大减少。

**3.** 使用自变量对数据的每个子集（每个内部节点）重复步骤 2，直到：

(a) 所有因变量均已耗尽。

(b) 满足停止标准。使用的一些停止标准是从根节点开始的树的层数、父/子节点中的最小观测数（例如，训练数据的 10%）以及不纯度指数的最小减少量。

**4.** 为树的叶节点（终端节点）生成业务规则（预测规则）。预测的类别是叶节点中的多数类。

我们可以使用 `caret` 构建决策树模型。通过 `train()`，`caret` 提供了 `method = rpart`，它内部使用来自 `rpart` 包的 `rpart()`。`rpart` 代表 Recursive PARTitioning，即 `CART` 的一种实现。

**1.** 如果结果变量（`Y`）是离散的，`rpart()` 会通过内部设置（`method = "class"`）将其识别为分类问题

**2.** 如果结果特征是数值型的，`rpart()` 会通过内部设置（`method = "anova"`）将其识别为回归问题

有各种参数，经过微调后可能会导致具有不同业务规则的决策树模型。换句话说，微调参数可能会导致在 `test_dt` 上更具泛化能力的决策树模型。通过 `rpart` 可用的一些参数显示在 **表 6.18.** 中。

`rpart` 会继续递归分割节点，除非违反 `minsplit` 或 `minbucket`，或分割不会降低由复杂度参数 `cp` 评估的树的成本。`cp`（定义在 **表 6.18.** 中）可以是 (0, ∞) 之间的值。因此，我们将 `cp` 称为微调参数（或超参数），其最佳值对于给定的 `train_dt` 需要从一系列值中确定。为了找到最佳值，我们需要创建交叉验证集，在这些集合上测试不同的 `cp` 值，并将导致误差（成本）最小化最多的值用于模型构建。此参数可使用 `caret` 中的 `method = rpart` 进行微调。实际上，我们也可以将 `minsplit` 和 `minbucket` 视为微调参数，但 `caret` 除非编写自定义代码，否则不提供微调它们的选项。

![](img/page217-01.png)![](img/page218-01.png)

作为 `rpart()` 的一部分，还有一组四个参数有助于该技术处理缺失值问题。因此，决策树也可作为执行数据插补的技术使用。这些参数显示在 **表 6.19.** 中。

因此，与许多其他技术（选择忽略该问题）相比，`rpart` 在处理数据、缺失值问题方面更稳健。具有缺失观测的特征在节点中是使用替代变量进行分类的。³ 如果数据中没有缺失值问题，将 `maxsurrogate` 设置为 `0` 是有用的（可节省计算时间）。

![](img/page218-02.png)

让我们了解上述代码行将如何工作。`grid_params` 定义了需要搜索的 `cp` 参数的范围。在 `control_params` 中，我们定义了模型训练开始时要使用的训练环境。我们已指定使用 `5-cross-validation`（`5-CV`）策略来微调 `grid_params` 中定义的复杂度参数 `cp`。当调用 `train()` 进行模型构建时，`control_params` 将定义一个空间，在该空间中 `grid_params`（本例中为 `cp`）将被微调。

**图 6.7** 描述了 `5-CV` 策略。让我们建立其直觉：

**1.** `5-CV` 集将 `train_dt` 划分为五个子集，使得每个子集大约具有相同数量的观测值。在 **图 6.7** 中，列 ‘`Set_1`’、‘`Set_2`’、‘`Set_3`’、‘`Set_4`’ 和 ‘`Set_5`’ 表示创建的五个子集。

![](img/page218-03.png)

**2.** 从 `grid_params` 中选取一个 `cp` 值（假设 `cp = 0.001`）。

(a) **迭代 1：** 使用（`Set_2` 至 `Set_5`）开发决策树模型（假设为 `Model_1`），并在保留样本（`Set_1`）上评估其性能。

(b) **迭代 2：** 使用（`Set_1` 和 `Set_3` 至 `Set_5`）开发决策树模型（假设为 `Model_2`），并在保留样本（`Set_2`）上评估其性能。

(c) **迭代 3：** 使用（`Set_1` 至 `Set_2` 和 `Set_4` 至 `Set_5`）开发决策树模型（假设为 `Model_3`），并在保留样本（`Set_3`）上评估其性能。

(d) **迭代 4：** 使用（`Set_1` 至 `Set_3` 和 `Set_5`）开发决策树模型（假设为 `Model_4`），并在保留样本（`Set_4`）上评估其性能。




## 6.6 模型训练与评估

(e) **第 5 次迭代：** 使用 (`Set_1` 至 `Set_4`) 开发一个决策树模型（假设为 `Model_5`），并在保留样本 (`Set_5`) 上评估其性能。

**3.** 计算并保存五个保留样本的平均性能。我们将定义一个指标（假设为 `Accuracy`），模型的性能将基于此指标报告（在 `train()` 中）。

**4.** 对每个 `grid_params` 值重复步骤 2，即 `cp` 在 (0.001 到 0.02) 范围内。

**5.** 找到在保留样本上表现最好的 `grid_params` 值。

**6.** 使用最佳参数值（`cp` 值）基于 `train_dt` 构建决策树模型。

请注意，当我们定义 `k`-CV 集时，总共会构建 `k + 1` 个模型。`k` 个模型用于寻找最佳参数组合，而第 (`k + 1`) 个模型是最终模型，它使用 `k` 个模型的最佳参数值构建。通常，`k` 的值设置为 5 或 10（经验上，这些值显示测试误差不会受到偏差或方差的影响）。随着 `k` 的增大，训练集与交叉验证子集之间的差异会变小。这是为了保持一个在统计上代表训练数据的子集。

我们现在准备开发决策树模型。让我们定义 `train()` 函数来构建决策树模型。

![](img/page219-01.png)

请注意，在调用 `train()` 之前使用了 `set.seed()`。这是为了确保在 `train()` 的调用之间使用相同的交叉验证集（`resamples`）。然而，如果涉及并行处理（此处未使用），在 `train()` 之前设置种子可能无法保证使用相同的重采样。我们在 `trainControl()` 中有一个 `seeds` 参数，应在重采样中创建模型时（使用并行处理）进行设置。我们将在后续章节讨论此选项。

`params` 是一个可选参数，对于分类问题，其默认值为：

**1.** `Prior` 是结果变量的先验概率。它从数据中估计得出。

**2.** `Loss` 是矩阵，通过它我们可以惩罚 `FPR` 和 `FNR`，以最大化灵敏度或特异性。内部地，损失矩阵会改变先验，从而影响在每个节点拆分数据集时变量的选择，在适当的地方给予更大权重（Williams, 2010）。

**3.** `Split` 默认设置为 `gini`。如果不纯度度量的标准是熵，我们可以设置为 `information`。

此外，`minsplit` 和 `minbucket` 是在 `method = rpart` 时适用的参数（上面已讨论）。`trControl` 和 `tuneGrid` 是 `train()` 的参数，我们已向其传递了从 `trainControl()` 和 `expand.grid()` 创建的对象。我们还可以使用 `train()` 的 `tuneLength` 参数来微调参数（将在 第 7 章 中讨论）。

让我们打印 `decision_tree_model`。

![](img/page220-01.png)![](img/page221-01.png)

上述输出显示了输入特征的高级统计信息、应用的采样策略等。然而，重要信息是尝试过的各种 `cp` 值。使用的最终 `cp` 值为 0.019，因为该值在交叉验证集上获得了最佳 kappa。我们将使用 `rpart.plot()` 绘制业务规则。

![](img/page221-02.png)

**图 6.8** 是 `decision_tree_model` 业务规则的可视化表示。规则是为终端（叶）节点生成的。让我们了解如何读取节点值：

**1.** 第一个节点（节点编号 1），即起始节点，其标签为‘Yes’。这意味着观测值数量最多的是‘Yes’类型。‘Yes’的比例为 73%（‘No’为 27%）。由于这是起始节点，它包含所有观测值，即 100% 的数据都在此节点中。

**2.** 第一个终端节点（标记为 4）标记为‘No’。这意味着观测值数量最多的是‘No’类型。‘No’的比例为 98%（‘Yes’为 2%）。该节点包含总体观测值的 18%。

我们可以通过 `print(decision_tree_model$finalModel)` 以文本格式获取业务规则。

![](img/page221-03.png)![](img/page222-01.png)

带星号标记的节点是叶节点。`rpart.plot()` 使用这些规则在 **图 6.8** 中进行可视化。决策树的优点如下：

**1.** 生成的规则简单且可解释。树可以可视化。

**2.** 对数值和分类数据都适用。无需对数据进行标准化，也无需创建虚拟变量。

**3.** 规则可以帮助制定业务策略。

### 6.6.1 创建混淆矩阵

让我们构建一个分类（混淆）矩阵来理解决策树模型。要创建混淆矩阵，我们将使用 `caret` 中的 `confusionMatrix` 函数。该函数期望：

**1.** 将预测类别和实际类别作为前两个参数传递。

**2.** 参数 `positive` 是可选的，它将使用实际类别中的第一个水平，即 (`test_dt$WORKING_STATUS`) 作为阳性结果（本例中为 No）。如果我们想将 Yes 作为阳性结果来解释模型，可以将其更改为 Yes。

**3.** `mode = everything` 用于报告所有统计信息（默认值为‘`sens_spec`’）。

![](img/page222-02.png)![](img/page223-01.png)

### 6.6.2 接收器操作特征（ROC）曲线和 ROC 曲线下面积（AUC）

我们在逻辑回归中对 ROC 和 AUC 的实现有详细概述。让我们报告 `decision_tree_model` 的 ROC 和 AUC。

让我们使用 `ROCR` 包获取 ROC 曲线和 AUC。首先，我们使用 `prediction` 函数计算各种度量。`rocr_prediction` 对象的类型是一个列表，其中包含本节讨论的各种度量。

![](img/page223-02.png)

这些度量由 `ROCR` 包的 `performance()` 函数使用，以获取 ROC、增益图、提升图、自定义图表等各种图表。

`performance()` 从 `prediction` 对象获取输入，并使用它们计算各种统计信息和图表，如“`auc`”、“roc plot”、“precision recall plot”“lift chart”等。

让我们使用 `performance()` 函数并将 `test_rocr_prediction` 对象作为参数传递。由于 ROC 是 `tpr` 和 `fpr` 之间的图，performance 函数将计算统计信息。为了使 performance 计算 `tpr` 和 `fpr`，我们也将它们作为参数传递。

![](img/page223-03.png)

**图 6.9** 显示了决策树模型的 ROC 曲线。当截止概率改变时，灵敏度和/或特异性可能会发生变化。斜线以上的线捕捉了当截止概率改变时灵敏度和 (1 − 特异性) 的变化。AUC 较高的模型更受青睐，并经常用于模型选择。`decision_tree_model` 的 AUC 为：

**交叉验证策略** 有助于微调高级机器学习模型的超参数。如果超参数的数量和为微调超参数而定义的网格空间非常大，该策略可能会变得计算成本高昂。

![](img/page224-01.png)

**多模型策略** 可能有助于减少特征空间，从而降低模型的复杂性，而不会对最终模型的性能统计造成重大变化。

![](img/page224-02.png)

对于此示例，AUC 为 0.88，这意味着‘随机给定一名已离开组织的员工和一名目前在组织工作的员工，模型将能够正确分类他们 88% 的时间’。

## 6.7 模型选择

一个有趣的点需要注意的是，传递给 `rpart()` 用于模型训练的 17 个特征中，最终的 `decision_tree_model` 只有四个特征。特征如下：

**1.** `DAYS_WORKED_IN_LAST_QUARTER`



2. `LEAVES_CURRENT_YEAR`
3. `EMPLOYMENT_TYPE`
4. `LEAVE_OVER_LAST_YEAR`

使用这四个特征的 `decision_tree_model` 帮助报告了合理的 F1 分数、模型准确率以及所有其他性能统计指标。在传递给 `glmStepAIC` 用于模型训练的同 17 个特征中，最终的 `step_logisitic_regression` 保留了十个特征（参见 第 6.3 节）：
1. `EMPLOYEE_CATEGORY`
2. `PRIOR_WORK_EXP`
3. `DAYS_WORKED_IN_LAST_QUARTER`
4. `CTC_PREVIOUS_YEAR`
5. `DEGREE_TYPE`
6. `RM_REPORTEE_FEMALE`
7. `CHANGE_IN_CTC`
8. `AGE_DIFFERENCE`
9. `LEAVE_OVER_LAST_YEAR`
10. `LEAVES_CURRENT_YEAR`

决策树模型使用的三个特征是最终逻辑回归特征列表的一部分。让我们比较 `step_logistic_model` 和 `decision_tree_model` 的 F1 统计量和 AUC：
1. `step_logisitic_model` 报告的 F1 分数为 0.7906，AUC 为 0. 9091（无最优截断值）。
2. `decision_tree_model` 报告的 F1 分数为 0.8548，AUC 为 0.8898。

现在，我们应该选择哪个模型？我们知道 ROC 是针对不同阈值水平（截断值）构建的。这意味着 ROC 曲线本身具有许多不同的 F1 分数值。
1. 当阈值下精确率和召回率都很高时，F1 分数会很高。
2. 其中 ROC 曲线的 AUC 对所有阈值取平均。

因此，当数据中存在类别不平衡时，这在 HR 离职数据中也是如此，选择具有更好 F1 分数的模型可能是有用的。因此，从 F1 分数和模型简洁性角度来看，似乎 `decision_tree_model` 比 `step_logisitic_model` 更好。

请注意，模型选择同时考虑模型简洁性和使用 F1 分数可能不是选择最终模型的唯一标准。可能还有各种其他业务约束和背景，最终决定部署哪个模型。

请注意，为了突出多模型方法，作为练习，我们还使用决策树模型保留的特征重建了 `step_logisitic_regression`。在 `test_dt` 上，重建的 `step_logistic_regression` 模型的 F1 分数和 AUC 分别为 0.8150 和 0.8810。有趣的是，如何使用一个模型的特征列表来简化现有模型，而性能统计指标几乎没有重大变化。读者可以自行重建逻辑回归模型并验证结果。

### Summary
1. 在分类问题中，因变量 `Y` 取有限离散值。逻辑回归是用于解决分类问题最流行的技术之一。
2. 逻辑回归提供事件发生的概率；最终类别通常使用分类截断概率预测。
3. 决策树生成可解释的规则，企业可以在此基础上制定策略。
4. LR 模型的准确性使用灵敏度、特异度、F 分数、精确率和 ROC 曲线下面积等指标来衡量。最终模型选择可以使用这些指标中的任何一个进行。
5. 最优分类截断概率通常使用 Youden’s Index 或基于成本的方法计算。
6. Gain 和 Lift 图是两种在处理不平衡数据集的分类问题时用于定位正类的技术。

### Exercises
#### Answer Questions 1 to 10 using the `SAheart` Dataset.
使用 `SAheart` 数据集回答第 1 至 10 题。
数据集 `SAheart.data` 来自以下链接：[`www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data`](http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data)

数据集 `SAheartrateData.txt` 包含南非西开普省心脏病高风险地区男性的记录。CHD 病例约有两名对照。许多 CHD 阳性男性在 CHD 事件后接受了降压治疗和其他降低危险因素的项目。在某些情况下，测量是在这些治疗后进行的。这些数据取自 Rousseauw 等人（1983 年）描述的一个更大数据集，*南非医学杂志*。它是一个制表符分隔文件（.csv），包含以下列：
• `sbp` – 收缩压
• `tobacco` – 累计吸烟量（千克）
• `ldl` – 低密度脂蛋白胆固醇
• `adiposity`
• `famhist` – 心脏病家族史（存在、缺失）
• `typea` – A 型行为
• `obesity`
• `alcohol` – 当前酒精摄入量
• `age` – 发病年龄
• `chd` – 结果，冠心病
1. 构建逻辑回归模型来预测患 `chd`（冠心病）的概率，即 `P(chd = 1)`。使用除 `chd` 之外的所有其他列作为特征构建模型。
2. 找出第 1 题构建的逻辑回归模型中统计显著的特征。仅使用显著特征构建新的逻辑回归模型。
3. 根据逻辑回归模型参数，确定哪些参数对 `chd` 的概率产生积极影响，哪些产生消极影响。
4. 计算从 0.0 到 1.0、间隔为 0.01 的所有可能截断概率的 Youden 指数。找到 Youden 指数最大时的最优截断值。
5. 基于第 4 题找到的截断概率构建混淆矩阵，并报告模型对 `chd` 病例（即 `chd` = 1）的精确率和召回率。
6. 使用基于成本的方法找到最优截断概率，使用 FPs 和 FNs 的成本定义如下。
• 将“`chd`”预测为“无 `chd`”（FNs）病例的成本是把“无 `chd`”预测为“`chd`”（FPs）的五倍。
• 然后找到模型对 `chd` = 1 的精确率和召回率。
7. 使用基尼指数和最大深度为 4 构建决策树分类模型来预测 `chd` = 1 的概率。
8. 比较决策树分类器和逻辑回归模型的性能。解释哪种准确率分数可用于找出哪个模型在将 `chd` 与 *无 chd* 病例分类方面更好。
9. 绘制决策树并找出顶节点最重要的分裂标准。解释决策树分类器顶节点的基尼指数是如何得出的。
10. 如果使用基尼指数作为分裂标准，找到决策树分类器的最优 `depth`。搜索 3 到 10 范围内的可能深度，并使用 ROC 和 AUC 作为评分来找到最优 `depth`。

#### Answer Questions 11 to 15 using the `HR` Dataset.
使用 `HR` 数据集回答第 11 至 15 题。
数据集 `hrdata.csv` 包含某招聘公司客户招聘流程中候选人的样本。该公司为印度多家信息技术（IT）公司提供人才招聘支持。他们面临的一个挑战是约 30% 接受工作 offer 的候选人最终没有加入公司。这导致公司重新启动招聘流程以满足人力需求，从而造成巨大的收入和时间损失。该公司想知道是否可以建立模型来预测候选人加入公司的可能性。如果可能性很高，公司就可以继续向候选人提供工作。

数据集包含有关候选人的多个属性，以及一个列（或变量）指示候选人是否最终会加入公司。以下是候选人属性的描述：
• `Candidate` – 参考编号；它是用于识别候选人的唯一编号
• `DO/ extended` – 二元变量，标识候选人是否要求入职日期延期（是/否）
• `Duration to accept the offer` – 候选人接受 offer 所需的天数（尺度变量）
• `Notice period` – 候选人在离职公司需履行的通知期，然后才能加入本公司（尺度变量）



# 变量定义

-   `Offered band` – 基于经验、面试轮次表现向候选人提供的职级（C0/C1/C2/C3/C4/C5/C6）
-   `Percentage hike expected` – 候选人期望的涨薪百分比（尺度变量）
-   `Percentage hike offered` – 公司提供的涨薪百分比（尺度变量）
-   `Joining bonus` – 二元变量，表示是否提供入职奖金（是/否）
-   `Gender` – 候选人的性别（男/女）
-   `Candidate source` – 获得候选人简历的来源（员工推荐/招聘机构/直接）
-   `REX` (年) – 候选人对所提供职位相关的年工作经验（尺度变量）
-   `LOB` – 提供 offer 的业务线（分类变量）
-   `Date of Birth` – 候选人的出生日期
-   `Joining location` – 为候选人入职而发出 offer 的公司地点（分类变量）
-   `Candidate relocation status` – 二元变量，表示候选人入职是否需要从一个城市搬迁到另一个城市（是/否）
-   `HR Status` – 候选人的最终入职状态（已加入/未加入）

## 任务

### 11. 建立逻辑回归模型来预测候选人加入公司的概率。假设 `Not Joined` 为阳性案例，`Joined` 为阴性案例。

### 12. 从 `LR` 模型中找到显著特征，并仅使用这些显著特征建立另一个逻辑回归模型。

### 13. 假设将 `Not Joining` 预测为 `Joining`（`FPs`）的成本是将其 `Joining` 预测为 `Not Joining`（`FNs`）的成本的三倍。找到确定候选人是否会加入的最佳截止概率。

### 14. 根据问题 13 中找到的截止概率构建混淆矩阵，并报告模型对加入案例的精确率和召回率。

### 15. 人力资源部门希望了解影响候选人加入的关键参数。因此，建立一棵具有最优参数的决策树，并为人力资源部门提供一些规则，以便制定策略，确保未来被提供工作的候选人最有可能加入公司。

### 参考文献

**1.** A Janne (2009), *“波动率微笑的决定因素：德国个人股票期权研究”*, Graduate School of Finance and Financial Accounting, University of Vaasa, 网址：[`www.docsity.com/en/determinants-of-volatility-smile-study-guide-470-800/6716864`](https://www.docsity.com/en/determinants-of-volatility-smile-study-guide-470-800/6716864)/，访问于 2021 年 5 月 10 日。
**2.** Anon (2018), *“印度 KPMG 2018–19 年度薪酬趋势调查”*, 网址：[`assets.kpmg/content/dam/kpmg/in/pdf/2018/04/KPMG-India-Annual-Compensation-Trends-Survey.pdf`](https://assets.kpmg/content/dam/kpmg/in/pdf/2018/04/KPMG-India-Annual-Compensation-Trends-Survey.pdf)，访问于 2021 年 1 月 29 日。
**3.** Anon (2020), *“模型训练与调优”*, 网址：[`topepo.github.io/caret/model-training-and-tuning.html`](http://topepo.github.io/caret/model-training-and-tuning.html)，访问于 2021 年 1 月 29 日。
**4.** Anon (2020), *“零和接近零方差预测因子”*, 网址：[`topepo.github.io/caret/pre-processing.html#zero--and-near-zero-variance-predictors`](http://topepo.github.io/caret/pre-processing.html#zero--and-near-zero-variance-predictors)，访问于 2021 年 1 月 29 日。
**5.** Anon (2021), *“灵敏度、特异度和精确度”*, National Institute of Industrial Engineering, Mumbai, 网址：[`www.coursehero.com/file/p7md6938/2494-exp-1-e-Male-Single-1-PY-102-1-1102-3580-exp-1-e-Status-Marital-Other-1-PY`](https://www.coursehero.com/file/p7md6938/2494-exp-1-e-Male-Single-1-PY-102-1-1102-3580-exp-1-e-Status-Marital-Other-1-PY)/，访问于 2021 年 5 月 10 日。
**6.** Atkinson B (2021)，“rpart.control”，网址：[`www.rdocumentation.org/packages/rpart/versions/4.1-15/topics/rpart.control`](https://www.rdocumentation.org/packages/rpart/versions/4.1-15/topics/rpart.control)，访问于 2021 年 5 月 10 日。
**7.** Khun M (2007)，“Caret 包中的数据集和杂项函数”，可获取于 [`ftp.uni-bayreuth.de/math/statlib/R/CRAN/doc/vignettes/caret/caretMisc.pdf`](http://ftp.uni-bayreuth.de/math/statlib/R/CRAN/doc/vignettes/caret/caretMisc.pdf)，访问于 2021 年 7 月 24 日。
**8.** Kumar U D (2017), *“商业分析 – 数据驱动决策科学”*, Wiley, New Delhi.
**9.** Pradhan M 和 Kumar U D (2019), *“使用 Python 的机器学习”*, Wiley, New Delhi.
**10.** Rossouw J E, Du Plessis J P, Benade A J, Jordaan P C, Kotze J P, Jooste P L 和 Ferreira J J (1983)，“三个农村社区的心脏病风险因素筛查 – CORIS 基线研究”，*南非医学杂志*，64(12)，430–436。
**11.** Sing T, Sander O, Beerenwinkel N, Lengaur T, Unterthiner T 和 Ernst F M (2020), *“Package ROCR”*, 网址：[`cran.r-project.org/web/packages/ROCR/ROCR.pdf`](https://cran.r-project.org/web/packages/ROCR/ROCR.pdf)，访问于 2021 年 1 月 29 日。
**12.** Theneau T M 和 Atkinson E J (2019), *“使用 RPART 程序进行递归划分的介绍”*, 网址：[`cran.r-project.org/web/packages/rpart/vignettes/longintro.pdf`](https://cran.r-project.org/web/packages/rpart/vignettes/longintro.pdf)，访问于 2021 年 1 月 29 日。
**13.** Williams G (2010), *“数据挖掘”*，可获取于 [`datamining.togaware.com/survivor/Loss_Matrix.html`](http://datamining.togaware.com/survivor/Loss_Matrix.html)，访问于 2021 年 5 月 10 日。
**14.** Youden W J (1950)，“用于评定诊断试验的指数”，*Cancer*，3，32–32。
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
¹[`assets.kpmg/content/dam/kpmg/in/pdf/2018/04/KPMG-India-Annual-Compensation-Trends-Survey.pdf`](https://assets.kpmg/content/dam/kpmg/in/pdf/2018/04/KPMG-India-Annual-Compensation-Trends-Survey.pdf)
²[`topepo.github.io/caret/pre-processing.html#zero--and-near-zero-variance-predictors`](http://topepo.github.io/caret/pre-processing.html#zero--and-near-zero-variance-predictors)
³[`cran.r-project.org/web/packages/rpart/vignettes/longintro.pdf`](https://cran.r-project.org/web/packages/rpart/vignettes/longintro.pdf)

# 高级机器学习

## 7

*我们听到的每一件事都是一个观点。不是事实。我们看到的一切都是一个视角。不是真理。*

**—马可·奥勒留**

### 学习目标

阅读本章后，你将能够：
- 理解机器学习算法的基础。
- 了解监督学习和无监督学习算法之间的区别。
- 理解并开发梯度下降优化算法。
- 理解欠拟合和过拟合的问题，并使用正则化来控制过拟合。
- 理解超参数以及如何搜索最优超参数
- 将通过 `caret` 包（`glmnet`）提供的机器学习算法应用于回归和分类问题。
- 学习使用机器学习模型进行特征选择。

## 7.1 概述




# 机器学习

机器学习算法是人工智能（AI）的一个子集，它模仿人类学习过程。人类通过多次经验来执行任务。同样，机器学习算法利用额外数据进行学习并开发多个模型（通常使用多个数据集），每个模型都类似于一次经验。例如，考虑一个试图学习网球的人。掌握发球需要大量练习，尤其是学习发 Ace 球（对手无法触及的发球）。要掌握网球发球（尤其是 Ace 球），球员必须练习数千次；每次练习都是一次学习。在机器学习算法中，我们开发的模型可能多达数百个，每个模型都被视为一次学习机会（Pradhan and Kumar, 2017）。Mitchell（2006）对机器学习作了如下定义：

> 一个计算机程序或算法，如果在给定任务（`T`）和性能度量（`P`）方面，其在任务（`T`）上的性能以性能度量（`P`）衡量随经验（`E`）而改善，则称其从经验（`E`）中学习。

设任务 `T` 为分类问题。更具体地说，考虑客户购买产品的倾向。性能 `P` 可以通过多个指标来衡量，例如总体准确率、灵敏度、特异度以及接收器操作特征曲线下面积（`AUC`）。经验 `E` 是学习算法试图学习任务（`T`）的数据。统计学习与机器学习的主要区别在于，统计学习 heavily 依赖于模型假设的验证和假设检验，而机器学习的目标是预测准确性。例如，在开发回归模型时，我们会检查残差的正态性、回归参数的显著性等假设。然而，在使用分类树的随机森林中，最重要的目标是模型的准确性/性能。请注意，回归和逻辑回归等统计学习技术是机器学习的子集。机器学习（`ML`）任务可分为三大类：

**1.** **监督学习：** 在监督学习中，数据集具有输入变量（特征值）的值以及相应的结果变量值。算法从训练数据集中学习，并根据给定的输入变量值预测新记录的结果变量。回归和逻辑回归是监督学习算法的例子。在监督学习中，特征权重是通过最小化损失函数来估计的。

**2.** **无监督学习：** 在这种情况下，数据集只有输入变量值，而没有结果变量。算法学习输入中的结构。聚类和因子分析是无监督学习的例子，将在第 8 章中讨论。

**3.** **强化学习：** 在这种情况下，输入和/或输出变量是不确定的。智能手机中使用的预测词是强化学习的一个例子。

## 7.2 | 机器如何学习？

在监督学习中，算法通过最小化损失函数（也称为成本函数或误差函数）来学习，该函数是使用输入的预测输出和期望输出的函数。如果 `h(X[i])` 是预测输出，而 `y[i]` 是期望输出，则损失函数如下：

![](img/page230-01.png)

其中 `n` 是进行预测的记录总数。公式 (7.1) 中定义的函数是平方误差之和，是回归算法的损失函数。目标是学习使损失函数最小化的参数值（又称特征权重）。有许多现有算法可用于最小化损失函数。最广泛使用的优化技术称为梯度下降。在下一节中，我们将看一个回归问题的例子，并了解梯度下降如何帮助学习函数。除了公式 (7.1)中定义的损失函数外，还有其他形式的损失函数。例如，偏差被用作逻辑回归中的损失函数。

## 7.3 | 梯度下降

在本节中，我们将讨论如何使用梯度下降（`GD`）算法来估计回归参数的值（Pradhan and Kumar, 2017），给定包含输入（`X`）和输出（`Y`）的数据集。简单线性回归模型的函数形式为

![](img/page230-02.png)

**1.** `h(X)` 是 `Y` 的预测值
**2.** `β[0]` 称为偏差或截距
**3.** `β[1]` 是特征权重或回归系数
**4.** `ε` 是预测误差

误差由下式给出

![](img/page230-03.png)![](img/page231-01.png)

线性回归模型的成本函数是所有记录的均方误差（`MSE`），其表达式为

![](img/page231-02.png)

其中 `n` 是数据中记录或示例的总数。`Y[i]` 和 `X[i]` 表示数据中第 `i^(th)` 条记录。误差是 `β[0]` 和 `β[r]` 的函数。它是一个纯凸函数，具有全局最小值，如 **图 7.1** 所示。`GD` 算法从随机起始值（对于 `β[0]` 和 `β[1]`）开始，并朝向最优解移动，如 **图 7.1** 所示。

`GD` 通过以下步骤找到使损失函数最小化的 `β[0]` 和 `β[1]` 的最优值：

**1.** 随机猜测 `β[0]`（偏差）和 `β[1]`（特征权重）的初始值
**2.** 计算偏差和权重初始化值下结果变量的估计值
**3.** 计算误差函数（`MSE`）
**4.** 通过计算误差函数的梯度来调整 `β[0]` 和 `β[1]` 值

![](img/page231-03.png)![](img/page231-04.png)

其中，`α` 是学习率；`α` 的值是根据每次迭代需要应用于偏差和权重的更新幅度来选择的。直观地说，学习率描述了 `GD` 算法下降到最小值时步长的大小。学习率是一个超参数，在确定最佳学习率之前可能需要测试不同的值。将此值设得过小可能会使算法花费更长时间收敛。将学习率设得过高可能会导致算法超调收敛点并持续振荡，但永远无法达到最小值。我们可以在确定最佳值之前测试一组值，即 0.01、0.03、0.09、0.27 等。

`MSE` 关于 `β[0]` 和 `β[1]` 的偏导数由下式给出

![](img/page231-05.png)![](img/page231-06.png)

**5.** 重复步骤 1-4，直到误差不再进一步减小或成本变化无限小。最小成本点处的 `β[0]` 和 `β[1]` 是最终估计值，对应的函数是可以学习的最佳模型。

### 7.3.1 开发线性回归模型的 GD 算法

为了更好地理解 `GD` 算法，我们将在 第 5 章 中讨论的 IPL 数据集 **表 7.1** 上实现它。

调用 `ggplot` 包绘制 `MSE`，并使用 `utils` 包中的 `read. csv()` 加载数据集。

![](img/page232-01.png)

对 `ipl_df` 应用一些基本更改，这些更改在 第 5 章 中讨论过。

![](img/page232-02.png)

#### 创建特征集（`X`）和结果变量（`Y`）

我们可以编写一个通用函数来从数据集中提取预测变量和响应变量，如下所示：

![](img/page232-03.png)



我们可以在模型构建中识别出不希望作为独立特征的特征。有三个这样的特征是 `PLAYER_NAME`、`TEAM` 和 `AUCTION_YEAR`。我们还将 `BASE PRICE` 保留在特征列表之外。下面的代码块从预测变量列表中删除这些特征。
![](img/page233-01.png)![](img/page233-02.png)
### 编码分类特征
在本节中，我们将讨论在不使用 `caret` 包的情况下对分类特征进行编码。请注意，数值特征也在标准化，以便 `GD` 更快收敛。
![](img/page233-03.png)![](img/page234-01.png)
### 设置 `x` 和 `y` 变量
`processed_df` 包含标准化且已进行哑变量编码的特征，这些特征将用于回归建模。将特征分离为 `X`（预测变量）和 `Y`（结果）特征。预测变量显示在 **表 7.2** 中。
![](img/page234-02.png)
`X` 中的前五条记录和前 10 个特征如下 **表 7.2**：
![](img/page234-03.png)
`SOLD PRICE`（`Y`）的前六条记录显示在 **表 7.3** 中：
![](img/page234-04.png)![](img/page234-05.png)
**表 7.3** | `Y` **特征**
| `SOLD_PRICE` |
| --- |
| −1.1583445 |
| --- |
| −1.1583445 |
| −0.4208947 |
| 0.8081883 |
| 0.6852800 |
| −1.1583445 |
### 实现 GD 算法
为了实现 第 7.3 节 中解释的步骤，需要实现以下一组用户自定义函数。
**步骤 1：** 用于随机初始化 beta 系数的函数。
![](img/page235-01.png)
`x` 表示数据集中的特征。在上述函数中，我们将为数据集中所有特征初始化 `betas` 为零。
**步骤 2：** 计算 `Y` 的预测值的函数，即给定偏差和权重下的 `Y`
![](img/page235-02.png)
`%*%` 表示矩阵乘法。因此，上述代码实现了方程 `h(x^(i)) = β[0] + β[1] * X¹ + … + β[m] * X^(m)`，用于数据集中所有 `m` 个特征（`X^m` 是第 `m^(th)` 个特征）。
**步骤 3：** 根据 `Y` 的预测值和实际值计算成本函数的函数。让我们将方程 ** 放入实现中并定义均方误差函数，即通过以下方式计算均方误差（`MSE`）：
**1.** 计算计算得到的 `Y` 与实际 `Y` 之间的差异
**2.** 计算上述残差的平方并求和
**3.** 用观测数量除
![](img/page235-03.png)
**步骤 4：** 计算梯度并调整偏差和权重的函数
这是最重要的方法，其中偏差和权重根据成本函数的梯度进行调整。方程 (7.5) 和 (7.6) 在 `update_beta()` 中实现为 `beta = beta – alpha * delta`。
![](img/page235-04.png)
**步骤 5：** 对 `betas` 的更新需要迭代进行，直到成本最小化。这可能需要多次迭代且耗时。有两种停止迭代的方法。
**1.** 运行固定次数的迭代，并在这些迭代结束时将 `betas` 用作最优值。
**2.** 运行迭代直到 `MSE` 或成本的 `δ` 变化很小，即小于预定义值，例如 0.001。
![](img/page235-05.png)
我们将说明第一种方法来找到最优的 `beta` 系数。让我们将学习率，即 `alpha` 初始化为 0.01。迭代 “`iter`” 是为下降定义的循环次数。
![](img/page236-01.png)
稍后，我们将使用 `caret` 包的 `glmnet()` 函数来找到使 `MSE` 或成本函数最小化的最佳 `beta` 系数。
#### 绘制成本值
我们可以将成本绘制为收敛迭代次数的函数。
![](img/page236-02.png)
在 **图 7.2** 中，我们可以看到当迭代次数超过 1,000 时，`MSE` 或成本似乎没有变化。通过分析 `cost_history`，我们可以看到收敛，即 `MSE` 的 `δ` 变化在 1,488 次迭代中已达到。可以改用 do while 或 while 循环使用上述代码，而不是限制迭代次数。最终权重存储在 `beta` 系数中。
![](img/page236-03.png)![](img/page237-01.png)
**梯度下降** 是一种流行的优化算法，是许多高级机器学习算法的核心，包括神经网络。梯度下降用于在 AI 和 ML 算法中查找特征权重。
权重是标准化值，因为我们使用了 `Y` 和 `X` 的标准化值。因此，`ODI_RUNS_S` 的 `beta` 系数的解释将以标准差为单位变化，即 `ODI_RUNS_S` 变化一个标准差时，`SOLD_PRICE` 变化 0.43 个标准差。
使用 `GD` 算法实现的上述机器学习算法对于理解特征权重的估计很重要。在上述实现中，我们没有考虑正则化。直观上，我们可以将正则化视为在模型过拟合（方差）和模型欠拟合（偏差）之间进行权衡的技术。正则化项被添加到 `MSE` 或成本函数中，以惩罚 `beta` 系数，从而解决过拟合问题。
![](img/page237-02.png)
## 7.4 | 偏差-方差权衡
模型误差可以分解为两个组成部分，称为偏差和方差。理解这两个组成部分是诊断模型准确性并避免模型过拟合或欠拟合的关键。高偏差可能导致构建欠拟合模型，而高方差可能导致过拟合模型，从而导致泛化误差。**表 7.4** 显示了患者数据集中两个特定特征，即体重（`X`）和患者的身高（`Y`）。
**表 7.4** | 病人数据
| `BODY_WEIGHT` || `BODY_HEIGHT` |
| --- | --- |
| 49 || 160 |
| --- | --- |
| 41 || 155 |
| 47 || 164 |
| 80 || 173 |
| 58 || 175 |
| 45 || 140 |
![](img/page238-01.png)
假设我们想要构建一个回归模型，根据体重预测一个人的身高。由于只有两个变量，我们可以通过散点图绘制它们来观察关系。
![](img/page238-02.png)
可以从 **图 7.3** 观察到 `Y` 与 `X` 之间的关系不是线性的，看起来是多项式的。但我们不确定多项式形式的次数。我们需要尝试 `X` 的各种多项式形式并验证哪个模型最适合数据。来自 stats 包的 `poly()` 函数可用于创建具有不同次数的特征，即 2、3、4 等。如果我们使用 `poly()` 函数创建一个二阶特征，数据将如下所示 **表 7.5**：
**表 7.5** | 多项式特征
| 1 || 2 |
| --- | --- |
| 49 || 2,401 |
| --- | --- |
| 41 || 1,681 |
| 47 || 2,209 |
| 80 || 6,400 |
| 58 || 3,364 |
| 45 || 2,025 |
![](img/page239-01.png)![](img/page239-02.png)
**表 7.5** 的第一列是实际体重，第二列表示体重的平方。使用 **表 7.5** 中的值作为预测变量，回归模型的函数形式将为 ![](img/pageIn_ch7-01.png)。然而，在进行模型构建之前，让我们将 `raw_df` 分成训练数据和测试数据。我们还将编写一个用户自定义函数 `fit_ploy()` 来构建任意次数 `n` 的多项式回归模型。
![](img/page239-03.png)



`fitted.values` 函数从模型中提取 `Y` 的预测值。 使用上面定义的 `fit_poly()` 函数，让我们创建一个线性拟合回归模型，并创建二到十次多项式拟合的模型，并将拟合值作为 `train_df` 的一部分添加。 **表 7.6** 显示了 `train_df` 上的 `fitted.values`。

![](img/page239-04.png)![](img/page240-01.png)![](img/page240-02.png)

**表 7.7** 显示了上述模型在 `test_df` 上的预测值。 稍后，我们将使用 **表 7.7** 的结果。

![](img/page240-03.png)

让我们绘制使用 `train_df` 构建的各种模型。 模型结果存储在 **表 7.6** 中，我们将使用 `ggplot()` 来可视化数据。

![](img/page240-04.png)

线性模型 (`h(x[i]) = β[0] + β[1] * X[1]`) 显示在 **图 7.4** 中。 从 **图 7.4** 可以明显看出，回归模型似乎不能很好地拟合数据。 它无法从数据中学习，因为假设了模型的形式过于简单，从而产生偏差。 这是欠拟合或偏差的情况（Pradhan and Kumar, 2017）。 该模型偏差很大。 让我们拟合一个带有多项式项的回归模型，即 `X` 的平方。

![](img/page240-05.png)![](img/page241-01.png)

**图 7.5** 显示了具有函数形式 ![](img/pageIn_ch7-02.png) 的拟合模型。 回归线似乎比之前的模型更能拟合数据。 但我们不确定这是否是最佳模型。 让我们绘制我们已构建的更高次模型。

![](img/page241-02.png)![](img/page241-03.png)![](img/page241-04.png)![](img/page242-01.png)

可以从 **图 7.6** 和 **7.7** 观察到，随着我们构建包含越来越多多项式项的模型，模型开始拟合训练集中的每个数据点（Pradhan and Kumar, 2019）。 这是过拟合的情况。 最高次数为 10 的多项式项模型将对训练示例的任何变化都很敏感。 从数据集中添加或删除甚至单个观测值都可能显著改变模型参数。

欠拟合模型由于偏差高而产生较大误差，而过拟合模型由于方差高而产生较大误差。 最优模型将在欠拟合和过拟合模型之间，具有低偏差和低方差。 这可以通过比较训练集和测试集中的模型准确性来观察。 对于 10 个不同的多项式模型，让我们计算 `train_df` 和 `test_df` 上的 `RMSE`。 请注意，指标 `RMSE` 和 `MSE` 对异常值敏感（`Mean Absolute Error`、`MAE` 可能对数据中的异常值更稳健）。 然而，在本例中，我们将继续使用 `RMSE` 来报告误差。 让我们将度和误差详细信息存储在名为 `error_df` 的数据框的不同列中。 **表 7.8** 显示了 `error_df` 的详细信息。

![](img/page242-02.png)![](img/page242-03.png)

**1.** `degree`: 模型的次数（多项式项数）

**2.** `train_error`: 训练集上的 RMSE 误差

**3.** `test_error`: 测试集上的 RMSE 误差

![](img/page243-01.png)![](img/page243-02.png)![](img/page243-03.png)

**图 7.8** 是我们在进行 60:40 数据划分时得到的。 此随机划分导致 `train_df` 有 100 条记录，`test_df` 有 63 条记录。 从 **图 7.8** 中，我们可以看到

**1.** 次数为 1 的多项式回归模型（**表 7.6** 中的 `fit_1_degree`）对 `train_df` 和 `test_df` 都显示出较高的误差（误差之间的巨大差距可能存在也可能不存在）。

**2.** 次数为 10 的多项式回归模型（**表 7.6** 中的 `fit_10_degree`）在 `train_df` 上显示出较低误差，但在 `test_df` 上显示出较高误差（误差之间存在巨大差距）。

![](img/page244-01.png)

**3.** 随着多项式次数的增加，模型在测试集上的误差最初会减少，但在特定次数后会出现增加。

**4.** 随着多项式次数的增加，模型在训练集上的误差持续下降。

我们必须决定选择哪个模型作为最佳模型。 直观上，当我们尝试选择导致最佳模型的多项式次数时，我们正在进行超参数微调。 或者说，每增加一个多项式项都类似于添加一个特征，因此导致最佳模型的多项式次数可以被视为超参数微调。

我们还可以将多项式的次数与模型的复杂度联系起来。 从 **图 7.8** 可以观察到，随着复杂度（模型中的多项式项数）的增加，模型开始很好地拟合训练和测试数据。 但超过特定复杂程度（Pradhan and Kumar, 2017），即复杂度等级 3，训练误差继续减少，但测试误差又开始增加。 这是模型开始过拟合训练集并停止泛化的点。 因此，最优模型复杂度为 3，具有低偏差和低方差。 因此，为了概括，我们选择满足以下三个标准的模型次数：

**1.** 在训练集上报告最低误差。

**2.** 在测试集上报告最低误差。

**3.** 训练误差与测试误差之间的差异最小。

然而，我们能否仅根据一次随机的训练集和测试集划分就得出结论，次数为 3 的多项式模型具有良好的泛化能力（测试数据上的误差更小）？ 我们必须对多个训练和测试数据重复此过程。

## 7.5 | 改进 ML 模型的策略 – 偏差方差权衡

我们经常遇到讨论拥有更多数据来构建更好的模型或更多特征来提高模型性能的情况。 添加更多特征等同于增加模型的复杂度（添加高次多项式项）。 然而，需要考虑的是，除非我们已经构建了第一个模型并评估了其性能，否则关于更多数据或更多特征的讨论可能没有意义。 如果模型存在高偏差（欠拟合）问题：

**1.** 添加更多训练数据可能没有帮助。

**2.** 添加更多特征或使用复杂模型可能有帮助。

实际上，从复杂模型开始然后降低模型复杂度以得到更具泛化能力的模型是有用的。 但如果我们从复杂模型开始，我们可能会遇到高方差问题。 如果模型存在高方差（过拟合）问题，则：

**1.** 添加更多训练数据可能有帮助，因为过拟合可能源于训练数据有限。

**2.** 减少特征数量或正则化也有助于降低高方差。

### 7.5.1 降低方差 – 增加更多观测值

从 **图 7.8** 我们可以得出结论，次数为 10 的模型会导致高方差问题。 让我们尝试通过在训练集上添加更多数据来解决高方差问题。 **图 7.9** 显示了通过将训练集和测试集划分更改为 70:30 时不同多项式模型的性能。

**图 7.8** 表明次数为 3 的模型是最好的。 然而，**图 7.9** 表明次数为 5 的模型有助于在测试集上进一步降低误差。 将数据按 80:20 划分导致了不同的性能，如 **图 7.10** 所示。




从 **图 7.10** 中，我们可以看到具有任意多项式次数项的模型报告的 `test_error` 都小于 `train_error`。然而，随着我们对数据进行随机划分以增加训练集，测试数据中的观测值会减少。尽管是随机划分，这个小的观测集合也可能意味着测试数据中没有异常值（极值）。`RMSE` 作为对异常值敏感的指标，可能导致训练数据上的误差较高，而模型在测试集上报告的误差较低，这并不一定意味着模型的泛化能力更好。从 **图 7.10** 中，我们仍会选择次数为 5 的模型作为最佳模型。然而，得到的启示是

**1.** 单次训练集和测试集划分可能不足以得出我们已选择一个在偏差和方差之间进行权衡的模型。

**2.** 通过减少测试集中的观测数量来增加训练集中的观测数量可能会导致选择复杂度更高的模型（比较 **图 7.8** 与 **图 7.9** 和 7.10。）

这就是我们可能需要使用交叉验证或重复交叉验证作为选择最佳模型策略的地方。

![](img/page245-01.png)
![](img/page246-01.png)
![](img/page246-02.png)

### `K` 折交叉验证

`K` 折交叉验证是一种稳健的验证方法，可用于验证模型是否过拟合（Pradhan and Kumar, 2019）。如果模型泛化良好且不过拟合，则不应对底层训练样本的任何变化非常敏感。`K` 折交叉验证可以通过从样本集中重采样多个训练集和验证集来构建和验证多个模型来实现这一点。`K` 折交叉验证中使用以下步骤：

**1.** 将训练数据集拆分为 `K` 个相等子集。每个子集称为一个折。将折命名为 `set_1`、`set_2`、… `set_K`。通常，`K` 的取值取为 3、5、7 或 10。

**2.** 对于 `i` = 1 到 `i` = `K`
(a) 将折 `set_i` 作为验证集，其余所有 `K-1` 个折作为训练集。
(b) 使用训练集训练机器学习模型，并用为验证保留的 `set_i` 计算模型的准确率。

**图 7.11** 描述了 `K` 折交叉验证的过程（在 **图 7.11** 中 `K` 取为 5）。

对 CV 的详细解释已在 第 6 章 中给出。通过对所有 `K` 个模型的准确率取平均值来计算最终准确率。平均准确率值显示模型在现实世界中的表现。这些准确率的方差是模型稳健性的指标。

### 7.5.2 | 降低方差 – 应用正则化

处理过拟合（降低方差）的另一种方法是应用正则化。在回归情况下，观察到过拟合通常是由参数的系数（权重）估计膨胀引起的。为了避免过拟合，估计的系数（权重）应通过惩罚来调节。正则化会在参数变得过大时对其施加惩罚，防止其权重过重。系数（权重）通过将系数项添加到成本函数中来受到惩罚。如果系数变得很大，成本会显著增加。因此，优化器控制系数值的大小以最小化成本函数。以下两种方法可用于向成本函数添加惩罚。

在构建机器学习模型时，**偏差-方差权衡** 是使模型泛化并使其在未见/未来数据点上预测时有用的重要考虑因素。

**1.** **L1 范数：** 添加系数的绝对值之和。这也称为最小绝对收缩和选择算子（LASSO 项）。相应的成本函数由下式给出

![](img/page247-01.png)

在 式 7.9 中，`n` 是记录数，`m` 是数据中的特征数。`a` 是一个乘数，其最优值需要通过超参数微调找到。

在 **L1 范数** 中，由于惩罚是系数项之和 ![](img/pageIn_ch7-03.png)，所定义的形状或区域为正方形。在 L2 范数中，由于惩罚是系数平方之和 ![](img/pageIn_ch7-04.png)，其所定义的形状/区域为圆形。

**2.** **L2 范数：** 添加系数的平方值。这称为岭项。成本函数由下式给出

![](img/page247-02.png)

`γ` 是一个乘数，其最优值需要通过超参数微调找到。注意，在 L1 和 L2 范数中，我们不对截距进行惩罚，即 `β[0]`。

Ridge 将系数值在所有特征间分布（平滑），而 LASSO 会将某些系数减小为零。系数值为零的特征可视为对模型无贡献的特征。因此，LASSO 也可用于特征选择，即移除系数为零的特征，从而减少特征数量。**图 7.12** 显示了正则化中 L1 和 L2 惩罚的作用。

**3.** **ElasticNet 回归：** ElasticNet 回归结合 L1 和 L2 正则化来构建回归模型。相应的成本函数由下式给出

`MSE` 具有凸形，在二维图中可绘制为椭圆形（等高线图）。在 L1 范数下寻找最小 `MSE` 直观上等同于寻找与正方形区域相切的椭圆形。鉴于底层数学，切线有时会落在正方形的顶点上，因此对于某些系数，估计值可能恰好为零。

![](img/page247-03.png)

在构建 ElasticNet 回归模型时，需要设置两个超参数 `σ`（L1）和 `γ`（L2）。

### 正则化的直观理解

考虑在 第 7.4 节 中讨论的患者数据集（身高和体重）。观察图表和偏差方差权衡，我们得出结论，多项式次数为 3 的模型似乎最适合数据。但假设我们构建了复杂模型并拟合了次数为 6 的多项式模型。那么我们用于建模的函数形式如下：

![](img/page247-04.png)

寻找 **L2 范数下的最小 MSE** 也直观上等同于寻找与圆形区域相切的椭圆形。鉴于底层数学，切线不太可能落在圆的轴上，尽管有时可能发生，因此系数估计可能接近于零但不完全为零。

![](img/page248-01.png)

其中 `h(X)` 是估计的身高，`x` 表示患者的体重。由于我们知道数据最佳拟合的模型将是次数为 3 的模型，让我们修改成本函数，使 `β[4]`、`β[5]` 和 `β[6]` 具有非常高的权重。因此，修改后的成本函数如下：

![](img/page248-02.png)

在 式 (7.13) 中，`β[4]`、`β[5]` 和 `β[6]` 已乘以 1,500 的值。由于目标是找到使 `MSE` 最小的 `βs`，我们可以直观地认为当 `β[4]` ≈ 0、`β[5]` ≈ 0 且 `β[6]` ≈ 0 时成本最小。当这种情况发生时，函数形式将简化为次数为 3 的多项式拟合。



然而，在实际示例中，我们并不知道可以赋予更高权重以降低特征对整体结果影响的特征。为了克服这种情况，我们对所有特征进行惩罚。这是通过添加 `L1` 或 `L2` 范数实现的，其本质上试图最小化所有特征对最终结果 (`h(x)`) 的影响。

交叉验证技术结合正则化，有助于构建稳健的机器学习模型。`caret` 提供了 `glmnet` 方法，可用于应用正则化。我们将使用来自 `caret` 包的 `glmnet` 方法以及通过 `trainControl()` 的 cv 方法来构建机器学习模型。我们还将看到来自 `glmnet` 包的 `cv.glmnet()` 方法的直接实现，以构建正则化回归模型。

## 7.6 | 机器学习 – 使用 glmnet 包进行回归

我们在 第 5 章（线性回归）和 第 6 章（分类）中使用了 `caret` 包来构建统计模型。在这里，我们将使用 `glmnet` 包来拟合线性、逻辑、多项式以及许多其他模型。使用 `glmnet` 包构建机器学习模型的步骤将保持不变。

**1.** 识别输入和输出变量。
**2.** 将数据集拆分为训练集和测试集。
**3.** 使用训练集构建模型。
**4.** 使用测试集预测结果变量。
**5.** 比较测试集中结果变量的预测值和实际值，并使用均值绝对百分比误差（MAPE）或均方根误差（RMSE）等指标衡量准确性。

需要注意的一点是，`glmnet` 方法期望显式的虚拟变量编码。因此，在调用 `glmnet()` 方法之前，我们将使用来自 `caret` 包的 `dummyVars()` 进行虚拟变量编码。

`glmnet` 中实际求解的回归成本函数为

![](img/page248-03.png)

其中 `n` 是观测值的数量，`m` 是特征的数量。对于高斯情况，即连续 `Y`，公式 (7.14) 中的 `l(y, η)` 被 ![](img/pageIn_ch7-05.png) 替换。因此，高斯情况下的 公式 (7.14) 将如下所示：

![](img/page248-04.png)

弹性网络惩罚由 `α` 控制。如果有两个以上的预测变量相互相关，则 `α = 0.5` 将选择所有预测变量（即使预测变量中有一个与结果变量有很强的相关性），或者不选择任何预测变量。控制上述成本函数的一些有用要点如下：

**1.** 设置（`α = 0`）给出岭回归。岭惩罚使相关预测变量的系数相互收缩。
**2.** 设置（`α = 1`，默认值）给出 LASSO 回归。如果存在两个相关系数，LASSO 惩罚倾向于选择其中一个并丢弃另一个。
**3.** 调优参数 `λ` 控制惩罚的整体强度。设置 `λ = 0` 无论 `α` 的值如何都会产生 OLS 模型。
**4.** `α` 是一个更高级别的参数，其值可以提前选择，也可以作为超参数微调提供。

让我们应用上述步骤，使用 `new_ipl_df` 构建正则化回归模型来预测球员的 `SOLD_PRICE`。使用 `new_ipl_df`，让我们生成 `ipl_with_dummy_df`，这是一个虚拟变量编码的 `data.frame`。**表 7.9** 显示了虚拟变量编码的 data.frame 的快照。

![](img/page249-01.png)![](img/page249-02.png)

### 7.6.1 创建特征集 (X) 和结果变量 (V)

让我们从 `ipl_with_dummy_df` 中获取预测变量和结果特征。

![](img/page249-03.png)![](img/page250-01.png)

`AGE`, `COUNTRY`, `PLAYING_ROLE`, `T_RUNS`, `T_WKTS`, `ODI_RUNS_S`, `ODI_SR_B`, `ODI_WKTS`, `ODI_SR_BII`, `CAPTAINCY_EXP`, `RUNS_S`, `HS`, `AVE_B`, `SR_B`, `SIXERS`, `RUNS_C`, `WKTS`, `AVE_BII`, `ECON`, `SR_BL`

### 7.6.2 创建训练集和测试集

来自 `caret` 包的 `createDataPartition()` 函数提供了将数据集随机拆分为训练集和验证数据集的能力。

![](img/page250-02.png)

由于 `glmnet` 期望 `X` 特征以矩阵形式存在，让我们将训练 df 类型转换为矩阵并创建 `X`（特征）和 `Y`（结果）变量。

![](img/page250-03.png)

### 7.6.3 使用 glmnet 进行 LASSO 回归

来自 `glmnet` 包的函数 `glmnet()` 可用于创建 LASSO、岭或 ElasticNet 模型。然而，该函数返回一系列模型。我们感兴趣的是获得最佳模型而不是一系列模型。交叉验证技术是此任务最简单且最广泛使用的方法。因此，`glmnet` 还提供了 `cv.glmnet` 来应用交叉验证策略直接选择最佳模型。

让我们直接使用来自 `glmnet` 包的 `cv.glmnet()` 构建模型。我们还将使用 `doMC` 包调用并行处理。我们将使用 `registerDoMC()` 函数启用两个核心。

![](img/page250-04.png)

让我们通过注册两个核心来调用并行处理构建 `init_model`。我们将使用 5 折交叉验证集返回最佳模型。我们将使用均方误差作为报告最佳模型的指标。`nlambda = 100` 是默认参数。

![](img/page251-01.png)

`cv.glment()` 和 `glmnet()` 的 family 参数默认设置为高斯，即处理连续结果 (`Y`)。`init_model` 对象包含解释和使用结果所需的所有信息。然而，有几点需要注意，如下所示：

**1.** `type.measure = "mse"` 意味着使用均方误差来报告最佳模型。
**2.** `cv.glmnet` 的结果是随机的，因为折叠是随机选择的。这种随机性可以通过多次运行 `cv.glmnet` 并平均误差曲线（使误差最小的 `lambda` 值的平均值）来降低。我们可以使用 `set.seed()` 使代码具有可重复性。
**3.** `cv.glmnet` 仅微调 `lambda` 值。它不会搜索 `alpha` 的值。应指定 `alpha` 的指定值，否则假设 `alpha = 1`（默认值，lasso 回归）。为了同时微调 `alpha` 和 `lambda`，请使用 `cva.glmnet()`。

#### Lambda 序列的直觉

在 `cv.glmnet()` 函数中，我们将要评估的 `lambda` 值数量指定为 100。程序内部生成 100 个不同的 `lambda` 值并提供最佳拟合模型。`glmnet` 关于 `lambda` 参数的 文档¹ 如下：

> “可以提供 Lambda 值，但通常不会提供，程序会构造一个序列。当自动生成时，`λ` 序列由 `lambda.max` 和 `lambda.min.ratio` 决定。后者，即 `lambda.min.ratio` 是生成的 `λ` 序列中最小值（假设为 `lambda.min`）与 `lambda.max` 的比率。然后程序在对数尺度上从 `lambda.max` 线性生成 `nlambda` 个值下降到 `lambda.min`”。

`lambda.max` 未给出，但可以从输入 `X` 和 `Y`（Anon, 2018）轻松计算；它是使所有系数都为零的 `lambda` 的最小值。²

![](img/page251-02.png)

在 公式 (7.16) 中，`m` 是数据中的观测值数量。让我们根据上述公式创建 `lambda.max` 值。我们将使用 `my_scale()` 函数标准化 `X` 变量。我们还定义了 `get_lambda_max()` 来获取 `lambda.max`。

![](img/page251-03.png)![](img/page252-01.png)

一旦确定了 `lambda.max`，策略就是选择 `lambda.min`（Friedman, Hastie, & Tibshirani, 2010）并在对数尺度上构造 `K = 100` 个 `lambda` 值，从 `lambda_max` 递减到 `lambda_min`。选择 `lambda.min` 的公式如下：

![](img/page252-02.png)



典型值是 `epsilon = 0.0001` 和 `K = 100`。为了生成 `lambda` 序列，让我们定义 `get_lambda_seq()`。

![](img/page252-03.png)

我们将调用上述函数来获取 `lambda` 值的序列：

![](img/page252-04.png)

`cv.glmnet` 生成的值序列如下：

![](img/page252-05.png)![](img/page253-01.png)

注意：

**1.** 手动序列与 `glmnet` 生成的序列完全相同。在后面的章节中，我们将使用手动序列通过 `caret` 包来训练模型。

**2.** 而不是 100 个 `lambda` 序列，`init_model` 只报告了 81 个 `lambda`。这是因为在路径上的其他 `lambda` 序列可能没有显示出 `MSE` 的改善。

**3.** 对于 `alpha = 0`（`ridge`）`lambda.max` 将为 ∞；因此，对于这种情况，`lambda` 值取自接近零的 `alpha` 值（`alpha = 0.001`）。

另一个有用的参数名为 `penalty.factor`，允许用户对每个系数应用单独的惩罚因子。其默认值对每个参数为 1，但也可以指定其他值。如果我们不希望某个特定特征受到惩罚，则可以将该特征的 `penalty.factor` 改为零。

`glmnet` 和 `cv.glmnet` 内部可以传递多个其他参数，但它们大多设置为默认值。有关可以传递给 `glmnet` 的参数的更多信息，可以通过在控制台上输入 `?glmnet::glmnet` 获得。

### 7.6.4 结果的解释

在 第 7.6.3 节 中，我们使用 `glmnet` 包开发了 `LASSO` 回归。让我们了解使用 `cv.glmnet` 创建的对象 `init_model` 中存储的结果。我们将使用下面的代码行打印 `init_model`。

![](img/page253-02.png)![](img/page254-01.png)

`init_model` 的输出显示以下内容：

**1.** 非零系数的数量（`Df`）。

**2.** 解释的偏差百分比（`%Dev`），即仅包含截距项的模型对结果变量的预测效果如何。

**3.** `lambda` 的值。每一行项目对应于其中提到的 `lambda` 值的模型。

默认情况下，`glmnet` 调用 100 个 `lambda` 值。然而，如果“`%Dev`”从一个 `lambda` 到下一个 `lambda` 的变化不足（通常在路径的末尾附近），程序会提前停止。

`plot` 函数可用于绘制上述信息。让我们绘制 `init_model`。

![](img/page255-01.png)

`init_model` 在 **图 7.13** 中的图包括以下内容：

**1.** 每个 `lambda` 的平均交叉验证误差（红色虚线，即 `init_model$cvm`）。

**2.** 沿 `lambda` 序列的上、下标准差曲线（误差条）。

**3.** 两个选定的 `lambda` 由垂直虚线指示。

第一根垂直线对应于使 `MSE` 测量的交叉验证误差最小的 `lambda` 值（本例中约为 10.25）。该值可以通过以下方式获得

![](img/page255-02.png)

请注意，**图 7.13** 中的图以对数刻度显示 `lambda`。在此 `lambda` 值下保留的特征数量为 11（次要 `X` 轴）。第二根垂直线对应于使误差在最小值的一个标准误差范围内、即 `MSE` 在最小 `MSE` 的一个标准误差范围内的最大 `λ` 的 `lambda` 值（本例中约为 11.1）。该值可以通过以下方式获得

![](img/page255-03.png)![](img/page256-01.png)

对应于使 `MSE` 最小的 `lambda` 的估计系数可以按如下方式获得

![](img/page256-02.png)

如图所示，`LASSO` 回归使某些特征的系数恰好等于零。使用 `init_model` 进行预测可以通过使用 `predict` 函数并传递 `train_df` 或 `test_df` 以及参数 ‘`s`’ 来完成，该参数取进行预测的 `lambda` 值。

![](img/page257-01.png)

需要注意的是，在 第 5 章 中，使用相同的特征集用 `ipl_df` 构建模型时，我们在测试集上最终获得了 0.18 的 `R-squared`（第 5 章，第 5.11 节）。我们可以使用 `cv.glment` 函数构建岭回归以及 `ElasticNet`。然而，对 `ElasticNet` 方法进行微调以测试不同的 `alpha` 值需要使用名为 `foldid` 的额外参数。不要使用 `cv.glment` 构建模型，让我们继续使用我们多次使用的 `caret`。

## 7.7 | 机器学习 – 使用 Caret 进行回归

直接使用 `glmnet` 包构建回归模型并通过 `caret` 调用 `glmnet` 会导致最佳模型返回的最终 `lambda` 值出现一些差异。这可能是由于 `caret` `glmnet` 方法与 `glmnet` 包之间的内部交互所致。然而，如果通过 `caret` 包正确地进行模型调优，结果可能不会有太大差异。在业务关键项目中，建议使用 `glmnet` 包而不是 `caret` 包来微调和构建回归模型。如果业务要求使用 `caret` 包，则建议使用 第 7.6.3 节 中所示的步骤生成 `lambda` 序列，并使用 `caret` 包（`glmnet` 方法）对这些 `lambda` 值进行网格搜索。

### 7.7.1 使用 Caret 进行 LASSO 回归

我们将使用 第 7.6.2 节 中创建的 `train_df` 和 `test_df`。让我们首先获取可通过 `caret` 包对 `glmnet` 进行微调的参数列表。

![](img/page257-02.png)

`alpha` 和 `lambda` 是可用于微调的参数，这与我们在 第 7.6.3 节 中看到的完全相同。让我们使用 `expand.grid()` 传递不同的 `alpha` 和 `lambda` 值来构建 `LASSO`、`ridge` 和 `ElasticNet` 回归模型。

让我们使用调用 `glmnet` 的 `caret` 包来构建模型。`LASSO` 的 `alpha` 值固定为 1。我们将改变想要微调的 `lambda` 值的范围。我们可以定义任何想要评估的 `lambda` 值序列。然而，在 第 7.6.3 节 中，我们手动生成了 `glmnet` 函数内部评估的序列。让我们使用相同的序列来微调 `lambda`。

![](img/page258-01.png)

请参阅 第 7.6.3 节 了解有关 `get_lambda_seq()` 的更多信息。`control_params` 使用 `repeatedcv()` 方法设置。`repeatedcv()` 还期望传递参数 `repeats`，它定义了我们想要重复交叉验证集的次数。

![](img/page258-02.png)![](img/page259-01.png)![](img/page260-01.png)

使用网格搜索的 `repeatedcv()` 报告的最终超参数或微调参数如下：

![](img/page260-02.png)

在最佳 `lambda` 值下的系数如下：

![](img/page260-03.png)![](img/page261-01.png)

对 `train_df` 和 `test_df` 的预测如下：

![](img/page261-02.png)

我们也可以使用简写形式进行预测，即 `predict(lasso_model, test_df)`。我们可以看到，使用 第 7.6.3 节 中的 `glmnet` 包得到的 `test_df` 上的结果与此处 `caret` 包的结果相同。

### 7.7.2 使用 Caret 进行岭回归

`ridge` 的 `alpha` 值固定为 0。对于 `alpha = 0`（`ridge`）`lambda.max` 将为 ∞；因此对于这种情况，`lambda` 值取自接近零的 `alpha` 值（例如 0.001）。请参阅 第 7.6.3 节 以进一步了解。



![](img/page261-03.png)![](img/page262-01.png)![](img/page263-01.png)![](img/page264-01.png)

使用 `repeatedcv` 进行网格搜索报告的最终超参数或微调参数如下：

![](img/page264-02.png)

获取对应最佳 `alpha` 和 `lambda` 的系数，我们将使用 `coef` 函数。

![](img/page264-03.png)![](img/page265-01.png)

对 `train_df` 和 `test_df` 的预测如下：

![](img/page265-02.png)

### 7.7.3 使用 Caret 的 ElasticNet 回归

让我们使用 `glmnet` 构建 ElasticNet 模型。我们将使用两种不同的方法构建 ElasticNet 模型：

**1.** 一种使用 `tuneGrid` 参数的方法，该参数在第 7.6.1 节和第 7.6.2 节中使用，期望一个 `expand.grid` 对象。我们将重用来自 第 7.6.3 节 的 `lambda_seq`。

**2.** 第二种使用 `tuneLength` 参数的方法，该参数随机搜索参数。

#### 使用 tuneGrid 的 ElasticNet 回归

让我们使用 第 7.6.3 节 中定义的 `get_lambda_seq` 函数获取 lambda 序列，并将其传递给 `expand.grid()`。

![](img/page265-03.png)

使用 `repeatedcv` 进行网格搜索报告的最终超参数或微调参数如下：

![](img/page266-01.png)

ElasticNet 模型的模型系数如下：

![](img/page266-02.png)

对 `train_df` 和 `test_df` 的预测如下：

![](img/page266-03.png)![](img/page267-01.png)

#### 使用 tuneLength 的 ElasticNet 回归

另一种微调超参数的方法是使用 `train` 函数的 `tuneLength` 参数。使用此参数不需要使用 `expand.grid`。如果我们指定 `tuneLength = 10`，

**1.** `caret` 选择 `alpha` = c(0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9 1)

**2.** `caret` 使用来自 `glmnet` 包的 `glmnet()` 函数在 `alpha` 为 0.5 时选取 `lambda` 值。换句话说，第 7.6.3 节 中的用户自定义函数 `get_lambda_seq(x, y, alpha = 0.5)` 可用于选取 `lambda` 值。

当每个 `alpha` 的 `tuneLength = 10` 时，将评估 10 个 `lambda` 值。因此，总共将构建 100 个模型。

![](img/page267-02.png)![](img/page268-01.png)![](img/page269-01.png)

读者可以使用 第 7.6.3 节 中定义的 `get_lambda_seq(x, y, alpha = 0.5)` 来验证 `train()` 函数的 `tuneLength` 参数选取的 `lambda` 序列与 `elasticnet_model` 对象的结果所示完全相同。使用 `repeatedcv` 且 `tuneLength = 10` 报告的最终超参数或微调参数如下：

![](img/page269-02.png)

ElasticNet 模型的模型系数如下：

![](img/page270-01.png)

对 `train_df` 和 `test_df` 的预测如下：

![](img/page270-02.png)

## 7.8 | 结果汇总

**表 7.10** 总结了使用 `glmnet` 和 `caret` 包在 `ipl_df` 上构建的所有模型的结果。从 **表 7.10** 中，我们可以看到

**1.** 使用 `glmnet` 和 `caret` 构建的 LASSO 回归报告了对应最佳模型的相同 `lambda` 值。

**2.** `ridge` 模型在 `test` 集合上的性能优于 LASSO 回归。`ridge` 回归中评估的 `lambda` 值范围是使用 `get_lambda_seq(x, y, alpha = 0.001)` 获得的。

**3.** 使用 `tuneGrid` 和 `tuneLength` 的 `ElasticNet` 模型结果几乎相似。结果的细微差异是由于我们使用 `get_lambda_seq(x, y, alpha = 1)` 创建了要评估的 `lambda` 序列并将其传递给 `tuneGrid`；然而，`caret` 创建了 `lambda` 值范围 `get_lambda_seq(x, y, alpha = 0.5)` 用于 `tuneLength`。

`glmnet` 也可以用于构建多元高斯模型。通过设置 `family = mgaussian`，`glmnet` 函数可以处理多任务学习问题，即存在多个（相关）响应 `Y`s 时。

![](img/page271-01.png)

## 7.9 | 机器学习 – 使用 glmnet 的逻辑回归

当响应变量 (`Y`) 为二元时，通常使用线性逻辑回归模型。逻辑回归模型通过预测变量的线性函数表示类条件概率。假设结果称为正例（通常编码为 `Y` = 1）和负例（通常编码为 `Y` = 0）。逻辑回归模型通过预测变量的线性函数表示类条件概率，给出为

![](img/page271-02.png)

其中 `Z` = `β`[0] + `β`[1] * `X`[1] + `β`[2] * `X`[2] + … + `β`[`m`] * `X`[`m`]

这里 `X`[1]、`X`[2]、… `X`[`m`] 是自变量或特征。如果数据有 `n` 个观测值，`Y`[1]、`Y`[2]、… `Y`[`n`]，那么似然函数，即观察结果 `L` = P(`Y`[1], `Y`[2], … `Y`[`n`]) 的联合概率，对于特定的 `Z` = `β`[0] + `β`[1] * `X`[1] + `β`[2] * `X`[2] + … + `β`[`m`] * `X`[`m`] 给出为 (Kumar, 2017)

![](img/page271-03.png)

取自然对数，式 (7.18) 可重写如下：

![](img/page271-04.png)

式 (7.19) 可简化如下：

![](img/page272-01.png)

目标（成本函数）是找到使 式 (7.19) 最大化的 `β` 系数，即对数似然函数。在 `glmnet` 中，惩罚逻辑回归的目标函数使用带正则化参数的负二项对数似然，给出为

![](img/page272-02.png)

**表 7.11** 显示了我们在分类中使用的 `HR_Attrition` 数据的快照（第 6 章）。请参阅 第 6 章 了解有关 `HR_Attrition` 数据的数据处理和特征工程的更多详细信息。我们将使用相同的数据使用 `glmnet` 包构建逻辑回归模型。构建逻辑回归模型的步骤将与 第 7.6 节 中遵循的步骤相似。

![](img/page272-03.png)![](img/page272-04.png)

### 7.9.1 创建特征集 (X) 和结果变量 (Y)

让我们从 **表 7.11** 中显示的 `attrition_with_dummy_dt` 中获取预测变量和结果特征。

![](img/page273-01.png)![](img/page274-01.png)

### 7.9.2 创建训练集和测试集

来自 `caret` 包的 `createDataPartition()` 函数提供了将数据集随机拆分为训练集和验证数据集的能力。

![](img/page274-02.png)

由于 `glmnet` 期望 `X` 特征以矩阵形式存在，让我们将 `train_dt` 类型转换为 `matrix` 并创建 `X`（特征）和 `Y`（结果）变量。

![](img/page274-03.png)

### 7.9.3 分类模型 – 使用 glmnet 的逻辑回归

现在，我们将使用 `family = binomial` 构建 LASSO 逻辑回归模型。

![](img/page274-04.png)

鼓励读者使用 第 7.6.3 节 中定义的 `get_lambda_max` 和 `get_lambda_seq` 函数来理解为逻辑回归模型生成的 `lambda` 序列。让我们获取逻辑模型的系数。

![](img/page274-05.png)![](img/page275-01.png)

正如可以看到的，LASSO 回归使某些特征的系数恰好等于零。请注意，我们没有删除一些特征，这些特征

**1.** 线性相关（`RM_REPORTEES_COUNT` = `RM_REPORTEE_MALE` + `RM_REPORTEE_FEMALE`），模型自行丢弃。

**2.** 高度相关，`AGE_DIFFERENCE` 与 `RM_AGE`，模型自行丢弃。但如果预测变量成组相关，LASSO 可能没有帮助。`ElasticNet` 与 `α = 0.5` 倾向于将组一起选入或剔除。



使用 `init_model` 进行预测可以通过使用 `predict` 函数并传递 `train_dt` 或 `test_dt` 以及参数 `s` 来实现，该参数取预测时使用的 `lambda` 值。我们还将传递参数 `type = response`，它将报告 (`Y` = 1) 的条件概率。我们将以默认截断值 0.50 将此概率转换为 `class`。要直接报告 `class`，我们可以传递 `type = class`。

![](img/page275-02.png)![](img/page276-01.png)![](img/page277-01.png)

### 7.9.4 分类模型 – 使用 Caret 的逻辑回归

我们将使用 `train` 函数的 `tuneLength` 参数来微调 `ElasticNet` 模型。有关 `tuneLength` 的详细信息，请参阅 第 7.7.3 节。

当 `tuneLength=10` 时，对于每个 `alpha`，将评估 10 个 `lambda` 值。因此，总共将构建 100 个模型。

![](img/page277-02.png)![](img/page278-01.png)![](img/page279-01.png)

`ElasticNet` 模型的模型系数如下：

![](img/page280-01.png)

对 `train_dt` 的预测如下：

![](img/page280-02.png)![](img/page281-01.png)

对 `test_dt` 的预测如下：

![](img/page281-02.png)![](img/page282-01.png)

我们已经看到了使用 `glmnet` 方法解决回归以及分类问题。

### Summary

在本章中，我们学习了

**1.** 通过定义成本函数并使用优化算法最小化成本函数来构建模型。

**2.** 实现 GD 算法以优化基于回归的模型的成本函数。

**3.** 偏差与方差权衡以及如何使用正则化避免模型过拟合。

**4.** 高级回归模型，如 `LASSO`、`ridge` 和 `ElasticNet` 模型。

**5.** 使用 `glmnet` 包构建机器学习模型（回归以及分类）。

**6.** 使用 `caret` 包构建机器学习模型（回归以及分类）。

### Exercise

数据集 `SAheart.data` 取自以下链接：

[`www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data`](http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data)

数据集 `SAheartrateData.txt` 包含南非西开普省心脏病高风险地区男性的记录。每例冠心病约有两例对照。许多冠心病阳性男性在冠心病事件后接受了降压治疗和其他降低危险因素的项目。在某些情况下，测量是在这些治疗后进行的。这些数据取自 Rousseauw 等人 (1983) 在 *South African Medical Journal* 中描述的更大数据集。它是一个制表符分隔的文件（.csv）并包含以下列：

• `sbp` – 收缩压

• `tobacco` – 累计烟草（kg）

• `ldl` – 低密度脂蛋白胆固醇

• `adipos ity`

• `famhist` – 心脏病家族史（存在，缺席）

• `typea` – A 型行为

• `obesity`

• `alcohol` – 当前酒精消费

• `age` – 发病年龄

• `chd` – 响应，冠心病

`chd` = 1 和 `chd` = 0 将分别称为 `chd` 和 `no chd` 病例。

**1.** 找出数据集中 `chd` 和 `no chd` 可用的病例数。使用条形图绘制结果，其中 `X` 为 chd 或 no chd，`Y` 给出每个组中的样本计数。

**2.** 使用 `caret` 构建 `lasso` 逻辑回归模型。使用 `K`\-折交叉验证（`K` = 5）并使用 ROC AUC 分数报告最佳模型。

**3.** 使用 `caret` `glmnet` 方法构建 `ridge` 逻辑回归模型。使用 `K`\-折交叉验证（`K` = 5）并使用 ROC AUC 分数报告最佳模型。

**4.** 使用 `caret` 构建 `ElasticNet` 逻辑回归模型。使用 `train()` 的 `tuneLength` 参数微调模型并使用 ROC AUC 分数报告最佳模型。

**5.** 使用 `glmnet` 包构建 `lasso` 逻辑回归模型。使用 K 折交叉验证（`K` = 5）报告最佳模型。比较并描述该模型的结果与第 2 题中获得的模型。

**6.** 使用 `glmnet` 包构建 `ridge` 逻辑回归模型。使用 `K`\-折交叉验证（`K` = 5）报告最佳模型。比较并描述该模型的结果与第 3 题中获得的模型。

**7.** 使用 `glmnet` 包构建 `ElasticNet` 逻辑回归模型。使用 `K`\-折交叉验证（`K` = 5）报告最佳模型。比较并描述该模型的结果与第 4 题中获得的模型。

### Bibliography

**1.** Anon (2018), *“Glmnet：如何选择 Lambda 和 Alpha”*，网址：[`stats.stackexchange.com/questions/357190/glmnet-how-to-select-lambda-and-alpha`](https://stats.stackexchange.com/questions/357190/glmnet-how-to-select-lambda-and-alpha)，于 2021 年 5 月 10 日访问。

**2.** Friedman J and Hastie T, *“通过坐标下降的广义线性模型的正则化路径”*，网址：[`web.stanford.edu/~hastie/Papers/glmnet`](https://web.stanford.edu/~hastie/Papers/glmnet)，于 2021 年 1 月 21 日访问。

**3.** Friedman J, Hastie T, and Tibshirani R (2008), “通过坐标下降的广义线性模型的正则化路径”，*Journal of Statistical Software*，33(1)，1–22。

**4.** Hastie T and Qian J (2014), *“Glmnet and Vignette”*，网址：[`web.stanford.edu/~hastie/glmnet/glmnet_alpha.html`](https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html)，于 2021 年 1 月 21 日访问。

**5.** Hastie T, Qian J and Kenneth Tay (2021), “An *Introduction to Glmnet”*，网址：[`glmnet.stanford.edu/articles/glmnet.html`](https://glmnet.stanford.edu/articles/glmnet.html)，于 2021 年 5 月 10 日访问。

**6.** Malviya D (2020), *“Machine Learning”*，网址：[`www.kaggle.com/deepprabhamalviya/ml-day8`](https://www.kaggle.com/deepprabhamalviya/ml-day8)，于 2021 年 5 月 10 日访问。

**7.** Mitchell T M (2006), “The Discipline of Machine Learning”，Carnegie Mellon University Report (CMU-ML-06-108)，可获得于 [`www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf`](https://www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf)，于 2021 年 8 月 2 日访问。

**8.** Pradhan M and Kumar U D (2019), *“Machine Learning Using Python”*，Wiley，Indian Institute of Management，Bangalore。

**9.** Simon N, Friedman J, and Hastie T (2013), “A Blockwise Descent Algorithm for Group-Penalised Multiresponse and Multinomial Regression”，网址：[`arxiv.org/abs/1311.6529`](https://arxiv.org/abs/1311.6529)，于 2021 年 5 月 10 日访问。

**10.** Simon N, Friedman J, Hastie T, and Tibshirani T (2011), “通过坐标下降的 Cox 比例风险模型的正则化路径”，*Journal of Statistical Software*，39(5)，1–13。

**11.** Tibshirani R, Bien J, Friedman J, Hastie T, Simon N, Taylor J, Tibshirani R J (2010), “Strong Rules for Discarding Predictors in Lasso-type Problems”，Journal of the Royal Statistical Society: Series B *(Statistical Methodology)*，74(2)，245–266。

________________________

¹[`web.stanford.edu/~hastie/glmnet/glmnet_alpha.html`](https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html)

²[`web.stanford.edu/~hastie/Papers/glmnet.pdf`](https://web.stanford.edu/~hastie/Papers/glmnet.pdf)

## 集成方法

## 8

*人人都知其道，少有人行之。*

**—菩提达摩**

学习目标

阅读本章后，你将能够：

• 学习集成方法背后的数学原理。

• 学习开发诸如 `Random Forest`、`Gradient boosting machine` 和 `Xtreme boosting` 等集成技术。

• 学习使用集成方法生成 `variable importance`（`feature importance`）。

• 理解机器学习算法中的 `hyper-parameters` 以及如何搜索最佳 `hyper-parameters`。

## 8.1 | 概述




# 集成方法

集成方法是一种学习算法，它接收一组估计器或分类器（模型），并使用诸如多数投票等策略对新的数据点进行分类。多数投票可以基于简单地统计每个分类器的投票，也可以基于分类器的准确率进行加权。集成方法也用于回归问题，其中新数据的预测是来自一组回归模型的所有预测的简单平均值或加权平均值，如 **图 8.1** 所示。

在 **图 8.1** 中，`K` 和 `N` 是原始集合中特征数和记录数，而 `k` 和 `n` 是采样集合中特征数和记录数。需要注意的是，构建多个分类器（模型）需要多个数据集（使用不同的特征和记录）。但在实践中，总有一个训练集可用。我们可能必须采用某些策略，为学习算法提供训练集的不同子集（视图）。

1. 策略如自助采样（训练数据的有放回随机样本）可用于创建训练集的多个子集。自助法与‘随机子空间方法’结合也用于特征子集的随机选择。这种自助法与随机子空间方法相结合的思想是随机森林算法的起源，并使其有别于早期的袋装算法（这些算法是未应用随机子空间方法的剪枝决策树分类器）。

2. 另一种可采用的策略是通过为训练数据的观测值分配权重，并向学习算法提供权重更高的观测值。一般来说，Boosting 算法在学习过程中依赖于这一策略。

![](img/page286-01.png)

创建训练数据的不同子集视图类似于为学习算法创建不同的经验，使其可以从中学习有用的模式。创建训练数据不同子集的这一概念与 第 7 章 中给出的机器学习的正式定义相联系。在本章中，我们将主要研究随机森林、自适应提升和极端提升。然而，我们还将对可使用 `R` 实现的其他袋装和提升算法提供一些见解。

## 8.2 | 随机森林

随机森林（通常称为 Bagging）是使用不同采样策略开发若干棵树（因此得名‘森林’）的流行集成方法之一（Breiman, 1996, 2001）。¹ 最常用的采样策略之一是 **Bootstrap 聚合**（或 **Bagging）。** Bagging 是有放回的随机采样。利用数据和特征的样本，随机森林开发多个分类模型（通常是树）。在连续结果变量（回归问题）的情况下，各种基础学习器的预测结果会被平均。在离散结果变量（分类问题）的情况下，新观测值通过多数投票进行分类。在他的开创性工作中，Breiman (1994, 2001) 认为随机森林（`RF`）在真实和模拟数据集上的回归和分类问题中都实现了显著的准确率提升。数学上，`RF` 是学习器 {`L``k`} 的集合，`k` = 1, 2,…, `N`}。`X` 是输入集合，`T`[`k`] 是独立同分布的样本，学习器（或分类器）`L``k` 在其上开发。

随机森林是按照以下步骤开发的（Kumar, 2017）：

1. 假设训练数据有 `N` 个观测值。需要生成若干个大小为 `M`（`M` ≤ `N`）的有放回样本（Bootstrap 聚合或 Bagging）。设基于训练数据集采样得到的样本数为 `K`，即树的数量为 `K`。

2. 如果数据有 `n` 个预测变量，则采样 `m` 个预测变量（`m` < `n`）。此步骤用于使树相互独立。

3. 使用步骤 2 中的预测变量样本为步骤 1 中生成的每个样本开发树。如果结果变量是离散的，则开发分类树；如果结果变量是连续的，则开发回归树。

4. 对步骤 1 中生成的所有样本重复步骤 3。

5. 在分类情况下使用多数投票预测结果变量值，在连续结果变量情况下使用预测值的平均值。

![](img/page287-01.png)

**图 8.2** 显示了随机森林模型开发的结构。在开发基础模型时使用不同特征样本的目的是使基础模型彼此独立。

### 8.2.1 袋外数据

使用 Bootstrap 聚合程序的一个优点是它提供了称为 `Out-of-Bag (OOB)` 数据的验证数据。在一个基础模型中，至少有 (`N`-`M`) 条记录不会参与模型构建；不属于基础模型的部分记录称为袋外数据。考虑一个有 20 条记录的数据集，标记为 1, 2 起，直至 20。设从这 20 条记录中生成大小为 10 的自助样本。一些可能的样本显示在 **表 8.1** 中。

在 **表 8.1** 中，样本 1 由记录 {7, 8, 9, 6, 2, 3, 3, 4, 17, 19} 组成，即记录 {1, 5, 10, 11, 12, 13, 14, 15, 16, 18, 20} 不属于样本 1；这些记录对样本 1 来说是袋外的。记录 16 在任何样本中都不存在，因此可以用作使用 **表 8.1** 中列出的样本生成的全部五个基础模型的测试数据。所有不属于某棵树训练数据的情况都可作为验证数据使用，这类情况称为 Out-Of-Bag 数据。随机森林模型使用 `Out-of-Bag (OOB)` 数据作为验证数据进行验证，因此不需要单独的验证数据。大约 33% 的数据不参与构建 `RF` 中的基础模型。然而，许多数据科学家仍然创建单独的验证数据。

### 8.2.2 使用随机森林预测净推荐值（NPS）

我们将通过净推荐值（`NPS`）预测的例子讨论随机森林方法。`NPS` 可用作衡量客户忠诚度的领先指标，基于一个问题 – 您有多大可能向朋友或同事推荐我们的公司或产品/服务？

客户在 0 到 10（11 点）量表上对回答进行评分。高度满意的客户很可能给出 9 或 10 分，被称为推荐者；被动客户给出 7 或 8 分，而那些给出 6 分及以下的则为贬损者。

![](img/page287-02.png)

将推荐者的百分比减去贬损者的百分比得出一个单一数字 – 公司的 `NPS`。贬损者很可能在朋友和同事中传播对组织的负面情绪。

#### 示例 – 随机森林模型开发

All India Electronics（`AIE`）是电子小工具的领先制造商，业务面向 B2B 领域。它为其向客户销售的设备提供预防性以及纠正性维护服务。客户满意度是业务增长的关键，`AIE` 的管理层希望改善其目前的 `NPS` 评分，该评分目前为 49%。




在一段时间内，AIE 开展了反馈调查并获得了客户的 NPS 评分。`device_feedback.csv` 包含客户人口统计信息、客户在一年期间为解决所面临的任何问题而进行的互动，以及这些客户最终给出的评分。此反馈是在预防性或纠正性维护服务的合同续签过程中收集的。`Table 8.2` 显示了 `device_feedback.csv` 数据集中可用的特征。

注意，大多数特征都是使用原始数据派生的，而原始数据主要由日期列组成。

### Table 8.2 Feature list

| 数据代码 | 描述 |
|---|---|
| `Customer ID` | 已随机化的唯一客户 ID |
| `Device` | 接受服务的设备 |
| `contract_renewed` | 这是新合同还是续约 |
| `new_or_renew` | 合同是否续约 |
| `Age in Yrs` | 该客户在 All India Electronic LLP 的年限 |
| `Count of sr after pm` | 预防性维护后提出的服务请求数量 |
| `days_to_report_first_issue_after_contract_renewal` | 合同续约后报告第一个问题所需的天数 |
| `days_to_resolve_first_issue_after_contract_renewal` | 合同续约后解决第一个问题所需的天数 |
| `days_to_resolve_last_issue_before_contract_expiry` | 合同到期前解决最后一个问题所需的天数 |
| `duration_between_report-ed_issues` | 合同到期前提出的最后一个问题与合同续约后提出的第一个问题之间的间隔 |
| `Zone` | 客户所属区域 |
| `Location` | 客户所在城市 |
| `papers_for_the_new_contracts_received` | 反馈时客户是否收到了新合同的合同文件 |
| `inclusions_exclusions_explained` | 合同续约期间是否解释了合同的包含和排除条款 |
| `services_in_contract_explained` | 合同续约期间是否解释了合同的服务条款 |
| `number_of_issue_reported` | 过去一年报告的问题数量 |
| `service_agency` | 服务是由特许经营提供还是由公司直接提供 |
| `rate_recommend_products_services` | 客户在 0–10  scale 上给出的评分 |
| `nps_classification` | 基于评分得出的 NPS 分类 |
| `merged_nps_classification` | Detractor 和 passive 合并为 Detractors。Promoter 单独保留。此项未使用。 |

派生特征列表如下：

1. `days_to_report_first_issue_after_contract_renewal`: `(first_issue_report_date_after_contractrenewal) - (contract_start_date)`
2. `days_to_resolve_first_issue_after_contract_renewal`: `(first_issue_closed_date_after_contractrenewal) - (first_issue_report_date_after_contract_renewal)`
3. `days_to_resolve_last_issue_before_contract_expiry`: `(last_issue_closed_date_before_contractexpiry) - (last_issue_report_date_before_contract_expiry)`
4. `duration_between_reported_issues`: `(first_issue_report_date_after_contract_renewal) - (last_issue_report_date_before_contract_expiry)`
5. `number_of_issue_reported`: `number_of_issue_reported = ZERO if (days_to_report_first_issue_after_contract_renewal) == 0 & (last_issue_report_date_before_contract_expiry) - (first_issue_report_date_after_contract_renewal) ≥ 365.0`
6. `number_of_issue_reported = ONE if (last_issue_report_date_before_contract_expiry) - (first_issue_report_date_after_contract_renewal) ≤ 0.0 & (contract_start_date) - (first_issue_report_date_after_contract_renewal) == 0`
7. `number_of_issue_reported = ONE if (contract_start_date) - (first_issue_report_date_after_contract_renewal) ≤ 0.0 & (last_issue_report_date_before_contract_expiry) - (first_issue_report_date_after_contract_renewal) == 0.0`
8. `number_of_issue_reported = MORE THAN ONE if None of the above condition is satisfied`

特征工程在任何机器学习模型中都发挥着关键作用，随机森林模型也不例外。上述所有派生特征在进行进一步分析之前都已得到业务的充分验证。我们将构建一个 NPS 分类模型，即使用 RF 算法尝试对贬损者、被动者和推广者进行分类。

## 8.3 Class Imbalance Problem

`device_feedback.csv` 有 1,889 个观测值和 20 个特征。结果变量，即 `NPS_CLASSIFICATION` 有以下标签：

1. `Promoter` 1,009
2. `Passive` 819
3. `Detractor` 77

该数据集有 53% 的推广者、43% 的被动者和仅 4% 的贬损者。从分类问题的角度来看，这是一个典型的类别不平衡数据的案例。如果结果特征中案例的比例偏向某一类，则称数据集为类别不平衡。在理想情况下，我们可以说当所有类别中案例的比例相同（在二分类情况下，这将是两个类别各 50%）时，数据存在类别不平衡问题。这种情况在现实使用案例中很难找到，因为大多数分类问题在一定程度上都会存在类别不平衡。然而，如果案例的比例高度偏斜（例如二分类问题中 90%–10% 的情况），分类问题就变得难以解决。

在这些数据中，我们观察到结果特征 `NPS_CLASSIFICATION` 中只有 4% 的客户属于贬损者类。因此，我们可以将此标记为类别不平衡问题。由于只有 4% 的记录是贬损者，传统模型可能无法很好地对贬损者进行分类。换句话说，数据中没有足够的学习机会来正确分类贬损者。

有时，对结果变量进行简单的对数变换可能有助于减少连续结果变量的偏斜并提高模型性能。在极端情况下，采样策略如 `SMOTER`（回归的 SMOTE）也可以应用于处理回归问题中的极端数值。

### 8.3.1 Dealing with Class Imbalance – Regrouping Classes

在应用任何学习算法之前，我们可能需要消除类别不平衡问题。处理此数据中类别不平衡的一种方法是合并类别。`MERGED_NPS_CLASSIFICATION` 列是通过将 Passive 重新分组到 Detractors 创建的。Passive 和 Detractors 组合并有两个原因：

1. 模型现在可以开发来解决二分类问题（推广者 vs. 贬损者）。在二分类中，我们将非推广者标记为贬损者。
2. 相对于结果变量，数据不再显示类别不平衡问题。

现在，如果我们将其作为二分类问题来解决，我们可能会得到贬损者和推广者的合理正确分类。请注意，这种重新分组应与业务进行验证。

采样策略是在处理分类问题数据集中类别不平衡问题时的重要考虑因素。然而，在回归问题中，连续结果变量的分布也可能偏斜，并可能导致均方误差升高。

### 8.3.2 Dealing with Class Imbalance – Sampling Strategy

处理类别不平衡问题的另一种方法是应用采样策略。两种常用的采样策略是上采样和下采样。让我们以 `device_feedback.csv` 数据为例来理解上采样。`NPS_CLASSIFICATION` 中标签的总计数如下：

1. `Promoter`: 1,009
2. `Passive`: 819
3. `Detractor`: 77



## 命名法
让我们定义术语 `majority class` 和 `minority class`。`majority class` 指的是具有最大类别频率的标签，即本数据集中 `Promoter` 类。`minority class` 指的是案例数最少的标签，即本数据集中 `Detractor` 类。

### 1. 上采样策略
上采样策略应用于数据，使得案例数，即不属于 `majority class` 的所有标签的类别频率，变得等于 `majority class`。实现此目的的一种方法是，对不属于 `majority class` 的所有案例进行有放回的随机抽样。如果我们在 `device_feedback` 数据中应用上采样策略，`NPS_CLASSIFICATION` 中各标签的总计数将如下所示：
- `Promoter`: 1,009
- `Passive`: 1,009
- `Detractor`: 1,009
上采样策略平衡了类别分布，但由于该策略只是重复数据（通过重复），因此不会提供额外的信息来改善模型性能。请注意，对其他类别进行上采样的百分比不一定需要达到使所有类别案例数相等程度。在使用 `h2o` 中的方法时，我们可以指定上采样的百分比。

### 2. 下采样策略
下采样策略应用于数据，使得案例数，即不属于 `minority class` 的所有标签的类别频率变得等于 `minority class`。实现此目的的一种方法是，对不属于 `minority class` 的所有案例进行有放回或无放回的随机抽样。如果我们在设备反馈数据中应用下采样策略，`NPS_CLASSIFICATION` 中各标签的总计数将如下所示：
- `Promoter`: 77
- `Passive`: 77
- `Detractor`: 77

#### 结果变量的简单对数变换
有时，对结果变量进行简单的对数变换可以帮助减少连续结果变量的偏度并改善模型性能。在极端情况下，像 `SMOTER`（回归的 Smote）这样的采样策略也可以应用于处理回归问题中的极端数值。

#### R 中的 UBL 包
`UBL` 包在 R 中实现了 `SmoteR` 采样方法（Torgo et al. (2013)）使用 `SmoteRegress()`。该包还通过 `SmognRegress()` 实现了带高斯噪声的回归合成少数类过采样技术（`SMOGN`）。
尽管该策略减少了数据中的总体案例数，但它消除了类别不平衡问题，并创建了一个异质混合，算法可以从中学习有用的模式。请注意，对其他类别进行下采样的百分比不一定需要达到使所有类别案例数相等程度。在使用 `h2o` 中的方法时，我们可以指定下采样的百分比。

### 3. 合成少数类过采样技术（SMOTE）
合成少数类过采样技术（`SMOTE`）是 Chawla 等人（2002）提出的另一种策略。该策略为每个少数类案例合成新示例，具体如下：
- 在 `minority class` 中，找到给定少数类案例（假设为 `A`）的 `k` 个最近邻。Chawla 等人（2002）建议为给定案例找到五个最近邻。
- 绘制一条线段，将给定 `minority case`（`A`）与 `k` 个 `minority class` 最近邻中的任意/全部连接起来。
- 根据需要过采样的案例数量，随机选择 `k` 个邻居中的任意/全部。例如，如果需要的过采样量为 300%，则从 `minority case`（`A`）的五个邻居中选择三个最近邻，并在三条线段上生成三个随机样本。样本将按如下方式生成：
  - 取特征向量（例如案例 `A`）与其中一个随机选择的最近邻的特征向量（假设为 `B`）之间的差值。
  - 将差值乘以 0 到 1 之间的随机数（Xu et al. 2017）。这将产生一个新的特征向量（假设为 `C`）。
  - 将新向量 `C` 加到特征向量（例如案例 `A`）上。这将在连接 `A` 和 `B` 的线段上选择一个随机案例。
  - 沿着另外两条线段重复上述步骤以生成另外两个样本。
`DMwR` 包中的 `SMOTE()` 方法通过设置参数 `perc.over` 实现 `minority class` 的合成采样。`SMOTE()` 方法还通过设置参数 `perc.under` 支持对 `majority class` 进行欠采样。
- `perc.over`：该参数默认设置为 200。对于原始数据集中属于 `minority class` 的每个案例，200/100，即为每个案例创建两个新示例（Anon, 2018; Torgo, 2010）。
- `perc.under`：该比例是相对于新生成的 `minority class` 记录数计算的。如果生成了 200 条 `minority class` 新记录，`perc.under` 的值为 200 将随机选择 200 个属于 `majority classes` 的案例。该参数默认设置为 200（Anon, 2018; Torgo, 2010）。
`SMOTE()` 方法也可以通过 `caret` 包的 `trainControl()` 方法调用。有关 `SMOTE` 的更多详细信息可通过 `?DMwR::SMOTE` 找到。

### 4. 随机过采样示例（ROSE）
随机过采样示例（`ROSE`）由 Menardi 和 Torelli（2014）提出，是另一种消除类别不平衡的采样技术。`ROSE` 作为一种方法通过 R 中的 `ROSE` 包实现，可用于在二分类问题中消除类别不平衡。为了理解 `ROSE` 采样，让我们取一个具有 `n` 个观测值的通用训练数据集 `T[n]`。设 (`x[i]`, `y[i]`) 表示一个观测值，其中 `X` 表示特征向量，`Y[i]` 属于 {`C[0]`, `C[1]`}，即二元类别。设类别 `C[j]`，`j` = 0,1 中的案例数为 `n[j]` < `n`。新样本按如下方式生成：
- 选择一个类别标签，`y*` = `C[j]`，概率为 `P[j]` = 0.5。`P[j]` = 0.5 确保大约相同数量的案例属于两个类别。
- 从训练集 `T[n]` 中以概率 ![图像](img/pageIn_ch8-01.png) 选择一个观测值 (`x[i]`, `y[i]`)，使得 `y[i]` 属于类别标签 `y*`。
- 生成一个新的观测值 `x*`，其均值为 ![图像](img/pageIn_ch8-02.png) ，方差为 `x[i]`。对于各种特征 `x` 的均值和方差，是分别针对类别标签 {`C[0]`, `C[1]`} 计算的。
本质上，在上述步骤中，我们是从训练集中随机挑选一个观测值，并在其邻域中生成一个新的样本 (`x*`, `y**`)。邻域的形状由特征的均值决定，宽度由特征的方差决定。可以很容易地证明，根据 `ROSE` 生成新示例相当于从核密度估计 `f(x|C[j])` 生成数据（Menardi and Torelli, 2014）。`ROSE` 也可用于生成分类特征的新样本。基本上，如果 (`x[i]`, `y[i]`) 中的某个特征是分类的，则新样本 (`x*`, `y**`) 将具有与所选观测值 (`x[i]`, `y[i]`) 相同的分类特征值。
与 `SMOTE` 不同，`SMOTE` 通过随机选择位于 `minority case` 及其最近邻之间线段上的点来生成样本，`ROSE` 使用模拟自助法（Efron and Tibshirani, 1993）来生成新样本。`ROSE()` 方法也可以通过 `caret` 包的 `trainControl()` 方法调用。有关 `ROSE` 的更多详细信息可通过 `?ROSE::ROSE` 找到。
请注意，在后续章节中，我们将使用 `h2o` 包演示上采样和下采样策略的使用。我们鼓励读者使用 `caret` 包在设备反馈数据上实现 `SMOTE` 和 `ROSE` 采样。
`UBL` 包在 R 中实现了 `SmoteR` 采样方法（Torgo et al. (2013)）使用 `SmoteRegress()`。该包还通过 `SmognRegress()` 实现了带高斯噪声的回归合成少数类过采样技术（`SMOGN`）。



## 8.4 | 使用 h2o 包的随机森林

集成模型（使用 `h2o` 包进行 bagging 和 boosting）的建模步骤如下：
**1.** 为了超参数微调，定义一组取值范围。该超参数的取值范围称为网格空间。需要微调的超参数可能是算法所有超参数的一个子集。
**2.** 定义搜索标准，该标准连同搜索策略（随机或笛卡尔）将包括用于报告最佳超参数值组合/最佳模型的指标。
**3.** 使用训练数据和验证/交叉验证数据分别构建模型并微调超参数。保存报告最佳模型的超参数值。
**4.** 固定已学习的超参数并迭代步骤 1 至 3，以查看是否还有更多超参数需要微调。
**5.** 在测试集上评估性能并保存模型，以便在部署场景中对案例进行评分。

我们将使用最先进的包 `h2o` 来构建集成模型。如果 `h2o` 包之前已安装且有最新版本可用，则 `h2o` 包的初始化可能因版本不匹配而报错。在这种情况下，请在继续之前重新安装包。在继续之前，请在控制台中运行下面两行。注意，我们已根据 `h2o` 网站上的语法和定义进行了复现，该网站可在 [`www.h2o.ai/resources`](https://www.h2o.ai/resources)/ 获取。

```
if (“package:h2o” %in% search()) { detach(“package:h2o”, unload=TRUE)}
```
```
if (“h2o” %in% rownames(installed.packages())) { remove.packages(“h2o”)}
```

![](img/page293-01.png)

以下代码可用于使用 `h2o` 包导入数据：

![](img/page293-02.png)

如果 Java 版本不受支持或机器上安装的是 32 位 Java 版本，则 `h2o` 的初始化可能会报错。请在继续之前更新 Java。此外，请通过在控制台中输入以下内容检查 R 环境是否指向正确的 Java 版本。

```
> Sys.getenv(“JAVA_HOME”)
‘/Library/Java/JavaVirtualMachines/jdk1.7.0_60.jdk/Contents/Home’
```

您可以使用控制台更改环境：

```
>Sys.setenv(JAVA_HOME = ‘/Library/Java/JavaVirtualMachines/jdk1.8.0_101.jdk/Contents/Home’)
```

![](img/page294-01.png)

`h2o.init` 提供的信息有助于理解 `h2o` 包启动的并行处理：
**3.** 集群可以被视为一组互连的计算机，其中节点或机器是集群中的物理机器。对于单台机器（个人笔记本电脑），节点数和集群数相同。`h2o` 集群总节点数：1 表示我们正在单台机器上运行此程序，可用内存（RAM）为 7.94 GB。
**4.** 处理器/CPU/核心可以被视为计算机中进行计算的物理设备。现代笔记本电脑可能拥有 4 到 16 个核心不等。我们可以看到运行该程序的机器有八个核心。
**5.** 给定一个包含 `n` 个节点的集群，其中每个节点有 `c` 个 CPU，则模型数量为 2 * `c`。因此，在此机器上我们可以并行构建 16 个模型。

**表 8.3** 显示了 `device_feedback` 数据的快照。

![](img/page295-01.png)![](img/page295-02.png)

让我们使用下面的代码片段获取 `raw_h2f` 的描述性统计信息。这是一个预处理后的数据，因此汇总统计信息可能不会显示数据存在任何问题。

![](img/page295-03.png)![](img/page296-01.png)

### 8.4.1 | 数据中的特征列表

在本节中，我们将创建一个数值特征和分类特征的列表，然后再创建一个将用于建模的所有特征的列表。**表 8.4** 显示了 `filter_h2f` 的快照，该快照是在下面的代码片段中创建的。

数据集中的数值特征如下：

![](img/page296-02.png)![](img/page297-01.png)![](img/page297-02.png)

数据集中的分类特征如下：

![](img/page297-03.png)![](img/page298-01.png)

### 8.4.2 | 使用 h2o 的模型

我们可以使用 `h2o` 的 `splitframe` 方法将数据拆分为训练集和测试集。`splitFrame` 创建的子集数量总是比参数 `ratios` 中指定的数量多一个。请注意，这不会给出精确的拆分。`h2o` 旨在在大数据环境中使用概率拆分方法而不是训练和测试数据的精确拆分来实现高效。

例如，当指定拆分为 `c(0.70)` 时，`h2o` 将产生测试/训练拆分，其期望值为 0.70/0.30 而不是精确的 0.70/0.30。根据 R 文档，‘在小数据集上，结果拆分的尺寸与期望值的偏差比大数据上更大，在大数据上它们会非常接近精确值（E LeDell, 2020）’。

![](img/page298-02.png)

训练集和测试集数据框的维度如下：

![](img/page299-01.png)

### 8.4.3 | 使用 h2o 包的随机森林

`h2o` 包具有 `randomForest` 方法，可直接调用以构建随机森林模型。然而，由于存在需要微调的超参数，我们将使用 `grid` 方法构建随机森林模型。此方法将帮助我们微调随机森林的超参数。请注意，`h2o` 中 `randomForest` 方法的实现与原始随机森林算法（Brieman, 2001）存在细微差异。`h2o` 的随机森林不执行自助采样，正如 Brieman（2001）的原始论文中所提出的。对于每棵树，`randomForest` 方法以 0.632 的速率采样观测值（这是任何自助样本中唯一行的期望值）。此外，还可以使用参数来控制树的生长。

### 8.4.4 | 随机子空间选择

控制随机特征选择的拟参数如下 *(来源：* docs.h2o.ai)：
**1.** `mtries` – 该参数表示在树的每个层级随机选择的列数。可传递给此参数的有效值有：−2、−1 以及任何 ≥1 的值（Anon, 2016）。在分类问题中，默认值 −1 表示选择的列数为预测变量数的平方根。在回归问题中，默认值 −1 表示选择的列数为 `p/3`，其中 `p` 为预测变量数。值为 −2 表示选择所有预测变量。任何大于或等于 1 的值，表示随机选择该数量的预测变量。
**2.** `col_sample_rate_per_tree` – 该参数指定为每棵树随机选择的列的比例（不放回）。取值范围为 0.0 到 1.0 之间。默认值是 1（为每棵树的生长选择所有列）。
**3.** `col_sample_rate_change_per_level` – 该参数与 `col_sample_rate_per_tree` 协同工作，用于随着树深度的增加而改变随机选择的列的比例。此参数的值可在 0 到 2 之间（默认为 1）。例如，假设 `col_sample_rate_change_per_level` 设置为 0.5，则
• level 1: `col_sample_rate_per_tree`
• level 2: `col_sample_rate_per_tree` * 0.5
• level 3: `col_sample_rate_per_tree` * 0.5²
• level 4: `col_sample_rate_per_tree` * 0.5³ 依此类推。

### 8.4.5 | 类别不平衡

**1.** `balance_classes` – 该参数用于消除数据中的类别不平衡。默认值是 FALSE。如果设置为 TRUE，则使用上采样来消除类别不平衡。




### 2. `class_sampling_factors`
此参数可与 `balance_classes`（设为 `TRUE`）一起使用，以指定对数据进行上采样或下采样的程度。它要求我们按类词典顺序传递上采样或下采样比率。它是可选参数，如果未传递此参数，则采样因子将在模型训练期间自动计算。

### 3. `max_after_balance_size`
当 `balance_classes` 设为 `TRUE` 时，此参数用于控制训练数据的相对大小。值为 1.0 表示在消除类别不平衡后，将训练数据的大小设置为与原始训练集相同。

## 8.4.6 随机行选择（Bootstrap）
以下方法用于在 RF 中采样记录（*来源：* docs.h2o.ai）。

### 1. `sample_rate`
此参数指定为每个树随机选择的行的比例（无放回）。此参数取值介于 0.0 和 1.0 之间。默认值是 0.6320000291。此参数值越高，可能提高训练准确率。此参数可与 `col_sample_rate_per_tree` 一起使用以微调模型。

### 2. `sample_rate_per_class`
此参数是可选的，是 `sample_rate` 的替代项（二者其一可用）。对于集成模型中的每棵树，此参数可用于控制需要为每个类别无放回采样的行的比例。该参数期望传递一个列表，值介于 0 和 1 之间（行的相对比例）。这可用于在不使用 第 8.4.5 节 中描述的参数的情况下消除类别不平衡。

在使用 `sample_rate_per_class` 参数时，可忽略 `balance_classes` 和 `class_sampling_factors`。在 NPS 预测案例中，`sample_rate_per_class` 似乎比使用 `balance_classes` 和 `class_sampling_factors` 参数的任何组合效果更好。

## 8.4.7 控制生长
Brieman（2001）建议分类器，即随机森林中的决策树无需剪枝。然而，从实现角度来看，包提供了限制树生长的选项。以下参数可用于限制树的生长。

### 1. `min_split_improvement`
此参数可通过限制树的生长来减少过拟合。该参数值表示将一个节点拆分为两个所需的平方误差的最小变化。默认值设为 10^(−5)。此参数的最优值范围可在 10^(−10) 至 10^(−3) 之间。

### 2. `max_depth`
此参数用于减少过拟合。它用于控制树可生长的深度。此参数值越高，树越复杂。如果值设为 0，则表示树生长无限制（高度复杂的树）。默认值设为 20。

### 3. `min_rows`
此参数指定叶节点中必须存在的最小观测数。默认值设为 1，这可能导致过拟合问题。

## 8.4.8 随机森林（h2o）– 超参数
让我们创建一个列表并为每个超参数提供值：

![](img/page300-01.png)

## 8.4.9 随机森林（h2o）– 搜索标准
在上一节中，我们为三个参数创建了一个值列表 `hyper_params`，以便找到最佳组合值。`hyper_params` 中的值可通过采用 `strategy = Cartesian` 或 `strategy = RandomDiscrete` 进行搜索。

### 1. 指定搜索标准
指定 `search_criteria = list(strategy = "Cartesian")` 将应用 Cartesian 策略。

Cartesian 将搜索超参数的所有组合。然而，如果基础设施有限或超参数组合数量过大，则可能需要 RandomDiscrete。在 RandomDiscrete 策略的情况下，有三种随机搜索空间并指定何时停止搜索的方法：

### 2. 最大模型数
`search_criteria = list(strategy = "RandomDiscrete", max_runtime_secs = 600, max_models = 100, stopping_metric = "AUTO", stopping_tolerance = 0.00001, stopping_rounds = 5, seed = 123456)`

### 3. 最大时间
`search_criteria = list(strategy = "RandomDiscrete", max_models = 42, max_runtime_secs = 28800)`

### 4. 基于指标的提前停止
`search_criteria = list(strategy = "RandomDiscrete", stopping_metric = "AUC", stopping_tolerance = 0.00001, stopping_rounds = 5)`

我们可以在验证 logloss 连续五次评分事件中至少未改善 0.01% 时应用提前停止。

![](img/page301-01.png)

## 8.4.10 随机森林 – 网格搜索
在使用 `caret` 包在 第 6 章 和 第 7 章 中时，我们讨论了基础包中的 `expand.grid()` 方法。`expand.grid()` 方法有助于从所提供的向量，即 `hyper_params` 的所有组合创建数据框。h2o 中的类似方法是 `grid`。我们将使用 h2o 的 `grid` 方法并传递模型参数、搜索标准和超参数列表。也传递 `train` 和 `validate` 数据框。

默认情况下，`grid` 方法的 `balance_classes` 参数会对案例进行上采样。为了应用下采样，让我们计算下采样的比例。**表 8.5** 显示了 `train_h2f` 中 `NPS_CLASSIFICATION` 的案例数量。

**表 8.5** | `train_h2f` 中 `NPS_CLASSIFICATION` 的案例数量

| `NPS_CLASSIFICATION` || 计数 |
| --- | --- |
| Detractor || 59 |
| --- | --- |
| Passive || 573 |
| Promoter || 709 |

为了下采样并使观测值与 Detractor 类别成比例：
1. 将 Passive 下采样为 59/573 = 0.102（约）
2. 将 Promoter 下采样为 59/709 = 0.083（约）

因此 `grid` 方法中的 `class_sampling_factors` 可设为 `class_sampling_factors = c(1.0,0.102,0.083)`。数字是按照类别的词典顺序书写的。

另一个选项是在 `grid` 方法中设置 `sample_rate_per_class` 为：
`sample_rate_per_class = c(1.0,0.102,0.083)`。数字是按照类别的词典顺序书写的。

在尝试上述两种选项用于多类分类问题时，我们发现 `sample_rate_per_class` 与使用 `class_sampling_factors` 相比效果更好。

具有不同超参数组合的模型将在 `validation_frame` 和/或交叉验证框架（`nfolds`）上使用适用指标进行验证。

![](img/page302-01.png)

`h2o.grid` 还有 `parallelism` 作为参数，可用于在模型训练时定义并行处理。
1. 值为 1 表示顺序构建，是此参数的默认值。
2. 值为 0 表示自适应并行，即 h2o 包将决定如何利用并行处理。
3. 值大于 1 表示并行构建这么多模型。

![](img/page303-01.png)

我们将在构建 `gbm` 和 `xgboost` 模型时使用 `parallelism`。请注意，`grid` 方法还具有诸如 `calibrate_model` 和 `calibration_frame` 等参数。这些用于改进集成模型（`randomforest`、`gbm`、`xgboost`）关于概率估计（Platt 缩放）的性能。然而，目前它仅在二元分类问题中有效。

## 8.4.11 模型诊断
在本节中，我们将讨论模型诊断。我们可以使用以下指标之一对模型进行排序：

`r2`, `mean_per_class_accuracy`, `max_per_class_error`, `err`, `total_rows`, `rmse`, `accuracy`, `err_count`, `logloss`, `mse`, `mean_per_class_error`




对于多分类问题，`logloss` 是一个可靠的指标来评估模型的性能。`logloss` 评估模型的预测值（估计概率）与实际值之间的接近程度。

换句话说，`logloss` 试图衡量模型是否倾向于为正类分配较高的预测概率，例如 0.90，还是显示出较差的识别正类能力并分配较低的预测概率，例如 0.55？

`logloss` 可以取大于 0 的任意值。值为 0 表示模型已正确分配了 0% 或 100% 的概率。**表 8.6** 按 `logloss` 递增顺序显示了排序后的表格。

![](img/page303-02.png)

让我们从 **表 8.6** 中选择第一个模型进行进一步评估。

![](img/page303-03.png)

我们可以通过下面的代码片段查看 `rf_model` 对象的训练指标。

![](img/page303-04.png)![](img/page304-01.png)

请注意，`Detractor` 类的错误报告为 NA，因为混淆指标是在 `OOB` 观测值上生成的。我们在生成每棵树时都包含了所有 Detractors，因此 `Detractor` 类没有 `OOB` 观测值。这是在我们指定每个类别的采样率为 `c(1.0, 0.102, 0.083)` 时完成的。

命中率是一个表格，表示预测正确的次数与预测总次数的比率。

**1.** `K` = 1 表示如果我们只给模型一次机会为每个观测值估计正确的类别，模型在 64% 的时间内是正确的。这在某种程度上与模型准确率一样好。

**2.** `K` = 2 表示如果我们只给模型两次机会为每个观测值估计正确的类别，模型在 91% 的时间内是正确的。

**3.** `K` = 3 表示如果我们只给模型三次机会为每个观测值估计正确的类别，模型在 100% 的时间内是正确的（当然，这应该是当类别数只有三个时）。

我们可以以类似的方式查看交叉验证指标：

![](img/page304-02.png)![](img/page305-01.png)

### 8.4.12 | 模型预测

让我们使用该模型对测试集进行预测 **(表 8.7)**。

![](img/page305-02.png)![](img/page306-01.png)

让我们看看模型在测试框架上的表现。

![](img/page306-02.png)

构建 `NPS` 模型的目的是在客户中识别出 `Detractors`。错误率为 0.22，模型在正确预测 `Detractors` 方面似乎表现相当不错。我们可以使用一组微调后的参数并使用完整数据集，即 `filter_h2f` 来构建最终模型。

![](img/page306-03.png)![](img/page307-01.png)

模型的准确率为 65%。

### 8.4.13 | 保存模型

现在可以使用一组微调后的参数保存模型。

![](img/page307-02.png)

在创建 `h2o` 的新实例后，可以调用此模型对新客户进行评分。假设 `test_h2f` 是新的一组客户，我们可以使用保存的模型来预测这些新客户的类别。

![](img/page308-01.png)

## 8.5 | 梯度提升机 – 回归

在本节中，我们将讨论回归的梯度提升。为了理解 GBM 的基本概念，让我们先了解回归问题中提升的通用框架。

设 `X`、`Y` = (`x[1]`, `y[1]`)、(`x[2]`, `y[2]`)、(`x[3]`, `y[3]`)…(`x[m]`, `y[m]`) 表示包含 `m` 个元素的数据集。让我们定义拟合模型 `f(x)` 的目标以最小化平方损失。假设我们已经有了预先构建的回归模型 `f(x)`，但它在估计结果 (`Y`) 方面存在滞后。在改进现有模型 `f(x)` 的约束下，任务是向现有模型 `f(x)` 添加另一个模型 `h(x)`，希望它能精确估计 `Y`，即

![](img/page309-01.png)

上述 式 (8.1) 可以写成如下形式：

![](img/page309-02.png)

虽然我们可能无法构建完全拟合数据的模型，但我们可以构建一个近似拟合残差的模型 `h(x)`，即 ![](img/pageIn_ch8-03.png)。

`y[i]` − `f(x[i])` 是残差，新模型 `h(x)` 的作用是弥补现有模型 `f(x)` 的不足。如果新模型 `f(x)` + `h(x)` 仍然滞后，我们可以添加另一个模型来弥补不足。这就是提升框架背后的基本思想。

### 8.5.1 | GBM 背后的理论

梯度提升的名称源自 ‘梯度下降’ + ‘提升’。在本节中让我们了解梯度下降的工作原理。从 第 7 章 中，我们可以回忆起通用梯度下降的形式为 式 (8.3)。

![](img/page309-03.png)

与传统优化问题中可以使用损失函数的梯度轻松学习参数 `θ` 不同，在基于树的学习中，树结构的学习（当然使用梯度）将采用加性策略进行。

在提升框架中，目标是将模型拟合到数据 `X`、`Y` 以最小化平方损失。因此，我们可以将目标用损失函数表示，如 式 (8.4) 所示。

![](img/page309-04.png)

我们希望通过调整 `f(x)` 来最小化 ![](img/pageIn_ch8-04.png)。因此 `f(x)` 可以被视为一个参数，对 `f(x)` 求导将得到以下结果：

![](img/page309-05.png)

使用上述 式 (8.5)，残差可以写成梯度的负值，如 式 (8.6) 所示。

![](img/page309-06.png)

因此，提升模型的更新可以用梯度表示如下：

![](img/page309-07.png)

将 式 (8.3) 与 式 (8.7) 进行比较，我们可以得出结论，模型的更新可以使用梯度下降进行，其中 `α` 设为 1。`α` 值是学习率，也可以进行微调。因此，在梯度提升中，实际模型是使用梯度下降构建的，其中：

**1.** 将 `h(x)` 拟合到残差等价于将 `h(x)` 拟合到负梯度。

**2.** 基于残差更新 `f(x)` 等价于基于负梯度更新 `f(x)`。

因此，一般来说，我们可以将回归的梯度提升步骤写为：

• 从初始 ![](img/pageIn_ch8-05.png) 开始

– 直到收敛迭代：

• 计算负梯度 − `g(x[i])` = `y[i]` − `f(x[i])`

• 将模型 `h(x)` 拟合到负梯度 − `g(x[i])`

• `f(x)` = `f(x)` + `α` * `h(x)`

最终预测如 式 (8.8) 所示。

![](img/page310-01.png)

其中 `K` 是树的数量，`f^(k)` 是所有可能的树 (`CART`) 的集合。在上述解释中，我们保持 `K` = 1（仅学习一个树结构），因此在 `f(x)` 和 `h(x)` 的下标中省略了它。

平方误差损失函数的一个缺点是异常值会被严重惩罚，因此整体模型性能可能表现出高偏差。然而，使用梯度的好处是我们可以使用绝对损失或 Huber 损失等其他损失函数，它们对异常值更稳健。需要注意的关键点是，如 式 (8.9) 所示的目标函数公式保持不变，即

![](img/page310-02.png)



`Ω(f^k)` 可以被视为一个正则化参数。我们可以将学习率 `α` 视为其中一个正则化参数，生长树的数量，即 `K` 也是另一个正则化参数。可能存在多个正则化参数，它们将控制模型的过拟合，并在展示实现时进行讨论。

### 8.5.2 | 随机梯度提升
基于 Bagging 方法，Friedman（2001）提出在提升模型的每次迭代中，`h(x)` 应拟合在随机抽样且不放回的训练集子样本上。这一修改显著提高了梯度提升的准确性，被称为随机梯度提升。

## 8.6 | 梯度提升机 – 分类
让我们了解 GBM 在分类问题中的工作原理。在 NPS 问题中，我们需要学习类别 `y[i]`，即 Detractor（`y[1]`）、Passive（`y[2]`）、Promoter（`y[3]`），即多类分类。我们将有三个评分函数，即三个模型 `f[1]`、`f[2]`、`f[3]`，其中 `f1` 为 Detractor 分配分数，`f2` 为 Passive 分配分数，`f3` 为 Promoter 分配分数。这些分数将用于使用 `SoftMax` 函数计算概率，公式 (8.10)。

![](img/page310-03.png)

预测类别将是概率最高的那个。以下步骤用于为每个数据点定义损失函数：

Step 1: 基于数据，将标签 `y[i]` 转换为真实概率分布。`Yc` 例如，如果数据中的第二个观测值为 Promoter，则。`Y1 = 0`、`Y2 = 1`、`Y3 = 0` 我们可以将其写为真实概率 `T[p2] = (0,1,0)`。

Step 2: 计算预测概率分布 `Pc`，其中 `c = 1, 2, 3` 基于当前模型 `f[1]`、`f[2]`、`f[3]`。假设计算得到的概率为 `P1 = 0.60`、`P2 = 0.25`、`P3 = 0.15`。我们可以将其写为第二个观测值的计算概率 `C[p2] = (0.6, 0.25, 0.15)`。

Step 3: 计算真实概率分布与预测概率分布之间的差异。Kullback–Leibler 散度²（KL 散度）可用于计算差异。

KL 散度是衡量一个概率分布与另一个概率分布不同的程度的指标（Kullback and Leibler，1951）。KL 散度值为零表示两个分布相同。`C[pi]` 到 `T[pi]` 的 KL 散度可以表示为 `DKL`。KL 散度也可称为如果使用代替 `T[pi]` 所获得的信息增益。

分类 GBM 的目标将是最小化总体 KL 散度，³ 公式 (8.11)，以便计算得到的概率可用于正确分类。

![](img/page311-01.png)![](img/page311-02.png)

公式 (8.12) 中的目标可以通过调整模型来实现，即 `f[1]`、`f[2]`、`f[3]`，因此 `f[1]`、`f[2]`、`f[3]` 成为需要优化的参数。![](img/pageIn_ch8-06.png)是 GBM 中的正则化分量，其中 `K` 是每个模型 `f[c]` 中的树数。

### 8.6.1 | GBM – 回归 vs. 分类
回归与分类 GBM 之间的区别在于

**1.** 与回归中的一个模型 `f(x)` 不同，分类具有 `f1`、`f2`、`f3`（设备内反馈数据）。因此，存在一个需要优化的参数矩阵

如 **表 8.9** 所示，存在一个需要计算的梯度矩阵。

![](img/page311-03.png)![](img/page311-04.png)![](img/page312-01.png)

因此，一般而言，考虑到设备反馈数据，我们可以将分类的梯度提升步骤写为：

**2.** 从初始模型 `f1`、`f2`、`f3` 开始：

– 迭代直至收敛：

• 计算 Detractor 的负梯度 -
![](img/page312-02.png)
• 计算 Passive 的负梯度 -
![](img/page312-03.png)
• 计算 Promoter 的负梯度 -
![](img/page312-04.png)
• 将模型 `h[1]` 拟合到负梯度 - `g1`
• 将模型 `h[2]` 拟合到负梯度 - `g2`
• 将模型 `h[3]` 拟合到负梯度 - `g3`
• 更新 `f1 = f1 + α * h1`
• 更新 `f2 = f2 + α * h2`
• 更新 `f3 = f3 + α * h3`

## 8.7 | 使用 h2o 包的梯度提升机
`h2o` 包具有 `gbm` 方法，可直接调用以构建 GBM 模型。如同在 `randomForest` 模型中，这里我们也将使用 `grid` 方法来微调超参数。

### 8.7.1 | 随机子空间选择
控制 `gbm` 方法的参数如下（*来源：* docs.h2o.ai）：

**1.** `col_sample_rate` - 此参数指定随机选择的列的比例（不放回）。该参数的值介于 0.0 和 1.0 之间。此参数值越高，可能提高训练准确率。此选项有助于实现随机 GBM，参考‘随机梯度提升’（Friedman，2002）。

**2.** `col_sample_rate_per_tree` - 此参数指定随机选择的列的比例（不放回）。取值介于 0.0 和 1.0 之间。默认值是 1（为每棵树的生长选择所有列）。

**3.** `col_sample_rate_change_per_level` - 此参数与 `col_sample_rate_per_tree` 协同工作，用于随着树深度的增加而改变随机选择的列的比例。此参数的值可在 0 到 2 之间（默认为 1）。例如，假设 `col_sample_rate_change_per_level` 设置为 0.5，则
• 层级 1: `col_sample_rate_per_tree`
• 层级 2: `col_sample_rate_per_tree * 0.5`
• 层级 3: `col_sample_rate_per_tree * 0.5²`
• 层级 4: `col_sample_rate_per_tree * 0.5³`

### 8.7.2 | 类别不平衡
**1.** `balance_classes` - 此参数用于消除数据中的类别不平衡。默认值是 FALSE。如果设置为 TRUE，则使用上采样来消除类别不平衡。

**2.** `class_sampling_factors` - 此参数可与 `balance_classes` 一起使用，以指定对数据进行上采样或下采样的程度。它要求我们按类字典顺序传递上采样或下采样比率。它是可选参数，如果未传递此参数，则采样因子将在模型训练期间自动计算。

**3.** `max_after_balance_size` - 在 `balance_classes` 设置为 TRUE 时，此参数用于控制训练数据的相对大小。它可以取大于或小于 1.0 的值。1.0 的值意味着，在消除类别不平衡后，将训练数据的大小设置为与原始训练集相同。

### 8.7.3 | 随机行选择 (Bootstrap)
**1.** `sample_rate` - 此参数指定为每棵树随机选择的行的比例（不放回）。此参数取值介于 0.0 和 1.0 之间（默认值是 1）。此参数值越高，可能提高训练准确率。



`sample_rate_per_class`: 此参数是可选的，是 `sample_rate` 的替代项（两者任选其一）。对于集成模型中的每棵树，此参数可用于控制每类需要进行无放回抽样的行比例。该参数期望传入一个列表，其值介于 0 和 1 之间（行的相对比例）。此选项的范围为 0.0 至 1.0。请注意，此方法为无放回抽样（*来源:* docs.h20.ai）。
在使用 `sample_rate_per_class` 参数时，`balance_classes` 和 `class_sampling_factors` 可能会被忽略。在 NPS 预测案例中，`sample_rate_per_class` 似乎比使用 `balance_classes` 和 `class_sampling_factors` 参数的任何组合效果更好。

### 8.7.4 | 控制增长
以下是可用于控制树生长的参数（*来源:* docs.h2o.ai）：
1. `min_split_improvement` – 此参数可通过限制树的生长来减少过拟合。该参数的值表示将节点拆分为两个所需的平方误差的最小变化。默认值设为 `10^(-5)`。此参数的最佳值范围可在 `10^(-10)` 至 `10^(-3)` 之间。
2. `max_depth` – 这是另一个用于减少过拟合的参数。它用于控制树可生长的深度。该参数值越高，树越复杂。如果将值设为零，则表示树生长无限制（高度复杂的树）。默认值为 `5`。
3. `min_rows` – 此参数指定叶节点中必须存在的最小观测数。默认值为 `1`，可能导致过拟合问题。
4. `learn_rate` – 此参数取值介于 0 和 1 之间，用于指定学习率。
5. `learn_rate_annealing` – 此参数与 `learn_rate` 协同工作，用于在每棵树之后以固定因子降低 `learn_rate`。如果模型中有 `N` 棵树，则 GBM 将从 `learn_rate` 开始，最终达到 `learn_rate * learn_rate_annealing ^ N`。

### 8.7.5 | GBM – 创建数据集
让我们为训练目的创建数据集。
![](img/page314-01.png)
`train`、`test` 和 `validate` 数据框的维度如下：
![](img/page314-02.png)

### 8.7.6 | GBM (h2o) – 超参数
让我们创建一个网格空间来搜索最佳超参数。
![](img/page314-03.png)

### 8.7.7 | GBM (h2o) – 搜索准则
我们使用 `Cartesian` 或 `DiscreteRandom` 策略定义搜索准则。让我们实现 ‘`RandomDiscrete`’ 搜索准则。
![](img/page314-04.png)

### 8.7.8 | GBM – 网格搜索
我们将使用 `h2o` 的 `grid` 方法并传入模型参数、搜索准则、超参数列表。具有不同超参数组合的模型将在 `validation_frame` 和/或交叉验证框架 (`nfolds`) 上使用适用指标进行验证。我们在随机森林中用于微调超参数使用了 3 折交叉验证策略。让我们使用验证框架和并行模型构建来微调 `gbm` 模型。
![](img/page315-01.png)
在 `gbm` 方法中，`distribution` 参数默认设置为 AUTO，可根据响应列识别回归或分类任务。`h2o.grid` 还有 `parallelism` 参数，可用于在模型训练期间定义并行处理。
1. `1` 的值表示顺序构建，是此参数的默认值。
2. `0` 的值表示自适应并行，即 `h2o` 包将决定如何利用并行处理。
3. 大于 `1` 的值表示并行构建这么多模型。

### 8.7.9 | 模型诊断
使用以下指标之一对模型进行排序：
`r2`, `mean_per_class_accuracy`, `max_per_class_error`, `err`, `total_rows`, `rmse`, `accuracy`, `err_count`, `logloss`, `mse`, `mean_per_class_error`
对于多类分类，`logloss` 是评估模型性能的可靠指标。`Logloss` 评估模型预测值（估计概率）与实际值的接近程度。
例如，模型是否对正类分配了较高的预测值如 `0.90`，还是显示出预测正类能力较差并分配较低的预测概率如 `0.20`（Anon, 2016）？
`Logloss` 可取大于 `0` 的任意值。值为 `0` 表示模型已正确分配了 `0%` 或 `100%` 的概率。
![](img/page316-01.png)![](img/page316-02.png)
从 **表 8.10** 中选择第一个模型进行进一步评估。
![](img/page316-03.png)
我们可以如下查看训练指标。
![](img/page316-04.png)![](img/page317-01.png)
命中率是一个表格，表示预测正确的次数占预测总次数的比例（Anon, 2016 © H2O.ai）。
1. `K = 1` 表示如果我们仅给模型一次机会为每个观测估计正确类别，模型 79% 的时间是正确的。这在某种程度上与模型准确率一样好。
2. `K = 2` 表示如果我们仅给模型两次机会为每个观测估计正确类别，模型 96% 的时间是正确的。
3. `K = 3` 表示如果我们仅给模型三次机会为每个观测估计正确类别，模型 100% 的时间是正确的（当然，当类别数只有三个时应该是这样）。
我们可以以类似方式查看验证指标：
![](img/page317-02.png)

### 8.7.10 | 模型预测
让我们使用模型对测试集进行预测。结果显示在 **表 8.11** 中。
![](img/page318-01.png)![](img/page318-02.png)
让我们查看模型在测试框架上的性能。
![](img/page318-03.png)

### 8.7.11 | GBM (h2o) – 结果讨论
一次微调所有参数可能会增加微调模型所需的时间。以下是执行的参数微调步骤。在后续迭代中微调参数时，保持之前迭代中获得的值固定。

#### 迭代 0：
使用数据分割 `(0.60,0.25,0.15)`，模型使用默认参数构建，但在调整 `sample_rate_per_class = c(1.0,0.102,0.083)` 后。模型的性能报告在 **表 8.12** 中。
![](img/page319-01.png)

#### 迭代 1：微调 ntree、max_depth 和 min_rows
1. `ntree = seq(30,100,10)`
2. `max_depth = seq(2,8,2)`
3. `min_rows = c(1,5,10,15)`
对于样本分割 `(0.60,0.25,0.15)` 获得的值为 `(50,6,5)`。模型性能报告在 **表 8.13** 中。
![](img/page319-02.png)

#### 迭代 2：
1. `col_sample_rate = c(0.6,0.8,0.9,1.0)`
2. `min_split_improvement = c(0,0.01,0.001,0.0001,0.00001)`
对于样本分割 `(0.60,0.25,0.15)` 获得的值为 `(1.0,0.00001)`，即默认值。模型性能报告在 **表 8.14** 中。
![](img/page319-03.png)

#### 迭代 3：
1. `learn_rate = c(0.1,0.3,0.5,1)`
此参数没有帮助改进模型。模型性能报告在 **表 8.15** 中。
![](img/page320-01.png)

#### 迭代 4：微调 ntree、max_depth 和 min_rows
1. `ntrees = seq(44,54,2)`
2. `max_depth = seq(2,8,2)`
3. `min_rows = c(1,5,10,15)`
对于样本分割 `(0.60,0.25,0.15)` 获得的值为 `(50,6,5)`。模型性能报告在 **表 8.16** 中。
![](img/page320-02.png)



由 表 8.13 可观察到 `ntrees`、`max_depth` 和 `min_rows` 导致 `logloss` 显著改善。尽管 `gbm` 中还有其他感兴趣的参数，但它们似乎并不能改善 `NPS` 问题中的 `logloss`。

构建 `NPS` 模型的目的是在客户中识别出 `Detractors`。错误率为 0.40，该模型在正确预测 `Detractors` 方面似乎不如 `Random Forest` 模型。然而，在测试集上整体准确率为 71% 的情况下，`GBM` 比 `Random Forest` 模型更好。

我们可以利用一组微调后的参数并使用完整数据集，即 `filter_h2f`，来构建最终模型。

### 8.7.12 最终 GBM 模型

最终模型使用数据划分 (0.60,0.25,0.15) 并采用 `model_iter4` 参数构建，得出 表 8.16：

![](img/page321-01.png)

模型的准确率为 82%。

### 8.7.13 保存模型

模型现在可以用一组微调后的参数保存。

![](img/page321-02.png)

创建 `h2o` 的新实例后，可以调用此模型对新客户进行评分。假设 `test_h2f` 是新的一组客户，我们可以使用保存的模型来预测这些新客户的类别。参考 第 8.4.13 节 以了解保存的模型在对新案例进行评分时的使用方法。

## 8.8 使用 h2o 包的 XGBoost

`XGBoost` 是另一种流行的提升技术，它进一步基于梯度提升机 (`GBM`) 框架构建，并且是最佳的 `GBM` 框架之一。`XGBoost` 的目标函数使用损失函数的泰勒展开式推导而来。⁴ `XGBoost` 也更强调正则化参数。

`XGBoost` 中的参数可分为通用参数、助推器参数和任务参数。

### 8.8.1 使用 h2o 的 XGBoost – 通用参数

通用参数与用于开发模型的 `booster` 相关。这些通常是树模型或线性模型：

`booster`: 可以是 `gbtree`、`gblinear` 或 `dart`；`gbtree` 和 `dart` 使用基于树的模型，而 `gblinear` 使用线性函数。默认值为 `gbtree`。

根据所选的 `booster`，其他助推器参数变得适用。`h2o` `XGBoost` 方法还能高效处理其他通用参数。

### 8.8.2 使用 H2O 的 XGBoost – 学习任务参数

在 `h2o` 中，`distribution`（即损失函数）参数决定了学习场景。选项包括 `AUTO`、`Bernoulli`、`multinomial`、`Gaussian`、`Poisson`、`gamma` 或 `Tweedie`（Anon, 2016）根据 doc.h2o.ai：

1. 对于 `Bernoulli` 分布，因变量列必须是二分类的。
2. 对于 `multinomial` 分布，因变量列必须是分类的。
3. 对于 `poisson` 分布，因变量列必须是数值型的。
4. 对于 `Tweedie` 分布，因变量列必须是数值型的。
5. 对于 `gaussian` 分布，因变量列必须是数值型的。
6. 对于 `gamma` 分布，因变量列必须是数值型的。

根据 docs.h2o.ai 网站，“默认执行 `AUTO` 分布。在这种情况下，算法将根据因变量列类型猜测模型类型。如果因变量列类型为数值型，`AUTO` 默认采用 ‘`gaussian`’；如果为分类型，`AUTO` 则根据响应类别的数量默认采用 `binomial` 或 `multinomial`（Anon, 2016）”。

### 8.8.3 使用 h2o 的 XGBoost – 助推器参数

这取决于所选的 `booster`。在 `h2o.xgboost` 中，对于 `booster = gbtree`，定义了以下助推器参数：

#### 随机子空间选择

以下方法可用于子空间选择（*Source:* docs.h2o.ai）：

1. “`col_sample_rate` (`colsample_bylevel`) – 该参数指定为每棵树随机选择的列的比例（不放回）。默认值是 1，但可以取 0.0 到 1.0 之间的任意值。该参数值越高，可能提高训练准确率。
2. `col_sample_rate_per_tree` (`colsample_by_tree`) – 该参数指定为每棵树随机选择的列的比例（不放回）。取值范围在 0.0 到 1.0 之间。默认值是 1，表示为每棵树的生长选择所有列。该参数与 `col_sample_rate` 协同工作。因此设置 `col_sample_rate = 0.7` 且 `col_sample_rate_per_tree = 0.7` 将导致在任何给定节点分裂时仅考虑 49% 的列。

#### 随机行选择（Bootstrap）

`sample_rate` (`subsample`) – 根据 docs.h2o.ai，该参数，“指定训练实例的行采样比例（*x*-axis）。请注意，此方法为不放回抽样。例如，将此值设置为 0.5 会使 `XGBoost` 随机收集一半的数据实例来生长树。默认值是 1，范围为 0.0 到 1.0。值越高可能提高训练准确率。当对列或行进行采样时，测试准确率会提高。详情请参阅‘Stochastic Gradient Boosting’（Friedman, 1999）”。

#### 类别不平衡

`max_abs_leafnode_pred` (`max_delta_step`): 根据 docs.h2o.ai，该参数，“指定每棵树权重估计中允许的最大增量步长。默认值是 0。将此值设置为 0 表示无约束。将此值设置为大于 0 可以使更新步骤更保守，并通过限制叶节点预测的绝对值来减少过拟合。此选项在类别极度不平衡时也有帮助。将值设置为 1-10 可能会有助于控制更新”。

#### 其他助推器参数

可用于控制树生长的参数（*Source:* docs. h2o.ai）。

1. `min_split_improvement` (`gamma`) – 该参数可通过限制树的生长来减少过拟合。该参数的值表示将节点分裂为两个所需的平方误差的最小变化。该参数的最佳值范围可在 10^(−10) 到 10^(−3) 之间。
2. `max_depth` – 这是另一个用于减少过拟合的参数。它用于控制树的生长深度。该参数值越高，树越复杂。如果值设为 0，则表示树生长无限制（高度复杂的树）。默认设置为 5。
3. `min_rows` (`min_child_weight`) – 指定叶节点的最小观测数，默认为 1。
4. `learn_rate` (`eta`) – 指定用于收缩特征权重的学习率。在每次提升步骤后收缩特征权重会使提升过程更保守并防止过拟合。`learn_rate` 的范围在 0.0 到 1.0 之间。该值默认为 0.3。
5. `reg_lambda` (`lambda`) – 权重上的 L2 正则化项，默认值为 1。增加该值会使模型更保守。
6. `reg_alpha` (`alpha`) – 权重上的 L1 正则化项，默认值为 0。增加该值会使模型更保守。

### 8.8.4 使用 h2o 的 XGBoost – 创建数据集

让我们创建用于训练的数据集。我们还将使用 `columns_weight` 参数来微调 `XGBoost` 模型。为此，我们将在 `filter_h2f` 数据框中创建一个 `WEIGHT` 列。

![](img/page323-01.png)![](img/page324-01.png)

```
sample_rate_per_class = c(Detractor = 1.0,passive = 0.102,Promoter 0.083),
```

![](img/page324-02.png)

`train`、`test` 和 `validate` 数据框的维度如下：

![](img/page324-03.png)

### 8.8.5 使用 h2o 的 XGBoost – 超参数

`h2o` 包具有 `XGBoost` 方法，可直接调用以构建 `XGBoost` 模型。如同在 `randomForest` 和 `gbm` 模型中一样，这里我们也将使用 `grid` 方法来微调超参数。让我们创建一个网格空间来搜索最佳超参数。





![](img/page324-04.png)

## 8.8.6 | 使用 h2o 的 XGBoost – 搜索标准

我们使用 `Cartesian` 或 `DiscreteRandom` 策略定义搜索标准。让我们按照 `randomForest` 中指定的方式实现搜索标准（第 8.4.9 节）。

![](img/page324-05.png)

## 8.8.7 | XGBoost – 网格搜索

我们将使用 `h2o` 的 `grid` 方法并传入模型参数、搜索标准、超参数列表。我们将使用为 `gbm` 创建的验证帧来训练和调优 `XGBoost` 模型。

![](img/page325-01.png)

## 8.8.8 | 模型诊断

使用以下其中一个指标对模型进行排序：

`r2`, `mean_per_class_accuracy`, `max_per_class_error`, `err`, `total_rows`, `rmse`, `accuracy`, `err_count`, `logloss`, `mse`, `mean_per_class_error`

正如 第 8.4.11 节 中所讨论的，对于多分类分类，`logloss` 是评估模型性能的可靠指标。`Logloss` 可以取大于 0 的任意值。值为 0 表示模型已正确分配了 0% 或 100% 的概率。

![](img/page325-02.png)![](img/page325-03.png)![](img/page326-01.png)

选择 **表 8.17** 中的第一个模型进行进一步评估。

![](img/page326-02.png)

我们可以如下查看训练指标。

![](img/page326-03.png)

我们可以以类似的方式查看验证指标：

![](img/page327-01.png)

## 8.8.9 | 模型预测

让我们使用该模型对测试集进行预测 **表 8.18**。

![](img/page327-02.png)![](img/page327-03.png)

让我们查看模型在测试帧上的性能。

![](img/page328-01.png)

## 8.8.10 | 使用 h2o 的 XGBoost – 结果讨论

一次微调所有参数可能会增加微调模型所需的时间。以下是执行的参数微调步骤。在后续迭代中微调参数时，保持之前迭代中获得的值固定。

### Iteration 0:

在数据拆分为 (0.55,0.25,0.20) 的情况下，模型使用默认参数构建，但在调整列权重后。模型的性能报告在 **表 8.19** 中。

### Iteration 1: Fine-tuning `ntree`, `min_rows` and `col_sample_rate`.

迭代 1：微调 `ntree`、`min_rows` 和 `col_sample_rate`。

1. `ntrees = seq(10,100,10)`
2. `min_rows = seq(1,10,1)`
3. `col_sample_rate = seq(0.1,1.0,0.1)`

样本拆分 (0.55,0.25,0.20) 报告 (30,2,0.1) 为最佳组合。**表 8.20** 包含该拆分的模型性能。

![](img/page328-02.png)![](img/page329-01.png)

### Iteration 2:

1. `max_depth = seq(1,10,1)`
2. `learn_rate = c(0.1,0.3,0.5,1)` #eta
3. `sample_rate = c(0.6,0.8,0.9,1.0)` #row sampling
4. `min_split_improvement = c(0,0.01,0.001,0.0001)` #gamma

样本拆分 (0.55,0.25,0.20) 报告 (7,0.3,1.0,0.001) 为最佳组合。模型性能报告在 **表 8.21** 中。

### Iteration 3:

1. `reg_lambda = c(0.6,0.8,0.9,1.0)`
2. `reg_alpha = c(0,0.1,0.2,0.3,0.5)`
3. `max_abs_leafnode_pred = c(0,1,5,10,15)`

默认参数 (1.0,0,1) 被报告为最佳参数。单独或组合使用，这些参数均未帮助在数据拆分为 (0.55,0.25,0.20) 时改善模型。模型性能报告在 **表 8.22** 中。

构建 NPS 模型的目的是在客户中识别贬损者。在 **表 8.22** 中，误差为 0.2857，模型在正确预测贬损者方面的表现似乎不如随机森林或 `gbm` 模型。然而，在整体准确率为 70% 的情况下，`XGBoost` 比随机森林更好。

![](img/page329-02.png)![](img/page329-03.png)

请注意

1. 报告的参数是使 `logloss` 改善最大的参数。
2. 尽管在 `model_iter0` 中未进行超参数微调，但它与基础模型并不相似。我们在任何迭代中开发模型之前就调整了 `weights_column`。

微调 `XGBoost` 模型耗时且需要在获得接近最优模型之前进行多次迭代。可以观察到 `ntrees`、`min_rows` 和 `col_sample_rate` 会显著改善 `logloss`。尽管 `XGBoost` 中还有其他感兴趣的参数，但它们似乎并不能改善 NPS 问题中的 `logloss`。

根据早期迭代获得的结果，最终模型使用以下参数的网格搜索构建：

1. `ntrees = seq(20,40,5)`
2. `max_depth = seq(4,8,1)`
3. `min_rows = seq(1,4,1)`
4. `col_sample_rate = seq(0.05,0.15,0.05)`
5. `min_split_improvement = c(0.01,0.001,0.0001)`

最佳组合为 (30,7,2,0.1,0.001)。

## 8.8.11 | 最终 XGBoost 模型

我们可以使用一组微调后的参数并使用完整数据集，即 `filter_h2f`，构建最终模型。

![](img/page330-01.png)![](img/page331-01.png)

最终 `XGBoost` 模型的准确率为 74%。

## 8.8.12 | 保存模型

模型现在可以使用一组微调后的参数保存。

![](img/page331-02.png)

## Summary

本章我们学习了

1. 通过为随机森林算法定义成本函数进行模型构建。
2. 梯度提升机的模型构建和微调。
3. 极端梯度提升 (`XGBoost`) 的模型构建和微调。
4. 偏差与方差权衡以及如何使用装袋和提升模型中的正则化避免模型过拟合。
5. 处理多分类分类模型中的类别不平衡问题。

## Exercise

### Answer Questions 1 to 8 using the Earnings Manipulation Dataset.⁵

使用盈余操纵数据集回答问题 1 至 8。⁵

MCA Technology Solutions Private Limited 成立于 2015 年于班加罗尔，目标是将分析和技术与业务整合。MCA Technology Solutions 帮助其客户在客户情报、预测、优化、风险评估、网络分析、文本挖掘和云解决方案等领域。MCA Technology Solutions 的风险评估部门专注于欺诈检测和信用评分等问题。MCA Technology Solutions 班加罗尔的董事 Sachin Kumar 被其客户之一的商业银行接洽，协助他们检测银行客户中的盈余操纵者。该银行为中小企业提供商业贷款，贷款价值从 1,000 万印度卢比到 5 亿印度卢比不等（1 美元 = 66.82 印度卢比，2016 年 8 月 16 日）。该银行怀疑其客户可能参与盈余操纵以增加获得贷款的机会。

MCA Technologies 的首席数据科学家 Saurabh Rishi 被分配了开发预测盈余操纵用例的任务。他知道诸如 *Beneish* 模型等用于预测盈余操纵的模型；然而，他不确定其性能，尤其是在印度背景下。Saurabh 决定使用从印度经济监测中心（CMIE）维护的 Prowess 数据库下载的数据开发自己的盈余操纵预测模型。Daniel 从印度证券交易委员会（SEBI）和 Lexis Nexis 数据库获得了有关盈余操纵者的信息。收集了 220 家公司的数据来开发模型。

数据可在文件 `EarningsManipulation220.csv` 中获得。列的描述在 **表 8.23** 中给出。在此表中

• `netPPE` 为净不动产、厂房和设备。不动产、厂房和设备是企业为经营业务而购买的所有建筑物、土地、家具和其他有形资本的价值。




下标 (`t`) 表示当年财务报表中的数值，下标 (`t` − 1) 表示上年财务报表中的数值。

![](img/page332-01.png)![](img/page333-01.png)

### 1. 数据集中操纵者与非操纵者的案例各有多少？绘制条形图来展示。

### 2. 创建 80:20 的划分，并找出测试数据中正例的数量。

### 3. 操纵者的案例数相比非操纵者非常少。使用 `caret` 包并使用过采样技术构建模型。
- 随机森林
- 梯度提升机
使用 ROC AUC 分数作为性能指标比较模型的准确率。

### 4. 操纵者的案例数相比非操纵者非常少。使用下采样技术创建平衡数据集。使用 `caret` 包构建以下模型：
- 随机森林
- 梯度提升机
使用 ROC AUC 分数作为性能指标比较模型的准确率。

### 5. 操纵者的案例数相比非操纵者非常少。使用 `SMOTE` 采样技术创建平衡数据集。使用 `caret` 包构建以下模型：
- 随机森林
- 梯度提升机
使用 ROC AUC 分数作为性能指标比较模型的准确率。

### 6. 操纵者的案例数相比非操纵者非常少。使用 `rose` 采样技术创建平衡数据集。使用 `caret` 包构建以下模型：
- 随机森林
- 梯度提升机
使用 ROC AUC 分数作为性能指标比较模型的准确率。

### 7. 比较使用过采样、下采样、`SMOTE` 和 `rose` 技术的结果。报告所有模型中最好的模型。哪种采样技术在此数据集上给出最佳结果。

### 8. 使用随机森林和梯度提升机报告最佳模型的特征重要性。解释结果。

### 参考文献

**1.** Anon (2016), *“mtries 描述”*, 网页地址：[`docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/al-go-params/mtries.html`](http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/al-go-params/mtries.html), 访问于 01 February 2021.

**2.** Anon (2016), *“性能与预测”*, 网页地址：[`docs.h2o.ai/h2o/latest-stable/h2o-docs/perfor-mance-and-prediction.html`](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/perfor-mance-and-prediction.html), 访问于 01 January 2021.

**3.** Anon (2016), *“性能与预测”*, 网页地址：[`h2o-release.s3.amazonaws.com/h2o/rel-yau/6/docs-website/h2o-docs/performance-and-prediction.html`](http://h2o-release.s3.amazonaws.com/h2o/rel-yau/6/docs-website/h2o-docs/performance-and-prediction.html), 访问于 01 January 2021.

**4.** Anon (2016), *“分布”*, 网页地址：[`docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/algo-params/distribution.html`](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/algo-params/distribution.html), 访问于 01 February 2021.

**5.** Anon (2016),*”GBM”*, 网页地址：[`h2o-release.s3.amazonaws.com/h2o/rel-turing/1/docs-website/h2o-docs/welcome.html`](https://h2o-release.s3.amazonaws.com/h2o/rel-turing/1/docs-website/h2o-docs/welcome.html), 访问于 01 February 2021.

**6.** Anon (2019), *“分布”*, 网页地址 [`h2o-re-lease.s3.amazonaws.com/h2o/rel-yau/3/index.html`](https://h2o-re-lease.s3.amazonaws.com/h2o/rel-yau/3/index.html), 访问于 01 February 2021.

**7.** Anon (2018), *“SMOTE – 用于不平衡分类问题的 SMOTE 算法”*, 网页地址：[`www.rdocumentation.org/packages/DMwR/versions/0.4.1/top-ics/SMOTE`](https://www.rdocumentation.org/packages/DMwR/versions/0.4.1/top-ics/SMOTE), 访问于 01 February 2021.

**8.** Anon (2020), *“在 R 中使用 SMOTE 创建 1:1 平衡数据集而不修改多数类的观测值”*, 网页地址：[`stackoverflow.com/questions/62871492/create-balanced-dataset-11-us-ing-smote-without-modifying-the-observations-of-th`](https://stackoverflow.com/questions/62871492/create-balanced-dataset-11-us-ing-smote-without-modifying-the-observations-of-th), 访问于 01 February 2021.

**9.** Anon (2021), *“将数据集拆分为训练/测试/验证”*, 查看日期 2021, 网页地址：[`h2o-re-lease.s3.amazonaws.com/h2o/rel-vajda/1/docs-website/h2o-docs/data-munging/splitting-datasets.html`](https://h2o-re-lease.s3.amazonaws.com/h2o/rel-vajda/1/docs-website/h2o-docs/data-munging/splitting-datasets.html), 访问于 01 February 2021.

**10.** Anon (2020), *“隔离森林”*, 网页地址：[`docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/if.html`](http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/if.html), 访问于 01 February 2021.

**11.** Anon (2020), *“性能与预测”*, 网页地址：[`docs.h2o.ai/h2o/latest-stable/h2o-docs/performance-and-prediction.html`](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/performance-and-prediction.html),, 访问于 01 February 2021.

**12.** Anon (2021), We are improving the predictions of training data but is the procedure also | Course Hero, 网页地址：[`www.coursehero.com/file/puj8l6/What-is-the-process-of-dividing-each-feature-by-its-range-called-fea-ture`](https://www.coursehero.com/file/puj8l6/What-is-the-process-of-dividing-each-feature-by-its-range-called-fea-ture)/, 访问于 01 February 2021.

**13.** Beneish M D (1999), “盈余操纵的检测”, *Financial Analyst Journal*, **55**(5), 24–36.

**14.** Bernard S, Heutte L, Adam S (2010), “随机森林中强度与相关性的研究”, *International Conference on Intelligent Computing*, Aug 2010, Changsha, China. pp.186–191, ff10.1007/978-3-642-14831-6\_25ff.ffhal-00598466f.

**15.** Breiman L (1996), “Bagging predictors,” *Machine Learning*, 24 (2), 123–140.

**16.** Breiman L (2001), “随机森林”, *Machine Learning*, **45** (1), 5–32.

**17.** Chawla N V, Bower K W, Hall L O and Kegelmeyer W P (2002), “SMOTE：合成少数类过采样技术”, *Journal of Artificial Intelligence Research*, **16**, 321–357.

**18.** Kumar U D, Syed T A I and Ganeshan (2016), “使用机器学习算法预测印度公司的盈余操纵”, *Harvard Business Publishing*, 可获取于 [`hbsp.harvard.edu/product/IMB577-PDF-ENG?Ntt=Earnings%20manipulation`](https://hbsp.harvard.edu/product/IMB577-PDF-ENG?Ntt=Earnings%20manipulation), 访问于 04 August 2021.

**19.** Friedman J H (2001), *“贪婪函数逼近：梯度提升机”*, Stanford University Report, 网页地址：[`statweb.stanford.edu/~jhf/ftp/trebst.pdf`](https://statweb.stanford.edu/~jhf/ftp/trebst.pdf), 访问于 01 February 2021.

**20.** Friedman J H (2002), “随机梯度提升”, *Computational Statistics and Data Analysis*, **38**(4), 367–378.

**21.** Kullback S and Leibler R A (1951), “关于信息与充分性”, *Annals of Mathematical Statistics*, **22** (1), 79–86.

**22.** LeDell L (2020), *“`h2o.splitFrame`”*, 网页地址：[`www.rdocumentation.org/packages/h2o/ver-sions/3.32.0.1/topics/h2o.splitFrame`](https://www.rdocumentation.org/packages/h2o/ver-sions/3.32.0.1/topics/h2o.splitFrame), 访问于 01 February 2021.

**23.** Li C (2018), *“梯度提升的温和介绍”*, 网页地址：[`www.ccs.neu.edu/home/vip/teach/MLcourse/4\_boosting/slides/gradient\_boosting.pdf`](https://www.ccs.neu.edu/home/vip/teach/MLcourse/4_boosting/slides/gradient_boosting.pdf), 访问于 01 February 2021.

**24.** D Li, W Li, X Wang, C T Nguyen and S Lu (2020), “基于深度神经网络的加密互联网流量中的应用轨迹识别”, *Computer Networks*, **179**, 网页地址：[`doi.org/10.1016/jxomnet.2020.107372`](https://doi.org/10.1016/jxomnet.2020.107372), 访问于 01 February 2021.




## 参考文献
**25.** Lunardon N, Menardi G and Torelli N (2014), “ROSE：用于二元不平衡学习的包” *R Journal*, **6**, 82–92.

**26.** Menardi G and Torelli N (2014), “使用不平衡数据训练和评估分类规则”, *Data Mining and Knowledge Discovery*, **28**, 92–122.

**27.** Torgo L (2010), *“使用 R 进行数据挖掘：案例学习”*, CRC Press., Florida

**28.** Torgo, Luis & Ribeiro, Rita & Pfahringer, Bernhard & Branco, Paula. (2013), “回归的 SMOTE”, 8154. 378–389. 10.1007/978-3-642-40669-0\_33.

**29.** Xu Y, Wu C, Zheng K, Niu X and Yang Y (2017), “模糊合成少数类过采样技术：基于模糊集理论的不平衡数据集中 Android 恶意软件检测的过采样”, *International Journal of Distributed Sensor Networks*, **13**(4), 网址: [`doi.org/10.1177/1550147717703116`](https://doi.org/10.1177/1550147717703116), 于 2021 年 2 月 1 日访问.

**30.** Yang F, Lu W, Luo L and Li T (2012), “基于边际优化的随机森林剪枝”, *Neurocomputing*, **94**, 54–63.

---

## 脚注
¹[`www.stat.berkeley.edu/~breiman/randomforest2001.pdf`](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)

²[`www.chengli.io/tutorials/gradient\_boosting.pdf`](http://www.chengli.io/tutorials/gradient_boosting.pdf)

³来源: [`www.chengli.io/tutorials/gradient\_boosting.pdf`](http://www.chengli.io/tutorials/gradient_boosting.pdf)

⁴来源: [`xgboost.readthedocs.io/en/latest/tutorials/model.html`](https://xgboost.readthedocs.io/en/latest/tutorials/model.html)

⁵*来源:* Kumar U D, Syed T A I and Ganeshan (2016), “Predicting Earnings Manipulations by Indian Firms Using Machine Learning Algorithms”, *Harvard Business Publishing*, 可在 [`hbsp.harvard.edu/product/IMB577-PDF-EN-G?Ntt=Earnings%20manipulation`](https://hbsp.harvard.edu/product/IMB577-PDF-EN-G?Ntt=Earnings%20manipulation) 获取, 于 2021 年 8 月 4 日访问.

# 文本分析

## 9

*当我们的错误认知得到纠正时，痛苦也随之结束。*

—Adi Shankara

### 学习目标

阅读本章后，您将能够：

• 了解文本分析的重要性。
• 了解处理文本数据相关的挑战。
• 了解正则表达式及其在文本数据预处理中的用途。
• 学习准备文本数据的各种预处理步骤。
• 学习开发文档词矩阵，该矩阵可用于情感分类。
• 学习创建包含数值特征和非结构化文本数据的混合数据集用于建模目的。
• 了解主题建模并将其应用于文本数据。

## 9.1 | 概述

在当今世界，文本数据是信息的最大来源之一，它是非结构化的——即数据不以矩阵形式存在。从产品评论或反馈中寻找客户情感，或从社交媒体数据中提取意见是文本分析的几个例子。我们迄今为止学习的技术要求数据以结构化格式（矩阵形式）可用。一旦文本数据被清理和准备好，迄今为止探索的算法例如回归、分类或聚类就可以应用于文本数据（Pradhan and Kumar, 2019）。文本数据上的模型示例如下：

**1.** 从新闻文章预测股价走势是回归的一个例子，其特征包括对一家公司的正面和负面情感。

**2.** 从评论评论中将客户情感分类为正面和负面是使用文本数据的分类的一个例子。

在本章中，我们将使用关于 COVID 大流行的 Twitter 数据集来展示基本的文本数据可视化并构建一个分类模型来分类情感。我们将为本章使用 R 版本 4.0.3。

## 9.2 | 数据抓取

在本节中，我们将讨论从 Twitter 抓取数据的过程。在抓取数据之前，我们需要在 Twitter 上设置我们的个人资料。以下步骤可用于从 Twitter 抓取数据。

**1.** 在 [`twitter.com/signup`](http://twitter.com/signup) 上创建个人资料。还请在设置 Twitter 个人资料时提供您的手机号码 **(Figure 9.1)。**

**2.** 创建个人资料后，使用凭据登录 [`developer.twitter.com/en/apps`](https://developer.twitter.com/en/apps)。点击“create an app”图标并按照步骤获取开发者访问权限 **(Figure 9.2)。**

填写详细信息后，您将在收件箱中收到一封电子邮件验证邮件。

![](img/page338-01.png)![](img/page338-02.png)![](img/page339-01.png)![](img/page339-02.png)

**3.** 点击链接，它会要求您提供一个应用名称（提供任何可用的名称）。我们已决定使用“`tis_tweet`”，如 **Figure 9.3** 所示。

**4.** API Key (`oauth_consumer_key`) 和 API secret (oauth consumer secret) 将在‘app name’成功创建后生成。保存它们，因为我们将需要使用它们从 R 平台连接到 Twitter。API key 和 secret —— 将其视为用户名和密码，分别代表您在进行 API 请求时 Twitter 开发者应用 (*来源:* developer.twitter.com)。

**5.** 如 **Figure 9.4** 所示，点击 ‘Generate/ReGenerate’ Access token and secret。Access token (`oauth_token`) 和 Access secret (`oauth_token_secret`) 将被生成。保存它们，因为我们将需要使用它们从 R 平台连接到 Twitter。Access token 和 access token secret 是用于验证 OAuth 1.0a API 请求的用户特定凭据 (*来源:* developer.twitter.com)。

我们已准备好进行数据抓取；然而，在抓取 Twitter 数据并进行进一步分析之前，我们将先介绍正则表达式作为一种语言。

## 9.3 | 正则表达式

处理非结构化数据需要额外的预处理将其转换为结构化格式。这涉及大量字符操作和模式匹配，以保留有用的文本并删除没有有用信息的词。Regex（正则表达式）是一种专门的语言，许多编程语言支持其在文本数据中进行模式匹配的使用。我们将使用这种语言来指定用于在数据中进行字符串匹配的规则，并进一步以各种方式拆分数据。R 中大多数文本处理包如 `stringr` 和 `stringi` 支持使用 **正则表达式**。来自 base R 的 `gsub()` 和 `grep()` 包也支持使用 regex 进行模式匹配。高级包如 `tidytext` 通过提供自己的函数简化了模式匹配的工作。这些函数内部使用 regex。

**正则表达式** 是一种专门的语言，在文本信息的数据预处理阶段发挥着重要作用。

### 9.3.1 匹配字符

在本节中，我们将讨论用于匹配字符和词的函数。让我们看一个下面所示的简单示例文本：

![](img/page340-01.png)

我们将使用 `gsub()` 函数搜索和替换文本中所有匹配的模式。让我们找到词‘Take’并将其替换为‘We should take’。

![](img/page340-02.png)

匹配和替换简单词很直接但区分大小写。Regex 提供了某些元字符，它们本身不匹配但提供了一种在文本中搜索模式的手段。这些元字符是 . ∧ $ \* + ? { } \[ \] \\ | ( )。让我们在下一节中了解这些元字符的使用。

#### 元字符：方括号 ‘[‘ 和 ‘]’




‘[‘和’]’用于指定一组字符，称为字符类，我们希望匹配该字符类。字符集可以单独列出或作为范围。`\[abc\]`或`\[a-c\]`将尝试匹配字符‘a’、‘b’或‘c’中的任意一个。要匹配从 a 到 z 的任意字符，我们可以写`\[a-z\]`。大多数元字符在字符类内部不活跃。因此`\[xy\\$z\]`将匹配‘x’、‘y, ‘z’或‘$’（尽管‘\\’和‘$’本身是元字符）。然而，∧ - \]在字符类内部也是特殊的。要在文本中查找‘\]’，将其放在列表最前面，如`\[\] xyz\]`。同样，要包含字面‘∧’，将其放在开头以外的位置，要插入字面‘-’，将其放在最前或最后（Silge and Robinson, 2017）。

让我们使用‘`\[teh|\]`’并将匹配项替换为空格（‘’）。模式‘`\[teh|\]`’在文本中查找‘t’或‘e’或‘h’或‘|’，任何匹配项都将被空格替换。

![](img/page341-01.png)

### 元字符：脱字符‘∧’

脱字符‘∧’用于表示字符的补集。‘`\[∧th∧\]`’将匹配任何字符但不匹配‘t, 不匹配‘h’，也不匹配‘∧’。请注意，‘∧’只有在字符集开头时才有意义。其他位置出现的‘∧’被视为要搜索的普通字符。`\[∧a-z\]`将匹配所有字符但不匹配‘a’到‘z。

让我们使用`\[∧a-z\]`来匹配模式。注意文本中的替换。

![](img/page341-02.png)

在字符类外部使用‘∧’表示在行开头进行搜索。假设我们想匹配`Festival`并替换为空格。与其写完整的单词‘Festival’，我们可以这样做：

![](img/page341-03.png)

上面`gsub()`中的代码在搜索模式中有三个组成部分：

1. ‘`∧F`’ - 查找以 F 开头的词。我们实际上可以去掉‘∧’，它仍然可以工作。
2. ‘`\\w`’ - 查找任何字母数字字符，即`\[a-zA-Z0-9\]`
3. ‘`+`’ − 查找前一个值一次或多次。符号+指的是在上述代码中`gsub()`内部传递的值。

上面的代码片段也可以重写如下：

![](img/page342-01.png)

我们也可以使用下面的代码片段来查找以‘F’或‘f’开头的任何单词并将其替换为空格。

![](img/page342-02.png)

让我们观察上面代码片段与下面使用的代码片段之间的结果差异。

![](img/page342-03.png)

### 元字符：反斜杠‘\\’

反斜杠‘\\’可以跟随各种字符以表示特殊序列。‘\\’也可以用于跳过元字符，使其可以在文本中匹配。`\[\\\]`将替换文本中的换行‘’或‘\\’。

![](img/page342-04.png)

R 支持某些预定义的字符类。如下所示（Silge and Robinson, 2017）：

1. `[:alnum:]` – 字母数字字符：`[:alpha:]`和`[:digit:]`即`\[a-zA-Z0-9\]`。
2. `∧[:alnum:]` – 非字母数字字符：`∧[:alpha:]`和`∧[:digit:]`即`∧\[a-zA-Z0-9\]`。
3. `[:alpha:]` – 字母字符：`[:lower:]`和`[:upper:]`即`\[a-zA-Z\]`。
4. `[:blank:]` – 空白字符：空格和制表符，以及可能的其他特定于区域设置的字符，如不间断空格。
5. `[:cntrl:]` – 控制字符。在 ASCII 中，这些字符的八进制代码为 000 到 037，以及 177（DEL）。
6. `[:digit:]` – 数字：0 1 2 3 4 5 6 7 8 9。
7. `[:graph:]` – 图形字符
8. `[:lower:]` – 当前区域设置中的小写字母。
9. `[:print:]` – 可打印字符
10. `[:punct:]` – 标点字符：! “ # $ % & ‘ ( ) \* + , − . / : ; < = > ? @ \[ \] ∧ \_ ‘ { | } ~.
11. `[:space:]` – 空格字符：制表符、换行符、垂直制表符、换页符、回车符、空格以及可能的其他特定于区域设置的字符。
12. `[:upper:]` – 当前区域设置中的大写字母。
13. `[:xdigit:]` – 十六进制数字：0 1 2 3 4 5 6 7 8 9 A B C D E F a b c d e f。

有关预定义字符类的更多帮助，请在控制台输入`?regex`。使用预定义的字符类，让我们从文本中删除换行符和数字。原始文本如下所示。

![](img/page343-01.png)

换行符和数字可以通过使用以下代码块删除：

![](img/page343-02.png)

上述结果也可以通过使用‘`\\d|\\s`’来实现，其中|是正则表达式中的‘或’运算符。下面的代码实现了‘`\\d|\\s`’以获得相同的结果。

![](img/page343-03.png)

让我们重新打印文本，然后删除除数字和空格之外的所有字符。

![](img/page343-04.png)

下面的代码片段将除数字和换行符（）之外的所有内容替换为空格。

![](img/page344-01.png)

可以用下面的代码将文本中的字母和数字替换为空格。

![](img/page344-02.png)

可以用下面的代码将文本中除字母和数字之外的所有内容替换为空格。

![](img/page344-03.png)

### 元字符：美元符号‘$’

元字符‘$’用于在行尾匹配模式。行尾定义为字符串末尾或紧邻换行符（`\\n`）之前的文本。让我们从下面每个句子的末尾删除句点‘x’。

![](img/page344-04.png)

### 元字符：点‘x’

点![](img/pageIn_ch9-01.png)是另一个元字符，用于匹配除换行符外的任何字符一次。‘`\[a.\]`’将匹配文本中一次字符‘a’。然而，由于我们使用的是‘`gsub()`‘函数，我们会看到匹配和替换发生在文本中的所有位置。因此，我们将使用`sub()`函数，该函数仅执行一次匹配。

![](img/page344-05.png)![](img/page345-01.png)

### 9.3.2 重复字符

除了匹配字符类中定义的一组字符外，正则表达式还可以用于查找模式以特定次数重复。

#### 元字符：星号‘\*’

‘\*’指定前一个字符可以重复零次或多次，而不是恰好一次。因此，*h*`[t*]`将查找以*‘h’*开头的词并匹配*‘t’*出现零次或多次。

![](img/page345-02.png)

#### 元字符：加号‘+’

‘+’指定前一个字符可以重复一次或多次，而不是恰好一次。因此，*h*`[t+]`将查找以*‘h’*开头的词并匹配*‘t’*出现一次或多次。

![](img/page345-03.png)

#### 元字符：问号‘?’

‘?’指定前一个字符可以重复一次或零次。因此，`covid-?19`将匹配‘covid-19’或‘covid19。

![](img/page345-04.png)![](img/page346-01.png)

### 9.3.3 正则表达式的应用

让我们创建正则表达式并使用它从文本中删除换行符、URL 以及标点符号。

![](img/page346-02.png)

实现上述结果的另一种方法如下：

![](img/page346-03.png)

我们现在将文本拆分为单独的单词。正则表达式“`\[∧[:alnum:]\]`”将查找不是字母数字字符的分界点。我们将使用`stringr`包中的`str_split()`函数来拆分数据。

![](img/page346-04.png)

正则表达式和`gsub`在数据清理中也很有用。**表 9.1**显示了混乱的数据。我们将此数据命名为‘`random_df`‘。

![](img/page347-01.png)

**表 9.1**显示了以下问题：

1. 列名具有‘$’符号，这可能导致在引用列名时出现问题。在其他情况下，列可能具有任何标点符号，这可能是不希望的。
2. 销售单位中的值包含‘,’，因此将被识别为字符变量。
3. 毛利率、净销售额等中的值包含‘$’符号和其他字符，这导致这些列被识别为不正确的数据类型。




这些问题可以通过使用 `gsub` 和正则表达式如下面所示进行纠正。

![](img/page347-02.png)

列名都已按语法正确顺序排列，且没有标点符号。让我们使用下面的代码来清理列值。

![](img/page347-03.png)

从 **表 9.2** 中，我们可以看到列名中不存在不需要的字符。然而，列值的数据类型可能仍然不正确（例如，SOP 单位变量的值中存在 ‘,’ 会使该列被标记为分类列）。`read.csv()` 的默认参数将分类变量类型转换为因子变量。因此，我们不能直接将这些列类型转换为数值。

![](img/page348-01.png)

如果这样做，列中的数值将不正确。因此，我们将首先将变量类型转换为字符变量，然后再将其类型转换为数值变量。下面的函数有助于实现这一点。

![](img/page348-02.png)

从 **表 9.3** 中，我们可以看到列名和列中的值的数据类型正确。此数据框可以使用 `write.csv()` 函数保存并可用于进一步分析。

本节让我们对正则表达式在文本处理中的使用有了一些了解。在以下各节中，我们将使用高级包，这些包抽象了正则表达式并提供易于应用于清理文本数据的方式。

## 9.4 | 文本分析包

我们将使用最先进的包，如 `twitteR`、`tidyVerse`、`tidytext`、`stringr`、`quanteda`、`text2vec` 和 `spacyr` 来预处理和分析文本数据。

**1.** `twitteR`、`streamR` 和 `rtweet`：它们都用于建立与 Twitter API 的连接并抓取推文。

**2.** `stringr`：用于字符操作、区分大小写的转换以及使用正则表达式（regex）进行模式匹配。我们将使用正则表达式与 `gusb()` 进行文本预处理。

![](img/page348-03.png)

**3.** `tidytext`：是 tidyverse 家族的包之一，可用于基本的数据清理、可视化、创建词频-逆文档频率（tf-idf）、创建 n-gram 以及主题建模。该包可与 `dplyr`、`ggplot` 用于可视化无缝协作。我们将广泛使用此包进行汇总、可视化、情感分析、创建 DTM（文档词矩阵）和主题建模。

**4.** `quanteda`：定量文本数据分析（`quanteda`）提供执行基本自然语言处理的功能，如文本预处理、标记化和创建文档特征矩阵、主题建模和其他高级操作。我们将不使用此包。

**5.** `text2vec`：该包受 `Gensim` 启发，可从文档中构建文档词矩阵或词共现矩阵（tcm）。使用 `text2vec`，我们可以通过从单词或 n-gram 到向量空间的映射来向量化文本。基于此向量化文本生成 dtm 或 tcm。诸如主题建模（Latent Dirichlet Allocation、Latent Semantic Analysis）、词嵌入（GloVe）、搭配、相似性搜索等模型可在此 dtm、tcm 上构建（Anon, 2021）。

**6.** `spacyr`：采用自 Python 中的 `spacy` 包，可用于高级自然语言处理（NLP），如为深度学习准备数据、标记化、解析等。该包可与 `quanteda` 和 `tidytext` 无缝协作。

请注意，在上述提到的包中，存在冗余函数和包。我们可以根据分析文本数据时要实现的目标使用包和函数。然而，一个有用且基础的包，它将在文本预处理中发挥作用的是 `stringr`。`Stringr` 使用正则表达式（regex）在文本中进行模式匹配，然后执行文本数据的清理。事实上，`tidytext` 包内的函数在内部会大量使用正则表达式。

如果其中任何包之前已安装，并且由于版本不匹配导致包初始化时出现错误，我们可能需要在继续之前重新安装该包。在继续之前，请在控制台中运行下面两行。

**1.**
```
if ("package:" %in% search()) { detach("package:", unload=TRUE)}
```
**2.**
```
if ("" %in% rownames(installed.packages())) { remove.packages("")}
```

![](img/page349-01.png)![](img/page350-01.png)

## 9.5 | 数据导入

我们需要建立与 Twitter 的连接并验证 R 以抓取推文。`twitteR` 中的 `setup_twitter_oauth` 函数授权 `twitteR` 会话。我们将使用 `twitteR` 从 Twitter 拉取请求。

### 9.5.1 使用 twitteR 包

`twitteR` 可用于在一段时间内抓取推文。`twitteR` 包中的 `searchTwitter` 函数用于抓取推文。由于我们想要抓取与印度疫情更新相关的推文，我们将使用以下关键词和 Twitter 账号：

**1.** #IndiaFightsCorona – 包含 hashtag IndiaFightsCorona。

**2.** @COVIDNewsByMIB – 提及 Twitter 账号“COVIDNewsByMIB”。

**3.** @covid19indiaorg – 提及 Twitter 账号“covid19indiaorg”。

**4.** @COVID19_INDIA – 提及 Twitter 账号“COVID19_INDIA”。

编写查询的指南在 Twitter 应用文档中提到 [`developer.twitter.com/en/docs/twitter-api/v1/tweets/search/guides/standard-operators`](https://developer.twitter.com/en/docs/twitter-api/v1/tweets/search/guides/standard-operators)。我们还可以通过使用下面的语法（Anon, 2020）来修改搜索查询以过滤或排除某些类型的结果：

**1.** 通过 “`-filter:retweets`” 排除转发

**2.** 通过 “`-filter:quote`” 排除引用

**3.** 通过 “`-filter:replies`” 排除回复

**4.** 通过 “`filter:verified`” 过滤（仅返回）已验证用户

**5.** 通过 “`-filter:verified`” 排除已验证用户

**6.** 通过 “`-filter:verified OR filter:verified`” 获取所有内容

**7.** 通过 “`filter:news`” 过滤（仅返回）包含新闻文章链接的推文 过滤（仅返回）包含媒体的推文 “`filter:media`”

例如，“`#IndiaFightsCorona -filter:retweets`” 将给出排除转发的推文。要获取有关 `searchTwitter` 函数参数的更多帮助，请在控制台中输入：`?twitteR::searchTwitter`。Twitter API 还列出了可传递给 `search_tweets` 的其他几个参数。¹ 让我们加载 `twitteR` 包并验证 R 以抓取推文。

![](img/page351-01.png)![](img/page351-02.png)

请注意，50,000 条推文的拉取请求可能不会在脚本的每次运行中都返回相同数量的推文。在上面的拉取请求中，第一次运行返回了 25,494 条推文，而第二次运行返回了 19,362 条推文。

`searchTwitter` 还有一个名为 `geocode` 的参数，我们可以在其中传递纬度、经度和想要搜索用户推文的半径。假设，在上述查询中，如果我们想搜索印度中央邦贾巴尔普尔 1,000 公里半径内的推文，`geocode` 将为 `geocode = "23.22321145,79.9811422182487,10 00km"`。该查询可能为此 `geocode` 报告 12,353 条推文。

`covid_twitteR` 对象的 数据类型为 list。我们将使用 `twitteR` 中的 `twListToDF` 函数将其转换为数据框。

![](img/page351-03.png)

我们还将把 `covid_twitter_df` 保存为 csv 文件，这样以后就不需要再次查询 Twitter API。

![](img/page351-04.png)

数据的维度如下：

![](img/page352-01.png)

Twitter API 返回的特征如下。

![](img/page352-02.png)



The `text` 特性包含用户评论，并且被 Twitter 限制为 280 个字符。此 `text` 特性将用于进一步分析。尽管 `longitude` 和 `latitude` 特性在特性列表中存在，我们可以在 **表 9.4** 中看到它们对每个用户都包含 NA 值。Twitter API 由于隐私问题不会报告用户的 `latitude` 和 `longitude`。然而，我们可以通过使用 `lookupUsers()` 函数获取用户的位置。这些函数如果用户没有私人账户将返回详细信息。

![](img/page352-03.png)

The `user_details` 对象是 `list` 类型。我们将把它转换为 `dataframe` 并保存为 csv 文件。

![](img/page352-04.png)![](img/page352-05.png)

Saving the user details to avoid further read from the API.

保存用户详细信息以避免进一步从 API 读取。

![](img/page353-01.png)

From the `user_detail_df`, we can get the user location by using `print(user_detail_df$location)`.

从 `user_detail_df` 中，我们可以通过使用 `print(user_detail_df$location)` 获取用户位置。

The `covid_twitter_df` may contain duplicate texts which can be removed before further analysis. We can remove the duplicate text in the `covid_text_df` by using `duplicated()` from the base package. The function expects a column vector or a `dataframe` to be passed. If we pass the column vector, say `covid_twitter_df$text`, we will get 7,484 unique texts. However, if we pass the complete `dataframe`, there is no duplicate record as the same tweet could have been shared by a different user (identified by `screenName` column). From the dimensions of ‘`covid_twitteR_unq_df`‘ `dataframe`, we can conclude that there is no duplicate record.

`covid_twitter_df` 可能包含重复文本，可以在进一步分析前将其删除。我们可以使用基础包中的 `duplicated()` 删除 `covid_text_df` 中的重复文本。该函数期望传递一个列向量或一个 `dataframe`。如果我们传递列向量，例如 `covid_twitter_df$text`，我们将得到 7,484 条唯一文本。然而，如果我们传递完整的 `dataframe`，则没有重复记录，因为同一条推文可能由不同的用户（由 `screenName` 列标识）分享。从 ‘`covid_twitteR_unq_df`‘ `dataframe` 的维度来看，我们可以得出结论没有重复记录。

![](img/page353-02.png)

We will proceed with further analysis using the `covid_twitter_df`. The first five observations are shown in **表 9.4.**

我们将使用 `covid_twitter_df` 进行进一步分析。前五个观察值显示在 **表 9.4** 中。

![](img/page353-03.png)

## 9.6 | 文本预处理

Before we process the `text` column of `covid_twitter_df` shown in **表 9.4**, let us understand some of the basics in text preprocessing. Unlike structured data, features (independent variables) are not explicitly available in text data. Thus, we need to process text data to extract features from it. One way to create a feature is to consider each word as a feature and find a measure to capture whether a word exists or does not exist in a sentence (Pradhan and Kumar, 2019). The row items of the `text` column in `covid_twitter_df` are sentences and contribute to building Bag-of-Words (`BoW`). Each sentence (record) is called a document and a collection of all documents is called corpus. Let us define `BoW`

在处理 **表 9.4** 中显示的 `covid_twitter_df` 的 `text` 列之前，让我们了解文本预处理中的一些基础知识。与结构化数据不同，特征（自变量）在文本数据中并未明确可用。因此，我们需要处理文本数据以从中提取特征。创建特征的一种方法是把每个词视为一个特征，并找到一个度量来捕捉某个词在句子中是否存在（Pradhan and Kumar, 2019）。`covid_twitter_df` 中 `text` 列的行项是句子，有助于构建词袋（`BoW`）。每个句子（记录）称为文档，所有文档的集合称为语料库。让我们定义 `BoW`

### 9.6.1 词袋 (BoW) 模型

Intuitively, `BoW` is a dictionary/vocabulary of known words from the corpus. A Bag-of-Word (`BoW`) model consists of the following:

直观地说，`BoW` 是来自语料库的已知词的词典/词汇表。词袋（`BoW`）模型包括以下内容：

**1.** Vocabulary of words from the corpus, that is, `BoW`

**1.** 来自语料库的词词汇，即 `BoW`

**2.** Measure which assigns numeric value to words

**2.** 为词分配数值值的度量

The measures which attach a numeric value to the words may also be called word embeddings. Word embeddings can be simple frequency-based measures such as count of words in the document or a Boolean value representing presence/absence of the vocabulary in the document.

将数值附加到词的度量也可能称为词嵌入。词嵌入可以是简单的基于频率的度量，例如文档中词的计数，或表示词汇在文档中存在/不存在的布尔值。

**Word embeddings**, intuitively, are measures which assigns numeric value to each word. The simplest of measures can be using ‘count’ of words in a document or ‘Boolean’ measure which shows presence or absence of words in a document.

**词嵌入**直观上是为每个词分配数值值的度量。最简单的度量可以使用文档中词的‘count’或显示词在文档中存在或不存在的‘Boolean’度量。

![](img/page354-01.png)

**Word embeddings** in strict sense assigns values (a real valued vector which is in tens or hundreds of dimensions) to a word in such a way that words which are similar are given very similar values. This helps overcome issues with `BoW` representation (which can represent a word in millions of dimensions in case of huge corpus). `BoW` is still a useful concept in basic data representation and sentiment analysis.

严格意义上的**词嵌入**为词分配值（一个实值向量，其维度在数十或数百维），使得相似的词被赋予非常相似的值。这有助于克服 `BoW` 表示的问题（在巨大语料库的情况下，`BoW` 可以用数百万维表示一个词）。`BoW` 在基本数据表示和情感分析中仍然是一个有用的概念。

The first step in creating a `BoW` model is the creation of a dictionary of all the words used in the corpus. We then select a measure to convert each document to a vector that assigns scores to words available in the document. There are four primitive frequency-based measures, aka word embeddings, which assign importance to the words in a `BoW` model.

创建 `BoW` 模型的第一步是创建语料库中使用的所有词的词典。然后我们选择一个度量将每个文档转换为向量，为文档中可用的词分配分数。有四种原始基于频率的度量，也称为词嵌入，它们为 `BoW` 模型中的词分配重要性。

**1.** Binary vector

**1.** 二进制向量

**2.** Count Vector

**2.** 计数向量

**3.** TF Vector

**3.** TF 向量

**4.** TF-IDF Vector

**4.** TF-IDF 向量

#### 二进制向量

Consider the following two documents:

考虑以下两个文档：

**1.** Document 1 (positive sentiment, coded as `y = 1`): I really really like IPL

**1.** 文档 1（积极情感，编码为 `y = 1`）：I really really like IPL

**2.** Document 2 (negative sentiment, coded as `y = 0`): I never like IPL Note: IPL stands for the Indian Premier League, which is played every year.

**2.** 文档 2（消极情感，编码为 `y = 0`）：I never like IPL 注：IPL 代表印度板球超级联赛，每年举办一次。

The complete vocabulary set (aka dictionary) for the above two documents will have words **I, really, never, like**, and **IPL.** These words may be considered as features (`x1` through `x5`). The number of words in the vocabulary defines the length of the vector which will be used to score the words in the document. In the above example, we can score the absence or presence of words in the document using 0/1 code as shown in **表 9.5.**

上述两个文档的完整词汇集（又称词典）将包含词 **I, really, never, like** 和 **IPL。** 这些词可被视为特征（`x1` 到 `x5`）。词汇中词的数量定义了用于对文档中词进行评分的向量的长度。在上述示例中，我们可以使用 0/1 编码对文档中词的缺失或存在进行评分，如 **表 9.5** 所示。

**表 9.5** is called a term-document matrix. Intuitively, the term-document matrix is a bag of words for a set of documents (two documents in this case) where row represents a single document and column represents a single feature.

**表 9.5** 称为词-文档矩阵。直观地说，词-文档矩阵是文档集（本例中为两个文档）的词袋，其中行代表单个文档，列代表单个特征。

#### 计数向量

The problem with Boolean representation is that it gives equal weightage to words in a document, irrespective of the number of times they appear in the document. To overcome this issue, we can count the words rather than treating the words as Boolean values. For creating count vectors, we simply score the words in a document by counting the occurrence of each word as shown in **表 9.6.**

布尔表示的问题在于它对文档中的词给予同等权重，而不管它们在文档中出现的次数。为克服此问题，我们可以计数词而不是将词视为布尔值。创建计数向量时，我们只需通过计算每个词在文档中的出现次数来对词进行评分，如 **表 9.6** 所示。

#### 词频 (TF) 向量

One of the potential issues with simple count vector is that the count of a word may be much more in a long document compared to the count of the same word in a short document. Thus, the words may get more weightage in analysis just by virtue of the document being long. So, it may be useful to normalize the count of words by dividing it by the count of total words in the document. This is called Term Frequency (`TF`) vector (Pradhan and Kumar, 2017) and is a measure of how frequently the word/term appears in a document. It is calculated for each document in the corpus by 公式 (9.1):

简单计数向量的潜在问题之一是，某个词在长文档中的计数可能远高于在短文档中的计数。因此，词可能仅因文档较长而在分析中获得更大权重。因此，将词的计数除以文档中总词数进行归一化可能是有用的。这称为词频（`TF`）向量（Pradhan and Kumar, 2017），是衡量词/术语在文档中出现的频率的指标。它是根据语料库中每个文档通过 公式 (9.1) 计算的：

![](img/page354-02.png)![](img/page355-01.png)![](img/page355-02.png)

where, `TF.` is the term frequency for word.

其中，`TF.` 为词的词频。

Term frequency for the two documents in shown in **表 9.7.**

两个文档的词频显示在 **表 9.7** 中。

#### 词频-逆文档频率 (TF-IDF)

Common words may appear in higher frequency in a document and in the entire corpus. These common words may not be very important in identifying a pattern in the data. Less common words should have more weightage in the corpus. Term Frequency-Inverse Document Frequency (`TF-IDF`) measures the importance of a word in a document to the same word in the collection of documents (corpus). The importance increases proportional to the number of times a word appears in the document but is offset by the frequency of the word in the corpus. `TF-IDF` for a word in a document is given by 公式 (9.2):

常见词可能在文档中和整个语料库中以更高频率出现。这些常见词在识别数据模式方面可能并不重要。较不常见的词应在语料库中具有更大权重。词频-逆文档频率（`TF-IDF`）衡量一个词在文档中的重要性相对于该词在文档集合（语料库）中的重要性。其重要性与词在文档中出现的次数成比例增加，但会被词在语料库中的频率所抵消。文档中某个词的 `TF-IDF` 由 公式 (9.2) 给出：

![](img/page355-03.png)

where

• `TF[i]` is the term frequency for word

• `N` is the total number of documents in the corpus

• `N[i]` is the number of documents that contain the word `i`

其中

• `TF[i]` 为词的词频

• `N` 为语料库中的文档总数

• `N[i]` 为包含词 `i` 的文档数量

The IDF value for each word in the above two documents is given in **表 9.8.**

上述两个文档中每个词的 IDF 值在 **表 9.8** 中给出。

The `TF-IDF` values for the two documents are shown in **表 9.9.**

两个文档的 `TF-IDF` 值显示在 **表 9.9** 中。

Though the concept to convert unstructured data to structured data using `BoW` seems straightforward, we may face many challenges. For a very large corpus, say 500 sci-fi novels in English, the vocabulary set may run into thousands and millions of words.

尽管使用 `BoW` 将非结构化数据转换为结构化数据的概念似乎很直接，但我们可能会面临许多挑战。对于非常大的语料库，例如 500 部英文科幻小说，词汇集可能达到数千甚至数百万个词。

![](img/page355-04.png)![](img/page355-05.png)



技术如 feature hashing、word2vec、Glove 都是有助于创建 **词表示** 的算法，该表示减少了词所表示的维度。

我们可能需要一个一百万维的特征向量来表示 `BoW`，然后使用 `BoW` 对每本书进行评分。这可能需要更多的存储内存，同时在建模时变得计算成本高昂。因此，我们可能希望减小构建 `BoWs` 时的词汇表大小。确定我们希望在 `BoWs` 中保留为特征的正确词集变得很重要。以下是用于减小词汇表的一些方法：

1. 从文本数据中删除不需要的词。删除文档中的标点符号，如 ‘,’ ‘,’ 和 ‘://’。这些通常由 `tidytext` 包中的函数处理。一般来说，我们可以使用 `regex` 来删除标点符号和不需要的词（非上下文词）。
2. 词干提取和词形还原可以将词还原为其词根形式，这也有助于减少 `BoW`。该概念将在后面的章节中讨论。
3. 除了不需要的词之外，还删除英语语法中的冠词、介词和连词，如 ‘the’、‘of’、‘to’、‘an’、‘a’ 和 ‘in’。这些被称为停用词。可以通过创建 `stop_words` 词典并从 `BoWs` 中过滤掉这些词来删除停用词。

清理文本数据还有其他几个挑战。除了实施上述概念之外，让我们使用以下章节中的推特数据来了解其他潜在问题及其解决方案。

## 9.7 | Twitter 数据可视化

我们将使用 `covid_twitter_df` 并分析推文。我们希望了解

1. 哪些用户推文最多？
2. 用户总体上在谈论什么？具体用户在谈论什么？
3. 推文的信息来源是什么？我们可以通过提取文本中的 URL 并进行某些预处理来获取此信息。

让我们获取上述问题的答案。

### 9.7.1 谁是推文最多的用户？

我们可以根据用户的 `screenName` 获取此信息。这相对直接。然而，对此查询可以得到两个不同的答案——一个包含转发，另一个排除转发。让我们绘制推文最多的用户（包含转发）。让我们绘制按推文数量排序的前 40 名用户。**表 9.10** 显示了六个用户的快照。数据可以使用 `ggplot` 包中的简单条形图（`geom_bar` 或 `geom_col`）表示。然而，我们使用的是 `ggplot` 包中的点图（`geom_point`）和线段图（`geom_segment`）的组合。这有助于构建一种称为棒棒糖图的精美图表。

**表 9.10** | 新冠疫情中推文数超过 40 的六大推文者

| `screenName` || `n` |
| --- | --- |
| ROBRAIPUR || 336 |
| --- | --- |
| PIBRaipur || 303 |
| NACOINDIA || 298 |
| BSDhruw2 || 293 |
| COVIDNewsByMIB || 255 |
| PIBKolkata || 253 |

![](img/page357-01.png)

从 **图 9.5** 可以看出，区域外联局（ROB）赖布尔、新闻信息局（PIB）赖布尔和实地外联局（FOB）比拉斯布尔（BSDhruw2）似乎非常活跃。

![](img/page357-02.png)![](img/page358-01.png)

国家艾滋病控制组织似乎也在积极就此话题发推。名为 kjayesh、vinyksr 和 VasGiri 的个人也很活跃。

让我们绘制至少有 100 条推文/转发的顶级用户。由于数据是根据推文数量排序的，**图 9.6** 将包含来自 **图 9.5** 的用户子集。

![](img/page358-02.png)

如果排除转发，活跃用户是谁？让我们绘制按推文数量排序的前 40 名用户。

![](img/page358-03.png)![](img/page359-01.png)

我们可以将 **图 9.7** 与 **图 9.5** 进行比较，可以看出 COVIDNewsByMIB 的转发并不多，但它正在积极发推。有趣的是，kjayeshb 似乎更积极转发而不是发推。让我们弄清楚这是否正确。**表 9.11** 显示了该用户的推文，它们大多似乎是转发，其中只提到了推特账号。在文本处理时，此类推文将被删除，因为它们不包含任何文本信息。

![](img/page359-02.png)

**表 9.11** | 用户 kjayeshb 的前六条推文

| `Text` || `screenName` |
| --- | --- |
| @COVIDNewsByMIB @FinMinIndia @MoHFW_INDIA @drharshvardhan @PrakashJavdekar @PIBHomeAffairs @ PIB_India @DDNewslive… [`t.co/n1EHgJYGdL`](https://t.co/n1EHgJYGdL) || kjayeshb |
| --- | --- |
| @COVIDNewsByMIB @FinMinIndia @MoHFW_INDIA @drharshvardhan @PrakashJavdekar @PIBHomeAffairs @ PIB_India @DDNewslive… [`t.co/Tmhvas2TPN`](https://t.co/Tmhvas2TPN) || kjayeshb |
| @COVIDNewsByMIB @FinMinIndia @MoHFW_INDIA @drharshvardhan @PrakashJavdekar @PIBHomeAffairs @ PIB_India @DDNewslive… [`t.co/3I0UiT1c81`](https://t.co/3I0UiT1c81) || kjayeshb |
| @COVIDNewsByMIB @ICMRDELHI @MoHFW_INDIA @AyushmanNHA @drharshvardhan @DDNewslive @ airnewsalerts @PIB_India… [`t.co/5X0GTppdmG`](https://t.co/5X0GTppdmG) || kjayeshb |
| @COVIDNewsByMIB @ICMRDELHI @MoHFW_INDIA @AyushmanNHA @drharshvardhan @DDNewslive @ airnewsalerts @PIB_India… [`t.co/DJK9lodqUM`](https://t.co/DJK9lodqUM) || kjayeshb |
| @MoHFW_INDIA @PMOIndia @drharshvardhan @AshwiniKChoubey @PIB_India @CovidIndiaSeva @COVID-NewsByMIB @mygovindia… [`t.co/rA6dnhfEsc`](https://t.co/rA6dnhfEsc) || kjayeshb |

![](img/page360-01.png)

在 **表 9.12** 中，我们看到另一方面 IndiaCovid19Bot 正在提供活跃病例和康复病例的每小时统计数据。这些文本数据还包含大量表情符号。在所进行的分析背景下，我们不需要数字、表情符号等，因此我们将使用 `regex` 删除此类词。

![](img/page360-02.png)![](img/page360-03.png)

### 9.7.2 人们在谈论什么

回答此查询需要创建在 第 9.6.1 节 中讨论的 `BoW` 数据。我们将使用 `covid_twitter_df` 创建 `BoW`。我们将使用 `tidytext`/`tokenizer` 包中的 `unnest_tokens` 函数来拆分文档的词。这些拆分后的词可以称为 tokens。因此，token 是文本的单位，例如词，我们希望在分析中使用。分词是将文档/文本拆分为 tokens 的过程。`unnest_token()` 要求将以下函数作为参数传递：

1. `output` – 存储分词后输出的列名。
2. `input` – 要拆分的输入列名。在此示例中，它是 `covid_twitter_df` 中名为 ‘`text`’ 的列。
3. `format` – 要拆分的文档格式。默认是文本文档。这也支持 ‘HTML’、‘XML’ 和 ‘latex’ 格式的拆分。
4. `token` – 分词的单位。默认是 ‘`word`’，意味着用每个词拆分文档。

可以传递的其他值如下：

> “`characters`”、“`character shingles`”、“`ngrams`”、“`skip ngrams`”、“`sentences`”、“`lines`”、“`paragraphs`”、“`regex`”、“`tweets`”（按词分词但保留用户名、hashtags 和 URL），以及 “`ptb`”（宾夕法尼亚树库）。

我们将 `token` 用作 ‘`tweets`’ 来按词拆分，但仍保留用户名、hashtags 和 URL。我们还将使用 `strip_url` 参数进一步删除作为 tokens 创建的 URL。默认情况下，每个词单独作为一个 token。然而，tokens 也可以是词的组合，然后称为 n-gram token，其中 `n` 是组合中出现的词数。



默认情况下，`unnest_tokens()` 会将词元转换为小写并去掉标点符号。我们可以使用 `to_lower` 和 `strip_punct` 参数来更改默认行为。

## 清理推文

在使用 `unnest_tokens()` 拆分数据之前，让我们了解一些需要处理的问题。我们将使用下面的文本来突出本节讨论的所有问题并依次修复它们。

![](img/page361-01.png)

**1.** 推特数据的其中一个问题是大多数推文会包含推特账号。我们使用 #IndiaFightsCorona、@COVIDNewsByMIB、@covid19indiaorg、@ COVID19_INDIA 来抓取推文。因此，推文会大量包含这些词，但不会携带太多信息。下面的正则表达式处理以‘#’或‘@’开头的词。我们将从推文中删除此类词。

正则表达式完美地完成了工作。

![](img/page362-01.png)

**2.** 推文中的 URL 在分析中可能不需要，这样的 URL 和不需要的词也需要删除。下面的正则表达式处理 URL 并将其删除。

![](img/page362-02.png)

**3.** 有些词可能不是 hashtags 和 URL，但仍在分析中可能没有太多意义。我们在文本数据中也不需要数字和标点符号。让我们创建一个表达式来删除此类词。我们可能无法提前识别所有信息量较小的词。可能需要多次迭代才能识别并删除信息量较小的词。

![](img/page362-03.png)

大部分表达式之前已讨论过，但让我们来看一下正则表达式“COVID(-?19)?”：

![](img/page362-04.png)

我们将同时对文本应用这三个正则表达式并查看结果。

![](img/page363-01.png)

上述输出显示，在应用所有正则表达式后，我们已修复了文本数据中的一些问题。然而，我们仍然在上述输出中发现一些 unicode 文本。该 unicode 对应于 emoji ![](img/pageIn_ch9-02.png)和 ![](img/pageIn_ch9-03.png)。我们还看到一些其他语言的文本。我们也将处理这两个问题。

**4.** 推特数据或一般社交媒体数据的一个主要问题是使用字形/表情符号，例如，![](img/pageIn_ch9-04.png)，等。这些被称为 Unicode 字符。Unicode 是一个字符集，旨在定义所有语言中的所有字符和字形（图形表示）。根据分析目的，我们可能希望保留数据中的字形，也可能不希望保留。要删除字形，我们可以在正则表达式中使用 Unicode，如下所示：

![](img/page363-02.png)

\\p 用于匹配表情符号。其后的字符表示表情符号所属的类别。Emoji 属于类 ‘Other_Symbol’ (So) 和 ‘Unassigned’ (Cn) 类。‘Math_Symbol’ (Sm) 和 ‘Currency_Symbol’ (Sc) 有时也可能需要。上述正则表达式中的最后一个表达式是为了处理未被 \\p{xx} 字符类处理的 emoji。例如，![](img/pageIn_ch9-05.png)(方括号内的问号) 的编码为 ‘\\U0001f3fd’，但未被 \\p{xx} 删除。为了删除此类特殊字符，我们可以使用由 \[\\U{1F000}-\\U{1FFFF}\] 给出的 Unicode 字符范围。- ..

**5.** 就用户书写文本的方式而言，Twitter 数据很混乱。我们总会在推文中看到语言混杂。在处理英语时，我们可能需要删除非英语的词。我们可以通过使用如下正则表达式来实现：

![](img/page363-03.png)

在 ‘`remove_non_english_regex`’ 中，表达式 “\[∧\\x01-\\x7F\] +”，匹配 ASCII 字符集（0-127，即 0x0 到 0x7F）。在 Unicode 中，相同的表达式将写为 “\[∧\\u0000-\\u007F\]+”。该表达式不仅可以删除非英语词，还有助于删除特殊/不可见字符和表情符号。因此，第 4 步也可能是多余的。

**6.** 词 ‘RT’ 也会出现在大多数推文中，表示它是转推。我们将使用 `dplyr` 和 `stringr` 中的 `filter()` 和 `str_detect()` 函数过滤掉转推。

**7.** 我们将使用 `tidytext` 包中内置的英语语法 BoW/词表，通过使用 `anti_join()` 来删除这些词。`anti_join()` 返回推文中在 `stop_words` 中没有匹配项的所有行。

上述七个步骤中使用的正则表达式可能需要根据分析的文本数据进行修改。让我们考虑上述七个步骤并使用 `unnest_token()` 对 `covid_twitter_df` 中的文本列进行拆分。**表 9.13** 显示了结果表中十个观察值。

![](img/page364-01.png)![](img/page364-02.png)![](img/page365-01.png)

词汇表包含 4,444 个词。请注意，如果在创建词元之前不应用正则表达式，词汇表将有 7,825 个唯一词。因此，它将创建一个长度为 7,825 的向量并消耗更多内存。

## 9.7.3 可视化 – 单词/词

让我们尝试了解语料库中使用的高频词是什么？**表 9.14** 显示了出现次数最多的前六个词。**图 9.8** 显示了数据的图表。

![](img/page365-02.png)

**表 9.14** | 高频词

| Word || *n* |
| --- | --- |
| Follow || 316 |
| --- | --- |
| Active || 300 |
| Mask || 261 |
| deaths || 243 |
| Hands || 230 |
| swachhbharat || 228 |

我们将绘制 `word_tokens` 中词元计数超过 40 的前 50 个词。此数据切片是通过从 `dplyr` 包中应用 `filter()` 然后 `slice_max()` 从 ‘word_tokens’ 中提取的。此外，在绘制数据时，我们将以正向显示频率计数 100+，以反向显示频率计数小于 100。这是通过将 `geom_segment` 的 `y` 参数设置为 100 来实现的。**图 9.8** 显示了数据的图表。

![](img/page365-03.png)![](img/page366-01.png)

在上面的代码片段中，`filter()` 函数是多余的，因为使用 `slice_max()` 提取的前 50 个词的计数都超过了 40。然而，这对于任何其他数据集可能不成立。从 **图 9.8** 中，我们可以得出结论

**1.** 使用 words like mask, wear, hands, wash, social, distancing, clean, don’t, etc. 表明人们对卫生的普遍认知。

**2.** 人们似乎在大量谈论 swachh bharat、PM (prime minister)。

**3.** 人们在谈论 deaths 和 recovery。推文中这些词的使用可能反映了人们在应对 COVID-19 时普遍的担忧情绪和谨慎态度。

**图 9.9** 显示了词元中计数为 40 及以上的最后 50 个词的图表。

![](img/page367-01.png)![](img/page367-02.png)

迄今为止我们看到的图表基于 BoW (`twitter_words`) 中词的简单计数。然而，我们也可以按每个用户 (`screenName`) 统计词的计数。在这里，`screenName` 可以被视为一个文档（在 第 9.6.1 节 中讨论），我们希望通过它来获取计数。让我们获取拥有多个推文（推文总词数超过 100）的用户 (`screenName`) 并了解他们使用的词。数据可以通过以下步骤准备：

**1.** 使用 `twitter_words` 数据框：
– 选择 `screenName` 和 `word` 列并使用 `count()` 获取所有词的计数。
– 使用 `group_by()` 按 `screenName` 分组数据。
– 创建一个存储用户所写总词数的列。这可以通过 `mutate()` 实现。
– 过滤总词数超过 100 的推文。使用 `filter()` 函数实现此操作。
– 使用 `slice_max()` 从每个用户中选择前七条记录。
– 使用 `ungroup()` 对数据取消分组。
– 使用 `arrange()` 按 `screenName` 和词计数排列数据。




– 创建一个名为 `order` 的列，用于跟踪之前步骤中完成的 `order`/排列。

最后三个步骤是可选的，目的是在使用 `ggplot` 中的 `facet_wrap` 时展示按排序顺序排列的词的图表，见 **图 9.10**。**表 9.15** 显示了使用上述步骤获得的用户列表。这些数据将让我们了解热衷推特的用户在谈论什么。

![](img/page368-01.png)

**图 9.10** 显示了来自 **表 9.16** 的数据的图表。

![](img/page368-02.png)![](img/page369-01.png)![](img/page369-02.png)![](img/page370-01.png)![](img/page370-02.png)

从 **图 9.10** 中，我们可以看到

**1.** 许多用户在推文中使用了超过 20 次 swachhbharat。他们可能正试图通过冠状病毒相关账号推广 swachhbharat 运动。

**2.** BaharBharat 大多在谈论航班运营和更新。

**3.** DDIndialive 似乎在使用表示提供 COVID-19 状态更新的词语。然而，DDSaptagirvja 似乎在其频道上推广其他内容。

**4.** 大多数用户似乎在创造意识以在疫情期间保持安全。这些用户大多似乎是政府或新闻频道推特账号。

**5.** IndiaCovidBot 似乎只非常频繁地使用少数几个词。查看数据可知，该机器人每小时只发布关于康复和死亡人数的推文。由于我们清理了文本（无数字等），我们只能看到可视化中出现的词语。

**6.** 教会似乎通过 PIBImphal 推特账号在 Ukhrul 地区传播了大量意识。

**图 9.11** 显示了来自同一 **表 9.16** 的数据的图表，但未排序。鼓励读者比较 **图 9.10** 和 **图 9.11** 之间的差异，并找出代码片段中差异的原因。

![](img/page371-01.png)![](img/page372-01.png)

由于我们构建的 `twitter_word_count` 数据框包含了所有用户及其使用的词语的信息，因此我们可以查看推文中词语数量在 50 到 100 之间的另一组用户。**图 9.12** 显示了此类用户的图表。

![](img/page372-02.png)

从 **图 9.12** 可以看出，也有少数个人用户在此话题上发推很多。在 **图 9.11** 中并非如此，那里主要是政府机构或新闻频道。

### 9.7.4 改进词袋 – 词干提取和词形还原

从 **图 9.12** 中，我们看到在 COVID-19 话题上写了超过 100 个词的用户使用的词语。然而，如果我们在创建词袋时也考虑到以下几点，本可以做得更好：

![](img/page373-01.png)

**1.** 许多词以多种形式出现，从而导致词汇量（词袋）增加。如果一个词在所有形式中含义相似，我们就可以仅使用其词根作为特征或词袋。词干提取和词形还原是解决此问题的两种流行技术。

– 像 recovery 和 recovered 这样的词出现在词元中。这些词本可以被还原为其词根形式，即 recover。这是通过词形还原过程完成的。

– 像 distancing 和 distance 这样的词也出现在前 100 个词中。我们本可以将这些词词干提取为词根形式，即 distance。这是通过词干提取过程完成的。

**2.** 我们本可以删除像 october、oct、day、days、people 等词。我们将清理此类词并可视化数据的任务留给读者。

#### 词干提取

词干提取通过消除词的屈折形式之间的差异来将每个词还原为其词根形式（Pradhan and Kumar, 2019）。这主要是通过截断词尾来实现的。例如，‘distancing’ 将被还原为词根 ‘distance’。词的词根形式甚至可能不是一个真实的词。例如，‘awesome’ 和 ‘awesomeness’ 将被词干提取为 awesom。词干提取的一个问题是，截断词可能导致不在词典中的词（例如，awesom）。Porter 词干提取器和 Lancaster 词干提取器是两种流行的词干提取算法，它们有关于如何截断词的规则。`library(SnowballC)` 通过 `wordStem()` 实现 Porter 词干提取器。

#### 词形还原

词形还原考虑了词的形态分析。它使用词典将词转换为词根（Pradhan and Kumar, 2019）。例如，词干提取无法区分 ‘man’ 和 ‘men’，而词形还原可以将这些词还原为其原始形式 – man。`library(textstem)` 通过 `lemmatize_words()` 实现词形还原。

我们将在 `covid_twitter_df` 上实现上述所有概念。以下代码片段有助于创建 **表 9.17** 中显示的一元词。

![](img/page374-01.png)

**表 9.17** | 一元词

| `screenName` || `word` |
| --- | --- |
| mygovindia || festiv |
| --- | --- |
| mygovindia || reason |
| mygovindia || forget |
| mygovindia || fight |
| mygovindia || pandem |
| mygovindia || precauti |
| MoHFW_INDIA || activ |
| MoHFW_INDIA || fall |
| MoHFW_INDIA || week |
| MoHFW_INDIA || continu |

**表 9.18** | 来自 twitter 词干数据框的前六个观察结果

| `word` || `n` |
| --- | --- |
| activ || 333 |
| --- | --- |
| follow || 316 |
| hand || 299 |
| mask || 288 |
| death || 266 |
| recoveri || 241 |

![](img/page375-01.png)

我们可以看到，词干提取和词形还原的额外步骤使词汇量从 4,444 个词减少到 3,562 个词。**表 9.18** 显示了来自 `twitter_words_stem` 数据框的词频计数。

![](img/page375-02.png)

#### 可视化 – 词干提取和词形还原后的词

让我们绘制 `word_tokens` 中词元计数超过 40 的前 50 个词。此数据切片是通过从 `dplyr` 包中应用 `filter()` 然后 `slice_max()` 从 `word_tokens` 中提取的。此外，在绘制数据时，我们将词元计数 100+ 显示在正方向，将词元计数小于 100 显示在反方向。这是通过将 `geom_segment` 的 `y` 参数设置为 100 来实现的。

**图 9.13** 显示了数据的图表。

![](img/page375-03.png)

将 **图 9.13** 与 **图 9.9** 进行比较，我们可以看到由于词干提取和词形还原的额外步骤，某些词的频率发生了变化。

同样，我们迄今为止看到的图表都是基于词袋（`twitter_words`）中词的简单计数。如 第 9.7.3 节 中所述，我们在这里也将按用户绘制词。让我们获取有多个推文（推文中总词数超过 100）的用户（`screenName`），并了解他们使用的词语。数据可按以下步骤准备：

![](img/page376-01.png)

**1.** 使用 `twitter_word_stem` 数据框：

– 选择 `screenName` 和 `word` 列，并使用 `count()` 统计所有词的频次

– 使用 `group_by()` 按 `screenName` 分组数据

– 创建一个新列来存储用户撰写的总词数。这可以通过 `mutate()` 实现

– 筛选总词数超过 100 的推文。使用 `filter()` 函数实现此操作。

– 使用 `slice_max()` 为每个用户选择前七条记录

– 使用 `ungroup()` 对数据取消分组。

– 使用 `arrange()` 按 `screenName` 和词频对数据排序。




– 创建一个名为 `order` 的列，用于跟踪之前步骤中完成的顺序/排列。

![](img/page377-01.png)

最后三个步骤是可选的，并且是为了在 `ggplot` 的 `facet_wrap` 中按排序顺序显示词的图而进行的，见 **图 9.14**。**表 9.19** 和 **9.20** 显示了使用上述步骤获得的用户列表。

![](img/page377-02.png)![](img/page378-01.png)![](img/page378-02.png)![](img/page378-03.png)

词‘appeal，未出现在 PIBImphal 的词图（见 **图 9.11**）中，在 **图 9.14** 中出现了。这表明词干提取和词形还原有助于提高词汇计数。

### 9.7.5 改进 BoW – TF-IDF

到目前为止，我们已通过移除停用词创建了词标记，并使用词频计数来可视化数据。在 第 9.6.1 节 中，我们了解了使用计数向量的潜在问题，并讨论了创建词频-逆文档频率（TF-IDF）作为可能的解决方案。在一个文档集合中（此处为 `screenName`），TF-IDF 试图识别对某个文档（用户/`screenName`）重要的词。让我们实现 TF-IDF 概念。**表 9.21** 显示了按 `screenName` 的词计数。

![](img/page379-01.png)

在这里，我们将 `screenName` 类似于一个文档（如 第 9.6.1 节 中所讨论的）。同一用户（`screenName`）的多个推文会创建多个 `IDs`。在后面的章节中，我们将使用 ‘`covid_twitter_df`’ 的 `ID` 列来表示一个文档。由此创建的 `twitter_words_tf` 数据框共有 3,562 个唯一词，由 1,204 个唯一用户发布。

![](img/page379-02.png)![](img/page379-03.png)![](img/page380-01.png)

让我们再创建一个特征，显示用户在推文中使用的总词数。**表 9.22** 显示了下面代码片段的结果。

![](img/page380-02.png)

**表 9.22** 的每一行代表一个用户-词组合，其中 `n` 表示用户使用该词的次数，`total_words_user` 表示用户使用的总词数。我们可以将词频计算为 `n/total_words_user`。然而，我们有来自 `tidytext` 包的 `bind_tf_idf()` 函数，它可以给出词频和逆文档频率。**表 9.23** 显示了每个标记的 TF-IDF。

![](img/page380-03.png)![](img/page380-04.png)![](img/page380-05.png)

在下面的代码片段中，我们使用 公式 (9.2) 计算了词 ‘death’ 的 IDF，其值与 **表 9.23** 中提到的一致。

![](img/page381-01.png)

让我们选取有多个推文（推文总词数超过 100）的用户并了解他们使用的词。从该用户列表中，我们将为每个用户选择前七个词。数据可按以下步骤准备：

使用 `twitter_word_tf` 数据框：

– 筛选总词数超过 100 的推文。使用 `filter()` 函数实现此操作。

– 使用 thee `slice_max()` 为每个用户选择前七条记录

– 使用 `ungroup()` 对数据取消分组。

– 使用 `arrange()` 按 `screenName` 和词计数排列数据。

– 创建一个名为 `order` 的列，用于跟踪之前步骤中完成的顺序/排列。

**表 9.24** 显示了使用上述步骤获得的用户子集。

![](img/page381-02.png)![](img/page382-01.png)

TF-IDF 的好处从 **表 9.24** 中可见。在组（`screenName`）内，我们有一些计数较少但 TF-IDF 值较高的词。**图 9.15** 显示了来自 **表 9.24** 的数据的图。

![](img/page382-02.png)

将 **图 9.15** 与 **图 9.14** 进行比较，我们注意到作为高频词被选出的词有一些变化。

**1.** 从 **图 9.14** 可以看出，对于用户 BaharBharat，‘Flights, International, October, Operated, Important’ 等词成为前五名词。然而，对于 **图 9.15** 中的同一用户，我们看到 ‘flight, international, operation, travel, announcement’ 被显示为前五名词。

![](img/page383-01.png)

**2.** 从 **图 9.14** 可以看出，对于用户 PIBImphal，前五名词为 ‘follow, ukhrul, people, baptist, church。 然而，对于 **图 9.15** 中的同一用户，‘ukhrul, baptist, church, pastor, appeal’ 是前五名词。由于 ‘follow’ 是一个常见词，可能被多个用户多次使用，其 TF-IDF 值会被抵消，这就是它被剔除出列表的原因。

### 9.7.6 改进 BoW – 使用 n-grams

迄今为止的分析单独使用了每个标记或词。但某些词的含义可能取决于其前后的词，例如 ‘not happy’。它应被视为一个特征，而不是两个不同的特征。`n`-gram 是 `n` 个词的连续序列。当两个连续词被视为一个特征时，称为二元词组；三个连续词称为三元词组，以此类推（Pradhan and Kumar, 2019）。我们将使用 `unnest_token()` 创建二元词组。请注意，在创建二元词组时，我们未使用词干提取和词形还原的概念。**表 9.25** 显示了下面代码的输出。

**表 9.25** | 二元词组

| `screenName` || `bigram` |
| --- | --- |
| ____alpha96 || i think |
| --- | --- |
| ____alpha96 || think i |
| ____alpha96 || i just |
| ____alpha96 || just drew |
| ____alpha96 || drew the |
| ____alpha96 || the future |
| ____alpha96 || future is |
| ____alpha96 || is it |
| ____alpha96 || it or |
| _ashoka_tech || hope agrees |

词干提取、词形还原以及作为词计数度量的 TF-IDF 可能会显著改善 **BoW 表示** 并有助于可视化重要词。

**表 9.26** | 去除停用词后的二元词组

| `screenName` || `Bigram` |
| --- | --- |
| _ashoka_tech || hope agrees |
| --- | --- |
| _ashoka_tech || awarded hope |
| _ashoka_tech || hope agrees |
| _ashoka_tech || hope agrees |
| _ashoka_tech || hope agrees |
| _sunnyrai || cover spike |
| 03Rajak || fight coro |
| 03Rajak || simple steps |
| 03Rajak || steps wear |
| 03Rajak || mask wash |

我们创建了二元词组，但它们包含停用词。我们将进行额外处理以移除停用词并重新创建二元词组。我们将按以下步骤进行：

使用中间二元词组

– 将二元词组拆分为两个词。这可以使用 `tidyr` 中的 `separate()` 完成。

– 使用 `tidy-text` 中的 `stop_words` 词表从拆分的词中移除停用词。

– 将两个词合并再次形成二元词组。这可以使用 `tidyr` 中的 `unite()` 完成。

**表 9.26** 显示了使用上述步骤得到的结果。

![](img/page385-01.png)

**表 9.27** | 频繁使用的二元词组

| `bigram` || `n` |
| --- | --- |
| active recovered || 105 |
| --- | --- |
| wash hands || 82 |
| social distancing || 81 |
| recovery rate || 67 |
| jan andolan || 66 |
| preventive measures || 64 |

### 9.7.7 可视化二元词组



## 二元组分析

让我们获取出现次数至少为 20 的二元组的计数并绘制它（表 9.27）。

![](img/page386-01.png)

从图 9.16 中，我们可以看到

**1.** 诸如恢复率、洗手、社交距离和预防措施之类的词语在许多推文中都被提及。

**2.** 部分推文还提到了节日季、心理健康、十月和稳定。

到目前为止，我们已经多次按每个用户（`screenName`）分析了词语。我们也将对二元组做同样的处理。让我们获取拥有多条推文（推文中的总词数超过 100）的用户（`screenName`），并了解他们使用的二元组。数据可通过以下步骤准备：

使用 `twitter_bigram` 数据框：

– 选择 `screenName` 和 `word` 列，并使用 `count()` 获取所有词语的计数。

– 使用 `group_by()` 按 `screenName` 对数据进行分组。

– 创建一个新列来存储用户撰写的总词数。这可以通过 `mutate()` 实现。

– 创建一个新列来存储二元组的 IDF 和 TF-IDF。这可以通过 `bind_tf_idf()` 实现。

– 筛选总词数超过 100 的推文。使用 `filter()` 函数来实现。

– 使用 `slice_max()` 为每个用户选择前七条记录。

– 使用 `ungroup()` 对数据进行取消分组。

– 使用 `arrange()` 按 `screenName` 和词语计数排列数据。

![](img/page387-01.png)

– 创建一个名为 `order` 的列，用于跟踪之前步骤中完成的顺序/排列。

让我们使用计数和 TF-IDF 按用户绘制二元组。

![](img/page387-02.png)![](img/page388-01.png)

表 9.28 显示了基于计数（`n`）的前七条记录。

![](img/page388-02.png)

图 9.17 显示了基于频率（变量 `n`）的每个用户的前七条记录的计数。

![](img/page388-03.png)

表 9.29 显示了基于 TF-IDF 的前七条记录。

![](img/page388-04.png)![](img/page389-01.png)![](img/page389-02.png)

来自表 9.29 的数据的图表显示在图 9.18 中。

![](img/page389-03.png)![](img/page390-01.png)![](img/page390-02.png)

比较图 9.17 和 9.18，我们可以看到对于少数用户，二元组的顺序发生了变化，但整体列表保持不变。TF-IDF 似乎对二元组没有影响，因为两个用户（`screenName`）使用相同的两个词以相同顺序组合发推的情况很少见。因此，二元组的计数可能不会因其他用户（`document`）使用相同二元组的频率而被抵消。

## 9.7.8 计数向量 vs. 带词干提取和词形还原的计数向量 vs. TF-IDF 向量

计数向量、带词干提取和词形还原的计数向量以及 TF-IDF 向量是创建 BoW 模型中词嵌入的三种不同方法。这三种衡量词语重要性的方法最终有助于为文档创建词向量。文档中词语的排名会根据所选的度量而变化。让我们深入研究用户‘PIBImphal 的推文。对于 PIBImphal，`twitter_word_count`、`twitter word stem count`和`twitter word tf count`中的词数为 551。对于 PIBImphal，让我们比较表 9.30 和 9.31：

**1.** 未进行词干提取和词形还原的表 9.30 显示‘church’和‘urges’是按`n`排序的前六条记录中的两个词。

**2.** 进行词干提取和词形还原的表 9.31 显示‘appeal’和‘minist’是按`n`排序的前六条记录中的两个词。

![](img/page391-01.png)![](img/page391-02.png)![](img/page391-03.png)![](img/page392-01.png)

词干提取和词形还原过程将词语

**1.** ‘appeals’和‘appealed’还原为其词根形式‘appeal’，从而增加了‘appeal’的计数。

**2.** ‘minister’和‘ministers’还原为其词根形式‘minist’，因此计数为八。

这导致表 9.30 中的最后两条记录被剔除，并清楚地表明了词语排序可能因词干提取和词形还原而发生变化。

使用 TF-IDF 有助于提取在同一主题上发推的用户集合中特定用户（`screenName`）的特征词。为了验证该说法，让我们比较表 9.30 和 9.32：

**1.** 未进行词干提取和词形还原的表 9.30 显示‘follow’和‘peopl’是按`n`排序的前七条记录中的两个词。

**2.** 进行词干提取和词形还原并加上 TF-IDF 的表 9.32 显示‘church’和‘pastor’是按`n`排序的前七条记录中的两个词。

基于 TF-IDF，我们可以在表 9.32 中看到‘church’和‘pastor’等词，这在 PIBImphal 的推文中更相关，而‘follow’和‘people’等词可能已被语料库中的许多用户使用。在表 9.30 中，计数为 13 的‘follow’未能进入表 9.32 中的前七条记录。与此同时，仅有六次计数的‘pastor’在表 9.32 中排名高于 minist（表格按 TF-IDF 升序排序）。

![](img/page392-02.png)

BoW 有其自身的缺点，但它是可视化文本数据的一种有用方法。BoW 模型还可以帮助构建基础的预测模型（将在后面的章节讨论）。然而，让我们继续进行关于 twitter 数据的最后一个查询。

## 9.7.9 推文的信息来源是什么？

我们可以通过提取文本中的 URL 并进行某些预处理来获取此信息。让我们尝试了解推特用户在他们使用的 hashtags 下的信息来源。由于我们将从 `tokens` 中过滤掉 URL，因此可以删除用于清理文本的 `regex`。

![](img/page392-03.png)

表 9.33 | 计数大于 8 的 URL

| `short_url` || `n` |
| --- | --- |
| [`t.co/QdOXQvzaPw`](https://t.co/QdOXQvzaPw) || 95 |
| --- | --- |
| [`t.co/ZaoOX3zu8V`](https://t.co/ZaoOX3zu8V) || 65 |
| [`t.co/PifpGVT6aq`](https://t.co/PifpGVT6aq) || 60 |
| [`t.co/M7AtMQCb4X`](https://t.co/M7AtMQCb4X) || 40 |
| [`t.co/ThENRZufhO`](https://t.co/ThENRZufhO) || 37 |
| [`t.co/4wc8k5IK4Z`](https://t.co/4wc8k5IK4Z) || 29 |
| [`t.co/lz6nVuk49T`](https://t.co/lz6nVuk49T) || 26 |
| [`t.co/ATU35sj129`](https://t.co/ATU35sj129) || 18 |
| [`t.co/4ZLdC85LU0`](https://t.co/4ZLdC85LU0) || 17 |
| [`t.co/4tQTPmvkfZ`](https://t.co/4tQTPmvkfZ) || 16 |
| [`t.co/PQHKrABmiZ`](https://t.co/PQHKrABmiZ) || 13 |
| [`t.co/WZpI4l9ECd`](https://t.co/WZpI4l9ECd) || 11 |
| [`t.co/CdH9aoQMzJ`](https://t.co/CdH9aoQMzJ) || 9 |
| [`t.co/CwXmsvrZHA`](https://t.co/CwXmsvrZHA) || 9 |
| [`t.co/izIfYcXdwh`](https://t.co/izIfYcXdwh) || 9 |
| [`t.co/kF2gyMK8qK`](https://t.co/kF2gyMK8qK) || 9 |
| [`t.co/NTYXhRNfkD`](https://t.co/NTYXhRNfkD) || 9 |
| [`t.co/3xeX1j11z4`](https://t.co/3xeX1j11z4) || 8 |
| [`t.co/HIQ3LxCpJf`](https://t.co/HIQ3LxCpJf) || 8 |
| [`t.co/WRggJbZOda`](https://t.co/WRggJbZOda) || 8 |

我们将过滤出计数超过八的 `url_tokens`，并使用 `httr` 包提取实际的 URL 链接。表 9.33 显示了计数超过八的 URL。

![](img/page393-01.png)



表 9.33 中的短网址可以使用下面的代码片段进行展开。表 9.34 显示了展开后的网址。

![](img/page393-02.png)

表 9.34 | 展开 URL 的前六个观测值

| `url` || `status_code` |
| --- | --- |
| [`twitter.com/MoHFW_INDIA/status/1316278631321100289/photo/1`](https://twitter.com/MoHFW_INDIA/status/1316278631321100289/photo/1) || 400 |
| --- | --- |
| [`twitter.com/mygovindia/status/1316602805818257410/photo/1`](https://twitter.com/mygovindia/status/1316602805818257410/photo/1) || 400 |
| [`twitter.com/mygovindia/status/1315610983793008640/photo/1`](https://twitter.com/mygovindia/status/1315610983793008640/photo/1) || 400 |
| [`twitter.com/mygovindia/status/1315616867776491520/photo/1`](https://twitter.com/mygovindia/status/1315616867776491520/photo/1) || 400 |
| [`twitter.com/mygovindia/status/1316596832928055297/photo/1`](https://twitter.com/mygovindia/status/1316596832928055297/photo/1) || 400 |
| [`twitter.com/MoHFW_INDIA/status/1317424639295909888/photo/1`](https://twitter.com/MoHFW_INDIA/status/1317424639295909888/photo/1) || 400 |

让我们将 URL 链接与短网址绑定。表 9.35 显示了短网址和对应的 URL 链接。

![](img/page394-01.png)

我们将从 URL 链接中提取域名并统计域名。前面章节中解释的 `gsub()` 和 `regex` 的使用将被用来提取 URL 链接。表 9.36 显示了域名及其出现的次数。

![](img/page394-02.png)

### 9.7.10 可视化 URL

图 9.19 使用 `ggplot` 显示了推文中常见域名的图表。

![](img/page394-03.png)![](img/page394-04.png)

表 9.36 | 域名计数

| `domain` || `domain_count` |
| --- | --- |
| twitter.com || 448 |
| --- | --- |
| pledge.mygov.in || 24 |
| livemint.com || 16 |
| blog.mygov.in || 8 |

![](img/page395-01.png)

图 9.19 显示在大多数情况下，推文的信息链接到 Twitter 源本身。我们可能还想了解用户在转发时使用的 hashtags。我们留给读者自行尝试。

## 9.8 情感分析

在创建了 `BoW` 模型并理解了基本的词嵌入之后，让我们深入探讨文本分析中另一个感兴趣的话题。用户对特定主题的情感备受关注。在本例中，我们想了解用户对与 COVID-19 相关主题的情绪。通过人工阅读，可以阅读推文并了解用户反映的情绪。它可能是一条正面/负面推文或快乐/中性/悲伤推文等。但对于人类来说，阅读所有推文并标记推文以反映情感意图将是令人难以承受的。

`tidytext` 附带内置词典（可通过 `textdata` 包获得），可帮助将推文分类为预定义的情感标签之一。`tidytext` 中的四个通用词典如下：

1. `Afinn` – 该词典来自 Finn Årup Nielsen（Nielsen, 2011），将 2,477 个唯一的 unigram 按 −5（负面情感）到 5（正面情感）的分数进行分类。它采用开放数据库许可（ODbL）v1.0 许可。表 9.37 显示了 afinn 词典中的六个观测值。

![](img/page395-02.png)

表 9.37 | afinn 词典中的前六个观测值

| `Word` || `value` |
| --- | --- |
| Abandon || −2 |
| --- | --- |
| Abandoned || −2 |
| abandons || −2 |
| abducted || −2 |
| abducted || −2 |
| abducted || −2 |

表 9.38 | nrc 词典中的前六个词

| `Word` || `sentiment` |
| --- | --- |
| abacus || trust |
| --- | --- |
| abandon || fear |
| abandon || negative |
| abandon || sadness |
| abandoned || anger |
| abandoned || fear |

1. `Nrc` – 该词典来自 Saif Mohammad 和 Peter Turney（2013），将词语归类到 ‘trust’、‘fear’、‘negative’、‘sadness’、‘anger’、‘surprise’、‘positive’、‘disgust’、‘joy’ 和 ‘anticipation’ 等标签下。它是最全面的，已将 6,468 个 unigram 归类到这些标签下。一个词可以映射到多个标签。该数据集需要商业使用许可。表 9.38 显示了 nrc 词典中的六个观测值。

![](img/page396-01.png)

2. `Bing` – 该词典来自 Bing Liu（2015）及其合作者，以二元方式对词语进行分类，即 positive/negative，即两个唯一标签。它已将 6,783 个 unigram 归类到这些标签下。默认情况下，只有该词典作为 `tidytext` 的一部分可用。表 9.39 显示了 bing 词典的六个观测值（S Biguzzi, 2020）。

![](img/page396-02.png)

3. `lougharn` – 该词典来自 Loughran-McDonald（2019），将词语归类到 ‘negative’、‘positive’、‘uncertainty’、‘litigious’、‘constraining’ 和 ‘superfluous’ 等标签下。该词典已将 3,917 个英语单词归类到这些情感意图下。词语可能映射到多个标签下。该词典需要商业使用许可。表 9.40 显示了 lougharn 词典的六个观测值。

![](img/page396-03.png)

我们需要安装 `textdata` 包以访问 ‘afinn’、‘nrc’ 和 ‘lougharn’ 词典。`get_sentiments()` 函数内部使用 `textdata::lexicon_afinn()`、`textdata::lexicon_nrc()`、`textdata::lexicon_loughran()` 下载这些词典并使其可用。上述所有词典均由词典作者使用众包平台构建和验证。使用这些词典的优点是我们能快速从语料中得出情感。缺点是如果语料的写作风格非常不同（例如，一本 100 年前的书，我们使用上述词典来判断书中表达的情感），情感的准确性可能值得怀疑。

表 9.39 | bing 词典中的前六个词

| `Word` || `sentiment` |
| --- | --- |
| 2-faces || negative |
| --- | --- |
| abnormal || negative |
| abolish || negative |
| abominable || negative |
| abominably || negative |
| abominate || negative |

表 9.40 | lougharn 词典中的前六个词

| `Word` || `sentiment` |
| --- | --- |
| abandon || negative |
| --- | --- |
| abandoned || negative |
| abandoning || negative |
| abandonment || negative |
| abandonments || negative |
| abandons || negative |

这些词典基于 unigram，因此情感处于 unigram 层级。推文（表示为 `BoW`）的情感可以通过组合 unigram 的情感得出。我们将使用 ‘nrc’ 词典对 covid 数据进行情感分析。我们将了解用户（`screenName`）表达的情感，这些用户多次发布推文，每条推文 50 到 100 个词。来自 第 9.7.3 节 的 ‘`twitter_word_count`’ 对象包含使用 `unnest_token()` 创建的 unigram。表 9.41 显示了推文词数在 50 到 100 之间的用户的前 20 行。

![](img/page397-01.png)![](img/page397-02.png)

推文情感 df 中有 45 个唯一用户。

![](img/page398-01.png)

让我们获取用户的情绪。`nrc` 词典中的标签如下：‘trust’、‘fear’、‘negative’、‘sadness’、‘anger’、‘surprise’、‘positive’、‘disgust’、‘joy’ 和 ‘anticipation’。让我们查看反映 ‘sadness’ 的推文，我们将按照以下步骤进行：

1. 从 ‘nrc’ 词典中获取反映 sadness 的词语并将其存储在变量 ‘`nrc_sad`’ 中。



**2.** 对 `tweet_sentiment_df` 执行 `inner_join` 与 `nrc_sad` 并统计反映悲伤情绪的词。

下面代码将用于应用上述步骤。

![](img/page398-02.png)

`tweet_sad` 的维度表明只有 41 个词与 `nrc` 词表中的悲伤情绪相匹配。

![](img/page398-03.png)

**表 9.42** 显示前 10 个词。

![](img/page398-04.png)![](img/page398-05.png)

### 预建词典
`Pre-built dictionaries` 可以显著减少执行情感分析时对数据标注的人工干预。通过 `tidytext` 和 `textdata` 包提供的词典如 `Afinn`、`Bing`、`Nrc`，可用于理解文本信息中表达的情感。

**表 9.43** | 来自修改后停用词词表的首次 10 条观测

| 词 || 词表 |
| --- | --- |
| music || custom |
| --- | --- |
| feeling || custom |
| lowest || custom |
| a || SMART |
| a’s || SMART |
| able || SMART |
| about || SMART |
| above || SMART |
| according || SMART |
| accordingly || SMART |

使用 `nrc` 词表，我们可以分析文本中由词定义的任何情感商数。我们鼓励读者更改上述代码片段以尝试 ‘anger’、surprise’ 和 ‘positive’ 等情绪。从 **表 9.42** 中，我们可以看到在推文中反映悲伤情绪的用户（`screenName`）。

**1.** 诸如 negative、evil、lowest、accident、hospital 等词出现在推文中并反映悲伤情绪。

**2.** 我们还看到诸如 music、feeling、lowest 等词出现在推文中，在 covid 数据的上下文中这些词可能并非悲伤情绪。

处理情绪分类错误的词的一种方法如下：

**1.** 将此类词添加到 `stop_words` 词表中。

**2.** 执行 `anti_join()` 将其从 `unigram` 中移除。

**3.** 再次使用情感词表执行 `inner_join()`。

下面的代码显示了将某些词添加到 `stop_words` 词表中的步骤。**表 9.43** 显示了来自自定义 `stop_words` 词表的 top 10 条观测。

![](img/page399-01.png)

### 9.8.1 使用词表进行情感分析 – Bing
有时，我们可能有兴趣了解用户推文是否反映总体正面情感或负面情感，而非通过词来理解特定情绪。我们可以使用 `bing` 词表来获取正面或负面情感。需遵循的步骤如下：

**1.** 获取推文中每个词的情感得分（`tweet_sentiment_df`）。这可以通过使用 `bing` 词表进行 `inner_join` 来完成。**表 9.44** 显示了此步骤的输出。

![](img/page399-02.png)![](img/page400-01.png)![](img/page400-02.png)

**2.** 统计每个用户的正面和负面情感。下面的代码生成了 **表 9.45** 中显示的输出。

![](img/page400-03.png)

**3.** 从 **表 9.45** 中，将正面和负面情感计数分离到单独的列中。这可以使用 `spread()` 来完成。然后，计算每个用户的 `overall_sentiment`（正面-负面）。我们可以使用 `mutate()` 来实现。下面的代码将有助于应用此步骤。

![](img/page400-04.png)![](img/page401-01.png)

**表 9.46** 显示了上述代码片段得到的前十条观测。

![](img/page401-02.png)

尽管原始数据框 `tweet_sentiment_df` 有 45 个用户，`tweet_sentiment_bing` 仅显示 42 个唯一用户。可能剩余三位用户的推文中使用的词与 `bing` 词表中的任何词都不匹配。**表 9.46** 中的 `overall_sentiment` 列是用户在其推文中使用的正面词和负面词之间的差值。

**1.** `overall_sentiment` 的正值意味着推文表达了正面情感。

**2.** 计数为零意味着推文为中性。

**3.** 负值意味着推文表达了负面情感。

让我们绘制整体情感。

![](img/page401-03.png)![](img/page402-01.png)

从 **图 9.20** 可以看出，大多数政府的官方 twitter 账号反映出正面情感。这些账号使用的词可能更多是疫情期间需要遵循的预防措施、指南和补救措施，因此它们可能被标记为正面情感。有趣的是，`tb9gujarati`、`LogicalIndians` 的推文被标记为反映负面情感的推文。

让我们生成词云以了解推文中反映正面和负面情感的词。这可以通过以下步骤完成：

**1.** 对 `tweet_sentiment_df` 与 `bing` 词表执行 `inner join`。

**2.** 使用 `count()` 函数统计词和情感。

![](img/page403-01.png)

**表 9.47** 显示了上述步骤的结果。

![](img/page403-02.png)

我们可以使用 `wordcloud` 包中的 `comparison.cloud()` 来可视化来自 **表 9.47** 的正面和负面词。然而，该函数需要一个词频矩阵作为输入，其行代表词，其列代表文档（正面和负面词的计数）。为了将 `sentiment_word_cloud` 转换为 `term.matrix`，我们将使用 reshape 包中的 `acast`/`dcast` 方法。`acast()` 与 `tidyr` 中的 `spread()` 函数类似，但也可以处理矩阵/数组（而 `spread` 不能）。**表 9.48** 显示了使用 `acast()` 后的结果。

![](img/page403-03.png)![](img/page403-04.png)

在上面的代码片段中，`~` 左侧的参数，即 `word`，指的是 ID 变量，而 `~` 右侧的参数（`sentiment`）指的是要展开为列名的变量。要展开的值在变量 `n` 中（value.var=`"n"`）。现在我们可以使用 `comparison.cloud()` 来可视化正面和负面词。

![](img/page404-01.png)

**图 9.21** 显示了推文中使用的负面词以黑色字体显示（上半部分）以及正面词以灰色字体显示（下半部分 **图 9.21** 的下半部分）。推文中词的频率越高，文本大小越大。`Decline` 在 covid 数据的上下文中可能不是一个负面词，但由于英语中该词的一般用法，它被显示为负面词。

### 9.8.2 情感 – Bing vs. Nrc vs. Affin
在所有可用的词表中，我们如何决定使用哪一个进行情感分析？我们可以使用全部三种来比较结果。最终的选择可能在验证三个词表的情感得分不同后进行。下面的代码块使用了上一节中的 `bing` 词表。**表 9.49** 显示了使用 `bing` 的情感得分。

![](img/page404-02.png)

**表 9.49** | 使用 Bing 的前 10 位用户及其情感得分

| 用户名 || Bing 情感得分 |
| --- | --- |
| arupwharton || 0 |
| --- | --- |
| CovidPlasmaIn || 1 |
| DistrictAdm_FBD || 0 |
| Drmubl || 2 |
| Esichq || −1 |
| FOBKeonjhar || 2 |
| FOBSrinagar || 6 |
| FOBUdhampur || 8 |
| HealthwireMedia || 4 |
| IndBloodDonors || 2 |

*注意：* 正值反映正面情感，负值反映负面情感，零值反映中性情感。

![](img/page405-01.png)



我们可以使用 `nrc` 在与 `bing` 词典类似的基础上创建情感得分。下面的代码用于使用 `nrc` 生成 **表 9.50** 的情感得分。

![](img/page405-02.png)

**表 9.50** | 前 10 名用户及使用 nrc 的情感得分

| `screenName` || `sentiment_nrc` |
| --- | --- |
| arupwharton || −2 |
| --- | --- |
| CovidindiaO || 1 |
| CovidPlasmaIn || 1 |
| DistrictAdm_FBD || 0 |
| drmubl || 3 |
| esichq || 6 |
| FOBKeonjhar || 4 |
| FOBSrinagar || 3 |
| FOBUdhampur || 5 |
| HealthwireMedia || 8 |

*注：* 正值反映积极情感，负值反映消极情感，零值反映中性情感。

**表 9.51** | 前 10 名用户及使用 afinn 的情感得分

| `screenName` || `sentiment_afinn` |
| --- | --- |
| arupwharton || −2 |
| --- | --- |
| CovidindiaO || 1 |
| CovidPlasmaIn || 3 |
| DistrictAdm_FBD || −1 |
| Drmubl || 8 |
| Esichq || 0 |
| FOBKeonjhar || 4 |
| FOBSrinagar || 6 |
| FOBUdhampur || 10 |
| HealthwireMedia || 6 |

*注：* 正值反映积极情感，负值反映消极情感，零值反映中性情感。

使用 `afinn` 的 **表 9.51** 进行情感分析。注意，由于 affin 词典中的情感得分是数值尺度，我们未使用 `spread()` 和 `mutate()`。

![](img/page406-01.png)

我们将合并由 `bing`、`nrc` 和 `afinn` 获得的情感得分以创建 **表 9.52。**

![](img/page406-02.png)![](img/page406-03.png)

**表 9.52** 显示了使用三种词典的情感得分。**图 9.22** 显示了来自 **表 9.52** 的 affin 得分的图表。如果比较三个得分，`nrc` 和 `bing` 对于用户似乎给出相似的情感（积极或消极）。然而，`afinn` 情感与 `nrc` 或 `bing` 不同的情况也存在。我们可以使用任一得分来获取用户的情感。另一种选择是使用投票机制（类似于集成技术）并得出综合得分和情感。我们鼓励读者尝试投票策略来汇总三种词典的结果并绘制图表。

![](img/page407-01.png)![](img/page407-02.png)

## 9.9 | 使用否定词的情感分析

在上一节中，我们通过统计积极和消极词来得出情感。然而，统计单个词的一个缺点是，单独的词可能无法传达积极或消极的情感。

**1.** 我不高兴 – 如果以 unigram 方式查看这些词，这句话可能传达积极情感。然而，‘not happy’ 意味着消极情感。

处理此类情感的一种方法是查看 n-gram（bigrams/tri-grams）以得出情感得分。我们已在 第 9.7.6 节 中创建了 bigrams（`separated_bigram` 变量）。让我们查看所有以 ‘not’ 开头的词。

![](img/page408-01.png)

从 **表 9.53** 可以看出，与 not 一起使用最常见的词是 ‘discriminate’、‘over’、‘forget、‘attend 等。我们还看到表中出现了 `stop_words`（如 like、to、a 等），但它们不传达情感。让我们使用 AFINN 词典来识别由否定词（‘not、‘no、‘never、‘without、‘dont’）引导并传达情感的词。**表 9.54** 显示了词及其情感得分。当然，这些情感得分需要相反地解释。负分表示积极情感，正分表示消极情感。

![](img/page408-02.png)

从 **表 9.54** 可以看出，与 not 关联最常见的词是 forget，实际上它应该得分为 +1（因为它前面有 ‘not’）。我们可以计算一个词在错误方向上的贡献程度。我们将 **表 9.54** 中的 `value` 和 `n` 列相乘以得到贡献。贡献直观上表明，一个值为 +2 且出现五次的词与一个情感值为 + 1 且出现 10 次的词具有相同的[content]
我们可以使用 `nrc` 在与 `bing` 词典类似的基础上创建情感得分。下面的代码用于使用 `nrc` 生成 **表 9.50** 的情感得分。

![](img/page405-02.png)

**表 9.50** | 前 10 名用户及使用 nrc 的情感得分

| `screenName` || `sentiment_nrc` |
| --- | --- |
| arupwharton || −2 |
| --- | --- |
| CovidindiaO || 1 |
| CovidPlasmaIn || 1 |
| DistrictAdm_FBD || 0 |
| drmubl || 3 |
| esichq || 6 |
| FOBKeonjhar || 4 |
| FOBSrinagar || 3 |
| FOBUdhampur || 5 |
| HealthwireMedia || 8 |

*注：* 正值反映积极情感，负值反映消极情感，零值反映中性情感。

**表 9.51** | 前 10 名用户及使用 afinn 的情感得分

| `screenName` || `sentiment_afinn` |
| --- | --- |
| arupwharton || −2 |
| --- | --- |
| CovidindiaO || 1 |
| CovidPlasmaIn || 3 |
| DistrictAdm_FBD || −1 |
| Drmubl || 8 |
| Esichq || 0 |
| FOBKeonjhar || 4 |
| FOBSrinagar || 6 |
| FOBUdhampur || 10 |
| HealthwireMedia || 6 |

*注：* 正值反映积极情感，负值反映消极情感，零值反映中性情感。

使用 `afinn` 的 **表 9.51** 进行情感分析。注意，由于 affin 词典中的情感得分是数值尺度，我们未使用 `spread()` 和 `mutate()`。

![](img/page406-01.png)

我们将合并由 `bing`、`nrc` 和 `afinn` 获得的情感得分以创建 **表 9.52。**

![](img/page406-02.png)![](img/page406-03.png)

**表 9.52** 显示了使用三种词典的情感得分。**图 9.22** 显示了来自 **表 9.52** 的 affin 得分的图表。如果比较三个得分，`nrc` 和 `bing` 对于用户似乎给出相似的情感（积极或消极）。然而，`afinn` 情感与 `nrc` 或 `bing` 不同的情况也存在。我们可以使用任一得分来获取用户的情感。另一种选择是使用投票机制（类似于集成技术）并得出综合得分和情感。我们鼓励读者尝试投票策略来汇总三种词典的结果并绘制图表。

![](img/page407-01.png)![](img/page407-02.png)

### 9.9 | 使用否定词的情感分析

在上一节中，我们通过统计积极和消极词来得出情感。然而，统计单个词的一个缺点是，单独的词可能无法传达积极或消极的情感。

**1.** 我不高兴 – 如果以 unigram 方式查看这些词，这句话可能传达积极情感。然而，‘not happy’ 意味着消极情感。

处理此类情感的一种方法是查看 n-gram（bigrams/tri-grams）以得出情感得分。我们已在 第 9.7.6 节 中创建了 bigrams（`separated_bigram` 变量）。让我们查看所有以 ‘not’ 开头的词。

![](img/page408-01.png)

从 **表 9.53** 可以看出，与 not 一起使用最常见的词是 ‘discriminate’、‘over’、‘forget、‘attend 等。我们还看到表中出现了 `stop_words`（如 like、to、a 等），但它们不传达情感。让我们使用 AFINN 词典来识别由否定词（‘not、‘no、‘never、‘without、‘dont’）引导并传达情感的词。**表 9.54** 显示了词及其情感得分。当然，这些情感得分需要相反地解释。负分表示积极情感，正分表示消极情感。

![](img/page408-02.png)

从 **表 9.54** 可以看出，与 not 关联最常见的词是 forget，实际上它应该得分为 +1（因为它前面有 ‘not’）。我们可以计算一个词在错误方向上的贡献程度。我们将 **表 9.54** 中的 `value` 和 `n` 列相乘以得到贡献。贡献直观上表明，一个值为 +2 且出现五次的词与一个情感值为 + 1 且出现 10 次的词具有相同的冲击力。**表 9.55** 显示了每个词的贡献。

![](img/page408-03.png)![](img/page409-01.png)![](img/page409-02.png)![](img/page409-03.png)![](img/page410-01.png)

**图 9.23** 可视化了具有否定方面的词的情感。

![](img/page410-02.png)

## 9.10 | 文档词矩阵

在所有之前的章节中，我们以表格格式处理和排列文本，使得它为“每个文档一个词元（这里是用户/`screenName` 的推文）每行一行”。这样做的好处是可以快速汇总和可视化文本数据以及进行情感分析。然而，数据的这种表格结构可能与在数据上应用其他 NLP 模型的包不兼容。

文本挖掘包最常用的结构之一是文档-词矩阵（或 DTM）。DTM 矩阵具有以下结构（Silge and Robinson, 2017）：

**1.** 每一行代表一个文档（例如用户/`screenName` 的推文）。

**2.** 每一列代表一个词元（unigram/bigram 等）。

**3.** 每个值（通常）包含该词在该文档中出现的次数。

该结构与 第 9.6.1 节 中的 **表 9.5** 和 **9.6** 完全相同。直观上，我们可以想象 DTM 将是一个稀疏矩阵，即文档和词的大多数配对的值为零。然而，不同的包以高效的方式创建 DTM。`cast()` 来自 tidytext 包可用于将前几节的表格数据转换为 DTM 格式。Tidytext 提供了三种 cast 函数变体：

**1.** `cast_sparse()` – 转换为可与 `Matrix` 包一起使用的稀疏矩阵。

**2.** `cast_dtm()` – 转换为可用于 `tm` 包操作的 DTM 对象。

**3.** `cast_dfm()` – 转换为可与 `quanteda` 包一起工作的文档特征矩阵（DFM）对象。DFM 只是 DTM 的另一个名称。

给定一个 DTM，tidytext 还提供了 `tidy()` 函数，该函数将 DTM 转换为表格格式（每个文档每个词元一行），以便轻松汇总和可视化数据。

我们将使用 `cast()` 创建 DTM 并将其与原始推文数据框 `covid_twitter_df` 合并。在创建 DTM 并合并之前，需要注意以下几点：

**1.** 我们将创建 `twitter_word` 数据框，如 第 9.7.2 节 所做。然而，在执行文本预处理时，它将不会删除转发。

**2.** 而不是使用 `screenName` 作为文档 ID 的同义词，我们将创建 `doc_id` 来跟踪各个推文。

将 `screenName` 作为文档 ID 在所有之前的章节中都不是问题，因为我们希望在 `screenName` 级别对用户进行汇总、可视化和情感分析。让我们从 DTM 角度理解为什么第二点变得重要。`covid_twitter_df` 显示在 **表 9.56** 中。

![](img/page411-01.png)![](img/page411-02.png)![](img/page412-01.png)



根据 **表 9.56**，我们可以看到 `screenName` 为 ‘MoHFW_INDIA’ 的推文有两条。如果我们使用 `screenName` 作为文档 ID，那么在创建 `DTM` 时，这两条推文的文本将被显示在同一个文档 ID 下。由于我们希望将 `DTM` 合并回 `covid_twitter_df`，因此我们希望将这两条推文视为两个不同的文档。于是创建了一个新的指标 `doc_id` 的原因。下面代码创建了一个名为 `doc_id` 的新变量。**表 9.57** 显示了下面代码片段的带有 `doc_id` 的数据框。

![](img/page412-02.png)

以下代码片段对 **表 9.57. 表 9.58** 的 `text` 列应用文本处理步骤。**表 9.58** 显示了以下代码的结果表。

![](img/page412-03.png)![](img/page413-01.png)![](img/page413-02.png)

请注意，通常通过 hashtags 或非英语单词或任何正则表达式删除推文，可能会导致某些推文的完整文本数据被删除（也许某些用户只发布了 hashtags 或非英语单词）。根据 **表 9.57**，我们看到观察编号 25,492，其中 `text` 列只有 hashtags 和 URL。总的来说，在 `new_covid_twitter_df` 中，`remove_hashtag_regex` 和 `remove_non_english_regex` 删除了 240 条推文。如果我们尝试将使用 `twitter_word` 变量得到的 `DTM` 与 `new_covid_twitter_df` 进行列绑定，这将产生问题。为了规避此问题，我们将 `doc_ids` 存储在列表中，并在合并 `DTM` 与数据框时将其用作键。下面代码将 `doc_id` 存储在 `unq_doc_id` 中。

![](img/page413-03.png)

让我们使用下面的代码获取 `twitter_word` 变量的词频。**表 9.59** 显示了下面代码片段的词频。

![](img/page413-04.png)![](img/page414-01.png)![](img/page414-02.png)

现在我们可以将 **表 9.59** 转换为 `DTM`。我们将使用 `cast_dtm()` 并将 `doc_id`、`word` 以及词频，即 `n` 作为参数传递给它。

![](img/page414-03.png)

`cast_dtm()` 的输出如下：

**1.** Documents: 24,254, terms: 5,499 :- 24,254 指的是 `DTM` 中的文档数量，这与 `covid_twitter_df` 中的推文/观测数量完全相同。5,499，被称为 terms，是 `twitter_word_count` 数据框中的唯一词数。

**2.** Non-/sparse entries: 1,60,584/13,32,12,162。这表明在 (24,254\*5,499 = 13,33,72,746) 中，`DTM` 中只有 1,60,584 个非零条目。这些非零条目是特定文档中词的计数。13,32,12,162 是 `DTM` 中零条目的数量。

**3.** Sparsity: 100%。这是 13,32,12,162/13,33,72,746，即 `DTM` 中大约 100% 的条目为零。

矩阵的行名将与我们在 `cast_dtm()` 中使用的 `doc_id` 相同。该矩阵的维度为 24,252\*5,499。我们将使用下面的代码将 `DTM` 类型转换为矩阵对象。**表 9.60** 显示了结果矩阵。

![](img/page415-01.png)

为了将 **表 9.57** 与 **表 9.60** 合并，我们需要执行以下步骤：

**1.** 将 `twt_dtm_matrix` 和 `doc_id` 进行列绑定。可以使用 `cbind()` 函数。

**2.** 通过使用 `as.data.frame()` 将矩阵类型转换为数据框。

下面的代码应用了这两个步骤并创建了 `mod_twt_dtm_df`。**表 9.61** 显示了 `mod_twt_dtm_df` 的输出。

![](img/page415-02.png)![](img/page415-03.png)![](img/page415-04.png)![](img/page416-01.png)

现在，我们可以使用 `dplyr` 包中的 `inner_join()` 将 `new_covid_twitter_df` **(表 9.57)** 与 `mod_twt_dtm_df` 按 `doc_id` 合并。结果显示在 **表 9.62** 中。

![](img/page416-02.png)

`ncovid_tweet_df` 的维度为 25,494\*5,516。如果 `ncovid_tweet_df` 是一个标记数据集，我们就可以在 `ncovid_tweet_df` 上应用任何监督机器学习算法。当然，`ncovid_tweet_df` 需要进一步预处理以删除某些特征，但它是一个将非结构化文本数据转换为结构化格式的数据集。

文档词矩阵可作为多种建模技术的输入。与将 ‘`tweet_dtm`’，即 `DTM`，与原始数据框合并不同，我们可以将 `DTM` 作为主题建模的输入。

## 9.11 主题建模

主题建模是一种无监督学习算法，试图提取语料库中讨论的主题。它将

**1.** 每个文档视为主题的混合。

**2.** 每个主题视为词的混合。

从文档中提取的主题数量 (`k`) 是主题建模算法的用户定义输入。让我们快速在 `tweet_dtm` `DTM` 上应用 `topicmodels` 包中的 `LDA()` 函数。

![](img/page416-03.png)

我们可以通过在 `tidy()` 中使用名为 `beta` 的参数来提取每个主题每个词的概率。**表 9.63** 显示了每个词来自六个主题的概率。

![](img/page416-04.png)![](img/page417-01.png)

我们可以将前 10 个词可视化为六个主题的一部分。

![](img/page417-02.png)![](img/page418-01.png)

根据 **图 9.24**，我们可以看到每个主题中使用的前几个词。

**1.** 主题 1 中的词似乎暗示政府规则和指南。

**2.** 主题 2 中的词似乎暗示需要保持个人卫生。

**3.** 主题 3 中的词似乎在谈论康复后支持和症状。

**4.** 主题 4 中的词（如 festive、events、season、entertainment）似乎在谈论在节日等期间传播意识。

让我们通过将参数 `gamma` 传递给 `tidy()` 来计算每个文档每个主题的概率。

![](img/page418-02.png)![](img/page419-01.png)

根据 **表 9.64**，我们可以查看所有文档的文档主题概率。如果一个文档对所有主题的概率都为 0.166，则意味着该文档中使用的词并未源自该文档。根据 **表 9.64**，我们清楚地看到文档 10 有 93% 的词属于主题 1。我们可以筛选 `covid_documents` 并了解每个文档的主题。**表 9.65** 显示了文档 1 中的主题，似乎文档 1 大多属于主题 4，即个人卫生。

![](img/page419-02.png)

在本节中我们简要讨论了主题模型。主题模型在文档长度不受限制的文档中应用可能更有用，例如推文。还可以从主题模型中制作其他可视化图表。我们留给读者尝试对主题模型进行不同的可视化。

![](img/page419-03.png)

## 摘要

在本章中，我们学习了

**1.** 设置系统抓取推特数据以及正则表达式在文本预处理中的重要性。

**2.** 文本是非结构化数据，在可视化和情感分析之前需要大量预处理。正则表达式有助于文本预处理。

**3.** 文档或句子可以被标记化为 unigrams 或 n-grams 以构建特征。

**4.** 文档可以用词或 n-grams 作为特征的向量表示。向量可以使用简单计数、TF（词频）或 TF-IDF 值创建。

**5.** 通过删除停用词并应用词干提取或词形还原，可以创建稳健的特征集。特征数量也可以通过仅选择频率更高的特征来限制。



### 6. 内置词典如 `afinn`、`nrc`、`bing` 等可用于理解文本数据的情感。单词和双词的可视化可能有助于对数据进行上下文理解。

### 7. 文档词矩阵可作为多种建模技术的输入。我们了解了 `DTM` 在主题模型上下文中的使用。

## 练习
### 使用加州大学欧文分校机器学习数据库中的“情感标注句子数据集”来回答以下问题。数据集可以从 [`archive.ics.uci.edu/ml/datasets/Sentiment+Labelled+Sentences`](https://archive.ics.uci.edu/ml/datasets/Sentiment+Labelled+Sentences) 下载（数据文件夹）使用数据文件 `yelp_labelled.txt` 回答问题 1-10。文件有两个列。第一列是文本句子，第二列是分数。`Score` 为 1（表示积极）或 0（表示消极）。

### 1. 加载数据集并找出数据集中有多少积极情感和多少消极情感文档。绘制条形图以描绘每个情感类别中的文档数量。打印一些积极情感和一些消极情感文档的样本。

### 2. 创建所有文档的计数向量。
#### a. 找出语料库中总共有多少个词或特征。
#### b. 哪些是频率或总计数最高的 10 个词？
#### c. 整个语料库中总频率小于 3 的词或特征有多少个？

### 3. 通过移除停用词创建计数向量（使用 `tidytext` 中的 `stop_words` 词典）。
#### a. 找出总共有多少个词或特征。
#### b. 哪些是频率或总计数最高的 10 个词？
#### c. 使用 `ggplot` 可视化前 10 个词？

### 4. 通过移除停用词创建 `tf-idf` 向量（使用 `tidytext` 中的 `stop_words` 词典）。
#### a. 找出总共有多少个词或特征。
#### b. 哪些是 `tf-idf` 最高的 10 个词？
#### c. 使用 `ggplot` 可视化前 10 个词？

### 5. 通过移除停用词创建双词组（使用 `tidytext` 中的 `stop_words` 词典）。
#### a. 存在多少个双词组。
#### b. 哪些是频率或总计数最高的 10 个词？
#### c. 使用 `ggplot` 可视化前 10 个词？

### 6. 使用 `bing` 词典获取数据集的情感（积极和消极）。将使用 `bing` 词典获得的情感分数与预先存在的情感列（即第二列 `Score`）进行比较。记录你的发现。

### 7. 使用数据创建文档词矩阵（`DTM`）。使用 `k` = 2 到 `k` = 6 建立主题模型。情感数据中出现了哪些主题。

### 8. 将文档按 80:20 的比例拆分。80% 的文档在训练集中，20% 的文档在测试集中。

### 9. 使用问题 7 中创建的 `DTM`，建立分类模型使用逻辑回归来预测文档为积极的概率。使用预先存在的标签列（即 `Score` 作为 `Y` 特征/变量）。解释为什么词具有正系数和负系数。

### 10. 从上面建立的模型中，使用 Youden 指数找到最佳截止值。然后使用最佳截止值对测试集中的文档进行分类。
#### a. 创建混淆矩阵。
#### b. 找出积极情感情况下的精确率和召回率。

## 参考书目
1. Anon (2020), `Search_Tweets` 可在 https://www.rdocumentation.org/packages/rtweet/versions/0.7.0/topics/search_tweets 获取，于 2021 年 1 月 30 日访问。
2. Anon (2021), “Word Embedding Tutorial: `word2vec` using `Gensim`”，可在 https://www.guru99.com/word-embedding-word2vec.html 获取，于 2021 年 1 月 30 日访问。
3. Biguzzi S (2020), “Sentiment Analysis”，可在 https://api.rpubs.com/biguzzis/data607assignment10 获取，于 2021 年 1 月 30 日访问。
4. Hu M and Liu B (2004), “Mining and summarizing customer reviews.”, Proceedings of the ACM SIGKDD International Conference on Knowledge Discovery & Data Mining (KDD-2004), Seattle, Washington, USA, Aug 22–25, 2004.
5. Jones K S (1972), “A statistical interpretation of term specificity and its application in retrieval”. *Journal of Documentation*, 28 (1), 可在 https://www.regular-expressions.info/unicode.html 获取，于 2021 年 1 月 30 日访问。
6. Liu B (2015), “Sentiment Analysis: Mining Sentiments, Opinions and Emotions”, Cambridge University Press, London.
7. Loughran T and McDonald B (2019), “Textual Analysis in Finance”，可在 `file:///C:/Users/Dinesh%20kumar/Downloads/SSRN-id3470272.pdf` 获取，于 2021 年 8 月 5 日访问。
8. Mohammad S M and Turney P (2013), “Crowdsourcing a Word-Emotion Association Lexicon.” *Computational Intelligence*, 29(3): 436–465, 可在 https://onlinelibrary.wiley.com/doi/abs/10.1111/j.1467-8640.2012.00460.x 获取，于 2021 年 1 月 30 日访问。
9. Nielsen F A (2011), “A New ANEW: Evaluation of a Word List for Sentiment Analysis for Microblogs”, In Proceedings of the ESWC2011 Workshop on ‘Making Sense of Microposts’: Big Things Come in Small Packages, Heraklion, Crete, Greece, May 30, 2011, pages 93–98.
10. Pradhan M and Kumar U D (2019), “Machine Learning Using Python”, Wiley, New Delhi.
11. Silge J and Robinson D (2017), “Text Mining Using R – A Tidy Approach”, O’Reilly Media.

¹[`developer.twitter.com/en/docs/twitter-api/v1/tweets/search/api-reference/get-search-tweets`](https://developer.twitter.com/en/docs/twitter-api/v1/tweets/search/api-reference/get-search-tweets)

## 进一步阅读
1. Acharya S (2018), “Data Analytics Using R”, McGraw Hill Education, New Delhi.
2. Anon (2021), “R Interface for the ‘H2O’ Scalable Machine Learning Platform”，可在 https://cran.r-project.org/web/packages/h2o/h2o.pdf 获取，于 2021 年 6 月 17 日访问。
3. Anon (2021), “Analytics Using R”，可在 https://pubs.wsb.wisc.edu/academics/analytics-using-r/getting-start-ed-with-r.html 获取，于 2021 年 5 月 30 日访问。
4. April S and Wagge J R (2020), “Learning R Programming Language with Psi Chi”, *Psi Chi Journal of Psychological Research* 25(1): 85–87.
5. Bach P, Chernozhukov V, Kurz M S and Spindler M (2021), “DoubleML – An Object-Oriented Implementation of Double Machine Learning in R”，可在 https://search-works.stanford.edu/articles/edsarx__edsarx.2103.09603 获取，于 2021 年 6 月 6 日访问。
6. Bali R and Sarkar D, (2016), “R Machine Learning By Example”，可在 https://searchworks.stanford.edu/articles/nlebk 1215154 获取，于 2021 年 6 月 6 日访问。
7. Bali R (2016), “R Machine Learning by Example”，可在 https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=f7ccefea-ce4b-454f-a91f-ec35aaaa7a21%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25657027&db=cat04202a 获取，于 2021 年 6 月 7 日访问。
8. Bell D (2020), “R Programming: A Step-by-Step Guide for Absolute Beginners”, 2^(nd) ed., Independent Publishing, USA.
9. Boehmke B and Greenwell BM (2019), “Hands-On Machine Learning with R”, Chapman, Boca Raton.




# 参考文献

10. Boehmke B (2020), “用 R 进行动手机器学习”, 可获取于 [`https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=0a57de82-50f3-4795-b61c-227713deac27%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWR-zLWxpdmU%3d#AN=ucb.b25219259&db=cat04202a`](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=0a57de82-50f3-4795-b61c-227713deac27%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWR-zLWxpdmU%3d#AN=ucb.b25219259&db=cat04202a), 访问于 2021 年 6 月 7 日.

11. Boehmke BC (2016), “使用 R 进行数据整理 (Use R!)”, Springer, New York.

12. Chang W (2018), “R 图形食谱：数据可视化的实用配方”, 2^(nd) 版, O’Reilly, California.

13. Chollet F and Allaire JJ (2018), “使用 R 的深度学习”, Manning, New York.

14. Ciaburro G and Venkateswaran B, (2017), “使用 R 的神经网络”, 可获取于 [`https://searchworks.stanford.edu/articles/nlebk\_\_1607842`](https://searchworks.stanford.edu/articles/nlebk__1607842), 访问于 2021 年 6 月 6 日.

15. Claster W B (2020), “机器学习的数学与 R 编程：从基础开始”, 可获取于 [`https://eds.b.ebscohost.com/eds/detail/de-tail?vid=0&sid=c72a0c6b-bac6-4cc1-8f60-904a29710a31%40sessionmgr101&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25808183&db=cat04202a`](https://eds.b.ebscohost.com/eds/detail/de-tail?vid=0&sid=c72a0c6b-bac6-4cc1-8f60-904a29710a31%40sessionmgr101&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25808183&db=cat04202a), 访问于 2021 年 6 月 7 日.

16. Cotton R (2013), “学习 R：数据分析的分步函数指南”, O’Reilly, California.

17. Crawley MJ (2012), “R 书”, Wiley, Hoboken.

18. Daroczi G. (2015), “精通 R 数据分析”, Packt, Birmingham.

19. Davies TM (2016), “R 书：编程与统计学入门课程”, Wiley, Hoboken.

20. De Vries A. (2016), “R 编程傻瓜书”, 2^(nd) 版, Wiley, Hoboken.

21. Deisenroth MP, Faisal AA and Cheng Soon Ong (2020), “机器学习数学”, Cambridge University Press, Cambridge.

22. DT Editorial (2016), “大数据黑皮书：涵盖 Hadoop 2、MapReduce、Hive、YARN、Pig、R 和数据可视化”, Dreamtech Press, New Delhi.

23. Dunn PK and Smyth GK (2018), “广义线性模型：R 中的示例”, Springer, New York.

24. Faraway JJ (2014), “使用 R 的线性模型”, Chapman, Florida.

25. Faraway JJ (2016), “扩展 R 中的线性模型：广义线性、混合效应和非参数回归模型”, 2^(nd) 版, Chapman, Florida.

26. Field A (1900), “使用 R 发现统计学”, Sage, California.

27. Fischetti A (2015), “使用 R 进行数据分析”, Ingram, La Vergne.

28. Fischetti A (2015), “使用 R 进行数据分析：使用世界上最强大的统计编程语言加载、整理和分析您的数据”, Packt, Birmingham.

29. Forte R M (2015), “精通 R 预测分析”, Packt, Birmingham.

30. Fox J and Weisberg S (2011), “应用回归的 R 伴侣”, Sage, California.

31. Gardener M. (2013), “入门 R：统计编程语言”, Wiley, Hoboken.

32. Gentleman R (2008), “生物信息学的 R 编程”, 可获取于 [`https://books.google.co.in/books?hl=en&lr=&id=34Y6WjJy8zEC&oi=fnd&pg=PP1&dq=articles+on+r+programming&ots=UjRd3t79oM&sig=opJ\_DwAy6-gv6yS7o-qwKbNCrsw#v=onepage&q&f=false`](https://books.google.co.in/books?hl=en&lr=&id=34Y6WjJy8zEC&oi=fnd&pg=PP1&dq=articles+on+r+programming&ots=UjRd3t79oM&sig=opJ_DwAy6-gv6yS7o-qwKbNCrsw#v=onepage&q&f=false), 访问于 2021 年 6 月 6 日.

33. Gentleman R (2009), “生物信息学的 R 编程”, 可获取于 [`https://eds.b.ebscohost.com/eds/detail/detail?Vid=0&sid=ca22a0e3-4e7d-473f-adeb-4f0a365a4316%40pdc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWxpdmU%3d#AN=ucb.b18033964&db=cat04202a`](https://eds.b.ebscohost.com/eds/detail/detail?Vid=0&sid=ca22a0e3-4e7d-473f-adeb-4f0a365a4316%40pdc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWxpdmU%3d#AN=ucb.b18033964&db=cat04202a), 访问于 2021 年 6 月 7 日.

34. Ghatak A (2017), “使用 R 的机器学习”, 可获取于 [`https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=9dad0d55-8330-45a4-8d8b-afd-dc6424ddb%40pdc-v-sessmgr03&bdata=JnNpd-GU9ZWRzLWxpdmU%3d#AN=ucb.b24175802&db=cat04202a`](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=9dad0d55-8330-45a4-8d8b-afd-dc6424ddb%40pdc-v-sessmgr03&bdata=JnNpd-GU9ZWRzLWxpdmU%3d#AN=ucb.b24175802&db=cat04202a), 访问于 2021 年 6 月 7 日.

35. Gillespie C (2016), “高效 R 编程：更智能编程的实用指南”, 可获取于 [`https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=83982043-1eef-43d8-9822-5fa9a8669591%40p-dc-v-sessmgr01&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25641403&db=cat04202a`](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=83982043-1eef-43d8-9822-5fa9a8669591%40p-dc-v-sessmgr01&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25641403&db=cat04202a), 访问于 2021 年 6 月 7 日.

36. Hartvigsen G (2014), “使用 R 进行生物数据分析与可视化的入门”, Columbia university press, New York.

37. Hefin (2020), “使用 R、tidyverse 和 mlr 进行机器学习 Rhys”, 可获取于 [`https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=f1b6523b-f19c-4246-b94b-a7dcf2d4759a%40sessionmgr101&bdata=JnNpd-GU9ZWRzLWxpdmU%3d#AN=ucb.b25764223&db=cat04202a`](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=f1b6523b-f19c-4246-b94b-a7dcf2d4759a%40sessionmgr101&bdata=JnNpd-GU9ZWRzLWxpdmU%3d#AN=ucb.b25764223&db=cat04202a), 访问于 2021 年 6 月 7 日.

38. Heiss F (2016), “使用 R 进行入门计量经济学”, Createspace, California.

39. Hornick M (2013), “使用 R 解锁大数据的价值”, McGraw Hill Education, New York.

40. Hothorn T (2014), “使用 R 的统计分析手册”, Chapman, Boca Raton.

41. Jeyaraman and Priyadarshini B (2019), “使用 R 的实用机器学习”, 可获取于 [`https://searchworks.stan-ford.edu/articles/edsvox\_\_edsvox.international.scholar-vox.88874202`](https://searchworks.stan-ford.edu/articles/edsvox__edsvox.international.scholar-vox.88874202), 访问于 2021 年 6 月 6 日.

42. Kabacoff R L (2015), “R 实战”, 2^(nd) 版 (Manning), Dreamtech Press, New Delhi.

43. Kassambara A (2017), “机器学习精要：R 中的实用指南”, 可获取于 [`https://books.goo-gle.co.in/books?hl=en&lr=&id=745QDwAAQBA-J&oi=fnd&pg=PP2&dq=articles+on+machine+learn-ing+and+R&ots=5EKqwNRZRt&sig=Ojs-n3Ak-th9g-DpP91B1cRQyLbI#v=onepage&q=articles%20on%20machine%20learning%20and%20R&f=false`](https://books.goo-gle.co.in/books?hl=en&lr=&id=745QDwAAQBA-J&oi=fnd&pg=PP2&dq=articles+on+machine+learn-ing+and+R&ots=5EKqwNRZRt&sig=Ojs-n3Ak-th9g-DpP91B1cRQyLbI#v=onepage&q=articles%20on%20machine%20learning%20and%20R&f=false), 访问于 2021 年 6 月 6 日.

44. Kruschke JK (2015), “R 编程语言”, 可获取于 [`https://www.sciencedirect.com/topics/mathe-matics/r-programming-language`](https://www.sciencedirect.com/topics/mathe-matics/r-programming-language)

45. Kuhn M (2019), “caret 包”, 可获取于： [`http://topepo.github.io/caret/index.html`](http://topepo.github.io/caret/index.html), 访问于 2021 年 6 月 17 日.

46. Kun R (2016), “学习 R 编程”, 可获取于 [`https://searchworks.stanford.edu/articles/nlebk\_\_1409189`](https://searchworks.stanford.edu/articles/nlebk__1409189), 访问于 2021 年 6 月 6 日.

47. Lai J, Christopher J. Lortie, Robert A. Muenchen, Yang J, Keping Ma (2019), “评估 R 在生态学中的流行度”, *Ecosphere* 10(1): 1–7. [`https://doi.org/10.1002/ecs2.2567`](https://doi.org/10.1002/ecs2.2567)

48. Lander J P (2017), “人人都能用的 R：高级分析和图形”, Addison-Wesley, Boston.



# 参考文献

49. Lantz B (2013), “使用 R 进行机器学习”, 可获取于 [`books.google.co.in/books?hl=en&lr=&id=ZQu8AQAAQBAJ&oi=fnd&pg=PT12&dq=articles+on+machine+learning+using+r+program-ming&ots=\_9se\_hak5c&sig=ey7V76BvCd--TYQIYrm-FgOU-dRY#v=onepage&q&f=false`](https://books.google.co.in/books?hl=en&lr=&id=ZQu8AQAAQBAJ&oi=fnd&pg=PT12&dq=articles+on+machine+learning+using+r+program-ming&ots=_9se_hak5c&sig=ey7V76BvCd--TYQIYrm-FgOU-dRY#v=onepage&q&f=false), 访问于 2021 年 6 月 6 日.

50. Lantz B (2019), “使用 R 进行机器学习：预测建模的专家技术”, 可获取于 [`books.google.co.in/books?hl=en&lr=&id=iNuS-DwAAQBAJ&oi=fnd&pg=PP1&dq=articles+on+ma-chine+learning+using+r+programming&ots=O83St-beEK2&sig=eEDP\_rvqFwwiJ3TtjvH6W0\_g\_1E#v=onep-age&q&f=false`](https://books.google.co.in/books?hl=en&lr=&id=iNuS-DwAAQBAJ&oi=fnd&pg=PP1&dq=articles+on+ma-chine+learning+using+r+programming&ots=O83St-beEK2&sig=eEDP_rvqFwwiJ3TtjvH6W0_g_1E#v=onep-age&q&f=false), 访问于 2021 年 6 月 6 日.

51. Lantz B (2015), “使用 R 进行机器学习：解决所有数据分析问题的预测建模专家技术”, 可获取于 [`searchworks.stan-ford.edu/articles/edsebk\_\_1048220`](https://searchworks.stan-ford.edu/articles/edsebk__1048220), 访问于 2021 年 6 月 6 日.

52. Lantz B (2019), “使用 R 进行机器学习：预测建模的专家技术”, 3^(rd) 版, 可获取于 [`searchworks.stanford.edu/articles/edsebk\_\_2106304`](https://searchworks.stanford.edu/articles/edsebk__2106304), 访问于 2021 年 6 月 6 日.

53. Lantz B (2013), “使用 R 进行机器学习”, 可获取于 [`searchworks.stanford.edu/articles/nlebk\_\_656222`](https://searchworks.stanford.edu/articles/nlebk__656222), 访问于 2021 年 6 月 6 日.

54. Lanzetta V B and Dasgupta N and Farias R A (2018), “动手实践 R 数据科学”, Packt, 伯明翰.

55. Larose D T and Larose C D (2019), “使用 Python 和 R 进行数据科学”, Wiley, 霍博肯.

56. Ledolter J (2013), “使用 R 进行数据挖掘和商业分析”, Wiley, 霍博肯.

57. Lesmeister C (2015), “精通使用 R 的机器学习”, 可获取于 [`searchworks.stanford.edu/articles/nlebk\_1087969`](https://searchworks.stanford.edu/articles/nlebk_1087969), 访问于 2021 年 6 月 6 日.

58. Lesmeister C (2019), “使用 R 的高级机器学习”, 可获取于 [`searchworks.stanford.edu/articles/edsvox\_\_edsvox.international.scholarvox.88871045`](https://searchworks.stanford.edu/articles/edsvox__edsvox.international.scholarvox.88871045), 访问于 2021 年 6 月 6 日.

59. Lewis N D (2014), “使用 R 可视化复杂数据：标准版”, Createspace, 加利福尼亚.

60. Long JD and Teetor P (2019), “R Cookbook：数据分析、统计和图形的实用配方”, 2^(nd) 版, O’Reilly, 加利福尼亚.

61. Mailund T (2018), “R 中的领域特定语言：高级统计编程”, Apress, 伯明翰.

62. Maindonald J and Braun J (2003), “使用 R 进行数据分析和图形：基于示例的方法”, Cambridge university press, 剑桥.

63. Malik F (2020), “R - 统计编程语言”, 可获取于 [`towardsdatascience.com/r-statisti-cal-programming-language-6adc8c0a6e3d`](https://towardsdatascience.com/r-statisti-cal-programming-language-6adc8c0a6e3d), 访问于 2021 年 6 月 6 日.

64. Matloff and Norman S (2011), “R 编程艺术：统计软件设计的巡览”, 可获取于 [`eds.b.ebscohost.com`](https://eds.b.ebscohost.com)/eds/detail/detail?vid=0&sid=3d4e7ca8-80f0-4a92-b8e4-ddeda6c144c8%-40sessionmgr101&bdata=JnNpdGU9ZWRzLWxpdmU%3d#AN=ucb.b25635221&db=cat04202a, 访问于 2021 年 6 月 7 日.

65. Mayor E (2015), “使用 R 学习预测分析”, Packt, 伯明翰.

66. Medeiros K (2018), “R 编程基础：使用各种建模技术处理数据’ 可获取于 [`eds.b.ebscohost.com/eds/detail/de-tail?vid=0&sid=ed4ad89a-fcaf-4768-a5ba-b871369476d7%40pdc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25657033&db=cat04202a`](https://eds.b.ebscohost.com/eds/detail/de-tail?vid=0&sid=ed4ad89a-fcaf-4768-a5ba-b871369476d7%40pdc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25657033&db=cat04202a), 访问于 2021 年 6 月 7 日.

67. Motwani, B (2019), “使用 R 进行数据分析”, Wiley, 新德里.

68. Mueller JP and Massaron L (2016), “傻瓜式机器学习（Python 和 R）”, Wiley, 霍博肯.

69. Navarro T and Omar (2017), “通过示例学习 R 编程：帮助你入门 R 的实用动手项目”, 可获取于 [`eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=9454f0b4-e27c-49a7-97da-b68d70ef9b0e%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWR-zLWxpdmU%3d#AN=ucb.b25657032&db=cat04202a`](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=9454f0b4-e27c-49a7-97da-b68d70ef9b0e%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWR-zLWxpdmU%3d#AN=ucb.b25657032&db=cat04202a), 访问于 2021 年 6 月 7 日.

70. Pacheco E R (2015), “使用 R 进行无监督学习”, Packt, 伯明翰.

71. Pearson R K (2020), “使用 R 进行探索性数据分析”, Chapman, 博卡拉顿.

72. Prajapati V (2013), “使用 R 和 Hadoop 进行大数据分析”, Packt, 伯明翰.

73. Rakshit S (2017), “R 编程入门”, McGraw Hill Education, 纽约.

74. Ratnoo S D and Ratnoo H S (2021), “数据分析的 R 基础”, Wiley, 新德里.

75. Ren K (2016), “学习 R 编程：成为高效的数据科学家”, 可获取于 [`eds.b.ebsco-host.com/eds/detail/detail?vid=0&sid=4308291d-6005-422c-b4a1-8c6fb6b1cce1%40sessionmgr101&bdata=JnNpdGU9ZWRzLWxpdmU%3d#AN=ucb.b25649156&db=cat04202a`](https://eds.b.ebsco-host.com/eds/detail/detail?vid=0&sid=4308291d-6005-422c-b4a1-8c6fb6b1cce1%40sessionmgr101&bdata=JnNpdGU9ZWRzLWxpdmU%3d#AN=ucb.b25649156&db=cat04202a), 访问于 2021 年 6 月 7 日.

76. Ren K. (2016), “学习 R 编程：语言、工具和实用技术”, Packt, 伯明翰.

77. Ren K (2017), “现代 R 编程 Cookbook：简化统计应用的配方”, 可获取于 [`eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=a373153a-b7c5-43fb-b3ea-28dfa2c170e2%40p-dc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25652445&db=cat04202a`](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=a373153a-b7c5-43fb-b3ea-28dfa2c170e2%40p-dc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25652445&db=cat04202a), 访问于 2021 年 6 月 7 日.

78. Sanz I P (2019), “使用 R 快速入门机器学习指南：从零开始使用 R 3.5 实现机器学习技术的初学者指南, 可获取于 [`eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=44fc693a-873a-4eb1-9eab-57a9e75c1e-c7%40sessionmgr103&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25649967&db=cat04202a`](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=44fc693a-873a-4eb1-9eab-57a9e75c1e-c7%40sessionmgr103&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25649967&db=cat04202a), 访问于 2021 年 6 月 7 日.

79. Schumacker RE (2015), “使用 R 进行多元统计”, Sage, 加利福尼亚.

80. Sheather S (2008), “使用 R 进行回归的现代方法”, Springer, 纽约.

81. Silge J and Robinson D (2017), “使用 R 进行文本挖掘：整洁的方法”, 可获取于： [`www.tidytextmining.com/index.html`](https://www.tidytextmining.com/index.html), 访问于 2021 年 6 月 17 日.

82. Tattar P N (2018), “动手实践使用 R 的集成学习”, Packt, 伯明翰.

83. Trejo O and Figliozzi P C (2017), “通过示例学习 R 编程”, 可获取于 [`searchworks.stanford.edu/articles/nlebk\_\_1682395`](https://searchworks.stanford.edu/articles/nlebk__1682395), 访问于 2021 年 6 月 6 日.



## 参考文献

84. Viswa V (2016), “R：分析、可视化与机器学习配方”, 可查阅于 [`searchworks.stanford.edu/articles/nlebk\_\_1428303`](https://searchworks.stanford.edu/articles/nlebk__1428303)，访问于 06 June 2021.

85. Wei-Meng Lee (2018), “R 编程语言导论”, 可查阅于 [`www.codemag.com/Article/1803081/Introduction-to-the-R-Program-ming-Language`](https://www.codemag.com/Article/1803081/Introduction-to-the-R-Program-ming-Language)，访问于 16 June 2021.

86. Wickham H (2015), “R 包”, O’Reilly, California.

87. Wickham H (2019), “高级 R”, 2^(nd) 版, Chapman, Florida.

88. Wicklam H and Grolemund G (2017), “R 数据科学：导入、整理、转换、可视化与建模数据”, O’Reilly, California.

89. Wiley M and Wiley J F (2019), “高级 R 统计编程与数据模型：分析、机器学习与可视化”, 可查阅于 [`books.google.co.in/books?hl=en&lr=&id=hBeJDwAAQBAJ&oi=fnd&pg=PR3&dq=articles+on+machine+learning+using+r+programming&ots=F1vOBohYRB&sig=8yVlltpt\_MtRO8OqX6rDgBYxUiME#v=onepage&q=articles%20on%20machine%20learning%20using%20r%20program-ming&f=false`](https://books.google.co.in/books?hl=en&lr=&id=hBeJDwAAQBAJ&oi=fnd&pg=PR3&dq=articles+on+machine+learning+using+r+programming&ots=F1vOBohYRB&sig=8yVlltpt_MtRO8OqX6rDgBYxUiME#v=onepage&q=articles%20on%20machine%20learning%20using%20r%20program-ming&f=false)，访问于 06 June 2021.

90. Yu-Wei and Chiu D (2015), “R 机器学习实战”, 可查阅于 [`books.goo-gle.co.in/books?hl=en&lr=&id=iPirBwAAQBAJ&oi=fnd&pg=PP1&dq=articles+on+machine+learn-ing+and+R&ots=\_WV7DFaIre&sig=qGDg3Wz6Sxlq0V4vsPnQVS50yoY#v=onepage&q=articles%20on%20machine%20learning%20and%20R&f=false`](https://books.goo-gle.co.in/books?hl=en&lr=&id=iPirBwAAQBAJ&oi=fnd&pg=PP1&dq=articles+on+machine+learn-ing+and+R&ots=_WV7DFaIre&sig=qGDg3Wz6Sxlq0V4vsPnQVS50yoY#v=onepage&q=articles%20on%20machine%20learning%20and%20R&f=false)，访问于 06 June 2021.

91. Zhao (2014), “R 数据挖掘应用”, Elsevier, Amsterdam.

92. Zumel N and Mount J (2014), “R 实用数据科学” (Manning), Dreamtech Press, New Delhi.

## 索引

### A

高级编码技术, 147

赤池信息准则 (`AIC`), 147, 190

`glmStepAIC` 方法, 190–194

使用进行模型选择, 157–159

步骤, 159–162, 194–195

Anaconda, 3

发行版, 14

Anaconda 导航器

方差分析 (`ANOVA`), 115–118

人工智能, 1–2, 229

### B

词袋 (`BoW`) 模型

二进制向量, 354

计数向量, 354

定义, 353

n-gram, 383–386

词干提取和词形还原, 372–379

词频-逆文档频率 (`TF-IDF`), 379–383

词频-逆文档频率 (`TF-IDF`), 355–356

词频 (`TF`) 向量, 354–355

核的带宽, 76

条形图或图表 Beta 分布, 106

偏差-方差权衡, 238–244

二进制编码, 147

二元逻辑回归模型, 176–178

二项分布

累积分布函数, 94

离散概率分布, 93

概率质量函数, 93

使用 R, 94–95

自助采样, 285

箱线图（又称箱须图）

### C

中心极限定理, 106–107

分类问题（或类概率）二元逻辑回归 (*参见* 二元逻辑回归模型)

类别不平衡问题, 289

重新分组类别, 290

采样策略, 290–292

综合 R 档案网络 (`CRAN`), 3–5

相关矩阵, 83–84

### D

`data.frame`, 12, 17

`data.table`, 23, 48–51

整洁 `data.frame`, 18

使用 `twitteR` 包导入数据, 350–353

数据预处理，定义, 17

数据抓取，从 Twitter 获取数据的步骤, 337–340

`data.table`

基本列子集操作, 27–31

使用 R 的基本操作, 24–26

基本行列选择及操作计算, 31–35

基本行子集操作, 26–27

基于二进制搜索的子集, 40–42

使用进行数据整理, 24

`DT` 包, 51–52

`.EACHI`, 35

分组操作, 36–40

连接操作, 42–48

键, 40–42

数据表对象, 21

R 中的数据可视化, 58–59

条形图或图表 (*参见* 条形图或图表)

箱线图（又称箱须图） (*参见* 箱线图（又称箱须图）)

相关矩阵 (*参见* 相关矩阵)

分布或密度图 (*参见* 分布或密度图)

热力图 (*参见* 热力图)

直方图 (*参见* 直方图)

散点图 (*参见* 散点图)

趋势图 (*参见* 趋势图)

决策树学习（或决策树）

`ROC` 曲线下面积 (`AUC`), 223–224

分类与回归树 (`CART`), 216

混淆矩阵，创建, 222–223

受试者工作特征 (`ROC`) 曲线, 223–224

深度学习 (`DL`) 算法, 1–2

描述性分析，使用 R 中的 `data.frame`, 17–18



### **D**
分布或密度图, 76
核密度估计 (KDE) (*参见* 核密度估计 (KDE)), 76
概率密度函数 (PDF) (*参见* 概率密度函数 (PDF)), 75, 93
文档词矩阵 (DTM)
下采样策略, 290–291
`DT` 包, 51–52

### **E**
集成方法, 285
类别不平衡问题 (*参见* 类别不平衡问题)
随机森林 (*参见* 随机森林)
指数分布, 96

### **F**
特征工程, 3–4, 55
特征提取, 4
特征哈希, 147
特征权重, 2

### **G**
逻辑回归模型的增益图, 211–216
伽马分布, 106
几何分布, 106
梯度提升机 (GBM), 308–309
模型诊断, 315–317
模型预测, 318
随机梯度提升 (*参见* 随机梯度提升)
类别不平衡, 313
控制增长, 313–314
超参数, 314
随机行选择 (自助抽样), 313
随机子空间选择, 312–313
搜索标准, 314
梯度下降 (GD) 算法, 230
线性回归模型的开发 创建特征集 (`X`) 和结果变量 (`Y`), 232–233
编码分类特征, 233–234
设置 `x` 和 `y` 变量, 234
绘制成本值, 236–238

### **H**
热力图, 83–85
六边形
售价与基础价格之间的图, 74
按角色划分的售价与基础价格之间的图, 75
直方图
售价与基础价格之间的 2D 直方图, 73
假设检验
备择假设, 107–108
卡方拟合优度检验和独立性检验, 113–115
非参数检验, 108
零假设, 107–108
单样本 t 检验, 110–111
单样本 Z 检验, 109–110
配对样本 t 检验, 112–113
参数检验, 108
双样本 `t` 检验, 111–112

### **I**
印度板球超级联赛 (IPL), 18–20

### **J**
Jupyter Notebook, 5, 15, 23

### **K**
核, 76
核密度估计 (KDE), 76
关键绩效指标 (KPI), 91

### **L**
逻辑回归模型的提升图, 211–216
线性依赖, 187 线性回归, 121–124
回归系数的估计, 133
模型构建, 128
模型诊断, 134
逻辑回归模型, 2
ROC 曲线下面积 (AUC), 205–206
二元 (*参见* 二元逻辑回归模型)
成本函数, 231
诊断
混淆矩阵的创建, 200–201
似然比 (LR) 检验, 198
在测试数据上的预测, 199–200
伪 `R²`, 198–199
Wald 检验, 198
寻找最佳分类阈值
基于成本的方法, 206, 209–211
Youden 指数, 206–209
增益图 (*参见* 逻辑回归模型的增益图)
提升图 (*参见* 逻辑回归模型的提升图)
衡量准确性
准确率, 201
F 分数, 204
Kappa 值，计算, 202
McNemar 假设检验, 203
无信息率 (NIR), 201–202
精确率 (阳性预测值), 204
灵敏度 (召回率或真正率), 203
特异度 (真负率), 204
接收者操作特征 (ROC) 曲线, 205–206

### **M**
机器学习 (ML) 算法, 2, 17
进化学习算法, 3
特征工程, 181–183
使用 `glmnet` 的逻辑回归, 271–272
使用 `glmnet` 和 `caret` 的分类模型, 274–282
创建特征集 (`X`) 和结果变量 (`Y`), 272–274
创建训练集和测试集, 274
使用 `glmnet` 和 `caret` 的模型，结果, 271
使用 `caret` 的回归
使用 `tuneGrid` 和 `tuneLength` 的弹性网络回归, 265–270
LASSO 回归, 257–261
岭回归, 261–265
使用 `glmnet` 包的回归, 248–249
创建特征集 (`X`) 和结果变量 (`Y`), 249–250
创建训练集和测试集, 250
结果解释, 253–257
`lambda` 序列背后的直觉, 251–253



使用 `glmnet` 的 LASSO 回归，250–251

强化学习算法，2，230

改进策略

增加更多观测值，245–246

应用正则化，246–248

`K` 折交叉验证，246

监督学习算法，2，230

无监督学习算法，2，230

多重共线性，188–190

多元线性回归 (`MLR`)（又称响应变量或结果变量）模型，162–163

其中的假设，141

使用 `caret` 包进行构建和重建，147–149，153–162

诊断，163–164

同质性假设，165

在数据框中识别异常值案例，167–169

有影响的值，167

线性假设，164

正态性假设，165

异常值和高杠杆点，165–167

响应变量的转换，169–170

转换后的变量，170–171

开发方法，141–142

创建训练集和测试集，147

创建特征集 (`X`) 和结果变量 (`Y`)，145–146

编码分类特征，146–147

导入数据集，142–145

多重共线性，其显著性，149–153

监督学习算法，140–141

## N
正态分布（或高斯分布）

股票数据分析，100–103

置信区间，104–105

累积概率分布，105–106

均值和方差，103–104

数据可视化，99–100

## O
序数编码，147

## P
文本分析包，348–350

泊松分布，95

预建词典，399

概率密度函数 (`PDF`)

连续随机变量，75

核，76

概率的极限值，75

概率论，91

事件，92

随机实验，92

样本空间，92

## R
随机森林（或袋装法）

模型开发，287

袋外数据，287

使用预测净推荐值 (`NPS`)，287–289

使用 `h2o` 包，292–296

类别不平衡，299–300

控制增长，300

搜索标准，301

数据中的特征列表，296–298

网格搜索，301–303

使用 `h2o` 包，299

超参数，300

模型诊断，303–305

模型预测，305–307

行选择（自助法），300

保存模型，307–308

将数据拆分为训练集和测试集，298–299

子空间选择，299

随机过采样示例 (`ROSE`)，291–292

随机子空间方法，285

随机变量，91

连续，92–93

离散，92

累积分布函数 (`CDF`)，93

概率质量函数 (`PMF`)，93

正则表达式

正则表达式的应用，346–348

匹配字符，340–345

重复字符，345–346

`R` 编程语言的概念

认真的重要性 (`TIOBE`) 编程指数，5–7

使用，4

`Rstudio`，23

## S
散点图

评估关系强度，59

在 `AVE_BL` 和 `SR_BL` 之间，60

在击球平均值和击球率之间，61–63

在击球平均值和击球率之间，带拟合线，61

使用分面网格，89

重叠表示，72

情感分析，395–399

`bing` 与 `nrc` 与 `affin`，404–407

使用负面词汇，408–410

使用 `bing` 词典，399–404

简单线性回归 (`SLR`) 模型

构建，123–124

`caret` 包，128–133

创建训练集和验证集，128

创建特征集 (`X`) 和结果变量 (`Y`)，128

数据导入和操作，126–127

定义，121

诊断

回归分析中的方差分析 (`ANOVA`)，136

决定系数（或 `R` 平方或 `R2`），135

回归系数的假设检验，135–136



模型诊断, 136–137
离群值分析, 138–140
回归系数，估计, 133–134
残差分析, 137–138
简单和多元回归问题, 121–122
结果变量的简单对数变换, 291
标准查询语言 (`SQL`), 17
统计学习 (`SL`) 算法, 2, 230
定义, 1
随机梯度提升, 310
合成少数类过采样技术 (`SMOTE`), 291–292
带高斯噪声的回归合成少数类过采样技术 (`SMOGN`), 291
## T
文本预处理
词袋 (`BoW`) 模型 (*参见* 词袋 (`BoW`) 模型)
主题建模, 416–419
趋势图, 84–87
阶梯图, 87
推特数据可视化
计数向量 *对比* 带词干提取和词形还原的计数向量 *对比* TF-IDF 向量, 391–392
改进 `BoW` 模型的方法, 372–386
可视化
双词组, 386–391
单词和词, 365–372
网址, 394–395
## U
`UBL` 包在 `R` 编程语言中, 291
上采样策略, 290
## V
方差膨胀因子 (`VIF`), 149–150
## W
Weibull 分布, 106
词嵌入, 353
`word-to-vec`, 147
## X
`XGBoost` 提升技术
数据集，创建, 323–324
结果讨论, 328–330
最终模型, 330–331
网格搜索, 325
超参数, 324
模型诊断, 325–327
模型预测, 327–328
参数
助推器, 322–323
通用, 322
学习任务, 322
模型保存，参数在, 331
搜索标准, 324
## Z
零和接近零方差 (`NZV`) 特征, 185–187
<!DOCTYPE html>![封面图像](img/Backcover.jpg`)
