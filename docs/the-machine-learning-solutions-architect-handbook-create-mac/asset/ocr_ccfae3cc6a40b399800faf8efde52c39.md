By default, SageMaker tracks all training jobs and their associated metadata, such as algorithms, input training dataset URLs, hyperparameters, and output locations. Training jobs also emit system metrics and algorithm metrics to AWS CloudWatch for monitoring. Training logs are also sent to CloudWatch logs for inspection and analysis needs.

SageMaker training jobs also allow you to integrate with the SageMaker debugger service. The debugger service allows the training job to capture additional details, such as system metrics (for example, CPU/GPU memory, network, and I/O metrics), deep learning framework metrics (for example, model training metrics at different neural network layers), and model training tensors (for example, model parameters) and save them to S3. Real-time debugger evaluation rules can be configured to monitor these states and send out alerts when they meet a certain threshold. Some examples of the built-in evaluation rules are vanishing gradients and model overfitting.

# SageMaker Tuning

To optimize the model's performance, you also need to try different hyperparameters, such as a learning rate for gradient descent and model training. An algorithm can contain a large number of hyperparameters, and tuning them manually would be a highly labor-intensive task. The SageMaker Tuning service works with SageMaker training jobs to tune model training hyperparameters automatically.

The SageMaker Tuning service supports two types of hyperparameter tuning strategies:

+   **Random search:** This is where a random combination of values for the hyperparameters is used to train a model.

+   **Bayesian search:** This is where the hyperparameter search is treated like a regression problem, where the inputs for regression are the values of the hyperparameters and the output is the model performance metric once the model has been trained using the input values. The Tuning Tuning service uses the values that have been collected from the training jobs to predict the next set of values that would produce model improvement.

The SageMaker Tuning service works with SageMaker training jobs to optimize the hyperparameters. It works by sending different input hyperparameter values to the training jobs and picking the hyperparameter values that return the best metrics.