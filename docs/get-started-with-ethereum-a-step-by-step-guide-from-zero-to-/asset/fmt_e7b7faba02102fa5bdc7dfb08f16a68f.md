
# Add Your Badge Image to IPFS

Add your badge image to IPFS.

```bash
$ ipfs add badge-image.png
```

Running this command, you will receive a hash. This hash is your image address in IPFS. ![](Image00017.jpg)

## Pinning the Badge to a Remote IPFS Node

Pin your badge using a remote IPFS service.

```bash
ipfs pin remote add --service=pinata --name=badge-image.png QmZPxKJWqJTdudyaZUyf6uBzwwAT41QQyxhTHmMZWB9yx4
```

You will get a response indicating the file was pinned successfully ![](Image00018.jpg)

## Creating the Badge Metadata

Create the badge metadata json file.

```bash
touch badge-metadata.json
```

Open the file. Set the badge name. Set the badge description. Set the badge image address using an IPFS gateway.

```json
{
  "name": "My badge",
  "description": "My badge description",
  "image": "https://ipfs.io/ipfs/QmZPxKJWqJTdudyaZUyf6uBzwwAT41QQyxhTHmMZWB9yx4"
}
```

## Add Your Badge Metadata to IPFS

```bash
$ ipfs add badge-metadata.json
```

Pin your badge metadata using a remote IPFS service.

```bash
$ ipfs pin remote add --service=pinata --name=badge-metadata.json QmRzcwAtLWbeYqyaZUyf6uBzwwAT41QQyxhTHmMZWBfUTa
```

# Compiling the Smart Contract

Compile the contract using `truffle`.

```bash
$ truffle compile
```

# Migrating the Smart Contract

Migrate the contract to rinkeby network using `truffle`.

```bash
$ truffle migrate --network rinkeby
```

# Instantiating the Smart Contract

Instantiate the contract using `truffle console`.

```bash
$ truffle console --network rinkeby
truffle(rinkeby) let instance = await UniqueAsset.deployed()
```

# Awarding Badge to a Wallet

Call the method `getThePrice`. Enter your public ethereum address as a first parameter. Enter the IPFS address corresponding your badge metadata.

```bash
truffle(rinkeby) let result = await instance.awardItem("0x62761466bB3A3Da83B408B5F5fE00ac7b2a5A996","https://ipfs.io/ipfs/QmRzcwAtLWBeYqUx3ba1BkYKubSDLNTHCuiUB7WAmdfUTa")
```

# Checking Badge on Etherscan

Copy the deployed contract address ![](Image00019.jpg)

