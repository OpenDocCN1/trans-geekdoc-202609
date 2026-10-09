+   * Start Instance: Navigate to the EC2 Dashboard in the AWS Management Console. Select the instance you want to start, and from the “Actions” dropdown menu, choose “Instance State” ► “Start instance.”

+   * Stop Instance: Similarly, to stop an instance, select it from the EC2 Dashboard, and from the “Actions” dropdown menu, choose “Instance State” ► “Stop instance.”

+   * Note: If you don’t stop the instance after you are done with your work, charges will incur. Ensure to stop the instance when it’s no longer needed to avoid unnecessary costs.

By following these steps, you will successfully provision an Amazon EC2 instance.

You can also automate these steps using Amazon CloudFormation—a tool that allows you to define and provision your cloud infrastructure using a simple text file. The script below, e.g., leverages Amazon CloudFormation to automate the creation of an EC2 instance with a t2.xlarge instance type, 40 GB gp3 EBS volume, and a security group allowing SSH access:

```
```yaml
[In]: AWSTemplateFormatVersion: "2010-09-09"
[In]: Description: Provision a t2.xlarge EC2 instance with a 40 GB gp3
     EBS volume for deep learning tasks

[In]: Resources:
      DeepLearningEC2Instance:
        Type: AWS::EC2::Instance
        Properties:
          InstanceType: t2.xlarge
          KeyName: instance1keypair.pem
```
```