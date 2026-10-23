```
```python
→ thresh=0.5, **kwargs):
super().__init__(nn.BCEWithLogitsLoss,
*args,
axis=axis,
floatify=floatify,
is_2d=False,
**kwargs)
self.thresh = thresh

def decodes(self, x): return x>self.thresh
def activation(self, x): return torch.sigmoid(x)
```
```

The code above shows the implementation of the loss-function. We first calculate a sigmoid activation: return torch.sigmoid(x) and afterwards we check whether the values are higher than a threshold. This way we can detect multiple labels for our data.

```
```python
learner.loss_func = BCEWithLogitsLossFlat()
learner.lr_find()
```
```

If we switch our model to *mixed-precision*, our model will train a bit faster.

```
```python
lr = 1e-2
learner = learner.to_fp16()
learner.fit_one_cycle(5, slice(lr))
```
```

| epoch | train_loss | valid_loss | accuracy_multi | time |
|---:|---:|---:|---:|---:|
| 0 | 0.950392 | 0.850503 | 0.554118 | 00:04 |
| 1 | 0.720215 | 0.239568 | 0.929118 | 00:03 |
| 2 | 0.508768 | 0.169727 | 0.942647 | 00:03 |
| 3 | 0.389080 | 0.154983 | 0.945000 | 00:03 |
| 4 | 0.316210 | 0.152061 | 0.945588 | 00:03 |

```
```python
learner.save('stage-1')
```
```

Now we unfreeze and train for some more epochs.

```
```python
learner.unfreeze()
learner.lr_find()
(0.00010000000474974513, 5.248074330665986e-07)
```
```