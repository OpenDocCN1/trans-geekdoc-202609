
(color component along the green-magenta axis), and B (color component along the blue-yellow axis). LAB image is split into its individual channels, resulting in a list of LAB planes. The L channel, which represents the image’s lightness, will be enhanced to improve contrast. CLAHE is a variant of histogram equalization that enhances contrast while limiting amplification of noise. It is adaptive to the local image content. Clip limit is taken as two. The grid size of tiles is taken to be five-by-five pixels. CLAHE operation is applied to L channel, enhancing the contrast of L in LAB image. This step aims to improve the overall contrast of the image while preserving local variations. An enhanced LAB image is created by merging enhanced L channel with original A and B channels. BGR color space image is created by converting the enhanced LAB image. This image is contrast-enhanced image.

## Hyperparameter Setup

Fine-tuning techniques are applied to optimize the model’s performance for colorectal cancer classification. Experimentation has been repeated through the hyperparameter search space to investigate the best model. The optimal parameter setup is detailed in Table 2.

SCRNN is trained using RMSProp optimizer. For training deep models, RMSprop can provide faster convergence compared to standard gradient descent. The adaptive learning rate feature of RMSprop can

## Table 2. Hyperparameter setup

| Layer | Description |
| :--- | :--- |
| Model = Data Preprocessing kernelSize - ks, strideSize - ss, activationType - at, filters = f, poolSize = ps, poolingType - pt, BatchNormalization - bn | |
| Image Filter | Gaussian, KernelSize = (5, 5), sigma_x = 1 |
| Contrast Enhancement | CLAHE |
| Model = ShuffleNetV2 scaleFactor = 1.0, inputShape = (32, 32, 3), ShuffleUnits = [3, 7, 3], paddingType = 'same' bottleneckRatio = 1, bottleneckChannels = [0.0, 0.0, 116.0, 464.0] | |
| Conv2D | f = 24, ks = (3, 3), ss = (2, 2), pt = ReLU |
| MaxPool2D | ps = (3, 3), s = (2, 2) |
| Shuffle Unit-s1-Conv2D | ks = (1, 1), s = 1, bn = yes, at = ReLU |
| Shuffle Unit-s1-DepthwiseConv2D | ks = 3, s = 2, bn = yes |
| Shuffle Unit-s1-Conv2D | ks = 1, s = 1, bn = yes, at = ReLU |
| Shuffle Unit-s2-DepthwiseConv2D | ks = 3, s = 2, bn = yes |
| Shuffle Unit-s2-Conv2D | ks = 1, s = 1, bn = yes |
| Conv2D | f = 1024, ks = 1, s = 1, at = ReLU |
| Pooling | max |
| Model = CRNN | |
| CNN | f = 512, ks = 3, pt = 'same', at = ReLU |
| BiLSTM | size = 256 |
| Dense Layer | Size = 8, at = softmax, optimizer = RMSprop, loss = categorical_crossentropy |

reduce the need for manual tuning of the learning rate. This saves time and effort in the hyperparameter tuning process. RMSprop is a versatile optimizer that works well in image classification.

## Experimental Results

The SCRNN model operates on a dataset comprising histological images of colorectal tissue. SCRNN model is trained on the preprocessed dataset to learn the patterns associated with different types of colorectal tissue. Figure 8 shows the sample “Mucosa” type image at various stages of SCRNN.

Experimental setup involved training and testing the models using a dataset of histological images. The dataset is divided into training and validation datasets to ensure robust evaluation. RMSprop optimizer is used for training as it offered adaptive learning rates and contributed to stable and efficient convergence during the training process. Early stopping with a patience of 5 epochs is employed to prevent overfitting. The models were trained using a batch size of 128 and a maximum of 50 epochs. SCRNN’s performance is evaluated using metrics including MCC to provide a comprehensive understanding of SCRNN’s effectiveness in colon cancer classification.

The performance of SCRNN is evaluated against other deep models. Experimental results demonstrate the model’s capability to classify colorectal tissue accurately (Table 3). A comparative analysis of proposed SCRNN model with other deep learning architectures is performed. Other deep models include Simple CNN, VGG16, ResNet-18, and MobileNet. The primary objective is to evaluate SCRNN’s performance in context of colon cancer classification based on histological images.

Figures 9, 10, 11, 12 shows the confusion matrix, accuracy & loss curves, P-R curve, ROC curve of SCRNN training and validation respectively. The confusion matrix indicates that SCRNN has achieved a high degree of accuracy in classifying different tissue types within the colon cancer histological images. The diagonal from top-left to bottom-right represents the true positives (correctly classified samples) for each tissue type. Strong values along this diagonal for all classes suggest that SCRNN is proficient at classifying most samples correctly. Some misclassifications can be observed in the matrix, indicated by non-zero values outside the diagonal. These misclassifications are not extensive, reflecting the robustness of SCRNN. ‘Complex’ and ‘Mucosa’ classes exhibit some confusion. SCRNN seems to occasionally confuse these two tissue types. However, the misclassifications between ‘Tumor’ and ‘Debris’ are relatively minor.

The baseline model, a simple CNN, achieved a commendable accuracy of 95.47%. While it demonstrated high specificity (96.53%), and MCC (0.9110) indicated room for improvement. However, its recall (88.57%) indicates some difficulty in recognizing cancerous regions, potentially leading to missed cases. The VGG16 model exhibited an accuracy of 96.73% and notably high specificity (97.22%). These results imply a robust ability to classify non-cancerous tissue accurately. It also showed improved recall (91.24%) and an MCC of 0.9013, indicating a strong performance compared to Simple CNN, enhancing its ability to detect cancerous regions. ResNet-18 demonstrated accuracy (98.99%) and high specificity (98.36%). These results suggest a strong capability to correctly classify non-cancerous tissue. Its recall (93.19%) and MCC (0.9247) surpasses that of VGG16, underlining an enhanced ability to identify cancerous regions. MobileNet delivered an accuracy of 99.12%, with a high specificity of 98.73%. It achieved an impressive recall (93.87%) and MCC (0.9256), showcasing its capabilities detecting cancerous regions.

SCRNN model performed better than other chosen architectures with an accuracy of 99.53%. It exhibited an appreciable specificity of 99.16%. These results signify the model’s proficiency in classifying non-cancerous tissue. With a recall of 94.50%, SCRNN excels at cancerous region identification.

The MCC value of 0.9344 indicated the model's robust performance. SCRNN achieved an F-Score of 0.9412 and precision of 0.9464.

While MobileNet and ResNet-18 demonstrate remarkable performance, it is noteworthy that SCRNN's marginally higher recall and MCC values set it apart. These metrics are critical in medical image analysis, where correctly identifying cancerous regions is paramount.

SCRNN achieved the highest accuracy among all models, indicating its ability to correctly classify histological images into eight classes. The impressive specificity, recall, MCC, F-Score, and precision values further emphasize the model's excellence in distinguishing different classes of colon cancer.

The observations from the P-R curve of SCRNN are as follows. The high accuracy and precision values for all classes indicate SCRNN's ability to make correct predictions for each tissue type. SCRNN demonstrate robustness in classifying various tissue types within colon cancer histological images. The

## Figure 8. Sample histological image at various stages of SCRNN

![](img/20813928ec98c7f6fbdbab0d52bde2f1_308_0.png)

## Figure 9. Confusion matrix of SCRNN

| Actual Class \ Predicted Class | ADIPOSE | COMPLEX | DEBRIS | EMPTY | LYMPHO | MUCOSA | STROMA | TUMOR |
|---|---|---|---|---|---|---|---|---|
| ADIPOSE | 174 | 0 | 0 | 17 | 0 | 0 | 0 | 0 |
| COMPLEX | 0 | 189 | 0 | 0 | 1 | 1 | 1 | 1 |
| DEBRIS | 0 | 7 | 188 | 1 | 1 | 0 | 0 | 0 |
| EMPTY | 1 | 0 | 0 | 172 | 0 | 0 | 0 | 0 |
| LYMPHO | 0 | 10 | 0 | 0 | 167 | 1 | 0 | 6 |
| MUCOSA | 0 | 20 | 0 | 0 | 4 | 149 | 5 | 3 |
| STROMA | 0 | 5 | 0 | 0 | 0 | 0 | 192 | 0 |
| TUMOR | 0 | 0 | 1 | 0 | 1 | 0 | 1 | 180 |
