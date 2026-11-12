# Table 1. Experiment result on the CATH4.2 dataset.

| Method | Perplexity↓ | | | Recovery(%)↑ | | |
|---|---|---|---|---|---|---|
| | Short | Single | All | Short | Single | All |
| StructGNN [15] | 8.29 | 8.74 | 6.40 | 29.44 | 28.26 | 35.91 |
| GraphTrans [15] | 8.39 | 8.83 | 6.63 | 28.14 | 28.46 | 35.82 |
| GCA [37] | 7.09 | 7.49 | 6.05 | 32.62 | 31.10 | 37.64 |
| GVP [16] | 7.23 | 7.84 | 5.36 | 30.60 | 28.95 | 39.47 |
| AlphaDesign [7] | 7.32 | 7.63 | 6.30 | 34.16 | 32.66 | 41.31 |
| ProteinMPNN [3] | 6.21 | 6.68 | 4.61 | 36.35 | 34.43 | 45.96 |
| PiFold [8] | 6.04 | 6.31 | 4.55 | 39.84 | 38.53 | 51.66 |
| GRADE-IF [42] | 5.49 | 6.21 | 4.35 | 45.27 | 42.77 | 52.21 |
| VFN-IF [22] | 5.70 | 5.86 | 4.17 | 41.34 | 40.98 | 54.74 |
| **AGSDD (ours)** | **4.06** | **4.76** | **2.93** | **53.57** | **48.95** | **64.07** |
| \multicolumn{7}{c}{w/ External Knowledge} |
| LM-Design [46] | 6.77 | 6.46 | 4.52 | 37.88 | 42.47 | 55.65 |
| KW-Design [6] | 5.48 | 5.16 | 3.46 | 44.66 | 45.45 | 60.77 |

# 4.3 Main Results

To validate the effectiveness of our method, we compared it with other strong competitors using the CATH4.2 benchmark, and the results are shown in Table 1. Experimental results demonstrate that our model achieves state-of-the-art performance in AA sequence recovery and perplexity. To the best of our knowledge, our method is the first to achieve 60% recovery without external knowledge of pre-trained language models. In addition, compared to the VFN-IF model, our approach improves the recovery rate by 9.33%, confirming its superior performance. Compared with GRADE-IF, our method increases the recovery rate by 11.86%, indicating the effectiveness of semantic denoising in the denoising network for sequence recovery. Furthermore, while the LM-Design and KW-Design models utilize external knowledge from the pre-trained ESM [21], achieving recovery rates of 55.65% and 60.77%, respectively, our model improves the recovery rates by 8.42% and 3.30%. This demonstrates that our model delivers strong sequence recovery capabilities without external knowledge, thereby reducing computational complexity during the inference stage.

# 4.4 Generalization Capability Analysis

To verify the generalization capability of our model, we directly evaluated the trained model on the TS50 and TS500 datasets. The TS50 and TS500 datasets consist of 50 and 500 test proteins, respectively. As shown in Table 2, our model achieves state-of-the-art performance on both datasets, significantly outperforming existing methods. Specifically, our model achieves a perplexity (PPL) of 2.67