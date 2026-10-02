used to compensate the different temperature intervals. The function of segmentation compensation is similar to Equation (2).

$$H_C = f(H_I, T) = \begin{cases} f_1(H_I, T), T \in [T_0, T_1] \\ f_2(H_I, T), T \in [T_1, T_2] \\ f_3(H_I, T), T \in [T_2, T_3] \end{cases} \tag{2}$$

Among these values, $T_0 \le T_1 \le T_2 \le T_3$, $f_2(H_I, T)$ is the compensation function of the temperature range with good linear regression effect. A simple and efficient least squares method was used for line fitting. $f_1(H_I, T)$ and $f_3(H_I, T)$ are compensated functions at low temperature and high temperature, respectively, and the GSA-BP neural network was used. The influence of temperature T was effectively reduced, and the measured data were approximated to the stand value of humidity. The overall idea of optimal compensation is shown in Figure 3.

![](bbox=[0.25, 0.42, 0.7, 0.48])

Figure 3. Compensation principle of humidity sensor.

# 3. Adaptive Segmentation Based on Multiple Linear Regression

For the humidity measurement errors at different temperatures, the key to improve the accuracy of compensation is to judge whether the segmentation compensation is necessary and find the best segmentation point. The linear regression method mainly determines how to obtain the best fitting line through the sample. The process is a mathematical optimization method, and it searches for the best function of data by minimizing the square of error [14]. In the regression analysis, two or more independent variables were included, and these independent variables can be approximated by a straight line. As seen from Figure 2, in the temperature experiment of the humidity sensor, there is a certain linear relationship between the measured error of humidity sensor and the temperature value in some intervals. The multivariate linear regression method can be used to analyze and compensate errors in linear intervals [15]. The regression model between the expected ideal humidity value, the measured value and the temperature was established. The coefficient of determination was calculated and whether it needed segmentation compensation according to its value was determined.

A multiple linear regression model for temperature compensation was established, such as Equation (3).

$$H_{Oi} = \beta_0 + \beta_1 H_{Ii} + \beta_2 T_i \tag{3}$$

where $H_{Oi}$ is the expected humidity value of the regression, $H_{Ii}$ is the measured value of the humidity sensor, $T_i$ is the value of the ambient temperature, $i$ represents the i-th group data, $i = 1,2,3\cdots n$, there are $n$ sets of data, and $\beta_0, \beta_1, \beta_2$ are the regression coefficients. The actual regression model can be expressed as Equation (4).

$$\hat{H}_{Oi} = \hat{\beta}_0 + \hat{\beta}_1 H_{Ii} + \hat{\beta}_2 T_i \tag{4}$$

where $\hat{\beta}_0, \hat{\beta}_1$ and $\hat{\beta}_2$ are the estimated values of $\beta_0, \beta_1$ and $\beta_2$, respectively. $\hat{H}_{Oi}$ is the estimated value of $H_{Oi}$, and the residual of them is $\varepsilon_i$. It can be known from the least squares method that $\hat{\beta}_0, \hat{\beta}_1$ and $\hat{\beta}_2$ should minimize the sum of squares of the residuals $\varepsilon_i$.

$$Q = \sum \varepsilon_i^2 = \sum (H_{Oi} - \hat{H}_{Oi})^2 = \sum (H_{Oi} - \hat{\beta}_0 - \hat{\beta}_1 H_{Ii} - \hat{\beta}_2 T_i)^2 \tag{5}$$