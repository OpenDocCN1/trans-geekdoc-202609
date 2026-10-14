
Handling missing data is an essential step in data preprocessing to ensure that analyses and models are based on as much available information as possible, without introducing bias or inaccuracies due to missing values.

在 Figure 46.6 中，展示了前文提到的数据集的箱线图表示。这种图形有效地展示了数据集中的异常值。具体来说，它提供了关于 RAM、设备宽度和设备高度的洞察，这些是导致异常值图变化的主要因素。理解这些异常值至关重要，因为它们可能会对模型预测产生显著影响，尤其是当它们的值出现大幅变化时。

![Figure 46.6 Boxplot diagram for outliers and missing values](img/fig46_6_C.jpg)

Figure 46.6 Boxplot diagram for outliers and missing values

为了更深入地探讨各种特征之间的关系以及它们与价格的相关性，进一步分析对于模型预测至关重要。采用 `Matplotlib` 库来使用热图（Heatmap）展示这些特征关系。热图是可视化不同属性之间依赖性和相关性的有价值工具，有助于全面理解各种因素如何影响移动电话的定价。印度正在扩大，移动客户群体也随之增长。印度拥有约 9 亿移动电话订阅用户，这为每个移动电话制造商提供了更强大的平台（Deepesh Kumar, 2012）。

能源散射光谱、扫描电子显微镜和 X 射线衍射（Sidhu, Goyal, and Goyal, 2017）Figure 46.7 分析了腐蚀产物。

![Figure 46.7 Heatmap for comparing and choosing the attribute to classify our model](img/fig46_7_C.jpg)

Figure 46.7 Heatmap for comparing and choosing the attribute to classify our model

数据的图形表示如下：

### 1. Rating/count

`Rating` 用于评分移动电话，用于获取购买该移动电话的用户的反馈。其值范围在 0 到 100 之间。该图表展示了易于理解的值（Figure 46.8）。

![Figure 46.8 Count plot is used to count the occurrence of the observation](img/fig46_8_C.jpg)

Figure 46.8 Count plot is used to count the occurrence of the observation

### 2. Primary camera/count

通过社交媒体分享照片已成为利用照片库的普遍做法。iPhone 和 Android 手机在完成这一任务方面表现出色，提供无缝的在线直接分享照片的方式。在数字时代，有许多方法和平台可以促进这一过程。手机摄像头的兆像素数在摄影领域具有重要意义。更高的像素数直接与照片质量相关。因此，在追求高质量照片时，建议考虑至少拥有 3 兆像素的移动电话摄像头。

总之，数字技术的普及使得在线分享照片变得简单且易于接近，而关注摄像头像素数仍然是实现卓越照片质量的关键因素。

摄像头像素越多，手机价格越高；但并非所有手机型号的价格都随之上升，价格会因手机而异。因此，该特征已纳入数据集，且上述为特征与价格的图形表示。

### 3. RAM/count

`RAM` 是移动电话的主要组成部分，数据存储在 `RAM` 中，包括操作系统、当前运行的应用程序和数据。数据存储在手机存储中，以便应用、图片、视频和文件能够顺畅运行。主存储器对于预测至关重要，通过 `RAM` 版本，我们可以获得准确的值。正是因为它，移动价格依赖于它。`RAM` 的变化会导致移动价格上升或下降。下面给出了关系的表示（Figure 46.9）。

![Figure 46.9 Count plot is used to count the occurrence of the RAM](img/fig46_9_C.jpg)

Figure 46.9 Count plot is used to count the occurrence of the RAM

### 4. Distplot for all main features

在数据集中，`RAM`、电池电量、摄像头尺寸和其他属性等各种特征在提高移动电话价格预测的精度方面发挥着重要作用。值得注意的是，数据值经过精确校准，这提高了预测模型的可靠性。

为了有效可视化和展示数据，采用了 `Seaborn` 库。具体使用 `sns.displot()` 函数来准确呈现数据。该函数有助于创建信息丰富的可视化，帮助理解数据分布和特征。

数据中观察到的变异性表明，数据值的选择是经过慎重考虑的。在提升模型预测准确性的关键因素中，`RAM`、电池电量和价格本身占据重要位置。这些属性在塑造模型的预测能力方面发挥了重要作用，从而实现更精确的移动电话价格预测（Figure 46.10）。

![Figure 46.10 Count plot is used to count the occurrence of the primary camera](img/fig46_10_C.jpg)

Figure 46.10 Count plot is used to count the occurrence of the primary camera

影响智能手机价格的因素包括：

