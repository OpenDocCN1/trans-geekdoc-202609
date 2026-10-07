# Applying the Bagging classifier model on live data

The purpose of building the model is to make predictions on live data. For this purpose, we demonstrate the mechanics of applying the model to the live data. The following code loads the live data and makes predictions on the same.

# Set the model to Random Forest Model we just developed

```
MODEL = bc
```

# Load the Kaggle Files

```
kaggleFiles = glob.glob('./Kaggle_Testset/Kaggle_Testset/*.wav',\nrecursive = False)
```

# Extract features from the Kaggle Files

```
XKaggle = extractFeaturesFromFiles(kaggleFiles)
```

# Make predictions for the emotions in the Kaggle Files

```
dfKaggle = pd.DataFrame(columns = ['Id'
```

```
print(dfKaggle.head())
100%| 201/201 [00:19<00:00, 10.38it/s]
```

| Id | Label |
|---|---|
| 0 | 16 happy |
| 1 | 103 neutral |
| 2 | 117 angry |