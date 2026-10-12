
所有前端 API 调用均在 `common/network.ts` 文件中进行，该文件使用 axios[^(34)](#c10.xhtml#ftn34) 发起 HTTP GET 或 POST 请求。当存在与信标铸造策略匹配的区块链交易时，将调用 Blockfrost webhook `updateTxStatus.ts`。该 webhook 配置为在三个**区块链确认**后触发。调用 Blockfrost webhook 时，它将更新具有相应交易 ID 的事件和兑换，并将其标记为已确认。

# Redis 数据库设置

在运行演示之前，必须在本地或使用云实例创建一个带有 JSON 堆栈的 Redis 数据库实例。

1.  访问 [https://redis.io/](https://redis.io/)
2.  登录或创建账户。
3.  创建一个 `$0` 订阅。
4.  创建一个新的 Redis Stack 数据库（包含 JSON 堆栈）。
5.  选择页面左侧的“Databases”导航链接。
6.  在“Endpoint”列下选择 `Connect`。
7.  然后选择 `Redis` `Client` 以获取您的凭证信息，如*[图 10.37](#c10.xhtml#fig10_37)*所示。

![](images/Figure-10.37.jpg)

**图 10.37：** Redis 数据库设置

# Blockfrost 设置

1.  登录 Blockfrost 仪表板并创建一个 webhook。
2.  输入您的应用程序 URL 作为端点 URL：
    `https://your.host.domain.name/api/updateTxStatus`
3.  设置所需的区块链确认数。
4.  输入信标铸造策略 ID 作为触发条件：
    `policy id = 421dacdd…e5ad68e76a6`
5.  创建另一个 webhook 并使用相同的端点 URL，但使用事件所有者的质押密钥作为发送者：
    `sender = stake_test1uqk6gt…6a5pj6p5qh6lc8v`
6.  复制 Auth Token 并将其添加到应用程序环境变量中：
    `export WEBHOOK_AUTH_TOKEN=8e81d5…24e0f5`

# 应用程序所有者公钥/私钥

您可以使用 init 文件夹中的 `generatePrivateKey.mjs` 实用程序来创建应用程序所有者的公钥和私钥。

```
$ cd chapter_10/helios/ticket-app
$ nvm use 18.17.0
$ npm install
$ export ENTROPY="put your 24 word seed phrase here"
$ node ./init/generatePriveKey.mjs
$ export OWNER_PRIVATE_KEY=383be…b632341a4e
$ export NEXT_PUBLIC_OWNER_PKH=61942b…653a7d3cdb0
```

# 演示

我们现在将运行应用程序，以在 Cardano preprod 网络上演示票务应用程序的功能。请确保在启动应用程序之前，以下 bash 环境变量已设置为正确的值：

```
$ cat ~/.bashrc
export NEXT_PUBLIC_HOST=localhost
export NEXT_PUBLIC_PORT=:3000
export NEXT_PUBLIC_PROTOCOL=http
export NEXT_PUBLIC_ENV=dev
export NEXT_PUBLIC_NETWORK=preprod
export REDIS_PASSWORD=CnitD9…9UsOAQ
export REDIS_HOST=redis-13…labs.com
export REDIS_PORT=13633
export BLOCKFROST_API_KEY="prepro…hE1aMi"
export BLOCKFROST_API="https://cardano-preprod.blockfrost.io/api/v0"
export WEBHOOK_AUTH_TOKEN=8e81d5…24e0f5
export OWNER_PRIVATE_KEY=889c4a…7cf5d5
export NEXT_PUBLIC_OWNER_PKH=18b022…9e3aeb
```

启动开发服务器：

```
$ source ~/.bashrc
$ npm run dev
```

使用浏览器访问外部端口以使用该应用程序。

# 初始启动

*[图 10.38](#c10.xhtml#fig10_38)* 显示了未创建任何兑换时 `Get Tickets` 页面的初始视图。要首先创建事件，用户需连接其钱包并选择 `My Events` 选项卡。

![](images/Figure-10.38.jpg)

**图 10.38：** 默认初始票务视图

# 连接钱包

当用户选择 `Connect` `Wallet` 时，会看到受支持且已安装的浏览器钱包列表，如*[图 10.39](#c10.xhtml#fig10_39)*所示。

![](images/Figure-10.39.jpg)

**图 10.39：** 连接钱包

# 我的事件

用户连接钱包后，可以前往 `My Events` 选项卡查看他们创建的事件列表。由于我们尚未创建任何事件，将看到一个空的事件列表，如*[图 10.40](#c10.xhtml#fig10_40)*所示。

![](images/Figure-10.40.jpg)

**图 10.40：** 我的事件

# 新建事件

当用户选择 `New Event` 按钮时，将看到一个允许输入事件详细信息的弹出窗口，如*[图 10.41](#c10.xhtml#fig10_41)*所示。选择 `Mint Tickets` 按钮时，分配的门票将被铸造并发送到门票持有地址。此外，请注意弹出窗口底部有一个查看智能合约的链接，如果用户想要独立验证智能合约。

![](images/Figure-10.41.jpg)

**图 10.41：** 新建事件

按下 `Mint Tickets` 按钮后，钱包会提示用户签署一笔交易以铸造活动门票。*[图 10.42](#c10.xhtml#fig10_42)* 显示了一批 1000 张门票成功铸造并发送到门票持有脚本地址。

![](images/Figure-10.42.jpg)

**图 10.42：** 分配的门票

# 开启兑换

接下来，通过开启兑换位置使门票可供出售，如*[图 10.43](#c10.xhtml#fig10_43)*所示。同时也会添加描述，并可为每个开启的兑换进行修改。用户可以从门票持有脚本中释放部分或全部门票并将其放入兑换位置。在本例中，我们将选择 700 张门票立即出售。

![](images/Figure-10.43.jpg)

**图 10.43：** 出售门票

# 获取门票

用户签署开启兑换交易后，门票将出现在 `Get Ticket` 屏幕上，如*[图 10.44](#c10.xhtml#fig10_44)*所示。如果用户仍连接其钱包，兑换将显示更新或关闭它的功能。这仅适用于拥有正确质押密钥的兑换位置所有者。

![](images/Figure-10.44.jpg)

**图 10.44：** 释放的门票

# 更新兑换

接下来，我们将在 `Get Tickets` 页面上更新兑换，将价格从 12 Ada 改为 15 Ada。更新交易成功，如*[图 10.45](#c10.xhtml#fig10_45)*所示。

![](images/Figure-10.45.jpg)

**图 10.45：** 更新兑换

# 购买门票

连接买家钱包后，我们选择 `Buy Tickets` 按钮，如*[图 10.46](#c10.xhtml#fig10_46)*所示。如果您的钱包需要，请记得启用买家钱包账户的 dApp 访问权限。

![](images/Figure-10.46.jpg)

**图 10.46：** 购买门票

我们将输入 4 张门票的数量，然后选择 `Buy Tickets` 按钮。签署购买交易后，将出现购买成功消息。由于我们购买了 4 张门票，兑换中当前可用的库存已变为 `696`，如*[图 10.47](#c10.xhtml#fig10_47)*所示。

![](images/Figure-10.47.jpg)

**图 10.47：** 购买门票

在*[图 10.48](#c10.xhtml#fig10_48)* 所示的钱包交易历史中，我们还可以看到执行了 2 个 Plutus 脚本。这使我们能够销毁 4 张已释放的门票并铸造 4 个门票代币和 4 个参考代币。这也可以在 Cardano 区块浏览器上查看[^(35)](#c10.xhtml#ftn35)。

![](images/Figure-10.48.jpg)

**图 10.48：** 购买门票钱包交易

# 我的门票

交易在区块链上确认后，用户可以前往 `My Tickets` 页面查看其钱包中的门票，如*[图 10.49](#c10.xhtml#fig10_49)*所示。由于用户拥有门票代币，他们也可以将其发送到另一个钱包或在 Cardano **DEX** 上挂单转售。临近活动时间，用户将打印门票以生成唯一的二维码，在活动时出示。二维码用于验证门票，验证后将标记为已使用。

![](images/Figure-10.49.jpg)

**图 10.49：** 我的门票

# 打印门票
