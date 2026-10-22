# Generating Complex Animated Characters of Various Art Styles

As we can observe from the table and the graph in Figure 5, after the 17th epoch, the loss incurred by the generator dropped down by a notable amount and the irregular behaviour of the discriminator graph also started to maintain a uniform pattern. From this, we can conclude that minimum 17 epoch were required for the GANs to generate optimal and noticeable anime faces from the training dataset and for the discriminator to successfully identify fake images from the real ones most of the times. The occurrence of irregular ups and downs before we reach the 17th epoch was due to the variety of the size and resolutions of the different images available in the training dataset. For images with low resolution or smaller size, the training and the loss incurred would be less for obvious reasons.

# Table 1. Loss values of discriminator and generator, reality, and fake scores of the model

| EPOCH | LOSS_G | LOSS_D | REAL_SCORE | FAKE_SCORE |
|---|---|---|---|---|
| [1/30] | 4.2624 | 1.1897 | 0.4249 | 0.0093 |
| [2/30] | 5.9760 | 0.8490 | 0.9119 | 0.4983 |
| [3/30] | 3.8402 | 0.9353 | 0.4846 | 0.0069 |
| [4/30] | 2.9925 | 0.6088 | 0.6365 | 0.0305 |
| [5/30] | 5.1690 | 0.1698 | 0.9083 | 0.0525 |
| [6/30] | 4.3950 | 0.2587 | 0.8218 | 0.0264 |
| [7/30] | 2.2849 | 0.3693 | 0.7622 | 0.0405 |
| [8/30] | 3.2187 | 0.5357 | 0.7150 | 0.1080 |
| [9/30] | 3.6240 | 0.2696 | 0.9099 | 0.1414 |
| [10/30] | 7.7262 | 0.5394 | 0.9974 | 0.3779 |
| [11/30] | 3.8929 | 0.1152 | 0.9192 | 0.0244 |
| [12/30] | 3.8561 | 0.2422 | 0.8842 | 0.0933 |
| [13/30] | 4.2902 | 0.1991 | 0.9046 | 0.0742 |
| [14/30] | 4.0930 | 0.2184 | 0.9554 | 0.1379 |
| [15/30] | 7.7984 | 0.4650 | 0.9937 | 0.3324 |
| [16/30] | 3.1602 | 0.1860 | 0.8857 | 0.0514 |
| [17/30] | 7.7802 | 0.6216 | 0.9800 | 0.3848 |
| [18/30] | 2.8651 | 0.2135 | 0.8804 | 0.0685 |
| [19/30] | 6.5866 | 0.4255 | 0.9908 | 0.3017 |
| [20/30] | 3.5519 | 0.1718 | 0.8960 | 0.0512 |
| [21/30] | 4.6133 | 0.1810 | 0.9350 | 0.0958 |
| [22/30] | 3.9121 | 0.2642 | 0.9372 | 0.1533 |
| [23/30] | 5.0405 | 0.1111 | 0.9681 | 0.0699 |
| [24/30] | 3.8156 | 0.1017 | 0.9480 | 0.0434 |
| [25/30] | 3.3393 | 0.1257 | 0.9143 | 0.0264 |
| [26/30] | 5.5289 | 0.0867 | 0.9786 | 0.0582 |
| [27/30] | 3.7967 | 0.1027 | 0.9587 | 0.0548 |
| [28/30] | 6.1093 | 0.1129 | 0.9802 | 0.0805 |
| [29/30] | 1.7882 | 0.5672 | 0.6160 | 0.0021 |
| [30/30] | 4.1189 | 0.0807 | 0.9496 | 0.0251 |