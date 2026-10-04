
The reconstructed feature maps are treated as the input of an `FCN` model. Considering the calculation speed, the basic structure of `LMB-CNN` is reused by `FCN`. However, the pooling operations and the full connection layers are removed to keep the feature map’s size unchanged. The structure of the `FCN` model is shown in [Fig. 6](#chap8.xhtml#fig6), taking an 8-kernel depthwise separable convolutional layer activated by a sigmoid function as the end of the network, which outputs eight channel segmentation masks to improve the segmentation reliability. Intuitively, voting on the multiple decisions is better than only one decision since different output channels consider different inner characteristics of the input features. [Figure 7](#chap8.xhtml#fig7) gives an intuitive view of the eight outputs. Experimental results in [Table 4](#chap8.xhtml#tab4) show that the voting strategy can reduce the false alarms and missing alarms.

![](images/p189-1.jpg)

**Figure 5:** The first nine reconstructed feature maps with size of 160 × 160 (corresponding to the sample image with 10240 × 10240 pixels), in which the deep features are extracted by `LMB-CNN`.

To train the `FCN` model, considering that the extraction of built-up area is a binary classification problem, it is convenient to measure the difference between the output results of each channel and ground truth by the mean square error. It also avoids the probability calculation when using cross-entropy. Besides, for this issue the false alarms and missing alarm which attract attention are usually located on the boundary of the built-up area. The sigmoid output probabilities of these samples are usually around 0.5 if one selects cross-entropy. However, the mean square error can highlight the contributions of these samples. Therefore, the loss function based on the square error is adopted for training the `FCN` model, but the output is divided into three parts when calculating the loss function: correct classification, false alarm and missing alarm. The specific loss function is as follows:

![](images/p190-1.jpg)

**Figure 6:** The structure of the `FCN` model.

![](images/p190-2.jpg)

**Figure 7:** The eight preliminary segmentation masks that are produced by the `FCN` model.

**Table 4.** Results of different voting thresholds.

![](images/p191-1.jpg)

![](images/p191-2.png)

where `h[θ](x^{(i)})` indicates the output of the `FCN` model and `y^{(i)}` is the ground truth. `y^{(i)} = 1` represents the built-up area and `y^{(i)} = 0` is the non-built-up area. `α` and `β` are the parameters that can be specified, and is the threshold discriminant result of `h[θ](x^{(i)})`, which is given as follows:

![](images/p191-3.png)

By adjusting the weights of the loss function, the contribution of the error classification part can be increased to avoid being covered by the correct classification part. In fact, after a certain number of iterations, more than 90% of the units will be classified correctly.

The eight segmentation masks of the `FCN` model are shown in [Fig. 7](#chap8.xhtml#fig7). There is an ~6% difference between each pair of masks, which indicates that each block may have varied binary values in different masks. The final segmentation result can be obtained via voting. Because each block is now a pixel in the feature maps, the voting process is converted to count the number of pixels being determined as built-up areas. The counting number is computed as follows:

![](images/p192-1.png)

where ![](images/in192-1.png) is the segmentation binary value in the `j`th mask map according to Eq. (10). According to experimental result, set the voting threshold to 4 to achieve the balance between the false alarm and the missing alarm. In practical applications, the threshold can be adjusted according to the emphasis on the false alarms and missing alarms. The range of the threshold has little effect on the overall precision.

## 7. Post-processing

Only a block-level result can be obtained by `DSCNN`, `LMB-CNN` or `FCN` compared to the pixel-level results of classical methods. In addition, built-up area refers to a region which has been exploited and constructed, it needs certain acreage larger than a threshold, and a small area of grass, pond, etc. should also be part of the built-up area. So post-processing is necessary to make the results more reasonable.

To remove the detected region where the acreage is not reached, setting the threshold of built-up area as 5-image patches is reasonable, taking the acreage of some villages into consideration. Each patch corresponds to an area of 64 m × 64 m. In addition, the lawns, pools and hills within the built-up area should be identified as parts of the built-up area, so the non-built-up area that is smaller than 5-image patches should be converted to built-up area, too.

For pixel-level results, just considering the aesthetics of the edges and simply enlarging the binary image of block-level results in the original size being enough such that the interpolation process smooths the boundary of built-up area. The results are shown in [Fig. 8](#chap8.xhtml#fig8). To obtain more an elaborate boundary, you can follow these steps:

(1) A simple linear iterative clustering (`SLIC`) [[59](#chap8.xhtml#fsr59)] segmentation operation is applied to the boundary blocks of built-up area, with a recommendation to set the parameters `spcount` as 16, `compactness` as 20, so that each super pixel is about 16 × 16 pixels.

![](images/p193-1.jpg)

**Figure 8:** (a) Shows block-level result. Treat each block as a pixel and enlarge it to original size, then obtain (b).

(2) Calculate the average vegetation indexes `AVE_NDVI` and `AVE_SAVI` of each super pixel, and then judge them by Eq. (14). `NDVI` [[60](#chap8.xhtml#fsr60)] and `SAVI` [[61](#chap8.xhtml#fsr61)] are calculated as Eqs. (12) and (13), where `Band[x]` represents the different bands of multi-spectral data, `L` means the adjustment coefficient of soil which ranges from 0 to 1. It has no vegetation coverage when `L` equals to 1, and the influence of soil background can be ignored when `L` equals to 0. Usually choosing `L = 0.5` is good enough. In Eq. (14), 0 means non-built-up area while 1 means built-up area. The threshold values are the corresponding vegetation index ranges of woodland and grassland [[62](#chap8.xhtml#fsr62)].

(3) Change the category of boundary super pixels which are judged as non-built-up area.

A more elaborate boundary based on super-pixel technology can be generated just like [Fig. 9](#chap8.xhtml#fig9), but time consumption is an obvious shortcoming, as this step takes much longer than the CNN part. In practice, boundary refinement based on super-pixel basically leads to no increase in accuracy according to statistical results, therefore, the first method to make the boundary more delicate is recommended.

![](images/p193-2.png)

![](images/p194-1.jpg)

**Figure 9:** (a) shows block-level result of `DSCNN`. (b) shows result refined based on `SLIC`.

![](images/p194-2.png)

## 8. Experimental Comparison with Classical Methods

The three depth models mentioned above have limited difference in classification accuracy, therefore, making the `FCN` model an example to compare with some classical methods. The performance of the algorithms is verified by four evaluation indexes, namely, User’s Accuracy, Producer’s Accuracy, Overall Accuracy and mean intersection-over union (`IOU`). The formulas of these indexes are as follows:

![](images/p195-1.png)
