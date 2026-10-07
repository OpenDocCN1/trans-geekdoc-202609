# Key points

+   - Linear regression is one of the most basic machine-learning models, dating back to the 1800s when Gauss and others discovered the method of Ordinary Least Squares. It models the relationship between different variables. You can turn linear regression into logistic regression with the sigmoid function, making it a classifier

+   - To build a logistic regression classifier in Keras, you just need one Dense layer followed by softmax activation. To use images with the Dense layer, you need to Flatten the image data into a one-dimensional vector first.

+   - To train a model in Keras, you need to choose a loss function — cross-entropy for a classifier — as well as an optimizer. Setting the optimizer’s learning rate is important or the model won’t be able to learn anything.

+   - Load your data with ImageDataGenerator. Use a normalization function to give your data a mean of 0 and a standard deviation of 1. Choose a batch size that fits your GPU — 32 or 64 is a good default choice.

+   - Be sure to check the loss and accuracy of your test set on the untrained model, to see if you get reasonable values. The accuracy should be approximately 1/num_classes, the loss should be close to np. log(num_classes).

+   - Keep your eye on the validation accuracy during training. If it stops improving while the training accuracy continues going up, your model is overfitting.

+   - A classical neural network is just two or more logistic regressions in a row.

+   - Logistic regression and classical feed-forward neural networks are not the best choice for building image classifiers.