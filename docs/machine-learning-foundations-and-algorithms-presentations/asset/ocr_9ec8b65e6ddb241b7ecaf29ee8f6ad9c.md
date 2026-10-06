# # Recap: Matrix Calculus

Derivatives of a scalar function w.r.t. a matrix...

+   - ... is again a matrix $
abla_W f = egin{bmatrix} \frac{\partial f(W)}{\partial W_{11}} & \dots & \frac{\partial f(W)}{\partial W_{1d}} \ \vdots & \vdots & \vdots \ \frac{\partial f(W)}{\partial W_{k1}} & \dots & \frac{\partial f(W)}{\partial W_{kd}} \end{bmatrix}$

Derivatives of a vector-valued function w.r.t. a matrix...

+   - ... is a 3D tensor! $
abla_W f = \frac{\partial f(W)}{\partial W} \in \mathcal{R}^{m 	imes n 	imes d} 	ext{ with } f: \mathcal{R}^{m 	imes n} ightarrow \mathcal{R}^d$

+   - Why do we need this?
  - Compute derivative w.r.t weight matrix $\frac{\partial Wx+b}{\partial W}$
  - Luckily there will be a simplification of this...