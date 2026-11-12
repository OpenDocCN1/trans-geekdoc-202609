# Figure 31. Implementation of CRF for the outcome of FCN- 8 and FCN-16 (Prisilla, Iyyanki & Aruna, 2018)

![](bbox=[0.26, 0.175, 0.75, 0.675])

a) Test image   b) ground truth   c) prediction

Pooling (Prisilla, Iyyanki & Aruna, 2018) helps in classifying networks and decreases the resolution with loss of information; hence the skip connections are implemented. The output of FCN-8 and FCN-32 model is depicted in the Appendix -2, and the results of the images passed in this model are shown in figure 31.

The transfer learning paradigm helps in saving lot of computational cost, time and increases the efficiency. Hence fully conv nets segments image at pixel level, this promotes the use of end-to-end conv network for semantic segmentation.