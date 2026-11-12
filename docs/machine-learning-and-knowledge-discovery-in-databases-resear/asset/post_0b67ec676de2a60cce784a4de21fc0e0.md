
embedding-based models. In addition, we did not examine how model performance varies with bag size. For MIL tasks based on the standard assumption, classification typically becomes more difficult as the bag size increases, especially in the case of synthetic data. Finally, compared to other paradigms for describing the graph pooling process (e.g., the SRC model [9]), the generalizability of embedding-based models is limited.

- Large Language Models (LLMs) can assist MIL on graphs in several key ways. First, LLMs can generate high-quality synthetic labels or bag-level descriptions to augment training data under weak supervision. Second, LLMs may facilitate the interpretation of MIL decisions by generating natural language explanations for instance-level contributions. Finally, their ability to generalize across modalities allows for flexible integration of multimodal metadata, aiding cross-domain graph representation learning.

## 9 Related Works

This work explores a novel task in Multiple Instance Learning (MIL), a type of weakly supervised learning problem that originated in the 1990s [4, 13]. Instead of receiving a set of instances that are individually labeled, the learning model receives a set of labeled bags, each containing many instances. Due to the diverse characteristics of tasks, MIL can be classified into four categories based on the following attributes: the composition of bags, the types of data distribution, the ambiguity of instance labels, and the task to be performed; each presenting different challenges [3]. MIL typically involves two levels of tasks: bag-level and instance-level, and we tackle the latter. MIL algorithms are often only effective for one of them [3, 11]. Given the prevalence of weakly supervised inexact data in real-world scenarios, MIL finds numerous applications in diverse domains (e.g., [17]). Since MIL is a long-established field that covers a diverse range of topics, we refer the readers to surveys (e.g., [3]) for more information.

On the other hand, this work is closely related to graph pooling from the methodological perspective. Graph pooling models condense a graph into a smaller-sized graph or a single vector, thus working as an essential component for graph-level tasks that require holistic graph-level representations, such as graph classification and graph generation. Generally, designs of graph pooling could be roughly divided into flat pooling (e.g., [18, 26]) and hierarchical pooling, while the latter can be further categorized into node cluster pooling (e.g., [29]) and node drop pooling (e.g., [15]). Existing pooling methods have been demonstrated to be successful in capturing high-order information on a wide range of applications; however, designing effective pooling operators for node-level tasks are still key challenges [19]. Furthermore, graph pooling faces critical challenges including interpretability, robustness, efficiency, expressiveness and so on. Similarly, we refer the readers to [9, 19] for a more complete and detailed introduction on graph pooling techniques. Our work addresses the lack of designs of effective pooling model for node-level tasks, and provides a comprehensive discussion of the key properties of different pooling paradigms.

## 10 Conclusions

In this work, we introduce the node-level MIL task for the first time and investigate the role of graph pooling in this context. We propose a general approach to transform classical embedding-based pooling into an instance-based style, which is intrinsically more suitable for node-level tasks. Furthermore, we analyze key theoretical properties of both frameworks, including permutation invariance, expressiveness, and interpretability. Experimental evaluations on benchmark datasets, simulating various application scenarios, demonstrate the effectiveness of instance-based models. This work pioneers the extension of graph pooling beyond graph-level tasks to node-level tasks, providing both theoretical and empirical insights. As future work, we will explore the design of pooling mechanisms with stronger generalization capabilities and higher efficiency.

## Acknowledgments

This paper is based on results obtained from the project, “Research and Development Project of the Enhanced infrastructures for Post-5G Information and Communication Systems” (JPNP20017), commissioned by the New Energy and Industrial Technology Development Organization (NEDO), and was supported by JSPS KAKENHI Grant Numbers JP25K21275, JP25K03231, JP23H03451.

## References

