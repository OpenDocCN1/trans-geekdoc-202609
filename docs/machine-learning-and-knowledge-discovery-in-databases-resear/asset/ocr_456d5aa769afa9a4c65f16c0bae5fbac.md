| Model | Kaggle | | | LCS | | |
|---|---|---|---|---|---|---|
| | F1 | AUC | Acc | F1 | AUC | Acc |
| BERT | 44.02 ±1.09 | 63.46 ±0.46 | 77.78 ±0.09 | 46.14 ±2.84 | 64.82 ±1.36 | 79.96 ±0.38 |
| RoBERTa | 50.93 ±0.76 | 66.94 ±0.40 | 79.12 ±0.10 | 47.72 ±0.44 | 65.55 ±0.22 | 80.16 ±0.03 |
| BART | 46.89 ±1.55 | 64.88 ±0.71 | 78.47 ±0.09 | 48.18 ±1.22 | 65.79 ±0.62 | 80.14 ±0.07 |
| DeBERTa | 49.94 ±1.13 | 66.42 ±0.59 | 79.08 ±0.09 | 47.38 ±2.22 | 65.42 ±1.08 | 80.13 ±0.08 |
| Bge-Large | 52.51 ±0.58 | 67.74 ±0.37 | 77.44 ±0.21 | 52.68 ±0.36 | 68.46 ±0.23 | 79.24 ±0.11 |
| GCN | 59.22 ±1.18 | 71.61 ±0.74 | 82.08 ±0.26 | 62.12 ±1.18 | 73.72 ±0.89 | 83.92 ±0.23 |
| R-GCN | 63.07 ±0.81 | 74.09 ±0.60 | 82.96 ±0.16 | 62.99 ±0.89 | 76.18 ±0.72 | 85.19 ±0.21 |
| GAT | 60.98 ±0.09 | 72.72 ±0.60 | 82.43 ±0.01 | 65.73 ±0.12 | 75.92 ±0.13 | 85.18 ±0.02 |
| SimpleHGN | 60.12 ±1.04 | 71.60 ±0.88 | 82.08 ±0.26 | 63.79 ±0.88 | 74.64 ±0.64 | 84.66 ±1.61 |
| HGT | 63.99 ±0.25 | 75.61 ±0.25 | 81.66 ±0.23 | 60.89 ±0.46 | 73.96 ±0.53 | 81.86 ±0.16 |
| GPS | 61.04 ±0.84 | 73.50 ±0.53 | 81.25 ±0.55 | 64.21 ±0.30 | 75.60 ±0.92 | 82.40 ±0.91 |
| DNSD | 46.33 ±2.37 | 64.50 ±1.11 | 78.44 ±0.14 | 44.69 ±1.64 | 64.10 ±0.74 | 79.76 ±0.08 |
| SpoilerNet | 57.19 ±0.69 | 70.64 ±0.44 | 79.85 ±0.10 | 62.86 ±0.38 | 74.62 ±0.69 | 83.23 ±0.23 |
| MVSD | <u>65.08</u> ±0.69 | <u>75.42</u> ±0.56 | <u>83.59</u> ±0.11 | <u>69.22</u> ±0.61 | <u>78.26</u> ±0.63 | <u>86.37</u> ±0.08 |
| Ours | **80.24** ±0.73 | **87.00** ±0.37 | **89.65** ±0.36 | **75.37** ±0.10 | **83.71** ±0.27 | **88.32** ±0.08 |

GUSD achieves **6.1%** higher Binary-F1, **5.5%** higher AUC, and **2.0%** higher accuracy on the LCS dataset, as well as **15.2%** higher Binary-F1, **11.6%** higher AUC, and **6.1%** higher accuracy on the Kaggle dataset. These improvements are statistically significant.

+   - In both datasets, **graph-based models generally outperform other types of baselines**, reaffirming the importance of analyzing the graph structure of reviews and their corresponding users and movies.
+   - Compared with DNSD [6], which also focuses on genre features of the reviews, GUSD surpasses DNSD across all three metrics in both datasets, further proving the effectiveness and robustness of our global-aware genreformer and GMoE methods.
+   - Both SpoilerNet [36] and GUSD utilize user bias, but GUSD outperforms SpoilerNet in all three metrics across both datasets. This demonstrates that our dynamic graph pretraining can better identify the latent behavior pattern of whether a user is likely to post spoilers.

# 4.3 Ablation Study

As GUSD outperforms all the baselines and has reached state-of-the-art (SOTA) performance across the two datasets, we conducted ablation study to further