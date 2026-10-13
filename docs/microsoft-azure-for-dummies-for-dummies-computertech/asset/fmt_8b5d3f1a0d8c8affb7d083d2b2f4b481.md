
# 配置网络安全组 (NSG)

## 创建 NSG

1.  使用 Azure 门户的全局搜索查找 **Network Security Groups** 边栏选项卡；然后单击工具栏上的 **Add**。

    ![Remember](images/remember.png) 不要选择 **Network Security Groups (Classic)** 选项。本书的重点是 ARM。

2.  填写 **Create Network Security Group** 边栏选项卡上的表单，然后单击 **Create**。

    使用以下属性：

    *   **Name:** `NSG1`
    *   **Subscription:** `[your subscription]`
    *   **Resource Group:** `Wiley`
    *   **Location:** `East US 2`（使用你的主区域；这些示例使用的是我的）

## 配置入站安全规则

3.  部署完成后，选择你的 NSG，并在 Settings 列表中浏览到 **Inbound Security Rules** 设置。

    请注意，入站和出站安全规则有单独的设置。**Default Rules** 按钮切换它们的状态。对于此练习，请保持两个设置都处于启用状态。

4.  单击 **Add**。

5.  填写 **Add Inbound Security Rule** 边栏选项卡上的表单，然后单击 **Create**。

    默认情况下，Azure 会将你置于 **Advanced** 视图中，这正是你想要的位置。（如果你愿意，单击 **Basic** 查看简化视图。）

    对 `NSG1` 使用以下配置属性：

    *   **Source:** `Service Tag`, `Internet`。
        源可以是 IP 地址或地址范围的逗号分隔列表、服务标记或应用程序安全组。目前，请理解此规则适用于源自公共 Internet 的入站流量。
    *   **Source Port Ranges:** `Any`（用星号表示）
    *   **Destination:** `VirtualNetwork`（服务标记来救场）
    *   **Destination Port Ranges:** `80`
    *   **Protocol:** `TCP`
    *   **Action:** `Allow`
    *   **Priority:** `100`
    *   **Name:** `HTTP-In-Allow`
    *   **Description:** （如果想要可添加）

## 配置出站安全规则

6.  为 `NSG1` 创建一个新的**出站**（我重复：出站）安全规则。

    此规则允许从 `web1` 子网流向你将放置在 `app1` 子网上的存储帐户的流量。

    使用以下属性：

    *   **Source:** `Virtual Network`
    *   **Source Port Ranges:** `Any`
    *   **Destination:** `Service tag`, `Storage`
    *   **Destination Port Ranges:** `Any`
    *   **Protocol:** `Any`
    *   **Action:** `Allow`
    *   **Priority:** `100`
    *   **Name:** `Storage-Out-Allow`
    *   **Description:** （如果想要可填写）

