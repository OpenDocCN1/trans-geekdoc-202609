
## 6.4: Autonomy and Near-Term Barriers

| Exploits | | |
|---|---|---|
| Public databases | Intel TTP | Dark web |
| Vulnerabilities | | |
| Public NVD | Natural language processing | |
| Intel TTP | | |

![](img/3a09e5358d763329b6e01a25dd2312d4_215_0.png)

**Figure 6.6** ML used to prioritize vulnerabilities, reducing cyberoperators' workload.

AI adoption will continue to vary across industry sectors, depending on company size, risks, and ability to generate revenue. In 2017, the McKinsey Global Institute performed a comprehensive survey of AI adoption and use [34]. It surveyed C-level executives at 3,073 companies. They covered fourteen industries, ten countries in Europe, North America, and Asia, with a workforce ranging from 10 employees to over 10,000. One of the sectors, midway in terms of adoption and the future AI demand trajectory, was in healthcare. From their survey, the leading industry sectors were in the financial services, high-tech, and telecommunications. These findings were not surprising since the leading sectors, in general, do not have the same level of concern relative to the confidence level versus consequence of actions. Plus, these issues relating to fairness, accountability, transparency, ethics, privacy, and security (FASTEPS)—discussed in more detail in chapter 8 easier than sectors such as healthcare to achieve faster adoption, acceptance, and regular use.

## 6.4 Autonomy and Near-Term Barriers

The progress toward more autonomy is a very exciting and active area of research and development (R&D). The machines are expected to operate farther to the right of the HMT spectrum shown in figure 6.2, converting knowledge from the ML stage into insight. One example earlier is in the field of precision agriculture [11], where, using sensor data and computer vision, an autonomous tractor can deliver nutrients to fertilize crops and pesticides to control infested plants. Similarly, Anastasia Volkova, the chief executive officer (CEO) of Regrow, and her team have developed a platform to analyze crop performance, soil health, and carbon outcomes using measurements from drones, satellites, and ground sensors applied to advanced agricultural [35, 36].

There are many roles that autonomous robots can perform quite effectively. For example, Misty II is a robot developed by Misty Robotics (owned by the social robotics company Furhart Robotics), Tim Enwall, the former head of Misty Robotics, expressed his vision for this type of social robot as follows: “These robots will be seen and treated as our friends, our teammates, and a part of our families—performing tasks, providing safety, and interacting with humans in entertaining and friendly ways that have only been seen before science fiction” [37]. In chapter 14, we describe a concept developed by MIT graduate using Misty II as a companion, while some time providing to the elderly with an onset of Alzheimer’s disease.

Pieter Abel, a professor at University of California at Berkeley and the recipient of the IEEE Kiyo Tomiyasu award (the is for outstanding early-career to midcareer contributions to technologies holding the promise of innovative applications), emphasizes that the next challenges for autonomous robots lie in performing tasks that do with their hands: “The way automation is going to expand is going to be robots that are capable of seeing what’s around them, adapting to what’s around them, and learning things on the fly” [38].

Another area to have significant growth is autonomous vehicles. The DARPA Urban Grand Challenge, held in November 2007, was the first time that autonomous vehicles interacted with both manned and unmanned vehicle traffic in an urban (and connected) environment. Of the eleven teams that entered the competition, six were able to finish the 85-kilometer course. Three of these teams finished the course without human intervention. Boss, from the Carnegie Mellon University (Tart Racing), was the winner, 2007 Chevrolet Tahoe modified for autonomous driving [39, 40]. Figure 6.7 illustrates its system architecture, including sensing, AI modules for perception complemented by the world model of the urban environment, and a set of planning modules informing the actuators (i.e., steering, braking, and speed) [41].

From observations to actions, figure 6.8 shows a representative command-and-control architecture, including deep learning for the perception tasks and reinforcement learning for determining courses of action (based on goals and policies) [42]. This architecture is very consistent with the Boss architecture shown in figure 6.7, undertaking sense-plan-act tasks. However, the Boss architecture is fully autonomous. The architecture shown in figure 6.8 also includes an interface for communicating back to the human, which might be located in or connected to a cloud computing center.

![](img/3a09e5358d763329b6e01a25dd2312d4_217_0.png)

| Sensing | Perception modules | Route planner |
| :--- | :--- | :--- |
| Lidars | Moving object detection | Plans routes via path search on global map |
| Camera | Obstacle detection | Monopoly board |
| GPS | Road edge detection | Keeps track of what to do via finite state machine |
| Accelerometers and gyros | World model Static and moving obstacles | Motion planner |
| Actuators | Road map | Plans short-term moves (a few seconds ahead) by searching for path |
| Steering | Position and speed of car | |
| Braking | | |

**Figure 6.7** The autonomous vehicle from Carnegie Mellon University, winner of DARPA [41].

The DARPA Urban Challenge was a remarkable demonstration of autonomous capabilities achieved over a very short period of time from the initial event of March 2004, when no vehicle finished the difficult course. However, achieving full autonomy is still very hard. Karaman points out, full autonomy is difficult to accomplish in scenarios that are complex and where high speed is involved, as shown in figure 6.9 [43]. However, in scenarios where low speeds are acceptable and the scenario is simple, as with farming tractors, full autonomy is available.

Another challenge is the ability to navigate autonomously over difficult terrain (e.g., suburban towns). Researchers at Berkeley have devised an approach to employ auxiliary sensors and sources of data—like inaccurate global positioning system, complemented with satellite images, contour maps, and prior experience learned from other environments—to build a learning-based method that is more indicative of traversable patterns [44]. This innovative approach is consistent with building an informed world model, as shown in figure 6.8.

![](img/3a09e5358d763329b6e01a25dd2312d4_218_0.png)

1. Deep learning
2. Cognitive AI
3. Reinforcement learning

**Figure 6.8** Representative example of a command-and-control architecture for a robotics system [42].

In typical DARPA fashion, based on its charter, their projects serve as initial pathfinders for others to follow. Several of the US tech giants are spending billions of R&D on so-called frontier technologies, a category that autonomous vehicles fall into [45]. For example, Amazon invested in Zoox, Aurora, and Rivian; Apple acquired Drive.AI, a self-driving car start up; Microsoft invested in a self-driving car named Wayve; and Google owns Waymo and Nuro. Similarly, Tesla is also allocating significant investment into making electric vehicles more autonomous.

According to the US Department of Transportation, in 2016 there were 37,461 people killed in car crashes, and 1.25 million worldwide (as reported by the World Health Organization).

In addition to providing relief to human drivers (in terms of fatigue, boredom, loss of
