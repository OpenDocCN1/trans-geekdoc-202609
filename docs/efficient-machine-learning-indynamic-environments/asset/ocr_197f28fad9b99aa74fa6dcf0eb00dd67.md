Proof. For simplicity, we assume that $f_t$ and $g$ are scalar-valued functions, since the proof goes through coordinate-wise. At each time, define the edge of the weak learning algorithm to be

$$\gamma_t = \sum_i K_t^+(i)(f_t(x_i) - g(x_i)) + \sum_i K_t^-(i)(g(x_i) - f_t(x_i)) \tag{2.9}$$

Let $Z_t$ denote the normalizing constant at time $t$, that is,

$$Z_t = \sum_i K_t^+(i) \exp(-\eta(f_t(x_i) - g(x_i))) + K_t^-(i) \exp(\eta(f_t(x_i) - g(x_i)))$$

From the update rule,

$$K_{T+1}^+(i) = \frac{K_T^+(i)e^{\eta(f_T(x_i)-g(x_i))}}{Z_T}$$ 
$$= \frac{K_1^+(i) \exp(-\eta \sum_{t=1}^T (f_t(x_i) - g(x_i))_j)}{\prod_{t=1}^T Z_t}$$ 
$$= \frac{K_1^+(i) \exp(-\eta T(F_T(x_i) - g(x_i)))}{\prod_{t=1}^T Z_t}$$

and similarly

$$K_{T+1}^-(i) = \frac{K_1^-(i) \exp(\eta T(F_T(x_i) - g(x_i)))}{\prod_{t=1}^T Z_t}$$

First, we bound $\ln(Z_t)$:

$$\ln(Z_t) = \ln\left( \sum_i K_t^+(i) \exp(-\eta(f_t(x_i) - g(x_i))) + \sum_i K_t^-(i) \exp(\eta(f_t(x_i) - g(x_i))) \right)$$ 
$$\le \ln\left( \sum_i K_t^+(i) \left( 1 - \eta(f_t(x_i) - g(x_i)) + \eta^2(f_t(x_i) - g(x_i))^2 \right) \right.$$ 
$$\left. + \sum_i K_t^-(i) \left( 1 + \eta(f_t(x_i) - g(x_i)) + \eta^2(f_t(x_i) - g(x_i))^2 \right) \right)$$ 
$$\le \ln\left( 1 - \eta \sum_i K_t^+(i)(f_t(x_i) - g(x_i)) + \eta \sum_i K_t^-(i)(f_t(x_i) - g(x_i)) + \eta^2 G_\infty^2 \right)$$ 
$$\le -\eta \gamma_t + \eta^2 G_\infty^2$$

where the second step follows from the identity $\exp(x) \le 1 + x + x^2$ for $x \le 1$, provided