
4. 完成设置后，点击**保存 (SAVE)**。

一旦分配了 IAM 角色，我们现在可以在宿项目中创建共享 VPC（Shared VPC）网络：

- 1. 从 Google Cloud 控制台进入**共享 VPC (Shared VPC)** 页面。
- 2. 确保您是以**共享 VPC Admin (Shared VPC Admin)** 的身份登录。
- 3. 从项目选择器选择共享 VPC 宿项目。
- 4. 点击**设置共享 VPC (SET UP SHARED VPC)**。

![](img/f681dfc12450e3a4c257352b70dbceca_173_0.png)

图 7.10 – 设置共享 VPC

5. 我们将移动到下一页，在启用宿项目（Enable host project）下点击保存并继续（SAVE & CONTINUE)。我们将选择您的现有项目作为宿项目。完成后，我们将进入下一步来配置子网。

![](img/f681dfc12450e3a4c257352b70dbceca_174_0.png)

图 7.11 – 启用宿项目

6. 在“选择子网（Select subnets）”部分，有两种选择子网的。如果您想将宿项目的所有 VPC 网络与下方列出的服务项目和服务项目管理员（项目级权限）共享，可以点击“所有子网”。或者，如果您需要与服务项目和服务项目管理员共享某些 VPC 网络子集，可以选择“单个子网（Individual subsets，子网级权限）”。请先选择您想要共享的子网。请参考图 7.12 查看可用选项。

## 选择子网

选择您想要共享的子网。您可以共享项目中的所有子网（包括未来创建的子网），也可以单独选择。

### 共享模式

- 共享所有子网（项目级权限）
  项目中的所有子网都将被共享，包括未来创建的子网。
- 单个子网（子网级权限）
  您想要共享的单个子网。未来创建的子网将不会自动共享。

### 要共享的子网

| | 区域 | VPC 网络 | IP 地址范围 |
|---|---|---|---|
| default | us-east-1 | default | 10.140.0/20 |
| default | us-east-2 | default | 10.170.0/20 |
| default | us-northeast-1 | default | 10.146.0/20 |
| default | us-southeast-2 | default | 10.174.0/20 |
| default | us-east-3 | default | 10.178.0/20 |
| default | us-south-1 | default | 10.160.0/20 |
| default | us-south-2 | default | 10.190.0/20 |
| default | us-southeast-1 | default | 10.148.0/20 |
| default | us-southeast-2 | default | 10.184.0/20 |
| default | australia-southeast-1 | default | 10.152.0/20 |

将共享 0 个子网

![](img/f681dfc12450e3a4c257352b70dbceca_175_0.png)

- 7. 完成后，您可以点击继续（CONTINUE）进入下一步进行配置权限。
- 8. 在项目名称（Project names）中，列出已连接的服务项目。使用“连接服务项目（Attach service projects）”不会指定服务项目管理员；那是下一步。
- 9. 在“按角色划分用户（Users by role）”部分，您可以将服务项目管理员添加到角色中。这些用户将在共享子网上使用 `compute.networkUser`。只有服务项目管理员可以构建 VPC 子网资源。
- 10. 完成后，您可以点击保存（Save）按钮。

一旦创建了共享 VPC 网络，可以通过以下步骤连接项目：

- 1. 点击“已连接项目（Attached projects）”选项卡；然后在下方点击“连接项目（Attach projects）”按钮。
- 2. 当您点击“连接项目”时，将导航到一个新页面，可以在那里指定项目名称。在这里，勾选服务项目。

