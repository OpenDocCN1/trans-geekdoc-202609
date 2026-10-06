
# Obtaining Deep Learning Models for Automatic Classification of Leukocytes

Figure 13. Loss registered on the training dataset by the set of models trained with transfer learning for 100 epochs

![](img/c5cbbc72cd5e7b9be32079eac36d685c_39_0.png)

Figure 14. Accuracy registered on the training dataset by the set of models trained with transfer learning for 100 epochs

![](img/c5cbbc72cd5e7b9be32079eac36d685c_39_1.png)

# Obtaining Deep Learning Models for Automatic Classification of Leukocytes

In general, the percentage of correctness for each of the categories has similar values, with the exception of the ResNet50, where some discrepancy in the classification process can be verified.

## Models Trained From Scratch

In the models trained from scratch, it was necessary to train the entire network, being indispensable the specification of the number of classes or categories. The fact that it is necessary to train the whole network makes this training much more time consuming than training with transfer learning. Thus, the training of the eight networks took an average of 18 hours on the computational architecture used (referred previously). Each network took an average of 2 hours and 14 minutes to train for 100 epochs. The fastest network was VGG16 with 1 hour and 15 minutes and the slowest was the Xception with 3 hours and 24 minutes. Figure 15 shows the behavior of the models in terms of losses.

As shown in Figure 15, the models that obtained lower loss values were the Xception and the DenseNet201, with ResNet50 having the highest loss.

Figure 15. Loss registered on the training dataset by set of models trained from scratch for 100 epochs

![](img/c5cbbc72cd5e7b9be32079eac36d685c_40_0.png)

The training accuracies reflect the losses previously presented with results, similar to the losses and accuracies in the validation dataset.

Some variation in the hit percentages in each of the categories indicating that the models are not properly trained, given the number of training examples for each category being very similar.

# Obtaining Deep Learning Models for Automatic Classification of Leukocytes

## Models Trained With Transfer Learning vs. Models Trained From Scratch

In order to get a general idea of the performance of the set of trained models with transfer learning and models trained from scratch, the graph of Figure 16 shows the mean of the values of loss obtained by the set of models in training and validation datasets.

This graph reveals lower values of the loss values of the models trained from scratch when compared to the models with transfer learning, implying a better performance in both the training and validation dataset. The values of loss for models trained without transfer learning, are after 100 epochs, below 0.15, converging to 0 in the case of the training dataset. The models with transfer learning have mean values of loss of about 0.4 for the validation dataset and about 0.3 for the training dataset.

*Figure 16. Average training and validation losses obtained with the set of models for 100 epochs from scratch and with transfer learning

![](img/c5cbbc72cd5e7b9be32079eac36d685c_41_0.png)

High accuracies were also obtained with the models trained from scratch, with values above 95% in both training and validation sets. The models trained with transfer learning got results below 90% in the two datasets previously referred.

The reduction of the value of the loss is associated with several factors. The fact that the results show very low values for this metric may be due to the existence of overfitting, that model "memorized" the training examples, with the possibility of becoming inefficient in the test dataset. Overfitting also happens when regularization is not applied in complex models (where the number of parameters W, the set of weights is large) or the number of data N (number of examples) is too low. In the case of models trained from scratch, no regularization method was used because there were no modifications made to the models supplied by Keras API. In the models with transfer learning, a layer of dropout (dropout = 0.5) was used at the network's top.

Table 1 shows the results obtained by the models trained from scratch. At the end of the training, these models were tested in a dataset with images different from those used during the training and validation processes. From its observation, it is possible to verify that the percentage of correctness is very low. The set of models trained from scratch achieve an accuracy of 26.31% for the 4 categories of leukocytes, which means that the process has results similar to a random classification.

Table 1. Classification accuracy percentages on the test dataset for each of the neural networks trained from scratch for 100 epochs, on four types of

