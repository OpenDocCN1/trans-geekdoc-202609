![](bbox=[0.16, 0.09, 0.86, 0.41])

Fig. 22.1 Matrix plot of input and output parameters

MNLR models are only valid for the ranges they trained and their performance is more acceptable in ranges which the density of data is more concentrated.

# 22.4.3 Derived Models

Following data division, training data set was presented to the GMDH, MARS, and MNLR algorithms for model training. The MARS model returned the following equation for concrete shear capacity:

```
v_u(kN) = 5.4 - 3.5 x BF_1 + 22 x BF_2 + 41 x BF_3 - 0.079 x BF_4 + 0.078 x BF_5
- 0.049 x BF_6 + 0.054 x BF_7 - 0.54 x BF_8 + 38 x BF_9 + 0.096 x BF_10
- 0.47 x BF_11 - 3.6 x BF_12 + 31 x BF_13 + 700 x BF_14 - 4100 x BF_15
- 16 x BF_16 - 15 x BF_17 + 1.7 x BF_18 + 4.3 x BF_19 - 0.09 x BF_20
- 0.79 x BF_21 - 23 x BF_22 - 0.15 x BF_23 + 0.48 x BF_24 + 17 x BF_25
+ 0.093 x BF_26 + 6.8 x 10^-5 x BF_27 + 2.4 x BF_28
```

Table 22.3 lists the BFs and their corresponding equations. It should be noted that, from Table 22.3, that of 28 BFs, 19 BFs with interaction terms are integrated in this model, indicating that the model is not simply additive and that interaction