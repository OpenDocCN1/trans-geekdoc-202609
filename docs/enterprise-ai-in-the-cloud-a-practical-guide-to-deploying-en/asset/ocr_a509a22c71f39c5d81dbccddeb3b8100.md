> **TIP** It is vital to keep track of the model artifacts as they will help in reproducibility, governance, explainability, troubleshooting, lineage tracking, and centralized artifacts management.

# MODEL TUNING

Model tuning involves fine-tuning the parameters not optimized during the training process. Model tuning helps to modify the structure of the model itself. During model training, the internal trainable parameters, such as weights and biases of the neural networks, are trained using the training data.

In the case of model tuning, the focus is on tuning hyperparameters. Those hyperparameters are structural settings that are set before fitting the model and are not learnable from the training data. These are parameters such as the learning rate, number of epochs, regularization strength, and so on.

> **TIP** Think of model tuning as sharpening your pencil. While training sets the foundation, tuning is where you achieve perfection.

# Hyperparameters

Suppose you are a chef trying to create a recipe to bake bread. While creating your bread, you can change a few parameters, such as the temperature and the baking time. You can think of these parameters as hyperparameters.

Hyperparameters control how the model works and help optimize the model performance on training and validation datasets. It helps to avoid overfitting or underfitting. These values cannot be estimated from data and are often configured by a practitioner.

Hyperparameters help to control the behavior of the algorithm or the model and control how fast the training occurs and how complex the