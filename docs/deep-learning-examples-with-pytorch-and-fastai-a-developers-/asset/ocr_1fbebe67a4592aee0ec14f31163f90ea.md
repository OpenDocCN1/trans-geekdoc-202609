We also need some transforms. We will use the mean and standard deviation from above.

```
batch_tfms = [*aug_transforms(do_flip=False, size=128),
Normalize.from_stats(mean=0.0692, std=0.2051)]
```

```
bengel = DataBlock(blocks=blocks,
getters = getters,
splitter=RandomSplitter(),
batch_tfms=batch_tfms,
n_inp=1)
```

```
bs=128
```

To increase training speed we will just use a subsample with 1000 items for training our model.

```
dls = bengel.dataloaders(train.sample(1000), bs=bs)
dls.show_batch(max_n=1, figsize=(3,3))
```

![](bbox=[0.225, 0.455, 0.315, 0.695])

To make sure everything went fine, we can print a sample batch. We see the image and our three labels.

# 17.3 Custom Heads

We want one model that does three jobs at once. Therefore we have to create custom heads.

DATASET FROM KAGGLE