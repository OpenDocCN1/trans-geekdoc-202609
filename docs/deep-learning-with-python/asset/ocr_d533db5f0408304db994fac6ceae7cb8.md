```
j * digit_size : (j + 1) * digit_size,
] = digit
```

```
plt.figure(figsize=(15, 15))
start_range = digit_size // 2
end_range = n * digit_size + start_range
pixel_range = np.arange(start_range, end_range, digit_size)
sample_range_x = np.round(grid_x, 1)
sample_range_y = np.round(grid_y, 1)
plt.xticks(pixel_range, sample_range_x)
plt.yticks(pixel_range, sample_range_y)
plt.xlabel("z [0]")
plt.ylabel("z [1]")
plt.axis("off")
plt.imshow(figure, cmap="Greys_r")
```

The grid of sampled digits (see figure 12.18) shows a completely continuous distribution of the different digit classes, with one digit morphing into another as you follow a path through latent space. Specific directions in this space have a meaning: for example, there are directions for “five-ness,” “one-ness,” and so on.

![](bbox=[0.173, 0.423, 0.743, 0.873])

Figure 12.18 Grid of digits decoded from the latent space