[Figure 4-4](#c04.xhtml#c04-fig-0004) 显示了我在 MSG1 Overview 页面上完成的 `NSG1` 配置。

![FIGURE 4-4: NSG1 configuration.](images/9781119612148-fg0404.png)

[FIGURE 4-4:](#c04.xhtml#rc04-fig-0004) NSG1 configuration.

## 添加服务标记和应用程序安全组

**Service tags**（服务标记）是聚合 IP 地址前缀池的标签，使编写准确的 NSG 规则变得更加容易。一些常见的服务标记包括：

*   **VirtualNetwork:** 所有虚拟网络地址空间，包括本地和对等互连的 VNet
*   **Internet:** 所有公共 IP 地址，包括 Azure 拥有的和公共的
*   **AzureLoadBalancer:** 你部署的 Azure 负载均衡器的虚拟 IP 地址
*   **AzureCloud:** Azure 公共 IP 地址空间
*   **Storage:** Azure 存储服务的 IP 地址范围

**Application security groups (ASGs)**（应用程序安全组）实际上是用户创建的服务标记。通过它们，你可以按管理员定义的方式对资源进行分组，以简化 NSG 规则分配。例如，你可能会创建一个名为 `web-servers` 的 ASG，应用于部署中的 Web 服务器 VM。

![Remember](images/remember.png) 遗憾的是，使用默认入站和出站规则是一个全有或全无的选择：你无法有选择地删除单个默认入站或出站规则。因此，你应该计划重新创建所需的规则，而不是使用默认规则。

![Technical stuff](images/technicalstuff.png) 有关 ASG 的更多信息，请阅读 Azure 文档文章“Security Groups”，网址为 [`https://docs.microsoft.com/en-us/azure/virtual-network/security-overview`](https://docs.microsoft.com/en-us/azure/virtual-network/security-overview)。

## 将 NSG 与相应子网关联

按照以下步骤将新的 NSG 与 `VNet1` 上的 `web1` 子网和 `VNet2` 上的 `web2` 子网链接：

1.  在 **NSG1 Configuration** 边栏选项卡上，选择 **Subnets**。
2.  在 **Subnets** 边栏选项卡上，单击 **Associate**。
3.  在 **Associate subnets** 边栏选项卡上，选择适当的虚拟网络和子网。

    你需要完成此过程两次：一次用于 `VNet1`/`web1`，一次用于 `VNet2`/`web2`。

# 理解服务终结点

**Service endpoints**（服务终结点）通过将某些 Azure 服务的连接限制在虚拟网络内来保护这些服务。你可能有一个包含敏感数据的存储帐户，该数据应仅由位于特定 VNet 上的 VM 访问。在这种情况下，在适当的虚拟网络上为该服务帐户创建服务终结点即可实现你的目标。

其他可以通过服务终结点绑定到 VNet 的 Azure 产品包括 SQL Database、Cosmos DB、Key Vault 和 App Service。

本节将引导你完成配置。要在 `Vnet1` 的 `app1` 子网上创建 `Microsoft.Storage` 服务终结点，请执行以下步骤：

1.  在 Azure 门户中，浏览到 `VNet1`，然后选择 **Service Endpoints** 设置。
2.  在工具栏上，单击 **Add**。
3.  在 **Add Service Endpoints** 边栏选项卡上，选择 `Microsoft.Storage` 作为服务，选择 `app1` 作为子网；然后单击 **Add** 完成配置。

    你的工作还没有完成：你需要将存储帐户与 `app1` 子网关联。你看，在 VNet 上定义服务终结点为将存储帐户集成到网络中打开了可能性。接下来你需要转到存储帐户以完成配置。

    在这种情况下，你可以忽略服务终结点策略，因为截至撰写本文时，它是一个公共预览功能，没有关联的服务级别协议 (SLA)。服务终结点策略允许你更精细地筛选发往 Azure 服务的 VNet 流量。

4.  打开 **Storage Explorer**，确保你可以连接到存储帐户。

    如果你在 [Chapter 3](#c03.xhtml) 中创建了存储帐户，可以使用该存储帐户。你应该能够访问文件的 blob 容器以及其中的 blob。

5.  回到 Azure 门户，浏览到 `VNet1` 资源，然后选择 **Service Endpoints** 设置。
6.  从 `Microsoft.Storage` 的上下文菜单（即行尾的省略号；我在 [**Figure 4-5**](#c04.xhtml#c04-fig-0005) 中向你展示了这一点），选择 **Configure Virtual Networks in a storage account**。

    ![FIGURE 4-5: In the Azure portal, most resources have a context menu from which you can select configuration options.](images/9781119612148-fg0405.png)

    [FIGURE 4-5:](#c04.xhtml#rc04-fig-0005) In the Azure portal, most resources have a context menu from which you can select configuration options.

7.  在 **Storage Accounts** 边栏选项卡上，选择你的存储帐户和 **Firewalls and Virtual Networks** 设置。
8.  在 **Allow Access From** 部分，选择 **Selected Networks**。
9.  在 **Virtual Networks** 部分，选择 **Add Existing Virtual Network**。
10. 浏览到 `VNet1` 虚拟网络和 `app1` 子网，然后单击 **Add**。
11. 单击 **Save** 完成配置。

     启用服务终结点后，存储帐户的 **Firewalls and Virtual Networks** 边栏选项卡包含一些其他选项：

     *   **Add Your Client IP Address:** 如果不选择此选项，你将无法从当前工作站访问存储帐户。
     *   **Allow Trusted Microsoft Services to Access This Storage Account:** 启用此选项以确保其他 Azure 服务（如 Key Vault、Azure AD 等）可以访问存储帐户，反之亦然。

12. 关闭并重新打开 **Storage Explorer**。
13. 测试与存储帐户的连接。

     你应该会看到 [Figure 4-6](#c04.xhtml#c04-fig-0006) 中显示的错误消息。
