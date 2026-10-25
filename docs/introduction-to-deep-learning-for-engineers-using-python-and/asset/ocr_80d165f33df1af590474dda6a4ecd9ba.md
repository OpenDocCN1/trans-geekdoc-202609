# Case Study: Practical Implementation Through Transfer Learning

# 7.1 PROBLEM STATEMENT

In this chapter, to demonstrate the use of deep learning, we have used a transfer learning process for a multiclass image classification problem. Our goal is to implement a deep learning model to determine the Make, Model, and Year of a car. In order to train and test our model, we have used an organized car dataset containing a total of 16,185 different car images. This dataset (Stanford's Cars Dataset) was used in a Kaggel's competition and can be downloaded from [62]. An earlier version of the dataset was also used in research for 3D object representation of fine-grained categorization of rigid classes [63].

In the Stanford's Cars Dataset, among 16,185 car images, 196 different classes (Make, Model, and Year) of cars are divided into training images (8,144) and testing images (8,041). Inside the car_devkit zip file, data classes, and corresponding bounding boxes to crop the images are available. From their website, the cars_test_annos_withlabels.mat file was used to find out our test data set accuracy. Note that there is a similar file (cars_test_annos.mat) available on their site that doesn't have the classes defined in it. So, we recommend everyone to check Stanford Cars Data set carefully before working on this project.

To identify car make and model from an image, we need to train a deep learning model using the training data and then test the performance of the model by using the testing data. A pre-trained deep neural network, known as Efficient B7, is used for this task to extract features from the training dataset.

A schematic of the transfer learning process using the pre-trained network is shown in Fig. 7.1. Finally, for testing purposes, we are going to feed several random car pictures (downloaded from the internet) to see how well the new deep learning model performs outside of the given dataset.

# 7.2 DATA PROCESSING

The data processing step is very critical for using any deep learning model effectively. We have to carefully check the labels and names for the images and the consistency between training