
await `erc20FixedSupply.deployed()`;

return `assert.isTrue(true)`;

});

it("should return total supply of 1000", async function () {

const `instance = await erc20FixedSupply.deployed()`;

const `totalSupply = await instance.totalSupply()`;

`assert.equal(totalSupply, 1000)`;

});

});

Test using the following command.

| TERMINAL |

| --- |

| `$ truffle test --network development` |

The test will pass. Writing test asserting for the contract balance Add one more test to assert that the balance is correct after a new transfer is made between two accounts.

| ERC20FixedSupply.js |

| --- |

| 16 17 18 19 20 21 22 23 24 25 |

```javascript
it("should transfer 150 FIX", async function(){
    const instance = await erc20FixedSupply.deployed();
    await instance.transfer("account[1]", 150);
    const balanceAccount0 = await instance.balanceOf(accounts[0]);
    const balanceAccount1 = await instance.balanceOf(accounts[1]);
    assert.equal(balanceAccount0.toNumber(), 850);
    assert.equal(balanceAccount1.toNumber(), 150);
});
```

Execute the test again.

| TERMINAL |

| --- |

| `$ truffle test --network development` |

All tests will pass. ![](Image00015.jpg)Try to change some values like the account balance at line 23 and 24 and see how the results change from pass to fail.

## ERC721- Non-Fungible Tokens

### Create your art NFT using Ganache and OpenZeppelin

An NFT is a digital asset that represents real-world objects like art, music, in-game items and videos. In this video I'll show you how to create a NFT ERC 721 and deploy it to ethereum testnet network as well as how to add it to your metamask mobile wallet. [https://eips.ethereum.org/EIPS/eip-721](https://eips.ethereum.org/EIPS/eip-721) [View on YouTube](https://www.google.com/url?q=https://youtu.be/IFpU4TNwXec&sa=D&source=editors&ust=1624824293420000&usg=AOvVaw0LAiWMu-EocDqEhypxlgiG)

| ESTIMATED TIME | 15 minutes |

| --- | --- |

| PRE REQUIREMENTS |

| --- |

