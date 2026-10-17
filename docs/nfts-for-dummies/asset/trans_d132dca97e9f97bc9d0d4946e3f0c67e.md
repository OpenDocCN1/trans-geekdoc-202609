
-   [MetaMask, 用于以太坊客户端 API]
-   [Ganache GUI, 用于本地测试区块链]
-   [Remix IDE, 用于源代码编译器]

Put On Your Hard Hat: 

# 构建你的环境

在本节中，我们解释如何在个人电脑上实现一个本地区块链。然后我们展示如何配置你的 MetaMask 钱包，以便在你的本地开发环境以及 Remix IDE 中使用。

## 设置你的本地区块链测试环境

如在第 7 章中解释，本地开发环境是一个私有且安全的地方，供你练习部署和测试智能合约。

要设置你的本地开发环境，请按照下面的步骤安装 Ganache 桌面应用（Ganache GUI），它是 Truffle Suite 为智能合约开发者提供的工具包的一部分。

1\. 访问 [www.trufflesuite.com/ganache](http://www.trufflesuite.com/ganache) 并点击下载按钮，如图 8-2 所示，下载 Ganache 桌面应用。

2\. 下载完成后，双击安装包并按照提示安装 Ganache，如图 8-3 所示。

3\. 安装完成后，启动 Ganache 并点击启动页上的 "Quickstart Ethereum" 选项，如图 8-4 所示。Ganache 会启动一个本地区块链，包含模拟以太坊外部账户的测试账户，如图 8-5 所示。

Ganache 的默认设置是启动十个测试账户，每个账户余额为 100 个测试 ETH，仅可在当前工作区使用。

144  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

![](images/00083.jpg)

![](images/00099.jpg)

FIGURE 8-4:

The

Ganache

start

screen.

FIGURE 8-5:

Ganache

Accounts

screen.

4\. 点击 "Blocks" 标签（位于顶部菜单栏的 "Accounts" 标签右侧）查看当前工作区的完整区块链账本。初始化时，你只有 Block 0（创世块）这一个块，如图 8-6 所示。

CHAPTER 8 Setting Up a Development Environment  145

![](images/00113.jpg)

![](images/00128.jpg)

FIGURE 8-6:

The

Ganache

genesis

block at

initiation.

5\. 点击 Ganache 应用窗口右上角的 "Save" 按钮保存工作区。Ganache 会自动（并随机）为你命名工作区。在我们的例子中，Ganache 命名为 "Handsomely-Vessel"。 (参见图 8-7。)

FIGURE 8-7:

Saving your

workspace

on

Ganache.

6\. 关闭并重新打开 Ganache，查看已保存的工作区，如图 8-8 所示，这样你就可以继续之前的工作。恭喜！你已准备好在你的私有开发环境中工作！

如果想更改工作区名称，点击工作区名称右侧的齿轮图标（Set-settings）。 (参见图 8-7。) 会出现一个新界面，你可以编辑工作区名称，如图 8-9 所示。

我们保留 Ganache 为我们随机生成的壮观工作区名称：Handsomely-Vessel！

146  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

![](images/00141.jpg)

![](images/00007.jpg)

FIGURE 8-8:

The

Ganache

start page,

after

reinitiation.

FIGURE 8-9:

Editing your

workspace

on

Ganache.

## 连接自定义（Ganache）网络到你的 MetaMask 钱包

在启动本地区块链后，你已准备好在 MetaMask 钱包中添加这个自定义“网络”及其关联账户。请按照以下步骤操作：

1\. 打开 Ganache 并加载你在前面章节中创建的工作区。

2\. 在 Ganache 界面中找到你的 RPC URL，默认是 [http://127.0.0.1:7545](http://127.0.0.1:7545)，如图 8-10 所示。

CHAPTER 8 Setting Up a Development Environment  147

![](images/00019.jpg)

![](images/00031.jpg)

FIGURE 8-10:

Locating the

RPC URL

from the

Ganache

interface.

3\. 登录你的 MetaMask 钱包。

4\. 在 MetaMask 中，从下拉菜单中选择 "Custom RPC" 选项，如图 8-11 所示。

FIGURE 8-11:

The

Network

drop-down

menu in the

MetaMask

wallet.

5\. 在出现的新页面中（如图 8-12 所示），填写网络名称、新 RPC URL 和链 ID，例如：

•  网络名称：HANDSOMELY-VESSEL

你可以使用任何你想要的网络名称。为了保持一致并避免混淆，我们建议使用你在 Ganache 工作区中选择的网络名称。

•  新 RPC URL：[http://127.0.0.1:7545](http://127.0.0.1:7545) — 默认 RPC URL

•  链 ID：1337 — 默认链 ID

6\. 点击 "Save" 按钮。恭喜！你已成功将新网络添加到 MetaMask 网络选项中，如图 8-13 所示。

FIGURE 8-12:

Adding a

new

network to

MetaMask

wallet.

CHAPTER 8 Setting Up a Development Environment  149

![](images/00075.jpg)

FIGURE 8-13:

HAND-

SOMELY-

VESSEL now

appears in

the

MetaMask

network

options.

## 向你的 MetaMask 钱包添加本地（Ganache）账户

安装 Ganache 并向 MetaMask 添加对应的自定义网络后，你会想要将 Ganache 工作区中的一些账户导入 MetaMask。

要导入本地账户，你需要它们的私钥。

要获取私钥，请按照以下步骤操作：

1\. 打开 Ganache 并加载你在本章前面“设置本地区块链测试环境”部分中创建的工作区。

2\. 在账户页面，选择一个账户并点击最右侧的钥匙图标，如图 8-14 所示。弹出的下一个屏幕会显示该账户的私钥，如图 15 所示。

150  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

![](images/00089.jpg)

![](images/00105.jpg)

FIGURE 8-14:

Accessing

account

private keys

in your

Ganache

workspace.

FIGURE 8-15:

Sample

account

address and

private key

in Ganache.

有了私钥，以下是如何将这些账户导入 MetaMask 的方法：

1\. 登录 MetaMask 钱包，并切换到 Handsomely-Vessel 网络。

我们的自定义网络名称是 Handsomely-Vessel，可能与你在前面章节“设置本地区块链测试环境”中的自定义网络名称不同。

2\. 点击 MetaMask 应用右上角的彩色圆圈，从下拉菜单中选择 "Import Account" 选项，如图 8-16 所示。

CHAPTER 8 Setting Up a Development Environment  151

![](images/00118.jpg)

FIGURE 8-16:

The Import

Account

option in

MetaMask.

3\. 在新出现的对话框中，粘贴 Ganache 工作区中账户的私钥，然后点击 "Import" 按钮，如图 8-17 所示。图 8-18 显示已导入的账户在 MetaMask 中。注意我们重命名了该账户。

重命名你的导入账户，以便记住它是本地 Ganache 账户。我们将导入账户重命名为 "Ganache HV 1"，因为它与原始账户名称相关。要在 MetaMask 中重命名账户，点击账户名称右侧的垂直省略号，选择 "Account Details"，然后点击账户名称旁的铅笔图标，重命名账户，最后点击复选框确认更改。 (更多详情请参见第 7 章。)

恭喜！你已成功将本地 Ganache 账户导入 MetaMask 钱包。