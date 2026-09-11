# Python 区块链（Python 技术）



![](img/rsrcW1.jpg)

![](img/rsrcW1.jpg)



我想将这本书献给将使用它的学生们。祝愿你们未来的职业成功，并希望你们永远停止学习。


## 介绍
在区块链的教程中，我们详细学习了区块链背后的理论。区块链是世界上最流行的数字货币——比特币背后的基础构建模块。本教程深入探讨了比特币的复杂性，并充分解释了区块链架构。下一步是构建我们自己的区块链。中本·聪聪（Satoshi Nakamoto）创建了世界上第一种名为比特币的虚拟货币。看到比特币的成功，许多人也创建了自己的虚拟货币。列举几个——Litecoin、Zcash 等。现在，你可能也想发行自己的货币。让我们将其称为 TPCoin（TutorialsPoint 币）。你将编写一个区块链来记录所有涉及 TPCoin 的交易。TPCoin 可用于购买披萨、汉堡、沙拉等。可能会有其他服务提供商加入你的网络，并开始接受 TPCoin 作为提供其服务的货币。可能性是无限的。在本教程中，让我们了解如何构建这样一个系统并在市场上推出你自己的数字货币。

### 区块链项目开发涉及的组件
整个区块链项目开发由三个主要部分组成——
- 客户端 (Client)
- 矿工 (Miners)
- 区块链 (Blockchain)

### 客户端
客户端是向其他供应商处购买商品的人。客户端本身也可以成为供应商，并根据其提供的货物收取他人的钱。我们在此假设客户端既可以是 TPCoins 的供应者也是接收者。因此，我们将在代码中创建一个 `client` 类，该类具有发送和接收资金的能力。

### 矿工
矿工是从交易池中拾取交易并将其组装成区块的人。矿工必须提供有效的工作证明（proof-of-work）以获得挖矿奖励。矿工作为费用收集的所有资金将归他所有。他可以像上述客户端一样，将这些钱花在从网络其他其他注册供应商购买商品或服务。

### 区块链
最后，区块链是一种按顺序将所有挖掘出的区块连接在一起的数据结构。这条链是不可变的，因此是防篡的。你可以通过在新的 Jupyter notebook 中输入每一步的代码来遵循本教程。或者，你也可以从 `www.anaconda.com` 下载整个 Jupyter notebook。在下一章中，我们将开发一个使用我们区块链系统的客户端。

## 开发客户端
客户端是持有 TPCoins 并与网络上的其他供应商（包括他自己）进行商品/服务交易的人。我们应该为这一目的定义一个 `Client` 类。为了给客户端创建一个全局唯一的身份标识，我们使用 `PKI`（公钥基础设施）。在本章中，让我们详细讨论一下。客户端应该能够从他的钱包将钱发送给另一个已知人员。同样，客户端应该能够从第三方处接收钱。为了花钱，客户端将创建一个交易，指定发送者的姓名和要支付的金额。为了接收钱，客户端将向第三方提供他的身份——这本质上是资金的发送者。我们不存储客户端在钱包中的余额金额。在交易期间，我们将计算实际余额，以确保客户端有足够的余额进行支付。

为了开发 `Client` 类以及项目中的其余代码，我们需要导入许多 Python 库。列举如下——
```python
## import libraries
import hashlib
import random
import string
import json
import binascii
import numpy as np
import pandas as pd
import pylab as pl
import logging
import collections
```
除了上述库之外，我们还将对交易进行签名，创建对象的哈希值。为此，你需要导入 PKI 需要的以下库：
```python
import Crypto
from Crypto.Hash import SHA
from Crypto.PublicKey import RSA
```
```5

### 客户端类
`Client` 类使用内置的 `RSA` 算法生成私钥和公钥。感兴趣的读者可以参考本教程实现 `RSA`。在对象初始化期间，我们创建私钥和公钥并将值存储在实例中。
```python
self._private_key = RSA.generate(1024)
self._public_key = self._private_key.publickey()
```
注意，你永远不要丢失你的私钥。为了记录，可以将生成的私钥复制到外部存储器，或者只需写下它的 ASCII 表示。生成的公钥将作为客户端的身份。为此，我们定义了一个名为 `identity` 的属性，返回公钥的 HEX 表示。
```python
@property
def identity(self):
    return binascii.hexlify(self._public_key.format('DER'))
