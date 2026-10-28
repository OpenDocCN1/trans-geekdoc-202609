by a sequence of fully connected layers branching in two fully connected layers: one for classification and one for bounding box regression. Note that by default the sequence of fully connected layers is adopted from the VGG16 base network. Due to the absence of fully connected layers in ZynqNet, different combinations of layers are examined as so-called classification head. The first examined classification head, in the following termed ZynqNet-Head, comprises all layers from ZynqNet after the 5<sup>th</sup> Fire module through the 9<sup>th</sup> Fire module followed by the two sibling fully connected layers for classification and regression, which remain unchanged for all setups. Furthermore, the default classification head termed VGG-Head is employed, whereby the fully connected layers are randomly initialized by using the Gaussian weight filler method. To retain a small parameter count, two variations of the VGG-Head classification head comprising fewer parameters are examined. For this, the number of outputs of each fully connected layer is reduced by factor 2 and 4, respectively.

**Table 7.11:** Comparison of the detection accuracy and the inference time for Faster R-CNN with different base networks on the DLR 3K dataset. For the ZynqNet architecture, different combinations of layers are examined as classification head due to the absence of fully connected layers.

| Base Network | Classification Head | AP (in %) | Time (in ms) Server | Time (in ms) Desktop |
|---|---|---:|---:|---:|
| VGG16 | VGG-Head | **94.3** | 286.2 | 663.5 |
| ZynqNet | ZynqNet-Head | 93.8 | 164.9 | 227.8 |
| ZynqNet | VGG-Head | 94.1 | 188.0 | 313.2 |
| ZynqNet | VGG<sub>0.5</sub>-Head | 94.1 | 166.7 | 227.0 |
| ZynqNet | VGG<sub>0.25</sub>-Head | 93.3 | **156.9** | **196.1** |

The impact of replacing the base architecture of Faster R-CNN on the detection accuracy and inference time is depicted in Table 7.11. For this, the time measurements are performed in accordance to Section 5.2.4. All models employing ZynqNet as base network are trained for 40,000 iterations using the training settings introduced in Section 5.1.3. Weights pre-trained on ImageNet are used for initializing the base network. Employing ZynqNet as