the changes in both the treated and control groups in the post-treatment period. The coefficient β₂ measures any change in the outcome that is not due to the implementation of the treatment. Lastly, e is the error term.

# 124.1.2.2 General settings for DID analysis: Multiple groups and time periods

The DID method can be extended to more groups and time periods.

Assuming that the treatment (policy) has the same effect on subjects every year, we can add a full set of time dummies to equation (124.1). If we relax this assumption, we can include a full set of dummies for each of the two groups and all time periods and pairwise interactions. Then, a treatment (policy) indicator (or continuous) variable can be used to measure the effects of the treatment (policy). Readers could refer a more detailed discussion on its application to Meyer (1995).

Drawing from a general framework provided by Bertrand, Duflo, and Mullainathan (2004), the below equation (124.2) expresses the DID application for multiple groups and periods:

$Y_{igt} = A_t + B_g + X_{gt}\beta + Z_{igt}\gamma_{gt} + v_{gt} + u_{igt}, \quad (124.2)$

where i indicates individual, g indicates group, and t indicates time. In this model, A_t estimates the time effects and B_g estimates the group effects. X_gt represents the covariates between group and time, Z_igt denotes the individual specific covariates, v_gt symbolizes unobserved group and time effects, and u_igt signifies individual-specific errors. The coefficient of interest is β.

In the case of cluster sample, we can rewrite equation (124.2) as equation (124.3):

$Y_{igt} = \delta_{gt} + Z_{igt}\gamma_{gt} + u_{igt}, \quad i = 1, \dots, M_{gt}. \quad (124.3)$

Equation (124.3) shows a model at the individual level, in which both the intercepts and slopes can differ across all (g, t) pairs. Then, we estimate δ_gt at the group/time period level, using the below equation (124.4):

$\delta_{gt} = A_t + B_g + X_{gt}\beta + v_{gt}. \quad (124.4)$

Presuming that the individual-level observations are independent, we can estimate (124.5) and ignore v_gt (we assume that v_gt is independent across g). Then, we can estimate δ_gt using OLS at the individual-level, assuming that E(Z'_igt u_igt) = 0 and the group/time sizes, M_gt, are large (Bertrand et al., 2004, Greene, 2008).

$\hat{\delta}_{gt} = A_t + B_g + X_{gt}\beta + v_{gt}. \quad (124.5)$