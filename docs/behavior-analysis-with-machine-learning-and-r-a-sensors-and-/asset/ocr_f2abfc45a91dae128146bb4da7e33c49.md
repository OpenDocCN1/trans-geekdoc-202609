![](bbox=[0.118, 0.095, 0.782, 0.395])

# # Predict classes.

```
classes <- model %%% predict_classes(testset$)
head(classes)
# [1] 2 2 1 3 0 1
```

Note that this function returns the classes with numbers starting with 0 just as in the original dataset.
Sometimes it is also useful to get the actual predicted scores for each class. This can be done with the predict_on_batch() function.

# # Make predictions on the test set.

```
predictions <- model %%% predict_on_batch(testset$)
head(predictions)
# [1] [2] [3]
# [1,1] 1.957638e-05 7.820648e-02 7.708290e-02 1.418910e-01
# [2,3] 3.937355e-05 2.571992e-04 9.966565e-03 3.136863e-03
# [3,4] 4.261451e-03 7.343097e-02 7.226156e-02 1.891673e-01
# [4,6] 8.669784e-06 2.088269e-04 1.339585e-01 8.657974e-01
# [5,1] 9.999956e-01 9.914154e-01 7.252949e-03 1.306421e-03
# [6] 2.513005e-05 9.914154e-01 7.252949e-03
```