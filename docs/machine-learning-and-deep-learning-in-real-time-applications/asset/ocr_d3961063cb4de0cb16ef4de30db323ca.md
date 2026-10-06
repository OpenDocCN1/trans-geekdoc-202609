The visualization of the TensorBoard window is given in Figure 22 (Aaryan, 2018).

Figure 22. TensorBoard Window (Aaryan, 2018)

![](bbox=[0.181, 0.215, 0.818, 0.613])

The first step to visualize the graph with TensorBoard is to write the logs of the program. For this, we need to create a writer for those logs using below line of code:

Figure 23.

```
writer = tf.summary.FileWriter([logdir], [graph])
```

When logdir is the directory where we want to store the log file, the second argument is the graph of the program on which we will work. There are two methods to get the graph:

+   - Creating the writer out of the session using tf.default_graph() function, which returns the default graph of the program.
- Creating the writer inside the session using sess.graph, which returns the graph of the session.