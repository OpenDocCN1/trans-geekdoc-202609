# CHAPTER 5 Advanced Protocols

bound with 3 percent probability. Alice's next message might state that she is bound with 5 percent probability and so on, until both are bound with 100 percent probability.

If Alice and Bob complete the protocol by the completion date, all is well. Otherwise, either party can take the contract to the judge, along with the party's signed message. The judge randomly chooses a value between 0 and 1 before seeing the contract. If the value is less than the probability the other party signed, both parties are bound. If the value is greater than the probability, then both parties are not bound. (The judge saves the value, in case he has to rule on another matter regarding the same contract.) This is what is meant by being bound to the contract with probability p.

That's the basic protocol

# Simultaneous Contract Signing without an Arbitrator
(Using Cryptography)

This cryptographic protocol uses the same baby-step approach [529]. DES is used in the description, although any symmetric algorithm will do.

+   (1) Alice and Bob randomly generate 2n DES keys, grouped in pairs. The pairs are not special; they are just grouped way for the protocol.

+   (2) Alice and Bob generate n pairs of messages, $L_i$ and $R_i$; "This is the left half of my ith signature" and "This is the right half of my ith signature," for example. The identifier, $i$, runs from 1 to n. Each message will possibly include a digital signature of the contract and a timestamp. The contract is considered signed if the other party can produce both, $L_i$, and $R_i$, of a single signature pair.

+   (3) Alice and Bob encrypt their messages in each of the DES keys pairs, the message with the left key in the pair and the right message with the right key in the pair.

+   (4) Alice and Bob send each other 2n encrypted messages, making clear which messages are halves of which pairs.

+   (5) Alice and Bob send each other every key using the oblivious transfer protocol for each pair. That is, Alice sends Bob the key she used to encrypt the message or the key used to encrypt the message, independently, for each of the n pairs. Bob does the same. They can alter sending halves or can send 100 and the other—it doesn't matter. Now Alice and Bob have one key in each key pair, but neither knows which halves the other has.

+   (6) Alice and Bob decrypt the message that they can, using the keys they received. They make sure that the decrypted messages are valid.