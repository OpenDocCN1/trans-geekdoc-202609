
# Decision Tree Complexity

## Complexity Analysis

Suppose the training data contains `n` instances and `m` attributes. We need to make some assumptions about the size of the tree, and we will assume that its depth is on the order of log `n`, `O(log n)`<mml:math><mml:mi>O</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>log</mml:mi><mml:mi mathvariant="italic">n</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000236si25.png). This is the standard rate of growth of a tree with `n` leaves, provided that it remains “bushy” and does not degenerate into a few very long, stringy branches. Note that we are tacitly assuming that most of the instances are different from each other and—this is almost the same thing—that the `m` attributes provide enough tests to allow the instances to be differentiated. For example, if there were only a few binary attributes they would allow only so many instances to be differentiated and the tree could not grow past a certain point, rendering an “in the limit” analysis meaningless.

The computational cost of building the tree in the first place is

`O(m n log n)`.<mml:math><mml:mi mathvariant="normal">O</mml:mi><mml:mo>(</mml:mo><mml:mi mathvariant="italic">mn</mml:mi><mml:mi>log</mml:mi><mml:mi>n</mml:mi><mml:mo>)</mml:mo><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000236si26.png)

Consider the amount of work done for one attribute over all nodes of the tree. Not all the examples need to be considered at each node, of course. But at each possible tree depth the entire set of `n` instances must be considered. And because there are log `n`<mml:math><mml:mi>log</mml:mi><mml:mi>n</mml:mi></mml:math>![Equation](images/F000236si27.png) different depths in the tree the amount of work for this one attribute is `O(n log n)`<mml:math><mml:mi mathvariant="normal">O</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>n</mml:mi><mml:mi>log</mml:mi><mml:mi>n</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000236si28.png). At each node all attributes are considered so the total amount of work is `O(m n log n)`<mml:math><mml:mi mathvariant="normal">O</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi mathvariant="italic">mn</mml:mi><mml:mi>log</mml:mi><mml:mi>n</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000236si29.png).

This reasoning makes some assumptions. If some attributes are numeric they must be sorted but once the initial sort has been done there is no need to re-sort at each tree depth if the appropriate algorithm is used (described earlier). The initial sort takes `O(n log n)`<mml:math><mml:mi mathvariant="normal">O</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>n</mml:mi><mml:mi>log</mml:mi><mml:mi>n</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000236si30.png) operations for each of up to `m` attributes; thus the earlier complexity figure is unchanged. If the attributes are nominal all attributes do *not* have to be considered at each tree node because attributes that are used further up the tree cannot be reused. However, if attributes are numeric they can be reused and so they have to be considered at every tree level.

Next consider pruning by subtree replacement. First an error estimate must be made for every tree node. Provided that counts are maintained appropriately this is linear in the number of nodes in the tree. Then each node needs to be considered for replacement. The tree has at most `n` leaves, one for each instance. If it were a binary tree, each attribute being numeric or two-valued, that would give it `2n − 1`<mml:math><mml:mn>2</mml:mn><mml:mi>n</mml:mi><mml:mo>&#8722;</mml:mo><mml:mn>1</mml:mn></mml:math>![Equation](images/F000236si31.png) nodes; multiway branches would only serve to decrease the number of internal nodes. Thus the complexity of subtree replacement is

`O(n)`.<mml:math><mml:mi mathvariant="normal">O</mml:mi><mml:mo>(</mml:mo><mml:mi>n</mml:mi><mml:mo>)</mml:mo><mml:mi>.</mml:mi></mml:math>

![Equation](images/F000236si32.png)

Finally, subtree lifting has a basic complexity equal to subtree replacement. But there is an added cost because instances need to be reclassified during the lifting operation. During the entire process each instance may have to be reclassified at every node between its leaf and the root as many as `O(log n)`<mml:math><mml:mi mathvariant="normal">O</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>log</mml:mi><mml:mi>n</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000236si33.png) times. That makes the total number of reclassifications `O(n log n)`<mml:math><mml:mi mathvariant="normal">O</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>n</mml:mi><mml:mi>log</mml:mi><mml:mi>n</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000236si34.png). And reclassification is not a single operation; one that occurs near the root will take `O(log n)`<mml:math><mml:mi mathvariant="normal">O</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>log</mml:mi><mml:mi>n</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000236si35.png) operations, and one of average depth will take half of this. Thus the total complexity of subtree lifting is as follows:

`O(n (log n)^2)`.<mml:math><mml:mi mathvariant="normal">O</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>n</mml:mi><mml:msup><mml:mrow><mml:mo stretchy="false">(</mml:mo><mml:mi>log</mml:mi><mml:mi>n</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msup><mml:mo stretchy="false">)</mml:mo><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000236si36.png)

Taking into account all these operations the full complexity of decision tree induction is

`O(m n log n) + O(n (log n)^2)`.<mml:math><mml:mi mathvariant="normal">O</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi mathvariant="italic">mn</mml:mi><mml:mi>log</mml:mi><mml:mi>n</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>+</mml:mo><mml:mi mathvariant="normal">O</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>n</mml:mi><mml:msup><mml:mrow><mml:mo stretchy="false">(</mml:mo><mml:mi>log</mml:mi><mml:mi>n</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msup><mml:mo stretchy="false">)</mml:mo><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000236si37.png)

### From Trees to Rules

It is possible to read a set of rules directly off a decision tree, as noted in [Section 3.4](#Ch003_67-89_B9780443158889000042.xhtml#s0025), by generating a rule for each leaf and making a conjunction of all the tests encountered on the path from the root to that leaf. This produces rules that are unambiguous in that it does not matter in what order they are executed. However, the rules are more complex than necessary.

The estimated error rate described previously provides exactly the mechanism necessary to prune the rules. Given a particular rule each condition in it is considered for deletion by tentatively removing it, working out which of the training examples are now covered by the rule, calculating from this a pessimistic estimate of the error rate of the new rule, and comparing this with the pessimistic estimate for the original rule. If the new rule is better delete that condition and carry on, looking for other conditions to delete. Leave the rule when there are no conditions left that will improve it if they are removed. Once all rules have been pruned in this way it is necessary to see if there are any duplicates and remove them from the rule set.
