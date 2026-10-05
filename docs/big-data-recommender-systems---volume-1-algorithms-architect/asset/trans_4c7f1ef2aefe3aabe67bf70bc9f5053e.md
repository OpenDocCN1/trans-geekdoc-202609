

# 用于推荐系统的深度生成模型

![](img/6d0ce7dba01af52e1c2fae47d5b04a05_145_0.png)

**图 6.9 协同变分自编码器：** (a) 展示了 PMF 和 VAE 的集成图形结构，(b) 展示了使用 VAE 的内容生成部分

第 6.2.3 节），该后验概率是不可计算的；因此，我们求助于变分推断（VI）。该模型的 ELBO 表达式如下：

```
log P(X, R) = E_q[log P(Z, U, V, R, X) - q(U, V, Z)] (6.35)
```

在这里，变分分布 $q$ 作用于三个隐变量 $U, V$ 和 $Z$ 上。ELBO 的右侧（即似然性项）可以展开为：

```
\mathcal{L}(U, V, \theta, \phi) = E_{q(Z)}[log P(X|Z) - \mathscr{D}(q(Z|X) || P(Z))] + E_{q(Z)}[log P(V|Z) + log P(R|U) + log Pr(U)] (6.36)
```

其中 $\phi$ 和 $\theta$ 分别是编码器和解码器网络的权重集合。上述方程的第一项仅仅是 VAE 的 ELBO，而第二项是 PMF 的似然性。可以观察到 VAE 的 ELBO 有两部分：第一部分是预测输入与实际输入之间的平方误差和，第二部分是 $\mathscr{D}$，即两个多元正态分布之间的 KL 散度，其公式为：

```
\mathscr{D}(q(Z|X)||Pr(Z)) = -\frac{1}{2}(tr (\Sigma_{\phi}(x)) + (\mu_{\phi}(x))^T (\mu_{\phi}(x)) - log det(\Sigma_{\phi}(x))) (6.37)
```

在似然函数 $\mathcal{L}(U, V, \theta, \phi)$ 中，对 $\theta$ 求梯度是直接的；然而，由于采样操作不是确定性函数，因此无法估计对 $\phi$ 的梯度。这反过来导致反向传播不可行。采用重参数化技巧从同向性正态分布中获取 $z$ 的样本，其中 $z = \mu_{\phi}(x) + \epsilon \Sigma_{\phi}(x)$，$\epsilon \sim N(0, I)$且 $x$ 是单个物品的属性向量 [34]。将相应的分布代入 6.36，得到以下 MAP 估计：

```
\mathscr{L}^{MAP}(U, V, \theta, \phi) = \mathscr{L}(VAE) - \sum_{ij} \frac{C_{ij}}{2}(R_{ij} - U_i^T V_j)^2 - \frac{\lambda_U}{2} \sum_{i} ||U_i||^2 - \frac{\lambda_V}{2} \sum_{j} E_{q(Z|Z)} ||V_j||^2 (6.38)
```

其中 $\mathcal{L}(VAE)$ 表示 VAE 的 ELBO。读者应该注意，上述表达式并不是严格的 MAP 估计，因为参数 Z 仍然在使用变分分布进行推断。因此，我们将上述表达式标记为 $\mathcal{L}^{MAP}$。

**评分预测：** 在学习了参数 $U, V$ 和 $Z$ 后，对于观测到的物品 $D$，用户 $i$ 对物品 $j$ 的预测评分可以如下：

```
$E[R_{j|D}] \approx E[u_i|D] + E[v_j|D]$ \quad (6.39)
```

如果物品 $j$ 没有遗憾（no regrets），则项 $E[v_j|D]$ 对上述表达式没有任何影响，预测评分将完全基于物品的内容信息。

# 6.5 总结

