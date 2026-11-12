
is. The way we have the side branches in-between, we have an estimation about the loss associated with each side branch. The features associated with side branches also know what they want to accomplish. If these side branches are not here, these inception modules will get information about the loss by backpropagating from the final classifier or output:

![](img/7e519fee1b702b91799cdf1664598392_354_0.png)

Figure 4.194: GoogLeNet architecture

![](img/7e519fee1b702b91799cdf1664598392_355_0.png)

Figure 4.195: Simplified GoogLeNet architecture

Residual inception modules: These IMs use the concept of residual networks so that whatever information collected by these IMs in the previous layer of the convolutional network, then at least that amount of information, which is achieved during the previous layer should not be lost, provided that we are not getting anything more in next few upcoming layers, as shown in figure 4.196:

![](img/7e519fee1b702b91799cdf1664598392_356_0.png)

Figure 4.196: Residual inception module

## Conclusion

This chapter is mainly focused on convolutional neural networks. In this chapter, we have explored various layers of CNN. We have discussed the concepts of padding, stride, and pooling in CNN with suitable examples, along with one- and two-dimensional convolution. We have also visualized the working of a three-dimensional filter in 2-D convolution. Moreover, we have shown the working of CNN with an illustrative example under the section How CNN works? Finally, CNN case studies are discussed with their architectures with corresponding parameters. At last, the reader can build their own CNN model for image classification by going through the entire chapter.

In the next chapter, we will start with object detection and localization.

## Web resources

- Intel Deep Learning Course https://software.intel.com/en-us/ai/courses/deep-learning/week6.
- Stanford University Deep Learning Course http://cs231n.stanford.edu/.
- A Beginner’s Guide To Understanding Convolutional Neural Networks https://adeshpande3.github.io/adeshpande3.github.io/A-Beginner’s-Guide-To-Understanding-Convolutional-Neural-Networks/.
- LeNet-5 http://deeplearning.net/tutorial/lenet.html.
- An intuitive explanation of CNN https://ujjwalkarn.me/2016/08/11/intuitive-explanation-convnets/.

## Subjective questions

- 1. Draw and explain the architecture of the generic convolution neural network.
- 2. Explain different types of layers of CNN.
- 3. Explain the terms correlation and convolution in detail.
- 4. Explain the spatial filter and its types.
- 5. Explain different types of smoothing filters.
- 6. Explain the term Laplacian filter with an example.
- 7. What are the different types of pooling in CNN?
- 8. Draw and explain the architecture of LeNet-5.
- 9. Draw and explain the architecture of AlexNet.
- 10. Draw and explain the architecture of VGG-16.

## Multiple choice questions

- 1. **While using a 1×1 convolution in a CNN, which of the following statements is true.**

  - a. It reduces the dimensionality of the input image.
  - b. Feature pooling can be achieved.
  - c. Less Overfitting.
  - d. All of the above.

- 2. **The input to a convolution layer is an image of size 28 * 28 and a filter of size 7 * 7, and a stride of 1. What will be the size of the convoluted matrix?**

  - a. 22 * 22
  - b. 28 * 28
  - c. 21 * 21
  - d. 7 * 7

- 3. **The input image matrix I is:**

| | | | | | | |
|---|---|---|---|---|---|---|
| 1 | 0 | 0 | 1 | 1 | 0 | 1 |
| 0 | 0 | 1 | 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 |
| 0 | 1 | 1 | 0 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 | 0 | 1 | 1 |

And filter F is:

| 1 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 1 | 0 |

What is the convolution output C with a stride of 2?

a.
| 4 | 4 | 3 | 3 | 3 |
| 4 | 4 | 3 | 3 | 2 |
| 3 | 3 | 2 | 1 | 3 |
| 3 | 4 | 3 | 3 | 2 |
| 4 | 3 | 3 | 2 | 4 |

b.
| 4 | 4 | 3 | 3 | 3 |
| 4 | 2 | 3 | 2 | 2 |
| 3 | 2 | 3 | 3 | 3 |
| 3 | 4 | 2 | 3 | 2 |
| 4 | 3 | 2 | 2 | 4 |

c.
| 4 | 3 | 3 |
| 3 | 3 | 3 |
| 4 | 3 | 4 |

d.
| 4 | 3 | 3 |
| 3 | 2 | 2 |
| 3 | 3 | 4 |

- 4. For the given 7*7 input matrix, what will be the output of max pooling with the filter of size 3*3 and stride of 2.

| 1 | 2 | 4 | 1 | 4 | 0 | 1 |
| 0 | 0 | 1 | 6 | 1 | 5 | 5 |
| 1 | 4 | 4 | 5 | 1 | 4 | 1 |
| 4 | 1 | 5 | 1 | 6 | 5 | 0 |
| 1 | 0 | 6 | 5 | 1 | 1 | 8 |
| 2 | 3 | 1 | 8 | 5 | 8 | 1 |
| 0 | 9 | 1 | 2 | 3 | 1 | 4 |

a.
| 4 | 6 | 5 |
| 6 | 6 | 8 |
| 9 | 8 | 8 |

b.
| 4 | 5 | 5 |
| 6 | 6 | 8 |
| 9 | 8 | 6 |

c.
| 4 | 5 | 6 |
| 3 | 6 | 8 |
| 9 | 9 | 8 |

d.
| 4 | 3 | 3 |
| 3 | 3 | 3 |
| 4 | 3 | 4 |

- 5. In CNN, max-pooling decreases the parameters.

  - a. False
  - b. True

- 6. What will be the value of “a” for the following?
Input:

| 1 | 1 | 1 | 0 | 0 |
|---|---|---|---|---|
| 0 | 1 | 1 | 1 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 1 | 0 | 0 |

Filter:

| 1 | 0 | 1 |
|---|---|---|
| 0 | 1 | 0 |
| 1 | 0 | 1 |

Output:

| ? | | |
|---|---|---|
| | | |
| | | |

  - a. 3
  - b. 4
  - c. 5
  - d. 6

## Answers

| 1 | d |
|---|---|
| 2 | a |
| 3 | c |
| 4 | a |
| 5 | a |
| 6 | b |

## Hands-on session [CNN]

The following CNN code has two versions: Shallow CNN and Deep CNN. Here, Shallow CNN refers to only a single hidden layer, and deep CNN means more than one hidden layer.

Download the ZIP file of any dataset you want to use.

```
# Extract the .zip file
from zipfile import ZipFile
file_name = 'Data.zip'
with ZipFile(file_name, 'r') as zip:
    zip.extractall()
    print("Done")
# Load Libraries
import numpy as np
import matplotlib.pyplot as plt
from keras.models import Sequential
from keras.layers import Dense , Conv2D, Flatten, MaxPooling2D
from keras.utils import np_utils
# Load Dataset from Images
#The dataset folder must contain separate folders for training and testing.
import os
import cv2
# load data from the path specified by the user
def data_loader(path_train, path_test):
    train_list=os.listdir(path_train)
    # Number of classes in the dataset
    num_classes=len(train_list)
    # Empty lists for loading training and testing data images as well as corresponding labels
    x_train=[]
    y_train=[]
    x_test=[]
    y_test=[]

    # Loading training data
    for label,elem in enumerate(train_list):
        path1=path_train+'/'+str(elem)
        images=os.listdir(path1)
        for elem2 in images:
            path2=path1+'/'+str(elem2)

            # Read the image from the directory
            img = cv2.imread(path2)

            # Append image to the train data list
            x_train.append(img)

            # Append class-label corresponding to the image
            y_train.append(label)

        # Loading testing data
        path1=path_test+'/'+str(elem)
        images=os.listdir(path1)
        for elem2 in images:
            path2=path1+'/'+str(elem2)

            # Read the image from the directory
            img = cv2.imread(path2)

            # Append image to the test data list
            x_test.append(img)

            # Append class-label corresponding to the image
            y_test.append(label)

    # Convert lists into numpy arrays
    x_train=np.asarray(x_train)
    y_train=np.asarray(y_train)
    x_test=np.asarray(x_test)
    y_test=np.asarray(y_test)
    return x_train,y_train,x_test,y_test

# path specified by the user
path_train = 'Data/train'
path_test = 'Data/test'
X_train,y_train,X_test,y_test = data_loader(path_train, path_test)
print("Loading Done")
X_train.shape
y_train.shape
X_test.shape
y_test.shape

# Formatting Data and Labels for Deep Learning
input_shape = (X_train.shape[1], X_train.shape[2], X_train.shape[3])

# forcing the precision of the pixel values to be 32 bit
X_train = X_train.astype('float32')
X_test = X_test.astype('float32')

# normalize inputs from 0-255 to 0-1
X_train = X_train / 255.
X_test = X_test / 255.

# one hot encode outputs using np_utils.to_categorical inbuilt function
y_train = np_utils.to_categorical(y_train)
y_test = np_utils.to_categorical(y_test)
num_classes = y_test.shape[1]

# Splitting data into training and validation
from sklearn.model_selection import train_test_split
#Splitting the training data into training and validation
```
