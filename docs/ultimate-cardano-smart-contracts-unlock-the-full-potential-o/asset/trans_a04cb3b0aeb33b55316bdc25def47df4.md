
`cardano-db-sync_1 | [db-sync-node:Info:65] [2024-05-08 10:15:15.00 UTC] Insert Babbage Block: epoch 0, slot 246, block 246, hash 888f504744cef550755ebd88a6cd6e9b5ad27f3ddcba11076ac8a00a9d04a258`

`cardano-db-sync_1 | [db-sync-node:Info:65] [2024-05-08 10:15:16.00 UTC] Insert Babbage Block: epoch 0, slot 247, block 247, hash be35c0eb241b0369af4a869480e9340a6c079fc25a3e8f96273fa633a22b4da9`

`…`

## 步骤 3：启动 Blockfrost-RYO

在另一个新的终端窗口中：

```
$ cd chapter_08/local-devnet/blockfrost-backend-ryo
$ nvm install 20.9.0
$ yarn install
$ yarn run dev-testnet
```

## 步骤 4：安装 Nami 本地开发网版本

打开另一个终端窗口并进入 Nami 目录。

```
$ cd chapter_08/local-devnet/nami
$ nvm use 20.9.0
$ npm install
$ npm run build
```

这将创建一个可加载到 Chrome 浏览器的构建目录。打开一个 Chrome 浏览器标签页的扩展窗口 `chrome://extensions/`，然后选择窗口左上角的“加载已解压的扩展程序”。接着导航到刚刚创建的 `nami/build` 目录并选择它。Nami 钱包现在应该已安装，你可以启动浏览器扩展。它首先会要求你创建一个新钱包和密码。你需要切换到测试网网络，方法是选择窗口右上角的头像。接下来，选择“设置”、“网络”，并从网络下拉菜单中选择“测试网”，如[图 8.12](#c08.xhtml#fig8_12)所示。此外，启用“自定义节点”并输入 `http://localhost:8090/api/submit/tx` 作为 URL。你可以通过查看 Nami 弹出窗口左下角的“测试网”标签来确认你位于正确的网络上。

![](images/Figure-8.12.jpg)

**图 8.12：** Nami 钱包开发网

**提示**：如果你使用解压方法安装了 Nami 钱包并关闭了浏览器，可能需要再次按照解压说明操作。如果你还重新创建了新的本地开发网网络，则需要创建一个新的 Nami 账户，或显式移除 Nami 钱包浏览器插件以清除缓存的 Nami 账户数据。

## 步骤 5：为钱包充值

打开 Nami 钱包后，选择“接收”按钮，并复制接收地址。然后，进入 `yaci-cli` 终端，输入 `topup` 命令，并粘贴接收地址和要发送的 Ada 数量，如[图 8.13](#c08.xhtml#fig8_13)所示。

![](images/Figure-8.13.jpg)

**图 8.13：** Yaci DevKit 充值

你可以在 Nami 钱包中确认已收到该金额，如[图 8.14](#c08.xhtml#fig8_14)所示。

![](images/Figure-8.14.jpg)

**图 8.14：** Nami 钱包充值

# 示例试运行

现在我们可以使用本地开发网试用之前的门票示例。使用另一个终端窗口，执行以下命令：

```
$ cd chapter_08/local-devnet/ticket
$ npm install
$ npm run dev
```

接下来，在本地开发网上铸造一些新门票，如[图 8.15](#c08.xhtml#fig8_15)所示。

![](images/Figure-8.15.jpg)

**图 8.15：** 在本地开发网上铸造

我们现在可以在本地 Yaci DevKit 区块链浏览器的“交易”标签页下查看交易详情，如[图 8.16](#c08.xhtml#fig8_16)所示。

![](images/Figure-8.16.jpg)

**图 8.16：** 本地开发网浏览器交易视图

我们还可以查看智能合约详情，包括[图 8.17](#c08.xhtml#fig8_17)中的赎回值。

![](images/Figure-8.17.jpg)

**图 8.17：** 本地开发网浏览器合约视图

# 附加资源

存在其他查询和响应 Cardano 区块链数据的方法和解决方案。[表 8.1](#c08.xhtml#tab8_1) 概述了更流行的 Cardano 工具选项。

| 名称 | 描述 | 技术栈 |
| --- | --- | --- |
| DB Sync[^29] | Cardano 区块链索引器 | Haskell, Postgres SQL DB |
| Kupo[^30] | Cardano 区块链索引器 | Haskell |
| Ogmios[^31] | Cardano 节点的轻量级接口 | Haskell |
| Yaci Store[^32] | Cardano 区块链索引器和实时监控 | Java, RDBMS 或 Redis/MongoDB |
| Carp[^33] | Cardano 区块链索引器 | Rust, Typescript, Oura, Cardano Multiplatform Lib, PostgresDB |
| Scrolls[^34] | 区块链爬虫、聚合器，具有实时更新 | Rust, Redis |
| Ouroboros Network JS[^35] | 使用 TypeScript 编写的 Ouroboros 网络库，配合 Node.js 流进行链同步、交易监控和提交 | Typescript |
| GraphQL[^36] | 面向 Cardano 的跨平台、类型化且可查询的 API | Typescript, Cardano DB Sync |
| Oura[^37] | 实时区块链监控和警报 | Rust, Pallas[^38] |

**表 8.1：** 区块链工具

# 结论

本章概述了可供开发者使用的一些更流行的 Cardano 链下提供商和工具。首先，我们探讨了 Blockfrost、Maestro、Koios 和 Dandelion 等 Cardano 区块链提供商。接下来，我们了解了一些 Cardano 基础设施组件和工具，如 Cardano 节点、Ogmios 和 Kupo，以及如何使用 Demeter.run 进行配置。我们还学习了如何使用 Yaci DevKit 部署本地开发网，以测试链上和链下代码。最后，为了完整性，我们提供了最流行工具组件的概述。现在我们已准备好进入下一章，利用我们对链下工具的知识构建一个完整的端到端区块链应用程序。

# 要点回顾

* 多个区块链 API 服务提供商和工具选项有助于促进去中心化，并避免生态系统中的单点故障。
* Blockfrost 是最早的 Cardano API 服务提供商之一，也是 Cardano 生态系统中使用最广泛的 API 服务提供商。
* Maestro 最近推出了其 API 的新版本，具有低延迟、高性能链索引查询、交易状态管理和优化的交易提交功能。
* Koios 是一个去中心化的分布式平台，提供 Cardano 区块链 API 服务。
* 链下工具组件用于查询、响应或提交区块链数据。
* Cardano 节点可以从 Docker 容器、静态二进制文件运行，或通过编译源代码运行。
* Demeter.run 拥有 Cardano 节点等资源，可运行并附加到工作区。
* `cardano-cli` 是 Cardano 的瑞士军刀，具有多种用途和功能。
* Ogmios 之所以流行，是因为它使用 REST API 或 Web RPC 接口暴露 Cardano 节点功能。
* Kupo 也是一个流行的开源 Cardano 区块链索引器，能快速捕获区块链数据并保存到内存数据库中。
* Lucid 内置了 Kupo 和 Ogmios 提供商，可连接到 Kupo 和 Ogmios 实例以进行区块链数据查询和交易提交。
* Yaci DevKit 可以设置类似于 Ethereum 的 Hardhat 的本地开发网。

# 多项选择题

1. 为什么需要区块链工具？
    1. 用于链上验证器逻辑
    2. 用于 Cardano 账本
    3. 启动/停止 Cardano 区块链所需
    4. 高效访问区块链数据

2. 使用 `cardano-cli` 无法实现什么功能？
    1. 启动/停止 Cardano 节点
    2. 提交交易
    3. 查询 Cardano 区块链顶端
    4. 查看 UTXO 内容

3. 如何访问 Ogmios？
    1. 节点套接字
    2. SQL 查询
    3. HTTP REST API
    4. HTTP REST API 或 RPC Web Socket

4. Yaci DevKit 的一些功能是什么？
    1. 区块链浏览器、Kupo 和 Ogmios API
    2. 代币注册表
    3. 主网网络
    4. GraphQL

5. 哪个工具可以提交交易？

