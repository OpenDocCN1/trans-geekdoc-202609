
# 机器学习简明入门指南：Supervised and Unsupervised Learning 入门

![img](img/cover.jpg)

## 机器学习简化

## 机器学习入门：监督学习与无监督学习

**Jose George**

Welcome to introduction to machining learning.

Machine learning is creating rapid and exciting changes across all levels of society.

*   It is the engine behind the recent advancements in industries such as autonomous vehicles.
*   It allows for more accurate and rapid translation of the text into hundreds of languages.
*   It powers the AI assistants you might find in your home.
*   It can help improve worker safety.
*   It can speed up drug design

Machine learning is a complex subject area. Our goal in this lesson is to introduce you to some of the most common terms and ideas used in machine learning. I will then walk you through the different steps involved in machine learning and finish with a series of examples that use machine learning to solve real-world situations.

在传统的软件问题解决中，人分析问题并编写代码以解决该问题。对于许多现实问题，这一过程可能费时费力（甚至是不可能的），因为正确的解决方案需要考虑大量的边界情况。

想象一下，挑战性的任务是编写一个程序来检测图像中是否存在猫。传统方式下，需要仔细关注诸如光照条件变化、不同种类的猫以及猫可能处于的各种姿态等细节。

在机器学习中，问题解决者将解决方案的一部分抽象为一个灵活的组件，称为模型，并使用一种特殊的程序——模型训练算法，对该模型在真实数据上进行调整。结果是一个经过训练的模型，可以用于预测训练数据集中未包含的结果。

在某种程度上，机器学习自动化了传统问题解决者所做的统计推理和模式匹配。

总体目标是使用由模型训练算法创建的模型，生成预测或在数据中发现模式，以解决问题。

*   AWS 提供最全面的云服务，专为机器学习优化。
*   机器学习在 AWS 上的规模远超其他任何地方。

## AWS Machine Learning offerings

在 AI 服务方面，你不一定需要从零编写机器学习解决方案。AWS 预训练的 AI 服务提供即插即用的智能，直接用于你的应用和工作流。你只需将这些服务应用于自己的使用场景即可。

Amazon 有不同的健康 AI 服务，无需机器学习知识即可使用。其中一个例子是 `Amazon Transcribe Medical`，它将医疗语音转换为文本。医护人员与患者之间的对话构成了患者诊断和治疗的基础。准确性至关重要。`Amazon Transcribe Medical` 是一种自动语音识别（ASR）服务，用于短时录音。

### AWS AI services

通过使用 AWS 预训练的 AI 服务，你可以将即插即用的智能应用于广泛的应用场景，如个性化推荐、联系中心现代化、提升安全与安全性以及提高客户参与度。

### Industry-specific solutions

无需机器学习知识，即可为医疗、制造等不同行业的应用添加智能。

### AWS Machine Learning services

AWS 让你能够快速构建、训练和部署模型。`Amazon SageMaker` 是一个完全托管的服务，消除了 ML 工作流的复杂性，使每个开发者和数据科学家都能为各种用例部署机器学习。

### ML infrastructure and frameworks

AWS 工作流服务简化了管理和扩展底层机器学习基础设施的难度。

![Image](img/image38.png)

### Getting started

除了 `AWS Training and Certification` 等教育资源外，AWS 还创建了一系列教育工具，帮助开发者以独特且有趣的方式将新的机器学习技术投入使用，如 `AWS DeepRacer` 和 `AWS DeepComposer`。

*   **AWS DeepRacer**：一种设计用于通过物理赛道测试增强学习模型的自主赛车。
*   **AWS DeepComposer**：一种由生成式 AI 驱动的创作设备，能够将旋律转化为全新原创歌曲。
*   **AWS ML Training and Certification**：用于培训 Amazon 开发者的课程。

![Image](img/image39.png)

## AWS Account Requirements

### 需要 AWS 账户

要完成本课程的练习，你需要一个 `AWS Account ID`。

然而，你无需完成本课时的练习才能从基础课程毕业。本课时包含的练习标记为 `OPTIONAL ONLY`，如果你无法创建 AWS 账户，只需阅读练习模块即可了解这些工具的工作方式。

要设置新的 `AWS Account ID`，请参考“如何创建并激活新的 Amazon Web Services 账户？”的说明。

创建账户时需要提供付款方式。如需了解哪些服务免费，请参阅 `AWS Free Tier` 文档。

### 这些练习会产生费用吗？

本课时包含大量演示和练习。你 `do not` 需要购买任何 AWS 设备即可完成本课。但请仔细阅读以下可能用于演示和完成练习的 AWS 服务列表。

#### 使用 AWS DeepRacer 训练强化学习模型

