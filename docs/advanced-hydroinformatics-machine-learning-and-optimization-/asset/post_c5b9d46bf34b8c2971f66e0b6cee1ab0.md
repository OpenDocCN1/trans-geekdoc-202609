
**Table 8.1** Potential evapotranspiration-elevation relationships.

| Month | Regression equation y = Pₑ (mm), x = elevation (m) |
|---|---|
| January | y = −7E−06x² − 0.0170x + 152.95 |
| February | y = −8E−06x² − 0.0164x + 156.04 |
| March | y = −1E−05x² − 0.0171x + 190.42 |
| April | y = −9E−06x² − 0.0202x + 194.52 |
| May | y = −7E−06x² − 0.0237x + 186.89 |
| June | y = −7E−06x² − 0.0181x + 165.79 |
| July | y = −9E−06x² − 0.0127x + 175.28 |
| August | y = −8E−06x² − 0.0122x + 170.12 |
| September | y = −8E−06x² − 0.0126x + 150.42 |
| October | y = −1E−05x² − 0.0094x + 149.56 |
| November | y = −9E−06x² − 0.0119x + 142.18 |
| December | y = −7E−06x² − 0.0168x + 144.91 |

*Source:* Adapted from SNET (2005).

Evapotranspiration data are estimated by using an evapotranspiration-elevation relationship shown in Table 8.1. These relationships were determined using the Hargreaves method and linear regression equations. For this study, we train an MLP-ANN Rainfall-Runoff forecast model for the part of the catchment that drains to La Cañoa station, which has an area of 900 km². This station is used for stakeholders and decision makers to monitor the flooding situation.

## 8.4. Methodology

### 8.4.1. Data Exploration

In this study, a Multilayer Perceptron Artificial Neural Network (MLP-ANN) architecture with one hidden layer with a sigmoid function and a linear model as an output layer is used to predict discharge at different lead times in Grande de San Miguel catchment. The first part of the study was related to the data cleansing and exploration. In Data-Driven models this is an important step since any wrong data can generate noise in the models; so the data were reviewed using a MATLAB code to detect outliers and remove erroneous data. The outliers were evaluated to determine whether or not they should be removed for the model training. For instance, if a rainfall intensity of 150 mm/hr was recorded by the gauge, then it was compared with the values of the closest gauges in order to determine if the rainfall intensity should be removed for the analysis or kept in the model building. Thereafter, the rainfall point data were averaged in the catchment using the Inverse Distance Weighting (IDW) method. Furthermore, the water level data set at La Cañoa station was also reviewed to detect spikes, noise, or suspicious values. After this process, all the water level data points were transformed into discharge values using a rating curve equation provided by MARN. Finally, the discharge and rainfall values were aggregated into hourly time steps since the time of concentration of the catchment is in hours.

### 8.4.2. Input Variable Selection

In the second part of the study, a maximum forecast horizon was defined according to the maximum time in which it is possible to predict using observed rainfall and discharge. For this study, an analysis of the physical characteristic of the basin was carried out in order to identify the average response time in the catchment. After this process, an analysis of interdependencies between the rainfall, evapotranspiration, and discharge was done using the correlation coefficient and the average mutual information (AMI). The aim of this process was to estimate which past rainfall (RF), evapotranspiration (ET), and discharge (Q) values have a major influence on the model output. Hence, the main forecast formulation can be represented as follows:

$$
Q_{(t+i)} = f(RF_t, RF_{t-1}, RF_{t-2}, \ldots, RF_{t-L}, Q_t, Q_{t-1}, Q_{t-2}, \ldots, Q_{t-N}, ET_t, ET_{t-1}, ET_{t-2}, \ldots, ET_{t-M}), \tag{8.4}
$$

where the optimal lags L for rainfall, M for potential evapotranspiration, and N for discharge are obtained through model optimization for different forecast lead time (i).

### 8.4.3. Data Partitioning and Model Developing

