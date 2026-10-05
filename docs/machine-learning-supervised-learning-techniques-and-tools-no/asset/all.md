   

MACHINE LEARNING.

SUPERVISED LEARNING TECHNIQUES AND TOOLS:

NONLINEAR MODELS

Exercises with R, SAS, STATA, EVIEWS AND SPSS

César Pérez López

# TABLE OF CONTENTS

[MACHINE LEARNING AND NON-LINEAR MODELLING](#c003.xhtml#_Toc179989016)

[NON-LINEAR MODELS](#c004.xhtml#_Toc179989017)

[1.1 NON-LINEAR MODELS](#c005.xhtml#_Toc179989018)

[1.2 SIMPLE NON-LINEAR MODELS](#c006.xhtml#_Toc179989019)

[1.3 NON-LINEAR LEAST SQUARES. NEWTON AND MARQUARDT ALGORITHMS](#c007.xhtml#_Toc179989020)

[1.4 STEPWISE OR SEGMENTED REGRESSION](#c008.xhtml#_Toc179989021)

[1.5 SPSS AND NON-LINEAR AND SEGMENTED ESTIMATION](#c009.xhtml#_Toc179989022)

[1.5.1 Curvilinear estimation with SPSS](#c010.xhtml#_Toc179989023)

[1.5.2 General and segmented non-linear estimation with SPSS](#c011.xhtml#_Toc179989024)

[1.6 SAS AND NON-LINEAR ESTIMATION. PROC NLIN](#c012.xhtml#_Toc179989025)

[1.7 SAS AND NON-LINEAR AND SEGMENTED ESTIMATION. MODEL PROCEDURE](#c013.xhtml#_Toc179989026)

[1.8 SAS AND NON-LINEAR SIMULTANEOUS EQUATION MODELS: THE MODELING PROCEDURE](#c014.xhtml#_Toc179989027)

[1.9 EVIEWS AND NON-LINEAR EQUATION MODELS](#c015.xhtml#_Toc179989028)

[1.10 stata AND NON-LINEAR ECUATION MODELS](#c016.xhtml#_Toc179989029)

[GENERALISED LINEAR MODELS . TREATMENT WITH R, SAS, SPSS and STATGRAPHICS](#c017.xhtml#_Toc179989030)

[2.1 GENERALIZED LINEAR model](#c018.xhtml#_Toc179989031)

[2.1.1 Components of a generalised linear model:](#c019.xhtml#_Toc179989032)

[2.2 LINK FUNCTIONS FOR LOGIT, PROBIT, POISSON AND NEGATIVE BINOMIAL MODELS](#c020.xhtml#_Toc179989033)

[2.3 EXPONENTIAL FAMILY OF DISTRIBUTIONS](#c021.xhtml#_Toc179989034)

[2.4 GENERALISED LINEAR MODELS WITH SAS](#c022.xhtml#_Toc179989035)

[2.5 GENERALISED LINEAR MODELS WITH SPSS](#c023.xhtml#_Toc179989036)

[2.5.1 Types of models](#c024.xhtml#_Toc179989037)

[2.5.2 Liaison functions](#c025.xhtml#_Toc179989038)

[2.6 GENERALISED LINEAR MODELS WITH R](#c026.xhtml#_Toc179989039)

[2.7 GENERALISED LINEAR MODELS IN R THROUGH MENUS](#c027.xhtml#_Toc179989040)

[2.8 GENERALISED LINEAR MODELS THROUGH STATGRAPHICS CENTURION](#c028.xhtml#_Toc179989041)

[LIMITED DEPENDENT VARIABLE, DISCRETE CHOICE, COUNT, CENSORED, TRUNCATED AND SAMPLE SELECTION MODELS. TREATMENT WITH STATA](#c029.xhtml#_Toc179989042)

[3.1 LIMITED DEPENDENT VARIABLE MODELS](#c030.xhtml#_Toc179989043)

[3.2 DISCRETE CHOICE MODELS](#c031.xhtml#_Toc179989044)

[3.3 BINARY DISCRETE CHOICE MODELS](#c032.xhtml#_Toc179989045)

[3.3.1 Linear probability model](#c033.xhtml#_Toc179989046)

[3.3.2 Probit and Logit models](#c034.xhtml#_Toc179989047)

[3.4 MULTIPLE CHOICE MODELS](#c035.xhtml#_Toc179989048)

[3.4.1 Multinomial Logit Model](#c036.xhtml#_Toc179989049)

[3.4.2 Conditional Logit Model](#c037.xhtml#_Toc179989050)

[3.4.3 Nested Logit Model](#c038.xhtml#_Toc179989051)

[3.4.4 Multinomial Probit Model](#c039.xhtml#_Toc179989052)

[3.5 ORDERED LOGIT AND PROBIT MODELS](#c040.xhtml#_Toc179989053)

[3.6 COUNT DATA MODELS](#c041.xhtml#_Toc179989054)

[3.6.1 Poisson Regression Model](#c042.xhtml#_Toc179989055)

[3.6.2 Negative Binomial Regression Model](#c043.xhtml#_Toc179989056)

[3.6.3 Exponential Regression Model](#c044.xhtml#_Toc179989057)

[3.6.4 Normal Regression Model](#c045.xhtml#_Toc179989058)

[3.7 CENSORED MODELS: THE TOBIT MODEL](#c046.xhtml#_Toc179989059)

[3.7.1 Interpretation of the coefficients in the Tobit model](#c047.xhtml#_Toc179989060)

[3.7.2 Partial effects in the Tobit model](#c048.xhtml#_Toc179989061)

[3.7.3 Tobit model with censorship in the data](#c049.xhtml#_Toc179989062)

[3.7.4 Maximum Likelihood (MV) estimation of the censored Tobit model](#c050.xhtml#_Toc179989063)

[3.7.5 Two-stage ordinary least squares estimation of the censored Tobit model](#c051.xhtml#_Toc179989064)

[3.8 SAMPLE SELECTION: TRUNCATED MODELS](#c052.xhtml#_Toc179989065)

[3.8.1 Truncated Tobit model estimation](#c053.xhtml#_Toc179989066)

[3.8.2 Partial effects in the truncated Tobit model](#c054.xhtml#_Toc179989067)

[3.8.3 Maximum Likelihood (MV) estimation of the truncated Tobit model](#c055.xhtml#_Toc179989068)

[3.8.4 Estimation by Amemiya's two-step method](#c056.xhtml#_Toc179989069)

[3.9 SAMPLE SELECTION CORRECTION: TWO-STAGE HECKMAN OR HECKIT ESTIMATION](#c057.xhtml#_Toc179989070)

[3.10 BOUNDED DEPENDENT VARIABLE MODELS WITH STATA: LOGIT AND PROBIT](#c058.xhtml#_Toc179989071)

[3.11 CENSORED AND TRUNCATED TOBIT MODELS WITH STATA. HECKMAN METHOD AND MILLS RATIO.](#c059.xhtml#_Toc179989072)

[3.12 POISSON MODEL WITH STATA](#c060.xhtml#_Toc179989073)

[LOGIT, PROBIT, TOBIT, TRUNCATED, RECOUNTED, CENSORED and SAMPLE SELECTION models. PROCESSING WITH EVIEWS](#c061.xhtml#_Toc179989074)

[4.1 BOUNDED DEPENDENT VARIABLE MODELS WITH EVIEWS: MLP, LOGIT AND PROBIT](#c062.xhtml#_Toc179989075)

[4.2 COUNTING MODELS WITH EVIEWS: POISSON, NEGATIVE BINOMIAL AND EXPONENTIAL MODELS](#c063.xhtml#_Toc179989076)

[4.3 CENSORED AND TRUNCATED TOBIT MODELS WITH EVIEWS. HECKMAN'S METHOD AND MILLS' RATIO](#c064.xhtml#_Toc179989077)

[GENERALISED LINEAR MODELS WITH PANEL DATA. NON-LINEAR PANEL MODELS](#c065.xhtml#_Toc179989078)

[5.1 INTRODUCTION TO PANEL DATA: DATA STRUCTURES](#c066.xhtml#_Toc179989079)

[5.1.1 Cross-sectional data](#c067.xhtml#_Toc179989080)

[5.1.2 Time series data](#c068.xhtml#_Toc179989081)

[5.1.3 Data structures. Combinations of cross-sections](#c069.xhtml#_Toc179989082)

[5.1.4 Data structures. Panel or longitudinal data](#c070.xhtml#_Toc179989083)

[5.2 PURE PANELS AND EXPANDED PANELS](#c071.xhtml#_Toc179989084)

[5.3 COMPARISON BETWEEN ANNUAL SAMPLES, COMBINATIONS OF CROSS-SECTIONS (POOLED DATA) AND PANELS](#c072.xhtml#_Toc179989085)

[5.4 ECONOMETRIC MODELS WITH PANEL DATA](#c073.xhtml#_Toc179989086)

[5.5 PANEL MODELS WITH CONSTANT COEFFICIENTS](#c074.xhtml#_Toc179989087)

[5.6 FIXED EFFECTS PANEL MODELS](#c075.xhtml#_Toc179989089)

[5.7 RANDOM EFFECTS PANEL MODELS](#c076.xhtml#_Toc179989090)

[5.8 DYNAMIC MODELS WITH PANEL DATA](#c077.xhtml#_Toc179989091)

[5.9 LOGIT AND PROBIT MODELS WITH PANEL DATA](#c078.xhtml#_Toc179989092)

[5.10 UNIT ROOTS AND COINTEGRATION WITH PANEL DATA](#c079.xhtml#_Toc179989093)

[5.11 stata AND THE PANEL DATA MODELS](#c080.xhtml#_Toc179989094)

[5.11.1 Logit, probit and Poisson models with panel data](#c081.xhtml#_Toc179989095)

[5.11.2 Dynamic panel estimation using Arellano-Bond methodology](#c082.xhtml#_Toc179989096)

[NEURONAL NETWORK models](#c083.xhtml#_Toc179989097)

[6.1 DESCRIPTION OF A NEURAL NETWORK](#c084.xhtml#_Toc179989098)

[6.1.1 Definition](#c085.xhtml#_Toc179989099)

[6.1.2 Output function and transfer or activation functions](#c086.xhtml#_Toc179989100)

[6.2 NEURAL NETWORKS AND REGRESSION MODEL FITTING](#c087.xhtml#_Toc179989101)

[6.3 LEARNING IN NEURAL NETWORKS](#c088.xhtml#_Toc179989102)

[6.5 THE BACK-PROPAGATION LEARNING ALGORITHM (BACK-PROPAGATION)](#c089.xhtml#_Toc179989103)

[6.6 DISCRIMINANT ANALYSIS THROUGH THE PERCEPTRON](#c090.xhtml#_Toc179989104)

[6.7 TIME SERIES ANALYSIS USING NEURAL NETWORKS](#c091.xhtml#_Toc179989105)

[6.8 ANALYSIS OF MAIN COMPONENTS WITH neural networks](#c092.xhtml#_Toc179989106)

[6.9 CLUSTERING USING NEURAL NETWORKS](#c093.xhtml#_Toc179989107)

[6.10 SPSS AND neural networks](#c094.xhtml#_Toc179989108)

[6.10.1 Multilayer Perceptron (MLP)](#c095.xhtml#_Toc179989109)

[6.10.2 Radial Basis Function (RBF)](#c096.xhtml#_Toc179989110)

[6.11 NEURAL NETWORKS IS THROUGH R](#c097.xhtml#_Toc179989111)

[6.11.1 neuralnet library](#c098.xhtml#_Toc179989112)

[6.11.2 nnet bookshop](#c099.xhtml#_Toc179989113)

[6.12 R AND TIME SERIES USING NEURAL NETWORKS](#c100.xhtml#_Toc179989114)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# MACHINE LEARNING AND NON-LINEAR MODELLING

![image](d2d_images/chapter_title_below.png)

In the field of Machine Learning, there are different types of models that are used to analyse and predict data. Two of the most common types are linear models and non-linear models.

Machine Learning uses two types of techniques: supervised learning, which trains models on known input and output data in order to predict future results, and unsupervised learning, which finds hidden patterns or intrinsic structures in the input data.

The goal of supervised machine learning is to build a model that makes evidence-based predictions in the presence of uncertainty. A supervised learning algorithm takes a known set of input data and known responses to the data (output) and trains a model to generate reasonable predictions for the response to new data. Supervised learning uses classification and regression techniques to develop predictive models.

Predictive classification models predict categorical responses, for example, whether a taxpayer defrauds or does not defraud, or whether a tumour is cancerous or benign. Classification models classify the input data into categories that are the dependent variable of the model, and the independent variables can be continuous, categorical or mixture.

Predictive regression models predict continuous responses and the independent variables are also usually continuous.

Linear models are those that assume a linear relationship between the input variables and the output variable. In other words, the data are assumed to follow a linear trend and fit a straight line in a multidimensional space. This type of model is based on the idea that changes in the input variables translate into proportional changes in the output variable.

On the other hand, non-linear models do not assume a linear relationship between the input variables and the output variable. Instead, they can fit different shapes and more complex patterns, such as curves, polynomials or even more irregular structures. These models are able to capture more complex and flexible relationships between variables, allowing them to better fit the data.

Linear and non-linear models have different assumptions and characteristics. Linear models assume a linear relationship and are simpler and more interpretable, while non-linear models are more flexible and can better fit non-linear data. The choice between one or the other will depend on the characteristics of the data and the objectives of the Machine Learning problem.

It is advisable to use a linear model when you want to understand how an input variable affects an output variable in a proportional way and when the data follow a linear trend. Non-linear models offer the advantage of being able to capture more complex relationships between variables and better fit non-linear data.

In this book we will develop supervised learning Machine Learning techniques related to non-linear regression. More specifically, we will go deeper into non-linear multiple regression models with all their identification, estimation and diagnosis problems. Special emphasis is placed on generalised linear models and all types of derived non-linear models: Logit Models, Probit Models, Poisson Models and Negative Binomial Models. This is followed by models of limited dependent variable, discrete choice, count, censored, truncated and sample selection. Non-linear models with panel data are also discussed in depth. An important section is devoted to predictive models of neuroanalytic networks. All chapters are illustrated with examples and representative exercises solved with the latest software such as R, SAS, SPSS, EVIEWS and STATGRAPHICS.

1Chapter 1

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# ​NON-LINEAR MODELS

![image](d2d_images/chapter_title_below.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.1  ​NON-LINEAR MODELS

![image](d2d_images/chapter_title_below.png)

It is common in the scientific world to identify relationships between variables, but not to identify the nature of the relationship. It is clear that different variables are related to each other, but what is not clear is the functional form of these relationships. Therefore, the model is usually specified in the form:

![image](d2d_images/image200.png)

where![image](d2d_images/image693.png)is, in general, a non-linear function of the components of the vectors![image](d2d_images/image607.png). As a particular case, the linear model appears when![image](d2d_images/image145.png).

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.2  ​SIMPLE NON-LINEAR MODELS

![image](d2d_images/chapter_title_below.png)

The following types of non-linear models are commonly used:

![Texto, Carta Descripción generada automáticamente](d2d_images/image405.png)

The above models, except for the last one, can be treated as linear or polynomial models by appropriate transformations. For example, the fourth model is treated as linear by the transformations![image](d2d_images/image067.png)and![image](d2d_images/image084.png).

The last of the models, in which the non-linearity affects the endogenous variable, making it impossible to express it as a function of the exogenous variables, constitutes the implicit function models, whose general functional form is:

![image](d2d_images/image085.png)

Obviously, the model,![image](d2d_images/image052.png)is a particular case of the implicit function model.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.3  ​NON-LINEAR LEAST SQUARES. NEWTON AND MARQUARDT ALGORITHMS

![image](d2d_images/chapter_title_below.png)

The general approach of the least squares method for the model![image](d2d_images/image057.png)does not depend on the linearity of the function f. However, the analytical resolution of the estimation problem is complicated by non-linearities.

The least squares problem is to find the values of the vectorβ that minimise the residual sum:

![image](d2d_images/image697.png)

Deriving with respect to each component of the vector ![image](d2d_images/image249.png)and equalling zero gives the following system of normal equations:

![Texto Descripción generada automáticamente con confianza media](d2d_images/image090.png)

The partial derivative![Texto Descripción generada automáticamente con confianza baja](d2d_images/image199.png)is a scalar for each i \= 1,...,k and for each period t \= 1,...,T and the same is true for the difference![image](d2d_images/image154.png)for each t \= 1,...,T. The above k equations constitute a system of normal equations completely analogous to the one obtained in linear models, which can be expressed in short as:

![image](d2d_images/image462.png)or in matrix form as:

![image](d2d_images/image392.png)

The linear case is the particular case where![image](d2d_images/image688.png) =X and ![image](d2d_images/image096.png)\=![image](d2d_images/image710.png). The above equation would be transformed into ![image](d2d_images/image035.png), which is the usual parameter estimate in the linear ordinary least squares OLS model.

As in the linear case, for the non-linear case the residual![image](d2d_images/image054.png)is defined as the difference![image](d2d_images/image120.png), so that the normal equations can be written as:

![image](d2d_images/image436.png)or in matrix form:

![image](d2d_images/image422.png)

expression that is equivalent to the orthogonality between the residuals and the explanatory variables when the model is linear.

We can say that the least squares estimator of the model:

![image](d2d_images/image386.png)

is the vector of residues orthogonal to each of the components of the gradient vector of the function ![image](d2d_images/image216.png)evaluated at![image](d2d_images/image411.png).

Practical problems in the case of non-linearity arise when the non-linear system of normal equations has no or no unique solution or is very difficult to compute (in which case iterative algorithms such as Newton's, Marquardt's and others are used). Moreover, the estimator obtained may not be unbiased.

For large sample sizes, the non-linear least squares estimator has a normal distribution with expectationβ and variance-covariance matrix:

![Diagrama Descripción generada automáticamente con confianza baja](d2d_images/image544.png)

where the parameter![image](d2d_images/image037.png)is estimated by means of ![image](d2d_images/image270.png)with ![image](d2d_images/image669.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.4  ​STEPWISE OR SEGMENTED REGRESSION

![image](d2d_images/chapter_title_below.png)

Suppose a linear model with dependent variable Y and explanatory variable X. Assume that the relationship linking Y and X is not the same for values less than one X\* value of X as it is for values of X greater than X\*.

In this case, it will be necessary to consider two legs of the variable![image](d2d_images/image596.png). This regression will be approached by considering the dummy variable D which is 0 for values of X less than X\* and one otherwise. The equation of the model to be fitted will be the following:

![image](d2d_images/image162.png)

![image](d2d_images/image617.png)

Assuming E(ut ) = 0, it follows that:

![image](d2d_images/image232.png)

It can be seen thatα2   corresponds to the slope of the regression line in the first leg![image](d2d_images/image517.png)is the slope of the regression line in the second leg. ![image](d2d_images/image540.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.5  ​SPSS AND NON-LINEAR AND SEGMENTED ESTIMATION

![image](d2d_images/chapter_title_below.png)

SPSS has procedures for fitting non-linear models. If the non-linear model to be fitted is polynomial, SPSS uses the procedure Curvilinear estimation, but if the non-linear model is defined by a more complicated equation, SPSS uses the procedure Non-linear regression.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.5.1  ​Curvilinear estimation with SPSS

![image](d2d_images/chapter_title_below.png)

This SPSS procedure can be used to fit non-linear models, easily reduced to linear by appropriate transformations. One or more curvilinear regression estimation models can be selected. To determine which model to use, pre-plot the data. If the variables appear to be linearly related, use a simple linear regression model. When the variables are not linearly related, try transforming the data. When transformation is not useful, you may need a more complicated model. Inspect the scatterplot of the data and if the scatterplot resembles a recognisable mathematical function, fit the data to that type of model. For example, if the data resembles an exponential function, use an exponential model. The Curvilinear estimation procedure considers the following models:

*   Linear: model whose equation is![image](d2d_images/image020.png). The values of the series are modelled as a linear function of time.

*   Logarithmic: model for which the equation is ![image](d2d_images/image610.png)

*   Inverse: model whose equation is ![image](d2d_images/image578.png)

*   Quadratic: model whose equation is![image](d2d_images/image299.png)The quadratic model can be used to model a series that "takes off" or a series that is amortised.
*   Cubic: a model defined by the equation ![image](d2d_images/image140.png)

*   Potential: model whose equation is ![image](d2d_images/image650.png)
*   Composite: model whose equation is ![image](d2d_images/image453.png)

*   S-curve: model with equation ![image](d2d_images/image217.png)

*   Logistic: model whose equation is ![image](d2d_images/image603.png)![image](d2d_images/image128.png)where u is the upper bound value. After selecting Logistic, specify a value for the upper bound to be used in the regression equation. The value must be a positive number greater than the maximum value of the dependent variable.

*   Growth: model whose equation is ![image](d2d_images/image641.png)

*   Exponential: model whose equation is ![image](d2d_images/image419.png)

The Curvilinear Estimation procedure generates regression estimation statistics (regression coefficients, multiple R, R-squared, corrected R-squared, standard error of the estimate, analysis of variance table, predicted values, residuals and forecast intervals) and related graphs. You can also save predicted values, residuals and predicted intervals as new variables.

As an example, from the file cars.sav, we look for the best polynomial fit for the model that explains the weight of the cars (weight) as a function of their displacement (engine). To do this we choose Analyse→ Regression→ Curvilinear estimation (Figure 1-1) and fill in the input screen as shown in Figure 1-2. In the Model field we tick Linear, Quadratic and Cubic to test the fit of the three polynomial model types. We also point to Include constant in equation and Represent models (to get an idea of the best fit). With the Save button the predicted values and residuals are stored (Figure 1-3). If we enter several dependent variables, a different model is fitted for each of them.

![image](d2d_images/image081.png)![image](d2d_images/image500.png)

Figure 1-1    Figure 1-2

![image](d2d_images/image031.png)

Figure 1-3

Pressing Continue and OK results in the simultaneous fitting of the three polynomial models as output of the procedure.

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image147.png)

We observe that the fit to the linear model is quite good with a high value of adjusted R² and with a very high joint and individual significance of the parameters (p-values of F and T practically zero). The fitting equation is:

![image](d2d_images/image477.png)

The fit of the quadratic model is presented below.

![image](d2d_images/image532.png)

We observe that the fit to the quadratic model is very good with a high adjusted R-value² which improves the linear fit and with very high joint and individual parameter significance (p-values of F and T practically zero). The fitting equation is now:

![image](d2d_images/image508.png)

The fit of the cubic model is presented below:

![image](d2d_images/image156.png)

We observe that the fit to the cubic model is also good with a high value of adjusted R² which improves the linear fit and equals the quadratic fit and with a high joint and individual significance of the parameters (p-values of F and T practically null except for the motor² ). The significance is somewhat lower than in the quadratic case. The fitting equation is now:

![image](d2d_images/image371.png)

Based on the fit data, we would be left with the quadratic model, a choice that is confirmed by the plot of the variables in Figure 1-4.

![image](d2d_images/image320.png)

Figure 1-4

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.5.2  ​General and segmented non-linear estimation with SPSS

![image](d2d_images/chapter_title_below.png)

When the non-linear model that relates the variables is more general, i.e. it has other terms in addition to the polynomial ones, SPSS uses the non-linear regression procedure for its estimation, which performs the non-linear least squares adjustment using iterative algorithms to find the solution. As an example, from the file cars.sav, we fit a model that relates consumption to the square of the acceleration (acel), the cube of the power (hp) and the logarithm of the displacement (engine).

To perform the non-linear regression, choose from the Analyse menus→ Regression→ Non-linear (Figure 1-5) and select the numerical dependent variable consumption from the list of variables in the working data file (Figure 1-6). To construct an expression for the model, either enter the expression in the Model Expression field or paste the components (variables, parameters, functions) into the field. Identify Name and Initial value of each parameter of the model expression by clicking on Parameters and click on Add to define the parameters (Figure 1-7). In the Loss button choose the loss function in non-linear regression (Figure 1-8), i.e. the function that is minimised by the algorithm. Select either Sum of squared residuals to minimise the sum of squared residuals or User-defined loss function to minimise a different function.

The Constraints button allows you to enter constraints on model variables (Figure 1-9). A constraint is a limitation on the allowed values for a parameter during the iterative search for a solution.

The Options button dialog box (Figure 1-10) allows you to choose Bootstrap estimates of the standard error (requires use of the sequential quadratic programming algorithm), the Estimation method (Sequential quadratic programming or Levenberg-Marquardt). The Sequential Quadratic Programming method allows you to specify new values for Maximum number of iterations and Limit for steps and you can change the selection found in the drop-down lists for Optimality tolerance, Function accuracy and Size for infinite steps. The Levenberg-Marquardt method allows you to specify Maximum number of iterations and you can change the selection in the drop-down lists for Convergence of sum of squares and Convergence in parameters. You can save a number of new variables to the active data file using the Save button (Figure 1-11). The available options are: Predicted values, Residuals, Derivatives and Loss function values. These variables can be used in subsequent analyses to test the model fit or to identify problem cases.

![image](d2d_images/image070.png)![image](d2d_images/image339.png)

Figure 1-5    Figure 1-6

![image](d2d_images/image526.png)![image](d2d_images/image672.png)

Figure 1-7    Figure 1-8

![image](d2d_images/image238.png)![image](d2d_images/image414.png)

Figure 1-9    Figure 1-10

![image](d2d_images/image692.png)

Figure 1-11

In the Model Expression field, segmented models (models that take different forms in different parts of their domain) can be introduced using conditional logic expressions within the single model statement. To use conditional logic within the model expression or loss function, the sum of a series of terms, one for each condition, must be constructed. Each term consists of a logical expression (in parentheses) multiplied by the expression that will result when that logical expression is true. For example, consider a segmented model that equals 0 for X < = 0, X for 0 < X < 1 and 1 for X > = 1. The expression for this example is:![image](d2d_images/image511.png)All logical expressions in parentheses must be evaluable to 1 (true) or 0 (false). Thus: if X < = 0, the above reduces to 1\*0 + 0\*X + 0\*1 = 0. If 0 < X < 1, it reduces to 0\*0 + 1\*X + 0\*1 = X. If X > = 1, it reduces to 0\*0 + 0\*X + 1\*1 = 1. More complicated examples can be easily constructed by replacing different logical expressions and result expressions. Remember that double inequalities, such as 0 < X < 1, must be written as compound expressions, of the form ![image](d2d_images/image040.png)

It is possible to use string variables within logical expressions: (city='Madrid')\*costliv + (city='Guadalajara')\*0.59\*costliv. This results in one expression (the value of the variable costliv) for the inhabitants of Madrid and another (59% of that value) for the inhabitants of Guadalajara. String constants must be enclosed in inverted commas or apostrophes, as shown in the syntax of this example.

If you select User-defined loss function, you must define the loss function whose sum (in all cases) must be minimised by your choice of parameter values. Most loss functions include the special variable resid\_, which represents the residual. The default loss function Sum of squared residuals could be entered explicitly as resid\_\*\*2. If you have to use the predicted value in the loss function, it is equal to the dependent variable minus the residual. A conditional loss function can be specified using conditional logic. You can either type an expression in the User Defined Loss Function field, or paste the components of the expression into the field. String constants must be enclosed in inverted commas or apostrophes, and numeric constants must be written in American format, with the full stop separating the decimal part.

In terms of statistics, parameter estimates and residual sum of squares are obtained for each iteration, and sum of squares for regression, residual, corrected and uncorrected total, parameter estimates, asymptotic standard errors and asymptotic correlation matrix of parameter estimates are obtained for each model.

Press OK in Figure 1-6 to obtain the model estimate.

![image](d2d_images/image630.png)

The fit has been performed in 5 iterations, the coefficient R² is higher than 50% and the fitted model equation is as follows:

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image159.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.6  ​SAS AND NON-LINEAR ESTIMATION. PROC NLIN

![image](d2d_images/chapter_title_below.png)

The NLIN procedure fits non-linear models using least squares or weighted least squares. The estimation method is iterative using Newton, gradient, Gass-Newton, Marquardt or false position (DUD) algorithms. The syntax is as follows:

![image](d2d_images/image581.png)

The BOUNDS statement restricts the estimated parameters to the specified conditions. The BY statement specifies variables to perform subgroups. The DER statement specifies first or second partial derivatives. The ID statement specifies additional variables to add to the output data set. The MODEL statement defines the relationship to fit between the dependent variable and the independent variables. The OUTPUT statement creates the output data set. The PARMS statement identifies parameters to be estimated and their initial values. The CONTROL statement declares control variables and specifies their values.

The PROC NLIN options are: DATA=input data set, OUTEST=output data set with estimates in the iterations, SAVE specifies that when iteration is exceeded to save the results BEST=n so that the sums of squares of the residuals are displayed, METHOD=GAUSS | MARQUARDT | NEWTON | GRADIENT | DUD chooses an iterative method for the fit, MAXSUBIT=n, RHO=n, SMETHOD=n and TAU=n control the step size, G4 and SIGSQ=n specify iteration details, CONVERGE=c, CONVERGEOBJ=c, CONVERGEPARM=c, SINGULAR=c and MAXITER=c tune the minimisation, HOUGAARD, NOITPRINT and NOPRINT modify the output quantity, LIST, LISTALL, LISTCODE, LISTDEP, LISTDER and XREF list the model structure, FLOW, PRINT and TRACE provide the trace of the model execution.

As an example we consider a theoretical model of enzyme kinetics that defines the initial rate of an enzymatic reaction at substrate concentration by:

![image](d2d_images/image311.png)

where xi represents the amount of substrate for n attempts and ![image](d2d_images/image381.png)is the rate of the reaction.

Suppose you want to study the relationship between concentration and rate for a particular enzyme/substrate pair by recording the reaction rate observed at different substrate concentrations.

![image](d2d_images/image248.png)

The output is as follows:

![image](d2d_images/image258.png)

![image](d2d_images/image695.png)

The estimated model turns out to be: 

![image](d2d_images/image036.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.7  ​SAS AND NON-LINEAR AND SEGMENTED ESTIMATION. MODEL PROCEDURE

![image](d2d_images/chapter_title_below.png)

An important advantage of proc MODEL is that it allows us to estimate non-linear models without using initial values. For example, we can fit the non-linear model discussed above with SYSLIN:

![image](d2d_images/image445.png)

For this we will use the proc MODEL directly without using initial values. The SAS syntax will be as follows:

![image](d2d_images/image089.png)

The estimated model is presented below.

![image](d2d_images/image105.png)

![image](d2d_images/image415.png)

Graphical diagnosis indicates that the residuals are normal and random because their histogram fits the Gaussian bell, the point cloud of the normality plot fits the diagonal of the first quadrant, and the residual autocorrelation and partial autocorrelation functions have no significantly non-zero terms as illustrated in the graph below:

![image](d2d_images/image556.png)

The estimated model turns out to be: 

![image](d2d_images/image229.png)

The result matches that of the SYLIN proc.

Using the proc MODEL it is also possible to estimate segmented models. As an example we estimate the following model:

![Texto, Carta Descripción generada automáticamente con confianza media](d2d_images/image367.png)

The proper syntax is as follows:

![image](d2d_images/image283.png)The output is as follows:

![image](d2d_images/image227.png)

![image](d2d_images/image537.png)

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image527.png)

Graphical diagnosis indicates that the residuals are normal and random because their histogram fits the Gaussian bell, the point cloud of the normality plot fits the diagonal of the first quadrant, and the residual autocorrelation and partial autocorrelation functions have no significantly non-zero terms as illustrated in the graph below:

![image](d2d_images/image083.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.8  ​SAS AND NON-LINEAR SIMULTANEOUS EQUATION MODELS: THE MODELING PROCEDURE

![image](d2d_images/chapter_title_below.png)

The MODEL procedure allows estimating systems of non-linear regression equations using ordinary least squares, 2-stage, 3-stage, seemingly related regressions and maximum likelihood. It also allows Monte Carlo simulation, linear programming, estimation of dynamic models, estimation of step models and solving ordinary differential equations. Its syntax is as follows:

![image](d2d_images/image487.png)

![image](d2d_images/image062.png)

The wide variety of options in this procedure requires consultation of the manual. However, they are all intuitive.

As an example, the estimation of a non-linear system of consumer demand equations based on the logarithmic transformation is shown. We have total expenditure data for three types of goods and estimate a model in which the proportion of expenditure on each item depends on the logarithm of prices and the logarithm of total expenditure using the following non-linear equations:

![Texto, Carta Descripción generada automáticamente](d2d_images/image261.png)

As this is a system of non-linear equations we use the proc MODEL with the following syntax:

![image](d2d_images/image464.png)

![image](d2d_images/image530.png)

The output with the estimated model is as follows:

![image](d2d_images/image618.png)![image](d2d_images/image201.png)

![image](d2d_images/image553.png)

![image](d2d_images/image276.png)

![image](d2d_images/image506.png)

The diagnosis is correct because the adjusted R2 is high and the p-values of the parameters are very low, indicating strong significance of the parameters. Furthermore, the graphical diagnosis shows normal and random residuals, as indicated in the graphs below:

![image](d2d_images/image681.png)

![image](d2d_images/image539.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.9  ​EVIEWS AND NON-LINEAR EQUATION MODELS

![image](d2d_images/chapter_title_below.png)

Eviews allows you to estimate non-linear models simply by using Quick → Estimate Equation (Figure 1-12) and entering the model equation in the Specification screen (Figure 1-13). Clicking OK produces the requested estimate (Figure 1-14).

![image](d2d_images/image664.png)![image](d2d_images/image264.png)

Figure 1-12    Figure 1-13

![image](d2d_images/image196.png)

Figure 1-14

The estimated model, with highly significant parameters, turns out to be:

![image](d2d_images/image495.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.10  ​stata AND NON-LINEAR ECUATION MODELS

![image](d2d_images/chapter_title_below.png)

STATA has the nl statement that allows estimating models with non-linear equations. Its basic syntax is as follows:

nl model equation, options

Among the more interesting options are variables(variables\_list) to specify the variables in the model, initial(initial\_values) to give initial values to the parameters of the model, parameters(parameters\_list) to specify the parameters in the model, nparameters(n) to specify that there are n parameters in the model, noconstant to fit the model without constant, hasconstant(name) to identify the constant term in the model, robust to estimate in the presence of heteroscedasticity, level(n) sets the confidence level at n, eps(n) to specify the convergence criterion and delta(n) which specifies n for computing derivatives.

As an example, using the data in the production.dta  file, we estimate the following CES production function:

![image](d2d_images/image425.png)

The solution is as follows:

![image](d2d_images/image342.png)

––––––––

![image](d2d_images/scene_break.png)

Very small p-values are observed, indicating high individual significance of the estimated parameters. The p-value of Fisher's F is also very small, indicating high joint significance of the estimated parameters. A high R² and small values of the estimation errors are also observed. The model fit is thus quite acceptable.

––––––––

![image](d2d_images/scene_break.png)

Exercise 1-1. Consider a theoretical model of enzyme kinetics that defines the initial rate v of an enzymatic reaction at substrate concentration x by:

![image](d2d_images/image239.png)

where x  represents the amount of substrate and ![image](d2d_images/image499.png) is the rate of the reaction. Suppose you want to study the relationship between concentration and rate for a particular enzyme/substrate pair by recording in file 1-4.sav the reaction rate observed at different substrate concentrations. What is the appropriate relationship under the data collected? From previous trials it is known thatθ1 varies around 150 andθ2 varies around 1 approximately. SPSS will be used.

You are fitting a non-linear function to n points, so you will need to use non-linear regression. To perform the non-linear regression, choose from the Analyse menus→ Regression→ Non-linear (Figure 1-15) and select the numerical dependent variable V from the list of variables in the working data file (Figure 1-16). To construct an expression for the model, enter the expression in the Model Expression field. Identify Name and Initial Value for each of the parameters of the model expression by clicking on Parameters and click Add to progressively define the parameters (Figure 1-17). You can save a new set of variables to the active data file using the Save button (Figure 1-18). In the Loss button choose the loss function in non-linear regression (Figure 1-19), i.e. the function that is minimised by the algorithm. Select either Sum of squared residuals to minimise the sum of squared residuals or User-defined loss function to minimise a different function. In the Constraints button, we do not enter constraints on the variables in the model. In the Options button dialogue box (Figure 1-20) we choose the Levenberg-Marquardt method with the default options.

![image](d2d_images/image554.png)![image](d2d_images/image236.png)

Figure 1-15    Figure 1-16

![image](d2d_images/image649.png)![image](d2d_images/image123.png)

Figure 1-17    Figure 1-18

![image](d2d_images/image409.png)![image](d2d_images/image659.png)

Figure 1-19    Figure 1-20

Pressing OK in Figure 1-16 produces the following output:

![image](d2d_images/image448.png)

![image](d2d_images/image633.png)

The fit has been performed in 17 iterations, the coefficient R² is very high (0.98452) and the estimated equation of the fitted model is as follows:

![image](d2d_images/image050.png)

We have already seen that the fit is good because the coefficient R² is very high. Additionally we plot the residuals by graphing→ Sequence and filling in the input screen as shown in Figure 1-21. The graph in Figure 1-22 shows that the residuals follow a random evolution. We also make a residual histogram by using Graphs→ Histogram and filling in the input screen as shown in Figure 1-23. The graph in Figure 1-24 shows that the residuals approximate a normal. Finally we plot residuals against predicted values by Graphing→ Dispersion→ Simple Dispersion and filling in the input screen as indicated in Figure 1-25. Figure 1-26 shows a random evolution.

![image](d2d_images/image628.png)![image](d2d_images/image000.png)

Figure 1-21    Figure 1-22

![image](d2d_images/image082.png)![image](d2d_images/image088.png)

Figure 1-23    Figure 1-24

![image](d2d_images/image174.png)![image](d2d_images/image572.png)

Figure 1-25    Figure 1-26

Exercise 1-2. Consider a country's population data over several decades:

![image](d2d_images/image053.png)

Fit the data with an appropriate model of population evolution over time.

We will use a logistic function type population model for fitting, which can be defined by![image](d2d_images/image066.png)where a, b and c are the parameters of the model with initial values![image](d2d_images/image294.png). To fit this model we use the following SAS syntax:

![image](d2d_images/image382.png)

The following output is obtained:

![image](d2d_images/image536.png)

![image](d2d_images/image322.png)

The fitted model will be population=244/(1+e^(3,88901-0,289) 7\*decade). The overall fit is quite good because the p-value of the F is less than one thousandth.

Exercise 1-3. The aim is to estimate the non-linear model:

![image](d2d_images/image362.png)Where a and b are parameters. The data from the citimon file in the sashelp library shall be used.

The SAS syntax with the proc MODEL would be as follows:

![image](d2d_images/image658.png)

The output of the non-linear model fit is as follows:

![image](d2d_images/image157.png)![image](d2d_images/image599.png)

![image](d2d_images/image160.png)

The fitted model equation, with good parameter significance (small p-values), is as follows:

![image](d2d_images/image212.png)

The graphical diagnosis shows the residual normality.

![image](d2d_images/image663.png)![image](d2d_images/image437.png)

Exercise 1-4. In this exercise we consider the Bodkin and Klein non-linear model used to explain output g in the United States. The variable z1 is the capital input, z2 is the labour input, z3 is the real output, z4 is the time years based on 1929 and z5 is the price of capital services. Fit the two-equation model to the data specified in the problem by the full maximum likelihood method.

The model has the following equations:

![g\_{1} = c\_{1} 10^{c\_{2}z\_{4}}(c\_{5} z^{-c\_{4}}\_{1} + (1- c\_{5}) z^{-c\_{4}}\_{2})^{-c\_{3}/c\_{4}} - z\_{3} = 0 ](d2d_images/image002.png)

![g\_{2} = \[c\_{5}/(1-c\_{5})\](z\_{1}/z\_{2})^{(-1 - c\_{4})} - z\_{5} = 0 ](d2d_images/image112.png)

As we are dealing with a system of two non-linear equations, we will use the SAS MODEL procedure using the following syntax:

![image](d2d_images/image667.png)

![image](d2d_images/image183.png)

The output is as follows:

![image](d2d_images/image316.png)![image](d2d_images/image594.png)

![image](d2d_images/image023.png)

––––––––

![image](d2d_images/scene_break.png)

It is observed that the estimated parameters are highly significant with very small p-values, so that the model has been fitted very well.

The residual normality and randomness are shown in the graphs below:

![image](d2d_images/image565.png)

![image](d2d_images/image149.png)

2Chapter 2

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# ​GENERALISED LINEAR MODELS . TREATMENT WITH R, SAS, SPSS and STATGRAPHICS

![image](d2d_images/chapter_title_below.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.1  ​GENERALIZED LINEAR model

![image](d2d_images/chapter_title_below.png)

Within the family of non-linear models, generalised linear models play an important role. The generalised linear model extends the general linear model, so that the dependent variable y is linearly related to the factors and covariates by a certain link function g: ![image](d2d_images/image024.png). If![image](d2d_images/image209.png)then ![image](d2d_images/image401.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.1.1  ​Components of a generalised linear model:

![image](d2d_images/chapter_title_below.png)

*   The response variables, and1 ,...,andn , are assumed to follow a common distribution that is a member of the exponential family.

*   A set of explanatory variables,![image](d2d_images/image318.png), and parameters![image](d2d_images/image013.png)defined as follows:

![image](d2d_images/image072.png)

*   A monotone link function g such that

![image](d2d_images/image049.png)

where ![image](d2d_images/image209.png)

We can also write the generalised linear model as:

![image](d2d_images/image173.png)

In addition, the model allows the dependent variable to have a non-normal distribution. The generalised linear model covers the most commonly used statistical models, such as linear regression for normally distributed responses, logistic models for binary data, log-linear models for count data, complementary log-log models for interval-censored survival data, as well as many other statistical models through the general formulation of the model itself.

The possibility of specifying a specific distribution for the dependent variable other than the normal distribution and the possibility of specifying a link function other than the identity is the main improvement of the generalised linear model with respect to the general linear model. If the distribution of the dependent variable is normal and the link function is the identity, this is the general linear model.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.2  ​LINK FUNCTIONS FOR LOGIT, PROBIT, POISSON AND NEGATIVE BINOMIAL MODELS

![image](d2d_images/chapter_title_below.png)

Discrete choice models directly predict the probability of an event that has two or more possibilities of occurrence. Since the values of a probability are between zero and one, predictions made with discrete choice models must be bounded to fall in the range between zero and one. The general model that satisfies this condition has the functional form:

![image](d2d_images/image139.png)

It is noted that if F is the distribution function of a random variable, then P varies between zero and one.

In the particular case in which the function F is the logistic function, we will be dealing with the Logit or Logistic Regression model, whose functional form will be the following:

![image](d2d_images/image016.png)It is noted that:

![image](d2d_images/image682.png)

The logit model can therefore also be expressed in the form:

![image](d2d_images/image356.png)

The link function turns out to be![Diagrama Descripción generada automáticamente](d2d_images/image514.png)which is called the logit link function and belongs to the binomial family.

In the particular case where the function F is the distribution function of a unit normal, the Probit model has the following functional form:

![image](d2d_images/image505.png)

We have:

![image](d2d_images/image181.png)

The logit model can therefore also be expressed in the form:

![image](d2d_images/image338.png)

where![image](d2d_images/image038.png)is the distribution function of a normal (0,1).

The link function turns out to be ![image](d2d_images/image541.png)which is called the probit link function and also belongs to the binomial family.

On the other hand, count data models are those that have as dependent variable a discrete variable that takes a finite or infinite numberable set of non-negative integer values. Poisson and Negative Binomial regression models are the most common of this type.

The Poisson regression model assumes that each yi is a realisation of a random variable with Poisson distribution of parameterλ and that this parameter is related to the vector of regressors xi . The basic equation of the model is:

![image](d2d_images/image298.png)

The most common formulation ofλ is logarithm-linear, i.e:

![image](d2d_images/image583.png)

Therefore the link function is ![image](d2d_images/image560.png)called the log (logarithmic) link function and belongs to the Poisson family.

The Negative Binomial regression model assumes that each yi is a realisation of a random variable with a Negative Binomial distribution of parameters μ and k. The probability function of this distribution is:

![image](d2d_images/image297.png)

y \= 0,1,2,...

It has to

![image](d2d_images/image545.png)

The parameter![image](d2d_images/image546.png)is a dispersion parameter, so if![image](d2d_images/image459.png)then![image](d2d_images/image063.png)and the negative binomial distribution converges to a Poisson distribution.

On the other hand, for a fixed value of k this distribution belongs to the natural exponential family, so that a negative binomial GLM model can be defined. In general, a logarithm-type function is used.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.3  ​EXPONENTIAL FAMILY OF DISTRIBUTIONS

![image](d2d_images/chapter_title_below.png)

The random variable y is said to be a member of the exponential family of distributions if its probability density function, f(y;θ), can be expressed as:

![image](d2d_images/image627.png)

If a(y) = y, the above distribution is said to be in its canonical form and b(θ) is called the natural parameter of the distribution.

Let y be a random variable with probability density function f(y,θ) a member of the exponential family. Then, using the natural parametrization, we can write:

![image](d2d_images/image022.png)

where θ is the natural or canonical location parameter and φ the dispersion parameter.

Below is a schematic showing the elements of the different distributions belonging to the exponential family in terms of the overall probability density of a random variable of the exponential family of distributions.

![image](d2d_images/image690.png)

For each of these distributions a General Linear Model belonging to the Distribution family and with link function θ   can be defined.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.4  ​GENERALISED LINEAR MODELS WITH SAS

![image](d2d_images/chapter_title_below.png)

The GENMOD procedure estimates generalised linear models. Its summary syntax is as follows:

![image](d2d_images/image426.png)

The BAYES statement performs Bayesian estimation using Gibbs sampling by default (the DIAGNOSTICS=ALL option performs full diagnosis, the PLOTS=TRACE|AUTOCORR|DENSITY|ALL option performs diagnostic plots, the SAMPLING=ARMS|GIBSS|GAMERMAN|GAM|IN option uses different sampling types and STATISTICS=ALL produces all output statistics), CLASS defines categorical variables of the model, EFFECTPLOT produces graphs of the estimated model (BOX, CONTOUR, FIT, INTERACTION and SLICEFIT options can be specified), EXACT runs exact tests for the specified parameters, EXACTOPTIONS collects the options to be applied to EXACT (the most important option is METHOD = DIRECT |NETWORK| NETWORKMC to specify the algorithm EXACT uses), FWDLINK specifies the link function if not done in MODEL, INVLINK specifies the inverse of the link function defined in FWLINK, LSMEANS computes and computes fixed effects means (the CL option computes confidence intervals for means and differences of effects means, PLOTS=ALL performs plots of means and comparisons of means, MEANS computes effect means and ALPHA=α sets the levelα for confidence), MODEL defines the model to estimate, OUTPUT specifies the output to send to file and the BY, FREQ and WEIGHT options have the same familiar functionality as in all SAS procedures.

The GENMOD options are as follows:

![Interfaz de usuario gráfica, Texto, Aplicación Descripción generada automáticamente con confianza media](d2d_images/image108.png)

![Texto Descripción generada automáticamente](d2d_images/image486.png)

The options of the MODEL statement are as follows:

![Tabla Descripción generada automáticamente](d2d_images/image646.png)

![Tabla Descripción generada automáticamente con confianza media](d2d_images/image620.png)

The possible values for the link function are:

![Interfaz de usuario gráfica Descripción generada automáticamente con confianza media](d2d_images/image444.png)

As a first example we consider an experiment comparing the effects of five different drugs, each of which is tested on a number of different subjects. The outcome of each experiment is the presence or absence of a positive response in one subject. The data collected represent the number of responses r in the n subjects for the five different drugs, labelled from A to E. The response is measured for different levels of a continuous covariate x for each drug. The type of drugs and the covariate x are explanatory variables in this experiment. The number of responses r is modelled as a binomial random variable for each combination of the values of the explanatory variables, with the binomial parameter whose parameter n is the number of subjects and whose parameter p is the probability of a response. The aim is to fit a logit model that estimates the probability of response as a function of the covariate x and the type of drug.

We will use logistic regression as a generalised linear model with a response equal to the binomial r/n ratio. The probability distribution (family) is binomial, and the link function is logit. The SAS syntax will be as follows:

![image](d2d_images/image509.png)

The output is as follows:

![image](d2d_images/image220.png)

![image](d2d_images/image267.png)

Good p-values are observed for the estimated parameters, except for the constant. In the following we will estimate the model without constant and with tabular and graphical diagnostic statistics. The syntax will be as follows:

![image](d2d_images/image383.png)

The new output is shown below.

![image](d2d_images/image192.png)

![image](d2d_images/image380.png)

We now observe a good fit and an acceptable diagnosis. The diagnostic plots below are acceptable, as all the plots have random clouds, except the plot of observed versus predicted values which evidently fits well to the diagonal of the first quadrant. The Cook's cloud has a candidate outlier residual, but this is counterbalanced by the Leverage cloud which shows no influential observations in the model fit.

![image](d2d_images/image691.png)

![image](d2d_images/image454.png)

![image](d2d_images/image639.png)

The prediction equation of the fitted logit  model will be as follows:

![Tabla Descripción generada automáticamente](d2d_images/image357.png)

––––––––

![image](d2d_images/scene_break.png)

As a second example, we know that the Poisson distribution can be used to model the distribution of box counts in a multi-way contingency table. This method can be used to model insurance claims information with the data qualified by two factors: age group (with two levels) and type of car (with three levels). The variable n represents the number of insurance policies and the variable c represents the number of insurance claims. The variable car is the type of car concerned (classified into three groups) and the variable age is the age group of the policyholder (classified into two groups). We will use PROC GENMOD to carry out a Poisson regression analysis of these data with a log link function estimating the probability of insurance claims. This type of model is sometimes referred to as a log-linear model.

The syntax is as follows:

![image](d2d_images/image515.png)

The output is as follows:

![image](d2d_images/image178.png)

![image](d2d_images/image551.png)

A good fit of the Poisson model is observed with all parameters highly significant (very small Chi-square p-values).

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.5  ​GENERALISED LINEAR MODELS WITH SPSS

![image](d2d_images/chapter_title_below.png)

IBM SPSS implements generalised linear models in the path Analyse → Generalised Linear Models →Generalised Linear Models (Figure 2-1).

![image](d2d_images/image674.png)

Figure 2-1

In addition to the default model types offered by SPSS, in the Model Type screen, Custom option, it is possible to choose the family of the Distribution of the dependent variable and the Link Function (Figure 2-2).

![image](d2d_images/image489.png)

Figure 2-2

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.5.1  ​Types of models

![image](d2d_images/chapter_title_below.png)

The different types of models are obtained by specifying the Distribution (y) and the Link Function (g) of the model. This results in a number of common models that are classified by response type.

Scale response. The following options are commonly used:

  Linear. Specifies the normal distribution and the identity link function.

  Gamma with log link. Specifies the gamma distribution and the log link function.

Ordinal response. The following options are commonly used:

  Ordinal logit. Specifies the multinomial (ordinal) distribution and the cumulative logit link function.

  Ordinal probit. Specifies the multinomial (ordinal) distribution and the cumulative probit link function.

Counts. The following options are commonly used:

  Poisson log-linear. Specifies the Poisson distribution and the log link function.

  Negative binomial with log link. Specifies the negative binomial distribution (with the value 1 for the auxiliary parameter) and the log link function. To have the procedure calculate the value of the auxiliary parameter, specify a custom model with negative binomial distribution and select Estimate value in the parameter group.

Binary response or Event/trial data. The following options are typically used:

  Binary logit. Specifies the binomial distribution and the logit link function.

  Binary probit. Specifies the binomial distribution and the probit link function.

  Interval censored survival. Specifies the binomial distribution and the complementary log-log link function.

Combination. The following options are commonly used:

  Tweedie with log link. Specifies the Tweedie distribution and the log link function.

  Tweedie with identity linking. Specifies the Tweedie distribution and the identity link function.

Customised. Sometimes a combination of distribution and customised link function is used.

The possibility of specifying a specific distribution for the dependent variable other than the normal distribution and the possibility of specifying a link function other than the identity is the main improvement of the generalised linear model over the general linear model. There are many possible combinations of distribution and link function, several of which may be appropriate for a given data set, so their choice may be guided by a priori theoretical considerations and by which combinations seem to work best.

  Binomial. This distribution is suitable only for variables that represent a binary response or a number of events.

  Gamma. This distribution is suitable for variables with positive scale values that deviate towards larger positive values. If a data value is less than or equal to 0 or is a missing value, the corresponding case shall not be used in the analysis.

  Inverse Gaussian. This distribution is suitable for variables with positive scale values that skew towards larger positive values. If a data value is less than or equal to 0 or is a missing value, the corresponding case shall not be used in the analysis.

  Negative binomial. This distribution considers the number of attempts needed to achieve k successes and is suitable for variables that have integer values that are not negative. If a data value is not integer, is less than 0 or is a missing value, the corresponding case shall not be used in the analysis. The value of the auxiliary parameter of the negative binomial distribution can be any number greater than or equal to 0; it can be set to a fixed value or left to be estimated by the procedure; when the auxiliary parameter is set to 0, using this distribution is equivalent to using the Poisson distribution.

  Normal. It is suitable for scaled variables whose values adopt a symmetrical bell-shaped distribution around a central value (the mean). The dependent variable must be numerical.

  Poisson. This distribution considers the number of occurrences of an event of interest in a fixed period of time and is appropriate for variables that have non-negative integer values. If a data value is not integer, is less than 0 or is a missing value, the corresponding case shall not be used in the analysis.

  Tweedie. This distribution is suitable for variables that can be represented by Poisson mixtures of gamma distributions; the distribution is a "mixture" in the sense that it combines the properties of continuous (takes non-negative real values) and discrete (positive probability mass at a single value, 0) distributions. The dependent variable must be numeric and the data values must be equal to or greater than zero. If a data value is less than 0 or is a missing value, the corresponding case shall not be used in the analysis. The fixed value of the Tweedie distribution parameter can be any number greater than one and less than two.

  Multinomial. This distribution is suitable for variables representing an ordinal response. The dependent variable can be numeric or string, and must have at least two different valid values of the data.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.5.2  ​Liaison functions

![image](d2d_images/chapter_title_below.png)

The link function g is a transformation of the dependent variable that allows the estimation of the model. The following functions are commonly used:

  Identity. g(x)\=x. The dependent variable is not transformed. This link can be used with any distribution.

  Complementary log-log. g(x)=log(-log(1-x)). It is appropriate only for the binomial distribution.

  Cumulative cauchit. g(x) = tan(π (x \- 0.5)), applied to the cumulative probability of each category of the response. It is appropriate only for the multinomial distribution.

  Cumulative complementary log-log. ![image](d2d_images/image111.png), applied to the cumulative probability of each category of the response. It is appropriate only for the multinomial distribution.

  Cumulative logit. g(x)=ln(x / (1-x)), applied to the cumulative probability of each category of the response. It is appropriate only for the multinomial distribution.

  Cumulative negative log-log. ![image](d2d_images/image214.png). applied to the cumulative probability of each response category. It is appropriate only for the multinomial distribution.

  Cumulative Probit.![image](d2d_images/image302.png)applied to the cumulative probability of each category of the response, where![image](d2d_images/image286.png)is the inverse standard normal cumulative distribution function. It is appropriate only for the multinomial distribution.

  Logarithm. ![image](d2d_images/image449.png)This link can be used with any distribution.

  Log complement. ![image](d2d_images/image127.png)It is appropriate only for the binomial distribution.

  Logit. ![image](d2d_images/image349.png)It is appropriate only for the binomial distribution.

  Negative binomial. ![image](d2d_images/image470.png)where k is the auxiliary parameter of the negative binomial distribution. It is appropriate only for the negative binomial distribution.

  Negative log-log. ![image](d2d_images/image064.png)It is appropriate only for the binomial distribution.

  Probability power.![image](d2d_images/image613.png)α is the required number specification and must be a real number. It is appropriate only for the binomial distribution.

  Probit. ![image](d2d_images/image406.png), where Φ^(−1) is the inverse standard normal cumulative distribution function. It is appropriate only for the binomial distribution.

  Power. ![image](d2d_images/image332.png)if α=0. α is the required number specification and must be a real number. This link can be used with any distribution.

As an example, we consider the logitb.sav file containing data from a sample of 53 prostate cancer patients measuring age, the acid level that measures the extent of the tumour, the aggressiveness of the tumour, the stage of the tumour, the results of an X-ray and when the cancer was detected by surgery to have spread to the lymph nodes. From these data, the aim is to fit a model that can predict when the cancer does (or does not) spread to the lymph nodes without the need for surgery.

As the dependent variable is categorical with two mutually exclusive values, we use binary logistic regression. To perform a binary logistic regression analysis via generalised linear models we use Analyse → Generalised linear models →Generalised linear models (Figure 2-1). In the Model Type tab of the Generalised Linear Models wizard we choose Binary Logistic (Figure 2-3). In the Response tab choose the dependent variable of the model (Figure 2-4). In the Predictive tab you choose the independent variables of the model (Figure 2-5). In the Model tab you set the Factors and Covariates and their interactions (Figure 2-6). In the Statistics tab, the output statistics are chosen. The rest of the tabs are left with their default values. Click OK to obtain the model estimation.

![image](d2d_images/image561.png)

Figure 2-3

![image](d2d_images/image344.png)

Figure 2-4

![image](d2d_images/image689.png)

Figure 2-5

![image](d2d_images/image073.png)

Figure 2-6

![image](d2d_images/image255.png)

Figure 2-7

In the output we observe that the family is the binomial and the link function is the logit function, since the model is logistic (Figure 2-8).

![image](d2d_images/image519.png)

Figure 2-8

In Figure 2-9 we see the Omnibus contrast which indicates that the overall significance of the model is very good (very small p-value) and the contrasts of the model effects show good significance.

![image](d2d_images/image233.png)

Figure 2-9

Finally, the estimation of the Logit model fitted to the data is presented (Figure 2-10).

![image](d2d_images/image271.png)

Figure 2-10

The prediction equation of the estimated Logit model will be:

![Tabla Descripción generada automáticamente](d2d_images/image417.png)

As a second example we carry out the previous exercise by fitting a Probit model for the same data.

To fit a probit model, we fill in the Model Type tab of the generalised linear model wizard by choosing Binary Probit (Figure 2-11).

![image](d2d_images/image637.png)

Figure 2-11

Figures 2-12 to 2-14 present the model fit for a Binomial probability family with Probit link function. The model has a good overall fit (Omnibus contrast with small p-value), significant effects and parameter estimates with acceptable small p-values.

![image](d2d_images/image152.png)![image](d2d_images/image131.png)

Figure 2-12    Figure 2-13

![image](d2d_images/image562.png)

Figure 2-14

The prediction equation of the estimated Probit model will be:

![Imagen que contiene Tabla Descripción generada automáticamente](d2d_images/image076.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.6  ​GENERALISED LINEAR MODELS WITH R

![image](d2d_images/chapter_title_below.png)

In R, advanced models can be adjusted through the glm command, the general syntax of which is as follows:

![image](d2d_images/image652.png)

The families and their default links that can be used are as follows:

![image](d2d_images/image172.png)

The following information can be obtained for a GLM model:

 
| summary(r) || Shows detailed results of the fitted model |
| --- | --- |
| coefficients(r) || List the fitted parameters of the model |
| confint(r) || List the 95% confidence intervals for the estimated model parameters. |
| plot(hatvalues(model)) || List predicted values in the fitted model |
| residuals(r) || List the residuals of the fitted model |
| anova(r) || List the ANOVA table of the fitted model |
| plot(rstudent(model)) || Graph the waste studied |
| influencePlot(model) || Spot the leverage points |
| plot(cooks.distance(model)) || Detects atypical waste |
| plot(r) || Displays graphical diagnostics for the fitted model |
| predict(r) || Predicts values with the fitted model |

As a first example, we fit a logit model that predicts the probability of car breakdowns as a function of fuel consumption, power and engine.

![image](d2d_images/image575.png)

We observe that the fit is quite good. The predictive equation of the model fit is as follows:

![image](d2d_images/image402.png)

To fit a probit model to the above case we use the following syntax:

![image](d2d_images/image485.png)

The output is as follows:

![image](d2d_images/image187.png)

The full output can be seen below:

![image](d2d_images/image698.png)

We note that the fit is quite good. The predictive equation for the model fit is as follows:

![image](d2d_images/image321.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.7  ​​Generalised linear models IN R THROUGH MENUS

![image](d2d_images/chapter_title_below.png)

The General linear model sub-option of the Fit models option of the Statistics menu allows (Figure 2-15) to fit generalised linear, logit, probit, clogloglog and other models. Filling in the input screen as shown in Figure 2-16 yields the output for the binomial logit model shown on the next page.

![image](d2d_images/image292.png)

Figure 2-15

![image](d2d_images/image222.png)

Figure 2-16

![image](d2d_images/image711.png)

It is observed that the fit of the binomial logit model explaining the probability of car failure as a function of fuel consumption, power, engine and weight is correct as the p-values of the estimated parameters are very low. The estimated predictive equation of the model is as follows:

![image](d2d_images/image225.png)

If we want to perform the above adjustment using a probit model we fill in the input screen as shown in Figure 2-17. Clicking OK produces the output on the next page.

![image](d2d_images/image634.png)

Figure 2-17

![image](d2d_images/image390.png)

![image](d2d_images/image696.png)

It is observed that the fit of the binomial probit model explaining the probability of car failure as a function of fuel consumption, power, engine and weight is correct as the p-values of the estimated parameters are very low. The predictive equation of the estimated model is as follows:

![image](d2d_images/image330.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 2.8  ​Generalised linear models THROUGH STATGRAPHICS CENTURION

![image](d2d_images/chapter_title_below.png)

STATGRAPHICS incorporates the Logit, Probit, Poisson and Negative Binomial models in the Relate → Attribute Data option (Figure 2-18).

![image](d2d_images/image678.png)

Figure 2-18

As an example we consider file 7-10.xls contains information on the variable narr86 which represents the number of times a man is arrested during 1986 and which we wish to explain by the variables pcnv (proportion of previous arrests in which he was convicted), avgsen (average length of sentences in months), tottime (time in prison in months), ptime86 (time in prison in 1986 in months), qemp86 (quarters employed in 1986), inc86 (legal income in 1986 in hundreds of dollars), black (dummy worth 1 for black arrestee), hispan (dummy worth 1 for hispanic arrestee) and born60 (dummy worth 1 if arrestee was born in 1960).

As the explained variable takes the value 0 in a large number of cases and only takes a value greater than 5 in 8 cases, a count data model could be used. The aim is to study the effect of the explanatory variables on the explained variable using Poissson count data, exponential and negative binomial. Compare the models.

To  fit our problem to a Negative Binomial model we use Relate → Attribute Data → Negative Binomial Regression (Figure 2-19) and fill in the input screen of the procedure as indicated in Figure 2-20.

![image](d2d_images/image017.png)

Figure 2-19

![image](d2d_images/image621.png)

Figure 2-20

OK is pressed and the Negative Binomial Regression Options screen is filled in as shown in Figure 2-21. The Tables and graphs screen is populated as shown in Figure 2-22.

![image](d2d_images/image368.png)

Figure 2-21

![image](d2d_images/image092.png)

Figure 2-22

The Analysis Summary  output shows a very good model fit with very good joint significance and acceptable coarse individual significance of the estimated parameters (except perhaps AVGSEN and BORN60 which are significant at approximately 50%).

![image](d2d_images/image398.png)

![image](d2d_images/image699.png)

![image](d2d_images/image230.png)

It is observed that the predictive equation of the estimated Negative Binomial model is as follows:

![image](d2d_images/image399.png)

The 95% confidence intervals for the estimated parameters are presented in the table below:

95.0% confidence intervals for coefficient estimates

 
|  ||  || Error ||  ||  |
| --- | --- | --- | --- | --- |
| Parameter || Dear || Standard || Lower Limit || Upper Limit |
| CONSTANT || 0,510418 || 0,0891951 || 0,335599 || 0,685238 |
| PCNV || \-0,401615 || 0,0717093 || \-0,542163 || \-0,261067 |
| AVGSEN || \-0,0238654 || 0,0156566 || \-0,0545519 || 0,00682115 |
| TOTTIME || 0,0245856 || 0,0113967 || 0,00224842 || 0,0469228 |
| PTIME86 || \-0,0985997 || 0,0182358 || \-0,134341 || \-0,0628582 |
| QEMP86 || \-0,0380555 || 0,0241328 || \-0,0853549 || 0,00924395 |
| INC86 || \-0,00808062 || 0,000930773 || \-0,00990491 || \-0,00625634 |
| BLACK=0 || \-0,661117 || 0,0593497 || \-0,77744 || \-0,544793 |
| HISPAN=0 || \-0,499853 || 0,0612882 || \-0,619976 || \-0,37973 |
| BORN60=0 || 0,0510633 || 0,0525824 || \-0,0519964 || 0,154123 |

![Tabla Descripción generada automáticamente](d2d_images/image493.png)

![image](d2d_images/image468.png)

The above model is then fitted using a Poisson regression model. To do this we use Relate → Attribute Data → Poisson Regression (Figure 2-23) and fill in the input screen of the procedure as shown in Figure 2-24.

![image](d2d_images/image457.png)

Figure 2-23

![image](d2d_images/image705.png)

Figure 2-24

OK  is pressed and the Poisson Regression Options screen is populated as shown in Figure 2-25. The Tables and Graphs screen is populated as shown in Figure 2-26.

![image](d2d_images/image438.png)

Figure 2-25

![image](d2d_images/image100.png)

Figure 2-26

The Analysis Summary  output shows a very good model fit with very good joint significance and acceptable coarse individual significance of the estimated parameters (except perhaps BORN60 which is significant at about 60%). The fit is better than in the previous case of the Negative Bnomial.

![image](d2d_images/image423.png)

![image](d2d_images/image351.png)

![image](d2d_images/image564.png)

The predictive equation of the estimated Poisson model is as follows:

![image](d2d_images/image428.png)

The 95% confidence intervals for the estimated parameters are as follows:

![image](d2d_images/image612.png)

![image](d2d_images/image615.png)

Exercise 2-1. File 7-10.sav contains information on the variable narr86 which represents the number of times a man is arrested during 1986 and which is to be explained by the variables pcnv (proportion of previous arrests in which he was convicted), avgsen (average length of sentences in months), tottime (time in prison in months), ptime86 (time in prison in 1986 in months), qemp86 (quarters employed in 1986), inc86 (legal income in 1986 in hundreds of dollars), black (dummy worth 1 for black arrestee), hispan (dummy worth 1 for hispanic arrestee) and born60 (dummy worth 1 if arrestee was born in 1960).

As the explained variable takes the value 0 in a large number of cases and only takes a value greater than 5 in 8 cases, a count data model could be used. Study the effect of the explanatory variables on the explained variable using Poissson count data, exponential and negative binomial. Compare the models. Use SPSS software.

We start by using the option Analyse → Generalised Linear Models → Generalised Linear Models. In the Model Type tab of the wizard we choose Negative Binomial with log link (Figure 2-27).

![image](d2d_images/image039.png)

Figure 2-27

The Response, Predictors, Model and Statistics  tabs are filled in as shown in Figures 2-28 to 2-31.

![image](d2d_images/image364.png)

Figure 2-28

![image](d2d_images/image466.png)

Figure 2-29

![image](d2d_images/image413.png)

Figure 2-30

![image](d2d_images/image130.png)

Figure 2-31

Pressing OK produces the output presented in Figures 2-32 to 2-34. A fit with Negative Binoial Probability Family and Log Link Function is observed. The individual and joint significance of the estimated parameters is quite acceptable.

![image](d2d_images/image247.png)![image](d2d_images/image341.png)

Figure 52-32

![image](d2d_images/image244.png)

Figure 2-33

It can be seen that the estimated predictive model does not coincide exactly with that obtained in STATGRAPHICS, but it is practically similar.

To estimate the same model using a Poisson regression, fill in the Model Type tab of the generalised linear models wizard by choosing Poisson Loglinear (Figure 2-34).

![image](d2d_images/image660.png)

Figure 2-34

Pressing OK produces the output presented in Figures 2-35 to 2-37. A fit with Poisson likelihood family and Log link function is observed. The individual and joint significance of the estimated parameters is quite acceptable.

It can be seen that the estimated predictive model does not coincide exactly with that obtained in STATGRAPHICS, but it is practically similar.

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image087.png)![image](d2d_images/image408.png)

Figure 2-35    Figure 2-36

![image](d2d_images/image680.png)

Figure 2-37

Exercise 2-2. Consider the logitb.sav file containing data from a sample of 53 prostate cancer patients, measuring age, the acid level that measures the extent of the tumour, the aggressiveness of the tumour, the stage of the tumour, the results of an X-ray, and when the cancer was detected by surgery to have spread to the lymph nodes. From these data, the aim is to fit a model that can predict when the cancer does (or does not) spread to the lymph nodes without the need for surgery.

We start by reading the logitb.sav file, looking at its contents and enabling its variables.

![image](d2d_images/image709.png)

We then adjust the ordered logít model.

![image](d2d_images/image228.png)

![image](d2d_images/image590.png)

It is observed that the constant is not significant. We will then fit the model without constant.

![image](d2d_images/image278.png)

The model is now more or less acceptable, except perhaps for the GRADE variable whose significance is 70%.

Exercise 2-3. Solve the previous exercise using a Probit model.

We start by estimating the model using a probit  regression.

![image](d2d_images/image193.png)

It is observed that the constant is not significant, which leads us to estimate the model without constant.

![image](d2d_images/image393.png)

![image](d2d_images/image097.png)

The model is already more or less acceptable, except perhaps for the GRADE variable whose significance is 70%. The results are very similar to the case of the logit model.

3Chapter 3

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# LIMITED DEPENDENT VARIABLE, DISCRETE CHOICE, COUNT, CENSORED, TRUNCATED AND SAMPLE SELECTION MODELS. TREATMENT WITH STATA

![image](d2d_images/chapter_title_below.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.1  ​limited dependent variable models

![image](d2d_images/chapter_title_below.png)

The functional expression of the multiple regression analysis model is![image](d2d_images/image451.png). Multiple regression admits the possibility of working with dependent variables whose range of values is restricted (binary variables with values 0 and 1, variables with positive integer values, etc.). In general, models that admit dependent variables with restricted range are called limited dependent variable models. 

Most of the economic variables under analysis have values that are constrained in some way, often because they must be positive. For example, hourly wages, house prices, and nominal interest rates must be greater than zero. But not all of these variables require special treatment. No special econometric model is usually needed to deal with variables that are strictly positive but take many different values. When the dependent variable is discrete (discrete choice models) and takes a small number of values, it does not make sense to treat it as if it were an approximately continuous variable. The fact that the dependent variable is discrete does not necessarily imply that linear models are not appropriate. However, for binary responses (binary choice models), Logit and Probit models and in certain cases the linear probability model are often used. Also for multiple responses (multiple choice models), logit and probit models are used.

Another important example of a limited dependent variable is the count variable, which takes non-negative integer values. A count data model is one that has as its dependent variable a discrete count variable that takes non-negative integer values. Poisson regression models are appropriate for analysing count variables.

In econometric analysis, other types of limited dependent variables appear, especially when we analyse the behaviour of individuals, households, or firms. For example, suppose that during a given year a large number of households in a region do not make any charitable donations. Therefore, the population distribution of donations made by households is highly dispersed over positive values, but with a high concentration at zero. This is an example of a corner solution. The Tobit model is explicitly designed for dependent variables that have corner solutions. These variables are zero for a considerable proportion of the population but are approximately continuously distributed for positive values.

Another type of limited dependent variables are those caused by data censoring. A censored regression model is one whose dependent variable is censored above (upper censoring) or below (lower censoring) some value, i.e. the dependent variable is not observed for a part of the population. In censored regression models the underlying dependent variable is approximately continuous, but is lower or upper censored, due to the way we collect the data or to institutional constraints. A truncated regression model is similar to a censored regression model, but has one important difference: in a truncated regression model, we do not have the data about some important segment of the population. This is usually the case when a sample targets a particular subset of the population and, perhaps because it is costly, ignores the rest of the population. This is a particular case of the general problem of sample selection, where we observe a non-random sample of the underlying population.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.2  ​DISCRETE CHOICE MODELS

![image](d2d_images/chapter_title_below.png)

The functional expression of the multiple regression analysis model is![image](d2d_images/image686.png). Multiple regression admits the possibility of working with discrete rather than continuous dependent variables to allow the modelling of discrete phenomena. When the dependent variable is a discrete variable reflecting individual decisions in which the choice set consists of separate and mutually exclusive alternatives, we are dealing with discrete choice models. When the dependent variable is discrete and takes only a small number of values, it does not make sense to treat it as if it were a continuous variable and it is usually of interest to characterise the probability that an agent takes a certain discrete decision, conditional on the values of certain explanatory variables. These distribution functions that characterise probabilities for each value of the explanatory variables are usually non-linear and do not usually have an analytical solution, so it is usually necessary to resort to numerical methods. Discrete choice models in which the choice set has only two possible alternatives are called binary choice models. When the choice set has several discrete values, these are called multiple choice models or multinomial models.

Discrete choice models are called count data models when the values of the discrete dependent variable are numbers that do not reflect categories. In case the numerical values of the discrete dependent variable reflect categories, the models are called categorical discrete choice models, and are usually classified into ordered categorical discrete choice models (the numerical values have no quantitative meaning and reflect an ordering of categories) and unordered categorical discrete choice models (the numerical values reflect only categories).

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.3  ​BINARY DISCRETE CHOICE MODELS

![image](d2d_images/chapter_title_below.png)

Within the discrete choice models in which the choice set has only two mutually exclusive possible alternatives, we will consider the linear probability model, the Logit model and the Probit model.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.3.1  ​Linear probability model

![image](d2d_images/chapter_title_below.png)

![Texto, Carta Descripción generada automáticamente](d2d_images/image296.png)

We are now dealing with the linear probability model, where, for example,β1 measures the variation in the probability of "success" (Y \= 1) for a unit variation in X1 (all else constant).

As Y is a Bernouilli random variable:

![Texto, Carta Descripción generada automáticamente](d2d_images/image189.png)

We are then faced with a model with heteroscedasticity because the error variance is not constant, since for each value of X1 ,...,Xk , the error variance has a different value (V(u) is not constant). Moreover, Y is a Bernouilli variable, so that the normality hypothesis is not satisfied either. This makes it necessary to estimate these models by an alternative method to ordinary least squares, for example, using maximum likelihood estimators or generalised least squares.

After estimating the linear probability model we have that:

![image](d2d_images/image431.png)

can be interpreted as an estimate of the probability of "success" (that Y \= 1). In some applications it makes sense to interpret![image](d2d_images/image086.png)as the probability of success when all X'sj are worth 0.

Another important limitation of the linear probability model is that for certain combinations of the explanatory variables X1 ,...,Xk , the estimated probabilities may be greater than zero or less than one.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.3.2  ​Probit and Logit models

![image](d2d_images/chapter_title_below.png)

We can consider Logit and Probit models as binary response models:

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image014.png)

which, to avoid the problems of the linear probability model, are specified as Y = G(Xβ), where G is a function that takes values strictly between 0 and 1 (0<G(Z)<1) for all real numbers z. According to the different definitions of G we have the different binary choice models.

![Texto, Carta Descripción generada automáticamente](d2d_images/image631.png)

The Probit and Logit  models, as they are non-linear models, cannot be estimated by OLS and maximum likelihood methods have to be used.

Suppose we have n identically and independently distributed observations (random sample) that follow the model:

![Texto Descripción generada automáticamente](d2d_images/image030.png)

The MV estimator ofβ is the one that maximises the logarithm of the likelihood function:

![image](d2d_images/image091.png)

which will be a consistent, asymptotically normal and asymptotically efficient estimator.

The first-order conditions shall be:

![Diagrama Descripción generada automáticamente con confianza media](d2d_images/image280.png)

where g(.) is the normal or logistic density function (derived from the distribution function).

The non-linearity of the problem means that to obtain the MV estimator fromβ we need to apply an iterative algorithm and obtain the estimator by iterative numerical methods. By means of the Scoring algorithm we have:

![Diagrama, Texto Descripción generada automáticamente](d2d_images/image044.png)

To perform hypothesis tests in Logit and Probit models we will take into account that the square root of the elements of the main diagonal of the asymptotic covariance matrix are the (asymptotic) standard errors of each of the![image](d2d_images/image379.png), which we can use to construct t-statistics (which will have an asymptotic normal distribution) or approximate confidence intervals for each parameter. We can also test several restrictions simultaneously. Usually, what we are interested in are exclusion restrictions, so this is what we are going to focus on.

To test the null hypothesis that a set of parameters is equal to zero we can use several procedures:

*   Wald statistic. It is asymptotically distributed as a Chi-square with q (number of restrictions) degrees of freedom and is provided by most programs.

*   Likelihood Ratio (LR) test. It is based on the difference between the logarithm of the likelihood function in the unconstrained and the constrained model:

![image](d2d_images/image559.png)

which is asymptotically distributed as a Chi-square with q degrees of freedom.

As for the goodness-of-fit measures in the Logit and Probit models we have:

*   Percentage of correct predictions. For each i we calculate the estimated probability that Yi = 1:

![image](d2d_images/image440.png)

*   If![image](d2d_images/image118.png)our prediction will be that Yi is 1 and if![image](d2d_images/image118.png)our prediction will be that Yi is 0. The % of times that the observed value of Yi matches the prediction is the % of correct predictions. The interesting thing is to calculate separately the % of correct predictions of zeros and ones.

*   Pseudo-R² (McFadden's). It is based on the logarithm of the likelihood function:

![image](d2d_images/image626.png)

![Texto Descripción generada automáticamente con confianza media](d2d_images/image657.png)

*   Information Criteria. These are measures that attempt to strike a balance between goodness of fit, as measured by the value of the logarithm of the likelihood function, and a parsimonious specification of the model. (Examples: Akaike (AIC), Schwarz (SC) and Hannan-Quinn (HQ).) The model with the lowest value of the information criterion is chosen.

When interpreting the estimates in the Probit and Logit models, what generally interests us is to know the effect of variations in a variable Xj on the probability of response, which if the variable is continuous will be:

![image](d2d_images/image642.png)

As![image](d2d_images/image226.png)depends on X, it is necessary to calculate the partial effects for interesting values of X (sample means, maximum and minimum values of the variables of interest, etc.). One can also calculate the partial effect for each individual and then calculate its mean.

The partial effect of a continuous variable Xj on the response probability P(Y \= 1|X) will be:

![image](d2d_images/image046.png)

where g(.) is the logistic (logit) or standard normal (probit) density function. This effect varies from individual to individual. As in the case of Probit and Logit, g(z)>0 for all z, the sign of the partial effect of Xj is the same as that ofβj .

The relative effect of two continuous variables Xj and Xh does not depend on X. Note that the quotient of the partial effects isβj /βh .

If X1 , for example, is a dummy explanatory variable, the partial effect of it varying from 1 to 0 will be given by:

![image](d2d_images/image300.png)

which also varies from one individual to another, as it depends on the values of all X'sj .

As in the Probit g(0) ≈ 0.4, in the Logit g(0) ≈ 0.25 and in the MPL g(0) = 1, the following relationship between the estimates can be obtained:

![image](d2d_images/image490.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.4  ​MULTIPLE CHOICE MODELS

![image](d2d_images/chapter_title_below.png)

The models studied so far are discrete choice models in which the choice set has only two possible alternatives and which are called binary choice models. But when the choice set has several discrete values, we are dealing with multiple choice models or multinomial models. We will now study the most common ones.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.4.1  ​Multinomial Logit Model

![image](d2d_images/chapter_title_below.png)

The Multinomial Logit Model is an extension of the binary model for the case where the response, "unordered", has more than 2 possibilities. Let (Xi , Yi ) be a random sample of the population (i \= 1..n).

As in the binary case, we are interested in how changes in the elements of X affect the response probabilities:

![Texto Descripción generada automáticamente con confianza media](d2d_images/image305.png)

If J=1, we are in the binary case.

In these models the partial effects are complicated and even the sign of the parameter does not give the sign of the effect. If Xk is continuous, the partial effect will be:

![Texto, Carta Descripción generada automáticamente](d2d_images/image496.png)

It is noted that:

![Texto, Carta Descripción generada automáticamente](d2d_images/image683.png)

The probability of choosing j, if the choice is between j and h, follows a standard Logit model with parameter vectorβj -βh :

![Texto, Carta Descripción generada automáticamente](d2d_images/image289.png)

and in general we will obtain consistent and asymptotically normal estimators.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.4.2  ​Conditional Logit Model

![image](d2d_images/chapter_title_below.png)

The Conditional Logit Model is used for problems where the individual's (or firm's) choices are made, at least in part, on the basis of the observable attributes of each alternative. In the Multinomial Logit, the explanatory variables do not change between alternatives, i.e., for each i, Xi contains variables specific to the individual, not to the alternatives, and is appropriate for situations where the characteristics of the alternatives are not important (or we do not observe them). In the Conditional Logit Model, for each i, Xi contains individual-specific and alternative-specific variables and is appropriate for situations where alternative characteristics are observed.

Suppose we have a random sample of size n from the underlying population (i \= 1,..., n). The utility of choosing alternative j is:

![image](d2d_images/image290.png)

where aij are unobservables that affect tastes and Xij varies between alternatives (and maybe also between individuals) but cannot contain elements that only vary between individuals (contains no constant term).

As an example we can consider the time taken to get to work by individual i using means of transport j or the cost of transport j (which may or may not vary between individuals).

If the disturbances atij are independently distributed with Weibull distribution with:

![Texto, Carta Descripción generada automáticamente](d2d_images/image284.png)

whereβk is the k-th element ofβ .

The estimation of the Conditional Logit Model is performed by the maximum likelihood method.

In the Conditional Logit Model the assumption of independence of irrelevant alternatives IAI is also satisfied because the ratio of probabilities of choice between 2 alternatives (Y= j instead of Y=h) is independent of the remaining alternatives. One has

![image](d2d_images/image571.png)

The assumption of independence of irrelevant alternatives IAI, which is derived from the assumption of independence of disturbances, is convenient for estimation, but may be a limitation, as in some applications with similar alternatives it is unrealistic. The assumption of independence of irrelevant alternatives IAI assumes that the relative likelihood of two existing alternatives is not affected by the inclusion of a third alternative. The IAI assumption can be tested using the test suggested in Hausman and McFadden.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.4.3  ​Nested Logit Model

![image](d2d_images/chapter_title_below.png)

The Nested Logit Model is a particular case of the Conditional Logit Model in which the IAI assumption is relaxed by grouping the J alternatives into L subgroups of similar alternatives. It is widely used to model consumption decisions. IAI is still maintained within each group but not between groups. The choice process is considered as first choosing one of the L groups P(Y G∈L |X) and then, within that group, the alternative j P(Y = j|Y G∈L ,X). The object of interest P(Y = j| X) is obtained by multiplying the two previous ones.

The Nested Logit Model can be estimated by the maximum likelihood method with full information (both decisions) or in 2 stages (Conditional Logit for the choice of each j in each group and then the probability of choosing group L).

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.4.4  ​Multinomial Probit Model

![image](d2d_images/chapter_title_below.png)

When in a conditional logit model the IAI assumption can be relaxed by using models with more flexible assumptions about aij , the multinomial probit model can be obtained as a particular case of this.

Suppose that aij follows a multivariate normal distribution with arbitrary correlations between aij and aih (with j≠ h) we have the Multinomial Probit Model. Although this model is theoretically attractive, the response probabilities are very complicated and maximum likelihood estimation is almost impossible with more than 5 alternatives. Recent econometric advances are making it easier to use these models.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.5  ​ORDERED LOGIT AND PROBIT MODELS

![image](d2d_images/chapter_title_below.png)

The multiple choice models seen so far do not take the ordinal nature of Y into account. Sometimes in multiple choice models Y is an ordered response and the value assigned to each alternative is not arbitrary. We are then dealing with ordered response models. For example, when Y can reflect the valuation of a credit, it is a scale from 0 to 6.

Let Y be an ordered response variable taking values {0, 1, 2, ..., J}. The ordered Probit (or Logit) model for Y (conditional on explanatory variables X) can be derived from a latent variable model:

![Texto, Carta Descripción generada automáticamente](d2d_images/image404.png)

If J=1 we have the binary Probit with the constant \-α1 included inside Ф(.) (in binaries we usually set the cut-off point to zero and estimate the constant).

The parameters α andβ can be estimated by the maximum likelihood method. If instead of using Ф(.) we use the logistic Λ(.) we will have the Ordered Logit Model.

For the Ordered Probit we have that the partial effects are:

![Texto, Carta Descripción generada automáticamente](d2d_images/image452.png)

The sign ofβk only determines the sign of the partial effect for P(Y=0|X) and P(Y=J|X), but not for the rest.

We can apply these ordered response models in cases where Y has a quantitative meaning but we are also interested in knowing the nature of the discrete ordered response. In these cases we may be interested in knowing:

![image](d2d_images/image430.png)

where a0 , a1 , ..., aJ are the values that the variable takes. Once we estimate the probabilities we can estimate E(Y|X) for any value of X we are interested in.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.6  ​COUNT DATA MODELS

![image](d2d_images/chapter_title_below.png)

An important type of limited dependent variable is the count variable, which takes non-negative integer values. A count data model is one that has as its dependent variable a discrete count variable that takes non-negative integer values. Poisson regression models are appropriate for analysing count variables. Exponential regression models and Negative Binomial regression models are also appropriate.

Count data models are characterised by the fact that they generally do not have a natural upper limit, take zero for some members of the population and usually take few values.

If Y is the count variable and![image](d2d_images/image463.png)are the explanatory variables, we will normally be interested in:

![image](d2d_images/image654.png)

In cases where Y is strictly positive we can employ the log(Y) transformation and use the linear model. However, in count data Y usually takes zero for a non-negligible percentage of the population. With count data we usually model![image](d2d_images/image410.png)by choosing functional forms that ensure positive values for all X and all parameter values.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.6.1  ​Poisson Regression Model

![image](d2d_images/chapter_title_below.png)

For count data, where the variable Y takes few values, it is most common to assume that Y given![image](d2d_images/image463.png)follows a Poisson distribution. The Poisson distribution is completely determined by its mean, so it is sufficient to specify![image](d2d_images/image265.png):

![Texto, Carta Descripción generada automáticamente](d2d_images/image622.png)

We can interpret the coefficients as if they were a linear model with dependent variable in logarithm.

We can measure the exact % variation at![image](d2d_images/image410.png)for a unit variation of Xk by![image](d2d_images/image324.png)

![Diagrama Descripción generada automáticamente con confianza media](d2d_images/image161.png)

Based on the assumptions we have made about the Poisson distribution and about the form of conditional expectation, we can construct the logarithm of the likelihood function as:

![image](d2d_images/image142.png)

where the term -log(Yi!) has been removed because it does not depend on![image](d2d_images/image007.png).

Maximising this function yields the MV estimator of![image](d2d_images/image007.png), which if the conditional distribution of Y is Poisson and the![image](d2d_images/image585.png)is well specified will be consistent, efficient and asymptotically normal. From these estimates the standard errors of the![image](d2d_images/image478.png)can be obtained.

Sometimes the Poisson distribution imposes restrictions that are not met in empirical applications. In particular, in the Poisson all higher order probabilities and moments are determined by the mean, so that E(Y|X) = V(Y|X). This equality does not hold in many applications. However, even if the Poisson distribution is not satisfied, we will still obtain consistent and asymptotically normal estimators of the![image](d2d_images/image260.png)if the conditional mean is well specified.

When Y given X1 , ..., Xk  does not follow a Poisson distribution the estimator obtained by maximising the logarithm of the likelihood function:

![image](d2d_images/image325.png)

is called a quasi maximum likelihood (QML) estimator. When estimating by CMV if the assumption E(Y|X) = V(Y|X) is not met, the standard errors must be adjusted to be valid, in order to make inference even if the conditional distribution of Y is misspecified. One possibility to adjust the standard errors is to assume that the variance is proportional to the mean:

![image](d2d_images/image704.png)

where![image](d2d_images/image369.png)is an unknown parameter. If![image](d2d_images/image424.png)we have the Poisson variance assumption. If![image](d2d_images/image671.png)we have overdispersion, which is what happens in many applications. If![image](d2d_images/image671.png)we have underdispersion, which is rare in empirical applications.

Under the assumption of variance proportional to the mean it is easy to adjust the Poisson standard errors obtained by maximum likelihood. They will have to be multiplied by![image](d2d_images/image525.png), where![image](d2d_images/image301.png)is a consistent estimator of![image](d2d_images/image301.png):

![image](d2d_images/image121.png)

The standard errors thus obtained are called GLM (Generalized Linear Models) standard errors. These standard errors are obtained under the assumption of variance proportional to the mean, but it is also possible to obtain standard errors for the CMV estimators of the Poisson model without restricting the variance.

Under the assumption of a Poisson distribution, for exclusion restriction tests, we can use the likelihood ratio test:

![image](d2d_images/image163.png)

which is asymptotically distributed as a Chi-square with q degrees of freedom.

Under the assumption of variance proportional to the mean, to perform exclusion restriction tests, it is sufficient to adjust the likelihood ratio test by dividing it by![image](d2d_images/image494.png)of the unrestricted model (CMV statistic). To measure the goodness of fit in these models, an R² defined as the square of the correlation coefficient between Yi and![image](d2d_images/image547.png)can be used. It has the advantage that it will always be between 0 and 1.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.6.2  ​Negative Binomial Regression Model

![image](d2d_images/chapter_title_below.png)

There are other regression models for count data using distributions that generalise the Poisson, for example using the Negative Binomial distribution. This is the Negative Binomial regression model. This model is used for cases of overdispersion since it is assumed that V(Y|X) =σ²  E(Y|X) = (1+η² ) E(Y|X). In this case the parameters![image](d2d_images/image007.png)and![image](d2d_images/image211.png)are estimated jointly by the maximum likelihood method. For the estimates to be consistent and efficient, the negative binomial assumption must be satisfied. If we estimate![image](d2d_images/image007.png)for fixed![image](d2d_images/image211.png), the estimates will be consistent if E(Y|X) is well specified.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.6.3  ​Exponential Regression Model

![image](d2d_images/chapter_title_below.png)

In the Exponential Regression Model the parameters are estimated by maximum likelihood using the exponential distribution. If E(Y|X) is well specified the estimators will be consistent even if the distribution is not exponential (like other CMV estimators). To obtain GLM errors it is assumed: V(Y|X) =σ 2 \[E(Y|X)\]2.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.6.4  ​Normal Regression Model

![image](d2d_images/chapter_title_below.png)

In the normal regression model the parameters are estimated by maximum likelihood using the normal distribution. For fixedσ 2, if E(Y|X) is well specified the estimators will be consistent even if the distribution is not normal.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.7  ​CENSORED MODELS: THE TOBIT MODEL

![image](d2d_images/chapter_title_below.png)

A certain very special type of limited dependent variables are those caused by data censoring. A censored regression model is one whose dependent variable is censored above (upper censoring) or below (lower censoring) some value, i.e. the dependent variable is not observed for a part of the population. In censored regression models the underlying dependent variable is approximately continuous, but is either under-censored or over-censored, due to the way we collect the data or to institutional constraints.

A particular case of data censoring occurs when the dependent variable is zero for a large part of the population and is continuous for positive values. We are then dealing with a bounded variable model with a corner solution. The Tobit model is explicitly designed for dependent variables that have corner solutions. These variables are zero for a considerable proportion of the population but are approximately continuously distributed for positive values.

The censored Tobit or Tobit type I regression model is expressed as follows:

![Texto, Carta Descripción generada automáticamente](d2d_images/image010.png)

We have formulated the Tobit model in terms of a latent variable Y\*, which satisfies the assumptions of the classical regression model, normally distributed, homoscedastic and with linear conditional mean.

The density of Y given X is the same as the density of Y\* given X for positive values. Moreover, we know that:

![Texto, Carta Descripción generada automáticamente](d2d_images/image513.png)

By maximising the likelihood function we obtain the MV estimators ofβ andσ . Standard errors of the estimated coefficients can be obtained and Student's t-statistics can be constructed for contrasts. The Wald statistic and RV can also be used.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.7.1  ​Interpretation of the coefficients in the Tobit model

![image](d2d_images/chapter_title_below.png)

We note that:

![Texto, Carta Descripción generada automáticamente](d2d_images/image567.png)

Then, if we estimate the Tobit model by OLS using only the observations for which Y>0, omitting the zeros, we would obtain an unbiased and inconsistent estimator ofβ , because we would omit the Mills ratio which is correlated with X.

In the Tobit model we have:

![Texto, Carta Descripción generada automáticamente](d2d_images/image501.png)

We are then faced with a non-linear function of X andβ , which allows us to conclude that if we estimate the Tobit model by OLS as a linear model with all observations we will not have consistent estimators.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.7.2  ​Partial effects in the Tobit model

![image](d2d_images/chapter_title_below.png)

If Xj is a continuous variable, the partial effect on the expected value of Y in the sub-population of positive values will depend onβj and a term between 0 and 1 and will be worth (\*):

![image](d2d_images/image589.png)

We can estimate this partial effect using the MV estimates ofβ andσ for the mean values of X or for others that are of interest in our applications. If Xj is a binary variable we can calculate the difference between E(Y|Y>0,X) for Xj = 1 and Xj = 0. Similarly this can be done for any discrete Xj .

Likewise, if Xj is a continuous variable, we can compute the partial effect on the expected value of Y. This partial effect can be decomposed into two parts, the effect on the mean value of Y in the positive part of the distribution, and the effect on the probability in the other part of the distribution. We have (\*\*):

![Tabla Descripción generada automáticamente con confianza media](d2d_images/image389.png)

This value of the effects can be easily estimated using the MV estimates ofβ andσ for the mean values of X or for other values of interest in our applications.

The Tobit model is based on the assumptions of normality and homoscedasticity in the latent model. When these assumptions are not met, the problem is not only the inconsistency of the MV estimator ofβ andσ . Even the expressions of the conditional expectation are not adequate. The model can be generalised to allow for certain forms of heteroskedasticity and non-normality. There are also tests for certain types of normality and heteroscedasticity, for example:

![image](d2d_images/image377.png)

But, for mild breaches of the assumptions, it is thought that the Tobit model can generate a good approximation of the partial effects.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.7.3  ​Tobit model with censorship in the data

![image](d2d_images/chapter_title_below.png)

We have analysed the Tobit model for corner solution, but we can generalise to the case where there is censoring of any kind in the data. The most general case is when the variable of interest is continuous but is censored above (right censoring) or below a value (left censoring) which need not be zero.

We can write the Tobit model as:

![image](d2d_images/image243.png)which can also be written as:

![Diagrama, Texto Descripción generada automáticamente con confianza media](d2d_images/image570.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.7.4  ​Maximum Likelihood (MV) estimation of the censored Tobit model

![image](d2d_images/chapter_title_below.png)

If we had a random sample we could estimateβ by OLS and perform inference in the usual way, but censoring the data causes us problems of inconsistency in OLS estimation (with all observations or without the censored ones). Given a random sample, we can obtain consistent estimates fromβ andσ if we estimate by OLS. For uncensored observations, Y = Y\*, the density of Y is the same as that of Y\*. For censored observations we have:

![image](d2d_images/image465.png)

We will calculate the logarithm of the likelihood function and perform the MV estimation. In this model theβj are interpreted as in the linear regression model.

The expression for the logarithm of the likelihood function for a sample of size n is as follows:

![image](d2d_images/image353.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.7.5  ​Two-stage ordinary least squares estimation of the censored Tobit model

![image](d2d_images/chapter_title_below.png)

Although the estimation of the OLS-censored Tobit model cannot be done directly, we can use the following two-step method:

1.  The dichotomous dummy variable is constructed which is worth 1 for positive values of Y (Yi  > 0 or Yi  > c) and which is worth 0 for values of Y less than or equal to zero (Y i≤ 0 or Y i≤ c). The corresponding Probit model is estimated and the Mills ratio is obtained from the estimated values:

![image](d2d_images/image026.png)

1.  We estimate by OLS the model ![image](d2d_images/image268.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.8  ​SAMPLE SELECTION: TRUNCATED MODELS

![image](d2d_images/chapter_title_below.png)

A truncated regression model is similar to a censored regression model, but has some important differences: in a truncated regression model, we do not have the data about some important segment of the population. This is usually the case when a sample targets a particular subset of the population and, perhaps because it is costly, ignores the rest of the population. This is a particular case of the general problem of sample selection, where we observe a non-random sample of the underlying population.

Suppose we have an underlying population model that satisfies the assumptions of the classical regression model:

![image](d2d_images/image476.png)

If we had a random sample of the population, the most efficient estimation procedure would be OLS. However, in the case of the truncated model the problem is that we do not have a random sample, because our observed sample has a bound of the type Y i≤ ci or Yi > ci (Truncated Tobit Model). If we want to estimateβ andσ we need to know the distribution of Yi given X and that Y i≤ ci   or Yi > ci . That is:

![Texto, Carta Descripción generada automáticamente](d2d_images/image051.png)

where f(Y|X ,iβσ² ) is the density of a normal with mean Xiβ and varianceσ² and F(ci |X ,iβσ² ) is the distribution function of a normal with mean Xiβ and varianceσ evaluated at ci .

If we divide the density of Y given X by the probability that Y i≤ ci or Yi > ci (given X), we take logarithms and sum for all n maximising the result we obtain the MV estimators ofβ and σ² , which will be consistent and asymptotically normal. But if the assumptions of homoscedasticity and normality are not met, the MV estimators will be inconsistent.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.8.1  ​Truncated Tobit model estimation

![image](d2d_images/chapter_title_below.png)

Let us suppose that we have a model Yi = Xiβ + ui and that the variable Yi is truncated from a certain boundary or barrier a (it only takes values from the barrier onwards). We have:

![Diagrama Descripción generada automáticamente](d2d_images/image373.png)

The truncated variable model can be specified as follows:

![image](d2d_images/image343.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.8.2  ​Partial effects in the truncated Tobit model

![image](d2d_images/chapter_title_below.png)

This involves quantifying the effect of a unit increase of a regressor Xk on the explained variable, which will be given by the partial derivative of its expected value with respect to the variable Xk we have:

![Diagrama Descripción generada automáticamente](d2d_images/image679.png)

Then the marginal effect of variable Xk with respect to the explained variable is equal to the estimated coefficientβk multiplied by the correction factor![image](d2d_images/image670.png)being:

![Imagen de la pantalla de un celular con letras Descripción generada automáticamente con confianza media](d2d_images/image376.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.8.3  ​Maximum Likelihood (MV) estimation of the truncated Tobit model

![image](d2d_images/chapter_title_below.png)

The likelihood function of the truncated regression model is calculated from the density function:

![image](d2d_images/image008.png)

Applying neperians we obtain that the logarithm of the likelihood function for a sample of size n is:

![image](d2d_images/image662.png)

Deriving and equalling zero we obtain the MV estimators ofβ andσ .

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.8.4  ​Estimation by Amemiya's two-step method

![image](d2d_images/chapter_title_below.png)

Although the estimation of the OLS truncated Tobit model cannot be done directly, we can use the following two-step method:

1.  We estimate by OLS the model ![image](d2d_images/image529.png)and we obtain ![image](d2d_images/image675.png)

1.  The auxiliary equation ![image](d2d_images/image277.png)is specified and estimated by the instrumental variables method using the regressors ![image](d2d_images/image180.png)as instruments.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.9  ​SAMPLE SELECTION CORRECTION: TWO-STAGE HECKMAN OR HECKIT ESTIMATION

![image](d2d_images/chapter_title_below.png)

Truncated regression is a special case of a general problem known as non-random sample selection that occurs when the sample available for estimation is not random.

Heckman devised a two-stage procedure for estimating models in the presence of incidental truncation that overcomes the problem of selection bias:

Stage 1. Using the n observations we estimate a Probit model of s over Z from which we obtain![image](d2d_images/image104.png). From these estimates we calculate for each i![image](d2d_images/image651.png).

Stage 2. Using the selected sample (s=1) we estimate by OLS the regression of Y on X and ![image](d2d_images/image246.png).

This procedure yields consistent and asymptotically normal estimators.

A test for the existence of sample selection bias consists of testing in the second stage the hypothesis ofρ = 0 using the t-statistic of![image](d2d_images/image619.png). Whenρ ≠ 0 the standard errors of the 2nd stage are not valid and must be corrected.

We have assumed that X is a subset of Z because if we inappropriately exclude any element of X we may have inconsistent estimators. It is important that Z contains at least one element that does not belong to X. This is not essential for the identification ofβ as the non-linearity of![image](d2d_images/image619.png)is sufficient for this purpose.

But if we have additional elements, the correlation of![image](d2d_images/image619.png)with X decreases and we will obtain more precise estimators of theβ . Moreover, if in the first stage we do not include additional items, the significance of![image](d2d_images/image619.png)in the second stage may be due to sample selection or misspecification.

In addition to using the 2-stage procedure, this type of models can be estimated by MV, although it is more complicated because we need the joint distribution of Y and s.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.10  ​BOUNDED DEPENDENT VARIABLE MODELS WITH STATA: LOGIT AND PROBIT

![image](d2d_images/chapter_title_below.png)

STATA has the logit command, which allows us to fit a binary logit model. As an example, we will start from the car file auto.dta and estimate a model that explains the probability of a car being foreign as a function of its weight and consumption. The model will then be:

![image](d2d_images/image250.png)F \= logistical distribution

and is estimated with STATA using the following syntax:

![image](d2d_images/image234.png)

![image](d2d_images/image616.png)

Odds ratios are obtained using the logistic procedure.

![image](d2d_images/image304.png)

STATA has the probit command, which allows us to fit a binary probit model. As an example we will start from the car file auto.dta and estimate a model that explains the probability of a car being foreign as a function of its weight and consumption. The model will then be:

![image](d2d_images/image279.png)normal distribution (0,1)

and is estimated with STATA using the following syntax:

![image](d2d_images/image346.png)

STATA provides the mlogit  command to fit multinomial logistic models. As an example, a model is fitted that explains the probability of having insurance with three alternative modes (insure) that are prepayment, indemnity and no insurance, as a function of the race of the insured (nonwhite) considering whites and non-whites as possible races. The syntax of STATA is as follows:

![image](d2d_images/image275.png)

According to this output, the probability of prepayment for whites (nonwhite=0) is modelled as follows:

![image](d2d_images/image412.png)

Similarly, for non-whites the probability of prepayment will be:

![image](d2d_images/image182.png)

STATA provides the mprobit command for fitting multinomial probit models. For the example above, the multinomial probit model is fitted using the following syntax:

![image](d2d_images/image580.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.11  ​CENSORED AND TRUNCATED TOBIT MODELS WITH STATA. HECKMAN METHOD AND MILLS RATIO.

![image](d2d_images/chapter_title_below.png)

STATA uses the tobit  command to fit models with censoring. As an example we fit a model that explains the consumption of cars as a function of their weight (divided by 1000) by censoring the data in the sense that consumptions less than or equal to 17 are replaced by the value 17 (left censoring). The adjustment would now be done using a tobit model as follows:

![image](d2d_images/image071.png)

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image021.png)

We then fit the above model but assuming that there are no mpg values higher than 24, i.e. in the presence of right censoring. The syntax for the corresponding tobit model could be as follows:

![image](d2d_images/image254.png)

If we now consider the left- and right-censored model, the corresponding tobit model would fit as follows:

![image](d2d_images/image521.png)

STATA fits models with selection bias using the heckman command. As an example, we fit a model that explains wage as a function of educational level and age in the presence of selection bias related to the variables marital status, children, educational level and age in the sense that wage is only observed if a linear combination of the latter variables is positive.

![image](d2d_images/image387.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 3.12  ​POISSON MODEL WITH STATA

![image](d2d_images/chapter_title_below.png)

STATA allows you to work with the Poisson count data model using the poisson command. An example is presented below.

![image](d2d_images/image648.png)

4Chapter 4

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# ​LOGIT, PROBIT, TOBIT, TRUNCATED, RECOUNTED, CENSORED and SAMPLE SELECTION models. PROCESSING WITH EVIEWS

![image](d2d_images/chapter_title_below.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 4.1  ​BOUNDED DEPENDENT VARIABLE MODELS WITH EVIEWS: MLP, LOGIT AND PROBIT

![image](d2d_images/chapter_title_below.png)

We will initially fit a linear probability model to data on 753 married women in 1975 (file married.wf1), of whom 428 participated in the labour market at some point during the year (inlf=1) and 325 did not participate (inlf=0).

The probability of participating in the labour market (inlf) is considered to depend on other sources of income (nwifeinc), years of education (educ), years of work experience (exper and exper² ), age, number of children under 6 (kidslt6) and number of children between 6 and 18 (kidsg6).

Using a linear probability model we will analyse the dependence of the probability of female labour market participation on the explanatory variables defined above.

We will consider the following linear probability model (LPM):

![image](d2d_images/image158.png)

We will start by estimating the MLP using OLS. To do so, choose Quick→ Estimate Equation, write the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose LS-Least Squares (NLS and ARMA) in the Method field to fit by ordinary least squares (Figure 4-1) and click OK. The results in Figure 4-2 are obtained with good individual and joint significances for the estimated parameters (except maybe kidsge6). The R² and the Durbin Watson statistic are not very good, but we have to think that we are estimating a linear probability model.

![image](d2d_images/image068.png)![image](d2d_images/image207.png)

Figure 4-1      Figure 4-2

But the relevant problem in a MLP is heteroscedasticity. View→ Residual Tests→ White Heteroskedasticity (Figure 4-3) yields p-values of F and Chi less than 0.05 (Figure 4-4), so there is heteroscedasticity. We will then use a method that is robust to heteroscedasticity, for example White's method, for estimation. The estimation using White's method is now done by filling in the Options tab of the Equation Estimation screen as shown in Figure 4-5. Clicking OK produces the non-heteroscedastic estimate in Figure 4-6.

![image](d2d_images/image334.png)![image](d2d_images/image550.png)

Figure 4-3      Figure 4-4

![image](d2d_images/image638.png)![image](d2d_images/image598.png)

Figure 4-5      Figure 4-6

Except for kidsge6 all variables are statistically significant and have the expected signs. There is also a strong joint significance. Interpreting the coefficients shows that if education increases by one year (and all other variables remain constant), women's probability of participating in the labour market increases by 0.038. The effect of other sources of income (nwifeinc) is significant, but very small, since if other income increases by one unit, women's probability of participating in the labour market decreases by 0.0034 (with all other factors held constant).

By varying experience by one year, with all other factors fixed, the estimated variation in women's probability of labour market participation is given by 0.039-2(0.0006)exper. The point at which experience does not affect the probability of participation (and from which the slope changes sign) is 0.039/0.0012=32.5 (there are only 13 women with exper>32). As age increases by one year (all other things being equal), women's probability of participating in the labour market decreases by 0.016. Having one more child under the age of 6 reduces women's probability of participating in the labour market by 0.262, for given levels of the other variables. Having a child between 6 and 18 increases the probability of female labour market participation by 0.013, for fixed levels of the other variables.

One of the major problems with MLP is that for certain combinations of values of the explanatory variables, the estimated probabilities may be less than 0 or greater than 1:

![image](d2d_images/image102.png)

To do so, click on Forecast and fill in the forecast screen as shown in Figure 4-7 (the variable inlff contains the values of![image](d2d_images/image125.png)for the 753 women in the sample). When we click OK we obtain Figure 4-8 representing![image](d2d_images/image125.png), noting that there are values greater than unity and less than 0). In fact, if we double-click on the variable inlff in the Workfile screen, we see its values. Figure 4-9 shows some values greater than unity, Figure 4-10 shows values less than zero. In total there are 17 values of![image](d2d_images/image125.png)greater than one and 16 less than zero.

Another inconsistency of the MLP is that the effect on the likelihood is the same for all values of the explanatory variables.

![image](d2d_images/image442.png)![image](d2d_images/image263.png)

Figure 4-7      Figure 4-8

![image](d2d_images/image450.png)![image](d2d_images/image378.png)

Figure 4-9      Figure 4-10

In the following, given the possible shortcomings of the linear probability model, we solve the above problem using a Probit model and a Logit model. In addition, the effects of the explanatory variables on women's probability of participating in the labour market are quantified and interpreted in the appropriate way.

We will first consider the Probit model:

![image](d2d_images/image001.png)

where Ф is the distribution function of a normal (0,1).

We will start by estimating using the probit model. To do this, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose BINARY-Binary choice (logit, probit, extreme value) in the Method field, choose Probit in the Binary estimation method field to fit the Probit model (Figure 4-11) and click OK. 

The results in Figure 4-12 are obtained with good individual significances for the estimated parameters (except for the constant and kidsge6). The joint significance is very high because the p-value of the likelihood ratio statistic is very small. McFadden's Pseudo R² is not very close to unity (0.22). The values of the information criteria (Akaike, Schwarz and Hannan-Quinn) are adequate because they are low and very close.

![image](d2d_images/image624.png)![image](d2d_images/image223.png)

Figure 4-11      Figure 4-12

Another criterion to measure the goodness of fit of the Probit  model is the criterion of the percentage of correct predictions which consists of observing the percentage of times the observed Y valuei matches its prediction. This task is carried out with Eviews through View → Expectation-Prediction Table (Figure 4-13).

Clicking OK produces the output in Figure 4-14, which shows that the model adequately predicts 73.44% of the observations. The ones (female labour market participation) are better predicted with 81.31% correct compared to 63.08% for non-participation.

![image](d2d_images/image640.png)![image](d2d_images/image706.png)

Figure 4-13      Figure 4-14

To quantify and interpret the effects of the explanatory variables on women's probability of participating in the labour market, we will bear in mind that the partial effect of a continuous explanatory variable Xj on the response probability P(Y \= 1|X) is:

![image](d2d_images/image018.png)

Since we have one effect for each observation, we will avoid calculating 753 effects by calculating the effects for the mean observations. To do so, we calculate the means of the variables in the model by selecting them in the Workfile screen and opening them as a group with the right mouse button using Open → as Group (Figure 4-15). Then choose View → Descriptive Statistics→ Individual samples (Figure 4-16) and obtain the descriptive statistics for all variables in the model, including the mean (Figure 4-17).

![image](d2d_images/image395.png)![image](d2d_images/image700.png)

Figure 4-15      Figure 4-16

![image](d2d_images/image359.png)

Figure 4-17

––––––––

![image](d2d_images/scene_break.png)

We have:

![image](d2d_images/image503.png)

with what:

![image](d2d_images/image240.png)

ϕ = Density function of the normal (0,1)

We can obtain the estimated partial effect of the continuous variables, for the mean values of X, by multiplying the estimated coefficients of the Probit model by 0.391.

Therefore, an additional year of education increases the probability of participating in the labour market by 0.131x0.391 = 0.05. Increasing age by one year decreases the probability of participation by 0.02 (-0.053x0.391=-0.021). As experience increases by one year, the probability of participating varies by \[0.124-(2x0.0019xexper\]x0.391. A unit increase in other income causes the probability of participating to decrease by 0.005 (-0.012x0.391 = -0.05).

We can also calculate the estimated effect of varying a discrete variable. For example, for kidslt6 the effect on the probability of working of going from having 0 to 1 child (under 6) is a reduction by 0.336 because Ф = Normal distribution function (0.1):

![image](d2d_images/image116.png)

and the effect on women's probability of working of moving from 1 to 2 children (under 6 years) will be reduced by 0.231because:

![image](d2d_images/image687.png)

Now we will perform the estimation using the Logit model. To do so, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose BINARY-Binary choice (logit, probit, extreme value) in the Method field, choose Logit in the Binary estimation method field to fit the Probit model (Figure 4-18) and click OK. 

The results in Figure 4-19 are obtained with good individual significances for the estimated parameters (except for the constant and kidsge6) as in the case of the Probit model. The joint significance is very high because the p-value of the likelihood ratio statistic is very small. McFadden's Pseudo R² is not very close to unity (0.219). The values of the information criteria (Akaike, Schwarz and Hannan-Quinn) are adequate.

![image](d2d_images/image435.png)![image](d2d_images/image314.png)

Figure 4-18      Figure 4-19

For the logistics function:

![image](d2d_images/image623.png)

(λ is the logistic density function and Λ is the logistic distribution function)

and calculating the average partial effects of the variables by multiplying the estimated coefficients by 0.227 gives the same results as for the Probit model.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 4.2  ​COUNTING MODELS WITH EVIEWS: POISSON, NEGATIVE BINOMIAL AND EXPONENTIAL MODELS

![image](d2d_images/chapter_title_below.png)

As an example we consider the file arrests.wf1 which contains information on the variable narr86 which represents the number of times a man is arrested during 1986 and which we wish to explain by the variables pcnv (proportion of previous arrests in which he was convicted), avgsen (average length of sentences in months), tottime (time in prison in months), ptime86 (time in prison in 1986 in months), qemp86 (quarters employed in 1986 in hundreds of dollars), black (fic86) (legal income in 1986 in hundreds of dollars), black (fic86) (fic86) (fic86) (fic86), ptime86 (time in prison in 1986 in months), qemp86 (quarters employed in 1986), inc86 (legal income in 1986 in hundreds of dollars), black (dummy worth 1 for black arrestee), hispan (dummy worth 1 for hispanic arrestee) and born60 (dummy worth 1 if the arrestee was born in 1960). As the explained variable takes the value 0 in a large number of cases and only takes a value greater than 5 in 8 cases, a count data model could be used. We will study the effect of the explanatory variables on the explained variable using Poissson, exponential and negative binomial count data models.

We first estimate the model using a Poisson count model. To do so, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose COUNT-Integer count data in the Method field, mark Poisson (ML and QML) in the Count estimation method field to fit by a Poisson count data model (Figure 4-20) and click OK. The results in Figure 4-21 are obtained with good individual and joint significances for the estimated parameters (except for avgsen, tottime, ptime86 and born60). The Pseudo R² is quite small and the values of the information criteria are quite acceptable. Similar fitting parameters to the previous case are observed. Using View → Representations (Figure 4-22) the fitted model equations are obtained (Figure 4-23).

![image](d2d_images/image164.png)![image](d2d_images/image025.png)

Figure 4-20      Figure 4-21

![image](d2d_images/image056.png)![image](d2d_images/image004.png)

Figure 4-22    Figure 4-23

As the adjustment is now ![image](d2d_images/image113.png)when interpreting the results we see that if the individual is employed in 1986 for one more quarter (all other factors fixed), the expected number of arrests in that year is reduced by 3.8% (not significant). All else being equal, the expected number of arrests of a black male is 66% higher than that of a white and that of a Hispanic is 50% higher than that of a white. The other parameters would be interpreted similarly.

If in the Equation Estimation  screen we click on the Options tab and choose Robust Covariances-GLM (Figure 4-24), when we click OK we obtain the estimation of the Poisson count model with GLM standard errors computed under V(Y|X)=σ² E(Y|X) as shown in Figure 4-25. It can be seen that the results do not differ too much from the previous case and the parameter estimates are very similar. Note that the variance estimate is:

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image555.png)

Asσ² >1 we have a case of overdispersion with respect to the Poisson variance. Using View → Representations (Figure 4-26) we obtain the fitted model (Figure 4-27).

![image](d2d_images/image134.png)![image](d2d_images/image337.png)

Figure 4-24      Figure 4-25

![image](d2d_images/image323.png)![image](d2d_images/image439.png)

Figure 4-26      Figure 4-27

We now estimate the model using a negative binomial count model (with quasi maximum likelihood). To do so, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose COUNT-Integer count data in the Method field, select Negative Binomial (QML) in the Count estimation method field to fit a negative binomial count data model with quadratic maximum likelihood (Figure 4-28) and click OK. 

The results in Figure 4-29 are obtained with good individual and joint significances for the estimated parameters (except for avgsen, tottime and born60). The Pseudo R² is quite small and the values of the information criteria are quite acceptable. Moreover, very similar results to the previous methods are observed. By means of View → Representations (Figure 4-30) the equations of the fitted model are obtained (Figure 4-31).

![image](d2d_images/image712.png)![image](d2d_images/image358.png)

Figure 4-28      Figure 4-29

![image](d2d_images/image269.png)![image](d2d_images/image372.png)

Figure 4-30      Figure 4-31

Finally, we now estimate the model using an exponential count model (with quasi-maximum likelihood). To do this, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose COUNT-Integer count data in the Method field, select Exponential (QML) in the Count estimation method field to fit an exponential count data model with quadratic maximum likelihood (Figure 4-32) and click OK. The results in Figure 4-33 are obtained. View → Representations (Figure 4-34) gives the equations of the fitted model (Figure 4-35).

![image](d2d_images/image055.png)![image](d2d_images/image028.png)

Figure 4-32      Figure 4-33

Good individual and joint significance is observed for the estimated parameters (except for avgsen, tottime and born60). The Pseudo R² is large and the values of the information criteria are quite acceptable. Furthermore, very similar results to the previous methods are observed. The most suitable count data model for this fit is the exponential model, as it has the lowest values for the Akaike, Schwarz and Hannan-Quinn information criteria.

![image](d2d_images/image095.png)![image](d2d_images/image331.png)

Figure 4-34      Figure 4-35

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 4.3  ​CENSORED AND TRUNCATED TOBIT MODELS WITH EVIEWS. HECKMAN'S METHOD AND MILLS' RATIO

![image](d2d_images/chapter_title_below.png)

We considered data from a company report on 753 households (file families.wf1) in which a model was estimated relating expenditure on car purchase![image](d2d_images/image647.png)to household income in the last year ![image](d2d_images/image203.png), the number of children under 18 ![image](d2d_images/image019.png)and the age of the head of household ![image](d2d_images/image707.png). The following behavioural equation was specified:

![image](d2d_images/image266.png)

This involves estimating the above model bearing in mind that there may be individuals surveyed who have not purchased a vehicle in that period, in which case they have been assigned a zero expenditure. The task is to find the marginal effects of the explanatory variables on the explained variable and compare them with the OLS estimates of the model coefficients and calculate the income elasticity of demand at the midpoint.

This is the particular case of data censoring that occurs when the dependent variable is zero for a part of the population and is continuous for the positive values. We are then faced with a limited variable model with a corner solution. Specifically, we are dealing with a censored Tobit model with corner solution.

We start by estimating using the maximum likelihood censored Tobit model. To do this, choose Quick→ Estimate Equation, write the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose CENSORED-Censored or truncated data (Tobit) in the Method field, set it to zero in the Left field and mark Actual censoring value because the Tobit model with corner solution is censored on the left by the value zero, choose Normal because we consider the model with normal distribution (Figure 4-36) and click OK. The results in Figure 4-37 are obtained with good individual significances for the estimated parameters. The R² is far away from unity, but this is usual for this type of models. It can be seen that out of a total of 753 observations there are 336 null values (uncensored observations, i.e. respondents who had not bought a car in that year) and 417 left-censored observations (because they are positive values with the censored value to their left). The values of the information criteria are not too high and are fairly consistent with each other.

![image](d2d_images/image488.png)![image](d2d_images/image151.png)

Figure 4-36     Figure 4-37

The marginal effect in the censored Tobit model of each of the variables is obtained by the expression (applied to the mean values):

![image](d2d_images/image144.png)

From the vector of the means of all the explanatory variables![image](d2d_images/image635.png)and the vector of the estimated parameters![image](d2d_images/image374.png), we have that:

![image](d2d_images/image210.png)

The marginal effects for the mid-point can then be calculated as follows:

![Diagrama Descripción generada automáticamente](d2d_images/image441.png)

Therefore, the income elasticity of demand will be estimated from our Tobit model as follows:

![Texto Descripción generada automáticamente](d2d_images/image366.png)

In order to compare the marginal effects for the midpoint with the estimated coefficients of the linear model using OLS, we will perform the latter estimation. To do so, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose LS-Two stage Least Squares (NLS and ARMA) in the Method field to fit by least squares (Figure 4-38) and click OK. The results are shown in Figure 4-39.

![image](d2d_images/image251.png)![image](d2d_images/image137.png)

Figure 4-38    Figure 4-39

It is observed that the marginal effects of the Tobit model are close to but do not coincide with the estimated values of the OLS model, being always a little bit lower. The difference between these OLS estimates and the Tobit marginal effects would be the errors that would be made in the model parameter estimates if OLS were used instead of a Tobit model.

It is now a matter of estimating a wage equation by specifying an econometric model in which the logarithm of wages received by employees Y is related to work experience (X2 ), its square (X3 ), the educational level (X4 ), the worker's marital status (X5 ) and the worker's university degree or not (X6 ) through the following behavioural equation:

![image](d2d_images/image427.png)

We will estimate this wage behaviour equation using a truncated Tobit model and calculate the marginal effects of the variables X2 , X3 and X4 on the wage. The data are collected in the file wages.wf1.

Since we only observe wage supply for individuals who are working (and not for those who are not working) we are dealing with a case of non-random sample selection in which we observe Y or not depending on another variable (employment). We are clearly facing a case of truncation in which the wage supply is observed depending on another variable which is the labour supply.

As we are in a truncated Tobit model we will use the smallest value of the dependent variable Y as the truncation value. This minimum value is the one that lies furthest to the left of the remaining Y values. To calculate the minimum value of Y we double-click on Y in the Workfile screen and choose View → Descriptive Statistics → Stats Table (Figure 4-40). In Figure 4-41 we see that the minimum value of Y is 1.8718.

![image](d2d_images/image568.png)![image](d2d_images/image135.png)

Figure 4-40    Figure 4-41

We now estimate the wage behaviour equation using the Tobit model truncated by maximum likelihood. To do this, choose Quick→ Estimate Equation, write the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose CENSORED-Censored or truncated data (Tobit) in the Method field, put 1.8718 in the Left field and mark Actual censoring value because the truncated Tobit model is censored to the left by this value, choose Normal because we consider the model with normal distribution, mark Truncated sample (Figure 4-42) and click on OK. The results in Figure 4-43 are obtained with good individual significances for the estimated parameters (except perhaps X3 and X5 at 80% and X6 at 50%). The R² is far away from unity, but this is usual in this type of models. The values of the information criteria are not too high and are fairly consistent with each other.

![image](d2d_images/image420.png)![image](d2d_images/image080.png)

Figure 4-42      Figure 4-43

The marginal effect in the truncated Tobit model of each of the variables is obtained by the expression (applied to the mean values):

![image](d2d_images/image281.png)

Then the marginal effect of variable Xk with respect to the explained variable is equal to the estimated coefficientβk multiplied by the correction factor![image](d2d_images/image670.png)being:

![Imagen de la pantalla de un celular con letras Descripción generada automáticamente con confianza media](d2d_images/image507.png)We have:

![Diagrama Descripción generada automáticamente](d2d_images/image606.png)

The marginal effects for the variables ![image](d2d_images/image573.png)on the wage will be calculated as follows:

![Texto Descripción generada automáticamente](d2d_images/image115.png)

Next we consider the file married.wf1 which contains data on 753 married women in 1975, of whom 428 participated in the labour market at some time during the year (inlf=1) and 325 did not participate (inlf=0). Labour market participation (inlf) is found to depend on other sources of income (nwifeinc), years of education (educ), years of work experience (exper and exper² ), age, number of children under 6 (kidslt6) and number of children between 6 and 18 (kidsg6).

Based on the above information, using a truncated Tobit model we will estimate the wage equation that makes the logarithm of women's wage depend on their educational level, work experience and the square of the latter variable using Heckman's two-stage method.

As in the previous case, this is a Tobit model with incidental truncation because labour market participation depends on labour supply.

In a first stage we estimate a Probit model of Inlf versus constant and all explanatory variables.  The model is:

![image](d2d_images/image491.png)

To do so, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose BINARY-Binary chice (logit, probit, extreme value) in the Method field, choose Probit in the Binary estimation method field to perform the fit using the Probit model (Figure 4-44) and click OK. The results in Figure 4-45 are obtained with good individual significances for the estimated parameters (except for the constant and kidsge6). The joint significance is very high because the p-value of the likelihood ratio statistic is very small. The McFadden's Pseudo R² is not very close to unity (0.22). The values of the information criteria (Akaike, Schwarz and Hannan-Quinn) are adequate because they are low and very close.

![image](d2d_images/image701.png)![image](d2d_images/image694.png)

Figure 4-44    Figure 4-45

Next we calculate the inverse of the Mills ratio through the generalised residuals of the newly fitted Probit model. To do this, in the Probit window choose Procs → Make residual series and select Generalized (Figure 4-46). The new variable resid01 \=![image](d2d_images/image619.png)equivalent to the Mills ratio is obtained (Figure 4-47).

![image](d2d_images/image512.png)![image](d2d_images/image347.png)

Figure 4-46    Figure 4-47

In a second stage, we estimate by OLS the wage equation including as an additional regressor the generalised Probit residual. The model to be estimated will be:

![image](d2d_images/image166.png)

To do this, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose LS-Two stage Least Squares (NLS and ARMA) in the Method field to fit by least squares (Figure 4-48) and click OK. The results are shown in Figure 4-49.

![image](d2d_images/image668.png)![image](d2d_images/image015.png)

Figure 4-48    Figure 4-49

We observe a very good significance of the estimated coefficients, both individually and jointly, good values of the information criteria and a Durbin Watson statistic very close to 2, indicating that there will be no problems of serial autocorrelation.

Exercise 4-1. In a study on the real estate market we have information on the income level of the families (INCOME), on the number of children in the family (CHILDREN), on a dichotomous variable (SUB) that takes the value 1 if the house is subsidised and 0 otherwise, and on the discrete variable HOUSE referring to the square metres of the houses that are available to buyers whose value depends on the surface area in the following way:

![Interfaz de usuario gráfica, Texto Descripción generada automáticamente](d2d_images/image184.png)

The aim is to analyse what type of housing families buy according to their characteristics (income and children) and those of the housing (subsidised or not) using a multiple response model ![image](d2d_images/image306.png) and assuming that the distribution function F can be a normal (0,1) or a logistic one Which method is better? 

As the dependent variable has values that can be ordered from smallest to largest according to their surface area, an ordered multiple response model of the type ![image](d2d_images/image605.png) can be specified with: 

![Imagen que contiene Esquemático Descripción generada automáticamente](d2d_images/image099.png)

The different models to be used are presented by considering the distribution function F as a normal (Multidimensional Probit model) or a logistic (Multidimensional Logit model).

To estimate the ordered Multinomial Probit model, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose ORDERED-Ordered choice in the Method field, choose Normal in the Error ditribution field to fit the Multinomial Probit model (Figure 4-50) and click OK. The results in Figure 4-51 are obtained with good individual significances for the estimated parameters (except perhaps SUB with a significance of about 85%). The joint significance is very high because the p-value of the likelihood ratio statistic is very small. The Pseudo R² is quite close to 60%. The values of the information criteria (Akaike, Schwarz and Hannan-Quinn) are adequate.

![image](d2d_images/image666.png)![image](d2d_images/image138.png)

Figure 4-50      Figure 4-51

To estimate the ordered Multinomial Logit model, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose ORDERED-Ordered choice in the Method field, choose Logistic in the Error distribution field to fit the Multinomial Logit model (Figure 4-52) and click OK. The results in Figure 4-53 are obtained with good individual significances for the estimated parameters (except perhaps SUB with a significance of about 85%). The joint significance is very high because the p-value of the likelihood ratio statistic is very small. The Pseudo R² is quite close to 60%. The values of the information criteria (Akaike, Schwarz and Hannan-Quinn) are adequate. It is observed that the results of the goodness-of-fit statistics are very similar to the case of the Probit model.

![image](d2d_images/image312.png)![image](d2d_images/image165.png)

Figure 4-52      Figure 4-53

The most efficient estimation method will be the one with the lowest values of the Akaike, Schwarz and Hannan-Quinn information criteria and the highest value of the likelihood function. Compiling we have:

![image](d2d_images/image107.png)

The method with the lowest values of the information criteria and the highest value of the likelihood function is the Probit   model. Therefore, the best fit is provided by the ordered Multinomial Probit model.

Exercise 4-2. In a study on the provision of televisions in Spanish households, 940 families have been surveyed asking about the number of televisions in the household (TV), the annual income in millions of monetary units (FI) and the level of education of the head of the household (NI). The variable TV can take the values 1, 2 or 3 depending on whether households have 1, 2 and 3 or more TV sets available. The level of education of the household head has been coded through four levels (Básica, Bachillerato superior, Universitaria media and Universitaria superior) with the respective integer values from 1 to 4. With the specified data contained in file 7-8.wf1, we are asked to fit a logit model that explains the probability of a household having a given number of TV sets as a function of the rest of the variables defined above.

For a family whose head of household has a basic level of education (NI=1) and an annual income of three million monetary units (IF=3), find the probability that he/she has only one television set. Calculate also the probability that this family has 2 televisions. Also, calculate the probability that this family has three or more televisions.

Calculate the marginal effect of having two televisions for a family with an annual income of four million monetary units and where the level of education of the head of household is basic compared to the case where the level of education of the head of household is high school. The data can be found in file 4-2.wf1.

As the response variable has more than two categories that can be ordered, this is the ordered multinomial logit model:

![image](d2d_images/image148.png)

To estimate the ordered Multinomial Logit model, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose ORDERED-Ordered choice in the Method field, choose Logistic in the Error ditribution field to fit the Multinomial Logit model (Figure 4-54) and click OK. The results in Figure 4-55 are obtained with good individual significances for the estimated parameters. The joint significance is very high because the p-value of the likelihood ratio statistic is very small. The Pseudo R² is quite close to unity (0.88). The values of the information criteria (Akaike, Schwarz and Hannan-Quinn) are adequate.

For a household whose head of household has a basic level of education (NI=1) and an annual income of three million monetary units (IF=3), the probability that he/she has only one TV set is given by

![image](d2d_images/image418.png)

For the above family, the probability that they will have two televisions will be:

![Texto, Carta Descripción generada automáticamente](d2d_images/image460.png)

For the above family, the probability of having three or more TV sets will be:

![image](d2d_images/image595.png)

![image](d2d_images/image593.png)![image](d2d_images/image472.png)

Figure 4-54      Figure 4-55

To calculate the marginal effect of having two televisions for a family with an annual income of four million monetary units and where the level of education of the head of the household is basic compared to the case where this level is high school, the probability must be calculated for each of the situations and the difference between them must be obtained. We have:

![Texto, Carta Descripción generada automáticamente](d2d_images/image684.png)

![Texto, Carta Descripción generada automáticamente](d2d_images/image309.png)

The marginal effect ordered is obtained as the difference between the two probabilities above:

![image](d2d_images/image074.png)

Exercise 4-3. File 4-3.wf1 contains data for 1445 prisoners on the number of months before an inmate is rearrested after release (durat).  It is considered that log(durat) depends on whether or not the prisoner has participated in prison employment programmes (workprg), the number of previous convictions (priors), the number of months spent in prison (tserved), whether or not the prisoner uses alcohol (alcohol), whether or not the prisoner uses drugs (drugs), whether or not the crime committed is serious (felon), whether or not the prisoner is black (black), whether or not the prisoner is married (married), the prisoner's educational level (educ) and the prisoner's age (age).  It is also known that of the 1445 prisoners there are 893 who were not arrested while being followed. We also have a dummy variable indicating whether each observation is censored or not (cens).

Based on the above information, using a Tobit model, estimate and interpret the relationship between the log(durat) variable and the rest of the explanatory variables, interpreting the result.

Since there are prisoners who were not arrested after their last release, we are dealing with a Tobit model that is censored by the right, the censorship being defined by the censorship variable that plays the role of censorship indicator.

We will estimate the right-censored Tobit model by maximum likelihood. To do this, choose Quick→ Estimate Equation, write the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose CENSORED-Censored or truncated data (Tobit) in the Method field, place the censoring variable in the Right field and mark Zero/One indicator of censoring because the Tobit model is censored on the right and the censoring indicator is the censoring variable, choose Normal because we consider the model with normal distribution (Figure 4-56) and click on Accept. The results in Figure 4-57 are obtained with good individual significances for the estimated parameters (except for workprg and educ). The values of the information criteria are not too high and are quite consistent with each other.

![image](d2d_images/image109.png)![image](d2d_images/image011.png)

Figure 4-56    Figure 4-57

The variables priors and tserved are found to have a negative effect. A prisoner with one more sentence will reduce the time to re-arrest by 14%. An extra month in prison reduces the time to re-arrest by 1.9%. An individual who uses drugs (drugs \= 1) takes approximately 29.8% less time to re-arrest![image](d2d_images/image348.png).

An individual who is black takes approximately 54.3% less time to be re-arrested than a white individual![image](d2d_images/image434.png).

It is observed that if we estimate the model by OLS without taking into account that 893 of the 1445 observations are censored, we obtain different results. To do so, choose Quick→ Estimate Equation, type the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose LS-Two stage Least Squares (NLS and ARMA) in the Method field to fit by least squares (Figure 4-58) and click OK. 

The results in Figure 4-59 are obtained with good individual significance for the estimated parameters (except workprg and educ) and joint significance. The values of the information criteria are not too high and are quite consistent with each other. The Durbin Watson statistic is very close to 2, indicating that there will be no problems of serial autocorrelation. The fit does not coincide with that of the censored Tobit model. Although the parameter estimates do not differ too much, one of them changes sign (workprg), which is precisely one of the individually non-significant variables.

![image](d2d_images/image396.png)![image](d2d_images/image429.png)

Figure 4-58    Figure 4-59

––––––––

![image](d2d_images/scene_break.png)

Exercise 4-4. This is to study the effects of two headache painkillers. The patients are divided into two groups so that each group receives a different type of painkiller (TYPE) and for each patient the time taken for the headache to subside after the painkiller has been given (MINUT) is recorded. As there may be patients who still have a headache at the end of the observation period, this is a case of right-censored data. The censored variable (CENS) will be 1 for censored data and zero for uncensored data. The data are collected in file 4-4.wf1.

Fit an appropriate model to explain the time to remission of headache pain as a function of patient group, which will allow comparison of the two painkillers. Fit the models assuming normal, logistic and extreme value distributions. Compare the three models.

As there may be patients who at the end of the observation period still have a headache, this is a case of a right-censored Tobit model, the censoring being defined by the variable CENS which plays the role of a censoring indicator.

We will estimate the right-censored Tobit model by maximum likelihood. To do this, choose Quick→ Estimate Equation, write the equation of the model to be fitted in the Equation Specification field of the Specification tab, choose CENSORED-Censored or truncated data (Tobit) in the Method field, place the censoring variable in the Right field and mark Zero/One indicator of censoring because the Tobit model is censored on the right, the censoring indicator being the CENS variable, choose Normal because we consider the model with normal distribution (Figure 4-60) and click on Accept. The results in Figure 4-61 are obtained with good individual significances for the estimated parameters. The values of the information criteria are acceptable and coincide with each other.

![image](d2d_images/image069.png)![image](d2d_images/image471.png)

Figure 4-60    Figure 4-61

It is observed that for a patient in group 1 (TYPE \= 1), the headache remission time is 17.317 + 3.666\*1 = 20.983 minutes, while for a patient in group 2 (TYPE = 2) it is 17.317 + 3.666\*2 = 24.649 minutes. It is observed that the painkiller given to group 1 is more effective because the pain subsides in less time than with the painkiller given to group 2.

To fit the right-censored Tobit model assuming logistic distribution, we point to Logistic in the Distribution field of the Equation Estimation screen (Figure 4-62). Clicking OK produces the results in Figure 4-63 with good individual significances for the estimated parameters. The values of the information criteria are acceptable and coincide with each other. It is also observed that the differences with the Normal distribution model are very small.

![image](d2d_images/image557.png)![image](d2d_images/image150.png)

Figure 4-62    Figure 4-63

To fit the right-censored Tobit model assuming logistic distribution, we point to Extreme value in the Distribution field of the Equation Estimation screen (Figure 4-64). Clicking OK produces the results in Figure 4-65 with good individual significances for the estimated parameters. The values of the information criteria are acceptable and coincide with each other. It is also observed that the differences with the Normal and Logit distribution models are small.

![image](d2d_images/image497.png)![image](d2d_images/image307.png)

Figure 4-64    Figure 4-65

After estimating the Tobit models for the three distributions, we will compare them in order to choose the most appropriate one. The most efficient model will be the one with the lowest values of the Schwarz and Hannan-Quinn   information criteria and the highest value of the likelihood function. Compiling we have:

![image](d2d_images/image365.png)

The method with the lowest values of the information criteria and the highest value of the likelihood function is the logistic distribution model with very little difference to the normally distributed model. The model with Weibull distribution (extreme value) is the least suitable in this case. Therefore, the best fit is provided by the right-censored Tobit model with logistic distribution.

5Chapter 5

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# GENERALISED LINEAR MODELS WITH PANEL DATA. NON-LINEAR PANEL MODELS

![image](d2d_images/chapter_title_below.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.1  INTRODUCTION TO PANEL DATA: DATA STRUCTURES

![image](d2d_images/chapter_title_below.png)

Panel data is a special type of sample in which the behaviour of a number of economic agents is followed over time. In this way, the researcher can perform economic analysis and specify models with the cross-sectional (or cross-sectional) data that are obtained when all economic agents are considered at an instant in time. In this way, different patterns of behaviour of all the agents studied together at different points in time can be evaluated. Alternatively, the same analyses can be performed considering the time series given by the evolution of each economic agent over all time periods of the sample. In the latter case, different patterns of individual-by-individual behaviour could be examined over the entire time interval of the sample.

Therefore, an essential characteristic of the panel data structure is its two-dimensionality. One dimension is the list of individuals and another dimension is the time instants. Consider as an example the case of the personal income tax panel (IRPF panel) produced by the Spanish Institute of Fiscal Studies, which aims to have a database with the income tax returns of the same individuals from year to year. The different individuals are the personal income taxpayers in the common tax territory (excluding the autonomous communities of the Basque Country and Navarre) and the time interval varies at the present time from 1999 to 2008.

In the following paragraphs we delve a little deeper into the data structures embedded in the two dimensions of a panel data set. On the one hand cross-sectional or cross-sectional data and on the other hand time series data.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.1.1  Cross-sectional data 

![image](d2d_images/chapter_title_below.png)

Among the most important data structures, typical in applied economics work, we have cross-sectional data or cross-sectional data. A cross-sectional data set is a sample composed of individuals, families, firms, cities, states, countries or other types of widely varying units collected at a given point in time. In general, we can assume that cross-sectional data have been obtained by random sampling from the underlying population. For example, if we obtain information on wages, education, experience and other characteristics by randomly choosing 500 persons from the employed population, we can say that we have a random sample of the entire employed population.

In the case of the personal income tax panel we consider all the variables included in the tax return model and they will be analysed for a given year. Considering the different years we will have all the cross-sections year by year.

Cross-sectional data are very frequently used in economics and other social sciences. In economics, cross-sectional data analysis is closely related to different branches of applied microeconomics, such as tax analysis, labour economics, state and local public finance, industrial organisation, urban economics, demography and health economics. Data on individuals, households, firms and cities at a given point in time are important for testing microeconomic hypotheses and evaluating economic policies and fiscal policies.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.1.2  Time series data

![image](d2d_images/chapter_title_below.png)

A time series data set consists of observations on a variable or variables over time. Typical examples of time series data are gross domestic product, money supply, consumer price indices, annual homicide rates or car sales figures. Since past events can have an influence on future events, and lagged effects on the behaviour of individuals are common in social science, time is an important parameter in time series sets. As opposed to the order of cross-sectional data, the chronological arrangement of observations in a time series does convey potentially important information.

Time series data tend to be used more in macroeconomic analysis, as opposed to cross-sectional data, which are mostly used in macroeconomic analysis. Time series are often more difficult to analyse than cross-sectional data because we can almost never assume that economic observations are temporally independent.

Most time series, whether economic or not, are related (often strongly related) to their recent history. For example, our knowledge of last quarter's gross national product tells us quite a lot about the level of GDP we can expect for the current quarter since GDP tends to remain stable from one quarter to the next. Another important characteristic of time series data is the periodicity with which they are collected (weekly, monthly, quarterly, etc.) with the additional fact that many weekly, monthly or quarterly time series show a marked seasonal characteristic which can be an important factor in the methodology of time series analysis.

For the case of the personal income tax samples we can consider the time series measuring the evolution of each tax variable over the period 1999-2008.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.1.3  Data structures. Combinations of cross-sections

![image](d2d_images/chapter_title_below.png)

A combination of cross\-sectional or pooled data is a data structure that has characteristics of both cross-sectional and time-series data. A data pool is an amalgamation of several cross-sections of data collected at different points in time in the same population (but not for the same individuals). For example, suppose two cross-sectional household surveys are conducted in a country, one in 1985 and one in 1990. In 1985, a survey is conducted with a random sample to obtain variables such as the level of income, savings, household size, etc. In 1990, a new random sample of households is taken and the same questions as in 1985 are used to conduct the survey. In order to increase the sample size, we can form a merged cross-sectional data set by combining the data from two years. Merging cross-sectional data from different years is often useful for analysing the effects of new government policies. The idea is to collect data from the years before and after a key policy change.

Generally, merged cross-sectional data are analysed in much the same way as conventional cross-sectional data, except that we often need to account for differences in variables over time. In fact, in addition to increasing the sample size, the goal of merging cross-sectional data is often also to look at how a key relationship has changed over time. However, by combining cross-sections obtained by random sampling from the same population at different points in time, we will have a sample of independently but not identically distributed observations.

In the case of personal income tax, a data pool could be formed by pooling all annually selected samples. Obviously the personal income tax samples randomly selected each year will not correspond to the same individuals.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.1.4  Data structures. Panel or longitudinal data

![image](d2d_images/chapter_title_below.png)

A panel data set, or longitudinal data, consists of a time series for each unit of a cross-section (or cross-sectional data set). A panel data is an amalgamation of several cross-sections of data collected at different points in time (or in different geographical units or for different enterprises, etc.) in the same population for the same individuals.

As an example, suppose we have a record of data on the salary, education, and employment history of a set of individuals followed over a ten-year period.  We could also collect information on the financial or investment data of the same set of firms over a five-year period (so the individuals need not be persons). Panel data can also be collected on geographical units. For example, we can collect data on immigration flows, level of taxation, wages, government expenditures, etc., in the same set of EU countries for the years 1990, 1995 and 2000. The key feature of panel data, which differentiates it from merged cross-section data, is the fact that information is collected from the same cross-section units (individuals, firms, countries, etc.) at different points in time.

Because panel data collection requires repeating the same survey units over time, panel data are more difficult to obtain than merged cross-sectional data, especially when dealing with data on individuals, households or firms. However, an advantage of panel data is that they often allow us to study the importance of lags in behaviour or lags in decision-making (dynamic panels). This information can be very significant given that many economic measures can be expected to have no impact until some time after their implementation. In the case of personal income tax, a panel is formed by following the returns of the same individuals over time. However, this concept, known as a pure panel, can be completed by means of expanded panel techniques, which have been used to form the personal income tax panel of the IEF and to which we will refer in depth later on.

But we should not forget that the essential characteristic of a panel is its temporal dimension, since it is made up of observations on a wide variety of individuals taken at different points in time, usually years. However, the distinguishing feature of a panel is that the observations usually come from the same individuals at different points in time. Moreover, when the source of information that feeds the panel is administrative records, there is practically no non-response, which makes it possible to form compact panels that are ideal for analysis free of missing values and outliers without the need to apply imputation methods for missing information. The stage of exploratory data analysis, which precedes any application with panel data and is decisive for the results, is thus strongly favoured.

The development of a database such as the one containing the information from the personal income tax panel with increasingly richer data in terms of the number of units collected and their characteristics, together with the increase in the power of computer resources for their processing, has recently led to a proliferation in the use of microsimulation models with a view to estimating the effects of public policies.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.2  PURE PANELS AND EXPANDED PANELS

![image](d2d_images/chapter_title_below.png)

A pure panel follows the same individuals over the entire time period. This causes problems of loss of representativeness of the sample as time progresses, since there are individuals who may drop out of the sample for different reasons. In this way, the panel wears out over time (attrition) and can become invalid.

This problem is usually alleviated by the decision to use "expanded" panels as opposed to the more usual idea of pure panels. The reason for this decision is that the latter do not constitute a faithful cross-sectional representation of the population from which they are drawn because they are affected, over time, by a flow of inflows and outflows which, in the case of the personal income tax panel or any other tax, would take the form, respectively, of new taxpayers and those who cease to be taxpayers in each year. Statistically this means that such pure panels would not constitute, each year, a random sample of the taxpayers of the year. This will have pernicious effects in at least two respects. On the one hand, cross-sectional panel studies would require the development of different statistical estimators each year based on sample rescaling techniques, i.e. assigning specific annual weights to each individual in the panel (elavation factors). Obviously, these estimators will naturally be more complex the lower the degree of similarity between the pure panel and the total number of respondents for the year under consideration. Consequently, the differences between the estimators for one year or another will depend on the degree or level of similarity (Panel/Population of taxpayers) previously mentioned.

On the other hand, pure panels on taxes would not allow the analysis of the specific peculiarities of new taxpayers or of those who cease to be taxpayers in each year, since, by their very nature, they could not contain any of them. In this sense, this limitation would make the panel less operational, especially if we take into account that in recent years new taxpayers in any tax tend to represent in each year a fairly significant percentage of the total and that, furthermore, by logic, there should be significant discrepancies between new taxpayers and old taxpayers.

The "expanded" panel emerges as a way to try to eliminate the pernicious effects mentioned above. It allows, however, all the studies associated with pure panels to be carried out, as it contains one of them as a sub-panel. It consists, in essence, of representative samples of taxpayers that are overlapping and that can be extracted recurrently, once the first one has been selected, by incorporating (or expanding) an additional sub-sample of the new taxpayers each year, compared to the previous ones, with an affixation or size to that of the already existing sample compared to the total of old taxpayers. Obviously, new taxpayers joining the panel will continue to be observed from the time of joining onwards. The drop-outs will, in fact, arise as a result of such observation, i.e. they will appear on the panel naturally when they are not found among the year's filers. In this way, representative samples will be available for each year in which we will have identified new and old filers as well as those who have left in a given year, the common part of these samples being the aforementioned pure panel subcontained in them. The expanded panel of the IEF provides the appropriate raising factors to carry out the cross-sectional estimates each year with a bounded error.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.3  COMPARISON BETWEEN ANNUAL SAMPLES, COMBINATIONS OF CROSS-SECTIONS (POOLED DATA) AND PANELS

![image](d2d_images/chapter_title_below.png)

Whenever there are no selection difficulties, as in the case of administrative registers, annual samples are usually used. An isolated annual (or cross-sectional) sample provides very rich information for a given point in time. However, it lacks a time dimension, which limits its usefulness considerably. However, when several samples obtained independently in different years (called independent cross-sectional combinations or data pools) are available, the richness of the applicable analyses increases exponentially.

Like the panel, a combination of independent cross-sections (data pool) has a temporal dimension, since it is formed from observations on a large variety of individuals taken at different points in time, usually years. However, the distinguishing feature of a data pool is that the observations do not come from the same individuals at different points in time, but the sample in each pool year faithfully represents the population of that year.

However, many studies on individuals, households, firms, etc. are repeated at regular intervals, often annually. If a random sample is drawn at each period, combining the results from them gives us a pool of data. By combining random samples drawn from the same population, but at different points in time, we obtain more precise estimators and more powerful test statistics, mainly due to the larger sample sizes involved. However, it must be borne in mind that the relationships between the dependent variable and some of the independent variables in the models applied must be maintained over time. Statistically, problems with a data pool may arise from the fact that the population may have different distributions in different periods, which is often solved by introducing dummy variables. Problems of non-constant variability over time or heteroscedasticity may also arise (many individuals and several periods make it almost impossible to maintain constant variabilities, usually required in economic modelling), but these problems are also solvable statistically (econometric treatment of the heteroscedasticity problem).

Combinations of cross-sections are also very useful for assessing the impact of certain events or policies. They are generally used when two or more cross-sectional data sets, collected before and after the occurrence of an event, are available to determine the effect of the economic outcomes of that event. For example, to assess the impact of a tobacco tax change on tobacco consumption, two random samples can be drawn at different points in time, so that at one point in time the tax change did not occur and at the other point in time it did. Most of the estimates of change and the sometimes successive estimates used in these cases are reasonably feasible from a pool of data.

However, the panel format is, as far as the simulation of tax reforms is concerned, far superior to a pool of annual samples. There are two strong arguments to justify this assertion:

1.  The panel allows the evaluation of tax reforms from a dynamic perspective. Specifically, it allows the impact of any tax change on the same individual (or household or fiscal unit) to be analysed over time. In other words, it allows for a structural analysis of reforms. This is a fundamental issue in the evaluation of tax reforms because individuals alter their behaviour in response to tax changes. And many of these changes do not occur in the instant after the reform but one or several periods later, so the time dimension of the panel to introduce the dynamics is essential.

1.  The effects of a reform can be measured more reliably when we compare homogeneous units (individuals or household or fiscal units). For example, when we analyse the impact of a reform on the net income of the poorest individuals (those in the first income decile), we compare the same group of individuals. Hence, it is essential to work with observations of the same individuals at different points in time.

But we should not underestimate annual samples either. A single annual sample in isolation may not have much power, but when a pool of successive annual samples is built up, the richness of the analysis increases exponentially and even allows the results obtained by means of panel analysis to be contrasted. Let us not forget that panel econometric techniques are not easy to implement, while there are not so many difficulties with pooled data. What is evident is that, in the case of personal income tax, as administrative records are available, stratified sampling with geographical criteria and some other additional type of criterion (income brackets or sources of income) is easy to carry out. This means that it is very appropriate to have both successive annual samples and a panel.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.4  ECONOMETRIC MODELS WITH PANEL DATA

![image](d2d_images/chapter_title_below.png)

The double dimensionality of a panel leads us to consider the panel regression model as a set of models for each value of the time variable. Note that what we call here a time variable can be any other variable that classifies individuals into different significant groups, e.g. geographical regions, firms, etc. However, for simplicity we will continue to refer to this second dimension of the panel as the time dimension.

Let us consider that we start from the regression model that has as dependent variable the variable and as independent variables![image](d2d_images/image006.png)given by the equation:

![image](d2d_images/image481.png)

Given a set of N observations for each of the endogenous and exogenous variables, we can write the model as follows:

![image](d2d_images/image608.png)

Consider now the above model for each time unit t where t=1, 2,3,..., T. This model, called the panel data model, can be written as follows:

![image](d2d_images/image114.png)

or in closed notation:

![image](d2d_images/image336.png)

where i= 1,....,N sample observations and t=1,...,T time instants. We have that uit  are the error terms at each time instant. We have that β0β1β2 , ...,βk   are the parameters to be estimated.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.5  PANEL MODELS WITH CONSTANT COEFFICIENTS

![image](d2d_images/chapter_title_below.png)

If we want to consider a panel data model as a standard regression model with NxT observations, we have to require the following conditions typical for any regression model:

![image](d2d_images/image327.png)for all t or time instant.

![image](d2d_images/image098.png)for any time instant t (homoscedasticity)

## ​​​​![image](d2d_images/image354.png)for any observation i≠ j and for any time instant t≠ s       (no autocorrelation)

![image](d2d_images/image510.png)for all i and t (exogeneity)

uit  follows a normal distribution with mean 0 and  ![image](d2d_images/image522.png)

Estimating this panel data model as a regular ordinary least squares regression model leads us to obtain coefficient estimators that are the same for each of the time instants in the sample. In this case we have to pay special attention to the problems of heteroscedasticity (typical when a large dataset is available for the estimation of the model) and autocorrelation (typical when long time series are available). Nor should we forget about residual normality (more difficult to comply with when more observations are available) and non-multicollinearity. It is unusual for panel data models to be treated as constant coefficient models).

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.6  FIXED EFFECTS PANEL MODELS

![image](d2d_images/chapter_title_below.png)

Consider the following general panel data model:

![image](d2d_images/image361.png)

where i= 1,...,N sample observations and t=1,...,T time instants.

Let us assume that the residuals of this model can be decomposed into a componentαi   relating to the sample observations or individuals independent of time, a componentϕt relating to the time instants of the panel independent of individuals, and a componentεit   relating to the variation across individuals and across time instants. We can then write the panel model as follows:

![image](d2d_images/image482.png)

When there are many sample observations (individuals) and few time instants (geographical regions, companies, etc.) the variation in the sample due to time instants is captured by introducing T-1 dichotomous variables dt  associated with each of the time instants (minus one which is taken as a reference to avoid multicollinearity). The variable d1  takes the value of 1 in the case that the observation refers to time instant 1 and takes the value 0 for the rest of the time units. Similarly, when there are few sample observations and many time instants, differences across the different individuals in the sample are captured by including N-1 dichotomous variables andi associated with each of the sample individuals (minus one which is taken as a reference to avoid multicollinearity). These variables take the value of 1 for a given individual and 0 for the rest.

The panel data model will now be as follows:

![Imagen que contiene Texto Descripción generada automáticamente](d2d_images/image480.png)

In the case of panel data with fixed effects, the final model to be estimated by Ordinary Least Squares (OLS) is as follows:

![image](d2d_images/image552.png)

The parameters pi will estimate the fixed effects relating to individuals or sample observations and the parameters qt will estimate the fixed effects relating to each time instant considered in the panel. The model can have only one of the individual or time effects (FIXONE) or both effects (FIXTWO). The parameters βj estimate the coefficients of the variables in the model that are common to individuals and time points.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.7  RANDOM EFFECTS PANEL MODELS

![image](d2d_images/chapter_title_below.png)

In the random effects model theαi and/or theϕt, vary randomly across individuals and over time. The model no longer has deterministic components. Its equation remains:

![image](d2d_images/image469.png)

but now, the error orit  has an individual random componentαi that is invariant across time instants and characterises each individual. This component is called the "between-group" component.

In turn, the error orit  has a random time componentϕt   that is invariant across individuals and characterises each of the time instants. This component is called the "within-groups" component.

Finally, error orit  also has a componentεit  which is random across individuals and over time.

In the random effects model all the components of the errorαi , ϕt , εit  are random with a normal distribution of null mean. Moreover, they are uncorrelated with themselves ![image](d2d_images/image155.png) for every individual![image](d2d_images/image484.png) , and for every time instant t≠ s), they have constant variance (homoscedasticity) and satisfy the exogeneity hypothesis![image](d2d_images/image433.png) for every individual![image](d2d_images/image484.png), and for every time instant ![image](d2d_images/image542.png)

It is also fulfilled ![image](d2d_images/image048.png)![image](d2d_images/image523.png)![image](d2d_images/image566.png)

The total error variance shall be

![image](d2d_images/image197.png)

The panel data model with random effects is estimated using the generalised least squares GCM method.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.8  DYNAMIC MODELS WITH PANEL DATA

![image](d2d_images/chapter_title_below.png)

Models with panel data can also have lagged variables and lags can appear in both the dependent and independent variables, although most commonly the lags appear in the dependent variable. A dynamic panel data model with a time lag in the dependent variable would have the following expression:

![image](d2d_images/image360.png)

To estimate this type of model, instrumental variables are usually used to replace the lagged endogenous variable yi,t-1 with an instrument y\*i,t-1 that is highly correlated with yi,t-1 and uncorrelated with the error. The new model to be estimated will be:

![image](d2d_images/image609.png)

In this case Ordinary Least Squares can be used for estimation, but it is difficult to find a suitable instrument. There is a large literature on the availability of instruments for the economic and other variables most commonly used in practice in applied panel models. Special attention should be paid to multicollinearity and autocorrelation problems when estimating this type of panel with instrumental variables (a variable and its respondent are logically correlated and may be linearly dependent). We should also not forget the problems of heteroscedasticity, especially when the samples are very large (this problem usually occurs in micro data).   There are also special alternative methods for estimating certain dynamically structured panels. The methodology of Arellano and Bond provides solutions for the estimation of dynamic panel data models.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.9  LOGIT AND PROBIT MODELS WITH PANEL DATA

![image](d2d_images/chapter_title_below.png)

Given the general linear model:

![image](d2d_images/image456.png)

with a probability as the dependent variable, if the function F is chosen as the distribution function of a Normal(0,1) so that the values of Pi always fall in the interval \[0,1\], we obtain the so-called Probit model, whose parametersβ admit estimation by maximum likelihood.

Let us not forget that:

![image](d2d_images/image458.png)

In the case of![image](d2d_images/image625.png)we would be dealing with the Logit model.

Logit and Probit models can be given a panel structure by introducing a new time-varying index.

The panel data Logit model can be written as follows:

![image](d2d_images/image256.png)

The estimation of the model parameters by maximum likelihood leads us to maximise the function:

![image](d2d_images/image188.png)

In this  way, the maximum likelihood estimate of the parameters of a Logit  model is obtained.

Similarly, the Probit panel data model can be written as follows:

![image](d2d_images/image205.png)

The estimation of the model parameters by maximum likelihood leads us to maximise the function:

![image](d2d_images/image065.png)

In this  way, the maximum likelihood estimate of the parameters of a Probit model is obtained.

A similar path can be followed to define panel data models with Poisson distribution and panel data models with negative binomial distribution.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.10  UNIT ROOTS AND COINTEGRATION WITH PANEL DATA

![image](d2d_images/chapter_title_below.png)

Unit root tests with panel data are similar to unit root tests performed on an individual series. The following equation is used as a starting point:

![image](d2d_images/image133.png)

Two assumptions can be made about![image](d2d_images/image574.png)The first is =![image](d2d_images/image677.png)an assumption used in the unit root tests of Levin, Lin and Chu (LLC tests), Breitung and Hadri. The second assumption allows![image](d2d_images/image009.png)to vary freely in the cross sections, hypothesis used in the Im, Pesaran and Sim (IPS) tests, in the Fisher-ADF and Fisher-PP tests proposed by Maddala and Wu and the Choi test.

The Fisher-ADF and Fisher-PP tests proposed by Maddala and Wu to test for the existence of unit roots in panel data combine the p-values of the individual unit root tests. If we defineπi as the p-value of the i-th cross-section unit root test, then, under the null hypothesis that there is a unit root in all N cross-sections, it is verified:

![image](d2d_images/image170.png)

Additionally Choi demonstrates that:

![image](d2d_images/image375.png)

The simplest panel cointegration test is to check, by means of a panel unit root test, that the residuals of the panel model are free of unit roots. There are other formal panel cointegration tests such as the Engel and Granger   test, the Kao and Pedroni test and the McKoskey and Kao test.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.11  stata AND THE PANEL DATA MODELS

![image](d2d_images/chapter_title_below.png)

STATA has the xtreg command that allows estimating models with fixed and random effects panel data. Its syntax is as follows:

Random effects model

xtreg dependent\_independent variable independent variables, re options

The most important options are i(variable) to indicate the panel ID variable, sa to use the Swamy-Arora variance composites estimator, vce(type) to indicate the type of robust, bootstrap or jackknife estimation, cluster to adjust standard errors for within-group correlations, and level(n) for the confidence level n.

Model estimated using the regression estimator between

xtreg dependent\_independent variable independent variables, be options

The most important options are i(variable) to indicate the panel ID variable, wls to use the weighted least squares estimator, vce(type) to indicate the bootstrap or jackknife estimation type and level(n) for the confidence level n.

––––––––

![image](d2d_images/scene_break.png)

Fixed effects model

xtreg independent\_dependent variable independent variables, fe options

The most important options are i(variable) to indicate the panel ID variable, vce(type) to indicate the type of robust, bootstrap or jackknife estimation, cluster to adjust standard errors for within-group correlations, and level(n) for the confidence level n.

Maximum likelihood random effects model

xtreg dependent\_independent variable independent variables, mle options

The most important options are i(variable) to indicate the panel ID variable, noconstant to remove the constant term from the model, vce(type) to indicate the type of bootstrap or jackknife estimation and level(n) for the confidence level n.

Population average model

xtreg dependent\_independent variable independent variables, pa options

The most important options are i(variable) to indicate the panel ID variable, noconstant to remove the constant term from the model, offset(variable) to include the variable in the model with coefficient restricted to unity, vce(type) to indicate the type of bootstrap or jackknife estimation and level(n) for the confidence level n, corr(correlations) for a given group correlation structure, forcé to obtain estimates when observations are unequally spaced in time, mnp to use as divisor of the N-P mean, rgf multiplies the estimated robust variance by (N-1)/(N-P), scale(x2) uses as scale parameter the Pearson's chi-squared statistic, scale(dev) uses as scale parameter the variance between degrees of freedom, scale(phi) does not rescale the variance, scale(n) uses n as scale parameter.

First, an example is presented using the regression estimator between.

![image](d2d_images/image213.png)

The same model is then estimated using fixed effects.

![image](d2d_images/image645.png)

Assume now that there is heteroscedasticity in the above model. The estimation will be performed with the robust option as follows:

![image](d2d_images/image308.png)

![image](d2d_images/image003.png)

The model is then estimated using random effects.

![image](d2d_images/image600.png)

The model is then estimated using random effects and the maximum likelihood estimator.

![image](d2d_images/image702.png)

![image](d2d_images/image656.png)

Finally, the model is estimated using the population mean estimator.

![image](d2d_images/image110.png)

The xtgls  statement fits panel data models using feasible generalised least squares (GLS). The syntax is similar to the xtreg case, but the most important options change. 

option i(variable) identifies the panel ID variable, t(variable) identifies the panel time variable, noconstant suppresses the constant term, panels(iid) uses i.i.d. error structure, panels(heteroskedastic) adjusts the panel with heteroscedasticity and no autocorrelation, panels(correlated) adjusts the panel in the presence of heteroscedasticity and autocorrelation, corr(independent) uses independent autocorrelation structure, corr(ar1) uses AR(1) autocorrelation structure, corr(psar1) uses a specific panel with AR(1) autocorrelation structure, igls uses the iterated GLS estimator instead of the two-step estimator, force performs the estimation when observations are unequally spaced in time, nmk normalises standard errors by N-K instead of N and level(n) places a confidence level n.

As a first example we estimate a panel model in the presence of heteroscedasticity.

![image](d2d_images/image253.png)

The panel is then estimated in the presence of heteroscedasticity and autocorrelation.

![image](d2d_images/image252.png)

![image](d2d_images/image310.png)

The model is then estimated in the presence of heteroscedasticity and assuming that in each group the errors follow an AR(1)   process.

![image](d2d_images/image245.png)

In all panel fits performed so far, we observe good individual significance of the parameters in all fits (very small p-values) and also good joint significance (the Wald test has a very small p-value).

The xtivreg  statement fits panel data models with instrumental variables using two-stage least squares. The syntax is similar to the case of xtreg. For random effects models the additional options ec2sls can be used to use Batagi's EC2SLS random effects and nosa to use Batagi's variance components estimator.

We then estimate a fixed effects panel model explaining the logarithm of the wage ln\_w as a function of age and tenure using the square of age2, the variable not\_smas and the variables union and south for tenure as instruments.  The syntax would be as follows:

![image](d2d_images/image708.png)

The xtregar statement fits fixed and random effects panel data models with AR(1) perturbation. The syntax is similar to the case of xtreg. An example is given below. 

![image](d2d_images/image319.png)

![image](d2d_images/image455.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.11.1  Logit, probit and Poisson models with panel data

![image](d2d_images/chapter_title_below.png)

The xtlogit, xtprobit and xtpoisson  statements allow to fit logit, probit and Poisson models with panel data. The options are very similar to those of the xtreg procedure.

As a first example we fit a panel logit  model with fixed effects.

![image](d2d_images/image293.png)

Adjustment can also be made with random effects.

![image](d2d_images/image363.png)

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image241.png)

We now perform the population mean fit of a logit model in the presence of heteroscedasticity.

![image](d2d_images/image582.png)

![image](d2d_images/image136.png)

We then fit a panel probit model with random effects.

![image](d2d_images/image421.png)

We then fit a Poisson model with panle data and fixed effects.

![image](d2d_images/image190.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 5.11.2  Dynamic panel estimation using Arellano-Bond methodology

![image](d2d_images/chapter_title_below.png)

STATA has the xtabond  statement, which allows the estimation of dynamic models with panel data of the type:

![image](d2d_images/image661.png)

The syntax of xtabond is similar to xtreg, but supports certain specific options: diffvars(variables) defines already differenced exogenous variables, inst(variables) introduces additional instrumental variables, lags(n) uses n lags of the dependent variable, maxldep(n) defines the maximum number of lags to use on the dependent variable to use as an instrument, maxlags(n) defines the maximum number of lags on the default variables to be used as instruments, robust estimation in the presence of heteroscedasticity, artests(n) uses n as the maximum order in autocorrelation tests, small produces a report of statistics for small samples, level(n) sets n as the confidence level, pre(variables \[... \]) defines default variables and tw0(variables \[... \]) defines default variables and tw0(variables \[... \]) defines default variables and tw0(variables \[... \]) defines default variables.\]) defines default variables and twostep uses the two-step estimator.

An example is given below.

![image](d2d_images/image078.png)

![image](d2d_images/image443.png)

We will now estimate the dynamic panel with heteroscedasticity.

![image](d2d_images/image041.png)

We then use the two-step method.

![image](d2d_images/image548.png)

6Chapter 6

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# ​NEURONAL NETWORK models

![image](d2d_images/chapter_title_below.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.1  ​​​​​​​DESCRIPTION OF A NEURAL NETWORK

![image](d2d_images/chapter_title_below.png)

## ​​​​​​​

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.1.1  Definition

![image](d2d_images/chapter_title_below.png)

We can define a neural network as a set of highly interconnected information processing elements, which are able to learn from the information fed to them. The main feature of this new neural network technology is that it can be applied to a large number of problems ranging from real complex problems to sophisticated theoretical models such as image recognition, speech recognition, signal analysis and filtering, classification, discrimination, financial analysis, dynamic prediction, etc.

Neural Networks attempt to emulate the nervous system, so that they are able to reproduce some of the main tasks performed by the human brain by mirroring the fundamental behavioural characteristics of the human brain. What neural networks actually attempt to model is one of the physiological support structures of the brain, the neuron, and the structured and interconnected groups of several of them, known as networks of neurons. In this way, they build systems that exhibit a certain degree of intelligence. However, we must insist on the fact that Artificial Neural Systems, like any other man-made tool, have limitations and only bear a superficial resemblance to their biological counterparts. Neural networks, in relation to information processing, inherit three basic characteristics of biological neural networks: massive parallelism, non-linear response of neurons to incoming inputs, and information processing through multiple layers of neurons.

One of the main properties of these models is their ability to learn and generalise from real examples. In other words, the network learns to recognise the relationship (which is equivalent to estimating a functional dependency) that exists between the set of inputs provided as examples and their corresponding outputs, so that, once learning is complete, when the network is presented with a new input (even if it is incomplete or contains an error), based on the functional relationship established therein, it is capable of generalising it by offering an output. Consequently, we can define an artificial neural network as an intelligent system capable not only of learning, but also of generalising.

A neural network is made up of processing units called neurons or nodes. These nodes are organised into groups called "layers". There are generally three types of layers: an input layer, one or more hidden layers and an output layer. Connections are established between adjacent nodes of each layer. The input layer, through which data is presented to the network, consists of input nodes that receive information directly from the outside. The output layer represents the response of the network to a given input and this information is transferred to the outside. The hidden or intermediate layers are responsible for processing the information and are interposed between the input and output layers and are the only ones that have no connection with the outside.

The most common network structure is the so-called feedforward network, as the connections between neurons are established in one direction only, in the following order: input layer, hidden layer(s) and output layer. For example, Figure 6-1 shows a network with two hidden layers. However, there are also feedback networks, which can have backward connections, i.e. from nodes in one layer to processing elements in previous layers, as well as recurrent networks, which can have connections both between neurons in the same layer and from a node to itself. Figure 6-2 illustrates a network model in which the different types of connections we have discussed, i.e. forward, backward and recurrent, coexist, showing full interconnection.

![image](d2d_images/image563.png)Input layer

![image](d2d_images/image345.png)![image](d2d_images/image391.png)![image](d2d_images/image483.png)Hidden layers Output layer

![image](d2d_images/image272.png)![image](d2d_images/image235.png)

Figure 6-1    Figure 6-2

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.1.2  ​​​​​​​Output function and transfer or activation functions

![image](d2d_images/chapter_title_below.png)

––––––––

![image](d2d_images/scene_break.png)

The fully interconnected neural network is one in which the nodes in each layer are connected to all nodes in the next layer. The input layer has the sole task of distributing the information presented to the neural network for processing in the next layer. The nodes of the hidden layers and the output layer process the signals by applying processing   factors, called weights. Each layer has an additional node called bias, which adds an additional term to the output of all nodes in the layer. All inputs at a node are weighted, combined and processed through a function, called a transfer function or activation function that controls the flow of output from that node to connect to all nodes in the next layer. This transfer function serves to normalise the output.

An artificial neural network is nothing more than the connection of several neurons. Thus, artificial neurons, also called units, nodes or processing elements, constitute the basic unit of a neural network (analogous to the biological neuron). These artificial neurons operate like simple microprocessors, whose function is to respond to a given input pattern. Each processing element, as in a biological neuron, receives inputs from other neighbouring nodes, or from the outside, in the case of the input layer, and its function is to transform, by means of simple internal calculations, these inputs into a single output value which it sends to the other nodes (constituting their input) or, if the neuron in question belongs to the output layer, to the outside. The connections between processing elements have a weight or connection strength W associated with them, which quantitatively determines the effect produced by some elements on others. In other words, the network information is stored in the weights, just as in biological neuron networks.

Whether an input has an excitatory or inhibitory effect depends on whether the sign of the corresponding weight is positive or negative, respectively. The effectiveness of the inputs is determined by the strength of the connection, represented by the absolute value of the weights. Thus, each of the elements Wij of the weight matrix W, known as the pattern of connections, represents the strength and direction of the relationship of process element j, with respect to process element i.

The process of transforming inputs into outputs in a forward-fed artificial neural network with r inputs, a single hidden layer composed of q processing elements, and an output unit can be summarised in the following formulation of the network output function:

![image](d2d_images/image333.png)where, ![image](d2d_images/image524.png)is the output of the network, the vector![image](d2d_images/image005.png)represents the inputs of the network (the 1 corresponds to the bias of a traditional model), ![image](d2d_images/image119.png)are the weights of the neurons of the input layer to those of the intermediate or hidden layer, ![image](d2d_images/image388.png), represents the connection strength of the hidden units to the output units (j=0 indexes the bias unit), q is the number of intermediate units, i.e. the number of nodes in the hidden layer, ![image](d2d_images/image475.png)is the activation function of the output unit and ![image](d2d_images/image447.png)corresponds to the activation function of the intermediate neurons. W is a vector that includes all the weights of the network, i.e. ![image](d2d_images/image492.png). Figure 6-3 represents the function![image](d2d_images/image215.png).

![image](d2d_images/image288.png)

Figure 6-3

Historically, threshold functions were used as activation functions, the effect of which is that the units are activated abruptly, i.e. either they are not activated, or they are activated suddenly. The response can only be black or white, so these functions are suitable for classification and recognition tasks. Over time, activation functions were introduced that allow neurons to gradually activate as the activity level of their inputs increases, rather than their state being only on-off. Specifically, the function proposed is the sigmoidal or logistic function ![image](d2d_images/image079.png), which produces a smoothed sigmoidal response.

If in the expression of ![image](d2d_images/image584.png)we consider![image](d2d_images/image502.png), we find that ![image](d2d_images/image479.png)corresponds to the binary logit model.

In general, the functions F and G can take any form in the expression of![image](d2d_images/image215.png). However, it is common practice to consider either that the activation function of the output and intermediate neurons is identical, ![image](d2d_images/image350.png), and that it corresponds to the sigmoidal function, or that ![image](d2d_images/image315.png) i.e. that it is the identity function and that G(a) corresponds to the logistic or sigmoidal function, which is equivalent to considering that there is only an activation function (the sigmoidal one) in the hidden units. This last hypothesis is the one we assume, from now on, in our approach, because in addition to greatly simplifying the notation, it is the one most frequently adopted in the construction of artificial neural networks. We should also point out that we use the sigmoidal function, which is the most commonly used, since its properties allow us to employ learning algorithms such as error backpropagation, which we use in our work. Formally, it is also possible to show that an ANN with a hidden layer and sigmoidal activation function is able to approximate any measurable function.

Assuming, as we have indicated, that there is only an activation function in the intermediate neurons and that this corresponds to the sigmoidal one, we have:

![image](d2d_images/image400.png)

Another possibility, of great utility in econometric applications, is to consider that in the network we represent, a forward-fed artificial neural network with r inputs, a single hidden layer, composed of q processing elements, and an output unit, there are also direct connections between the input and output layers. In this case, the output of the network is obtained by the following expression:

![image](d2d_images/image045.png)whereα is a vector of dimension r× 1 representing the weights of the direct connections between the input and output layers. Logically, now W, which collects all the weights of the network, is composed of ![image](d2d_images/image204.png).

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.2  ​​​​​​​NEURAL NETWORKS AND REGRESSION MODEL FITTING

![image](d2d_images/chapter_title_below.png)

The output function![image](d2d_images/image215.png)can be broken down into two parts. The first of these, which corresponds to the first two terms, represents a linear model, so that, if we take as input variables r lags of the variable x, it becomes a linear regression on the lagged input variables, which act as explanatory variables, and a constant ( ![image](d2d_images/image474.png)).

This first part, as is logical, captures the linear dependencies between the input patterns and the outputs of the network. The second part, which is the third term of the previous formulation, captures, if they exist, the non-linear dependencies between the input variables and the output of the network, given that the function used is non-linear. Concretely, this third term is a composition, weighted with the synaptic weights of the intermediate neurons to the output neurons ![image](d2d_images/image282.png)of sigmoidal functions of the network inputs, the latter weighted by the connection strength of the input units to the intermediate ones. This model can be considered an extension of the well-known and frequently used linear models, since it is composed of a linear model augmented with non-linear terms.

As we can see, the network that we describe by means of the expression of![image](d2d_images/image577.png), enjoys such a degree of flexibility that it allows all types of functions to be adjusted, which is why artificial neural networks are characterised as "universal approximators". In other words, a neural network is capable of learning any function. The artificial neural network model should be considered as one of a set of non-parametric models to which the results of statistical inference can be applied. Thus, the range of opportunities is not limited to artificial neural networks, but, on the contrary, multiple alternatives such as classification and regression trees (CART) and multivariate adaptive regression splines (Friedman, 1991).

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.3  ​​​​​​​LEARNING IN NEURAL NETWORKS

![image](d2d_images/chapter_title_below.png)

After designing an artificial neural network, what we want to achieve with it is that, for certain inputs, or example patterns that we supply to the network, it is capable of generating a desired output. To achieve this, in addition to the topology of the network (understood as the structure of the network) being appropriate, it is required that the network learns to provide correct solutions, i.e., it is necessary to subject the network to a learning or training process. Learning can be understood as a trial and error procedure that allows the statistical estimation of the parameters of the neural network model used.

Three basic types of learning are generally considered to give rise to different types of neural networks. When the trainer provides the network with the desired output, the learning is said to be supervised. Otherwise, it is unsupervised learning. Finally, an intermediate type of learning is reinforcement or hybrid learning, in which the trainer only provides the network with an indication of whether the response to a given input is good or bad.

Unsupervised learning neural networks are those that train without the need for an external supervisor or trainer to provide the network with the desired output, as they are able to organise their parameters internally by adapting to the environment in the best possible way. The network, once presented with the inputs, is able to determine, on its own, the characteristics, correlations, regularities or categories of the inputs, providing a coded output. Therefore, we can say that these networks have self-organising properties. This type of learning should only be used when there is some degree of redundancy in the input patterns presented to the network. Otherwise, the network is unable to detect the behavioural patterns and characteristics of the data offered to it. The structure of the network must be appropriate for the type of input data presented to it, because depending on the architecture of the unsupervised learning neural network, it will be able to detect one type of pattern or another. Neural systems with unsupervised learning are characterised by simple architectures, since the learning laws already complicate their operation quite a lot. Secondly, most of them are feed-forward networks, or feed-forward networks with a single intermediate or hidden layer. The most typical models that train by unsupervised learning are the networks of Kohonen (1977,1984) and Grossberg (1976). Unsupervised networks are often used for classification. In particular, Cohonen networks are often used when one of the objectives of the analysis is the simple and intuitive visualisation of clusters, when the shape of the clusters is unknown, or when there are outliers or errors in the data.

Neural networks with supervised learning, which are usually associated with the multilayer perceptron (Multilayer Perceptron MLP) and the radial basis function RBF, have an output pattern or dependent variable that allows them to contrast and correct the data. Neural networks with an output pattern are a technique used for classification and prediction, which can be used to segment markets, position products, make demand forecasts, evaluate credit files or analyse the value of shares on the stock exchange, and a host of other applications. The multilayer perceptron neural network model is based on back-propagation learning and typically uses the back-propagation algorithm, the conjugate gradient descent algorithm and the Levenberg-Marquardt algorithm.

Just as in the multilayer percetron all layers have the same (linear) structure, in the radial basis function (RBF), the intermediate layer has precisely a radial structure. The radial basis function is a supervised function with output pattern that performs classifications (and or forecasts) from ellipses and hyperellipses that split the input data space. The radial basis function has certain advantages over multi-layer neural networks including the fact that it can be modelled using only one intermediate layer instead of several and that its algorithm is faster and never settles on a local solution.

It should be noted that, sometimes, although supervised learning can be applied, unsupervised learning methods can be very useful and even provide better results. For example, the Back-Propagation Algorithm in multi-layer networks is very slow, because the value that each weight adopts depends on the values it takes in the other layers. To avoid this problem, either an unsupervised learning method or a hybrid system could be used, which allows some layers to self-organise before their outputs are passed to the supervised network. On the other hand, it should be noted that it may be advisable to perform some kind of unsupervised training to networks previously trained by supervised learning mechanisms. The purpose of this approach is to allow the network to gradually adapt to possible changes in the environment.

Reinforced or hybrid learning is intermediate between supervised and unsupervised learning. In this type of learning, as in supervised learning, there is an external teacher or supervisor. However, they differ in that the "trainer" does not provide the network with the desired outputs, as its behaviour is evaluated globally, i.e. it is only possible to decide and indicate to the network whether its response is good or bad and to what degree it behaves well. The rationale of reinforcement learning is that actions that lead to an improvement in the behaviour and response of the neural network should be reinforced.

Analogous to supervised learning, the neural network responds by generating a set of outputs, corresponding to the input patterns presented to it. However, since no desired outputs are provided to the system, it is impossible to compute the fraction of error made by each of the output units. Only an indicator of the success or failure of the network is available, similar to a utility function, which evaluates the network as a whole. This requires the use of much more complex learning algorithms than in supervised learning, as well as higher demands on sample size.

Formally, the learning process consists of solving a non-linear least squares problem. To do this, numerical optimisation methods such as back-propagation, which is based on the stochastic approximation algorithm of Robbins and Monro (1951) applied to non-linear least squares, must be used. It is currently the most widely used algorithm.

Once learning has been completed, the network must be tested. The test phase consists of introducing new input patterns and checking the efficiency of the generated system. If it is not acceptable, the training phase is repeated using new example-patterns, and it may even be necessary to modify the structure of the network.

6.4  ​​​​​​FUNCTIONING OF A NEURAL NETWORK

For the creation and application of a neural network to a specific problem, we have to distinguish the following steps:

Conceptualisation of the model for the study of the specific problem. In this Model we must point out the inputs, the outputs and the information available.

Adaptation of the available information to the structure of the network to be created. In other words, the learning patterns, part of the information that will be used for training or learning the network, and the validation patterns, part of the information that will be used to validate the network, will be created.

Learning phase. The network is presented with suitable patterns and the network provides an output, this process is repeated in a number of stages, these outputs are compared with the expected outputs and the various learning algorithms attempt to minimise the error between the output provided by the network and the expected output.

Validation phase. The trained network is presented with the set of validation patterns, and the error made by the network on this set is seen, this error is a measure of the goodness of the network.

Generalisation phase. If we have obtained a suitable network, we proceed to use the network as a predictor model, providing it with a new input, the network will process it and give an output.

As an illustrative example, we consider a bank that wants to build a model for granting personal loans for the purchase of a car. The information set is made up of a file of 5,000 previous clients in which the following variables are recorded for each client: sex, marital status, salary, assets, current account, etc., and whether or not the client has made regular payments. The model would therefore have an input layer with as many nodes as there are variables in the file, one or several intermediate layers and an output layer with one node, in which there is an expected output of zero or one depending on whether or not the customer has paid regularly.

We will divide the file into a part that will constitute the learning set and the other part the validation set. The network is given a learning set as input, the network will be trained, we would validate the model with the validation set and when the new customer arrives we present his information to the network and if the network is well trained it will classify the customer in the class of those who pay on time or in the complementary class.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.5  ​​​​​​​THE BACK-PROPAGATION LEARNING ALGORITHM (BACK-PROPAGATION)

![image](d2d_images/chapter_title_below.png)

The learning or training process of the network consists of presenting the network with the set of patterns in a certain number of pre-set stages, in order to minimise the learning error, understood as the quadratic difference between the expected output and the output provided by the network. In the first stage, the network has some randomly chosen interconnection weights, the network is presented with an input vector in the first stage, constituted by the first pattern, this is propagated through all the layers until it provides an output, the output signal is compared with the desired output in all the nodes of the output layer. This process is performed for all the patterns in the learning set, and the sum of the squared errors of all the patterns will be the error made by the network in that first stage.

The objective is to change or update the interconnection weights for the second stage in order to reduce the total error. The idea of the back-propagation algorithm is to update the interconnection weights so that the error signal is transmitted backwards from the output layer; however, these intermediate units only receive a fraction of the error proportional to their relative contribution to the output. This process is repeated layer by layer until all nodes have received an error signal describing their contribution to the error. Once the weights have been updated, the process of re-presenting the learning patterns and error calculation is repeated, either because the total error is less than a preset one, or because the preset number of stages has been completed.

The importance of this process is that as the network is trained, nodes in the hidden layers learn to recognise different features of the problem.

For the mathematical description of the algorithm in a three-layer network, we will use the following notation (Pascual and Parras):

![Interfaz de usuario gráfica, Texto, Aplicación Descripción generada automáticamente](d2d_images/image370.png)

![Texto, Carta Descripción generada automáticamente](d2d_images/image075.png)

The objective of back-propagation is to determine the set of weights (wij , wjk ), which minimise the quadratic error of the network. The algorithm starts with a set of arbitrary weights and is updated at each stage according to the following rule:

1.  Firstly, the weights of the final layer, wjk using the gradient descent technique:

![image](d2d_images/image397.png)

so that wjk is updated with a negative learning rate (-η), so that the updated wjk is ![image](d2d_images/image340.png)

1.  The update of the weights corresponding to the hidden layer are:

![image](d2d_images/image329.png)

Sometimes a moment term is added to the update, thus speeding up the weight update process.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.6  ​​​​​​​DISCRIMINANT ANALYSIS THROUGH THE PERCEPTRON

![image](d2d_images/chapter_title_below.png)

The purpose of the perceptron is to classify a set of input signals (input stimuli or patterns), into one of two classes, C1 or C2 . The decision rule for classification is to assign the inputs x1 , x2 ,...xn , corresponding to a given pattern, to class C1 if the output of the perceptron is +1, and to class C2 if the output of the perceptron is -1.

![Diagrama, Esquemático Descripción generada automáticamente](d2d_images/image385.png)

The first question that arises is how to determine the synaptic weights so that the perceptron gets a correct classification of each of the input patterns. Suppose we have p input patterns, represented by![image](d2d_images/image206.png)so that we know the class to which each of them belongs (we will call them training vectors or patterns). For example, ![image](d2d_images/image259.png)can represent a set of n symptoms of patient r who may (y=1), or may not (y=-1), present a certain disease.

It is possible to modify the synaptic weights through an iterative procedure, which we will call the network learning process, so that after a finite number of iterations the p input patterns are correctly classified, whenever possible, i.e. the classes C1 and C2 are linearly separable. Two classes are said to be linearly separable if there exists a set of weights, w1 , w2 ,...,wn , such that:

![Texto, Carta Descripción generada automáticamente con confianza media](d2d_images/image604.png)

This learning process consists of observing the output values for each of the training patterns and checking whether the classification made by the perceptron is correct. In case of incorrect classification, the weights are modified. The process is repeated, pattern by pattern, until all the training patterns are correctly classified, or the number of incorrect classifications is considered adequate. Specifically:

![Texto, Carta Descripción generada automáticamente](d2d_images/image176.png)

Therefore, at the output of the network there is a controller or teacher that compares the output of the network with the desired value, and in case they match (incorrect output) modifies the weights of the network as we have indicated above. It is therefore a supervised learning procedure with error correction. Note that the above learning rule can also be expressed as follows:

![image](d2d_images/image597.png)

where d(k) is the desired output at stage k.

The learning rate should be chosen so as to accelerate the convergence of the procedure. An appropriate choice of learning rate is as follows:

![image](d2d_images/image355.png)

Where ![image](d2d_images/image586.png)and ![image](d2d_images/image384.png). The normalised learning rule of the perceptron is thus obtained, as it ensures at each iteration that the synaptic weight vectors are normalised. The perceptron convergence theorem ensures that after a finite number of iterations the perceptron correctly classifies all training patterns, provided they are linearly separable (see Haykin 1994). If we now consider m neurons receiving the same input signals, we will have m outputs and we can apply the same learning process to each neuron, but now we have 2^m possible outputs for each input.

On the other hand, a discriminant rule d is an application corresponding to a partition of the space R^n into L disjoint regions R1 ,R2 ,...,RL , and is defined as:

Assign x to population Ci if xєRi

The maximum likelihood Gaussian classifier corresponds to a parametric estimation procedure where the samples (set of input signals) of class Ci , i=1,2, follow a multivariate normal distribution of mean![image](d2d_images/image629.png)and covariance matrix Σ, and classes C1 and C2 are equiprobable. It is defined as follows:

![Texto, Carta Descripción generada automáticamente](d2d_images/image167.png)

The perceptron and the maximum likelihood Gaussian classifier are linear classifiers. The perceptron operates on the assumption that the two classes are linearly separable while the Gaussian classifier does not. The perceptron is a non-parametric procedure, in the sense that it makes no assumptions about the shape of the distributions of each class. In this sense it is a more robust procedure. The normality assumption of the Gaussian classifier limits its area of application. The perceptron algorithm is adaptive and simple to implement; storage needs are reduced to synaptic weights and thresholding. On the other hand, the Gaussian classifier design is fixed, although it can be made adaptive, but it requires a significant increase in storage and the computations are more complex. The Gaussian classifier minimises the average probability of misclassification. With respect to which criterion or desirable measure is the perceptron optimal? Shynk (1990) has derived the perceptron algorithm from the following criterion: minimise the expected value of the error weighted by the difference between the synaptic potential and the threshold, i.e. ![image](d2d_images/image676.png)where d(k) is the desired output at the kth iteration.

The instantaneous estimator of the above objective function is:

![image](d2d_images/image416.png)

and its gradient vector:

![image](d2d_images/image287.png)

If we modify the weights in the opposite direction to the gradient, we obtain:

![image](d2d_images/image569.png)

which is the perceptron rule.

In a classification problem involving m classes, C1 , C2 ,..., Cm , we will use a layer of m neurons all connected to the same input signals and giving us m output signals (multilayer perceptron). If the input x \= (x1 ,x2 ,...,xn ) is of class C1 then the desired output is: d1  = 0, d2 = 0,..., di  = 1,..., dm  = 0.

If we introduce a hidden layer of neurons, i.e., a layer of neurons between the input and output neurons, which use the linear or logistic activation function, and the output neurons use the linear or logistic activation function, we can correctly classify sets of non-linearly separable patterns using the error backpropagation learning rule (see Haykin 1994). Moreover, it can be shown that these neural networks with a hidden layer are universal classifiers (Cybenko, 1989).

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.7  ​​​​​​​TIME SERIES ANALYSIS USING NEURAL NETWORKS

![image](d2d_images/chapter_title_below.png)

A time series consists of a sequence of values of several variables that evolve (change) over time. The aim is to predict the future behaviour of the phenomenon or dynamic system that generates these values based on a collection of historical data. For example, predicting electricity consumption or predicting the number of flu vaccines that will be demanded in a given region. The best way to solve these problems is to find the underlying law that generates these processes. This law can be obtained by analytical methods, such as a set of differential equations. However, the information we will have about the process will generally be partial or incomplete and, therefore, the prediction cannot be made by means of a known analytical model. An attempt will be made to discover some strong empirical regularity in the time series observations. In many real-world problems some regularities, such as periodicity, are masked by noise, and even some dynamic processes are described by chaotic time series, where the data appear random with no apparent periodicities.

Although chaos prevents any long-term prediction, however, promising results for short-term predictions are achieved using artificial neural networks that are described by a non-linear multivariate function:

![image](d2d_images/image713.png)

where![image](d2d_images/image665.png), t = m, m-1,....,k, are the given samples of the time series, F is an unknown non-linear function and k<m.

Most of the available techniques assume linear relationships between variables or between variables lagged in time. But these techniques are often inadequate for analysing real-world temporal data because of their inability to account for sudden changes of large amplitude and at irregular time intervals. The formulation of reasonable non-linear models is a very difficult task. Therefore, since the goal is to make good forecasts, neural networks are a good alternative for the calculation of predictions. Lapides and Fraber (1987) were the pioneers in applying neural networks for modelling simple (noise-free) systems and their prediction. The main problem, at least for the time being, is the difficulty of finding the appropriate network for each case; there are no fixed rules that determine the appropriate neural network architecture for each case of study. The work of La Fuente and Pino (1995) presents a comparative analysis for the calculation of forecasts between Box-Jenkins methodologies and neural networks and proposes the use of the Box-Jenkins methodology as a prior step to the design of the neural network structure.

The multilayer perceptron is the most widely used model of artificial neural networks for predicting future values. The output unit gives a linear combination of the outputs of all hidden units:

![image](d2d_images/image061.png)

whereψj is the activation function. The synaptic weightsωji andωj are adjusted during the learning process and can be positive, negative or zero.

To design the neural network we have to see how many hidden neurons we should use. Generally the number of hidden neurons is proportional to the sample size used for training the network.  The behaviour of the network is evaluated according to the error function:

![image](d2d_images/image059.png)

where p is the number of samples used in training.

It has recently been shown that, for p training samples, a perceptron with a single hidden layer of p-1 neurons can implement such a training set. That is, p-1 neurons are sufficient, but generally we will need fewer.

An alternative model to the perceptron is the neural network that uses radial basis functions, i.e. its output is of the form:

![image](d2d_images/image219.png)

where![image](d2d_images/image632.png)are the centres of the radial basis functions. A widely used radial basis function is the Gaussian function:

![image](d2d_images/image303.png)

It has been shown experimentally that neural networks with radial basis functions approximate a wide class of multidimensional functions. In addition, they have the advantage over the perceptron in that their training times are much shorter.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.8  ​​​​​​​ANALYSIS OF MAIN COMPONENTS WITH neural networks

![image](d2d_images/chapter_title_below.png)

We know that obtaining the principal components will allow us to reduce the dimensionality by losing little information and to detect the characteristic features of the dataset, which can be useful in classification and recognition problems.

Consider a network of artificial neurons whose output is given by![image](d2d_images/image328.png), where x \= (x1 , x2 ,...,xn )' the input vector to the processing unit (neuron) and  ![image](d2d_images/image498.png)the vector of synaptic weights.

The learning rule we are going to consider was proposed by Hebb (Hebbian learning). Hebb's postulate states that changes in synaptic weights (changes in synaptic efficacy) are proportional to the product of the presynaptic (input) signals, x, and the postsynaptic signal, y. That is, ![image](d2d_images/image179.png)or, in vector form![image](d2d_images/image012.png)the learning rate.

Suppose now that the input vector x is a random vector with density function f(x). At each time instant k, k=1, 2,... we present the network with an input vector x which is a value of the random vector with density function f(x), and we update the synaptic weights according to Hebb's rule mentioned above. Therefore, we can consider that![image](d2d_images/image191.png)is a random vector whose expected value is:

![image](d2d_images/image221.png)

and if we assume that x andω are statistically independent, the above expression is:

![image](d2d_images/image143.png)

Furthermore, we can assume, without loss of generality, that the random vector x has zero mean in all its components and so the matrix![image](d2d_images/image124.png)is the covariance matrix.

The network could reach equilibrium (stabilise) if![image](d2d_images/image644.png).  This leads to the fact that Cω = 0 and soω^(\*) = 0 is the only equilibrium state. The matrix C (real and symmetric) is positive semidefinite and so its eigenvalues ![image](d2d_images/image224.png)are positive or zero and it has eigenvectors orthogonal to^i , i \= 1, 2,...,n, which satisfy:

![image](d2d_images/image132.png)

It can be proved that the solutionω^(\*) = 0 is not stable and therefore the above equation of the expected value is unstable and so this rule leads to an unbounded growth of the vector of synaptic weightsω (infinite magnitude with a direction parallel to the eigenvector having the largest associated eigenvalue). To solve this problem, some kind of normalisation or saturation must be incorporated in the learning rule that updates the synaptic weights. This leads to the following learning rule:

![image](d2d_images/image103.png)

An alternative (Oja's rule) proposed is to add a term that subtracts a quantity to provide a and² :

![image](d2d_images/image531.png)

Oja's rule converges on average to a stateω^(\*) that maximises the mean value of y² , E(y² ), subject to the condition![image](d2d_images/image262.png). Therefore,ω^(\*) is the principal eigenvector (that which corresponds to the largest eigenvalue) of the covariance matrix.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.9  ​​​​​​​CLUSTERING USING NEURAL NETWORKS

![image](d2d_images/chapter_title_below.png)

Clustering techniques are concerned with partitioning a given set of data into several groups or categories. They have applications in many fields such as medicine, biology, zoology and, above all, information technology. Most of the techniques that have been developed can be divided into three main groups: hierarchical, cost or distortion minimisation and graph theory. However, when dealing with large datasets, only cost minimisation techniques are suitable, for reasons of computational complexity.

Given a set of data![image](d2d_images/image543.png)corresponding to n values of a random vector X whose distribution function Fx is unknown, but is known to be a mixture of m distribution functions, the problem is to form m groups or categories with the data according to a certain distance function or distortion measure, which in our case is going to be the squared Euclidean distance (the squared Euclidean distance).

Each group will be represented by its centroid, i.e. its mean vector. Therefore, the aim is to determine m centroids, ![image](d2d_images/image101.png), in such a way that the distortion between each data and its centroid is minimal, i.e. minimised:

![image](d2d_images/image576.png)

The solution of this problem leads to a partition of the data set into m classes, categories or regions, Ci , i \= 1, 2,...,m, defined as follows:

![image](d2d_images/image587.png)

Note that, for a given partition, the representation vectors ωi , i \= 1, 2,...,m, also called prototypes or reference vectors, which make the distortion minimal are the centroids of the group, i.e:

![Imagen que contiene objeto, reloj Descripción generada automáticamente](d2d_images/image106.png)

where ni is the number of elements of group Ci .

The number of different partitions of a set of N elements into K groups is:

![image](d2d_images/image643.png)

Many algorithms have been proposed to solve this problem, such as the K-means algorithm of Moqueen (1967). However, these algorithms lead to partial solutions, i.e., local minima, which need not be global minima (optimal solution). Thus, the difficulty of this problem lies in the fact that the objective function has many local minima, which are not necessarily global minima (optimal solution).

To carry out this type of grouping we will use competitive neural networks with unsupervised learning, which allow us to form groups or categories with the input data. Each input will be assigned to the class specified by the activated output unit. In this type of learning, the neurons compete with each other to see which one is activated; only one of them is activated, so it is often called winner-take-all learning. Here the network, on its own (unsupervised), groups the data into categories and gives us the prototypes for each category.

This new learning paradigm was introduced by Rumelhart and Zipser (1985), under the name of competitive learning. The network consists of a layer of m neurons or processing units that are connected to the input signals or patterns and these connections have associated synaptic weights that will represent the prototype patterns. Each neuron has only two possible output values: 0 (not activated) or 1 (activated) and only one neuron is activated for each input pattern, the one that receives a higher synaptic potential (winning neuron).

If neuron i receives the input signal ![image](d2d_images/image528.png)and has the synaptic weights ωi = (ωi1 , ωi2 ,..., ωin )', its synaptic potential is given by the expression:

![Texto Descripción generada automáticamente](d2d_images/image168.png)

Note that as we have defined the synaptic potential it follows that:

![image](d2d_images/image195.png)

where d is the Euclidean distance. Therefore, the neuron that is activated is the one whose vector of synaptic weights is closest to the input pattern x, i.e. is the most similar.

The aim is to ensure that the vector of synaptic weights of each neuron becomes the centroid (prototype) of the data set it represents, i.e. for which that neuron is the winner. This is achieved with the competitive learning rule.

To deduce the competitive learning rule we will consider a set of p input patterns, which we will represent by xi = (xi1 , xi2 ,..., xin )', i=1, 2,..., p, and which we will call the training set of the network, since from it we will obtain the value of the synaptic weights of each neuron in the network. If for the input x the neuron is the winner, it is because its vector of weights is the most similar, and so this input is assigned to class r.

This means that the vector of synaptic weights ωr is the one that represents the input pattern x, and since we want this representation to be as good as possible, ωr must be as close as possible to all the patterns of the group it represents. To do so, we must update (modify) the vector of synaptic weights ωr of the winning neuron r by bringing it closer to the input pattern s. That is, if in stage k+1 we have introduced the input pattern x and neuron r is the winner, then we modify its synaptic weights according to the expression:

![image](d2d_images/image461.png)

where ηr is the learning rate of neuron r.

The other neurons do not change their synaptic weights. This is the standard rule of competitive learning. Note that it is a linear combination between the input vector and the vector of synaptic weights, and the smaller the value of the learning rate, the smaller the modification of the synaptic weights. The learning rate of each neuron must be a decreasing function with respect to the stage number, so that after a suitable number of stages the network stabilises and stops learning. During the learning process, an input pattern is introduced at each iteration and the synaptic weights are updated, so that the learning process ends after the data set has been introduced several times.

With this network, neurons learn individually to specialise on sets of patterns and are thus feature detectors. Each vector of synaptic weights represents the prototype of the class or group that defines the corresponding neuron.

This algorithm is similar to MacQueen's K-means algorithm, which consists of assigning each pattern to the nearest centroid and redetermining the centroids of the new groups formed.  Ahalt et al. (1990) have shown the convenience of using competitive learning to solve our problem as it leads to optimal or near-optimal solutions.

Ueda and Nakano (1994) have proposed a new competitive learning with a selection mechanism based on the equidistortion principle that allows the network to escape local minima and Uchiyama and Arbib (1994) have shown the relationship between our clustering problem and vector quantization, and present a competitive learning algorithm that generates units where the input data density is high, applying it to colour image segmentation.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.10  ​​SPSS AND neural networks

![image](d2d_images/chapter_title_below.png)

Neural networks are the tool of choice for many predictive data mining applications because of their power, flexibility and ease of use. Predictive neural networks are especially useful in applications where the underlying process is complex; for example:

*   Anticipate consumer demand to rationalise production and delivery costs.

*   Predict the probability of response to direct mail marketing to determine to which households on a mailing list an offer should be sent.

*   To score an applicant in order to determine the risk involved in granting credit.

*   Detect fraudulent transactions in an insurance claims database.

Neural networks used in predictive applications, such as multilayer perceptron (MLP) and radial basis function (RBF) networks, are monitored in the sense that the results predicted by the model can be compared with the known values of the target variables. The neural networks option allows you to fit the MLP and RBF networks and save the resulting models for scoring.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.10.1  ​​Multilayer Perceptron (MLP)

![image](d2d_images/chapter_title_below.png)

The IBM SPSS Multi-Layer Perceptron (MLP) procedure generates a predictive model for one or more dependent (target) variables based on the values of the predictor variables. Two situations in which the MLP procedure is used are described below:

A bank loan officer wants to be able to identify characteristics that are indicative of individuals who may cause credit delinquency and use these characteristics to identify positive and negative credit risks. Using a sample of past customers, he can train a multilayer perceptron, validate the analysis using a reserved sample of past customers, and then use the network to classify potential customers according to the credit risks they present. A hospital system is interested in tracking the costs and lengths of inpatient stays for myocardial infarction treatment. Obtaining accurate estimates of these measures allows the administration to properly manage the available beds as patients are treated. Using the treatment records of a sample of patients treated for myocardial infarction, the administrator can train a network that predicts both cost and length of stay.

In our case we consider an example similar to the first one presented here. A bank decision-maker has to identify to which customers he can grant a loan with sufficient guarantee of repayment. He has a database with a history of customers in which he knows whether or not the customers have repaid the loan (CREDIT\_V), the professional category of the customers (CAT\_PROF), their monthly salary (PAY\_MONTH), their age (AGE) and whether or not they have credit cards (AMEX). With this information, it must build a predictive model that predicts the category of the dependent variable (does or does not repay the credit in the variable CREDIT\_V) in which it must classify any new customer who applies for credit, knowing the values of its independent variables (CAT\_PROF, PAYMENT\_MONTH and AMEX).

We will use a multilayer Perceptron neural network. To do this, after loading the credits.sav file containing the information on the variables mentioned above into memory, we choose from the SPSS menus Analyse → Neural Networks → Multilayer Perceptron (Figure 6-4).

![image](d2d_images/image060.png)

Figure 6-4

The Multilayer Perceptron screen is obtained, in whose Variables tab (Figure 6-5) we define the dependent variable(s) of the model, the categorical independent variables (Factors) and the metric independent variables (Covariates). In the Partitions tab (Figure 6-6) we define the percentage of cases in the file that we will dedicate to network training, testing and reservation. In the Architecture tab (Figure 6-7) we define the architecture of the neural network by allowing automatic selection of the architecture (recommended option) or by customising the number of hidden layers of the network, the number of units, the activation function, the activation function of the output layer and the scaling of the scale dependent variables. In the Training tab (Figure 6-8) the training type, the optimisation algorithm and the training options are defined. The Results tab (Figure 6-9) defines the results to be obtained in the neural network model adjustment, both for the structure of the network, as well as for its performance and summary of case processing and importance of the independent variables. In the Save tab (Figure 6-10) we define the variables to be saved in the data file (predicted category of the dependent variables and their probabilities). In the Export tab (Figure 6-11) we can decide to export the synaptic weights to an XML file. In the Options tab (Figure 6-12) we can define the treatment of missing values, the stopping rules, the training time of the network, the data used to calculate the prediction error, the number of cases to store in memory and other values to adjust the network.

![image](d2d_images/image602.png)

Figure 6-5

![image](d2d_images/image601.png)

Figure 6-6

![image](d2d_images/image516.png)

Figure 6-7

![image](d2d_images/image504.png)

Figure 6-8

![image](d2d_images/image432.png)

Figure 6-9

![image](d2d_images/image313.png)

Figure 6-10

![image](d2d_images/image274.png)

Figure 6-11

![image](d2d_images/image518.png)

Figure 6-12

Clicking OK produces the output. A summary of cases and network information is shown in Figure 6-13.

![image](d2d_images/image042.png)

Figure 6-13

Figure 6-14 shows the network structure. Figure 6-15 shows a summary of the fitted network model and its parameter estimation. Figure 6-16 shows the confusion matrix which indicates more than 80% accuracy in predicting the known data. Figure 6-17 shows the ROC curve which is close enough to the upper triangle to indicate a good fit corroborated by an area of 87.2% under the curve. Figures 6-18 and 6-19 show the gain and elevation curves very close to the theoretical values. Figure 6-20 shows the importance of the predictors in the ranking, noting that the most influential variables are professional category and salary.

The data set (Figure 6-21) shows that its last three columns are the variables relating to the category of the dependent variable into which each observation has been classified and to the probabilities of each observation belonging to each of the categories of the dependent variable. To predict a future observation with the neural network, it is sufficient to incorporate the values of its independent variables as an additional row in the data set. The dependent variable can be assigned any value. The process is run again and the prediction of the membership category for the new observation is obtained.

![image](d2d_images/image611.png)

Figure 6-14

![image](d2d_images/image655.png)

Figure 6-15

![image](d2d_images/image202.png)

Figure 6-16

![image](d2d_images/image558.png)

Figure 6-17

![image](d2d_images/image273.png)

Figure 6-18

![image](d2d_images/image592.png)

Figure 6-19

![image](d2d_images/image093.png)

Figure 6-20

![image](d2d_images/image538.png)

Figure 6-21

In the following, the specification of the different sections of the network output is expanded.

Network structure. Displays summary information about the neural network.

\- Description. Displays information about the neural network, including the dependent variables, the number of input and output units, the number of hidden units and layers, and the activation functions.

\- Diagram. Displays the network diagram as an editable graph. Note that as the number of covariates and factor levels increases, the diagram becomes more difficult to interpret.

\- Synaptic weights. Samples the coefficient estimates that show the relationship between the units of a given layer with the units of the next layer. Synaptic weights are based on the training sample even if the active data set is split into training, test and reserved data. Note that the number of synaptic weights can be quite high, and these weights are generally not used to interpret network results.

Network performance. Shows the results used to determine if the model is "good". Note: The graphs in this group are based on the training and test samples combined, or only the training sample if there is no test sample.

\- Model summary. Displays a summary of the neural network results by partition and overall, including the error, the relative error or percentage of incorrect predictions, the stopping rule used to stop training and the training time.

The error is the error of quadratic sums when the hyperbolic tangent, identity or sigmoid activation function is applied to the output layer. This is the cross-entropy error when the softmax activation function is applied to the output layer.

The percentages or relative errors of incorrect forecasts are shown depending on the measurement levels of the dependent variable. If any dependent variable has a scale level of measurement, the overall average relative error (relative to the model mean) is shown. If all dependent variables are categorical, the average percentage of incorrect forecasts is shown. Relative errors or percentage of incorrect forecasts are also shown for individual dependent variables.

\- Ranking results. Displays a classification table for each categorical dependent variable by partition and overall. Each table provides the number of correctly and incorrectly classified cases for each dependent variable category. The percentage of total cases that were correctly classified is also reported.

\- COR curve. Displays a Receiver Operating Characteristic (COR) curve for each categorical dependent variable. It also shows a table providing the area under each curve. For a given dependent variable, the COR chart shows a curve for each category. If the dependent variable has two categories, each curve treats the category in question as the positive state vis-à-vis the other category. If the dependent variable has more than two categories, each curve treats the category in question as the positive state against the aggregation of the other categories.

\- Cumulative earnings graph. Displays a cumulative earnings graph for each categorical dependent variable. The presentation of a curve for each category of dependent variable is the same as for the COR curves.

\- Elevation plot. Displays an elevation graph for each categorical dependent variable. The presentation of a curve for each category of dependent variable is the same as for the COR curves.

\- Graph of predicted by observed. Displays a plot of predicted values per observed for each dependent variable. For categorical dependent variables, clustered box plots of predicted pseudoprobabilities are shown for each response category, with the observed response category as the cluster variable. For scale dependent variables, a scatter plot is shown.

\- Graph of residuals by predicted. Displays a plot of residuals by predicted values for each scale dependent variable. There should be no visible patterns between residuals and predicted values. This graph is only generated for scale dependent variables.

Case processing summary. Displays the case processing summary table, which summarises the number of cases included and excluded in the analysis, in total and by training, test and reserved samples.

Analysis of the importance of the independent variable. Performs a susceptibility analysis, which calculates the importance of each predictor in determining the neural network. The analysis is based on the combined training and test samples, or only the training sample if there is no test sample. This creates a table and graph showing the importance and normalised importance of each predictor. Note that the susceptibility analysis involves a very extensive calculation process that can take a long time if the number of predictors or cases is large.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.10.2  ​​Radial Basis Function (RBF)

![image](d2d_images/chapter_title_below.png)

The IBM SPSS Radial Basis Function (RBF) procedure generates a predictive model for one or more dependent (target) variables based on the values of the predictor variables. Two situations in which the MLP procedure is used are described below:

We consider an example of a bank decision-maker who has to identify to which customers he can grant a loan with sufficient guarantee of repayment. He has a database with a history of customers in which he knows whether or not the customers have repaid the loan (CREDIT\_V), the professional category of the customers (CAT\_PROF), their monthly salary (PAY\_MONTH), their age (AGE) and whether or not they have credit cards (AMEX). With this information, it must build a predictive model that predicts the category of the dependent variable (does or does not repay the credit in the variable CREDIT\_V) in which it must classify any new customer who applies for credit, knowing the values of its independent variables (CAT\_PROF, PAY\_MONTH, AGE and AMEX).

We will use a neural network of the Radial basis function type. To do this, after loading the credits.sav file containing the information on the variables mentioned above into memory, we choose from the SPSS menus Analyse → Neural Networks → Radial Basis Function (Figure 6-22).

The Radial Basis Function  screen is obtained, in whose Variables tab (Figure 6-23) we define the dependent variable(s) of the model, the categorical independent variables (Factors) and the metric independent variables (Covariates). In the Partitions tab (Figure 6-24) we define the percentage of cases in the file that we will dedicate to network training, testing and reservation. In the Architecture tab (Figure 6-25) we define the architecture of the neural network by allowing automatic selection of the architecture (recommended option) or by customising the number of hidden layers of the network, the number of units, the activation function, the activation function of the output layer and the scaling of the scale dependent variables. The Results tab (Figure 6-26) defines the results to be obtained in the neural network model fitting, both for the structure of the network, as well as for its performance and summary of case processing and importance of the independent variables. In the Save tab (Figure 6-27) we define the variables to be saved in the data file (predicted category of the dependent variables and their probabilities). In the Export tab (Figure 6-28) we can decide to export the synaptic weights to an XML file. In the Options tab (Figure 6-29) we can define the treatment of missing values, the stopping rules, the training time of the network, the data used to calculate the prediction error, the number of cases to store in memory and other values to adjust the network.

Clicking OK produces the output. Figure 6-30 shows a summary of cases and information about the network. Figure 6-31 shows the network structure. Figure 6-32 shows a summary of the network model fitted to the confusion matrix indicating more than 90% accuracy in predicting the known data. Figure 6-33 shows the ROC curve which is close enough to the upper triangle to indicate a good fit corroborated by a 94.5% area under the curve. Figures 6-34 and 6-35 show the gain and elevation curves very close to the theoretical values. Figure 6-36 shows the importance of the predictors in the ranking, noting that the most influential variables are age, salary and professional category.

![image](d2d_images/image029.png)

Figure 6-22

![image](d2d_images/image403.png)

Figure 6-23

![image](d2d_images/image257.png)

Figure 6-24

![image](d2d_images/image614.png)

Figure 6-25

![image](d2d_images/image588.png)

Figure 6-26

![image](d2d_images/image317.png)

Figure 6-27

![image](d2d_images/image549.png)

Figure 6-28

![image](d2d_images/image153.png)

Figure 6-29

![image](d2d_images/image171.png)

Figure 6-30

![image](d2d_images/image126.png)

Figure 6-31

![image](d2d_images/image535.png)

Figure 6-32

![image](d2d_images/image146.png)

Figure 6-33

![image](d2d_images/image043.png)

Figure 6-34

![image](d2d_images/image520.png)

Figure 6-35

![image](d2d_images/image295.png)

Figure 6-36

If the data set is displayed (Figure 6-37), it can be seen that its last three columns are the variables relating to the category of the dependent variable into which each observation has been classified and to the probabilities of each observation belonging to each of the categories of the dependent variable. To predict a future observation with the neural network, it is sufficient to incorporate the values of its independent variables as an additional row in the data set. The dependent variable can be assigned any value. The process is run again and the prediction of the membership category for the new observation is obtained.

Comparing the problem fit with a multilayer Perceptron and a Radial Basis Function neural network, we see that the latter is more accurate because it has a better COR curve, a confusion matrix with a higher hit rate and higher probabilities of individuals belonging to the classes of the dependent variable. Therefore, the Radial Basis Function neural network predicts more accurately than the Multi-Layer Perceptron neural network. However, the category of the dependent variable predicted for each individual is the same for virtually all individuals.

![image](d2d_images/image237.png)

Figure 6-37

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.11  ​​​​NEURAL NETWORKS IS THROUGH R

![image](d2d_images/chapter_title_below.png)

The R libraries neuralnet and nnet have functions suitable for working with neural networks in R-.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.11.1  ​​neuralnet library

![image](d2d_images/chapter_title_below.png)

The neuralnet command of the neuralnet library has the following simplified syntax:

neuralnet(formula, data=dataset, hidden = c(m,n),...)

The vector c(m,n) specifies the number of hidden neurons in each layer.

As an example, we are going to calculate the probabilities that applicants for bank loans have of successfully repaying the loan. To do this, we use a file named credits.sav that contains a dichotomous variable credit\_v that collects the success or failure in the repayment of a credit in the history of clients (1=successful repayment, 0=failure to repay or non-repayment). This variable will be the dependent variable of the network model. As independent variables, the customer's professional category, monthly salary, age and whether or not the customer has an American Express card will be used.

We start by loading the file, separating its variables and obtaining basic statistics on them.

![Imagen que contiene Interfaz de usuario gráfica Descripción generada automáticamente](d2d_images/image185.png)

![Una captura de pantalla de un celular Descripción generada automáticamente con confianza media](d2d_images/image122.png)

Next, we install and load the neuralnet library.

![image](d2d_images/image129.png)

Now with the neuralnet function we create the network model with two hidden layers of 2 and 3 nodes respectively and represent it (the estimated synaptic weights are shown in graph 6-38).

![image](d2d_images/image169.png)

![Gráfico, Gráfico radial Descripción generada automáticamente](d2d_images/image208.png)

Figure 6-38

We then calculate the predicted probabilities and plot the density function (Figure 6-39).

![Texto Descripción generada automáticamente](d2d_images/image077.png)

![Gráfico, Diagrama Descripción generada automáticamente](d2d_images/image533.png)

Figure 6-39

We obtain a bimodal density that indicates that for both low and high probabilities of credit evolution there is a high density of clients. For medium probabilities the client   density is low.

We then calculate the predicted classes.

![image](d2d_images/image285.png)

To carry out the diagnosis, we obtain the confusion matrix.

![Imagen que contiene Interfaz de usuario gráfica Descripción generada automáticamente](d2d_images/image047.png)

Out of the 323 customers 32 are misclassified (2 out of the 168 who do not return the loan correctly and 30 out of those who return the loan correctly). Therefore   the overall probability of hits is (323-32)/323=90%, which is a very high value.

Among those who do not repay the loan, they are classified as good (168-2)/168=98.8%. Among those who repay the loan are classified as good (155-30)/155=80.6%.

Let us now plot the ROC curve (Figure 6-40).

![image](d2d_images/image094.png)

![Gráfico Descripción generada automáticamente](d2d_images/image703.png)

Figure 6-40

As the area under the ROC curve is 0.963 (very close to 1) it is concluded that the neural network model is very good. Furthermore, it outperforms the decision tree model of the previous chapter which had a lower area under the ROC curve (0.877). We will get a lot of numerical information about the neural network if we use:

![image](d2d_images/image394.png)

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.11.2  ​​nnet bookshop

![image](d2d_images/chapter_title_below.png)

To work with the neural network, the nnet  function of the nnet library   can also be used. Its simplified syntax is as follows:

nnet(formula, data, weights, size=n ...,)

The argument size=n indicates the number of nodes in the hidden layer.

We will build the network in the example above with 8 nodes in the hidden layer.

![Texto Descripción generada automáticamente](d2d_images/image117.png)

We will then calculate the probability of repayment for each customer and the class to which he belongs (successful or unsuccessful repayment).

![image](d2d_images/image291.png)

If we plot the probability density (Figure 6-41) we see that it is bimodal around zero and 1.

![image](d2d_images/image034.png)![Gráfico, Gráfico de líneas Descripción generada automáticamente](d2d_images/image467.png)

Figure 6-41

We will now perform the diagnosis of the model through the confusion matrix and the ROC curve.

![Imagen que contiene Texto Descripción generada automáticamente](d2d_images/image198.png)

It can be seen that the overall percentage of successes is (323-32)/323=90%, which is a similar value to that obtained previously with the neuralnet command.

Let us now plot the ROC curve (Figure 6-42).

![Interfaz de usuario gráfica Descripción generada automáticamente con confianza media](d2d_images/image231.png)

![Gráfico Descripción generada automáticamente](d2d_images/image032.png)

Figure 6-42

We see that the area under the ROC curve also coincides with the nnet and neuralnet functions. The accuracy of both networks is similar.

 
| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 6.12  ​​R AND TIME SERIES USING NEURAL NETWORKS

![image](d2d_images/chapter_title_below.png)

R has the nnetar command in the forecast library that allows predicting time series through neural networks.

Let us consider the monthly series X of the seasonal.sav file starting in January 1968 and ending in October 1981. The aim is to calculate a year of predictions using neural networks.

We start by reading the series and giving it the structure of a time series.

![image](d2d_images/image027.png)

The appropriate neural network model to obtain the pedictions is then estimated.

![Texto, Carta Descripción generada automáticamente](d2d_images/image579.png)

Next we perform the model diagnosis by performing the residual analysis and calculating estimation errors (Figure 6-43). Regarding the residual analysis, some deficiencies are observed in the residual randomness as some terms of the residual autocorrelation function are outside the confidence band. The residual normality is well fulfilled as the residual histogram fits well to the Gaussian bell.

![image](d2d_images/image033.png)

![Gráfico Descripción generada automáticamente](d2d_images/image186.png)

Figure 6-43

We now calculate the estimation errors.

![image](d2d_images/image352.png)

Exercise 6-1. Consider the monthly sales series of a company with name sales from the file test.sav starting in January 1988 and ending in April 1996. Calculate a year's worth of predictions using automatic modelling and neural network modelling. Compare results.

We start by reading the series and giving it the structure of a time series.

![image](d2d_images/image335.png)

We then carry out the identification and estimation of the automatic ARIMA model.

![Texto, Carta Descripción generada automáticamente](d2d_images/image175.png)

We see that an ARIMA(1,1,1)  model is identified as optimal. R has atomically detected the non-stationarity of the sales series. We then carry out the diagnosis by analysing the individual significance of the estimated parameters and performing the residuals analysis.

![Texto Descripción generada automáticamente](d2d_images/image326.png)All parameters are significant because their p-values are very small.

We now perform the residual diagnosis (Figure 6-44).

![image](d2d_images/image218.png)

![Texto Descripción generada automáticamente](d2d_images/image591.png)

![Interfaz de usuario gráfica, Gráfico Descripción generada automáticamente](d2d_images/image636.png)

Figure 6-44

We see that the residuals are random (p-value of the Ljung-Box statistic=0.5846 which is greater than 0.05) and normal (histogram well fitted to the Gaussian bell). Next we see that the estimation errors are small.

![image](d2d_images/image177.png)

We now calculate the predictions and their confidence intervals.

![Texto, Aplicación Descripción generada automáticamente](d2d_images/image653.png)

![Texto Descripción generada automáticamente](d2d_images/image194.png)

The predictions are plotted below (Figure 6-45).

![image](d2d_images/image534.png)

![Gráfico, Gráfico de líneas, Histograma Descripción generada automáticamente](d2d_images/image473.png)

Figure 6-45

The optimal automatic model is then identified, estimated and diagnosed taking into account parallel processing.

![Imagen que contiene Texto Descripción generada automáticamente](d2d_images/image141.png)

![Texto Descripción generada automáticamente](d2d_images/image242.png)

It is observed that, in this case, R detects the same automatic ARIMA model with and without parallel processing.

We are now going to obtain sales  predictions through neural network models.

![Texto, Carta Descripción generada automáticamente](d2d_images/image673.png)

We will now perform the residual diagnosis (Figure 6-46).

![image](d2d_images/image685.png)

![Gráfico, Histograma Descripción generada automáticamente](d2d_images/image446.png)

Figure 6-46

There are terms in the residual ACF that fall outside the confidence band. Therefore the residual may have non-randomness problems.

We then calculate and plot the predictions (Figure 6-47).

![Texto Descripción generada automáticamente](d2d_images/image058.png)

![Gráfico, Histograma Descripción generada automáticamente](d2d_images/image407.png)

Figure 6-47

The predictions are too increasing and less logical than in the case of the automatic model. For this time series of sales it is clear that the optimal model is the one offered by the automatic method with the auto.arima command. We are left with the ARIMA(1,1,1) model and its predictions.