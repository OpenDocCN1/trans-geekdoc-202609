

你可以选择创建组以使此策略不适用于这些组。强制执行时，此策略适用于 Google Cloud 控制台访问、`gcloud` 命令行工具（Google Cloud SDK）以及任何属于你或第三方、且需要 Google Cloud 范围（https://pack.link/Q1sR2）用户授权的应用程序。请注意，Google Cloud 会话长度控制不适用于 Google Cloud 移动应用。我们将查看如何从管理控制台强制执行会话长度：

- 1. 通过 admin.google.com 登录。
- 2. 导航至 安全性 (Security) | 访问和数据控制 (Access and Data Control) | Google Cloud 会话控制 (Google Cloud session control)。

参考以下截图供你配置的多个选项。

![](img/f681dfc12450e3a4c257352b70dbceca_97_0.png)

图 5.5 – Google Cloud 会话控制

- 3. 从左侧菜单中选择想要应用此策略的组织单元和组。如前所述，你可以将此策略选择性地应用于特定组中的用户，而不是所有用户进行会话控制，为标准用户和特权用户设置不同的会话控制设置。

## 让我们来看看我们可以配置的其他可用选项：

- **重新身份验证策略 (Reauthentication policy)：** 在此处，你选择需要重新身份验证 (Require reauthentication)，然后指定重新身份验证频率 (Reauthentication frequency)。最小频率为一小时，最大为 24 小时。有一个选项可以使受信任应用程序不受重新身份验证策略。你可以通过导航至 安全性 | 访问和数据控制 | API 选项 (API options) 来配置哪些应用程序是受信任的。从那里，你可以管理第三方应用程序。

| API 控制 | 访问控制 |
|---|---|
| 使用这些控制来启用或限制对第三方应用程序和服务帐户的访问。通过限制对受信任项目的访问，减少滥用 Workspace API 的风险。 | 管理对你的 Google 服务的访问。确保用户只能访问你组织信任的应用程序。了解更多<br>0 个受限的 Google 服务<br>15 个不受信任的 Google 服务<br>管理 Google 服务<br>管理第三方应用访问 |

![](img/f681dfc12450e3a4c257352b70dbceca_98_0.png)

- 接下来，你可以配置重新身份验证方法 (Reauthentication method)。在这里你可以指定密码或安全密钥。这取决于你的用场景。强烈建议对特权用户强制执行安全密钥。

> 注意
> 你可以在此处阅读更多关于 Google Cloud 会话长度的信息：https://packt.link/B2wvT。

## 基于 SAML 的 SSO

通过 SSO，你可以配置企业级应用程序，让用户使用由 Google 管理的凭据登录；在其他情况下，Google Workspace 将充当身份提供者。你有两种不同的选项来配置 SSO：预集成 (pre-integrated) 或自定义 (custom)。使用预集成选项时，Google 支持超过 300 种预配置的应用程序，你可以从 Cloud Identity 控制台部署它们。如果你有自定义应用程序或未预配置的应用程序，则可以使用自定义的安全断言标记语言 (SAML) 选项。

假设你理解 SAML 2.0 的工作原理。在本节中，我们仅查看如何使用 SAML 配置 SSO，而不涵盖 Google 如何实现 SAML 的基础知识。如果你想了解更多关于在 Google Cloud 上使用 SAML 进行 SSO 的信息，请参考章节末尾的*延伸阅读* (Further reading)。

为了考试目的，我们将介绍为自定义应用程序使用 SAML 配置 SSO 所需步骤。

在开始之前，请确保你已拥有**断言get服务 (ACS)** URL 和实体 ID (entity ID)，因为当你在配置外部 IdP 并可选地启动 URL 时将需要它们。此外，在此阶段还需确定你的外部 IdP 是否支持**多因素身份验证 (MFA)**；如果支持，你可以配置通过外部 IdP 使用 MFA 的选项，但如果由于某些原因你的自定义应用程序不支持 MFA，你可以配置 Google Identity 来强制执行 MFA。

现在让我们来看使用 SAML 为自定义应用程序完成设置所需的步骤：

- 1. 开始登录 `admin.google.com` 上的管理控制台。
- 2. 从主控制台导航至**应用 (Apps) | 网页和移动应用 (Web and mobile apps)**。
- 3. 从那里，选择**添加应用 (Add app) | 添加自定义 SAML 应用 (Add custom SAML app)**。

![](img/f681dfc12450e3a4c257352b70dbceca_99_0.png)

## 4. 这将带你进入四步向导来配置你的自定义 SAML 应用。

![](img/f681dfc12450e3a4c257352b70dbceca_100_0.png)

图 5.8 – 配置你的自定义 SAML 应用

- 5. 按照步骤为你的自定义应用程序命名，并可选地提供简短描述并上传图标。完成后，点击**继续 (Continue)**。
- 6. 下一步将为你提供两个选项：下载 IdP 元数据或复制并粘贴 SSO URL 以及带有 SHA-256 指纹的证书。这些是你的服务提供者所需的 Google 身份提供者详细信息。一旦你决定下载或复制粘贴这些信息，就可以点击**继续 (CONTINUE)** 按钮进入下一步。
- 7. 理想情况下，你现在可以登录你的服务提供者控制台，并复制粘贴第 6 步中获取的信息。
- 8. 在这一步中，你可以填写 ACS URL、实体 ID，以及可选的启动 URL。ACS URL 是你服务提供者的端点；实体 ID 值由服务提供者提供。在此阶段，你可以设置签名断言。Name ID 值是你的主邮箱；然而，你可以执行**添加 SAML 应用** 流程。
- 9. 下一步是可选的，创建属性映射。如果没有映射，你可以点击完成 (FINISH) 来完成设置。

![](img/f681dfc12450e3a4c257352b70dbceca_101_0.png)

图 5.9 – SAML 服务提供者详情

## 安全你的账户

![](img/f681dfc12450e3a4c257352b70dbceca_101_1.png)

图 5.10 – 应用详情页

你可以在应用 | 网页和移动应用页面上查看已配置的应用，并通过点击应用名称查看详情，如图 5.8 所示。
