
The value we obtained corresponds to the one we have obtained with the olsInOut with 80% of the sample being the in-sample. Since our sample is simulated as being homogeneous, this is the result we are expecting. The cross-validation reveals its power on more complex data with possible heteroscedastic nature.

## 13.12 CONCLUSION

We implemented the ordinary least squares method in the form of an estimation suite. The suite contains a number of additional features, which helps us to assess the performance of a fit. Besides, we have extended the routine for the in-sample/out-of-sample estimation and provided the k-fold cross-validation. This altogether allows us to use the suite for a number of tasks ranging from model estimation and statistical inference to robust model selection. Last but not least, it outlined a way to extend the existing framework for additional functionalities. We will illustrate the extension in a subsequent chapter, where we add regularisation into our linear models.

# CHAPTER 14

## Time Series Econometrics

kdb+/q is a very powerful language to store, manage and analyse large data sets. Time series are data sets containing a set of values of observation at discrete points in time. Time series are present in nearly all fields of applications that rely on a form of data that measures how things evolve. One of the main objectives of time series analysis is the forecast of future realisations of a random phenomenon. One typical example of time series analysis in finance is the forecast of the evolution of a financial asset based on its historical returns, sometimes with the help of exogenous variables such as macroeconomic factors or intrinsic values of the underlying instrument.

This chapter presents the maine forecasting techniques in time series analysis and shows how they can be implemented in q. The chapter is divided into two parts. The first part introduces the autoregressive and moving average processes, stationarity and Granger causality tests and vector autoregressive models. The second part presents a possible implementation of the processes in q.

## 14.1 AUTOREGRESSIVE AND MOVING AVERAGE PROCESSES

### 14.1.1 Introduction

A time series is a sequential set of data constructed chronologically over consecutive times $t=0,1,2,...$, denoted $X_t$. Time series are discrete, where data are usually sampled at equally spaced time intervals, or continuous. Time series containing records of more than one variable are multivariate. Multivariate time series are non-deterministic by nature and are generally affected by four main components: a trend, cyclical, seasonal, and random components. A trend measures the long-term variations in a time series. The cyclical variation of a time series describes the medium-term changes in the data set over time, such as business cycles. A cyclical pattern exists when data exhibit rises and falls that are not of a fixed period. Seasonal variations are of the fixed and known period. The random variations in a time series are caused by unpredictable behaviours of the data that do not follow a particular pattern.

The following sections present the class of univariate ARMA and multivariate VARMA models capable handling trend, cyclical and seasonal behaviour of time series.

### 14.1.2 AR(p) Process

To efficiently forecast the future of a finite series of random variables we need to admit that these variables are somehow dependent from each other. If it is not the case, the series is purely random and not predictable. This section introduces autoregressive models:

Formally, the autoregressive process of order p, denoted as AR(p) is defined as:

$$X_t = c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t, \quad (14.1)$$

where $\phi_1, \dots, \phi_p$ are the parameters of the model, $c$ is a constant and $\{\epsilon_i\}$ the white noise, i.e., $\epsilon_i \sim N(0, \sigma_i^2)$. $E[\epsilon_i] = 0, s < t$. Its expectation is $E[X_t] = c + \sum_{i=1}^p \phi_i E[X_{t-i}]$. If $|\phi_i| < 1, \forall i \in [1]$, the process 14.1 is wide-stationary and $E[X_{t-i}]$ is identical for all values of $t$. Denoting $E[X_t] = \mu, \mu = c + \mu \sum_{i=1}^p \phi_i$, i.e.

$$\mu = \frac{c}{1 - \sum_{i=1}^p \phi_i} \quad (14.2)$$

The variance of (14.1) solves $Var[X_t] = \sum_{i=1}^p \phi_i^2 Var[X_{t-i}] + Var[\epsilon_i]$. If the process $X_t$ is homoskedastic, i.e. $\forall t: Var[X_t] = \sigma^2$,

