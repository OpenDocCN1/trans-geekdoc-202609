The posterior for $a_t$ is given by

$$q_t(a_t)=\mathcal{N}(a_t\mid m_t,v_t) \tag{10.172}$$

$$m_t=\int a_t\frac{1}{Z_t}p(y_t\mid a_t)q_{t\mid t-1}(a_t)\,da_t \tag{10.173}$$

$$v_t=\int a_t^2\frac{1}{Z_t}p(y_t\mid a_t)q_{t\mid t-1}(a_t)\,da_t-m_t^2 \tag{10.174}$$

$$Z_t=\int p(y_t\mid a_t)q_{t\mid t-1}(a_t)\,da_t \tag{10.175}$$

where $p(y_t\mid a_t)=\operatorname{Ber}(y_t\mid a_t)$. These integrals are one dimensional, and so can be computed using Gaussian quadrature, as explained in [Zoe07].

Having inferred $q_t(a_t)$, we need to compute $q_t(\mathbf{w}\mid a_t)$. This can be done as follows. Define $\delta_m$ as the change in the mean and $\delta_v$ as the change in the variance:

$$m_t=m_{t\mid t-1}+\delta_m,\quad v_t=v_{t\mid t-1}+\delta_v \tag{10.176}$$

Then one can show that the new factored posterior over the model parameters is given by

$$q_t(w_{t,j})=\mathcal{N}(w_{t,j}\mid\mu_{t,j},\tau_{t,j}) \tag{10.177}$$

$$\mu_{t,j}=\mu_{t\mid t-1,j}+a_j\delta_m \tag{10.178}$$

$$\tau_{t,j}=\tau_{t\mid t-1,j}+a_j^2\delta_v \tag{10.179}$$

$$a_j\triangleq\frac{x_{t,j}\tau_{t\mid t-1,j}}{\sum_{j'}x_{t,j'}^2\tau_{t\mid t-1,j'}} \tag{10.180}$$

Thus we see that the parameters which correspond to inputs with larger magnitude (big $|x_{t,j}|$) or larger uncertainty (big $\tau_{t\mid t-1,j}$) get updated most, which makes intuitive sense.

Note that the whole algorithm only takes $O(D)$ time and space per step, the same as SGD. However, unlike SGD, there are no step-size parameters, since the diagonal covariance implicitly specifies the size of the update for each dimension. Furthermore, we get a posterior approximation, not just a point estimate.

# 10.7 Exercises

# Exercise 10.1 [Gradient and Hessian of log-likelihood for multinomial logistic regression]

+   a. Let $\mu_{ik}=\mathcal{S}(\eta_i)_k$, where $\eta_i=\mathbf{w}^T\mathbf{x}_i$. Show that the Jacobian of the softmax is

$$\frac{\partial\mu_{ik}}{\partial\eta_{ij}}=\mu_{ik}(\delta_{kj}-\mu_{ij}) \tag{10.181}$$

where $\delta_{kj}=I(k=j)$.

+   b. Hence show that the gradient of the NLL is given by

$$\nabla_{\mathbf{w}_c}\ell=\sum_i(y_{ic}-\mu_{ic})\mathbf{x}_i \tag{10.182}$$

Hint: use the chain rule and the fact that $\sum_c y_{ic}=1$.