+   3. Predictions can be made by calling the predict() function$^{3}$ and specifying the index of the time or times to be predicted.

Let's start off with something simple. We will fit an ARIMA model to the entire Shampoo Sales dataset and review the residual errors. First, we fit an **ARIMA(5,1,0)** model. This sets the lag value to 5 for autoregression, uses a difference order of 1 to make the time series stationary, and uses a moving average model of 0. When fitting the model, a lot off debug information is provided about the fit of the linear regression model. We can turn this off by setting the **disp** argument to 0.

```
# fit an ARIMA model and plot residual errors  
from pandas import read_csv  
from pandas import datetime  
from pandas import DataFrame  
from statsmodels.tsa.arima_model import ARIMA  
from matplotlib import pyplot  
# load dataset  
def parser(x):  
return datetime.strptime('1990'+x, '%Y-%m')  
series = read_csv('shampoo-sales.csv', header=0, index_col=0, parse_dates=True,  
squeeze=True, date_parser=parser)  
# fit model  
model = ARIMA(series, order=(5,1,0))  
model_fit = model.fit(disp=0)  
# summary of fit model  
print(model_fit.summary())  
# line plot of residuals  
residuals = DataFrame(model_fit.resid)  
residuals.plot()  
pyplot.show()  
# density plot of residuals  
residuals.plot(kind='kde')  
pyplot.show()  
# summary stats of residuals  
print(residuals.describe())
```

Listing 24.4: ARIMA model of the Shampoo Sales dataset.

Running the example prints a summary of the fit model. This summarizes the coefficient values used as well as the skill of the fit on the in-sample observations.

ARIMA Model Results  

```  
                             Dep. Variable:    D.Sales  
No. Observations:                 35  
Model:                     ARIMA(5, 1, 0)  
Log Likelihood              -196.170  
Method:                        css-mle  
S.D. of innovations              64.241  
Date:                    Fri, 20 Jan 2017  
AIC                            406.340  
Time:                           15:01:24  
BIC                            417.227  
Sample:                      02-01-1901  
HQIC                           410.098  
                               - 12-01-1903  
                                  
             coef    std err         z    P>|z|   [95.0% Conf. Int.]  
```

$^{3}$http://statsmodels.sourceforge.net/develop/generated/statsmodels.tsa.arima_model.ARIMA.predict.html