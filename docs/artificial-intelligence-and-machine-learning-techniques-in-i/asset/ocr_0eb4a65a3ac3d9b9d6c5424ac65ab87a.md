The combination of labeled ($L_L$), unlabeled ($L_U$), and generated ($L_G$) loss function is used for optimization process.<sup>4</sup> The equations are given below,

```
\( L = L_L + L_U + L_G \quad \text{(3.2)}\)

\( L_L = E_{r,s \sim P_{data}} \, log p_{model} \left( s | r, s < K + 1 \right) \quad \text{(3.3)}\)

\( L_U = E_{r \sim P_{data}} \, log(1 - p_{model} \left( s = K + 1 | r \right)) \quad \text{(3.4)}\)

\( L_G = E_{r \sim G} \, log p_{model} \left( s = K + 1 | r \right) \quad \text{(3.5)}\)
```

From the above equations, the notion \( r \) defines real image, \( s \) indicates label, and \( P_{data} \) corresponds to real-data distribution. The SSGAN used K class for generated image while K + 1 class represented for fake image class. The following Figures 3.4 and 3.5 show the schematic representation of generator and discriminator layers.

The SSGAN was designed to handle images of 32 × 32 pixels. At initial stage testing, the BreakHis histopathology image was converted into 32 × 32 pixels and analyzed using conventional algorithms. Due to the resizing, the images suffered from information loss which causes poor performance. Hence, the SSGAN is modified to use the original size of dataset with 700 × 460. The discriminator input layer size was adjusted to 224 × 224 × 3. In the subsequent layers, the reshape layer of the generator was adjusted to 28 × 28 × 256, followed by three convolutional transpose layers, each of which produced images with 224 × 224 pixels of color. The training was performed by dividing the entire training process into mini-batches. The weight has been updated in each stage of dividing the training samples. The input data were normalized by dividing each range by 1. The activation function of Relu was used in the last generator layer.

In eq (3.3), the supervised loss function is calculated after training the discriminator with labeled data and holding the generator weights. In eq (3.4), the unsupervised loss function using discriminator trained on unlabeled data and fake data. As a result, in eq (3.5), the discriminator loss function was calculated by adding both losses together. The back-propagation procedure was utilized to update the discriminator weights. After updating the discriminator, the evaluated weight is fixed froze then the generator training was performed. The mini-batch samples included half-real data and half-fictitious data. Using the discriminator, mini-batch