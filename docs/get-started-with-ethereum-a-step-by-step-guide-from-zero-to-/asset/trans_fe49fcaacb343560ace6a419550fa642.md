

uint80 roundID,

int price,

uint startedAt,

uint timeStamp,

uint80 answeredInRound,

) = priceFeed.latestRoundDate();

return price;

}

}

创建迁移

创建迁移文件

| TERMINAL |

| --- |

| $ touch migrations/2\_deploy\_contracts.sol |

编写代码以部署“PriceConsumer”智能合约

| 2\_deploy\_contracts.js |

| --- |

| 1 2 3 4 5 |

```javascript
const PriceConsumer = artifacts.require("PriceConsumer");

module.exports = function (deployer) {
  deployer.deploy(PriceConsumer);
};
```

设置 Infura 项目

访问 infura.io

进入控制面板

点击“ethereum”

点击“create a project”

定义项目名称

您可以连接到不同的测试网以及主网

复制项目 ID

保存更改

配置钱包

安装文件系统“fs”包

| TERMINAL |

| --- |

| $ npm install fs |

安装钱包提供程序“hdwallet”包

| TERMINAL |

| --- |

| $ npm install @truffle/hdwallet-provider@1.2.3 |

打开 `truffle-config.js` 文件

取消注释 HDWalletProvider 代码部分

| truffle-config.js |

| --- |

| 21 22 23 24 25 |

```javascript
const HDWalletProvider = require('@truffle/hdwallet-provider');

const infuraKey = 'fj4jll3k.....';

const fs = require('fs');

const mnemonic = fs.readFileSync(".secret").toString().trim();
```

将 Infura 项目 ID 作为变量 `infuraKey` 的值粘贴进去

配置网络

取消注释“ropsten”网络部分

将“ropsten”更改为“kovan”

将“ropsten” Infura URL 更改为“kovan”

将“YOU-PROJECT-ID”更改为“`${infuraKey}`”

将 `network_id` 更改为 42

| truffle-config.js |

| --- |

| 60 61 62 63 64 65 66 67 |

```javascript
kovan: {
  provider: () => new HDWalletProvider(mnemonic, `https://kovan.infura.io/v3/${infuraKey}`),
  network_id: 42,
  gas: 5500000,
  confirmations: 2,
  timeoutBlocks: 200,
  skipDryRun: true
},
```

配置 Solidity 编译器

取消注释“compilers”部分

将版本更改为“0.8.0”

| truffle-config.js |

| --- |

| 93 94 95 96 97 98 99 100 101 102 103 104 105 |

```javascript
compilers: {
  solc: {
    version: "0.8.0",
    docker: true,
    settings: {
      optimizer: {
        enabled: false,
        runs: 200
      },
      evmVersion: "byzantinum"
    }
  }
},
```

配置私钥

创建密钥文件

| TERMINAL |

| --- |

| $ touch .secret |

在浏览器中打开连接到 Infura 网络的 MetaMask 钱包

点击您的账户

点击“settings”

点击“security & privacy”

点击“reveal seed phrase”

输入钱包密码以继续

复制私钥

粘贴钱包助记词密钥

编译智能合约

使用 Truffle 编译合约

| TERMINAL |

| --- |

| $ truffle compile |

部署智能合约

使用 Truffle 将合约部署到 Kovan 网络

| TERMINAL |

| --- |

| $ truffle migrate --network kovan |

等待合约部署完成，并在区块链上确认交易

确认您的合约地址

从智能合约获取价格信息

使用 Truffle 控制台实例化合约

| TERMINAL |

| --- |

| $ truffle console --network kovan |

`truffle(kovan) let instance = await PriceConsumer.deployed()`

调用方法“getThePrice”

| TERMINAL |

| --- |

| `truffle(kovan) let price = await instance.getThePrice()` |

将结果输出为数字

| TERMINAL |

| --- |

| `truffle(kovan) price.toNumber()` |

265499339990

就是这样，您刚刚创建了一个智能合约并使用了 Chainlink 价格预言机！

Nethereum 使用 Nethereum 获取以太币余额

Nethereum 是一个开源的 .NET 集成库，用于以太坊，简化了智能合约管理以及与以太坊节点（无论是公共还是私有）的交互。[Nethereum](https://nethereum.com) [在 YouTube 上观看](https://www.google.com/url?q=https://youtu.be/xIYCv15MpbA&sa=D&source=editors&ust=1624824293642000&usg=AOvVaw2qydc0iQhOz5k4yHDhbKTs)

| 预计时间 |

| --- |

| 5 分钟 |

创建项目

打开终端并点击“新建终端”

创建一个新的 .NET 控制台项目

| TERMINAL |

| --- |

| $ dotnet new console -o sample |

进入项目根目录

| TERMINAL |

| --- |

| $ cd sample |

安装 Web3

安装 Nethereum Web3 包

| TERMINAL |

| --- |

| $ dotnet add package Nethereum.Web3 |

还原所有项目包

| TERMINAL |

| --- |

| $ dotnet restore |

创建方法

打开“Program.cs”文件

添加线程和 Web3 的引用

添加一个新方法来获取账户余额

实例化一个新的 Web3 对象

进入您的 Infura 项目设置

选择“Ropsten”网络

复制 Ropsten HTTPS 端点

使用此端点作为 Web3 对象构造函数的参数

从 Web3 获取余额

使用您的钱包公共地址作为参数

编写代码以 Wei 为单位输出余额

将 Wei 余额转换为以太币

编写代码以以太币为单位输出余额

现在更改主方法以调用 `GetAccountBalance()`

| Program.cs |

| --- |

| 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 |

```csharp
using System;

using System.Threading.Tasks;

using Nethereum.Web3;

namespace NethereumSample

{

    class Program

    {

        static void Main(string[] args)

        {

            GetAccountBalance().Wait();

            Console.ReadLine();

        }

        static async Task GetAccountBalance()

        {

            var web3 = new Web3("https://ropsten.infura.io/v3/39180531508b4b659780ef7a36426a86");

            var balance = await web3.Eth.GetBalance.SendRequestAsync("0x03d1b3162DBFaB4A175038eAa4EA4b39423d5A6F");

            Console.WriteLine($"Balance in Wei: {balance.Value}");

            var etherAmount = Web3.Convert.FromWei(balance.Value);

            Console.WriteLine($"Balance in Ether: {etherAmount}");

        }

    }

}
```

获取余额

构建项目

| TERMINAL |

| --- |

| $ dotnet build |

运行项目

| TERMINAL |

| --- |

| $ dotnet run |

