# 6. Conclusions and Recommendations

This study explores the capabilities of regression algorithms to predict two-phase flow parameters. The mean void fractions and structure velocities of intermittent flow patterns at varying gas and liquid superficial velocities, liquid viscosities and densities, and pipe inclination were predicted using multiple linear regression, polynomial regression, random forest, support vector regression, and deep neural network. For both parameters, the MLR predicted the target variables with the least accuracy, thus suggesting that the relationship between the two-phase parameters and flow variables are complex and cannot be adequately modelled using a linear relationship. Although all other ML models show a similar performance, RF and DNN show the best result with reference to the statistical error parameters considered in this study. A cross plot of the predicted results shows that majority of the data aligns within 20% of the corresponding test data. The ML predictive models were validated by comparing the performance with well-established correlations. All the ML models, except MLR, outperform the traditional empirical correlations considered in this study by at least 8% of the RMSE, APPE, APE, or R².

In this study, the ML models were evaluated using test data having the same configurations as the training data set. The authors suggest that future work should explore validation data from other sources to adequately validate the ML models, account for overfitting tendencies, and enable optimal hyperparameters tuning to optimize the versatility and generalization of these regression models. Furthermore, utilizing ML libraries to evaluate feature importance should be considered. This technique quantifies the contribution of each flow variable on the ML model and by extension, the magnitude of its influence on the two-phase flow parameter which is challenging to capture using the traditional correlation approach.

# Nomenclature

| Symbol | Description |
|--------|-------------|
| A | area of pipe |
| C_d | drift coefficient |
| C_o | distribution coefficient |
| D | diameter of the pipe |
| g | acceleration due to gravity |
| Re | Reynolds number |
| U_d | drift velocity |
| U_m | mixture velocity |
| U_TB | translational velocity |
| x | quality |
| θ | pipe inclination |
| ε | void fraction |
| σ | Surface tension |
| ρ_L | liquid density |
| ρ_G | gas density |
| μ_G | gas viscosity |
| μ_L | liquid viscosity |