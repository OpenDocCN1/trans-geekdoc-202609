
## Table 126.3: Ranks of different variables in terms of three different discriminant functions.

| Variable | Function 1 Y₁ | Function 2 Y₂ | Function 3 Y₃ |
|---|---|---|---|
| X₁ | 1 | 6 | 2 |
| X₂ | 2 | 2 | 5 |
| X₃ | 3 | 3 | 1 |
| X₄ | 6 | 1 | 6 |
| X₅ | 5 | 4 | 4 |
| X₆ | 4 | 5 | 3 |

significantly different, the six variables entering the final MDA model can be examined. The individual discriminating ability of each of the variables and their rank of importance in the three discriminant functions was defined in equation 126.8 and are now presented as follows.

Table 126.3 indicates the relative importance of each variable for different discriminant functions. For example, variable 1 is most important in discriminant function 1, however it is least important in discriminant function 2. In addition, variable 1 is the second most important in discriminant function 3.

The MDA model correctly rated 92 of the 132 bonds in the original sample, which corresponds to a correct prediction rate of 69.7 percent; this is analogous to the coefficient of determination (R²) in regression analysis. If an analyst were interested only in the ability of the model to predict ratings within one classification (either higher or lower) of the actual rating, the model performed very accurately, classifying all but two of the bonds within one rating of the actual rating.

In another test of validity, the model was applied to the holdout sample. With this group, the model correctly rated 31 of 48 bonds (64.58 percent) and rated all 48 bonds within one rating higher or lower than the actual rating. In order to further validate the MDA model, a stratified random sample of 48 companies issuing bonds during the first six months of 1969 was gathered. The MDA model (developed from a sample of newly rated bonds issued in 1967 and 1968) was employed to predict the ratings on the new bonds issued in 1969. Twenty-seven of the 48 bonds were rated correctly, indicating that the model possesses future predictive ability.

The subordination status of a corporate bond [represented by a binary (0-1) variable] appears to be the most important variable among those that were examined in this study. If one were interested only in rating bonds as investment quality (AA, A, and BAA) or noninvestment quality (BA and B),

the best single predictor is the subordinated status of the bond. Based on this variable alone, correct ratings (investment vs. noninvestment quality) would have occurred 88.6 percent of the time for the original sample (117/132) and 83.3 percent of the time for the holdout sample (40/48).

The model performed very poorly for BAA-rated bonds. An analysis of the multiple range tests indicated that the inability of the MDA model to accurately predict BAA-rated bonds appears to be due to a lack of statistically significant differences in the quantifiable variables included in the model. Overall, though, the model’s ability to discriminate between different bond rating is fairly good, and it shows potential for application to the prediction of future bond ratings.

There are two major technical differences between the methods and procedures used in this section and those used in Section 126.3. First, the MDA used in this section is a k-group instead of two-group analysis. Secondly, Pinches and Mingo’s MDA analysis is predictive instead of descriptive in nature. Joy and Tollefson (1974) argue that MDA can be used for either predictive or descriptive purposes. They regard Altman’s (1968) MDA application as a descriptive instead of a predictive analysis. This comment can also apply to both Sinkey’s and Trieschmann and Pinches’ (1973) MDA analysis. Other related arguments can be found in Joy and Tollefson (1978) and Altman and Eisenbeis (1978).

The financial-ratio-based credit-scoring model for bond rating system requires the maximization of two conflicting objectives (i.e., the explanatory and discriminatory power, simultaneously), which had not been directly addressed in the paper by Pinches (1973). Therefore, Kao and Lee’s (2012) paper has developed a hybrid multivariate credit-scoring model that combines the principal component analysis and Fisher’s discriminant analysis using the MINIMAX goal programming technique so that the maximization of the two conflicting objectives can be compromised. The performance of alternative credit-scoring models is analyzed and compared using dataset from previous studies. They found that the proposed hybrid credit-scoring model outperforms other alternative models in both explanatory and discriminatory powers.

For multiple-class prediction, a frequently used approach is based on ordered probit model. Hwang et al. (2008) show that this approach is not optimal in the sense that it is not designed to minimize the error rate of the prediction. Based upon the works by Altman (1968), Ohlson (1980), and Begley et al. (1996) on two-class prediction, Hwang et al. (2008) propose a modified ordered probit model. The modified approach depends on an

