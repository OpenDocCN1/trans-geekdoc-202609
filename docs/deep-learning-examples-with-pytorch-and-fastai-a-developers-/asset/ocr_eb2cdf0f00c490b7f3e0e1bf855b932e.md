to improve the performance of our model.

```
learn = audio_learner(dls, xresnet18(), CrossEntropyLossFlat(), → accuracy)
learn.lr_find()
```

(0.06309573650360108, 0.0030199517495930195)

![](bbox=[0.13, 0.22, 0.71, 0.52])

```
learn.fit_one_cycle(5, 1e-2)
```

epoch train_loss valid_loss accuracy time

0 3.944870 2.120851 0.300000 00:01
1 2.000032 4.179723 0.307500 00:01
2 1.246085 0.557256 0.835000 00:01
3 0.844206 0.506152 0.847500 00:01
4 0.599616 0.128170 0.960000 00:01

# 20.8 MFCC + Delta

Another transform we are looking at is the Delta transform.
A delta is defined as the local estimate of the derivative of the input data along the selected axis.

This means we can generate multiple channels out of one single signal. We see the different channels with the batch-data (channel image 0, channel