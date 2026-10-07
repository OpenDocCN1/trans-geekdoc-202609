# 216 ■ Machine Intelligence

![](bbox=[0.125, 0.116, 0.874, 0.513])

**Figure 11.2** Class distribution (dependent variable) of gastric cancer gene dataset.

[AB006782_at, 'AC00207_at', 'D26129_at', 'D38535_at', 'D42047_at', 'D78134_at', 'D87742_at', 'HG3162-HT3339_at', 'J03915_s_at', 'J04982_at', 'J05412_at', 'J07590_at', 'L1344_at', 'L32179_at', 'L41668_mal_at', 'L6628_s_at', 'L76465_at', 'M12759_at', 'M21812_at', 'M31328_at', 'M61855_at', 'M6628_s_at', 'M63154_at', 'M74542_at', 'S68616_at, S69232_at, U05259_mal_at, U15177_at, U19948_at, U21931_at, U26424_at, U27325_s_at, U57094_at, U59752_s_at, U66052_at, U66702_at, U70663_at, U79288_at, U83461_at, X05049_at, X05997_at, X51698_s_at, X52003_at, X53961_at, X58529_at, X66839_at, X69220_s_at, X76223_s_at, X76342_at, X96752_at, Z29754_at]

**Figure 11.3** List of top 50 features selected by ANOVA method.

categorical, the label encoder is used to convert the values to numeric. The number of features is huge, many of the features do not provide much relevant to the study. Hence, the Feature Selection is employed using Analysis of Variance (ANOVA) to select the top 50 features which will be used to model (Figure 11.3). The top 50 features selected by the ANOVA method are passed as an independent feature to the four supervised machine learning classification models such as LR, DT, NB, and KNN. The performance metrics, namely Accuracy,