![](bbox=[0.12, 0.1, 0.9, 0.46])

snet-fd90ca15d6ec

You can have a look at the source code of ResBlock in fastai: ??ResBlock.

But by now we want to build a ResBlock on our own. We define a class ResBlock that inherits from a fastai Module. This is why we only have to overwrite the constructor (__init__) and the forward method.

So if we want to see the implementation of Module, again we just call ?? Module.

```
class ResBlock(Module):
def __init__(self, number_filters: int):
    self.conv1 = ConvLayer(number_filters, number_filters)
    self.conv2 = ConvLayer(number_filters, number_filters)

def forward(self, x):
    return x + self.conv2(self.conv1(x))
```

We use this ResBlock and add it between our conv2 layers in the last model. This provides a rather complicated model-architecture.

```
model = nn.Sequential(
```