# Chapter 3 Primer on Cryptocurrencies and Distributed Ledgers | 59

![](bbox=[0.156, 0.083, 0.843, 0.303])

**Figure 3.5** An attempt of double spend in a centralized setup. Own graphics.

![](bbox=[0.143, 0.363, 0.856, 0.558])

**Figure 3.6** An attempt of double spend in a decentralized, peer-to-peer setup. Two conflicting transactions are propagated through the network, reaching peers at different instants. Own graphics.

This process looks trivial in a centralized context, where the bank is the only party to process payments because it is, see Figure 3.5.

# 3.5.2 Illustration in a decentralized setup

Let us now consider a similar situation in a decentralized setup such as Bitcoin. The account now holds 1 BTC on the Bitcoin ledger and he would like to buy both a red bike and a blue bike, each worth 1 BTC. Intuition suggests that the owner can only purchase either the red bike, or the blue bike, as the value of both goods is 2 BTC, which is larger than his total wealth. The owner aims to claim the secret and creates two transactions at the same time: the first transaction sending 1 BTC to pay for the red bike and the second transaction sending 1 BTC to pay for the blue bike. Details are shown in Figure 3.6.

The peer-to-peer broadcast of both transaction requests starts, and each network node notified of each transaction immediately broadcasts it to its own set of neighbor nodes. Following a cascade effect, one of the, or generally both transactions quickly become