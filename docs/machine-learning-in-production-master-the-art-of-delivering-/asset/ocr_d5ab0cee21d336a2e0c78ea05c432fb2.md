You can create and set the experiment name using the CLI, as shown in the following figure.

```
mlflow.set_experiment("Loan_prediction")
```

```
(venv) suhas@ds:~/mlb/mlflow$ mlflow experiments create --experiment-name Loan_prediction
Created experiment 'Loan_prediction' with id 1
```

Figure 5.10: Creating a new experiment using the command

```
mlflow run . --experiment-name Loan_prediction
```

The following figure shows the output of the preceding command:

```
(venv) suhas@ds:~/mlb/mlflow$ mlflow run . --experiment-name Loan_prediction
2021/11/20 00:18:14 INFO mlflow.projects.utils: === Created directory /tmp/tmpkv82_lo6 for downloading remote URIs passed to arguments of type 'path' ===
2021/11/20 00:18:14 INFO mlflow.projects.backend.local: === Running command 'source /home/suhas/miniconda3/bin/../etc/profile.d/conda.sh && conda activate mlflow-b5055c7e7fba84943972ce6c6cd0d8f32c893b5ce 1>&2 && python train.py' in run with ID '40c8762545204d6ca12e726d091876cd' ===
2021/11/20 00:19:23 INFO mlflow.projects: === Run (ID '40c8762545204d6ca12e726d091876cd') succeeded ===
```

Figure 5.11: Output of ML project's run command

Run the following command in your terminal to run MLproject from the GitHub repository:

```
mlflow run https://github.com/suhas-ds/mlflow_loan_prediction
--experiment-name Loan_prediction
```

The following figure shows the output of the preceding command:

```
(venv) suhas@ds:~/mlb/mlflow$ mlflow run https://github.com/suhas-ds/mlflow_loan_prediction --experiment-name Loan_prediction
2021/11/20 00:08:47 INFO mlflow.projects.utils: === Fetching project from https://github.com/suhas-ds/mlflow_loan_prediction into /tmp/tmpsre4t5yp ===
Username for 'https://github.com': suhas-ds
Password for 'https://suhas-ds@github.com':
2021/11/20 00:09:20 INFO mlflow.projects.utils: === Created directory /tmp/tmpnb2xuisb for downloading remote URIs passed to arguments of type 'path' ===
2021/11/20 00:09:20 INFO mlflow.projects.backend.local: === Running command 'source /home/suhas/miniconda3/bin/../etc/profile.d/conda.sh && conda activate mlflow-b5055c7e7fba84943972ce6c6cd0d8f32c893b5ce 1>&2 && python train.py' in run with ID '2315c9aba4eb4e43836d83c19355d33e' ===
2021/11/20 00:10:32 INFO mlflow.projects: === Run (ID '2315c9aba4eb4e43836d83c19355d33e') succeeded ===
```

Figure 5.12: Running ML project from GitHub