$$\sigma^2 = \frac{\sigma_\epsilon^2}{1 - \sum_{i=1}^p \phi_i^2} \quad (14.3)$$

The autocovariance $E[X_t X_{t-n}]$ with $t > n$ solves:

$$E[X_t X_{t-n}] = E[(c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t)(c + \sum_{i=1}^p \phi_i X_{t-i-n} + \epsilon_{t-n})]$$
$= c^2 + c \sum_{i=1}^p \phi_i E[X_{t-i}] + c \sum_{i=1}^p \phi_i E[X_{t-i-n}] + (\sum_{i=1}^p \phi_i E[\epsilon_{t-i}])(\sum_{i=1}^p \phi_i E[\epsilon_{t-i-n}]) \quad (14.4)$$

If $X_t$ is homoskedastic with mean $\mu$:

$$E[X_t X_{t-n}] = (c + \mu \sum_{i=1}^p \phi_i)^2.$$

### 14.1.2.1 Simulation

The autoregressive model $X_t = 0.82X_{t-1} + \epsilon_t$ can be simulated as

$y + 0.82*x + \epsilon$

where eps is a list of random numbers. Given the following 5 normally distributed numbers generated by genBoxMuller from simul namespace:

```
eps:-0.153913 2.22843 -0.320418 0.371417 0.573757;
off (y-0.82*x)\eps
```

returns

```
-0.153913 2.102221 1.403403
```

which corresponds to-0.153913 (-0.153913*0.82)+2.22843 (2.102221*0.82)
-0.320418 ...
An implementation of the simulation of an AR(p) model is given by the function
simAR[phi;eps] presented in the second part of the chapter.
To illustrate the behaviour of an autoregressive process, we simulate 100 paths of
t AR(2) process $X_t=0.99X_{t-1}-0.1X_{t-2}$:
quantQ.ts.simAR([0.99;-0.1]);

and depict this in Figure 14.1. We see from Figure 14.1 that the values at time t are strongly correlated with the value at t-1 and slightly negatively with the value at t-2. As such, the process bounces around the mean. Figure 14.2 shows the AR(1) process with $c=0.5, \phi_1=0.4, \sigma=0.2$. Figure 14.3 shows the AR(2) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \sigma=0.2$. Figure 14.4 shows the AR(3) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \sigma=0.2$. Figure 14.5 shows the AR(4) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \phi_4=0.05, \sigma=0.05$.

The following sections present the class of univariate ARMA and multivariate VARMA models capable handling trend, cyclical and seasonal behaviour of time series.

DATA SCIENCE

### 14.1.2.2 Estimation of AR Parameters

To efficiently forecast the future of a finite series of random variables we need to admit that these variables are somehow dependent from each other. If it is not the case, the series is purely random and not predictable. This section introduces autoregressive models:

Formally, the autoregressive process of order p, denoted as AR(p) is defined as:

$$X_t = c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t, \quad (14.1)$$

where $\phi_1, \dots, \phi_p$ are the parameters of the model, $c$ is a constant and $\{\epsilon_i\}$ the white noise, i.e., $\epsilon_i \sim N(0, \sigma_i^2)$. $E[\epsilon_i] = 0, s < t$. Its expectation is $E[X_t] = c + \sum_{i=1}^p \phi_i E[X_{t-i}]$. If $|\phi_i| < 1, \forall i \in [1]$, the process 14.1 is wide-stationary and $E[X_{t-i}]$ is identical for all values of $t$. Denoting $E[X_t] = \mu, \mu = c + \mu \sum_{i=1}^p \phi_i$, i.e.

$$\mu = \frac{c}{1 - \sum_{i=1}^p \phi_i} \quad (14.2)$$

The variance of (14.1) solves $Var[X_t] = \sum_{i=1}^p \phi_i^2 Var[X_{t-i}] + Var[\epsilon_i]$. If the process $X_t$ is homoskedastic, i.e. $\forall t: Var[X_t] = \sigma^2$,

$$\sigma^2 = \frac{\sigma_\epsilon^2}{1 - \sum_{i=1}^p \phi_i^2} \quad (14.3)$$

The autocovariance $E[X_t X_{t-n}]$ with $t > n$ solves:

$$E[X_t X_{t-n}] = E[(c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t)(c + \sum_{i=1}^p \phi_i X_{t-i-n} + \epsilon_{t-n})]$$
$= c^2 + c \sum_{i=1}^p \phi_i E[X_{t-i}] + c \sum_{i=1}^p \phi_i E[X_{t-i-n}] + (\sum_{i=1}^p \phi_i E[\epsilon_{t-i}])(\sum_{i=1}^p \phi_i E[\epsilon_{t-i-n}]) \quad (14.4)$$

If $X_t$ is homoskedastic with mean $\mu$:

$$E[X_t X_{t-n}] = (c + \mu \sum_{i=1}^p \phi_i)^2.$$

### 14.1.2.1 Simulation

The autoregressive model $X_t = 0.82X_{t-1} + \epsilon_t$ can be simulated as

$y + 0.82*x + \epsilon$

where eps is a list of random numbers. Given the following 5 normally distributed numbers generated by genBoxMuller from simul namespace:

```
eps:-0.153913 2.22843 -0.320418 0.371417 0.573757;
off (y-0.82*x)\eps
```

returns

```
-0.153913 2.102221 1.403403
```

which corresponds to-0.153913 (-0.153913*0.82)+2.22843 (2.102221*0.82)
-0.320418 ...
An implementation of the simulation of an AR(p) model is given by the function
simAR[phi;eps] presented in the second part of the chapter.
To illustrate the behaviour of an autoregressive process, we simulate 100 paths of
t AR(2) process $X_t=0.99X_{t-1}-0.1X_{t-2}$:
quantQ.ts.simAR([0.99;-0.1]);

and depict this in Figure 14.1. We see from Figure 14.1 that the values at time t are strongly correlated with the value at t-1 and slightly negatively with the value at t-2. As such, the process bounces around the mean. Figure 14.2 shows the AR(1) process with $c=0.5, \phi_1=0.4, \sigma=0.2$. Figure 14.3 shows the AR(2) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \sigma=0.2$. Figure 14.4 shows the AR(3) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \sigma=0.2$. Figure 14.5 shows the AR(4) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \phi_4=0.05, \sigma=0.05$.

The following sections present the class of univariate ARMA and multivariate VARMA models capable handling trend, cyclical and seasonal behaviour of time series.

### 14.1.2.2 Estimation of AR Parameters

To efficiently forecast the future of a finite series of random variables we need to admit that these variables are somehow dependent from each other. If it is not the case, the series is purely random and not predictable. This section introduces autoregressive models:

Formally, the autoregressive process of order p, denoted as AR(p) is defined as:

$$X_t = c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t, \quad (14.1)$$

where $\phi_1, \dots, \phi_p$ are the parameters of the model, $c$ is a constant and $\{\epsilon_i\}$ the white noise, i.e., $\epsilon_i \sim N(0, \sigma_i^2)$. $E[\epsilon_i] = 0, s < t$. Its expectation is $E[X_t] = c + \sum_{i=1}^p \phi_i E[X_{t-i}]$. If $|\phi_i| < 1, \forall i \in [1]$, the process 14.1 is wide-stationary and $E[X_{t-i}]$ is identical for all values of $t$. Denoting $E[X_t] = \mu, \mu = c + \mu \sum_{i=1}^p \phi_i$, i.e.

$$\mu = \frac{c}{1 - \sum_{i=1}^p \phi_i} \quad (14.2)$$

The variance of (14.1) solves $Var[X_t] = \sum_{i=1}^p \phi_i^2 Var[X_{t-i}] + Var[\epsilon_i]$. If the process $X_t$ is homoskedastic, i.e. $\forall t: Var[X_t] = \sigma^2$,

