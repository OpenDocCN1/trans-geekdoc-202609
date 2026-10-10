
```
uint numberPosition = _numberStorage.length;
```

修改为：

```
uint numberPosition = _numberStorage.length - 1;
```

现在再次运行 `truffle migrate`，完成后，运行 `truffle console`。在控制台中，再次运行以下命令：

```
~> Storage.deployed().then((i) => { iStorage = i})
~> iStorage.AddedNewNumber({}).watch((err, res) => { console.log("NUMBER POSITION: " + res.args.position.toNumber()) });
~> iStorage.addNumber(12);
~> output: "NUMBER POSITION: 0"
~> iStorage.getNumber(0)
~> iStorage.getNumber(0).then((res) => { console.log(res.toNumber()) } )
~> output: 12
```

你已成功部署并调试了智能合约！

# 第 10 章：使用 Puppeth，以太坊私有网络管理器

### 作者：Bruno Škvorc

**在前面的章节中，[我们讨论了 Geth](#part0003_split_000.html#2RHM0-7bc08c01daea4ad09f5951d0fde8baea)，它是最流行的以太坊节点之一。**

![下载界面](images/00049.jpeg)

当你安装带有辅助工具的 Geth 时，它会附带一个名为 Puppeth 的实用工具，你可以用它来维护和安装各种辅助工具，以管理和部署你的私有区块链。如果你安装了 Go，也可以通过以下命令独立安装 Puppeth：

```
go get github.com/ethereum/go-ethereum/cmd/puppeth
```

让我们来看看这个工具。

#### 先决条件

本教程要求你拥有两台远程机器。无论是像 [Homestead Improved](http://www.sitepoint.com/quick-tip-get-homestead-vagrant-vm-running/) 这样的虚拟机，还是你网络上的实际服务器，亦或是两者的组合，都无所谓。在本教程中，我们将通过虚拟机演示设置过程。

#### 烦人的 Bug

由于 [Puppeth 中的一个 Bug](https://github.com/ethereum/go-ethereum/issues/16905)，如果你的虚拟机（见下文）太小，这种方法可能行不通。要么创建更大的虚拟机（更多内存），要么如果无法做到这一点，就等待修复。

## 引导启动

我们将遵循 [此流程](http://www.sitepoint.com/quick-tip-get-homestead-vagrant-vm-running/) 启动并运行两台虚拟机。我们需要两台机器，因为我们将运行两个以太坊节点，每个节点拥有自己的 IP 地址。

#### 为什么需要两个节点？

这是 Puppeth 的一个限制，因为无法使用此工具在同一台机器上部署一个出块节点。

如果你不知道什么是 Vagrant，以及我们在这里使用了什么工具，我们建议你阅读 [Vagrant 入门](http://www.sitepoint.com/re-introducing-vagrant-right-way-start-php/)，它以对新手友好的方式进行了详细拆解。

```
mkdir my_project; cd my_project
git clone https://github.com/swader/homestead_improved hi_puppeth1
git clone https://github.com/swader/homestead_improved hi_puppeth2
```

通过进入 `hi_puppeth2` 文件夹并将 `IP address` 字段修改为 `192.168.10.11` 而不是 `192.168.10.10`，来更改第二个克隆的 IP 地址。

接下来，通过修改每个克隆的 `Homestead.yaml` 末尾部分来在虚拟机上打开一些端口，如下所示：

```
 ports:
     - send: 8545
       to: 8545
     - send: 30301
       to: 30301
     - send: 30302
       to: 30302
     - send: 30303
       to: 30303
     - send: 30304
       to: 30304
     - send: 30305
       to: 30305
     - send: 30306
       to: 30306
```

别忘了将这些虚拟主机也添加到宿主机的 `/etc/hosts` 文件中。否则虚拟机将无法通过域名访问！

```
192.168.10.10 homestead.test
192.168.10.11 puppethnode.test
```

#### IP 地址

如果你的虚拟机 IP 地址不同，请相应更改。

最后，运行 `vagrant up; vagrant ssh` 启动每台机器并通过 SSH 登录。记得要从*两个单独的标签页*运行此命令，以便保持两台机器都处于开启和运行状态。

## 先决条件

现在让我们在*每台机器*上安装先决软件。

Puppeth 会在 Docker 容器中为你运行辅助应用程序和以太坊节点，所以我们需要 Docker。安装 Geth 本身也很有用。

```
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common \
    ethereum \
    docker.io \
    docker-compose
```

所有其他先决条件将由 Puppeth 通过 docker 自动拉取，但我们需要先确保当前用户被允许操作 Docker 命令：

```
sudo usermod -a -G docker $USER
```

在宿主机上（虚拟机外部），我们应该在运行项目的文件夹中创建新的以太坊账户。

如果你按上述建议使用虚拟机，如果 `myproject` 是包含 `hi_puppeth1` 和 `hi_puppeth2` 的父文件夹，那么可以在 `myproject` 中进行。

```
mkdir node1 node2
geth --datadir node1 account new
geth --datadir node2 account new
```

记下此过程生成的地址：

```
$ mkdir node1 node2
$ geth --datadir node1 account new
INFO [05-20|10:27:20] Maximum peer count                       ETH=25 LES=0 total=25
Your new account is locked with a password. Please give a password. Do not forget this password.
Passphrase:
Repeat passphrase:
Address: {aba88be2dc16eaed464e3991eed5a1eaa5e7b11b}
$ geth --datadir node2 account new
INFO [05-20|10:27:35] Maximum peer count                       ETH=25 LES=0 total=25
Your new account is locked with a password. Please give a password. Do not forget this password.
Passphrase:
Repeat passphrase:
Address: {655a6ea9950cdf9f8a8175fda639555f17277bdf}
```

我们需要两个账户，因为在权威证明区块链中至少需要两个*签名者*（稍后详述）。

## Puppeth

现在我们的虚拟机正在运行，账户也已初始化，让我们看看 Puppeth 提供了什么功能。在远程服务器/虚拟机仍在运行的情况下，在宿主机上打开一个新标签页，通过 `puppeth` 运行 Puppeth。

它首先会询问网络名称。如果你在本地机器上运行多条区块链，这有助于识别各个区块链。我们这里将使用 "puptest"。

```
Please specify a network name to administer (no spaces or hyphens, please)
> puptest

Sweet, you can set this via --network=puptest next time!

INFO [05-20|10:32:15] Administering Ethereum network           name=puptest
WARN [05-20|10:32:15] No previous configurations found         path=/Users/swader/.puppeth/puptest
```

现在让我们连接到我们的“远程”服务器，以便 Puppeth 将它们列入列表并可以对它们执行操作。

### 跟踪新的远程服务器

使用此选项可以连接到将运行区块链相关服务的服务器。选择选项 3，然后按如下方式输入值：

```
Please enter remote server's address:
> vagrant@192.168.10.10
What's the decryption password for /Users/swader/.ssh/id_rsa? (won't be echoed)
>

The authenticity of host '192.168.10.10:22 (192.168.10.10:22)' can't be established.
SSH key fingerprint is 38:53:d3:c2:85:cf:77:54:a5:54:26:3b:93:5b:6f:09 [MD5]
Are you sure you want to continue connecting (yes/no)? yes
What's the login password for vagrant at 192.168.10.10:22? (won't be echoed)
>
INFO [05-20|10:39:53] Starting remote server health-check      server=vagrant@192.168.10.10
+-----------------------+---------------+---------+--------+-------+
|        SERVER         |    ADDRESS    | SERVICE | CONFIG | VALUE |
+-----------------------+---------------+---------+--------+-------+
| vagrant@192.168.10.10 | 192.168.10.10 |         |        |       |
+-----------------------+---------------+---------+--------+-------+
```

Puppeth 会询问你的 SSH 密钥密码，以防通过 SSH 连接到服务器。如果不是，它将询问 SSH 密码（如上例所示）。相关虚拟机上用户 `vagrant` 的默认 SSH 密码是 `vagrant`。

