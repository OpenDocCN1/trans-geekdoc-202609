more than the standard training, which makes adversarial training slow. We will discuss some ways to overcome this problem in the next section.

After obtaining \(x'\), we will run one update to solve the outer minimization problem to obtain a better parameter \(\theta\). This can be done by computing the gradient of \(\theta\) with respect to \(x'\) (\(\nabla_\theta L(f_\theta(x'), y)\)) and then pass this gradient to the update rule optimizers (e.g., (SGD or Adam) for the parameter update. The overall PGD-based adversarial training algorithm can be found in Algorithm 3.

+   **Algorithm 3 PGD-based adversarial training (Madry et al., 2018).**
+   
+   1: **Input:** Initial model parameter \(\theta_0\), number of PGD steps \(k\)
+   2: **for** \(t = 0, 1, 2, ...\) **do**
+   3: Sample \((x, y)\) from training data \(\mathcal{D}\)
+   4: Let \(x_0 = x\)
+   5: **for** \(t' = 0, ..., k-1\) **do**
+   6: \(x_{t'+1} \leftarrow \text{Proj}_{B(x)}(x_{t'} + \alpha \cdot \text{sign}(\nabla_x L(f_\theta(x_{t'}), y)))\)
+   7: **end for**
+   8: Update \(\theta\) by \(\theta \leftarrow \theta - \eta \nabla_\theta L(f_\theta(x_k), y)\)
+   9: **end for**

# 12.2 Faster adversarial training

As mentioned in the previous section, PGD-based adversarial training requires \(k\) inner steps, which will increase the training time by \(k\) times over standard training. To reduce this overhead, several methods have been developed to achieve a better tradeoff between the robust accuracy and training speed.

Recall that in adversarial training the model update requires gradient of loss function with respect to \(\theta\), whereas the PGD updates rely on the gradient of the same loss function with respect to \(x\). These two gradients, denoted as \(\nabla_\theta L(f_\theta(x), y)\) and \(\nabla_x L(f_\theta(x), y)\), compute the gradient of the same function, but with respect to different variables. In neural networks, gradient is usually computed by back-propagation, and these two gradients can actually share the whole back-propagation process – after computing \(\nabla_\theta L(f_\theta(x), y)\), only one additional linear projection step can compute \(\nabla_x L(f_\theta(x), y)\). This means that computing both \(\nabla_\theta L(f_\theta(x), y)\) and \(\nabla_x L(f_\theta(x), y)\) together will have the same cost as computing each of them individually. Motivated by this observation, we can make additional updates during inner PGD steps. In the original adversarial training, each PGD step