$$\sigma^2 = \frac{\sigma_\epsilon^2}{1 - \sum_{i=1}^p \phi_i^2} \quad (14.3)$$

The autocovariance $E[X_t X_{t-n}]$ with $t > n$ solves:

$$E[X_t X_{t-n}] = E[(c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t)(c + \sum_{i=1}^p \phi_i X_{t-i-n} + \epsilon_{t-n})]$$
$= c^2 + c \sum_{i=1}^p \phi_i E[X_{t-i}] + c \sum_{i=1}^p \phi_i E[X_{t-i-n}] + (\sum_{i=1}^p \phi_i E[\epsilon_{t-i}])(\sum_{i=1}^p \phi_i E[\epsilon_{t-i-n}]) \quad (14.4)$$

If $X_t$ is homoskedastic with mean $\mu$:

$$E[X_t X_{t-n}] = (c + \mu \sum_{i=1}^p \phi_i)^2.$$

### 14.1.2.1 Simulation

The autoregressive model $X_t = 0.82X_{t-1} + \epsilon_t$ can be simulated as

$y + 0.82*x + \epsilon$

where eps is a list of random numbers. Given the following 5 normally distributed numbers generated by genBoxMuller from simul namespace:

```
eps:-0.153913 2.22843 -0.320418 0.371417 0.573757;
off (y-0.82*x)\eps
```

returns

```
-0.153913 2.102221 1.403403
```

which corresponds to-0.153913 (-0.153913*0.82)+2.22843 (2.102221*0.82)
-0.320418 ...
An implementation of the simulation of an AR(p) model is given by the function
simAR[phi;eps] presented in the second part of the chapter.
To illustrate the behaviour of an autoregressive process, we simulate 100 paths of
t AR(2) process $X_t=0.99X_{t-1}-0.1X_{t-2}$:
quantQ.ts.simAR([0.99;-0.1]);

and depict this in Figure 14.1. We see from Figure 14.1 that the values at time t are strongly correlated with the value at t-1 and slightly negatively with the value at t-2. As such, the process bounces around the mean. Figure 14.2 shows the AR(1) process with $c=0.5, \phi_1=0.4, \sigma=0.2$. Figure 14.3 shows the AR(2) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \sigma=0.2$. Figure 14.4 shows the AR(3) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \sigma=0.2$. Figure 14.5 shows the AR(4) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \phi_4=0.05, \sigma=0.05$.

The following sections present the class of univariate ARMA and multivariate VARMA models capable handling trend, cyclical and seasonal behaviour of time series.

### 14.1.2.2 Estimation of AR Parameters

To efficiently forecast the future of a finite series of random variables we need to admit that these variables are somehow dependent from each other. If it is not the case, the series is purely random and not predictable. This section introduces autoregressive models:

Formally, the autoregressive process of order p, denoted as AR(p) is defined as:

$$X_t = c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t, \quad (14.1)$$

where $\phi_1, \dots, \phi_p$ are the parameters of the model, $c$ is a constant and $\{\epsilon_i\}$ the white noise, i.e., $\epsilon_i \sim N(0, \sigma_i^2)$. $E[\epsilon_i] = 0, s < t$. Its expectation is $E[X_t] = c + \sum_{i=1}^p \phi_i E[X_{t-i}]$. If $|\phi_i| < 1, \forall i \in [1]$, the process 14.1 is wide-stationary and $E[X_{t-i}]$ is identical for all values of $t$. Denoting $E[X_t] = \mu, \mu = c + \mu \sum_{i=1}^p \phi_i$, i.e.

$$\mu = \frac{c}{1 - \sum_{i=1}^p \phi_i} \quad (14.2)$$

The variance of (14.1) solves $Var[X_t] = \sum_{i=1}^p \phi_i^2 Var[X_{t-i}] + Var[\epsilon_i]$. If the process $X_t$ is homoskedastic, i.e. $\forall t: Var[X_t] = \sigma^2$,

