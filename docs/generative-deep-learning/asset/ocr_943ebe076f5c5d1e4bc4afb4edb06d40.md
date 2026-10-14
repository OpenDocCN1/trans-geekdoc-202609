The output is shown in Figure 3-18.

![](bbox=[0.14, 0.11, 0.85, 0.26])

Figure 3-18. New generated faces

Amazingly, the VAE is able to take the set of points that we sampled from a standard normal distribution and convert each into a convincing image of a person's face. This is our first glimpse of the true power of generative models!

Next, let's see if we can start to use the latent space to perform some interesting operations on generated images.

# Latent Space Arithmetic

One benefit of mapping images into a lower-dimensional latent space is that we can perform arithmetic on vectors in this latent space that has a visual analogue when decoded back into the original image domain.

For example, suppose we want to take an image of somebody who looks sad and give them a smile. To do this we first need to find a vector in the latent space that points in the direction of increasing smile. Adding this vector to the encoding of the original image in the latent space will give us a new point which, when decoded, should give us a more smiley version of the original image.

So how can we find the smile vector? Each image in the CelebA dataset is labeled with attributes, one of which is Smiling. If we take the average position of encoded images in the latent space with the attribute Smiling and subtract the average position of encoded images that do not have the attribute Smiling, we will obtain the vector that points in the direction of Smiling, which is exactly what we need.

Conceptually, we are performing the following vector arithmetic in the latent space, where alpha is a factor that determines how much of the feature vector is added or subtracted:

```
z_new = z + alpha * feature_vector
```