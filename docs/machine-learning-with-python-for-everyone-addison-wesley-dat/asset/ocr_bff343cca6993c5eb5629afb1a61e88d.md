Phew, that was a lot of work to verify the answer. Often, we can make use of shortcuts to reduce the number of calculations we have to perform. Sometimes these shortcuts are from knowledge of the problem and sometimes they are clever applications of the rules of probability we’ve seen so far. If we see multiplication, we can mentally think about the two-dice scenario. If we have a scenario like the dice, we can multiply.

# 2.4.3 Conditional Probability

Let’s create one more scenario. In classic probability-story fashion, we will talk about two urns. Why urns? I guess that, before we had buckets, people had urns. So, if you don’t like urns, you can think about buckets. I digress.

The first urn U_I has three red balls and one blue ball in it. The second urn U_II has two red balls and two blue balls. We flip a coin and then we pull a ball out of an urn. If the coin comes up heads, we pick from U_I; otherwise, we pick from U_II. We end up at U_I half the time and then we pick a red ball 3/4 of those times. We end up at U_II the other half of the time and we pick a red ball 2/4 of those times. This scenario is like wandering down a path with a few intersections. As we walk along, we are presented with a different set of options at the next crossroads.

![](bbox=[0.25, 0.48, 0.8, 0.73])

Figure 2.1 A two-step game from coins to urns.

If we sketch out the paths, it looks like Figure 2.1. If we count up the possibilities, we will see that under the whole game, we have five red outcomes and three blue outcomes. P(red) = 5/8. Simple, right? Not so fast, speedy! This counting argument only works when we have equally likely choices at each step. Imagine we have a very wacky coin that causes me to end up at Urn I 999 out of 1000 times: then our chances of picking a red ball would end up quite close to the chance of just picking a red ball from Urn I. It would be similar to almost ignoring the existence of Urn II. We should account for this difference and, at the same time, make use of updated information that might come along the way.