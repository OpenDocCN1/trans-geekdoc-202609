

 理解活动目录中的

（其中的点）。当主和备用 DNS 后缀均失败时，DNS 客户端将对 GlobalName 区域进行查询。

鉴于之前的讨论，配置这些步骤并不困难：

- 1. 创建一个名为 GlobalNames 的区域。
  建议使用 Active Directory 集成区域，以便向其他域控制器提供复制复制功能。
- 2. 使用 `Set-DNSServerGlobalNameZone` 命令启用 GlobalNames 支持：
  C:\Users\Administrator.DC1>Set-DNSServerGlobalNameZone -Enable $True
- 3. 将区域复制到其他域控制器。
  切记将这些域控制器添加到特定的主机上。
- 4. 在区域中添加 CNAME 记录以重定向到特定主机。
  在我们的示例中，我们将其重定向到 hostrecord.PrimaryZone.local，如图 6.29 所示。

![](img/41a83208e6906a3732620203b836cea7_278_0.png)

- 5. 如果你需要其他 Active Directory 森林查询全局名称，请添加服务位置记录：

你可以使用 `nslookup` 实用程序来测试全局名称的解析：

```
C:\Users\Administrator.DC1>nslookup
Default Server: DC01.bigfirm.com
Address: 192.168.0.1
```

```
> WWW
Server: DC01.bigfirm.com
Address: 192.168.0.1

Name: hostrecord.primaryzone.local
Address: 192.168.0.21
Aliases: bigfirm.com
```

在大多数依赖 Windows 服务器的环境中，对单名称（NetBIOS）的需求已经如我们之前讨论的那样通过变通方法解决。通过正确部署使用 FQDN 的应用程序并利用 DNS，这种需求也降到了最低。

## 后台区域加载

某些旧环境的 DNS 区域非常大，导致域控制器需要一个多小时才能重启 DNS 服务。如果你遇到了这个问题，那么后台区域加载将是你的幸幸！我们预计 DNS 区域必须拥有海量记录才会导致此问题。

在 DNS 服务启动期间，它将开始对已加载的区域做出响应。对尚未加载区域的请求可能会被引用到其他服务器。

## DNSSEC

像 HTTP 一样，DNS 是未加密且未经认证的协议。正如我们在上面提到反向区域时说的，黑客可以伪造 DNS 响应。为了应对这一点，开发了 DNS 安全扩展（DNSSEC），它允许 DNS 服务器对资源记录进行数字签名。Windows Server 2012 R2 提供了作为 DNSSEC 区域辅助区域的支持。它仅允许来自数字签名区域的记录查询。它还将提供验证签名所需的资源记录。

这些记录是 KEY、SIG 和 NXT 记录。KEY 是签名 DNS 服务器的公钥。SIG 是资源记录的数字签名。NXT 基本上列出了命名空间中所有的有效记录。

通过 Windows Server 2012 R2，DNSSEC 相比其前代版本具有以下增强：

- Active Directory 集成以及对 DNS 动态更新的支持
- 更新的 DNSSEC 标准支持（NSEC3 和 RSA/SHA-2）
- 通过使用更新的 DNSSEC 进行记录验证
- 对 DNSSEC 额外的 PowerShell 支持

如果你想在实验室中运行 DNSSEC，请查看微软提供的此分步指南：

```
http://tinyurl.com/dnsseclab
```

## 信任锚点

信任锚点是 DNSSEC 服务器的公共证书，DNS 服务器将信任这些证书用于通信。信任锚点证书将用于验证响应的数字签名。它们以公钥的形式添加到 DNS 服务器的属性。Windows Server 2012 R2 包含了针对信任锚点的以下新增强功能：

- 使用 Active Directory 进行信任锚点发布
- 自动轮转支持
- 简化信任锚点的提取

## 支持基于互联网的 DNS 解析

信任锚点显示在 Windows Server 2012 R2 的 DNS 管理台中，位于“Trust Points”（信任点）文件夹中，你可以从左侧的树视图看到它。

## 支持基于互联网的 DNS 解析

在组织内部，也有管理互联网命名空间的需求。局域网内的用户需要访问网站和其他基于互联网的服务。外部用户至少需要访问组织的网站和邮件服务器。因此，你必须留意这些需求。

为了让用户能够访问你的网站，需要部署一个外部 DNS。因此，你需要考虑是否有必要部署外部 DNS 服务器。内部计算机将通过内部 DNS 服务器解析外部名称。因此，需要与互联网 DNS 结构集成。

## 支持外部 DNS 域

