
# OpenZeppelin Library

One of the coolest tools in the toolset of an Ethereum developer is OpenZeppelin’s library. It’s a framework consisting of many Solidity code patterns and smart contract modules, written in a secure way. The authors are Solidity auditors and consultants themselves, and you can [read about a third-party audit of these modules here](https://blog.zeppelin.solutions/external-audit-of-openzeppelin-2ea50404ba7b). Manuel Araoz from Zeppelin Solutions, an Argentinian company behind OpenZeppelin, [outlines](https://blog.zeppelin.solutions/onward-with-ethereum-smart-contract-security-97a827e47702) the main Solidity security patterns and considerations.

OpenZeppelin is establishing itself as an industry standard for reusable and secure open source (MIT) base of Solidity code, which [can easily be deployed using Truffle](https://blog.zeppelin.solutions/how-to-create-token-and-initial-coin-offering-contracts-using-truffle-openzeppelin-1b7a5dae99b6). It consists of smart contracts which, once installed via `npm`, can be easily imported and used in our contracts.

The Truffle Framework [published a tutorial for using OpenZeppelin with Truffle and Ganache](http://truffleframework.com/tutorials/robust-smart-contracts-with-openzeppelin).

These contracts are meant to be imported and their methods are meant to be overridden, as needed. The files shouldn’t be modified in themselves.

## ICO Patterns

OpenZeppelin’s library contains a set of contracts for publishing tokens on the Ethereum platform — for [ERC20](https://en.wikipedia.org/wiki/ERC20) tokens, including a `BasicToken` contract, `BurnableToken`, `CappedToken`. This is a mintable token with a fixed cap, `MintableToken`, `PausableToken`, with which token transfers can be paused. Then there is `TokenVesting`, a *contract that can release its token balance gradually like a typical vesting scheme, with a cliff and vesting period*, and more.

There’s also [set of contracts for ERC721](https://openzeppelin.org/api/docs/token_ERC721_ERC721Token.html) tokens — or non-fungible, unique tokens of the CryptoKitties type.

[ERC827 tokens](https://github.com/ethereum/EIPs/issues/827) contracts, standard for sending data along with transacted tokens, are [also included](https://openzeppelin.org/api/docs/token_ERC827_ERC827.html).

There’s also a set of *[crowdsale contracts](https://openzeppelin.org/api/docs/crowdsale_Crowdsale.html)* — contracts for conducting Initial Coin Offerings. These can [log purchases](https://openzeppelin.org/api/docs/crowdsale_Crowdsale.html#TokenPurchase), [deliver/emit tokens](https://openzeppelin.org/api/docs/crowdsale_Crowdsale.html#_deliverTokens) to buyers, [forward ETH funds](https://openzeppelin.org/api/docs/crowdsale_Crowdsale.html#_forwardFunds). There are functions for validating and processing token purchases.

The [FinalizableCrowdsale](https://openzeppelin.org/api/docs/crowdsale_distribution_FinalizableCrowdsale.html) contract provides for execting some logic post-sale. [PostDeliveryCrowdsale](https://openzeppelin.org/api/docs/crowdsale_distribution_PostDeliveryCrowdsale.html) allows freezing of withdrawals until the end of the crowdsale. [RefundableCrowdsale](https://openzeppelin.org/api/docs/crowdsale_distribution_RefundableCrowdsale.html) is an *extension of the Crowdsale contract that adds a funding goal, and the possibility of users getting a refund if the goal is not met*.

[Destructible contracts](https://openzeppelin.org/api/docs/lifecycle_Destructible.html) can be destroyed by the owner, and have all the funds sent to the owner. There are also [contracts for implementing *pausability* to child contracts](https://openzeppelin.org/api/docs/lifecycle_Pausable.html).

OpenZeppelin provides many helpers and utilities for conducting ICOs — like a [contract which enables recovery of ERC20 tokens](https://openzeppelin.org/api/docs/ownership_CanReclaimToken.html) mistakenly sent to an ICO address instead of ETH. [A heritable contract](https://openzeppelin.org/api/docs/ownership_Heritable.html) provides for transferring of ownership to another owner under certain circumstances. The [Ownable contract](https://openzeppelin.org/api/docs/ownership_Ownable.html) has an owner address, and provides basic authorization/permissions and transferring of ownership.

The [RBAC contract](https://openzeppelin.org/api/docs/ownership_rbac_RBAC.html) provides utilities for role-based access control. We can assign different roles to different addresses, with an unlimited number of roles.

Zeppelin also provides a sample crowdsale starter Truffle project which hasn’t been audited yet, so it’s best used as an introduction to using OpenZeppelin. It makes it easy to start off with a crowdsale and a token fast.

## ZeppelinOS

![ZeppelinOS diagram](images/00037.jpeg)

[ZeppelinOS](https://zeppelinos.org/) is *an open-source, decentralized platform of tools and services on top of the EVM to develop and manage smart contract applications securely*.

In effect, this is a kind of middleware layer on top of EVM, which would be a step further than the current OpenZeppelin framework. What Zeppelin Solutions promise here is *enabling developers to opt-in to mutability for their deployed code through [upgradeability patterns](https://blog.zeppelinos.org/proxy-patterns/)*. Those who write smart contracts for the EVM know that one of the concerns/restrictions is immutability of deployed contracts: once on the blockchain, contracts cannot be changed. That is one of the things that make the promise of ZeppelinOS interesting.

Up until now, in order to “update” a contract one would have to deploy two contracts — one as a proxy with the interface, and the other as the implementation. The proxy’s functions would be called, forwarding requests to the implementation. Then, if a change was needed, the implementation is switched out in the proxy (another implementation is retargeted, and optionally the original one is killed off with a `suicide` function) and the new implementation seamlessly activates.

We are waiting to see the future adoption of ZeppelinOS by the community. Zeppelin Solutions are already namedropping some non-trivial players like OpenBazaar, district0x, storj.io as some who are using ZeppelinOS.

## Truffle Boxes

The [Truffle Framework](http://truffleframework.com) is a development environment, testing framework and asset pipeline for Ethereum. It’s the most complete set of tools, with the most traction among the Ethereum developers. Truffle’s ecosystem includes a number of [Truffle boxes](http://truffleframework.com/boxes/) — boilerplates that include front-end JavaScript code, Solidity contracts and workflow utilities like a boilerplate webpack project with its toolset — migrations, tests, build pipeline etc. Truffle Boxes can contain entire starter dapps.

Some of the officially supported boxes are:

*   **Drizzle**: a [set of React/Redux-based front-end libraries](http://truffleframework.com/boxes/drizzle) that make creation of dapp front ends easier.
*   **React box**: a [bare-bones app](http://truffleframework.com/boxes/react) to start interacting with smart contracts from a React, front-end application.
*   **[React Auth box](http://truffleframework.com/boxes/react-auth)**: brings a set of components needed for authentication powered by smart contracts.
*   **[React-Uport](http://truffleframework.com/boxes/react-uport)**: this authentication box connects the front end with the UPort blockchain authentication system.
*   Then there’s the [webpack project boilerplate](http://truffleframework.com/boxes/webpack) box we mentioned before.

Community-created boxes also bring along boilerplates for [integration of contracts with mobile apps / Status IM](http://truffleframework.com/boxes/status), or provide Angular and Vue.js boilerplates, etc.

These boxes are integrated with Truffle, so we get started with them by running commands like `truffle unbox react` — which will download the *React* box and install its dependencies locally.
