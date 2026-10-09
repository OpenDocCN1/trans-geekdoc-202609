# TABLE 10.7 Activity Recognition Results on the Aruba Dataset

Model Precision (%) Recall F-Measure (%) Accuracy (%)
NB 42.87 61.04% 50.36 84.37
HMM 43.66 72.03% 54.36 77.90
HSMM 43.97 71.56% 54.47 77.98
CRF 50.24 52.83% 51.50 88.58
LSTM 38.65 41.29% 39.92 89.00
CNN-1D 31.42 36.78% 33.89 87.50
CNN-2D 46.84 41.68% 44.11 89.67
CNN-2D + LSTM 51.20 50.55% 50.87 89.72

results (77.90% and 77.98% respectively). NB gives a better accuracy result (84.37%) than HMM and HSMM but it results in lower precision (42.87%) and recall (61.04%) rates. Although HMM and HSMM give the best recall rates (72.03% and 71.56%), they fail in giving good precision rates (43.66% and 43.97% respectively). We see that the CNN-1D network has an accuracy of 87.50% while it fails in high precision (31.42%) and recall (36.78%) values. CNN-1D extracts features on temporal dimension, it takes temporal information within a time-slice chunk into account but on the other hand, it ignores the relationship between sensors since it doesn't do convolution on the feature dimension. Thus, it doesn't learn class-specific feature maps to differentiate between different classes resulting in high accuracy (87.50%) but low precision and recall. When 2D convolution is used, both temporal information and spatial information are considered and the networks learn more informative features. Thus, it gains the ability to learn class-specific features, which results in higher precision and recall values (46.84% and 41.68%) and high accuracy results (89.67%). CNNs cannot remember the previous and the next inputs, but feeding the feature maps into an LSTM layer helps us process the temporal dimension further. As a result, CNN-2D + LSTM networks achieve a precision rate of 51.20%, a recall rate of 50.55% and an accuracy of 89.72%.

The learnt feature patterns are depicted in Figure 10.3. As the features are going to the next layers, it is seen that noise is reduced and features become clearer. The feature dimension is shown on the $x$-axis and the time axis is depicted on the $y$-axis while the white pixels show the activations.

Results on the Aruba dataset show that classifiers most successfully detect the instances of leave home and enter home activities since they are the only activities involving door sensors, thus they are not confused with any other activities. Moreover, meal preparation activity is confused with