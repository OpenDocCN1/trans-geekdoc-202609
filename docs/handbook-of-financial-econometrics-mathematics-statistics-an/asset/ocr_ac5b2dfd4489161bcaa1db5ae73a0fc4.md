likely to renegotiate.⁶ To test their hypotheses, Rodano *et al.* (2016) implement a DID research design by estimating the following model⁷:

$Y_{ijt} = \text{Constant} + \alpha\,\text{Exposed}_i + \beta\,(\text{Exposed}_i \times \text{After Reorganization}_t)$

$\qquad\qquad + \gamma\,(\text{Exposed}_i \times \text{Interim Period}_t) + \delta\,(\text{Exposed}_i \times \text{After Liquidation}_t)$

$\qquad\qquad + \cdots + \text{Quarter} \times \text{Year} + \varepsilon_{ijt},$

where $Y_{ijt}$ represents the interest rate on the loan issued by bank, $j$, to firm, $i$, at time, $t$ (interaction between quarter and year). Exposedᵢ is a dummy variable dividing the sample into two subgroups based on the value of the firm’s score (e.g., *Score*, 1–9), which measures the probability of a firm defaulting. A higher score indicates a greater probability of default; as such, the treatment group (with *Score* of 5–9) is more sensitive to legal reforms (treatments) than the control group (with *Score* of 1–4). The interaction terms between the exposure and reform indicators (After Reorganization and After Liquidation) measure the impact of each legal reform on loan interest rates. The coefficient of the interaction (Exposedᵢ × After Reorganizationₜ), β, is the DID estimate for the impact of reorganization reform, which measures the differences in the interest rates between the two groups in the post-reorganization period compared to in the pre-reorganization period. Rodano *et al.* (2016) predict β to be positive. The coefficient of the interaction (Exposedᵢ × After Liquidationₜ), δ, is the DID estimate for the impact of liquidation reform, which is expected to be negative.

Table 124.2 shows that the results (OLS regression estimated coefficients and firm-clustered standard errors in the parentheses) are consistent with their predictions.

The research design of Rodano *et al.* (2016) is more like a quasi-experiment than a natural-experiment because the members of treatment group were not randomly selected. Therefore, it is important to hold the aforementioned assumptions when drawing a causal inference for their results. Figure 124.2 shows that the parallel trend assumption, the most important assumption that needs to make a causal inference, holds in their setting.⁸ Their sample selection procedure does not show any violation of

⁶ The debtors who are more likely to default are also the ones who are more likely to renegotiate to avoid default and are expected to be more sensitive to the reforms.

⁷ Interested readers could also look at Autor (2003) for the generalized DID application on testing the influence of “unjust dismissal” on the US Temporary Help Services (THS) employment.

⁸ Using figures/graphs/plots to check if the parallel assumption holds has been widely used in the DID design applied to social sciences research (e.g., Cerqueiro, Ongena, and Roszbach, 2016; Qin and Ronen, 2018).