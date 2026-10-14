we should probably reduce the reconstruction loss factor, since the KL divergence term isn't having enough effect.

The first 50 dimensions in our latent space are shown in Figure 3-17. There aren't any distributions that stand out as being significantly different from the standard normal, so we can move on to generating some faces!

![](bbox=[0.12, 0.21, 0.9, 0.34])

Figure 3-17. Distributions of points for the first 50 dimensions in the latent space

# Generating New Faces

To generate new faces, we can use the code in Example 3-17.

Example 3-17. Generating new faces from the latent space

```
grid_width, grid_height = (10,3)
z_sample = np.random.normal(size=(grid_width * grid_height, 200)) ①

reconstructions = decoder.predict(z_sample) ②

fig = plt.figure(figsize=(18, 5))
fig.subplots_adjust(hspace=0.4, wspace=0.4)
for i in range(grid_width * grid_height):
    ax = fig.add_subplot(grid_height, grid_width, i + 1)
    ax.axis("off")
    ax.imshow(reconstructions[i, :, :]) ③
```

+   ① Sample 30 points from a standard multivariate normal distribution with 200 dimensions.
+   ② Decode the sampled points.
+   ③ Plot the images!