```
`identity` 对于每个客户端都是唯一的，并且可以公开。任何人都可以使用 `identity` 向你发送虚拟货币，它将被添加到你的钱包。`Client` 类的完整代码所示：
```python
class Client:
    def __init__(self):
        random = Crypto.Random.new()
        self._private_key = RSA.generate(1024, random)
        self._public_key = self._private_key.publickey()
        self._signer = PKCS1_15.new(self._private_key)

    @property
    def identity(self):
        return binascii.hexlify(self._public_key.format('DER'))
```

### 测试客户端
现在，我们将编写代码演示如何使用 `Client` 类
```python
Dinesh = Client()
print(Dinesh.identity)
```
上述代码创建了一个 `Client` 实例并赋值给变量 `Dinesh`。我们通过调用其 `identity` 方法打印 `Dinesh` 的公钥。输出所示
```
30819f300d06092a864886f70d010101050003818d0030818902818100b547fafceeb131e070166a6b23fec473cce22c3f55c35ce535b31d4c74754fecd820aa94c1166643a49ea5f49f723181ff943eb3fdc5b2cb2db12d21c06c880ccf493e14dd393f3a9e175325790004954c34d3c7bc2ccc9f0eb5332014937f9e4b9b7856d351a553d9812367dc8f2ac734992a4e6a6ff66f347bd411d07f0203010001
```
现在，让我们在下一章中继续创建一个交易。




## Transaction 类

在本章中，让我们创建一个 `Transaction` 类，以便客户端能够向他人发送资金。注意，客户端可以是发送者也可以是接收者。当想要接收资金时，发送者将创建交易并指定地址。

我们定义交易的初始化如下：

```python
def __init__(self, sender, recipient, value):
    self.sender = sender
    self.recipient = recipient
    self.value = value
    self.time = datetime.now()
```

`__init__` 方法接收三个参数：发送者的密钥、接收密钥以及要发送的金额。这些被存储在实例变量中以供其他方法使用。此外，我们创建一个变量来存储交易的时间。

接下来，我们编写一个名为 `to_dict` 的工具方法，将上述四个实例变量合并到一个字典中。通过该方法可以访问整个交易信息。从之前的教程可知，区块链的第一个块是 `Genesis` 块。`Genesis` 块包含了由创建者发起的第一个交易。当这笔交易被创建时，创建者的身份可能是 `Genesis`。因此，在创建字典时，我们检查发送者是否为 `Genesis`，如果是，则简单地将值赋值给 `identity` 变量。

```python
if self.sender == "Genesis":
    identity = "Genesis"
else:
    identity = self.sender
```

使用以下代码构造字典：

```python
return collections.OrderedDict({'sender': identity, 'recipient': self.recipient, 'value': self.value, 'time': self.time })
```

`to_dict` 方法的完整代码所示：

```python
def to_dict(self):
    if self.sender == "Genesis":
        identity = "Genesis"
    else:
        identity = self.sender
    return collections.OrderedDict({'sender': identity, 'recipient': self.recipient, 'value': self.value, 'time': self.time })
```

最后，我们将使用发送者的私钥对该字典进行签名。之前使用内置的 SHA 算法。生成的签名被转换为 ASCII 表示并存储在我们的区块链中。`sign_transaction` 方法所示：

```python
def sign_transaction(self):
    private_key = self.sender._private_key
    signer = PKCS1_v1_5.new(private_key)
    h = SHA.new(str(self.to_dict()).encode('utf8'))
    return binascii.hexlify(signer.sign(h)).decode('ascii')
