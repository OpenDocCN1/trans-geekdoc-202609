So we can start our approach to algorithms with a problem that we can solve by just writing down. Suppose we have two sets of objects and want to spread the objects of one of the two sets as evenly as possible among the objects of the other set. We will use crosses (×) for the objects of the first set and bullets (•) for the objects of the second set. We want to spread out crosses among the bullets.

If the number of crosses divides the total number of objects, that is easy. We just partition the crosses among the bullets as if we would do division. For example, if we have 12 objects in total, out of which three are crosses and nine are bullets, we put one cross, then three bullets, then one cross, three bullets, and finally another cross and three bullets:

× • • × • • • × • •

But what if the total number of objects, crosses and bullets taken together, cannot be divided exactly by the crosses? What can we do if we have five crosses and seven bullets?

We start by putting all crosses followed by all bullets in one row as follows:

× × × × • • • • •