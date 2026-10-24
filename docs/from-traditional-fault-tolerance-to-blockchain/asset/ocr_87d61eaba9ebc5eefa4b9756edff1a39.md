message). For the v variables corresponding to other lieutenants, a lieutenant uses the values set in step (3) of the immediate lower level recursion instance it has started.

To illustrate how the augmented rules for step (3) works, consider the following example with f = 2.

# EXAMPLE 7.3

In this example, we show how the OM(2) algorithm works with 7 generals. The basic steps are highlighted in Figure 7.3. As can be seen, OM(2) will trigger three levels of recursion, from OM(2) to 6 instances of OM(1), and 6 x 5 = 30 instances of OM(0) (to avoid cluttering, we only included 6 instances of OM(0) in Figure 7.3).

![](bbox=[0.28, 0.4, 0.78, 0.84])

Figure 7.3 The message flow and the basic steps of the OM(2) algorithms.

At the end of step (2) of the OM(1) instance that is started by lieutenant i, a lieutenant j ≠ i receives 4 messages sent in the