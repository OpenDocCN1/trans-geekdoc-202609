
## 4.1 Introduction

Gliomas are a category of brain and spinal cord tumors that arise from anomalous division of glial cells [[1](#ch4.xhtml#ref4_1)]. They are known to infiltrate the surrounding tissues which make surgical removal and treatment of these tumors very hard, resulting in a high casualty rate for those afflicted by these tumors. These tumors can be malignant or benign. `WHO` (World Health Organization) has a segregation system that classifies these tumors with a `I—IV` grading system with `IV` representing the most aggressive form [[2](#ch4.xhtml#ref4_2)]. Gliomas are classified depending on the specific type of brain cell that is affected. By introducing the computerized tomography (`CT`) and magnetic resonance imaging (`MRI`) techniques, the brain tumor incidence rates have been relatively stable.

Despite numerous developments in glioma research, the patient diagnoses are very poor. More aggressive form of the disease is being considered as high-grade, which require immediate treatment. They have median survival rate of less than two years. The low-grade variants, which are slow-growing, *viz.,* low-grade astrocytomas or oligodendrogliomas, have relatively higher life expectancy, which allows the delay of overly aggressive treatment methods as they can cause serious tissue damage. Less than 3% of glioblastoma patients are still alive at 5 years after diagnosis [[3](#ch4.xhtml#ref4_3)]. Early detection of the brain tumor is crucial and has been the crux for a lot of research.

Neuroimaging is one of the important tools for diagnosis, treatment planning, and post-therapy assessment of any brain tumors. Radiology has played an integral role in this process and a lot of progress has been made in this field to involve accurate diagnosis, non-invasively and assessing the therapeutic response [[4](#ch4.xhtml#ref4_4)]. The brain tumor segmentation helps in separating the tumor from the normal brain cells, which will provide the information for diagnosis and planning can be emphasized for treatment.

The magnetic resonance imaging (`MRI`) techniques have been conventionally employed in modern neuroimaging for its superior characterization of structure and its ability to capture various cellular and metabolic functions [[5](#ch4.xhtml#ref4_5)], [[6](#ch4.xhtml#ref4_6)], [[7](#ch4.xhtml#ref4_7)]. The standardized neuroimaging protocol includes, three-dimensional (`3D`) `Ti`, axial fluid-attenuated inversion recovery (`FLAIR`), axial diffusion-weighted imaging (`DWI`), axial gadolinium contrast-enhanced `T2` and `3D` gadolinium contrast-enhanced `Ti`. `MRI` offers a higher contrast based image which enables better visualization and segmentation which is why these images have been employed in most segmentation algorithms. Accurate segmentation is vital to glioma study and diagnosis. Manual segmentation is a labor inductive method that is prone to misinterpretation and variability. Deep learning systems have been exploited by physicians to aid in offering second opinions and flagging regions of interest (`ROIs`) in images [[8](#ch4.xhtml#ref4_8)]. Automatic segmentation using `3D CNN` (convolutional neural networks) has shown high efficiency in capturing multi-scale contextual information from the images [[9](#ch4.xhtml#ref4_9)]. The process involves the hierarchical segmentation of the entire tumor structure, core region, and enhanced tumor structures.

Convolutional neural networks (`CNNs`) are deep learning algorithms designed to process the data of natural spatial invariance. In `CNN`, the receptive field of a node is the region of the input signal that is involved in the multilayer convolution up to that node in a forward pass [[10](#ch4.xhtml#ref4_10)], [[11](#ch4.xhtml#ref4_11)]. The composition of a typical segmentation architecture is as follows:

1.  **Downsampling path**, which is responsible for extracting coarse semantic features
2.  **Upsampling path** trained to recover the input image resolution at the output of the model and optionally
3.  **Post-processing module** for the refinement of the model predictions.

Densely connected convolutional networks or `DenseNets` have produced great outputs when utilized for image classification tasks [[12](#ch4.xhtml#ref4_12)]. `DenseNets` are based on directly connecting each and every layer to the other layer in feed-forward fashion to make the network more accurate and increase the ease of training the network. They are built using pooling operations and dense blocks where every block is one of the iterative concatenations of previous feature maps. This architecture is an extension of residual networks (`ResNets`) and designed for additional uses such as the following:

1.  **Parameter efficiency**: `DenseNets` use the parameters more efficiently
2.  **Deep supervision**: `DenseNets` perform deep supervision using the short paths in the architecture
3.  **Feature reuse**: The current layer under study utilizes the previous layer information with computed feature maps. These attributes make them a good fit for the semantic segmentation.

The output of the "`l`th" layer, `x[1]` is computed by applying nonlinear transformation, `H` to the output of the previous layer, and `x[l-1]` in a standard `CNN`. `H` is defined as convolution followed by rectified non-linear function (`ReLU`) and a dropout. The output is calculated as `x = H[1](x[1] - 1)`.

`DenseNets` integrate a pattern with more connectivity with all feature outputs in a feed-forward fashion. In this case, the output of the "`l`th" layer is given by `x[1] = H[1]([x[l-1], x[l-2], ..., x[0]])`, where the concatenation operation is represented. Here, reuse of the features will occur and all layers of the architecture receive supervision signals. For each layer, the output dimension has `k` feature maps where `k` is the growth rate parameter and `k` is typically set to a small value. Hence, the number of feature maps in `DenseNets` grows linearly with the depth.

This makes the `DenseNet` architecture suitable for efficient and accurate segmentation of the images while preserving the essential edge details. As per the segmentation performed, the neural network is to segregate the images into low grade gliomas. This gives a measure of the severity of the gliomas in accordance with the `WHO` classification of gliomas.

## 4.2 Aim

This study aims to tackle the automation of the segmentation of large amounts of `MRI` data produced while imaging low grade and high grade gliomas, using `DenseNet` architecture. We endeavor to aid in gliomal treatment at the diagnostic level, addressing the crucial task of accurate and efficient segmentation and gradation of gliomal tumors. More precise segmentation of brain tumors that resulted from `MRI` images reveals crucial and challenging tasks in diagnosis and planning for tumor treatment. Along the boundaries of tumors, it is still a challenging task because of the irregularities. Advancements in this area of research are the use of convolutional neural networks (`CNNs`). We take on the essential task of improving classification accuracy by extracting more efficient features while using minimal training data. There is still a lot of room for additional research to implement various machine learning techniques and modify them to specifically address the requirements of tumor diagnosis. These techniques should also satisfy the criteria of generic application in order for them to have utility in the medical field and satisfy general requirements of patient—doctor use.

## 4.3 Objectives

*   Building a `DenseNet` architecture for `MRI` image segmentation
*   Neural network training for segmentation of brain tumor
*   Testing the trained neural network to obtain segmented images
*   Classification of tumors as high grade (`HGG`) or low grade gliomas (`LGG`)

## 4.4 Methodology

*   The `MRI` images obtained using the `BRaTS` dataset are pre-processed and are used for training and testing of the neural network.
