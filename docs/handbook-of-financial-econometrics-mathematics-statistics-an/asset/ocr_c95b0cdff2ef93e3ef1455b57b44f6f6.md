This step results in an estimate of the implied spot variance and the structural parameter values, for date t. Go back to Step 1 until the two steps have been repeated for each day in the sample.

# 51.4.1.3.2 Implied parameters and in-sample pricing fit

Before proceeding to the model comparison, we first preset the comparison between the unrestricted and the restricted (β ≥ 0) CEV model as follows:

| Category | Model | Observation | Beta | SSE | Implied volatility |
|---|---|---|---|---|---|
| All options | Unrestricted CEV | 50.9735 | -2.9290 | 23.9336 | 0.1964 |
|  | Restricted CEV |  | 0.0031 | 50.1240 | 0.2015 |
| Short-term options | Unrestricted CEV | 19.4066 | -4.4277 | 4.6479 | 0.2021 |
|  | Restricted CEV |  | 0.0158 | 9.5121 | 0.2118 |
| At-the-money options | Unrestricted CEV | 13.9563 | -2.7787 | 3.5062 | 0.1852 |
|  | Restricted CEV |  | 0.1316 | 4.9300 | 0.1856 |

From the testing results above, we find that out the pricing performance of the unrestricted CEV model is clearly superior to the restricted CEV model. The average daily square sum of dollar pricing error (SSE) of the unrestricted CEV model is smaller than the restricted CEV model in all of the categories we tested. This is consistent with the findings of Jackwerth and Rubinstein (2001). In addition, the elasticity parameter β is less than two, which confirms the negative correlation between index level and volatility. Thus, in this chapter hereafter, we only use the unrestricted CEV model throughout all of the empirical tests.

As shown in Table 51.1, we compare the testing results of the CEV model with those of the BS, the SV, the SVSI, and the SVJ models obtained by Bakshi et al. (1997). In the all-option category, the SSE of the CEV model is lower than that of the BS model, but higher than those of the SV, the SVSI, and the SVJ models. However, in short-term options category, the CEV model has lower SSE than the those of SV and the SVSI models, only higher than the SSE of the SVJ model. Furthermore, the CEV model performs best even better than the SVJ model in at-the-money options category.

# 51.4.1.4 Assessment of the relative model misspecification

As Rubinstein (1985) had done, the most popular diagnostic of relative model misspecification is to compare the implied-volatility patterns of each model