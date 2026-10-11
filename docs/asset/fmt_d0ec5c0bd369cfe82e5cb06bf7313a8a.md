
```
[In]: nano install-docker.sh
```

- 将 Docker 提供的整个脚本内容复制并粘贴到该文件中。该脚本位于 https://get.docker.com/，用于自动化 Docker 安装过程。

### 步骤 2：使脚本可执行。

- 粘贴脚本后，按 `Ctrl + X`，然后按 `Y`，最后按 `Enter` 保存并关闭文件。

- 通过运行以下命令设置脚本为可执行：

```
[In]: chmod +x install-docker.sh
```

### 步骤 3：以 root 权限运行脚本。

- 执行脚本以管理员权限安装 Docker：

```
[In]: sudo ./install-docker.sh
```

- 脚本将检测您的 Linux 发行版和版本，然后相应地进行 Docker 安装。

### 步骤 4：验证 Docker 安装。

- 脚本完成后，运行以下命令验证 Docker 是否正确安装：

```
[In]: docker -version
```

- 您应该看到实例上安装的 Docker 版本，确认安装成功。

### 步骤 5：运行测试 Docker 容器。

- 为确保 Docker 正常工作，运行一个测试 Docker 容器：

```bash
[In]: sudo docker run hello-world
```

- 该命令将下载并运行一个测试镜像，如果成功，将显示确认消息。

### 步骤 6：安装 Docker Compose。

- 使用以下命令下载并安装 Docker Compose：

```bash
[In]: sudo curl -L \
         "https://github.com/docker/compose/releases/latest/download/" \
         "docker-compose-$(uname -s | tr '[:upper:]' '[:lower:]')" \
         "-$(uname -m)" -o /usr/bin/docker-compose
```

```bash
[In]: sudo chmod 755 /usr/bin/docker-compose
```

第一条命令从官方 GitHub 仓库下载最新版本的 Docker Compose 二进制文件，选择适合您系统的正确版本并将其保存为 `/usr/bin/docker-compose`。第二条命令通过设置适当的权限使 Docker Compose 二进制文件可执行。

- 通过检查 Docker Compose 的版本确认安装：

```
[In]: docker-compose -version
```

### 步骤 7：下载 Airflow Docker Compose 配置。

- Apache Airflow 提供了一个官方的 Docker Compose 设置，使运行 Airflow 变得轻松。下载 `docker-compose.yaml` 文件，该文件包含在 Docker 容器中运行 Airflow 及其相关服务（如 PostgreSQL 和 Redis）的配置：

```
[In]: curl -Lf0 \
'https://airflow.apache.org/docs/apache-airflow/' \
'2.7.2/docker-compose.yaml'
```

### 步骤 8：准备环境。

- 创建 Airflow 将用于 DAG、日志和插件的目录：

```
[In]: mkdir -p ./dags ./logs ./plugins
```

- 创建 `.env` 文件以设置必要的环境变量，包括您的用户 ID 和组 ID，以避免权限问题：

```
[In]: echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env
```

### 步骤 9：初始化 Airflow 数据库。

- 运行以下命令初始化 Airflow 数据库：

```
[In]: docker compose up airflow-init
```

### 步骤 10：启动 Airflow 服务。

- 数据库初始化完成后，启动 Airflow Web 服务器、调度器和其他必要服务：

```
[In]: docker compose up -d
```

- 通过检查状态确保所有 Airflow 容器都在运行：

```
[In]: docker compose ps
```

### 步骤 11：访问 Airflow Web 界面。

- 获取您的 EC2 实例的公共 IP：

    - 您可以在 AWS 管理控制台中您的 EC2 实例详情下找到公共 IP。

- 在安全组中打开所需端口：

    - 默认情况下，Airflow 的 Web 服务器运行在 `8080` 端口。

    - 确保您的 EC2 实例关联的安全组中打开了 `8080` 端口。您可以在安全组中添加入站规则，允许来自您的 IP 地址的 `8080` 端口的流量。

入站规则示例：

- 类型：自定义 TCP 规则

- 协议：TCP

- 端口范围：8080

- 源：您的 IP（或 `0.0.0.0/0` 表示开放访问）

- 在您的浏览器中访问 Airflow：

    - 打开网络浏览器并导航至：

```
[In]: http://<your-ec2-public-ip>:8080
```

    - 将 `<your-ec2-public-ip>` 替换为您 EC2 实例的实际公共 IP。

    - 您应该能看到 Airflow 登录页面/Airflow 仪表板。

## 安装 JupyterLab

JupyterLab 是一个开源的基于 Web 的交互式开发环境 (IDE)，用于 Jupyter 笔记本、代码和数据。它提供了一种灵活且可扩展的架构，可用于处理多种编程语言（包括 Python）中的代码、数据和可视化。

以下是逐步说明，用于在 EC2 实例上安装和配置 JupyterLab：

### 步骤 1：安装 JupyterLab

- 连接到您的 EC2 实例并打开命令提示符。

- 激活您的虚拟环境：

```
[In]: source myenv/bin/activate
```

- 运行以下命令使用 pip 下载并安装 JupyterLab 及其依赖项：

```
[In]: pip install jupyterlab
```

### 步骤 2：生成 Jupyter Notebook 配置

- 运行以下代码生成 Jupyter Notebook 配置文件：

```
[In]: jupyter notebook --generate-config
```

生成 Jupyter Notebook 配置文件允许您自定义 Jupyter Notebook 环境的各个方面，例如指定默认设置、配置安全选项以及设置认证机制。

### 步骤 3：为 JupyterLab 设置密码

```
[In]: jupyter notebook password
```

### 步骤 4：启动 JupyterLab

- 运行以下命令在 `8888` 端口上启动 JupyterLab，并监听所有可用的 IP 地址：

```
[In]: jupyter lab --ip=0.0.0.0 --port=8888 --no-browser
```

### 步骤 5：配置安全组并访问 JupyterLab

- 更新安全组：确保您的 EC2 实例的安全组允许 `8888` 端口的入站流量。为此：

    - 前往 AWS 管理控制台中的 EC2 仪表板。

    - 在左侧菜单中，在 Network & Security 下选择 Security Groups。

    - 选择与您的 EC2 实例关联的安全组。

    - 点击 Inbound rules 选项卡，然后选择 Edit inbound rules。

    - 添加一条规则，允许来自您的 IP 或任何 IP（`0.0.0.0/0`，出于测试目的；出于安全原因，请谨慎使用此选项）的 `8888` 端口上的自定义 TCP 流量。

- 访问 JupyterLab：打开网络浏览器并导航至 `http://<your_ec2_instance_ip>:8888`。

现在，您应该能够使用您生成的密码在 EC2 实例上访问 Jupyter。

## 设置 Databricks 账户和工作区

如果您更喜欢使用 Databricks 对数据进行处理，以下步骤概述了创建 Databricks 账户、设置工作区以及将其与您的 AWS 账户连接的过程：

### 步骤 1：注册 Databricks

- 前往位于 https://www.databricks.com/ 的 Databricks 网站。

- 点击右上角的 “Try Databricks” 按钮。

- 填写创建账户所需的信息，包括您的名和姓、电子邮件地址、公司、职位和国家，并选择您的云提供商（在本例中为 AWS；其他为 Microsoft Azure 和 Google Cloud Platform）。

## 步骤 2：确认您的电子邮件。

- 注册后，请查看来自 Databricks 的验证邮件。

- 点击邮件中的验证链接以确认您的电子邮件地址。

## 步骤 3：登录 Databricks。

- 电子邮件确认后，使用您的凭据登录 Databricks 平台。

## 步骤 4：创建工作区。

- 登录后，系统将提示您创建一个 Databricks 工作区。

- 为您的工作区选择一个名称。

- 按照屏幕上的说明完成工作区的创建过程。

## 步骤 5：探索 Databricks。

- 工作区创建完成后，您可以开始探索 Databricks 环境。

- 熟悉工作区界面、笔记本及其他功能。

## 步骤 6：从 Databricks 访问 S3。

- 在使用 Databricks 时，可以使用不同的方法来访问 S3 存储桶。对于测试和快速搭建，您可以在 Databricks 中运行以下代码：

```python
ACCESS_KEY = "your-access-key"
SECRET_KEY = "your-secret-key"
AWS_BUCKET_NAME = "your-bucket-name"
MOUNT_NAME = "/mnt/datalake-central"
dbutils.fs.mount(
    source=f"s3a://{ACCESS_KEY}:{SECRET_KEY}@{AWS_BUCKET_NAME}/",
    mount_point=MOUNT_NAME,
    extra_configs={
        "fs.s3a.access.key": ACCESS_KEY,
        "fs.s3a.secret.key": SECRET_KEY
    }
)
```

此代码包含两个主要部分——变量赋值和挂载 S3 存储桶：

### 变量赋值

- `ACCESS_KEY`：从环境变量中获取 AWS 访问密钥。

- `SECRET_KEY`：从环境变量中获取 AWS 秘密密钥。

- `AWS_BUCKET_NAME`：存储您想要挂载的 S3 存储桶名称。

- `MOUNT_NAME`：指定 S3 存储桶的挂载点。在此示例中，挂载名称为“datalake-central”，但可以是任何名称。在挂载名称前加上 `/mnt/` 是 Linux 环境中的常见约定，尤其是在挂载外部存储设备或网络共享时。

### 挂载 S3 存储桶

- `dbutils.fs.mount`：此函数用于挂载 S3 存储桶。它接受几个参数：

    - `source`：S3 存储桶的 URL，包括访问密钥和秘密密钥。这种格式允许 Databricks 使用提供的凭据对 S3 存储桶进行身份验证。

    - `mount_point`：S3 存储桶将挂载到的本地挂载点。

    - `extra_configs`：额外配置，在此情况下为 S3 存储桶的访问密钥和秘密密钥。`extra_configs` 参数为挂载操作提供额外的配置。此处，它再次包含访问密钥和秘密密钥，这是访问 S3 存储桶所必需的。

通过执行此代码，您将把指定的 S3 存储桶挂载到 Databricks 环境中的指定挂载点，从而可以像操作本地文件系统一样与该 S3 存储桶交互。

您可以按照以下方式从 AWS 管理控制台获取代码所需的访问密钥和秘密密钥：

- 前往 AWS 管理控制台（https://aws.amazon.com/console/）并使用您的 AWS 账户凭据登录。

- 登录后，在 AWS 管理控制台的服务列表中选择一个服务，导航至 IAM（身份和访问管理）服务。

- 在 IAM 控制台中，从左侧导航窗格中选择“Users”。

- 选择要为其创建访问密钥和秘密密钥对的 IAM 用户。

- 在“Security credentials”选项卡中，向下滚动至“Access keys”部分。

- 点击“Create access key”按钮。

- 在“Use case”下选择“Application running on an AWS compute service”，并在屏幕底部确认消息“I understand the above recommendation and want to proceed to create an access key”。

- 创建访问密钥后，您将看到访问密钥 ID 和秘密访问密钥。请记下这些凭据，因为它们只会显示一次。如果您丢失了它们，将需要创建一个新的访问密钥。

- 确保与访问密钥对关联的 IAM 用户或角色具有执行 S3 操作所需的权限。这可以通过附加适当的策略（如 `AmazonS3FullAccess`）来实现。

这种方法的一个问题是代码中硬编码凭据带来的安全风险，这可能导致意外泄露。另一个问题与维护有关：更新凭据需要修改代码，这可能很繁琐。

更好的解决方案是使用 IAM 角色，AWS 会安全地管理这些角色，无需在代码中指定访问 S3 所需的凭据。这种方法更加安全且易于扩展，尤其是在生产环境中。

IAM 角色是您可以创建并分配特定权限的 AWS 身份，允许受信任的实体（如运行 Databricks 的 EC2 实例）假设该角色并在 AWS 中执行操作。当将 IAM 角色附加到托管您的 Databricks 集群的 EC2 实例时，AWS 会自动为这些实例提供临时凭据。这些凭据由 AWS 轮换和管理，从而消除了在代码中嵌入访问密钥的需要。

请按照以下步骤在 Databricks 中设置和使用 IAM 角色：

## 步骤 1：创建具有 S3 访问权限的 IAM 角色。

- 登录 AWS 管理控制台并前往 IAM 服务。

- 创建一个新的角色：

    - 在左侧菜单中点击 Roles，然后点击 Create role。

    - 选择 EC2 作为受信任实体，因为该角色将由运行 Databricks 的 EC2 实例假设。

- 附加策略：

    - 将 `AmazonS3FullAccess` 策略附加到角色，或者创建一个根据您的需求定制特定 S3 权限的自定义策略。

- 完成角色创建：

    - 为角色命名（例如，`DatabricksS3AccessRole`）并完成创建过程。

## 步骤 2：将 IAM 角色附加到 Databricks 集群。

- 在 AWS 管理控制台中，导航至 EC2 仪表板。

- 识别组成您的 Databricks 集群的 EC2 实例。

- 附加 IAM 角色：

    - 选择每个实例，前往 Actions > Security > Modify IAM role，并附加您创建的 `DatabricksS3AccessRole`。

## 步骤 3：在 Databricks 中无需硬编码凭据即可访问 S3。

- 成功创建 IAM 角色并将其附加到您的 Databricks 集群后，现在您可以安全地访问您的 S3 存储桶，而无需硬编码任何凭据。以下代码片段演示了如何使用 IAM 角色挂载 S3 存储桶：

```python
AWS_BUCKET_NAME = "your-bucket-name"
MOUNT_NAME = "/mnt/datalake-central"
dbutils.fs.mount(
    source=f"s3a://{AWS_BUCKET_NAME}/",
    mount_point=MOUNT_NAME
)
```

您可以运行以下代码来测试挂载是否成功：

```python
MOUNT_NAME = "/mnt/datalake-central"
mounts = dbutils.fs.mounts()
mount_point_exists = any(
    mount.mountPoint == MOUNT_NAME for mount in mounts
)
if mount_point_exists:
    print("S3 bucket was successfully mounted.")
else:
    print("S3 bucket mount failed.")
```

`S3 bucket was successfully mounted.`

以下是每行代码的解析：

- `MOUNT_NAME = "/mnt/datalake-central"`：这行代码定义了一个名为 `MOUNT_NAME` 的变量，并将其赋值为“/mnt/datalake-central”。该变量存储在 Databricks 文件系统中 S3 存储桶挂载点的路径。

- `mounts = dbutils.fs.mounts()`：这行代码使用 `dbutils.fs` 模块中的 `mounts()` 函数获取 Databricks 环境中当前所有已挂载文件系统的列表。列表中的每一项代表一个已挂载的文件系统。

- `mount_point_exists = any(mount.mountPoint == MOUNT_NAME for mount in mounts)`：这行代码检查指定的挂载点是否存在于已挂载的文件系统中。它使用带有 `any()` 函数的生成器表达式，遍历每个已挂载的文件系统（`mount`），并检查其 `mountPoint` 属性是否与 `MOUNT_NAME` 变量中存储的值匹配。
