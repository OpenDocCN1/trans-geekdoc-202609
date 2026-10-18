

[Figure 16.1](#chapter16.xhtml#fig16_1) 描述了上述 *Planning* 预测/控制解决方案的方法。我们从一个任意的 Policy 开始，该 Policy 用于与 Environment *E* 进行交互（图中向上指向的箭头）。这些交互生成 Experiences，用于执行 Supervised Learning（图中向右指向的箭头）以学习模型 *M*。该模型 *M* 用于规划所需的 Value Function/Policy（图中向左指向的箭头）。通过此 Planning 过程产生的 Policy 然后用于进一步与 Environment *E* 交互，进而生成一组新的 Experiences，进而用于更新模型 *M*（增量式 Supervised Learning），进而用于规划更新后的 Value Function/Policy，循环往复。

![Figure 16.1 Planning with a Supervised-Learnt Model](images/fig16_1.jpg)

[Figure 16.1](#chapter16.xhtml#b16fig16_1) Planning with a Supervised-Learnt Model

### 16.1.2 Learning the Solution of Prediction/Control

在第二种方法（*Learning* 预测/控制的解决方案）中，我们不费心构建模型。相反，AI Agent 直接从与真实 MDP Environment *E* 交互获得的经验数据中估计所需的 Value Function/Policy。AI Agent 通过使用本书 Module III 中涵盖的任何 RL 算法来实现这一点。由于这种方法是“无模型”的，我们将此方法称为 *Model-Free RL*。

### 16.1.3 Advantages and Disadvantages of Planning versus Learning

在前两个小节中，我们介绍了两种不同的解决预测/控制的方法，即通过 *Planning* ([subsection 16.1.1](#chapter16.xhtml#sec16_1_1)) 或通过 *Learning* ([subsection 16.1.2](#chapter16.xhtml#sec16_1_2))。现在让我们谈谈它们的优缺点。

*Planning* 涉及构建模型，因此其自然优势在于能够使用高效且鲁棒的 Supervised Learning 方法从经验数据中构建模型。*Planning* 的另一个关键优势是我们可以对模型不确定性进行推理。具体来说，当我们使用 Supervised Learning 学习模型 *M* 时，我们通常会获得模型参数估计的标准误差，然后可以使用这些误差为使用模型规划的 Value Function 和 Policy 创建置信区间。此外，由于对现实世界问题进行建模往往相当困难，因此创建一系列具有不同假设、不同函数形式、不同参数化等的模型，并推理 Value Function/Policy 将如何作为这一模型范围的函数而分散，是有价值的。这在典型的现实世界问题中非常有益，因为它使我们能够以 *robust* 的方式进行预测/控制。

*Planning* 的缺点是我们有两个近似误差来源——第一个来自使用 Supervised Learning 估计模型 *M*，第二个来自构建 Value Function/Policy（给定模型）。因此，*Learning* 方法（不诉诸模型，即 Model-Free RL）的优势在于没有第一个近似误差来源（即模型误差）。

### 16.1.4 Blending Planning and Learning

在本小节中，我们展示了一种相当创造性且在实践中强大的方法，用于解决现实世界的预测和控制问题。我们基本上将 [Figure 16.1](#chapter16.xhtml#fig16_1) 扩展到 [Figure 16.2](#chapter16.xhtml#fig16_2)。如您在 [Figure 16.2](#chapter16.xhtml#fig16_2) 中所见，变化在于 *Experiences* 节点到 *Policy* 节点有一个向下指向的箭头。这个向下指向的箭头指的是 *Model-Free Reinforcement Learning*，即直接从与 Environment *E* 交互获得的经验中学习 Value Function/Policy，即 Model-Free RL。这意味着我们通过 *Planning*（使用模型 *M*）和 *Learning*（使用 Model-Free RL）的协作方法获得所需的 Value Function/Policy。

![Figure 16.2 Blending Planning and Learning](images/fig16_2.jpg)

[Figure 16.2](#chapter16.xhtml#b16fig16_2) Blending Planning and Learning

请注意，当 Planning 基于使用与模拟 Environment *S*（基于模型 *M*）交互获得的经验进行 RL 时，我们从两个来源的经验（来自 *E* 和 *S*）中获得所需的 Value Function/Policy，这些经验被合并并提供给 RL 算法。这意味着我们同时进行 Model-Based RL 和 Model-Free RL。这很有创意且强大，因为它融合了两全其美的优点——Planning（使用 Model-Based RL）和 Learning（使用 Model-Free RL）。除了 Model-Free RL 和 Model-Based RL 在这里融合以获得更准确的 Value Function/Policy 之外，模型也在同时通过增量式 Supervised Learning 进行更新（[Figure 16.2](#chapter16.xhtml#fig16_2) 中的向右指向的箭头），因为作为 Policy 与 Environment *E* 交互的结果生成了新的经验（[Figure 16.2](#chapter16.xhtml#fig16_2) 中的向上指向的箭头）。

这种融合 Planning 和 Learning 的框架是由 Richard Sutton 创建的，他将其命名为 Dyna ([Richard S. Sutton 1991](#bib01.xhtml#refbib_61))。

## 16.2 DECISION-TIME PLANNING

在本章的接下来两个部分中，我们介绍了几种基于采样的 Planning 方法（通过与采样模型交互获得的经验），并使用 RL 技术从模型采样的经验中求解所需的 Value Function/Policy。我们介绍了著名的 Monte-Carlo Tree-Search (MCTS) 算法，随后介绍了一种 MCTS 的精神起源算法——Adaptive Multi-Stage Sampling (AMS) 算法。

这两种算法都是 *Decision-Time Planning* 的示例。*Decision-Time Planning* 这个术语需要一些解释。在 Planning（带模型）方面，有两种可能性：

*   Background Planning: 这指的是一种 Planning 方法，其中 AI Agent 预先计算 *所有状态* 所需的 Value Function/Policy，当 AI Agent 需要为给定状态执行所需动作时，它只需参考预先计算的 Policy 并将该 Policy 应用于给定状态。基本上，在 *后台*，AI Agent 正在不断改进所需的 Value Function/Policy，无论 AI Agent 当前需要对哪个状态采取行动。因此，术语 *Background Planning*。

*   Decision-Time Planning: 这种方法与 Background Planning 形成对比。在这种方法中，当 AI Agent 需要识别当前遇到的特定状态的最佳动作时，该最佳动作识别的计算仅在 AI Agent *到达该状态时* 进行。这在状态空间中有大量状态导致 Background Planning 不可行的情况下是合适的。但是，为了使 Decision-Time Planning 有效，AI Agent 需要有足够的时间来执行计算以识别 *在到达给定状态时* 要采取的动作。这在国际象棋等游戏中是可行的，因为 AI Agent 在遇到棋盘的特定状态时确实有时间走棋（移动响应不需要立即）。但是，对于自动驾驶汽车来说，这不可行，因为加速/刹车或转向的决定必须是立即的（这需要 *Background Planning*）。

