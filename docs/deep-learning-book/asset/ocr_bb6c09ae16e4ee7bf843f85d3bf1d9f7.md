(by the definition of the $L^2$ norm, equation 2.30)

= $\boldsymbol{x}^\top \boldsymbol{x} - \boldsymbol{x}^\top g(\boldsymbol{c}) - g(\boldsymbol{c})^\top \boldsymbol{x} + g(\boldsymbol{c})^\top g(\boldsymbol{c})$ (2.57)

(by the distributive property)

= $\boldsymbol{x}^\top \boldsymbol{x} - 2\boldsymbol{x}^\top g(\boldsymbol{c}) + g(\boldsymbol{c})^\top g(\boldsymbol{c})$ (2.58)

(because the scalar $g(\boldsymbol{c})^\top \boldsymbol{x}$ is equal to the transpose of itself).

We can now change the function being minimized again, to omit the first term, since this term does not depend on $\boldsymbol{c}$:

$\boldsymbol{c}^* = \arg\min -2\boldsymbol{x}^\top g(\boldsymbol{c}) + g(\boldsymbol{c})^\top g(\boldsymbol{c})$ (2.59)

To make further progress, we must substitute in the definition of $g(\boldsymbol{c})$:

$\boldsymbol{c}^* = \arg\min -2\boldsymbol{x}^\top \boldsymbol{D}\boldsymbol{c} + \boldsymbol{c}^\top \boldsymbol{D}^\top \boldsymbol{D}\boldsymbol{c}$ (2.60)

= $\arg\min -2\boldsymbol{x}^\top \boldsymbol{D}\boldsymbol{c} + \boldsymbol{c}^\top \boldsymbol{I}_l \boldsymbol{c}$ (2.61)

(by the orthogonality and unit norm constraints on $\boldsymbol{D}$)

= $\arg\min -2\boldsymbol{x}^\top \boldsymbol{D}\boldsymbol{c} + \boldsymbol{c}^\top \boldsymbol{c}$ (2.62)

We can solve this optimization problem using vector calculus (see section 4.3 if you do not know how to do this):

$\nabla \left(-2\boldsymbol{x}^\top \boldsymbol{D}\boldsymbol{c} + \boldsymbol{c}^\top \boldsymbol{c}\right) =$ (2.63)

$-2\boldsymbol{D}^\top \boldsymbol{x} + 2\boldsymbol{c} =$ (2.64)

$\boldsymbol{c} = \boldsymbol{D}^\top \boldsymbol{x}$ (2.65)

This makes the algorithm efficient: we can optimally encode $\boldsymbol{x}$ using just a matrix-vector operation. To encode a vector, we apply the encoder function

$f(\boldsymbol{x}) = \boldsymbol{D}^\top \boldsymbol{x}$ (2.66)

Using a further matrix multiplication, we can also define the PCA reconstruction operation:

$r(\boldsymbol{x}) = g\left(f(\boldsymbol{x})\right) = \boldsymbol{D}\boldsymbol{D}^\top \boldsymbol{x}$ (2.67)