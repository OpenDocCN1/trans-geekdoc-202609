
![wrong](images/wrong.png) 答案 C 不正确，因为设置用户无法修改网络连接的 GPO 已应用于 Training OU。由于 Training OU 也是 Corp 的子 OU，其设置不会应用于 Sales OU。答案 D 不正确；Sales OU 中的用户将同时具有 Corp OU 和 Sales OU 的设置。

## 13.
你被要求确保网络安全策略已到位，并且用户配置的标准已实施。网络是一个单一的 Active Directory 域网络。有五个 OU：Corp、Sales、Marketing、Development 和 Technical。Corp OU 是所有其他 OU 的父 OU。你被给出以下需要满足的目标列表：
■ 所有用户必须禁止编辑其注册表。
■ 所有用户必须拥有至少八个字符的密码。
■ Sales 和 Marketing OU 中的用户不得在任何服务器上存储超过 50 MB 的数据。
■ Development OU 中的用户必须每 30 天更改一次密码。
■ 所有策略设置应仅影响其预期目标。
以下哪个解决方案能完成你的所有目标？
A. 创建一个名为 Policy 的 GPO，设置禁止用户使用 Regedit，并要求密码至少为八个字符。将 Policy 链接到 Corp OU。创建一个名为 Data 的 GPO，将磁盘配额设置为 50 MB。将 Data 链接到 Sales OU 和 Marketing OU。创建一个名为 Password 的 GPO，使用户每 30 天更改一次密码。将 Password 链接到 Development OU。
B. 创建一个名为 Policy 的 GPO，设置禁止用户使用 Regedit，并要求密码至少为八个字符。将 Policy 链接到域。创建一个名为 Data 的 GPO，将磁盘配额设置为 50 MB。将 Data 链接到 Corp OU。创建一个名为 Password 的 GPO，使用户每 30 天更改一次密码。将 Password 链接到 Development OU。
C. 创建一个名为 Policy 的 GPO，设置禁止用户使用 Regedit，并要求密码至少为八个字符。将 Policy 链接到 Corp OU。创建一个名为 Data 的 GPO，将磁盘配额设置为 50 MB。将 Data 链接到 Corp OU。创建一个名为 Password 的 GPO，使用户每 30 天更改一次密码。将 Password 链接到 Corp OU。
D. 创建一个名为 Policy 的 GPO。在 Policy 中，定义禁止用户使用 Regedit、要求密码至少为八个字符、将磁盘配额设置为 50 MB 以及最大密码使用期限为 30 天的设置。将 Policy 链接到 Corp OU。
☑ A. 唯一满足所有要求的答案是答案 A。虽然此解决方案实施起来较长，但它是唯一一个将所有期望的策略应用于其预期目标而不影响其他计算机或 OU 的方案。
![wrong](images/wrong.png) 答案 B 不正确，因为磁盘配额设置已应用于 Corp OU。然后该设置将应用于所有用户，而不仅仅是 Sales 和 Marketing 中的用户。答案 C 不正确，因为它将磁盘配额应用于所有用户，而不仅仅是 Sales 和 Marketing 中的用户，并且它也将更改密码应用于所有用户。答案 D 不正确，因为它使所有策略都应用于所有用户。策略设置仅影响其预期目标的需求未得到满足。

## 14.
你的 Active Directory 域有两个 OU。Corp OU 是 Technical OU 的父 OU。你已在 Corp OU 上链接了一个 GPO。你不希望这些设置影响 Technical OU 中的用户。如何在最小努力的情况下实现这一点？
A. 在链接到 Technical OU 的 GPO 上，选择阻止策略继承。
B. 在链接到 Corp OU 的 GPO 上，选择阻止策略继承。
C. 在链接到 Technical OU 的 GPO 上，通过为这些选项选择已禁用来否定 Corp OU 中设置的任何选项。
D. 在链接到 Technical OU 的 GPO 上，选择无覆盖。
☑ A. 通过在 Technical OU 上阻止策略继承，你有效地声明该 OU 中的所有对象应从“干净的 slate”开始，并且不受任何更高级别策略的影响。你可以通过为所有选项选择已禁用来否定 Corp OU 的 GPO 中的所有设置，但这在最好情况下也是繁琐的。无覆盖选项是为管理员提供的，以防止其他管理员或用户在较低级别有效地使用阻止策略继承选项。
![wrong](images/wrong.png) 答案 B 不正确，因为如果将阻止继承应用于父 OU，则不会产生预期效果。它需要在子 OU 上设置以阻止父级中制定的策略设置。答案 C 不正确，因为这需要持续关注并且不符合最小努力的要求。答案 D 不正确，因为在 Technical OU 上设置无覆盖将确保其设置不会被其子 OU 中的任何设置覆盖。它不会影响来自其父 OU 的设置。

## 15.
John Smith 是你公司的初级网络管理员。他的用户账户是 JSmith。你希望他负责将所有网络组策略链接到适当的 OU。由于他的经验水平，你不希望他对 OU 有额外的控制。最简单的方法是什么？
A. 使用委派控制向导。选择 JSmith，并勾选创建、删除和管理组。
B. 使用委派控制向导。选择 JSmith，并勾选管理组策略链接。
C. 使用委派控制向导。选择 JSmith，并勾选创建和修改组策略。
D. 使用委派控制向导。选择 JSmith，并勾选应用组策略。
☑ B. 使用委派控制向导，你可以允许用户管理组策略链接。请注意，通过委派此任务，相关管理员可以管理链接，但不一定有权修改 GPO 本身。
![wrong](images/wrong.png) 答案 A、C 和 D 不正确，因为你只希望他具有管理组策略链接的能力。其他选项会赋予他比此情况下所需更多的权限。

## Chapter 6 Working with Active Directory Sites
## 第 6 章 使用 Active Directory 站点

### Understanding the Role of Sites
### 理解站点的角色

### 1.
### 1.
一个 Active Directory 环境已配置了多个站点，并且每个站点都有适当的资源。Active Directory 环境的管理员尝试为两个站点之间复制信息的传输选择一个协议。两个站点之间的连接具有以下特征：
■ 由于网络提供商不可靠，链接在一天中的某些时间不可用。
■ 复制传输必须在链接可用或不可用的情况下进行。
■ 复制流量必须能够通过标准 Internet 连接传输。
以下哪个协议满足这些要求？
A. Internet 协议 (IP)
B. 简单邮件传输协议 (SMTP)
C. 远程过程调用 (RPC)
D. 动态主机配置协议 (DHCP)
☑ B. SMTP 适用于没有持久连接的环境。它使用存储转发方法以确保如果无法建立连接，数据不会丢失。
![wrong](images/wrong.png) 答案 A 不正确，因为 IP 需要持久连接来传输数据。答案 C 不正确，因为 RPC 用于在需要持久连接的远程站点之间传输 DC 之间的信息。答案 D 不正确，因为 DHCP 用于分配 IP 地址和分发 TCP/IP 配置信息；它不用于复制。
