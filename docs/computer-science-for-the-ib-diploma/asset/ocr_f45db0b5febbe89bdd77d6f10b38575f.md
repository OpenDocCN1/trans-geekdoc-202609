# Top tip!

# Regression with non-linear data?

If you have a data set you would like to fit to a non-linear function, the scipy curve_fit() function is what you are looking for.

For example, assuming you have NumPy arrays of x_data and y_data that you wish to fit to a quadratic function:

```
import numpy as np
from scipy.optimize import curve_fit
x_data = [......your data here......]
y_data = [......your data here......]
def my_quadratic(x, a, b, c):
    return a * x**2 + b * x + c
params, params_covariance = curve_fit(my_quadratic,
                                      x_data, y_data)
a, b, c = params # Extract the fitted coefficients
```

For more information, search online for scipy.optimize.curve_fit (https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html).

# A4.3.2 Supervised learning: classification techniques

> Classification techniques: where a machine learning model has been trained to identify, from a predefined list of categories, which category (or class) the input data would most likely be associated with.

One task frequently required of machine learning algorithms is to classify data as belonging to one of a given range of categories. Whereas the output prediction from linear regression is numeric, classification algorithms generally produce a non-numeric value to represent a category.

Categorization through machine learning is useful as it facilitates automation of decision-making processes and can be applied to a wide range of practical problems. Examples of everyday classification problems include:

+   - email spam detection (spam or not spam)
+   - medical diagnosis (disease or no disease)
+   - credit score (good credit risk or poor credit risk)
+   - image recognition (identifying what category of object is in the image)
+   - natural language processing / sentiment analysis (positive or negative sentiment)
+   - recommendation engine (what genre of movie to suggest next).

Two popular methods that do not require neural networks are k-nearest neighbours and decision trees.