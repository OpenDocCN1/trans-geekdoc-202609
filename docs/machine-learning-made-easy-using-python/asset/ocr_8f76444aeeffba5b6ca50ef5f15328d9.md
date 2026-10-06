# # Saving and loading models

So we have created our model, tested it and even improved it. Let's say we want to use the model somewhere else or share it, how to do that? Well, we can do so using the **joblib** module. So let's save our **KNN** weight predicting model using joblib

```
In [6]: import joblib

joblib.dump(KNN, "WeightPred.sav")

Out[6]: ['WeightPred.sav']
```

We used the `dump()` function and passed the KNN regressor and the "WeightPred.sav" filename as arguments. Make sure to use the `.sav` extension after the model name. As we haven't specified any specific location it is stored in the place where jupyter notebook is hosted

+   - sales_data.csv
- somefile.png
- trees.csv
- WeightPred.sav

Now we can open a new jupyter notebook, import joblib and our model

```
In [1]: import joblib
KNN = joblib.load("WeightPred.sav")
KNN.predict([[70]])

Out[1]: array([133.4852])
```

We imported our model using the `load()` function and passed the saved model name. We also asked the model to predict the weight of a person with 70 inches of height and it passed 133.5 pounds