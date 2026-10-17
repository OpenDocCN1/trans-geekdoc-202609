
From here, your transaction is added to a memory pool of

pending transactions waiting to be added to the blockchain —

all without disclosing your private key `K`

\= {7}!

priv

If a malicious user tries to withdraw funds from your account,

they can’t do so without your private key. Suppose that the

malicious user wrongly guesses that your private key is equal to

{8} (instead of the true K

\= {7}). Here’s what would

priv

happen:

1\. To sign the 16 ETH transfer request, the malicious user now

takes 16 to the power of 8 (instead of 7) and then divides by

33 (using the information in your public key K = {3, 33}).

pub

The remainder here is now 4, which is the digital signature

that is broadcast to the network.

2\. The malicious user submits the transaction request along

with the digital signature {16, 4}, claiming that they’re the

rightful owner and requesting to withdraw 16 ETH, with a

digital signature proof of 4.

3\. To verify, validators take 4 to the power of 3 and then divide

by 33 (again, using the known public key K = {3, 33}).

pub

The remainder of the division is 31, which doesn’t equal the

16 ETH transfer request.

Thus, this fraudulent transaction is rejected, demonstrating

the beauty of digital signatures.

Of course, this simple example doesn’t fully convey the digital

signing and verification process that Ethereum uses. Still, it

shows how key pairs and digital signatures operate to credibly

demonstrate that you’re the rightful owner of an account with-

out ever disclosing your private keys.

Discovering Contract Accounts

Contract accounts, which are often simply referred to as contracts or smart contracts, are designed to store data and code at a designated contract address on the EVM. In essence, when you deploy a software program to the EVM, you create a contract account that houses this program.

CHAPTER 7 Creating an Ethereum Account  123

Contract accounts (contracts) differ from externally owned accounts (accounts) in several key ways:

» Contracts will cost you ETH. The creation of a contract account is itself a transaction that must be initiated from an externally owned account.

» Contracts cannot initiate transactions. Once created, contract accounts lie dormant until triggered by a transaction. A contract account can be called by another contract account, but this string of calls must ultimately originate from an externally owned account.

» Contracts have no private keys. Contract accounts have only public addresses, which — like those of externally owned accounts — are also represented by a 42-digit hexadecimal number.

Naturally, because transactions cannot be initiated from a contract account, there’s no need for contract accounts to have private keys.

After a contract has been deployed to the EVM, it is public and anyone can access it. Anyone is free to use the functions embedded in the contract or to even access all its source code, which can be found on the public blockchain as follows:

1\. Go to [https://etherscan.io. ](https://etherscan.io/)

2\. In the text-based search bar in the upper-right corner, type the address of the contract you want to find.

3\. Click the Contract tab on the tab row across the top of the screen to see the contract’s source code, as shown in Figure 7-6.

The contract address is 0x1A79E50064C012639fB6fB6761E332Acf5Ba15d1

Although creating a contract account costs gas, after that contract account has been created, the creator pays no ongoing maintenance fees to keep the contract account up and running.

Instead, anyone who wants to use functions embedded in the contract must initiate a request from an externally owned account and pay for the appropriate amount of gas for that transaction.

124  PART 3  Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

![](images/00117.jpg)

FIGURE 7-6:

Finding a

contract’s

source

code.

Creating a contract account entails submitting a transaction that contains your code without specifying a destination address. In other words, you don’t simply create a contract account without purpose in the way that you might simply create an externally owned account, even if you don’t yet have a reason to use it.

The following list highlights important points about contract accounts (even though you aren’t ready to do a lot of these things just yet):

» To create a contract account, your smart-contract code should already be ready to go.

» From an externally owned account, submit an Ethereum transaction to the network containing your compiled code without specifying any recipients.

» Once validated and mined, your smart contract has its own public address on the Ethereum blockchain for future reference by anyone in the network.

Before you can create a contract account, you first need to follow the steps in the later section “Preparing Your Accounts (on MetaMask)” to set up your various (externally owned) accounts for different uses. After that, you must complete the steps of CHAPTER 7 Creating an Ethereum Account 125 setting up your development environment (see Chapter 8) before proceeding to finally deploying your first smart contract (see Chapter 9).

Knowing the Difference Between Public Networks and Private Environments

Public networks are permissionless and open to anyone who wants to participate without requiring permission from a central authority. Two categories of public networks are important to the Ethereum ecosystem:

» Mainnet: This main Ethereum network is the primary blockchain on which transactions of actual value occur and are memorialized. When someone talks about Ethereum, Mainnet is generally what they’re talking about. You need to use real, honest-to-goodness ETH to fuel transactions on Mainnet.

» Testnets: Test networks are available for developers to test various features before transacting on Mainnet. You get to use test-ETH — rather than the real thing — to fuel transactions on a testnet.

Even before playing around on a testnet, developers often test their code on a local development environment, which has the advantages of being faster and simpler.

Local development environments are private and provide an easy-and-safe sandbox where you can observe how your smart contracts might behave after they’re deployed. Sandboxes are safe because they’re isolated testing environments built for experimentation — the code in a sandbox isn’t live, so errors don’t cause real damage or network congestion.

126 PART 3 Developing Your Knowledge: A Step-by-Step Guide to Programming Your Own NFT

These local environments, such as Ganache (which we introduce in Chapter 8), simulate the Ethereum blockchain by providing a private blockchain with preseeded test accounts. Unlike in a public network, your transactions are automatically executed in order to make it easier to debug your contracts without having to wait for blocks to be mined via an onerous proof-of-work process. (See Chapter 6 for an explanation of proof of work.)

Test networks

Public testnets provide another practice environment closer to how the main Ethereum network functions. Unlike local development environments, testnets provide public blockchains that mostly follow the rules of the main Ethereum blockchain.

Testnets provide a gateway to Ethereum without the pain of wasting actual ETH to deploy test contracts that haven’t yet been fully debugged. You don’t use real ETH to fuel transactions on testnets — you use the respective test ETH native to the testnet in question.

Testnets come in two flavors:

» Proof of work: Only one testnet — the Ropsten Test Network — is based on a proof-of-work consensus protocol, making it the closest representation of the main Ethereum network.

We use the Ropsten Test Network in our step-by-step guide because it relies on proof of work, which, as we explain in
