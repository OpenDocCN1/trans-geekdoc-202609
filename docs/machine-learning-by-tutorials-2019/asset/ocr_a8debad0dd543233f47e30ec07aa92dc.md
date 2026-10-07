# Machine Learning Chapter 5: Digging Deeper into Turi Create

MXFeatureExtractor is an object from the MXNet machine learning framework that Turi Create is built on. In Python, names starting with underscore are considered to be private, but you can still import them. Next, enter and run this code statement:

```
train_features = feature_extractor.extract_features(train_data, "image", verbose=True)
```

You're using the MXFeatureExtractor to extract the SqueezeNet features from the training dataset. This is the operation that takes the most time when you run tc.image_classifier.create(). By running this separately, you won't have to wait for feature extraction every time you want to train the classifier. Next, enter and run this code statement:

```
extracted_train_features = tc.SFrame({"label": train_data["label"], "image_features__": train_features})
```

Here, you're just combining the features of each image with its respective label into a new SFrame. This is worth saving for later! Enter and run this code statement:

```
extracted_train_features.save("extracted_train_features.sframe")
```

You're saving extracted_train_features to a file. The next time you want to do more training with these same features, you can simply load the SFrame again, which takes a fraction of the time it took to extract the features:

```
# Run this tomorrow or next week
extracted_train_features = tc.SFrame("extracted_train_features.sframe")
```