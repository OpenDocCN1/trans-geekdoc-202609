Sometimes, their main concern is the speed of the algorithms. For example, it is more likely for them to choose a less persuasive algorithm that can quickly provide results. This gives them an idea of which algorithms they should try next.

# Which Parameters Should We Select to Tune?

There are three categories of data that are handled by your application during model training:

+   1. Input data, or training data, is a collection of individual instances that are important to solve your machine learning problem. This data is responsible for accurately making predictions during the training process to configure the model about new instances of similar data. However, these values can never be a part of your model.

+   2. Model parameters are the variables that are used to adjust to your data by the machine learning technique chosen by you. For example, a deep neural network (DNN) is considered as a model parameter. It is composed of neurons which are also called processing nodes; operations are performed in each data as it travels through the network. Each node has a weight value after your DNN is trained. This shows how much impact it has on the final prediction. These weights are examples of your model's parameters.

+   3. Hyperparameters are the variables whose values must be defined outside the training process. They oversee the training process itself. For example, to set up a deep neural network, you have to first decide the number of hidden layers you want to use between the input layer and the output layer and the number of nodes used by each layer. Hyperparameters are configuration variables that are not directly related to the training data. Unlike other parameters, which change during a training job, hyperparameters remain ordinarily constant during a job.

The process of choosing the right hyperparameters is known as hyperparameter optimization. Selecting the right hyperparameters is a crucial step because they directly control the training algorithm's behavior and have a massive impact on the model's performance,