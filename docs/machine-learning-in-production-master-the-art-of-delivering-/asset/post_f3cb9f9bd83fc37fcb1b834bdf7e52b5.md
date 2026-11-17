
changes. Alternatively, you can use AWS CloudFormation or Terraform to automate the creation of infrastructure or services.

## Conclusion

In this chapter, you created an Amazon Elastic Container Service (ECS) cluster with Fargate to deploy the ML app. First off, you created an AWS account and created a codebase including a buildspec.yml file for Amazon Elastic Container Service (ECS) deployment. You added the Continuous Training stage in CI/CD pipeline and accuracy test cases in the pytest file. Next, you pushed the codebase and dependencies to AWS CodeCommit. After that, you created AWS Elastic Container Registry (ECR) to store and manage Docker container images, and you used AWS CodeBuild to build and push the Docker images to AWS Elastic Container Registry (ECR) using buildspec.yml. You created an Application Load Balancer (ALB) with a security and target group to distribute incoming traffic across the Fargate tasks, created ECS Service with a security group, and added an Application Load Balancer (ALB) to it. Finally, you created AWS CodePipeline and integrated these services to automate ML app deployment.

In the next chapter, you will study the drift in ML models and the monitoring process for the deployed model.

### Points to remember

- Amazon Elastic Container Service (ECS) offers deployment models: EC2 and Fargate.
- Application Load Balancer (ALB) can be specified at the time of service creation only.
- Application Load Balancer (ALB) checks the health of its registered targets (by default, the root path is set to '/'; however, it can be changed to a different path of application) and routes the traffic to healthy targets only.
- It is recommended to install and configure the latest version of AWS CLI and Docker on the local machine.
- Amazon ECS cluster is a logical grouping of tasks or services.
- Create one or more IAM users with the required permissions to run the services and avoid using root user to run the services directly.

### Multiple choice questions

- 1. __________ is serverless pay-as-you-go compute for containers.
  - a) EC2
  - b) Fargate
  - c) CloudWatch
  - d) Amazon Lightsail

- 2. The target group for load balancing __________
  - a) takes the request from Application Load Balancer (ALB)
  - b) routes the request to specified targets
  - c) handles dynamic IP of the tasks
  - d) all of the above

### Answers

- 1. b
- 2. d

### Questions

- What is a task in the Amazon ECS cluster?
- What is the use of an Application Load Balancer (ALB)?
- What are ECS services and their role?

### Join our book's Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_404_0.png)

## CHAPTER 14

### Introduction

So far, you have learned various techniques to deploy ML models in production. However, deploying a model into production is not the end; monitoring is the next important step. This chapter talks about concepts and techniques of model monitoring. Model monitoring is not limited to the final endpoint where the model is deployed; you should also integrate it into the intermediate stages wherever required. The static ML model is trained offline on historical data. However, this model may not deliver consistent performance forever. The main reasons could be changes in input data, business requirements, and model degradation over time.

### Structure

The following topics will be covered in this chapter:

- Importance of Monitoring
- Fundamentals of ML monitoring
- Metrics for monitoring your ML system
- Drift in ML - Types and detection techniques
- Operational monitoring using Prometheus and Grafana
- ML model monitoring with whylogs and WhyLabs

### Objectives

After studying this chapter, you can start monitoring ML models. You should be able to understand the importance and fundamentals of monitoring, decide on the metrics to monitor for your project and understand the concept of drift in ML, its types, and techniques to detect the drift. You should also be able to monitor drift in the data using whylogs, an open-source lightweight library, and WhyLabs, an observability platform. You should be able to integrate Prometheus and Grafana with FastAPI, and operational monitoring with open-source tools, that is, Prometheus and Grafana.

### Importance of monitoring

Once an ML model is deployed in production, it is essential to monitor it in order to ensure that the model's performance stays up to the mark and it continues to deliver reliable output seamlessly. As a matter of fact, there are many reasons for failure in ML apps or services, such as pipeline failure, model degradation over time, change in model input data, system or server failure, and change in the schema.

Multiple teams are involved while deploying models to production, which usually includes a team of Data Scientists, Data Engineers, and DevOps. If prediction errors increase, who will be held responsible? Who is the owner of the model in production?

Due to COVID-19, banks' ML model's performance was heavily affected. The model's predictions were far away from the actual figures. This is the case of a shift in input data. This should give you an overview of the challenges post-deploying models into production and the necessity of monitoring ML models.

Monitoring is essential when it comes to comparing new and old models' performance and their predictions over time. There could be latency issues, that is, delayed output. For tracking and investigating latency issues, efficient monitoring is needed. You need to monitor input data to ensure that production input data is being processed like the training data. To track and handle extreme values, out of the range values, or special cases before passing them to the models, monitoring is required. Last but not least is model security, that is, monitoring is required to track any external attack on the model or system.

The objectives of ML monitoring are as follows:

- To detect the issues or failures at early stages so that necessary steps can be taken
- To keep a track of resource usage and model prediction to evaluate model and system performance in the production environment
- To detect the change in distribution, schema, and anomalies in input data that may cause an error in the predictions
- To ensure the availability of model predictions and that they are explainable
- To track and store metrics in specified storage or database

Model monitoring helps data scientists to reduce model failures, avoid downtime, and ensure reliable outcomes for users.

### Fundamentals of ML monitoring

ML monitoring refers to tracking the performance, errors, metrics, and such of deployed models and sending alerts (when required) to ensure models continue performing above an acceptable threshold. It is not limited to tracking input data or model degradation. However, it should take all the things into account that may affect model performance directly or indirectly. ML monitoring helps decide whether an existing model needs to be updated.

The following are the essential steps to consider:

- **Monitoring is the key**: Monitoring is essential once a model is deployed in production. Monitoring enables you to track and fix issues or errors in a faster manner. Monitoring can be broadly divided into two types:
  - **Functional monitoring**: In the case of ML, functional monitoring refers to tracking metrics, errors, and performance related to ML models, such as accuracy and outliers.
  - **Operational monitoring**: Operational monitoring refers to tracking system-specific metrics, such as CPU and RAM utilization, uptime, and throughput.

- **Scalable integration**: Monitoring should be easy to integrate with your existing infrastructure and workflow. The monitoring system should be seamless and scalable to integrate. It should be able to track multiple models if there is more than one model. The monitoring solution should be platform agnostic so that it can be used for different types of deployment, having different tech stacks.

- **Metrics tracking**: Tracking accuracy is not enough. Monitoring systems should be able to track all the metrics that can affect model and system performance over time. A centralized monitoring system should use multiple performance metrics to give the overall status of the solution. Use different metrics for different types of features. For instance, min, max, mean, standard deviation, and outliers can be used for numerical data. The metrics records and logs need to be stored in a database so that they can be analyzed later on.
