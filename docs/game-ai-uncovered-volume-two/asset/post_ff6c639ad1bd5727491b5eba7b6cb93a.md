
briefly is a standard behaviour tree, but there are many variations that can be made to tailor it to your needs specifically.

### 5.3.5 HIGH AUTONOMY: PROCEDURAL BEHAVIOURS

An alternate approach to modelling behaviours hierarchically is an approach known as GOAP. With FSMs and Behaviour Trees, we are defining states or actions and then transitioning between them. With GOAP however, we uncouple our states and actions from authored transitions, instead letting a planning system determine the best set of actions that will allow us to reach a set goal. This results in procedural behaviours constructed at runtime, giving our agents the possibility of maximum autonomy.

Goals in GOAP define the resulting state(s) that we want the agent, and/or the world, to be in. For example, having a buddy revive the player. We might consider this goal complete if the player is not currently downed. But how does the buddy complete this task? Through actions. Much like a leaf node in a Behaviour Tree, an action is an encapsulation of some functionality. Actions in GOAP, however, have both pre-conditions that determine if they can be executed and the resulting effects that determine how they change the state of the world and/or agent. They also come with an associated cost set by their author that is used in the planning stage.

With our goals defined, and sub-actions capable of putting the world/agent into a state to satisfy those conditions, we pass over to our planner. This is the stage where a plan of action is generated for our agent. For a given goal, the planner will perform a search, such as A*, over the available actions to find all possible routes from the current state to the goal state. Image 5.5 shows an example of how a goal of ‘Eat’ might look.

![](img/f4a4f6e4de5338a867590c30638990cf_61_0.png)

IMAGE 5.5 GOAP example.

There are two possible paths identified. Overall, it is cheaper for the agent to start a fire and cook ingredients, however, if they do not have any ingredients to cook that branch would not be possible, so they would fall back to the more expensive approach of searching for food. Since the availability of actions differs based on the current game state, the same goal can be achieved in multiple different ways, bringing variability to decision-making that would be difficult to replicate with a fully authored model such as a behaviour tree. The process of determining action sequences at run time allows agents to react dynamically within their world. It also provides a time save for production. With GOAP, there is no need to implement defined behaviours into a complex behaviour tree. Once the new behaviour is implemented, it is simply added to the pool and the planner will do its magic at runtime.

The benefits of GOAP do not come without drawbacks. Depending on how many actions you have, the planning stage can be processor-intensive. For each goal to be evaluated, it will search over all actions available at the time, until the goal is met, within the set action limit. There is also re-validation of the current goal that needs to be done periodically to ensure that the initial game state has not changed, such that the current goal no longer makes sense.

Another consideration, particularly applicable to buddies, is the lack of control over the resulting behaviours. Given they will be generated at runtime based on transient data, the current game state, it might be difficult to reproduce a given set of actions at a particular point in time. The procedural nature of the system means that without tightly controlling the game state, you could not be certain of what behaviours would be executed. This variability will also increase the need for stringent testing of the agent, ensuring that all behaviours can lead into/from one another without issue and that no bad sequences are generated.

GOAP is a great system for bringing plenty of autonomy to an agent, allowing them to determine what to do at runtime without the need for explicit authoring. There are performance considerations to be made, however, if your design permits a highly autonomous agent, this is worth digging deeper into.

## 6 Making Up Your AI's Mind
Decision-Making Architectures

Tobias Karlsson

### 6.1 INTRODUCTION

One of the first and most fundamental decisions you must make when you are creating an AI to control a creature in a game is what decision-making architecture to use. The decision-making architecture is the framework within which your AI decides what behaviour to execute and then executes that behaviour at any given moment. This chapter explores the more popular options available, their respective strengths and weaknesses, and under what circumstances you would choose one over the other.

For this chapter, a behaviour is defined as a set of actions an AI can take to achieve a specific goal or to react to a specific situation. The granularity of each behaviour is up to the implementer, for instance, you could choose to have a behaviour for combat or to have many behaviours for different aspects of combat, such as a behaviour for reloading the AI’s weapon and one for throwing grenades. The granularity you choose depends on what makes sense for the AI in your game. The AI for an individual creature is created by giving it a set of behaviours and the information needed to select the appropriate behaviour at runtime.

### 6.2 IMPORTANT CHARACTERISTICS

There are many different characteristics of decision-making architectures, and which are more important in a given situation depends on the exact nature of the problem you are trying to solve; however, for most projects, many of the following characteristics will have some relevance.

### 6.2.1 PREDICTING BEHAVIOUR SELECTION

Every agent will have a set of behaviours. Some of these behaviours may be quick reactions to a surprising event, whereas others might be a fallback behaviour that is only active if no other good behaviour can be found. It is important to be able to reason about when and under what circumstances a particular behaviour will become active and the priority of one behaviour when compared to another. This might seem like a simple requirement, but as the complexity of your AI grows, keeping track of all the conditions for when behaviours can activate or not and how they interact becomes more and more difficult. Even the simplest of agents tend to acquire an impressive array of tests and conditions for behaviour selection as you get closer to ship, to cover all the possible edge cases. A good decision-making architecture will make it easy for both the author(s) of the AI and anyone who will subsequently have to maintain it, to get a picture of the conditions for when an agent’s various behaviours will be selected for execution by looking at the data.

### 6.2.2 UNDERSTANDING THE STATE OF A DECISION-MAKING PROCESS AT RUNTIME

Even under the best of circumstances, you will find that your AI is going to choose the wrong behaviour as you test it; hence, it is critical to be able to inspect the state of the decision-making process at runtime so that you can determine why an agent decided to do what it did. You need to be able to understand what behaviour your agent is running, why a specific behaviour was selected, and why a specific behaviour was not selected. Ideally, you will also have access to not just the current state of your agent but also to a history of how it got there. Depending on how your architecture selects behaviours, the problem of describing a specific decision can range from trivial to requiring tracking a significant amount of extra data that may also be difficult to display. It is worth noting that having external applications, most commonly the editor pulling double duty, that can connect to an instance of the game and display that agent’s state, is becoming more and more popular. This is a great capability that is something you should seriously consider, but even with an external app, you will want to be able to display at least some of the AI’s state in game for quick debugging. This will allow for better information gathering, which can be used by your QA partners who may not have access to the editor. Something related and very beneficial is the ability to dump the current state of the AI to a file to be inspected later. This allows someone testing the game to easily provide you with a large amount of data about an agent that behaved unexpectedly.

### 6.2.3 MODULARISATION

Being able to create a behaviour from simpler, reusable parts is extremely powerful. Even if your game only has one agent, you will find that there are many functions and tests that recur in most behaviours. Being able to reuse the building blocks is going to save your development time, as you only need to write and test them once. More importantly, you can add metadata to your building blocks to improve your ability to debug your AI. Building blocks are frequently used to assemble the AI’s behaviour in a visual editor, but there are, of course, other options that create the same effect. Another benefit of using building blocks is that it becomes easier to learn and understand the AI system. A new developer only needs to learn how the building blocks work, rather than having to understand the details of each and every behaviour.
