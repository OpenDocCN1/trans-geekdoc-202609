# LogisticRegression(multi_class="multinomial")

There is no need to set the parameter since scikit-learn will automatically detect when we have more than two labels. We will now demonstrate how we fit and plot the logistic regression model to obtain results presented in Fig. 4.5. We can select and fit the model using a standard scikit-learn API

```
model = LogisticRegression()
model.fit(X,y)
```

To plot the classification results, we will predict the labels for the whole 2D feature space. First, we sample the relevant ranges of values for both features

```
import numpy as np
x1 = np.linspace(-2.5, 2, 1000)
x2 = np.linspace(-3.3, 3.5, 1000)
```

Next, we combine the individual feature vectors into matrices of 2D coordinates, with sizes 1000 × 1000, suitable for plotting

```
x1, x2 = np.meshgrid(x1,x2.T)
```

However, scikit-learn requires a matrix in shape number of samples × number of features, which is 1,000 × 2 in our case. We will achieve this by flattening x1 and x2 into 1D vectors and concatenating to form a feature matrix

```
Feature_space = np.c_[x1.ravel(),x2.ravel()]
```

Now, we are to predict the labels for the sampled 2D feature space

```
y_pred = model.predict(Feature_space)
```

Before we can plot these, we need to reshape them back to a 2D grid

```
y_pred = y_pred.reshape(x1.shape)
```

We will plot the result using a matplotlib function contour that takes the coordinates and the intensity (color) to be plotted as input arguments

```
import matplotlib.pyplot as plt
plt.contour(x1, x2, y_pred, cmap='summer')
```

The parameter cmap determines the colormap for the Final. Finally, we plot the data on and annotate the plot

```
plt.plot(X[y==0,0],X[y==0,1],'bo')
plt.plot(X[y==1,0],X[y==1,1],'rd')
plt.plot(X[y==2,0],X[y==2,1],'g^')
plt.xlabel('Ejection Fraction')
```