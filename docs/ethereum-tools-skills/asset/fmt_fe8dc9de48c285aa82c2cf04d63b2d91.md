
The JavaScript VM provides five fake accounts with `100` ether each, which we can use to test the contract. You can select a current account from the dropdown menu with the name `Account` below the `Environment` dropdown.

![Select a current account](images/00019.jpeg)

Now, to send money to the contract, we first set the `Value` variable (between 0.001 and 0.1) and the unit (ether) from the dropdown menu. Then we call the fallback function by simply clicking on its corresponding red button.

![Calling the fallback function](images/00020.jpeg)

That’s it. We’ve sent money to the contract. The address of the selected account should be added to the `players` array. To check that, simply click on the blue `players` button.

![Clicking on the blue Players button](images/00021.jpeg)

You can add other participants by selecting a new account and repeat the previous process (to check if an account is added to the array simply enter the index, from 0 to 4, for that account in the text-box next to `players` button).

If you add an account that has already participated, you should get a warning in the terminal and the transaction will fail with a message like the following:

![Failure message](images/00022.gif)

## Remix Alternatives

There are many alternatives for easy development and deployment of smart contracts, such as:

*   [Truffle](http://truffleframework.com/): advertised as the Ethereum Swiss army knife and claims to be the most popular development framework for Ethereum with a mission to make your life a whole lot easier. We’ll be working with Truffle a lot in upcoming chapters
*   [Embark](https://github.com/embark-framework/embark): a framework that allows you to easily develop and deploy Decentralized Applications (DApps).
*   [MetaMask](https://metamask.io/): a bridge that allows you to visit the distributed web of tomorrow in your browser today. It allows you to run Ethereum DApps right in your browser without running a full Ethereum node. For how to develop with MetaMask, check this [faq](https://github.com/MetaMask/faq/).
*   [Dapp](https://dapp.readthedocs.io/en/latest/): Dapp is a simple command line tool for smart contract development.
*   different plugins for adding Solidity support to popular IDEs such as [this Visual Code plugin](https://marketplace.visualstudio.com/items?itemName=JuanBlanco.solidity) and [this Atom plugin](https://atom.io/packages/language-ethereum) etc.

## Conclusion

We’ve introduced you to the Remix IDE for developing smart contracts for the Ethereum blockchain. You can find more detailed information in the [docs](http://remix.readthedocs.io/en/latest/).

With a basic introduction behind you, feel free to dive in deeper and experiment with changing the code and exploring the different functions and tabs the editor offers.

# Chapter 2: An Introduction to Geth and Running Ethereum Nodes

## by Mislav Javor

**In this article, we’ll look at what Ethereum nodes are, and explore one of the most popular ones, called Geth.**

In order to communicate with the blockchain, we must use a blockchain **client**. The client is a piece of software capable of establishing a p2p communication channel with other clients, signing and broadcasting transactions, mining, deploying and interacting with smart contracts, etc. The client is often referred to as a **node**.

The formal definition of the functionality an Ethereum node must follow is defined in the [ethereum yellow paper](https://ethereum.github.io/yellowpaper/paper.pdf). The yellow paper defines the required functions of nodes on the network, the mining algorithm, private/public key [ECDSA](https://en.wikipedia.org/wiki/Elliptic_Curve_Digital_Signature_Algorithm) parameters. It defines the entirety of features which make nodes fully compatible Ethereum clients.

Based on the yellow paper, anyone is able to create their own implementation of an Ethereum node in whatever language they see fit.

A full list of clients can be seen [here](https://github.com/ethereum/wiki/wiki/Clients,-tools,-dapp-browsers,-wallets-and-other-projects#ethereum-clients).

The most popular clients so far are [Geth](https://github.com/ethereum/go-ethereum/wiki) and [Parity](https://wiki.parity.io/). The implementations differ mostly by the programming language of choice — where Geth uses Golang and Parity uses Rust.

Since Geth is the most popular client implementation currently available, we’ll focus on it for now.

## Types of Nodes

When you’re joining the Ethereum network, you have an option of running various types of nodes. The options currently are:

*   Light node
*   Full node
*   Archive node

An archive node is a special case of a full node, so we won’t go into detail on it. One of the best summaries on the types of nodes I’ve found is on [Stack Exchange](https://ethereum.stackexchange.com/questions/5975/what-are-the-types-of-nodes-in-ethereum):

> In general, we can divide node software into two types: full nodes and light(weight) nodes. Full nodes verify block that is broadcast onto the network. That is, they ensure that the transactions contained in the blocks (and the blocks themselves) follow the rules defined in the Ethereum specifications. They maintain the current state of the network (as defined according to the Ethereum specifications).
>
> Transactions and blocks that do not follow the rules are not used to determine the current state of the Ethereum network. For example, if A tries to send 100 ether to B but A has 0 ethers and a block includes this transaction, the full nodes will realize this does not follow the rules of Ethereum and reject that block as invalid. In particular, the execution of smart contracts is an example of a transaction. Whenever a smart contract is used in a transaction (e.g., sending ERC-20 tokens), all full nodes will have to run all the instructions to ensure that they arrive at the correct, agreed-upon next state of the blockchain.
>
> There are multiple ways of arriving at the same state. For example, if A had 101 ether and gave a hundred of them to B in one transaction paying 1 ether for gas, the end result would be the same as if A sent 100 transactions of 1 ether each to B paying 0.01 ether per transaction (ignoring who received the transaction fees). To know if B is now allowed to send 100 ether, it is sufficient to know what B’s current balance is. Full nodes that preserve the entire history of transactions are known as full archiving nodes. These must exist on the network for it to be healthy.
>
> Nodes may also opt to discard old data; if B wants to send 100 ether to C, it doesn’t matter how the ether was obtained, only that B’s account contains 100 ether. Light nodes, in contrast, do not verify every block or transaction and may not have a copy of the current blockchain state. They rely on full nodes to provide them with missing details (or simply lack particular functionality). The advantage of light nodes is that they can get up and running much more quickly, can run on more computationally/memory constrained devices, and don’t eat up nearly as much storage. On the downside, there is an element of trust in other nodes (it varies based on client and probabilistic methods/heuristics can be used to reduce risk). Some full clients include features to have faster syncs (e.g., Parity’s warp sync).

## Installing Geth

The installation instructions for Geth on various platforms (Windows, macOS, Linux) can be found [here](https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum). The list is quite comprehensive and kept up to date, so I won’t go over it in the article.

## Running Geth

In order to spin up a Geth node, the only thing you need to do is go to your terminal window and run `geth`. When you do it, you should get an output similar to this:
