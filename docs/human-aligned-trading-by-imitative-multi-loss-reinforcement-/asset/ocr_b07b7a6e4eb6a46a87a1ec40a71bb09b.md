# Table 2

Ablation study on the impacts by loss weights ω_s and ω_n (as per Eq. (8)). Each cell represents a stock's average daily intra-day trading return averaged over all testing periods + standard deviation. We observe that, higher values of both ω_s and ω_n tend to produce better performance although weight values higher than 1.0 do not appear to consistently produce distinguishable performances.

|  | ω_s = 2.0 | ω_s = 1.6 | ω_s = 1.2 | ω_s = 0.8 | ω_s = 0.4 | BnH |
|---|---|---|---|---|---|---|
| AAPL | 0.171% + 1.552% | 0.134% + 1.674% | 0.037% + 1.673% | 0.096% + 1.535% | 0.106% + 1.663% | 0.049% + 1.690% |
| COST | 0.066% + 0.943% | 0.015% + 1.029% | 0.093% + 0.909% | 0.015% + 1.005% | -0.028% + 0.923% | -0.023% + 1.042% |
| DIS | 0.202% + 1.295% | 0.247% + 1.271% | 0.219% + 1.327% | 0.153% + 1.365% | 0.132% + 1.387% | 0.135% + 1.407% |
| JPM | -0.059% + 1.333% | 0.030% + 1.366% | -0.125% + 1.371% | -0.066% + 1.217% | -0.054% + 1.261% | -0.100% + 1.341% |
| NFLX | 0.294% + 2.812% | 0.324% + 2.758% | 0.205% + 2.780% | 0.266% + 2.775% | 0.158% + 2.792% | 0.198% + 2.849% |
| NVAX | -1.045% + 4.051% | -0.992% + 4.172% | -0.972% + 4.234% | -1.091% + 4.038% | -1.142% + 4.180% | -1.113% + 4.195% |
| NVTA | 0.241% + 2.933% | 0.231% + 2.974% | 0.223% + 2.963% | 0.166% + 2.851% | 0.158% + 2.909% | 0.105% + 2.994% |
| APPS | 0.399% + 3.946% | 0.263% + 3.941% | 0.404% + 3.949% | 0.352% + 3.972% | 0.410% + 3.958% | 0.279% + 4.008% |
| RUN | 1.490% + 2.814% | 1.532% + 2.779% | 1.548% + 2.855% | 1.414% + 2.967% | 1.394% + 2.809% | 1.417% + 2.939% |
| SFIX | -0.704% + 2.672% | -0.678% + 2.627% | -0.695% + 2.779% | -0.691% + 2.735% | -0.660% + 2.679% | -0.702% + 2.769% |
|  | ω_n = 2.0 | ω_n = 1.6 | ω_n = 1.2 | ω_n = 0.8 | ω_n = 0.4 | BnH |
| AAPL | 0.145% + 1.571% | 0.153% + 1.538% | 0.186% + 1.558% | 0.117% + 1.628% | 0.172% + 1.704% | 0.049% + 1.690% |
| COST | 0.057% + 0.986% | 0.085% + 0.939% | -0.017% + 1.081% | -0.053% + 1.004% | -0.056% + 1.039% | -0.023% + 1.042% |
| DIS | 0.243% + 1.323% | 0.194% + 1.324% | 0.219% + 1.432% | 0.114% + 1.279% | 0.130% + 1.286% | 0.135% + 1.407% |
| JPM | -0.096% + 1.356% | 0.051% + 1.276% | -0.070% + 1.368% | -0.082% + 1.220% | -0.103% + 1.352% | -0.100% + 1.341% |
| NFLX | 0.170% + 2.809% | 0.199% + 2.839% | 0.329% + 2.738% | 0.193% + 2.821% | 0.162% + 2.845% | 0.198% + 2.849% |
| NVAX | -0.985% + 4.050% | -1.035% + 4.170% | -1.017% + 4.079% | -1.076% + 4.066% | -1.126% + 4.204% | -1.113% + 4.195% |
| NVTA | 0.207% + 2.989% | 0.191% + 2.862% | 0.190% + 2.879% | 0.098% + 2.972% | 0.066% + 2.889% | 0.105% + 2.994% |
| APPS | 0.405% + 3.851% | 0.423% + 3.906% | 0.370% + 3.873% | 0.316% + 3.979% | 0.385% + 4.022% | 0.279% + 4.008% |
| RUN | 1.387% + 2.814% | 1.521% + 2.862% | 1.470% + 2.845% | 1.453% + 2.857% | 1.545% + 2.945% | 1.417% + 2.939% |
| SFIX | -0.587% + 2.748% | -0.693% + 2.678% | -0.545% + 2.787% | -0.698% + 2.638% | -0.664% + 2.784% | -0.702% + 2.769% |

hence, incurs less trading cost which contributes to better cumulative returns. This behaviour is commonly observed when running tests on these five small-cap stocks.

# 5.4. Ablation studies

Since the HAT model is an integration of multiple modelling features and multiple loss components, we conduct additional experiments to gain understanding on the contribution by key components. First, we look at how the model performs under different weightings for the n-step Q loss ω_n and the supervised loss on trading actions ω_s with the 1-step Q loss ω being set to 1 as explained in Section 3.6. We assign one of 0.4, 0.8, 1.2, 1.6, and 2.0 to each of the weight parameters and execute the same testing routines as used in Section 5.3. We make a conscious decision of setting an upper limit of 2.0 because we do not want any loss to dominate over others. The results are presented in Table 2. We observe that applying a higher weighting to either ω_n or ω_s consistently contributes to an improved trading performance compared to a buy-and-hold strategy. Small weights of ω_n and ω_s do benefit the results but we do not consistently observe this. This result corroborates our design principles of wanting to incorporate both loss components which we theorise in earlier sections. We also observe that setting the parameters to 1.2, 1.6, and 2.0 does not appear to bring along a performance that is materially different. We present in Fig. 5 two actual intra-day returns when trading Apple Inc over two different days by changing the values of ω_n and ω_s, respectively. It is possible that the impact on the combined loss might change if we were to continue increasing the value of these two weightings, but, in the current study, we want to focus on presenting a balanced human-aligning model. We settle on the value of 1.2 for both parameters in our final design.

Next, we assess the impact of different values of n in the n-step loss. Again, without going with out-sized values, we test n ∈ [3, 6, 9, 12, 15] and evaluate the model's trading return and return variance by running the same testing routines as used in Section 5.3. The summary results are in Table 3. The result appears to show that there is no clear winner choosing one of 9, 12, or 15, but all perform better than the other two smaller values. We settled to use n = 12 in our final performance testing. We provide an example intra-day returns on Costco using one of these 5 values of n in Fig. 6 for demonstration purpose. Despite these findings, we believe that a principled way for choosing the step size n is still needed and dynamically tuning n during the course of learning may be a suitable addition to the process, something we will look into to introduce in the next research phase of this topic.

![](bbox=[0.55, 0.45, 0.95, 0.6])

(a) Day-trading Apple on 20 Aug 2020 with changing values of ω_n

![](bbox=[0.55, 0.65, 0.95, 0.8])

(b) Day-trading Apple on 21 Aug 2020 with changing values of ω_s

Fig. 5. Example intra-day trading returns (y-axis) demonstrating the changing impacts by ω_n and ω_s. The x-axis represents minutes. We observe better performances when these weight parameters are set above 1.0 while no obvious further gains are observed going up to 2.0 (the self-imposed upper limit).

# 6. Conclusion

We have identified RL as a suitable candidate in financial algorithmic trading thanks to its ability of self-learning, online learning