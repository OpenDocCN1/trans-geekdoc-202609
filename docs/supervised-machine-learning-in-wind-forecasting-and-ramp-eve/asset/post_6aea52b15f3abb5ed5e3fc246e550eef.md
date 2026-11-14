
| Wind speed (Y) (m/s) | Wind direction (X) (degree) |
|---|---|
| 6.51 | 240.7 |
| 6.63 | 237.1 |
| 7.31 | 238.2 |
| 6.45 | 238.9 |
| 6.21 | 240.3 |
| 5.99 | 238.9 |
| 5.64 | 240.1 |
| 5.97 | 249.8 |
| 6.27 | 252.4 |
| 5.46 | 253.3 |

## Table A.1 Wind speed and direction
data for linear regression.

## Example A.8. R codes for linear regression

```
lm.fit<-lm(speed ~ direction)
summary(lm.fit)
```

## Output

Call:
lm(formula = speed ~ direction)
Residuals:
Min 1Q Median 3Q Max
-2.1752 -0.7153 -0.2277 0.8084 3.0242
Coefficients:
Estimate Std. Error t value Pr(>|t|)
(Intercept) 1.87824 3.50950 0.535 0.595
direction 0.01925 0.01388 1.387 0.172
Residual standard error: 1.097 on 48 degrees of freedom
Multiple R-squared: 0.03852, Adjusted R-squared: 0.01849
F-statistic: 1.923 on 1 and 48 DF, p-value: 0.1719

From this R code output we can see that the wind speed is related to wind direction with a mathematical model given as (see Fig. A.5)

speed = 1.87824 + 0.01925 · direction. (A.4)

It is worth noting that the R² value for the current regression problem
is very small. The predictions can be improved further if we use more than
one independent variable.

![](img/b53e39e35231af65df8ccaa99eb28bee_193_0.png)

## Figure A.5 Linear regression model for speed and distance in R.

![](img/b53e39e35231af65df8ccaa99eb28bee_193_1.png)

## Figure A.6 Support vector regression model.

## A.3 Support vector regression in R

Let us now see how to fit a support vector machine model for a regression model for the example studied in previous case. Here the data for wind speed and direction remain the same. We try to fit an svm model as described in Fig. A.6 and find out its error performance.

## Example A.9. R codes for SVR

```
model <- svm(speed ~ direction)
predicted_speed <- predict(model, direction)
points(direction, predicted_speed, col = "red", pch=4)
rmse <- function(error)
{
sqrt(mean(error^2))
}
error <- model$residuals # same as speed-predicted_speed
predictionRMSE <- rmse(error)
```

## Performance of 'svm'

![](img/b53e39e35231af65df8ccaa99eb28bee_194_0.png)

## Figure A.7 Mean squared error after tuning SVM hyperparameters.

```
plot(direction,speed,pch=14)
points(direction,predicted_speed,col="red",pch=4)
```

SVM performance can be further improved by tuning the hyperparameters. A grid search can be performed in the range of 2-10—210 to determine optimal values of tolerance error ε and regularization parameter C. R commands for hyperparameters tuning are given next.

## Example A.10. Hyperparameter tuning in R

```
tuneResult <- tune(svm, speed ~ direction, data = Data,
ranges = list(epsilon = seq(0,1,0.1), cost = 2^(2:9)) )
```

In this example, Data is a data frame consisting of wind speed and wind directions, which are column vectors. The results of hyperparameter tuning can be accessed using print(tuneResult). See Fig. A.7.

## A.4 Random forest regression in R

Random forest regression can be implemented in R using a set of commands. The data for predictor (independent variables) and output variables are to be stored in the form of a data frame. In case of machine learning techniques the data are split into training and testing sets with an appropriate ratio. Consider a dataset with wind speed as output variable and its wavelet decomposition as predictor variables. As discussed in Chapter 5, the approximate and detail signals form the input dataset for predicting wind speed. In this example for RF model, we take a dataframe f5 with 4320 samples and divide them into training (3000) and testing (1320) sets.

## Example A.11. R codes for RF model

```
head(f5)
summary(f5)
library(caret)
library(caTools)
traindata<-f5[1:3000,]
testdata<-f5[3001:4320,]
xtrain<-traindata[,c(2,3,4,5,6,7)]
ytrain<-traindata[,1]
test<-testdata[,1]
xtest<-testdata[,c(2,3,4,5,6,7)]
library(randomForest)
rfrobj<-randomForest(ws~.,data=f5,
ntree=1000,keep.forest=TRUE, importance=TRUE,
na.action=na.omit)
summary(rfrobj)
predict.rfr<-predict(rfrobj,xtest)
write.table(predict.rfr, file = "rfr.txt", row.names = TRUE,
col.names = NA)
print(predict.rfr)
summary(predict.rfr)
rmse.rfr<-sqrt(mean((predict.rfr-ytest)^2))
nmse.rfr<-sum((predict.rfr-ytest)^2)/sum((ytest-mean(ytest))^2)
r2.rfr<-sum((predict.rfr-mean(ytest))^2)/sum((ytest-mean(ytest))^2)
plot(rfrobj)
lines(predict.rfr)
```

