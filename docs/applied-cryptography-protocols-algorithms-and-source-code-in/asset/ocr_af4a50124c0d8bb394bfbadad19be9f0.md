# 6.3 Anonymous Message Broadcast

This kind of voting could occur in real life. It could be part of a corporation's organiza- national structure, where certain people have more power than others, or it could be part of the United Nations' procedures, where certain nations have more power than others.

# Multiparty Unconditionally Secure Protocols

This is a simple case of a general theorem: Any function of $n$ inputs can be computed by a set of $n$ players in a way that will all learn the value of the func- tion, but any set of $n/2$ players will not get any additional information that does not follow from their own inputs and the value of the output information. details, see [136,334,1288,621].

# Secure Circuit Evaluation

Alice has her input, a. Bob has his input, b. Together they will compute some general function, $f_{ab}$, such that Alice learns about Bob's input and Bob learns nothing about Alice's input. The general problem of secure multiparty computation is also secure circuit evaluation. Here, Alice and Bob can create an arbitrary Boolean circuit. Circuit accepts inputs from Alice and from Bob and produces an output. Secure circuit evaluation is a protocol that accomplishes three things:

+   1. Alice can enter her input without Bob's being able to learn.
2. Bob can enter his input without Alice's able to learn it.
3. Both Alice and Bob can calculate the output, with both parties being sure the output is correct and neither party has tampered with it.

Details on secure circuit evaluation can be found in [831].

# 6.3 ANONYMOUS MESSAGE BROADCAST

You can't go out to dinner with a bunch of cryptographers without raising a ruckus. In [321], David Chaum introduced the Dining Cryptographers Problem:

Three cryptographers are sitting down at dinner their favorite three-star restaurant. Their waiter informs them that arrangements have been made with the maître d'hotel for the bill to be paid anonymously. One of the cryptographers might be paying for the dinner, or it might have been the NSA. The three crypt-ographers respect each other's right to make an anonymous payment, but they wonder if the NSA is paying.

How do the cryptographers, named Alice, Bob, and Carol, determine if one of them is paying for dinner, while at the same time preserving the anonymity of the payer? Chaum goes to solve the problem:

Each cryptographer flips an unbiased coin behind his menu, between him and the cryptographer to his right, so that only the two of them can see the outcome. Each