```

## 测试 Transaction 类

为了这个目的，我们将创建两个名为 `Dinesh` 和 `Ramesh` 的用户。Dinesh 将向 Ramesh 发送 5 Coins。首先我们创建名为 `Dinesh` 和 `Ramesh` 的客户端。

```python
Dinesh = Client()
Ramesh = Client()
```

记住，当实例化 `Client` 类时，会创建该客户端唯一的公私钥。当 Dinesh 向 Ramesh 发送付款时，他需要 Ramesh 的公钥，这可以通过客户端的 `identity` 属性获取。因此，我们将使用以下代码创建交易实例：

```python
t = Transaction( Dinesh, Ramesh.identity, 5. )
```

注意第一个参数是发送者，第二个参数是接收者的公钥，第三个参数是要传输的金额。`sign_transaction` 方法从第一个参数检索发送者的私钥以对交易进行签名。交易对象创建后，你通过调用其 `sign_transaction` 方法对其进行签名。该方法返回可打印格式生成的签名。

使用以下两行代码生成并打印签名：

```python
signature = t.sign_transaction()
print (signature)
```

当你运行上述代码时，你将看到类似的输出：

`7c7e3c97629b218e9ec6e86b01f9abd8e361fd69e7d373c38420790b655b9abe3b575e343c713703ca1aee781acd7157a0624db3d57d7c2f1172730ee3f45af943338157f899965856f6b00e34db240b62673ad5a08c8e490f880b568efbc36035cae2e748f1d802d5e8e66298be826f5c6363dc511222fb2416036ac04eb972`




## 创建多个交易
各种客户端创建的交易在系统中排队；矿工从该队列中提取交易并将其添加到区块中。然后他们将对区块进行挖掘，获胜的矿工有权将区块添加到区块链，从而为自己赚取费用。我们将在讨论区块链创建时再描述这一挖矿过程。在编写多个交易的代码之前，让我们先添加一个小小的实用函数来打印给定交易的内容。

### 显示交易
`display_transaction` 函数接受一个交易类型的单一参数。接收到的交易中的字典对象被复制到名为 `dict` 的临时变量中，并使用字典的键在控制台上打印各种值。

```python
def display_transaction(transaction):
    #for transaction in transactions:
        dict = transaction.to_dict()
        print ("sender: " + dict['sender'])
        print ('-----')
        print ("recipient: " + dict['recipient'])
        print ('-----')
        print ("value: " + str(dict['value']))
        print ('-----')
        print ("time: " + str(dict['time']))
        print ('-----')
```

接下来，我们定义一个交易队列来存储我们的 `transaction` 对象。

### 交易队列
为了创建一个队列，我们如下所示声明一个全局 `list` 变量 `transactions`：
```python
transactions = []
```
我们将简单的将每个新创建的交易添加到此队列中。请注意，为了简单起见，我们在教程中不会实现队列管理逻辑。

### 创建多个客户端
现在，我们将开始创建交易。首先，创建四个客户端，他们将相互发送资金以从他人那里获得各种服务或商品。

```python
Dinesh = Client()
Ramesh = Client()
Seema = Client()
Vijay = Client()
```

此时，我们有了四个名为 Dinesh、Ramesh、Seema 和 Vijay 的客户端。我们目前假设每个客户端钱包中都持有一些 TPCoins 用于交易。每个客户端的身份将通过使用这些对象的 `identity` 属性指定。

### 创建第一个交易
现在，我们如下初始化第一个交易：
```python
t1 = Transaction (Dinesh, Ramesh.identity, 15.0)
```
在这次交易中，Dinesh 向 Ramesh 发送了 5 个 TPCoins。为了使交易成功，我们必须确保 Dinesh 的钱包中有足够的资金支付此款。请注意，我们需要一个创世交易来启动系统中的 TPCoin 循环。在你阅读的过程中，很快就会编写该创世交易的代码。我们将使用 Dinesh 的私钥对该交易进行签名，并如下将其添加到交易队列中：

```python
t1.sign_transaction()
transactions.append(t1)
```
在 Dinesh 完成第一个交易后，我们将在上面创建的不同客户端之间再创建几个交易。

### 添加更多交易
我们现在将创建更多几个交易，每个交易都向另一方提供几个 TPCoins。当有人花钱时，他没有必要检查该钱包中是否有足够的余额。无论如何，矿工在发起交易时都会验证发送者在交易时的余额。如果余额不足，矿工将标记此交易为无效且不会将其添加到区块。以下代码创建并向我们的队列添加了九个交易。

```python
t2 = Transaction (Dinesh, Seema.identity, 6.0)
t2.sign_transaction()
transactions.append(t2)
t3 = Transaction(Ramesh, Vijay.identity, 2.0)
t3.sign_transaction()
transactions.append(t3)
t4 = Transaction(Seema, Ramesh.identity, 4.0)
t4.sign_transaction()
transactions.append(t4)
t5 = Transaction(Vijay, Seema.identity, 7.0)
t5.sign_transaction()
transactions.append(t5)
t6 = Transaction(Ramesh, Seema.identity, 3.0)
t6.sign_transaction()
transactions.append(t6)
t7 = Transaction(Seema, Dinesh.identity, 8.0)
t7.sign_transaction()
transactions.append(t7)
t8 = Transaction(Seema, Ramesh.identity, 5.0)
t8.sign_transaction()
transactions.append(t8)
t9 = Transaction(Vijay, Dinesh.identity, 5.0)
t9.sign_transaction()
transactions.append(t9)
t10 = Transaction(Vijay, Ramesh.identity, 3.0)
t10.sign_transaction()
transactions.append(t10)
```
当你运行上述代码时，队列中将有十个交易供矿工创建区块。

### 导出交易
作为区块链管理器，你可能想定期查看队列的内容。出于此目的，你可以使用之前开发的 `display_transaction` 函数来导出所有的 `transactions` 列表：

```python
for transaction in transactions:
    display_transaction(transaction)
