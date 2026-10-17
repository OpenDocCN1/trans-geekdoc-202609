
在上一章节，我们将工作集中在使我们的服务可部署，但我们只在本地部署了它。在这一章节，我们将把我们的服务部署到云端并将其放在 Internet 上。Kubernetes 抽象了应用程序所需的资源——容器、网络、存储卷等——类似于 Go 抽象操作系统和处理器架构，使您可以在每个系统上运行相同的程序。因此，将本地 Kubernetes 集群移动到云端所需的更改可能很少，甚至不需要。

主导市场的三大云平台是：Google Cloud Platform (GCP)、^([\[63\]](#f_0088.xhtml#FOOTNOTE-63)) Amazon Web Services (AWS)、^([\[64\]](#f_0088.xhtml#FOOTNOTE-64)) 和 Microsoft Azure。^([\[65\]](#f_0088.xhtml#FOOTNOTE-65)) 这三个平台提供相似的功能集，并拥有各自的 Kubernetes 服务。由于 Kubernetes 消除了平台之间的差异，我们可以轻松部署到任一平台，在提供商之间切换（甚至可以与提供商协商更优价格），或同时在所有平台上运行。本章节，我们将把服务部署到 Google Cloud Platform。

GCP 提供免费产品的免费层级，带有限制，并提供 12 个月的免费试用期内 $300 信用额度。对于本书的工作而言，重要的是免费层级包含一个 Kubernetes 集群和 5 GB 的存储空间——足以将我们的服务部署到云端。尽管 Google 不会在免费试用期间向您收费，但您需要一张信用卡来注册，并且在试用期间，Google 会显示一个横幅，显示您还有多少信用额度和剩余时间，以便您了解状态。一旦试用期结束，或者您决定购买服务并使用平台的更多资源时，Google 要求您启用自动计费。

## 创建 Google Kubernetes Engine 集群

让我们先通过创建 Google Cloud 账户和 Google Kubernetes Engine (GKE) 集群来为您设置 Google Cloud，并配置您的计算机的 Docker 和 `kubectl` 以便与云服务配合工作。GKE 是 GCP 的托管 Kubernetes 服务，它允许您通过单击即可创建一个 Kubernetes 集群。GKE 集群由 Google 的站点可靠性工程师管理，确保您的集群可用且保持最新，因此您可以专注于应用程序，而非 Kubernetes。

### 使用 Google Cloud 注册

打开 GCP 注册表单^([\[66\]](#f_0088.xhtml#FOOTNOTE-66))，登录到您现有的 Google 账户或创建新账户。按照表单指示，填写您的信息直到开始免费试用。然后继续下一步，创建 Kubernetes 集群。

### 创建 Kubernetes 集群

导航到 Kubernetes Engine 服务^([\[67\]](#f_0088.xhtml#FOOTNOTE-67))，点击“创建集群”以打开集群创建表单（如下图所示）。在表单中，将名称字段从默认的 cluster-1 更改为 proglog。保持位置类型为默认（Zonal）。在主版本部分，选择“Release 频道”单选框，并选择当前的“Regular 频道”，即 1.16.11-gke.5（截至本文撰写时）。然后点击页面底部的“创建”按钮。页面将刷新并显示一个指示 GCP 正在配置集群的旋转图标。当集群准备就绪时，您会看到一个绿色对勾，如[示例](#f_0085.xhtml#fig.gke1)所示。

![images/gke-page.png](Images/gke-page.png)

### 安装和验证 gcloud

Google Cloud 提供一个包含多种工具和库的云软件开发套件 (SDK)，用于与 Google 服务协作。该 SDK 包含 gcloud CLI，我们需要它来与 Google Cloud API 交互并配置 Docker。按照您的操作系统在 Google Cloud Developer Tools 页面上的安装说明安装最新的 Cloud SDK。^([\[68\]](#f_0088.xhtml#FOOTNOTE-68))

安装 gcloud CLI 后，运行以下命令对您的账户进行验证：

| ​  || $ gcloud auth login |
| --- | --- |
现在，您可以运行 gcloud 命令来操作您账户中的资源。获取您的项目 ID，并配置 gcloud 使用该项目作为默认值：

| ​  || $ PROJECT\_ID=$(gcloud projects list | tail -n 1 | cut -d' ' -f1) |
| --- | --- |
| ​  || $ gcloud config set project $PROJECT\_ID |
我们将多次使用这个 PROJECT\_ID 环境变量，因此如果您打开新的终端会话，请确保再次设置该变量。

### 将我们的服务镜像推送到 Google 的容器注册表

我们需要让我们的服务镜像能够被 GKE 集群的节点拉取，因此需要将镜像推送到 Google 的 Container Registry。运行以下命令将镜像推送到注册表：

| ​  || $ gcloud auth configure-docker |
| --- | --- |
| ​  || $ docker tag github.com/travisjeffery/prolog:0.0.1 \\ |
| ​  || gcr.io/$PROJECT\_ID/prolog:0.0.1 |
| ​  || $ docker push gcr.io/$PROJECT\_ID/prolog:0.0.1 |
第一行配置 Docker 使用 Google 的 Container Registry，并使用 gcloud 作为这些注册表的凭据帮手。您可以打开 Docker 配置文件（默认位于 ~/.docker/config.json）查看配置变更。第二行为 gcr.io 注册表创建新标签。gcr.io 注册表位于美国（但这可能会改变），如果您需要在特定区域存储镜像，还可以使用 us.gcr.io、eu.gcr.io 和 asia.gcr.io。第三行将镜像推送到注册表。

### 配置 kubectl

最后的设置允许 `kubectl` 和 Helm 调用我们的 GKE 集群：

| ​  || $ gcloud container clusters get-credentials proglog --zone us-central1-c |
| --- | --- |
| ​  || Fetching cluster endpoint and auth data. |
| ​  || kubeconfig entry generated for proglog. |
此命令会更新您的 kubeconfig 文件（默认位于 ~/.kube/config），将 `kubectl` 指向 GKE 集群。Helm 也使用该 kubeconfig 文件。

好了，我们已完成 Google Cloud 项目的设置、创建 GKE 集群，并配置客户端以管理集群。我们可以直接将服务部署到 GKE，但当前的部署设置无法使服务在 Internet 上可用。

让我们修复它。

## 使用 Metacontroller 创建自定义控制器

我们可以直接部署服务而无需修改，服务的功能与在本地 Kind 集群中相同。但我们希望扩展部署设置，使服务能够在 Internet 上提供。由于我们的服务通过客户端负载均衡，每个 pod 需要其 own 静态 IP，因此需要为每个 pod 创建一个负载均衡服务。虽然理想情况下 Kubernetes 能自动创建和删除负载均衡服务以适应 pod 的伸缩，但它默认不支持此功能。

Enter Metacontroller.

Metacontroller^([\[69\]](#f_0088.xhtml#FOOTNOTE-69)) 是一个 Kubernetes 插件，它简化了编写和部署自定义控制器的过程。Metacontroller 让我们能够挂载到 Kubernetes 的变更上，从而可以与我们自己的变更组合。它会处理与 Kubernetes API 的所有交互，包括在您 behalf 运行基于级别的重新调conciliation 循环。您只需接收描述 Kubernetes 观察状态的 JSON，并返回描述您期望状态的 JSON。您可以使用 Kubernetes 编写需要编写 Operator^([\[70\]](#f_0088.xhtml#FOOTNOTE-70))（一种流行的扩展 Kubernetes 的模式）所需的功能，但所需代码和努力远少于 Operator。

### 安装 Metacontroller

安装 Metacontroller 需要应用几个定义 Metacontroller API 和授权的 YAML 文件，以便这些 API 能够管理 Kubernetes 集群的资源。您可以使用两种 Metacontroller API：