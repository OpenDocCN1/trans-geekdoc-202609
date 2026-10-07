If you now look at x, the values are much smaller:

```
array([[[ 0.6862745 , 0.6862745 , 0.7019608 ],
[ 0.654902 , 0.654902 ,  ],
[ 0.6235293, 0.6235293, 0.6235293 ], ...

[ 0.1921569, 0.17647064, 0.07450986 ],
[ 0.16078346, 0.14509890, 0.04313731 ],
[ 0.1686275, 0.15294123, 0.03529418 ]]])
```

If you are curious, you can print the mean and standard deviation of this training image with x.mean() and x.std(). The mean of a single training image may not be exactly 0, but the entire training set it will be close to 0. The standard deviation should be around 0.15.

The np.expand_dims() function added a new dimension to the front, to turn this single image into a batch of images with batch size 1. The tensor containing this image is now of rank 4. You can view this with:

```
x.shape
```

This prints (1, 32, 32, 3). It's always a good idea to double-check the sizes of your images and other data objects, to verify they are correct. Adding this batch dimension is necessary because the Keras training functions all work on a batch of images, and expect this dimension to be there.

# Too soon to make predictions?

Even though the model isn't trained yet, you can already make a prediction on the input image:

```
pred = model.predict(x)
print(pred)
```

> Note: If your Jupyter crashes when you run this cell, execute the following command from the Terminal: conda install nomkl. This fixes a package conflict that sometimes causes trouble on the Mac.

You should get an array with 20 values, one probability for each class. Since you haven't trained the model yet, these predictions aren't very useful. You'll see something like the following: