
# 性能

机密 VM 运行在带有 AMD EPYC 处理器的宿主机上

## IAM 授权

受保护的 VM 使用 Cloud IAM 进行授权。以下是受保护的 VM 使用 Compute Engine 权限：

- `compute.instances.updateShielded-ShieldedInstanceConfig`: 允许用户更改 VM 实例上的受保护 VM 选项
- `compute.instances.setShieldedInstanceIntegrityPolicy`: 允许用户更新 VM 实例上的完整性策略基准
- `compute.instances.getShieldedInstanceIdentity`: 允许用户从 vTPM 中检索信任背书信息

受保护的 VM 权限被授予以下 Compute Engine 角色：

- `roles/compute.instanceAdmin.1`
- `roles/compute.securityAdmin`

您可以向自定义角色授予受保护的 VM 权限。

# 受保护的 VM 的组织策略约束

您可以将 `constraints/compute.requireShieldedVm` 组织策略约束设置为 `True`，以要求组织内创建的 Compute Engine VM 实例必须是受保护的 VM 实例。

## 机密计算

机密计算涉及使用基于硬件的可信执行环境 `TEE` 在数据在使用时对其进行保护。`TEE` 是安全且隔离的环境，可以防止应用程序和数据在运行期间被访问或更改。一个名为“机密计算联盟”（Confidential Computing Consortium）的团体可能会使用以下端到端加密：

- 静态加密：在数据存储时保护您的数据
- 传输加密：当数据在两点之间移动时保护您的数据
- 使用中加密：在数据被处理时保护您的数据

机密计算为您提供了端到端加密的最后环节点：使用中加密。

## Google Cloud 机密计算的核心功能

当您使用机密 VM 时，您的数据和应用程序在使用期间将保持私密和加密状态。这是 Compute Engine VM 的一种类型。它运行在带有 AMD EPYC 处理器的宿主机上，这些处理器支持 AMD 安全加密虚拟化 `SEV`。机密 VM 运行在这些主机上。在机密 VM 中添加 `SEV` 具有以下功能和优势：

- 隔离：加密密钥在 VM 创建时由 AMD 安全处理器 `SP` 生成，且它们仅存在于 AMD 系统级芯片 `SOC` 上。Google 无法查寻到这些密钥，使得它们更具私密性。
- 证明：机密 VM 使用 `vTPM`。每当基于 `SEV` 的机密 VM 启动时，都会进行证明。
