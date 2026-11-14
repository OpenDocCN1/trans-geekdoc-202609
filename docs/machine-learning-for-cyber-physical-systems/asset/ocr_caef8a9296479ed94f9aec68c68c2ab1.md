ML model to describe the relationship between the input and output parameters. Upper and lower boundaries for the allowed input parameter variations are defined as stated in Table 1. Boundaries for the quality criteria have to be defined as well. These depend on the type of component that is produced. The focus can be on maximum component hardness or for example on the maximum thickness of the finished component. As we focus on a part from the automotive industry we want to maximize/increase both, the sheet thickness and hardness at critical points which are prone to tearing. Thus, no upper boundaries for P1H and P2ST were defined.

Table 1. Process parameters, quality criteria, and regression coefficients for the estimation of P1H and P2ST.

| Variable | lower boundary | upper boundary | default | coefficients P1H | coefficients P2ST |
|---|---|---|---|---|---|
| ST [mm] | 1.45 | 1.55 | 1.5 | - | 9.4 x 10^-1 |
| STemp [°C] | 900 | 950 | 900 | 1.1 | - |
| TT [s] | 5 | 55 | 5 | -6.2 | 4.9 x 10^-4 |
| ToTemp [°C] | 80 | 300 | 190 | -7.4 x 10^-2 | -5.3 x 10^-6 |
| QF [kN] | 500 | 2,500 | 2,000 | 3.5 x 10^-6 | -1.3 x 10^-9 |
| QT [s] | 2 | 65 | 2 | 3.3 x 10^-1 | -1.2 x 10^-4 |
| Sp [mm] | 0.1 | 2 | 1.05 | 1.1 | 2.4 x 10^-3 |
| Intercept | | | | -4.5 x 10^2 | 6.2 x 10^-2 |
| P1H [HV] | 390 | | | | |
| P2ST [mm] | 1.43 | | | | |

# 3.2 Linear Regression for Quality Prognosis

Description of the Model Ultimately, we aim for on-line process control which makes the application of high speed models and fast predictions necessary. As a first step – conducted off-line – we need to describe the relationship between input and output variables in a distinguishable way. A general linear model which accounts for the single parameters linear effects was considered. In general, a linear regression equation has the following form

```
DepVar = a + (b1 x IndepVar1) + ... + (bn x IndepVarn).
```

Where a, b1, ..., bn are unknown parameters, DepVar stands for dependent variable and represents the qualities P1H and P2ST, respectively. IndepVar's are the independent variables, such as the process parameters.

The analysis is carried out in R using the lm() function for fitting linear models independently for the two quality parameters P1H and P2ST. The resulting regression coefficients are shown in Table 1.