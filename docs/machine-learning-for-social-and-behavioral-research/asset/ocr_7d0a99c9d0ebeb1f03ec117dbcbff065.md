# Machine Learning with Mixed-Effects Models

```
$$\hat{y}_i = b_0 + \sum_{k=1}^{M} b_k(x_i - \tau_k)^*$
```

where $(x_i - 	au_k)^*$ is either the negatively truncated function $(x_i - 	au_k)^-$ or the positively truncated function $(x_i - 	au_k)^+$, $	au_k$ is the $k$th knot point, and $b_k$ is the regression coefficient.

Going beyond the MARS, a number of variations on splines exist. First, there are cubic splines, natural cubic splines, restricted cubic splines, and smoothing splines with greater flexibility and smooth transitions at the knot point (see Harrell (2015) and Wang (2011) for more detail). Second, and relevant for this chapter is that spline models can be integrated into more complex models, such as mixed-effects models by allowing for inclusion of random effects (Zhang, 1997, 1999, 2004). Zhang and He's (2009) MASAL algorithm combines linear mixed-effects models with the MARS algorithm to search for nonlinearity in associations between observation-level variables through the use of piecewise splines. The MASAL algorithm was available in $\mathbb{R}$ through the *masal* package, but the package is no longer available. However, a stand-alone version of the algorithm is available at https://publichealth.yale.edu/c2s2/software/masal/

# 9.6.2 Generalized Additive Models

Generalized additive models (GAMs; Hastie & Tibshirani, 1986; Wood, 2017) fit a sum (the additive piece) of smooth functions, with the smooth function able to take on a number of flexible forms, including splines (smoothing, linear, cubic, etc.). GAMs take the general form of

```
$$\hat{y}_i = f_1(x_1) + f_2(x_2) + f_3(x_1,x_2) + f_4(x_3) + f_5(x_1,x_3) + f_6(x_2,x_3) + f_7(x_1,x_2,x_3) + ...$$
```

where each smoothing function $f()$ can take one of many forms and include either a single variable or multiple variables. The main distinction between GAMs and MARS is in the use of splines, which typically account for nonlinearities with smooth functions as opposed to only piecewise splines. This leads to a higher degree of complexity in GAMs compared to piecewise splines. The choice between the algorithms typically rests with the researcher to determine whether smooth or rough transition points make more theoretical sense.

GAMs have been extended in multiple ways. For example, GAMs can include autoregressive parameters (Bringmann et al., 2017) and the have been used for single-case designs (Sullivan, Shadish, & Steiner, 2015).