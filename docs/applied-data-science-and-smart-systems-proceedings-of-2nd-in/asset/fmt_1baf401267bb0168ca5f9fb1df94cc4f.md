
A total of 356 .jiff images illustrating instances of pink eye were amassed for analysis. It is important to mention that a small subset of these images was considered unsuitable and was manually excluded from the dataset, which ends up with the 265 number of images. Furthermore, an independent set of 130 .jpg images featuring healthy eyes (`[Singh et al., 2019](#ch13.xhtml#ref13_11)`) was obtained for the purpose of comparison, as shown in `[Figure 13.4](#ch13.xhtml#fig13_4)`.

![Figure 13.4 Number of images in the dataset](images/fig13_4_C.jpg)

[Figure 13.4 Number of images in the dataset](#ch13.xhtml#R_fig13_4)

### B. Data pre-processing

The eye data collected are of different sizes which can hamper the performance of the system, hence their size have been reduced to (`224×224`), as shown in `[Figure 13.5](#ch13.xhtml#fig13_5)`.

![Figure 13.5 Resized dimension of images](images/fig13_5_C.jpg)

[Figure 13.5 Resized dimension of images](#ch13.xhtml#R_fig13_5)

Later, the quality of the resized images have been enhanced and the process starts with individual `histogram equalization` on each color channel (blue, green, and red) to enhance contrast by spreading pixel intensity distribution. This enriches visual appeal, making dark and light areas distinct. Following this, `unsharp masking` is applied. A blurred version of the enhanced image is subtracted from the original, emphasizing high-frequency components like edges and details. These components are then blended back into the image, sharpening it and highlighting features. This blend of techniques enhances contrast and sharpness, resulting in an image with heightened visual appeal and clear details. The approach is demonstrated by showcasing the original and enhanced images, as shown in `[Figure 13.6](#ch13.xhtml#fig13_6)`.

![Figure 13.6 Enhanced eye images](images/fig13_6_C.jpg)

[Figure 13.6 Enhanced eye images](#ch13.xhtml#R_fig13_6)

### C. Data augmentation

It involves applying transformations to the original images to diversify the dataset and improve model training. Here, `ImageDataGenerator()` has been used to perform rotation (within a range of -50 to +50 degrees), horizontal flipping, and vertical flipping generating 12 augmented images of single image (4 augmented images each simulating different angles from which the eye might be captured). Hence, in total we have 1690 healthy images and 3445 pink eye images. This augmented dataset aids learning models in learning from a wider range of image variations, leading to better generalization and performance. `[Figure 13.7](#ch13.xhtml#fig13_7)` presents the main augmented images.

![Figure 13.7 Augmented images. (a) Healthy eye. (b) Pink eye](images/fig13_7_C.jpg)

[Figure 13.7 Augmented images. (a) Healthy eye. (b) Pink eye](#ch13.xhtml#R_fig13_7)

### D. Cnn

Convolutional neural networks (CNNs) are a specialized type of deep learning model designed for processing visual data like images. They consist of layers that automatically learn and extract features from images. The core components are convolutional layers, which detect patterns in the input image, and pooling layers, which downsample the data, as shown in `[Figure 13.8](#ch13.xhtml#fig13_8)` (`Kumar, 2023`).

![Figure 13.8 Architecture of CNN model](images/fig13_8_C.jpg)

[Figure 13.8 Architecture of CNN model](#ch13.xhtml#R_fig13_8)

[Table 13.1](#ch13.xhtml#tab13_1) represents the layered architecture of a CNN model. Each row corresponds to a layer in the network, and provides information about the layer type, output shape, and the number of parameters (or weights) in each layer.

[Table 13.1 Layered architecture of proposed CNN model](#ch13.xhtml#R_tab13_1)

| Layer || Output shape || Param # |
| --- | --- | --- |
| `Conv2d` || (None, 222,222,32) || 896 |
| `Max_pooling2d` || (None,111,111,32) || 0 |
| `Conv2d_1` || (None,109,109,64) || 18496 |
| `Max_pooling2d_1` || (None, 54,54,64) || 0 |
| `Conv2d_2` || (none, 52,52,128) || 73856 |
| `Max_pooling2d_2` || (None, 26,26,128) || 0 |
| `Flatten` || (None, 86528) || 0 |
| `Dense` || (None, 512) || 44302848 |
| `Dropout` || (None,512) || 0 |
| `Dense_1` || (None,1 ) || 513 |

***Convolutional layers:*** The network starts with three convolutional layers (`conv2d`, `conv2d_1`, `conv2d_2`). These layers use 2D convolutions to extract features from the input data. The number after the layer name (e.g., 32, 64, 128) indicates the number of filters applied in each layer. ***Max pooling layers:*** Following each convolutional layer is a max-pooling layer (`max_pooling2d`, `max_pooling2d_1`, `max_pooling2d_2`). Max pooling reduces the dimensions of the feature maps, aiding in retaining important features while reducing computational load.

***Flatten layer:*** After the convolutional and pooling layers, there’s a `flatten` layer that reshapes the data from 2D arrays to a 1D vector. This prepares the data for the subsequent fully connected layers.

***Dense (fully connected) layers:*** Two fully connected layers (`dense`, `dense_1`) follow the flattening layer. These layers process the flattened data to make final predictions. The number after “Dense” indicates the number of neurons in each layer.

***Dropout layer:*** The “dropout” layer is used for regularization. It randomly sets a fraction of input units to zero during training, reducing the risk of over fitting.

***44396609 total parameters*** have been generated which provides the total number of trainable parameters in the network to represent the weights and biases that the model learns during training. These parameters are updated to minimize the loss function during training.

### E. Performance metrics

In `[Table 13.2](#ch13.xhtml#tab13_2)`, the metrics provide crucial insights into the performance of applied learning models and aid in comprehending the strengths and weaknesses of models across different aspects of classification performance (`[Modi et al., 2021](#ch13.xhtml#ref13_19)`; `Kumar et al., 2022`; `Koul et al., 2023`).

[Table 13.2 Performance metrics](#ch13.xhtml#R_tab13_2)

| Metrics || Formulae |
| --- | --- |
| Accuracy ||  

$$\\begin{matrix} {True\\ Positive + True\\ Negative} \\\\ {True\\ Positive + True\\ Negative + False\\ Positive +} \\\\ {False\\ Neqative} \\\\ \\end{matrix}$$  

| Loss ||  

$$\\frac{{(Actual\\ Value - Predicted\\ Value)}^{2}}{Number\\ of\\ observations}$$  

| Precision ||  

$$\\frac{True\\ Positive}{True\\ Positive + False\\ Positive}$$  

| Recall ||  

$$\\frac{True\\ Positive}{True\\ Positive + False\\ Positive}$$  

| F1 score ||  

$$2\\frac{Precision \\ast Recall}{Recall + Precision}$$  

|

### IV. Results

In this section, the applied CNN model has been evaluated on the basis of various performance metrics such as accuracy, loss, precision, recall, and F1 score. The hyper-parameters used to compile the model are mentioned in `[Table 13.3](#ch13.xhtml#tab13_3)`:

[Table 13.3 Hyper-parameters of CNN model](#ch13.xhtml#R_tab13_3)

| Hyper-parameters || Values ||  |
| --- | --- | --- |
| Activation || ReLu/Sigmoid ||  |
| Optimizer || Adam ||  |
| Class mode || Binary ||  |
| Batch_Size || 32 ||  |
| Loss || Binary cross entropy ||  |
| Dropout rate || 0.5 ||  |
| Epochs || 10 ||  |

[Table 13.4](#ch13.xhtml#tab13_4) provides a summary of the performance metrics for a trained CNN model on both the training and testing datasets.

[Table 13.4 Evaluation of CNN model](#ch13.xhtml#R_tab13_4)

| Model  || Training || Testing |
| --- | --- | --- |
|  || Accuracy || Loss || Accuracy || Loss |
| CNN || 0.83 || 0.35 || 0.88 || 0.25 |

