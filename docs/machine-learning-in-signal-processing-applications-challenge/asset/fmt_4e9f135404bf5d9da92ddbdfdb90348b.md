
### Image Preprocessing
As the images are acquired from the real field, they may contain dust, spores, and water spots as noise. The purpose of data preprocessing is to eliminate the noise in the image, so as to adjust the pixel values. It enhances the quality of the image. In this model, we trained the plant leaf images of tomato, potato, and corn with diseases of 38 classes samples are ([Figure 9.1](#ch09.xhtml#f9_1)):

### Image Segmentation
Image segmentation is the third step in our proposed method. The segmented images are categorized into color and area affected of leaf.

### Feature Extraction
Feature extraction is the important part to gracefully predict the infected region. Here, shape and textural feature extraction is done. The shape-oriented features of extraction like area, color axis length, eccentricity, solidity, and perimeter are calculated. Similarly, the texture-oriented features of extraction like contrast, correlation, energy, homogeneity, and mean are calculated. Leaf image is captured and processed to determine the health of each plan. The initial process is to select the image. By using the image preprocessing technique, the leaf has to be diagnosed whether it was affected or unaffected. Then, the image has to be segmented, and the name of the disease has to be identified. This project provides a solution to overcome from the leaf diseases, and it also analyzes the overall percentage of the affected leaf and its surrounding region.

![FIGURE 9.1 (a) SquashMildew, (b) Corn_blight, and (c) PotatoEarly disease category images.](images/Fig09_01.jpg)

[**FIGURE 9.1**](#ch09.xhtml#f9_1b) (a) SquashMildew, (b) Corn_blight, and (c) PotatoEarly disease category images.

The below section describes the most common preprocessing operations used for accurate tumor classification

| Methods || Range |
| --- | --- |
| Flip horizontally || 0.5 |
| --- | --- |
| Flip vertically || 0.5 |
| Rotation || 15° |
| Shift || 0.05 (in horizontal & vertical direction) |
| Shear || 0.05 (in horizontal direction) |

### 9.4.3 Classification Algorithms with Applications
Deep learning-based classification algorithms are very useful in health care domain. Anjanadevi B and N S Akhil [[22](#ch09.xhtml#r9_22)] proposed a model in health care domain which describes the techniques in classification to build a `CNN` model that would classify the tumor and nontumor images. This model is effective and accurate in classifying if the images are tumor type or not. Patel et al. presented a deep learning-based price prediction model for cryptocurrency. This model obtains high accuracy in the prediction of cryptocurrency price. Bondalapati et al. [[25](#ch09.xhtml#r9_25)] proposed an effective unified moving object detection model in real-time video surveillance systems which handles challenging conditions such as camera jitter, dynamic background, and shadow appearance of images. This project is the combination of classification and segmentation. Mainly, `VGG16` and `Mobile Net` are recent methodologies used to categorize the insulator images which are captured through drone cameras, Anjanadevi et al. [[26](#ch09.xhtml#r9_26)] proposed a lightweight deep learning-based classification model to classify the insulators’ working condition weather they are working good or not. This model consumes less time compared to the brain tumor classification model found in Anjanadevi et al. which classified the tumor (yes) and nontumor (No) images, and later segmentation is applied on the tumor (yes) images. We implemented a classification model with eight convolution layers and five pooling layers with three fully convolution layers as a base model. Furthermore, to improve the accuracy along with base model, we proposed the transfer learning technique with one `dropout` layer with 0.5 value and extended to `dense` layer with `sigmoid` function. This model achieves high accuracy in classifying images having tumor or not. The following section describes about various deep learning models.

## 9.5 Lightweight Deep Convolution Neural Network Architecture (`LW-DCNN`)

### 9.5.1 Introduction
Deep convolution neural networks (`DCNNs`) have a good breakthrough in processing images while reducing computational cost and increasing accuracy. The proposed approach focuses on object detection using classification with the `DCNN` model. This model uses feature map for preprocessing the images, and convolution layers help to minimize the processing using deep learning perceptrons. After that, the proposed approach uses the lightweight deep convolution neural network (`LW_DCNN`) model which includes a smaller number of convolution layers, max pooling layers with relevant parameters, and dense, flattened layers to train the data using `Leaky ReLU` function for improving accuracy. The proposed methodology `LW_DCNN` is highly efficient compared to traditional classification techniques and present simple and powerful model for object detection in video surveillance systems.

#### Algorithm (Lightweight DCNN Classification Model (`LW_DCNN`))
Input images considered in target size `251 * 250 * 3` hold raw pixel values of the image (width, height, and channels) as `(251, 250, 3)`.

The applied `Convolution2D` with kernel `(3 × 3)` and 64 filters are used to compute the feature map with local regions in the input image, and `ReLu` activation function is used with a dot product between their weights, and local regions that are connected to input volume produce the output shape `(118, 118, 32)`.

Max pooling with pool size `2 × 2` with padding `= 1` produces output shape `(59, 59, 32)`.

`Convolution2D` with 32 filters with `ReLU` produces `(57,57,32)`, and max pooling with same padding produces `(28, 28, 32)`.

Repeating step 4 and applying layers produce output shape `(13, 13, 32)`.

Finally, flattened and dense layers used in the network for handling data into vectors achieved an accuracy of 0.8154. [Figure 9.2](#ch09.xhtml#f9_2) describes the overall system process step by step. This customized algorithm effectively classifies the working condition of insulators on electric polls. This algorithm is emerging in usage in current real-time surveillance systems. Through drone cameras or surveillance cameras, we can collect the large set of images of insulators from electric polls, and through this, we can automatically classify the working condition (either good or bad) of insulators without manual check.

![FIGURE 9.2 Proposed LW_DCNN model.](images/Fig09_02.jpg)

[**FIGURE 9.2**](#ch09.xhtml#f9_2b) Proposed `LW_DCNN` model.

### 9.5.2 Architecture
