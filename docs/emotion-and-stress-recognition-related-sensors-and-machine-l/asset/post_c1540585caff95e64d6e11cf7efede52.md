
# Algorithm 1 Learning algorithm of the FER model with the jointly lost loss functions

**Input:** training data $\{x_i\}$, mini-batch size $m$, number of iterations $T$, learning rates $\mu$ and $\gamma$, and hyper-parameters $\lambda$.

1. **Initialize:** Network layer parameters $W$, weighted-softmax loss parameters $\theta$, and weighted-cluster loss parameters (i.e., $\{\zeta_j | j = 1, 2, \dots, n\}$).
2. **for** $t = 1$ **to** $T$
3. **Calculate** the joint loss
4. $L^t = L^t_{\text{Weighted-softmax}} + \lambda L^t_{\text{Weighted-cluster}}$
5. **Compute** the backpropagation error for each $i$
6. $\frac{\partial L^t}{\partial x_i} = \frac{\partial L^t_{\text{Weighted-softmax}}}{\partial x_i} + \lambda \frac{\partial L^t_{\text{Weighted-cluster}}}{\partial x_i}$
7. **Update** the weighted-softmax loss parameters $\theta$
8. $\theta^{t+1} = \theta^t - \mu \frac{\partial L^t_{\text{Weighted-softmax}}}{\partial \theta}$
9. **Update** the weighted-cluster loss parameters $\zeta_j$, for $j$ as in Equation (9)
10. $\zeta_j^{t+1} = \zeta_j^t - \gamma \Delta\zeta_j$
11. **Update** the network parameters $W$
12. $W^{t+1} = W^t - \mu \frac{\partial L^t}{\partial W}$
13. **end for**

**Output:** Network layer parameters $W$

In this work, we consider the problem in recognizing eight common facial expressions from the AffectNet dataset [5]. The AffectNet dataset contains more than 1,000,000 images from the Internet that were obtained by querying search engines using emotion-related tags. AffectNet is by far the largest database that provides facial expressions in two different emotion models (a categorical model and a dimensional model), which can be used for studies in automated recognition of facial expressions, valences, and arousal in real-world scenarios. About 450,000 images already have manually annotated labels for eight basic expressions which are neutral, happy, sad, surprise, fear, disgust, anger, and contempt, as well as some non-emotion-related image classes such as none, uncertain, and non-face. Figure 2 shows some sample images from the dataset.

![](img/601340ca744b738277eef45ff127492a_311_0.png)

**Figure 2.** Sample images from the AffectNet dataset (0: neutral; 1: happy; 2: sad; 3: surprise; 4: fear; 5: disgust; 6: anger; 7: contempt).

In this work, only images of the eight common emotion classes (manually annotated) were used to train the FER model. From each of the emotion classes, we randomly selected 500 samples for a validation set and another 500 samples were selected for a test set. The remainder were used for fine-tuning the FER models. The numbers of samples in training, validation, and test sets are shown in Table 3.

**Table 3.** Numbers of samples in training, validation, and test sets.

| Emotion | Training | Validation | Test |
|---|---|---|---|
| Neutral | 74,374 | 500 | 500 |
| Happy | 133,915 | 500 | 500 |
| Sad | 24,959 | 500 | 500 |
| Surprise | 13,580 | 500 | 500 |
| Fear | 5,878 | 500 | 500 |
| Disgust | 3,303 | 500 | 500 |
| Anger | 24,362 | 500 | 500 |
| Contempt | 1,250 | 500 | 500 |
| Total | 283,651 | 4000 | 4000 |

Although AffectNet is considered one of the largest facial expression databases, it still has shortcomings when used for training FER models. This database is highly imbalanced, as can be seen in Figure 3. Specifically, the number of images in the largest category (happy with 134,915 images) is approximately 30 times larger than the smallest category (contempt, with 4250 images). Furthermore, images were manually annotated, which may result in a low-reliability dataset. Therefore, transfer learning is still needed to mitigate these drawbacks.

![](img/601340ca744b738277eef45ff127492a_312_0.png)

Figure 3. Distribution of the eight classes in the training set.

## 4.1.2. VGGFace2 Dataset

VGGFace2 [22] is a new large-scale dataset that contains 3.31 million images of 9131 subjects, with an average of 9131 subjects. Images were manually annotated. Figure 4 shows some sample images from VGGFace2.

![](img/601340ca744b738277eef45ff127492a_312_0.png)

Figure 4. Sample images from VGGFace2.

## 4.2. Evaluation Metrics

In this work, only images of the eight common emotion classes (manually annotated) were used to train the FER model. From each of the emotion classes, we randomly selected 500 samples for a validation set and another 500 samples were selected for a test set. The remainder were used for fine-tuning the FER models. The numbers of samples in training, validation, and test sets are shown in Table 3.

Although AffectNet is considered one of the largest facial expression databases, it still has shortcomings when used for training FER models. This database is highly imbalanced, as can be seen in Figure 3. Specifically, the number of images in the largest category (happy with 134,915 images) is approximately 30 times larger than the smallest category (contempt, with 4250 images). Furthermore, images were manually annotated, which may result in a low-reliability dataset. Therefore, transfer learning is still needed to mitigate these drawbacks.

In this work, we consider the problem in recognizing eight common facial expressions from the AffectNet dataset [5]. The AffectNet dataset contains more than 1,000,000 images from the Internet that were obtained by querying search engines using emotion-related tags. AffectNet is by far the largest database that provides facial expressions in two different emotion models (a categorical model and a dimensional model), which can be used for studies in automated recognition of facial expressions, valences, and arousal in real-world scenarios. About 450,000 images already have manually annotated labels for eight basic expressions which are neutral, happy, sad, surprise, fear, disgust, anger, and contempt, as well as some non-emotion-related image classes such as none, uncertain, and non-face. Figure 2 shows some sample images from the dataset.

To evaluate the performance of the FER model, we use various metrics such as accuracy, F1-score, Cohen's kappa, Krippendorff's alpha, AUC, and AUC-PR.

Table 4. List of acronyms.

| Abbreviation | Meaning |
|---|---|
| ResNet | Residual network |
| SE-ResNet | Squeeze and excitation neural network |
| Alpha | Krippendorff's alpha |
| Kappa | Cohen's kappa |
| AUC | Area under ROC curve |
| AUC-PR | Area under precision curve |

