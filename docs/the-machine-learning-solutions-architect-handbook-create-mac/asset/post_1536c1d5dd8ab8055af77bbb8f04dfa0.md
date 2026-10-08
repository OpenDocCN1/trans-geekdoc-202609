
## Hands-on exercise – building a data science architecture using open source technologies 225

```python
output: str ) -> str :
import os

import boto3
import mlflow
import pandas as pd
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
```

```python
s3 = boto3.client('s3', region_name=region)
response = s3.list_objects(Bucket=bucket, Prefix=key)

key = response['Contents'][0]['Key']
s3.download_file('datalake-demo-dyping', key, 'churn.csv')
```

```python
churn_data = pd.read_csv('churn.csv')
```

```python
# Split the dataset into training (80%) and testing (20%)
churn_train, churn_test = train_test_split(churn_data, test_size=0.2)
```

```python
churn_train_X = churn_train.loc[:, churn_train.columns != 'exited']
churn_train_y = churn_train['exited']
```

```python
churn_test_X = churn_test.loc[:, churn_test.columns != 'exited']
churn_test_y = churn_test['exited']
```

```python
tracking_uri = <<your mlflow tracking server url>>
```

```python
mlflow.set_tracking_uri(tracking_uri)
mlflow.set_experiment('Churn Experiment 3')
```

```python
with mlflow.start_run(run_name="churn_run 2") as run:
    bank_churn_clf = RandomForestClassifier(max_depth=2, random_state=0)
```

```python
mlflow.sklearn.autolog()
bank_churn_clf.fit(churn_train_X, churn_train_y)
mlflow.sklearn.log_model(sk_model=bank_churn_clf,
artifact_path="sklearn-model", registered_model_name="churn-model")
```

```python
print(f"MLflow run id: {run.info.run_id}")
return f"MLflow run_id: {run.info.run_id}"
```

```python
train_model_op = components.func_to_container_op(
train_model,
base_image=BASE_IMAGE,
packages_to_install=('boto3', 'mlflow', 'scikit-learn', 'matplotlib'),
)
```

The preceding training step will register the model in the MLflow model registry. We will need to download a target model version and upload it to the S3 bucket for the deployment step. Add the following code block to the notebook, which will create a download_model_op component. Remember to replace model-deployment-<your initials> with your own bucket name, and replace <<your mlflow server>> with your own tracking server:

```python
@dsl.python_component(
name='model_download_op',
description='model training step',
base_image=BASE_IMAGE # you can define the base image
here, or when you build in the next step.
)
```

```python
def download_model(model_version: int, previous_output: str)
-> str :
    import mlflow
    import os
    import shutil
    import boto3
```

```python
model_name = "churn-model"
model_version = model_version
```

## Hands-on exercise – building a data science architecture using open source technologies 227

```python
tracking_uri = <<your mlflow tracking server>>
```

```python
mlflow.set_tracking_uri(tracking_uri)
mlflow.set_experiment('Churn Experiment 3')
```

```python
sk_model = mlflow.sklearn.load_model(f"models:/{model_name}/{model_version}")
```

```python
mlflow.sklearn.save_model(sk_model, f"{model_name}_{model_version}")
```

```python
os.makedirs(f"sksver_{model_name}_release")
```

```python
src = f"{model_name}_{model_version}/model.pkl"
des = f"sksver_{model_name}_release/model.joblib"
```

```python
shutil.copyfile(src, des)
```

```python
targetbucket = "model-deployment-<your initials>"
prefix = f"mlflow-models/{model_name}_release"
```

```python
def upload_objects(src_path, bucketname):
    s3 = boto3.resource('s3')
    my_bucket = s3.Bucket(bucketname)
```

```python
for path, dirs, files in os.walk(src_path):
    dirs[:] = [d for d in dirs if not d.startswith('.')]
```

```python
    path = path.replace("\\", "//")
    directory_name = prefix + path.replace(src_path, "")
    for file in files:
        my_bucket.upload_file(os.path.join(path, file), 
            directory_name + "/" + file)
```

```python
upload_objects(des, targetbucket)
```

```python
print(f"target bucket: {targetbucket}, prefix: {prefix}")
return f"target bucket: {targetbucket}, prefix: {prefix}")
```

```python
model_download_op = components.func_to_container_op(
download_model,
base_image=BASE_IMAGE,
packages_to_install=['boto3', 'mlflow', 'scikit-learn'],
)
```

