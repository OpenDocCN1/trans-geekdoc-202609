
4 GW to 19 GW as a result of a sudden change in wind speed [42]. Further, Nissen studies the seasonal variations in wind speed over coastal areas of Hovsore, Denmark, which shows that the wind speed variation is primarily dominant in the spring and winter season [43]. Also, it is found that the wind power ramp events are characterized based on magnitude error, phase error, and location error as pointed out by Potter et al. [44]. Cutler et al. have discussed the MesoLAPS and Wind power prediction tool (WPPT) for analyzing and categorizing large wind power ramp events. The root mean squared error (RMSE) is evaluated over a period of one year for two wind speed time series with 5-min and 10-min sampling intervals [45].

Results reveal that the RMSE values are found to be more optimistic than conventional persistence and climatology methods. Cornejo-Bueno et al. [46] have described the machine learning techniques like support vector regression (SVR), Gaussian process regression (GPR), multilayer perceptrons (MLPs), and extreme learning machines (ELMs) to forecast wind power ramp events. Experimental analysis is carried out for three wind farms, and results reveal that GPR–based regression yields better ramp forecasts for a time interval of 6 h.

## 7.3.1 Case study for onshore and offshore wind farms

In this section, we discuss the forecasting performance of the prediction models (persistence, ε-SVR, LSSVR, TSVR, ε-TSVR, RFR, and GBM). The ramp-up and ramp-down events are identified for a threshold of 10% of nominal wind power. The forecasting process is carried out by splitting the entire dataset into training (80%) and testing (20%) sets. For the persistence model, the forecast is carried out using two previous dispatch windows. Further, for SVR and its variants, the hyperparameters, that is, RBF bandwidth σ and regularization parameter C are tuned from the set [2^-10, 2^-9, ..., 2^9, 2^10]. For random forest regression (RFR) and gradient boosted machines (GBM), the simulations are carried out in R studio using random forest package. The number of trees used in training phase are 1000 for RFR, whereas for GBM, the learning rate is kept at 0.05, and the number of trees is 10000. The input feature set to all the prediction models is a matrix consisting of approximation signal A5 and detail signals (D1, D2, ..., D5) obtained from wavelet decomposition of wind speed time series. Further, we evaluate the absolute error for ramp-up and ramp-down events as R^up and R^down, respectively. Table 7.3 depicts the mean and standard deviation (SD) for the onshore and offshore wind speed datasets.

| Onshore wind farm | Site coordinates | Mean | SD |
| --- | --- | --- | --- |
| Amakhala Emoyeni, SA (a) | −32.17° N, 25.95° E | 6.264 | 3.198 |
| Clyde, Scotland (b) | 55.46° N, 03.65° W | 3.829 | 1.626 |
| Gansu, China (c) | 40.20° N, 96.90° E | 4.000 | 2.477 |
| McCain Foods, UK (d) | 52.56° N, 0.172° W | 6.491 | 3.519 |
| Shepherds Flat, USA (e) | 45.70° N, 120.06° W | 6.074 | 2.618 |
| Akhfenir, Morocco (f) | 27.95° N, 12.00° W | 3.096 | 1.505 |

| Offshore wind farm | Site coordinates | Mean | SD |
| --- | --- | --- | --- |
| Amrumbank, Germany (Aa) | 54.50° N, 7.80° E | 11.176 | 4.962 |
| Anholt, Denmark (Bb) | 56.60° N, 11.21° E | 8.999 | 3.537 |
| Gemini, Netherlands (Cc) | 54.03° N, 5.96° E | 7.577 | 4.174 |
| HornsRev 2, Denmark (Dd) | 55.60° N, 7.59° E | 11.183 | 4.546 |
| Veja Mate, Germany (Ee) | 54.31° N, 5.87° E | 11.490 | 4.685 |
| Walney, UK (Ff) | 54.04° N, 5.92° W | 11.342 | 5.015 |

For onshore wind farm sites, the datasets labeled are **a**, **b**, **c**, **d**, **e**, and **f**. For dataset **a**, GBM outperforms all the prediction models in terms of RMSE and NMSE. For predicting ramp-up and ramp-down events, TSVR outperforms GBM and RFR. In terms of $R^2$, TSVR gives the best fit close to 1.00, whereas $\varepsilon$-SVR gives a value greater than 1.00 causing over-fitting. The over-fitting in prediction is avoided by using RFR and GBM. Figs. 7.10–7.12 illustrate scatter plots for the different onshore datasets.

Similarly, for offshore wind farm datasets (**Aa**, **Bb**, **Cc**, **Dd**, **Ee** & **Ff**), Figs. 7.13–7.15 illustrate scatter plots.

TSVR outperforms all the models in terms of RMSE and NMSE for predicting wind speed, whereas for predicting ramp events, TSVR gives the best result in terms of $R^2$. Further, since the datasets are large sized, TSVR, $\varepsilon$-TSVR, RFR, and GBM take less computation time than conventional $\varepsilon$-SVR. The detailed performance metrics for onshore wind farm sites are depicted in Tables 7.4, 7.5, and 7.6.

