
## 94 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

## Time–Frequency Distribution

TFD is used to describe the relationship between a signal's information in the time domain and its corresponding spectral content in the frequency domain (Cohen 1989). It is an effective approach in feature extraction as it reserves and reveals both time and frequency information of the original signal simultaneously. There are a variety of methods that are able to generate good time–frequency resolution, wavelet transform is widely adopted in analyzing signals measured on induction motors.

Continuous wavelet transform (CWT) is widely used and can be calculated by the inner product of the signal and a family of the wavelets (Lin and Qu 2000). Scale and translating the mother wavelet $\Psi(t)$ generates the wavelet family:

$$\Psi_{s,\tau}=\frac{1}{\sqrt{s}}\Psi\left(\frac{t-\tau}{s}\right) (6.1)$$

where $s$ and $\tau$ denote the scale parameter and the translation parameter, separately, and $s$ is related to frequency inversely.

The CWT of given signal $x(t)$ can be obtained by the convolution operation of the complex conjugate, which is mathematically defined as follows:

$$\Psi_{s,\tau}=\frac{1}{\sqrt{s}}\Psi\left(\frac{t-\tau}{s}\right)W(s,\tau)=\frac{1}{\sqrt{s}}\int x(t)\psi^*\left(\frac{t-\tau}{s}\right)dt (6.2)$$

where $\psi^*)$ represents the complex conjugate of $\psi())$. That is, the signal is decomposed into a set of wavelet coefficients. As there are two kinds of parameters, scale and translation parameters, the signal can be projected to a 2D plane. Therefore, time-scale (or frequency) images can be obtained by conducting CWT to the original signals.

## DCNN-Based Multi-Sensor Fusion for Intelligent Fault Diagnosis

A fault diagnosis framework based on DCNN for detecting the working state of induction motors using multiple sensor signals. The proposed method can automatically classify induction motor condition by learning patterns that contain crucial information for distinguishing different working states directly from the original signals.

In general, multiple sensor signals are used for the purpose of fault diagnosis. In induction motor fault tasks, vibration signal and current are currently used as they contain useful fault-related signature reflecting the certain working state. Therefore, both vibration signal and current are used in this chapter, and their TFD images that provide discriminative information among different working conditions are used as the input. Figure 6.1 shows examples of original vibration and current signals collected from the induction motor under three different fault conditions.

As shown in Figure 6.1, the original signals in time domain do not have clear native features and it is difficult to correctly distinguish different working states. Therefore, data preprocessing using CWT is implemented as it generates time-frequency images containing fault signature among different conditions where DL method can be used to learn the certain hidden pattern from the images, and examples are shown in Figure 6.2. Figure 6.3 illustrates the flowchart of the DCNN-based multi-signal induction motor fault diagnosis, where both vibration signal and current signal are simultaneously measured by sensors attached on the induction motors under operation, and then these signals are converted to TFDs using CWT. These obtained TFDs are treated as gray-scale images and used as the input to the proposed deep model. CNN is adopted as the building block of our multi-signal framework, and the building block is designed with one input layer, one output layer, three convolutional layers where each convolutional layer is followed by a maxpooling operation and one fully connected layer after convolutional and maxpooling layers, as shown in Figure 6.4. The size of the input layer equals to gray-scale images size, and the model output is the label prediction which points to one certain condition that the input sample is most likely to belong to. The designed model is randomly initialized and training dataset (6000 samples with 6 working states and each working state has 1000 samples) is used to train the deep model. By minimizing the error between output prediction from the model and real labels, the parameters of DCNN model are updated iteratively. After enough training epochs, the model is well trained and fine-tuned parameters are saved, which can then be applied to.

![](img/f29bba55de4872c43f26af4667e705f2_105_0.png)

![](img/f29bba55de4872c43f26af4667e705f2_105_1.png)

FIGURE 6.1 Original vibration signals and current signals from induction motor under three different states.

![](img/f29bba55de4872c43f26af4667e705f2_105_2.png)

![](img/f29bba55de4872c43f26af4667e705f2_105_3.png)

FIGURE 6.2 TFDs of vibration signals and current signals from induction motor under three different fault states.

![](img/f29bba55de4872c43f26af4667e705f2_106_0.png)

FIGURE 6.3 Flowchart of DCNN-based induction motor fault diagnosis.

## Vibration Signal

![](img/f29bba55de4872c43f26af4667e705f2_106_0.png)

FIGURE 6.4 CNN as the building block of multi-signal framework.

## Multi-Sensor Fusion for Intelligent Fault Diagnosis

### EXPERIMENTAL STUDIES

#### Data Preprocessing and Splitting

To verify the performance of the proposed approach, the data acquired on machine fault simulator are used in this chapter. Specifically, vibration signals and current signals are measured simultaneously, as illustrated in Figure 6.5. In order to prepare dataset for training and testing, 1024 data points are chosen to be one sample and time–frequency image of each sample is reshaped to $128 \times 128$ pixels. In all, 1000 samples for each working condition are acquired and randomly divided into training and testing subsets, with 800 training samples and 200 testing samples. As 6 working conditions are investigated, the overall dataset contains 6000 samples.

![](img/29bba55de4872c43f26af4667e705f2_107_0.png)

![](img/f29bba55de4872c43f26af4667e705f2_107_1.png)

FIGURE 6.5 Experimental facility (Yang, Yan, 2015).

#### Evaluation Metrics

Classification accuracy is calculated as the metrics to evaluate the performances of deep architectures:

$$Accuracy = \frac{N_{right}}{N_{total}} (6.3)$$

where $N_{right}$ represents the number of samples that the deep architecture is able to classify correctly, and $N_{total}$ is the number of total samples.

#### Training Details

In order to provide a robust estimation of the proposed model, experiments are repeated 50 times and statistics are used to summarize the model performance. Training and testing time are also recorded to investigate the model efficiency. All the algorithms are conducted in Keras platform using TensorFlow backend. TensorFlow was originally invented by Google Brain for machine learning researches and for training DNNs. Now, it has become an open-source software library for numerical computation. Keras is a high-level neural networks programming interface which enables fast implementation in building and training DNNs. We conducted all the experiments on a Linux server using one Nvidia GTX 1080 GPU.

#### Compared Models

Methods used for comparison are listed as follows:
- Shallow neural network with one hidden layer using original signals as input (neural network based on back propagation).
- SVM utilizing wavelet energy features as input (wavelet energy + SVM).
- DNN with three hidden layers that are fully connected using wavelet energy of features as input (wavelet energy + DNN).
- One-layer SAE-based neural network using vibration signal.

TABLE 6.1 Working Condition of Induction Motor (Yang, Yan, 2015)
| Condition | Description |
| --- | --- |
| HEA | Healthy motor |
| SSTM | Shorted turns occur in winding |
| UBM | Rotor with added unbalance |
| RMAM | Bearing has defect in inner ring |
| BRB | Rotor bars are broken |
| BRM | Rotor is bent |
