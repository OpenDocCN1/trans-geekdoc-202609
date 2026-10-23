![](bbox=[0.12, 0.09, 0.35, 0.27])

![](bbox=[0.38, 0.09, 0.61, 0.27])

![](bbox=[0.64, 0.09, 0.88, 0.27])

![](bbox=[0.13, 0.31, 0.34, 0.48])

![](bbox=[0.38, 0.31, 0.61, 0.48])

![](bbox=[0.64, 0.3, 0.88, 0.48])

![](bbox=[0.12, 0.51, 0.35, 0.68])

![](bbox=[0.38, 0.51, 0.62, 0.68])

![](bbox=[0.65, 0.51, 0.88, 0.68])

The sample batch looks good.
Now we set the c (classes) property of our dataloaders so we can create the model’s output easier.

```
dataloaders.c = dataloaders.train.after_item.c
dataloaders.c
18
```

This means our model generates 18 classes – remember we want to regress on 9 different keypoints. This means we have to generate 9 pairs of keypoint coordinates (or 18 single values).