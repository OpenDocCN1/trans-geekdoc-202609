
As in the case of standard search algorithms applied to sensorless problems, the `AND–OR search algorithm` treats belief states as black boxes, just like any other states. One can improve on this by checking for previously generated belief states that are subsets or supersets of the current state, just as for sensorless problems. One can also derive incremental search algorithms, analogous to those described for sensorless problems, that provide substantial speedups over the black-box approach.

## 4.4.4 An agent for partially observable environments

An agent for partially observable environments formulates a problem, calls a search algorithm (such as `AND-OR-SEARCH`) to solve it, and executes the solution. There are two main differences between this agent and the one for fully observable deterministic environments. First, the solution will be a conditional plan rather than a sequence; to execute an `if–then–else` expression, the agent will need to test the condition and execute the appropriate branch of the conditional. Second, the agent will need to maintain its belief state as it performs actions and receives percepts. This process resembles the prediction–observation–update process in [Equation (4.5)](#Chapter04-04.xhtml#eq4-5) but is actually simpler because the percept is given by the environment rather than calculated by the agent. Given an initial belief state `b`, an action `a`, and a percept `o`, the new belief state is:

$\\begin{matrix} {b^{\\prime} = \\text{UPDATE(PREDICT(}b,a\\text{),}o\\text{)~}\\text{.}} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(4.6)} \\\\ \\end{matrix}$

Consider a kindergarten vacuum world wherein agents sense only the state of their current square, and any square may become dirty at any time unless the agent is actively cleaning it at that moment.[7](#Chapter04-07.xhtml#sup04-7) [Figure 4.17](#Chapter04-04.xhtml#fig4-17) shows the belief state being maintained in this environment.

Description

State space 1: An arrow from a node labeled `S` points to a node labeled “a”. Two arrows from the node labeled “a” point to two unlabeled nodes. An arrow from the first unlabeled node points to a node labeled `G`. An arrow from the second unlabeled node points to a third unlabeled node which has a self-loop. State space 2: An arrow from a node labeled `S` points to a node labeled “a”. Two arrows from the node labeled “a” point to two unlabeled nodes. An arrow from the first unlabeled node points to a third unlabeled node which has a self-loop. An arrow from the second unlabeled node points to a node labeled `G`.

×![](images/Fig-64.jpg)

Figure 4.17 Two prediction–update cycles of belief-state maintenance in the kindergarten vacuum world with local sensing.

In partially observable environments—which include the vast majority of real-world environments—maintaining one’s belief state is a core function of any intelligent system. This function goes under various names, including monitoring, filtering, and state estimation. [Equation (4.6)](#Chapter04-04.xhtml#eq4-6) is called a recursive state estimator because it computes the new belief state from the previous one rather than by examining the entire percept sequence. If the agent is not to “fall behind,” the computation has to happen as fast as percepts are coming in. As the environment becomes more complex, the agent will only have time to compute an approximate belief state, perhaps focusing on the implications of the percept for the aspects of the environment that are of current interest. Most work on this problem has been done for stochastic, continuous-state environments with the tools of probability theory, as explained in [Chapter 14](#Chapter14-00.xhtml).

Monitoring
Filtering
State estimation

In this section we will show an example in a discrete environment with deterministic sensors and nondeterministic actions. The example concerns a robot with a particular state estimation task called localization: working out where it is, given a map of the world and a sequence of percepts and actions. Our robot is placed in the maze-like environment of [Figure 4.18](#Chapter04-04.xhtml#fig4-18). The robot is equipped with four sonar sensors that tell whether there is an obstacle—the outer wall or a dark shaded square in the figure—in each of the four compass directions. The percept is in the form of a bit vector, one bit for each of the directions north, east, south, and west in that order, so `1011` means there are obstacles to the north, south, and west, but not east.

Description

Seven long thin blocks are arranged at different levels, and the count of the block extends to `n` numbers. A path is traced with alternate upper and lower parts of the blocks. The path starts at `S` and ends at `G`.

×![](images/Fig-65.jpg)

Figure 4.18 Possible positions of the robot, ʘ, (a) after one observation, `E1 = 1011`, and (b) after moving one square and making a second observation, `E2 = 1010`. When sensors are noiseless and the transition model is accurate, there is only one possible location for the robot consistent with this sequence of two observations.

Localization

We assume that the sensors give perfectly correct data, and that the robot has a correct map of the environment. But unfortunately, the robot’s navigational system is broken, so when it executes a `Right` action, it moves randomly to one of the adjacent squares. The robot’s task is to determine its current location.

Suppose the robot has just been switched on, and it does not know where it is—its initial belief state `b` consists of the set of all locations. The robot then receives the percept `1011` and does an update using the equation `bo = UPDATE(1011)`, yielding the 4 locations shown in [Figure 4.18(a)](#Chapter04-04.xhtml#fig4-18). You can inspect the maze to see that those are the only four locations that yield the percept `1011`.

Next the robot executes a `Right` action, but the result is nondeterministic. The new belief state, `ba = PREDICT(bo, Right)`, contains all the locations that are one step away from the locations in `bo`. When the second percept, `1010`, arrives, the robot does `UPDATE(ba, 1010)` and finds that the belief state has collapsed down to the single location shown in [Figure 4.18(b)](#Chapter04-04.xhtml#fig4-18). That’s the only location that could be the result of

`UPDATE(PREDICT(UPDATE(b, 1011), Right), 1010)`.

With nondeterministic actions the `PREDICT` step grows the belief state, but the `UPDATE` step shrinks it back down—as long as the percepts provide some useful identifying information. Sometimes the percepts don’t help much for localization: If there were one or more long east-west corridors, then a robot could receive a long sequence of `1010` percepts, but never know where in the corridor(s) it was. But for environments with reasonable variation in geography, localization often converges quickly to a single point, even when actions are nondeterministic.

What happens if the sensors are faulty? If we can reason only with Boolean logic, then we have to treat every sensor bit as being either correct or incorrect, which is the same as having no perceptual information at all. But we will see that probabilistic reasoning ([Chapter 12](#Chapter12-00.xhtml)), allows us to extract useful information from a faulty sensor as long as it is wrong less than half the time.

## 4.5 Online Search Agents and Unknown Environments
