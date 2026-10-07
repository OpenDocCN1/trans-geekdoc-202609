# Equation 11-8. Adam algorithm

+   1. $m \leftarrow eta_1 m - (1 - eta_1)
abla_	heta(	heta)$
2. $s \leftarrow eta_2 s + (1 - eta_2)
abla_	heta(	heta) \otimes 
abla_	heta(	heta)$
3. $m \leftarrow \frac{m}{1-eta_1^t}$n4. $\hat{s} \leftarrow \frac{s}{1-eta_2^t}$n5. $	heta \leftarrow 	heta - \eta \frac{m}{\sqrt{\hat{s}} + \epsilon}$

- $t$ represents the iteration number (starting at 1).
If you look at steps 1, 2, and 5, you will notice Adam's close similarity to both Momentum optimization and RMSProp. The only difference is that step 1 computes an exponentially decaying average rather than an exponentially decaying sum, but these are actually equivalent for a constant factor (the decaying average is $1-eta$, times the decaying sum). Steps 3 and 4 are somewhat of a technical detail: since $m$ and $s$ are initialized at 0, they will be biased towards 0 at the beginning of training, so these two steps will help $m$ and $s$ at the beginning of training.

The decay hyperparameter $eta_1$ is typically initialized to 0.9, while the decay hyperparameter $eta_2$ is often initialized to 0.999. As earlier, the smoothing term is usually initialized to a tiny number such as $10^{-7}$. These are the default values for the *Adam* class (to be precise, defaults to None, which tells Keras to use `keras.backend.epsilon()`, which defaults to $10^{-7}$; you can change it using `keras.backend.epsilon()`).

```
optimizer = keras.optimizers.Adam(lr=0.001, beta_1=0.9, beta_2=0.999)
```

Since Adam is an adaptive learning rate algorithm (like AdaGrad and RMSProp), it requires less tuning of the learning rate hyperparameter $\eta$. You can often use the default value $\eta = 0.001$, making Adam even easier to use Gradient Descent.

If you are starting to feel overwhelmed by all these different techniques, and wondering how to choose the right ones for your task, don't worry: some practical guidelines are provided at the end of this chapter.

![](bbox=[0.176, 0.737, 0.244, 0.816])

Finally, two variants of Adam are worth mentioning: