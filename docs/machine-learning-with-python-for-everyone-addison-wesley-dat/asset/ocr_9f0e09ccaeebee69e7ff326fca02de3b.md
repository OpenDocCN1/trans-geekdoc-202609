# Chapter 12 Combining Learners

So, extreme random forests don’t consider all possible split points. They merely choose a random subset of points to consider, evaluate those points, and take the best—of that limited set.



I remember studying for vocabulary and geography tests using flash cards. I don’t know if the App Generation knows about these things. They were little pieces of paper—two-sided, like most pieces of paper—and on one side you would put a word or a noun or a concept and on the other side you would put a definition or an important characteristic of that thing. For example, one side might be gatto and the other side cat (for an Italian vocab test), or Lima on one side and capital of Peru on the other (for a world geography test).

![](bbox=[0.05, 0.58, 0.95, 0.78])

The process of taking cards out of the deck is a bit like weighting the likelihood of seeing those cards but in an extreme way: it takes the probability down to zero. Now, if I really wanted to be thorough, instead of removing the easy cards, I could add duplicates of the hard cards. The effect would be similar: hard cards would be seen more often and easy cards would be seen less. The difference is that the process would be gradual.

We can apply this same idea—focusing on the hard examples—to a learning system. We start by fitting a Simple-McSimple Model to some hard data. Not surprisingly, we get a lot of examples wrong. But surprisingly, we do get a few right. We refocus our efforts on the harder examples and try again. That repeated process of focusing our efforts on harder examples—and considering the easier examples done(-ish)—is the heart of boosting.