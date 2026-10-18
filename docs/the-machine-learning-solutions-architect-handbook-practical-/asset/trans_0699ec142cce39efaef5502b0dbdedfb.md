

服务账户用于为在 Pod 中运行的进程提供身份。它们在 Kubernetes 中创建和管理。默认情况下，服务账户需要位于一个命名空间中。每个命名空间中还有一个 `default` 服务账户。如果 Pod 未分配服务账户，则将默认服务账户分配给该 Pod。服务账户有一个关联的身份验证令牌，保存为 Kubernetes Secret，并用于 API 身份验证。Kubernetes Secret 用于存储敏感信息，例如密码、身份验证令牌和 SSH 密钥。我们将在本章后面更详细地介绍 Secret。

在用户或服务账户经过身份验证后，请求需要获得授权才能执行允许的操作。Kubernetes 使用控制平面中的 API 服务器对经过身份验证的请求进行授权，并且它有几种授权模式：

*   `Attribute-based access control` (`ABAC`): 通过策略向用户授予访问权限。请注意，每个服务账户都有一个对应的用户名。以下示例策略允许 `joe` 用户访问所有命名空间中的所有 API。

    ```
    {
    "apiVersion": "abac.authorization.kubernetes.io/v1beta1",
    "kind": "Policy",
    "spec": {
    "user": "joe",
    "namespace": "*",
    "resource": "*",
    "apiGroup": "*"
    }
    }
    ```

    以下策略允许 `system:serviceaccount:kube-system:default` 服务账户访问所有命名空间中的所有 API：

    ```
    {
    "apiVersion": "abac.authorization.kubernetes.io/v1beta1",
    "kind": "Policy",
    "spec": {
    "user": "system:serviceaccount:kube-system:default",
    "namespace": "*",
    "resource": "*",
    "apiGroup": "*"
    }
    }
    ```

*   `Role-based access control` (`RBAC`): 根据用户的角色授予访问权限。RBAC 使用 `rbac.authorization.k8s.io` API 组进行授权。RBAC API 使用四个 Kubernetes 对象：`Role`、`ClusterRole`、`RoleBinding` 和 `ClusterRoleBinding`。

`Role` 和 `ClusterRole` 包含一组权限。权限是 `additive` 的，这意味着没有拒绝权限，您需要显式添加资源权限。`Role` 对象是命名空间的，用于指定命名空间内的权限。`ClusterRole` 对象不是命名空间的，但可用于授予给定命名空间或集群范围的权限。请参见以下插图：

![](OEBPS/Images/B20836_06_11.png)

图 6.11：Role 与 ClusterRole

以下 `.yaml` 文件为核心 API 组中的默认命名空间内的所有 Pod 资源提供 get、watch 和 list 访问权限：

```
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
namespace: default
name: pod-reader
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "watch", "list"]
```

以下策略允许对集群中所有 Kubernetes 节点进行 get、watch 和 list 访问：

```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
name: nodes-reader
rules:
- apiGroups: [""]
  resources: ["nodes"]
  verbs: ["get", "watch", "list"]
```

`RoleBinding` 和 `ClusterRoleBinding` 将 `Role` 或 `ClusterRole` 对象中定义的权限授予用户或一组用户，并引用 `Role` 或 `ClusterRole` 对象。以下策略将 `joe` 用户绑定到 `pod-reader` 角色：

```
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
name: read-pods
namespace: default
subjects:
- kind: User
name: joe
apiGroup: rbac.authorization.k8s.io
roleRef:
kind: Role
name: pod-reader
apiGroup: rbac.authorization.k8s.io
```

以下 `RoleBinding` 对象将服务账户 `SA-name` 绑定到 `ClusterRole` `secret-reader`：

```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
name: read-secrets-global
subjects:
- kind: ServiceAccount
name: SA-name
namespace: default
roleRef:
kind: ClusterRole
name: secret-reader
apiGroup: rbac.authorization.k8s.io
```