大多数公司注册 DNS 命名空间以支持网站和电子邮件。小型及某些中期公司允许 ISP 在其外部 DNS 服务器上管理命名空间。这样做的好处是服务器可用性，并且减少了在面向公共互联网的子网上维护额外服务器的麻烦。这些服务器通过接口管理，仅允许 host、cname 和 MX 等少数类型的记录。

使用 Windows Server 2012 R2 进行外部 DNS 操作是可能的。DNS 角色可以安装在不是域成员的服务器上（如之前在“配置独立 DNS 服务器”中讨论的那样）。

- Windows Server 2012 R2 是免费的，但将其作为外部 DNS 解决方案并不是最经济的方法。

## 分 Split DNS (Split BRAIN)

在大多数依赖 Windows 服务器的环境中，对单名称（NetBIOS）的需求已经如我们之前讨论的通过变通方法解决。通过正确部署使用 FQDN 的应用程序并利用 DNS，这种需求也降到了最低。

## 后台区域加载

某些旧环境的 DNS 区域非常大，导致域控制器需要一个多小时才能重启 DNS 服务。如果你遇到了这个问题，那么后台区域加载将是你的幸运！我们预计 DNS 区域必须拥有海量记录才会导致此问题。

在 DNS 服务启动期间，它将开始对已加载的区域做出响应。对尚未加载区域的请求可能会被引用到其他服务器。

## DNSSEC

像 HTTP 一样，DNS 是未加密且未经认证的协议。正如我们在上面提到反向区域时说的，黑客可以伪造 DNS 响应。为了应对这一点，开发了 DNS 安全扩展（DNSSEC），它允许 DNS 服务器对资源记录进行数字签名。Windows Server 2012 R2 提供了作为 DNSSEC 区域辅助区域的支持。它仅允许来自数字签名区域的记录查询。它还将提供验证签名所需的资源记录。

这些记录是 KEY、SIG 和 NXT 记录。KEY 是签名 DNS 服务器的公钥。SIG 是资源记录的数字签名。NXT 基本上列出了命名空间中所有的有效记录。

通过 Windows Server 2012 R2，DNSSEC 相比其前代版本具有以下增强：

- Active Directory 集成以及对 DNS 动态更新的支持
- 更新的 DNSSEC 标准支持（NSEC3 和 RSA/SHA-2）
- 通过使用更新的 DNSSEC 进行记录验证
- 对 DNSSEC 额外的 PowerShell 支持

如果你想在实验室中运行 DNSSEC，请查看微软提供的此分步指南：

```
http://tinyurl.com/dnsseclab
```

## 信任锚点

信任锚点是 DNSSEC 服务器的公共证书，DNS 服务器将信任这些证书用于通信。信任锚点证书将用于验证响应的数字签名。它们以公钥的形式添加到 DNS 服务器的属性。Windows Server 2012 R2 包含了针对信任锚点的以下新增强功能：

- 使用 Active Directory 进行信任锚点发布
- 自动轮转支持
- 简化信任锚点的提取

## 支持基于互联网的 DNS 解析

信任锚点显示在 Windows Server 2012 R2 的 DNS 管理台中，位于“Trust Points”（信任点）文件夹中，你可以从左侧的树视图看到它。

## 支持基于互联网的 DNS 解析

在组织内部，也有管理互联网命名空间的需求。局域网内的用户需要访问网站和其他基于互联网的服务。外部用户至少需要访问组织的网站和邮件服务器。因此，你必须留意这些需求。

为了让用户能够访问你的网站，需要部署一个外部 DNS。因此，你需要考虑是否有必要部署外部 DNS 服务器。内部计算机将通过内部 DNS 服务器解析外部名称。因此，需要与互联网 DNS 结构集成。

## 支持外部 DNS 域

大多数公司注册 DNS 命名空间以支持网站和电子邮件。小型及某些中期公司允许 ISP 在其外部 DNS 服务器上管理命名空间。这样做的好处是服务器可用性，并且减少了在面向公共互联网的子网上维护额外服务器的麻烦。这些服务器通过接口管理，仅允许 host、cname 和 MX 等少数类型的记录。

使用 Windows Server 2012 R2 进行外部 DNS 操作是可能的。DNS 角色可以安装在不是域成员的服务器上（如之前在“配置独立 DNS 服务器”中讨论的那样）。

- Windows Server 2012 R2 是免费的，但将其作为外部 DNS 解决方案并不是最经济的方法。

## 分 Split DNS (Split BRAIN)

在大多数依赖 Windows 服务器的环境中，对单名称（NetBIOS）的需求已经如我们之前讨论的通过变通方法解决。通过正确部署使用 FQDN 的应用程序并利用 DNS，这种需求也降到了最低。

## 使用 Split DNS (Split BRAIN) 的注意事项

（此处省略）

