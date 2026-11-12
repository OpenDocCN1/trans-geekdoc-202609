
- 24. Pichl, M., Zangerle, E., Specht, G.: Understanding playlist creation on music streaming platforms. In: IEEE International Symposium on Multimedia, ISM, pp. 475–480. IEEE Computer Society (2016). https://doi.org/10.1109/ISM.2016.0107

- 25. Pronzato, L., Wynn, H., Zhigljavsky, A.: A generalized golden-section algorithm for line search. IMA J. Math. Control Inf. 15 (1998). https://doi.org/10.1093/imamci/15.2.185

- 26. Ribeiro, M.T., Singh, S., Guestrin, C.: Why should I trust you?: Explaining the predictions of any classifier. In: KDD, pp. 1135–1144. ACM (2016)

- 27. Rosenberg, G., et al.: Explainable artificial intelligence using expressive boolean formulas. Mach. Learn. Knowl. Extract. 5(4), 1760–1795 (2023). https://doi.org/10.3390/make5040086, https://www.mdpi.com/2504-4990/5/4/86

- 28. Sakurai, K., Togo, R., Ogawa, T., Haseyama, M.: Controllable music playlist generation based on knowledge graph and reinforcement learning. Sensors 22(10), 3722 (2022)

- 29. Samer, M., Szeider, S.: Algorithms for propositional model counting. J. Discrete Algorithms 8(1), 50–64 (2010)

- 30. Shih, A., Choi, A., Darwiche, A.: A symbolic approach to explaining bayesian network classifiers. In: IJCAI, pp. 5103–5111. ijcai.org (2018)

- 31. Mr, U.C.I.: Mushroom. UCI Machine Learning Repository (1987). https://doi.org/10.24432/C5S95T

- 32. Mr, U.C.I.: Molecular biology (Splice-junction Gene Sequences). UCI Mach. Learn. Repository (1992). https://doi.org/10.24432/C5M888

- 33. Verreet, V., De Raedt, L., Bekker, J.: Modeling PU learning using probabilistic logic programming. Mach. Learn. 113(3), 1351–1372 (2024)

- 34. Vreeken, J., van Leeuwen, M., Siebes, A.: Krimp: mining itemsets that compress. Data Min. Knowl. Discov. 23(1), 169–214 (2011)

- 35. Wang, E., Khosravi, P., Van den Broeck, G.: Probabilistic sufficient explanations. In: IJCAI, pp. 3082–3088. ijcai.org (2021)

- 36. Xiao, H., Rasul, K., Vollgraf, R.: Fashion-MNIST: a novel image dataset for benchmarking machine learning algorithms. CoRR abs/1708.07747 (2017)

- 37. Yuan, Y., Bai, F.: Absolute value inequality svm for the pu learning problem. Mathematics 12, 1454 (2024). https://doi.org/10.3390/math12101454

- 38. Zhang, H., Chen, Q., Zou, Y., Pan, Y., Wang, J., Stevenson, M.: Document set expansion with positive-unlabeled learning: a density estimation-based approach. CoRR arXiv:2401.11145 (2024)

## Interpretable Hybrid-Rule Temporal Point Processes

Yunyang Cao, Juekai Lin, Hongye Wang, Wenhao Li, and Bo Jin

Tongji University, 200092 Shanghai, China

{whli,bjin}@tongji.edu.cn

