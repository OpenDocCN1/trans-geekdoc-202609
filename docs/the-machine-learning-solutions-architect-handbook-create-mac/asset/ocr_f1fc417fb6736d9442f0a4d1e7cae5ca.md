```
sagemaker_session = sagemaker.Session ()
bucket = <bucket name>
prefix = "sagemaker/pytorch-bert-financetext"
role = sagemaker.get_execution_role()
```

```
inputs_train = sagemaker_session.upload_data("./data/train.csv", bucket=bucket, key_prefix=prefix)
inputs_test = sagemaker_session.upload_data("./data/test.csv", bucket=bucket, key_prefix=prefix)
```

Finally, we must up the SageMaker PyTorch estimator and kick off the training. Note that you can also specify the PyTorch framework version and Python version to set the container. For simplicity, we are passing the name of the training file and test file, as well as max length, hyperparameters. The train.py file can also be modified to look them up dynamically:

```
from sagemaker.pytorch import PyTorch
output_path = f"s3://{bucket}/{prefix}",
```

```
estimator = PyTorch(
entry_point="train.py',
source_dir="code",
role=role,
framework_version="1.6",
py_version="py3",
instance_count=1,
instance_type="ml.p3.2xlarge",
out_path=output_path,
hyperparameters{
    "epochs": 4,
    "lr": 5e-5,
    "num labels": 3,
    "train_file": "train.csv",
    "test file": "test.csv",
    "MAX_LEN": 315,
    "batch-size": 16,
    "test-batch-size": 10
}
```