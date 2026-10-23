```
self.consonant = create_head(nf, n[2])

def forward(self, x):
    y = self.body(x)
    graph = self.grapheme(y)
    vowel = self.vowel(y)
    const = self.consonant(y)
    return [graph, vowel, const]
```

net = MultiModel(body, dls.c)
This model passes the inputs into the three pooling layers and returns the outputs.

# 17.4 Training the Model

For training we are borrowing some code from Miguel Pinto: https://www.kaggle.com/mnpinto/bengali-ai-fastai2-starter-lb0-9598

We need a CombinationLoss that is basically a Cross-Entropy-Loss, but has some weights associated with it. And we use a RecallMetric that looks at the last few predictions.

```
from sklearn.metrics import recall_score
class CombinationLoss(Module):
"Cross Entropy Loss on multiple targets"
def __init__(self, func=F.cross_entropy, weights=[2, 1, 1]): self.func, self.w = func, weights

def forward(self, xs, *ys, reduction='mean'):
for i, w, x, y in zip(range(len(xs)), self.w, xs, ys): if i == 0: loss = w*self.func(x, y, reduction=reduction)
else: loss += w*self.func(x, y, reduction=reduction)
return loss
class RecallPartial(Metric):
"Stores predictions and targets on CPU in accumulate to
```