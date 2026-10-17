
# CHAPTER 10 Discovering Token Standards

## ERC-721 非同质化代币标准

要符合 ERC-721 标准，代币合约必须实现 ERC-721 接口和 ERC-165 接口中的以下元素。所有函数和事件都必须使用这些接口规定的相同命名约定进行声明。

让我们先来看看必需的函数：

`name()` 和 `symbol()`：这些可选函数返回其对应状态变量中存储的值。

`balanceOf(address _owner)`：此函数返回指定地址 `_owner` 的账户中拥有的 NFT 数量。

`ownerOf(uint256 _tokenId)`：此函数返回指定 NFT `_tokenId` 的所有者地址。

`safeTransferFrom(address _from, address _to, uint256 _tokenId, bytes data)`：此函数将指定 NFT `_tokenId` 从一个指定账户 `_from` 转移到另一个账户 `_to`，并向接收账户 `_to` 传递 `data` 数据。

`safeTransferFrom(address _from, address _to, uint256 _tokenId)`：此函数将指定 NFT `_tokenId` 从一个指定账户 `_from` 转移到另一个账户 `_to`。

`transferFrom(address _from, address _to, uint256 _tokenId)`：此函数与 `safeTransferFrom` 功能类似，但不验证接收账户 `_to` 是否能够接收 NFT。

`approve(address _approved, uint256 _tokenId)`：此函数允许指定账户 `_approved` 转移指定 NFT `_tokenId`。

`setApprovalForAll(address _operator, bool _approved)`：此函数切换指定账户 `_operator` 是否拥有所有 NFT 的转移权限。

`getApproved(uint256 _tokenId)`：此函数返回拥有指定 NFT `_tokenId` 转移权限的账户地址。

`isApprovedForAll(address _owner, address _operator)`：此函数检查一个账户 `_operator` 是否拥有另一个账户 `_owner` 的所有 NFT 的转移权限。

`supportsInterface(bytes4 interfaceID)`：此函数是 ERC-165 标准接口检测所必需的，用于标准接口检测。

接下来，我们来查看 ERC-721 接口中声明的事件：

`Transfer(address indexed _from, address indexed _to, uint256 indexed _tokenId)`：当 NFT 从一个账户转移到另一个账户时，必须触发此事件。

`Approval(address indexed _owner, address indexed _approved, uint256 indexed _tokenId)`：每当一个账户批准另一个账户转移 NFT 时，必须触发此事件。

`ApprovalForAll(address indexed _owner, address indexed _operator, bool _approved)`：每当一个账户允许或禁止另一个账户访问其所有 NFT 时，必须触发此事件。

在实现 ERC-721 接口时，还需要在代币合约中存储一些状态变量。与之前一样，以下状态变量可以按你的具体实现方式来声明和定义：

`owners[]`：此变量存储每个单个 NFT 的所有者账户地址（此变量是一个数组）。

`balances[]`：此变量存储每个账户中的 NFT 数量（此变量是一个数组）。

`tokenApprovals[]`：此变量存储每个单个 NFT 当前被允许转移权限的账户地址（此变量是一个数组）。

`operatorApprovals[][]`：跟踪一个账户是否拥有另一个账户的转移权限（此变量是一个二维数组）。

`currently allowed to transfer the NFTs from the other account`

`(this variable is a matrix).`

`name (optional) stores the unifying group name for the NFTs`

`(such as CryptoKitties).`

`symbol (optional) stores the symbol for the NFTs (such as CK in`

`the case of CryptoKitties).`

Again, different implementations may require additional `funcName()` or variables, which can be declared and defined as you see fit. To be ERC-721 compliant, however, all functions and events declared in the ERC-721 interface and ERC-165 interface must be named and implemented as specified by the interfaces.

## Other token standards on Ethereum

With the proliferation of fungible and non-fungible tokens alike, varying implementations continue to provide added functionality and enhancements. Some of these features have been formalized as additional token standards, to provide either a new standard altogether (such as the multi-token standard) or a standard interface for improvements to the original fungible or non-fungible token interfaces.

Here are some examples of finalized standards:

» The ERC-777 Token Standard: This standard introduced an interface for an ERC-20 backward-compatible fungible token with advanced features, some of which were popularized by the ERC-721 Non-Fungible Token Standard. For instance, the ERC-777 interface specifies a function to grant an account the right to transfer tokens on behalf of another account.

» The ERC-1363 Payable Token Standard: This standard introduced an interface for ERC-20 tokens to enable automatic code execution upon a successful call to the `transfer`, `transferFrom`, or `approve` functions.

» The ERC-2981 NFT Royalty Standard: The ERC-2981 standard introduced an interface for ERC-721 and ERC-1155 non-fungible tokens to designate a royalty amount and recipient to be paid each time the NFT in question is sold.

» The ERC-1155 Multi-Token Standard: This standard introduced a consolidated interface to manage fungible, non-fungible, and semi-fungible tokens (similar to limited-edition releases).

As adoption continues to spread and additional use cases materialize, you’re sure to see more interesting and exciting token standards to come!

# CHAPTER 11 Building an ERC-721 Token

This chapter walks you through the steps in developing, compiling, and deploying your first non-fungible token contract.

To successfully follow the step-by-step guide in this chapter, you need to have completed some key steps in advance. We assume that you have faithfully followed the prerequisite hands-on instructional portions of Chapters 7, 8, and 9.

## Writing and Compiling Your NFT

Because a token contract is a special type of smart contract, you begin your NFT journey with the steps for launching your first smart contract that we show you in Chapter 9. When in doubt, refer to that chapter for an illustrated guide on file creation and compilation.

## The code

When building a token contract, always start by firing up the Remix environment — just follow these steps to get the ball rolling:

1. Go to [`remix.ethereum.org`](http://remix.ethereum.org/). You must type http:// (without the s) and not https:// (with the s), or else Remix can’t access MetaMask.

2. Click the New File link under the File heading on the main page. (Alternatively, you can find the New File icon in the File Explorers pane, located on the left side of the page.)

A new file appears in the File Explorers pane, waiting for you to type a new name.

3. Using the cursor, click into the blank text box, type `NFTFD.sol`, and then press Enter. A new tab pops up, labeled with the name of the file.

The `.sol` extension is used to indicate a Solidity source file.

For more on Solidity, see Chapter 9.

At any time, click the Double Page icon, located on the toolbar running down the left side of the window, to return to the File Explorer browser pane.

4. Type the following code into the newly created `NFTFD.sol` file:

```solidity
pragma solidity ⁰.8.0;

import “https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol”;

contract NFTFD is ERC721URIStorage {
address public founder;
constructor() ERC721(“NFTs For Dummies”,
“NFTFD”) {
founder = msg.sender;
for (uint tokenID=1; tokenID<=5;
tokenID++) {
_mint(founder, tokenID);
_setTokenURI(tokenID, “NFTFD
Limited Edition Initial Release”);
}
}
}
function mintNFT(
address to,
uint256 tokenID,
string memory tokenURI
)
public
{
require(msg.sender == founder, “not
an authorized minter”);
_mint(to, tokenID);
_setTokenURI(tokenID, tokenURI);
}
```
