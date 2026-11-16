![](bbox=[0.106, 0.071, 0.821, 0.432])

FIGURE 6.11: Feature x follows a Gaussian distribution with an outlier at x=8.

Outliers can be interesting data points (e.g. criticisms). When an outlier influences the model it is also an influential instance.

# Influential instance

An influential instance is a data instance whose removal has a strong effect on the trained model. The more the model parameters or predictions change when the model is retrained with a particular instance removed from the training data, the more influential that instance is. Whether an instance is influential for a trained model also depends on its value for the target y. The following figure shows an influential instance for a linear regression model.