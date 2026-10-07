Machine Learning

Chapter 7: Going Convolutional

Unfortunately, the bump only happened in the training loss, the validation loss just keeps getting worse. If you also plot the accuracy curves, you'll see that the validation score accurately stabilizes at 41% correct at this point.

In general, you want to start with a high learning rate as you can get away with, then lower it over time. If the learning rate is too high, the loss will “explode”.

For a classifier, the initial loss should roughly be np.log(num_classes). If the loss at any point becomes much larger than that, and only keeps increasing over time, you need to lower the learning rate.

Changing the learning rate is hand by using manual learning rate annealing. Keras can do this automatically for you using a callback (more about that in the next chapters).

Usually, you want to lower the learning rate when you find the validation loss is no longer decreasing. That’s often a good indication that the optimizer has gotten “stuck”. The way to get unstuck is by lowering the learning rate, which lets you squeeze a few extra percentage points of accuracy out of the model.

# It’s better... but not good enough

It’s clear that you were able to create a better model using these convolutional layers with only Dense layers. The final test accuracy for this model is about 40% correct, compared to only 15% from the last chapter. That’s a big improvement!

All thanks to the convolutional layers, because they know how to take advantage of the natural structure of the images.

But note that this particular model overfits a lot — again! That’s bad news. With over one million parameters and about 4,800 training images, there is too much freedom for the model to memorize the images. Adding more layers or more filters per layer is only going to make this problem worse, so you’ll also look at how to fix problem once and for all.

> Note: Even though the model you trained isn’t optimal, this very straightforward exercise of conv layers and pooling layers can work well in practice; it is very similar to the famous VGG network that is used by many in the deep-learning community. One way to get better results with this architecture is to first train the model on a much larger dataset as ImageNet — which has over one million images — and then adapt it to your images. But that takes a long time… It’s often easier to build on top of an

raywenderlich.com

267