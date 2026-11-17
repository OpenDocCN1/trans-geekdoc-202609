

- AWS Elastic Container Registry (ECR)
- AWS CodeCommit
- Amazon Elastic Container Service (ECS)
- AWS CodeBuild
- Application Load Balancer (ALB)
- 将基于Web的机器学习应用与服务和Application Load Balancer (ALB)一起部署到Elastic Container Service (ECS)
- AWS CodePipeline
- 构建自动化CI/CD CodePipeline以在Amazon Web Services (AWS)上部署基于Web的机器学习应用

## 目标

本章学习完成后，您将能够在Amazon Elastic Container Service (ECS)上部署机器学习模型，而无需集成AWS以外的任何外部工具、服务或平台。您将使用AWS CodeCommit在AWS上创建远程Git仓库，并使用Amazon Elastic Container Service (ECS)集群运行可扩展的机器学习应用。您还将学习如何将Application Load Balancer (ALB)与Amazon Elastic Container Service (ECS)集成，以路由来自外部的请求。接下来，您将通过端口映射将服务端口与Docker端口集成，为Application Load Balancer (ALB)创建安全组，并学习将Docker容器镜像推送到AWS Elastic Container Registry (ECR)。完成本章后，您将能够使用AWS CodePipeline、AWS CodeBuild、AWS Elastic Container Registry (ECR)、Application Load Balancer (ALB)和Amazon Elastic Container Service (ECS)创建完全自动化的CI/CD流水线。

## Amazon Web Services (AWS)简介

Amazon Web Services (AWS)是一个可用于托管应用程序的云基础设施。2006年，AWS开始以Web服务的形式向市场提供IT服务。AWS是领先的云服务提供商之一。

## AWS计算服务

Amazon Web Services (AWS)提供计算服务，用于管理包含许多服务器或实例的工作负载。

以下是AWS提供的一些广泛使用的计算服务，可根据业务或应用程序需求使用。这些服务将在本章后面讨论。

## Amazon Elastic Compute Cloud (EC2)

Amazon EC2是一个代表远程服务器的虚拟机。Amazon EC2服务归类于**基础设施即服务（Infrastructure-as-a-Service，IaaS）**。Amazon EC2为应用程序提供可调整的计算能力，这些EC2机器称为实例。您可以创建具有不同计算大小的多个实例。创建后，您甚至可以升级RAM、vCPU等，因此无需重新创建新实例并再次配置。这就是使用“弹性”一词的原因。

## Amazon Elastic Container Service (ECS)

Amazon **Elastic Container Service** (**ECS**)可让您部署、扩展和管理容器化应用程序。它管理容器，并使开发人员能够在EC2实例集群上运行容器化应用程序。但是，它不基于Kubernetes。Amazon ECS是免费的，这意味着您无需为ECS集群付费。但是，需要为在ECS任务中运行的EC2实例支付额外费用。启动ECS集群主要有两种方式：

- Fargate启动
- EC2启动

Amazon ECS是AWS独有的技术。ECS可以轻松与AWS **Application Load Balancer (ALB)** 和 **Network Load Balancer (NLB)** 集成。

## Amazon Elastic Kubernetes Service (EKS)

Amazon **Elastic Kubernetes Service** (**EKS**) 是一项由AWS支持的Kubernetes服务，可让您在无需在EC2上手动安装Kubernetes的情况下在AWS上构建Kubernetes集群。Amazon Elastic Kubernetes Service (EKS)允许您在Kubernetes环境中管理或编排容器。您需要为EKS集群付费，并在Kubernetes pod中运行的EC2实例产生额外费用。Amazon EKS服务会为您设置和管理Kubernetes控制平面。

如果您需要多云功能以及与Amazon **Elastic Container Service** (**ECS**) 相比的其他功能，这是一个不错的选择。

## Amazon Elastic Container Registry (ECR)

Amazon **Elastic Container Registry** (**ECR**)允许开发人员在Amazon ECS上存储、共享和部署Docker镜像。它为其中存储的镜像提供安全性。Amazon Elastic Container Registry (ECR)与Amazon ECS集成。它类似于Docker Hub容器注册表，但由AWS管理。它允许您在其中存储私有Docker容器镜像。

## AWS Fargate

简单来说，AWS Fargate是面向容器的无服务器计算。您按分钟为容器使用的资源（如虚拟CPU（vCPU）和内存）付费。AWS Fargate与Amazon Elastic Container Service (ECS)和Amazon Elastic Kubernetes Service (EKS)兼容。

## AWS Lambda

AWS Lambda简单且成本较低。它是一种无服务器且事件驱动的计算服务；它是一种功能即服务（FaaS）。这意味着您无需管理服务器或集群。事件可以是任何简单的活动，例如用户单击链接以获取最新新闻。Lambda一词据说来源于λ演算和编程中的函数。它主要由三个组件组成：

- 函数：它是执行任务的实际代码。
- 配置：它决定函数的执行。
- 事件源：这是触发函数的事件。但是，此组件是可选的。

AWS Lambda是事件驱动编程的不错选择，或者在您需要访问多个服务时使用。

## Amazon SageMaker

AWS还提供一种名为Amazon SageMaker的机器学习平台即服务。它消除了手动管理和维护服务器的开销。它还降低了在AWS云上部署机器学习模型的时间和成本。

Amazon SageMaker是一个基于云的机器学习平台，使数据科学家和开发人员能够在生产环境中构建、训练、调整和部署机器学习模型。它使用Amazon Simple Storage Service (S3)存储数据，并带有超过15种最常用的内置机器学习算法用于训练数据。它将ML模型部署到SageMaker端点。Amazon SageMaker使用Amazon Elastic Container Registry (ECR)来存储容器镜像。

您现在应该已经了解了AWS及其服务的要点。您即将在Amazon Elastic Kubernetes Service (EKS)上部署机器学习模型。学完本章后，您将能够熟练使用AWS进行机器学习模型部署。

## 设置AWS账户

首先，设置一个AWS账户；但是，这是一次性活动。登录后即可立即使用。

AWS免费套餐为客户提供免费探索和试用AWS服务的功能，每项服务都有指定的使用限额。免费套餐包含三种不同类型的产品：12个月免费套餐、永久免费产品和短期试用。

### 步骤1：创建或登录现有AWS账户

创建AWS账户（如果您还没有账户）并登录。可以在AWS平台上创建免费试用账户，网址为 https://aws.amazon.com/free。

首先，单击Create a Free Account按钮。接下来，提供登录详细信息，例如电子邮件ID、密码和AWS账户名称。然后，选择账户类型（专业版或个人版）并提供联系信息。之后，提供PAN和付款详细信息。最后，在身份验证页面上完成验证流程。

几分钟后，账户将被激活并可以使用。根据您的要求选择一个计划。

### 步骤2：创建IAM用户并提供所需权限

登录AWS管理控制台后，打开IAM控制台 - https://console.aws.amazon.com/iam/。IAM代表身份和访问管理。接下来，在导航窗格中单击Users并选择Add users。然后，为该用户提供用户名并选择访问类型。之后，从附加的现有策略中选择现有策略，或为该用户创建新策略。在此场景中，IAM用户被授予管理员访问权限。标签是可选的。最后，检查并完成流程。不要忘记保存用户详细信息，如Access key ID、Secret access key和用户名。在此示例中，将使用IAM用户执行所有任务。单击Create user按钮并完成流程。

