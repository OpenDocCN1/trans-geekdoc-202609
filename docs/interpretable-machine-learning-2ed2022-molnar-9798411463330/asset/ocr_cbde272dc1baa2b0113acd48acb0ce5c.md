The predictions by much. Therefore, variations of the images are created by segmenting the image into “superpixels” and turning superpixels off or on. Superpixels are interconnected pixels with similar colors and can be turned off by replacing each pixel with a user-defined color such as gray. The user can also specify a probability for turning off a superpixel in permutation.

# 8.2.3.1 Example

In this example we look at a classification made by the Inception V3 neural network. The image used some bread I baked which are in a bowl. Since we have several predicted labels per image (sorted by probability), we can explain the top labels. The prediction is “Bagel” with a probability of 77%, followed by “Strawberry” with a probability of 4%. The following images show for “Bagel” and “Strawberry” the LIME explanations. The explanations can be displayed directly on the image samples. Green means that this part of the image increases the probability for the label and red means a decrease.

![](bbox=[0.232, 0.413, 0.833, 0.559])

Figure 8.8: Left: Image of a bowl of bread. Middle and right: LIME explanations for the top 2 classes (bagel, strawberry) for image classification made by Google’s Inception V3 neural network.

The prediction and explanation for “Bagel” are very reasonable, even if the prediction is wrong – these are clearly no bagels since the hole in the middle is missing.

# 8.2.4 Advantages

Even if you replace the underlying machine learning model, you can still the same local, interpretable model for explanation. Suppose the people looking at the explanations understand decision trees best. Because you use local surrogates, you use decision trees as explanations without actually having to use a decision tree to make the predictions. For example, you can use a SVM. And if it turns out that an xgboost model works better, you replace the SVM and still use a decision tree to explain the predictions.

Local surrogates benefit from the literature and experience of training and interpreting interpretable models.