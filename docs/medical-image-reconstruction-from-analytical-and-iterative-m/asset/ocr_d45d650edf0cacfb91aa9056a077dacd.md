![](bbox=[0.16, 0.1, 0.91, 0.39])

Fig. 9.1: A belief about the three categories of image reconstruction algorithms.

# 9.2 Basic principles of machine learning

The basic principle of machine learning is illustrated in Figure 9.2, where the black box is a general mapping, which transforms an input numerical string to an output numerical string. Here, a numerical string is a general term for a picture, a time series, a paragraph of text, and so on. Regardless the types of the input, they are first converted into numbers before fed into the black box. The output numerical string is sometimes referred to as the prediction. Therefore, the purpose of the black box is to make a prediction for a given input. This black box is fairly magical.

![](bbox=[0.175, 0.655, 0.725, 0.72])

Fig. 9.2: A magical black box can transform an input numerical string to a desired output numerical string. This black box is a neural network.

Machine learning has two major types: classification and regression. Fundamentally, classification is about predicting a discrete value and regression is about predicting a continuous value. For a classification application, the label is always represented by a number, most commonly an integer. One example of a classifier is to have a black box to predict whether the input picture contains a dog or a cat. We can use 1 to label a dog and 2 to label a cat. As another important application, thanks to this black box, the