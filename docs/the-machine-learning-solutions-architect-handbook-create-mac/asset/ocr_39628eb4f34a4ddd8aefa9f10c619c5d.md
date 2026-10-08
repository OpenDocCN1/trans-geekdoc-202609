```
mlflow.sklearn.autolog())
bank_churn_clf.fit(churn_train_X, churn_train_y)
mlflow.sklearn.log_model(sk_model=bank_churn_clf,
artifact_path="sklearn-model", registered_model_name="churn-
model")
```

```
print(f"MLflow run id: {run.info.run_id}")
return mlflow.run_id: {run.info.run_id}
```

```
train_model_op = components.func_to_container_op(
train_model,
base_image=BASE_IMAGE,
packages_to_install=('boto3', 'mlflow', 'scikit-learn',
'matplotlib'),
)
```

The preceding training step will register the model in the MLflow model registry. We will need to download a target model version and upload it to the S3 bucket for the deployment step. Add the following code block to the notebook, which will create a download_model_op component. Remember to replace model-deployment-<your initials> with your own bucket name, and replace <<your mlflow server>> with your own tracking server:

```
@dsl.python_component(
name='model_download_op',
description='model training step',
base_image=BASE_IMAGE # you can define the base image
here, or when you build in the next step.
)
```

```
def download_model(model_version: int, previous_output: str)
-> str :
    import mlflow
    import os
    import shutil
    import boto3
```

```
model_name = "churn-model"
model_version = model_version
```