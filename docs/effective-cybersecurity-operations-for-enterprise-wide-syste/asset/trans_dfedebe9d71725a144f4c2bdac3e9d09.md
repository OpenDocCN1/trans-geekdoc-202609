
-   [PIU平均分在男性和女性之间相似，说明性别在预测PIU时无关。此外，两性的分数分布均匀，正态性检验被拒绝。分数分布如图14和15所示。]

| Figure 11. PIU score distribution categorised by genders |

| --- |

| ![Figure978-1-6684-9018-1.ch001.f11](i/ch001.f11.png) |

| --- |

-   与性别结果类似，将PIU分数与在家办公（WFH）条件结合后的发现同样无关。两个条件的均值约相同，说明这是一个无显著预测Internet成瘾的因素。PIU分数的分布如图16和17所示。值得注意的是，在家办公有时的参与者比疫情前几乎没有在家办公的人得分更高。

Table 14. PIU statistical overview grouped by WFH conditions

|  || Frequency || Mean || Standard Deviation |

| --- | --- | --- | --- |

| Rarely Worked From home (<once a day per week) || 205 || 13.849 || 4.365 |

| --- | --- | --- | --- |

| Work from home sometimes (>= once a day per week) || 94 || 13.372 || 4.672 |

| Figure 12. PIU distribution for both WFH conditions |

| --- |

| ![Figure978-1-6684-9018-1.ch001.f12](i/ch001.f12.png) |

| --- |

-   本研究使用了JASP version 0.16.1来研究与数据集相关的模式。JASP（Jefferey's Amazing Statistics Program的缩写）是一款开源软件，主要用于统计和量化分析。在本研究的父项研究中，使用了AMOS-SPSS进行量化分析。然而，SPSS与MacOS设备不兼容，这限制了当前研究作者的使用。与SPSS不同，JASP是免费工具，能够执行类似AMOS-SPSS的功能。首先进行了Shapiro-Wilk测试，并记录其p值，以检查变量分布是否为正态。

The Shapiro-Wilk test refers to a statistical test used to check if a continuous variable follows a normal distribution. The null hypothesis H[0] states that the distribution is normal and the alternative hypotheses (H[1]) states that the distribution is not normal. The p-value of the Shapiro wilk test indicates the hypothesis that is valid and accepted. In the context of the current study, the sample size of 299 participants meant that the distribution of the variable needs to be determined so as to choose the appropriate statistical method. The two major hypothesis testing methods are Parametric and Non-Parametric testing. The parametric testing is most applicable to normal distributions while the non-parametric tests are independent of the normality status. The results of Shapiro wilk test and its corresponding p-values for relevant variables in the hypothesis is illustrated in the table below:

Table 15. Statistical tests results of psychosocial metrics

|  || Shapiro-Wilk (W) || P-Value of Shapiro-Wilk |

| --- | --- | --- |

| PIUQ || 0.979 || <.001 |

| --- | --- | --- |

| SWLS || 0.972 || <.001 |

| UCLA || 0.912 || <.001 |

The Shapiro-Wilk test showed that the distributions (PIUQ, SWLS, UCLA) departed significantly from normality (W= .979,.972 and .912, and p-value <.001). Based on this outcome, a non-parametric test was used. To test the relationship between variables relevant in the hypothesis, this study adopts the use of regression analysis to make findings. A combination of multiple linear regression and logistical regression was used to show relationships and determine the factors that are significant predictors of the observed psycho-social variables. For each relationship variable relationship investigated, the overall model summary is reported along with its Anova description and its individual regression results.

Model 1: Multiple Regression Predicting Security Behaviour Using Internet Addiction Levels and WFH Variable

Based on evidence identified in previous literature, internet addiction is known to be a significant predictor of an individual’s online security behaviour ([Hadlington & Parsons, 2017](#978-1-6684-9018-1.ch001.xhtml#r55)). This is confirmed in the current study using a linear regression (p=.002, R²\=0.032), the results signify there is a 3.2% variance in security behavior when addicted users and non-addicted users are compared. Although this value is quite small, the p-value shows that it is a significant difference. This model aims to investigate the impact of WFH conditions mixed with internet addiction levels, as a predictor for cyber security behaviors. The descriptive overview of the combined variable is shown below:

Table 16. Overview of PIUQ and WFH categories together

|  || PIUQ Level |

| --- | --- |

| WFH Conditions ||  || 1 (Unaddicted) || 2(Addicted) || Total |

| 1 (Barely) || 114 || 91 || 205 |

| 2 (Often) || 58 || 36 || 94 |

| Total || 172 || 127 || 299 |

Overall, there are more participants who barely worked from home, as well as participants who exhibit little internet addiction traits. Due to the significant difference in group density, the results can be interpreted in different ways. One way of interpreting this statistical overview is 38% of participants barely worked from home and were not addicted to the internet, a total of 91 participants barely worked from home and suffered problematic internet use, also, there are more participants who often worked from home and are non-addicts (19.4%) compared to those who often worked from home and had no internet regulation (12%). A more detailed way to interpret the statistical overview is addressing each variable with reference to the other variable. That said, the table shows that 62% of individuals who often worked from home are regulated internet users, while 44.3% of those who often work from home are addicted to the internet.

The results of the linear regression of this model are shown below:

Table 17. Model 1 summary

| Model || R || R² || Adjusted R² || RMSE |

| --- | --- | --- | --- | --- |

| H[0] || 0.000 || 0.000 || 0.000 || 8.388 |

| --- | --- | --- | --- | --- |

| H[1] || 0.196 || 0.038 || 0.032 || 8.253 |

The summary model shows the result of all variables taken together, and how these variables combined together predict the security behaviour. The R² value shows the proportion of variance in Security Behaviour that is impacted by the variables put together. In this case, the R² is 0.038, a considerably small value that indicates that there is a 3.8% in variance in security behaviour by both internet addiction and WFH conditions put together. RMSE, short “Root Mean Square Error”, is a measure of how far from the regression line the data points are located. RMSE value for this regression model is 8.253.

Table 18. Model 1 anova summary

| Model ||  || Sum of Squares || df || Mean Squares || F || p |

| --- | --- | --- | --- | --- | --- | --- |

| H[1] || Regression || 805.648 || 2 || 402.824 || 5.914 || 0.003 |

| --- | --- | --- | --- | --- | --- | --- |

|  || Residual || 20163.168 || 296 || 68.119 ||  ||  |

|  || Total || 20968.816 || 298 ||  ||  |
