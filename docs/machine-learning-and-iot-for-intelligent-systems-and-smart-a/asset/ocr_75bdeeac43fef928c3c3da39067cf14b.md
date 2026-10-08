![](bbox=[0.27, 0.06, 0.73, 0.51])

FIGURE 10.2 Block diagram.

# 10.2.3 MELANOMA SAMPLE IMAGE 1

In Figure 10.5a and 10.5b, we show the images of skin lesions before and after preprocessing is done. In Figure 10.5c and 10.5d, we show the histograms of the image before and after preprocessing is done.

# 10.2.4 MELANOMA SAMPLE IMAGE 2

In Figure 10.6a and 10.6b, the image of skin lesions before and preprocessing is done is depicted. In Figure 10.6c and 10.6d, the histograms of the original image before and after preprocessing is done are depicted.

The histograms clearly show the difference in the pixal density of colors between the original image and the preprocessed image.

# 10.3 TRANSFER LEARNING CAD SCC MODEL

ISIC dataset has been taken for training this model which has 1.8k benign and 1.4k malignant images. Model was trained using Transfer Learning technique. InceptionV3 was used as base network. InceptionV3 has 311 layers. The model was trained by retraining 100th layers onwards [32,33]. GlobalAveragePooling followed