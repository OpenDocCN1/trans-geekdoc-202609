

## ALPHAGO ZERO

AlphaGo Zero 可理解为遵循广义策略迭代方案，在训练循环中融入 MCTS 以同时执行策略改进和策略评估。MCTS 可视为策略改进算子。它输出的落子概率强于神经网络的原始概率。带搜索的自博弈可视为策略评估算子。它使用 MCTS 选择落子，并以获胜者作为价值函数的样本。随后，策略迭代过程更新神经网络权重，使移动概率和价值更贴近改进后的搜索概率和自博弈获胜者，并在下一次迭代中使用更新后的神经网络权重进行自博弈，以使搜索更强。

与 AlphaGo (Silver et al., 2016a) 相比，AlphaGo Zero (Silver et al., 2017) 的特点为：1) 通过自博弈强化学习从随机对弈中学习，无需人类数据或监督；2) 以棋盘上的黑白棋子作为输入，无需任何人工特征工程；3) 使用单一神经网络同时表示策略和价值，而非分离的策略网络和价值网络；4) 利用神经网络进行局面评估和 MCTS 的落子采样，且不执行 Monte Carlo 模拟。AlphaGo Zero 部署了神经网络的若干近期成果：残差卷积神经网络 (ResNets)、批量归一化和整流线性单元。

AlphaGo Zero 的自博弈训练流水线包含三个主要组件，并异步并行执行：1) 从近期自博弈数据中持续优化神经网络权重；2) 持续评估选手；3) 使用最强选手生成新的自博弈数据。

当 AlphaGo Zero 与对手对弈时，MCTS 从当前状态开始，使用训练好的神经网络权重进行搜索，生成落子概率，然后选择一个落子。

我们在算法 12 中为 AlphaGo Zero 的训练提供了简洁的概念性伪代码，有助于更易理解。

## ALPHA ZERO

Alpha Zero (Silver et al., 2017) 将 AlphaGo Zero 的学习框架推广到更多领域，特别是完美信息两人零和博弈，使用通用强化学习算法，除游戏规则外无需人类知识即可学习，并在国际象棋、将棋和围棋游戏中达到超人水平。

## DISCUSSIONS

AlphaGo Zero 是一种强化学习算法。它既不是监督学习也不是无监督学习。游戏得分是奖励信号，而非监督标签。优化损失函数 l 是监督学习。然而，它在广义策略迭代的一轮中执行策略评估和策略改进。

AlphaGo Zero 不仅仅是一种启发式搜索算法。AlphaGo Zero 遵循广义策略迭代流程，其中，启发式搜索（特别是 MCTS）起关键作用，但属于强化学习广义策略迭代方案的一部分，如算法 12 的伪代码所示。MCTS 可视为策略改进算子。

AlphaGo Zero 已达到超人水平的表现。这可能证实人类职业选手已发展出有效策略。然而，它无需模仿人类职业对弈。因此，它无需正确预测对方的落子。

AlphaGo Zero 的输入包括局面的原始棋盘表示、其历史以及以 19 × 19 图像形式表示的执棋颜色；游戏规则；游戏得分函数；游戏规则在旋转和反射下的不变性；以及除了贴目外颜色转置的不变性。

AlphaGo Zero 使用 64 个 GPU 工作者和 19 个 CPU 参数服务器进行训练，约 2000 个 TPU 用于数据生成，4 个 TPU 用于对弈。计算成本可能对于平均计算资源的研究人员来说过于高昂，难以复现 AlphaGo Zero。ELF OpenGo 是使用 ELF (Tian et al., 2017) 重新实现的 AlphaGo Zero/AlphaZero，网址为 https://facebook.ai/developers/tools/elf。

```
Input: the raw board representation of the position, its history, and the colour to play as 19 × 19
images; game rules; a game scoring function; invariance of game rules under rotation and
reflection, and invariance to colour transposition except for komi
Output: policy (move probabilities) p, value v
initialize Neural network weights θ0 randomly
//AlphaGo Zero follows a generalized policy iteration procedure
for each iteration i do
    // termination conditions:
    // 1. both players pass
    // 2. the search value drops below a resignation threshold
    // 3. the game exceeds a maximum length
    initialize s0
    for each step t, until termination at step T do
        // MCTS can be viewed as a policy improvement operator
        // search algorithm: asynchronous policy and value MCTS algorithm (APV-MCTS)
        // execute an MCTS search πt = αθt-1(st) with previous neural network fθt-1
        // each edge (s, a) in the search tree stores a prior probability P(s, a), a visit count N(s, a),
        // and an action value Q(s, a)
        while computational resource remains do
            select: each simulation traverses the tree by selecting the edge with maximum upper
            confidence bound Q(s, a) + U(s, a), where U(s, a) ∝ P(s, a)/(1 + N(s, a))
            expand and evaluate: the leaf node is expanded and the associated position s is
            evaluated by the neural network, (P(s, ·), V(s)) = fθi(s); the vector of P values are
            stored in the outgoing edges from s
            backup: each edge (s, a) traversed in the simulation is updated to increment its visit
            count N(s, a), and to update its action value to the mean evaluation over these
            simulations, Q(s, a) = 1/N(s, a) ∑s'|s,a→s' V(s'), where s'|s, a → s' indicates that
            a simulation eventually reached s' after taking move a from position s
        end
        // self-play with search can be viewed as a policy evaluation operator: select each move
        // with the improved MCTS-based policy, use the game winner as a sample of the value
        play: once the search is complete, search probabilities π ∝ N1/τ are returned, where N is
        the visit count of each move from root and τ is a parameter controlling temperature; play
        a move by sampling the search probabilities πt, transition to next state st+1
    end
    score the game to give a final reward rT ∈ {-1, +1}
    for each step t in the last game do
        zt ← ±rT, the game winner from the perspective of the current player
        store data as (st, πt, zt)
    end
    sample data (s, π, z) uniformly among all time-steps of the last iteration(s) of self-play
    //train neural network weights θi
    //optimizing loss function l performs both policy evaluation, via (z − v)2, and policy
    improvement, via −πT log p, in a single step
    adjust the neural network (p, v) = fθi(s):
    to minimize the error between the predicted value v and the self-play winner z, and
    to maximize similarity of neural network move probabilities p to search probabilities π
    specifically, adjust the parameters θ by gradient descent on a loss function
    (p, v) = fθi(s) and l = (z − v)2 − πT log p + c||θi||2
    l sums over the mean-squared error and cross-entropy losses, respectively
    c is a parameter controlling the level of L2 weight regularization to prevent overfitting
    evaluate the checkpoint every 1000 training steps to decide if replacing the current best player
    (neural network weights) for generating next batch of self-play games
end
```

