# Table 3. Ablation study. “w/o SA” indicates the model without semantic alignment, “w/o CA” refers to the model without contextual aggregator in the geometric denoising, “w/o ALL” denotes the model without SA, CA and the cell module in message passing.

| Model | CATH Rec | CATH PPL | TS50 Rec | TS50 PPL | TS500 Rec | TS500 PPL |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **AGSDD** | 64.07 | 2.93 | 67.03 | 2.67 | 71.61 | 2.31 |
| w/o SA | 63.13 | 3.00 | 64.46 | 2.80 | 70.32 | 2.39 |
| w/o CA | 61.60 | 3.16 | 64.24 | 2.89 | 68.74 | 2.52 |
| w/o SA & CA | 61.48 | 3.17 | 63.68 | 2.92 | 68.73 | 2.51 |
| w/o ALL | 60.96 | 3.21 | 63.61 | 2.95 | 68.36 | 2.54 |

![](bbox=[0.28, 0.325, 0.75, 0.445])

# Fig. 2. Nonlinear features analysis of contextual aggregator module on layer output. The x-axis shows two adjacent layers, and the y-axis represents the logarithm of KL divergence, which measures changes in node feature distributions. The polyline depicts nonlinear divergences in node representations for 50 randomly selected protein cases from CATH4.2 test set with or without the CA module. Arrows indicate the direction towards nodes with stronger nonlinear features.

the entire protein chain. This limitation hinders the model's ability to contextualize residue interactions, as evidenced by decreased recall and increased perplexity across all datasets. These results confirm the effectiveness of integrating global chain-level information to enrich residue representations and improve predictive accuracy. When both the semantic alignment and contextual aggregator module are simultaneously removed (“w/o SA & CA”), the model suffers further performance degradation. This reinforces the complementary contributions of these two components, highlighting that both are indispensable for capturing complex residue dependencies within the denoising network. Lastly, we explore the role of the Cell module within the Message Passing part, which integrates node and edge representations from neighboring nodes. When the Cell module is replaced with a MLP, model performance declines, indicating the crucial role of the Cell module in effectively integrating neighboring node and edge representations.