# Basics: Gaussian Identities

Eq (1): joint from Marginal and Conditional: $p(x) \leftarrow p(y|x) \leftarrow p(x, y)$

$\mathcal{N}(x|\mu_x,\Sigma_x)\mathcal{N}(y|Fx, \Sigma_y) = \mathcal{N} \left( \left[ \begin{array}{c} x \ y \end{array} ight] \middle| \left[ \begin{array}{cc} \mu_x & \ F\mu_x & \end{array} \right] , \left[ \begin{array}{cc} \Sigma_x & \Sigma_x^T \ F\Sigma_x & \Sigma_y + F\Sigma_xF^T \end{array} \right] \right] \right)$

Eq (2): Marginal and Conditional Gaussian from Joint: $p(x,y) \rightarrow p(y|x),p(x)$

$\mathcal{N} \left( \left[ \begin{array}{c} x \ y \end{array} \right] \middle| \left[ \begin{array}{c} \mu_x \ \mu_y \ \end{array} \right] , \left[ \begin{array}{cc} \Sigma_x & C \ C^T & \Sigma_y \ \end{array} \right] \rightright) = \mathcal{N}(x|\mu_x,\Sigma_x)\mathcal{N}(y|\mu_y + C^T\Sigma_x^{-1}(x-\mu_x), \Sigma_y - C^T\Sigma_x^{-1}C)$

Can also be derived by "completing the square"...