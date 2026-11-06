
# 全局编录和 Active Directory 架构

## GC 服务器的部署

`GC` 服务器的部署需要在网络设计过程中尽早考虑。如果您没有确定需要和不需要 `GC` 服务器的位置并据此规划，可能会出现通信问题，用户也可能受到不利影响。一个经验法则是记住，如果某个位置的用户超过 50 人，则该位置需要一个 `DC`。将网络划分为站点会影响 `GC` 信息的复制流量处理方式。站点内的复制（`intrasite replication`）的处理方式与不同站点之间的复制（`intersite replication`）不同。在每个站点内部署 `GC` 服务器可能并非必要，但您应跟踪计算机使用的带宽。大量 `GC` 查询会占用大量带宽。

## 通用组和缓存

如果域功能级别至少为 `Windows 2000 Native`，则可以使用 `Universal Groups`。`GC` 是 `Universal Group` 信息存在的唯一位置。当用户登录时，会验证其 `Universal Group` 成员身份。进行身份验证的 `DC` 会向 `GC` 服务器发出此请求。如果 `GC` 服务器无法满足请求，则可能会拒绝登录。但是，使用 `Windows Server 2003` 时，可以缓存 `Universal Group` 成员身份以防止此问题。缓存必须在 `Active Directory Sites and Services` 控制台中的 `NTDS Site Settings Properties` 下启用，如本章前面所述。启用此设置后，进行身份验证的 `DC` 将查询最近的 `GC` 以获取 `Universal Group` 成员身份。接收到的信息将被缓存到进行身份验证的 `DC` 上，并默认每八小时刷新一次。启用缓存后，即使无法访问 `GC`，该进行身份验证的 `DC` 也能够处理登录，因为信息已被缓存。

## Active Directory 架构概述

架构定义了 Active Directory 的结构。可以在 Active Directory 中管理各种类型的对象。Active Directory 中的对象是类的实例，例如 `User` 或 `Printer`。类定义对象的类型。与每个 `Object` 类相关联的都是可以修改的属性。例如，属性可以是 `Location` 或 `First Name`。属性有两种不同的类型。最常见的是 `single-value attribute`，它包含一个数据项。您可能还会使用 `multivalue attributes`，它可以包含多于一个数据项。后者的一个例子是电话号码。`Other` 按钮允许您在某人拥有多个电话号码的情况下添加额外条目。

## 属性索引和对象引用

为了加快查询并使搜索更轻松，可以启用属性索引。此过程会为实例中的每个属性构建索引。应索引常用属性，但并非所有属性都应被索引。对 `multivalued attributes` 的索引应给予特别考虑。您可能会因为实例中所有 `multivalued attributes` 的复制而产生大量额外流量。当您使用 `Schema` 对象时，有不同的方式可以引用对象。描述对象的常见方式包括 `LDAP` 名称、`Common Names` 和 `OIDs`。`LDAP` 是一种行业标准协议，也是 Active Directory 的主要访问协议。`Common Name` 是识别对象的一种更简单的方式。`OID` 由第三方机构分配。关于 `OIDs` 必须遵循标准。我们建议您遵循为 `LDAP` 和 `Common Name` 制定命名的标准。

## 架构修改

您可以使用 `Schema MMC snap-in` 对 `GC` 和架构进行所有修改。要安装此管理单元，首先必须注册 `schmmgmt.dll` 文件；然后您可以创建自定义 `MMC` 并添加 `Schema snap-in`。`Schema snap-in` 用于在默认类和属性不能满足需求时扩展架构。在考虑扩展架构时，您需要确保在将其应用于生产网络之前已彻底测试更改。架构出现问题可能意味着网络出现严重故障。您必须以 `Schema Admins` 组成员身份登录才能对架构进行任何修改或扩展。此组的唯一默认成员是林根域的 `Administrator`。

## 架构停用

对架构所做的更改无法删除，但可以停用。`Windows Server 2003` 不允许删除 Active Directory 中的类或属性。停用的类或属性仍在架构数据库中，但不可用。

## 考试目标快速通道

### 使用全局编录和 GC 服务器

☑ `GC` 服务器保存 `Universal Membership` 数据。

☑ 在 `Windows Server 2003` 网络中，`Universal Membership` 信息可以缓存在非 `GC` 服务器上。

☑ `GC` 服务器协助在 Active Directory 中搜索对象。

☑ `GC` 处理 `UPN` 身份验证。

☑ 将网络划分为站点有助于通过 `WAN` 链路的复制流量。

### 使用 Active Directory 架构

☑ 架构由 `Object` 类组成，例如 `User`、`Printer` 和 `Server`。

☑ 每个 `Object` 类都有与其关联的一系列属性。

☑ 可以有 `multivalue attributes` 和 `single-value attributes`。

☑ 您必须是 `Schema Admins` 组的成员才能修改架构。

☑ `Schema` 对象遵循 `LDAP` 或 `Common Name` 标准。

☑ 类和属性不能被删除，但可以被停用。

## 考试目标常见问题

以下常见问题解答由本书作者提供，旨在检验您对本章中考试目标的理解，并帮助您在实际生活中实施这些概念。您还可以在 [`ITFAQnet.com`](http://www.ITFAQnet.com) 访问数千个其他常见问题解答。

Q: 我想在 `DC` 上启用 `GC` 功能。我在哪里可以做到？

A: 在“常规”选项卡上的 `NTDS Settings Properties` 窗口中。只需选中 `Global Catalog` 旁边的复选框，然后单击“确定”。

Q: 我有一个只有 10 个用户的办公室。我应该在此位置放置 `GC` 服务器吗？

A: 可能不需要；微软建议某个位置有 50 个或更多用户才需要在该办公室部署本地 `DC`。

Q: 我注意到公司总部和分支机构之间有大量流量。我最近在分支机构添加了 `GC` 服务器/域控制器。为什么会有这么多额外流量？

A: 很可能，您没有为每个位置设置站点。将 `GC` 服务器放置在站点中有助于控制复制并应减少带宽使用。在站点之间发送数据前会进行压缩，从而保持带宽使用量较低。

Q: 我尝试修改架构但无法进行任何更改。为什么？

A: 请确保您以 `Schema Admin` 组成员身份登录。只有 `Schema Admin` 成员可以修改架构。

Q: 类和属性有什么区别？

A: 类定义您正在处理的对象类型，例如 `User` 对象或 `Computer` 对象。对象与各种属性相关联，这些属性是数据字段，例如用户名、名字、位置等。

Q: 我想删除我添加的新属性，但找不到该选项。为什么？

A: 您无法删除类或属性。您可以停用类或属性，这将使类或属性不再可供使用，尽管它仍在架构中定义。如果以后想再次使用它，可以重新激活它。

Q: 如果您的 `GC` 服务器过载怎么办？

A: 添加另一个 `GC` 服务器以平衡流量。

Q: 如果您无法修改架构，并且已确认您是 `Schema Admin`，还有什么其他可能原因会导致架构扩展无法工作？

A: `Schema Operations Master` 可能无法访问

Q: 如果我有四个位置，由 56 K 或更低的 `WAN` 链路分隔，如果每个位置的用户超过 1000 人，我应该有多少个 `GC` 服务器？
