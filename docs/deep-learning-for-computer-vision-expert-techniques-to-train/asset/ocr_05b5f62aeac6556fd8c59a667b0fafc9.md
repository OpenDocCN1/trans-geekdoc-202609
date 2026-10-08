# Generative Models

The optimization can be run for 10 iterations to see the results, as shown:

```
iterations = 10
generated_image = optimise(optimiser, iterations, generated_image,
content_image_shape, 'content')
```

If everything goes well, the loss should print as shown here, over the iterations:

+   Current loss value: 73.2010421753
Current loss value: 22.7840021353
Current loss value: 12.6585302353
Current loss value: 8.53817081451
Current loss value: 6.64649853425
Current loss value: 5.56395864487
Current loss value: 4.83072710037
Current loss value: 4.32800722122
Current loss value: 3.94804215431
Current loss value: 3.663876533531

Here is the image that is generated and now, it almost looks like a bird. The optimization can be run for further iterations to have this done:

![](bbox=[0.302, 0.47, 0.696, 0.683])

An optimizer took the image and updated the pixels so that the content is the same. Though the results are worse, it can reproduce the image to a certain extent with the content. All the images through iterations give a good intuition on how the image is generated. There is no batching involved in this process. In the next section, we will see how to create an image in the style of a painting.