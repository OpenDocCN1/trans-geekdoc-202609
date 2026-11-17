

register as production model perform better written inside the **except** block and exit from the code.

将模型注册为生产模型，最好在 **except** 块中编写，并从代码中退出。

If the run id is found in `aml_config/run_id.json`, it will register the model. Finally, it will write the registered model details to `/aml_config/model.json`.

如果在 `aml_config/run_id.json` 中找到运行 ID，则会注册该模型。最后，它会将已注册模型的详细信息写入 `/aml_config/model.json`。

The following code update is incorporated into the existing script:

以下代码更新已合并到现有脚本中：

```
# Download Model to Project root directory

model_name = "sklearn_classification_model.pkl"

run.download_file(
    name="./outputs/" + model_name, output_file_path="./model/" + model_name
)

print("Downloaded model {} to Project root directory".format(model_name))

os.chdir("./model")

model = Model.register(
    model_path=model_name, # This points to a local file
    model_name=model_name, # This is the name the model is registered as
    tags={"area": "loan", "type": "classification", "run_id": run_id},
    description="Classification model for loan dataset",
    workspace=ws,
)
```

### aml_service/30-CreateScoringImage.py

In the beginning, it will look for the `aml_config/model.json` file generated from the previous step. If it is not found, the script will be terminated with the message **No new model to register thus no need to create new scoring image**.

开始时，它会查找上一步生成的 `aml_config/model.json` 文件。如果找不到，脚本将显示消息 **没有新模型可注册，因此无需创建新的评分镜像** 后终止。

The following code update is incorporated into the existing script:

以下代码更新已合并到现有脚本中：

```
image_name = "loan-model-score"

image_config = ContainerImage.image_configuration(
    execution_script="score.py",
    runtime="python-slim",
    conda_file="conda_dependencies.yml",
    description="Image with logistic regression model",
    tags={"area": "loan", "type": "classification"},
)
```

This will create the image for the model, and at the end, capture the image details, such as name, version, creation_state, image_location, and image_build_log_uri in the /aml_config/image.json.

这将为模型创建镜像，最后在 /aml_config/image.json 中捕获镜像详细信息，如名称、版本、创建状态、镜像位置和镜像构建日志 URI。

### aml_service/50-deployOnAci.py

**Azure Container Instances (ACI)** is an Azure service that enables users to run a container on the Azure cloud without demanding the use of a **Virtual Machine (VM)**。

**Azure 容器实例 (ACI)** 是一项 Azure 服务，使用户能够在 Azure 云上运行容器，而无需使用 **虚拟机 (VM)**。

In the beginning, it will look for the _aml_config/image.json_ file generated from the previous step. If it is not found, the script will be terminated with the message **No new model, thus no deployment on ACI.**

开始时，它会查找上一步生成的 _aml_config/image.json_ 文件。如果找不到，脚本将显示消息 **没有新模型，因此不在 ACI 上部署。** 后终止。

The following code update is incorporated into the existing script:

以下代码更新已合并到现有脚本中：

```
aciconfig = AciWebservice.deploy_configuration(
    cpu_cores=1,
    memory_gb=1,
    tags={"area": "loan", "type": "classification"},
    description="A loan prediction app",
)
```

This script will create a web service and capture the ACI details in /aml_config/aci_webservice.json at the end of the script.

此脚本将创建 Web 服务，并在脚本结束时将 ACI 详细信息捕获到 /aml_config/aci_webservice.json 中。

### aml_service/60-AciWebserviceTest.py

In the beginning, it will look for the _aml_config/aci_webservice.json_ file generated from the previous step. If it is not found, the script will be terminated with the message **No new model, thus no deployment on ACI.**

开始时，它会查找上一步生成的 _aml_config/aci_webservice.json_ 文件。如果找不到，脚本将显示消息 **没有新模型，因此不在 ACI 上部署。** 后终止。

The following code update is incorporated into the existing script:

以下代码更新已合并到现有脚本中：

```
# Input for Model with all features
input_j = [[[1,1,0,1,0,1,2,3849],[1,1,3,0,0,0,1,5540]]]
```

## Configure CI pipeline

## 配置 CI 管道

At this stage, you will configure the CI pipeline. This pipeline will execute the following tasks:

此阶段，您将配置 CI 管道。该管道将执行以下任务：

- Set up Python version 3.6.
- Install required dependencies.
- Create or get Azure Machine Learning (AML) workspace.
- Build and train the ML model.
- Evaluate newly trained model performance against the existing model to decide whether the model is to be promoted to production.
- Register model in Azure Machine Learning (AML) service.
- Create a scoring Docker image with the required dependencies.
- Publish the artifacts (all files) to the repo.

