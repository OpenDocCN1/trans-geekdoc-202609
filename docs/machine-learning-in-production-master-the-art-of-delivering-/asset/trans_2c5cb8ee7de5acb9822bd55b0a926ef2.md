

```
24. args:
25. - -c
26. - |
27. echo "List of files and directories within the current working directory"
28. ls -l
29.
30.# Deploy container image to GKE
31.- name: "gcr.io/cloud-builders/gke-deploy"
32. id: Deploy on GKE
33. args:
34. - run
35. - --filename=k8s/
36. - --image=gcr.io/$PROJECT_ID/mlapp:latest
37. - --location=us-west1-b
38. - --cluster=mlkube
```

在前面的文件中，主要使用了三个（受支持的）构建器镜像：

- **gcr.io/cloud-builders/docker**: 构建并将 Docker 容器镜像推送到容器注册表
- **gcr.io/cloud-builders/gcloud**: 运行内联 Bash 脚本
- **gcr.io/cloud-builders/gke-deploy**: 在 GKE 中部署容器化应用

此外，python:3.7-slim 是用于使用 tox 测试代码的公开可用镜像。如果要从 Docker Hub 使用任何镜像，只需在单引号中提供镜像名称即可。但是，如果镜像来自其他注册表，则需要在单引号中指定完整的注册表路径。构建步骤的 args 字段接受参数列表，并将其传递给由 name 字段引用的镜像。

## 容器注册表

容器注册表是 GCP 提供的一种用于管理和存储私有容器镜像的服务。它允许用户安全地推送和拉取容器镜像。在此示例中，Docker 容器镜像将被推送到容器注册表。Kubernetes 引擎将拉取该镜像以在云端部署 ML 应用。

容器注册表使用主机名、项目 ID、镜像以及标签或镜像摘要来访问镜像，其中镜像摘要是镜像内容的 sha256 哈希值。格式如下：

```
HOSTNAME/PROJECT-ID/IMAGE : TAG
```

Or

```
HOSTNAME/PROJECT-ID/IMAGE : @IMAGE-DIGEST
```

启用容器注册表 API 后，下图显示了 GCP 容器注册表，其中 mlapp 是应用名称，gcr.io 是主机名。目前，gcr.io 在美国托管镜像。

![](img/cc4299656808e62a294f1843a1e18e72_336_0.png)

图 12.5：容器注册表

## Kubernetes

容器编排是运行容器化工作负载和服务所需操作流程的自动化。它可以自动化部署、扩容/缩容、生命周期管理、负载均衡、配置、安全、资源分配、健康监控以及容器网络等任务。

Kubernetes（也称为 K8s 或 Kube）是一个用于容器编排的开源平台。它允许应用在不中断生产环境中运行的应用的情况下随时扩缩容。它可以快速创建多个容器化应用副本以应对流量增加，并在流量减少时自动减少副本数量。

在 Kubernetes 上部署会创建包含容器的 Pod。Pod 是 Kubernetes 环境中的最小单元。一个 Pod 可以包含一个或多个容器。它始终在节点上运行，但一个节点可以拥有多个 Pod。节点只是 Kubernetes 环境中的一个工作节点（VM 或物理机）。所有节点均由控制平面管理。

每个节点都运行 Kubelet 和容器运行时（例如 Docker）。Kubelet 是控制平面与节点之间的通信媒介。它还管理节点中的 Pod 和运行中的容器。Docker 等容器运行时会从注册表拉取镜像，并运行容器化应用。

## Google Kubernetes Engine (GKE)

Google Kubernetes Engine (GKE) 提供用于管理、部署和扩缩容容器化应用的基础架构。GKE 的底层架构由一组组装成集群的 Compute Engine 实例组成。

清单是一个包含要部署的所有组件描述的文件（JSON 或 YAML）。这些清单文件指导 Kubernetes 在容器之间进行网络通信。Kubernetes 将容器部署到集群中，并为容器识别最佳主机。在决定主机后，它会根据预先规划的规格管理容器的生命周期。

在 GCP 控制台中搜索并启用 Kubernetes Engine API，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_337_0.png)

图 12.6：Kubernetes Engine API

接下来，单击 GCP 账户右上角的“Activate Cloud Shell”图标。它将打开一个基于云的终端：

```
gcloud container clusters create mlkube --zone "us-west1-b" --machine-type "n1-standard-1" --num-nodes "1" --project mlops-54321
```

