For performing the estimation of optical flow, the functional Eq. (10.5) needs to be minimized. Let \(\mu \equiv \mu(\mathcal{X}, \mathcal{Y})\) and \(\nu \equiv \nu(\mathcal{X}, \mathcal{Y})\) be two arbitrary functions such that the deviations \(\boldsymbol{w}\) from the desired optical flow solution \(\boldsymbol{w}^\star\) can be written as

\(\boldsymbol{w} = \boldsymbol{w}^\star + \epsilon \boldsymbol{\Phi}\) (10.6)

where \(\epsilon\) represents a real variable, and \(\boldsymbol{\Phi} = (\eta, \phi)^T\). Let us describe the Marchaud differentiation of Eq. (10.6) of order \(\alpha\) as follows:

\(D_+^\alpha \boldsymbol{w}^T = D_+^\alpha \boldsymbol{w}^\star^T + \epsilon D_+^\alpha \boldsymbol{\Phi}^T\) (10.7)

Substituting the right-hand sides of Eqs. (10.6) and (10.7) into the expression (10.5) and employing the definition of \(\psi\), the following variable scalar valued function is obtained:

\(E(\epsilon) = \int_\Omega \left[ \sigma \sqrt{1 + \left( \frac{\nabla \mathcal{J}^T (\boldsymbol{w}^\star + \epsilon \boldsymbol{\Phi}) + \mathcal{J}_\mathcal{I}}{\sigma} \right)^2} + \beta^2 (\boldsymbol{w}^\star + \epsilon \boldsymbol{\Phi})^T (\boldsymbol{w}^\star + \epsilon \boldsymbol{\Phi}) + \lambda e^T \left[ \left( D_+^\alpha \boldsymbol{w}^\star^T + \epsilon D_+^\alpha \boldsymbol{\Phi}^T \right) \odot \left( D_+^\alpha \boldsymbol{w}^\star^T + \epsilon D_+^\alpha \boldsymbol{\Phi}^T \right) \right] e \right] dX\) (10.8)

This function gives the required solution when \(\epsilon = 0\); therefore, the derivative of Eq. (10.8) with respect to \(\epsilon\) vanishes for \(\epsilon = 0\) [39].

\(0 = \int_\Omega \left[ \left\{ \frac{(\nabla \mathcal{J}^T \boldsymbol{w}^\star + \mathcal{J}_\mathcal{I}) (\nabla \mathcal{J}^T \boldsymbol{\Phi})}{\psi (\nabla \mathcal{J}^T \boldsymbol{w}^\star + \mathcal{J}_\mathcal{I})} \right\} + 2\beta^2 \boldsymbol{w}^\star^T \boldsymbol{\Phi} + 2\lambda \left\{ e^T \left( D_+^\alpha \boldsymbol{w}^\star^T \odot D_+^\alpha \boldsymbol{\Phi}^T \right) e \right\} \right] dX\) (10.9)

on applying the Fubini theorem [40], the theorem in [23] and the Marchaud derivative [37] on Eq. (10.9), we obtain

\(\int_\Omega e^T \left( D_+^\alpha \boldsymbol{w}^\star^T \odot D_+^\alpha \boldsymbol{\Phi}^T \right) e dX = \int_\Omega \left[ \left\{ \left( D_{-}^\alpha D_+^\alpha \right)^T e \right\} \boldsymbol{w}^\star \odot \boldsymbol{\Phi} \right] dX\) (10.10)