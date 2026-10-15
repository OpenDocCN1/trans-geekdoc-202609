dataset, likely as it is beginning to overfit the data. We see a rough drop in classification accuracy on the test dataset, likely because of the overfitting.

```
> layers=2, train=0.816, test=0.830
> layers=3, train=0.834, test=0.830
> layers=4, train=0.836, test=0.824
> layers=5, train=0.830, test=0.824
> layers=6, train=0.848, test=0.820
> layers=7, train=0.830, test=0.826
> layers=8, train=0.850, test=0.824
> layers=9, train=0.840, test=0.838
> layers=10, train=0.842, test=0.830
> layers=11, train=0.850, test=0.830
> layers=12, train=0.850, test=0.826
```

Listing 10.21: Example output from supervised pre-training on the blobs problem.

A line plot is also created showing the train (blue) and test set (orange) accuracy as each additional layer is added to the model. In this case, the plot suggests a slight overfitting of the training dataset, but perhaps better test set performance after seven added layers.

![](bbox=[0.14, 0.45, 0.8, 0.8])

Figure 10.2: Line Plot for Supervised Greedy Layer-Wise Pretraining Showing Model Layers vs Train and Test Set Classification Accuracy on the Blobs Classification Problem.

An interesting extension to this example would be to allow all weights in the model to be