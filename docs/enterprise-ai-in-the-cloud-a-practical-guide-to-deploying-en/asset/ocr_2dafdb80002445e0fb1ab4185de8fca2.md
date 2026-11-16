![](bbox=[0.125, 0.088, 0.875, 0.205])

# FIGURE 17.9: Validation across ML model development phases

# During Model Training

During the model training phase, you can break down the dataset into training and validation datasets. Once the training is completed using the training dataset, you can validate the model on the validation dataset and optimize the model parameters accordingly to prevent overfitting.

# During Model Tuning

During the model tuning process, you will choose the combination of the hyperparameters using techniques such as a grid or random search that optimizes the validation metrics.

# During Model Evaluation

Once the model is trained and tuned, you can then evaluate the model using the validation metrics on the test dataset. It helps you to understand how well the model will perform on new, unseen data.

> **TIP** Validation metrics are used to measure the model performance in a quantifiable manner during different phases of the model development lifecycle. During model building, use them to choose the right model; during training, use them to ensure learning is on the right track; during tuning, use them to choose the right hyperparameters; and during evaluation, use them to finalize the model.

# Validation Metrics for Classification Problems