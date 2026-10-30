
apiVersion: v1
kind: ServiceAccount
metadata:
name: tiller
namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRoleBinding
metadata:
name: tiller
roleRef:
apiGroup: rbac.authorization.k8s.io
kind: ClusterRole

name: cluster-admin
subjects:
- kind: ServiceAccount
name: tiller
namespace: kube-system

### Step Create the tiller service account and cluster-admin role binding.
### 步骤 创建 tiller 服务账号和 cluster-admin 角色绑定。

```bash
kubectl apply -f rbac-config.yaml
```

### Step Initialize Helm.
### 步骤 初始化 Helm。

```bash
helm init --service-account tiller
```

### Step Copy the namespace that you can find by either running the following command which will give a list of namespace, or from the UI.
### 步骤 复制命名空间，您可以通过运行以下命令找到该命名空间，该命令将列出命名空间，或从 UI 中找到。

```bash
kubectl get namespace
```

Otherwise, copy the drop down and paste in the Notepad example here: aniruddha-choudhury.
否则，复制下拉菜单并粘贴到记事本示例中：aniruddha-choudhury。

![](img/8f8a671916d96b455297952d0f37b96c_100_0.png)

Figure 1.44: Namespace
图 1.44：命名空间

### Step Deploy the NFS-Client Provisioner.
### 步骤 部署 NFS-Client Provisioner。

Create an instance of NFS-Client Provisioner connected to the Filestore instance that you created earlier via its IP address (${FSADDR}). The NFS-Client Provisioner creates a new storage class: nfs-client. Persistent volume claims against that storage class will be fulfilled by creating persistent volumes backed by directories under the /volumes directory on the Filestore instance's managed storage.
创建一个 NFS-Client Provisioner 实例，通过其 IP 地址 (${FSADDR}) 连接到您之前创建的 Filestore 实例。NFS-Client Provisioner 创建一个新的存储类：nfs-client。针对该存储类的持久卷声明将通过创建由 Filestore 实例托管存储上的 /volumes 目录下的目录支持的持久卷来满足。

```bash
helm install stable/nfs-client-provisioner --name nfs-cp --set nfs.server=${FSADDR} --set nfs.path=/volumes
watch kubectl get po -l app=nfs-client-provisioner
```

![](img/8f8a671916d96b455297952d0f37b96c_101_0.png)

Figure 1.45: FileStore
图 1.45：文件存储

### Step Make a Persistent Volume Claim.
### 步骤 创建持久卷声明。

Create a Kubernetes Persistent Volume Claim specification. This is a .yaml file that allows a Kubernetes pod to access the storage resources of a Persistent Volume. The specification looks similar to the following example:
创建一个 Kubernetes 持久卷声明规范。这是一个 .yaml 文件，允许 Kubernetes pod 访问持久卷的存储资源。该规范看起来类似于以下示例：

![](img/8f8a671916d96b455297952d0f37b96c_101_1.png)

Figure 1.46: PVC yaml
图 1.46：PVC yaml

Here, storage is the size of the Persistent Volume Claim that you want to make available to the Kubernetes objects.
这里，storage 是您希望提供给 Kubernetes 对象的持久卷声明的大小。

You must specify the storage value in one of the supported units described in the Resource quantities. The value you specify must be equal to or less than the storage you specified for the Persistent Volume.
您必须使用 Resource quantities 中描述的支持的单位之一指定 storage 值。您指定的值必须等于或小于您为持久卷指定的存储。

Deploy the Persistent Volume Claim specification:
部署持久卷声明规范：

```bash
kubectl create -f persistent-volume-claim-file-name.yaml
```

Here, persistent-volume-file-name is the name of the Kubernetes Persistent Volume specification file that you created in the previous step.
这里，persistent-volume-file-name 是您在上一步中创建的 Kubernetes 持久卷规范文件的名称。

### Step Copy the PVC name from above and paste it in the Jupyter Notebook in Kubeflow Workspace Volume Name.
### 步骤 从上面复制 PVC 名称并将其粘贴到 Jupyter Notebook 中的 Kubeflow 工作区卷名称。

```bash
## paste the namespace here to get the name
kubectl get pvc -n {namespace}
```

### 1.8 Conclusion
### 1.8 结论

