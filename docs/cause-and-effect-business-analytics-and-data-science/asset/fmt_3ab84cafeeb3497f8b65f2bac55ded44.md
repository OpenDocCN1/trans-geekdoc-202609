
### 6.5.3 Method 2: A Single-Model Approach with a Treatment Dummy

[Lo (2002)](#chapter6.xhtml#ref6_8) proposes to model the treatment and control groups together in a single model, capturing lift through terms that interact with the treatment variable. This method was also mentioned by [Potter (2013)](#chapter6.xhtml#ref6_17) as the chosen approach for a recent presidential election. In this method, the model population includes both the treatment and control observations, and as before, the dependent variable is a binary measure of response. But here the independent variables comprise two sets: first are the variables that capture baseline response for both treatment and control populations (the “main” effects), while the second set captures lift response by interacting the control variables with a dummy variable that is set to 1 for treatment and takes on values of 0 for all control observations.

Formally, the probability of response, `P[i]`, is a function of the treatment dummy variable, `T[i]`, and a vector of independent variables or predictors, `X[i]`:

$$P\_{i} = \\frac{exp\\left( \\alpha + \\beta{'X}\_{i} + \\gamma T\_{i} + \\delta'X\_{i}T\_{i} \\right)}{1 + exp\\left( \\alpha + \\beta'X\_{i} + \\gamma T\_{i} + \\delta'X\_{i}T\_{i} \\right)}$$

where `α`, `β`, `γ`, and `δ` are parameters to be estimated. Therefore,

`P[i]`|treatment−`P[i]`|control = `P[i]`|(`T[i]`\=1)−`P[i]`|(`T[i]`\=0)

$$= \\frac{\\exp\\left( {\\alpha + \\gamma + \\beta^{\\prime}X\_{i} + \\delta^{\\prime}X\_{i}} \\right)}{1 + \\exp\\left( {\\alpha + \\gamma + \\beta^{\\prime}X\_{i} + \\delta^{\\prime}X\_{i}} \\right)}$$

$$= \\frac{\\exp\\left( {\\alpha + \\beta^{\\prime}X\_{i}} \\right)}{1 + \\exp\\left( {\\alpha + \\beta^{\\prime}X\_{i}} \\right)}$$

(6.1)

The final prediction of true lift is then equal to the difference of two scores, given by

Prob (response if Treated)–Prob (response if not Treated)

= score with treatment dummy set to 1 – score with treatment dummy set to 0

Page 134 Since this model is fit to the data only once, one is guaranteed that the two scores will be on the same scale.

The process is summarized in detail as follows:

1. Include the response and covariate data, `{Y[i], X[i]}` from both the treatment and control groups in the analysis data set and assign a dummy variable `T[i]` to 1 for the treatment group and 0 for the control group.
2. Randomly divide the data set into training and holdout samples;
3. Further divide the training sample into two sub-samples by `T[i]`, that is, one is treatment and the other is control.
4. Multiply all independent variables, `X[i]`, by `T[i]` to form the interaction effects, `X[i]*T[i]`.
5. Fit a stepwise logistic model using `Y[i]` as the dependent variable and `X[i]`, `T[i]`, and `X[i]*T[i]` as independent variables.

Method 2 is not without its own disadvantages. Including the interaction terms, there may be a large number of variables, and multicollinearity is likely. When the correlation between a baseline and its interaction variable is very high (say, over 95%), some judgment call may be needed to select one of them for model development. As with Method 1, taking the difference between two model scores may compound errors.

Method 2 proposed for marketing is actually similar to measuring heterogeneous treatment effects (also known as effect modification) in fields such as epidemiology and social sciences where interaction effects are used for analysis. The subtle difference is that Method 2 focuses on predicting individual level lift for future targeting while those other fields typically study group-level differences (e.g., [Greenland et al. 2008](#chapter6.xhtml#ref6_3); [Brand and Xie 2010](#chapter6.xhtml#ref6_1)).

Note that both Methods 1 and 2 can be easily applied with other supervised-learning techniques such as MARS, neural network, and decision trees (e.g., [Haughton and Oulabi 1997](#chapter6.xhtml#ref6_4)).

## 6.6 Uplift Model Evaluation Methods

In addition to the model development method, [Lo (2002)](#chapter6.xhtml#ref6_8) has proposed a procedure for validation using a holdout sample. Because treatment and control groups are both involved, and the objective is to measure the “lift over control,” this procedure is different from validating a standard supervised learning model, such as the standard logistic regression approach, where only Page 135 the treatment group is used. Given that such a procedure is used by other industrial practitioners, we adopt the same validation procedure, which may be summarized as follows:

1. For every individual in the holdout sample (regardless of whether they were originally in the treatment or control group), compute the predicted values of response probabilities for both the treatment and control by assigning `T[i]` = 1 or 0, respectively, and then create the predicted uplift score by taking the difference between the two estimated probabilities, as in Eqn. 6.1.
2. Rank the entire holdout sample by this score and derive the score-driven semideciles (i.e., 5% intervals) to provide sufficient granularity.
3. In each semidecile, calculate the observed response rates in the treatment group and control group respectively, and then take the observed difference (this is the actual or observed lift in each decile).
4. Plot the observed difference between treatment and control by decile to validate the model and graphically assess the model.
5. Compute relevant metrics to support model evaluation; this is discussed more fully below.

Step 4 is a simple graphical method proposed by [Lo (2002)](#chapter6.xhtml#ref6_8). Step 5 builds on suggestions made by [Kane et al. (2014)](#chapter6.xhtml#ref6_6), who used three metrics, obtained from holdout samples, related to how the models would likely perform in the next iteration of the marketing campaign. These metrics are (1) a “Gini” coefficient, (2) a “Gini top 15%,” and (3) a “Gini repeatability metric” (or `R²` of the lift chart). Each calls for some further explanation.

The Gini coefficient gives an estimate of the overall model fit. It measures the area between the gains curve – this measures the cumulative percent of responders and is the top curve in [Figure 6.9](#chapter6.xhtml#fig6_9) – and the population curve, shown by the straight line that gives the cumulative percent of population, sorted by decreasing size of uplift. For standard response models, the gains curve always rises. For lift models, however, the gains curve can rise (for positive lift) and fall (for negative lift, i.e., suppressed response). The Gini coefficient computation is described in [Appendix 6.2](#chapter6.xhtml#app6_2).

![Figure 6.9 Gains chart for uplift/true-lift models. ⏎](images/fig6_9.jpg)

Figure 6.9 Gains chart for uplift/true-lift models. [⏎](#chapter6.xhtml#b6fig6_9)

The Gini top 15% is another useful measure. For a campaign with an unlimited budget, the target population would include all candidates up to the point where the gains curve begins to fall (and uplift goes from positive to negative). However, many campaigns have limited budgets, in which case the gains for the initial deciles (say, deciles 1 and 2) are more important than the gains for the higher deciles. For this evaluation, we chose the Gini area for the top 15% of scorers as an example, since many campaigns target just Page 136 the top 1 or 2 deciles in practice; this is shown as the dark-shaded area to the left of [Figure 6.9](#chapter6.xhtml#fig6_9). One can use similar metrics such as Gini top 30% as a metric if the next campaign expects to target the top 3 deciles (30%) instead of the top 15%. The computational formula of Gini Top 15% is in [Appendix 6.2](#chapter6.xhtml#app6_2).
