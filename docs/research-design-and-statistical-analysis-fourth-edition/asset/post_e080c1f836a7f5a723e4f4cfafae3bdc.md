
# Integrated Analysis III 433

16.4 a) Discuss the pros and cons of the designs in Exercises 16.2 and 16.3.

b) What effects would change the correlation (ρ) and the degrees-of-freedom adjustment (e) have on the power of the tests of targets and context in each design?

16.5 Sixteen participants read 15 short tests. Although all participants were fluent in English, each had learned it as a second language (Group = 1; native speaker or bilingual). Each text contained an ambiguous word whose meaning was made clear by a short disambiguating region of text following the word. Time looking at the disambiguating region was preceded by its meaning (A = 1); in five, the contexts were neutral (A = 2); and in the remaining five tests (A = 3), the contexts implied the wrong interpretation. Data are at the book's website in the file EX16_5. Perform the ANOVA and discuss the results.

16.6 In studies as described in Exercise 16.6, scores are often missing and researchers calculate minF to test hypotheses. The files EX16_68 and EX16_61 of the book's website were constructed by randomly deleting a small number of scores from the EX_15_files. In the EX16_65 file were calculated by averaging the remaining item scores in each level of A for each participant. The numbers in the EX16_61 file were calculated by averaging the scores in each level of C for each item. Calculate the minF and its degrees of freedom for the test of the A effect. Box 14.2 provides an example of the calculations.

16.7 Twenty participants were presented with a series of four flight simulations and their response times were recorded. The sequence of tests (A) balanced over four blocks of time (B). The data are on the website in the EX16_7 file.
a) Ignoring block and group variability, we can treat the design as a simple 20 participants by four levels of A design. The source of variance, df, sums of squares, mean squares, F ratios, and p-values, assuming this is the design.
b) Reanalyze the data taking its Latin square properties into consideration. What is the relationship between the two sets of sums of squares in the analyses in part (a) and (b)?
c) What changes, if any, would there be in the analysis if B is assumed to have random effects?

16.8 The experiment described in Exercise 16.7 was replicated, but this time there were 24 participants, under 60 years old (Age = 1) and more than 60 years old (Age = 2). The data are in the file EX16_8; Group refers to the order of the situations, A refers to the situation, and B refers to the position in time. Perform the ANOVA and discuss the results.

# Notes

+ 1 We do not recommend using this hypothetical design in a real experiment because it confines time of test with number viewed before providing a rating.
2 The complete data set is at the website in the file Table 16_11 A3 data.
3 One can build the model in an SPSS syntax file, which can be saved and modified for other similar analyses.
4 The Latin square is an incomplete-block design because each participant, or block, is tested under some (actually 1 / a) of the possible combinations of factors A and B.

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_454_0.png)

# Correlation and Regression

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_456_0.png)

# Chapter 17

# An Introduction to Correlation and Regression

# 17.1 Introduction to the Correlation and Regression Chapters

Although the ANOVAs we have so far discussed are widely used to determine whether independent and dependent variables are related, they have some important limitations. Standard ANOVA treats factors as qualitative categorical variables even if they are inherently quantitative and continuous, thereby ignoring potentially useful information. In ANOVA, levels of a factor are merely considered to be different from one another. The ordering of levels or how different the levels are from one another is not considered. Also, the neat partitioning of variability into nonoverlapping components with main effects and interactions is the hallmark of ANOVA only occurs when the factors are uncorrelated. Factors are uncorrelated in designed experiments with equal numbers of scores in each cell, but generally not otherwise.

We now begin a series of chapters that develop a general framework which incorporates both categorical and quantitative variables and deal with correlated factors:

- Chapter 17 introduces the basic ideas of correlation and regression.
- Chapter 18 introduces statistical inference and power analysis for correlation and considers some alternative measures.
- Chapter 19 extends the discussion of bivariate regression and considers inference and power analysis for regression.
- Chapter 20–22 develop regression procedures when there is more than one predictor variable. This use of regression is known as multiple regression.
- Chapter 23 introduces the idea of coding categorical variables so that they can be used along with quantitative variables in regression, thereby developing a very general framework for statistical analysis. We show that ANOVA is a special case of regression.
- Chapter 24 deals with analysis of covariance (ANCOVA) within the regression framework.
- Chapter 25 integrates multiple regression analyses and focuses on interpretation.

# 17.2 Overview of Chapter 17

In Chapter 2 we considered how to graph and summarize distributions of single variables. We also briefly introduced scatterplots and the Pearson correlation coefficient as ways of summarizing data. A major goal of this chapter is to discuss in detail how to represent data in ways that allow us to see how strongly variables are related. A major focus is to expand our understanding of the correlation coefficient as a measure of degree to which variables have a linear (i.e., straight-line) relationship. This can lead to much confusion about how to interpret it and whether to compare correlations.

Another major goal of the chapter is to develop the basics of linear regression. If two variables are systematically related, it would be possible to use information about one of the variables to predict the other. For example, knowing a father's height is useful in predicting the height of his son. Although any single prediction may not be very accurate, if we consider many fathers and sons, the average can predict a son's height much better if we do not. As we would expect, the closer the variables are, the better we can predict. We would like to develop procedures for making the best predictions using the information that we have. Linear equations that use information about one variable to make optimal predictions about a second variable are referred to as bivariate equations.

# Research Design and Statistical Analysis

are interested in variables are related to one another. For example, we may wish to know how cholesterol levels vary with age or math skills are related to verbal skills. A major goal of the chapter is to present statistics that summarize important aspects of the relationship. In Chapter 17, we have the following goals:

- Provide examples of bivariate regressions and discuss how they might be represented with scatterplots.
- Discuss how to use "smoothers" or "fit lines" to extract systematic relationships between two variables in the face of random variability.
- Discuss the Pearson correlation coefficient as a measure of the strength of a relationship.
- Introduce least-squares linear regression, first with z scores and then with raw scores.
- Discuss the major differences between regression and correlation.
- Introduce the concept of regression toward the mean and provide examples of how people misunderstand or to appreciate, the consequences of this phenomenon.
- Consider measures of linear fit such as the coefficient of determination and the standard error of the estimate.
- Discuss the interpretation of the correlation coefficient and factors that influence it.

# 17.3 Some Examples of Bivariate Relationships

Consider subtraction and multiplication accuracy scores on the arithmetic skills (percent correct) for third-graders children from the Royer data set on the book's website). The basic statistics for the 28 third-grade students with values on both variables are given in Table 17.1. The multiplication accuracy scores tend to be lower than the subtraction scores, t(27) = 3.09, p = .005, and exhibit greater variability,¹ z = 2.78, p = .023.
