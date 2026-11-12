(Lynch and Park 2017; Kavraki and LaValle 2016; Chung, Fu, and Kröger 2016; Villani and Shutter 2016), knowledge-based approaches (Beetz et al. 2012, 2016), and combinations of them.

To make our discussion more concrete, we take a look at the knowledge-based approach to robot programming that is illustrated in figure 21.1. The control program of a robotic agent in the knowledge-based approach consists of a generalized plan and a knowledge base of assertions and asserted reasoning patterns, often called axioms and inference rules.

The generalized plan spells out the logic of the implemented action. For the fetch&place task, this means the robot performs the pickup action at the location where it expects the object to be and places the object at its destination. Lots of complexity is hidden by this simple plan structure. For example, in order to be at a certain location, the robot has to navigate there. And if the robot has to change its position—for example, due to a sudden, more urgent request—it has to interrupt the task and return to it later in order to complete it. Another important aspect hidden in the plan is failure detection, recovery, and continuation. In autonomous robot applications requiring goal-directed object manipulation, more than 80 percent of the programs are concerned with competent failure handling.

A key reason why the robot plan is so compact and elegant is that programmers can state action parameters vaguely. The term “at the location of the object” abstracts away from various pieces of detailed information that a robot needs to perform the task success-

| Generalized plan |
|---|
| def-plan fetch&place ((obj): (an object (type thing)), (dest): (a location (type place)))<br>1. at-location (a location (location-of (obj)))<br>perform (an action<br>(type fetching)<br>(object-acted-on (obj)))<br>2. at-location (a location (dest))<br>perform (an action<br>(type placing)<br>(object-acted-on (obj)))<br>(destination (dest))) |
| Knowledge base |
|---|
| Cups used for tablesetting have to be clean and unused<br>People want to use their preferred items<br>Cups in cupboards are clean<br>Clean cups are empty<br>Cups have to be grasped outside<br>... |

**Figure 21.1**
The knowledge-based approach to robot programming includes two main components: a generalized robot plan and a knowledge base of assertions and rules.