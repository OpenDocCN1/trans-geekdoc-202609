
# Incomplete information game

Second is that the state and action spaces are continuous, as they’ve been throughout this chapter. We learned in [Chapter 6](#Chapter06-00.xhtml) how to do tree search to tackle discrete games, but how do we tackle continuous spaces?

Third, even though at the high level the game model makes sense—humans do move, and they do have objectives—a human’s behavior might not always be well-characterized as a solution to the game. The game comes with a computational challenge not only for the robot, but for us humans too. It requires to what the person does, which depends on what the robot thinks the person will do, and pretty soon we get to “what do you think I think you think I think”— it’s turtles all the way down! Humans can’t deal with all of that, and exhibit certain suboptimalities. This means that the robot should account for these suboptimalities.

So, then, what is an autonomous car to do when the coordination problem is this hard? We will do something similar to what we’ve done before in this chapter. For motion planning and control, we took an `MDP` and broke it up into planning a trajectory and then tracking it with a controller. Here too, we will take the game, and break it up into making predictions about human actions, and deciding what the robot should do given these predictions.

## Predicting human action

Predicting human actions is hard because they depend on the robot’s actions and vice versa. One trick that robots use is to pretend the person is ignoring the robot. The robot assumes people are noisily optimal with respect to their objective, which is unknown to the robot and is modeled as no longer dependent on the robot’s actions: `JH(x, uH)`. In particular, the higher the value of an action for the objective (the lower the cost to go), the more likely the human is to take it. The robot can create a model for `P(uH | x, JH)`, for instance using the `softmax` function from [page 862](#Chapter23-05.xhtml#page_862):

$\\begin{matrix} {P\\text{(}u\_{H}\\text{|~}x\\text{,}\\, J\_{H}\\text{)} \\propto e^{- Q(x,u\_{H};J\_{H})}\\ } & {\\,\\,\\,\\,\\,\\,\\,\\,(26.8)} \\\\ \\end{matrix}$

with `Q(x, uH; JH)` the Q-value function corresponding to `JH` (the negative sign is there because in robotics we like to minimize cost, not maximize reward). Note that the robot does not assume perfectly optimal actions, nor does it assume that the actions are chosen based on reasoning about the robot at all.

Armed with this model, the robot uses the human’s ongoing actions as evidence about `JH`. If we have an observation model for how human actions depend on the human’s objective, each human action can be incorporated to update the robot’s belief over what objective the person has:

$\\begin{matrix} \\left. b^{\\prime}(J\_{H}) \\propto b(J\_{H})P(u\_{H} \\middle| x,J\_{H}). \\right. & {\\,\\,\\,\\,\\,\\,\\,\\,\\,(26.9)} \\\\ \\end{matrix}$

An example is in [Figure 26.27](#Chapter26-08.xhtml#fig26-27): the robot is tracking a human’s location and as the human moves, the robot updates its belief over human goals. As the human heads toward the windows, the robot increases the probability that the goal is to look out the window, and decreases the probability that the goal is going to the kitchen, which is in the other direction.

Description

In all three parts, a map of a room is shown. The entrance is at the top and a corridor connects the entrance to an area that has the kitchen at the top and the lounge at the bottom. A room is present to the left of the kitchen. Multiple small spaces are present below the lounge area and a secretary desk to the left of the lounge area. Part (“a”): The map of the room is shown. Part (b): A heatmap of the prediction after seeing a small part of the person’s trajectory is shown. The trajectory is highlighted as a white line and ends at the end of the corridor from the entrance. The kitchen area and the room to its right have the maximum heat according to the heat map and are highlighted in deep red. The lounge area and the spaces below it have much lower heat according to the heat map and are highlighted in reddish-orange, yellow, and white colors based on the heat. Part (c): A heatmap of the predictions after seeing more human actions is shown. The trajectory is highlighted as a white line and ends close to the lounge area. The lounge area has the maximum heat, specifically going toward the secretary desk, and is highlighted in deep red. The spaces below the lounge area are highlighted in yellow. The kitchen area and the room to its right have no heat whatsoever.

×![](images/Fig-390.jpg)

Figure 26.27Making predictions by assuming that people are noisily rational given their goal: the robot uses the past actions to update a belief over what goal the person is heading to, and then uses the belief to make predictions about future actions. (a) The map of a room. (b) Predictions after seeing a small part of the person’s trajectory (white path); (c) Predictions after seeing more human actions: the robot now knows that the person is not heading to the hallway on the left, because the path taken so far would be a poor path if that were the person’s goal. Images courtesy of Brian D. Ziebart. See Ziebart et al. (2009).

This is how the human’s past actions end up informing the robot about what the human will do in the future. Having a belief about the human’s goal helps the robot anticipate what next actions the human will take. The heatmap in the figure shows the robot’s future predictions: red is most probable; blue least probable.

The same can happen in driving. We might not know how much another driver values efficiency, but if we see them accelerate as someone is trying to merge in front of them, we now know a bit more about them. And once we know that, we can better anticipate what they will do in the future—the same driver is likely to come closer behind us, or weave through traffic to get ahead.

Once the robot can make predictions about human future actions, it has reduced its problem to solving an `MDP`. The human actions complicate the transition function, but as long as the robot can anticipate what action the person will take from any future state, the robot can calculate `P(x' | x, uR)`: it can compute `P(uH | x)` from `P(uH | x, JH)` by marginalizing over `JH`, and combine it with `P(x' | x, uR, uH)`, the transition (dynamics) function for how the world updates based on both the robot’s and the human’s actions. In [Section 26.5](#Chapter26-05.xhtml#sec26-5) we focused on how to solve this in continuous state and action spaces for deterministic dynamics, and in [Section 26.6](#Chapter26-06.xhtml#sec26-6) we discussed doing it with stochastic dynamics and uncertainty.

Splitting prediction from action makes it easier for the robot to handle interaction, but sacrifices performance much as splitting estimation from motion did, or splitting planning from control.

A robot with this split no longer understands that its actions can influence what people end up doing. In contrast, the robot in [Figure 26.27](#Chapter26-08.xhtml#fig26-27) anticipates where people will go and then optimizes for reaching its own goal and avoiding collisions with them. In [Figure 26.28](#Chapter26-08.xhtml#fig26-28), we have an autonomous car merging on the highway. If it just planned in reaction to other cars, it might have to wait a long time while other cars occupy its target lane. In contrast, a car that reasons about prediction and action jointly knows that different actions it could take will result in different reactions from the human. If it starts to assert itself, the other cars are likely to slow down a bit and make room. Roboticists are working towards coordinated interactions like this so robots can work better with humans.

Description
