← 'VAS C': 6

CODE 7.1: The seven categories of skin lesions.

2 Several possible augmentations are presented in Code (7.2). It is usually, that by trial and error one finds the best possible augmentation for a target data-set. However, methods such as AutoAugment may render the manual selection of augmentations obsolete.

```
```
1  self.transforms = []
2  if rotate:
3      self.transforms.append(RandomRotate())
4  if flip:
5      self.transforms.append(RandomFlip())
6  if brightness != 0:
7      self.transforms.append(PILBrightness())
8  if contrast != 0:
9      self.transforms.append(PILContrast())
10 if colorbalance != 0:
11     self.transforms.append(PILColorBalance())
12 if sharpness != 0:
13     self.transforms.append(PILSharpness())
```
```

CODE 7.2: Pseudoe code for augmentations.

3 In contrast to the ResNet CNN which ends by an FC layer, the ImageNet pre-trained DPN CNN family, in this case the pretrainedmodels.dpn107, terminated by a Conv2d layer and hence must be adapted accordingly if one wishes to change the number fo classes from the 1000 (ImageNet) classes to our skin lesion classification problem (7 classes). Line 7 in Code (7.3) demonstrated this idiom.

```
```python
1 import torch
```
```