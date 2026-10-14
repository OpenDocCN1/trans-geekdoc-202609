
OCT is a non-invasive medical imaging technology that captures high-resolution cross-sectional images of biological tissues using light waves. It is most typically used in ophthalmology to see and analyze the retina and other ocular components, but it is also utilized in cardiology and dermatology. OCT functions based on the principle of interferometry, wherein a light beam is divided into two distinct paths: a reference path and a sample path. The reference beam is directed towards a mirror, while the sample beam is directed towards the tissue being analyzed. Subsequently, light waves originating from both directions engage with the tissue before retracing their path to the apparatus.

In ophthalmology, OCT is particularly valuable for visualizing the retina and identifying various retinal conditions, such as macular degeneration, diabetic retinopathy, and glaucoma. It allows clinicians to assess the thickness, integrity, and pathological changes in retinal layers, aiding in diagnosis, treatment planning, and monitoring of these conditions.

OCT is also used in other medical specialties. In cardiology, it can provide detailed imaging of blood vessels and identify atherosclerotic plaques in coronary arteries. In dermatology, OCT can help visualize and assess skin lesions and guide biopsies. One of the key advantages of OCT is its high-resolution imaging capability, allowing for the visualization of fine tissue structures with micrometer-level precision. However, OCT has certain limitations. It is primarily limited to imaging superficial tissues due to the limited penetration depth of light waves. Medical images taken at a microscopic level are utilized to assess the tissue’s small structure. The biopsy is utilized to retrieve tissue for investigation, and subsequently, staining components are employed to expose cellular features in areas of the tissue. Counter stains are used to give the graphics more color, visibility, and contrast.

## Data augmentation

The enactment of DL neural networks was determined by the handiness of appropriate facts. Facts augmen-tation, which includes removing a set of reasonable alterations to the samples (e.g., flip, rotate, mirror) in addition to augmenting color (grey) values, is the greatest commonly use method for aggregate the extent of the training dataset. The efficiency of data augmentation is examined in non-clinical research, and the outcomes tell that classic augmentation methods can enrich by up to 7% ([Fotenos et al., 2005](#ch36.xhtml#ref36_40); [Golan et al., 2016](#ch36.xhtml#ref36_41); [Milletari et al., 2017](#ch36.xhtml#ref36_42)). When real data is scarce, numerous data augmentation procedures are used to generate more training data from the existing dataset. These augmentation techniques change images while retaining their class, and they can include methods such as – (1) Image translation: This technique involves shifting the pixels of an image along a single direction, either horizontally or vertically, without altering the overall dimensions of the image; (2) Image flipping: Flipping the image pixels horizontally and vertically by retreating the rows and columns of pixels; (3) Picture rotation: Rotation of a picture from 0 to 360 degrees; (4) Contrast adjusting: Changing picture illumination levels to train the procedure to accommodate for such distinctions in test shots; (5) Image zooming: Randomly increase in or out of the picture by adding fresh boundary pixels or using interpolation. Using nearest-neighbor fill, boundary pixel duplication, averaging, or interpolation, few existing pixels are deleted and fresh pixels are included in most of these techniques. The first four solutions are referred to as inflexible data augmentation strategies since the data shape remains unaltered. The fifth method keeps the vertical and horizontal augmentation ratios the same. If it’s not the same, the picture will spread further in a single way than the other (image stretching). The goal of these augmentation techniques is to make deep neural networks more generalizable while avoiding feature under-fitting and over-fitting. These strategies are usually applied mechanically throughout the network’s training phase. An additional resolution is to transfer knowledge from successful models that have been implemented in the same (or even other) industries. In transfer learning the system is trained to recognize and apply understanding educated in a prior origin domain to a fresh assignment. Transfer learning, on the other hand, is influenced by network structure, organ imaging modality, and dataset size ([Perez et al., 2017](#ch36.xhtml#ref36_43)).

## Quantitative analysis

The objective analysis plays a vital role in determining the effectiveness of a segmentation algorithm. The picture segmentation system is evaluated using recognized benchmarks, which allows for comparisons with recently published approaches in the literature. The selection of an appropriate evaluation metric is influenced by various factors, including the specific implementation of the system. These metrics assess different aspects such as accuracy, processing time, memory usage, and computational complexity ([Shie et al., 2015](#ch36.xhtml#ref36_44)). [Table 36.2](#ch36.xhtml#tab36_2) provides definitions for the various abbreviations (TP, FP, FN, and TN) used to assess DL model segmentation performance:

[Table 36.2 DL segmentation performance parameter](#ch36.xhtml#R_tab36_2)

| Category || Actual disease || Actual no disease |
| --- | --- | --- |
| Predicted disease || True positive (TP) || False positive (FP) |
| Predicted No disease || False negative (FN) || True negative (TN) |

### Accuracy

The most basic performance indicator is this one. An alternative term for it is overall pixel precision. The precision is in identifying whether a patient is unwell or healthy.

(2)  

$$Accuracy = \\frac{Correctly\\ Predicted\\ Pixels}{Total\\ No.of\\ Image\\ Pixels} = \\frac{TP + TN}{TP + FP + FN + TN}$$  

### Precision/specificity

Precision denotes the proportion of affected pixels in the automated segmentation output that align with the authentic disease pixels. Precision is a valuable evaluation metric for gauging segmentation performance, particularly in scenarios prone to excessive segmentation. The capacity to accurately measure instances of wellness is referred to as specificity ([Lalkhen et al., 2008](#ch36.xhtml#ref36_45)).

(3)  

$$Precision = \\frac{Correctiy\\ Predicted\\ Disease\\ Pixels}{Total\\ No.of\\ Predicted\\ Disease\\ Pixels} = \\frac{TP}{TP + FP}$$  

### DICE similarity coefficient (DSC)

The DSC surpasses total pixel accuracy as it impartially considers both false alarms and omitted data within each class. DICE is too thought to be better as it measures not just the number of pixels that have been suitably identified, but also the precision with which the segmentation borders have been drawn ([Van et al., 2009](#ch36.xhtml#ref36_46)). Here S stands for segmentations in this case.

(4)  

$$DICE = \\frac{2 \\times TP}{2 \\times TP + FP + FN}$$  

### Sensitivity/recall

Sensitivity refers to the ability to accurately measure disease cases. The fraction of illness pixels in the ground truth which is exactly predicted using programmed segmentation is referred to as sensitivity.

(5)  

$$Sensitivity = \\frac{TP}{TP + FN}$$  

### Jaccard similarity index (JSI)

The percentage of the space of intersection among the anticipated subdivision and the ground fact subdivision to the region of merger among anticipated subdivision and the ground truth subdivision is called JSI (Intersection-Over-Union).

(6)  

$$JSI = \\frac{TP}{TP + FP + FN}$$  

As can be seen from the above, there is a distinction between JSI and DSC.

(7)  

$$JSI = \\frac{DSC}{2 - DSC}DSC = \\frac{2JSI}{1 + JSI}$$  

### Negative predictive value (NPV)
