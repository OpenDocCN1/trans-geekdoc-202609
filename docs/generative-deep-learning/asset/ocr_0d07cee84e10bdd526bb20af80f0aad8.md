Let's see this in action. Figure 3-19 shows several images that have been encoded into the latent space. We then add or subtract multiples of a certain vector (e.g., Smiling, Black_Hair, Eyeglasses, Young, Male, Blond_Hair) to obtain different versions of the image, with only the relevant feature changed.

![](bbox=[0.2, 0.18, 0.88, 0.48])

Figure 3-19. Adding and subtracting features to and from faces

It is remarkable that even though we are moving the point a significantly large distance in the latent space, the core image remains approximately the same, except for the one feature that we want to manipulate. This demonstrates the power of variational autoencoders for capturing and adjusting high-level features in images.

# Morphing Between Faces

We can use a similar idea to morph between two faces. Imagine two points in the latent space, A and B, that represent two images. If you started at point A and walked toward point B in a straight line, decoding each point on the line as you went, you would see a gradual transition from the starting face to the end face.

Mathematically, we are traversing a straight line, which can be described by the following equation:

```
z_new = z_A * (1- alpha) + z_B * alpha
```

Here, alpha is a number between 0 and 1 that determines how far along the line we are, away from point A.