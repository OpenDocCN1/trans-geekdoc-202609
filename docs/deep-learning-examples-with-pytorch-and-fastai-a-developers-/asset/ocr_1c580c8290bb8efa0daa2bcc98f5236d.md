```
learner.save('14-object-detection-stage1')
learner.load('14-object-detection-stage1')
<fastai2.learner.Learner at 0x7f11755f2e10>
```

UserWarning: changed to

Default grid_sample align_corners=False if the old behavior of grid_sample for details.

affine_grid behavior has

# 16.4 Using the Model for Inference

Now we can use the model for inference.

```
from matplotlib import patches, patheffects
import torch
import matplotlib.pyplot as plt
from torch import FloatTensor, LongTensor, tensor from fastai2.basics
import range_of
```

First of all we need some helper functions.

```
def _draw_outline(o, lw:int):
    'Outline bounding box onto image `Patch`.'
    o.set_path_effects([patheffects.Stroke(
        linewidth=lw, foreground='black'), patheffects.Normal())

def draw_rect(ax:plt.Axes, b, color:str='white', text=None, text_size=14):
    'Draw bounding box on `ax`.'
    patch = ax.add_patch(patches.Rectangle(b[:2], *b[-2:],
        fill=False,
        edgecolor=color,
        lw=2))
    _draw_outline(patch, 4)
    if text is not None:
```