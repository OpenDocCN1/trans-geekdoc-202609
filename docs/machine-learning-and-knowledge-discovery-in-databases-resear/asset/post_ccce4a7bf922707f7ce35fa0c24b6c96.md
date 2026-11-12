

with Dijkstra-generated shortest paths at varying proportions, and compared the resulting differences in precision. The results, presented in Fig. 5c, demonstrate the effectiveness of the shortcuts in enhancing model performance.

**Criteria for Node Contraction.** We employed three criteria for potential node contraction: node occurrence frequency in historical paths (**NF**), bottom-up edge difference (**BUD**), and top-down edge difference (**TDD**). Each criterion was applied to reduce 30% of the nodes across the entire graph, with the comparison results shown in Fig. 5d. The results indicate that selecting the top-down edge difference as the criterion for node contraction effectively maximizes control over the increase in node out-degree, thereby enhancing prediction accuracy and improving search speed. Additionally, the top-down node contraction method demonstrates a notably faster contraction speed.

**Ratios for Node Contraction.** In order to achieve a balance between accuracy and query speed, we tested the precision and query rate of our model under different contraction ratios. The comparison results are presented in Fig. 5e. Thus, to simultaneously maintain a high prediction accuracy and a faster query rate, we ultimately selected a contraction ratio of 0.5.

## 6 Conclusion

Route generation plays a critical role in numerous downstream applications. In practical scenarios, when addressing the problem of recommending the most likely route, it is not only imperative to ensure high prediction accuracy, but also to significantly improve the inference speed. This latter aspect remains a key limitation of existing route generation models. To mitigate this issue, we propose **DRNCS**, an accelerated dual-level route generation model based on node contraction and shortcuts. Specifically, we transformed the original graph into a sparse graph through Shortcut-Edge Differential Contraction. By training the model on both the original trajectories from the original graph and the sparse trajectories from the sparse graph, we successfully generated a dual-level trained model. Furthermore, we employed a shortcut generation approach that consists of two distinct methods: first, merging historical paths, and second, generating shortcuts based on the trained model from the original graph. This comprehensive methodology enabled us to create a more accurate shortcut database in a significantly reduced timeframe. Ultimately, the final prediction results are derived by performing predictions on the sparse graph while invoking the stored shortcut data. Additionally, testing on road network datasets of varying scales demonstrated that our approach achieved over 40% improvement in query speed, while effectively maintaining satisfactory accuracy and reachability. Notably, this optimization in query speed becomes even more pronounced as the scale of the road network increases, thereby highlighting the practical applicability and advantages of our model in real-world scenarios.

## References

