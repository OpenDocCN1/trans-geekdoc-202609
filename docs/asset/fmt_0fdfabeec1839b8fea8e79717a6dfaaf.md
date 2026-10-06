
# Long short-term memory (LSTM) has a structure that uses the output obtained in the previous step as the input of the current step and organizes the flow of information by keeping it in memory for a short time. It is frequently used in modeling and forecasting time series. This method has achieved high success in estimating nonlinear data. In recent years, the method has been often preferred in hydrology for future predictions (Baykal et al., 2023; Latifoğlu & Nuralan, 2020; Swagatika et al., 2024). Xu et al. (2024) stated that the Cauchy mutation and adaptive weight factor (CABES) method increased the success of LSTM in estimating annual flow values of Xiajiang hydrological station in the Ganjiang River Basin, China. Kadam et al. (2024) made a drought assessment with 6-month SPI values using recurrent neural network, gated recurrent unit (GRU), and LSTM deep learning methods for the Marathwada region in India. They stated that the model based on LSTM with 6-month SPI is the most successful model for the region. Li, Liu et al. (2024) used LSTM, GRU, and temporal convolutional network deep learning methods to predict the level changes of Polang Lake, located in the middle parts of the Yangtze River in China. They preferred Bayesian model average and Monte Carlo methods to increase the prediction accuracy of the models and stated that GRU gave the best estimations. Li, Shu et al. (2024) compared LSTM and `bidirectional long short-term memory (BiLSTM)` methods in a different study for Polang Lake level prediction. While both methods were found to be successful in short-term forecasts, BiLSTM was found to be more successful in long-term forecasts.

In this study, the effects of meteorological droughts on Eğirdir Lake water level changes, that is, hydrological drought, were examined with ML algorithms. For this purpose, firstly, SPI series were calculated for meteorological drought in a 12-month period using precipitation data between 1976 and 2019 from Eğirdir, Senirkent, Uluborlu, Yalvaç, and Isparta meteorological stations. ML models were developed to estimate the water level of Eğirdir Lake with only SPI values during dry periods as input. Then, the next 10-year (2020–30) SPI values of each station were estimated with LSTM and the possible change of Eğirdir Lake water level was examined with the most appropriate ML model selected. When analyzing the existing studies in the literature, it was seen that ML studies on the prediction of lake water level from meteorological drought were limited. In addition, estimating lake levels using only the dry periods of the SPI series and forecasting possible level changes with LSTM also reveal the novelty of the study.

## 12.2. Materials and methods

### 12.2.1 Study region

Lake Eğirdir is the second largest freshwater lake in Turkey, located within the borders of Isparta Province, formed by tectonic and karst effects. It is located between 35°37′41″ and 38°16′55″ northern latitudes and 30°44′39″ and 30°57′43″ eastern longitudes (Fig. 12–1). The lake, which has steep rocks and a flat and shallow bottom, has a shoreline length of 150 km. Another of the most important features of Lake Eğirdir is its connection with the sea. The waters coming to Kovada Lake through the 22 km Kovada canal were discharged from the Kovada Valley to Aksu Stream and from there to the Mediterranean via karst paths. For the last 20 years, the waters of the lake have been flowing to the Karacaören I and II Dams built in the Çandır Plain.

![Figure 12–1 The study region. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000055f12-01-9780443219054.jpg)

Figure 12–1 The study region. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

The most important water inputs feeding the lake are the springs from the bottom of the lake. At the same time, there are many large and small streams and streams descending from the surrounding mountains and fed by rainwater. The most important of these are the Pupa Stream, which comes from Yalvaç district and flows into the lake from Gelendost district, passing through Akçay, Uluborlu and Senirkent districts, Değirmen Stream descending from Hoyran Plain, and Aksu Stream, which connects to the lake with a channel from Aksu Stream. Eğirdir Lake meets the drinking water needs of Isparta province and surrounding settlements. It is also used as irrigation water in the plains of Isparta, Gönen, Uluborlu, Senirkent, Yalvaç, Gelendost, and Eğirdir (URL-1).

### 12.2.2 Standardized precipitation index

SPI is a widely used method developed by McKee et al. (1993) to monitor meteorological drought. Abnormalities in dry or wet events at any time scale in a region can be determined by SPI, which depends on only precipitation parameter. It is the index value (SPI) obtained by dividing the difference of the precipitation value (*X*[*i*]) from the mean (*X*[mean]) for the specified period by the standard deviation (*σ*) (Eq. 12.1).

```
${SPI} = \left( \frac{x_{i}{- x}_{mean}}{\sigma} \right)$<mml:math><mml:mi mathvariant="normal">SPI</mml:mi><mml:mo>=</mml:mo><mml:mo>(</mml:mo><mml:mfrac><mml:mrow><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:msub><mml:mrow><mml:mo>&#8722;</mml:mo><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="normal">mean</mml:mi></mml:mrow></mml:msub></mml:mfrac><mml:mo>)</mml:mo></mml:math> (12.1)
```

![Equation](img/F000055si2.png)(12.1)

### 12.2.3 Machine learnings algorithms

ML uses a variety of computational methods to generate knowledge from data. Data scientists note that there is no best, one-size-fits-all algorithm for solving a problem. The type of algorithm to be used to obtain the best model may vary depending on the problem type and the number of variables. ML is broadly classified into four groups: supervised (in case of smaller amount of data and clearly labeled for training), unsupervised (usually for large datasets), semisupervised (where unlabeled data are available and retrieving labeled data are exhausting), and reinforcement learning (maximizing cumulative reward concept in an environment of software agents) (Mahesh, 2020). In this study, kNN, SVR, adaptive boosting (AdaBoost), RF, Extra trees (ET), gradient boosting regressor (GBR), eXtreme gradient boosting (XGBoost), and CatBoost algorithms were used.

#### 12.2.3.1 k-nearest neighbors

kNN is a nonparametric ML algorithm proposed by Shakhnarovich et al. (2008). It relies on data training to predict outcomes. The term closest to the output using the training data is measured by distance. For a data point, the kNN algorithm determines points that are close and similar to the training data and averages the values of these points (Lee et al., 2021; Twumasi & Twumasi, 2022).

#### 12.2.3.2 Support vector regression

Proposed by `Cortes` and `Vapnik` (1995), `SVR` is an ML technique where a model learns the significance of a variable to characterize the relationship between input and output (`Zhang & O'Donnell`, 2020). It is a statistical learning algorithm that allows reaching a universal solution with a small number of examples. This algorithm is a powerful regression approach for estimating linear and nonlinear systems and has been widely used in different studies to solve estimation problems (`Malik` et al., 2021). Moreover, having high prediction accuracy increases generalization ability (`Awad` et al., 2015).

#### 12.2.3.3 Adaptive boosting
