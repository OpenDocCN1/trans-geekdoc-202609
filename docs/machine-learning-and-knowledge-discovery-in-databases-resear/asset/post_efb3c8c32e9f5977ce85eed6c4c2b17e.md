
## 6 Conclusion

We studied the problem of counting temporal triangles in a stream of temporal edges. We introduced **STEP**, a sampling algorithm enhanced with a predictor, which provides highly accurate estimates while using minimal computational resources compared to SotA approaches. To the best of our knowledge, **STEP** is the _first algorithm_ for temporal triangle counting using predictions. Experimental results show that **STEP** is much faster than SotA exact methods and requires significantly less resources than approximate SotA streaming algorithms, often obtaining more accurate estimates. Finally, we show how to efficiently compute a simple predictor, that can be also used for an online processing of the graph.

Future research includes the development of more advanced and domain-dependent predictors (e.g., learning specific edge-weights for the classification of important edges to retain over the stream), and extending **STEP**'s approach to other temporal motifs [32,34].

**Acknowledgments.** This research is funded by the Ministry of University and Research within the Complementary National Plan PNC-I.1 “Research initiatives for innovative technologies and pathways in the health and welfare sector. D.D. 931 of 06/06/2022, PNC0000002 DARE - Digital Lifelong Prevention CUP: B53C22006440001” and PRIN Project n. 2022TS4Y3N “EXPAND: scalable algorithms for EXploratory Analyses of heterogeneous and dynamic Networked Data”. This research is also funded by the ERC Advanced Grant REBOUND (834862), and the Wallenberg AI, Autonomous Systems and Software Program (WASP) funded by the Knut and Alice Wallenberg Foundation.

**Disclosure of Interests.** The authors have no competing interests to declare that are relevant to the content of this article.

## References

- 1. Azar, Y., Panigrahi, D., Touitou, N.: Online graph algorithms with predictions. SODA (2022)
- 2. Belth, C., Zheng, X., Koutra, D.: Mining persistent activity in continually evolving networks. KDD (2020)
- 3. Bernardini, G., Lindermayr, A., Marchetti-Spaccamela, A., Megow, N., Stougie, L., Sweering, M.: A universal error measure for input predictions applied to online graph problems. NeurIPS (2022)
- 4. Boldin, C., Vandin, F.: Fast and accurate triangle counting in graph streams using predictions. ICDM (2024)
- 5. Boucheron, S., Lugosi, G., Bousquet, O.: Concentration Inequalities. Springer (2004)
- 6. Chen, J., Silwal, S., Vakilian, A., Zhang, F.: Faster fundamental graph algorithms via learned predictions. ICML (2022)
- 7. Chen, J.Y., et al.: Triangle and four cycle counting with predictions in graph streams. ICLR (2022)
- 8. Debrouvier, A., Parodi, E., Perazzo, M., Soliani, V., Vaisman, A.: A model and query language for temporal graph databases. VLDB Journal (2021)
- 9. Gao, Z., Cheng, C., Yu, Y., Cao, L., Huang, C., Dong, J.: Scalable motif counting for large-scale temporal graphs. ICDE (2022)
- 10. Gionis, A., Oettershagen, L., Sarpe, I.: Mining temporal networks. WWW (2024)
- 11. Heeg, F., Scholtes, I.: Using causality-aware graph neural networks to predict temporal centralities in dynamic graphs. NeurIPS (2024)
- 12. Hessel, J., Tan, C., Lee, L.: Science, AskScience, and BadScience: On the Coexistence of Highly Related Communities. ICWSM (2016)
- 13. Holme, P., Saramäki, J.: Temporal networks. Phys. Rep. (2012)
- 14. Holme, P., Saramäki, J.: Temporal Network Theory. Publishing, Springer Int (2023)
- 15. Jiang, S.H.C., Liu, E., Lyu, Y., Tang, Z.G., Zhang, Y.: Online facility location with predictions. ICLR (2022)
- 16. Kondor, D., Csabai, I., Szüle, J., Pósfai, M., Vattay, G.: Inferring the interplay between network structure and market effects in bitcoin. New J. Phys. (2014)
- 17. Lattanzi, S., Ola, S., Sergei, V.: Speeding up Bellman-Ford via minimum violation permutations. ICML (2023)
- 18. Li, J., Qi, J., Huang, Y., Cao, L., Yu, Y., Dong, J.: MoTTo: Scalable motif counting with time-aware topology constraint for large-scale temporal graphs. CIKM (2024)
- 19. Liu, L., et al.: QTCS: Efficient query-centered temporal community search. PVLDB (2024)
- 20. Liu, P., Benson, A.R., Charikar, M.: Sampling methods for counting temporal motifs. WSDM (2019)
- 21. Liu, P., Guarrasi, V., Sariyuce, A.E.: Temporal network motifs: Models, limitations, evaluation. TKDE (2021)
- 22. Mackey, P., Porterfield, K., Fitzhenry, E., Choudhury, S., Chin, G.: A chronological edge-driven approach to temporal subgraph isomorphism. Big Data (2018)
- 23. Mang, Q., et al.: Efficient historical butterfly counting in large temporal bipartite networks via graph structure-aware index. arXiv (2024)
- 24. Matula, D.W., Beck, L.L.: Smallest-last ordering and clustering and graph coloring algorithms. JACM (1983)
- 25. McGregor, A.: Graph stream algorithms: a survey. SIGMOD (2014)
- 26. Mitzenmacher, M., Vassilvitskii, S.: Algorithms with predictions. CACM (2022)
- 27. Muthukrishnan, S., et al.: Data streams: algorithms and applications. In: Found. Trends®. Theor. Comput. Sci. (2005)
- 28. Pan, Y., Bhalerao, O., Seshadhri, C., Talati, N.: Accurate and fast estimation of temporal motifs using path sampling. ICDM (2024)
- 29. Paranjape, A., Benson, A.R., Leskovec, J.: Motifs in temporal networks. WSDM (2017)
- 30. Pashanasangi, N., Seshadhri, C.: Faster and generalized temporal triangle counting, via degeneration ordering. KDD (2021)
- 31. Porter, A., Mirzasoleiman, B., Leskovec, J.: Analytical models for motifs in temporal networks. WWW (2022)
- 32. Pu, J., Wang, Y., Li, Y., Zhou, X.: Sampling algorithms for butterfly counting on temporal bipartite graphs. arXiv (2023)
- 33. Qin, H., Li, R.H., Yuan, Y., Wang, G., Qin, L., Zhang, Z.: Mining bursting core in large temporal graphs. PVLDB (2022)
- 34. Sarpe, I., Vandin, F.: Eden: simultaneous approximation of multiple motif counts in large temporal networks. CIKM (2021)
- 35. Sarpe, I., Vandin, F.: PRESTO: Simple and scalable sampling techniques for the rigorous approximation of temporal motif counts. SDM (2021)
- 36. Sarpe, I., Vandin, F., Gionis, A.: Scalable temporal motif densest subnetwork discovery. KDD (2024)
- 37. Seshadhri, C., Tirthapura, S.: Scalable subgraph counting: The methods behind the madness. WWW (2019)
- 38. Tang, J., Musolesi, M., Mascolo, C., Latora, V.: Temporal distance metrics for social network analysis. SIGCOMM (2009)
- 39. Tu, K., Li, J., Towsley, D., Braines, D., Turner, L.D.: gl2vec: learning feature representation using graphlets for directed networks. ASONAM (2019)
- 40. Venturin, G., Sarpe, I., Vandin, F.: Efficient Approximate Temporal Triangle Counting in Streaming with Predictions (extended version). arXiv (2025)
- 41. Wang, J., Wang, Y., Jiang, W., Li, Y., Tan, K.L.: Efficient sampling algorithms for approximate motif counting in temporal graph streams. arXiv (2022)
- 42. Wang, P., Qi, Y., Sun, Y., Zhang, X., Tao, J., Guan, X.: Approximately counting triangles in large graph streams including edge duplicates with a fixed memory usage. PVLDB (2017)
- 43. Zhang, T., Fang, J., Yang, Z., Cao, B., Fan, J.: TATKC: A temporal graph neural network for fast approximate temporal Katz centrality ranking. WWW (2024)

## Backdoor Attacks on Graph Classification via Data Augmentation and Dynamic Poisoning

Yadong Wang$^1$, Zhiwei Zhang$^{1(\otimes)}$, Pengpeng Qiao$^2$, Ye Yuan$^1$,
and Guoren Wang$^1$

$^1$ Beijing Institute of Technology, Beijing, China
bit.wangyd@gmail.com, {zwzhang, yuan-ye}@bit.edu.cn, wanggrbit@126.com
$^2$ Institute of Science Tokyo, Tokyo, Japan
peng2qiao@gmail.com

**Abstract.** Graph neural networks (GNNs) have gained widespread adoption in domains such as bioinformatics, social networks, and chem-informatics, yet they remain susceptible to backdoor attacks. Existing backdoor attacks typically rely on subgraph triggers, which often introduce detectable anomalies and employ random poisoned sample selection, resulting in reduced stealthiness and efficiency. To address these limitations, we propose a novel backdoor attack framework that leverages data augmentation-based triggers and dynamic poisoned sample selection. Specifically, we design three alternative data augmentation strategies, edge modification guided by cosine similarity, edge removal based on degree centrality, and feature masking via gradient saliency, as backdoor triggers. Furthermore, we introduce a dynamic poison sample selection method informed by forgetting events. This method dynamically prioritizes high-impact poisoned samples to enhance attack efficiency while reducing the number of samples required to achieve the corresponding attack success rate (ASR). Experiments on four benchmark datasets, PROTEINS, NCI1, Mutagenicity, and ENZYMES, demonstrate the superiority of our method.

**Keywords.** GNNs · Graph Classification · Backdoor Attacks

## 1 Introduction

Graph classification has emerged as a fundamental research direction across multiple domains, particularly in bioinformatics and drug discovery [17], chemoinformatics [11], protein-protein interaction networks [10], and social network analysis [5]. With the rapid advancement of GNNs [1,2,9,14], the ability to model and process graph-structured data has significantly improved. By capturing high-order dependencies between nodes and edges, GNNs have demonstrated outstanding performance in graph classification tasks. However, the widespread
