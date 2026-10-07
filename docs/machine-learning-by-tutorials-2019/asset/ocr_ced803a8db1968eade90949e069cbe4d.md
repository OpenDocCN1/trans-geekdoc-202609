Because we only care about whether a certain pattern was detected, but not where, taking the average of its 28×28 heatmap is good enough. If nothing was detected, then this average is a small number close to zero. If something was detected, the average will be a high number. The stronger the detection, the higher the number.

After this global average pooling layer, you now have a 256-element vector that says which of the 256 patterns were detected in the original input image and how strong these detections are. But because you still don't really know what these 256 patterns represent, you can't use them to directly draw conclusions from. But you can use them as features for the logistic regression.

That's why the final two layers in the model are a Dense layer followed by a softmax activation. They serve the same purpose as before: to perform logistic regression on top of the extracted features. The convolutional layers and pooling layers now act as a feature extractor that converts the original pixels into features that are more suitable for use with logistic regression.

And logistic regression learns which combinations of the detected patterns belong to the different classes that you want to detect.

> **Note:** The global pooling layer flattens the four-dimensional image tensor into a two-dimensional feature vector (where the first dimension is the batch size). Unlike a Flat layer, which always expects a fixed number of input features, a global pooling layer can work on images of any arbitrary input size. Models with a Flat layer are therefore much less flexible and not considered to be "fully convolutional". Most modern convnets use a global pooling layer so that they can accept images of any size. Remember: for the best results, images used for inference shouldn't be too much larger or smaller than the images the model was trained on.

# # Training the model

The model you’ve built in the previous sections is a typical convnet design, and although not necessarily the optimal—it’s a good start. Let’s see how well this model learns.

As usual, compile the model before use:

```
model.compile(loss="categorical_crossentropy",n              optimizer=optimizers.Adam(lr=1e-3),
              metrics=["accuracy"]
```