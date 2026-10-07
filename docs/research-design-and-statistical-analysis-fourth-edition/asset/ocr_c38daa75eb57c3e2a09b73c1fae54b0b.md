> AnovaCl(data = datM, BDI_transform ~ health + activity + education, type=3)
Anova Table (Type III tests)

Response: BDI_transform
Sum Sq Df F value Pr(>F)
(Intercept) 13.819 1 27.3986 8.425e-07 ***
health 15.676 1 31.0788 1.903e-07 ***
activity 6.538 1 43.0016 0.0004628 ***
education 1.102 1 2.1853 0.142302
Residuals 53.465 106

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * ' ' 1

> AnovaCl(data = datW, BDI_transform ~ health + activity + education, type=3)
Anova Table (Type III tests)

Response: BDI_transform
Sum Sq Df F value Pr(>F)
(Intercept) 36.759 1 36.0197 2.79e-08 ***
health 8.921 1 8.7420 0.003827 **
activity 4.897 1 4.7987 0.030652 *
education 4.288 1 4.2016 0.042831 *
Residuals 109.195 107

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * ' ' 1

> AnovaCl(data = datM, BDI_transform ~ activity), type=3)
Anova Table (Type III tests)

Response: BDI_transform
Sum Sq Df F value Pr(>F)
(Intercept) 36.658 1 552.5609 < 2.2e-16 ***
activity 8.54 1 12.9098 0.0004943 ***
Residuals 71.47 108

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * ' ' 1

> AnovaCl(data = datW, BDI_transform ~ activity), type=3)
Anova Table (Type III tests)

Response: BDI_transform
Sum Sq Df F value Pr(>F)
(Intercept) 478.050 1 417.1795 < 2e-16 ***
activity 7.220 1 6.2863 0.01364 *
Residuals 124.900 109

Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * ' ' 1

Figure 25.1 ANCOVA results from R for the Activity experiment for participants identifying as men (Panel a) and as women (Panel b), and the ANOVA results for men (Panel c) and women (Panel d).