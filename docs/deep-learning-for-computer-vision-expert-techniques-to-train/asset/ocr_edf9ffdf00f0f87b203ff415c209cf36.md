# Faster R-CNN

Faster R-CNN is proposed by Ren et al. (https://arxiv.org/pdf/1506.01497.pdf). The difference between Faster R-CNN and the Fast R-CNN method is that Faster R-CNN uses CNN features of architecture such as VGG and Inception for proposals instead of selective search. The CNN features are further passed through the region proposal network. A sliding window is passed through features with potential bounding boxes and scores as the output, as well as a few aspect ratios that are intuitive, the model outputs bounding box and score:

![](bbox=[0.238, 0.303, 0.762, 0.597])

Faster R-CNN is faster than Fast R-CNN as it saves computation by computing the feature only once.

# Single shot multi-box detector

SSD (Single shot multi-box) is proposed by the fastest of all the methods. This method simultaneously predicts the object and finds the bounding box. During training, there be a lot of negatives and hence hard-negative mining the class imbalance. The output from CNN has various sizes of features. These are passed to a 3x3 convolutional filter to predict bounding box.