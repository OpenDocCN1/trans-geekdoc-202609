
### 2.6.8 Softmax regression of spiral data set

Train the softmax regression model on the previous 3-category spiral dataset:

```python
def compute_loss_history(w_history, X, y, reg=0., OneHot=False):
    loss_history = []
    X = np.hstack((np.ones((X.shape[0], 1), dtype=X.dtype), X))
    if OneHot:
        for w in w_history:
            loss_history.append(loss_softmax_onthot(w, X, y, reg))
    else:
        for w in w_history:
            loss_history.append(loss_softmax(w, X, y, reg))
    return loss_history
```

```python
X_spiral, y_spiral = gen_spiral_dataset()
X = X_spiral
y = y_spiral

alpha = 1e-0
iterations = 200
reg = 1e-3

w = np.zeros([X.shape[1] + 1, len(np.unique(y))])
w_history = gradient_descent_softmax(w, X, y, reg, alpha, iterations)
w = w_history[-1]
print("w: ", w)
loss_history = compute_loss_history(w_history, X, y, reg)
print(loss_history[:-1:len(loss_history)//10])
plt.plot(loss_history, color='r')
```

```
w: [[-0.05432759  0.00909428  0.04523331]
 [ 1.33458061  1.00350822 -2.33808883]
 [-2.34741204  2.66497338 -0.31756134]]
[1.0676120053842029, 0.8282060256848282, 0.7842866954902825, 0.7712475770990912, 0.7664708448591956, 0.7645211840017035, 0.7636739840781024, 0.7632912248183761, 0.7631138695802607, 0.763030293277599]
```

![](EPUB/media/file78.png)

**Figure 3-43 Training loss curve**

The following function can calculate the prediction accuracy of the trained model on a batch of data (`X`, `y`):

```python
def getAccuracy(w, X, y):
    X = np.hstack((np.ones((X.shape[0], 1), dtype=X.dtype), X))
    probs = softmax(np.dot(X, w))
    predicts = np.argmax(probs, axis=1)
    accuracy = sum(predicts == y) / (float(len(y)))
    return accuracy
```

Use `getAccuracy()` to calculate the prediction accuracy of the trained softmax model for the data set just now.

```python
getAccuracy(w, X_spiral, y_spiral)
```

```
0.5366666666666666
```

The following code plots the classification boundaries of the softmax model for this problem:

```python
# plot the resulting classifier
h = 0.02
x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1
xx, yy = np.meshgrid(np.arange(x_min, x_max, h),
                     np.arange(y_min, y_max, h))

Z = np.dot(np.c_[np.ones(xx.size), xx.ravel(), yy.ravel()], w)
Z = np.argmax(Z, axis=1)
Z = Z.reshape(xx.shape)
fig = plt.figure()
plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral, alpha=0.3)
plt.scatter(X[:, 0], X[:, 1], c=y, s=40, cmap=plt.cm.Spectral)
plt.xlim(xx.min(), xx.max())
plt.ylim(yy.min(), yy.max())
# fig.savefig('spiral_linear.png')
```

```
(-1.908218802050246, 1.9517811979497575)
```

![](EPUB/media/file79.png)

**Figure 3-44 Classification of the three-category data point set**

It can be seen that the softmax regression is still a linear function model in essence, and the dividing lines are all straight lines on the graph. It is difficult to segment the data nonlinearly. The accuracy of the model is `0.5366666666666666`.

## 3.7 Batch Gradient Descent and Stochastic Gradient Descent

### 3.7.1 MNIST handwritten digit set

The MNIST handwritten digit training set is some images of handwritten digits, and each image is a handwritten digit. There are 10 digit images of 0,1,...,9 in the sample dataset. So this is a 10 classification problem.

The following code reads the MNIST handwritten digit training set:

```python
import pickle, gzip, urllib.request, json
import numpy as np
import os.path

if not os.path.isfile("mnist.pkl.gz"):
    # Load the dataset
    urllib.request.urlretrieve("http://deeplearning.net/data/mnist/mnist.pkl.gz", "mnist.pkl.gz")

with gzip.open('mnist.pkl.gz', 'rb') as f:
    train_set, valid_set, test_set = pickle.load(f, encoding='latin1')

train_X, train_y = train_set
valid_X, valid_y = valid_set
test_X, test_y = test_set  # Fixed: was valid_set in original
print(train_X.shape, train_y.shape)
print(valid_X.shape, valid_y.shape)
print(test_X.shape, test_y.shape)
print(train_X.dtype, train_y.dtype)
print(train_X[9][300], train_y[9])
print(np.min(train_y), np.max(train_y))
```

```
(50000, 784) (50000,)
(10000, 784) (10000,)
(10000, 784) (10000,)
float32 int64
0.98828125 4
0 9
```

The training set has 50,000 samples, and the validation and test sets each have 10,000 samples. Each pixel value of the image is a real number of float type, and the value range is a real number between `[0, 1]`, indicating the grayscale intensity of each pixel, and the label value indicates the digital classification corresponding to the image, using 0, 1, 2, ..., 9 represent.

The following code visualizes one of these images:

```python
import matplotlib.pyplot as plt
%matplotlib inline
digit = train_X[9].reshape(28, 28)
plt.subplot(1, 2, 1)
plt.imshow(digit)
plt.colorbar()
plt.subplot(1, 2, 2)
plt.imshow(digit, cmap='gray')
plt.colorbar()
plt.show()
```

![](EPUB/media/file80.png "fig:")

**Figure 3-44 Images of handwritten digits from the Mnist dataset**

Continue outputting the few pixel values (data features) in that sample.

```python
print(train_X.shape)
print(train_X[9][200:250])
```

```
(50000, 784)
[0. 0. 0. 0. 0. 0.
 0. 0. 0. 0. 0. 0.
 0. 0. 0. 0. 0.75 0.984375
 0.73046875 0. 0. 0. 0. 0.
 0. 0. 0. 0. 0. 0.
 0. 0. 0. 0. 0. 0.
 0.2421875 0.72265625 0.0703125 0. 0. 0.
 0. 0.34765625 0.921875 0.84765625 0.18359375 0.
 0. 0.]
```

### 3.7.2 Training logistic regression with partial training samples

The number of samples in the training set reaches 50,000. Using the samples of the entire training set for training requires a lot of resources and time for each calculation. In order to improve the training efficiency, some data can be taken out, such as training with `batch=500` samples:

```python
batch = 500

alpha = 1e-2
iterations = 1000
reg = 1e-3

w_history = []

w = np.zeros([train_X.shape[1] + 1, len(np.unique(train_y))])
for i in range(5):
    s = i * batch
    X = train_X[s:s + batch, :]
    y = train_y[s:s + batch]
    w_history_batch = gradient_descent_softmax(w, X, y, reg, alpha, iterations)
    w = w_history_batch[-1]
    w_history.extend(w_history_batch)

print("w: ", w)
loss_history = compute_loss_history(w_history, X, y, reg)
print(loss_history[:-1:len(loss_history)//10])
```

Calculate the accuracy of the model function on the training set, validation set, and test set respectively:

```python
print("Accuracy on the training set:", getAccuracy(w, train_X, train_y))
print("Validation set accuracy:", getAccuracy(w, valid_X, valid_y))
print("Accuracy on test set:", getAccuracy(w, test_X, test_y))
```

```
Accuracy on training set: 0.88412
Validation set accuracy: 0.8979
Accuracy on test set: 0.8979
```

Iterative loss learning curves for training and validation sets can be plotted:

```python
loss_history_valid = compute_loss_history(w_history, valid_X[0:1000, :], valid_y[0:1000], reg)

plt.plot(loss_history, color='r')
plt.plot(loss_history_valid, color='b')
plt.ylim(0, 5)
plt.xlabel('iterations')
plt.ylabel('loss')
plt.title('iterative learning curve')
plt.legend(['train', 'valid'])
plt.ylim(-0.2, 3)
plt.show()
```

![](EPUB/media/file81.png)

**Figure 3-45 Training loss curve**

### 3.7.3 Batch Gradient Descent Method and Implementation

If the training set is large, the training becomes very large when using the entire training set. In fact, as long as a small number or even one sample is used, the gradient of the loss function can be calculated and the model parameters can be updated. Therefore, in practical problems, a small number of samples are usually randomly selected from the training set, and this batch of samples is used to perform gradient updates on the model parameters. A different batch of samples can be used for each gradient update. This gradient descent method is called **batch gradient descent** (**mini batch gradient descent**). In order to ensure that all samples in the training set can be used for training.

The general approach of the batch gradient descent method is:
