

```json
"spec": {
  "user": "system:serviceaccount:kube-system:default",
  "namespace": "*",
  "resource": "*",
  "apiGroup": "*"
}
```

- **基于角色的访问控制 (RBAC):** 权限根据用户的角色授予。RBAC 利用了 `rbac.authorization.k8s.io` API 组。RBAC API 与四个 Kubernetes 对象协同工作：Role、ClusterRole、RoleBinding 和 ClusterRoleBinding。

Role 和 ClusterRole 包含一组权限。这些权限是累加的，这意味着没有“拒绝”权限，你需要显式地为资源添加权限。Role 对象是有命名空间的（namespaced），用于指定特定命名空间内的权限。ClusterRole 对象是非命名空间的，但可以用于授予特定命名空间或集群范围的权限。以下 yaml 文件提供了对核心 API 组中默认命名空间下所有 Pod 资源的 get、watch 和 list 权限：

```yaml
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

以下策略允许对集群中所有 Kubernetes 节点 get、watch 和 list 访问。

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: nodes-reader
rules:
```

RoleBinding 和 ClusterRole 通过引用 Role 或 ClusterRole 对象，将 Role 或 ClusterRole 对象中定义的权限授予一个用户或一组用户。以下策略将 joe 用户绑定到 pod-reader 角色：

```yaml
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

以下 RoleBinding 对象将服务账户 SA-name 绑定到 ClusterRole nodes-reader：

```yaml
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

Kubernetes 有用于存储和管理敏感信息（如密码）的内置功能。与其直接在 Pod 中以明文存储这些敏感信息，你可以将这些信息存储为 Kubernetes Secrets，并使用 Kubernetes RBAC 创建和或读取 secrets 的特定访问权限。默认情况下，secrets 以未加密的明文 Base64 编码字符串存储，可以对 secrets 静态加密。以下策略展示了如何为 AWS 访问凭据创建 secret。

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: aws-secret
type: Opaque
data:
  AWS_ACCESS_KEY_ID: XXXX
  AWS_SECRET_ACCESS_KEY: XXXX
```

- 作为 Pod 规范模板中的环境变量：

```yaml
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

容器内部的应用代码可以像访问环境变量一样访问 secrets。

- 作为挂载到 Pod 卷中的文件：

```yaml
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
    secret:
      secretName: aws-secret
```

在之前的示例中，你将在 /etc/aws 文件夹中看到每个对应 secret 名称（如 SECRET_AWS_ACCESS_KEY）的文件，其中包含了 secrets 的值。

## 在 Kubernetes 上运行 ML 负载

我们现在知道容器是什么以及它们如何部署在 Kubernetes 集群上。我们还知道如何配置 Kubernetes 网络以允许 Pod 之间通信，以及如何使用不同的网络选项在集群外部暴露 Kubernetes 容器以进行访问。

Kubernetes 可以作为运行 ML 负载的基础设施。例如，你可以在 Kubernetes 上运行容器化的 Jupyter Notebook，作为科学实验和模型构建的环境。

（此处后续为原文中的重复/碎片文本，已按要求完成核心内容翻译）