Among different regressors, TSVR gives a minimum prediction error for ramp-up and ramp-down events for datasets **c** and **d**. In terms of RMSE, for dataset **c**, TSVR outperforms $\varepsilon$-TSVR, LSSVR, RFR, and GBM by 85%, 84.2%, 98.3%, and 97.6%, respectively.

From the performance metrics of the onshore wind sites we can observe that the decision tree ensemble methods like random forest and gradient boosted machines result in significantly lower RMSE and NMSE than supervised machine learning models. For example, for dataset **a**, ε-SVR

![](img/b53e39e35231af65df8ccaa99eb28bee_139_0.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_1.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_2.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_3.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_4.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_5.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_6.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_7.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_8.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_9.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_10.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_11.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_12.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_139_13.png)
Figure 7.10 Scatter plots for onshore wind farm sites: Datasets a and b.

![](img/b53e39e35231af65df8ccaa99eb28bee_140_0.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_140_1.png)
Figure 7.11 Scatter plots for onshore wind farm sites: Datasets c and d.

![](img/b53e39e35231af65df8ccaa99eb28bee_141_0.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_141_1.png)

![](img/b53e39e35231af65df8ccaa99eb28bee_142_0.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_142_1.png)

![](img/b53e39e35231af65df8ccaa99eb28bee_143_0.png)
Figure 7.14 Scatter plots for offshore wind farm sites: Datasets Cc and Dd.

![](img/b53e39e35231af65df8ccaa99eb28bee_144_0.png)
![](img/b53e39e35231af65df8ccaa99eb28bee_144_1.png)
Figure 7.15 Scatter plots for offshore wind farm sites: Datasets Ee and Ff.

## Table 7.4 Performance metrics of ramp prediction models (Onshore sites).

| Dataset | Model | RMSE U2 | NMSE Rup | R2 Rdown | U1 CPU time |
| --- | --- | --- | --- | --- | --- |
| a | LSSVR | 0.3602 | 0.0177 | 0.9856 | 0.0024 |
| | | 0.5678 | 0.0236 | NA | 1.46082 |
| | TSVR | 0.3525 | 0.0177 | 0.9899 | 0.0001 |
| | | 0.0519 | 0.0016 | NA | 57.41689 |
| | ε-TSVR | 0.3475 | 0.0178 | 0.9701 | 0.0046 |
| | | 0.6538 | 0.0036 | NA | 7.3946 |
| | RFR | 0.3436 | 0.1251 | 0.9506 | 0.5633 |
| | | 0.6276 | 0.0789 | NA | 4.2693 |
| | GBM | 0.1197 | 0.0044 | 0.9705 | 0.0115 |
| | | 0.1539 | 0.0043 | NA | 0.7119 |
| | Persistence | 0.4399 | 0.0221 | 1.0145 | 0.0259 |
| | | 0.6296 | 0.2800 | NA | 0.02545 |
| | ε-SVR | 0.3620 | 0.0178 | 1.0004 | 0.0029 |
| | | 6.6035 | 0.0862 | NA | 238.8274 |
| b | LSSVR | 0.0403 | 0.00057 | 0.9748 | 0.0044 |
| | | 0.5716 | 0.1169 | 0.1498 | 0.76059 |
| | TSVR | 0.0268 | 0.0002 | 0.9832 | 0.0029 |
| | | 0.444 | 0.0881 | 0.1228 | 23.9192 |
| | ε-TSVR | 0.0486 | 0.0008 | 0.9758 | 0.0053 |
| | | 0.6978 | 0.1098 | 0.1332 | 3.3806 |
| | RFR | 0.06991 | 0.00121 | 0.9730 | 0.0660 |
| | | 0.7191 | 0.1112 | 0.1421 | 32.11 |
| | GBM | 0.0651 | 0.0017 | 0.9986 | 0.0078 |
| | | 0.0219 | 0.0235 | 0.0307 | 45.93 |
| | Persistence | 0.4399 | 0.0108 | 1.0068 | 0.0190 |
| | | 0.6429 | 0.2350 | 0.2000 | 0.04356 |
| | ε-SVR | 0.0593 | 0.0013 | 0.9556 | 0.0065 |
| | | 0.6517 | 0.1876 | 0.2367 | 84.4812 |

model gives an R2 value greater than 1, which suggests overfitting when performed on an unseen data. The problem of overfitting as discussed in Chapter 5 can be eliminated by using a boosting algorithm like XBoost. Also it is worth noting that the error in predicting ramp-down event is greater than that in predicting ramp-up event. This observation remains true for most of the datasets.

Consider dataset Aa. The RMSE value is minimum for ε-TSVR followed by TSVR and LSSVR. The decision tree ensemble methods give a
