# Machine Learning
Chapter 8: Advanced Convolutional Neural Networks

> **Note:** Depending on your version of Keras, you may also see ZeroPadding2D layers before the DepthwiseConv2D layer, which adds padding around the input sensor so that the convolution works correctly for pixels at the edges. Another small detail: The activation function used is actually **ReLU6**, a variation of ReLU that you've seen before. It works in the same way as ReLU but also prevents the output of the convolution from becoming too large — it limits output to 6, hence the name — which allows for the use of faster limited-precision computations on mobile and embedded devices.

Looking at the model.summary(), you may have noticed that MobileNet does not use any pooling layers, yet the spatial dimensions of the image tensor do become smaller over time — from 224×224 to the beginning to only 7×7 at the end.

MobileNet achieves this pooling by setting the *stride* of some of the Conv2D and DepthwiseConv2D layers to 2 instead of 1.

The *stride* is the size of the steps the convolution kernel takes as it slides through the image. Usually, this step size is 1 and the convolution looks at all the pixels.

With a stride of 2, the window will skip every other pixel, thereby computing products for half the pixels in both the width and height directions. This way you don't need a special pooling layer to make the image smaller.

You'll see both techniques, pooling and larger strides, used in practice.
The final layer in this model outputs a tensor of size (7, 7, 1024). This tensor contains the features that MobileNet has extracted from the input image. You're simply going to add a logistic regression on top of these extracted features, exactly like you've done before.

> **Note:** MobileNet has more learned parameters than SqueezeNet, so it takes up more space in your app bundle and also RAM at runtime. However, thanks to these additional parameters, MobileNet produces higher quality than SqueezeNet. Even better, it's also faster than SqueezeNet due to the depthwise separable convolutions.

Choosing a feature extractor is always a trade-off between quality, storage size and runtime speed. If MobileNet is too large for your app — it adds 8 and 16 MB to your app bundle — then SqueezeNet might be a better choice. But the predictions of a SqueezeNet-based model may be worse and it runs slower.

![](bbox=[0.162, 0.926, 0.837, 0.956])