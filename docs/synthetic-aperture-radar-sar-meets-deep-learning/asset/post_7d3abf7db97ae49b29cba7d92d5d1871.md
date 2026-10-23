
where σ is the sigmoid function. Then, g^h and g^w are used in the position-enhanced attention block:

$$y_c(i,j) = x_c(i,j) \times g_c^h(i) \times g_c^w(j) \tag{8}$$

Position-enhanced attention considers the encoding of spatial information. As mentioned above, attention along both horizontal and vertical directions applies to the input tensor. This coding process allows position-enhanced attention to more accurately locate the target position in the image, thus helping the whole model to achieve better recognition. Experiments show that our method does achieve good results.

## 4. Experiments

To verify the proposed method, we conducted a series of related experiments to evaluate the model’s detection performance. The content of this section includes details of some settings in the experiment and the main content of the SSDD dataset, followed by the evaluation indicators used in the experimental results, the influence of each module proposed in the ablation experiment on the model and a comparison with other target detection algorithms. Finally, LPEDet is compared with other recent SAR imaging methods.

### 4.1. Dataset and Experimental Settings

In our experiment, the datasets used were SSDD [34] and HRSID. For each ship, the detection algorithm predicts the frame of the ship target and gives the confidence of the ship target. The SSDD process is based on the PASCALVOC dataset and its data format is algorithmically compatible, making it easier to use with fewer code changes.

SSDD data are obtained by downloading public SAR images from the internet. Figure 5 shows part of the images in the dataset. The target area was cropped to approximately 500 × 500 pixels and the ship target location was manually marked. As long as there is a ship in the dataset, there are no requirements regarding ship type. The data in this dataset mainly include HH, HV, VV and VH polarization modes. There are 1160 images in the dataset and each image contains 2456 ships of different numbers and sizes. Although SSDD has few pictures, for the detection network, the number of targets that only recognize ships is sufficient. The corresponding relationship between the number of pictures and the number of ships in the dataset is shown in Table 2.

![](img/828a5d28a36454f7b3332df93f35492f_257_0.png)

Figure 5. Illustration of the diversity of ship targets in the SSDD dataset.

Table 2. Correspondence between NoS and NoI in the SSDD dataset.

| NoS | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 |
| NoI | 725 | 183 | 89 | 47 | 45 | 16 | 15 | 8 | 4 | 11 | 5 | 3 | 3 | 0 |

NoS = number of ships; NoI = number of images.

In addition, to verify the detection performance of our proposed method in different scenarios, we introduced another large-scale SAR target detection dataset, namely, the HRSID dataset. The images in this dataset are high-resolution SAR images, which are mainly used for ship detection, semantic segmentation and instance segmentation tasks. The dataset contains a total of 5604 high-resolution SAR images and 16,951 ship instances. The HRSID dataset borrows from the construction process of the Microsoft Common Objects in Context (COCO) dataset, including SAR images with different resolutions, polarizations, sea states, sea areas and coastal ports. For HRSID, the resolutions of the SAR images are: 0.5 m, 1 m and 3 m, respectively.

To make a fair comparison with previous work, we attempted to use the same settings that previous workers used. We randomly divided the original SSDD dataset according to the ratio of 8:2 commonly used in existing studies and 80% of the datasets were used for the training of all methods. The remaining 20% was used as a test set to evaluate the detection performance of all methods. The data in the training set and test set were not repeated at all among the methods to ensure the rigor and fairness of the experiment. Other parameters included a batch size of 8 and an image size for the input model of 640, RandomHorizontalFlip was adopted, ColorJitter and multiscale were used for data augmentation, and Mosaic and MixUp enhancement strategies were employed. Using the lr×batchsize/64 learning rate, the cosine lr schedule and initial lr = 0.01 were employed. The weight decayed to 0.0005 and the SGD momentum was 0.9. A total of 600 epochs were trained. In the HRSID [35] dataset, we used a ratio of 6.5:3.5 to split the dataset, with 65% data for training and 35% for testing, the same as the original author split. The image size of the input model was 800. All experiments in this paper were carried out on an Ubuntu 18.04 operating system equipped with a GeForce RTX2060.

### 4.2. Evaluation Indicators

We used average precision (mAP) to analyze and verify the detection performance of our proposed method. Average accuracy can be derived from accuracy and recall.

