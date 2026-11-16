

![](img/1490b3cf638678afadc8c48abc1698d5_454_0.png)

**FIGURE 17.3:** Model training and tuning components

## Steps Involved During Model Building

Model building involves the following steps:

- 1. Choosing an appropriate algorithm, such as a decision tree, linear regression, or neural network based on the problem to be solved
- 2. Defining the features and the label that needs to be predicted
- 3. Choosing the loss function such as mean squared error
- 4. Building the model architecture if required

Model building is all about experimenting with different algorithms, features, and hyperparameters iteratively until a satisfactory performance is achieved. As part of this process, you may be required to carry out some data preprocessing, such as scaling, encoding, or feature engineering.

> **TIP** Model architecture refers to the algorithm or framework that is used to predict. It can refer to the layers, nodes, activation functions, loss functions, and optimization algorithms that are arranged and configured in a certain way. Some common machine learning model architectures are linear regression, decision trees, neural networks, convolution neural networks, and recurrent neural networks.

## Developing the Algorithm Code

As a machine learning engineer, you can write your algorithm code in different languages, such as Python, R, or Java, depending on your preferences or environment. Your code will need to do the following:

- Import the data
- Clean the data
- Split the data
- Train the model
- Make predictions

## Selecting the Right Algorithm

During this model building process, you will be experimenting with different algorithms and parameters to shortlist the right algorithm. You will be evaluating the models based on different parameters such as training/prediction time, accuracy, explainability, memory requirements, and so on.

For our case study, you may choose classification algorithms such as logistic regression, naïve Bayes, and support vector machines as possible candidates to build the model.

> NOTE Refer to Chapter 16 on algorithms to learn more about various algorithms and when to use which one.

## MODEL TRAINING

Once you have shortlisted a model during model building, the next step is to train your model with the training dataset. Model training is a crucial step in machine learning that results in a working model, which you can validate, test, and deploy. Using the cooking analogy, model training is like actually starting to cook the meal using the recipe you came up with during the model building process.

> NOTE A model is a set of rules or equations that the machine can use to learn from data to make predictions. Depending on the type of problem, these predictions could be about identifying if an email is spam or classifying images as different types of animals.

During this step, you will feed the training data into the model and begin the training process. The training process teaches the machine how to make its predictions. During this process, the weights (parameters) of the algorithm get updated to reduce the loss, which is the difference between the prediction and the actual labels. In other words, the training process helps to increase the accuracy with which the machine makes its predictions.

> TIP Keep a close eye on metrics such as accuracy, precision, and recall to check if the model is performing well or needs adjustment.

## Distributed Training

When dealing with a lot of data or a complex model, your training process can take a long time, sometimes even days or hours. It is where distributed training comes to our rescue. Distributed training involves using multiple machines to train your model.

You have two types of distributed training, namely, data parallelism and model parallelism.

### Model Parallelism

Model parallelism involves splitting the model into smaller parts to predict different features and assigning each part to different machines. The models are then combined to form the final model.

Model parallelism is more complex than data parallelism but is more suited for models that cannot fit into one device. You can also combine model parallelism with other techniques such as data parallelism to improve training efficiency.

### Data Parallelism

Data parallelism involves splitting the training dataset into mini batches evenly distributed across multiple nodes.

For example, if you have 1,000 emails to identify spam, you can divide them into 10 groups of 100 emails each and assign each group to a different computer. Therefore, each node trains on only a fraction of the dataset. You will update the model with the results from the other machines to make the final model.

> NOTE An optimization algorithm helps update the parameters of the model to reduce a loss function, such as mean squared error. A good example is the gradient descent algorithm, which adjusts the parameters iteratively in the direction of the steepest descent of the loss function.

## Problems Faced When Training Models

When training your models, you are going to face a number of problems, some of which are listed in Figure 17.4. We will review these challenges in this section.

![](img/1490b3cf638678afadc8c48abc1698d5_458_0.png)

**FIGURE 17.4:** Problems faced when training models

### Overfitting and Underfitting

Overfitting happens when you are training the model with a lot of training data. Your model starts to memorize the labels and is unable to generalize to new data. It happens when the model captures every noise or irrelevant pattern in the data. The model becomes too complex and is unable to predict against new data. It can lead to errors and inaccuracies in your model predictions on validation or test data.

Underfitting is the reverse of overfitting. In this case, the model is too simple and does not capture important patterns or relationships that are relevant for the prediction.

### System Bottlenecks

When your system faces a bottleneck, it can bring down the entire process performance regarding memory, CPU disk space, or network bandwidth.

### Saturated Activation Functions

Saturated activation functions mean the output does not change even if the input changes, which means the neural network cannot learn anymore. It happens when the activation functions, namely, sigmoid and tanh, have reached their minimum or maximum levels. When this happens, we say the activation functions are saturated. ReLU is an alternative in such situations.

### Vanishing Gradients

Vanishing gradients happen when the gradients or the incremental changes to the neural network weights are minimal or close to 0 during backpropagation. When this happens, the neural network will not learn much from the data. It can happen when using sigmoid or tanh, as well as when the gradients are not propagated back through the network.

> TIP Think of **saturated activation functions** as rusty gears in a machine. If they are not moving, neither is your model's learning. Similarly, vanishing gradients are like whispers in a noisy room and your model is not hearing them. Opt for ReLU for activation functions and proper weight initialization to address these issues.

To resolve this situation, you can either use ReLU or use weight initialization schemes to prevent the gradients from becoming too small.

You can use a debugger tool to keep track of the network’s inputs, outputs, gradients, weights, metrics, logs, errors, and so on. The tool can also capture the state of a machine learning job at periodic intervals, such as various epochs, batches, steps, or layers.

Some examples of a debugger are the PyTorch debugger, TensorFlow debugger, SageMaker Debugger, and Azure Machine Learning debugger. ML debuggers help you to debug and profile the performance at various intervals using breakpoints, alerts, watches, visualizations, and filters.

## Training Code Container

A training code container comes in handy when you want to include the training code and all the environmental dependencies into one package to take care of code dependencies.

**TIP** _Building training code containers is an essential step in the machine learning process to build and deploy models quickly and reliably at scale._

Suppose you're trying to build a model to predict customer churn. You have collected all your data and used the logistic regression model to predict customer churn. And now, you have written some Python code in your local machine to train the model. You have integrated your code with other frameworks and libraries such as scikit-learn and pandas.

Now, you are all set to deploy your working code into production using the cloud. Unfortunately, this is where you are going to face some issues, such as the following:

- Your code may not run due to differences in the hardware, software, and operating system configuration.
- Your code may not be able to access the data that is stored in the cloud platform.
- You may need to scale up or down your compute and storage resources depending upon the workload.

Here comes your training container to your rescue. You will start by creating a container image with the training code and the entire dependent stack, such as the libraries, framework, tools, and environment variables for your model to run. You can then train the model quickly and deploy it on another platform at scale because now your code is running as part of a self-contained unit with all the dependencies taken care of.

### Creating a Training Code Container

To create a training code container, you need the following:

