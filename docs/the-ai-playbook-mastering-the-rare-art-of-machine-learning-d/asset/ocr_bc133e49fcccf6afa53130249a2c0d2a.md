Lift applies universally, across ML applications. No matter what you’re using ML for, lift serves as a fundamental, cross-disciplinary metric to report on a model’s pure predictive performance. It provides a straightforward reading on how well the model can identify individuals relatively more likely to behave in a certain way.

But lift can only be calculated for a model once the model has targeted a group. This means it must commit to yes/no predictions that determine which individuals do and which don’t belong in the group. Calculating lift—as well as profit—is possible only in relation to such a group. However, a raw model doesn’t commit. For each individual, it outputs a probabilistic score that ranges across the spectrum of 0 to 100 percent. So, to determine who belongs in the targeted group, a threshold must be established in order to commit to a decision for each individual. Individuals with scores above the threshold belong in the targeted group. So where do you draw that line?

# An Illustrative Example: How Big Is Your TV?

When I teach lift in the classroom, I get everyone to stand up and be the data. Each person holds up a piece of paper with the size of the largest TV in their home and the group arranges itself into a row ordered by TV size:

![](bbox=[0.135, 0.635, 0.865, 0.715])

People in order of their TV size (a zero means they have no TV). Those with a raised hand are subscribed to HBO.

Then I ask a question related to TV usage, such as, “Who has a subscription to HBO?” Not forgetting to thoroughly define the prediction goal, my question is actually more precise: “Who lives in a household that not only uses but pays for a subscription to HBO or Max?”