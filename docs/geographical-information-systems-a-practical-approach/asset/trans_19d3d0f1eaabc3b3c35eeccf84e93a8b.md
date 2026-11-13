

the relationship between the dependent and independent variables is linear, but only partial relationships are dealt with, not precise mathematical ones, and the residuals have a normal distribution and are independent of each other, with no autocorrelation. Multiple regression also assumes that the independent variables are not significantly correlated with one another – that is, there is no multicollinearity among the independent variables. If there is significant multicollinearity, the variance of the estimated regression coefficients will become inflated, which may make insignificant independent variables to appear significant. The severity of multicollinearity can be quantified using the **variance inflation factor** (VIF). VIF is calculated for each independent variable as follows:

$VIF_i = \frac{1}{1 - R_i^2}$ (6.41)

where $VIF_i$ is the VIF for independent variable $x_i$, and $R_i^2$ is the multiple coefficient of determination associated with the regression of $x_i$ (taken as the dependent variable) on all other independent variables. As a rule of thumb, a VIF of greater than 7.5 suggests high multicollinearity – an indication of potential multicollinearity problems. The square root of VIF also indicates how much larger the standard error is compared with what it would be if that variable was uncorrelated with the other independent variables.

Whether or not the residuals from a regression model are normally distributed is tested using the Jarque–Bera test statistic (Jarque and Bera 1987). The null hypothesis for this test is that the residuals are normally distributed. When the p-value for the test is less than the significance level, $H_0$ is rejected and the residuals are not normally distributed, indicating the regression model is biased. If the residuals are also spatially autocorrelated, the bias may result from missing one or more key independent variables. The spatial autocorrelation of the residuals can be tested using global Moran's I.

A multivariate geographical problem may involve a large number of variables. It is not necessary to include all possible variables in a multiple regression equation. Which variables should be included or excluded is decided mainly based on domain knowledge, practical considerations and, sometimes, common sense. Determination of the best multiple regression equation relies on the assessment of the statistical significance of the regression equation and individual coefficients, adjusted $R^2$, VIF and some other statistical measures. Generally, a regression equation can be selected when it has overall significance determined by the p-value. For a given number of independent variables, the equation with the largest value of adjusted $R^2$ should be selected. Insignificant variables and variables with high multicollinearity (VIF >7.5) need to be weeded out. Therefore, a multiple regression equation can be constructed step by step, by testing one independent variable at a time and including it in the regression model if it is statistically significant, or by including all potential independent variables in the equation and removing those that are not statistically significant. Practical 6.8 shows how to use these principles to find a regression equation to model the relationship between annual average temperature, elevation and aspect.

**Practical 6.8 See the Support Material**

In this practical, you are going to learn regression analysis in ArcGIS Pro or QGIS.

### 6.6.3 Geographically Weighted Regression

Conventional regression analysis creates a single regression equation to represent the relationship between a dependent variable and a number of independent variables based on the assumption that the relationship is static and consistent across the whole study area. In other words, a conventional simple or multiple regression equation is a global model in which the regression coefficients are considered to be constant over space. However, in geographical analysis, these parameters may themselves be a function of geographical location because the form and strength of relationships among the variables could be different across space. The results of conventional regression will not capture the true nature of spatially varying relationships between a geographical phenomenon and the influencing factors. **Geographically weighted regression** (GWR) was developed to overcome this limitation (Fotheringham et al. 2002).

GWR extends ‘global’ multiple regression by producing a set of local parameter estimates for each relationship at every data point in a region. Essentially, it estimates a linear regression equation at every data location with varying regression coefficients.

A GWR local regression equation can be written as:

\(\hat{y}_i = a_i + b_{i1}x_{i1} + b_{i2}x_{i2} + ... + b_{ik}x_{ik}\) (6.42)

where \(k\) is the number of independent variables, \(\hat{y}_i\) is the predicted value of the dependent variable \(y\) at location \(i\), \(a_i\) and \(\{b_{ij} | j=1, 2, ..., k\}\) are the regression coefficients at location \(i\) and \(x_{ij}\) is the observed value of the independent variable \(j\) at location \(i\). Therefore, the regression equation is specific to the location of data point \(i\).

A local regression equation at location \(i\) is estimated through weighting all surrounding observations by a function of distance from location \(i\) – that is, each observation is assigned a weight representing the influence of the observed value on the value at location \(i\) to be estimated. The observations closer to location \(i\) get larger weights than those further away. The weights can be determined by several methods. The simplest way is to define the weights as:

\(w_{ij} = \begin{cases} 1 & \text{if } d_{ij} \le d \\ 0 & \text{otherwise} \end{cases}\) (6.43)

where $w_{ij}$ is the weight assigned to observation or sample point $j$ for estimating a regression equation at location $i$, $d_{ij}$ denotes the distance from location $i$ to sample point $j$ and $d$ is a distance threshold value.

With the preceding weighting method, any observation further than distance $d$ from location $i$ is considered to have no influence on location $i$ and is excluded from estimating a regression equation for location $i$. All the observations within $d$ from location $i$ have equal weights. However, this method suffers from the problem of discontinuity. The regression coefficients at different locations may change considerably, particularly when the density of sample points differs greatly around those locations. One way to address this is to define weights using a continuous weighting function known as a *kernel*. A typical **kernel function** is:

\(\omega_{il} = e^{-\left(\frac{d_{il}}{h}\right)^2}\) (6.44)

where $h$ is a quantity known as the bandwidth. This function represents a Gaussian curve. The weight at location $i$ is 1, where $i=l$ and $d_{il}=0$. The weights of other data points decrease according to a Gaussian curve as the distance between $i$ and $l$ increases. When $d_{il}$ increases to a certain distance, the weights will become virtually zero, effectively excluding these observations from the estimation of regression coefficients for location $i$. The bandwidth in the kernel is expressed in the same units as the coordinates used in the data. When a very large bandwidth is selected, the weights approach 1 and the *local* GWR model becomes a conventional *global* regression model.

The Gaussian kernel expressed in equation 6.44 uses a fixed bandwidth $h$. It is suitable for use when the sample points are reasonably regularly spaced in the study area. However, when the sample points are not regularly spaced, it is expected that relatively small bandwidths are used in areas where the sample points are densely distributed, and relatively large bandwidths used where the sample points are sparsely distributed. One way of implementing this adaptive bandwidth approach is to specify the exact same number of sample points to be included in the local bandwidth of a kernel for estimation at each location. The following weighting function is such an adaptive kernel, called the bisquare kernel:

\(\omega_{il} = \left\{ \begin{array}{ll} \left[ 1 - \left( \frac{d_{il}}{h_i} \right)^2 \right]^2 & if \ d_{il} \le h_i \\ 0 & otherwise \end{array} \right.\) (6.45)

where $h_i$ is the bandwidth set to include the $p$ observations nearest to location $i$, assuming $p$ is the specified number of sample points to be included.

The bandwidth may be optimised by minimising the cross-validated sum of squared errors, denoted as:

\(CV(h) = \sum_{i=1}^{n} \left[ y_i - \hat{y}_{\neq i}(h) \right]^2\) (6.46)

where $y_i$ is the observed value of $y$ at location $i$, and $\hat{y}_{\neq i}(h)$ is the predicted value of $y$ at location $i$ made using a specific value of $h$ when observation $i$ is not used in the estimation (Brunsdon et al. 1998). Observation $i$ is omitted from the calculation so

