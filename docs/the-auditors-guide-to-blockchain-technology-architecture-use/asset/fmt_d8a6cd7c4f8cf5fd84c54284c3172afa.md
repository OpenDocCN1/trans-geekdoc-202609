
*   **Oracles**: These off-chain data repositories act as a link between blockchains and the rest of the world. Off-chain data are inaccessible to blockchains and smart contracts; however, to carry out certain contractual arrangements, it is essential to have relevant details from the outside world. This is where blockchain oracles come in, as they provide connections between off-chain and on-chain information. Oracles are important in the blockchain ecosystem because they expand the range of smart contracts that can be used. Often, smart contracts would be useless without the updated and independent data provided by oracles. A blockchain oracle is the layer that queries, verifies and authenticates external data sources before relaying the information. Price details, the effective completion of a payment or the temperature measured by a sensor are all examples of data transmitted by oracles. The smart contract must be invoked, and network resources must be expended, in order to call data from the outside world. Some oracles may also send information back to external sources, in addition to relaying it to smart contracts.

Tools make the process of developing blockchain apps easier and aid in the creation of software applications. Thus, they contribute to the expansion of our blockchain awareness [[30](#ch17.xhtml#r343), [38](#ch17.xhtml#r351)].

### Table 9.3 Tools Download Source Links

| **Tool** | **Source** |
| --- | --- |
| **Solidity** | [https://docs.soliditylang.org/en/v0.7.4/](https://docs.soliditylang.org) |
| **Truffle** | [https://truffleframework.com/](https://truffleframework.com) |
| **Oracle** | [https://developer.oracle.com/ca-en/open-source/](https://developer.oracle.com) |
| **Remix** | [https://remix.ethereum.org](https://remix.ethereum.org) |
| **IPFS** | [https://ipfs.io/](https://ipfs.io) |
| **Ganache** | [https://www.trufflesuite.com/ganache](https://www.trufflesuite.com) |
| **Mist** | [https://github.com/ethereum/mist/releases](https://github.com) |
| **Geth** | [https://github.com/ethereum/go-ethereum](https://github.com) |
| **MetaMask** | [https://metamask.io/](https://metamask.io) |
| **Ether.js** | [https://github.com/ethers-io/ethers.js/](https://github.com) |
| **Infura** | [Https://infura.io](Https://infura.io) |

## Integrated Development Environment

According to Lyn, Integrated Development Environment (IDE) is an application software providing application developers a single platform to design, test and debug computer programs. The process of eradicating the errors or bugs is known as debugging and is achieved with the help of debugging tools. Debugging creates an environment which makes it easy to create or develop eminent software applications. Text editor, terminal, debugging tools and code snippets are the tools generally incorporated in the Integrated Development Environment [[29](#ch17.xhtml#r342)].

IDE’s may even make use of either compilation or interpreter tools, or both, thus providing an atmosphere that is conducive to software growth. The modern IDEs come with object explorer, class browser and class hierarchy diagram features [[9](#ch17.xhtml#r322)].

Some of the IDE’s work on JavaScript or Python platforms [[45](#ch17.xhtml#r358)]. IDE is a single graphical user interface with debugger, local build automation and source code editor as its pillar. For developer’s use, local build automation uses simple redundant tasks. With extensive capabilities such as syntax highlighting, the source code aids in the creation of software code [[19](#ch17.xhtml#r332)].

IDE tools increase the productivity and capability to perform tasks such as continuous compilation, automated testing, integrated debugging, refactoring and navigation among classes. Eclipse and visual studio also work with IDE. While using visual basics, IDE developers can set breakpoints or clear breakpoints just next to a line of code. Furthermore, in the immediate window at the bottom of the IDE, the developer can use visual basics statements. Hence, the focus of an IDE is to provide comprehensive facilities to software programmers in software application development [[41](#ch17.xhtml#r354)].

## Good Practices for Blockchain Development

*   **Use caution calling external contracts, favor own**: It is strongly advisable to favor in-house contracts over those created by a third party, as much as possible. In other words, all contracts developed in-house have already been subjected to the same level of security, review, testing and acceptance criteria as the rest of the solution, so they will comply with the same quality and safety standards set for the rest of solution components. Adequate audit and testing time and effort in order to carefully review the source code of any external contracts should be allocated. When using a third-party contract, it is essential to ensure there are no inherent security flaws created by the third party.

*   **Handle all errors; catch all exceptions in external calls**: In smart contracts, functions must be surrounded by `try/catch` statements and every exception must be handled explicitly, no matter how unlikely it appears to be. All exceptions that aren’t explicitly caught and managed should be thrown, and exception should be raised to its calling function or contract. Contracts should try to gracefully address exceptions and attempt to move forward without user intervention. If this is not possible, an error message should be sent with suggestions regarding how to resolve the error. As mentioned, when dealing with external contracts, there should be no assumption that another developer has taken the same precautions. Users will view an application as having a defect if they receive any unexpected or cryptic errors [[8](#ch17.xhtml#r321)].

*   **Push versus pull payments**: A push-based financial transaction happens when a seller uses an automated transaction to electronically remove or add funds from or to a customer’s account. Subscription or utilities payment plans that perform automatic monthly or annual debits are an example of a push-based financial transaction. In a blockchain environment, pull payments offer an important benefit. To further explain, a pull payment should divide the payment process into two phases. The first step should be a notification informing the user that there are available funds waiting to be pulled from a smart contract. In the second step the payee should act on the notification in order to pull the available funds out of the payee’s correct wallet address. This methodology will help avoid issues with funds being sent to an incorrect wallet address which cannot be reversed, unlike traditional banking transactions [[7](#ch17.xhtml#r320), [12](#ch17.xhtml#r325), [32](#ch17.xhtml#r345), [35](#ch17.xhtml#r348), [43](#ch17.xhtml#r356)] ([Figures 9.1](#ch17.xhtml#f22) and [9.2](#ch17.xhtml#f23)).

    ![Figure 9.1 A push payment transaction. ¶ Source: [32].](html/images/9781032078243_C009_001.jpg)

    **Figure 9.1** A push payment transaction. ¶ Source: [[32](#ch17.xhtml#r345)].

    ![Figure 9.2 A pull payment transaction. ¶ Source: [32].](html/images/9781032078243_C009_002.jpg)

    **Figure 9.2** A pull payment transaction. ¶ Source: [[32](#ch17.xhtml#r345)].
