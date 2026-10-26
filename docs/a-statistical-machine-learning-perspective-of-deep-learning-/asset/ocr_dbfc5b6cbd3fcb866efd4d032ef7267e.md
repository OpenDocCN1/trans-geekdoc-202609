![](bbox=[0.02, 0.03, 0.07, 0.16])

# Cavs Enables Batched Computation

+   - Batched computation is natural and automatic in Cavs
+     - Cavs transforms the backpropagation as **evaluating F on nodes of a batch of input graphs**, see the figure below.
+   - Then, batched computation can be realized by
+     - Figure out a set of vertices that we are ready to evaluate F on
+     - Batch the evaluation of F on this set of vertices
+     - Pass the output of F to their parent vertices