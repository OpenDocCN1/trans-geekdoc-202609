## 1.9 章节大纲
## 模块 I：过程与规划算法
## 模块 II：金融应用建模
## 1.9.3 Module III: Reinforcement Learning Algorithms
## 1.9.4 模块 IV：收尾工作
## 1.9.5 简短附录章节
## 2.3.2 具体分布
## 2.3.3 检查类型
## 2.3.4 类型变量
## 2.3.5 功能
## 2.4 抽象计算
## 2.4.1 第一类函数
## 2.4.2 Iterative Algorithms
## IProcesses and Planning Algorithms
## 马尔可夫过程与马尔可夫性质
## Process 1
## Process 2
## 4.3 形式定义马尔可夫决策过程
## 4.4 POLICY
## 4.5 [MARKOV DECISION PROCESS, POLICY]: = MARKOV REWARD PROCESS
## 如第 3 章所见
## 固定点理论与动态规划简介
## 单调性与常数平移性质
### 2. 常数平移性质
## Policy Iteration 与 Generalized Policy Iteration
## 有限时域马尔可夫决策过程（Finite-Horizon MDP）
## 状态-奖励转移概率函数
## 价值函数与贝尔曼策略方程
## 算法实现
## 控制问题：最优价值函数与最优策略
## ClearancePricingMDP 类说明
## 反向传播方法
# II 建模金融应用
## 定义财富与投资假设
## 连续时间随机过程
## 财富演化与随机控制问题
## 二项期权定价模型
## 最优做市
## 形式化
## MDP 模型
## 实现
## III 强化学习算法
## 分段性与持续性轨迹
## 值函数逼近与损失函数
## 表格式蒙特卡洛预测
## 基于 GPI 思想的 MC 控制
## mdp: `MarkovDecisionProcess[S, A]`
## states: `NTStateDistribution[S]`
## approx\_0: `QValueFunctionApprox[S, A]`
## gamma: `float`
## epsilon\_as\_func\_of\_episodes: `Callable[[int], float]`
## max\_episode\_length: `int`
## Windy Grid MDP 问题规格说明
## MDP 实现与求解算法
## 实验结果
## 收敛性分析
## SARSA 与 Q-Learning 的比较
## 12.6.3 Importance Sampling
## 12.7 DP 和 TD 算法之间的概念关联
## 12.8 RL 算法的收敛性
## Chapter 5: 动态规划基础
## Chapter 6: 函数近似与近似动态规划
## Module II: 将金融应用建模为 MDP
## Chapter 8: 动态资产配置与消费
## Chapter 9: 衍生证券定价与对冲
## Chapter 10: 订单簿上的最优交易
## Module III：强化学习算法
## Chapter 11：RL 预测算法
## Chapter 12：RL 控制算法
## Chapter 13：高级 RL 算法
## Chapter 14：策略梯度算法
## Module IV：探索、利用以及学习与规划的融合
## 17.2 现实世界中的强化学习
## A.4 MINIMIZING THE MGF
## E. 附录
## 索引条目
## state transition probability function
## state-reward transition probability function
## terminal states
## time-homogeneous
## transition probabilities
## variants and extensions of MDPs
## Markov process
### continuing
### episodic
### finite
### Markov property
### non-terminal states
### representations
### start states
## state
#### destination
#### source
### state space
### stationary distribution
### terminal states
### time-homogeneous
### transition probabilities
### transition probability function
## Markov reward process
### continuing
### episodic
### finite
### Markov property
### non-terminal states
### return
### reward
### reward function
### reward transition function
### start states
### state
### state space
### terminal states
### time-homogeneous
### transition probabilities
### transition probability function
## model
### probabilities model
### sampling model
## moment generating function
### for normal distribution
## multi-armed bandits
### action value
### bayes-adaptive MDP
### bayesian ucb
### decaying *ϵ*[*t*]-greedy
### *ϵ*-greedy
### Gittins index
### gradient bandits
### greedy
### information state space MDP
### Lai-Robbins lower bound
### linear total regret
### logarithmic total regret
### optimism in the face of uncertainty
### optimistic initialization
### probability matching
### regret
### slot machines
### sublinear total regret
### Thompson sampling
### ucb1
### upper confidence bound
## planning
### background planning
### decision-time planning
### heuristic search
## planning versus learning
## policy
### behavior policy
### deterministic policy
### *ϵ*-greedy policy
### existence of optimal policy
### greedy policy
### Markovian policy
### optimal policy
## policy\_iteration
## POMDP
## portfolio theory
## principle of optimality
## probability
## process
## projected Bellman error
## projection operator
## Q
## Q^(\*)
## q\_learning
## q\_learning\_experience\_replay
## RandomWalkMRP
## reinforce\_gaussian
## reinforcement learning
## sequential uncertainty
## UniformPolicy
## utility theory
## V
## V^(\*)
## V^(*π*)
## value function
## value_iteration
## VampireMDP
## variance reduction
## vector space
## windy grid
## WindyGrid
## yield