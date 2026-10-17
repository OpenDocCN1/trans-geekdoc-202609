
# 2020 第六次伊朗信号处理与智能系统会议 (ICSPIS) (伊朗马什哈德 2020.12.23-2020.12.24)

**Mehkdi Salkhhorde Hagighi**  
计算机工程与信息学院  
Sadjad大学  
伊朗马什哈德  
`haghigh@sadjad.ac.ir`

**Mohammad Javad Mashhadi Hoseini**  
计算机工程与信息学院  
Sadjad大学  
伊朗马什哈德  
`mo.mashhadi_hoseini42@sadjad.ac.ir`

## 摘要

挖掘方法可用于将人员分类为患病或健康以诊断疾病。使用多层神经网络等学习方法诊断疾病时，面临的重大挑战之一是需要用元启发式算法求解的参数选择，但这些元启发式方法中并非没有问题。在某种程度上，它们只能减少误差，而为了减少机器学习误差，必须选择合适的特征。所提方法包含两层：第一层使用果蝇算法进行特征选择，在输入层使用果蝇算法的二进制版本进行特征选择。在 UCI 数据库中各种医疗数据集上的结果表明，所提方法的准确率、敏感性和特异性分别为 98.80%。除了 PSO、FA、SHO 和 HMO 算法外，所提方法在糖尿病诊断方面也是准确的。

在医疗领域需要训练并创建一个分类模型，将健康与个体分开。在机器学习的帮助下，分类至关重要，因为它降低了使用数据和医疗医生过去信息来发现疾病隐藏模式的成本，另一方面，分类可以帮助医生诊断疾病。基于机器学习的方法有多种，其中一些使用元启发式算法输出误差。有必要进行特征选择以仅关注重要特征。在研究 [4], 2019 中，在使用灰狼优化算法 (GWO) 诊断疾病之前，利用机器学习减少疾病诊断误差。所提方法显示的准确率超过 76%，但在他们的实验中，准确率也在 73% 左右。在他们的实验中观察到，所提方法的敏感性约为 88%，特异性约为 90%。

**关键词** `特征选择`、`数据挖掘`、`果蝇算法`、`机器学习`、`疾病诊断`、`群智能`

## 1 引言

分类是根据拥有的标签将数据分为不同类别的过程，与聚类不同，这些类别是在时间之前定义的或之后创建的 [1]。分类信息有多种方法，包括支持向量机、决策树和最近邻 [2]。与患者相关的数据被用于数据挖掘方法分类心脏病、糖尿病和胃肠道疾病。据报道，健康人和患者病史中的信息可以是分析其模式和预测疾病的重要来源。对这些数据进行分析是稀缺的，且需要高水平的知识。

在其中发现它们并根据这些知识进行评估 [3]。使用模糊方法结合特征提取方法进行数据分类的医疗数据分析诊断技术。实验表明，所提方法在解决疾病诊断的现实问题方面优于其他方法。在研究 [7], 2020 中，展示了使用支持向量技术分析医疗结构。在研究 [8], 2020 中，群智能方法在数据挖掘特征选择中的优势之一是它回顾了群体智能方法来选择特征。缺点之一是它被用于各个领域的数据问题，医学领域在特征数量或维度方面，这导致当专门使用机器学习算法时，“大维度”会产生时间挑战和分类误差。特征选择是一项选择少量且信息丰富的特征子集以提高性能的重要技术。

- 在研究 [9], 2020 中，提出并建模了一种基于混沌的用于医疗诊断的支持向量机优化算法。实验结果表明，所提方法在分类性能和特征子集大小方面优于其他竞争对手。
- 在研究 [10], 2020 中，介绍并展示了用于癌症诊断的基于混沌的支持向量机优化算法。实验结果表明，所提方法在分类性能上优于其他对手。
- 在研究 [13], 2020 中，使用了遗传算法 (GA) 用于肝炎诊断的分类方法。实验结果表明，所提方法在分类性能和特征子集大小方面优于现有方法。

根据综述，所提方法尝试克服的神经网络局限性如下：

- 在这些研究中，支持向量机被用于分类和分析疾病，主要的挑战是支持向量机的复杂性，所提方法使用了神经网络。
- 在研究中，优化算法被用于机器学习中的参数选择，重要的挑战是分类不仅取决于参数选择，还需要特征的最优选择。
- 在某些方法中，特征选择被用于减少误差。所提方法通过果蝇算法优化神经网络的参数以减少分类误差。

在研究中，果蝇算法被用于特征选择以提高准确率和发现。因此，所提方法尝试通过神经网络的优选择来增加准确率和发现。

本文的目标包括通过改进的机器学习和群智能使用果蝇算法进行疾病诊断，并在医学应用于特征选择。为此，使用了果蝇进化算法，它具有很强的空间搜索能力，优于遗传算法等粒子群优化算法。本文由若干部分组成：首先描述神经网络和果蝇算法，然后解释所提方法，接着展示所提方法的实验和分析，最后给出结论。

## 2 多层神经网络

