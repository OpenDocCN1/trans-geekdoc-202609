Flattening step consists of taking all our Pooled Feature Maps and put them into one single vector.

> This is going to be a huge vector of color even if we reduced the size of the Feature Map in pooled-feature-maps, we have many Pooled Feature Maps.

+   - This single vector is going to be the Input Layer of a future ANN, which is similar to the previous chapter ANN (which had hidden layers), but this ANN has Fully Connected Layers (hidden layers with full connection with all nodes).

![](bbox=[0.495, 0.055, 0.892, 0.206])

Now we can discuss two important points:

+   - Why don't we lose the spatial structure by Flattening all these Feature Maps into one same, single vector?
- By creating, convolution-layer of feature-maps, we extracted the spatial information, by getting some high numbers in each Feature Map, using specific FeatureDetector/filter that we applied on the Input Image.
- These high numbers in each Feature Map preserve the spatial structure of our images, because these are high numbers associated to a specific feature in the input.
- When we apply Max Pooling Step, we keep these numbers because we take the Max-values.
- The Flattening Step just consists of putting all numbers in the cells of each Pooled-Feature-Map of the pooling-layer into one, single vector. Here those high numbers that are associated to a specific feature in the input image (represents the spatial/structural) are still in the flattened-vector.

Hence all the spatial information preserved in this one, huge, flattened-ID-vector.

+   - Why didn't we directly take the pixels of the Input Image and Flatten them into this one, same vector, without applying the previous steps: Convolution and Max-Pooling?

+   - If we flatten all the Input pixels into this huge, one-dimensional vector, each node of this vector will represent one independent pixel of the image.
- We then only get the information of the pixel not the other pixels that are around it.
- We don't get information of how this pixel is spatially connected to the other pixels around it. We don't get any information of the spatial structure around this pixel.

+   - If we use the Convolution and Max Pooling step to create all the Pooled-Feature-Maps, and Flatten all these Maps into this huge, one-dimensional vector
- Then each feature Map corresponds to one specific feature of the image, each node of this flattened-ID-vector will represent the information of a specific feature, a specific detail of the Input Image (for example, the upper layer of a dog node).
- Because this high number doesn't represent a unique pixel itself but study of specific feature, that the Feature extracted from the Input Image, through the Convolution Operation.

And therefore eventually, we keep the spatial structure information of the Input Image.

+   - Flattening the Pooling-layer: As usual, we're gonna take our classifier cnn_classifier, apply same add() method to our classifier and add(add()) to flatten the pooling-layer.

```
### step 3 : Flattening
cnn_classifier.add(Flatten())
```

+   - There is no need to specify any parameters, because Keras will understand that,
- Since we're a cnn_classifier object, that needs to Flatten the previous layer that we obtain in the Max Pooling Step, after the Convolution.

Now this huge, single vector is created and basically it contains all the spatial information of the structure of our images. Then the 4th step is to create a classic ANN, that will classify the images using this huge, single vector, as the Input Vector.