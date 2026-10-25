# 6.1 Tutorial Overview

This tutorial is divided into six parts; they are:

+   1. Select a One-Dimensional Function
+   2. Define a Discriminator Model
+   3. Define a Generator Model
+   4. Training the Generator Model
+   5. Evaluating the Performance of the GAN
+   6. Complete Example of Training the GAN

# 6.2 Select a One-Dimensional Function

The first step is to select a one-dimensional function to model. Something of the form:

$y = f(x)$ (6.1)

Where $x$ are input values and $y$ are the output values of the function. Specifically, we want a function that we can easily understand and plot. This will help in both setting an expectation of what the model should be generating and in using a visual inspection of generated examples to get an idea of their quality. We will use a simple function of $x^2$; that is, the function will return the square of the input. You might remember this function from high school algebra as the u-shaped function. We can define the function in Python as follows:

```
# simple function
def calculate(x):
    return x * x
```

Listing 6.1: Example of defining a target function.

We can define the input domain as real values between -0.5 and 0.5 and calculate the output value for each input value in this linear range, then plot the results to get an idea of how inputs relate to outputs. The complete example is listed below.

```
# demonstrate simple x^2 function
from matplotlib import pyplot

# simple function
def calculate(x):
    return x * x

# define inputs
inputs = [-0.5, -0.4, -0.3, -0.2, -0.1, 0, 0.1, 0.2, 0.3, 0.4, 0.5]
# calculate outputs
outputs = [calculate(x) for x in inputs]
# plot the result
pyplot.plot(inputs, outputs)
pyplot.show()
```

Listing 6.2: Example of plotting the domain for the target function.