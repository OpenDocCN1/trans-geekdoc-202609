
# Classification

Classification models are a subset of supervised learning algorithms used to predict the likelihood that an instance belongs to a specific category or class. Unlike regression models, which output numerical values, classification models output values indicating whether an item belongs to a specific category.

Classification models fall into two categories: binary classification and multi-class classification. In binary classification, the model generates a value from a category with only two possibilities. For example, a model might predict whether a transaction is fraudulent or not fraudulent (Figure 10.2). Multi-class classification involves making predictions from multiple categories. For example, classifying weather conditions as sunny, cloudy, rainy, or snowy.

![Figure 10.2: Classification task example - predicting if a transaction is fraudulent](img/Figure10.2.png)

The table below shows several classification task scenarios:

| Target | Potential Input Variables | Predicted Classification Outcome |
| --- | --- | --- |
| Customer Churn Prediction | Customer demographics, purchase history, support interactions, feedback | Churn (Yes/No) |
| Email Spam Classification | Email content, sender information, historical spam data | Spam (Yes/No) |
| Loan Approval Prediction | Applicant credit score, income, debt-to-income ratio, employment status, loan amount requested | Loan Approved (Yes/No) |
| Customer Segment Identification | Purchase history, demographics, website interactions | Customer Segment Category: e.g., Premium, Standard, New |
| Customer Subscription Prediction | Customer activity, usage patterns, engagement with subscription-related features | Subscribed (Yes/No) |

Table 10.4: Classification Task Examples

## Unsupervised Learning

In unsupervised learning, training data lacks explicit labels, requiring the model to learn patterns and structures without explicit guidance. Unlike supervised learning, there are no labeled outputs to guide the model's learning process. This approach is particularly useful when exploring and understanding the inherent complexities and relationships within a dataset, especially when labeled examples are unavailable or difficult to obtain.

A common technique in unsupervised learning is clustering, where the model identifies natural groupings in data by finding data points that share common characteristics or patterns. Figure 10.3 illustrates a clustering schematic:

![Figure 10.3: Clustering - Unsupervised Learning](img/Figure10.3.png)

Besides clustering, there are several other unsupervised learning tasks. One is anomaly detection, which identifies data points that deviate significantly from the majority of the data. Anomaly detection can be used for applications like fraud detection, network intrusion detection, and manufacturing defect identification. Another task is dimensionality reduction, which reduces the number of features in a dataset while retaining the most important information. Dimensionality reduction can also be used for visualizing high-dimensional data.

## Reinforcement Learning

Reinforcement Learning (`RL`) is a branch of machine learning where algorithms learn by interacting with an environment. `RL` models learn through exploration, taking actions, and receiving feedback in the form of rewards or penalties. The goal of `RL` is for the agent to discover a policy—a set of rules dictating the best action to take in different situations—to maximize cumulative reward.

Reinforcement learning has been successfully applied to various tasks, such as training robots to perform manipulation tasks like grasping and pouring, and navigating unknown environments. It is also used to recommend products or content based on user interactions, and to develop AI agents capable of achieving professional-level play in games like poker.

## Generative AI

Generative AI models are deep learning algorithms capable of creating various types of content—such as images, music, articles, and even videos—using user input. A key advantage of generative AI is its ability to handle diverse inputs and outputs. For example, a model can accept text and images as input and generate video as output, or accept an image as input and generate a descriptive text caption.

### 生成式 AI 应用利用基础模型

生成式 AI 应用利用基础模型，这些模型在海量多样化数据上进行了广泛训练。此类基础模型的一个例子是大语言模型（`LLMs`），专门经过训练以处理和生成基于文本的内容。它们可以高效执行广泛的下游任务，例如问答、摘要生成和开放式内容生成。`LLMs` 可帮助企业分析数据并自动化与语言相关的任务，如报告生成。这不仅节省了宝贵的时间和资源，还提高了准确性和效率。此外，还有多模态基础模型，它们在图像、软件代码或视频上进行训练。

### ML 算法的主要挑战

