
According to Binance, Proof of Authority (PoA) is a reputation-based consensus algorithm that employs a practical and efficient solution for blockchain networks, particularly the private blockchain networks. The term was proposed in 2017 by Ethereum co-founder and former CTO Gavin Wood.

The POA consensus algorithm leverages the value of identities, which means that block validators are not staking coins but their own reputation instead. Therefore, POA blockchains are secured by validator nodes that are preselected as trustworthy entities.

The Chi PoA blockchain network employs a limited number of validators and this makes it highly scalable. Blocks and transactions are verified by pre-approved validators, who act as moderators of the system. In contrast to POW, POA does not require nodes to spend a huge amount of computational resources and electricity to maintain the blockchain network.

The Chi PoA blockchain network has much higher transaction rate, low latency and higher tolerance for compromised and malicious nodes compared to blockchain networks that are powered by POW or POS consensus algorithms. The highly efficient and secure POA system will ensure the safety of crypto funds and financial data. It is also flexible enough to develop innovative business applications on Chi PoA blockchain platform.

## 3.2 The Chi Blockchain Platform

![](img/f2f9952d33ef3f083419e55bc6a6e2e1_303_0.png)

## The Chi Blockchain Network

The Chi blockchain network consists of validator nodes and peer nodes. Only validator nodes have the authority to verify transactions and to elect new validators or dismiss misbehaving validators. Peer nodes are required to help maintain the network.

Some of the nodes can be assigned the status of a Master node if they agreed to host the Chi Blockchain Network 24/7 and carry additional duties. The role of Master nodes is to ensure the blockchain security and reliability of Chi Blockchain Network. In addition, all the nodes will be incentivized with Chi Tokens.

All nodes are subjected to yearly re-election using smart contracts to ensure democracy and transparency. Malicious nodes will be voted out while the nodes who performed well will be re-elected to protect the integrity of the Chi POA Blockchain network.

The Chi blockchain network will be hosted on a secure enterprise cloud server such as AWS. We rely on public-key cryptography, multiple factor authentication and system isolation of private keys to ensure topmost security and reliability.

## 3.4 Setting Up Chi Blockchain Network Using Parity Ethereum

The Chi blockchain network will be set up using Parity Ethereum. Parity Ethereum is the fastest and most Advanced Ethereum Client.

Parity Ethereum is built for mission-critical use: Miners, service providers, and exchanges need fast synchronization and maximum uptime. Parity Ethereum provides the core infrastructure essential for speedy and reliable services.

- Clean, modular codebase for easy customization
- Advanced CLI-based client
- Minimal memory and storage footprint
- Synchronize in hours, not days with Warp Sync
- Modular for light integration into your service or product

Parity Ethereum was developed using the sophisticated and cutting-edge Rust programming language. Parity Ethereum is licensed under GPLv3 and can be used for all your Ethereum needs.

For the complete guide to install Parity Ethereum and to set up the Chi POA blockchain network, please refer to the Chi technical whitepaper.

## 3.5 Chi Token Smart Contract

The Chi Token is an ERC20 token minted using a smart contract based on the Solidity programming language. The code shown here is the intellectual property of Chi Management Ltd. Prior consent is required to adapt the code.

```solidity
pragma solidity ^0.5.0;
contract ChiToken {
  /* This creates an array with all balances *
  mapping(address => uint256) public balanceOf;
  string public name;
  string public symbol;
  uint8 public decimals;

  /* Initializes contract with initial supply tokens
  to the creator of the contract */
  constructor(
    uint256 initialSupply,
    string tokenName,
    string tokenSymbol,
    uint8 decimalUnits
  ) public {
    balanceOf[msg.sender] = initialSupply; // Give the creator all initial tokens
    name = tokenName; // Set the name for display purposes
    symbol = tokenSymbol; // Set the symbol for display purposes
    decimals = decimalUnits; // Amount of decimals for display purposes
  }

  /* Send coins */
  function transfer(address _to, uint256 _value)
  returns (bool success) {
    require(balanceOf[msg.sender] >= _value); // Check if the sender has enough
    require(balanceOf[_to] + _value >= balanceOf[_to]);

    // Check for overflows
    balanceOf[msg.sender] -= _value;
    // Subtract from the sender
    balanceOf[_to] += _value;
    // Add the same to the recipient
    return true;
  }
}
```

