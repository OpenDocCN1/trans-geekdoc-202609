

## 9.8.3.4 6G 集成 DRL 调度的优势：

- **近乎瞬时的任务执行**：为关键应用提供实时 AI 处理。
- **提高网络适应性**：DRL 智能体能够根据网络拥塞和可用性动态调整调度策略。
- **无缝云边协作**：实现边缘节点与远程云服务器之间平滑的任务任务迁移。

## 9.8.3.5 核心总结与未来展望

| 未来技术 | 对基于 DRL 调度的关键影响 | 示例用例 |
| --- | --- | --- |
| 联邦学习 | 增强隐私性和可扩展性 | 在不暴露患者记录的情况下进行安全的医疗健康数据处理。 |
| 多智能体强化学习 | 实现多个边缘节点之间的协作调度 | 自动驾驶车辆车队优化实时导航。 |
| 6G 网络 | 提供超低延迟和 AI 原生网络 | 具有实时 AI 驱动决策能力的智能城市基础设施。 |

通过集成联邦学习、多智能体强化学习和 6G 网络，基于 DRL 的调度将开启边缘计算环境中效率、可扩展性和智能的新水平！

## 9.9 结论

DRL 已成为边缘计算中任务调度的一种 transformational 解决方案，解决了资源受限、动态工作负载、延迟敏感性和基础设施异构性等固有挑战。传统的调度方法（如基于启发式和静态规则的方法）往往无法适应快速变化的环境，导致资源利用率低下和延迟增加。如表 9.7 所示，DRL 通过利用持续学习和自适应决策，为优化资源分配、减少计算开销和提高边缘系统的整体效率提供了一个稳健的框架。

基于 DRL 调度的最显著的优势之一是它能够从实时系统状态中动态学习，并在无需预定义规则的情况下做出智能调度决策。通过将 `DNN`（深度神经网络）与强化学习过程集成，DRL 能够高效地处理高维系统参数（如 CPU 利用率、网络带宽和能耗），以确定最有效的调度动作。与需要大量标记数据和静态训练的传统机器学习不同，DRL 通过与环境的交互不断改进其调度策略，确保其在不断变化的情况下保持有效。

DRL 在边缘任务调度中的实现遵循结构化框架，涉及数据收集、模型训练和实时部署。边缘节点持续收集关键系统信息（包括资源可用性和任务到达），这些信息用于训练分布式 DRL 模型。训练后的模型随后被部署到边缘设备上，由其自主管理调度决策以优化工作负载分布、最小化延迟并提高能效。通过这种方法，DRL 实现了低延迟任务执行，确保具有严格限制的应用（如自动驾驶汽车、增强现实和医疗监控）在现实场景中无缝运行。

边缘计算已探索了多种基于强化学习的算法，它们提供了独特的优势。`DQN` 有效地处理离散调度动作，使其非常适合 IoT 环境下的任务卸载。策略梯度方法（`PPO` 和 `TRPO`）通过直接最大化奖励来优化调度策略，使其对波动的工作负载具有更好的适应性。Actor-critic 算法（`A3C` 和 `Soft Actor-Critic (SAC)`）在基于价值的学习和基于策略的学习之间取得了平衡，改进了调度决策中的探索与利用。这些先进技术使得 DRL 在吞吐量、响应时间和功率效率方面优于传统的调度方法。

基于 DRL 调度的现实影响 [11] 在多个领域都是显而易见的。在智能医疗领域，DRL 优先考虑紧急监控任务，缩短了响应时间并改进了能量处理。在自动驾驶领域，实时调度确保了快速决策，增强了车辆导航和安全性。在 IoT 中，DRL 的预测性维护减少了停机时间。展望未来，联邦学习、多智能体强化学习和 6G 网络集成将为 DRL 在边缘计算中的应用提供隐私保护、协作、超低延迟和 AI 原生架构。

总结来说，联邦学习将增强 DRL 在边缘计算中的应用，至关重要。

## 基于深度强化学习的任务调度 ■ 205

## 参考文献

- 1. Lin, K., Li, Y., Zhang, Q., & Fortino, G. (2021). Deep learning task scheduling for 6G-enabled mobile. Internet of Things, 8(7), 5264–5273.
- 2. Mustafa, S. & Gupta, P. (2024). Neural network inspired task scheduling for cloud infrastructure. Internet of Things and Cyber-Physical, 4.
- 3. Gupta, P., Saini, D., & Vidyarthi, A. (2023). Dynamic virtual machine allocation in cloud computing using elephant herd optimization. Internet of Circuits, Systems and Computers, 32,235018.
- 4. Rawat, P., Gaur, S., Barthwal, V., Gupta, P., Ghosh, D., Gupta, D., & Rodrigues, J. (2025). Federated learning inspired Antlion in cloud computing using BSO-ANN hybrid technique. Alexandria Engineering Journal, 110–152.
- 5. Rawat, P., Saini, D. (2023). Neural network differential evolution. Alexandria Engineering Journal, 73.
- 6. HS, M. & Gupta, P. (2024). Federated learning inspired Antlion orchestra for Edge computing. PLoS One, 19(6), e03467.
- 7. Gupta, P., Anand, A., Agarwal, P., & McArdle, G. (2024). Neural network inspired scalable task scheduling for cloud infrastructure. Internet of Things and Cyber-Physical, 4, 268–279.
- 8. Li, Y., et al. (2020). Reinforcement learning for resource management in edge computing. IEEE Transactions on Mobile Computing, 1–22.
- 9. Sutton, R. S., & Barto, A. G. (2018). Reinforcement Learning: An Introduction, The MIT Press, Cambridge, Massachusetts, 322 pp, ISBN 0-262-19398-1.
- 10. Mnih, V., et al. (2015). Human-level control through deep reinforcement learning. Nature, 518(7540), 529–533.
- 11. Silver, D., et al. (2016). Mastering the game of Go with deep neural networks and search. Nature, 529(7587), 484–489.

