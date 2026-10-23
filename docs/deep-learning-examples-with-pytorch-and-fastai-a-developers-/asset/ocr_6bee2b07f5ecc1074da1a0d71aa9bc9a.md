```
n = train[['grapheme_root', 'vowel_diacritic',
    'consonant_diacritic']].nunique();
print(n)
```

grapheme_root 168 vowel_diacritic 11 consonant_diacritic 7 dtype: int64
dls.c (#3) [168,11,7]

For the body of our model, we’ll use a standard resnet34. We need to modify the first ConvLayer so that it accepts a 1D image. There are a few ways to go about this. I chose this particular method, but the ResNet was trained for a three channel image. Therefore, we have to update the first layer in the body to accept a one-dimensional image.

```
body = create_body(resnet34, pretrained=True)
l = nn.Conv2d(1, 64, kernel_size=(7,7), stride=(2,2), padding=(3,3),
bias=False)
l.weight = nn.Parameter(l.weight.sum(dim=1, keepdim=True)) body[0] = l
```

# 17.3.1 Helper Functions for Visualization

As we have stated above, we will use the fastdot library to visualize our model architecture. We need some helper functions for this job.

```
from fastdot import *
def _fillcolor(o:str):
    if 'Lin' in o:
        return 'lightblue'
    elif 'ReLU' in o:
        return 'gray'
    elif 'Flatten' in o:
        return 'white'
    elif 'Pooling' in o:
        return 'pink'
    elif 'Conv' in o:
        return 'white'
    else:
        return 'gold'
```