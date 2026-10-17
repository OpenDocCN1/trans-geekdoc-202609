
在交换函数内部，我们首先从图 10.31 获取`Context`。接下来，我们创建交换的总资产`totalAssetVal`。

以下是用于允许前端与后端应用组件（如`Redis DB`和`Blockfrost`）通信的 API 列表。

```bash
$ tree pages/api
├── closeSwap.ts
├── getAssetUtxo.ts
├── getEvent.ts
├── getEvents.ts
├── getFilterSwaps.ts
├── getTicketMetadataCIP25.ts
├── getTicketMetadataCIP68.ts
├── getTicketPkh.ts
├── getWalletInfo.ts
├── printTicket.ts
├── setBeacon.ts
├── setEvent.ts
├── setStakeKey.ts
├── setSwap.ts
├── signSubmitTx.ts
├── submitTx.ts
├── updateEvent.ts
├── updateSwap.ts
├── updateTxStatus.ts
└── verifyTicket.ts
```

所有的前端 API 调用均在`common/network.ts`文件中，该文件使用`axios`发送 HTTP GET 或 POST 请求。当存在匹配 beacon 铸造策略的区块链交易时，会调用 Blockfrost 的 webhook`updateTxStatus.ts`。该 webhook 被配置在三个`blockchain confirmations`之后触发。当 Blockfrost webhook 被调用时，它将更新具有相应交易 ID 的事件和交换，并将其标记为已确认。

## Redis DB 设置

在运行演示之前，必须在本地或使用云实例创建一个带有`JSON stack`的`Redis DB`实例。

