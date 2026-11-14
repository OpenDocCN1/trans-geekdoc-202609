

# Kerberos

它是一种提供域身份验证服务的协议（而非 `AAA`）。它需要第三方进行身份验证（除 `Client` 和 `Server` 之外）。用户在 `Server`（即 `Key Distribution Center (KDC)`，密钥分发中心，也就是域控制器）上进行身份验证。该 `Server` 会颁发一张票据，用于访问托管在其他 `Servers` 上的服务。它只需要一次访问（`SSO`，`Single SignOn` 单点登录），用户认证一次即可获得所有访问权限。`KDC` 由两部分组成：执行身份验证的 `Authentication Server`（认证服务器）和颁发票据的 `TGS`（`Ticket Granting Server`，票据授予服务器）。`Kerberos` 允许您防范欺骗攻击（得益于双向认证）、嗅探攻击（加密通信）和重放攻击（有时效限制的票据）。`KDC` 的弱点是 `Single Point of Failure`（单点故障），即如果没有服务工作，它将不可用。`Kerberos` 使用 `UDP 88` 端口。

# Authorization（授权）

一旦确定了用户的身份，就有必要确定他可以获得什么访问权限。这就是授权阶段。共有三种方法：`Mandatory`（强制）、`Discretionary`（自主）和 `Role Based`（基于角色）。

## Mandatory Access Control (MAC)（强制访问控制）

`MAC`（`Mandatory Access Control`）涉及在数据录入系统时为所有数据打上安全级别标签（例如：绝密、机密、私密）。当用户尝试打开文档时，系统会决定该用户是否拥有足够的权限。只有少数管理员控制一切，负责授权用户和标记数据。

## Discretionary Access Control (DAC)（自主访问控制）

`Dictionary Access Control (DAC)` 要求每个资源都有一个所有者，由其自行决定分配访问权限。资源会被分配一个 `ACL`（`Access Control List`，访问控制列表），以确定谁可以读取和/或修改数据。典型的实现是在 `NTFS` 磁盘上的文件和文件夹权限。

## Role-Based Access Control (RBAC)（基于角色的访问控制）

`Role-Based` 规定创建角色。每个角色被分配完成工作所需的权限。当有新用户或用户变更工作时，只需将正确的角色应用到账户，他就会获得所有必要的访问权限。`RBAC` 也可以指 `Rule-Based`（基于规则）访问控制，这是一种用规则来管控访问的方法。因此，在 `MAC` 中提供访问权限的是安全管理员，在 `DAC` 中是文件所有者，而在 `RBAC` 中则是公司策略。

## Need to Know（知情需求）

`Need to Know` 是针对敏感数据的机密访问控制。任何对标记有 `Need to Know` 的文档的访问都必须被请求并证明合理性。请求会被评估，仅当申请人证明有知情需求时才会同意访问。

## NTFS Permissions（NTFS 权限）

使用 `NTFS` 格式化允许您设置各种类型的权限（配合 Windows）。权限包括：`read`（读取）、`read and execute`（读取和执行，等同于读取外加打开可执行文件的权限）、`write`（写入，创建文件和子文件夹）、`edit`（修改，等同于写入外加删除文件夹的可能性）、`full control`（完全控制）。

# Account Management（账户管理）

在账户管理实践中，我们遵循以下原则：

1. `Least Privilege`（最小权限）  
   在非必要情况下，不要创建管理员账户。
2. `Principle of Responsibility`（责任原则）  
   不要创建通用的组账户，而只创建个人账户。
3. `Acceptable Use Policies`（可接受使用策略）  
   定义用户不能做什么。
4. `Password Policy`（密码策略）  
   定义复杂度和密码更新要求。
5. `Lock Policy`（锁定策略）  
   锁定离职人员的账户，即使是暂时离职。
6. `Periodic Checks`（`user account review`，定期检查/用户账户审查）  
   定期审查账户和权限，移除不再需要的账户。

## Permission Assignment（权限分配）

权限可以通过以下方式分配：

1. `on an individual basis`（基于个人）  
   这是用户较少的公司或特殊权限的常规做法。
2. `for groups`（基于组）  
   这对于大型网络更实用。组可以基于公司地点或职位划分。一个用户也可以被放入多个组。

## Time of Day Restriction（时间限制）