## Algorithm 12: AlphaGo Zero training pseudo code, based on Silver et al. (2017)

AlphaGo Zero 需要大量数据进行训练，因此仍是大数据问题。然而，数据可以通过自博弈生成，前提是拥有完美模型或精确游戏规则。

由于围棋拥有完美模型或精确游戏规则，AlphaGo 算法存在其局限性。例如，在医疗、机器人和自动驾驶问题中，通常很难收集大量数据，且很难甚至不可能拥有足够接近甚至完美的模型。因此，直接将 AlphaGo Zero 算法应用于此类应用并非易事。

另一方面，AlphaGo 算法，尤其是其底层技术，即深度学习、强化学习、蒙特卡洛树搜索和自博弈，有许多应用。Silver et al. (2016a) 和 Silver et al. (2017) 推荐以下应用：通用游戏对弈（特别是视频游戏）、经典规划、部分可观测规划、调度、约束满足、机器人、工业控制和在线推荐系统。AlphaGo Zero 博客位于 `https://deepmind.com/blog/alphago-zero-learning-scratch/`，提及以下结构化问题：蛋白质折叠、降低能耗以及寻找革命性新材料。7 其中几项，如规划、调度、约束满足，属于约束编程问题 (Rossi et al., 2006)。

AlphaGo 取得了巨大进展，并在 AI 领域树立了里程碑。然而，距离实现通用人工智能 (AGI) 仍遥遥无期。

观察 AlphaGo 中深度神经网络能变得多强，即逼近最优价值函数和策略，以及何时极强的围棋程序可在手机上运行，这很有趣。

## 15.2 纸牌游戏

纸牌游戏的变体，包括德州扑克、麻将、Skat 等，属于不完全信息博弈，作为博弈论问题的一种，具有许多应用，例如安全和医疗决策支持 (Chen and Bowling, 2012)。观察深度强化学习在此类应用中取得更多进展，以及完整版的德州扑克，这很有趣。

头对头限注德州扑克 (Heads-up Limit Hold’em Poker) 基本上已被求解 (Bowling et al., 2015)，使用反事实遗憾最小化 (CFR)，这是一种通过两个遗憾最小化算法之间的重复自博弈来逼近广义形式博弈纳什均衡的迭代方法。

## DEEPSTACK

最近，在头对头无限注德州扑克 (Heads-up No-Limit Hold’em Poker) 方面取得了重大进展 (Moravčík et al., 2017)，DeepStack 计算机程序首次击败了职业扑克玩家。DeepStack 利用 CFR 的递归推理来处理信息不对称，将计算集中在决策时出现的特定情境，并使用自动训练的价值函数，几乎无需领域知识或人类专家对弈，无需抽象化和先前的完整策略离线计算。DeepStack 遵循广义策略迭代。观看 Michael Bowling 的演讲，网址为 `https://vimeo.com/212288252`。

希望看到 DeepStack 扩展到多人设置。目前对扑克的研究仅限于单手牌，而扑克通常有多手牌。因此，有必要进行调查

7 有一篇标题为 "AlphaGo, in context" 的博客，发布于 2017 年 5 月，作者 Andrej Karpathy，在 AlphaGo 击败柯洁之后，网址为 `https://medium.com/@karpathy/alphago-in-context-c47718cb95a5`。作者将计算机围棋的特性描述为：完全确定性、完全可观测、离散动作空间、可访问的完美模拟器、相对较短的回合：对局、清晰快速的评估有利于大量试错，以及大量的人类对弈数据集，以说明 AlphaGo 的局限性。（AlphaGo Zero 使最后一条属性“庞大人类对弈数据集”失效。）诚然，计算机围棋在问题设置上存在局限性，因此在潜在应用方面也有局限，且距离通用人工智能还很远。然而，我们将 AlphaGo 的成功，特别是 AlphaGo Zero 的成功，视为 AI 的胜利，特别是其底层技术，即深度学习、强化学习、蒙特卡洛树搜索和自博弈；这些技术出现在 AI 许多近期成就中。AlphaGo 技术将为经典 AI 领域（如规划、调度和约束满足 (Silver et al., 2016a)）以及 AI 新领域（如逆合成 (Segler et al., 2018)）提供启发。据报道，AlphaGo 征服浩瀚搜索空间的成功启发了量子物理学家求解量子多体问题 (Carleo and Troyer, 2017)。

