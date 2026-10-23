SuggestedLRs(lr_min=0.00831763744354248, lr_steep=0.0012022644514217973)

![](bbox=[0.14, 0.13, 0.7, 0.42])

# choose a learning rate with a high negative slope

```
learn.fit_one_cycle(5, lr_max=(1e-3))
```

epoch train_loss valid_loss error_rate time

| epoch | train_loss | valid_loss | error_rate | time |
|---|---|---|---|---|
| 0 | 1.197415 | 0.257222 | 0.089986 | 00:48 |
| 1 | 0.480817 | 0.243021 | 0.084574 | 00:47 |
| 2 | 0.285627 | 0.192219 | 0.062246 | 00:47 |
| 3 | 0.159144 | 0.184564 | 0.053451 | 00:47 |
| 4 | 0.123560 | 0.187495 | 0.057510 | 00:47 |

So with the bigger model architecture, we get an even lower error rate of 0.05. Now we can do unfreezing and/or training for more epochs.

```
learn.save('resnet50')
```

Path('/home/bmayr/.fastai/data/oxford-iiit-pet/models/resnet50.pth') Again we can run unfreeze() and retrain the whole model

```
learn.load('resnet50')
learn.unfreeze()
learn.fit_one_cycle(2, lr_max=4e-4)
```