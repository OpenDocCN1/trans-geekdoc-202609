# 4.2. 4S-TFSM-based CNN

Neural networks solve multiclass classification problems in machine learning. In particular, CNNs allow weight sharing and downsampling at several stages of the network, reducing the number of parameters and resulting in an effective architecture for large-scale classification.

The structure and parameters of the 4S-TFSM-CNN network are given in Table 3. During the training process, stochastic gradient descent is used to minimize the loss according to the cross-entropy loss function. The rectified linear unit (ReLU) activation function is employed in the implicit layer, and softmax is applied in the output layer to obtain a probability sum of 1 for each category and to use the predicted category as the category with the highest probability.

The training set was used to generate 320,000 training subtasks in the model training process, with the batch size set to 32, the training step size set to 10,000, and the learning rate set to 0.001. To prevent chance and specificity, 300 task data were selected in the test set and the average test precision and standard deviation of all tasks were obtained.

The accuracy of the oil well working condition recognition using different numbers of DCs constituting the 4S-TFSM is shown in Table 4. It can be seen that after feature extraction of the DC data by 4S-TFS, the highest recognition accuracy of 98.48% and the lowest standard deviation of 0.72% were achieved with the composition of 4 DCs. The training and test processes of 10,000 times for this scenario are shown in Fig. 7.

As shown in Fig. 7, only approximately 3000 training epochs are needed to achieve an accuracy of nearly 98% for working condition recognition on the test dataset, and the loss value drops to a low level and then stabilizes around that value, which indicates that the trained CNN has good stability and also shows that it is feasible to train the CNN model with 3000 samples.

As described in Section 3.2, based on the 4S-TFSM with 4 DCs, we also used 4 DCs to form the 1S-TFSM, 2S-TFSM and 8S-TFSM. Table 5 shows the accuracy of the working condition identification using 4 DCs under different TFSMs.

It is evident that the 1S-TFSM constructed with all interpolated load-displacement data cannot extract enough feature information, thus reducing the recognition accuracy. Similarly, the recognition accuracy of splitting the dynamometer curve into 8 segments to form the 8S-TFSM is relatively low due to the dynamometer curve consists of only 200 points with simple features, and the sample points are too small to extract effective time-frequency features, which reduces the recognition accuracy of the 8S-TFSM. It is worth mentioning that the 2S-TFSM and 4S-TFSM achieve nearly the same result, which is due to the simple curve composition of S₁ and S₃ in Fig. 3, and the two parts also belong to the upstroke load and downstroke load, respectively, which causes the difference in the extracted time-frequency features to not be obvious.

**Table 3**  
The architecture of 4S-TFSM-CNN.

| Layer | Type | Feature maps | Filter size | Dropout |
|---|---|---|---|---|
| 0 | Input | 23 × 23 × 4 | — | — |
| 1 | Conv 1 | 23 × 23 × 32 | 3 × 3 | — |
| 2 | Conv 2 | 23 × 23 × 64 | 3 × 3 | — |
| 3 | Pool 1 | 12 × 12 × 64 | 2 × 2 | — |
| 4 | Conv 3 | 12 × 12 × 128 | 3 × 3 | — |
| 5 | Conv 4 | 12 × 12 × 128 | 3 × 3 | — |
| 6 | Pool 2 | 6 × 6 × 128 | 2 × 2 | — |
| 7 | FC 1 | 1 × 1 × 1024 | — | 0.1 |
| 8 | FC 2 | 1 × 1 × 512 | — | 0.1 |
| 9 | FC 3 | 1 × 1 × 8 | — | 0.1 |

# 4.3. Performance comparison

The method of classifying the dynamometer cards as images has been successfully applied to the working condition recognition of SRPS. Inspired by this result, we conducted a comparative study of image-CNN and the 4S-TFMS-CNN proposed in this paper. We first draw the DC based on the sensor data and generate a 640 × 480 image. Subsequently, the binarization process is performed. Finally, the binarized image is compressed to 64 × 64 and used as the input of the image-CNN.

Different from 4S-TFSM-CNN, the input size of image-CNN is 64 × 64 × 1, so we added 1 maximum pooling layer between the first and second convolutional layers. In addition, we also tried to input load-displacement data into the neural network to generate the data-based-CNN, and to input 4S-TFS features extracted from a single DC into the neural network to generate the 4S-TFS-CNN. The structure and parameters of the three neural networks are depicted in Table 6.

The accuracies of the four methods for working condition recognition are shown in Table 7. It is evident that the recognition accuracy of 4S-TFS-CNN is 97.53%, which is significantly higher than the accuracies of 96.83% and 97.39% of image-CNN and data-based-CNN methods. Meanwhile, the standard deviation of 4S-TFS-CNN is 0.91%, which is also lower than 1.08% and 0.99% of image-CNN and data-based-CNN, which indicates that the 4S-TFS feature-extraction method for a single DC can extract effective features for CNN classification. In addition, among the four methods, 4S-TFSM-CNN has the highest recognition accuracy of 98.48% and the lowest standard deviation of 0.72%, which demonstrates that the construction of 4S-TFSM by combining multiple DCs can solve the heterogeneity problem and improve the work condition recognition accuracy.

Fig. 8 shows the working condition recognition accuracies of image-CNN, data-based-CNN, and 4S-TFSM-CNN with different training steps. Fig. 8(a) demonstrates that throughout the training phase, the 4S-TFSM-CNN achieves similar accuracy and loss as the image-CNN and data-based-CNN. On the test set in Fig. 8(b), the accuracy of 4S-TFS-CNN is higher than that of the image-CNN and data-based-CNN overall, which is consistent with the findings in Table 7. This also illustrates that sufficient feature information can be extracted from multiple DCs for CNN working condition recognition by a 4S-TFSM, which confirms the effectiveness of the 4S-TFSM-CNN.

In addition, Table 8 demonstrates the effects of the four methods on CNN performance. It is evident that the proposed 4S-TFS-CNN method has the least algorithmic complexity, time complexity and training time, and the recognition accuracy is higher than that of Image-CNN and Data-based-CNN. Compared with data-based-CNN, the proposed 4S-TFSM-CNN method increases in algorithm complexity, time complexity and training time, but the recognition accuracy is the highest. The analysis of Tables 7 and 8 verifies that the proposed 4S-TFSM can reduce the model complexity and computational cost, and improve recognition accuracy.

# 4.4. Discussion

We used classical machine learning methods such as RF, k-NN and SVM for prediction on the same dataset, and the results are given in Table 9. It can be seen that image-RF (image as input feature) and RF algorithm as classifier has the lowest expected accuracy of 92.59% and 4S-TFSM-CNN obtains the highest accuracy of 98.48%. Compared with other deep learning-based methods, such as RNN, LSTM and GRU, image-RNN has the lowest accuracy of 87.40%, while LSTM and GRU-based methods have better performance than RNN, but the accuracy is also lower than the proposed