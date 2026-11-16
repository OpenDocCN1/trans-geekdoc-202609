$x_j^l = f(\beta_j^{\text{down}}(x_j^{l-1}) + b_j^l)$.

According to the sensitivity of calculating formula of gradient descent, the sensitivity of sampling layer obtained is shown as the following formula:

$\delta_j^l = \delta_j^{l+1}w_j^{l+1} \circ f'(u^l)$.

Whereby the bias updating formula of sampling layer can be obtained, as is shown in formula (10). According to formula (3), bias value updating can be obtained:

$\frac{\partial E}{\partial b_{\text{old}}^l} = \frac{\partial E}{\partial b_j^l} = \sum_{(u,v)} (\delta_j^l)_{uv}$.

# Exponential Momentum Training Algorithm

The traditional gradient descent method only transmits gradient error between single layers, which lead to slow convergence rate of the network. Increasing the learning rate $\eta$ is a good way to improve the convergence speed.

But it not only improves the convergence speed but also causes unstable problem of the network, namely, “oscillation.” Faced with this situation, paper [19] proposes the momentum method, which increases the convergence speed by adding momentum factor. Paper [31] proposes the self-adaptive momentum method based on paper [19].

However, neither of these methods considers the relation between oscillation, convergence, and momentum. And the momentum factor does not promote convergence and enhance learning performance. This paper applies error exponential function of gradient to adjust the pace of momentum factor.

The function can increase the momentum factor at the flat region, which can accelerate the network convergence speed and can decrease the momentum factor at the steep region of error curve, which can avoid excessive network convergence. Such method can improve the convergence rate of the algorithm and avoid oscillation of convergence process.