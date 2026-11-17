
## Mitigate the risk of model attacks

The ML pipeline can be broadly divided into two phases: the training phase and the test phase. You can address various ML model attacks based on these phases.

## Training phase

A data scientist performs activities like data gathering, data cleansing, feature engineering, choosing suitable algorithms, hyperparameter tuning, and model building. Attackers target this phase via attacks like data poisoning. If a model is trained on poisoned data, you cannot rely on its predictions.

You can implement the following techniques to mitigate the risk of attacks during the training phase:

- Data encryption
- Protect the integrity of training data
- Robust statistics
- Data sanitization

## Test phase

In this phase, attackers target ML models. Model extraction attacks are common among attackers. They attempt to determine whether input X is part of training data or try to steal model parameters defined during the training phase.

The following techniques can be implemented to mitigate the risk during the test phase:

- Adversarial training
- Autoencoders
- Distillation
- Ensemble techniques
- Limit the number of requests per user

You can use a Python library Adversarial Robustness Toolbox (ART) and a command-line tool Counterfit for ML model security. This library will defend against the most common types of ML attacks. It also supports popular ML frameworks, libraries, and data types.

## A/B testing

A/B testing is widely used in marketing, website designs, and email campaigns to learn and understand user preferences. The goal of A/B testing is to increase the conversion rate, success rate, revenue, and so on.

A/B testing involves splitting the audiences or customers from the population into equal sets. These sets will route to the control version and the experimental version. The control version is the existing version, whereas the experimental version is the new or challenger version. First off, define the problem statement for the A/B test, the null hypothesis, and the alternative hypothesis for the problem statement. Next, design the experiment to track and analyze the metric, and then run and validate the experiment. After that, compare the statistics of the output. Finally, make the decision based on the results. If the A/B test is not performed correctly, then its output will be unreliable.

Data scientists perform an offline evaluation of ML models by dividing data into training and validation sets. However, the A/B test allows you to perform the online evaluation of ML models by measuring business metrics or success rates. The A/B test can be implemented when you perform operations on training data, such as scaling and normalizing or applying different algorithms, and hyper-parameters while model building. An MLOps engineer or a data scientist can deploy multiple models simultaneously to test models in production. Google Cloud (GCP) and Amazon SageMaker allow the deployment of multiple models into the production behind the same endpoint to decide which model is performing better from the business point of view.

A Multi-Armed Bandit (MAB) is an advanced version of A/B testing. It is more complex than the A/B test, as it uses ML algorithms while dynamically allocating more traffic to the better-performing version and less traffic to the underperforming version based on the data.

## MLOps is the future

The field of Machine Learning is booming. Industries are making ML a critical part of the business development process, and many new challenges are being addressed by the ML system.

MLOps can handle the complexity and scalability of ML models. Hence, the demand for MLOps is increasing across the industry. There is a shortage of MLOps engineers in the industry, as MLOps is an intersection of Machine Learning and software development. Companies need to set up separate teams for MLOps engineers, or they can upskill their data scientists to execute MLOps tasks. MLOps cut costs and reduce the manual efforts of the overall ML life cycle. This allows data scientists and ML engineers to focus on other productive tasks.

MLOps is getting more popular than DevOps. Your model may be performing well in the local environment; however, if it is not reaching end users or customers, then its business impact is low. More than 85% of ML models are not deployed into the production environment. MLOps engineers can fill the gap between research environments and the production environment. This is a highly demanding field, as data scientists alone are not enough to convert ML models to business value.

## Conclusion

In this chapter, you learned the importance of model security and studied the various attacks in the ML life cycle. Building ML models and MLOps solutions is not enough; data scientists should work on delivering business value from them. A/B testing and Multi-Armed Bandit (MAB) play crucial roles while comparing existing models against newer models in order to improve the overall outcome and business metric. Finally, you learned how MLOps demand is increasing in the industry.

## Points to remember