多层神经网络根据大脑的信息处理结构和功能进行建模。多层神经网络是神经网络的一种示例，具有输入层、隐藏层，在这种类型的网络中，在输入层和输出层之间有隐藏层。每一层都有人工神经元，其任务是对输入起作用并提供输出函数。

人工神经元可以将输入映射为权重，并将它们加到某些基上，利用激活函数产生最终输出。

## 3 果蝇优化算法

果蝇优化算法是一种具有群体智能方法的元启发式算法，用于解决问题，其性能如图 1 所示。可以看到，最优解被视为猎物和食物位置，其他解向该最优解飞去。

![图 1：果蝇算法的最优解性能 [12]](img/2850741be238fbb31e5292a4a6444119_1_0.png)

果蝇优化算法基于果蝇探测食物的能力。果蝇在嗅觉和视觉能力方面优于其他物种。因此，它利用这两种方式来寻找食物。果蝇可以通过视觉和搜索放置食物的区域来感知食物。该算法提出的是问题的每个解都被视为决策变量的向量，如公式 (1) 所示。随后在随机问题空间中创建初始解种，其中每个解是使用如方程 (3) 等评估函数进行评估，并定义了每个函数的适用性。

```
$X_i = <<\nX_{i,1}, X_{i,2}, ..., X_{i,d} = <<\n\n\alpha + \beta = \chi.$
```

在这些关系中，$D_i$ 是第 $i$ 个解距离最优解的距离，$S_i$ 是解的适应度和适应度度。在算法中，在水平和垂直维度上产生最大奖励（可以使用函数进行评估）的最优解的位置被视为 `bestsmell`。然后将它的水平和垂直位置放置在步长变量中，如方程 (10) 和 (11) 所示：

```
$X_{1,1} X_{1,2} ... X_{1,d}\nX_{2,1} X_{2,2} ... X_{2,d}\nX_{m,1} X_{m,2} ... X_{m,d} = Pop$
```

```
$X_{axis} = X(bestsmell)\nY_{axis} = Y(bestsmell)$
```

```
$Pop = f(X_{1,1} X_{1,2} ... X_{1,d}), \f(X_{2,1} X_{2,2} ... X_{2,d}), \f(X_{m,1} X_{m,2} ... X_{m,d})$
```

疾病设计中的重要挑战之一是将健康人与病人进行分类，另一个挑战是如果数据特征和样本数量很大，误差较大的学习方法会设计错病人。为了解决这个问题，该方法具有以下两个层：

- 使用果蝇算法通过特征选择与疾病相关的适当性，并减少数据维度。
- 使用果蝇算法优化人工神经网络的权重和偏置，以减少其在疾病分类中的误差。

在这些关系中，$S_i$ 是质量或果实职责，种群数量，$f$ 是目标优化的函数。每个解都可以在水平或垂直维度空间中随机运行，如方程 (4) 和 (5) 所示：

```
$X_{axis} = rands(1,2)\nY_{axis} = rands(1,2)`
```

在这些关系中，适应步长在 1 和 2 之间，是随机的。根据关系 (4) 和 (5) 中适应步长的大小，蝇可以在水平或垂直方向上扩展其维度，如 (6) 和 (7) 所示：

在区分病人和健康人的多层神经网络中，在数据集中收集了患者和健康样本，并平均划分样本。训练样本用于训练和创建人工神经网络中的学习模型，该模型在训练后需要进行评估以计算其准确率和误差。区分病人和健康人的难度意味着问题所在。该模型可以用于确定区分病人与健康人的准确性。区分病人与健康人的误差取决于多种因素，最重要的是哪些特征区分了病人和病人。所有特征都用于训练人工神经网络，因为它们并不同等重要，因此可以预期这种重要性将导致问题维度和数据很大。这种现象也增加了执行时间。为了减少或修改这些问题，可以使用特征选择，利用 (2) 中的元启发式算法作为框架来减少人工网络。这更大。在这种背景下，区分病人和健康人的重要阶段如下：

```
$X_i = X_i + RandomValue\nY = Y_i + RandomValue`
```

为了评估每个解其距离食物或最优答案的距离，可以计算：

```
$D_i = \sqrt{X_i^2 + Y_i^2}`
```

每个解的值可以根据其与最优解的倒数距离 (9) 来考虑：

```
$S_i = \frac{1}{D_i}`
```

特征集被视为元启发式算法的成员。

- 随机生成疾病相关的特征向量
- 使用特征向量进行人工神经网络训练
- 选择最优特征向量
- 更新疾病相关的特征向量
- 重复？
- 否
- 数据

使用最优特征向量进行神经网络神经网络训练并创建分类模型。

- 从人工神经网络中选择最优权重和偏置
- 健康
- 病人
- 以元创新算法或果蝇优化算法成员的形式对特征向量编码。
- 生成具有 0 和 1 的属性向量初始随机种群。
- 每个特征向量都用于学习人工神经网络。
- 在每次迭代中，选择最优特征向量并使用元启发式算法更新。
- 以此，以多层网络权重和偏置的形式将特征编码传递给元启发式算法。它持续到人工神经网络的最优权重和偏置。
- 最后一次迭代中最优特征向量用于学习和具有最优权重和偏置的。