许多系统允许设置时间限制的访问。这样账户登录只能在特定的日期和时间进行，从而在用户不在公司时，消除了恶意软件使用 `brute force`（暴力破解）技术攻击的可能性。这种限制称为 `Time of Day Restriction`。

## Password Policy Details（密码策略详情）

`password policy` 非常重要，它规定：

1. `Minimum password complexity`（最小密码复杂度）  
   最小长度（例如 8 个字符）、复杂度（大写、小写和特殊数字）、密码过期（例如每 30 天）、密码历史记录（避免将来重复使用相同密码）。
2. `Blocking the account after too many wrong attempts`（错误尝试过多后锁定账户）  
   防止 `brute force`（暴力破解）攻击。
3. `Educate users to protect their passwords`（教育用户保护密码）  
   不要把密码写在纸上，不要告诉任何人，为不同账户使用不同密码，学会识别虚假网站，并使用复杂的密码存储技术。
4. `Reject the most common passwords`（拒绝最常见的密码）  
   例如 `12345678`、`qwerty`、`welcome`。
5. `Make password recovery impossible`（使密码恢复变得不可能）  
   服务器保存 `password hash`（密码哈希）。您可以使用 `cognitive password`（认知密码）技术，通过回答几个问题来重置密码。

# Subnetting（子网划分）

## Network Segmentation（网络分段）

网络分段是一种非常重要的加固技术，它将网络划分为多个隔间，从而提高安全性。分段技术包括：`secure zone creation`（安全区域创建）、`subnetting`（子网划分）和 `VLAN`。

## Subnetting（子网划分）

`Subnetting` 允许您将大型网络划分为子网，以提高性能和安全性。您可以通过 `router`（路由器）上的 `ACLs` 过滤一个网络到另一个网络的流量，因此数据包流量会减少，因为主机变少了，而且如果子网中出现问题，损害将仅限于该子网。

## VLANs

`VLANs` 通过创建独立的组来分割局域网。`Virtual LANs`（虚拟局域网）不同于由 `routers` 管理的 `subnetting` 创建的子网，它们由 `switches`（交换机）管理，并允许分离连接到同一 `switches` 的主机，即使它们在物理上非常接近。`switches` 绝不允许来自一个 `VLAN` 的数据包进入另一个 `VLAN`，因此，两个不同 `VLAN` 中的两台主机只能通过 `router` 直接通信。您可以在不同的 `switches` 上设置相同的 `VLAN`，以便远距离的主机进行通信。

## Trunking and 802.1Q（中继与 802.1Q）

属于不同 `VLANs` 的数据包可以通过 `switches` 之间的连接（`trunks`，中继链路）传输。重要的是要注意，在 `trunks` 上，必须标识每个数据包所属的 `VLAN`，此信息被录入专门添加到 `Ethernet frame`（以太网帧）中的 `tag`（标签）字段。所用的协议是 `802.1Q`。

![](rsrcK0.jpg)

# Router Hardening（路由器加固）

`router` 的加固可以减少或消除系统的漏洞。要正确应用加固，您必须：

- **`ACL` (`Access Control List`)**  
  允许 `router` 按 `IP addresses`（IP 地址）和 `port numbers`（端口号）过滤数据包。
- **`Secure remote access`**  
  使用 `Secure Remote Management (SSH)` 协议。
- **`Set a timeout`**  
  关闭活动连接。
- **`Manage accounts`**  
  安全地管理账户，始终更改访问配置的默认密码，并仅创建配置所需的最少账户。

# Switch Security（交换机安全）

`switch`（交换机）不同于 `hub`（集线器），它仅将数据包转发给接收者，这得益于 `switch` 能够读取目标 `MAC address`。`switch` 的主要优势在于大大增加了窃听的难度。要保障 `switches` 安全，您必须做到：

- **`Network Access Control`**  
  通过 `802.1x` 进行的控制，它控制接入主机的 `MAC address`。
- **`Flood guard`**  
  用于避免 `ARP poisoning`（ARP 欺骗/投毒）。
- **`Disable all doors that are not used`**  
  未使用的端口很危险，因为它们可能成为未授权用户的入口。
- **`Perform port security`**  
  您必须小心，因为 `port security`（端口安全）可能通过欺骗 `MAC address` 来绕过。
- **`Physical security`**  
  所有与 `physical security`（物理安全）相关的内容，包括摄像头、入口警卫和其他工具，以确保只有授权人员才能进入大楼。

