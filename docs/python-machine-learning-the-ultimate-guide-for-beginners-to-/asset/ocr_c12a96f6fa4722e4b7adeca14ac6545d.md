is calculated as the mode value of the total observation.
This means that if we have an unknown data observation,
we can predict with the help of the mode value. Keep in
mind that mode values are the values that we find the most
frequently in a given set of values. On the other hand,
regression trees extract the value from the training data in
the form of the mean of the total observations. This mean
value is then used to calculate any missing data
observations.

+   3. Regression and classification trees rely on binary splitting.
+   This concept involves going from the top of the tree to the
+   bottom. This means that when we have observations in
+   one region of the tree, there are a number of branches
+   below it that are divided. The division happens within the
+   predictor space. This concept is also often referred to as
+   greedy because the algorithm seeks the variable that is
+   needed for the current split that is being analyzed. The
+   operation does not take any future splits in consideration
+   and that is why sometimes we don’t have the most
+   accurate results. This issue needs to be taken into
+   consideration in order to counteract its effects with various
+   methods and create a better decision tree.

Now let’s discuss more about the concept of splitting and see where
it occurs. As already mentioned, splitting directly affects the accuracy
of the decision trees. This means that if we are applying a number of
algorithms on a decision tree, they will all affect the way a data node
is divided into a number of subnodes. At this time you should keep in
mind the differences between the two decision tree categories. The
subnodes that are created as a result of splitting will maintain some
form of uniformity. In addition, the node splitting is performed on
every variable, however only the most uniform subnodes are selected.
This process involves some mathematics and we will not
dig deeper into the details. It’s enough to understand the theory
behind the process in order to start building the decision trees. With
that being said, let’s see how to work with them in an application.