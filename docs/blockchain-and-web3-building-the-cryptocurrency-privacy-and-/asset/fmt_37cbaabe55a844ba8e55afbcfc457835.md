
# After Bitcoin: Altcoins and Ethereum

After bitcoin, many of the additional cryptocurrencies – also called "altcoins" – were created to address certain gaps or inefficiencies with bitcoin, and they are available through various networks. Popular altcoins include Dash, Litecoin, and XRP (offered through Ripple). Of all the alternative cryptocurrency networks, Ethereum is most popular (see [Figure 3.4](#c03.xhtml#c03-fig-0004)). It is an open-source platform that allows users to build and launch decentralized applications, including cryptocurrencies or digital ledgers. Users must spend a specific digital currency, ether, to run applications on Ethereum. Ether can also serve as an alternative to regular money, but its primary purpose is to facilitate Ethereum operations.

## Blockchain as a Distributed Ledger

As shown by the bitcoin section, blockchain is a distributed ledger, or database, shared across a public or private computing network. Each computer node in the network holds a copy of the ledger, so there is no single point of failure. Every piece of information is mathematically encrypted and added as a new "block" to the chain of historical records. Various consensus protocols are used to validate a new block with other participants before it can be added to the chain. This prevents fraud or double spending without requiring a central authority.

![Figure 3.4 Market Cap of Major Cryptocurrencies (2013–2022) Source: Forbes (2021, Nov 30), CoinMarketCap (2014–2022, Nov 30 for 2014–2021, Jan 30 for 2022), Statista (2013) Notes: Polkadot was launched in May 2020, Solann Mar 2020, USDC May 2018, Binance Jul 2017, Cardano Sept 2017, Ethereum Jul 2015, Tether Jul 2014, Dogecoin Dec 2013. Data is not available prior to their founding date](images/c03f004.png)

**[Figure 3.4](#c03.xhtml#R_c03-fig-0004) Market Cap of Major Cryptocurrencies (2013–2022)** Source: Forbes (2021, Nov 30), CoinMarketCap (2014–2022, Nov 30 for 2014–2021, Jan 30 for 2022), Statista (2013) Notes: Polkadot was launched in May 2020, Solann Mar 2020, USDC May 2018, Binance Jul 2017, Cardano Sept 2017, Ethereum Jul 2015, Tether Jul 2014, Dogecoin Dec 2013. Data is not available prior to their founding date

## Smart Contracts

Represented by Ethereum, the blockchain ledger can also be programmed with "smart contracts," a set of conditions recorded on the blockchain, so that transactions automatically trigger when the conditions are met. For example, smart contracts could be used to automate insurance-claim payouts. It allows financial and other assets to be exchanged using computer code with no attorney or escrow agent involved. (As will be discussed in [Chapter 8](#c08.xhtml), smart contracts themselves are a new type of programming, and it takes careful diligence and review to ensure secure, gas-efficient smart contracts that reduce the risk of vulnerabilities, which we cover in our section on smart contract security.)

## Ethereum and the EVM

In 2014, Ethereum came in with a new proposition for building decentralized applications. There would be a single blockchain where people would be able to deploy any kind of program. Ethereum achieved this by turning the `Application` layer into a virtual machine called the `Ethereum Virtual Machine (EVM)`. This virtual machine was able to process programs called `smart contracts` that any developer could deploy to the Ethereum blockchain in a permissionless fashion. This new approach allowed thousands of developers to start building decentralized applications (dApps).

A smart contract is simply a program that runs on the Ethereum blockchain. It's a collection of code (its functions) and data (its state) that resides at a specific address on the Ethereum blockchain. At a very basic level, a smart contract can be viewed as a sort of vending machine: a script that, when called with certain parameters, performs some actions or computation if certain conditions are satisfied. For example, a simple vendor smart contract could create and assign ownership of a digital asset if the caller sends ether (ETH) to a specific recipient.

Smart contracts are a type of Ethereum account, where accounts are defined as entities in the network that can hold a balance and send transactions. This means they have a monetary value balance, and they can send transactions over the network. However, they are not controlled by a user; instead they are deployed to the network and run as programmed. User accounts can then interact with a smart contract by submitting transactions that execute a function defined on the smart contract. Smart contracts can define rules, like a regular contract, and automatically enforce them via the code. Smart contracts cannot be deleted by default, and interactions with them are irreversible.

## Consensus and Execution

Ethereum currently uses a `PoW` consensus mechanism. `EVM` is essentially a single, canonical computer whose state everyone on the Ethereum network agrees on. Everyone who participates in the Ethereum network (every Ethereum node) keeps a copy of the state of this computer. Additionally, any participant can broadcast a request for this computer to perform arbitrary computation. Whenever such a request is broadcast, other participants on the network verify, validate, and carry out ("execute") the computation. This execution causes a state change in the `EVM`, which is committed and propagated throughout the entire network.

Requests for computation are called transaction requests; the record of all transactions and the `EVM`'s present state gets stored on the blockchain, which in turn is stored and agreed on by all nodes. Any participant who broadcasts a transaction request must also offer some amount of ether to the network as a bounty. This bounty will be awarded to whoever eventually does the work of verifying the transaction, executing it, committing it to the blockchain, and broadcasting it to the network. The amount of ether paid corresponds to the time required to do the computation.

## Gas Fees

The ether cryptocurrency supports a pricing mechanism for Ethereum's computing power. When users want to make a transaction, they must pay ether to have their transaction recognized on the blockchain. These usage costs are known as gas fees, and the gas fee depends on the amount of computing power required to execute the transaction and the network-wide demand for computing power at the time. Because of the boom of crypto transactions in 2021, the Ethereum network was pushed to its full capacity, and the gas fees on Ethereum skyrocketed. As Web3 evolves, the demand for crypto infrastructure also increases.

# Bitcoin versus Web3 (Pure Decentralization vs. Modified Decentralization)

As illustrated, blockchain tokenization and smart contract techniques can act as a form of advanced software that ensures that what has been agreed is executed upon, enabling the recognition of data rights, risks, and rewards. In the creation of economic value models, blockchain may act as an enabler in market-based mechanisms to attach value and permissions to the data.

But which crypto token will be *the currency* of the Metaverse? Is this about a war between Bitcoin and Ethereum? No doubt, bitcoin is the most recognized, first-ever digital asset, but there are hundreds and even thousands of other digital assets in the ecosystem. But there is also concern regarding bitcoin that as the first digital asset, it may be vulnerable to innovative destruction from competitors like Ethereum (such as the story of MySpace and Facebook).

In other words, is there going to be one clear winner that is crowned as the main metaverse currency? Or is it likely that there will always be a coexistence of multiple cryptocurrencies, each serving slightly, or entirely, different functions?