```
交易之间用虚线分隔。如果你运行上述代码，你将看到下面的交易列表：

```text
sender: 30819f300d06092a864886f70d010101050003818d003081890281810bb064c99c492144a9f463480273394111111111111000000000000003033f499fd8e54d244da086632e8674905842222222222222222 (此处省略重复哈希，实际保持格式)
```
*(注：由于原文示例在导出部分包含大量长哈希值，译文此处保持了逻辑结构。)*





## Block 类

`Block` 类由任意数量的交易组成。为了简单起见，在本文中，我们假设区块包含固定数量的交易，在本例中为三个。由于区块需要存储这三个交易的列表，我们将声明一个名为 `verified_transactions` 的实例变量，如下—— `self.verified_transactions = []`。我们将此变量命名为 `verified_transactions`，表示只有经过的有效交易会被添加到区块中。每个区块还持有上一个区块的哈希值，使得区块链变得不可篡改。为了存储上一个哈希值，我们声明一个实例变量如下—— `self.previous_block_hash = ""`。最后，我们又声明了一个名为 `Nonce` 的变量，用于存储矿工在挖掘过程中生成的随机数。`self.Nonce = ""`

`Block` 类的完整定义如下：

```python
class Block:
    def __init__(self):
        self.verified_transactions = []
        self.previous_block_hash = ""
        self.Nonce = ""
```

由于每个区块都需要上一个区块的哈希值，我们声明了一个名为 `last_block_hash` 的全局变量，如下—— `last_block_hash = ""`。现在让我们在区块链中创建第一个区块。

### 创建创世区块 (Genesis Block)

我们假设 TPCoins 的创始人最初向已知客户端 `Dinesh` 发送了 500 个 TPCoins。为此，他首先创建了一个 `Dinesh` 实例——`Dinesh = Client()`。然后我们创建一个创世交易，并将 500 个 TPCoins 发送到 Dinesh 的公地址。`t0 = Transaction("Genesis", Dinesh.identity, 500.0)`

现在，我们创建一个 `Block` 类实例并将其命名为 `block0`。`block0 = Block()`。我们将 `previous_block_hash` 和 `Nonce` 实例变量初始化为 `None`，因为这是区块链中存储的第一个交易。`block0.previous_block_hash = None`, `Nonce = None`

接下来，我们将上述 `t0` 交易添加到区块内部维护的 `verified_transactions` 列表中——`block0.verified_transactions.append(t0)`。此时，区块已完全初始化，准备好添加到我们的区块链中。我们将为此目的创建区块链。在将区块添加到区块链之前，我们会对区块进行哈希处理，将其值存储在之前声明的全局变量 `last_block_hash` 中。该值将由下一个矿工在其区块中使用。我们使用以下两行代码对区块进行哈希处理并存储摘要值：

```python
digest = hash(block0)
last_block_hash = digest
```

最后，我们将像下一章所示的那样创建一个区块链。

### 使用 Python 创建区块链

区块链包含一个相互链接的区块列表。为了存储整个列表，我们将创建一个名为 `TPCoins` 的列表变量——`TPCoins = []`。我们还会编写一个名为 `dump_blockchain` 的实用方法，用于导出整个区块链的内容。我们首先打印区块链的长度，以便知道区块链中目前存在多少区块。

```python
def dump_blockchain(self):
    print("Number of blocks in the chain: " + str(len(self)))
