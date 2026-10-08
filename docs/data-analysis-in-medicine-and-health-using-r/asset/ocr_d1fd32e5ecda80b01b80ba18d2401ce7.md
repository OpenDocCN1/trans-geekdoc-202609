It is not recommended to adjust for every available Covariate because it has some practical drawbacks. The set of covariates it identifies can be far larger than needed for adequate confounding control (far from minimally sufficient) and may be clumsy for subsequent analyses; there be many covariates whose causal status (and thus their fulfillment of the criterion) is uncertain. Controlling too many variables by means can lead to or aggravate two related problems: (a) data sparsity, in which full control results in few subjects at crucial combinations of the variables, with consequent inflation of estimates, and (b) multicollinearity, by which we mean high correlation (or more generally, high association) of the controlled variables with study exposures (Greenland and Pearce, 2015).

# 14.4 Variable Selection for Prediction

Variable selection means choosing many variables to include in a particular model, that is, to select appropriate variables from a complete list of variables by removing those that are irrelevant or redundant. The purpose of such selection is to determine a set of variables that will provide the best fit for the model so that accurate predictions can be made (Chowdhury and Turin, 2020).

Chowdhury and Turin (2020) listed some variable selection methods:

+   - Backward elimination
- Forward selection
- Stepwise selection
- All possible subset selection



Backward elimination is the simplest of all variable selection methods. This method starts with a full model that considers all of the variables to be included in the model. Variables then are deleted one by one from the full model until all remaining variables are considered to have some significant contribution to the outcome. The variable with the smallest test statistic (a measure of the variable's contribution to the model) less than the cut-off value or with the highest p value greater than the cut-off value—the least significant—is deleted first. The model is refitted without the deleted variable and the test statistics or p values are recalculated. Again, the variable with the smallest test statistic or with the highest p value greater than the cut-off value is deleted in the refitted model. This process is repeated until every remaining variable is significant at the cut-off value. The cut-off value associated with the p value is sometimes referred to as 'p-to-remove' and does not have to be set at 0.05.