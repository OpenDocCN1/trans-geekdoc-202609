# Simple RNN

# GRU

# LSTM

![](bbox=[0.075, 0.075, 0.345, 0.222])

![](bbox=[0.365, 0.075, 0.635, 0.222])

![](bbox=[0.655, 0.075, 0.925, 0.222])

# TCN

# VNET

# Transformer

![](bbox=[0.075, 0.258, 0.345, 0.405])

![](bbox=[0.365, 0.258, 0.635, 0.405])

![](bbox=[0.655, 0.258, 0.925, 0.405])

Fig. 4. Band-LSTM Graphs for Multi-Patient Analysis in All Models. The x axis shows the mean of the predicted true value and the y axis shows difference for each time instance. The mean difference (diff) as evaluated (as ± 1.6 SD or standard deviation) for each model.

# Table 5
ablation results for multi-patient analysis.

| Ablation | Simple Loss (ms) | GRU Test MAE (ms) | LSTM Test MAE (ms) | TCN Test MAE (ms) | VNET Test MAE (ms) | Transformer Test MAE (ms) |
|---|---|---|---|---|---||}{
| ABP | | 8.23 | 7.51 | | 8.11 | 5.42 | 8.46 |
| PPG | | 6.84 | 7.20 | 7.23 | 5.14 | 5.24 | 7.31 |
| ECG | | 6.79 | 6.72 | 6.54 | 5.28 | 7.33 |
| ABP + PPG | | 6.32 | 6.32 | 5.77 | 5.45 | 5.17 | 7.41 |
| ABP + ECG | | 5.91 | 5.78 | 5.66 | 5.36 | 5.32 | 6.36 |
| PPG + ECG | | 5.14 | 5.18 | 5.20 | 4.98 | 5.05 | |
| ECG | | | | | | |

The test results obtained from subsets of waves (evaluated by the MAE test set in pooling, ABP + PPG + ECG) is the benchmark of using waveforms to preprocess ICD.

they are invasive, requiring surgical performance
We conducted a methodological analysis of a range of deep learning algorithms applied to time-series. Understanding the differences in predictions obtained when using distinct models could provide insights into the clinical and technical components of each model. However, the performance of Simple RNN, GRU, TCN, and VNET varies, including the data representation set. Transformers are particularly effective when there is a clear signal in the data, such as in image or language processing tasks. They capture distant elements, enabling them to model both long-term and temporal dependencies across various domains. However, this complex architecture may be harder to extract or encode long-term dependencies due to the vanishing gradient problem. The architectures of TCN, GRU, VNET, and the other, are designed to address these issues, making them more suitable for the task at hand.

contrast, TCN leverages convolutions to efficiently capture long-range dependencies within sequential data, which may explain their higher correlations with GRU, LSTM, and VNET. However, TCN's ability to perform on multi-scale models is a challenge; attention mechanisms may help capture temporal dependencies within the extracellular and ICD physiological waves. By using a range of deep learning models, we found that different models have strengths in both types of temporal information embedded within extracellular and ICD physiological waves, as well as each model's capacity for leveraging and searching for precise predictions. Our results provide insight into the variability of model for application. For instance, RNN, GRU, and VNET exhibited a smaller MAE for PPG + ECG. Whereas, LSTM and Transformer showed better performance for ABP + ECG data. When evaluating these models independently, identify their divergent dependencies in ABP + ECG versus PPG + ECG. This suggests that the combined information from all three extrac waves may compensate for the architectural differences between deep learning models, resulting in similar performance in