*   使用 `AWS DeepRacer` 入门，你将在首月获得 `10 小时免费` 用于训练或评估模型，以及 `5GB 免费存储空间`。这足以训练第一个时间试验模型、对其进行评估、调优，然后将其提交至 `AWS DeepRacer` 联盟。`此优惠在你首次使用服务后 30 天内有效`。
*   超过 `10 小时` 的训练和评估后，你需要为训练、评估和存储机器学习模型付费。费用基于你为新模型训练和评估的时间以及存储模型的大小。想了解 `AWS DeepRacer` 计费细节，请参阅 `AWS DeepRacer Pricing`。

#### 使用 AWS DeepComposer 生成音乐

*   入门时，`AWS DeepComposer` 为首次用户提供 `12 个月免费额度`。免费额度允许你最多进行 `500 项推理任务`，即可生成 `500 件音乐`，使用 `AWS DeepComposer Music Studio`。你可以使用其中一个实例免费完成练习。想了解 `AWS DeepComposer` 的费用，请参阅 `AWS DeepComposer Pricing`。

#### 构建自定义生成式 AI 模型（GAN）使用 Amazon SageMaker（可选）

*   `Amazon SageMaker` 是独立服务，拥有自己的计费和计费等级。要训练自定义生成式 AI 模型，教练使用的实例类型不在 `Amazon SageMaker` 免费额度范围内。如果你想与教练一起编码并训练自己的自定义模型，可能会产生费用。请注意，创建自定义模型完全是可选的，完成本课程不需要完成此练习。想了解 `SageMaker` 的费用，请参阅 `Amazon SageMaker Pricing`。

请确认你已完成本课时所需的必要步骤。

*   我拥有 `AWS 账户 ID`
*   我理解，要完成本课程，无需购买 `AWS DeepRacer` 或 `AWS DeepComposer` 设备。
*   我理解，在首次使用 `AWS DeepRacer` 后的 30 天内，我有 `10 小时免费` 的模型训练和评估时间，用于完成 DeepRacer 部分的演示和练习。
*   我理解，`AWS Free Tier` 为我提供 `500 项 AWS DeepComposer 推理任务`（即 500 件音乐）免费。
*   我理解，“构建自定义 GAN” 演示是可选的，我可以观看演示而不是自己完成，因为我可能需要为完成该练习承担费用。
*   我理解，我可能需对我的 AWS 账户中产生的任何费用负责。

## 强化学习及其应用

本节介绍一种叫强化学习（RL）的机器学习类型。你会了解其实际应用，并通过 `AWS DeepRacer` 示例学习基本概念。本节结束时，你将能够在 `AWS DeepRacer` 控制台创建、训练和评估强化学习模型。

在强化学习（RL）中，代理（agent）通过与环境交互，根据收到的反馈来训练达成目标。它为每个采取的动作获得一个数值奖励。有助于代理达成目标的动作会获得更高的奖励，无帮助的动作则获得低奖励或无奖励。

以最大化总累计奖励为学习目标，随着时间的推移，代理通过试错学会在不同情境下映射有价值的动作。训练得更好的代理能更高效地选择能实现目标的动作。

### 强化学习应用

强化学习在多个领域用于解决实际问题，特别适用于具有长期目标的顺序性问题。以下是一些示例。

*   RL excels at **playing games**:
    *   Go (board game) was mastered by the AlphaGo Zero software.
    *   Atari classic video games are commonly used as a learning tool for creating and testing RL software.
    *   StarCraft II, the real-time strategy video game, was mastered by the AlphaStar software.
*   RL is used in **video game level design**:
    *   Video game level design determines how complex each stage of a game is and directly affects how boring, frustrating, or fun it is to play that game.
    *   Video game companies create an agent that plays the game over and over again to collect data that can be visualized on graphs.
    *   This visual data gives designers a quick way to assess how easy or difficult it is for a player to make progress, which enables them to find that “just right” balance between boredom and frustration faster.
*   RL is used in **wind energy optimization**:
    *   RL models can also be used to power robotics in physical devices.
    *   When multiple turbines work together in a wind farm, the turbines in the front, which receive the wind first, can cause poor wind conditions for the turbines behind them. This is called wake turbulence and it reduces the amount of energy that is captured and converted into electrical power.
    *   Wind energy organizations around the world use reinforcement learning to test solutions. Their models respond to changing wind conditions by changing the angle of the turbine blades. When the upstream turbines slow down it helps the downstream turbines capture more energy.
*   Other examples of real-world RL include:
    *   **Industrial robotics**
    *   **Fraud detection**
    *   **Stock trading**
    *   **Autonomous driving**

![Image](img/image40.png)

## 新术语

