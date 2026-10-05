# 3.4 Training system

A Neural Network is a network or circuit of neurons, using the neural network, we can compare the HSV value of input image with the pre-trained datasets and the desired result is predicted. In this training section, the training model gets in the segmentation performance. The soil pH and the soil nutrient are based on the standards by Soil health lab, Udupi and these values collected from the lab serves as a database for the system. Convolutional Neural Network is used to improve the accuracy of the result. For soil micronutrient and soil pH level, the dataset contains about 4000 soil samples image. From the image data, 80% of the images were used for training; 20% for testing. The CNN model consists of various layers as Convolutional layer, ReLu layer, Pooling layer, Fully connected layer.

+   a) Convolutional layer. The first step is Convolution layer, the relation between the pixels is preserved by the image features using small squares of the input data. It is mathematical operation, that takes image matrix and filter as an input. convolution of images with various filters will perform operation like blur, edge detection and sharper by applying filters. The convolution layer is called using annConvLayer.
ReLu layer-Linear activation as the non-linear operation. The basic need of it is to introduce non-linearity to convert. ReLu provides better performance compared to other non linear functions such as tanh or sigmoid.

+   c) Pooling layer. In the Pooling layer when images are large the number of parameters is reduced. subsampling and downsampling are also called as spatial pooling, which decreases the dimensionality of every single map but only the required information. Pooling works better and takes largest element from rectified feature map.

+   d) Fully-Connected Layer. The final is the Fully-Connected Layer also called as dense FC layer. This layer extracts only the important information from the image, with the help of input layer, all the features are combined to create a model. Here, there is one hidden layer and one output layers.

To train the model with training dataset, we use the function: train(cnn,train_x,train_y,no_of_epochs,batch_size);
where, train_x is training data, train_y is corresponding images, batch_size should be in integer multiple of total no.of training data and, no_of_epochs should be > 1 for better accuracy it takes lot of time to train.

To test the model, we use the function:
test(cnn,test_x,test_y);
where, test_x is test data, test_y is corresponding values. The process of training is repeated, the training number is reached.

![](bbox=[0.293, 0.663, 0.703, 0.775])

Figure 3. Convolution neural network architecture.

+   e) Accuracy.
Using the function, model's accuracy is calculated. The machine learning algorithm uses to improve the accuracy. The performance of Convolutional Neural Network is determined using an accuracy metric in a interpretable way. The model's accuracy is determined after the parameters are calculated in the format of percentage. It measures how well our model predicts by true values with model prediction i.e.. Predicted result with the Test

32