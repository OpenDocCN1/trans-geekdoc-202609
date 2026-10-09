$H=-\sum_{i=1}^{M} p_{i}\log p_{i}$ (9.1)

Image entropy for a 2D slice of a volume image can be calculated through image histograms [14]. The key reason behind using entropy is that it provides a reasonable measure of how much information (or variation of data) a slice of an image contains. Higher entropy typically points to images that have rich information. Instead of using randomly selected images, we can select the most informative slices by utilizing image entropy in this manner, which will result in a more robust dataset.

In Table 9.1, we show that through our proposed entropy-based image filtering combined with transfer learning, we can achieve state-of-the-art classification results for all three classification scenarios in Alzheimer’s prediction. The three classification problems are AD vs. normal control (NC), mild cognitive impairment (MCI) vs. AD, and MCI vs. NC on the benchmark ADNI dataset [5]. Although we get a reasonable boost in accuracy, the more important contribution is the reduction in the size of the training set. The closest competitor or proposed method is that of Ref. [16], with a training size of 39,942, while our proposed method has a training size of only 2,560, thus providing a reduction of 16 times. Transfer learning combined with our intelligent training-data filtering method can reduce the excessive reliance on a large amount of training data, making deep learning more usable in clinical settings.

We further investigated whether making some convolutional layers trainable results in improved accuracy. In Figure 9.1, we see comparative results for all three classification problems (AD vs. NC, AD vs. MCI, and MCI vs. NC) when groups of convolutional layers are frozen together. The groups correspond to the freezing of VGG16 conv. layers as follows:

+   1.  **All:** None of the convolutional layers are frozen (all of them trainable).
2.  **Group 1:** The first four convolutional layers are frozen

| TABLE 9.1 Accuracy Results (in %) Compared to State-of-the-Art on the ADNI Dataset. | | | | |
|---|---|---|---|
| *Architecture* | *Training Set (# Images)* | *AD vs. NC* | *AD vs. MCI* | *MCI vs. NC* |
| Patch-based autoencoder [15] | 103,683 | 94.74 | 88.1 | 86.35 |
| 3D CNN [16] | 39,942 | 97.6 | 95 | 90.8 |
| Inception [17] | 46,751 | 98.84 | – | – |
| Proposed | **2,560** | **99.36** | **99.2** | **99.04** |
| | | | | |
| *Note: Best method in Bold* | | | | |