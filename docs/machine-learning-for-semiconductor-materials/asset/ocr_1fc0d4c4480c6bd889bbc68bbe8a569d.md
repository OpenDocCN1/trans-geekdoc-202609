+   - **Batch Size:** Batch size decides how many samples are looked at in each training round. Bigger batches help reach the goal faster, but they need more memory and computing power. Methods like batch normalization and gradient accumulation can help keep training steady when using large batches.

+   - **Regularization Parameters:** Regularization tricks like L1 and L2 regularization or dropout stop overfitting. They do this by keeping parameter values in check or turning off units during training. The strength of regularization depends on hyperparameters. These need to be adjusted to make the model work its best.

+   - **Hyperparameter Search:** This involves looking into different hyperparameter combinations to make the model work better. You can use methods like grid search, random search, and Bayesian optimization to check out various hyperparameter options and find the best ones.

# 3. Optimization Algorithms

+   - **Stochastic Gradient Descent:** Stochastic gradient descent (SGD) is a way to train machine learning models in deep neural networks. It is different from regular gradient descent methods. SGD tweaks the model's settings for individual data points or small groups rather than looking at all the data at once. This approach makes calculations faster and helps the model learn quicker. SGD works well with big datasets where it's not possible to process everything in one go.

+   - **Adam:** Adam is a learning rate optimization algorithm that is open to input. It uses momentum and RMSprop. It changes the training speed for each parameter based on the first and second moments of the gradients. This leads to quicker convergence and better standardization.

+   - **RMSprop:** RMSprop is another algorithm that adapts the learning rate. It uses a moving average of squared gradients to work out the training rate for each parameter in the algorithm. It solves the problem of gradients that vanish or burst by changing learning rates on the fly based on the most recent gradient history.

+   - **Loss Function:** The loss function you use depends on what you are trying to do with your semiconductor inspection. If you are sorting things into many groups, cross-entropy for multiple categories is a go-to choice. For yes-or-no decisions, binary cross-entropy works well. When you need to predict numbers, mean squared error can do the job.

By looking at how to split data, adjust settings, and pick the right math tricks, companies can build and improve CNN models that work well for checking semiconductors. This helps them spot defects and keep quality high when making these tiny electronic parts.

# 5.11 MODEL TESTING

+   1. **Accuracy:** Accuracy is a basic statistic that shows the percentage of grouped items in a dataset. It gives a full look at how right the model is by showing how many predictions match the real labels. For checking semiconductors, accuracy is a key sign of how well the model spots flaws or odd things in