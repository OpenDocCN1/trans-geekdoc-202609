
coding for these transformations, like adding noise, cropping, flipping, rotation, scaling, translation, brightness, contrast, color augmentation, saturation, adversarial training, neural style transfer, and generative adversarial networks-based augmentation (Fig. 2) [19].

![](img/12e321fe66dd89993b17a8d73b64bd0c_251_0.png)

Fig. (2). Example of three simple data augmentation operations (rotation, shearing and scaling).

## Image Fusion

Image Fusion encompasses all data analysis strategies, displayed in Fig. (3), aimed at combining information from multiple images obtained with the same or different spectroscopic platforms [20]. IF combines two or more registered images of the same object into a single image that is more easily interpreted than any of the originals [21]. The motivation for Medical Image fusion from different modalities is to obtain a high-quality image by intelligently combining the collected essential information from multi-modal input images [22]. IF techniques shown in figure can be classified as spatial and frequency domains.

![](img/12e321fe66dd89993b17a8d73b64bd0c_252_0.png)

Fig. (3). Different image fusion techniques [20].

## Related Work

Several contributions have been proposed to address the topic of tumor classification using several classical and advanced techniques [23 - 31]. It should be noted that the most modern techniques use DL to treat this subject. For example, the authors of [23] proposed to use CNNs for BT classification via the transfer learning (TL) technique. The anticipated method reports a mean classification accuracy of 98%, outperforming all related work. The manuscript focuses on a 3-class BT to adopt the concept of deep TL using GoogLeNet [32] to extract features from MRI.

A decision support system for multimodal BT using DL is proposed by Sharif et al. [24]. For the experimental process, the authors used two datasets, BRATS2018, and BRATS2019, and achieved an accuracy of more than 95%.

Mohsen et al. [25] proposed a CNN to classify the BT into three classes (glioma, meningioma, and pituitary) with an accuracy of 98.93% and a sensitivity of 98.18% for cropped lesions, while the results for uncropped lesions are 99% accuracy and 98.52% sensitivity and the results for segmented lesion images are 97.62% for accuracy and 97.40% sensitivity.

Saleh et al. [26] used CNN combined with discrete wavelet transform (DWT), and principal component analysis, to classify 66 brain MRIs into 4 classes: normal, glioblastoma, sarcoma, and metastatic bronchogenic carcinoma tumors, as well as the performance evaluation, was relatively good for all performance measures.

To bring more scientific value to state of the art, we present an approach that uses data augmentation with fusion techniques for brain tumor classification using deep learning and autoencoder.

## METHODOLOGY

Using a relatively small dataset that we constructed in our L2M3S lab consisting of 24*10 = 240 images representing 10 classes of BT, we began our three-step approach shown in Fig. (4).

![](img/12e321fe66dd89993b17a8d73b64bd0c_253_0.png)

Fig. (4). The proposed methodology consists of three steps: classification without data augmentation, classification with classical data augmentation techniques and classification with data augmentation using fusion techniques.

### Dataset

The dataset in Fig. (5) consists of two types of images (test and training), each type consisting of 10 classes (aneurysm, multiple sclerosis, hydrocephalus, stroke, infections, cysts, swelling, hemorrhage, bleeding, inflammation). For the training images, we have 24 images for each class, and for the test images, we have 8 images for each class.

![](img/12e321fe66dd89993b17a8d73b64bd0c_254_0.png)

Fig. (5). Extracted from the dataset used.

### Deep Learning Approach with Classical Data Augmentation

We used Google Colab to take advantage of the computational power of google; we started by loading our dataset and preprocessing the images. After that, we find out the average dimensions of images, as shown in Fig. (6).

![](img/12e321fe66dd89993b17a8d73b64bd0c_254_1.png)

Fig. (6). The average dimensions of brain-tumor.

### Data Pre-Processing for the Model

There is too much data for us to load all of them into memory. We are able to use some Keras functions (we used ImageDataGenerator to do this automatically) to automatically process the data, generate a batch data stream from a directory and also manipulate the images. It is usually a good idea to manipulate the images with some simple parameters (Table 1), like rotation, resizing and scaling, so that the model becomes more robust to the different images that our dataset does not have, as the image in Fig. (7).

Table 1. Configuration of the data augmentation generator.

| Parameter | Value | Description |
|---|---|---|
| Rotation_range | 20 | Rotate the image 20 degrees |
| Width_shift_range | 0.10 | Shift the pic width by a max of 5% |
| Height_shift_range | 0.10 | Shift the pic height by a max of 5% |
| Rescale | 1/255 | Rescale the image by normalizing it |
| Shear_range | 0.1 | Shear means cutting away part of the image (max 10%) |
| Zoom_range | 0.1 | Zoom in by 10% max |
| Horizontal_flip | True | Allow horizontal flipping |
| Fill_mode | nearest | Fill in missing pixels with the nearest filled value |

![](img/12e321fe66dd89993b17a8d73b64bd0c_255_0.png)

Fig. (7). Example of automatic generation of an image.

### Generation of many Manipulated Images from a Directory

To use flow_from_directory, we organized the images into subdirectories. This is an absolute requirement, otherwise, the method will not work. The directories should only contain images of one class, like in Fig. (8), so one folder per image class.

![](img/12e321fe66dd89993b17a8d73b64bd0c_256_0.png)

Fig. (8). Organization of the data set into a training database and a test database.

### Design of the Model Architecture

For visual learning and image recognition, the CNN model, like in Fig. (9), is the most common and widely used machine learning algorithm.

![](img/12e321fe66dd89993b17a8d73b64bd0c_256_1.png)

Fig. (9). General architecture of a convolution neural network.

### Convolution Layer

The convolution layer is the key component of CNN, and is always at least its first layer. Its objective is to identify the presence of a set of features in the images received as input. To do this, we perform convolution filtering: the principle is to “drag” a window representing the feature on the image, and to compute the convolution product between the feature and each portion of the scanned image. A feature is then seen as a filter: the two terms are equivalent in this context.

### Pooling Layer

This is a subsampling operation typically applied after a convolutional layer. In particular, the most popular types of pooling are max and average pooling, where the maximum and average values are taken, respectively. Max-Pooling is a sample-based discretization process. Its objective is to subsample an input representation (image, hidden layer output matrix, etc.) by reducing its dimension. Moreover, its interest is that it reduces the computational cost by reducing the number of parameters to be learned and provides invariance by small translations (if a small translation does not modify the maximum of the scanned region, the maximum of each region will remain the same and thus the new matrix created will remain identical).

### Flatten Layer

The Flatten layer provides a connection between the convolution layers and the base layers of Deep Learning. It allows diffusing the data through the layers by reducing its dimension. The data finally reaches a prediction layer, such as the Dense layer, which provides the label detected by the Deep Learning model.

### Dense Layer

A Dense layer which is a classical neural layer, completely connected with the previous and the next layer. A dense output layer with one neuron per class, and a “softmax” activation function that gives an output probability for each neuron, with the output neuron with the highest probability then deciding that its associated class is the predicted class. Fig. (10) shows the architecture of the model used.

### Learning and Same Parameters

In classification tasks, it would be useful to have all outputs fall between 0 and 1. These values can then present probability assignments for each class. There are 2 main types of multi-class situations: non-exclusive and mutually exclusive Classes. We used a configuration for the case of a 10-class exclusive classification problem whose code is presented in Table 2.
