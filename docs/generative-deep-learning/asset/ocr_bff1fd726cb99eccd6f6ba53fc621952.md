```
padding="valid",
)(x) ④

out = layers.Conv2D(
    filters=4, kernel_size=1, strides=1, activation="softmax", padding="valid"
)(x) ⑤

pixel_cnn = models.Model(inputs, out) ⑥

adam = optimizers.Adam(learning_rate=0.0005)
pixel_cnn.compile(optimizer=adam, loss="sparse_categorical_crossentropy")

pixel_cnn.fit(
    input_data
  , output_data
  , batch_size=128
  , epochs=150
) ⑦
```

① The model Input is a grayscale image of size 16 × 16 × 1, with inputs scaled between 0 and 1.

② The first Type A MaskedConv2D layer with a kernel size of 7 uses information from 24 pixels—21 pixels in the three rows above the focus pixel and 3 to the left (the focus pixel itself is not used).

③ Five ResidualBlock layer groups are stacked sequentially.

④ Two Type B MaskedConv2D layers with a kernel size of 1 act as Dense layers across the number of channels for each pixel.

⑤ The final Conv2D layer reduces the number of channels to four—the number of pixel levels for this example.

⑥ The Model is built to accept an image and output an image of the same dimensions.

⑦ Fit the model—input_data is scaled in the range [0, 1] (floats); output_data is scaled in the range [0, 3] (integers).

# Analysis of the PixelCNN

We can train our PixelCNN on images from the Fashion-MNIST dataset that we encountered in Chapter 3. To generate new images, we need to ask the model to predict the next pixel given all preceding pixels, one pixel at a time. This is a very slow process compared to a model such as a variational autoencoder! For a 32 × 32