- Model security is an essential part of MLOps.
- A/B testing enables you to perform an online evaluation of ML models.
- Attackers can use the Black-box method or the White-box method while attempting an adversarial attack.
- A Python library Adversarial Robustness Toolbox (ART) and a command-line tool Counterfit can be used for ML model security.
- A Multi-Armed Bandit (MAB) is an advanced version of A/B testing. It is smart enough to decide which model should get more traffic by evaluating multiple models.

## Multiple choice questions

- 1. In ______, attackers intentionally send malicious data to the model so that the model makes incorrect predictions.
  - a) phishing
  - b) an adversarial attack
  - c) shoulder surfing
  - d) piggybacking

- 2. __________ refers to getting information about training data from the trained model by reverse engineering.
  - a) Extraction
  - b) Evasion
  - c) Inversion
  - d) Monitoring

## Answers

- 1. b
- 2. c

## Questions

- 1. What is a data poisoning attack?
- 2. What is A/B testing?
- 3. What are the different techniques that can be implemented to mitigate the model security risk during the training phase?

## Join our book's Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_450_0.png)

## Index

### Symbols

__init__ method 9

### A

- A/B testing 423, 424
- Activate Cloud Shell icon 313
- Adversarial Robustness Toolbox (ART) 423
- Amazon CloudWatch Container Insights 378
- Amazon Elastic Compute Cloud (EC2) 327
- Amazon Elastic Container Registry (ECR) 327, 336, 337
- Amazon Elastic Container Service (ECS) 327, 346
  - cluster 347
  - container 347
  - service 347
  - task 346
  - task definition 346, 349
- Amazon Elastic Kubernetes Service (EKS) 327
- Amazon SageMaker 328
- Amazon Simple Storage Service (S3) 328
- Amazon Virtual Private Cloud (Amazon VPC) 351, 352
- Amazon Web Services (AWS) 326
- Anaconda installing 2
- Application Load Balancer (ALB) 352, 358-362
- array 4
- AWS account setting up 329, 330
- AWS Application Load Balancer (ALB) 327
- AWS CodeBuild 339-344
  - container registry access, attaching to service role 345, 346
- AWS CodeCommit 331-335
- AWS CodePipeline 371, 372
  - build stage, adding 374
  - deploy stage, adding 375, 376
  - monitoring 378
  - running 376-378
  - settings 372
  - source stage, adding 373, 374
- AWS Command-Line Interface (CLI) 330
- AWS compute services 326, 327
- AWS ECS deployment models 347
  - EC2 instance 347, 348
  - Fargate 348, 349
- AWS Fargate 328
- AWS Lambda 328
- Azure 250, 251
  - deployment, with GitHub Actions 251-253
  - infrastructure setup 263
- Azure account
  - setting up 251
- Azure App Service
  - configuring, for using GitHub Actions for CD 274-278
  - creating 267-270
- Azure Container Instance (ACI) 289, 292, 297
- Azure Container Registry (ACR) 252, 263
  - creating 264-267
- Azure Kubernetes Service (AKS) 250, 292
- Azure Machine Learning (AML) service 249, 279
- Azure Machine Learning Studio
  - experiments 280
  - features 279
  - runs 280-289
  - workspace 280

### C

- CD pipeline
  - configuring 292-298
- CI/CD pipeline
  - building 189
  - codebase, developing 189-196
  - creating, with Jenkins 202
  - for ML 184, 185
  - GitHub Actions and Heroku, using 227
  - Personal Access Token (PAT), creating on GitHub 196
  - using, Cloud Build 317, 318
  - using, CodePipeline 369, 370
  - webhook, creating on GitHub repository 197, 198
- CI/CD pipeline, with Jenkins 202
  - deployment-status-email 210-217
  - GitHub-to-container 203-205
  - testing 207-210
  - training 205-207
- CI pipeline
  - configuring 290-292
- class 9
- Cloud Alert manager 401
- Cloud Build 309-311
  - trigger, creating 318-322
- Cloud Source Repositories 304-308, 317
- CloudWatch logs 345
