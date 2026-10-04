
# S. Sun et al.

# Biomedical Signal Processing and Control 112 (2026) 108528

![](img/227c841f21f5a658d08dfdd42355ede_5_0.png)
Fig. 5. Structure of Bidirectional Long-Term Memory (Bi-LSTM) network.

By applying PSO to our architecture, we optimized the number of convolutional layers and kernel sizes. Specifically, we set the number of kernels between 12 and 16, and the kernel size to 10 × 10 and 15 × 15. This optimization significantly improved the overall network performance by finding the most effective combination of these hyperparameters for classification task.

# Algorithm 1 PSO
1: FOR each particle i
2: FOR each dimension
3: Initialize $x_i$ within permissible range
4: Update velocity $v_i$ within permissible range
5: END FOR
6: END FOR
7: FOR iteration =1
8: FOR each particle i
9: Calculate fitness
10: If fitness is better than $g_{best}$
11: SET current fitness as $g_{best}$
12: END FOR
13: END FOR
14: Choose the best value $g_{best}$ for the particle
15: Update $v_i'$ of the particle
16: Update $x_i'$ of the particle
17: WHILE iterations or minimum error are not attained
18: END WHILE

![](img/227c841f21f5a658d08dfdd42355ede_5_1.png)
Fig. 6. Squeeze-and-Attention mechanism.

| X | H × W × C |
|---|---|
| Global pooling | 1 × 1 × C |
| FC | 1 × 1 × C |
| ReLU | 1 × 1 × C |
| FC | 1 × 1 × C |
| Sigmoid | 1 × 1 × C |

configuration, as illustrated in Fig. 7, and its detailed hyperparameters shown in Table 1.

## 2.5.4 Attention Extraction

In deep learning, the importance of various spatial locations or channels is dynamically enhanced by the Squeeze-and-Attention mechanism, allowing to concentrate on the most relevant to the task at hand. In our model, we integrated the attention mechanism within the CNN network, adding attention layers. Instead of using all channels, the attention mechanism learns their importance based on their contribution to our task. This data-driven approach enables the model to learn important features without relying on prior assumptions. The detailed architecture of this is shown in Fig. 6.

- The first 1D convolutional layer (Conv1d) applies 16 filters with 10 × 10 kernel size to capture spatial patterns.
- 2nd convolutional layer (Conv2d) refines the extracted features with 15 × 15 kernel.
- These layers are followed by batch normalization (BN) and ReLU activation, ensuring stable gradient and improved feature representation.
- A pooling layer is then applied to the feature maps, reducing computational complexity while preserving spatial information.

## 2.5.5. SE fusion network

This study proposes a fusion network that integrates CNN, Squeeze-and-Attention (SE) mechanism, and Bidirectional Long-Term Memory (Bi-LSTM) networks to effectively capture both spatial and temporal characteristics of EEG signals. The network architecture follows CNN.

## B. SE Attention: Adaptive Feature Extraction

The attention mechanism enhances the model's ability to focus on the most informative channels. It dynamically recalibrates feature importance through the following strategy:

- 1. Global Average Pooling (GAP): The feature maps are mapped to 1 × 1 × C map, which encodes the global distribution of signals.

![](img/227c841f21f5a658d08dfdd42355ede_6_0.png)
![](img/227c841f21f5a658d08dfdd42355ede_6_1.png)
Table 1: Parameters of hybrid deep learning network.

| Layer | Filters | Size | Activation |
|---|---|---|---|
| CNN | Input | (251,251) | |
| Conv_1 | 16 | (10,10) | ReLU |
| Conv_2 | 12 | (10,1) | ReLU |
| SE | Maxpool | (15,15) | ReLU |
| FC_1 | 3 | | |
| FC_2 | 12 | | Sigmoid |
| Bi-LSTM | Flatten | 13,080 | |
| FC_3 | 16 | | |
| SoftMax Output | 2 | | |

- A sigmoid activation function normalizes the learned attention weights to the range [0,1], emphasizing specific channels.
- These weights applied to the original feature maps element-wise multiplication, selectively enhancing significant channels while suppressing irrelevant ones.

