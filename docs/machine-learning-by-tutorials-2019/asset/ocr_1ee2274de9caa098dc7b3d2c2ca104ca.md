Note: Each pixel needs three numbers because color is stored as RGB: a red, green and blue intensity value. Some images also have a fourth channel, the alpha channel, that stores transparency information, but this is typically not used by image classifiers. It’s OK to use an RGBA image as input, but the classifier will simply ignore the alpha value.

Here’s the big idea: Each of the 227×227 input images can be represented by a unique point in a 150,000-dimensional space.

Whoop, try to wrap your head around that... It’s pretty easy for us to think in 3D space but not much in higher-dimensional spaces, especially not ones with hundreds of thousands of dimensions. But the principle is the same: given 3 numbers (x, y, z) you can describe any point in 3-dimensional space, right? Well, given 150,000 numbers with the RGB values of all the pixels in the image, you end up at a point in 150,000-dimensional space.

![](bbox=[0.283, 0.423, 0.716, 0.656])

By the way, don’t try to think in 150,000 dimensions. pretend it’s more than three dimensions. That’s what everyone else does too, since humans aren’t capable of visualizing more than three dimensions.

To classify the images, you want to be able to draw a line through this high-dimensional space and say, “All the images containing healthy snacks are on this side of the line, and all the images with unhealthy snacks are on the other side.” If that would be possible, classifying an image is easy: You just have to look at which side of the line the image’s point falls.