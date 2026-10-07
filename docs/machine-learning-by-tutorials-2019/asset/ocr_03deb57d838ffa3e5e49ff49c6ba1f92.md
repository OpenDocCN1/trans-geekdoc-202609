# Machine Learning

# Chapter 7: Going Convolutional

A donut may actually be matched by a combination of different patterns, perhaps a "round shape" pattern and a "has a hole in it" pattern.

For any image, many of the 256 channels in this tensor will light up to a certain extent, and it is really hard to interpret what this means. You need to do a bit more work to convert this tensor into something meaningful, such as a logistic regression that maps these patterns to the classes you are interested in.

# Honey, I shrunk the tensors!

It's possible Flatten the 28x28x256 tensor and train a logistic regression on top of it. That would turn the tensor into a 200,704-element vector. Recall from the last chapter that the logistic regression already had a hard enough time with just 3,072 features, left alone two hundred thousand...

Fortunately, for a classification model, you don't really care so much exactly the pattern was matched, whether it was matched at all. So you can use a trick, which will actually make life a little easier for the logistic regression. That trick is called global pooling or adaptive pooling.

The GlobalAveragePooling2D layer calculates the average value of each 28x28 feature map, which is just a scalar number. It puts these numbers into a vector of 256 elements, for each channel in the tensor. Then the logistic regression will use this vector as the feature vector. 256 features are much more palatable than 200,704!

Global average pooling is a pooling layer just like the max-pooling you've seen before, except now the window is the size of the image, i.e., 28x28 pixels, and it takes the mean value of all these pixels instead of the maximum. In each channel, we take the average of the 28x28 pixels and reduce it to a single number:

![](bbox=[0.188, 0.673, 0.812, 0.833])

Global average pooling