# 8.1.3 How Neuron works in ANN : Terminologies

+   - Input-layers: In the input layer, inputs are in fact independent variables. These independent variables are all for one observation. So that if it is each one row in your database (think your observation points as (a, b, c, d, ...) a multi-dimensional vectors.

+   - Eg: independent variables may have deposits, in the bank, drive/walk, salary etc. But that's all descriptors of one specific person (one single observation) that can be either in your training model or prediction.

![](bbox=[0.265, 0.145, 0.735, 0.415])

+   - Standardize/Normalize the variables: You need to standardize these variables so you have a mean of zero and a variance one.

+   - Or you can also sometimes normalize instead of standardize them. Meaning that instead of making a mean of zero and a variance one, you subtract the minimum value from each element of a column and then divide by the [maximum - minimum] by the range of values and therefore you get values between 0 and 1.

+   - And it depends on this scenario you might want to standardize or normalize.

Basically you all of these variables to be quite similar because these values are going to go into a neural network and is going to be easier for the neural network to process them if they're all about the same.

If you want to read more about standardization/normalization and other things read following paper: Yann LeCun is a leading Deep Learning expert works at Meta/facebook as Chief Scientist. And is close friend to Geoffrey Hinton. In this paper you'll learn more about centralization and normalization.

# Additional Reading:

# Efficient BackProp

By Yann LeCun et al. (1998)

Link:

http://yann.lecun.com/exdb/publis/pdf/lecun-98b.pdf

![](bbox=[0.525, 0.695, 0.875, 0.895])