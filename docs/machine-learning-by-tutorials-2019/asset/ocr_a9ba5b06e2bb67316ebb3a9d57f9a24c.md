# Inspecting the extracted features

Let's see what these features actually look like — enter and run this command:

```
extracted_train_features.head()
```

| _image_features_ | label |
|--- |--- |
| 8.133785177612305, 10.1284418106079, ... | apple |
| 9.666998816894531, 14.6653202581871, ... | apple |
| 10.662542223237637, 15.4729650447856, ... | apple |
| 12.1590135042832, 11.2351984571532, ... | apple |

The head of the extracted features table

Each row has the features for one training image. The `_image_features_` column contains a list with numbers, while the label column has the corresponding class name for them. Enter and run this command:

```
extracted_train_features[]("__image_features_")
```

This shows what a feature 'd' looks like — it prints something like:

```
array('d', [6.133785177612305, 10.1284418106079, 13.0251061628129, 7.93194305419522, 12.038099288894043, 15.1032281924219, 12.72883714904875, 10.93909343475341, 17.2873115442818, 14.2080370068359, 16.8399658203125, 11.71684875488281, ...])
```

This is a list of 1000 vectors — use `len()` to verify this. They all appear to be numbers between 0 and about 30. What do they represent? I have no idea, but the features that SqueezeNet has determined to be important — long, round, square, orange, etc. the objects are. All that matters is that you can train a logistic classifier to learn from these features.

In the same way, extract the features for the images from the validation dataset, and save them as a DataFrame to file:

```
val_features = feature_extractor.extract_features(val_data,
  "image", verbose=True)
extracted_val_features = tc.SFrame(
  "label": val_data["label"],
  "_image_features_": val_features,
```