$$\sigma^2 = \frac{\sigma_\epsilon^2}{1 - \sum_{i=1}^p \phi_i^2} \quad (14.3)$$

The autocovariance $E[X_t X_{t-n}]$ with $t > n$ solves:

$$E[X_t X_{t-n}] = E[(c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t)(c + \sum_{i=1}^p \phi_i X_{t-i-n} + \epsilon_{t-n})]$$
$= c^2 + c \sum_{i=1}^p \phi_i E[X_{t-i}] + c \sum_{i=1}^p \phi_i E[X_{t-i-n}] + (\sum_{i=1}^p \phi_i E[\epsilon_{t-i}])(\sum_{i=1}^p \phi_i E[\epsilon_{t-i-n}]) \quad (14.4)$$

If $X_t$ is homoskedastic with mean $\mu$:

$$E[X_t X_{t-n}] = (c + \mu \sum_{i=1}^p \phi_i)^2.$$

### 14.1.2.1 Simulation

The autoregressive model $X_t = 0.82X_{t-1} + \epsilon_t$ can be simulated as



To empirically verify the convergence of an autoregressive process, we simulate 100 paths of
t AR(2) process $X_t=0.99X_{t-1}-0.1X_{t-2}$:
quantQ.ts.simAR([0.99;-0.1]);

and depict this in Figure 14.1. We see from Figure 14.1 that the values at time t are strongly correlated with the value at t-1 and slightly negatively with the value at t-2. As such, the process bounces around the mean. Figure 14.2 shows the AR(1) process with $c=0.5, \phi_1=0.4, \sigma=0.2$. Figure 14.3 shows the AR(2) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \sigma=0.2$. Figure 14.4 shows the AR(3) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \sigma=0.2$. Figure 14.5 shows the AR(4) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \phi_4=0.05, \sigma=0.05$.

The following sections present the class of univariate ARMA and multivariate VARMA models capable handling trend, cyclical and seasonal behaviour of time series.

### 14.1.2.2 Estimation of AR Parameters

To efficiently forecast the future of a finite series of random variables we need to admit that these variables are somehow dependent from each other. If it is not the case, the series is purely random and not predictable. This section introduces autoregressive models:

Formally, the autoregressive process of order p, denoted as AR(p) is defined as:

$$X_t = c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t, \quad (14.1)$$

where $\phi_1, \dots, \phi_p$ are the parameters of the model, $c$ is a constant and $\{\epsilon_i\}$ the white noise, i.e., $\epsilon_i \sim N(0, \sigma_i^2)$. $E[\epsilon_i] = 0, s < t$. Its expectation is $E[X_t] = c + \sum_{i=1}^p \phi_i E[X_{t-i}]$. If $|\phi_i| < 1, \forall i \in [1]$, the process 14.1 is wide-stationary and $E[X_{t-i}]$ is identical for all values of $t$. Denoting $E[X_t] = \mu, \mu = c + \mu \sum_{i=1}^p \phi_i$, i.e.

$$\mu = \frac{c}{1 - \sum_{i=1}^p \phi_i} \quad (14.2)$$

The variance of (14.1) solves $Var[X_t] = \sum_{i=1}^p \phi_i^2 Var[X_{t-i}] + Var[\epsilon_i]$. If the process $X_t$ is homoskedastic, i.e. $\forall t: Var[X_t] = \sigma^2$,

$$\sigma^2 = \frac{\sigma_\epsilon^2}{1 - \sum_{i=1}^p \phi_i^2} \quad (14.3)$$

The autocovariance $E[X_t X_{t-n}]$ with $t > n$ solves:

$$E[X_t X_{t-n}] = E[(c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t)(c + \sum_{i=1}^p \phi_i X_{t-i-n} + \epsilon_{t-n})]$$
$= c^2 + c \sum_{i=1}^p \phi_i E[X_{t-i}] + c \sum_{i=1}^p \phi_i E[X_{t-i-n}] + (\sum_{i=1}^p \phi_i E[\epsilon_{t-i}])(\sum_{i=1}^p \phi_i E[\epsilon_{t-i-n}]) \quad (14.4)$$

If $X_t$ is homoskedastic with mean $\mu$:

$$E[X_t X_{t-n}] = (c + \mu \sum_{i=1}^p \phi_i)^2.$$

### 14.1.2.1 Simulation

The autoregressive model $X_t = 0.82X_{t-1} + \epsilon_t$ can be simulated as

$y + 0.82*x + \epsilon$

where eps is a list of random numbers. Given the following 5 normally distributed numbers generated by genBoxMuller from simul namespace:

```
eps:-0.153913 2.22843 -0.320418 0.371417 0.573757;
off (y-0.82*x)\eps
```

returns

```
-0.153913 2.102221 1.403403
```

which corresponds to-0.153913 (-0.153913*0.82)+2.22843 (2.102221*0.82)
-0.320418 ...
An implementation of the simulation of an AR(p) model is given by the function
simAR[phi;eps] presented in the second part of the chapter.
To illustrate the behaviour of an autoregressive process, we simulate 100 paths of
t AR(2) process $X_t=0.99X_{t-1}-0.1X_{t-2}$:
quantQ.ts.simAR([0.99;-0.1]);

and depict this in Figure 14.1. We see from Figure 14.1 that the values at time t are strongly correlated with the value at t-1 and slightly negatively with the value at t-2. As such, the process bounces around the mean. Figure 14.2 shows the AR(1) process with $c=0.5, \phi_1=0.4, \sigma=0.2$. Figure 14.3 shows the AR(2) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \sigma=0.2$. Figure 14.4 shows the AR(3) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \sigma=0.2$. Figure 14.5 shows the AR(4) process with $c=0.5, \phi_1=0.4,,phi_2=0.2, \phi_3=0.1, \phi_4=0.05, \sigma=0.05$.

The following sections present the class of univariate ARMA and multivariate VARMA models capable handling trend, cyclical and seasonal behaviour of time series.

### 14.1.2.2 Estimation of AR Parameters

To efficiently forecast the future of a finite series of random variables we need to admit that these variables are somehow dependent from each other. If it is not the case, the series is purely random and not predictable. This section introduces autoregressive models:

Formally, the autoregressive process of order p, denoted as AR(p) is defined as:

$$X_t = c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t, \quad (14.1)$$

where $\phi_1, \dots, \phi_p$ are the parameters of the model, $c$ is a constant and $\{\epsilon_i\}$ the white noise, i.e., $\epsilon_i \sim N(0, \sigma_i^2)$. $E[\epsilon_i] = 0, s < t$. Its expectation is $E[X_t] = c + \sum_{i=1}^p \phi_i E[X_{t-i}]$. If $|\phi_i| < 1, \forall i \in [1]$, the process 14.1 is wide-stationary and $E[X_{t-i}]$ is identical for all values of $t$. Denoting $E[X_t] = \mu, \mu = c + \mu \sum_{i=1}^p \phi_i$, i.e.

$$\mu = \frac{c}{1 - \sum_{i=1}^p \phi_i} \quad (14.2)$$

The variance of (14.1) solves $Var[X_t] = \sum_{i=1}^p \phi_i^2 Var[X_{t-i}] + Var[\epsilon_i]$. If the process $X_t$ is homoskedastic, i.e. $\forall t: Var[X_t] = \sigma^2$,

$$\sigma^2 = \frac{\sigma_\epsilon^2}{1 - \sum_{i=1}^p \phi_i^2} \quad (14.3)$$

The autocovariance $E[X_t X_{t-n}]$ with $t > n$ solves:

$$E[X_t X_{t-n}] = E[(c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t)(c + \sum_{i=1}^p \phi_i X_{t-i-n} + \epsilon_{t-n})]$$
$= c^2 + c \sum_{i=1}^p \phi_i E[X_{t-i}] + c \sum_{i=1}^p \phi_i E[X_{t-i-n}] + (\sum_{i=1}^p \phi_i E[\epsilon_{t-i}])(\sum_{i=1}^p \phi_i E[\epsilon_{t-i-n}]) \quad (14.4)$$

If $X_t$ is homoskedastic with mean $\mu$:

$$E[X_t X_{t-n}] = (c + \mu \sum_{i=1}^p \phi_i)^2.$$

### 14.1.2.1 Simulation

The autoregressive model $X_t = 0.82X_{t-1} + \epsilon_t$ can be simulated as

$y + 0.82*x + \epsilon$

where eps is a list of random numbers. Given the following 5 normally distributed numbers generated by genBoxMuller from simul namespace:

```
eps:-0.153913 2.22843 -0.320418 0.371417 0.573757;
off (y-0.82*x)\eps
```

returns

```
-0.153913 2.102221 1.403403
```

which corresponds to-0.153913 (-0.153913*0.82)+2.22843 (2.102221*0.82)
-0.320418 ...
An implementation of the simulation of an AR(p) model is given by the function
simAR[phi;eps] presented in the second part of the chapter.
To illustrate the behaviour of an autoregressive process, we simulate 100 paths of
t AR(2) process $X_t=0.99X_{t-1}-0.1X_{t-2}$:
quantQ.ts.simAR([0.99;-0.1]);

and depict this in Figure 14.1. We see from Figure 14.1 that the values at time t are strongly correlated with the value at t-1 and slightly negatively with the value at t-2. As such, the process bounces around the mean. Figure 14.2 shows the AR(1) process with $c=0.5, \phi_1=0.4, \sigma=0.2$. Figure 14.3 shows the AR(2) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \sigma=0.2$. Figure 14.4 shows the AR(3) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \sigma=0.2$. Figure 14.5 shows the AR(4) process with $c=0.5, \phi_1=0.4, \phi_2=0.2, \phi_3=0.1, \phi_4=0.05, \sigma=0.05$.

The following sections present the class of univariate ARMA and multivariate VARMA models capable handling trend, cyclical and seasonal behaviour of time series.

### 14.1.2.2 Estimation of AR Parameters

To efficiently forecast the future of a finite series of random variables we need to admit that these variables are somehow dependent from each other. If it is not the case, the series is purely random and not predictable. This section introduces autoregressive models:

Formally, the autoregressive process of order p, denoted as AR(p) is defined as:

$$X_t = c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t, \quad (14.1)$$

where $\phi_1, \dots, \phi_p$ are the parameters of the model, $c$ is a constant and $\{\epsilon_i\}$ the white noise, i.e., $\epsilon_i \sim N(0, \sigma_i^2)$. $E[\epsilon_i] = 0, s < t$. Its expectation is $E[X_t] = c + \sum_{i=1}^p \phi_i E[X_{t-i}]$. If $|\phi_i| < 1, \forall i \in [1]$, the process 14.1 is wide-stationary and $E[X_{t-i}]$ is identical for all values of $t$. Denoting $E[X_t] = \mu, \mu = c + \mu \sum_{i=1}^p \phi_i$, i.e.

$$\mu = \frac{c}{1 - \sum_{i=1}^p \phi_i} \quad (14.2)$$

The variance of (14.1) solves $Var[X_t] = \sum_{i=1}^p \phi_i^2 Var[X_{t-i}] + Var[\epsilon_i]$. If the process $X_t$ is homoskedastic, i.e. $\forall t: Var[X_t] = \sigma^2$,

$$\sigma^2 = \frac{\sigma_\epsilon^2}{1 - \sum_{i=1}^p \phi_i^2} \quad (14.3)$$

The autocovariance $E[X_t X_{t-n}]$ with $t > n$ solves:

$$E[X_t X_{t-n}] = E[(c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t)(c + \sum_{i=1}^p \phi_i X_{t-i-n} + \epsilon_{t-n})]$$
$= c^2 + c \sum_{i=1}^p \phi_i E[X_{t-i}] + c \sum_{i=1}^p \phi_i E[X_{t-i-n}] + (\sum_{i=1}^p \phi_i E[\epsilon_{t-i}])(\sum_{i=1}^p \phi_i E[\epsilon_{t-i-n}]) \quad (14.4)$$

If $X_t$ is homoskedastic with mean $\mu$:

$$E[X_t X_{t-n}] = (c + \mu \sum_{i=1}^p \phi_i)^2.$$

### 14.1.2.1 Simulation

The autoregressive model $X_t = 0.82X_{t-1} + \epsilon_t$ can be simulated as

$y + 0.82*x + \epsilon$

where eps is a list of random numbers. Given the following 5 normally distributed numbers generated by genBoxMuller from simul namespace:

```
eps:-0.153913 2.22843 -0.320418 0.371417 0.573757;
off (y-0.82*x)\eps
```

returns

```
-0.153913 2.102221 1.403403
```

which corresponds to-0.153913 (-0.153913*0.82)+2.22843 (2.102221*0.82)
-0.320418 ...
An implementation of the simulation of an AR(p) model is given by the function
simAR[phi;eps] presented in the second part of the chapter.
To illustrate the behaviour of an autoregressive process, we simulate 100 paths of
t AR(2) process $X_t=0.99X_{t-1}-0.1X_{t-2}$:
quantQ.ts.simAR([0.99;-0.1]);

DATA SCIENCE



To efficiently forecast the future of a finite series of random variables we need to admit that these variables are somehow dependent from each other. If it is not the case, the series is purely random and not predictable. This section introduces autoregressive models:

Formally, the autoregressive process of order p, denoted as AR(p) is defined as:

$$X_t = c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t, \quad (14.1)$$

where $\phi_1, \dots, \phi_p$ are the parameters of the model, $c$ is a constant and $\{\epsilon_i\}$ the white noise, i.e., $\epsilon_i \sim N(0, \sigma_i^2)$. $E[\epsilon_i] = 0, s < t$. Its expectation is $E[X_t] = c + \sum_{i=1}^p \phi_i E[X_{t-i}]$. If $|\phi_i| < 1, \forall i \in [1]$, the process 14.1 is wide-stationary and $E[X_{t-i}]$ is identical for all values of $t$. Denoting $E[X_t] = \mu, \mu = c + \mu \sum_{i=1}^p \phi_i$, i.e.

$$\mu = \frac{c}{1 - \sum_{i=1}^p \phi_i} \quad (14.2)$$

The variance of (14.1) solves $Var[X_t] = \sum_{i=1}^p \phi_i^2 Var[X_{t-i}] + Var[\epsilon_i]$. If the process $X_t$ is homoskedastic, i.e. $\forall t: Var[X_t] = \sigma^2$,

$$\sigma^2 = \frac{\sigma_\epsilon^2}{1 - \sum_{i=1}^p \phi_i^2} \quad (14.3)$$

The autocovariance $E[X_t X_{t-n}]$ with $t > n$ solves:

$$E[X_t X_{t-n}] = E[(c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t)(c + \sum_{i=1}^p \phi_i X_{t-i-n} + \epsilon_{t-n})]$$
$= c^2 + c \sum_{i=1}^p \phi_i E[X_{t-i}] + c \sum_{i=1}^p \phi_i E[X_{t-i-n}] + (\sum_{i=1}^p \phi_i E[\epsilon_{t-i}])(\sum_{i=1}^p \phi_i E[\epsilon_{t-i-n}]) \quad (14.4)$$

If $X_t$ is homoskedastic with mean $\mu$:

$$E[X_t X_{t-n}] = (c + \mu \sum_{i=1}^p \phi_i)^2.$$
