not beneficial to the player but are required as part of the challenge of creating an environment that minimises this wasted time.

These problems lend themselves naturally to a utility system. You can continuously determine the utility between each actor and task pairing, and then assign out the pairings in order at the end of each evaluation cycle. This provides automated 'ant-farm'-type behaviour where the environment requires minimum player oversight, freeing them to make more high-level decisions within the game as they are relatively unburdened by micro-management.

# 11.3 UTILITY TASKS

A task is defined as a self-contained logical construct that is made up of two parts:

+   1. The utility function, which takes an actor state and produces a value that is a combination of the priority of the task for the current world state and the suitability of the actor.
+   
+   2. The behaviour of any actor assigned to it, which specifies how an actor assigned to the task must complete it. The complexity of the behaviour can vary considerably, as it is highly context-dependent, but is typically a graph of atomic actions that need to be performed or a behaviour tree.

When determining a utility function, you must consider not only which tasks are preferable to perform over others, but also which individuals are best placed to perform them – and the relationship between the two.

This is highly context-dependent, but a starting point is often the distance between the actor and the task. For example, you may prefer Task A is completed over Task B all things being equal, but Task B may be very close to an actor and Task A very far away.

Similarly, it is often a good idea to encourage tasks whose conditions are more difficult to satisfy by giving them higher utility. This not only helps to produce a more even spread of executed tasks but also helps ensure that rare tasks are able to be executed at all.

Let us take what appears to be a relatively simple example, a fire that needs putting out. There are multiple considerations here: Do you prefer actors near a fire extinguisher or near the fire? If the latter, do you prefer fire extinguishers near the fire or near the actor? What if the agent already holds a fire extinguisher? Should you hold a task for every fire and assign them out, even if they are in proximity, or should you group them together into single tasks, or lower the priority if nearby tasks are already assigned to actors? Does the answer to that depend on how far the actors and extinguishers are from the fires, whether they are likely to spread, and how long an extinguisher can be used before it runs out?

As you can see, the complications can quickly spiral out of control, so it is often wise to start with the simplest implementation and see how that feels, rather than trying to create an optimal result – more complexity slows evaluation and makes understanding the system more difficult for both players and creators. In practice, simpler implementations are often sufficient and even preferred.