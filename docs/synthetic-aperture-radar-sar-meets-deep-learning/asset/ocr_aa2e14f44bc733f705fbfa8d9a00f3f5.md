![](bbox=[0.27, 0.17, 0.7, 0.66])

Figure 18. Four detailed areas of road extraction results in complicated scene images (a) area of label image; (b) D-LinkNet; (c) S-DenseNet; (d) SD-DenseNet; (e) SDG-DenseNet.

Figures 14 and 15 show the extraction results of general scene images. D-LinkNet shows the network built on residual blocks and the encoder part, DenseNet shows the network built on the Dense block, S-DenseNet shows the network built on Dense block and Stem block, SD-DenseNet represents that the network has also added dilated convolution on the basis of the previous networks, and SDG-DenseNet is built on the basis of the Stem block, D-Dense Blocks, and the GIRM module. The extraction results of the DLinkNet model contain some redundant information, and many independent patches are left in the image, which could affect the result of the overall accuracy. The parking lot areas, which are similar to roads, were successfully identified as backgrounds. However, some roads are not completely extracted. SDG-DenseNet has been further improved to make the completeness of roads better. The information extracted by the SDG-DenseNet network structure is more accurate.

Figure 15 shows the IoU scores for each image in each row in Figure 14. The proposed SDG-DenseNet achieves high IoU scores under all three optical images, which are 9.53%, 9.46%, and 8.18% higher than the baseline D-LinkNet, respectively.

Figure 16 shows the three extraction results of the complicated scene images from the 49 test images. Each road network includes more different level roads and flyover roads.