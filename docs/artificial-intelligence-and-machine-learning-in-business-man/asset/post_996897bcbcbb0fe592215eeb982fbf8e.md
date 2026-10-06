
## Recurrent Neural Network-Based Long Short-Term Memory

![](img/9665bc5b38d724f414bf1c78dda7410a_235_0.png)

**FIGURE 13.2** (i). deep learning-based model (LSTM) predicting nearly the actual trends for Australian Dollar (AUD) data set.

![](img/9665bc5b38d724f414bf1c78dda7410a_235_1.png)

**FIGURE 13.3** (ii). deep learning-based model (LSTM) predicting nearly the actual trends for British Pound (GBP) data set.

LSTM deep neural network model for five different currencies exchange datasets. It can also be observed clearly from Figure 13.2 that deep learning based model (LSTM) predicting nearly the actual trends for all five forex data sets.

deep learning-based model (LSTM) predicting nearly the actual trends for Australian Dollar (AUD) data set is shown below in Figure 13.2 (i).

deep learning-based model (LSTM) predicting nearly the actual trends for British Pound (GBP) data set is shown below in Figure 13.3 (ii).

deep learning-based model (LSTM) predicting nearly the actual trends for Canadian Dollar (CAD) data set is shown below in Figure 13.4 (iii).

## 216 Artificial Intelligence and Machine Learning in Business Management

![](img/9665bc5b38d724f414bf1c78dda7410a_236_0.png)

**FIGURE 13.4** (iii) Deep learning-based model (LSTM) predicting nearly the actual trends for Canadian Dollar (CAD) data set.

![](img/9665bc5b38d724f414bf1c78dda7410a_236_1.png)

**FIGURE 13.5** (iv) deep learning-based model (LSTM) predicting nearly the actual trends for Indian Rupee (INR) data set.

Deep learning-based model (LSTM) predicting nearly the actual trends for Indian Rupee (INR) data set is shown below in Figures 13.5 (iv) and 13.6 (v).

Figure 13.2 Training and testing observations of LSTM model for one day prediction for five different currencies: i) Australian Dollar (AUD) ii British Pound (GBP) iii Canadian Dollar (CAD) iv Indian Rupee (INR) and v Japanese Yen (JPY)

The MSE convergence plot of one day prediction using all the three models BPNN, FLANN, and LSTM for the Australian Dollar (AUD) forex data set is shown below in Figure 13.7 (i).

The MSE convergence plot of one day prediction using all the three models BPNN, FLANN, and LSTM for the British Pound (GBP) forex data set is shown below in Figure 13.8 (ii).

## Recurrent Neural Network-Based Long Short-Term Memory 217

![](img/9665bc5b38d724f414bf1c78dda7410a_237_0.png)

**FIGURE 13.6** (v). deep learning-based model (LSTM) predicting nearly the actual trends for Japanese Yen (JPY) data set.

![](img/9665bc5b38d724f414bf1c78dda7410a_237_1.png)

**FIGURE 13.7** (i) The MSE convergence plot of one day ahead prediction using the three models BPNN, FLANN and LSTM for the Australian Dollar (AUD) forex data set.

The MSE convergence plot of one day ahead prediction using all the three models BPNN, FLANN, and LSTM for the Canadian Dollar (CAD) forex data set is shown below in Figure 13.9 (iii).

The MSE convergence plot of one day ahead prediction using all the three models BPNN, FLANN, and LSTM for the Indian Rupee (INR) forex data set is shown below in Figure 13.10 (iv).

The MSE convergence plot of one day ahead prediction using all the three models BPNN, FLANN, and LSTM for the Japanese Yen (JPY) forex data set is shown below in Figure 13.11 (v).

## Artificial Intelligence and Machine Learning in Business Management

![](img/9665bc5b38d724f414bf1c78dda7410a_238_0.png)

**FIGURE 13.8** (ii). The MSE convergence plot of one day ahead prediction using the three models BPNN, FLANN and LSTM for the British Pound (GBP) forex data set.

![](img/9665bc5b38d724f414bf1c78dda7410a_238_1.png)

**FIGURE 13.9** (iii). The MSE convergence plot of one day ahead prediction using all the three models BPNN, FLANN and LSTM for the Canadian Dollar (CAD) forex data set.

13.3 MSE convergence plots obtained using three forecasting models (BPNN, FLANN and LSTM) of 1 day ahead prediction for five different currencies: i) Australian Dollar (AUD) ii British Pound (GBP) iii Canadian Dollar (CAD) iv Indian Rupee (INR) and v) Japanese Yen (JPY).

During training phase of the proposed model, Figure 13.3 was obtained. These figures are the MSE convergence plot of one day ahead prediction using all the models BPNN, FLANN and LSTM for the same different data sets and it reveals that deep learning neural network converges faster with minimum errors than the other two neural models used in this study.

## Recurrent Neural Network-Based Long Short-Term Memory

![](img/9665bc5b38d724f414bf1c78dda7410a_239_0.png)

**FIGURE 13.10** (iv). The MSE convergence plot of one day prediction using all the three models BPNN, FLANN and LSTM for the Indian Rupee (INR) data set.

![](img/9665bc5b38d724f414bf1c78dda7410a_239_1.png)

**FIGURE 13.11** (v). The MSE convergence plot of one day prediction using all the three models BPNN, FLANN and LSTM for the same different set Japanese Yen (JPY).

## 13.6 CONCLUSION

This paper describes the implementation of special type of RNN, Long-Term Memory network for the exchange rate forecasting in details. Due to its distinct features, gated input and output and memory block LSTM model is performing well in time series prediction. Gates are responsible for the selection of data, removal of data and modification of the block. These gates work as memory cell by storing previous values and compare them with upcoming variance to update the model by observing the input patterns. From simulation made in Section 4, it clearly observed that the proposed deep learning network-based LSTM model giving better accuracy in different horizons from 1 day ahead to 30 days ahead as well as it is faster than the other widely accepted neural network models (i.e., BPNN and FLANN). From the results we also discovered that error is increasing for long horizon. So, to improve the accuracy of the models in long term, we need to introduce inflating factors, more statistical features and technical indicators. The prediction accuracy may also be enhanced by exploring other variants of deep neural network models.

## REFERENCES

- 1. Taylor, S. J. (1987). Forecasting the volatility of currency rates. International Journal of Forecasting, 3(1), 159–170.
- 2. Kamruzzaman, J., Sarker, R. A., & Ahmad, I. (2003, November). SVM models for predicting currency rates. In Third International Conference on Data Mining (pp. 557–560).
- 3. Nagarajan, W., Wu, Y., Li, M., & Wang, Q. (2005, June). Forecast studies for financial markets using technical analysis. In 2005 International Conference on Control and Automation (Vol. 1, pp. 259–264).
- 4. Galeshuk, S. (2016). Neural networks performance in exchange rate prediction. Neurocomputing, 172, 446–453.
- 5. Huang, W., Lu, S., Bao, Y., & Wang, L. (2006). Comparisons of the different frequencies of input data for neural networks in foreign exchange rates forecasting. In International Conference on Computational Science (pp. 517–524). Springer, Berlin, Heidelberg.
- 6. Bui, L. T., & D, T. T. H. (2018). A new evolutionary multi-objective learning approach for forecasting currency exchange rates. Data & Knowledge Engineering, 114, 40–66.
- 7. He, K., Ji, L., To, G. K., Zhu, B., & Zou, Y. (2018). Forecasting Exchange Rate Value at Risk using Deep Belief Network Ensemble approach. Procedia computer science, 139, 25–32.
- 8. Ni, H., & Yin, H. (2009). Exchange rate prediction using hybrid neural networks and trading indicators. 72(13-15), 2815–2823.
- 9. Andreou, A. S., Georgopoulos, E. F., & Likothanos, S. D. (2002). Exchange-forecasting: A hybrid algorithm on genetically optimized neural networks. Computational Economics, 20(3), 191–210.
- 10. Jena, P. R., Majhi, R., & Majhi, B. (2015). Development and performance evaluation of a novel knowledge guarded artificial neural network (KGANN) for exchange rate prediction. Journal of King Saud University-Computer and Information Sciences, 27(4), 450–457.
- 11. Rehman, M., Khan, G. M., & Mahmud, S. A. (2014). Foreign currency exchange rates prediction using cgg and recurrent neural network. IERI Proceedings, 10, 239–244.
- 12. Chao, J., Shen, F., & Zhao, J. (2011, July). Forecasting exchange rate with deep neural networks. In The 2011 International Joint Conference on Neural Networks (pp. 1259–1266). IEEE.
- 13. Shen, F., Chao, J., & Zhao, J. (2015). Forecasting exchange rate using deep belief works and conjugate gradient method. Neurocomputing, 167, 243–253.
