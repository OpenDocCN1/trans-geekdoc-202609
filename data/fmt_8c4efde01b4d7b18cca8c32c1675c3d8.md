
在医疗应用领域（如分类、疾病预测等）中，对医疗数据的分类日益受到重视。除了学习外，神经系统还具有其他显著优势，包括能够分离噪声、易受影响或不精确的特性。因此，特征选择的重要性在于它将分类器的能力限制在被认为在精确分类中相关的测量范围内。本工作的主要目标是整理医疗数据，并探讨利用独特输入特征和分类器的可行性，以识别医疗数据集。本文提出了深度神经网络（`DNN`）用于分类。结果显示，拟议的 `DNN` 分类器在慢性肾病（`CKD`）数据集上，其准确率、灵敏度和特异性均高于传统机器学习（`ML`）分类算法。

**Keywords:** 深度学习, 慢性肾病 (`CKD`), 特征提取, 分类

## Introduction

肾脏是人体最复杂的器官之一，执行多项功能。肾脏在尿液形成过程中排出废物，帮助净化血液。肾脏还参与体液、电解质和酸碱平衡的调节。了解肾脏是理解和处理药物的关键，因为若肾脏功能不佳，药物处理会受到影响 (`Luck et al., 2016`)。全球范围内，与这些疾病相关的发病率正在上升，影响各地区和所有经济阶层。

肾脏参与多种激素功能，包括预防贫血和维生素 D 缺乏。维生素 D 在体内注射后，需经肾脏激活才能发挥作用。肾脏还参与血细胞生成 (`Singh and Singh, 2020`)。肾脏合成的激素 `erythropoietin` 作用于骨髓，促进红细胞（`RBC`）的产生。若肾脏功能不正常，该激素水平下降，患者易出现贫血 (`Alloghani et al., 2020`)。

血压调节是肾脏功能的另一重要方面。肾脏细胞分泌的激素 `renin` 对血压调节至关重要。若肾脏功能受损，这些表现将会显现。肾脏的结构和功能单元是肾小球 (`Harimoorthy and Thangavelu, 2021`)。每个肾脏含有数百万个肾小球。血液经血管进入肾小球。由于肾脏作为血液过滤器，是人体最重要的血管器官之一，约占心输出量的 25%。心脏疾病可影响肾脏功能。心脏问题是导致肾功能受损的主要原因之一。血液在肾小球进行滤过，随后形成尿液 (`Khamparia et al., 2020`)。

糖尿病和高血压是印度最常见的两种肾脏疾病原因。其他主要影响女性的肾脏疾病，根据 `Feng et al. (2016)` (`Li et al., 2014`) 所述。泌尿道感染和自身免疫性疾病（如类风湿性关节炎和系统性红斑狼疮（`SLE`））可导致肾脏瘢痕。随着肾脏功能逐渐丧失，慢性肾病（`CKD`）随之出现，进程可慢亦可快。了解其根本原因有助于正确启动治疗，保持肾脏健康 (`Mushtaq et al., 2022`)。糖尿病是肾脏疾病的主要原因。若糖尿病患者未加以管理，或病程较长，血液中过多的糖分会破坏血管，导致肾功能下降。据 Adeniyi 等人（2016）指出，肾衰竭主要由高血压（即高血压）引起，这是影响肾功能的第二大因素。若不治疗，肾脏血管可能遭受永久性损伤 (`Fatima and Pasha, 2017`) (`Figure 47.1`)。

![Figure 47.1  Causes of CKD](img/fig47_1_C.jpg)

Figure 47.1  Causes of CKD

## Literature review

`Bala and Kumar (2014)` 对 47,204 名中国成年人进行横断面调查，旨在测定 `CKD` 的患病率。收集的数据包括生活方式、病史、血压、血清肌酐和白蛋白尿。农村地区的 `CKD` 患病率总体为 10.8%。与其他地区相比，北部（16.9%）和西南部（18.3%）的患病率最高。年龄、高血压、性别、糖尿病、心血管疾病史、高尿酸血症、居住地、社会经济水平等因素均与肾脏损伤独立相关。

为了探讨肾脏疾病事件与死亡及终末期肾病（`ESRD`）在有无糖尿病人群中的关系，`Rubini and Eswaran (2015)` 进行了一项元分析（`Rubini and Eswaran, 2015; Thakur et al., 2021`）。选取的文献依据 `CKD` 预后联盟设定的标准。利用 Cox 比例危险模型计算了 `eGFR` 和白蛋白尿与死亡及 `ESRD` 的危险比。分析纳入 128,505 名糖尿病患者和 1,024,977 名来自普通人群、高风险心血管人群以及 13 个 `CKD` 人群的参与者。糖尿病患者的死亡风险比无糖尿病者高 1.3 倍。