ML 算法有潜力发挥高效作用，但其成功取决于一个关键因素：高质量数据。然而，获取充足、准确且相关的数据对开发者来说可能是个障碍，这使得创建可靠高效的 ML 模型变得具有挑战性。让我们看看一些主要挑战：

#### 数据量不足

训练 ML 模型的基本要求之一是大量数据。数据不足会阻碍模型学习复杂模式的能力。

**解决方案：** 您可以使用数据增强等技术，或生成合成数据，以增加可用数据的数量和多样性。

#### 低质量数据

低质量数据会严重削弱 ML 算法的性能。嘈杂、缺失或错误的数据可能导致模型产生偏差，无法捕捉数据中的潜在模式。在低质量数据上训练的模型可能会产生不准确且不可靠的预测。

**解决方案：** 实施稳健的数据预处理技术，如清洗、过滤和插补，以提高数据质量。进行彻底的探索性数据分析（`EDA`），以识别并处理异常值和离群点。

#### 无关特征

对预测或结果无贡献的特征会稀释模型性能。在训练数据中包含此类特征会引入噪声和复杂性。

**解决方案：** 执行特征选择或提取技术，以识别并仅保留最相关的特征。

#### 有偏训练数据

如果训练数据不能准确反映现实世界中数据的分布，模型可能无法很好地泛化到新的、未见过的数据。训练集中的偏差可能导致预测和决策产生偏差。

**解决方案：** 持续审查并刷新训练数据集，以确保它们始终代表应用领域。

#### 欠拟合

当模型过于简单，无法捕捉训练数据中的潜在模式时，就会发生欠拟合。这会导致性能不佳，因为模型未能学习数据集中固有的复杂性。

**解决方案：** 您可以使用更高级的算法，或向数据集添加更多重要特征。

#### 过拟合

当模型过于复杂，从训练数据中捕捉到了噪声和无关细节时，就会发生过拟合。这导致缺乏泛化能力，即模型在训练集上表现良好，但在新的、未见过的数据上表现不佳。

**解决方案：** 通过简化模型、使用正则化技术，或增加训练数据集的大小和多样性来解决过拟合问题。

### 结论

ML 是一个快速发展的领域，有潜力改变众多行业，并彻底改变我们的生活和工作方式。在本章中，我们探讨了 ML 的基本构建模块，探索了如何有效构建 ML 问题，并了解了可用的不同类型的 ML 系统。此外，我们还检视了 ML 算法的主要挑战，如欠拟合、过拟合和数据质量问题。在下一章中，我们将了解如何在 R 语言中实现不同的 ML 算法。

### 加入我们书籍的 Discord 空间

加入书籍的 Discord 工作区，获取最新动态、优惠、全球科技动态、新版本发布及作者见面会：

