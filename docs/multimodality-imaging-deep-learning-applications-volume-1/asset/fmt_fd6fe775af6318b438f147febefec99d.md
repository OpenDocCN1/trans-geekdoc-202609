
Feature mining in ML based algorithms for 3D images is complicated, since the system tries to capture features/parameters in 3D translation, orientation, and anisotropic scale. Therefore, the ultimate search space of feature mining is 9D, which is difficult considering contemporary models. In this respect, a marginal space deep learning model (MSDLM) was proposed \[[43](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib43)\] that is capable of incrementally learning features and thereby determine the shape of the LV contour. The MSDLM consists of two stages, whereby in the first stage of the model the ROI is detected and in the second stage the LV boundary is delineated. The localization of the ROI is performed using DL based classifiers (DLCs). The DLC learns the position, orientation, and scale of the LV contour iteratively, by maximizing the probability of locality of the LV by using translation, orientation, and scale space. It is specified as

``` 
$$\\left( \\hat{\\overset{\\rightarrow}{\\mathbf{T}},\\ }\\hat{\\overset{\\rightarrow}{\\mathbf{R}}},\\ \\hat{\\overset{\\rightarrow}{\\mathbf{S}}} \\right) = {\\arg\\ }\\max\_{\\overset{\\rightarrow}{\\mathbf{T}},\\overset{\\rightarrow}{\\mathit{R}},\\overset{\\rightarrow}{\\mathbf{S}}}\\left( {\\overset{\\rightarrow}{\\mathbf{T}},\\overset{\\rightarrow}{\\mathbf{R}},\\overset{\\rightarrow}{\\mathbf{S}} \\mid \\mathbf{I}} \\right),$$  

(2.13)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch2eqn45.gif" position="float"/

where *T* represents the translation, *R* denotes the orientation, and *S* signifies the scale space. Three DLCs were trained to predict the position, orientation, and space of the LV. The first DLC estimates the position, the second DLC estimates the orientation by taking input from the first, and the third DLC estimates scale by taking input from the first and second. In the second stage, an active shape model based on deep learning is applied for LV shape deformation. To prevent overfitting, dropout is employed. The dataset is 2891 3D volumes taken from 869 patients. The proposed DL based MSDLM model performed comparatively better than the earlier conventional system employing the same methodology but without the DL component. The comparative results are displayed in table [2.1](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2t1). The corresponding process model and resulting images are displayed in figures [2.12](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig12) and [2.13](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig13), respectively.

**Table 2.1.** Comparison of the MSDLM and the conventional MSM model.

| Accuracy parameters || DL based MSDLM || Conventional MSM |

| --- | --- | --- |

| Position error || 1.47 mm || 3.12 mm |

| --- | --- | --- |

| Corner error || 2.80 mm || 0.42 m |

![Figure 2.12. Deep classifier based 3D LV segmentation model.](images/bk978-0-7503-2244-7ch2f12_online.jpg)

**Figure 2.12.** Deep classifier based 3D LV segmentation model.

![Figure 2.13. Deep classifier based 3D LV segmentation model outputs. The auto-detected bounding box is shown in green while the ground truth bounding box is shown in yellow. (Reproduced with permission from \[43\]. Copyright 2016 IEEE.)](images/bk978-0-7503-2244-7ch2f13_online.jpg)

**Figure 2.13.** Deep classifier based 3D LV segmentation model outputs. The auto-detected bounding box is shown in green while the ground truth bounding box is shown in yellow. (Reproduced with permission from \[[43](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib43)\]. Copyright 2016 IEEE.)

##### 2.3.1.4 Vessel mining from x-ray angiograms

Globally, cardiovascular diseases (CVDs) kill more than 17 million people annually. Coronary artery disease is one of the main CVDs and a leading cause of death (figure [2.14](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig14)). Traditional methods, i.e. tracking and filter based methods, are unable to provide better accuracy due to low resolution, the presence of noise, and similar echogenic organs near the ROI increasing complexity. A DL based CNN model was used for detecting vessel regions from x-ray angiography images \[[44](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib44)\]. In this experiment, 44 images were collected. The images were pre-processed to increase the contrast using the top-hat transform. A patching based method was applied, where 1 040 000 patches were mined for training and testing the CNN. The CNN (two convolutions + two max-pooling + two fully connected layers (500)) generated the probabilities for the two classes vessel and not-vessel. The CNN model generated a high accuracy of 93.5% which was comparatively better than previous methods. Moreover, the better results were generated despite the presence of noise, low-resolution, and complex backgrounds. However, the CNN model used was only six layers deep and, therefore, the dataset should be trained/tested on a deeper model for better results, reliability, and clinical use. The segmentation results are displayed in figure [2.15](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig15).

![Figure 2.14. Segmentation of x-ray images using CNNs.](images/bk978-0-7503-2244-7ch2f14_online.jpg)

**Figure 2.14.** Segmentation of x-ray images using CNNs.

![Figure 2.15. Row one shows five input images. Row two shows the corresponding ground truth of the row one images. Row three shows analogous images for segmentation outputs using CNN. (Reproduced with permission from \[44\]. Copyright 2016 IEEE.)](images/bk978-0-7503-2244-7ch2f15_online.jpg)

**Figure 2.15.** Row one shows five input images. Row two shows the corresponding ground truth of the row one images. Row three shows analogous images for segmentation outputs using CNN. (Reproduced with permission from \[[44](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib44)\]. Copyright 2016 IEEE.)

##### 2.3.1.5 Plaque characterization

Vulnerable plaque identification is an important element of CVD detection and can be helpful in early risk assessment and preparation of a treatment plan. However, there are several challenges in plaque detection owing to its small size, complex multifocal appearance, and the presence of speckle noise, making segmentation difficult and the characterization of plaque thus constituents a complicated task. In this regard, an automated DL based CNN model was proposed for plaque characterization \[[45](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib45)\]. The CNN model (four convolution layers + four ReLu + three fully connected layers) used the softmax classification technique. The cross-entropy loss function was used for training and the results of the proposed model were compared to single-scale and multi-scale support vector machines (SVMs).

For the experiment, 56 ultrasound CCA images were used. A patch based strategy was followed. Therefore, 90 000 patches were mined from the ultrasound images. They were annotated into three categories, lipid core, fibrous, and calcified, which were used as the ground truth for CNN model learning. The comparative results of the DL model and the other conventional ML model are listed in table [2.2](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2t2), which shows that the DL based model outperformed the ML based models by a huge margin. The process of the model and the segmentation results are displayed in figures [2.16](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig16) and [2.17](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig17), respectively.

**Table 2.2.** Comparison of the DL and conventional models for plaque characterization \[[45](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib45)\].

| Model || Accuracy |

| --- | --- |

| DL based CNN || 78.5% |

| --- | --- |

| Single-scale SVM || 14.3% |

| Multi-scale SVM || 7.2% |

![Figure 2.16. Global diagram for plaque characterization.](images/bk978-0-7503-2244-7ch2f16_online.jpg)

**Figure 2.16.** Global diagram for plaque characterization.
