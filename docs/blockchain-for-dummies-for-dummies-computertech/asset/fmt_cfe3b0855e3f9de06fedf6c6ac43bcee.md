
# Ripple Consumer Wallet Closure and GateHub Guide

Ripple has stopped opening new consumer wallet accounts on Ripple Trade, its consumer-facing portal. For the most part, Ripple has also pulled down all its consumer-facing products. The regulatory burden of servicing consumers was too high and was clarified by the Financial Crimes Enforcement Network (FinCEN) ruling regarding the need for participants in the virtual currency arena to register as money services businesses under federal law.

The network growing out of the consumer-facing portal wasn’t going to rival the growth in the banking network for Ripple. As of now, Ripple is focusing its efforts on servicing large enterprise customers. Banks are the ones who truly need what Ripple can offer at a scale that is profitable for them.

As a consumer, you can access Ripple through third parties. The wallet that Ripple references is GateHub.

The GateHub wallet stores all your different currencies; allows you to send money; and allows you to trade gold, silver, XRP, and Bitcoin on the Ripple network directly from your wallet. It also shows you the net worth of your different currencies as they fluctuate with the market.

GateHub will require you to identify yourself, and setting up your account will take some time. When your account is up and running, you’ll be able to explore the power of the Ripple network.

Follow these steps to get up and running on GateHub:

1. Go to [`www.gatehub.net`](http://www.gatehub.net).
2. Click Sign Up.
3. Enter your email address and a password, and click Sign Up.
4. Save your recovery key in a safe place.
5. Verify your email.
6. Verify your identity.

GateHub verifies your identity and asks for your phone number, a name, a photo, and supporting documents.

After you provide your personal information, GateHub will clear your account and you’ll be set to trade through the Ripple protocol.

At this point you can send funds to your new account from your Bitcoin wallets.

If you want to build anything on Ripple, you’ll need to be a programmer or at least have access to one. Ripple has great documentation and a support team to get you started.

![warning](Image00006.jpg)Ripple is made for moving money faster and cheaper. This area of the economy is very heavily regulated. Ripple states clearly that it’s only software that enables you to perform these tasks. It’s completely up to you to understand and comply with regulations.

If you’re still interested in building a custom project on the Ripple network, they’ll offer you support. The best way to get started is by going directly to the Ripple build page ([`https://ripple.com/build/`](https://ripple.com/build/)). If you want to dive even deeper into the Ripple network, check out its GitHub at [`https://github.com/ripple`](https://github.com/ripple).

## Exercising Caution with Ripple

![remember](Image00004.jpg)Ripple, like other blockchains, which work through cryptocurrencies, has many dangers. Use common sense while working in the cryptocurrency world, and follow all other security best practices described in this book. It truly is the new wild west, full of opportunity and risk.

![warning](Image00006.jpg)Here are some risks unique to Ripple:

* **Unethical trading:** As described earlier, Ripple was created to move value across the world cheaper and faster than any another network. The structure of Ripple works with clusters of markets. These markets have trusted nodes confirming transactions together. There are small price differences between these groups at times, and these price differences attract unethical trading.

* **Transaction manipulation:** The Ripple network, in particular, is prone to *arbitrage* (the simultaneous buying and selling assets in different markets in order to take advantage of differing prices for the same asset) because it has many currencies and multiple markets, and clever programmers can manipulate the order of transactions. The two known forms of this on Ripple are as follows:

    * **Advantageous arbitrage transaction placement:** Taking advantage of a price difference between multiple markets before the ledger closes. The ledger closes every five seconds, so traders use arbitrage bots to exploit the market. These bots strike a combination of matching deals that capitalize on the small imbalances between the markets and also push their transactions into an optimal position within the ledger. The traders then profit by taking the difference in price of these markets.

    * **Large trade front running:** The structure and latency in Ripple’s consensus exposes the network to a new type of front running of large trades. It is possible to do this because each node in the network broadcasts transactions to other trusted nodes. During this time, bots will be monitoring all transactions for opportunities to jump in front of large trades.

        The bot will buy up initial offers to fulfill the large purchase and then upsell them to the original owner. At the same time, the bots will also reposition the transactions within the ledger to allow this to happen. The net result of this behavior is that the original owner will receive less value in the trade.

        ![tip](Image00003.jpg)You can find out more about this vulnerability at [`http://availableimagination.com/exploiting-ripple-transaction-ordering-for-fun-and-profit/`](http://availableimagination.com/exploiting-ripple-transaction-ordering-for-fun-and-profit/).

Ripple is excellent about keeping exploits out of its network and has an open offer for programmers to earn money through hunting down bugs, exploits, and vulnerabilities. It is highly likely that these two bugs will be fixed in the near future.

# Chapter 7 Finding the Factom Blockchain

IN THIS CHAPTER

![check](Image00001.jpg)**Making entries in Factom**

![check](Image00001.jpg)**Diving into chain structure**

![check](Image00001.jpg)**Uncovering identity on the blockchain**

![check](Image00001.jpg)**Seeing Factom in use**

The Factom blockchain is a powerful tool that will help industry scale blockchain technology. It’s different from other public blockchains and has unique properties that make it ideal for publishing data streams and securing systems. The Factom blockchain also has a corporation behind it — Factom, Inc. — which spearheads its development and builds tools and products on top of the protocol.

Factom software is being built into systems that govern identity and security of both people and things. They’re integrating and bridging other blockchains and blockchain technology as well. The linking between blockchains improves the security of Factom and makes the other blockchains more interoperable.

This chapter explains how Factom works, fills you in on its unique properties, and provides easy-to-follow instructions that will help you get started using it. After reading this chapter, you’ll understand many of the core concepts of Factom blockchain technology and know where it will add value to your blockchain projects.

This may be the time to mention that I am a co-founder of and the chief marketing officer at Factom, Inc. Although my aim is objectivity, my enthusiasm for Factom is hard to hide.

## A Matter of Trust

Blockchains at their core are about allowing different entities to cooperate and collaborate without needing to trust each other’s data security or business processes. Historically, trusted middlemen or industry consortiums have enabled this to happen, but those have high overhead costs and merely shift the trust to a different party. Blockchains shift the trust to a network of disimpassioned third parties and, ultimately, math.
