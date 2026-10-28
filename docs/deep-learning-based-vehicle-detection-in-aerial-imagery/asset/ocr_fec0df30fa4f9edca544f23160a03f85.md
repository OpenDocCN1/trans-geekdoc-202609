![](bbox=[0.15, 0.14, 0.88, 0.42])

Figure 7.8: Example images of the training set used to train the SAR classifier for DLR 3K. The top row shows examples for the category with at least one object, while the bottom row shows examples for the category without objects.

The SAR classifier is trained for 10,000 iterations with a batch size of 8. The initial learning rate is set to 0.001 and decreased after 5,000 iterations by a factor of 10. Note that all weights of Faster R-CNN are kept fixed in the second training stage.

For deployment, the sub-division-SAR layer, sub-division-RPN layer, and the modified proposal layer are added to the framework to perform the search area reduction and the detection in a single network as depicted in Figure 7.7. For each tile, NMS is applied on the 400 region proposals exhibiting the highest confidence score. The top-80 ranked proposals after NMS are then forwarded to the classification stage. As the input images are divided into 25 tiles, the maximum number of proposals before and after NMS are 10,000 and 2,000, respectively, which is equivalent to the numbers for Faster R-CNN without the SAR module (see Section 5.1.3). The further settings are analogous to the settings employed for Faster R-CNN without the SAR module.

# 7.2.3 Ablation Experiments

The impact of the proposed SAR module on the inference time is evaluated on the DLR 3K dataset and the VEDAI LCI dataset in order to account for different area categories with varying vehicle distributions, as the speed-up