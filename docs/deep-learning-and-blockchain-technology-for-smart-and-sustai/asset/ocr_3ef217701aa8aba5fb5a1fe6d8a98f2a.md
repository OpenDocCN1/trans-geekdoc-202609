| Model | R2 Score | MAE | RMSE | Computation Time (Seconds) |
|---|---|---|---|---|
| RNN | 0.9037 | 32.5071 | 47.1041 | 42.7279 |
| LSTM | 0.9185 | 33.5863 | 43.208 | 44.6122 |
| GRU | 0.9213 | 32.0499 | 42.5716 | 30.2707 |
| Stacked LSTM | 0.9389 | 28.2051 | 37.5179 | 38.1415 |
| LSTM+RNN | 0.9286 | 31.7077 | 40.5503 | 44.5576 |
| RNN+GRU | 0.9349 | 30.4267 | 38.7052 | 27.1417 |
| **Proposed LSTM+GRU** | **0.9446** | **21.8368** | **35.7074** | **23.2089** |

This section compares the suggested hybrid model's assessment metrics to those of other DL models. Any model implementation process must include evaluation, which also makes it possible to choose the best model from a variety of options based on performance outcomes. Four criteria are used in this research to undertake an evaluation and relative assessment of the efficiency of various models. The computations were completed by comparing the actual value to the predicted results. The proposed hybrid model LSTM+GRU outperforms other individual and hybrid models in terms of prediction accuracy and error rate, as shown in Table 13.5.

Therefore, it makes sense to believe that the suggested model is suitable for projecting data about air quality. Based on the experimental results, we suggest a hybrid LSTM+GRU model that outperforms a single LSTM model in this circumstance. In comparison with alternative models, certain criteria yield fewer desirable results. The suggested model's outcome is contrasted with the outcomes of the other current methodologies, and the related comparison analysis is presented in Table 13.5.

# 13.5 Conclusion and Future Scope

The study concludes by showcasing the potential benefits of the hybrid models using DL for ambient AQI predictions in sustainable and smart cities. Through the use of a unified framework that combines RNNs, LSTM networks, CNNs,