根据 `Kunwar et al., (2016 a)`，糖尿病和高血压导致印度糖尿病患者 40–60% 为慢性肾病（`CKD`）患者。印度成年人口的糖尿病患病率从 Jharkhand 的 5.3% 到 Chandigarh 的 13.6% 不等。约 10.4% 的泰米尔纳德邦（Tamilnadu）Kanchipuram 和 Thiruvallur 地区居民患有糖尿病。显然，这是印度慢性肾病（`CKD`）发病率上升的主要目标人群，因此需要进一步开展糖尿病和高血压的控制研究，以避免并发症。为教育公众了解 `CKD` 的阶段及如何控制糖尿病和高血压，需要在印度开展更多的 `CKD` 筛查研究。该研究的目标是确定印度的 `CKD` 患病率。

`Chetty et al. (2015)` 在门诊开展，旨在评估自行测血压方案、门诊随访以及激励性电话呼叫对糖尿病和肾病患者血压管理及药物依从性的帮助作用（`Kunwar et al., (2016 b)`）。参与者随机分为干预组和对照组。干预组在 3 个月内进行（n = 39），随后在干预后 3、6、9 个月进行随访（n = 41）。研究结果显示，两组之间未出现统计学显著差异，但干预组（n = 36）的平均收缩压下降了 6 mmHg。

在澳大利亚，由 `Chen et al. (2019)`（`Singh et al., 2009`；`Chetty et al., 2015`）进行的随机对照研究也持续了三个月（n = 21），并在干预后 3、6、9 个月随访（n = 8）。

2015 年，Jerlin Rubini 和 Eswaran（`Chen et al., 2019`）比较了四种分类算法（随机森林 `RF`、决策树 `DT`、随机树 `RT`、简单 `CART`）的分析结果。对于医疗领域专家而言，拥有适当的 `CKD` 预测模型至关重要。由于大量医疗信息仍为非结构化，需要高效模型来提取有价值的洞察。基于数据分类算法的机器学习（`ML`）技术能够发挥重要作用。作者从 `UCI` 存储库中对 `CKD` 数据集进行分类，结果表明所提的 `RF` 方法在准确率、精确率和召回率方面取得了最佳分类效果。

## System methodology

### Pre-processing

分析数据首先需进行筛选，以避免误导结果。因此，首先检查数据的质量和表示。大量非结构化数据包含大量冗余和无关信息，且数据呈噪声和不可靠性（`Zheng et al., 2015`）。训练阶段比发现的知识更为复杂，一般需要较长的处理时间以完成数据过滤和准备。结果受原始数据的质量、缺失值以及不一致性影响。数据预处理在数据挖掘过程中能够提升效率和数据质量。

数据预处理是数据挖掘中的重要步骤，这一阶段负责对数据集进行转换和准备，以便后续处理。在预处理过程中，非数值型数据被转换为数值型数据。获得数值数据后，非数值型数据被移除（`Rubini and Eswaran, 2015`）。除其他属性外，不考虑缺失值的属性。其他属性的观测依据某一属性缺失值的分布进行。在本研究中，选取 `UCI ML` 仓库的 `CKD` 医疗数据集用于 `CKD` 诊断。

### Feature reduction

特征维度降低旨在提升预测准确率。为降低高维数据的维度，需更深入地理解底层数据结构。高维数据难以感知且难以分析（`Sornam and Prabhakaran, 2018`）。通过维度降低，可实现特征转换或特征选择。当特征数量较多时，分类任务变得困难。在不损失分类准确率的前提下，特征应被压缩；因此本研究应用了特征维度降低方法。该过程去除噪声或冗余信息，并减少特征数量。通过开发 `OLPP` 算法，将特征向量维度进一步压缩。线性判别分析（`LDA`）和主成分分析（`PCA`）是两种不同的分析方法，用于区分 `OLPP` 算法。

在维度降低过程中，`PCA` 是初始步骤，而 `OLPP` 用于构建邻接图。样本点之间的类关系通过最优特征选择体现，而 `OLPP` 则用于构建邻接图。根据低维空间中的结构，可以将维度降低方法划分为线性和非线性。在映射矩阵方面，`OLPP` 解决了正交基问题，并具备维度降低的特性。

*Algorithm 47.1* 特征降低

### Classification

分类旨在寻找有类标签的实例集合中属性之间的显性或隐性规律。一般假设是基于这些关系和/或规律建立的。在拥有已建立的预测特征以及未知类标签的情况下，假设结果用于对未来未见实例进行预测。分类问题主要涉及医学预后和诊断。患者的医疗数据依据临床、病理和人口学数据预测其预后。

## Proposed DNN model