Go to [rinkeby.etherscan.io](https://www.google.com/url?q=https://rinkeby.etherscan.io/&sa=D&source=editors&ust=1624824293484000&usg=AOvVaw2X6oFOKB_p-6n7749VXd0B). Paste the contract address in the search bar ![](Image00020.jpg). Click on search icon. Now you can see that the contract was deployed successfully ![](Image00021.jpg). You can also realize that the last transaction made was for award a new item.

# Adding the NFT Token to Your Wallet

Open your MetaMask wallet on your mobile phone (collectibles are only available on mobile version). Click on “collectibles” ![](Image00022.jpg). Click on "add collectible". Paste the token contract address here (the same that you copied in the last section). Enter the token ID, as it is the first token you will enter 1 here. Click on "add". Wait for a few seconds. Now the NFT token was added! ![](Image00023.jpg). Click on “UniqueAsset”. Now you can see all the badges that you earn ![](Image00024.jpg). Click on “My Badge”. You can see the badge details now! Also, you have a send button so that you can send it to another wallet ![](Image00025.jpg). That’s it, you just created your first NFT token!

# Ether Faucets

## Get Test Ether From Faucet on Ropsten Network

This ethereum test faucet drips 1 ether every 5 seconds. You can use it to test smart contracts on the Ropsten network with no need to use real ether for this purpose (even because eth from the mainnet is not valid in ropsten and vice versa). You have a request limit of 1 eth for every 24 hours in order to avoid network spam. Ether in a test network has no real value except for testing purposes in smart contracts development.

[https://faucet.ropsten.be](https://www.google.com/url?q=https://faucet.ropsten.be&sa=D&source=editors&ust=1624824293488000&usg=AOvVaw39Zbse6NzzonrzBxkJmjX_)

[View on YouTube](https://www.google.com/url?q=https://youtu.be/rSL3kP13gOI&sa=D&source=editors&ust=1624824293489000&usg=AOvVaw1VYd0meZ7Ibg4mR-22rteP)

| ESTIMATED TIME | 2 minutes |
| --- | --- |

| PRE REQUIREMENTS | |
| --- | --- |

| [Install and Setup MetaMask Wallet](#text00008.html#toc20_MetaMask) | |

## Accessing the Faucet

Go to [https://faucet.ropsten.be](https://www.google.com/url?q=https://faucet.ropsten.be&sa=D&source=editors&ust=1624824293492000&usg=AOvVaw0g-iC5yFF7nOgZhKww_POb). Copy your wallet address (make sure the network selected is Ropsten). Paste your contract address in the form field. Click on "send me test ether". Waiting for the transaction. Click on the "transaction hash" (open in a new window). Wait for the transaction be completed. The transaction was successfully completed. Go to your MetaMask wallet, you have now 1 ether!

## Get Test Ether From Faucet on Rinkeby Testnet

This Ether faucet is running on the Rinkeby network. To prevent malicious actors from exhausting all available funds or accumulating enough Ether to mount long running spam attacks, requests are tied to common 3rd party social network accounts. Anyone having a Twitter or Facebook account may request funds within the permitted limits.

[https://faucet.rinkeby.io](https://www.google.com/url?q=https://faucet.rinkeby.io&sa=D&source=editors&ust=1624824293493000&usg=AOvVaw35VO63U2Ccimtq0olysaU4)

[View on YouTube](https://www.google.com/url?q=https://youtu.be/iJBpiBqEMtA&sa=D&source=editors&ust=1624824293494000&usg=AOvVaw18LCPDv2bcqiYJTsoSKFO_)

| ESTIMATED TIME | 2 minutes |
| --- | --- |

## Preparing for Funding

Open your Metamask wallet. Copy you wallet address to clipboard. Go to your twitter account. Paste your wallet address. Click on your tweet. Copy your tweet address (the url in the address bar).

## Funding Your Wallet

Go to [https://faucet.rinkeby.io](https://www.google.com/url?q=https://faucet.rinkeby.io&sa=D&source=editors&ust=1624824293496000&usg=AOvVaw1OGB41VLbzKTklNDl_FAnP). Paste your tweet address in the text field. Click on “Give me Ether”. Select on of the options available (for example: 3 Ethers / 8 hours). The request will be funding in a few seconds ![](Image00026.jpg).

## Checking Your Wallet

Wait a few moments and check your Metamask wallet. You will get 3 ether in your wallet account!

# IPFS - InterPlanetary File System

## Create Your IPFS Node

The InterPlanetary File System (IPFS) is a protocol and peer-to-peer network for storing and sharing data in a distributed file system. IPFS uses content-addressing to uniquely identify each file in a global namespace connecting all computing devices.

[https://ipfs.io](https://www.google.com/url?q=https://ipfs.io&sa=D&source=editors&ust=1624824293497000&usg=AOvVaw3fUJS9jf6wVMTjDheE9ywi)

[View on YouTube](https://www.google.com/url?q=https://youtu.be/dFWpGn73BBM&sa=D&source=editors&ust=1624824293497000&usg=AOvVaw04WtS08v6b6m1gv56Z6Lqt)

| ESTIMATED TIME | 3 minutes |
| --- | --- |

## Command Overview

| Command | Description |
| --- | --- |
| `choco install go-ipfs` | Install the IPFS implementation in go. |
| `ipfs init` | Initialize the local IPFS repository. |
| `ipfs daemon` | Start IPFS local server on 127.0.0.1:5001. |
| `ipfs cat <hash>` | View IPFS file content. |
| `ipfs swarm peers` | Show the peers who are directly connected to your node. |

## Installing the Node

VS CODE - BASH TERMINAL

```bash
$ choco install go-ipfs
```

## Configuring the Node

VS CODE - BASH TERMINAL

```bash
$ ipfs init
$ ipfs daemon
```

## Testing the Node

VS CODE - BASH TERMINAL

```bash
$ ipfs cat "hash"
$ ipfs swarm peers
```

![](Image00027.jpg)

## Exploring Your IPFS Node

Copy the WebUI link. Go to browser and paste the link. Your node is connected to IPFS! Click on "files", no files here yet! Click on "explore". Click on "peers". This are the peers that you are connected. Click on "settings". You can see your node settings here.
