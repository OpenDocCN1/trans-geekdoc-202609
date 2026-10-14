# Normalizing Flow Models

# Chapter Goals

In this chapter you will:

+   - Learn how normalizing flow models utilize the change of variables equation.
+   - See how the Jacobian determinant plays a vital role in our ability to compute an explicit density function.
+   - Understand how we can restrict the form of the Jacobian using coupling layers.
+   - See how the neural network is designed to be invertible.
+   - Build a RealNVP model—a particular example of a normalizing flow to generate points in 2D.
+   - Use the RealNVP model to generate new points that appear to have been drawn from the data distribution.
+   - Learn about two key extensions of the RealNVP model, GLOW and FFJORD.

So far, we have discussed three families of generative models: variational autoencoders, generative adversarial networks, and autoregressive models. Each presents a different way to address the challenge of modeling the distribution $p(x)$, either by introducing a latent variable that can be easily sampled (and transformed using the decoder in VAEs or generator in GANs), or by tractably modeling the distribution as a function of the values of preceding elements (autoregressive models).

In this chapter, we will cover a new family of generative models—normalizing flow models. As we shall see, normalizing flows share similarities with both autoregressive models and variational autoencoders. Like autoregressive models, normalizing flows are able to explicitly and tractably model the data-generating distribution $p(x)$. Like