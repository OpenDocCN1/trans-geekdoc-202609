# Table 2. Unsupervised experiment results (F1-score). ↑ indicates the performance gain of BotTrans against the best unsupervised model.

| | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|---|
| DGI+LOF | 0.5471 | 0.5455 | 0.5392 | **0.5582** | 0.6017 | 0.4808 | 0.5106 | 0.4928 | 0.5190 | 0.5157 |
| DGI+IF | **0.5797** | **0.6477** | **0.6572** | 0.5484 | **0.6966** | **0.6215** | **0.5280** | **0.5254** | **0.5510** | **0.5170** |
| CoLA | 0.4824 | 0.4975 | 0.5022 | 0.5118 | 0.5012 | 0.4971 | 0.4835 | 0.4920 | 0.4894 | 0.5005 |
| CONAD | 0.4207 | 0.4419 | 0.4498 | 0.4506 | 0.4383 | 0.4339 | 0.4802 | 0.4128 | 0.4134 | 0.3945 |
| BotTrans | 36.82%↑ | 24.60%↑ | 20.66%↑ | 33.30%↑ | 18.48%↑ | 20.24%↑ | 18.34%↑ | 31.93%↑ | 27.76%↑ | 32.20%↑ |

**Effectiveness Analysis:** Guided by the theory of generalization bounds, we explore the reasons behind our model's effectiveness by experimentally assessing its capability to minimize the supervised loss within the sources and to reduce discrepancies between source and target domains. Thus, we plot the training process in three representative transfer tasks for BotTrans with another strong baseline AdaGCN in Fig. 3. Key findings include: 1) BotTrans achieves lower source training error Lsup, indicating the CSD-MP module mitigates the network heterophily and over-smoothing problem in source domains, and 2) BotTrans achieves lower domain divergence Ld, indicating the SMST module proposes better adaptation strategy in multi-source tasks.

![](bbox=[0.12, 0.435, 0.9, 0.62])

**Efficiency Analysis:** We compare with strong baselines in Table 1. Time Complexity: BotTrans's running time matches AdaGCN but is 2×M³SDA's, 3×Commander's, and 4×Grade's. However, it offers up to 19% performance boost. Spatial Complexity: BotTrans only requires an additional few hundred megabytes in memory and GPU usage, which is mainly introduced by CSD-MP. Overall, BotTrans achieves a balance between effectiveness and efficiency.

# 5.3 Ablation Study

To address RQ2, we perform ablation studies by incrementally adding key model components, with results summarized in Table 3. We begin with a variant, Base, which uses a simple GCN encoder (Eq. 1) and single-source adaptation components (Eq. 6 and 8). Next, we implement CSD-MP (w/o. edge feature), based on Base, but with cross-source-domain topology excluding edge features. We then sequentially introduce