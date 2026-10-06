# 2.9.1 Scaled Brownian Motion

We will prove that $\hat{W}_t$ defined by

$$$\hat{W}_t = \frac{1}{c}W_{c^2t}, \quad c > 0$$

is Brownian motion.
Let us consider the process

$$$\hat{Y}_t = W_{c^2t}.$$$$

From equation (2.9.2), we have $a_t = 1, f_t = c^2t, a'_t = 0$, and $f'_t = c^2$.
Substituting these values into equation (2.9.6) yields

$$$dY_t = \sqrt{c^2}dt \ dZ_t,$$$$

which gives

$$$dY_t = c\sqrt{c}dt \ dZ_t = cW_t.$$$$

Therefore, $\hat{W}_t = \frac{dY_t}{c}$ is Brownian motion.

# 2.9. Mean Reverting Process

We will now show that the mean reverting Ornstein-Uhlenbeck process (see Section 2.10) can be represented as:

$$$Y_{W,t} = \exp(-at)\Psi_t, \quad \text{where} \psi_t = \frac{\sigma^2 \exp(2at)}{2\alpha} \quad \alpha > 0. \quad (2.9.7)$$$$

Proof. From equation (2.9.2) and equation (2.9.7), we have

$$$f_t = \frac{\sigma^2 \exp(2at)}{2\alpha} \quad \text{and} \quad a_t = \exp(-2at). \quad (2.9.8)$$$$

Therefore,

$$$a'_t = \frac{-a\exp(-at)}{a_t} = -a\exp(-at) \quad (2.9.9)$$$$

and

$$$f'_t = \frac{\sigma^2}{2\alpha}\exp(2at) = \sigma^2\exp(2at). \quad (2.9.10)$$$$

So,

$$$\sqrt{f_t}dt = \sqrt{\sigma^2 \exp(2at)} = \sigma\exp(at)\sqrt{dt}. \quad (2.9.11)$$$$

Thus,
which means that

$$$dW_{W,t} = -aY_{W,t}dt + \exp(-at)\sigma\exp(at)\sqrt{dt} \ dZ, \quad (2.9.12)$$$$

From equation (2.9.13), it can be seen that conditional mean and variance are

$$$E[dW_{W,t}|F_t] = \alpha Y_{W,t}dt, \quad (2.9.14)$$$$

$$$Var[dW_{W,t}|F_t] = \sigma^2dt. \quad (2.9.15)$$$$