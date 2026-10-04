

# 68 T. P. Fowdar, L. Babooram, M. U-D-Ibn Nazir Rosun 和 M. Indoondonman

![](img/2b52fde0e707e8c2f05a10309c3f8982_79_0.png)

图 2.60. 将项目目录与 Firebase 项目关联。

7. 然后，我们指定包含项目文件的文件夹（在本例中为 'public'），并在出现图 2.61 所示的下一个提示时按回车。

![](img/2b52fde0e707e8c2f05a10309c3f8982_79_1.png)

图 2.61. Firebase hosting 设置。

8. 针对图 2.62 显示的后续三个点，我们输入 N(no)，因为我们不想将其配置为单页应用，也不想在 Github 上设置部署。此外，我们不希望 html 文件被 firebase 生成的另一个 index.html 文件覆盖。

```
Configure as a single-page app (rewrite all urls to /index.html)? No
Set up atomic builds and deploys with GitHub? No
Wrote public/4.html
File public/index.html already exists. Overwrite? No
Skipping write of public/index.html
Writing configuration to firebase.json
Writing project information to .firebaserc
Writing gitignore file to .gitignore
Firebase initialization complete!
C:\Users\user1>
```

图 2.62. 完成 Firebase 初始化。

9. 最后，通过输入 `firebase deploy` 部署应用，如图 2.63 所示。

部署完成后，firebase 提供了两个 URL，即 'Project Console' 和 'Hosting URL'如图 2.63 底部所示。

# 云计算基础

```
E:\users\userid\test1>firebase deploy
== Deploying to "fir-experiments-55b7a"
 > hosting
 hosting:fir-experiments-55b7a: beginning deployment...
 hosting:fir-experiments-55b7a: Uploaded 2 files fully
 hosting:fir-experiments-55b7a: file upload complete
 hosting:fir-experiments-55b7a: finalizing version...
 hosting:fir-experiments-55b7a: deploy finished
 hosting:fir-experiments-55b7a: releasing new version...
 hosting:fir-experiments-55b7a: release complete

Deploy Complete!
```

Project Console: https://console.google.com/project/fir-experiments-55b7a/overview
Host URL: https://fir-experiments-55b7a.web.app
C:\Users\userid\test1>
```

图 2.63. 在 Firebase 中部署应用。

- 10. 在 Firebase 仪表板上选择 hosting，并注意到现在已可用图 2.64 所示的 web 应用链接。

![](img/2b52fde0e707e8c2f05a10309c3f8982_80_0.png)

图 2.64. 在 Firebase 上定位托管的应用。

- 11. 点击 web 应用链接时，应用程序的网页将在 Firebase 托管的公共域名上加载，如图 2.65 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_80_1.png)

图 2.65. 部署在 Firebase  Web 应用。

70 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun 和 M. Indoondom

- 12. 我们可以输入另一条记录来测试数据是否存储在学生记录中，如图 2.65 所示；当我们检查图 2.66 所示的实时数据库时，发现多了一了一条记录。

![](img/2b52fde0e707e8c2f05a10309c3f8982_81_0.png)

图 2.66. Firebase 中的额外记录。

最后的观察结果是 public 文件夹 test1 和 public 中创建了额外的文件，如图 2.67 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_81_1.png)

图 2.67. 托管应用后 public 和 test1 文件夹的内容。

# 2.7. IBM CLOUD 平台简介

IBM Cloud 是一个基于 Cloud Foundry 开源技术的公共云平台，其目录由多个产品组成的完整栈组成。它包含了传统的计算、存储和网络服务等多种服务和解决方案。此外，它还提供了端到端的应用程序开发框架、设置和易于部署的设施、安全管理服务、传统的或数据库以及云原生服务。它还通过平台即服务 (PaaS) 简化了应用程序开发，并提供了集成的移动后端即服务 (MaaS) 潜力。为了使内部开发易于扩展，提供了可直接使用的服务以及托管功能，以便应用程序可以快速部署。有关此云平台架构和特性的更多细节，可以从 [19] 和 [20] 获取。

在本节中，重点将开发移动和桌面应用程序，这些程序可以向 IBM Cloud 数据库发送和接收数据，并向托管在 IBM Cloud 上的 servlet 发送查询并接收响应。

# 2.7.1. IBM Cloud 数据库配置

在本节中，将配置 IBM Cloud 数据库并开发能够执行以下任务的应用程序：

- I. 从 Android 应用向 IBM Bluemix cloudant 数据库发送和接收数据
- II. 从桌面应用向 IBM Bluemix cloudant 数据库发送和接收数据
- III. 从 Web 应用向 IBM Bluemix cloudant 数据库发送和接收数据。

起点是按照以下步骤创建 IBM Cloud 账户：

- 1. 转到链接 https://cloud.ibm.com
- 2. 点击创建 IBM Cloud 账户。显示图 2.68 所示的网页。

![](img/2b52fde0e707e8c2f05a10309c3f8982_82_0.png)

图 2.68. IBM Cloud 登录页面。

- 3. IBM Cloud 将向输入的邮箱发送 7 位验证码。如图 2.69 所示。

![](img/2b52fde0e707e8c2f05a10309c3f8982_83_0.png)

图 2.69. 验证。

- 4. 填入个人信息并按图 2.70 所示创建账户。

![](img/2b52fde0e707e8c2f05a10309c3f8982_83_1.png)

图 2.70. 个人信息。

- 5. 显示带有某些通用信息的页面，点击继续进入图 2.71 所示的 IBM Cloud 仪表板。

![](img/2b52fde0e707e8c2f05a10309c3f8982_84_0.png)

图 2.71. 仪表板。

- 6. 点击图 2.72 所示的创建资源。展开 Services，选择 Databases 中的 Cloudant。

![](img/2b52fde0e707e8c2f05a10309c3f8982_84_1.png)

图 2.72. Cloudant。

- 7. 设置身份验证方法为 IAM 并点击创建。

![](img/2b52fde0e707e8c2f05a10309c3f8982_84_2.png)

图 2.73. IAM。

- 8. 数据库通常需要一些时间来部署。完成后，显示图 2.74 所示的界面。

![](img/2b52fde0e707e8c2f05a10309c3f8982_85_0.png)

图 2.74. 服务。

- 9. 点击图 2.75 所示的端点，将用于从 Java 程序访问数据库。

![](img/2b52fde0e707e8c2f05a10309c3f8982_85_1.png)

图 2.75. 端点。

- 10. 点击图 2.76 所示的启动。

![](img/2b52fde0e707e8c2f05a10309c3f8982_85_2.png)

图 2.76. 启动。

- 11. 将弹出图 2.77 所示的登录界面。

![](img/2b52fde0e707e8c2f05a10309c3f8982_86_0.png)

图 2.77. 登录。

- 12. 点击图 2.78 所示的创建数据库。

![](img/2b52fde0e707e8c2f05a10309c3f8982_86_1.png)

图 2.78. 创建数据库。

- 13. 之后，为数据库命名，选择非分区，并按图 2.79 所示点击创建。

## 创建数据库

图 2.79. 非分区数据库。

