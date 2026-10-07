# Autoencoders for Intelligent Fault Diagnosis ■ 33

TABLE 2.2 Parameter Setting up SAE-Based DNN
| SAE | | | DNN | |
|---|---|---|---|---||
| $M$ | 2000 | Input nodes | $M$ | 2000 | Input nodes |
| $S_2$ | | Hidden nodes | $S$ | 600 | Hidden nodes |
| $Out$ | 2000 | | $Out$ | 6 | Output nodes |
| $ho$ | | Sparse target | Dropout | 0.3 | Dropout nodes |
| $eta$ | | 0.4 | Sparse rate | $\epsilon$ | 1 | Learning rate |
| $Denoise$ | | 0.1 | Denoising rate | | |
| $Dropout$ | | 0.3 | Dropout rate | | |
| $\epsilon$ | | 1 | Learning rate | |

SAE are also considered, i.e., support vector machine (SVM) and logistic regression (LR) (Khashei, Hamadani, and Bijari 2012). The features learned by the SAE, i.e., the output of the SAE, are fed into both the SVM and the LR classifiers. For a fair comparison, the SAE is the same as the one used in the proposed approach, but the features learned by the SAE cannot be fine-tuned during training for both the SVM and the LR classifiers.

In the proposed SAE-based DNN framework, the input size, hidden node, and output size are set to 2000, 600, and 2000, respectively. Considering the vibration signals six different working conditions, the layer sizes for DNN is set as [2000 600 6]. The hidden nodes of the DNN and SAE are so that the features learned by the SAE can be utilized by the DNN and fine-tuned further supervised training. The three hyperparameters of the proposed SAE-based DNN, including sparse parameter, denoted as sparse rate b, denoising rate, and dropout, are set to be 0.4, 0.1, and 0.3, respectively, via cross-validation with other baseline methods. All parameters of the proposed SAE-based DNN are listed in Table 2.2 for better understanding.

Here for all neural network-based methods, the cross-entropy is calculated on training samples and propagated through layers to update model parameters, in which the stochastic gradient descent method is used. The simulation environment for all algorithms performed in the experiments is MATLAB R2011b software.

# Results and Discussion

Since the level of corruption is a hyper-parameter in the SAE, it is meaningful to study the effect of corruption noise on the final classification performance. Here, the noise levels changed from 0 to 0.5 with a step size of 0.1. Figure 2.5 (a) shows the classification performance with different corruption noise. It can be seen that proper denoising coding in the SAE could improve its performance, but too heavy corruption will degrade the input data quality, leading to a decrease of the classification performance. This verified that the SAE trained with appropriate noise data can extract more robust features than traditional one and it is of great significance in complex environment.

In addition, the effect of dropout on the performance of the DNN is also studied. Here, dropout rate changed from 0 to 0.5 with a step size of 0.1. Figure 2.5 (b) shows the classification performances with different dropout rates. The results showed that the best classification performance was obtained at a dropout rate close to 0.3 and the performance decreased