optimal cutoff value and can be easily applied in applications. An empirical study is used to demonstrate that the prediction accuracy rate of the modified classifier is better than that obtained from usual ordered probit model. In addition, we also show that not only the usual accounting variables are useful for predicting issuer credit ratings, market-driven variables and industry effects are also important determinants.

## 126.6 Ohlson’s and Shumway’s Methods for Estimating Default Probability¹

Beginning in the 1980s more complex estimation methods such as logit and probit were used to determine the likelihood of company bankruptcy. Logit model is a methodology that uses maximum likelihood estimation, or so-called conditional logit model. Two well-known models using logit models to estimate the probability of bankruptcy are Ohlson (1980) and Shumway (2001), which we will discuss next. Ohlson discusses the following econometric advantages of logit model over multivariate discriminant analysis (MDA) used for the development of Altman Z-score. MDA imposes certain statistical requirements on the distributional properties of the predictors, violation of which will result in invalid or poor approximations. For example, MDA assumes the same variance-covariance matrices of the predictors for both failed and non-failed group; it also requires normal distributions of failure predictors which bias against the use of indicator independent variables. Moreover, the output of MDA model is a score which has little intuitive interpretation. The matching procedure which is typically used in MDA technique can result in losing useful information such as losing meaningful predictors. The use of logistic regression, on the other hand, essentially overcomes the weaknesses of MDA discussed above.

Ohlson (1980) used data available prior to the date of bankruptcy to ensure the strict forecasting relationships. His sample included 105 bankruptcies and 2058 non-bankruptcies from the seventies (1970–1976). Among the 105 bankrupt firms, 8 firms are traded in New York Stock Exchange, 43 are traded in American Stock Exchange, and 54 are traded over-the-counter market or regional exchanges. Nine variables defined below are used to develop the logit model.

X₁ = Natural log of (Total Assets/ GNP Implicit Price Deflator Index).

The index assumes a base value of 100 for 1968;

X₂ = (Total Liabilities/Total Assets);
X₃ = (Current Assets − Current Liabilities)/Total Assets;
X₄ = Current Assets/Current Liabilities;
X₅ = One if total liabilities exceeds total assets, zero otherwise;
X₆ = Net income/total assets;
X₇ = Funds provided by operations/total liabilities;
X₈ = One if net income was negative for the last two years, zero otherwise; and
X₉ = (Net income in year t − Net income in t − 1) / (Absolute net income in year t + Absolute net income in year t − 1).

Three sets of coefficients are estimated using data one year prior to bankruptcy and/or two years prior to bankruptcy. Intuitively, the model with estimates computed using data one year prior to bankruptcy performs the best, which is expressed as follows:

Y = −1.32 − 0.407X₁ + 6.03X₂ − 1.43X₃ + 0.0757X₄ − 2.37X₅ − 1.83X₆ + 0.285X₇ − 1.72X₈ − 0.521X₉, (126.9)

where Y = log[P/(1 − P)], P = the probability of bankruptcy.

Thus, the probability of bankruptcy (P) is calculated as exp(Y)/[1 + exp(Y)], and the model becomes relatively easy to interpret.

Ohlson found that using a probability cutoff of 3.8 percent for classifying firms as bankrupt minimized Type I and Type II errors of the model presented in equation (126.9). At this probability cutoff point, the model correctly classified 87.6 percent of his bankrupt firm sample and 82.6 percent of the non-bankrupt firms. Begley et al. (1996) applied Ohlson's logit model (1980) to predict bankruptcy for a holdout sample of 65 bankrupt and 1300 non-bankrupt firms in the 1980s. They found substantially higher Type I and Type II error rates than those in the original studies. They re-estimated the coefficients for each model using data for a portion of their 1980s sample. However, they found no performance improvement for the re-estimated Ohlson Model.

The logit model used by Ohlson (1980) is single-period static logit model. Shumway (2001) employed a discrete hazard model or multiple-period dynamic logit model. The concept of discrete-time hazard model originates
