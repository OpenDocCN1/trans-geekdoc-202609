
Prediction capability was evaluated using different performance measures such as Mean Absolute Error (MAE), Root Mean Square Error (RMSE), and Pearson Correlation Coefficient (CC). [Table 6](#Ch006_107-168_S0169716122000578.xhtml#t0035) summarizes the result of two data-driven approaches, i.e., support vector machine (SVM), extreme learning machines (ELM), and four modes of LSTMs with respect to different performance measures.

[Table 6](#Ch006_107-168_S0169716122000578.xhtml#B-t0035)

Summary of MAE, RMSE and CC for predicted vs observed wind speed for stations at New Delhi and Bengaluru. 

|  || New Delhi || Bengaluru |

| --- | --- | --- |

| Measures || MAE || RMSE || CC || MAE || RMSE || CC |

| SVM || 0.824 || 1.091 || 0.510 || 1.757 || 2.287 || 0.614 |

| --- | --- | --- | --- | --- | --- | --- |

| ELM || 0.773 || 1.027 || 0.547 || 0.919 || 1.173 || 0.651 |

| LSTM1 || 0.179 || 0.210 || 0.044 || 0.154 || 0.189 || 0.167 |

| LSTM2 || 0.100 || 0.128 || 0.100 || 0.136 || 0.161 || 0.170 |

| LSTM3 || 0.078 || 0.107 || 0.489 || 0.133 || 0.160 || 0.716 |

| LSTM4 || 0.077 || 0.105 || 0.585 || 0.129 || 0.156 || 0.760 |

Among all the LSTMs, LSTM3 and LSTM4 which are ensemble-based method, perform better than non-ensemble LSTMs in terms of low MAE, RMSE and high correlation coefficient for both New Delhi and Bengaluru stations.

Plotting of total 15,456 data points in a single graph for all the models creates a huddle for managing a such huge number of data points. Therefore, the prediction capability of time division LSTM compared to the data-driven model is depicted in [Figs. 13](#Ch006_107-168_S0169716122000578.xhtml#f0070) and [14](#Ch006_107-168_S0169716122000578.xhtml#f0075) on a small dataset of 192 timesteps from 1st February 2014.

```
if (condVar > someVal) {console.log("xxx")}
```

[Fig. 13](#Ch006_107-168_S0169716122000578.xhtml#B-f0070) Comparison between model simulated (SVM, ELM, and Time division LSTM) and observed half-hourly wind speed (m/s) at New Delhi station for the period 1st February to 4th February 2014.

![Fig. 13 Comparison between model simulated (SVM, ELM, and Time division LSTM) and observed half-hourly wind speed (m/s) at New Delhi station for the period 1st February to 4th February 2014.](images/S0169716122000578/f06-13-9780443184307.jpg)

[Fig. 13](#Ch006_107-168_S0169716122000578.xhtml#B-f0070) Comparison between model simulated (SVM, ELM, and Time division LSTM) and observed half-hourly wind speed (m/s) at New Delhi station for the period 1st February to 4th February 2014.

![Fig. 14 Comparison between model simulated (SVM, ELM, and Time division LSTM) and observed half-hourly wind speed (m/s) at Bengaluru station for the period 1st February to 4th February 2014.](images/S0169716122000578/f06-14-9780443184307.jpg)

[Fig. 14](#Ch006_107-168_S0169716122000578.xhtml#B-f0075) Comparison between model simulated (SVM, ELM, and Time division LSTM) and observed half-hourly wind speed (m/s) at Bengaluru station for the period 1st February to 4th February 2014.

As shown in [Figs. 13](#Ch006_107-168_S0169716122000578.xhtml#f0070) and [14](#Ch006_107-168_S0169716122000578.xhtml#f0075), the ensemble method performs better than the SVM and ELM models and their performance is slightly disparaged at both locations. However, none of them could predict lower wind speed satisfactorily.

As shown in [Figs. 15](#Ch006_107-168_S0169716122000578.xhtml#f0080) and [16](#Ch006_107-168_S0169716122000578.xhtml#f0085), a unit line is drawn in the scatter plot between observed and predicted wind speed in both locations to depict the model performs better way with more clarity on bias and the extent of errors.

![Fig. 15 Scatter plot shows the comparison between the observed and predicted wind speed (m/s) from various models ((A) AR, (B) SVM, (C) ELM (D) Time Division LSTM) at New Delhi during the study period.](images/S0169716122000578/f06-15-9780443184307.jpg)

[Fig. 15](#Ch006_107-168_S0169716122000578.xhtml#B-f0080) Scatter plot shows the comparison between the observed and predicted wind speed (m/s) from various models ((A) AR, (B) SVM, (C) ELM (D) Time Division LSTM) at New Delhi during the study period.

![Fig. 16 Scatter plot shows the comparison between the observed and predicted wind speed (m/s) from various models ((A) AR, (B) SVM, (C) ELM (D) Time Division LSTM) at Bengaluru during the study period.](images/S0169716122000578/f06-16-9780443184307.jpg)

[Fig. 16](#Ch006_107-168_S0169716122000578.xhtml#B-f0085) Scatter plot shows the comparison between the observed and predicted wind speed (m/s) from various models ((A) AR, (B) SVM, (C) ELM (D) Time Division LSTM) at Bengaluru during the study period.

From the scatter plot for New Delhi presented in [Fig. 15](#Ch006_107-168_S0169716122000578.xhtml#f0080), it can be seen that all four models are comparable and have a slight positive bias for wind prediction. However, the data-driven models (SVM and ELM) are unable to predict low wind speed.

For the Bengaluru location as depicted in [Fig. 16](#Ch006_107-168_S0169716122000578.xhtml#f0085), it is observed that there is a large negative bias for the AR method. Both the data-driven models and time division LSTM shows better performance compared to statistical models. SVM could predict high wind speed, i.e., greater than 6 m/s, but unable to predict very low wind speed, i.e., lesser than 1 m/s. ELM is successful in predicting medium wind speed but is unable to predict high and low wind speeds. Time division LSTM (LSTM4) could predict all categories except the very high wind speed of more than 7 m/s.

###  3.6: Application of LSTM for the estimation of crop production

Adequate crop production helps in assuring the food requirements of a country and creates a foreign exchange. Reliable prediction of crop production in advance helps policymakers to decide on trading that makes value addition to food security. Thus, there is a need for a robust and accurate model to predict the crop production of a country in advance. An attempt is made to design an AI model for predicting the rice production of India by feeding input as rice production of neighboring Asian countries that are part of the South Asian Monsson system and rainfall of India. The result depicts that prediction capability for future years is improvised by the joint effort of local and regional scale parameters. Import-export crop production data of India and neighboring counties are used to validate the capability of this predictive model ([Marndi et al., 2021](#Ch006_107-168_S0169716122000578.xhtml#bb0245)).

As LSTM is efficient in handling time series data, Stack LSTM is used for designing a sensitive analysis model to identify the correct input set for a predictive model for predicting rice production in India.

####  3.6.1: Automated model for selection of optimal input data set for designing crop prediction model

India's rice production may not be affected by the rice production of all neighboring countries although the influences from rice production of some of the countries are significant. The accuracy of an AI-based predictive model depends hugely on the proper input data set. An automated model has been designed to identify the right input for designing a more accurate predictive model by performing mathematical combinations.

As shown in [Table 7](#Ch006_107-168_S0169716122000578.xhtml#t0040), all possible combinations, i.e., 2^(20)–22 of rice production from 20 neighboring countries rice production are computed. It is very complex and computationally intensive for identifying the best combination from a total of 2^(20)–22, no. of combinations. The detailed procedure to determine the optimal input set is depicted below:

[Table 7](#Ch006_107-168_S0169716122000578.xhtml#B-t0040)

Different mathematical combinations of rice production of different Asian countries.

| ^(20)C[2] = 190 || ^(20)C[8] = 125,970 || ^(20)C[14] = 38,760 |

| --- | --- | --- |

| ^(20)C[3] = 1140 || ^(20)C[9] = 167,960 || ^(20)C[15] = 15,504 |

| --- | --- | --- |

| ^(20)C[4] = 4845 || ^(20)C[10] = 184,756 || ^(20)C[16] = 4845 |

| ^(20)C[5] = 15,504 || ^(20)C[11] = 167,960 || ^(20)C[17] = 1140 |

| ^(20)C[6] = 38,760 || ^(20)C[12] = 125,970 || ^(20)C[18] = 190 |
