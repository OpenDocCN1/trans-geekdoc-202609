


- 使用 GitHub Actions 构建 CI/CD 流水线
- Azure Machine Learning (AML) 服务
- 使用 Azure Machine Learning (AML) 服务和 Azure DevOps 构建 CI/CD 流水线

## 目标

本章学习结束后，你应当能够将 ML 模型部署到 平台即服务 (PaaS) 和 机器学习即服务 (MLaaS) 上。你还应当能够将 GitHub 仓库集成到 Azure，以实现应用的自动化部署。你应当知道如何创建 Web 应用及其容器。此外，你将熟悉如何使用 GitHub Actions 和 Azure 构建并运行 CI/CD 流水线，以及在 GitHub Actions 上使用 pytest 和 tox 执行多个测试用例。在本章后续部分，你将学习如何为 GitHub Actions 创建 YAML 文件以运行工作流。到本章结束时，你还应当能够使用 Azure DevOps 构建并运行 CI/CD 流水线。

## Azure

Microsoft Azure（又称 Azure）是微软提供的云计算服务。Azure 提供多种形式的云计算选项，例如软件即服务 (SaaS)、平台即服务 (PaaS)、机器学习即服务 (MLaaS) 和基础设施即服务 (IaaS)，用于在 Azure 上部署应用程序和服务。

微软于 2008 年首次以 Windows Azure 名称推出其云计算服务，但商业上是在 2010 年推出的。之后，在 2014 年，他们扩展了服务并将其重新推出为 Microsoft Azure。

Azure 是一个即用型、资源丰富、灵活、快速且经济的云平台。它附带 200 多种产品和云服务；不过，在开发者中运行虚拟机 (VM) 或容器很受欢迎。它与 Docker、Jenkins 和 Kubernetes 等开源技术兼容。Azure 内置了持续集成和持续部署流水线。

Azure 支持与 GitHub 集成，以便轻松将 GitHub 仓库中的代码部署到运行在 Azure 上的应用程序。当为 Azure 应用配置 GitHub 集成后，Azure 可以自动构建并发布（如果该阶段成功完成）并将其推送到 Azure。

Azure 应用服务可以使用 Azure Kubernetes 服务 (AKS) 进行缩放。你可以选择不同的层级，每个层级附带一组计算能力，并设置自动缩放限制。在需要时，它会创建服务的副本以无缝处理请求。

在 Azure 平台上部署应用有许多方式，但你将在本章中探索两种方法：

- 使用 GitHub Actions 进行部署
- 使用 Azure DevOps 和 Azure ML 进行部署

Azure 主要采用按需付费定价计划，允许你仅为所使用的服务付费。如果某个应用程序使用多个服务，则每个服务将根据其获得的计划/层级计费。如果用户或组织寻求长期承诺，微软会提供折扣价格。

Azure 是一项付费服务，但允许新用户使用免费积分在有限时长内免费探索其功能和服务。之后，你需要激活按需付费定价计划。

## 设置 Azure 账户

你需要设置一个 Azure 账户。这是一次性操作，完成后即可使用。访问 Azure 平台 https://azure.microsoft.com/。

创建 Azure 账户（如果你还没有），然后登录。

> 注：你可以免费探索 Azure；但是，你需要提供信用卡/借记卡信息。如果需要付款，Azure 会发送通知。此外，你可以免费使用热门服务 12 个月，并额外获得 30 天的 $200 额度。

本章将使用 Azure DevOps。为此，你需要登录 Azure DevOps。

https://azure.microsoft.com/en-us/services/devops/

要连接并与 Azure 通信，需要 Azure 命令行工具，即 azure-cli 和 azureml-sdk。

使用本地终端安装 Azure CLI：

```
pip install azure-cli==2.37.0
pip install --upgrade azureml-sdk[cli]
```

你可以创建资源组。它是一个容器，用于保存 Azure 项目的相关资源。你可以根据需要将资源分配给此资源组。

## 使用 GitHub Actions 进行部署

在本部分中，将使用 Docker 在 Azure Web 服务中部署一个 ML 应用。GitHub Actions 将用于构建、测试和部署 Azure 上的 ML 应用。首先，GitHub Actions 会构建 Docker 镜像并将其推送到 **Azure 容器注册表 (ACR)**，然后将其拉取到 Azure 应用服务。