为了评估每个属性向量，可以考虑两个重要因素，并根据这些因素重写目标函数：

- 误差因素与疾病有关，使用果蝇算法特征选择减少数据维度。
- 使用果蝇算法优化人工神经网络的权重和偏置以减少其在疾病分类中的误差。

## 4 实验结果与分析

将所提方法与其他现有的疾病分类方法进行比较。结果显示，所提方法在准确率、灵敏度和特异性方面更好。结果显示，所提方法的准确率、灵敏度和特异性分别为 100%。区分病人和健康人的难度意味着问题所在。该模型可以用于确定区分病人与健康人的准确性。区分病人与健康人的误差取决于多种因素，最重要的是哪些特征区分了病人和病人。所有特征都用于训练人工神经网络，因为它们并不同等重要，因此可以预期这种重要性将导致问题维度和数据很大。这种现象也增加了执行时间。为了减少或修改这些问题，可以使用特征选择，利用 (2) 中的元启发式算法作为框架来减少人工网络。这更大。在这种背景下，区分病人和健康人的重要阶段如下：

此类健康人群分类的准确率、灵敏度和诊断能力。

数据挖掘机器学习的重要应用之一是诊断如糖尿病等疾病。本文提出了一种通过增强多层神经网络的特征选择和权重偏差的方法，以减少数据分类错误和模式样本。实验表明，所提方法优于现有方法。通过结合特征选择和优化神经网络权重，糖尿病疾病中使用的机器学习和分类基础错误降低了 32%，且所提方法的准确率、灵敏度和检测能力得到了提高。未来的研究将尝试识别其他疾病（例如心脏病、肝脏疾病）以及与多种疾病相关的数据集。

## 5 结论

本文提出了一种基于果蝇算法的两阶段疾病诊断方法，结合特征选择与神经网络参数优化，在糖尿病等疾病诊断中取得了优于现有方法的分类性能。

## 参考文献

- [1] Alazoubi, L., Fahed, M. A., Olwei, S. R., Al-Shamma, O., & Zhang, J. (2020). QUTNet: diabetic foot ulcer classification using novel deep convolutional neural network. *Methods in Applications*, 15(1), 247-254.
- [2] Nalli, S., Rahmani, R. V., Ramasubahari, S., Govinda, K., & Swetha, S. (2020). Chronic Heart Disease Prediction Using Data Mining Techniques. In *Data Engineering and Communication Technology* (pp. 903–910). Singapore: Springer.
- [3] Islam, M. F., Ferdosi, R., Rahman, S., & Bushra, H. Y. (2020). Likelihood prediction of diabetes at early stage using data mining technology Support Vector Machine and Machine Learning in Medical Image Analysis (pp. 113-125). Springer, Singapore.
- [4] Shankar, A., & Mashkandari, S. (2019). Diagnosis of Diabetes Diseases Using Fuzzy Rule Set by Gray Optimization. *Pattern Recognition Letters*.
- [5] Alam, M. M., Khan, M. S., & Rahman, M. S. (2019). A Random Forest based predictor for medical classification using feature attention mechanism. *Medical Informatics*, 22, 101908.



- [6] Dao, H., Naik, B., & He, S. (2020). Medical disease analysis using fuzzy logic with feature selection for classification. In *Informatics*, 7(4), 101628.

- [7] Li, T., Li, Z., Zhao, W., Li, X., Xu, X., Pan, S., ..., & Li, J. (2020). Analysis of medical rescue strategies on a rough and genetic algorithm based classification perspective. *International Journal of Disaster Risk Reduction*, 42, 101325.

- [8] Nguyen, B. H., Xue, B., & Zhang, M. (2020). A survey on intelligence approaches to feature selection in data mining. *Swarm and Evolutionary Computation*, 54, 100683.

- [9] Wang, M., & Chen, H. (2020). Chaotic multi-wave optimizer support vector machine for medical diagnosis. *Applied Soft Computing*.

- [10] Demir, F. B., Tancer, C., Kocamaz, A., & Ertam, F. (2020). A survival classification method for hepatitis patients with chaotic diabetes optimization method based feature selection. *Medical*.

- [11] Sujitha, M., Sujitha, R., Nitha, R., Nandini, A. S., & Harsh, N. (2020). An Diabetes Risk Assessment System Using IoT Cloud Based Artificial Neural Network for Cognitive Computing. In *Cognitive Computing* (pp. 322–327). Springer.

- [12] Shen, L., Chen, H., Yu, Z., Wang, Z., Zhang, B., Li, H., ..., & Li, D. (2016). Evaluating support vector machine using feature property optimization for classification. *Soft Computing*, 96, 61-75.

- [13] Parisi, L., & Ravichandran, N. (2020). Evolutionary feature formation improving prognostic forecast of hepatitis. *Knowledge-Based Systems*, 299, 106012.
