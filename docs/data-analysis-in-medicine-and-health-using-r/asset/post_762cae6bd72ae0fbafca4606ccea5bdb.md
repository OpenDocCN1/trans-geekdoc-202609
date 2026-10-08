
# Contents

- 10.4.5 Multivariable analysis ... 183
- 10.4.6 Interaction ... 185
- 10.4.7 Model fit assessment ... 186
- 10.4.8 Presentation and interpretation ... 188
- 10.4.9 Prediction ... 192
- 10.5 Poisson Regression for Rate ... 193
- 10.5.1 About Poisson regression for rate ... 193
- 10.5.2 Dataset ... 193
- 10.5.3 Data exploration ... 194
- 10.5.4 Univariate analysis ... 196
- 10.5.5 Multivariable analysis ... 198
- 10.5.6 Interaction ... 199
- 10.5.7 Model fit assessment ... 200
- 10.5.8 Presentation and interpretation ... 201
- 10.6 Quasi-Poisson Regression for Overdispersed Data ... 204
- 10.7 Summary ... 205

## 11 Survival Analysis: Kaplan-Meier and Cox Proportional Hazard (PH) Regression ... 207
- 11.1 Objectives ... 207
- 11.2 Introduction ... 207
- 11.3 Types of Survival Analysis ... 208
- 11.4 Prepare Environment for Analysis ... 208
- 11.4.1 RStudio project ... 208
- 11.4.2 Packages ... 209
- 11.5 Data ... 210
- 11.6 Explore Data ... 212
- 11.7 Kaplan-Meier Survival Estimates ... 215
- 11.8 Plot the Survival Probability ... 217
- 11.9 Comparing Kaplan-Meier Estimates Across Groups ... 219
- 11.9.1 Log-rank test ... 219
- 11.9.2 Peto-to-peto test ... 220
- 11.10 Semi-Parametric Models in Survival Analysis ... 222
- 11.10.1 Cox proportional hazards regression ... 222
- 11.10.2 Advantages of the Cox Proportional hazards regression ... 223
- 11.11 Estimation from Cox Proportional Hazards Regression ... 224
- 11.11.1 Simple Cox PH regression ... 224
- 11.11.2 Multiple Cox PH regression ... 227
- 11.12 Adding Interaction in the Model ... 230
- 11.13 The Proportional Hazard Assumption ... 232
- 11.13.1 Risk constant over time ... 232
- 11.13.2 Test for PH assumption ... 232
- 11.13.3 Plots to assess PH assumption ... 233
- 11.14 Model Checking ... 236
- 11.14.1 Prediction from Cox PH model ... 236
- 11.14.2 Residuals from Cox PH model ... 238
- 11.14.3 Influential observations ... 239
- 11.15 Plot the Adjusted Survival ... 240
- 11.16 Presentation and Interpretation ... 240
- 11.17 Summary ... 241

## 12 Parametric Survival Analysis ... 243
- 12.1 Objectives ... 243
- 12.2 Introduction ... 243
- 12.2.1 Advantages of parametric survival analysis ... 244
- 12.3 Parametric Survival Model ... 244
- 12.3.1 Proportional hazard models ... 245
- 12.3.2 Accelerated failure time (AFT) models ... 245
- 12.4 Analysis ... 246
- 12.4.1 Dataset ... 247
- 12.4.2 Set the environment ... 247
- 12.4.3 Read dataset ... 248
- 12.4.4 Data wrestling ... 248
- 12.4.5 Exploratory data analysis (EDA) ... 249
- 12.4.6 Exponential survival model ... 250
- 12.4.7 Weibull (accelerated failure time) ... 251
- 12.4.8 Weibull (proportional hazard) ... 253
- 12.4.9 Model adequacy for Weibull distribution ... 255
- 12.5 Summary ... 256

## 13 Introduction to Missing Data ... 257
- 13.1 Objectives ... 257
- 13.2 Introduction ... 257
- 13.3 Types of Missing Data ... 257
- 13.4 Preliminaries ... 259
- 13.4.1 Packages ... 259
- 13.4.2 Dataset ... 260
- 13.5 Exploring Missing Data ... 261
- 13.6 Handling Missing Data ... 264
- 13.6.1 Listwise deletion ... 265
- 13.6.2 Simple imputation ... 265
- 13.6.3 Single imputation ... 268
- 13.6.4 Multiple imputation ... 274
- 13.7 Presentation ... 280
- 13.8 Resources ... 280
- 13.9 Summary ... 281

## 14 Model Building and Variable Selection ... 283
- 14.1 Objectives ... 283
- 14.2 Introduction ... 283
- 14.3 Model Building ... 284
- 14.4 Variable Selection for Prediction ... 285
- 14.4.1 Backward elimination ... 285
- 14.4.2 Forward selection ... 286
- 14.4.3 Stepwise selection ... 286
- 14.4.4 All possible subset selection ... 286
- 14.5 Stopping Rule and Selection Criteria in Automatic Variable Selection ... 287
- 14.6 Problems with Automatic Variable Selection ... 287
- 14.7 Purposeful Variable Selection ... 288
- 14.8 Summary ... 288

# Bibliography 289

# Index 291

# Preface

We wrote this book to help new R programming users with limited programming and statistical backgrounds. We understand the struggles they are going through to move from point-and-click statistical software such as SPSS or MS Excel to move code-centric software as R and Python. From our experiences, frustration sets early in learning this code-centric software. It often demotivates new users to the extent that they ditch them and return to using point-and-click statistical software. This book will minimize these struggles and gently help these excited but fragile users to learn quickly and effectively the codes and workflows to perform data and statistical analysis using the R programming language.

This book's audience includes postgraduate students, public health researchers, epidemiologists and biostaticians. From our experiences teaching students in the public health, epidemiology and biostatistics programs at the School of Medical Sciences, Universiti Sains Malaysia. Between KIM and WNA, we have over 30 years of experience and training undergraduate and postgraduate students. As mentioned earlier, most of our postgraduate students are dentists in the public health, epidemiology or biostatistics programs at the School of Medical Sciences, Universiti Sains Malaysia.

The courses we teach include basic and advanced statistics, multivariable data analysis, structural equation modeling, advanced numerical data analysis and categorical data analysis. This book, we believe, will achieve its objective. The main objective is to help new R programming users (such as our undergraduate and postgraduate students) understand the R programming language, make plots, explore data, summarize data and perform statistical analyses inside RStudio IDE. We also provide the interpretation of graphs, tables and statistical models relevant to our students and us. They do not have strong mathematical and statistical grounds; however, in their career, they are very involved with collecting, analyzing and interpreting data. We do work at medical and health institutions and organizations. Their applied knowledge and skills in data analysis and epidemiological and statistical models will help them draw health policies and make evidence-based public health interventions.
