
- **A Docker file:** This file contains the instructions to build the image.
- **train.py:** This file contains the training code for the machine learning model.
- **requirements.txt:** This file contains the dependencies such as scikit-learn and pandas for the machine learning model to run.

You can then use the Docker file to build the container image and push it to a container registry such as the Docker Hub or the Google Container Registry.

## Using the Training Code Container

The container image can be pulled to train the model onto any machine that has docker installed. You need to specify the data sources, compute resource requirements, and set other parameters for the training job. You can save the file once the training is completed and you have chosen the right hyperparameters.

Using that file for real-time predictions, you can then deploy the model on any other machine.

## Model Artifacts

You need to realize that the final model is one of many outputs you will get when training a model. There will also be other model artifacts, such as the trained parameters, model definition, and metadata. These model artifacts are essential pieces of the puzzle to understand, use, reproduce, and improve upon your model. [Figure 17.5](https://www.example.com) shows the artifacts.

![](img/1490b3cf638678afadc8c48abc1698d5_462_0.png)

### FIGURE 17.5: Model artifacts outputted during model training

## Trained Parameters

In the case of predicting the price of a house, you had trained parameters such as the weights and biases that your model learned during the model training process. These parameters define the relationship between the features and the price of the house. They basically determine how the model works.

## Model Definition

Model definition defines the architecture or structure of the model. It defines how the data flows into the model, the layers, the nodes, and how they interact. In the case of the house pricing prediction model, this could define the structure of the neural network in all the regression models. It would detail how the inputs (house features) are processed to produce the output (predicted price).

## Other Metadata

This could be any information that you may have used during the model training process, such as the preprocessing steps that you used to prepare the data, the versions of the libraries, the hyperparameters to tune the model, and the validation metrics that you used to evaluate the model, and so on.

> **TIP** It is vital to keep track of the model artifacts as they will help in reproducibility, governance, explainability, troubleshooting, lineage tracking, and centralized artifacts management.

## MODEL TUNING

Model tuning involves fine-tuning the parameters not optimized during the training process. Model tuning helps to modify the structure of the model itself. During model training, the internal trainable parameters, such as weights and biases of the neural networks, are trained using the training data.

In the case of model tuning, the focus is on tuning hyperparameters. Those hyperparameters are structural settings that are set before fitting the model and are not learnable from the training data. These are parameters such as the learning rate, number of epochs, regularization strength, and so on.

> **TIP** Think of model tuning as sharpening your pencil. While training sets the foundation, tuning is where you achieve perfection.

## Hyperparameters

Suppose you are a chef trying to create a recipe to bake bread. While creating your bread, you can change a few parameters, such as the temperature and the baking time. You can think of these parameters as hyperparameters.

Hyperparameters control how the model works and help optimize the model performance on training and validation datasets. It helps to avoid overfitting or underfitting. These values cannot be estimated from data and are often configured by a practitioner.

Hyperparameters help to control the behavior of the algorithm or the model and control how fast the training occurs and how complex the model is. Hyperparameters are set before the model gets trained, and they guide how the model learns its trainable parameters.

I next discuss the learning rate, regularization, batch size, number of epochs, hidden layers, and hidden unit hyperparameters, as shown in Figure 17.6.

## Learning Rate

Learning rate is the rate at which the model parameters are updated at each iteration of the gradient descent.

You can think of the learning rate as the baking temperature. A high temperature can speed up the baking, but it can get spoiled by overheating. Similarly, a high learning rate speeds up the convergence to minimize the loss function. However, it can also cause instability or overshooting. A low learning rate can ensure stability but can take a long time to converge and potentially get stuck in local minima.

![](img/1490b3cf638678afadc8c48abc1698d5_465_0.png)

### FIGURE 17.6: Tuning hyperparameters for optimal model performance

## Regularization

Regularization is adding a penalty to the loss to reduce the complexity or magnitude of the parameters. While this approach may reduce the variance and help avoid overfitting, it can introduce bias. Using the cooking analogy, compare the situation of overfitting to having added more salt. To reduce this saltiness, you would add more water. You can think of regularization in a similar manner.

## Batch Size

Batch size is the number of data points in each dataset used to train the model for each iteration of the gradient descent.

A large data size can reduce the variance in the parameter updates and noise, but it takes a long time to compute and uses a lot of memory. Smaller batch size is the reverse effect: it reduces the time taken to compute and uses less memory. However, it increases the noise and variance in the parameter updates.

## Number of Epochs

The number of epochs stands for the number of times the entire training dataset is fed to the model for training. A higher number means the model runs the risk of overfitting, while a lower number may lead to underfitting of the model.

To find the sweet spot for the number of epochs, you can resort to techniques such as early stopping in the case of overfitting and adopt techniques such as cross-validation to get better results.

## Hidden Layers

Hidden layers are the layers that are not visible to the user in a neural network.

> NOTE The hidden layer is an important parameter that can decide the complexity of the model.

Simple layers can catch broad features, and deeper layers can catch more intricate, specific details. A higher number of hidden layers can result in overfitting, while a lower number can lead to underfitting. To identify the right number of hidden layers, you can try grid search or random search techniques to evaluate the performance using different numbers of hidden layers.

## Hidden Units

Hidden units are the number of neurons in a layer in a neural network. They determine the representational capacity of the neural network. A higher value can lead to overfitting, and a lower value can lead to underfitting. You can identify the correct optimal number of hidden units using techniques such as a grid or random search to evaluate the network's performance using different numbers of hidden units.

## Choosing the Right Hyperparameter Optimization Technique

You can employ manual or automated model-tuning techniques such as grid search, random search, or Bayesian optimization (see Figure 17.7).

- Tries all hyperparameter combinations
- Finds global optimum but slower

![](img/1490b3cf638678afadc8c48abc1698d5_467_0.png)

- Samples random combinations
- Faster but may miss optimal setting

### FIGURE 17.7: Grid versus random searches

You can use your intuition or experience when choosing the hyperparameters to manually tune a model. Your goal is to choose the model with the best validation performance. While using an automated approach, the grid search provides the best possible model. In contrast, the random search approach is more efficient.

> **TIP** If you're running on, you will choose the random search approach, but if you're looking for accuracy, you will choose the grid search approach.

### Grid Search vs. Random Search

Say you're trying to predict whether a patient has cancer, and you're using a random forest model that contains two hyperparameters, namely, the depth of the tree and the number of trees in the model. See Figure 17.7.

To use grid search to tune the hyperparameters, you can set the maximum depth of the decision tree to 10, 20, 30, 40, and 50. You can set the number of trees in the random forest to 100, 200, 300, 400, and 500.

When you use grid search, the system will try all 25 combinations of the hyperparameter values, which will take a long time but will
