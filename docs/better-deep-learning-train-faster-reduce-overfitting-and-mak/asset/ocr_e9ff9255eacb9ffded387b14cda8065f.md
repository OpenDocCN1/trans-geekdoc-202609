![](bbox=[0.17, 0.14, 0.81, 0.48])

Figure 11.3: Loss and Accuracy Learning Curves on the Train and Test Sets for an MLP on Problem 2.

Now that we have a baseline of performance and learning dynamics for an MLP on Problem 2, we can see how the addition of transfer learning affects the MLP on this problem.

# 11.2.4 MLP With Transfer Learning for Problem 2

The model that was fit on Problem 1 can be loaded and the weights can be used as the initial weights for a model fit on Problem 2. This is a type of transfer learning where learning on a different but related problem is used as a type of weight initialization scheme. This requires that the fit_model() function be updated to load the model and refit it on examples for Problem 2. The model saved in model.h5 can be loaded using the load_model() Keras function.

```
# load model
model = load_model('model.h5')
```

Listing 11.21: Example loading a saved model.

Once loaded, the model can be compiled and fit as per normal. The updated fit_model() with this change is listed below.

```
# load and re-fit model on a training dataset
def fit_model(trainX, trainy, testX, testy):
    # load model
```