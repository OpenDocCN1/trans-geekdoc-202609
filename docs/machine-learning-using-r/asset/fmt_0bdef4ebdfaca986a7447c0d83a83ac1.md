
As can be seen, the variables to be dropped are `HS`, `AVE_B`, and `RUNS_S` as they have the highest MAC values. Similarly, from **[Table 5.14](#13_Chapter05.xhtml#tab5.14)**, the number of runs scored by a player in ODIs (`ODI_RUNS_S`) and number of runs scored in Test cricket (`T_RUNS`) are highly correlated (>0.60). The MAC values are shown in **[Table 5.17](#13_Chapter05.xhtml#tab5.17):**
So the variable to be dropped is `ODI_RUNS_S`. Similarly,
• **[Table 5.18](#13_Chapter05.xhtml#tab5.18)** shows the MAC among bowling strike rate in IPL (`SR_BL`), bowling average (`AVE_BL`), and economy rate IPL (`ECON`).
• Number of wickets taken in IPL (`WKTS`) is highly correlated with runs conceded in IPL (`RUNS_C`). The MAC is shown in **[Table 5.19](#13_Chapter05.xhtml#tab5.19).**
• Wickets taken in ODIs (`ODI_WKTS`) is highly correlated with wickets taken in Tests (`T_WKTS`). **[Table 5.20](#13_Chapter05.xhtml#tab5.20)** shows the MAC between these variables.
From **[Tables 5.18](#13_Chapter05.xhtml#tab5.18), [5.19](#13_Chapter05.xhtml#tab5.19)**, and **[5.20](#13_Chapter05.xhtml#tab5.20)**, we can conclude that:
**1.** The variable to be dropped in the first case is `SR_BL` and `AVE_BL`.
**2.** The variable to be dropped in the second case is `WKTS`.
**3.** The variable to be dropped in the third case is `ODI_WKTS`.
Thus `HS`, `AVE_B`, `RUNS_S`, `ODI_RUNS_S`, `SR_BL`, `WKTS`, `AVE_BL`, and `ODI_WKTS` are the variables identified by `findCorrelation()` function which is marked for removal. Though the above variables have been highlighted by `findCorrelation()` function and it is being suggested that they be removed, the final call on retaining or removing a variable depends on understanding of the data and the domain. In actual business scenarios, it may take multiple iterations before deciding at a final set of variables, which do not have multicollinearity. The final set of variables thus decided were `HS`, `AVE_B`, `RUNS_S`, `T_RUNS`, `AVE_BL`, `ECON`, `RUNS_C`, `T_WKTS`, `SR_BL`, `SR_B`, and `ODI_SR_B`.

## 5.9.7 Rebuild Model: Using the Caret Package
Now we will build a new IPL train and test set by removing the variables identified for exclusion in the above section. Let’s revisit the predictor list created in the previous section and remove some more features.
![](images/page154-01.png)![](images/page155-01.png)
We will run the regression model with the new train set.
![](images/page155-02.png)![](images/page156-01.png)
The `p`-values of the estimated coefficients show if the variables are statistically significant in influencing response variables or not. If the `p`-value is less than the significance value (α), then the feature is statistically significant; otherwise it is not. The value of α is usually selected as 0.05. However, it may be chosen based on the context of the problem.
Using the understanding of VIF, we can infer that none of the variables in the `ipl_new_reg_model` have multicollinearity and thus can be sure that the standard error of the estimated coefficients will not be inflated.
![](images/page156-02.png)![](images/page156-03.png)
**TABLE 5.17** | MAC value between ODI runs scored and test runs scored
| `ODI_RUNS_S` || `T_RUNS` |
| --- | --- |
| 0.371 || 0.331 |
| --- | --- |
![](images/page156-04.png)
**TABLE 5.19** | MAC value between wickets taken and runs conceded in IPL
| `WKTS` || `RUNS_C` |
| --- | --- |
| 0.341 || 0.339 |
| --- | --- |
**TABLE 5.20** | MAC value between ODI wickets taken and test match wickets takes
| `ODI_WKTS` || `T_WKTS` |
| --- | --- |
| 0.2642 || 0.2628 |
| --- | --- |

### Model Selection Using AIC
Based on the `p`-values, reported by using `ipl_new_reg_model` object, only the variables `COUNTRYENG` and `SIXERS` have come out statistically significant. The interpretation of these features on the `SOLD_PRICE` is as follows:
**1.** On an average, `SOLD_PRICE` of player goes up by $562,423 for players from England compared to players from Australia (base category).
**2.** On an average, `SOLD_PRICE` of player goes up by $4,683 for every unit increase in the number of sixes hit.
However, there are other variables in the regression result for which the `p`-value is greater than 0.05. These variables would have impacted the beta coefficient estimate of significant variables as well. We have to remove these insignificant variables and run a regression again to find the true beta estimate of the significant variable. Moreover, removal of an insignificant variable has to be carried out by assessing the impact of its removal on all other variables. This assessment is needed as there will be always a certain degree of correlation among all the independent variables, which will render some significant variables insignificant. Another way to look at it is that every addition or deletion of a variable means creating a new model and thus there are many models from which to select the best model. This seems like an iterative process and may require many steps to remove all insignificant variables.
In order to overcome the issue of running the regression model in iterations, the `caret` package has a method `lmStepAIC()` which implements the strategy of variable selection and elimination by looking at **Akaike information criterion** (AIC).
As the name suggests, `lmStepAIC()` is a step function which uses AIC as a criterion for model selection. AIC estimates the quality of each model, relative to each of the other models, for a given set of variables. Thus, AIC provides a means for making a simple model by retaining fewer predictor variables.
AIC does not provide a test of a model in terms of null hypothesis and thus it does not say anything about the absolute quality of a model but only the quality relative to other models.
Formula to compute AIC is
![](images/page157-01.png)
In [Eq. (5.27)](#13_Chapter05.xhtml#eq5.27),
• `n` is the number of observations in the data.
• `RSS` is the regression sum of squares.
• `k` is the penalizing factor. Usually, `k` = 2 is used for calculating AIC. `k` = log(`n`) is sometimes referred to as Bayesian Information Criteria (BIC).
• `P` is the number of parameters in the model.
The below code chunk implements the regression model using `lmStepAIC()` method and backward elimination strategy. `lmStepAIC()` method calls `stepAIC()` function from the `MASS` package.
![](images/page157-02.png)![](images/page158-01.png)![](images/page159-01.png)

### Understanding AIC Steps
Let us first calculate the initial AIC value using [Eq. \[5.27\]](#13_Chapter05.xhtml#eq5.27). We will use `ipl_new_reg_model` object which was developed using `lm()` method from the `caret` package for calculating the initial AIC.
![](images/page159-02.png)
Let us understand the `ipl_aic_reg_model` object which is an outcome of the `lmStepAIC` and has resulted in four iterations:
• Iteration 1:
– The start AIC value for `ipl_aic_reg_model` is 2702.4. This value signifies that all the independent variables were included in the model. We calculated this value manually using the `ipl_new_reg_model` object created by `lm()` method and found this value to be same, that is 2702.4.
– ‘none’ category in `ipl_aic_reg_model` corresponds to a model that would include all the variables. In other words, none of the variables was removed and the AIC value corresponding to this is 2702.4.
– `PLAYING_ROLE`: This builds a model with `PLAYING_ROLE` variable removed from the model while retaining all other variables. In `ipl_aic_reg_model`, the AIC value with `PLAYING_ROLE` removed from the model is 2699.7. Let us reproduce this AIC value manually using `lm()` method.
![](images/page159-03.png)![](images/page160-01.png)
We found the AIC value to be same as 2699.7.
• Iteration 1 Continued:
