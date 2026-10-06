# Obtaining Deep Learning Models for Automatic Classification of Leukocytes

modifications made to the models supplied by Keras API. In the models with transfer learning, a layer of dropout (dropout = 0.5) was used at the network's top.
Table 1 shows the results obtained by the models trained from scratch. At the end of the training, these models were tested in a dataset with images different from those used during the training and validation processes. From its observation, it is possible to verify that the percentage of correctness is very low. The set of models trained from scratch achieve an accuracy of 26.31% for the 4 categories of leukocytes, which means that the process has results similar to a random classification.

Table 1. Classification accuracy percentages on the test dataset for each of the neural networks trained from scratch for 100 epochs, on four types of

| Eosinophils | Lymphocytes | Monocytes | Neutrophils |
|---|---|---|--|
| DenseNet121 | 19.09 | 18,18 | 29.09 | 27,27 |
| DenseNet121 | 20.91 | 29.09 | 20,00 | 25,44 |
| DenseNet121 | 24,55 | 24,55 | 22,73 | 28,18 |
| InceptionV3 | 25,45 | 19,09 | 22,73 | 19,09 |
| ResNet50 | 20,91 | 23,64 | 26,36 | 20,91 |
| VGG16 | 26,36 | | 21,82 | 27,27 |
| VGG19 | 26,36 | 24,55 | 21,82 | 28,18 |
| Xception | 25,45 | 26,00 | 30,00 | 30,91 |

From this, it is possible to reduce the probability of overfitting during since since training and validation results are very good, but the models cannot perform with high precision classifications (or accuracy) in images different from those that were used in training.
Table 2 shows the results obtained by the models with transfer learning in the test dataset. Models, such as the DenseNet, achieved average high percentages (all 4 categories) above 97%. The worst-performing model Dense is the ResNet50 with only 46.4%. This value is due to the choice of the optimizer, for regularization, or the need for a higher number of training enhances. The networks

Table 2. Classification accuracy percentages on the test dataset for each of the neural networks trained with transfer learning for 100 epochs, on four types of leukocytes

| Eosinophils | Lymphocytes | Monocytes | Neutrophils |
|---|---|---|--|
| DenseNet121 | 96,36 | 98,18 | 99,09 | 98,18 |
| DenseNet121 | 96,36 | 99,09 | 98,18 | 99,09 |
| DenseNet121 | 97,27 | 99,09 | 98,18 | 98,18 |
| InceptionV3 | 91,82 | 97,27 | 93,64 | 97,27 |
| ResNet50 | 34,18 | 82,73 | 40,91 | 23,64 |
| VGG16 | 78,18 | 86,36 | 86,36 | 90,00 |
| VGG19 | 81,82 | 90,00 | 80,00 | 88,18 |
| Xception | 95,45 | 97,27 | 96,36 | 97,27 |