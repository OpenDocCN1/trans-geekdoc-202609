
## Control Theory Overview
We have covered how to plan motions, but not how to actually move—to apply current to motors, to produce torque, to move the robot. This is the realm of control theory, a field of increasing importance in AI. There are two main questions to deal with: how do we turn a mathematical description of a path into a sequence of actions in the real world (open-loop control), and how do we make sure that we are staying on track (closed-loop control)?

### Control theory

### Description
The motion of the robot arm to grab a bottle is shown in three stages. Two boxes are kept to the right of the bottle. In the first stage, the initial trajectory is plotted on the end effector of the robot arm. The path concave goes over the boxes to reach the bottle. In the second stage, the final trajectory after optimization is shown. The path is concave downward and goes directly toward the bottle without any obstacle in between. In the last stage, a photograph shows the robot arm about to grab the bottle using the trajectory from the second stage.

![](images/Fig-384.jpg)

Figure 26.21 The task of reaching to grasp a bottle solved with a trajectory optimizer. Left: the initial trajectory, plotted for the end effector. Middle: the final trajectory after optimization. Right: the goal configuration. Courtesy of Anca Dragan. See Ratliff et al. (2009).

## From configurations to torques for open-loop tracking
Our path `τ(t)` gives us configurations. The robot starts at rest at `q_s = τ(0)`. From there the robot’s motors will turn currents into torques, leading to motion. But what torques should the robot aim for, such that it ends up at `q_g = τ(1)`?

This is where the idea of a dynamics model (or transition model) comes in. We can give the robot a function `f` that computes the effects torques have on the configuration. Remember `F = ma` from physics? Well, there is something like that for torques too, in the form $u = f^{- 1}(q,\\overset{˙}{q},\\overset{¨}{q})$, with `u` a torque, $\\overset{˙}{q}$ a velocity, and $\\overset{¨}{q}$ an acceleration.[2](#Chapter26-12.xhtml#sup26-2) If the robot is at configuration `q` and velocity $\\overset{˙}{q}$, and applied torque `u`, that would lead to acceleration $\\overset{¨}{q} = f(q,\\overset{˙}{q},u)$. The tuple $(q,\\overset{˙}{q})$ is a dynamic state, because it includes velocity, whereas `q` is the kinematic state and is not sufficient for computing exactly what torque to apply. `f` is a deterministic dynamics model in the MDP over dynamic states with torques as actions. `f^{-1}` is the inverse dynamics, telling us what torque to apply if we want a particular acceleration, which leads to a change in velocity and thus a change in dynamic state.

### Dynamics model
### Dynamic state
### Kinematic state
### Inverse dynamics

Now, naively, we could think of `t ∈ [0,1]` as “time” on a scale from 0 to 1 and select our torque using inverse dynamics:

$\\begin{matrix} {u\\text{(}t\\text{)~=~}f^{- 1}\\text{(}\\tau(t),\\text{(}\\overset{˙}{\\tau}\\text{(}t\\text{),}\\overset{¨}{\\tau}\\text{(}t\\text{))}} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(26}\\text{.2)}} \\\\ \\end{matrix}$

assuming that the robot starts at $(\\tau(0),\\overset{˙}{\\tau}(0))$. In reality though, things are not that easy.

The path `τ` was created as a sequence of points, without taking velocities and accelerations into account. As such, the path may not satisfy $\\overset{˙}{\\tau}(0) = 0$ (the robot starts at 0 velocity), or even that `τ` is differentiable (let alone twice differentiable). Further, the meaning of the endpoint “1” is unclear: how many seconds does that map to?

In practice, before we even think of tracking a reference path, we usually retime it, that is, transform it into a trajectory `ξ(t)` that maps the interval `[0, T]` for some time duration `T` into points in the configuration space `C`. (The symbol `ξ` is the Greek letter Xi.) Retiming is trickier than you might think, but there are approximate ways to do it, for instance by picking a maximum velocity and acceleration, and using a profile that accelerates to that maximum velocity, stays there as long as it can, and then decelerates back to 0. Assuming we can do this, [Equation (26.2)](#Chapter26-05.xhtml#eq26-2) above can be rewritten as

### Retimimg

$\\begin{matrix} {u\\text{(}t\\text{)~=~}f^{- 1}\\text{(}\\xi(t),\\text{(}\\overset{˙}{\\xi}\\text{(}t\\text{),}\\overset{¨}{\\xi}\\text{(}t\\text{))}\\text{.}} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(26}\\text{.3)}} \\\\ \\end{matrix}$

Even with the change from `τ` to `ξ`, an actual trajectory, the equation of applying torques from above (called a control law) has a problem in practice. Thinking back to the reinforcement learning section, you might guess what it is. The equation works great in the situation where `f` is exact, but pesky reality gets in the way as usual: in real systems, we can’t measure masses and inertias exactly, and `f` might not properly account for physical phenomena like stiction in the motors (the friction that tends to prevent stationary surfaces from being set in motion—to make them stick). So, when the robot arm starts applying those torques but `f` is wrong, the errors accumulate and you deviate further and further from the reference path.

### Control law
### Stiction

Rather than just letting those errors accumulate, a robot can use a control process that looks at where it thinks it is, compares that to where it wanted to be, and applies a torque to minimize the error.

A controller that provides force in negative proportion to the observed error is known as a proportional controller or P controller for short. The equation for the force is:

### P controller

`u(t) = K_p(ξ(t) - q[t])`

where `q_t` is the current configuration, and `K_P` is a constant representing the gain factor of the controller. `K_P` regulates how strongly the controller corrects for deviations between the actual state `q_t` and the desired state `ξ(t)`.

### Gain factor

[Figure 26.22(a)](#Chapter26-05.xhtml#fig26-22) illustrates what can go wrong with proportional control. Whenever a deviation occurs—whether due to noise or to constraints on the forces the robot can apply—the robot provides an opposing force whose magnitude is proportional to this deviation. Intuitively, this might appear plausible, since deviations should be compensated by a counterforce to keep the robot on track. However, as [Figure 26.22(a)](#Chapter26-05.xhtml#fig26-22) illustrates, a proportional controller can cause the robot to apply too much force, overshooting the desired path and zig-zagging back and forth. This is the result of the natural inertia of the robot: once driven back to its reference position the robot has a velocity that can’t instantaneously be stopped.

### Description
In all three parts, the trajectory is shown around an irregular triangle-shaped obstacle. The starting point and the goal point are on either side near the vertex of the triangle. The trajectory starts at the left side, moves below the base, and ends at the right side. Part (“a”): Closely aligned spiral curves are shown along the path. Part (b): Loosely aligned spiral curves are shown along the path. Part (c): The line follows the path almost smoothly.

![](images/Fig-385.jpg)

Figure 26.22 Robot arm control using (a) proportional control with gain factor 1.0, (b) proportional control with gain factor 0.1, and (c) PD (proportional derivative) control with gain factors 0.3 for the proportional component and 0.8 for the differential component. In all cases the robot arm tries to follow the smooth line path, but in (a) and (b) deviates substantially from the path.