The available data were partitioned into training, cross-validation, and verification. The aim of the training data set is to reduce the difference between the observed and simulated discharge. This procedure is performed in such a way as to ensure that the maximum and minimum values for each input variable are included in the training data set to reduce possible extrapolation. All the MLP-ANN models for different lead times were trained with the Levenberg-Marquardt optimization algorithm (Levenberg, 1944; Marquardt, 1963) with a learning rate of 0.1, one hidden layer with sigmoid function, and one linear function in the output layer. The ANN-MLP models for different lead times have been optimized using a cross-validation data set, which allows to stop the training process, determine the number of neurons (i.e., nodes) using a trial-and-error optimization, and avoid overfitting (i.e. the model tries to follow all the training data points). Last, the verification data set allows to see how the model would perform with data that it has never seen.

The results of each trained MLP-ANN forecast model for different lead times were evaluated using goodness-of-fit functions and visual inspection analysis between the observed and simulated discharge. The following error functions are used as goodness-of-fit functions between the observed discharge (Q_obs) and the simulated discharge (Q_sim).

#### The Mean Error (ME)

The Mean Error function is calculated using the mean difference between the observed (Q_obs) and simulated discharge (Q_sim). The problem related to this error is that it could display a low value as well as low accuracy and precision.

$$
ME = \frac{\sum (Q_{sim} - Q_{obs})}{n} \tag{8.5}
$$

#### The Nash-Sutcliffe Efficiency (NSE)

The Nash-Sutcliffe efficiency (1970) is defined as one minus the sum of the absolute square difference between the simulated and observed values normalized by the variance of the observed values. The NSE range varies from −∞ to 1 where a value of 1 indicates a perfect reproduction between the observed and simulated discharge. Conversely, if the NSE value is equal or less than 0, it means that the model is not a better predictor than the mean observed discharge (Q̅_obs). In literature, a value larger than 0.6 indicates a satisfactory result of the model performance (Gupta et al., 1998). The major disadvantage of this goodness-of-fit function was stated by Legates and McCabe (1999) and Krause et al. (2005) in which the NSE value overestimates larger values and neglects lower ones.

$$
NSE = 1 - \frac{\sum (Q_{sim} - Q_{obs})^2}{\sum (Q_{obs} - \overline{Q}_{obs})^2} \tag{8.6}
$$

#### The Root Mean Square Error (RMSE)

The Root Mean Square Error (RMSE) is a widely used goodness-of-fit function for verifying hydrological model performance ensures Maximum Likelihood Estimation (MLE). This error function punishes large deviation, which is usually found in high flows but the bias and shape might be not contemplated (Corzo Perez, 2009).

$$
RMSE = \sqrt{\frac{\sum (Q_{sim} - Q_{obs})^2}{n}} \tag{8.7}
$$

#### The Normalized Root Mean Square Error (NRMSE)

The normalized Root Mean Square Error (NRMSE) compares the classical RMSE with the standard deviation of the measurement (σ_obs). This error function can be used to compare different time series (Corzo Perez, 2009).

$$
NRMSE = \frac{RMSE}{\sigma_{obs}} \tag{8.8}
$$

#### The Kling-Gupta Efficiency (KGE)

The Kling-Gupta efficiency (KGE) was proposed by Gupta et al. (2009). It is based on the decomposition of the Nash-Sutcliffe efficiency into three distinctive components representing the linear correlation (r), the variability bias (α), and mean bias (β).

$$
KGE = 1 - \sqrt{(r - 1)^2 + (\alpha - 1)^2 + (\beta - 1)^2} \tag{8.9}
$$

Equation (8.9) can be represented using the following formula:

$$
KGE = 1 - \sqrt{(r - 1)^2 + \left(\frac{\sigma_{sim}}{\sigma_{obs}} - 1\right)^2 + \left(\frac{\mu_{sim}}{\mu_{obs}} - 1\right)^2} \tag{8.10}
$$

where σ_obs is the standard deviation in observations, σ_sim the standard deviation in simulations, μ_sim the simulation mean, and μ_obs the observation mean. Similar to the NSE, a value of KGE equal to 1 indicates a perfect agreement between the observed and simulated discharge.

The MLP-ANN forecast model for different lead times was compared with a naïve reference model, which allows one to benchmark model performance and to evaluate how much a sophisticated forecast model (MLP-ANN) is improving the results based on a simple autoregressive model.