- 设置 Python 3.6 版本。
- 安装所需的依赖项。
- 创建或获取 Azure 机器学习 (AML) 工作区。
- 构建并训练 ML 模型。
- 评估新训练模型与现有模型的性能，以决定是否将模型提升到生产环境。
- 在 Azure 机器学习 (AML) 服务中注册模型。
- 使用所需的依赖项创建评分 Docker 镜像。
- 将构件（所有文件）发布到仓库。

The following figure shows the steps of the CI pipeline:

以下图显示了 CI 管道的步骤：

![](img/cc4299656808e62a294f1843a1e18e72_314_0.png)

Figure 11.25: CI pipeline for ML

图 11.25: 机器学习的 CI 管道

Note: You need to select Azure service connection from the Azure subscription dropdown wherever necessary.

注意：在需要的地方，请从 Azure 订阅下拉列表中选择 Azure 服务连接。

Next, in the **Triggers** tab, select **Enable continuous integration** checkbox. This enables the CI pipeline to run as soon as any changes are pushed to the code repository.

接下来，在 **触发器** 选项卡中，选择 **启用持续集成** 复选框。这样可启用 CI 管道，以便在将任何更改推送到代码仓库时立即运行。

You can trigger the CI pipeline by pushing any changes to the repository. The Azure CI pipeline detects the changes in the repo and starts building the pipeline. To see the progress of the CI pipeline, switch to the **Summary** tab.

您可以通过向仓库推送任何更改来触发 CI 管道。Azure CI 管道会检测仓库中的更改并开始生成管道。要查看 CI 管道的进度，请切换到 **摘要** 选项卡。

The following figure displays the **Summary** tab. You can see the commit message on the top, followed by the summary and the jobs. The job status and progress of steps can be seen by clicking on **Phase 1**.

以下图显示了 **摘要** 选项卡。您可以在顶部看到提交消息，接着是摘要和作业。单击 **阶段 1** 可以查看作业状态和步骤进度。

![](img/cc4299656808e62a294f1843a1e18e72_315_0.png)

Figure 11.26: CI pipeline for ML-Jobs summary

图 11.26: 机器学习的 CI 管道 - 作业摘要

After clicking on Phase 1 under the Jobs section, you should see the progress of the CI pipeline. The following figure shows the terminal output of each CI pipeline step:

在作业部分单击阶段 1 后，您应该能看到 CI 管道的进度。以下图显示了每个 CI 管道步骤的终端输出：

![](img/cc4299656808e62a294f1843a1e18e72_316_0.png)

Figure 11.27: CI pipeline for ML-logs

图 11.27: 机器学习的 CI 管道 - 日志

## Configure CD pipeline

## 配置 CD 管道

Now that you have completed the CI pipeline configuration, it's time to configure the CD pipeline. The CD pipeline will deploy the image generated through the CI pipeline to the Azure Container Instance (ACI) and Azure Kubernetes Service (AKS). In the current case, the scope of the project is limited to ACI. However, you can deploy it on AKS to handle large amounts of traffic and make it scalable.

完成 CI 管道配置后，现在是配置 CD 管道的时候了。CD 管道将通过 CI 管道生成的镜像部署到 Azure 容器实例 (ACI) 和 Azure Kubernetes 服务 (AKS)。在当前情况下，项目范围仅限于 ACI。但是，您可以将其部署到 AKS 以处理大量流量并实现可扩展性。

This pipeline executes the following tasks:

此管道将执行以下任务：

- Set up Python version 3.6.
- Install the required dependencies.
- Deploy a web service on the Azure container instance (ACI).
- Test the ACI web service by passing data that needs to be tested.
- Deploy a web service on Azure container instance (AKS).
- Test the AKS service by passing the data to be tested.

- 设置 Python 3.6 版本。
- 安装所需的依赖项。
- 在 Azure 容器实例 (ACI) 上部署 Web 服务。
- 通过传递需要测试的数据来测试 ACI Web 服务。
- 在 Azure 容器实例 (AKS) 上部署 Web 服务。
- 通过传递要测试的数据来测试 AKS 服务。

The following figure shows the CD pipeline:

以下图显示了 CD 管道：

![](img/cc4299656808e62a294f1843a1e18e72_317_0.png)

Figure 11.28: CD pipeline for ML

图 11.28: 机器学习的 CD 管道

Now, navigate to Pipeline | Releases, select Deploy Web service and click on Edit pipeline.

现在，导航到 Pipeline | 发布版本，选择部署 Web 服务，然后单击编辑管道。

The following figure shows the QA – Deploy on ACI stage of the CD pipeline when switched to the Tasks tab.

切换到任务选项卡时，以下图显示了 CD 管道中 QA – 部署到 ACI 阶段。

![](img/cc4299656808e62a294f1843a1e18e72_317_1.png)

Figure 11.29: CD pipeline for ML-QA stage