## 3.6 Chi Token Listing

The Chi Token will be listed on multiple exchanges. The full list of exchanges will be available on our website when trading begins. Additional exchanges will be added over time. Trading will be automated via API integration with the exchanges.

The liquidation price of the Chi Tokens will be determined through the use of an exchange service developed by Chi. Automation of liquidation price updates are an essential part of smooth business operation; however, automation can also expose security risks due to the necessity of online private key storage. We circumvent this risk by implementing a two-tier permissions system, with multiple addresses allocating only the necessary permissions to fulfill a particular task, such as updating the liquidation price. This strategy enables risk-mitigating automation without having to store crucial private keys online.

## 4. Security

## 4.1 Safe Storage of Crypto Assets

Chi will implement security industry best practices for defense against cyberattacks and bad actors. Strong identity verification and authentication procedures are in place to ensure secure operations. Besides that, the vast majority of Chi cryptoassets will be stored offline in cold wallets.

Chi will at any stage hold varying amounts of the 20 coins that form the index it tracks. The majority of each of these cryptocurrencies will be stored in cold wallets with a small percentage of each currency stored in a wallet on our servers to facilitate automatic rebalancing. If rebalancing necessitates moving more of the cryptocurrency to these hot wallets will be done manually via interfacing with various cold wallets – Chi's portfolio managers will be notified ahead of time to accommodate this. The weekly rebalancing period affords more than sufficient time for this purpose.

Ledger Nano S will be used for the storage of all cryptocurrencies it supports. For all cryptocurrencies that are not supported, encrypted USB drives will be utilized. These storage devices will be held in secure safe deposit boxes with back-up paper wallets stored at separate secure locations. Locations are undisclosed due to security considerations. A public audit will confirm the presence and safe storage of the USB drives and paper wallets, to be accessible for all members. Wallet interactions with Chi will be facilitated through light clients.

## 4.2 Multisig Wallet

To further improve security and increase trust among the investors, the best solution is to store crypto assets in a multisig wallet.

The multisig wallet is one where you need control over multiple keys to spend from that wallet. The idea with multisig wallets is that multiple people can cooperatively control the funds in the wallet. With multisig, it allows users to have one Bitcoin address with multiple key holders sign off on it

In the case of Chi, the multisig wallet will be entrusted to a council comprising the management team and selected investors. Each member holds his private key for signing the wallet. Nobody can withdraw or spend the funds in the wallet unless all members agree to do so by using their private keys.

For steps on creating a multisig wallet, please refer our technical guide on multisig wallet.

## 5. Funds Allocation

To maximize profit and minimize risk for our investors, 50% of the funds raised will be used to purchase Bitcoins (BTC) at the current market value and deposit them in a secure multisig custodian wallet to hedge the risk and volatility of the crypto market. Another 25% of the funds will be used to invest in Chi Index Fund. The balance 25% will be spent on marketing activities.

Bitcoin might be a volatile product on the current market, but Bitcoin had shown a consistent increment on a yearly basis, from the average of USD 144 back in 2013 up to the current average of USD 8000. In the current volatility of the market which involves USD value, gold value and Bitcoin value, the prices have gone up and down constantly, but Bitcoin has shown an upwards trend since its creation back in 2008 (as shown in the figure).

The value of Bitcoin may fluctuate from time to time, but in the long run, Bitcoin price will increase in value. Hence, if Bitcoin is held, users will earn substantial profit in the future, as shown in the figure below.
