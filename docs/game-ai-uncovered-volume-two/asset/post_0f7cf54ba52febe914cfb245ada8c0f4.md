
## REFERENCES

- Coleridge, S., and Shawcross, J. (2001) Biographia Literaria. London: Electric Book Co.
- Fogg, B., and Tseng, H. (1999) The elements of computer credibility. Proceedings of the SIGCHI Conference on Human Factors in Computing Systems the CHI is the Limit – CHI ’99, New York.
- Frank, A., Stern, A., and Resner, B. (1997) Socially intelligent virtual petz. Socially Intelligent Agents. AAAI Fall Symposium, [online] pp 43–45. Available at: <http://alumni.media.mit.edu/~benres/verbiage/Socially%20Intelligent%20Virtual%20Petz.htm#:~:text=Socially%20Intelligent%20Virtual%20Petz&text=We%20have%20developed%20a%20series,layered%20D3D%20animation%20and%20sound.>; [Accessed 7 August 2022].
- Lombard, M., and Ditton, T. (2006) At the heart of it all: The concept of presence. Journal of Computer-Mediated Communication, 3(2). Available at: https://academic.oup.com/jcmc/article/3/2/JJCMC321/4080403
- Reeves, B., and Nass, C. (2003) The Media Equation: How People Treat Computers, Television, and New Media Like Real People and Places. Center for the Study of Language and Information Publication, Cambridge University Press.
- Reynaud, Q., Donnart, J., and Corrublo, V. (2014) Evaluating the believability of virtual agents with anticipatory abilities. Proceedings of the 2014 International Conference on Autonomous Agents and Multi-Agent Systems, Paris, pp. 1533–1534.
- Rosenskind, M., Winstanley, G., and Blake, A. (2012) Adapting bottom-up, emergent behaviour for character-based AI in games. Research and Development in Intelligent Systems, XXIX, pp. 333–346.
- Thomas, F., and Johnston, O. (1995) The Illusion of Life. New York: Hyperion.
- Warpefelt, H., and Johnston, O. (2016) The Non-Player Character – Exploring the believability of NPC presentation and behaviour. Ph.D. Stockholm University.
- Warpefelt, H., Johansson, M., and Verhagen, H. (2013) Analyzing the believability of game character behaviour using the Game Agent Matrix. Proceedings of DiGRA 2013: DeFragging Game Studies, Atlanta, GA.

## 18 Automated Testing Using AI Planning

Dr Bram Ridder

### 18.1 INTRODUCTION

As games are growing ever larger and more complex, the need for testing, and the time it takes to test a game, has increased. There are many well-established types of automated tests like unit tests, functional tests, and smoke tests. These tests gather performance metrics like frames per second, memory usage, loading times, bandwidth usage, and many more. They also perform code coverage, detect crashes, fire asserts, and create error logs, amongst a plethora of other functions. This data is invaluable for development teams to optimise and stabilise their games.

This chapter will focus on automated testing i.e., tests that play the game as a player by simulating keyboard, mouse, and game controller inputs. Most solutions that are used to test games like this use a combination of pre-generated scripts, behaviour trees (BTs), finite-state machines (FSM), and reinforcement learning agents. They load a level and test it for a certain amount of time and then quit. Taking this a step further, an AI framework will be described that is capable of consistently completing entire games from start to finish. The benefits of such a system are manyfold. Not only does it provide more extensive code coverage and metrics that better reflect the game, but it can also detect game and level design issues. If the framework is unable to complete a game, then this is usually due to a coding bug or issue with the level or game design. The system described in this chapter has been successfully utilised to complete games such as _Zombie Army 4_, _Evil Genius 2_, and _Sniper Elite 5_, amongst others.

### 18.2 AI PLANNING