`DNN` 的核心组件是卷积层，大部分复杂计算在此层完成。该层的主要目标是通过卷积核与输入信号之间的卷积，从图像中提取属性或视觉属性。模型还包含全连接层、Softmax 层以及四个卷积层，如 `Figure 47.2` 所示。网络输入为一个 160 × 190 × 3 的光谱图。每个卷积层之后使用指数线性单元（`ELU`）激活函数以及 3 × 3 的最大池化层，池化步长为 2。`ELU` 作为激活函数比常见的 sigmoid 函数更能提升训练过程的有效性（`Figure 47.3`）。

```
[Figure 47.2  Block diagram of the proposed approach for CKD prediction]
```

![Figure 47.2  Block diagram of the proposed approach for CKD prediction](img/#ch47.xhtml#R_fig47_2)

![Figure 47.3 Architecture of proposed DNN mode](img/#ch47.xhtml#R_fig47_3)

- 输入层（第 0 层）使用 `32` 位核大小进行卷积，随后经过 `ELU`，生成第 1 层（顶层）。`3 × 3` 核由标记为 `32` 的核用于卷积选定区域。然后，每个特征图在之后（第 2 层）进行大小为 3、步长为 2 的最大池化。第 3 层是通过将第 2 层的特征图与一个核（64 位滤波器）进行卷积而创建的。每个特征图（第 4 层）随后经过另一次最大池化，结果是 40 × 48 × 64 的缩减。然后，第 6 层和 `ELU` 通过将第 5 层的特征图与大小为 128 的滤波器卷积生成。随后，每个特征图进行大小为 3 的最大池化，将神经元数量降低到 20 × 24 × 128（第 6 层）。随后，第 7 层通过将第 6 层的特征图与大小为 256 的核（滤波器）卷积创建。第 8 层的最大池化执行一次后，结果为 10 × 12 × 256。最终，第 9 层提供 30,720 个完全连接的神经元，然后将神经元发送到第 10 层，即 softmax 层。

```
Algorithm 47.2 Proposed DNN
```

## Result and discussion

### Performance measures

Several performance measures are used to analyze the efficiency of the proposed and existing algorithms. The accuracy, sensitivity, and specificity have been used to evaluate the performance of the proposed algorithm.

## Accuracy

It calculates the global prediction rate is determined by dividing the number of successfully classified CKD by the total number of CKD affected patients used for classification, yielding the following ratio,

$$\text{Accuracy~} = \frac{TP + TN}{TP + TN + FP + FN}$$

## Sensitivity

Sensitivity is a metric that assesses the likelihood that CKD will be present in the patient population. It is determined by dividing the total number of CKD patients by the proportion of correctly categorized CKD dataset.

$$\text{Sensitivity~} = \frac{TN}{TP + FN}$$

## Specificity

Specificity is a metric that establishes whether or not a person has the CKD ([Table 47.1). The ratio of correctly categorized normal person to total CKD affected patients is what determines follows,

Table 47.1. CKD dataset description.

| Attribute name || Description of the attribute |
| --- | --- |
| Age || Patients age is main criteria |
| Blood pressure || The sign of heart rate should be measure |
| Specific gravity || Measure urine density ratio compared with water density |
| Albumin || The total amount of protein in the urine is indicated |
| Sugar || The high level sugar in the urine must show |
| Red blood cells || The high amount of red blood cells in urine must be specified |
| Pus cell || Major and minor infections must be indicated |
| Pus cell clumps || Bunch of pus cells and infections to be identified |
| Bacteria || Identification of kidney infection and growth level of bacteria |
| Blood glucose random || Glucose (sugar) level should be checked |
| Blood urea || To measure the urea nitrogen in blood amount |
| Serum creatinine || To identify the amount of creatinine in blood |
| Sodium || To show the amount of sodium in blood |
| Potassium || To show the amount of potassium in blood |
| Hemoglobin || Protein in red blood cells must specify |
| Hypertension || Top level blood pressure must be indicated |
| Red blood cell count || Determine an amount of red blood cells in blood |
| White blood cell count || Finding the amount of white blood cells in blood |
| Packed cell volume || To measure the percentage of cells in blood |
| Diabetes mellitus || Must show the top stage of blood sugar |
| Coronary artery disease || Heart disease must be identified which affects the kidney function |
| Appetite || Detecting the loss of appetite |
| Pedal edema || Determination of legs swelling |
| Anemia || Low level of red blood cells or hemoglobin must specify |

$$\text{Sensitivity~} = \frac{TN}{TP + FN}$$

`DNN` achieved the highest performance. The accuracy, sensitivity and specificity measure of `DNN` were 98.89%, 98.56% and 93.23%. Table 47.2 and Figure 47.4 illustrate the performance analysis of the proposed `DNN` for `CKD` dataset.

Table 47.2  Performance of the proposed DNN.

| CKD dataset  ||  ||  ||  |
| --- | --- | --- | --- |
