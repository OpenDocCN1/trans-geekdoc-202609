

run: |
  tox

- name: Login via Azure CLI
  uses: azure/login@v1
  with:
    creds: ${{ secrets.AZURE_CREDENTIALS }}

- name: Login to Azure Container Registry
  uses: azure/docker-login@v1
  with:
    login-server: mlappcd.azurecr.io
    username: ${{ secrets.REGISTRY_USERNAME }}
    password: ${{ secrets.REGISTRY_PASSWORD }}

- name: Build and push container image to the registry
  run: |
    docker build . -t mlappcd.azurecr.io/mlapp-cd:${{ github.sha }}
    docker push mlappcd.azurecr.io/mlapp-cd:${{ github.sha }}

- name: Deploy to App Service
  uses: azure/webapps-deploy@v2
  with:
    app-name: 'mlapp-cd'
    images: 'mlappcd.azurecr.io/mlapp-cd:${{ github.sha }}'

- name: Azure logout
  run: |
    az logout

Next, create the repository on GitHub for this (if not created already) and push the codebase into that repo.

## 服务主体

你需要在 GitHub Actions 工作流中提供服务主体，用于 Azure 身份验证和应用部署。要获取凭据，请在终端中使用你的订阅 ID 执行以下命令。

```
az ad sp create-for-rbac --name "github-actions" --role contributor --scopes /subscriptions/<Subscription ID>/resourceGroups/mlapp-cd --sdk-auth
```

With the preceding command, you will create an Azure Role Based Access Control (RBAC) named github-actions with a contributor role and scope.

Note: You can get the subscription ID from the subscription you have used while creating a resource group.

Azure RBAC is an authorization system built on Azure Resource Manager that provides access management of Azure resources.

You should get the following output:

```
{
    "clientId": "",
    "clientSecret": "",
    "subscriptionId": "",
    "tenantId": "",
    "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
    "resourceManagerEndpointUrl": "https://management.azure.com/",
    "activeDirectoryGraphResourceId": "https://graph.windows.net/",
    "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
    "galleryEndpointUrl": "https://gallery.azure.com/",
    "managementEndpointUrl": "https://management.core.windows.net/"
}
```

In the preceding response, clientId, clientSecret, subscription, and tenantId are unique for the individual account. Copy and save the response of the preceding command for future use.

Now, go to GitHub repo settings and create three GitHub secrets:

- AZURE CREDENTIALS: Entire JSON response from preceding
- REGISTRY_USERNAME: clientId value from JSON response
- REGISTRY_PASSWORD: clientSecret value from JSON response

## 配置 Azure 应用服务以使用 GitHub Actions 进行持续部署

你需要配置 Azure 应用服务，以便使用 GitHub Actions 进行自动化。前往 Azure 应用服务 | 部署中心，并链接 GitHub 仓库主分支，如下图所示。

![](img/cc4299656808e62a294f1843a1e18e72_298_0.png)

图 11.14: Azure 服务-GitHub 配置

你需要授权 GitHub Actions 以实现持续部署自动化并提供所需详细信息。你可以添加部署槽位，例如暂存或预生产。当你不希望将更新后的 Azure 应用服务直接暴露到生产环境时，这非常有用。你需要按照上述步骤为部署中心执行相同的配置。

After completing the configuration in the app service, place the `prod.workflow.yml` workflow file in the linked GitHub repository. The path would be `.github/workflows/prod.workflow.yml`. When you push any changes to the GitHub repo, it will trigger the GitHub Actions workflow. After completing all the stages, the ML app will be deployed on Azure.

Go to the Actions tab in the GitHub repository, and you will see that GitHub has already started running the `prod.workflow.yml` workflow for app deployment on Azure.

Push the changes with a **部署** text as a comment, as you can see in the following figure.

![](img/cc4299656808e62a294f1843a1e18e72_299_0.png)

图 11.15: GitHub Actions-工作流运行

Click on **部署**, and it will take you to the summary of this workflow. You will see the status of the jobs you have defined in the workflow. Other execution details are also mentioned, such as the time taken to complete this workflow, the username that pushed the updates to the **主分支** branch, and the name of the workflow file.

**部署**
Build and deploy to production #5

![](img/cc4299656808e62a294f1843a1e18e72_300_0.png)

