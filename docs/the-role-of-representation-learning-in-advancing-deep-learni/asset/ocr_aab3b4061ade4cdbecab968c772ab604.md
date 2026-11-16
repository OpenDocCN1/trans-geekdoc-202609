Table D.1.4: Effect of tree depth on object detection performance. The MP Sliding Window parser is evaluated with varying tree depths L. A Backbone-Decoder model (i.e. no tree encoder) is used as a baseline (L = 1).

| Model | mAP | mAP50 | mAP75 | mAPS | mAPM | mAPL |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Backbone-Decoder (L = 1) | 24.40 ± 0.10 | 46.77 ± 0.14 | 22.39 ± 0.11 | 6.30 ± 0.12 | 25.11 ± 0.13 | 42.66 ± 0.02 |
| MP Sliding Window (L = 3) | 23.24 ± 0.43 | 44.39 ± 0.47 | 21.37 ± 0.41 | 4.79 ± 0.84 | 22.64 ± 0.68 | 43.17 ± 0.41 |
| MP Sliding Window (L = 5) | 25.56 ± 0.41 | 48.36 ± 0.96 | 23.97 ± 0.52 | 6.62 ± 0.22 | 26.71 ± 0.95 | 44.85 ± 0.48 |

# Tree Depth

We analyze how the tree’s depth (i.e. number of levels) influences model performance. Specifically, we test three different tree depths: 5 levels, 3 levels and 1 level. The 5-level configuration corresponds to the default depth used in the previous experiments. The 1-level configuration is equivalent to a simplified model consisting of only a backbone and a standard transformer decoder (i.e. no tree encoder). For the 3-level and 5-level configurations, we use the best model configuration from the previous experiments (trained without using the “all nodes” loss component).

Table D.1.4 presents the evaluation metrics for the different configurations tested. Increasing the tree depth generally improves object detection performance. The model with 5 levels statistically significantly outperforms the others in most metrics (except mAPS). This may be because higher-level nodes capture longer-range dependencies due to their larger receptive fields. This is supported by the fact that, among the size-based metrics (mAPS, mAPM and mAPL), the largest performance difference occurs in mAPL.

However, the Backbone-Decoder baseline (L = 1) outperforms the model with 3 levels. This suggests that shallow tree representations may not fully exploit the benefits of our proposed architecture, and can even reduce performance.

# Scaling with increased resolution

We analyze the effect on performance when doubling the input resolution, thus adding another level to the tree. As we can see in Table D.1.5, performance increases by a decent margin. These results underpin the effectiveness of our proposed architecture and the capabilities of the decoder to effectively parse a tree with many levels.