classification.

With fastai we have a great opportunity to look into our model’s results by getting the classification-interpretation. This allows to show the most mismatched examples and plot a confusion matrix.

```
```python
interp = ClassificationInterpretation.from_learner(learn) losses, idxs =
interp.top_losses()
assert len(dls.valid_ds)==len(losses)==len(idxs)
```
```

This shows the top losses with the predicted and the actual class labels and the loss-values as well as the probability.

```
```python
interp.plot_top_losses(9, figsize=(15,10))
```
```

Now we print the confusion matrix. A “perfect” model would only have values on the diagonal because this means that the model has always predicted the correct label.

Below or above the diagonal are misclassified values.
`interp.plot_confusion_matrix(figsize=(12,12), dpi=75)` Not too bad for just doing 4 epochs of training.