1. 访问[`redis.io/`](https://redis.io/)

2. 登录或创建一个账户。

3. 创建`$0`订阅。

4. 创建一个新的`Redis Stack`数据库（包含`JSON stack`）。

5. 选择页面左侧的`Databases`导航链接。

6. 选择`Endpoint`列下的`Connect`。

7. 然后选择`Redis` `Client`以获取您的凭据信息，如图 10.37 所示。

![](img/Figure-10.37.jpg)

**图 10.37：** Redis DB 设置

## Blockfrost 设置

1. 登录 Blockfrost 仪表板并创建一个 webhook。

2. 输入您的应用程序 URL 作为`Endpoint URL`输入：

   `https://your.host.domain.name/api/updateTxStatus`

3. 设置所需的`blockchain confirmations`。

4. 输入`Beacon Minting Policy ID`作为触发条件：

   `policy id = 421dacdd…e5ad68e76a6`

5. 创建另一个 webhook 并使用相同的`Endpoint URL`，但使用事件所有者的质押密钥作为发送者：

   `sender = stake_test1uqk6gt…6a5pj6p5qh6lc8v`

6. 复制`Auth Token`并将其添加到应用程序环境变量：

   `export WEBHOOK_AUTH_TOKEN=8e81d5…240f5`

## 应用所有者公钥/私钥

你可以使用`init`文件夹中的`generatePrivateKey.mjs`工具创建应用所有者的公钥和私钥。

```bash
$ cd chapter_10/helios/ticket-app
$ nvm use 18.17.0
$ npm install
$ export ENTROPY="put your 24 word phrase here"
$ node ./init/generatePrivateKey.mjs
$ export OWNER_PRIVATE_KEY=383be…632341ae
$ export NEXT_PUBLIC_OWNER_PKH=61942b…653a7dcb0
```

## 演示

现在我们将运行应用程序，演示 Cardano preprod 网络上票务应用的功能。在启动应用程序之前，请确保已设置了以下 bash 环境变量：

```bash
$ cat ~/.bashrc
export NEXT_PUBLIC_HOST=localhost
export NEXT_PUBLIC_PORT=3000
export NEXT_PUBLIC_ENV=dev
export NEXT_PUBLIC_NETWORK=preprod
export REDIS_PASSWORD=password
export REDIS_HOST=127.0.0.1
export REDIS_PORT=6379
export BLOCKFST_API_KEY="https://blockfrost.io/api/v2"
export WEBHOOK_AUTH_TOKEN=8e81d5…240f5
export OWNER_PRIVATE_KEY=383be…632341ae
export NEXT_PUBLIC_OWNER_PKH=61942b…653a7dcb0
```

启动服务器：

```bash
$ source ~/.bashrc
$ npm run
```

使用浏览器并访问应用程序。

## 初始状态

图 10.38 显示尚未创建任何交换的`Get Tickets`页面。

# 连接钱包

图 10.39 显示连接钱包的`Connect`状态。

## 事件列表

图 10.40 显示尚未创建任何事件的`My Events`页面。

## 新事件

图 10.41 用户选择`New Event`按钮，将弹出详情窗口。

图 10.42 点击`Mint Tickets`按钮后，将显示铸造票据。

# 已分配交换

图 10.43 开启交换位置后，票据将可以出售。

## 获取票据

图 10.44 用户签名开启交换交易后，票据将出现在`Get Tickets`屏幕上。

图 10.48：购票钱包交易

# 我的门票

一旦交易在区块链上通过确认，用户就可以进入`My Tickets`（我的门票）页面查看钱包中的门票，如图 10.49 所示。

图 10.49：我的门票

# 打印门票

当用户选择`Print Ticket`（打印门票）按钮时，他们需要签署一个交易，用钱包的公钥哈希值来更新引用令牌。这样，我们就能确定用户在打印时确实拥有该门票。如果此交易成功，用户将看到一个 QR 代码，他们可以将其保存备用并在活动现场出示，如图 10.50 所示。

图 10.50：打印门票

# 验证门票

为了模拟在活动现场验证门票，`Print Ticket`弹出窗口有一个`Verify Ticket`（验证门票）按钮。选中后，它将检查 QR 代码签名和消息，以确认它们与数据库或引用令牌数据中的公钥哈希相匹配，如图 10.51 所示。

图 10.51：验证门票

## 关闭交换

演示的最后部分是关闭交换仓。因此，我们将钱包切换回活动所有者的钱包，并进入`My Events`（我的活动）页面，如图 10.52 所示。

图 10.52：已转换的门票

在`Get Tickets`（获取门票）页面上，使用活动所有者的钱包，交换交换将带有一个`Close Swap`（关闭交换）按钮，该按钮会将门票返回到持有脚本，如图 10.53 所示。

图 10.53：关闭交换

在`Close Swap`交易完成后，活动所有者将看到持有脚本中的门票数量为`996`，如图 10.54 所示。

图 10.54：持有的门票

## 搜索

用户还可以通过基于文本的搜索或根据时间或门票数量进行过滤来搜索开放的交换。在我们的演示中，现在有两个开放的交换，并将文本搜索`Jane Town`，它只会在一个交换中被找到，如图 10.55 所示。

图 10.55：搜索交换

一旦用户选择了`Apply Filter`（应用筛选）按钮，将仅显示匹配文本的门票交换，如图 10.56 所示。

图 10.56：搜索交换

# 浏览器钱包

门票令牌也可以直接在浏览器钱包中查看，如图 10.57 所示。

图 10.57：浏览器钱包令牌

## 区块链优势

目前，通过区块链可以确保用户在打印时确实拥有该门票。区块链的优势如下：

- 区块链数据的不可篡改性

- 门票的真实性

- 透明的分配

- 真实的转售验证

- 去中心化的门票销售

- 门票销售的透明度

- 门票令牌也可用于忠诚积分

- 避免第三方支付结算

## 结论

在本章中，我们回顾了复杂门票应用程序的实现细节。我们探讨了数据复制的概念以改进用户体验。我们利用了`ChakraUI`、`Next.js`、`Redis DB`和`Blockfrost`技术栈来创建完整的门票生命周期（铸造、出售、购买、兑换）。我们查看了智能合约开发中的一些挑战，如循环引用、检查输入输出以及区块确认。我们展示了如何通过 QR 代码证明门票的所有权。最后，我们通过一个端到端的演示结束了区块链应用程序的功能。在下一章中，我们将介绍测试技术以及如何编写安全可扩展的区块链应用程序。

## 要点

- 纯客户端区块链应用程序更符合区块链原理，并提供了良好的透明性和可审计性。

- `Redis DB`包含了应用程序使用的模型，是相关区块链数据的副本。

- `Redis DB`是一种内存数据库，允许极快的读取操作。

- 将区块链数据和元数据复制到应用程序数据库中可以提升用户体验并提供丰富的 UI 功能，如多维度筛选和搜索。

- `Next.js`中的全局状态通过`walletAPI`等对象传递给子 React 组件。

- UI 更改可以触发应用程序和数据库的变化，同时应用程序监听区块确认。

- `CIP-68`元数据标准为令牌名称添加十六进制前缀，以区分用户令牌和引用令牌。

- 交换数据包含`askedAssetValue`和`offeredAssetValue`。

- `askedAssetValue`指定请求的资产以及每种提供资产的价格。

- `offeredAssetValue`指定提供的资产以及当前锁定在交换中的资产数量。

- 在智能合约中评估截止日期条件时，需要时间有效性间隔。

- 使用交易 ID 和索引作为合约参数或令牌名称可以创建线程令牌。

- 当一个智能合约依赖于预知另一个智能合约的地址反之亦然时，就会发生循环引用。

- 当涉及涉及策略的事件时，webhook 会调用应用程序。

- 门票令牌一旦铸造并转换就是唯一的 Cardano NFT 原生令牌。

## 选择题

1. 纯客户端区块链应用程序的优势是什么？

   1. 响应速度更快

   2. 更容易审计和信任

   3. 更容易构建

   4. 不需要浏览器

## 2. 在区块链应用中复制区块链数据有什么优势？

1. 简化架构

2. 提高去中心化

3. 更好的用户体验

4. 更好的供应商支持

## 3. CIP-25 和 CIP-68 之间有什么区别？

1. 它们是相同的，都记录交易元数据

2. `CIP-25`使用`datum`来记录交易元数据

3. `CIP-68`使用交易元数据来记录 NFT 元数据

4. `CIP-68`使用带有`datum`的引用标记（reference token）来记录 NFT 元数据

## 4. 为什么需要时间有效区间？

1. Cardano 区块链只能确认某个时间范围对于特定交易有效

2. Cardano 区块链使用`Oracles`来获取时间

3. Cardano 区块链是非确定性的

4. 大约每 20 秒会创建一个`Cardano Block`

## 5. 什么时候会发生循环引用？

1. `Plutus Script`使用了`reference script`

2. Cardano 是确定性的，因此这不是一个有效的场景

3. 一个`Plutus script`引用另一个`Plutus script`反之亦然

4. 使用指针地址

## 答案

1. b

2. c

3. d

4. a

5. c

## 问题

1. 在保持可审计性和透明性的同时，提高用户体验的方法有哪些？

2. `CIP-0067`和`CIP-0068`之间有什么关系？

3. 如何计算特定 UTXO 的正确最小 lovelace？

4. 输入是如何排序的，为什么很难提前知道？

5. 是否有其他解决循环问题的方法？

## 核心术语

- **Blake2B**: 产生针对 64 位架构优化的加密哈希值。

- **Blockchain Confirmation**: Cardano 区块链网络对区块的接受。

- **DEX**: 去中心化交易所。

- **Functional Components**: 一种 React UI 组件。

- **Redis JSON full stack**: Redis 数据库中用于存储 JSON 对象的可选组件。

- **Time Interval**: 以毫秒为单位的开始结束时间。

- **Trustless Model**: 自审计能力，且不需要信任应用程序。

- `useEffect`: 根据页面挂载或变量变化触发动作。

- **Witness Signature**: 包含消息和签名，证明消息是由给定的公钥签名的

________________

[1] [`chakra-ui.com/`](https://chakra-ui.com/)

[2] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/WalletPopup.tsx`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/WalletPopup.tsx)

[3] [`github.com/cardano-foundation/cardano-connect-with-wallet`](https://github.com/cardano-foundation/cardano-connect-with-wallet)

[4] [`swr.vercel.app/`](https://swr.vercel.app/)

[5] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/components/SwapView.tsx`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/components/SwapView.tsx)

[6] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/components/SwapView.tsx`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/components/SwapView.tsx)

[7] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/api/getFilterSwaps.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/api/getFilterSwaps.ts)

[8] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/api/getFilterSwaps.ts`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/pages/api/getFilterSwaps.ts)

[9] [`github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/components/SwapView.tsx`](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_10/helios/ticket-app/components/SwapView.tsx)
