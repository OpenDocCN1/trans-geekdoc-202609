The datasets used for these phases are:

+   1. Hold-out test set
+   2. Validation test set
+   3. Training set

We can relate these phases and datasets to the factory machine scenario. This time, I'll work from the inside out.

+   1. The training set is used to adjust the knobs on the factory machine.
+   2. The validation test set is used to get a non-taught-to-the-test evaluation of that finely optimized machine and help us pick between different optimized machines.
+   3. The hold-out test set is used to make sure that the entire process of building one or more factory machines, optimizing them, evaluating them, and picking among them is evaluated fairly.

The last of these is a big responsibility: there are many ways to peek and be misled by distractions. If we train and validation-test over and over, we are building up a strong idea of what works and doesn't work in the validation test set. It may be indirect, but we are effectively peeking at the validation test set. The hold-out test set—data we have never used before in any training or validation-testing for this problem—is necessary to protect us from this indirect peeking and to give us a fair evaluation of how our final system will do with novel data.

# 5.2.2.2 Terms for Test Sets

If you check out a number of books on machine learning, you'll find the term validation set used, fairly consistently, for Selection. However, when you talk to practitioners, folks will verbally use the phrase test set for both datasets used for Selection and for Assessment. To sweep this issue under the carpet, if I'm talking about evaluation and it is either (1) clear from context or (2) doesn't particularly matter, I'll use the generic phrase testing for the data used in either Assessment or Selection. The most likely time that will happen is when we aren't doing Selection of models—we are simply using a basic train-test split, training a model and then performing a held-out evaluation, Assessment, on it.

If the terms do matter, as when we're talking about both phases together, I'll be a bit more precise and use more specific terms. If we need to distinguish these datasets, I'll use the terms hold-out test set (HOT) and validation set (ValS). Since Assessment is a one-and-done process—often at the end of all our hard work applying what we know about machine learning—we'll be talking about the HOT relatively infrequently. That is not to say that the HOT is unimportant—quite the contrary. Once we use it, we can never use it as a HOT again. We've peeked. Strictly speaking, we've contaminated both ourselves and our learning system. We can delete a learning system and start from scratch, but it is very difficult to erase our own memories. If we do this repeatedly, we'd be right back into teaching to the test. The only solution for breaking the lockbox of the HOT is