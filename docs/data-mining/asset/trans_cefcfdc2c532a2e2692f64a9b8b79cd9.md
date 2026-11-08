
为了执行知识蒸馏，我们将原始的复杂模型解释为“教师模型”，并用它来训练一个更小、更简单的“学生模型”。这样做的关键洞见在于，教师模型通过为训练集中的硬分配类别标签生成类别概率，从而改进了这些标签，从而区分哪些实例是某个特定类别的明确成员，哪些则是较为模糊的边界案例。不是直接在训练数据上训练学生模型，我们在训练数据上训练它，但使用教师模型的类别概率，即“`soft targets`”，代替类别标签。学生模型因此可以访问教师模型关于实例可能类别标签的“知识”。我们可以通过最小化基于教师模型类别概率的交叉熵损失来实现这一点。然而，如果教师的类别概率都接近于零或接近于一，那么使用教师的预测而不是原始标签就不会获得太多收益。为了解决这个问题，我们可以通过改变分布的“温度” `T`![方程](images/F000121si166.png) 来展平类别分布，从而获取更细致的相对类别概率信息。假设最后一层具有 `softmax` 激活函数，我们将类别概率写为：

$p\\left( {y\_{i}\\text{|}x\_{i}} \\right) = \\frac{\\exp\\left( \\frac{z\_{c}}{T} \\right)}{\\sum\_{c\\prime}{\\exp\\left( \\frac{z\_{c}^{\\prime}}{T} \\right)}}.$<mml:math><mml:mstyle displaystyle="true"><mml:mi>p</mml:mi><mml:mrow><mml:mfenced open="(" close=")"><mml:mrow><mml:msub><mml:mrow><mml:mi>y</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mtext>|</mml:mtext><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub></mml:mrow></mml:mfenced></mml:mrow><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mi>exp</mml:mi><mml:mrow><mml:mfenced open="(" close=")"><mml:mrow><mml:mfrac><mml:mrow><mml:msub><mml:mrow><mml:mi>z</mml:mi></mml:mrow><mml:mrow><mml:mi>c</mml:mi></mml:mrow></mml:msub></mml:mrow><mml:mrow><mml:mi>T</mml:mi></mml:mrow></mml:mfrac></mml:mrow></mml:mfenced></mml:mrow></mml:mrow><mml:mrow><mml:msub><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mrow><mml:mi>c</mml:mi></mml:mrow><mml:mrow><mml:mo accent="false">&#8242;</mml:mo></mml:mrow></mml:mrow></mml:msub><mml:mrow><mml:mi>exp</mml:mi><mml:mrow><mml:mfenced open="(" close=")"><mml:mrow><mml:mfrac><mml:mrow><mml:msubsup><mml:mrow><mml:mi>z</mml:mi></mml:mrow><mml:mrow><mml:mi>c</mml:mi></mml:mrow><mml:mrow><mml:mo accent="true">&#8242;</mml:mo></mml:mrow></mml:msubsup></mml:mrow><mml:mrow><mml:mi>T</mml:mi></mml:mrow></mml:mfrac></mml:mrow></mml:mfenced></mml:mrow></mml:mrow></mml:mrow></mml:mfrac><mml:mo>.</mml:mo></mml:mstyle></mml:math>

![方程](images/F000121si167.png)

这里 `z`[`c`] <mml:math><mml:msub><mml:mrow><mml:mi>z</mml:mi></mml:mrow><mml:mrow><mml:mi>c</mml:mi></mml:mrow></mml:msub></mml:math>![方程](images/F000121si168.png) 是模型下类别 `c` <mml:math><mml:mi>c</mml:mi></mml:math>![方程](images/F000121si169.png) 概率的对数几率。当温度 `T` = 1 <mml:math><mml:mi>T</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:math>![方程](images/F000121si170.png) 时，这是一个常规的 softmax 单元，而较大的 `T` <mml:math><mml:mi>T</mml:mi></mml:math>![方程](images/F000121si171.png) 值会使概率不那么极端。我们使用较高的 `T` <mml:math><mml:mi>T</mml:mi></mml:math>![方程](images/F000121si172.png) 值训练模型，但在进行最终预测时将其转换回 `T` = 1 <mml:math><mml:mi>T</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:math>![方程](images/F000121si173.png)。请参阅 [图 11.14](#Ch012_433-471_B9780443158889000121.xhtml#f0075) 以了解说明。

![图 11.14 知识蒸馏。署名：James Foulds](images/F000121f11-14-9780443158889.jpg)

[图 11.14](#Ch012_433-471_B9780443158889000121.xhtml#Bf0075) 知识蒸馏。署名：James Foulds

## 11.7 深度强化学习

本章我们主要关注监督学习，其中“教师”对用于训练模型的实例进行了标注。如果没有“教师”持续为系统提供信息，学习就会变得更加困难。例如，考虑通用人工智能问题，它通常以 `intelligent agent`（例如机器人吸尘器）的形式来表述。智能体处于一个环境中，它使用传感器感知环境，做出决策，并通过其执行器（例如轮子）在世界中行动。智能体有一个任务要执行（例如清洁房间），并且必须对环境及其行动的结果做出反应以实现该任务。在 `reinforcement learning` 中，我们假设智能体接收到一种相当有限的反馈信号，即奖励和惩罚，让它知道任务完成得好坏。这个 `reward signal` 可能在智能体采取每一次行动后给出，也可能只在场景结束时给出。智能体旨在行动以获得尽可能高的累计奖励和尽可能少的惩罚（可视为负奖励）。

虽然使用深度学习只是强化学习的一种可能方法，但这两个领域交叉的“`deep reinforcement learning`”领域已被证明是成功的，并且由于以下几个原因仍具有前景。`DNNs` 可以处理复杂的数据，例如来自传感器（例如摄像头或雷达）的输入。更重要的是，`DNNs` 需要大量数据，而模拟的强化学习环境可以提供源源不断的此类数据，从而促进强大而准确模型的训练。尽管在 2010 年代崭露头角，神经网络方法在强化学习中的应用早在 1995 年就已取得成功，当时 TD-Gammon 系统能够在 backgammon 游戏中表现出色。更近期的，深度学习的兴起带动了所有领域，包括强化学习，这与许多相同的原因有关，包括计算能力的提升和深度学习架构的改进。

深度强化学习的一些重要成功案例来自 DeepMind，现在称为 Google DeepMind，这是一家专注于该技术的英国科技初创公司。DeepMind 研究人员开发了一种名为“`deep Q-learning`”的方法，该方法将深度学习集成到 `Q-learning` 算法中，这是一种“`model-free`”强化学习算法，避免学习环境的“`transition model`”。他们成功开发了 `deep Q-learning networks`（`DQNs`），这些网络仅以原始像素值作为输入，就能从零开始学习玩许多 Atari 游戏。他们的系统使用了 `CNNs`，并通过玩游戏进行训练。在许多游戏中，他们的系统能够超越专家人类玩家和专用 ML 系统。
