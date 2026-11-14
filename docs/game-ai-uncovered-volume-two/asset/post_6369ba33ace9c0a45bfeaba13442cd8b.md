

![](img/f4a4f6e4de5338a867590c30638990cf_32_0.png)

IMAGE 2.5 A behaviour tree and the representative execution states of an active selector node and a failed child node.

![](img/f4a4f6e4de5338a867590c30638990cf_32_1.png)

IMAGE 2.6 A behaviour tree and the representative execution states of an active selector node moving to its next child.

## 2.4.2 PROBLEM NODES

### 2.4.2.1 Delays and Cooldowns

As mentioned earlier, the delay and cooldown nodes required some consideration. With the possibility of multiple cooldown or delay nodes being active at the same time, it was not possible to store their mutable time remaining state in the blackboard under a single key. Multiple active nodes would fight each other, continuously updating this value and invalidating it for all but the last node to post an updated value. Instead, it was required that each of these nodes have a user-specified and unique key against which their state was pushed to the blackboard. This not only adds some responsibility to those creating and editing trees to pay attention to duplicated blackboard keys but also allows some freedom with it. If a designer could guarantee that two cooldown or delay nodes would not be active at the same time, then they were fine to share the same space in the blackboard to store their mutable state. While this saved a few bytes of memory here and there, it was totally overshadowed by the potential for bugs to be introduced by these particular nodes overwriting each other's data. The additional overhead of keeping an eye on this would have been incentive enough to automate the blackboard key generation for these nodes if only time was not such a limited resource.

### 2.4.2.2 Subtrees

The subtree node's mutable state proved to be a far less stressful issue to resolve. Each NPC has only one behaviour tree active at any one time, with subtrees taking the focus from their parent behaviour tree upon execution starting and handing back focus upon completion. For each executing behaviour tree, an ExecutionState object is required to represent its state, so the solution to allow for tracking multiple behaviour tree states was to replace the single ExecutionState object with a stack of ExecutionState objects. Upon a subtree taking focus, a new ExecutionState was pushed onto the stack representing this behaviour tree. Upon this tree finishing execution, its ExecutionState was then popped from the stack and the parent tree, upon becoming active once again, would have its ExecutionState on the top of the stack in the exact state it was left in when control was originally handed over to the subtree.

## 2.5 CONCLUSION

While the decision to investigate such an invasive change late in the development of The Survivalists at first caused significant concern, confidence was quickly gained when the relatively elegant solution was suggested and prototyped. A lot of this concern stemmed from the sheer amount of data that needed to be moved, how it would be stored and the likelihood of unchecked or unnoticed blackboard key clashes. Once the solution was implemented though, it was quickly realised that a lot of the data used to track a behaviour tree's state was in fact superfluous. Instead, the relevant data being inferred at the cost of a few more clock cycles, clock cycles that became easier to justify using the frantic attempts to find more memory became more time-sensitive.

## 3 Monkey Business NPC Player Imitation in Team17's The Survivalists

Steven Dalton

### 3.1 INTRODUCTION

A key gameplay component of The Survivalists is the crafting mechanic allowing players to construct, strengthen and protect their settlements, forge tools and weapons to aid in exploration and concoct and create recipes for health and statistic-boosting meals among many other commodities. Those who have played games with an emphasis on resource gathering and crafting will be aware of the amount of time that must be committed to farming and harvesting these resources and to the potentially lengthy process of construction, especially when creating more valuable items on offer.

In The Survivalists, the player is encouraged to focus more on exploration than on the grind of crafting items and building bases. To reduce the amount of time, a player must commit to the farming and crafting processes, side-quests exist that see the player rescuing and befriending a maximum of twenty monkey companions from the clutches of the evil inhabitants of the game's numerous islands. These new friends can be commanded to mimic any of the actions that the player can perform, automating tasks that would have otherwise taken up a significant amount of the player's time, time that can instead be spent exploring the game's world and even used to further bolster the number of helpful monkey companions.

### 3.2 WORK SMART, NOT HARD

The intention of adding the companion non-player characters (NPCs) was to empower the player to offload the time-consuming tasks in order to use their time for other activities. To achieve this, the player must be able to issue commands to their simian assistants, preferably without having to trudge through numerous menus, after all the goal is to save the player time. This is achieved by giving the monkeys the ability to observe the player when performing a task to interpret the individual steps into a sequence of bespoke actions that they can then perform to repeat the process. To achieve this, a banana is thrown to the monkey(s) to be given a task, putting them into an observation state in which they will record everything the observed party is doing. They will continue to observe the actions performed by the player for a brief period until they either lose interest (a 30-second timer expires) or until they fully observe a task that they are capable of performing. They will then perform this task until it is no longer possible due to resources being exhausted, a required equipped item expires or the player instructs them to stop or to observe a new action.

The actions that the player and monkeys can perform include, but are by no means limited to:

- Chop down trees and shrubbery (requires a cutting tool such as an axe or a sword).
- Destroy rocks (requires a clobbering tool such as a pickaxe and the like).
- Gather resources from the ground, such as wood from felled trees and stone from destroyed rocks.
- Deliver gathered resources to designated locations such as storage chests, placed constructable blueprints or crafting benches.
- Craft items from player-generated blueprints at crafting benches.

Given this list of actions, it is possible to take your primitive accomplices to an area rich in resources, such as trees and rocks, and set up a production line resulting in the creation of the most basic of items through to rather complex items, crafting a plethora of required ingredients along the way. The process might look something like this, given a troop of four monkey companions, each instructed to perform a different task, and the most basic of resources:

- Monkey #1, wielding an axe, will cut down trees, producing timber.
- Monkey #2, wielding a pickaxe, will break rocks, producing stone shards.
- Monkey #3, crafting tool in hand, will attend to any player-generated blueprints on three nearby crafting benches and will craft:
  - Tool handles out of wood from fallen trees,
  - Axe blades out of stone from destroyed rocks and
  - Axes, from the tool handles and axe blades created at the other crafting benches.
- Monkey #4, will collect and deliver any resources required by the three crafting benches.

This is shown in Image 3.1, which is a screenshot from *The Survivalists* and shows the monkey companions working on their tasks. This process could be expanded to craft more complex tools and items at crafting benches, to creating static structures, or to even building additional crafting benches. This results in a process that takes the simplest of materials and eventually, given a large enough workforce and sufficient resources, crafts the most complex and time-consuming objects available. All of this is achievable by having a troop of monkey buddies each watch the player perform a different task only once and then copying it ad infinitum.

