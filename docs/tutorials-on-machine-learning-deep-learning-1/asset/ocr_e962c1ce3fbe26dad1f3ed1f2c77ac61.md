# 9.5.10 Compilation: CNN model

We just need to compile the NN by choosing a SGD algorithm, a loss function and, eventually, a performance metric. It is as same as the classic-CNN in the previous chapter.

```
# compile the NN
nn_classifier.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
```

We apply compile() over our c classifier cnn_classifier.

+   Parameters:
- optimizer: adam specifies the SGD algorithm It is the Adam algorithm.

+   Loss: we choose the binary_crossentropy for two reasons:
- First of all, because this function performs the logarithmic loss, which is the loss function we use in general for classification problems using a classification modellike logistic regression.
- The second reason is that we have a binary outcome, cat or dog, and therefore, we need to choose the binary-crossentropy loss function.
- If we have more than two classes, like cats, dogs, and birds, we would need to choose categorical-cross-entropy loss function.
- metrics: To choose the performance metric The most common performance metric is the accuracy metric.

![](bbox=[0.105, 0.372, 0.894, 0.658])

# 9.5.11 Image Preprocessing

We just completed part: Building the CNN We designed the architecture of our CNN.

+   Now we're beginning part two: Image Preprocessing where we will fit our CNN to our images.
- We will do it in one step because we're gonna use a shortcut, the Keras Documentation.

+   We will use Keras Documentation for a process called image augmentation, which basically consists of preprocessing your images to prevent overfitting
- If we don't do this Image Augmentation, we will get a great accuracy on the training set, but a much lower accuracy on the test set.

Image Augmentation Purpose: We know that one of the situations that lead to overfitting is when we have few data to train our model. In this situation, our model finds some correlations in the few observations of the training set, but fail to generalize this correlations on some observations.

And when it comes to we actually need a lot of images to train and generalize some correlations, because in Computer Vision, our model doesn't need to find correlations between independent and dependent variables. It needs some patterns in the pixels, and to do this it requires a lot of images.