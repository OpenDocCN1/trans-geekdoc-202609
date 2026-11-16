

![](img/34b7fc2f1ee27beb73bca14927d42340_689_0.png)

Looking at the digits, you can see why handwritten digit recognition is a challenge:

- Some people write “open” 4s (like the ones in the first and third rows), and some write “closed” 4s (like the one in the second row). Though each 4 has some similar features, they’re all different from one another.

- The 3 in the second row looks strange—more like a merged 6 and 7. Compare this to the much clearer 3 in the fourth row.

- The 5 in the second row could easily be confused with a 6.

- Also, people write their digits at different angles, as you can see with the four 6s in the third and fourth rows—two are upright, one leans left and one leans right.

If you run the preceding snippet multiple times, you can see additional randomly selected digits. 8 You’ll probably find that—if not for the labels displayed above each digit—it would be difficult for you to identify some of the digits. We’ll soon see how accurately our first convnet will predict the digits in the MNIST test set.

8 If you do run the cell multiple times, the snippet number next to the cell will increment each time, as it does in IPython at the command line.

## 15.6.3 Data Preparation

Recall from the “Machine Learning” chapter that Scikit-learn’s bundled datasets were preprocessed into the shapes its models required. In real-world studies, you’ll generally have to do some or all of the data preparation. The MNIST dataset requires some preparation for use in a Keras convnet.

### Reshaping the Image Data

Keras convnets require NumPy array inputs in which each sample has the shape:

```
(width, height, channels)
```

For MNIST, each image's width and height are 28 pixels, and each pixel has one channel (the grayscale shade of the pixel from 0 to 255), so each sample's shape will be:

```
(28, 28, 1)
```

Full-color images with RGB (red/green/blue) values for each pixel, would have three channels—one channel each for the red, green and blue components of a color.

As the neural network learns from the images, it creates many more channels. Rather than shade or color, the learned channels will represent more complex features, like edges, curves and lines, that will eventually enable the network to recognize digits based on these additional features and how they're combined.

Let's reshape the 60,000 training and 10,000 testing set images into the correct dimensions for use in our convnet and confirm their new shapes. Recall that NumPy array method reshape receives a tuple representing the array's new shape:

Click here to view code image

```
[12]: X_train = X_train.reshape((60000, 28, 28, 1))
[13]: X_train.shape
[13]: (60000, 28, 28, 1)
[14]: X_test = X_test.reshape((10000, 28, 28, 1))
[15]: X_test.shape
[15]: (10000, 28, 28, 1)
```

### Normalizing the Image Data

Numeric features in data samples may have value ranges that vary widely. Deep learning networks perform better on data that is scaled either into the range 0.0 to 1.0, or to a range for which the data's mean is 0.0 and its standard deviation is 1.0. Getting your data into one of these forms is known as normalization.

9 S. Ioffe and Szegedy, C.. Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift. https://arxiv.org/abs/1502.03167.

In MNIST, each pixel is an integer in the range 0–255. The following statements convert the values to 32-bit (4-byte) floating-point numbers using the NumPy array method astype, then divide every element in the resulting array by 255, producing normalized values in the range 0.0–1.0:

Click here to view code image

```
[16]: X_train = X_train.astype('float32') / 255
[17]: X_test = X_test.astype('float32') / 255
```

### One-Hot Encoding: Converting the Labels From Integers to Categorical Data

As we mentioned, the convnet's prediction for each digit will be an array of 10 probabilities, indicating the likelihood that the digit belongs to a particular one of the classes 0 through 9. When we evaluate the model's accuracy, Keras compares the model's predictions to the labels. To do that, Keras requires both to have the same shape. The MNIST label for each digit, however, is one integer value in the range 0–9. So, we must transform the labels into **categorical data**—that is, arrays of categories that match the format of the predictions. To do this, we'll use a process called **one-hot encoding**, which converts data into arrays of 1.0s and 0.0s in which only one element is 1.0 and the rest are 0.0s. For MNIST, the one-hot-encoded values will be 10-element arrays representing the categories 0 through 9. One-hot encoding also can be applied to other types of data.

This term comes from certain digital circuits in which a group of bits is allowed to have only one bit turned on (that is, to have the value 1). https://en.wikipedia.org/wiki/One-hot.

We know precisely which category each digit belongs to, so the categorical representation of a digit label will consist of a 1.0 at that digit's index and 0.0s for all the other elements (again, Keras uses floating-point numbers internally). So, a 7's categorical representation is:

Click here to view code image

```
[0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0]
```

and a 3's representation is:

Click here to view code image

```
[0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
```

The tensorflow.keras.utils module provides function to_categorical to perform one-hot encoding. The function counts the unique categories then, for each item being encoded, creates an array of that length with a 1.0 in the correct position. Let's transform y_train and y_test from one-dimensional arrays containing the values 0–9 into two-dimensional arrays of categorical data. After doing so, the rows of these arrays will look like those shown above. Snippet [21] outputs one sample's categorical data for the digit 5 (recall that NumPy shows the decimal point, but not trailing 0s on floating-point values):

Click here to view code image

```
[18]: from tensorflow.keras.utils import to_categorical

[19]: y_train = to_categorical(y_train)

[20]: y_train.shape
[20]: (60000, 10)

[21]: y_train[0]
[21]: array([ 0., 0., 0., 0., 0., 1., 0., 0., 0., 0.], dtype=float32)

[22]: y_test = to_categorical(y_test)
```

```
[23]: y_test.shape

[23]: (10000, 10)
```

## 15.6.4 Creating the Neural Network

Now that we've prepared the data, we'll configure a convolutional neural network. We begin with the Keras Sequential model from the tensorflow.keras.models module:

Click here to view code image

```
[24]: from tensorflow.keras.models import Sequential

[25]: cnn = Sequential()
```

The resulting network will execute its layers sequentially—the output of one layer becomes the input to the next. This is known as a feed-forward network. As you'll see when we discuss recurrent neural networks, not all neural network operate this way.

### Adding Layers to the Network

A typical convolutional neural network consists of several layers—an input layer that receives the training samples, hidden layers that learn from the samples and an output layer that produces the prediction probabilities. We'll create a basic convnet here. Let's import from the tensorflow.keras.layers module the layer classes we'll use in this example:

Click here to view code image

```
[26]: from tensorflow.keras.layers import Conv2D, Dense, Flatten, MaxPooling2D
```

We discuss each below.

### Convolution

We'll begin our network with a convolution layer, which uses the relationships between pixels that are close to one another to learn useful features (or patterns) in small areas of each sample. These features become inputs to subsequent layers.

The small areas that convolution learns from are called kernels or patches. Let's examine convolution on a 6-by-6 image. Consider the following diagram in which the 3-by-3 shaded square represents the kernel—the numbers are simply position numbers showing the order in which the kernels are visited and processed:

