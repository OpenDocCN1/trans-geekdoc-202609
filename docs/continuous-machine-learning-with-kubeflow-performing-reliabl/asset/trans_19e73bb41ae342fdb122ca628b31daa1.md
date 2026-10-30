
```
headers={"Host": "
{0}.kubeflow.example.com".format(MODEL_NAME)}
response =
requests.post("http://{0}/v1/models/{1}:predict".format(cluster_ip,
MODEL_NAME), data = data1,headers = headers)
response.json()
```

```
{'predictions': 'Negative Equity'}
```

图 6.37: KF serving Prediction O/P Python

## 6.6 使用 Grafana 仪表板监控性能

Grafana 包含对 Prometheus 的内置支持。本主题解释了 Prometheus 数据源特定的选项、变量、查询以及其他选项。启动 Grafana 仪表板。如第 4 章《Building TFX Pipeline》第 4.7 节所示，我们已经安装了 Grafana。

接下来，从本地终端运行并使用浏览器上的 `localhost:8080` 打开 `grafana` 仪表板。探索 Grafana 仪表板的各个组件。

```bash
kubectl port-forward --namespace knative-monitoring $(kubectl get pod --namespace knative-monitoring --selector="app=grafana" --output jsonpath='{.items[0].metadata.name}') 8080:3000
```

以下仪表板讨论了 Knative Serving 可视化的 HTTP 请求，我们将按每秒请求进行服务。

![](img/8f8a671916d96b455297952d0f37b96c_414_0.png)

图 6.38: Grafana Dashboard HTTP Request

因此，以下是控制平面的仪表板，显示 CPU 消耗和内存使用效率。

![](img/8f8a671916d96b455297952d0f37b96c_414_1.png)

图 6.39: Grafana CPU/Memory Dashboard

## 6.7 结论

在本章中，我们学习了如何在 Weights & Biases 中构建端到端的 LightGBM 框架，该框架在每次运行中捕获我们的模型并输出指标。我们为 LightGBM 算法参数构建了 sweep 和 Wandb 配置，同时为超参数搜索构建了平行坐标图。

我们还在 Kubernetes 平台上部署了 Kubeflow，并在 Kubernetes 集群中使用 KF serving 部署了模型，并在 Grafana 仪表板中监控了我们的预测结果。

在本章中，我们还获得了如何利用 Google Cloud Platform 的强大功能，并将 DevOps 知识与机器学习结合以成为 MLops 的知识。

## 6.8 参考文献

https://plotly.com/python/builtin-colorscales/

https://technowhisp.com/kaggle-api-python-documentation/

https://www.kaggle.com/numerai/encrypted-stock-market-data-from-numerai

https://github.com/Kaggle/kaggle-api

https://lightgbm.readthedocs.io/en/latest/Parameters.html

https://www.wandb.com/

https://github.com/kubeflow/kfserving

## 使用 AWS SageMaker 的应用机器学习

在本章中，我们将开展 Housing Price Sales Dataset 项目，在 Amazon SageMaker 云环境中完整运行、评估和部署模型，并使用 S3 进行数据存储。我们还将使用内置容器算法 XG-Boost 进行模型构建，以便能够从头到尾理解 SageMaker 模型构建框架的架构。

## 结构

本章将涵盖以下主题：

- 问题陈述
- AWS SageMaker 设置入门
- JupyterLab Notebook 实例、SDK 和 S3 存储桶入门
- 启动笔记本并将数据加载到 S3 入门
- 加载、分析和转换训练数据
- Amazon SageMaker 训练模型
- Amazon SageMaker 模型部署

## 目标

学习本章后，您将能够理解以下内容：

如何将数据加载并推送到用于数据存储的 Amazon S3 中。

离群值分析、特征转换以及分类和数值列的插补。

如何在 Amazon SageMaker 中创建笔记本、构建模型并部署它。在这里，我们将使用 XG-Boost 内置算法。

我们在 Amazon CloudWatch 中部署的模型的指标和性能。

## 7.1 问题

这里，一位购房者描述了他们的梦想房屋，他们可能不会从地下室天花板的高度或靠近东西向铁路开始。

因此，我们有 79 个变量描述了爱荷华州埃姆斯市住宅房屋几乎各方面的情况；这挑战了预测每栋房屋的最终价格。

房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。
房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。
房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。
房屋。 房屋。 房屋。
---
房屋。

## 7.2 AWS SageMaker 设置入门

因此，我们将从 AWS 账户设置开始我们的旅程。要完成设置，请完成以下步骤：

创建 AWS 账户电子邮件地址和密码以作为 AWS 账户根用户登录，并导航到 IAM 控制台，链接如下：

![](img/8f8a671916d96b455297952d0f37b96c_421_0.png)

图 7.1: AWS Sign-in Console

接下来，为您将创建的 IAM 管理员用户启用计费数据的访问权限：

在您账户名称的导航栏中选择 **My Account**。

在 **IAM User and Role Access to Billing** 旁边选择 Edit Next

接下来，选择复选框以 **Activate IAM Access** 并选择

![](img/8f8a671916d96b455297952d0f37b96c_422_0.png)

*图 7.2: AWS My account. Dashboard*

从导航栏中选择 **Services**，然后选择 IAM 进入 IAM 仪表板。

![](img/8f8a671916d96b455297952d0f37b96c_423_0.png)

图 7.3: AWS IAM Dashboard

您可以在 IAM 中的访问管理控制台中自定义下方给出的控制台登录链接，其中有自定义选项可更改。

单击 **Users** 并添加新用户：

类型

现在，选择 AWS Management Console access 旁边的复选框；然后选择自定义密码；接下来，在文本框中输入您自己的新密码。因此，默认情况下，AWS 会强制新用户在首次登录 AWS 时创建新密码。因此，我们可以 optionally 取消选中 User 旁边的框，因为用户必须在下次登录时创建新密码，以便新用户在登录后重置其密码。

![](img/8f8a671916d96b455297952d0f37b96c_424_0.png)

图 7.4: AWS Add User Screen

选择下一步：

在设置权限页面，选择直接附加现有策略。

单击下一步：

单击创建用户。

下载 csv 文件。

![](img/8f8a671916d96b455297952d0f37b96c_425_0.png)

图 7.5: AWS User Creation Last Step Screen

接下来，打开 csv 文件并复制链接到您的浏览器，以 myrole 用户名和您的自定义密码登录。可选：您可以在 IAM 的访问管理控制台中自定义下方的控制台登录链接，其中有自定义选项可更改。

以下是我们已下载的 csv 文件的屏幕截图：

![](img/8f8a671916d96b455297952d0f37b96c_425_1.png)

图 7.6: AWS IAM Role Creation csv file credentials

接下来，以 IAM 用户身份登录并搜索

![](img/8f8a671916d96b455297952d0f37b96c_426_0.png)

图 7.7: AWS Service search dashboard

这里，我们将搜索 **AmazonSagemaker**

## 7.3 JupyterLab Notebook 实例和 SDK 及 S3 存储桶入门

### 7.3.1 创建 S3 存储桶

现在，模型的训练将产生以下内容：

转换后的模型训练数据存储在 S₃ 中。

模型工件，即 Amazon SageMaker 在模型训练期间生成的。

我们可以将所有这些内容保存在 **Amazon Simple Storage Service** 存储桶中；我们可以将训练数据期间使用的数据集和训练作业输出的模型工件存储在单个存储桶或两个单独的存储桶中。

登录后，屏幕将如下所示的屏幕截图：

![](img/8f8a671916d96b455297952d0f37b96c_429_0.png)

图 7.8: AWS S3 Create Bucket Screen

现在，您的存储桶已创建。

![](img/8f8a671916d96b455297952d0f37b96c_429_1.png)

图 7.9: AWS S3 Bucket Dashboard

### 7.3.2 创建 Amazon SageMaker 笔记本实例

导航到 Amazon SageMaker 控制台 > 笔记本实例 > 创建笔记本实例。步骤如下：

在创建笔记本实例页面，提供以下信息（如果未提及某个字段，请保留默认值）：

在笔记本实例名称部分，为您的笔记本实例输入名称。

然后，对于实例类型，选择 这是最便宜的实例类型，也是笔记本实例支持的推荐类型。

![](img/8f8a671916d96b455297952d0f37b96c_430_0.png)