Figure 11.16: GitHub Actions-workflow steps

The following figure shows the output of app deployment to the Azure step from GitHub Actions. You can see that the app is successfully deployed and running on Azure. An app service application URL is printed at the end.

![](img/cc4299656808e62a294f1843a1e18e72_300_1.png)

Figure 11.17: GitHub Actions-deployment status

Head over to the Azure App Service; you should see container logs in the Azure App Service, as shown in the following figure. This helps you debug the issue while deploying the app.

![](img/cc4299656808e62a294f1843a1e18e72_301_0.png)

Figure 11.18: App service-container logs

If everything goes well, the app should work on Azure post deployment.

The following figure shows the app running on the Azure platform on successful completion of the prod.workflow.yml workflow.

![](img/cc4299656808e62a294f1843a1e18e72_301_1.png)

Figure 11.19: App service-ML web app running

Azure provides a monitoring service to track the usage of the Azure app. You can select metrics from the dropdown.

The following figure shows the monitoring service of the Azure app.

![](img/cc4299656808e62a294f1843a1e18e72_302_0.png)

Figure 11.20: App service-monitoring service

Thus, you have learned to create a simple CI/CD pipeline using GitHub to deploy the ML app on the Azure platform. However, you can modify it as per business and application requirements.

## 使用 Azure DevOps 和 Azure ML 进行部署

In this part, you will use Azure DevOps and AML to deploy an ML app on the Azure cloud. Unlike the previous part, the CI pipeline and CD pipeline are in the Azure cloud. This approach requires parallelism to be enabled. If you are using free credits, then by default, parallelism is not enabled; however, you can activate it by sending the request via email. You can use Azure Git repo or other sources, such as GitHub. This approach gives more flexibility, such as integration with other platforms, manual approval before deploying to the production, auto redeploy triggers, and such.

The following figure shows the automated ML workflow:

![](img/cc4299656808e62a294f1843a1e18e72_303_0.png)

Figure 11.21: Azure DevOps pipeline for ML

## Azure 机器学习 (AML) 服务

Azure Machine Learning (AML) service enable the creation of a reproducible CI/CD pipeline for ML. It is an Azure cloud-hosted environment that allows developers and organizations to deploy ML models quickly in the production environment with minimal code. In Azure Machine Learning Studio, you can run the notebooks on the cloud, use Automated ML for automated training and tuning the ML model using a metric, or use a designer to deploy a model from data preparation using a drag-and-drop interface.

The following are the salient features of Azure Machine Learning Studio:

- Storage provision to store your data and artifacts
- MLFlow to track your experiments and log the run details like timestamp, model metrics, and so on
- Model registry to store trained ML models for reusability
- Key vault to store credentials and variables
- Supports open-source libraries and frameworks
- Compute instance, which enables building and training in a secure VM
- Pipelines and CI/CD for faster training and deployment

- Endpoints for ML model
- Data drift functionality to deliver consistent accuracy and predictions
- Monitoring service to track the model, logs, and resources

### 工作区

A machine learning workspace is the main resource of AML. It contains experiments, models, endpoints, datasets, and such. It also includes other Azure resources, such as Azure Container Registry (ACR), which registers Docker containers at the time of Docker image deployment, storage, application insights, and key vault.

### 实验

An experiment consists of several runs initiated from the script. Run details and metadata are stored under the experiment. When you run the script, the experiment name needs to be provided to store the run information. However, it will create a new experiment if the name provided in the script does not exist in the given workspace.

### 运行

A run can be defined as a single iteration of the training script. Multiple runs are recorded under an experiment. A run logs model metrics and metadata, such as timestamps.

The best thing about AML is that you do not need to create a separate web service API using frameworks like Flask, Django, and FastAPI. AML creates endpoints for trained ML models and tracks the web service.

In this section, you will be using the Azure Machine Learning template and modifying it as per your requirements. You can build your codebase from the scratch; however, this template saves time as it has reusable and required steps already defined. The Azure DevOps demo generator can be accessed at the following link:

https://azuredevopsdemogenerator.azurewebsites.net/environment/createproject

Go to DevOps Labs, select the Azure Machine Learning template and add it to your project by providing the project name and organization in the next step.

Alternatively, you can directly go to the following URL:

https://azuredevopsdemogenerator.azurewebsites.net/?name=machinelearning

