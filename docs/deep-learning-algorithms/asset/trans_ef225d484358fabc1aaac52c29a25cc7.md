
惩罚函数 P(a[t])，其中 t 时刻的控制动作决策为 a[t]，可表示如下：

min : \(\lim_{t \to \infty} \sum_{t=0}^{t-1} P(a[t])\) (3)

受队列稳定性约束：

\(\lim_{t \to \infty} \frac{1}{t} \sum_{t=0}^{t-1} Q[t] < \infty.\) (4)

在 (3) 中，P(a[t]) 表示 t 时刻控制动作决策为 a[t] 时的惩罚函数。

如前所述，当效用最大化（或惩罚函数最小化）与延迟之间存在权衡时，可以使用 Lyapunov 优化理论。基于这一特性，漂移加惩罚（DPP）算法 [2, 3, 4] 旨在在队列稳定性约束下最大化时间平均效用。这里，Lyapunov 函数定义为 \(L(Q[t]) = \frac{1}{2}(Q[t])^2\)，并令 \(\Delta(.)\) 为条件二次 Lyapunov 函数，表达式为 E[L(Q[t+1])−L(Q[t])|Q[t]]，称为 t 时刻的漂移。根据 [2]，该动态策略旨在通过最小化 DPP 中考虑的惩罚函数的上界来实现队列稳定性，其表达式为

\(\Delta(Q[t]) + V\mathbb{E}[P(a[t])].\) (5)

其中 V 是权衡系数。t 时刻 Lyapunov 函数漂移的上界推导如下：

\(L(Q[t + 1]) - L(Q[t]) = \frac{1}{2}((Q[t + 1]^2 - Q[t]^2))\) (6)

\(\le \frac{1}{2}((a(a[t]))^2 + b(a[t])^2) + Q[t](a(a[t]) - b(a[t])).\) (7)

因此，条件 Lyapunov 漂移的上界可推导如下：

\(\Delta(Q[t]) = \mathbb{E}[L(Q[t + 1]) - L(Q[t])|Q[t]] \le C + \mathbb{E}[Q[t](a(a[t]) - b(a[t]))|Q[t]],\) (8)

其中 C 是一个由以下给出的常数：

\(\frac{1}{2}\mathbb{E}[(a(a[t]))^2 + b(a[t])^2|Q[t]] \le C,\) (9)

这假设了到达和离开过程的速率被上界约束。由于 C 是常数，最小化 DPP 的上界如下：

\(V\mathbb{E}[P(\alpha[t])] + \mathbb{E}[Q[t] \cdot (a(\alpha[t]) - b(\alpha[t]))].\) (10)

### 算法 1. 稳定时间平均惩罚函数最小化

```
Initialize:
1: \( t \leftarrow 0 \);
2: \( Q[t] \leftarrow 0 \);
3: Decision Action: \( \forall \alpha[t] \in \mathcal{A} \)
Time-Average Penalty Function Minimization subject to Stability
4: while \( t \le T \) do // T: operation time
5: Observe \( Q[t] \);
6: \( T^* \leftarrow \infty \);
7: for \( \alpha[t] \in \mathcal{A} \) do
8: \( T \leftarrow V \cdot P(\alpha[t]) + Q[t] \cdot (a(\alpha[t]) - b(\alpha[t])) \);
9: if \( T \le T^* \) then
10: \( T^* \leftarrow T \);
11: \( \alpha^*[t+1] \leftarrow \alpha[t] \);
12: end if
13: end for
14: end while
```

最后，基于 Lyapunov 优化理论，每个单位时间 t 中用于在队列稳定性约束下最小化时间平均惩罚函数 \(P(\alpha[t])\) 的动态控制动作决策 \(\alpha[t]\) 可表述如下：

```
\(\alpha^*[t+1] \quad \underset{\alpha[t] \in \mathcal{A}}{\arg \min} [V \cdot P(\alpha[t]) + Q[t] \cdot (a(\alpha[t]) - b(\alpha[t]))]\) (11)
```

其中 A 是所有可能控制动作的集合，\(\alpha^*[t+1]\) 是下一个时隙的最优控制动作决策。

为了验证 (11) 是否正确，可以考虑以下两个示例情况：

- 情况 1：假设 Q[t] \(\approx \infty\)。则

```
\(\alpha^*[t+1] \quad \underset{\alpha[t] \in \mathcal{A}}{\arg \min} [V \cdot P(\alpha[t]) + Q[t] \cdot (a(\alpha[t]) - b(\alpha[t]))]\) (12)
```

```
\(\approx \underset{\alpha[t] \in \mathcal{A}}{\arg \min} [a(\alpha[t]) - b(\alpha[t])].\) (13)
```

然后，(13) 表明控制动作决策应按以下方式工作，即 (i) 到达过程应最小化，(ii) 离开过程应最大化。两种情况均旨在稳定队列，即当 Q[t]≈∞ 时应有利。

- 情况 2：假设 Q[t]=0。则

```
\(\alpha^*[t+1] \arg \min_{a[t] \in \mathcal{A}} [V \cdot P(a[t]) + Q[t] \cdot (a(a[t]) - b(a[t]))]\)
```

```
\(= \arg \min_{a[t] \in \mathcal{A}} V \cdot P(a[t])\)
```

