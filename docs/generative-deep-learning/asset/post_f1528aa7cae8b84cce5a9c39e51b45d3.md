
image. The same idea applies to the filters in the second convolutional layer that have a depth of 10, to match the 10 channels output by the first convolutional layer.

![](img/f0f0f5d89818fdddf117bbe758ac8143_71_0.png)

In general, the depth of the filters in a layer is always equal to the number of channels output by the preceding layer.

## Inspecting the model

It’s really informative to look at how the shape of the tensor changes as data flows through from one convolutional layer to the next. We can use the model.summary() method to inspect the shape of the tensor as it passes through the network (Table 2-2).

Table 2-2. CNN model summary

| Layer (type) | Output shape | Param # |
|---|---|---|
| InputLayer | (None, 32, 32, 3) | 0 |
| Conv2D | (None, 16, 16, 10) | 490 |
| Conv2D | (None, 8, 8, 20) | 1,820 |
| Flatten | (None, 1280) | 0 |
| Dense | (None, 10) | 12,810 |

Total params 15,120
Trainable params 15,120
Non-trainable params 0

Let’s walk through our network layer by layer, noting the shape of the tensor as we go:

- 1. The input shape is (None, 32, 32, 3)—Keras uses None to represent the fact that we can pass any number of images through the network simultaneously. Since the network is just performing tensor algebra, we don’t need to pass images through the network individually, but instead can pass them through together as a batch.
- 2. The shape of each of the 10 filters in the first convolutional layer is 4 × 4 × 3. This is because we have chosen each filter to have a height and width of 4 (kernel_size = (4,4)) and there are three channels in the preceding layer (red, green, and blue). Therefore, the number of parameters (or weights) in the layer is (4 × 4 × 3 + 1) × 10 = 490, where the + 1 is due to the inclusion of a bias term attached to each of the filters. The output from each filter will be the pixelwise multiplication of the filter weights and the 4 × 4 × 3 section of the image it is covering. As strides = 2 and padding = "same", the width and height of the output are both halved to 16, and since there are 10 filters the output of the first layer is a batch of tensors each having shape [16, 16, 10].
- 3. In the second convolutional layer, we choose the filters to be 3 × 3 and they now have depth 10, to match the number of channels in the previous layer. Since there are 20 filters in this layer, this gives a total number of parameters (weights) of (3 × 3 × 10 + 1) × 20 = 1,820. Again, we use strides = 2 and padding = "same", so the width and height both halve. This gives us an overall output shape of (None, 8, 8, 20).
- 4. We now flatten the tensor using the Keras Flatten layer. This results in a set of 8 × 8 × 20 = 1,280 units. Note that there are no parameters to learn in a Flatten layer as the operation is just a restructuring of the tensor.
- 5. We finally connect these units to a 10-unit Dense layer with softmax activation, which represents the probability of each category in a 10-category classification task. This creates an extra 1,280 × 10 = 12,810 parameters (weights) to learn.

This example demonstrates how we can chain convolutional layers together to create a convolutional neural network. Before we see how this compares in accuracy to our densely connected neural network, we’ll examine two more techniques that can also improve performance: batch normalization and dropout.

## Batch Normalization

One common problem when training a deep neural network is ensuring that the weights of the network remain within a reasonable range of values—if they start to become too large, this is a sign that your network is suffering from what is known as the exploding gradient problem. As errors are propagated backward through the network, the calculation of the gradient in the earlier layers can sometimes grow exponentially large, causing wild fluctuations in the weight values.

![](img/f0f0f5d89818fdddf117bbe758ac8143_72_0.png)

If your loss function starts to return NaN, chances are that your weights have grown large enough to cause an overflow error.

This doesn’t necessarily happen immediately as you start training the network. Sometimes it can be happily training for hours when suddenly the loss function returns NaN and your network has exploded. This can be incredibly annoying. To prevent it from happening, you need to understand the root cause of the exploding gradient problem.

### Covariate shift

One of the reasons for scaling input data to a neural network is to ensure a stable start to training over the first few iterations. Since the weights of the network are initially randomized, unscaled input could potentially create huge activation values that immediately lead to exploding gradients. For example, instead of passing pixel values from 0–255 into the input layer, we usually scale these values to between –1 and 1.

Because the input is scaled, it’s natural to expect the activations from all future layers to be relatively well scaled as well. Initially this may be true, but as the network trains and the weights move further away from their random initial values, this assumption can start to break down. This phenomenon is known as covariate shift.

![](img/f0f0f5d89818fdddf117bbe758ac8143_73_0.png)

### Covariate Shift Analogy

Imagine you’re carrying a tall pile of books, and you get hit by a gust of wind. You move the books in a direction opposite to the wind to compensate, but as you do so, some of the books shift, so that the tower is slightly more unstable than before. Initially, this is OK, but with every gust the pile becomes more and more unstable, until eventually the books have shifted so much that the pile collapses. This is covariate shift.

Relating this to neural networks, each layer is like a book in the pile. To remain stable, when the network updates the weights, each layer implicitly assumes that the distribution of its input from the layer beneath is approximately consistent across iterations. However, since there is nothing to stop any of the activation distributions shifting significantly in a certain direction, this can sometimes lead to runaway weight values and an overall collapse of the network.

### Training using batch normalization

Batch normalization is a technique that drastically reduces this problem. The solution is surprisingly simple. During training, a batch normalization layer calculates the mean and standard deviation of each of its input channels across the batch and normalizes by subtracting the mean and dividing by the standard deviation. There are then two learned parameters for each channel, the scale (gamma) and shift (beta). The output is simply the normalized input, scaled by gamma and shifted by beta. Figure 2-14 shows the whole process.

```
Input: Values of x over a mini-batch: B = {x1...m};
Parameters to be learned: γ, β
Output: {yi = BNγ,β(xi)}

μB ← 1/m Σ_{i=1}^m xi          // mini-batch mean
σ_B^2 ← 1/m Σ_{i=1}^m (xi - μB)^2   // mini-batch variance
\hat{x}_i ← (xi - μB) / sqrt(σ_B^2 + ε)      // normalize
y_i ← γ \hat{x}_i + β ≡ BN_{γ,β}(xi)   // scale and shift
```

Algorithm 1: Batch Normalizing Transform, applied to activation x over a mini-batch.

Figure 2-14. The batch normalization process (source: Ioffe and Szegedy, 2015)⁶

We can place batch normalization layers after dense or convolutional layers to normalize the output.

![](img/f0f0f5d89818fdddf117bbe758ac8143_74_0.png)

Referring to our previous example, it's a bit like connecting the layers of books with small sets of adjustable springs that ensure there aren't any overall huge shifts in their positions over time.

### Prediction using batch normalization

You might be wondering how this layer works at prediction time. When it comes to prediction, we may only want to predict a single observation, so there is no batch over which to calculate the mean and standard deviation. To get around this problem, during training a batch normalization layer also calculates the moving average of the mean and standard deviation of each channel and stores this value as part of the layer to use at test time.

How many parameters are contained within a batch normalization layer? For every channel in the preceding layer, two weights need to be learned: the scale (gamma) and shift (beta). These are the trainable parameters. The moving average and standard deviation also need to be calculated for each channel, but since they are derived from the data passing through the layer rather than trained through backpropagation, they are called nontrainable parameters. In total, this gives four parameters for each channel in the preceding layer, where two are trainable and two are nontrainable.
