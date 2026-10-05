# CHAPTER 2 Protocol Building Blocks

With one-way hash functions, multiple signatures are easy:

+   (1) Alice signs the hash of the document.
(2) Bob signs the hash of the document.
(3) Bob sends his signature to Alice.
(4) Alice signs the document, her signature, and Bob's signature to Carol.
(5) Carol verifies both Alice's signature and Bob's signature.

Alice and Bob can do steps (1) and (2) either in parallel or in series. In step (5), Alice can verify one signature without verifying the other.

# repudiation and Digital Signatures

Alice can cheat with digital signatures and there's nothing that can be done about it. She can sign a document and later claim that she did not. First, she signs the document normally. Then, she anonymously publishes her private key, conveniently loses in a public place, or pretends to do either. Alice claims that her signature has been compromised and that others are using it, pretending to be her. She disavows signing the document and any others she signed using that private key. This is called repudiation.

Timestamps can limit the effects of this kind of cheating, but Alice can always claim that her key was compromised earlier. If Alice times well, she can sign a document and then successfully claim she did not. This is why there is so much talk about private keys buried in tamper-resistant modules—so Alice can't get at them. Although nothing can be done about this possible abuse, one can take steps to guarantee that old signatures are not invalidated by actions taken in disputing new ones. For example, Alice could “lose” her keep to paying Bob for the junk car he sold her yesterday, in the process, invalidate his bank account.) The solution is for the receiver of a signed document to have it timestamped [43]. The general protocol is given in [28]:

+   (1) Alice signs a message.
(2) Alice generates a header containing some identifying information. She concatenates the header with the signed message, signs, and sends it to Trent.
(3) Trent verifies the outside signature and confirms the identifying information. He adds a timestamp to Alice's signed message and the identifying information. Then he signs it all and sends to both Alice and Bob.
(4) Bob verifies Trent's signature, the identifying information, and Alice's signature.
(5) Alice verifies the message Trent sent to Bob. If she did not originate the message, she speaks up quickly.