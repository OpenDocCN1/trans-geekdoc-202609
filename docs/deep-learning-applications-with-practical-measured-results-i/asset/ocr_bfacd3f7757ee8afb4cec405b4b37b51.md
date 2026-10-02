acquisition unit. The temperature and humidity test chamber was adjusted, and the points near the preset value were observed and recorded. The experimental principle is shown in Figure 1.

![](bbox=[0.26, 0.2, 0.75, 0.3])

Figure 1. Error experiment of humidity sensor at different temperatures.

The humidity-sensitive capacitive sensor was placed in the temperature and humidity regulating chamber. The humidity was set to 10% RH, and the temperature was changed. After the temperature was stabilized, the measured value of the humidity sensor was read. The humidity was set to 30% RH, 50% RH, 70% RH and 90% RH, and the above steps were repeated. The measuring error curve of the humidity sensor at different temperatures was obtained as shown in Figure 2.

![](bbox=[0.25, 0.46, 0.7, 0.68])

Figure 2. Measured error curve of the humidity sensor at different temperatures.

From the error curve of Figure 2, it can be seen that the error of the humidity sensor obviously increases in low and high temperature regions and has nonlinear characteristics. The original measurement value of the sensor was compensated according to different ambient temperatures, such that the compensated value was close to the standard value. Setting the ambient temperature T, the relationship between the original measured value of the humidity sensor H_I and the compensated humidity value H_C is Equation (1).

$H_C = f(H_I, T)$
(1)

$H_C$ and $T$ are both single-valued functions of $H_I$, then the inverse function $H_I = f^{-1}(H_C, T)$ exists. So the introduced influence parameter $T$ and the measured value $H_I$ were used as data to be compensated, and the regression analysis was performed by the binary linear regression function. The regression effect and the value of the segmentation point $T_1$, $T_2$ were determined based on the value of the coefficient of determination $R^2$. The least squares method and GSA-BP neural network were