Through this process, the SE mechanism dynamically adjusts the importance of different channels, ensuring that channels containing noise are prioritized. This weighting improves the ability to distinguish imagery patterns effectively.

- Bi-LSTM Component: Temporal Dependency Modeling. The weighted feature maps from the SE module are then processed by the Bi-LSTM network, which captures both forward and backward temporal dependencies in EEG signals.
- The Bi-LSTM layer contains 16 hidden units, allowing it to effectively encode long-range dependencies across time.
- A fully connected (FC) layer reduces the feature dimensions from C to C/r (where r is the reduction ratio, set to 3), ensuring compact feature representation.
- A second FC restores the feature dimensions back to C, maintaining consistency with the original features.
- A fully connected layer with tanh activation integrates bidirectional, enabling the network to construct a more comprehensive representation.

## 2. Dimensionality Reduction & Restoration:

## 3. Channel Weighting

## D. Optimization and Training.

To optimize the algorithm, Particle Swarm Optimization (PSO) algorithm is used to determine the optimal number of convolutional kernels. Training is conducted using the Adaptive Moment Estimation (ADAM) optimizer, with an initial learning rate of 0.01, which is reduced to 001 after 300 epochs to balance convergence speed and accuracy.

To evaluate the model, we employ three metrics: accuracy, kappa value and sensitivity. Accuracy provides an average measure of correct predictions across all classes, with the kappa value accounting for disagreement between observed and expected classifications. These metrics will be used to compare our model against baseline methods and state-of-the-art approaches, demonstrating the superior performance of our fusion in EEG-based classification.

participant, preprocessing pipeline described in Section 2.3 to ensure consistency and fairness. Parameter optimization for machine learning models was performed using grid search. Accuracy, sensitivity, and kappa coefficient were used as evaluation metrics across all models.

$$P_{acc} = \frac{TP + TN}{TP + TN + FN} (10)$$

$$P_{\kappa} = \frac{(TP + TN)(TP + FN)}{(TP + FP)(TN + FN)} (11)$$

$$Kappa = \frac{TP - FP}{TP - FP + TN + FN} (12)$$

$$Sensitivity = \frac{TP}{TP + FN} (13)$$

Here, True Positive (TP) refers to cases where the model correctly identifies the intent imagery, and True Negative (TN) denotes where the model correctly predicts the absence of intent imagery. Conversely, False Positive (FP) occurs when the model incorrectly classifies a non-intent imagery; False Negative (FN) refers to cases where the model fails to detect the imagery. $P_{acc}$ refers to the classification accuracy, and $P_{\kappa}$ refers to the expected accuracy due to random chance.

## 3. Results

### 3.1. Classification performance

After 400 iterations of training, the proposed model achieved an average accuracy of 72.14% (SD - 3.60) for distinguishing left and right imagery classes across subjects (Fig. 8). Despite inter-subject variability, participants' accuracies ranged from 70% to 75%, indicating relatively consistent performance.

### 3.2. Comparative analysis

Table 2 presents a comparison of our approach with widely used classification techniques, including EEGNet [36], CNN-SVM [38], energy-efficient CNN [39], and CNN-LSTM [40]. All methods were trained and tested on the same dataset. Our model achieved high average accuracy (72.1%) and kappa coefficient (0.436), which is significantly higher than other methods. For instance, the average accuracy of 63.7% is much higher than that of CNN-SVM (59.5%) and energy-efficient CNN (53.8%). Our kappa coefficient of 0.096 is also much higher than that of CNN-SVM (0.027) and CNN-LSTM (0.050), showing that our method performs better compared to others.

To evaluate classification performance, the sensitivity of each method is analyzed, as shown in Table 3, which reflects the ability to correctly classify each class, which is a key metric for assessing the effectiveness of the classification system. The highest sensitivity (69.9%) was achieved by the proposed model, consistently outperforming all other approaches. It is followed by CNN-LSTM (67.5%) and CNN-Net (62.2%), while the lowest sensitivity (54.9%) was observed for CNN-SVM.
