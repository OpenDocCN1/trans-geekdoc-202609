
Other important aspects of robot state are measured by force sensors and torque sensors. These are indispensable when robots handle fragile objects or objects whose exact size and shape are unknown. Imagine a one-ton robotic manipulator screwing in a light bulb. It would be all too easy to apply too much force and break the bulb. Force sensors allow the robot to sense how hard it is gripping the bulb, and torque sensors allow it to sense how hard it is turning. High-quality sensors can measure forces in all three translational and three rotational directions. They do this at a frequency of several hundred times a second so that a robot can quickly detect unexpected forces and correct its actions before it breaks a light bulb. However, it can be a challenge to outfit a robot with high-end sensors and the computational power to monitor them.

Force sensor
Torque sensor

### 26.2.3 Producing motion

The mechanism that initiates the motion of an effector is called an actuator; examples include transmissions, gears, cables, and linkages. The most common type of actuator is the electric actuator, which uses electricity to spin up a motor. These are predominantly used in systems that need rotational motion, like joints on a robot arm. Hydraulic actuators use pressurized hydraulic fluid (like oil or water) and pneumatic actuators use compressed air to generate mechanical motion.

Actuator
Hydraulic actuator
Pneumatic actuator

Actuators are often used to move joints, which connect rigid bodies (links). Arms and legs have such joints. In revolute joints, one link rotates with respect to the other. In prismatic joints, one link slides along the other. Both of these are single-axis joints (one axis of motion). Other kinds of joints include spherical, cylindrical, and planar joints, which are multi-axis joints.

Revolute joint
Prismatic joint

To interact with objects in the environment, robots use grippers. The most basic type of gripper is the parallel jaw gripper, with two fingers and a single actuator that moves the fingers together to grasp objects. This effector is both loved and hated for its simplicity. Three-fingered grippers offer slightly more flexibility while maintaining simplicity. At the other end of the spectrum are humanoid (anthropomorphic) hands. For instance, the Shadow Dexterous Hand has a total of 20 actuators. This offers a lot more flexibility for complex manipulation, including in-hand manipulator maneuvers (think of picking up your cell phone and rotating it in-hand to orient it right-side up), but this flexibility comes at a price—learning to control these complex grippers is more challenging.

Parallel jaw gripper

## 26.3 What kind of problem is robotics solving?

Now that we know what the robot hardware might be, we’re ready to consider the agent software that drives the hardware to achieve our goals. We first need to decide the computational framework for this agent. We have talked about search in deterministic environments, MDPs for stochastic but fully observable environments, POMDPs for partial observability, and games for situations in which the agent is not acting in isolation. Given a computational framework, we need to instantiate its ingredients: reward or utility functions, states, actions, observation spaces, etc.

We have already noted that robotics problems are nondeterministic, partially observable, and multiagent. Using the game-theoretic notions from [Chapter 17](#Chapter17-00.xhtml), we can see that sometimes the agents are cooperative and sometimes they are competitive. In a narrow corridor where only one agent can go first, a robot and a person collaborate because they both want to make sure they don’t bump into each other. But in some cases they might compete a bit to reach their destination quickly. If the robot is too polite and always makes room, it might get stuck in crowded situations and never reach its goal.

Therefore, when robots act in isolation and know their environment, the problem they are solving can be formulated as an MDP; when they are missing information it becomes a POMDP; and when they act around people it can often be formulated as a game.

What is the robot’s reward function in this formulation? Usually the robot is acting in service of a human—for example delivering a meal to a hospital patient for the patient’s reward, not its own. For most robotics settings, even though robot designers might try to specify a good enough proxy reward function, the true reward function lies with the user whom the robot is supposed to help. The robot will either need to decipher the user’s desires, or rely on an engineer to specify an approximation of the user’s desires.

As for the robot’s action, state, and observation spaces, the most general form is that observations are raw sensor feeds (e.g., the images coming in from cameras, or the laser hits coming in from lidar); actions are raw electric currents being sent to the motors; and state is what the robot needs to know for its decision making. This means there is a huge gap between the low-level percepts and motor controls, and the high-level plans the robot needs to make. To bridge the gap, roboticists decouple aspects of the problem to simplify it.

For instance, we know that when we solve POMDPs properly, perception and action interact: perception informs which actions make sense, but action also informs perception, with agents taking actions to gather information when that information has value in later time steps. However, robots often separate perception from action, consuming the outputs of perception and pretending they will not get any more information in the future. Further, hierarchical planning is called for, because a high-level goal like “get to the cafeteria” is far removed from a motor command like “rotate the main axle 1°,”

In robotics we often use a three-level hierarchy. The task planning level decides a plan or policy for high-level actions, sometimes called action primitives or subgoals: move to the door, open it, go to the elevator, press the button, etc. Then motion planning is in charge of finding a path that gets the robot from one point to another, achieving each subgoal. Finally, control is used to achieve the planned motion using the robot’s actuators. Since the task planning level is typically defined over discrete states and actions, in this chapter we will focus primarily on motion planning and control.

Task planning
Control

Separately, preference learning is in charge of estimating an end user’s objective, and people prediction is used to forecast the actions of other people in the robot’s environment. All these combine to determine the robot’s behavior.

Preference learning
People prediction

Whenever we split a problem into separate pieces we reduce complexity, but we give up opportunities for the pieces to help each other. Action can help improve perception, and also determine what kind of perception is useful. Similarly, decisions at the motion level might not be the best when accounting for how that motion will be tracked; or decisions at the task level might render the task plan uninstantiatable at the motion level. So, with progress in these separate areas comes the push to reintegrate them: to do motion planning and control together, to do task and motion planning together, and to reintegrate perception, prediction, and action—closing the feedback loop. Robotics today is about continuing progress in each area while also building on this progress to achieve better integration.

## 26.4 Robotic Perception
