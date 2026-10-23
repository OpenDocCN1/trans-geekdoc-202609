# Target/Prediction

![](bbox=[0.12, 0.17, 0.47, 0.37])

![](bbox=[0.53, 0.17, 0.88, 0.37])

# 8.2.2 Testing our Model on the Testdataset

Now we can check how the model does on the testdataset. First we show the first four images from the testdataset. We can grab these from our learner’s dataloaders:

```
dl = learner.dls.test_dl(fnames[:4])
dl.show_batch()
```

With the test-dataloader we can do a prediction of a set of images instead of just predicting the target value for a single input.

![](bbox=[0.12, 0.65, 0.36, 0.78])

![](bbox=[0.4, 0.65, 0.63, 0.78])

We pass over our dataloader dl as the dataloader parameter for the get_preds-function. You would also do so if you serve your model and you want the server to do batch-predictions.