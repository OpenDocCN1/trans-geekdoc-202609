Suppose that after recording these facts, we see Adams run by again. Forgetting that we already recorded his jogging, we now try the following update:

**add:** The Person with surname 'Adams' jogs.

![](bbox=[0.285, 0.185, 0.725, 0.335])

FIG. 4.2 A unary fact type with sample population.

![](bbox=[0.245, 0.385, 0.785, 0.49])

FIG. 4.3 Is this update allowed?

If accepted, this update may be pictured as shown in Fig. 4.3. The database is a variable whose population at any state is a set of facts. Because the fact that Adams jogs was already present, if this fact were added again the population would remain unaltered because sets are insensitive to repetition. For example, the set {Adams jogs, Adams jogs} is identical to the set {Adams jogs}. Sets are defined simply by their membership, and don’t change if we display a member more than once (even if this is unusual). So, the two fact tables shown in Fig. 4.3 are equivalent if we look at each as a set of instances. Hence, there is no problem with accepting the update.

From the internal viewpoint, however, when a fact is added to a database it is typically stored in a previously unallocated space. So, accepting this update would cause the fact that Adams jogs to be stored twice, in separate locations. This is an example of redundancy. If redundancy occurs, the database is a bag of facts rather than a set of facts. A bag or multiset is just like a set, except repetition of its members is significant. For example, although the sets {1} and {1, 1} are equal, the bags [1] and [1, 1] are different.

Avoiding redundancy in a database helps maintain its integrity by simplifying the correct handling of updates. For instance, suppose the fact that Adams jogs is stored twice in the database. If we later wanted to delete or change this fact, then we would need to take care to do this for both its recorded instances. Controlling redundancy in this way can be a headache, and uncontrolled redundancy can lead to inconsistency.