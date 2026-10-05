# CHAPTER 6 Esoteric Protocols

(7) The merchant asks Alice to write a random identity string on the money
order.

(8) Alice complies.

(9) The merchant takes the money order to the bank.

(10) The bank verifies the signature and checks its database to make sure a
money order with either uniqueness Xs has not been previously
deposited. If it hasn't, the bank credits $1000 to the merchant's account.
The bank records the uniqueness string and the identity string in a database.

(11) If the uniqueness string is in the database, the merchant refuses to accept the
money order. Then, it compares the identity string on the money order
with the one stored in the database. If it is the same, the bank knows that
the merchant photocied the money order. If it is different, the bank
knows that the person who bought the money order photocopied.

This protocol assumes that the merchant cannot change the identity string once
Alice writes it on the money order. The money order might have a series of little
squares, which the merchant would require Alice to fill in with either Xs or Os. The
money order might be made of paper that feared erased,

Since the interaction between the merchant and the bank takes place after Alice
sends the money, the merchant could be stuck with a bad money order. Practical
implementations of this protocol might require Alice to wait near the cash register
during the merchant-bank interaction, much the same way as credit-card purchases
are handled today.

Alice could also frame a copy of the money order
a second time, giving the same identity string in step [7]. Unless the merchant keeps
d database of money orders it already received, he would be fooled. The next proto-
coliminates that problem.

# Protocol #4

If it turns out that the person who bought the money order tried to cheat the mer-\chant, the bank would want to know who that person was. To do that moving
a from a physical analogy and into the world of cryptography.
The technique of secret splitting could be used to hide Alice's name in the digital
money order.

(1) Alice prepares n money orders for a given amount.

Each of the money order contains a different random uniqueness string,
X one long enough to make the chance of two being identical negligible.
On each money order, there are pairs of identity bit strings, $h_i,
l_i, \dots, l_n$ [Yes, there are n different orders on each check.] Each of these pairs is
generated as follows: Alice creates a string that gives her name, address, and\other piece of identifying information that the bank wants to see. Then,
s splits it into two pieces using the secret splitting protocol [see Section
3.6). Then, she commits to each piece using a bit-commitment protocol.