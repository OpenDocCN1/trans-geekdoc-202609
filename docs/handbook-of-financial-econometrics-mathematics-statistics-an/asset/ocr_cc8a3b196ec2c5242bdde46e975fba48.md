In this depiction of the MIM, $I_j^*$ is the actual level of index $j$, while $b_{ij}^*$ is the actual responsiveness of security $i$ to index $j$. If the component of the security return is not related to any of the indexes, then this index model can be divided into two parts: (1) $a_i$, the expected value of the unique return, and (2) $c_i$ which represents the distribution of the random effect; $c_i$ has a mean effect of zero and a variance of $\sigma_{c_i}^2$.

This model can be utilized with multiple regression techniques, but if the indexes are unrelated to each other, the calculations would be made much simpler. This assumption reduces the number of calculations, as compared with the Markowitz full variance–covariance model, but is obviously more complex than the single-index model. To assure that the indexes are unrelated, the index variables can be orthogonalized (made uncorrelated) by completing inter-regressions on the indexes themselves.

Assume there is a hypothetical model that deals with two indexes:

$R_i = a_i^* + b_{i1}^* I_1^* + b_{i2}^* I_2^* + c_i.$  (81.22)

Suppose the indexes are the market index and an index of wholesale prices. If these two indexes are correlated, the correlation may be removed from either index.

To remove the relation between $I_1^*$ and $I_2^*$, the coefficients of the following equation can be derived by regression analysis:

$I_2^* = e_0 + e_1 I_1^* + d_i,$

where $e_0$ and $e_1$ are the regression coefficients, and $d_i$ is the random error term.

By the assumptions of regression analysis, $d_i$ is uncorrelated with $I_1$. Therefore,

$\hat{d}_i = I_2^* - (\hat{e}_0 + \hat{e}_1 I_1^*),$

which is an index of the performance of the sector index without the effect of $I_1$(the market removed). Defining

$I_2 = \hat{d}_i = I_2^* - \hat{e}_0 - \hat{e}_1 I_1^*,$

an index is obtained that is uncorrelated with the market. By solving for $I_2^*$ and substituting into equation (81.22),

$R_i = a_i^* + b_{i1}^* I_1^* + b_{i2}^* I_2 - b_{i2}^* \hat{e}_0 - b_{i2}^* \hat{e}_1 I_1^* + c_i.$

Rearranging,