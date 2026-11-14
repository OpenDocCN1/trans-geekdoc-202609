
prediction. The potential superiority of decision tree ensemble models over SVR models and its variants is also discussed where the problem of over-fitting causes large errors for raw wind speed data. We also discuss a special application of machine learning-based forecasting models for wind farms in the presence of wake interactions. Two case studies with different wind farm layouts are considered, and relevant wind turbines affecting prediction of a given turbine are identified.

Overall, an integrated solution that aims to find a best possible machine learning model for wind speed time series can be found for optimal wind power dispatch considering the reserve power capacity. Wind farm operators also face an important challenge of decision making, which has its roots from the forecasting technique incorporated to plan their wind power dispatch [1–3]. For a hybrid wind farm, operational strategies that a wind farm operator decides to take are also dependent on the reserve power capacity available. For ensuring a good balance between forecasts and reserve capacity, an integrated approach considering the wake effect that alters the power production of a wind farm can be deduced. Wake effects can be controlled up to a certain amount by implementing redirection strategies. These strategies involve accurate measurement devices like LIDAR, which gives an estimate of wind speed just before it actually interacts with the wind turbine. Availability of such devices helps a wind farm operator to take necessary steps in conjunction with the operational strategy to be implemented. Since wind markets require clearances at a short interval of 30 minutes to 1 hour, more focus is laid on short-term wind forecasting, which also tries to encompass weather models. The integrated methodology will determine the best forecasting technique, which under the effect of wake will lead to savings in reserve power capacity in terms of BESS and increase its life time.

## References

- [1] H.S. Dhiman, D. Deb, Decision and Control in Hybrid Wind Farms, Springer, 2019.
- [2] H. Dhiman, D. Deb, V. Muresan, V. Balas, Wake management in wind farms: an adaptive control approach, Energies 12 (7) (2019) 1247, https://doi.org/10.3390/en12071247.
- [3] H.S. Dhiman, D. Deb, V. Muresan, M.-L. Unguresan, Multi-criteria decision making approach for hybrid operation of wind farms, Symmetry 11 (5) (2019) 675, https://doi.org/10.3390/sym11050675.

## APPENDIX A

### Introduction to R for machine learning regression

### A.1 Data handling in R

Data in R can be handled in several forms like vectors, lists, matrices, and data frames. Commonly used forms are vectors and lists as they are easy to work with. Vectors and matrices represent homogeneous data, whereas lists and data frames deal with heterogeneous data.

### A.1.1 Data handling via vectors, lists, and data frames

### Example A.1. Creating vectors in R

```
Player <- c("Cristiano","Messi","Neymar")
Salary<-c(35000,50000,100000)
```

### Example A.2. Creating lists in R

```
Profile <- list(name=c("Cristiano","Messi","Neymar"),
salary=c(75000,50000,100000))
```

### Output

```
Profile
$name
[1] "Cristiano" "Messi" "Neymar"
$salary
[1] 75000 50000 100000
```

### A.1.2 Importing data through .xlsx and .csv files

Most of the data used in machine learning applications are stored in forms of column vectors, which are saved in .xlsx or .csv files. Data handling, storing, manipulation, and computation offered by Microsoft Excel file format is undisputed in terms of popularity and security. Conveniently, in R the Excel files with large chunk of data can be directly imported into workspace by using simple one line command. The following code shows how to import wind data along with several other weather variables for a site in Brazil; see the output of the data imported and visualize the summary of the imported data.

### Example A.3. Example to import data from .xlsx file

```
library(xlsx)
read.xlsx("wind_data_brazil.xlsx",sheetName="Sheet2")
View(wind_data_brazil)
```

### Output

| Sr no. | Ozone | Solar R | Wind | Temp | Month | Day |
|---|---|---|---|---|---|---|
| 1 | 41 | 190 | 7.4 | 67 | 5 | 1 |
| 2 | 36 | 118 | 8.0 | 72 | 5 | 2 |
| 3 | 12 | 149 | 12.6 | 74 | 5 | 3 |
| 4 | 18 | 313 | 11.5 | 62 | 5 | 4 |
| 5 | NA | NA | 14.3 | 56 | 5 | 5 |

### Summary

```
summary(wind_data_brazil$Wind)
```

| Min. | 1st Qu. | Median | Mean | 3rd Qu. | Max. |
|---|---|---|---|---|---|
| 1.700 | 7.400 | 9.700 | 9.958 | 11.500 | 20.700 |

Importing .csv files works in a similar way. We further give an example to import a file named “Anholt_Denmark_March2019.csv”. To view the summary of the variables, the same command can be used as in case of .xlsx files.

