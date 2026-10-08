Table 5. Accuracy of the conventional methods. (DT; Decision Tree, kNN; k-Nearest Neighbors, LF; Logistic Regression, RF; Random Forest, SVM; Support Vector Machine)

| Stressor | Classifier | Window Length (s) | |
|---|---|---|---||
| | | 10 | 30 | 60 |
| MA | DT | 0.539 (0.050) | 0.517 (0.062) | 0.490 (0.062) |
| | kNN | 0.497 (0.029) | 0.511 (0.040) | 0.535 (0.058) |
| | LR | 0.495 (0.021) | 0.537 (0.076) | 0.508 (0.055) |
| | SVM | 0.512 (0.075) | 0.560 (0.062) | 0.513 (0.041) |
| | DT | 0.488 (0.210) | 0.457 (0.234) | 0.512 (0.208) |
| | kNN | 0.561 (0.051) | 0.425 (0.150) | 0.451 (0.208) |
| | LR | 0.447 (0.188) | 0.443 (0.235) | 0.434 (0.225) |
| | RF | 0.528 (0.187) | 0.486 (0.215) | 0.523 (0.193) |
| | SVM | 0.514 (0.155) | 0.533 (0.177) | 0.498 (0.205) |

# 3.1. Feature Representation

We observed the features from each stage using the t-SNE method, which converts high-dimensional features (the number of components, width, and channel) to 2-dimensional features, which we can analyze using a scatter plot. Figure 3 shows the t-SNE scatter plots for the input (raw ECG) and the extracted features from each stage. The input is from a subject who participated in the mental arithmetic task and is sliced using a 10 min window. The proposed model, trained by Type III classification, generated features for each stage. As shown in Figure 3, there was almost no difference between the stress- and rest-labeled ECGs. By considering the features that passed through the stages, a distinction could be observed between the labels. The t-SNE plots imply that it is possible to distinguish the two labels clearly the softmax classifier after the last stage.

![](bbox=[0.24, 0.57, 0.76, 0.804])

Figure 3. The t-SNE plots of raw ECG and extracted features from stages. Round points denote features of ECG labeled as rest, and crosses represent stress-labeled features. This figure shows only the extracted features from stage 1, stage 5, and the last stage.