| [Install Truffle](#text00005.html#a2X3) |

| [Create an Account on Infura.io](#text00009.html#a2XG) |

| [Get Test Ether From Faucet on Rinkeby Network](#text00021.html#toc87_Get_Test_Ether_From_Faucet_on_Rinkeby_Testnet) |

| [Install and Setup MetaMask Wallet](#text00008.html#toc20_MetaMask) |

| COMMAND OVERVIEW |

| --- |

| `truffle init` |

| Initialize new and empty Ethereum project |

| `npm install` |

| This command installs a package and any packages that it depends on |

| `ipfs daemon` |

| Start IPFS local server on 127.0.0.1:5001 |

| `ipfs add <file>` |

| Add file to your IPFS local node |

| `ipfs pin remote add --service=pinata -name=<file> <hash>` |

| Pin your file to the remote IPFS pinning service |

| `truffle compile` |

| Compile contract source file |

| `truffle migrate` |

| Run migrations to deploy contracts |

| `truffle console` |

| A basic interactive console connecting to an Ethereum client |

### Creating the project

Create a new project using truffle

| TERMINAL |

| --- |

| `$ truffle init` |

### Install open zeppelin contracts

| TERMINAL |

| --- |

| `$ npm install @openzeppelin/contracts` |

### Create a new solidity smart contract

| TERMINAL |

| --- |

| `$ touch contracts/UniqueAsset.sol` |

Open the file Import ERC721 URI Storage extension Import Counters util Create a new class extending ERC721URIStorage Declare counters Declare the constructor passing the coin name and the code Create a new method for award item Inside the new method, increment the token Get the new token number Mint a new item Set the token URI

| UniqueAsset.sol | [View on GitHub](https://www.google.com/url?q=https://github.com/davibauer/blockchain/blob/master/nft/contracts/UniqueAsset.sol&sa=D&source=editors&ust=1624824293441000&usg=AOvVaw0kQm6OCdMH2KrrQpUMgQxn) |

| --- | --- |

| 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 |

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/utils/Counters.sol";

contract UniqueAsset is ERC721URIStorage {
    using Counters for Counters.Counter;
    Counters.Counter private _tokenIds;

    constructor() ERC721("UniqueAsset", "UNA") {}

    function awardItem(address recipient, string memory metadata) public returns (uint256) {
        _tokenIds.increment();
        uint256 newItemId = _tokenIds.current();
        _mint(recipient, newItemId);
        _setTokenURI(newItemId, metadata);
        return newItemId;
    }
}
```

### Create a new migration file

| TERMINAL |

| --- |

| `$ touch migrations/2_deploy_contracts.js` |

### Export the smart contract in the migration file

| 2_deploy_contracts.js | [View on GitHub](https://www.google.com/url?q=https://github.com/davibauer/blockchain/blob/master/nft/migrations/2_deploy_contracts.js&sa=D&source=editors&ust=1624824293449000&usg=AOvVaw10o1zZ2Ri74tBsK1M4YoGF) |

| --- | --- |

| 1 2 3 4 5 |

```javascript
const UniqueAsset = artifacts.require("UniqueAsset");

module.exports = function(deployer) {
    deployer.deploy(UniqueAsset);
}
```

### Configuring the wallet

Install the file system “fs” package

| TERMINAL |

| --- |

| `$ npm install fs` |

Install the wallet provider “hdwallet” package

| TERMINAL |

| --- |

| `$ npm install @truffle/hdwallet-provider@1.2.3` |

Open `truffle-config.js` file Uncomment the HDWalletProvider code section

| truffle-config.js |

| --- |

| 21 22 23 24 25 |

```javascript
const HDWalletProvider = require('@truffle/hdwallet-provider');
const infuraKey = 'fj4jll3k.....';
const fs = require('fs');
const mnemonic = fs.readFileSync(".secret").toString().trim();
```

Paste your Infura project id as a value for the variable `infuraKey` Configuring the network Uncomment the “ropsten” network section Change “ropsten” to “rinkeby” Change “ropsten” infura url to “rinkeby” Change “YOU-PROJECT-ID” to “${infuraKey}” Change the network_id to 42

| truffle-config.js |

| --- |

| 60 61 62 63 64 65 66 67 |

```javascript
rinkeby: {
    provider: () => new HDWalletProvider(mnemonic, `https://rinkeby.infura.io/v3/${infuraKey}`),
    network_id: 4,
    gas: 5500000,
    confirmations: 2,
    timeoutBlocks: 200,
    skipDryRun: true
},
```

Configuring the solidity compiler Uncomment the “compilers” section Change version to “0.8.0”

| truffle-config.js |

| --- |

| 93 94 95 96 97 98 99 100 101 102 103 104 105 |

```javascript
compilers: {
    solc: {
        version: "0.8.0",
        docker: true,
        settings: {
            optimizer: {
                enabled: false,
                runs: 200
            },
            evmVersion: "byzantinum"
        }
    }
},
```

### Configuring the private key

Create the secret file

| TERMINAL |

| --- |

| `$ touch .secret` |

Go to the browser and open your MetaMask wallet connected to infura network Click on your account Click on "settings" Click on "security & privacy" ![](Image00016.jpg)Click on "reveal seed phrase" Enter your wallet password to continue Copy the private key Paste the wallet mnemonic secret Creating the badge image Create the badge folder

| TERMINAL |

| --- |

| `$ mkdir badge` |

Go to the badge root folder

| TERMINAL |

| --- |

| `$ cd badge` |

Download the image that you will use as a badge from the internet. You can also copy and paste an existing image in this folder.

| TERMINAL |

| --- |

| `curl https://planouhost.z15.web.core.windows.net/badge.png > badge-image.png` |

Adding the badge to your local IPFS Initialize your local IPFS node

| TERMINAL |

| --- |

| `$ ipfs daemon` |