The roots of planning can be traced back to STRIPS, a planning language that defines an initial state and goal as propositional values and a set of actions. Each action has a precondition, which dictates when an action can be executed, and an effect which details how a state is updated after applying the action. A solution to such a planning problem is a sequence of actions that, when applied to the initial state, leads to a state where all the goal conditions are true. The most notable application of AI planning systems in the games industry is Goal-Oriented Action Planning (GOAP). This was first popularised by _FEAR_ and has since been used in various other projects like _Tomb Raider_, _Assassins Creed_, and _Middle-earth: Shadow of Mordor_ games. One of the main benefits of such deliberate systems, compared to reactive systems like BTs, is that it allows for smarter AI that can reason how their actions affect the world state and future actions.

### 18.2.1 SIMPLE NUMERICAL PLANNING

Simple numerical planning problems are deterministic, fully observable, and can reason about numbers but do not deal with time. The framework described is expressive enough to model and find solutions to complete all campaigns of Evil Genius 2, Sniper Elite 5, Zombie Army 4, and many others.

### 18.2.1.1 Domain

A planning system needs an abstract model of the game that it needs to play, a so-called Domain. This includes the following information:

- The type of things that can exist in the game. For example, Player, Enemy, Location, Door, Key, and the like. Each type can also be a supertype of other types, for instance, you could define a Type Actor that is the supertype of Player or Enemy.
- The properties between these types. These denote their relationships using first-order predicate logic. Each predicate has a name and a sequence of types. For example:
  - (at Actor Location), an `Actor` can be **at** a `Location`;
  - (#amount Item Actor), an `Actor` can have an **amount** of `Items`. Numerical predicates are prefixed with a #.
- And finally, the actions the player can perform in the game. Each action has a name, a sequence of named types, specifies when it is applicable (its preconditions), and how it affects the world state (its effects). For example, for a player to move from location A to location B, the player must be at location A and there must be a valid path from location A to B. The effect on the world of this action is that the player is no longer at location A but is now at location B, see Code Listing 18.1 for the full definition using PDDL notation.

```
Code Listing 18.1: A Move action.

(:action Move
  :parameters (?p - Player ?from ?to - Location)
  :precondition (and
    (at ?p ?from)
    (connected ?from ?to))
  :effect (and
    (not (at ?p ?from))
    (at ?p ?to))
)
```

### 18.2.1.2 The Problem

During runtime, an *instance* of the domain is created, which consists of the initial state, a representation of the current game world, and the goal we are trying to achieve. This is a problem that the AI Planner is tasked to solve.

### 18.2.1.2.1 The Initial State

The initial state consists of all *Objects* that are part of the world. Each object has a unique name and is of a certain type that is defined in the domain. For example:

- p – Player, object *p* of type *Player*.
- blue_key – Key, object *blue_key* of type *Key*.

It also contains all *Facts* that are true. A *Fact* is an instance of a predicate, where each *Type* is instantiated with an Object of the correct type or subtype. For example:

- (at p player_loc), the *Player* object p is at the *Location* object *player_loc*,
- (#amount blue_key p)=2, the *Player* object p has two *blue_key* objects.

For boolean predicates, you only declare those *Facts* that are true. This is the so-called closed world principle which means that all *Facts* that are not declared are assumed to be false. For numerical facts, their numerical value is declared.

### 18.2.1.2.2 The Goal

The goal is a logical expression of what value *Facts* must have. For numerical facts, the following expressions are allowed: equal to, less than, greater than, less or equal to, and greater or equal to. For example, a goal could be:

- (and (at p finish_loc) #(amount reactor_cores p)>3)

### 18.2.2 Finding a Solution

Once the initial state and the goal are defined, the AI planner creates all the possible facts and actions that can exist. In a process called *grounding*, all possible facts and *grounded* actions that can exist are constructed by enumerating all possible sets of objects that match the predicate’s types defined in the domain.

For example, starting with the following objects:

- p1, p2 – Player
- loc1, loc2, loc3 – Location

Six Facts will be generated:

- (at p1 loc1)
- (at p1 loc2)
- (at p1 loc3)
