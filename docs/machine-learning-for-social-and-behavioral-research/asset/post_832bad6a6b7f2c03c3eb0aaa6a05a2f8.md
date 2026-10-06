
# Machine Learning for Social and Behavioral Research

**FIGURE 7.7.** Gaussian graphical model for the Grit data. Each edge represents the partial correlation between variables (nodes).

![](img/5047f0f064e22688ceb5d0cdfaf3e964_212_0.png)

factor models (Hallquist, Wright, & Molenaar, 2019), while some research has developed network loadings to further highlight the similarity across methods (Christensen & Golino, 2021), making the theoretical distinctions between graphical models and SEM less clear. In our data, the correlation between centrality and the item $R^2$ values (sum of all factor loadings to that variable) in the CFA model above were 0.82, and 0.91 when using the results from the EFA with two latent variables.

## 7.7 Summary

In this chapter, we discuss a number of ways and methods for assessing variables to be used as predictors. Notably absent was a discussion of error in the outcome variable. Similar approaches can be used as explained above if the outcome is a scale score, including modeling the latent variable representation in an SEM model (see Chapter 8). However, just with a single predictor variable, there is no way to overcome the error in an outcome variable when the aim is prediction. Finally, it is almost always preferable to use the individual items as opposed to scale scores when maximizing predictive performance is the goal. Along with this, we recommend assessing the reliability of individual items and scales to provide additional information into why some items/scales were more important, or why prediction was lower than expected.

## Machine Learning and Measurement

### 7.7.1 Further Reading

- Reliability and validity are both complex topics, and have been written extensively. See Furr (2011) for an introductory textbook. For more recent discussions of validity, see Kane (2013) or Flake, Pek, and Hehman (2017), and for reliability, see McNeish (2018).

- We only briefly discussed a handful of SEM fit indices. This is an extremely broad topic, as dozens of indices have been developed to assess the fit of SEMs. See McNeish and Wolf (2021) as well as Golino et al. (2021) for recent developments in this area.

- Our coverage of variable network models was relatively scant despite a recent increase in development in this area. While much of the research in this area is focused on modeling longitudinal data (see Skkamp et al., 2018), see Isvorani Epskamp, Waldorf, and Borsboom (2022) and Borsboom et al. (2021) for recent reviews.

- While we briefly explored factor analysis, we recommend the book by Mulaik (2009) for more background, particularly from a technical perspective. For a more introductory textbook, see Beaujean (2014).

- To prevent an overoptimistic assessment of model fit when testing multiple MFA models (or PCA) from the aim of producing “final” CFA model, it is important to separate the data used to create the model, and the data used to estimate the model fit. We discuss this further in Chapter 8 for general SEM, but for scale or factor model development, we recommend Fokena and Greiff (2017).

## 7.7.2 Computational Time and Resources

Many of the methods detailed in the chapter involve modeling covariance matrices which can often be modeled relatively quickly (at most a few minutes). However, for many latent models that involve missingness, more complex constructs, or additional types of estimation, runtimes can be on the order of hours. For factor analysis and SEM, we recommend using both psych and lavaan packages in R, as they are both easy to use and have developed extensively. While general SEM software, the psych (Revelle, 2020) package contains a variety of functions for factor analysis, reliability, and other psychometric operations. Further, both packages contain functionality for generating factor scores. Additionally, the openmix (Boker et al., 2011) package is an extremely flexible SEM program, and we will detail its use when paired with trees in Chapter 10. Finally, there are a host of packages for running variable network models. See the following site for reference to many of the most commonly used R packages in this area: http://sachaepkamp.com/R.

## 8 Machine Learning and Structural Equation Modeling

In Chapter 7 we introduced the concept of latent variables as a method to account for measurement error. We followed this introduction with detailing the consequence of measurement error, namely, reducing our ability to predict an outcome of interest, as well as increase the instability of decision tree results. In this chapter we integrate concepts from Chapters 4 and 7 in using structural equation modeling (SEM) to account for measurement error while incorporating concepts more traditionally used in machine learning.

The preceding chapters (Chapters 4-6) focused primarily on predictive aims, and, to a lesser extent, descriptive aims in assessing relationships and variable importance. The idea of prediction in SEM has long been discussed and debated, because of the uncertainty regarding the application of SEM for purely predictive purposes, caseworkewise. Given that SEM is a multivariate method that encompasses the estimation and modeling of covariance matrices, individual responses on X or Y variables are not necessary for the majority of models. With this in, and given that SEM cannot generate casework for some models (Evermann & Tate, 2016), alternatives such as partial least squares SEM (PLS-SEM) have been championed (see Hair, Sarstedt, Ringle, & Mena, 2012) specific forms of PLS-SEM have been shown to be equivalent to the use of factor score regression (Yuan & Deng, 2021). Finally, a recent paper demonstrated how to use SEM to generate casework, highlighting that it can be seen as an even less complex model for prediction (de Rooij et al., 2022).

The aim of this chapter is not to explain how SEM can be used in a purely predictive domain. Instead, we discuss a number of strategies for moving the pendulum with how SEM is typically applied, from purely explanatory or descriptive applications, to increasingly incorporating aspects of prediction. This holds true for this chapter, as well as Chapters 9 and 10, where we no longer truly have a singular outcome. To accomplish this, we break this chapter down into three main sections: latent variables as linear predictors, latent variables as linear outcomes, and nonlinear relationships in SEM. Although both linear and nonlinear relationships should be tested in a succession of models, we dissect the sections for pedagogical purposes, summarizing both frameworks at the conclusion of the chapter.

### 8.1 Key Terminology

- Maximum likelihood estimation: The most commonly used form of estimation in SEM since, with most common data characteristics in social and behavioral research, it has the best asymptotic (population) characteristics as long as assumptions (multivariate normality) hold (e.g., see Zhong & Yuan, 2011).
- Endogenous variable: A variable with at least one directed toward it, meaning it is an outcome variable. Note that in SEM endogenous variable can also have directed paths from it to other variables.
- Exogenous variable: A variable that is not predicted or has any directed paths to it. This is typically referred to as an independent variable in regression models.
- Measurement model: The part of an SEM that determines the composition of a latent variable, typically through a confirmatory factor analysis specification.
- Structural model: Part of an SEM that has directed or undirected paths between observed and latent variables. If a measurement model is not included, then it is typically referred to as path analysis. Mediation models that do not include the presence of latent variables are a subset of this.
- Multiple indicator multiple cause (MIMIC) model: An SEM model that incorporates a measurement model to represent latent variables, along with predictors of the latent variables.
- Interpretation confounding: When the meaning of a latent variable is confounded by the inclusion of a directed path to the latent variable to what is described as an outcome variable. In this situation, there is no distinction between a regression path and factor loading.
