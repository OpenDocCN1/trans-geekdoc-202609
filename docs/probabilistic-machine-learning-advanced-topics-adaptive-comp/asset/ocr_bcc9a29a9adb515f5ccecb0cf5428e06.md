matrix of responses (with each row being an output variable and each column being an observation), and \(\mathbf{E} = [e_1, \cdots, e_n]\) is the matrix of residual errors, where \(e_i \stackrel{iid}{\sim} \mathcal{N}(\mathbf{0}, \Sigma)\). It can be seen from the definition that given \(\Sigma\), \(\mathbf{W}\) and \(\mathbf{X}\), columns of \(\mathbf{Y}\) are independently random variables following multivariate normal distributions. So the likelihood of the observation is

\(p(\mathbf{Y}|\mathbf{W}, \mathbf{X}, \Sigma) = \frac{1}{(2\pi)^{N_y \times N} |\Sigma|^{N/2}} \exp \left( \sum_{i=1}^N - \frac{1}{2} (\mathbf{y}_i - \mathbf{W}\mathbf{x}_i)^\top \Sigma^{-1} (\mathbf{y}_i - \mathbf{W}\mathbf{x}_i) \right)\) (15.106)

\(= \frac{1}{(2\pi)^{N_y \times N} |\Sigma|^{N/2}} \exp \left( - \frac{1}{2} \text{tr} \left( (\mathbf{Y} - \mathbf{W}\mathbf{X})^\top \Sigma^{-1} (\mathbf{Y} - \mathbf{W}\mathbf{X}) \right) \right)\) (15.107)

\(= \mathcal{MN}(\mathbf{Y}|\mathbf{W}\mathbf{X}, \Sigma, \mathbf{I}_{N \times N}),\) (15.108)

The conjugate prior for this is the matrix normal inverse Wishart distribution,

\(\mathbf{W}, \Sigma \sim \text{MNIW}(\mathbf{M}_0, \mathbf{V}_0, \nu_0, \mathbf{\Psi}_0)\) (15.109)

where the MNIW is defined by

\(\mathbf{W}|\Sigma \sim \mathcal{MN}(\mathbf{M}_0, \Sigma_0, \mathbf{V}_0)\) (15.110)

\(\Sigma \sim \text{IW}(\nu_0, \mathbf{\Psi}_0),\) (15.111)

where \(\mathbf{V}_0 \in \mathbb{R}_{++}^{N_x \times N_x}, \mathbf{\Psi}_0 \in \mathbb{R}_{++}^{N_y \times N_y}\) and \(\nu_0 > N_x - 1\) is the degree of freedom of the inverse Wishart distribution.

The posterior distribution of \(\{\mathbf{W}, \Sigma\}\) still follows a matrix normal inverse Wishart distribution.

We follow the derivation in [Fox09, App.F]. Tthe density of the joint distribution is

\(p(\mathbf{Y}, \mathbf{W}, \Sigma) \propto |\Sigma|^{-(\nu_0 + N_y + 1 + N_x + N)/2} \times \exp \left\{ - \frac{1}{2} \text{tr}(\mathbf{\Omega}_0) \right\}\) (15.112)

\(\mathbf{\Omega}_0 \triangleq \mathbf{\Psi}_0 \Sigma^{-1} + (\mathbf{Y} - \mathbf{W}\mathbf{X})^\top \Sigma^{-1} (\mathbf{Y} - \mathbf{W}\mathbf{X}) + (\mathbf{W} - \mathbf{M}_0)^\top \Sigma^{-1} (\mathbf{W} - \mathbf{M}_0) \mathbf{V}_0\) (15.113)

We first aggregate items including \(\mathbf{W}\) in the exponent so that it takes the form of a matrix normal distribution. This is similar to the "completing the square" technique that we used in deriving the conjugate posterior for multivariate normal distributions in Section 3.4.4.3. Specifically,

\(\text{tr} \left[ (\mathbf{Y} - \mathbf{W}\mathbf{X})^\top \Sigma^{-1} (\mathbf{Y} - \mathbf{W}\mathbf{X}) + (\mathbf{W} - \mathbf{M}_0)^\top \Sigma^{-1} (\mathbf{W} - \mathbf{M}_0) \mathbf{V}_0 \right]\) (15.114)

\(= \text{tr} \left( \Sigma^{-1} [(\mathbf{Y} - \mathbf{W}\mathbf{X})(\mathbf{Y} - \mathbf{W}\mathbf{X})^\top + (\mathbf{W} - \mathbf{M}_0)\mathbf{V}_0 (\mathbf{W} - \mathbf{M}_0)^\top] \right)\) (15.115)

\(= \text{tr} \left( \Sigma^{-1} [\mathbf{W} \mathbf{S}_{xx} \mathbf{W}^\top - 2 \mathbf{S}_{yx} \mathbf{W}^\top + \mathbf{S}_{yy}] \right)\) (15.116)

\(= \text{tr} \left( \Sigma^{-1} [(\mathbf{W} - \mathbf{S}_{yx} \mathbf{S}_{xx}^{-1}) \mathbf{S}_{xx} (\mathbf{W} - \mathbf{S}_{yx} \mathbf{S}_{xx}^{-1})^\top + \mathbf{S}_{y|x}] \right).\) (15.117)

where

\(\mathbf{S}_{xx} = \mathbf{X}\mathbf{X}^\top + \mathbf{V}_0, \qquad \mathbf{S}_{yx} = \mathbf{Y}\mathbf{X}^\top + \mathbf{M}_0 \mathbf{V}_0,\) (15.118)

\(\mathbf{S}_{yy} = \mathbf{Y}\mathbf{Y}^\top + \mathbf{M}_0 \mathbf{V}_0 \mathbf{M}_0^\top, \qquad \mathbf{S}_{y|x} = \mathbf{S}_{yy} - \mathbf{S}_{yx} \mathbf{S}_{xx}^{-1} \mathbf{S}_{yx}^\top.\) (15.119)