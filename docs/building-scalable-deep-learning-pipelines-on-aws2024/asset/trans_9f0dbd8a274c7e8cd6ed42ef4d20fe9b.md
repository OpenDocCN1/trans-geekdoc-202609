

- 重新启动 Airflow Web 服务器：

```
[In]: airflow webserver &
```

## 基于 Docker 的部署

在 Docker 中运行 Apache Airflow 相比传统独立安装具有显著优势，它提供了一个简化且一致的环境，从而简化了设置过程，减少了配置错误，并增强了可移植性。Docker 将 Airflow 及其依赖项封装在容器内，确保了工作流在不同系统（无论是开发、测试还是生产环境）上的可靠执行。

要在 Docker 中设置 Apache Airflow，您需要安装 Docker 和 Docker Compose。Docker 将应用程序（包括所有必要的代码、库和依赖项）打包成容器，确保在不同环境中保持一致性。Docker Compose 通过允许您定义和管理多容器应用程序，进一步简化了这一过程，这对于像 Apache Airflow 这样复杂的设置特别有用，因为在这些设置中，Web 服务器、调度器、数据库等服务必须协同工作。

Apache Airflow 项目提供了一个官方的 `docker-compose.yml` 文件，该文件定义了所有必需的服务，包括用于工作流管理的 Airflow Web 服务器、用于任务执行的调度器、用于元数据存储的 Postgres、用于任务队列管理的 Redis，以及用于执行任务和触发延迟操作的 workers 和 triggerers。

在 Linux 操作系统（例如 Ubuntu）上安装 Docker 以进行测试的最简单方法是使用 Docker 提供的便利脚本，位于 `https://get.docker.com/`。在您的 EC2 实例上安装 Docker 后，您使用官方的 Docker Compose 配置来设置并运行 Airflow。

请遵循以下步骤：

### 步骤 1：创建脚本文件。

- 一旦您通过 SSH 连接到 EC2 实例，首先创建一个新的 shell 脚本文件：

```
[In]: nano install-docker.sh
```

- 将 Docker 提供的整个脚本内容复制并粘贴到该文件中。该脚本位于 https://get.docker.com/，用于自动化 Docker 安装过程。

### 步骤 2：使脚本可执行。

- 粘贴脚本后，按 Ctrl + X，然后按 Y，最后按 Enter 保存并关闭文件。
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

第一条命令从官方 GitHub 仓库下载最新版本的 Docker Compose 二进制文件，选择适合您系统的正确版本并将其保存为 /usr/bin/docker-compose。第二条命令通过设置适当的权限使 Docker Compose 二进制文件可执行。

- 通过检查 Docker Compose 的版本确认安装：

```
[In]: docker-compose -version
```

### 步骤 7：下载 Airflow Docker Compose 配置。

- Apache Airflow 提供了一个官方的 Docker Compose 设置，使运行 Airflow 变得轻松。下载 docker-compose.yaml 文件，该文件包含在 Docker 容器中运行 Airflow 及其相关服务（如 PostgreSQL 和 Redis）的配置：

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

- 创建 .env 文件以设置必要的环境变量，包括您的用户 ID 和组 ID，以避免权限问题：

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
    - 默认情况下，Airflow 的 Web 服务器运行在 8080 端口。
    - 确保您的 EC2 实例关联的安全组中打开了 8080 端口。您可以在安全组中添加入站规则，允许来自您的 IP 地址的 8080 端口的流量。

入站规则示例：

- 类型：自定义 TCP 规则
- 协议：TCP
- 端口范围：8080
- 源：您的 IP（或 0.0.0.0/0 表示开放访问）

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

- 运行以下命令在 8888 端口上启动 JupyterLab，并监听所有可用的 IP 地址：

```
[In]: jupyter lab --ip=0.0.0.0 --port=8888 --no-browser
```

### 步骤 5：配置安全组并访问 JupyterLab

- 更新安全组：确保您的 EC2 实例的安全组允许 8888 端口的入站流量。为此：
    - 前往 AWS 管理控制台中的 EC2 仪表板。
    - 在左侧菜单中，在 Network & Security 下选择 Security Groups。
    - 选择与您的 EC2 实例关联的安全组。
    - 点击 Inbound rules 选项卡，然后选择 Edit inbound rules。
    - 添加一条规则，允许来自您的 IP 或任何 IP（0.0.0.0/0，出于测试目的；出于安全原因，请谨慎使用此选项）的 8888 端口上的自定义 TCP 流量。
- 访问 JupyterLab：打开网络浏览器并导航至 `http://<your_ec2_instance_ip>:8888`。

现在，您应该能够使用您生成的密码在 EC2 实例上访问 Jupyter。

## 设置 Databricks 账户和工作区

如果您更喜欢使用 Databricks 对数据进行处理，以下步骤概述了创建 Databricks 账户、设置工作区以及将其与您的 AWS 账户连接的过程：

### 步骤 1：注册 Databricks

- 前往位于 https://www.databricks.com/ 的 Databricks 网站。
- 点击右上角的 “Try Databricks” 按钮。
- 填写创建账户所需的信息，包括您的名和姓、电子邮件地址、公司、职位和国家，并选择您的云提供商（在本例中为 AWS；其他为 Microsoft Azure 和 Google Cloud Platform）。

