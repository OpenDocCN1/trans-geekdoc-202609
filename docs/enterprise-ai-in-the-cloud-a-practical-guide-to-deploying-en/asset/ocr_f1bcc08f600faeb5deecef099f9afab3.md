taken to compute and uses less memory. However, it increases the
noise and variance in the parameter updates.

# Number of Epochs

The number of epochs stands for the number of times the entire
training dataset is fed to the model for training. A higher number
means the model runs the risk of overfitting, while a lower number
may lead to underfitting of the model.

To find the sweet spot for the number of epochs, you can resort to
techniques such as early stopping in the case of overfitting and adopt
techniques such as cross-validation to get better results.

# Hidden Layers

Hidden layers are the layers that are not visible to the user in a
neural network.

> NOTE The hidden layer is an important parameter that can
> decide the complexity of the model.

Simple layers can catch broad features, and deeper layers can catch
more intricate, specific details. A higher number of hidden layers can
result in overfitting, while a lower number can lead to underfitting.
To identify the right number of hidden layers, you can try grid search
or random search techniques to evaluate the performance using
different numbers of hidden layers.

# Hidden Units

Hidden units are the number of neurons in a layer in a neural
network. They determine the representational capacity of the neural
network. A higher value can lead to overfitting, and a lower value can
lead to underfitting. You can identify the correct optimal number of
hidden units using techniques such as a grid or random search to
evaluate the network's performance using different numbers of
hidden units.