Now, we're ready to construct the pipeline definition. We construct the pipeline definition by using @dsl.pipeline decorator and defining a function that specifies the flow of the pipeline. To run the pipeline, we will need to add some permissions to the service account (default-editor) associated with the pipeline in order to deploy the model to the cluster. The right way to do this is to create a new role with proper permissions. For simplicity, we will reuse the existing cluster-admin role, which has all rules we need to deploy the model (default-editor). We will create clusterbinding.yaml. Run the following code block in CloudShell environment to create a .yaml file for the clusterrole object, and then run kubectl apply -f sa-binding.yaml to establish the binding:

```yaml
cat << EOF > sa-binding.yaml
apiVersion: rbac.authorization.k8s.io
kind: ClusterBinding
metadata:
  name: default-editor-binding
  namespace: admin
subjects:
  - kind: ServiceAccount
    name: default-editor
    namespace: admin
roleRef:
  kind: ClusterRole
  name: cluster-admin
  apiGroup: rbac.authorization.k8s.io
EOF
```

Next, we need to create a Seldon deployment file for the pipeline to use. Create a new file in your Jupyter environment called bank_churn_deployment.yaml, copy the code to it, and save. Make sure to replace <<S3 uri of model file>> before you save the file:

```yaml
apiVersion: machinelearning.seldon.io
kind: SeldonDeployment
metadata:
  name: bank-churn
spec:
  name: bank-churn
  predictors:
    name: classifier
    name: default
    replicas: 1
    implementation: <<S3 uri of model file>>
    envSecretName: aws-secret
EOF
```

Alright, we are now ready to construct the pipeline by running the following code block. Note that we will use AWS credentials in some of the steps. To securely manage the AWS credentials and pass them to the component, we need to create a new secret in the admin namespace before we build the pipeline. Run the following script in the CloudShell terminal, and then `kubectl apply -f aws_secret.yaml`. Remember to replace <<your AWS access key>> and <<your AWS secret key>> with your own keys:

```yaml
cat << EOF > aws_secret.yaml
apiVersion: v1
kind: Secret
metadata:
  name: aws-secret
  namespace: admin
type: Opaque
data:
  AWS_ACCESS_KEY_ID:<<your AWS access key>>
  AWS_SECRET_ACCESS_KEY: <<your AWS secret key>>
EOF
```

Now, construct the pipeline definition by running the following code block in a Jupyter cell. We will have four steps in this workflow:

- preprocess_data_task
- model_training_task
- model_download_task
- seldondeploy

For simplicity, we added the default values to the pipeline. Remember to replace <<aws region>> with your region:

```python
@dsl.pipeline(
name='bank churn pipeline',
description='Train bank churn model'
)
def preprocess_train_deploy(
    bucket: str = 'datalake-demo-dyping',
    glue_job_name: str = 'customer-churn-processing',
    region: str = <<aws region>>,
    tag: str = '4',
    model: str = 'bank_churn_model',
    model_version: int = 1
):
    preprocess_data_task = process_data_op(glue_job_name, region).apply(use_aws_secret('aws-secret', 'AWS_ACCESS_KEY_ID', 'AWS_SECRET_ACCESS_KEY', 'us-west-1'))

    model_training_task = train_model_op(bucket, 'ml-customer-churn/data/', region, preprocess_data_task.output).apply(use_aws_secret())

    model_download_task = model_download_op(model_version, model_training_task.output).apply(use_aws_secret())
```

```python
seldon_config = yaml.load(open("bank_churn_deployment.yaml"))
deploy_op = dsl.ResourceOp(
name="seldondeploy",
k8s_resource=seldon_config,
action="apply",
attribute_outputs={"name": "{.metadata.name}"})
```

```python
deploy_op.after(model_download_task)
```

The pipeline definition needs to be registered with the Kubeflow Pipelines service. To do this, we need to compile the preceding definition and save it into a file. Run the following code block in a new cell to compile the pipeline into a file:

```python
import kfp.compiler as compiler
```

```python
pipeline_filename = 'bank_churn_pipeline.tar.gz'
compiler.Compiler().compile(preprocess_train_deploy, pipeline_filename)
```

We are ready to register and run the pipeline by creating an experiment (which is used to organize all the end-to-end workflow runs for the different experiments) and run the pipeline using the run_pipeline() function. Note that we are also using MLflow to track the details for the model training step of the workflow:

```python
client = kfp.Client()
experiment = client.create_experiment(name='data_experiment',
namespace='admin')
```

```python
arguments = {'model_version':1}
pipeline_func = preprocess_train_deploy
run_name = pipeline_func.name + ' run'
run_result = client.run_pipeline(experiment.id, run_name,
pipeline_filename, arguments)
```
