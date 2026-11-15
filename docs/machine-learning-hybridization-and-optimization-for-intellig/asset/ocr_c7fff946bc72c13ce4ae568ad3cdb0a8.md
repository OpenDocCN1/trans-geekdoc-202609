the PNN network than other works. The performance metric values of the present method are given in Table 9.3.

# TABLE 9.3 Performance metrics of PNN and KNN

| S. No. | Performance metrics | PNN | KNN |
|---|---|---|---|
| 1. | Accuracy | 98.4% | 96.67% |
| 2. | Sensitivity | 95% | 93.75% |
| 3. | Specificity | 90% | 89.5% |

From the above representation, it is inferred that our proposed method for feature extraction and classification was executed by utilizing DWT, LBP, and PNN, respectively. It is more efficient and accurate with an accuracy of 98.4% for PNN and 96.67% for KNN.

To begin with, in the proposed work, a graphical user interface (GUI) is created indicating all the required processing to be done. The GUI is created with all interfaces to load the signal, perform preprocessing, apply DWT to extract features, carry out the training phase, test and classify arrhythmia types, and finally carry out the validation step. Firstly, the input is loaded into the program and preprocessing is done. Figure 9.8 shows the input signal that is fed and the corresponding filtered output signal. The filtering is performed using the NLMS filter. In addition, LBP is used to compute histogram features such as mean and standard deviation.