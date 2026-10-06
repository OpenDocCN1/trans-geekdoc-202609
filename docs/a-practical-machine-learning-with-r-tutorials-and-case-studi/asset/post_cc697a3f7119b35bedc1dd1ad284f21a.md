
200 8 Logistic Regression — Handling Imbalanced Data

- How to identify problems related to imbalanced data — unequal distribution of the binary classification variable (see the interactive Section 8.4).
- How to troubleshoot an imbalanced Logistic Regression, when predictive quality varies dramatically between sensitivity and specificity (see the interactive Section 8.5).
- How to use downsampling and upsampling to install an imbalanced dataset (see the interactive Section 8.5).

## 8.2 R Packages Required for the Chapter

This section lists the R packages that you need to load and execute code in the interactive sections in RStudio. Please install the following packages using Tools -> Install Packages ... from the RStudio menu (you can find more information about installing and loading packages in Section 8.4):

- The rio package (Chin et al. (2021)) to enable the loading of various data formats with one import() command. Files can be loaded from the user's hard drive or the Internet.

- The janitor package (Firke (2023)) to rename variable names to Upper-Camel and to substitute spaces and special characters in variable names.

- The tidymodels package (Kuhn and Wickham (2020)) to streamline data engineering and machine learning tasks.

- The tableExtra package (Zhu (2021)) package to support the rendering of tables.

- The learner package (Aden-Bieue et al. (2022)), which is needed together with the shiny package (Chang et al. (2022)) for the interactive exercises in this book.

- The shiny package (Chang et al. (2022)), which is needed together with the learner package (Aden-Bieue et al. (2022)) for the interactive exercises in this book.

- The glm2 package (Friedman et al. (2010) and Tay et al. (2023)), which is needed to execute Logistic Regression.

- The themis package (Hvitfeldt (2023)) to up- and downsample imbalanced datasets with advanced algorithms.

>¹See Section 4.8 for the concepts of sensitivity and specificity.

## 8.3 The Idea Behind Logistic Regression

The idea behind *Logistic Regression* can be best demonstrated with an example. Let us start with creating a synthetic dataset based on a made-up story:

After a few years past graduation, eleven close friends reunite. Financially, some of them are doing very well, while others are just doing OK. In Table 8.1, you find the yearly salaries (in $1,000) for 10 of our 11 friends with their names and an indicator if they own a yacht ($Yacht=1$) or not ($Yacht=0$). Note that there are only 10 rows in Table 8.1 as one of the 11 friends, Nina, has to arrive. We will talk more about Nina later.

Our objective is to find a machine learning algorithm that can predict for the 10 friends whether or not they own a yacht. In Table 8.1, you can see that for Jack, all friends who own a yacht have a six-figure income, and the ones who do not have low income. Therefore, finding a machine learning algorithm that uncovers this rule should be relatively easy.

To keep the simple example and because we do not aim to predict yacht ownership over our group of friends, we use all of the data from Table 8.1 as training data and do not use a testing dataset.

### TABLE 8.1 Income and Yacht Ownership

| Name | Income | Yacht |
|---|---|---|
| Jack | 45 | 1 |
| Sarah | 50 | 0 |
| Carl | 55 | 0 |
| Eric | 60 | 0 |
| Zoe | 67 | 0 |
| James | 250 | 1 |
| Enrico | 280 | 1 |
| Erica | 320 | 1 |
| Stephanie | 370 | 1 |
| Susan | 500 | 1 |

An obvious — but as it turns out, suboptimal — approach could use *OLS* to find a regression line with slope $\beta_1$ and intercept $\beta_2$ that best approximates the data (minimizing the $MSE$). Figure 8.1 shows the resulting regression line for the data in Table 8.1 and Equation (8.1) shows the related prediction equation:

$$P_{prob} = \beta_1 Inc_i + \beta_2$$
$$P_{prob} = 0.0023 Inc_i + 0.1418 \quad (8.1)$$

![](img/f240d449191f5add983daf6c380e4fe3_218_0.png)

**FIGURE 8.1** Linear Function for Binary Classification

As you can see from the regression line in Figure 8.1, the underlying regression assigns continuous numbers to different income levels rather than signing values such as 1 (yacht owner: yes) or 0 (yacht owner: no). Therefore, we interpret the continuous predictions from the regression as being a yacht owner ($P^{prob}$). Consequently, the methodology used is the Linear Probability Model (LPM)².

The linear regression in Figure 8.1, the underlying regression assigns continuous numbers to different income levels rather than signing values such as 1 (yacht owner: yes) or 0 (yacht owner: no). Therefore, we interpret the continuous predictions from the regression as being a yacht owner ($P^{prob}$). Consequently, the methodology used is the Linear Probability Model (LPM)².

## 8 Logistic Regression — Handling Imbalanced Data

The linear regression in Figure 8.1, the underlying regression assigns continuous numbers to different income levels rather than signing values such as 1 (yacht owner: yes) or 0 (yacht owner: no). Therefore, we interpret the continuous predictions from the regression as being a yacht owner ($P^{prob}$). Consequently, the methodology used is the Linear Probability Model (LPM)².

### 8.3 The Idea Behind Logistic Regression

For example, a person with an income of 75 ($75,000) is predicted not to own yacht. 0., and four of them do not own a yacht. One person has an income of 45 ($45,000), which is left of the dashed line. His yacht ownership was consequently predicted as “No”, but he does a yacht (see the horizontal line). 0.31143). Since 0.31 is smaller than 0.5, here is a shortcut to see quickly incomes are predicted:

1. Find the intersection point between the prediction function and the horizontal 0.5 line.
2. Draw a vertical line through the intersection point (see the dashed line). This line is called the decision boundary, because it reflects the boundary between predicted classes.
3. All incomes left the decision boundary (income smaller than 158) are predicted as “no”. All incomes right of the decision boundary (income greater than 158) are predicted as “yes”.

Based on the decision boundary in Figure 8.1, you can see that persons with an income greater than 158 ($158,000) are predicted to own a yacht. Five of our friends have an income greater than 158, and all own yacht (the five correctly predicted points in the upper-right section). On the other hand, persons with an income smaller than 158 ($158,000) are predicted not to own a yacht. Five of our friends have an income smaller than 158, and four of them do not own a yacht. One person has an income of 45 ($45,000), which is left of the dashed line. His yacht ownership was consequently predicted as “No”, but he does a yacht (the incorrectly predicted red point in the upper section of the diagram). Jack’s case seems to be a special case. He has the lowest income but still owns a yacht. Maybe Jack loves boats so much that he spends all his money on his boat. Perhaps he lives on the boat to save rent inherited it. We don’t know.

In any case, with predicting only one out of ten observations incorrectly linear regression seems well to predict variables. In what follows, we will show the drawbacks of linear regression to predict categorical variables, and we will provide a better alternative.

The first drawback of using linear regression to predict categorical variables is already evident in Figure 8.1. All incomes greater than 375 ($375,000) lead to probabilities greater than 1 (100%). For example, the probability of owning a yacht with an income of 500 ($500,000) is predicted to be 1.29 (129%). That makes no sense since probabilities take on on values between 0 and 1.
