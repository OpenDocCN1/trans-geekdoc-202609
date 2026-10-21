
### Table 66.4: Quantile regression of firm value, social media and bank relationships.

| **Quantiles** | Q25 | Q50 | Q75 |
|---|---|---|---|
| **Social Media** |  |  |  |
| Facebook | 0.060*** (0.017) | 0.098*** (0.028) | 0.068 (0.045) |
| YouTube | -0.024 (0.036) | 0.053 (0.036) | 0.195** (0.079) |
| Twitter | -0.054 (0.064) | -0.133** (0.052) | -0.099 (0.129) |
| Others | 0.074** (0.038) | 0.088*** (0.030) | 0.055 (0.038) |
| **Bank Relationships** |  |  |  |
| BankRelationship | -0.006 (0.013) | -0.035*** (0.008) | -0.064*** (0.018) |
| BankDebt_TA | 0.478** (0.212) | 0.423*** (0.154) | 0.487*** (0.182) |
| **Firm Characteristics** |  |  |  |
| Age | -0.0003 (0.0005) | -0.003*** (0.0004) | -0.006*** (0.0007) |
| LnSize | -0.003 (0.007) | 0.002 (0.007) | 0.020* (0.011) |
| Intangible | 0.480*** (0.170) | 0.530 (0.389) | 1.546** (0.624) |
| SaleGrowth | -1.41e-06 (4.80e-06) | -2.24e-06 (2.02e-06) | -5.68e-06 (3.36e-06) |
| OCF_CL | 0.0006*** (0.0002) | 0.001*** (0.0002) | 0.002*** (0.0003) |
| CurrentRatio | -0.0001 (0.0001) | 3.18e-06 (0.0002) | 0.000354 (0.0003) |
| Leverage | -0.003*** (0.0009) | -0.003*** (0.001) | -0.008*** (0.001) |
| NWC_Assets | 0.118** (0.049) | 0.126** (0.060) | -0.083 (0.099) |
| Constant | 0.767*** (0.121) | 0.989*** (0.096) | 1.278*** (0.139) |
| Observations | 4,701 | 4,701 | 4,701 |
| R-squared | 0.0309 | 0.0437 | 0.0912 |

Notes: This table reports the quantile regression of firm value, social media and bank relationships. Columns 2-4 report the quantile regression results at quantiles 0.25, 0.5 and 0.75. All regressions include a full set of controls, as described in Appendix B. The standard errors of estimated coefficients are clustered by firm and displayed in parentheses. *, ** and *** represent the statistical significance at the 10%, 5% and 1% levels, respectively.

### 66.4.5 Endogeneity concerns of exogenous shocks

Facebook held its initial public offering (IPO) on May 18, 2012. The IPO was the biggest in technology and Internet history, with a peak market capitalization of over $104 billion. The IPO has immediate impacts on the stock price and would indirectly spread the effect over the related networks, such as users, investors and stakeholders. To solve this potential endogeneity problem resulting from the exogenous shock, we perform a DID method to identify the effects of the IPOs separately from the time-specific changes.

In a given year, some sample firms use Facebook to deliver information (treatment group), whereas other sample firms do not (control group). The two groups experience the same time-specific changes. Thus, differences in their Tobin's Q provide an estimate of the net effect of Facebook on the firm's value. A key assumption of the DID identification strategy is that the timing of Facebook's IPO is exogenous to the policies related to firm value. We believe that this assumption is appropriate for the following reason. When the company's listing is highly secure for users, firms are more willing to use Facebook to deliver information and mitigate information asymmetry. Investigating information asymmetry is economically important because it has implications on market valuation.

The DID analysis was centered on the event year 2012, where the first difference is between before and after the event and the second difference is between the usage and not usage of Facebook. We require sufficient observations for the two groups, with a dummy variable that equals one after the event or zero otherwise.

We suspect that the problem is that the changes in Tobin's Q might be systematically different across Facebook usage and that it is the bank relationship that differs rather than the timing factor (IPO). Specifically, we estimate a modified equation (66.3) based on equation (66.1) as follows:

Tobin's Q = β₀ + β₁ Facebook + β₂ After × Facebook + β₃ Bank Relationships × Facebook + β₄ After × Bank Relationships × Facebook + β₅ Bank Relationships + β₆ After + β₇ Firms Characteristics + εₜ. (66.3)

