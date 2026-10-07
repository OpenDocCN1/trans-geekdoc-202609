

# 身份感知代理 (Identity-Aware Proxy)

![](img/f681dfc12450e3a4c257352b70dbceca_217_0.png)

图 8.7 – IAP 如何与 App Engine 工作

让我们观察图 8.7 来理解 IAP 如何与 App Engine 工作。当应用程序或资源受 IAP 保护时，只有具有适当 IAP 权限（IAP 安全用户角色）的用户才能访问它。为了访问受保护的资源，IAP 会对请求的用户进行身份验证和授权检查。

IAP 拦截对资源的请求并检查该服务是否启用了 IAP。如果启用了此选项，请求头或 Cookie 中出现的任何 IAP 凭据将提交到 IAP 认证服务器。如果用户没有浏览器凭据，则会将用户重定向到存储了令牌的 OAuth 2.0 Google 账号登录流程，以供后续登录使用。

# 高级网络安全

对于 GKE 和 GCE，如果用户可以访问 VM 的应用程序服务端口，就可以绕过 IAP 认证。IAP 保护的应用程序无法防止执行在不同 VM 上的代码，因为防火墙限制无法阻止它。类似的情况适用于 Cloud Run，如果用户拥有自动签名的 URL，他们就可以绕过 IAP 认证。为了防止并非源自服务基础设施的流量，你必须实现防火墙规则和负载均衡器。其他替代方案（例如为 Cloud Run 和 App Engine 使用入口控制/ingress controls）可以用于签名标头。

接下来，我们将介绍 IAP 如何支持你本地应用程序的访问。设置中将引入一个新组件：IAP 连接器（IAP connector）。我们将了解这个连接器是什么，并查看 IAP 连接器的内部工作原理。从考试的角度来看，你不会被测试关于 IAP 连接器工作原理的知识，但了解它总是有好的。

![](img/f681dfc12450e3a4c257352b70dbceca_218_0.png)

图 8.8 - 本地 IAP 的工作原理

# 身份感知代理 (Identity-Aware Proxy)

我们将使用图 8.8 提供的插图来理解本地 IAP 的流程和关键组件。然后，我们将查看如何为通过 Google Cloud 到本地的混合连接器连接的应用程序提供安全访问。

工作流的初始部分与之前解释的 IAP 为 App Engine 工作的方式类似。对用户执行的身份验证和授权检查没有区别。请求随后被发送到 IAP 连接器，它通过 Interconnect 的点对点连接将请求转发到本地网络。

IAP 通过使用 IAP 连接器针对本地应用程序。你可以从 Google Cloud 控制台的 IAM 仪表板创建 IAP 连接器。IAP 连接器使用可配置的 Google Cloud Deployment manager 进行部署。该模板部署了运行主机和运行 IAP 连接器所需的资源。在你的 Google Cloud 项目中，该模板在 GKE 集群上部署了一个 Ambassador 代理。该代理负责将受 Cloud Identity 保护的流量路由到你的本地应用程序，直接应用 Google Cloud 身份和访问管理（Cloud IAM）策略。

你必须为 IAP 连接器定义映射（mappings）。每个路由名称（routing name）必须对应于由 ambassador 创建的 GCE 后端资源。映射参数（mapping parameter）必须定义带有源和目的地的路由。这是为了确保请求可以从源端路由到正确的目的地，目的地可能是本地网络上的应用程序。以下示例显示了映射的样式：

```
routing:
  - name: crm
    mapping:
      name: host
      source: www.crm-domain.com
      destination: crm-internal.domain.com
  - name: sub
      source: customer.hr-domain.com
      destination: customer.hr-internal.domain.com
  - name: billing
    mapping:
      name: host
      source: www.billing-domain.com
      destination: billing-internal.domain.com
```

在此示例中，我们将来自 www.crm-domain.com 的入站请求路由到 crm-internal.domain.com，并为主机和子域名都创建了映射。稍后，我们将查看为本地应用程序启用 IAP 的步骤。

# 高级网络安全

这里需要注意的一点是，IAP 默认与 Google 身份集成，并使用 Google Cloud Identity 和 Cloud IAM 等服务。然而，你也可以选择使用外部身份而不是 Google Cloud Identity Platform（这是 Google 的客户 IAM 解决方案）。Google Cloud Identity Platform 可以与 IAP 一起使用。Google Cloud Identity Platform 是一个完全不同的产品，不在考试范围内。

接下来，我们将查看如何将 TCP 转发用于 IAP。用例限于支持使用 HTTP 或 HTTPS 的应用程序。在编写此书时，尚不支持厚客户端（thick clients）。但你可以使用 TCP 转发来同时支持安全壳（SSH）和远程桌面协议（RDP）。这允许用户通过 TCP 转发连接到 GCE 上的任何 TCP 端口，IAP 打开一个监听端口并将所有流量发送到所选实例。IAP 使用 HTTPS 加密客户端流量。`gcloud compute ssh` 将 SSH 封装在 HTTPS 中并将其传递给远程实例。TCP 转发仅适用于使用 IAP 的 GCE，而不适用于本地。

# 为本地环境启用 IAP

你应该熟悉四种不同的配置：为本地应用启用 IAP、为 App Engine 启用 IAP、为 GKE 启用 IAP 以及为 GCE 启用 IAP。IAP 允许管理托管在 App Engine、GCE 或负载均衡上的访问。执行以下步骤为 App Engine 启用 IAP：

1. 打开控制台左侧菜单。
2. 点击安全性（Security）。
3. 选择身份感知代理（Identity-Aware Proxy）。你的资源列在身份感知代理页面上。如果尚未操作，请确保你已配置了 OAuth。
4. 完成后，返回身份感知代理页面。按照以下步骤配置意意屏幕：
   - 转到 OAuth 同意屏幕。
   - 在支持电子邮件下，选择你想显示的地址。该地址必须属于登录用户帐户或用户所属的组。
   - 输入你想显示的应用程序名称。
   - 添加任何可选详细信息。
   - 点击保存。
5. 返回身份感知代理页面并选择你想保护的应用程序。如果没有看到你的应用，请确保你已配置了 App Engine。对于 GCE 和 GKE，确保你已配置了带有后端的负载均衡器。我们在第 7 章虚拟私有云中涵盖了创建负载均衡器的方法。

> 注意 为你的所选应用启用 IAP 后，只有经过验证和授权的成员才能访问它。

6. 点击行左侧的复选框选择应用程序。
7. 打开该应用程序的 IAP 开关。
8. 为了确认让资源受 IAP 保护，点击窗口中的启用。

为了控制谁可以访问应用程序，需要授予访问权限。在接下来的步骤中，你将指定成员并为他们分配适当的角色以访问你的应用程序。

9. 点击信息面板中的添加成员按钮。这会打开添加成员面板。添加面板会临时隐藏此处共享的示例。
10. 在添加成员面板中，在新成员字段中输入用户和/或组。
11. 为每个新成员选择一个想要授予的 IAP 角色。这些角色如下：
    - IAP 策略管理员 (IAP Policy Admin)：授予对 Cloud IAP 权限的管理员权限
    - IAP 安全应用用户 (IAP-secured Web App User)：授予使用 Cloud IAP 的 HTTPS 资源的访问权限
12. 点击保存。

