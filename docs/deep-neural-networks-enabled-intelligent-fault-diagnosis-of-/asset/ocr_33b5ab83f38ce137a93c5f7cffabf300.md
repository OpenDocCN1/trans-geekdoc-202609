# 64 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

![](bbox=[0.121, 0.085, 0.882, 0.4])

FIGURE 4.2 The framework of CDFL method.

# CNN-Based Intelligent Fault Diagnosis

In the proposed CDFL framework, a convolutional pooling architecture is first designed with K local filters of N window size. Then, the BPNN is constructed, which is a three-layer structure where the sizes of input layer, hidden layer, and output layer are filter window size, filter number, and fault counts, respectively. Therefore, the learning templates are prepared for discriminative learning, whose lengths are set to be the same as filters’ window size. These templates with their fault labels are used to train the BPNN. The parameters between the input layer and hidden layer are transferred into the one for convolutional layer. Then, the convolutional pooling architecture with the transferred parameters is applied to the raw data to learn new representations. Finally, the new representations are fed into SVM for classification to predict fault categories. As a summary, BPNN is used to learn the model parameters and then the learned parameters are adopted for the local filters realizing the convolutional discriminative feature learning. Then the learned representation can be fed for the classification of SVM. The whole procedure for motor fault diagnosis via the proposed CDFL method is illustrated in Figure 4.2.

# EXPERIMENTAL STUDIES

In this section, we test the induction motor dataset to verify the performance of the CDFL method for comparative studies.

# Induction Motor Dataset

The machine fault simulator is illustrated in Figure 4.3. The machine fault simulator is driven by a 1/2-hp induction motor (Model: Marathon Motors 56T34F5301J). A triaxial ring-style accelerometer (Model: PCB 604B31) with ±50 g measurement range at 100 mv/g sensitivity is mounted on the surface of the induction motor to the shaft end