![](bbox=[0.146, 0.098, 0.862, 0.298])

![](bbox=[0.146, 0.312, 0.862, 0.512])

![](bbox=[0.146, 0.526, 0.862, 0.726])

Figure 8.12 Wind forecasting for $WT_5$ with and without GRA for dataset D2.

20% (100 data points) were used for testing. For dataset D2, the effective wind speed for wind turbine $WT_5$ is calculated based on Jensen's and Frandsen's models, and GRA is done for inputs $u_{15}$, $u_{35}$, and $u_{45}$. Based on the GCD rankings, we select $u_{35}$ as the input to the SVR model along with decomposition signals using the wavelet transform. The RMSE values for