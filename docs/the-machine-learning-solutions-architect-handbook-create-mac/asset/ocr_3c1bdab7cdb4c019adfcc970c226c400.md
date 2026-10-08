```
AWS_ACCESS_KEY_ID:<<your AWS access key>>
AWS_SECRET_ACCESS_KEY: <<your AWS secret key>>
EOF
```

Now, construct the pipeline definition by running the following code block in a Jupyter notebook cell. We will have four steps in this workflow:

+   - preprocess_data_task
- model_training_task
- model_download_task
- seldondeploy

For simplicity, we added the default values to the pipeline. Remember to replace <<aws region>> with your region:

```
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