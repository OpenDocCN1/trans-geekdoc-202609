
- AWS Elastic Container Registry (ECR)
- AWS CodeCommit
- Amazon Elastic Container Service (ECS)
- AWS CodeBuild
- Application Load Balancer (ALB)
- Deploy web-based ML app to Elastic Container Service (ECS) with service and Application Load Balancer (ALB)
- AWS CodePipeline
- Build an automated CI/CD CodePipeline to deploy a web-based ML app on Amazon Web Services (AWS)

## Objectives

After studying this chapter, you should be able to deploy an ML model on Amazon Elastic Container Service (ECS) without the need to integrate any external tool, service, or platform except AWS. You will create a remote Git repository on AWS using AWS CodeCommit and Amazon Elastic Container Service (ECS) cluster to run scalable ML apps. You will also learn to integrate Application Load Balancer (ALB) with Amazon Elastic Container Service (ECS) for routing requests coming from the external world. Moving on, you will integrate the service port with the Docker port via port mapping, create a security group for Application Load Balancer (ALB) and learn to push the Docker container image to AWS Elastic Container Registry (ECR). You should be able to create a fully automated CI/CD pipeline with AWS CodePipeline, AWS CodeBuild, AWS Elastic Container Registry (ECR), Application Load Balancer (ALB), and Amazon Elastic Container Service (ECS) after completing this chapter.

## Introduction to Amazon Web Services (AWS)

Amazon Web Services (AWS) is a cloud infrastructure where you can host applications. In 2006, AWS started offering IT services to the market in the form of web services. AWS is one of the leading cloud service providers.

## AWS compute services

Amazon Web Services (AWS) offers compute services for managing workloads that comprise many servers or instances.

Here are some of the widely used compute services offered by AWS that can be used as per the business or application requirements. These services will be discussed later in the chapter.

## Amazon Elastic Compute Cloud (EC2)

Amazon EC2 is a virtual machine that represents a remote server. Amazon EC2 service is grouped under **Infrastructure-as-a-Service (IaaS)**. Amazon EC2 enables applications with resizable computing capacity, and these EC2 machines are known as instances. You can create multiple instances with different computing sizes. You can even upgrade the RAM, vCPU, and so on after creation, so you do not need to recreate a new instance and configure it again. This is why the elastic term is used.

## Amazon Elastic Container Service (ECS)

Amazon **Elastic Container Service** (**ECS**) enables you to deploy, scale, and manage containerized applications. It manages containers and enables developers to run containerized applications across the cluster of EC2 instances. However, it is not based on Kubernetes. Amazon ECS is free, meaning you don't need to pay for the ECS cluster. However, additional charges are to be paid for EC2 instances running in ECS tasks. There are mainly two ways to launch an ECS clusters:

- Fargate Launch
- EC2 Launch

Amazon ECS is a technology owned exclusively by AWS. ECS easily integrates with AWS **Application Load Balancer (ALB)** and **Network Load Balancer (NLB)**.

## Amazon Elastic Kubernetes Service (EKS)

Amazon **Elastic Kubernetes Service** (**EKS**) is a Kubernetes service backed by AWS, which enables you to build Kubernetes clusters on AWS without manually installing Kubernetes on EC2. Amazon Elastic Kubernetes Service (EKS) allows you to manage or orchestrate containers in a Kubernetes environment. You need to pay for the EKS cluster, with additional charges for EC2 instances running inside the Kubernetes pod. Amazon EKS service set up and manages the Kubernetes control plane for you.

It is a good choice if you are looking for multi-cloud functionality and additional features compared to the Amazon **Elastic Container Service** (**ECS**).

## Amazon Elastic Container Registry (ECR)

Amazon **Elastic Container Registry** (**ECR**) allows developers to store, share and deploy Docker images on Amazon ECS. It provides security to images stored in it. Amazon Elastic Container Registry (ECR) is integrated with Amazon ECS. It is similar to the Docker Hub container registry but is managed by AWS. It allows you to store private Docker container images in it.

## AWS Fargate

Simply put, AWS Fargate is a serverless compute for containers. You pay for the usage per minute for the resources used by containers like virtual CPU (vCPU) and memory. AWS Fargate is compatible with both Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS).

## AWS Lambda

AWS Lambda is simple and less expensive. It is a serverless and event-driven compute service; it is a Function as a Service (FaaS). That means you don't need to manage servers or clusters. Events could be any simple activity, such as a user clicking on links to get the latest news. The term Lambda is supposed to be borrowed from functions of lambda calculus and programming. Mostly, it comprises three components:

- A function: It is the actual code to perform the task.
- A configuration: It dictates the execution of a function.
- An event source: This is the event that triggers the function. However, this component is optional.

AWS Lambda is a good choice for event-driven programming or when you need to access several services.

## Amazon SageMaker

AWS also provides a machine learning platform as a service, that is, Amazon SageMaker. It removes the overhead of managing and maintaining servers manually. It also reduces the time and cost of machine learning model deployment on the AWS cloud.

Amazon SageMaker is a cloud-based machine learning platform that enables data scientists and developers to build, train, tweak, and deploy machine learning models in production environments. It uses Amazon Simple Storage Service (S3) to store the data and comes with over 15 most commonly used built-in machine learning algorithms for training the data. It deploys the ML models to SageMaker endpoints. Amazon SageMaker uses the Amazon Elastic Container Registry (ECR) to store container images.

You must have got the gist of AWS and its services. You are going to deploy a Machine Learning model to the Amazon Elastic Kubernetes Service (EKS). After this chapter, you will be comfortable working on AWS for ML model deployment.

## Set up an AWS account

First of all, set up an AWS account; however, this is a one-time activity. It is ready to use immediately on log in.

The AWS Free Tier provides customers the ability to explore and try out AWS services free of charge up to specified limits for each service. The Free Tier consists of three different types of offerings, a 12-month Free Tier, an Always Free offer, and short-term trials.

### Step 1: Create or log in to the existing AWS account

Create an AWS account (if you don't have one) and sign in. A free trial account can be created on the AWS platform at https://aws.amazon.com/free.

First, click on the Create a Free Account button. Next, provide the login details, such as email ID, password, and AWS account name. Then, select the account type (Professional or Personal) and provide contact information. After that, provide PAN and payment details. Finally, complete the verification process on the identity verification page.

After a few minutes, the account will be activated and ready to use. Select a plan as per your requirements.

### Step 2: Create an IAM user and provide the required permissions

After signing in to the AWS Management Console, open the IAM console - https://console.aws.amazon.com/iam/. IAM stands for Identity and Access management. Next, click on Users in the navigation pane and choose Add users. Then, provide the user name for that user and choose the access type. After that, select the existing policies from the attached existing policies or create a new one for that user. In this scenario, Administrator access is given to the IAM user. Tags are optional. Finally, review and complete the process. Do not forget to save the user details like Access key ID, Secret access key, and user name. In this case, an IAM user will be used to execute all the tasks. Hit the Create user button and complete the process.
