Once you have started the tuning process, there are two additional steps that you might want to check: tracking the process of tuning and selecting the winner model (that is, the one with the best set of hyperparameters).

In order to find your training jobs, you should go to the SageMaker console and navigate to Hyperparameter training jobs. You will then find a list of executed tuning jobs, including yours:

![](bbox=[0.125, 0.225, 0.875, 0.315])

Figure 9.11 – Finding your tuning job

If you access your tuning job, by clicking under its name, you will find a summary page, which includes the most relevant information regarding the tuning process. On the **Training jobs** tab, you will see all the training jobs that have been executed:

![](bbox=[0.125, 0.425, 0.875, 0.725])

Figure 9.12 – Summary of the training jobs in the tuning process

Finally, if you click on the **Best training job** tab, you will find the best set of hyperparameters for your model, including a handy button for creating a new model based on those best hyperparameters that have just been found: