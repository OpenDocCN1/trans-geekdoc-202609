```
latent_points, labels = generate_latent_points(100, 100)
# specify labels
labels = asarray([x for _ in range(10) for x in range(10)])
# generate images
X = model.predict([latent_points, labels])
# scale from [-1,1] to [0,1]
X = (X + 1) / 2.0
# plot the result
save_plot(X, 10)
```

Listing 17.25: Example of loading the saved conditional generator model and using it to generate images.

Running the example loads the saved conditional GAN model and uses it to generate 100 items of clothing. The clothing is organized in columns. From left to right, they are t-shirt, trouser, pullover, dress, coat, sandal, shirt, sneaker, bag, and ankle boot. We can see not only are the randomly generated items of clothing plausible, but they also match their expected category.

![](bbox=[0.206, 0.413, 0.793, 0.743])

Figure 17.7: Example of 100 Generated items of Clothing using a Conditional GAN.

# 17.7 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.