Accuracy is the percentage of targets that are correctly identified in the test set. The percentage is defined by true positives (TPs) and false positives (FPs):

$P = \frac{TP}{TP + FP}$ (9)

TP means that the prediction of the classifier is positive and the prediction is correct; FP indicates that the prediction of the classifier is positive and the prediction is incorrect.

The recall rate is the probability that all positive samples in the test set are correctly identified, which is derived from true positives (TPs) and false negatives (FNs):

$R = \frac{TP}{TP + FN}$ (10)

FN indicates that the prediction of the classifier is negative and the prediction is incorrect.

Based on the accuracy and recall rate, an average accuracy value is also obtained. The graphical meaning can be clearly seen in the coordinate axis, that is, the area under the accuracy and recall rate curve, which is defined as follows:

$\text{mAP} = \int_{0}^{1} P(R) dR$ (11)

### 4.3. Experimental Results and Analysis

### 4.3.1. Ablation Experiments on SSDD Datasets

To clearly compare the advantages of the added modules, we conducted the following ablation experiments. The first experiment ensured that other settings remained unchanged while replacing the backbone network Darknet-53 with a lightweight backbone NLCNet. Second, the attention module position-enhanced attention was added on the basis of the original network. This process did not change other settings and parameters.

It should be noted that the methods in the ablation experiment were reproduced according to the official open-source code of the comparison method and applied to the SSDD dataset for experimental comparison. The dataset used by the comparison method was exactly the same as that used by our proposed method; the hyperparameters of the comparison method were all set with standard default settings and the number of training epochs was also consistent with our method.

Influence of the NLCNet Backbone Network on the Experimental Results

The backbone Darknet-53 was replaced with our proposed NLCNet based on YOLOX, as previously shown in Figure 2. The mAP increased by 0.6% from 96.2% to 96.8% and the FLOPs dropped by 8.37 from 26.64 to 18.27. According to the data, our redesigned NLCNet showed advantages in feature extraction with respect to SAR image ship targets, not only improving accuracy but also reducing the number of parameters, making the model more lightweight and easier to transplant in industrial settings.

Influence of Position-Enhanced Attention on Experimental Results

To verify the effectiveness of our proposed position-enhanced attention and its advantages, we conducted ablation experiments with the original network without attention, the network with coordinate attention and the new network with our proposed position-enhanced attention in our dataset, respectively. The experimental results are shown in Table 3. The mAP of the network with our proposed position-enhanced attention was greatly improved compared to the network without attention, which increased from 96.8% to 97.4%. At the same time, the increase in FLOPs and params was negligible. The results show the effectiveness of our proposed position-enhanced attention. Compared with the original network with coordinate attention, the detection accuracy of our proposed model increased from 97.1% to 97.4% with the parameters and FLOPs unchanged. It should be noted that we kept two significant digits after the decimal point when we counted the experimental results. Therefore, it was calculated that the parameters of FLOPs and params of our position-enhanced attention model and the original coordinate attention model were the same size. Thus, the advantages of our designed positional attention are demonstrated by the results. The visualization results are shown in Figure 6.

Table 3. Results of ablation experiments. (mAP, FLOPs, Params and average inference time represent detection accuracy, computational complexity, parameter amount and average inference time, respectively).

| Model | Backbone | Attention | mAP (%) | FLOPs (GMac) | Params (M) | Average Inference Time (ms) |
|---|---|---|---|---|---|---|
| YOLOX | Darknet-53 | - | 96.2 | 26.64 | 8.94 | 8.20 |
| YOLOX | NLCNet | - | 96.8 | 18.27 | 5.58 | 5.27 |
| YOLOX | NLCNet | Coordinate attention | 97.1 | 18.38 | 5.68 | 7.01 |
| YOLOX | NLCNet | Position-enhanced attention | 97.4 | 18.38 | 5.68 | 7.01 |

### 4.3.2. Comparison with the Latest Target Detection Methods Using SSDD Datasets

To further demonstrate the validity of our work, we compared LPEDet with some of the latest target detection methods, including the one-stage RetinaNet, SSD300, YOLOv3, YOLOX, YOLOv5, AFSar, two-stage Faster R-CNN, Cascade R-CNN, FPN and anchor-free CornerNet, CenterNet and FCOS methods. Among them, considering that our model