本章介绍了推荐系统生成模型和深度学习（DL）模型的一些最新趋势。首先介绍了 PMF 和 LDA 等经典生成式模型，以及将 PMF 与 LDA 集成创建 CTR 混合模型的方法。第二节介绍了完全基于深度学习的推荐框架，其中我们讨论了 RBM-CF、AutoRec、NCF 和 RNN 等模型。本章最后一节说明了生成模型和深度学习模型的优缺点，并解释了合并这些技术以创建 CDAE 和 CVAE 等深度生成模型的方法。

# 参考文献

- [1] Mnih A, Salakhutdinov RR. Probabilistic matrix factorization. In: Advances in Neural Information Processing Systems; 2008. p. 1257–1264.
- [2] Hofmann T. Probabilistic semantic indexing. In: Proceedings of the 22nd Annual International ACM SIGIR Conference on Research and Development in Information Retrieval. ACM; 1999. p. 50–57.
- [3] Blei DM, Ng Jordan. Latent Dirichlet allocation. The Journal of Machine Learning Research. 2003;3:993–1022.
- [4] Wang C, Blei DM. Collaborative modeling for recommending scientific articles. In: Proceedings of the 17th ACM KDD Conference on Knowledge Discovery and Mining. ACM; 2001. p. 448–456.
- [5] Schmidhuber J. Deep learning in neural networks: An overview. Neural Networks. 2015.
- [6] Covington P, Adams J, Sargin E. Deep neural networks for recommendations. In: Proceedings of the 10th ACM Conference on Recommender Systems. 2016.
- [7] Cheng HT, Koc L, Harmsen J. Wide & deep learning. In: Proceedings of the 1st Workshop on Deep. ACM; 2016.
- [8] Okura S, Tagami Y, Ono S. Embedding-based recommendation for millions of users. In: Proceedings of the 23rd ACM SIGKDD Conference on Knowledge Discovery and Mining.; 2017.
- [9] Salakhutdinov R, Mnih A, Hinton G. Restricted Boltzmann machines for collaborative filtering. In: Proceedings of the 24th International Conference on Machine Learning. 2007.
- [10] Sedayn S, Menon A, Sanner S. Autoencoders meet collaborative filtering. In: Proceedings of the 24th International Conference on World Web. ACM; 2015.
- [11] He X, Liao L, Zhang H. Neural collaborative filtering. In: Proceedings of the 26th International Conference on World Web. 2017.
- [12] Wu CY, Ahmed A, Beutel A. Recurrent neural networks for recommendation. In: Proceedings of The ACM Conference on Search and Mining. 2017.
- [13] Wang H, Wang N, Yang Y. Collaborative deep learning for recommender systems. In: Proceedings of the 21st ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2015.
- [14] Li X, She J. Collaborative variational autoencoder for recommender systems. In: Proceedings of the 23rd ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2017.
- [15] Koren Y, Bell R, Volinsky C. Matrix factorization techniques for recommender systems. Computer. 2009;42(8):30–37.
- [16] Liu B, Fu Y, Yao Z. Learning geographical preferences for point-interest recommendation. In: Proceedings of the 19th ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2013.
- [17] Chanie AJ, Blei DM, Eliassi-Rad T. A probabilistic model for using social networks in personalized item recommendation. In: Proceedings of the 9th ACM Conference on Recommender Systems. ACM; 2015.
- [18] Hofmann T, Puzichha J. Latent class models for collaborative filtering. In: IJCAI vol. 99, 1999. 688–693.
- [19] Popescul A, Pennock DM, Lawrence S. Probabilistic models for unified collaborative and content-based recommendation in sparse-data environments. In: Proceedings of the Seventeenth Conference on Uncertainty in Artificial Intelligence. Morgan Kaufmann Publishers Inc.; 2001. 437–444.
- [20] Ye M, Liu X, Lee WC. Exploring social influence for recommendation: A generative model approach. In: Proceedings of the 35th ACM SIGIR Conference on Research and Development in Information Retrieval. ACM; 2012. p. 671–680.
- [21] Yuan Q, Cong G, Ma Z. Who, where and when what: Discover spatio-temporal topics for twitter users. In: Proceedings of the 19th ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2013, p. 605–613.

