# Machine Learning Chapter 5: Digging Deeper into Turi

When you run this cell, you'll be pleasantly surprised at how fast the feature extraction is, compared to last chapter. This is because SqueezeNet extracts only 1000 features from 227×227-pixel images, compared with VisionFeaturePrint_Screen’s 2048 features from 299×299 images.

However, you'll probably be disappointed by the training and validation accuracies:

| Iteration | Passes | Step size | Elapsed Time | Training Accuracy | Validation Accuracy |
|---|---|---|---|---|--|
| 9 | 16 | 1.000000 | 2.250278 | 0.447152 | 0.373901 |
| 24 | 41 | 1.000000 | 5.490575 | 0.597476 | 0.533058 |
| 49 | 77 | 1.000000 | 11.472903 | 0.706684 | 0.648760 |
| 74 | 113 | 1.000000 | 17.694513 | 0.755657 | 0.661157 |
| 99 | 162 | 1.0.0000 | 25.050267 | 0.803525 | 0.670412 |

> Note: It's likely you will slightly different results than what is shown in this book. Recall untrained models, in cases the logistic regression part of the model, are initialized with random numbers. This can cause variations between different training runs. Just try again if you get a training accuracy that is much less than 65%. Advanced users of machine learning actually take advantage of these differences between training runs to combine multiple models into one ensemble that gives more robust predictions.

Like Create ML, Turi Create randomly chooses 5% of the training data as validation data, so validation accuracies can vary quite a bit between training runs. The model might do better on a larger fixed validation dataset that you choose yourself (which you'll do in this chapter).

Evaluate the model and display metrics:

```
metrics = model.evaluate(test_data)
print("Accuracy:
```

No surprises — accuracy is pretty close to the validation accuracy:

Accuracy: 0.6470588235294188
Precision: 0.644134936364582
Recall: 0.6445289115646259