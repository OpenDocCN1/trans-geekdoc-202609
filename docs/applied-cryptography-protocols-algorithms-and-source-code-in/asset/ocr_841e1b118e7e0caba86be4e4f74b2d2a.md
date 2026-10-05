# CHAPTER 2 Protocol Building Blocks

Even so, arbitrators still have a role to play. In protocols using a trusted arbitrator, the part will be played by Trent.

# Adjudicated Protocols

Because of the high cost of arbitrators, arbitrated protocols can be subdivided into two lower-level subprotocols. One is a nonarbitrated subprotocol, executed every parties wants to complete the protocol. The other is an arbitrated subprotocol, executed in exceptional circumstances—when there is a dispute. This special type of arbitrator is called an adjudicator (see Figure 2.1b).

An adjudicator is a disinterested and trusted third party. Unlike an arbitrator, he is not directly involved in every protocol. The adjudicator is called in only to determine whether a protocol was performed.

Judges are professional adjudicators. Unlike a notary public, a judge is brought in only if there is a dispute. Alice and Bob can enter into a contract without a judge. A judge never sees the contract until one of them hauls the other into court. This contract-signing protocol can be formalized in this way: Nonarbitrated subprotocol (executed every time):

+   * Alice and Bob negotiate the terms of the contract.
* Alice signs the contract.
* Bob signs the contract.

Adjudicated subprotocol (executed only in case of a dispute):

+   * Alice and Bob appear before a judge.
* Alice presents her evidence.
* Bob presents his evidence.
* The judge rules over the evidence.

The difference between an adjudicator and an arbitrator (as used in this book) is that the adjudicator is not always necessary. If there is no dispute, a judge is called to adjudicate.

There are adjudicated computer protocols. These protocols rely on the parties to be honest, if someone suspects cheating, a body of data exists so that a trusted third party could determine if someone cheated. In a good adjudicated protocol, the adjudicator could also determine the cheater's identity. Instead of preventing cheating, adjudicated protocols detect cheating. The inevitability of detection acts as a preventive and discouraging cheating.

# Self-Enforcing Protocols

A self-enforcing protocol is the best type of protocol. The protocol itself guarantees fairness (see Figure 2.1c). No arbitrator is required to complete the protocol, No adjudicator is required to resolve disputes. The protocol is constructed so that there