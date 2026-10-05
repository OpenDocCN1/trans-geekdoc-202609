this interval is divided into three segments, $[x_{start}, x_1]$, $[x_1, x_2]$ and $[x_2, x_{end}]$. In each segment, a linear or nonlinear approximate is designed, which is called a spline function. The final approximate to an unknown function is defined as below, where $f_1(x), f_2(x)$ and $f_3(x)$ are three approximate functions for three segments.

```
s(x) = \begin{cases} f_1(x) & x \in [x_{start}, x_1] \ f_2(x) & x \in [x_1, x_2] \ f_3(x) & x \in [x_2, x_{end}] \end{cases}
```

For a multivariate regression problem, a GAM model can be re-written as below, where K is the number of independent variables, $x_i$ is the $i^{th}$ independent variable and $eta_i$ is its spline coefficient,

```
y = \beta_0 + \sum_{i=1}^{K} \beta_i s(x_i) + \varepsilon
```

GAM has also been applied to biological/medical research. For instance, it has been applied to examine how the heat stress impact on dairy cows [Benni, et al., 2020] and used in a haemorrhagic fever research [Zhang, et al., 2019].

There is an R package called gam for using GAM in that package and its format is shown below, where df function is also named as gam and df is the degrees of freedom for a spline function

```
gam(y~s(x, df), ...)
```

To create the confidence bands for a GAM model, the predict function should be called, in which a constructed GAM model (model) is used as the first input.

```
predict(model, type='link', se.fit=TRUE)
```

GAM employs the Akaike information criterion (AIC) [Akaike, 1981] for model optimisation, i.e., selecting the order (degrees of freedom) of splines employed in a model. Figure 4.15 shows an example of using this function for a nonlinear regression problem with three different degrees of freedom (being 3, 5 and 7), where the confidence bands and AIC values