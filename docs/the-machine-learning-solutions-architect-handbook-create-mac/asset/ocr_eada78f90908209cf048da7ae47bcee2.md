# Hands-on exercise – building an MLOps pipeline on AWS 295

| PolicyName: cwe-pipeline-execution |
| PolicyDocument: |
| ... |

+   1. Now, run this CloudFormation template to create a new pipeline. You can delete the previously created pipeline by deleting the CloudFormation stack. This will run the pipeline again automatically until the pipeline's execution is complete before you start the next step.

+   3. Now, let's test the automatic execution of the pipeline by committing a change to the code repository. Create a new file named pipelinetest.txt and commit the change to the code repository. Navigate to the CodePipeline console; you should see the codecommit-events-pipeline starting to run.

Congratulations! you have successfully used CloudFormation to build a Based ML training pipeline that automatically runs when there is a file change in CodeCommit repository. Next, let's build the ML deployment pipeline for the model.

# Creating a CloudFormation template for the ML deployment pipeline

To start a deployment, perform the following steps:

+   1. Copy the following code block to create a file named mldeployment.yaml. This CloudFormation template will deploy a model using the SageMaker hosting service. Make sure that you enter the correct model name for your environment:

| Description: Basic Hosting of registered model |
| Parameters: |
| ModelName: |
| Description: Model Name |
| Type: String |
| Default: <mode name> |
| Resources: |
| Endpoint: |
| Type: AWS::SageMaker::Endpoint |
| Properties: |
| EndpointConfigName: !GetAtt EndpointConfig |
| EndpointConfig |