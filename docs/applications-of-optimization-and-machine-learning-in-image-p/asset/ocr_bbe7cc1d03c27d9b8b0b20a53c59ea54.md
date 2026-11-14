where \(\boldsymbol{w}_{ud} = (\boldsymbol{v}(i, j), \mu(i, j))^T, \mathcal{I}^{(n)} = \left(\mathcal{I}_{\mu}^{(n)}, \mathcal{I}_{v}^{(n)}\right)^T\) ,

\(\mathcal{I}_{\mu}^{(n)} = \left( \frac{1}{\psi \left( \nabla \mathcal{J}^T \boldsymbol{w}^{(n)} + \mathcal{J}_{\mathcal{T}} \right)} \mathcal{J}_{\mathcal{X}} + 2\beta^2 + 2\lambda \sum_{(\bar{i}, \bar{j}) \in \varphi(i, j)} \omega_{p_y}^{(\alpha)} \right)^{-1}\)

and \(\mathcal{I}_{v}^{(n)} = \left( \frac{1}{\psi \left( \nabla \mathcal{J}^T \boldsymbol{w}^{(n)} + \mathcal{J}_{\mathcal{T}} \right)} \mathcal{J}_{\mathcal{Y}} + 2\beta^2 + 2\lambda \sum_{(\bar{i}, \bar{j}) \in \varphi(i, j)} \omega_{p_y}^{(\alpha)} \right)^{-1}\) . An outer

fixed point iteration technique is utilized in converting this nonlinear system into a linear system of equations. Further, Gauss–Seidel method [42, 43] is employed for solving the resulting linear system. The pseudo-code of the fractional order optical flow estimation algorithm is given as Algorithm 1 and illustrated in Figure 10.2.

```
Algorithm 1: Fractional order optical flow estimation algorithm
Input: \(\mathcal{J}_1, \mathcal{J}_2\) (reference and target image frames), \(\alpha, \beta, \lambda, W, N_{warp}, N_{pyr}\) and \(N_{it}\)
Output: Optical flow field \(\boldsymbol{w} = (\mu, \nu)\)
Set up image pyramids \(\mathcal{J}_1^{pyr(k)}\) and \(\mathcal{J}_2^{pyr(k)}\)
for \(k = N_{pyr}-1\) to 0 do
    \(\mathcal{J}_1 = \mathcal{J}_1^{pyr(k)}, \mathcal{J}_2 = \mathcal{J}_2^{pyr(k)}\);
    if \(k == N_{pyr}-1\) then
        Set \(\boldsymbol{w} = \mathbf{0}\);
    else
        Upsample \(\mu, \nu\) to the current level;
    if \(k \neq N_{pyr}-1\) then
        Update \(\mathcal{J}_1 = warping(\mathcal{J}_1, \boldsymbol{w})\);
    Initialize \(\delta\boldsymbol{w}\) to zero with \(size == size(\mathcal{J}_1)\);
    for \(w = 1\) to \(N_{warp}\) do
        Compute \(\mathcal{J}_{\mathcal{X}}\), \(\mathcal{J}_{\mathcal{Y}}\) and \(\mathcal{J}_{\mathcal{T}}\), using \(\mathcal{J}_1\) and \(\mathcal{J}_2\);
        for \(it = 1\) to \(N_{it}\) do
            Compute fractional order derivatives of order \(0 < \alpha < 1\) of \(\delta\boldsymbol{w}\);
            Update \(\delta\boldsymbol{w}\) using Eq. 21;
        Update \(\boldsymbol{w} = \boldsymbol{w} + \delta\boldsymbol{w}\);
        Update \(\mathcal{J}_1 = warping(\mathcal{J}_1, \delta\boldsymbol{w})\);
        Initialize \(\delta\boldsymbol{w}\) to zero;
```