**Abstract.** Temporal Point Processes (TPPs) are widely used for modeling event sequences in various medical domains, such as disease onset prediction, progression analysis, and clinical decision support. Although TPPs effectively capture temporal dynamics, their lack of interpretability remains a critical challenge. Recent advancements have introduced interpretable TPPs. However, these methods fail to incorporate numerical features, thereby limiting their ability to generate precise predictions. To address this issue, we propose Hybrid-Rule Temporal Point Processes (HRTPP), a novel framework that integrates temporal logic rules with numerical features, improving both interpretability and predictive accuracy in event modeling. HRTPP comprises three key components: basic intensity for intrinsic event likelihood, rule-based intensity for structured temporal dependencies, and numerical feature intensity for dynamic probability modulation. To effectively discover valid rules, we introduce a two-phase rule mining strategy with Bayesian optimization. To evaluate our method, we establish a multi-criteria assessment framework, incorporating rule validity, model fitting, and temporal predictive accuracy. Experimental results on real-world medical datasets demonstrate that HRTPP outperforms state-of-the-art interpretable TPPs in terms of predictive performance and clinical interpretability. In case studies, the rules extracted by HRTPP explain the disease progression, offering valuable contributions to medical diagnosis. The supplementary material is available at https://github.com/yy-c/HRTPP0.

**Keywords:** Temporal point processes · Interpretability · Event sequence modeling · Logic rules

J. Lin and H. Wang—Contributed equally to this work.

**Supplementary Information** The online version contains supplementary material available at https://doi.org/10.1007/978-3-032-06066-2_26.

### 1 Introduction

Event sequence data is prevalent in various domains, especially healthcare, including disease onset prediction [3, 21], progression analysis [6, 14], and clinical decision support [10, 20], where events occur asynchronously over time. Unlike traditional continuous-time series, which record values at regular intervals, event sequence data consists of discrete events with irregular time stamps, highlighting the necessity of specialized methods for discrete temporal data processing. Numerical features often accompany event sequences, providing crucial contextual information such as intensity, magnitude, or categorical attributes, which are essential for capturing complex temporal dependencies and enhancing predictive performance [18].

Temporal Point Processes (TPPs) are widely used for modeling event sequence data due to their ability to capture the stochastic nature of event occurrences over time. Traditional point process models, such as the Poisson process [13], Hawkes process [9], and self-correcting process [11], rely on predefined parametric intensity functions, which often struggle to capture complex temporal dependencies and require strong assumptions about the underlying data distribution. To address these limitations, neural point processes, including models based on recurrent neural networks (RNNs) [5], transformer architectures [29], and continuous normalizing flows [25], have been proposed to learn flexible, data-driven representations of event dynamics. However, these learning-based approaches often lack interpretability and require large amounts of training data to generalize effectively.

The interpretability of temporal point processes is crucial for many real-world applications, especially in healthcare, where understanding the underlying event dynamics is as important as making accurate predictions. For example, in medical diagnostics, an interpretable TPP model can assist doctors in analyzing disease progression by identifying key rules influencing the timing of medical events. Recent advancements have introduced interpretable TPPs, incorporating rule-based mechanisms [14,15,23] or sparse attention structures [17]. However, these methods typically sacrifice key advantages of numerical features, thereby limiting their ability to generate precise predictions. Thus, existing approaches face several limitations: traditional TPP models [4,9], though capable of utilizing numerical features, often lack the flexibility to capture complex temporal dependencies; neural TPP models [5], though powerful, are typically considered black boxes with limited transparency; and interpretable models [14,17], while offering some level of interpretability, often fail to incorporate rich numerical features effectively, reducing their predictive accuracy and rule reliability.

An urgent issue is ensuring both interpretability and accuracy. To address these issues, we propose Hybrid-Rule Temporal Point Processes (HRTPP), a novel framework that integrates rule-based mechanisms with numerical feature enhancement. HRTPP integrates three key intensity components: basic intensity, rule-based intensity, and numerical feature intensity, which together determine the overall intensity. The numerical feature intensity captures the influence of continuous-valued attributes. The rule-based intensity encodes temporal dependencies through predefined logic rules, which are optimized via a structured rule mining process involving Bayesian optimization. The best rule set is finally selected by a two-stage mining strategy.

The contributions of this paper are as follows:

- A rule-guided numerical augmentation framework is proposed, integrating rule-based mechanisms with numerical features to enhance TPP modeling.
