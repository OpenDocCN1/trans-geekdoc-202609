![](bbox=[0.125, 0.08, 0.875, 0.365])

Fig. 20.5 The variations of $F_{max}$ with input variables for different classes

# ## 20.4.4 The MARS Model

As stated in Sect. 20.3, the segments (splines) of the MARS algorithm can be either piecewise linear or cubic segments. In this study, both segments are used to develop model; but the developed model based on piecewise linear segment, which had better performance, is only presented. After presenting training data set to MARS algorithm, the following equation for maximum bond strength is derived:

```
$F_{max}(kN) = 17 - 0.71 \times BF_1 - 1.2 \times BF_2 + 0.25 \times BF_3 - 0.076 \times BF_4$\n$+ 3.8 \times 10^3 \times BF_5 - 0.019 \times BF_6 - 0.94 \times BF_7 + 0.118F_8 + 0.067BF_9$\n$- 7.5 \times 10^4 BF_{10} + 3.7 \times 10^3 BF_{11} - 3.8 \times 10^3 BF_{12} - 3BF_{13}$\n(20.19)
```

The basis functions (BFs) and their corresponding equations are listed in Table 20.2. It should be noted that, from Table 20.2, that of 14 BFs, 12 BFs with interaction terms are integrated in this model, indicating that the model is not simply additive and that interaction terms play a significantly important role. The final model of MARS (Eqs. (20.18a–20.18d)) is achieved via GCV obtained from forward selection and backward deletion process. As observed, one of the advantages of MARS algorithm is that not only captures complex relationships between independent and dependent variables but also does not require additional effort to verify a prior assumption about the relationship between the set of independent variables and the dependent response variable. The latter feature becomes more important as the dimension of the problem increases.