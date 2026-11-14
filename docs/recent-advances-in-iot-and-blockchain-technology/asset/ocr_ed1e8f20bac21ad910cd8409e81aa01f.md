repeated activation results in a feature map which in turn is used by the maxpoolig2d layer. Pseudocodes for Accuracy metric and loss function has been shown in Figs. (6 and 7), respectively:

```
#accuracy Metric
from keras import backend as K
def iou_coef(y_true, y_pred, smooth=1):
    intersection = K.sum(K.abs(y_true * y_pred), axis=[1,2,3])
    union = K.sum(y_true,[1,2,3])+K.sum(y_pred,[1,2,3])-intersection
    iou = K.mean(((intersection + smooth) / (union + smooth)), axis=0)

    return iou
```

Fig. (6). Accuracy Metric determined using accuracy and loss metrics.

```
#loss function
def dice_coef(y_true, y_pred, smooth = 1):
    y_true_f = K.flatten(y_true)
    y_pred_f = K.flatten(y_pred)
    intersection = K.sum(y_true_f * y_pred_f)
    return (2. * intersection + smooth) / (K.sum(y_true_f) + K.sum(y_pred_f) + smooth)

def soft_dice_loss(y_true, y_pred):
    return 1-dice_coef(y_true, y_pred)
```

Fig. (7). Loss Function.

After the sample is downsampled and features are extracted, the model starts upsampling. Also, an important point to note is that selectively downsampling connections made to the mirror side of U-Net known as skip connection, which helps in encoder and decoder type of architecture to retrieve fine details in prediction might have been lost during processing through various layers.

# Splitting and Training

After pre-processing the dataset and defining our model we need to split our data into the train and test samples. Training data consists of 80% images and the rest 20% of images correspond to testing data from the sample. This splitting has been shown in Fig. (8).