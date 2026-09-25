![](images/9780262358019.jpg)

![Cover Image](images/9780262358019.jpg)

 

Probabilistic Machine Learning for Civil Engineers

 

Probabilistic Machine Learning for Civil Engineers

James-A. Goulet

The MIT Press

Cambridge, Massachusetts

London, England

 

© 2020 Massachusetts Institute of Technology

This work is subject to a Creative Commons CC-BY-NC-ND license.

![art](images/Art_P1.jpg)

Subject to such license, all rights are reserved.

This book was set in ![art](images/Art_P2.jpg)by the author.

Library of Congress Cataloging-in-Publication Data

Names: Goulet, James-A., author.

Title: Probabilistic machine learning for civil engineers / James-A. Goulet.

Description: Cambridge, Massachusetts : The MIT Press, 2020. *|* Includes bibliographical references and index.

Identifiers: LCCN 2019027152 *|* ISBN 9780262358019

Subjects: LCSH: Machine learning. *|* Probabilities.

Classification: LCC Q325.5 .G68 2020 | DDC 006.3/1—dc23

LC record available at [https://lccn.loc.gov/2019027152](https://lccn.loc.gov/2019027152)

d\_r0

 

*Contents*

[**Copyright**](#copyright.xhtml)

[**List of Figures**](#preface001.xhtml)

[**List of Algorithms**](#preface002.xhtml)

[**Acknowledgments**](#acknowledgments.xhtml)

[**Nomenclature & Abbreviations**](#preface003.xhtml)

[**1   Introduction**](#introduction001.xhtml)

[**I    Background**](#part001.xhtml)

[**2   Linear Algebra**](#chapter001.xhtml)

[2.1    Notation](#chapter001.xhtml#h1-1)

[2.2    Operations](#chapter001.xhtml#h1-2)

[2.3    Norms](#chapter001.xhtml#h1-3)

[2.4    Transformations](#chapter001.xhtml#h1-4)

[2.4.1    Linear Transformations](#chapter001.xhtml#h2-2)

[2.4.2    Eigen Decomposition](#chapter001.xhtml#h2-3)

[**3   Probability Theory**](#chapter002.xhtml)

[3.1    Set Theory](#chapter002.xhtml#h1-5)

[3.2    Probability of Events](#chapter002.xhtml#h1-6)

[3.3    Random Variables](#chapter002.xhtml#h1-7)

[3.3.1    Discrete Random Variables](#chapter002.xhtml#h2-4)

[3.3.2    Continuous Random Variables](#chapter002.xhtml#h2-5)

[3.3.3    Conditional Probabilities](#chapter002.xhtml#h2-6)

[3.3.4    Multivariate Random Variables](#chapter002.xhtml#h2-7)

[3.3.5    Moments and Expectation](#chapter002.xhtml#h2-8)

[3.4    Functions of Random Variables](#chapter002.xhtml#h1-8)

[3.4.1    Linear Functions](#chapter002.xhtml#h2-9)

[3.4.2    Linearization of Nonlinear Functions](#chapter002.xhtml#h2-10)

[**4   Probability Distributions**](#chapter003.xhtml)

 

[4.1    Normal Distribution](#chapter003.xhtml#h1-9)

[4.1.1    Univariate Normal](#chapter003.xhtml#h2-11)

[4.1.2    Multivariate Normal](#chapter003.xhtml#h2-12)

[4.1.3    Properties](#chapter003.xhtml#h2-13)

[4.1.4    Example: Conditional Distributions](#chapter003.xhtml#h2-14)

[4.1.5    Example: Sum of Normal Random Variables](#chapter003.xhtml#h2-15)

[4.2    Log-Normal Distribution](#chapter003.xhtml#h1-10)

[4.2.1    Univariate Log-Normal](#chapter003.xhtml#h2-16)

[4.2.2    Multivariate Log-Normal](#chapter003.xhtml#h2-17)

[4.2.3    Properties](#chapter003.xhtml#h2-18)

[4.3    Beta Distribution](#chapter003.xhtml#h1-11)

[**5   Convex Optimization**](#chapter004.xhtml)

[5.1    Gradient Ascent](#chapter004.xhtml#h1-12)

[5.2    Newton-Raphson](#chapter004.xhtml#h1-13)

[5.3    Coordinate Ascent](#chapter004.xhtml#h1-14)

[5.4    Numerical Derivatives](#chapter004.xhtml#h1-15)

[5.5    Parameter-Space Transformation](#chapter004.xhtml#h1-16)

[**II    Bayesian Estimation**](#part002.xhtml)

[**6   Learning from Data**](#chapter005.xhtml)

[6.1    Bayes](#chapter005.xhtml#h1-17)

[6.2    Discrete State Variables](#chapter005.xhtml#h1-18)

[6.2.1    Example: Disease Screening](#chapter005.xhtml#h2-19)

[6.2.2    Example: Fire Alarm](#chapter005.xhtml#h2-20)

[6.2.3    Example: Post-Earthquake Damage Assessment](#chapter005.xhtml#h2-21)

[6.3    Continuous State Variables](#chapter005.xhtml#h1-19)

[6.3.1    Likelihood: *f*(D|**x**)](#chapter005.xhtml#h2-22)

[6.3.2    Evidence: *f*(D)](#chapter005.xhtml#h2-23)

[6.3.3    Posterior: *f*(*x*|D)](#chapter005.xhtml#h2-24)

[6.3.4    Number of Observations and Identifiability](#chapter005.xhtml#h2-25)

[6.4    Parameter Estimation](#chapter005.xhtml#h1-20)

[6.4.1    Prior: *f*(*θ*)](#chapter005.xhtml#h2-26)

[6.4.2    Likelihood: *f*(D|*θ*)](#chapter005.xhtml#h2-27)

[6.4.3    Posterior PDF: *f*(*θ*|D)](#chapter005.xhtml#h2-28)

[6.5    Monte Carlo](#chapter005.xhtml#h1-21)

[6.5.1    Monte Carlo Integration](#chapter005.xhtml#h2-29)

[6.5.2    Monte Carlo Sampling: Continuous State Variables](#chapter005.xhtml#h2-30)

[6.5.3    Monte Carlo Sampling: Parameter Estimation](#chapter005.xhtml#h2-31)

[6.6    Conjugate Priors](#chapter005.xhtml#h1-22)

[6.7    Approximating the Posterior](#chapter005.xhtml#h1-23)

[6.7.1    Maximum Likelihood and Posterior Estimates](#chapter005.xhtml#h2-32)

 

[6.7.2    Laplace Approximation](#chapter005.xhtml#h2-33)

[6.8    Model Selection](#chapter005.xhtml#h1-24)

[**7   Markov Chain Monte Carlo**](#chapter006.xhtml)

[7.1    Metropolis](#chapter006.xhtml#h1-25)

[7.2    Metropolis-Hastings](#chapter006.xhtml#h1-26)

[7.3    Convergence Checks](#chapter006.xhtml#h1-27)

[7.3.1    Burn-In Phase](#chapter006.xhtml#h2-34)

[7.3.2    Monitoring Convergence](#chapter006.xhtml#h2-35)

[7.3.3    Estimated Potential Scale Reduction](#chapter006.xhtml#h2-36)

[7.3.4    Acceptance Rate](#chapter006.xhtml#h2-37)

[7.3.5    Proposal Tuning](#chapter006.xhtml#h2-38)

[7.4    Space Transformation](#chapter006.xhtml#h1-28)

[7.5    Computing with MCMC Samples](#chapter006.xhtml#h1-29)

[**III    Supervised Learning**](#part003.xhtml)

[**8   Regression**](#chapter007.xhtml)

[8.1    Linear Regression](#chapter007.xhtml#h1-30)

[8.1.1    Mathematical Formulation](#chapter007.xhtml#h2-39)

[8.1.2    Overfitting and Cross-Validation](#chapter007.xhtml#h2-40)

[8.1.3    Mathematical Formulation >1-D](#chapter007.xhtml#h2-41)

[8.1.4    Limitations](#chapter007.xhtml#h2-42)

[8.2    Gaussian Process Regression](#chapter007.xhtml#h1-31)

[8.2.1    Updating a GP Using Exact Observations](#chapter007.xhtml#h2-43)

[8.2.2    Updating a GP Using Imperfect Observations](#chapter007.xhtml#h2-44)

[8.2.3    Multiple Covariates](#chapter007.xhtml#h2-45)

[8.2.4    Parameter Estimation](#chapter007.xhtml#h2-46)

[8.2.5    Example: Soil Contamination Characterization](#chapter007.xhtml#h2-47)

[8.2.6    Example: Metamodel](#chapter007.xhtml#h2-48)

[8.2.7    Advanced Considerations](#chapter007.xhtml#h2-49)

[8.3    Neural Networks](#chapter007.xhtml#h1-32)

[8.3.1    Feedforward Neural Networks](#chapter007.xhtml#h2-50)

[8.3.2    Parameter Estimation and Backpropagation](#chapter007.xhtml#h2-51)

[8.3.3    Regularization](#chapter007.xhtml#h2-52)

[8.3.4    Example: Metamodel](#chapter007.xhtml#h2-53)

[**9   Classification**](#chapter008.xhtml)

[9.1    Generative Classifiers](#chapter008.xhtml#h1-33)

[9.1.1    Formulation](#chapter008.xhtml#h2-54)

[9.1.2    Example: Post-Earthquake Structural Safety Assessment](#chapter008.xhtml#h2-55)

[9.2    Logistic Regression](#chapter008.xhtml#h1-34)

[9.3    Gaussian Process Classification](#chapter008.xhtml#h1-35)

 

[9.4    Neural Networks](#chapter008.xhtml#h1-36)

[9.5    Regression versus Classification](#chapter008.xhtml#h1-37)

[**IV    Unsupervised Learning**](#part004.xhtml)

[**10 Clustering and Dimension Reduction**](#chapter009.xhtml)

[10.1  Clustering](#chapter009.xhtml#h1-38)

[10.1.1  Gaussian Mixture Models](#chapter009.xhtml#h2-56)

[10.1.2  K-Means](#chapter009.xhtml#h2-57)

[10.2  Principal Component Analysis](#chapter009.xhtml#h1-39)

[**11 Bayesian Networks**](#chapter010.xhtml)

[11.1  Graphical Models Nomenclature](#chapter010.xhtml#h1-41)

[11.2  Conditional Independence](#chapter010.xhtml#h1-42)

[11.3  Inference](#chapter010.xhtml#h1-43)

[11.4  Conditional Probability Estimation](#chapter010.xhtml#h1-44)

[11.4.1  Fully Observed Bayesian Network](#chapter010.xhtml#h2-58)

[11.4.2  Partially Observed Bayesian Network](#chapter010.xhtml#h2-59)

[11.5  Dynamic Bayesian Network](#chapter010.xhtml#h1-45)

[**12 State-Space Models**](#chapter011.xhtml)

[12.1  Linear Gaussian State-Space Models](#chapter011.xhtml#h1-47)

[12.1.1  Basic Problem Setup](#chapter011.xhtml#h2-60)

[12.1.2  General Formulation](#chapter011.xhtml#h2-61)

[12.1.3  Forecasting and Smoothing](#chapter011.xhtml#h2-62)

[12.1.4  Parameter Estimation](#chapter011.xhtml#h2-63)

[12.1.5  Limitations and Practical Considerations](#chapter011.xhtml#h2-64)

[12.2  State-Space Models with Regime Switching](#chapter011.xhtml#h1-48)

[12.2.1  Switching Kalman Filter](#chapter011.xhtml#h2-65)

[12.2.2  Example: Temperature Data with Regime Switch](#chapter011.xhtml#h2-66)

[12.3  Linear Model Structures](#chapter011.xhtml#h1-49)

[12.3.1  Generic Components](#chapter011.xhtml#h2-67)

[12.3.2  Component Assembly](#chapter011.xhtml#h2-68)

[12.3.3  Modeling Dependencies Between Observations](#chapter011.xhtml#h2-69)

[12.4  Anomaly Detection](#chapter011.xhtml#h1-50)

[**13 Model Calibration**](#chapter012.xhtml)

[13.1  Least-Squares Model Calibration](#chapter012.xhtml#h1-52)

[13.1.1  Illustrative Examples](#chapter012.xhtml#h2-71)

[13.1.2  Limitations of Deterministic Model Calibration](#chapter012.xhtml#h2-72)

[13.2  Hierarchical Bayesian Estimation](#chapter012.xhtml#h1-53)

[13.2.1  Joint Posterior Formulation](#chapter012.xhtml#h2-73)

[13.2.2  Predicting at Unobserved Locations](#chapter012.xhtml#h2-74)

 

[**V    Reinforcement Learning**](#part005.xhtml)

[**14 Decisions in Uncertain Contexts**](#chapter013.xhtml)

[14.1  Introductory Example](#chapter013.xhtml#h1-55)

[14.2  Utility Theory](#chapter013.xhtml#h1-56)

[14.2.1  Nomenclature](#chapter013.xhtml#h2-75)

[14.2.2  Rational Decisions](#chapter013.xhtml#h2-76)

[14.2.3  Axioms of Utility Theory](#chapter013.xhtml#h2-77)

[14.3  Utility Functions](#chapter013.xhtml#h1-57)

[14.4  Value of Information](#chapter013.xhtml#h1-58)

[14.4.1  Value of Perfect Information](#chapter013.xhtml#h2-78)

[14.4.2  Value of Imperfect Information](#chapter013.xhtml#h2-79)

[**15 Sequential Decisions**](#chapter014.xhtml)

[15.1  Markov Decision Process](#chapter014.xhtml#h1-60)

[15.1.1  Utility for an Infinite Planning Horizon](#chapter014.xhtml#h2-80)

[15.1.2  Value Iteration](#chapter014.xhtml#h2-81)

[15.1.3  Policy Iteration](#chapter014.xhtml#h2-82)

[15.1.4  Partially Observable Markov Decision Process](#chapter014.xhtml#h2-83)

[15.2  Model-Free Reinforcement Learning](#chapter014.xhtml#h1-61)

[15.2.1  Temporal Difference Learning](#chapter014.xhtml#h2-84)

[15.2.2  Temporal Difference Q-Learning](#chapter014.xhtml#h2-85)

[**Bibliography**](#bibliography001.xhtml)

[**Index**](#index.xhtml)

 

 

[*List of Figures*](#toc.xhtml#pref-1)

| [1.1](#introduction001.xhtml#Fig_1-1) || [How relationships are learned from data with and without using machine learning.](#introduction001.xhtml#Fig_1-1) |
| --- | --- |
| [1.2](#introduction001.xhtml#Fig_1-2) || [The field of artificial intelligence (AI) includes the field of machine learning (ML)](#introduction001.xhtml#Fig_1-2) |
| [1.3](#introduction001.xhtml#Fig_1-3) || [Diagram illustrating the organization of this book.](#introduction001.xhtml#Fig_1-3) |
| [2.1](#chapter001.xhtml#Fig_2-1) || [1-D plot representing a linear system, *y* = *ax* + *b*.](#chapter001.xhtml#Fig_2-1) |
| [2.2](#chapter001.xhtml#Fig_2-2) || [2-D plot representing a linear system, *y* = **a^(**T**)x** + *b*.](#chapter001.xhtml#Fig_2-2) |
| [2.3](#chapter001.xhtml#Fig_2-3) || [Example of matrix multiplication operation **C** = **AB**.](#chapter001.xhtml#Fig_2-3) |
| [2.4](#chapter001.xhtml#Fig_2-4) || [Examples of applications of different norms for computing the length of a vector **x**.](#chapter001.xhtml#Fig_2-4) |
| [2.5](#chapter001.xhtml#Fig_2-5) || [Examples of linear transformations **x**′ = **Ax**.](#chapter001.xhtml#Fig_2-5) |
| [2.6](#chapter001.xhtml#Fig_2-6) || [Example of eigen decomposition, **A** = **V**diag(***λ***)**V**^(−1).](#chapter001.xhtml#Fig_2-6) |
| [2.7](#chapter001.xhtml#Fig_2-7) || [Example of a nearly singular transformation.](#chapter001.xhtml#Fig_2-7) |
| [3.1](#chapter002.xhtml#Fig_3-1) || [A coin toss illustrates the concept of epistemic uncertainty.](#chapter002.xhtml#Fig_3-1) |
| [3.2](#chapter002.xhtml#Fig_3-2) || [The concrete elastic modulus *E* at a given location is an example of deterministic, yet unknown quantity.](#chapter002.xhtml#Fig_3-2) |
| [3.3](#chapter002.xhtml#Fig_3-3) || [Venn diagram representing the sampling space S, an event *E*, its complement *E*, and an elementary event *x*.](#chapter002.xhtml#Fig_3-3) |
| [3.4](#chapter002.xhtml#Fig_3-4) || [Venn diagrams representing the two basic operations.](#chapter002.xhtml#Fig_3-4) |
| [3.5](#chapter002.xhtml#Fig_3-5) || [Venn diagrams representing the concepts of mutual exclusivity and collective exhaustivity for events.](#chapter002.xhtml#Fig_3-5) |
| [3.6](#chapter002.xhtml#Fig_3-6) || [Venn diagram representing the addition rule for the probability of events.](#chapter002.xhtml#Fig_3-6) |
| [3.7](#chapter002.xhtml#Fig_3-7) || [Venn diagram representing the conditional occurrence of events.](#chapter002.xhtml#Fig_3-7) |
| [3.8](#chapter002.xhtml#Fig_3-8) || [Venn diagram representing the conditional occurrence of events in the context of Bayes rule.](#chapter002.xhtml#Fig_3-8) |
| [3.9](#chapter002.xhtml#Fig_3-9) || [Parallel between a Venn diagram and a continuous domain to represent a random variable.](#chapter002.xhtml#Fig_3-9) |
| [3.10](#chapter002.xhtml#Fig_3-10) || [Representation of a sampling space for a discrete random variable.](#chapter002.xhtml#Fig_3-10) |
| [3.11](#chapter002.xhtml#Fig_3-11) || [Comparison of a probability *p[X]*(*x*) and a cumulative *F[X]*(*x*) mass function.](#chapter002.xhtml#Fig_3-11) |
| [3.12](#chapter002.xhtml#Fig_3-12) || [Examples of PDF and CDF for a continuous random variable.](#chapter002.xhtml#Fig_3-12) |
| [3.13](#chapter002.xhtml#Fig_3-13) || [Schematic example of how observations of the peak ground acceleration *y* can be employed to infer the structural state of a building *x* using conditional probabilities.](#chapter002.xhtml#Fig_3-13) |
| [3.14](#chapter002.xhtml#Fig_3-14) || [Examples of marginals and a bivariate probability density function.](#chapter002.xhtml#Fig_3-14) |
| [3.15](#chapter002.xhtml#Fig_3-15) || [Examples of marginals and a bivariate cumulative distribution function.](#chapter002.xhtml#Fig_3-15) |
| [3.16](#chapter002.xhtml#Fig_3-16) || [Examples of marginals and bivariate probability mass functions.](#chapter002.xhtml#Fig_3-16) |
| [3.17](#chapter002.xhtml#Fig_3-17) || [Examples of scatter plots between the realizations of two random variables for different correlation coefficients *ρ*.](#chapter002.xhtml#Fig_3-17) |
| [3.18](#chapter002.xhtml#Fig_3-18) || [A scatter plot where there is a quadratic dependence between the variables.](#chapter002.xhtml#Fig_3-18) |
| [3.19](#chapter002.xhtml#Fig_3-19) || [Example of 1-D nonlinear transformation *y* = *g*(*x*).](#chapter002.xhtml#Fig_3-19) |
| [3.20](#chapter002.xhtml#Fig_3-20) || [Illustration of a 2-D transformation.](#chapter002.xhtml#Fig_3-20) |
| [3.21](#chapter002.xhtml#Fig_3-21) || [Examples of transformations through a linear function.](#chapter002.xhtml#Fig_3-21) |
| [3.22](#chapter002.xhtml#Fig_3-22) || [Example of a linearized nonlinear transformation.](#chapter002.xhtml#Fig_3-22) |
| [4.1](#chapter003.xhtml#Fig_4-1) || [Representation of the univariate Normal for *µ* = 0, *σ* = 1.](#chapter003.xhtml#Fig_4-1) |
| [4.2](#chapter003.xhtml#Fig_4-2) || [Illustration of the univariate Normal probability density function formulation for *µ* = 0, *σ* = 1.](#chapter003.xhtml#Fig_4-2) |
| [4.3](#chapter003.xhtml#Fig_4-3) || [Example of bivariate PDF for which the covariance matrix is decomposed into its eigenvector and eigenvalues.](#chapter003.xhtml#Fig_4-3) |
| [4.4](#chapter003.xhtml#Fig_4-4) || [Examples of bivariate PDF and CDF.](#chapter003.xhtml#Fig_4-4) |
| [4.5](#chapter003.xhtml#Fig_4-5) || [Example of dependence between the resistance of beams.](#chapter003.xhtml#Fig_4-5) |
| [4.6](#chapter003.xhtml#Fig_4-6) || [Joint prior PDF ![art](images/Art_P3.jpg)and conditional PDF ![art](images/Art_P4.jpg)describing the resistance of beams.](#chapter003.xhtml#Fig_4-6) |
| [4.7](#chapter003.xhtml#Fig_4-7) || [Steel cables each made from multiple wires.](#chapter003.xhtml#Fig_4-7) |
| [4.8](#chapter003.xhtml#Fig_4-8) || [PDF of the cable’s resistance depending on the correlation between the strength of each wire.](#chapter003.xhtml#Fig_4-8) |
| [4.9](#chapter003.xhtml#Fig_4-9) || [Univariate log-normal probability density function for {*µ[X]* = 2, *σ[X]* = 1} and {*λ* = 0.58, ζ = 0.47}.](#chapter003.xhtml#Fig_4-9) |
| [4.10](#chapter003.xhtml#Fig_4-10) || [Example of bivariate log-normal probability density function.](#chapter003.xhtml#Fig_4-10) |
| [4.11](#chapter003.xhtml#Fig_4-11) || [Three examples of the Beta probability density function evaluated for different sets of parameters {*α*, *β*}.](#chapter003.xhtml#Fig_4-11) |
| [5.1](#chapter004.xhtml#Fig_5-1) || [Examples of a convex and a non-convex set.](#chapter004.xhtml#Fig_5-1) |
| [5.2](#chapter004.xhtml#Fig_5-2) || [Representations of convex/concave and non-convex/non-concave functions.](#chapter004.xhtml#Fig_5-2) |
| [5.3](#chapter004.xhtml#Fig_5-3) || [Example of application of the Armijo rule to test if *θ*[new] has sufficiently increased the objective function in comparison with *θ*[old].](#chapter004.xhtml#Fig_5-3) |
| [5.4](#chapter004.xhtml#Fig_5-4) || [Example of application of gradient ascent with backtracking for finding the maximum of a function.](#chapter004.xhtml#Fig_5-4) |
| [5.5](#chapter004.xhtml#Fig_5-5) || [Example of application of gradient ascent converging to a local maximum for a function.](#chapter004.xhtml#Fig_5-5) |
| [5.6](#chapter004.xhtml#Fig_5-6) || [Comparison of gradient ascent with and without momentum.](#chapter004.xhtml#Fig_5-6) |
| [5.7](#chapter004.xhtml#Fig_5-7) || [Example of application of Newton-Raphson to a quadratic function.](#chapter004.xhtml#Fig_5-7) |
| [5.8](#chapter004.xhtml#Fig_5-8) || [Example of application of the Newton-Raphson algorithm with backtracking line search for finding the maximum of a function.](#chapter004.xhtml#Fig_5-8) |
| [5.9](#chapter004.xhtml#Fig_5-9) || [Example of saddle point ***θ*** where ![art](images/Art_P5.jpg)and ![art](images/Art_P6.jpg).](#chapter004.xhtml#Fig_5-9) |
| [5.10](#chapter004.xhtml#Fig_5-10) || [Example of application of the coordinate ascent Newton-Raphson algorithm with backtracking for finding the maximum of a 2-D function.](#chapter004.xhtml#Fig_5-10) |
| [5.11](#chapter004.xhtml#Fig_5-11) || [Illustration of 1-D numerical derivatives.](#chapter004.xhtml#Fig_5-11) |
| [5.12](#chapter004.xhtml#Fig_5-12) || [Illustration of 2-D partial numerical derivatives.](#chapter004.xhtml#Fig_5-12) |
| [5.13](#chapter004.xhtml#Fig_5-13) || [Examples of transformation functions.](#chapter004.xhtml#Fig_5-13) |
| [6.1](#chapter005.xhtml#Fig_6-1) || [Visual interpretation of Bayes rule in the context of disease screening.](#chapter005.xhtml#Fig_6-1) |
| [6.2](#chapter005.xhtml#Fig_6-2) || [The example of a disease so rare that only one human on Earth has it.](#chapter005.xhtml#Fig_6-2) |
| [6.3](#chapter005.xhtml#Fig_6-3) || [Fire alarm example.](#chapter005.xhtml#Fig_6-3) |
| [6.4](#chapter005.xhtml#Fig_6-4) || [Example illustrating the role of the prior in sequential data acquisition and interpretation.](#chapter005.xhtml#Fig_6-4) |
| [6.5](#chapter005.xhtml#Fig_6-5) || [Extensive damage after San Francisco’s 1906 earthquake.](#chapter005.xhtml#Fig_6-5) |
| [6.6](#chapter005.xhtml#Fig_6-6) || [Venn diagram illustrating the sample space for earthquake intensity and post-earthquake structural states.](#chapter005.xhtml#Fig_6-6) |
| [6.7](#chapter005.xhtml#Fig_6-7) || [Representation of the likelihood function for a direct observation.](#chapter005.xhtml#Fig_6-7) |
| [6.8](#chapter005.xhtml#Fig_6-8) || [Representation of the likelihood function for an upper-bound censored observation.](#chapter005.xhtml#Fig_6-8) |
| [6.9](#chapter005.xhtml#Fig_6-9) || [Representation of the likelihood function for a lower-bound censored observation.](#chapter005.xhtml#Fig_6-9) |
| [6.10](#chapter005.xhtml#Fig_6-10) || [Examples of application of the rectangle integration rule.](#chapter005.xhtml#Fig_6-10) |
| [6.11](#chapter005.xhtml#Fig_6-11) || [Example of prior, likelihood, and posterior.](#chapter005.xhtml#Fig_6-11) |
| [6.12](#chapter005.xhtml#Fig_6-12) || [Example of two streams merging in a single river.](#chapter005.xhtml#Fig_6-12) |
| [6.13](#chapter005.xhtml#Fig_6-13) || [Posterior contours for an example of non-identifiable problem.](#chapter005.xhtml#Fig_6-13) |
| [6.14](#chapter005.xhtml#Fig_6-14) || [Posterior contours for an example of non-identifiable problem constrained by the prior knowledge.](#chapter005.xhtml#Fig_6-14) |
| [6.15](#chapter005.xhtml#Fig_6-15) || [Example of posterior PDF tending toward the Dirac delta function.](#chapter005.xhtml#Fig_6-15) |
| [6.16](#chapter005.xhtml#Fig_6-16) || [Example of Bayesian parameter estimation.](#chapter005.xhtml#Fig_6-16) |
| [6.17](#chapter005.xhtml#Fig_6-17) || [The posterior PDF for parameters reduces to a Dirac delta function when the number of independent observations tends to infinity.](#chapter005.xhtml#Fig_6-17) |
| [6.18](#chapter005.xhtml#Fig_6-18) || [Examples of Monte Carlo numerical integration for which the theoretical answer is *a* = *πr*² = 0.785.](#chapter005.xhtml#Fig_6-18) |
| [6.19](#chapter005.xhtml#Fig_6-19) || [Example of difficult situation encountered when trying to sample from the prior.](#chapter005.xhtml#Fig_6-19) |
| [6.20](#chapter005.xhtml#Fig_6-20) || [Example of Bayesian estimation with censored observations.](#chapter005.xhtml#Fig_6-20) |
| [6.21](#chapter005.xhtml#Fig_6-21) || [Comparative example of a uniform and normal prior PDF for performing Bayesian estimation with censored observations.](#chapter005.xhtml#Fig_6-21) |
| [6.22](#chapter005.xhtml#Fig_6-22) || [Example where drawing Monte Carlo samples from the prior leads to a poor estimate of the posterior because no sample falls in the high probability region.](#chapter005.xhtml#Fig_6-22) |
| [6.23](#chapter005.xhtml#Fig_6-23) || [Example of samples taken from the same concrete batch.](#chapter005.xhtml#Fig_6-23) |
| [6.24](#chapter005.xhtml#Fig_6-24) || [Examples of Bayesian estimation as a function of the number of observations employed, D = {1, 5, 100}.](#chapter005.xhtml#Fig_6-24) |
| [6.25](#chapter005.xhtml#Fig_6-25) || [Thumbtacks described by a random variable with sample space S = {Head (H), Tail(T)}.](#chapter005.xhtml#Fig_6-25) |
| [6.26](#chapter005.xhtml#Fig_6-26) || [Example of application of conjugate priors on traffic data.](#chapter005.xhtml#Fig_6-26) |
| [6.27](#chapter005.xhtml#Fig_6-27) || [Posterior PDF for the probability of an accident *before* refection works.](#chapter005.xhtml#Fig_6-27) |
| [6.28](#chapter005.xhtml#Fig_6-28) || [Prior and posterior PDF for the probability of an accident *after* refection works.](#chapter005.xhtml#Fig_6-28) |
| [6.29](#chapter005.xhtml#Fig_6-29) || [Example of an application of the Laplace approximation to describe a posterior PDF.](#chapter005.xhtml#Fig_6-29) |
| [7.1](#chapter006.xhtml#Fig_7-1) || [Example of random walk generated with MCMC.](#chapter006.xhtml#Fig_7-1) |
| [7.2](#chapter006.xhtml#Fig_7-2) || [Examples of 1-D and 2-D proposal distributions, *q*(***θ***′|***θ***).](#chapter006.xhtml#Fig_7-2) |
| [7.3](#chapter006.xhtml#Fig_7-3) || [Step-by-step example of 1-D Metropolis sampling.](#chapter006.xhtml#Fig_7-3) |
| [7.4](#chapter006.xhtml#Fig_7-4) || [Example illustrating how, when using a truncated Normal PDF as a proposal, *q*(*θ*′|*θ*) ≠ *q*(*θ*|*θ*′).](#chapter006.xhtml#Fig_7-4) |
| [7.5](#chapter006.xhtml#Fig_7-5) || [The impact of the initial starting location on MCMC sampling.](#chapter006.xhtml#Fig_7-5) |
| [7.6](#chapter006.xhtml#Fig_7-6) || [The impact of the initial starting location using a stochastic process.](#chapter006.xhtml#Fig_7-6) |
| [7.7](#chapter006.xhtml#Fig_7-7) || [The notation for samples taken from multiple chains.](#chapter006.xhtml#Fig_7-7) |
| [7.8](#chapter006.xhtml#Fig_7-8) || [The EPSR metric to check for convergence.](#chapter006.xhtml#Fig_7-8) |
| [7.9](#chapter006.xhtml#Fig_7-9) || [Comparison of the ESPR convergence metric ![art](images/Rcap.jpg)for 100, 1,000, and 10,000 MCMC samples.](#chapter006.xhtml#Fig_7-9) |
| [7.10](#chapter006.xhtml#Fig_7-10) || [Relative convergence speed of MCMC for P ≥ 5 as a function of the acceptance rate *β*.](#chapter006.xhtml#Fig_7-10) |
| [7.11](#chapter006.xhtml#Fig_7-11) || [Comparison of the EPSR convergence metric ![art](images/Rcap.jpg)for 1,000 MCMC samples using different proposal distributions.](#chapter006.xhtml#Fig_7-11) |
| [7.12](#chapter006.xhtml#Fig_7-12) || [Example of application of MCMC sampling for the estimation of the resistance of a concrete mix.](#chapter006.xhtml#Fig_7-12) |
| [8.1](#chapter007.xhtml#Fig_8-1) || [Examples of applications of regression analysis in the context of civil engineering.](#chapter007.xhtml#Fig_8-1) |
| [8.2](#chapter007.xhtml#Fig_8-2) || [Examples of linear regression applied to linear and nonlinear relationships.](#chapter007.xhtml#Fig_8-2) |
| [8.3](#chapter007.xhtml#Fig_8-3) || [The minimum of a continuous function corresponds to the location where its derivative equals zero.](#chapter007.xhtml#Fig_8-3) |
| [8.4](#chapter007.xhtml#Fig_8-4) || [Example of linear regression minimizing the performance metric *J* computed on the training set.](#chapter007.xhtml#Fig_8-4) |
| [8.5](#chapter007.xhtml#Fig_8-5) || [Examples of linear regression applied to nonlinear relationships.](#chapter007.xhtml#Fig_8-5) |
| [8.6](#chapter007.xhtml#Fig_8-6) || [Illustration of the *bias* and *variance* when talking about predictive performance and model complexity.](#chapter007.xhtml#Fig_8-6) |
| [8.7](#chapter007.xhtml#Fig_8-7) || [Example of (a) a model with correct complexity, and (b) a model with too much capacity.](#chapter007.xhtml#Fig_8-7) |
| [8.8](#chapter007.xhtml#Fig_8-8) || [The *N*\-fold cross-validation procedure.](#chapter007.xhtml#Fig_8-8) |
| [8.9](#chapter007.xhtml#Fig_8-9) || [Example of 2-fold cross-validation for the model *g*[1](*x*) = *b*[0] + *b*[1]*x*.](#chapter007.xhtml#Fig_8-9) |
| [8.10](#chapter007.xhtml#Fig_8-10) || [Example of 2-fold cross-validation for the model *g*[2](*x*) = *b*[0] + *b*[1]*x* + *b*[2]*x*² + *b*[3]*x*³ + *b*[4]*x*⁴ + *b*[5]*x*⁵.](#chapter007.xhtml#Fig_8-10) |
| [8.11](#chapter007.xhtml#Fig_8-11) || [Example of 2-fold cross-validation for the model *g*[3](*x*) = *b*[0] + *b*[1]*x*, where the data follows the real model ![art](images/Art_P7.jpg).](#chapter007.xhtml#Fig_8-11) |
| [8.12](#chapter007.xhtml#Fig_8-12) || [Example of application of linear regression to a 2-D data set.](#chapter007.xhtml#Fig_8-12) |
| [8.13](#chapter007.xhtml#Fig_8-13) || [Illustrations of some of the limitations of the linear regression method presented in §8.1.1](#chapter007.xhtml#Fig_8-13). |
| [8.14](#chapter007.xhtml#Fig_8-14) || [Example of a 100 km long pipeline.](#chapter007.xhtml#Fig_8-14) |
| [8.15](#chapter007.xhtml#Fig_8-15) || [Representation of the prior knowledge for the temperature along a pipeline.](#chapter007.xhtml#Fig_8-15) |
| [8.16](#chapter007.xhtml#Fig_8-16) || [Square-exponential correlation function.](#chapter007.xhtml#Fig_8-16) |
| [8.17](#chapter007.xhtml#Fig_8-17) || [Examples of Gaussian process realizations for different length-scale parameter values.](#chapter007.xhtml#Fig_8-17) |
| [8.18](#chapter007.xhtml#Fig_8-18) || [Joint Gaussian prior knowledge of the temperature at two locations and conditional PDF for the temperature *g*[1], given the observation *g*[2] = −2.](#chapter007.xhtml#Fig_8-18) |
| [8.19](#chapter007.xhtml#Fig_8-19) || [Examples of how the Gaussian process describing the pipeline temperature evolves as it is updated with different data sets D.](#chapter007.xhtml#Fig_8-19) |
| [8.20](#chapter007.xhtml#Fig_8-20) || [Examples of how the Gaussian process describing the pipeline temperature evolves as it is updated with different data sets D, with an observation standard deviation *σ[V]* = 1°C](#chapter007.xhtml#Fig_8-20) |
| [8.21](#chapter007.xhtml#Fig_8-21) || [Bivariate square-exponential correlation function with parameters *ℓ*[1] = 1 and *ℓ*[2] = 1.5.](#chapter007.xhtml#Fig_8-21) |
| [8.22](#chapter007.xhtml#Fig_8-22) || [Log-likelihood maximization.](#chapter007.xhtml#Fig_8-22) |
| [8.23](#chapter007.xhtml#Fig_8-23) || [Example of application of GPR for soil contamination characterization.](#chapter007.xhtml#Fig_8-23) |
| [8.24](#chapter007.xhtml#Fig_8-24) || [Examples of finite element structural models.](#chapter007.xhtml#Fig_8-24) |
| [8.25](#chapter007.xhtml#Fig_8-25) || [Tamar Bridge finite element model.](#chapter007.xhtml#Fig_8-25) |
| [8.26](#chapter007.xhtml#Fig_8-26) || [Tamar Bridge model parameter description.](#chapter007.xhtml#Fig_8-26) |
| [8.27](#chapter007.xhtml#Fig_8-27) || [Comparison of the GPR model predictions with the finite-element model predictions using the leave-one-out cross-validation procedure.](#chapter007.xhtml#Fig_8-27) |
| [8.28](#chapter007.xhtml#Fig_8-28) || [An example of Matern-class correlation function.](#chapter007.xhtml#Fig_8-28) |
| [8.29](#chapter007.xhtml#Fig_8-29) || [Examples of periodic correlation functions.](#chapter007.xhtml#Fig_8-29) |
| [8.30](#chapter007.xhtml#Fig_8-30) || [Example of application of a periodic covariance function to model temperature data.](#chapter007.xhtml#Fig_8-30) |
| [8.31](#chapter007.xhtml#Fig_8-31) || [Examples of homo- and heteroscedastic cases.](#chapter007.xhtml#Fig_8-31) |
| [8.32](#chapter007.xhtml#Fig_8-32) || [Representation of linear regression as a feedforward neural network.](#chapter007.xhtml#Fig_8-32) |
| [8.33](#chapter007.xhtml#Fig_8-33) || [Representation of linear regression using multiple layers.](#chapter007.xhtml#Fig_8-33) |
| [8.34](#chapter007.xhtml#Fig_8-34) || [Comparison of the *logistic*, *tanh*, and *ReLU* activation functions.](#chapter007.xhtml#Fig_8-34) |
| [8.35](#chapter007.xhtml#Fig_8-35) || [A simple feedforward neural network.](#chapter007.xhtml#Fig_8-35) |
| [8.36](#chapter007.xhtml#Fig_8-36) || [A fully connected neural network having L hidden layers, each having A activation units.](#chapter007.xhtml#Fig_8-36) |
| [8.37](#chapter007.xhtml#Fig_8-37) || [Example of early stopping when the loss function for the validation set stops decreasing.](#chapter007.xhtml#Fig_8-37) |
| [8.38](#chapter007.xhtml#Fig_8-38) || [Comparison of the system responses with the model predictions obtained in a leave-one-out cross-validation setup.](#chapter007.xhtml#Fig_8-38) |
| [9.1](#chapter008.xhtml#Fig_9-1) || [Examples of application of classification analysis in the context of civil engineering.](#chapter008.xhtml#Fig_9-1) |
| [9.2](#chapter008.xhtml#Fig_9-2) || [Example of generative classifier using marginal PDFs.](#chapter008.xhtml#Fig_9-2) |
| [9.3](#chapter008.xhtml#Fig_9-3) || [Examples of PDF *f*(**x**|*y* = *j*) for naive Bayes, LDA, and QDA.](#chapter008.xhtml#Fig_9-3) |
| [9.4](#chapter008.xhtml#Fig_9-4) || [Example of quadratic discriminant analysis.](#chapter008.xhtml#Fig_9-4) |
| [9.5](#chapter008.xhtml#Fig_9-5) || [Empirical observations of the ratio between fundamental frequency of buildings after and before an earthquake.](#chapter008.xhtml#Fig_9-5) |
| [9.6](#chapter008.xhtml#Fig_9-6) || [Posterior PDFs of means and standard deviations and posterior predictive PDFs of frequency ratios *x* for each damage index *d*.](#chapter008.xhtml#Fig_9-6) |
| [9.7](#chapter008.xhtml#Fig_9-7) || [Posterior predictive probability of a damage index *d* given a frequency ratio *x*.](#chapter008.xhtml#Fig_9-7) |
| [9.8](#chapter008.xhtml#Fig_9-8) || [The logistic sigmoid function *σ*(*z*) = (1 + exp(−*z*))^(−1).](#chapter008.xhtml#Fig_9-8) |
| [9.9](#chapter008.xhtml#Fig_9-9) || [Example of a function *g*(*x*) = 0.08*x* − 4 passed through the logistic sigmoid function.](#chapter008.xhtml#Fig_9-9) |
| [9.10](#chapter008.xhtml#Fig_9-10) || [Example of application of logistic regression.](#chapter008.xhtml#Fig_9-10) |
| [9.11](#chapter008.xhtml#Fig_9-11) || [The standard Normal CDF, where Φ(*z*) denotes the CDF of *Z* ~ N (*z*; 0, 1).](#chapter008.xhtml#Fig_9-11) |
| [9.12](#chapter008.xhtml#Fig_9-12) || [Example of Gaussian process *G*(*x*) evaluated through Φ(*G*(*x*)) and whose uncertainty is marginalized in order to describe Pr(*Y* = +1|*x*).](#chapter008.xhtml#Fig_9-12) |
| [9.13](#chapter008.xhtml#Fig_9-13) || [Example of application of Gaussian process classification using the package GPML with a different number of observations D ∈ {25, 50, 100}.](#chapter008.xhtml#Fig_9-13) |
| [9.14](#chapter008.xhtml#Fig_9-14) || [Example of application of Gaussian process classification to the post-earthquake structural safety evaluation data set.](#chapter008.xhtml#Fig_9-14) |
| [9.15](#chapter008.xhtml#Fig_9-15) || [Nomenclature for a feedforward neural network employed for classification.](#chapter008.xhtml#Fig_9-15) |
| [10.1](#chapter009.xhtml#Fig_10-1) || [Eruption durations and time between eruptions can be clustered into two groups.](#chapter009.xhtml#Fig_10-1) |
| [10.2](#chapter009.xhtml#Fig_10-2) || [Examples of Gaussian mixture PDFs.](#chapter009.xhtml#Fig_10-2) |
| [10.3](#chapter009.xhtml#Fig_10-3) || [The first two iterations of the EM algorithm for a Gaussian mixture model applied on the Old Faithful data.](#chapter009.xhtml#Fig_10-3) |
| [10.4](#chapter009.xhtml#Fig_10-4) || [Example of an application of a Gaussian mixture model to the Old Faithful geyser data set.](#chapter009.xhtml#Fig_10-4) |
| [10.5](#chapter009.xhtml#Fig_10-5) || [Example of an application of a Gaussian mixture model to overlapping clusters.](#chapter009.xhtml#Fig_10-5) |
| [10.6](#chapter009.xhtml#Fig_10-6) || [Example of application of K-means.](#chapter009.xhtml#Fig_10-6) |
| [10.7](#chapter009.xhtml#Fig_10-7) || [Example of application of principal component analysis to the normalized and centered Old Faithful data set.](#chapter009.xhtml#Fig_10-7) |
| [10.8](#chapter009.xhtml#Fig_10-8) || [Example of application of the principal component analysis for dimensionality reduction.](#chapter009.xhtml#Fig_10-8) |
| [11.1](#chapter010.xhtml#Fig_11-1) || [Example of Bayesian network for representing the relationships between temperature, the presence of the flu virus, and being sick from the flu virus. 167](#chapter010.xhtml#Fig_11-1) |
| [11.2](#chapter010.xhtml#Fig_11-2) || [Example of dependence represented by directed links between hidden (white) and an observed (shaded) nodes describing random variables.](#chapter010.xhtml#Fig_11-2) |
| [11.3](#chapter010.xhtml#Fig_11-3) || [Example of cyanobacteria bloom.](#chapter010.xhtml#Fig_11-3) |
| [11.4](#chapter010.xhtml#Fig_11-4) || [Bayesian network for the cyanobacteria example.](#chapter010.xhtml#Fig_11-4) |
| [11.5](#chapter010.xhtml#Fig_11-5) || [Cases where *A* and *C* are conditionally independent for the different types of connection in Bayesian networks.](#chapter010.xhtml#Fig_11-5) |
| [11.6](#chapter010.xhtml#Fig_11-6) || [The concept of conditional independence illustrated using the cyanobacteria example.](#chapter010.xhtml#Fig_11-6) |
| [11.7](#chapter010.xhtml#Fig_11-7) || [Example of data set for learning conditional probability tables.](#chapter010.xhtml#Fig_11-7) |
| [11.8](#chapter010.xhtml#Fig_11-8) || [Example of partially observed Bayesian network for the cyanobacteria data set.](#chapter010.xhtml#Fig_11-8) |
| [11.9](#chapter010.xhtml#Fig_11-9) || [Equivalent expanded and compact representations of a dynamic Bayesian network.](#chapter010.xhtml#Fig_11-9) |
| [11.10](#chapter010.xhtml#Fig_11-10) || [Dynamic Bayesian network for the cyanobacteria example.](#chapter010.xhtml#Fig_11-10) |
| [12.1](#chapter011.xhtml#Fig_12-1) || [The concept of time-series stationarity.](#chapter011.xhtml#Fig_12-1) |
| [12.2](#chapter011.xhtml#Fig_12-2) || [A cannon-man trajectory.](#chapter011.xhtml#Fig_12-2) |
| [12.3](#chapter011.xhtml#Fig_12-3) || [Example of state-space model.](#chapter011.xhtml#Fig_12-3) |
| [12.4](#chapter011.xhtml#Fig_12-4) || [Apollo mission service module.](#chapter011.xhtml#Fig_12-4) |
| [12.5](#chapter011.xhtml#Fig_12-5) || [Step-by-step probabilistic hidden-state estimation.](#chapter011.xhtml#Fig_12-5) |
| [12.6](#chapter011.xhtml#Fig_12-6) || [The error caused on the level and the trend by a constant acceleration ![art](images/Art_P8.jpg)over a time step of length Δ*t*.](#chapter011.xhtml#Fig_12-6) |
| [12.7](#chapter011.xhtml#Fig_12-7) || [Example of hidden-state estimation for a constant-speed model.](#chapter011.xhtml#Fig_12-7) |
| [12.8](#chapter011.xhtml#Fig_12-8) || [Comparison of *filtering*, *smoothing*, and *forecasting*.](#chapter011.xhtml#Fig_12-8) |
| [12.9](#chapter011.xhtml#Fig_12-9) || [Example of hidden-state forecast for a constant-speed model.](#chapter011.xhtml#Fig_12-9) |
| [12.10](#chapter011.xhtml#Fig_12-10) || [Information flow for the filtering and smoothing processes.](#chapter011.xhtml#Fig_12-10) |
| [12.11](#chapter011.xhtml#Fig_12-11) || [Comparison of filtering, smoothing, and the true states.](#chapter011.xhtml#Fig_12-11) |
| [12.12](#chapter011.xhtml#Fig_12-12) || [The MLE optimal parameters correspond to the location where the derivative of the log-likelihood equals zero.](#chapter011.xhtml#Fig_12-12) |
| [12.13](#chapter011.xhtml#Fig_12-13) || [Comparison between single- and multiple-regime models.](#chapter011.xhtml#Fig_12-13) |
| [12.14](#chapter011.xhtml#Fig_12-14) || [Comparison of regime switching with and without merging the state at each time step.](#chapter011.xhtml#Fig_12-14) |
| [12.15](#chapter011.xhtml#Fig_12-15) || [Switching Kalman filter: How initial states transition through two distinct models.](#chapter011.xhtml#Fig_12-15) |
| [12.16](#chapter011.xhtml#Fig_12-16) || [The switching Kalman filter *merge step*.](#chapter011.xhtml#Fig_12-16) |
| [12.17](#chapter011.xhtml#Fig_12-17) || [Example of a Gaussian mixture PDF.](#chapter011.xhtml#Fig_12-17) |
| [12.18](#chapter011.xhtml#Fig_12-18) || [Examples of Gaussian mixtures.](#chapter011.xhtml#Fig_12-18) |
| [12.19](#chapter011.xhtml#Fig_12-19) || [General overview of the switching Kalman filter procedure.](#chapter011.xhtml#Fig_12-19) |
| [12.20](#chapter011.xhtml#Fig_12-20) || [Example of data set where there is a switch between a zero-speed regime and a constant-speed regime.](#chapter011.xhtml#Fig_12-20) |
| [12.21](#chapter011.xhtml#Fig_12-21) || [Example of hidden-states estimation using the switching Kalman filter.](#chapter011.xhtml#Fig_12-21) |
| [12.22](#chapter011.xhtml#Fig_12-22) || [Generic components that can be seen as the building blocks, which, once assembled, allow modeling complex empirical responses.](#chapter011.xhtml#Fig_12-22) |
| [12.23](#chapter011.xhtml#Fig_12-23) || [Examples of local level components.](#chapter011.xhtml#Fig_12-23) |
| [12.24](#chapter011.xhtml#Fig_12-24) || [Examples of local trend components.](#chapter011.xhtml#Fig_12-24) |
| [12.25](#chapter011.xhtml#Fig_12-25) || [Examples of local acceleration components.](#chapter011.xhtml#Fig_12-25) |
| [12.26](#chapter011.xhtml#Fig_12-26) || [Examples of periodic components.](#chapter011.xhtml#Fig_12-26) |
| [12.27](#chapter011.xhtml#Fig_12-27) || [Examples of autoregressive components.](#chapter011.xhtml#Fig_12-27) |
| [12.28](#chapter011.xhtml#Fig_12-28) || [Montreal YUL airport daily average temperature observations for the period 1953–2013.](#chapter011.xhtml#Fig_12-28) |
| [12.29](#chapter011.xhtml#Fig_12-29) || [Hidden-state estimates for the temperature time series.](#chapter011.xhtml#Fig_12-29) |
| [12.30](#chapter011.xhtml#Fig_12-30) || [Observed time series for the displacement and temperature of a bridge.](#chapter011.xhtml#Fig_12-30) |
| [12.31](#chapter011.xhtml#Fig_12-31) || [Hidden-state estimates for the displacements and temperatures.](#chapter011.xhtml#Fig_12-31) |
| [12.32](#chapter011.xhtml#Fig_12-32) || [Example of a dam displacement time series that contains an anomaly that requires using the switching Kalman filter.](#chapter011.xhtml#Fig_12-32) |
| [12.33](#chapter011.xhtml#Fig_12-33) || [Probability of regimes 1 and 2 obtained using the SKF algorithm.](#chapter011.xhtml#Fig_12-33) |
| [12.34](#chapter011.xhtml#Fig_12-34) || [Expected values *µ[t|t]* and uncertainty bound *µ[t|t]* ± *σ[t|t]* for hidden states resulting from a combination of regimes 1 and 2 using the SKF algorithm.](#chapter011.xhtml#Fig_12-34) |
| [13.1](#chapter012.xhtml#Fig_13-1) || [Example of hard-coded finite-element model for which we want to infer the parameter values ***θ*** = \[*θ*[1]*θ*[2]\]^(**T**) from sets of observations (*x[i], y[i]*).](#chapter012.xhtml#Fig_13-1) |
| [13.2](#chapter012.xhtml#Fig_13-2) || [The reference model ![art](images/Art_P9.jpg)that is employed to generate simulated observations.](#chapter012.xhtml#Fig_13-2) |
| [13.3](#chapter012.xhtml#Fig_13-3) || [Least-squares model calibration where the interpretation model is identical to the reference model, ![art](images/Art_P10.jpg), and where there are no measurement errors.](#chapter012.xhtml#Fig_13-3) |
| [13.4](#chapter012.xhtml#Fig_13-4) || [Least-squares model calibration where the interpretation model is simplified in comparison with the reference model, ![art](images/Art_P11.jpg), and where there are measurement errors.](#chapter012.xhtml#Fig_13-4) |
| [13.5](#chapter012.xhtml#Fig_13-5) || [Least-squares model calibration where the interpretation model is overcomplex in comparison with the reference model, ![art](images/Art_P12.jpg), and where there are measurement errors.](#chapter012.xhtml#Fig_13-5) |
| [13.6](#chapter012.xhtml#Fig_13-6) || [In complex engineering contexts, no matter how good a hard-coded physics-based model is, it never perfectly represents the reality.](#chapter012.xhtml#Fig_13-6) |
| [13.7](#chapter012.xhtml#Fig_13-7) || [Graphical representation of the prior knowledge for prediction errors arising from the use of a simplified interpretation model.](#chapter012.xhtml#Fig_13-7) |
| [13.8](#chapter012.xhtml#Fig_13-8) || [Bivariate scatter plots and histograms describing the marginal posterior PDFs.](#chapter012.xhtml#Fig_13-8) |
| [13.9](#chapter012.xhtml#Fig_13-9) || [Comparison of the posterior predictive model predictions with the displacement of the reference model.](#chapter012.xhtml#Fig_13-9) |
| [14.1](#chapter013.xhtml#Fig_14-1) || [Decision context for a soil contamination example.](#chapter013.xhtml#Fig_14-1) |
| [14.2](#chapter013.xhtml#Fig_14-2) || [Decision tree for the soil contamination example.](#chapter013.xhtml#Fig_14-2) |
| [14.3](#chapter013.xhtml#Fig_14-3) || [Comparison between risk *\-seeking*, *\-neutral*, and *\-averse* behaviors for utility functions.](#chapter013.xhtml#Fig_14-3) |
| [14.4](#chapter013.xhtml#Fig_14-4) || [Discrete case: Comparison of the effect of a risk-neutral and a risk-averse behavior on the expected utility.](#chapter013.xhtml#Fig_14-4) |
| [14.5](#chapter013.xhtml#Fig_14-5) || [Continuous case: Comparison of the effect of a linear (risk-neutral) and a nonlinear (risk-averse) utility function on the expected utility.](#chapter013.xhtml#Fig_14-5) |
| [14.6](#chapter013.xhtml#Fig_14-6) || [Decision tree illustrating the value of perfect information.](#chapter013.xhtml#Fig_14-6) |
| [14.7](#chapter013.xhtml#Fig_14-7) || [Decision tree illustrating the value of imperfect information.](#chapter013.xhtml#Fig_14-7) |
| [15.1](#chapter014.xhtml#Fig_15-1) || [Contextual illustration of a sequential decision process applied to the problem of infrastructure maintenance planning.](#chapter014.xhtml#Fig_15-1) |
| [15.2](#chapter014.xhtml#Fig_15-2) || [Example of bridge condition time histories.](#chapter014.xhtml#Fig_15-2) |
| [15.3](#chapter014.xhtml#Fig_15-3) || [Schematic representation of the interaction between an agent and its environment.](#chapter014.xhtml#Fig_15-3) |
| [15.4](#chapter014.xhtml#Fig_15-4) || [Value iteration algorithm converging to stationary expected utilities.](#chapter014.xhtml#Fig_15-4) |
| [15.5](#chapter014.xhtml#Fig_15-5) || [Expected utility for each action and state obtained using the value iteration algorithm.](#chapter014.xhtml#Fig_15-5) |
| [15.6](#chapter014.xhtml#Fig_15-6) || [The incremental calculation of an average for a set {*x*[1], *x*[2], ⋯ , *x*[500]}, *x[t]* : *X* ~ N (*x*; 3, 1).](#chapter014.xhtml#Fig_15-6) |
| [15.7](#chapter014.xhtml#Fig_15-7) || [Expected utility convergence for the Q-learning algorithm.](#chapter014.xhtml#Fig_15-7) |
| [15.8](#chapter014.xhtml#Fig_15-8) || [Evolution of *ϵ*(N(*s*)) for each state *s* as a function of the number of episodes.](#chapter014.xhtml#Fig_15-8) |

 

[*List of Algorithms*](#toc.xhtml#pref-2)

| [1](#chapter004.xhtml#Tab_1) || [Gradient ascent with backtracking line search](#chapter004.xhtml#Tab_1) |
| --- | --- |
| [2](#chapter004.xhtml#Tab_2) || [Newton-Raphson with backtracking line search](#chapter004.xhtml#Tab_2) |
| [3](#chapter004.xhtml#Tab_3) || [Coordinate ascent using Newton-Raphson](#chapter004.xhtml#Tab_3) |
| [4](#chapter006.xhtml#Tab_4) || [Metropolis sampling](#chapter006.xhtml#Tab_4) |
| [5](#chapter006.xhtml#Tab_5) || [Convergence check and scaling parameter tuning](#chapter006.xhtml#Tab_5) |
| [6](#chapter006.xhtml#Tab_6) || [Metropolis with transformed space](#chapter006.xhtml#Tab_6) |
| [7](#chapter007.xhtml#Tab_7) || [*N*\-fold cross-validation](#chapter007.xhtml#Tab_7) |
| [8](#chapter009.xhtml#Tab_8) || [EM for Gaussian mixture models](#chapter009.xhtml#Tab_8) |
| [9](#chapter009.xhtml#Tab_9) || [K-means](#chapter009.xhtml#Tab_9) |
| [10](#chapter014.xhtml#Tab_10) || [Value iteration](#chapter014.xhtml#Tab_10) |
| [11](#chapter014.xhtml#Tab_11) || [Policy iteration](#chapter014.xhtml#Tab_11) |
| [12](#chapter014.xhtml#Tab_12) || [Temporal difference Q-learning](#chapter014.xhtml#Tab_12) |

 

 

*Acknowledgments*

I would like to acknowledge the help I have received from colleagues, students, and friends in the process of writing this book. I especially thank Jonathan Jalbert, Shervin Khazaeli, Saeid Amiri, Sébastien Le Digabel, Marco Broccardo, Luong-Ha Nguyen, Rocio Lilen Segura, and Gerd Brandstetter for helping me with reviewing the manuscript. I also acknowledge the feedback I have received from many students who attended my CIV6540 graduate class at Polytechnique Montreal. I want to thank Michel Goulet, who contributed to the book with several of his photos; as well as Daphne and Daniel Dethier, who provided helpful insights during the design of the book cover. I thank the anonymous reviewers who took the time to read the manuscript and whose comments were integrated into the final version.

In a broader perspective, I would like to thank my family for their inexhaustible support over the years. Also, I want to recognize the constructive influence from my advisers, who guided me since the beginning of my university years: André Picard, Mario Fafard, Ian F.C. Smith, and last but certainly not least, Armen Der Kiureghian, who was an inspiration through his lectures and mentoring.

Finally, I want to acknowledge the exceptional freedom I was allowed to have as a young professor by my host institution, Polytechnique Montreal. Without it, I do not see how this book would have been possible.

 

 

[*Nomenclature & Abbreviations*](#toc.xhtml#pref-3)

*General Mathematical Symbols*

 
| ℝ || Real domain ≡ (−∞, ∞) |
| --- | --- |
| ℝ^+ || Real positive domain ≡ (0, ∞) |
| ℤ || Real integer domain ≡ {⋯ , −1, 0, 1, 2, ⋯ } |
| (0, 1) || Continuous close interval between 0 and 1, which includes 0 and 1 |
| (0, 1\] || Continuous open interval between 0 and 1, which includes 0 and not 1 |
| ![art](images/Art_P13.jpg) || A limit when *n* tends to infinity |
| ∀ || For all |
| : || Such that |
| ![art](images/Art_P14.jpg) || The true value for *x* |
| ![art](images/Art_P15.jpg) || An approximation of *x* |
| ∑ || Sum operation |
| ¬ || The negation symbol |
| ∏ || Product operation |
| *∫ dx* || Integral operation with respect to *x* |
| ![art](images/Art_P16.jpg) || Derivative or gradient of *v*(*x*) with respect to *x* |
| ![art](images/Art_P17.jpg) || Partial derivative of *v*(*x, y, z*) with respect to *x* |
| |*x*| || Absolute values of *x* |
| ≈ || Approximately equal |
| ∝ || Proportional to |
| ≡ || Equivalent |
| ln(*x*) ≡ log*[e]*(*x*) || Natural logarithm of *x*ln(exp(*x*)) = *x* |
| exp(*x*) ≡ *e^x* || Exponential function of *x*, = 2.71828*^x*, exp(ln(*x*)) = *x* |
| Δ*x* || An infinitesimal interval for *x* |
| *A* ⇔ *B* || *A* implies *B* and *B* implies *A* |

 

*Linear Algebra*

 
| *x* || A scalar variable |
| --- | --- |
| **x** || A column vector, **x** = \[*x*[1]*x*[2] ⋯ *x*[X]\]^(**T**) |
| **X** || A matrix |
| *x[i]* ≡ \[**x**\][*i*] || *i*^(th) element of a vector |
| *x[ij]* ≡ \[**X**\]*[ij]* || {*i, j*}^(th) element of a matrix |
| **X** = diag(**x**) || Square matrix **X** where the terms on the main diagonal are the elements of **x** and 0 elsewhere |
| **x** = diag(**X**) || Vector **x** consisting in the main diagonal terms of a matrix **X** |
| **I** || The identity matrix, i.e., a square matrix with 1 on the main diagonal and 0 elsewhere |
| blkdiag(**A**, **B**) || Block diagonal matrix where matrices **A** and **B** are concatenated on the main diagonal of a single matrix |
| **T** || Transposition operator : \[**X**\]*[ij]* = \[**X**^(**T**)\]*[ji]* |
| · || Scalar product |
| × || Matrix multiplication |
| ⊙ || Hadamar (element-wise) product |
| ||x||*[p]* || *L^p*\-norm of a vector **x** |
| det(**A**) ≡ |**A**| || Determinant of a Matrix **A** |
| tr(**A**) || Sum of the elements on the main diagonal of **A** |
| → || A transformation from a space to another |
| **J[y,x]** || The Jacobian matrix so that ![art](images/Art_P18.jpg) |
| ![art](images/Art_P19.jpg) || Partial derivative of *g*(**x**) with respect to the *i*^(th) variable *x[i]* |
| ∇*g*(**x**) || A gradient vector, ![art](images/Art_P20.jpg) |
| **H** || The Hessian matrix containing second-order partial derivatives, ![art](images/Art_P21.jpg) |

*Probability Theory and Random Variables*

 
| A = {*E*[1], *E*[2], ⋯ } || A set is described by a *calligraphic* letter |
| --- | --- |
| #A || Number of elements in a set A |
| S || Universe/sampling space, i.e., the ensemble of possible results |
| *x* || An elementary event, *x* ∈ S |
| *x* ∈ S || *x* belongs to the sampling space S |
| *E* || An ensemble of elementary events |
| *E* ⊂ S || E is a subset of S |
| *E* ⊆ S || E is a subset or is equal to S |
| *E* = S || A certain event |
| *E* = ∅ || An impossible event |
| *E* || The complement of the event *E* |
| Pr(·) || The probability of an event (∈ (0, 1)) |
| ∪ || Union operation for events, i.e., “or” |
| ∩ || Intersection operation for events, i.e., “and” |
| *X* || A random variable |
| **X** || A vector of random variables |
| *f*(*x*) ≡ *f[X]*(*x*) || Probability density function of a random variable *X* |
| *X* ~ *f*(*x*) || *X* is distributed as described by its marginal probability density function *f*(*x*) |
| **X** ~ *f*(x) || **X** is distributed as described by its joint probability density function *f*(x) |
| ![art](images/Art_P22.jpg) || Converges in distribution |
| *x*, *x[i]* || Realization of a random variable *x* : *X* ~ *f*(*x*) |
| *F* (*x*) ≡ *F[X]*(*x*) || Cumulative distribution (or mass) function of a random variable *X* |
| Φ(*x*) || Cumulative distribution function of a standard Normal random variable with mean equal to 0 and variance equal to 1 |
| *p*(*x*) ≡ *p[X]*(*x*) || Probability mass function of a random variable *X* |
| *X* ╨ *Y* || The random variables *X* and *Y* are statistically independent |
| *X* ╨ *Y*|*z* || The random variables *X* and *Y* are conditionally independent given z |
| *X*|*y* || The random variable *X* is conditionally dependent on *y* |
| ![art](images/Art_P23.jpg) || Expectation operation for a random variable *X* |
| var\[*X*\] || Variance operation for a random variable *X* |
| cov(*X, Y*) || Covariance operation for a pair of random variables *X*, *Y* |
| *δ[X]* || Coefficient of variation of a random variable *X* |
| *µ[X]* || The mean of a random variable *X* |
| ![art](images/Art_P24.jpg) || The variance of a random variable *X* |
| *ρ* || The correlation coefficient |
| ***µ*[X]** || The mean values for a vector of random variables **X** |
| **Σ[X]** || A covariance matrix for a vector of random variables **X** |
| **R**[X] || A correlation matrix for a vector of random variables **X** |
| **D[X]** || A standard deviation matrix for a vector of random variables **X** |
| N (*x*; *µ, σ*²) || The probability density function of a univariate Normal random variable *X*, parameterized by its mean and variance |
| N (***x*; *µ*[X], Σ[X]**) || The joint probability density function of a multivariate Normal random variable **X**, parameterized by its mean vector and covariance matrix |
| lnN(*x*; *λ, ζ*) || The probability density function of a log-normal random variable *X*, parameterized by its mean and standard deviation defined in the log space |
| B(*x*; *α, β*) || The probability density function of a Beta random variable *X*, parameterized by *α* and *β* |
| U(*x*; 0, 1) || The uniform probability density function for a random variable *X* defined for the interval (0, 1) |
| *δ*(*x*) || The dirac-delta function |
| *f*(*y*|*x*) ≡ L(*x*|*y*) || The likelihood, i.e., the prior probability density of observing *Y* = *y* given *x* |

*Optimization*

 
| ![art](images/Art_P25.jpg) || Target function we want maximize |
| --- | --- |
| ![art](images/Art_P26.jpg) || First derivative of a function |
| ![art](images/Art_P27.jpg) || Second derivative of a function |
| ![art](images/Art_P28.jpg) || The values of ***θ*** that maximize ![art](images/Art_P29.jpg) |
| ![art](images/Art_P30.jpg) || The maximal value of ![art](images/Art_P31.jpg) |
| ***θ^∗*** || An optimal value |
| *d* || Search direction |
| *λ* || Scale factor for the search direction |
| ![art](images/Art_P32.jpg) || An indicator vector for which all values are equal to 0, except the *i*^(th), which is equal to one |

*Sampling*

 
| ***θ*** || Vector of parameters |
| --- | --- |
| *q*(***θ′***|***θ***) || Proposal distribution describing the probability of moving to ***θ′*** from ***θ*** |
| ![art](images/Art_P33.jpg) || Target distribution from which we want to draw samples |
| *α* || Acceptance probability |
| *β* || Acceptance rate |
| ![art](images/Rcap.jpg) || Estimated potential scale reduction |

*Utility & Decisions*

 
| **A** = {**a[1]**, ⋯ , **a[A]**} || A set of possible actions |
| --- | --- |
| *x* ∈ ![art](images/Art_P34.jpg)⊆ ![art](images/Art_P35.jpg) || An outcome from a set of discrete states |
| *L* || A lottery |
| ![art](images/Art_P36.jpg)(*a, x*) || Utility given a state *x* and an action *a* |
| ![art](images/Art_P37.jpg) || Expected utility conditional on an action *a* |
| ![art](images/Art_P38.jpg) || Long-term expected utility conditional on a current state *s* and that a policy *π* is followed |
| *π*(*s*) || A policy defining an action *a* to take, conditional on a state *s* |
| *r*(*s, a, s′*) || The reward for being in state *s*, taking the action *a* and ending in state *s′* |
| ![art](images/Art_P40.jpg) || Action-utility function |
| *γ* || Discount factor |
| *α* || The learning rate |
| *ϵ* || The probability that an agent takes a random action rather than following the policy *π*(*s*) |
| *←* || An assignment in a recurrent equation, e.g., *x* ← 2*x* |

*Abbreviations*

 
| AI || Artificial intelligence |
| --- | --- |
| BN || Bayesian network |
| CDF || Cumulative distribution function |
| CLT || Central limit theorem |
| CMF || Cumulative mass function |
| CPT || Conditional probability table |
| CV || Cross-validation |
| DAG || Directed acyclic graph |
| DBN || Dynamic Bayesian network |
| e.g. || For example |
| EM || Expectation maximization |
| EPSR || Estimated potential scale reduction |
| FCNN || Fully connected feedforward neural network |
| GA || Gradient ascent |
| GMM || Gaussian mixture model |
| GP || Gaussian process |
| GPC || Gaussian process classification |
| GPR || Gaussian process regression |
| GPU || Graphical processing unit |
| HMM || Hidden Markov model |
| i.e. || That is |
| iid || Independent identically distributed |
| KF || Kalman filter |
| KS || Kalman smoother |
| LDA || Linear discriminant analysis |
| LLOCV || Leave-one-out cross-validation |
| MAP || Maximum a-posteriori |
| MCMC || Markov chain Monte Carlo |
| MDP || Markov decision process |
| ML || Machine learning |
| MLE || Maximum likelihood estimate |
| NB || Naïve Bayes |
| NN || Neural network |
| NR || Newton-Raphson |
| PCA || Principal component analysis |
| PDF || Probability density function |
| PMF || Probability mass function |
| POMDP || Partially observable Markov decision process |
| PSD || Positive semi-definite |
| QDA || Quadratic discriminant analysis |
| RL || Reinforcement learning |
| R.V. || Random variable |
| SKF || Switching Kalman filter |
| SSM || State-space model |
| sym. || Symmetric |
| TD || Temporal difference |
| VOI || Value of information |
| VPI || Value of perfect information |

 

[*1*](#toc.xhtml#intr-1)

[*Introduction*](#toc.xhtml#intr-1)

**Civil engineering examples**

*Geotechnics*: From a set of discrete observations of soil resistances measured across space, we want to predict the resistance for other unobserved locations.

*Environment*: For a lake, we want to build a model linking the effect of temperature and the usage of fertilizers with the prevalence of cyanobacteria, fish mortality, and water color.

*Transportation*: We want to predict the demand for public transportation services from multiple heterogeneous data sources such as surveys and transit card usage.

*Structures*: From observations made on the displacement of a structure over time, we want to detect the presence of anomalies in its behavior.

*Machine learning* (ML) describes a family of methods that allows learning from data what relationships exist between quantities of interest. The goal of learning relationships between quantities of interest is to gain information about how a system works and to make predictions for unobserved quantities. This new knowledge can then be employed to support decision making.

Learning from data is not new in the field of engineering. As depicted in [figure 1.1a](#introduction001.xhtml#Fig_1-1), without machine learning, the task of learning is typically the role of the engineer, who has to figure out the relationships between the variables in a data set, then build a hard-coded model of the system, and then return predictions by evaluating this model with the help of a computer. The issue with *hard-coding* rules and equations is that it becomes increasingly difficult as the number of factors considered increases. [Figure 1.1b](#introduction001.xhtml#Fig_1-1) depicts how, with machine learning, the role of the human is now shifted from learning to programming the computer so it can learn. The question is, How do we program a *computer to learn*? The quick answer is this: by defining a generic model that can be adapted to a wide array of problems by changing its parameters and variables. For most machine learning methods, *learning* consists in inferring these *parameters* and *variables* from data. Notwithstanding the specificities for reinforcement learning that we will cover later, the big picture is the following: learning about parameters and variables is done by quantifying, for a given set of their values, how good the model is at predicting observed data. This task typically leads to nonunique solutions, so we have to make a choice: either pick a single set of values (that is, those leading to the best predictions) or consider all possible values that are compatible with data. In [figure 1.1b](#introduction001.xhtml#Fig_1-1), the dashed arrow represents the practical reality where ML typically relies on a human decision for the selection of a particular mathematical method adapted to a given data set and problem.

**Note:** For a generic model *y* = *g*(*x*; *θ*), *x* and *y* are the input and output *variables* of interest that are evaluated by the model. *θ* is a *parameter* characterizing the model behavior.

![art](images/Art_P41.jpg)

Figure 1.1: Comparison of how, in the context of engineering, relationships are learned from data with and without using machine learning.

 

One term often employed together with machine learning is *artificial intelligence* (AI). ML and AI are closely interconnected, yet they are not synonyms. In its most general form, artificial intelligence consists in the reproduction of an intelligent behavior by a machine. AI typically involves a system that can perceive and interact dynamically with its environment through the process of making *rational decisions*. Note that such an AI system does not have to take a physical form; in most cases it is actually only a computer program. In AI systems, decisions are typically not hard-coded or learned by imitation; instead, the AI system chooses actions with the goal of maximizing an objective function that is given to it. Behind such an AI system that interacts with its environment are machine learning methods that allow extracting information from observations, predict future system responses, and choose the optimal action to take. As depicted in the Venn diagram in [figure 1.2](#introduction001.xhtml#Fig_1-2), machine learning is part of the field of artificial intelligence.

![art](images/Art_P42.jpg)

Figure 1.2: The field of artificial intelligence (AI) includes the field of machine learning (ML).

Now, going back to machine learning, why opt for a *probabilistic* approach to it? It is because the task of learning is intrinsically uncertain. Uncertainties arise from the imperfect models employed to learn from data, because data itself often involves imperfect observations. Therefore, probabilities are at the core of machine learning methods for representing the uncertainty associated with our lack of knowledge. If we do not want to use machine learning as a black box, but instead to understand how it works, going through the probabilistic path is essential.

In machine learning, there are three main subfields: supervised learning, unsupervised learning, and reinforcement learning. *Supervised learning* applies in the context where we want to build a model describing the relationships between the characteristics of a *system* defined by *covariates* and observed system responses that are typically either continuous values or categories. With *unsupervised learning*, the objective is to discover structures, patterns, subgroups, or even anomalies without knowing what the right answer is because the target outputs are not observed. The third subfield is *reinforcement learning*, which involves more abstract concepts than supervised and unsupervised learning. Reinforcement learning deals with sequential decision problems where the goal is to learn the optimal action to choose, given the knowledge that a system is in a particular state. Take the example of infrastructure maintenance, where, given the state of a structure today, we must choose between performing maintenance or doing nothing. The key is that there is no data to train on with respect to the decision-making behavior that the computer should reproduce. With reinforcement learning, the goal is to identify a *policy* describing the optimal action to perform for each possible state of a system in order to maximize the long-term accumulation of rewards. Note that the classification of machine learning methods within supervised, unsupervised, and reinforcement learning has limitations. For many methods, the frontiers are blurred because there is an overlap between more than one ML subfield with respect to the mathematical formulations employed as well as the applications.

**Note:** We employ the generic term *system* to refer to either a single object or many interconnected objects that we want to study. We use the term *covariates* for variables describing the characteristics or the properties of a system.

*This book is intended to help making machine learning concepts accessible to civil engineers who do not have a specialized background in statistics or in computer science.* The goal is to dissect and simplify, through a step-by-step review, a selection of key machine learning concepts and methods. At the end, the reader should have acquired sufficient knowledge to understand dedicated machine learning literature from which this book borrows and thus expand on advanced methods that are beyond the scope of this introductory work.

The diagram in [figure 1.3](#introduction001.xhtml#Fig_1-3) depicts the organization of this book, where arrows represent the dependencies between different chapters. Colored regions indicate to which machine learning subfield each chapter belongs. Before introducing the fundamentals associated with each machine learning subfield in [Parts II](#part002.xhtml)–[V](#part005.xhtml), [Part I](#part001.xhtml) covers the *background* knowledge required to understand machine learning. This background knowledge includes *linear algebra* ([chapter 2](#chapter001.xhtml)), where we review how to harness the potential of matrices to describe systems; *probability theory* ([chapter 3](#chapter002.xhtml)) and *probability distributions* ([chapter 4](#chapter003.xhtml)) to describe our incomplete knowledge; and *convex optimization* ([chapter 5](#chapter004.xhtml)) as a first method for allowing a computer to learn about model parameters.

![art](images/Art_P43.jpg)

Figure 1.3: Each square node describes a chapter, and arrows represent the dependencies between chapters. Shaded regions group chapters into the five parts of the book. Note that at the beginning of each part, this diagram is broken down into subparts in order to better visualize the dependencies between the current and previous chapters.

[Part II](#part002.xhtml) first covers *Bayesian estimation* ([chapter 6](#chapter005.xhtml)), which is behind the formulation of supervised and unsupervised learning problems. Second, it covers *Markov chain Monte Carlo* (MCMC) methods ([chapter 7](#chapter006.xhtml)), allowing one to perform Bayesian estimation in complex cases for which no analytical solution is available.

[Part III](#part003.xhtml) explores methods and concepts associated with supervised learning. [Chapter 8](#chapter007.xhtml) covers regression methods, where the goal is to build models describing continuous-valued system responses as a function of covariates. [Chapter 9](#chapter008.xhtml) presents classification methods, which are analogous to regression except that the system responses are categories rather than continuous values.

[Part IV](#part004.xhtml) introduces the notions associated with unsupervised learning, where the task is to build models that can extract the underlying structure present in data without having access to direct observations of what this underlying structure should be. In [chapter 10](#chapter009.xhtml), we first approach unsupervised learning through *clustering* and *dimension reduction*. For clustering, the task is to identify subgroups within a set of observed covariates for which we do not have access to the subgroup labels. The role of dimension reduction is, as its name implies, to reduce the number of dimensions required to represent data while minimizing the loss of information. [Chapter 11](#chapter010.xhtml) presents *Bayesian networks*, which are graph-based probabilistic methods for modeling dependencies within and between systems through their joint probability. [Chapter 12](#chapter011.xhtml) presents *state-space models*, which allow creating probabilistic models for time-dependent systems using sequences of observations. Finally, [chapter 13](#chapter012.xhtml) presents how we can employ the concepts of probabilistic inference for the purpose of *model calibration*. Model calibration refers to the task of using observations to improve our knowledge associated with hard-coded mathematical models that are commonly employed in engineering to describe systems. This application is classified under the umbrella of *unsupervised learning* because, as we will see, the main task consists in inferring hidden-state variables and parameters, for which observations are not available.

[Part V](#part005.xhtml) presents the fundamental notions necessary to define reinforcement learning problems. First, [chapter 14](#chapter013.xhtml) presents how rational decisions are made in uncertain contexts using the *utility theory*. [Chapter 15](#chapter014.xhtml) presents how to extend rational decision making to a sequential context using the *Markov decision process* (MDP). Finally, building on the MDP theory, we introduce the fundamental concepts of *reinforcement learning*, where a virtual agent learns how to take optimal decisions through trial and error while interacting with its environment.

 

 

[**Part I**](#toc.xhtml#part-1)

[**Background**](#toc.xhtml#part-1)

![art](images/Art_P44.jpg)

 

 

[*2*](#toc.xhtml#chap-1)

[*Linear Algebra*](#toc.xhtml#chap-1)

*Linear algebra* is employed in a majority of machine learning methods and algorithms. Before going further, it is essential to understand the mathematical notation and basic operations.

 

[*2.1   Notation*](#toc.xhtml#Rh1-1)

 
| *x* || : || scalar variable |
| --- | --- | --- |
| **x** || : || column vector |
| **X** || : || matrix |
| *x[i]* ≡ \[**x**\]*[i]* || : || *i*^(th) element of a vector |
| *x[ij] ≡* \[**X**\]*[ij]* || : || {*i, j*}^(th) element of a matrix |

Examples of variables *x* belonging to different domains

| *x* || ∈ || ℝ || ≡ (−∞, ∞) |
| --- | --- | --- | --- |
|  || ∈ || ℝ^+ || ≡ (0, ∞) |
|  || ∈ || ℤ || ≡ {⋯ , −1, 0, 1, 2, ⋯ } |

We employ lowercase letters *x, s, v,* ⋯ in order to describe variables that can lie in specific domains such as real numbers ℝ, real positive ℝ^+, integers ℤ, closed intervals \[*·, ·*\], open intervals (*·, ·*), and so on. Often, the problems studied involve multiple variables that can be regrouped in arrays. A 1-D array or *vector* containing scalars is represented as

![art](images/Art_P45.jpg)

By convention, a vector **x** implicitly refers to a *n* × 1 column vector. For example, if each element *x[i]* ≡ \[**x**\]*[i]* is a real number \[**x**\][*i*] ∈ ℝ for all *i* from 1 to *n*, then the vector belongs to the *n*\-dimensional real domain ℝ*^n*. This last statement can be expressed mathematically as \[**x**\]*[i]* ∈ ℝ, ∀*i* ∈ {1 : *n*} → **x** ∈ ℝ*^n*. In machine learning, it is common to have 2-D arrays or *matrices*,

![art](images/Art_P46.jpg)

where, for example, if each *x[ij]* ≡ \[**X**\]*[ij]* ∈ ℝ, ∀*i* ∈ {1 : *m*}, *j* ∈ {1 : *n*} → **X** ∈ ℝ^(*m*×*n*). Arrays beyond two dimensions are referred to as *tensors*. Although tensors are widely employed in the field of *neural networks*, they will not be treated in this book.

 

There are several matrices with specific properties: A diagonal matrix is square and has only terms on its main diagonal,

![art](images/Art_P47.jpg)

An identity matrix **I** is similar to a diagonal matrix except that elements on the main diagonal are 1, and 0 everywhere else,

![art](images/Art_P48.jpg)

A *block diagonal* matrix concatenates several matrices on the main diagonal of a single matrix,

![art](images/Art_P50.jpg)

![art](images/Art_P49.jpg)

We can manipulate the dimensions of matrices using the *transposition* operation so that indices are permuted \[**X^(**T**)**\]*[ij]* = \[**X**\]*[ji]*. For example,

![art](images/Art_P51.jpg)

The *trace* of a square matrix **X** corresponds to the sum of the elements on its main diagonal,

![art](images/Art_P52.jpg)

 

[*2.2   Operations*](#toc.xhtml#Rh1-2)

In the context of machine learning, linear algebra is employed because of its capacity to model *linear systems of equations* in a format that is compact and well suited for computer calculations. In a 1-D case, such as the one represented in [figure 2.1](#chapter001.xhtml#Fig_2-1), the *x* space is *mapped* into the *y* space, ℝ *→* ℝ, through a linear (i.e., *affine*) function. [Figure 2.2](#chapter001.xhtml#Fig_2-2) presents an example of a 2-D linear function where the x space is *mapped* into the *y* space, ℝ²*→* ℝ. This can be generalized to linear systems **y** = **Ax** + **b**, defining a mapping so that ℝ*^n* → ℝ*^m*, where **x** and **y** are respectively *n* × 1 and *m* × 1 vectors. The product of the matrix **A** with the vector **x** is defined as \[**Ax**\]*[i]* = ∑[*j*]\[**A**\][*ij*] · \[**x**\][*j*].

![art](images/Art_P53.jpg)

Figure 2.1: 1-D plot representing a linear system, *y* = *ax* + *b*.

![art](images/Art_P54.jpg)

Figure 2.2: 2-D plot representing a linear system, *y* = **a^(**T**)x** + *b*.

In more general cases, linear algebra is employed to multiply a matrix **A** of size *n* × *k* with another matrix **B** of size *k* × *m*, so the result is a *n* × *m* matrix,

| **C** || \= || **AB** |
| --- | --- | --- |
|  || \= || **A** × **B**. |

The *matrix multiplication* operation follows \[**C**\]*[ij]* = ∑[*k*]\[**A**\][*ik*] · \[**B**\][*kj*], as illustrated in [figure 2.3](#chapter001.xhtml#Fig_2-3). Following the requirement on the size of the matrices multiplied, this operation is not generally commutative so that **AB** ≠ **BA**. Matrix multiplication follows several properties such as the following:

 
| Distributivity || **A**(**B** + **C**) || \= || **AB** + **AC** |
| --- | --- | --- | --- |
| Associativity || **A**(**BC**) || \= || (**AB**)**C** |
| Conjugate transposability || (**AB**)^T || \= || **B**^T **A**^T. |

![art](images/Art_P55.jpg)

Figure 2.3: Example of matrix multiplication operation **C** = **AB**.

When the matrix multiplication operator is applied to *n* × 1 vectors, it reduces to the *inner product*,

![art](images/Art_P56.jpg)

Another common operation is the *Hadamar product* or *element-wise product*, which is represented by the symbol ⊙. It consists in multiplying each term from matrices **A**[*m*×*n*] and **B**[*m*×*n*] in order to obtain **C**[*m*×*n*],

 
| **C** || \= || **A** ⊙ **B** |
| --- | --- | --- |
| \[**C**\]*[ij]* || \= || \[**A**\]*[ij]* · \[**B**\]*[ij]*. |

The element-wise product is seldom employed to define mathematical equations; however, it is extensively employed when implementing these equations in a computer language. Matrix addition is by definition an element-wise operation that applies only to matrices of same dimensions,

 
| **C** || \= || **A** + **B** |
| --- | --- | --- |
| \[**C**\]*[ij]* || \= || \[**A**\]*[ij]* + \[**B**\]*[ij].* |

One last key operation is the *matrix inversion* **A**^(−1). In order to be invertible, a matrix must be square and must not have *linearly dependent* rows or columns. The product of a matrix with its inverse is equal to the identity matrix **A**^(−1)**A** = **I**. Matrix inversion is particularly useful for solving linear systems of equations,

 

 
| **Ax** || \= || **b**, |
| --- | --- | --- |
| **A**^(−1)**Ax** || \= || **A**^(−1)**b**, |
| **Ix** || \= || **A**^(−1)**b**, |
| **x** || \= || **A**^(−1)**b**. |

**Linearly dependent vectors**

Vectors **x**[1] ∈ **R***^n* and **x**[2] ∈ **R***^n* are *linearly dependent* if a nonzero vector **y** ∈ **R**² exists, such that *y*[1]**x**[1] + *y*[2]**x**[2] = **0**.

 

[*2.3   Norms*](#toc.xhtml#Rh1-3)

Norms measure how large a vector is. In a generic way, the *L^p*\-norm is defined as

![art](images/Art_P58.jpg)

Special cases of interest are

![art](images/Art_P59.jpg)

These cases are illustrated in [figure 2.4](#chapter001.xhtml#Fig_2-4). Among all cases, the *L*²\-norm (Euclidian distance) is the most common. For example, [§8.1.1](#chapter007.xhtml#Sec_8.1.1) presents for the context of linear regression how choosing a Euclidian norm to measure the distance between observations and model predictions allows solving the parameter estimation problem analytically.

![art](images/Art_P57.jpg)

Figure 2.4: Examples of applications of different norms for computing the length of a vector **x**.

 

[*2.4   Transformations*](#toc.xhtml#Rh1-4)

Machine learning involves transformations from one space to another. In the context of linear algebra, we are interested in the special case of linear transformations.

 

[*2.4.1   Linear Transformations*](#toc.xhtml#Rh2-2)

[Figure 2.1](#chapter001.xhtml#Fig_2-1) presented an example for a ℝ → ℝ linear transformation. More generally, a *n* × *n* square matrix can be employed to perform a ℝ*^n* → ℝ*^n* linear transformation through multiplication. [Figures 2.5a–c](#chapter001.xhtml#Fig_2-5) illustrate how a matrix **A** transforms a space x into another **x**′ using the matrix product operation **x**′ = **Ax**. The deformation of the circle and the underlying grid (see (a)) show the effect of various transformations. Note that the terms on the main diagonal of **A** control the transformations along the ![art](images/Art_P60.jpg)and ![art](images/Art_P61.jpg)axes, and the nondiagonal terms control the transformation dependency between both axes, (see, for example, [figure 2.6](#chapter001.xhtml#Fig_2-6)).

![art](images/Art_P62.jpg)

Figure 2.5: Examples of linear transformations **x**′ = **Ax**.

![art](images/Art_P63.jpg)

Figure 2.6: Example of eigen decomposition, **A** = **V**diag(***λ***)**V**^(−1).

The *determinant* of a square matrix A measures how much the transformation contracts or expands the space:

*   det(**A**) = 1: preserves the space/volume
*   det(**A**) = 0: collapses the space/volume along a subset of dimensions, for example, 2-D space → 1-D space (see [figure 2.7](#chapter001.xhtml#Fig_2-7)) 
    
    ![art](images/Art_P64.jpg)
    
    Figure 2.7: Example of a nearly singular transformation.
    

In the examples presented in [figure 2.5a–c](#chapter001.xhtml#Fig_2-5), the determinant quantifies how much the area/volume is changed in the transformed space; for the circle, it corresponds to the change of area caused by the transformation. As shown in [figure 2.5a](#chapter001.xhtml#Fig_2-5), if **A** = **I**, the transformation has no effect so det(**A**) = 1. For a square matrix \[**A**\][*n*×*n*], det(**A**) : ℝ^(*n*×*n*) → ℝ.

 

[*2.4.2   Eigen Decomposition*](#toc.xhtml#Rh2-3)

Linear transformations operate on several dimensions, such as in the case presented in [figure 2.6](#chapter001.xhtml#Fig_2-6) where the transformation introduces dependency between variables. *Eigen decomposition* enables finding a linear transformation that removes the dependency while preserving the area/volume. A square matrix \[**A**\]*[n×n]* can be decomposed in *eigenvectors* {***ν***[1], ⋯ , ***ν****[n]*} and *eigenvalues* {*λ*[1], ⋯ , *λ[n]*}. In its matrix form,

**A** = **V**diag(**λ**)**V**^(−1),

where

 
| **V** || \= || \[***ν***[1] ⋯ ***ν**[n]*\] |
| --- | --- | --- |
| **λ** || \= || \[*λ*[1] ⋯ *λ[n]*\]^T. |

[Figure 2.6](#chapter001.xhtml#Fig_2-6) presents the eigen decomposition of the transformation **x**′ = **Ax**. Eigenvectors ***ν***[1] and ***ν***[2] describe the new referential into which the transformation is independently applied to each axis. Eigenvalues *λ*[1] and *λ*[2] describe the transformation magnitude along each eigenvector.

A matrix is *positive definite* if all eigenvalues *\>* 0, and a matrix is *positive semidefinite* (PSD) if all eigenvalues ≥ 0. The determinant of a matrix corresponds to the product of its eigenvalues. Therefore, in the case where one eigenvalue equals zero, it indicates that two or more dimensions are linearly dependent and have collapsed into a single one. The transformation matrix is then said to be *singular*. [Figure 2.7](#chapter001.xhtml#Fig_2-7) presents an example of a nearly singular transformation. For a positive semidefinite matrix **A** and for any vector x, the following relation holds:

**x^TAx** ≥ 0.

This property is employed in [§3.3.5](#chapter002.xhtml#Sec_3.3.5) to define the requirements for an admissible covariance matrix.

A more exhaustive review of linear algebra can be found in dedicated textbooks such as the one by Kreyszig.^([1](#chapter001.xhtml#footnote_1))

 

 

*Exercises*

| P2.1 || Calculate the Euclidian, Manhattan, and max norm for the vector **x** = \[1 4 2 7 4\]^(**T**). |
| --- | --- |
| P2.2 || Reformulate the two equations 2*x*[1] + 6*x*[2] = 8 and 5*x*[1] + *x*[2] = 0 as a system of linear equations, and solve it for \[*x*[1]*x*[2]\]^(**T**) using linear algebra. |
| P2.3 || Draw the result of transforming a unit radius circle through the function **x**′ = **Ax** + **b**, where ![art](images/Art_P65.jpg). |
| P2.4 || For the transformation in P2.3, calculate the eigen decomposition for the matrix **A**, and plot the deformed unit circle in a set of axes corresponding to the eigenvectors. |
| P2.5 || Identify which matrix is positive semidefinite: ![art](images/Art_P66.jpg). |

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter001.xhtml#footnote_ref_1) Kreyszig, E. (2011). *Advanced engineering mathematics* (10th ed.). Wiley.

 

[*3*](#toc.xhtml#chap-2)

[*Probability Theory*](#toc.xhtml#chap-2)

The interpretation of probability theory employed in this book follows Laplace’s view of “*common sense reduced to calculus*.” It means that probabilities describe our state of knowledge rather than intrinsically *aleatory* phenomena. In practice, few phenomena are actually intrinsically unpredictable. Take, for example, a coin as displayed in [figure 3.1](#chapter002.xhtml#Fig_3-1). Whether a coin toss results in either heads or tails has nothing to do with an inherently aleatory process. The outcome appears unpredictable because of the *lack of knowledge* about the coin’s initial position, speed, and acceleration. If we could gather information about the coin’s initial kinematic conditions, the outcome would become predictable. Devices that can throw coins with repeatable initial kinematic conditions will lead to repeatable outcomes.

![art](images/Art_P67.jpg)

“La théorie des probabilités n’est, au fond, que le bon sens réduit au calcul; elle fait apprécier avec exactitude ce que les esprits justes sentent par une sorte d’instinct”

— Pierre-Simon, marquis de Laplace (1749–1827)

 

![art](images/Art_P68.jpg)

Figure 3.1: A coin toss illustrates the concept of epistemic uncertainty.

(Photo: Michel Goulet)

[Figure 3.2](#chapter002.xhtml#Fig_3-2) presents another example where we consider the *elastic modulus*^([1](#chapter002.xhtml#footnote_1)) *E* at one specific location in a dam. Notwithstanding long-term effects such as *creep*,^([2](#chapter002.xhtml#footnote_2)) at any given location, *E* does not vary with time: *E* is a deterministic, yet unknown constant. Probability is employed here as a tool to describe our incomplete knowledge of that constant.

![art](images/Art_P69.jpg)

Figure 3.2: The concrete elastic modulus *E* at a given location is an example of deterministic, yet unknown quantity. The possible values for *E* can be described using the probability theory.

There are two types of uncertainty: *aleatory* and *epistemic*. aleatory uncertainty is characterized by its *irreducibility*; no information can either reduce or alter it. Alternately, epistemic uncertainty refers to a lack of knowledge that can be altered by new information. In an engineering context, aleatory uncertainties arise when we are concerned with future realizations that have yet to occur. Epistemic uncertainty applies to any other case dealing with deterministic, yet unknown quantities.

This book approaches machine learning using probability theory because in many practical engineering problems, the number of observations available is limited, from a few to a few thousand. In such a context, the amount of information available is typically insufficient to eliminate epistemic uncertainties. When large data sets are available, probabilistic and deterministic methods may lead to indistinguishable results; the opposite occurs when little data is available. Therefore, *the less we know about it, the stronger the argument for approaching a problem using probability theory*.

In this chapter, a review of *set theory* lays the foundation for *probability theory*, where the central part is the concept of *random variables*. Machine learning methods are built from an ensemble of functions organized in a clever way. Therefore, the last part of this chapter looks at what happens when random variables are introduced into deterministic functions.

For specific notions related to probability theory that are outside the scope of this chapter, the reader should refer to dedicated textbooks such as those by Box and Tiao;^([3](#chapter002.xhtml#footnote_3)) Ang and Tang.^([4](#chapter002.xhtml#footnote_4))

 

[*3.1   Set Theory*](#toc.xhtml#Rh1-5)

**Set:** Ensemble of events or elements.

**Universe/sampling space** (S)**:** Ensemble of all possible events.

**Elementary event** (*x*)**:** A single event, *x* ∈ S.

**Event** (E)**:** Ensemble of elementary events.

| *E* ⊂ S ||    : Subset of S |
| --- | --- |
| *E* = S ||    : Certain event |
| *E* = *∅* ||    : Impossible event |
| *E* ||    : Complement of *E* |

**Union** (“or”)

*E*[1] ∪ *E*[2]

**Intersection** (“and”)

*E*[1] ∩ *E*[2] ≡ *E*[1]*E*[2]

**Commutativity**

![art](images/Art_P70.jpg)

**Associativity**

(*E*[1]∪*E*[2])∪*E*[3] = *E*[1]∪(*E*[2]∪*E*[3]) = *E*[1]∪*E*[2]∪*E*[3]

**Distributivity**

*E*[1](*E*[2] ∪ *E*[3]) = (*E*[1]*E*[2] ∪ *E*[1]*E*[3])

A *set* describes an ensemble of *elements*, also referred to as *events*. An *elementary* event *x* refers to a single event among a *sampling space* (or *universe*) denoted by the calligraphic letter S. By definition, a sampling space contains all the possible events, *E* ⊆ S. The special case where an event is equal to the sampling space, *E* = S, is called a *certain event*. The opposite, *E* = ∅, where an event is an empty set, is called a *null event*. *E* refers to the complement of a set, that is, all elements belonging to S and not to *E*. [Figure 3.3](#chapter002.xhtml#Fig_3-3) illustrates these concepts using a *Venn diagram*.

![art](images/Art_P71.jpg)

Figure 3.3: Venn diagram representing the sampling space S, an event *E*, its complement *E*, and an elementary event *x*.

Let us consider the example,^([5](#chapter002.xhtml#footnote_5)) of the state of a structure following an earthquake, which is described by a sampling space,

| S || \= || {no damage, light damage, important damage, collapse} |
| --- | --- | --- |
|  || \= || {N, L, I, C}. |

In that context, an event *E*[1] = {N, L} could contain the no damage and light damage events, and another event *E*[2] = {C} could contain only the collapsed state. The complements of these events are, respectively, *E*[1] = {I, C} and *E*[2] = {N, L, I}.

The two main operations for events, *union* and *intersection*, are illustrated in [figure 3.4](#chapter002.xhtml#Fig_3-4). A union is analogous to the “or” operator, where *E*[1] ∪ *E*[2] holds if the event belongs to either *E*[1], *E*[2], or both. The intersection is analogous to the “and” operator, where *E*[1] ∩ *E*[2] ≡ *E*[1]*E*[2] holds if the event belongs to both *E*[1] and *E*[2]. As a convention, intersection has priority over union. Moreover, both operations are *commutative*, *associative*, and *distributive*.

![art](images/Art_P72.jpg)

Figure 3.4: Venn diagrams representing the two basic operations.

Given a set of *n* events {*E*[1], *E*[2], ⋯ , *E[n]*} ∈ S, *E*[1], *E*[2], ⋯ , *E[n]*, the events are *mutually exclusive* if *E[i]E[j]* = ∅, ∀*i* ≠ *j*, that is, if the intersection for any pair of events is an empty set. Events *E*[1], *E*[2], ⋯ , *E[n]* are *collectively exhaustive* if ![art](images/Art_P73.jpg), that is, the union of all events is the sampling space. Events *E*[1], *E*[2], ⋯ , *E[n]* are *mutually exclusive and collectively exhaustive* if they satisfy both properties simultaneously. [Figure 3.5](#chapter002.xhtml#Fig_3-5) presents examples of mutually exclusive (3.5a), collectively exhaustive (3.5b), and mutually exclusive and collectively exhaustive (3.5c–d) events. Note that the difference between (b) and (c) is the absence of overlap in the latter.

![art](images/Art_P75.jpg)

Figure 3.5: Venn diagrams representing the concepts of mutual exclusivity and collective exhaustivity for events.

 

[*3.2   Probability of Events*](#toc.xhtml#Rh1-6)

Pr(*E[i]*) denotes the *probability* of the event *E[i]*. There are two main interpretations for a probability: the *Frequentist* and the *Bayesian*. Frequentists interpret a probability as the number of occurrences of *E[i]* relative to the number of samples *s*, as *s* goes to *∞*,

![art](images/Art_P74.jpg)

For Bayesians, a probability measures how likely is *E[i]* in comparison with other events in S. This interpretation assumes that the nature of uncertainty is epistemic, that is, it describes our knowledge of a phenomenon. For instance, the probability depends on the available knowledge and can change when new information is obtained. Throughout this book we are adopting this Bayesian interpretation.

By definition, the probability of an event is a number between zero and one, 0 ≤ Pr(*E[i]*) ≤ 1. At the ends of this spectrum, the probability of any event in S is one, Pr(S) = 1, and the probability of an empty set is zero, Pr(*∅*) = 0. If two events *E*[1] and *E*[2] are mutually exclusive, then the probability of the events’ union is the sum of each event’s probability. Because the union of an event and its complement are the sampling space, *E* ∪ *E* = S (see [figure 3.5d](#chapter002.xhtml#Fig_3-5)), and because Pr(S) = 1, then the probability of the complement is Pr(*E*) = 1 − Pr(*E*).

When events are not mutually exclusive, the general addition rule for the probability of the union of two events is

Pr(*E*[1] ∪ *E*[2]) = Pr(*E*[1]) + Pr(*E*[2]) − Pr(*E*[1]*E*[2]).

This general addition rule is illustrated in [figure 3.6](#chapter002.xhtml#Fig_3-6), where if we simply add the probability of each event without accounting for the subtraction of Pr(*E*[1]*E*[2]), the probability of the intersection of both events will be counted twice.

![art](images/Art_P76.jpg)

Figure 3.6: Venn diagram representing the addition rule for the probability of events.

 

Pr(*E*[1]*|E*[2]) denotes the probability of the event *E*[1] conditional on the realization of the event *E*[2]. This conditional probability is defined as the joint probability for both events divided by the probability of *E*[2],

![art](images/Art_P77.jpg)

**Note:** Pr(*E*[2]) ≠ 0 on the denominator because a division by 0 is not finite.

The probability of a single event is referred to as a *marginal* probability. A *joint* probability designates the probability of the intersection of events. The terms in equation 3.1 can be rearranged to explicitly show that the joint probability of two events {*E*[1], *E*[2]} is the product of a conditional probability and its associated marginal,

| Pr(*E*[1]*E*[2]) || \= || Pr(*E*[1]*|E*[2]) · Pr(*E*[2]) |
| --- | --- | --- |
|  || \= || Pr(*E*[2]*|E*[1]) · Pr(*E*[1]). |

In cases where *E*[1] and *E*[2] are *statistically independent*, *E*[1] ╨ *E*[2], conditional probabilities are equal to the marginal,

![art](images/Art_P78.jpg)

**Note:** Statistical independence (╨) between a pair of random variables implies that learning about one random variable does not modify our knowledge for the other.

In the special case of statistically independent events, the joint probability reduces to the product of the marginals,

Pr(*E*[1]*E*[2]) = Pr(*E*[1]) · Pr(*E*[2]).

The joint probability for *n* events can be broken down into *n* − 1 conditionals and one marginal probability using the *chain rule*,

| Pr(*E*[1]*E*[2] ⋯ *E[n]*) || \= || Pr(*E*[1]|*E*[2] ⋯ *E[n]*) Pr(*E*[2] ⋯ *E[n]*) |
| --- | --- | --- |
|  || \= || Pr(*E*[1]|*E*[2] ⋯ *E[n]*) Pr(*E*[2]|*E*[3] ⋯ *E[n]*) Pr(*E*[3] ⋯ *E[n]*) |
|  || \= || Pr(*E*[1]|*E*[2] ⋯ *E[n]*) Pr(*E*[2]|*E*[3] ⋯ *E[n]*) ⋯ Pr(*E*[*n*−1]|*E[n]*) Pr(*E[n]*). |

Let us define {*E*[1], *E*[2], *E*[3], ⋯ , *E[n]*} ∈ S, a set of mutually exclusive and collectively exhaustive events, that is, *E[i]E[j]* = ∅, ∀*i* ≠ *j*, ![art](images/Art_P79.jpg)– and an event *A* belonging to the same sampling space, that is, *A* ∈ S. This context is illustrated using a Venn diagram in [figure 3.7](#chapter002.xhtml#Fig_3-7). The probability of the event *A* can be obtained by summing the joint probability of *A* and each event *E[i]*,

![art](images/Art_P80.jpg)

![art](images/Art_P82.jpg)

Figure 3.7: Venn diagram representing the conditional occurrence of events.

This operation of obtaining a marginal probability from a joint is called *marginalization*. The addition rule for the union of *E*[1] ∪ *E*[2] conditional on *A* is

Pr(*E*[1] ∪ *E*[2]|*A*) = Pr(*E*[1]|*A*) + Pr(*E*[2]|*A*) − Pr(*E*[1]*E*[2]|*A*),

and the intersection rule is

Pr(*E*[1]*E*[2]|*A*) = Pr(*E*[1]|*E*[2], *A*) · Pr(*E*[2]|*A*).

Using the definition of a conditional probability in equation 3.1, we can break Pr(*AE[i]*) into two different products of a conditional and its associated marginal probability,

![art](images/Art_P81.jpg)

Reorganizing the right-hand terms of equation 3.3 leads to *Bayes rule*,

![art](images/Art_P83.jpg)

On the left-hand side is the *posterior probability*: the probability of the event *E[i]* given the realization of the event *A*. On the numerator of the right-hand side is the product of the *conditional probability* of the event *A* given the event *E[i]*, times the *prior probability* of *E[i]*. The term on the denominator is referred to as the *evidence* and acts as a normalization constant, which ensures that ∑[*i*] Pr(*E[i]*|*A*) = 1. The normalization constant Pr(*A*) is obtained using the marginalization operation presented in equation 3.2. In practical applications, Pr(*A*) is typically difficult to estimate. [Chapters 6](#chapter005.xhtml) and [7](#chapter006.xhtml) present analytic as well as numerical methods for tackling this challenge. [Figure 3.8](#chapter002.xhtml#Fig_3-8) illustrates the conditional occurrence of events in the context of Bayes rule.

![art](images/Art_P84.jpg)

Figure 3.8: Venn diagram representing the conditional occurrence of events in the context of Bayes rule.

  

[*3.3   Random Variables*](#toc.xhtml#Rh1-7)

Set theory is relevant for introducing the concepts related to probabilities. However, on its own, it has a limited applicability to practical problems that require defining the concept of *random variables*. A random variable is denoted by a capital letter *X*. Contrarily to what its name implies, a random variable is not intended to describe only intrinsically random events; in our case, it describes lack of knowledge. A random variable *X* does not take any specific value. Instead, it takes any value in its valid sampling space *x* ∈ S and, as we will see shortly, the probability of occurrence of each value is typically not equal. Values of *x* are either called *realizations* or *outcomes* and are elementary events that are mutually exclusive and collectively exhaustive. A sampling space S for a random variable can either be *discrete* or *continuous*. Continuous cases are always *infinite*, whereas discrete ones can either be *finite* or *infinite*. [Figure 3.9](#chapter002.xhtml#Fig_3-9) illustrates how the concepts of events and sampling space can be transposed from a Venn diagram representation to the domain of a random variable.

![art](images/Art_P85.jpg)

Figure 3.9: Parallel between a Venn diagram and a continuous domain to represent a random variable.

 

[*3.3.1   Discrete Random Variables*](#toc.xhtml#Rh2-4)

**Notation**

 
| *X* : || Random variable |
| --- | --- |
| *x* : || Realization of *X* |
| *p[X]*(*x*) : || Probability that *X* = *x* |

In the case where S is a discrete domain, the probability that *X* = *x* is described by a *probability mass function* (PMF). In terms of notation Pr(*X* = *x*) ≡ *p[X]*(*x*) ≡ *p*(*x*) are all equivalent. Moreover, we typically describe a random variable by defining its sampling space and its probability mass function so that *x* : *X* ~ *p[X]*(*x*). The symbol ~ reads as *distributed like*. Analogously to the probability of events, the probability that *X* = *x* must be

0 ≤ *p[X]*(*x*) ≤ 1,

and the sum of the probability for all *x* ∈ S follows

![art](images/Art_P86.jpg)

For the post-earthquake structural safety example introduced in [§3.1](#chapter002.xhtml#Sec_3.1), where

![art](images/Art_P87.jpg)

the sampling space along with the probability of each event can be represented by a probability mass function as depicted in [figure 3.10](#chapter002.xhtml#Fig_3-10).

![art](images/Art_P88.jpg)

Figure 3.10: Representation of a sampling space for a discrete random variable.

 

The event corresponding to damages that are either light or important corresponds to L ∪ I ≡ {1 ≤ *x* ≤ 2}. Because the events *x* = 1 and *x* = 2 are mutually exclusive, the probability

| Pr(L ∪ I) || \= || Pr({1 ≤ *X* ≤ 2}) |
| --- | --- | --- |
|  || \= || *p[X]*(*x* = 1) + *p[X]*(*x* = 2). |

The probability that *X* takes a value less than or equal to *x* is described by a *cumulative mass function* (CMF),

![art](images/Art_P89.jpg)

[Figure 3.11](#chapter002.xhtml#Fig_3-11) presents on the same graph the *probability mass function* (PMF) and the cumulative mass function. As its name indicates, the CMF corresponds to the cumulative sum of the PMF. Inversely, the PMF can be obtained from the CMF following

*p[X]*(*x[i]*) = *F[X]*(*x[i]*) − *F[X]*(*x*[*i*−1]).

![art](images/Art_P90.jpg)

Figure 3.11: Comparison of a probability *p[X]*(*x*) and a cumulative *F[X]*(*x*) mass function.

 

[*3.3.2   Continuous Random Variables*](#toc.xhtml#Rh2-5)

The concepts presented for discrete sampling spaces can be extended for cases where S is a continuous domain. Because continuous domains are inevitably infinite, the probability that a random variable takes a specific value *X* = *x* is zero,

Pr(*X* = *x*) = 0.

**Note:** Here, the probability equal to zero does not mean that a specific value *x* is impossible. Take, for example, a random variable defined in the interval (0, 1), for which all the outcomes are equally probable. The probability that *X* = 0.23642 is only one out of an infinite number of possibilities in (0, 1).

For continuous random variables, the probability is only defined for intervals *x < X* ≤ *x* + Δ*x*,

Pr(*x* < *X* ≤ *x* + Δ*x*) = *f[X]*(*x*)Δ*x*,

where *f[X]*(*x*) ≡ *f*(*x*) denotes a *probability density function* (PDF). A PDF must always be greater than or equal to zero *f[X]*(*x*) *≥* 0; however, unlike for the discrete case where 0 ≤ *p[X]*(*x*) ≤ 1, *f[X]*(*x*) can take values greater than one because it describes a *probability density* rather than a *probability*. In order to satisfy the property that Pr(S) = 1, the integral of *f[X]*(*x*) over all possible values of *x* must be one,

![art](images/Art_P91.jpg)

The probability that Pr(*X* ≤ *x*) is given by the *cumulative density function* (CDF),

![art](images/Art_P92.jpg)

 

For a random variable *x* ∈ ℝ : *X ~ f[X]*(*x*), the CDF evaluated at the lower and upper bounds is, respectively, *F[X]*(*−∞*) = 0 and *F[X]*(+*∞*) = 1. Notice that the CDF is obtained by integrating the PDF, and inversely, the PDF is obtained by differentiating the CDF,

![art](images/Art_P93.jpg)

Moreover, because *F[X]*(*x*) is the integral of *f[X]*(*x*) and *f[X]*(*x*) *≥* 0, *F[X]*(*x*) is *nondecreasing*. [Figure 3.12](#chapter002.xhtml#Fig_3-12) presents examples of probability density and cumulative distribution function.

![art](images/Art_P94.jpg)

Figure 3.12: Examples of PDF and CDF for a continuous random variable.

 

[*3.3.3   Conditional Probabilities*](#toc.xhtml#Rh2-6)

Conditional probabilities describe the probability of a random variable’s outcomes, given the realization of another variable. The conditional notation for discrete random variables follows

![art](images/Art_P95.jpg)

and the conditional notation for continuous random variables follows,

![art](images/Art_P96.jpg)

Conditional probabilities are employed in Bayes rule to infer the posterior knowledge associated with a random variable, given the observations made for another.

Let us revisit the post-earthquake structural safety example introduced in [§3.1](#chapter002.xhtml#Sec_3.1), where the damage state *x* ∈ S. If we measure the *peak ground acceleration* (PGA) after an earthquake *y* ∈ ℝ^+, we can employ the conditional probability of having structural damage given the PGA value to infer the structural state of a building that itself has not been observed. [Figure 3.13](#chapter002.xhtml#Fig_3-13) illustrates schematically how an observation of the peak ground acceleration *y* can be employed to infer the structural state of a building *x*, using conditional probabilities. Because the structural state *X* is a discrete random variable, *p*(*x*|*y*) describes the posterior probability of each state *x* ∈ S, given an observed value of PGA *y* ∈ ℝ^+. *f*(*y*) is a normalization constant obtained by marginalizing *X* from *f*(*x, y*) and evaluating it for the particular observed value *y*,

![art](images/Art_P98.jpg)

*Peak ground acceleration* is a metric quantifying the intensity of an earthquake using the maximal acceleration recorded during an event.

 

![art](images/Art_P97.jpg)

Figure 3.13: Schematic example of how observations of the peak ground acceleration *y* can be employed to infer the structural state of a building *x* using conditional probabilities.

The posterior is obtained by multiplying the likelihood of observing the particular value of PGA *y* given each of the structural states *x*, times the prior probability of each structural state, and then dividing by the probability of the observation *y* itself. Conditional probabilities can be employed to put in relation any combination of continuous and discrete random variables. [Chapter 6](#chapter005.xhtml) further explores Bayesian estimation with applied examples.

 

[*3.3.4   Multivariate Random Variables*](#toc.xhtml#Rh2-7)

It is common to study the joint occurrence of multiple phenomena. In the context of probability theory, it is done using multivariate random variables. **x** = \[*x*[1]*x*[2] ⋯ *x[n]*\]^(**T**) is a vector (column) containing realizations for *n* random variables **X** = \[*X*[1]*X*[2] ⋯ *X[n]*\]^(**T**), **x : X** ~ *p*[**X**](**x**) ≡ *p*(**x**), or **x** : **X** ~ *f*[**X**](**x**) ≡ *f*(**x**). For the discrete case, the probability of the joint realization **x** is described by

*p*[**X**](**x**) = Pr(*X*[1] = *x*[1] ∩ *X*[2] = *x*[2] ∩ ⋯ ∩ *X[n]* = *x[n]*),

where 0 ≤ *p*[**X**](**x**) ≤ 1. For the continuous case, it is

*f*[**X**](**x**)Δ**x** = Pr(*x*[1] < *X*[1] ≤ *x*[1] + Δ*x*[1] ∩ ⋯ ∩ *x[n]* < *X[n]* ≤ *x[n]* + Δ*x[n]*),

**for** Δ**x** → **0**. Note that *f*[**X**](**x**) can be > 1 because it describes a probability density. As mentioned earlier, two random variables *X*[1] and *X*[2] are statistically independent (╨) if

![art](images/Art_P99.jpg)

If *X*[1] ╨ *X*[2] ╨ ⋯ ╨ *X[n]*, the joint PMF is defined by the product of its marginals,

![art](images/Art_P100.jpg)

For the general case where *X*[1], *X*[2], ⋯ , *X[n]* are not statistically independent, their joint PMF can be defined using the *chain rule*,

![art](images/Art_P101.jpg)

The same rules apply for continuous random variables except that *p*[**X**](**x**) is replaced by *f*[**X**](**x**). [Figure 3.14](#chapter002.xhtml#Fig_3-14) presents examples of marginals and a bivariate joint probability density function.

![art](images/Art_P102.jpg)

Figure 3.14: Examples of marginals and a bivariate probability density function.

The multivariate cumulative distribution function describes the probability that a set of *n* random variables is simultaneously lesser or equal to **x**,

*F*[**X**](**x**) = Pr(*X*[1] ≤ *x*[1] ∩ ⋯ ∩ *X[n] ≤ *x[n]*).*

 

The joint CDF is obtained by integrating the joint PDF over each dimension from its lower bound up to **x**, and inversely, the joint PDF is obtained by differentiating the CDF,

![art](images/Art_P103.jpg)

A multivariate CDF has values 0 ≤ *F*[**X**](**x**) ≤ 1, and its value is zero at the lowest bound for any dimension and one at the upper bound for all dimensions,

![art](images/Art_P104.jpg)

[Figure 3.15](#chapter002.xhtml#Fig_3-15) presents an example of marginals and a bivariate cumulative distribution function.

![art](images/Art_P105.jpg)

Figure 3.15: Examples of marginals and a bivariate cumulative distribution function.

The operation consisting of removing a random variable from a joint set is called *marginalization*. For a set of *n* joint random variables, we can remove the *i*^(th) variable by summing over the *i*^(th) dimension,

![art](images/Art_P106.jpg)

If we marginalize all variables by summing over all dimensions, the result is

![art](images/Art_P107.jpg)

For the example presented in [figure 3.16](#chapter002.xhtml#Fig_3-16), *X*[1] ╨ *X*[2] so the joint PMF is obtained by the product of its marginals. It is possible to obtain the marginal PMF for *x*[1] from the joint through marginalizing, ![art](images/Art_P108.jpg)

![art](images/Art_P109.jpg)

**Marginalization**

![art](images/Art_P110.jpg)

![art](images/Art_P114a.jpg)

![art](images/Art_P114.jpg)

Figure 3.16: Examples of marginals and bivariate probability mass functions.

Marginalization applies to continuous random variables using integration,

![art](images/Art_P111.jpg)

where again, if we integrate over all dimensions, the result is

![art](images/Art_P112.jpg)

 

For both continuous and discrete random variables, we can marginalize a random variable by evaluating its CDF at its upper bound,

![art](images/Art_P113.jpg)

 

[*3.3.5   Moments and Expectation*](#toc.xhtml#Rh2-8)

**Expected value**

![art](images/Art_P115.jpg)

The *moment* of order *m*, ![art](images/Art_P116.jpg)of a random variable *X* is defined as

![art](images/Art_P117.jpg)

where ![art](images/Art_P118.jpg)denotes the *expectation* operation. For *m* = 1, ![art](images/Art_P119.jpg)is a measure of position for the centroid of the probability density or mass function. This centroid is analogous to the concept of *center of gravity* for a solid body or cross section. An *expected value* refers to the sum of all possible values weighted by their probability of occurrence. A key property of the expectation is that it is a *linear operation* so that

![art](images/Art_P120.jpg)

The notion of expectation can be extended for any function of random variables *g*(*X*),

![art](images/Art_P121.jpg)

The expectation of the function *g*(*X*) = (*X* − *µ[X]*)*^m* is referred to as *centered moment of order m*,

![art](images/Art_P122.jpg)

For the special cases where *m* = 1, ![art](images/Art_P123.jpg), and for *m* = 2,

![art](images/Art_P124.jpg)

where *σ[X]* denotes the *standard deviation* of *X*; and var\[·\] denotes the *variance* operator that measures the dispersion of the probability density function with respect to its mean. The notion of variance is analogous to the concept of *moment of inertia* for a cross section. Together, *µ[X]* and *σ[X]* are metrics describing the centroid and dispersion of a random variable. Another adimensional dispersion metric for describing a random variable is the coefficient of variation, ![art](images/Art_P125.jpg). Note that *δ[X]* only applies for *µ[X]* ≠ 0.

Given two random variables *X, Y* , their *covariance*, cov(*X, Y*), is defined by the expectation of the product of the mean-centered variables,

![art](images/Art_P126.jpg)

The *correlation coefficient ρ[XY]* can take a value between -1 and 1, which quantifies the *linear dependence* between *X* and *Y*,

![art](images/Art_P127.jpg)

A positive (negative) correlation indicates that a large outcome for *X* is associated with a high probability for a large (small) outcome for *Y*. [Figure 3.17](#chapter002.xhtml#Fig_3-17) presents examples of scatter plots generated for different correlation coefficients.

![art](images/Art_P128.jpg)

Figure 3.17: Examples of scatter plots between the realizations of two random variables for different correlation coefficients *ρ*.

In the special case where *X* and *Y* are independent, the correlation is zero, *X* ╨ *Y* ⇒ *ρ[XY]* = 0. Note that the inverse is not true; a correlation coefficient equal to zero does not guarantee the independence, *ρ[ij]* = 0 ⇏ *X[i]* ╨ *X[j]*. This happens because correlation only measures the linear dependence between a pair of random variables; two random variables can be nonlinearly dependent, yet have a correlation coefficient equal to zero. [Figure 3.18](#chapter002.xhtml#Fig_3-18) presents an example of a scatter plot with quadratic dependence yet no linear dependence, so *ρ* ≈ 0.

![art](images/Art_P129.jpg)

Figure 3.18: Example of scatter plot where there is a quadratic dependence between the variables, yet the correlation coefficient *ρ* ≈ 0.

Correlation also does not imply *causality*. For example, the number of flu cases is negatively correlated with the temperature; when the seasonal temperatures drop during winter, the number of flu cases increases. Nonetheless, the cold itself is not causing the flu; someone isolated in a cold climate is unlikely to contract the flu because the virus is itself unlikely to be present in the environment. Instead, studies have shown that the flu virus has a higher transmissibility in the cold and dry conditions that are prevalent during winter. See, for example, Lowen and Steel.^([6](#chapter002.xhtml#footnote_6))

For a set of *n* random variables *X*[1], *X*[2], ⋯ , *X[n]*, the *covariance matrix* defines the dispersion of each variable through its variance located on the main diagonal, and the dependence between variables through the pairwise covariance located on the off-diagonal terms,

![art](images/Art_P130.jpg)

 

A covariance matrix is symmetric (sym.), and each term is defined following ![art](images/Art_P131.jpg). Because a variable is linearly correlated with itself (*ρ* = 1), the main diagonal terms reduce to ![art](images/Art_P132.jpg). A covariance matrix has to be *positive semi-definite* (see [§2.4.2](#chapter001.xhtml#Sec_2.4.2)) so the variances on the main diagonal must be > 0. In order to avoid singular cases, there should be no linearly dependent variables, that is, −1 < *ρ[ij]* < 1, ∀*i* ≠ *j*.

 

[*3.4   Functions of Random Variables*](#toc.xhtml#Rh1-8)

Let us consider a continuous random variable *X* ~ *f[X]*(*x*) and a *monotonic* deterministic function *y* = *g*(*x*). The function’s output *Y* is a random variable because it takes as input the random variable *X*. The PDF *f[Y]* (*y*) is defined knowing that for each infinitesimal part of the domain *dx*, there is a corresponding *dy*, and the probability over both domains must be equal,

![art](images/Art_P133.jpg)

A *monotonic* function *g*(*x*) takes one variable as input and returns one variable as output and is strictly either increasing or decreasing.

The *change-of-variable* rule for *f[Y]* (*y*) is defined by

![art](images/Art_P134.jpg)

where multiplying by ![art](images/Art_P136.jpg)accounts for the change in the size of the neighborhood of *x* with respect to *y*, and where the absolute value ensures that *f[Y]* (*y*) ≥ 0. For a function *y* = *g*(*x*) and its inverse *x* = *g*^(−1)(*y*), the *gradient* is obtained from

![art](images/Art_P137.jpg)

A transformation from a space *x* to another space *y* requires taking into account the change in the size of the neighborhood

![art](images/Art_P135.jpg)

[Figure 3.19](#chapter002.xhtml#Fig_3-19) presents an example of nonlinear transformation *y* = *g*(*x*). Notice how, because of the nonlinear transformation, the maximum for *f[X]*(*x^∗*) and the maximum for *f[Y]* (*y^∗*) do not occur for the same locations, that is, *y^∗* ≠ *g*(*x^∗*).

![art](images/Art_P138.jpg)

Figure 3.19: Example of 1-D nonlinear transformation *y* = *g*(*x*). Notice how the nonlinear transformation causes the modes (i.e., the most likely values) to be different in the *x* and *y* spaces.

Given a set of *n* random variables **x** ∈ ℝ*^n* : **X** ~ *f*[**X**](**x**), we can generalize the transformation rule for an *n* to *n* multivariate function **y** = *g*(**x**), as illustrated in [figure 3.20a](#chapter002.xhtml#Fig_3-20) for a case where *n* = 2. As with the univariate case, we need to account for the change in the neighborhood size when going from the original to the transformed space, as illustrated in [figure 3.20b](#chapter002.xhtml#Fig_3-20). The transformation is then defined by

![art](images/Art_P140.jpg)

![art](images/Art_P139.jpg)

Figure 3.20: Illustration of a 2-D transformation.

where ![art](images/Art_P141.jpg)is the inverse of the determinant of the *Jacobian* matrix,

![art](images/Art_P142.jpg)

The Jacobian is an *n* × *n* matrix containing the partial derivatives of *y[k]* with respect to *x[l]*, evaluated at **x** so that ![art](images/Art_P143.jpg),

![art](images/Art_P144.jpg)

Note that each row of the Jacobian matrix corresponds to the *gradient vector* evaluated at **x**,

![art](images/Art_P145.jpg)

The determinant (see [§2.4.1](#chapter001.xhtml#Sec_2.4.1)) of the Jacobian is a scalar quantifying the size of the neighborhood of *d***y** with respect to *d***x**.

 

[*3.4.1   Linear Functions*](#toc.xhtml#Rh2-9)

[Figure 3.21b](#chapter002.xhtml#Fig_3-21) illustrates how a function *y* = 2*x* transforms a random variable *X* with mean *µ[X]* = 1 and standard deviation *σ[X]* = 0.5 into *Y* with mean *µ[Y]* = 2 and standard deviation *σ[y]* = 1. In the machine learning context, it is common to employ linear functions of random variables *y* = *g*(*x*) = *ax* + *b*, as illustrated in [figure 3.21a](#chapter002.xhtml#Fig_3-21). Given a random variable *X* with mean *µ[X]* and variance ![art](images/Art_P147.jpg), the change in the neighborhood size simplifies to

![art](images/Art_P148.jpg)

![art](images/Art_P146.jpg)

Figure 3.21: Examples of transformations through a linear function.

In such a case, because of the linear property of the expectation operation (see [§3.3.5](#chapter002.xhtml#Sec_3.3.5)),

*µ[Y]* = *g*(*µ[X]*) = *aµ[X]* + *b*, *σ[Y]* = |*a*|*σ*[*X*].

 

Let us consider a set of *n* random variables **X** defined by its mean vector and covariance matrix,

![art](images/Art_P149.jpg)

and the variables **Y** = \[*Y*[1]*Y*[2] ⋯ *Y[n]*\]^(**T**) obtained from a linear function **Y** = **g**(**X**) = **AX** + **b** so that

![art](images/Art_P150.jpg)

**Note:** For linear functions **Y** = **AX** + **b**, the Jacobian **J**[y,x] is the matrix **A** itself.

The function outputs **Y** (i.e., the mean vector), covariance matrix, and the joint covariance are then described by

![art](images/Art_P151.jpg)

If instead of having an *n* → *n* function, we have an *n* → 1 function *y* = *g*(**X**) = **a**^(**T**)**X** + *b*, then the Jacobian simplifies to the gradient vector ![art](images/Art_P152.jpg), which is again equal to the vector **a**^(**T**),

![art](images/Art_P153.jpg)

The function output *Y* is then described by

![art](images/Art_P154.jpg)

 

[*3.4.2   Linearization of Nonlinear Functions*](#toc.xhtml#Rh2-10)

Because of the analytic simplicity associated with linear functions of random variables, it is common to approximate nonlinear functions by linear ones using a Taylor series so that

![art](images/Art_P155.jpg)

The *Hessian* **H**(*µ*[**X**]) is an *n* × *n* matrix containing the 2^(nd)\-order partial derivatives evaluated at ***µ*[X]**. See [§ 5.2](#chapter004.xhtml#Sec_5.2) for details.

 

In practice, the series are most often limited to the first-order approximation, so for a one-to-one function, it simplifies to

*Y* = **g**(*X*) ≈ *aX* + *b*.

[Figure 3.22](#chapter002.xhtml#Fig_3-22) presents an example of such a linear approximation for a one-to-one transformation. Linearizing at the expected value *µ[x]* minimizes the approximation errors because the linearization is then centered in the region associated with a high probability content for *f[X]*(*x*). In that case, *a* corresponds to the gradient of *g*(*x*) evaluated at *µ[X]*,

![art](images/Art_P156.jpg)

![art](images/Art_P159.jpg)

Figure 3.22: Example of a linearized nonlinear transformation.

For the *n* → 1 multivariate case, the linearized transformation leads to

 
| *Y* = *g*(**X**) || ≈ || **a**^(**T**)**X** + *b* |
| --- | --- | --- |
|  || \= || ∇*g*(***µ*[X]**)(**X** − ***µ*[X]**) + *g*(***µ***[**X**]), |

where *Y* has a mean and variance equal to

![art](images/Art_P157.jpg)

For the *n* → *n* multivariate case, the linearized transformation leads to

 
| **Y** = **g**(**X**) || ≈ || **AX** + **b** |
| --- | --- | --- |
|  || \= || **J[Y,X]**(***µ*[X]**)(**X** − ***µ*[X]**) + **g**(***µ*[X]**), |

where *Y* is described by the mean vector and covariance matrix,

![art](images/Art_P158.jpg)

For multivariate nonlinear functions, the gradient or Jacobian is evaluated at the expected value ***µ*[X]**.

 

 

*Exercises*

 
| P3.1 || Draw on the Venn diagram: *E*[1] ∪ *E*[2] ∩ *E*[3] ∪ *E*[1] ∩ *E*[2].![art](images/Art_P160.jpg) |
| --- | --- |
| P3.2 || Explain the difference between independent and mutually exclusive events. |
| P3.3 || Compute Pr(*E*[1] ∪ *E*[2]) for two events *E*[1] : Pr(*E*[1]) = 0.2 and *E*[2] : Pr(*E*[2]) = 0.5, for which Pr(*E*[1]*E*[2]) = 0.1. |
| P3.4 || Given two discrete random variables *X* : *x* ∈ {*x*[1], *x*[2], *x*[3]} and *Y* : *y* ∈ {*y*[1], *y*[2], *y*[3]} with the joint PMF defined below, compute the marginal probabilities *p*(*x*) and *p*(*y*) and the conditional probabilities *p*(*x*|*y*).![art](images/Art_P160a.jpg) |
| P3.5 || Explain the difference between *X* and *x* for a random variable. |
| P3.6 || Draw the PMF and CMF of *X* as defined in P3.4. |
| P3.7 || Why can a PDF *f[X]*(*x*) be > 1 and a PMF *p[X]*(*x*) cannot? |
| P3.8 || Why is a CDF *F[X]*(*x*) nondecreasing? |
| P3.9 || Explain why two random variables can have a correlation coefficient *ρ* = 0 and still not be independent. |
| P3.10 || In what case does ![art](images/Art_P161.jpg)hold? |
| P3.11 || If *F[X]*(20) = 0.5 and *F[X]*(10) = 0.1, what is Pr(10 ≤ *X* ≤ 20)? |
| P3.12 || For *X* : ![art](images/Edouble.jpg)\[*X*\] = 20, var\[*X*\] = 10² and a deterministic function *Y* = 5*X* + 30, compute ![art](images/Edouble.jpg)\[*Y*\] and var\[Y\]. |
| P3.13 || Given a slender column with a resistance defined by *F*, *K* is a random variable ![art](images/Edouble.jpg)with {*µ[K]* = 0.75, *σ[K]* = 0.1}, *E* = 200,000 MPa, *L* = 10,000 mm, and *I* = 10⁷ mm⁴. (a) Compute ![art](images/Edouble.jpg)\[*F*\] and var\[*F*\] by linearizing *F*. (b) Draw the PDF for *F* using the change of variable rule.![art](images/Art_P162.jpg) |

 

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter002.xhtml#footnote_ref_1) Elastic modulus relates the stress *σ* and strains *ϵ* in Hooke’s law *σ* = *ϵE*.

[²](#chapter002.xhtml#footnote_ref_2) Creep is the long-term (i.e., ≫years) deformation that occurs under constant stress.

[³](#chapter002.xhtml#footnote_ref_3) Box, G. E. P. and G. C. Tiao (1992). *Bayesian inference in statistical analysis*. Wiley.

[⁴](#chapter002.xhtml#footnote_ref_4) Ang, A. H.-S. and W. H. Tang (1975). *Probability concepts in engineering planning and decision*, Volume 1—Basic Principles. John Wiley.

[⁵](#chapter002.xhtml#footnote_ref_5) This example is adapted from Armen Der Kiureghian’s course, CE229, at University of California, Berkeley.

[⁶](#chapter002.xhtml#footnote_ref_6) Lowen, A. C. and J. Steel (2014). Roles of humidity and temperature in shaping influenza seasonality. *Journal of Virology 88* (14), 7692–7695.

 

[*4*](#toc.xhtml#chap-3)

[*Probability Distributions*](#toc.xhtml#chap-3)

The definition of probability distributions *f[X]*(*x*) was left aside in [chapter 3](#chapter002.xhtml). This chapter presents the formulation and properties for the probability distributions employed in this book: the Normal distribution for *x* ∈ ℝ, the log-normal for *x* ∈ ℝ^+, and the Beta for *x* ∈ (0, 1).

 

[*4.1   Normal Distribution*](#toc.xhtml#Rh1-9)

**Univariate Normal**

*x* ∈ ℝ : *X* ~ N (*x*; *µ, σ*²)

The most widely employed probability distribution is the *Normal*, also known as the *Gaussian*, distribution. In this book, the names *Gaussian* and *Normal* are employed interchangeably when describing a probability distribution. This section covers the mathematical foundation for the univariate and multivariate Normal and then details the properties explaining its widespread usage.

 

[*4.1.1   Univariate Normal*](#toc.xhtml#Rh2-11)

The probability density function (PDF) for a Normal random variable is defined over the real numbers *x* ∈ ℝ. *X* ~ N (*x*; *µ, σ*²) is parameterized by its *mean µ* and *variance σ*², so its PDF is

![art](images/Art_P163.jpg)

[Figure 4.1](#chapter003.xhtml#Fig_4-1) presents an example of PDF and cumulative distribution function (CDF) with parameters *µ* = 0 and *σ* = 1. The mode—that is, the most likely value—corresponds to the mean. Changing the mean *µ* causes a translation of the distribution. Increasing the standard deviation *σ* causes a proportional increase in the PDF’s dispersion. The Normal CDF is presented in [figure 4.1b](#chapter003.xhtml#Fig_4-1). Its formulation is obtained through integration, where the integral can be formulated using the *error function* erf(·),

![art](images/Art_P165.jpg)

![art](images/Art_P164.jpg)

Figure 4.1: Representation of the univariate Normal for *µ* = 0, *σ* = 1.

[Figure 4.2](#chapter003.xhtml#Fig_4-2) illustrates the successive steps taken to construct the univariate Normal PDF. Within the innermost parenthesis of the PDF formulation is a linear function ![art](images/Art_P166.jpg), which centers *x* on the mean *µ* and normalizes it with the standard deviation *σ*. This first term is then squared, leading to a positive number over all its domain except at the mean, where it is equal to zero. Taking the negative exponential of this second term leads to a bell-shaped curve, where the value equals one (exp(0) = 1) at the mean *x* = *µ* and where there are inflexion points at *µ* ± *σ*. At this step, the curve is proportional to the final Normal PDF. Only the normalization constant is missing to ensure that ![art](images/Art_P167.jpg). The normalization constant is obtained by integrating the exponential term,

![art](images/Art_P168.jpg)

![art](images/Art_P170.jpg)

Figure 4.2: Illustration of the univariate Normal probability density function formulation for *µ* = 0, *σ* = 1.

Dividing the exponential term by the normalization constant in equation 4.1 results in the final formulation for the Normal PDF. Note that for *x* = *µ*, *f*(*µ*) ≠ 1 because the PDF has been normalized so its integral is one.

 

[*4.1.2   Multivariate Normal*](#toc.xhtml#Rh2-12)

**Multivariate Normal**

**x** ∈ ℝ*^n* : **X** ~ N (**x**; ***µ*[X]**, **Σ[X]**)

The joint probability density function (PDF) for two Normal random variables {*X*[1], *X*[2]} is given by

![art](images/Art_P169.jpg)

There are three terms within the parentheses inside the exponential. The first two are analogous to the quadratic terms for the univariate case. The third one includes a new parameter *ρ* describing the correlation coefficient between *X*[1] and *X*[2]. Together, these three terms describe the equation of a 2-D ellipse centered at \[*µ*[1]*µ*[2]\]^(**T**).

In a more general way, the probability density function for *n* random variables **X** = \[*X*[1]*X*[2] ⋯ *X[n]*\]^(**T**) is described by **x** ∈ ℝ*^n* : **X** ~ N (**x**; ***µ*[X]**, **Σ[X]**), where ***µ*[X]** = \[*µ*[1]*µ*[2] ⋯ *µ[n]*\]^(**T**) is a vector containing mean values and ∑**[X]** is the covariance matrix,

![art](images/Art_P171.jpg)

| **D[X]** || : Standard deviation matrix |
| --- | --- |
| **R[X]** || : Correlation matrix |
| **Σ[X]** || : Covariance matrix |

**D[X]** is the *standard deviation matrix* containing the standard deviation of each random variable on its main diagonal, and **R[X]** is the symmetric (sym.) *correlation matrix* containing the correlation coefficient for each pair of random variables,

![art](images/Art_P172.jpg)

Note that a variable is linearly correlated with itself so the main diagonal terms for the correlation matrix are \[**R[X]**\]*[ii]* = 1, ∀*i*. The multivariate Normal joint PDF is described by

![art](images/Art_P173.jpg)

where the terms inside the exponential describe an *n*\-dimensional ellipsoid centered at ***µ*[X]**. The directions of the principal axes of this ellipsoid are described by the eigenvector (see [§2.4.2](#chapter001.xhtml#Sec_2.4.2)) of the covariance matrix **Σ[X]**, and their lengths by the eigenvalues. [Figure 4.3](#chapter003.xhtml#Fig_4-3) presents an example of a covariance matrix decomposed into its eigenvector and eigenvalues. The curves overlaid on the joint PDF describe the marginal PDFs in the eigen space.

![art](images/Art_P174.jpg)

Figure 4.3: Example of bivariate PDF with *µ*[1] = *µ*[2] = 0, *σ*[1] = *σ*[2] = 1, and *ρ* = 0.8, for which the covariance matrix is decomposed into its eigenvector and eigenvalues.

For the multivariate Normal joint PDF formulation, the term on the left of the exponential is again the normalization constant, which now includes the determinant of the covariance matrix. As presented in [§2.4.1](#chapter001.xhtml#Sec_2.4.1), the determinant quantifies how much the covariance matrix **Σ[X]** is scaling the space x. [Figure 4.4](#chapter003.xhtml#Fig_4-4) presents examples of bivariate Normal PDF and CDF with parameters *µ*[1] = 0, *σ*[1] = 2, *µ*[2] = 0, *σ*[2] = 1, and *ρ* = 0.6. For the bivariate CDF, notice how evaluating the upper bound for one variable leads to the marginal CDF, represented by the bold red line, for the other variable.

![art](images/Art_P184.jpg)

Figure 4.4: Examples of bivariate PDF and CDF for *µ*[1] = *µ*[2] = 0, *σ*[1] = 2, *σ*[2] = 1, and *ρ* = 0.6.

 

[*4.1.3   Properties*](#toc.xhtml#Rh2-13)

A multivariate Normal random variable follow several properties. Here, we insist on six:

 

1.  It is *completely defined* by its *mean vector **µ[X]*** and *covariance matrix***Σ[X]**.
2.  Its *marginal distributions are also Normal*, and the PDF of any marginal is given by
    
    *x[i]* : *X[i]* ~ N (*x[i]*; \[***µ*[X]**\]*[i]*, \[**Σ[X]**\]*[ii]*).
    
3.  The *absence of correlation implies statistical independence*. Note that this is not generally true for other types of random variables (see [§3.3.5](#chapter002.xhtml#Sec_3.3.5)),
    
    *ρ[ij]* = 0 ⇔ *X[i]* ╨ *X[j]*.
    
4.  The *central limit theorem* (CLT) states that, under some conditions, the asymptotic distribution obtained from the normalized sum of *independent identically distributed* (iid) random variables (normally distributed or not) is Normal. Given *X[i]*, ∀*i* ∈ {1, ⋯ , *n*}, a set of iid random variables with expected value ![art](images/Art_P175.jpg)and finite variance ![art](images/Art_P176.jpg), the PDF of ![art](images/Art_P177.jpg)approaches ![art](images/Art_P178.jpg), for *n* → ∞. More formally, the CLT states that
    
    ![art](images/Art_P179.jpg)
    
    where ![art](images/Art_P180.jpg)means *converges in distribution*. In practice, when observing the outcomes of real-life phenomena, it is common to obtain empirical distributions that are similar to the Normal distribution. We can see the parallel where these phenomena are themselves issued from the superposition of several phenomena. This property is key in explaining the widespread usage of the Normal probability distribution.
    
5.  The output from *linear functions of Normal random variables are also Normal*. Given **x : X** ~ N (**x**; ***µ*[X]**, **Σ[X]**) and a linear function **y** = **Ax** + **b**, the properties of linear transformations described in [§3.4.1](#chapter002.xhtml#Sec_3.4.1) allow obtaining
    
    **Y** ~ N(**y**; **A*µ*[X]** + **b, AΣ[X]A**^(**T**)).
    
    Let us consider the simplified case of a linear function *z* = *x* + *y* for two random variables ![art](images/Art_P181.jpg), ![art](images/Art_P182.jpg). Their sum is described by
    
    ![art](images/Art_P183.jpg)
    
    In the case where both variables are statistically independent *X* ╨ *Y*, the variance of their sum is equal to the sum of their respective variance. For the general case describing the sum of a set of *n* correlated normal random variables *X[i]* such that **X** ~ N (**x**; ***µ*[X]**, **Σ[X]**),
    
    ![art](images/Art_P185.jpg)
    
    As we will see in the next chapters, the usage of linear models is widespread in machine learning because of the analytical tractability of linear functions of Normal random variables.
    
6.  *Conditional distributions are Normal*. For instance, we can partition an ensemble of *n* random variables **X** in two subsets so that
    
    ![art](images/Art_P186.jpg)
    
    where Σ*[i]* describes the covariance matrix for the *i*^(th) subset of random variables and ![art](images/Art_P187.jpg)describes the covariance between the random variables belonging to subsets *i* and *j*. It is mentioned in [§3.3.4](#chapter002.xhtml#Sec_3.3.4) that a conditional probability density function is obtained from the division of a joint PDF by a marginal PDF. The same concept applies to define the conditional PDF of **X***[i]* given a vector of observations **X***[j]* = **x***[j]*,
    
    ![art](images/Art_P188.jpg)
    
    where the conditional mean and covariance are
    
    ![art](images/Art_P189.jpg)
    
    If we simplify this setup for only two random variables *X*[1] and *X*[2], where we want the conditional PDF of *X*[1] given an observation *X*[2] = *x*[2], then equation 4.3 simplifies to
    
    ![art](images/Art_P190.jpg)
    
    In the special case where the prior mean *µ*[1] = *µ*[2] = 0 and the prior standard deviations *σ*[1] = *σ*[2] > 0, then the conditional mean simplifies to the observation *x*[2] times the correlation coefficient *ρ*. Note that the conditional variance ![art](images/Art_P191.jpg)is independent of the observed value *x*[2]; it only depends on the prior variance and the correlation coefficient. For the special case where *ρ* = 1, then ![art](images/Art_P192.jpg).
    

  

[*4.1.4   Example: Conditional Distributions*](#toc.xhtml#Rh2-14)

For the beam example illustrated in [figure 4.5](#chapter003.xhtml#Fig_4-5), our *prior knowledge for the resistance* {*X*[1], *X*[2]} of two adjacent beams is

![art](images/Art_P194.jpg)

![art](images/Art_P193.jpg)

Figure 4.5: Example of dependence between the resistance of beams.

and we know that the beam resistances are correlated with *ρ*[12] = 0.8. Such a correlation could arise because both beams were fabricated with the same process, in the same factory. This prior knowledge is described by the joint bivariate Normal PDF,

![art](images/Art_P195.jpg)

If we observe that the resistance of the second beam *x*[2] = 700 kN·m, we can employ conditional probabilities to estimate the PDF of the strength *X*[1], given the observation *x*[2],

![art](images/Art_P196.jpg)

where

![art](images/Art_P197.jpg)

[Figure 4.6](#chapter003.xhtml#Fig_4-6) presents the joint and conditional PDFs corresponding to this example. For the joint PDF, the highlighted pink slice corresponding to *x*[2] = 700 is proportional to the conditional probability ![art](images/Art_P198.jpg). If we want to obtain the conditional distribution from the joint PDF, we have to divide it by the marginal PDF ![art](images/Art_P199.jpg). This ensures that the conditional PDF for *x*[1] integrates to 1. This example is trivial, yet it sets the foundations for the more advanced models that will be presented in the following chapters.

![art](images/Art_P200.jpg)

Figure 4.6: Joint prior PDF ![art](images/Art_P201.jpg)and conditional PDF ![art](images/Art_P202.jpg)describing the resistance of beams.

 

[*4.1.5   Example: Sum of Normal Random Variables*](#toc.xhtml#Rh2-15)

[Figure 4.7](#chapter003.xhtml#Fig_4-7) presents steel cables where each one is made from dozens of individual wires. Let us consider a cable made of 50 steel wires, each having a resistance *x[i]* : *X[i]* ~ N (*x[i]*; 10, 3²) kN. We use equation 4.2 to compare the cable resistance ![art](images/Art_P204.jpg)depending on the correlation coefficient *ρ[ij]*. With the hypothesis that *X[i]* ╨ *X[j]* ⇔ *ρ[ij]* = 0, all nondiagonal terms of the covariance matrix \[Σ[**X**]\]*[ij]* = 0, ∀*i* ≠ *j*, which leads to

![art](images/Art_P205.jpg)

![art](images/Art_P203.jpg)

Figure 4.7: Steel cables each made from multiple wires. (This example is adapted from Armen Der Kiureghian’s CE229 course at UC Berkeley.)

With the hypothesis *ρ[ij]* = 1, all terms in \[Σ[**X**]\]*[ij]* = (3 kN)², ∀*i*, *j*, so that

![art](images/Art_P206.jpg)

[Figure 4.8](#chapter003.xhtml#Fig_4-8) presents the resulting PDFs for the cable resistance, given each hypothesis. These results show that if the uncertainty in the resistance for each wire is independent, there will be some cancellation; some wires will have a resistance above the mean, and some will have a resistance below. The resulting coefficient of variation for *ρ* = 0 is ![art](images/Art_P207.jpg), which is approximately three times smaller than ![art](images/Art_P208.jpg), the variability associated with each wire. In the opposite case, if the resistance is linearly correlated (*ρ* = 1), the uncertainty adds up as you increase the number of wires, so ![art](images/Art_P209.jpg).

![art](images/Art_P210.jpg)

Figure 4.8: Probability density function of the cable resistance depending on the correlation between the strength of each wire.

 

[*4.2   Log-Normal Distribution*](#toc.xhtml#Rh1-10)

**Univariate log-normal**

| *x* ∈ ℝ^+ : *X* ~ ln N (*x*; *λ, ζ*) |
| --- |
| *x′* ∈ ℝ || : *X′* = ln *X* ~ N (ln *x*; *λ, ζ*²) |
| *µ[X]* || : mean of *X* |
| *λ* || : mean of ln *X* (= *µ*[ln]*X*) |
| ![art](images/Art_P211.jpg) || : variance of *X* |
| *ζ*² || : variance of ![art](images/Art_P212.jpg) |

The *log-normal* distribution is obtained by transforming the Normal distribution through the function ln *x*. Because the logarithm function is only defined for positive values, the domain of the log-normal distribution is *x* ∈ ℝ^+.

 

[*4.2.1   Univariate Log-Normal*](#toc.xhtml#Rh2-16)

The random variable *X* ~ ln N (*x*; *λ, ζ*) is log-normal if ln *X* ~ N (ln *x*; *λ, ζ*²) is Normal. Given the transformation function *x′* = ln *x*, the *change of variable* rule presented in [§3.4](#chapter002.xhtml#Sec_3.4) requires that

![art](images/Art_P213.jpg)

where the derivative of ln *x* with respect to x is

![art](images/Art_P214.jpg)

Therefore, the analytic formulation for the log-normal PDF is given by the product of the transformation’s derivative and the Normal PDF evaluated for *x′* = ln *x*,

![art](images/Art_P215.jpg)

The univariate log-normal PDF is parameterized by the mean (*µ*[ln *X*] = *λ*) and variance ![art](images/Art_P216.jpg)defined in the log-transformed space (ln *x*). The mean *µ[X]* and variance ![art](images/Art_P217.jpg)of the log-normal random variable can be transformed in the log-space using the relations

![art](images/Art_P218.jpg)

Note that for *δ[X]* < 0.3, the standard deviation in the log-space is approximately equal to the coefficient of variation in the original space, *ζ* ≈ *δ[X]*. [Figure 4.9](#chapter003.xhtml#Fig_4-9) presents an example of log-normal PDF plotted (a) in the original space and (b) in the log-transformed space. The mean and standard deviation are {*µ[X]* = 2, *σ[X]* = 1} in the original space and {*λ* = 0.58, *ζ* = 0.47} in the log-transformed space.

![art](images/Art_P219.jpg)

Figure 4.9: Univariate log-normal probability density function for {*µ[X]* = 2, *σ[X]* = 1} and {*λ* = 0.58, *ζ* = 0.47}.

 

[*4.2.2   Multivariate Log-Normal*](#toc.xhtml#Rh2-17)

**Multivariate log-normal**

**x** ∈ (ℝ^+)*^n* : **X** ~ ln N (**x**; *µ*[ln **X**], Σ[ln **X**])

*X*[1], *X*[2], ⋯ , *X[n]* are jointly log-normal if ln *X*[1], ln *X*[2], ⋯ *,* ln *X[n]* are jointly Normal. The multivariate log-normal PDF is parameterized by the mean values ![art](images/Art_P220.jpg), variances ![art](images/Art_P221.jpg), and correlation coefficients (*ρ*[ln]*X[i]* ln *X[j]*) defined in the log-transformed space. Correlation coefficients in the log-space *ρ*[ln]*X[i]* ln *X[j]* are related to the correlation coefficients in the original space ![art](images/Art_P222.jpg)using the relation

![art](images/Art_P223.jpg)

where ![art](images/Art_P224.jpg)for ![art](images/Art_P225.jpg). The PDF for two random variables {*X*[1], *X*[2]} such that {*x*[1], *x*[2]} > 0 is

![art](images/Art_P226.jpg)

 

[Figure 4.10](#chapter003.xhtml#Fig_4-10) presents an example of bivariate log-normal PDF with parameters *µ*[1] = *µ*[2] = 1.5, *σ*[1] = *σ*[2] = 0.5, and *ρ* = 0.9. The general formulation for the multivariate log-normal PDF is

![art](images/Art_P227.jpg)

![art](images/Art_P228.jpg)

Figure 4.10: Example of bivariate log-normal probability density function for *µ*[1] = *µ*[2] = 1.5, *σ*[1] = *σ*[2] = 0.5, and *ρ* = 0.9.

where ***µ***[ln **X**] and Σ[ln **X**] are respectively the mean vector and covariance matrix defined in the log-space.

 

[*4.2.3   Properties*](#toc.xhtml#Rh2-18)

Because the log-normal distribution is obtained through a transformation of the Normal distribution, it inherits several of its properties.

1.  It is *completely defined by* its *mean vector **µ***[ln **X**] and *covariance matrix* Σ[ln **X**].
2.  Its *marginal distributions are also log-normal*, and the PDF of any marginal is given by
    
    *x[i]* : *X[i]* ~ ln *N* (*x[i]*; \[***µ***[ln **X**]\]*[i]*, \[Σ[ln **X**]\]*[ii]*).
    
3.  The *absence of correlation implies statistical independence*. Remember that this is not generally true for other types of random variables (see [§3.3.5](#chapter002.xhtml#Sec_3.3.5)),
    
    *ρ[ij]* = 0 ⇔ *X[i]* ╨ *X[j]*.
    
4.  *Conditional distributions are log-normal*, so the PDF of X*[i]* given an observation **X***[j]* = **x***[j]* is given by
    
    ![art](images/Art_P229.jpg)
    
    where the conditional mean vector and covariance are
    
    ![art](images/Art_P230.jpg)
    
5.  The *multiplication of jointly log-normal random variables is jointly log-normal* so that for *X* ~ ln N (*x*; *λ[X], ζ[X]*) and *Y* ~ ln N (*y*; *λ[Y], ζ[Y]*), where *X* ╨ *Y* ,
    
    ![art](images/Art_P231.jpg)
    
    Because the product of log-normal random variables can be transformed in the sum of Normal random variables, the properties of the *central limit theorem* presented in [§4.1.3](#chapter003.xhtml#Sec_4.1.3) still hold.
    

  

[*4.3   Beta Distribution*](#toc.xhtml#Rh1-11)

**Beta**

![art](images/Art_P232.jpg)

The Beta distribution is defined over the interval (0, 1). It can be scaled by the transformation *x′* = *x* · (*b − a*) + *a* to model bounded quantities within any range (*a, b*). The Beta probability density function (PDF) is defined by

![art](images/Art_P233.jpg)

where *α* and *β* are the two distribution parameters, and the Beta function B(*α, β*) is the normalization constant so that

![art](images/Art_P234.jpg)

A common application of the Beta PDF is to employ the interval (0, 1) to model the probability density of a probability itself. Let us consider two mutually exclusive and collectively exhaustive events, for example, any event *A* and its complement *A*, S = {*A*, A}. If the probability that the event *A* occurs is uncertain, it can be described by a random variable so that

![art](images/Art_P235.jpg)

where *x* ∈ (0, 1) : *X* ~ B(*x*; *α, β*). The parameter *α* can be interpreted as *pseudo-counts* representing the number of observations of the event *A*, and *β* is the number of observations of the complementary event *A*. This relation between *pseudo-counts* and the Beta distribution, as well as practical applications, are further detailed in [chapter 6](#chapter005.xhtml). [Figure 4.11](#chapter003.xhtml#Fig_4-11) presents examples of Beta PDFs for three sets of parameters. Note how for *α* = *β* = 1, the Beta distribution is analogous to the Uniform distribution U(*x*; 0, 1).

![art](images/Art_P236.jpg)

Figure 4.11: Three examples of the Beta probability density function evaluated for different sets of parameters {*α, β*}.

 

 

*Exercises*

 
| P4.1 || For the joint PDFs N (\[*x*[1]*x*[2]\]^(**T**); ***µ*[X]**, **Σ[X]**),a) Compute ![art](images/Art_P237.jpg); andb) Draw the joint PDF contours if ***µ*[X]** = \[0 0\]^(**T**).![art](images/Art_P238.jpg) |
| --- | --- |
| P4.2 || Explain the role of the five parameters ![art](images/Art_P239.jpg), and *ρ* describing the bivariate Normal PDF. |
| P4.3 || Explain what happens to a bivariate Normal PDF if its covariance matrix is singular. |
| P4.4 || Given *Z* = *X* + *Y* , so that *X* ~ N(*x*; 0, 1²) and *Y* ~ N (*y*; 2, 5²), compute *µ[Z]* and ![art](images/Art_P240.jpg)if a) *ρ* = 0, b) *ρ* = 1. |
| P4.5 || For a log-normal random variable *X* ~ ln N (*x*; *λ, ζ*), explain the difference between {*µ[X]*, *σ[X]*} and {*λ, ζ*} (reminder: *λ* ≡ *µ*[ln *X*] and *ζ* ≡ *σ*[ln *X*]). |
| P4.6 || Plot the PDF and CDF for *X* ~ N(*x*; 0, 1²). |
| P4.7 || Plot the PDF and CDF for *Y* ~ ln N (*y*; *λ, ζ*), if ![art](images/Art_P241.jpg)and Var\[*Y*\] = 0.25. |
| P4.8 || Plot the PDF and CDF for *Z* ~ B(*z*; *α, β*), if ![art](images/Art_P242.jpg)and Var\[*Z*\] = 0.03. |
| P4.9 || From the marginal PDFs in P4.6 and P4.8, plot the contours of the joint PDF *f*(*y, z*) if *Y* ╨ *Z*. |
| P4.10 || The prior knowledge of the resistance (*X*[1], *X*[2], *X*[3], *X*[4], *X*[5]) for five adjacent beams is*X[i]* ~ N (*x[i]*; 500, 150²) \[kN · m\].Knowing that the resistance of beams is correlated *ρ[ij]* = 0.8, ∀*i* ≠ *j*, what is the mean and covariance for strengths *X*[1], *X*[2], and *X*[3], given that we have observed that *x*[4] = 695 kN · m and *x*[5] = 675 kN · m? |

 

 

[*5*](#toc.xhtml#chap-4)

[*Convex Optimization*](#toc.xhtml#chap-4)

When building a model in the context of machine learning, we often seek optimal model parameters ***θ***, in the sense where they *maximize* the prior probability (or probability density) of predicting observed data. Here, we denote by ![art](images/Art_P243.jpg)the target function we want to maximize. Optimal parameter values ***θ^∗*** are those that maximize the function ![art](images/Art_P244.jpg),

![art](images/Art_P247.jpg)

**Note:** In the context of this book, we are only concerned by target functions ![art](images/Art_P245.jpg)that are continuous and twice differentiable.

**Note:** In order to be mathematically rigorous, equation 5.1 should employ the operator ∈ rather than \= to recognize that ***θ^∗*** belongs to a set of possible solutions maximizing ![art](images/Art_P246.jpg).

With a small caveat that will be covered below, *convex optimization* methods can be employed for the maximization task in equation 5.1. The key aspect of convex optimization methods is that, under certain conditions, they are guaranteed to reach optimal values for convex functions. [Figure 5.1](#chapter004.xhtml#Fig_5-1) presents examples of convex and non-convex sets. For a set to be *convex*, you must be able to link any two points belonging to it without being outside of this set. [Figure 5.1b](#chapter004.xhtml#Fig_5-1) presents a case where this property is not satisfied. For a *convex function*, the segment linking any pair of its points lies above or is equal to the function. Conversely, for a *concave function*, the opposite holds: the segment linking any pair of points lies below or is equal to the function. A concave function can be transformed into a convex one by taking the negative of it. Therefore, a maximization problem formulated as a *concave optimization* can be formulated in terms of a *convex optimization* following

![art](images/Art_P248.jpg)

![art](images/Art_P249.jpg)

Figure 5.1: Examples of a convex and a non-convex set.

In this chapter, we refer to *convex optimization* even if we are interested in maximizing a concave function, rather than minimizing a convex one. This choice is justified by the prevalence of *convex optimization* in the literature. Moreover, note that for several machine learning methods, we seek ***θ^∗*** based on a minimization problem where ![art](images/Art_P251.jpg)is a function of the difference between observed values and those predicted by a model. [Figure 5.2](#chapter004.xhtml#Fig_5-2) presents examples of convex/concave and non-convex/non-concave functions. Non-convex/non-concave functions such as the one in [figure 5.2b](#chapter004.xhtml#Fig_5-2) may have several *local optima*. Many functions of practical interest are non-convex/non-concave. As we will see in this chapter, convex optimization methods can also be employed for non-convex/non-concave functions given that we choose a proper starting location. This chapter presents the gradient ascent and Newton-Raphson methods, as well as practical tools to be employed with them. For full-depth details regarding optimization methods, the reader should refer to dedicated textbooks.^([1](#chapter004.xhtml#footnote_1))

![art](images/Art_P250.jpg)

Figure 5.2: Representations of convex/concave and non-convex/non-concave functions.

 

[*5.1   Gradient Ascent*](#toc.xhtml#Rh1-12)

A *gradient* is a vector containing the partial derivatives of a function with respect to its variables. For a continuous function, the maximum is located at the point where its gradient equals zero. *Gradient ascent* is based on the principle that as long as we move in the direction of the gradient, we are moving toward a maximum. For the unidimensional case, we choose to move to a new position *θ*[new] defined as the old value *θ*[old] plus a search direction *d* defined by a scaling factor *λ* times the derivative estimated at *θ*[old],

![art](images/Art_P254.jpg)

**Derivative**

![art](images/Art_P252.jpg)

**Gradient**

![art](images/Art_P252a.jpg)

**Maximum of a concave function**

![art](images/Art_P253.jpg)

*λ* is also known as the *learning rate* or *step length*.

A common practice for setting *λ* is to employ *backtracking line search* where a new position is accepted if the *Armijo rule*^([2](#chapter004.xhtml#footnote_2)) is

![art](images/Art_P255.jpg)

[Figure 5.3](#chapter004.xhtml#Fig_5-3) presents a comparison of the application of equation 5.2 with the two extreme cases, *c* = 0 and *c* = 1. For *c* = 1, *θ*[new] is only accepted if ![art](images/Art_P257.jpg)lies above the plane defined by the tangent at *θ*[old]. For *c* = 0, *θ*[new] is only accepted if ![art](images/Art_P258.jpg). The larger *c* is, the stricter is the Armijo rule for ensuring that sufficient progress is made by the current step. With backtracking line search, we start from an initial value of *λ*[0] and reduce it until equation 5.2 is satisfied. [Algorithm 1](#chapter004.xhtml#Tab_1) presents a minimal version of the gradient ascent with backtracking line search.

![art](images/Art_P256.jpg)

Figure 5.3: Example of application of the Armijo rule to test if *θ*[new] has sufficiently increased the objective function in comparison with *θ*[old].

 

**Algorithm 1:** Gradient ascent with backtracking line search

![art](images/Art_P259.jpg)

[Figure 5.4](#chapter004.xhtml#Fig_5-4) presents the first two steps of the application of [algorithm 1](#chapter004.xhtml#Tab_1) to a non-convex/non-concave function with an initial value *θ*[0] = 3.5 and a scaling factor *λ*[0] = 3. For the second step, the scaling factor *λ* has to be reduced twice in order to satisfy the Armijo rule. One of the difficulties with gradient ascent is that the convergence speed depends on the choice of *λ*[0]. If *λ*[0] is too small, several steps will be wasted and convergence will be slow. If *λ*[0] is too large, the algorithm may not converge.

![art](images/Art_P260.jpg)

Figure 5.4: Example of application of gradient ascent with backtracking for finding the maximum of a function.

[Figure 5.5](#chapter004.xhtml#Fig_5-5) presents a limitation common to all convex optimization methods when applied to functions involving local maxima; if the starting location *θ*[0] is not located on the slope segment leading to the global maximum, the algorithm will most likely miss it and converge to a local maximum. The task of selecting a proper value *θ*[0] is nontrivial because in most cases, it is not possible to visualize ![art](images/Art_P261.jpg). This issue can be tackled by attempting multiple starting locations ***θ***[0] and by using domain knowledge to identify proper starting locations.

![art](images/Art_P262.jpg)

Figure 5.5: Example of application of gradient ascent converging to a local maximum for a function.

Gradient ascent can be applied to search for the maximum of a multivariate function by replacing the univariate derivative by the gradient so that

![art](images/Art_P263.jpg)

As illustrated in [figure 5.6](#chapter004.xhtml#Fig_5-6), because gradient ascent follows the direction where the gradient is maximal, it often displays an oscillatory pattern. This issue can be mitigated by introducing a *momentum* term in the calculation of ***θ***[new],^([3](#chapter004.xhtml#footnote_3))

![art](images/Art_P264.jpg)

![art](images/Art_P265.jpg)

Figure 5.6: Comparison of gradient ascent with and without momentum.

where **v** can be interpreted as a velocity that carries the momentum from the previous iterations.

  

[*5.2   Newton-Raphson*](#toc.xhtml#Rh1-13)

**Second-order derivatives**

![art](images/Art_P266.jpg)

**Hessian**

![art](images/Art_P267.jpg)

The *Newton-Raphson* method allows us to adaptively scale the search direction vector using the second-order derivative ![art](images/Art_P268.jpg). Knowing that the maximum of a function corresponds to the point where the gradient is zero, ![art](images/Art_P269.jpg), we can find this maximum by formulating a linearized gradient equation using the second-order derivative of ![art](images/Art_P270.jpg)and then set it equal to zero. The analytic formulation for the linearized gradient function (see [§3.4.2](#chapter002.xhtml#Sec_3.4.2)) approximated at the current location *θ*[old] is

![art](images/Art_P271.jpg)

We can estimate *θ*[new] by setting equation 5.3 equal to zero, and then by solving for *θ*, we obtain

![art](images/Art_P272.jpg)

Let us consider the case where we want to find the maximum of a *quadratic function* (i.e., ∝ *x*²), as illustrated in [figure 5.7](#chapter004.xhtml#Fig_5-7). In the case of a quadratic function, the algorithm converges to the exact solution in one iteration, no matter the starting point, because the gradient of a quadratic function is exactly described by the linear function in equation 5.3.

![art](images/Art_P273.jpg)

Figure 5.7: Example of application of Newton-Raphson to a quadratic function.

[Algorithm 2](#chapter004.xhtml#Tab_2) presents a minimal version of the Newton-Raphson method with backtracking line search. Note that at line 6, there is again a scaling factor *λ*, which is employed because the Newton-Raphson method is exact only for quadratic functions. For more general non-convex/non-concave functions, the linearized gradient is an approximation such that a value of *λ* = 1 will not always lead to a *θ*[new] satisfying the Armijo rule in equation 5.2.

[Figure 5.8](#chapter004.xhtml#Fig_5-8) presents the application of [algorithm 2](#chapter004.xhtml#Tab_2) to a non-convex/non-concave function with an initial value *θ*[0] = 3.5 and a scaling factor *λ*[0] = 1. For each loop, the pink solid line represents the linearized gradient function formulated in equation 5.3. Notice how, for the first two iterations, the second derivative ![art](images/Art_P274.jpg). Having a positive second derivative indicates that the linearization of ![art](images/Art_P275.jpg)equals zero for a minimum rather than for a maximum. One simple option in this situation is to define *λ* = *−λ* in order to ensure that the next step moves in the same direction as the gradient. The convergence with Newton-Raphson is typically faster than with gradient ascent.

![art](images/Art_P284.jpg)

Figure 5.8: Example of application of the Newton-Raphson algorithm with backtracking line search for finding the maximum of a function.

 

**Algorithm 2:** Newton-Raphson with backtracking line search

![art](images/Art_P276.jpg)

The Newton-Raphson algorithm can be employed for identifying the optimal values ![art](images/Art_P277.jpg)in domains having multiple dimensions. The equation 5.4 developed for univariate cases can be extended for *n*\-dimensional domains by following

![art](images/Art_P278.jpg)

![art](images/Art_P279.jpg)denotes the *n* × *n Hessian* matrix containing the second-order partial derivatives for the function ![art](images/Art_P280.jpg)evaluated at ***θ***. The Hessian is a symmetric matrix where each term is defined by

![art](images/Art_P281.jpg)

When the terms on the main diagonal of the Hessian matrix are positive, it is an indication that our linearized gradient points toward a minimum rather than a maximum. As we did in [algorithm 2](#chapter004.xhtml#Tab_2), it is then possible to move toward the maximum by reversing the search direction. One issue with gradient-based multi-dimensional optimization is *saddle points*. [Figure 5.9](#chapter004.xhtml#Fig_5-9) presents an example of a saddle point in a function for which one second-order partial derivative is negative ![art](images/Art_P282.jpg)and the other is positive ![art](images/Art_P283.jpg).

![art](images/Art_P285.jpg)

Figure 5.9: Example of saddle point ***θ*** where ![art](images/Art_P286.jpg)and ![art](images/Art_P287.jpg).

 

In such a case, one option is to regularize the Hessian matrix by substracting a constant *α* on its main diagonal in order to ensure that all terms are negative:

![art](images/Art_P288.jpg)

Avoiding being trapped in saddle points is a key challenge in optimization. The reader interested in more advanced strategies for that purpose should consult specialized literature.^([4](#chapter004.xhtml#footnote_4))

In practice, second-order methods such as Newton-Raphson can be employed when we have access to an analytical formulation for evaluating the Hessian, ![art](images/Art_P289.jpg). Otherwise, if we have to employ numerical derivatives (see [§5.4](#chapter004.xhtml#Sec_5.4)) to estimate the Hessian, the computational demand quickly becomes prohibitive as the number of variables increases. For example, if the number of variables is *n* = 100, by considering the symmetry in the Hessian matrix, there are ![art](images/Art_P290.jpg)second-order partial derivatives to estimate for each Newton-Raphson iteration. Even for computationally efficient functions ![art](images/Art_P291.jpg), the necessary number of evaluations becomes a challenge. In addition, for a large *n*, there is a substantial effort required to invert the Hessian in equation 5.5. Therefore, even if Newton-Raphson is more efficient in terms of the number of iterations required to reach convergence, this does not take into account the time necessary to obtain the second-order derivatives. When dealing with a large number of variables or for functions ![art](images/Art_P292.jpg)that are computationally expensive, we may revert to using momentum-based gradient-ascent methods.

 

[*5.3   Coordinate Ascent*](#toc.xhtml#Rh1-14)

One alternative to the methods we have seen for multivariate optimization is to perform the search for each variable separately, which corresponds to solving a succession of 1D optimization problems. This approach is known as *coordinate optimization*.^([5](#chapter004.xhtml#footnote_5)) This approach is known to perform well when there is no strong coupling between parameters with respect to the values of the objective function. [Algorithm 3](#chapter004.xhtml#Tab_3) presents a minimal version of the coordinate ascent Newton-Raphson using backtracking line search. [Figure 5.10](#chapter004.xhtml#Fig_5-10) presents two intermediate steps illustrating the application of [algorithm 3](#chapter004.xhtml#Tab_3) to a bidimensional non-convex/non-concave function.

![art](images/Art_P294.jpg)

Figure 5.10: Example of application of the coordinate ascent Newton-Raphson algorithm with backtracking for finding the maximum of a 2-D function.

 

**Algorithm 3:** Coordinate ascent using Newton-Raphson

![art](images/Art_P293.jpg)

 

[*5.4   Numerical Derivatives*](#toc.xhtml#Rh1-15)

**Examples**

![art](images/Art_P301.jpg)

One aspect that was omitted in the previous sections is *How do we obtain the first- and second-order derivatives*? When a twice differentiable formulation for ![art](images/Art_P295.jpg)exists, ![art](images/Art_P296.jpg)and ![art](images/Art_P297.jpg)can be expressed analytically. When analytic formulations are not available, derivatives can be estimated numerically using either a *forward*, *backward*, or *central differentiation* scheme.^([6](#chapter004.xhtml#footnote_6)) Here, we only focus on the *central differentiation method*. Note that forward and backward differentiations are not as accurate as central, yet they are computationally cheaper. As illustrated in [figure 5.11](#chapter004.xhtml#Fig_5-11), first- and second-order partial derivatives of ![art](images/Art_P298.jpg)with respect to the *i*^(th) element of a vector ***θ*** = \[*θ*[1]*θ*[2] ⋯ *θ[n]*\]^(**T**) are given by

![art](images/Art_P299.jpg)

![art](images/Art_P300.jpg)

Figure 5.11: Illustration of 1-D numerical derivatives.

where Δ*θ* ≪ *θ* is a small perturbation to the value *θ[i]* and ![art](images/Art_P302.jpg)is a *n* × 1 indicator vector, for which all values are equal to 0, except the *i*^(th), which is equal to one.

As illustrated in [figure 5.12](#chapter004.xhtml#Fig_5-12), numerical derivatives can also be employed to estimate each term of the Hessian matrix,

![art](images/Art_P304.jpg)

![art](images/Art_P303.jpg)

Figure 5.12: Illustration of 2-D partial numerical derivatives.

where terms on the numerator are defined as

![art](images/Art_P305.jpg)

In practice, the full Hessian matrix can only be estimated numerically when the number of variables *n* is small or when evaluating ![art](images/Art_P306.jpg)is computationally cheap.

 

[*5.5   Parameter-Space Transformation*](#toc.xhtml#Rh1-16)

When optimizing using either the gradient ascent or the Newton-Raphson method, we are likely to run into difficulties for parameters *θ* that are not defined in an unbounded space. In such a case, the efficiency is hindered because the algorithms may propose new positions *θ*[new] that lie outside the valid domain. When trying to identify optimal parameters for probability distributions such as those described in [chapter 4](#chapter003.xhtml), common domains for parameters are as follows:

*   Mean parameters: *µ* ∈ ℝ
*   Standard deviations: *σ* ∈ ℝ^+
*   Correlation coefficients: *ρ* ∈ (−1, 1)
*   Probability: Pr(*X* = *x*) ∈ (0, 1)

One solution to this problem is to perform the optimization in a transformed space *θ*^(tr) such that

*θ*^(tr) = *g*(*θ*) ∈ ℝ.

For each *θ*, the choice of transformation function *g*(*θ*) depends on its domain. [Figure 5.13](#chapter004.xhtml#Fig_5-13) presents examples of transformations for *θ* ∈ ℝ, *θ* ∈ ℝ^+, and *θ* ∈ (*a, b*). Note that in the simplest case, where *θ* ∈ ℝ, no transformation is required, so *θ*^(tr) = *θ*.

![art](images/Art_P307.jpg)

Figure 5.13: Examples of transformation functions.

 

For θ ∈ ℝ^+, a common transformation is to take the logarithm *θ*^(tr) = ln(*θ*), and its inverse transformation is ![art](images/Art_P308.jpg). The analytical derivatives for the transformation and its inverse are

![art](images/Art_P309.jpg)

For parameters bounded in an interval *θ* ∈ (*a, b*), a possible transformation is the scaled *logistic sigmoid* function

![art](images/Art_P310.jpg)

and its inverse is given by

![art](images/Art_P311.jpg)

The derivative of the transformation and its inverse are

![art](images/Art_P312.jpg)

Note that the derivative of these transformations will be employed in [chapter 7](#chapter006.xhtml) when performing parameter-space transformations using the change-of-variable rule we have seen in [§3.4](#chapter002.xhtml#Sec_3.4). The transformations presented here are not unique, as many other functions can be employed. For further details about parameter space transformations, the reader is invited to refer to Gelman et al.^([7](#chapter004.xhtml#footnote_7))

 

 

*Exercises*

 
| P5.1 || Explain the differences between gradient ascent and Newton-Raphson and how each of them works. |
| --- | --- |
| P5.2 || In what case is gradient ascent better suited than Newton-Raphson? |
| P5.3 || With convex optimization algorithms, what is the purpose of performing the optimization in a transformed space? |
| P5.4 || Implement a gradient ascent algorithm to find the value *x* that maximizes the function ![art](images/Art_P313.jpg)in the interval (0, 12). Use as a starting point *θ*[0] = −3. Check your results with [figure 5.4](#chapter004.xhtml#Fig_5-4). |
| P5.5 || Implement a Newton-Raphson algorithm to find the value *θ* that maximizes the function and setup from P5.4. Check your results with [figure 5.8](#chapter004.xhtml#Fig_5-8). |
| P5.6 || Repeat P5.5 to confirm that you reach the same result while using numerical derivatives rather than analytical ones. |
| P5.7 || Implement a 2-D coordinate-ascent Newton-Raphson algorithm to find the value ***θ*** that maximizes the function ![art](images/Art_P314.jpg), diag(\[1 1\]²) + 0.4 · N(***θ***, \[0.75 − 1.5\]^(**T**), diag(\[2 2\]²)). Use as a starting point ***θ***[0] = \[1 − 3\]^(**T**). Check your results with [figure 5.10](#chapter004.xhtml#Fig_5-10). |

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter004.xhtml#footnote_ref_1) Bertsekas, D. P., A. Nedi, and A. E. Ozdaglar (2003). *Convex analysis and optimization*. Athena Scientific; Chong, E. K. P. and S. H. Zak (2013). *An introduction to optimization* (4th ed.). Wiley; and Nocedal, J. and S. Wright (2006). *Numerical optimization*. Springer Science & Business Media.

[²](#chapter004.xhtml#footnote_ref_2) Armijo, L. (1966). Minimization of functions having Lipschitz continuous first partial derivatives. *Pacific Journal of Mathematics 16* (1), 1–3.

[³](#chapter004.xhtml#footnote_ref_3) Rumelhart, D. E., G. E. Hinton, and R. J. Williams (1986). Learning representations by back-propagating errors. *Nature 323*, 533–536.

[⁴](#chapter004.xhtml#footnote_ref_4) Nocedal, J. and S. Wright (2006). *Numerical optimization*. Springer Science & Business Media; Dauphin, Y. N., R. Pascanu, C. Gulcehre, K. Cho, S. Ganguli, and Y. Bengio (2014). Identifying and attacking the saddle point problem in high-dimensional non-convex optimization. In *Advances in Neural Information Processing Systems*, 27, 2933–2941; and Goodfellow, I., Y. Bengio, and A. Courville (2016). *Deep learning*. MIT Press.

[⁵](#chapter004.xhtml#footnote_ref_5) Wright, S. J. (2015). Coordinate descent algorithms. *Mathematical Programming 151* (1), 3–34; and Friedman, J., T. Hastie, H. Höfling, and R. Tibshirani (2007). Pathwise coordinate optimization. *The Annals of Applied Statistics 1* (2), 302–332.

[⁶](#chapter004.xhtml#footnote_ref_6) Nocedal, J. and S. Wright (2006). *Numerical optimization*. Springer Science & Business Media; and Abramowitz, M. and I. A. Stegun (1972). *Handbook of mathematical functions with formulas, graphs, and mathematical table*. National Bureau of Standards, Applied Mathematics.

[⁷](#chapter004.xhtml#footnote_ref_7) Gelman, A., J. B. Carlin, H. S. Stern, and D. B. Rubin (2014). *Bayesian data analysis* (3rd ed.). CRC Press.

 

[**Part II**](#toc.xhtml#part-2)

[**Bayesian Estimation**](#toc.xhtml#part-2)

![art](images/Art_P315.jpg)

 

 

[*6*](#toc.xhtml#chap-5)

[*Learning from Data*](#toc.xhtml#chap-5)

**Learning context**

![art](images/Art_P316.jpg)

When scalars *x* are employed to model physical phenomena, we can use empirical observations y to learn about the probability (or probability density) for each value that *x* can take. When *X* is a random variable, we can use observations to learn about the parameters ***θ*** describing its probability density (or mass) function *f*(*x*;***θ***). This chapter presents the general Bayesian formulation, as well as approximate methods derived from it, for learning about unknown state variables and parameters, given known data. The applications presented in this chapter focus on simple models in order to keep the attention on the Bayesian methods themselves. We will see in [chapters 8](#chapter007.xhtml)–[13](#chapter012.xhtml) how this theory can be generalized for applications to machine learning models having complex architectures. For an in-depth review of Bayesian methods applied to data analysis, the reader may refer to specialized textbooks such as those by Gelman et al.^([1](#chapter005.xhtml#footnote_1)) or Box and Tiao.^([2](#chapter005.xhtml#footnote_2))

 

[*6.1   Bayes*](#toc.xhtml#Rh1-17)

Learning from data can be seen as an indirect problem; we observe some quantities **y**, and we want to employ this information to infer knowledge about hidden\-state variables **x** and model parameters ***θ***, where **y** depends on **x** and ***θ*** through *f*(**y**|**x**;***θ***). In [chapter 3](#chapter002.xhtml), we saw that such a dependence can be treated using *conditional probabilities*.

**Note:** The term *hidden* describes a state variable that is not directly observed.

**Notation:** ; and | are both employed to describe a conditional probability or probability density. The distinction is that ; is employed when ***θ*** are parameters of a PDF or PMF, for example, *f*(*x*; ***θ***) = N (*x*; *µ, σ*²), and | denotes a conditional dependence between variables, for example, *f*(*y*|*x*). Besides these semantic distinctions, both are employed in the same way when it comes to performing calculations.

In the first part of this chapter, we solely focus on the estimation of hidden-state variables *x*. Given two random variables *X* ~ *f*(*x*) and *Y* ~ *f*(*y*), their joint probability density function (PDF) is obtained by the product of a conditional and a marginal PDF,

![art](images/Art_P317.jpg)

 

In the case where *y* is known and *X* is not, we can reorganize the terms of equation 6.1 in order to obtain *Bayes rule*,

![art](images/Art_P318.jpg)

which describes the posterior PDF (i.e., our posterior knowledge) of *X* given that we have observed *y*. Let us consider *X*, a random variable so that *X* ~ *f*(*x*), and given a set of observations D = {*y*[1], *y*[2], ⋯ , *y*[D]} that are realizations of the random variables **Y** = \[*Y*[1]*Y*[2] ⋯ *Y*[D]\]^(**T**) ~ *f*(**y**). Our posterior knowledge for *X* given the observations *D* is described by the conditional PDF

![art](images/Art_P319.jpg)

**Note:** From now on, the number of elements in a set or the number of variables in a vector is defined by a typewriter\-font upper-case letter; for example, D is the number of observations in a set D, and X is the number of variables in the vector **x** = \[*x*[1]*x*[2] · · · *x*[X]\]^T.

**A set of observations**

D = {*y*[1], *y*[2], · · · , *y*[D]}

| e.g., || D || \= || {1.2, 3.8, ⋯ , 0.22}, (*y* ∈ ℝ) |
| --- | --- | --- | --- |
|  || D || \= || {3, 1, ⋯ , 6}, (*y* ∈ ℤ+) |
|  || D || \= || {blue, blue, ⋯ , red},  
  (*y* ∈ {blue, red, green}) |

*Prior*   *f*(*x*) describes our *prior knowledge* for the values *x* that a random variable *X* can take. The prior knowledge can be expressed in multiple ways. For instance, it can be based on heuristics such as expert opinions. In the case where data is obtained sequentially, the posterior knowledge at time *t* − 1 becomes the prior at time *t*. In some cases, it also happens that no prior knowledge is available; then, we should employ a *non-informative* prior, that is, a prior that reflects an absence of knowledge (see [§6.4.1](#chapter005.xhtml#Sec_6.4.1) for further details on non-informative priors).

**Note:** A *uniform* prior and a *non-informative* prior are not the same thing. Some non-informative priors are uniform, but not all uniform priors are non-informative.

*Likelihood*   *f*(**Y** = **y**|*x*) ≡ *f*(D|*x*) describes the *likelihood*, or the conditional probability density, of observing the event {**Y** = D}, given the values that *x* can take. Note that in the special case of an exact observation where D = *y* = *x*, then

![art](images/Art_P320.jpg)

In such a case, the observations are exact so the prior does not play a role; by observing *y* you have all the information about *x* because *y* = *x*. In the general case where *y* : *Y* = fct(*x*), that is, *y* is a realization from a stochastic process, which is a function of *x*—*f*(D|*x*) describes the *prior* probability density of observing D given a specific set of values for *x*.

Here, the term *prior* refers to our state of knowledge that has not yet been influenced by the observations in D.

*Evidence*   *f*(**Y** = **y**) ≡ *f*(D) is called the *evidence* and consists in a *normalization constant* ensuring that the posterior PDF integrates to 1. In [§3.3](#chapter002.xhtml#Sec_3.3) we saw that for both the discrete and the continuous cases,

![art](images/Art_P321.jpg)

For that property to be true, the normalization constant is defined as the sum/integral over the entire domain of *x*, of the likelihood times the prior,

![art](images/Art_P322.jpg)

So far, the description of learning as an indirect problem is rather abstract. The next sections will apply this concept to simple problem configurations involving discrete and continuous random variables.

 

[*6.2   Discrete State Variables*](#toc.xhtml#Rh1-18)

**Discrete state variable**: A discrete random variable *X* employed to represent the uncertainty regarding the state *x* of a system.

This section presents how the probability of occurrence for discrete state variables are estimated from observations. In all the examples presented in this section, the uncertainty associated with our knowledge of a *hidden* random variable *X* is epistemic because a *true value*![art](images/Art_P323.jpg)exists, yet it is unknown. Moreover, *x* is not directly observable; we can only observe *y*, where *p*(*y*|*x*) describes the conditional probability of an observation *y* given the value of the discrete hidden-state variable *x*.

*Reminder:* The term *hidden* refers to a variable that is not observed.

 

[*6.2.1   Example: Disease Screening*](#toc.xhtml#Rh2-19)

[Figure 6.1](#chapter005.xhtml#Fig_6-1) illustrates the context of a rare disease for which the probability of occurrence in the general population is 1 percent, and a screening test such that if one has the disease, the probability of testing positive is Pr(test+|disease) = 0.8; and if one does not have the disease, the probability of testing positive is Pr(test+|¬disease) = 0.1. The sample space for the variable describing the hidden state we are interested in is *x* ∈ {disease, ¬disease}, for which the prior probability is Pr(*X* = disease) = 0.01 and Pr(*X* = ¬disease) = 1 − Pr(*X* = disease) = 0.99.

![art](images/Art_P324.jpg)

Figure 6.1: Visual interpretation of Bayes rule in the context of disease screening. (Adapted from John Henderson (CC BY).)

For a single observation, D = {test+}, the posterior probability of having the disease is

![art](images/Art_P325.jpg)

and the posterior probability of not having the disease is

![art](images/Art_P326.jpg)

If we push this example to the extreme case where the disease is so rare that only one human on Earth has it (see [figure 6.2](#chapter005.xhtml#Fig_6-2)) and where we have a highly accurate screening test so that

![art](images/Art_P327.jpg)

![art](images/Art_P328.jpg)

Figure 6.2: The example of a disease so rare that only one human on Earth has it.

the question is *If you test positive, should you be worried?* The answer is no; the disease is so rare that even with the high test accuracy, if we tested every human on Earth, we would expect ≈ 0.001 × (8 × 10⁹) = 8 × 10⁶ false positive diagnoses. This example illustrates how in extreme cases, prior information may outweigh the knowledge you obtain from observations.

 

[*6.2.2   Example: Fire Alarm*](#toc.xhtml#Rh2-20)

**Note:** ![art](images/Art_P329.jpg)does not have to equal one for the likelihood; however, it does for the posterior, ![art](images/Art_P330.jpg).

It is common to observe that when a fire alarm is triggered in a public building, people tend to remain calm and ignore the alarm. Let us explore this situation using conditional probabilities. The sample space for the hidden state we are interested in is ![art](images/Art_P331.jpg)and the sample space for the observation is ![art](images/Art_P332.jpg). If we assume that

![art](images/Art_P333.jpg)

then the question is *Why does no one react when a fire alarm is triggered?* The issue here is that ![art](images/Art_P334.jpg)describes the probability of an alarm given the state; in order to answer the question, we need to calculate ![art](images/Art_P335.jpg), which depends on the prior probability that there was a fire at time *t* − 1 as well as at the transition probabilities *p*(*x[t]*|*x*[*t*−1]), as illustrated in [figure 6.3](#chapter005.xhtml#Fig_6-3).

![art](images/Art_P336.jpg)

Figure 6.3: Fire alarm example.

 

We assume that at *t* − 1, before the alarm is triggered, our prior knowledge is

![art](images/Art_P337.jpg)

The transition probability between *t* − 1 and *t*, at the moment when the alarm is triggered, is described by the conditional probabilities

![art](images/Art_P338.jpg)

By combining the prior knowledge at *t* − 1 with the transition probabilities, we obtain the joint prior probability of hidden states at both time steps,

![art](images/Art_P339.jpg)

We obtain the marginal prior probability of each state *x* at a time *t* by marginalizing this joint probability, that is, summing over states at *t* − 1,

![art](images/Art_P340.jpg)

If we combine the information from the prior knowledge at *t* and the observation, we can compute the posterior probability of the state *x[t]*, given that the alarm has been triggered,

![art](images/Art_P341.jpg)

 

Overall, despite an alarm being triggered, the probability that there is a fire remains less than 30 percent.

We can explore what would happen at time *t* + 1 if, after the alarm has been triggered, a safety official informs us that there is a fire and that we need to evacuate. We assume here that the conditional probability of receiving such information given the state is

![art](images/Art_P342.jpg)

as illustrated in [figure 6.4](#chapter005.xhtml#Fig_6-4). Here we assume that given the state, the probability of receiving the information from the safety official is conditionally independent from the alarm, that is, ![art](images/Art_P343.jpg). If, as we did for the estimation at time *t*, we combine the information from the prior knowledge at time *t*, the transition probabilities, and the observation at time *t* + 1, we can compute the posterior probability of the hidden state *x*[*t*+1], given that the alarm has been triggered and that we received the information from a safety official. First, the marginal prior probabilities of each state at time *t* + 1 are estimated from the posterior probability at *t* combined with the transition probabilities so that

![art](images/Art_P344.jpg)

![art](images/Art_P345.jpg)

Figure 6.4: Example illustrating the role of the prior in sequential data acquisition and interpretation.

Then, the posterior probability at *t* + 1 is estimated following

![art](images/Art_P346.jpg)

This example illustrates how when knowledge about a hidden state evolves over time as new information becomes available, the posterior at *t* is employed to estimate the prior at *t* + 1.

  

[*6.2.3   Example: Post-Earthquake Damage Assessment*](#toc.xhtml#Rh2-21)

Given an earthquake of intensity^([3](#chapter005.xhtml#footnote_3))

*X* : *x* ∈ {light (L), moderate (M), important (I)}

and a structure that can be in a state (e.g., see [figure 6.5](#chapter005.xhtml#Fig_6-5))

*Y* : *y* ∈ {damaged (D), undamaged (D)}.

![art](images/Art_P348.jpg)

Figure 6.5: Extensive damage after San Francisco’s 1906 earthquake.

These two random variables are illustrated using a Venn diagram in [figure 6.6](#chapter005.xhtml#Fig_6-6). The likelihood of damage given each earthquake intensity is

![art](images/Art_P347.jpg)

![art](images/Art_P349.jpg)

Figure 6.6: Venn diagram illustrating the sample space where the earthquake intensities light (L), moderate (M), and important (I) are mutually exclusive and collectively exhaustive events. The post-earthquake structural states of damaged (D) and undamaged (D) intersect the earthquake intensity events.

and the prior probability of each intensity is given by

![art](images/Art_P350.jpg)

We are interested in inferring the intensity of an earthquake given that we have observed damaged buildings *y* = D following an event, so that

![art](images/Art_P351.jpg)

The first step to solve this problem is to compute the normalization constant,

![art](images/Art_P352.jpg)

**Note:** For the likelihood ![art](images/Art_P353.jpg); however, for the prior ![art](images/Art_P354.jpg), and for the posterior ![art](images/Art_P355.jpg).

Then, the posterior probability of each state is calculated following

![art](images/Art_P356.jpg)

We see that despite the prior probability of a high-intensity earthquake being small (i.e., Pr(*X* = I) = 0.02), the posterior is significantly higher because of the observation indicating the presence of structural damage.

  

[*6.3   Continuous State Variables*](#toc.xhtml#Rh1-19)

This section presents examples of applications of hidden-state estimation for continuous cases. Compared with discrete cases, continuous ones involve more abstract concepts in the definition of the likelihood *f*(D|*x*) and evidence *f*(D). Like for the discrete case, if our model is *y* = *x* and we observe *y*, then we know all there is to know about *x* so the conditional probability of *y* given *x* is nonzero only for the true value ![art](images/Art_P357.jpg). In this section, we will cover cases involving imperfect observations rather than perfect ones.

 

[*6.3.1   Likelihood: f*(D|**x**)](#toc.xhtml#Rh2-22)

In practice, we are interested in the case where ![art](images/Art_P358.jpg)is a true yet unknown hidden-state variable and where we have access to imprecise observations *y[i]*, where the *observation model* is either

![art](images/Art_P359.jpg)

where in all three cases the observation error, ![art](images/Art_P360.jpg), *V[i] ╨ V[j]*, ∀*i* ≠ *j*. A direct observation corresponds to the standard case where the observation is the true state ![art](images/Art_P361.jpg)on which an observation error *v* is added. *V* is a Normal random variable employed to describe observation errors. *V* is often chosen to be Normal in order to simplify the problems by maintaining analytical tractability for linear models (see [§4.1.3](#chapter003.xhtml#Sec_4.1.3)). Lower- and upper-bound observations are called *censored* observations where we only know that the hidden-state variable is either respectively greater or smaller than the observed value *y*.

**Note:** *V[i]* ╨ *V[j]*, ∀*i* ≠ *j* indicates that the random variable *V[i]* is independent of *V[j]*, for all *i* ≠ *j* (i.e., that all observation errors are independent of each other).

*Direct observations*   For a *direct observation y*, the likelihood is formulated from the additive observation model so that the PDF of *Y* is described by the Normal PDF ![art](images/Art_P363.jpg). Because ![art](images/Art_P364.jpg)is unknown, the likelihood denoted by *f*(*y*|*x*) or L(*x*|*y*) describes the prior probability density of observing {*Y* = *y*} given ![art](images/Art_P365.jpg),

![art](images/Art_P366.jpg)

![art](images/Art_P362.jpg)

The leftmost surface in [figure 6.7](#chapter005.xhtml#Fig_6-7) corresponds to equation 6.2 plotted with respect to both *x* and *y*, for *σ[V]* = 1. The pink dashed curve represents the explicit evaluation of *f*(*y*|*x* = 0), where the evaluation at *x* = 0 is arbitrarily chosen for illustration purpose, and the red solid curve reverses the relationship to represent the likelihood of the observation *y* = −1 for any value *x*, where *f*(*y* = −1|*x*) = L(*x*|*y* = −1).

![art](images/Art_P367.jpg)

Figure 6.7: Representation of the likelihood function for a direct observation. The leftmost surface describes *f*(*y*|*x*), the rightmost graph describes *f*(*y* = −1|*x*) = L(*x*|*y* = −1), and the center graph describes *f*(*y*|*x* = 0).

Keep in mind that the likelihood is not a PDF with respect to *x* so it does not integrate to 1. Accordingly, the rightmost graph in [figure 6.7](#chapter005.xhtml#Fig_6-7) is a function quantifying for each value *x* how likely it is to observe the value *y* = −1.

*Upper-bound observations*   For an *upper-bound observation* ![art](images/Art_P368.jpg), the likelihood is described by the cumulative distribution function (CDF) of ![art](images/Art_P369.jpg),

![art](images/Art_P370.jpg)

The surface in [figure 6.8](#chapter005.xhtml#Fig_6-8) corresponds to equation 6.3 plotted with respect to *x* and *y*, for *σ[V]* = 1. The pink dashed curve represents the explicit evaluation of *f*(*y*|*x* = 0), where the evaluation at *x* = 0 is arbitrarily chosen for illustration purpose, and the red solid curve reverses the relationship to represent the likelihood of the observation *y* = −1, given any value *x*, L(*x*|*y* = −1).

![art](images/Art_P371.jpg)

Figure 6.8: Representation of the likelihood function for an upper-bound censored observation. The leftmost surface describes *f*(*y*|*x*), the rightmost graph describes *f*(*y* = −1|*x*) = *L*(*x|y* = −1), and the center graph describes *f*(*y*|*x* = 0).

 

*Lower-bound observations*   For a *lower-bound observation* ![art](images/Art_P372.jpg), the likelihood is described by the complement of the cumulative distribution function of ![art](images/Art_P373.jpg),

![art](images/Art_P374.jpg)

The surface in [figure 6.9a](#chapter005.xhtml#Fig_6-9) corresponds to equation 6.4 plotted with respect to *x* and *y*, for *σ[V]* = 1. The pink dashed curve represents the explicit evaluation of *f*(*y*|*x* = 0), where the evaluation at *x* = 0 is arbitrarily chosen for illustration purpose, and again the red curve reverses the relationship to represent the likelihood of the observation *y* = −1, given any value *x*, L(*x*|*y* = −1). Note that in [figure 6.9b](#chapter005.xhtml#Fig_6-9), if instead of having *σ[V]* = 1, *σ[V]* tends to zero, the smooth transition from low likelihood values to high ones would become a sharp jump from zero to one.

![art](images/Art_P375.jpg)

Figure 6.9: Representation of the likelihood function for a lower-bound censored observation. The leftmost surface describes *f*(*y*|*x*), the rightmost graph describes *f*(*y* = −1|*x*) = L(*x*|*y* = −1), and the center graph describes *f*(*y* |*x* = 0).

*Multiple observations*   All cases above dealt with a single observation. When multiple observations are available, one must define the joint likelihood for all observations given *x*. With the assumption that observations are *conditionally independent* given *x*, the joint PDF is obtained from the product of marginals,

![art](images/Art_P376.jpg)

**Note:** The notion of conditional independence implies that given *x*, *Y[i]* is independent of *Y[j]*, that is,

*Y[i]* ╨ *Y[j]*|*x* ⇔ *f*(*y[i]*|*y[j]*, *x*) = *f*(*y[i]*|*x*),

so that *f*(*y[i]*, *y[j]*|*x*) = *f*(*y[i]*|*x*) · *f*(*y[j]*|*x*). This assumption is often satisfied because the observation model follows the form

*y* = *x* + *v*

where *v* is the realization of an observation error so that *V[i]* ╨ *V[j]*, ∀*i* ≠ *j*.

Note that practical difficulties related to numerical *underflow* or *overflow* arise when trying to evaluate the product of several marginal likelihoods *f*(*y[i]|x*). This is why in equation 6.5, the product of the marginals is replaced with the equivalent yet numerically more robust formulation using the exponential of the sum of the log marginals.

 

[*6.3.2   Evidence: f*(D)](#toc.xhtml#Rh2-23)

The evidence acts as a normalization constant obtained by integrating the product of the likelihood and the prior over all possible values of *x*,

![art](images/Art_P377.jpg)

This integral is typically difficult to evaluate because it is not analytically tractable. [Figure 6.10](#chapter005.xhtml#Fig_6-10) presents a naive way of approaching this integral using the *rectangle rule*, where the domain containing a significant probability content is subdivided in S bins of width Δ*x[s]* in order to approximate

![art](images/Art_P378.jpg)

![art](images/Art_P379.jpg)

Figure 6.10: Examples of application of the rectangle integration rule.

This approach is reasonable for trivial 1-D problems; however, it becomes computationally intractable for problems in larger dimensions (i.e., for **x** ∈ ℝ^(**X**)) because the number of grid combinations to evaluate increases exponentially with the number of dimensions X to integrate on. [Section 6.5](#chapter005.xhtml#Sec_6.5) presents an introduction to sampling methods that allow overcoming this challenge. [Chapter 7](#chapter006.xhtml) will introduce more advanced sampling methods allowing the estimation of the normalization constants for high-dimensional domains.

  

[*6.3.3   Posterior: f*(**x**|D)](#toc.xhtml#Rh2-24)

The posterior is the product of the likelihood function times the prior PDF divided by the normalization constant,

![art](images/Art_P380.jpg)

Let us consider two direct observations D = {*y*[1] = −1, *y*[2] = 0} obtained from the observation model

*y[i]* = *x* + *v[i]*, *v[i]* : *V[i]* ~ N (*v*; 0, 1²), *V[i]* ╨ *V[j]*, ∀*i* ≠ *j*.

The likelihood is thus given by *f*(D|*x*) = N (*y*[1]; *x,* 1²) · N (*y*[2]; *x*, 1²). We assume the prior PDF follows a uniform PDF within the range from -5 to 5, *f*(*x*) = U(*x*; −5, 5). As presented in [figure 6.10](#chapter005.xhtml#Fig_6-10), the normalization constant is estimated using the rectangle integration rule to ![art](images/Art_P381.jpg). [Figure 6.11](#chapter005.xhtml#Fig_6-11) presents the prior, the likelihood, and the posterior for this example.

![art](images/Art_P382.jpg)

Figure 6.11: Example of prior, likelihood, and posterior.

 

[*6.3.4   Number of Observations and Identifiability*](#toc.xhtml#Rh2-25)

In the extreme case where no observation is available (i.e., D = *∅*), the posterior is equal to the prior *f*(**x**|*∅*) = *f*(**x**). In order to explore what happens at the other end of the spectrum where an infinite amount of data is available, it is required to distinguish between *identifiable* and *non-identifiable* problems. A problem is *identifiable* when, given an infinite number of direct observations, we are theoretically able to retrieve the true hidden state of a deterministic system ![art](images/Art_P383.jpg). For *non-identifiable* problems, even an infinite number of direct observations does not allow retrieving the true hidden state of the system ![art](images/Art_P384.jpg), because multiple equally valid solutions exist.

*Example: Non-identifiable problem*   Take the example illustrated in [figure 6.12](#chapter005.xhtml#Fig_6-12), where we want to estimate the contaminant concentration in two streams *x*[1] and *x*[2] and where we only have access to contaminant concentration observations

*y[i]* = *x*[1] + *x*[2] + *v[i]*, *v[i]* : *V[i]* ~ N (*v*; 0, 2²), *V[i]* ╨ *V[j]*, ∀*i* ≠ *j*,

![art](images/Art_P385.jpg)

Figure 6.12: Example of two streams merging in a single river.

(Photo: Ashwini Chaudhary)

 

which are collected at the output of a river after both streams have merged. We assume that our prior knowledge is uniform over positive concentration values, that is, *f*(*x*[1], *x*[2]) ∝ 1. The resulting posteriors are presented in [figure 6.13](#chapter005.xhtml#Fig_6-13) for D = 1 and D = 100 observations, along with the true values marked by a red cross. This problem is intrinsically non-identifiable because, even when the epistemic uncertainty has been removed by a large number of observations, an infinite number of combinations of *x*[1] and *x*[2] remain possible.

![art](images/Art_P388.jpg)

Figure 6.13: Posterior contours for an example of non-identifiable problem.

Non-identifiable problems can be regularized using prior knowledge. If, for example, we know that the prior probability for the contaminant concentration in the first stream follows *p*(*x*[1]) = *N* (*x*[1]; 10, 5²), the posterior will now have a single mode, as presented in [figure 6.14](#chapter005.xhtml#Fig_6-14).

![art](images/Art_P390.jpg)

Figure 6.14: Posterior contours for an example of non-identifiable problem for D = 1 and which is constrained by the prior knowledge *f*(*x*[1], *x*[2]) ∝ N (*x*[1]; 10, 5²).

*Well-constrained identifiable problems*   For *well-constrained* problems where a true value ![art](images/Art_P386.jpg)exists, given an infinite number of direct observations (D*→ ∞*) that are conditionally independent given *x*, the posterior tends to a Dirac delta function, which is nonzero only for ![art](images/Art_P387.jpg),

![art](images/Art_P389a.jpg)

[Figure 6.15](#chapter005.xhtml#Fig_6-15) presents an example of such a case where the posterior has collapsed over a single value. The posterior expected value then corresponds to the true value

![art](images/Art_P389.jpg)

![art](images/Art_P391.jpg)

Figure 6.15: Example of posterior PDF tending toward the Dirac delta function.

and the posterior variance tends to zero because no epistemic uncertainty remains about the value of *x*,

![art](images/Art_P390a.jpg)

Note that in most practical cases we do not have access to an infinite number of observations. Moreover, keep in mind that the less data we have access to, the more important it is to consider the uncertainty in the posterior *f*(*x*|*D*).

 

[*6.4   Parameter Estimation*](#toc.xhtml#Rh1-20)

**Notation**

*x[i]* : *X* ~ *f[X]*(*x*; ***θ***)

***θ***: PDF’s parameters

{*x*[1], *x*[2], ⋯ , *x*[D]}: realizations of the hidden variable *X*

In this section, we will explore how to extend Bayesian estimation for the parameters ***θ*** defining the probability density function of a hidden random variable *x* : *X* ~ *f*(*x*) ≡ *f*(*x*; ***θ***). This setup is relevant when the system responses are stochastic. For example, even in the absence of observation errors, different samples from a concrete batch made from the same mix of components would have different resistances due to the uncertainty associated with the intrinsic heterogeneity of the material. The posterior probability density function sought is now

![art](images/Art_P392.jpg)

where *f*(***θ***) is the prior PDF of unknown parameters, *f*(D|***θ***) is the likelihood of observations D = {*y*[1], ⋯ , *y*[D]}, and *f*(***θ***|D) is the posterior PDF for unknown parameters ***θ***. After having estimated the posterior PDF for parameters *f*(***θ***|D), we can *marginalize* this uncertainty in *f*(*x*; ***θ***) in order to obtain the *posterior predictive* PDF for the hidden variable *X*,

![art](images/Art_P393.jpg)

[Figure 6.16](#chapter005.xhtml#Fig_6-16) presents an example where we want to estimate the joint posterior probability of the mean *µ[X]* and standard deviation *σ[X]* defining the PDF of *X*, which describes the variability in the resistance of a given concrete mix. Here, the concrete resistance *X* is assumed to be a random variable. It means that unlike in previous sections, no true value exists for the resistance because it is now a stochastic quantity. Despite this, true values can still exist for the parameters of *f*(*x*; *θ*), that is, ![art](images/Art_P395.jpg). This example will be further explored in [§6.5.3](#chapter005.xhtml#Sec_6.5.3).

![art](images/Art_P394.jpg)

Figure 6.16: Example of Bayesian parameter estimation.

 

[*6.4.1   Prior: f*(*θ*)](#toc.xhtml#Rh2-26)

**Non-informative prior**

![art](images/Art_P396.jpg)

*f*(***θ***) describes our prior knowledge for the values that ***θ*** can take. Prior knowledge can be based on heuristics (expert knowledge), on the posterior PDF obtained from previous data, or on a non-informative prior (i.e., absence of prior knowledge). A *non-informative* prior for parameters such as the mean of a Normal PDF is described by a uniform density *f*(*µ*) ∝ 1. For standard deviations, the non-informative prior typically assumes that all orders of magnitudes for *σ* have equal probabilities. This hypothesis implies that *f*(ln *σ*) ∝ 1. By using the change of variable rule presented in [§3.4](#chapter002.xhtml#Sec_3.4), it leads to ![art](images/Art_P397.jpg), because the derivative of this transformation is ![art](images/Art_P398.jpg). Note that the two non-informative priors described for *µ* and *σ* are *improper* because ∫ *f*(*θ*)*dθ* = ∞, which does not respect the fundamental requirement that a PDF integrates to 1, as presented in [§3.3](#chapter002.xhtml#Sec_3.3). For this reason we cannot draw samples from an improper prior. Nevertheless, when used as a prior, an improper PDF can yield to a proper posterior (see [§7.5](#chapter006.xhtml#Sec_7.5)).

 

[*6.4.2   Likelihood: f*(D|*θ*)](#toc.xhtml#Rh2-27)

![art](images/Art_P401a.jpg)

*f*(D|***θ***) ≡ *f*(**Y** = **y**|***θ***) ≡ *f*(**y**|***θ***) ≡ L(***θ***|**y**) are all equivalent ways of describing the likelihood of observing specific values **y**, given ***θ***. In the special case where *y* = *x* so that realizations of *x* : *X* ~ *f*(*x*; ***θ***) are directly observed, the likelihood is

*f*(*y*|***θ***) = *f*(*y*; ***θ***) = *f*(*x*; ***θ***).

In a more general case where observations D = {*y[i]*, ∀*i* ∈ {1 : D}} are realizations of an additive observation model *y[i]* = *x[i]* + *v[i]*, where ![art](images/Art_P399.jpg)and ![art](images/Art_P400.jpg), the likelihood is

![art](images/Art_P401.jpg)

This choice of an *additive observation model* using normal random variables allows having an analytically tractable formulation for the likelihood. If we want to employ a multiplicative observation model, *y* = *x* · *v*, then choosing ![art](images/Art_P402.jpg)and ![art](images/Art_P403.jpg)as lognormal random variables also preserves the analytical tractability for the likelihood that follows

![art](images/Art_P404.jpg)

 

[*6.4.3   Posterior PDF: f*(*θ*|D)](#toc.xhtml#Rh2-28)

In [§6.3.4](#chapter005.xhtml#Sec_6.3.4), when the number of *independent* observations D → ∞, we saw that the posterior for *X* tends to a Dirac delta function ![art](images/Art_P405.jpg). The situation is different for the estimation of parameters describing the PDF of a hidden random variable (R.V.); when D → ∞, it is now the posterior PDF for ***θ*** that tends to a Dirac delta function as presented in [figure 6.17](#chapter005.xhtml#Fig_6-17),

![art](images/Art_P406.jpg)

**Note:** The term *independent* observations is employed as a shortcut for the more rigorous term that should be in this case *conditionally independent* given **x**.

![art](images/Art_P408.jpg)

Figure 6.17: The posterior PDF for parameters reduces to a Dirac delta function when the number of independent observations tends to infinity.

where the posterior expected value tends toward the true parameter value and the variance of the posterior tends to zero,

![art](images/Art_P407.jpg)

 

In such a situation, the epistemic uncertainty associated with parameter values ***θ*** vanishes and the uncertainty about *X* reaches its irreducible level, ![art](images/Art_P410.jpg).

In practical cases where the number of observations D < ∞, uncertainty remains about the parameters *f*(***θ***|D), so *f*(*x*|D) is typically more diffused than ![art](images/Art_P411.jpg). The uncertainty associated with parameters *f*(***θ***|D) can be *marginalized* as described in equation 6.6 in order to obtain the *posterior predictive* PDF for the hidden random variable. This integral is typically not analytically tractable, so it is common to resort to the *Monte Carlo sampling methods* presented in the next section in order to compute the posterior predictive expected value and variance for *f*(*x*|D).

 

[*6.5   Monte Carlo*](#toc.xhtml#Rh1-21)

*Monte Carlo* sampling is a numerical integration method that allows performing Bayesian estimation for analytically intractable cases. In this section, we will first see how Monte Carlo can be employed as an integration method. Then, we will explore how this method fits in the context of Bayesian estimation.

 

[*6.5.1   Monte Carlo Integration*](#toc.xhtml#Rh2-29)

We employ the example of a unit diameter circle with area *a* = *xr*² = 0.785 to demonstrate how we can approximate this area with Monte Carlo numerical integration. A circle of diameter *d* = 1 (*r* = 0.5) is described by the equation

(*x* − 0.5)² + (*y* − 0.5)² = *r*².

This equation is employed in the definition of the *indicator function*

![art](images/Art_P412.jpg)

We then define a bivariate uniform probability density in the range {*x, y*} ∈ (0, 1), where *f[XY]* (*x, y*) = 1. The circle area *a* can be formulated as the integral of the product of the indicator function times *f[XY]* (*x, y*),

![art](images/Art_P413a.jpg)

 

We saw in [§3.3.5](#chapter002.xhtml#Sec_3.3.5) that the integral in equation 6.7 corresponds to the *expectation* of the indicator function *I*(*X, Y*). Given S random samples {*x[s], y[s]*}, *s* ∈ {1, 2, ⋯ , S} generated from a uniform probability density *f[XY]* (*x, y*), the expectation operation is defined as

![art](images/Art_P414.jpg)

In practice, because the number of samples S is finite, our estimation will remain an approximation of the expectation,

![art](images/Art_P415.jpg)

**Note:** The hat in ![art](images/Art_P417.jpg)denotes that the quantity is an approximation of ![art](images/Art_P418.jpg).

[Figure 6.18](#chapter005.xhtml#Fig_6-18) presents realizations for S = {10², 10³, 10⁴} samples as well as their approximation of the area *a*. As the number of samples increases, the approximation error decreases and ![art](images/Art_P416.jpg)tends to the true value of *a* = *πr*² = 0.785.

![art](images/Art_P413.jpg)

Figure 6.18: Examples of Monte Carlo numerical integration for which the theoretical answer is *a* = *πr*² = 0.785.

The interesting property of Monte Carlo integration is that the estimation quality, measured by the variance var ![art](images/Art_P419.jpg), depends on the *number of samples* and *not on the number of dimensions*.^([4](#chapter005.xhtml#footnote_4)) This property is key for the application of the Monte Carlo method in high-dimensional domains.

 

[*6.5.2   Monte Carlo Sampling: Continuous State Variables*](#toc.xhtml#Rh2-30)

**Monte Carlo sampling**

*h*(*x*): Sampling PDF

*x[s]* : *X* ~ *h*(*x*)

*s* ∈ {1, 2, ⋯ ,S}

Monte Carlo methods are now applied to the Bayesian estimation context presented in [§6.3](#chapter005.xhtml#Sec_6.3) where we are interested in estimating continuous state variables. The Monte Carlo integration method is first employed for approximating the evidence

![art](images/Art_P420.jpg)

A Monte Carlo approximation of the evidence can be computed using *importance sampling* where

![art](images/Art_P421.jpg)

where samples *x[s]* : *X* ~ *h*(*x*) are drawn from any sampling distribution such that *h*(*x*) > 0 for any *x* for which the PDF on the numerator *f*(D|*x*) · *f*(*x*) > 0. If we choose the prior PDF as sampling distribution, *h*(*x*) = *f*(*x*), the formulation simplifies to

![art](images/Art_P422.jpg)

 

because the prior and the sampling distribution cancel out.

The performance of the Monte Carlo integration depends on how close our sampling distribution *h*(*x*) is to the posterior *f*(*x*|D). Note that sampling from the prior, *h*(*x*) = *f*(*x*), is often not a viable option when the number of observations D is large. This is because in such a case, the likelihood is the product of several terms so the probability content typically ends up being concentrated in a small region that is not well described by the prior, as illustrated in [figure 6.19](#chapter005.xhtml#Fig_6-19).

![art](images/Art_P423.jpg)

Figure 6.19: Example of difficult situation encountered when trying to sample from the prior.

The posterior mean and variance can be approximated with Monte Carlo integration using

![art](images/Art_P424.jpg)

and

![art](images/Art_P425.jpg)

For both the posterior mean and variance, when choosing the prior as the sampling distribution, *h*(*x*) = *f*(*x*), it cancels out from the formulation.

*Example: Concentration estimation*   [Figure 6.20](#chapter005.xhtml#Fig_6-20) depicts a laboratory test for measuring a deterministic mercury concentration ![art](images/Art_P427.jpg). Observations follow the observation model

![art](images/Art_P428.jpg)

![art](images/Art_P426.jpg)

Figure 6.20: Example of Bayesian estimation with censored observations.

(Photo: Elevate)

where the measuring device has a minimum threshold and the mutually independent observation errors are described by

*v[i]* : *V[i]* ~ N (*v*; 0, 2²), *V[i]* ╨ *V[j]*, ∀*i* ≠ *j*.

We want to estimate the posterior PDF describing the concentration if the observation obtained is D = {error} for two hypotheses regarding the prior knowledge: (1) uniform in the interval (0, 50), *f*(*x*) = U(*x*; 0, 50), and (2) a normal PDF with mean 25 and standard deviation 10, *f*(*x*) = N(*x*; 25, 10²). [Figure 6.21](#chapter005.xhtml#Fig_6-21) presents the results for the (a) uniform prior and (b) normal prior. Note that only 100, out of the 10⁵ Monte Carlo samples that were employed to estimate the evidence *f*(D), are displayed. This example illustrates how information can be extracted from censored observations. Note also how the choice of prior influences the posterior knowledge. The choice of prior is particularly important here because limited information is carried by the censored observations.

![art](images/Art_P429.jpg)

Figure 6.21: Comparative example of a uniform and normal prior PDF for performing Bayesian estimation with censored observations.

We consider a different context where we employ D = 100 direct observations, D = {25.4, 23.6, 24.1, ⋯ , 24.3}[1×100], and the prior is *p*(*x*) = U(*x*; 0, 50). The prior, likelihood, and posterior are presented in [figure 6.22](#chapter005.xhtml#Fig_6-22). Note that here, out of the 100 Monte Carlo samples displayed, none lie in the high probability region for the likelihood. As a result, it leads to a poor approximation of the evidence where the true value is *f*(*D*) = 1.19 × 10^(−78) and where the approximation is

![art](images/Art_P431.jpg)

![art](images/Art_P430.jpg)

Figure 6.22: Example where drawing Monte Carlo samples from the prior leads to a poor estimate of the posterior because no sample falls in the high probability region.

 

Although it is possible to solve this problem by increasing the number of samples, this approach is computationally inefficient and even becomes impossible for high-dimensional domains. [Chapter 7](#chapter006.xhtml) presents advanced Monte Carlo methods for solving this limitation.

 

[*6.5.3   Monte Carlo Sampling: Parameter Estimation*](#toc.xhtml#Rh2-31)

For D observations D = {*y*[1], *y*[2], ⋯ , *y*[D]}, and samples ***θ***[*s*] ~ *h*(***θ***) = *f*(***θ***), *s* ∈ {1, 2, ⋯ , S} drawn from the prior PDF of parameters, we can estimate the evidence

![art](images/Art_P432.jpg)

as well as the posterior expected values and variance for parameters

![art](images/Art_P432a.jpg)

*Example: Concrete strength*   We consider the case where we want to characterize the resistance *R* of a given concrete batch, where the intrinsic variability is estimated by testing the resistance from several samples, as depicted in [figure 6.23](#chapter005.xhtml#Fig_6-23). We assume that the true yet unknown parameter values are ![art](images/Art_P434.jpg)and ![art](images/Art_P435.jpg)and that the resistance *R* is described by a log-normal random variable

![art](images/Art_P436.jpg)

![art](images/Art_P433.jpg)

Figure 6.23: Example of samples taken from the same concrete batch.

The unknown parameters we want to learn about are ***θ*** = \[*µ[R] σ[R]*\]^(**T**). Here, *R* is a hidden random variable because it is not directly observed; only imprecise observations *y[i]* are available. The set of observations D = {*y*[1], *y*[2], ⋯ , *y*[D]} is employed to estimate the posterior PDF for the parameters ***θ*** that are controlling the PDF of the hidden random variable *X*,

![art](images/Art_P437.jpg)

 

The joint prior knowledge for parameters *f*(*µ[R]*, *σ[R]*) = *f*(*µ[R]*) · *f*(*σ[R]*), (*µ[R]* ╨ *σ[R]*) is obtained from the product of the marginal PDFs,

![art](images/Art_P438.jpg)

The prior PDF for *µ[R]* and *σ[R]* are themselves described by log-normal PDFs with respective mean ![art](images/Art_P439.jpg)and variance ![art](images/Art_P440.jpg).

The observation model is ln *y[i]* = ln *r[i]* + *v[i]*, where the observation errors *v[i]* : *V* ~ N (*v*; 0, 0.01²) MPa. With these assumptions regarding the observation model, the marginal likelihood for each observation is

![art](images/Art_P441.jpg)

and the joint likelihood for the entire set of observations is

![art](images/Art_P442.jpg)

Note that the marginal and joint likelihood are defined as a function of the log-space parameters. In order to evaluate the likelihood for the parameters {*µ[R]*, *σ[R]*}, we employ the transformation functions given in equation 4.4. Note that the likelihood *f*(**y**|***θ***) describes a probability density only for **y** and not for ***θ***. Therefore this re-parametrization ***θ***[ln] = fct(***θ***) of the likelihood does not require using the change of variable rule we saw in [§3.4](#chapter002.xhtml#Sec_3.4).

[Figure 6.24](#chapter005.xhtml#Fig_6-24) presents the prior PDF for parameters, the likelihood, the posterior, and the posterior predictive for (a) D = 1, (b) D = 5, and (c) D = 100 observations. We see that, as the number of observations D increases, the likelihood and posterior for ***θ*** become concentrated around the true values, and the posterior predictive for *R* tends toward the true PDF with parameters ![art](images/Art_P443.jpg)and ![art](images/Art_P444.jpg).

![art](images/Art_P445.jpg)

Figure 6.24: Examples of Bayesian estimation as a function of the number of observations employed, D = {1, 5, 100}.

 

[*6.6   Conjugate Priors*](#toc.xhtml#Rh1-22)

The previous section went through the process of using numerical approximation methods for estimating the posterior PDF for the parameters of a hidden random variable *X*. This complex process is necessary when no analytical formulation exists to describe the posterior.

For specific combinations of *prior* distribution and *likelihood* function, the *posterior* PDF follows the same type of distribution as the prior PDF. These specific combinations are referred to as *conjugate priors*. For conjugate priors, analytic formulations are available to describe the posterior PDF of parameters *f*(***θ***|D) as well as the posterior predictive *f*(*x*|D).

One classic example of conjugate prior is the *Beta-Binomial*. Take, for example, the probability that a thumbtack (see [figure 6.25](#chapter005.xhtml#Fig_6-25)) lands on either *Head* or *Tail*, S = {Head (H), Tail (T)}. We can employ the Beta-Binomial conjugate prior to describe the posterior PDF for *x* = Pr(Head|D) ∈ (0, 1), given a set of observations D. It is suited in this case to assume that the prior PDF for *x* = Pr(Head) follows a Beta PDF,

![art](images/Art_P447.jpg)

where **B**(*α, β*) is the normalization constant. In this case, observations are binary, so for a set containing D = D[H] + D[T] observations, heads are assigned the outcome ![art](images/Art_P448.jpg)and tails are assigned the outcome ![art](images/Art_P449.jpg). In that case, the likelihood describing the probability of observing D[H] heads and D[T] tails follows a Binomial distribution,

![art](images/Art_P450.jpg)

![art](images/Art_P451.jpg)

![art](images/Art_P446.jpg)

Figure 6.25: Thumbtacks described by a random variable with sample space S = {Head (H), Tail(T)}.

(Photo: Michel Goulet)

The multiplication of the prior and the likelihood remains analytically tractable so that

![art](images/Art_P452.jpg)

and by recalculating the normalization constant, we find that the posterior also follows a Beta PDF with parameters *α*+D[H] and *β* +D[T],

![art](images/Art_P453.jpg)

The analytic formulation for conjugate priors with their parameters, likelihood, posterior, and posterior predictive can be found online^([5](#chapter005.xhtml#footnote_5)) or in specialized publications such as the compendium by Murphy.^([6](#chapter005.xhtml#footnote_6))

 

*Example: Traffic safety*   We take as another example an intersection where the number of users is *u* = 3 × 10⁵/yr and where 20 accidents occurred over the last 5 years. Note that for the purpose of simplicity, the number of passages without accidents is taken as the total number of users rather than this number minus the number of accidents. This current information can be summarized as

![art](images/Art_P454.jpg)

Our prior knowledge for *x*, the probability of accident per user, is described by the Beta PDF *f*(*x*) = B(*x*; 1, 1), where the parameters are *α*[0] = *β*[0] = 1, which corresponds to a uniform distribution over the interval (0, 1). The posterior PDF describing the daily probability of accident given the observations D[old] is thus also described by the Beta PDF,

*f*(*x*|D[old]) = B(*x*; *α*[0] + D[A], *β*[0] + *D*[N]).

![art](images/Art_P455.jpg)

Figure 6.26: Example of application of conjugate priors on traffic data.

(Photo: John Matychuk)

[Figure 6.27](#chapter005.xhtml#Fig_6-27) presents the posterior PDF transformed in the log[10]\-space using the change of variable rule (see [§3.4](#chapter002.xhtml#Sec_3.4)),

![art](images/Art_P456.jpg)

![art](images/Art_P457.jpg)

Figure 6.27: Posterior PDF for the probability of an accident *before* refection works.

Now, we consider that following refection works made on the intersection in order to decrease the probability of accidents, we observe *a* = 1 accident over a period of one year, that is, 3 × 10⁵ users without accident. In order to estimate the new probability of accident, we assume that our previous posterior knowledge *f*(*x*|D[old]) is an upper-bound for *X*, because the refection works made the intersection safer. The new posterior then becomes

![art](images/Art_P458.jpg)

Note that because the prior is now described by the complement of the CDF of *X*|D[old], which is not a conjugate prior, the posterior does not have an analytic solution anymore, and the evidence *f*(D[new]) must be approximated using numerical integration. [Figure 6.28](#chapter005.xhtml#Fig_6-28) presents the prior, 1 − *F* (*x|D*[old]) and posterior PDF, *f*(*x*|D), for the probability of an accident after the intervention. The posterior predictive probability of an accident before the refection works was 1.3 × 10^(−5) compared to 5.8 × 10^(−6) after.

![art](images/Art_P459.jpg)

Figure 6.28: Prior and posterior PDF for the probability of an accident *after* refection works.

  

[*6.7   Approximating the Posterior*](#toc.xhtml#Rh1-23)

For complex machine learning models such as those that will be covered in the next chapters, conjugate priors are often not applicable, and it can be computationally prohibitive to rely on sampling methods for performing Bayesian estimation. In those cases, we may have to employ *point estimates* rather than a probability density function for describing the posterior PDF of model parameters.

 

[*6.7.1   Maximum Likelihood and Posterior Estimates*](#toc.xhtml#Rh2-32)

Instead of estimating the posterior using a Bayesian approach, a common approximation is to find a single set of optimal parameter values ***θ***^∗ that maximizes the likelihood (MLE) or the product of the likelihood and the prior (MAP) where

![art](images/Art_P460.jpg)

Optimization methods covered in [chapter 5](#chapter004.xhtml) can be employed to identify ***θ***^∗. Note that it is common to perform the optimization using a log-transformed objective function, for example, ln(*f*(D|***θ***), for numerical stability reasons (see equation 6.5). Note that it is equivalent to optimize either the original or the log-transformed objective function,

![art](images/Art_P461.jpg)

Estimating only the most likely value with respect to either the MAP or MLE criterion can lead to a negligible approximation error when applied to *identifiable* problems (see [§6.3.4](#chapter005.xhtml#Sec_6.3.4)), where the amount of independent data is large; in that case, the posterior is concentrated around a single value *f*(***θ***|D) *→ δ*(*θ^∗*). When the set of observations is small, in the case of a multimodal posterior, or for *non-identifiable* problems, estimating only *θ^∗* is no longer a good approximation of the posterior. The definition of what is a *small* or a *large* data set is problem dependent. In simple cases, data sets containing fewer than 10 observations will typically lead to significant epistemic uncertainty associated with unknown parameter values. Cases involving complex models, such as those treated in [chapter 12](#chapter011.xhtml), may need tens of thousands (D ∝ 10⁵) of observations to reach the point where the epistemic uncertainty associated with unknown parameter values is negligible.

We saw in [§5.5](#chapter004.xhtml#Sec_5.5) that it is common to resort to parameter-space transformations in order to perform optimization in an unconstrained domain. For an MLE, the quantity maximized is the likelihood of observations **y**, given the parameters ***θ***. Because *f***(y** |***θ***) describes a probability density only for **y** and not for ***θ***, a parameter-space transformation for an MLE does not require using the change of variable rule we saw in [§3.4](#chapter002.xhtml#Sec_3.4). On the other hand, the MAP seeks to maximize the product of the likelihood and the prior, *f***(y**|***θ***)*·f*(***θ***). Here, the prior is a probability density, so the change of variable rule applies when we employ space transformations. Nevertheless, as we saw in [figure 3.19](#chapter002.xhtml#Fig_3-19), when a PDF is subject to a nonlinear transformation, the modes in the original and transformed spaces do not coincide. Therefore, the MLE is invariant to parameter-space transformations and the MAP is not.^([7](#chapter005.xhtml#footnote_7)) Note that Bayesian estimation is invariant to parameter-space transformations, given that we apply the change of variable rule. We will apply parameter-space transformations in the context of Bayesian estimation in [chapter 7](#chapter006.xhtml).

 

[*6.7.2   Laplace Approximation*](#toc.xhtml#Rh2-33)

Another method for approximating a posterior PDF for the unknown parameters of a hidden random variable is the *Laplace approximation*. This method approximates the posterior as a multivariate Normal with a posterior mean vector equal to either the MLE or MAP estimate ***θ***^∗, and a posterior covariance Σ[***θ***∗],

![art](images/Art_P462.jpg)

When we choose the MLE approximation to describe the posterior mode, the posterior covariance is approximated by the inverse Hessian matrix of the negative log-likelihood evaluated at *θ^∗*,

![art](images/Art_P463.jpg)

Details regarding the numerical estimation of the Hessian are presented in [§5.4](#chapter004.xhtml#Sec_5.4). In order to include prior knowledge, we have to estimate the Laplace approximation using ln(*f*(D|***θ***^∗) · *f*(***θ***^∗)) instead of the log-likelihood ln *f*(D|***θ***^∗) alone.

The relation between the second derivative of the log-likelihood evaluated at ***θ***^∗ and the covariance Σ[***θ***∗] can be explained by looking at the multivariate Normal with probability density function described by

 

![art](images/Art_P464.jpg)

where P is the number of parameters ***θ*** = \[*θ*[1]*θ*[2] ⋯ *θ*[P]\]^(**T**). By taking the natural logarithm of *f*(*θ*), we obtain

![art](images/Art_P465.jpg)

where the derivative of ln *f*(***θ***) with respect to ***θ*** is

![art](images/Art_P466.jpg)

If we differentiate this last expression a second time with respect to ***θ***, we obtain

![art](images/Art_P467.jpg)

This development shows how the Laplace approximation allows estimating the covariance matrix using the posterior PDF’s curvatures.

In the case of a Gaussian log-posterior, the second-order derivatives are constant, so the curvatures can be evaluated anywhere in the domain. In practice, we employ the Laplace approximation when the posterior is not Gaussian; in order to minimize the approximation error, we evaluate the second-order derivatives of the log-posterior at the MLE or MAP ***θ***^∗, where the probability density is the highest.

[Figure 6.29](#chapter005.xhtml#Fig_6-29) presents an example of an application of the Laplace approximation, where a generic posterior PDF for two parameters is approximated by a bivariate Normal PDF. The Hessian matrix evaluated at the mode ***θ***^∗ = \[−1.47 0.72\]^(**T**) is

![art](images/Art_P469.jpg)

![art](images/Art_P468.jpg)

Figure 6.29: Example of an application of the Laplace approximation to describe a posterior PDF.

so the Laplace approximation of the posterior covariance is described by

![art](images/Art_P470.jpg)

The closer the posterior is to a multivariate Normal, the better the Laplace approximation is. Note that for problems involving several parameters, computing the Hessian matrix using numerical derivatives becomes computationally prohibitive. One possible approximation is to estimate only the main diagonal of the Hessian. The main diagonal of the Hessian contains information about the variances of the posterior with respect to each variable without providing information about the covariances (i.e., the pairwise linear dependencies between variables).

In addition to being employed to approximate the posterior PDF, the Laplace approximation can be used to estimate the evidence *f*(D). With the Laplace approximation, the posterior is

![art](images/Art_P471.jpg)

In equation 6.9, (a) corresponds to the normalization constant for the exponential term indicated in (b), for which the value is exp(0) = 1 when evaluated at the mode ***θ***^∗ (see [§4.1](#chapter003.xhtml#Sec_4.1)). When estimating ![art](images/Art_P472.jpg)using either an MAP ![art](images/Art_P473.jpg)or an MLE ![art](images/Art_P474.jpg), its value is not going to equal 1. Therefore, the normalization constant in (a) must be multiplied by the value of the unnormalized posterior evaluated at the mode ***θ***^∗ so that

![art](images/Art_P475.jpg)

The reader interested in the formal derivation of this result from a Taylor-series expansion should consult MacKay.^([8](#chapter005.xhtml#footnote_8))

 

[*6.8   Model Selection*](#toc.xhtml#Rh1-24)

In the concrete strength estimation example presented in [§6.5.3](#chapter005.xhtml#Sec_6.5.3), it is known that the data was generated from a log-normal distribution. In real-life cases, the PDF form for the hidden random variable *X* may either remain unknown or not correspond to an analytically tractable probability density function. In these cases, it is required to compare the performance of several *model classes* at explaining the observations D.

Given a set of M*model classes m* ∈ M = {1, 2, ⋯ , M}, the posterior probability of each class given D is described using Bayes rule,

![art](images/Art_P476.jpg)

**Note:** With Bayesian model selection, the objective is not to identify the single best model; it allows quantifying the posterior probability of each model, which can be employed for performing subsequent predictions.

where *p*(*m*|D) and *p*(*m*) are respectively the posterior and prior probability mass functions for the model classes. The likelihood of a model class *m* is obtained by marginalizing the model parameters from the joint distribution of observations and parameters,

![art](images/Art_P477.jpg)

where ***θ***^({*m*}) is the set of parameters associated with the model class *m*. The likelihood of a model class in equation 6.12 corresponds to its evidence, which also corresponds to the normalization constant from the posterior PDF for its parameters,

![art](images/Art_P478.jpg)

The normalization constant for the model comparison problem presented in equation 6.11 is obtained by summing the likelihood of each model class times its prior probability,

![art](images/Art_P479.jpg)

Note that using the importance-sampling procedure presented in equation 6.8 for estimating the normalization constants in equation 6.13 is only a viable option for simple problems involving a small number of parameters and a small number of observations. [Section 7.5](#chapter006.xhtml#Sec_7.5) further discusses the applicability of more advanced sampling methods for estimating *f*(D).

Here, we revisit the concrete strength example presented in [§6.5.3](#chapter005.xhtml#Sec_6.5.3). We compare the posterior probability for two model classes *m* ∈ *M* = {L, N} (i.e., a log-normal and a Normal PDF); note that we know the correct hypothesis is *m* = L because simulated data were generated using a log-normal PDF.

For D = 5 observations, the evidence of each model is

*f*(D|L) = 8.79 × 10^(−7)

*f*(D|N) = 6.44 × 10^(−7).

With the hypothesis that the prior probability of each model is equal, *p*(L) = *p*(N) = 0.5, the posterior probability for model classes *m* are

![art](images/Art_P480.jpg)

 

This result indicates that both models predict with almost equal performance the observations D. Therefore, if we want to make predictions for unobserved quantities, it is possible to employ both models where the probability of each of them is quantified by its posterior probability *p*(*m*|D).

In practice, because estimating the evidence *f*(D|*m*) is a computationally demanding task, it is common to resort to approximations such as the *Akaike information criterion* (AIC) and *Bayesian information criterion* (BIC) for comparing model classes. Note that the BIC is a special case derived from the Laplace approximation in equation 6.10 for estimating *f*(D). Other advanced approximate methods for comparing model classes are the *Deviance information criterion*^([9](#chapter005.xhtml#footnote_9)) (DIC) and the *Watanabe-Akaike information criterion*^([10](#chapter005.xhtml#footnote_10)) (WAIC). The reader interested in these methods should refer to specialized textbooks.^([11](#chapter005.xhtml#footnote_11)) Another common model selection technique widely employed in machine learning is *cross-validation*; the main idea consists in employing a first subset of data to estimate the model parameter and then test the predictive performance of the model using a second independent data set. The details regarding cross-validation are presented in [§8.1.2](#chapter007.xhtml#Sec_8.1.2), where the method is employed to discriminate among model structures in the context of regression problems.

 

 

*Exercises*

 
| P6.1 || Explain the difference between a posterior, a prior, and a likelihood function. |
| --- | --- |
| P6.2 || Explain what a non-informative prior is. |
| P6.3 || Explain why it is hard to compute the normalization constant *f*(D). |
| P6.4 || Explain in what circumstances the prior plays an important role and when it has a negligible role. |
| P6.5 || Explain what a censored observation is. |
| P6.6 || Explain why, in the context of importance sampling, when the number of observations D is large, it is typically not efficient to draw samples from the prior in order to estimate *f*(D). |
| P6.7 || Explain what a posterior predictive PDF is. |
| P6.8 || Explain what a non-identifiable problem is and what we can do about it. |
| P6.9 || Explain what the main difficulty is when using Bayesian model selection. |
| P6.10 || Explain what a conjugate prior is and why it is computationally efficient. |
| P6.11 || Given the prior failure probability of a pipe Pr(F) = 0.001 and an observation *y* ∈ {+, −} from a non-destructive test with a likelihood![art](images/Art_P481.jpg)compute the posterior probabilities of a pipe failure for both measurement outcomes Pr(F|+) and Pr(F|−), and explain why Pr(F|+) ≠ Pr(F|−). |
| P6.12 || For the observation models below, formulate the likelihood for a set of observations D = {*y*[1], *y*[2], ⋯ , *y*[D]}.a) ![art](images/Art_P482.jpg)b) ![art](images/Art_P483.jpg)c) ![art](images/Art_P484.jpg) |

 

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter005.xhtml#footnote_ref_1) Gelman, A., J. B. Carlin, H. S. Stern, and D. B. Rubin (2014). *Bayesian data analysis* (3rd ed.). CRC Press.

[²](#chapter005.xhtml#footnote_ref_2) Box, G. E. P. and G. C. Tiao (1992). *Bayesian inference in statistical analysis*. Wiley.

[³](#chapter005.xhtml#footnote_ref_3) This example is adapted from Armen Der Kiureghian’s CE229 course at UC Berkeley.

[⁴](#chapter005.xhtml#footnote_ref_4) MacKay, D. J. C. (1998). Introduction to Monte Carlo methods. In *Learning in graphical models*, pp. 175–204. Sprigner.

[⁵](#chapter005.xhtml#footnote_ref_5) Wikipedia (2017). Conjugate prior. URL [https://en.wikipedia.org/wiki/conjugate\_prior](https://en.wikipedia.org/wiki/conjugate_prior). Accessed November 8, 2019.

[⁶](#chapter005.xhtml#footnote_ref_6) Murphy, K. P. (2007). Conjugate Bayesian analysis of the Gaussian distribution. Citeseer.

[⁷](#chapter005.xhtml#footnote_ref_7) Jermyn, I. H. (2005). Invariant Bayesian estimation on manifolds. *The Annals of Statistics 33* (2), 583–605.

[⁸](#chapter005.xhtml#footnote_ref_8) MacKay, D. J. C. (2003). *Information theory, inference, and learning algorithms*. Cambridge University Press.

[⁹](#chapter005.xhtml#footnote_ref_9) Spiegelhalter, D. J., N. G. Best, B. P. Carlin, and A. van der Linde (2002). Bayesian measures of model complexity and fit. *Journal of the Royal Statistical Society: Series B (Statistical Methodology) 64* (4), 583–639.

[^(10)](#chapter005.xhtml#footnote_ref_10) Watanabe, S. (2010). Asymptotic equivalence of Bayes cross validation and widely applicable information criterion in singular learning theory. *Journal of Machine Learning Research 11*, 3571–3594.

[^(11)](#chapter005.xhtml#footnote_ref_11) Burnham, K. P. and D. R. Anderson (2002). *Model selection and multimodel inference: A practical information-theoretic approach* (2nd ed.). Springer; and Gelman, A., J. B. Carlin, H. S. Stern, and D. B. Rubin (2014). *Bayesian data analysis* (3rd ed.). CRC Press.

[*7*](#toc.xhtml#chap-6)

[*Markov Chain Monte Carlo*](#toc.xhtml#chap-6)

The *importance sampling* method was introduced in [chapter 6](#chapter005.xhtml) for estimating the normalization constant of a posterior probability density function (PDF) as well as its expected values and covariance. A limitation of this approach is related to the difficulties associated with the choice of an efficient sampling distribution *h*(·). The sampling methods covered in this chapter address this limitation by providing ways of sampling directly from the posterior using Markov chain Monte Carlo (MCMC) methods.

*Markov chain Monte Carlo* takes its name from the *Markov property*, which states:

*Given the present, the future is independent from the past*.

It means that if we know the current state of the system, we can predict future states without having to consider past states. Starting from *X[t]* ~ *p*(*x[t]*), we can transition to *x*[*t*+1] using a transition probability *p*(*x*[*t*+1]|*x[t]*) that only depends on *x[t]*. It implicitly conveys that the conditional probability depending on *x[t]* is equivalent to the one depending on *x*[1:*t*],

*p*(*x*[*t*+1]|*x[t]*) = *p*(*x*[*t*+1]|*x*[1], *x*[2], ⋯ , *x[t]*).

A *Markov chain* defines the joint distribution for random variables by combining the chain rule (see [§3.3.4](#chapter002.xhtml#Sec_3.3.4)) and the Markov property so that

![art](images/Art_P485.jpg)

The idea behind MCMC is to construct a Markov chain for which the stationary distribution is the posterior. Conceptually, it corresponds to *randomly walking* through the parameter space so that the *fraction of steps spent* at exploring each part of the domain is proportional to the posterior density. [Figure 7.1](#chapter006.xhtml#Fig_7-1) presents an example of a random walk generated with MCMC that follows the density described by the underlying contour plot.

![art](images/Art_P486.jpg)

Figure 7.1: Example of random walk generated with MCMC.

Several MCMC methods exist: Metropolis-Hastings, Gibbs sampling, slice sampling, Hamiltonian Monte Carlo, and more. This chapter covers only the Metropolis and Metropolis-Hastings methods because they are the most accessible. The reader interested in advanced methods should refer to dedicated textbooks such as the one by Brooks et al.^([1](#chapter006.xhtml#footnote_1))

 

[*7.1   Metropolis*](#toc.xhtml#Rh1-25)

**Notation**

Initial state: ***θ***[0]

Target distribution: ![art](images/Art_P487.jpg)

Proposal distribution: *q*(***θ***′|***θ***)

The *Metropolis* algorithm^([2](#chapter006.xhtml#footnote_2)) was developed during the Second World War while working on the Manhattan project (i.e., the atomic bomb) at Los Alamos, New Mexico. Metropolis is not the most efficient sampling algorithm, yet it is a simple one allowing for an easy introduction to MCMC methods.

The Metropolis algorithm requires defining an *initial state* for a set of P parameters ![art](images/Art_P488.jpg), a target distribution ![art](images/Art_P489.jpg)corresponding to the unnormalized posterior we want to sample from, and a *proposal distribution*, *q*(***θ***′|***θ***), which describes where to move next given the current parameter values. The proposal must have a *nonzero probability to transit from the current state to any state* supported by the *target distribution* and must be *symmetric*, that is,

*q*(***θ***′|***θ***) = *q*(***θ***|***θ***′).

The *Normal distribution* (see [§4.1](#chapter003.xhtml#Sec_4.1)) is a common general-purpose proposal distribution,

*q*(***θ***′|***θ***) = N (***θ***′; ***θ***, Σ*[q]*),

where the mean is defined by the current position and the probability to move in a region around the current position is controlled by the covariance matrix Σ*[q]*. [Figure 7.2](#chapter006.xhtml#Fig_7-2) presents an example of 1-D and 2-D Normal proposal distributions.

![art](images/Art_P490.jpg)

Figure 7.2: Examples of 1-D and 2-D proposal distributions, *q*(***θ***′|***θ***).

The Metropolis algorithm is recursive so at the *s*^(th) step, given a current position in the parameter space ***θ*** = ***θ**[s]*, we employ *q*(***θ***′|***θ***) to propose moving to a new position ***θ***′. If the target distribution evaluated at the proposed location is greater than or equal to the current one, that is, ![art](images/Art_P492.jpg)—we accept the proposed location. If the proposed location has a target value that is lower than the current one, we accept moving to the proposed location with a probability equal to the *acceptance ratio*![art](images/Art_P493.jpg). In the case where the proposed location is rejected, we stay at the current location and ***θ***[*s*+1] = ***θ**[s]*. Each step from the Metropolis sampling method is formalized in [algorithm 4](#chapter006.xhtml#Tab_4).

**Note:** In order to accept a proposed location with a probability equal to ![art](images/Art_P491.jpg), we compare it with a sample *u* taken from U(0, 1). If *u* ≤ *r*, we accept the move; otherwise, we reject it.

**Algorithm 4:** Metropolis sampling

![art](images/Art_P494.jpg)

If we apply this recursive algorithm over S iterations, the result is that the fraction of the steps spent exploring each part of the domain is proportional to the density of the target distribution ![art](images/Art_P495.jpg). Note that this last statement is valid under some conditions regarding the chain starting location and number of samples S that we will further discuss in [§7.3](#chapter006.xhtml#Sec_7.3). If we select a target distribution that is an unnormalized posterior, it implies that each sample ***θ**[s]* is a realization of that posterior, ***θ**[s]* : ***θ*** ~ *f*(D|***θ***) · *f*(***θ***).

[Figure 7.3](#chapter006.xhtml#Fig_7-3) presents a step-by-step application of [algorithm 4](#chapter006.xhtml#Tab_4) for sampling a given target density ![art](images/Art_P496.jpg). The proposal distribution employed in this example has a standard deviation *σ[q]* = 1. At step *s* = 1, the target value at the proposed location *θ′* is greater than at the current location *θ*, so the move is accepted. For the second step, *s* = 2, the target value at the proposed location is smaller than the value at the current location. The move is nevertheless accepted because the random number *u* drawn from U(0, 1) turned out to be smaller than the ratio ![art](images/Art_P497.jpg). At step *s* = 3, the target value at the proposed location *θ′* is greater than the value at the current location *θ*, so the move is accepted. [Figure 7.3d](#chapter006.xhtml#Fig_7-3) presents the chain containing a total of S = 2400 samples. The superposition of the sample’s histogram and the target density confirms that the Metropolis algorithm is sampling from ![art](images/Art_P498.jpg).

![art](images/Art_P499.jpg)

Figure 7.3: Step-by-step example of 1-D Metropolis sampling.

  

[*7.2   Metropolis-Hastings*](#toc.xhtml#Rh1-26)

The *Metropolis-Hastings* algorithm^([3](#chapter006.xhtml#footnote_3)) is identical to the Metropolis algorithm except that it allows for *nonsymmetric transition probabilities* where

*q*(***θ***′|***θ***) ≠ *q*(***θ***|***θ***′).

The main change with Metropolis-Hastings is that when the proposed location ***θ**′* has a target value that is lower than the current location ***θ***, we accept the proposed location with a probability equal to the ratio ![art](images/Art_P500.jpg)times the ratio ![art](images/Art_P501.jpg), that is, the ratio of the probability density of going from the proposed location to the current one, divided by the probability density of going from the current location to the proposed one.

Applying Metropolis-Hastings only requires replacing line 9 in [algorithm 4](#chapter006.xhtml#Tab_4) with the new acceptance ratio,

![art](images/Art_P502.jpg)

In the particular case where transition probabilities are symmetric, that is, *q*(***θ***′|***θ***) = *q*(***θ***|***θ***′), then Metropolis-Hastings is equivalent to Metropolis. Note that when we employ a Normal proposal density for parameters defined in the unbounded real domain, ***θ*** ∈ ℝ^P, then there is no need for Metropolis-Hastings. On the other hand, using Metropolis-Hastings for sampling bounded domains requires modifying the proposal density at each step. [Figure 7.4](#chapter006.xhtml#Fig_7-4) illustrates why if we employ a truncated Normal PDF as a proposal, *q*(*θ*′|*θ*) ≠ *q*(*θ|θ′*) because the normalization constant needs to be recalculated at each iteration. [Section 7.4](#chapter006.xhtml#Sec_7.4) shows how to leverage transformation functions *θ*^(tr) = *g*(*θ*) in order to transform a bounded domain into an unbounded one *θ*^(tr) ∈ ℝ so that the Metropolis method can be employed.

![art](images/Art_P503.jpg)

Figure 7.4: Example illustrating how, when using a truncated Normal PDF as a proposal, *q*(*θ′|θ*) ≠ *q*(*θ|θ′*).

 

[*7.3   Convergence Checks*](#toc.xhtml#Rh1-27)

So far, the presentation of the Metropolis and Metropolis-Hastings algorithms overlooked the notions of convergence. For that, we need to further address two aspects: the *burn-in phase* and *convergence metrics*.

 

[*7.3.1   Burn-In Phase*](#toc.xhtml#Rh2-34)

For samples taken with an MCMC method, in order to be considered as realizations from the stationary distribution describing the target PDF, a chain must have *forgotten where it started from*. Depending on the choice of initial state *θ*[0] and transition PDF, the sampling procedure may initially stay trapped in a part of the domain so that the sample’s density is not representative of the target density. As depicted in [figure 7.5](#chapter006.xhtml#Fig_7-5), this issue requires discarding samples taken before reaching the stationary distribution. These discarded samples are called the *burn-in phase*. In practice, it is common to discard the first half of each chain as the burn-in phase and then perform the convergence check that will be further detailed in [§7.3.2](#chapter006.xhtml#Sec_7.3.2).

![art](images/Art_P504.jpg)

Figure 7.5: The impact of the initial starting location on MCMC sampling.

[Figure 7.6](#chapter006.xhtml#Fig_7-6) presents an example adapted from Murphy,^([4](#chapter006.xhtml#footnote_4)) where given a current location *x* ∈ {0, 1, ⋯ , 20}, the transition model is defined so there is an equal probability of moving to the nearest neighbor either on the left or on the right. If we apply this random transition an infinite number of times, we will reach the stationary distribution *p*^((*∞*))(*x*) = 1/21, ∀*x*. Each graph in [figure 7.6](#chapter006.xhtml#Fig_7-6) presents the probability *p*^((*n*))(*x*) of being in any state *x* after *n* transitions from the initial state *x*[0] = 17. Here, we see that even after 100 transitions, the chain has not yet forgotten where it started from because it is still skewed toward *x* = 17. After 400 transitions, the initial state has been forgotten, because in this graph we can no longer infer the chain’s initial value.

![art](images/Art_P505.jpg)

Figure 7.6: The impact of the initial starting location using a stochastic process.

 

[*7.3.2   Monitoring Convergence*](#toc.xhtml#Rh2-35)

Monitoring convergence means assessing whether or not the MCMC samples belong to a stationary distribution. For one-dimensional problems, it is possible to track the convergence by plotting the sample numbers versus their values and identifying visually whether or not they belong to a stationary distribution (e.g., see [figure 7.3](#chapter006.xhtml#Fig_7-3)). When sampling in several dimensions, this visual check is limited. Instead, the solution is to generate samples from multiple chains (e.g., 3–5), each having a different starting location ***θ***[0]. The stationarity of these chains can be quantified by comparing the variance within and between chains using the *estimated potential scale reduction* (EPSR). [Figure 7.7](#chapter006.xhtml#Fig_7-7) illustrates the notation employed to describe samples from multiple chains, where *θ[s,c]* identifies the *s*^(th) sample out of S, from the *c*^(th) chains out of C. Note that because the final number of samples desired is S, a quantity equal to 2S samples must be generated in order to account for those discarded during the burn-in period.

![art](images/Art_P506.jpg)

Figure 7.7: The notation for samples taken from multiple chains.

  

[*7.3.3   Estimated Potential Scale Reduction*](#toc.xhtml#Rh2-36)

The *estimated potential scale reduction*^([5](#chapter006.xhtml#footnote_5)) metric denoted by ![art](images/Rcap.jpg)is computed from two quantities: the within-chains and between-chains variances. The *within-chains* mean *θ*[·*c*] and variance *W* are estimated using

![art](images/Art_P507.jpg)

and

![art](images/Art_P508.jpg)

The property of the within-chains variance is that it underestimates the true variance of samples. The *between-chains* mean *θ*[··] is estimated using

![art](images/Art_P509.jpg)

and the variance between the means of chains is given by

![art](images/Art_P510.jpg)

Contrarily to the within-chain variance *W* , the between-chain estimate

![art](images/Art_P511.jpg)

overestimates the variance of samples. The metric ![art](images/Rcap.jpg)is defined as the square root of the ratio between ![art](images/Vcap.jpg)and *W*,

![art](images/Art_P512.jpg)

Because ![art](images/Vcap.jpg)overestimates and *W* underestimates the variance, ![art](images/Art_P513.jpg)should be greater than one. As illustrated in [figure 7.8](#chapter006.xhtml#Fig_7-8), a value ![art](images/Art_P514.jpg)indicates that the upper and lower bounds have converged to the same value. Otherwise, if ![art](images/Art_P515.jpg), it is an indication that convergence is not reached and the number of samples needs to be increased. In practice, convergence can be deemed to be met when ![art](images/Art_P516.jpg). When generating MCMC samples for ***θ*** = \[*θ*[1]*θ*[2] ⋯ *θ*[P]\]^(**T**), we have to compute the EPSR ![art](images/Art_P517.jpg)for each true value dimension *i* ∈ {1, 2, ⋯ , P}.

![art](images/Art_P519.jpg)

Figure 7.8: The EPSR metric to check for convergence.

[Figures 7.9a–c](#chapter006.xhtml#Fig_7-9) compare the EPSR convergence metric ![art](images/Rcap.jpg)for the Metropolis method applied to a 2-D target distribution using a different number of samples. [Figures 7.9a–c](#chapter006.xhtml#Fig_7-9) are using an isotropic bivariate Normal proposal PDF with *σ[q]* = 1. From the three tests, only the one employing S = 10⁴ samples meets the criterion that we have set here to ![art](images/Art_P518.jpg).

![art](images/Art_P520.jpg)

Figure 7.9: Comparison of the ESPR convergence metric ![art](images/Rcap.jpg)for 100, 1,000, and 10,000 MCMC samples.

  

[*7.3.4   Acceptance Rate*](#toc.xhtml#Rh2-37)

The *acceptance rate β* is the ratio between the number of steps where the proposed move is accepted and the total number of steps. [Figures 7.9a–c](#chapter006.xhtml#Fig_7-9) have an acceptance rate of 60 percent.

In the case presented in [figure 7.9d](#chapter006.xhtml#Fig_7-9), the standard deviation of the proposal was doubled to *σ[q]* = 2. It has the effect of reducing the acceptance rate to 38 percent. The convergence speed of MCMC methods is related to the acceptance rate. For ideal cases involving Normal random variables, the optimal acceptance rate is approximately 23 percent for parameter spaces having five dimensions or more (i.e., P ≥ 5), and approximately 44 percent for cases in one dimension (P = 1).^([6](#chapter006.xhtml#footnote_6)) [Figure 7.10](#chapter006.xhtml#Fig_7-10) presents the relative convergence speed as a function of the acceptance rate for a case involving five dimensions or more (P ≥ 5). Note that there is a wide range of values for *β* with similar efficiency, so the optimal values should not be sought strictly.

![art](images/Art_P521.jpg)

Figure 7.10: Relative convergence speed of MCMC for P ≥ 5 as a function of the acceptance rate *β*.

(Adapted from Rosenthal (2011).)

 

[Figure 7.11](#chapter006.xhtml#Fig_7-11) presents another set of examples applied to a target distribution having a high (negative) correlation between the dimensions *θ*[1] and *θ*[2], and using a fixed number of samples equal to S = 1000. In comparison with the case presented in (a), the case in (b) displays worse ![art](images/Art_P524.jpg)values. This difference is due to the poor choice of correlation coefficient for the proposal PDF in (b); the correlation coefficient of the proposal has a sign that is the opposite of the one for the target PDF. If, like in [figure 7.11c](#chapter006.xhtml#Fig_7-11), the proposal is well selected for the target distribution, the convergence speed will be higher.

![art](images/Art_P522.jpg)

Figure 7.11: Comparison of the EPSR convergence metric ![art](images/Art_P523.jpg)for 1,000 MCMC samples using different proposal distributions.

For trivial cases, it may be possible to infer efficient parameters for proposals from trials and errors or from heuristics. However, for more complex cases involving a large number of dimensions, manual tuning falls short. The next section presents a method for automatically tuning the proposal covariance matrix.

 

[*7.3.5   Proposal Tuning*](#toc.xhtml#Rh2-38)

One generic way to define the proposal PDF is using a multivariate Normal centered on the current state ***θ*** and with covariance matrix *γ*²Σ[***θ***∗],

![art](images/Art_P525.jpg)

where the scaling factor *γ* depends on the number of parameters P. The covariance matrix Σ[***θ***]∗ is an approximation of the posterior covariance obtained using the *Laplace approximation* (see [§6.7.2](#chapter005.xhtml#Sec_6.7.2)) calculated for the *maximum a-posteriori* value (MAP), ***θ***^∗. The MAP value can be estimated using gradient-based optimization techniques such as those presented in [§5.2](#chapter004.xhtml#Sec_5.2).

[Algorithm 5](#chapter006.xhtml#Tab_5) presents a simple implementation of the Metropolis algorithm with convergence checks and with a tuning procedure for the scaling factor *γ*. Note that this algorithm is a minimal example intended to help the reader understand the algorithm flow. Implementations with state-of-the-art efficiency include several more steps.

 

[*7.4   Space Transformation*](#toc.xhtml#Rh1-28)

**Change of variable rule**

*f*[**Y**](**y**) = *f*[**X**](**x**) |det **J[y,x]**|^(−1) (see [§ 3.4](#chapter002.xhtml#Sec_3.4))

When dealing with parameters that are not defined in the unbounded real space, one solution is to employ the Metropolis-Hastings algorithm to account for the non-reversibility of the transitions caused by the domain constraints, as illustrated in [figure 7.4](#chapter006.xhtml#Fig_7-4).

 

**Algorithm 5:** Convergence check and scaling parameter tuning

![art](images/Art_P526.jpg)

Another solution is to transform each constrained parameter in the real space in order to employ the Metropolis algorithm. Transformation functions *θ*^(tr) = *g*(*θ[i]*) suited for this purpose are described in [§3.4](#chapter002.xhtml#Sec_3.4). When working with transformed parameters, the proposal distribution has to be defined in the transformed space,

![art](images/Art_P527.jpg)

where ![art](images/Art_P528.jpg)is estimated using the Laplace approximation, which is itself defined in the transformed space. The target probability can be evaluated in the transformed space using the inverse transformation function *g*^(−1)(***θ***^(tr)), its gradient ![art](images/Art_P529.jpg)evaluated at ***θ***^(tr), and the change of variable rule,

![art](images/Art_P530.jpg)

 

Because each transformation function *g*(*θ[i]*) depends on a single parameter, the determinant of the diagonal Jacobian matrix required for the transformation *g*(*θ*) simplifies to the product of the inverse absolute value of the gradient of each transformation function evaluated at ![art](images/Art_P531.jpg). [Algorithm 6](#chapter006.xhtml#Tab_6) presents a simple implementation of the Metropolis algorithm applied to a transformed space.

**Determinant of a diagonal matrix** ![art](images/Art_P532.jpg)

**Algorithm 6:** Metropolis with transformed space

![art](images/Art_P533.jpg)

 

[*7.5   Computing with MCMC Samples*](#toc.xhtml#Rh1-29)

When employing an MCMC method, each sample ***θ**[s]* is a realization of the target distribution ![art](images/Art_P534.jpg). When we are interested in performing a Bayesian estimation for parameters using a set of observations D = {*y*[1], *y*[2], ⋯ , *y*[D]}, the unnormalized target distribution is defined as the product of the likelihood and the prior,

![art](images/Art_P535.jpg)

The posterior expected values and covariance for *f*(***θ***|D) are then obtained by computing the empirical average and covariance of the samples ***θ**[s]*,

![art](images/Art_P536.jpg)

Given *f[X]*(*x*; ***θ***), a probability density function defined by the parameters ***θ***. The posterior predictive density of *X* given observations D is obtained by marginalizing the uncertainty of ***θ***,

![art](images/Art_P537.jpg)

Predictive samples *x[s]* can be generated by using samples ***θ**[s]* and evaluating them in *f[X]*(*x*; ***θ**[s]*), so

![art](images/Art_P538.jpg)

The posterior predictive expected value and variance for *X*|D ~ *f*(*x*|D) can then be estimated as

![art](images/Art_P539.jpg)

Given a function that depends on parameters ***θ*** such that *z* = *g*(***θ***), posterior predictive samples from that function can be obtained by evaluating it for randomly selected samples ***θ**[s]*,

![art](images/Art_P540.jpg)

The posterior predictive expected value and variance for the function output are thus once again

![art](images/Art_P541.jpg)

As we saw in [§6.8](#chapter005.xhtml#Sec_6.8), performing Bayesian model selection requires computing the evidence

![art](images/Art_P542.jpg)

It is theoretically possible to estimate this normalization constant from Metropolis-Hastings samples using the *harmonic mean of the likelihood*.^([7](#chapter006.xhtml#footnote_7)) This method is not presented here because it is known for its poor performance in practice.^([8](#chapter006.xhtml#footnote_8)) The *annealed importance sampling*^([9](#chapter006.xhtml#footnote_9)) (AIS) is a method combining annealing optimization methods, importance sampling, and MCMC sampling. Despite being one of the efficient methods for estimating *f*(D), we have to keep in mind that estimating the evidence is intrinsically difficult when the number of parameters is large and when the posterior is multimodal or when it displays nonlinear dependencies. Therefore, we should always be careful when estimating *f*(D) because no perfect black-box solution is currently available for estimating it.

*Example: Concrete tests*   We are revisiting the example presented in [§6.5.3](#chapter005.xhtml#Sec_6.5.3), where Bayesian estimation is employed to characterize the resistance *R* of a concrete mix. The resistance is now modeled as a Normal random variable with unknown mean and variance, ![art](images/Art_P544.jpg). The observation model is *y* = *r* + *v, v* : *V* ~ *N* (*y*; 0, 0.01²) MPa, where *V* describes the observation errors that are independent of each other, that is, *V[i]* ╨ *V[j]*, ∀*i* ≠ *j*. Our goal is to estimate the posterior PDF for the resistance’s mean *µ[R]* and standard deviation *σ[R]*,

![art](images/Art_P545.jpg)

![art](images/Art_P543.jpg)

In order to reflect an absence of prior knowledge, we employ non-informative priors (see [§6.4.1](#chapter005.xhtml#Sec_6.4.1)) for both parameters, so that *f*(*µ[R]*) ∝ 1, *f*(*σ[R]*) ∝ 1/*σ[R]*, and thus *f*(*µ[R], σ[R]*) ∝ 1/*σ[R]*. The likelihood of an observation *y*, given a set of parameters ***θ***, is ![art](images/Art_P546.jpg). Because of the conditional independence assumption for the observations, the joint likelihood for D observations is obtained from the product of the marginals,

![art](images/Art_P547.jpg)

In this example, we assume we only have three observations D = {43.3, 40.4, 44.8} MPa.

The parameter *σ[R]* ∈ (0, *∞*) = ℝ^+ is constrained to positive real numbers. Therefore, we perform the Bayesian estimation in the transformed space ***θ***^(tr),

![art](images/Art_P548.jpg)

Note that no transformation is applied for *µ[R]* because it is already defined over ℝ.

The Newton-Raphson algorithm is employed in order to identify the set of parameters maximizing the target PDF defined in the transformed space,

![art](images/Art_P549.jpg)

The optimal values found are

 
| ***θ***^∗tr || \= || \[43.0 0.6\]^(**T**) |
| --- | --- | --- |
| ***θ***^∗ || \= || \[43.0 1.8\]^(**T**). |

The Laplace approximation evaluated at ***θ***^(∗tr) is employed to estimate the posterior covariance

![art](images/Art_P550.jpg)

This estimation is employed with a scaling factor *γ*² = 2.88 in order to initialize the proposal PDF covariance. A total of C = 4 chains are generated, where each contains S = 10⁴ samples. The scaling factor obtained after tuning is *γ*² = 1.44, which leads to an acceptance rate of *β* = 0.29 and EPSR convergence metrics ![art](images/Rcap.jpg)\= \[1.0009 1.0017\].

 

The posterior mean and posterior covariance are estimated from the MCMC samples ***θ**[s]*,

![art](images/Art_P551.jpg)

The posterior predictive mean and variance for the concrete resistance, which include the epistemic uncertainty about the parameters *µ[R]* and *σ[R]*, are

![art](images/Art_P552.jpg)

where samples ![art](images/Art_P553.jpg)are generated using the MCMC samples ***θ**[s]* = \[*µ[R,s] σ[R,s]*\]^(**T**).

[Figure 7.12](#chapter006.xhtml#Fig_7-12) presents the prior, likelihood, posterior, and posterior predictive PDFs. Samples ***θ**[s]* are represented by dots on the posterior. Note how the posterior predictive does not exactly correspond with the true PDF for *R*, which has for true values ![art](images/Art_P554.jpg)and ![art](images/Art_P555.jpg). This discrepancy is attributed to the fact that only 3 observations are available, so epistemic uncertainty remains in the estimation of parameters {*µ[R], σ[R]*}. In [figure 7.12](#chapter006.xhtml#Fig_7-12), this uncertainty translates in heavier tails for the posterior predictive than for the true PDF.

![art](images/Art_P556.jpg)

Figure 7.12: Example of application of MCMC sampling for the estimation of the resistance of a concrete mix. The cross indicates the true (unknown) parameter values.

 

 

*Exercises*

 
| P7.1 || What is the Markov hypothesis, and what is its role in MCMC methods? |
| --- | --- |
| P7.2 || In the MCMC sampling context, what is the role of the burn-in phase? |
| P7.3 || With MCMC sampling, how can we quantify the convergence? |
| P7.4 || Explain what factors affect the sampling efficiency of the Metropolis algorithm. |
| P7.5 || What case is best suited to employ MCMC sampling rather than an MAP or MLE point approximation for a posterior? |
| P7.6 || With MCMC, what is the purpose of performing the sampling in a transformed space? |
| P7.7 || Use the Metropolis algorithm to sample the target function![art](images/Art_P557.jpg)Check your results with [figure 7.9](#chapter006.xhtml#Fig_7-9). |
| P7.8 || Three soil specimens are tested to estimate the parameters {*µ[x], σ[x]*} of the probability distribution function describing the friction angle ![art](images/Art_P558.jpg). Observations *y[i]* are realizations of the observation model *y* : *Y* = *X* + *V* , where *V[i]* ~ N (*v*; 0, 1²) is a random variable describing the measurement device’s uncertainty (note: *V[i]* ╨ *V[j]*, ∀*i* ≠ *j*). The set of observations available is D = {*y*[1] = 30°, *y*[2] = 35°, *y*[3] = 27°}. The prior knowledge *f*(*µ[x]*) = U(*µ[x]*; 20, 35) follows a uniform PDF, *f*(*σ[x]*) ∝ 1/*σ[x]* follows a non-informative prior, and *µ[x]* ╨ *σ[x]*.a. In the context of MCMC sampling, write down the formulation for the target distribution ![art](images/Art_P559.jpg).b. Implement your own MCMC algorithm to draw samples from the unnormalized posterior *f*(*µ[x]*, *σ[x]*|D). Use the proposal model *f*(**s**[*t*]|**s**[*t*−1]) = N(**s**[*t*]; **s**[*t*−1], diag(\[4 4\]). Report the acceptance rate and present a 2-D contour plot of your posterior overlaid with your MCMC samples.c. Compute the marginal posterior means and standard deviations ![art](images/Art_P560.jpg), ![art](images/Art_P560a.jpg).d. Using results from (b), generate samples from the posterior predictive distribution![art](images/Art_P561.jpg)and plot a histogram for these samples. |

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter006.xhtml#footnote_ref_1) Brooks, S., A. Gelman, G. Jones, and X.-L. Meng (2011). *Handbook of Markov Chain Monte Carlo*. CRC Press.

[²](#chapter006.xhtml#footnote_ref_2) Metropolis, N., A. W. Rosenbluth, M. N. Rosenbluth, A. H. Teller, and E. Teller (1953). Equation of state calculations by fast computing machines. *The Journal of Chemical Physics 21* (6), 1087–1092.

[³](#chapter006.xhtml#footnote_ref_3) Hastings, W. K. (1970). Monte Carlo sampling methods using Markov chains and their applications. *Biometrika 57* (1), 97–109.

[⁴](#chapter006.xhtml#footnote_ref_4) Murphy, K. P. (2012). *Machine learning: A probabilistic perspective*. MIT Press.

[⁵](#chapter006.xhtml#footnote_ref_5) Gelman, A. and D. B. Rubin (1992). Inference from iterative simulation using multiple sequences. *Statistical Science 7* (4), 457–472.

[⁶](#chapter006.xhtml#footnote_ref_6) Rosenthal, J. S. (2011). Optimal proposal distributions and adaptive MCMC. In *Handbook of Markov Chain Monte Carlo*, 93–112. CRC Press.

[⁷](#chapter006.xhtml#footnote_ref_7) Newton, M. A. and A. E. Raftery (1994). Approximate Bayesian inference with the weighted likelihood bootstrap. *Journal of the Royal Statistical Society. Series B (Methodological) 56*(1), 3–48.

[⁸](#chapter006.xhtml#footnote_ref_8) Neal, R. (2008). The harmonic mean of the likelihood: Worst Monte Carlo method ever. URL [https://radfordneal.wordpress.com/2008/08/17/the-harmonic-mean-of-the-likelihood-worst-monte-carlo-method-ever/](https://radfordneal.wordpress.com/2008/08/17/the-harmonic-mean-of-the-likelihood-worst-monte-carlo-method-ever/). Accessed November 8, 2019.

[⁹](#chapter006.xhtml#footnote_ref_9) Neal, R. M. (2001). Annealed importance sampling. *Statistics and Computing 11*(2), 125–139.

 

[**Part III**](#toc.xhtml#part-3)

[**Supervised Learning**](#toc.xhtml#part-3)

![art](images/Art_P561a.jpg)

 

 

[*8*](#toc.xhtml#chap-7)

[*Regression*](#toc.xhtml#chap-7)

**Data**

D = {(**x***[i], y[i]*), ∀*i* ∈ {1 : D}}

![art](images/Art_P562.jpg)

*y[i]* ∈ ℝ : Observation

**Model**

*g*(*x*) ≡ fct(*x*)

Regression consists in the task of modeling the relationships between a *system’s* responses and the covariates describing the properties of this system. Here, the generic term *system* is employed because regression can be applied to many types of problems. [Figure 8.1](#chapter007.xhtml#Fig_8-1) presents examples of applications in the field of civil engineering; for instance, one could model the relationship between (a) the number of pathogens and chlorine concentration, (b) the number of accidents at a road intersection as a function of the hour of the day, and (c) concrete strength as a function of the water-cement ratio. These examples are all functions of a single covariate; later in this chapter we will see how regression is generalized to model the responses of a system as a function of any number of covariates.

![art](images/Art_P564.jpg)

Figure 8.1: Examples of applications of regression analysis in the context of civil engineering.

In regression problems, the data sets are described by D pairs of observations D = {(**x***[i], y[i]*), ∀*i* ∈ {1 : D}} where ![art](images/Art_P563.jpg)are *covariates*, also called *attributes* or *regressors*, and *y[i]* ∈ ℝ¹ is an observed system response. A regression model *g*(**x**) ≡ fct(**x**) ∈ ℝ¹ is thus a X → 1 function, that is, a function of X covariates leading to one output. This chapter covers three regression methods for building *g*(**x**): *linear regression*, *Gaussian process regression*, and *neural networks*.

 

[*8.1   Linear Regression*](#toc.xhtml#Rh1-30)

*Linear regression* is one of the easiest methods for approaching regression problems. Contrarily to what its name may lead us to think, linear regression is not limited to cases where the relationships between the covariates and system responses are linear. The term *linear* refers to the linear dependence of the model with respect to its parameters. In the case involving a single covariate *x*, the model employed in linear regression takes the form

*g*(*x*) = *b*[0] + *b*[1]*ϕ*[1](*x*) + *b*[2]*ϕ*[2](*x*) + … + *b*[B]*ϕ*[B](*x*),

where ***θ*** = **b** = \[*b*[0]*b*[1] ⋯ *b*[B]\]^(**T**) is a vector of model parameters and *ϕ[i]*(*x*) is a *basis function* applied on the covariate *x*. Basis functions are nonlinear functions employed when we want to apply linear regression to describe nonlinear relationships. [Figure 8.2](#chapter007.xhtml#Fig_8-2) presents two examples of linear regression applied to (a) linear and (b) nonlinear relationships.

![art](images/Art_P565.jpg)

Figure 8.2: Examples of linear regression applied to linear and nonlinear relationships.

 

[*8.1.1   Mathematical Formulation*](#toc.xhtml#Rh2-39)

For the simplest case where there is only one covariate, the data set consists in D pairs of covariates and system responses D = {(*x[i], y[i]*), ∀*i* ∈ {1 : D}}, where a covariate *x[i]* ∈ ℝ, and its associated observation *y[i]* ∈ ℝ. The observation model is defined as

![art](images/Art_P566.jpg)

where *v* describes the observation errors that are assumed to be independent of each other, *V[i]* ╨ *V[j]*, ∀*i* ≠ *j*. Note that observed covariates *x* are assumed to be exact and free from any observation errors. Let us consider the special case of a linear basis function *ϕ*(*x*) = *x* where the model takes the form

![art](images/Art_P567.jpg)

**Note:** The 1 in ![art](images/Art_P568.jpg)stands for the absence of dependence on a covariate for the bias parameter *b*[0].

We can express the model for the entire data set using the following matrix notation,

![art](images/Art_P569.jpg)

With this matrix notation, we reformulate the observation model as

![art](images/Art_P570.jpg)

where **I** is the identity matrix indicating that all measurement errors are independent from each other and have the same variance. If we separate the set of observations D = {D[*x*], D[*y*]} by isolating covariates D*[x]* and system responses D*[y]*, the joint likelihood of observed system responses given the set of observed covariates and model parameters ***θ*** = **b** is expressed as

![art](images/Art_P571.jpg)

The goal is to estimate optimal parameters ***θ***^∗ = **b**^∗, which maximize the likelihood *f*(D[*y*]|D[*x*], ***θ***), or equivalently, which maximize the log-likelihood,

![art](images/Art_P572.jpg)

**Note:** Because we have assumed that *σ[V]* is the same for all observations, optimal parameters values ***θ***^∗ are independent of the observation-error standard deviation.

The set of data D employed to obtain the maximum likelihood estimate (MLE) for parameters ***θ*** = **b** is called the *training set*. In the context of linear regression, the objective of maximizing ln *f*(D[*y*]|D[*x*], ***θ***) is often replaced by the equivalent objective of *minimizing* a *loss function J*(**b**) corresponding to the sum of the squares of the prediction errors,

![art](images/Art_P574.jpg)

**Note:**

![art](images/Art_P575.jpg)

[Figure 8.3](#chapter007.xhtml#Fig_8-3) presents a loss function *J*(*b*) as a function of the model parameters *b*. Optimal parameter values ***θ***^∗ = **b**^∗ are defined as

![art](images/Art_P577.jpg)

![art](images/Art_P576.jpg)

Figure 8.3: The minimum of a continuous function corresponds to the location where its derivative equals zero.

As for other continuous functions, the minimum of *J*(**b**^∗) coincides with the point where its derivative equals zero,

![art](images/Art_P578.jpg)

By reorganizing the terms from the last equation, optimal parameters are defined as

![art](images/Art_P579.jpg)

 

[Figure 8.4](#chapter007.xhtml#Fig_8-4) presents an example of linear regression employing a linear basis function

*g*(*x*) = *b*[0] + *b*[1]*x*.

![art](images/Art_P580.jpg)

Figure 8.4: Example of linear regression minimizing the performance metric *J* computed on the training set.

The optimal parameters found using the training set are **b**^∗ = \[1.14 3.71\]^(**T**), for which *J[train]*(**b**^∗) = 1.98.

We can extend the formulation presented above for the general case where the relationship between *x* and *y* is modeled by the summation of multiple basis functions,

*g*(*x*) = *b*[0] + *b*[1]*ϕ*[1](*x*) + *b*[2]*ϕ*[2](*x*) + ⋯ + *b*[B]*ϕ*[B](*x*) = **Xb**,

where *ϕ[i]*(*x*) can be any linear or nonlinear function, for example: *ϕ[i]*(*x*) = *x*², *ϕ[i]*(*x*) = sin(*x*), ⋯. In a matrix form, this general model is expressed as

![art](images/Art_P581.jpg)

Remember that with linear regression, the model is necessarily linear with respect to *ϕ[i]*(*x*) and **b**, yet not *x*. [Figure 8.5](#chapter007.xhtml#Fig_8-5) presents two examples of linear regression applied to nonlinear relationships between a system response and a covariate.

![art](images/Art_P582.jpg)

Figure 8.5: Examples of linear regression applied to nonlinear relationships.

 

[*8.1.2   Overfitting and Cross-Validation*](#toc.xhtml#Rh2-40)

One of the main challenges with linear regression, as with many other machine learning methods, is *overfitting*. Overfitting happens when you select a model class or model structure that represents the data in your training set well, yet it fails to provide good predictions for other covariates that were not seen during training. A highly complex model capable of adapting to the training data is said to have a large *capacity*.

Overfitting with a model that has too much capacity corresponds to the case (c) in [figure 8.6](#chapter007.xhtml#Fig_8-6), where prediction errors are displaying a low bias when evaluated with the data employed to train the model; however, when validated with the true objective of predicting unobserved data, there is a high variance. Case (b) represents the situation where a model underfits the data because its low capacity causes a large bias and a small variance. As depicted in (e), we want the optimal *model complexity* offering a tradeoff between the prediction bias and variance by minimizing the validation error. This is known as the *bias-variance tradeoff*. The concept illustrated in [figure 8.6](#chapter007.xhtml#Fig_8-6) will be revisited at the end of this section.

![art](images/Art_P583.jpg)

Figure 8.6: Illustration of the *bias* and *variance* when talking about predictive performance and model complexity.

 

In the context of the linear regression, overfitting arises when one chooses basis functions *ϕ*(*x*) that have too much capacity and that will be able to fit the data in a training set but not the data of an independent validation set. [Figure 8.7a](#chapter007.xhtml#Fig_8-7) presents an example where data is generated from a linear basis function and where the regression model also employs a linear basis function to fit the data. [Figure 8.7b](#chapter007.xhtml#Fig_8-7) presents the case where the same data is fitted with a model using polynomial basis functions of order 5. Notice how when more complex basis functions are introduced in the model, it becomes more flexible, and it can better fit the data in the training set. Here the fitting ability is quantified by the loss function *J* that is lower for the polynomial model than for the linear one.

![art](images/Art_P584.jpg)

Figure 8.7: Example of (a) a model with correct complexity, and (b) a model with too much capacity.

One solution to this challenge is to replace the MLE procedure for optimizing the parameters b (see equation 8.2) with the Bayesian estimation procedure as described in [§6.3](#chapter005.xhtml#Sec_6.3). The appropriate model complexity should then be selected by employing Bayesian model selection as presented in [§6.8](#chapter005.xhtml#Sec_6.8). In practice, this is seldom performed because calculating the evidence *f*(D|*m[i]*) for a model is computationally demanding. An alternative is to perform *ridge regression*,^([1](#chapter007.xhtml#footnote_1)) which is a special case of Bayesian linear regression that employs *regularization* to constrain the parameters (see [§8.3.3](#chapter007.xhtml#Sec_8.3.3)).

Another general procedure to identify the optimal model complexity is to employ *cross-validation*. The idea is to avoid employing the same data to (1) estimate optimal parameters, (2) discriminate between model classes, and (3) test the final model performance using the loss function. To start with, the data is separated into a training set and a test set. In order to maximize the utilization of the data available, we can rely on the *N-fold cross-validation* procedure, where the training set is again divided into N subsets called *folds*; one at a time, each subset is employed as an independent validation set while the training is performed on the remaining folds. The total loss is obtained by summing the loss obtained for each validation subset. The model class selected is the one with the lowest aggregated loss. Once a model class is selected as the best one, its parameters can be retrained using the entire training set, and its predictive performance is evaluated on the independent test set that was not employed to estimate parameters or to discriminate between model classes.

[Figure 8.8](#chapter007.xhtml#Fig_8-8) presents an example of a 3-fold cross-validation where the green-shaded boxes describe the part of the data set employed to train the model, the blue boxes describe the part of the data set employed to compare the predictive performance while choosing between model classes, and the red box represents the independent test set that is only employed to quantify the model performance on unobserved data. It is essential that for each fold, the training and validation sets, and the test set are kept separated. Typically, we would employ 80 percent of the data for the training and validation sets and 20 percent for the test set.

![art](images/Art_P585.jpg)

Figure 8.8: The *N*\-fold cross-validation procedure.

 

It is common to employ 10-fold cross-validation because it offers a balance between the computational effort required and the amount of data available to estimate the model parameters. For N folds, the model needs to be trained N times, which may involve a substantial computational effort. On the other hand, using few folds may lead to poor parameter estimates. For example, if we only employ 2 folds, for each of them the model is only trained on half the training set. When N = D[*train*], the procedure is called *leave-one-out cross-validation* (LOOCV). This approach leads to the best estimation of validation errors because more data is employed during training, yet it is the most computationally demanding. [Algorithm 7](#chapter007.xhtml#Tab_7) summarizes the *N*\-fold cross-validation procedure for choosing between M model classes.

**Algorithm 7:** *N*\-fold cross-validation

![art](images/Art_P586.jpg)

 

[Figures 8.9](#chapter007.xhtml#Fig_8-9) and [8.10](#chapter007.xhtml#Fig_8-10) present a 2-fold cross-validation procedure employed to choose between a linear model *g*[1](*x*) and a fifth-order polynomial one *g*[2](*x*),

![art](images/Art_P587.jpg)

Figure 8.9: Example of 2-fold cross-validation for the model *g*[1](*x*) = *b*[0] + *b*[1]*x*.

| *g*[1](*x*) = *b*[0] + *b*[1]*x* || (linear) |
| --- | --- |
| *g*[2](*x*) = *b*[0] + *b*[1]*x* + *b*[2]*x*² + *b*[3]*x*³ + *b*[4]*x*⁴ + *b*[5]*x*⁵ || (5^(th) order). |

For the linear model, the sum of the losses for the two training and validation sets is

![art](images/Art_P589.jpg)

and for the fifth-order polynomial model, the sum of the losses for the two training and validation sets is

![art](images/Art_P590.jpg)

These results indicate that the fifth-order polynomial function is better at fitting the training set; however, it fails at predicting data that was not seen in the training set. This is reflected in the loss function for the validation set, which is lower for the linear model having the correct complexity, compared to the fifth-order polynomial function that is overcomplex.

We now come back to the targets presented in [figure 8.6](#chapter007.xhtml#Fig_8-6); the model *g*[1](*x*) presented in [figure 8.9](#chapter007.xhtml#Fig_8-9) corresponds to the target in [figure 8.6a](#chapter007.xhtml#Fig_8-6), where the complexity is optimal so there is both a low bias and a low variance. The model *g*[2](*x*) presented in [figure 8.10](#chapter007.xhtml#Fig_8-10) corresponds to [figure 8.6c](#chapter007.xhtml#Fig_8-6), where because the capacity is too high, the model closely fits the training data in each fold (low bias), yet the model is drastically different (i.e., high variance) for each fold. Here, the high model capacity allowed to overfit the noise contained in the data. Finally, the target in [figure 8.6b](#chapter007.xhtml#Fig_8-6) corresponds to the new case illustrated in [figure 8.11](#chapter007.xhtml#Fig_8-11), where the model does not have enough capacity to fit the data. The result is that the model is highly biased, yet there is almost no variability between the models obtained for each fold.

![art](images/Art_P588.jpg)

Figure 8.10: Example of 2-fold cross-validation for the model *g*[2](*x*) = *b*[0] + *b*[1]*x* + *b*[2]*x*² + *b*[3]*x*³ + *b*[4]*x*⁴ + *b*[5]*x*⁵.

![art](images/Art_P592.jpg)

Figure 8.11: Example of 2-fold cross-validation for the model *g*[3](*x*) = *b*[0] + *b*[1]*x*, where the data follows the real model ![art](images/Art_P593.jpg).

 

[*8.1.3   Mathematical Formulation >1-D*](#toc.xhtml#Rh2-41)

Linear regression can be employed for cases involving more than one covariate. The data set is then D = {(**x***[i], y[i]*), ∀*i* ∈ {1 : D}}, where ![art](images/Art_P591.jpg)is an X by one vector associated with an observation *y[i]* ∈ ℝ¹. The model is an X → 1 function, *g*(**x**) ≡ fct(**x**) ∈ ℝ¹, which is defined using basis functions so that

*g*(**x**) = *b*[0] + *b*[1]*ϕ*[1](*x*[1]) + *b*[2]*ϕ*[2](*x*[2]) + ⋯ + *b*[B]*ϕ*[B](*x*[X]) = **Xb**.

 

The matrix notation for the model defined over the entire data set is

![art](images/Art_P594.jpg)

where \[**x***[i]*\]*[j]* ≡ *x[i,j]* refers to the *j*^(th) component of the x vector for the *i*^(th) observation. [Figure 8.12](#chapter007.xhtml#Fig_8-12) presents an example of multivariate linear regression for **x** = \[*x*[1]*x*[2]\]^(**T**) and for which the model is

![art](images/Art_P596.jpg)

![art](images/Art_P595.jpg)

Figure 8.12: Example of application of linear regression to a 2-D data set.

Note that even if the model now involves multiple covariates, the optimal model parameters **b**^∗ are still estimated using equation 8.2.

 

[*8.1.4   Limitations*](#toc.xhtml#Rh2-42)

Some of the limitations of the linear regression method presented in [§8.1.1](#chapter007.xhtml#Sec_8.1.1) are illustrated in [figure 8.13](#chapter007.xhtml#Fig_8-13): (a) it assumes *homoscedastic* errors and is thus not suited for the cases where the variance of errors depends on the covariate *x*, that is, *heteroscedastic* cases, (b) it is sensitive to *outliers*, so a single biased observation may severely affect the model, and (c) it does not differentiate between *interpolation* and *extrapolation*. Interpolation refers to predictions made between covariates for which observations are available to train the model, and extrapolation refers to predictions made beyond the domain the model has been trained for. In (c), the predictions performed with *g*(*x*) are good at interpolating between data points in the training set, yet they offer a poor performance for extrapolating beyond them on the test data. A main limitation with the linear regression formulation presented here is that it does not provide uncertainty estimates indicating that its predictive performance degrades for covariate values that are far from those available in the training set.

![art](images/Art_P597.jpg)

Figure 8.13: Illustrations of some of the limitations of the linear regression method presented in [§ 8.1.1](#chapter007.xhtml#Sec_8.1.1).

Another key limitation not illustrated in [figure 8.13](#chapter007.xhtml#Fig_8-13) is that the performance of linear regression depends on our ability to handpick the correct basis functions. For cases involving one or two covariates, this task is feasible from a simple visual representation of the data set. This task becomes difficult when the number of covariates X > 2. In short, linear regression is simple and parameter estimation is quick, yet it is outperformed by modern techniques such as *Gaussian process regression* and *neural networks*, which will be covered in the next sections. Note that the cross-validation technique covered here is not limited to linear regression and can be employed with a wide range of machine learning methods.

 

[*8.2   Gaussian Process Regression*](#toc.xhtml#Rh1-31)

**Note:** As for linear regression (see [§ 8.1](#chapter007.xhtml#Sec_8.1)), covariates *x* are assumed to be deterministic constants that are free from observation errors.

Gaussian process regression (GPR) works by describing the prior knowledge of system responses over its covariate domain using a joint multivariate Normal probability density function (PDF). Then, it employs the properties of the multivariate Normal (see [§4.1.3](#chapter003.xhtml#Sec_4.1.3)) in order to update the joint prior PDF using empirical observations.

*Pipeline example*   Take for example the 100 km long pipeline illustrated in [figure 8.14](#chapter007.xhtml#Fig_8-14), for which we are interested in quantifying the temperature at any coordinate *x* ∈ (0, 100) km. Given that we know the pipeline temperature to be *y* = 8°*C* at *x* = 30 km, *what is the temperature at x* = 30.1 *km?* Because of the proximity between the two locations, it is intuitive that the temperature has to be close to 8°*C*. Then, *what is the temperature at x* = 70 *km?* We cannot say for sure that it is going to be around 8°*C* because over a 40 km distance, the change in temperature can reach a few degrees. This example illustrates how we can take advantage of the underlying dependencies between system responses for different observed covariates *x*, for predicting the responses for unobserved covariates.

![art](images/Art_P598.jpg)

Figure 8.14: Example of a 100 km long pipeline.

Let us consider system responses defined by a single covariate *x[i]* so that

![art](images/Art_P599.jpg)

The data set is defined as D = {(*x[i], g[i]*), ∀*i* ∈ {1 : D}} = {D*[x]*, D*[g]*}, where for D observations,

D*[g]* = {**g**} = {\[*g*[1]*g*[2] ⋯ *g*[D]\]^(**T**)}, and D*[x]* = {**x**} = {\[*x*[1]*x*[2] ⋯ *x*[D]\]^(**T**)},

so for each observed *g[i]*, there is an associated covariate *x[i]*. A *Gaussian process* is a multivariate Normal random variable defined over a domain described by covariates. In the case of Gaussian process regression, a set of system responses is assumed to be a realization from a Gaussian process *g*(**x**) : **G**(**x**) ~ N (*g*(**x**); ***µ*[G]**, Σ[**G**]), where ***µ*[G]** is the mean vector \[***µ*[G]**\]*[i]* = *µ*[**G**](*x[i]*) and the covariance matrix Σ[**G**] is

\[Σ[**G**]\]*[ij]* = *ρ*(*x[i], x[j]*) *· σ[G]*(*x[i]*) · σ[G](*x[j]*), *ρ*(*x[i], x[j]*) = fct(*x[i] − x[j]*).

Σ[**G**] defines the covariance between a discrete set of Gaussian random variables for which the pairwise correlation *ρ*(*x[i], x[j]*) between *G*(*x[i]*) and *G*(*x[j]*) is a function of the distance between the covariates *x[i]* and *x[j]*. Note that ***µ*[G]** and **Σ[G]** depend implicitly on the covariates **x**.

*Pipeline example (continued)*   [Figure 8.15](#chapter007.xhtml#Fig_8-15) illustrates our prior knowledge of the temperature for coordinates **x** = \[0 1 ⋯ 100\]^(**T**) km,

![art](images/Art_P602.jpg)

![art](images/Art_P600.jpg)

Figure 8.15: Representation of the prior knowledge for the temperature along a pipeline. The dashed horizontal red line represents the prior mean, and the pink-shaded area is the ±2*σ[G]* confidence region. Overlaid colored curves represent five realizations of the Gaussian process, **g***[i]* : **G** ~ N (*g*(**x**); *µ*[**G**], Σ[**G**]).

where each colored curve represents a different realization of the Gaussian process **G**. The prior means and standard deviations are assumed to be equal for all locations *x*, so *µ[G]*(*x*) = *µ[G]* = 0°*C* and *σ[G]*(*x[i]*) = *σ[G]* = 2.5*°C*. The correlation between the temperature at two locations *G*(*x[i]*) and *G*(*x[j]*) is defined here by a *square exponential* correlation function

![art](images/Art_P603.jpg)

where *ℓ* is the *length-scale* parameter. [Figure 8.16](#chapter007.xhtml#Fig_8-16) presents the square-exponential correlation function plotted for parameter values *ℓ* = {1, 2, 5}.

![art](images/Art_P601.jpg)

Figure 8.16: Square-exponential correlation function.

In [figure 8.15](#chapter007.xhtml#Fig_8-15), for a length-scale of *ℓ* = 25 km, the correlation for the three pairs of coordinates *x* = {30, 31, 70} is

![art](images/Art_P604.jpg)

[Figure 8.17](#chapter007.xhtml#Fig_8-17) presents examples of realizations for the same Gaussian process using different length-scale parameters.

![art](images/Art_P605.jpg)

Figure 8.17: Examples of Gaussian process realizations for different length-scale parameter values. The dashed horizontal red line represents the prior mean, and the pink-shaded area is the ±2*σ[G]* confidence region.

 

[*8.2.1   Updating a GP Using Exact Observations*](#toc.xhtml#Rh2-43)

**Nomenclature**

**x** = \[*x*[1]*x*[2] ⋯ *x*[D]\]^(**T**): Covariates for D observed locations

**x**[∗] = \[*x*[∗1]*x*[∗2] ⋯ *x*[∗P]\]^(**T**): Covariates for P prediction locations

**g** = \[*g*[1]*g*[2] ⋯ *g*[D]\]^(**T**): System responses for D observed locations

**g**[∗] = \[*g*[∗1]*g*[∗2] ⋯ *g*[∗P]\]^(**T**): Model predictions for P locations

Σ[**G**]: Prior covariance of **G** for observed locations **x**

Σ[∗]: Prior covariance of **G**[∗] for prediction locations **x**[∗]

Σ[**G**∗]: Prior covariance of **G** between observed and prediction locations, **x** and **x**[∗], respectively

Let us consider D = {(*x[i], g[i]*), *i* ∈ {1 : D}}, a set of D exact observations (i.e., without observation errors), and **x**[∗] = \[*x*[∗1]*x*[∗2] ⋯ *x*[∗P]\]^(**T**), a vector of P covariates corresponding to either observed or unobserved locations where we want to obtain predictions. The goal is to obtain the posterior PDF *f*(**g**[∗]|**x**[∗], D). Before obtaining this posterior PDF, we have to define the joint prior knowledge for the system responses at both the observed **x** and prediction **x**[∗] locations,

![art](images/Art_P606.jpg)

where ***µ*[G]** and ***µ***[∗] are, respectively, the prior means at observed and at prediction locations; ![art](images/Art_P607.jpg)and ![art](images/Art_P608.jpg)are their respective covariances. The covariance between observed and prediction locations is described by ![art](images/Art_P609.jpg). The posterior probability of **G**[∗] at prediction locations **x**[∗], conditioned on the observations D, is given by *f*[**G**∗|**x**∗,D](**g**[∗]|**x**[∗], D) = N (**g**[∗]; ***µ***[∗|D], Σ[∗|D]), where the posterior mean vector and covariance matrix are

![art](images/Art_P610.jpg)

These two equations are analogous to those presented [§4.1.3](#chapter003.xhtml#Sec_4.1.3) for the conditional distribution of a multivariate Normal (≡ Gaussian).

*Strength and limitations*   One of the main differences between the Gaussian process regression and other regression methods that encode the relationships contained in the data set through a parametric model is that GPR is a *nonparametric approach*, for which predictions depend explicitly on the observations available in the data set. The upside, in comparison with other methods such as linear regression, is that there is no requirement to define basis functions that are compatible with the system responses. GPR thus allows modeling highly nonlinear responses using few parameters. Another key feature of GPR is that it is an intrinsically probabilistic method that allows differentiating between the prediction quality in interpolation and extrapolation situations. For example, [figures 8.19c](#chapter007.xhtml#Fig_8-19) and [8.19d](#chapter007.xhtml#Fig_8-19) show how interpolating between observation leads to a narrower confidence region than when extrapolating.

One of the main downsides of Gaussian process regression is that when the data set is large (D > 1000), building the matrices describing the joint prior knowledge becomes computationally demanding and it is then necessary to employ approximate methods.^([2](#chapter007.xhtml#footnote_2))

 

*Pipeline example (continued)*   We consider the case where the pipeline temperature *g*[2] = −2°*C* is observed for the covariate *x*[2] and we want to use this information to obtain the posterior PDF describing the temperature *G*[1] at a location *x*[1]. Given *µ[G]* = 0°*C*, *σ[G]* = 2.5°*C*, and *ρ*(*x*[1], *x*[2]) = 0.8, the joint PDF describing the prior probability of the temperature at locations *x*[1] and *x*[2] is defined by

![art](images/Art_P612.jpg)

The conditional probability of *G*[1] given the observation *g*[2] is

![art](images/Art_P613.jpg)

where the posterior mean and standard deviation are

![art](images/Art_P614.jpg)

Again, these last two equations are analogous to those presented in [§4.1.3](#chapter003.xhtml#Sec_4.1.3). The joint prior and posterior PDFs are presented in [figure 8.18](#chapter007.xhtml#Fig_8-18). [Figure 8.19](#chapter007.xhtml#Fig_8-19) presents the generalization of this update process for P = 101 predicted locations **x**[∗] = \[0 1 ⋯ 100\]^(**T**) km and using, respectively, D = {0, 1, 2, 3} observations. Note how the uncertainty reduces to zero at locations where observations are available. Realizations of the updated Gaussian process are then required to pass by all observed values. The correlation embedded in the joint prior knowledge allows sharing the information carried by observations for predicting the system responses at adjacent unobserved covariate values.

![art](images/Art_P611.jpg)

Figure 8.18: Joint Gaussian prior knowledge of the temperature at two locations and conditional PDF for the temperature *g*[1], given the observation *g*[2] = −2.

![art](images/Art_P615.jpg)

Figure 8.19: Examples of how the Gaussian process describing the pipeline temperature evolves as it is updated with different data sets D.

 

[*8.2.2   Updating a GP Using Imperfect Observations*](#toc.xhtml#Rh2-44)

We now explore how to extend the formulation presented in the previous section to the case where observations are contaminated by noise. The observation model is now defined as

![art](images/Art_P616.jpg)

where ![art](images/Art_P617.jpg)describes zero-mean independent observation errors so that *V[i]* ╨ *V[j]* ∀*i* ≠ *j*. Because *g*(*x*) : **G**(*x*) is now indirectly observed through *y*, we have to redefine our prior knowledge between the observations **Y** and the model responses **G**[∗] at prediction locations. The joint prior knowledge is described by

![art](images/Art_P618.jpg)

In the case where the observation noise has a mean equal to zero, the mean vector for observations equals the prior mean for the system responses, ***µ*[Y]** = ***µ*[G]**. The global covariance matrix is then defined using

![art](images/Art_P619.jpg)

Given the prediction locations **x**[∗] and the observations D, the posterior knowledge for the system responses **G**[∗] is

*f*[**G***∗*|**x***∗,D*](**g**[∗]|**x**[∗], D) = N (**g**[∗]; ***µ***[∗|D], Σ*[∗|D]*),

where the posterior mean vector ***µ***[∗|D] and covariance matrix Σ[∗|D] are

![art](images/Art_P620.jpg)

*Pipeline example (continued)*   We continue our study of the pipeline example by considering noisy observations characterized by a measurement error standard deviation *σ[V]* = 1 °C. [Figure 8.20](#chapter007.xhtml#Fig_8-20) presents the updated Gaussian process for P = 101 prediction locations **x**[∗] = \[0 1 ⋯ 100\]^(**T**) km, and using, respectively, D = {0, 1, 2, 3} noisy observations. Notice how, contrarily to results presented in [figure 8.19](#chapter007.xhtml#Fig_8-19), uncertainty now remains in the posterior at observed locations. The larger *σ[V]* is, the less information observations carry and the less they modify the prior knowledge.

![art](images/Art_P621.jpg)

Figure 8.20: Examples of how the Gaussian process describing the pipeline temperature evolves as it is updated with different data sets D, with an observation standard deviation *σ[V]* = 1 °C.

 

[*8.2.3   Multiple Covariates*](#toc.xhtml#Rh2-45)

![art](images/Art_P622.jpg)

In the case where the regression is performed for multiple covariates **x** = \[*x*[1]*x*[2] ⋯ *x*[**X**]\]^(**T**), it is necessary to define a joint correlation function defining the correlation coefficient associated with a pair of covariate vectors. Typically, the joint correlation function is obtained from the product of a marginal correlation function *ρ*(\[**x***[i]*\]*[k],* \[**x***[j]*\]*[k]*) for each covariate,

![art](images/Art_P623.jpg)

The multivariate formulation for the *square-exponential* correlation function is

![art](images/Art_P624.jpg)

where there is one parameter *ℓ[k]* for each covariate. [Figure 8.21](#chapter007.xhtml#Fig_8-21) presents an example of a bivariate square-exponential correlation function. One relevant feature with this correlation function is that the length-scales *ℓ[k]* are directly measuring the importance of each covariate for predicting the system responses. As a simple heuristic, we can say that if *ℓ[k]* is greater than two times the empirical standard deviations of the observed covariates ![art](images/Art_P626.jpg), then the *k*^(th) covariate has a limited influence on the system response predictions. The reason is because the correlation coefficient remains close to one for any pairs of this *k*^(th) covariate. In the opposite case, where *ℓ[k]* is smaller than the empirical standard deviation ![art](images/Art_P627.jpg), we can conclude that the *k*^(th) covariate has a strong influence on the system response predictions.

![art](images/Art_P625.jpg)

Figure 8.21: Bivariate square-exponential correlation function with parameters *ℓ*[1] = 1 and *ℓ*[2] = 1.5.

 

[*8.2.4   Parameter Estimation*](#toc.xhtml#Rh2-46)

Up to now, we have assumed that we knew the parameters such as the observation standard deviation *σ[V]* , the Gaussian process prior standard deviation *σ[G]*, and the length-scales *ℓ* = \[*ℓ*[1]*ℓ*[2] ⋯ *ℓ*[X]\]^(**T**). In practice, we need to learn these *parameters* ***θ*** = \[*σ[V] σ[G] ℓ*^(**T**)\]^(**T**) from the training data D = {D*[x]*, D*[y]*} = {(**x***[i]*, *y[i]*), *i* ∈ {1 : D}}. Following Bayes rule, the posterior PDF for parameters given data is

![art](images/Art_P628.jpg)

***θ*** = \[*σ[V] σ[G] ℓ*^(**T**)\]^(**T**) can be referred to as *hyperparameters* because they are parameters of the prior.

Often, evaluating *f*(***θ***|D*[x]*, D*[y]*) is computationally expensive, so a maximum likelihood estimation approach (see [§6.7](#chapter005.xhtml#Sec_6.7)) is typically employed. The optimal parameter values ***θ***^∗ are then

![art](images/Art_P629.jpg)

 

The *likelihood* function *f*(D*[y]*|D*[x], **θ***) describes the joint prior probability density of observations D*[y]*, given a set of parameters ***θ***,

![art](images/Art_P630.jpg)

Theoretically, here, we should refer to *f*(D*[y]*|D*[x], **θ***) as the *marginal likelihood* because the hidden variables **g** are marginalized.

The log-likelihood for a vector of observations **y** = \[*y*[1]*y*[2] ⋯ *y*[D]\]^(**T**) is given by

![art](images/Art_P631.jpg)

The optimal parameters ***θ***^∗ correspond to the parameter values for which the derivative of the likelihood equals zero, as illustrated in [figure 8.22](#chapter007.xhtml#Fig_8-22). For ***µ*[Y]** = **0**, the derivative of the log-likelihood is

![art](images/Art_P633.jpg)

![art](images/Art_P632.jpg)

Figure 8.22: Log-likelihood maximization.

Efficient gradient-based optimization algorithms for learning parameters by maximizing the log-likelihood are already implemented open-source packages such as the GPML^([3](#chapter007.xhtml#footnote_3)), GPStuff^([4](#chapter007.xhtml#footnote_4)), and pyGPs^([5](#chapter007.xhtml#footnote_5)) toolboxes.

 

[*8.2.5   Example: Soil Contamination Characterization*](#toc.xhtml#Rh2-47)

**Covariate importance metric**

![art](images/Art_P639.jpg)

This section presents an applied example of GPR for the characterization of contaminant concentration in soils. Take, for example, a set of observations **y***[i]* of soil contaminant concentrations,

D = {D*[x]*, D*[y]*} = {(**l***[i]*, *y[i]*), *i* ∈ {1 : 116}},

where **l***[i]* is a covariate vector associated with each concentration observation. These covariates denote the geographic coordinates (longitude, latitude, and depth) of each observation,

![art](images/Art_P634.jpg)

Each observation is represented in [figure 8.23](#chapter007.xhtml#Fig_8-23) by a circle where its size is proportional to the contaminant concentration. The goal is to employ Gaussian process regression in order to model the contaminant concentration across the whole soil volume, given the available observations for 116 discrete locations.

![art](images/Art_P636.jpg)

Figure 8.23: Example of application of GPR for soil contamination characterization. The iso-contours correspond to Pr(\[ \] > 55 mg/kg) = 0.5, and the size of each circle is proportional to the observed contaminant concentration.

(Adapted from Quach et al. (2017).)

Because a concentration must be a positive number, and because several of the observations available are close to zero, the observation model is defined in the log-space,

![art](images/Art_P635.jpg)

 

where *g*(**l**) models the natural logarithm of the true contaminant concentration. When transformed back to the original space using the exponential function, the model predictions are restricted to positive values. The observation errors are assumed to be described by the zero-mean independent Normal random variable ![art](images/Art_P637.jpg), *V[i]* ╨ *V[j]*, ∀*i* ≠ *j*. The correlation between covariates is modeled using a square-exponential correlation function, and the prior mean at any location is assumed to be equal to one in the original space, which corresponds to zero in the log-transformed space.

The parameters to be estimated from the data are the length-scale along each direction, the Gaussian process standard deviation, and the observation noise standard deviation,

***θ*** = {*ℓ[x], ℓ[y], ℓ[z], σ[G], σ[V]*}.

The maximum likelihood estimate (MLE) parameter values are

![art](images/Art_P638.jpg)

The optimal values for the length-scales {*ℓ[x], ℓ[y], ℓ[z]*} are all smaller than the range of each covariate, as depicted in [figure 8.23](#chapter007.xhtml#Fig_8-23). This confirms that all three coordinates have an influence on the contaminant concentration. [Figure 8.23](#chapter007.xhtml#Fig_8-23) presents the iso-contours describing Pr(\[ \] > 55 mg/kg) = 0.5, where l*^∗* are the covariates describing the *x, y, z* geographic coordinate of a 3-D grid covering the entire soil volume for the site studied. Further details about this example are presented in the paper from Quach et al.^([6](#chapter007.xhtml#footnote_6))

 

[*8.2.6   Example: Metamodel*](#toc.xhtml#Rh2-48)

In civil engineering, it is common to employ computationally demanding models such as the finite element models presented in [figure 8.24](#chapter007.xhtml#Fig_8-24). When performing probabilistic studies related to structural or system reliability, it is often required to have millions of model realizations for different parameter values. In such a case, for the purpose of computational efficiency, it may be interesting to replace the finite element model with a regression model built from a set of simulated responses. Such a model of a model is called a *metamodel* or a *surrogate model*. Because observations are the output of a simulation, the observation model does not include any observation error and follows the formulation presented in [§8.2.1](#chapter007.xhtml#Sec_8.2.1).

![art](images/Art_P640.jpg)

Figure 8.24: Examples of finite element structural models.

 

In this example, we built a metamodel for the Tamar Bridge finite element model.^([7](#chapter007.xhtml#footnote_7)) [Figure 8.25a](#chapter007.xhtml#Fig_8-25) presents an overview of the bridge finite element model, and [figure 8.25b](#chapter007.xhtml#Fig_8-25) presents the modal displacement associated with its first natural frequency, which is the response modeled in this example. A set of D = 1000 model simulations is obtained by evaluating the finite element model for several sets of parameters that are generated from the prior *f*(***θ***). There are five model parameters that are treated as covariates of the GP regression model, ![art](images/Art_P641.jpg): the *stiffness* of the three expansion joints located on the bridge deck, along with the *initial strain* in the cables on the main and side spans. The locations of elements affected by these parameters are illustrated in [figure 8.26](#chapter007.xhtml#Fig_8-26). This problem employs the square-exponential correlation function, so there is a total of six parameters to be learned,

***θ*** = {*ℓ*[1], *ℓ*[2], *ℓ*[3], *ℓ*[4], *ℓ*[5], *σ[G]*}.

![art](images/Art_P642.jpg)

Figure 8.25: Tamar Bridge finite element model.

![art](images/Art_P643.jpg)

Figure 8.26: Tamar Bridge model parameter description.

[Figure 8.27](#chapter007.xhtml#Fig_8-27) compares the GPR model predictions with the true finite element model outputs *g[i]*. Note that in order to obtain a meaningful comparison between predicted and measured values, it is essential to test the model iteratively using a cross-validation procedure, where at each step, the observation corresponding to the prediction location in the validation set is removed from the training set.

![art](images/Art_P644.jpg)

Figure 8.27: Comparison of the GPR model predictions with the finite-element model predictions using the leave-one-out cross-validation procedure.

 

[*8.2.7   Advanced Considerations*](#toc.xhtml#Rh2-49)

There are several aspects that should be considered in order to take advantage of the full potential of Gaussian process regression. Key aspects are related to (1) the definition of the prior mean functions, (2) the choice of covariance and correlation functions, and (3) the formulation required for modeling cases involving heteroscedastic errors.

*Prior mean functions*   In the examples presented in [§8.2](#chapter007.xhtml#Sec_8.2), the prior mean was always assumed to be a known constant. If needed, this assumption can be relaxed by treating the prior mean as a parameterized function to be inferred from data. In its simplest case, the mean can be assumed to be a single unknown constant. In more advanced cases we could describe our prior knowledge of the mean as a parameterized function that depends on covariates x. For example, if there is a single covariate, the mean could be modeled by the affine function *m*(*x*) = *ax* + *b*, where {*a, b*} are parameters that need to be estimated from data. When using complex functions to describe the prior mean, it is essential to keep in mind that this procedure is sensitive to *overfitting* in a similar way as linear regression (see [§8.1.2](#chapter007.xhtml#Sec_8.1.2)). Employing a highly flexible parameterization may lead to an increased log-likelihood in the training set, yet it may not materialize in the prediction performance evaluated on the test set. It is therefore essential to choose the best prior parameterization using methods such as *cross-validation* (see [§8.1.2](#chapter007.xhtml#Sec_8.1.2)) or *Bayesian model selection* (see [§6.8](#chapter005.xhtml#Sec_6.8)).

*Covariance functions*   In this section, only the square-exponential correlation function was described; nonetheless, several other choices exist. In his thesis, Duvenaud^([8](#chapter007.xhtml#footnote_8)) presents several covariance models. A common one is the *Matern*\-class correlation function, for which a special case is defined as

![art](images/Art_P645.jpg)

[Figure 8.28](#chapter007.xhtml#Fig_8-28) represents this correlation function for several length-scale values.

![art](images/Art_P646.jpg)

Figure 8.28: An example of Matern-class correlation function.

When using the square-exponential correlation function with covariate values that are close to each other, it is common to obtain correlation coefficients *ρ*(**x***[i],***x***[j]*) close to one. This has the adverse effect of leading to singular or near-singular covariance matrices (see [§2.4.2](#chapter001.xhtml#Sec_2.4.2)). Matern-class correlation functions can mitigate this problem because of its rapid reduction of the correlation coefficient, with an increase in the absolute distance between covariates.

Another correlation function particularly useful for engineering applications is the *periodic* one defined as

![art](images/Art_P647.jpg)

[Figure 8.29](#chapter007.xhtml#Fig_8-29) presents examples of the periodic correlation function for periods *p* = {5, 10} and length-scale parameters *ℓ* = {0.5, 1}. As its name indicates, this function is suited for modeling periodic phenomena, where events spaced by a distance close to the period *p* will have a high correlation. The length-scale *ℓ* controls how fast the correlation decreases as the distance between covariates gets away from an integer that is a multiple of the period *p*.

![art](images/Art_P648.jpg)

Figure 8.29: Examples of periodic correlation functions.

[Figure 8.30](#chapter007.xhtml#Fig_8-30) presents an example of the periodic correlation function employed to model the historical daily average temperatures recorded at Montreal airport from 1953 to 1960. The blue circles represent the training data that were employed to learn the parameters: the prior mean value *µ*, the Gaussian process prior standard deviation *σ[G]*, the observation standard deviation *σ[V]* , and the period *p*. The pink crosses represent the test data that was not employed to perform predictions or to learn parameters. Most observations from the test set lie within the *±*2*σ* posterior interval. It shows how Gaussian process regression can, even with such a simple model with only four parameters, capture the temperature pattern as well as its uncertainty.

![art](images/Art_P649.jpg)

Figure 8.30: Example of application of a periodic covariance function to model temperature data.

For more complex problems, highly complex covariance structures can be built by adding together simpler ones, such as those described in this section (see Rasmussen and Williams^([9](#chapter007.xhtml#footnote_9)) for details). The choice regarding which correlation or covariance structure is most appropriate should, as for the prior mean functions, be based on methods such as *cross-validation* (see [§8.1.2](#chapter007.xhtml#Sec_8.1.2)) or *Bayesian model selection* (see [§6.8](#chapter005.xhtml#Sec_6.8)).

*Homo- and heteroscedasticity*   So far, this section has only treated cases associated with homoscedastic errors such as the generic case presented in [figure 8.31a](#chapter007.xhtml#Fig_8-31). In engineering applications, it is common to be confronted with cases where the variances ![art](images/Art_P650.jpg)or ![art](images/Art_P651.jpg)depend on the covariate values. A generic example of heteroscedastic cases is presented in [figure 8.31b](#chapter007.xhtml#Fig_8-31), which has been modeled by considering that the observation-error standard deviation *σ[V]* is itself modeled as a Gaussian process that depends on covariate values.^([10](#chapter007.xhtml#footnote_10)) This method is implemented in the GPstuff^([11](#chapter007.xhtml#footnote_11)) toolbox.

![art](images/Art_P652.jpg)

Figure 8.31: Examples of homo- and heteroscedastic cases where the shaded regions represent *µ[Y]* ± 2*σ[Y]*.

 

[*8.3   Neural Networks*](#toc.xhtml#Rh1-32)

The idea behind neural networks originates from the perceptron model^([12](#chapter007.xhtml#footnote_12)) developed in the 1950s. Neural networks became extremely popular in the period from 1980 until the mid-1990s when they became overshadowed by other emerging methods. It was not until the early 2010s, with the appellation of *deep learning*, that they again took the leading role in the development of machine learning methods. In deep learning, the label *deep* refers to the great number of layers in the model. The rise of deep learning as the state-of-the-art method was caused by three main factors:^([13](#chapter007.xhtml#footnote_13)) (1) the increasing size of the data sets to train on, (2) the increase in computational capacity brought by graphical processing units (GPUs), and (3) the improvements in the methods allowing to train deeper models. One limitation is that in order to achieve the performance it is renowned for, deep learning requires large data sets containing from thousands to millions of labeled examples for covariates **x***[i]* and system responses *y[i]*. In the field of computer vision, speech recognition, and genomics, it is common to deal with data sets of such a large size; in the civil engineering context, it is not yet the case.

This section presents the basic formulation for the simplest neural network architecture: the *feedforward neural network*. The reader interested in a detailed review of neural networks and their numerous architectures—such as *convolutional neural networks* (CNN), *generative adversarial networks* (GAN), and *recurrent neural networks* (RNN, LSTM)—should refer to specialized textbooks such as the one by Goodfellow, Bengio, and Courville (2016).

 

[*8.3.1   Feedforward Neural Networks*](#toc.xhtml#Rh2-50)

Feedforward is the simplest architecture for neural networks, where information is transferred from the input layer to the output layer by propagating it into layers of hidden variables. The idea is to approximate complex functions by a succession of simple combinations of hidden variables organized in layers.

*Linear regression*   The linear regression method presented in [§8.1](#chapter007.xhtml#Sec_8.1) is employed to introduce the concepts surrounding feedforward neural networks. [Figure 8.32](#chapter007.xhtml#Fig_8-32) presents a regression problem where three covariates x = \[*x*[1]*x*[2]*x*[3]\]^(**T**) are associated with a single observed system response *y* = *z* + *v*, ![art](images/Art_P653.jpg), where *v* is a realization of a zero-mean normal observation error. *z* represents a hidden variable, which is defined by the linear combination of covariate values using three weight parameters and one bias parameter,

*z* = *w*[1]*x*[1] + *w*[2]*x*[2] + *w*[3]*x*[3] + *b*.

![art](images/Art_P654.jpg)

Figure 8.32: Representation of linear regression as a feedforward neural network. The leftmost nodes represent covariates, the white node is a hidden variable, and the rightmost node represents the observation.

In [figure 8.32](#chapter007.xhtml#Fig_8-32), the leftmost nodes represent covariates, the white node is a hidden variable, and the rightmost node is the observations ![art](images/Art_P655.jpg). Arrows represent the dependencies defined by the weight and bias parameters {*w*[1], *w*[2], *w*[3], *b*}. Weight parameter *w[i]* describes the slope of a plane with respect to each variable, and *b* the plane’s intercept (e.g., see [figure 2.2](#chapter001.xhtml#Fig_2-2)). With the current configuration, this model is limited because it is only a linear function, that is, the hidden variable *z* is a linear function with respect to covariates **x**.

**Nomenclature**

![art](images/Art_P659.jpg): the *i*^(th) hidden variable on the *l*^(th) layer

![art](images/Art_P660.jpg): the weight defining the dependence between the *i*^(th) variable of the (*l* + 1)^(th) layer and the *j*^(th) hidden variable of the (*l*)^(th) layer

![art](images/Art_P661.jpg): the plane’s intercept for the *i*^(th) hidden variable of the (*l* + 1)^(th) layer

*x[j]*: *j*^(th) covariate

*Linear regression with multiple layers*   Now we explore the effect of modifying the model as presented in [figure 8.33](#chapter007.xhtml#Fig_8-33) by adding multiple hidden variables, where each one is modeled as a linear combination of either the covariates or the hidden variables on the preceding layer. First, let us define the notation employed to describe this network: ![art](images/Art_P656.jpg)represents the *i*^(th) hidden variable on the *l*^(th) layer. In the first layer, the two hidden variables are defined by

![art](images/Art_P657.jpg)

![art](images/Art_P658.jpg)

Figure 8.33: Representation of linear regression using multiple layers. The leftmost nodes represent covariates, the white nodes the hidden variables, and the rightmost node the observation.

where ![art](images/Art_P662.jpg)is the weight defining the dependence between the *j*^(th) variable of the 0^(th) layer (i.e., the first covariate itself) and the *i*^(th) hidden variable of the 1^(st) layer. Following the same notation, ![art](images/Art_P663.jpg)describes the plane’s intercept for the *i*^(th) hidden variable of the 1^(st) layer. The only hidden variable on the second layer is defined as a linear combination of the two hidden variables on layer 1, so

![art](images/Art_P664.jpg)

The observation model is now defined by ![art](images/Art_P665.jpg), so each observation of the system response is defined as ![art](images/Art_P666.jpg). Note that ![art](images/Art_P667.jpg)implicitly depends on the covariates **x**, so that there are covariates implicitly associated with each observation *y[i]*. The complete data set is D = {D*[x]*, D*[y]*} = {(**x***[i]*, *y[i]*), ∀*i* ∈ {1 : D}}.

In this second case, adding hidden variables did not help us to generalize our model to nonlinear system responses because linear functions of linear functions are themselves still linear. Therefore, no matter how many layers of hidden variables we add, the final model remains a hyperplane. In order to describe nonlinear functions, we need to introduce nonlinearities using *activation functions*.

*Activation functions*   An *activation function* describes a nonlinear transformation of a hidden variable *z*. Common activation functions are the *logistic*, the *hyperbolic tangent* (tanh), and the *rectified linear unit* (ReLU),

![art](images/Art_P668.jpg)

These three activation functions are presented in [figure 8.34](#chapter007.xhtml#Fig_8-34). The ReLU activation function is currently widely employed because it facilitates the training of models by mitigating the problems associated with vanishing gradients (see [§8.3.2](#chapter007.xhtml#Sec_8.3.2)).

![art](images/Art_P669.jpg)

Figure 8.34: Comparison of the *logistic*, *tanh*, and *ReLU* activation functions.

*Feedforward neural networks: A simple case*   In a feedforward network, a hidden variable ![art](images/Art_P670.jpg)is passed through an activation function,

![art](images/Art_P671.jpg)

before getting fed to the next level. The output of the activation function is called the *activation unit*. [Figure 8.35](#chapter007.xhtml#Fig_8-35) presents the expanded and compact forms for a simple feedforward network with three covariates in its *input layer*, one *hidden layer* containing two activation units (green nodes), and one *output layer* containing a single activation unit (blue node). Note that in the compact forms (i.e., (b) and (c)), hidden variables ![art](images/Art_P672.jpg)are not explicitly represented anymore. The activation units on the first layer are

![art](images/Art_P673.jpg)

![art](images/Art_P677.jpg)

Figure 8.35: A simple feedforward neural network.

The output unit *a*^((O)) is equal to the hidden variable *z*^((O)), which is itself defined as a linear combination of the activation units on the hidden layer so that

![art](images/Art_P674.jpg)

The observation model is now defined by ![art](images/Art_P675.jpg), so each observation of the system response is defined as ![art](images/Art_P676.jpg).

*Fully connected feedforward neural network*   We now describe formulation for the *fully connected feedforward neural network* (FCNN) with L hidden layers, each having A activation units. The example presented includes a single output observation. In practice, FCNN can be employed for any number of output variables.

 

[Figure 8.36](#chapter007.xhtml#Fig_8-36) presents a graphical representation for an FCNN where (a) presents the connectivity with the activation functions and (b) the nomenclature employed for weights ![art](images/Art_P678.jpg)and hidden units ![art](images/Art_P679.jpg). The activation unit *i* in the first layer is described by a linear combination of covariates,

![art](images/Art_P680.jpg)

![art](images/Art_P681.jpg)

Figure 8.36: A fully connected neural network having L hidden layers, each having A activation units. The leftmost nodes describe the *input layer* containing X covariates. The green inner nodes describe the unobserved *hidden layers* where an activation unit *i* in layer *l* is ![art](images/Art_P682.jpg). The blue node describes the *output layer* where *a*^((O)) = *σ*^O(*z*^((O))) = *z*^((O)) for regression problems. The rightmost node describes the *observed system responses*, which are realizations ![art](images/Art_P683.jpg).

In subsequent layers, the activation unit *i* in layer *l* + 1 is a linear combination of all the activation units in layer *l* as described by

 

![art](images/Art_P684.jpg)

The feedforward propagation for all the units contained in a layer can be expressed with a matrix notation as **a**^((*l*+1)) = *σ*(**z**^((*l*+1))), that is,

![art](images/Art_P685.jpg)

where the hidden variables are given by **z**^((*l*+1)) = **W**^((*l*))**a**^((*l*)) + **b**^((*l*)), that is,

![art](images/Art_P686.jpg)

The variables *z*^((O)) and *a*^((O)) on the output layer are obtained from a linear combination of the activation units on the last hidden layer L,

![art](images/Art_P687.jpg)

Because we are dealing with a regression problem, we can consider that the output activation function *σ*^O(·) is linear. The observation model is defined by ![art](images/Art_P688.jpg), ![art](images/Art_P688a.jpg), so each observation of the system response is defined as ![art](images/Art_P689.jpg).

Neural networks are characterized by their large number of parameters to be estimated. For example, a fully connected network with L layers, each having A activation units, has A × A × (L − 1) weight parameters and A × L bias parameters for its hidden layers. For L = A = 10, it leads to more than 1000 parameters to be learned from the data set D. In comparison, the GPR model presented in [§8.2](#chapter007.xhtml#Sec_8.2) had fewer than 10 parameters. Moreover, it is not uncommon for modern deep neural networks to be parameterized by millions of parameters. As a consequence, learning these parameters (i.e., training the neural network) requires large data sets and is a computationally demanding task.

 

[*8.3.2   Parameter Estimation and Backpropagation*](#toc.xhtml#Rh2-51)

The task of learning model parameters is referred to as *training* a neural network. In general, there are so many parameters to be learned that the utilization of second-order optimization methods such as Newton-Raphson (see [§5.2](#chapter004.xhtml#Sec_5.2)) are computationally prohibitive. Instead, neural networks rely on gradient descent algorithms (see [§5.1](#chapter004.xhtml#Sec_5.1)), where the gradient of the loss function with respect to each parameter is obtained using the *backpropagation* method.

*Log-likelihood*   As for other types of regression models, the performance of a neural network is measured using quantities derived from the likelihood of observations *f*(D*[y]*|D*[x]*, ***θ**[w]*, ***θ**[b]*), where {***θ**[w]*, ***θ**[b]*} are respectively the weight and bias parameters. By assuming that observations are conditionally independent given *a*^((O)), the joint likelihood for a data set D = {D*[x], D[y]*} = {(**x***[i], y[i]*), ∀*i* ∈ {1 : D}} is defined as

![art](images/Art_P690.jpg)

where *a*^((O))(**x***[i]*; ***θ***[*w*], ***θ**[b]*) ≡ *a*^((O)) explicitly defines the dependence of the output layer on the bias and weight parameters from all layers. In practice, neural networks are trained by minimizing a loss function *J*(D; ***θ**[w], **θ**[b]*), which is derived from the negative log-likelihood,

**Note:** The derivation of the loss function for a *neural network* is analogous to the derivation of the loss function presented in [§ 8.1.1](#chapter007.xhtml#Sec_8.1.1) for *linear regression*.

![art](images/Art_P691.jpg)

Note that the loss function *J*(D; ***θ**[w], **θ**[b]*) corresponds to the *mean-square error* (MSE). The optimal set of parameters ![art](images/Art_P692.jpg)are thus those which minimize the MSE,

![art](images/Art_P693.jpg)

 

*Gradient descent*   The optimal values ***θ***^∗ are sought iteratively using a gradient-descent algorithm, where the updated parameter values are

***θ*** ← ***θ*** − λ∇[***θ***]*J*(D; ***θ**[w]*, ***θ**[b]*)

and where *λ* is the *learning rate* (see [§5.1](#chapter004.xhtml#Sec_5.1)). The gradients are estimated using the *backpropagation* algorithm that will be presented next. The parameters ***θ***[0] = {***θ**[w], **θ**[b]*} are typically initialized randomly following ***θ**[i]* ~ N (***θ***; 0, *ϵ*²), where *ϵ* ≈ 10^(−2). The random initialization is intended to avoid having an initial symmetry in the model. The objective of having initial values close to zero is that multiplying covariates and hidden variables by weights ![art](images/Art_P694.jpg)will initially limit the model capacity. Note that a common practice is to normalize covariates and observations in the data set.

**Feedforward neural network**

![art](images/Art_P695.jpg)

**Chain rule of derivation**

![art](images/Art_P696.jpg)

*Backpropagation*   The *backpropagation*^([14](#chapter007.xhtml#footnote_14)) method employs the 14 Rumelhart, D. E., G. E. Hinton, and *chain rule of derivation* in order to backpropagate the model prediction errors through the network. For a single observation (**x***[i], y[i]*), the prediction error ![art](images/Art_P697.jpg)is defined as the discrepancy between the predicted value *a*^((O))(**x***[i]*; ***θ**[w], **θ**[b]*) and the observation *y[i]*, times the gradient of the output’s activation function,

![art](images/Art_P698.jpg)

In the context of regression, the term ![art](images/Art_P699.jpg)is equal to one because *a*^((O)) = *σ*^O(*z*^((O))) = *z*^((O)). Note that in order to evaluate the prediction error for an observation *y[i]*, we first need to evaluate the model prediction for the current parameter values {***θ**[w], **θ**[b]*} and a vector of covariates **x***[i]*. For the *i*^(th) observation in the training set, the gradient vector of the loss function with respect to either weight or bias parameters on the *l*^(th) layer is

![art](images/Art_P700.jpg)

For hidden layers, the responsibility of each activation unit for the prediction error is estimated using

![art](images/Art_P701.jpg)

where ⊙ is the Hadamar (element-wise) product, and ∇ denotes the gradient vector.

 

The common procedure is to perform parameter updates not using each observation individually, but by using *mini-batches*. A mini-batch D^(mb) ⊂ D is a subset of observations of size *n* that is a power of 2 ranging from 32 to 256. The power of 2 constraint is there to maximize the computational efficiency when working with graphical processing units (GPUs). The gradient of the loss function is then the average of the gradients obtained for each observation in a mini-batch,

![art](images/Art_P702.jpg)

**Note:** Several of the advances made in neural networks can be attributed to advancements in GPU calculations. Nowadays most nontrivial models are trained using GPUs.

During training, an *epoch* corresponds to performing one pass of parameter update for all mini-batches contained in the training set. Neural networks are typically trained using *stochastic gradient descent*, which computes the gradient on the subset of data contained in mini-batches rather than on the full data set. The reader should refer to specialized literature^([15](#chapter007.xhtml#footnote_15)) for descriptions of stochastic gradient descent optimization methods such as *Adagrad*, *RMSprop*, and *Adam*.

 

[*8.3.3   Regularization*](#toc.xhtml#Rh2-52)

Because of the large number of parameters involved in the definition of a neural network, it is prone to overfitting, where the performance obtained during training will not generalize for the test set. Here, we present two *regularization* procedures to prevent overfitting: *weight decay* and *early stopping*.

*Weight decay*   The first regularization strategy is to employ maximum a-posteriori (MAP) estimation rather than a maximum likelihood estimate (MLE). The prior knowledge for model parameters in an MAP allows us to prevent overfitting by limiting the model complexity. For instance, we can define a prior for the weights in the vector ***θ**[w]* so that ![art](images/Art_P703.jpg). A large *α* value forces weight parameters to be close to zero, which in turn reduces the model capacity. If *α* is small, little penalization is applied on weights and the model is then free to be highly nonlinear and can more easily fit the data in the training set.

With MAP, the posterior is now approximated by the product of the likelihood and the prior, so

![art](images/Art_P704.jpg)

We can then redefine the loss function as

![art](images/Art_P705.jpg)

where Ω(***θ***), the *regularization* or *weight decay* term, is

![art](images/Art_P706.jpg)

Defining a Gaussian prior for weights corresponds to *L*²\-norm regularization. This choice for regularization is not the only one available, yet it is a common one. The gradient of the loss function with respect to weight parameters has to be modified to include the regularization term, so

![art](images/Art_P707.jpg)

In short, weight decay allows controlling the model capacity with the hyperparameter *α*. The hyperparameter *α* then needs to be learned using a method such as *cross-validation* (see [§8.1.2](#chapter007.xhtml#Sec_8.1.2)).

*Early stopping*   Given that we initialize each parameter randomly, following *θ[i]* ~ N (*θ*; 0, *ϵ*²), with *ϵ* ≈ 10^(−2), the model will initially have a poor performance at fitting the observations in the training set. As the number of optimization epochs increases, the fitting ability of the model will improve and, as a result, the loss for the training set *J*(D^(train); ***θ**[w], **θ**[b]*) will decrease. If we keep optimizing parameters, there is a point where the model will gain too much capacity, and it will start overfitting the data in the training set. Thus, a second option to prevent overfitting is to monitor the loss function evaluated at each epoch for an independent validation set *J*(D^(validation); ***θ**[w], **θ**[b]*). Note that the data in the validation set must not be employed to train the model parameters. The optimal parameter values ![art](images/Art_P708.jpg)are taken as those corresponding to the epoch for which the loss evaluated for the validation set is minimal. This procedure is equivalent to treating the number of training epochs as a hyperparameter to be optimized using the validation set.

[Figure 8.37](#chapter007.xhtml#Fig_8-37) presents an example of early stopping where we see that the loss for the training set keeps decreasing with the number of epochs. For the loss evaluated on the validation set, the minimum is reached at seven epochs. Beyond seven epochs, the fitting ability we gain on the training set does not generalize on the validation set.

![art](images/Art_P709.jpg)

Figure 8.37: Example of early stopping when the loss function for the validation set stops decreasing.

 

[*8.3.4   Example: Metamodel*](#toc.xhtml#Rh2-53)

Here we revisit the example presented in [§8.2.6](#chapter007.xhtml#Sec_8.2.6), where we construct a metamodel for the responses of a structure using five covariates and a set of D = 1000 simulations. For this example, we employ a tanh activation function with A = 10 activation units on each of the L = 2 hidden layers. [Figure 8.38](#chapter007.xhtml#Fig_8-38) compares the system responses with the model predictions obtained in a leave-one-out cross-validation setup where for each fold, 90 percent of the data is employed for training the model and the remaining 10 percent to validate when the training should be stopped. The loss function *J*(D; ***θ**[w], **θ**[b]*), evaluated using the leave-one-out cross-validation procedure, is equal to 1.32 × 10^(−5). In comparison, the equivalent mean-square error obtained for the GPR model presented in [§8.2.6](#chapter007.xhtml#Sec_8.2.6) is 8.8 × 10^(−6). It shows that neural networks are not necessarily outperforming other methods, because they are typically best suited for problems involving a large number of covariates and for which large data sets are available.

![art](images/Art_P710.jpg)

Figure 8.38: Comparison of the system responses with the model predictions obtained in a leave-one-out cross-validation setup.

 

 

*Exercises*

 
| P8.1 || Why does linear regression have an analytic formulation for identifying the MLE optimal parameters while other regression methods do not? |
| --- | --- |
| P8.2 || How can linear regression be employed to model nonlinear relationships between *x* and *y*? |
| P8.3 || Explain the bias-variance tradeoff and its relationship with overfitting. |
| P8.4 || Explain the approaches to prevent overfitting. |
| P8.5 || Explain a correlation and covariance function in the context of a Gaussian process. |
| P8.6 || For Gaussian process regression, what is the relationship between a length-scale *ℓ* and the importance of its associated covariate? |
| P8.7 || Explain why methods such as linear regression and neural networks are more prone to overfitting than Gaussian process regression. In what case does the Gaussian process regression also become sensitive to overfitting? |
| P8.8 || In the context of regression, formulate the likelihood for a set of observations D = {D*[x]*, D*[y]*}, D*[x]* = {*x*[1], *x*[2], ⋯ , *x*[D]}, D*[y]* = {*y*[1], *y*[2], ⋯ , *y*[D]} for the observation model![art](images/Art_P711.jpg) |
| P8.9 || Given the data set D = {(*x[i], y[i]*), ∀*i* = {1 : 10}} where *x* describes the longitudinal position in kilometers along a pipeline and *y* describes the temperature in degrees Celsius. Observations follow the equation *y[i]* = *g*(*x[i]*) + *v[i]*, where *v[i]* is an observation error that is a realization of the random variable ![art](images/Art_P712.jpg).![art](images/Art_P713.jpg)a. Implement your own Gaussian process regression model for the data set, and learn the maximum likelihood estimate for hyperparameters P = {*σ[V]*, *σ[g], ℓ*}. Use the hypothesis that the prior mean ***µ*[g]** = **0**.b. Estimate the posterior covariance matrix for hyperparameters obtained in (a) using the Laplace approximation.c. Plot the expected values *µ*[∗] as well as the *µ*[∗] ± *σ*[∗] confidence region for the model in the range *x*[∗] ∈ {0, 1, ⋯ , 100}. |

 

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter007.xhtml#footnote_ref_1) Hoerl, A. E. and R. W. Kennard (1970). Ridge regression: Biased estimation for nonorthogonal problems. *Technometrics 12* (1), 55–67.

[²](#chapter007.xhtml#footnote_ref_2) Quiñonero-Candela, J. and C. E. Rasmussen (2005). A unifying view of sparse approximate Gaussian process regression. *Journal of Machine Learning Research 6*, 1939–1959.

[³](#chapter007.xhtml#footnote_ref_3) Rasmussen, C. E. and H. Nickisch (2010). Gaussian processes for machine learning (GPML) toolbox. *The Journal of Machine Learning Research 11*, 3011–3015.

[⁴](#chapter007.xhtml#footnote_ref_4) Vanhatalo, J., J. Riihimäki, J. Hartikainen, P. Jylänki, V. Tolvanen, and A. Vehtari (2013). GPstuff: Bayesian modeling with Gaussian processes. *Journal of Machine Learning Research 14*, 1175–1179.

[⁵](#chapter007.xhtml#footnote_ref_5) Neumann, M., S. Huang, D. E. Marthaler, and K. Kersting (2015). pyGPs: A python library for Gaussian process regression and classification. *The Journal of Machine Learning Research 16* (1), 2611–2616.

[⁶](#chapter007.xhtml#footnote_ref_6) Quach, A. N. O., D. Tabor, L. Dumont, B. Courcelles, and J.-A. Goulet (2017). A machine learning approach for characterizing soil contamination in the presence of physical site discontinuities and aggregated samples. *Advanced Engineering Informatics 33*, 60–67.

[⁷](#chapter007.xhtml#footnote_ref_7) Westgate, R. J. and J. M. W. Brownjohn (2011). Development of a Tamar Bridge finite element model. In *Conference Proceedings of the Society for Experimental Mechanics*, Volume 5, pp. 13–20. Springer.

[⁸](#chapter007.xhtml#footnote_ref_8) Duvenaud, D. (2014). *Automatic model construction with Gaussian processes*. PhD thesis, University of Cambridge.

[⁹](#chapter007.xhtml#footnote_ref_9) Rasmussen, C. E. and C. K. Williams (2006). *Gaussian processes for machine learning*. MIT Press.

[^(10)](#chapter007.xhtml#footnote_ref_10) Tolvanen, V., P. Jylänki, and A. Vehtari (2014). Expectation propagation for nonstationary heteroscedastic Gaussian process regression. In *IEEE International Workshop on Machine Learning for Signal Processing (MLSP)*, 1–6. IEEE.

[^(11)](#chapter007.xhtml#footnote_ref_11) Vanhatalo, J., J. Riihimäki, J. Hartikainen, P. Jylänki, V. Tolvanen, and A. Vehtari (2013). GPstuff: Bayesian modeling with Gaussian processes. *Journal of Machine Learning Research 14*, 1175–1179.

[^(12)](#chapter007.xhtml#footnote_ref_12) Rosenblatt, F. (1958). The perceptron: A probabilistic model for information storage and organization in the brain. *Psychological Review 65* (6), 386.

[^(13)](#chapter007.xhtml#footnote_ref_13) Goodfellow, I., Y. Bengio, and A. Courville (2016). *Deep learning*. MIT Press.

[^(14)](#chapter007.xhtml#footnote_ref_14) R. J. Williams (1986). Learning representations by back-propagating errors. *Nature 323*, 533–536.

[^(15)](#chapter007.xhtml#footnote_ref_15) Goodfellow, I., Y. Bengio, and A. Courville (2016). *Deep learning*. MIT Press.

 

[*9*](#toc.xhtml#chap-8)

[*Classification*](#toc.xhtml#chap-8)

**Data**

D = {(**x***[i]*, *y[i]*), ∈*i* ∈ {1 : D}}

![art](images/Art_P715.jpg)

*y[i]* ∈ {−1, +1} : Observation for binary classification

*y[i]* ∈ {1, 2, ⋯ , C} : Observation for multiclasses classification

Classification is similar to regression, where the task is to predict a system response *y*, given some covariates x describing the system properties. With regression, the system responses were continuous quantities; with *classification*, the system responses are now *discrete classes*. [Figure 9.1](#chapter008.xhtml#Fig_9-1) presents two examples of classification applied to the civil engineering context; in (a), the sigmoid-like curve describes the probability of having pathogens in water, as a function of the chlorine concentration. In this problem, observations are either −1 or +1, respectively corresponding to one of the two classes {pathogens, ¬pathogens}. The second example, (b), presents the probability of having structural damage in a building given the peak ground acceleration (PGA) associated with an earthquake. Observations are either −1 or +1, respectively corresponding to one of the two classes {damage, ¬damage}.

![art](images/Art_P714.jpg)

Figure 9.1: Examples of application of classification analysis in the context of civil engineering.

For classification, the data consists in D pairs of covariates **x***[i]* ∈ ℝ^X and system responses *y[i]* ∈ {−1, +1}, so D = {(**x***[i], y[i]*), ∀*i* ∈ {1 : D}}. For problems involving multiple classes, the system response is *y[i]* ∈ {1, 2, ⋯ , C}. The typical goal of a classification method is to obtain a mathematical model for the probability of a system response given a covariate, for example, Pr(*Y* = +1|**x**). This problem can be modeled with either a *generative* or a *discriminative* approach. A generative classifier models the probability density function (PDF) of the covariates **x**, for each class *y*, and then use these PDFs to compute the probability of classes given the covariate values. A discriminative classifier directly builds a model of Pr(*Y* = +1|**x**) without modeling the probability density function (PDF) of covariates **x**, for each class *y*. In practice, discriminative approaches are most common because they typically perform better on medium and large data sets,^([1](#chapter008.xhtml#footnote_1)) and are often easier to use. This chapter presents the generic formulation for probabilistic generative classifiers and three discriminative classifiers: *logistic regression*, *Gaussian process classification*, and *neural networks*. We will see that *generative classifiers* are best suited for small data sets, *Gaussian process classification* is suited for medium-size ones, and *neural networks* for large ones. In order to simplify the explanations, this chapter presents each method while focusing on the context of *binary* classification, that is, *y* ∈ {−1, +1}.

 

[*9.1   Generative Classifiers*](#toc.xhtml#Rh1-33)

The basic idea of a *generative classifier* is to employ a set of observations D to model the conditional PDF of covariates **x** ∈ ℝ^X given each class *y* ∈ {−1, +1}. Then these PDFs are employed in combination with the prior probability of each class in order to obtain the posterior probability of a class given a covariate **x**. Generative classifiers are most appropriate when working with problems involving a small number of covariates and observations because they allow us to explicitly include domain-specific knowledge regarding *f*(**x**|*y*) or tailored features such as censored data.

 

[*9.1.1   Formulation*](#toc.xhtml#Rh2-54)

The posterior probability of a class *y* given covariates **x** can be expressed using Bayes rule,

![art](images/Art_P716.jpg)

The posterior probability of a class *y* conditional on a covariate value *x* is defined according to

![art](images/Art_P717.jpg)

The prior probability of a class is described by the probabilities

![art](images/Art_P718.jpg)

**Note:** the prior knowledge can either be based on expert knowledge, i.e., *p*(*y*), or be empirically estimated using observations, i.e.,

![art](images/Art_P719.jpg)

The prior and posterior are described by probability mass functions because *y* ∈ {−1, +1} is a discrete variable. The likelihood of covariates **x** conditional on a class *y* is a multivariate conditional probability density function that follows

![art](images/Art_P720.jpg)

 

The normalization constant (i.e., the evidence) is obtained by summing the product of the likelihood and prior over all classes,

![art](images/Art_P721.jpg)

A key step with a generative classifier is to pick a distribution type for each *f*(**x**|*y[j]*; ***θ**[j]*), ∀ *j* and then estimate the parameters ***θ**[j]* for these PDFs using the data set D, that is, *f*(***θ**[j]*|D). For a class *y* = *j*, the parameters of *f*(**x**|*y[j]*) ≡ *f*(**x**|*y[j]*; ***θ**[j]*) are estimated using only observations D*[j]* : {(**x**, *y*)*[i]*, ∀*i* : *y[i]* = *j*}, that is, the covariates **x***[i]* such that the associated system response is *y[i]* = *j*. The estimation of parameters ***θ*** can be performed using either a Bayesian approach or a deterministic one as detailed in [§6.3](#chapter005.xhtml#Sec_6.3). Like for the likelihood, the prior probability of each class *p*(*y*|D) can be estimated using either a Bayesian approach or a deterministic one using the relative frequency of observations where *y[i]* = *j*. With a Bayesian approach, the posterior predictive probability mass function (PMF) is obtained by marginalizing the uncertainty about the posterior parameter estimate,

![art](images/Art_P722.jpg)

**Note:** The notation *f*(**x**|*y*; ***θ***) ≡ *f*(**x**|*y, **θ***) indicates that the conditional probability *f*(**x**|*y*) is parameterized by ***θ***.

When either a maximum a-posteriori (MAP) or a maximum likelihood estimate (MLE) is employed instead of a Bayesian estimation approach, the posterior predictive is replaced by the approximation,

![art](images/Art_P724.jpg)

where ***θ**^∗* are the MLE or MAP estimates for parameters.

*Maximum likelihood estimate*   In the special case where ![art](images/Art_P725.jpg)and the number of available data D is large, one can employ the MLE approximation for the parameters ![art](images/Art_P726.jpg)and ![art](images/Art_P727.jpg)which is defined by

![art](images/Art_P728.jpg)

where D*[j]* = #{*i* : *y[i]* = *j*} denotes the number of observations in a data set D that belongs to the *j*^(th) class. The MLE approximation of *p*(*y* = *j*; ***θ**^∗*) is given by

![art](images/Art_P729.jpg)

![art](images/Art_P723.jpg)

 

[Figure 9.2](#chapter008.xhtml#Fig_9-2) presents an example of application of a generative classifier where the parameters for the normal PDFs are estimated using the MLE approximation. The bottom graph overlays the empirical histograms for the data associated with each class along with the PDFs *f*(*x*|*y* = *j, **θ**^∗*). The top graph presents the classifier *p*(*y* = +1|*x, **θ***^∗), which is the probability of the class *y* = +1 given the covariate value *x*. If we assume that the prior probability of each class is equal, this conditional probability is computed as

![art](images/Art_P730.jpg)

![art](images/Art_P732.jpg)

Figure 9.2: Example of generative classifier using marginal PDFs.

*Multiple covariates*   When there is more than one covariate **x** = \[*x*[1]*x*[2] ⋯ *x*[X]\]^(**T**) describing a system, we must define the joint PDF *f*(**x**|*y*). A common approach to define this joint PDF is called *naive Bayes* (NB). It assumes that covariates *X[k]* are independent of each other so their joint PDF is obtained from the product of the marginals,

![art](images/Art_P731.jpg)

The method employing the special case where the joint PDF of covariates is described by a multivariate normal *f*(**x**|*y*) = N (**x**; ***µ***, Σ) is called *quadratic discriminant analysis* (QDA). The label *quadratic* refers to the shape of the boundary in the covariate domain where the probability of both classes are equal, Pr(*y* = +1|**x**) = Pr(*y* = −1|**x**). In the case where the covariance matrix Σ is the same for each class, the boundary becomes linear, and this special case is named *linear discriminant analysis* (LDA). Both the naive Bayes, QDA, and LDA methods typically employ an MLE approach to estimate the parameters of *f*(**x**|*y* = *j*). [Figure 9.3](#chapter008.xhtml#Fig_9-3) presents examples of *f*(**x**|*y* = *j*) for the three approaches: NB, LDA, and QDA. [Figure 9.4](#chapter008.xhtml#Fig_9-4) presents an example of an application of quadratic discriminant analysis where the joint probabilities *f*(**x**|*y*) are multivariate Normal PDFs as depicted by the contour plots. The mean vector and covariance matrices describing these PDFs are estimated using an MLE approximation. Because there are two covariates, the classifier *f*(*y* = +1|**x**) is now a 2-D surface obtained following

![art](images/Art_P733.jpg)

![art](images/Art_P734.jpg)

Figure 9.3: Examples of PDF *f*(**x**|*y* = *j*) for naive Bayes, LDA, and QDA.

![art](images/Art_P736.jpg)

Figure 9.4: Example of quadratic discriminant analysis where the joint probabilities *f*(**x**|*y[i]*) depicted by contour plots are described by multivariate Normal PDFs. The parameters of each PDF are estimated using an MLE approach.

 

Note that for many problems, generative methods such as naive Bayes and quadratic discriminant analysis are outperformed by discriminative approaches such as those presented in [§9.2](#chapter008.xhtml#Sec_9.2)–[§9.4](#chapter008.xhtml#Sec_9.4).

 

[*9.1.2   Example: Post-Earthquake Structural Safety Assessment*](#toc.xhtml#Rh2-55)

We present here an example of a data-driven post-earthquake structural safety assessment. The goal is to assess right after an earthquake whether or not buildings are safe for occupation, that is, *y* ∈ {safe, ¬safe}. We want to guide this assessment based on empirical data where the observed covariate *x* ∈ (0, 1) describes the ratio of a building’s first natural frequency *f* \[Hz\] after and before the earthquake,

![art](images/Art_P735.jpg)

[Figure 9.5](#chapter008.xhtml#Fig_9-5) presents a set of 45 empirical observations^([2](#chapter008.xhtml#footnote_2)) collected in different countries and describing the frequency ratio *x* as a function of the damage index *d* ∈ {0, 1, 2, 3, 4, 5}, which ranges from undamaged (*d* = 0) up to collapse (*d* = 5). Note that observations marked by an arrow are censored data, where *x* is an upper-bound censored observation (see [§6.3](#chapter005.xhtml#Sec_6.3)) for the frequency ratio. The first step is to employ this data set ![art](images/Art_P737.jpg)in order to learn the conditional PDF of the frequency ratio *X*, given a damage index *d*. Because *x* ∈ (0, 1), we choose to describe its conditional PDF using a Beta distribution,

![art](images/Art_P738.jpg)

![art](images/Art_P741.jpg)

Figure 9.5: Empirical observations of the ratio between fundamental frequency of buildings after and before an earthquake.

Note that the Beta distribution is parameterized here by its mean and standard deviation and not by *α* and *β* as described in [§4.3](#chapter003.xhtml#Sec_4.3). The justification for this choice of parameterization will become clear when we present the constraints that are linking the prior knowledge for different damage indexes *d*. For a given *d*, the posterior PDF for the parameters ***θ***(*d*) = {*µ*(*d*), *σ*(*d*)} is obtained using Bayes,

![art](images/Art_P739.jpg)

and the posterior predictive PDF of *X* is obtained by marginalizing the uncertainty associated with the estimation of ***θ***(*d*),

![art](images/Art_P740.jpg)

 

By assuming that observations are conditionally independent given *x*, the joint likelihood of observations is

![art](images/Art_P742.jpg)

where the marginal likelihood for each observation (see [§6.3](#chapter005.xhtml#Sec_6.3)) is

![art](images/Art_P743.jpg)

and where *f*(·) denotes the PDF and *F* (·) denotes the cumulative distribution function (CDF). The prior is assumed to be uniform in the range (0, 1) for *µ*(*d*) and uniform in the range (0, 0.25) for *σ*(*d*). For the mean parameters *µ*(*d*), the prior is also constrained following *µ*(0) *\> µ*(1) > ⋯ > *µ*(5). These constraints reflect our domain-specific knowledge where expect the mean frequency ratio to decrease with increasing values of *d*.

The Metropolis algorithm presented in [§7.1](#chapter006.xhtml#Sec_7.1) is employed to generate S = 35,000 samples (![art](images/Art_P745.jpg)≤ 1.005 for C = 3 chains) from the posterior for the parameters ***θ***(*d*). [Figure 9.6a](#chapter008.xhtml#Fig_9-6) presents the contours of the posterior PDF for each pair of parameters {*µ*(*d*), *σ*(*s*)} along with a subset of samples. The predictive PDFs *f*(*x*|*d*, D) of a frequency ratio *x* conditional on *d* are presented in [figure 9.6b](#chapter008.xhtml#Fig_9-6). The predictive probability of each damage index *d* given a frequency ratio *x* is obtained following

![art](images/Art_P746.jpg)

![art](images/Art_P744.jpg)

Figure 9.6: Posterior PDFs of means and standard deviations and posterior predictive PDFs of frequency ratios *x* for each damage index *d*.

The integral in equation 9.1 can be approximated using the Markov chain Monte Carlo (MCMC) samples as described in [§7.5](#chapter006.xhtml#Sec_7.5). [Figure 9.7](#chapter008.xhtml#Fig_9-7) presents the posterior predictive probability *p*(*d*|*x*, D), which is computed while assuming that there is an equal prior probability *p*(*d*) for each damage index. This classifier can be employed to assist inspectors during post-earthquake safety assessment of structures.

![art](images/Art_P747.jpg)

Figure 9.7: Posterior predictive probability of a damage index *d* given a frequency ratio *x*.

 

[*9.2   Logistic Regression*](#toc.xhtml#Rh1-34)

*Logistic regression* is not a state-of-the-art approach, yet its prevalence, historical importance, and simple formulation make it a good choice to introduce *discriminative* regression methods. Logistic regression is the extension of linear regression (see [§8.1](#chapter007.xhtml#Sec_8.1)) for classification problems. In the context of regression, a linear function ℝ^X → ℝ is defined so that it transforms an X\-dimensions covariate domain into a single output *g*(**x**) = **Xb** ∈ ℝ. In the context of classification, system responses are discrete, for example, *y* ∈ {−1, +1}. The idea with classification is to transform the output of a linear function *g*(**x**) into the (0, 1) interval describing the probability Pr(*y* = +1|*x*). We can transform the output of a linear model **Xb** in the interval (0, 1) by passing it through a logistic *sigmoid* function *σ*(*z*),

![art](images/Art_P748.jpg)

as plotted in [figure 9.8](#chapter008.xhtml#Fig_9-8). The sigmoid is a transformation ℝ → (0, 1) such that an input defined in the real space is squashed in the interval (0, 1). In short, logistic regression maps the covariates **x** to the probability of a class,

![art](images/Art_P749.jpg)

![art](images/Art_P750.jpg)

Figure 9.8: The logistic sigmoid function *σ*(*z*) = (1 + exp(−*z*))^(−1).

Note that *g*(**x**) is considered as a *latent* or *hidden* variable because it is not directly observed; only the class *y* and its associated covariate **x** are.

[Figure 9.9](#chapter008.xhtml#Fig_9-9) presents the example of a function *g*(*x*) = 0.08*x* − 4 (i.e., the red line on the horizontal plane), which is passed through a logistic sigmoid function. The blue curve on the leftmost vertical plane is the logistic sigmoid function, and the orange curve on the right should be interpreted as the probability the class *y* = +1, given a covariate *x*, Pr(*y* = +1|*x*). For four different covariates *x[i]*, simulated observations *y[i]* ∈ {−1, +1} are depicted by crosses.

![art](images/Art_P752.jpg)

Figure 9.9: Example of a function *g*(*x*) = 0.08*x* − 4 passed through the logistic sigmoid function.

In practice, we have to follow the reverse path, where observations D = {(*x[i], y[i]*), ∀ *i* ∈ {1 : D}} are available and we need to estimate the parameters b and the basis functions *ϕ*(*x*) defining the model matrix **X**. For a given data set and a choice of basis functions, we separate the observations *x[i]* in order to build two model matrices: one for *x[i]* : *y[i]* = −1, **X**[(−1)], and another for *x[i]* : *y[i]* = +1, **X**[(+1)]. The likelihood of an observation *y* = +1 is given by Pr(*y* = +1|*x*) = *σ*(**Xb**), and for an observation *y* = −1 the likelihood is Pr(*y* = −1|*x*) = 1 − *σ*(**Xb**). With the hypothesis that observations are conditionally independent, the joint likelihood is obtained from the product of the marginal likelihood or, equivalently, the sum of the marginal log-likelihood of observations given parameters **b**,

![art](images/Art_P751.jpg)

Optimal parameters **b***^∗* can be inferred using an MLE procedure that maximizes ln *p*(D|b). Unfortunately, contrarily to the optimization of parameters in the case of the linear regression presented in [§8.1](#chapter007.xhtml#Sec_8.1), no close-form analytic solution exists here to identify **b**^∗. With linear regression, the derivative of the log-likelihood (i.e., the loss function) was linear, leading to an analytic solution for ![art](images/Art_P753.jpg). With logistic regression, the derivative of the log-likelihood is a nonlinear function, so we have to resort to an optimization algorithm (see [chapter 5](#chapter004.xhtml)) to identify **b***^∗*.

*Example: Logistic regression*   [Figure 9.10](#chapter008.xhtml#Fig_9-10) presents three examples involving a single covariate *x* and a linear model *g*(*x*) = *b*[1]*x* + *b*[0], and where parameters **b** = \[*b*[0]*b*[1]\]^(**T**) are estimated with respectively 5, 10, and 100 observations. The true parameter values employed to generate simulated observations are ![art](images/Art_P754.jpg). The corresponding functions ![art](images/Art_P755.jpg)and ![art](images/Art_P756.jpg)) are represented by dashed lines, and those estimated using MLE parameters *g*(**Xb**^∗) and *σ*(*g*(**Xb**^∗)) are represented by solid lines. We can observe that as the number of observations increases, the classifier converges toward the one employed to generate the data.

![art](images/Art_P757.jpg)

Figure 9.10: Example of application of logistic regression.

This case is a trivial one because, in this closed-loop simulation, the model structure (i.e., as defined by the basis functions in model matrix **X**) was a perfect fit for the problem. In practical cases, we have to select an appropriate set of basis functions *ϕ[j]*(*x[i]*) to suit the problem at hand. Like for the linear regression, the selection of basis functions is prone to overfitting, so we have to employ either the Bayesian model selection (see [§6.8](#chapter005.xhtml#Sec_6.8)) or cross-validation (see [§8.1.2](#chapter007.xhtml#Sec_8.1.2)) for that purpose.

*Civil engineering perspectives*   In the field of transportation engineering, logistic regression has been extensively employed for *discrete choice modeling*^([3](#chapter008.xhtml#footnote_3)) because of the interpretability of the model parameters b in the context of behavioral economics. However, for most benchmark problems, the predictive capacity of logistic regression is outperformed by more modern techniques such as *Gaussian process classification* and *neural networks*, which are presented in the next two sections.

 

[*9.3   Gaussian Process Classification*](#toc.xhtml#Rh1-35)

*Gaussian process classification*   (GPC) is the extension of Gaussian process regression (GPR; see [§8.2](#chapter007.xhtml#Sec_8.2)) to classification problems. In the context of GPR, a function ℝ^X → ℝ is defined so that it transforms an X\-dimensions covariate domain into a single output *g*(**x**) ∈ ℝ. In the context of classification, the system response is *y* ∈ {−1, +1}. Again, the idea with classification is to transform *g*(**x**)’s outputs into the (0, 1) interval describing the probability Pr(*Y* = +1|*x*). For GPC, the transformation in the interval (0, 1) is done using the standard Normal CDF presented in [figure 9.11](#chapter008.xhtml#Fig_9-11), where Φ(*z*) denotes the CDF of *Z* ~ N (*z*; 0, 1).

![art](images/Art_P758.jpg)

Figure 9.11: The standard Normal CDF, where Φ(*z*) denotes the CDF of *Z* ~ N (*z*; 0, 1).

Like the logistic sigmoid function presented in [§9.2](#chapter008.xhtml#Sec_9.2), Φ(*z*) is a transformation ℝ → (0, 1), such that an input defined in the real space is mapped in the interval (0, 1). Note that choosing the transformation function Φ(*z*) instead of the logistic function is not arbitrary; we will see later that it allows maintaining the analytic tractability of GPC. We saw in [§8.2](#chapter007.xhtml#Sec_8.2) that the function *g*(**x**[∗]), describing the system responses at prediction locations **x**[∗], is modeled by a Gaussian process,

![art](images/Art_P759.jpg)

In order to compute Pr(*Y* = +1|*x*[∗], D), that is, the probability that *Y* = +1 for a covariate *x*[∗] and a set of observations D, we need to transform *g*[∗] in the interval (0, 1) and then marginalize the uncertainty associated with *f*(*g*[∗]|*x*[∗], D) so that

![art](images/Art_P760.jpg)

If we choose the standard normal CDF, with Φ(*z*) as a transformation function, the integral in equation 9.2 follows the closed-form solution

![art](images/Art_P761.jpg)

where for the *i*^(th) prediction locations, ![art](images/Art_P762.jpg)and var\[*G*[∗]|*x*[∗], D\] ≡ \[Σ[∗|D]\]*[ii]*. [Figure 9.12](#chapter008.xhtml#Fig_9-12) illustrates how the uncertainty related to a Gaussian process evaluated through Φ(*G*(*x*)) is marginalized in order to describe Pr(*Y* = +1|*x*, D).

![art](images/Art_P763.jpg)

Figure 9.12: Example of Gaussian process *G*(*x*) evaluated through Φ(*G*(*x*)) and whose uncertainty is marginalized in order to describe Pr(*Y* = +1|*x*).

So far, we have seen how to employ the standard normal CDF to transform a Gaussian process *g*[∗] ∈ ℝ, with PDF *f*(*g*[∗]|*x*[∗], D) obtained from a set of observations D = {D[*x*], D*[y]*} = {(**x***[i], y[i]* ∈ ℝ), ∀*i* ∈ {1 : D}}, into a space Φ(*g*[∗]) ∈ (0, 1). The issue is that in a classification setup, *g*(*x*) is not directly observable; only *y[i]* ∈ {−1, +1} is. This requires inferring for each covariate *x* ∈ D*[x]* the mean and standard deviations for *latent* variables *G*(*x*). For that, we need to rewrite equation 9.3 in order to explicitly include the conditional dependence over g so that

**Note:** The qualification *latent* refers to variables that are not directly observed and that need to be inferred from observations of the classes *y* ∈ {−1, +1}.

![art](images/Art_P764.jpg)

For the *i*^(th) prediction locations, ![art](images/Art_P765.jpg)and var\[*G*[∗]|*x*[∗], **g**, D\] ≡ \[Σ[∗|**g**,D]\]*[ii]*, where

![art](images/Art_P766.jpg)

Equation 9.4 presents the posterior probability of the Gaussian process outcomes **g**[∗] at prediction location **x**[∗], given the data set D = {D*[x]*, D*[y]*} = {(**x***[i], y[i]* ∈ {−1, 1}), ∀*i* ∈ {1 : D}}, and the inferred values for **g** at observed locations **x**. The mean and covariance matrix for the PDF in equation 9.4 are, respectively,

![art](images/Art_P767.jpg)

**Note:** The prior mean for the Gaussian process at both observed *µ*[∗] and predicted *µ*[**G**] locations are assumed to be equal to zero.

where ***µ***[**G**|D] and Σ[**G**|D] are the mean vector and covariance matrix for the inferred latent observations of *G*(**x**) ~ *f*(**g**|D) = N (**g**; ***µ***[**G**|D], Σ[**G**|D]). The posterior PDF for inferred latent variables *G*(**x**) is

![art](images/Art_P768.jpg)

The first term corresponds to the joint likelihood of observations D[*y*] given the associated set of inferred latent variables **g**. With the assumption that observations are conditionally independent given *g[i]*, the joint likelihood is obtained from the product of the marginals so that

![art](images/Art_P769.jpg)

**Note:** Because of the symmetry in the standard normal CDF,

*p*(*y* = +1|*g*) = Φ(*g*) and

*p*(*y* = −1|*g*) = 1 − Φ(*g*) = Φ(*−g*).

It explains why the marginal likelihood simplifies to *p*(*y*|*g*) = Φ(*y* · *g*).

The second term in equation 9.5, *f*(**g**|D*[x]*) = N (**g**; *µ*[**G**] = **0**, Σ[G]) is the prior knowledge for the inferred latent variables *G*(**x**). The posterior mean of *f*(**g**|D), that is, ***µ***[**G**|D], is obtained by maximizing the logarithm of *f*(**g**|D) so that

![art](images/Art_P770.jpg)

**Note:** As detailed in [§ 8.2](#chapter007.xhtml#Sec_8.2), the prior covariance ![art](images/Art_P771.jpg)depends on the hyperparameters ***θ*** = {*σ[G], ℓ*}, which also need to be inferred from data.

 

The maximum **g**^∗ corresponds to the location where the derivative equals zero so that

![art](images/Art_P773.jpg)

By isolating **g** in equation 9.6, we can obtain optimal values **g**^∗ iteratively using

![art](images/Art_P774.jpg)

where the initial starting location can be taken as **g** = **0**. The uncertainty associated with the optimal set of inferred latent variables ***µ***[**G**|D] = **g**^∗ is estimated using the Laplace approximation (see [§6.7.2](#chapter005.xhtml#Sec_6.7.2)). The Laplace approximation for the covariance matrix corresponds to the inverse of the Hessian for the negative log-likelihood evaluated at ***µ***[**G**|D], so that

![art](images/Art_P775.jpg)

Note that we can improve the efficiency for computing the MLE in equation 9.8 by using the information contained in the Hessian as we did with the Newton-Raphson method in [§5.2](#chapter004.xhtml#Sec_5.2). In that case, optimal values **g**^∗ are obtained iteratively using

![art](images/Art_P776.jpg)

[Figure 9.13](#chapter008.xhtml#Fig_9-13) presents an application of GPC using the Gaussian process for machine learning (GPML) package with a different number of observations, D ∈ {25, 50, 100}. In this figure, the green solid lines on the horizontal planes describe the inferred confidence intervals for the latent variables, *µ[G|D] ±* 2*σ[G|D]*. We can see that as the number of observations increases, the inferred function Pr(*Y* = +1|*x*[∗], D) (orange solid line) tends toward the true function (orange dashed line).

![art](images/Art_P777.jpg)

Figure 9.13: Example of application of Gaussian process classification using the package GPML with a different number of observations D ∈ {25, 50, 100}.

[Figure 9.14](#chapter008.xhtml#Fig_9-14) presents the application of Gaussian process classification to the post-earthquake structural safety assessment example introduced in [§9.1.2](#chapter008.xhtml#Sec_9.1.2). Here, the multiclass problem is transformed into a binary one by modeling the probability that the damage index is either 0 or 1. The main advantage of GPC is that the problem setup is trivial when using existing, pre-implemented packages. With the generative approaches presented in [§9.1](#chapter008.xhtml#Sec_9.1), the formulation has to be specifically tailored for the problem. Nevertheless, note that a generative approach allows including censored data, whereas a discriminative approach such as the GPC presented here cannot.

![art](images/Art_P778.jpg)

Figure 9.14: Example of application of Gaussian process classification to the post-earthquake structural safety evaluation data set.

 

In practice, all the operations required to infer the latent variables G(x) as well as the parameter ***θ*** = {*σ[g], ℓ}* in GPC are already implemented in the same open-source packages dealing with GPR, for example, GPML, GPstuff, and pyGPs (see [§8.2](#chapter007.xhtml#Sec_8.2)).

*Strengths and limitations*   With the availability of Gaussian process classification implemented in a variety of open-source packages, the setup of a GPC problem is trivial, even for problems involving several covariates **x**. When the number of observations is small, the task of inferring latent variables g becomes increasingly difficult and the performance decreases. Note also that the formulation presented assumes that we only have error-free direct observations. Moreover, because of the computationally demanding procedure of inferring latent variables **g**, the performance is limited in the case of large data sets, for example, D > 10⁵. Given the limitations for both small and large data sets, the GPC presented here is thus best suited for medium-size data sets.

For more details about the Gaussian process classification and its extension to multiple classes, the reader should refer to dedicated publications such as the book by Rasmussen and Williams^([4](#chapter008.xhtml#footnote_4)) or the tutorial by Ebden.^([5](#chapter008.xhtml#footnote_5))

 

[*9.4   Neural Networks*](#toc.xhtml#Rh1-36)

The formulation for the feedforward neural network presented in [§8.3](#chapter007.xhtml#Sec_8.3) can be adapted for binary classification problems by replacing the linear output activation function by a *sigmoid* function as illustrated in [figure 9.15a](#chapter008.xhtml#Fig_9-15). For an observation *y* ∈ {−1, +1}, the log of the probability for the outcome *y[i]* = +1 is modeled as being *proportional* to the hidden variable on the output layer *z*^((O)), and the log of the probability for the outcome *y[i]* = −1 is assumed to be proportional to 0,

![art](images/Art_P779.jpg)

![art](images/Art_P783.jpg)

Figure 9.15: Nomenclature for a feedforward neural network employed for classification: (a) represents the case for binary classification *y* ∈ {−1, +1}; (b) the case for C classes *y* ∈ {1, 2, ⋯ , C}.

These unnormalized log-probabilities are transformed into a probability for each possible outcome by taking the exponential of each of them and then normalizing by following

![art](images/Art_P780.jpg)

 

As presented in [§8.3.1](#chapter007.xhtml#Sec_8.3.1), this procedure for normalizing the log-probabilities of *y* is equivalent to evaluating the hidden variable *z*^((O)) (or its negative) in the logistic sigmoid function. Thus, the likelihood of an observation *y* ∈ {−1, +1}, given its associated covariates x and a set of parameters ***θ*** = {***θ**[w]*, ***θ**[b]*}, is given by

*p*(*y*|**x**, ***θ***) = *σ*(*y* · *z*^((O))).

With neural networks, it is common to minimize a loss function *J*(D; ***θ**[w], **θ**[b]*) that is defined as the negative joint log-likelihood for a set of D observations,

![art](images/Art_P781.jpg)

In the case where the observed system responses can belong to multiple classes, *y* ∈ {1, 2, ⋯ , C}, the output layer needs to be modified to include as many hidden states as there are classes, ![art](images/Art_P782.jpg), as presented in [figure 9.15b](#chapter008.xhtml#Fig_9-15). The log-probability of an observation *y* = *k* is assumed to be proportional to the *k*^(th) hidden state *z[k]*,

![art](images/Art_P784.jpg)

The normalization of the log-probabilities is done using the *softmax* activation function, where the probability of an observation *y* = *k* is given by

![art](images/Art_P785.jpg)

By assuming that observations are conditionally independent from each other given **z**^((O)), the loss function for the entire data set is obtained as in [§8.3.2](#chapter007.xhtml#Sec_8.3.2) by summing the log-probabilities (i.e., the marginal log-likelihoods) for each observation,

![art](images/Art_P786.jpg)

Minimizing the loss function *J*(D; ***θ**[w], **θ**[b]*) defined in equation 9.9 corresponds to minimizing the *cross-entropy*. Cross-entropy is a concept from the field of *information theory*^([6](#chapter008.xhtml#footnote_6)) that measures the similarity between two probability distributions or mass functions.

**Note:** Given two PMFs, *p*(*x*) and *q*(*x*), the cross-entropy is defined as

![art](images/Art_P787.jpg)

Note that in the context of classification, the gradient ∇*σ*^O(*z*^((O))) in the *backpropagation* algorithm (see [§8.3.2](#chapter007.xhtml#Sec_8.3.2)) is no longer equal to one because of the sigmoid function. Moreover, like for the regression setup, a neural network classifier is best suited for problems with a large number of covariates and for which large data sets are available.

 

[*9.5   Regression versus Classification*](#toc.xhtml#Rh1-37)

Note that when the data and context allow for it, it can be preferable to formulate a problem using a *regression* approach rather than using *classification*. Take, for example, the soil contamination example presented in [§8.2.5](#chapter007.xhtml#Sec_8.2.5). The data set available describes the contaminant concentration *c[i]* measured at coordinates **l***[i]* = {*x[i], y[i], z[i]*}. Using regression to model this problem results in a function describing the PDF of contaminant concentration as a function of coordinates **l**, *f*(**c**|**l**, D). A classification setup would instead model the probability that the soil contamination exceeds an admissible value *c*[adm]., Pr(**C** ≥ *c*[adm.]|**l**, D). Here, the drawback of classification is that information is lost when transforming a continuous system response **C** into a categorical event {**C** ≥ *c*[adm].}. For the classification setup, the information available to build the model is whether the contaminant concentration is above (*c[i]* = +1) or below (*c[i]* = −1) the admissible concentration *c*[adm.] for multiple locations **l***[i]*. The issue with a classification approach is that because we work with categories, the information about how far or how close we are from the threshold *c*[adm.] is lost.

 

 

*Exercises*

 
| P9.1 || Explain the differences between generative and discriminative classification approaches. |
| --- | --- |
| P9.2 || Explain why it is easier for generative approaches to consider censored observations. |
| P9.3 || Explain the differences between naive Bayes, LDA, and QDA. |
| P9.4 || Explain the relation between linear regression and logistic regression. |
| P9.5 || Given a logistic regression model *σ*(*b*[0] + *b*[1]*x*), write the likelihood formulation for D = {(*x* = 3, *y* = +1), (*x* = 8, *y* = −1)}. |
| P9.6 || What are the parameters to infer in the context of logistic regression? |
| P9.7 || What are the parameters and hidden variables to infer in the context of Gaussian process classification? |
| P9.8 || Implement a generative classifier using Gaussian marginal PDFs and apply it to the data set D = {D[+1], D[−1]},

D[+1] = {**y** = +**1**, **x** = \[1.4 2.2 2.0 3.5 1.7 0.4 2.2 1.5 1.3 2.3 0.5 2.3\]^T}

D[−1] = {**y** = −**1**, **x** = \[6.1 2.9 3.9 5.5 3.4 4.4 2.3 5.9\]^T}.

 |
| P9.9 || Implement the logistic regression method and reproduce the results presented in [figure 9.10b](#chapter008.xhtml#Fig_9-10) using the data set D = {D[+1], D[−1]},

D[+1] = {**y** = +**1**, **x** = \[92.6 84.4 41.0 72.1\]^T}

D[−1] = {**y** = −**1**, **x** = \[23.6 22.9 21.0 42.9 0.2 11.2\]^T}.

 |
| P9.10 || Implement the Gaussian process classification method and reproduce the results presented in [figure 9.13a](#chapter008.xhtml#Fig_9-13) using the data set D = {D[+1], D[−1]},D[+1] = {**y** = +**1**, **x** = \[12.7 9.8 27.8 54.7 95.8 96.5 15.8 95.7 14.2 42.2 96.0 3.6\]^T}D[−1] = {**y** = −**1**, **x** = \[90.6 91.3 63.2 97.0 48.5 80.0 91.6 79.2 65.6 84.9 93.4 67.9 75.8\]^T} |

 

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter008.xhtml#footnote_ref_1) Ng, A. and M. Jordan (2002). On discriminative vs. generative classifiers: A comparison of logistic regression and naive Bayes. In *Advances in neural information processing systems*, Volume 14, pp. 841–848. MIT Press.

[²](#chapter008.xhtml#footnote_ref_2) Goulet, J.-A., C. Michel, and A. Der Kiureghian (2015). Data-driven post-earthquake rapid structural safety assessment. *Earthquake Engineering & Structural Dynamics 44* (4), 549–562.

[³](#chapter008.xhtml#footnote_ref_3) Ben-Akiva, M. E. and S. R. Lerman (1985). *Discrete choice analysis: Theory and application to travel demand*. MIT Press; and McFadden, D. (2001). Economic choices. *American Economic Review 91* (3), 351–378.

[⁴](#chapter008.xhtml#footnote_ref_4) Rasmussen, C. E. and C. K. Williams (2006). *Gaussian processes for machine learning*. MIT Press.

[⁵](#chapter008.xhtml#footnote_ref_5) Ebden, M. (2008, August). Gaussian processes: A quick introduction. *arXiv preprint (1505.02965)*.

[⁶](#chapter008.xhtml#footnote_ref_6) MacKay, D. J. C. (2003). *Information theory, inference, and learning algorithms*. Cambridge University Press.

 

[**Part IV**](#toc.xhtml#part-4)

[**Unsupervised Learning**](#toc.xhtml#part-4)

![art](images/Art_P788.jpg)

 

 

[*10*](#toc.xhtml#chap-9)

[*Clustering and Dimension Reduction*](#toc.xhtml#chap-9)

This chapter covers two key problems associated with *unsupervised learning*: *clustering* and *dimension reduction*. Clustering consists in discovering patterns or subgroups among a set of covariates. Clustering is considered *unsupervised learning* because the cluster indexes are not available to train a model; cluster indexes have to be learned from the observed covariates themselves. With dimension reduction, the goal is to identify a lower-dimensional subspace for a set of covariates, in which the data can be represented with a negligible loss of information. In this chapter, we will introduce two clustering methods, Gaussian mixture models and K-means, and a dimension reduction technique, that is, principal component analysis.

 

[*10.1   Clustering*](#toc.xhtml#Rh1-38)

[Figure 10.1](#chapter009.xhtml#Fig_10-1) presents the Old Faithful geyser data set^([1](#chapter009.xhtml#footnote_1)) where the covariates ![art](images/Art_P789.jpg)describe the eruption time and the time to the next eruption. [Figure 10.1](#chapter009.xhtml#Fig_10-1) displays two distinct behaviors: short eruptions with short times to the next ones and long eruptions with a long time to the next ones. The goal with clustering is to discover the existence of such an underlying structure in data.

![art](images/Art_P790.jpg)

Figure 10.1: Eruption durations and time between eruptions can be clustered into two groups.

Note that when working with data sets D = D*[x]* = {**x***[i]*, ∀*i* ∈ {1 : D}}, **x***[i]* ∈ ℝ^X, with covariates defined in three or fewer dimensions (X ≤ 3), it is then trivial to visually identify clusters. The interest of having clustering methods is in identifying patterns in cases where X > 3, such that the dimensionality of the data does not allow for a visual separation of clusters.

 

[*10.1.1   Gaussian Mixture Models*](#toc.xhtml#Rh2-56)

**Data**

![art](images/Art_P791.jpg)

**Gaussian mixture parameters**

![art](images/Art_P797.jpg)

Clustering can be formulated as the task of fitting a *Gaussian mixture* model (GMM), on a set of observed covariates. A Gaussian mixture distribution is defined as the sum of K Normal (i.e., Gaussian) probability density functions (PDFs), each weighted by a probability *p*(*k*), ∀*k* ∈ {1 : K}. The joint PDF for a Gaussian mixture is defined by

![art](images/Art_P792.jpg)

where ***θ*** = {(***µ**[k]*, **Σ***[k]*), ∀*k* ∈ {1 : K}} describes the PDF parameters. [Figure 10.2](#chapter009.xhtml#Fig_10-2) presents examples of 1-D and 2-D Gaussian mixture PDFs. The issue is that in practice, we do not know ***θ*** or *p*(*k*), so we have to learn P = {***θ***, *p*(*k*)} from D*[x]*. Given the hypothesis that D*[x]* contains observations that are conditionally independent given P, the joint likelihood defined from equation 10.1 is

![art](images/Art_P793.jpg)

and equivalently, the log-likelihood is

![art](images/Art_P794.jpg)

![art](images/Art_P795.jpg)

Figure 10.2: Examples of Gaussian mixture PDFs.

If we choose a maximum likelihood estimate (MLE) approach to estimate the parameters, their optimal values are defined as

![art](images/Art_P796.jpg)

When the optimization in equation 10.3 employs methods such as those presented in [chapter 5](#chapter004.xhtml), it is referred to as *hard clustering*. Hard clustering is a difficult task because of several issues such as the constraints on **Σ***[k]* that require it to be positive semi-definite (see [§3.3.5](#chapter002.xhtml#Sec_3.3.5)), and because of non-identifiability (see 6.3.4). *Soft clustering* solves these issues by employing the *expectation maximization* method to estimate **P^∗**.

*Expectation maximization*^([2](#chapter009.xhtml#footnote_2)) (EM) is an iterative method that allows identifying optimal parameters **P^∗** for problems involving *latent* (i.e., unobserved) variables. In the context of clustering, the latent variable is the unobserved cluster index *k*. If we could observe D = {D*[x]*, D*[k]*} = {(**x***[i]*, *k[i]*), ∀*i* ∈ {1 : D}}, the *complete data* log-likelihood for one observation (**x***[i]*, *k[i]*) would be

![art](images/Art_P798.jpg)

Because complete data is not available, EM identifies optimal parameters by maximizing the *expected complete data log-likelihood*, *Q*(P^((*t*)), P^((*t*−1))), which depends on the sets of parameters defined for two successive iterations, *t* − 1 and *t*. For a single observation **x***[i]*,

![art](images/Art_P799.jpg)

where *p*(*k*|**x***[i]*, P^((*t*−1))) is the posterior probability mass function (PMF) for the latent cluster labels *k* obtained at the previous iteration *t* − 1. This last quantity is referred to as the *responsibility* of a cluster *k*. For an entire data set D = {D*[x]*} = {**x***[i]*, ∀*i* ∈ {1 : D}}, the expected complete data log-likelihood is

![art](images/Art_P800.jpg)

The EM method identifies the optimal parameter values P^∗ from *Q*(P^((*t*)), P^((*t*−1))) by iteratively performing the *expectation* and *maximization* steps detailed below.

*Expectation step*   For an iteration *t*, the expectation step computes the probability ![art](images/Art_P801.jpg)that an observed covariate **x***[i]* is associated with the cluster *k*, given the parameters P^((*t*−1)) so that

![art](images/Art_P802.jpg)

The particularity of the expectation step is that the estimation of the responsibility ![art](images/Art_P803.jpg)in equation 10.4 employs the PDF parameters ![art](images/Art_P804.jpg)and the marginal PMF *p*^((*t*−1))(*k*) estimated at the previous iteration *t* − 1.

*Maximization step*   In the maximization step, the goal is to identify

![art](images/Art_P805.jpg)

 

where the optimization is broken into two parts. The PDF’s new set of optimal parameters ***θ***^((*t*)) is obtained through the maximization problem

![art](images/Art_P806.jpg)

where the maximum corresponds to the value ***θ*** such that the derivative of the function is zero,

![art](images/Art_P807.jpg)

By isolating the mean vector ![art](images/muparentk.jpg)and the covariance matrix ![art](images/sigmaparentk.jpg), the new estimates are

![art](images/Art_P808.jpg)

By taking the derivative of ln *Q*(P^((*t*)), P^((*t*−1))) with respect to *p*(*k*) and repeating the same procedure, the new marginal PMF for each cluster *k* is given by

![art](images/Art_P809.jpg)

In practice, the values ![art](images/muparen0k.jpg)are initialized randomly, ![art](images/Art_P810.jpg)is taken as a diagonal matrix, and *p*^((0))(*k*) = 1/K is initially assumed to be equal for each cluster. [Algorithm 8](#chapter009.xhtml#Tab_8) summarizes the steps of the expectation maximization algorithm for estimating the parameters of a Gaussian mixture model.

[Figure 10.3](#chapter009.xhtml#Fig_10-3) presents the first two steps of the EM algorithm for a Gaussian mixture model applied to the Old Faithful example introduced in [figure 10.1](#chapter009.xhtml#Fig_10-1). At the first iteration *t* = 1, the two cluster centers ![art](images/muparen0k.jpg)as well as their covariances ![art](images/sigmaparen0k.jpg)are initialized randomly. In the expectation step, the cluster responsibility is estimated for each data point **x***[i]*. As depicted in [figure 10.3a](#chapter009.xhtml#Fig_10-3), a data point belongs to the cluster associated with the highest responsibility. At this point, due to the crude initialization of ![art](images/Art_P811.jpg), the quality of the cluster membership assignment is poor. The maximization step for *t* = 1 updates the initial cluster centers and covariances. The updated contours for the clusters using ![art](images/muparen1k.jpg)and ![art](images/sigmaparen1k.jpg)are depicted in [figure 10.3b](#chapter009.xhtml#Fig_10-3). Note that the responsibility for each data point **x***[i]* has not changed, so the cluster membership assignment remains the same. [Figure 10.3c](#chapter009.xhtml#Fig_10-3) presents the expectation step for the second iteration, where we can notice the change in cluster membership assignment in comparison with the previous steps in (a) and (b). In (d), the contours of each cluster are presented for parameters ![art](images/Art_P812.jpg), which have been updated for the second time. [Figure 10.4](#chapter009.xhtml#Fig_10-4) presents the final clusters along with their contours obtained after *t* = 12 iterations.

![art](images/Art_P813.jpg)

Figure 10.3: The first two iterations of the EM algorithm for a Gaussian mixture model applied on the Old Faithful data.

![art](images/Art_P815.jpg)

Figure 10.4: Example of an application of a Gaussian mixture model to the Old Faithful geyser data set. Contours represent the clusters identified using the EM algorithm after *t* = 12 iterations.

**Algorithm 8:** EM for Gaussian mixture models

![art](images/Art_P814.jpg)

[Figure 10.5](#chapter009.xhtml#Fig_10-5) presents a second example of a Gaussian mixture model for K = 3 generic clusters. Note that despite the overlap between clusters, the method performed well because, like in the previous case, each cluster is well approximated by a multivariate Normal. Gaussian mixture models may display a poor performance when the clusters do not have ellipsoidal shapes. In such a case, we should resort to more advanced methods such as *spectral clustering*.^([3](#chapter009.xhtml#footnote_3)) Further details regarding the derivation and theoretical justification of the EM methods are presented by Murphy^([4](#chapter009.xhtml#footnote_4)) and Bishop.^([5](#chapter009.xhtml#footnote_5))

![art](images/Art_P816.jpg)

Figure 10.5: Example of an application of a Gaussian mixture model to overlapping clusters. Contours represent the clusters identified using the EM algorithm.

*Estimating the number of clusters*   In the previous examples, we have assumed that we knew the number of clusters K. In most practical applications, this is not the case and K must be estimated using methods such as cross-validation (see [§8.1.2](#chapter007.xhtml#Sec_8.1.2)) or Bayesian model selection (see [§6.8](#chapter005.xhtml#Sec_6.8)).

 

[*10.1.2   K-Means*](#toc.xhtml#Rh2-57)

*K-means*^([6](#chapter009.xhtml#footnote_6)) is one of the most widespread clustering methods due to its simplicity. It can be seen as a special case of the Gaussian mixture model presented in [§10.1.1](#chapter009.xhtml#Sec_10.1.1), where the probability of each cluster is *p*(*k*) = 1/K, the covariance of each cluster is diagonal **Σ***[k]* = *σ*²**I**, and we seek to infer the cluster means ***µ**[k]* ∈ ℝ^X. With Gaussian mixture models, we were computing the probability that the covariates **x***[i]* belong to the cluster *k*; with K-means, the cluster membership assignment ![art](images/kasti.jpg)for a covariate **x***[i]* is deterministic so that it corresponds to

![art](images/Art_P817.jpg)

where a covariate **x***[i]* is assigned to the cluster associated with the mean it is the closest to,

![art](images/Art_P818.jpg)

The mean vector for the *k*^(th) cluster is estimated as the average location of the covariates **x***[i]* associated with a cluster *k* so that

![art](images/Art_P819.jpg)

where ![art](images/Art_P820.jpg)is the number of observed covariates assigned to the cluster *k*.

The general procedure consists in initializing ![art](images/muparen0k.jpg)randomly, iteratively assigning each observation to the cluster it is the closest to, and recomputing the mean of each cluster. [Figure 10.6](#chapter009.xhtml#Fig_10-6) presents in (a) the true cluster and in (b) the cluster membership assignment computed using K-means, where the mean of each cluster is presented by a cross. Note that because clusters are assumed to be spherical (i.e., **Σ***[k]* = *σ*²**I**), the cluster membership assignment is only based on the Euclidian distance between a covariate and the center of each cluster. This explains why in [figure 10.6b](#chapter009.xhtml#Fig_10-6) several observed covariates are assigned to the wrong cluster. [Algorithm 9](#chapter009.xhtml#Tab_9) summarizes the steps for K-means clustering.

![art](images/Art_P821.jpg)

Figure 10.6: Example of application of K-means. Notice how some samples were misclassified due to the hypothesis related to the circular shape of each cluster, that is, **Σ***[k]* = *σ*²**I**.

**Algorithm 9:** K-means

![art](images/Art_P822.jpg)

 

[*10.2   Principal Component Analysis*](#toc.xhtml#Rh1-39)

*Principal component analysis* (PCA)^([7](#chapter009.xhtml#footnote_7)) is a dimension reduction technique often employed in conjunction with clustering. The goal of PCA is to transform the covariate space in a new set of orthogonal axes for which the variance is maximized for the first dimension. Note that in order to perform PCA, we must work with normalized data with mean zero and with variance equal to one for each covariate.

Let us assume, our observations consist of a set of raw unnormalized covariates D = {**x***[i]*, ∀*i* ∈ {1 : D}}, where ![art](images/Art_P823.jpg). We normalize each value *x[ij]* = \[**x***[i]*\]*[j]* in this data set by subtracting from it the empirical average ![art](images/Art_P824.jpg)and dividing by the empirical standard deviation ![art](images/Art_P825.jpg)so that

![art](images/Art_P826.jpg)

From our set of normalized covariates ![art](images/Art_P827.jpg), we seek orthogonal vectors ***ν**[i]* ∈ ℝ^X, ∀*i* ∈ {1 : X} so that our transformation matrix,

![art](images/Art_P828.jpg)

is orthonormal, that is, **V^TV** = **I**. We can transform the covariates ![art](images/xtildei.jpg)into the new space using ![art](images/Art_P829.jpg). The transformed data is then referred to as the *score*. Here, we want to find the orthogonal transformation matrix **V** that minimizes the reconstruction error

![art](images/Art_P830.jpg)

The optimal solution minimizing *J*(**V**) is obtained by taking **V** as the matrix containing the eigenvectors (see [§2.4.2](#chapter001.xhtml#Sec_2.4.2)) from the empirical covariance matrix estimated from the set of normalized covariates,

![art](images/Art_P831.jpg)

With PCA, the eigenvectors ***ν**[i]* in **V** are sorted according to the decreasing order of its associated eigenvalues. PCA finds a new set of orthogonal reference axes so that the variance for the first principal component is maximized in the transformed space. This explains why we need to work with normalized data so that the variance is similar for each dimension in the original space. If it is not the case, PCA will identify a transformation that is biased by the difference in the scale or the units of covariates. Note that an alternative to performing principal component analysis using the eigen decomposition is to employ the *singular value decomposition*^([8](#chapter009.xhtml#footnote_8)) procedure.

[Figure 10.7](#chapter009.xhtml#Fig_10-7) presents a PCA transformation applied to the Old Faithful geyser example. In (a), the data is normalized by subtracting the empirical average and dividing by the empirical standard deviation for each covariate. We then obtain the PCA transformation matrix by performing the eigen decomposition of the empirical covariance matrix estimated from normalized covariates,

![art](images/Art_P832.jpg)

![art](images/Art_P833.jpg)

Figure 10.7: Example of application of principal component analysis to the normalized and centered Old Faithful data set.

We can see in [figure 10.7b](#chapter009.xhtml#Fig_10-7) that when transformed in the PCA space, the variance is maximized along the first principal component.

*Fraction of the variance explained*   In the PCA space, the eigenvalues describe the variance associated with each principal component. The fraction of the variance explained by each principal component I is quantified by the ratio of the eigenvalue associated with the *i*^(th) component divided by the sum of eigenvalues,

![art](images/Art_P834.jpg)

In the example presented in [figure 10.7](#chapter009.xhtml#Fig_10-7), the fraction of the variance explained by each principal component is I = {0.9504, 0.0496}.

 

*Dimension reduction*   PCA can be employed to reduce the number of dimensions describing the covariate space. This is achieved by removing the eigenvectors, that is, columns from the matrix **V**, that are associated with a negligible fraction of the variance explained. [Figure 10.8a](#chapter009.xhtml#Fig_10-8) presents the example of a data set with K = 3 clusters and where covariates **x***[i]* ∈ ℝ³. In [figure 10.8b](#chapter009.xhtml#Fig_10-8), we see clusters identified using the K-means algorithm. By performing PCA on the normalized and centered data, we find the transformation matrix

![art](images/Art_P835.jpg)

where the fraction of the variance explained by each principal component is I = {85.5, 14.2, 0.3}. We can see here that the third principal component explains a negligible fraction of the variance. This indicates that the original data set defined in a 3-D space can be represented in a 2-D space with a negligible loss of information. Such a 2-D space is obtained by removing the last column from the original PCA matrix,

![art](images/Art_P836.jpg)

and then performing the transformation ![art](images/Art_P837.jpg). [Figure 10.8c](#chapter009.xhtml#Fig_10-8) presents K-means clusters for the covariates transformed in the 2-D PCA space, **z***[i]* ∈ ℝ².

![art](images/Art_P838.jpg)

Figure 10.8: Example of application of the principal component analysis for dimensionality reduction.

Note that principal component analysis is limited to linear dimensional reduction. For nonlinear cases, we can opt for more advanced methods such as *t-distributed stochastic neighbor embedding* (t-SNE).^([9](#chapter009.xhtml#footnote_9)) In addition to being employed in unsupervised learning, PCA and other dimensionality reduction techniques can be employed in the context of regression and classification (see [chapters 8](#chapter007.xhtml) and [9](#chapter008.xhtml)). In such a case, instead of modeling the relationship between the observed system responses and the covariates, the relationship is modeled between the observed system responses and the transformed covariates represented in a lower-dimensional space where inter-covariate dependence is removed using PCA or any other dimension-reduction technique.

 

 

*Exercises*

| P10.1 || Explain what makes clustering different from classification. |
| --- | --- |
| P10.2 || Explain why the expectation maximization algorithm is needed for estimating the parameters of a Gaussian mixture model. |
| P10.3 || Explain the relations between K-means and Gaussian mixture models. |
| P10.4 || Implement the K-mean algorithm and apply it to the Old Faithful geyser data set. Compare your result with [figure 10.1b](#chapter009.xhtml#Fig_10-1). |
| P10.5 || Implement a Gaussian mixture model with the EM algorithm and apply it to the Old Faithful geyser data set. Compare your result with [figure 10.1b](#chapter009.xhtml#Fig_10-1). |
| P10.6 || Use principal component analysis to reproduce the results presented in [figure 10.7b](#chapter009.xhtml#Fig_10-7). |

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter009.xhtml#footnote_ref_1) Adelchi, A. and A. W. Bowman (1990). A look at some data on the Old Faithful geyser. *Journal of the Royal Statistical Society. Series C (Applied Statistics) 39*(3), 357–365.

[²](#chapter009.xhtml#footnote_ref_2) Dempster, A. P., N. M. Laird, and D. B. Rubin (1977). Maximum likelihood from incomplete data via the EM algorithm. *Journal of the Royal Statistical Society. Series B (methodological) 39*(1), 1–38.

[³](#chapter009.xhtml#footnote_ref_3) Ng, A., M. Jordan, and Y. Weiss (2002). On spectral clustering: Analysis and an algorithm. In *Advances in neural information processing systems*, Volume 14, pp. 849–856. MIT Press.

[⁴](#chapter009.xhtml#footnote_ref_4) Murphy, K. P. (2012). *Machine learning: A probabilistic perspective*. MIT Press.

[⁵](#chapter009.xhtml#footnote_ref_5) Bishop, C. M. (2006). *Pattern recognition and machine learning*. Springer.

[⁶](#chapter009.xhtml#footnote_ref_6) Lloyd, S. (1982). Least squares quantization in PCM. *IEEE Transactions on Information Theory 28*(2), 129–137.

[⁷](#chapter009.xhtml#footnote_ref_7) Hotelling, H. (1933). Analysis of a complex of statistical variables into principal components. *Journal of Educational Psychology 24*(6), 417.

[⁸](#chapter009.xhtml#footnote_ref_8) Van Loan, C. F. and G. H. Golub (1983). *Matrix computations*. Johns Hopkins University Press.

[⁹](#chapter009.xhtml#footnote_ref_9) Van der Maaten, L. and G. Hinton (2008). Visualizing data using t-SNE. *Journal of Machine Learning Research 9*, 2579–2605.

 

[*11*](#toc.xhtml#chap-10)

[*Bayesian Networks*](#toc.xhtml#chap-10)

Bayesian networks were introduced by Pearl^([1](#chapter010.xhtml#footnote_1)) and are also known as *belief networks* and *directed graphical models*. They are the result of the combination of *probability theory* covered in [chapter 3](#chapter002.xhtml) with *graph theory*, which employs graphs defined by links and nodes.

We saw in [§3.2](#chapter002.xhtml#Sec_3.2) that the *chain rule* allows formulating the joint probability for a set of random variables using conditional and marginal probabilities, for example, *p*(*x*[1], *x*[2], *x*[3]) = *p*(*x*[3]|*x*[2], *x*[1])*p*(*x*[2]|*x*[1])*p*(*x*[1]). Bayesian networks (BNs) employ *nodes* to represent random variables and *directed links* to describe the dependencies between them. Bayesian networks are probabilistic models where the goal is to learn the joint probability defined over the entire network. The joint probability for the structure encoded by these nodes and links is formulated using the *chain rule*. The key with Bayesian networks is that they allow building sparse models for which efficient variable elimination algorithms exist in order to estimate any conditional probabilities from the joint probability.

BNs can be categorized as *unsupervised learning*^([2](#chapter010.xhtml#footnote_2)) where the goal is to estimate the joint probability density function (PDF) for a set of observed variables. In its most general form we may seek to learn the structure of the BN itself. In this chapter, we restrict ourselves to the case where we know the graph structure, and the goal is to learn to predict unobserved quantities given some observed ones.

*Flu virus example*   [Section 3.3.5](#chapter002.xhtml#Sec_3.3.5) presented the distinction between *correlation* and *causality* using the flu virus example. A Bayesian network can be employed to model the dependence between the *temperature*, the presence of the flu *virus*, and being sick from the *flu*. We model our knowledge of these three quantities using discrete random variables that are represented by the nodes in [figure 11.1](#chapter010.xhtml#Fig_11-1). The arrows represent the dependencies between variables: The temperature *T* affects the virus prevalence *V*, which in turns affects the probability of catching the virus and being sick *F*. The absence of a link between *T* and *F* indicates that the temperature and being sick from the flu are *conditionally independent* from each other. In the context of this example, conditional independence implies that *T* and *F* are independent when *V* is known. The joint probability for *T*, *V*, and *F*,

![art](images/Art_P839.jpg)

**Virus example: Marginal and conditional probability tables**

![art](images/Art_P840.jpg)

is obtained using the chain rule where, for each arrow, the conditional probabilities are described in a *conditional probability table*.

![art](images/Art_P843.jpg)

Figure 11.1: Example of Bayesian network for representing the relationships between temperature, the presence of the flu virus, and being sick from the flu virus.

In the case where we observe *F* = *f*, we can employ the *marginalization* operation in order to obtain a conditional probability quantifying how the observation *f* ∈ {sick, ¬sick} changes the probability for the temperature *T*,

![art](images/Art_P844.jpg)

**Joint probability using chain rule**

![art](images/Art_P841.jpg)

**Variable elimination: Marginalization**

![art](images/Art_P842.jpg)

In minimalistic problems such as this one, it is trivial to calculate the joint probability using the chain rule and eliminating variables using marginalization. However, in practical cases involving dozens of variables with as many links between them, these calculations become computationally demanding. Moreover, in practice, we seldom know the marginal and conditional probabilities tables. A key interest of working with directed graphs is that efficient estimation methods are available to perform all those tasks.

Bayesian networks are applicable not only for discrete random variables but also for continuous ones, or a mix of both. In this chapter, we restrict ourselves to the study of BN for discrete random variables. Note that the state-space models presented in [chapter 12](#chapter011.xhtml) can be seen as a time-dependent Bayesian network using Gaussian random variables with linear dependence models. This chapter presents the nomenclature employed to define graphical models, the methods for performing inference, and the methods allowing us to learn the conditional probabilities defining the dependencies between random variables. In addition, we present an introduction to time-dependent Bayesian networks that are referred to as *dynamic Bayesian networks*. For advanced topics regarding Bayesian networks, the reader is invited to consult specialized textbooks such as the one by Nielsen and Jensen^([3](#chapter010.xhtml#footnote_3)) or Murphy’s PhD thesis.^([4](#chapter010.xhtml#footnote_4))

  

[*11.1   Graphical Models Nomenclature*](#toc.xhtml#Rh1-41)

Bayesian networks employ a special type of graph: *directed acyclic graph* (DAG). A DAG G = {U, E} is defined by a set of nodes U interconnected by a set of directed links E. In order to be acyclic, the directed links between variables cannot be defined such that there are self-loops or cycles in the graph. For a set of random variables, there are many ways to define links between variables, each one leading to the same joint probability. Note that directed links between variables *are not required to describe causal relationships*. Despite causality not being a requirement, it is a key to efficiency; if the directed links in a graphical model are assigned following the causal relationships, it generally produces sparse models requiring the definition of a smaller number of conditional probabilities than noncausal counterparts.

[Figure 11.2a](#chapter010.xhtml#Fig_11-2) presents a directed acyclic graph and (b) presents a directed graph containing a cycle so that it cannot be modeled as a Bayesian network. In [figure 11.2a](#chapter010.xhtml#Fig_11-2) random variables are represented by nodes, where the observed variable *X*[4] depends on the hidden variables *X*[2] and *X*[3]. The directions of links indicate that *X*[2] and *X*[3] are the *parent* of *X*[4], that is, parents(*X*[4]) = {*X*[2], *X*[3]}, and consequently, *X*[4] is the *child* of *X*[2] and *X*[3]. Each child is associated with a *conditional probability table* (CPT) whose size depends on the number of parents, *p*(*x[i]*|parents(*X[i]*)). Nodes without parents are described by their marginal prior probabilities *p*(*x[i]*). The joint PDF *p*(U) for the entire Bayesian network is formulated using the chain rule,

![art](images/Art_P845.jpg)

![art](images/Art_P846.jpg)

Figure 11.2: Example of dependence represented by directed links between hidden (white) and an observed (shaded) nodes describing random variables.

This application of the chain rule requires that given its parents, each node is independent of its other ancestors.

*Cyanobacteria example*   We explore the example illustrated in [figure 11.3](#chapter010.xhtml#Fig_11-3) of cyanobacteria blooms that can occur in lakes, rivers, and estuaries. Cyanobacteria blooms are typically caused by the use of fertilizers that wash into a water body, combined with warm temperatures that allow for bacteria reproduction. Cyanobacteria blooms can cause a change in the water color and can cause fish or marine life mortality. We employ a Bayesian network to describe the joint probability for a set of random variables consisting of the temperature *T*, the use of fertilizer *F*, the presence of cyanobacteria in water *C*, fish mortality *M*, and the water color *W*. In [figure 11.4](#chapter010.xhtml#Fig_11-4), the definition of the graph structure and its links follow the causal direction where the presence of cyanobacteria in water *C* depends on the temperature *T* and the presence of fertilizer *F*. Both the fish mortality *M* and water color *W* depend on the presence of cyanobacteria in water *C*.

![art](images/Art_P847.jpg)

Figure 11.3: Example of cyanobacteria bloom. (Photo: NASA and USGS)

![art](images/Art_P848.jpg)

Figure 11.4: Bayesian network for the cyanobacteria example.

 

[*11.2   Conditional Independence*](#toc.xhtml#Rh1-42)

As stated earlier, the absence of a link between two variables indicates that the pair is *conditionally independent*. In the case of a *serial connection*, as illustrated in [figure 11.5a](#chapter010.xhtml#Fig_11-5), the absence of a link between *A* and *C* indicates that these two are independent if *B* is known, that is, *A* ⊥ *C*|{*B* = *b*}. Therefore, as long as *B* is *not* observed, *A* and *C* depend on each other through *B*. It is equivalent to say that given its parent (i.e., *B*), *C* is independent of all its other non-descendants. In the case of a *diverging connection* ([figure 11.5b](#chapter010.xhtml#Fig_11-5)), again the absence of link between *A* and *C* indicates that these two are independent if *B* is observed. The case of a *converging connection* represented in [figure 11.5c](#chapter010.xhtml#Fig_11-5) is different from the two others; the absence of link between *A* and *C* implies that both variables are independent unless *B*, or one of its descendants, is observed. When *B*, or one of its descendants is observed, the knowledge gained for *B* also modifies the knowledge for *A* and *C*. We say that *A* and *C* are *d-separated* in the case of a serial or diverging connection, where the intermediary variable *B* is observed, or in the case of a converging connection, where neither the intermediary variable *B* nor one of its descendants is observed. For any *d*\-separated variables, a change in the knowledge for one variable does not affect the knowledge of the others.

![art](images/Art_P849.jpg)

Figure 11.5: Cases where *A* and *C* are conditionally independent for the different types of connection in Bayesian networks.

*Cyanobacteria example*   In the example presented in [figure 11.4b](#chapter010.xhtml#Fig_11-4), the sets of variables {*T*, *C*, *M*}, {*T*, *C*, *W*}, {*F*, *C*, *M*}, and {*F*, *C*, *W*} are all examples of serial connections. If as illustrated in [figure 11.6a](#chapter010.xhtml#Fig_11-6), we observe the presence of cyanobacteria, that is, *C* = yes, then the temperature *T* becomes independent of fish mortality *M* and water color *W*, that is, *T* ⊥ *M*|*c*, *T* ⊥ *W*|*c*. It implies that gaining knowledge about water temperature would not change our knowledge about either fish mortality or water color because these two quantities only depend on the presence of cyanobacteria, which is now a certainty given that *C* was observed. For the diverging connection between variables {*M*, *C*, *W*} illustrated in [figure 11.6b](#chapter010.xhtml#Fig_11-6), observing *C* = *c* causes the fish mortality *M* to be independent from the water color *W*, *M* ⊥ *W*|*c*. Gaining knowledge about the occurrence of fish mortality would not change our knowledge about water color because these two quantities only depend on the presence of cyanobacteria, which is a certainty when *C* is observed. For the converging connection between variables {*T*, *C*, *F*} represented in [figure 11.6c](#chapter010.xhtml#Fig_11-6), despite the absence of a link between *T* and *F*, the temperature is *not* independent from the use of fertilizer *F* if we observe *C* or one of its descendants, that is, *M* or *W*. Without observing *C*, *M*, or *W*, the knowledge gained about the use of fertilizer has no impact on our knowledge of the temperature. On the other hand, if we observe the presence of cyanobacteria (*C* = yes), then knowing that no fertilizer is present in the environment (*F* = no) would increase the probability that the temperature is high because there is only a small probability of having cyanobacteria without fertilizer and with cold temperature.

![art](images/Art_P850.jpg)

Figure 11.6: The concept of conditional independence illustrated using the cyanobacteria example.

 

[*11.3   Inference*](#toc.xhtml#Rh1-43)

**Cyanobacteria example**

![art](images/Art_P851.jpg)

**Cyanobacteria example: CPT**

![art](images/Art_P855.jpg)

The finality of Bayesian networks is not only to define the joint probability for random variables; it is to perform *inference*, that is, to compute the conditional probability for a set of unobserved random variables, given a set of observed ones. Let us consider U = {*X*[1], *X*[2], ⋯, *X*[X]}, the set of random variables corresponding to the nodes defining a system, a subset of *observed variables* D ⊂ U, and another subset of query variables Q ⊂ U, such that Q ∩ D = ∅. Following the definition of conditional probabilities presented in [§3.2](#chapter002.xhtml#Sec_3.2), the posterior probability for the variables in Q given observations D is

![art](images/Art_P852.jpg)

where U \\ {Q, D} describes the set of variables belonging to U while excluding those in {Q, D}. For the cyanobacteria example presented in [figure 11.4b](#chapter010.xhtml#Fig_11-4), let us consider we want the posterior probability *p*(*m*|*w* = green), that is, the probability of fish mortality *M* given that we have observed colored water, *W* = green. This joint probability is described by

![art](images/Art_P853.jpg)

 

where both terms on the right-hand side can be obtained through the marginalization of the joint probability mass function (PMF),

![art](images/Art_P854.jpg)

This approach is theoretically correct; however, in practice, calculating the joint probability *p*(U) quickly becomes computationally intractable with the increase in the number of variables in U. The solution is to avoid computing the full joint probability table and instead proceed by eliminating variables sequentially.

*Variable elimination*   The goal of *variable elimination* is to avoid computing the full joint probability table *p*(U) by working with its chain-rule factorization. For the cyanobacteria example, the joint probability is

![art](images/Art_P856.jpg)

where computing *p*(*m*, *w* = green) corresponds to

![art](images/Art_P859.jpg)

**Variable elimination**

![art](images/Art_P857.jpg)

**Inference**

![art](images/Art_P858.jpg)

Note how several terms in equation 11.1 are independent from the variables in the summation operators. It allows us to take out of the sums the terms that do not depend on them and then perform the marginalization sequentially. This procedure is more efficient than working with full probability tables. In the previous equation, braces refer to the ordering of operations and indicate the size of each probability table. The variable elimination procedure allows working with probability tables containing no more than 2³ = 8 entries. In comparison, the full joint probability table for *p*(U) contains 2⁵ = 32 entries.

The efficiency of the variable elimination approach depends on the ordering of operations. The common method for ordering operations while performing variable elimination is the *junction tree* method. This method transforms the graph into a tree and then employs clustering to group nodes. The reader interested in the details of this inference method should refer to specialized textbooks. Note that the methods covered above are *exact inference methods*. In the case where the number of variables is so large that exact methods become computationally prohibitive, we can also resort to approximate methods based on Monte Carlo sampling.

 

[*11.4   Conditional Probability Estimation*](#toc.xhtml#Rh1-44)

In the previous sections, it was always assumed that the probabilities contained in conditional probability tables (CPTs) were known. In practice this is seldom the case; CPTs must be learned from data. There are two typical learning setups; in the first setup, the Bayesian network is *fully observed* so each observation D*[i]* = {**x***[i]*} consists in a joint realization **x***[i]* : **X** ∼ *p*(U). [Figure 11.7a](#chapter010.xhtml#Fig_11-7) presents a table where each line is one observation for the fully observed BN employed in the cyanobacteria example. In the second learning setup, the BN is only *partially observed* so that some variables are not observed for the realization of **x***[i]* : **X** ∼ *p*(U). [Figure 11.7b](#chapter010.xhtml#Fig_11-7) presents a data set for the cyanobacteria example where the BN is partially observed.

![art](images/Art_P860.jpg)

Figure 11.7: Example of data set for learning conditional probability tables.

 

[*11.4.1   Fully Observed Bayesian Network*](#toc.xhtml#Rh2-58)

For a fully observed Bayesian network, the maximum likelihood estimate (MLE) for the conditional probability Pr(*X*[1] = *x*[1]|*X*[2] = *x*[2]) can be estimated as the ratio between the number of realizations of a specific joint outcome {*X*[1] = *x*[1], *X*[2] = *x*[2]}, divided by the total number of realizations of the outcome {*X*[2] = *x*[2]},

![art](images/Art_P861.jpg)

**Reminder:** #{ · } denotes the number of elements in a set.

We must be careful in the case where a specific outcome is not observed in the data set so #{*X*[1] = *x*[1], *X*[2] = *x*[2]} = 0. In such a case, the MLE will lead to a conditional probability equal to zero. This situation is problematic because we might not have observed this specific outcome yet, simply because the number of observations is too limited. A solution is to employ a maximum a-posteriori (MAP) estimation by adding one observation count to each possible outcome. Given that *x*[1] ∈ {1, 2, ⋯ *n*}, equation 11.2 becomes

![art](images/Art_P862.jpg)

*Cyanobacteria example*   From the data set D presented in [figure 11.7a](#chapter010.xhtml#Fig_11-7), we can estimate each CPT involved in the definition of *p*(U) in equation 11.1. For example, we might want to obtain the MLE estimate for the probability of having cyanobacteria given a hot temperature and the presence of fertilizer, *p*(*c* = yes|*t* = hot, *f* = yes). In such a case, we compute the number of realizations of {*c* = yes, *t* = hot, *f* = yes} in D, divided by the number of realizations of {*t* = hot, *f* = yes}. If we want to employ the MAP estimate instead of the MLE, we add one count to the numerator and two to the denominator so that

![art](images/Art_P863.jpg)

The same method applies for any entry in a conditional probability table. In the case of the estimation of marginal probabilities such as *p*(*t* = hot), the calculation simplifies to the number of events where {*t* = hot} divided by D + 2, the number of joint observations in the data set plus the number of possible outcomes for *t*,

![art](images/Art_P864.jpg)

Before going further, we will explore the theoretical justification for the MLE and MAP in equations 11.2 and 11.3. Let us consider the simplified case where a network is made from X random variables U = {**X**} = {\[*X*[1] *X*[2] ⋯ *X*[X]\]^(**T**)}, where *x[k]* ∈ {0, 1}, ∀*k* ∈ {1 : X}. Here, the definition of a specific structure for the network is not necessary; we simply assume that the network is structured as a DAG, so that for each *X[k]*, we have *p*(*x[k]*|parents(*X[k]*)). The quantity we seek to estimate from the data is the conditional probability *θ[k]* = *p*(*x[k]* = 1|parents(*X[k]*)), where because *x[k]* is a binary variable, we also have 1 − *θ[k]* = *p*(*x[k]* = 0|parents(*X[k]*)). We describe the prior probability for *θ[k]* by a Beta PDF (see [§4.3](#chapter003.xhtml#Sec_4.3)),

![art](images/Art_P865.jpg)

**Note:** We add +1 to the parameters of the Beta prior because without them,

![art](images/Art_P866.jpg)

which would lead to an MAP equal to

![art](images/Art_P867.jpg)

 

We have a data set

![art](images/Art_P868.jpg)

containing D realizations from the fully observed Bayesian network U. Here, we are interested in the probability of the joint realization of *X[k]* = 1, along with a specific combination of its parents, that is, parents(*X[k]*) ≡ **x**^(pa(*k*)). The number of such outcomes in the data set D is *α* = #{*x[k]* = 1, **x**^(pa(*k*))} ∈ {0, 1, ⋯ , D}. Analogously, the number of realizations in the data set of *X[k]* = 0 along with the same specific combination of its parents is *β* = #{*x[k]* = 0, **x**^(pa(*k*))} ∈ {0, 1, ⋯ , D}, and note that *α* + *β* = #{**x**^(pa(*k*))}. The posterior PDF *f*(*θ[k]*|D) is formulated following

![art](images/Art_P869.jpg)

We saw in [§6.3](#chapter005.xhtml#Sec_6.3) that it is the same value ![art](images/thetacirck.jpg)that maximizes either *f*(*θ[k]*|D) or ln *f*(*θ[k]*|D). Therefore, the log-posterior is formulated following

![art](images/Art_P870.jpg)

where products were replaced by sums. We saw in [§5.1](#chapter004.xhtml#Sec_5.1) that the MAP estimator ![art](images/thetacirck.jpg)corresponds to the location where the derivative of the log-posterior equals zero. The derivative of the log-posterior is given by

![art](images/Art_P871.jpg)

*α* = #{*x[k]* = 1, **x**^(pa(*k*))} ∈ {0, 1, ⋯ , D}

*β* = #{*x[k]* = 0, **x**^(pa(*k*))} ∈ {0, 1, ⋯ , D}

Note that when taking the derivative of ln *f*(*θ[k]*|D) with respect to *θ[k]*, the sum with respect to *i* simplifies to a single term involving the parameter *θ[k]* we are trying to estimate, that is, the conditional log-probability ![art](images/Art_P872.jpg). By setting the derivative ![art](images/Art_P873.jpg), we obtain the MAP estimator

![art](images/Art_P874.jpg)

When we employ the prior parameters *α*[0] = *β*[0] = 1, the MAP estimator simplifies to

![art](images/Art_P875.jpg)

which is analogous to the formulation given in equation 11.3. If instead of having a binary state *x[k]* ∈ {0, 1} we have *x[k]* ∈ {0, 1, ⋯ , *n*}, then the prior PDF is a Dirichlet distribution, and the same principles apply for the derivation of the MAP estimator.

The Dirichlet distribution is a generalization of the Beta distribution for multivariate domains.

 

[*11.4.2   Partially Observed Bayesian Network*](#toc.xhtml#Rh2-59)

It is common in practice not to be able to observe every variable in a Bayesian network. In such a case, the method presented for a fully observed BN is not directly applicable, and we can resort to the *expectation maximization* (EM) method^([5](#chapter010.xhtml#footnote_5)) (see [§10.1.1](#chapter009.xhtml#Sec_10.1.1)). The EM method consists in repeating two steps recursively until convergence: in the *expectation step*, we employ the current values contained in the conditional probability tables, along with the inference procedure presented in [§11.3](#chapter010.xhtml#Sec_11.3) in order to replace observation counts by the expected number of observation counts. Take the cyanobacteria example, where we want to estimate *p*(*c* = yes|*t* = hot, *f* = yes) from a partially observed Bayesian network. We need to replace the explicit number of realizations #{*c* = yes, *t* = hot, *f* = yes} in equation 11.4 by the *expected number of counts*,

![art](images/Art_P876.jpg)

For the first observation D[1] = {**x**[1]} = {cold, ![art](images/boxquestion.jpg), yes, ![art](images/boxquestion.jpg), clear} contained in the data set presented in [figure 11.8](#chapter010.xhtml#Fig_11-8), the conditional probability equals zero because the event where the temperature is *t* = hot is impossible because we already know for this observation that the temperature is *t* = cold,

*p*(*c* = yes, *t* = hot, *f* =s yes|D[1]) = 0.

![art](images/Art_P877.jpg)

Figure 11.8: Example of partially observed Bayesian network for the cyanobacteria data set.

 

For the second observation D[2] = {**x**[2]} = {![art](images/boxquestion.jpg), ![art](images/boxquestion.jpg), yes, yes, clear}, the joint probability to be inferred using the procedure presented in [§11.3](#chapter010.xhtml#Sec_11.3) and the current values contained in the CPTs is

*p*(*c* = yes, *t* = hot, *f* = yes|D[2]) = *p*(*t* = hot, *f* = yes|*c* = yes, *m* = yes, *w* = clear) ∈ (0, 1).

In the case where no variables are missing for an observation, as in the fourth observation D[4], then

*p*(*c* = yes, *t* = hot, *f* = yes|D[4]) = 1.

Once the expectation procedure is completed for all observations in D, the *maximization step* consists in computing either the MLE or MAP for updating the probabilities contained in CPTs. The maximization step employs the method presented in [§11.4.1](#chapter010.xhtml#Sec_11.4.1) for fully observed Bayesian networks, this time using the expected number of counts, for example,

![art](images/Art_P878.jpg)

The expectation maximization method is intrinsically iterative, whereas the expectation step employs the CPT entries found at the last iteration during the maximization step. Both steps are repeated until a steady solution is reached.

 

[*11.5   Dynamic Bayesian Network*](#toc.xhtml#Rh1-45)

So far we have looked at Bayesian networks for modeling static systems that do not have a temporal component. When a BN is defined over time steps, we call it a *dynamic Bayesian network* (DBN). Just like for Bayesian networks, the dependence between variables is described by directed links and conditional probability tables; the same holds for the dependence between variables over successive time steps. [Figure 11.9a](#chapter010.xhtml#Fig_11-9) presents the expanded representation of a dynamic Bayesian network, where pairs of hidden states *X*[*t*−1] and *X[t]* are linked by an arrow that points in the direction of time. [Figure 11.9b](#chapter010.xhtml#Fig_11-9) represents the same network using a compact notation where the representation of the same state at different time steps is replaced by a single state *X[t]* with the double arrows indicating the links between different time steps. [Figure 11.10](#chapter010.xhtml#Fig_11-10) shows how the notion of time could be introduced in the cyanobacteria example where the double self-loop arrows indicate the presence of links between these variables over subsequent time steps.

![art](images/Art_P879.jpg)

Figure 11.9: Equivalent expanded and compact representations of a dynamic Bayesian network. In (b), the double-lined arrow represents the conditional relationship between time steps.

![art](images/Art_P880.jpg)

Figure 11.10: Dynamic Bayesian network for the cyanobacteria example.

For DBNs, we can apply the same *conditional probability estimation* methods we presented for Bayesian networks in [§11.4](#chapter010.xhtml#Sec_11.4). In the case of inference, specialized algorithms are available to perform variable elimination for DBN. The details for such algorithms can be found in dedicated literature.^([6](#chapter010.xhtml#footnote_6))

*Hidden Markov models*   Note that the dynamic Bayesian network presented in [figure 11.9](#chapter010.xhtml#Fig_11-9) represents a special case called a *hidden Markov model* (HMM). An HMM has only one *hidden-state variable* at each time *t* along with one observed variable. The model is *Markovian* because the future (*X*[*t*+1]) is independent of the past (*X*[*t*−1]) given the present (*X[t]*), that is, *X*[*t*+1] ⊥ *X*[*t*−1]|*x[t]*. The HMM model is thus defined by an *observation model p*(*y[t]*|*x[t]*) and a *transition model p*(*x*[*t*+1]|*x[t]*). The fire alarm example presented in [§6.2.2](#chapter005.xhtml#Sec_6.2.2) can be described by a hidden Markov model. The reader interested in specialized inference algorithms for HMM should refer to dedicated literature. In this book we will instead focus our attention on the case of a dynamic Bayesian network using continuous state variables, that is, *state-space models*. These models are described at length in the next chapter. The reader interested about the relationships between Bayesian networks, HMM, state-space models, and the Markov decision process (see [chapter 15](#chapter014.xhtml)) should consult the papers by Diard, Bessière and Mazer;^([7](#chapter010.xhtml#footnote_7)) and Ghahramani.^([8](#chapter010.xhtml#footnote_8))

 

 

*Exercises*

 
| P11.1 || Explain the notion of conditional independence. |
| --- | --- |
| P11.2 || Explain the notion of *d*\-separation in the context of Bayesian networks. |
| P11.3 || Explain what a directed acyclic graph is. |
| P11.4 || Explain how the expectation maximization algorithm is employed to learn the conditional probability tables in partially observed Bayesian networks. |
| P11.5 || For the cyanobacteria example presented in [figure 11.4](#chapter010.xhtml#Fig_11-4), use variable elimination to compute *p*(*w* = green|*m* = no), the conditional probability of having green water given that there is no fish mortality. |

 

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter010.xhtml#footnote_ref_1) Pearl, J. (1988). *Probabilistic reasoning in intelligent systems: Networks of plausible inference*. Morgan Kaufmann.

[²](#chapter010.xhtml#footnote_ref_2) Ghahramani, Z. (2004). Unsupervised learning. In *Advanced lectures on machine learning*, Volume 3176, pp. 72–112. Springer.

[³](#chapter010.xhtml#footnote_ref_3) Nielsen, T. D. and F. V. Jensen (2007). *Bayesian networks and decision graphs*. Springer.

[⁴](#chapter010.xhtml#footnote_ref_4) Murphy, K. P. (2002). *Dynamic Bayesian networks: representation, inference and learning*. PhD thesis, University of California, Berkeley.

[⁵](#chapter010.xhtml#footnote_ref_5) **Note:** Here, we need to satisfy a key hypothesis; the underlying process controlling whether a data *x[i]* is available or missing must be independent of its actual value so that we can say that data is *missing at random*. For the cyanobacteria example, the hypothesis of *independence for the missing data* would not be satisfied if, for example, experimentalists were reluctant to go and collect samples when the water temperature is *T* = cold.

[⁶](#chapter010.xhtml#footnote_ref_6) Murphy, K. P. (2002). *Dynamic Bayesian networks: representation, inference and learning*. PhD thesis, University of California, Berkeley.

[⁷](#chapter010.xhtml#footnote_ref_7) Diard, J., P. Bessiere, and E. Mazer (2003). A survey of probabilistic models using the Bayesian programming methodology as a unifying framework. In *International Conference on Computational Intelligence, Robotics and Autonomous Systems (IEEE-CIRAS)*, Singapore.

[⁸](#chapter010.xhtml#footnote_ref_8) Ghahramani, Z. (2001). An introduction to hidden Markov models and Bayesian networks. *International Journal of Pattern Recognition and Artificial Intelligence 15*(1), 9–42.

 

[*12*](#toc.xhtml#chap-11)

[*State-Space Models*](#toc.xhtml#chap-11)

State-space models are suited to analyze time-series data. In [chapter 8](#chapter007.xhtml), we saw that it is possible to model time series using *regression* methods (e.g., see [figure 8.30](#chapter007.xhtml#Fig_8-30)). Regression is suited for modeling time series displaying a *stationary* or *trend-stationary* baseline on which is added recurrent patterns, as displayed in [figures 12.1a–b](#chapter011.xhtml#Fig_12-1). In the case of a time series consisting in nonstationary processes such as the one in [figure 12.1c](#chapter011.xhtml#Fig_12-1), regression methods typically have a limited predictive capacity when extrapolating beyond the cases covered in the training set.

**Note:** A time series or process is said to be *stationary* when its statistical properties, such as its mean and variance, are constant through time, as illustrated in [figure 12.1d](#chapter011.xhtml#Fig_12-1). A time series is said to be *trend-stationary* if the trend (linear or not) can be removed from it.

![art](images/Art_P881.jpg)

Figure 12.1: The concept of time-series stationarity.

State-space models (SSM) analyze time series in a different way than regression models do. Regression is used in a supervised setup in order to describe the dependence between system responses and covariates, whereas in the case of time series, the covariates are related to time. On the other hand, *state-space models* bears that name because it uses a *dynamic model* to describe the dependence between the *hidden states* of a system at subsequent time steps. Take, for example, the task illustrated in [figure 12.2](#chapter011.xhtml#Fig_12-2) of predicting the landing location of a projectile; using kinematic equations, we can derive a linear model of the projectile position at time *t*[0] + ∆*t*, from the initial position *x*[0], the initial velocity *ẋ*[0], and the exit angle *θ*[0]. This task is not well suited for regression methods, yet it can easily be formulated as an SSM because there is a kinematic model available for describing the dependence between the hidden states at a time *t* and *t* + ∆*t*. SSM is a probabilistic method where, given a model’s structure, the task is to learn how to predict the hidden-state variables **x**[*t*+1] given the current knowledge for **x***[t]*. State-space models can be classified as *unsupervised learning* because it builds a joint probability density for a set of hidden-state variables while most of them are typically never observed.

![art](images/Art_P882.jpg)

Figure 12.2: A cannon-man trajectory can be described using the kinematics equations

![art](images/Art_P883.jpg)

where ![art](images/Art_P884.jpg)is a perturbation in the trajectory.

In the context of civil engineering we can, for example, use SSMs for modeling the degradation of infrastructures over time. As illustrated in [figure 12.3](#chapter011.xhtml#Fig_12-3), we employ the state variable *x* to describe the condition of a structure. Starting from a known initial condition *x*[0], we may develop a dynamic model *f*(*x*[1]|*x*[0]), similar to the one in the projectile example, in order to describe the kinematic process behind degradation. Because our model will inevitably be an approximation of the real degradation kinematics, we will recursively update our predictions using observations *y[t]* as they become available. The theory presented in this chapter allows combining probabilistically the information contained in the prior knowledge *f*(*x*[*t*−1]), the model *f*(*x[t]*|*x*[*t*−1]), and the observation *y[t]*, in order to obtain a posterior estimate *f*(*x[t]*|*y*[1], ⋯ , *y[t]*). The procedure is employed recursively to go from a time step *t* − 1 to *t*.

![art](images/Art_P885.jpg)

Figure 12.3: Example of state-space model where the state *x[t]* at a time *t* is estimated from the combination of an observation *y[t]*, a dynamic model describing the conditional probability *f*(*x[t]*|*x*[*t*−1]), and the prior knowledge for *x*[*t*−1].

SSMs allow performing several tasks such as removing (i.e., filtering) the observation errors, forecasting future states, and estimating *hidden states* that are not directly observable. For example, in the infrastructure degradation example, even if only the condition *x[t]* is observed, an SSM allows estimating two additional *hidden states*: the degradation speed *ẋ[t]* and its acceleration *ẍ[t]*. State-space models take their origin from the field of *control theory*, where the breakthrough application of the method was the guiding system for the *Apollo mission* in the 1960s (see [figure 12.4](#chapter011.xhtml#Fig_12-4)).

![art](images/Art_P886.jpg)

Figure 12.4: Apollo mission service module. (Photo: NASA)

 

[*12.1   Linear Gaussian State-Space Models*](#toc.xhtml#Rh1-47)

We can describe the mathematical formulation for SSMs using the same theory we covered in [§3.4.1](#chapter002.xhtml#Sec_3.4.1), for the linear functions of random variables, and in [§4.1.3](#chapter003.xhtml#Sec_4.1.3), where we explored the analytic formulation of the multivariate Normal conditional probability density function (PDF). Let us consider a linear model **Y** = **AX** + **b**, where **X** ∼ N(**x**; ***µ*[X]**, **Σ[X]**), and a vector of observations **y**. We saw in [§3.4.1](#chapter002.xhtml#Sec_3.4.1) that the output for linear functions of Normal random variables is also Normal,

![art](images/Art_P887.jpg)

In [§3.4.1](#chapter002.xhtml#Sec_3.4.1), we saw that the conditional PDF of **X** given the observations **y** is obtained by dividing the joint PDF of **X** and **Y** by the PDF of **Y** evaluated for observations **y**,

![art](images/Art_P888.jpg)

 

where the conditional mean vector and covariance matrix are

![art](images/Art_P889.jpg)

 

[*12.1.1   Basic Problem Setup*](#toc.xhtml#Rh2-60)

We employ a basic setup involving a single hidden-state variable in order to illustrate how the notions of linear functions of random variables and the multivariate Normal conditional PDF are behind the state-space model theory. We use *t* ∈ {0, 1, ⋯ , T} to describe discrete time stamps, *x[t]* to describe a hidden state of a system at a time *t*, and *y[t]* to describe an imperfect observation of *x[t]*.

A hidden state *x[t]* is a deterministic, yet unknown, quantity.

*Observation and transition models*   The relation between an observation and a hidden state is described by the *observation model*,

![art](images/Art_P890.jpg)

We call the observation *y[t]* imperfect because what we observe is the true state contaminated by zero-mean Normal-distributed observation errors. *x[t]* is referred to as a hidden state because it is not directly observed; only *y[t]* is. The dynamic model describing the possible transitions between successive time steps from a state *x*[*t*−1] to *x[t]* is described by the *transition model*,

![art](images/Art_P891.jpg)

where *w[t]* is a zero-mean Normal-distributed model error describing the discrepancy between the reality and our idealized transition model. The transition model in equation 12.1 is *Markovian* (see [chapter 7](#chapter006.xhtml)) because a state *x[t]* only depends on the state *x*[*t*−1] and is thus independent of all previous states. This aspect is key in the computational efficiency of the method.

*Notation*   In order to keep the notation simple, we opt for compact abbreviations; a set of observations {*y*[1], *y*[2], ⋯ , *y[t]*} is described by *y*[1:*t*] and the posterior conditional expected value for *X[t]* given *y*[1:*t*], E\[*X[t]*|*y*[1:*t*]\], is summarized by *µ*[*t*|*t*]. For the subscript, [*t*|*t*], the first index refers to *X[t]* and the second to *y*[1:*t*]. Following the same notation, E\[*X[t]*|*y*[1:*t*−1]\] is equivalent to *µ*[*t*|*t*−1]. The posterior conditional variance for *X[t]* given *y*[1:*t*], var\[*X[t]*|*y*[1:*t*]\], is summarized by ![art](images/Art_P892.jpg).

**Notation**

 
| *y*[1:*t*] || ≡ || {*y*[1], *y*[2], ⋯ , *y[t]*} |
| --- | --- | --- |
| *µ*[*t*|*t*] || ≡ || E\[*X[t]*|*y*[1:*t*]\] |
| *µ*[*t*|*t*−1] || ≡ || E\[*X[t]*|*y*[1:*t*−1]\] |
| ![art](images/Art_P893.jpg) || ≡ || var\[*X[t]*|*y*[1:*t*]\] |

 

*Prediction step*   At time *t* = 0, only our prior knowledge E\[*X*[0]\] = *µ*[0] and ![art](images/Art_P894.jpg)are available. From our prior knowledge at *t* = 0, the transition model *x[t]* = *x*[*t*−1] + *w[t]*, and the observation model *y[t]* = *x[t]* + *v[t]*, we can compute our joint prior knowledge at *t* = 1 for *X*[1] and *Y*[1], *f*(*x*[1], *y*[1]) = N(\[*x*[1], *y*[1]\]^T; ***µ***, **Σ**), where the mean vector and covariance matrix are described by

![art](images/Art_P895.jpg)

**Note:** An absence of prior knowledge for *X*[0] can be described by var\[*X*[0]\] → ∞.

The expected value E\[*X*[1]\] and variance var\[*X*[1]\] are obtained by propagating the uncertainty associated with the prior knowledge for *X*[0] through the transition model (*x[t]* = *x*[*t*−1] + *w[t]*),

![art](images/Art_P896.jpg)

**Note:** We use the notation *µ*[1] and *σ*[1] rather than *µ*[1|0] and *σ*[1|0] because there is no observation at *t* = 0.

The expected value E\[*Y*[1]\] and variance var\[*Y*[1]\] are obtained by propagating the uncertainty associated with the prior knowledge for *X*[1] through the observation model (*y[t]* = *x[t]* + *v[t]*),

![art](images/Art_P897.jpg)

The covariance ![art](images/Art_P898.jpg)is equal to var\[*X*[1]\].

*Update step*   We can obtain the posterior knowledge at time *t* = 1 using

![art](images/Art_P899.jpg)

where the posterior mean and variance are

![art](images/Art_P900.jpg)

Note that the terms in equation 12.4 correspond to those defined in equations 12.2 and 12.3. The posterior *f*(*x*[1]|*y*[1]) contains the information coming from the prior knowledge at *t* = 0, the system dynamics described by the transition model, and the observation at time *t* = 1.

The prediction and update steps are now generalized to transition from *t* − 1 → *t*. From our posterior knowledge at *t* − 1, the transition model *x[t]* = *x*[*t*−1] + *w[t]*, and the observation model *y[t]* = *x[t]* + *v[t]*, we compute our joint prior knowledge at *t*, *f*(*x[t]*, *y[t]*|*y*[1:*t*−1]) = N(\[*x[t] y[t]*\]^T; ***µ***, **Σ**), where the mean and covariance are

![art](images/Art_P901.jpg)

Each term of the mean vector and covariance matrix is obtained following

![art](images/Art_P902.jpg)

**Note:** cov(*X[t], Y[t]*|*y*[1:*t*−1])

Following the covariance properties,

| cov(*X*[1] + *X*[2], *X*[3] + *X*[4])  || \= || cov(*X*[1],*X*[3]) |
| --- | --- | --- |
| ⋯ + cov(*X*[1],*X*[4]) |
| ⋯ + cov(*X*[2],*X*[3]) |
| ⋯ + cov(*X*[2],*X*[4]) |

therefore,

![art](images/Art_P903.jpg)

The posterior knowledge at *t* is given by

![art](images/Art_P904.jpg)

where posterior mean and variance are

![art](images/Art_P905.jpg)

The *marginal likelihood f*(*y[t]*|*y*[1:*t*−1]) describing the prior probability density of observing *y[t]* given all observations up to time *t* − 1 is given by

![art](images/Art_P906.jpg)

**Note:** *f*(*y[t]*|*y*[1:*t*−1]) ≡ *f*(*y[t]*|*y*[1:*t*−1]; ***θ***), that is, we can represent either implicitly or explicitly the dependency on the model parameters ***θ*** that enter in the definition of the transition and observation equations. See [§ 12.1.4](#chapter011.xhtml#Sec_12.1.4) for further details.

We refer to *f*(*y[t]*|*y*[1:*t*−1]) as the *marginal likelihood* because the hidden state *x[t]* was marginalized. In the case of the multivariate Normal, the solution to *∫ f*(*y[t]*, *x[t]*|*y*[1:*t*−1])*dx[t]* is analytically tractable; see [§ 4.1.3](#chapter003.xhtml#Sec_4.1.3).

*Example: Temperature time series*   We now look at an illustrative example where we apply the prediction and update steps recursively to estimate the temperature *x[t]* over a period of three hours using imprecise observations made every hour for *t* ∈ {1, 2, 3}. Our prior knowledge is described by E\[*X*[0]\] = 10°*C* and *σ*\[*X*[0]\] = 7°*C*. The transition and observation models are

![art](images/Art_P907.jpg)

Performing the prediction step from *t* = 0 → *t* = 1 leads to

![art](images/Art_P908.jpg)

At the time *t* = 1, the observed temperature is *y*[1] = 4.8, leading to a likelihood *f*(*y[t]*|*y*[1:*t*−1]) = 0.04. Performing the update step leads to

![art](images/Art_P909.jpg)

Following the Gaussian conditional example presented in [§4.1.4](#chapter003.xhtml#Sec_4.1.4), [figure 12.5a](#chapter011.xhtml#Fig_12-5) presents graphically each of the quantities associated with the prior knowledge at *t* = 1 obtained by propagating the knowledge of *X*[0] in the transition and observation models, the likelihood of *y[t]*, and the posterior knowledge. By repeating the same prediction and update steps for *t* = 2, where *y*[2] = 12.1, we obtain

![art](images/Art_P912.jpg)

Figure 12.5: Step-by-step probabilistic hidden-state estimation. Note that the pink curve overlaid on the surfaces describes either the joint or the conditional PDF evaluated for the observed value *y[t]*.

**Prediction step**

![art](images/Art_P910.jpg)

**Update step**

![art](images/Art_P911.jpg)

These results are illustrated in [figure 12.5b](#chapter011.xhtml#Fig_12-5). The details of subsequent steps are not presented because they consist in repeating recursively the same prediction and update steps. [Figure 12.5c](#chapter011.xhtml#Fig_12-5) shows how, in only three time steps, we went from a diffuse knowledge describing *X*[0] to a more precise estimate for *X*[2].

 

[*12.1.2   General Formulation*](#toc.xhtml#Rh2-61)

**Observation model**

![art](images/Art_P916.jpg)

**C**: Observation matrix

**R**: Observation errors covariance

**Transition model**

![art](images/Art_P917.jpg)

**A**: Transition matrix

**Q**: Transition errors covariance

We now extend the prediction and update steps with a formulation compatible with multiple hidden states. For example, consider the case where want to use a SSM to estimate the hidden states **x**[*t*] = \[*x[t] ẋ[t]*\]^T, that is, the temperature *x[t]* and its *rate of change ẋ[t]*. The observation model then becomes

![art](images/Art_P913.jpg)

where the *observation matrix* **C** = \[1 0\] indicates that an observation *y[t]* is a function of *x[t]* but not of the rate of change *ẋ[t]*. *v[t]* is a realization of an observation error ![art](images/Art_P914.jpg). In the general case, observation errors are described by a multivariate Normal random variable **V** ∼ N(**v**; **0**, **R**), where **R** is the covariance matrix. The transition model for the two hidden states is

![art](images/Art_P915.jpg)

where the transition matrix **A** describes the model kinematics and **w***[t]* are realizations of the model errors **W** ∼ N(**w**; **0**, **Q**) that affect each of the hidden states.

In the *prediction step*, we compute our prior knowledge at *t* from our posterior knowledge at *t* − 1, using the transition model and the observation model,

![art](images/Art_P918.jpg)

These terms are collectively describing our joint prior knowledge *f*(**x***[t]*, **y***[t]*|**y**[1:*t*−1]) = N(\[**x***[t]* **y***[t]*\]^T; ***µ***, **Σ**) with the mean vector and covariance matrix defined as

![art](images/Art_P919.jpg)

In the *update step*, the posterior knowledge is obtained using the conditional multivariate Normal PDF,

![art](images/Art_P920.jpg)

which is defined by its posterior mean vector and covariance matrix,

![art](images/Art_P921.jpg)

 

The posterior knowledge *f*(**x***[t]|***y**[1:*t*]) combines the information coming from the prior knowledge {***µ***[0], **Σ**[0]}, the sequence of observation y[1:*t*], and the system dynamics described by the transition model. Equations 12.5 and 12.6, obtained using the theory presented in [§3.4.1](#chapter002.xhtml#Sec_3.4.1) and [§4.1.3](#chapter003.xhtml#Sec_4.1.3) are referred to as the *Kalman filter*^([1](#chapter011.xhtml#footnote_1)) where they are reorganized as

**Prediction step**

 
| ***µ***[*t*|*t*−1] || \= || **A*µ***[*t*−1|*t*−1] || Prior mean |
| --- | --- | --- | --- |
| **Σ**[*t*|*t*−1] || \= || **AΣ**[*t*−1|*t*−1]**A**^T + **Q** || Prior covariance |

**Update step**

 
| *f*(**x***[t]*|**y**[1:*t*]) || \= || N(**x***[t]*; ***µ***[*t*|*t*], **Σ**[*t*|*t*]) ||  |
| --- | --- | --- | --- |
| ***µ***[*t*|*t*] || \= || ***µ***[*t*|*t*−1] + **K***[t]***r***[t]* || Posterior expected value |
| **Σ**[*t*|*t*] || \= || (**I** − **K***[t]***C**)**Σ**[*t*|*t*−1] || Posterior covariance |
| **r***[t]* || \= || **y***[t]* − **ŷ***[t]* || Innovation vector |
| **ŷ***[t]* || \= || **C*µ***[*t*|*t*−1] || Prediction observations vector |
| **K***[t]* || \= || ![art](images/Art_P922.jpg) || Kalman gain matrix |
| **G***[t]* || \= || **CΣ**[*t*|*t*−1]**C**^T + **R** || Innovation covariance matrix |

In the name *Kalman filter*, the term *filter* refers to the action of removing the observation errors from an observed time series. Filtering is an intrinsically recursive operation that is suited for applications where a flow of data can be continuously processed as it gets collected. Note that in the classic Kalman formulation,^([2](#chapter011.xhtml#footnote_2)) there are additional control terms for including the effect of external actions on the system. These terms are omitted here because, contrarily to the field of aerospace, where flaps, rudders, or trust vectors are employed to continuously modify the state (i.e., position, speed, and acceleration) of a vehicle traveling through space, civil systems seldom have the possibility of such direct control actions being applied to them.

*Example: Temperature time series*   We want to estimate **x**[*t*] = \[*x[t] ẋ[t]*\]^T, the temperature and its rate of change over a period of 5 hours using imprecise observations made every hour for *t* ∈ {1, 2, ⋯ , 5}. The observation and transition models are respectively

![art](images/Art_P923.jpg)

Our prior knowledge for the temperature is E\[*X*[0]\] = 10°*C*, *σ*\[*X*[0]\] = 2°*C*, and for the rate of change, E\[*Ẋ*[0]\] = −1°*C*, *σ*\[*Ẋ*[0]\] = 1.5°*C*. We assume that our knowledge for *X*[0] and *Ẋ*[0] is independent ![art](images/Art_P924.jpg), so the prior mean vector and covariance matrix are

![art](images/Art_P925.jpg)

The observation-errors standard deviation is *σ[V]* = 4°*C*. Model errors are defined by the covariance matrix **Q**, which describes the errors on the temperature estimate and its rate of change. We assume that these errors are caused by a constant acceleration that takes place during the interval ∆*t*, which is not accounted for in the model, that builds on the hypothesis of a constant speed and no acceleration. In order to define the covariance matrix **Q**, we need to define a new vector ![art](images/Art_P926.jpg)that describes a realization of **Z***[t]* ∼ N(**z***[t]*; **0**, **Σ***[Z]*), that is, the effect of a constant acceleration having a random magnitude such that **Z*[t]*** ⊥ **Z**[***t***+*i*], ∀*i* ≠ 0. As illustrated in [figure 12.6](#chapter011.xhtml#Fig_12-6), having a constant acceleration ![art](images/zdotdott.jpg)over a time step of length ∆*t* causes a change of ![art](images/Art_P927.jpg)in the trend (i.e., speed) and a change of ![art](images/Art_P928.jpg)in the level. We can express the errors caused by the constant acceleration in **z***[t]* in terms of our transition errors **w***[t]* as

![art](images/Art_P929.jpg)

where

![art](images/Art_P930.jpg)

![art](images/Art_P932.jpg)

Figure 12.6: The error caused on the level and the trend by a constant acceleration ![art](images/zdotdott_s.jpg)over a time step of length ∆*t*.

Therefore, the definition of the matrix **Q** for the transition errors **W***[t]* is

![art](images/Art_P931.jpg)

For further details regarding the derivation of the process noise covariance matrices, the reader should consult the textbook by Bar-Shalom, Li, and Kirubarajan.^([3](#chapter011.xhtml#footnote_3)) In this example, the noise parameter is equal to ![art](images/Art_P933.jpg)and ∆*t* = 1. [Figure 12.7](#chapter011.xhtml#Fig_12-7) presents the state estimates for the temperature and its rate of change along with the true values that were employed to generate simulated observations.

![art](images/Art_P934.jpg)

Figure 12.7: Example of hidden-state estimation for a constant-speed model.

  

[*12.1.3   Forecasting and Smoothing*](#toc.xhtml#Rh2-62)

The *filtering* method presented in the previous section estimates *f*(**x***[t]*|**y**[1:*t*]), that is, the posterior probability density of hidden states **x***[t]*, given all the observations up to time *t*. With this procedure, acquiring new data at a time *t* + 1 does not modify our knowledge about **x***[t]*. This second task of estimating the posterior probability of hidden states **x***[t]* given all the observations up to time T > *t*, *f*(**x***[t]*|**y**[1:T]), is referred to as *smoothing*. A third task consists in *forecasting* the hidden states **x**[*t*+*n*], *n* time steps in the future, given all the observations up to time *t*, that is, *f*(**x**[*t*+*n*]|**y**[1:*t*]). The three tasks of *filtering*, *smoothing*, and *forecasting* are illustrated schematically in [figure 12.8](#chapter011.xhtml#Fig_12-8).

![art](images/Art_P935.jpg)

Figure 12.8: Comparison of *filtering*, *smoothing*, and *forecasting*, where the blue region corresponds to the data employed to estimate *x[t]* or forecast *x*[*t*+*n*].

*Forecasting:*   *f*(**x**[*t*+*n*]|**y**[1:*t*]) In the context of SSMs, forecasting is trivial because it only involves recursively propagating the current knowledge ***µ***[*t*|*t*], **Σ**[*t*|*t*] at time *t* through the prediction step. In short, forecasting from a time *t* to *t* + 1 follows

![art](images/Art_P936.jpg)

Note that whenever *data is missing* at a given time step, only the prediction step is recursively applied until new data is obtained. Therefore, missing data is treated in the same way as forecasting using the transition model. This is an interesting feature for SSMs, which do not require any special treatment for cases where data is missing.

*Example: Temperature time series (continued)*   We build on the temperature estimation example presented in [figure 12.7](#chapter011.xhtml#Fig_12-7) to illustrate the concept of forecasting. The goal here is to forecast the temperature for five hours after the last time step for which data is available. The result is presented in [figure 12.9](#chapter011.xhtml#Fig_12-9). Note how, because no observation is available to update the predictions, the standard deviation of the estimated hidden states keeps increasing because at each time step, the model error covariance matrix **Q** is added recursively to the hidden-state covariance matrix.

![art](images/Art_P937.jpg)

Figure 12.9: Example of hidden-state forecast for a constant-speed model.

*Smoothing:*   *f*(**x***[t]*|**y**[1:T])  With smoothing, we perform the reverse process of updating the knowledge at a time *t*, using the knowledge at *t* + 1. Smoothing starts from the last time step T estimated using the filtering procedure described in [§12.1.2](#chapter011.xhtml#Sec_12.1.2) and moves recursively backward until the initial time step is reached. The information flow during filtering and smoothing is illustrated in [figure 12.10](#chapter011.xhtml#Fig_12-10). The posterior knowledge *f*(**x***[t]*|**y**[1:T]) combines the information coming from the prior knowledge {***µ***[0], **Σ**[0]}, the entire sequence of observation y[1:T], and the transition model. The smoothing procedure can be employed to learn initial hidden states {***µ***[0], **Σ**[0]} → {***µ***[0|T], **Σ**[0|T]}. Updating initial values using the smoother typically improves the model quality. The most common algorithm for performing smoothing is the *RTS Kalman smoother*,^([4](#chapter011.xhtml#footnote_4)) which is defined following

![art](images/Art_P938.jpg)

![art](images/Art_P939.jpg)

Figure 12.10: Information flow for the filtering and smoothing processes.

As illustrated in [figure 12.10](#chapter011.xhtml#Fig_12-10), the RTS Kalman smoother is performed iteratively starting from the Kalman filter step *t* = T − 1, where the mean vector ***µ***[*t*+1|T] = ***µ***[T|T] and covariance matrix **Σ**[*t*+1|T] = **Σ**[T|T] are already available from the last Kalman filter step.

*Example: Smoothing temperature estimates*   [Figure 12.11](#chapter011.xhtml#Fig_12-11) presents the RTS smoothing procedure applied to the temperature estimation example initially presented in [figure 12.5](#chapter011.xhtml#Fig_12-5). These results show how, between the filtering and smoothing procedures, the mean at *t* = 2 went from 8.6 to 8.4, and the variance from 4.2 to 1.8. The uncertainty is reduced with smoothing because the estimate var\[*X*[2|3]\] is based on one more data point than var\[*X*[2|2]\]. [Figure 12.11](#chapter011.xhtml#Fig_12-11) presents the entire smoothed estimate, which almost coincides with the true values and has a narrower uncertainty confidence region than the filtering estimates.

![art](images/Art_P940.jpg)

Figure 12.11: Comparison of filtering, smoothing, and the true states.

  

[*12.1.4   Parameter Estimation*](#toc.xhtml#Rh2-63)

The definition of matrices **A**, **C**, **Q**, and **R** involved in the observation and transition models requires estimating several parameters ***θ*** using observations D = {*y*[1:T]}. As for other methods presented in previous chapters, the posterior for parameters is

![art](images/Art_P941.jpg)

In this Bayesian formulation for estimating the posterior PDF for parameters, the key component is the marginal likelihood, *f*(D|*θ*) ≡ *f*(*y*[1:T]|*θ*). With the hypothesis that observations are conditionally independent given the states **x***[t]*, the joint marginal likelihood (i.e., the joint prior probability density of observations given a set of parameters) is

![art](images/Art_P942.jpg)

We refer to *f*(**y**[1:T]|***θ***) as the joint *marginal likelihood* because the hidden variables **x**[1:T] are marginalized. In the remainder of this chapter, for the sake of brevity, we use the term *likelihood* instead of *marginal likelihood*.

where the marginal prior probability of each observation is obtained using the filtering procedure,

*f*(**y***[t]*|**y**[1:*t*−1], ***θ***) = N(**y***[t]*; **C*µ***[*t*|*t*−1], **CΣ**[*t*|*t*−1]**C^T** + **R**).

The posterior *f*(***θ***|D) can be estimated using the sampling techniques^([5](#chapter011.xhtml#footnote_5)) presented in [chapter 7](#chapter006.xhtml). However, because evaluating *f*(**y**[1:T]|***θ***) can be computationally demanding, most practical applications found in the literature only employ the maximum likelihood estimate (MLE) rather than estimating the full posterior with a Bayesian approach. For an MLE, the optimal set of parameters is then defined as

![art](images/Art_P943.jpg)

where because often *f*(**y***[t]*|**y**[1:*t*−1], ***θ***) ≪ 1, the product of the marginals ![art](images/Art_P944.jpg)is sensitive to zero underflow issues. When the contrary happens, so that *f*(**y***[t]*|**y**[1:*t*−1], ***θ***) ≫ 1, the problem of numerical overflow arises. In order to mitigate these issues, the log-likelihood is employed instead of the likelihood,

![art](images/Art_P945.jpg)

As illustrated in [figure 12.12](#chapter011.xhtml#Fig_12-12), the optimal set of parameters ***θ***^∗ corresponds to the location where the derivative of the log-likelihood equals zero. The values ***θ***^∗ can be found using a gradient ascent method such as the Newton-Raphson algorithm presented in [§5.2](#chapter004.xhtml#Sec_5.2). Note that because Newton-Raphson is a convex optimization method, and because SSMs typically involve a *non-convex* (see [chapter 5](#chapter004.xhtml)) and *non-identifiable* (see [§6.3.4](#chapter005.xhtml#Sec_6.3.4)) likelihood function, the optimization is particularly sensitive to initial values ***θ***[0]. It is thus essential to initialize parameters using engineering knowledge and to try several initial starting locations.

![art](images/Art_P946.jpg)

Figure 12.12: The MLE optimal parameters correspond to the location where the derivative of the log-likelihood equals zero.

Note that a closed-form *expectation maximization* method exists for estimating the parameters of SSMs.^([6](#chapter011.xhtml#footnote_6)) However, even if it is mathematically elegant, in the context of civil engineering applications such as those presented in the following sections, it is still sensitive to the selection of the initial values and is thus easily trapped in local maxima.

 

[*12.1.5   Limitations and Practical Considerations*](#toc.xhtml#Rh2-64)

There are some limitations to the Kalman filter formulation. First, it is sensitive to numerical errors when the covariance is rapidly reduced in the measurement step, for example, when accurate measurements are used or after a period with missing data, or when there are orders of magnitude separating the eigenvalues of the covariance matrix. Two alternative formulations that are numerically more robust are the UD filter and square-root filter. The reader interested in these methods should consult specialized textbooks such as the one by Simon^([7](#chapter011.xhtml#footnote_7)) or Gibbs.^([8](#chapter011.xhtml#footnote_8))

A second key limiting aspect is that the formulation of the Kalman filter and smoother are only applicable for linear observation and transition models. When problems at hand require nonlinear models, there are two main types of alternatives: First, there are the *unscented Kalman filter*^([9](#chapter011.xhtml#footnote_9)) and *extended Kalman filter*,^([10](#chapter011.xhtml#footnote_10)) which allow for an approximation of the Kalman algorithm while still describing the hidden states using multivariate Normal random variables. The second option is to employ sampling methods such as the *particle filter*,^([11](#chapter011.xhtml#footnote_11)) where the hidden-state variables are described by particles (i.e., samples) that are propagated through the transition model. The weight of each particle is updated using the likelihood computed from the observation model. Particle filtering is suited to estimate PDFs that are not well represented by the multivariate Normal. The reader interested in these nonlinear-compatible formulations can consult Murphy’s^([12](#chapter011.xhtml#footnote_12)) textbook for further details.

  

[*12.2   State-Space Models with Regime Switching*](#toc.xhtml#Rh1-48)

The state-space model theory we have covered so far is applicable for a set of system responses following a same regime. [Figures 12.13a–b](#chapter011.xhtml#Fig_12-13) are both examples of behaviors where SSMs are applicable. [Figure 12.13c](#chapter011.xhtml#Fig_12-13) presents an example where a standard SSM is not applicable because there is a switch from a zero-speed regime to a constant-speed regime.

![art](images/Art_P947.jpg)

Figure 12.13: Comparison between single- and multiple-regime models.

Estimating the probability of hidden states along with the probability of each regime involves computational challenges. For example, if we consider a case with S = 2 possible regimes, we then have 2 possible transitions along with 2 models to describe each regime. We start from a time step *t*, where the system can be in regime 1 with probability ![art](images/pi11.jpg)and in regime 2 with probability ![art](images/Art_P948.jpg), as illustrated in [figure 12.14a](#chapter011.xhtml#Fig_12-14). There are 2 regimes × 2 possible transition paths, leading to 4 possible combinations to describe the joint probability at times *t* and *t* + 1. Going from *t* + 1 to *t* + 2, each of the 4 paths at *t* + 1 branches into 2 new ones at *t* + 2, leading to a total of now 8 paths. We see through this example that the number of paths to consider increases exponentially (S^T) with the number of time steps T. Even for short time series, this approach becomes computationally prohibitive. In this section, we present the *generalized pseudo Bayesian algorithm of order two*,^([13](#chapter011.xhtml#footnote_13)) which is behind the *switching Kalman filter*.^([14](#chapter011.xhtml#footnote_14)) The key aspect of this method is to collapse the possible transition paths at each time step, as illustrated in [figure 12.14b](#chapter011.xhtml#Fig_12-14).

![art](images/Art_P949.jpg)

Figure 12.14: Comparison of regime switching with and without merging the state at each time step. (Adapted from Nguyen and Goulet (2018).)

 

[*12.2.1   Switching Kalman Filter*](#toc.xhtml#Rh2-65)

We first explore the switching Kalman filter (SKF) while considering only S = 2 possible regimes. The goal is to estimate at each time step *t* the probability of each regime, along with the estimates for the hidden states corresponding to each of them. The notation that will be employed in the SKF is

![art](images/Art_P950.jpg)

where the superscript on the mean vector and covariance matrix refers to the regime number, which is described by the variable *s* ∈ {1, 2, ⋯ , S}. ![art](images/Art_P951.jpg)is the shorthand notation for the probability of the regime *i* at time *t*, given all the available observations up to time *t*, Pr(*S[t]* = *i*|**y**[1:*t*]).

 

*Filtering step*   As presented in [figure 12.15](#chapter011.xhtml#Fig_12-15), starting from regime 1, at *t* − 1, there are two possible paths, each of them corresponding to one of the regime switches. The two possible paths *j* ∈ {1, 2} are explored by estimating the posterior state estimates ![art](images/Art_P953.jpg), along with their likelihood ![art](images/Art_P954.jpg), using the filtering procedure presented in [§12.1.2](#chapter011.xhtml#Sec_12.1.2),

![art](images/Art_P955.jpg)

![art](images/Art_P952.jpg)

Figure 12.15: Switching Kalman filter: How initial states transition through two distinct models.

In equation 12.7, the initial states are obtained from the regime *i*, and the matrices {**A***[j]*, **C***[j]*, **Q***[j]*, **R***[j]*} are those from the model *j*.

Once the procedure presented in [figure 12.15](#chapter011.xhtml#Fig_12-15) is repeated for each model, the next step consists in merging the state estimates that landed in a same regime. [Figure 12.16](#chapter011.xhtml#Fig_12-16) presents an example where the state estimates from the model starting from regime 1 at *t* − 1 and transiting through regime 1 are merged with the state estimates from the model starting from regime 2 at *t* − 1 and transiting through regime 1. This merge step is performed by considering that the final state estimates ![art](images/Art_P956.jpg), along with its probability ![art](images/Art_P957.jpg), describe a multivariate Normal, itself obtained by mixing the state estimates originating from all paths that transited from *t* − 1 → *t* through model *j*.

![art](images/Art_P958.jpg)

Figure 12.16: The switching Kalman filter *merge step*.

*Gaussian mixture*   We now take a quick detour from the switching Kalman filter in order to review the mathematical details related to *Gaussian mixtures* (see [§10.1.1](#chapter009.xhtml#Sec_10.1.1)) that are behind the merge step. For example, we have two states *X*[1] and *X*[2] described by Gaussian random variables so that

![art](images/Art_P959.jpg)

The outcome of the random process, where *π*[1] and *π*[2] = 1 − *π*[1] correspond to the probability of each state, is described by a Gaussian mixture,

![art](images/Art_P960.jpg)

 

[Figure 12.17](#chapter011.xhtml#Fig_12-17) presents an example of two Gaussian PDFs combining in a Gaussian mixture. We can approximate a Gaussian mixture by a single Gaussian^([15](#chapter011.xhtml#footnote_15)) ![art](images/Art_P962.jpg)having a mean and variance given by

![art](images/Art_P963.jpg)

![art](images/Art_P961.jpg)

Figure 12.17: Example of a Gaussian mixture PDF.

[Figure 12.18](#chapter011.xhtml#Fig_12-18) presents four examples of Gaussian mixtures approximated by a single Gaussian PDF. Notice how in (b), when the PDFs of *X*[1] and *X*[2] have the same parameters, the result coincides with the two distributions. Also, by comparing figures (c) and (d), we see that the greater the distance |*µ*[1] − *µ*[2]| is, the greater *σ*[12] is.

![art](images/Art_P964.jpg)

Figure 12.18: Examples of Gaussian mixtures.

*Merge step*   Going back to the switching Kalman filter, the merge step is based on the approximation of a Gaussian mixture by a single Gaussian PDF. The joint posterior probability of the regimes *S*[*t*−1] = *i* and *S[t]* = *j* is proportional to the product of the likelihood ![art](images/Art_P965.jpg), the prior probability ![art](images/Art_P966.jpg), and the probability *Z^(i,j)* of transiting from *s*[*t*−1] = *i* to *s[t]* = *j*,

![art](images/Art_P967.jpg)

The posterior probability of the regime *j* at time *t* is obtained by marginalizing the joint posterior in equation 12.8. For a regime *j*, this operation corresponds to summing the probability of all paths transiting through model *j*, irrespective of their origin,

![art](images/Art_P968.jpg)

The posterior states for each regime *j*, ![art](images/Art_P969.jpg), ![art](images/Art_P970.jpg), are estimated using

![art](images/Art_P971.jpg)

The general overview of the switching Kalman filter is presented in [figure 12.19](#chapter011.xhtml#Fig_12-19). Note that in addition to the parameters defining each filtering model, the SKF requires defining the prior probability of each regime ![art](images/pij0.jpg)along with the S × S transition matrix **Z** defining the probability of transiting from a state at time *t* − 1 to another at time *t* + 1.

![art](images/Art_P972.jpg)

Figure 12.19: General overview of the switching Kalman filter procedure.

 

[*12.2.2   Example: Temperature Data with Regime Switch*](#toc.xhtml#Rh2-66)

This example explores an application of the switching Kalman filter to temperature data subject to a regime switch. [Figure 12.20](#chapter011.xhtml#Fig_12-20) presents the data set where there is a switch between a zero-speed regime and a constant-speed regime. Note that with the SKF, the filtering model associated with each regime must have the same hidden states. In this example, the two states **x***[t]* = \[*x[t] ẋ[t]*\]^T are the temperature and its rate of change, with initial states for both models initialized as

![art](images/Art_P973.jpg)

![art](images/Art_P974.jpg)

Figure 12.20: Example of data set where there is a switch between a zero-speed regime and a constant-speed regime.

Note that the initial states {***µ***[0], **Σ**[0], ***π***[0]} can be estimated using the smoothing algorithm. The first regime is described by a local level where the rate of change is forced to be equal to 0 in the transition matrix \[**A**\][:,2] = 0,

![art](images/Art_P975.jpg)

 

The second regime is described by a local trend model where

![art](images/Art_P976.jpg)

Describing the four possible paths, that is, {1 → 1, 1 → 2, 2 → 1, 2 → 2}, requires the definition of four covariance matrices for the transition-model errors,

![art](images/Art_P977.jpg)

In \[**Q**[12]\][2,2], the MLE optimal parameter estimated using empirical data is *σ*[12] = 2.3 × 10^(−4). There is a single observation model for both regimes defined following

![art](images/Art_P978.jpg)

The MLE for terms on the main diagonal are *z[ii]* = 0.997 so that the complete transition matrix is defined as

![art](images/Art_P979.jpg)

[Figure 12.21](#chapter011.xhtml#Fig_12-21) presents the outcome from the switching Kalman filter: (a) presents the probability of the local trend regime, which marks the transition between the zero-speed and constant-speed regimes; (b) presents the level describing the filtered system responses where the observation errors were removed; and (c) presents the rate of change of the system responses, that is, the trend.

![art](images/Art_P980.jpg)

Figure 12.21: Example of hidden-states estimation using the switching Kalman filter.

 

[*12.3   Linear Model Structures*](#toc.xhtml#Rh1-49)

This section presents how to build linear models from generic components. This approach is referred to as *Bayesian dynamic linear models* by Goulet and Nguyen,^([16](#chapter011.xhtml#footnote_16)) and more commonly as *Bayesian forecasting* or *dynamic linear models* in the literature^([17](#chapter011.xhtml#footnote_17)). Note that the term *linear* does not mean that these models can only be employed to describe linear relationships with respect to time; it refers to the linearity of the observation and transition equations.

Five main components are reviewed here: local level, local trend, local acceleration, periodic, and autoregressive. As illustrated in [figure 12.22](#chapter011.xhtml#Fig_12-22), these components can be seen as the building blocks that, once assembled, allow modeling complex time series. Each component has its own specific mathematical formulation and is intended to model a specific behavior. We will first see the mathematical formulation associated with each component; then we present how to assemble components to form {**A**, **C**, **Q**, **R**} matrices.

![art](images/Art_P981.jpg)

Figure 12.22: Generic components that can be seen as the building blocks, which, once assembled, allow modeling complex empirical responses. From left to right: local level, local trend, local acceleration, periodic, and autoregressive.

 

[*12.3.1   Generic Components*](#toc.xhtml#Rh2-67)

![art](images/Art_P982.jpg)Local level (*x*^(LL))

*Local level*   A local level describes a quantity that is *locally constant* over a time step. It is described by a single hidden variable *x*^(LL). Because of its locally constant nature, its transition model predicts that the hidden state at *t* is equal to the one at *t* − 1, so the transition coefficient is 1. The standard deviation describing the prediction error for the locally constant model is ![art](images/sigmaLLW.jpg). Local levels are part of the hidden variables that contribute to observations, so the coefficient in the observation matrix equals 1. The hidden-state variables as well at the formulation for the transition and observation model matrices are

**x**^(LL) = *x*^(LL), **A**^(LL) = 1, **C**^(LL) = 1, **Q**^(LL) = (*σ*^(LL))².

[Figure 12.23](#chapter011.xhtml#Fig_12-23) presents realizations of a stochastic process defined by the transition model of a local level. We can see that the process variability increases as the standard deviation *σ*^(LL) increases.

![art](images/Art_P983.jpg)

Figure 12.23: Examples of local level components. The initial state ![art](images/Art_P984.jpg)is the same for all realizations.

*Local trend*   A local trend describes a quantity that has a *locally constant* rate of change over a time step. It acts jointly with a hidden variable describing the level. It is thus defined by two hidden variables \[*x*^L *x*^(LT)\]^(**T**). Because of its locally constant nature, its transition model predicts that the hidden state at *t* is equal to the current one, ![art](images/Art_P985.jpg), so the transition coefficient is 1. The hidden state ![art](images/Art_P986.jpg)is described by the current level value plus the change brought by the local trend, multiplied by the time step length ∆*t*. As we have seen in [§12.1.2](#chapter011.xhtml#Sec_12.1.2), the definition of the process-noise covariance matrix **Q**^(LT) requires considering the uncertainty that is caused by a constant acceleration with a random magnitude that can occur over the span of a time step. Analytically, it corresponds to

![art](images/Art_P987.jpg)

![art](images/Art_P988.jpg)Level (*x*^L)

![art](images/Art_P989.jpg)Local trend (*x*^(LT))

where *σ*^(LT) is the process noise parameter. In most cases involving a local trend, only the hidden variable representing the level contributes to observations, so the coefficient in the observation matrix for *x*^(LT) equals 0. The hidden-state estimation as well as the formulation for the transition and observation model matrices are

![art](images/Art_P990.jpg)

[Figure 12.24](#chapter011.xhtml#Fig_12-24) presents realizations of a stochastic process defined by the transition model of a local trend. We can see that the hidden-state variable *x*^(LT) is locally constant and that *x*^L has a locally constant speed. A local trend is employed to model a system response that changes over time with a locally constant speed.

![art](images/Art_P991.jpg)

Figure 12.24: Examples of local trend components. The initial state ![art](images/Art_P992.jpg)is the same for all realizations.

*Local acceleration*   A local acceleration describes a quantity that has a *locally constant* acceleration over a time step. It acts jointly with a level hidden variable and a trend hidden variable. It is thus defined by three hidden-state variables \[*x*^L *x*^T *x*^(LA)\]^T. Because of its locally constant nature, its transition model predicts that the hidden state at *t* is equal to the current one, ![art](images/Art_P993.jpg), so the transition coefficient is 1. The hidden state ![art](images/Art_P994.jpg)is described by the current value plus the change brought by the local acceleration multiplied by the time step length ∆*t*. The hidden state ![art](images/Art_P995.jpg). The hidden-state variables as well as the formulation for the transition and observation model matrices are

![art](images/Art_P996.jpg)

![art](images/Art_P997.jpg)Level (*x*^L)

![art](images/Art_P998.jpg)Trend (*x*^T)

![art](images/Art_P999.jpg)Local acceleration (*x*^(LA))

[Figure 12.25](#chapter011.xhtml#Fig_12-25) presents realizations of a stochastic process defined by the transition model of a local acceleration. We can see that the *x*^(LA) hidden variable is locally constant, *x*^T has a locally constant speed, and *x*^L has a locally constant acceleration. A local acceleration is employed to model a system response that changes over time with a locally constant acceleration.

![art](images/Art_P1000.jpg)

Figure 12.25: Examples of local acceleration components. The initial state ![art](images/Art_P1001.jpg)is the same for all realizations.

*Periodic*   Periodic components are expressed in their *Fourrier form* where they can be described by two hidden variables **x**^S = \[*x*^(S1) *x*^(S2)\]^T. Here, only the first hidden variable contributes to observations, so the coefficients in the observation matrix are 1 for *x*^(S1) and 0 for *x*^(S2). The hidden-state variables as well as the formulation for the transition and observation model matrices are

![art](images/Art_P1002.jpg)

![art](images/Art_P1003.jpg)Periodic (*x*^(S1), *x*^(S2))

 

where the frequency ![art](images/Art_P1004.jpg)is defined as a function of the period *p* and the time step length. [Figure 12.26](#chapter011.xhtml#Fig_12-26) presents realizations of the hidden variables describing the periodic process. A periodic component is employed to model sine-like periodic phenomena with known period *p*. For example, in the context of civil engineering, it can be employed to model the effect of daily and seasonal temperature changes.

![art](images/Art_P1005.jpg)

Figure 12.26: Examples of periodic components. The initial state ![art](images/Art_P1006.jpg)and the period *p* = 10 are the same for all realizations.

*Autoregressive*   The autoregressive (AR) component is described by a single hidden variable *x*^(AR) that presents a dependence on itself over consecutive time steps. Here, we only present the autoregressive process of order 1, where the current state only depends on the previous one,

![art](images/Art_P1007.jpg)

![art](images/Art_P1008.jpg)Autoregressive (*x*^(AR))

*ϕ*^(AR) is the autoregression coefficient defining the transition matrix. The autoregressive hidden-state variable contributes to the observation, so the coefficient in the observation matrix equals 1. The state variable as well as the formulation for the transition and observation model matrices are

x^(AR) = *x*^(AR), **A**^(AR) = *ϕ*^(AR), **C**^(AR) = 1, **Q**^(AR) = (*σ*^(AR))².

[Figure 12.27](#chapter011.xhtml#Fig_12-27) presents examples of realizations of an autoregressive process for different parameters. Like for other components, the variability increases with the process-error standard deviation *σ*^(AR). A key property of the autoregressive process is that for 0 < *ϕ*^(AR) < 1, it leads to a stationary process for which the standard deviation is

![art](images/Art_P1009.jpg)

 

![art](images/Art_P1010.jpg)

Figure 12.27: Examples of autoregressive components. The shaded region corresponds to the ±*σ*^(AR,0) confidence region for the process’s stationary parameters. Note that cases (c) and (f) are nonstationary because *ϕ*^(AR) > 1. The initial state ![art](images/Art_P1011.jpg)is the same for all realizations.

The confidence region corresponding to ±*σ*^(AR,0) is represented by the shaded area. Notice that for *ϕ*^(AR) ≥ 1 the process is nonstationary, which explains why examples (c) and (f) do not display the ±*σ*^(AR,0) region. The special case where *ϕ*^(AR) = 1 corresponds to a *random walk*, which is equivalent to the local level component because *x[t]* = *x*[*t*−1] + *w[t]*.

The autoregressive (AR) component plays a key role in the model. It is there to describe the model errors that have inherent dependencies over time steps; the definition of a transition model involves some approximation errors, and because the transition model is employed to make predictions over successive time steps, the prediction errors are correlated across time. Moreover, note that this correlation tends to one as the time-step length tends to zero. If we do not employ an AR process to describe these time-dependent model errors, our ability to correctly estimate other hidden-state variables can be diminished.

 

[*12.3.2   Component Assembly*](#toc.xhtml#Rh2-68)

A time series of observations *y*[1:T] is modeled by selecting the relevant components and then assembling them to form the global matrices {**A**, **C**, **Q**, **R**}. The global hidden-state variable vector **x** is obtained by concatenating in a column vector the state variables defining each selected component. The observation matrix **C** is obtained by concatenating in a row vector the specific **C** vectors defining each selected component. The transition matrix **A** and the process noise covariance **Q** are obtained by forming *block diagonal* matrices (blkdiag(·, ·)). **A** and **Q** each employs the specific terms defining the selected components. For a single time series, the observation error covariance matrix **R** contains only one term, ![art](images/sigma2V.jpg).

*Example: Climate change*   This example studies daily average temperature data recorded at Montreal’s YUL airport for the period 1953–2013, as presented in [figure 12.28](#chapter011.xhtml#Fig_12-28). The goal is to quantify the current yearly rate of change in the average temperature. Because data is recorded daily, the time-step length is ∆*t* = 1 day. [Figure 12.28](#chapter011.xhtml#Fig_12-28) shows a yearly seasonal pattern with frequency ![art](images/Art_P1013.jpg). In addition to the periodic component, this model requires a local trend to quantify the rate of change and an autoregressive one to capture the time-correlated model prediction errors. For these components, the hidden-state variables are

![art](images/Art_P1014.jpg)

**Note:** The length of a solar year is 365.2422 days.

![art](images/Art_P1012.jpg)

Figure 12.28: Montreal YUL airport daily average temperature observations for the period 1953–2013.

The specific formulation for each component is described below: Local trend component - LT ![art](images/Art_P1015.jpg)

![art](images/Art_P1016.jpg)

Periodic component - S ![art](images/Art_P1017.jpg)

![art](images/Art_P1018.jpg)

Autoregressive component - AR ![art](images/Art_P1019.jpg)

 
| **A^(AR)** || \= || \[*ϕ*^(AR)\] |
| --- | --- | --- |
| **Q^(AR)** || \= || \[(*σ*^(AR))²\] |
| **C^(AR)** || \= || \[1\] |

 

The global matrices describing the model are obtained by assembling the components so that

 
| **A** || \= || blkdiag(**A**^(LT), **A**^S, **A**^(AR)) |
| --- | --- | --- |
| **Q** || \= || blkdiag(**Q**^(LT), **Q**^S, **Q**^(AR)) |
| **C** || \= || \[**C**^(LT) **C**^S **C**^(AR)\] |
| **R** || \= || ![art](images/Art_P1020.jpg). |

The prior knowledge defining the initial states is defined as

 
| E\[*X*[0]\] || \= || \[5 0 0 0 0\]^T |
| --- | --- | --- |
| cov\[*X*[0]\] || \= || diag(\[100 10^(−6) 100 100 100\]). |

The unknown parameters and their MLE optimal values learned from data using the Newton-Raphson algorithm are

***θ***^∗ = \[*ϕ*^(AR), *σ*^(LT), *σ*^(AR), *σ[V]*\]^T = \[0.69 2.2 × 10^(−6) 3.4 2.1 × 10^(−4)\]^T.

[Figure 12.29](#chapter011.xhtml#Fig_12-29) presents the smoothed estimates for hidden-state variables **x***[t]*. Notice in [figure 12.29a](#chapter011.xhtml#Fig_12-29) how the long-term average temperature drops from the 1950s to the 1970s and then increases steadily. [Figure 12.29b](#chapter011.xhtml#Fig_12-29) presents the rate of change in °C/day. When reported on an annual basis, the annual rate of change in 2013 is estimated to be *µ*[T|T] = 0.06 °C/year with a standard deviation *σ*[T|T] = 0.05 °C/year.

![art](images/Art_P1021.jpg)

Figure 12.29: Hidden-state estimates for the temperature time series.

 

[*12.3.3   Modeling Dependencies Between Observations*](#toc.xhtml#Rh2-69)

State-space models can be employed to model the dependencies between several observations. Take, for example, the seasonal variations in the air temperature affecting the displacement of a structure. If we observe both quantities, that is, the temperature and the displacement, we can perform their joint estimation.

In the general case where there are D observed time series, we have to select relevant components for each time series and then assemble them together. The global state vector **x***[t]* for all time series and all components is obtained by concatenating in a column vector the state vectors ![art](images/Art_P1022.jpg), ∀*j* ∈ {1, 2, ⋯ , D} from each time series. The global observation (**C**), transition (**A**), process noise covariance (**Q**), and observation covariance (**R**) matrices are all built in the same way by concatenating block diagonal matrices from each time series,

 
| **C** || \= || blkdiag(**C**¹, **C**², ⋯ , **C**^D) |
| --- | --- | --- |
| **A** || \= || blkdiag(**A**¹, **A**², ⋯ , **A**^D) |
| **Q** || \= || blkdiag(**Q**¹, **Q**², ⋯ , **Q**^D) |
| **R** || \= || blkdiag(**R**¹, **R**², ⋯ , **R**^D). |

 

The global matrix **C** requires special attention because it contains the information regarding the time-series dependencies. In the **C** matrix, each row corresponds to a time series. The component-wise representation of the observation matrix is

![art](images/Art_P1023.jpg)

where the off-diagonal terms ![art](images/Ccij.jpg)are row vectors with the same number of elements as the matrix **C***^j*. When there is no dependence between observations, the off-diagonal matrices ![art](images/Ccij.jpg)contain only zeros. When dependence exists between observations, it can be encoded in a dependence matrix such as

![art](images/Art_P1024.jpg)

where *d[i,j]* ∈ {0, 1} is employed to indicate whether (1) dependence does exist or (0) does not. When *d[i,j]* = 0, ![art](images/Art_P1025.jpg); when dependence exists and *d[i,j]* = 1, the off-diagonal matrix ![art](images/Art_P1026.jpg)contains *k[j]* regression coefficients ![art](images/Art_P1027.jpg)describing the linear dependence between the *k*^(th) component from the *j*^(th) time series and the *i*^(th) time series. All regression coefficients *ϕ*^(*i*|*j*) are treated as unknown parameters to be learned from data.

*Example: Bridge displacement versus temperature*   We consider the joint estimation of the hidden-state variables for two time series: the displacement and temperature measured on a bridge from 2013 until 2015. Both time series are presented in [figure 12.30](#chapter011.xhtml#Fig_12-30), where we can see a negative correlation between the observed displacement and temperature seasonal cycles.

![art](images/Art_P1028.jpg)

Figure 12.30: Observed time series for the displacement and temperature of a bridge.

The *temperature* is modeled using a local level, two periodic components with respective periods of 365.2422 and 1 day, and an autoregressive component,

![art](images/Art_P1029.jpg)

 

All matrices defining the transition and the observation models are obtained by assembling the specific mathematical formulation associated with each component,

![art](images/Art_P1030.jpg)

where ![art](images/Art_P1031.jpg)and ![art](images/Art_P1032.jpg).

The *displacement* is modeled using a local level and an autoregressive component,

![art](images/Art_P1033.jpg)

Matrices defining the transition and the observation models are again obtained by assembling the specific mathematical formulation associated with each component,

 
| **A**^D || \= || block diag (1, *ϕ*^(D,AR)) |
| --- | --- | --- |
| **Q**^D || \= || block diag ([0,] (*σ*^(D,AR))²) |
| **C**^D || \= || \[1 1\] |
| **R**^D || \= || ![art](images/Art_P1034.jpg). |

The global model matrices for the joint data set ![art](images/Art_P1035.jpg)are assembled following

 
| **x** || \= || ![art](images/Art_P1036.jpg) |
| --- | --- | --- |
| **A** || \= || block diag (**A**^D, **A**^T) |
| **C** || \= || block diag (**C**^D, **C**^T) |
| **R** || \= || block diag (**R**^D, **R**^T) |
| **Q** || \= || block diag (**Q**^D, **Q**^T). |

The dependence matrix is defined ![art](images/Art_P1037.jpg), which indicates that the displacement observations depend on the hidden states defined for the temperature. The assembled global observation matrix is thus

![art](images/Art_P1038.jpg)

where the first row corresponds to the displacement and the second to the temperature. Note that there are two regression coefficients describing the dependence between the displacement observations and the temperature hidden-state variables: ![art](images/Art_P1039.jpg), the long-term seasonal effects described by the first periodic component, and ![art](images/Art_P1040.jpg), the short-term ones described by the second periodic component and the autoregressive term. MLE optimal model parameter values estimated from data are

![art](images/Art_P1041.jpg)

The resulting smoothed hidden-state estimations are presented in [figure 12.31](#chapter011.xhtml#Fig_12-31). The periodic behavior displayed in [figure 12.30a](#chapter011.xhtml#Fig_12-30) is not present in any of the displacement components presented in [figures 12.31a–b](#chapter011.xhtml#Fig_12-31). This is because the periodic behavior displayed in the displacement is modeled through the dependence over the temperature’s hidden states.

![art](images/Art_P1042.jpg)

Figure 12.31: Hidden-state estimates for the displacements and temperatures.

 

[*12.4   Anomaly Detection*](#toc.xhtml#Rh1-50)

It is possible to detect anomalies in time series using the regime-switching method presented in [§12.2](#chapter011.xhtml#Sec_12.2). The idea is to create two models representing, respectively, a normal and an abnormal regime. The key strength of this approach is to consider not only the likelihood of each model at each time step but also the information about the prior probability of each regime as well as the probability of switching from one regime to another. In the context of anomaly detection, it allows reducing the number of false alarms while increasing the detection capacity. In a general context, the number of regimes is not limited, so several models can be tested against each other.

*Example: Anomaly detection*   This example illustrates the concept of anomaly detection for observations made on a dam displacement. [Figure 12.32](#chapter011.xhtml#Fig_12-32) presents observations showing a downward trend as well as a yearly periodic pattern. Because no temperature observations are available for a joint estimation, this case is thus treated as a single time series. The components employed are a local acceleration, two periodic components with respective periods *p* = 365.2422 and *p* = 162.1211 days, and one autoregressive component. In this case, we want to employ two different models, where one is constrained to have a constant speed and the other a constant acceleration. The vector of hidden-state variables for both regimes is

![art](images/Art_P1043.jpg)

 

![art](images/Art_P1044.jpg)

Figure 12.32: Example of a dam displacement time series that contains an anomaly that requires using the switching Kalman filter.

Global model matrices **A**^((*j*)), **C**^((*j*)), **Q**^((*j*)), **R**^((*j*)) for regimes *j* ∈ {1, 2} are assembled following the procedure described in [§12.3.2](#chapter011.xhtml#Sec_12.3.2). The only things differentiating the two models are the transition matrices and the process noise covariance for the local acceleration component,

![art](images/Art_P1045.jpg)

The model associated with the first regime has the particularity that the terms in the transition matrix that corresponds to the acceleration are set equal to zero. The covariance matrices for the transition errors from regimes 1 → 2 and 2 → 1 are respectively

![art](images/Art_P1046.jpg)

The transition matrix is parameterized by *z*^(11) and *z*^(22) as defined in

![art](images/Art_P1047.jpg)

[Figure 12.33](#chapter011.xhtml#Fig_12-33) presents the probability of each regime as a function of time; and [figure 12.34](#chapter011.xhtml#Fig_12-34) presents the hidden-state estimates for the level, trend, and acceleration. This example displays a switch between the normal and the abnormal regimes during a short time span. These results illustrate how anomalies in time series can be detected using regime switching. They also illustrate how the baseline response of a system can be isolated from the raw observations contaminated by observation errors and external effects caused by environmental factors. The model allows estimating that before the regime switch, the rate of change was -2 mm/year, and it increased in magnitude to -2.9mm/year after the switch.

![art](images/Art_P1048.jpg)

Figure 12.33: Probability of regimes 1 and 2 obtained using the SKF algorithm.

![art](images/Art_P1049.jpg)

Figure 12.34: Expected values *µ*[*t*|*t*] and uncertainty bound *µ*[*t*|*t*] ± *σ*[*t*|*t*] for hidden states resulting from a combination of regimes 1 and 2 using the SKF algorithm.

 

All the details related to this example can be found in the study performed by Nguyen and Goulet.^([18](#chapter011.xhtml#footnote_18))

The package OpenBDLM^([19](#chapter011.xhtml#footnote_19)) allows using the state-space model’s theory and includes the formulation for the various components defined for Bayesian dynamic linear models.

 

 

*Exercises*

 
| P12.1 || What is the difference between filtering, forecasting, and smoothing? |
| --- | --- |
| P12.2 || Why is the Kalman filter not applicable for nonlinear transition or observation models? What are the alternatives? |
| P12.3 || From prior knowledge ![art](images/Art_P1050.jpg)and the transition and observation models below, compute ![art](images/Art_P1051.jpg)as well as {E\[*Y*[1]\], var\[*Y*[1]\]}.![art](images/Art_P1052.jpg) |
| P12.4 || How do we handle missing data with the Kalman filter? |
| P12.5 || What is the role of the Markov hypothesis in the Kalman filter? |
| P12.6 || Explain what circumstances require employing a Kalman filter with regime switching? |
| P12.7 || Implement the Kalman filter to reproduce the example in [figure 12.9](#chapter011.xhtml#Fig_12-9) using the data **y**[1:5] = \[3.6 10.8 6.7 3.2 2.6\]^T. |
| P12.8 || Building on the Kalman filter you implemented in P12.7, implement the Kalman smoother to reproduce the results presented in [figure 12.28](#chapter011.xhtml#Fig_12-28) using the data set found in the file YUL\_1953\_2013.csv for Montreal’s airport. |
| P12.9 || Repeat the analysis from P12.8 for the data from Toronto’s airport (YZZ\_1938\_2013.csv), located 550 km to the southwest of Montreal, and compare both results. |

 

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter011.xhtml#footnote_ref_1) Kalman, R. E. (1960). A new approach to linear filtering and prediction problems. *Transactions of the ASME–Journal of Basic Engineering 82*(Series D), 35–45.

[²](#chapter011.xhtml#footnote_ref_2) Simon, D. (2006). *Optimal state estimation: Kalman, H infinity, and nonlinear approaches*. Wiley.

[³](#chapter011.xhtml#footnote_ref_3) Bar-Shalom, Y., X. Li, and T. Kirubarajan (2001). *Estimation with applications to tracking and navigation: Theory algorithms and software*. John Wiley & Sons.

[⁴](#chapter011.xhtml#footnote_ref_4) Rauch, H. E., C. T. Striebel, and F. Tung (1965). Maximum likelihood estimates of linear dynamic systems. *AIAA Journal 3*(8), 1445–1450.

[⁵](#chapter011.xhtml#footnote_ref_5) Nguyen, L. H., I. Gaudot, and J.-A. Goulet (2019). Uncertainty quantification for model parameters and hidden state variables in Bayesian dynamic linear models. *Structural Control and Health Monitoring 26*(3), e2309.

[⁶](#chapter011.xhtml#footnote_ref_6) Ghahramani, Z. and G. E. Hinton (1996). Parameter estimation for linear dynamical systems. Technical Report CRG-TR-96-2, University of Toronto, Dept. of Computer Science.

[⁷](#chapter011.xhtml#footnote_ref_7) Simon, D. (2006). *Optimal state estimation: Kalman, H infinity, and nonlinear approaches*. Wiley.

[⁸](#chapter011.xhtml#footnote_ref_8) Gibbs, B. P. (2011). *Advanced Kalman filtering, least-squares and modeling: A practical handbook*. Wiley.

[⁹](#chapter011.xhtml#footnote_ref_9) Wan, E. A. and R. van der Merwe (2000). The unscented Kalman filter for nonlinear estimation. In *Adaptive Systems for Signal Processing, Communications, and Control Symposium*, 153–158. IEEE.

[^(10)](#chapter011.xhtml#footnote_ref_10) Ljung, L. (1979). Asymptotic behavior of the extended Kalman filter as a parameter estimator for linear systems. *IEEE Transactions on Automatic Control 24*(1), 36–50.

[^(11)](#chapter011.xhtml#footnote_ref_11) Del Moral, P. (1997). Non-linear filtering: interacting particle resolution. *Comptes Rendus de l’Académie des Sciences—Series I—Mathematics 325*(6), 653–658.

[^(12)](#chapter011.xhtml#footnote_ref_12) Murphy, K. P. (2012). *Machine learning: A probabilistic perspective*. MIT Press.

[^(13)](#chapter011.xhtml#footnote_ref_13) Blom, H. A. P. and Y. Bar-Shalom (1988). The interacting multiple model algorithm for systems with Markovian switching coefficients. *IEEE Transactions on Automatic Control 33*(8), 780–783.

[^(14)](#chapter011.xhtml#footnote_ref_14) Murphy, K. P. (1998). Switching Kalman filters. Citeseer; and Kim, C.-J. and C. R. Nelson (1999). *State-space models with regime switching: Classical and Gibbs-sampling approaches with applications*. MIT Press.

[^(15)](#chapter011.xhtml#footnote_ref_15) Runnalls, A. R. (2007). Kullback-Leibler approach to Gaussian mixture reduction. *IEEE Transactions on Aerospace and Electronic Systems 43*(3), 989–999.

[^(16)](#chapter011.xhtml#footnote_ref_16) Nguyen, L. H. and J.-A. Goulet (2018). Anomaly detection with the switching Kalman filter for structural health monitoring. *Structural Control and Health Monitoring 25*(4), e2136; and Goulet, J.-A. (2017). Bayesian dynamic linear models for structural health monitoring. *Structural Control and Health Monitoring 24*(12), 1545–2263.

[^(17)](#chapter011.xhtml#footnote_ref_17) Harrison, P. J. and C. F. Stevens (1976). Bayesian forecasting. *Journal of the Royal Statistical Society: Series B (Methodological) 38*(3), 205–228; West, M. and J. Harrison (1999). *Bayesian forecasting and dynamic models*. Springer; and West, M. (2013). Bayesian dynamic modelling. In *Bayesian theory and applications*, 145–166. Oxford University Press.

[^(18)](#chapter011.xhtml#footnote_ref_18) Nguyen, L. H. and J.-A. Goulet (2018). Anomaly detection with the switching Kalman filter for structural health monitoring. *Structural Control and Health Monitoring 25*(4), e2136.

[^(19)](#chapter011.xhtml#footnote_ref_19) Gaudot, I., L. H. Nguyen, S. Khazaeli, and J.-A. Goulet (2019, May). OpenBDLM, an open-source software for structural health monitoring using bayesian dynamic linear models. In *13th Proceedings from the 13th International Conference on Applications of Statistics and Probability in Civil Engineering (ICASP)*.

 

[*13*](#toc.xhtml#chap-12)

[*Model Calibration*](#toc.xhtml#chap-12)

**Nomenclature**

*Observed system responses*

D*[y]* = {*y*[1], *y*[2], ⋯ , *y*[D]}

*Covariates*

D*[x]* = {**x**[1], **x**[2], ⋯ , **x**[D]}

*Parameter values*

***θ*** = \[*θ*[1] *θ*[2] ⋯ *θ*[P]\]^T

*Model predictions*

**g**(***θ***, **x**) = \[*g*(***θ***, **x**[1]) ⋯ *g*(***θ***, **x**[D])\]^T

In civil engineering, *model calibration* is employed for the task of estimating the parameters of *hard-coded physics-based models* using empirical observations D = {(*x[i]*, *y[i]*), ∀*i* ∈ {1 : D}} = {D[*x*], D*[y]*}. The term *hard-coded physics-based* refers to mathematical models made of constitutive laws and rules that are themselves based on physics or domain-specific knowledge. In contrast, models presented in [chapters 8](#chapter007.xhtml), [9](#chapter008.xhtml), and [12](#chapter011.xhtml) are referred to as *empirical models* because they are built on empirical data with little or no hard-coded rules associated with the underlying physics behind the phenomena studied. The hard-coded model of a system is described by a function *g*(***θ***, **x**), which depends on the covariates **x** = \[*x*[1] *x*[2] ⋯ *x*[X]\]^T ∈ ℝ^X as well as its model parameters ***θ*** = \[*θ*[1] *θ*[2] ⋯ *θ*[P]\]^T. The *observed system responses* D*[y]* = {*y*[1], *y*[2], ⋯ , *y*[D]} depend on covariates D*[x]* = {**x**[1], **x**[2], ⋯ , **x**[D]}. [Figure 13.1](#chapter012.xhtml#Fig_13-1) presents an example of a model where the parameters ***θ*** describe the boundary conditions and the initial tension in cables. For this example, the covariates **x** and **x**^∗ describe the locations where predictions are made, as well as the type of predictions, that is, displacement, rotation, strain, and so on. The vector **x** describes covariates for observed locations, and **x**^∗ those for the unobserved locations.

![art](images/Art_P1053.jpg)

Figure 13.1: Example of hard-coded finite-element model for which we want to infer the parameter values ***θ*** = \[*θ*[1] *θ*[2]\]^T from sets of observations (*x[i]*, *y[i]*).

Model calibration is not in itself a subfield of machine learning. Nevertheless, in this chapter, we explore how the machine learning methods presented in previous chapters can be employed to address the challenges associated with the probabilistic inference of model parameters for hard-coded models. This application is classified under the umbrella of *unsupervised learning* because, as we will see, the main task consists in inferring hidden-state variables and parameters that are themselves not observed.

*Problem setups*   There are several typical setups where we want to employ empirical observations in conjunction with hard-coded models. For the example presented in [figure 13.1](#chapter012.xhtml#Fig_13-1), if we have a prior knowledge for the joint distribution of model parameters *f*(***θ***), we can propagate this prior knowledge through the model in order to quantify the uncertainty associated with predictions. This uncertainty propagation can be, for instance, performed using either Monte Carlo sampling (see [§6.5](#chapter005.xhtml#Sec_6.5)) or first-order linearization (see [§3.4.2](#chapter002.xhtml#Sec_3.4.2)). When the uncertainty in the prior knowledge *f*(***θ***) is weakly informative, it may lead to a large variability in model predictions. In that situation, it becomes interesting to employ empirical observations to reduce the uncertainty related to the prior knowledge of model parameters. The key with model calibration is that model parameters are typically not directly observable. For instance, in [figure 13.1](#chapter012.xhtml#Fig_13-1) it is often not possible to directly measure the boundary condition properties or to measure the cable internal tension. These properties have to be inferred from the observed structural responses D*[y]*. Another key aspect is that we typically build physics-based models **g**(***θ***, **x**) because they can predict quantities that cannot be observed. For example, we may want to learn about model parameters ***θ*** using observations of the static response of a structure defined by the covariates **x** and then employ the model to predict the unobserved responses **g**(***θ***, **x**^∗), defined by other covariates **x**^∗. The vector **x**^∗ may describe unobserved locations or quantities such as the dynamic behavior instead of the static one employed for parameter estimation. One last possible problem setup is associated with the selection of model classes for describing a phenomenon.

There are three main challenges associated with model calibration: *observation errors*, *prediction errors*, and *model complexity*. The first challenge arises because the observations available D*[y]* are in most cases contaminated by observation errors. The second is due to the discrepancy between the prediction of hard-coded physics-based models **g**(***θ***, **x**) and the real system responses; that is, even when parameter values are known, the model remains an approximation of the reality. The third challenge is related to the difficulties associated with choosing a model structure having the right complexity for the task at hand. In [§13.1](#chapter012.xhtml#Sec_13.1), we explore the impact of these challenges on the least-squares model calibration approach, which is still extensively used in practice. Then, the subsequent sections explore how to address some of these challenges using a hierarchical Bayesian approach combining concepts presented in [chapters 6](#chapter005.xhtml) and [8](#chapter007.xhtml).

  

[*13.1   Least-Squares Model Calibration*](#toc.xhtml#Rh1-52)

![art](images/Art_P1054.jpg)

What we will see in [§ 13.1](#chapter012.xhtml#Sec_13.1) is an example of what *not to do* when calibrating a hard-coded physics-based model as well as why one should avoid it.

This section presents the pitfalls and limitations of the common least-squares deterministic model calibration. With *least-squares* model calibration, the goal is to find the model parameters ***θ*** that minimize the sum of the square of the differences between predicted and measured values. The difference between predicted and observed values at one observed location **x***[i]* is defined as the residual

*r*(***θ***, (**x***[i], **y**[i]*)) = *y[i]* − *g*(***θ***, **x***[i]*).

For the entire data set containing D data points, the least-squares loss function is defined as

![art](images/Art_P1055.jpg)

Because of the square exponent in the loss function, its value is positive *J*(***θ***, D) ≥ 0. The task of identifying the optimal parameters ***θ***^∗ is formulated as a minimization problem where the goal is to minimize the sum of the square of the residual at each observed location,

![art](images/Art_P1056.jpg)

Gradient-based optimization methods such as those presented in [chapter 5](#chapter004.xhtml) can be employed to identify ***θ***^∗.

 

[*13.1.1   Illustrative Examples*](#toc.xhtml#Rh2-71)

This section presents three examples based on simulated data using the *reference beam model ǧ*(*Ě*, *x*) presented in [figure 13.2](#chapter012.xhtml#Fig_13-2) along with the values for its parameters. Observations consist in displacement measurements made for positions *x*[1] = *L*/2 and *x*[2] = *L*. The first example corresponds to the idealized context where there is no observation or prediction errors because the model employed to infer parameter values is the same as the reference model employed to generate synthetic data. The second example employs a simplified model to infer parameters. Finally, the third example employs an overcomplex model to infer parameters. Note that the last two examples include observation errors. For all three cases, there is a single unknown parameter: the elastic modulus *E*, which characterizes the flexural stiffness of the beam.

![art](images/Art_P1057.jpg)

Figure 13.2: The reference model *ǧ*(*Ě*, *x*) that is employed to generate simulated observations.

 

**Example #1  
Reference Model**

![art](images/Art_P1058.jpg)

**Interpretation Model**

![art](images/Art_P1059.jpg)

*Example #1: Exact model without observation errors*   The first example illustrates an idealized context where there are no observation or prediction errors because the model employed to infer parameter values *g*(*E*, *x*) is the same as the one employed to generate synthetic data *ǧ*(*Ě*, *x*). [Figure 13.3](#chapter012.xhtml#Fig_13-3) compares the predicted and true deflection curves along with observed values. Here, because of the absence of model or measurement errors, the optimal parameter also coincides with its true value *θ*^∗ = *E*^∗ = *Ě*, and the predicted deflection obtained using the optimal parameter value *θ*^∗ coincides with the true deflection. Note that the loss function evaluated for *θ*^∗ equals zero. Even if least-squares model calibration worked perfectly in this example, this good performance cannot be generalized to real case studies because in this oversimplified example, there are no model or measurement errors.

![art](images/Art_P1060.jpg)

Figure 13.3: Least-squares model calibration where the interpretation model is identical to the reference model, *ǧ*(*Ě*, *x*) = *g*(*Ě*, *x*), and where there are no measurement errors.

**Example #2  
Reference Model**

![art](images/Art_P1061.jpg)

**Interpretation Model**

![art](images/Art_P1062.jpg)

*Example #2: Simplified model with observation errors*   The second example presents a more realistic case, where the model *g*(*E*, *x*) employed to infer parameters contains a simplification in comparison with the real system described by the reference model *ǧ*(*Ě*, *x*). In this case, the simplification consists in omitting the rotational spring that is responsible for the nonzero initial rotation at the support. In addition, observations are affected by observation errors *v[i]* : *V* ∼ N(*v*; 0, 1) mm, where the observation model is defined as

*y[i]* = *ǧ*(*Ě*, *x[i]*) + *v[i], V[i]* ⊥ *V[j]*, ∀*i* ≠ *j*.

[Figure 13.4](#chapter012.xhtml#Fig_13-4) compares the predicted and true deflection curves along with observed values. We see that because of the combination of model simplification and observation errors, we obtain a higher loss for the correct parameter value *Ě* = 35 GPa than for the optimal value *E*^∗ = 22 GPa. As a result, the model predictions are also biased for any prediction location *x*. This second example illustrates how deterministic least-squares model calibration may identify wrong parameter values as well as lead to inaccurate predictions for measured and unmeasured locations.

![art](images/Art_P1063.jpg)

Figure 13.4: Least-squares model calibration where the interpretation model is simplified in comparison with the reference model, *ǧ*(*Ě*, *x*) ≠ *g*(*Ě*, *x*), and where there are measurement errors.

 

**Example #3 Reference Model**

![art](images/Art_P1064.jpg)

**Interpretation Model**

![art](images/Art_P1065.jpg)

*Example #3: Overcomplex model with observation errors*   The third example illustrates the pitfalls of performing model calibration using a simplified yet overcomplex interpretation model, that is, a model that contains simplifications yet also contains too many parameters for the problem at hand. Here, overcomplexity is caused by the use of two parameters for describing the elastic modulus, *E*[1] and *E*[2]. Like in the second example, observations are affected by observation errors *v[i]* : *V* ∼ N(*v*; 0, 1) mm.

[Figure 13.5](#chapter012.xhtml#Fig_13-5) compares the predicted and true deflection curves along with observed values. Note how the over-parameterization allowed to wrongly match both observations. Parameter values identified are biased in comparison with the true value, and the predictions made by the model are also biased. Because in practice the true deflection and parameter values remain unknown, the biggest danger is *overfitting* where we could believe that the model is capable of providing accurate predictions because the calibration wrongly appears to be perfect. In the context of least-squares model calibration, this issue can be mitigated using cross-validation (see [§8.1.2](#chapter007.xhtml#Sec_8.1.2)), where only subsets of observations are employed to train the model, and then the remaining data is employed to test the model’s predictive capacity. This procedure would reveal that the interpretation model is poorly defined. In a more general way, we can also use Bayesian model selection (see [§6.8](#chapter005.xhtml#Sec_6.8)) for quantifying the probability of each model class.

![art](images/Art_P1066.jpg)

Figure 13.5: Least-squares model calibration where the interpretation model is overcomplex in comparison with the reference model, *ǧ*(*Ě*, *x*) ≠ *g*(*Ě*[1], *Ě*[2], *x*), and where there are measurement errors.

  

[*13.1.2   Limitations of Deterministic Model Calibration*](#toc.xhtml#Rh2-72)

Deterministic model calibration using methods such as least-squares residual minimization performs well when model and measurement errors are negligible and when data sets are large; the issue is that in practical engineering applications, the errors associated with measurements and especially hard-coded models are not negligible, and data sets are typically small. As illustrated in [figure 13.6](#chapter012.xhtml#Fig_13-6), for engineering systems, no matter how much effort is devoted to building a hard-coded physics-based model, it will always remain a simplified version of the reality. Therefore, model simplifications introduce prediction errors that need to be considered explicitly as hidden variables to be inferred in addition to model parameters ***θ***.

![art](images/Art_P1067.jpg)

Figure 13.6: In complex engineering contexts, no matter how good a hard-coded physics-based model is, it never perfectly represents the reality. (Photo: Tamar Bridge, adapted from Peter Edwards)

 

[*13.2   Hierarchical Bayesian Estimation*](#toc.xhtml#Rh1-53)

This section presents a Bayesian *hierarchical* method for jointly estimating model parameters as well as prediction errors. The justification for this approach is that no matter how good a hard-coded model is, it remains an approximation of the reality. Therefore, in addition to the model parameters, we need to infer prediction errors. There is typically an issue of non-identifiability (see [§6.3.4](#chapter005.xhtml#Sec_6.3.4)) between model parameters and prediction errors. As we will see, the problem is made identifiable using prior knowledge. In addition, note that because of observation errors, observations *y[i]* are not exact representations of the reality either, that is,

![art](images/Art_P1068.jpg)

In the previous equation, observations **y** = \[*y*[1] *y*[2] ⋯ *y*[D]\]^T are modeled by the sum of *model predictions* **g**(***θ***, **x**) ∈ ℝ^D, which are a function of covariates **x** = \[**x**[1] **x**[2] ⋯ **x**[D]\]^T ∈ ℝ^(X×D) and *model parameters **θ*** = \[*θ*[1] *θ*[2] ⋯ *θ*[P]\]^T ∈ ℝ^P; *prediction errors* **w**(**x**) = \[*w*(**x**[1]) *w*(**x**[2]) ⋯ *w*(**x**[D])\]^T ∈ ℝ^D, which are also a function of covariates **x**; and *measurement errors* **v** = \[*v*[1] *v*[2] ⋯ *v*[D]\]^T ∈ ℝ^D.

 

[*13.2.1   Joint Posterior Formulation*](#toc.xhtml#Rh2-73)

The model predictions **g**(***θ***, **x**) depend on the known covariates **x** describing the prediction locations and unknown model parameters ***θ*** describing physical properties of the system. The observed structural responses are described by

 

![art](images/Art_P1069.jpg)

where measurement errors are assumed to be independent of the covariates **x**. All the terms in equation 13.1 are considered as deterministic quantities because, for a given set of observations D = {D*[x]*, D*[y]*} = {(**x***[i], **y**[i]*), ∀*i* ∈ {1 : D}}, quantities **x**, **y**, ***θ***, **w**(**x**), and **v** are not varying, yet values for ***θ***, **w**(**x**), and **v** remain unknown.

The prior knowledge for model parameters is described by the random variable **Θ** ∼ *f*(***θ***; **z***[p]*), where **z***[p]* are the *hyperparameters*, that is, parameters of the prior probability density function (PDF). When hyperparameters **z***[p]* are unknown, the random variable **Z***[p]* is described by a *hyper-prior f*(**z***[p]*) and a *hyper-posterior f*(**z***[p]*|D), that is, the prior and posterior PDFs of hyperparameters. Unlike the parameter values ***θ***, for which true values may exist, hyperparameters **z***[p]* are parameters of our prior knowledge, for which, by nature, no true value exists. When hyperparameters **z***[p]* are assumed to be fixed constants that are not learned from data, they can be implicitly included in the prior PDF formulation *f*(***θ***; **z***[p]*) = *f*(***θ***).

The concept of *prior*, *posterior*, *hyper-prior*, and *hyper-posterior* not only applies to unknown parameters ***θ*** but also to prediction errors **w**(**x**) and measurement errors **v**. Note that, unlike for hyperparameters **z***[p]* and **z***[w]*, a true value can exist for **z***[v]*. When it exists, the true value for **z***[v]* can typically be inferred from the statistical precision of the measuring instruments employed to obtain **y**. In this section, in order to simplify the notation and to allow focusing the attention on model parameters ***θ*** and prediction errors **w**(**x**), we assume that **z***[p]* and **z***[v]* are known constants.

The formulation for the joint posterior PDF for unknown model parameters ***θ***, prediction errors **w**(**x**), and prediction errors prior PDF hyperparameters **z***[w]* follows:

![art](images/Art_P1070.jpg)

 

*Likelihood*   The formulation for the joint posterior in equation 13.2 allows the explicit quantification of the dependence between model parameters and prediction errors at observed locations. In the case where several sets of model parameters and prediction errors {***θ***, **w**(D*[x]*)} can equally explain the observations, then the problem is non-identifiable (see [§6.3.4](#chapter005.xhtml#Sec_6.3.4)) and several sets of values will end up having an equal posterior probability, given that the prior probability of each set is also equal. Here, the likelihood of data D*[y]* is formulated considering that **g**(***θ***, D*[x]*) and **w**(D*[x]*) are unknown constants, so the only aleatory quantities are the observation errors **V** ∼ N(**v**; **0**, **Σ***[v]*). The formulation of the likelihood is then

![art](images/Art_P1071.jpg)

*Prior*   It is necessary to define a mathematical formulation for the prior PDF of prediction errors, **W** ∼ *f*(**w**|**z***[w]*). A convenient choice consists in describing the prior PDF for prediction errors using a Gaussian process analogous to the one described in [§8.2](#chapter007.xhtml#Sec_8.2). With the assumption that our model is unbiased, that is, the prior expected value for prediction errors is **0**, this Gaussian process is expressed as

 
| **W** || ∼ || N(**w**; **0**, **Σ***[w]*), where |
| --- | --- | --- |
| \[**Σ***[w]*\]*[ij]* || \= || *σ[w]*(**x***[i]*) · *σ[w]*(**x***[j]*) · *ρ*(**x***[i]*, **x***[j]*, *ℓ*), and |
| *σ[w]*(**x**) || \= || fct(**x**, **z***[s]*), |
| *ρ*(**x***[i]*, **x***[j]*, *ℓ*) || \= || ![art](images/Art_P1072.jpg), |
| **z***[w]* || \= || \[**z***[s] ℓ*\]^T. |

The prediction error standard deviation *σ[w]*(**x**) is typically covariate dependent, so that it needs to be represented by a problem-specific function fct(**x**, **z***[s]*), where **z***[s]* are its parameters. The correlation structure can be represented by a square-exponential covariance function, where **Σ***[ℓ]* is a diagonal matrix, parameterized by the length-scale parameters *ℓ* = \[*ℓ*[1] *ℓ*[2] ⋯ *ℓ*[X]\]^(**T**). *ℓ[k]* is the hyperparameter describing how the correlation decreases as the distance (*x*[*k*,*i*] − *x*[*k*,*j*])² increases. Note that this choice for the correlation structure is not exclusive and others can be employed as described in [§8.2](#chapter007.xhtml#Sec_8.2). The hyperparameters regrouped in **z***[w]* need to be learned from data.

**Example #4  
Reference model**

![art](images/Art_P1073.jpg)

**Interpretation model**

![art](images/Art_P1074.jpg)

*Example #4: Joint posterior estimation*   We are revisiting example #2, where the model employed to infer parameters *g*(*E*, *x*) contains simplifications in comparison with the reference model *ǧ*(*Ě*, *x*) describing the real system studied. In this case, the simplification consists in omitting the rotational spring allowing for a nonzero initial rotation at the support. In addition, observations are affected by independents and identically distributed observation errors *v[i]* : *V* ∼ N(*v*; 0, 1) mm.

[Figure 13.7a](#chapter012.xhtml#Fig_13-7) presents the true deflection obtained from the reference model as well as from the interpretation model using the true parameter value *Ě* = 35 GPa. We can see that for any location other than *x* = 0, there is a systematic prediction error. The prior knowledge for these theoretically unknown prediction errors is modeled using a zero-mean Gaussian process,

*f*(**w**) = N(**w**; **0**, **Σ***[w]*),

where each term of the covariance matrix is defined as

![art](images/Art_P1075.jpg)

![art](images/Art_P1077.jpg)

Figure 13.7: Graphical representation of the prior knowledge for prediction errors arising from the use of a simplified interpretation model.

The prior knowledge for prediction errors is parameterized by **z***[w]* = \[*a ℓ*\]^(**T**). [Figure 13.7b](#chapter012.xhtml#Fig_13-7) presents the marginal ±*σ[w]* confidence interval around the predicted deflection. The prior knowledge for each parameter and hyperparameter is elastic modulus N(*E*; 20, 20²) GPa, model error prior scale factor N(*a*;10^(−4), (5 × 10^(−4))²), and length-scale N(*ℓ*; 5, 50²) m. Note that all of those priors are assumed to be independent from each other, so the joint prior can be described by the product of the marginals. The analytic formulation of the posterior PDF for the unknown model parameter *θ* = *E*, the prediction errors *w*(5), *w*(10), and the hyperparameters *a*, *ℓ* is known up to a constant, so that

![art](images/Art_P1076.jpg)

 

Using the Metropolis sampling method presented in [§7.1](#chapter006.xhtml#Sec_7.1), three parallel chains, containing a total of S = 10⁵ joint samples, are taken from the unnormalized posterior *f*(*E*, *w*(5), *w*(10), *a*, *ℓ*|D*[y]*), where each joint sample is described by {*E*, *w*(5), *w*(10), *a*, *ℓ*}*[s]*. The first half of each chain are discarded as burn-in samples; the Metropolis acceptance rate is approximately 0.25, and the estimated potential scale reduction (EPSR, i.e., chain stationarity metric; see [§7.3.3](#chapter006.xhtml#Sec_7.3.3)) is below 1.1 for all parameters and hyperparameters. The Markov chain Monte Carlo (MCMC) posterior samples are presented in [figure 13.8](#chapter012.xhtml#Fig_13-8), where, when it exists, the true value is represented by the symbol ∗. Note the almost perfect correlation in the posterior between *w*[1](5) and *w*[2](10). It happens because, as illustrated in [figure 13.7](#chapter012.xhtml#Fig_13-7), whenever the model either under- or overestimates the displacement, it does for both locations. Notice that there is also a clear dependence between prediction errors *w[i]* and the elastic modulus *E*, where small (large) values for *E* are compensated by large positive (negative) prediction errors. These are examples of non-identifiability regularized by prior knowledge, as described in [§6.3.4](#chapter005.xhtml#Sec_6.3.4).

![art](images/Art_P1078.jpg)

Figure 13.8: Bivariate scatter plots and histograms describing the marginal posterior PDFs. The symbol ∗ indicates the true values.

  

[*13.2.2   Predicting at Unobserved Locations*](#toc.xhtml#Rh2-74)

**Note:** From equation 13.3,

![art](images/Art_P1082.jpg)

In practical applications, we are typically interested in predicting the structure’s responses *u* at unobserved locations **x**[∗]. Analogous to equation 13.1, the predicted values at unobserved locations are defined as

*u* = *g*(*E*, **x**[∗]) + **w**(**x**[∗]).

When predicting at unobserved locations, we want to consider the knowledge obtained at observed locations, as described by the posterior samples displayed in [figure 13.8](#chapter012.xhtml#Fig_13-8). When using MCMC samples (see [§7.5](#chapter006.xhtml#Sec_7.5)), we can approximate the posterior predictive expected values and covariances by following

![art](images/Art_P1079.jpg)

In order to compute E\[**U**|D\] and cov(**U**|D), we have to generate realizations of **u***[s]* from *f*(**u**|D) using the MCMC samples {*E*, *w*(5), *w*(10), *a*, *ℓ*}*[s]* obtained from the unnormalized posterior *f*(*E*, *w*(5), *w*(10), *a*, *ℓ*|D*[y]*). Through that process, we must first generate realizations for the covariance matrices ![art](images/Art_P1080.jpg)describing the model errors prior PDF. These realizations are then used to update the posterior mean vector and covariance matrix describing the model errors at prediction locations, so that

![art](images/Art_P1081.jpg)

Realizations of the model errors at prediction locations **w**[*s*∗] can be sampled from the multivariate Gaussian PDF defined by

![art](images/Art_P1083.jpg)

Finally, we can obtain a realization of the structure’s behavior at predicted locations by summing the realization of model errors **w**[*s*∗] with the model predictions evaluated for the model parameter MCMC sample *E[s]*,

**u***[s]* = *g*(*E[s]*, **x**[∗]) + **w**[*s*∗].

 

[Figure 13.9a](#chapter012.xhtml#Fig_13-9) presents a comparison of the posterior predictive model prediction samples **u***[s]* with the deflection of the reference model. [Figure 13.9b](#chapter012.xhtml#Fig_13-9) presents the same comparison, this time using the posterior predictive mean vector and confidence interval. Notice how the confidence interval and the smoothness of the realizations match the true deflection profile.

![art](images/Art_P1084.jpg)

Figure 13.9: Comparison of the posterior predictive model predictions with the displacement of the reference model.

The scatter plots in [figure 13.8](#chapter012.xhtml#Fig_13-8) show that significant uncertainty remains regarding the parameter *E* and prediction errors *w*(5), *w*(10). However, because there is a strong dependence in the joint posterior PDF describing these variables, the posterior uncertainty for the deflection remains limited. It happens because abnormally small (large) values for the elastic modulus *E[s]* result in large (small) negative displacements, which are compensated for by large positive (negative) prediction errors *w[s]*(5), *w[s]*(10). This example illustrates why, when calibrating model parameters, it is also necessary to infer model prediction errors because parameters and prediction errors are typically dependent on each other.

The most difficult part of such a hierarchical Bayesian estimation procedure is to define an appropriate function for describing the prior knowledge of model prediction errors. This aspect is what is limiting its practical application to complex case studies where the prediction errors depend not only on the prediction locations but also on the prediction types, for example, rotation, strain, acceleration, and so on. When several formulations for the prior knowledge of prediction errors are available, the probability of each of them can be estimated using Bayesian model selection (see [§6.8](#chapter005.xhtml#Sec_6.8)) or cross-validation (see [§8.1.2](#chapter007.xhtml#Sec_8.1.2)). Further details about hierarchical Bayesian estimation applied to model calibration can be found in Kennedy and O’Hagan;^([1](#chapter012.xhtml#footnote_1)) Brynjarsdóttir and O’Hagan.^([2](#chapter012.xhtml#footnote_2))

 

 

*Exercises*

 
| P13.1 || Explain the issues with the least-square calibration of hard-coded physics-based models. |
| --- | --- |
| P13.2 || Explain why there are dependencies between unknown model parameters and model prediction errors. |
| P13.3 || Explain the differences between a prior and a hyper-prior. |
| P13.4 || Reproduce the results presented in [figure 13.4](#chapter012.xhtml#Fig_13-4) using least-square model calibration. Use the data set D*[x]* = {−3.3, 6.6, 10} m, D*[y]* = {−2.8, −6.9, −12.6} mm, along with the beam displacement governed by the equation![art](images/Art_P1085.jpg) |
| P13.5 || Repeat the problem in P13.4, this time using the hierarchical Bayesian approach presented in [§13.2](#chapter012.xhtml#Sec_13.2). |

 

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter012.xhtml#footnote_ref_1) Kennedy, M. C. and A. O’Hagan (2001). Bayesian calibration of computer models. *Journal of the Royal Statistical Society: Series B (Statistical Methodology) 63*(3), 425–464.

[²](#chapter012.xhtml#footnote_ref_2) Brynjarsdóttir, J. and A. O’Hagan (2014). Learning about physical parameters: The importance of model discrepancy. *Inverse Problems 30*(11), 114007.

 

[**Part V**](#toc.xhtml#part-5)

[**Reinforcement Learning**](#toc.xhtml#part-5)

![art](images/Art_P1086.jpg)

 

 

[*14*](#toc.xhtml#chap-13)

[*Decisions in Uncertain Contexts*](#toc.xhtml#chap-13)

This chapter explores how to make rational decisions regarding actions to be taken in a context where the state variables on which a decision is based are themselves uncertain. Basic contextual notions will be presented through an illustrative example before introducing the formal mathematical notation associated with *rational decisions* and *value of information*.

 

[*14.1   Introductory Example*](#toc.xhtml#Rh1-55)

**Actions**

Do nothing ![art](images/keep_s.jpg)

Recycle ![art](images/chain_s.jpg)

**States**

Not contaminated ![art](images/tick_s.jpg)

Contaminated ![art](images/skull_s.jpg)

In order to introduce the notions associated with *utility theory*, we revisit the soil contamination example presented in [§8.2.5](#chapter007.xhtml#Sec_8.2.5), where we have a cubic meter of potentially contaminated soil. The two possible states ![art](images/Art_P1087.jpg)are either *contaminated* or *not contaminated*, and the two possible actions ![art](images/Art_P1088.jpg)are either to *do nothing* or to *send the soil to a recycling plant* where it is going to be decontaminated. A soil sample is defined as contaminated if the pollutant concentration *c* exceeds a threshold value *c* > *ϕ*[adm.]. The issue is that for most m³ in an industrial site, there are no observations made in order to verify whether or not it is contaminated. Here, we rely on a regression model built from a set of discrete observations to predict for any *x*, *y*, *z* coordinates what our knowledge of the contaminant concentration is as described by its expected value and variance. In this example, our current knowledge indicates that, for a specific m³,

![art](images/Art_P1089.jpg)

The optimal decision regarding the action to choose depends on the value incurred by taking an action given the state *x*. In this example we have two states and two actions, so there are four possibilities to be defined, as illustrated in [figure 14.1](#chapter013.xhtml#Fig_14-1). The incurred value ($) for each pair of states *x* and actions taken *a* are

![art](images/Art_P1092.jpg)

where doing nothing when the soil is not contaminated incurs no cost, decontaminating incurs a cost of $100/m³ whether or not the soil is contaminated, and omitting the decontamination when it is actually contaminated (i.e., *c* > *ϕ*[adm.]) incurs a cost of $10 K in future legal fees and compensatory damages.

![art](images/Art_P1091.jpg)

Figure 14.1: Decision context for a soil contamination example.

[Figure 14.2](#chapter013.xhtml#Fig_14-2) depicts a *decision tree* illustrating the actions along with the probability of each outcome. The optimal action to be taken must be selected based on *the expected* value conditional on each action,

![art](images/Art_P1093.jpg)

![art](images/Art_P1095.jpg)

Figure 14.2: Decision tree for the soil contamination example.

Because ![art](images/Art_P1094.jpg), the optimal action is thus to send the soil to a recycling plant where it will be decontaminated. As you can expect, changing the probability of each state or changing the incurred relative value ($) for a pair of states *x* and actions taken *a* will influence the optimal action to be taken. The next section presents the *utility theory*, which formalizes the method employed in this introductory example.

 

[*14.2   Utility Theory*](#toc.xhtml#Rh1-56)

*Utility theory*   defines how rational decisions are made. This section presents the nomenclature associated with utility theory, it formalizes what a rational decision is, and it presents its fundamental axioms.

 

[*14.2.1   Nomenclature*](#toc.xhtml#Rh2-75)

 
| **A = {**a**[1], ⋯ , **a**[A]}** || A set of possible  
actions |
| --- | --- |
| *x* ∈ X ⊆ ℤ or ⊆ ℝ || An outcome from  
a set of possible  
states |
| Pr(*X* = *x*) ≡ Pr(*x*) || Probability of a  
state *x* |
| U(*a*, *x*) || Utility given a state *x* and an action *a* |

A decision consists in the task of choosing an action a*[i]* from a set of possible actions **A** = {**a**[1], **a**[2], ⋯ , **a**[A]}. This decision is based on our knowledge of one or several state variables *x*, which can either be discrete or continuous. Our knowledge of a state variable is either described by its probability density *X* ∼ *f*(*x*) or mass function *X* ∼ *p*(*x*) = Pr(*X* = *x*). The *utility* U(*a*, *x*) quantifies the relative preferences we have for the joint result of taking an action *a* while being in a state *x*.

![art](images/Art_P1099.jpg)

*Soil contamination example*   For the example presented in the introduction of this chapter, the actions and states can be formulated as binary discrete variables; ![art](images/Art_P1096.jpg)and ![art](images/Art_P1097.jpg). The probability of each state is Pr(*X* = *x*) = {0.9, 0.1}, and the utility of each pair of actions, and states, is

![art](images/Art_P1098.jpg)

 

[*14.2.2   Rational Decisions*](#toc.xhtml#Rh2-76)

In the context of the utility theory, a *rational decision* is defined as a decision that maximizes the *expected utility*. In an uncertain context, the perceived benefit of an action a*[i]* is measured by the expected utility, U(*a*) ≡ E\[U(*a*, *X*)\]. When *X* is a discrete random variable so that *x* ∈ X = {1, 2, ⋯ , X}, the expected utility is

![art](images/Art_P1100.jpg)

Instead, when *X* is a continuous random variable, the expected utility is

![art](images/Art_P1101.jpg)

The *optimal* action *a*^∗ is the one that *maximizes the expected utility*,

![art](images/Art_P1102.jpg)

 

[*14.2.3   Axioms of Utility Theory*](#toc.xhtml#Rh2-77)

 
| *L[i]* ≻ *L[j]* || *L[i]* is preferred over *L[j]* |
| --- | --- |
| *L[i]* ∼ *L[j]* || *L[i]* and *L[j]* are indifferent |
| *L[i]* ≽ *L[j]* || *L[i]* is preferred over *L[j]* or are indifferent |

The axioms of utility theory are based on the concepts of *lotteries*. A lottery *L* is defined by a set of possible outcomes *x* ∈ X = {1, 2, ⋯ , X}, each having its own probability of occurrence *p[X]*(*x*) = Pr(*X* = *x*), so that

![art](images/Art_P1103.jpg)

A decision is a choice made between several lotteries. For the soil contamination example, there are two lotteries, each one corresponding to a possible action. If we choose to send the soil to a recycling facility, we are certain of the outcome, that is, the soil is not contaminated after its treatment. If we choose to do nothing, there are two possible outcomes; either no significant contaminant was present with a probability of 0.9, or the soil was wrongly left without treatment with a probability of 0.1. These two lotteries can be summarized as

![art](images/Art_P1104.jpg)

The nomenclature employed for ordering preferences is *L[i]* ≻ *L[j]* if we prefer *L[i]* over *L[j]*, *L[i]* ∼ *L[j]* if we are indifferent about *L[i]* and *L[j]*, and *L[i]* ≽ *L[j]* if either we prefer *L[i]* over *L[j]* or are indifferent. The axioms of utility theory^([1](#chapter013.xhtml#footnote_1)) define a rational behavior. Here, we review these axioms following the nomenclature employed by Russell and Norvig:^([2](#chapter013.xhtml#footnote_2))

 
| *Orderability* (Completeness) || A decision maker has well-defined preferences for lotteries so that one of (*L[i]* ≻ *L[j]*), (*L[j]* ≻ *L[i]*), (*L[i]* ∼ *L[j]*) holds. |
| --- | --- |
| *Transitivity* || Preferences over lotteries are *transitive*, so that if (*L[i]* ≻ *L[j]*) and (*L[j]* ≻ *L[k]*), then (*L[i]* ≻ *L[k]*). |
| *Continuity* || If the preferences for lotteries are ordered following (*L[i]* ≻ *L[j]* ≻ *L[k]*), then a probability *p* exists so that \[{*p*, *L[i]*}; {1 − *p*, *L[k]*}\] ∼ *L[j]*. |
| *Substitutability* (Independence) || If two lotteries are equivalent (*L[i]* ∼ *L[j]*), then the lottery *L[i]* or *L[j]* can be substituted by another equivalent lottery *L[k]* following \[{*p*, *L[i]*}; {1 − *p*, *L[k]*}\] ∼ \[{*p*, *L[j]*}; {1 − *p*, *L[k]*}\]. |
| *Monotonicity* || If the lottery *L[i]* is preferred over *L[j]*, *L[i]* ≻ *L[j]*, then for a probability *p* greater than *q*, \[{*p*, *L[i]*}; {1 − *p*, *L[j]*}\] ≻ \[{*q*, *L[i]*}; {1 − *q*, *L[j]*}\]. |
| *Decomposability* || The decomposability property assumes that there is no reward associated with the decision-making process itself, that is, there is no fun in gambling. |

If the preferences over lotteries can be defined following all these axioms, then a rational decision maker should choose the lottery associated with the action that maximizes the expected utility.

 

[*14.3   Utility Functions*](#toc.xhtml#Rh1-57)

The axioms of utility theory are used to define a utility function so that if a lottery *L[i]* is preferred over *L[j]*, then the lottery *L[i]* must have a greater utility than *L[j]*. If we are indifferent about two lotteries, their utilities must be equal. These properties are summarized as

| U(*L[i]*) || \> || U(*L[j]*) || ⇔ || *L[i]* || ≻ || *L[j]* |
| --- | --- | --- | --- | --- | --- | --- |
| U(*L[i]*) || \= || U(*L[j]*) || ⇔ || *L[i]* || ∼ || *L[j]*. |

The *expected utility* of a lottery (see equation 14.1) is defined as the sum of the utility of each possible outcome in the lottery multiplied by its probability,

![art](images/Art_P1105.jpg)

Keep in mind that a utility function defines the relative preferences between outcomes and not the absolute one. It means that we can transform a utility function through an affine function,

U^(tr)(*x*) = *w*U(*x*) + *b*,     *w* > 0,

without changing the preferences of a decision maker. In the case where we multiply a utility function by a negative constant *w* < 0, this is no longer true; instead of maximizing the expected utility, the problem would then consist in *minimizing the expected loss*,

![art](images/Art_P1106.jpg)

![art](images/Art_P1107.jpg)

*Nonlinear utility functions*   We now look at the example of a literal lottery as the term is commonly employed outside the field of utility theory. This lottery is defined like so: you receive $200 if a coin toss lands on heads, and you pay $100 if a coin toss lands on tails. This situation is formalized by the two lotteries respectively corresponding to taking the bet ![art](images/Art_P1108.jpg)or passing ![art](images/Art_P1109.jpg),

![art](images/Art_P1110.jpg)

where you are only certain of the outcome if you choose to pass. The question is, *Do you want to take the bet*? In practice, when people are asked, most would not accept the bet, which contradicts the utility theory principle requiring that one chooses the lottery with the highest expected utility. For this problem,

![art](images/Art_P1111.jpg)

which indicates that a rational decision maker should take the bet. Does this mean that the utility theory does not work or that people are acting irrationally? The answer is no; the reason for this behavior is that utility functions for quantities such as monetary value are typically nonlinear.

 

*Risk averse versus risk seeking*   Instead of directly defining the utility for being in a state *x* while having taken the action *a*, we can define it for continuous quantities such as a monetary value. We define a *value v*(*a*, *x*) associated with the outcome of being in a state *x* while having taken the action *a*, and U(*v*(*a*, *x*)) ≡ U(*v*) is the utility for the value associated with *x* and *a*.

[Figure 14.3](#chapter013.xhtml#Fig_14-3) presents examples of utility functions expressing different risk behaviors. When a utility function is linear with respect to a value *v*, we say that it represents a *risk-neutral* behavior, that is, doubling *v* also doubles U(*v*). In common cases, individuals are not displaying risk-neutral behavior because, for example, gaining or losing $1 will impact behavior differently depending on whether a person has $1 or $1,000,000. A *risk-averse* behavior is characterized by a utility function having a negative second derivative so that the change in utility for a change of value *v* decreases as *v* increases. The consequence is that given the choice between a certain event of receiving $100 and a lottery for which the expected gain is E\[*L*\] = $100, a risk-averse decision maker would prefer the certain event. The opposite is a *risk-seeking* behavior, where there is a small change in the utility function for small values and large changes in the utility function for large values. When facing the same previous choice, a risk-seeking decision maker would prefer the lottery over the certain event.

![art](images/Art_P1112.jpg)

Figure 14.3: Comparison between risk *\-seeking*, *\-neutral*, and *\-averse* behaviors for utility functions.

Let us consider a generic utility function for *v* ∈ (0, 1) so that,

![art](images/Art_P1113.jpg)

[Figure 14.4](#chapter013.xhtml#Fig_14-4) compares the effect of a risk-neutral and a risk-seeking behavior on the conditional expected utilities E\[U(*v*(a*[i]*, *X*))\]. In this example, there is a binary random variable *X* describing the possible state *x* ∈ {1, 2}, where the probability of each outcome depends on an action a*[i]*, and where *v*(a*[i]*, *x*) is the value of being in a state *x* while the action a*[i]* was taken. This illustrative example is designed so that the expected value for both actions are equal, E\[*v*(a[1], *X*)\] = E\[*v*(a[2], *X*)\], but not their variance, var\[*v*(a[1], *X*)\] > var\[*v*(a[2], *X*)\]. With a risk-neutral behavior in (a), the expected utilities remain equal for both actions, E\[U(*v*(a[1], *X*))\] = E\[U(*v*(a[2], *X*))\]. For the risk-averse behavior displayed in (b), the expected utility is higher for action 2 than for action 1, E\[U(*v*(a[2], *X*))\] > E\[U(*v*(a[1], *X*))\], because the variability in value is greater for action 1 than for action 2.

![art](images/Art_P1114.jpg)

Figure 14.4: Discrete case: Comparison of the effect of a risk-neutral and a risk-averse behavior on the expected utility.

[Figure 14.5](#chapter013.xhtml#Fig_14-5) presents the same example, this time for a continuous random variable. The transformation of the probability density function (PDF) from the value space to the utility space is done following the change of variable rule presented in [§3.4](#chapter002.xhtml#Sec_3.4). Again, for a risk-neutral behavior (a), the expected utility is equal, and for a risk-averse behavior (b), the expected utility is higher for action 2 than for action 1, E\[U(*v*(a[2], *X*))\] > E\[U(*v*(a[1], *X*))\], because the variability in the value is greater for action 1 than for action 2.

![art](images/Art_P1115.jpg)

Figure 14.5: Continuous case: Comparison of the effect of a linear (risk-neutral) and a nonlinear (risk-averse) utility function on the expected utility.

People and organizations typically display a risk-averse behavior, which must be considered if we want to properly model optimal decisions. In such a case, an optimal decision a*[i]* is the one that maximizes E\[U(*v*(a*[i]*, *X*))\]. Although such a decision is optimal in the sense of utility theory, it is not the one with the highest expected monetary value. Only a neutral attitude toward risks maximizes the expected value.

For the bet example presented at the beginning of the section, we discussed that the action chosen is typically to not take the bet, even if taking it would result in the highest expected gain. Part of it has to do with the repeatability of the bet; it is a certainty that the gain per play will tend to the expected value as the number of times played increases. Nevertheless, $100 might appear as an important sum to gamble because if a person plays and loses, he or she might not afford to play again to make up for the loss. In the civil engineering context, risk aversion can be seen through a similar scenario, where if someone loses a large amount of money as the consequence of a decision that was rightfully maximizing the expected utility, that person might not keep his or her job long enough to compensate for the current loss with subsequent profitable decisions.

Risk-averse behavior is the reason of being for insurance companies, who have a neutral attitude toward the risks they are providing insurance for. What they do is cover the risks associated with events that would incur small monetary losses in comparison with the size of the company. Insurers seek to diversify the events covered in order to maximize the independence of the probability of each event. The objective is to avoid being exposed to payments so large that it would jeopardize the solvency of the company. Individuals who buy the insurance are risk averse, so they are ready to pay a premium over the expected value in order not to be put in a risk-neutral position. In other words, they accept paying an amount higher than the expected costs to an insurer, who itself has to pay the expected cost because its exposure to losses is spread over thousands if not millions of customers.

  

[*14.4   Value of Information*](#toc.xhtml#Rh1-58)

*Value of information*   quantifies the value associated with the action of gathering additional information about a state *X* in order to reduce the epistemic uncertainty associated with its knowledge. In this section, we will cover two cases: *perfect* and *imperfect* information.

 

[*14.4.1   Value of Perfect Information*](#toc.xhtml#Rh2-78)

In cases where the value of a state *x* ∈ X = {1, 2, ⋯ , X} is imperfectly known, one possible action is to collect additional information about *X*. With the current knowledge of *X* ∼ *p*(*x*), the expected utility of the optimal action *a*^∗ is

![art](images/Art_P1116.jpg)

If we gather perfect information so that *y* = *x* ∈ X, we can then directly observe the true state variable, and the utility of the optimal action becomes

![art](images/Art_P1117.jpg)

However, because *y* has not been observed yet, we must consider all possible observations *y* = *x* weighted by their probability of occurrence so the expected utility conditional on perfect information is

![art](images/Art_P1118.jpg)

Notice how in equation 14.2, the max operation was outside of the sum, whereas in equation 14.3, the max is inside. In equation 14.2, we compute the expected utility where the state is a random variable and for an optimal action that is common for all states. In equation 14.3, we assume that we will know the true state once the observation becomes available, so we will be able to take the optimal action for each state. Consequently, the expected utility is calculated by weighting the utility corresponding to the optimal action for each state, times the probability of occurrence of that state. The *value of perfect information* (VPI) is defined as the difference between the expected utility conditional on perfect information and the expected utility for the optimal action,

VPI(*y*) = U(*ã*^∗) − U(*a*^∗) ≥ 0.

 

Because the expected utility estimated using perfect information E\[U(*ã*^∗, *X*)\] is greater than E\[U(*a*^∗, *X*)\], the VPI(*y*) must be greater or equal to zero. The VPI quantifies the amount of money you should be willing to pay to obtain perfect information. Note that the concepts presented for discrete random variables can be extended for continuous ones by replacing the sums by integrals.

*Soil contamination example*   We apply the concept of the value of perfect information to the soil contamination example. The current expected utility conditional on the optimal action is

![art](images/Art_P1119.jpg)

so the current optimal action is to send the soil to a recycling plant with an associated expected utility of -$100. [Figure 14.6](#chapter013.xhtml#Fig_14-6) presents the decision tree illustrating the calculation for the value of perfect information. The expected utility conditional on perfect information is

![art](images/Art_P1121.jpg)

![art](images/Art_P1124.jpg)

Figure 14.6: Decision tree illustrating the value of perfect information.

Having access to perfect information reduces the expected cost because there is now a probability of 0.9 that the observation will indicate that no treatment is required and only a probability of 0.10 that treatment will be required. Moreover, the possibility of the worst case associated with a false negative where ![art](images/Art_P1122.jpg)is now removed from the possibilities. The value of perfect information is thus

![art](images/Art_P1123.jpg)

It means that we should be willing to pay up to $90 for perfect information capable of indicating whether not the m³ of soil is contaminated.

 

[*14.4.2   Value of Imperfect Information*](#toc.xhtml#Rh2-79)

It is common that observations of state variables are imperfect, so that we want to compute the value of imperfect information. For the case of a discrete state variable *x* that belongs to the set X = {*x*[1], *x*[2], ⋯ , *x*[X]}, the expected costs conditional on imperfect information is obtained by marginalizing over both the possible states *x* ∈ X and the possible observations *y* ∈ X, so that

![art](images/Art_P1125.jpg)

*Soil contamination example*   We apply the concept of the value of imperfect information to the soil contamination example. The conditional probability of an observation *y* conditional on the state *x* is

![art](images/Art_P1126.jpg)

where the observation is perfect if the soil is not contaminated, and the probability of a correct classification is 0.95 if the soil is contaminated.

[Figure 14.7](#chapter013.xhtml#Fig_14-7) depicts the decision tree for calculating the value of information for this example, where the probability of each observation is obtained by marginalizing the joint probability for both observations and states,

![art](images/Art_P1127.jpg)

![art](images/Art_P1130.jpg)

Figure 14.7: Decision tree illustrating the value of imperfect information.

The expected utility conditional on imperfect information is then

![art](images/Art_P1128.jpg)

The *value of information* is now defined by the difference between the expected utility conditional on imperfect information and the expected utility for the optimal action, so that

![art](images/Art_P1129.jpg)

By comparing this result with the value of perfect information that was equal to $90, we see that having observation uncertainty reduces the value of the information.

The reader interested in advanced notions related to rational decisions and utility theory should consult specialized textbooks^([3](#chapter013.xhtml#footnote_3)) such as those by Russell and Norvig or Bertsekas.

 

 

*Exercises*

 
| P14.1 || Explain what quantitative criterion defines a rational decision. |
| --- | --- |
| P14.2 || What are the units of the utility? |
| P14.3 || Explain the concepts associated with risk-neutral, risk-averse, and risk-seeking behaviors. |
| P14.4 || What is the consequence associated with having a nonlinear utility function? |
| P14.5 || Explain the value of perfect and imperfect information. |
| P14.6 || Why is the value of perfect and imperfect information greater than or equal to 0? |
| P14.7 || A structural health monitoring (SHM) system is employed to monitor the state of a structure and can lead to one of the two following actions: either *alert an engineer* (e) or *do nothing* (¬e), *a* ∈ {e, ¬e}. The utility associated with each action and state is![art](images/Art_P1131.jpg)where the state of the structure can be either *normal* (n) or *abnormal* (¬n), *s* ∈ {n, ¬n}. If the SHM system indicates that the probability of being in a normal state is 0.73:a. Compute the expected utility of each action E\[U(*a*, *s*)\] and identify the optimal action to take.b. Compute the *value of perfect information*, that is, the maximal amount you would be willing to pay in order to know with certainty if the state is either n or ¬n. |

 

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter013.xhtml#footnote_ref_1) Von Neumann, J. and O. Morgenstern (1947). *The theory of games and economic behavior*. Princeton University Press.

[²](#chapter013.xhtml#footnote_ref_2) Russell, S. and P. Norvig (2009). *Artificial Intelligence: A Modern Approach* (3rd ed.). Prentice-Hall.

[³](#chapter013.xhtml#footnote_ref_3) Russell, S. and P. Norvig (2009). *Artificial Intelligence: A Modern Approach* (3rd ed.). Prentice-Hall; and Bertsekas, D. P. (2007). *Dynamic programming and optimal control* (4th ed.), Volume 1. Athena Scientific.

 

[*15*](#toc.xhtml#chap-14)

[*Sequential Decisions*](#toc.xhtml#chap-14)

 
| States: || *s* ∈ S = {s[1], s[2], ⋯ , s[S]} |
| --- | --- |
| Actions: || *a* ∈ A = {a[1], a[2], ⋯ , a[A]} |
| Policy: || *π* = {*a*(s[1]), *a*(s[2]), ⋯ *, a*(s[S])} |
| Reward: || *r*(*s, a, s′*) ∈ ℝ |
| Transition model: || *p*(*s′*|*s*, *a*) |

In this chapter, we explore how to make optimal decisions in a sequential context. Sequential decisions differ from the decision context presented in [chapter 14](#chapter013.xhtml) because here, the goal is to select the optimal action to be performed in order to maximize the current reward as well as future ones. In that process, we must take into account that our current action will affect future states as well as future decisions. Let us consider a system that can be in a state *s* ∈ S = {s[1], s[2], ⋯ , s[S]}. The set of actions *a* ∈ A = {a[1], a[2], ⋯ , a[A]} that should be performed given each state of the system is called a *policy*,

*π* = {*a*(s[1]), *a*(s[2]), ⋯ *, a*(s[S])}.

In the context of sequential decisions, the goal is to identify the optimal policy *π*^∗ describing for each possible state of the system the optimal action to take. This task can be formulated as a *reinforcement learning* (RL) problem, where the optimal policy is learned by choosing the actions *a*^∗(*s*) that maximize the *expected utility* over a given *planning horizon*. In order to compute the expected utility, we need a function describing for each set of current state *s*, action *a*, and next state *s′* the associated *reward r*(*s*, *a*, *s′*) ∈ ℝ. In practical cases, it can happen that the reward simplifies to a special case such as *r*(*s*, *a*, *s′*) = *r*(*s*, *a*), *r*(*s*, *a*, *s′*) = *r*(*a*, *s′*), or even *r*(*s*, *a*, *s′*) = *r*(*s*). The last part we need to define is the *Markovian transition model p*(*s′*|s*[j]*, a*[i]*) = Pr(*S′* = s*[k]*|*s* = s*[j]*, a*[i]*), ∀*k* ∈ {1 : S}, that is,

![art](images/Art_P1132.jpg)

**Note:** Reinforcement learning differs from supervised learning because the optimal policy is not learned using other examples of policies. RL also differs from unsupervised learning because the goal is not to discover a structure or patterns in the data.

The *transition model* describes, given the current state of the system s*[j]* and an action taken a*[i]*, the probability of ending in any state *s′* ∈ S at time *t* + 1. Here, the Markov property (see [chapter 7](#chapter006.xhtml)) allows formulating a model where the probability of each state *s′* ∈ S at time *t* + 1 depends on the current state s*[j]* at time *t* and is independent of any previous states. Although sequential decision problems could also be formulated for continuous state variables, *s* ∈ ℝ, in this chapter we restrict ourselves to the discrete case.

**Note:** A transition model is analogous to the concept of a conditional probability table presented in [chapter 11](#chapter010.xhtml).

*Example: Infrastructure maintenance planning*   The notions associated with reinforcement learning and the sequential decision process are illustrated through an application to infrastructure maintenance planning. Let us consider a population of bridges (see [figure 15.1](#chapter014.xhtml#Fig_15-1)) for which at a given time *t*, each bridge can be in a state

![art](images/Art_P1133.jpg)

where 100 percent indicates a perfect condition, and 0 percent corresponds to a state where the damage is so extensive that the structure must be closed. The objective of sequential decision making is to learn the optimal policy *π*^∗(*s*) that identifies among a set of possible actions,

*a* ∈ A = {do nothing (N), maintain (M), replace (R)},

what is the optimal one *a*^∗(*s*) to take at each time, depending on the current condition *s*.

![art](images/Art_P1134.jpg)

Figure 15.1: Contextual illustration of a sequential decision process applied to the problem of infrastructure maintenance planning.

In this example, a bridge condition *s* is rated every year from the results of visual inspections. We assume we have a database D containing the conditions obtained from inspection results for N structures each inspected T times,

![art](images/Art_P1135.jpg)

Each line in this database corresponds to a given structure and each column corresponds to a given time *t* ∈ {1, 2, ⋯ , T}. [Figure 15.2](#chapter014.xhtml#Fig_15-2) presents an example for N = 15 bridges and time histories of length T = 20. One of them has been highlighted with a thicker red line to better visualize how a structure transits from state to state through time. In this data set, the action taking place at each time *t* is *a* = do nothing. We can use this data set to estimate the parameters of the Markovian transition model *p*(*s*[*t*+1]|*s[t]*, *a* = do nothing) by employing the maximum likelihood estimate for each transition probability (see [§11.4](#chapter010.xhtml#Sec_11.4)). The maximum likelihood estimate (MLE) corresponds to the number of structures that, from a state *i* at time *t*, transitioned to a state *j* at *t* + 1, divided by the number of structures that started from a state *i* at time *t*,

![art](images/Art_P1137.jpg)

where {s*[i]*, s*[j]*} ∈ S² and the # symbol describes the number of elements in a set. These results are stored in a *transition matrix*,

![art](images/Art_P1138.jpg)

where each element \[ \]*[ij]* corresponds to the probability of landing in state *s*[*t*+1] = s*[j]* given that the system is currently in state *s[t]* = s*[i]*. This matrix is analogous to the transition matrix we have seen in [§12.2](#chapter011.xhtml#Sec_12.2). In the case of infrastructure degradation, the transition matrix has only zeros below its main diagonal because, without intervention, a bridge’s condition can only decrease over time, so a transition from *s[t]* = s*[i]* → *s*[*t*+1] = s*[j]* can only have a nonzero probability for *j* ≥ *i*.

![art](images/Art_P1136.jpg)

Figure 15.2: Example of bridge condition time histories.

For maintenance and replacement actions, the transition matrix can be defined deterministically as

![art](images/Art_P1139.jpg)

where from a current state *s[t]* = s*[i]*, the state becomes *s*[*t*+1] = s[*i*−1]. For example, if at a time *t* the state is *s[t]* = s[3] = 60%, the maintenance action will result in the state *s*[*t*+1] = s[2] = 80%. Note that if the state is *s[t]* = s[1] = 100%, it remains the same at *t* + 1. For a replacement action, no matter the initial state at *t*, the next state becomes *s*[*t*+1] = s[1] = 100% so,

![art](images/Art_P1140.jpg)

 

In order to identify the optimal policy *π*^∗, we need to define the *reward r*(*s*, *a*, *s′*). Here, we assume that the reward simplifies to *r*(*s*, *a*) = *r*(*s*) + *r*(*a*), so it is only a function of the state *s* and the action *a*. For a given structure, the reward *r*(*s*) is estimated as a function of the number of users quantified through the *annual average daily traffic flow* (AADTF = 10⁵ users/day), times a value of $3/user, times the capacity of the bridge as a function of its condition. The capacity is defined as *c*(S) = {1, 1, 1, 0.90, 0.75, 0}, and the associated rewards are

**Note:** Here the value of $3/user does not necessarily represent the direct cost per user as collected by a toll booth. It instead corresponds to the indirect value of the infrastructure for the society.

| *r*(S)  || \= || 10⁵ users/day · 365 day · $3/user · *c*(S) |
| --- | --- | --- |
| \= || {109.5, 109.5, 109.5, 98.6, 82.1, 0}$*M*. |

The rewards for actions *r*(*a*) correspond to a cost, so their values are lesser than or equal to zero,

*r*(A) = {0, −5, −20}$*M*.

For the context of reinforcement learning, we can generalize the example above by introducing the concept of an *agent* interacting with its *environment*, as depicted in [figure 15.3](#chapter014.xhtml#Fig_15-3). In the context of the previous example, the environment is the population of structures that are degrading over time, and the agent is the hypothetical entity acting with the intent of maximizing the long-term accumulation of rewards. The environment interacts with the agent by defining, for each time *t*, the state *s[t]* of the system and the reward for being in that state *s*, taking a given action *a*, and ending in the next state *s′*. The agent perceives the environment’s state and selects an action *a*, which in turn can affect the environment and thus the state at time *t* + 1.

![art](images/Art_P1141.jpg)

Figure 15.3: Schematic representation of the interaction between an agent and its environment.

This chapter explores the task of identifying the optimal policy *π*^∗(*s*) describing the optimal actions *a*^∗ to be taken for each state *s*. This task is first formulated in [§15.1](#chapter014.xhtml#Sec_15.1) using the model-based method known as the *Markov decision process*. Building on this method, [§15.2](#chapter014.xhtml#Sec_15.2) then presents two model-free reinforcement learning methods: *temporal difference* and *Q-learning*.

 

[*15.1   Markov Decision Process*](#toc.xhtml#Rh1-60)

**Finite planning horizon**

Nonstationary policy

**Infinite planning horizon**

Stationary policy

In order to formulate a *Markov decision process* (MDP), we need to define a *planning horizon* over which the utility is estimated. Planning horizons may be either finite or infinite. With a *finite planning horizon*, the rewards are considered over a fixed period of time. In such a case, the optimal policy *π*^∗(*s*, *t*) is nonstationary because it depends on the time *t*. For the infrastructure maintenance example, a finite planning horizon could correspond to the case where we want to identify the optimal actions to take over the next T = 20 years, after which we know a structure is going to be demolished. The optimal action for a state *s[t]* = 40 % would then not be the same whether we are at *t* = 1 or at *t* = 19. For an *infinite planning horizon*, the rewards are considered over an infinite period of time. In such a case, the optimal policy *π*^∗(*s*) is *stationary* as it does not depend on the time *t*. It means that at any time *t*, the optimal action to take is only a function of the current state *s* we are in. In this chapter, we only study problems associated with an infinite planning horizon, as they allow identifying a stationary optimal policy *π*^∗(*s*) rather than one which depends on time *π*^∗(*s*, *t*), as is the case with a finite planning horizon.

 

[*15.1.1   Utility for an Infinite Planning Horizon*](#toc.xhtml#Rh2-80)

The *utility* associated with an infinite planning horizon is defined as the reward for being in the current state plus the sum of the discounted rewards for all future states,

![art](images/Art_P1142.jpg)

**Note:** Some references employ the term *utility*, others, the term *value* to refer to the sum of discounted rewards.

**Note:** In this subsection, the notation is simplified by assuming that *r*(*s*, *a*, *s′*) = *r*(*s*). Nevertheless, the same reasoning holds for the general case where the reward is *r*(*s*, *a*, *s′*).

For a *discount factor γ* ∈ (0, 1\], the discounted sum of rewards over an infinite planning horizon is a finite quantity. This is an essential property because without a discount factor, we could not compare the performance of actions that would each have infinite utilities. In the special case where there is a *terminal state* for which the problem stops, the discount factor can be taken as *γ* = 1 because it will be possible to compute a finite estimate for the utility. Note that for the infrastructure maintenance planning example, there is no terminal state and the discount factor can be interpreted as an interest rate using the transformation ![art](images/Art_P1143.jpg). The issue with our planning problem is that we do not know yet what will be the future states *s*[*t*\=1], *s*[*t*\=2], ⋯ , so we cannot compute the utility using equation 15.1. Instead, the *expected utility* for being in the state *s*[0] is computed as

![art](images/Art_P1144.jpg)

In equation 15.2, the probability of each state *s* at each time *t >* 0 is estimated recursively using the transition model *p*(*s*[*t*+1]|*s[t]*, *a*), where at each step, the action taken is the one defined in the policy *π*(*s*). Here, we choose to simplify the notation by writing the expected utility as E\[U(*s*, *π*)\] ≡ U(*s*, *π*). Moreover, the notation U(*s*, *π*) ≡ U(*s*) is employed later in this chapter in order to further simplify the notation by making the dependency on the policy *π* implicit.

For a state *s*, the optimal policy *π*^∗(*s*) is defined as the action *a* that maximizes the expected utility,

![art](images/Art_P1145.jpg)

The difficulty is that, in this definition, the optimal policy *π*^∗(*s*) appears on both sides of the equality. The next two sections show how this difficulty can be tackled using *value* and *policy iteration*.

 

[*15.1.2   Value Iteration*](#toc.xhtml#Rh2-81)

Equation 15.2 described the expected utility for being in a state *s*, where the dependence on the actions *a* was implicit. The definition of this relationship with the explicit dependence on the actions is described by the *Bellman*^([1](#chapter014.xhtml#footnote_1)) equation,

![art](images/Art_P1146.jpg)

where the optimal action *a*^∗(*s*) is selected for each state through the max operation. Again, the difficulty with this equation is that the expected utility of a state U(*s*) appears on both sides of the equality. One solution to this problem is to employ the *value iteration* algorithm where we go from an iteration *i* to an iteration *i* + 1 using the *Bellman update step*,

![art](images/Art_P1147.jpg)

**Note:** The symbol ← indicates that the quantity on the left-hand side is recursively updated using the terms on the right-hand side, which are themselves depending on the updated term.

In order to use the Bellman update, we start from the initial values at iteration *i* = 0, for example, U^((0))(*s*) = 0, and then iterate until we converge to a steady state. The value iteration algorithm is guaranteed to converge to the exact expected utilities U^((*∞*))(*s*) if an infinite number of iterations is employed. The optimal actions *a*^∗(*s*) identified in the process for each state *s* define the optimal policy *π*^∗. The sequence of steps for value iteration are detailed in [algorithm 10](#chapter014.xhtml#Tab_10).

![art](images/Art_P1149.jpg)

*Example: Infrastructure maintenance planning*   We now apply the value iteration algorithm to the infrastructure maintenance example defined at the beginning of this chapter. The last parameters that need to be defined are the convergence criterion *η* = 10^(−3) and the discount factor taken as *γ* = 0.97, which corresponds to an interest rate of 3 percent. Starting from U^((0))(S) = {0, 0, 0, 0, 0, 0} $*M*, we perform iteratively the Bellman update step for each state *s*,

![art](images/Art_P1148.jpg)

**Algorithm 10:** Value iteration

![art](images/Art_P1150.jpg)

**Example setup**

![art](images/Art_P1151.jpg)

where we choose the optimal action *a*^∗ leading to the maximal expected utility. The expected utilities for two first and last iterations are

![art](images/Art_P1152.jpg)

 

Here, we explicitly show the calculations made to go from U^((1))(100%) = $109.5*M* → U^((2))(100%) = $222.5*M*,

![art](images/Art_P1153.jpg)

where the optimal action to perform if you are in state *s* = 100% is *π*^(∗(2))(100%) = *a*^∗ = do nothing. In order to complete a full iteration, this operation needs to be repeated for each states *s* ∈ S. [Figure 15.4](#chapter014.xhtml#Fig_15-4) presents the evolution of the expected utility of each state as a function of the iteration number. Note how the expected utilities converge to stationary values for all state variables. The corresponding optimal policy is

![art](images/Art_P1154.jpg)

![art](images/Art_P1155.jpg)

Figure 15.4: Value iteration algorithm converging to stationary expected utilities.

[Figure 15.5](#chapter014.xhtml#Fig_15-5) presents the expected utility for each action and state obtained using the value iteration algorithm. For each state, the expected utility corresponding to the optimal action is highlighted with a red border.

![art](images/Art_P1156.jpg)

Figure 15.5: Expected utility for each action and state obtained using the value iteration algorithm. The expected utilities of the optimal action is highlighted with a red border.

In the Bellman update step of the value iteration algorithm, the max operation is computationally expensive if the number of possible actions A is large. The difficulty is solved by the *policy iteration* algorithm.

 

[*15.1.3   Policy Iteration*](#toc.xhtml#Rh2-82)

Remember that a policy *π* = {*a*(s[1]), *a*(s[2]), ⋯ , *a*(s[S])} defines an action to be taken for each state *s* ∈ S. For the calculation of the expected utility of each state *s*, we can reduce the computational burden of the Bellman update step in equation 15.4 by replacing the max operation with the action *a* defined by the policy *π*^((*i*))(*s*),

![art](images/Art_P1157.jpg)

If we employ equation 15.5 instead of equation 15.4 to update the expected utility, we are required to perform only one sum rather than A sums, where A corresponds to the number of possible actions. Once the expected utility has been calculated for each state, the policy can be optimized using

![art](images/Art_P1158.jpg)

We then repeat the successive steps of first calculating the expected utility with the value iteration algorithm using a fixed policy, and then update the policy. The details of the policy iteration procedure are presented in [algorithm 11](#chapter014.xhtml#Tab_11), where the *policy evaluation* step corresponds to the value iteration performed while employing equation 15.5 instead of equation 15.4. Note that identifying an optimal policy using the policy or the value iteration algorithm leads to the same results, except that policy iteration is computationally cheaper.

**Algorithm 11:** Policy iteration

![art](images/Art_P1159.jpg)

![art](images/Art_P1183.jpg)

*Example: Infrastructure maintenance planning*   Starting from U^((0))(S) = {0, 0, 0, 0, 0, 0} $*M*, we perform the policy iteration algorithm where the Bellman update step in the policy evaluation is defined by equation 15.5, where the optimal action *a* = *π*^((*i*))(*s*) is defined by the optimal policy at iteration *i*. The expected utilities for the two first and last iterations are

![art](images/Art_P1160.jpg)

and their corresponding policies are

 
| *π*^((0))(S) || \= || {N, N, N, N, N, N} |
| --- | --- | --- |
| *π*^((1))(S) || \= || {M, M, R, R, R, R} |
| *π*^((2))(S) || \= || {N, N, M, M, R, R} |
|  || ⋮ ||  |
| *π*^∗(S) = *π*^((6)) = *π*^((5))(S) || \= || {N, M, M, M, R, R}. |

![art](images/Art_P1161.jpg)

Here, we explicitly show the calculations made to go from the policy iteration loop 1 → 2, U^((1))(100%) = $2063*M* → U^((2))(100%) = $3483*M*, within which 351 policy evaluation calls are required,

![art](images/Art_P1163.jpg)

Once the policy evaluation loop is completed, the policy must be updated. Here, we explicitly look at the specific iteration *π*^((1))(100%) = M → *π*^((2))(100%) = N, so that

![art](images/Art_P1164.jpg)

 

The policy iteration converges in five loops and it leads to the same optimal policy as the value iteration,

![art](images/Art_P1165.jpg)

Further details as well as advanced concepts regarding Markov decision processes can be found in the textbooks by Russell and Norvig,^([2](#chapter014.xhtml#footnote_2)) and by Bertsekas.^([3](#chapter014.xhtml#footnote_3))

 

[*15.1.4   Partially Observable Markov Decision Process*](#toc.xhtml#Rh2-83)

**MDP**

![art](images/Art_P1168.jpg)

**POMDP**

![art](images/Art_P1169.jpg)

One hypothesis with the Markov decision process presented in the previous section is that state variables are exactly observed, so that at the current time *t*, one knows in what state *s* the system is in. In such a case, the optimal action defined by the policy *π*(*s*) can be directly selected. For the case we are now interested in, *s* is a hidden-state variable, and the observed state *y* is defined through the conditional probability *p*(*y*|*s*). This problem configuration is called a *partially observable MDP* (POMDP). The challenge is that at any time *t*, you do not observe exactly what is the true state of the system; consequently, you cannot simply select the optimal action from the policy *π*(*s*).

Because the state is observed with uncertainty, at each time *t*, we need to describe our knowledge of the state using a probability mass function *p*(*s*) = {Pr(*S* = s[1]), Pr(*S* = s[2]), ⋯ , Pr(*S* = s[S])}. Given the PMF *p*(*s*) describing our current knowledge of *s*, an action taken *a*, and an observation *y* ∈ S, then the probability of ending in any state *s′* ∈ S at time *t* + 1 is given by

![art](images/Art_P1166.jpg)

With the MDP, the policy *π*(*s*) was a function of the state we are in; with the POMDP we need to redefine the policy as being a function of the probability of the state *π*(*p*(*s*)) we are in. In the context of an MDP, the policy can be seen as a function defined over discrete variables. With a POMDP, if there are S possible states, *π*(*p*(*s*)) is a function of a continuous domain with S − 1 dimensions. This domain is continuous because Pr(*S* = *s*) ∈ (0, 1), and there are S − 1 dimensions because of the constraint requiring that ![art](images/Art_P1167.jpg).

 

Because the policy is now a function of probabilities defined in a continuous domain, the value and policy iteration algorithms presented for an MDP are not directly applicable. One particularity of the POMDP is that the set of actions now includes additional information gathering through observation. The reader interested in the details of value and policy-iteration algorithms for POMDP should refer to specialized literature such as the paper by Kaelbling, Littman, and Cassandra.^([4](#chapter014.xhtml#footnote_4)) Note that solving a POMDP is significantly more demanding than solving an MDP. For practical applications, the exact solution of a POMDP is often intractable and we have to resort to approximate methods.^([5](#chapter014.xhtml#footnote_5))

 

[*15.2   Model-Free Reinforcement Learning*](#toc.xhtml#Rh1-61)

The Markov decision process presented in the previous section is categorized as a *model-based* method because it requires knowing the model of the environment that takes the form of the transition probabilities *p*(*s′*|*s*, *a*). In some applications, it is not possible or practical to define such a model because the number of states can be too large, or can be continuous so that the definition of transition probabilities is not suited. Model-free reinforcement learning methods learn from the interaction between the agent and the environment, as depicted in [figure 15.3](#chapter014.xhtml#Fig_15-3). This learning process is typically done by subjecting the agent to multiple *episodes*. In this section, we will present two *model-free* methods suited for such a case: *temporal difference learning* and *Q-learning*.

 

[*15.2.1   Temporal Difference Learning*](#toc.xhtml#Rh2-84)

The quantity we are interested in estimating is E\[U(*s*, *π*)\] ≡ U(*s*, *π*) ≡ U(*s*), that is, the expected utility for being in a state *s*. We defined in [§15.1.1](#chapter014.xhtml#Sec_15.1.1) that the utility is the sum of the discounted rewards,

![art](images/Art_P1170.jpg)

obtained while following a policy *π* so that *a[t]* = *π*(*s[t]*). Moreover, we saw in [§6.5](#chapter005.xhtml#Sec_6.5) that we can estimate an expected value using the Monte Carlo method. Here, in the context where our agent can interact with the environment over multiple episodes, we can estimate U(*s*, *π*) by taking the average over a set of realizations of U(*s*, *π*).

In a general manner, the average *x*[T] of a set {*x*[1], *x*[2], ⋯ , *x*[T]} can be calculated incrementally by following

![art](images/Art_P1171.jpg)

 

[Figure 15.6](#chapter014.xhtml#Fig_15-6) presents an example of an application of the incremental average estimation for a set of T = 500 realizations of *x[t]* : *X* ∼ N(*x*; 3, 1). We can apply the same principle for the incremental estimation of the expected utility so that

![art](images/Art_P1172.jpg)

where N(*s*) is the number of times a state has been visited. Estimating U(*s*) through Monte Carlo sampling is limited to problems having a terminal state and requires evaluating the utilities over entire episodes. *Temporal difference* (TD) learning,^([6](#chapter014.xhtml#footnote_6)) allows going around these requirements by replacing the explicit utility calculation U^((*i*))(*s*) by the *TD-target* defined as *r*(*s*, *a*, *s′*) + *γ*U^((*i*))(*s′*), so that equation 15.6 can be rewritten as

![art](images/Art_P1173.jpg)

![art](images/Art_P1174.jpg)

Figure 15.6: The incremental calculation of an average for a set {*x*[1], *x*[2], ⋯ , *x*[500]}, *x[t]* : *X* ∼ N(*x*; 3, 1).

Temporal difference learns by updating recursively the *state-utility* function U^((*i*+1))(*s*) by taking the difference in expected utilities estimated at consecutive times while the agent interacts with the environment.

In equation 15.7, *α* is the *learning rate* defining how much is learned from the TD update step. Typically, we want to employ a learning rate that is initially large so our poor initial values for U(*s*) are strongly influenced by the TD updates and then decrease *α* as a function of the number of times a particular set of state and action has been seen by the agent. In order to ensure the convergence of the state-utility function, the learning rate should satisfy the two following conditions,

![art](images/Art_P1175.jpg)

A common learning rate function that satisfies both criteria is

![art](images/Art_P1176.jpg)

where N(*s*, *a*) is the number of times a set of state and action has been visited and *c* ∈ ℝ^+ is a positive constant.

The TD-learning update step presented in equation 15.7 defines the behavior of a *passive agent*, that is, an agent, who is only evaluating the *state-utility function* for a predefined policy *π*. In other words, in its current form, TD-learning is suited to estimate U(*s*) given that we already know the policy *π*(*s*) we want the agent to follow. In practice, this is seldom the case because instead, we want an *active agent*, who will learn both the expected utilities and the optimal policy. The next section presents *temporal difference Q-learning*, a common active reinforcement learning method capable of doing both tasks simultaneously.

 

[*15.2.2   Temporal Difference Q-Learning*](#toc.xhtml#Rh2-85)

*Temporal difference Q-learning*^([7](#chapter014.xhtml#footnote_7)) (often referred to as simply Q-learning) is an *active reinforcement learning* method that consists in evaluating the *action-utility function* Q(*s*, *a*), from which both the optimal policy

![art](images/Art_P1177.jpg)

and the resulting expected utilities

![art](images/Art_P1178.jpg)

can be extracted. Analogously to equation 15.7, the TD update step for the *action-utility function* Q(*s*, *a*) is defined as

![art](images/Art_P1179.jpg)

Equation 15.8 describes the behavior of an *active agent*, which updates Q(*s*, *a*) by looking one step ahead and employing the action *a′* that maximizes Q(*s′*, *a′*). Q-learning is categorized as an *off-policy* reinforcement learning method because the optimal one-step look-ahead action *a′* employed to update Q(*s*, *a*) is not necessarily the action that will be taken by the agent to transit to the next state. This is because in order to learn efficiently, it is necessary to find a tradeoff between *exploiting* the current best policy and *exploring* new policies.

While learning the action-utility function using Q-learning, one cannot only rely on the currently optimal action *a*^∗ = *π*^∗(*s*) in order to transit between successive states, *s* and *s′*. This is because such a *greedy* agent that always selects the optimal action is likely to get stuck in a local maxima because of the poor initial estimates for Q(*s*, *a*). One simple solution is to employ the *ϵ*\-greedy strategy, which consists in selecting the action randomly with probability *ϵ*(N(*s*)) and otherwise selecting the action from the optimal policy *π*^∗(*s*). Here, N(*s*) is again the number of times a state has been visited. Therefore, an *ϵ*\-greedy agent selects an action following

![art](images/Art_P1180.jpg)

where *u* is a sample taken from a uniform distribution U(0, 1). *ϵ*N(*s*)) should be defined so that it tends to zero when the number of times a state has been visited N(*s*) → ∞. [Algorithm 12](#chapter014.xhtml#Tab_12) details the sequence of steps for temporal difference Q-learning.

**Algorithm 12:** Temporal difference Q-learning

![art](images/Art_P1181.jpg)

![art](images/Art_P1183.jpg)

*Example: Infrastructure maintenance planning*   We revisit the infrastructure maintenance example, this time using the temporal difference Q-learning algorithm. The problem definition is identical to that in [§15.1](#chapter014.xhtml#Sec_15.1), except that we now initialize the action-utility functions as Q^((0))(*s*, *a*) = $0 *M*, ∀{*s* ∈ S, *a* ∈ A}. Also, we define the iteration-dependent learning schedule as

![art](images/Art_P1182.jpg)

and the exploration schedule by

![art](images/Art_P1184.jpg)

where *c* = 70. We choose to learn over a total of 500 episodes, each consisting in 100 time steps. For each new episode, the state is initialized randomly. [Figure 15.7](#chapter014.xhtml#Fig_15-7) presents the evolution of the expected utility U(*s*) for each state as a function of the number of episodes. Given that we employed 500 episodes, each comprising 100 steps, the total number of iterations is 50,000. For the last iteration, the expected utilities are

U^((50 000))(S) = {3640, 3635, 3630, 3615, 3592, 3510} $*M*.

![art](images/Art_P1186.jpg)

Figure 15.7: Expected utility convergence for the Q-learning algorithm.

Those values are identical to the ones obtained using either the policy- or value-iteration algorithm in [§15.1](#chapter014.xhtml#Sec_15.1). Analogously, the optimal policy derived from the action-utility function is also identical and corresponds to

![art](images/Art_P1185.jpg)

[Figure 15.8](#chapter014.xhtml#Fig_15-8) present *ϵ*(N(*s*)) as a function of the number of episodes, that is, for each state, the probability that the agent selects a random action. For the learning rate *α*N(*s*, *a*)), which is not displayed here, there are three times as many curves because it also depends on the action *a*.

![art](images/Art_P1187.jpg)

Figure 15.8: Evolution of *ϵ*(N(*s*)) for each state *s* as a function of the number of episodes.

For this simple infrastructure maintenance example, using an active reinforcement learning method such as Q-learning is not beneficial in comparison with passive methods such as the policy- or value-iteration algorithm in [§15.1](#chapter014.xhtml#Sec_15.1). Nevertheless, active reinforcement learning becomes necessary for more advanced contexts where the number of states is large and often continuous. The reader interested in learning more about topics related to *on-policy* reinforcement learning methods such as *sarsa*, advanced exploration strategies, efficient action-utility function initialization, as well as continuous *function approximation* for Q-learning, should consult dedicated textbooks such as the one by Sutton and Barto.^([8](#chapter014.xhtml#footnote_8))

 

 

*Exercises*

 
| P15.1 || What is a policy, and why is it stationary for an infinite planning horizon and nonstationary for a finite one? |
| --- | --- |
| P15.2 || Explain the Markov decision process (MDP). |
| P15.3 || What does the Markov hypothesis imply in the context of an MDP? |
| P15.4 || Explain the discount factor and what happens if *γ* = 1. |
| P15.5 || How is an optimal policy defined in the context of an MDP? |
| P15.6 || Why do we need to employ iterative algorithms to evaluate the Bellman equation? |
| P15.7 || What is the advantage of the policy-iteration algorithm in comparison with value iteration? |
| P15.8 || Explain the differences between model-based and model-free reinforcement learning. |
| P15.9 || Using the same setup as the bridge maintenance example presented in this chapter:a. Employ the data set in MDP\_bridge.csv to estimate the transition matrix for the Markovian degradation model of structures for the action *a* = do nothing.b. Implement a policy-iteration algorithm and, using the discount factor *γ* = 0.95, identify the optimal action for each state *s* ∈ S and its corresponding expected utility.c. Implement a temporal difference Q-learning algorithm to reproduce the results you obtained in (b). |

\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#chapter014.xhtml#footnote_ref_1) Bellman, R. (1957). A Markovian decision process. *Journal of Mathematics and Mechanics 6*(5), 679–684.

[²](#chapter014.xhtml#footnote_ref_2) Russell, S. and P. Norvig (2009). *Artificial Intelligence: A Modern Approach* (3rd ed.). Prentice-Hall.

[³](#chapter014.xhtml#footnote_ref_3) Bertsekas, D. P. (2007). *Dynamic programming and optimal control* (4th ed.), Volume 1. Athena Scientific.

[⁴](#chapter014.xhtml#footnote_ref_4) Kaelbling, L. P., M. L. Littman, and A. R. Cassandra (1998). Planning and acting in partially observable stochastic domains. *Artificial Intelligence 101*(1), 99–134.

[⁵](#chapter014.xhtml#footnote_ref_5) Hauskrecht, M. (2000). Value-function approximations for partially observable Markov decision processes. *Journal of Artificial Intelligence Research 13*(1), 33–94.

[⁶](#chapter014.xhtml#footnote_ref_6) Sutton, R. S. (1988). Learning to predict by the methods of temporal differences. *Machine Learning 3*(1), 9–44.

[⁷](#chapter014.xhtml#footnote_ref_7) Watkins, C. J. and P. Dayan (1992). Q-learning. *Machine Learning 8*(3–4), 279–292.

[⁸](#chapter014.xhtml#footnote_ref_8) Sutton, R. S. and A. G. Barto (2018). *Reinforcement learning: An introduction* (2nd ed.). MIT Press.

 

[*Bibliography*](#toc.xhtml#bib-1)

Abramowitz, M. and I. A. Stegun (1972). *Handbook of mathematical functions with formulas, graphs, and mathematical table*. National Bureau of Standards, Applied Mathematics.

Adelchi, A. and A. W. Bowman (1990). A look at some data on the Old Faithful geyser. *Journal of the Royal Statistical Society. Series C (Applied Statistics) 39*(3), 357–365.

Ang, A. H.-S. and W. H. Tang (1975). *Probability concepts in engineering planning and decision*, Volume 1—Basic Principles. John Wiley.

Armijo, L. (1966). Minimization of functions having Lipschitz continuous first partial derivatives. *Pacific Journal of Mathematics 16*(1), 1–3.

Bar-Shalom, Y., X. Li, and T. Kirubarajan (2001). *Estimation with applications to tracking and navigation: Theory algorithms and software*. John Wiley & Sons.

Bellman, R. (1957). A Markovian decision process. *Journal of Mathematics and Mechanics 6*(5), 679–684.

Ben-Akiva, M. E. and S. R. Lerman (1985). *Discrete choice analysis: Theory and application to travel demand*. MIT Press.

Bertsekas, D. P. (2007). *Dynamic programming and optimal control* (4th ed.), Volume 1. Athena Scientific.

Bertsekas, D. P., A. Nedi, and A. E. Ozdaglar (2003). *Convex analysis and optimization*. Athena Scientific.

Bishop, C. M. (2006). *Pattern recognition and machine learning*. Springer.

Blom, H. A. P. and Y. Bar-Shalom (1988). The interacting multiple model algorithm for systems with Markovian switching  coefficients. *IEEE Transactions on Automatic Control 33*(8), 780–783.

Box, G. E. P. and G. C. Tiao (1992). *Bayesian inference in statistical analysis*. Wiley.

Brooks, S., A. Gelman, G. Jones, and X.-L. Meng (2011). *Handbook of Markov Chain Monte Carlo*. CRC Press.

Brynjarsdóttir, J. and A. O’Hagan (2014). Learning about physical parameters: The importance of model discrepancy. *Inverse Problems 30*(11), 114007.

Burnham, K. P. and D. R. Anderson (2002). *Model selection and multimodel inference: A practical information-theoretic approach* (2nd ed.). Springer.

Chong, E. K. P. and S. H. Zak (2013). *An introduction to optimization* (4th ed.). Wiley.

Dauphin, Y. N., R. Pascanu, C. Gulcehre, K. Cho, S. Ganguli, and Y. Bengio (2014). Identifying and attacking the saddle point problem in high-dimensional non-convex optimization. In *Advances in Neural Information Processing Systems*, 27, 2933–2941.

Del Moral, P. (1997). Non-linear filtering: interacting particle resolution. *Comptes Rendus de l’Académie des Sciences—Series I—Mathematics 325*(6), 653–658.

Dempster, A. P., N. M. Laird, and D. B. Rubin (1977). Maximum likelihood from incomplete data via the EM algorithm. *Journal of the Royal Statistical Society. Series B (methodological) 39*(1), 1–38.

Diard, J., P. Bessiere, and E. Mazer (2003). A survey of probabilistic models using the Bayesian programming methodology as a unifying framework. In *International Conference on Computational Intelligence, Robotics and Autonomous Systems (IEEE-CIRAS)*, Singapore.

Duvenaud, D. (2014). *Automatic model construction with Gaussian processes*. PhD thesis, University of Cambridge.

Ebden, M. (2008, August). Gaussian processes: A quick introduction. *arXiv preprint (1505.02965)*.

Friedman, J., T. Hastie, H. Höfling, and R. Tibshirani (2007). Pathwise coordinate optimization. *The Annals of Applied Statistics 1*(2), 302–332.

 

Gaudot, I., L. H. Nguyen, S. Khazaeli, and J.-A. Goulet (2019, May). OpenBDLM, an open-source software for structural health monitoring using bayesian dynamic linear models. In *13th Proceedings from the 13th International Conference on Applications of Statistics and Probability in Civil Engineering (ICASP)*.

Gelman, A., J. B. Carlin, H. S. Stern, and D. B. Rubin (2014). *Bayesian data analysis* (3rd ed.). CRC Press.

Gelman, A. and D. B. Rubin (1992). Inference from iterative simulation using multiple sequences. *Statistical Science 7*(4), 457–472.

Ghahramani, Z. (2001). An introduction to hidden Markov models and Bayesian networks. *International Journal of Pattern Recognition and Artificial Intelligence 15*(1), 9–42.

Ghahramani, Z. (2004). Unsupervised learning. In *Advanced lectures on machine learning*, Volume 3176, pp. 72–112. Springer.

Ghahramani, Z. and G. E. Hinton (1996). Parameter estimation for linear dynamical systems. Technical Report CRG-TR-96-2, University of Toronto, Dept. of Computer Science.

Gibbs, B. P. (2011). *Advanced Kalman filtering, least-squares and modeling: A practical handbook*. Wiley.

Goodfellow, I., Y. Bengio, and A. Courville (2016). *Deep learning*. MIT Press.

Goulet, J.-A. (2017). Bayesian dynamic linear models for structural health monitoring. *Structural Control and Health Monitoring 24*(12), 1545–2263.

Goulet, J.-A., C. Michel, and A. Der Kiureghian (2015). Data-driven post-earthquake rapid structural safety assessment. *Earthquake Engineering & Structural Dynamics 44*(4), 549–562.

Harrison, P. J. and C. F. Stevens (1976). Bayesian forecasting. *Journal of the Royal Statistical Society: Series B (Methodological) 38*(3), 205–228.

Hastings, W. K. (1970). Monte Carlo sampling methods using Markov chains and their applications. *Biometrika 57*(1), 97–109.

Hauskrecht, M. (2000). Value-function approximations for partially observable Markov decision processes. *Journal of Artificial Intelligence Research 13*(1), 33–94.

 

Hoerl, A. E. and R. W. Kennard (1970). Ridge regression: Biased estimation for nonorthogonal problems. *Technometrics 12*(1), 55–67.

Hotelling, H. (1933). Analysis of a complex of statistical variables into principal components. *Journal of Educational Psychology 24*(6), 417.

Jermyn, I. H. (2005). Invariant Bayesian estimation on manifolds. *The Annals of Statistics 33*(2), 583–605.

Kaelbling, L. P., M. L. Littman, and A. R. Cassandra (1998). Planning and acting in partially observable stochastic domains. *Artificial Intelligence 101*(1), 99–134.

Kalman, R. E. (1960). A new approach to linear filtering and prediction problems. *Transactions of the ASME–Journal of Basic Engineering 82*(Series D), 35–45.

Kennedy, M. C. and A. O’Hagan (2001). Bayesian calibration of computer models. *Journal of the Royal Statistical Society: Series B (Statistical Methodology) 63*(3), 425–464.

Kim, C.-J. and C. R. Nelson (1999). *State-space models with regime switching: Classical and Gibbs-sampling approaches with applications*. MIT Press.

Kreyszig, E. (2011). *Advanced engineering mathematics* (10th ed.). Wiley.

Ljung, L. (1979). Asymptotic behavior of the extended Kalman filter as a parameter estimator for linear systems. *IEEE Transactions on Automatic Control 24*(1), 36–50.

Lloyd, S. (1982). Least squares quantization in PCM. *IEEE Transactions on Information Theory 28*(2), 129–137.

Lowen, A. C. and J. Steel (2014). Roles of humidity and temperature in shaping influenza seasonality. *Journal of Virology 88*(14), 7692–7695.

MacKay, D. J. C. (1998). Introduction to Monte Carlo methods. In *Learning in graphical models*, pp. 175–204. Sprigner.

MacKay, D. J. C. (2003). *Information theory, inference, and learning algorithms*. Cambridge University Press.

McFadden, D. (2001). Economic choices. *American Economic Review 91*(3), 351–378.

 

Metropolis, N., A. W. Rosenbluth, M. N. Rosenbluth, A. H. Teller, and E. Teller (1953). Equation of state calculations by fast computing machines. *The Journal of Chemical Physics 21*(6), 1087–1092.

Murphy, K. P. (1998). Switching Kalman filters. Citeseer.

Murphy, K. P. (2002). *Dynamic Bayesian networks: representation, inference and learning*. PhD thesis, University of California, Berkeley.

Murphy, K. P. (2007). Conjugate Bayesian analysis of the Gaussian distribution. Citeseer.

Murphy, K. P. (2012). *Machine learning: A probabilistic perspective*. MIT Press.

Neal, R. (2008). The harmonic mean of the likelihood: Worst Monte Carlo method ever. URL [https://radfordneal.wordpress.com/2008/08/17/the-harmonic-mean-of-the-likelihood-worst-monte-carlo-method-ever/](https://radfordneal.wordpress.com/2008/08/17/the-harmonic-mean-of-the-likelihood-worst-monte-carlo-method-ever/). Accessed November 8, 2019.

Neal, R. M. (2001). Annealed importance sampling. *Statistics and Computing 11*(2), 125–139.

Neumann, M., S. Huang, D. E. Marthaler, and K. Kersting (2015). pyGPs: A python library for Gaussian process regression and classification. *The Journal of Machine Learning Research 16*(1), 2611–2616.

Newton, M. A. and A. E. Raftery (1994). Approximate Bayesian inference with the weighted likelihood bootstrap. *Journal of the Royal Statistical Society. Series B (Methodological) 56*(1), 3–48.

Ng, A. and M. Jordan (2002). On discriminative vs. generative classifiers: A comparison of logistic regression and naive Bayes. In *Advances in neural information processing systems*, Volume 14, pp. 841–848. MIT Press.

Ng, A., M. Jordan, and Y. Weiss (2002). On spectral clustering: Analysis and an algorithm. In *Advances in neural information processing systems*, Volume 14, pp. 849–856. MIT Press.

Nguyen, L. H., I. Gaudot, and J.-A. Goulet (2019). Uncertainty quantification for model parameters and hidden state variables in Bayesian dynamic linear models. *Structural Control and Health Monitoring 26*(3), e2309.

 

Nguyen, L. H. and J.-A. Goulet (2018). Anomaly detection with the switching Kalman filter for structural health monitoring. *Structural Control and Health Monitoring 25*(4), e2136.

Nielsen, T. D. and F. V. Jensen (2007). *Bayesian networks and decision graphs*. Springer.

Nocedal, J. and S. Wright (2006). *Numerical optimization*. Springer Science & Business Media.

Pearl, J. (1988). *Probabilistic reasoning in intelligent systems: Networks of plausible inference*. Morgan Kaufmann.

Quach, A. N. O., D. Tabor, L. Dumont, B. Courcelles, and J.-A. Goulet (2017). A machine learning approach for characterizing soil contamination in the presence of physical site discontinuities and aggregated samples. *Advanced Engineering Informatics 33*, 60–67.

Quiñonero-Candela, J. and C. E. Rasmussen (2005). A unifying view of sparse approximate Gaussian process regression. *Journal of Machine Learning Research 6*, 1939–1959.

Rasmussen, C. E. and H. Nickisch (2010). Gaussian processes for machine learning (GPML) toolbox. *The Journal of Machine Learning Research 11*, 3011–3015.

Rasmussen, C. E. and C. K. Williams (2006). *Gaussian processes for machine learning*. MIT Press.

Rauch, H. E., C. T. Striebel, and F. Tung (1965). Maximum likelihood estimates of linear dynamic systems. *AIAA Journal 3*(8), 1445–1450.

Rosenblatt, F. (1958). The perceptron: A probabilistic model for information storage and organization in the brain. *Psychological Review 65*(6), 386.

Rosenthal, J. S. (2011). Optimal proposal distributions and adaptive MCMC. In *Handbook of Markov Chain Monte Carlo*, 93–112. CRC Press.

Rumelhart, D. E., G. E. Hinton, and R. J. Williams (1986). Learning representations by back-propagating errors. *Nature 323*, 533–536.

Runnalls, A. R. (2007). Kullback-Leibler approach to Gaussian mixture reduction. *IEEE Transactions on Aerospace and Electronic Systems 43*(3), 989–999.

 

Russell, S. and P. Norvig (2009). *Artificial Intelligence: A Modern Approach* (3rd ed.). Prentice-Hall.

Simon, D. (2006). *Optimal state estimation: Kalman, H infinity, and nonlinear approaches*. Wiley.

Spiegelhalter, D. J., N. G. Best, B. P. Carlin, and A. van der Linde (2002). Bayesian measures of model complexity and fit. *Journal of the Royal Statistical Society: Series B (Statistical Methodology) 64*(4), 583–639.

Sutton, R. S. (1988). Learning to predict by the methods of temporal differences. *Machine Learning 3*(1), 9–44.

Sutton, R. S. and A. G. Barto (2018). *Reinforcement learning: An introduction* (2nd ed.). MIT Press.

Tolvanen, V., P. Jyläanki, and A. Vehtari (2014). Expectation propagation for nonstationary heteroscedastic Gaussian process regression. In *IEEE International Workshop on Machine Learning for Signal Processing (MLSP)*, 1–6. IEEE.

Van der Maaten, L. and G. Hinton (2008). Visualizing data using t-SNE. *Journal of Machine Learning Research 9*, 2579–2605.

Van Loan, C. F. and G. H. Golub (1983). *Matrix computations*. Johns Hopkins University Press.

Vanhatalo, J., J. Riihimäki, J. Hartikainen, P. Jylänki, V. Tolvanen, and A. Vehtari (2013). GPstuff: Bayesian modeling with Gaussian processes. *Journal of Machine Learning Research 14*, 1175–1179.

Von Neumann, J. and O. Morgenstern (1947). *The theory of games and economic behavior*. Princeton University Press.

Wan, E. A. and R. van der Merwe (2000). The unscented Kalman filter for nonlinear estimation. In *Adaptive Systems for Signal Processing, Communications, and Control Symposium*, 153–158. IEEE.

Watanabe, S. (2010). Asymptotic equivalence of Bayes cross validation and widely applicable information criterion in singular learning theory. *Journal of Machine Learning Research 11*, 3571–3594.

Watkins, C. J. and P. Dayan (1992). Q-learning. *Machine Learning 8*(3–4), 279–292.

 

West, M. (2013). Bayesian dynamic modelling. In *Bayesian theory and applications*, 145–166. Oxford University Press.

West, M. and J. Harrison (1999). *Bayesian forecasting and dynamic models*. Springer.

Westgate, R. J. and J. M. W. Brownjohn (2011). Development of a Tamar Bridge finite element model. In *Conference Proceedings of the Society for Experimental Mechanics*, Volume 5, pp. 13–20. Springer.

Wikipedia (2017). Conjugate prior. URL [https://en.wikipedia.org/wiki/conjugate\_prior](https://en.wikipedia.org/wiki/conjugate_prior). Accessed November 8, 2019.

Wright, S. J. (2015). Coordinate descent algorithms. *Mathematical Programming 151*(1), 3–34.

 

[*Index*](#toc.xhtml#indx-1)

Acceptance rate, [96](#chapter006.xhtml#p96)

Activation functions, [128](#chapter007.xhtml#p128)

Activation unit, [129](#chapter007.xhtml#p129)

Affine function, [10](#chapter001.xhtml#p10)

Agent, [244](#chapter014.xhtml#p244)

Aleatory, [17](#chapter002.xhtml#p17)

Anomaly detection, [208](#chapter011.xhtml#p208)

Armijo rule, [48](#chapter004.xhtml#p48)

Artificial intelligence, [2](#introduction001.xhtml#p2)

Autoregressive, [202](#chapter011.xhtml#p202)

Backpropagation, [132](#chapter007.xhtml#p132), [133](#chapter007.xhtml#p133), [151](#chapter008.xhtml#p151)

Backtracking, [48](#chapter004.xhtml#p48)

Basis function, [108](#chapter007.xhtml#p108), [145](#chapter008.xhtml#p145)

Bayes rule, [21](#chapter002.xhtml#p21), [60](#chapter005.xhtml#p60)

Bayesian dynamic linear models, [198](#chapter011.xhtml#p198)

Bayesian network, [167](#chapter010.xhtml#p167)

Beta, [44](#chapter003.xhtml#p44)

Beta-Binomial, [80](#chapter005.xhtml#p80)

Bias-variance tradeoff, [110](#chapter007.xhtml#p110)

Block diagonal, [10](#chapter001.xhtml#p10)

Burn-in, [92](#chapter006.xhtml#p92)

Capacity, [110](#chapter007.xhtml#p110)

Causality, [28](#chapter002.xhtml#p28)

Censored observations, [66](#chapter005.xhtml#p66), [67](#chapter005.xhtml#p67)

Central differentiation, [53](#chapter004.xhtml#p53)

Central limit theorem, [38](#chapter003.xhtml#p38), [43](#chapter003.xhtml#p43)

Chain rule, [20](#chapter002.xhtml#p20), [167](#chapter010.xhtml#p167)

Change of variable, [29](#chapter002.xhtml#p29)

Classes, [139](#chapter008.xhtml#p139)

Classification, [139](#chapter008.xhtml#p139)

Clustering, [157](#chapter009.xhtml#p157)

Collective exhaustivity, [19](#chapter002.xhtml#p19)

Conditional independence, [68](#chapter005.xhtml#p68), [73](#chapter005.xhtml#p73), [168](#chapter010.xhtml#p168), [170](#chapter010.xhtml#p170)

Conditional probability, [20](#chapter002.xhtml#p20)

Conditional probability table, [168](#chapter010.xhtml#p168)

Conjugate priors, [80](#chapter005.xhtml#p80)

Convex optimization, [47](#chapter004.xhtml#p47)

Convexity, [47](#chapter004.xhtml#p47)

Coordinate optimization, [52](#chapter004.xhtml#p52)

Correlation coefficient, [28](#chapter002.xhtml#p28)

Correlation function, [116](#chapter007.xhtml#p116)

Correlation matrix, [37](#chapter003.xhtml#p37)

Covariance, [28](#chapter002.xhtml#p28)

Covariance matrix, [28](#chapter002.xhtml#p28)

Covariate, [107](#chapter007.xhtml#p107)

Cross-entropy, [151](#chapter008.xhtml#p151)

Cross-validation, [87](#chapter005.xhtml#p87), [111](#chapter007.xhtml#p111)

Cumulative distribution function (CDF), [23](#chapter002.xhtml#p23)

Cumulative mass function, [23](#chapter002.xhtml#p23)

d-separation, [170](#chapter010.xhtml#p170)

Decision tree, [230](#chapter013.xhtml#p230)

Decisions, [229](#chapter013.xhtml#p229)

Deep learning, [126](#chapter007.xhtml#p126)

Determinant, [13](#chapter001.xhtml#p13), [30](#chapter002.xhtml#p30)

Diagonal matrix, [10](#chapter001.xhtml#p10)

Dimension reduction, [157](#chapter009.xhtml#p157), [165](#chapter009.xhtml#p165)

Dirac delta function, [71](#chapter005.xhtml#p71), [73](#chapter005.xhtml#p73)

Directed acyclic graph, [169](#chapter010.xhtml#p169)

Discrete choice model, [146](#chapter008.xhtml#p146)

Discriminative classifier, [139](#chapter008.xhtml#p139)

Distributions, [35](#chapter003.xhtml#p35)

Dynamic Bayesian network, [177](#chapter010.xhtml#p177)

Early stopping, [134](#chapter007.xhtml#p134), [135](#chapter007.xhtml#p135)

Eigen decomposition, [13](#chapter001.xhtml#p13)

Eigenvalues, [13](#chapter001.xhtml#p13), [37](#chapter003.xhtml#p37)

Eigenvectors, [13](#chapter001.xhtml#p13), [37](#chapter003.xhtml#p37)

Epistemic, [17](#chapter002.xhtml#p17), [19](#chapter002.xhtml#p19)

Epoch, [134](#chapter007.xhtml#p134)

Error function, [36](#chapter003.xhtml#p36)

Estimated potential scale reduction, [93](#chapter006.xhtml#p93)

Euclidian distance, [12](#chapter001.xhtml#p12)

Events, [18](#chapter002.xhtml#p18)

Evidence, [60](#chapter005.xhtml#p60), [69](#chapter005.xhtml#p69)

Expectation, [27](#chapter002.xhtml#p27), [75](#chapter005.xhtml#p75)

Expectation maximization, [158](#chapter009.xhtml#p158), [176](#chapter010.xhtml#p176)

Extrapolation, [114](#chapter007.xhtml#p114)

Feedforward neural networks, [127](#chapter007.xhtml#p127)

Forecasting, [190](#chapter011.xhtml#p190)

Frequentist, [19](#chapter002.xhtml#p19)

Gaussian conditional, [39](#chapter003.xhtml#p39)

Gaussian distribution, [35](#chapter003.xhtml#p35)

Gaussian mixture, [157](#chapter009.xhtml#p157), [195](#chapter011.xhtml#p195)

Gaussian process, [115](#chapter007.xhtml#p115)

Gaussian process classification, [146](#chapter008.xhtml#p146)

Gaussian process regression, [115](#chapter007.xhtml#p115)

Generative classifier, [140](#chapter008.xhtml#p140)

Gradient, [29](#chapter002.xhtml#p29), [30](#chapter002.xhtml#p30), [48](#chapter004.xhtml#p48)

Gradient ascent, [48](#chapter004.xhtml#p48)

Graph theory, [167](#chapter010.xhtml#p167)

Hadamar product, [11](#chapter001.xhtml#p11), [133](#chapter007.xhtml#p133)

Hard clustering, [158](#chapter009.xhtml#p158)

Hard-coding, [1](#introduction001.xhtml#p1)

Hessian, [31](#chapter002.xhtml#p31), [51](#chapter004.xhtml#p51), [54](#chapter004.xhtml#p54)

Heteroscedasticity, [114](#chapter007.xhtml#p114), [126](#chapter007.xhtml#p126)

Hidden Markov models, [178](#chapter010.xhtml#p178)

Hidden variable, [59](#chapter005.xhtml#p59), [128](#chapter007.xhtml#p128), [181](#chapter011.xhtml#p181)

Hierarchical Bayes, [218](#chapter012.xhtml#p218)

 

Homoscedasticity, [114](#chapter007.xhtml#p114)

Hyperbolic tangent, [128](#chapter007.xhtml#p128)

Hyperparameters, [219](#chapter012.xhtml#p219)

Identifiability, [70](#chapter005.xhtml#p70)

Identity matrix, [10](#chapter001.xhtml#p10)

Importance sampling, [75](#chapter005.xhtml#p75)

Improper distribution, [72](#chapter005.xhtml#p72)

Incremental average, [253](#chapter014.xhtml#p253)

Inference, [171](#chapter010.xhtml#p171)

Inner product, [11](#chapter001.xhtml#p11)

Interpolation, [114](#chapter007.xhtml#p114)

Intersection, [18](#chapter002.xhtml#p18)

Inverse, [12](#chapter001.xhtml#p12)

Jacobian, [30](#chapter002.xhtml#p30), [32](#chapter002.xhtml#p32)

Joint probability, [20](#chapter002.xhtml#p20)

Junction tree, [173](#chapter010.xhtml#p173)

K-means, [162](#chapter009.xhtml#p162)

Kalman filter, [188](#chapter011.xhtml#p188)

Kalman smoother, [191](#chapter011.xhtml#p191)

Laplace approximation, [83](#chapter005.xhtml#p83), [149](#chapter008.xhtml#p149)

Latent variables, [147](#chapter008.xhtml#p147), [158](#chapter009.xhtml#p158)

Learning rate, [48](#chapter004.xhtml#p48), [253](#chapter014.xhtml#p253)

Length scale, [116](#chapter007.xhtml#p116)

Likelihood, [60](#chapter005.xhtml#p60), [66](#chapter005.xhtml#p66)

Line search, [48](#chapter004.xhtml#p48)

Linear discriminant analysis, [142](#chapter008.xhtml#p142)

Linear functions, [30](#chapter002.xhtml#p30)

Linear regression, [107](#chapter007.xhtml#p107), [127](#chapter007.xhtml#p127)

Linear system, [10](#chapter001.xhtml#p10)

Local acceleration, [200](#chapter011.xhtml#p200)

Local level, [183](#chapter011.xhtml#p183), [199](#chapter011.xhtml#p199)

Local optimum, [48](#chapter004.xhtml#p48)

Local trend, [199](#chapter011.xhtml#p199)

Log-normal, [41](#chapter003.xhtml#p41)

Logistic, [55](#chapter004.xhtml#p55), [128](#chapter007.xhtml#p128), [145](#chapter008.xhtml#p145)

Logistic regression, [144](#chapter008.xhtml#p144)

Loss function, [109](#chapter007.xhtml#p109)

Mapping, [10](#chapter001.xhtml#p10)

Marginal likelihood, [121](#chapter007.xhtml#p121), [185](#chapter011.xhtml#p185), [192](#chapter011.xhtml#p192)

Marginal probability, [20](#chapter002.xhtml#p20)

Marginalization, [21](#chapter002.xhtml#p21), [26](#chapter002.xhtml#p26), [168](#chapter010.xhtml#p168)

Markov chain, [89](#chapter005.xhtml#p89)

Markov decision process, [244](#chapter014.xhtml#p244)

Markov property, [89](#chapter005.xhtml#p89), [183](#chapter011.xhtml#p183), [242](#chapter014.xhtml#p242)

Matern-class kernel, [124](#chapter007.xhtml#p124)

Matrix, [9](#chapter001.xhtml#p9)

Matrix inversion, [11](#chapter001.xhtml#p11)

Matrix multiplication, [11](#chapter001.xhtml#p11)

Maximum likelihood, [82](#chapter005.xhtml#p82)

Metamodel, [122](#chapter007.xhtml#p122)

Metropolis, [90](#chapter006.xhtml#p90)

Metropolis-Hastings, [92](#chapter006.xhtml#p92)

Mini-batch, [134](#chapter007.xhtml#p134)

Missing at random, [176](#chapter010.xhtml#p176)

Model calibration, [213](#chapter012.xhtml#p213)

Model class, [85](#chapter005.xhtml#p85)

Model complexity, [110](#chapter007.xhtml#p110)

Model selection, [85](#chapter005.xhtml#p85)

Moment, [27](#chapter002.xhtml#p27)

Momentum, [49](#chapter004.xhtml#p49)

Monotonic, [29](#chapter002.xhtml#p29)

Monte Carlo, [74](#chapter005.xhtml#p74), [89](#chapter005.xhtml#p89), [252](#chapter014.xhtml#p252)

Mutual exclusivity, [19](#chapter002.xhtml#p19)

Naive Bayes, [142](#chapter008.xhtml#p142)

Neural networks, [126](#chapter007.xhtml#p126), [150](#chapter008.xhtml#p150)

Newton-Raphson, [50](#chapter004.xhtml#p50)

Non-informative prior, [60](#chapter005.xhtml#p60), [72](#chapter005.xhtml#p72)

Normal distribution, [35](#chapter003.xhtml#p35)

Normalization, [163](#chapter009.xhtml#p163)

Normalization constant, [60](#chapter005.xhtml#p60)

Norms, [12](#chapter001.xhtml#p12)

Numerical derivatives, [53](#chapter004.xhtml#p53)

Observation model, [66](#chapter005.xhtml#p66), [183](#chapter011.xhtml#p183)

Outliers, [114](#chapter007.xhtml#p114)

Overfitting, [110](#chapter007.xhtml#p110), [217](#chapter012.xhtml#p217)

Periodic, [201](#chapter011.xhtml#p201)

Planning horizon, [241](#chapter014.xhtml#p241), [244](#chapter014.xhtml#p244)

Point estimates, [82](#chapter005.xhtml#p82)

Policy, [241](#chapter014.xhtml#p241)

Policy iteration, [248](#chapter014.xhtml#p248)

POMDP, [251](#chapter014.xhtml#p251)

Positive definite, [13](#chapter001.xhtml#p13)

Positive semidefinite, [13](#chapter001.xhtml#p13), [29](#chapter002.xhtml#p29)

Posterior predictive, [72](#chapter005.xhtml#p72)

Principal component analysis, [163](#chapter009.xhtml#p163)

Prior, [72](#chapter005.xhtml#p72)

Probability, [19](#chapter002.xhtml#p19)

Probability density function (PDF), [23](#chapter002.xhtml#p23)

Probability mass function, [22](#chapter002.xhtml#p22)

Q-learning, [254](#chapter014.xhtml#p254)

Quadratic discriminant analysis, [142](#chapter008.xhtml#p142)

Random variable, [22](#chapter002.xhtml#p22)

Random walk, [89](#chapter005.xhtml#p89), [90](#chapter006.xhtml#p90)

Rational decision, [231](#chapter013.xhtml#p231)

Realizations, [22](#chapter002.xhtml#p22)

Rectangle rule, [69](#chapter005.xhtml#p69)

Rectified linear unit, [129](#chapter007.xhtml#p129)

Regression, [107](#chapter007.xhtml#p107)

Regularization, [134](#chapter007.xhtml#p134)

Reinforcement learning, [3](#introduction001.xhtml#p3), [241](#chapter014.xhtml#p241)

Reward, [241](#chapter014.xhtml#p241)

Risk aversion, [234](#chapter013.xhtml#p234)

Saddle points, [51](#chapter004.xhtml#p51)

Sampling space, [18](#chapter002.xhtml#p18)

Score, [163](#chapter009.xhtml#p163)

Set theory, [18](#chapter002.xhtml#p18)

Sigmoid, [55](#chapter004.xhtml#p55), [145](#chapter008.xhtml#p145)

Singular matrix, [13](#chapter001.xhtml#p13), [125](#chapter007.xhtml#p125)

Smoothing, [190](#chapter011.xhtml#p190)

Soft clustering, [158](#chapter009.xhtml#p158)

Softmax, [151](#chapter008.xhtml#p151)

Space transformation, [54](#chapter004.xhtml#p54), [97](#chapter006.xhtml#p97)

Square exponential kernel, [116](#chapter007.xhtml#p116)

Standard deviation, [27](#chapter002.xhtml#p27)

Standard normal CDF, [147](#chapter008.xhtml#p147)

State-space models, [181](#chapter011.xhtml#p181)

Stationarity, [181](#chapter011.xhtml#p181)

Statistical independence, [20](#chapter002.xhtml#p20)

Supervised learning, [3](#introduction001.xhtml#p3)

Switching Kalman filter, [194](#chapter011.xhtml#p194)

Taylor series, [31](#chapter002.xhtml#p31)

Temporal difference learning, [252](#chapter014.xhtml#p252)

Trace, [10](#chapter001.xhtml#p10)

Training set, [109](#chapter007.xhtml#p109)

Transformations, [12](#chapter001.xhtml#p12)

Transition model, [183](#chapter011.xhtml#p183), [241](#chapter014.xhtml#p241)

Transposition, [10](#chapter001.xhtml#p10)

Trend-stationary, [181](#chapter011.xhtml#p181)

Underflow, [69](#chapter005.xhtml#p69)

Union, [18](#chapter002.xhtml#p18)

Unsupervised learning, [3](#introduction001.xhtml#p3), [157](#chapter009.xhtml#p157)

 

Utility theory, [230](#chapter013.xhtml#p230)

Value iteration, [246](#chapter014.xhtml#p246)

Value of information, [236](#chapter013.xhtml#p236)

Variable elimination, [172](#chapter010.xhtml#p172)

Variance, [27](#chapter002.xhtml#p27)

Vector, [9](#chapter001.xhtml#p9)

Venn diagram, [18](#chapter002.xhtml#p18)

Weight decay, [134](#chapter007.xhtml#p134)