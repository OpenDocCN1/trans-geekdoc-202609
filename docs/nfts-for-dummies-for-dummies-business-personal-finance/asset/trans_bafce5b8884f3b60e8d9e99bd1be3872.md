

![Technicalstuff](images/technicalstuff.png)

不同的实现可能需要额外的函数或变量，但你至少必须按照接口规范，命名并实现 ERC-20 接口中声明的函数和事件。你在 ERC-20 接口实现中声明的变量名称不会影响你的代币合约与任何其他预期与 ERC-20 代币交互的合约的互操作性。

## ERC-721 非同质化代币标准

要符合 ERC-721 标准，代币合约必须实现 ERC-721 接口和 ERC-165 接口的以下要素。所有函数和事件必须按照这些接口规定的命名约定进行声明。

首先让我们看看所需的函数：

*   `name()` 和 `symbol()`：这些可选函数返回存储在其同名状态变量中的值。
*   `balanceOf(address _owner)`：此函数返回地址为 `_owner` 的账户中 NFT 的数量。
*   `ownerOf(uint256 _tokenId)`：此函数返回拥有指定 NFT `_tokenId` 的账户地址。
*   `safeTransferFrom(address _from, address _to, uint256 _tokenId, bytes data)`：此函数将指定的 NFT `_tokenId` 从一个指定账户 (`_from`) 转移到另一个账户 (`_to`)，并将 `data` 传递给接收账户 (`_to`)。
*   `safeTransferFrom(address _from, address _to, uint256 _tokenId)`：此函数将指定的 NFT `_tokenId` 从一个指定账户 (`_from`) 转移到另一个账户 (`_to`)。
*   `transferFrom(address _from, address _to, uint256 _tokenId)`：此函数类似于 `safeTransferFrom`，但不验证接收账户 (`_to`) 是否可以接收 NFT。
*   `approve(address _approved, uint256 _tokenId)`：此函数允许指定账户 (`_approved`) 转移指定的 NFT (`_tokenID`)。
*   `setApprovalForAll(address _operator, bool _approved)`：此函数切换权限设置，以确定指定账户 (`_operator`) 是否拥有你账户中所有 NFT 的转移权。
*   `getApproved(uint256 _tokenId)`：此函数返回拥有指定 NFT (`_tokenID`) 转移权的账户地址。
*   `isApprovedForAll(address _owner, address _operator)`：此函数检查一个账户 (`_operator`) 是否拥有另一个账户 (`_owner`) 所有 NFT 的转移权。
*   `supportsInterface(bytes4 interfaceID)`：此函数包含自必需的 ERC-165 接口，用于标准接口检测。

现在让我们看看 ERC-721 接口中声明的事件：

*   `Transfer(address indexed _from, address indexed _to, uint256 indexed _tokenId)`：当 NFT 从一个账户转移到另一个账户时，必须触发此事件。
*   `Approval(address indexed _owner, address indexed _approved, uint256 indexed _tokenId)`：每当一个账户批准另一个账户的 NFT 转移权时，必须触发此事件。
*   `ApprovalForAll(address indexed _owner, address indexed _operator, bool _approved)`：每当一个账户允许或禁止另一个账户访问其所有 NFT 时，必须触发此事件。

在实现 ERC-721 接口时，某些状态变量也必须存储在代币合约中。和之前一样，以下状态变量可以根据你对接口的特定实现，以你认为合适的方式声明和定义。

*   `owners[]` 存储与每个单独 NFT 关联的所有者账户地址（此变量为数组）。
*   `balances[]` 存储每个账户中的 NFT 数量（此变量为数组）。
*   `tokenApprovals[]` 存储当前被允许拥有每个单独 NFT 转移权的账户地址（此变量为数组）。
*   `operatorApprovals[][]` 跟踪一个账户当前是否被允许转移另一个账户的 NFT（此变量为矩阵）。
*   `name`（可选）存储 NFT 的统一组名（例如 `CryptoKitties`）。
*   `symbol`（可选）存储 NFT 的符号（例如 CryptoKitties 的 `CK`）。

同样，不同的实现可能需要额外的函数或变量，可以根据需要声明和定义。然而，要符合 ERC-721 标准，ERC-721 接口和 ERC-165 接口中声明的所有函数和事件必须按照接口规范进行命名和实现。

## 以太坊上的其他代币标准

随着同质化和非同质化代币的大量涌现，不同的实现持续提供额外的功能和增强。其中一些功能已被正式确立为额外的代币标准，以提供全新的标准（如多代币标准）或原始同质化或非同质化代币接口改进的标准接口。

以下是一些已定稿标准的示例：

*   **ERC-777 代币标准：** 该标准引入了一个接口，用于具有高级功能的 ERC-20 向后兼容同质化代币，其中一些功能由 ERC-721 非同质化代币标准推广。
    例如，ERC-777 接口指定了一个函数，用于授予账户代表另一个账户转移代币的权利。
*   **ERC-1363 可支付代币标准：** 该标准引入了一个接口，使 ERC-20 代币能够在成功调用 `transfer`、`transferFrom` 或 `approve` 函数时自动执行代码。
*   **ERC-2981 NFT 版税标准：** ERC-2981 标准引入了一个接口，用于 ERC-721 和 ERC-1155 非同质化代币，以指定每次相关 NFT 售出时应支付的版税金额和接收者。
*   **ERC-1155 多代币标准：** 该标准引入了一个统一接口，用于管理同质化、非同质化和半同质化代币（类似于限量版发行）。

随着采用的持续扩展和更多用例的出现，你肯定会看到更多有趣且令人兴奋的代币标准问世！

# 第 11 章：构建 ERC-721 代币

## 本章内容

![Bullet](images/check.png) **启动你自己的 NFT**

![Bullet](images/check.png) **追踪你的 NFT**

![Bullet](images/check.png) **与你的 NFT 交互**

本章将指导你完成开发、编译和部署你的第一个非同质化代币合约的步骤。

要成功遵循本章中的分步指南，你需要提前完成一些关键步骤。我们假设你已忠实地遵循了第 [7](#c07.xhtml)、[8](#c08.xhtml) 和 [9](#c09.xhtml) 章中的先决实操指导部分。

## 编写和编译你的 NFT

因为代币合约是一种特殊类型的智能合约，所以你可以从第 [9](#c09.xhtml) 章中展示的启动第一个智能合约的步骤开始你的 NFT 之旅。如果有疑问，请参考该章以获取关于文件创建和编译的图解指南。

### 代码

构建代币合约时，始终从启动 Remix 环境开始 —— 只需遵循以下步骤即可开始：

1.  **访问** [`http://remix.ethereum.org`](http://remix.ethereum.org/)**。**

    ![Remember](images/remember.png) 你必须输入 `http://`（不带 *s*），而不是 `https://`（带 *s*），否则 Remix 无法访问 MetaMask。

2.  **点击主页上“File”标题下的“New File”链接。（或者，你可以在页面左侧的“File Explorers”窗格中找到“New File”图标。）**

    一个新文件会出现在“File Explorers”窗格中，等待你输入新名称。

3.  **使用光标点击空白文本框，输入** `NFTFD.sol`，**然后按 Enter 键。**

    一个新标签页会弹出，标签上显示文件名。

