
![cover](images/cover.jpeg)

Dr. Hedaya Mahmood Alasooly

# Quick Guide for Smart Contracts Creation and Deployment on Ethereum Blockchain

BookRix GmbH & Co. KG  
80331 Munich

## Quick Guide for Smart Contracts Creation and Deployment on Ethereum Blockchain

**By**  
Dr. Hedaya Mahmood Alasooly  
Hedaya_alasooly@yahoo.com

## 1. Overview

This work explains briefly the creation and deployment of Smart Contracts on the Ethereum Blockchain. The work consists of the following sections:

*   Blockchain
*   Solidity variables and types
*   How to Setup or Install Ethereum on Windows
*   How to compile and deploy smart contract on JavaScriptVM
*   How to install Ganache Blockchain on Windows and deploy smart contract using it
*   How to compile and deploy Smart Contract on Test Networks
*   Quick example of deploying ERC20 token smart contract
*   Getting started tutorial on Solidity
*   Creating ERC-20 smart contract and crowd sale (ICO) smart contract without coding
*   ERC-20 smart contract and crowd sale (ICO) smart contract
*   Creating Ethereum ERC-20 Tokens and Crowd Sales (ICO) without coding with Token Wizard
*   Example of creating and deploying an ERC20 token on the test and main network!!!

## 2. Blockchain

A blockchain is a digital record of transactions. The name comes from its structure, in which individual records, called blocks, are linked together in a single list, called a chain. Blockchains are used for recording transactions made with cryptocurrencies, such as Bitcoin, and have many other applications.

Each transaction added to a blockchain is validated by multiple computers on the Internet. These systems, which are configured to monitor specific types of blockchain transactions, form a peer-to-peer network. They work together to ensure each transaction is valid before it is added to the blockchain. This decentralized network of computers ensures a single system cannot add invalid blocks to the chain.

When a new block is added to a blockchain, it is linked to the previous block using a cryptographic hash generated from the contents of the previous block. This ensures the chain is never broken and that each block is permanently recorded. It is also intentionally difficult to alter past transactions in a blockchain since all the subsequent blocks must be altered first.

### Blockchain Uses

While blockchain is widely known for its use in cryptocurrencies such as Bitcoin, Litecoin, and Ether, the technology has several other uses. For example, it enables "smart contracts," which execute when certain conditions are met. This provides an automated escrow system for transactions between two parties. Blockchain can potentially be used to allow individuals to pay each other without a central clearing point, which is required for ACH and wire transfers. It has the potential to greatly increase the efficiency of stock trading by allowing transactions to settle almost instantly instead of requiring three or more days for each transaction to clear. Blockchain technology can also be used for non-financial purposes. For example, the InterPlanetary File System (IPFS) uses blockchain to decentralize file storage by linking files together over the Internet. Some digital signature platforms now use blockchain to record signatures and verify documents have been digitally signed. Blockchain can even be used to protect intellectual property by linking the distribution of content to the original source.

Blockchain is a decentralized database that consists of records and data. The entire data is spread out in a bunch of distributed computers to form a peer-to-peer (p2p) network. The records in these databases are stored in the form of blocks which are linked together in a secured way.

The Bitcoin blockchain stores data specific to keeping track of cryptocurrency balances between different parties.

The Ethereum blockchain can store much deeper data than the Bitcoin blockchain. The Ethereum blockchain allows building decentralized apps. These decentralized apps are defined by smart contracts. So smart contracts allow individuals to exchange information in a trusted, confident, free manner without relying on a third party such as a bank or lawyer. These Ethereum smart contracts are stored in special transactions in the Ethereum blockchain which can then be used to build applications. You can think of smart contracts as decentralized APIs. As smart contracts are stored in Ethereum blockchains, they need to be validated or mined as any other transactions. So there are small costs associated with deploying smart contracts.

How to code a smart contract? We do that with Solidity. Solidity is a language used to code smart contracts. The syntax is similar to JavaScript and is designed with the Ethereum Virtual Machine (EVM) in mind. So we will use Solidity to create smart contracts in a web-based IDE called Remix.

## 3. Solidity variables and types

*   You can write the Solidity code and test it at `https://remix.ethereum.org/`.
*   Here is a screenshot of `https://remix.ethereum.org`:

![](images/159551591299085953_1.jpg)

*   Create a new contract. I called it `Coursetro`.
*   Start off by writing (or pasting) the following code:

```solidity
pragma solidity ^0.4.18;

contract Coursetro {

}
```

The very first line defines the version of Solidity you are going to use. Next, you define the contract and its name and open it up like a JavaScript class.

*   On the right side of the browser under the **Run** tab, you will see a **Deploy** button. Click on this. You will notice that underneath the Deploy button a new section appears with the name of the contract and "at 0x..." (memory):

![](images/159551591230265132_2.jpg)

*   This means that the smart contract (yes, it's not very smart at this point) lives at an address. To see this full address along with other information, in the debugger if you click on the **Details** button, it will provide you with more information:
*   Notice there is a `contractAddress`; this is where the smart contract actually lives. No, it's not live on the Ethereum Blockchain because right now, we are simply working within the JavaScript EVM.
*   Also notice `gas`. Every time a contract is deployed and modified, nodes on the Ethereum network must verify the contract. It is referred to as being redundantly parallel, as a way to reach consensus. `Gas` is the name for the execution fee that senders of transactions (in our case, senders of a smart contract transaction) will pay for verification.

### Elaborating on this further

From `etherdocs.org`:

> "Gas is the name for the execution fee that senders of transactions need to pay for every operation made on an Ethereum blockchain. The name gas is inspired by the view that this fee acts as cryptofuel, driving the motion of smart contracts. Gas is purchased for ether from the miners that execute the code. Gas and ether are decoupled deliberately since units of gas align with computation units having a natural cost, while the price of ether generally fluctuates as a result of market forces. The two are mediated by a free market: the price of gas is actually decided by the miners, who can refuse to process a transaction with a lower gas price than their minimum limit. To get gas you simply need to add ether to your account. The Ethereum clients automatically purchase gas for your ether in the amount you specify as your maximum expenditure for the transaction."

In Solidity, you define a variable by first specifying its type. What other types are there?

1.  **bool**  
    This is a Boolean, which returns `true` or `false`.

2.  **int / uint**  
    Both `int` and `uint` represent integers, or number values. The primary difference between `int` and `uint` (Unsigned Integer) is that `int` can hold negative numbers as values.

3.  **address**
