+   3. Data mining
+   4. Proof-of-work
+   5. Blockchain
+   6. Convolutional neural networks
+   7. Large language models
+   8. Deep Sea Drones

It’s not critical to our case study to know what the professor’s work likely did, but it’s illustrative of understanding how something as straightforward as fudging the data may have gone undetected. Feel free to skip the next section if you’re happy to accept the proposition ‘some research is too complicated for lay people to easily understand’.

# THE BLACKBRIAR ALGORITHM

Let’s begin with the term simulated annealing – this is a reasonably well-defined process where a computer algorithm will use probability-based searches to find a ‘good’ solution when it’s too costly to exhaustively search all the possibilities. Right there we see the issue – in order to understand one thing, we need to understand several others.

A probability-based search is one that will search, based on some calculated values that indicate likely ‘good’ places to look, in different places each time it’s run. Imagine a probability-based maze-solving algorithm. In its simplest form, it might say ‘25% of the time, turn left. 25% of the time, turn right. 50% of the time, go forward’. When we encounter our first decision, half the time we’ll go forward and the other times we’ll take a turn. We don’t know in advance though which way we’re going to look. Many of the more interesting search routines in computing use some variation of this, making use of probability to deal with huge amounts of possible ‘hiding places’ that need to be investigated. You might use this kind of system when for example you have hundreds of millions of possible combinations of input values and can’t possible assess them all in a reasonable period of time.

You won’t get anywhere though if all you’re doing is cycling through a virtually limitless set of combinations. You need a way to determine the ‘fitness’ of particular combinations too so that you know when you’ve found a good one. The basic criteria are ‘You know when a particular combination