- **品牌**：智能手机制造商的品牌声誉和市场存在感会显著影响其价格。知名品牌通常因其感知的质量和功能而能够收取更高的价格。
- **市场持续时间**：特定设备在移动电话市场的停留时间会影响其价格。新型号在上市初期因其尖端技术可能价格较高，而旧型号则可能因时间推移而出现价格下降（Figure 46.11）。
- **国际可用性**：智能手机的国际可用性（如供应链问题：全球商品通胀、网络因供应链中断导致的兼容性和解锁状态等）会影响生产成本，进而影响价格。提供全球可用性的设备通常会面临额外成本，这些成本可能转嫁给消费者，导致价格上涨。
- **能源价格**：制造和运输过程中的能源价格波动会影响智能手机的整体生产和分销成本。
- **劳动力短缺**：制造地区的劳动力短缺会影响生产成本，可能导致价格调整。
- **投入成本**：构建智能手机所需的材料和组件的成本会因需求、供应和全球经济状况等因素而波动。
- **市场竞争**：移动电话行业内的竞争格局也会影响定价。制造商可能会调整价格以获取市场份额或区分其产品。

需要注意的是，某些智能手机的价格可能显著高于其他手机，这归因于高级功能、高端材料和品牌影响。理解这些因素对于消费者在购买智能手机时做出明智选择至关重要。

Apple: 重要原因在于苹果使用极高质量的材料制造手机，从而保证比安卓手机更长的使用寿命。为了能够负担这些优质材料，苹果需要收取合理的价格。iPhone 通常价格超过 1,000 美元，尤其是新款机型。

Samsung: 有很多因素，下面列出：

1. 更便宜的建材 – 三星最近开始在部分 A 系列手机上加入玻璃背面，但整体上仍然使用比高端手机更低质量的金属合金和表面处理。
2. 性能较弱 – 高端系列始终采用最新的顶级规格，而 A 系列使用最新的中端处理器，性能虽低但仍然经过优化以降低电池消耗。
3. 摄像头较弱 – 采用较弱的摄像头传感器，且计算摄影能力较弱。

每个数据值都有差异，这为我们的模型提供了巨大的区分度。这就是对比图的美妙之处。因此，我们简单调用 `Seaborn` 库并使用 `Pairplot` 函数。

## Preparing data for the model

从此我们开始准备数据，确定需要什么、不需要什么。取决于我们在模型中选择的特征。价格是我们的目标变量，其余数据用于测试和训练模型。通过限制分割数量和节点大小来进行额外调整，可获得收益（Mark, 2004）。我们使用 `pandas` 将目标列分离，并利用 `sklearn` 库将数据标准化，以便将数据以数组形式输入模型，从而在移动设备价格预测模型中实现有效预测。

## Training the model

在我们的数据集中（不包括公司列），我们使用三种主要算法训练预测模型：`KNN`、`决策树` 和 `逻辑回归`。

### 决策树算法的使用

决策树是决策过程的可视化表示，通常以流程图形式呈现，用于规划和说明业务和操作决策。在机器学习领域，决策树作为算法，通过成本函数区分数据集特征。决策树最初会展开，随后通过优化剪除无关的分支。可以调整树的深度等参数，以防止过拟合并避免树过于复杂。

要实现决策树分类器，我们首先在 Jupyter Notebook 中导入 `sklearn.tree` 模块。然后调用 `DecisionTreeClassifier()` 函数创建分类器实例。为验证，可以打印数据以确认其为合适的数组形式且无错误。确认后，即可进行手机价格预测模型的预测。

创建分类器实例后，使用 `fit()` 函数在训练数据集上训练模型，随后使用 `predict()` 函数在测试数据集上进行预测。这一步骤帮助我们有效利用决策树算法（Table 46.1）

Table 46.1. Summary of parameters

| Summary ||  |
| --- | --- |
| Correctly Classified Instances 71.429% || 20 |
| --- | --- |
| Incorrectly Classified Instances 28.571% || 8 |
| Kappa Statistic 0.6177 ||  |
| Mean Absolute Error 0.2066 ||  |
| Root mean squared error 0.3668 ||  |
| Relative absolute error 54.2608% ||  |
| Root relative squared error 81.8652% ||  |
| Total Number of Instances || 28 |

### 第二种 KNN 用于预测模型

`KNN` 算法可以与最精确的模型相对比，因为它在特定情境下能提供更高的准确率。因此，它常用于需要高精度但不需要可解释模型的应用。预测性能依赖于距离度量，特别适合模式识别任务。作为受监督学习算法，它既可用于回归也可用于分类，但在机器学习领域主要用于分类。

使用 `Neighbors` 库文件对模型进行预测，与树分类器相同，只是预测函数的使用方式不同（Figure 46.12）

![Figure 46.12 Predicting the model after applying the decision tree](img/fig46_12_C.jpg)

Figure 46.12 Predicting the model after applying the decision tree

### 第三种逻辑回归用于预测模型

逻辑回归无疑是最广泛使用的机器学习算法之一，尤其在监督学习领域。其主要目标是根据给定的自变量预测二元或多分类的因变量。与产生连续结果的算法不同，逻辑回归输出的是类别或离散结果，如 "Yes" 或 "No"、 "0" 或 "1"、 "true" 或 "false" 等。不过，它并不直接给出 0 或 1 等精确值，而是生成介于 0 与 1 之间的概率值。

