
| 6 || 5.4 || 3.9 || 1.7 || 0.4 |

## Principal Components Regression

We now run the principal components regression model:

```
> pcr_model <- pcr(Sepal.Length~., data = iris.2, scale = TRUE, validation = “CV”)
```

In the model statement, `Sepal.Length~.` implies the response as a function of all other variables in the `iris` data, and `scale = TRUE` requests the data to be standardized. The statement `validation = “CV”` requests cross-validation on the model. To request leave-one-out cross-validation specifically, one would code `validation = “LOO”`:

We obtain a summary:

```
> summary(pcr_model)
Data: X dimension: 150 3
     Y dimension: 150 1
Fit method: svdpc
Number of components considered: 3
VALIDATION: RMSEP
Cross-validated using ten random segments.
```

|  || (Intercept) || 1 comps || 2 comps || 3 comps |
| --- | --- | --- | --- | --- |
| CV || 0.8308 || 0.5432 || 0.3867 || 0.3177 |
| --- | --- | --- | --- | --- |
| adjCV || 0.8308 || 0.5429 || 0.3865 || 0.3173 |

```
TRAINING: % variance explained
```

|  || 1 comps || 2 comps || 3 comps |
| --- | --- | --- | --- |
| X || 74.05 || 98.84 || 100.00 |
| --- | --- | --- | --- |
| Sepal.Length || 57.97 || 78.47 || 85.86 |

