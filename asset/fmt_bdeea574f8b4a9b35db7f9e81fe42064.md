
FROM julia:latest

COPY Project.toml server.jl nqueens/

WORKDIR nqueens

RUN julia -e "using Pkg; pkg\"activate .\"; pkg\"instantiate\"; "

CMD julia server.jl

```

让我们讨论前面的代码行：

1. 我们采用基础 Julia Docker 容器。
2. 将 `Project.toml` 和 `server.jl` 复制到工作目录。
3. 我们使用 Julia 包管理更新容器。
4. 最后，我们设置容器运行时要启动的命令。

您可以使用以下命令构建 Docker 镜像：

```bash
$ sudo docker build –t queens .
```

可以使用 `docker run queens` 启动容器。您可以使用与之前相同的客户端，但请确保将服务器的 IP 地址更改为 Docker 容器的 IP 地址。`SimpleContainerGenerator` 包有助于根据某些元数据构建 DockerFile 配置。

## Kubernetes：编排容器

虽然 Docker 是容器管理的事实标准，但 Kubernetes 是云部署最常用的编排平台。云原生计算基金会认证了 90 多个支持 Kubernetes 的平台以符合 API 标准。一些知名的产品如下：

* 亚马逊网络服务的 **弹性 Kubernetes 服务 (EKS)**
* 微软 Azure 的 **Azure Kubernetes 服务 (AKS)**
* Google 的 **Google Kubernetes Engine (GKE)**

因此，使用 Docker 创建的 Julia 容器可以使用 Kubernetes 在几乎所有知名的云平台上进行编排。`Kuber` 包提供了管理 Kubernetes 编排环境的 Julia API。关于在 Azure AKS 上使用 Kuber 编排容器的教程已经可用。该教程提供了创建新节点、启动它们的方法，并提供了删除和清理资源的步骤。各种 Kubernetes 节点和 Pod 的指标也可以从 Julia 查询。我们将尝试使用以下步骤将我们之前创建的容器部署到 **Azure Kubernetes 服务 (AKS)**：

我们需要安装 Azure **命令行界面 (CLI)**。这适用于 Windows、Mac OS X 和 Linux。

1. 使用管理员登录和以下命令登录 Azure 环境：
```bash
$ az login
```

2. 使用以下命令在 Azure 门户中创建资源组：
```bash
az group create --name HOJP --location centralindia
```
您也可以使用门户执行相同操作。

3. 在 HOJP 资源组中创建 Kubernetes 集群，如下所示：
```bash
$ az aks create --resource-group HOJP --name hojpcluster --node-count 1 --enable-addons monitoring --generate-ssh-keys
```
对于这个实验性集群，我们仅使用一个节点。

4. 我们需要使用以下命令缓存凭据以供将来使用：
```bash
$ az aks get-credentials --resource-group HOJP --name hojpcluster
```

5. 此外，我们需要 AKS 客户端进行某些操作，必须使用以下命令安装它：
```bash
$ sudo az aks install-cli
```
您将能够使用 `kubectl` 执行许多 Kubernetes 命令。

6. `kubectl proxy` 对于通过 Web 服务连接到 Azure Kubernetes 服务很有用。

7. 您需要将 Docker 容器安装到 AKS 中。镜像必须驻留在 AKS 环境中，并必须在 Azure 容器注册表中注册，以便它们可以被拉取到容器中。您可以使用以下命令执行此操作：
```bash
$ az acr create -n hojpreg -g HOJP --sku Standard
```

8. 注册表可能需要身份验证才能推送和拉取镜像。一种为注册表提供 Azure 管理员访问权限的方法是将注册表附加到集群。但这不建议用于真正的生产 Azure 部署。
```bash
$ az aks update -n hojpcluster -g HOJP --attach-acr hojpreg
```

9. 现在您可以使用以下命令创建 Docker 镜像并将其推送到 Azure 容器注册表：
```bash
$ docker build . -f Dockerfile -t hojpreg.azurecr.io/kubqueens

$ docker push hojpreg.azurecr.io/kubqueens
```
考虑到您的网络连接，这可能需要一些时间。镜像大小可能有几百兆字节。

### 使用 Kuber.jl 部署

现在镜像已在 AKS 注册表中注册，我们将使用 `Kuber` 包部署服务，如下所示：

1. 启动一个通过代理连接 AKS 的上下文：
```julia
using Kuber

ctx = Kuber.KuberContext()
```

2. 从 kubqueens 镜像获取由一个或多个容器服务的 Pod，如下所示：
```julia
kubqueens_pod = kuber_obj(ctx, """

{
"kind": "Pod",
"metadata":{
"name": "kubqueens-pod",
"namespace": "default",
"labels": {
"name": "kubqueens-pod"
}
},
"spec": {
"containers": [{
"name": "kubqueens",
"image": "hojpreg.azurecr.io/kubqueens",
"ports": [{"containerPort": 8888}]
}]
}
}""")
```

3. 创建一个负载均衡器服务，以便容器可以通过公共 URL 暴露。
```julia
kubqueens_service = kuber_obj(ctx, """

{
"kind": "Service",
"metadata": {
"name": "kubqueens-service",
"namespace": "default",
"labels": {"name": "kubqueens-service"}
},
"spec": {
"type": "LoadBalancer",
"ports": [{"port": 8888}],
"selector": {"name": "kubqueens-pod"}
}
}""")
```

4. 两个对象都必须附加到上下文以将它们部署到 AKS 集群，如下所示：
```julia
put!(ctx, kubqueens_pod);
put!(ctx, kubqueens_service);
```

5. 现在等待负载均衡器启动：
```julia
while true
    println("waiting for loadbalancer to be configured…")
    status = get(ctx, :Service, "kubqueens-service").status
    if nothing !== status.loadBalancer.ingress &&
        !isempty(status.loadBalancer.ingress)
        println(status.loadBalancer.ingress[1])
        break
    end
    sleep(5)
end
```

6. 我们可以通过使用公共 IP 地址访问 REST 端点来访问 AKS 部署的服务，如下所示：
```bash
C:\>curl http://<public_IP>:8888/webqueens/8
{"data":[4,2,7,3,6,8,5,1],"code":0}
```
您也可以使用前面提到的客户端代码连接到 AKS 并渲染 UI。完整的 Kubernetes 编排器代码可以在 `Chapter-14/kubernetes/kubserver.jl` 中看到。可以通过调用 `delete!` 方法轻松移除服务，如下所示：
```julia
delete!(ctx, kubqueens_service)
delete!(ctx, kubqueens_pod)
```
