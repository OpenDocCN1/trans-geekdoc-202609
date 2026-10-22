We can also obtain the derivatives in the reference grid by shifting equation (A.53) a half grid-point in the negative direction; i.e.,

\[\frac{\partial g(x)}{\partial x} \approx \frac{1}{\Delta x} \left[ -g \left( x - \frac{1}{2}\Delta x \right) + g \left( x + \frac{1}{2}\Delta x \right) \right] \ . \] (A.54)

Equation (A.54) is the second-order operator for approximating the first-order derivatives. Our time derivatives here are based on this formula.

For spatial derivatives, we will use the fourth- or higher-order approximation. We can obtain the fourth-order approximation by using a five-point formula. For an arbitrary α, the first-order derivatives of a function g(x) can be approximated by a five-point formula, as follows:

\[\frac{\partial g(x + \alpha\Delta x)}{\partial x} = \frac{1}{\Delta x} \left[ \frac{1}{12} (2\alpha^3 - 3\alpha^2 - \alpha + 1) g(x - 2\Delta x) 
 - \frac{1}{6} (4\alpha^3 - 3\alpha^2 - 8\alpha + 4) g(x - \Delta x) 
 + \frac{1}{2} (4\alpha^3 - 3\alpha) g(x) 
 + \frac{1}{6} (4\alpha^3 - 3\alpha^2 - 8\alpha + 4) g(x + \Delta x) 
 - \frac{1}{12} (2\alpha^3 - 3\alpha^2 - \alpha + 1) g(x + 2\Delta x) \right] + ... \ . \] (A.55)

The evaluated equation (A.55) at α = 0 gives us the derivatives at the reference grid:

\[\frac{\partial g(x)}{\partial x} \approx \frac{1}{\Delta x} \left[ \frac{1}{12}g(x - 2\Delta x) - \frac{2}{3}g(x - \Delta x) + \frac{2}{3}g(x + \Delta x) - \frac{1}{12}g(x + 2\Delta x) \right] \ . \] (A.56)

Similarly, evaluated equation (A.55) at α = 1/2 gives us

\[\frac{\partial g(x + \frac{1}{2}\Delta x)}{\partial x} \approx \frac{1}{\Delta x} \left[ \frac{1}{24}g(x - \Delta x) - \frac{9}{8}g(x) + \frac{9}{8}g(x + \Delta x) - \frac{1}{24}g(x + 2\Delta x) \right] \ . \] (A.57)

We can also obtain the derivatives in the reference grid by shifting equation (A.57) a half-grid-point in the negative direction; i.e.,

\[\frac{\partial g(x)}{\partial x} \approx \frac{1}{\Delta x} \left[ \frac{1}{24}g(x - \frac{2}{3}\Delta x) - \frac{9}{8}g(x - \frac{1}{2}\Delta x) + \frac{9}{8}g(x + \frac{1}{2}\Delta x) - \frac{1}{24}g(x + \frac{3}{2}\Delta x) \right] \ . \] (A.58)