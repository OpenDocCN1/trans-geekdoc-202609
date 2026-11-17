+   • **Annotations and descriptions:** You can add comments, short descriptions, and annotations for models. Your team members will come to know about the model through the descriptions you add.

# Start the MLflow server

All the required steps to start the MLflow server with MySQL as a database have been completed.

To start the MLflow server, you can use the following command:

```
mlflow server --host 0.0.0.0 --port 5000   --backend-store-uri mysql://
mlflow_user:mlflow@localhost/db_mlflow   --default-artifact-root $PWD/mlruns
```

The syntax to start the MLflow server is mlflow server <args>. In the preceding command, MLflow uses the backend store as MySQL server (provide MLflow username and database name) and the default artifacts store as the mlruns directory.

You can run the MLproject and pass the experiment name as a parameter (optional).

```
mlflow run . --experiment-name 'Loan_prediction'
```

You can see, in the MLflow UI, that the version column shows alphanumeric values. The model's metrics parameters are displayed under the Loan_prediction experiment.

The following figure shows the output of the Loan_prediction experiment using MySQL as a backend store:

![](bbox=[0.132, 0.599, 0.868, 0.908])

# Figure 5.22: Output of ML project on MLflow UI