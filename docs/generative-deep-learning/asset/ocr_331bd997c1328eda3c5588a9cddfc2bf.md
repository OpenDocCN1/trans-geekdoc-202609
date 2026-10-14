![](bbox=[0.18, 0.08, 0.85, 0.49])

Figure 10-8. The StyleGAN generator architecture (source: Karras et al., 2018)

![](bbox=[0.17, 0.56, 0.25, 0.63])

# Training Your Own StyleGAN

There is an excellent tutorial by Soon-Yau Cheong on training your own StyleGAN using Keras available on the Keras website. Bear in mind that training a StyleGAN to achieve the results from the paper requires a significant amount of computing power.

# The Mapping Network

The mapping network f is a simple feed-forward network that converts the input noise z ∈ Z into a different latent space w ∈ W. This gives the generator the opportunity to disentangle the noisy input vector into distinct factors of variation, which can be easily picked up by the downstream style-generating layers.

The point of doing this is to separate out the process of choosing a style for the image (the mapping network) from the generation of an image with a given style (the synthesis network).