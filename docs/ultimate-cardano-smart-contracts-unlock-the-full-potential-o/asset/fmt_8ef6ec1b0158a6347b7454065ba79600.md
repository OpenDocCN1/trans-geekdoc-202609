
Kupo[^(19)](#c08.xhtml#ftn19) 是一个开源的 Cardano 区块链索引器，具有快速、轻量级和可配置的特点。其 [API 文档][^(20)](#c08.xhtml#ftn20) 非常完善，是许多倾向于使用内部工具的 Cardano 开发团队的首选。区块链被设计为一系列相互连接的区块，形成一条链。然而，这使得执行高效的数据查询变得非常困难。这就是为什么我们需要索引器来接收区块链数据并将其存储在数据库中。这些数据可以被索引，然后进行查询、过滤和分析。`Kupo` 可以下载、构建并在本地安装，也可以使用 `Demeter.run` 设置为托管服务。

我们将再次进入 Project 页面并添加另一个资源，这次是 `Kupo` 资源。选择 deploy 并为 preprod 网络创建资源。接下来，复制 HTTPS URL 以备将来参考。我们应该能看到四个资源：Workspace、Node、Ogmios 和 Kupo，如 [Figure 8.9](#c08.xhtml#fig8_9) 所示。

![](images/Figure-8.9.jpg)

**Figure 8.9:** Demeter.run Resources

要快速测试确认 `Kupo` 是否正常工作，可以执行以下命令，并将主机名替换为从 `Demeter.run` Kupo 资源复制的主机名。

```
$ curl -fsSL https://dmtr_kupo12e…mph005.preprod-v2.kupo-m1.demeter.run/health
# TYPE kupo_configuration_indexes gauge
kupo_configuration_indexes  1.0
# TYPE kupo_connection_status gauge
kupo_connection_status  1.0
# TYPE kupo_most_recent_checkpoint counter
kupo_most_recent_checkpoint  59235759
# TYPE kupo_most_recent_node_tip counter
kupo_most_recent_node_tip  59235759
```

在这种情况下，`Kupo` 实例是健康的，你可以看到最近的 `checkpoint` 和 `node tip`。Checkpoints 是已被 `Kupo` 处理的链上区块，主要用于重启后与区块链同步[^(21)](#c08.xhtml#ftn21)。

## Code Example

现在，我们准备好更新 vesting 和 ticket 代码示例，以便将 `Ogmios` 和 `Kupo` 一起使用。`Lucid` 为此确切目的提供了一个 provider，称为 `kupmios`，如 [Figure 8.10](#c08.xhtml#fig8_10) 所示。

![](images/Figure-8.10.jpg)

**Figure 8.10:** Lucid Kupmios[^(22)](#c08.xhtml#ftn22)

通过切换到 `Kupmios` provider，vesting 示例无需其他更改即可工作。然而，ticket 示例需要对 `pages/API/getTicketMetadata.ts` 进行更改，如 [Figure 8.11](#c08.xhtml#fig8_11) 所示。

![](images/Figure-8.11.jpg)

**Figure 8.11:** Kupo getMetadata[^(23)](#c08.xhtml#ftn23)

要从 `Kupo` 检索元数据，首先获取与 mint 交易关联的交易。Token asset 在第 70 行提供，结果按区块链上发生的交易顺序排序。因此，mint 是第一笔交易，所以使用第一个交易 ID，然后在第 73 行查找该特定交易的元数据。第 76-81 行解析元数据对象并将结果返回给前端。

## Setup

要设置 `Demeter.run` 环境以运行 `Kupo` + `Ogmios` 演示，请在终端窗口中执行以下命令。

```
$ export NEXT_PUBLIC_KUPO_API=https://dmtr_kupo12e…mph005.preprod-v2.kupo-m1.demeter.run
$ export NEXT_PUBLIC_OGMIOS_API=wss://dmtr_ogmios1v…g0t6mk.preprod-v5.ogmios-m1.demeter.run
$ export NEXT_PUBLIC_ENV="dev"
$ export NEXT_PUBLIC_HOST="your-demeter-run-host"
$ export NEXT_PUBLIC_PROTOCOL="https"
$ export NEXT_PUBLIC_PORT=""
```

## Local Devnet

得益于 BoxBean[^(24)](#c08.xhtml#ftn24) 的出色工作；现在可以轻松安装本地 Devnet，类似于 Ethereum 的 Hardhat。`Yaci Devkit` 使用轻量级组件对区块链数据进行索引和查询。特别是，BoxBean 创建了 `Yaci`，一个模块化的、基于 Java 的 Ouroboros 迷你协议，它监听传入的区块、监控本地 mempool 并提交交易[^(25)](#c08.xhtml#ftn25)。该团队还创建了 `Yaci Store`，一个基于 Java 的解决方案，提供 API 查询索引数据并处理回滚[^(26)](#c08.xhtml#ftn26)。为了支持与 Nami 和 Helios 等浏览器扩展钱包集成以进行链下交易构建，本地 Devnet 还将使用本地 `Cardano DB Sync` 向本地 `Blockfrost API` provider 提供区块链数据。

设置本地 devnet 需要以下五个步骤：

1.  Set up `YaciDevkit`[^(27)](#c08.xhtml#ftn27)
2.  Set up `Cardano DB Sync`
3.  Set up `Blockfrost backend RYO` (Run Your Own)
4.  Build and install `Nami browser wallet` with a local Testnet network
5.  Top up wallet with funds

## Environment

以下设置说明已在 Ubuntu Linux 20.04.1 上测试通过。其他操作系统可能需要额外的设置。

## Install Docker

```
$ sudo apt -y install apt-transport-https ca-certificates curl software-properties-common
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
$ echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
$ sudo apt update
$ sudo apt -y install docker-ce docker-ce-cli containerd.io
$ sudo usermod -aG docker $USER
$ newgrp docker
$ docker run hello-world
```

### Step 1: Setting up Yaci Devkit

安装好 Docker 后，你可以 `cd` 进入 `yaci-devkit` 目录，以便安装以下两个 docker 镜像[^(28)](#c08.xhtml#ftn28)。我们将作为设置过程的一部分安装以下镜像：

| REPOSITORY | TAG | IMAGE ID | SIZE |
| :--- | :--- | :--- | :--- |
| bloxbean/yaci-cli | 0.0.20-beta1 | 0b5f0541f396 | 1.2GB |
| bloxbean/yaci-viewer | 0.0.9 | 73b52df24dfb | 579MB |

```
$ git clone https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts.git --recurse-submodules
$ cd Mastering-Cardano-Smart-Contracts/chapter_08/local-devnet/yaci-devkit
$ sudo ./start.sh
$ sudo ./yaci-cli.sh
```

要启动一个新集群，请使用命令 `create-node -o --start`。

```
yaci-cli:>create-node -o --start
[Success] Delete existing folder
[Success] Create cluster folder !!!
[Success] Slot length updated in genesis.json
[Success] Updated configuration.yaml
[Success] Update ports
[Success] Create Cluster : default
###### Node Details (Container) ######
[Node port] 3001
[Node Socket Paths]
/clusters/default/node-spo1/node.sock
[Submit Api Port] 8090
[Protocol Magic] 42
[Block Time] 1.0 sec
[Slot Length] 1.0 sec
[Start Time] 0
#################### URLS (Host) ####################
[Yaci Viewer] http://localhost:5173
[Yaci Store Swagger UI] http://localhost:8080/swagger-ui.html
[Yaci Store Api URL] http://localhost:8080/api/v1/
[Pool Id] pool1wvqhvyrgwch4jq9aa84hc8q4kzvyq2z3xr6mpafkqmx9wce39zy…
[OK] Yaci Store Started
devnet:default>
```

有关启动选项和配置的更多信息，请参阅 GitHub 仓库：[https://github.com/bloxbean/yaci-devkit](https://github.com/bloxbean/yaci-devkit)。

### Step 2: Starting DB Sync

在一个新的终端窗口中：

```
$ cd chapter_08/local-devnet/yaci-devkit
$ ./start-db-sync.sh
```

如果成功，你应该会看到以下输出。

```
...
cardano-db-sync_1  | [db-sync-node:Info:65] [2024-05-08 10:15:13.01 UTC] Insert Babbage Block: epoch 0, slot 244, block 244, hash 74ec222296e80d0dae52fd7723c7317746928144fdbf8b9f5fd31a7ca6daf095
cardano-db-sync_1  | [db-sync-node:Info:65] [2024-05-08 10:15:14.00 UTC] Insert Babbage Block: epoch 0, slot 245, block 245, hash e13b22299709d612d8381bc6292a75ef04f5fa912a308c97ad8f804c8044fc94
```