In this chapter, we learned about the Kubernetes Orchestration concepts and architecture, and how it works in deployment level and scaling our application, alongside exposing to the outer world with the Network & Service; and how the Docker makes it easy for a developer to containerize applications.
在本章中，我们学习了 Kubernetes 编排概念和架构，以及它在部署级别和扩展我们的应用程序方面的工作方式，同时通过网络和服务向外部世界公开；以及 Docker 如何使开发人员轻松地将应用程序容器化。

Then, we saw how to set up the Jupyter Notebook with CPU and GPU with the PVC attached and how to setup the PVC to store our required data for lifetime. We also learned more about deployment, service, and the ingress framework structure in Google Cloud. Finally, we learned how to setup Kubeflow in Google Cloud Platform for our following chapters.
然后，我们了解了如何使用附加 PVC 设置 CPU 和 GPU 的 Jupyter Notebook，以及如何设置 PVC 以永久存储我们所需的数据。我们还进一步了解了 Google Cloud 中的部署、服务和 ingress 框架结构。最后，我们学习了如何为后续章节在 Google Cloud Platform 上设置 Kubeflow。

In this chapter, we have gained how to leverage the power of Google Cloud Platform, and how to use your Devops knowledge with Machine Learning to become a MLops.
在本章中，我们了解了如何利用 Google Cloud Platform 的强大功能，以及如何将您的 DevOps 知识与机器学习结合起来成为 MLOps。

### 1.9 Reference
### 1.9 参考

https://kubernetes.io/docs/tutorials/kubernetes-basics/

https://kubernetes.io/docs/reference/

https://github.com/kubernetes/kubernetes

https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/

## Developing Kubeflow Pipeline in GCP
## 在 GCP 中开发 Kubeflow Pipeline

In this chapter, we will build an end-to-end TensorFlow classification Model deployment with Kubeflow Orchestration, which includes deploying Kubeflow in Kubernetes Cluster in GCP, building the pipeline components for the model with Docker and Kubeflow SDK, and then serving the Model with KF serving to have an endpoint for prediction. We will also track the monitoring and performance for our serving traffic endpoint in Grafana Dashboard.
在本章中，我们将使用 Kubeflow 编排构建端到端的 TensorFlow 分类模型部署，其中包括在 GCP 的 Kubernetes 集群中部署 Kubeflow，使用 Docker 和 Kubeflow SDK 为模型构建流水线组件，然后使用 KF serving 提供模型以获得预测端点。我们还将在 Grafana 仪表板中跟踪我们服务流量端点的监控和性能。

## Structure
## 结构

In this chapter, we will cover the following topics:
本章将涵盖以下主题：

- Problem statement
- 问题陈述
- Getting started in GCP Kubeflow and Docker setup
- 在 GCP Kubeflow 和 Docker 设置中入门
- Breakdown technique to build the production pipeline
- 构建生产流水线的分解技术
- Building the Kubeflow Pipeline components for TensorFlow model
- 为 TensorFlow 模型构建 Kubeflow Pipeline 组件
- Serving the Model with KF Serving
- 使用 KF Serving 提供模型
- Building the pipeline end to end
- 端到端构建流水线
- Monitoring the performance with Grafana dashboard
- 使用 Grafana 仪表板监控性能

## Objectives
## 目标

In this chapter, we will learn the following:
在本章中，我们将学习以下内容：

- How to use Docker and Kubernetes to build the Kubeflow Pipeline.
- 如何使用 Docker 和 Kubernetes 构建 Kubeflow Pipeline。
- How to build the individual pipeline components like the training and model evaluation.
- 如何构建单个流水线组件，如训练和模型评估。
- How to serve the Model with KF serving and predict the model request, and monitor with the Grafana Dashboard.
- 如何使用 KF serving 提供模型并预测模型请求，并使用 Grafana 仪表板进行监控。
- How to use Kubernetes, and many Google Cloud Platform to leverage the power of Machine learning with Devops Knowledge.
- 如何使用 Kubernetes 和许多 Google Cloud Platform 来利用 DevOps 知识的机器学习能力。

### 2.1 Problem statement
### 2.1 问题陈述

In this example, we have a classification dataset of breast cancer, and it will have 30 attributes. We have to classify the Malignant and Benign.
在此示例中，我们有一个乳腺癌分类数据集，它将有 30 个属性。我们需要对 Malignant 和 Benign 进行分类。

Benign. Benign. Benign. Benign. Benign. Benign. Benign. Benign.
Benign. Benign. Benign. Benign. Benign. Benign. Benign. Benign.
Benign. Benign. Benign. Benign. Benign. Benign. Benign. Benign.
Benign. Benign. Benign. Benign. Benign. Benign. Benign. Benign.
Benign.

