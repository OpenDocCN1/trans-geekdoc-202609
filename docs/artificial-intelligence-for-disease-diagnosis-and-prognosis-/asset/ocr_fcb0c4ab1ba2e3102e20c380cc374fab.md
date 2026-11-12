The results of the confusion matrices are provided in Figure 14.5. The confusion matrix visualizes the true vs predicted label deviation. In these results, it can be seen that the proposed method clearly outperformed the competing models with a few mis-classification rates.

The proposed method is also tested on the live video stream. Figure 14.6 presents the results of facemask detection. In the figure, a bounding box around a person’s face was drawn with green or red text which denotes the existence of a mask and no mask, respectively.

![](bbox=[0.123, 0.24, 0.894, 0.372])

Figure 14.4 The trend of training and validation performance over each epoch. (a) MobileNet V2, (b) RestNet50, (c) VGG16 (Proposed).

![](bbox=[0.106, 0.455, 0.894, 0.63])

Figure 14.5 The confusion matrices of three different algorithms on the test dataset: (a) MobileNet V2, (b) RestNet50, (c) VGG16 (Proposed).

# 14.5 CONCLUSION AND FUTURE WORK

In this chapter, we developed a deep learning-based automated facemask detection system. The proposed methodology deployed a visual geometry group network (VGG16) to learn mask and non-mask benchmark datasets. But it is required an abundance of the dataset for accurate model building. Thus, we applied a transfer learning scheme that integrates a pre-trained VGG16 model on the ImageNet dataset to mitigate the data scanty situation. To verify the effectiveness of the proposed method, we performed rigorous experiments on benchmark offline datasets and real-time video streams. The experimental results suggest that the proposed facemask detection system is highly effective on both office and real-time images, yielding 41%