

# 身份和访问管理

身份和访问管理是一个用于管理数字身份的框架。IAM 管理用户数据库，记录用户登录和注销时间，管理组或角色的创建，并允许分配和删除访问权限。许多不同的组织提供 IAM 框架，其中最著名的可能是亚马逊网络服务（AWS），它使用该框架来控制对其提供的基础设施即服务（IaaS）技术的访问。

IAM 通常使用 PIM 和 PAM 来实现这些目标。一个实现良好且全面的 IAM 框架可以跨操作系统工作，并处理多种不同类型的资源。

## 7.3.5. Unix 文件权限

从诞生之初，Unix 就被设计为多用户环境，因此对文件权限给予了高度重视。Unix 系统中的每个文件都有一个所有者和一个组。每个文件还具有针对所有者、组和所有用户的权限。权限使用八进制数字设置，其中每个位代表读取（位 0：1）、写入（位 1：2）或执行（位 2：4）权限。

![](images/permissions.svg)

例如，如果你想要读取和执行权限，则数字为 5（1 + 4）。读取和写入权限则为 3（1 + 2）。

权限使用 `chmod` 命令指定，第一个八进制数字是所有者的权限，第二个是组的权限，第三个是所有用户的权限。因此，要将文件更改为所有者具有读取、写入和执行权限，组具有读取权限，其他人没有权限，命令将是 `chmod 710 <filename>`，其中 `<filename>` 是你的文件名。

文件的所有者和组可以使用 `chown` 命令设置：`chown <owner>.<group> <filename>`。如果未指定 `<group>`，则仅更改所有者。

## 7.3.6. ACLs

访问控制列表（ACL）用于基于特征允许或拒绝访问。它们通常基于简单的特征，要么拒绝不在列表中的任何人访问，即 `allowlist`，要么拒绝在列表中的任何人访问，即 `denylist`。

ACL 通常用于网络，并通常基于 IP 地址进行过滤。你可以在大多数防火墙产品以及 Amazon Web Services (AWS) 虚拟私有云（VPC）中找到 ACL 的示例。

文件系统 ACL 将相同的概念应用于文件。Linux 使用文件系统 ACL 以比 [Unix 文件权限](#index.xhtml#_unix_file_permissions) 更细致的方式允许或拒绝访问。

## 7.3.7. SSH 密钥

安全外壳服务器（SSH）支持使用非对称加密密钥进行身份验证。大多数服务器支持 RSA、DSA 和 ECDSA 密钥，其中 RSA 最为常见。SSH 服务器维护一个授权密钥列表，通常位于 `~/.ssh/authorized_keys`，可用于连接到服务器。当客户端连接时，SSH 服务器会发出一个挑战，要求客户端使用其私钥对一段随机数据进行签名。如果私钥与 `authorized_keys` 文件中存储的公钥匹配，则用户将登录。

SSH 密钥的优势在于更易于使用，因为用户不需要记住并输入密码。因此，在通过 SSH 运行协议（例如 [git](https://git-scm.com/)）时，密钥常用于身份验证。密钥还具有可能挫败中间人（MitM）攻击的优势。虽然恶意行为者冒充 SSH 服务器可以轻易窃取密码，但通过密钥进行身份验证只会传输一段签名的随机数据。这段数据对中间人来说毫无用处。

## 7.3.8. 会话和 Cookie

HTTP 会话也可用于控制对资源的访问。这在 Web 应用程序中很常见。成功登录后，用户会获得一个带有加密防篡改会话 ID 的 Cookie。用户对该网站发出的每个请求都会包含该 Cookie。最终会话会超时，用户的请求会因会话 ID 不再有效而被拒绝。通常，网站会将用户从受保护的资源重定向到登录页面，以便他们可以重新登录。

网站 Cookie 也可用于存储用户偏好或应用程序的当前状态。Cookie 可以列出用户购物车中当前的商品，或指定用户是否偏好深色模式。Cookie 一直是审查的目标，因为它们可能被用于攻击。如果 Cookie 可以被外部应用程序或 Web 浏览器中的单独恶意标签页访问，则可以用于获取用户会话的访问权限。

## 7.3.9. 单点登录（SSO）

鉴于 Web 应用程序的普遍性，为用户维护单独的用户名和密码可能很困难。最近的趋势是支持单点登录，其中一个身份提供者用于确认用户就是他们声称的那个人。有一些协议使这成为可能，包括 SAML 和 OAuth。

SAML 代表安全断言标记语言，是一种基于 XML 的单点登录解决方案。SAML 工作流围绕 SAML 身份提供者或 IDP 展开。以下步骤用于通过 SAML 授予对资源的访问权限：

1. 用户访问一个服务

2. 用户被重定向到带有 SAML 请求的 SAML IDP

3. 用户登录

4. 凭据被验证

5. SAML IDP 将凭据发送到服务

OpenID 是另一种协议，允许用户以类似于 SAML 的方式使用第三方身份提供者进行身份验证。主要区别之一是 OpenID 设计为去中心化，允许用户从多个 IDP 中选择。2014 年 2 月，OpenID 引入了 OpenID Connect (OIDC)，这是一种更现代的系统，允许 IDP 通过 REST API 提供有关用户的信息。这一举动很大程度上是对 OAuth 流行程度的回应。

OAuth 是一种允许网站在用户许可下访问用户个人资料部分的方法。OAuth 并非 `技术上` 一个完整的身份验证协议，但它通常作为其中一部分使用。以下图表突出了 OpenID 身份验证和 OAuth 流之间的区别：

![OpenID vs. Pseudo-Authentication using OAuth by Perhelion used under CC0 1.0](images/oauth.svg)

[OpenID vs. Pseudo-Authentication using OAuth](https://commons.wikimedia.org/wiki/File:OpenIDvs.Pseudo-AuthenticationusingOAuth.svg) by [Perhelion](https://commons.wikimedia.org/wiki/File:OpenIDvs.Pseudo-AuthenticationusingOAuth.svg) used under [CC0 1.0](https://commons.wikimedia.org/wiki/File:OpenIDvs.Pseudo-AuthenticationusingOAuth.svg)

## 7.3.10. Kerberos

Kerberos 是一种用于客户端-服务器连接的身份验证协议。它由 MIT 在 1980 年代开发，主要部署在 Windows 网络上，但许多 Linux 发行版也支持使用它进行身份验证。Kerberos 大量使用基于时间的票据，因此所有参与的客户端必须时钟同步。当正常工作时，Kerberos 允许在不受信任的网络上进行完整的身份验证。

Kerberos 使用许多不同的服务和概念来履行其职责。其中一些服务可能运行在同一台机器上，并且几乎总是缩写：

身份验证服务器（AS）

: 与客户端执行身份验证步骤

票据授予服务（TGS）

: 创建和签署票据的服务

票据授予票据（TGT）

: 带时间戳并加密（使用 TGS 密钥）的票据，授予为服务创建票据和会话的能力

密钥分发中心（KDC）

: 运行 TGS 并授予 TGT

服务主体名称（SPN）

: 使用 Kerberos 身份验证的服务的名称