*   **Agent**：你正在训练的软件称为 agent。它在环境中做出决策以达成目标。
*   **Environment**：环境是代理交互的周围区域。
*   **Reward**：代理在给定状态下每个动作的反馈是数值奖励。
*   **Action**：对于每个状态，agent 需要采取动作以实现目标。

## 强化学习与 AWS DeepRacer

### 强化学习概念

本节将使用 `AWS DeepRacer` 为例，学习一些基础强化学习术语和概念。

本节介绍六个基础强化学习术语，并为每个术语在 `AWS DeepRacer` 语境中提供示例。

![Image](img/image41.png)

### 基础 RL 术语：Agent、environment、state、action、reward、episode

#### Agent

*   你正在训练的软件称为 agent。
*   它在环境中做出决策以达成目标。
*   在 `AWS DeepRacer` 中，agent 是 `AWS DeepRacer` 小车，其目标是在尽可能快地完成 * laps（圈数）的同时，在某些情况下避免障碍。

#### Environment

*   环境是代理交互的周围区域。
*   对于 `AWS DeepRacer`，这是模拟器中的赛道或真实世界中的赛道。

#### State

*   状态是代理当前在环境中可见或已知的位置。
*   在 `AWS DeepRacer` 的情况下，每个状态都是由它的摄像头捕获的图像。
*   车辆的初始状态是赛道的起始线，其终止状态是当车辆完成一圈、撞击障碍物或驶离赛道时。

#### 动作

*   对于每个状态，代理需要采取一个动作以实现其目标。
*   当 `AWS DeepRacer` 车辆接近一个转弯时，它可以选择加速或减速，并向左转、向右转或直行。

#### 奖励

*   代理在给定状态下执行每个动作时会收到反馈。
*   这种反馈是一个数值奖励。
*   奖励函数是一种激励计划，为赛道上的不同区域分配奖励分数。

#### 集 episode

*   集 episode 代表一个试错的时期，当代理做出决策并从其环境中获得反馈时。
*   对于 `AWS DeepRacer`，集 episode 从初始状态开始，当车辆离开起始位置时开始，并在车辆完成一圈、撞击障碍物或驶离赛道时结束。

在强化学习模型中，代理通过试错在交互式实时环境中学习，利用自身行为的反馈。反馈以奖励的形式给出。

![Image](img/image42.png)

在强化学习模型中，代理通过试错在交互式实时环境中学习，利用自身行为的反馈。反馈以奖励的形式给出。

## 在 AWS DeepRacer 上加入自己的特色：

### 强化学习实践者的角色

`AWS DeepRacer` 可能是自主的，但你在模型成功中仍扮演着重要角色。本节介绍训练算法、动作空间、超参数和奖励函数，并讨论你的想法如何产生影响。

*   算法是一组指令，告诉计算机做什么。机器学习的特殊之处在于它使计算机无需被明确编程即可学习。
*   训练算法定义了你的模型的学习目标，即最大化总累计奖励。不同的算法有不同的策略来实现这一点。
*   `软 actor critic (SAC)` 拥抱探索并且数据高效，但可能缺乏稳定性。
*   `接近政策优化 (PPO)` 稳定但数据密集。
*   动作空间是代理在与环境交互时可以选择的所有有效动作或选择的集合。
    *   离散动作空间表示在每个状态中，代理可能的所有动作为有限的转向角度和油门值组合。
    *   连续动作空间允许代理从你为每个状态定义的值范围中选择动作。
*   超参数是控制你的代理在训练期间性能的变量。有多种类别可供尝试。修改值以增加或减少模型不同部分的影响。
    *   例如，`学习率` 是一个超参数，它控制每一步在学习中计数的新经验数量。更高的 `学习率` 会导致训练更快，但可能降低模型的质量。
*   奖励函数的目的是鼓励代理达到其目标。确定如何奖励哪些动作是你最重要的工作之一。

## 将强化学习与 AWS DeepRacer 结合起来

本视频通过将我们所学的概念付诸实践，将奖励函数想象为在 `AWS DeepRacer` 训练环境中映射到赛道上的网格，并将其可视化为图表上的指标。它还介绍了探索与利用之间的权衡，这是这种类型机器学习的一个重要挑战。

![Image](img/image43.png)

每个方块是一个状态。绿色方块是起始位置，即初始状态，而终点线是目标，即终止状态。

## 关于奖励函数的要点回顾：

*   奖励函数为赛道网格上的每个状态分配分数。你通过给予奖励最高的赛道部分来激励支持你的车辆快速完成圈的行为。
*   奖励函数是你编写的实际代码，用于帮助你的代理判断它刚刚执行的动作是好是坏，以及好或坏程度。

![Image](img/image44.png)
