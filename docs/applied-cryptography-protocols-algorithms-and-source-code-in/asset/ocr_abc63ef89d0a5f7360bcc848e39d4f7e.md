(by querying a repository for the appropriate tree root and comparing it against a hash
value appropriately recomputed from the file and its certificate). For information
contact Surety Technologies, 1 Main St., Chatham, NJ, 07928; (201) 701-0600; Fax:
(201) 701-0601.

# 4.2 Subliminal Channel

Alice and Bob have been arrested and are going to prison. He's going to the men's
prison and she's going to the women's prison. Walter, the warden, is willing to let
Alice and Bob exchange messages, but he won not allow them to be encrypted. Walter
expects them to coordinate an escape plan, so he wants to be able to read everything
they say.

Walter also hopes to deceive Alice or Bob. He wants one of them to accept
a fraudulent message as a genuine message from the other. Alice and Bob go along
with this risk of deception, otherwise they cannot communicate at all, and they
have to coordinate their plans. To do this have to deceive the warden and find
a way of communicating secretly. They have to set up a subliminal channel, a covert
communications channel between them in full view of Walter, even though the\essages contain no secret information. Through the exchange of
fertuously innocent signed messages they will pass secret information back and forth
and fool, even though Walter is watching all the communications.

An easy subliminal channel might be the number of words in a sentence. An odd
number of words in a sentence might correspond to "D". So, while you read this seemingly innocent para-
graph, I have sent my operates in the field "101." The problem with
this technique is that it is steganography [see Section 1.2]; there is no key and
security depends on the secrecy of the algorithm.

Gustav Simmons introduced the concept of a subliminal channel in a conventional
signature algorithm [1458,1473]. Since the subliminal messages are hidden in
what looks like normal digital signatures, this is the form of obfuscation. Walter sees
signed messages pass back and forth, but he completely misses the infor-
mation being sent over the subliminal channel. In fact, the subliminal chan-
age algorithm is indistinguishable (from a normal signature algorithm, at least to
Walter. Walter may not cannot read the subliminal message, but he also has no idea
that one is even present.

In general the protocol looks like this:

+   1. Alice generates an innocent message, pretty much at random.
2. Using a secret key shared with Bob, Alice sends the innocent message in
a way that that she hides her subliminal message in the signature. (This is
the meat of the subliminal channel protocol; see Section 23.3.)
3. Alice sends this signed message to Bob via Walter.
4. Walter reads the innocent message and checks the signature. Finding
nothing amiss, he passes the signed message to Bob.