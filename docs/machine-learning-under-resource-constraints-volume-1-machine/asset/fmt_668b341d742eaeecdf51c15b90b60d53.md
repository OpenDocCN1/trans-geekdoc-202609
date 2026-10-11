
请注意运行时间的对数刻度。此处可见，`ThreeSieves` 和 `Random` 方法速度最快。使用 `T = 1000` 有一定性能优势，但最大化性能的下降使其难以被证明合理；而 `T = 5000` 速度仅略慢，却提供了好得多的最大化性能。`SieveStreaming` 和 `SieveStreaming++` 运行时间非常相似，但比 `Random` 和 `ThreeSieves` 慢几个数量级。最后，`Salsa` 是最慢的方法。

关于内存消耗，请再次注意对数刻度。此处，所有版本的 `ThreeSieves` 均使用最少资源，因为我们的算法在所有配置中仅存储单个摘要。这些曲线与 `Random` 重合，因此只能看到 4 条曲线而非 7 条。`SieveStreaming` 及其变体使用的内存大约多两个数量级，因为它们并行跟踪多个筛选器。符合预期，`SieveStreaming++` 使用的内存少于 `SieveStreaming`，后者又少于 `Salsa`。

### 不同 ε 下的性能

不同近似比下算法的表现呈现出与之前略有不同的图景。对于较大的 `ε > 0.05`，非概率算法的性能保持相对稳定，但 `ThreeSieves` 的性能开始下降。对于较小的 `ε ≤ 0.05` 和较大的 `T`，`ThreeSieves` 和 `Salsa` 在所有情况下再次表现最佳。同样，`SieveStreaming` 和 `SieveStreaming++` 表现出相同的行为。关于运行时间和内存消耗，我们看到的图景与之前类似：`ThreeSieves` 以巨大优势成为最快且使用资源最少的方法，其次是 `SieveStreaming(++)` 和 `Salsa`。同样请注意，`ThreeSieves` 在所有配置中需要相同数量的内存，因此在图中呈现重叠。

### 实验总结

总之，`ThreeSieves` 与其他算法具有竞争力，有时甚至优于它们。该算法的概率保证在许多情况下伴随着有竞争力的性能，同时使用更少资源。在某些情况下，`ThreeSieves` 甚至优于 `Greedy` 算法。`ThreeSieves` 最适合小 `ε` 和大 `T`。与其他算法不同，`ThreeSieves` 的资源消耗和总运行时间不会因 `ε` 减小或 `T` 增大而受损。

![Fig. 3.1 Comparison of IndependentSetImprovement, SieveStreaming, SieveStreaming++, Salsa, Random, and ThreeSieves for different K values with fixed ε = 0.001 (top figure) and different ε with fixed K = 50 (bottom figure). The first row shows the relative performance to Greedy (larger is better), the second row shows the total runtime in seconds (logarithmic scale, smaller is better), and the third row shows the maximum memory consumption (logarithmic scale, smaller is better). Each column represents one data-set.](graphic/b_9783110785944-003_fig_001.png)

**图 3.1** 不同 `K` 值下（固定 `ε = 0.001`，顶部图形）和不同 `ε` 下（固定 `K = 50`，底部图形）`IndependentSetImprovement`、`SieveStreaming`、`SieveStreaming++`、`Salsa`、`Random` 和 `ThreeSieves` 的对比。第一行显示相对于 `Greedy` 的相对性能（越大越好），第二行显示总运行时间（秒，对数刻度，越小越好），第三行显示最大内存消耗（对数刻度，越小越好）。每列代表一个数据集。

### 3.1.6 结论

数据摘要是人类快速浏览、检查和理解大量数据的宝贵工具。对于复杂且长时间运行的过程，这些摘要必须在数据生成过程中在线选取。虽然摘要的质量高度依赖于任务和人员（主观性强），但子模函数为生成适用于各种不同任务的小型、可理解摘要提供了成熟的数学框架。在本节中，我们讨论了用于数据摘要的子模函数及其最大化问题。我们专注于流摘要任务，即每个项目仅被评估一次，且必须即时决定是否将其添加到摘要中。我们回顾了该领域现有算法及其理论属性。这些算法针对最坏情况进行优化，而实际问题通常表现得更加良好，特别是流内的数据通常是独立同分布的。这使得 `ThreeSieves` 算法能够以高概率计算出良好的摘要。我们通过实验表明，`ThreeSieves` 不仅优于当前最先进水平，而且资源消耗降低了一个数量级。该算法设计允许选择核函数。这使得人类用户能在极短时间内通过查看具有不同核函数的多个摘要，实现更具交互性的数据探索。

## 3.2 面向数据流和分布式数据回归问题的核心集与草图

*Alexander Munteanu*

**摘要：** 核心集和草图是针对给定计算问题（如回归或聚类）的小型数据摘要。它们在微小失真范围内保留任意可能解的代价函数，因此在优化或推理过程中可作为海量原始数据集的代理。它们具有很强的聚合属性（如线性或可合并性），因此便于在数据流和分布式数据上构建。一旦计算出数据摘要，即可使用经典算法对其进行分析，所得结果将被证明接近最优解。总之，这提高了效率和可扩展性，并支持使用标准离线算法进行流式和分布式计算。

我们将展示线性草图如何实现流式和分布式数据处理，并展示如何通过“合并与缩减”原则，将静态离线核心集构建扩展到这些灵活的计算设置中。接下来，我们综述普通线性回归的经典草图和核心集结果，并展示如何将其扩展到更复杂的模型，如贝叶斯回归、广义线性模型和依赖网络。我们还将通过互补下界展示数据摘要的局限性，以及自然假设和参数化超最坏情况分析如何帮助克服这些局限。

### 3.2.1 引言
