– a special class from the fastai framework. We will train this one for some epochs too.

```
loss_crit = AdaptiveLoss(nn.BCEWithLogitsLoss())
```

```
def create_crit_learner(dls, metrics):
return Learner(dls, gan_critic(),
metrics=metrics,
loss_func=loss_crit)
```

![](bbox=[0.12, 0.31, 0.35, 0.5])

![](bbox=[0.38, 0.31, 0.62, 0.5])

![](bbox=[0.65, 0.31, 0.88, 0.5])

![](bbox=[0.12, 0.52, 0.35, 0.7])

![](bbox=[0.38, 0.52, 0.62, 0.7])

![](bbox=[0.65, 0.52, 0.88, 0.7])

![](bbox=[0.12, 0.72, 0.35, 0.9])

![](bbox=[0.38, 0.72, 0.62, 0.9])

![](bbox=[0.65, 0.72, 0.88, 0.9])