Benign.

### 2.2 Getting started in GCP Kubeflow setup
### 2.2 在 GCP Kubeflow 设置中入门

So, before we begin, we must setup the Kubeflow Cluster in GCP; please refer to *Chapter 1: Introduction to Kubeflow & Kubernetes Cloud* section 1.6 (Getting Started in GCP Kubeflow setup).
因此，在开始之前，我们必须在 GCP 中设置 Kubeflow 集群；请参阅 *第 1 章：Kubeflow 和 Kubernetes 云简介* 第 1.6 节（在 GCP Kubeflow 设置中入门）。

### 2.3 Breakdown technique to build production pipeline
### 2.3 构建生产流水线的分解技术

In this section, we will see how to frame your business problem, so that we can break down the Machine learning life cycle components, and build each component, so that we can build the Kubeflow pipeline.
在本节中，我们将了解如何构建您的业务问题，以便我们可以分解机器学习生命周期组件并构建每个组件，从而构建 Kubeflow 流水线。

The following is the high level framework from the Jupyter Notebook code to the Pipeline components, and serving and hosting that in Cloud.
以下是从 Jupyter Notebook 代码到流水线组件的高级框架，以及在云中提供和托管该框架。

![](img/8f8a671916d96b455297952d0f37b96c_110_0.png)

Figure 2.1: Pipeline Components E2E Architecture
图 2.1：流水线组件 E2E 架构

We will Dockerize each and every component, and push to the container registry of any Cloud, like for AWS, GCP, Azure, so that we can use that in the Kubeflow pipeline.
我们将对每个组件进行 Docker 化，并推送到任何云的容器注册表中，例如 AWS、GCP、Azure，以便我们可以在 Kubeflow 流水线中使用它。

### Steps to perform:
### 执行步骤：

**Data Extraction or** Let's say we have our machine learning; the first component is to extract the data from any sources like S3 bucket, Cloud Storage, and so on. Now, we will write the single component of the Input data sources and connection between Kubeflow components to all the data sources in the Python code.

And a next a service account in json format will be used so that we can connect to external source. Then, we will Dockerize the component.
**Data Extraction or** 假设我们有机器学习；第一个组件是从任何来源（如 S3 存储桶、Cloud Storage 等）提取数据。现在，我们将在 Python 代码中编写输入数据源的单个组件以及 Kubeflow 组件与所有数据源之间的连接。

接下来将使用 json 格式的服务账号，以便我们可以连接到外部源。然后，我们将对组件进行 Docker 化。

![](img/8f8a671916d96b455297952d0f37b96c_111_0.png)

*Figure 2.2: Pipeline Component 1: Data Ingestion*
*图 2.2：流水线组件 1：数据摄取*

**Data** The next component in our machine learning project is to pre-process or feature the engineering step. Here, we will build or transform all the incoming data which will be required for the training, according to all the use case like Computer vision, NLP, Structured data with the respective business pre-processing logic, and we will save the artifacts or the transformed data back to the Storage bucket for future reference.
**Data** 我们机器学习项目中的下一个组件是预处理或特征工程步骤。在这里，我们将构建或转换所有传入的数据，这些数据将根据所有用例（如计算机视觉、NLP、结构化数据）以及相应的业务预处理逻辑用于训练，并将工件或转换后的数据保存回存储桶以供将来参考。

![](img/8f8a671916d96b455297952d0f37b96c_112_0.png)

Figure 2.3: Pipeline Component 2: Data Pre-processing
图 2.3：流水线组件 2：数据预处理

So, here we will train the model it can any TensorFlow or Sklearn, and so on with our pre-process data, and will save the model artifacts and logs in the external storage and internally in the native Kubernetes' Persistent Volume Claim
因此，在这里我们将使用预处理数据训练模型，可以是任何 TensorFlow 或 Sklearn 等，并将模型工件和日志保存到外部存储以及 Kubernetes 原生的持久卷声明中

![](img/8f8a671916d96b455297952d0f37b96c_112_1.png)

Figure 2.4: Pipeline Component 3: Training
图 2.4：流水线组件 3：训练

Similarly, like the preceding step, we will build the evaluator component for the Kubeflow pipeline and then we will serve the model by loading the model from any storage like S3, Cloud Bucket, and so on.
类似于前一步，我们将为 Kubeflow 流水线构建评估器组件，然后通过从任何存储（如 S3、Cloud Bucket 等）加载模型来提供模型。
