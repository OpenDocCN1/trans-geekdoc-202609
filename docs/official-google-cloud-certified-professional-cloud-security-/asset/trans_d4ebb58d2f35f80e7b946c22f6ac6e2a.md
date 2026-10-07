

# 注意

要了解更多关于如何查看和验证证明的信息，请参阅以下 Google Cloud 文档：https://packt.link/2A5Er。

# HSM 中的加密操作流程

当你在 Cloud KMS 中执行加密操作时，你不需要知道你使用的是 HSM 保护的密钥还是软件密钥。当 Cloud KMS API 检测到操作涉及受 HSM 保护的密钥时，它会将请求转发到相同位置的 HSM：

- 1. GFE 将请求路由到相应位置的 Cloud KMS 服务器。Cloud KMS API 验证调用者的身份、调用者访问密钥并执行操作的权限，以及项目对加密操作的配额。
2. Cloud KMS API 从数据存储中检索封装的密钥（wrapped key），并使用 Cloud KMS 主密钥解密一层加密。该密钥仍然使用针对 Cloud KMS 位置的 Cloud HSM 封装密钥进行封装。
3. Cloud KMS API 检测到保护级别为 HSM，并将部分解封装的密钥以及加密操作的输入内容发送到 Cloud HSM。
4. Cloud HSM 直接与 HSM 接口。HSM 执行以下操作：
   I. 检查封装的密钥及其属性是否被修改过。
   II. 解封装密钥并将其加载到存储中。
   III. 执行加密操作并返回结果。
- 5. Cloud KMS API 将结果传回给调用者。

使用受 HSM 保护的密钥进行的加密操作完全在配置位置的 HSM 内部执行，只有结果对调用者可见。现在我们已经查看了 Cloud HSM，让我们继续了解 Cloud 外部密钥管理器 (EKM)。这是 Google 提供的云密钥管理的最新产品。

# Cloud EKM

Cloud EKM 是数据保护的最新产品之一。通过 Cloud EKM，你可以使用在 EKM 合作伙伴处管理的密钥。

Cloud EKM 提供了多项优势：

- 密钥溯源：你控制外部管理密钥的位置和分发。外部管理的密钥永远不会在 Google Cloud 中被缓存或存储。相反，Cloud EKM 会为每个请求直接与外部密钥管理合作伙伴进行通信。
- 访问控制：你管理对外部管理密钥的访问权限。在使用外部管理的密钥对 Google Cloud 中的数据加密或解密之前，你必须授予 Google Cloud 项目使用该密钥的权限。你可以随时撤销此访问。
- 集中式密钥管理：你可以从特定的位置和用户界面管理你的密钥和访问策略，无论它们保护的是云端数据还是本地场所的数据。

在所有情况下，密钥都存储在外部系统中，永远不会发送给 Google。以下支持 EKM 托管的合作伙伴：

- Fortanix
- Futurex
- Thales
- Virtu

Google Cloud 支持多种用于 Cloud EKM 进行 CMEK 加密的云服务服务。请参考 Google Cloud 文档以获取当前支持的服务。

# Cloud EKM 的架构

图 9.8 显示了 Cloud EKM 的架构。

![](img/f681dfc12450e3a4c257352b70dbceca_272_0.png)

图 9.8 – Cloud EKM 架构

EKM 的创建流程如下：

- 与合作伙伴建立账户。他们有自己的门户，你可以在那里管理密钥。
- 创建密钥或使用现有密钥。这具有唯一的 URI 或密钥路径。复制此路径以备在第 4 步中使用。
- 接下来，授予你的 Google Cloud 项目负载服务账户访问外部密钥管理合作伙伴系统中密钥的权限。
- 在你的 Google Cloud 项目中，使用外部管理密钥的 URI 或密钥路径创建一个 Cloud EKM 密钥。

虽然 Cloud EKM 看起来是一个很棒的选择，但你仍应该注意一些事项：