[`discord.bpbonline.com`](https://discord.bpbonline.com)

![](img/fm1.png)

# 第 11 章：训练机器学习模型

### 简介

训练有效的 ML 模型是更广泛的机器学习生命周期的核心组成部分。本章将概述几种基本的建模技术和概念。我们将从探索线性回归开始，这是一种广泛用于建模因变量与一个或多个自变量之间关系的方法。在此基础上，我们将了解逻辑回归，它用于估计二元结果概率的二分类任务。超越线性模型，讨论将转向决策树，它通过递归划分特征空间为区域来捕捉复杂和非线性关系。然而，这些模型的强大功能也伴随着过拟合的风险，这凸显了理解偏差-方差权衡及其对模型性能影响的重要性。扎实掌握这些基本的 ML 概念将帮助您理解权衡，并有效利用每种方法的优势。

### 结构

本章将涵盖以下主题：

*   机器学习生命周期
*   线性回归
    *   数据拆分
    *   回归评估指标
    *   使用线性回归预测 ETA
*   逻辑回归
    *   逻辑回归的似然函数
    *   分类评估指标
    *   使用逻辑回归预测贷款违约
    *   线性模型的局限性
*   决策树
*   偏差-方差权衡
*   聚类
    *   K 均值聚类

### 目标

本章涵盖与模型训练和评估相关的几个关键主题。首先，将讨论线性回归和逻辑回归的基础知识，重点介绍其用例和底层数学原理。接下来，我们将讨论决策树以及如何利用它们解决各种 ML 问题。将引入偏差-方差权衡的概念，解释其如何影响模型性能，以及在训练过程中寻找恰当平衡的重要性。最后，我们将深入探讨无监督学习技术 K 均值聚类，并了解如何使用它来发掘数据中隐藏的模式和结构。全章将提供实际示例和真实应用，以加深对这些基本 ML 模型和技术的理解。

### 机器学习生命周期

让我们开始了解 ML 生命周期的各个阶段。图 11.1 展示了 ML 生命周期阶段。

![](img/Figure11.1.png)

**图 11.1：** ML 生命周期

各阶段详细解释如下。

*   **确定业务目标：** 任何机器学习项目的第一步是确定您试图解决的问题。明确定义您旨在解决的业务问题，并量化预期收益。建立可衡量的目标和成功标准，以确保 ML 项目与组织的整体战略保持一致。
*   **构建 ML 问题：** 通过识别输入（特征）和期望输出（目标变量），将业务问题转化为机器学习问题。确定用于评估模型成功的误差指标。
*   **收集数据：** 下一步是收集和汇集与问题相关的数据。这可能涉及从各种来源收集数据，如数据库、API、文件和传感器。

### 数据预处理

收集数据后，必须对其进行处理以准备用于机器学习。这可能涉及清洗数据、处理缺失值、归一化数据，以及将数据转换为合适的格式。预处理是关键步骤，因为它会显著影响机器学习模型的准确性。

### 特征工程

特征工程是从现有数据创建新特征的过程，有助于提高机器学习模型的性能。这可能涉及创建衍生特征、组合现有特征，以及从数据中提取相关信息。

### 训练机器学习模型并评估

选择合适的算法，并在训练数据集上训练模型。使用与问题相关的指标以及泛化能力，在测试数据集上评估模型的性能。

### 模型部署

评估模型后，您可以将其部署到生产环境，用于为业务创造价值。部署可能涉及将模型与现有系统集成、创建 API 端点、监控模型性能，并根据需要进行更新。

### 监控

必须随时间监控机器学习模型的性能，以确保其保持准确和相关。建立监控系统，确保模型保持其预期的性能水平。快速检测并解决任何性能下降或异常，以维持模型的准确性和相关性。

### 线性回归

线性回归是一种用于预测连续结果变量的统计技术。尽管历史悠久，线性回归在现代数据分析中仍是一种流行且有效的方法。

线性回归的核心思想是构建一个线性模型，以捕捉因变量（`Y`）与一个或多个自变量（`X`）之间的关系。该模型通过计算输入特征的加权和，加上一个称为偏置或截距的常数项，来预测给定 `X` 时 `Y` 的期望值。数学上可表示为：

```
Y = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ + ε
```

其中：

*   `Ŷ` 是预测的结果变量
*   `β₀` 是偏置项，表示当所有 `X` 变量均等于零时 `Y` 的基准值
*   `β₁` 是与 `x₁` 相关的权重，决定了在保持其他 `X` 变量不变时，`x₁` 每变化一个单位 `Y` 所发生的变化
*   `x₁` 是单个特征或输入变量

要训练机器学习模型，我们使用带标签的示例来确定权重和偏置的最优值。在监督学习中，机器学习算法通过分析大量示例并识别出一个使损失最小化的模型来构建模型。损失是对不准确预测的惩罚，用一个数值表示单个示例中错误的程度。理想情况下，模型的预测完美无缺，损失为 0。然而，如果预测不完美，损失就会增大。训练模型的目标是找到一组权重和偏置，使其在所有示例上的损失较低。

我们的目标是获得系数估计，并确保线性模型很好地拟合可用数据。我们可以基于 `X` 的值表达对 `Y` 的预测为：

```
ŷᵢ = β₀ + β₁xᵢ
```

残差（`eᵢ`）是观测响应值（`yᵢ`）与预测响应值（`ŷᵢ`）之间的差异。残差（`eᵢ`）计算公式为 `eᵢ = yᵢ - ŷᵢ`。
