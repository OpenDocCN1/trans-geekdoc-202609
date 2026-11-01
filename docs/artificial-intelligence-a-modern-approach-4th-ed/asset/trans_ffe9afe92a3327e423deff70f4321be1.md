
The belief-state approach was reinvented in the context of sensorless and partially observable search problems by Genesereth and Nourbakhsh (1993). Additional work was done on sensorless problems in the logic-based planning community (Goldman and Boddy, 1996; Smith and Weld, 1998). This work has emphasized concise representations for belief states, as explained in [第11章](#Chapter11-00.xhtml). Bonet and Geffner (2000) introduced the first effective heuristics for belief-state search; these were refined by Bryce et al. (2006). The incremental approach to belief-state search, in which solutions are constructed incrementally for subsets of states within each belief state, was studied in the planning literature by Kurien et al. (2002); several new incremental algorithms were introduced for nondeterministic, partially observable problems by Russell and Wolfe (2005). Additional references for planning in stochastic, partially observable environments appear in [第16章](#Chapter16-00.xhtml).

Algorithms for exploring unknown state spaces have been of interest for many centuries. Depth-first search in a reversible maze can be implemented by keeping one’s left hand on the wall; loops can be avoided by marking each junction. The more general problem of exploring Eulerian graphs (i.e., graphs in which each node has equal numbers of incoming and outgoing edges) was solved by an algorithm due to Hierholzer (1873).

*欧拉图*

The first thorough algorithmic study of the exploration problem for arbitrary graphs was carried out by Deng and Papadimitriou (1990), who developed a completely general algorithm but showed that no bounded competitive ratio is possible for exploring a general graph. Papadimitriou and Yannakakis (1991) examined the question of finding paths to a goal in geometric path-planning environments (where all actions are reversible). They showed that a small competitive ratio is achievable with square obstacles, but with general rectangular obstacles no bounded ratio can be achieved. (See [图4.20](#Chapter04-05.xhtml#fig4-20).)

In a dynamic environment, the state of the world can spontaneously change without any action by the agent. For example, the agent can plan an optimal driving route from A to B, but an accident or unusually bad rush hour traffic can spoil the plan. Incremental search algorithms such as `Lifelong Planning A*` (Koenig et al., 2004) and `D* Lite` (Koenig and Likhachev, 2002) deal with this situation.

The `LRTA*` algorithm was developed by Korf (1990) as part of an investigation into realtime search for environments in which the agent must act after searching for only a fixed amount of time (a common situation in two-player games). `LRTA*` is in fact a special case of reinforcement learning algorithms for stochastic environments (Barto et al., 1995). Its policy of optimism under uncertainty—always head for the closest unvisited state—can result in an exploration pattern that is less efficient in the uninformed case than simple depth-first search (Koenig, 2000). Dasgupta et al. (1994) show that online iterative deepening search is optimally efficient for finding a goal in a uniform tree with no heuristic information.

Several informed variants on the `LRTA*` theme have been developed with different methods for searching and updating within the known portion of the graph (Pemberton and Korf, 1992). As yet, there is no good theoretical understanding of how to find goals with optimal efficiency when using heuristic information. Sturtevant and Bulitko (2016) provide an analysis of some pitfalls that occur in practice.

[1](#Chapter04-01.xhtml#sup04_1)Luby et al. (1993) suggest restarting after a fixed number of steps and show that this can be much more efficient than letting each search continue indefinitely.

[2](#Chapter04-02.xhtml#sup04_2)Knowledge of vectors, matrices, and derivatives is useful for this section (see [附录A](#Appendix-A-00.xhtml)).

[3](#Chapter04-02.xhtml#sup04_3)In general, the `Newton–Raphson` update can be seen as fitting a quadratic surface to `f` at `x` and then moving directly to the minimum of that surface—which is also the minimum of `f` if `f` is quadratic.

[4](#Chapter04-02.xhtml#sup04_4)A set of points `S` is convex if the line joining any two points in `S` is also contained in `S`. A convex function is one for which the space “above” it forms a convex set; by definition, convex functions have no local (as opposed to global) minima.

[5](#Chapter04-03.xhtml#sup04_5)We assume that most readers face similar problems and can sympathize with our agent. We apologize to owners of modern, efficient cleaning appliances who cannot take advantage of this pedagogical device.

[6](#Chapter04-04.xhtml#sup04_6)In a fully observable environment, each belief state contains one physical state. Thus, we can view the algorithms in [第3章](#Chapter03-00.xhtml) as searching in a belief-state space of singleton belief states.

[7](#Chapter04-04.xhtml#sup04_7)The usual apologies to those who are unfamiliar with the effect of small children on the environment.

[8](#Chapter04-05.xhtml#sup04_8)The term “online” here refers to algorithms that must process input as it is received rather than waiting for the entire input data set to become available. This usage of “online” is unrelated to the concept of “having an Internet connection.”

[9](#Chapter04-05.xhtml#sup04_9)Random walks are complete on infinite one-dimensional and two-dimensional grids. On a three-dimensional grid, the probability that the walk ever returns to the starting point is only about 0.3405 (Hughes, 1995).

# 第5章

## 约束满足问题

我们将看到如何通过将状态视为不仅仅是小黑盒子，从而导致新的搜索方法和对问题结构的更深入理解。

[第3章](#Chapter03-00.xhtml) 和 [第4章](#Chapter04-00.xhtml) 探索了通过搜索状态空间来解决问题的思想：一个节点为状态、边为动作的图。我们看到领域特定的启发式方法可以估计从给定状态到达目标的成本，但从搜索算法的角度来看，每个状态都是原子的或不可分割的——一个没有内部结构的小黑盒。对于每个问题，我们都需要领域特定的代码来描述状态之间的转换。

在本章中，我们通过使用每个状态的分解表示来打开黑盒：变量的集合，每个变量都有一个值。当每个变量都有一个满足该变量所有约束的值时，问题就得到解决。这样描述的问题称为约束满足问题，或 `CSP`。

*约束满足问题*

`CSP` 搜索算法利用状态的结构，并使用通用而非领域特定的启发式方法来解决复杂问题。主要思想是一次性通过识别违反约束的变量/值组合来消除搜索空间的大部分。`CSPs` 的额外优势是动作和转换模型可以从问题描述中推导出来。

### 5.1 定义约束满足问题

约束满足问题由三个组成部分组成，`X`、`D` 和 `C`：

`X` 是一个变量集合，（`X1,..., Xn`}。

`D` 是一个域集合，{`D1,..., Dn`}，每个变量一个。

`C` 是一个约束集合，指定允许的值组合。
