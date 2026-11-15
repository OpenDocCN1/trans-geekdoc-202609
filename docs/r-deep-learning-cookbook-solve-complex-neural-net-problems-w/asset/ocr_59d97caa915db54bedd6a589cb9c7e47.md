# Getting ready

Generative models in machine learning domains are referred to as models that have an ability to generate observable data values. For example, training a generative model on an images repository to generate new images like it. All generative models aim to compute the joint distribution over given datasets, either implicitly or explicitly:

+   1. Install and set up TensorFlow.
+   2. Load required packages:
+   
+   library(tensorflow)

# How to do it...

The section will provide steps to set-up an RNN model.

+   1. Load the MNIST dataset:
+   
+   # Load mnist dataset from tensorflow library
+   datasets <- tf$contrib$learn$datasets
+   mnist <- datasets$mnist$read_data_sets("MNIST-data", one_hot = TRUE)

+   2. Reset the graph and start an interactive session:
+   
+   # Reset the graph and set-up a interactive session
+   tf$reset_default_graph()
+   sess<-tf$InteractiveSession()

+   3. Reduce image size to 16 x 16 pixels using the reduceImage function from Chapter 4, Data Representation using Autoencoders:
+   
+   # Covert train data to 16 x 16 pixel image
+   trainData<-t(apply(mnist$train$images, 1, FUN=reduceImage))
+   validData<-t(apply(mnist$test$images, 1, FUN=reduceImage))

+   4. Extract labels for the defined train and valid datasets:
+   
+   labels <- mnist$train$labels
+   labels_valid <- mnist$test$labels