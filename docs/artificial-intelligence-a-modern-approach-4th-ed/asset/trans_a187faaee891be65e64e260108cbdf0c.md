
# 强化学习背景

## 逆强化学习
逆强化学习 (`IRL`) 由 Russell (1998) 提出，首批算法由 Ng 和 Russell (2000) 开发。 （在经济学中，类似的问题早已被研究，标题为 `MDPs` 的结构估计 (Sargent, 1978)。）本章给出的算法由 Abbeel 和 Ng (2004) 提出。 Baker 等 (2009) 描述了如何将对另一智能体行为的理解视为逆向规划。 Ho 等 (2017) 表明，智能体可以从具有启发性而非最优的行为中更好地学习。 Hadfield-Menell 等 (2017a) 将 `IRL` 扩展为包含观察者和演示者的博弈论形式化，展示了教学和学习行为如何作为博弈的解出现。

## 安全强化学习
García 和 Fernández (2015) 对安全强化学习进行了全面综述。 Munos 等 (2017) 描述了一种用于安全离策略（例如 `Q-learning`）探索的算法。 Hans 等 (2008) 将安全探索问题分为两部分：定义一个安全函数以指示应避免的状态，以及定义一个备份策略以在智能体可能进入不安全状态时将其带回安全状态。 You 等 (2017) 展示了如何训练深度强化学习模型在仿真中驾驶汽车，然后使用迁移学习在现实世界中安全驾驶。

Thomas 等 (2017) 提出了一种学习方法，该方法以高概率保证不会比当前策略更差。 Akametalu 等 (2014) 描述了一种基于可达性的方法，其中学习过程在控制策略的指导下进行，该策略确保智能体永远不会到达不安全状态。 Saunders 等 (2018) 证明系统可以使用人工干预阻止其游离出安全区域，并随着时间的推移学会减少干预需求。

## 策略搜索方法
策略搜索方法由 Williams (1992) 提出，他开发了 `REINFORCE` 系列算法，其名称代表“REward Increment = Nonnegative Factor × Offset Reinforcement × Characteristic Eligibility”。 Marbach 和 Tsitsiklis (1998)、Sutton 等 (2000) 以及 Baxter 和 Bartlett (2000) 的后续工作加强并推广了策略搜索的收敛结果。 Schulman 等 (2015b) 描述了信任域策略优化，这是一种理论基础扎实且实用的策略搜索算法，已衍生出许多变体。 用于降低蒙特卡洛比较中方差的相关采样方法由 Kahn 和 Marshall (1953) 提出；它也是 Hammersley 和 Handscomb (1964) 探索的多种方差缩减方法之一。

## 分层强化学习
早期的分层强化学习 (`HRL`) 方法尝试使用状态抽象构建层次结构——即把状态分组为抽象状态，然后在抽象状态空间中进行强化学习 (Dayan and Hinton, 1993)。 不幸的是，抽象状态的转移模型通常是非马尔可夫的，导致标准强化学习算法出现发散行为。 本章中的时间抽象方法在 1990 年代末发展起来 (Parr and Russell, 1998; Andre and Russell, 2002; Sutton et al., 2000)，并由 Marthi 等 (2005) 扩展以处理并发行为。 Dietterich (2000) 提出了由子程序层次结构诱导的 Q 函数加性分解的概念。 时间抽象基于 Forestier 和 Varaiya (1978) 的更早结果，他们表明大型 `MDP` 可以分解为双层系统，其中监督层在低级控制器中进行选择，每个控制器在完成时将控制权交还给监督者。 抽象层次本身的学习问题至少自 Peter Andreae (1985) 的工作以来就已被研究；关于学习机器人运动原型的最新探索，参见 Frans 等 (2018)。 Keepaway 游戏由 Stone 等 (2005) 提出；本文给出的 `HRL` 解法由 Bai 和 Russell (2017) 提出。

## 神经科学启发
神经科学经常启发强化学习并证实了该方法的价值。 使用单细胞记录的研究表明灵长类大脑中的多巴胺系统实现了类似于价值函数学习的功能 (Schultz et al., 1997)。 Dayan 和 Abbott (2001) 的神经科学著作描述了时间差分学习的可能神经实现；相关研究描述了其他神经科学和行为学实验 (Dayan and Niv, 2008; Niv, 2009; Lee et al., 2012)。

## 仿真环境
强化学习工作的推进得益于用于开发和测试学习智能体的开源仿真环境的可用性。 阿尔伯塔大学的街机学习环境 (`ALE`) (Bellemare et al., 2013) 为 55 款经典 Atari 电子游戏提供了这样的框架。 屏幕上的像素作为感知提供给智能体，同时还提供游戏迄今为止的硬连线分数。 `ALE` 被 DeepMind 团队用于实现 `DQN` 学习并在多种游戏中验证其系统的通用性 (Mnih et al., 2015)。

DeepMind 反过来开源了多个智能体平台，包括 DeepMind Lab (Beattie et al., 2016)、AI Safety Gridworlds (Leike et al., 2017)、Unity 游戏平台 (Juliani et al., 2018) 和 DM Control Suite (Tassa et al., 2018)。 暴雪发布了星际争霸 II 学习环境 (`SC2LE`)，DeepMind 为其添加了用于 Python 机器学习的 `PySC2` 组件 (Vinyals et al., 2017a)。

Facebook 的 AI Habitat 仿真 (Savva et al., 2019) 为室内机器人任务提供照片级逼真的虚拟环境，其 `HORIZON` 平台 (Gauci et al., 2018) 使大规模生产系统中的强化学习成为可能。 `SYNTHIA` 系统 (Ros et al., 2016) 是一个专为提升自动驾驶汽车计算机视觉能力而设计的仿真环境。 `OpenAI Gym` (Brockman et al., 2016) 为强化学习智能体提供多个环境，并与 Google Football 模拟器等其他仿真兼容。

## 综述和参考文献
Littman (2015) 为普通科学受众综述了强化学习。 由该领域两位先驱 Sutton 和 Barto (2018) 所著的经典著作展示了强化学习如何将学习、规划和行动的思想融合在一起。 Kochenderfer (2015) 采用了略少数学化的方法，并提供了大量现实世界示例。 Szepesvari (2010) 的短书概述了强化学习算法。 Bertsekas 和 Tsitsiklis (1996) 提供了动态规划和随机收敛理论的严格基础。 强化学习论文经常发表在《Machine Learning》和《Journal of Machine Learning Research》期刊上，以及国际机器学习会议 (`ICML`) 和神经信息处理系统 (`NeurIPS`) 会议的论文集上。

## 脚注
[1](#Chapter23-01.xhtml#sup23_1)正如 Yann LeCun 和 Alyosha Efros 所指出的，“人工智能革命将不会是监督式的。”

[2](#Chapter23-01.xhtml#sup23_2)在更依赖运筹学而非经济学的强化学习文献中，效用函数通常被称为价值函数并记为 `V(s)`。

[3](#Chapter23-02.xhtml#sup23_3)技术条件在 [第702页](#Chapter19-06.xhtml#page_702) 给出。在 [图23.5](#Chapter23-02.xhtml#fig23-5) 中我们使用了 `α(n) = 60/(59 + n)`，它满足条件。

[4](#Chapter23-04.xhtml#sup23_4)效用函数之间距离的定义相当技术性；参见 Tsitsiklis 和 Van Roy (1997)。

[5](#Chapter23-04.xhtml#sup23_5)关于 keepaway 受巴塞罗那足球俱乐部现实战术启发的传闻可能毫无根据。