| Eosinophils | Lymphocytes | Monocytes | Neutrophils |
| :--- | :--- | :--- | :--- |
| DenseNet121 | 19.09 | 18.18 | 29.09 | 27.27 |
| DenseNet121 | 20.91 | 29.09 | 20.00 | 25.44 |
| DenseNet121 | 24.55 | 24.55 | 22.73 | 28.18 |
| InceptionV3 | 25.45 | 19.09 | 22.73 | 19.09 |
| ResNet50 | 20.91 | 23.64 | 26.36 | 20.91 |
| VGG16 | 26.36 | 21.82 | 27.27 | 27.27 |
| VGG19 | 26.36 | 24.55 | 21.82 | 28.18 |
| Xception | 25.45 | 26.00 | 30.00 | 30.91 |

From this, it is possible to reduce the probability of overfitting since training and validation results are very good, but the models cannot perform with high accuracy in images different from those were used in training. Table 2 shows the results obtained by the models with transfer learning in the test dataset. Models such as DenseNet achieved average high percentages above 97%. The worst-performing model is the ResNet50 with only 46.4%. This value is due to the choice of the optimizer, regularization, or the need for a higher number of training epochs.

Table 2. Classification accuracy percentages on the test dataset for each of the neural networks trained with transfer learning for 100 epochs, on four types of leukocytes

| Eosinophils | Lymphocytes | Monocytes | Neutrophils |
| :--- | :--- | :--- | :--- |
| DenseNet121 | 96.36 | 98.18 | 99.09 | 98.18 |
| DenseNet121 | 96.36 | 99.09 | 98.18 | 99.09 |
| DenseNet121 | 97.27 | 99.09 | 98.18 | 98.18 |
| InceptionV3 | 91.82 | 97.27 | 93.64 | 97.27 |
| ResNet50 | 34.18 | 82.73 | 40.91 | 23.64 |
| VGG16 | 78.18 | 86.36 | 86.36 | 90.00 |
| VGG19 | 81.82 | 90.00 | 80.00 | 88.18 |
| Xception | 95.45 | 97.27 | 96.36 | 97.27 |

# Obtaining Deep Learning Models for Automatic Classification of Leukocytes

VGG16 and VGG19 obtained results of approximately 85% on 100 epochs of training. InceptionV3 and Xception achieved 95% and 96.6% respectively.

From the observation of the obtained results, it is possible to realize that in spite of the initial indication that the models trained from scratch would obtain better performance (based on the best values of loss obtained during the training) didn't happen in the test dataset. This can be explained by the large complexity of the models compared to the dataset diversity. In addition to less time-consuming works, the models trained with transfer learning were more successful being able to perform more correct classifications in the test dataset, with an overall rate of 87.8%, compared to 26.3% of the models trained from scratch.

## Training of Models With Transfer Learning for 5000 Epochs

In an attempt to improve the performances of the models with transfer learning in the test dataset, training of the same models was done for 5000 epochs. Although the percentage of correctness was quite high in some models, it was verified that the training increased the percentage of the correctness of these networks slightly. The training of all models for 5000 epochs took 69 hours and 2 minutes (while for the 100 epochs, all models took 1 hour and 20 minutes). The network that took less time to train was the VGG16 with 4 hours and 56 minutes and the one that took most time to train was the Xception with 14 hours and 32 minutes.

Overall, the increase in the percentage of network setup between the set of trained models for 100 and 5000 epochs is 1.68%, from 87.81% in 100 training to 89.49% in 5000 epochs of training.

The networks that had already achieved hit averages 96% obtained minor improvements, although they should not be neglected. The DenseNet121 achieved slightly lower results than those obtained after training 100 epochs.

The networks that most benefited from the increase in the number of training epochs were the VGG16, the VGG19, and the Res50 with between 3% and 5%, although the Res50 remained very low hit percentages. There was a tendency to increase the validation loss in most of the models, which suggests that the models are performing overfitting, remarkable also for the high accuracy of training (very close to One). One could use a higher dropout value, increase decay and decrease the rate as a way to prevent overfitting.

Comparable to what was verified in training 100 epochs, the hit percentage for each of the categories has similar values, with the exception of the Res50 where one can see some discrepancy in the classification process.
