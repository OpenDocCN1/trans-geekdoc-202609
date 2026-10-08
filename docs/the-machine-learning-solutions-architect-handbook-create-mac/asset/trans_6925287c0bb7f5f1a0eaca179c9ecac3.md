
图（图 6.3）显示了 Kubernetes 集群中命名空间（namespaces）、Pod 和容器（containers）之间的关系。在图中，每个命名空间都包含一组 Pod，而每个 Pod 可以包含运行在其内部的一个或多个容器。

- **Deployment：**Kubernetes 使用 Deployment 来创建或修改 Pod 以运行应用程序。例如，为了部署一个容器化应用程序，您创建一个配置文件（通常为 YAML 文件格式），在其中指定详细信息，例如容器部署名称、命名空间、容器镜像 URI、Pod 副本数量以及应用程序的通信端口。在使用 Kubernetes 客户端工具（kubectl）应用部署后，工作节点上将创建运行指定镜像的相应 Pod。以下示例创建了一个符合规范的 Nginx 部署：

```yaml
apiVersion: apps/v1 # 用于创建此部署的 k8s API 版本
kind: Deployment # 类型。在这种情况下是 deployment
metadata:
  name: nginx-deployment # 部署名称
spec:
  selector:
    matchLabels:
      app: nginx # 部署的 app 标签。 
      # 这可用于查找/选择 Pod
  replicas: 2 # 告诉部署运行 2 个匹配的 Pod
template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:1.14.2 # 用于部署的 Docker 容器镜像
          ports:
            - containerPort: 80 # 与容器通信的网络端口
```

接下来的图显示了将上述部署文件应用到 Kubernetes 集群的流程，并创建两个 Pod 来托管两个 Nginx 容器副本：

![](img/bd21298357d8484151447cff0b2f138b_176_0.png)

部署完成后，Deployment 控制器会监控已部署的容器实例。如果某个实例故障，控制器将在工作节点上用另一个实例替换它。

- **Kubernetes Job：** Kubernetes Job 是一种控制器，用于创建一个或多个 Pod 来运行某些任务，并确保任务成功完成。如果某些 Pod 由于节点故障或其他系统问题而失败，Kubernetes Job 将重新创建 Pod 以完成任务。Kubernetes Job 可用于运行批处理任务，例如在大量推理请求上运行批数据处理脚本、ML 模型训练脚本或 ML 批量推理脚本。任务完成后，Pod 不会被终止，因此您可以访问任务日志并检查任务的详细状态。以下运行训练任务的示例模板：

```yaml
apiVersion: batch/v1
kind: Job # 表示这是一个 Kubernetes Job
metadata:
  name: train-job
spec:
  template:
    spec:
      containers:
      - name: train-container
        imagePolicy: Always # 告诉任务在启动时
          始终拉取新的容器镜像
        image: <包含训练内容的 Docker 镜像 uri>
        script:
          command: ["python3", "train.py"] # 告诉
            容器在启动后运行此命令
      backoffLimit: 0
```

- **Kubernetes 自定义资源 (CRs) 和算器 (operators)：** Kubernetes 提供了一系列内置资源，例如满足不同需求的 Pods 或部署。它还允许您像管理内置资源一样创建并管理 CRs，您可以使用相同的工具（如 kubectl）来管理它们。当您在 Kubernetes 中创建自定义资源（CR）时，它会为该资源的每个版本创建一个新的 API（例如，<custom resource name>/<version>）。这也被称为扩展 Kubernetes APIs。要创建 CR，您需要创建一个自定义资源定义（CRD）YAML 文件。要在 Kubernetes 中注册 CRD，只需运行 `kubectl apply -f <name of the CRD yaml file>` 应用该文件。之后，您就可以像使用任何其他 Kubernetes 资源一样使用它。例如，为了在 Kubernetes 上管理自定义训练任务，您可以定义一个包含如下规范的算法名称、数据加密设置、训练镜像、输入数据源、任务失败重试次数、副本数量和任务存活检查频率的 CRD。

Kubernetes operator 是一种在自定义资源上运行的控制器。它监控集群状态并进行更改使当前状态向期望状态移动。operator 封装了特定领域的知识以管理复杂的应用程序。例如，operator 可以处理数据库备份、扩展或升级。接下来的图显示了 operator 与资源之间的交互：

![](img/bd21298357d8484151447cff0b2f138b_178_0.png)

图 6.5 – Operator 与资源的交互

## Kubernetes 上的网络

在 Kubernetes 中，每个 Pod 都会被分配一个自己的 IP 地址，Pod 之间无需 NAT 即可与集群中的其他 Pod 通信。这是因为使用了扁平网络模型，每个 Pod 都可以访问其他任何 Pod。Service 为一组 Pod 提供稳定的 IP 地址和 DNS 名称。

虽然节点、Pod 和服务都分配了集群私有 IP，但这些 IP 无法从集群外部路由。要从集群外部访问 Pod 或服务，您有以下选项：

- **从节点或 Pod 访问：** 您可以使用 `kubectl exec` 命令连接到运行中 Pod 的 shell，并从 shell 访问其他 Pod、节点和服务。
- **Kubernetes Proxy：** 您可以在本地机器上运行 `kubectl proxy --port=<port number>` 命令来访问服务。一旦代理运行，您就可以访问节点、Pod 或服务。例如，您可以使用以下方案访问服务：

```
http://localhost:<port number>/api/v1/proxy/namespaces/<NAMESPACE>/services/<SERVICE NAME>:<PORT_NAME>
```

- **NodePort：** NodePort 在所有工作节点上打开一个特定端口，发送到任何节点 IP 地址上该端口的流量都将转发到该端口后的服务。节点的 IP 需要从外部源可路由。接下来的图（图 6.7）显示了使用 NodePort 的通信流：

![](img/bd21298357d8484151447cff0b2f138b_181_0.png)

图 6.7 – 通过 NodePort 访问 Kubernetes 服务
