![](image_rsrc1BH.jpg)

  

101   
DATA SCIENCE   
DRAWINGS

Raymond Lim

@MinuteData

Copyright © 2025  
Raymond Lim

All rights reserved. This book or any portion thereof may not be reproduced or used in any manner whatsoever without the express written permission of the author except for the use of brief quotations in a book review.

ISBN 9798317027308

Published through Amazon KDP

Introduction

One spring day in 2018, I strolled past my childhood elementary school. I glanced through the windows to see if I’d recognized the teacher. Nope - it was a young teacher enthusiastically teaching first graders shapes… using PowerPoint! Call me old-school, but how are kids learning how to draw shapes when they just magically appear on PowerPoint slides?!

Fast forward to 2024. I was preparing for data science interviews using online courses, YouTube videos and mobile apps. However, as a millennial who went to school before smartphones, passively scrolling through online content did not work.

I soon created TikToks drawing out data topics with colorful markers, hoping others would draw along. This book is a compilation of those drawings.

Who this book is for: People who previously learned statistics, machine learning, econometrics, SQL, and want to refresh with colorful one-pagers (think flash cards!). This book is intentionally informal, colorful and raw. You’ll find scribbles, corrections, obscure handwriting that will make you learn more actively.

Watch the accompanying videos on social media!

tiktok.com/@MinuteData

youtube.com/@MinuteData

instagram.com/MinuteData

facebook.com/MinuteData

minutedata22@gmail.com

About the author: Raymond Lim graduated from Columbia University before data science classes even existed. He worked for 15+ years as an economics researcher in academia, biostatistician in healthcare, data scientist at Meta and Google. He’s also a latin ballroom dancer!

Table of Contents

