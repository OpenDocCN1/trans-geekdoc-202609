# 10.5 Poisson Regression for Rate

```
## 2 cigar_day 1.07 0.00640 10.1 8.79e-24 1.05e+0 1.08e+0
## 3 smoke_yrs20-24 2.62 1.15 0.833 4.05e-1 3.35e-1 5.29e+1
## 4 smoke_yrs25-29 5.53 1.08 1.58 1.13e-1 9.44e-1 1.05e+2
## 5 smoke_yrs30-34 24.7 1.02 3.14 1.67e-3 5.23e+0 4.42e+2
## 6 smoke_yrs35-39 25.6 1.02 3.17 1.54e-3 5.35e+0 4.59e+2
## 7 smoke_yrs40-44 67.2 1.01 4.15 3.30e-5 1.46e+1 1.19e+3
## 8 smoke_yrs45-49 85.5 1.03 4.27 1.22e-5 1.83e+1 1.52e+3
## 9 smoke_yrs50-54 113.5 1.02 4.80 1.60e-6 2.83e+1 2.38e+3
## 10 smoke_yrs55-59 213. 1.02 5.25 1.52e-7 4.51e+1 3.86e+3
```

export it to .csv_file

```
write.csv(tib_pois_case, "tib_pois_case.csv")
```

We now present the model equation, which unfortunately this time quite a one.

```
round(summary(pois_case_final)$coefficients, 2)
```

```
Estimate Std. Error z value Pr(|z|)
## (Intercept) -11.32 1.01 -11.23 0.00
## cigar_day 0.06 0.01 10.05 0.00
## smoke_yrs25-29 1.71 1.08 1.58 0.11
## smoke_yrs20-24 0.96 1.15 0.83 0.40
## smoke_yrs35-39 3.24 1.02 3.17 0.00
## smoke_yrs30-34 3.21 1.02 3.14 0.00
## smoke_yrs40-44 4.21 1.01 4.15 0.00
## smoke_yrs45-49 4.45 1.02 4.37 0.00
## smoke_yrs50-54 4.89 1.02 4.80 0.00
## smoke_yrs55-59 5.37 1.02 5.25 0.00
```

and put the values in the equation. Remember to include the offset in the equation.

```
ln(case) = ln(person_yrs) - 11.32 + 0.06 * cigar_day
+ 0.96 * smoke_yrs(20 - 24) + 1.71 * smoke_yrs(25 - 29)
+ 3.21 * smoke_yrs(30 - 34) + 3.24 * smoke_yrs(35 - 39)
+ 4.21 * smoke_yrs(40 - 44) + 4.45 * smoke_yrs(45 - 49)
+ 4.89 * smoke_yrs(50 - 54) + 5.37 * smoke_yrs(55 - 59)
```