```
o = net(input_image)
print(o.shape)
>>> torch.Size([1, 10])
```

We can see that the network returned 10 outputs as expected.
The convolutional neural networks are trained the same way as fully connected networks presented in Chap. 10. For example, to classify digits with this network, we could optimize a cross entropy loss using a stochastic gradient descent optimizer.

# 11.2.8 Exercises

+   1. Implement a convolutional layer as follows²:
  a. Create a random image with spatial dimensions 100 × 100 and 3 channels;
  b. Implement a convolutional layer that outputs 5 channels and has a kernel size of 3 × 3. Pass the image through. Print out the dimensions of the results;
  c. Change the convolutional layer so that its output has spatial dimensions 100;
  d. Change the stride of the convolutional layer, so that the output has spatial dimensions 20 × 20;
  e. Instead of changing the stride, implement a max-pooling operation to reduce the dimension of the convolutional layer with stride 1 to 20 × 20.
2. Calculate the number of learnable parameters of the convolutional layer in Exercise 1.
3. Modify the CNN by changing each of the following:
  a. the name of the model to CNNNode2;
  b. the number of output channels of the first and second convolutional layer to 4 and 6 respectively;
  c. the number of outputs of the first and second fully connected layer to 32 and 2, respectively
Create an instance net2 of the new model. Perform forward pass with input_image.
Check that you have 2 outputs.

# 11.3. Predicting prematurity from neonatal brain MRI

In this section we will design and train a CNN classifier to predict prematurity status directly from neonatal MR images [13,18]. We will use 2D slices rather than 3D images to reduce the need for GPU memory and speed up training. The 2D brain MR images and the prematurity status of 157 babies are given in the file

> ²Skeleton code and solutions for exercises 1 and 3 are available from github.com/MachineLearning-BiomedicalApplications/notebooks.