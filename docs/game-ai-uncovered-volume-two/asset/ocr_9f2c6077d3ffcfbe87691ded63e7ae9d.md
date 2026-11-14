# 2.4 MOVING THE MUTABLE STATE

Since the behaviour tree framework was already making use of a blackboard per NPC to store various pieces of NPC and world state to be accessed by behaviour trees, it was initially thought that all states could simply be pushed to the blackboard. This only proved to be unworkable once it was realised how many bespoke blackboard keys would have to be generated, either automatically or by those working with the behaviour trees, to handle all mutable states. For example, if you assume that a single NPC would make use of ten behaviour trees in total, each with an average of ten composite nodes (sequence, selector, etc.). It would require 100 unique blackboard keys to be generated to track the 100 composite nodes’ mutable states that determine their current child to be executed. While by no means impossible, this created an additional task in which unique blackboard keys must either be generated automatically or must be vetted for duplication after being created manually. The act of manually creating and managing this number of unique blackboard keys would have added a layer of complexity and concern to the creation and editing of behaviour trees that could likely be avoided.

# 2.4.1 REMOVING THE MUTABLE STATE

Rather than automatically generating a lot of the blackboard keys and pushing a swathe of additional data to the blackboard, it was investigated whether this step could be removed entirely. Instead, a single structure containing a reference to the current executing behaviour tree, the index of the current executing node and the executing node’s execution status (Running, Failed or Succeeded) was created and maintained, as a behaviour tree was executed. The composite nodes that once relied upon an index into their list of children to be maintained could instead infer what to do next upon a child node terminating by querying this execution state metadata object, as defined in Code Listing 2.1.

```
Code Listing 2.1: A very simple data structure containing
all data required to represent the current state and
infer how to progress a behaviour tree.

public enum ExecutionStatus
{
    Running, Succeeded, Failed
}

public struct ExecutionState
{
    public BehaviourTree _tree;
    public int _nodeIndex;
    public ExecutionStatus _executionStatus;
}
```

Images 2.3–2.6 show how this simple data structure representing a behaviour tree’s state changes when moving between nodes. Rather than relying upon mutable states within the composite nodes, it can simply be inferred what to do next. If the child of a sequence node completes successfully, then it should simply move to the next child, the index of which can be found by finding the failed nodes’ index in the list of children, and selecting the next. If the child fails, then the parent sequence node also fails.