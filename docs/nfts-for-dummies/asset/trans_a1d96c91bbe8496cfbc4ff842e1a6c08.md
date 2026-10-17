
currently allowed to transfer the NFTs from the other account

(this variable is a matrix).

name (optional) stores the unifying group name for the NFTs

(such as CryptoKitties).

symbol (optional) stores the symbol for the NFTs (such as CK in

the case of CryptoKitties).

Again, different implementations may require additional `funcName()` or variables, which can be declared and defined as you see fit. To be ERC-721 compliant, however, all functions and events declared in the ERC-721 interface and ERC-165 interface must be named and implemented as specified by the interfaces.

Other token standards

on Ethereum

With the proliferation of fungible and non-fungible tokens alike, varying implementations continue to provide added functionality and enhancements. Some of these features have been formalized as additional token standards, to provide either a new standard altogether (such as the multi-token standard) or a standard interface for improvements to the original fungible or non-fungible token interfaces.

194 PART 3 Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

Here are some examples of finalized standards:

» The ERC-777 Token Standard: This standard introduced an interface for an ERC-20 backward-compatible fungible token with advanced features, some of which were popularized by the ERC-721 Non-Fungible Token Standard. For instance, the ERC-777 interface specifies a function to grant an account the right to transfer tokens on behalf of another account.

» The ERC-1363 Payable Token Standard: This standard introduced an interface for ERC-20 tokens to enable automatic code execution upon a successful call to the transfer, transferFrom, or approve functions.

» The ERC-2981 NFT Royalty Standard: The ERC-2981 standard introduced an interface for ERC-721 and ERC-1155 non-fungible tokens to designate a royalty amount and recipient to be paid each time the NFT in question is sold.

» The ERC-1155 Multi-Token Standard: This standard introduced a consolidated interface to manage fungible, non-fungible, and semi-fungible tokens (similar to limited-edition releases).

As adoption continues to spread and additional use cases materialize, you’re sure to see more interesting and exciting token standards to come!

CHAPTER 10 Discovering Token Standards 195

![](images/00119.jpg)

IN THIS CHAPTER

» Launching your own NFT

» Tracking your NFT

» Interacting with your NFT

Chapter 11

Building an ERC-721 Token

This chapter walks you through the steps in developing, compiling, and deploying your first non-fungible token contract.

To successfully follow the step-by-step guide in this chapter, you need to have completed some key steps in advance. We assume that you have faithfully followed the prerequisite hands-on instructional portions of Chapters 7, 8, and 9.

Writing and Compiling Your NFT

Because a token contract is a special type of smart contract, you begin your NFT journey with the steps for launching your first smart contract that we show you in Chapter 9. When in doubt, refer to that chapter for an illustrated guide on file creation and compilation.

CHAPTER 11 Building an ERC-721 Token 197

The code

When building a token contract, always start by firing up the Remix environment — just follow these steps to get the ball rolling:

1\. Go to [http://remix.ethereum.org](http://remix.ethereum.org/). You must type http:// (without the s) and not https:// (with the s), or else Remix can’t access MetaMask.

2\. Click the New File link under the File heading on the main page. (Alternatively, you can find the New File icon in the File Explorers pane, located on the left side of the page.)

A new file appears in the File Explorers pane, waiting for you to type a new name.

3\. Using the cursor, click into the blank text box, type NFTFD. sol, and then press Enter. A new tab pops up, labeled with the name of the file.

The .sol extension is used to indicate a Solidity source file.

For more on Solidity, see Chapter 9.

At any time, click the Double Page icon, located on the toolbar running down the left side of the window, to return to the File Explorer browser pane.

4\. Type the following code into the newly created NFTFD. sol file:

```solidity
pragma solidity ^0.8.0;

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
```

5\. To compile the source code you just typed, click the Solidity-Compiler icon, located in the Navigation pane to the far left.

You can find the Solidity Compiler icon just below the File Explorers Double Page icon.

6\. From the Solidity Compiler browser pane, click the Compile NFTFD. sol button.

CHAPTER 11 Building an ERC-721 Token 199

![](images/00057.jpg)

The compilation details for this contract appear underneath the Compile NFTFD. sol button. This time, when you click the Contract drop-down menu that appears (as shown in Figure 11-1), the following contract names appear in addition to NFTFD:

» ERC721URIStorage

» ERC721

» IERC721

» IERC721Receiver

» IERC721Metadata

» Address

» Context

» Strings

» ERC165

» IERC165

FIGURE 11-1:

NFTFD and base contract compilation details on Remix.

If you take a closer look at the source code we have you type in Step 4, you notice the line contract NFTFD is ERC721URI Storage {. It tells you that the NFTFD contract is directly derived from the prebuilt base contract — ERC721URIStorage (imported from [https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol)) — which is derived from the ERC721 base contract, which itself is derived from the other interfaces and contracts in the preceding list.

The play-by-play

The following is a chunk-by-chunk explanation of the NFTFD. sol code you use for your token contract. We also provide tips for whether you can easily customize elements of the code and not accidentally break something.

```solidity
pragma solidity ^0.8.0;

I.  This Solidity version pragma allows the source code to be compiled only under versions 0.8.x (including and following version 0.8.0 but strictly preceding version 0.9.0).

import “https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721URIStorage.sol”;

II.  The next line of code directs the compiler to import the ERC721URIStorage contract from OpenZeppelin’s smart-contract library. This contract serves as the base from which we derive our own token contract.
```