- Cloud EKM 可以与托管私有 HSM 使用，创建一个与 Cloud KMS 集成的单租户 HSM 解决方案。选择支持单租户 HSM 的 Cloud EKM 合作伙伴。
- 当你使用 Cloud EKM 密钥时，Google 无法控制合作伙伴系统中外部管理密钥的可用性。如果你在 Google Cloud 之外丢失了密钥，Google 无法恢复你的数据。
- 在选择 Cloud EKM 密钥的位置时，请查看有关外部密钥管理合作伙伴和区域的指南。
- 查看 Cloud EKM 服务级别协议 (SLA)。
- 通过互联网与外部服务通信可能会导致可靠性、可用性和延迟问题。对于对此类风险容忍度较低的应用，考虑使用 Cloud HSM 或 Cloud KMS 存储你的密钥材料。
- 你需要与外部密钥管理合作伙伴签订支持合同。Google Cloud 支持只能对 Google Cloud 服务中的问题提供支持，无法直接协助解决外部系统中的问题。你可能需要与双方的支持团队合作以排除互操作性问题。

# 限制

以下是在使用 Cloud EKM 时你应该注意的一些通用限制：

- 不支持自动轮换。
- 当你使用 API 或 Google Cloud CLI 创建 Cloud EKM 密钥时，它不能有初始密钥版本。这不适用于使用 Cloud 控制台创建的 Cloud EKM 密钥。
- 除了 Cloud KMS 操作配额外，Cloud EKM 操作受特定配额限制。

涉及对称加密密钥时，请注意这些限制：

- 对称加密密钥仅支持以下场景：
    * 支持的集成服务中的 CMEK
    * 直接使用 Cloud KMS 进行对称加密和解密
    * 使用 Cloud EKM 外部管理密钥加密的数据，在不使用 Cloud EKM 的情况下无法解密

涉及非对称加密密钥时，请注意这些限制：

- 非对称加密密钥仅支持以下场景：
    * 支持的集成服务中的 CMEK
    * 直接使用 Cloud KMS 进行对称加密和解密
    * 使用 Cloud EKM 外部管理密钥加密的数据，在不使用 Cloud EKM 的情况下无法加密

# Cloud KMS 最佳实践

现在你了解了各种 Cloud KMS 产品，让我们来看一些密钥管理的最佳实践。

密钥访问和权限管理通过将密钥组织到密钥环以及授予 IAM 权限来完成。在构建云环境时，请遵循以下指南：

- 创建一个独立的 Cloud KMS 项目，与负载项目分离。
- 在 Cloud KMS 项目中添加密钥环。根据需要创建密钥环以实施职责分离。
- 监控特权操作：删除密钥被视为特权操作。
- 在 Security Center 中查看 CMEK 相关发现。
- 根据数据敏感性使用适当强度的加密密钥。

以下列表提供了如何应用 IAM 角色以支持你的安全指南：

- 在托管密钥的项目、文件夹或组织上，避免使用项目级基础角色（如 owner、editor 和 viewer）。相反，请在组织级别指定组织管理员。
- 在项目级别授予其他 IAM 角色。如果你对职责分离有进一步担忧，请在密钥环或密钥级别授予 IAM 角色。
- 使用 Cloud KMS 预定义角色来实现最小权限原则和职责分离。例如：
  - 分离管理角色（roles/cloudkms.admin 和 roles/cloudkms.importer），并为密钥使用角色
  - 将 roles/cloudkms.admin 的使用限制在安全团队成员以及通过 Terraform 等工具创建密钥和对象的服务帐户
  - 对于非对称密钥，分别授予需要私钥权限的角色（roles/cloudkms.cryptoDecrypter 和 roles/cloudkms.signer）和不需要私钥权限的角色（roles/cloudkms.publicKeyViewer 和 roles/cloudkms.signerVerifier）

现在你已经熟悉了密钥管理的最佳实践，让我们来理解为你的 Cloud KMS 基础设施必须做的一些重要密钥管理决策。

# Cloud KMS 基础设施决策

当你为项目设置 Cloud KMS 时，你需要对密钥做出若干决策。下表提供了关于在创建密钥和密钥环时应考虑的因素的指南。

| 密钥属性 | 密钥属性指南 |
| :--- | :--- |
| 密钥位置 | 选择距离你要执行加密操作的数据地理上最近的位置。对于加密这些数据的 CMEK，使用相同的密钥环位置。更多信息，请参阅 Cloud KMS 文档中的选择最佳位置类型。 |

