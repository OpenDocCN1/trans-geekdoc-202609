

创建 EKS 集群后，你将探索 EKS 环境以检查其部分核心组件，然后学习如何部署容器化的 Jupyter Notebook 应用程序，并使其可从互联网访问。

让我们完成以下步骤以开始：

1. 启动 AWS CloudShell 服务。

登录到你的 AWS 账户，选择 **Oregon** 区域，并启动 AWS CloudShell。CloudShell 是一项 AWS 服务，提供基于浏览器的 **Linux** 终端环境，用于与 AWS 资源交互。使用 CloudShell，你可以使用 AWS 控制台凭据进行身份验证，并可以轻松运行 `AWS CLI`、`AWS SDK` 和其他工具。

1. 安装 `eksctl` 实用程序。

按照 Unix 的安装说明在 [https://github.com/weaveworks/eksctl/blob/main/README.md#installation](https://github.com/weaveworks/eksctl/blob/main/README.md#installation) 安装 eksctl。`eksctl` 实用程序是用于管理 EKS 集群的命令行实用程序。我们将使用 `eksctl` 实用程序在 Amazon EKS 上创建 Kubernetes 集群，如 *步骤 3* 中所示：

1. 运行以下命令，在你的 AWS 账户的 **Oregon** 区域内开始创建 EKS 集群。运行设置大约需要 15 分钟才能完成：

```
eksctl create cluster --name <cluster name> --region us-west-2
```

该命令将启动一个 `cloudformation` 模板，并将创建以下资源：

* 一个在新的 Amazon `virtual private cloud` (`VPC`) 内包含两个工作节点的 Amazon EKS 集群。Amazon EKS 提供完全托管的 Kubernetes 主节点，因此你不会在私有 VPC 中看到主节点。

* 一个保存在 CloudShell 上 `/home/cloudshell-user/.kube/config` 目录中的 EKS 集群配置文件。`config` 文件包含 API 服务器 `url` 地址、用于管理集群的管理员用户名以及用于向 Kubernetes 集群进行身份验证的客户端证书等详细信息。`kubectl` 实用程序使用 `config` 文件中的信息连接并向 Kubernetes API 服务器进行身份验证。

* EKS 将工作节点组织为称为 `nodegroup` 的逻辑组。运行以下命令查找 `nodegroup` 名称。你可以在 EKS 管理控制台中查找集群的名称。节点组的名称应该类似于 `ng-xxxxxxxx`：

```
eksctl get nodegroup --cluster=<cluster name>
```

1. 安装 `kubectl` 实用程序。

按照 [https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html) 中的说明为 Linux 安装 kubectl。你需要知道 Kubernetes 服务器的版本，以便安装匹配的 kubectl 版本。你可以使用 `kubectl version --short` 命令查找 Kubernetes 服务器的版本。

1. 探索集群。

现在集群已启动，让我们稍微探索一下。尝试在 CloudShell 终端中运行以下命令，看看返回的内容：

![](OEBPS/Images/B20836_06_12.png)

图 6.12: kubectl 命令

1. 部署 Jupyter Notebook。

让我们将 Jupyter Notebook 服务器部署为容器化应用程序。复制并运行以下代码块。它应该创建一个名为 `deploy_Jupyter_notebook.yaml` 的文件。我们将使用 Docker Hub 镜像仓库中的容器镜像：

```
cat << EOF > deploy_Jupyter_notebook.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
name: jupyter-notebook
labels:
app: jupyter-notebook
spec:
replicas: 1
selector:
matchLabels:
app: jupyter-notebook
template:
metadata:
labels:
app: jupyter-notebook
spec:
containers:
- name: minimal-notebook
image: jupyter/minimal-notebook:latest
ports:
- containerPort: 8888
EOF
```

现在，通过运行以下命令创建一个 Deployment：

```
kubectl apply -f deploy_Jupyter_notebook.yaml.
```

通过执行 `kubectl get pods` 检查 Pod 是否正在运行。

通过运行 `kubectl logs <name of notebook pod>` 检查 Jupyter 服务器 Pod 的日志。在日志中找到包含 `http://jupyter-notebook-598f56bf4b-spqn4:8888/?token=XXXXXXX...` 的部分，并复制令牌 (`XXXXXX…`) 部分。我们将在 *步骤 8* 中使用该令牌。

你还可以通过运行 `kubectl exec --stdin --tty <name of notebook pod> -- /bin/sh` 使用交互式 shell 访问 Pod。运行 `ps aux` 查看运行中的进程列表。你将看到与 Jupyter Notebook 相关的进程。

1. 将 Jupyter Notebook 暴露到互联网。

此时，我们有一个在 Docker 容器中运行的 Jupyter 服务器，该容器位于 AWS VPC 中的两个 EC2 实例上的 Kubernetes Pod 中，但我们无法访问它，因为 Kubernetes 集群没有公开指向容器的路由。我们将创建一个 Kubernetes Service，将 Jupyter Notebook 服务器暴露到互联网，以便可以从浏览器访问。

运行以下代码块以创建新 Service 的规范文件。它应该创建一个名为 `jupyter_svc.yaml` 的文件：

```
cat << EOF > jupyter_svc.yaml
apiVersion: v1
kind: Service
metadata:
name: jupyter-service
annotations:
service.beta.kubernetes.io/aws-load-balancer-type: alb
spec:
selector:
app: jupyter-notebook
ports:
- protocol: TCP
port: 80
targetPort: 8888
type: LoadBalancer
EOF
```

文件创建完成后，运行 `kubectl apply -f jupyter_svc.yaml` 创建服务。应该会创建一个名为 `jupyter-service` 的新 Kubernetes Service 以及一个新的 `LoadBalancer` 对象。你可以通过运行 `kubectl get service` 验证服务。记下并复制与 `jupyter-service` 服务关联的 `EXTERNAL-IP` 地址。

将 `EXTERNAL-IP` 地址粘贴到新的浏览器窗口中，并将你之前复制的令牌输入到 **密码或令牌** 字段中，如以下屏幕截图所示登录。你应该会看到一个 Jupyter Notebook 窗口出现：

![](OEBPS/Images/B20836_06_13.png)

图 6.13: Jupyter 登录屏幕

以下图表显示了你在完成本实践练习后创建的环境。

![](OEBPS/Images/B20836_06_14.png)

图 6.14: EKS 集群上的 Jupyter Notebook 部署

恭喜，你已成功在 AWS 上创建了一个新的 Amazon EKS 集群，并将 Jupyter 服务器实例作为容器部署到集群上。我们将在下一章中重用此 EKS 集群。但是，如果你计划在一段时间内不使用此 EKS，建议关闭集群以避免不必要的费用。要关闭集群，请先运行 `kubectl delete svc <service name>` 删除服务。然后运行 `eksctl delete cluster --name <cluster name>` 删除集群。

# 摘要

在本章中，我们介绍了 Kubernetes，这是一个强大的容器管理平台，为构建开源 ML 平台提供了基础设施基础。在本章中，你了解了容器，并深入了解了 Kubernetes 的工作原理。此外，你还获得了在 AWS 上利用 AWS EKS 建立 Kubernetes 集群的实践经验。另外，我们探索了将容器化的 Jupyter Notebook 应用程序部署到集群上的过程，从而创建了一个基础数据科学环境。在下一章中，我们将重点转向探索一系列与 Kubernetes 基础设施无缝集成的开源 ML 平台。

# 在 Discord 上加入我们的社区

加入我们社区的 Discord 空间，与作者和其他读者进行讨论：

[https://packt.link/mlsah](https://packt.link/mlsah)

![](OEBPS/Images/QR_Code7020572834663656.png)

# 7

# 开源 ML 平台

