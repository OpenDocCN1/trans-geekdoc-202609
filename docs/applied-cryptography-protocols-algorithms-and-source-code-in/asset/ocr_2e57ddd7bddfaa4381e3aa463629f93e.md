# 4.10 Fair Coin Flips

It's story time with Joe Kilian [31]:

Alice and Bob wanted to flip a fair coin, but had no physical coin to flip. Alice offered a simple way of flipping a fair coin mentally.

“First, you think up a random bit, then I'll think up a random bit. We'll then exclusive-or the two bits together,” she suggested.

“But if one of us doesn't flip a fair coin at random?” Bob asked.

“It doesn't matter. As long as one of the is truly random, the exclusive-or of the bits should be truly random.” Alice replied, and after a moment's reflection, Bob agreed.

A while later, Alice and Bob happened upon a book on artificial intelligence, lying abandoned by the roadside. A good citizen, Alice said, “One us must pick this book up and find a suitable receptacle.” Bob agreed, and suggested they use their coin-flipping protocol to determine who would have to throw the book away.

“If the final bit is 0, then you pick the book up, and if it is 1, then I will,” said Alice. “What is your bit?

Bob replied, “So is mine,”

“Why, so is mine,” Alice slyly, “I guess this isn't your lucky day.” Needless to say, this coin-flipping protocol had a serious bug. While it is true a truly random bit, x. exclusive-OR with independently distributed bit will yield a truly random bit, Alice's protocol did not ensure that the two bits were distributed independently. In fact, it is not hard to verify that no protocol could allow infinitely powerful parties to flip a fair coin. Alice and Bob were in trouble until they received a letter from an obscure student in cryptography. The information in the letter was too theoretical to be of easily anyone to use, but the envelope came in was extremely handy.

The next time Alice and Bob wished to flip a coin, they played a modified version of the original protocol. Bob decided on a bit but instead of announcing it immediately, he wrote down on a piece of paper and placed the paper in the envelope. Next, Alice announced her bit. Finally, Alice and Bob took Bob's bit out of the envelope and computed the random bit. This bit was indeed random whenever at least one of them played honestly. Alice and Bob had a working protocol, the cryptographer's dream of social relevance was fulfilled, and they lived happily ever after.

Those envelopes sound a lot like bit-commitment blobs. When Manuel Blum introduced the problem of flipping a fair coin over a modern [194], he solved it using a bit-commitment protocol:

+   (1) Alice commits to a random bit, using any of the bit-commitment schemes listed in 4.9.