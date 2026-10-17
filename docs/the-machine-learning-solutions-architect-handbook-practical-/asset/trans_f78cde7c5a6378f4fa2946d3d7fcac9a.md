

*   **`NodePort`**: `NodePort` 在所有工作节点上打开一个特定端口，任何发送到节点 IP 地址上该端口的流量都会转发到该端口背后的服务。节点的 IP 地址需要能够从外部来源路由。下图展示了使用 `NodePort` 的通信流程：

    ![](OEBPS/Images/B20836_06_07.png)

    图 6.7: 通过 NodePort 访问 Kubernetes 服务

    `NodePort` 使用简单，但也存在一些限制，例如每个 `NodePort` 只能对应一个服务、需使用固定端口范围（`3000` 到 `32767`），并且需要知道各个工作节点的 IP 地址。

*   **`Load balancer`**: 当使用 AWS 等云服务提供商时，负载均衡器是一种将服务暴露到互联网的方式。使用负载均衡器，你会获得一个可从互联网访问的公共 IP 地址，所有发送到该 IP 地址的流量都会转发到负载均衡器背后的服务。负载均衡器不是 Kubernetes 的一部分，而是由 Kubernetes 集群所在的云基础设施提供（例如 AWS）。下图展示了从负载均衡器到服务和 Pod 的通信流程：

    ![](OEBPS/Images/B20836_06_08.png)

    图 6.8: 通过负载均衡器访问 Kubernetes 服务

    负载均衡器允许你选择要使用的确切端口，并且可以支持每个服务多个端口。但是，它确实需要每个服务配备一个独立的负载均衡器。

*   **`Ingress`**: Ingress 网关是集群的入口点。它充当负载均衡器，并根据路由规则将传入流量路由到不同的服务。

    ![](OEBPS/Images/B20836_06_09.png)

    图 6.9: 通过 Ingress 访问 Kubernetes 服务

    Ingress 与负载均衡器和 `NodePort` 的不同之处在于，它充当代理来管理集群的流量。它与 `NodePort` 和负载均衡器协同工作，并将流量路由到不同的服务。Ingress 方式正在变得越来越常用，尤其是与负载均衡器结合使用时。

    除了管理来自集群外部的网络流量之外，Kubernetes 网络管理的另一个重要方面是控制集群内不同 Pod 和服务之间的流量流动。例如，你可能希望允许某些流量访问 Pod 或服务，同时拒绝来自其他来源的流量。这对于基于微服务架构构建的应用程序尤其重要，因为可能有许多服务或 Pod 需要协同工作。这种微服务网络也称为 `service mesh`。随着服务数量的增加，理解和管理网络要求（例如 `service discovery`、`network routing`、`network metrics` 和 `failure recovery`）变得具有挑战性。`Istio` 是一种开源的服务网格管理软件，它可以轻松在 Kubernetes 上管理大型服务网格，并提供以下核心功能：

*   **`Ingress`**: Istio 提供一个 Ingress 网关，可用于将服务网格内的 Pod 和服务暴露到互联网。它充当负载均衡器，管理服务网格的入站和出站流量。网关只允许流量进出网格——它不执行流量路由。要将流量从网关路由到服务网格内的服务，你需要创建一个名为 `VirtualService` 的对象来提供路由规则，以将传入流量路由到集群内的不同目标，并且你需要在虚拟服务和网关对象之间创建绑定以连接两者。

*   **`Network traffic management`**: Istio 提供基于规则的简单网络路由，以控制不同服务之间的流量和 API 调用流动。安装 Istio 后，它会自动检测集群中的服务和端点。Istio 使用名为 `VirtualService` 的对象来提供路由规则，以将传入流量路由到集群内的不同目标。Istio 使用名为 `gateway` 的负载均衡器来管理网络网格的入站和出站流量。`gateway` 负载均衡器只允许流量进出网格——它不执行流量路由。要将流量从网关路由，你需要在虚拟服务和 `gateway` 对象之间创建绑定。

    为了管理进出 Pod 的流量，一个 Envoy 代理组件（又称 `sidecar`）会被注入到 Pod 中，它拦截并决定如何路由所有流量。管理 sidecar 流量配置和服务发现的 Istio 组件称为 `Pilot`。`Citadel` 组件管理服务间和最终用户的身份验证。`Gallery` 组件负责将其他 Istio 组件与底层 Kubernetes 基础设施隔离开来。下图展示了 Kubernetes 上 Istio 的架构：

    ![](OEBPS/Images/B20836_06_10.png)

    图 6.10: Istio 架构

    Istio 还支持安全性和可观测性，这对于构建生产级系统至关重要：

*   **`Security`**: Istio 为服务间通信提供身份验证和授权。

*   **`Observability`**: Istio 捕获集群内所有服务通信的指标、日志和跟踪。指标示例包括网络延迟、错误和饱和度。跟踪示例包括网格内的调用流和服务依赖关系。

    Istio 可以处理广泛的部署需求，例如负载均衡和服务间身份验证。它甚至可以扩展到其他集群。

# 安全性和访问管理

安全性是在 Kubernetes 上构建生产级系统时的关键考量因素。作为计划将 Kubernetes 用作机器学习基础平台的从业者，熟悉 Kubernetes 的各种安全性方面非常重要。

Kubernetes 拥有许多内置的安全性功能。这些安全性功能允许你对不同的 Kubernetes API 和服务实施细粒度的网络流量控制和访问控制。在本节中，我们将讨论网络安全性、身份验证和授权。

## API 身份验证和授权

对 Kubernetes API 的访问可以对用户和 Kubernetes `service accounts`（服务帐户为在 Pod 中运行的进程提供身份）进行身份验证和授权。

用户在 Kubernetes 之外处理，Kubernetes 有多种用户身份验证策略：

*   **`X.509 client certificate`**: 将签名证书发送到 API 服务器进行身份验证。API 服务器通过证书颁发机构验证此证书以验证用户。

*   **`Single sign-on with OpenID Connect`** (`OIDC`): 用户与 OIDC 提供商进行身份验证并接收一个承载令牌（`JSON Web Token` (`JWT`)，其中包含有关用户的信息。用户将承载令牌传递给 API 服务器，API 服务器通过检查令牌中的证书来验证令牌的有效性。

*   **`HTTP basic authentication`**: HTTP 基本身份验证要求将用户 ID 和密码作为 API 请求的一部分发送，并针对与 API 服务器关联的密码文件验证用户 ID 和密码。

*   **`Authentication proxy`**: API 服务器从 HTTP 标头中提取用户身份，并通过证书颁发机构验证用户。

*   **`Authentication webhook`**: 使用外部服务来处理 API 服务器的身份验证。

