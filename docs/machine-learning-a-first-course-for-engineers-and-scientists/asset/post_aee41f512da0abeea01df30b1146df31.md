
## 11 User aspects of machine learning

All available data

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_243_0.png)

Figure 11.4: Revising the training-validation-test data split by carving out a separate train-validation data from the training data.

### Extending the training data with slightly different data

As mentioned, there are situations where we can accept the training data from a slightly different distribution than the validation and test data. One reason to accept this is if we would have access to a substantially larger training dataset.

Consider a problem with 10,000 data points representing the data that we would also expect to get when the model is deployed in production. We call this Dataset A. We have another dataset with 200,000 data points that come from a slightly different distribution, but which is similar to what we think-so-called exploiting information from data can improve the model. We call this Dataset B. Some options to proceed with the following:

- **Option 1** Use only Dataset A and split it into training, validation, and test data.

Dataset A

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_243_1.png)

The advantage of this option is that we only train, validate, and evaluate on Dataset A, which is also the type of data we want our model to perform well on. The disadvantage is that we have quite few data points and we do not exploit potentially useful information in the larger Dataset B.

- **Option 2** Use both Dataset A and Dataset B. Randomly shuffle the data and split it in training, validation and test data.

Dataset A + B

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_243_2.png)

The advantage over option 1 is that we have more data available for training. However, the disadvantage is that we mainly evaluate the model on data from Dataset B, which we want our model to perform well on data from Dataset A.

- **Option 3** Use both Dataset A and Dataset B. Use data points from Dataset A for validation and test data and some in the training data. Dataset B only goes into the training data.

### 11.3 What if we cannot collect more data?

| Dataset B | Dataset A | Val. data | Test data |
|---|---|---|---|
| Training data | 2,500 | 2,500 |
| 200 000 from Dataset B | data set | data set |
| 5,000 from Dataset A | | | |

Similar to option 2, the advantage is that we have more training data in comparison to option 1 and in contrast to option 2 we now evaluate on data from Dataset A, which is the data we want our model to perform well on. However, one disadvantage is that training data no longer have the same distribution as the validation and test data.

From these three options we would recommend option 1 or 3. In which we exploit the information available in the larger Dataset B, but evaluate only on the data where we want the model to perform well (Dataset A). The main disadvantage is that training data no longer comes from the same distribution as the validation and test data. To quantify how big this mismatch has on the final performance, techniques described in Section 11.2 can be used. To push the model to do better on data from Dataset A during training, we can also consider giving data from an object weight higher than the cost function from Dataset B, or simply use the data points in Dataset A that belongs to the training data.

There is not guarantee that adding Dataset B to the training data improves the model. If the data is very different from Dataset A it can also harm, and we might be better off using Dataset A as suggested in option 1. Using option 2 is generally not recommended since we would then (in contrast to option 1 and 3) evaluate on data which is different from the one we want to perform on. Hence, if the data in Dataset A is scarce, prioritize putting the validation and test datasets.

### Data augmentation

Data augmentation is another approach to extend the training without the need to collect more data. In data augmentation we construct new data points. For example, rotation, flipping, noise addition, color shift and contrast. One should be aware that some transformations are invariant. For example, if we flip horizontally or vertically, we need to know if the label remains the same. Hence, if the data in Dataset A is scarce, prioritize putting the validation and test datasets.

### Transfer learning

Transfer learning is another technique that allows to exploit information from more data than we have. In transfer learning we use the knowledge from a model that has been trained on a different task and then apply that in solving a different, but slightly related, problem. Transfer learning is especially common for model structures such as the neural networks introduced in Chapter 6. Consider an application where we want to detect whether a type of skin cancer is malignant or for this task we have 100,000 labeled images. We call this Task A. Instead of training the full neural network from scratch on skin data, we can reuse an already pretrained network from another classification task (Task B), which preferably has been trained on a much larger dataset. Using the weights from the model trained for Task B and only train the last few layers for the data for Task A. The procedure is also displayed in Figure 11.6. The intuition is that the layers closer to the input acquaint tasks that are generic for all types of images, such as extracting lines, edges and corners in the, whereas the layers closer to the output are more specific to the particular problem.

In order for transfer learning to be we need the two tasks to have the same type of input (in the example above, images of the same domain). Further, for transfer learning to be an attractive option, the task we transfer from should have been trained on substantially more data than the task we transfer.

### Learning from unlabeled data

We can also improve our model by learning from an additional (typically much larger) dataset without outputs, so called unlabeled data. Two such methods are semi-supervised learning and

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_243_0.png)

Figure 11.4: Revising the training-validation-test data split by carving out a separate train-validation data from the training data.

### Extending the training data with slightly different data

As mentioned, there are situations where we can accept the training data from a slightly different distribution than the validation and test data. One reason to accept this is if we would have access to a substantially larger training dataset.

Consider a problem with 10,000 data points representing the data that we would also expect to get when the model is deployed in production. We call this Dataset A. We have another dataset with 200,000 data points that come from a slightly different distribution, but which is similar to what we think-so-called exploiting information from data can improve the model. We call this Dataset B. Some options to proceed with the following:

- **Option 1** Use only Dataset A and split it into training, validation, and test data.

Dataset A

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_243_1.png)

The advantage of this option is that we only train, validate, and evaluate on Dataset A, which is also the type of data we want our model to perform well on. The disadvantage is that we have quite few data points and we do not exploit potentially useful information in the larger Dataset B.

- **Option 2** Use both Dataset A and Dataset B. Randomly shuffle the data and split it in training, validation and test data.

Dataset A + B

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_243_2.png)

The advantage over option 1 is that we have more data available for training. However, the disadvantage is that we mainly evaluate the model on data from Dataset B, which we want our model to perform well on data from Dataset A.

- **Option 3** Use both Dataset A and Dataset B. Use data points from Dataset A for validation and test data and some in the training data. Dataset B only goes into the training data.

### 11.3 What if we cannot collect more data?

| Dataset B | Dataset A | Val. data | Test data |
|---|---|---|---|
| Training data | 2,500 | 2,500 |
| 200 000 from Dataset B | data set | data set |
| 5,000 from Dataset A | | | |

Similar to option 2, the advantage is that we have more training data in comparison to option 1 and in contrast to option 2 we now evaluate on data from Dataset A, which is the data we want our model to perform well on. However, one disadvantage is that training data no longer have the same distribution as the validation and test data.

From these three options we would recommend option 1 or 3. In which we exploit the information available in the larger Dataset B, but evaluate only on the data where we want the model to perform well (Dataset A). The main disadvantage is that training data no longer comes from the same distribution as the validation and test data. To quantify how big this mismatch has on the final performance, techniques described in Section 11.2 can be used. To push the model to do better on data from Dataset A during training, we can also consider giving data from an object weight higher than the cost function from Dataset B, or simply use the data points in Dataset A that belongs to the training data.

There is not guarantee that adding Dataset B to the training data improves the model. If the data is very different from Dataset A it can also harm, and we might be better off using Dataset A as suggested in option 1. Using option 2 is generally not recommended since we would then (in contrast to option 1 and 3) evaluate on data which is different from the one we want to perform on. Hence, if the data in Dataset A is scarce, prioritize putting the validation and test datasets.

### Data augmentation

Data augmentation is another approach to extend the training without the need to collect more data. In data augmentation we construct new data points. For example, rotation, flipping, noise addition, color shift and contrast. One should be aware that some transformations are invariant. For example, if we flip horizontally or vertically, we need to know if the label remains the same. Hence, if the data in Dataset A is scarce, prioritize putting the validation and test datasets.

### Transfer learning

Transfer learning is another technique that allows to exploit information from more data than we have. In transfer learning we use the knowledge from a model that has been trained on a different task and then apply that in solving a different, but slightly related, problem. Transfer learning is especially common for model structures such as the neural networks introduced in Chapter 6. Consider an application where we want to detect whether a type of skin cancer is malignant or for this task we have 100,000 labeled images. We call this Task A. Instead of training the full neural network from scratch on skin data, we can reuse an already pretrained network from another classification task (Task B), which preferably has been trained on a much larger dataset. Using the weights from the model trained for Task B and only train the last few layers for the data for Task A. The procedure is also displayed in Figure 11.6. The intuition is that the layers closer to the input acquaint tasks that are generic for all types of images, such as extracting lines, edges and corners in the, whereas the layers closer to the output are more specific to the particular problem.

In order for transfer learning to be we need the two tasks to have the same type of input (in the example above, images of the same domain). Further, for transfer learning to be an attractive option, the task we transfer from should have been trained on substantially more data than the task we transfer.

### Learning from unlabeled data

We can also improve our model by learning from an additional (typically much larger) dataset without outputs, so called unlabeled data. Two such methods are semi-supervised learning and

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_243_0.png)

