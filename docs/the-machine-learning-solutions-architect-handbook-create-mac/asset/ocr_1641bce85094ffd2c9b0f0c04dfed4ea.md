# Building an Enterprise ML Architecture with AWS ML Services

| Resources |
| CodePipelineArtifactStoreBucket |
| Type: 'AWS::S3::Bucket |
| DeletionPolicy: Delete |
| Pipeline |
| Type: 'AWS::CodePipeline::Pipeline |
| ... |

+   2. Similarly, let us launch this cloud template in the CloudFormation console to create the pipeline definition for execution. Once the CloudFormation template has been executed, navigate to the CodePipeline management console to verify that it has been created. The CloudFormation execution will also execute the newly created pipeline automatically, so you should see that it already once run. You can test it again by clicking on the Release changes button in the SageMaker management console.

We want to be able to kick off the CodePipeline execution when a change is made (such as a code commit) in the CodeCommit repository. To enable this, we need to create a CloudWatch event that monitors this and kicks off the pipeline. Let's get started:

+   1. Add the following code block to the mlpipeline.yaml file, just before the Outputs section, and save the file as mlpipeline_1.yaml. You can find the complete file at https://github.com/PacktPublishing/The-Machine-Learning-Architect-Handbook/blob/main/Chapter09/mlpipeline_1.yaml:

| AmazonCloudChangeEventRole |
| Type: 'AWS::IAM::Role |
| Properties: |
| AssumeRolePolicyDocument: |
| Version: 2012-10-17 |
| Statement: |
| Effect: Allow |
| Principal: |
| Service: |
| events.amazonaws.com |
| Action: 'sts:AssumeRole |
| Path: / |
| Policies: |