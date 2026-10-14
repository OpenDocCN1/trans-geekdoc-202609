
此外，Amazon SageMaker 可与更广泛的 AWS 生态系统无缝集成，确保从数据准备到模型部署的连贯工作流。您可以轻松从 Amazon S3、Amazon EFS 或 Amazon FSx for Lustre 导入数据；利用 `AWS Lambda` 函数进行预处理；并使用 Amazon SageMaker 终端节点或 `AWS Lambda` 部署模型以进行实时推理。这种紧密的集成简化了 ML 生命周期，提高了运营效率，并减少了管理 ML 管道不同组件所需的时间和精力。它还允许您利用 Amazon SageMaker 的分布式训练功能，这可以显著加速大型数据集上的模型训练。

在本节中，我们将探讨 Amazon SageMaker 提供的内置算法、其适用的用例，以及如何有效利用它们来构建稳健的 ML 模型。[图 4.8](#c004.xhtml#c04-fig-8) 可帮助您将内置算法映射到特定的 ML 问题类型、输入格式和用例。

![图 4.8 Amazon SageMaker 内置算法。](images/c04f008.png)

[图 4.8](#c004.xhtml#rc04-fig-8) Amazon SageMaker 内置算法。

## 监督 ML 算法

正如您在 [第 1 章](#c001.xhtml#c001) 中所学，监督 ML 是一种从带标签的训练数据中学习以进行预测或决策的算法类型。在监督学习中，每个训练样本都包含以特征集形式呈现的输入数据，以及相应的输出或标签。算法利用这些带标签的样本学习输入与输出之间的映射关系，随后可将这种学习到的映射应用于新的、未见过的数据以预测结果。

当输入特征与相应标签（也称为 `target variable`）之间存在清晰且预先定义的关系时，这种方法特别有用。监督学习的常见应用包括回归任务（目标是预测连续值，例如根据大小和位置等特征预测房价）和分类任务（目标是将数据归类为离散的类别，例如识别电子邮件是否为垃圾邮件）。

当有带标签的数据可用，且目标是基于这些数据进行准确预测时，应使用监督学习。在监督学习中，根据 ML 问题的性质，存在多种途径。

对于回归问题，可采用线性回归、决策树和 XGBoost 等算法来预测连续值。

在二元分类中，逻辑回归、支持向量机和 k-近邻 (k-NN) 等算法有助于区分两个类别。

对于多类分类（即数据需归类为两个以上的类别），常用决策树、随机森林和神经网络等方法。

此外，监督学习还涵盖 DeepAR 等时间序列预测算法，该算法基于过去的观测值预测未来值。而且，Object2Vec 等算法可用于创建嵌入，以捕捉对象或实体的语义信息，从而增强推荐系统或语义搜索等下游任务的性能。

### 通用回归和分类算法

本节介绍 Amazon SageMaker 提供的最常见的回归和分类监督 ML 算法。

#### Linear Learner

我们将从 Amazon SageMaker Linear Learner 算法开始，该算法为分类和回归问题提供了解决方案。

在线性回归用例中，您向算法提供带标签的样本 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mfenced close=")" open="("><mrow><mi>x</mi><mo>,</mo><mi>y</mi></mrow></mfenced></math>![x, y](images/c004_dequ1.png)。<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>x</mi></math>![x](images/c004_dequ2.png) 是特征值 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><msub><mi>x</mi><mn>1</mn></msub><mo>,</mo><msub><mi>x</mi><mn>2</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mtext>&#160;</mtext><msub><mi>x</mi><mi>n</mi></msub></math>![x sub 1, x sub 2, dot dot dot dot, x sub n](images/c004_dequ3.png) 的高维向量，而 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>y</mi></math>![y](images/c004_dequ4.png) 是表示与样本数据点关联的标签的实数。

对于二元分类问题，标签必须为 0 或 1。

对于多类分类问题，标签必须为 0 到 `num_classes` – 1。

该算法学习一个线性函数，或针对分类问题学习一个线性阈值函数，并将向量 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>x</mi></math>![x](images/c004_dequ5.png) 映射到标签 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>y</mi></math>![y](images/c004_dequ6.png) 的近似值。

Linear Learner 算法需要一个数据矩阵，其中行代表观测值（或数据点），列代表特征的维度。它还需要一个包含与数据点匹配的标签的额外列。至少，Amazon SageMaker 的 Linear Learner 要求您将输入和输出数据位置以及目标类型（分类或回归）作为参数指定。特征维度也是必需的。有关更多信息，请参阅 `https://docs.aws.amazon.com/sagemaker/latest/APIReference/API_CreateTrainingJob.html`。

您可以在请求体的 `HyperParameters` 字符串映射中指定其他参数。这些参数控制优化过程或您训练的目标函数的细节，例如 epoch 数量、正则化和损失类型。

让我们深入探讨线性回归和逻辑回归，它们分别是回归和分类 ML 问题中最常见的线性建模用例。支持向量机 (SVM) 也作为 Linear Learner 算法的另一种选择被包含在内。

##### 线性回归

线性回归是监督 ML 中最简单且应用最广泛的算法之一。线性回归的主要目标是对因变量（也称为 `target` 或 `output variable`）与一个或多个自变量（称为 `features` 或 `predictors`）之间的关系进行建模。它通过将线性方程拟合到观测数据来实现这一点。线性方程可以写成以下形式：

<math class="a" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll" display="block"><mi>y</mi><mo>=</mo><msub><mi>&#946;</mi><mrow><mn>0</mn></mrow></msub><mo>+</mo><msub><mi>&#946;</mi><mrow><mn>1</mn></mrow></msub><msub><mi>x</mi><mrow><mn>1</mn></mrow></msub><mo>+</mo><mo>&#8943;</mo><mo>+</mo><msub><mi>&#946;</mi><mrow><mrow><mi mathvariant="normal">n</mi></mrow></mrow></msub><msub><mi>x</mi><mrow><mrow><mi mathvariant="normal">n</mi></mrow></mrow></msub><mo>+</mo><mi>&#949;</mi></math>![y equals sum with variable number of summands beta sub zero plus beta sub one times x sub one plus ellipsis plus beta sub normal n times x sub normal n plus epsilon](images/MathcabEQ_0009.png)
