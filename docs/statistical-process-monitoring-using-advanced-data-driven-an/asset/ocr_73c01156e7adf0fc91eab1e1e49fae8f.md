# 3.1.2 Shortcomings of contribution plots/scores

A very common first approach to isolating the variables associated with a fault is to use contribution scores or plots that quantify the contribution of each variable to the monitoring statistic [11,12]. Then, those variables with the largest contribution are deemed shifted. With a small number of features and a single shifted variable, this approach is simple to implement and interpret, but it is not advisable for multiple reasons. First, contribution scores are subject to variable smearing. This occurs when variable i shifts, and its shift contaminates the contribution scores of all other variables. Secondly, even under IC conditions, the contributions of all variables are unequal, so misdiagnoses can occur when variables whose contributions are small under IC conditions still do not have the largest contribution in OC conditions.

We will show the variable smearing effect for the Q statistic, using notation adapted from [13]. First, the covariance of X is estimated with S = (1/(n-1))X'X. Then, principal component analysis (PCA) decomposes S as follows:

$$ \mathbf{S} = \mathbf{P}\mathbf{\Lambda}\mathbf{P}' + \tilde{\mathbf{P}}\tilde{\mathbf{\Lambda}}\tilde{\mathbf{P}}' = \hat{\mathbf{S}} + \tilde{\mathbf{S}}, $$

where \(\hat{\mathbf{S}} = \mathbf{P}\mathbf{\Lambda}\mathbf{P}'\); \(\tilde{\mathbf{S}} = \tilde{\mathbf{P}}\tilde{\mathbf{\Lambda}}\tilde{\mathbf{P}}'\); **P** is a matrix of size \(p \times l\) of eigenvectors termed principal loadings; \(\tilde{\mathbf{P}}\) is a matrix of size \(p \times (p-l)\) of eigenvectors termed residual loadings; \(l\) is the number of principal components (PCs) retained to explain the variability in **S**; and \(\mathbf{\Lambda}\) and \(\tilde{\mathbf{\Lambda}}\) are diagonal matrices containing the principal and residual eigenvalues, respectively. An individual measurement, \(\mathbf{x}_i\), can be rewritten as \(\mathbf{x}_i = \hat{\mathbf{x}}_i + \tilde{\mathbf{x}}_i = \mathbf{PP}'\mathbf{x}_i + \tilde{\mathbf{P}}\tilde{\mathbf{P}}'\mathbf{x}_i = \mathbf{Cx}_i + \tilde{\mathbf{C}}\mathbf{x}_i\), where \(\mathbf{C} = \mathbf{PP}'\) is the projection matrix into the principal component subspace (PCS), and \(\tilde{\mathbf{C}} = \tilde{\mathbf{P}}\tilde{\mathbf{P}}'\) is the projection matrix into the residual subspace (RS).

The Q statistic, also commonly known as the Squared Prediction Error (SPE), measures the goodness of fit in the lower dimensional model (i.e., \(l < p\)) via the squared norm of the residual vector, \(\tilde{\mathbf{x}}_i\), computed as

$$ Q = \|\tilde{\mathbf{x}}_i\|^2 = \mathbf{x}'_i\tilde{\mathbf{C}}\tilde{\mathbf{C}}\mathbf{x}_i = \mathbf{x}'_i\tilde{\mathbf{C}}\mathbf{x}_i = \|\tilde{\mathbf{C}}^{1/2}\mathbf{x}_i\|^2. $$

The contribution of a variable to the Q statistic is called that variable's *contribution score*, with variables with the largest contribution scores presumed to be those most likely to be shifted. The contribution scores for the Q statistic are

$$ c_j^Q = \left( \mathbf{d}'_j \tilde{\mathbf{C}} \mathbf{x}_i \right)^2 , $$

where \(\mathbf{d}_j\) is a vector of zeroes of length \(p\) except for a one in the \(j\)th row and is referred to as the direction vector.

Now, consider that variable \(j\) is shifted, resulting in a faulty measurement with \(\mathbf{x}_i = \mathbf{x}^*_i + \mathbf{d}_j\delta\), where \(\mathbf{x}^*_i\) is the fault-free part of the measurement, and \(\mathbf{d}_j\delta\) is the faulty part. The faulty part is composed of the fault direction, \(\mathbf{d}_j\), and \(\delta\) is