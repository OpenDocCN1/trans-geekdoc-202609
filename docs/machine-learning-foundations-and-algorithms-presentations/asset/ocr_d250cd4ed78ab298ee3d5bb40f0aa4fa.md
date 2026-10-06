# Diffusion Summary

Diffusion models are Hierarchical VAEs with extra restrictions

+   - The loss is the vanilla VAE ELBO loss with an added denoising term
- The encoder has 0 parameters
- The true denoising posterior can be exactly calculated
- The ELBO is decomposed into each time step: fast to train
- Can be made extremely deep (up to 1k diffusion steps)
- The problem can be reformulated as a noise prediction problem
- There's a lot of math underlying a rather simple intuition

A lot more research happened the last 2-3 years:

+   - Score-based diffusion models – Noise models learn the gradient of the log-density
- Use of continuous stochastic differential equation (SDE) theory