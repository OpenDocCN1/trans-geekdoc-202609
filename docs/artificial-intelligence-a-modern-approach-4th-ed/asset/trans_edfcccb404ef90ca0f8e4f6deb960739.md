
A model of the world can also be useful in reducing the sample complexity of model-free reinforcement learning methods by doing sim-to-real transfer: transferring policies that work in simulation to the real world. The idea is to use the model as a simulator for a policy search ([第23.5节](#Chapter23-05.xhtml#sec23-5)). To learn a policy that transfers well, we can add noise to the model during training, thereby making the policy more robust. Or, we can train policies that will work with a variety of models by sampling different parameters in the simulations—sometimes referred to as domain randomization. An example is in [图26.26](#Chapter26-07.xhtml#fig26-26), where a dexterous manipulation task is trained in simulation by varying visual attributes, as well as physical attributes like friction or damping.

×![](images/Fig-389.jpg)

图26.26 训练鲁棒策略。(a) 运行多个机器人手操作物体的仿真，使用不同的物理和光照随机化参数。鸣谢 Wojciech Zaremba。(b) 真实世界环境，笼子中央有一个机器人手，周围环绕着摄像机和测距仪。(c) 仿真和真实世界训练产生多种抓取物体的策略；这里是捏取抓取和四足抓取。鸣谢 OpenAI。参见 Andrychowicz et al. (2018a)。

<p class="sidebar">仿真到现实</p> <p class="sidebar">领域随机化</p>

Finally, hybrid approaches that borrow ideas from both model-based and model-free algorithms are meant to give us the best of both. The hybrid approach originated with the `Dyna` architecture, where the idea was to iterate between acting and improving the policy, but the policy improvement would come in two complementary ways: 1) the standard model-free way of using the experience to directly update the policy, and 2) the model-based way of using the experience to fit a model, then plan with it to generate a policy.

More recent techniques have experimented with fitting local models, planning with them to generate actions, and using these actions as supervision to fit a policy, then iterating to get better and better models around the areas that the policy needs. This has been successfully applied in end-to-end learning, where the policy takes pixels as input and directly outputs torques as actions—it enabled the first demonstration of deep RL on physical robots.

Models can also be exploited for the purpose of ensuring safe exploration. Learning slowly but safely may be better than learning quickly but crashing and burning half way through. So arguably, more important than reducing real-world samples is reducing real-world samples in dangerous states—we don’t want robots falling off cliffs, and we don’t want them breaking our favorite mugs or, even worse, colliding with objects and people. An approximate model, with uncertainty associated to it (for example by considering a range of values for its parameters), can guide exploration and impose constraints on the actions that the robot is allowed to take in order to avoid these dangerous states. This is an active area of research in robotics and control.

## 26.7.2 利用其他信息

Models are useful, but there is more we can do to further reduce sample complexity.

When setting up a reinforcement learning problem, we have to select the state and action spaces, the representation of the policy or value function, and the reward function we’re using. These decisions have a large impact on how easy or how hard we are making the problem.

One approach is to use higher-level motion primitives instead of low-level actions like torque commands. A motion primitive is a parameterized skill that the robot has. For example, a robotic soccer player might have the skill of “pass the ball to the player at (`x` , `y`).” All the policy needs to do is to figure out how to combine them and set their parameters, instead of reinventing them. This approach often learns much faster than low-level approaches, but does restrict the space of possible behaviors that the robot can learn.

<p class="sidebar">运动原语</p>

Another way to reduce the number of real-world samples required for learning is to reuse information from previous learning episodes on other tasks, rather than starting from scratch. This falls under the umbrella of metalearning or transfer learning.

Finally, people are a great source of information. In the next section, we talk about how to interact with people, and part of it is how to use their actions to guide the robot’s learning.

## 26.8 人类与机器人

Thus far, we’ve focused on a robot planning and learning how to act in isolation. This is useful for some robots, like the rovers we send out to explore distant planets on our behalf. But, for the most part, we do not build robots to work in isolation. We build them to help us, and to work in human environments, around and with us.

This raises two complementary challenges. First is optimizing reward when there are people acting in the same environment as the robot. We call this the coordination problem (see [第17.1节](#Chapter17-01.xhtml#sec17-1)). When the robot’s reward depends on not just its own actions, but also the actions that people take, the robot has to choose its actions in a way that meshes well with theirs. When the human and the robot are on the same team, this turns into collaboration.

Second is the challenge of optimizing for what people actually want. If a robot is to help people, its reward function needs to incentivize the actions that people want the robot to execute. Figuring out the right reward function (or policy) for the robot is itself an interaction problem. We will explore these two challenges in turn.

## 26.8.1 协调

Let’s assume for now, as we have been, that the robot has access to a clearly defined reward function. But, instead of needing to optimize it in isolation, now the robot needs to optimize it around a human who is also acting. For example, as an autonomous car merges on the highway, it needs to negotiate the maneuver with the human driver coming in the target lane—should it accelerate and merge in front, or slow down and merge behind? Later, as it pulls to a stop sign, preparing to take a right, it has to watch out for the cyclist in the bicycle lane, and for the pedestrian about to step onto the crosswalk.

Or, consider a mobile robot in a hallway. Someone heading straight toward the robot steps slightly to the right, indicating which side of the robot they want to pass on. The robot has to respond, clarifying its intentions.

### 人类作为近似理性代理

One way to formulate coordination with a human is to model it as a game between the robot and the human ([第17.2节](#Chapter17-02.xhtml#sec17-2)). With this approach, we explicitly make the assumption that people are agents incentivized by objectives. This does not automatically mean that they are perfectly rational agents (i.e., find optimal solutions in the game), but it does mean that the robot can structure the way it reasons about the human via the notion of possible objectives that the human might have. In this game:

•环境的状态捕捉机器人和人类代理的配置；记为 `x = (xR, xH)`；
•每个代理可以采取动作，分别为 `uR` 和 `uH`；
•每个代理都有一个目标，可以表示为代价，`JR` 和 `JH`：每个代理都希望安全高效地到达其目标；
•而且，如同任何博弈一样，每个目标都取决于状态和两个代理的动作：`JR(x, uR, uH)` 和 `JH(x, uH, uR)`。想想汽车-行人交互——汽车应停车如果行人横穿，而应向前行驶如果行人等待。

Three important aspects complicate this game. First is that the human and the robot don’t necessarily know each other’s objectives. This makes it an incomplete information game.