```
Created [https://container.googleapis.com/v1/projects/mlops-54321/zones/us-west1-b/clusters/mlkube]
To inspect the contents of your cluster, go to: https://console.cloud.google.com/kubernetes/workload/_/gcloud/us-west1-b/mlkube?project=mlops-54321
Kubeconfig entry generated for mlkube.
NAME: mlkube
LOCATION: us-west1-b
MASTER_VERSION: 1.22.8-gke.202
MASTER_IP: 34.168.38.219
MACHINE_TYPE: n1-standard-1
NODE_VERSION: 1.22.8-gke.202
NUM_NODES: 1
STATUS: RUNNING
```

图 12.7：使用 Cloud Shell 创建 Kubernetes 集群

Kubernetes 集群成功创建后，可以使用 GKE 服务查看其详细信息，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_338_0.png)

图 12.8：Kubernetes 集群

所有清单文件都包含 apiVersion 字段。每个 Kubernetes 配置文件都有三个部分：metadata、specification 和 status。metadata 和 specification 由开发人员在配置文件中提供；然而，status 部分由 Kubernetes 管理。例如，如果声明了 2 个副本但只有一个副本正在运行，那么 Kubernetes 会检查状态并创建另一个副本，以使所需状态与实际状态一致。如下所示，Kubernetes 配置文件位于 k8s 目录中。labels 和 selectors 负责连接服务和部署文件。service.yaml 和 deployment.yaml 文件中应使用相同的标签，以便服务和部署之间成功通信。

```
k8s
|-- deployment.yaml
|-- service.yaml
```

## deployment.yaml

此文件包含 Kubernetes 部署的配置，例如要创建的副本数和要部署的容器镜像。deployment.yaml 的作用是启动带有容器化应用的 Pod，并确保 Kubernetes 集群中始终运行所需数量的副本。在以下文件中，template 是 Pod 的蓝图。它有自己的 metadata 和 specification。在此示例中，replicas 字段设置为 2，这意味着它将创建两个 Pod 副本。

```
1. apiVersion: apps/v1
2. kind: Deployment
3. metadata:
4. name: loan-prediction
5. spec:
6. replicas: 2
7. selector:
8. matchLabels:
9. app: mlapp
10. template:
11. metadata:
12. labels:
13. app: mlapp
14. spec:
15. containers:
16. - name: loan-prediction-app
17. image: gcr.io/mlops-54321/mlapp:latest
18. ports:
19. - containerPort: 8000
```

## service.yaml

此文件将容器化应用连接到最终用户。service.yaml 的作用是向由 deployment.yaml 创建的 Pod 公开一个接口，从而实现集群与服务之间的网络访问。它将部署的应用公开到外部世界。容器化应用的端口 8000 与端口 80 映射。在 ports 中，可以指定多个端口。在此示例中，服务类型为 LoadBalancer，它将通过 GCP（云提供商）的负载均衡器公开服务。标签选择器有助于定位 Pod。在此示例中，mlapp 是一个标签。

```
1. apiVersion: v1
2. kind: Service
3. metadata:
4. name: mlapp
5. spec:
6. type: LoadBalancer
7. selector:
8. app: mlapp
9. ports:
10. - port: 80
11. targetPort: 8000
```

注意：在 targetPort 字段中，使用大写字母 'P'，因为它是一个键值对。在键值对中，第二个单词的首字符应为大写。

## 使用 Cloud Shell 进行部署 – 手动触发

首先，打开 Cloud Shell 并使用 `git clone` 命令克隆远程 Git 仓库。现在，代码文件在 GCP Cloud Shell 终端中可用。使用以下命令手动运行 `cloudbuild.yaml` 文件：

```
gcloud builds submit --config cloudbuild.yaml --project=mlops-54321
```

此命令执行需要几分钟。在此场景中，流水线被手动触发，一系列步骤将从 `cloudbuild.yaml` 文件依次执行。

下图显示了前面命令的输出，其中给出了使用 Kubernetes 部署的应用的详细信息，例如部署的 ML 应用的 IP 地址、源、持续时间、状态，以及工作负载、服务、配置和存储的 GKE URL。

![](img/cc4299656808e62a294f1843a1e18e72_340_0.png)

图 12.9：使用手动触发在 GKE 上部署 ML 应用

