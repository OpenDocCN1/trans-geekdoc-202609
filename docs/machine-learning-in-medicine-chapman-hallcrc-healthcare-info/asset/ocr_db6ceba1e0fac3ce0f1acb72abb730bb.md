where \( t^{l} \), \( t^{r} \), \( a^{l} \) and \( a^{r} \) are the four learnable real number parameters (initialized as \( a^{l} \)=0, \( t^{l} \)=0, and \( t^{r} \)=maxInput, where maxInput is a hyper-parameter). SReLU's rather large number of parameters results in high representation power.

The gradients of SReLU are given by

![](bbox=[0.34, 0.24, 0.67, 0.33])

![](bbox=[0.34, 0.35, 0.76, 0.4])

![](bbox=[0.34, 0.42, 0.62, 0.49])

# ### 5.2.7 APLU

Adaptive Piecewise Linear Unit (APLU) [21] is defined as

![](bbox=[0.3, 0.61, 0.75, 0.64])

where \( a_{c} \) and \( b_{c} \) are real numbers, each different for each channel of the input. APLU is a linear piecewise function able to approximate, as noted in the Introduction, any continuous function on a compact set.

The gradient of APLU is given by the sum of the gradients of ReLU and of the functions contained in the sum. With respect to the parameters, \( a_{c} \) and \( b_{c} \), the gradients are

![](bbox=[0.19, 0.82, 0.78, 0.87])

In this study, the parameters \( a_{c} \) were initialized to 0, while the points were randomly initialized. Added was a 0.001 \( L^{2} \)-penalty on the norm of the