虽然逻辑回归与线性回归相似，但它们用途不同：线性回归用于预测连续数值的回归问题，而逻辑回归专门用于分类任务，即将数据划分为预定义的类别或组（Philipp, Wright, and Boulesteix, 2018）。

## Data with features and company columns

### Tree classifier

监督学习是数据点根据预定义值系统地组织的领域，目标是解决特定问题。在此背景下，决策树算法极为高效且易用，常被称为 `CART`（Classification and Regression Trees）。

每棵决策树包含一个根节点，根节点通过特定条件分出分支，最终到达叶子节点。树中的内部节点代表对数据集的各种测试。决策树能够同时处理分类和回归问题，在各行各业中广泛应用，提供实用的解决方案。

一个恰当的类比是：预测是通过精心调节的分支参数实现的（Seifert, Gundlach, and Szymczak, 2019）

### Random forest

随机森林算法是一种多功能的监督机器学习方法，适用于分类和回归任务。它利用集成学习概念，多个分类器协同工作以解决复杂问题并提升模型性能。在我们的价格预测模型中，加入随机森林很可能获得更精确的预测。

该算法作为分类器，基于数据集的不同子集构建多棵决策树，然后取这些预测的平均值来提高预测精度。与单棵决策树不同，随机森林汇聚多棵树的预测，这显著提升了其有效性。

### Support vector regression (SVR)

支持向量机（SVM）算法在机器学习领域广为人知，能够有效解决分类问题。

然而，尽管支持向量机（SVM）在分类任务中的应用已得到充分记录，但其在回归中的使用在机器学习文献中相对较少见。尽管如此，支持向量回归（SVR）作为一种强大的监督学习算法，用于预测连续值而脱颖而出。

`SVR` 与 `SVM` 共享基本原理，但在目标函数上有所不同。它不像 `SVM` 那样对数据点进行分类，而是寻找最合适的直线（称为超平面），该超平面在预定义的阈值内最大化地包围数据点。该阈值表示超平面与边界线之间的距离。

值得注意的是，`SVR` 的时间复杂度随着样本数量的增加而显著上升，这使得它不适合处理样本量巨大的数据集（通常超过数万）。在这类情况下，线性 `SVR` 或随机梯度下降（SGD）回归是更快的替代方案，尽管它们仅限于使用线性核。

`SVR` 模型的一个显著特征是它仅依赖于训练数据的子集。这是因为成本函数忽略了预测值与目标值非常接近的样本。这种对数据点的选择性使用显著提升了模型的效率。整个算法的结果在 Table 46.2 中给出。

Table 46.2. Top five attributes with accuracy.

| # of attributes || Accuracy % || Addition of attributes |
| --- | --- | --- |
| 1 || 25 || Display size |
| --- | --- | --- |
| 2 || 46.4 || Memory |
| 3 || 46.4 || Card slot |
| 4 || 75 || Camera |
| 5 || 75 || Video |

在特征选择的这一阶段，我们最初识别并移除了 5–7 个特定特征。因此，模型的准确率达到了峰值 92%，显著提升了预测性能。然而，当我们将随机访问内存（RAM）相关的特征加入模型时，准确率出现下降。令人惊讶的是，RAM 的加入导致模型准确率下降，这表明在该特征组合中，RAM 对预测能力贡献不大，甚至可能引入噪声或混淆，从而降低准确率（Table 46.3）。

Table 46.3 Bottom seven attributes with accuracy

| # of attributes || Accuracy % || Removal of attributes |
| --- | --- | --- |
| 10 || 71.428 || No |
| --- | --- | --- |
| 9 || 71.42 || Battery |
| 8 || 71.42 || Weight |
| 7 || 71.42 || Card slot |
| 6 || 75 || Display |
| 5 || 75 || Thickness |
| 4 || 57.14 || RAM |

在此组合中，我们实现了最高的准确率，达到令人印象深刻的 94%。特征选择过程使我们保留了 5–6 个相关特征，并丢弃了 4 个被认为信息量不足或可能带有噪声的特征。

有趣的是，当我们在选定子集之外添加更多特征时，精度出现下降。这一下降可以归因于加入那些对特定特征组合和分类器没有积极贡献的非有用数据。仔细选择特征对于确保模型的高效性和预测能力至关重要（Figure 46.13）。

![Figure 46.13 Attributes vs. accuracy of five attributes](img/fig46_13_C.jpg)

Figure 46.13 Attributes vs. accuracy of five attributes

在此特定组合中，我们实现了可喜的最高准确率 91%。这得益于选择并使用 5 个关键特征。我们在建模过程中有意排除了这些 5 个特征之外的任何其他特征。

值得注意的是，当我们将 RAM 相关特征加入模型时，准确率出现下降。这表明 RAM 代表的额外数据对于该特征组合和分类器不相关，甚至可能引入噪声或混淆，对模型性能产生不利影响。