- 1. Bianchi, F.M., Lachi, V.: The expressive power of pooling in graph neural networks. Adv. Neural. Inf. Process. Syst. **36**, 71603–71618 (2023)
- 2. Bojchevski, A., Günnemann, S.: Deep Gaussian embedding of graphs: unsupervised inductive learning via ranking. arXiv preprint arXiv:1707.03815 (2017)
- 3. Carbonneau, M.A., Cheplygina, V., Granger, E., Gagnon, G.: Multiple instance learning: a survey of problem characteristics and applications. Pattern Recogn. **77**, 329–353 (2018)
- 4. Dietterich, T.G., Lathrop, R.H., Lozano-Pérez, T.: Solving the multiple instance problem with axis-parallel rectangles. Artif. Intell. **89**(1–2), 31–71 (1997)
- 5. Duan, Y., et al.: Dual cost-sensitive graph convolutional network. In: 2022 International Joint Conference on Neural Networks (IJCNN), pp. 1–8. IEEE (2022)
- 6. Duan, Y., Liu, X., Jatowt, A., Yu, H.T., Lynden, S.J., Matono, A.: Inexact graph representation learning. In: IJCNN (2024)
- 7. Fey, M., Lenssen, J.E.: Fast graph representation learning with PyTorch geometric. arXiv preprint arXiv:1903.02428 (2019)
- 8. Foulds, J., Frank, E.: A review of multi-instance learning assumptions. Knowl. Eng. Rev. **25**(1), 1–25 (2010)
- 9. Grattarola, D., Zambon, D., Bianchi, F.M., Alippi, C.: Understanding pooling in graph neural networks. IEEE Trans. Neural Netw. Learn. Syst. **35**(2), 2708–2718 (2022)
- 10. Hamilton, W., Ying, Z., Leskovec, J.: Inductive representation learning on large graphs. Adv. Neural Inf. Process. Syst. **30** (2017)
- 11. Ilse, M., Tomczak, J., Welling, M.: Attention-based deep multiple instance learning. In: International Conference on Machine Learning, pp. 2127–2136. PMLR (2018)
- 12. Javed, S.A., Juyal, D., Padigela, H., Taylor-Weiner, A., Yu, L., Prakash, A.: Additive MIL: intrinsically interpretable multiple instance learning for pathology. Adv. Neural. Inf. Process. Syst. **35**, 20689–20702 (2022)
- 13. Keeler, J., Rumelhart, D., Leow, W.: Integrated segmentation and recognition of hand-printed numerals. Adv. Neural Inf. Process. Syst. **3** (1990)
- 14. Kingma, D.P., Ba, J.: Adam: a method for stochastic optimization. arXiv preprint arXiv:1412.6980 (2014)
- 15. Lee, J., Lee, I., Kang, J.: Self-attention graph pooling. In: International Conference on Machine Learning, pp. 3734–3743. PMLR (2019)
- 16. Leman, A., Weisfeiler, B.: A reduction of a graph to a canonical form and an algebra arising during this reduction. Nauchno-Tekhnicheskaya Informatsiya **2**(9), 12–16 (1968)
- 17. Li, W., Duan, L., Xu, D., Tsang, I.W.H.: Text-based image retrieval using progressive multi-instance learning. In: 2011 International Conference on Computer Vision, pp. 2049–2055. IEEE (2011)
- 18. Li, Y., Tarlow, D., Brockschmidt, M., Zemel, R.: Gated graph sequence neural networks. arXiv preprint arXiv:1511.05493 (2015)
- 19. Liu, C., et al.: Graph pooling for graph neural networks: progress, challenges, and opportunities. arXiv preprint arXiv:2204.07321 (2022)
- 20. Lundberg, S.: A unified approach to interpreting model predictions. arXiv preprint arXiv:1705.07874 (2017)
- 21. Ma, Y.T.: Deep Learning on Graphs. Cambridge University Press (2021)
- 22. Pei, H., Wei, B., Chang, K.C.C., Lei, Y., Yang, B.: Geom-GCN: geometric graph convolutional networks. arXiv preprint arXiv:2002.05287 (2020)
- 23. Qi, C.R., Su, H., Mo, K., Guibas, L.J.: PointNet: deep learning on point sets for 3D classification and segmentation. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 652–660 (2017)
- 24. Shchur, O., Mumme, M., Bojchevski, A., Günnemann, S.: Pitfalls of graph neural network evaluation. arXiv preprint arXiv:1811.05868 (2018)
- 25. Sirinukunwattana, K., Raza, S.E.A., Tsang, Y.W., Snead, D.R., Cree, I.A., Rajpoot, N.M.: Locality sensitive deep learning for detection and classification of nuclei in routine colon cancer histology images. IEEE Trans. Med. Imag. **35**(5), 1196–1206 (2016)
- 26. Vinyals, O., Bengio, S., Kudlur, M.: Order matters: sequence to sequence for sets. arXiv preprint arXiv:1511.06391 (2015)
- 27. Wang, X., Yan, Y., Tang, P., Bai, X., Liu, W.: Revisiting multiple instance neural networks. Pattern Recogn. **74**, 15–24 (2018)
- 28. Yang, Z., Cohen, W., Salakhudinov, R.: Revisiting semi-supervised learning with graph embeddings. In: International Conference on Machine Learning, pp. 40–48. PMLR (2016)
- 29. Ying, Z., You, J., Morris, C., Ren, X., Hamilton, W., Leskovec, J.: Hierarchical graph representation learning with differentiable pooling. NeurIPS **31** (2018)
- 30. Zaheer, M., Kottur, S., Ravanbakhsh, S., Poczos, B., Salakhutdinov, R.R., Smola, A.J.: Deep sets. Adv. Neural Inf. Process. Syst. **30** (2017)
- 31. Zhang, B., et al.: The expressive power of graph neural networks: a survey. IEEE Trans. Knowl. Data Eng. (2024)
