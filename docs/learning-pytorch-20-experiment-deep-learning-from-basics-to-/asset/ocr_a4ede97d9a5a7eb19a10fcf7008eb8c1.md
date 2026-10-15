```
return x * self.weight
```

In the given codes, MyLayer is a custom layer that scales its input by a trainable weight. nn.Parameter is a special kind of tensor that's automatically included in the parameters list of a nn.Module. This means that PyTorch will consider this weight as a trainable parameter of the model.

Now, we will define a custom network that uses this custom layer:

```
class MyNetwork(nn.Module):
```

```
def __init__(self):
```

```
super(MyNetwork, self).__init__()
```

```
self.layer1 = MyLayer()
```

```
self.layer2 = MyLayer()
```

```
def forward(self, x):
```