首先，为此实现准备所需的代码库。接下来，创建一个 ACR，然后构建 Docker 镜像并将其推送到 ACR。在下一步中，在 Azure 应用服务中创建 Web 应用，它将从 ACR 拉取容器镜像以部署基于 Web 的 ML 应用。

下图显示了使用 GitHub Actions 在 Azure 应用服务 (Web 应用) 上进行部署的工作流：

![](img/cc4299656808e62a294f1843a1e18e72_276_0.png)

图 11.1：GitHub Actions 和 Web 应用工作流

你可以在以下 GitHub 仓库中访问代码：

https://github.com/suhas-ds/mlapp-cd

以下目录结构显示了将用于 CI/CD 流水线的文件：

```
.
|-- .github
|   |-- workflows
|       |-- prod.workflow.yml
|-- src
|   |-- prediction_model
|       |-- config
|           |-- __init__.py
|           |-- config.py
|       |-- datasets
|           |-- __init__.py
|           |-- test.csv
|           |-- train.csv
|       |-- processing
|           |-- __init__.py
|           |-- data_management.py
|           └ preprocessors.py
|       |-- trained_models
|           |-- __init__.py
|           └ classification_v1.pkl
|       |-- VERSION
|       |-- __init__.py
|       |-- pipeline.py
|       |-- predict.py
|       └ train_pipeline.py
|       |-- tests
|           |-- pytest.ini
|           └ test_predict.py
|   |-- MANIFEST.in
|   |-- README.md
|   |-- requirements.txt
|   |-- setup.py
|   └ tox.ini
|-- Dockerfile
|-- docker-compose.yml
|-- main.py
|-- pytest.ini
|-- requirements.txt
|-- runtime.txt
|-- start.sh
|-- test.py
└─ tox.ini
```

让我们讨论前面文件中的代码和概念。在 `src` 目录中，将使用 *第 4 章：打包 ML 模型* 中的文件。

## .gitignore

此文件包含 Git 应忽略的文件和目录的名称。

- venv/
- __pycache__/
- .pytest_cache
- .tox

## main.py

此文件将加载模型的 pickle 对象并运行 FastAPI 应用。首先，从 **预测模型** 加载依赖项和模块：

```
1. # Importing Dependencies
2. from fastapi import FastAPI
3. from pydantic import BaseModel
4. import uvicorn
5. import pickle
6. import os
7. import numpy as np
8. import pandas as pd
9. from fastapi.middleware.cors import CORSMiddleware
10. from prediction_model.predict import make_prediction
11. import pandas as pd
```

创建一个 FastAPI 实例并将其分配给 **应用**，以便在创建 API 时 **应用** 成为交互点。

```
1. app = FastAPI(
2.     title="Loan Prediction Model API",
3.     description="A simple API that uses ML model to predict the Loan application status",
4.     version="0.1",
5. )
```

**跨源资源共享 (CORS)** 是指当在浏览器中运行的前端具有与后端通信的 JavaScript 代码，而后端与前端来源不同的情况。但是，是否使用它取决于你的应用程序和要求。

```
1. origins = [
2.       "*"
3.     ]
4.
5. app.add_middleware(
6.     CORSMiddleware,
7.     allow_origins=origins,
8.     allow_credentials=True,
9.     allow_methods=["*"],
10.    allow_headers=["*"],
11. )
```

定义 LoanPred 类，该类定义客户端预期的数据类型。

用于数据模型的 LoanPred 类继承自 BaseModel。然后，添加一个带有函数的根视图，该函数为主页返回 'message': 'Loan Prediction App'。

```
1. class LoanPred(BaseModel):
2.     Gender: str
3.     Married: str
4.     Dependents: str
5.     Education: str
6.     Self_Employed: str
7.     ApplicantIncome: float
8.     CoapplicantIncome: float
9.     LoanAmount: float
10.    Loan_Amount_Term: float
11.    Credit_History: float
12.    Property_Area: str
13.
14. @app.get('/')
15. def index():
16.     return {'message': 'Loan Prediction App'}
17.
```