Kubernetes 有一个内置功能，用于存储和管理敏感信息，例如密码。您可以将此敏感信息作为 Kubernetes Secret 存储，而不是直接以纯文本形式存储在 Pod 中，并使用 Kubernetes RBAC 对其提供特定访问权限以创建和/或读取这些 Secret。默认情况下，Secret 存储为未加密的纯文本 Base64 编码字符串，并且可以为 Secret 启用静态数据加密。以下策略显示如何创建用于存储 AWS 访问凭据的 Secret：

```
apiVersion: v1
kind: Secret
metadata:
name: aws-secret
type: Opaque
data:
AWS_ACCESS_KEY_ID: XXXX
AWS_SECRET_ACCESS_KEY: XXXX
```

在 Pod 中使用 Secret 有几种方式：

*   作为 Pod 规范模板中的环境变量：

    ```
    apiVersion: v1
    kind: Pod
    metadata:
    name: secret-env-pod
    spec:
    containers:
    - name: mycontainer
    image: redis
    env:
    - name: SECRET_AWS_ACCESS_KEY
    valueFrom:
    secretKeyRef:
    name: aws-secret
    key: AWS_ACCESS_KEY_ID
    - name: SECRET_AWS_SECRET_ACCESS_KEY
    valueFrom:
    secretKeyRef:
    name: aws-secret
    key: AWS_SECRET_ACCESS_KEY
    restartPolicy: Never
    ```

    容器内的应用程序代码可以像访问其他环境变量一样访问 Secret。

*   作为挂载到 Pod 的卷中的文件：

    ```
    apiVersion: v1
    kind: Pod
    metadata:
    name: pod-ml
    spec:
    containers:
    - name: pod-ml
    image: <Docker image uri>
    volumeMounts:
    - name: vol-ml
    mountPath: "/etc/aws"
    readOnly: true
    volumes:
    - name: vol-ml
    Secret:
    secretName: aws-secret
    ```

在前面的示例中，您将在 Pod 的 `/etc/aws` 文件夹中看到每个对应的 Secret 名称（例如 `SECRET_AWS_ACCESS_KEY`）的文件，该文件包含 Secret 的值。

我们现在知道什么是容器以及如何在 Kubernetes 集群上部署它们。我们还了解如何在 Kubernetes 上配置网络以允许 Pod 相互通信，以及如何使用不同的网络选项将 Kubernetes 容器暴露给集群外部的外部访问。

Kubernetes 可以作为运行 ML 工作负载的基础架构。例如，您可以将 `Jupyter` `notebook` 作为容器化应用程序在 Kubernetes 上运行，作为数据科学环境用于实验和模型构建。

如果您需要额外资源，也可以将模型训练作业作为 Kubernetes Job 运行，然后将模型作为容器化 Web 服务应用程序提供服务，或将训练好的模型作为 Kubernetes Job 运行批量推理。在以下动手实践中，您将学习如何使用 Kubernetes 作为运行 ML 工作负载的基础架构。

# 动手实践 – 在 AWS 上创建 Kubernetes 基础架构

在本节中，您将使用 Amazon EKS 创建 Kubernetes 环境，Amazon EKS 是 AWS 上的托管 Kubernetes 环境，它使设置 Kubernetes 集群更加容易。让我们先看看问题陈述。

## 问题陈述

作为 ML 解决方案架构师，您已被指派评估 Kubernetes 作为银行一个业务单元构建 ML 平台的潜在基础架构平台。您需要在 AWS 上构建一个沙箱环境，并证明您可以将 Jupyter notebook 作为容器化应用程序部署，供数据科学家使用。

## 实验说明

在本动手实践中，您将使用 Amazon EKS 创建 Kubernetes 环境，Amazon EKS 是 AWS 上的 Kubernetes 托管服务，它会自动创建和配置带有主节点和工作节点的 Kubernetes 集群。EKS 预配置并扩展控制平面，包括 API 服务器和后端持久层。它还运行开源 Kubernetes，并与所有基于 Kubernetes 的应用程序兼容。

