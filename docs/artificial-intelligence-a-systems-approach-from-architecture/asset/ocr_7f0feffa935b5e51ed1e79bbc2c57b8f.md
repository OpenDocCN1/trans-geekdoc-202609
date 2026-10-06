# 6.4: Autonomy and Near-Term Barriers 203

![](bbox=[0.363, 0.103, 0.636, 0.233])

| Sensing | Perception modules | Route planner |
| :--- | :--- | :--- |
| Lidars | Moving object detection | Plans routes via path search on global map |
| Camera | Obstacle detection | Monopoly board |
| GPS | Road edge detection | Keeps track of what to do via finite state machine |
| Accelerometers and gyros | World model Static and moving obstacles | Motion planner |
| Actuators | Road map | Plans short-term moves (a few seconds ahead) by searching for a short path |
| Steering | Position and speed of car | |
| Braking | | |

**Figure 6.7** The autonomous vehicle from Carnegie Mellon University, winner of the DARPA Urban Challenge [41].

The DARPA Urban Challenge was a remarkable demonstration of autonomous capabilities achieved over a very short period of time from the initial event of March 2004, when no vehicle finished the difficult dessert course. However, achieving full autonomy is still very hard. Karaman points out, full vehicle autonomy is difficult to accomplish in scenarios that are complex and where high speed is involved, as shown in figure 6.9 [43]. However, in scenarios where low speeds are acceptable and the scenario is simple, as with farming tractors, full autonomy is available.

Another challenge is the ability to navigate autonomously over difficult terrain (e.g., suburban towns). Researchers at Berkeley have devised an approach to employ auxiliary sensors and sources of data—like an inaccurate global positioning system, complemented with satellite images, contour maps, and prior experience learned from other environments—to build a learning-based method that it is more indicative of without