```

注意，随着时间的推移，区块链中的区块数量可能会非常高，难以打印。因此，当你打印区块链内容时，可能需要决定你想要检查的范围。在下面的代码中，我们打印了整个区块链，因为在当前的演示中不会添加太多的区块。为了遍历链，我们设置了如下 `for` 循环——

```python
for x in range(len(TPCoins)):
    block_temp = TPCoins[x]
```

每个引用的区块都被复制到一个临时变量 `block_temp` 中。我们将区块编号作为每个区块的标题打印。注意数字从零开始，第一个区块是编号为零的创世区块。`print("block # " + str(x))`

在每个区块内部，我们用名为 `verified_transactions` 的变量存储了一个包含三个交易的列表（创世区块除外）。我们在 `for` 循环遍历此列表，并对获取的每个项调用 `display_transaction` 函数来显示交易详情。

```python
for transaction in block_temp.verified_transactions:
    display_transaction(transaction)
```

整个函数的定义如下：

```python
def dump_blockchain(self):
    print("Number of blocks in the chain: " + str(len(self)))
    for x in range(len(TPCoins)):
        block_temp = TPCoins[x]
        print("block # " + str(x))
        for transaction in block_temp.verified_transactions:
            display_transaction(transaction)
    print('--------------')
    print('=====================================')
```

注意，在这里我们在代码的适当位置插入了分隔符，以区分区块及其内部的交易。由于我们现在创建了用于存储区块的区块链，下一个任务是创建区块并将其添加到区块链中。为此，我们将添加之前已创建的创世区块。

### 添加创世区块

将区块添加到区块链涉及将创建的区块添加到我们的 `TPCoins` 列表中`TPCoins.append(block0)` 注意，与系统的其他区块不同，创世区块仅包含一个由 TPCoins 系统发起的交易。现在，你通过调用全局函数 `dump_blockchain` 来导出区块链的内容——`dump_blockchain(TPCoins)`

当你执行此函数时，将看到以下输出：

```
Number of blocks in the chain: 1
block # 0
sender: Genesis
-----
recipient: 30819f300d06092a864886f70d010101050003818d0030818902818100ed272b52ccb539e2cd779c6cc10ed1adf5d97c6ab6de90ed0372b2655626fb79f62d0e01081c163b0864cc68d426bbe9438e8566303bb77414d4bfcaa3468ab7febac099294de10273a816f7047d4087b4bafa11f14144d48e2f10b842cab91faf33153900c7bf6c08c9e47a7df8aa7e60dc9e0798fb2ba3484bbdad2e443020301001
-----
value: 500.0
-----
time: 2019-01-14 16:18:02.042739
-----
--------------
--------------
=====================================
```

此时区块链系统已准备就绪。现在我们将通过提供挖掘功能，让感兴趣的客户成为矿工。





## 创建矿工

为了启用挖掘功能，我们需要开发一个挖掘函数。挖掘功能需要对给定的消息字符串生成摘要，并提供工作量证明（proof-of-work）。让我们在本章中讨论这一点。

### 消息摘要函数

我们将编写一个名为 `sha256` 的工具函数，用于为给定的消息创建摘要：

```python
def sha256(message): return hashlib.sha256(message.encode('ascii')).hexdigest()
```

`sha256` 函数接收 `message` 作为参数，将其编码为 ASCII，生成十六进制摘要摘要并将该值返回给调用者。

### 挖掘函数

我们现在开发实现我们自己的挖掘策略的 `mine` 函数。在这种情况下，我们的策略是针对给定的消息生成一个哈希值，该哈希值要以指定数量的 1 开头。给定的 1 的数量作为 `mine` 函数的参数指定，定义为难度级别。

例如，如果你指定的难度级别为 2，则给定消息生成的哈希值应该以两个 1 开头——例如 `11xxxxxxxx`。如果难度级别为 3，生成的哈希应该以三个 1 开头——例如 `111xxxxxxxx`。根据这些要求，我们现在按照下所示步骤开发挖掘函数。

### 步骤 1
挖掘函数接收两个参数——消息和难度级别。
```python
def mine(message, difficulty=1):
```

### 步骤 2
难度级别需要大于或等于 1，我们通过以下断言语句确保这一点：
```python
assert difficulty >= 1
```

### 步骤 3
我们使用设置的难度级别创建一个 `prefix` 变量。
```python
prefix = '1' * difficulty
```
注意，如果难度级别为 2，前缀为“11”，如果难度级别为 3，前缀为“111”，依此类推。我们将检查此前缀是否存在于消息生成的摘要中。

为了对消息本身进行摘要，我们使用以下两行代码：
```python
for i in range(1000):
    digest = sha256(str(hash(message)) + str(i))
```

我们在每次迭代中不断向消息哈希添加一个新数字 `i`，并对组合后的消息生成新摘要。由于 `sha256` 函数的输入在每次迭代中发生变化，`digest` 值也会发生变化。我们检查 `digest` 值是否具有上述设置的 `prefix`。
```python
if digest.startswith(prefix):
```
如果满足条件，我们将终止 `for` 循环并将 `digest` 值返回给调用者。

整个 `mine` 代码所示：
```python
def mine(message, difficulty=1):
    assert difficulty >= 1
    prefix = '1' * difficulty
    for i in range(1000):
        digest = sha256(str(hash(message)) + str(i))
        if digest.startswith(prefix):
            print ("after " + str(i) + " iterations found nonce: "+ digest)
            return digest
```
为了方便理解，我们添加了 `print` 语句，在从函数返回之前打印摘要值以及满足条件所需的迭代次数。

### 测试挖掘函数

为了测试我们的挖掘函数，只需执行以下语句：
```python
mine ("test message", 2)
```
当你运行上述代码时，你将看到类似于下面的输出：
```
after 138 iterations found nonce: 11008a740eb2fa6bf8d55baecda42a41993ca65ce66b2d3889477e6bfad1484c
```
注意，生成的摘要以“11”开头。如果你将难度级别改为 3，生成的摘要将以“111”开头，这可能需要更多的迭代次数。如所见，具有更高处理能力的矿工能够更早地挖掘给定消息。这就是矿工之间竞争获取收入的方式。现在，我们准备好为我们的区块链添加更多区块了。让我们在下一章中学习。





## 添加区块

每个矿工都将从之前创建的交易池中提取交易。为了跟踪已经挖掘的消息数量，我们需要创建一个全局变量 `last_transaction_index = 0`。现在，我们将让第一个矿工向区块链添加一个区块。

### 添加第一个区块

要添加一个新区块，我们首先创建一个 `Block` 类的实例。

```python
block = Block()
```

我们从队列中提取前 3 笔交易：

```python
for i in range(3):
    temp_transaction = transactions[last_transaction_index]
```

### 验证交易

在将交易添加到区块之前，矿工将验证交易的有效性。交易的有效性通过将发送者提供的哈希与矿工使用发送者公钥生成的哈希进行相等性测试来验证。此外，矿工还将验证发送者是否有足够的余额支付当前交易。为了简单起见，我们没有在教程中包含此功能。

交易通过验证后，我们将其添加到 `block` 实例的 `verified_transactions` 列表中。

```python
block.verified_transactions.append(temp_transaction)
```

我们增加最后一次交易的索引，以便下一个矿工能够获取队列中的后续交易。

```python
last_transaction_index += 1
```

我们向区块恰好添加了三笔交易。一旦完成，我们将初始化 `Block` 类的其余实例变量。我们首先添加上一个区块的哈希。

```python
block.previous_block_hash = last_block_hash
```

接下来，我们以难度为 2 的级别挖掘该区块。

```python
block.Nonce = mine(block, 2)
```

注意，`mine` 函数的第一个参数是一个二进制对象。现在我们对整个区块进行哈希处理并创建其创建一个摘要。

```python
digest = hash(block)
```

最后，我们将创建的区块添加到区块链中，并重新初始化全局变量 `last_block_hash` 以供下一个区块使用。添加区块的完整代码所示：

```python
block = Block()
for i in range(3):
    temp_transaction = transactions[last_transaction_index]
    # validate transaction
    # if valid:
    block.verified_transactions.append(temp_transaction)
    last_transaction_index += 1
