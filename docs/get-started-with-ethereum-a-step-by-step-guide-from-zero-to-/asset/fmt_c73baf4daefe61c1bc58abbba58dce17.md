

# How to Get Started With Ethereum

## About this Book

Get Started With Ethereum This book is a step by step guide for everyone who wants to start as an Ethereum developer. It was designed for those who have never programmed anything in blockchain and want to get started. I will cover everything from installing basic requirements to writing, testing and deploying smart contracts. I will also cover topics like IPFS, ENS, Chainlink, Truffle, Ganache, OpenZeppelin, Pinata, Fleek, Infura, Metamask, Opensea, among others. You will receive free updates as new content becomes available. Enjoy!

## About the Author

Davi Pedro Bauer I have 20+ years of experience in the IT market with experience in analysis and systems development. I've been working with agile methods since 2009, where I participated in agile adoption programs in multidisciplinary teams, supporting the implementation of processes and practices such as Scrum and Kanban, as well as the launch of new digital products for web and mobile platforms. Since 2016, I have been studying on topics related to Blockchain, such as cryptocurrencies, asset tokenization, smart contracts and distributed applications (DApps) and since 2019 I’ve been working with DevSecOps from code to infrastructure. Follow me on [Linkedin](https://www.google.com/url?q=https://linkedin.com/in/davibauer&sa=D&source=editors&ust=1624824293293000&usg=AOvVaw1kyQQ-tE9h-0igpZrajywT) Follow me on [Github](https://www.google.com/url?q=https://github.com/davibauer&sa=D&source=editors&ust=1624824293293000&usg=AOvVaw2BImFRPjY1W5nY0Z1pHovP) [https://leanpub.com/u/davibauer](https://www.google.com/url?q=https://leanpub.com/u/davibauer&sa=D&source=editors&ust=1624824293293000&usg=AOvVaw3T7Ob8Mtlbqf-YNKMNMlKm)

## Pre requirements

### Install Blockchain Dev Kit Extension on VS Code

The Blockchain Developer Kit was built for both new users to Ethereum, but not get in the way for those familiar with the process. One of the primary goals is to help users create a project structure for these smart contracts, help in the compilation and building of these assets, deployment of these assets to blockchain endpoints as well as debugging of these contracts. [View on YouTube](https://www.google.com/url?q=https://www.youtube.com/watch?v%3DWIUppKQhtKk&sa=D&source=editors&ust=1624824293295000&usg=AOvVaw1YBFUmb_Tpv7XsKpH7VvtV)

| ESTIMATED TIME  || 1 minute  |

| --- | --- |

### Installing the extension

Go to Extensions. Search for “blockchain development kit for ethereum”. Click on the extension created by Microsoft, usually will be the first one. ![](Image00002.jpg)Click on “Install”. ![](Image00003.jpg)Wait for the installation complete That’s done!

### Install Truffle

Truffle is a development environment, testing framework and asset pipeline for Ethereum, aiming to make life as an Ethereum developer easier. [View on YouTube](https://www.google.com/url?q=https://www.youtube.com/watch?v%3DmE3_3wL5-jI&sa=D&source=editors&ust=1624824293298000&usg=AOvVaw2cFLaiP5gJqszRcJiOlcWT)

| ESTIMATED TIME  || 2 minutes  |

| --- | --- |

### Installing Truffle

Go to the terminal windows VS CODE - BASH TERMINAL

| TERMINAL  |

| --- |

| `$ npm install -g truffle` |

### Checking Truffle installation

Check if the installation was done successfully VS CODE - BASH TERMINAL

| TERMINAL  |

| --- |

| `$ truffle` |

![](Image00004.jpg)

### Install Ganache CLI

Ganache is a personal blockchain for rapid Ethereum and Corda distributed application development. You can use Ganache across the entire development cycle; enabling you to develop, deploy, and test your dApps in a safe and deterministic environment. [View on YouTube](https://www.google.com/url?q=https://www.youtube.com/watch?v%3DfbQH6pzfXig&sa=D&source=editors&ust=1624824293302000&usg=AOvVaw0QoYm6VV7ZG3XndRnEaLWT)

| ESTIMATED TIME  || 2 minutes  |

| --- | --- |

| COMMAND OVERVIEW  |

| --- |

| `npm install` |

| This command installs a package and any packages that it depends on.  |

| `ganache-cli` |

| Start the ganache development blockchain on 127.0.0.1:8545.  |

### Installing Ganache

Go to the terminal windows VS CODE - BASH TERMINAL

| TERMINAL  |

| --- |

| `npm install -g ganache-cli` |

### Starting Ganache locally

Start Ganache CLI on 127.0.0.1:8545 VS CODE - BASH TERMINAL

| TERMINAL  |

| --- |

| `ganache-cli` |

It will also generate 10 accounts with their respectives public and private keys so that you can use it for test purposes. ![](Image00005.jpg)

## MetaMask Install and Setup MetaMask Wallet

MetaMask is an extension for accessing Ethereum enabled distributed applications, or "Dapps" in your browser. The extension injects the Ethereum web3 API into every website's javascript context, so that dApps can read from the blockchain. MetaMask also lets the user create and manage their own identities (via private keys, local client wallet and hardware wallets like Trezor), so when a Dapp wants to perform a transaction and write to the blockchain, the user gets a secure interface to review the transaction, before approving or rejecting it. [View on YouTube](https://www.google.com/url?q=https://youtu.be/Bj6IozLyVxw&sa=D&source=editors&ust=1624824293310000&usg=AOvVaw35Z4w76gWuYK2yAD_VK7yB)

| ESTIMATED TIME  || 2 minutes  |

| --- | --- |

### Installing the wallet

Go to metamask.io Click on "Install MetaMask" Click on "Add to Brave" or your browser name Click on "Add extension" Click on "Get Started"

### Configuring the wallet

Click on "Create a Wallet" Click on "No Thanks" (but if you prefer, click on "I Agree" instead) Define the password that you will use to open your wallet Confirm the password Agree to the terms of use Click on "Create" Now you can backup your secret backup phrase (you can also do it later) For now, click on "Remind me later" Your wallet is done!

### Accessing your wallet

Click on extensions and pin MetaMask to your bar Click on MetaMask icon, your wallet will be shown

### Discovering your wallet address

Click on the three dots on the upper right side and then on "Account details" You can see your wallet address in hash format and in a QR code format You can also copy your wallet address by clicking on account name That's all!

## Infura Create an Account on Infura

Infura provides the tools and infrastructure that allow developers to easily take their blockchain application from testing to scaled deployment - with simple, reliable access to Ethereum and IPFS. [View on YouTube](https://www.google.com/url?q=https://www.youtube.com/watch?v%3DNcKMBgNsBuw&sa=D&source=editors&ust=1624824293313000&usg=AOvVaw2CHIrHiVW_pwOTZNT4B1iC)

| ESTIMATED TIME  || 2 minutes  |

| --- | --- |

### Creating a new account

Go to [infura.io](https://www.google.com/url?q=https://infura.io/&sa=D&source=editors&ust=1624824293315000&usg=AOvVaw2qnN-ZVazIFCaJz8pZcX3o) Click on “Get Started for Free”. Enter your email and password Click on “Sign Up” A verification email will be send to your address Check your email and confirm your account by clicking the verification link After that, you will be redirected to your dashboard Click on “Ethereum” tab on the left side menu ![](Image00006.jpg)Now your account was created and you can start setting up a new project. ![](Image00007.jpg)

### Setting up your infura project

Go to infura.io Access your dashboard Click on "ethereum" Click on "create a project" Define the project name You can connect with different testnets and also to the mainnet Save changes ![](Image00008.jpg)

