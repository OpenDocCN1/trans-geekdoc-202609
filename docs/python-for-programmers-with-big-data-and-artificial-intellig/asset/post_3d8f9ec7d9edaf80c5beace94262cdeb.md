
and Sharp Minima. CoRR abs/1609.04836 (2016).
https://arxiv.org/abs/1609.04836.

- In general, some samples should be used to *validate* the model. If you specify validation data, after each epoch, the model will use it to make predictions and display the *validation loss and accuracy*. You can study these values to tune your layers and the *fit* method's hyperparameters, or possibly change the layer composition of your model. Here, we used the *validation_split* argument to indicate that the model should reserve the *last 10%* (0.1) of the training samples for validation 4—in this case, 6000 samples will be used for validation. If you have separate validation data, you can use the *validation_data* argument (as you'll see in Section 15.9) to specify a tuple containing arrays of samples and target labels. In general, it's better to get *randomly selected* *validation data*. You can use scikit-learn's *train_test_split* function for this purpose (as we'll do later in this chapter), then pass the randomly selected data with the *validation_data* argument.

4 https://keras.io/getting-started/faq/#how-is-the-validation-split-computed.

In the following output, we highlighted the training accuracy (acc) and validation accuracy (val_acc) in bold:

Click here to view code image

```
[37]: cnn.fit(X_train, y_train, epochs=5, batch_size=64,
    validation_split=0.1)
Train on 54000 samples, validate on 6000 samples
Epoch 1/5
54000/54000 [==============================] - 68s 1ms/step - loss: 0.1407 -
Epoch 2/5
54000/54000 [==============================] - 64s 1ms/step - loss: 0.0426 -
Epoch 3/5
54000/54000 [==============================] - 69s 1ms/step - loss: 0.0299 -
Epoch 4/5
54000/54000 [==============================] - 70s 1ms/step - loss: 0.0197 -
Epoch 5/5
54000/54000 [==============================] - 63s 1ms/step - loss: 0.0155 -
[37]: <tensorflow.python.keras.callbacks.History at 0x7f105ba0ada0>
```

In Section 15.7, we'll introduce *TensorBoard*—a TensorFlow tool for visualizing data from your deep-learning models. In particular, we'll view charts showing how the training and validation accuracy and loss values change through the epochs. In Section 15.8, we'll demonstrate Andrej Karpathy's ConvnetJS tool, which trains convnets in your web browser and dynamically visualizes the layers' outputs, including what each convolutional layer “sees” as it learns. Also run his MNIST and CIFAR10 models. These will help you better understand neural networks’ complex operations.

As the training proceeds, the *fit* method outputs information showing you the progress of each epoch, how long the epoch took to execute (in this case, each took 63–70 seconds), and the evaluation metrics for that pass. During the last epoch of this model, the accuracy reached 99.48% for the training samples (`acc`) and 99.27% for the validation samples (`val_acc`). Those are impressive numbers, given that we have not yet tried to tune the hyperparameters or tweak the number and types of the layers, which could lead to even better (or worse) results. Like machine learning, deep learning is an empirical science that benefits from lots of experimentation.

## Evaluating the Model

Now we can check the accuracy of the model on data the model has not yet seen. To do so, we call the model's `evaluate` method, which displays as its output, how long it took to process the test samples (four seconds and 366 microseconds in this case):

Click here to view code image

```
[38]: loss, accuracy = cnn.evaluate(X_test, y_test)
10000/10000 [===================================] - 4s 366us/step

[39]: loss
[39]: 0.026809450998473768

[40]: accuracy
[40]: 0.9917
```

According to the preceding output, our convnet model is 99.17% accurate when predicting the labels for unseen data—and, at this point, we have not tried to tune the model. With a little online research, you can find models that can predict MNIST with nearly 100% accuracy. Try experimenting with different numbers of layers, types of layers and layer parameters and observe how those changes affect your results.

## Making Predictions

The model's `predict method` predicts the classes of the digit images in its argument array (`X_test`):

Click here to view code image

```
[41]: predictions = cnn.predict(X_test)
```

We can check what the first sample digit should be by looking at `y_test[0]`:

Click here to view code image

```
[42]: y_test[0]
[42]: array([0., 0., 0., 0., 0., 0., 0., 1., 0., 0.], dtype=float32)
```

According to this output, the first sample is the digit 7, because the categorical representation of the test sample's label specifies a 1.0 at index 7—recall that we created this representation via `one-hot encoding`.

Let's check the probabilities returned by the `predict` method for the first test sample:

Click here to view code image

```
[43]: for index, probability in enumerate(predictions[0]):
  print(f'{index}: {probability:.10%}')
0: 0.00000000201%
1: 0.000001355%
2: 0.0000186951%
3: 0.0000015494%
4: 0.0000000003%
5: 0.0000000012%
6: 0.0000000000%
7: 99.9999761581%
8: 0.0000005577%
9: 0.0000011416%
```

According to the output, `predictions[0]` indicates that our model believes this digit is a 7 with nearly 100% certainty. Not all predictions have this level of certainty.

## Locating the Incorrect Predictions

Next, we’d like to view some of the *incorrectly* predicted images to get a sense of the ones our model has trouble with. For example, if it’s always mispredicting 8s, perhaps we need more 8s in our training data.

Before we can view incorrect predictions, we need to locate them. Consider `predictions[0]` above. To determine whether the prediction was correct, we must compare the index of the largest probability in `predictions[0]` to the index of the element containing `1.0` in `y_test[0]`. If these index values are the same, then the prediction was correct; otherwise, it was incorrect. NumPy’s `argmax` function determines the index of the highest valued element in its array argument. Let’s use that to locate the incorrect predictions. In the following snippet, `p` is the predicted value array, and `e` is the expected value array (the expected values are the labels for the dataset’s test images):

Click here to view code image

```
[44]: images = X_test.reshape((10000, 28, 28))
incorrect_predictions = []
for i, (p, e) in enumerate(zip(predictions, y_test)):
  predicted, expected = np.argmax(p), np.argmax(e)
  if predicted != expected:
    incorrect_predictions.append(
      (i, images[i], predicted, expected))
```

In this snippet, we first reshape the samples from the shape `(28, 28, 1)` that Keras required for learning back to `(28, 28)`, which Matplotlib requires to display the images. Next, we populate the list `incorrect_predictions` using the `for` statement. We zip the rows that represent each sample in the arrays `predictions` and `y_test`, then enumerate those so we can capture their indexes. If the `argmax` results for `p` and `e` are different, then the prediction was incorrect, and we append a tuple to `incorrect_predictions` containing that sample’s index, image, the `predicted` value and the `expected` value. We can confirm the total number of incorrect predictions (out of 10,000 images in the test set) with:

```
[45]: len(incorrect_predictions)
[45]: 83
```

## Visualizing Incorrect Predictions

The following snippet displays 24 of the incorrect images labeled with each image’s index, predicted value (p) and expected value (e):

Click here to view code image

```
[46]: figure, axes = plt.subplots(nrows=4, ncols=6, figsize=(16, 12))
for axes, item in zip(axes.ravel(), incorrect_predictions):
    index, image, predicted, expected = item
    axes.imshow(image, cmap=plt.cm.gray_r)
    axes.set_xticks([]) # remove x-axis tick marks
    axes.set_yticks([]) # remove y-axis tick marks
    axes.set_title(
    f'index: {index}\np: {predicted}; e: {expected}')
plt.tight_layout()
```

Before reading the expected values, look at each digit and write down what digit you think it is. This is an important part of getting to know your data:

![](img/34b7fc2f1ee27beb73bca14927d42340_705_0.png)

## Displaying the Probabilities for Several Incorrect Predictions

Let's look at the probabilities of some incorrect predictions. The following function displays the probabilities for the specified prediction array:
