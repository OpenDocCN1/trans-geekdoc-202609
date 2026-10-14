
# Other cryptocurrencies

Lightning Network requires certain enhancements such as segregated witness to overcome the risk of transaction malleability and so on. There are many cryptocurrencies that use almost the same codebase and scripting language as Bitcoin. The enhancements that enabled Lightning Network on Bitcoin network may also enable Lightning Network on many other cryptocurrencies.

As of now, Litecoin is the only other cryptocurrency that has enabled Lightning Network on its network. A few other cryptocurrencies have shown interest, but none have added the required support for Lightning till date.

# Cross-chain atomic swap

You learned how HTLC can be used to swap off-chain balance with on-chain balance using Submarine Swaps. Similarly, HTLC can be used to perform cross-chain swaps with another cryptocurrency. This has been demonstrated with Litecoin by the Litecoin founder Charlie Lee on 16 September, 2017. A 2-minute demo is available on YouTube titled `Lightning Cross-Blockchain Swap Between Bitcoin and Litecoin`:

**https://www.youtube.com/watch?v=cBVcgzEuJ7Q**

# Network topology

Lightning Network is still evolving, and the structure of the network may change in the future. However, it seems that the overall network is trying to imitate postal network where individuals connect to a wallet provider, the wallet maintains channels with bigger hops, and bigger hops are connected to a few other similar hops to simplify forwarding.

As an end user, we never need to close our channel with the wallet. If we send and receive funds, this channel can continue for extended period; thus, the overall fee paid is negligible.

The following is the illustration of Lightning Network topology:

![](images/Figure-13.31.jpg)

**Figure 13.31:** Lightning network topology

In the preceding figure, we can see that there are thousands of nodes connected with channels. These are public channels, so they can be found and used to update topology.

# Conclusion

In this chapter, you learned about the Lightning Network protocol, a layer-two protocol of Bitcoin. You learned how Bitcoin’s primitive scripting language makes reliable instant transaction possible and understood that Lightning Network has its open specification and messaging system to allow different software implementations to talk to each other.

You also learned about the nodes that help in routing payments or rebalancing of channels and about the ecosystem that is being built for and on Lightning Network.

This brings us to the end of the book. The intention of this book is to help build developer community for Bitcoin by making the reader aware of internal details of Bitcoin protocol, network, blockchain, transactions, enhancements etc. The more developer enters the Bitcoin development community the more secure and better Bitcoin will become which gives us hope for more decentralized future.

# Points to remember

*   Lightning Network is layer-two protocol and uses Bitcoin transaction scripting.
*   It allows instant offline payment of bitcoins.
*   To perform offline transactions using Lightning Network, a channel is created between the sender and the receiver.
*   Offline transactions can be performed if the required funds are available at the sender’s end of channel.
*   Channels can be unilaterally closed, or a mutual closure can happen.
*   A channel breach is when an attacker closes a channel by publishing an older transaction.
*   Victim of a channel breach punishes attacker by publishing justice transaction, which contains revocation key provided by the attacker to pay itself the attacker’s funds.
*   A unidirectional channel has funds only at the sender’s end when the channel is created.
*   A bidirectional channel has funds locked at both ends of a channel.
*   A channel is created by locking funds in 2-of-2-multisig.
*   A payment can be made between two individuals who do not have direct channels by routing payments over multiple nodes passing through a sequence of channels.
*   Source routing is when the sender communicates with nodes to build network topology to find the best route to the destination.
*   Trampoline nodes help the sender find the best route.
*   Trampoline nodes maintain updated network topology, and the sender only needs partial topology.
*   Nodes need to remain online all the time; otherwise, a peer can publish an old transaction, and the offline node will lose funds.
*   Watchtower nodes can serve nodes by monitoring on-chain all the time and publish justice transaction if required.
*   Nodes can connect to watchtower server and update it regularly about channel states and justice transaction.
*   Circular rebalancing is a method in which a node can balance a channel by moving funds to its other channel, which is loaded at the peer side.
*   Submarine swaps or Lightning Loop node helps move on-chain funds to nodes at the end of channel or vice versa.
*   Splicing allows you to dynamically add or reduce capacity of a channel without bringing a channel offline.
*   Adding capacity of channel is called splice-in, and reducing capacity is called splice-out.
*   Multi-part payment allows a sender to send large value transactions over Lightning Network by splitting the amount into smaller values and sending them over different channels and routes.
*   Lightning Invoice is generated by merchant or receiver and can be in the form of QR code. It is used by a sender to make payment.
*   LNURL is a layer-three protocol.
*   LNURL provides a way to repeatedly make payment using single QR code.
*   With LNURL, one can perform various other tasks like authentication and creation of channels.

# Questions

1.  Explain the difference between the exchange of messages between unidirectional and bidirectional channels.
2.  Why is it important for public routing nodes to keep the channel balanced?
3.  What are the benefits of using Trampoline nodes over source routing?
4.  Explain the benefits of using MPP.
5.  Fill in the blanks:
    1.  Capacity of a channel can be increased by channel management technique called `splice-in`.
    2.  Lightning Network can be used for authenticating a site by using LNURL `auth`.
    3.  Lightning Network has been demonstrated to perform `cross-chain atomic swap` of values between Bitcoin node and Litecoin node.
6.  True/False:
    1.  LNURL is layer-three protocol because it has its own messaging protocol that helps establish and perform Lightning Network operations.
    2.  Circular rebalancing is the best suited channel balancing method for merchants as they mostly always receive funds.
    3.  Turbo channels are without risks, so high-capacity channel can be opened.
    4.  Lightning Network usability depends on how well nodes are interconnected, which depends on its popularity.
7.  Create lists of custodial and non-custodial wallets.
8.  Install Lightning Network wallet, make a payment, and try to guess the steps that have happened in the background.

# Index

## Symbols

*   51% attack [255](#c08.xhtml#page255)

## A

*   Abstract section [62](#c05.xhtml#page62), [63](#c05.xhtml#page63)
*   address [280](#c09.xhtml#page280)–[283](#c09.xhtml#page283)
*   address format [272](#c09.xhtml#page272), [450](#c12.xhtml#page450)–[454](#c12.xhtml#page454)
*   address generation [450](#c12.xhtml#page450)–[454](#c12.xhtml#page454)

## B

*   bech32 format
    *   advantages [450](#c12.xhtml#page450)
*   bech32 string
    *   characters [451](#c12.xhtml#page451)
*   BGP hijacking attack [248](#c08.xhtml#page248)
*   bidirectional dual-funded channel
    *   about [469](#c13.xhtml#page469)
    *   channel creation [470](#c13.xhtml#page470), [471](#c13.xhtml#page471)
*   Bitcoin
    *   about [56](#c04.xhtml#page56)
    *   Byzantine general problem [25](#c02.xhtml#page25)–[27](#c02.xhtml#page27)
