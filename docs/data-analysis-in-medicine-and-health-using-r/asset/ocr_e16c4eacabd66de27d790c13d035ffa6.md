# 12.4 Analysis

# 12.4.7.1 Interpretation of the parameters is as follow:

The interpretation of the parameters is as follow:

+   - The estimated log ratio to die for every increment of 1 year of age was –0.0527. The Acceleration Factor (AF) or Time Ratio (TR) is exp(–0.0527) which equals 0.949. It means that for every 1 year increase in age, OA patients die earlier (a factor of 0.949). Or, we can say for every 1 year increase in age, the survival time for OA patients would be significantly shorter by 5.1% when adjusted for surgery and marital status. The reduction in survival in OA patients could range between 4.6% and 5.7% (Adj. TR=0.949, 95% CI=0.943, 0.954).

+   - The estimated log ratio to die in OA patients who underwent surgery (in comparison to those who did not) was 0.625. The Acceleration Factor (AF) or Time Ratio (TR) is exp(0.625) which equals 1.87. The survival time for OA patients who underwent surgery was estimated to be 1.87% longer than that of patients who did not undergo surgery. Or, it also means, the survival time among OA patients who underwent surgery was 87.0% longer than those who did not go for surgery, when adjusted for age and marital status. The increase of survival ranges between 51.0% and 131.0% (Adj. TR=1.87, 95% CI=1.51,2.31)

+   - The estimated log ratio to die in subjects who were single (in comparison to those who were married) –0.354. The Acceleration Factor (AF) or Time Ratio (TR) is exp(–0.354) which equals 0.702. The survival time for OA patients who were single, estimated to be about a factor of 70.2% than OA patients who were married. The survival time among OA patients who were single was shorter by 29.8%; when adjusted for surgery status and age. The survival shortened by 14.3% and 42.5% (Adj. TR=0.702, 95% CI=0.575,0.857).

+   - The estimated log ratio to die in subjects who were separated or divorced or widowed (in comparison to those who were married) –0.100. The Acceleration Factor (AF) or Time Ratio (TR) is exp(–0.100) which equals 0.905. This shows that the survival of OA patients who were separated or divorced or widowed was 90.5% as compared to OA patients who were married. The survival time in OA patients was shorter when adjusted for surgery status and age. The reduction is survival time ranged between 26.7% and 12.0% (Adj. TR=0.905, 95% CI=0.733,1.12).

# 12.4.8 Weibull (proportional hazard)

In contrast to AFT metric, the flexsurvreg() could convert the estimation for proportional hazard (PH) metric. Below, we will obtain the estimate for log hazard ratio and the hazard ratio with their 95% confidence intervals.