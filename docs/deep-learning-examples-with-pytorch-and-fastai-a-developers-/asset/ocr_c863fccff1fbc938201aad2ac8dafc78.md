```
def setups(self, dl):
its = dl.do_item(0)
for t in its:

if isinstance(t, TensorPoint): self.c = t.numel()

def encodes(self, x:(PILBase,TensorImageBase)): return self._grab_sz(x)
def decodes(self, x:(PILBase,TensorImageBase)): return self._grab_sz(x)

def encodes(self, x:TensorPoint):
return _scale_pnts(x, self._get_sz(x), self.do_scale, _ self.y_first)
def decodes(self, x:TensorPoint):
return _unscale_pnts(x.view(-1, 2), self._get_sz(x))
```

Now we can make a DataBlock with our implemented code. We follow along the usual pattern: First call create, second do the scaling.

my_point_block = TransformBlock(type_tfms=myTensorPointCreate,
item_tfms=myPointScaler) If we use the @patch decorator, we can use any transform on our tensor-points.

```
def _neg_axis(x, axis):
x[..., axis] = x[..., axis]
return x
```

```
@patch
def flip_lr(x: TensorPoint): return
→ TensorPoint(_neg_axis(x.clone(), 0))
```

We have seen how to explore the internals of fastai. You could do this with any framework. Try replicating the implementation. This way you learn very well how the framework is built.

# Chapter 8

# Image Segmentation