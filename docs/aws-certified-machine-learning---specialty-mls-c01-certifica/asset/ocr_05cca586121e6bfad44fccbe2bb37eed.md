```
}
],
```

You also need to specify where the results will be stored:

```
"OutputDataConfig": {
  "S3OutputPath": "s3://{}/{}/output".format(bucket,prefix)
},
```

Finally, you set the resource configurations, roles, static parameters, and stopping conditions. In the following section of code, you want to use two instances of type ml.c4.2xlarge with 10 GB of storage:

```
"ResourceConfig": {
  "InstanceCount": 2,
  "InstanceType": "ml.c4.2xlarge",
  "VolumeSizeInGB": 10
},
"RoleArn": <<your_role_name>>,
"StaticHyperParameters": {
  "eval_metric": "auc",
  "num_round": "100",
  "objective": "binary:logistic",
  "rate_drop": "0.3",
  "tweedie_variance_power": "1.4"
},
"StoppingCondition": {
  "MaxRuntimeInSeconds": 43200
}
}
```

# IMPORTANT NOTE

*Please note that you are using other variables in this configuration file, bucket and prefix, which should be replaced by your bucket name and prefix key (if needed), respectively. You are also referring to s3_input_train and s3_input_validation, which are two variables that point to the train and validation datasets in S3.*

Once you have set your configurations, you can spin up the tuning process:

```
smclient.create_hyper_parameter_tuning_job(
  HyperParameterTuningJobName = "my-tuning-example",
  HyperParameterTuningJobConfig = tuning_job_config,
  TrainingJobDefinition = training_job_definition
)
```

Next, let's find out how to track the execution of this process.

# Tracking your training jobs and selecting the best model