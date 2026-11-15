![](bbox=[0.18, 0.09, 0.785, 0.285])

FIG. 15.22 AND composition of states (a) decomposed and (b) composed.

This approach is sometimes known as AND composition because we are in one state in region R *and* one state in region T. Another way of looking at this is to see it as an AND composition of OR compositions (because in any orthogonal region we can only be in one state at a time).

One additional feature shown in Fig. 15.22(b) is the use of a guard associated with the transition from state V to state U. The guard condition must evaluate to “True” to enable the transition. The result is that event F will not trigger the transition in region R unless we are in state Y in region T. This is consistent with the equivalent transition in Fig. 15.22(a) between state V-Y and state U-Y.

Although the savings made by OR and AND composition may appear trivial in simple examples, they can become very significant in larger models. For instance, in Fig. 15.22(b), region R has two substates and region T has three substates. If these were increased to four substates and five substates, respectively, the orthogonal version would have (4 + 5) = 9 nodes, but the nonorthogonal version would have (4 x 5) = 20 nodes.

It’s important to recognize that state models are primarily intended to define the locus of control within a given scope. A state model does not in itself define any actions that should be taken. However, an action definition can be linked to the state model to identify the (relative) time that the action should be taken.

The main possibilities are for actions to take place as part of a particular transition from one state to another (Mealy semantics) or in a particular state (Moore semantics). Within a state, we can further distinguish between actions that are taken just after the state is entered, sometime during the state, or just before the state is exited.

So far, we’ve looked at some basic ideas about describing information dynamics in a generic way. The features of process- and state-based models discussed so far can be found in many methodologies and tools that address this area. To provide a more concrete illustration, we turn to one of the most widely used modeling approaches: the unified modeling language (UML).