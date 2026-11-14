| Model | RMSE | MSE | \( R^2 \) | NMSE | U1 | U2 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| \(\epsilon\)-SVR | 13.63 | 185.77 | 1.099 | 0.0201 | 0.004 | 0.2017 |
| Persistence | 35.12 | 1233.41 | 7.6129 | 6.8104 | 0.0749 | 0.5517 |

SVR. Continuous ACO is used to optimize \(\sigma\), \( C \), and \(\varepsilon \), and the forecasting results are compared with seasonal ARIMA (S-ARIMA) model. The traffic flow data for the city of Panchiao, Taiwan, are segmented into training and testing data for morning and evening peak hours. In terms of normalized RMSE, CACO-SVR model outperforms S-ARIMA model. Due to better SVR generalization capability and added advantage of parameter optimization, the model holds an upper edge over S-ARIMA. Sales growth forecasting is studied by Wang et al. [10] utilizing improved PSO (IPSO) based SVR method. To assess accuracy of the proposed IPSO-SVR model, it is tested against benchmark models like multiple regression model, back propagation neural network, and direct regression model, and results reveal that IPSO-SVR outperforms all other methods. Overall, hybrid SVR models involving parameter search algorithms are used extensively for real-time forecasting problems. The supervised learning approach significantly improves forecast performance.

# Stock price prediction: a case study

Next, we discuss the opening stock price prediction for L&T Infotech keeping the highest price, lowest price, and closing price for a particular day as predictor variables. Daily data for two years are taken from August 21, 2017, to August 20, 2019. A total of 492 samples are segmented into training (400) and testing (92) sets. The hyperparameters are tuned in the range of \( 2^{-10} - 2^{10} \) for SVR model. The results from Table 4.1 indicate that SVR model outperforms the persistence model in terms of RMSE and \( R^2 \) value. Here the problem of overfitting persists, which can be potentially eliminated by using better versions of SVR models discussed in the next section. Fig. 4.5 illustrates the prediction of opening stock prices for both models.

# 4.3 Least-square support vector regression

Least-square support vector regression (LSSVR) is originally derived from least-square support vector classifiers (LSSVC) proposed in [11], where