block.previous_block_hash = last_block_hash
block.Nonce = mine(block, 2)
digest = hash(block)
TPCoins.append(block)
last_block_hash = digest
```

### 添加更多区块

现在我们将为我们的区块链再添加两个区块。添加接下来两个区块的代码所示：

### 矿工 2 添加一个区块

```python
block = Block()
for i in range(3):
    temp_transaction = transactions[last_transaction_index]
    # validate transaction
    # if valid:
    block.verified_transactions.append(temp_transaction)
    last_transaction_index += 1
block.previous_block_hash = last_block_hash
block.Nonce = mine(block, 2)
digest = hash(block)
TPCoins.append(block)
last_block_hash = digest
```

### 矿工 3 添加一个区块

```python
block = Block()
for i in range(3):
    temp_transaction = transactions[last_transaction_index]
    display_transaction(temp_transaction)
    # validate transaction
    # if valid:
    block.verified_transactions.append(temp_transaction)
    last_transaction_index += 1
block.previous_block_hash = last_block_hash
block.Nonce = mine(block, 2)
digest = hash(block)
TPCoins.append(block)
last_block_hash = digest
```

当你添加这两个区块时，你还会看到找到 `Nonce` 所需的迭代次数。此时，我们的区块链总共包含 4 个区块（包括创世区块）。

### 导出整个区块链

你可以使用以下语句验证整个区块链的内容：

```python
dump_blockchain(TPCoins)
```

你将看到类似于所示的输出：

```text
Number of blocks in the chain: 4
block # 0
sender: Genesis
-----
recipient: 30819f300d06092a864886f70d010101050003818d0030818902818100ed272b52ccb539e2cd779c6cc10ed1dfadf5d97c6ab6de90ed0372b2655626fb79f62d0e01081c163b0864cc68d426bbe9438e8566303bb77414d4bfcaa3468ab7febac099294de10273a816f7047d4087b4bafa11f141544d48e2f10b842cab91faf33153900c7bf6c08c9e47a7df8aa7e60dc9e0798fb2ba3484bbdad2e4430203010001
-----
value: 500.0
-----
time: 2019-01-14 16:18:02.042739
-----
--------------
=====================================
block # 1
sender: 30819f300d06092a864886f70d010101050003818d0030818902818100ed272b52ccb539e2cd779c6cc10ed1dfadf5d97c6ab6de90ed0372b2655626fb79f62d0e01081c163b0864cc68d426bbe9438e8566303bb77414d4bfcaa3468ab7febac099294de10273a816f7047d4087b4bafa11f141544d48e2f10b842cab91faf33153900c7bf6c08c9e47a7df8aa7e60dc9e0798fb2ba3484bbdad2e4430203010001
... (省略)
```




## 范围与结论

在本教程中，我们学习了如何使用 `Python` 构建一个区块链项目。在许多领域，你可能需要为该项目添加更多功能。

例如：
- 你需要编写函数来管理交易队列。在交易被挖矿且挖出的区块被系统接受后，就不再需要存储它们。
- 此外，矿工显然更倾向于选择手续费最高的交易。同时，你必须确保低费或无费的交易不会永远被饿死。你需要开发算法来管理该队列。
- 另外，本教程不包含客户端接口代码。你需要为普通客户端和矿工开发这部分代码。

完整的区块链项目将涉及更多行代码，超出了本教程的范围。感兴趣的读者可以下载比特币源代码进行进一步学习。

### 结论

这个简洁的教程应该能帮你开始创建自己的区块链项目。对于完整的区块链开发，你可以从 `bitcoin source` 中学习更多知识。对于较大的商业或非商业项目，你可以考虑使用 `Ethereum` —— 这是一个即用的区块链应用平台。

