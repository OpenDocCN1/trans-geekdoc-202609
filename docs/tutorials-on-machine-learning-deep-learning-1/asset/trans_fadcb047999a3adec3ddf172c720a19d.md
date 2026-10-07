

算法 2.具有 $M$ 个温度的 $k$ 步并行温度
**输入：** RBM $(V_1,\dots,V_n,H_1,\dots,H_n$，训练批 $S$，马尔可夫链的当前状态 $v$，平稳分布为 $p_r$，对于 $r=1,\dots,M$
**输出：** 梯度近似 $\Delta v_i$, $\Delta b_j$, $\Delta c_i$，对于 $i=1,\dots,n, j=1,\dots,n$
1 初始化 $\Delta v_i = \Delta b_j = \Delta c_i = 0$，对于 $i=1,\dots,n, j=1,\dots,n$
2 对于每个 $v \in S$ 执行
   对于 $r=1,\dots,M$ 执行
     $v^{(0)} \leftarrow v$
     对于 $i=1,\dots,n$ 采样 $h_{i}^{(r)} \sim p(h_i|v^{(0)})$
     对于 $t=0,\dots,k$ 执行
       对于 $j=1,\dots,n$ 采样 $v_{r,j}^{(t+1)} \sim p(v_j|h_r^{(t)})$
       对于 $i=1,\dots,n$ 采样 $h_{r,i}^{(t+1)} \sim p(h_i|v_r^{(t+1)})$
3 对于 $r \in \{2 \leq s \leq M \text{ 且 } s \pmod 2 \neq 0\}$ 执行
   以 (40) 给概率交换 $(v_{r}^{(k)})$ 和 $(v_{s}^{(k)})$
4 对于 $r \in \{3 \leq s \leq M \text{ 且 } s \pmod 2 \neq 1\}$ 执行
   以 (40) 的概率交换 $(v_{r}^{(k)})$ 和 $(v_{s}^{(k)})$
5 对于 $i=1,\dots,n, j=1,\dots,n$ 执行
     $\Delta w_{ij} \leftarrow \Delta w_{ij} + v_j^{(k)} - p(H_i=1)p(H_i=1|v_{j}^{(k)})$
     $\Delta b_j \leftarrow \Delta b_j + v_j^{(k)} - v_{j}^{(k)}$
     $\Delta c_i \leftarrow \Delta c_i + p(H_i=1) - p(1|v_{i}^{(k)})$

在算法的每一步中，我们在每个温度冷却链中运行 $k$（通常 $k=1$）个采样步，产生样本 $(v_1, h_1), \dots, (v_M, h_M)$。之后，两个温度为 $T_r$ 和 $T_{r-1}$ 的相邻链可能会交换粒子 $(v_r, h_r)$ 和 $(v_{r-1}, h_{r-1})$，其交换概率基于 Metropolis 比例（比：
$$\min \left\{1, \frac{p_r(v_{r-1}, h_{r-1})p_{r-1}(v_r, h_r)}{p_r(v_r, h_r)p_{r-1}(h_{r-1})}\right\}$$ (39)
对于 RBM，其结果为
$$\min \left\{1, \exp \left(-\frac{T_r}{T_{r-1}} (E(v_r, h_r) - E(v_{r-1}, h_{r-1}))\right)\right\}$$ (40)

在执行这些增大混合速率的链间交换后，我们取原始链（温度为 $T_1=1$）的下一个（最终交换的）样本 $v_1$ 作为模型分布的样本。此过程重复 $L$ 次，产生样本 $v_{1,1}, \dots, v_{1,L}$，用于 RBM 分布下的对数似然期望（即 (9) 中的第二项）。通常 $L$ 设置为训练数据批次中的样本数，如算法 2 所示。

与 CD 相比，PT 引入了计算开销，但带来了更快的马尔可夫链混合以及更小的梯度偏差。使用不同 $M$ 取值的 PT 进行对数似然训练的演变见图。

## 6 实值 RBM

到目前为止，我们只考虑了由二进制向量表示的观测，但希望对连续数据进行建模。定义具有实值变量的 RBM 有几种方法。如 [18] 所示，可以通过一种简单的“技巧”使用二进制 RBM 建模连续分布——将输入数据缩放到 $[0,1]$ 区间。即与其采样二进制值，期望 $p(V_j=h)$ 被视为 $V_j$ 的当前状态。除了可见变量的连续值和结果的变化外，采样过程保持不变。通过在能量函数中增加由参数 $d_j, j=1,\dots,m$ 加权的二次项 $d_j^2$，可以使用高斯分布表示可见神经元，这在 (27) 中得出。

标准 RBM 在实值单元上的通用近似能力是有限制的 [38]。

更一般，通过将 RBM 的定义扩展到任意 RF 来覆盖连续变量，能量函数满足 $p(h)=\prod p(h|v)$ 和 $p(v)=\prod p(v|h)$。直接取决于 Hammersley-Clifford 定理并在 [18] 中讨论，这对于任何形式的能量函数
$$E(v,h) = \sum_{i,j} \phi_{ij}(h_i, v_j) + \sum_{j} \psi_j(v_j) + \sum_{i} \nu_i(h_i)$$
其中实值函数 $\phi_{ij}, \psi_j, i=1,\dots,n$, 以及 $j=1,\dots,m$ 满足配分函数 $Z$ 有限的约束。对于任意边缘分布 $p(v_j)$ 和 $p(h_i)$ 几乎相同的能量函数形式。

## 7 放宽限制

在结束章节中，我们将对选定的扩展 RBM 进行简要展望，通过引入对进一步变量的依赖或允许节点之间的任意连接来放宽二分拓扑的限制。

- **条件 RBM**。存在 RBM 的多种推广和扩展。著名的例子是条件 RBM（例如 [35,29]）。在这些模型中，RBM 的某些参数被替换为条件变量函数。
- **玻尔兹机器**。从 RBM 中去掉 "R" 回回到起点——由隐藏和可见变量组成的 MRF，其能量由
$$E(v, h) = -\sum_{i=1}^m h_{ij}v_j - \sum_{k=1}^n \sum_{l=1}^m v_{kl}h_l - \sum_{j=1}^m b_j$$
对应于一层。这些依赖关系使得独立采样和训练变得更加困难。然而，已经开发了专门算法 [32]。

## 下一步

本教程的目标是从概率图模型的角度介绍 RBM，重点关注我们在工作中发现有用的材料。我们希望读者现在已准备好进入构建深度学习架构的高级模型。教程中的所有实验都可以使用开源机器学习库进行复制。

**致谢**。作者感谢联邦教育与研究部的支持，基金编号 01GQ951。

## 参考文献

1. Ackley, D., Hinton, G.: A learning algorithm for Boltzmann machines. Cognitive Science 9, 147–169 (1985).
2. Bengio, Y.: Learning deep architectures for Trends in Machine Learning 21(6), 1601–1621 (2009).
3. Bengio, Y., Delelleau, O.: Justifying contrastive divergence. Neural Computation 21(6), 1601–1621 (2009).
4. Bengio, Y., Lamblin, P., Popovici, D., Larochelle, H.: Greedy training of neural networks. In Schkopf, B., Platt, J., Hoffman, T. (eds) Advances in Neural Information Processing (NIPS), 153–160 (2007).
5. Bishop, C.M.: Markov chains: Pattern recognition and machine learning. Springer (2006).
6. Bremaux, P.: Markov chains: Gibbs fields, Monte Carlo simulation, and queues.
7. Carreira-Perpián, M.A., Hinton, G.E.: Contrastive divergence. In 10th International Conference on Artificial Intelligence and Systems (AISTATS 2003), 59–66 (2003).
8. Cho, K., Rao, T.: Parallel tempering for learning restricted Boltzmann machines. In Proceedings of the International Joint Conference on Neural Networks (IJCNN) 2010, pp. 3246–3253. IEEE Press.
9. Desjaines, G., Curcelle, A.: Parallel tempering of RBMs. In Lee, H., Hinton, G., Ng, A. (eds) NIPS 2010, Deep Learning and Unsupervised.
10. Desjaines, G., Bengio, Y., Vincent, E.: Parallel tempering for training restricted Boltzmann machines. In JMLR Workshop and Conference: AISTATS 2012, pp. 628–646.
11. Fisher, A., Hinton, G.: The Divergence of... Inant     ,,,,22222......, A A A.,,,,.:.: contrast contrast divergence divergence 12, 666666770000000
3.,,,, M, D,,,,,,... on Pattern and Machine Analysis, 6(7), 71–78 (1984).
14. Hastings, K.W.: Monte Carlo methods using Markov chains. Biomet, 57(1), 97–109 (1970).
15. Hinton, G.: Training deep belief nets by minimizing contrastive divergence. Neural Computation, 14, 1771–1800 (2002).
16. Hinton, G.E.: Boltzmann machines. Scholarpage 2(5), 1668 (2007).
1. Hinton, G.E.: Learning layers of representations. In Trends in Cognitive Science, Neural Computation 18(7), 1527–1554 (2006).
18. Hinton, G., Salakhutdin, R., Teh, Y.W.: Reducing the dimensionality of wide data with deep learning. Science, 315(5796), 504–507 (2006).
19. Gel, C., Bachman, T., Heidlich-Mier, V.: Sparse. Journal of Machine Learning Research 9, 953–966 (2008).
20. Kramer, J., Williams, C.: Parallel texture boltzmann machines. In: JMLR Workshop and Conference Proceedings: AISTATS 2012, pp. 628–646 (2012).
21. Koller, D., Friedman, N.: Probabilistic graphical models: Principles and techniques. MIT Press (2009).
22. Lauritzen, L.S.: Graphical models. Oxford University Press (1996).
23. Le Roux, R., Bengio, Y.: Representational power of restricted Boltzmann machines and deep belief networks. Neural Computation 20(6), 1631–1649 (2008).
24. Le Roux, N., Hinton, S., Winn, J.M.: Learning a generative model of images by factoring appearance and shape. Neural Computation 25(3), 595–650 (2011).