- 1. Bhumika, Das, D.: Marrs: a framework for multi-objective risk-aware route recommendation using multitask-transformer. In: Proceedings of the 16th ACM Conference on Recommender Systems (2022). https://api.semanticscholar.org/CorpusID: 252216597
- 2. Dijkstra, E.W.: A note on two problems in connexion with graphs. Numer. Math. 1, 269–271 (1959)
- 3. Geisberger, R., Sanders, P., Schultes, D., Delling, D.: Contraction hierarchies: faster and simpler hierarchical routing in road networks. In: McGeoch, C.C. (ed.) Exper. Algorithms, pp. 319–333. Springer, Berlin Heidelberg (2008)
- 4. Grover, A., Leskovec, J.: node2vec: scalable feature learning for networks. In: Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining (2016)
- 5. Hsieh, H.P., Lin, F.: Recommending taxi routes with an advance reservation – a multi-criteria route planner. Int. J. Urban Sci. 26, 162 – 183 (2021). https://api.semanticscholar.org/CorpusID:233810149
- 6. Jain, J.L., Badia, V., Manchanda, S., Ranu, S.: Neuromlr: Robust & reliable route recommendation on road networks. In: Neural Information Processing Systems (2021)
- 7. Kuo, A.T., Chen, H., Ku, W.S.: Bert-trip: effective and scalable trip representation using attentive contrast learning. In: 2023 IEEE 39th International Conference on Data Engineering (ICDE), pp. 612–623 (2023). https://api.semanticscholar.org/CorpusID:260171278
- 8. Li, X., Cong, G., Cheng, Y.: Spatial transition learning on road networks with deep probabilistic models. In: IEEE 36th International Conference on Data Engineering (ICDE), pp. 349–360 (2020)
- 9. Li, X., Cong, G., Sun, A., Cheng, Y.: Learning travel time distributions with deep generative model. The World Wide Web Conference (2019)
- 10. Rahmani, M., Koutsopoulos, H.N.: Path inference of low-frequency GPS probes for urban networks. In: International IEEE Conference on Intelligent Transportation Systems, pp. 1698–1701 (2012)
- 11. Rahmani, M., Koutsopoulos, H.N.: Path inference from sparse floating car data for urban networks. Transport. Res. Part C-emerging Technol. 30, 41–54 (2013)
- 12. Tarjan, R.E.: Data structures and network algorithms. In: CBMS-NSF Regional Conference Series in Applied Mathematics (1983)
- 13. Wang, J., Wu, N., Zhao, W.X., Peng, F., Lin, X.: Empowering a* search algorithms with neural networks for personalized route recommendation. In: Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining (2019)
- 14. Wang, Y., Wei, L., Chen, P.: Trajectory reconstruction for freeway traffic mixed with human-driven vehicles and connected and automated vehicles. Transport. Res. Part C: Emerg. Technol. 111, 135–155 (2020)
- 15. Qing Wu, H., Chen, Z., Sun, W., Zheng, B., Wang, W.: Modeling trajectories with recurrent neural networks. In: International Joint Conference on Artificial Intelligence (2017)
- 16. Zheng, Y., Quddus, M.A.: Weight-based shortest-path aided map-matching algorithm for low-frequency positioning data (2011)
- 17. Mahmood, M.T., Ali, M.E., Cheema, M.A., Rashid, S.M.M., Sellis, T.: PathOracle: a deep learning based trip planner for daily commuters. In: Machine Learning and Knowledge Discovery in Databases: European Conference (2022)

## GraphWeave : Interpretable and Robust Graph Generation via Random Walk Trajectories

Rahul Nandakumar and Deepayan Chakrabarti

The University of Texas at Austin, Austin, TX 78713, USA

{rahul.nandakumar,deepayan}@utexas.edu

**Abstract.** Given a set of graphs from some unknown family, we want to generate new graphs from that family. Recent methods use diffusion on either graph embeddings or the discrete space of nodes and edges. However, simple changes to embeddings (say, adding noise can mean uninterpretable changes in the graph. In discrete-space diffusion, each step may add or remove many nodes/edges. It is hard to predict what graph patterns we will observe after many diffusion steps. Our proposed method, called GraphWeave, takes a different approach. We separate pattern generation and graph construction. To find patterns in the training graphs, we see how they transform vectors during random walks. We then generate new graphs in two steps. First, we generate realistic random walk “trajectories” which match the learned patterns. Then, we find the optimal graph that fits these trajectories. The optimization infers all edges jointly, which improves robustness to errors. On four simulated and five real-world benchmark datasets, GRAPHWEAVE outperforms existing methods. The most significant differences are on large-scale graph structures such as PageRank, cuts, communities, degree distributions, and flows. GRAPHWEAVE is also 10x faster than its closest competitor. Finally, GRAPHWEAVE is simple, needing only a transformer and standard optimizers. Code is available at https://github.com/rahulnanda1999/GraphWeave.

**Keywords:** Graph Generation · Diffusion · Random Walk · Trajectory

### 1 Introduction

Suppose that we have a set of molecules with some desirable property. For example, these molecules bind to a target protein to treat a disease. Our goal is to find other molecules that have this property. We can formalize this as a graph generation problem. Each molecule is a graph of atoms connected by bonds. The desirable property corresponds to some unknown pattern common to the given graphs. We want to generate new graphs that possess these patterns automatically. As another example, suppose we want to detect bots in a social network.

