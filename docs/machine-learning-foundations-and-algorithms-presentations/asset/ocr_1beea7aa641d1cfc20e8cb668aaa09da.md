# Additional Notes for EM

EM assumes that E-step can set the KL to zero:

+   - I.e. we can evaluate the posterior analytically
- Lower bound is tight
- Marginal likelihood always improves (good to check for debugging!)
- Only possible if z is discrete or we have linear Gaussian models!

For more complex latent variable models (e.g. Deep Neural Networks), this is typically not possible:

+   - Extension of EM called Variational Bayes / Variational Inference can still do that
- Approximates the posterior, i.e. KL will be > 0 after E-step
- Very active research, underlying algorithm of many deep learning architectures (e.g. variational autoencoder)
- Will be covered in the end of the lecture