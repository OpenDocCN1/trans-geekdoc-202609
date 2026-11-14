is that it allows for smarter AI that can reason how their actions affect the world state and future actions.

# ## 18.2.1 SIMPLE NUMERICAL PLANNING

Simple numerical planning problems are deterministic, fully observable, and can reason about numbers but do not deal with time. The framework described is expressive enough to model and find solutions to complete all campaigns of Evil Genius 2, Sniper Elite 5, Zombie Army 4, and many others.

# ## 18.2.1.1 Domain

A planning system needs an abstract model of the game that it needs to play, a so-called Domain. This includes the following information:

+   - The type of things that can exist in the game. For example, Player, Enemy, Location, Door, Key, and the like. Each type can also be a supertype of other types, for instance, you could define a Type Actor that is the supertype of Player or Enemy.

+   - The properties between these types. These denote their relationships using first-order predicate logic. Each predicate has a name and a sequence of types. For example:
+     - (at Actor Location), an `Actor` can be **at** a `Location`;
+     - amount Item Actor), an `Actor` can have an **amount** of `Items`. Numerical predicates are prefixed with a #.

+   - And finally, the actions the player can perform in the game. Each action has a name, a sequence of named types, specifies when it is applicable (its preconditions), and how it affects the world state (its effects). For example, for a player to move from location A to location B, the player must be at location A and there must be a valid path from location A to B. The effect on the world of this action is that the player is no longer at location A but is now at location B, see Code Listing 18.1 for the full definition using PDDL notation.

```
Code Listing 18.1: A Move action.

(:action Move
  :parameters (?p - Player ?from ?to - Location)
  :precondition (and
    (at ?p ?from)
    connected ?from ?to))
  :effect (and
    (not (at ?p ?from))
    (at ?p ?to))
)
```