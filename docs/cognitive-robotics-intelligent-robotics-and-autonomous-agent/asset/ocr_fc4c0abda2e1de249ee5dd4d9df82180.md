# # 17 Cognitive Control for Decision and Human-Robot Collaboration

Erwin Jose Lopez Pulgarin, Ute Leonards, and Guido Herrmann

This chapter focuses on the concept of cognitive control in robotics and how it is linked to decision, control, and human-robot interaction (HRI). Achieving a control paradigm that enables robust, flexible goal-driven performance in a myriad of scenarios involving unstructured changing environments and interaction between robots and other agents such as humans has been pursued during the last decade (e.g., Avery, Kelley, and Davani 2006; Baud-Bovy et al. 2014; Herrmann and Leonards 2018). In order to achieve this, inspiration has been taken from nature, with a focus on the way humans and other animals undertake their decision and control processes (see chapter 1). Indeed, by creating controllers inspired by human flexibility and adaptability, some or all of the qualities found in human cognitive processes can be pursued (i.e., adaptability, robustness, goal-driven behavior with sensor and subtask prioritization) in artificial programmable systems.

First, this chapter includes an introduction to the concept of control in the context of industrial processes and expands it to robotics in general; challenges behind robot control will be raised, highlighting the need for novel decision and control architectures for modern robotics such as those involved in closely interacting with humans, dealing with unstructured environments, and learning to better perform a task—hence cognitive control.

Second, the word “cognitive” in the context of control will be defined after an overview about how “cognition” has been used in the literature; the definition of what a cognitive controller is will include aspects about both its architecture and inputs, highlighting how it relates to the term originally used in human behavioral studies and cognitive neuroscience.

Finally, a modeling approach for cognitive control, which integrates the principles of multiagent interaction into a decision-making (i.e., discrete and probabilistic) and control action (i.e., continuous and dynamic) framework will be proposed. This will be followed by a discussion around the framework’s elements and their wider impact in different areas of application, such as autonomous driving, teleoperation, and human-humanoid interaction.

# ## 17.1 Control in Robotics

When considering any system that interacts with the environment and manipulates it by any means or in any way, the concept of control needs to be considered. Starting from industrial control or process control (Ogata 2010), the main objective of “control” science