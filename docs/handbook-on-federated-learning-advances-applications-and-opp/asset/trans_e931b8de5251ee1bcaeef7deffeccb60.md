

## 图 1：联邦学习的多级基础设施

在[图 1](#ch8.xhtml#fig8_1)中，展示了两层联邦架构工作流的实际运行情况。架构分为上下两层：下层托管车辆节点，上层由雾服务器联邦支撑。随着下层车辆的 Actor 和 Critic 网络学习策略和价值，它们接管控制权。上层雾服务器收集范围内车辆的数据，并聚合 Actor 和 Critic 的更新。卸载决策模型受益于两层间交换的最新信息。

![Figure 1. A multi-level infrastructure for federated learning. There is two-way communication between the lower-tier cars and the associated fog node below.](images/fig8_1_B.jpg)

[Figure 1. A multi-level infrastructure for federated learning. There is two-way communication between the lower-tier cars and the associated fog node below.](#ch8.xhtml#R_fig8_1)

## 分布式多层学习系统

在分布式多层学习系统中，`N` 个移动智能体竞争有限的计算资源。每个车辆在其自身的完整车辆环境 `A3C` 实例中探索状态空间，因为我们有许多 `A3C` 实例并行运行。在高度动态的资源共享系统中，每个智能体致力于创建策略 `π`，以减少其在每项活动上花费的时间。与依赖经验回放或集中式架构的现有 `DRL` 方法不同，我们采用分布式方法，学习在多个层级同时发生。在持续收敛的状态空间设置中改进决策，对广泛的延迟容忍车辆服务具有重要意义。正如上文所述，学习过程分为两层。

### 下层学习

每个车辆智能体在连接到更大网络时，使用其 Actor-Critic 网络实例。智能体可利用该网络学习本地模型的定制版本。首先，智能体从全局 Actor-Critic 网络导入权重 `θ[i]`、`w[i]` 到其本地网络，后者随即重置为初始值。此后，智能体通过与环境交互开始在线学习。换言之，当接收到新任务时，智能体的 Actor 网络将根据策略 `π(s) → a` 执行卸载动作 `ai`，并获得奖励 `ri`。本地 Critic 网络通过计算状态价值 `V^π(s[t])` 为 Actor 提供建设性反馈。基于此预测值，Actor 网络将探索其他卸载选项。Actor 和 Critic 网络共同掌握卸载模型。在建立最终状态之前，智能体根据本地策略与环境交互有限时间 `t-max`。每个回合结束后，智能体根据计算出的本地价值和策略损失更新全局网络。

### 上层学习

每个回合结束时，本地学习到的卸载模型权重以符号 `(θ'[1], θ'[2], ..., θ'[n], w'[1], w'[2], ..., w'[n])` 发送至全局 Actor-Critic 网络。若满足结束条件或游戏结束，回合终止。在本项目中，我们通过雾服务器联盟部署全球网络。需注意，全局网络的学习任务已移交给单个联邦节点（可能是驻留时间最短的雾服务器 `argmin_{i ∈ F} Z_i`），其余联邦节点处理层间通信。全局网络通过添加本地模型权重来更新全局模型 `(θ[1], θ[2], ..., θ[n], w[1], w[2], ..., w[n])`。得益于方法的异步特性，全局网络无需接收定期的本地更新。由于两层间丰富的通信与协作信息交换，该方法通过最小化预测折扣未来效用 `Rt|(st, ai)`（与作业在队列中的驻留时长成正比）而快速收敛。

## 卸载决策机制

由于任务驻留时长与奖励的相关性，车辆做出卸载判断。如前所述，车辆选择动作将任务委托给邻近节点，获得的奖励取决于所选动作。卸载车辆在运行期间监控车辆健康状况，并通过基于时间的任务时长计算验证总奖励。在每个作业节点花费时间最少的卡车获得最多奖励并更快到达终点。因此，该解决方案能够基于训练模型的权重和概率分布，针对不同到达率做出卸载决策。正如我们所见，车辆对卸载模型任务的分布式学习，在基础层面解决了优化问题。由于我们使用分布式 `A3C` 技术，同时执行多个仿真场景。操作车辆的智能体也在其虚拟世界中交互。每辆车实时从环境中学习，做出适合其独特情况的最优卸载决策。上层必须聚合来自下层的参数更新并将其反馈下发。通过汇编仿真环境中所有车辆的最新信息，上层助力智能体获得更多样化的训练体验。

## 算法 1：基于 A3C 的任务卸载解决方案

```
1:  procedure main(self)
2:    if Training Model exists then
3:      x ← LowerTierLearning()          ▻ Agents Online Learning
4:    end if
5:  end procedure

6:  procedure LowerTierLearning(V[1], V[3], V[n])
7:    Get Concurrent Threads
8:    Global Parameters ← (θ, w)
9:    Local Parameters ← (θ′, w′)
10:   dθ = dw = 0                        ▻ Zero Gradient initialization
11:   θ′ = θ and w′ = w                  ▻ reset using global weights
12:   x ← AgentExperience()
13:  end procedure

14:  procedure AgentExperience(self, s, a, r, s′)
15:    s = sample state for an agent v[i]
16:    for t ≤ t[max] do:
17:      while (episode[i] != End) do:
18:        Actor ← π(s; a[i])             ▻ Actor Takes Action
19:        r[t](s, s′)                    ▻ Gets reward and move to the next state
20:        Update t = t + 1
21:      end while
22:      Critic ← V(S[t]; w)              ▻ Critic Estimate
23:      Gradient Computation w.r.t θ′ : dθ ← From Equation??
24:      Gradient Computation w.r.t w′ : dw ← From Equation 14
25:      x ← UpperTierUpdate()            ▻ Global Model Update
26:    end for
27:  end procedure

28:  procedure UpperTierUpdate(dθ, dw)
29:    Global[α] ← dθ; Global[c] ← dw     ▻ Asynchronous Local to Global updates
30:  end procedure
```

