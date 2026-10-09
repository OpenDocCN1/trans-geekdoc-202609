# Step 5: Define Task Dependencies

In this final step, we define dependencies between tasks:

```
[In]: preprocess_task >> train_task >> evaluate_task
```

This line of code defines the task dependencies within the Airflow DAG:

+   -   preprocess_task >> train_task >> evaluate_task: This line specifies the order in which tasks should be executed. It uses the >> operator to define dependencies between tasks.
-   preprocess_task: This task represents the preprocessing step, which must be completed before proceeding to the next step.
-   train_task: This task represents the training of the TensorFlow model. It depends on the completion of the preprocessing task (preprocess_task). Once the preprocessing is done, the training can begin.
-   evaluate_task: This task represents the evaluation of the TensorFlow model. It depends on the completion of the training task (train_task). Once the training is completed, the model can be evaluated.

This step ensures that the tasks are executed in the correct order: preprocessing data, then training the TensorFlow model, and finally evaluating its performance. It establishes the workflow within the Airflow DAG.

To execute the code on the AWS EC2 instance, we first activated the virtual environment named “myenv” to ensure that the necessary dependencies are available. Next, we navigated to the directory where