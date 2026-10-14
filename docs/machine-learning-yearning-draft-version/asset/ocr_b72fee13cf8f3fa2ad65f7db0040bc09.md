# 14 Error analysis: Look at dev set examples to evaluate ideas

![](bbox=[0.32, 0.18, 0.68, 0.37])

When you play with your cat app, you notice several examples where it mistakes dogs for cats. Some dogs do look like cats!

A team member proposes incorporating 3rd party software that will make the system do better on dog images. These changes will take a month, and the team member is enthusiastic. Should you ask them to go ahead?

Before investing a month on this task, I recommend that you first estimate how much it will actually improve the system’s accuracy. Then you can more rationally decide if this is worth the month of development time, or if you’re better off using that time on other tasks.

In detail, here’s what you can do:

+   1. Gather a sample of 100 dev set examples that your system misclassified. I.e., examples that your system made an error on.
+   2. Look at these examples manually, and count what fraction of them are dog images.

The process of looking at misclassified examples is called error analysis. In this example, if you find that only 5% of the misclassified images are dogs, then no matter how much you improve your algorithm’s performance on dog images, you won’t get rid of more than 5% of your errors. In other words, 5% is a “ceiling” (meaning maximum possible amount) for how much the proposed project could help. Thus, if your overall system is currently 90% accurate (10% error), this improvement is likely to result in at best 90.5% accuracy (or 9.5% error, which is 5% less error than the original 10% error).