### Example A.4. Example to import data from .csv files

```
library(readr)
data <- read_csv("Anholt_Denmark_March2019.csv")
View(data)
```

### A.1.3 Line plots, histograms, and autocorrelation function for wind speed in R

Consider a list of variables f1, consisting of wind speed, temperature, humidity, and air pressure for a site. To plot the distribution of wind speed for this site, R commands can be conveniently used as follows.

### Example A.5. R code for Line plot & Histogram

```
plot(f1$windspeed,xlab = "time",ylab = "Wind speed")
```

See Fig. A.1.

![](img/b53e39e35231af65df8ccaa99eb28bee_189_0.png)

Figure A.1 Line plot for wind speed.

![](img/b53e39e35231af65df8ccaa99eb28bee_189_1.png)

Figure A.2 Wind speed probability density distribution using R command.

```
hist(f1$windspeed,main="Wind speed distribution",col="red",
probability = TRUE)
```

See Fig. A.2.

We now discuss the R commands for autocorrelation functions for wind speed. An autocorrelation function depicts the dependence of an element with respect to elements of the series itself. For a wind speed time series, autocorrelation aids in selecting the lag orders for ARMA and ARIMA models. Dominant lag instants are helpful in identifying the behavioral pattern in wind speed. Mathematically, autocorrelation at lag instant k for a time series Y_t is expressed as

$$r_k = \frac{\sum_{t=1}^{N-k} (Y_t - \overline{Y}) (Y_{t+k} - \overline{Y})}{\sum_{t=1}^{N} (Y_t - \overline{Y})^2}. \quad \text{(A.1)}$$

### Series f1$windspeed

![](img/b53e39e35231af65df8ccaa99eb28bee_190_0.png)

Figure A.3 ACF plot for time series f1$windspeed in R.

### Example A.6. Autocorrelation of time-series

```
acf(f1$windspeed, lag.max = length(f1$windspeed), plot = TRUE)
```

See Fig. A.3.

### A.1.4 Parameter estimation for wind speed probability density functions in R

Various PDFs like Weibull, Rayleigh, gamma, log-normal, and Lindley are based on parameters that decide the shape and scale of wind speed distributions. Estimation of such parameters is based on nonlinear minimization of loglikelihood function. In R the parameters can be estimated by applying defining functions for individual distributions. For example, the Stacy–Mihram model described in Chapter 2 has parameters α and β, which can be estimated by minimizing the negative of the loglikelihood function

$$
L(v|\alpha, \beta) = n \log \beta - n \beta \log \alpha + (\beta - 1) \sum_{i=1}^{n} \log(v_i) - \sum_{i=1}^{n} (v_i / \alpha)^\beta. \quad \text{(A.2)}
$$

Let us consider the parameter vector θ = (α, β) such that θ[1] = α and θ[2] = β. The function nlm for nonlinear minimization can be used as follows.

### Example A.7. Parameter estimation for distributions in R

```
n<-length(Y)
fn<-function(theta)
{
```

![](img/b53e39e35231af65df8ccaa99eb28bee_191_0.png)

### Figure A.4 Scatter plot between wind speed and direction.

```
-n*log(theta[2])+n*(theta[2])*log(theta[1])-(theta[2]-1)
*sum(log(Y))+sum((Y/theta[1])^theta[2])
}
theta_est<-nlm(fn, theta <- c(20,45), hessian=TRUE)
```

In these R commands, Y is a column vector depicting the wind speed time series, and n is the length of the time series. Note that the function fn minimized here is the negative of the loglikelihood function described by (A.2). The initial guess of the parameters is passed through a vector theta<-c(\alpha_0, \beta_0). The estimates (\hat{\alpha}, \hat{\beta}) can be accessed using $ operator as theta_est$estimate.

### A.2 Linear regression analysis in R

Linear regression aims to model a dependent variable Y as a function of independent variable X that follows an expression given as

\(Y = \phi_1 + \phi_2 X + v, \quad \text{(A.3)}\)

where \phi_1, \phi_2, and v are the intercept, slope, and error terms for the regression model. Let us study how to carry out a simple linear regression in R. We take a data set Y as wind speed for a particular region and X as wind direction to see dependence of wind speed on wind direction and analyze error metrics. The data for wind speed and wind direction are collected from a wind farm Bishop & Clerks in USA. The scatter plot for 50 data points is illustrated in Fig. A.4. Further, Table A.1 depicts the first 10 data-points for wind speed and wind direction. The data can be imported in R workspace via .xlsx file as described in an earlier section.
