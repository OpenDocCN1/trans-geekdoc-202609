The voters broadcast their votes and accompanying edges using an anonymous broadcast protocol so no one can know how each voter voted. A much deeper analysis of the cryptographic properties of the protocol is given in Khabiboulline et al. [2021].

# ## 3.2.6 Quantum Byzantine Generals Solution

The _Byzantine Generals Problem_ (BGP) is a well-known challenging problem in distributed computing. The problem is about how to achieve consensus among multiple parties (e.g. a node in a distributed system) when some of the parties fail or a party receives conflicting information from different parties.

The _Byzantine Generals Problem_ (_BGP_) or _Byzantine Agreement_ (_BA_) problem can be stated using a metaphor using the idea of the “Byzantine army,” as follows:

> We imagine that several divisions of the Byzantine army are camped outside an enemy city, each division commanded by its own general. The generals can communicate with one another only by messenger. After observing the enemy, they must decide upon a common plan of action. However, some of the generals may be traitors, trying to prevent the loyal generals from reaching agreement. The generals must have an algorithm to guarantee that:

+   A. All loyal generals decide upon the same plan of action. ...

+   B. A small number of traitors cannot cause the loyal generals to adopt a bad plan .... [Lamport et al., 1982, p. 382–383]

More specifically:

A commanding general must send an order to his $n - 1$ lieutenant generals such that

+   IC1. All loyal lieutenants obey the same order.

+   IC2. If the commanding general is loyal, then every local lieutenant obeys the orders he sends.

...Note that if the commander is loyal, then IC1 follows from IC2. However, the commander need not be loyal. [Lamport et al., 1982, p. 384]

IC stands for interactive consistency. An assumption is that the generals can send messages directly to each other. The commanding general can be disloyal in that it sends different messages to the lieutenant generals, thereby sabotaging the attack.

It was noted that there is no solution for the BA problem unless more than two-thirds of the generals are loyal, but if additional conditions are imposed so that