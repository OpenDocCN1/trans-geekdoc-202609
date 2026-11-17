

- 3. numpy==1.19.0
- 4. pandas==1.0.5
- 5. scikit-learn==0.23.1
- 6. scipy==1.5.1
- 7. sklearn==0.0
- 8.
- 9. # testing requirements
- 10. pytest<5.0.0,>=4.6.6
- 11.
- 12. # packaging
- 13. setuptools==40.6.3
- 14. wheel==0.32.3
- 15.
- 16. # FastAPI app requirements
- 17. fastapi>=0.68.0,<0.69.0
- 18. pydantic>=1.8.0,<2.0.0
- 19. uvicorn>=0.15.0,<0.16.0
- 20. gunicorn>=20.1.0

## Dockerfile

创建一个 `Dockerfile`，将其命名为 Dockerfile（不带任何文件扩展名），并向其中添加以下命令。

```
1. FROM python:3.7-slim-buster
2.
3. RUN apt-get update && apt-get install -y \
4.   build-essential \
5.   libpq-dev \
6.   && rm -rf /var/lib/apt/lists/*
7.
8. RUN pip install --upgrade pip
9.
10. COPY . /code
11.
12. RUN chmod +x /code/src
13.
14. RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt
15.
16. EXPOSE 8005
17.
18. WORKDIR /code/src
19.
20. ENV PYTHONPATH "${PYTHONPATH}:/code/src"
21.
22. CMD pip install -e .
```

在前述 Dockerfile 中，它首先会拉取基础镜像，即 Python 3.7 slim buster，并安装必要的软件包。之后，将从要求文件安装软件包，并公开 **8005** 端口，以便可以在 Docker 容器外部访问。最后，它将在 **ENV** 指令中分配 **PYTHONPATH**，并执行 CMD 指令中提到的命令，以可编辑模式安装 Python 包。

## 在 GitHub 上创建个人访问令牌 (PAT)

如果使用 `git cli` 命令执行拉取、推送或克隆等任何操作，则 GitHub 密码将不再可用。事实上，GitHub 已移除密码身份验证。相反，您必须使用 **个人访问令牌 (PAT)**。

PAT 是使用 GitHub API 或命令行进行 GitHub Enterprise Server 身份验证时密码的替代方案。

首先，您需要创建一个 PAT。此过程在以下链接中描述：

https://docs.github.com/en/enterprise-server@3.4/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

要生成或重新生成 PAT，您可以转到 Settings | Tokens（需要登录）：

https://github.com/settings/tokens

如果系统未提示您输入用户名和密码，您的凭据可能已缓存在本地计算机中。

## 在 GitHub 仓库上创建 Webhook

Webhook 可视为一种轻量级 API，在由特定事件触发后可实现单向数据共享。在 GitHub 中，当对仓库执行推送和拉取等操作时，可以触发 Webhook。借助 GitHub Webhook，您可以在远程服务器上触发 CI 阶段。

转到您的 GitHub 仓库 | Settings | Webhooks。

或者，您可以使用以下 URL 直接跳转到该页面：

```
https://github.com/<username>/<your-repo-name>/settings/hooks
```

在当前情况下，如下所示：

```
https://github.com/suhas-ds/docker_pkg_jenkins/settings/hooks
```

您不能在 GitHub Webhook 的负载 URL 中使用 https://localhost:8080/github-webhook/，因为 localhost URL 需要暴露到互联网上。您可以使用 ngrok 将 localhost URL 暴露到互联网。有关更多详细信息，请参阅 ngrok 官方网站 https://ngrok.com/。

在此，ngrok 仅用于演示目的；但是，在部署阶段可以使用远程服务器的 IP 或域名。

使用命令 ngrok http 8080 将 8080 端口公开暴露。

![](img/cc4299656808e62a294f1843a1e18e72_221_0.png)

图 9.2：ngrok

如下图所示提供负载 URL。负载 URL 格式已在本章前面讨论过。将 **内容类型** 选择为 **application/json** 格式。**密钥** 字段为可选项。目前请留空。

## Webhooks / 管理 Webhook

![](img/cc4299656808e62a294f1843a1e18e72_222_0.png)

图 9.3：GitHub Webhook

如下图所示，选择 **启用 SSL 验证** 和 **仅推送事件** 选项，这样只有在有人向仓库推送更新时才会发送数据。但是，您也可以选择单个事件，即 **让我选择单个事件**。

现在，单击 **添加 Webhook** 按钮以保存 Jenkins GitHub Webhook。

![](img/cc4299656808e62a294f1843a1e18e72_222_1.png)

图 9.4：GitHub Webhook

## 配置 Jenkins

在当前场景中，主要需要配置两个部分：GitHub Webhook 集成和扩展电子邮件集成。

- 1. 转到 Jenkins 控制面板。
- 2. 转到 **管理 Jenkins | 管理插件**。
- 3. 安装 Git、GitHub 和电子邮件插件，无需重启。

如果上述插件已被选中，您可以继续下一步。

现在，让我们在 Jenkins 中配置 GitHub Webhook。

转到 **管理 Jenkins | 配置系统**。

向下滚动并在 **GitHub** 部分中更新 **API URL**，如下所示：

```
https://api.github.com
```

在 **凭据** 部分中，添加上一步生成的 GitHub PAT。您可以将 **名称** 字段留空。

最后，单击 **保存** 按钮。

下图显示了 Jenkins 中的 GitHub Webhook 集成：

![](img/cc4299656808e62a294f1843a1e18e72_223_0.png)

图 9.5：Jenkins 中的 GitHub 配置

现在，每当开发者向仓库推送更新时，Jenkins 都会检测到更改并开始逐个执行一系列命令。

接下来，配置电子邮件以用于反馈循环或状态更新，例如成功或失败。

转到 **管理 Jenkins | 配置系统**。

向下滚动并更新 **GitHub** 部分中的字段。

如下图所示，**默认主题** 字段在开头添加了 **状态**。此外，在 **默认内容** 字段中添加了电子邮件正文。它高度可自定义，因此您可以根据要求进行更新。

![](img/cc4299656808e62a294f1843a1e18e72_224_0.png)

图 9.6：电子邮件配置

在 **默认触发器** 部分中，选择 **始终** 复选框，以便 Jenkins 在成功和失败场景下都发送状态电子邮件，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_224_1.png)

图 9.7：电子邮件配置 - 触发器

现在，在 **默认内容类型** 字段的下拉列表中选择 **HTML (text/html)**，并在 **默认收件人** 中添加您的电子邮件 ID，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_225_0.png)

## 图 9.8：电子邮件配置 – 内容类型和收件人

在扩展电子邮件通知部分中，提供电子邮件通知的详细信息。在当前场景中，提供了 Gmail 详细信息，如下所示：

- smtp.gmail.com 用于 SMTP 服务器
- 465 用于 SMTP 端口
- 添加电子邮件登录凭据
- 选中 **使用 SSL** 复选框
- 单击 **保存** 按钮

如下图所示提供您的电子邮件详细信息：

![](img/cc4299656808e62a294f1843a1e18e72_225_1.png)

## 图 9.9：扩展电子邮件通知

向下滚动并单击 **应用** 和 **保存** 按钮以保存更改，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_226_0.png)

## 图 9.10：扩展电子邮件通知

如果您要为电子邮件通知集成 Gmail 帐户，则需要在 Gmail 帐户设置中允许不够安全的应用。如果处于关闭状态，可以访问以下 URL 将其打开。

https://myaccount.google.com/lesssecureapps

有关更多详细信息，请访问 https://support.google.com/accounts/answer/6010255?hl=en。

Jenkins 所需的配置已完成。

## 使用 Jenkins 创建 CI/CD 管道

现在，您将使用 GitHub 和 Jenkins 构建一个简单的 CI/CD 管道。当开发者向 GitHub 仓库推送更新时，GitHub Webhook 会检测到更改并将通知发送到 Jenkins。Jenkins 从 GitHub 仓库拉取最新代码，构建 Docker 镜像，并使用该镜像运行容器。接下来，它训练模型并从训练好的模型中导出 pickle 对象。在下一步中，pytest 结果会被导出并在 Jenkins 中显示。所有测试通过后，它将运行 ML Web 应用。最后，它将通过电子邮件向开发者或相关团队发送反馈。

![](img/cc4299656808e62a294f1843a1e18e72_226_1.png)

## 图 9.11：使用 Jenkins 构建的 CI/CD 管道

