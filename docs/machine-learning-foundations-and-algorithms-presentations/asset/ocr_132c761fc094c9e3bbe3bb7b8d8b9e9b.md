# Basics: Gaussian Identities

+   - Eq (1): Joint from Marginal Conditional: $p(x),p(y|x) ightarrow p(x,y)$
$\mathcal{N}(x|\mu_{oldsymbol{x}}, \Sigma_{oldsymbol{x}})\mathcal{N}(y|Foldsymbol{x}, \Sigma_{oldsymbol{y}}) = \mathcal{N}\left(\left[egin{array}{c} x \ y \end{array}ight] \middle| \left[egin{array}{c} \mu_{oldsymbol{x}} \ F\mu_{oldsymbol{x}} \end{array}ight], \left[egin{array}{cc} \Sigma_{oldsymbol{x}} & \Sigma_{oldsymbol{x}}F^T \ F\Sigma_{oldsymbol{x}} & \Sigma_{oldsymbol{y}} + F\Sigma_{oldsymbol{x}}F^T \end{array}ight]ight)$

+   - Eq (2): Marginal and Conditional Gaussian from Joint: $p(x,y) ightarrow p(y|x), p(x|y)$
$\mathcal{N}\left(\left[egin{array}{c} x \ y \end{array}ight] \middle| \left[egin{array}{c} \mu_{oldsymbol{x}} \ \mu_{oldsymbol{y}} \end{array}ight], \left[egin{array}{cc} \Sigma_{oldsymbol{x}} & C^T \ C & C^T\Sigma_{oldsymbol{x}}C \end{array}ight]ight) = \mathcal{N}(x|\mu_{oldsymbol{x}}, \Sigma_{oldsymbol{x}})\mathcal{N}(y|\mu_{oldsymbol{y}} + C^T\Sigma_{oldsymbol{x}}^{-1}(x-\mu_{oldsymbol{x}}), \Sigma_{oldsymbol{y}}-C^T\Sigma_{oldsymbol{x}}^{-1}C)$

Can also be derived by “completing the square”...