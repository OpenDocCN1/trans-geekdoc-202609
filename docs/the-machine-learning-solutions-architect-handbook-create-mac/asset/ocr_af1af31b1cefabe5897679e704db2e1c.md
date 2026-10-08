# Designing an MLOps architecture for AI services

![](bbox=[0.145, 0.1, 0.854, 0.41])

Figure 1.2 - MLOps architecture for AI services on AWS

In this multi-account AWS environment, developers use the custom model development environment to build and test the pipelines for data engineering, model training, and model deployment. When ready, the pipelines are promoted for formal model building and testing using production training data in the model development environment. Since trained AI services models cannot normally be exported, we will need to replicate the model training workflow in the production environment for model deployment.

The shared services environment hosts CI/CD tools such as AWS CodePipeline and AWS CodeBuild to build different pipelines for data engineering, model building, and model deployment running in different environments. For example, a pipeline for the UAT environment could have the following components and steps:

+   - **CodePipeline definition:** This definition would have a CodeBuild step, a CloudFormation execution step, and a Step Functions workflow execution step.
- **CodeBuild step:** The CodeBuild step enriches the CloudFormation template with additional inputs needed to create a Step Functions workflow that orchestrates data engineering, dataset creation, data ingestion, model training, and model deployment.