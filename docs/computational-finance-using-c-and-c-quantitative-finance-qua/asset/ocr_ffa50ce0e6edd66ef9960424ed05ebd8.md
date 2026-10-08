Using Ito's lemma,

$dY_{W,t} = \frac{\partial Y_t}{\partial t} dt + \frac{\partial Y_t}{\partial W_t} dW_t \quad (2.9.3)$

where we used the fact that $\frac{\partial^2 Y_t}{\partial W_t^2} = 0.$

From Eq. (2.9.3)

$dY_{W,t} = \left(\frac{\partial a_t}{\partial t}ight) W_{f,t} dt + a_t dW_{f,t} \quad (2.9.4)$

Now

$dW_{f,t} = \sqrt{d f_t} dZ_t = \sqrt{\frac{\partial f_t}{\partial t}} dt dZ_t \quad (2.9.5)$

so we can write:

$dY_{W,t} = a'_t W_{f,t} + a_t \sqrt{f'_t} dt dZ_t \quad (2.9.6)$

where

$a'_t = \frac{\partial a_t}{\partial t} \quad \text{and} \quad f'_t = \frac{\partial f_t}{\partial t}$

# 2.9.1 Scaled Brownian motion

We will prove that $\widehat{W}_t$ defined by

$\widehat{W}_t = \frac{1}{c}W_{c^2t}, \quad c > 0,$

is Brownian motion.

Let us consider the process

$Y_t = W_{c^2t}$

From Eq. (2.9.2) we have $a_t = 1, f_t = c^2t, a'_t = 0$ and $f'_t = c^2$. Substituting these values into Eq. (2.9.6), yields

$dY_t = \sqrt{c^2}dt dZ_t$

which gives

$dY_t = c\sqrt{dt}dZ_t = c dW_t$

Therefore $\widehat{W}_t = dY_t/c$ is Brownian motion.

# 2.9.2 The Ornstein-Uhlenbeck process

We will now show that the Ornstein-Uhlenbeck process (see Section 2.10) can be represented as follows:

$Y_{W,t} = \exp(-\alpha t)W_{\psi_t} \quad \text{where} \psi_t = \frac{\sigma^2 \exp(2\alpha t)}{2\alpha}, \alpha > 0 \quad (2.9.7)$