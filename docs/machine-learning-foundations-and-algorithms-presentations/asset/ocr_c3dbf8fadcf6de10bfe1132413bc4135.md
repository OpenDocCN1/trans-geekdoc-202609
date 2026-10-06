# # Denoising cost function

This lets us rewrite the true mean of the denoising process as:

$$\mu_t = \frac{\sqrt{ar{\alpha}_t(1-ar{\alpha}_{t-1})}x_t + \sqrt{ar{\alpha}_{t-1}}(1-\alpha_t)x_0}{1-ar{\alpha}_t} \Rightarrow \mu_t = \frac{1}{\sqrt{ar{\alpha}_t}} \left( x_t - \frac{(1-\alpha_t)}{\sqrt{1-ar{\alpha}_t}} \epsilon \right)$

> Rewrite in terms of noise
$$x_t = \sqrt{ar{\alpha}_t}x_0 + \sqrt{1-\bar{\alpha}_t}\epsilon \n\rightarrow x_0 = \frac{x_t - \sqrt{1-\bar{\alpha}_t}\epsilon}{\sqrt{ar{\alpha}_t}}$$

We can also write the predicted mean as:

$$\mu\theta(x_t, t) = \frac{1}{\sqrt{ar{\alpha}_t}} \left( x_t - \frac{(1-\alpha_t)}{\sqrt{1-\bar{\alpha}_t}} \epsilon\theta(x_t, t) \right)$

This lets us reformulate the loss to present a noise prediction problem:

$L_{t-1} = \mathbb{E}_{x_0, \epsilon} \left[ \frac{(1-\alpha_t)^2}{2\Sigma\alpha_t(1-\bar{\alpha}_t)} \right] ||\epsilon - \epsilon\theta(x_t, t)||^2 + \mathcal{C}$