The `CV` number is the cross-validation, whereas the `adjCV` is a bias-corrected CV estimate ([Mevik & Wehrens, 2024](#ref.xhtml#re_CIT000249), p. 5). `RMSEP` is the root mean-squared error of prediction. We also see the % variance explained increasing with the number of components (up to three), as it should. We can plot the `RMSEP` for sepal length on those components ([Figure 5.8](#c5.xhtml#f5.8)):251

![Figure 5.8 RMSEP as a function of number of components. CV and adjCV are virtually the same on this data (the overlap may be difficult to see in the plot).Return to text.⏎](images/fig5.8.jpg)

*Figure 5.8* RMSEP as a function of number of components. CV and adjCV are virtually the same on this data (the overlap may be difficult to see in the plot).[Return to text.⏎](#c5.xhtml#re_f5.8)

```
> plot(RMSEP(pcr_model), legendpos = “topright”)
```

We can clearly see that `RMSEP` decreases as the number of components increases, which makes intuitive sense. We could have obtained the above plot through the following code as well (output not shown), where `val.type = “MSEP”` is also requested, where `MSEP` = mean-squared error of prediction:

```
> validationplot(pcr_model)
> validationplot(pcr_model, val.type=“MSEP”)
> predplot(pcr_model)
> coefplot(pcr_model)
```

The `predplot()` function reveals a plot ([Figure 5.9](#c5.xhtml#f5.9), left) of predicted values against measured (observed) values for the case of three components. The right plot in [Figure 5.9](#c5.xhtml#f5.9) plots the regression coefficients for each predictor, where `coef(pcr_model)` will yield the corresponding coefficients for sepal width (variable = 1), petal length (variable = 2) and petal width (variable = 3):252

![Figure 5.9 Plot of predicted values against measured values (left). Plot of regression coefficients against each predictor (right).Return to text.⏎](images/fig5.9.jpg)

*Figure 5.9* Plot of predicted values against measured values (left). Plot of regression coefficients against each predictor (right).[Return to text.⏎](#c5.xhtml#re_f5.9)

## 5.13 Partial Least-Squares Regression

Whereas principal components regression only uses `x[1]` through `x[p]` in its construction of components, partial least-squares seeks out dimensionality or directions in the data that incorporates both the predictors and the response variable. That is, the components found in `x[1]` through `x[p]` are not just relevant to the predictor side, but are also relevant to the response `y`. Partial least-squares, or “PLS” for short, is often considered a supervised alternative to principal components regression ([James et al., 2013](#ref.xhtml#re_CIT000168)) since `PLS` will incorporate the response when determining the best “directions.”

As well described by Izenman,

> PLS searches for a set of components (called latent vectors) that performs a simultaneous decomposition of `X` and `Y` with the constraint that these components explain as much as possible of the covariance between `X` and `Y`. In this manner, the derived variables in PLS are constructed in such a way as to retain most of the information in the `X[1]` through `X[p]` variables and is typically obtained via algorithm rather than optimization procedure ([Izenman, 2008](#ref.xhtml#re_CIT000167), p. 133).

To unpack what PLS actually accomplishes, recall once more what a linear combination looks like in the typical PCA:

`z[1] = e[1]x[1] + e[2]x[2] + ... + e[p]x[p]`

In PLS, the coefficients in `z[1]`, those of `e[1]`, etc., are set to the coefficients resulting from a simple linear regression of `y` on `x` for each predictor. This coefficient (e.g., for `e[1]`) is proportional to the correlation between `y` and `x[j]`, the given predictor we are considering. That is, in computing the first component, variables `x` that are most strongly related to `y` (in a univariate sense) receive the most weight.

To obtain the second component, `z[2]`, each of the variables for `z[1]` are first adjusted by regressing each variable on `z[1]` and taking residuals of what is “left over.” If the first component accounts for all the information in the predictors, the residual will equal zero. More than likely, the first 253component will not account for all information, and hence the residual will be greater than zero. The second component `z[2]` is computed using these residuals, which are orthogonal to the first component. The iterative approach continues for ensuing directions (i.e., components) of `z`.

It is clear then why the method is referred to as partial least-squares. It is so because it capitalizes on residuals that are orthogonal to previous component values. Hence, if PLS could talk, it would say, “After the predictive part is removed (or ‘partialled’), let’s now regress the new component on what is left over.” Partial least-squares, as is true of principal components regression, is not scale-invariant, and hence standardizing predictors is often advised. However, as noted elsewhere in the book, the decision to standardize should not be made without careful consideration of the nature (and specifically, scales) of the variables under study.

### 5.13.1 Partial Least-Squares in R

The `caret` package ([Kuhn](#ref.xhtml#re_CIT000208), 2008) allows us to fit a variety of models, including that of partial least-squares. The following is a partial least-squares discriminant analysis where the response variable is binary:

```
> library(caret)
> library(mlbench)
> data(Sonar)
```

We print only a few variables and cases of the data:254255

```
> head(Sonar)
```

|  || V1 || V2 || V3 || V4 || V5 || V6 || V7 || V8 || V9 || V10 || V11 || V12 || V13 || V14 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 0.0200 || 0.0371 || 0.0428 || 0.0207 || 0.0954 || 0.0986 || 0.1539 || 0.1601 || 0.3109 || 0.2111 || 0.1609 || 0.1582 || 0.2238 || 0.0645 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2 || 0.0453 || 0.0523 || 0.0843 || 0.0689 || 0.1183 || 0.2583 || 0.2156 || 0.3481 || 0.3337 || 0.2872 || 0.4918 || 0.6552 || 0.6919 || 0.7797 |
| 3 || 0.0262 || 0.0582 || 0.1099 || 0.1083 || 0.0974 || 0.2280 || 0.2431 || 0.3771 || 0.5598 || 0.6194 || 0.6333 || 0.7060 || 0.5544 || 0.5320 |
| 4 || 0.0100 || 0.0171 || 0.0623 || 0.0205 || 0.0205 || 0.0368 || 0.1098 || 0.1276 || 0.0598 || 0.1264 || 0.0881 || 0.1992 || 0.0184 || 0.2261 |
| 5 || 0.0762 || 0.0666 || 0.0481 || 0.0394 || 0.0590 || 0.0649 || 0.1209 || 0.2467 || 0.3564 || 0.4459 || 0.4152 || 0.3952 || 0.4256 || 0.4135 |
| 6 || 0.0286 || 0.0453 || 0.0277 || 0.0174 || 0.0384 || 0.0990 || 0.1201 || 0.1833 || 0.2105 || 0.3039 || 0.2988 || 0.4250 || 0.6343 || 0.8198 |
|  || V56 || V57 || V58 || V59 || V60 || Class |