[Part 1: Supervised Learning             6](#part0003.xhtml#a19P)

[1\. Supervised vs Unsupervised Learning             6](#part0003.xhtml#a199)

[2\. K-Nearest Neighbor             7](#part0004.xhtml#a181)

[3\. Decision Trees             8](#part0005.xhtml#a15N)

[4\. Random Forest             9](#part0005.xhtml#a192)

[5\. Gradient Boosted Trees             10](#part0005.xhtml#a13N)

[6\. Gradient Descent             11](#part0005.xhtml#a13H)

[7\. Support Vector Machine             12](#part0005.xhtml#a13J)

[8\. Bias-Variance Tradeoff             13](#part0005.xhtml#a15W)

[9\. Cross Validation             14](#part0005.xhtml#a142)

[10\. Regularization - Lasso vs Ridge             15](#part0005.xhtml#a14M)

[11\. Hyperparameter Tuning             16](#part0005.xhtml#a16X)

[12\. Stepwise Feature Selection             17](#part0005.xhtml#a19K)

[13\. Naive Bayes             18](#part0005.xhtml#a18U)

[14\. Collaborative Filtering             19](#part0005.xhtml#a15X)

[15\. Bagging vs Boosting vs Stacking             20](#part0005.xhtml#a19N)

[16\. Multi-Armed Bandit             21](#part0005.xhtml#a187)

[Part 2: Unsupervised Learning             22](#part0005.xhtml#a15G)

[17\. K-Means Clustering             22](#part0005.xhtml#a197)

[18\. Hierarchical Clustering             23](#part0005.xhtml#a195)

[19\. Density Clustering             24](#part0005.xhtml#a17Y)

[20\. How Many Clusters? Calinski Index             25](#part0005.xhtml#a18J)

[21\. Dendrogram             26](#part0005.xhtml#a137)

[22\. Distance Measures             27](#part0005.xhtml#a18Y)

[23\. Cosine Similarity             28](#part0005.xhtml#a138)

[24\. String Distance             29](#part0005.xhtml#a13T)

[25\. Earth Mover's Distance             30](#part0005.xhtml#a151)

[26\. Principal Components Analysis             31](#part0006.xhtml#a15Y)

[27\. Topic Modeling - Latent Dirichlet Allocation             32](#part0006.xhtml#a16V)

[Part 3: Probability & Statistics             33](#part0006.xhtml#a163)

[28\. Levels of Measurement             33](#part0006.xhtml#a17T)

[29\. Bernoulli vs Binomial             34](#part0006.xhtml#a16G)

[30\. Law of Large Numbers vs Central Limit Theorem             35](#part0006.xhtml#a135)

[31\. Bayes Theorem             36](#part0006.xhtml#a13D)

[32\. Monty Hall Problem             37](#part0006.xhtml#a19W)

[33\. Variance, Standard Deviation             38](#part0006.xhtml#a17H)

[34\. Confidence Interval             39](#part0006.xhtml#a17D)

[35\. Standard Normal Distribution             40](#part0006.xhtml#a170)

[36\. Coefficient of Variation             41](#part0006.xhtml#a17E)

[37\. P-value             42](#part0006.xhtml#a149)

[38\. Type I vs Type II Error             43](#part0006.xhtml#a14R)

[39\. Bivariate Tests             44](#part0006.xhtml#a17Z)

[40\. Pearson Correlation             45](#part0006.xhtml#a17N)

[41\. Chi-Square Test             46](#part0006.xhtml#a16H)

[42\. ANOVA             47](#part0006.xhtml#a16R)

[43\. Rank Sum Test             48](#part0006.xhtml#a19U)

[44\. Wilcoxon Signed Rank Test             49](#part0006.xhtml#a194)

[45\. Accuracy, Precision, Recall             50](#part0006.xhtml#a18A)

[46\. ROC Curve             51](#part0006.xhtml#a18C)

[47\. Standardization, Feature Scaling             52](#part0006.xhtml#a18E)

[48\. Outlier Detection             53](#part0006.xhtml#a18R)

[49\. Log Transformation             54](#part0006.xhtml#a17W)

[50\. Winsorization             55](#part0006.xhtml#a13S)

[51\. Missing Data             56](#part0006.xhtml#a16C)

[52\. Switchback Test             57](#part0006.xhtml#a19E)

[53\. Kolmogorov-Smirnov Test             58](#part0006.xhtml#a143)

[54\. Reliability, Validity             59](#part0007.xhtml#a13G)

[55\. Sample Size Calculation             60](#part0007.xhtml#a190)

[56\. Multiple Comparisons             61](#part0007.xhtml#a144)

[57\. Blocked vs Stratified Sampling             62](#part0007.xhtml#a176)

[58\. Anscombe’s Quartet             63](#part0008.xhtml#a16Y)

[59\. Power Law             64](#part0008.xhtml#a158)

[60\. Survivorship Bias             65](#part0008.xhtml#a154)

[61\. Meta Analysis             66](#part0008.xhtml#a14W)

[Part 4: Econometrics             67](#part0009.xhtml)

[62\. Linear Regression             67](#part0009.xhtml#a18D)

[63\. Deriving OLS             68](#part0010.xhtml#a12W)

[64\. Interaction Effect             69](#part0011.xhtml#a171)

[65\. Chow Test (Structural Break)             70](#part0012.xhtml#a17R)

[66\. Linear Probability Model             71](#part0013.xhtml#a148)

[67\. Logistic Regression             72](#part0014.xhtml#a14F)

[68\. Ordered Logistic Regression             73](#part0015.xhtml#a15Z)

[69\. Censored Regression (Tobit)             74](#part0016.xhtml#a17X)

[70\. Poisson Regression             75](#part0017.xhtml#a161)

[71\. R-Squared             76](#part0018.xhtml#a16K)

[72\. Heteroskedasticity             77](#part0019.xhtml#a16T)

[73\. Multicollinearity, Variance Inflation Factor             78](#part0020.xhtml#a14G)

[74\. Standardized Coefficients             79](#part0021.xhtml#a17S)

[75\. Regression to the Mean             80](#part0022.xhtml#a13Z)

[76\. Spline Regression             81](#part0023.xhtml#a13F)

[77\. Simpson’s Paradox             82](#part0024.xhtml#a18G)

[78\. Fixed Effects vs Random Effects             83](#part0025.xhtml#a17M)

[79\. Hausman Test             84](#part0026.xhtml#a13B)

[80\. Fixed Effects as Ability             85](#part0027.xhtml#a18H)

[81\. Causal Inference             86](#part0028.xhtml#a18P)

[82\. Propensity Score Matching             87](#part0029.xhtml#a193)

[83\. Difference-in-Differences             88](#part0030.xhtml#a17K)

[84\. Regression Discontinuity             89](#part0031.xhtml#a16M)

[85\. 2-Stage-Least-Squares; Instrumental Variables             90](#part0032.xhtml#a19G)

[86\. Heckman Selection Model             91](#part0033.xhtml#a15D)

[Part 5: SQL             92](#part0034.xhtml)

[87\. Inner vs Outer Join             92](#part0034.xhtml#a18W)

[88\. Cross Join             93](#part0035.xhtml#a18F)

[89\. Where vs Having             94](#part0036.xhtml#a15A)

[90\. Group By             95](#part0037.xhtml#a13C)

[91\. Window Functions             96](#part0038.xhtml#a177)

[92\. Lag             97](#part0039.xhtml#a159)

[93\. Moving Average             98](#part0040.xhtml#a15U)

[94\. Union vs Union All             99](#part0041.xhtml#a198)

[95\. Rank vs Dense Rank             100](#part0042.xhtml#a14X)

[96\. CTE vs Subquery             101](#part0043.xhtml#a15C)

[97\. Table Alias             102](#part0044.xhtml#a17V)

[98\. Wildcard             103](#part0045.xhtml#a17F)

[99\. Like             104](#part0046.xhtml#a16P)

[100\. Regular Expressions             105](#part0047.xhtml#a13Y)

[Part 6: Career             106](#part0048.xhtml)

[101\. Academic vs Tech             106](#part0048.xhtml#a19R)

[102\. \[BONUS\] Case Study: Man in Finance             107](#part0049.xhtml#a175)

[Closing Thoughts             108](#part0049.xhtml#a13V)

# Part 1: Supervised Learning

## 1.  [Supervised vs Unsupervised Learning](https://www.tiktok.com/@minutedata/video/7328791238952439046)

![](image_rsrc1BJ.jpg)

## 2.  [K-Nearest Neighbor](https://www.tiktok.com/@minutedata/video/7273832570977275141)

![](image_rsrc1BK.jpg)

## 3.  [Decision Trees](https://www.tiktok.com/@minutedata/video/7272465826043759878)

![](image_rsrc1BM.jpg)

## 4.  [Random Forest](https://www.tiktok.com/@minutedata/video/7274188400687648006)

![](image_rsrc1BN.jpg)

## 5.  [Gradient Boosted Trees](https://www.tiktok.com/@minutedata/video/7448304139924294955)

![](image_rsrc1BP.jpg)

## 6.  [Gradient Descent](https://www.tiktok.com/@minutedata/video/7384736566188510470)

![](image_rsrc1BR.jpg)

## 7.  [Support Vector Machine](https://www.tiktok.com/@minutedata/video/7273433569970720005)

![](image_rsrc1BS.jpg)

## 8.  [Bias-Variance Tradeoff](https://www.tiktok.com/@minutedata/video/7273458327420538117)

![](image_rsrc1BT.jpg)

## 9.  [Cross Validation](https://www.tiktok.com/@minutedata/video/7283123147103210758)

![](image_rsrc1BU.jpg)

## 10.                    [Regularization - Lasso vs Ridge](https://www.tiktok.com/@minutedata/video/7367735762382556421)

![](image_rsrc1BV.jpg)

## 11.                    [Hyperparameter Tuning](https://www.tiktok.com/@minutedata/video/7379251948161109253)

![](image_rsrc1BW.jpg)

## 12.                    [Stepwise Feature Selection](https://www.tiktok.com/@minutedata/video/7349550090106703110)

![](image_rsrc1BX.jpg)

## 13.                    [Naive Bayes](https://www.tiktok.com/@minutedata/video/7393719005476867334)

![](image_rsrc1BY.jpg)

## 14.                    [Collaborative Filtering](https://www.tiktok.com/@minutedata/video/7275832619948985606)

![](image_rsrc1BZ.jpg)

## 15.                    [Bagging vs Boosting vs Stacking](https://www.tiktok.com/@minutedata/video/7286840428064967941)

![](image_rsrc1C0.jpg)

## 16.                    [Multi-Armed Bandit](https://www.tiktok.com/@minutedata/video/7307994669399444742)

![](image_rsrc1C1.jpg)

# Part 2: Unsupervised Learning

## 17.                    [K-Means Clustering](https://www.tiktok.com/@minutedata/video/7272158813283716358)

![](image_rsrc1C2.jpg)

## 18.                    [Hierarchical Clustering](https://www.tiktok.com/@minutedata/video/7272512671935696133)

![](image_rsrc1C3.jpg)

## 19.                    [Density Clustering](https://www.tiktok.com/@minutedata/video/7336572535556836613)

![](image_rsrc1C4.jpg)

## 20.                    [How Many Clusters? Calinski Index](https://www.tiktok.com/@minutedata/video/7272173372966964485)

![](image_rsrc1C5.jpg)

## 21.                    [Dendrogram](https://www.tiktok.com/@minutedata/video/7351753709413485829)

![](image_rsrc1C6.jpg)

## 22.                    [Distance Measures](https://www.tiktok.com/@minutedata/video/7374147332549512454)

![](image_rsrc1C7.jpg)

## 23.                    [Cosine Similarity](https://www.tiktok.com/@minutedata/video/7370329004550655238)

![](image_rsrc1C8.jpg)

## 24.                    [String Distance](https://www.tiktok.com/@minutedata/video/7471665854489496878)

![](image_rsrc1C9.jpg)

## 25.                    [Earth Mover's Distance](https://www.tiktok.com/@minutedata/video/7463821039949106478)

![](image_rsrc1CA.jpg)

## 26.                    [Principal Components Analysis](https://www.tiktok.com/@minutedata/video/7422241457311943982)

![](image_rsrc1CB.jpg)

## 27.                    [Topic Modeling - Latent Dirichlet Allocation](https://www.tiktok.com/@minutedata/video/7383334782421257477)

![](image_rsrc1CC.jpg)

# Part 3: Probability & Statistics

## 28.                    [Levels of Measurement](https://www.tiktok.com/@minutedata/video/7320994567925288197)

![](image_rsrc1CD.jpg)

## 29.                    [Bernoulli vs Binomial](https://www.tiktok.com/@minutedata/video/7273429809311665413)

![](image_rsrc1CE.jpg)

## 30.                    [Law of Large Numbers vs Central Limit Theorem](https://www.tiktok.com/@minutedata/video/7273234089778482438)

![](image_rsrc1CF.jpg)

## 31.                    [Bayes Theorem](https://www.tiktok.com/@minutedata/video/7284964722930191621)

![](image_rsrc1CG.jpg)

## 32.                    [Monty Hall Problem](https://www.tiktok.com/@minutedata/video/7386994948475735302)

![](image_rsrc1CH.jpg)

## 33.                    [Variance, Standard Deviation](https://www.tiktok.com/@minutedata/video/7391086131355340037)

![](image_rsrc1CJ.jpg)

## 34.                    [Confidence Interval](https://www.tiktok.com/@minutedata/video/7304694821736762630)

![](image_rsrc1CK.jpg)

## 35.                    [Standard Normal Distribution](https://www.tiktok.com/@minutedata/video/7417044609982795039)

![](image_rsrc1CM.jpg)

## 36.                    [Coefficient of Variation](https://www.tiktok.com/@minutedata/video/7453940817078537514)

![](image_rsrc1CN.jpg)

## 37.                    [P-value](https://www.tiktok.com/@minutedata/video/7273963663676017925)

![](image_rsrc1CP.jpg)

## 38.                    [Type I vs Type II Error](https://www.tiktok.com/@minutedata/video/7280462823505825029)

![](image_rsrc1CR.jpg)

## 39.                    [Bivariate Tests](https://www.tiktok.com/@minutedata/video/7411884175587904799)

![](image_rsrc1CS.jpg)

## 40.                    [Pearson Correlation](https://www.tiktok.com/@minutedata/video/7435273613063867694)

![](image_rsrc1CT.jpg)

## 41.                    [Chi-Square Test](https://www.tiktok.com/@minutedata/video/7400028850681302303)

![](image_rsrc1CU.jpg)

## 42.                    [ANOVA](https://www.tiktok.com/@minutedata/video/7375899872844696838)

![](image_rsrc1CV.jpg)

## 43.                    [Rank Sum Test](https://www.tiktok.com/@minutedata/video/7430095738148834603)

![](image_rsrc1CW.jpg)

## 44.                    [Wilcoxon Signed Rank Test](https://www.tiktok.com/@minutedata/video/7469059181287460138)

![](image_rsrc1CX.jpg)

## 45.                    [Accuracy, Precision, Recall](https://www.tiktok.com/@minutedata/video/7273233132218895622)

![](image_rsrc1CY.jpg)

## 46.                    [ROC Curve](https://www.tiktok.com/@minutedata/video/7344369840192376069)

![](image_rsrc1CZ.jpg)

## 47.                    [Standardization, Feature Scaling](https://www.tiktok.com/@minutedata/video/7278451645837626629)

![](image_rsrc1D0.jpg)

## 48.                    [Outlier Detection](https://www.tiktok.com/@minutedata/video/7277576322623212806)

![](image_rsrc1D1.jpg)

## 49.                    [Log Transformation](https://www.tiktok.com/@minutedata/video/7334362781023472902)

![](image_rsrc1D2.jpg)

## 50.                    [Winsorization](https://www.tiktok.com/@minutedata/video/7369232724265159942)

![](image_rsrc1D3.jpg)

## 51.                    [Missing Data](https://www.tiktok.com/@minutedata/video/7401489098189393183)

![](image_rsrc1D4.jpg)

## 52.                    [Switchback Test](https://www.tiktok.com/@minutedata/video/7445671119614496042)

![](image_rsrc1D5.jpg)

## 53.                    [Kolmogorov-Smirnov Test](https://www.tiktok.com/@minutedata/video/7334371572569869573)

![](image_rsrc1D6.jpg)

## 54.                    [Reliability, Validity](https://www.tiktok.com/@minutedata/video/7419687616469142826)

![](image_rsrc1D7.jpg)

## 55.                    [Sample Size Calculation](https://www.tiktok.com/@minutedata/video/7346953124302621958)

![](image_rsrc1D8.jpg)

## 56.                    [Multiple Comparisons](https://www.tiktok.com/@minutedata/video/7354747368878787846)

![](image_rsrc1D9.jpg)

## 57.                    [Blocked vs Stratified Sampling](https://www.tiktok.com/@minutedata/video/7339179599479262470)

![](image_rsrc1DA.jpg)

## 58.                    [Anscombe’s Quartet](https://www.tiktok.com/@minutedata/video/7315813283787738369)

![](image_rsrc1DB.jpg)

## 59.                    [Power Law](https://www.tiktok.com/@minutedata/video/7289825534375202054)

![](image_rsrc1DC.jpg)

## 60.                    [Survivorship Bias](https://www.tiktok.com/@minutedata/video/7283637581575785733)

![](image_rsrc1DD.jpg)

## 61.                    [Meta Analysis](https://www.tiktok.com/@minutedata/video/7430487627507240234)

![](image_rsrc1DE.jpg)

# Part 4: Econometrics

## 62.                    [Linear Regression](https://www.tiktok.com/@minutedata/video/7272160357349657862)

## ![](image_rsrc1DF.jpg)

## 63.                    [Deriving OLS](https://www.tiktok.com/@minutedata/video/7364391928982424837)

## ![](image_rsrc1DG.jpg)

## 64.                    [Interaction Effect](https://www.tiktok.com/@minutedata/video/7376638415795752197)

## ![](image_rsrc1DH.jpg)

## 65.                    [Chow Test (Structural Break)](https://www.tiktok.com/@minutedata/video/7427832792249093419)

## ![](image_rsrc1DJ.jpg)

## 66.                    [Linear Probability Model](https://www.tiktok.com/@minutedata/video/7381819195505380614)

## ![](image_rsrc1DK.jpg)

## 67.                    [Logistic Regression](https://www.tiktok.com/@minutedata/video/7305577569561234693)

## ![](image_rsrc1DM.jpg)

## 68.                    [Ordered Logistic Regression](https://www.tiktok.com/@minutedata/video/7466425750670052654)

## ![](image_rsrc1DN.jpg)

## 69.                    [Censored Regression (Tobit)](https://www.tiktok.com/@minutedata/video/7458677073490611502)

## ![](image_rsrc1DP.jpg)

## 70.                    [Poisson Regression](https://www.tiktok.com/@minutedata/video/7437879440421489962)

## ![](image_rsrc1DR.jpg)

## 71.                    [R-Squared](https://www.tiktok.com/@minutedata/video/7385873692955315461)

## ![](image_rsrc1DS.jpg)

## 72.                    [Heteroskedasticity](https://www.tiktok.com/@minutedata/video/7337314998533836038)

## ![](image_rsrc1DT.jpg)

## 73.                    [Multicollinearity, Variance Inflation Factor](https://www.tiktok.com/@minutedata/video/7310982307815460102)

## ![](image_rsrc1DU.jpg)

## 74.                    [Standardized Coefficients](https://www.tiktok.com/@minutedata/video/7406663556080422174)

## ![](image_rsrc1DV.jpg)

## 75.                    [Regression to the Mean](https://www.tiktok.com/@minutedata/video/7326180131960098053)

## ![](image_rsrc1DW.jpg)

## 76.                    [Spline Regression](https://www.tiktok.com/@minutedata/video/7313208608701893893)

## ![](image_rsrc1DX.jpg)

## 77.                    [Simpson’s Paradox](https://www.tiktok.com/@minutedata/video/7276033354598747397)

## ![](image_rsrc1DY.jpg)

## 78.                    [Fixed Effects vs Random Effects](https://www.tiktok.com/@minutedata/video/7276382032324758789)

## ![](image_rsrc1DZ.jpg)

## 79.                    [Hausman Test](https://www.tiktok.com/@minutedata/video/7432675432945798443)

## ![](image_rsrc1E0.jpg)

## 80.                    [Fixed Effects as Ability](https://www.tiktok.com/@minutedata/video/7440458304553291054)

## ![](image_rsrc1E1.jpg)

## 81.                    [Causal Inference](https://www.tiktok.com/@minutedata/video/7292803089449422086)

## ![](image_rsrc1E2.jpg)

## 82.                    [Propensity Score Matching](https://www.tiktok.com/@minutedata/video/7281230505620655366)

## ![](image_rsrc1E3.jpg)

## 83.                    [Difference-in-Differences](https://www.tiktok.com/@minutedata/video/7272495555694169350)

## ![](image_rsrc1E4.jpg)

## 84.                    [Regression Discontinuity](https://www.tiktok.com/@minutedata/video/7273213592713923846)

## ![](image_rsrc1E5.jpg)

## 85.                    [2-Stage-Least-Squares; Instrumental Variables](https://www.tiktok.com/@minutedata/video/7424874851468397867)

## ![](image_rsrc1E6.jpg)

## 86.                    [Heckman Selection Model](https://www.tiktok.com/@minutedata/video/7396327471794228486)

# ![](image_rsrc1E7.jpg)

# Part 5: SQL

## 87.                    [Inner vs Outer Join](https://www.tiktok.com/@minutedata/video/7318405787829767429)

## ![](image_rsrc1E8.jpg)

## 88.                    [Cross Join](https://www.tiktok.com/@minutedata/video/7380760269301091590)

## ![](image_rsrc1E9.jpg)

## 89.                    [Where vs Having](https://www.tiktok.com/@minutedata/video/7360354277556063494)

## ![](image_rsrc1EA.jpg)

## 90.                    [Group By](https://www.tiktok.com/@minutedata/video/7323613042816634117)

## ![](image_rsrc1EB.jpg)

## 91.                    [Window Functions](https://www.tiktok.com/@minutedata/video/7275113981310979333)

## ![](image_rsrc1EC.jpg)

## 92.                    [Lag](https://www.tiktok.com/@minutedata/video/7275304984877518086)

## ![](image_rsrc1ED.jpg)

## 93.                    [Moving Average](https://www.tiktok.com/@minutedata/video/7276044708357377285)

## ![](image_rsrc1EE.jpg)

## 94.                    [Union vs Union All](https://www.tiktok.com/@minutedata/video/7398896687206403334)

## ![](image_rsrc1EF.jpg)

## 95.                    [Rank vs Dense Rank](https://www.tiktok.com/@minutedata/video/7286102078106144006)

## ![](image_rsrc1EG.jpg)

## 96.                    [CTE vs Subquery](https://www.tiktok.com/@minutedata/video/7331357454187416837)

## ![](image_rsrc1EH.jpg)

## 97.                    [Table Alias](https://www.tiktok.com/@minutedata/video/7341785232347073797)

## ![](image_rsrc1EJ.jpg)

## 98.                    [Wildcard](https://www.tiktok.com/@minutedata/video/7357328600011459846)

## ![](image_rsrc1EK.jpg)

## 99.                    [Like](https://www.tiktok.com/@minutedata/video/7324417354551790854)

## ![](image_rsrc1EM.jpg)

## 100.             [Regular Expressions](https://www.tiktok.com/@minutedata/video/7414127584595741983)

# ![](image_rsrc1EN.jpg)

# Part 6: Career

## 101.             [Academic vs Tech](https://www.tiktok.com/@minutedata/video/7362934467259944198)

## ![](image_rsrc1EP.jpg)

## 102.             [\[BONUS\] Case Study: Man in Finance](https://www.tiktok.com/@minutedata/video/7378116786052533509)

## ![](image_rsrc1ER.jpg)

# Closing Thoughts

Online courses, education apps and AI summaries make learning so accessible. We consume more information than ever, yet barely remember half of it. Next time you’re learning something, write it out! Draw, scribble, erase, cross out, doodle! You may be surprised how much more you’ll remember!