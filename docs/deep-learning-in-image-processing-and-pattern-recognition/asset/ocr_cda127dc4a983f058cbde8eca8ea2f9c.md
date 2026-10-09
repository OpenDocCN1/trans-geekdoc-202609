indicating slow learner and larger loss values indicating fast learner $[ \mathcal{L}_{val}(\mathbf{C}_{q_{i f}^{s}}, w_{q_{i f}^{s}}^{*}) < \mathcal{L}_{val}(\mathbf{C}_{q_{i s}^{s}}, w_{q_{i s}^{s}}^{*}) ]$. Then, $q_{j s}^{t}$ learns from $q_{i f}^{t}$ and updates it.

$\Delta q_{i s}^{t} = \eta_{1}(q_{i f}^{t} - q_{i s}^{t}) + \eta_{2} \Delta q_{i s}^{t - 1}$

(12)

Here, $\eta_{1}, \eta_{2} \in [0,1]$ represents a randomly generated value obtained from a uniform distribution. Specifically, $\eta_{1}$ determines the step size for $q_{i f}^{t}$ to learn from $q_{j f}^{t}$, and $\eta_{2}$ determines the influence of momentum $\Delta q_{i s}^{t-1}$. Finally, all fast-slow learners are aggregated to form a new group of the $t+1$ th generation. The above pseudo gradient update method is derived from the second derivative of gradient descent in back propagation, so each architecture vector in the search space of the multi-attention mechanism designed in this work will move towards the optimal update direction from the vector that converges faster than them.

After the architecture update process, it is necessary to evaluate the performance of candidate architectures for decoding architecture vectors, so that for each pair of architecture vectors, fast learners can learn and update slow learners by verifying the loss. Subsequently, the candidate architecture $\mathbf{C}_{a s}$ is assessed by solving the following optimization problems:

$w_{o s}^{*} = \mathrm{optimize}(w_{o s}) = s t e p(s t e p(\ldots s t e p(w_{o s}|\mathbf{C}_{a s}) \ldots \mathbf{C}_{a s})|\mathbf{C}_{a s})$

(13)

In the given equation, $w_{o s}^{*}$ represents the optimal weight of the candidate architecture, while $s t e p(\cdot)$ denotes the iterative optimization process utilized for updating the weights of the neural network.

# 2.2.3. Lion Optimizer

The optimizer is utilized to update and compute the network parameters that influence model training and output, with the goal of approaching or achieving the optimal value and thereby minimizing (or maximizing) the loss function. This study utilizes the Lion optimizer, known for its simplicity, efficiency, and speed. Reducing redundancy is an important aspect of this work. At the same time, this optimizer is suitable for large-scale optimization problems involving big datasets or high-dimensional parameter spaces. The use of the Lion optimizer can not only effectively improve the accuracy of HSI data classification but also reduce memory overhead and effectively reduce training time because the algorithm only tracks momentum and uses symbolic operation to calculate updates. The Lion optimizer formula is written as follows [43]:

$\theta_{t+1} = \omega_{t} \theta_{t}$

(14)

$g_{t} = \nabla g f(\theta_{t-1})$

(15)

where $\omega_{t}$ is the decay rate, $\theta_{t}$ is the weights, and $g_{t} = \nabla g f(\theta_{t-1})$ is the gradient at $\theta_{t-1}$. To calculate the average attenuation of the current and past square gradient, the mathematical relationship can be written as follows:

$c_{t} = \hat{\beta}_{1} m_{t-1} + (1 - \hat{\beta}_{1}) g_{t}$

(16)

where $c_{t}$ is the 1st moment estimate, and $m_{t-1}$ represents the momentum vector from the previous iteration. $\hat{\beta}_{1}$ is the decay rate of the 1st moment. The weight reduction process for decoupling is as follows:

$\theta_{t} \leftarrow \theta_{t-1} - \eta_{t}(s i g n(c t) + \lambda \theta_{t-1})$

(17)

where $\eta_{t}$ is the step size. To counteract biases, the bias-corrected first and second moments are computed in the following manner: