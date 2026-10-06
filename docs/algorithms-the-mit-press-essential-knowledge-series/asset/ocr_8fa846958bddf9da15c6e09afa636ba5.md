we find the one we are looking for. A much better strategy is to go straight to the middle of the pile. Then we compare the number identifier on the document in the middle to the number of the document that we are looking for. There are three possible outcomes:

+   1. If we are lucky, we may have landed exactly on the document that we want. We are done; our search is over.

+   2. The identifier of the document we are looking for is greater than the identifier of the document we have in our hands. Then we know for sure that we can discard the document at hand *as well as all preceding documents*. As they are ordered, they will all have smaller identifiers. We have undershot our target.

+   3. The opposite happens: the identifier of the document we are looking for is smaller than the identifier of the document we have in our hands. Then we can safely discard the document at hand *as well as all the documents that come after it*. We have overshot our target.

In either of the last two outcomes, we are now left with a pile that is at most half the original one. If we start with an odd number of documents, say $n$, splitting $n$ documents in the middle gives us two parts, each with $n / 2$ items (discarding the fractional part in the division):