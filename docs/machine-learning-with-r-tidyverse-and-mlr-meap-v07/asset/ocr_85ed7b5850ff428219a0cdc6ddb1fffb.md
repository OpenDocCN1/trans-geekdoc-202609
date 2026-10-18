# Modeling spectral data

The dataset we're working with is an example of spectral data. Spectral data contains observations made across a range of (usually) wavelengths. For example, we might measure how much a substance absorbs light from a range of different colors.

Statisticians and data scientists call this kind of data functional data, where there are many dimensions in the dataset (the wavelengths we measure across) and there is a particular order to those dimensions (starting by measuring the absorbance at the lowest wavelength and working our way to the highest wavelength).

A branch of statistics called functional data analysis is dedicated to modeling data like this. In functional data analysis, each predictor variable is turned into a function (for example, a function that describes how absorption changes over ultraviolet and near-infrared wavelengths). That function is then used in the model as a predictor, to predict the outcome variable. We won't apply this kind of technique to this data, but if you're interested in functional data analysis, check out Functional Data Analysis by James Ramsay (Springer, 2005).

As the pre-defined fuelsubset.task defines the ultraviolet and near-infrared spectra as functional variables, we're going to define our own task, treating each wavelength as a separate predictor. We do this as usual, using the makeRegrTask() function, setting the heatan variable as our target. I then define our k-NN learner using the makeLearner() function.

# NOTE

Notice that for regression, the name of the learner is "regr.kknn" with two ks, rather than the "classif.kknn" we used in chapter 3. This is because this function is taken from the kknn package, which allows us to perform kernel k-nearest neighbors, where we use a kernel function (just like with SVMs in chapter 6) to find a linear decision boundary between classes..

# Listing 12.4 Defining the task and k-NN learner

```
fuelTask <- makeRegrTask(data = fuelTib, target = "heatan")
kknn <- makeLearner("regr.kknn")
```