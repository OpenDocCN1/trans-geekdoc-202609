

$$
\\text{KL}(p_{1}||p_{2}) = \\frac{1}{2}\\left\\lbrack {(\\mathbf{\\mu}_{2} - \\mathbf{\\mu}_{1})}^{T}\\Sigma_{2}^{- 1}(\\mathbf{\\mu}_{2} - \\mathbf{\\mu}_{1}) + \\text{trace}\\left\\{ \\Sigma_{2}^{- 1}\\Sigma_{1} \\right\\} - \\ln\\frac{|\\Sigma_{1}|}{|\\Sigma_{2}|} - l \\right\\rbrack,
$$

![Equation](images/B9780443292385000251/si552.png)(19.64)

*   其中 $|\\cdot|$ 表示相应的行列式。现在让我们做一个简化假设，这稍后也将很有用。假设反向路径中条件分布的协方差矩阵是对角的、预先固定的且独立于 `$\\boldsymbol{\\theta}$`，例如，

$$\\boldsymbol{\\Sigma}_{\\boldsymbol{\\theta}}(\\mathbf{x}[t], t) = \\sigma[t]^{2}\\mathbf{I}.$$

![Equation](images/B9780443292385000251/si554.png)(19.65)

*   然后，很容易看出结合公式 [(19.66)](#Chp019_997-1102_B9780443292385000251.xhtml#deq140)、[(19.68)](#Chp019_997-1102_B9780443292385000251.xhtml#deq142) 和 [(19.69)](#Chp019_997-1102_B9780443292385000251.xhtml#deq143)，我们得到

