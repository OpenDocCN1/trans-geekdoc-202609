temperature value at this time is the temperature segmentation points T₁, T₂, which are 22.36 and 29.98, respectively.

+   3. Determine whether the interval of the temperature segmentation point is greater than 5. The experimental data satisfy this condition; therefore, segmentation compensation is made. The least squares method is used for linear fitting of the temperature range [22.36, 29.98]. Taking the straight line fitting effect of 30% RH as an example, the fitted straight line is: ε = −0.2695T + 4.4723, where ε is the compensation value, and T is the temperature value. When the value of measured humidity is 30% RH, input the value of temperature and obtain the corresponding humidity compensation value, then add the measured value to obtain the compensated value.
4. Use GSA to optimize the weight and threshold of the BP neural network, train the neural network, and compensate the data in the nonlinear interval.
5. The compensation function model is shown in Figure 9. The compensation effect diagram is shown in Figure 10. It can be seen from Figure 10 that the compensated humidity value has a good linear relationship with the standard humidity such that the measured value is closer to the true value.

![](bbox=[0.22, 0.48, 0.78, 0.68])

Figure 9. Compensation function model.