Further, to determine the optimal number of trees for the given dataset,
R command which.min(rfrobj$mse) can be used. Fig. A.8 illustrates the
MSE values with variation in number of trees.

## A.5 Gradient boosted machines in R

Similar to random forest regression, gradient boost machines (GBMs) can
be used to predict wind speed or any other variable. We now discuss the
R codes for GBM model for the same example discussed in the previous
section. See Fig. A.9.

## rfrobj

![](img/b53e39e35231af65df8ccaa99eb28bee_196_0.png)

![](img/b53e39e35231af65df8ccaa99eb28bee_196_1.png)

## Figure A.8 Variation of MSE with number of trees and scatter plot between actual and predicted values for RF model.

![](img/b53e39e35231af65df8ccaa99eb28bee_196_2.png)

![](img/b53e39e35231af65df8ccaa99eb28bee_196_3.png)

## Figure A.9 Variation of MSE with number of trees and scatter plot between actual and predicted value for GBM model.

## Example A.12. R codes for GBM

```
library(gbm)
library(xgboost)
library(h2o)
library(pdp)
library(ggplot2)
head(f5)
summary(f5)
traindata<-f5[1:3000,]
testdata<-f5[3001:4320,]
xtrain<-traindata[,c(2,3,4,5,6,7)]
ytrain<-traindata[,1]
test<-testdata[,1]
xtest<-testdata[,c(2,3,4,5,6,7)]
gbm.fit<-gbm(formula=ws~.,data = f5,
var.monotone = c(0,0,0,0,0,0),
distribution = "gaussian", n.trees = 10000, shrinkage = 0.05,
interaction.depth = 3, bag.fraction = 0.5, train.fraction = 0.5,
n.minobsinnode = 10, cv.folds = 5, keep.data = TRUE,
verbose = FALSE, n.cores = 1)
print(gbm.fit)
sqrt(min(gbm.fit$cv.error))
gbm.perf(gbm.fit,method="cv")
ynew<-predict(gbm.fit, xtest, 9982, type = "link",
single.tree = FALSE)
write.table(ynew, file = "yGBM.txt", row.names = TRUE,
col.names = NA)
library(forecast)
accuracy(ynew,ytest)
rmse.gbm<-sqrt(mean((ynew-ytest)^2))
nmse.gbm<-sum((ynew-ytest)^2)/sum((ytest-mean(ytest))^2)
r2.gbm<-sum((ynew-mean(ytest))^2)/sum((ytest-mean(ytest))^2)
write.table(ytest, file = "ytest.txt", row.names = TRUE,
col.names = NA)
```

## Index

- A
- Absolute error (AE), 117
- Abundant wind resource, 9
- Actuator disk model (ADM), 10
- Advanced forecasting algorithms, 7, 101
- Agricultural forecasts, 102
- Air quality index (AQI), 109, 110
- Allied areas, 1
- forecasting, 76
- wind forecasting, 5
- Annual electricity production (AEP), 162
- Annual energy production (AEP), 19
- Artificial bee colony optimization (ABCO), 28
- Artificial neural network (ANN), 6, 9, 27, 29, 34, 36, 41, 143, 154
- Atmospheric boundary layer (ABL), 149
- Atmospheric conditions, 26, 28, 117, 141, 145, 146
- Autoregression (AR), 29, 75, 110
- Autoregressive exogenous moving average (ARMAX), 29, 30
- Autoregressive integrated moving average (ARIMA), 4, 29, 30, 32, 36, 37, 61, 77, 110, 113, 143
- model, 32, 64, 91, 94, 131
- process, 32
- Autoregressive moving average (ARMA), 4, 29, 30, 32, 143
- model, 30–32
- process, 31
- B
- Back propagation neural network (BPNN), 76
- Battery energy storage system (BESS), 5
- Benchmark models, 32, 37, 61, 64, 70, 76, 77, 93, 143, 149, 153, 154, 156, 159
- persistence models, 67, 75, 136
- prediction models, 53
- wake models, 141, 167

- Bilateral Gaussian wake model, 143, 146, 148–151, 156, 164, 167
- Bimodal wind, 11
- Bimodal wind regimes, 13
- Boosting algorithm, 67, 68, 129
- C
- California Irrigation Management Information System (CIMIS), 107
- Classic SVR model, 53
- Combined cycle power plant (CCPP), 49
- Computational fluid dynamics (CFD), 144
- Continuous wavelet transform (CWT), 78
- Conventional SVR model, 94, 95
- Crop forecasting, 102
- Cup anemometer, 84, 148, 153
- D
- Decomposition forecasting algorithms (DFA), 27
- Deep neural network (DNN), 27, 69
- Discrete wavelet transform (DWT), 27, 76, 78
- Downstream distance, 146–148
- Downwind distance, 144–146, 149, 152, 164
- E
- Earthquake forecasting, 102
- Electric power, 1, 101
- Electric power generation, 11
- Electricity markets, 4, 5, 79, 120
- Elman neural network (ENN), 76
- Empirical mode decomposition (EMD), 28, 91, 134
- Empirical wavelet transform (EWT), 27
- Ensemble empirical mode decomposition (EEMD), 29, 76, 77
- Error function, 63
- metrics, 31, 94
- minimization, 36
- prediction, 122
