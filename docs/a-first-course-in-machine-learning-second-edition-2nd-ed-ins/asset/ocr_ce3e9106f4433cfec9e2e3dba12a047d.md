First and second derivatives are:

\[ \frac{\partial \log p(\mathbf{x}|\boldsymbol{\mu}, \boldsymbol{\Sigma})}{\partial \boldsymbol{\mu}} = \boldsymbol{\Sigma}^{-1}\mathbf{x} - \boldsymbol{\Sigma}^{-1}\boldsymbol{\mu} \]

\[ \frac{\partial^2 \log p(\mathbf{x}|\boldsymbol{\mu}, \boldsymbol{\Sigma})}{\partial \boldsymbol{\mu}\partial \boldsymbol{\mu}^{\mathsf{T}}} = -\boldsymbol{\Sigma}^{-1}. \]

Therefore, the Fisher information is:

\[ \mathcal{F} = \boldsymbol{\Sigma}^{-1}. \]