The parameters for fully or local connectivity for all the layers in this CNN are listed in Table 1.

The system can be visualized with simplification in Figure 7.

# System Validation Using ImageNET Dataset

Before applying this system into the ocean fish data set developed in this research, authors downloaded images from the well-known ImageNet ILSVRC [21] to do a system validation testing through object classification. There are 500 images with 20 classes ranging from fish, coral, sea turtle, frog, ship, etc. Here all the RGB images are rescaled to 448×448. Ground truths images are obtained from operate labeling soware manually. Each image is divided into a grid of 7×7 cells. Each cell will predict the two bounding boxes location information and class information made up of a 1×1×30 vector. This vector consists of object center coordinates (X, Y), the width w, and height h of the bounding box confidence scores, and predicted probabilities of fish, as shown in Figure 8.To predict the target location of an image, the target is displayed in a bounding box. There are always errors between the ground truth and the predictions. Loss function was developed to measure errors consisting of three parts: coordinate error, (Intersection over union) IoU error, and class error. Equation (2) gives the mathematics form of the loss function.

```
Loss = \sum_{i=0}^{S} coordError + IoUError + classError.
```

Here, IoU is used to measure position accuracy as shown in Figure 9.

![](bbox=[0.295, 0.655, 0.685, 0.79])

Figure 4. Feature extractor using convolutional operation.