With calibration of both two moments as follows:

$$\hat{\mathbf{m}}^{(t)} = \frac{\mathbf{m}^{(t)}}{1 - \beta_1^t} \\ \hat{\mathbf{v}}^{(t)} = \frac{\mathbf{v}^{(t)}}{1 - \beta_2^t},$$ (A.32)

where \(\beta_1^t\) and \(\beta_2^t\) refer to the \(t\) power of \(\beta_1\) and \(\beta_2\), Adam updates parameters as follows:

$$\theta^{(t+1)} = \theta^{(t)} - \frac{\eta}{\sqrt{\hat{\mathbf{v}}^{(t)}} + \epsilon} \hat{\mathbf{m}}^{(t)}.$$ (A.33)

# AdaMax

AdaMax is a variant of Adam based on the infinity norm. Moment vectors are computed as follows:

$$\mathbf{m}^{(t)} = \beta_1 \mathbf{m}^{(t-1)} + (1 - \beta_1) \nabla L(\theta^{(t)}) \\ \mathbf{v}^{(t)} = \max(\beta_2 \mathbf{v}^{(t-1)}, |\nabla L(\theta^{(t)})|).$$ (A.34)

Finally AdaMax updates parameters as follows:

$$\theta^{(t+1)} = \theta^{(t)} - \frac{\eta}{(1 - \beta_1^t) \mathbf{v}^{(t)}} \mathbf{m}^{(t)},$$ (A.35)

where \(\beta_1^t\) refers to the \(t\) power of \(\beta_1\).

# A.2.3 Newton's method

Newton's method

Given a function \(f(\theta^{(t)})\) with respect to a single variable \(\theta\), Newton's method aims to find the root of the function \(f(\theta^{(t)}) = 0\) by following approximation:

$$\theta^{(t+1)} = \theta^{(t)} - \frac{f(\theta^{(t)})}{f'(\theta^{(t)})}.$$ (A.36)

Geometrically, the updated \(\theta^{(t+1)}\) is the intersection of the x-axis and the tangent of the function \(f\) at the old \(\theta^{(t)}\).

Given a loss function \(L(\theta^{(t)})\) with respect to parameters \(\theta^{(t)}\), both global and local minima satisfy \(\nabla L(\theta^{(t)}) = 0\). Hence by extending Eq. (A.36) into multivariable scenario and replacing \(f(\theta^{(t)})\) with \(\nabla L(\theta^{(t)})\), the Newton's method takes the form as follows:

$$\theta^{(t+1)} = \theta^{(t)} - \mathbf{H}^{-1} \nabla L(\theta^{(t)}),$$ (A.37)

where \(\mathbf{H}\) is the Hessian matrix of \(L\) with respect to the entries of \(\theta^{(t)}\). Newton's method works well when the problem is convex; that is, the Hessian matrix is positive definite.