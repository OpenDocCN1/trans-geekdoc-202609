
44

# Block Transactions #

| Hash | | | | | |
|---|---|--|
| e5e84898da28047151d0e56f8dc6292773603d0d6aabbdd2b5... | | 2009-01-03 07:27 |
| COINBASE (Newly Generated Coins) | 1475f640bc0c5f28b8f5sKV25m/Vpnjc3ahq | 72126094 BTC ₿ |
| Fee | OP_RETURN | 0.00000000 BTC |
| | 10.00000000 - 0.000 sec/WU - 308 cycles | 0.00000000 BTC |
| | OP_RETURN | 72126094 BTC |

Figure 2.4

From Figure 2.4, you can see that the Coinbase transactions which means the newly minted Bitcoin do not come from anyone's wallet. You can only see the winning miner's wallet address here.

# 2.7 How to achieve Proof of Work?

Mining involves the process of producing a hash whose value is less than the target value. When this hash has been found, it is called a valid hash and hence proof of work is achieved.

The mining algorithm uses a counter known as the nonce to generate the hash using the SHA256 cryptographic function. A hash algorithm always produces the same arbitrary length data given the same inputs. It is impossible to compute the same hash with two different inputs. It is also impossible to predict the output of any given data in advance.

The value of nonce is initialized to 0. Mining is finding the nonce, the only input that changes every time we run the hash function. The goal is to find a value for the nonce that will result in a hash lower than the target. So, the mining node might need to try billions or trillions of nonce values before it gets a valid hash. As you can see, mining is like playing the slot machine, there is no way to predict when you strike a jackpot.

It is quite easy to prove that the nonce found indeed produces a valid hash. All the information is available, everyone in the network can run the hash function and confirm if the hash is valid or not. Because it is also impossible to predict what the nonce will be, it also acts as a proof that the miner has indeed achieved Proof-of-Work.

Calculation of a valid hash is as follows (based on block #540909):

The formula to calculate the current target of the block is

Current target = Maximum target / Difficulty

Maximum target is

```
0x00000000FFFFFFFF000000000000000000000000000000000000000000000
```

This is a hexadecimal number. After conversion to a decimal number, the maximum target is

```
269599466715063979466701508701963067363714422540572841103610249215
```

Difficulty is (as given in the block)

```
701999231177.17
```

Therefore, the current target is

```
269599466715063979466701508701963067363714422540572841103610249215/701999231177.17
```

```
= 3.84089×10^54
```

The hash of the block

```
00000000000000000000ef17668e407e78c5a247f731b1138ad16f5bf79f1c0d
```

Converted to a decimal number, the value is

```
89454716205495239529548710168460626470818561584946189
```

The hash value is approximately 8.95×10^51. Clearly, the hash value is less than the current target, therefore it is a valid hash.

# Chapter 3

# Ethereum - The Programmable Blockchain and DApps Platform

Many alternative cryptocurrencies or simply altcoins have emerged since the successful launch of Bitcoin in 2009. There are more than a thousand at the time of writing this book. However, none of the cryptocurrencies came close to challenging Bitcoin until the invention of Ethereum by Vitalik Buterin.

# 3.1 A Brief History of Ethereum

Ethereum was first conceptualized by Vitalik Buterin in 2013. He is a young Russian Canadian programming genius (born 1994). In 2014, he cofounded the Ethereum platform with Mihai Alisie, Anthony Di Iorio and Charles Hoskinskinson.

The Ethereum Foundation held an Ethereum crowdsale in July 2014 during which they sold 60 million tokens. A total of 12 million Ether (ETH) tokens were created so the Ethereum Foundation could expand its development and marketing efforts. The Ethereum Mainnet went live on 30 July 2015, with 72 million coins "premined".

Ethereum broke into the mainstream in early 2017 when the price of ETH increased by 1000 percent over the course of a couple of months. This led to a similar rise in the price of alternative blockchain tokens, also known as altcoins. It is still ranked second behind Bitcoin on Coinmarketcap at the time of writing. Currently there are over 1600 altcoins, and this number is still growing.

# 3.1.1 What is Ethereum?

Ethereum is an open-source blockchain-based decentralized platform featuring smart contracts. Besides that, Ethereum is a programmable blockchain that enables developers to build and deploy decentralized applications. Of course, it also offers Ether, an alternative cryptocurrency to Bitcoin. It is also a platform for running an Initial Coin Offering (ICO), which is a crypto crowdfunding initiative. I shall explain ICO in another chapter. Ethereum runs on distributed blockchain. Ethereum Virtual Machine (EVM) is the core engine. It is Turing complete machine which can perform any logical step. Ethereum serves as a platform for decentralized applications (dApps).

# 3.1.2 Gas, Gas Price and Gas Limit

As mentioned earlier, you need to understand its terms: gas price and gas limit.

# 3.1.3 What is Gas?

Gas is a unit that measures the amount of computational effort it will take to execute operations. Operations include sending tokens, deploying a smart contract, interacting with anything else. Gas does not come for free, just like paying for gasoline.

# 3.1.4 What is Gas Price?

Gas price is the amount of Ether you need to pay per unit of gas. It is measured in Gwei (1 Gwei = 0.000000001 ETH). Its value is determined by the miners, who can refuse to process the transaction with less gas price. The transaction fee is paid to the successful miner as a form of incentive. The transaction fee is calculated using the following formula:

For example, for a certain transaction:

Gas used = 21,000

Gas price = 6 Gwei or 0.000000006 ETH

Transaction fee = 21,000 x 0.000000006 ETH = 0.000126 ETH

You can see the actual output in a smart contract on Etherscan, as shown in Table 3.1.

# Table 3.1 Block #1015194

| Block | 1015194 |
|---|---|
| Timestamp | 18 mins ago (May-28-2020 01:01:20 AM +UTC) |
| From | 0x5a0b54d5dc17e0aadc383d2db4b0a0d3e029c4c (Spark Pool) |
| To | 0x8fd00f170fdf3772c5ebdcd90bf25731669ba45 |
| Value | 109.6201869961092145 Ether ($25,796.77) |
| Transaction Fee | 0.000126 Ether ($0.03) |
| Gas Used by Transaction Limit | 21,000 |
| Gas Price | 100,000.000000006 Ether (6 Gwi) |

In addition, you can incentivize the miners to do your work first by paying more gas fees. In this way, you can jump to the front of the queue so that transaction can be processed first.
