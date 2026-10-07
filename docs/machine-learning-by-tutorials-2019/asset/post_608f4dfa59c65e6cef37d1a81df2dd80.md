
Machine Learning

Chapter 7: Going Convolutional

Unfortunately, the bump only happened in the training loss, the validation loss just keeps getting worse. If you also plot the accuracy curves, you'll see that the validation score accurately stabilizes at 41% correct at this point.

In general, you want to start with a high learning rate as you can get away with, then lower it over time. If the learning rate is too high, the loss will “explode”.

For a classifier, the initial loss should roughly be np.log(num_classes). If the loss at any point becomes much larger than that, and only keeps increasing over time, you need to lower the learning rate.

Changing the learning rate is handled by using manual learning rate annealing. Keras can do this automatically for you using a callback (more about that in the next chapters).

Usually, you want to lower the learning rate when you find the validation loss is no longer decreasing. That’s often a good indication that the optimizer has gotten “stuck”. The way to get unstuck is by lowering the learning rate, which lets you squeeze a few extra percentage points of accuracy out of the model.

## It’s better... but not good enough

It’s clear that you were able to create a better model using these convolutional layers with only Dense layers. The final test accuracy for this model is about 40% correct, compared to only 15% from the last chapter. That’s a big improvement!

All thanks to the convolutional layers, because they know how to take advantage of the natural structure of the images.

But note that this particular model overfits a lot — again! That’s bad news. With over one million parameters and about 4,800 training images, there is too much freedom for the model to memorize the images. Adding more layers or more filters per layer is only going to make this problem worse, so you’ll also look at how to fix the problem once and for all.

> Note: Even though the model you trained isn’t optimal, this very straightforward exercise of conv layers and pooling layers can work well in practice; it is very similar to the famous VGG network that is used by many in the deep-learning community. One way to get better results with this architecture is to first train the model on a much larger dataset as ImageNet — which has over one million images — and then adapt it to your images. But that takes a long time… It’s often easier to build on top of an existing pre-trained model that you can simply download for free, without having to do the laborious ImageNet training yourself. Yep, we'll be talking transfer learning again!

## Key points

- You need to access a powerful GPU in order to train these deep learning models. Unfortunately, Mac GPUs are not well supported by popular training tools. The cloud to the rescue!
- Convolution layers are key to making good image classifiers. like Dense layers they compute dot products but only over small regions of the image. Speaking mathematically, convolution is actually the same as a Dense layer in which most of the connections are zero, and the other connections share the same weights.
- Convnets are made up of a series of convolution layers and pooling layers. Layers deeper in the network have more filters and learn to detect higher-level patterns that represent abstract concepts.
- Choosing the right values for the hyperparameters such as the learning rate is essential for getting an optimal result. It's also a good idea to plot the loss and accuracy curves, to see if your model is overfitting or whether it is done learning.

## Where to go from here?

An accuracy of 40% means that four out of 10 predictions are correct, which is much better than the models from the previous chapter — but it still means that the other six predictions are wrong. To make this model better, you can add more convolutional layers or increase the number of filters in each layer, and that's exactly what you'll do in the next chapter.

![](img/5720be5c3cca252e12448e68d25607b5_268_0.png)

**Update Note:** This chapter has been updated to iOS 13, Xcode 11 and Swift 5.1.

## SqueezeNet

What you did in the simple previous chapter is very similar to what Create ML and Turi do when they train models, except the convnet they use is a little more advanced. Puri Create actually gives you a choice between different convnets:

- SqueezeNet
- ResNet50
- VisionFeaturePrint_Scene

In this section, you'll take a quick look at the architecture of SqueezeNet and how it is different from the simple convnet you made. ResNet50 is a model that is used a lot in deep learning, but at, over 25 million parameters, it's on the big side for use on mobile devices and we'll pay it no further attention.

We'd love to show you the architecture for VisionFeaturePrint_Scene, but, alas, this model is built into iOS itself and so we don't know what it actually looks like.

This is SqueezeNet, zoomed out:

![](img/5720be5c3cca252e12448e68d25607b5_269_0.png)

SqueezeNet uses the now-familiar Conv2D and MaxPool22D layers, as well as the ReLU activation. However, it also has a branching structure that looks like this:

![](img/5720be5c3cca252e12448e68d25607b5_269_1.png)

## The fire module

This combination of different layers is called a fire module. In SqueezeNet, the output from the squeeze branches into two parallel convolutions, one with a 1×1 window size and the other with a 3×3. Both convolutions have 64 filters, which is why this is called the expand partition of the fire module.

The squeeze layer that follows it reduces these 128 channels back to 16, and so on. As is usual for convnets, the number of channels increases the further you go into the network, but this pattern of reduce-expand repeats several times over.

The reason for using two convolutions on the same data is that using different transformations potentially lets you extract more information. You see similar ideas in the Inception modules from Google's famous Inception-v3 model, which combines 1×1, 3×3, and 5×5 convolutions, and even pooling, into the kind of parallel structure.

The fire module is very effective, by the fact that SqueezeNet is a powerful model — especially for one that has 1.2 million learnable parameters. It scores about 67% correct on the snakes dataset, compared to 40% from the basic convnet of the previous section, which has about the same number of parameters.

If you are curious, you can see a Keras version of SqueezeNet in the notebook SqueezeNet.ipynb in this chapter. This notebook reproduces the results from Turi with Keras. We're not going to explain that code in detail here since you'll be using an architecture that gets better results than SqueezeNet. However, feel free to play with this notebook — it's fast enough to run on your Mac, no GPU needed.

## Chapter 8: Advanced Convolutional Networks

The output from the squeeze branches into two parallel convolutions, one with a 1×1 window size and the other with a 3×3. Both convolutions have 64 filters, which is why this is called the expand partition of the fire module.

The squeeze layer that follows it reduces these 128 channels back to 16, and so on. As is usual for convnets, the number of channels increases the further you go into the network, but this pattern of reduce-expand repeats several times over.

The reason for using two convolutions on the same data is that using different transformations potentially lets you extract more information. You see similar ideas in the Inception modules from Google's famous Inception-v3 model, which combines 1×1, 3×3, and 5×5 convolutions, and even pooling, into the kind of parallel structure.

The fire module is very effective, by the fact that SqueezeNet is a powerful model — especially for one that has 1.2 million learnable parameters. It scores about 67% correct on the snakes dataset, compared to 40% from the basic convnet of the previous section, which has about the same number of parameters.

If you are curious, you can see a Keras version of SqueezeNet in the notebook SqueezeNet.ipynb in this chapter's resources. This notebook reproduces the results from Turi with Keras. We're not going to explain that code in detail here since you'll be using an architecture that gets better results than SqueezeNet. However, feel free to play with this notebook — it's fast enough to run on your Mac, no GPU needed.

## The Keras functional API

One thing we should mention in this point is the Keras functional API. You've seen how to make a model using Sequential but that is limited to linear pipelines that consist of layers in a row. To code SqueezeNet's branching structures with Keras, you need to specify your model in a slightly different way.

In the file squeezezenet/squeezenet.py, there is a function SqueezeNet(...) that defines the Keras model. It more-or-less does the following:

```
img_input = Input(shape=input_shape)
x = Conv2D(64, 3, padding='valid')(img_input)
```
