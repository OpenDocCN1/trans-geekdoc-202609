been devised that are model selection consistent (see e.g., [BG11; HTW15]).

# 11.5.7 Group lasso

In standard ℓ₁ regularization, we assume that there is a 1:1 correspondence between parameters and variables, so that if ŵ_d = 0, we interpret this to mean that variable d is excluded. But in more complex models, there may be many parameters associated with a given variable. In particular, each variable d may have a vector of weights w_d associated with it, so the overall weight vector has block structure, w = [w₁, w₂, …, w_D]. If we want to exclude variable d, we have to force the whole subvector w_d to go to zero. This is called group sparsity.

# 11.5.7.1 Applications

Here are some examples where group sparsity is useful:

+   - Linear regression with categorical inputs: If the d’th variable is categorical with K possible levels, then it will be represented as a one-hot vector of length K (Sec. 10.4.1), so to exclude variable d, we have to set the whole vector of incoming weights to 0.
+   - Multinomial logistic regression: The d’th variable will be associated with C different weights, one per class (Sec. 10.3), so to exclude variable d, we have to set the whole vector of outgoing weights to 0.
+   - Neural networks: the k’th neuron will have multiple inputs, so if we want to “turn the neuron off”, we have to set all the incoming weights to zero. This allows us to use group sparsity to learn neural network structure (for details, see e.g., [GEH19]).
+   - Multi-task learning: each input feature is associated with C different weights, one per output task. If we want to use a feature for all of the tasks or none of the tasks, we should select weights at the group level [OTJ07].

# 11.5.7.2 Penalizing the two-norm

To encourage group sparsity, we partition the parameter vector into G groups, w = [w₁, …, w_G]. Then we minimize the following objective

PNLL(w) = NLL(w) + λ Σ_{g=1}^G ||w_g||₂   (11.114)

where ||w_g||₂ = √{Σ_{d∈g} w_d²} is the 2-norm of the group weight vector. If the NLL is least squares, this method is called group lasso [YL06; Kyu+10].

Note that if we had used the sum of the squared 2-norms in Eq. (11.114), then the model would become equivalent to ridge regression, since

Σ_{g=1}^G ||w_g||₂² = Σ_g Σ_{d∈g} w_d² = ||w||₂²   (11.115)