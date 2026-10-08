
# ML pipeline monitoring

The ML pipeline's execution needs to be monitored for statuses and errors, so corrective actions can be taken as needed. During a pipeline execution, there are pipeline-level statuses/events as stage-level and action-level statuses/events. You can use these events and statuses to understand the progress of each pipeline and stage and get alerted when something is wrong. The following diagram shows how AWS CodePipeline, CodeBuild, and CodeCommit can work with CloudWatch, CloudWatch Logs, and EventBridge for general status monitoring and reporting, as well as problem troubleshooting:

![](img/bd21298357d48415447ff0b2f138b_303.png)

CodeBuild can send metrics, such as SucceededBuilds, FailedBuilds, and Duration metrics. These can be accessed through both the CodeBuild console and CloudWatch dashboard.

CodeBuild, CodeCommit, and CodePipeline can emit events to EventBridge to report status changes and trigger custom event processing, such as notifications, or log the events to another repository for archiving. All three services can send detailed logs to CloudWatch to support operations such as troubleshooting.

Step Functions provides a list of metrics to CloudWatch, such as execution metrics (such as execution failure, abort, timeout) and activity metrics (such as activity started, succeeded). You can view these metrics in the management console and set thresholds for alerts.

# Service provisioning

Another key component of enterprise ML platform is service provisioning. For large-scale provisioning and deployment, an automated process should be adopted. Here, we will focus on provisioning the ML platform itself, not provisioning AWS accounts and networking, which should be established as the base for ML platform provisioning. For ML platform provisioning, there are two main tasks:

- Data science environment provisioning: Provisioning the data science environment for scientists mainly includes provisioning tools for experimentation, as well as access to pre-built ML automation pipelines.
- ML automation pipeline provisioning: ML automation pipelines need to be provisioned in advance for data scientists and MLOps engineers to use them to automate tasks such as container training and model deployment.

There are multiple technical approaches to automate service provisioning on AWS, such as using scripts, CloudFormation, and AWS CDK. With scripts, you can sequentially call the AWS CLI commands to provision different components, such as creating a SageMaker notebook. CloudFormation is the IaC service for infrastructure deployment on AWS. With CloudFormation, you create templates that describe the desired resources and dependencies to be launched as a single stack. When the template is executed, all the resources and dependencies specified in the stack are deployed automatically. The following code shows the template for deploying a SageMaker domain:

```yaml
Type: AWS::SageMaker::Domain
Properties:
  NetworkAccessType: String
  AuthMode: String
  UserSettings:
    DomainName: String
  KmsKeyIds: String
  Subnets:
    - String
  VpcId: String
```

AWS CDK allows you to create different products to be deployed on AWS. These products can include SageMaker notebooks, a CodeCommit repository, and CodePipeline definitions. AWS CDK uses CloudFormation templates to describe products. With AWS CDK, administrators create products with templates, organize these products by portfolio, and entitle end users with access. The end users access the products from the CDK portfolio. The following diagram shows the flow of creating a CDK product and launching it from the CDK service:

![](img/bd21298357d48415447ff0b2f138b_305.png)

For large-scale and governed product management, CDK is the recommended approach. CDK supports multiple deployment options, including single AWS account and hub-and-spoke deployments. A hub-and-spoke deployment allows you to centrally manage all products and make them available in different accounts. In our enterprise reference architecture, we use the hub-and-spoke architecture to support the provisioning of data science environments and ML pipelines, as shown in the following diagram:

![](img/bd21298357d48415447ff0b2f138b_306.png)

Figure 9.9 – The hub-and-spoke architecture for enterprise ML product management. In the preceding architecture, we use the central portfolio in the shared services account. All the products, such as creating SageMaker domains, user profiles, CodePipeline definitions, and training pipeline definitions, are centrally managed in the hub account. Some products are shared with different data science accounts to create environments for scientists and teams. Some other products are shared with training accounts for standing up ML pipelines.

With that, we have talked about the core components of an enterprise-grade ML platform. Next, let's get hands-on and build a pipeline to automate model training and deployment.

# Hands-on exercise – building an MLOps pipeline on AWS

In this hands-on exercise, you will get hands-on building a simplified version of the enterprise MLOps pipeline. For simplicity, we will not be using the multi-account architecture for the enterprise pattern. Instead, we will build several core functions in a single AWS account. The following diagram shows what you will be building:

![](img/bd21298357d48415447ff0b2f138b_307.png)

Figure 9.10 – Architecture of the hands-on exercise

At a high level, you will create two pipelines using CloudFormation: one for model training and one for model deployment.

## Creating a CloudFormation template for the ML training pipeline

In this section, we will create two CloudFormation templates that do the following:

- The first template creates AWS Step Functions for an ML model training workflow that performs data processing, model training, and model registration. This will be a component of the training pipeline.
- The second template creates a CodePipeline ML model training pipeline definition with two stages:
    - A source stage, which listens to changes in a CodeCommit repository to kick off the execution of the Step Functions workflow that we created
    - A deployment stage, which kicks off the execution of the ML model training workflow

Now, let's get started with the CloudFormation template for the Step Functions workflow:

- Create a Step Functions execution role called `AmazonSageMaker-StepFunctionsWorkflowExecutionRole`. Then, create and attach the following IAM policy to it. This role will be used by the Step Functions workflow to provide permission to invoke the SageMaker APIs. Take note of the ARN of the newly created IAM role you will need for the next step. You can find the complete code sample at https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook/blob/main/Chapter09/AmazonSageMaker-StepFunctionsWorkflowExecution-policy.json:

```json
{
  "Version" : "2012-10-17",
  "Statement": [
    {
      "Effect" : "Allow",
      "Action": [
        "sagemaker:CreateModel",
        "sagemaker:DeleteEndpointConfig",
        "sagemaker:DescribeTrainingJob",
        "sagemaker:CreateEndpoint",
        "sagemaker:StopTrainingJob",
        "sagemaker:CreateTrainingJob",
        "sagemaker:UpdateEndpoint",
        "sagemaker:CreateEndpointConfig",
        "sagemaker:DeleteEndpoint"
      ],
      "Resource" : [
        "arn:aws:sagemaker*:*:*:*"
      ]
    }
  ]
}
```