Table 66.5 reports the regression results from equation (66.3), with the clean estimates shown at the end of the table. This evidence helps us mitigate concerns that endogeneity might drive our results.

### Table 66.6: Summary of DID estimation.

| **Estimated Coefficient: ∂Tobin's Q/∂Facebook** | Before 2012 | After 2012 | Difference | t-value |
|---|---|---|---|---|
| Facebook without BankRelationship | 0.250 (β₁) | 0.066 (β₁ + β₂) | −0.184 (β₂) | −1.65* |
| Facebook with BankRelationship | 0.166 (β₁ + β₃) | 0.080 (β₁ + β₂ + β₃ + β₄) | −0.086 (β₂ + β₄) | −0.82 |
| Difference | −0.084 (β₃) | 0.014 (β₃ + β₄) | 0.098 (β₄) | 0.83 |

Notes: Clean effect (β₁ + β₃ + β₄) = 0.264 (isolated from direct effect of Facebook IPO 2012).

This table provides the summary of the DID estimation for a time comparison before and after 2012 between firms that use Facebook and firms that have bank relationships and those without. The model is presented using the following equation:

Tobin's Q = β₀ + β₁ Facebook + β₂ After × Facebook + β₃ Bank Relationship × Facebook + β₄ After × Bank Relationship × Facebook + β₅ After 2012 + β₆ Bank Relationship + β₇ Firms Characteristics + εₜ. (Equation (66.3))

The coefficient estimates for Facebook and After_Facebook are 0.25 and −0.184, which are significant. These results indicate that the net effect of use of FB on average increases Tobin's Q by 6.16% (= (0.25 − 0.184)/1.071) in the post-IPO period.

In this specification, β₁ captures the effect of Facebook on Tobin's Q for firm value before IPO, while β₁ + β₂ represents the net effect of using Facebook for firms in the post-IPO period; here, β₂ captures the marginal effects of the use of Facebook in the post-IPO period. As the Facebook IPO imposed an exogenous shock on the social media usage of firms, β₁ + β₂ + β₃ + β₄ captures all the effects of social media on firm value and the direct effects of post-IPO simultaneously. Hence, one would obtain the clean effect of social media (β₁ + β₃ + β₄) by subtracting the direct effects of post-IPO (β₂) from the combined effect (β₁ + β₂ + β₃ + β₄) using Facebook without bank relationships. Equation (66.5) of Table 66.6 provides a clean estimate of Facebook relative to firm value, which is 0.264 (β₁ + β₃ + β₄ = 0.25 − 0.084 + 0.098). Hence, the positive result is robust without the concern for endogeneity.

We also try to perform other informal financial reforms that might affect the banking relationships and the related firm value, and the results remain unchanged without concerns.

## 66.5 Conclusions

The usage of social media and establishing banking relationships are beneficial to firms. This chapter explores how social media and bank relationships mitigate information asymmetry and affect firm value. Using 855 listed Taiwanese firms and with 6,636 observations over the period 2008–2015, the following results are obtained.

- First, we find that Facebook, Google+ and LinkedIn positively influence firm value, whereas YouTube and Twitter affect firm value insignificantly. The use of Facebook contributes to Tobin's Q by 12.6%, whereas the use of Google+ and LinkedIn contribute to Tobin's Q by 9.3%.

- Second, the two measures of bank relationships affect firm value differently. While the higher number of banks firms borrow from reduces the value, high bank debt creates value. Interestingly, although one-unit increase in bank relationship reduces Tobin's Q by 2.24%, using Twitter may reverse the result and create value. Twitter and bank relationships are complementary. Again, although the use of YouTube does not affect value, the use of bank debt may reverse the result and add value to a firm. The use of YouTube and bank debt is complementary as well. Besides, substitution effects exist between other types of social media and banking relationships on firm value.

- Third, the use of Facebook, Google+ and LinkedIn adds value to a firm that was driven by firms that are having Tobin's Q at low to median quantiles. For those firms whose Tobin's Q are at high quantile, the results are insignificant.

- Fourth, the results remain robust after conducting a DID analysis where the exogenous shock of the Facebook IPO in 2012 is taken into consideration. The endogeneity concerns mostly dispel.

The social media has a function similar to that of banks in mitigating the information asymmetry between firms and outsiders; the information types vary. Banks create more soft and private information, while social media deliver more public and hard information. The accuracy of information is
