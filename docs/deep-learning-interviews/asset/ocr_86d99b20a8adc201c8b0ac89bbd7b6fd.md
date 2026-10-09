same logic on the ResNet152 architecture, the resulting FV has 2048 floating point elements.

![](bbox=[0.24, 0.15, 0.8, 0.38])

```
```
import torchvision.models as models
...
res_model = models. resnet34(pretrained= True)
```
```

FIGURE 7.2: PyTorch declaration for a pre-trained ResNet34 CNN (simplified).

The premise behind FE is that CNNs which were originally trained on the ImageNet Large Scale Visual Recognition Competition [ 2 ], can be adapted and used (for instance in a classification task) on a completely different (target) domain **without any additional training** of the CNN layers. The power of a CNN to do so lies in its ability to generalize well beyond the original data-set it was trained on, therefore FE on a new target data-set involves no training and requires only inference.

# 7.2 Problems

# 7.2.1 CNN as Fixed Feature Extractor

Before attempting the problems in this chapter you are highly encouraged to read the following papers [ 1 , 3 , 2 ]. In many DL job interviews, you will be presented with a paper you have never seen before and subsequently be asked