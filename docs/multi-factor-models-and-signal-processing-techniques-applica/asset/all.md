![images](images/cover.jpg)

Table of Contents

[Foreward](#Foreword.xhtml)

[Notations and Acronyms](#Notations_and_Acronyms.xhtml)

[Introduction](#Introduction.xhtml)

[I.1. Digital society and new paradigms in fund management](#Introduction.xhtml#head1)

[I.2. Statistical signal processing and factor models in finance](#Introduction.xhtml#head2)

[I.3. Multiexpertise team of authors](#Introduction.xhtml#head3)

[I.4. Book positioning and targeted readers](#Introduction.xhtml#head4)

[I.5. Book organization](#Introduction.xhtml#head5)

[Chapter 1: Factor Models and General Definition](#c01.xhtml)

[1.1. Introduction](#c01.xhtml#head1)

[1.2. What are factor models?](#c01.xhtml#head2)

[1.3. Why factor models in finance?](#c01.xhtml#head3)

[1.4. How to build factor models?](#c01.xhtml#head4)

[1.5. Historical perspective](#c01.xhtml#head5)

[1.6. Glossary](#c01.xhtml#head6)

[Chapter 2: Factor Selection](#c02.xhtml)

[2.1. Introduction](#c02.xhtml#head1)

[2.2. Qualitative know-how](#c02.xhtml#head2)

[2.3. Quantitative methods based on eigenfactors](#c02.xhtml#head3)

[2.4. Model order choice](#c02.xhtml#head4)

[2.5. Appendix 1: Covariance matrix estimation](#c02.xhtml#head5)

[2.6. Appendix 2: Similarity of the eigenfactor selection with the MUSIC algorithm](#c02.xhtml#head6)

[2.7. Appendix 3: Large panel data](#c02.xhtml#head7)

[2.8. Chapter 2 highlights](#c02.xhtml#head8)

[Chapter 3: Least Squares Estimation (LSE) and Kalman Filtering (KF) for Factor Modeling: *A Geometrical Perspective*](#c03.xhtml)

[3.1. Introduction](#c03.xhtml#head1)

[3.2. Why LSE and KF in factor modeling?](#c03.xhtml#head2)

[3.3. LSE setup](#c03.xhtml#head3)

[3.4. LSE objective and criterion](#c03.xhtml#head4)

[3.5. How LSE is working (for LSE users and programmers)](#c03.xhtml#head5)

[3.6. Interpretation of the LSE solution](#c03.xhtml#head6)

[3.7. Derivations of LSE solution](#c03.xhtml#head7)

[3.8. Why KF and which setup?](#c03.xhtml#head8)

[3.9. What are the main properties of the KF model?](#c03.xhtml#head9)

[3.10. What is the objective of KF?](#c03.xhtml#head10)

[3.11. How does the KF work (for users and programmers)?](#c03.xhtml#head11)

[3.12. Interpretation of the KF updates](#c03.xhtml#head12)

[3.13. Practice](#c03.xhtml#head13)

[3.14. Geometrical derivation of KF updating equations](#c03.xhtml#head14)

[3.15. Highlights](#c03.xhtml#head15)

[3.16. Appendix: Matrix inversion lemma](#c03.xhtml#head16)

[Chapter 4: A Regularized Kalman Filter (rgKF) for Spiky Data](#c04.xhtml)

[4.1. Introduction](#c04.xhtml#head1)

[4.2. Preamble: statistical evidence on the KF recursive equations](#c04.xhtml#head2)

[4.3. Robust KF](#c04.xhtml#head3)

[4.4. rgKF: the rgKF(NG,*l^q*)](#c04.xhtml#head4)

[4.5. Application to detect irregularities in hedge fund returns](#c04.xhtml#head5)

[4.6. Conclusion](#c04.xhtml#head6)

[4.7. Chapter highlights](#c04.xhtml#head7)

[Appendix: Some Probability Densities](#Appendix.xhtml)

[A1.1. Gaussian distribution](#Appendix.xhtml#head1)

[A1.2. *χ*² distribution](#Appendix.xhtml#head2)

[A1.3. Student’s **t**\-distribution](#Appendix.xhtml#head3)

[A1.4. Fisher (or Fisher–Snedecor or Snedecor’s *F*) distribution](#Appendix.xhtml#head4)

[A1.5. Hotelling’s **t**\-squared distribution](#Appendix.xhtml#head5)

[A1.6. Wishart distribution](#Appendix.xhtml#head6)

[A1.7. Marčenko–Pastur distribution](#Appendix.xhtml#head7)

[A1.8. Bernoulli–Gaussian distribution](#Appendix.xhtml#head8)

[Conclusion](#Conclusion.xhtml)

[Bibliography](#Bibliography.xhtml)

[Index](#index.xhtml)

[Color Plate](#Figures.xhtml)

![image](images/img_1_2.jpg)

First published 2013 in Great Britain and the United States by ISTE Ltd and John Wiley & Sons, Inc.

Apart from any fair dealing for the purposes of research or private study, or criticism or review, as permitted under the Copyright, Designs and Patents Act 1988, this publication may only be reproduced, stored or transmitted, in any form or by any means, with the prior permission in writing of the publishers, or in the case of reprographic reproduction in accordance with the terms and licenses issued by the CLA. Enquiries concerning reproduction outside these terms should be sent to the publishers at the undermentioned address:

ISTE Ltd

27-37 St George’s Road

London SW19 4EU

UK

[www.iste.co.uk](http://www.iste.co.uk)

John Wiley & Sons, Inc.

111 River Street

Hoboken, NJ 07030

USA

[www.wiley.com](http://www.wiley.com)

© ISTE Ltd 2013

The rights of Serge Darolles, Patrick Duvaut and Emmanuelle Jay to be identified as the authors of this work have been asserted by them in accordance with the Copyright, Designs and Patents Act 1988.

Library of Congress Control Number: 2013941318

British Library Cataloguing-in-Publication Data

A CIP record for this book is available from the British Library

ISBN: 978-1-84821-419-4

![images](images/img_22_3.jpg)

Foreword

With the irruption of electronic markets and the widespread use of quantitative models for trading, order execution and risk management, financial markets have evolved from the low-tech environment where they started from a few decades ago to the one where market participants routinely employ advanced data processing techniques to analyze large data flows in real time and feed the results into trading algorithms and risk management systems. Operational constraints arising from the sheer volume of data to be analyzed have created the need for intelligent data processing and modeling methods and parsimonious models whose estimation and simulation is feasible in the high-dimensional settings represented by the large number of risk factors involved in risk decisions.

In this context, advanced tools and methods from signal processing – the branch of science and engineering that deals with the modeling and analysis of complex streams of data – are increasingly used to analyze financial data and estimate the statistical models used by portfolio managers and risk managers.

In contrast to the traditional toolkit of portfolio theory, which is mostly based on *static* analysis of portfolio loss distributions, the use of models based on stochastic process allows risk managers a dynamic, and more realistic, view of portfolio risk which is dynamically updated as new information is revealed. However, the use of such dynamic models comes at a price: we need more advanced tools to estimate, simulate and analyze portfolio risk in these models. Tools that have long been used in engineering, such as the Kalman filter, but may be unfamiliar to some risk management professionals, turn out to be relevant when moving beyond the static setting.

Simultaneously, the use of high-dimensional models entail new estimation problems: in many asset allocation problems, one has a few years (so, a few hundreds of daily observations) to estimate the parameters describing the evolution of hundreds, if not thousands, of risk factors. In this context, traditional estimation methods, such as principal component analysis and basic covariance analysis, fail to be consistent and yield unexpected (and biased!) results **. . .** Tools such as random matrix theory, initially developed in nuclear physics to model the energy levels of complex nuclei, have been recently used to explore such estimation biases and propose methods for overcoming them.

Leveraging on their double profile of quantitative risk professionals with a strong research and technical background, Serge Darolles, Patrick Duvaut and Emmanuelle Jay have done an excellent job in presenting a nice selection of advanced signal processing tools and statistical models that address some of these points in a self-contained manner, at a level accessible to students and professionals involved with quantitative risk management.

By drawing on their professional experience in quantitative modeling to achieve the right level of technical sophistication, Serge, Patrick and Emmanuelle have succeeded in covering a variety of relevant concepts without sacrificing the technical details necessary for a serious implementation: multi-factor models, advanced estimation methods based on random matrix theory, filtering algorithms and regularization methods for identification of latent risk factors. The use of these tools in risk management and asset allocation is nicely illustrated through examples using financial data.

I trust that the hard work done by the authors will benefit a wide range of readers across academic and professional circles and act as an incentive for readers to delve into the vast research literature on statistical modeling in finance. *Bonne lecture!*

Rama CONT

London

June 2013

# Introduction

# I.1. Digital society and new paradigms in fund management

The massive digitization of all our activities from entertainment to all public and economical domains marks the era of the digital society. This latter generates an overwhelming amount of data, measured in zetta (10^(21)) bytes.

This phenomenon called *Big Data* impacts the finance sphere as well. The so-called *five Vs* need to be handled by fund management companies: volume, velocity, variety, visualization and value. Moreover, the 2008 mortgage crisis and its macroeconomic effects had two major consequences that make the situation even more difficult for fund managers. First, these large amounts of data are highly *hectic* (non-stationary), even more unpredictable and noisy. Second, the fund management paradigm has been shifted from an “abstruse gain race” at any risk to being able to control the risks (draw down) while securing a minimum gain, with a maximum transparency.

One way to address the above mentioned challenging issues is to provide fund managers with appropriate and “user friendly” QUANT(ITATIVE) tools that are market driven. This is where Factor Models, Statistical Signal Processing (SSP) and Multi-factor Models and Signal Processing Techniques come into play.

# I.2. Statistical signal processing and factor models in finance

The linear factor model is nowadays a benchmark in portfolio management theory and in the understanding of asset returns, even in the hedge fund industry where returns may have high nonlinearities. The idea is to relate a large number and variety of returns to a few relevant *factors*, up to Gaussian errors that cannot be described solely by the factors. The factors thus drive and parsimoniously explain the *spatial correlation between* assets, while the errors are *idiosyncratic to each* asset.

Factors need to be chosen and/or identified first, then the parameters of the linear model that connect them to the assets, such as the *alphas* (gains) and the *betas* (assets exposures) have to be estimated and tracked. Based on a linear regression fed by market data, linear factor models are thus suitable for all the requirements listed above of friendliness to the users, transparency and as being market driven.

Statistical signal processing (SSP) methods allow us to access both the factors and the model parameters, in a very noisy, highly unpredictable and hectic environment. SSP methods have proved their ergonomy, efficiency and practicality in highly hostile and changing conditions in the past few decades when applied to medical diagnostics, non-destructive testing of nuclear plants, aircrafts, cars and in boosting both the performance and the robustness of mobile phones, with some top achievements in the 4G Long Term Evolution (LTE) standards.

The aim of this book is to share the same when dealing with fund management and more specifically when facing the identification of linear factor models. While application of SSP to finance has been ongoing for a few years, it is still a big challenge due to the difficulty of relying on joint expertise in fund management, statistical signal processing and being at the crossroad of Academia and Business, to make the recent results of research usable for fund managers.

# I.3. Multiexpertise team of authors

The three authors’ complementary expertise and experience meet the challenging above mentioned conditions. First, the three of them have both academia and business experience. Second, two of them are experienced fund managers, while the third was an executive of a US company involved in asset capitalization. Moreover, the three authors have been working together many years, as partners of the same Company QAMLab^©, involved in quantitative solutions for fund management. It is worth mentioning that the authors’ expertise range from mathematical finance to SSP.

This book is thus the outcome of such a unique pluridisciplinary and market-oriented expertise.

# I.4. Book positioning and targeted readers

The book targets three worldwide audiences. First, graduate students of Business, Finance, Management Masters, including, of course, MBAs who would like to understand how SSP methods can leverage linear factor models in the complicated and hectic digital asset management activities of the emerging digital society. Second, SSP grad students who would like to ramp up in quantitative finance following familiar tracks of least squares, Kalman filtering (KF) and more advanced tools based on most recent regularized Kalman approaches. Third, qualitative fund managers who are eager to add to their daily management softwares and practices, several standalone and/or end-to-end SSP methods in order to enhance and boost their own management style, in a very practical, transparent and market-oriented manner.

The book material is unique since it presents QUANT tools as practical answers to market driven issues faced by fund managers. First in the associated chapters, the SSP material is introduced from the users’ stand-point, answering the questions, why do we need these tools, how do they work, how do we use them, how can they be tuned to the real data? The derivations of the results are provided in appendices and can be skipped for user-only readers. On the other hand, SSP skillful audience can access quickly this advanced material. Second, numerous examples and real market data are used through the whole book to better understand the SSP methods and their pluses when dealing with linear factor models. Finally, highlights emphasize the most relevant contents at the end of each chapter, to allow quick access.

It is important to note that the book contents were already taught by all the authors, both in finance and Information Science Masters. Feedback from the students has thus been a valuable input to improve the clarity and the depth of the writing.

# I.5. Book organization

The book is organized into four chapters.

Chapter 1 introduces the factor model foundations of the whole book, the equations, the notations, the main concepts, the origin, the applications, etc. While most of it can be skipped by readers familiar with fund management, it is nevertheless valuable to check it to master the model that will be used in the remainder of the book.

Chapter 2 presents qualitative and quantitative ways to choose the factors. While qualitative approaches leverage pure markets know-how, quantitative methods are based on the so-called *eigenfactors*, derived from the eigen-decomposition of the returns covariance matrix. Statistical methods to select the “optimum” number of factors are also detailed. Even SSP readers can enrich their knowledge by grasping the connection between eigen-methods and the determination of the appropriate number of factors.

Least squares and Kalman algorithms that aim to estimate the alphas and the betas of the factor model are the main focus of Chapter 3. A geometrical presentation of both methods enables us to understand their objectives, usage, performance, and limitations in a practical way, especially to the attention of readers from finance and business backgrounds. The whole derivation of KF is provided in Chapter 3 appendix, still along a geometrical fashion. These two methods are basic tools in SSP.

Chapter 4 contents are the most advanced from SSP standpoint and share results at the edge (at the time the book is written) of relevant research about KF regularization to handle some impulsive and non-Gaussian markets behaviors. Spectacular improvement with respect to traditional KF is obtained and illustrated on market data.

Notations and Acronyms

| a, b, etc. || Column vectors |
| --- | --- |
| A, B, etc. || Matrices |
| A′ || Transpose of matrix A |
| A^(*H*) || Transpose conjugate of matrix A |
| A^(−1) || Inverse of matrix A |
| tr(A) || Trace of matrix A |
| ∇[x](**.**) || Gradient vector-operator |
| 0[*N*] || *N* × *N* null matrix |
| I[*N*] || *N* × *N* identity matrix |
| 1[*N*] || *N*\-dimensional vector of 1s |
| *a, b*, etc. || Scalars |
| *t* || Time |
| *T* || Total number of time observations |
| *t* = 1, …, *T* || One-step vector of time going from 1 to *T* by step of 1 |
| *N* || Number of assets |
| *s*[*i,t*] || Price of asset *i* at time *t* |
| *r*[*t*] || Return of an asset at time *t* |
| *r*[*f*] || Return of the risk-free asset |
| *r*[*i,t*] || Return of asset *i* at time *t* |
| *r*[*m,t*] || Return of the market *m* at time *t* |
| r[*t*] || *N*\-dimensional vector of returns at time *t* |
| r[*k*] || *T*\-dimensional vector of returns for asset *k* |
| ![image](images/Inline_21_3.jpg) || Matrix of returns for the *N* observed assets |
| ![image](images/Inline_21_4.jpg) || Matrix of the *K* factor returns included in factor models |
| f[*k*] || *k*th column of F |
| f[*t*] || *tt*h row of F and *K*\-dimensional vector of the factor values at *t* |
| G = \[1 F\] || Matrix F augmented by a vector of 1s having the same number of rows |
| g[*k*] || *k*th column of G |
| g[*t*] || *tt*h row of G and *K* + 1-dimensional vector of values at *t* |
| *α* || “Alpha” or the specific performance of an asset over the market performance |
| *β* || “Beta” or the exposure of an asset to a specific factor |
| *β* or b || “Betas” or the vector of asset exposures to the *K* selected factors |
| ![image](images/Inline_22_2.jpg) || *K* + 1-dimensional vector of the unknown parameters of a multi-factor model |
| ![image](images/Inline_22_3.jpg) || *l^q*\-norm |
| ![image](images/Inline_22_4.jpg) || Indicator function |
| â || Estimated value of a |
| i.i.d. || Independent and identically distributed |
| ~ || Distributed according to |
| ![images](images/parallel.gif) || Statistically independent |
| IE(.) || Statistical expectation |
| *V*(.) or *V ar*(.) || Variance |
| *Cov*(.) || Covariance |
| *N* (*μ σ*²) || Gaussian distribution with mean *μ* and variance *σ*² |
| *N* (*μ*, ∑) || Multivariate Gaussian distribution with a mean vector *μ* and covariance ∑ |
| AIC || Akaike information criterion |
| APT || Arbitrage pricing theory |
| BIC || Bayes information criterion |
| CAPM || Capital asset pricing model |
| FP || Fixedpoint |
| KF || Kalman filter |
| LSE || Least squares estimate |
| MDL || Minimum description length |
| ML || Maximum likelihood |
| MMSE || Minimum mean square error |
| MSE || Mean square error |
| MUSIC || Multiple signal characterization |
| NAV || Net asset value |
| OLS || Ordinary least squares |
| PCA || Principal component analysis |
| QAMLAB^© || Quantitative Asset Management Laboratory |
| rgKF || Regularized Kalman filter |
| RKF || Robust Kalman filter |
| RMSE || Root mean square error |
| RMT || Random matrix theory |
| SCM || Sample covariance matrix |
| SSP || Statistical signal processing |
| SW-OLS || Sliding window ordinary least squares |

# Chapter 1

# Factor Models and General Definition

# **1.1. Introduction**

Today, the linear factor model is a benchmark in portfolio management theory \[MAR 52, LIN 65\], and arbitrage pricing theory (APT) \[ROS 76, ROL 80\]. In practice, factor models are also used widely to understand the cross-section dispersion of asset returns, whatever the asset class is. Even in the hedge fund industry, where returns feature high nonlinearity, this approach is largely implemented, in general with some improvement such as nonlinear factors or time-varying parameters. This chapter introduces not only the common version of linear factor models but also discusses its limits and the developments described in the following chapters of this book.

In section 1.2, we introduce the different notations and discuss the model and its structure. We list in section 1.3 the reasons why factor models are generally used in finance, and discuss the limits of this approach. Section 1.4 describes the different steps in the building of factor models, i.e. factor selection and parameter estimation. This section is a direct introduction to Chapter 2 for the factor selection step, and Chapters 3 and 4 for the parameter estimation step. Finally, section 1.5 concludes the chapter by giving a historical perspective on the use of factor models in finance.

# **1.2. What are factor models?**

## **1.2.1.** ***Notations***

We first consider a set of *N* risky assets, indexed *i* = 1*, …, N*. We denote by *s[*i,t*]* the price of the asset *i* at time *t*, and *r*[*i,t*] the corresponding return for the period (*t* − 1*, t*). This return is defined by:

\[1.1\] ![images](images/img_6_25.jpg)

If prices are observed on a daily (respectively, weekly, monthly, etc.) basis, then *r*[*i,t*] represents daily (respectively, weekly, monthly, etc.) returns. We then denote by *μ*[*i*] the expected return of asset *i*, and ![images](images/sig2.gif)² its variance:

\[1.2\] ![images](images/img_8_25.jpg)

The variance ![images](images/sig2.gif)(or the volatility σ[*i*]) is often used to measure the risk relative to the asset *i*. The greater the volatility, the greater is the risk. The covariance *σ*[*i,j*] = *Cov*(*r*[*i,t*]*, r*[*j,t*]) between assets *i* and *j* will be useful to compute the risk of a portfolio of several assets.

As opposed to risky assets, we also consider a risk-free asset that gives a return *r*[*f*], called the risk-free rate (supposed to be constant). In practice, short-term government securities such as US Treasury Bills are used as a proxy for the risk-free asset; this results in a non-constant *r*[*f*].

The expected excess return (or risk premium) of asset *i* is the return we can expect from asset *i* in excess of *r*[*f*], that is

\[1.3\] ![images](images/img_2_26.jpg)

and is the premium relative to the risk taken when investing in asset *i*.

According to Markowitz’s \[MAR 52\] theory of *mean-variance efficiency*, investors (should) therefore require a higher expected return for holding a more risky asset and want to earn the highest possible return for a level of risk that they are willing to take. A portfolio is said to be mean-variance efficient if we cannot create another portfolio with a greater expected return and the same variance of returns (or another portfolio with a lower variance and the same expected return).

[Figure 1.1](#c01.xhtml#fig1) illustrates the time series evolution of three risky assets in comparison to an asset that is a proxy for the risk-free asset. Their mean-variance trade-offs are given in [Table 1.1.](#c01.xhtml#tab1)

[**Table 1.1.**](#c01.xhtml#tab1_1) *Annualized return (μ), annualized volatility (σ) and return-to-risk ratio (Sharpe Ratio) calculated between Feburary 2003 and November 2009 for the four financial instruments shown in [Figure 1.1](#c01.xhtml#fig1) and ordered by increasing level of risk*

![images](images/img_8_26.jpg)

[**Figure 1.1.**](#c01.xhtml#fig1_1) *Monthly evolution of four time series (in US dollars and based at $100 at the end of January 2003) representing: (1) an investment in the US T-Bill 1 year, a 1 year maturity US Treasury Bill, considered as a proxy for the risk-free asset, (2) the NAV of HFRI ED index, an index of event-driven (ED) hedge funds, (3) the price of the S&P500, a US market index and (4) the price of the equity APPLE (on the right axis)*

![images](images/img_2_27.jpg)

The net asset value (NAV) gives the evolution over time of $100 invested in each asset. We can easily compute the NAV from the arithmetic returns with:

![images](images/img_4_27.jpg)

with *NAV*[*i,0*] = 100 (end of January 2003).

## **1.2.2.** ***Factor representation***

A factor model is a multivariate regression linking the returns of a set of risky assets to several factors. We focus our attention on linear factor models where the relationship between factors and returns is linear.

Factors represent fundamental data, statistical factors or specific portfolios. Fundamental data are specified using economic theory and the knowledge of financial markets and include macroeconomic variables such as the inflation rate, the unemployment rate and the gross national product. Typically, macroeconomic variables are correlated.

To select uncorrelated factors, empirical dimension reduction techniques, such as factor analysis (FA) or principal component analysis (PCA), are performed on the covariance matrix of the returns of the risky assets. It gives rise to *eigenfactors* arising from an eigenvalue decomposition of the covariance matrix.

However, factors can be substituted by specific portfolios, especially if they represent different strategies that an investor can pursue at a low cost. The factors represent the various sources of risk present in the market to which an investor is exposed.

We now introduce the following linear factor model specification. The returns of a set of *N* risky assets indexed by *i* = 1, …*, N* are assumed to be wide-sense stationary, and can be expressed, for *t* = 1, …*, T*, by:

[\[1.4\]](#c01.xhtml#eqn1_4) ![images](images/img_6_28.jpg)

where:

– r[*t*] = \[*r*[[1],t], …*, r*[*N,t*]\]′ is the *N*\-dimensional vector of the risky asset returns at time *t*; – f[*t*] = \[*f*[1,t], …*, f*[^K,t]\]′ is the *K*\-dimensional vector of values of *common risk factors* at *t* whose covariance matrix is Σ[f] ; – B = \[b[1], …, b^K \] is a *N* × *K* matrix where each element *b*[*i,k*] ^∈ IR defines the exposure (or sensitivity) of the asset *i* to risk factor *k*. The sensitivities of asset *i* to the *K* factors are the *K*\-dimensional row-vector b′[*i*] = \[*b*[*i*,1], …*, b*[*i*,]^K \]. It is also referred to as the *beta*; – *α* = \[*α*[1], …, *α*[*N*] \]′ denotes the *N*\-dimensional vector of intercepts and is called *alpha*; and – *![images](images/e.gif)*[*t*] = \[![images](images/e.gif)[1,t], …, ![images](images/e.gif)[*N,t*]\]′ is the *N*\-dimensional vector of the zero-mean asset-specific residual returns whose covariance matrix is Σ[![images](images/e.gif)]. 

In \[1.4\], the unknown *N* × (*K* + 1) matrix of parameters is Θ = \[*θ*[1], …, *θ*[*N*] \]′ = \[*α* B\] and the inputs of the model are r[*t*] and f[*t*]. Let *![images](images/e.gif)*[*i*] = \[![images](images/e.gif)[*i*,1], …, ![images](images/e.gif)[*i,t*] \]′ and *f*[*k*] = \[*f*[k,1], …*, f*[*k,T*] \]′ denote the *t* -dimensional vectors of, respectively, the residual returns of asset *i* and the values of factor *k*.

Additional assumptions are made for \[1.4\]:

A1) The residual returns are uncorrelated with each of the factors: IE ![images](images/Inline_30_10.jpg)\= 0[*T*], *i* = 1, …*, N*, *k* = 1, …*, K*. A2) The residual returns are temporally uncorrelated: IE ![images](images/Inline_30_11.jpg)\= 0[*N*] for *t*[1] ≠ *t*[2]. A3) The residual returns are uncorrelated, that is Σ[![images](images/e.gif)] is a diagonal matrix. 

Assumption A3 means that the only sources of correlation among asset returns are those that arise from their exposures to the factors and the covariances among the factors. Residuals of asset returns are assumed to be unrelated to each other and hence totally *specific* to each asset. In other words, the risk associated with the residual return is *idiosyncratic* to the asset in question.

Note that the covariance matrix of the asset returns specified by \[1.4\] is:

\[1.5\] ![images](images/img_2_30.jpg)

The right-hand side of \[1.5\] consists of two distinct terms: BΣ[f] B′ is called the *systematic risk*, that is the risk explained by the *K* common factors and also known as *non-diversifiable risk*, *beta risk* or *market risk*.

The second term, Σ[![images](images/e.gif)], is called the *idiosyncratic risk*, also known as *diversifiable risk* or *asset-specific risk* and is totally specific to the assets.

As opposed to the *non-diversifiable systematic risk*, an investor has the possibility to reduce the amount of the *asset-specific risk* by properly diversifying his (or her) investments. Note also that Σ[f] is diagonal when *eigenfactors* are selected.

When *N* is large, using \[1.5\] helps to narrow down the dimensionality to estimate the covariance matrix Σ[r]. On the one hand, the number of terms that must be estimated reduces significantly and on the other hand, *K* < *t* usually meets the requirement to obtain an invertible estimated covariance matrix.

# **1.3. Why factor models in finance?**

## **1.3.1.** ***Style analysis***

Let us consider a portfolio of *n* risky assets whose returns are *r*[*i,t*]*, i* = 1*, …, N*. The portfolio returns are denoted by *r*[*p,t*] and are obtained from *r*[*i,t*]*, i* = 1*, …, N* by the following formula:

![images](images/img_11_30.jpg)

where r[*t*] = \[*r*[1,t], …*, r*[*N,t*]\]′ and a = \[*a*[1], …, *a*[*N*] \]′ is the vector of (fixed) weights of assets in the portfolio. The distribution of *r*[*p,t*] depends directly on the joint distribution of the vector r[*t*], which can be considered as the factors explaining the portfolio performance. However, these factors can be highly correlated and/or unobserved (when we do not know the portfolio manager investment universe). A more parsimonious and tractable representation is then obtained using a small number of observed factors correlated with the portfolio performance. However, we must consider in this case the potential error made in explaining portfolio returns with a set of “common” factors. This explains why we introduce error terms in the linear factor representation.

A given portfolio allocation basically reflects the portfolio manager’s bets. If we assume that these bets remain unchanged over the whole observation period, then the approach described above is relevant. However, from a practical standpoint, these bets are in general time-varying. The portfolio manager reallocates his/her portfolio on a continuous basis, and only the average exposure to factors is obtained through this classical return-based style analysis (see \[SHA 92\] for greater details on this approach). The linear combination of factors exposures and their respective performance gives then the strategic or long-term portfolio benchmark. The value added by the portfolio manager (or market timing ability) is then defined as the return difference between this portfolio returns and the strategic long-term benchmark (see \[DAR 12\]).

As a portfolio manager’s bets are made on a continuous basis, it could also be interesting to track their impacts on the portfolio performance in the short term. Tactical portfolio allocation decisions rely on short-term portfolio manager’s forecasts of risk premia (bets on factors) and can, as a result, also be captured using a linear factor model, but with time-varying exposures. Since information arrives randomly, and tactical bets are assumed to be responses to new information, we expect the exposure to risk factors to evolve randomly over time. [Equation \[1.4\]](#c01.xhtml#eqn4) in this case becomes:

![images](images/img_3_32.jpg)

where B[*t*] (respectively, *α*[*t*] ) denotes the time-varying exposure of assets to factors (respectively, alpha). Risk factor exposures are not directly observed and must be filtered from **r**[*t*].

Let us consider the case of a portfolio of hedge funds (or fund of hedge funds). Hedge funds are used in the following chapters to give empirical illustrations. Although the trend is very clearly toward more transparency, investors do not systematically have access to the full composition of hedge funds, and their evolution over time. Fund of hedge fund managers themselves do not always have a complete view of the risk factor exposures of their underlying investments, and, as a result, of the bets they implicitly make. This is all the more true when the trading frequency of the underlying funds is significantly higher than their reporting frequency (i.e. embedded risks can be dramatically different from those shown at a specific date), or when the number and the diversity of positions make it difficult to come up with accurate aggregated factor exposures. Tactical bets explicitly (at the portfolio level) and implicitly (at the underlying level) made by the fund of hedge fund manager can alternatively add up or cancel each other. Using a return-based style analysis therefore allows us to mitigate one of the main shortcomings of holding-based approaches, by capturing and assessing both effects concomitantly.

This example shows that this return-based style analysis must be done with time-varying parameter to filter from portfolio returns both long-term and short-term bets.

## **1.3.2.** ***Optimal portfolio allocation***

Let us consider a portfolio of *N* risky assets whose returns are *r*[*i,t*]*, i* = 1*, …, N*, with *N* large. According to Markowitz’s \[MAR 52\] theory, optimal diversified portfolios are obtained by inverting the covariance matrix of asset returns Σ[r]. This matrix is unknown, and we have to estimate it from observations *r*[*i,t*]*, i* = 1*, …, N, t* = 1*, …, T* by using, for example, the empirical covariance matrix:

![images](images/img_3_33.jpg)

where r[*t*] = \[*r*[1,t], …*, r*[*N,t*]\]′ is the vector of asset returns. If the dimension *t* is lower than *N*, then ![images](images/Inline_34_5.jpg)is not invertible, and the optimal Markovitz’s portfolios cannot be computed. Moreover, even in the case where *N* is lower than *T*, this empirical covariance matrix can have a determinant close to zero, and we can encounter numerical problems when trying to invert it with the usual algorithms. This is, in particular, the case when correlations between assets are high. Factor models can be used to manage these high correlations and therefore give an alternative to the direct numerical inversion approach.

Let us develop these computations in the very simple case \[1.4\]. We assume in the following that the risk-free rate is set to zero and excess risky asset returns r[*t*] satisfy the following linear single risk factor model:

![images](images/img_7_33.jpg)

where the unobserved single factor *f*[*t*] is assumed to be Gaussian ![images](images/Inline_34_9.jpg)and ![images](images/e.gif)[*i,t*]*, i* = 1*, …, N* have Gaussian distribution ![images](images/Inline_34_10.jpg). The expected excess return is IE(*r*[*i,t*]) = *b*[*i*] *m*[*f*] and the idiosyncratic risk ![images](images/Inline_34_11.jpg)The systematic source of risk (i.e. the unobserved single factor) creates an additional individual risk equal to ![images](images/Inline_35_2.jpg)but also a covariance between excess returns of two different assets:

![images](images/img_3_34.jpg)

for *i* ≠ *j*. This covariance term can lead to correlation close to 1 when the systematic risk is high relative to the idiosyncratic risk. However, we can compute explicitly the mean-variance optimal allocation. The vector of efficient allocations in the *N* risky assets is indeed proportional to:

![images](images/img_5_34.jpg)

where r[*t*] = \[*r*[1,t], …*, r*[*N,t*]\]′. Using the factor structure, we can explicit the two first moments of r[*t*] and get the following closed-form formula:

![images](images/img_7_34.jpg)

where B = \[*b*[1], …*, b*[*N*] \]′. We then obtain the efficient allocation by estimating the parameters involved in the previous formula, without having to numerically invert the covariance matrix.

In this example, the single factor is unobserved and then must be filtered from asset returns, or replaced by a proxy that is able to explain all the correlation structure observed between risky assets.

# **1.4. How to build factor models?**

## **1.4.1.** ***Factor selection***

The factor selection problem is not new in the financial literature. The main issue is related to the delicate balance between using too many or too few factors. On the one hand, adding too many factors lowers the regressors efficiency when we estimate factor exposures using [equation \[1.4\]](#c01.xhtml#eqn4). On the other hand, working with too few factors also has an important risk of missing the correlation structure observed between asset returns. This raises the question whether it is possible to build a factor selection methodology allowing us to consider only the appropriate factors.

The first solution consists of using a predefined set of observable factors, already documented in the financial literature for their ability to explain the cross-section of asset returns. These factors are used to build long- and short-term benchmarks in the style analysis of section 1.3.1. They are also used to reduce the dimension of the covariance matrix, when optimal portfolio allocation must be computed for a large set of risky assets in section 1.3.2. If we miss some risk factors in the style analysis, both long- and short-term benchmarks are misspecified, and the portfolio manager’s added value is not correctly calculated. In particular, we can interpret positive risk-adjusted returns as a manager’s skills and omit an important risk exposure. In the portfolio allocation example, omitted factors imply residual correlations between idiosyncratic risk terms. As these correlations are not taken into account in the calculation of the optimal portfolio, we underestimate the portfolio risk or, in other words, we overestimate the diversification effect.

A second solution is to use statistical approaches to filter from the asset returns distribution (and, in particular, the covariance matrix) unobservable factors that are able to explain the cross-section of asset returns. If this approach seems appealing to a statistical point of view, it has also many drawbacks from a financial point of view. First, it is, in general, difficult to give an economic interpretation of these statistical factors. Second, the factor representation is not unique, and any linear combination of a given set of factors defines an equivalent factor model. Third, the factor decomposition is, in general, time-varying and then difficult to interpret. Both approaches are described in detail in Chapter 2.

## **1.4.2.** ***Parameters estimation***

Once a set of factors is chosen, parameters estimation consists of computing numerical values of factors exposures. When parameters are not time-varying, least squares (LS) approaches can be used to compute these estimators, depending on the residual properties. However, both in the style analysis of section 1.3.1 and the optimal portfolio allocation problem of section 1.3.2, parameters can be time-varying and more complex statistical filtering approaches must be used (see e.g. \[BOL 09, PAT 13\]) such as the Flexible Least Squares \[KAL 89, MAR 04\], the Kalman filter (KF) \[RON 08a, RON 08b, RAC 10\] or Markov switching regimes \[BIL 12\].

The LS estimator can always be computed on rolling windows, updated each time we get new data. This provides a time series of estimators that have then a time-varying behavior. However, this approach, if useful when changes in parameters over time are smooth, can be misleading when big changes occur. A style analysis computed using rolling window LS can miss a sudden style rotation decided by the portfolio manager. On the contrary, this estimation method provides very good results when style drifts are small and/or implemented step by step.

The KF approach is by definition more reactive and can capture in theory quick style rotations. However, this approach works well only when the relevant factors are used in [equation \[1.4\]](#c01.xhtml#eqn4). Indeed, assumptions made up of the statistical behavior of the residual returns are more constraining, and any failure can have a huge impact of the filtered time-varying exposures. It is, for example, the case when residual returns do not follow a Gaussian distribution. Commonalities and discrepancies between LS and KF are discussed in Chapter 3, and an enhanced version of KF is discussed in Chapter 4.

# **1.5. Historical perspective**

Factor models have been the focus of numerous studies in empirical finance since Treynor \[TRE 62\], Sharpe \[SHA 64\], Lintner \[LIN 65\] and Mossin \[MOS 66\] developed the capital asset pricing model (CAPM) in the 1960s.

## **1.5.1.** ***CAPM and Sharpe’s market model***

CAPM lays the foundation for all the existing factor models. It gives the theoretical *equilibrium* relationship that should occur between the returns and the risks of individual assets with regard to the market returns.

Its conception is based on two fundamental financial concepts: market equilibrium that occurs if the amount of demand is balanced by the amount of supply (represented by the market portfolio), and, as a result, the mean-variance efficiency of the market portfolio.

Given the risk-free rate *r*[*f*] and the risk *σ*[*m*] of the market portfolio *m*, the CAPM stipulates that the returns we expect from individual assets in excess of *r*[*f*] are given in proportion to the excess returns expected from the market, as follows:

\[1.6\] ![images](images/img_8_37.jpg)

where ![images](images/Inline_39_2.jpg)is related to the amount of risk given by *i*, with **γ**[*im*] being the covariance between *r*[*i*] and *r*[*m*]. Larger values of *β*[*i*] correspond to larger expected return and larger risk for asset *i*. The term (IE(*r*[*m,t*]) − *r*[*f*] ) is called market risk premium.

In practice, the unknown parameter *β*[*i*] is estimated through the following univariate regression using historical data for the asset returns, the market portfolio and the risk-free rate:

\[1.7\] ![images](images/img_4_38.jpg)

where ![images](images/e.gif)[*i,t*] satisfies IE(![images](images/e.gif)[*i,t*]) = 0. Additional parameter *α*[*i*] is the asset *alpha*. The strict form of \[1.6\] specifies that *alpha* must be zero and that deviation from zero is the result of temporary disequilibrium. With *α*[*i*] = 0 in \[1.7\], this model coincides with Sharpe’s market model that is an output of \[1.6\]. The market portfolio is usually replaced by a major standard equity index (such as the S&P500) since Black \[BLA 72\] has shown that in market equilibrium, such market-value weighted indices are always efficient. The parameter *α*[*i*] can be used to perform fitted performance analysis (see \[DAR 10\]).

CAPM results can be represented by the so-called security market line (SML) as shown in [Figure 1.2](#c01.xhtml#fig2). The SML is the plot of the expected return of any asset *i* as a function of its *beta*, as given by \[1.6\]. It is obtained for a fixed period of time through \[1.6\] where *r*[*f*] is the mean of the risk-free asset returns, IE(*r*[*m,t*]) is the mean of the returns for the proxy of the market portfolio and where some theoretical values for the *β*[*i*]s are chosen. For each risky asset *i*, *α*[*i*] and *β*[*i*] are estimated through \[1.7\] and ![images](images/Inline_39_8.jpg)is the estimated mean of its returns. According to CAPM, given ![images](images/Inline_39_9.jpg)if ![images](images/Inline_39_10.jpg)does not lie on the theoretical SML, then the asset is mispriced.

In practice, this model has received several criticisms (e.g. see Roll’s critique \[ROL 77\]). First, the market portfolio is unobservable. Standard equity indices usually substitute for it but do not reflect all the wealth in the economy as the market portfolio does. Second, the mean-variance approach depends only on the first two moments of the asset returns, which is too restrictive.

[**Figure 1.2.**](#c01.xhtml#fig2_1) *The security market line (SML, the black line) shows the expected return of asset i as a function of its beta, as given by* \[1.6\]*, and given in annualized values over the period August 2004 / October 2010: r[*f*]* = 2.93%*, IE*(*r[*m,t*]*) = 4.41%*, and σ[*m*]* = 22.81%*. Here, r[*f*] is the average rate of the US T-Bill 1 year over the whole period, m is the S&P500 and the risky assets are some of its components. Each (blue) point has for coordinates* ![images](images/Inline_40_3.jpg)*– the estimated values, for asset i, of β[*i*] and IE*(*r[i,t]*)*. If* ![images](images/Inline_40_4.jpg)*is lower (respectively, higher) than IE*(*r[i,t]*)*, obtained from* \[1.6\] *given r[*f*], IE*(*r[*m,t*]*) *and* ![images](images/Inline_40_5.jpg)*then the asset is said to be under (respectively, over) valued. Stocks with an \* have significant (at 99.5%) non-zero α[*i*]*

![images](images/img_6_39.jpg)

Finally, empirical studies often invalidate the CAPM because of its strong assumptions and show that more than one factor is necessary to identify the market risks.

## **1.5.2.** ***APT for arbitrage pricing theory***

Ross \[ROS 76\] and Roll and Ross \[ROL 77, ROL 80\] developed an alternative *arbitrage* model to the CAPM, called APT model. APT follows from two basic postulates:

P1) the risky assets follow a *K-factor structure* like \[1.4\] with three additional assumptions: A4) *K* << *N*; A5) IE(*f*[*k*] ) = 0, *k* = 1, …*, K* that leads to IE(r[*t*]) = *α*; A6) ∃ *s* < ∞such that ![images](images/Inline_41_7.jpg)P2) pure *arbitrage* profits are impossible. 

Pure arbitrage profits are risk-free profits at zero cost: an investor can earn a positive return on any combination of assets without undertaking risk and without making some net investment of funds. With P1 and P2, APT stipulates that the risk premiums of the risky assets are given through a linear combination of the factor *risk prices* weighted by the factor sensitivities b[*i*] of \[1.4\]:

\[1.8\] ![images](images/img_10_40.jpg)

where **λ**[*k*] defines the *price of risk* for factor *k*. The full APT expression is then obtained by replacing *α*[*i*], *i* = 1, …*, N* in \[1.4\] by \[1.8\]. Jointly estimating the *K*\-dimensional vectors b[*i*] and *λ* = \[**λ**[1], …**, λ**^K \]′ is not trivial. In practice, a two-pass methodology can be used: first estimate b[*i*] through \[1.4\] (giving rise to ![images](images/Inline_41_13.jpg)then use ![images](images/Inline_41_14.jpg)as input to estimate *λ* through:

![images](images/img_15_40.jpg)

where ***u***[*i,t*] represents zero-mean residual errors with usual assumptions. Unlike the CAPM, APT does not provide any information about the nature of the *K* factors.

# **1.6. Glossary**

### ***Volatility***

The volatility *σ* of an asset *a* refers to the standard deviation of the continuously compounded returns of *a* within a specific time horizon. Volatility is usually expressed in annualized terms: if the volatility *σ* is computed using daily (respectively, weekly) returns and if we consider that a year is made us of 250 business days (respectively, 52 weeks), then the annualized volatility will be equal to ![images](images/Inline_42_5.jpg)(respectively, ![images](images/Inline_042_5.jpg).

### ***Risk***

The risk of holding an asset *a* may be quantified by the volatility of *a*.

### ***Risk-free rate***

The theoretical rate of return of an investment with zero risk; the risk-free rate, commonly denoted *r*[*f*], represents the minimum return an investor expects for any investment when taking no risk. This is often considered as a lower bound of what should at least give any riskier investment since bearing any risk should be more remunerating than a risk-free investment.

### ***Expected (excess) return***

The expected return of an asset *a* is the return on *a* expected in the future and is computed by IE(*r*[*a*]). The expected excess return is the expected return on *a* in excess of the return given by the risk-free rate (or by any other market measure): IE(*r*[*a*]) −*r*[*f*].

### ***Risk premium***

The risk premium of an asset *a* is the expected return on *a* in excess of the risk-free rate, that is IE(*r*[*a*]) −*r*[*f*].

### ***Zero-cost portfolio***

A zero-cost portfolio is a portfolio for which the weights add up to zero. For example, the excess return of an asset *a*, that is IE(*r*[*a*]) − *r*[*f*] is a zero-cost portfolio. It invests 100% in *a* and −100% in the risk-free rate. The amount borrowed at *r*[*f*] is invested in *a*. As the investor will have to pay the interest for borrowing money at *r*[*f*], he/she would therefore expect to receive more than *r*[*f*] in return for his/her investment in *a*.

### ***Tradable portfolio***

A portfolio is said to be tradable if it is a zero-cost portfolio.

### ***Portfolio diversification***

Diversifying a portfolio is the act of adding more investments to one’s portfolio to reduce the risk inherent in any one investment. It increases the possibility of making a profit, or at least avoiding a loss. In general, the broader the diversification, the less is the risk and the return. Adding more investments to the portfolio for diversification involves subdividing the portfolio among many smaller investments. If the portfolio’s size increases instead of remaining constant, the portfolio’s risk may not decrease especially if the assets added in the portfolio are uncorrelated. Here is a very simple example of diversification benefits on the variance of the portfolio. If the *N* assets in the portfolio are mutually uncorrelated and have identical variances *σ*², portfolio variance is minimized by holding all assets in the equal proportions 1/*N*. Then, the portfolio variance equals *σ*²/*N* that is monotonically decreasing in *N*. So, even if the added assets are uncorrelated, the portfolio variance decreases. Benefits of diversification amplify when adding negatively correlated assets in the portfolio. The modern understanding of diversification dates back to the work of Harry Markowitz \[MAR 52\] in the 1950s.

### ***Market portfolio***

A market portfolio is a perfectly well-diversified portfolio and represents the evolution of the market as a whole. In the factor model framework, a perfectly diversified portfolio admits a pure factor structure, that is a factor structure where there is no additional idiosyncratic risk.

### ***Market efficiency***

The market is said to be efficient if the price of the assets in the market reflects all information available.

### ***Market equilibrium***

The market equilibrium occurs if the amount of demand is balanced by the amount of supply. In this condition, the prices should tend not to change unless demand or supply change.

### ***Arbitrage***

Arbitrage is the possibility of a risk-free profit at zero cost. For example, if the same asset does not trade at the same price on all markets, buying and selling this asset simultaneously and instantaneously on two different markets will take advantage of the price difference.

### ***Market capitalization***

Market capitalization, also known as Market Cap. or cap. (MC), is the number of outstanding shares of a firm times the price of its share in the market. MC measures the size of the firm. It changes every day because of the quoted firm price (P). For example, in October 24, 2010, the six largest MC in the world were (T$ is for trillions US dollars and B$ for billions US dollars):

(1) Telecom Brasil with MC = T$6.57 and P = $5.99, (2) Exxon Mobil with MC = B$337.69 and P = $66.32, (3) Apple with MC = B$282.77 and P = $309.52, (4) PetroChina with MC = B$229.20 and P = $125.23, (5) BHP Billiton with MC = B$224.83 and P = $80.81, and (6) Microsoft with MC = B$219.97 and P = $25.42. 

# Chapter 2

# Factor Selection

# **2.1. Introduction**

The use of factor models requires the determination of the nature and the number of the factors. Two approaches can be distinguished in the literature: the empirical *ad hoc* approach and the statistical approach which involve subspace methods and lead to the so-called *eigenfactors*.

Empirical studies generally compare the two approaches (see \[CHE 93, CON 95, CHA 98, DAR 11\]) and mostly emphasize the superiority of eigenfactors over macro-economic factors regarding their expected properties (uncorrelated factors) and the percentage of the explained part of the systematic returns they contain. Eigenfactors are nevertheless difficult to relate to observed macro-economic factors which lower in a certain sense their attractiveness to practitioners.

This chapter is organized as follows: section 2.2 focuses on the empirical *ad hoc* approach and presents three reference models that are widely used in the literature. These models are all based on the factor representation described in Chapter 1 (see section 1.4), but highlight the nature (and the number) of the factors to be used to explain specific asset class returns. In section 2.3, we present the statistical approach. As opposed to the empirical factor selection where *a priori* knowledge on the observed data is required, the purely statistical approach extracts a smaller group of implicit eigenfactors from the time series of the observed returns which explain a large amount of information contained in the observed data. The problem is then to determine the order of the resulting model. Some classical techniques, arising from the information theory, are described in section 2.4. Sections 2.5–2.7 are complementary sections giving some light on related problems to this approach such as the estimation of the covariance matrix of the data, the similarity of the approach with subspace methods and the extension of this approach to large panel data.

# **2.2. Qualitative know-how**

In an empirical *ad hoc* approach, the nature and the number of factors are chosen with some *a priori* consideration of the market conditions. The factors are observable market risk factors and are included in the model through a discretionary choice. They also depend on the class of assets under study so that the mis-specification risks are non-negligible.

A substantial amount of work is available on the subject in the literature, so, in this section, we present three major reference models: the factor model of Fama and French \[FAM 93\], the Chen *et al.* model \[CHE 86\] – two models developed to explain the risks in the US equity market, and the risk-based factor model of Fung and Hsieh \[FUN 01, HSI\], a model adapted to explain the risks bourne by the trend-follower hedge funds.

## **2.2.1.** ***Fama and French model***

The three-factor model of Fama and French \[FAM 93\] is an extension to the capital asset pricing model (CAPM). Observing that *small caps* and *value* stocks outperformed the market on a regular basis, Fama and French included two additional factors to Sharpe’s market model: *SMB* for *small minus big* (market capitalization, MC), which reflects the relative performance of the small versus large caps stocks, and *HML* for *high minus low* (book-to-market value), which reflects the relative performance of the high-valued versus the low-valued stocks. MC gives information about the size of the firm (equal to the stock price times the number of its outstanding shares). Book-to-market ratio is related to the accounting value of the firm (equal to the MC of the firm divided by the accounting value of all the firm’s shares).

For example, SMB factor may be constructed at time *t* as follows, for a fixed period of time of length *T* (from *t* – *T* to *t*):

– consider a large universe of stocks in the equity market, for example take the constituents of the Russel 2000 equity Index at *t*; – for each stock in the universe, get its MC from *t* − *T* to *t*; – for each date, rank the stocks according to their relative MC; – to obtain the relative performance of the small versus the large caps stocks, compute, for each date, an equi-weighted (or a market cap weighted) portfolio composed of the stocks having an MC lower (respectively bigger) than a specific value; – SMB factor returns are then computed as the difference between the returns of the small MC portfolio and the big MC portfolio. 

The procedure is identical to construction of the HML factor but is based on the values of the book-to-market value of the stocks instead of their MC values.

This approach is used, for example, by Morningstar to rate stocks and mutual funds using a five stars grid[¹](#c02.xhtml#fnt1).

The four-factor model of Carhart \[CAR 97\] is an extension of the three-factor model of Fama and French \[FAM 93\], including a momentum factor. The model is shown to explain persistence in equity mutual funds’ mean and risk-adjusted returns.

## **2.2.2.** ***The Chen et al. model***

The Chen *et al*. \[CHE 86\] model is a particular case in the arbitrage pricing theory (APT) framework. Studying the stocks in the US market, the authors identified a set of economic state variables that were significant in explaining the expected stock returns: industrial production, changes in the risk premium, twists in the yield curve, measures of unanticipated inflation and changes in inflation during high volatile periods for these variables. Whereas a value-weighted stock equity index explains a significant portion of the time series variability of stock returns, it has an insignificant influence on pricing (i.e. on expected return) when compared against the above state variables.

As opposed to the Fama and French model, this factor model contains only observed macro-economic factors, so that there is no other specific procedure to construct such a model than getting from a data provider the time series of the above cited factors on the period where the study is conducted.

## **2.2.3.** ***The risk-based factor model of Fung and Hsieh***

The eight-factor model of Fung and Hsieh (*F&H model* \[FUN 01, HSI\]) is a risk factor model adapted to trend-follower hedge funds. Hedge funds are non-quoted speculative funds seeking high expected returns theoretically uncorrelated with the market. Hedge fund managers can borrow money to substantially *leverage* their profitability, often at a factor of 10 to 1, or more. They usually purchase derivative products (such as options) and take *short* positions to also benefit from downward movements of the assets. The positions are managed dynamically. As a result, hedge funds exhibit nonlinear option-like exposures to the standard asset classes that cannot be captured by the traditional linear factor models. A growing body of literature is devoted to finding accurate hedge fund risk factors (see \[AGA 00a, AGA 00b, AGA 04, AGA 09, SAD 10\]), and one of the most famous hedge fund risk models is the F & H model. It recommends seven asset-based risk factors and one emerging market risk factor to describe the risks of the *trend-follower* hedge funds and is composed of \[HSI\]:

1) three customized *trend-following* risk factors, which are specific portfolios, constructed by the authors using an appropriate mix of options (or more precisely *lookback straddles*) that allow the characterization of pure directional positions taken by the *trend-follower* hedge fund managers on three different asset classes: i) *PTFSCOM*, representing the returns of a specific portfolio invested in commodities, ii) *PTFSBD*, representing the returns of a specific portfolio invested in bonds, and iii) *PTFSFX*, representing the returns of a specific portfolio invested in foreign exchange; 2) two *equity-oriented* risk factors, which are based on equity market indices: i) *SP500* represents the total return of the Standard and Poors 500 equity index, and ii) *EquitySizeSpread* represents the performance of the smallest MC of the US Equities as being the difference between the total returns of the large Russel 2000 equity index (composed of the 2,000 largest MC in the US equity market) and *SP500*; 3) two *bond-oriented* risk factors, representing the bond market: i) *Bond10y* is the monthly change in the 10-year treasury constant maturity yield, and ii) *CreditSpread* is the monthly change in the Moody’s Baa yield less 10-year treasury constant maturity yield; 4) the recently added emerging market index factor: i) *MXEF*, representing the total returns of the Morgan Stanley Capital International (MSCI) emerging market index. 

The eight risk factors of Fung and Hsieh are available on the author’s webpage (see \[HSI\]) and are quoted monthly from January 1994. [Table 2.1](#c02.xhtml#tab1_1) gives some basic statistics on these factors on the period January 1994 to December 2012. These statistics are: the annualized return, the annualized volatility, the ratio between annualized return and the annualized volatility (denoted as the Sharpe ratio), the minimum and the maximum monthly returns on the period, and the skewness and the kurtosis of the return distribution.

[**Table 2.1.**](#c02.xhtml#tab1) *Averaged statistics and correlation for the eight risk factors of Fung and Hsieh. Computation of the statistics is made on monthly returns from January 1994 to December 2012*

![images](images/img_2_52.jpg)

[**Figure 2.1.**](#c02.xhtml#fig1) *Net Asset Values (NAVs) of the eight risk factors of Fung and Hsieh. The NAVs are based at 100 in December 1993 and end in December 2012*

![images](images/img_4_52.jpg)

As an illustration, [Figure 2.1](#c02.xhtml#fig1_1) shows the evolution of these factors if we had invested 100 in each of them in December 1993, and [Figure 2.2](#c02.xhtml#fig2_1) represents the correlation matrix between these factors computed with monthly factor returns from January 1994 to December 2012. Two groups of anti-correlated factors can be distinguished: the first group, composed of *SP500*, *EquitySizeSpread*, *MXEF* and *Bond10y* are negatively correlated with the other four factors. Moreover, within each group, we observe a quite weak (positive or negative) correlation between the factors, excepted for the two equity-based risk factors (which are positively correlated at approx. 60%) and the two bond-related risk factors (which present a negative correlation at approx. 45%).

**[Figure 2.2](#c02.xhtml#fig2).** *Empirical correlation matrix of the eight risk factors of Fung and Hsieh from December 1993 and end in December 2012 (see color plate section)*

![images](images/img_3_53.jpg)

Macro-economic factors are naturally correlated. To avoid correlation between the returns of the different asset class factors, the factors may be selected through a stepwise regression technique \[AGA 00b\]: the factors are entered or removed from the model, one at a time, depending on their relative discriminant power. Used in its ascending version, the single best factor is chosen first, then paired with each of the other variables, and the second best factor is chosen, and so on. The order of the model increases until adding a new factor does not improve the discriminant power of the previous model. Used in its descending version, the initial model contains all the pre-selected factors and removes, one at a time, the worst factor, until removing one of the remaining factors does not improve the discriminant power of the previous model.

# **2.3. Quantitative methods based on eigenfactors**

In this section, we denote by *eigenfactors* the factors obtained from the observations using the eigenvector decomposition of the covariance matrix of the returns. In the literature on empirical quantitative finance, *eigenfactors* might be viewed as special *latent factors* that are a subset of vectors obtained from linear combinations of returns. Such methods are often used when there is no *a priori* knowledge on the economic factors that may drive the data under study and give the remarkable property of yielding to orthogonal factors especially when subspace methods are used to derive such factors.

In the statistical literature, the most frequently used methods are the Factor Analysis method and the Principal Component Analysis (PCA) method. Mainly used in order to reduce the dimensionality of the matrix of observations, such methods use the eigenvector decomposition of the correlation matrix and yield to components that are constructed as linear combinations of returns. The most important result is that the original data may be approximated with a high percentage of accuracy by keeping only a few eigenvectors that are selected such that their associated eigenvalues are the highest. The difficulty is therefore to determine the selection threshold. This part of the problem is discussed in section 2.4.

## **2.3.1.** ***Notation***

Let us assume that returns are stored in a *T* × *N* matrix R whose *N* columns represent *T* consecutive asset returns sampled at a regular frequency (e.g. on a daily basis, **…**):

\[2.1\] ![images](images/img_4_55.jpg)

If *μ* = IE(R) = \[*μ*[1] *μ*² … *μ*[N]\]′ denotes the *N*\-dimensional mean vector, then:

\[2.2\] ![images](images/img_7_55.jpg)

is the centered version of R.

If *σ* = \[*σ*[1] *σ*² … *σ*[N]\]′ denotes the *N*\-dimensional standard deviation vector and D a diagonal *N* × *N* matrix whose principal diagonal is *σ*, such that:

\[2.3\] ![images](images/img_11_55.jpg)

then let us define ![images](images/Inline_56_14.jpg)as the standardized version of r[*j*] which is then a zero-mean vector with a unitary variance. We also have:

[\[2.4\]](#c02.xhtml#eqn4_1) ![images](images/img_2_56.jpg)

The covariance matrix Σ[R] of R, defined as Σ[R] = *V ar*(R) = ![images](images/ch02_image004.gif), can therefore be expressed as:

\[2.5\] ![images](images/img_5_56.jpg)

Let us note that Σ[R] is symmetric. If Σ[R] is full rank, then Σ[R] is also definite positive, which means that its *N* eigenvalues are strictly positive. If it is not full rank then the matrix is semi-definite positive.

Several methods may be used to estimate the covariance matrix. The traditional sample covariance matrix (SCM) and robust approach with *M* estimators are presented in section 2.5.

## **2.3.2.** ***Subspace methods: the Principal Component Analysis***

The most commonly used method in financial applications to obtain *latent* factors is the PCA that makes an eigen-decomposition of the covariance matrix of returns. In this section, we assume that the covariance matrix is either known or estimated with any method (like those presented in section 2.5 or any other one), and we use the notation ![images](images/Inline_57_11.jpg)to designate the covariance matrix estimate.

Assume that the observations are standardized, that is we use ![images](images/Inline_58_2.jpg)as defined in \[2.4\] with ![images](images/Inline_58_3.jpg). In such a case, we then have tr ![images](images/Inline_58_4.jpg)

If ![images](images/Inline_58_6.jpg)designates an estimate version of ![images](images/Inline_58_7.jpg)then its eigen-decomposition can be written as:

[\[2.6\]](#c02.xhtml#eqn6) ![images](images/img_8_57.jpg)

where U = \[u[1] u[2] … u[N]\] is the *N* × *N* unitary matrix composed of the *N* eigenvectors corresponding to the *N* eigenvalues ![images](images/Inline_58_11.jpg)stored in a decreasing order (**λ**[1] ≥ **λ**² ≥ …≥ **λ**[N] ) in the *N* ×*N* diagonal matrix Γ.

Let us say that the *K* largest eigenvalues are stored in Γ[*K*]. We then have:

\[2.7\] ![images](images/img_14_57.jpg)

and

\[2.8\] ![images](images/img_17_57.jpg)

so that [equation \[2.6\]](#c02.xhtml#eqn6_1) can easily be rewritten as:

\[2.9\] ![images](images/img_20_57.jpg)

In many applications, *K* is linked to the order of the model: it is assumed that the observations come from *K* < *N* sources and the *N* − *K* remaining sources may be considered as noise. As an example, MUSIC algorithm (MUltiple SIgnal Characterization) \[STO 89, STO 97, TRE 02\] is commonly used for determining the number of sources in an array antenna as well as the angle of arrival. The signal space, defined by the *K* largest eigenvalues, is orthogonal to the noise space (the *N* − *K* smallest eigenvalues) so that projecting the observation on to the signal space allows for detecting the signal of interest.

Using the *K*\-dimensional subspace defined by Γ[*K*], and similarly by U[*K*] the *K* eigenvectors corresponding to the *K* largest eigenvalues, then the *K* estimated eigen factors ![images](images/Inline_59_3.jpg)are obtained by:

\[2.10\] ![images](images/img_4_58.jpg)

By construction, ![images](images/Inline_59_7.jpg)is a *T* -dimensional vector with:

\[2.11\] ![images](images/img_8_58.jpg)

The estimated eigenfactors are zero-mean with a diagonal covariance matrix Γ[*K*]. Each *T* -dimensional vector ![images](images/Inline_59_11.jpg)is a linear combination of the asset returns and can be interpreted as diversified and orthogonal portfolios in which we must invest so as to capture commonalities across the assets.

One major difficulty is therefore to estimate the value of *K*. Some of the most commonly used techniques coming from the information theory are described in the following section.

# **2.4. Model order choice**

Identifying *K*, the number of common factors, is one of the key tasks of factor models. After performing an eigen-decomposition of the covariance matrix estimate, the simplest procedure is to select the *K* largest eigenvalues given that various tests exist for determining if an eigenvalue is large:

1) Looking at the percentage of the total power contained in **λ**[*k*] : 

\[2.12\] ![images](images/img_4_59.jpg)

2) Computing the ratio of the (*k* + 1)th eigenvalue to the *k*th eigenvalue which has been declared to be large: 

\[2.13\] ![images](images/img_7_59.jpg)

It is obvious that the result of these tests will depend on the values chosen for *η*[1] or *η*[2]. More general criteria might be useful and two families of criteria appear: (1) the traditional and (2) those defined on large panel data and more specific to the factor model identification.

## **2.4.1.** ***Information criteria***

The first category of tests to detect the value of *K* are referred to as sequential hypothesis (SH) tests or sphericity tests, originating from the statistical field (see \[AND 63\]). The objective is to find the likelihood ratio between the hypothesis that the *N* − *K* smallest eigenvalues are equal versus the hypothesis that only the *N* − *K* − 1 smallest eigenvalues are equal. Anderson \[AND 63\] showed that for *T* ![images](images/great.gif)*N*, the *N* − *K* smallest eigenvalues clustered all around a small value *s*² and showed that a sufficient statistic is:

\[2.14\] ![images](images/img_2_60.jpg)

This ratio uses the ratio of the arithmetic mean of the *N* − *d* smallest eigenvalues to the geometric mean of the *N* − *d* smallest eigenvalues. If the *N* − *d* smallest eigenvalues are equal, then *L*(*d*) = 0. Asymptotically, statistics \[2.14\] correspond to a *χ*²((*N* − *d*)² − 1)-distributed variable, so that given a confidence interval and sequential tests a value for *d* can be determined.

A second category of tests adds a penalty function to *L*(*d*) which takes into account the degree of freedom of the model. It results in a function of *d* to be minimized and the classical Akaike information criteria (AIC) and minimum description length (MDL) tests can be written in such a way, that is *L*(*d*) + *p*(*d*) \[TRE 02, RIS 78\].

### 2.4.1.1. *Akaike information criteria*

Akaike \[AKA 74\] introduced an information-theoretic criterion which is well known as the AIC. This test can be conveniently written as:

\[2.15\] ![images](images/img_8_60.jpg)

so that we get the AIC estimated value ![images](images/ch02_image001.gif)by minimizing \[2.15\]:

\[2.16\] ![images](images/img_11_60.jpg)

It has been shown that AIC is inconsistent and, asymptotically, tends to overestimate the number of sources. However, for small *T*, the AIC generally has a higher probability of a correct decision if compared with the results obtained with the MDL test.

### 2.4.1.2. *Minimum description length*

MDL differs from AIC by the value of the penalty function added to the Anderson’s sufficient statistic *L*(*d*):

\[2.17\] ![images](images/img_4_61.jpg)

so that we get the MDL estimated value ![images](images/Inline_62_7.jpg)by minimizing \[2.17\]:

\[2.18\] ![images](images/img_8_61.jpg)

As opposed to the AIC, MDL estimate is consistent with the time dimension, that is *T* → ∞, MDL estimate approaches *K*. In practice, MDL is therefore preferred to AIC and Bayes information criterion (BIC).

# **2.5. Appendix 1: Covariance matrix estimation**

Subspace methods require the computation of the covariance matrix of the observations which is mostly estimated by the SCM. SCM is the solution of the maximum likelihood approach under the multivariate Gaussian assumption but suffers from non-robustness in the case of outliers in returns. In this section, we first give the expressions and the properties for the sample mean and SCM and then present a family of robust estimators, the *M*\-estimators.

**Figure 2.3.** *Comparison between the AIC and MDL criteria in the determination of the number of factors in a set of N* = 72 *Hedge Funds monthly returns of size T* = 144*. MDL indicates more clearly the cutoff point in the data set (K* = 6 *factors) whereas AIC is a monotonic decreasing function*

![images](images/img_2_62.jpg)

## **2.5.1.** ***Sample mean***

The sample mean gives an unbiased and consistent estimation of the mean of a vector and is computed as the arithmetic mean of its values:

\[2.19\] ![images](images/img_5_62.jpg)

where 1[*T*] denotes a *T* -dimensional vector of 1.

This estimator is:

![images](images/img_2_63.jpg)

It coincides with the maximum likelihood estimator if the vector of observations is a Gaussian white random vector.

## **2.5.2.** ***Sample covariance matrix***

The maximum likelihood estimate ![images](images/Inline_64_6.jpg)of Σ in the Gaussian case is:

\[2.20\] ![images](images/img_7_63.jpg)

This estimator is:

![images](images/img_10_63.jpg)

So, if we define ![images](images/Inline_64_12.jpg)then S is the so-called unbiased SCM and we have:

\[2.21\] ![images](images/img_14_63.jpg)

\[2.22\] ![images](images/img_15_63.jpg)

\[2.23\] ![images](images/img_17_63.jpg)

COMMENT 2.1.– If the observations are zero-mean or if the mean vector *μ* is known, then the maximum likelihood estimate ![images](images/Inline_64_20.jpg)of the covariance matrix is unbiased and ![images](images/Inline_64_21.jpg)

*Some asymptotic results*:

\[2.24\] ![images](images/img_2_64.jpg)

\[2.25\] ![images](images/img_4_64.jpg)

[\[2.26\]](#c02.xhtml#eqn26_1) ![images](images/img_6_64.jpg)

In \[2.25\], *r* denotes the rank of Σ (if matrix is full rank, then *r* = *N*).![images](images/Inline_65_9.jpg)is the Hotelling’s T-squared statistic with parameters *N* and *T* − 1 \[HOT 31\]. Hotelling’s T-squared statistic, developed by Harold Hotelling, is a generalization of Student’s T-test statistic and is often used in multivariate hypothesis testing. When a random variable ![images](images/Inline_65_10.jpg)then ![images](images/Inline_65_11.jpg)where *F*[*p,n*−p*+*1] is the *F* -distribution with parameters *p* and *n* − *p* + 1 also called Snedecor’s *F*\-distribution or Fisher–Snedecor distribution (see appendices A1.4 and A1.5).

*Gaussian case*: If the observations are Gaussian multivariate ![images](images/N.gif)(*μ*, Σ), then the maximum likelihood estimates ![images](images/Inline_65_13.jpg)and ![images](images/Inline_65_14.jpg)are derived by minimizing:

\[2.27\] ![images](images/img_15_64.jpg)

when (*T* − 1) ≥ *N* and where V = (*T* −1)S. Since the last term is positive, we only have to minimize:

\[2.28\] ![images](images/img_18_64.jpg)

Then, we have:

\[2.29\] ![images](images/img_2_65.jpg)

[\[2.30\]](#c02.xhtml#eqn30_1) ![images](images/img_4_65.jpg)

\[2.31\] ![images](images/img_6_65.jpg)

where ![images](images/w.gif)(*n*, A) denotes the Wishart distribution with parameters *n* and A (see appendix A1.6 or \[BIL 99\] for more details).

When the Gaussian assumption is not verified, then the SCM estimate may be corrupted by outliers and deviate from optimality so that methods using a robust approach for estimation should be preferred. Robustness of an estimator may be quantified by stable estimation results when the observed data deviate more or less slightly from the assumed model within a relatively large confidence interval. The literature in robust methods for estimation is large and was probably first stated in the 1960’s by John Wilder Tukey \[TUK 60, TUK 62\]. Peter J. Huber in \[HUB 64\] and \[HUB 67\] considered that given a distribution model, the true distribution lies in a neighborhood of the model, which may describe a theoretical approach for robustness. The *M*\-estimators are therefore introduced as a generalization of the maximum likelihood approach, which considers that the assumed model may be erroneous. In the same manner, Huber’s *gross error model* assumes that within a perfectly known distribution *G*, a piece of datum, say 0 ≤ *![images](images/e.gif)* ≤ 1, comes from an unknown distribution *H*, so that the complete characterization of the datum is given by distribution *F* = (1 − *![images](images/e.gif)*)*G* + **![images](images/e.gif)* H*.

In the following section, we discuss the family of the so-called *M*\-estimators \[HUB 64, HUB 77, MAR 76\], which offers an alternative to the classical SCM and comes also from the maximum likelihood theory \[CON 02, GIN 02\].

## **2.5.3.** ***Robust covariance matrix estimation: M-estimators***

Assuming that the *N* columns ![images](images/Inline_67_3.jpg)of R are independent, the *M*\-estimator of Σ is defined as the solution of the following equation:

\[2.32\] ![images](images/img_4_66.jpg)

where the function *u*(.) may follow the following conditions \[MAR 76\]:

1) *u*(*s*) is non-negative, non-increasing and continuous for *s* ≥ 0; 2) Defining *ψ*(*s*) = *su*(*s*), ∀*s* ≥ 0, *ψ*(**.**) is bounded with *K* = sup[*s*≥0] *ψ*(*s*); 3) *ψ* is non-decreasing and is strictly increasing in the interval where *ψ* < *K*; 4) There exists *s*[0] such that ![images](images/Inline_67_11.jpg)\> *N*^. 

### 2.5.3.1. *Huber’s* *M-estimator*

Huber’s *M*\-estimator is defined for the specific weighting function *u*:

\[2.33\] ![images](images/img_14_66.jpg)

where I1(*x*) is the indicator function defined by I1(*x*) = 1 if *x* is verified, 0 otherwise.

Huber’s estimator is then a solution to:

\[2.34\] ![images](images/img_19_66.jpg)

Function \[2.33\] is shown in [Figure 2.4](#c02.xhtml#Fig4_1). Parameters *a* and *β* are adjustable: *a* allows us to control the percentage of data to be attenuated and *β* allows us to control the distance between the asymptotic value of the estimator and its theoretical value. If *a* is large, then Huber’s estimator behaves like the SCM: it means that the amount of data to be considered as outliers or outside the main distribution is negligible, so that all the samples are taken into account in the estimation. On the other hand, if *a* is small, then Huber’s estimator tends toward the fixed point (FP) estimator. The latter is described hereafter.

**[Figure 2.4](#c02.xhtml#Fig4).** *Weighting function u of the Huber’s M-estimator when a* = 0.4 *and β* = 0.5

![images](images/img_3_67.jpg)

### 2.5.3.2. *The fixed-point (FP) estimator*

The so-called FP estimate ![images](images/Inline_68_6.jpg)of Σ is defined as a FP of a function *f*[N,Σ] such that:

[\[2.35\]](#c02.xhtml#eqn35_1) ![images](images/img_7_67.jpg)

where ![images](images/Inline_69_2.jpg)positive definite} with ![images](images/ch02_image002.gif)matrices with elements in ![images](images/Inline_69_3.jpg)}.

[Equation \[2.35\]](#c02.xhtml#eqn35) or equation ![images](images/Inline_69_8.jpg)has a solution of the form *α* Σ where *α* is an arbitrary scaling factor (see \[PAS 08\] for a detailed explanation). The name of this estimator comes from the eponymous algorithm that is used for its computation \[PAS 08, TYL 83\]. It has been shown that this estimator is consistent and unbiased \[PAS 06\]. Under particular statistical assumption for vector r, it may be possible to get its asymptotic distribution (e.g. if r is a complex Gaussian compound vector (like a spherically invariant random vector (SIRV)), then \[2.35\] tends, in law, toward a complex Gaussian vector \[PAS 05\]).

As mentioned above, the FP solution of [equation \[2.35\]](#c02.xhtml#eqn35) is up to a scalar *α*. To get one of the solutions, we may impose a specific normalization, such that ![images](images/Inline_69_9.jpg)\= *N*. Moreover, this norm may also be imposed on the theoretical covariance matrix.

The performance of the SCM, Huber’s and FP estimators is compared in [Figure 2.5](#c02.xhtml#fig5_1). Data are simulated from a standard Gaussian distribution with *T* = 250 observations and *N* = 100 assets. Some outliers are randomly introduced in the data and come from a Bernoulli–Gauss process of variance 15. We have assumed that 50% of each of the *N* observation vectors is corrupted with outliers. Moreover, in order to compute Huber’s *M*\-estimator, we have assumed that only 60% of the data are not corrupted, so that the parameter *α* is the value of a *χ*² variable with *N* degree of freedom within a 60% confidence interval.

[Figure 2.5](#c02.xhtml#fig5_1) shows that the SCM estimate is sensitive to outliers whereas the FP estimate is fully robust to outliers. Huber’s *M*\-estimate is somewhere between the both, depending on parameters *a* and *β*. As a reference, we have added the SCM estimate on the uncorrupted data.

**[Figure 2.5](#c02.xhtml#fig5).** *Comparison between the SCM, Huber’s and FP estimators of the covariance matrix of T* = 250 *i.i.d. normal returns of size N* = 100 *sampled from a ![images](images/N.gif)*(**0**, **I**)*. Some outliers (*50% *of the data) are randomly introduced in the observations sampled from a Bernoulli–Gauss process of variance* 15*. We have assumed, for Huber’s estimator, that* 60% *of the data come from a Gaussian distribution (see color plate section)*

![images](images/img_3_69.jpg)

# **2.6. Appendix 2: Similarity of the eigenfactor selection with the MUSIC algorithm**

As mentioned in section 2.3.2, the MUSIC algorithm \[STO 89\] uses the same methodology as principal component analysis does, that is it is based on the eigen-decomposition of the covariance matrix of the observations. Nevertheless, MUSIC algorithm is used for data described by the following model:

\[2.36\] ![images](images/img_6_69.jpg)

where A(*θ*) is an *m* × *n* Vandermonde matrix, x[*t*] is an *n*\-dimensional vector representing the amplitude of the observed signal y[*t*] and e[*t*] is a zero-mean *m*\-dimensional vector of white Gaussian noise. In this model, the unknown parameters are the *n* < *m* arrival angles present in *θ* and the problem is therefore: (1) to estimate the number of sources *n*, which is often supposed fixed, (2) to estimate the amplitudes of the signal: when the vector *θ* is estimated, then the amplitudes are estimated by using a maximum likelihood estimation (MLE) approach and (3) to estimate *θ* that uses the eigen-decomposition of the covariance matrix.

The covariance matrix of y is therefore:

\[2.37\] ![images](images/img_3_70.jpg)

where the superscript *H* is the transpose and conjugate operation, M[*x*] = IE(xx^(*H*)) is the *n* × *n* signal auto-correlation matrix and *σ*² is the noise variance. Assuming that *n* < *m* signals are present, then the *n* eigenvectors associated with the *n* largest eigenvalues define the signal subspace (the column space of A), and the *m* − *n* other eigenvalues define the noise subspace ![images](images/U.gif)[*v*]. As the signal subspace is orthogonal to the noise subspace, the strongest frequencies correspond to the peaks of the following function:

\[2.38\] ![images](images/img_6_70.jpg)

MUSIC algorithm assumes that the number of samples *m* and the number of sources are known and its efficiency is measured by the ratio between the smallest variance (given by the Cramér–Rao bound – CRLB) \[CRA 46\] and the variance of the MUSIC estimator, that is *eff* = *V ar[CRLB]/V ar[music]*.

# **2.7. Appendix 3: Large panel data**

In the asymptotic case where the number of observations *T* and the number of assets *N* are large, Bai and Ng \[BAI 02\] have developed an econometric theory to determine the number of latent factors. They consider that the data have an *r* factor representation:

\[2.39\] ![images](images/img_3_71.jpg)

where *X* is the *T* × *N* matrix of observed data, *F* is the *T* × *r* matrix of factors, Γ is the *N* × *r* matrix of factor loadings and *e* is the *T* × *N* matrix of idiosyncratic noise. It may be rewritten for each asset *i* = 1, …*, N* and each date *t* = 1, …*, T* as follows:

\[2.40\] ![images](images/img_6_71.jpg)

In this representation, it is supposed that the factors, their loadings and the idiosyncratic errors are not observable. Their approach differs from the theory developed for classical factor models, which does not apply when both *N* and *T* → ∞. Inference on *r* can be theoretically based on the eigenvalues of the covariance matrix estimate since within the *r* factor representation \[2.40\] the first *r* largest population eigenvalues diverge as *N* increases to infinity, but the (*r* + 1)*th* eigenvalue is bounded \[CHA 83\]. And it can be shown that all non-zero sample eigenvalues increase with *N*, a test based on the sample eigenvalues is thus not feasible. A likelihood ratio test can also be used to select the number of factors if the residual noise *e*[*T*] is assumed to be Gaussian distributed.

The authors estimate the common factors by the method of asymptotic principal components. The true number of factor *r* is unknown but fixed. They start with an arbitrary number *k* (*k* < min(*N, T*)) and then solve the following optimization problem:

[\[2.41\]](#c02.xhtml#eqn41_1) ![images](images/img_2_72.jpg)

where the superscript *k* indicates the current order of the model in the iterated process.

The optimization problem \[2.41\] is subject to the normalization of either ![images](images/Inline_73_6.jpg)Considering the latter one, then solving \[2.41\] is equivalent to maximizing tr(*F*^(*k*′) (*XX*′)*F* ^(*k*)). The estimated factor matrix denoted by ![images](images/Inline_73_7.jpg)is ![images](images/ch02_image003.gif)times the eigenvectors corresponding to the *k* largest eigenvalues of the *T* × *T* matrix *XX*′. Given ![images](images/Inline_73_8.jpg)then ![images](images/Inline_73_9.jpg)is the corresponding matrix of factor loadings.

## **2.7.1.** ***Large panel data criteria***

AIC, BIC and MDL are not consistent when both cross-sectional and time dimension increase. Bai and Ng \[BAI 02\] developed an asymptotic theory for the *approximate* factor models of Chamberlain and Rothschild \[CHA 83\] with large panel data. This results in consistent estimators (the so-called *IC*[*p*] and *PC*[*p*] estimators) that compute the number of eigenvalues larger than a threshold value, specified by a chosen penalty function. Onatski \[ONA 06\] modified these estimators by computing the threshold from the empirical distribution of the eigenvalues. In a similar context, Ahn and Horenstein \[AHN 09\] proposed the eigenvalue ratio (ER) and the growth ratio (GR) estimators, obtained simply by maximizing the ratio of two adjacent eigenvalues. Recent advances in the field of random matrix theory (RMT), which provides mathematical tools to characterize the empirical eigenvalue distribution for many symmetric matrices \[ELD 05\], can also be used in this context \[POT 05\].

### 2.7.1.1. **Panel* C[p] *(*PC[p] *and information criteria (*IC[p]*)) estimators \[BAI 02\]**

Let us first recall [equation \[2.41\]](#c02.xhtml#eqn41) that denotes the sum of squared residuals when *k* factors are estimated:

![images](images/img_4_73.jpg)

Estimating the number of factors is related to finding a penalty function *g*(*N,T*) such that criteria of the form:

\[2.42\] ![images](images/img_6_73.jpg)

can consistently estimate *K* with a bounded integer *K*[*max*] such that *K* < *K*[*max*]. In the same way, the authors show that the class of criteria defined by:

\[2.43\] ![images](images/img_9_73.jpg)

can also consistently estimate *K*. Various forms of *PC*[*p*] and *IC*[*p*] are then obtained from \[2.42\] and \[2.43\] and give:

[\[2.44\]](#c02.xhtml#eqn44_1) ![images](images/img_12_73.jpg)

\[2.45\] ![images](images/img_14_73.jpg)

\[2.46\] ![images](images/img_16_73.jpg)

\[2.47\] ![images](images/img_18_73.jpg)

\[2.48\] ![images](images/img_1_74.jpg)

[\[2.49\]](#c02.xhtml#eqn49_1) ![images](images/img_3_74.jpg)

where ![images](images/Inline_75_6.jpg)is set to be a consistent estimate of the variance of the residuals and ![images](images/Inline_75_7.jpg)The class of *PC*[*p*] criteria generalizes the *C*[*p*] criterion of Mallows \[MAL 73\] developed in a different context. Note also that the penalty functions *g*(*N, T*) in equations [\[2.44\]](#c02.xhtml#eqn44)–[\[2.49\]](#c02.xhtml#eqn49) depend on both *N* and *T*, which is not the case for the AIC and BIC. Moreover, these criteria show that the penalty functions satisfy the two following conditions, necessary to get consistent estimate of *K* : (1) *g*(*N, T*) → 0, and (2)![images](images/Inline_75_8.jpg)(see \[BAI 02\] for the details).

Let us also note that the classical AIC and BIC criteria can also be written as follows:

\[2.50\] ![images](images/img_10_74.jpg)

\[2.51\] ![images](images/img_12_74.jpg)

### 2.7.1.2. *Eigenvalue distribution test: random matrix theory*

Statistical theory usually presumes a constant number of dimensions or at least *T* /*N* → ∞. The quantity *q* = *T*/*N* can be interpreted as average sample size per dimension or as effective sample size. Unfortunately, large sample properties fail if *q* is small even if *T* is large. RMT is a branch of statistical physics that deals with this case of high-dimensional data. RMT is mainly concerned with the distribution of eigenvalues of randomly generated matrices. An important result is that under the hypothesis of independent and identically distributed matrix elements, the distribution of the eigenvalues converges to a specified law that does not depend on the distribution of the matrix elements but primarily on *q* = *T*/*N*.

Since the SCM \[2.21\] is a random matrix (see [equations \[2.26\]](#c02.xhtml#eqn26) and [\[2.30\]](#c02.xhtml#eqn30)), the results of RMT can be applied in the case of normally distributed data. In cases where the data are generalized elliptically distributed, the results of RMT are no longer applicable if we use the SCM, but may find some evidence by using the spectral estimator instead. Results on generalized elliptical distributions and the spectral estimator of the covariance matrix can be found in \[TYL 83\], \[TYL 87a\] and \[TYL 87b\] where it is shown that for such distributions the spectral estimator corresponds to an *M*\-estimator.

This section focuses on the basis of the RMT. The reader may refer to \[FRA 04\], \[POT 05\], \[HAR 07\] and \[BAI 10\] for a more complete and advanced description of the RMT.

Suppose that we use the SCM computed on the standardized matrix of returns ![images](images/R.gif)as described in [equation \[2.4\]](#c02.xhtml#eqn4). The resulting estimated covariance matrix S has therefore random elements with an assumed variance *σ*². Then, in the limit *T, N* → ∞, keeping the ratio *q* = *T* /*N* ≥ 1 constant, the density of the eigenvalues of S is given by:

\[2.52\] ![images](images/img_5_75.jpg)

where the maximum and the minimum eigenvalues are given by:

\[2.53\] ![images](images/img_8_75.jpg)

and (*x* − *a*)^([+]) = *max*(0, *x* − *a*). The density *ρ*(*λ*) is known as the Marčenko–Pastur density \[MAR 67, PAS 11\]. [Figure 2.6](#c02.xhtml#Fig6_1) shows the form of the Marčenko–Pastur density for different values of *q* = *T*/*N*.

**[Figure 2.6](#c02.xhtml#Fig6).** *Marčenko–Pastur densities for q* = 1, 2, 5

![images](images/img_3_76.jpg)

As is illustrated in [Figures 2.7](#c02.xhtml#Fig7_1)–[2.9](#c02.xhtml#Fig9_1) even for rather small matrices, the theoretical limiting density approximates the actual density very well. In these three figures, the ratio *q* = *T*/*N* is successively equal to 5, 2 and 1.

As mentioned in various studies, the Marčenko–Pastur density is a very good approximation of the density of eigenvalues of the correlation matrix of randomized vectors even though the density is fat-tailed. The question is therefore how to select the significant eigenvalues and then to determine the order of the model or the number of factors and to interpret the corresponding eigenvectors. The latter point is related to the observed data and it has been pointed out, for example, that the eigenvector corresponding to the largest eigenvalue is representative of the market factor as it covers the major part of the variance of the returns. The other eigenvectors may be compared with observed time series in the market as it was done in \[DAR 11\].

**[Figure 2.7.](#c02.xhtml#Fig7)** *Distribution of the eigenvalues of the SCM for q* = 5 *computed from i.i.i. random normal returns using (T* = 5,000*, N* = 1,000*) and (T* = 500*, N* = 100*). The corresponding Marčenko–Pastur density is superimposed*

![images](images/img_3_77.jpg)

In a more general setting, selection of the significant eigenvalues is done through a thresholding procedure: all eigenvalues above some number λ∗ are considered informative, otherwise eigenvalues relate to noise. To reconstruct a filtered covariance matrix estimate or to construct the corresponding eigenfactors, all noise-related eigenvalues may be replaced with a constant. This yields to renormalize the eigenvalues by the total sum. Then, the denoised covariance matrix estimate is obtained by the inverse procedure of its diagonalization.

Let us recall that each eigenvalue relates to the variance of a portfolio of assets. A very small eigenvalue means that there exists a portfolio of assets with very small out-of-sample variance, which is probably not realistic.

**Figure 2.8.** *Distribution of the eigenvalues of the SCM for q* = 2 *computed from i.i.i. random normal returns using (T* = 2,000*, N* = 1,000*) and (T* = 500*, N* = 250*). The corresponding Marčenko–Pastur density is superimposed*

![images](images/img_3_78.jpg)

**[Figure 2.9](#c02.xhtml#Fig9).** *Distribution of the eigenvalues of the SCM for q* = 1 *computed from i.i.i. random normal returns using (T* = 500*, N* = 500*) and (T* = 200, *N* = 200*). The corresponding Marčenko–Pastur density is superimposed*

![images](images/img_4_78.jpg)

# **2.8. Chapter 2 highlights**

#### ***Best factor models***

– The three-factor model of Fama and French \[FAM 93\] includes two additional factors to Sharpe’s market model: small minus big (SMB) market cap and high minus low (HML) book-to-market value. – The four-factor model of Carhart \[CAR 97\] is an extension of the Fama and French model including a momentum factor. – The Chen *et al*. model \[CHE 86\] is a model that includes several macro-economic factors that explain the returns of stocks in the US market. – The eight-factor model of Fung and Hsieh \[FUN 01\], designed to explain trend-followers’ hedge funds, includes eight risk-based factors: three specific portfolios invested in commodities, bonds and foreign exchange, two equity-oriented risk factors, two bond-oriented factors and an equity index of emerging stocks. 

#### ***Sample estimates***

Given the *T* × *N* matrix of observations R with mean *μ* and covariance matrix Σ, the consistent unbiased sample estimates for *μ* and Σ are, respectively, given by:

![images](images/img_9_79.jpg)

#### ***Wishart distribution***

The Wishart distribution ![images](images/w.gif)(*K*, A) is the distribution of ![images](images/Inline_80_12.jpg)where the z[*k*]s are independent, identically distributed (i.i.d.) according to a Gaussian distribution with zero-mean and covariance A.

#### *M**\-estimates***

![images](images/img_3_80.jpg)

#### ***Huber’s** M**\-estimator***

![images](images/img_5_80.jpg)

#### ***Fixed-point estimate***

![images](images/img_7_80.jpg)

#### ***Eigen-decomposition***

![images](images/img_9_80.jpg)

#### *K **eigenfactors***

![images](images/img_11_80.jpg)

#### ***Anderson’s sufficient statistic***

![images](images/img_13_80.jpg)

#### ***Akaike information criteria***

![images](images/img_2_81.jpg)

#### ***Minimum description length***

![images](images/img_4_81.jpg)

#### ***Eigenvalues follow the Marčenko–Pastur density***

When both *T, N* → ∞ and given *q* = *T*/*N* ≥ 1 constant, the density of the eigenvalues of S is given by the Marčenko–Pastur density:

![images](images/img_7_81.jpg)

where the maximum and the minimum eigenvalues are given by:

![images](images/img_9_81.jpg)

and (*x* − *a*)^+ = *max*(0, *x* −*a*).

[¹](#c02.xhtml#fnt1_1) See [http://www.morningstar.com](http://www.morningstar.com)

# Chapter 3

# Least Squares Estimation (LSE) and Kalman Filtering (KF) for Factor Modeling: *A Geometrical Perspective*

# **3.1. Introduction**

Following a geometrical approach, this chapter introduces, illustrates and derives both least squares estimation (LSE) and Kalman filter (KF) estimation of the alpha and betas of a return, for a given number of factors that have already been selected. An emphasis is put on commonalities and discrepancies between least squares (LS) and KF. In particular, both techniques use as the “measurement” equation or regression the “per return” factor model that linearly links the inputs (return and factors) with the unknown parameters (alpha and betas). In a common geometrical framework, both LS and KF optimization criteria aim at minimizing the square Euclidian norm of an error-vector. While KF provides genuine recursive estimates of the alpha and betas, the LS technique cannot, since it processes the inputs in a block fashion, over a certain sliding observation window. Moreover, the window has to be long enough to ensure some numerical stability. LSE thus exhibits limited tracking capabilities. Tracking abilities of the KF are induced by an underlying recursive model (called the state equation) of the alpha and betas that is not part of LSE setup.

This chapter is organized as follows. Section 3.2 formalizes the “per return factor model” and the concept of recursive estimate of the alpha and betas. Sections 3.3–3.7 are dedicated to LSE while the contents of sections 3.8–3.12 deal with KF. A summary of the most important outcomes of the chapter is contained in section 3.15. Numerous simulation results are displayed and commented throughout of the chapter to illustrate the behaviors, performance and limitations of LSE and KF.

# **3.2. Why LSE and KF in factor modeling?**

## **3.2.1.** ***Factor model per return***

For a single asset *i*, the model of return *r*[*i,t*] at time *t* based on the *K* factors *f[t,k]*, 1 ≤ *k* ≤ *K* takes the following form \[JAY 11a\], ∀1 ≤ *i* ≤ *N*:

[\[3.1\]](#c03.xhtml#eqn_1) ![image](images/img_6_83.jpg)

NOTE 3.1.– The assumptions inherent to the model \[3.1\] are the same as the assumptions introduced in Chapter 1. In particular, ![images](images/e.gif)[*i,t*] are zero-mean random processes with IE![image](images/Inline_84_9.jpg).

In this chapter, for the sake of simplicity, the reference to a specific asset will be implicit and the index *i* is thus dropped. Accordingly, we introduce *θ*[*t*] the unknown *K* + 1-dimensional “parameter-vector” at time *t*, which collects *α* and the *K* betas (per return), such that:

\[3.2\] ![image](images/img_2_84.jpg)

If we aggregate the *K* factors *f[t,k]*, 1 ≤ *k* ≤ *K* in the (*K* + 1)-sized vector g′[*t*] = \[1 *f[t,]*[1] *f[t,]*[2] … *f[t,K]* \], with its first component equal to one, then [equation \[3.1\]](#c03.xhtml#eqn1) can be rewritten in a more compact form called hereafter the *per return factor model* or the observation/measurement equation:

[\[3.3\]](#c03.xhtml#eqn_3) ![image](images/img_5_84.jpg)

The (per asset) return *r*[*t*] that is also referred to, in a more generic way, as the observation, or the measurement, or the response, is the first input of model \[3.3\]. The “factors” *g[t,k]*, 0 ≤ *k* ≤ *K* (with *g*[*t*,0] = 1, *g[t,k]* = *f[t,k]* for *k* ≠ 0), commonly designated as the regressors in the framework of linear regression, are the other inputs to the per asset factor model.

## **3.2.2.** ***Alpha and beta estimation per return***

In this chapter, it is assumed that the *K* factors *f[t,k]*, 1 ≤ *k* ≤ *K* have already been selected. LSE and KF are two different methods, among many others, that allow the estimation of *θ*[*t*] for a given set of factors. Such an estimate is denoted ![image](images/Qcap.gif)*t*.

LSE and KF exhibit two major commonalities that are leveraged throughout the chapter. First, they share the same observation [equation \[3.3\]](#c03.xhtml#eqn3). Second, their optimization criteria and subsequent solutions can be interpreted geometrically in similar ways, involving the square of specific Euclidian or “second order” distances. For both of them, the geometrical light eases the understanding of how the methods are working, how they perform and how the optimum solutions are derived.

One fundamental discrepancy differentiates LSE and KF. Thanks to “instantaneous and recursive processing” of the inputs mentioned above, KF provides a recursive estimate ![image](images/Inline_86_2.jpg)that can be naturally expressed as a function of ![image](images/Inline_86_3.jpg)Contrary to KF, LSE has limited “tracking capabilities” (*of dynamic investment styles like in hedge funds, for instance*), since it is based on “block processing” and does not yield any recursive estimate. As opposed to instantaneous processing, block processing requires the access to several (and not only one) measurements and factors values to come up with an estimate.

These points are detailed in sections 3.3–3.7 for block processing-based LSE and in sections 3.8–3.12 for recursive and instantaneous processing-based KF.

# **3.3. LSE setup**

## **3.3.1.** ***Current observation window and block processing***

Operating LSE method requires us to define the “current observation” window that limits the time index of the inputs involved in the block processing needed to compute the current parameter LSE. The current observation window is denoted (*t, h*), where *t* represents the current time instant (*i.e. actually chosen as the end of the window*) and *h* the number of time instants comprised in this window. We have (*t, h*) = {*l,* such that: *t* − *h* + 1 ≤ *l* ≤ *t*}. We also call *h* the window length.

## 3.3.2. *LSE regression*

Since LSE leverages block processing of the responses *r*[*l*] and the regressors ![image](images/glcap.gif)for *l* ∈ (*t, h*), LSE implicitly assumes that the parameter-vector of alpha and betas holds a certain value denoted *θ*[(*t,h*)] across the observation window (*t, h*). This allows the generation of the measurements *r[l]* for *l* ∈ (*t, h*), according to the so-called “LSE regression”, derived from [equation \[3.3\]](#c03.xhtml#eqn3):

\[3.4\] ![image](images/img_2_86.jpg)

LSE regression \[3.4\] can be rewritten in a “block” fashion, as it is more appropriate to define the LSE objective criterion and derive its solution:

[\[3.5\]](#c03.xhtml#eqn_5) ![image](images/img_5_86.jpg)

In [equation \[3.5\]](#c03.xhtml#eqn5), we have ![image](images/Inline_87_8.jpg)![image](images/Inline_87_9.jpg)and ![image](images/Inline_87_10.jpg)The LSE “block regression” aggregates *h* instances of the return process *r*[*l*] .

ASSUMPTION 3.1.– The window length *h* is assumed to be much larger than the number *K* + 1 of unknown quantities, that is *h* ![images](images/great.gif)*K* + 1 and the \[*h, K* + 1\] matrix G[(*t,h*)] is assumed to be full rank (*equal to* *K* + 1).

# 3.4. LSE objective and criterion

The LSE ![image](images/Inline_87_14.jpg)achieves the minimum of the squared Euclidian norm ||.||[*l2*] of the difference r[(*t,h*)] = G[(*t,h*)] *ξ* among all the possible real-valued (*K* + 1)-dimensional vectors *ξ*:

[\[3.6\]](#c03.xhtml#eqn_6) ![image](images/img_15_86.jpg)

The term G[(*t,h*)] *ξ* can be viewed as an estimate![image](images/Inline_87_18.jpg)of the response-vector r[(*t,h*)] built across the current observation window (*t, h*). As such, if we denote![image](images/Inline_87_19.jpg)1 ≤ *k* ≤ *K* + 1, the *K* + 1 column-vectors (*also called column-factors*) of the matrix G[(*t,h*)], the term G[(*t,h*)] *ξ* can be rewritten as a linear combination of the![image](images/Inline_88_2.jpg)that is:

\[3.7\] ![image](images/img_3_87.jpg)

Consequently and as defined in \[3.6\], the LSE ![image](images/Inline_88_9.jpg)helps us to build the linear combination of the column-regressors ![image](images/Inline_88_7.jpg)(factors) that best fits the measurements (*returns*) r[(*t,h*)] in a geometrical and Euclidian sense. The geometrical interpretation of the solution is detailed in section 3.6.2. It is important to note that the LSE optimality criterion does not put any constraint on the solution ![image](images/Inline_88_8.jpg)In particular, the magnitude of![image](images/Inline_88_9.jpg)is not prevented from becoming very large which could lead to unreliable responses estimate![image](images/Inline_88_10.jpg). In such a situation, LSE has to be regularized or constrained (see Chapter 4).

# 3.5. How LSE is working (for LSE users and programmers)

If G[(*t,h*)] is full rank, then the \[*K* + 1*, K* + 1\] matrix ![image](images/Inline_88_13.jpg)is invertible and the LSE ![image](images/Inline_88_14.jpg)requires the following block processing over the observation window (*t, h*) (see section 3.6 for the derivation):

[\[3.8\]](#c03.xhtml#eqn_8) ![image](images/img_15_87.jpg)

According to the explicit form of ![image](images/Inline_88_18.jpg)given in \[3.8\], it is clear that the tracking capabilities of the LSE are burdensome, if not limited. As a matter of fact, the computation of ![image](images/Inline_88_19.jpg)based on the next observation window (*t* + 1*, h*) requires going through the full block processing, that is the calculation of both ![image](images/Inline_88_20.jpg)These two latter entities do not exhibit any recursivity property that would allow the derivation of ![image](images/Inline_89_2.jpg)as a mere function of the current LSE ![image](images/Inline_89_3.jpg)This is actually a major limitation of the LSE.

# 3.6. Interpretation of the LSE solution

## *3.6.1.* *Bias and variance*

Substituting the LSE regression \[3.5\] into the LSE solution \[3.8\] reveals the relationship between the estimate ![image](images/Inline_88_9.jpg)and the unknown *θ*[(*t,h*)]:

[\[3.9\]](#c03.xhtml#eqn_9) ![image](images/img_8_88.jpg)

[Equation \[3.9\]](#c03.xhtml#eqn9) turns out to be the keystone of the LSE performance evaluation both in terms of bias and variance. Indeed, in keeping with \[3.9\], the bias *B*(![image](images/Inline_88_9.jpg)) of the LSE ![image](images/Inline_88_9.jpg)defined as the difference ![image](images/Inline_89_13.jpg)is equal to zero, because the observation noise vector *∈*[(*t,h*)] is zero-mean. This means that, on average, the LSE coincides with the true parameter. But the bias reflects only the first-order moment of ![image](images/Inline_89_14.jpg)and subsequently displays a narrowed view of the LSE quality.

The LSE reliability also requires gauging the magnitude of its fluctuations around the true value. If ![image](images/Inline_89_16.jpg)can fluctuate a lot around *θ*[(*t,h*)], then there is a substantial probability that the LSE value ![image](images/Inline_89_17.jpg)falls far from *θ*[(*t,h*)] which makes the LSE highly unreliable, even if it is unbiased. The covariance matrix S[(*t,h*)] of the innovation vector, ![image](images/Inline_89_18.jpg)helps to quantify these fluctuations. Thanks to \[3.9\] and the whiteness of the observation noise *∈*[(*t,h*)], with a covariance matrix equal to ![image](images/Inline_89_19.jpg)we have:

\[3.10\] ![image](images/img_20_88.jpg)

If the parameter *θ*[(*t,h*)] was scalar (one dimensional), the matrix S[(*t,h*)] would coincide with the dispersion metrics itself, that is the variance. Hereafter, we define the dispersion index of the LSE ![image](images/Inline_88_9.jpg)around its average *θ*[(*t,h*)] as the trace of S[(*t,h*)]. It is emphasized that this trace is always positive because S[(*t,h*)] is a positive definite matrix. Denoting {*λ*^(*i*)[(*t,h*)]}1[≤[*i*]≤]*K*[+1] the *K* + 1 (positive) eigenvalues of the matrix (G′ G)[(*t,h*)] and noting that the trace is also equal to the summation of the eigenvalues we get:

\[3.11\] ![image](images/img_2_89.jpg)

To obtain \[3.11\], the fact that the eigenvalues of the inverse of a matrix are equal to the inverse of the eigenvalues can be used. Identity \[3.9\] casts light on when the worst case of large dispersion around the true value is met. It is indeed straightforward to conclude from \[3.9\] that *tr*\[S[(*t,h*)]\] is lower bounded as follows:

\[3.12\] ![image](images/img_5_89.jpg)

We see from \[3.12\] that the LSE may exhibit a large dispersion around the true parameter if the minimum eigenvalue ![image](images/Inline_90_8.jpg)of (G′ G)[(*t,h*)] is small w.r.t. the observation noise variance ![image](images/Inline_90_9.jpg)This may happen when the matrix (G′ G)[(*t,h*)] is ill-conditioned ![image](images/Inline_90_10.jpg), although invertible.

## 3.6.2. *Geometrical interpretation of LSE*

As noted in section 3.4, the term ![image](images/Inline_90_13.jpg)might be viewed as the LSE ![image](images/Inline_90_14.jpg)of the return or measurement vector r[(*t,h*)]. In keeping with the interpretation of section 3.4, ![image](images/Inline_90_15.jpg)represents the linear combination of the column-regressors ![image](images/Inline_91_2.jpg)(column-factors) that best fits the measurements (returns) r[(*t,h*)] in a geometrical and Euclidian sense. Taking into account [equation \[3.8\]](#c03.xhtml#eqn8), we have:

[\[3.13\]](#c03.xhtml#eqn_13) ![image](images/img_3_90.jpg)

where

\[3.14\] ![image](images/img_6_90.jpg)

The matrix ∏[⊥],G(*[t,h]*[)] is actually the orthogonal projection matrix in the space spanned by the *K* + 1 column-regressors ![image](images/Inline_91_9.jpg)(column-factors). Indeed, it is easy to check that the operator ![image](images/Inline_91_10.jpg)maps G[(*t,h*)] to itself, that is ![image](images/Inline_91_11.jpg)This operator also satisfies a characteristic property of projectors, that is ![image](images/Inline_91_12.jpg)This helps us to understand that, according to \[3.13\], the projector nature of ![image](images/Inline_91_13.jpg)is nothing but the orthogonal projection of the return-vector r[(*t,h*)] onto the space of the column-factors ![image](images/Inline_91_14.jpg)To some extent, this feature turns out to be expected: LSE ![image](images/Inline_88_9.jpg)builds the best geometrical and Euclidian approximation of r[(*t,h*)] that is achieved by making its orthogonal projection in the “approximation” space, or column-factor space for the time window (*t, h*). This space, denoted hereafter *col*{G[(*t,h*)]}, is spanned by the columns of the matrix G[(*t,h*)]. [Figure 3.1](#c03.xhtml#Fig1) illustrates geometrically how ![image](images/Inline_91_15.jpg)is obtained from r[(*t,h*)].

[Figure 3.1](#c03.xhtml#Fig1) also illustrates the so-called LSE orthogonality principle. Indeed, the residual ![image](images/Inline_91_17.jpg)of the orthogonal projection of ![image](images/Inline_91_18.jpg)denoted ![image](images/Inline_91_19.jpg)and also called the return-vector innovation, is geometrically orthogonal to the column-factor space. We symbolically write this orthogonality principle as follows: ![image](images/Inline_92_2.jpg)This makes a lot of sense, as the innovation represents the part of the return that cannot be explained by the factors and has thus to be orthogonal to them, according to some particular “geometry”. The LSE is actually based on Euclidian geometry and it is easy to prove that the Euclidian product ![image](images/Inline_92_3.jpg)is a null vector. We first derive from \[3.13\] and the definition of the return innovation of the following identities:

\[3.15\] ![image](images/img_4_91.jpg)

with,

[\[3.16\]](#c03.xhtml#eqn_16) ![image](images/img_7_91.jpg)

[**Figure 3.1**](#c03.xhtml#Fig_1). *Geometrical and Euclidian interpretation of the least square estimate (LSE)*![image](images/Inline_92_10.jpg)*and the LSE orthogonality principle*

![image](images/img_11_91.jpg)

By construction, the operator ![image](images/Inline_92_13.jpg)involved in \[3.16\] happens to be the orthogonal projection matrix into the space orthogonal to the space spanned by the column-vectors of G[(*t,h*)]. [Equations \[3.13\]](#c03.xhtml#eqn13)–[\[3.16\]](#c03.xhtml#eqn16) combined with the following projection property ![image](images/Inline_93_2.jpg)lead to the identity chain that completes the proof:

\[3.17\] ![image](images/img_3_92.jpg)

The LSE orthogonality principle allows us to write an orthogonal decomposition of the return-vector r[(*t,h*)] such that, ![image](images/Inline_93_6.jpg)with ![image](images/Inline_93_7.jpg)and ![image](images/Inline_93_8.jpg)Pythagorean theorem subsequently yields the relationship \[3.18\]:

\[3.18\] ![image](images/img_9_92.jpg)

It is then straightforward to evaluate the minimum value of the LSE cost function, that is ![image](images/Inline_93_12.jpg)First, because of the return vector-innovation ![image](images/Inline_91_19.jpg)definition we note that the minimum value of the LSE cost function coincides with the square Euclidian norm of the return-vector innovation ![image](images/Inline_93_13.jpg)see also [Figure 3.1](#c03.xhtml#Fig1). Second, we derive from \[3.18\] that:

\[3.19\] ![image](images/img_14_92.jpg)

Finally, the definition of the Euclidian norm combined with [equations \[3.13\]](#c03.xhtml#eqn13) and [\[3.16\]](#c03.xhtml#eqn16) enable us to involve the projector ![image](images/Inline_93_17.jpg)in the following manner:

\[3.20\] ![image](images/img_18_92.jpg)

We note from \[3.20\] that, for a given set of returns r[(*t,h*)] and factor values G[(*t,h*)] that occur across the observation window (*t, h*), the LSE accuracy increases when the “positive” quadratic form ![image](images/Inline_93_21.jpg)decreases. This happens when the “angle” between r[(*t,h*)] and the approximation space *col*{G[(*t,h*)]} is obviously small, meaning that the returns and the factors share a lot of commonalities. This conclusion was obviously an upfront common sense expectation.

# 3.7. Derivations of LSE solution

In keeping with the problem statement given in [equation \[3.6\]](#c03.xhtml#eqn6), the LSE cost function ![image](images/Inline_94_4.jpg)to be minimized w.r.t. the *K* + 1 dimensional real-valued vector *ξ* is the square Euclidian norm of the difference ![image](images/Inline_94_5.jpg)We thus have:

\[3.21\] ![image](images/img_6_93.jpg)

Ω[(*t,h*)](*ξ*) is a convex function with a unique minimum under the assumption that the positive definite matrix G′[(*t,h*)] G[(*t,h*)] is full rank (has no vanishing eigenvalues). The vector *ξ*^(*op*) that achieves the minimum of Ω[(*t,h*)](*ξ*) is thus the solution of the following equation:

\[3.22\] ![image](images/img_9_93.jpg)

where ∇[ξ](*.*) designates the gradient vector-operator, that is ![image](images/Inline_94_12.jpg)Straightforward calculation leads to:

[\[3.23\]](#c03.xhtml#eqn_23) ![image](images/img_13_93.jpg)

[Equating \[3.23\]](#c03.xhtml#eqn23) to zero gives finally the optimum solution \[3.8\]. It is interesting to grasp the behavior of the LSE cost function close to the optimum. A second-order Taylor expansion (the first-order term is zero because of the optimality condition \[3.22\]) gives:

\[3.24\] ![image](images/img_2_94.jpg)

In \[3.24\],![image](images/Inline_95_5.jpg)denotes the \[*K* + 1*, K* + 1\] Hessian matrix, that is ![image](images/Inline_95_6.jpg)We obtain from \[3.22\] that ![image](images/Inline_95_7.jpg)\= 2 (G′G)[(*t,h*)]. Substitution into \[3.24\] leads to:

\[3.25\] ![image](images/img_8_94.jpg)

Since ![image](images/Inline_95_11.jpg)is positive definite and full rank if *ξ* ≠ *ξ*^(*op*), then ![image](images/Inline_95_12.jpg)close to the optimum. This confirms the convexity curvature of the cost function.

# 3.8. Why KF and which setup?

## 3.8.1. *LSE method does not provide a recursive estimate*

Coarsely (details will follow in section 3.10), both LSE and KF leverage measurements *r*[*t*] that are connected to an unknown parameter *θ*[*t*], see \[3.27\], to find its best estimate ![image](images/Qcap.gif)[*t*] based on a minimum squared distance criterion. Limited to the scope of the factor model problem, *r*[*t*] is the scalar return of any asset and *θ*[*t*] is the (*K* + 1)-dimensional column vector collecting the alpha and exposures (betas) of the asset (for the sake of simplicity the subscript referring to the asset has been dropped). The two other components of \[3.27\] have the same meaning as in the previous sections. One issue with LSE arises from the absence of recursivity of the estimate ![image](images/Qcap.gif)[*t*]. By recursivity, we mean the explicit updating of the new estimate ![image](images/Inline_96_2.jpg)from the previous estimate ![image](images/Inline_96_3.jpg)Operating the LSE across a sliding window (*t, h*), as described in section 3.3.2, opens a path that allows an update on the fly of the estimate but is not a recursive estimator *per se*.

Recursivity of the estimate bears virtues. The most important advantage is the tracking capability of both the estimate and its accuracy. If the main drivers of the measuring process and the evolution of the true parameter have not significantly changed from time *t* − 1 to time *t*, then the new estimate should closely replicate the previous estimate, saving a lot of processing burden. In addition, if the new value of the true parameter and/or the new measurements depart significantly from the previous situation, then the updated estimate should reflect the change instantaneously. Real-time tracking and thus recursivity is essential in aeronautics, automatic surveillance and monitoring, car and train control, speech and image (multimedia) processing \[FUK 90, BAR 93, KAY 93, DUV 94, KAY 98\], intensive care medicine, econometrics and quantitative finance, etc.

The measurement ([equation \[3.27\]](#c03.xhtml#eqn27)), yields no recursivity of the parameter. Therefore, to build a recursive estimate, KF needs to rely on a recursive equation that drives the true parameter evolution and, moreover, that equation has to be known ahead to be included in the estimate derivation. Recursivity of the estimate will be induced by the recursivity of the true unknown parameter. This is the key difference between LSE and KF setups.

## 3.8.2. *The state space model and its recursive component*

This recursive equation, also called the state equation, is a discrete time version of a differential equation. It can be “natural” or “intuitive”. If natural, it comes from the well-known laws of physics (mechanics, thermodynamics, electromagnetism, optics, etc.) and chemistry that describe phenomena along with their key variables by differential equations. We invite the reader to check the many examples provided in \[BAR 93, KAY 93, KAY 98, NOR 04\]. If no particular law can be leveraged, it is still possible to postulate an “intuitive behavioral description” of the parameter evolution that is a key stone of KF.

*KF state-space model/set up*

Evolution of the parameters *θ*[*t*], state recursive equation:

[\[3.26\]](#c03.xhtml#eqn_26) ![image](images/img_4_96.jpg)

Measurement–observation equation:

[\[3.27\]](#c03.xhtml#eqn_27) ![image](images/img_7_96.jpg)

No particular law of economics or finance yields a recursive equation of the alphas and exposures of any given asset. An intuitive evolution model has thus to be introduced. The simplest model leads to the fewest number of extra-parameters to be tuned and exhibits the easiest rationale to understand. The simplest and most parsimonious recursive model is given by [equation \[3.26\]](#c03.xhtml#eqn26). It assumes that the new “state” of the parameter at time *t* is equal to the previous “state” at time *t* − 1 plus another component, the state noise w[*t*], that is statistically orthogonal (uncorrelated) to the previous state. This means that, to describe the new state, we have to fully innovate w.r.t. the statistical information contained in the previous state.

## 3.8.3. *Parsimony and orthogonality assumptions*

Orthogonality (see also section 3.9) and parsimony are easy to achieve if we choose a zero-mean, Gaussian and white state noise with uncorrelated components, that is IE ![image](images/Inline_98_2.jpg)with *δ*\[0\] = 1 and *δ*\[*k*\] = 0, *k* ≠ 0, otherwise.

Consequently, the state equation depends only on one scalar parameter, that is ![image](images/Inline_98_4.jpg)because the Gaussian probability density function depends only on the first- and second-order moments (see Appendix A1.1). The other KF model assumptions are summarized below. In keeping with the parsimony feature, both the observation noise and the initial state are also assumed Gaussian and white.

*Summary of KF model assumptions*

![image](images/img_6_97.jpg)

# 3.9. What are the main properties of the KF model?

## 3.9.1. *Self-aggregation feature*

The two key properties of the KF model formalize the main features of recursivity, parsimony and orthogonality mentioned in section 3.8. They are both based on the explicit writing of the parameter *θ*[*t*] as a function of the state noise w[*t*] and the initial value *θ*[0]. It is straightforward to derive from \[3.26\] the following relationship:

[\[3.28\]](#c03.xhtml#eqn_28) ![image](images/img_10_97.jpg)

[Equation \[3.28\]](#c03.xhtml#eqn28) means, for instance, that the sole value of *θ*[*t*−1] self-aggregates the knowledge of the whole series {*θ*[0], *θ*[1], …, *θ*[*t*−1]}.

## 3.9.2. *Markovian property*

The self-aggregation feature is leveraged in the so-called “Markovian” property described in [equation \[3.29\]](#c03.xhtml#eqn29) and states that the Probability Density Function (PDF) of *θ*[*t*] conditional to its whole past is the same as its PDF conditional to its most recent value *θ*[*t*−1]. The Markovian property expresses the recursivity feature at the probability density level of the parameter.

[\[3.29\]](#c03.xhtml#eqn_29) ![image](images/img_4_98.jpg)

[Equation \[3.29\]](#c03.xhtml#eqn29) can also be interpreted in terms of parsimony, because we need to propagate *θ*[*t*−1] only to sample the next value.

## 3.9.3. *Innovation property*

As w[*t*] is white, it is statistically orthogonal to all the previous state noise samples {w[1], …, w[*t*−1], }. By “statistically orthogonal”, we mean uncorrelated, that is IE\[w[*t*] w′[*n*]\] = 0, *t* ≠ *n*, where 0 designates the zero matrix. In what follows, the symbol ![images](images/parallel.gif)will stand for “statistical orthogonality”.

Moreover, the KF setup assumptions make w[*t*] orthogonal to *θ*[0]. Consequently, because of [equation \[3.28\]](#c03.xhtml#eqn28), w[*t*] is orthogonal to the previous state *θ*[*t*−1]:

[\[3.30\]](#c03.xhtml#eqn_30) ![image](images/img_10_98.jpg)

[Equation \[3.30\]](#c03.xhtml#eqn30) stands for the “innovation” (orthogonal) property: each update of the state noise brings pure innovation to the parameter evolution. As detailed in sections 3.11 and 3.12, both the Markovian and innovation properties drive the architecture of the KF.

# 3.10. What is the objective of KF?

Given the measurements up to time *t*, {*r*[*k*], 1 ≤ *k* ≤ *t*} AND the state-space setup (model) described by [equations \[3.26\]](#c03.xhtml#eqn26) and [\[3.27\]](#c03.xhtml#eqn27), KF aims at deriving a *recursive and linear* (regarding linearity, see the second and third notes hereafter) estimate ![image](images/Inline_100_4.jpg)of the unobservable state or parameter *θ*[*t*], *t* ≥ 1 based on the minimization of the mean square error (MSE). The second subscript *q* of ![image](images/Inline_100_5.jpg)stands for the end of the time window of the observation space ![image](images/Inline_100_6.jpg)used to estimate *θ*[*t*], *t* ≥ 1. If the problem is limited to KF, then *q* = *t*. For Kalman prediction and smoothing, not addressed in this book, we would have *q* < *t* and *q* > *t* respectively.

KF objectives:

\[3.31\] ![image](images/img_8_99.jpg)

Based on minimum mean square error (MMSE) optimality criterion:

[\[3.32\]](#c03.xhtml#eqn_32) ![image](images/img_11_99.jpg)

In [equation \[3.32\]](#c03.xhtml#eqn32), ![image](images/Inline_100_14.jpg)designates any element of the observation space ![image](images/Rt1.jpg)spanned by the random variables {*r*[1], …*, r*[*t*]}, see section 3.14 for the geometrical and Euclidian interpretation of MMSE criterion.

NOTE 3.2.– The recursivity of the estimate is naturally induced by the recursivity of the state [equation \[3.26\]](#c03.xhtml#eqn26) and the consecutive Markovian property \[3.29\].

NOTE 3.3.– For the sake of simplicity and for the benefit of newcomers, we have positioned the objectives of KF as a recursive MMSE estimate, limiting thus the optimality search to an intuitive “distance-like” or geometrical-like second-order criterion (see section 3.14). The geometrical path skips the probabilistic or Bayesian presentation, based on conditional probability densities. Probabilistic derivation requires a lengthy introduction of maximum *a posteriori* methods and detailed properties of normal conditional PDFs, at the expense of the intuitive and quick understanding of KF structure, behavior and performance.

NOTE 3.4.– In the probabilistic (Bayesian) approach and under Gaussian assumptions, linearity of the estimate w.r.t. both the measurements and the previous estimate is a consequence of the optimization process. The MMSE-based presentation undertaken in this chapter needs to specify the structure of the estimate. It is limited hereafter to linear operators in order to lead exactly to the same solution as the probabilistic derivation.

# 3.11. How does the KF work (for users and programmers)?

## 3.11.1. *Algorithm summary*

Resolution of the problem stated in section 3.10 is detailed in section 3.14. Hereafter, we describe and interpret the recursive structure of the KF solution that should be well understood by both KF users and programmers. One *full recursive KF step* from time *t* − 1 to time *t*, with *t* ≤ 1, is twofold. Indeed, as displayed in [Figure 3.2](#c03.xhtml#Fig2), the KF full step updates, on the one hand, the (alphas and betas), from ![image](images/Inline_101_7.jpg)to ![image](images/Inline_102_2.jpg)and, on the other hand, the associated KF “accuracy” matrix, from ![image](images/Inline_102_3.jpg)is called the *KF*(*n*/*q*) innovation,![image](images/Inline_102_4.jpg)The accuracy matrix is nothing but the covariance matrix of the current KF innovation. The decrease of its dynamic range tracks the accuracy improvement and thus the convergence of the KF estimate closer to the targeted parameter *θ*[*t*] .

1) Initialization *t* = 0 

KF is initialized in the following manner:

[\[3.33\]](#c03.xhtml#eqn_33) ![image](images/img_7_101.jpg)

From time *t* − 1 to time *t*, with *t* ≤ 1: full KF recursive processing breaks into (1) prediction (also called *a priori* update) and (2) correction (also called *a posteriori* update), see [Figure 3.2](#c03.xhtml#Fig2).

2) Prediction, from (*t* − 1|*t* − 1) to (*t*|*t* − 1).

Prediction is the sole genuine recursive step of KF induced by the recursive (Markovian) state equation of the model (see [Figure 3.2](#c03.xhtml#Fig2)). The prediction step relies only on the confidence in the recursive state-space KF model given by [equation \[3.26\]](#c03.xhtml#eqn26). Prediction updates are split into prediction filtering that computes the new state estimate ![image](images/Inline_102_12.jpg)from the previous state estimate ![image](images/Inline_102_13.jpg)see \[3.34\], and prediction accuracy processing, see \[3.35\], that refreshes of the accuracy matrix.

Prediction filtering

[\[3.34\]](#c03.xhtml#eqn_34) ![image](images/img_15_101.jpg)

Prediction accuracy processing

[\[3.35\]](#c03.xhtml#eqn_35) ![image](images/img_18_101.jpg)

3) Correction, from (*t*|*t* − 1) to (*t*|*t*).

Correction is triggered by the capture of the updated measurement *r*[*t*] (see [Figure 3.2](#c03.xhtml#Fig2)). After the calculation of the so-called Kalman gain, see \[3.36\], the correction filtering sub-step computes ![image](images/Inline_103_2.jpg)see \[3.37\]. The correction accuracy processing evaluates S[*t|t*], see \[3.38\].

Correction filtering *t* ≥ 1

Kalman gain

[\[3.36\]](#c03.xhtml#eqn_36) ![image](images/img_5_102.jpg)

Correction update

[\[3.37\]](#c03.xhtml#eqn_37) ![image](images/img_8_102.jpg)

Correction accuracy processing

[\[3.38\]](#c03.xhtml#eqn_38) ![image](images/img_11_102.jpg)

[Figure 3.2](#c03.xhtml#Fig_2). *Inputs/outputs schematic of Kalman filtering prediction and correction steps*

![image](images/img_14_102.jpg)

As displayed in [equation \[3.37\]](#c03.xhtml#eqn37), the “Kalman gain” z[*t*] defined by \[3.36\] helps us to balance, on the one hand, the weight of the recursive model reflected in ![image](images/Inline_103_16.jpg)and, on the other hand, the weight of the measurement current value and the observation [equation \[3.27\]](#c03.xhtml#eqn27).

[Figure 3.2](#c03.xhtml#Fig2) displays the schematic of the full KF recursive step that is split into prediction and correction processing, as per [equations \[3.34\]](#c03.xhtml#eqn34)–[\[3.38\]](#c03.xhtml#eqn38). The KF schematic emphasizes the key roles of the state recursive [equation \[3.26\]](#c03.xhtml#eqn26) and the observation \[3.27\] model in each of the two steps.

## 3.11.2. *Initialization of the KF recursive equations*

Similar to several algorithms where initial values have to be chosen, there is a trade-off to make between the estimation accuracy and the convergence speed of the algorithm. Depending of the initial values, recursive algorithms will converge more or less quickly toward the true values. There is no universal rule, only some “good sense rules”.

As stated in [equation \[3.33\]](#c03.xhtml#eqn33), the parameters of the space-state model have to be initialized. The initial values of the vector ![image](images/Inline_104_5.jpg)have to be set regarding the knowledge of the problem and what represents this vector. In the case of factor model, *θ* accounts for the exposures of the portfolio to some market factors, so that their values are mostly comprised between −1 and +1. Initializing ![image](images/Inline_104_6.jpg)with zeros is therefore very plausible.

The initial value of the variance of the estimation error is also linked to *θ* and should not be too small: if so, then the Kalman gain will also be quite small, and regarding [equation \[3.37\]](#c03.xhtml#eqn37), the correction value of ![image](images/Inline_104_8.jpg)will remain close to the prediction value ![image](images/Inline_104_9.jpg)Then, if the true values of *θ* are not close to the initial value, the algorithm will never reach these true values as it will always propose some values close to the initial values.

In addition, if ![image](images/Inline_104_11.jpg)is initialized to a value which is too large, then the algorithm will converge slower toward the true value than if ![image](images/Inline_104_12.jpg)were set to a more convenient value.

In our case, we may set ![image](images/Inline_105_2.jpg)to 1 or 1*.*5 as from 0 we wish to reach the lowest and the highest bound (−1 and +1) of the range of potential values.

The two other parameters ![image](images/Inline_105_4.jpg)and ![image](images/Inline_105_5.jpg)of the space-state model are supposed to be known. The variance ![image](images/Inline_105_6.jpg)of the observation equation represents the magnitude of the error made on the model so that it may be set as a fraction of the variance of the observed returns. The variance ![image](images/Inline_105_7.jpg)impacts the prediction accuracy processing \[3.35\] and has also to be set in concordance with the amplitude and assumed variability of the state variable.

# 3.12. Interpretation of the KF updates

All the prediction and correction updating equations will be derived in section 3.14 based on a simple “geometric and Euclidian approach”. Hereafter, we give intuitive interpretations of each of them. These qualitative rationales turn out to be very useful when programming and/or using KF, especially to monitor the performance and tune the KF inputs.

## 3.12.1. *Prediction filtering, [equation \[3.34\]](#c03.xhtml#eqn34)*

[Equation \[3.34\]](#c03.xhtml#eqn34) predicts the estimate ![image](images/Inline_105_14.jpg)based on ![image](images/Inline_105_13.jpg)According to the notations introduceection 3.10, both estimates ![image](images/Inline_105_14.jpg)and ![image](images/Inline_105_15.jpg)are based on the same measurement (returns) samples contained in the observation set, up to time *t* − 1, that is ![image](images/Inline_105_16.jpg)According to the state recursive [equation \[3.26\]](#c03.xhtml#eqn26), the only difference between *θ*[*t*] and *θ*[*t*−1] is the state noise w[*t*] that is statistically orthogonal (uncorrelated with) to *θ*[*t*−1], because of the “innovation property” (see section 3.9). Moreover, w[*t*] is not correlated to the observation noise ![images](images/e.gif)[*t*], by assumption. This means that w[*t*] is statistically orthogonal to the measurement set ![image](images/Inline_106_2.jpg)Therefore, any of the samples contained in ![image](images/Inline_106_3.jpg)cannot contribute to an estimation of w[*t*] . There is thus no rationale to change the estimate ![image](images/Inline_106_4.jpg)when switching to ![image](images/Inline_106_5.jpg)as expressed in [equation \[3.34\]](#c03.xhtml#eqn34).

## 3.12.2. *Prediction accuracy processing, [equation \[3.35\]](#c03.xhtml#eqn35)*

As defined at the beginning of this section, the matrix S[*n*|*q*] is a covariance matrix and, as such, is a non-negative definite matrix (all its eigenvalues are greater or equal to zero). For the sake of fluidity of the present interpretation, we assume that S[*n*|*q*] is full rank (none of its eigenvalues is vanishing). Consequently, its inverse ![image](images/Inline_106_8.jpg)exists and is positive definite. Both their traces are positive, and thus the trace of ![image](images/Inline_106_9.jpg)denoted ![image](images/Inline_106_10.jpg)can be used, in the context of KF, as a positive measure or magnitude of the updates accuracy. Indeed, the larger the trace ![image](images/Inline_106_10.jpg), the “smaller” the error, and the larger the accuracy. If the matrix S[*n|q*] is zero (the error is zero), the accuracy degree becomes “infinite” which is consistent with common sense. We denote ![image](images/Inline_106_12.jpg)the eigenvalues of S[*n|q*] that are all assumed to be strictly positive for the sake of simplicity of the current interpretation, that is ![image](images/Inline_106_13.jpg)Taking into account that the eigenvalues of the inverse of a matrix are equal to the inverse of the eigenvalues of the matrix and noting that the trace is also the summation of the eigenvalues, it is then straightforward to derive from \[3.35\] and the definition of the accuracy degree the following relationship:

[\[3.39\]](#c03.xhtml#eqn_39) ![image](images/img_14_105.jpg)

[Equations \[3.34\]](#c03.xhtml#eqn34) and [\[3.39\]](#c03.xhtml#eqn39) mean that the prediction step decreases the “accuracy”, because (obviously) ![image](images/Inline_107_2.jpg)Inherently, this is not surprising: the state noise w[*t*] that is part of the recursive model \[3.26\] is statistically orthogonal to ![image](images/Inline_107_3.jpg)Consequently, no change of the estimate takes place ([equation \[3.34\]](#c03.xhtml#eqn34)) in the prediction step, while the previous state *θ*[*t*−1] undergoes the additive state noise ([equation \[3.26\]](#c03.xhtml#eqn26)). Accuracy will improve only across the correction step that fully benefits from the new return measurement *r*[*t*] .

## 3.12.3. *Correction filtering [equations \[3.36\]](#c03.xhtml#eqn36)–[\[3.37\]](#c03.xhtml#eqn37)*

We start the correction updates interpretation by noting that, in [equation \[3.37\]](#c03.xhtml#eqn37), the term ![image](images/Inline_107_6.jpg)is a genuine estimate ![image](images/Inline_107_7.jpg)of the current measurement *r*[*t*] based on its past samples contained in ![image](images/Inline_107_9.jpg)Therefore, the difference ![image](images/Inline_107_8.jpg)equal to ![image](images/Inline_107_10.jpg)stands for an error signal, denoted ![image](images/Inline_107_11.jpg)and called, in what follows, the current measurement (return) innovation. Moreover, the difference ![image](images/Inline_107_12.jpg)might also be viewed as an estimate ![image](images/Inline_107_13.jpg)of the observation noise ![images](images/e.gif)[*t*] . Finally, we have the following identities chain that turns out to be truly meaningful to understand the different aspects of [equation \[3.37\]](#c03.xhtml#eqn37):

\[3.40\] ![image](images/img_14_106.jpg)

Substitution of the first of the above identities in \[3.37\] yields the following simple form of the correction KF updates:

\[3.41\] ![image](images/img_17_106.jpg)

[Equation \[3.37\]](#c03.xhtml#eqn37) and its more concise version \[3.41\] clearly express that the correction update, that is *t*|*t* − 1 → *t*|*t*, balances the weight of predicted estimate ![image](images/Inline_107_20.jpg)(based on the prediction filtering) and the weight of the measurement (return) estimation error (innovation)![image](images/Inline_107_21.jpg)via the Kalman gain z[*t*] . According to [equation \[3.36\]](#c03.xhtml#eqn36), for a given covariance matrix S[*t|t*−1], when the observation noise variance ![image](images/Inline_108_2.jpg)increases, the Kalman gain norm:

\[3.42\] ![image](images/img_3_107.jpg)

decreases, subsequently reducing the weight of the measurement (return) innovation ![image](images/Inline_108_6.jpg)in the final update. This self-regulation of the correction is actually expected. When the observation noise is large, the measurement estimate is not reliable and the associated error should be marginalized, in the overall updating process to prevent further contamination of the current estimate. The Kalman gain norm is also drastically reduced when, for a given ![image](images/Inline_108_7.jpg)the covariance matrix S[*t|t*−1] becomes “small”, like close to the zero matrix. In this case, the Kalman gain vanishes since the filter has converged close to the solution and any new measurement will not significantly improve the estimate. In this latter situation, the KF reliability is mostly put on the predicted component ![image](images/Inline_104_9.jpg)

Conversely, when the variance ![image](images/Inline_108_10.jpg)of the observation noise decreases, the measurement component of the update \[3.37\] becomes more reliable and should thus be more emphasized which is the case since the Kaman gain norm \[3.42\] subsequently increases.

## **3.12.4.** ***Correction accuracy processing, [equation \[3.38\]](#c03.xhtml#eqn38)***

To interpret the accuracy update contained in [equation \[3.38\]](#c03.xhtml#eqn38), it is appropriate to replace the Kalman gain by its explicit form given by [equation \[3.36\]](#c03.xhtml#eqn36). In doing so, [equation \[3.38\]](#c03.xhtml#eqn38) becomes:

\[3.43\] ![image](images/img_13_107.jpg)

with ![image](images/Inline_109_2.jpg)Moreover (still assuming that the matrix S[*t*|*t*–1] is full rank for the sake of simplicity), the matrix inversion lemma (see Appendix 3.16) yields:

\[3.44\] ![image](images/img_3_108.jpg)

Combining \[3.43\], \[3.44\] and \[3.45\] leads to the following chain of updates:

[\[3.45\]](#c03.xhtml#eqn_45) ![image](images/img_6_108.jpg)

[equation \[3.45\]](#c03.xhtml#eqn45) is easy to interpret in terms of degree of accuracy. As a matter of fact, [equation \[3.38\]](#c03.xhtml#eqn38) and consequently \[3.45\] mean that the correction step always improves the accuracy w.r.t. of the prediction step, because \[3.45\] implies that:

\[3.46\] ![image](images/img_9_108.jpg)

Recursion \[3.46\] clearly means that ![image](images/Inline_109_12.jpg)the correction step always increases degree of accuracy, as much as the quantity ![image](images/Inline_109_13.jpg)is large. This latter entity that may be viewed as “factor-to-observation noise ratio” of the measurement becomes marginal if the variance ![image](images/Inline_109_14.jpg)of the observation noise drastically increases, thus limiting significantly the accuracy gain. Another virtue of the update \[3.45\] arises from the “numerical” propagation of the positive-definiteness of the inverse of the covariance matrix ![image](images/Inline_109_15.jpg)Indeed, we derive from \[3.45\] that, whatever is the non-zero vector u:

\[3.47\] ![image](images/img_16_108.jpg)

Identity \[3.47\] leads to:

\[3.48\] ![image](images/img_2_109.jpg)

# **3.13. Practice**

This section is the application part of this chapter. We will study three different cases:

(1) a toy example, where synthetic observed returns are generated like a linear combination of two observed and known factors, the S&P500 Index and the US 10Y-Bond, (2) a one-factor model used to hedge accurately the systematic risk of a given portfolio (section 3.13.2) and then (3) a multi-factor model used in order to analyze and decompose the exposition of trend-follower hedge funds to several market risks as defined by Fung and Hsieh \[FUN 01\] (section 3.13.3). 

## **3.13.1.** ***Comparison of the estimation methods on synthetic data***

### 3.13.1.1. *Data description*

In this example, we generate synthetic observed returns *r*[*t*] on the period September 10 1997/December 19 2012 (around 15 years long with *T* = 3, 986 daily numbers) using two market factors and given theoretical parameters ![image](images/Inline_110_12.jpg)accounting for the betas. The two market factors are:

– the daily returns of the first Generic Future on the mini-S&P500 Index, denoted as ![image](images/Inline_110_15.jpg), – the daily returns of the first Generic Future on the US 10Y Treasury note, denoted as ![image](images/Inline_110_16.jpg), and the resulting synthetic returns are written for *t* = 1, …, *T*: 

\[3.49\] ![image](images/img_17_109.jpg)

Over the whole period, the means and standard deviations of the two market factors are reported in [Table 3.1.](#c03.xhtml#tab3_1)

**[Table 3.1.](#c03.xhtml#tab3-1)** *Mean and standard deviation of the time series of the two market factor used in the toy example*

![image](images/img_4_110.jpg)

Two different cases are considered: (1) *w*[*t*] constant over time and (2) *w*[*t*] piecewise constant over time. For each case, we will compare the estimation results of sliding window ordinary least squares (SW-OLS) and KF.

**– First case:** *w*[*t*] **is constant over time; no observation error** 

[Figure 3.3](#c03.xhtml#Fig3) shows the evolution (base 1,000 at the beginning of the period) of the time series for the two selected market factors and the resulting synthetic data for *w*[*t*] = 0.3, ∀*t*, that is when *w*[*t*] is constant over time.

[**Figure 3.3.**](#c03.xhtml#Fig_3) *Time series of the two selected assets in the toy example and the resulting synthetic data obtained with a constant parameter w[*t*]* = 0.3

![image](images/img_8_110.jpg)

A state equation is added to \[3.49\] to apply a KF. The model is therefore written as:

\[3.50\] ![image](images/img_2_111.jpg)

where ![image](images/Inline_112_5.jpg)with *σ*[є] = 10^(−1).

In that (unrealistic) particular case, the ordinary least squares (OLS)-family methods are the optimal methods. In [Figure 3.4](#c03.xhtml#Fig4), we have reported the estimation results for a SW-OLS (using a 252-long window) and a KF, starting with two different initial values. As expected, SW-OLS returns exactly the theoretical value, whereas the KF estimate converges to the theoretical value after a period of almost 3 years of data, depending also on the initial value.

[**Figure 3.4.**](#c03.xhtml#Fig_4) *SW-OLS and Kalman filter estimation results of the constant parameter (w[*t*]* = 0.3*) in the toy example*

![image](images/img_8_111.jpg)

If we ever add a Gaussian random noise even with a small variance when generating the returns in \[3.49\], then the results differ and the KF estimates yield to lower MMSE than SW-OLS for small window lengths. To illustrate this result, we have run *N[simu]* = 1, 000 simulations:

For each case *i* = 1, …, *N[simu]*:

a) Generate synthetic noisy returns as: 

[\[3.51\]](#c03.xhtml#eqn_51) ![image](images/img_4_112.jpg)

with *σ* = 10^(−3) and **ξ** ∼ *N*(0, 1).

b) SW-OLS: \- for each time *t* = h + 1 to *T*, estimate ![image](images/Inline_113_9.jpg)with SW-OLS given two different window lengths, h = 21 and h = 252; \- compute the root mean square error (RMSE): rmse ![image](images/Inline_113_11.jpg)c) Kalman filter: \- estimate ![image](images/Inline_113_14.jpg)using the KF recursive equations; \- compute the RMSE: rmse ![image](images/Inline_113_16.jpg)

*Note that we could remove the h-first estimated values.*

At the end, we compare in [Figure 3.5](#c03.xhtml#Fig5) the distributions of the RMSEs through a boxplot of the *N[simu]* values of the RMSEs.

[**Figure 3.5.**](#c03.xhtml#Fig_5) *Comparison of the RMSEs for SW-OLS (h* = 21, 252*) and Kalman filter for the synthetic noisy returns of [equation \[3.51\]](#c03.xhtml#eqn51) having a constant parameter w[*t*]* = 0.3

![image](images/img_2_113.jpg)**– Second case:** *w*[*t*] **is piecewise constant** 

Let us now consider that *w*[*t*] is piecewise constant:

\[3.52\] ![image](images/img_5_113.jpg)

The resulting estimations of the piecewise constant parameter are given in [Figure 3.6](#c03.xhtml#Fig6). Overall, SW-OLS and KF react quite well to the changes in parameter *w*[*t*]. It should be noted that the variance of the estimation is lower for the KF than for SW-OLS, especially when SW-OLS is used with small window lengths. Moreover and as expected, the SW-OLS estimates are more lagged than the KF estimates.

[**Figure 3.6.**](#c03.xhtml#Fig_6) *Comparison of the SW-OLS (h* = 21, 126, 252*) and KF for the synthetic and noisy returns of equation* \[3.51\] *having a piecewise constant parameter w[*t*] as defined in \[3.52\] (see color plate section)*

![image](images/img_3_114.jpg)

In practice, portfolio managers do not turn their portfolio so sharply. This case is extreme but highlights the tracking capabilities of the KF in a dynamic environment. It confirms the growing interest in such filtering techniques to dynamically hedge a portfolio or to estimate the nonlinear and dynamic exposures in hedge returns.

The next example is focused on a single-factor model applied to hedge dynamically a truly managed long-only Indian equity portfolio. The objective is to accurately estimate the exposure of the managed portfolio to its reference index, the Nifty Index.

## **3.13.2.** ***Market risk hedging given a single-factor model***

Let us assume in this section that the observed returns *r*[*t*] are the returns of a long-only equity portfolio. The portfolio manager selects a subset of stocks in which to invest and define an allocation either based on his/her own market feeling or resulting from an investment committee.

A long-only equity portfolio is usually constructed and managed in order to over-perform a given stock index that often results in a strong historical correlation between the returns of the portfolio and the stock index itself. What is expected from such an investment is to deliver a performance which is larger than the performance given by the stock index, and this may be due to the manager’s skills to select stocks which will deliver some *α* over the performance of the benchmark.

Given this setup, we can observe that the market risk is not hedged at all. The long-only strategy is not expected to be hedged against any risk arising in the market, but only to deliver a better performance than a given benchmark.

In the case where the market risk has to be hedged, we have to answer to “how much the portfolio is market-dependent?”

As explained by the factor model, if there is a single market risk (the benchmark stock index), then a single-factor model may be used to link the portfolio returns to the market returns:

![image](images/img_7_115.jpg)

where *α*[*t*] is the time-varying “alpha”, *β*[*t*] is the time-varying exposure of the portfolio to the single factor *f*[*t*], and *![images](images/e.gif)*[*t*] has the properties described in the previous section.

In this application, the returns of the long-only equity portfolio are the returns of an Indian equity portfolio managed by an asset manager in India. The manager selects a subset of equity stock according to a discretionary approach based on an in-depth analysis of the fundamental numbers related to the balance sheet of the companies and on a set of specific financial ratios. The selected names are mainly growth companies for which the manager has a strong belief that these companies are under-valued and have a high level of future growth. Each name is kept in the portfolio for a given period, from 1 month to several months. The portfolio comprises between 15 and 30 names at a time. The net asset value (NAV) of this portfolio is shown in [Figure 3.7](#c03.xhtml#Fig7), where an initial value of 1, 000 is set. The returns are net of all fees, including trading costs, management fees, and performance fees and do not include any cash management. In [Figure 3.7](#c03.xhtml#Fig7), the NAV of the BSE200 Index is also reported. BSE200 Index is an index composed by the 200 biggest market capitalizations quoted in the Indian equity market.

[**Figure 3.7.**](#c03.xhtml#Fig_7) *Long-only Indian equity portfolio price and two reference stock indices, the BSE200 Index and the Nifty Index*

![image](images/img_3_116.jpg)

The Indian equity stock market is very specific: even if the BSE200 Index is quoted on a daily basis, there are no future contracts quoted for this index. Only future contracts on the smallest Nifty Index are traded, so that even if the BSE200 Index is chosen as the benchmark reference for the performance of the portfolio, it will not be possible to hedge the portfolio by shorting future contracts on the BSE200 Index. The single-factor *f* is therefore the Nifty Index and the time series used to compute the model parameters is the time series of the generic Nifty Index futures, which is a roll-adjusted time series.

The hedging procedure is presented in the following:

– At each computing time *t*, parameters *α*[*t*] and *β*[*t*] are estimated with method M given, if necessary, a fixed window length. – The value of the estimated *β*[*t*] is then used as the parameter that reflects the linear dependence between the past returns of the portfolio and the past returns of the factor: we will then adjust the previous quantity *q*[*t*−1,*t*] of futures contracts to short, given the required proportion of the portfolio to be hedged at *t* for the period \[*t, t* + 1\]. The quantity of futures contracts to short at *t* for the time range \[*t, t* + 1\] is then given by *q*[*t,t*+1] = *Round* (![image](images/Inline_118_5.jpg)) and the adjustment of the hedge quantity is given by *q*[*t,t*+1] − *q*[*t*−1,*t*] . In this equation, *Round*(.) rounds off the value to the lowest integer value, *NAV*[*t*] denotes the NAV of the portfolio at time *t* and *CV*[*t*] denotes the value of the futures contracts at time *t*, equal to its price time the value of one point of this contract, and ![image](images/Inline_118_6.jpg)is the estimated value of the *β* at time *t*. 

Depending on the method used to estimate the value of *β*, the resulting hedged portfolio will have different behavior, given the fact that the estimation might be lagged, dynamic or jittered with residual outliers.

[**Figure 3.8.**](#c03.xhtml#Fig_8) *Comparison of the estimated exposure of the L/O portfolio to the selected market factor, the Nifty future: a) represents the dynamic estimates of the beta and b) and c) present the estimated spikes if using an RKF or an rgKG-l*¹ *as presented in Chapter 4*

![image](images/img_2_118.jpg)

[Figure 3.8](#c03.xhtml#Fig8) shows the different results obtained for the estimations of the beta using either a SW-OLS (21 and 252 days), a KF, a Robust Kalman Filter (RKF) with *δ* = 0.3 and a regularized version of the KF (rgKF-*l*¹) with *δ*[*t*] = 0.01 (see Chapter 4 for a detailed description of both these algorithms). Estimating the exposure of the portfolio with a short window length and the OLS yields to very noisy estimates. The longer window gives apparently lagged and too smoothed values. The reference will therefore be the KF results which are more reactive to the beta changes than the SW-OLS and much less noisy. If we compare KF results with the results from more advanced techniques which filter the potential specific events, say first RKF and then rgKF-*l*¹, combined with the final hedged portfolios and the resulting cumulative costs (see [Figure 3.9](#c03.xhtml#Fig9)), then rgKF-*l*¹ seems to be more efficient and gives more convenient and reliable exposures of the portfolio to the market factor.

[**Figure 3.9.**](#c03.xhtml#Fig_9) *Cumulative costs induced by shorting nifty Index Futures to hedge the L/O portfolio according to each of the estimation method used*

![image](images/img_3_119.jpg)

The results are shown in [Figure 3.10](#c03.xhtml#Fig10) and compare the NAVs of the long-only Indian equity portfolio hedged by a proportion of Nifty Index futures whose values are determined either by a constant-beta OLS or a 63 days SW-OLS, or a KF, or a RKF, or a rgKF – see Chapter 4 for a detailed presentation.

From a practical view, the KFs are preferred because it leads to dynamic estimation of the parameters where, at time *t*, the only knowledge of the past is fully summarized in the previous set of information given in *t* − 1 without any specification of a window length. Moreover, the equations of the KF introduce a dynamic evolution of the model parameters, which brings some *a priori* information about what we actually do not know.

[**Figure 3.10.**](#c03.xhtml#Fig_10) *NAVs of a long-only Indian equity portfolio hedged by a proportion of nifty Index futures computed with (1) OLS over the whole period, (2) SW-OLS with a window length of 3 months, (3) a Kalman Filter, (4) a Robust Kalman Filter and (5) a regularized version of the Kalman filter, which filters out outliers. The classical KF and its various versions seem to be the more accurate versus the cost of hedging a portfolio*

![image](images/img_2_120.jpg)

[Figure 3.10](#c03.xhtml#Fig10) shows the results for a RKF and a rgKF. KF equations assume conditionally Gaussian-distributed state and observation errors that are invalidated in the presence of outliers. These versions of KF account for outliers in the observation equation and the KF recursive equations are then regularized and therefore robust to outliers. These methods are presented in Chapter 4.

## **3.13.3.** ***Hedge fund style analysis using a multi-factor model***

Analyzing the risks in the hedge fund (HF) industry has gained interest because it has been Noting that, by construction and in keeping with recognized that HF returns have very specific characteristics, such as heavy tail and asymmetric distributions, option-like payoffs and dynamic risk exposures.

Using multi-factor models allows us to decompose the observed returns on a set of several variables, selected as being nonlinearly dependent and bringing multiple insights. The rough task of selecting appropriate factors has been discussed in Chapter 2. In that example, we focused on the estimation methods and use the eight Fung and Hsieh risk factors \[HSI\].

### 3.13.3.1. *Fung and Hsieh risk factors*

The eight risk factors of Fung and Hsieh \[HSI\], as described in Chapter 2, were quoted on a monthly basis from January 1994 to December 2012 and include:

– three *trend-following* risk factors: *PTFSBD*, a bond-based risk factor; *PTFSFX*, a currency-based risk factor, and *PTFSCOM*, a commodity-based risk factor; – two *equity-oriented* risk factors: *SP500*, the Standard & Poors 500 index, and *EquitySizeSpread*, the size spread factor expressed as the difference between the Russell 2000 index monthly total returns and the *SP500* returns; – two *bond-oriented* risk factors: *bond10y*, the monthly change in the 10-year treasury constant maturity yield, and *CreditSpread*, the difference between the monthly change in the Moody’s Baa yield and *bond10y*; – one *emerging market* risk factor: *MXEF*, the Morgan Stanley Capital International (MSCI) emerging market index. 

These factors are stored in f[*t*] at each time *t* as inputs for \[1.4\].

### 3.13.3.2. *Hedge fund data*

The eight risk factors of Fung and Hsieh were initially built to explain trend-follower funds, so we select *directional* HFs such as *global macro*\-hedge funds. Global macro-hedge fund managers may take directional positions in currencies, debt, equities or commodities, and may also elect to take *relative value* positions combining *long* positions paired off against *short* positions.

We illustrate the performance of the different estimation methods on a trend-follower hedge fund, named Aequam Diversified Fund, which has been managed by Aequam Capital since 17 December 2010. The fund is a systematic HF taking long and short positions on futures on bonds, futures on stock indices, futures on foreign exchange and futures on commodities. The fund has been a UCITS IV Fund since June 2012 and is a weekly audited fund with around M$20 of assets under management (AUM). Even though this fund was opened in 2010 we have access to its historical and backtested performance since 2004. Systematic funds have this specificity: backtested performance is reliable because Commodity Trading Advisor (CTA) and systematic funds run a designed process which is exactly the same as the process which is run once the fund is invested. Moreover, managing futures offers a high liquidity to the fund.

[Table 3.2](#c03.xhtml#tab3_2) gives some basic statistics for the eight risk factors and for Aequam Diversified Fund. These statistics are computed using monthly (end month-to-end month) returns. [Figure 3.11](#c03.xhtml#Fig11) illustrates the evolution of the eight risk factors of Fung and Hsieh and Aequam Diversified Fund given a base 100 in December 2003.

### 3.13.3.3. *Estimation methods results*

We compare in this section the results of the estimation of the exposures of the Aequam Diversified Fund for the SW-OLS with 24 months, the KF and the rgKF.

[Figure 3.12](#c03.xhtml#Fig12) displays the tracking performance for Aequam Diversified fund using Fung and Hsieh factors. They have been selected to keep the economic interpretation of the HF exposures. The top graph compares the HF’s NAV to the reconstructed NAVs after estimating its returns using OLS, KF and a rgKF. *NAV*[1] = 1, 000 at the end of November 2005; the first 24 months are discarded in regard to the window length used for OLS estimation.

[**Table 3.2.**](#c03.xhtml#tab3-2) *Averaged statistics and correlation for the eight risk factors of Fung and Hsieh and Aequam Diversified Fund. Computation of the statistics is made on monthly returns from January 2004 to December 2012*

![image](images/img_3_123.jpg)

[**Figure 3.11.**](#c03.xhtml#Fig_11) *Time series evolution of the eight risk factors of Fung and Hsieh and Aequam Diversified Fund given a base 100 in December 2003 and compounding the monthly returns*

![image](images/img_5_123.jpg)

[**Figure 3.12.**](#c03.xhtml#Fig_12) *Estimated and observed hedge fund returns for Aequam Diversified Fund (see color plate section)*

![image](images/img_2_124.jpg)

[Figure 3.12(b)](#c03.xhtml#Fig12) represents the evolution, in a logarithmic scale, of the absolute relative error ![image](images/Inline_125_5.jpg)arising from each of the three estimation methods. KF and rgKF achieve almost the same performance whereas SW-OLS is a long way from the observed time series.

[Figures 3.13](#c03.xhtml#Fig13)–[3.15](#c03.xhtml#Fig15) show the estimated time-varying exposures for Aequam Diversified Fund using respectively a SW-OLS with a 24 month-long window, a KF and a rgKF. SW-OLS and the KF results are similar but SW-OLS results are more volatile and indicate higher exposures to the factors than KF. The management style of this HF is dynamical but the changes in the estimated exposures are rather smoothed month end to month end. This is exactly what occurs during the management of the fund. The positions are calculated three times a day and adjusted day after day according to a smooth indicator mixing a trend filter and a risk-aversion indicator. Moreover, at the end of the period, Aequam Diversified Fund was long on equity index futures, slightly short on interest rates futures (which is equivalent to be long interest rates), short on US Dollar (USD) versus the major foreign exchanges and short on commodity futures, which is equivalent to being long on the synthetic portfolio of straddles in commodity (PTFSCOM).

[**Figure 3.13.**](#c03.xhtml#Fig_13) *Estimated SW-OLS exposures to the eight risk factors of Fung and Hsieh for the Aequam Diversified Fund (see color plate section)*

![image](images/img_3_125.jpg)

The results obtained through this example are coherent with the management style of the fund: dynamic but smoothed exposures and identical exposures versus the real positions. As a preliminary result to the next chapter, it seems that Aequam Diversified Fund does not present any liquidity issues or extreme and specific events because the results of KF and rgKF coincide (no outliers were detected).

**Figure 3.14.** *Estimated KF exposures to the eight risk factors of Fung and Hsieh for the Aequam Diversified Fund (see color plate section)*

![image](images/img_2_126.jpg)

[**Figure 3.15.**](#c03.xhtml#Fig_15) *Estimated rgKF exposures to the eight risk factors of Fung and Hsieh for the Aequam Diversified Fund (see color plate section)*

![image](images/img_4_126.jpg)

# **3.14. Geometrical derivation of KF updating equations**

## **3.14.1.** ***Geometrical interpretation of MSE criterion and the MMSE solution***

KF presentations and derivations are numerous, both in papers and books. In this introductory chapter, instead of following a probabilistic or Bayesian approach that relies on conditional probability densities that often discourage the newcomer who wants to understand where the KF updates come from, we lay a full geometrical foundation of KF, closer to intuitive and Euclidian knowledge, widely shared by most grad readers.

To do so, the first step consists of giving a geometrical interpretation of the problem statement \[3.32\] and the MMSE criterion at time *t* − 1. Indeed, KF updates given in section 3.11 rely on the previous estimate at time *t* − 1.

In [Figure 3.16](#c03.xhtml#Fig16), the plan symbolizes the observation space ![image](images/Inline_128_6.jpg)spanned by the random variables {*r*[1], …, *r*[*t*]^(−1)}. Any vector element ![image](images/Inline_128_7.jpg)of ![image](images/Inline_128_8.jpg)is linearly related to the ![image](images/Inline_128_9.jpg)and is represented by a dotted arrow that belongs to the plan. In general, the state *θ*[*t*−1] at time *t* − 1 does not belong to the observation plan and thus contains a piece of statistical information that is uncorrelated with (statistically orthogonal to) the random variables {*r*[1], …, *r*[*t*−1]}.

The MSE, IE ![image](images/Inline_128_11.jpg), can be viewed geometrically as the square uclidian norm ![image](images/Inline_128_12.jpg)of the “difference vector” ![image](images/Inline_128_13.jpg)drawn in dotted line in [Figure 3.16](#c03.xhtml#Fig16), that is IE ![image](images/Inline_128_14.jpg)As such, the minimum MSE is associated with the minimum geometrical square norm of ![image](images/Inline_128_15.jpg)achieved when the element **ξ**[|*t*−1] coincides with the orthogonal projection of *θ*[*t*−1] onto the observation plan ![image](images/Inline_128_16.jpg), as depicted in [Figure 3.16](#c03.xhtml#Fig16):

[\[3.53\]](#c03.xhtml#eqn_53) ![image](images/img_17_127.jpg)

[**Figure 3.16.**](#c03.xhtml#Fig_16) *Geometrical interpretation of MMSE estimate*

![image](images/img_2_128.jpg)

Orthogonal projection means that the difference vector ![image](images/Inline_129_4.jpg)that achieves the minimun square norm, called in what follows the innovation, ![image](images/Inline_129_5.jpg)is orthogonal to the observation plan. Being orthogonal to the observation plan implies being orthogonal or, in keeping with the random nature of the variables we deal with, being uncorrelated with all the random variables {*r*[1], …, *r*[*t*−1]}.

As a summary, the geometrical light cast on the MMSE, substitutes to the optimization problem a mere orthogonal projection onto the appropriate space (see \[3.53\]). This can also be expressed in the so-called orthogonality principle: “the innovation is statistically orthogonal to the observation space”:

[\[3.54\]](#c03.xhtml#eqn_54) ![image](images/img_7_128.jpg)

The interpretation of the MMSE criterion depicted in [Figure 3.16](#c03.xhtml#Fig16) and more specifically contained in [equations \[3.53\]](#c03.xhtml#eqn53) and [\[3.54\]](#c03.xhtml#eqn54) are the keystones of geometrical derivations of KF updates.

## **3.14.2.** ***Derivation of the prediction filtering update***

We derive in this section [equation \[3.34\]](#c03.xhtml#eqn34). Across prediction filtering, the measurement set is still ![image](images/Inline_130_3.jpg)(no new measurement has been captured w.r.t. the previous estimation). Combination of the recursive component \[3.26\] of the state-space model, [equation \[3.54\]](#c03.xhtml#eqn54) and the linearity of the projection operator lead to the following identity chain:

\[3.55\] ![image](images/img_4_129.jpg)

Innovation property \[3.30\] and the statistical orthogonality between w[*t*] and the observation noise *![images](images/e.gif)*[*t*] yield ![image](images/Inline_130_7.jpg)that implies Proj[![images](images/parallel.gif)]![image](images/Inline_130_8.jpg)which completes the proof of \[3.34\] (see [Figure 3.17](#c03.xhtml#Fig17)).

[**Figure 3.17.**](#c03.xhtml#Fig_17) *Illustration of the prediction filtering update, see also \[3.51\] and \[3.34\]*

![image](images/img_10_129.jpg)

## **3.14.3.** ***Derivation of the prediction accuracy update***

We derive in this section [equation \[3.35\]](#c03.xhtml#eqn35). Across the prediction accuracy updating, the measurement set is still ![image](images/Inline_130_13.jpg)(no new measurement has been captured w.r.t. the previous estimation). The definition of the *KF*(*n*/*q*) innovation ![image](images/Inline_131_2.jpg)combined with \[3.34\] and \[3.26\] leads to the recursive computation of the “prediction step innovation” ![image](images/Inline_131_3.jpg)

[\[3.56\]](#c03.xhtml#eqn_56) ![image](images/img_4_130.jpg)

Moreover, ![image](images/Inline_131_7.jpg)because of the innovation property \[3.30\] and the following orthogonality ![image](images/Inline_131_8.jpg)unveiled in section 3.14.2 (see [Figure 3.17](#c03.xhtml#Fig17)). Taking into account both the definition of the covariance matrix ![image](images/Inline_131_9.jpg)and [equation \[3.56\]](#c03.xhtml#eqn56) added to the fact that the covariance matrix of the summation of two uncorrelated vectors is the summation of the two associated covariance matrices, this completes the proof of \[3.35\].

## **3.14.4.** ***Derivation of the correction filtering update***

We derive in this section both [equations \[3.36\]](#c03.xhtml#eqn36) and [\[3.37\]](#c03.xhtml#eqn37).

### 3.14.4.1. *Updating of the measurement set*

Correction filtering leverages the new measurement *r*[*t*] thus involving orthogonal projections (as per section 3.14.1) onto the enlarged (updated) observation (return) set ![image](images/Inline_131_14.jpg). Because *r*[*t*] is not necessarily orthogonal to the previous measurement set ![image](images/Inline_131_15.jpg), the orthogonal projection onto ![image](images/Inline_131_16.jpg)is not necessarily equal to the summation of the projection onto ![image](images/Inline_131_17.jpg)and the projection on *r*[*t*], as it would be the case, if the projection was operating with an orthogonalized enlarged measurement (return) set. Nevertheless, the correction filtering update requires the expression of Proj![image](images/Inline_131_18.jpg)in terms of Proj![image](images/Inline_131_19.jpg)This becomes possible by “orthogonalizing” the enlarged observation (return) set ![image](images/Inline_131_20.jpg)

### 3.14.4.2. *Orthogonal decomposition of the updated observation set* ![image](images/Inline_132_2.jpg)

Orthogonalizing the enlarged set ![image](images/Inline_132_4.jpg)consists of breaking the new measurement *r*[*t*] into a component that belongs to ![image](images/Inline_132_5.jpg)plus an orthogonal residual. This orthogonal splitting is straightforwardly derived from the geometrical interpretation described in section 3.14.1. Indeed, applying the orthogonal break of *θ*[*t*−1] displayed in [Figure 3.16](#c03.xhtml#Fig16) to *r*[*t*] yields:

[\[3.57\]](#c03.xhtml#eqn_57) ![image](images/img_6_131.jpg)

where, by construction, ![image](images/Inline_132_9.jpg)Moreover, the observation component \[3.27\] of the state-space model allows us to write:

\[3.58\] ![image](images/img_10_131.jpg)

Linearity properties of the projection operator, the uncorrelation (orthogonality) between *![images](images/e.gif)*[*t*] and ![image](images/Inline_132_13.jpg)combined with [equations \[3.27\]](#c03.xhtml#eqn27) and [\[3.57\]](#c03.xhtml#eqn57), give the following identities:

[\[3.59\]](#c03.xhtml#eqn_59) ![image](images/img_14_131.jpg)

Finally, we can write that the updated measurement set ![image](images/Inline_132_17.jpg)is split between ![image](images/Inline_132_20.jpg)and the new measurement innovation ![image](images/Inline_132_19.jpg)that happens to be orthogonal to ![image](images/Inline_132_20.jpg)by construction:

[\[3.60\]](#c03.xhtml#eqn_60) ![image](images/img_21_131.jpg)

In \[3.60\], the symbol ⊕ stands for the orthogonal decomposition.

### 3.14.4.3. *Correction of the predicted estimate* ![image](images/Inline_133_2.jpg)*based on the new measurement* *r*[*t*]

In terms of orthogonal projection, the identity of \[3.60\] helps to split the projection of *θ*[*t*] into the enlarged measurement (return) set ![image](images/Inline_133_4.jpg)such that:

[\[3.61\]](#c03.xhtml#eqn_61) ![image](images/img_5_132.jpg)

In keeping with the geometrical interpretation depicted in [Figure 3.16](#c03.xhtml#Fig16) of the different estimates, [equation \[3.61\]](#c03.xhtml#eqn61) can be rewritten in order to express the new estimate ![image](images/Inline_133_8.jpg)as the “predicted estimate” ![image](images/Inline_133_9.jpg)plus a “correction term” due to the new observation *r*[*t*] :

[\[3.62\]](#c03.xhtml#eqn_62) ![image](images/img_10_132.jpg)

The correction term is equal to Proj![image](images/Inline_133_9a.jpg)and it has to be explicitly evaluated to obtain \[3.36\] and \[3.37\]. [Figure 3.18](#c03.xhtml#Fig18) geometrically illustrates identity \[3.62\].

[**Figure 3.18.**](#c03.xhtml#Fig_18) *Geometrical illustration of the correction update undergone by the predicted estimate* ![image](images/img_10_132a.jpg)*due to the new measurement *r*[*t*], see also [equations \[3.59\]](#c03.xhtml#eqn59) and [\[3.62\]](#c03.xhtml#eqn62)*

![image](images/img_14_132.jpg)

### 3.14.4.4. *Evaluation of the correction component Proj*![image](images/Inline_133_16.jpg)

Like any projection and as illustrated in [Figure 3.18](#c03.xhtml#Fig18), the orthogonal projection of *θ*[*t*] on the measurement innovation ![image](images/Inline_134_2.jpg)is “proportional” to ![image](images/Inline_134_3.jpg)But since *θ*[*t*] is a vector and ![image](images/Inline_134_4.jpg)a scalar, the proportionality relationship involves a vector z[*t*] such that:

[\[3.63\]](#c03.xhtml#eqn_63) ![image](images/img_5_133.jpg)

Noting that, by construction and in keeping with [Figure 3.18](#c03.xhtml#Fig18), the “difference” ![image](images/Inline_134_8.jpg)is statistically orthogonal to ![image](images/Inline_134_4.jpg)which allows us to derive the explicit form of z[*t*] . Indeed, the definition of statistical orthogonality, combined with \[3.63\], yields the following chain:

\[3.64\] ![image](images/img_9_133.jpg)

Chain \[3.64\] straightfowardly leads to:

[\[3.65\]](#c03.xhtml#eqn_65) ![image](images/img_12_133.jpg)

Taking into account that ![image](images/Inline_134_15.jpg)and [equation \[3.59\]](#c03.xhtml#eqn59) added to the orthogonality between *![images](images/e.gif)*[*t*] and ![image](images/Inline_134_15b.jpg)help us to write the denominator of z[*t*] as:

\[3.66\] ![image](images/img_16_133.jpg)

According to [equation \[3.60\]](#c03.xhtml#eqn60) and [Figure 3.18](#c03.xhtml#Fig18), we have ![image](images/Inline_134_19.jpg)therefore, ![image](images/Inline_134_20.jpg)which combined with \[3.55\], allows us to write the following different forms of the numerator of z[*t*] \[3.36\] as:

[\[3.67\]](#c03.xhtml#eqn_67) ![image](images/img_21_133.jpg)

Finally [equations \[3.63\]](#c03.xhtml#eqn63) and [\[3.65\]](#c03.xhtml#eqn65)–[\[3.67\]](#c03.xhtml#eqn67) give:

\[3.68\] ![image](images/img_24_133.jpg)

### 3.14.4.5. *Correction filtering updates, [equations \[3.36\]](#c03.xhtml#eqn36) and [\[3.37\]](#c03.xhtml#eqn37)*

We derive from \[3.59\], \[3.62\] and \[3.68\] the following correction filtering update chain due to the capture of the new measurement *r*[*t*]:

\[3.69\] ![image](images/img_3_134.jpg)

which coincides with \[3.36\] and \[3.37\] noting that z[*t*] is nothing but the Kalman gain.

## **3.14.5.** ***Derivation of the correction accuracy update***

We derive in this section [equation \[3.38\]](#c03.xhtml#eqn38). From the first identity of the chain \[3.69\], we have:

\[3.70\] ![image](images/img_8_134.jpg)

which combined with \[3.59\] and the definition of the innovation ![image](images/Inline_134_15b.jpg)implies:

\[3.71\] ![image](images/img_12_134.jpg)

Moreover, because of the orthogonality principle, that is ![image](images/Inline_135_15.jpg), the following identity holds:

\[3.72\] ![image](images/img_16_134.jpg)

Substituting \[3.71\] into \[3.72\] and the fact that ![image](images/Inline_135_19.jpg)yield:

\[3.73\] ![image](images/img_20_134.jpg)

Finally the identity is:

\[3.74\] ![image](images/img_2_135.jpg)

due also to the orthogonality principle (i.e.![image](images/Inline_136_5.jpg), see [Figure 3.17](#c03.xhtml#Fig17), transforming [equation \[3.38\]](#c03.xhtml#eqn38) into \[3.73\] which completes its proof.

# **3.15. Highlights**

This section gives a summary of the most important outcomes of the chapter dealing with LSE and KF.

#### ***Least squares estimation (LSE)***

LSE implicitly assumes that a linear regression holds between the returns, the factors, the alpha and the betas, across a certain observation window, (*t, h*) = {*l,* such that: *t* − *h* + 1 ≤ *l* ≤ *t*}; this regression is also called the LSE “block” measurement equation, it is as follows:

[\[3.75\]](#c03.xhtml#eqn_75) ![image](images/img_10_135.jpg)

The inputs of the LSE block regression are: the values of one specific return within the window ![image](images/Inline_136_13.jpg)and the factors contained in the \[*h, K* + 1\] “factor matrix”, ![image](images/Inline_136_14.jpg)with ![image](images/Inline_136_15.jpg)Factors are also named the regressors. The unknown or the parameters of the LSE regression are the alpha and betas that are assumed constant across the window. They filled up the column-vector *θ*[(*t*,*h*)] with *θ*′[(*t*,*h*)] = ![image](images/Inline_136_16.jpg)The residual of the LSE regression is *є*[(*t*,*h*)] with ![image](images/Inline_136_17.jpg)

The LSE ![image](images/Inline_136_19.jpg)minimizes the (convex) square Euclidian norm of the difference between the measurement (return) vector r[(*t*,*h*)] and its linear approximation based on the factors, that is G[(*t*,*h*)] *ξ*. Assuming that the \[*h, K* + 1\] matrix G[(*t*,*h*)] is full rank, the LSE solution is unique and we have:

\[3.76\] ![image](images/img_2_136.jpg)

The LSE ![image](images/Inline_137_5.jpg)is an unbiased estimate of *θ*[(*t*,*h*)] but its variance may become large when the matrix (G′ G)[(*t*,*h*)] is ill conditioned. This happens if its minimum eigenvalue becomes too small. In this latter situation, the LSE has to be “regularized” to limit the magnitude of ![image](images/Inline_137_6.jpg)(this topic is addressed in Chapter 4). The term ![image](images/Inline_137_7.jpg)is the orthogonal projection of the return vector r[(*t*,*h*)] into the space spanned by the columns of the factor matrix G[(*t*,*h*)]. The LSE ![image](images/Inline_137_8.jpg)operates in a block processing fashion and is not recursive. It has thus limited tracking capabilities.

#### ***Kalman setup, objective and geometrical view***

The KF setup bears two enabling features that naturally lead to a recursive estimate ![image](images/Inline_137_11.jpg)of the parameter vector *θ*[*t*] (whose components are the alpha and betas). These two key characteristics are missing in the LSE model. First and as opposed to LSE, KF set up leverages an “instantaneous” measurement equation (involving the return, the factors, the alpha and the betas). KF does not need any windowing of the data, as LSE does: LSE [equation \[3.75\]](#c03.xhtml#eqn75) is a block and not instantaneous measurement equation. Indeed, KF observation (return) equation takes the following “instantaneous” form:

[\[3.77\]](#c03.xhtml#eqn_77) ![image](images/img_12_136.jpg)

with ![image](images/Inline_137_15.jpg)and ![image](images/Inline_137_16.jpg). Second, KF setup relies on a recursive equation that drives the dynamic evolution of *θ*[*t*] . This is called the state recursive equation (*θ*[*t*] is a function of the previous value *θ*[*t*−1]). The recursive equation that does not exist in the LSE model may be derived from the laws of physics, econometrics, finance, etc., or it may be intuitively postulated. In this latter and frequent situation, its form has to be parsimonious. The simplest intuitive “state recursive” equation is as follows:

[\[3.78\]](#c03.xhtml#eqn_78) ![image](images/img_2_137.jpg)

where w[*t*] is a zero-mean, white, Gaussian noise. The above recursive parameters (i.e. the alpha and betas) equation means that the new “state” of the parameters at time *t* is equal to the previous “state” at time *t* − 1 plus another component, the state noise w[*t*] that is statistically orthogonal (uncorrelated) to the previous state that is w[*t*] ![images](images/parallel.gif)*θ*[*t*−1].

Given the recursive evolution equation of the alpha and betas \[3.78\] and the collection of returns ![image](images/Inline_138_6.jpg)that are assumed following the observation [equation \[3.77\]](#c03.xhtml#eqn77), KF provides a recursive (and linear) estimate ![image](images/Inline_138_7.jpg)that minimizes the MSE IE ![image](images/Inline_138_8.jpg)(IE\[.\] designates the expected value). The vector *ξ*[|t] belongs to the space ![image](images/Inline_133_4.jpg)spanned by the returns {*r*[*k*], 1 ≤ *k* ≤ *t*}. As defined, the KF optimality criterion benefits from the same (natural) geometrical interpretation as the LSE Euclidian metrics, provided the MSE is viewed as the square of a special Euclidian norm ![image](images/Inline_138_10.jpg)that is ![image](images/Inline_138_11.jpg)

### ***Kalman filtering solution and updates***

KF provides updating not only for the previous estimate ![image](images/Inline_138_14.jpg)but also for the previous covariance or “accuracy” matrix, ![image](images/Inline_138_15.jpg), as suggested by the MSE criterion.

The two inputs of the full KF updating step from *t* − 1|*t* − 1 to *t*|*t* are thus the “previous” estimate and “previous” covariance matrix, that is ![image](images/Inline_138_14.jpg)and ![image](images/Inline_139_2.jpg)with *t* ≥ 1. This full KF step is split between the prediction and the correction steps.

– **Prediction step:** from *t* − 1|*t* − 1 to *t*|*t* − 1 

Inputs:![image](images/Inline_139_5.jpg)Output:![image](images/Inline_139_6.jpg)(“predicted” estimate and “predicted” covariance matrix).

The prediction transition leverages the recursive evolution [equation \[3.78\]](#c03.xhtml#eqn78) to “recursively” anticipate the evolution of the estimate and its accuracy based only on the predicted parameter, according to the model \[3.78\]. The prediction step does not make use of a new measurement (current value of the return). It comprises the prediction filtering and the prediction accuracy processing:

Prediction filtering

\[3.79\] ![image](images/img_9_138.jpg)

Prediction accuracy processing

[\[3.80\]](#c03.xhtml#eqn_80) ![image](images/img_12_138.jpg)

Because the prediction transition does not benefit from a new value of the return, it loses accuracy as displayed in [equation \[3.80\]](#c03.xhtml#eqn80), that is ![image](images/Inline_139_15.jpg)

– **Correction step:** from *t*|*t* − 1 to *t*|*t* 

Inputs (predicted estimate and covariance matrix): ![image](images/Inline_139_18.jpg)Outputs:![image](images/Inline_139_19.jpg)(“current” estimate and “current” covariance matrix).

The correction step leverages the instantaneous observation [equation \[3.78\]](#c03.xhtml#eqn78) and the current value of the return *r*[*t*] . The correction step comprises the correction filtering and the correction accuracy processing. The correction filtering balances, via the Kalman gain z[*t*] the weight of the predicted estimate ![image](images/Inline_140_2.jpg)and the weight of the current measurement *r*[*t*] :

Correction filtering

\[3.81\] ![image](images/img_4_139.jpg)

Correction accuracy processing

\[3.82\] ![image](images/img_7_139.jpg)

The Kalman gain ![image](images/Inline_140_10.jpg)decreases if the current measurement is not reliable (large variance ![image](images/Inline_140_11.jpg)of the measurement noise) or if the algorithm has converged close to the true parameter (covariance matrix ![image](images/Inline_140_12.jpg)is “small”). In these two latter situations, priority is given to the predicted estimate ![image](images/Inline_140_2.jpg). Conversely, the Kalman gain increases if the observation noise becomes marginal, that is ![image](images/Inline_140_14.jpg)KF is thus self-regulated via its gain.

# **3.16. Appendix: Matrix inversion lemma**

In this appendix, we prove identity \[3.44\] based on direct calculation of the following matrix P:

\[3.83\] ![image](images/img_17_139.jpg)

Noting that the quadratic form ![image](images/Inline_140_20.jpg)is a scalar, we straightly derive from \[3.83\] that:

\[3.84\] ![image](images/img_21_139.jpg)

In \[3.84\], I designates the identity matrix. On the right-hand side of \[3.84\], reduction to the same denominator of ![image](images/Inline_140_24.jpg)yields finally the identity P = I that completes the proof of \[3.44\].

# Chapter 4

# A Regularized Kalman Filter (rgKF) for Spiky Data

# **4.1. Introduction**

This chapter is an extension of the previous chapter and presents a regularized version of the Kalman filter (KF). As stated earlier, the recursive equations of the KF rely on the Gaussian assumption of the errors of the model so that exogenous outliers coming from either unknown sensor failures, abnormal measurements, portfolio illiquidity issues or even intentional jamming challenge the state-space model introduced in Chapter 3.

In the framework of tracking or estimating unobserved processes, usually solved with KF or one of its extensions, such exogenous outliers are referred to as *additive outliers* or *AOs* \[FOX 72, RUC 10\] and occur in the observation. Endogenous outliers that may affect the innovations of the state equation are called *innovative outliers* or *IOs* and are beyond the scope of this book. Recursive least squares can serve to deal with AOs applying a Huber weight function \[MAR 06\] to the innovation error in the KF recursive equation. We can also penalize the KF by introducing an *l*¹\- or *l*²\-regularization term. Regularization usually offers good results but requires the determination of the regularization parameter introduced to limit the amplitude of the solution. The search for the optimal regularization parameter has no ideal solution and each existing method (e.g. cross-validation, generalized cross-validation \[CRA 79\], maximum *a posteriori* estimation \[PAN 11\], Bernouilli-Gaussian assumption or Markov Chain Monte Carlo (MCMC) methods \[AND 97\]) is relevant to the problem under study. Regularization is widely used in statistical signal processing (e.g. in basis pursuit, compressed sensing, signal recovery and wavelet thresholding), in statistics with ridge regressions and Least Absolute Shrinkage and Selection Operator (LASSO) algorithm or fused LASSO \[TIB 96\] and is also very useful in decoding linear codes or geophysics problems. In finance, *l*¹\-regularization also applies in the context of portfolio optimization \[JAG 03, BRO 08, DEM 09\].

In this chapter, we first discuss a robust Kalman filter (RKF) as presented in \[MAT 10\], whose performance depends on the value of the regularization parameter, and then propose an alternative methodology to the choice of the regularization parameter by introducing an outlier *detection* step in the recursive equations of the KF. Detecting first the presence of the outliers is equivalent to implicitly choosing the value of the regularization parameter and remains valid even if there is no outlier.

This chapter is organized as follows: section 4.3 discusses the RKF as described in \[MAT 10\]. The family of *detection and estimation* algorithms that we introduce to handle exogenous outliers is discussed in section 4.4. Section 4.5 deals with the application of our algorithm to detect irregularities in hedge fund returns.

# **4.2. Preamble: statistical evidence on the KF recursive equations**

If we have a look to the recursive equations of the KF (summarized in the table below), we clearly realize that the observation *r*[*t*], the unknown and unobserved states *θ*[*t*] and the innovation are Gaussian processes. If a large error measurement (most often considered an outlier) occurs at *t*, the observation *r*[*t*] is then corrupted as well as the innovation term. It will yield to an erroneous correction for ![images](images/eqn1.gif)whereas the accuracy matrix S[t/t] and the Kalman gain z[*t*] will not be impacted. The error will spread along the recursions especially if the error variance is fixed.

![images](images/img_4_142.jpg)

In such a case, the state-space model may be extended with an additional term in the observation equation, which will be taken into account in the recursive estimates. The following section describes how to deal with such an extended model and discusses the RKF (see \[MAT 10\]).

# **4.3. Robust KF**

## **4.3.1.** ***RKF description***

The setup of the RKF introduces an additional term in \[3.27\] to capture outliers that may appear in the observations. The extended state-space model is written as follows \[MAT 10\]:

\[4.1\] ![images](images/img_2_143.jpg)

\[4.2\] ![images](images/img_4_143.jpg)

The basic assumptions are the same as for the state-space model \[3.27\] and *v*[*t*] is a stochastic impulse process, for example a Bernoulli–Gaussian process, suitable for modeling unknown sensor failures, measurement outliers or even intentional jamming. As with the standard KF (where *v*[*t*] = 0), the objective of the problem stated in \[4.1\] and \[4.2\] is to derive recursive estimate![images](images/Inline_144_7.jpg)of the unobservable parameter *θ*[*t*], given the measurement *r*[*t*] and the observed variables g[*t*] up to time *t*, based on the minimization of the mean-square error (MSE)![images](images/Inline_144_8.jpg).

In the presence of the non-Gaussian outlier *v*[*t*], the optimum recursive estimate cannot be explicitly derived and moreover may be nonlinear. An elegant alternative consists of regularizing the KF quadratic cost function by adding a *l*^(*q*) -penalty (*l*¹ in RKF).

The RKF algorithm consists of following steps:

[\[4.3\]](#c04.xhtml#equ4-3) ![images](images/img_11_143.jpg)

\[4.4\] ![images](images/img_13_143.jpg)

\[4.5\] ![images](images/img_13_143b.jpg)

\[4.6\] ![images](images/img_17_143.jpg)

[\[4.7\]](#c04.xhtml#equ4-7) ![images](images/img_19_143.jpg)

\[4.8\] ![images](images/img_21_143.jpg)

Regularization ![images](images/Inline_144_8a.jpg)is a solution of min*[vt] C*(*v[t] ,δ*)

[\[4.9\]](#c04.xhtml#equ4-9) ![images](images/img_2_144.jpg)

with

\[4.10\] ![images](images/img_5_144.jpg)

\[4.11\] ![images](images/img_7_144.jpg)

[Equations \[4.3\]](#c04.xhtml#equ4_3)–[\[4.7\]](#c04.xhtml#equ4_7) are similar to the KF recursive equations. [Equation \[4.9\]](#c04.xhtml#equ4_9) is referred to as a *regularized regression* and is equivalent to the LASSO setup \[TIB 96, OSB 00\]. Given an appropriate value of *δ*, minimizing *C*(*v*[*t*] *,δ*) is equivalent to both detecting and estimating *v*[*t*] . The *l*¹ -norm will reduce the value of *v*[*t*] to zero for high values of *δ* and consider a non-zero value of *v*[*t*] with a small value of *δ* (see [Figure 4.1](#c04.xhtml#fig4_1) for an illustration). Jointly detecting and estimating ![images](images/Inline_144_8a.jpg)depends therefore on the good choice of *δ*, which has to be tuned such that the sparsity of *v*[*t*] coincides with the sparsity seen through the observations. If the value of *δ* is inappropriate, then many false alarms are generated. In \[TIB 96\], the author observes that the search for *δ* can be restricted to the range![images](images/Inline_145_10.jpg)In practice, the upper bound seems to be very generous \[SCH 05\], but it can be adaptive and specific to the observed variable.

# **4.4. rgKF: the rgKF(NG,*l^q*)**

## **4.4.1.** ***rgKF description***

Hereafter, we propose a family of algorithms called regularized Kalman filters or rgKF(OD, E-*l*^(*q*) ) that includes an outlier detection (OD) step followed by an *l*^(*q*) (*q* > 0) estimation step (E-*l*^(*q*) ). OD stands for the name of the detection method, for example if OD = *NG*(*α*), then a non-Gaussian deviation test is applied with a threshold extreme value *α*.

**[Figure 4.1.](#c04.xhtml#fig4-1)** *Effect of the l*¹ *\-regularization term on the shape of a quadratic form to be minimized*

![images](images/img_3_145.jpg)

In the following, we consider only *q* = 1, 2. RKF, which consists of a single and joint detection/estimation step, falls into the *l*¹\-regularization approach and is equivalent to rgKF(*l*¹, E-*l*¹). [Table 4.1](#c04.xhtml#tab4_1) summarizes these algorithms.

The rgKF is a simple and efficient algorithm. Based on the fact that *v*[*t*] is an AO in the observations, it is obvious that the innovation![images](images/Inline_146_6.jpg)in \[4.5\] should contain *v[t]* if *v[t]* occurs at time *t*. Moreover, the observation error![images](images/Inline_146_8.jpg)is assumed to be a Gaussian random variable with a fixed variance![images](images/Inline_146_9.jpg). If *v*[*t*] occurs at time *t*, then![images](images/Inline_146_10.jpg)should not lie in the range space of the Gaussian density.

**[Table 4.1.](#c04.xhtml#tab4-1)** *Family of outlier detection and estimation algorithms*

![images](images/img_3_146.jpg)

Our rgKF algorithm \[JAY 11b\] with exogenous outlier *detection and estimation* can be summarized in the following steps:

[\[4.12\]](#c04.xhtml#equ4-12) ![images](images/img_4_146.jpg)

\[4.13\] ![images](images/img_6_146.jpg)

\[4.14\] ![images](images/img_8_146.jpg)

[\[4.15\]](#c04.xhtml#equ4-15) ![images](images/img_10_146.jpg)

\[4.16\] ![images](images/img_12_146.jpg)

\[4.17\] ![images](images/img_14_146.jpg)

\[4.18\] ![images](images/img_16_146.jpg)

\[4.19\] ![images](images/img_18_146.jpg)

\[4.20\] ![images](images/img_20_146.jpg)

Outlier estimation

\[4.21\] ![images](images/img_23_146.jpg)

[\[4.22\]](#c04.xhtml#equ4-22) ![images](images/img_1_147.jpg)

\[4.23\] ![images](images/img_2_147.jpg)

![images](images/img_4_147.jpg)

\[4.24\] ![images](images/img_5_147.jpg)

[\[4.25\]](#c04.xhtml#equ4-25) ![images](images/img_7_147.jpg)

[\[4.26\]](#c04.xhtml#equ4-26) ![images](images/img_9_147.jpg)

\[4.27\] ![images](images/img_11_147.jpg)

\[4.28\] ![images](images/img_13_147.jpg)

[Equations \[4.12\]](#c04.xhtml#equ4_12)–[\[4.15\]](#c04.xhtml#equ4_15), [\[4.22\]](#c04.xhtml#equ4_22) and [\[4.25\]](#c04.xhtml#equ4_25)–[\[4.26\]](#c04.xhtml#equ4_26) are similar to the RKF recursive equations as RKF is a particular case of rgKF.

The OD step \[4.18\] presented above is a classical non-Gaussian test. It allows for incorporating the recursive prediction and correction equations for the first two moments of the innovation process (mean and variance) and has thus the advantage of keeping the recursive property of the original KF.

Parameter *α* of the hypothesis tests \[4.19\] and \[4.20\] is often around 3 but may be chosen as an *α*\-quantile of the Gaussian distribution. For example, if we aim at detecting an outlier within a 1% confidence interval, then *α* is such that ![images](images/Inline_148_18.jpg)which is *α* = 2.5758 (such values can be found in the statistical tables like in \[FOR 10\]). The often used value of *α* = 3 corresponds to a double confidence interval of 0.13%.

In the *l*¹\-regularization case ([equation \[4.22\]](#c04.xhtml#equ4_22)), and if an outlier is detected (if the OD-test *H*[1] (*α*) is verified), then the value for *δ* ranges from 0 to 2![images](images/Inline_149_2.jpg)In practice, *δ* should be close to 0 and will never tend to its upper bound, which is very generous. As shown in [Figure 4.1](#c04.xhtml#fig4_1), the smaller is *δ* and the less regularized is the quadratic form, which allows for estimating potential extreme values. On the contrary, a high value of *δ* reduces the outlier value to zero, extending therefore the support of the underlying distribution. The OD step bypasses the tricky problem of choosing a convenient value for the regularization parameter.

In the *l*²\-regularization case, the estimated value for the outlier still depends on the chosen value for *δ*. The *l*²\-regularization is often preferred in the literature when closed-form expressions of \[4.23\] need to be derived (like in \[4.24\]) and to insure good mathematical properties such as a differentiable and continuous function. In this section, we are mainly interested in the *l*¹\-regularization because of the sparsity of the additive term *v*[*t*] that is supposed to represent spiky returns.

## **4.4.2.** ***rgKF performance***

To demonstrate why rgKF should be applied in any case, this section discusses the performance of the rgKF-*l*¹ and *l*² on simulated data intentionally corrupted by sparse outliers. The simulated data are similar to the data presented in \[3.51\], that is a two-factor model (including the S&P500 Equity Index and the T-Bond 10y) and piecewise constant parameters *w*[*t*] and (1 − *w*[*t*]). The difference is that we use the end-of-month returns of the two factors in this example (instead of daily data) to match the sampling frequency of the Fung and Hsieh factors and the hedge fund returns used in the next section. Spikes are then intentionally added to the observations and are generated according to a Bernoulli– Gaussian process occurring at five random instant times in the time series. When occurring, the spikes are sampled from a Gaussian density of variance 0.25, which is approximately 10 times higher than the average variance of the two factors (the average daily numbers of [Table 3.1](#c03.xhtml#tab3_1) times![images](images/Inline_150_2.jpg)– to get monthly equivalent numbers – compared to![images](images/Inline_150_3.jpg)give a ratio of around 10).

[Figure 4.2](#c04.xhtml#fig4_2) illustrates and compares the performance of the KF and the rgKF, when an NG(3)-test is applied followed by, respectively, an *l*²\-and an *l*¹\-regularization. We set *δ*[*l*2] = 0.5 and *δ*[*l*1] = 0.01. Left-hand side graphs are for the non-spiky data and the right-hand side graphs are for the spiky data. The results are obvious: KF delivers the most reliable estimates when no outlier is added and the rgKF-*l*¹ results are very close to the KF results. When outliers appear, KF fails to track the parameters whereas rgKF shows good performance. As expected, rgKF-*l*² will depend on the fixed value of *δ*: when *δ* is small, then a too large set of data is considered as outlier; when *δ* increases, outliers are not regularized and perturb the estimation of the parameters. In this case, *δ*[*l*2] = 0.5 seemed to be a good intermediate trade-off and we decided to show only one example for the sake of clarity. On its side, rgKF-*l*¹ does very well and is close to the KF results.

In conclusion, rgKF-*l*¹ should be a substitute for any other method in estimating the dynamic parameters of factor models. Generally, we do not have so much *a priori* information about the presence of outliers. KF already exhibits better tracking abilities than sliding window ordinary least squares (SW-OLS) but it will always lead to spurious results if at least one outlier or extreme event occurs. If the outliers are not filtered from the recursive equations, then what should be considered as specific events might be considered as systematic events, which is obviously misleading.

**[Figure 4.2.](#c04.xhtml#fig4-2)** *Performance of KF, rgKF-l*² *and rgKF-l*¹ *on synthetic monthly returns using a two-factor model (S&P500 and US TBond 10y) and piecewise constant parameters (see model* \[3.51\] *applied on monthly returns). On the right-hand side graphs, spikes are randomly added in the observations. rgKF-l*¹ *is therefore the most adapted algorithm*

![images](images/img_2_150.jpg)

# **4.5. Application to detect irregularities in hedge fund returns**

The goal of our example is to explain the importance of removing outliers using rgKF algorithms. A multi-factor decomposition of the returns helps us to understand which part of the returns comes from the market and which part is specific (as shown in [Table 4.2](#c04.xhtml#tab4_2)). If outliers appear in the observations and if the model does not take them into account, then market exposure estimates can be totally spurious. rgKF algorithms avoid the contamination of these estimates by simply filtering outliers. In practice, portfolio managers may use multi-factor approaches to hedge one specific or all market risks. Bad estimates can lead to some inappropriate decisions being made concerning the optimal hedging portfolio.

**[Table 4.2.](#c04.xhtml#tab4-2)** *Breakdown of asset returns and risks into systematic and idiosyncratic components.* Σ*[*f*] is the covariance matrix of the factors*

![images](images/img_5_151.jpg)

This section deals with applying rgKF(NG, *l*¹) on real hedge fund data to detect the potential occurrence of outliers. We conduct the analysis on returns of *Global macro* hedge funds. Managers of such funds take directional positions in currencies, debt, equities or commodities and may also elect to take relative positions combining long positions paired off against short positions. Hedge fund data come from the hedge fund research (HFR) database \[RES\]. The returns are end-of-month returns, available from January 1998 to June 2010 (i.e. for 150 months).

We choose the eight risk factors of Fung and Hsieh (F&H) \[HSI\], selected and constructed by the authors \[FUN 01\] to explain trend-follower hedge funds. These factors are now widely used in the literature of hedge fund analysis. They are quoted on a monthly basis and stored in f[*t*] at each end-of-month *t*. The reader may refer to section 2.2.3 for a more detailed description of these factors.

[Figure 4.3](#c04.xhtml#fig4_3) illustrates the capability of the rgKG(NG,*l*¹)to detect, estimate and filter some points in the observed returns time series, which might be considered as a hedge fund’s specific events, outliers, irregularities or illiquidity issues. As can be seen on the top graph in [Figure 4.3](#c04.xhtml#fig4_3), when an outlier occurs, then the resulting KF estimations of *β* suddenly jump to four or five times their previous values whereas no special event occurs in the market.

**[Figure 4.3.](#c04.xhtml#fig4-3)** *Outliers detection and estimation for a single trend-follower hedge funds of the database HFR (OSV Currency Fund). Impact of outliers on the fund’s exposures can be observed on the top graph: KF does not filter the rgKF(NG,l*¹ *) estimated spikes and gives incorrect estimations of the market risks (see color plate section)*

![images](images/img_4_152.jpg)

# **4.6. Conclusion**

This chapter has presented a new family of algorithms named rgKFs that have been derived to *detect and estimate* exogenous outliers that might occur in the observation equation of a standard KF. Inspired from the RKF of Mattingley and Boyd \[MAT 10\], which makes use of a *l*¹\-regularization step, we introduce a simple but efficient detection step in the recursive equations of the RKF. This solution is one means by which to solve the problem of adapting the value of the *l*¹\-regularization parameter: when an outlier is detected in the innovation term of the KF, the value of the regularization parameter is set to a value that will let the *l*¹\-based optimization problem estimate the amplitude of the spike. We have also tested an *l*²\-based regularization term for which the solution is known in a closed form.

The results obtained on synthetic data show that the best performance is achieved by the rgKF(NG,*l*¹) that handles the choice of the regularization parameter. In the context of analyzing hedge funds returns, the rgKF(NG,*l*¹) could help risk managers to dynamically and accurately estimate the exposures of hedge funds for which they do not have any other information except the observed returns. Interpreting outliers as illiquidity issues, our algorithms would therefore be very useful to classify funds according to their “illiquidity quality” and to make accurate decisions from a regulation point of view.

# **4.7. Chapter highlights**

#### ***Extended space-state model***

![images](images/img_6_153.jpg)

As for the classical KF state-space model,![images](images/Inline_155_2.jpg)and![images](images/Inline_155_3.jpg)Additional *v*[*t*] is a stochastic impulse process, for example a Bernoulli–Gaussian process.

#### ***Robust Kalman filter (RKF)***

The RKF algorithm consists of the following steps:

![images](images/img_6_154.jpg)

#### ***Regularized Kalman filter (rgKF)***

Our *rgKF* algorithm \[JAY 11b\] with exogenous outlier *detection and estimation* can be summarized in the following steps:

![images](images/img_9_154.jpg)

![images](images/img_1_155.jpg)

Outlier detection Non-Gaussian test:

![images](images/img_3_155.jpg)

Outlier estimation

![images](images/img_5_155.jpg)

![images](images/img_5_155a.jpg)

**Appendix**

**Some Probability Densities**

# **A1.1. Gaussian distribution**

## **A1.1.1.** ***Gaussian vector (with a multivariate Gaussian density)***

If an *N*\-dimensional random vector x is Gaussian distributed, then its probability density is fully characterized by its two first centered moments, its mean *μ* = IE\[x\] and its full-rank (invertible) covariance matrix ![images](images/Inline_157_6.jpg)whose expression is as follows:

\[A1.1\] ![images](images/img_7_156.jpg)

where |Σ| denotes the determinant of the covariance matrix Σ. It is usually denoted by ![images](images/Appendix_image001.gif).

## **A1.1.2.** ***White Gaussian vector with iso-variance components***

The vector x is said to be “white” if its *N* components *x*[*k*], 1 ≤ *k* ≤ *N* are independent. This implies that, ![images](images/Inline_158_2.jpg)Independent random variables are consequently uncorrelated, that is ![images](images/Inline_158_3.jpg)![images](images/Inline_158_4.jpg)If a random vector is Gaussian and white, with all its components sharing the same variance ![images](images/Inline_158_5.jpg)![images](images/Inline_158_6.jpg)then its covariance matrix is proportional to the *N* × *N* identity matrix,![images](images/Inline_158_7.jpg)and the form \[A1.1\] simplifies into:

[\[A1.2\]](#Appendix.xhtml#eqn2_1) ![images](images/img_8_157.jpg)

[Equation \[A1.2\]](#Appendix.xhtml#eqn2) displays a “parsimonious” Probability Density (in the sense of section 3.8.3) that depends only on *N* + 1 parameters, that is the *N* means, IE ![images](images/Inline_158_11.jpg)and the variance *σ*². Moreover, if x is zero mean, that is ![images](images/Inline_158_12.jpg)then *p*(x) depends solely upon the variance *σ*².

## **A1.1.3.** ***Gaussian random variable***

If *N* = 1, then \[A1.1\] becomes the Probability Density of a Gaussian random variable *x*, that is ![images](images/Inline_158_15.jpg), with:

\[A1.3\] ![images](images/img_16_157.jpg)

# **A1.2. *χ***² **distribution**

## **A1.2.1. *χ***² ***probability density***

A random variable *x* is **χ**²\-distributed with *ν* degree of freedom (or ![images](images/Inline_158_21.jpg)) if, and only if, its probability density function is given by, ![images](images/Inline_158_22.jpg)

\[A1.4\] ![images](images/img_23_157.jpg)

where Γ(**.**) is the gamma function defined for all complex number *z* by:

[\[A1.5\]](#Appendix.xhtml#eqn5_1) ![images](images/img_2_158.jpg)

In particular, we have IE(*x*) = *ν* and *V ar*(*x*) = 2*ν*.

## **A1.2.2.** ***A*** **χ**² ***variable is the sum of squared i.i.d. Gaussian variables***

If we consider *N* i.i.d. Gaussian random variables *x*[*i*], with mean *μ*[*i*] and variance *σ*[*i*], for *i* = 1, …*, N*, then:

\[A1.6\] ![images](images/img_7_158.jpg)

Following the central limit theorem, as soon as *N* is large (*N* > 100), the distribution of the random variable *y* may be approximated by a Gaussian distribution with mean *N* and variance 2 *N*.

# **A1.3. Student’s** **t****\-distribution**

## **A1.3.1.** ***Student’s t-probability density***

The Student’s *t*\-distribution of a random variable *t* is characterized by a single parameter *ν* ≥ 0 and is given by:

\[A1.7\] ![images](images/img_13_158.jpg)

It is usually denoted as *t* ∼ *t*(*ν*). In particular, we have IE(*t*) = 0 for *ν* > 1, IE(*t*) undefined for *ν* = 1 and ![images](images/Inline_159_16.jpg)infinite for *ν* ≤ 2. The function Γ(**.**) is given in [equation \[A1.5\]](#Appendix.xhtml#eqn5).

## **A1.3.2.** ***A Student’s t variable is the ratio between a Gaussian-distributed variable and a*** **χ**²***\-distributed variable***

![images](images/Inline_160_3.jpg)

\[A1.8\] ![images](images/img_4_159.jpg)

## **A1.3.3.** ***Confidence interval of the estimate of the mean of a Gaussian random variable with unknown variance***

The confidence interval at *α*\-confidence level for ![images](images/Inline_160_8.jpg)an estimate of the mean value *μ* of *x* (see \[A1.3\] with *σ*² unknown and estimated by *s*²), is given by:

\[A1.9\] ![images](images/img_9_159.jpg)

where ![images](images/Inline_160_12.jpg)is the ![images](images/Inline_160_13.jpg)quantile of the Student’s *t* variable *t*(*N* − 1).

# **A1.4. Fisher (or Fisher–Snedecor or Snedecor’s** ***F*****) distribution**

## **A1.4.1.** ***The Fisher (or Fisher–Snedecor, or Snedecor’s F) probability density***

This probability density *F* (*p, q*) is given, ![images](images/Inline_160_17.jpg)and *p, q* ∈ IN^∗, by:

\[A1.10\] ![images](images/img_18_159.jpg)

where ![images](images/B.gif)(*a, b*) is the beta function defined by:

\[A1.11\] ![images](images/img_2_160.jpg)

In particular, we have ![images](images/Inline_161_5.jpg)for *ν*[[2]] > 2, and ![images](images/Inline_161_6.jpg)

## **A1.4.2.** ***A Fisher variable is the ratio between two*** **χ**² ***variables***

![images](images/Inline_161_9.jpg)

\[A1.12\] ![images](images/img_10_160.jpg)

## **A1.4.3.** ***The inverse of a Fisher variable is a Fisher variable***

![images](images/Inline_161_14.jpg)

## **A1.4.4.** ***A squared Fisher variable may be a Student’s-t variable***

![images](images/Inline_161_17.jpg)

## **A1.4.5.** ***A squared Fisher variable may be a Gaussian variable***

![images](images/Inline_161_20.jpg)

# **A1.5. Hotelling’s** *t***\-squared distribution**

The Hotelling’s *t* -squared probability density with parameters *p* and *q* and denoted by ![images](images/Inline_162_3.jpg)is related to the Fisher probability density \[A1.10\] as follows: if ![images](images/Inline_162_4.jpg)then ![images](images/Inline_162_5.jpg)

# **A1.6. Wishart distribution**

The Wishart distribution denoted by ![images](images/w.gif)(*K*, A) is the distribution of:

\[A1.13\] ![images](images/img_8_161.jpg)

where the z[*k*]s are independent, identically distributed (i.i.d.) according to a Gaussian distribution with zero mean and covariance A.

# **A1.7. Marčenko–Pastur distribution**

Suppose that we use the sample covariance matrix computed on the standardized matrix of returns ![images](images/R.bar.gif)as described in [equation \[2.4\]](#c02.xhtml#eqn4). The resulting estimated covariance matrix S therefore has random elements with an assumed variance *σ*². Then, in the limit *T, N* → ∞, keeping the ratio *q* = *T*/*N* ≥ 1 constant, the density of the eigenvalues of S is given by:

\[A1.14\] ![images](images/img_13_161.jpg)

where the maximum and the minimum eigenvalues are given by:

\[A1.15\] ![images](images/img_2_162.jpg)

and ![images](images/Inline_163_5.jpg). The density *ρ*(**λ**) is known as the Marčenko–Pastur density \[MAR 67, PAS 11\].

# **A1.8. Bernoulli–Gaussian distribution**

A Bernouilli–Gaussian process x is such that given a set *S* of indices drawn from a set *I* = {1, …*, N*} with a probability *p* ![images](images/less.gif)1, each element of x is identically zero if the corresponding index is not in the set *S*, otherwise the element is Gaussian with mean *μ* and non-zero variance *σ*². Elements of x are i.i.d. given the support set.

The probability that the cardinality of the support set *S* equals *K* is given by ![images](images/Inline_163_9.jpg). If x[*S*] denotes the vector consisting of the elements of x whose indices are in the set *S*, then the vector x[*S*] follows i.i.d. Gaussian distribution, that is ![images](images/Inline_163_10.jpg). Thus, *S* is the support set of the signal vector x with expected cardinality ![images](images/Appendix_image002.gif)and x is sparse with high probability.

# Conclusion

As mentioned in the introduction, our objective in this book is to adapt the QUANT(ITATIVE) tools to the new financial world characterized by noisy data, enhanced risk controls and an increasing demand for more transparency. Throughout this book, the classic linear factor model is our benchmark to prove how the statistical signal processing (SSP) techniques can help in solving this task. Keeping a “user friendly” framework that gives an intuitive explanation of most of the stylized facts empirically observed, we show that more complex phenomena, such as nonlinearities or liquidity issues, can be taken into account to obtain robust results.

Of course, this robust treatment has a cost in terms of complexity. Kalman filter estimators must replace least squares estimators; regularization techniques have to be implemented to treat the noisy impact of illiquidity on asset returns. But SSP gives us a proven technical framework, which is easy to adapt in our context. We have shown in the different chapters how factor selection and parameter estimation can be done to get these robust results that we are targeting.

Most of our empirical illustrations come from the asset management industry, and in particular the hedge fund industry. Linear factor models and style analysis could in theory give a good answer, as is the case for mutual funds. However, hedge fund returns, and their particularities, nonlinearity in particular, encourages us to adapt the basic linear setup by considering either nonlinear factors or time-varying linear exposures to risk factors. The first approach has a main drawback. By introducing nonlinearities in the model, we answer to the demand for transparency by using tools that cannot be considered as “usual practices” in the industry. The second approach gives a more “user friendly” solution as it corresponds to an intuitive extension of the current practices.

# Bibliography

\[AGA 00a\] AGARWAL V., NAIK N., “Multi-period performance persistence analysis of hedge funds”, *Journal of Financial and Quantitative Analysis*, vol. 35, no. 3, pp. 327–342, September 2000.

\[AGA 00b\] AGARWAL V., NAIK N., “On taking the alternative route: risks, rewards and performance persistence of hedge funds”, *Journal of Alternative Investments*, vol. 2, no. 4, pp. 6–23, 2000.

\[AGA 04\] AGARWAL V., NAIK N., “Risks and portfolio decisions involving hedge funds”, *Review of Financial Studies*, vol. 17, no. 1, pp. 63–98, 2004.

\[AGA 09\] AGARWAL V., BAKSHI G.S., HUIJ J., “Do higher-moment equity risks explain hedge fund returns?”, *1st Annual Conference on Econometrics of Hedge Funds*, Research Paper No. RHS 06066, R. H. Smith School, 2009.

\[AHN 09\] AHN S.C., HORENSTEIN A.R., Eigenvalue ratio test for the number of factors, Mimeo, Arizona State University, 2009.

\[AKA 74\] AKAIKE H., “A new look at the statistical model identification”, *IEEE Transaction on Automatic and Control*, vol. 19, no. 6, pp. 716–723, June 1974.

\[AMM 10\] AMMANN M., HUBER R.O., SCHMID M.M., “Benchmarking hedge funds: the choice of the factor model”, August 2011.

\[AND 63\] ANDERSON T.W., “Asymptotic theory for principal component analysis”, *Annals of Mathematics and Statistics*, vol. 34, pp. 122–148, February 1963.

\[AND 97\] ANDRIEU C., DOUCET A., DUVAUT P., “Bayesian estimation of filtered point processes using Markov chain Monte Carlo methods”, *31st Asilomar Conference on Signals, Systems & Computers*, vol. 2, pp. 1097–1100, November 1997.

\[BAI 02\] BAI J., NG S., “Determining the number of factors in approximate factor models”, *Econometrica*, vol. 70, no. 1, pp. 191– 221, 2002.

\[BAI 10\] BAI Z., SILVERSTEIN J.W., *Spectral Analysis of Large Dimensional Random Matrices*, 2nd. ed., Springer, 2010.

\[BAR 93\] BAR\-SHALOM Y., LI X.R., *Estimation and Tracking: Principles, Techniques, and Software*, Artech House, 1993.

\[BIL 12\] BILLIO M., GETMANSKY M., PELIZZON L., “Dynamic risk exposure in hedge funds”, *Computational Statistics and Data Analysis*, vol. 56, pp. 3517–3532, 2012.

\[BIL 99\] BILODEAU M., BRENNER D., *Theory of Multivariate Statistics*, Springer, 1999.

\[BLA 72\] BLACK F., “Capital market equilibrium with restricted borrowing”, *Journal of Business*, vol. 45, no. 3, pp. 444–455, 1972.

\[BOL 09\] BOLLEN N.P.B., WHALEY R.E., “Hedge fund risk dynamics: implications for performance appraisal”, *Journal of Finance*, vol. 64, no. 2, pp. 987–1037, 2009.

\[BRO 08\] BRODIE J., DAUBECHIES I., MOL C.D., *et al*., Sparse and stable markowitz portfolios, European Central Bank working paper no. 936, September 2008.

\[BUR 09\] BURASCHI A., KOSOWKI R., TROJANI F., “When there is no place to hide: correlation risk and the cross-section of hedge fund returns”, *1st Annual Conference on Econometrics of Hedge Funds*, Imperial College working paper, 2009.

\[BUR 03\] BURMEISTER E., ROLL R., ROSS S.A., Using macroeconomic factors to control portfolio risk, Working paper, BIRR Portfolio Analysis, Inc., 2003.

\[CAM 97\] CAMPBELL J., LO A.W., MACKINLAY A.C., *The Econometrics of Financial Markets*, Princeton University Press, 1997.

\[CAR 97\] CARHART M.M., “On persistence in mutual fund performance”, *The Journal of Finance*, vol. 52, no. 1, pp. 57–82, March 1997.

\[CAT 66\] CATTELL R.B., “The scree test for the number of factors”, *Multivariate Behavioral Research*, vol. 1, pp. 245–276, 1966.

\[CAU 02\] CAUCHIE S., HOESLI M., ISAKOV D., The determinants of stock returns: an analysis of industrial sector indices, Report, HEC-University of Geneva, 2002.

\[CHA 83\] CHAMBERLAIN G., ROTHSCHILD M., “Arbitrage, factor structure and mean-variance analysis on large asset markets”, *Econometrica*, vol. 51, no. 5, pp. 1281–1304, 1983.

\[CHA 98\] CHAN K.C., KARCESKI J., LAKONISHOK J., “The risk and return from factors”, *Journal of Financial and Quantitative Analysis*, vol. 33, no. 2, pp. 159–188, 1998.

\[CHE 86\] CHEN N.F., ROLL R., ROSS S.A., “Economic forces and the stock market”, *Journal of Business*, vol. 59, no. 3, pp. 383–403, 1986.

\[CHE 93\] CHEN S.J., JORDAN B.D., “Some empirical tests in the arbitrage pricing theory: macrovariables vs. derived factors”, *Journal of Banking and Finance*, vol. 17, no. 1, pp. 65–89, 1993.

\[CON 95\] CONNOR G., “The three types of factor models: a comparison of their explanatory power”, *Financial Analysts Journal*, pp. 42–46, May/June 1995.

\[CON 02\] CONTE E., MAIO A.D., RICCI G., “Recursive estimation of the covariance matrix of a compound-Gaussian process and its application to adaptive CFAR detection”, *IEEE Transactions of Signal Processing*, vol. 50, no. 8, pp. 1908–1915, August 2002.

\[CRA 46\] CRAMER H., *Mathematical Methods of Statistics*, Princeton University Press, 1946.

\[CRA 79\] CRAVEN P., WAHBA G., “Smoothing noisy data with spline functions”, *Numerische Mathematik*, vol. 31, pp. 377–403, 1979.

\[CRI 10\] CRITON, G., SCAILLET O., “Time-varying analysis in risk and hedge fund performance: how forecast ability increases estimated alpha”, 2010.

\[CRO 05\] CROWLEY P.M., LEE J., “Decomposing the co-movement of the business cycle: a time-frequency analysis of growth cycles in the euro zone”, *Macroeconomics 0503015*, EconWPA, pp. 1075– 1080, 2005.

\[DAR 10\] DAROLLES S., GOURIÉROUX C., “Conditional fitted Sharpe performance with application to hedge fund rating”, *Journal of Banking and Finance*, vol. 34, no. 3, pp. 578–593, 2010.

\[DAR 11\] DAROLLES S., MERO G., “Hedge fund returns and factor models: a cross section approach”, *Bankers, Markets and Investors*, vol. May–June, no. 112, pp. 34–53, 2011.

\[DAR 12\] DAROLLES S., VAISSIÉ M., “The alpha and omega of fund of hedge fund added value”, *Journal of Banking and Finance*, vol. 36, no. 4, pp. 1067–1078, April 2012.

\[DEM 09\] DEMIGUEL V., GARLAPPI L., NOGALES F.J., *et al.*, “A generalized approach to portfolio optimization: improving performance by constraining portfolio norms”, *Management Science*, vol. 55, no. 5, pp. 798–812, May 2009.

\[DJU 03\] DJURIĆ P.M., KOTECHA J.H., ZHANG J., *et al*., “Particle filtering”, *IEEE Signal Processing Magazine*, vol. 20, pp. 19–38, September 2003.

\[DRA 09\] DRAKAKIS K., “Application of signal processing to the analysis of financial data”, *IEEE Signal Processing Magazine*, vol. 26, no. 5, pp. 156–160, September 2009.

\[DUV 94\] DUVAUT P., *Traitement du Signal, Concepts et Applications*, Hermes Science, 1994.

\[ELD 05\] ELDERMAN A., RAO N.R., “Random matrix theory”, *Acta Numerica*, vol. 14, pp. 233–297, 2005.

\[FAM 73\] FAMA E.F., MACBETH J., “Risk, return and equilibrium: empirical tests”, *Journal of Political Economy*, vol. 81, pp. 607– 636, 1973.

\[FAM 92\] FAMA E.F., FRENCH K.R., “The cross-section of expected stock returns”, *Journal of Finance*, vol. 47, no. 2, June 1992.

\[FAM 93\] FAMA E.F., FRENCH K.R., “Common risk factors in the returns on stocks and bonds”, *Journal of Financial Economics*, vol. 33, no. 1, pp. 3–56, 1993.

\[FOR 10\] FORBES C., EVANS M., HASTINGS N., *Statistical Distributions*, 4th ed., John Wiley & Sons, 2010.

\[FOX 72\] FOX A.J., “Outliers in time series”, *Journal of the Royal Statistical Society*, *Series B*, vol. 34, pp. 350–363, 1972.

\[FRA 04\] FRAHM G., Generalized elliptical distributions: theory and applications, PhD Thesis, University of Koln, July 2004.

\[FRE 03\] FRENCH C.W., “The Treynor capital asset pricing model”, *Journal of Investment Management*, vol. 1, no. 2, pp. 60–72, 2003.

\[FUK 90\] FUKUNAGA K., *Introduction to Statistical Pattern Recognition*, 2nd ed., Academic Press, 1990.

\[FUN 01\] FUNG W., HSIEH D., “The risk in hedge fund strategies, theory and evidence from trend followers”, *Review of Financial Studies*, vol. 14, no. 2, pp. 313–341, 2001.

\[GEN 05\] GENÇAY R., SELÇUK F., WHITCHER B., “The risk in hedge fund strategies, theory and evidence from trend followers”, *Journal of International Money and Finance*, vol. 24, pp. 55–70, 2005.

\[GIN 02\] GINI F., GRECO M.V., “Covariance matrix estimation for CFAR detection in correlated heavy tailed clutter”, *Signal Processing*, vol. 82, no. 12, pp. 1847–1859, December 2002.

\[HAM 94\] HAMILTON J.D., *Time Series Analysis*, Princeton University Press, 1994.

\[HAR 07\] HARDING M.C., Essays in econometrics and random matrix theory, PhD Thesis, Massachusetts Institute of Technology, May 2007.

\[HAR 09\] HARVEY A., KOOPMAN S.J., “Unobserved components models in economics and finance”, *IEEE Control Systems Magazine*, vol. 29, no. 6, pp. 71–81, December 2009.

\[HOT 31\] HOTELLING H., “The generalization of Student’s ratio”, *Annals of Mathematical Statistics*, vol. 2, no. 3, pp. 360–378, 1931.

\[HSI\] HSIEH D. A., “Data library webpage: hedge fund risk factors”. Available at [http://faculty.fuqua.duke.edu/%7Edah7/HFRFData.htm](http://faculty.fuqua.duke.edu/%7Edah7/HFRFData.htm).

\[HUB 64\] HUBER P.J., “Robust estimation of a location parameter”, *The Annals of Mathematical Statistics*, vol. 35, no. 1, pp. 73–101, 1964.

\[HUB 67\] HUBER P.J., “The behavior of maximum likelihood estimates under nonstandard conditions”, *5th Berkeley Symposium on Mathematical Statistics and Probability*, vol. 1, pp. 221–233, 1967.

\[HUB 77\] HUBER P.J., *Robust Covariances in Statistical Decision Theory and Related Topics*, Academic Press Inc., New York, 1977.

\[JAG 03\] JAGANNATHAN R., MA T., “Risk reduction in large portfolios: why imposing the wrong constraints helps”, *Journal of Finance*, vol. 58, no. 4, pp. 1651–1684, 2003.

\[JAY 03\] JAY E., Détection en environnement non-Gaussien, application à la détection radar, PhD Thesis, University of Cergy-Pontoise/ONERA, June 2003.

\[JAY 11a\] JAY E., DUVAUT P., DAROLLES S., *et al.*, “Multi-factor models: examining the potential of signal processing techniques”, *IEEE Signal Processing Magazine*, vol. 28, no. 5, pp. 37–48, September 2011.

\[JAY 11b\] JAY E., DUVAUT P., DAROLLES S., *et al*., “Lq-regularization of the Kalman filter for exogenous outlier removal: application to hedge funds analysis”, *4th International Workshop on Computational Advances in Multi-Sensor Adaptive Processing (CAMSAP)*, IEEE Signal Processing Society, December 2011.

\[KAL 89\] KALABA R., TESFATSION L., “Time-varying linear regression via flexible least squares”, *Computers and Maths with Applications*, vol. 17, no. 8–9, pp. 1215–1245, 1989.

\[KAY 93\] KAY S.M., *Fundamentals of Statistical Signal Processing*, *Volume I: Estimation Theory*, Prentice Hall, 1993.

\[KAY 98\] KAY S.M., *Fundamentals of Statistical Signal Processing*, *Volume 2: Detection Theory*, Prentice Hall, 1998.

\[KEN 01\] KENT D.D., HIRSHLEIFER D., SUBRAHMANYAM A., “Overconfidence, arbitrage, and equilibrium asset pricing”, *Journal of Finance*, vol. LVI, no. 3, pp. 921–965, June 2001.

\[LIN 65\] LINTNER J., “The valuation of risk assets and selection of risky investments in stock portfolios and capital budgets”, *Review of Economics and Statistics*, vol. 47, no. 1, pp. 13–37, 1965.

\[MAL 73\] MALLOWS C.L., “Some comments on Cp”, *Technometrics*, vol. 15, pp. 661–675, 1973.

\[MAR 67\] MARČENKO V.A., PASTUR L.A., “Distribution of eigenvalues for some sets of random matrices”, *Mathematics of the USSR Sbornik*, vol. 1, no. 4, pp. 457–483, 1967.

\[MAR 52\] MARKOWITZ H.M., “Portfolio selection”, *Journal of Finance*, vol. 7, no. 1, pp. 77–91, 1952.

\[MAR 04\] MARKOV M., MOTTL V., MUCHNIK I., Principles of nonstationary regression estimation: a new approach to dynamic multi-factor models in finance, Technical Report number 2004-47, DIMACS, Rutgers University, Piscataway, NJ, October 2004.

\[MAR 76\] MARONNA R.A., “Robust M-estimators of multivariate location and scatter”, *Annals of Statistics*, vol. 4, no. 1, pp. 51– 67, 1976.

\[MAR 06\] MARONNA R.A., MARTIN R.D., YOHAI V.J., *Robust Statistics, Theory and Methods*, John Wiley & Sons, 2006.

\[MAT 10\] MATTINGLEY J., BOYD S., “Real-time convex optimization in signal processing”, *IEEE Signal Processing Magazine*, vol. 27, no. 3, pp. 50–61, May 2010.

\[MOS 66\] MOSSIN J., “Equilibrium in a capital market”, *Econometrica*, vol. 34, no. 4, pp. 768–783, 1966.

\[NOR 04\] NORMAN S., *Control System Engineering*, John Wiley & Sons, 2004.

\[ONA 06\] ONATSKI A., Determining the number of factors from empirical distribution of eigenvalues, Working paper, Columbia University, 2006.

\[OSB 00\] OSBORNE M.R., PRESNELL B., TURLACH B.A., “On the LASSO and its dual”, *Journal of Computational and Graphical Statistics*, vol. 9, no. 2, pp. 319–337, June 2000.

\[PAN 11\] PANAHI A., VIBERG M., “Maximum a posteriori based regularization parameter selection”, *Proceedings of the IEEE International Conference on Acoustics, Speech, and Signal Processing* (*ICASSP 2011*), IEEE, pp. 2452–2455, May 2011.

\[PAS 05\] PASCAL F., FORSTER P., OVARLEZ J.P., *et al*., “Theoretical analysis of an improved covariance matrix estimator in Non-Gaussian noise: existence and algorithm analysis”, *30th International Conference on Acoustics, Speech and Signal Processing (ICASSP’ 05)*, vol. IV, Philadelphia, PA, pp. 69–72, March 2005.

\[PAS 06\] PASCAL F., Détection et estimation en environnement non-Gaussien, PhD Thesis, University of Nanterre/ONERA, December 2006.

\[PAS 08\] PASCAL F., CHITOUR Y., OVARLEZ J.P., *et al*., “Covariance structure maximum-likelihood estimates in compound Gaussian noise: existence and algorithm analysis”, *IEEE Transactions of Signal Processing*, vol. 56, pp. 34–48, January 2008.

\[PAS 11\] PASTUR L., SHCHERBINA M., *Eigenvalue Distribution of Large Random Matrices*, AMS, 2011.

\[PAT 13\] PATTON A.J., RAMADORAI T., “On the high-frequency dynamics of hedge fund risk exposures”, *Journal of Finance*, vol. 68, no. 2, April 2013.

\[POT 05\] POTTERS M., BOUCHAUD J.P., “Financial applications of random matrix theory: old laces and new pieces”, *Acta Physica Polonica B*, vol. 36, no. 9, pp. 2767–2784, 2005.

\[RAC 10\] RACICOT F.E., “Modeling hedge funds returns using the Kalman filter: an errors-in-variables perspective”, *Atlantic Economic Journal*, vol. 38, no. 3, pp. 377–378, September 2010.

\[RES\] Hedge Funds Research (HFR), “HFR databases”. Available at [http://www.hedgefundresearch.com/](http://www.hedgefundresearch.com/).

\[RIS 78\] RISSANEN J., “Modeling by shortest data description”, *Automatica*, vol. 14, pp. 465–471, 1978.

\[ROL 77\] ROLL R., “A critique of the asset pricing theory’s tests part I: on past and potential testability of the theory”, *Journal of Financial Economics*, vol. 4, no. 2, pp. 129–176, 1977.

\[ROL 80\] ROLL R., ROSS S.A., “An empirical investigation of the arbitrage pricing theory”, *Journal of Finance*, vol. 35, no. 5, pp. 1073–1103, 1980.

\[RON 08a\] RONCALLI T., TEILETCHE J., “An alternative approach to alternative Beta”, *Journal of Financial Transformation*, vol. 24, pp. 43–52, 2008.

\[RON 08b\] RONCALLI T., WEISANG G., “Tracking problems, hedge fund replication and alternative beta”, 2008. Available at [http://www. guillaume-weisang.com/Assets/Download/Roncalli \_Weisang\_HFR-PF-20081224.pdf](http://www.%20guillaume-weisang.com/Assets/Download/Roncalli%20_Weisang_HFR-PF-20081224.pdf).

\[ROS 76\] ROSS S.A., “The arbitrage theory of capital asset pricing”, *Journal of Finance*, vol. 13, no. 3, pp. 341–360, 1976.

\[RUC 10\] RUCKDESCHEL P., “Optimally robust Kalman filtering”, *Berichte des Fraunhofer ITWM*, number 185, Fraunhofer, ITWM, May 2010.

\[SAD 10\] SADKA R., “Liquidity risk and the cross-section of hedge-fund returns”, *Journal of Financial Economics*, vol. 98, pp. 54–71, October 2010.

\[SCH 05\] SCHMIDT M., Least squares optimization with L1-norm regularization, Project Report number CS542B, UBC, University of Alberta, Canada, December 2005.

\[SHA 64\] SHARPE W.F., “Capital asset prices: a theory of market equilibrium under conditions of risk”, *Journal of Finance*, vol. 19, no. 3, pp. 425–442, 1964.

\[SHA 92\] SHARPE W.F., “Asset allocation: management style and performance measurement”, *Journal of Portfolio Management*, vol. 18, no. 2, pp. 7–19, 1992.

\[STO 89\] STOICA P., NEHORAI A., “MUSIC, maximum likelihood, and Cramer-Rao bound”, *IEEE Transactions on Acoustics, Speech, and Signal Processing*, vol. 37, no. 5, pp. 720–741, 1989.

\[STO 97\] STOICA P., MOSES R., *Introduction to Spectral Analysis*, Prentice Hall, 1997.

\[TIB 96\] TIBSHIRANI R., “Regression shrinkage and selection via the LASSO”, *Journal of the Royal Statistical Society, Series B*, vol. 58, pp. 267–288, 1996.

\[TRE 62\] TREYNOR J.L., “Toward a theory of market value of risky assets”, Unpublished manuscript. A final version was published in 1999, in KORAJCZYK R.A., *Asset Pricing and Portfolio Performance: Models, Strategy and Performance Metrics*,Risk Books, (ed.) London, pp. 15–22, 1962.

\[TRE 02\] TREES H.L.V., *Optimum Array Processing, Part IV of Detection, Estimation and Modulation Theory*, John Wiley & Sons, 2002.

\[TUK 60\] TUKEY J.W., “A survey of sampling from contaminated distributions”, *Contributions to Probability ans Statistics, Olkin and Others, Stanford University Press*, pp. 448–485, 1960.

\[TUK 62\] TUKEY J.W., “The future of data analysis”, *The Annals of Mathematical Statistics*, vol. 33, no. 1, pp. 1–67, 1962.

\[TYL 83\] TYLER D.E., “Robustness and efficiency properties of scatter matrices”, *Biometrika*, vol. 70, pp. 411–420, 1983.

\[TYL 87a\] TYLER D.E., “A distribution-free M-estimator of multivariate scatter”, *The Annals of Statistics*, vol. 15, pp. 234– 251, 1987.

\[TYL 87b\] TYLER D.E., “Statistical analysis for the angular central Gaussian distribution on the sphere”, *Biometrika*, vol. 74, pp. 579–589, 1987.

Index

**A**

Akaike information criteria (AIC)

Alpha

Anderson’s sufficient statistic

Arbitrage pricing theory (APT)

Arbitrage

Asset-specific risk, *see* Idiosyncratic risk

**B**

Bernoulli–Gaussian process

Beta

Beta risk, *see* Systematic risk

Book-to-market ratio

**C**

Capital Asset Pricing model (CAPM)

Carhart’s four-factor model

Chen, Roll and Ross model

Covariance

Covariance matrix estimation

Empirical Covariance Matrix Fixed-point (FP) estimator Huber’s *M*\-estimator *M*\-estimators Robust methods Sample Covariance Matrix (SCM) 

Cramér–Rao lower bound

**D**

Diversifiable risk, *see* Idiosyncratic risk

Diversification

**E**

Efficiency, *see* Market efficiency

Eigen-decomposition

Eigenfactor

Eigenfactor selection

Eigenvalue distribution Test

Eigenvalues density

Empirical *ad hoc* approach

Empirical matrix estimation

Equilibrium, *see* Market equilibrium

Equity index

Excess return

Expected excess return, *see* Risk premium

Expected return

Exposure

Alpha Beta Sensitivity 

Extended state space model

**F**

Factor

Factor analysis (FA)

Factor model

APT

CAPM

Carhart’s four-factor model

Chen, Roll and Ross model

Empirical *ad hoc* approach

Fama and French model

Fung and Hsieh model

Multi-Factor model

Sharpe’s Market model

Factor representation

Factor selection

Empirical *ad hoc* approach

Statistical approach

Stepwise regression

Fama and French factor HML

Sharpe’s market model

SMB

Fama and French model

Fixed-Point (FP) estimator

Fund of hedge funds

Fung and Hsieh factor

Bond10y

CreditSpread

EquitySizeSpread

MXEF

PTFSBD

PTFSCOM

PTFSFX

SP500

Fung and Hsieh model

**G**

Gaussian

Random variable

Vector

Probability density

White Gaussian vector

**H**

Hedge Funds

Hotelling’s T-squared statistics

Huber’s *M*\-estimator

**I**

IC[*p*]

Idiosyncratic risk

Information criteria

Akaike information criteria (AIC)

Minimum description length (MDL)

Innovation

Innovation property

Inversion lemma, *see* Matrix

**K**

Kalman Filter (KF)

Correction accuracy processing

Correction filtering

Correction update

Innovation

Innovation property

Kalman gain

Markovian property

Measurement equation

Prediction accuracy processing

Prediction filtering

Regularized Kalman Filter(rgKF)

Robust Kalman Filter(RKF)

State equation

State-space model

Kalman gain

**L**

l¹\-regularization

l²\-regularization

Large panel data

Large panel data criteria

LASSO

Least squares estimation (LSE)

Linear factor model, *see* Factor model

**M**

*M*\-estimators

Fixed-Point (FP) estimator

Huber’s *M*\-estimator

Market

Capitalization

Efficiency

Equilibrium

Portfolio

Market risk, *see* Systematic risk

Market risk premium

Markowitz’s theory

Marčenko–Pastur density

Matrix

Random

Vandermonde

Maximum likelihood estimation (MLE)

Mean square error (MSE)

Mean-variance efficiency

Minimum description length (MDL)

Model order choice

*IC*[*p*]

*PC*[*p*]

Akaike information criteria (AIC)

Anderson’s sufficient statistic

Large panel data criteria

Minimum description length (MDL)

Random matrix theory (RMT)

Multi-factor model

MUSIC algorithm

**N, O**

Net asset value (NAV)

Non-diversifiable risk, *see* Systematic risk

Optimal portfolio allocation

Outlier detection (OD)

Outlier estimation

**P**

Parameter estimation

Least squares estimation (LSE)

Sliding window OLS (SW-OLS)

PC[p]

Portfolio

Market portfolio

Tradable portfolio

Zero-cost portfolio

Portfolio allocation

Portfolio diversification

Portfolio management theory

Portfolio returns

Markowitz’s theory

Mean-variance efficiency

Principal Component Analysis (PCA)

Asymptotic principal components

Probability density

χ² distribution

Bernoulli-Gaussian process

Eigenvalues density

Fisher–Snedecor (or Snedecor’s-*F*) distribution

Gaussian distribution

Hotelling’s *T*\-squared statistics

Marčenko–Pastur distribution

Marcenko–Pastur density

Multi-variate Gaussian distribution

Snedecor’s-F (or Fisher-Snedecor) distribution

Student’s-t statistics

Wishart distribution

**R**

Random matrix theory (RMT)

Recursive equations, *see*

Kalman filter

Regression

Regularized Regularization parameter

Regularized Kalman Filter (rgKF)

Correction

Innovation

l¹\-regularization

l²\-regularization

Mean correction

Mean prediction

Outlier detection (OD)

Outlier estimation

Variance correction

Variance prediction

Return

Return-based style analysis

Style analysis

Risk

Idiosyncratic

Specific

Systematic

Risk premium

Risk-free rate

Risky asset

Robust covariance estimation

Fixed-point (FP) estimator

Huber’s *M*\-estimator

*M*\-estimators

Robust Kalman Filter (RKF)

Robust methods

**S**

Sample covariance matrix

(SCM) Sample mean

Security market line (SML)

Sensitivity

Sharpe ratio

Sharpe’s market model

Sliding window OLS (SW-OLS)

Small cap stocks

Snedecor’s-F distribution

Sparsity

Specific risk

State-space model

Stepwise regression

Student’s-t statistics

Style analysis

Subspace methods

MUSIC algorithm

Principal Component

Analysis (PCA) Systematic risk

**T**

Tactical portfolio allocation

Transparency

**V**

Value stocks

Vandermonde matrix

Variance Volatility

Variance Volatility

**W**

White Gaussian vector

Wishart distribution

**[Figure 2.2](#c02.xhtml#fig2_1).**

![image](images/img_2_182.jpg)

**[Figure 2.5](#c02.xhtml#fig5_1).**

![image](images/img_4_182.jpg)

**[Figure 3.6](#c03.xhtml#Fig6).**

![image](images/img_2_183.jpg)

**[Figure 3.12](#c03.xhtml#Fig12).**

![image](images/img_4_183.jpg)

**[Figure 3.13](#c03.xhtml#Fig13).**

![image](images/img_2_184.jpg)

**[Figure 3.14](#c03.xhtml#Fig14).**

![image](images/img_4_184.jpg)

**[Figure 3.15](#c03.xhtml#Fig15).**

![image](images/img_2_185.jpg)

**[Figure 4.3](#c04.xhtml#fig4_3).**

![image](images/img_4_185.jpg)