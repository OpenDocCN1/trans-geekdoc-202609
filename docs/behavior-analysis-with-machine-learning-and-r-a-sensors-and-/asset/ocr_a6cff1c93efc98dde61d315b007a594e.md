# CHAPTER 3. PREDICTING BEHAVIOR WITH ENSEMBLE LEARNING

99

train set

![](bbox=[0.244, 0.125, 0.755, 0.463])

Figure 3.1: Bagging example.

Bootstrapping means generating new train sets by sampling instances with replacement from the original train set. If the original train set has $N$ instances, the method selects $N$ instances at random to produce a new train set. With replacement means that repeated instances are allowed. This has the effect of generating a new train set of size $N$ by removing some instances and duplicating other instances. By using this method, $n$ different train sets can be generated and used to train $n$ different learners.

It has been showing that more diverse base learners increases performance. One way of generating diverse learners is by using different train sets as just described. In his original work, Breiman (1996) used decision trees as base learners. Decision trees are considered to be very unstable. This means that small changes in the train set produce very different trees—this is a good thing for bagging! Most of the time, the aggregated predictions produce better than the best individual learner from the ensemble.

Figure 3.1 shows bootstrapping in action. The train set is sampled with replacement 3 times. The numbers represent indices to arbitrary train instances. Here, we can see that in the first sample, the instance number 5 is missing but instead, instance 2 is duplicated. All samples have five elements. Then, each sample is used to train individual decision trees.

One of the disadvantages of ensemble methods is their higher computational time both during