Figure 11.4: Revising the training-validation-test data split by carving out a separate train-validation data from the training data.

### 11 User aspects of machine learning

All available data

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_243_0.png)

Figure 11.4: Revising the training-validation-test data split by carving out a separate train-validation data from the training data.

### Extending the training data with slightly different data

As mentioned, there are situations where we can accept the training data from a slightly different distribution than the validation and test data. One reason to accept this is if we would have access to a substantially larger training dataset.

Consider a problem with 10,000 data points representing the data that we would also expect to get when the model is deployed in production. We call this Dataset A. We have another dataset with 200,000 data points that come from a slightly different distribution, but which is similar to what we think-so-called exploiting information from data can improve the model. We call this Dataset B. Some options to proceed with the following:

- **Option 1** Use only Dataset A and split it into training, validation, and test data.

Dataset A

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_243_1.png)

The advantage of this option is that we only train, validate, and evaluate on Dataset A, which is also the type of data we want our model to perform well on. The disadvantage is that we have quite few data points and we do not exploit potentially useful information in the larger Dataset B.

- **Option 2** Use both Dataset A and Dataset B. Randomly shuffle the data and split it in training, validation and test data.

Dataset A + B

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_243_2.png)

The advantage over option 1 is that we have more data available for training. However, the disadvantage is that we mainly evaluate the model on data from Dataset B, which we want our model to perform well on data from Dataset A.

- **Option 3** Use both Dataset A and Dataset B. Use data points from Dataset A for validation and test data and some in the training data. Dataset B only goes into the training data.

### 11.3 What if we cannot collect more data?

| Dataset B | Dataset A | Val. data | Test data |
|---|---|---|---|
| Training data | 2,500 | 2,500 |
| 200 000 from Dataset B | data set | data set |
| 5,000 from Dataset A | | | |

Similar to option 2, the advantage is that we have more training data in comparison to option 1 and in contrast to option 2 we now evaluate on data from Dataset A, which is the data we want our model to perform well on. However, one disadvantage is that training data no longer have the same distribution as the validation and test data.

From these three options we would recommend option 1 or 3. In which we exploit the information available in the larger Dataset B, but evaluate only on the data where we want the model to perform well (Dataset A). The main disadvantage is that training data no longer comes from the same distribution as the validation and test data. To quantify how big this mismatch has on the final performance, techniques described in Section 11.2 can be used. To push the model to do better on data from Dataset A during training, we can also consider giving data from an object weight higher than the cost function from Dataset B, or simply use the data points in Dataset A that belongs to the training data.

There is not guarantee that adding Dataset B to the training data improves the model. If the data is very different from Dataset A it can also harm, and we might be better off using Dataset A as suggested in option 1. Using option 2 is generally not recommended since we would then (in contrast to option 1 and 3) evaluate on data which is different from the one we want to perform on. Hence, if the data in Dataset A is scarce, prioritize putting the validation and test datasets.

### Data augmentation

Data augmentation is another approach to extend the training without the need to collect more data. In data augmentation we construct new data points. For example, rotation, flipping, noise addition, color shift and contrast. One should be aware that some transformations are invariant. For example, if we flip horizontally or vertically, we need to know if the label remains the same. Hence, if the data in Dataset A is scarce, prioritize putting the validation and test datasets.

### Transfer learning

Transfer learning is another technique that allows to exploit information from more data than we have. In transfer learning we use the knowledge from a model that has been trained on a different task and then apply that in solving a different, but slightly related, problem. Transfer learning is especially common for model structures such as the neural networks introduced in Chapter 6. Consider an application where we want to detect whether a type of skin cancer is malignant or for this task we have 100,000 labeled images. We call this Task A. Instead of training the full neural network from scratch on skin data, we can reuse an already pretrained network from another classification task (Task B), which preferably has been trained on a much larger dataset. Using the weights from the model trained for Task B and only train the last few layers for the data for Task A. The procedure is also displayed in Figure 11.6. The intuition is that the layers closer to the input acquaint tasks that are generic for all types of images, such as extracting lines, edges and corners in the, whereas the layers closer to the output are more specific to the particular problem.

In order for transfer learning to be we need the two tasks to have the same type of input (in the example above, images of the same domain). Further, for transfer learning to be an attractive option, the task we transfer from should have been trained on substantially more data than the task we transfer.

### Learning from unlabeled data

We can also improve our model by learning from an additional (typically much larger) dataset without outputs, so called unlabeled data. Two such methods are semi-supervised learning and
