
## Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

on the test data. In this study, the dropout technique is applied to train the SAE-based DNN to prevent complex co-adaptations on the training data and allow extraction of the same features repeatedly. Technically, the “dropout” can be realized by setting the output $a = sigmoid(Wx + b)$ of some hidden neurons to zero so that these neurons will not be involved in the forward propagation training process. It should be noted that there are some differences between the training process and testing process with dropout. The dropout is turned off during testing, which means the outputs of all hidden neurons will not be masked during testing. This will help to improve the feature extraction and classification capability of the SAE-based DNN.

### SAE-Based Intelligent Fault Diagnosis
By taking advantage of the unsupervised learning, the denoising SAE is used to learn features from unlabeled data and initialize the DNN structure. When the learned sparse feature representation of the AE is utilized to train a neural network classifier with motor fault diagnosis, instead of direct utilization of learning by denoising SAE, the parameters of the neural network classifier with the corresponding parameters are initialized in a well-trained SAE and then updated further. This adaptation enables further fine-tuning of learned parameters so that the learned representation can capture more discriminative components in vibration signals. In addition, a previous study (Coates, Lee, and Ng 2011) indicated that the number of hidden neurons in the deep model is as important as the choice of learning algorithm and the depth of the model for achieving high classification performance, which means that single-layer network in unsupervised feature learning also perform well. Therefore, in this study only single-layer SAE is utilized to realize the DNN for the induction motor fault diagnosis.

The training procedure of the DNN is shown in Figure 2.3 and it is described in subsequence text.

![](img/f29bba55de4872c43f26af4667e705f2_40_0.png)

FIGURE 2.3 Structure of the sparse AE-based deep neural network.

## Autoencoders for Intelligent Fault Diagnosis

The unlabeled induction motor vibration data $X_1$ are first used to train the SAE though following steps:

- 1. Set up the learning rate, sparse rate and denoising parameters, dropout rate, etc. and initialize the weight $W$ and $b$ randomly.
- 2. Use the stochastic batches training method in the forward propagation algorithm to compute the average activation $\rho_j$ for sparsity.
- 3. Compute the sparse cost function as:

```
$C_{sparse}(W,b) = \left[ \sum_{i=1}^{n} |h_{w,b}(x(i)) - y(i)|^2 \right] + \beta \sum_{j=1}^{52} KL(\rho|\rho_j) \quad (2.10)$
```
- 4. Update the parameters $W$ and $b$ based on Eq. (2.6) and (2.7).

Then the labeled induction motor vibration data $(X_2, Y_2)$ are used to train the DNN for classification.

- 1. Set up the parameters of the SAE to initialize the first layer of the DNN.
- 2. Set up the training parameters and dropout rate, and conduct the forward propagation algorithm to extract the labeled features for classification.
- 3. Compute the mean square error for the cost function of the DNN using Eq. (2.4).
- 4. Conduct the backpropagation algorithm the same as before except for the sparse term (set sparse penalty to 0) to update the weights and fine-tune the entire network.

Finally, the test data $(X_3, Y_3)$ are used to verify the effectiveness of the presented SAE-based DNN.

## EXPERIMENTAL STUDIES (FOR INDUCTION MOTOR INTELLIGENT FAULT DIAGNOSIS)

In this section, we are going to verify the performance of the proposed SAE-based intelligent fault diagnosis method on an induction motor dataset.

### Experimental Description

To verify the effectiveness of the SAE-based DNN for induction motor fault diagnosis, the experiments have been conducted on a machine fault simulator as illustrated in Figure 2.4. The vibration signals can be acquired by an acceleration sensor when the motor operates under six different conditions. The vibration data of the simulator under the power supply are collected with the sampling frequency of 20 kHz. The descriptions of different motor working conditions are listed in Table 2.1.

![](img/f29bba55de4872c43f26af4667e705f2_42_0.png)

FIGURE 2.4 Experimental setup: (1) Tachometer, (2) induction motor, (3) bearing, (4) shaft, (5) load disc, (6) belt, (7) data acquisition board, (8) bevel gearbox, (9) magnetic load, (10) reciprocating mechanism, (11) variable speed controller, and (12) current probe.

The task defined here is to classify different motor working conditions based on vibration data. In this study, 600 data samples with 200 features from each induction motor working condition were obtained, in which each feature corresponds to one sampled data point of the vibration. For each working condition, 400 of the samples were chosen randomly for training and the rest for testing. When 2400 training samples and 1200 testing samples are obtained with feature dimensionality of 2000, they are all normalized to set the value between -1 and 1.

Several neural network-based methods are compared here with the proposed approach. To verify the effectiveness of the SAE-based DNN, the experiments have been conducted on a machine fault simulator as illustrated in Figure 2.4. The vibration signals can be acquired by an acceleration sensor when the motor operates under six different conditions. The vibration data of the simulator under the power supply are collected with the sampling frequency of 20 kHz. The descriptions of different motor working conditions are listed in Table 2.1.

| Condition | Description |
| :--- | :--- |
| HEA | Healthy motor |
| BRB | Broken bar |
| BRM | Bowed rotor |
| RMAM | Defective bearing |
| SSTM | Stator winding |
| UBM | Unbalanced rotor |

### Table 2.2 Setting up SAE-Based DNN

| SAE | DNN |
| :--- | :--- |
| $M$ | 2000 |
| $S_2$ | 600 |
| $Out$ | 2000 |
| $\rho$ | Sparse target |
| $\beta$ | 0.4 |
| $Dropout$ | 0.3 |
| $\epsilon$ | 1 |