图 11.29: 机器学习的 CD 管道 - QA 阶段

Note: You need to select Azure service connection from the Azure subscription dropdown wherever necessary.

注意：在需要的地方，请从 Azure 订阅下拉列表中选择 Azure 服务连接。

In the following figure, you can see the entire file path provided by the artifacts that are retrieved from the CI pipeline:

在以下图中，您可以看到从 CI 管道检索的构件提供的完整文件路径：

![](img/cc4299656808e62a294f1843a1e18e72_318_0.png)

Figure 11.30: CD pipeline for ML-QA stage requirement step

图 11.30: 机器学习的 CD 管道 - QA 阶段要求步骤

When you update the CD pipeline, you can run the CD pipeline manually by hitting the **Create Release** button or setting the auto trigger, which means that the CD pipeline starts executing upon completion of the CI pipeline. You need to make sure that continuous deployment triggers are enabled in the **Artifacts** stage and the **QA -Deploy on ACI** stage of the CD pipeline.

更新 CD 管道时，您可以通过单击 **创建发布版本** 按钮或设置自动触发器手动运行 CD 管道，这意味着 CD 管道将在 CI 管道完成后开始执行。您需要确保在 CD 管道的 **构件** 阶段和 **QA - 部署到 ACI** 阶段中启用了持续部署触发器。

In the following figure, you can see the CD pipeline triggers upon completion of the CI pipeline, which caused the **QA -Deploy on ACI** stage to start executing:

在以下图中，您可以看到 CD 管道在 CI 管道完成后触发，这导致 **QA - 部署到 ACI** 阶段开始执行：

![](img/cc4299656808e62a294f1843a1e18e72_319_0.png)

Figure 11.31: CD pipeline for ML-triggered after CI pipeline

图 11.31: 机器学习的 CD 管道 - CI 管道完成后触发

It takes a few minutes to execute all the steps. You should see the number of tasks completed and the status of the stage. If you want to see the details of each step, click on the Logs option.

执行所有步骤需要几分钟。您应该能看到完成的任务数量和阶段状态。如果要查看每个步骤的详细信息，请单击日志选项。

The following figure shows the status of each step with logs.

以下图显示了带日志的每个步骤的状态。

![](img/cc4299656808e62a294f1843a1e18e72_319_1.png)

Figure 11.32: CD pipeline for ML-QA stage logs

图 11.32: 机器学习的 CD 管道 - QA 阶段日志

When ACI deployment is completed, it waits for manual approval from the developer but for a limited time. You can update the time from the options. After approval, it will deploy to the AKS. If you want to automate this step, you can remove the manual approval or set auto approval. However, it is recommended to keep manual approval before deploying it on AKS.

ACI 部署完成后，它会等待开发者的手动批准，但仅限有限时间。您可以从选项中更新时间。批准后，它将部署到 AKS。如果要自动执行此步骤，可以删除手动批准或设置自动批准。但是，建议在部署到 AKS 之前保留手动批准。

In the following figure, you can see that the QA – Deploy on ACI stage is completed, and it is pending approval for deploying it on AKS. You can set the time for approval requests to be active. After approval, the pipeline will deploy the app using AKS.

在以下图中，您可以看到 QA – 部署到 ACI 阶段已完成，并且正在等待批准以部署到 AKS。您可以设置批准请求的有效时间。批准后，管道将使用 AKS 部署应用。

![](img/cc4299656808e62a294f1843a1e18e72_320_0.png)

Figure 11.33: Azure pipeline for ML-completed

图 11.33: 机器学习的 Azure 管道 - 已完成

Now, head over to the Azure Machine Learning studio, and go to Jobs from the left panel. You should see the experiment with the name provided in the training script, that is, **mlops-classification**. On the right side, you can see the details like the experiment name, the date of creation, and the last submission. When you go to the experiment, you will see the run information with status and other metadata. On the top, you can see metrics details with graphs. In the current case, accuracy and CV score are being logged. You can assess each job’s details by clicking on it.

现在，请转到 Azure 机器学习工作室，然后从左侧面板进入作业。您应该能看到训练脚本中提供的名称的实验，即 **mlops-classification**。在右侧，您可以看到实验名称、创建日期和上次提交等详细信息。进入实验后，您将看到带有状态和其他元数据的运行信息。在顶部，您可以看到带图表的指标详细信息。在当前情况下，正在记录准确率和 CV 分数。您可以单击每个作业来评估其详细信息。

The following figure shows the model metrics, that is, accuracy and CV score, along with run information and other details. In the graphs, you can see the value of each metric logged in the runs separately.

以下图显示了模型指标（即准确率和 CV 分数），以及运行信息和其他详细信息。在图表中，您可以看到各个运行中分别记录的每个指标的值。

