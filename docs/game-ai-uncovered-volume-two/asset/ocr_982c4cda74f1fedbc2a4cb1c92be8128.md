# ## 6.2.4 Hierarchical Decision-Making

Modelling decision-making as a hierarchy of decisions can be very helpful. It matches well with how humans think about decisions. You make the big picture decision first, and then add more and more detailed decisions until you eventually reach the point where no more decisions need to be made and actions can be taken. An additional advantage of hierarchical decision-making is that it allows multiple behaviours to share decisions, meaning that you do not have to make the same calculations twice. For instance, if you have several behaviours that depend on there being a valid path to the targeted enemy, then collecting them all under one instance of that test in a hierarchy, allows you to make the test once and reject all of the behaviours together if the test fails. This also helps by making it easier to understand how an agent is going to behave, as decisions are split up into multiple, simpler decisions, and by runtime debugging becoming correspondingly simplified as it is easy to see where in a hierarchy a decision node failed.

# ## 6.2.5 Ease of Adding New Behaviours

Whenever you add a new behaviour to a character, you must ensure that it interacts well with all existing behaviours. This is always going to require some work, but some architectures make it easier to localise the changes, while others inherently have more dependencies between behaviours that need to be explicitly dealt with.

# ## 6.2.6 Ability to Model States and State Transitions

Often, AIs have distinct states that they can be in, with procedures for how to transition between them. An example of states that commonly occur in games is an agent being in either an *Idle*, *Alert*, or *Combat* state. Each of these states will come with a particular selection of valid behaviours, and the transitions between these states often require a specific process, for example, playing a surprised reaction when transitioning from *Idle* directly to *Combat*. In games, you will most often find clear instances of states at the very highest level of an AI as in the case of the idle-alerted-combat scenario, and at the very lowest levels, such as how a melee grapple attack works.

# ## 6.2.7 Sequencing Behaviour

The ability to sequence behaviour, i.e., first do A, then B, then C in that order is often very useful if the AI is to execute some more complex behaviour. Sequencing is a sub-problem of states and state transitions but can be implemented without states. Sequencing is normally relatively easy within an individual behaviour building block but becomes more difficult when creating sequences of separate behaviours, something that is usually desirable for modularisation.