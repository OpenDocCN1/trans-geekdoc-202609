```
train_op = SageMakerTrainingOperator(
  task_id='tf_training',
  config=train_config,
  wait_for_completion=True,
  dag=dag)
```

SageMaker also has a built-in workflow automation tool called SageMakerPipelines. A training step can be created using the SageMaker TrainingStep API and become part of the larger SageMaker Pipelines workflow.

# Model training life cycle management

SageMaker training manages the life cycle of the model training process. It uses AWS IAM as the mechanism to authenticate and authorize access to its functions. Once authorized, it provides the desired infrastructure, deploys the software stacks for the different model training requirements, moves the data from sources to training nodes, and kicks off the training job. Once the training job has been completed, model artifacts are saved into an S3 output bucket and the infrastructure is torn down. For lineage tracking, training metadata such as source datasets, model training containers, hyperparameters, and model outputs are captured. Any logging from the job runs is saved in CloudWatch Logs, and system metrics such as CPU and GPU utilization are captured in CloudWatch metrics.

Depending on the overall end-to-end ML platform architecture, a training environment can also host services for data preprocessing, model validation, and model training postprocessing, as those are important steps in an end-to-end ML flow. There are multiple technology options available for this, such as the SageMaker processing service and AWS Lambda.

# Model hosting environment deep dive

An enterprise-grade model hosting environment needs to support a broad range of ML frameworks in a secure, performant, and scalable way. It should come with a list of pre-built inference engines that can serve models out of the box behind a RESTful API or via the grpc protocol. It also needs to provide flexibility to host custom-built inference engines for unique requirements. Users should also have access to different hardware devices, such as CPU, GPU, and purpose-built chips, for the different inference needs.