然后，(15) 表明控制动作决策应致力于最小化给定的惩罚函数。这在语义上是合理的，因为当 Q[t]=0 时，无需考虑稳定性，因此可以专注于我们的主要目标。

所提时间平均惩罚函数最小化算法的伪代码如算法 1 所示。第 1 到第 3 行初始化所有变量和参数。算法在每个单位时间中运行，如第 4 行所示。在第 5 行，观察当前队列积压 Q[t] 以用于 (11)。第 7 到第 13 行描述了 (11) 的主要计算过程。

到目前为止，已考虑时间平均惩罚函数最小化。基于该理论，每个单位时间 t 中用于在队列稳定性约束下最大化时间平均效用函数 U(a[t]) 的动态控制动作决策 a[t] 可表述如下：

```
\(\alpha^*[t+1] \arg \max_{a[t] \in \mathcal{A}} [V \cdot U(a[t]) - Q[t] \cdot (a(a[t]) - b(a[t]))]\)
```

其中 A 是所有可能控制动作的集合，\(\alpha^*[t+1]\) 是下一个时隙的最优控制动作决策。

## 2.2 示例：移动设备中的多核调度

本节以一个简单的玩具模型为例，介绍基于 Lyapunov 优化的稳定时间平均优化算法。在本示例中，设计了一种动态核分配决策算法，旨在在队列稳定性约束下最小化时间平均能耗。

如图 1 所示，移动智能手机配备了具有多个内核的处理器。例如，ARM big.LITTLE 处理器配备了多个小核和大核异构内核。

在该系统中，当用户生成事件时会生成任务事件，如图 1 中 a[t] 所示。然后，这些事件会被放入任务队列（即图 1 中的 Q[t]）。随后，事件可以由多核处理器处理。在这种情况下，如果为了处理队列中的事件而分配更多内核，处理可以加速，这有利于队列稳定性。然而，这不利于我们的主要目标，即能耗最小化。另一方面，如果分配较少内核，处理速度会变慢，这对队列稳定性不利，但有利于我们的主要目标，即能耗最小化。最后，可以在能耗最小化（即我们的主要目标）和稳定性之间观察到权衡。因此，可以证实基于 Lyapunov 优化的算法可以使用。

![](img/1752b062af2760b8561f6faaf183b3d0_86_0.png)

图 1. 具有多核处理器的移动设备。

为了设计动态核分配决策，基于 (11)，每个单位时间 t 中用于在队列稳定性约束下最小化时间平均能耗 E(a[t]) 的 a[t] 可表述如下：

```
\alpha^* [t + 1] \quad \arg \min_{a[t] \in \mathcal{A}} [V \cdot E(a[t]) + Q[t] \cdot (a[t] - b(a[t]))] \quad (17)
```

其中 A 是所有可能的核分配组合的集合，\(\alpha^*[t+1]\) 是下一个时隙的最优核分配决策。这里，很明显到达过程是不可控的（i.i.d. 随机事件）；因此可以忽略。然后，动态决策算法的最终形式可定义如下：

```
\alpha^* [t + 1] \quad \arg \min_{a[t] \in \mathcal{A}} [V \cdot E(a[t]) - Q[t] \cdot b(a[t])]. \quad (18)
```

为了检查推导出的等式 (18) 是否正确，可以考虑两个示例情况，即 (i) Q[t] \approx \infty，和 (ii) Q[t]=0：

- 忙碌队列情况 (Q[t]≈∞)：在这种情况下

```
\(\alpha^* [t+1] \quad \arg \min_{a[t] \in \mathcal{A}} [V \cdot E(a[t]) - Q[t] \cdot b(a[t])],\) (19)
```

```
\(= \arg \min_{a[t] \in \mathcal{A}} [-b(a[t])] = \arg \max_{a[t] \in \mathcal{A}} b(a[t]),\) (20)
```

因此，应加速离开过程，即应分配更多内核。这在语义上是正确的，因为如果发生溢出情况，希望能快速处理队列中的事件。

- 忙碌队列情况 (Q[t]=0)：在这种情况下

```
\(\alpha^* [t+1] \quad \arg \min_{a[t] \in \mathcal{A}} [V \cdot E(a[t]) - Q[t] \cdot b(a[t])],\) (21)
```

```
\(= \arg \min_{a[t] \in \mathcal{A}} V \cdot E(a[t]),\) (22)
```

因此，应分配较少内核以实现能耗最小化，这是我们的主要目标。这在语义上是正确的，因为如果系统稳定，即 Q[t]=0，则应希望实现给定的主要目标。

如示例所讨论，所提基于 Lyapunov 优化的动态核分配决策算法按预期工作。

## 稳定控制中的讨论

所提动态超分辨率模型选择算法在多个方面具有益处，具体如下。

### 与硬件/系统无关的自适应

假设该所提算法实现在类似超级计算机的高性能计算机中。在这种情况下，处理应快速；因此，队列积压始终较低。因此，系统有更多机会专注于我们的主要目标，即惩罚函数最小化或效用函数最大化。另一方面，如果硬件本身性能/资源受限（例如，移动设备），则处理速度也会受到处理器低规格的限制。因此，队列积压可能经常繁忙，因为即使使用最快的模型，也可能无法处理队列中的许多数据。因此，
