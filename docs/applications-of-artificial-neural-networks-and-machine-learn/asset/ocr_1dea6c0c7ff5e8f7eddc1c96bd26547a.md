(ANOVA) decomposition of the developed MARS models based on both with piece-wise linear and cubic segments is presented in Table 20.5. The first column lists the number of ANOVA function. The second column gives the standard deviation of the corresponding ANOVA functions. This gives one indication of the relative contribution of each function to the overall model performance. The third column provides another indication of the importance of the corresponding ANOVA function, by listing the GCV score for a model with the whole basis functions compared to a model in which that particular ANOVA function is removed. This can be used to judge whether this ANOVA function makes an important contribution to the model performance, or whether it slightly improves the global GCV score. The last column gives the particular predictor variables associated with that ANOVA function [34]. This ability of MARS can be applied to determine the most important parameters in prediction of bond strength of EBR FRP systems.

In Fig. 20.9, the relative importance of the input parameters for the developed MARS models based on ANOVA analysis is depicted. The relative importance of each input parameter was determined based on the increase of GCV value that caused by removing the considered variables from the developed MARS model. For example, according to the Table 20.5, the ANOVA functions with parameters of $b_p$ and $b_p/b_m$ remarkably improved the amount of GCV values. Therefore, it can be expected that these parameters have remarkable contribution in developing prediction models for bond strength. As graphically shown in the Fig. 20.9, $b_p/b_m$ and $b_p$ were the most important parameters in the developed MARS models and $L_b$, $f_{mt}$, and $E_p t_p$ were the other important parameters, respectively.

| Func. | STD Linear | STD Cubic | GCV Linear | GCV Cubic | Variable(s) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 2812.925 | 49.643 | 11,572,307.35 | 3607.591 | $b_p/b_m$ |
| 2 | 1.242 | 2.122 | 12.99 | 33.324 | $f_{mt}$ |
| 3 | 0.759 | 0.961 | 5.415 | 8.992 | $E_p t_p$ |
| 4 | 5.647 | 5.213 | 105.579 | 87.188 | $b_p$ |
| 5 | 4.032 | 3.169 | 32.75 | 29.965 | $L_b$ |
| 6 | 2817.19 | 52.778 | 11,038,785.57 | 3922.107 | $b_p/b_m, b_p$ |
| 7 | 1.904 | 1.454 | 9.351 | 14.589 | $b_p/b_m, L_b$ |
| 8 | 1.111 | 1.505 | 6.018 | 10.967 | $f_{mt}, b_p$ |
| 9 | 4.832 | 4.555 | 47.506 | 54.292 | $f_{mt}, L_b$ |
| 10 | 2.038 | 1.848 | 10.11 | 12.049 | $f_{mt}, b_p/b_m, L_b$ |
| 11 | 1.35 | 0.384 | 6.929 | 7.618 | $f_{mt}, b_p/b_m, L_b, E_p t_p$ |